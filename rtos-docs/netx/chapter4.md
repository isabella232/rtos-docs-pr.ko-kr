---
title: 4장 - Azure RTOS NetX 서비스 설명
description: 이 장에서는 모든 Azure RTOS NetX 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810458"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a><span data-ttu-id="112c2-103">4장 - Azure RTOS NetX 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="112c2-103">Chapter 4 - Description of Azure RTOS NetX Services</span></span>

<span data-ttu-id="112c2-104">이 장에서는 모든 Azure RTOS NetX 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-104">This chapter contains a description of all Azure RTOS NetX services in alphabetic order.</span></span> <span data-ttu-id="112c2-105">서비스 이름은 모든 유사한 서비스가 함께 그룹화되도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-105">Service names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="112c2-106">예를 들어 모든 ARP 서비스는 이 장의 시작 부분에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-106">For example, all ARP services are found at the beginning of this chapter.</span></span>

> [!NOTE]
> <span data-ttu-id="112c2-107">BSD 호환 소켓 API는 고성능 NetX API를 충분히 활용할 수 없는 레거시 애플리케이션 코드에 사용할 수 있습니다. BSD 호환 소켓 API에 대한 자세한 내용은 부록 D를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="112c2-107">*Note that a BSD-Compatible Socket API is available for legacy application code that cannot take full advantage of the high-performance NetX API. Refer to Appendix D for more information on the BSD-Compatible Socket API.*</span></span>

<span data-ttu-id="112c2-108">각 설명의 “반환 값” 섹션에서 **BOLD** 로 표시된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 NX_DISABLE_ERROR_CHECKING 옵션의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-108">In the "Return Values" section of each description, values in **BOLD** are not affected by the NX_DISABLE_ERROR_CHECKING option used to disable the API error checking, while values in non-bold are completely disabled.</span></span> <span data-ttu-id="112c2-109">“허용되는 위치” 섹션은 각 NetX 서비스를 호출할 수 있는 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-109">The "Allowed From" sections indicate from which each NetX service can be called.</span></span>

## <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="112c2-110">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="112c2-110">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="112c2-111">ARP 캐시의 모든 동적 항목을 무효화합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-111">Invalidate all dynamic entries in the ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-112">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-112">Prototype</span></span>

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-113">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-113">Description</span></span>

<span data-ttu-id="112c2-114">이 서비스는 현재 ARP 캐시에 있는 모든 동적 ARP 항목을 무효화합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-114">This service invalidates all dynamic ARP entries currently in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-115">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-115">Parameters</span></span>

- <span data-ttu-id="112c2-116">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-116">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-117">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-117">Return Values</span></span>

- <span data-ttu-id="112c2-118">**NX_SUCCESS**(0x00) ARP 캐시 무효화에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-118">**NX_SUCCESS** (0x00) Successful ARP cache invalidate.</span></span>
- <span data-ttu-id="112c2-119">**NX_NOT_ENABLED**(0x14) ARP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-119">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="112c2-120">**NX_PTR_ERROR**(0x07) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-120">**NX_PTR_ERROR** (0x07) Invalid IP address.</span></span>
- <span data-ttu-id="112c2-121">**NX_CALLER_ERROR**(0x11) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-121">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-122">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-122">Allowed From</span></span>

<span data-ttu-id="112c2-123">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-123">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-124">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-124">Preemption Possible</span></span>

<span data-ttu-id="112c2-125">예</span><span class="sxs-lookup"><span data-stu-id="112c2-125">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-126">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-126">Example</span></span>

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-127">See Also</span></span>

- <span data-ttu-id="112c2-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="112c2-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="112c2-129">nx_arp_hardware_address_find, nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-129">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="112c2-130">nx_arp_ip_address_find, nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-130">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="112c2-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="112c2-132">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="112c2-132">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="112c2-133">동적 ARP 항목을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-133">Set dynamic ARP entry</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-134">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-134">Prototype</span></span>

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="112c2-135">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-135">Description</span></span>

<span data-ttu-id="112c2-136">이 서비스는 ARP 캐시의 동적 항목을 할당하고 지정된 IP를 물리적 주소 매핑으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-136">This service allocates a dynamic entry from the ARP cache and sets up the specified IP to physical address mapping.</span></span> <span data-ttu-id="112c2-137">물리적 주소를 0으로 지정하면 물리적 주소를 확인하기 위해 실제 ARP 요청이 네트워크로 송신됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-137">If a zero physical address is specified, an actual ARP request is sent to the network in order to have the physical address resolved.</span></span> <span data-ttu-id="112c2-138">이 항목은 ARP 에이징이 활성인 경우 또는 ARP 캐시가 고갈되어 오래전에 사용된 ARP 항목인 경우에도 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-138">Also note that this entry will be removed if ARP aging is active or if the ARP cache is exhausted and this is the least recently used ARP entry.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-139">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-139">Parameters</span></span>

- <span data-ttu-id="112c2-140">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-140">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-141">**ip_address** 매핑할 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-141">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="112c2-142">**physical_msw** 물리적 주소의 상위 16비트(47-32)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-142">**physical_msw** Top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="112c2-143">**physical_lsw** 물리적 주소의 하위 32비트(31-0)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-143">**physical_lsw** Lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-144">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-144">Return Values</span></span>

- <span data-ttu-id="112c2-145">**NX_SUCCESS**(0x00) ARP 동적 항목 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-145">**NX_SUCCESS** (0x00) Successful ARP dynamic entry set.</span></span>
- <span data-ttu-id="112c2-146">**NX_NO_MORE_ENTRIES**(0x17) ARP 캐시에 사용할 수 있는 ARP 항목이 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-146">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="112c2-147">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-147">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="112c2-148">**NX_PTR_ERROR**(0x07) 잘못된 IP 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-148">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="112c2-149">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-149">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="112c2-150">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-150">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-151">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-151">Allowed From</span></span>

<span data-ttu-id="112c2-152">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-152">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-153">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-153">Preemption Possible</span></span>

<span data-ttu-id="112c2-154">예</span><span class="sxs-lookup"><span data-stu-id="112c2-154">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-155">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-155">Example</span></span>

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-156">See Also</span></span>

- <span data-ttu-id="112c2-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable,</span></span>
- <span data-ttu-id="112c2-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="112c2-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="112c2-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="112c2-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_enable"></a><span data-ttu-id="112c2-161">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-161">nx_arp_enable</span></span>

<span data-ttu-id="112c2-162">ARP(주소 확인 프로토콜)를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-162">Enables Address Resolution Protocol (ARP).</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-163">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-163">Prototype</span></span>

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a><span data-ttu-id="112c2-164">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-164">Description</span></span>

<span data-ttu-id="112c2-165">이 서비스는 특정 IP 인스턴스에 대해 NetX의 ARP 구성 요소를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-165">This service initializes the ARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="112c2-166">ARP 초기화에는 ARP 메시지 송신 및 수신에 필요한 ARP 캐시와 다양한 ARP 처리 루틴 설정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-166">ARP initialization includes setting up the ARP cache and various ARP processing routines necessary for sending and receiving ARP messages.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-167">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-167">Parameters</span></span>

- <span data-ttu-id="112c2-168">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-168">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-169">**arp_cache_memory** ARP 캐시를 지정할 메모리 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-169">**arp_cache_memory** Pointer to memory area to place ARP cache.</span></span>
- <span data-ttu-id="112c2-170">**arp_cache_size** 각 ARP 항목은 52바이트이므로 총 ARP 항목 수는 52로 나뉘는 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-170">**arp_cache_size** Each ARP entry is 52 bytes, the total number of ARP entries is, therefore, the size divided by 52.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-171">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-171">Return Values</span></span>

- <span data-ttu-id="112c2-172">**NX_SUCCESS**(0x00) ARP를 사용하도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-172">**NX_SUCCESS** (0x00) Successful ARP enable.</span></span>
- <span data-ttu-id="112c2-173">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 캐시 메모리 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-173">**NX_PTR_ERROR** (0x07) Invalid IP or cache memory pointer.</span></span>
- <span data-ttu-id="112c2-174">**NX_SIZE_ERROR**(0x09) 사용자 제공 ARP 캐시 메모리가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-174">**NX_SIZE_ERROR** (0x09) User supplied ARP cache memory is too small.</span></span>
- <span data-ttu-id="112c2-175">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-175">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-176">**NX_ALREADY_ENABLED**(0x15) 이 구성 요소는 이미 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-176">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-177">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-177">Allowed From</span></span>

<span data-ttu-id="112c2-178">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-178">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-179">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-179">Preemption Possible</span></span>

<span data-ttu-id="112c2-180">예</span><span class="sxs-lookup"><span data-stu-id="112c2-180">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-181">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-181">Example</span></span>

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a><span data-ttu-id="112c2-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-182">See Also</span></span>

- <span data-ttu-id="112c2-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="112c2-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="112c2-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="112c2-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="112c2-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="112c2-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="112c2-187">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="112c2-187">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="112c2-188">무상 ARP 요청을 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-188">Send gratuitous ARP request</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-189">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-189">Prototype</span></span>

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="112c2-190">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-190">Description</span></span>

<span data-ttu-id="112c2-191">이 서비스는 인터페이스 IP 주소가 유효하면 모든 실제 인터페이스를 통해 무상 ARP 요청을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-191">This service goes through all the physical interfaces to transmit gratuitous ARP requests as long as the interface IP address is valid.</span></span> <span data-ttu-id="112c2-192">이어서 ARP 응답을 수신하면 제공된 응답 처리기가 호출되어 무상 ARP에 대한 응답을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-192">If an ARP response is subsequently received, the supplied response handler is called to process the response to the gratuitous ARP.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-193">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-193">Parameters</span></span>

- <span data-ttu-id="112c2-194">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-194">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-195">**response_handler** 응답 처리 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-195">**response_handler** Pointer to response handling function.</span></span> <span data-ttu-id="112c2-196">NX_NULL이 제공되면 응답은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-196">If NX_NULL is supplied, responses are ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-197">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-197">Return Values</span></span>

- <span data-ttu-id="112c2-198">**NX_SUCCESS**(0x00) 무상 ARP 송신에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-198">**NX_SUCCESS** (0x00) Successful gratuitous ARP send.</span></span>
- <span data-ttu-id="112c2-199">**NX_NO_PACKET**(0x01) 사용할 수 있는 패킷이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-199">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="112c2-200">**NX_NOT_ENABLED**(0x14) ARP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-200">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="112c2-201">**NX_IP_ADDRESS_ERROR**(0x21) 현재 IP 주소가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-201">**NX_IP_ADDRESS_ERROR** (0x21) Current IP address is invalid.</span></span>
- <span data-ttu-id="112c2-202">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-202">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-203">**NX_CALLER_ERROR**(0x11) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-203">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-204">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-204">Allowed From</span></span>

<span data-ttu-id="112c2-205">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-206">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-206">Preemption Possible</span></span>

<span data-ttu-id="112c2-207">예</span><span class="sxs-lookup"><span data-stu-id="112c2-207">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-208">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-208">Example</span></span>

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-209">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-209">See Also</span></span>

- <span data-ttu-id="112c2-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="112c2-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="112c2-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="112c2-212">nx_arp_ip_address_find, nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-212">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="112c2-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="112c2-214">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="112c2-214">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="112c2-215">제공된 IP 주소에 해당하는 물리적 하드웨어 주소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-215">Locate physical hardware address given an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-216">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-216">Prototype</span></span>

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a><span data-ttu-id="112c2-217">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-217">Description</span></span>

<span data-ttu-id="112c2-218">이 서비스는 제공된 IP 주소와 연결된 ARP 캐시에서 물리적 하드웨어 주소를 찾으려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-218">This service attempts to find a physical hardware address in the ARP cache that is associated with the supplied IP address.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-219">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-219">Parameters</span></span>

- <span data-ttu-id="112c2-220">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-220">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-221">**ip_address** 검색할 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-221">**ip_address** IP address to search for.</span></span>
- <span data-ttu-id="112c2-222">**physical_msw** 물리적 주소의 상위 16비트(47-32)를 반환하는 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-222">**physical_msw** Pointer to the variable for returning the top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="112c2-223">**physical_lsw** 물리적 주소의 하위 32비트(31-0)를 반환하는 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-223">**physical_lsw** Pointer to the variable for returning the lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-224">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-224">Return Values</span></span>

- <span data-ttu-id="112c2-225">**NX_SUCCESS**(0x00) ARP 하드웨어 주소 찾기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-225">**NX_SUCCESS** (0x00) Successful ARP hardware address find.</span></span>
- <span data-ttu-id="112c2-226">**NX_ENTRY_NOT_FOUND**(0x16) ARP 캐시에서 매핑을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-226">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="112c2-227">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-227">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="112c2-228">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 메모리 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-228">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="112c2-229">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-229">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-230">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-230">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-231">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-231">Allowed From</span></span>

<span data-ttu-id="112c2-232">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-232">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-233">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-233">Preemption Possible</span></span>

<span data-ttu-id="112c2-234">예</span><span class="sxs-lookup"><span data-stu-id="112c2-234">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-235">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-235">Example</span></span>

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a><span data-ttu-id="112c2-236">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-236">See Also</span></span>

- <span data-ttu-id="112c2-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="112c2-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="112c2-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,</span></span>
- <span data-ttu-id="112c2-239">nx_arp_ip_address_find, nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-239">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="112c2-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_info_get"></a><span data-ttu-id="112c2-241">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-241">nx_arp_info_get</span></span>

<span data-ttu-id="112c2-242">ARP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-242">Retrieve information about ARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-243">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-243">Prototype</span></span>

```C
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="112c2-244">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-244">Description</span></span>

<span data-ttu-id="112c2-245">이 서비스는 연결된 IP 인스턴스의 ARP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-245">This service retrieves information about ARP activities for the associated IP instance.</span></span>

<span data-ttu-id="112c2-246">대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-246">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-247">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-247">Parameters</span></span>

- <span data-ttu-id="112c2-248">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-248">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-249">**arp_requests_sent** 이 IP 인스턴스에서 송신된 총 ARP 요청 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-249">**arp_requests_sent** Pointer to destination for the total ARP requests sent from this IP instance.</span></span>
- <span data-ttu-id="112c2-250">**arp_requests_received** 네트워크에서 수신된 총 ARP 요청 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-250">**arp_requests_received** Pointer to destination for the total ARP requests received from the network.</span></span>
- <span data-ttu-id="112c2-251">**arp_responses_sent** 이 IP 인스턴스에서 송신된 총 ARP 응답 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-251">**arp_responses_sent** Pointer to destination for the total ARP responses sent from this IP instance.</span></span>
- <span data-ttu-id="112c2-252">**arp_responses_received** 네트워크에서 수신된 총 ARP 응답 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-252">**arp_responses_received** Pointer to the destination for the total ARP responses received from the network.</span></span>
- <span data-ttu-id="112c2-253">**arp_dynamic_entries** 현재 동적 ARP 항목 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-253">**arp_dynamic_entries** Pointer to the destination for the current number of dynamic ARP entries.</span></span>
- <span data-ttu-id="112c2-254">**arp_static_entries** 현재 고정 ARP 항목 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-254">**arp_static_entries** Pointer to the destination for the current number of static ARP entries.</span></span>
- <span data-ttu-id="112c2-255">**arp_aged_entries** 오래되고 잘못된 총 ARP 항목 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-255">**arp_aged_entries** Pointer to the destination of the total number of ARP entries that have aged and became invalid.</span></span>
- <span data-ttu-id="112c2-256">**arp_invalid_messages** 수신되었으나 잘못된 총 ARP 메시지 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-256">**arp_invalid_messages** Pointer to the destination of the total invalid ARP messages received.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-257">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-257">Return Values</span></span>

- <span data-ttu-id="112c2-258">**NX_SUCCESS**(0x00) ARP 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-258">**NX_SUCCESS** (0x00) Successful ARP information retrieval.</span></span>
- <span data-ttu-id="112c2-259">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-259">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-260">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-260">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-261">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-261">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-262">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-262">Allowed From</span></span>

<span data-ttu-id="112c2-263">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-263">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-264">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-264">Preemption Possible</span></span>

<span data-ttu-id="112c2-265">예</span><span class="sxs-lookup"><span data-stu-id="112c2-265">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-266">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-266">Example</span></span>

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
    &arp_requests_received,
    &arp_responses_sent,
    &arp_responses_received,
    &arp_dynamic_entries,
    &arp_static_entries,
    &arp_aged_entries,
    &arp_invalid_messages);
/* If status is NX_SUCCESS, the ARP information has been stored in
    the supplied variables. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-267">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-267">See Also</span></span>

- <span data-ttu-id="112c2-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="112c2-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="112c2-269">nx_arp_enable, nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="112c2-269">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="112c2-270">nx_arp_hardware_address_find, nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="112c2-270">nx_arp_hardware_address_find, nx_arp_ip_address_find,</span></span>
- <span data-ttu-id="112c2-271">nx_arp_static_entries_delete, nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="112c2-271">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="112c2-272">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-272">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_ip_address_find"></a><span data-ttu-id="112c2-273">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="112c2-273">nx_arp_ip_address_find</span></span>

<span data-ttu-id="112c2-274">제공된 물리적 주소에 해당하는 IP 주소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-274">Locate IP address given a physical address</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-275">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-275">Prototype</span></span>

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="112c2-276">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-276">Description</span></span>

<span data-ttu-id="112c2-277">이 서비스는 제공된 물리적 주소와 연결된 ARP 캐시에서 IP 주소를 찾으려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-277">This service attempts to find an IP address in the ARP cache that is associated with the supplied physical address.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-278">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-278">Parameters</span></span>

- <span data-ttu-id="112c2-279">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-279">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-280">**ip_address** 매핑된 IP 주소가 있는 경우, 반환 IP 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-280">**ip_address** Pointer to return IP address, if one is found that has been mapped.</span></span>
- <span data-ttu-id="112c2-281">**physical_msw** 검색할 물리적 주소의 상위 16비트(47-32)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-281">**physical_msw** Top 16 bits (47-32) of the physical address to search for.</span></span>
- <span data-ttu-id="112c2-282">**physical_lsw** 검색할 물리적 주소의 하위 32비트(31-0)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-282">**physical_lsw** Lower 32 bits (31-0) of the physical address to search for.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-283">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-283">Return Values</span></span>

- <span data-ttu-id="112c2-284">**NX_SUCCESS**(0x00) ARP IP 주소 찾기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-284">**NX_SUCCESS** (0x00) Successful ARP IP address find</span></span>
- <span data-ttu-id="112c2-285">**NX_ENTRY_NOT_FOUND**(0x16) ARP 캐시에서 매핑을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-285">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="112c2-286">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 메모리 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-286">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="112c2-287">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-287">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-288">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-288">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="112c2-289">**NX_INVALID_PARAMETERS**(0x4D) Physical_msw 및 physical_lsw는 둘 다 0입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-289">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-290">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-290">Allowed From</span></span>

<span data-ttu-id="112c2-291">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-291">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-292">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-292">Preemption Possible</span></span>

<span data-ttu-id="112c2-293">예</span><span class="sxs-lookup"><span data-stu-id="112c2-293">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-294">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-294">Example</span></span>

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a><span data-ttu-id="112c2-295">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-295">See Also</span></span>

- <span data-ttu-id="112c2-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="112c2-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="112c2-297">nx_arp_enable, nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="112c2-297">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="112c2-298">nx_arp_hardware_address_find, nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-298">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="112c2-299">nx_arp_static_entries_delete,nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="112c2-299">nx_arp_static_entries_delete,nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="112c2-300">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-300">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="112c2-301">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-301">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="112c2-302">모든 고정 ARP 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-302">Delete all static ARP entries</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-303">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-303">Prototype</span></span>

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-304">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-304">Description</span></span>

<span data-ttu-id="112c2-305">이 서비스는 ARP 캐시의 모든 고정 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-305">This service deletes all static entries in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-306">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-306">Parameters</span></span>

- <span data-ttu-id="112c2-307">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-307">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-308">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-308">Return Values</span></span>

- <span data-ttu-id="112c2-309">**NX_SUCCESS**(0x00) 고정 항목이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-309">**NX_SUCCESS** (0x00) Static entries are deleted.</span></span>
- <span data-ttu-id="112c2-310">**NX_PTR_ERROR**(0x07) 잘못된 ip_ptr 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-310">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>
- <span data-ttu-id="112c2-311">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-311">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-312">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-312">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-313">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-313">Allowed From</span></span>

<span data-ttu-id="112c2-314">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-314">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-315">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-315">Preemption Possible</span></span>

<span data-ttu-id="112c2-316">예</span><span class="sxs-lookup"><span data-stu-id="112c2-316">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-317">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-317">Example</span></span>

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-318">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-318">See Also</span></span>

- <span data-ttu-id="112c2-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="112c2-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="112c2-320">nx_arp_enable, nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="112c2-320">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="112c2-321">nx_arp_hardware_address_find, nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-321">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="112c2-322">nx_arp_ip_address_find, nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="112c2-322">nx_arp_ip_address_find, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="112c2-323">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-323">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_create"></a><span data-ttu-id="112c2-324">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="112c2-324">nx_arp_static_entry_create</span></span>

<span data-ttu-id="112c2-325">ARP 캐시에 고정 IP-하드웨어 매핑을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-325">Create static IP to hardware mapping in ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-326">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-326">Prototype</span></span>

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="112c2-327">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-327">Description</span></span>

<span data-ttu-id="112c2-328">이 서비스는 지정된 IP 인스턴스의 ARP 캐시에 고정 IP-물리적 주소 매핑을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-328">This service creates a static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span> <span data-ttu-id="112c2-329">고정 ARP 항목에는 ARP 정기 업데이트가 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-329">Static ARP entries are not subject to ARP periodic updates.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-330">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-330">Parameters</span></span>

- <span data-ttu-id="112c2-331">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-331">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-332">**ip_address** 매핑할 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-332">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="112c2-333">**physical_msw** 매핑할 물리적 주소의 상위 16비트(47-32)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-333">**physical_msw** Top 16 bits (47-32) of the physical address to map.</span></span>
- <span data-ttu-id="112c2-334">**physical_lsw** 매핑할 물리적 주소의 하위 32비트(31-0)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-334">**physical_lsw** Lower 32 bits (31-0) of the physical address to map.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-335">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-335">Return Values</span></span>

- <span data-ttu-id="112c2-336">**NX_SUCCESS**(0x00) ARP 고정 항목 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-336">**NX_SUCCESS** (0x00) Successful ARP static entry create.</span></span>
- <span data-ttu-id="112c2-337">**NX_NO_MORE_ENTRIES**(0x17) ARP 캐시에 사용할 수 있는 ARP 항목이 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-337">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="112c2-338">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-338">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="112c2-339">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-339">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-340">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-340">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-341">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-341">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="112c2-342">**NX_INVALID_PARAMETERS**(0x4D) Physical_msw 및 physical_lsw는 둘 다 0입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-342">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-343">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-343">Allowed From</span></span>

<span data-ttu-id="112c2-344">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-344">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-345">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-345">Preemption Possible</span></span>

<span data-ttu-id="112c2-346">예</span><span class="sxs-lookup"><span data-stu-id="112c2-346">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-347">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-347">Example</span></span>

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-348">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-348">See Also</span></span>

- <span data-ttu-id="112c2-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="112c2-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="112c2-350">nx_arp_enable, nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="112c2-350">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="112c2-351">nx_arp_hardware_address_find, nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-351">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="112c2-352">nx_arp_ip_address_find, nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-352">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="112c2-353">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-353">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="112c2-354">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-354">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="112c2-355">ARP 캐시에서 고정 IP-하드웨어 매핑을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-355">Delete static IP to hardware mapping in ARP cache</span></span>


### <a name="prototype"></a><span data-ttu-id="112c2-356">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-356">Prototype</span></span>

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="112c2-357">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-357">Description</span></span>

<span data-ttu-id="112c2-358">이 서비스는 지정된 IP 인스턴스의 ARP 캐시에서 이전에 만든 고정 IP-물리적 주소 매핑을 찾아서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-358">This service finds and deletes a previously created static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-359">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-359">Parameters</span></span>

- <span data-ttu-id="112c2-360">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-360">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-361">**ip_address** 정적으로 매핑된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-361">**ip_address** IP address that was mapped statically.</span></span>
- <span data-ttu-id="112c2-362">**physical_msw** 정적으로 매핑된 물리적 주소의 상위 16비트(47-32)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-362">**physical_msw** Top 16 bits (47 - 32) of the physical address that was mapped statically.</span></span>
- <span data-ttu-id="112c2-363">**physical_lsw** 정적으로 매핑된 물리적 주소의 하위 32비트(31-0)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-363">**physical_lsw** Lower 32 bits (31 - 0) of the physical address that was mapped statically.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-364">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-364">Return Values</span></span>

- <span data-ttu-id="112c2-365">**NX_SUCCESS**(0x00) ARP 고정 항목 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-365">**NX_SUCCESS** (0x00) Successful ARP static entry delete.</span></span>
- <span data-ttu-id="112c2-366">**NX_ENTRY_NOT_FOUND**(0x16) ARP 캐시에서 고정 ARP 항목을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-366">**NX_ENTRY_NOT_FOUND** (0x16) Static ARP entry was not found in the ARP cache.</span></span>
- <span data-ttu-id="112c2-367">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-367">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-368">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-368">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-369">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-369">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="112c2-370">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-370">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="112c2-371">**NX_INVALID_PARAMETERS**(0x4D) Physical_msw 및 physical_lsw는 둘 다 0입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-371">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-372">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-372">Allowed From</span></span>

<span data-ttu-id="112c2-373">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-373">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-374">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-374">Preemption Possible</span></span>

<span data-ttu-id="112c2-375">예</span><span class="sxs-lookup"><span data-stu-id="112c2-375">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-376">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-376">Example</span></span>

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-377">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-377">See Also</span></span>

- <span data-ttu-id="112c2-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="112c2-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="112c2-379">nx_arp_enable, nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="112c2-379">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="112c2-380">nx_arp_hardware_address_find, nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-380">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="112c2-381">nx_arp_ip_address_find, nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-381">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="112c2-382">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="112c2-382">nx_arp_static_entry_create</span></span>

## <a name="nx_icmp_enable"></a><span data-ttu-id="112c2-383">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-383">nx_icmp_enable</span></span>

<span data-ttu-id="112c2-384">ICMP(Internet Control Message Protocol)를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-384">Enable Internet Control Message Protocol (ICMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-385">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-385">Prototype</span></span>

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-386">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-386">Description</span></span>

<span data-ttu-id="112c2-387">이 서비스는 지정된 IP 인스턴스의 ICMP 구성 요소를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-387">This service enables the ICMP component for the specified IP instance.</span></span>
<span data-ttu-id="112c2-388">ICMP 구성 요소는 인터넷 오류 메시지와 ping 요청 및 회신을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-388">The ICMP component is responsible for handling Internet error messages and ping requests and replies.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-389">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-389">Parameters</span></span>

- <span data-ttu-id="112c2-390">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-390">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-391">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-391">Return Values</span></span>

- <span data-ttu-id="112c2-392">**NX_SUCCESS**(0x00) ICMP를 사용하도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-392">**NX_SUCCESS** (0x00) Successful ICMP enable.</span></span>
- <span data-ttu-id="112c2-393">**NX_ALREADY_ENABLED**(0x15) ICMP는 이미 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-393">**NX_ALREADY_ENABLED** (0x15) ICMP is already enabled.</span></span>
- <span data-ttu-id="112c2-394">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-394">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-395">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-395">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-396">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-396">Allowed From</span></span>

<span data-ttu-id="112c2-397">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-397">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-398">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-398">Preemption Possible</span></span>

<span data-ttu-id="112c2-399">예</span><span class="sxs-lookup"><span data-stu-id="112c2-399">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-400">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-400">Example</span></span>

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-401">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-401">See Also</span></span>

- <span data-ttu-id="112c2-402">nx_icmp_info_get, nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="112c2-402">nx_icmp_info_get, nx_icmp_ping</span></span>

## <a name="nx_icmp_info_get"></a><span data-ttu-id="112c2-403">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-403">nx_icmp_info_get</span></span>

<span data-ttu-id="112c2-404">ICMP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-404">Retrieve information about ICMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-405">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-405">Prototype</span></span>

```C
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```

### <a name="description"></a><span data-ttu-id="112c2-406">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-406">Description</span></span>

<span data-ttu-id="112c2-407">이 서비스는 지정된 IP 인스턴스의 ICMP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-407">This service retrieves information about ICMP activities for the specified IP instance.</span></span>

<span data-ttu-id="112c2-408">대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-408">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-409">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-409">Parameters</span></span>

- <span data-ttu-id="112c2-410">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-410">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-411">**pings_sent** 송신된 총 ping 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-411">**pings_sent** Pointer to destination for the total number of pings sent.</span></span>
- <span data-ttu-id="112c2-412">**ping_timeouts** 총 ping 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-412">**ping_timeouts** Pointer to destination for the total number of ping timeouts.</span></span>
- <span data-ttu-id="112c2-413">**ping_threads_suspended** ping 요청에서 일시 중단된 총 스레드 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-413">**ping_threads_suspended** Pointer to destination of the total number of threads suspended on ping requests.</span></span>
- <span data-ttu-id="112c2-414">**ping_responses_received** 수신된 총 ping 응답 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-414">**ping_responses_received** Pointer to estination of the total number of ping responses received.</span></span>
- <span data-ttu-id="112c2-415">**icmp_checksum_errors** 총 ICMP 체크섬 오류 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-415">**icmp_checksum_errors** Pointer to destination of the total number of ICMP checksum errors.</span></span>
- <span data-ttu-id="112c2-416">**icmp_unhandled_messages** 처리되지 않은 총 ICMP 메시지 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-416">**icmp_unhandled_messages** Pointer to estination of the total number of un-handled ICMP messages.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-417">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-417">Return Values</span></span>

- <span data-ttu-id="112c2-418">**NX_SUCCESS**(0x00) ICMP 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-418">**NX_SUCCESS** (0x00) Successful ICMP information retrieval.</span></span>
- <span data-ttu-id="112c2-419">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-419">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-420">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-420">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-421">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-421">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-422">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-422">Allowed From</span></span>

<span data-ttu-id="112c2-423">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-423">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-424">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-424">Preemption Possible</span></span>

<span data-ttu-id="112c2-425">예</span><span class="sxs-lookup"><span data-stu-id="112c2-425">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-426">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-426">Example</span></span>

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-427">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-427">See Also</span></span>

- <span data-ttu-id="112c2-428">nx_icmp_enable, nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="112c2-428">nx_icmp_enable, nx_icmp_ping</span></span>

## <a name="nx_icmp_ping"></a><span data-ttu-id="112c2-429">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="112c2-429">nx_icmp_ping</span></span>

<span data-ttu-id="112c2-430">지정된 IP 주소로 ping 요청을 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-430">Send ping request to specified IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-431">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-431">Prototype</span></span>

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-432">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-432">Description</span></span>

<span data-ttu-id="112c2-433">이 서비스는 지정된 IP 주소로 ping 요청을 송신하고 지정된 시간 동안 ping 응답 메시지를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-433">This service sends a ping request to the specified IP address and waits for the specified amount of time for a ping response message.</span></span> <span data-ttu-id="112c2-434">응답이 수신되지 않는 경우 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-434">If no response is received, an error is returned.</span></span> <span data-ttu-id="112c2-435">응답이 수신되는 경우 response_ptr이 가리키는 변수에 전체 응답 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-435">Otherwise, the entire response message is returned in the variable pointed to by response_ptr.</span></span>

<span data-ttu-id="112c2-436">NX_SUCCESS가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 이 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-436">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet after it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-437">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-437">Parameters</span></span>

- <span data-ttu-id="112c2-438">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-438">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-439">**ip_address** 호스트 바이트 순서대로 표시된 ping할 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-439">**ip_address** IP address, in host byte order, to ping.</span></span> <span data-ttu-id="112c2-440">ping 메시지의 데이터 영역에 대한 데이터 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-440">data Pointer to data area for ping message.</span></span>
- <span data-ttu-id="112c2-441">**data_size** ping 데이터의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-441">**data_size** Number of bytes in the ping data</span></span>
- <span data-ttu-id="112c2-442">**response_ptr** ping 응답 메시지를 반환하는 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-442">**response_ptr** Pointer to packet pointer to return the ping response message in.</span></span>
- <span data-ttu-id="112c2-443">**wait_option** ping 응답 대기 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-443">**wait_option** Defines how long to wait for a ping response.</span></span> <span data-ttu-id="112c2-444">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-444">wait options are defined as follows:</span></span>

  - <span data-ttu-id="112c2-445">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-445">NX_NO_WAIT (0x00000000)</span></span>
  - <span data-ttu-id="112c2-446">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="112c2-447">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-447">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-448">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-448">Return Values</span></span>

- <span data-ttu-id="112c2-449">**NX_SUCCESS**(0x00) ping에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-449">**NX_SUCCESS** (0x00) Successful ping.</span></span> <span data-ttu-id="112c2-450">response_ptr이 가리키는 변수에 응답 메시지 포인터가 배치되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-450">Response message pointer was placed in the variable pointed to by response_ptr.</span></span>
- <span data-ttu-id="112c2-451">**NX_NO_PACKET**(0x01) ping 요청 패킷을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-451">**NX_NO_PACKET** (0x01) Unable to allocate a ping request packet.</span></span>
- <span data-ttu-id="112c2-452">**NX_OVERFLOW**(0x03) 지정된 데이터 영역은 이 IP 인스턴스의 기본 패킷 크기를 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-452">**NX_OVERFLOW** (0x03) Specified data area exceeds the default packet size for this IP instance.</span></span>
- <span data-ttu-id="112c2-453">**NX_NO_RESPONSE**(0x29) 요청된 IP에서 응답하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-453">**NX_NO_RESPONSE** (0x29) Requested IP did not respond.</span></span>
- <span data-ttu-id="112c2-454">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-454">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="112c2-455">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-455">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="112c2-456">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 응답 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-456">**NX_PTR_ERROR** (0x07) Invalid IP or response pointer.</span></span>
- <span data-ttu-id="112c2-457">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-457">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-458">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-458">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-459">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-459">Allowed From</span></span>

<span data-ttu-id="112c2-460">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-460">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-461">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-461">Preemption Possible</span></span>

<span data-ttu-id="112c2-462">예</span><span class="sxs-lookup"><span data-stu-id="112c2-462">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-463">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-463">Example</span></span>

```C
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
    Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
    &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
    address 1.2.3.5 and the response packet is contained in the
    packet pointed to by response_ptr. It should have the same "abcd"
    four bytes of data. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-464">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-464">See Also</span></span>

- <span data-ttu-id="112c2-465">nx_icmp_enable, nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-465">nx_icmp_enable, nx_icmp_info_get</span></span>

## <a name="nx_igmp_enable"></a><span data-ttu-id="112c2-466">nx_igmp_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-466">nx_igmp_enable</span></span>

<span data-ttu-id="112c2-467">IGMP(Internet Group Management Protocol)를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-467">Enable Internet Group Management Protocol (IGMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-468">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-468">Prototype</span></span>

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-469">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-469">Description</span></span>

<span data-ttu-id="112c2-470">이 서비스는 지정된 IP 인스턴스에서 IGMP 구성 요소를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-470">This service enables the IGMP component on the specified IP instance.</span></span>
<span data-ttu-id="112c2-471">IGMP 구성 요소는 IP 멀티캐스트 그룹 관리 작업에 대한 지원을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-471">The IGMP component is responsible for providing support for IP multicast group management operations.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-472">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-472">Parameters</span></span>

- <span data-ttu-id="112c2-473">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-473">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-474">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-474">Return Values</span></span>

- <span data-ttu-id="112c2-475">**NX_SUCCESS**(0x00) IGMP를 사용하도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-475">**NX_SUCCESS** (0x00) Successful IGMP enable.</span></span>
- <span data-ttu-id="112c2-476">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-476">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-477">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-477">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-478">**NX_ALREADY_ENABLED**(0x15) 이 구성 요소는 이미 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-478">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-479">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-479">Allowed From</span></span>

<span data-ttu-id="112c2-480">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-480">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-481">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-481">Preemption Possible</span></span>

<span data-ttu-id="112c2-482">예</span><span class="sxs-lookup"><span data-stu-id="112c2-482">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-483">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-483">Example</span></span>

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-484">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-484">See Also</span></span>

- <span data-ttu-id="112c2-485">nx_igmp_info_get, nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-485">nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="112c2-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join</span><span class="sxs-lookup"><span data-stu-id="112c2-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="112c2-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="112c2-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_info_get"></a><span data-ttu-id="112c2-488">nx_igmp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-488">nx_igmp_info_get</span></span>

<span data-ttu-id="112c2-489">IGMP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-489">Retrieve information about IGMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-490">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-490">Prototype</span></span>

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a><span data-ttu-id="112c2-491">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-491">Description</span></span>

<span data-ttu-id="112c2-492">이 서비스는 지정된 IP 인스턴스의 IGMP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-492">This service retrieves information about IGMP activities for the specified IP instance.</span></span>

<span data-ttu-id="112c2-493">대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-493">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-494">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-494">Parameters</span></span>

- <span data-ttu-id="112c2-495">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-495">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-496">**igmp_reports_sent** 송신된 총 ICMP 보고서 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-496">**igmp_reports_sent** Pointer to destination for the total number of ICMP reports sent.</span></span>
- <span data-ttu-id="112c2-497">**igmp_queries_received** 멀티캐스트 라우터에 수신된 총 쿼리 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-497">**igmp_queries_received** Pointer to destination for the total number of queries received by multicast router.</span></span>
- <span data-ttu-id="112c2-498">**igmp_checksum_errors** 수신 패킷의 총 IGMP 체크섬 오류 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-498">**igmp_checksum_errors** Pointer to destination of the total number of IGMP checksum errors on receive packets.</span></span>
- <span data-ttu-id="112c2-499">**current_groups_joined** 이 IP 인스턴스를 통해 가입된 현재 그룹 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-499">**current_groups_joined** Pointer to destination of the current number of groups joined through this IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-500">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-500">Return Values</span></span>

- <span data-ttu-id="112c2-501">**NX_SUCCESS**(0x00) IGMP 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-501">**NX_SUCCESS** (0x00) Successful IGMP information retrieval.</span></span>
- <span data-ttu-id="112c2-502">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-502">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-503">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-503">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-504">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-504">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-505">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-505">Allowed From</span></span>

<span data-ttu-id="112c2-506">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-506">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-507">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-507">Preemption Possible</span></span>

<span data-ttu-id="112c2-508">예</span><span class="sxs-lookup"><span data-stu-id="112c2-508">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-509">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-509">Example</span></span>

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-510">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-510">See Also</span></span>

- <span data-ttu-id="112c2-511">nx_igmp_enable, nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-511">nx_igmp_enable, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="112c2-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join</span><span class="sxs-lookup"><span data-stu-id="112c2-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="112c2-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="112c2-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="112c2-514">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-514">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="112c2-515">IGMP 루프백을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-515">Disable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-516">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-516">Prototype</span></span>

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-517">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-517">Description</span></span>

<span data-ttu-id="112c2-518">이 서비스는 가입된 모든 후속 멀티캐스트 그룹에 대해 IGMP 루프백을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-518">This service disables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-519">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-519">Parameters</span></span>

- <span data-ttu-id="112c2-520">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-520">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-521">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-521">Return Values</span></span>
- <span data-ttu-id="112c2-522">**NX_SUCCESS**(0x00) IGMP 루프백을 사용하지 않도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-522">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="112c2-523">**NX_NOT_ENABLED**(0x14) IGMP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-523">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="112c2-524">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-524">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-525">**NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-525">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-526">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-526">Allowed From</span></span>

<span data-ttu-id="112c2-527">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-527">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-528">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-528">Preemption Possible</span></span>

<span data-ttu-id="112c2-529">예</span><span class="sxs-lookup"><span data-stu-id="112c2-529">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-530">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-530">Example</span></span>

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-531">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-531">See Also</span></span>

- <span data-ttu-id="112c2-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,</span></span>
- <span data-ttu-id="112c2-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="112c2-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="112c2-534">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="112c2-534">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="112c2-535">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-535">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="112c2-536">IGMP 루프백을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-536">Enable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-537">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-537">Prototype</span></span>

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-538">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-538">Description</span></span>

<span data-ttu-id="112c2-539">이 서비스는 가입된 모든 후속 멀티캐스트 그룹에 대해 IGMP 루프백을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-539">This service enables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-540">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-540">Parameters</span></span>

- <span data-ttu-id="112c2-541">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-541">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-542">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-542">Return Values</span></span>
- <span data-ttu-id="112c2-543">**NX_SUCCESS**(0x00) IGMP 루프백을 사용하지 않도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-543">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="112c2-544">**NX_NOT_ENABLED**(0x14) IGMP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-544">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="112c2-545">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-545">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-546">**NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-546">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-547">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-547">Allowed From</span></span>

<span data-ttu-id="112c2-548">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-548">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-549">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-549">Preemption Possible</span></span>

<span data-ttu-id="112c2-550">예</span><span class="sxs-lookup"><span data-stu-id="112c2-550">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-551">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-551">Example</span></span>

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-552">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-552">See Also</span></span>

- <span data-ttu-id="112c2-553">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-553">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="112c2-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="112c2-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="112c2-555">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="112c2-555">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_interface_join"></a><span data-ttu-id="112c2-556">nx_igmp_multicast_interface_join</span><span class="sxs-lookup"><span data-stu-id="112c2-556">nx_igmp_multicast_interface_join</span></span>

<span data-ttu-id="112c2-557">인터페이스를 통해 IP 인스턴스를 지정된 멀티캐스트 그룹에 가입합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-557">Join IP instance to specified multicast group via an interface</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-558">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-558">Prototype</span></span>

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="112c2-559">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-559">Description</span></span>

<span data-ttu-id="112c2-560">이 서비스는 지정된 네트워크 인터페이스를 통해 IP 인스턴스를 지정된 멀티캐스트 그룹에 가입합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-560">This service joins an IP instance to the specified multicast group via a specified network interface.</span></span> <span data-ttu-id="112c2-561">동일한 그룹이 가입된 횟수를 추적하도록 내부 카운터가 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-561">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="112c2-562">멀티캐스트 그룹에 가입한 후에는 IGMP 구성 요소가 지정된 네트워크 인터페이스를 통해 이 그룹 주소를 사용하는 IP 패킷의 수신을 허용하며 이 IP가 이 멀티캐스트 그룹의 멤버임을 라우터에 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-562">After joining the multicast group, the IGMP component will allow reception of IP packets with this group address via the specified network interface and also report to routers that this IP is a member of this multicast group.</span></span> <span data-ttu-id="112c2-563">IGMP 멤버 자격 가입, 보고, 탈퇴 메시지도 지정된 네트워크 인터페이스를 통해 송신됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-563">The IGMP membership join, report, and leave messages are also sent via the specified network interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-564">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-564">Parameters</span></span>

- <span data-ttu-id="112c2-565">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-565">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-566">**group_address** 호스트 바이트 순서대로 표시된 가입할 클래스 D IP 멀티캐스트 그룹 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-566">**group_address** Class D IP multicast group address to join in host byte order.</span></span>
- <span data-ttu-id="112c2-567">**interface_index** NetX 인스턴스에 연결된 인터페이스 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-567">**interface_index** Index of the Interface attached to the NetX instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-568">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-568">Return Values</span></span>

- <span data-ttu-id="112c2-569">**NX_SUCCESS**(0x00) 멀티캐스트 그룹 가입에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-569">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="112c2-570">**NX_NO_MORE_ENTRIES**(0x17) 멀티캐스트 그룹을 더 이상 가입할 수 없습니다. 최댓값이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-570">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="112c2-571">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-571">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-572">**NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-572">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="112c2-573">**NX_IP_ADDRESS_ERROR**(0x21) 제공된 멀티캐스트 그룹 주소가 잘못된 클래스 D 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-573">**NX_IP_ADDRESS_ERROR** (0x21) Multicast group address provided is not a valid class D address.</span></span>
- <span data-ttu-id="112c2-574">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-574">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-575">**NX_NOT_ENABLED**(0x14) IP 멀티캐스트 지원이 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-575">**NX_NOT_ENABLED** (0x14) IP multicast support is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-576">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-576">Allowed From</span></span>

<span data-ttu-id="112c2-577">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-577">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-578">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-578">Preemption Possible</span></span>

<span data-ttu-id="112c2-579">예</span><span class="sxs-lookup"><span data-stu-id="112c2-579">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-580">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-580">Example</span></span>

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-581">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-581">See Also</span></span>

- <span data-ttu-id="112c2-582">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-582">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="112c2-583">nx_igmp_loopback_enable, nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="112c2-583">nx_igmp_loopback_enable, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="112c2-584">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="112c2-584">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_join"></a><span data-ttu-id="112c2-585">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="112c2-585">nx_igmp_multicast_join</span></span>

<span data-ttu-id="112c2-586">IP 인스턴스를 지정된 멀티캐스트 그룹에 가입합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-586">Join IP instance to specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-587">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-587">Prototype</span></span>

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="112c2-588">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-588">Description</span></span>

<span data-ttu-id="112c2-589">이 서비스는 IP 인스턴스를 지정된 멀티캐스트 그룹에 가입합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-589">This service joins an IP instance to the specified multicast group.</span></span> <span data-ttu-id="112c2-590">동일한 그룹이 가입된 횟수를 추적하도록 내부 카운터가 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-590">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="112c2-591">호스트가 그룹을 가입하려는 것을 나타내는, 네트워크에서 송신된 첫 번째 가입 요청인 경우 드라이버에서 IGMP 보고서 송신 명령이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-591">The driver is commanded to send an IGMP report if this is the first join request out on the network indicating the host's intention to join the group.</span></span> <span data-ttu-id="112c2-592">가입 후에는 IGMP 구성 요소가 이 그룹 주소를 사용하는 IP 패킷을 수신할 수 있으며 이 IP는 해당 멀티캐스트 그룹의 멤버임을 라우터에 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-592">After joining, the IGMP component will allow reception of IP packets with this group address and report to routers that this IP is a member of this multicast group.</span></span>

> [!NOTE]
> <span data-ttu-id="112c2-593">기본 디바이스가 아닌 디바이스에서 멀티캐스트 그룹을 가입하려면 **nx_igmp_multicast_interface_join** 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-593">*To join a multicast group on a non-primary device, use the service **nx_igmp_multicast_interface_join.***</span></span>

- <span data-ttu-id="112c2-594">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="112c2-594">**Parameters**</span></span>

- <span data-ttu-id="112c2-595">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-595">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-596">**group_address** 가입할 클래스 D IP 멀티캐스트 그룹 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-596">**group_address** Class D IP multicast group address to join.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-597">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-597">Return Values</span></span>

- <span data-ttu-id="112c2-598">**NX_SUCCESS**(0x00) 멀티캐스트 그룹 가입에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-598">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="112c2-599">**NX_NO_MORE_ENTRIES**(0x17) 멀티캐스트 그룹을 더 이상 가입할 수 없습니다. 최댓값이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-599">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="112c2-600">**NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-600">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="112c2-601">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 그룹 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-601">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="112c2-602">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-602">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-603">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-603">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-604">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-604">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-605">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-605">Allowed From</span></span>

<span data-ttu-id="112c2-606">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-606">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-607">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-607">Preemption Possible</span></span>

<span data-ttu-id="112c2-608">예</span><span class="sxs-lookup"><span data-stu-id="112c2-608">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-609">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-609">Example</span></span>

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-610">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-610">See Also</span></span>

- <span data-ttu-id="112c2-611">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-611">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="112c2-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join</span><span class="sxs-lookup"><span data-stu-id="112c2-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="112c2-613">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="112c2-613">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="112c2-614">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="112c2-614">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="112c2-615">IP 인스턴스가 지정된 멀티캐스트 그룹에서 탈퇴하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-615">Cause IP instance to leave specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-616">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-616">Prototype</span></span>

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="112c2-617">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-617">Description</span></span>

<span data-ttu-id="112c2-618">이 서비스를 사용하면 탈퇴 요청 수와 가입 요청 수가 일치하는 경우 IP 인스턴스가 지정된 멀티캐스트 그룹에서 탈퇴하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-618">This service causes an IP instance to leave the specified multicast group, if the number of leave requests matches the number of join requests.</span></span> <span data-ttu-id="112c2-619">일치하지 않으면 내부 가입 수만 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-619">Otherwise, the internal join count is simply decremented.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-620">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-620">Parameters</span></span>

- <span data-ttu-id="112c2-621">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-621">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-622">**group_address** 나갈 멀티캐스트 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-622">**group_address** Multicast group to leave.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-623">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-623">Return Values</span></span>

- <span data-ttu-id="112c2-624">**NX_SUCCESS**(0x00) 멀티캐스트 그룹 가입에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-624">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="112c2-625">**NX_ENTRY_NOT_FOUND**(0x16) 이전 가입 요청을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-625">**NX_ENTRY_NOT_FOUND** (0x16) Previous join request was not found.</span></span>
- <span data-ttu-id="112c2-626">**NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-626">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="112c2-627">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 그룹 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-627">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="112c2-628">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-628">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-629">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-629">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-630">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-630">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-631">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-631">Allowed From</span></span>

<span data-ttu-id="112c2-632">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-632">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-633">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-633">Preemption Possible</span></span>

<span data-ttu-id="112c2-634">예</span><span class="sxs-lookup"><span data-stu-id="112c2-634">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-635">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-635">Example</span></span>

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a><span data-ttu-id="112c2-636">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-636">See Also</span></span>

- <span data-ttu-id="112c2-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="112c2-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join</span><span class="sxs-lookup"><span data-stu-id="112c2-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="112c2-639">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="112c2-639">nx_igmp_multicast_join</span></span>

## <a name="nx_ip_address_change_notifiy"></a><span data-ttu-id="112c2-640">nx_ip_address_change_notifiy</span><span class="sxs-lookup"><span data-stu-id="112c2-640">nx_ip_address_change_notifiy</span></span>

<span data-ttu-id="112c2-641">IP 주소가 변경되면 애플리케이션에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-641">Notify application if IP address changes</span></span>


### <a name="prototype"></a><span data-ttu-id="112c2-642">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-642">Prototype</span></span>

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a><span data-ttu-id="112c2-643">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-643">Description</span></span>

<span data-ttu-id="112c2-644">이 서비스는 IP 주소가 변경될 때마다 호출되는 애플리케이션 알림 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-644">This service registers an application notification function that is called whenever the IP address is changed.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-645">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-645">Parameters</span></span>

- <span data-ttu-id="112c2-646">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-646">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-647">**change_notify** IP 변경 알림 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-647">**change_notify** Pointer to IP change notification function.</span></span> <span data-ttu-id="112c2-648">이 매개 변수가 NX_NULL이면 IP 주소 변경 알림이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-648">If this parameter is NX_NULL, IP address change notification is disabled.</span></span>
- <span data-ttu-id="112c2-649">**additional_info** IP 주소가 변경되면 알림 함수에도 제공되는 선택적 추가 정보에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-649">**additional_info** Pointer to optional additional information that is also supplied to the notification function when the IP address is changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-650">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-650">Return Values</span></span>

- <span data-ttu-id="112c2-651">**NX_SUCCESS**(0x00) IP 주소 변경 알림에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-651">**NX_SUCCESS** (0x00) Successful IP address change notification.</span></span>
- <span data-ttu-id="112c2-652">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-652">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-653">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-653">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-654">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-654">Allowed From</span></span>

<span data-ttu-id="112c2-655">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-655">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-656">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-656">Preemption Possible</span></span>

<span data-ttu-id="112c2-657">예</span><span class="sxs-lookup"><span data-stu-id="112c2-657">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-658">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-658">Example</span></span>

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-659">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-659">See Also</span></span>

- <span data-ttu-id="112c2-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,</span></span>
- <span data-ttu-id="112c2-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="112c2-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="112c2-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="112c2-664">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-664">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_address_get"></a><span data-ttu-id="112c2-665">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="112c2-665">nx_ip_address_get</span></span>

<span data-ttu-id="112c2-666">IP 주소 및 네트워크 마스크를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-666">Retrieve IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-667">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-667">Prototype</span></span>

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="112c2-668">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-668">Description</span></span>

<span data-ttu-id="112c2-669">이 서비스는 기본 네트워크 인터페이스의 IP 주소 및 해당 서브넷 마스크를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-669">This service retrieves IP address and its subnet mask of the primary network interface.</span></span>

<span data-ttu-id="112c2-670">\*보조 디바이스에 대한 정보를 가져오려면 다음 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-670">\*To obtain information of the secondary device, use the service</span></span>
- <span data-ttu-id="112c2-671">**nx_ip_interface_address_get**\*</span><span class="sxs-lookup"><span data-stu-id="112c2-671">**nx_ip_interface_address_get**.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-672">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-672">Parameters</span></span>

- <span data-ttu-id="112c2-673">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-673">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-674">**ip_address** IP 주소 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-674">**ip_address** Pointer to destination for IP address.</span></span>
- <span data-ttu-id="112c2-675">**network_mask** 네트워크 마스크 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-675">**network_mask** Pointer to destination for network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-676">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-676">Return Values</span></span>

- <span data-ttu-id="112c2-677">**NX_SUCCESS**(0x00) IP 주소 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-677">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="112c2-678">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 반환 변수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-678">**NX_PTR_ERROR** (0x07) Invalid IP or return variable pointer.</span></span>
- <span data-ttu-id="112c2-679">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-679">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-680">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-680">Allowed From</span></span>

<span data-ttu-id="112c2-681">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-681">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-682">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-682">Preemption Possible</span></span>

<span data-ttu-id="112c2-683">예</span><span class="sxs-lookup"><span data-stu-id="112c2-683">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-684">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-684">Example</span></span>

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-685">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-685">See Also</span></span>

- <span data-ttu-id="112c2-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="112c2-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,</span></span>
- <span data-ttu-id="112c2-687">nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-687">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="112c2-689">nx_ip_forwarding_enable, nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-689">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="112c2-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="112c2-691">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-691">nx_system_initialize</span></span>

## <a name="nx_ip_address_set"></a><span data-ttu-id="112c2-692">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-692">nx_ip_address_set</span></span>

<span data-ttu-id="112c2-693">IP 주소 및 네트워크 마스크를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-693">Set IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-694">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-694">Prototype</span></span>

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="112c2-695">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-695">Description</span></span>

<span data-ttu-id="112c2-696">이 서비스는 기본 네트워크 인터페이스의 IP 주소 및 네트워크 마스크를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-696">This service sets IP address and network mask for the primary network interface.</span></span>

<span data-ttu-id="112c2-697">보조 디바이스의 IP 주소 및 네트워크 마스크를 설정하려면 **nx_ip_interface_address_set** 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-697">*To set IP address and network mask for the secondary device, use the service **nx_ip_interface_address_set**.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-698">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-698">Parameters</span></span>

- <span data-ttu-id="112c2-699">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-699">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-700">**ip_address** 새 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-700">**ip_address** New IP address.</span></span>
- <span data-ttu-id="112c2-701">**network_mask** 새 네트워크 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-701">**network_mask** New network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-702">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-702">Return Values</span></span>

- <span data-ttu-id="112c2-703">**NX_SUCCESS**(0x00) IP 주소 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-703">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="112c2-704">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-704">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="112c2-705">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-705">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-706">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-706">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-707">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-707">Allowed From</span></span>

<span data-ttu-id="112c2-708">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-708">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-709">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-709">Preemption Possible</span></span>

<span data-ttu-id="112c2-710">예</span><span class="sxs-lookup"><span data-stu-id="112c2-710">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-711">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-711">Example</span></span>

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-712">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-712">See Also</span></span>

- <span data-ttu-id="112c2-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="112c2-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,</span></span>
- <span data-ttu-id="112c2-714">nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-714">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="112c2-716">nx_ip_forwarding_enable, nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-716">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="112c2-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="112c2-718">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-718">nx_system_initialize</span></span>

## <a name="nx_ip_create"></a><span data-ttu-id="112c2-719">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="112c2-719">nx_ip_create</span></span>

<span data-ttu-id="112c2-720">IP 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-720">Create an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-721">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-721">Prototype</span></span>

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="112c2-722">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-722">Description</span></span>

<span data-ttu-id="112c2-723">이 서비스는 사용자 제공 IP 주소 및 네트워크 드라이버를 사용하여 IP 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-723">This service creates an IP instance with the user supplied IP address and network driver.</span></span> <span data-ttu-id="112c2-724">또한 애플리케이션은 내부 패킷 할당에 사용할 IP 인스턴스에 대해 이전에 만든 패킷 풀을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-724">In addition, the application must supply a previously created packet pool for the IP instance to use for internal packet allocation.</span></span> <span data-ttu-id="112c2-725">제공된 애플리케이션 네트워크 드라이버는 이 IP의 스레드가 실행될 때까지 호출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-725">Note that the supplied application network driver is not called until this IP's thread executes.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-726">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-726">Parameters</span></span>

- <span data-ttu-id="112c2-727">**ip_ptr** 새 IP 인스턴스를 만들 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-727">**ip_ptr** Pointer to control block to create a new IP instance.</span></span>
- <span data-ttu-id="112c2-728">**name** 새 IP 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-728">**name** Name of this new IP instance.</span></span>
- <span data-ttu-id="112c2-729">**ip_address** 새 IP 인스턴스의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-729">**ip_address** IP address for this new IP instance.</span></span>
- <span data-ttu-id="112c2-730">**network_mask** 서브넷 및 슈퍼넷 지정에 사용할 IP 주소의 네트워크 부분을 나타내는 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-730">**network_mask** Mask to delineate the network portion of the IP address for sub-netting and super-netting uses.</span></span>
- <span data-ttu-id="112c2-731">**default_pool** 이전에 만든 NetX 패킷 풀의 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-731">**default_pool** Pointer to control block of previously created NetX packet pool.</span></span>
- <span data-ttu-id="112c2-732">**ip_network_driver** IP 패킷 송신 및 수신에 사용되는 사용자 제공 네트워크 드라이버입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-732">**ip_network_driver** User-supplied network driver used to send and receive IP packets.</span></span>
- <span data-ttu-id="112c2-733">**memory_ptr** IP 도우미 스레드 스택 영역의 메모리 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-733">**memory_ptr** Pointer to memory area for the IP helper thread’s stack area.</span></span>
- <span data-ttu-id="112c2-734">**memory_size** IP 도우미 스레드 스택의 메모리 영역 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-734">**memory_size** Number of bytes in the memory area for the IP helper thread’s stack.</span></span>
- <span data-ttu-id="112c2-735">**priority** IP 도우미 스레드 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-735">**priority** Priority of IP helper thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-736">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-736">Return Values</span></span>
- <span data-ttu-id="112c2-737">**NX_SUCCESS**(0x00) IP 인스턴스 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-737">**NX_SUCCESS** (0x00) Successful IP instance creation.</span></span>
- <span data-ttu-id="112c2-738">**NX_NOT_IMPLEMENTED**(0x4A) NetX 라이브러리가 잘못 구성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-738">**NX_NOT_IMPLEMENTED** (0x4A) NetX library is configured incorrectly.</span></span>
- <span data-ttu-id="112c2-739">**NX_PTR_ERROR**(0x07) 잘못된 IP, 네트워크 드라이버 함수 포인터, 패킷 풀 또는 메모리 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-739">**NX_PTR_ERROR** (0x07) Invalid IP, network driver function pointer, packet pool, or memory pointer.</span></span>
- <span data-ttu-id="112c2-740">**NX_SIZE_ERROR**(0x09) 제공된 스택 크기가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-740">**NX_SIZE_ERROR** (0x09) The supplied stack size is too small.</span></span>
- <span data-ttu-id="112c2-741">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-741">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-742">**NX_IP_ADDRESS_ERROR**(0x21) 제공된 IP 주소가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-742">**NX_IP_ADDRESS_ERROR** (0x21) The supplied IP address is invalid.</span></span>
- <span data-ttu-id="112c2-743">**NX_OPTION_ERROR**(0x21) 제공된 IP 스레드 우선 순위가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-743">**NX_OPTION_ERROR** (0x21) The supplied IP thread priority is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-744">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-744">Allowed From</span></span>

<span data-ttu-id="112c2-745">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-745">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-746">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-746">Preemption Possible</span></span>

<span data-ttu-id="112c2-747">예</span><span class="sxs-lookup"><span data-stu-id="112c2-747">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-748">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-748">Example</span></span>

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-749">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-749">See Also</span></span>

- <span data-ttu-id="112c2-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="112c2-751">nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-751">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="112c2-753">nx_ip_forwarding_enable, nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-753">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="112c2-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="112c2-755">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-755">nx_system_initialize</span></span>

## <a name="nx_ip_delete"></a><span data-ttu-id="112c2-756">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-756">nx_ip_delete</span></span>

<span data-ttu-id="112c2-757">이전에 만든 IP 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-757">Delete previously created IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="112c2-758">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-758">Prototype</span></span>

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-759">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-759">Description</span></span>

<span data-ttu-id="112c2-760">이 서비스는 이전에 만든 IP 인스턴스를 삭제하고 IP 인스턴스가 소유하는 모든 시스템 리소스를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-760">This service deletes a previously created IP instance and releases all of the system resources owned by the IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-761">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-761">Parameters</span></span>
- <span data-ttu-id="112c2-762">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-762">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-763">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-763">Return Values</span></span>

- <span data-ttu-id="112c2-764">**NX_SUCCESS**(0x00) IP 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-764">**NX_SUCCESS** (0x00) Successful IP deletion.</span></span>
- <span data-ttu-id="112c2-765">**NX_SOCKETS_BOUND**(0x28) 이 IP 인스턴스는 여전히 UDP 또는 TCP 소켓과 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-765">**NX_SOCKETS_BOUND** (0x28) This IP instance still has UDP or TCP sockets bound to it.</span></span> <span data-ttu-id="112c2-766">IP 인스턴스를 삭제하려면 먼저 모든 소켓을 바인딩 해제하고 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-766">All sockets must be unbound and deleted prior to deleting the IP instance.</span></span>
- <span data-ttu-id="112c2-767">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-767">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-768">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-768">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-769">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-769">Allowed From</span></span>

<span data-ttu-id="112c2-770">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-770">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-771">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-771">Preemption Possible</span></span>

<span data-ttu-id="112c2-772">예</span><span class="sxs-lookup"><span data-stu-id="112c2-772">Yes</span></span>

### <a name="example"></a><span data-ttu-id="112c2-773">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-773">Example</span></span>

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-774">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-774">See Also</span></span>

- <span data-ttu-id="112c2-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="112c2-776">nx_ip_create, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-776">nx_ip_create, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="112c2-778">nx_ip_forwarding_enable, nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-778">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="112c2-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="112c2-780">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-780">nx_system_initialize</span></span>

## <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="112c2-781">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-781">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="112c2-782">네트워크 드라이버에 대해 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-782">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-783">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-783">Prototype</span></span>

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-784">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-784">Description</span></span>

<span data-ttu-id="112c2-785">이 서비스는 ***nx_ip_create*** 호출 중 지정된 애플리케이션의 기본 네트워크 인터페이스 드라이버에 대해 직접 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-785">This service provides a direct interface to the application's primary network interface driver specified during the ***nx_ip_create*** call.</span></span>

<span data-ttu-id="112c2-786">애플리케이션별 명령을 사용하면 NX_LINK_USER_COMMAND 이상의 숫자 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-786">Application-specific commands can be used providing their numeric value is greater than or equal to NX_LINK_USER_COMMAND.</span></span>

<span data-ttu-id="112c2-787">보조 디바이스에 대해 명령을 실행하려면 **nx_ip_driver_interface_direct_command** 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-787">*To issue command for the secondary device, use the **nx_ip_driver_interface_direct_command** service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-788">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-788">Parameters</span></span>

- <span data-ttu-id="112c2-789">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-789">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-790">**command** 숫자 명령 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-790">**command** Numeric command code.</span></span> <span data-ttu-id="112c2-791">표준 명령은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-791">Standard commands are defined as follows:</span></span>

- <span data-ttu-id="112c2-792">NX_LINK_GET_STATUS(10)</span><span class="sxs-lookup"><span data-stu-id="112c2-792">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="112c2-793">NX_LINK_GET_SPEED(11)</span><span class="sxs-lookup"><span data-stu-id="112c2-793">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="112c2-794">NX_LINK_GET_DUPLEX_TYPE(12)</span><span class="sxs-lookup"><span data-stu-id="112c2-794">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="112c2-795">NX_LINK_GET_ERROR_COUNT(13)</span><span class="sxs-lookup"><span data-stu-id="112c2-795">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="112c2-796">NX_LINK_GET_RX_COUNT(14)</span><span class="sxs-lookup"><span data-stu-id="112c2-796">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="112c2-797">NX_LINK_GET_TX_COUNT(15)</span><span class="sxs-lookup"><span data-stu-id="112c2-797">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="112c2-798">NX_LINK_GET_ALLOC_ERRORS(16)</span><span class="sxs-lookup"><span data-stu-id="112c2-798">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="112c2-799">NX_LINK_USER_COMMAND(50)</span><span class="sxs-lookup"><span data-stu-id="112c2-799">NX_LINK_USER_COMMAND (50)</span></span>

- <span data-ttu-id="112c2-800">**return_value_ptr** 호출자의 반환 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-800">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-801">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-801">Return Values</span></span>

- <span data-ttu-id="112c2-802">**NX_SUCCESS**(0x00) 네트워크 드라이버 직접 명령이 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-802">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="112c2-803">**NX_UNHANDLED_COMMAND**(0x44) 처리되지 않거나 구현되지 않은 네트워크 드라이버 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-803">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="112c2-804">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 반환 값 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-804">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="112c2-805">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-805">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-806">**NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-806">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-807">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-807">Allowed From</span></span>

<span data-ttu-id="112c2-808">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-808">Threads</span></span>

- <span data-ttu-id="112c2-809">**가능한 선점**</span><span class="sxs-lookup"><span data-stu-id="112c2-809">**Preemption Possible**</span></span>

<span data-ttu-id="112c2-810">예</span><span class="sxs-lookup"><span data-stu-id="112c2-810">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-811">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-811">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-812">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-812">See Also</span></span>

- <span data-ttu-id="112c2-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="112c2-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="112c2-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="112c2-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="112c2-817">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-817">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_driver_interface_direct_command"></a><span data-ttu-id="112c2-818">nx_ip_driver_interface_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-818">nx_ip_driver_interface_direct_command</span></span>

<span data-ttu-id="112c2-819">네트워크 드라이버에 대해 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-819">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-820">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-820">Prototype</span></span>

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-821">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-821">Description</span></span>

<span data-ttu-id="112c2-822">이 서비스는 IP 인스턴스의 애플리케이션 네트워크 디바이스 드라이버에 대해 직접 명령을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-822">This service provides a direct command to the application's network device driver in the IP instance.</span></span> <span data-ttu-id="112c2-823">애플리케이션별 명령을 사용하면 *NX_LINK_USER_COMMAND* 이상의 숫자 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-823">Application-specific commands can be used providing their numeric value is greater than or equal to *NX_LINK_USER_COMMAND*.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-824">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-824">Parameters</span></span>

- <span data-ttu-id="112c2-825">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-825">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-826">**command** 숫자 명령 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-826">**command** Numeric command code.</span></span> <span data-ttu-id="112c2-827">표준 명령은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-827">Standard commands are defined as follows:</span></span>
- <span data-ttu-id="112c2-828">NX_LINK_GET_STATUS(10)</span><span class="sxs-lookup"><span data-stu-id="112c2-828">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="112c2-829">NX_LINK_GET_SPEED(11)</span><span class="sxs-lookup"><span data-stu-id="112c2-829">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="112c2-830">NX_LINK_GET_DUPLEX_TYPE(12)</span><span class="sxs-lookup"><span data-stu-id="112c2-830">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="112c2-831">NX_LINK_GET_ERROR_COUNT(13)</span><span class="sxs-lookup"><span data-stu-id="112c2-831">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="112c2-832">NX_LINK_GET_RX_COUNT(14)</span><span class="sxs-lookup"><span data-stu-id="112c2-832">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="112c2-833">NX_LINK_GET_TX_COUNT(15)</span><span class="sxs-lookup"><span data-stu-id="112c2-833">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="112c2-834">NX_LINK_GET_ALLOC_ERRORS(16)</span><span class="sxs-lookup"><span data-stu-id="112c2-834">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="112c2-835">NX_LINK_USER_COMMAND(50)</span><span class="sxs-lookup"><span data-stu-id="112c2-835">NX_LINK_USER_COMMAND (50)</span></span>
- <span data-ttu-id="112c2-836">**interface_index** 명령을 송신해야 하는 대상 네트워크 인터페이스 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-836">**interface_index** Index of the network interface the command should be sent to.</span></span>
- <span data-ttu-id="112c2-837">**return_value_ptr** 호출자의 반환 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-837">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-838">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-838">Return Values</span></span>
- <span data-ttu-id="112c2-839">**NX_SUCCESS**(0x00) 네트워크 드라이버 직접 명령이 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-839">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="112c2-840">**NX_UNHANDLED_COMMAND**(0x44) 처리되지 않거나 구현되지 않은 네트워크 드라이버 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-840">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="112c2-841">**NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-841">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index</span></span>
- <span data-ttu-id="112c2-842">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 반환 값 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-842">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="112c2-843">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-843">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-844">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-844">Allowed From</span></span>

<span data-ttu-id="112c2-845">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-845">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-846">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-846">Preemption Possible</span></span>

<span data-ttu-id="112c2-847">예</span><span class="sxs-lookup"><span data-stu-id="112c2-847">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-848">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-848">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;
    status = nx_ip_driver_interface_direct_command(&ip_0,
    NX_LINK_GET_STATUS,
    interface_index,
    &link_status);
/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-849">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-849">See Also</span></span>

- <span data-ttu-id="112c2-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="112c2-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="112c2-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="112c2-854">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-854">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="112c2-855">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-855">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="112c2-856">IP 패킷 전달을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-856">Disable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-857">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-857">Prototype</span></span>

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-858">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-858">Description</span></span>

<span data-ttu-id="112c2-859">이 서비스는 NetX IP 구성 요소 내부에서 IP 패킷 전달을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-859">This service disables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="112c2-860">IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-860">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-861">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-861">Parameters</span></span>

- <span data-ttu-id="112c2-862">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-862">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-863">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-863">Return Values</span></span>

- <span data-ttu-id="112c2-864">**NX_SUCCESS**(0x00) IP 전달을 사용하지 않도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-864">**NX_SUCCESS** (0x00) Successful IP forwarding disable.</span></span>
- <span data-ttu-id="112c2-865">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-865">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-866">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-866">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-867">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-867">Allowed From</span></span>

<span data-ttu-id="112c2-868">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="112c2-868">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-869">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-869">Preemption Possible</span></span>

<span data-ttu-id="112c2-870">예</span><span class="sxs-lookup"><span data-stu-id="112c2-870">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-871">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-871">Example</span></span>

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-872">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-872">See Also</span></span>

- <span data-ttu-id="112c2-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="112c2-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="112c2-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="112c2-877">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-877">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="112c2-878">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-878">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="112c2-879">IP 패킷 전달을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-879">Enable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-880">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-880">Prototype</span></span>

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-881">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-881">Description</span></span>

<span data-ttu-id="112c2-882">이 서비스는 NetX IP 구성 요소 내부에서 IP 패킷 전달을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-882">This service enables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="112c2-883">IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-883">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-884">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-884">Parameters</span></span>

- <span data-ttu-id="112c2-885">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-885">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-886">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-886">Return Values</span></span>
- <span data-ttu-id="112c2-887">**NX_SUCCESS**(0x00) IP 전달을 사용하도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-887">**NX_SUCCESS** (0x00) Successful IP forwarding enable.</span></span>
- <span data-ttu-id="112c2-888">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-888">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-889">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-889">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-890">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-890">Allowed From</span></span>

<span data-ttu-id="112c2-891">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="112c2-891">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-892">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-892">Preemption Possible</span></span>

<span data-ttu-id="112c2-893">예</span><span class="sxs-lookup"><span data-stu-id="112c2-893">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-894">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-894">Example</span></span>

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-895">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-895">See Also</span></span>

- <span data-ttu-id="112c2-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="112c2-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="112c2-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="112c2-900">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-900">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_disable"></a><span data-ttu-id="112c2-901">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-901">nx_ip_fragment_disable</span></span>

<span data-ttu-id="112c2-902">IP 패킷 조각화를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-902">Disable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-903">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-903">Prototype</span></span>

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-904">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-904">Description</span></span>

<span data-ttu-id="112c2-905">이 서비스는 IP 패킷 조각화 및 리어셈블 기능을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-905">This service disables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="112c2-906">이 서비스는 리어셈블 대기 중인 패킷이 있는 경우 해당 패킷을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-906">For packets waiting to be reassembled, this service releases these packets.</span></span> <span data-ttu-id="112c2-907">IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-907">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-908">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-908">Parameters</span></span>

- <span data-ttu-id="112c2-909">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-909">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-910">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-910">Return Values</span></span>
- <span data-ttu-id="112c2-911">**NX_SUCCESS**(0x00) IP 조각화를 사용하지 않도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-911">**NX_SUCCESS** (0x00) Successful IP fragment disable.</span></span>
- <span data-ttu-id="112c2-912">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-912">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-913">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-913">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-914">**NX_NOT_ENABLED**(0x14) IP 인스턴스에서 IP 조각화가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-914">**NX_NOT_ENABLED** (0x14) IP Fragmentation is not enabled on the IP instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-915">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-915">Allowed From</span></span>

<span data-ttu-id="112c2-916">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-916">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-917">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-917">Preemption Possible</span></span>

<span data-ttu-id="112c2-918">예</span><span class="sxs-lookup"><span data-stu-id="112c2-918">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-919">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-919">Example</span></span>

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-920">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-920">See Also</span></span>

- <span data-ttu-id="112c2-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="112c2-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="112c2-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="112c2-925">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-925">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_enable"></a><span data-ttu-id="112c2-926">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-926">nx_ip_fragment_enable</span></span>

<span data-ttu-id="112c2-927">IP 패킷 조각화를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-927">Enable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-928">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-928">Prototype</span></span>

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-929">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-929">Description</span></span>

<span data-ttu-id="112c2-930">이 서비스는 IP 패킷 조각화 및 리어셈블 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-930">This service enables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="112c2-931">IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-931">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-932">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-932">Parameters</span></span>

- <span data-ttu-id="112c2-933">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-933">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-934">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-934">Return Values</span></span>

- <span data-ttu-id="112c2-935">**NX_SUCCESS**(0x00) IP 조각화를 사용하도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-935">**NX_SUCCESS** (0x00) Successful IP fragment enable.</span></span>
- <span data-ttu-id="112c2-936">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-936">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-937">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-937">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-938">**NX_NOT_ENABLED**(0x14) NetX에 IP 조각화 기능이 컴파일되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-938">**NX_NOT_ENABLED** (0x14) IP Fragmentation features is not compiled into NetX.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-939">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-939">Allowed From</span></span>

<span data-ttu-id="112c2-940">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-940">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-941">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-941">Preemption Possible</span></span>

<span data-ttu-id="112c2-942">예</span><span class="sxs-lookup"><span data-stu-id="112c2-942">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-943">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-943">Example</span></span>

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-944">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-944">See Also</span></span>

- <span data-ttu-id="112c2-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="112c2-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="112c2-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,</span></span>
- <span data-ttu-id="112c2-949">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-949">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="112c2-950">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-950">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="112c2-951">게이트웨이 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-951">Set Gateway IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-952">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-952">Prototype</span></span>

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a><span data-ttu-id="112c2-953">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-953">Description</span></span>

<span data-ttu-id="112c2-954">이 서비스는 IP 게이트웨이 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-954">This service sets the IP gateway IP address.</span></span> <span data-ttu-id="112c2-955">전송을 위한 네트워크 외부 트래픽은 모두 이 게이트웨이로 라우트됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-955">All out-of-network traffic are routed to this gateway for transmission.</span></span> <span data-ttu-id="112c2-956">게이트웨이는 네트워크 인터페이스 중 하나를 통해 직접 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-956">The gateway must be directly accessible through one of the network interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-957">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-957">Parameters</span></span>

- <span data-ttu-id="112c2-958">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-958">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-959">**ip_address** 게이트웨이 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-959">**ip_address** IP address of the gateway.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-960">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-960">Return Values</span></span>

- <span data-ttu-id="112c2-961">**NX_SUCCESS**(0x00) 게이트웨이 IP 주소 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-961">**NX_SUCCESS** (0x00) Successful Gateway IP address set.</span></span>
- <span data-ttu-id="112c2-962">**NX_PTR_ERROR**(0x07) 잘못된 IP 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-962">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="112c2-963">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-963">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="112c2-964">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-964">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-965">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-965">Allowed From</span></span>

<span data-ttu-id="112c2-966">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-966">Initialization, thread</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-967">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-967">Preemption Possible</span></span>

<span data-ttu-id="112c2-968">예</span><span class="sxs-lookup"><span data-stu-id="112c2-968">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-969">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-969">Example</span></span>

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a><span data-ttu-id="112c2-970">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-970">See Also</span></span>

- <span data-ttu-id="112c2-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_info_get"></a><span data-ttu-id="112c2-972">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-972">nx_ip_info_get</span></span>

<span data-ttu-id="112c2-973">IP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-973">Retrieve information about IP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-974">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-974">Prototype</span></span>

```C
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```

### <a name="description"></a><span data-ttu-id="112c2-975">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-975">Description</span></span>

<span data-ttu-id="112c2-976">이 서비스는 지정된 IP 인스턴스의 IP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-976">This service retrieves information about IP activities for the specified IP instance.</span></span>

<span data-ttu-id="112c2-977">대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-977">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-978">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-978">Parameters</span></span>

- <span data-ttu-id="112c2-979">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-979">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-980">**ip_total_packets_sent** 송신된 총 IP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-980">**ip_total_packets_sent** Pointer to destination for the total number of IP packets sent.</span></span>
- <span data-ttu-id="112c2-981">**ip_total_bytes_sent** 송신된 총 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-981">**ip_total_bytes_sent** Pointer to destination for the total number of bytes sent.</span></span>
- <span data-ttu-id="112c2-982">**ip_total_packets_received** 총 IP 수신 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-982">**ip_total_packets_received** Pointer to destination of the total number of IP receive packets.</span></span>
- <span data-ttu-id="112c2-983">**ip_total_bytes_received** 수신된 총 IP 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-983">**ip_total_bytes_received** Pointer to destination of the total number of IP bytes received.</span></span>
- <span data-ttu-id="112c2-984">**ip_invalid_packets** 잘못된 총 IP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-984">**ip_invalid_packets** Pointer to destination of the total number of invalid IP packets.</span></span>
- <span data-ttu-id="112c2-985">**ip_receive_packets_dropped** 삭제된 총 수신 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-985">**ip_receive_packets_dropped** Pointer to destination of the total number of receive packets dropped.</span></span>
- <span data-ttu-id="112c2-986">**ip_receive_checksum_errors** 수신 패킷의 총 체크섬 오류 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-986">**ip_receive_checksum_errors** Pointer to destination of the total number of checksum errors in receive packets.</span></span>
- <span data-ttu-id="112c2-987">**ip_send_packets_dropped** 삭제된 총 송신 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-987">**ip_send_packets_dropped** Pointer to destination of the total number of send packets dropped.</span></span>
- <span data-ttu-id="112c2-988">**ip_total_fragments_sent** 송신된 총 조각 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-988">**ip_total_fragments_sent** Pointer to destination of the total number of fragments sent.</span></span>
- <span data-ttu-id="112c2-989">**ip_total_fragments_received** 수신된 총 조각 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-989">**ip_total_fragments_received** Pointer to destination of the total number of fragments received.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-990">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-990">Return Values</span></span>

- <span data-ttu-id="112c2-991">**NX_SUCCESS**(0x00) IP 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-991">**NX_SUCCESS** (0x00) Successful IP information retrieval.</span></span>
- <span data-ttu-id="112c2-992">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-992">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-993">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-993">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-994">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-994">Allowed From</span></span>

<span data-ttu-id="112c2-995">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-995">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-996">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-996">Preemption Possible</span></span>

<span data-ttu-id="112c2-997">예</span><span class="sxs-lookup"><span data-stu-id="112c2-997">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-998">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-998">Example</span></span>

```C
/* Retrieve IP information from previously created IP
Instance 0. */
status = nx_ip_info_get(&ip_0,
    &ip_total_packets_sent,
    &ip_total_bytes_sent,
    &ip_total_packets_received,
    &ip_total_bytes_received,
    &ip_invalid_packets,
    &ip_receive_packets_dropped,
    &ip_receive_checksum_errors,
    &ip_send_packets_dropped,
    &ip_total_fragments_sent,
    &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-999">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-999">See Also</span></span>

- <span data-ttu-id="112c2-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="112c2-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="112c2-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="112c2-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_interface_address_get"></a><span data-ttu-id="112c2-1005">nx_ip_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1005">nx_ip_interface_address_get</span></span>

<span data-ttu-id="112c2-1006">인터페이스 IP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1006">Retrieve interface IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1007">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1007">Prototype</span></span>

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="112c2-1008">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1008">Description</span></span>

<span data-ttu-id="112c2-1009">이 서비스는 지정된 네트워크 인터페이스의 IP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1009">This service retrieves the IP address of a specified network interface.</span></span>

<span data-ttu-id="112c2-1010">기본 디바이스가 아닌 경우 지정된 디바이스가 이전에 이미 IP 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1010">*The specified device, if not the primary device, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1011">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1011">Parameters</span></span>

- <span data-ttu-id="112c2-1012">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1012">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1013">**interface_index** 인터페이스 인덱스로, IP 인스턴스에 연결된 네트워크 인터페이스의 인덱스와 값이 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1013">**interface_index** Interface index, the same value as the index to the network interface attached to the IP instance.</span></span>
- <span data-ttu-id="112c2-1014">**ip_address** 디바이스 인터페이스 IP 주소 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1014">**ip_address** Pointer to destination for the device interface IP address.</span></span>
- <span data-ttu-id="112c2-1015">**network_mask** 디바이스 인터페이스 네트워크 마스크 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1015">**network_mask** Pointer to destination for the device interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1016">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1016">Return Values</span></span>

- <span data-ttu-id="112c2-1017">**NX_SUCCESS**(0x00) IP 주소 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1017">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="112c2-1018">**NX_INVALID_INTERFACE**(0x4C) 지정된 네트워크 인터페이스가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1018">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="112c2-1019">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1019">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-1020">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1020">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1021">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1021">Allowed From</span></span>

<span data-ttu-id="112c2-1022">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1022">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1023">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1023">Preemption Possible</span></span>

<span data-ttu-id="112c2-1024">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1024">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1025">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1025">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1026">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1026">See Also</span></span>

- <span data-ttu-id="112c2-1027">nx_ip_interface_address_set, nx_ip_interface_attach</span><span class="sxs-lookup"><span data-stu-id="112c2-1027">nx_ip_interface_address_set, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="112c2-1028">nx_ip_interface_info_get, nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-1028">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="112c2-1029">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1029">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_address_set"></a><span data-ttu-id="112c2-1030">nx_ip_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1030">nx_ip_interface_address_set</span></span>

<span data-ttu-id="112c2-1031">인터페이스 IP 주소 및 네트워크 마스크를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1031">Set interface IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1032">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1032">Prototype</span></span>

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="112c2-1033">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1033">Description</span></span>

<span data-ttu-id="112c2-1034">이 서비스는 지정된 IP 인터페이스의 IP 주소 및 네트워크 마스크를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1034">This service sets the IP address and network mask for the specified IP interface.</span></span>

<span data-ttu-id="112c2-1035">지정된 인터페이스가 이전에 이미 IP 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1035">*The specified interface must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1036">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1036">Parameters</span></span>

- <span data-ttu-id="112c2-1037">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1037">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1038">**interface_index** NetX 인스턴스에 연결된 인터페이스 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1038">**interface_index** Index of the interface attached to the NetX instance.</span></span>
- <span data-ttu-id="112c2-1039">**ip_address** 새 네트워크 인터페이스 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1039">**ip_address** New network interface IP address.</span></span>
- <span data-ttu-id="112c2-1040">**network_mask** 새 인터페이스 네트워크 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1040">**network_mask** New interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1041">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1041">Return Values</span></span>

- <span data-ttu-id="112c2-1042">**NX_SUCCESS**(0x00) IP 주소 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1042">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="112c2-1043">**NX_INVALID_INTERFACE**(0x4C) 지정된 네트워크 인터페이스가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1043">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="112c2-1044">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1044">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-1045">**NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1045">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="112c2-1046">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1046">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1047">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1047">Allowed From</span></span>

<span data-ttu-id="112c2-1048">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1048">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1049">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1049">Preemption Possible</span></span>

<span data-ttu-id="112c2-1050">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1050">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1051">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1051">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1052">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1052">See Also</span></span>

- <span data-ttu-id="112c2-1053">nx_ip_interface_address_get, nx_ip_interface_attach</span><span class="sxs-lookup"><span data-stu-id="112c2-1053">nx_ip_interface_address_get, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="112c2-1054">nx_ip_interface_info_get, nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-1054">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="112c2-1055">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1055">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_attach"></a><span data-ttu-id="112c2-1056">nx_ip_interface_attach</span><span class="sxs-lookup"><span data-stu-id="112c2-1056">nx_ip_interface_attach</span></span>

<span data-ttu-id="112c2-1057">IP 인스턴스에 네트워크 인터페이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1057">Attach network interface to IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1058">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1058">Prototype</span></span>

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="112c2-1059">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1059">Description</span></span>

<span data-ttu-id="112c2-1060">이 서비스는 IP 인터페이스에 실제 네트워크 인터페이스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1060">This service adds a physical network interface to the IP interface.</span></span> <span data-ttu-id="112c2-1061">IP 인스턴스는 기본 인터페이스를 사용하여 만들어지므로 각각의 추가 인터페이스는 기본 인터페이스에 대한 보조 인스턴스가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1061">Note the IP instance is created with the primary interface so each additional interface is secondary to the primary interface.</span></span> <span data-ttu-id="112c2-1062">IP 인스턴스에 연결된 총 네트워크 인터페이스 수(기본 인터페이스 포함)는 **NX_MAX_PHYSICAL_INTERFACES** 를 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1062">The total number of network interfaces attached to the IP instance (including the primary interface) cannot exceed **NX_MAX_PHYSICAL_INTERFACES**.</span></span>

<span data-ttu-id="112c2-1063">IP 스레드가 아직 실행되지 않은 경우 모든 실제 인터페이스를 초기화하는 IP 스레드 시작 프로세스의 일부로 보조 인터페이스가 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1063">If the IP thread has not been running yet, the secondary interfaces will be initialized as part of the IP thread startup process that initializes all physical interfaces.</span></span>

<span data-ttu-id="112c2-1064">IP 스레드가 아직 실행되고 있지 않으면 보조 인터페이스가 ***nx_ip_interface_attach*** 서비스의 일부로 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1064">If the IP thread is not running yet, the secondary interface is initialized as part of the ***nx_ip_interface_attach*** service.</span></span>

<span data-ttu-id="112c2-1065">ip_ptr은 유효한 NetX IP 구조를 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1065">*ip_ptr must point to a valid NetX IP structure.*</span></span>

- <span data-ttu-id="112c2-1066">IP 인스턴스의 네트워크 인터페이스 수에 대한 **NX_MAX_PHYSICAL_INTERFACES** 를 구성해야 합니다. 기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1066">***NX_MAX_PHYSICAL_INTERFACES** must be configured for the number of network interfaces for the IP instance. The default value is one.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1067">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1067">Parameters</span></span>

- <span data-ttu-id="112c2-1068">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1068">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1069">**interface_name** 인터페이스 이름 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1069">**interface_name** Pointer to interface name string.</span></span>
- <span data-ttu-id="112c2-1070">**ip_address** 호스트 바이트 순서대로 표시된 디바이스 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1070">**ip_address** Device IP address in host byte order.</span></span>
- <span data-ttu-id="112c2-1071">**network_mask** 호스트 바이트 순서대로 표시된 디바이스 네트워크 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1071">**network_mask** Device network mask in host byte order.</span></span>
- <span data-ttu-id="112c2-1072">**ip_link_driver** 인터페이스 이더넷 드라이버입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1072">**ip_link_driver** Ethernet driver for the interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1073">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1073">Return Values</span></span>

- <span data-ttu-id="112c2-1074">**NX_SUCCESS**(0x00) 항목이 고정 라우팅 테이블에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1074">**NX_SUCCESS** (0x00) Entry is added to static routing table.</span></span>
- <span data-ttu-id="112c2-1075">**NX_NO_MORE_ENTRIES**(0x17) 최대 인터페이스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1075">**NX_NO_MORE_ENTRIES** (0x17) Max number of interfaces.</span></span>
- <span data-ttu-id="112c2-1076">**NX_MAX_PHYSICAL_INTERFACES** 를 초과했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1076">**NX_MAX_PHYSICAL_INTERFACES** is exceeded.</span></span>
- <span data-ttu-id="112c2-1077">**NX_DUPLICATED_ENTRY**(0x52) 제공된 IP 주소는 이 IP 인스턴스에서 이미 사용되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1077">**NX_DUPLICATED_ENTRY** (0x52) The supplied IP address is already used on this IP instance.</span></span>
- <span data-ttu-id="112c2-1078">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1078">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-1079">**NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1079">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="112c2-1080">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1080">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1081">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1081">Allowed From</span></span>

<span data-ttu-id="112c2-1082">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1082">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1083">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1083">Preemption Possible</span></span>

<span data-ttu-id="112c2-1084">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1084">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1085">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1085">Example</span></span>

```C
/* Attach secondary device for device IP address 192.168.1.68 with
    the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
    IP_ADDRESS(192,168,1,68),
    0xFFFFFF00UL,
    nx_etherDriver);
/* If status is NX_SUCCESS the interface was successfully added to
    the IP instance interface table. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1086">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1086">See Also</span></span>

- <span data-ttu-id="112c2-1087">nx_ip_interface_address_get, nx_ip_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1087">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="112c2-1088">nx_ip_interface_info_get, nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-1088">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="112c2-1089">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1089">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_info_get"></a><span data-ttu-id="112c2-1090">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1090">nx_ip_interface_info_get</span></span>

<span data-ttu-id="112c2-1091">네트워크 인터페이스 매개 변수를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1091">Retrieve network interface parameters</span></span>


### <a name="prototype"></a><span data-ttu-id="112c2-1092">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1092">Prototype</span></span>

```C
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```

### <a name="description"></a><span data-ttu-id="112c2-1093">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1093">Description</span></span>

<span data-ttu-id="112c2-1094">이 서비스는 지정된 네트워크 인터페이스의 네트워크 매개 변수에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1094">This service retrieves information on network parameters for the specified network interface.</span></span> <span data-ttu-id="112c2-1095">모든 데이터는 호스트 바이트 순서대로 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1095">All data are retrieved in host byte order.</span></span>

<span data-ttu-id="112c2-1096">ip_ptr은 유효한 NetX IP 구조를 가리켜야 합니다. 기본 인터페이스가 아닌 경우 지정된 인터페이스가 이전에 이미 IP 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1096">*ip_ptr must point to a valid NetX IP structure. The specified interface, if not the primary interface, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1097">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1097">Parameters</span></span>

- <span data-ttu-id="112c2-1098">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1098">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1099">**interface_index** 네트워크 인터페이스를 지정하는 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1099">**interface_index** Index specifying network interface.</span></span>
- <span data-ttu-id="112c2-1100">**interface_name** 네트워크 인터페이스 이름이 포함된 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1100">**interface_name** Pointer to the buffer that holds the name of the network interface.</span></span>
- <span data-ttu-id="112c2-1101">**ip_address** 인터페이스 IP 주소 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1101">**ip_address** Pointer to the destination for the IP address of the interface.</span></span>
- <span data-ttu-id="112c2-1102">**network_mask** 네트워크 마스크 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1102">**network_mask** Pointer to destination for network mask.</span></span>
- <span data-ttu-id="112c2-1103">**mtu_size** 이 인터페이스의 최대 전송 단위 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1103">**mtu_size** Pointer to destination for maximum transfer unit for this interface.</span></span>
- <span data-ttu-id="112c2-1104">**physical_address_msw** 디바이스 MAC 주소의 상위 16비트 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1104">**physical_address_msw** Pointer to destination for top 16 bits of the device MAC address.</span></span>
- <span data-ttu-id="112c2-1105">**physical_address_lsw** 디바이스 MAC 주소의 하위 32비트 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1105">**physical_address_lsw** Pointer to destination for lower 32 bits of the device MAC address.</span></span>


### <a name="return-values"></a><span data-ttu-id="112c2-1106">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1106">Return Values</span></span>
- <span data-ttu-id="112c2-1107">**NX_SUCCESS**(0x00) 인터페이스 정보를 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1107">**NX_SUCCESS** (0x00) Interface information has been obtained.</span></span>
- <span data-ttu-id="112c2-1108">**NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1108">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="112c2-1109">**NX_INVALID_INTERFACE**(0x4C) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1109">**NX_INVALID_INTERFACE** (0x4C) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-1110">**NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1110">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1111">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1111">Allowed From</span></span>

<span data-ttu-id="112c2-1112">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1112">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1113">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1113">Preemption Possible</span></span>

<span data-ttu-id="112c2-1114">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1114">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1115">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1115">Example</span></span>

```C
/* Retrieve interface parameters for the specified interface (index
    1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1

status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
    &name_ptr, &ip_address,
    &network_mask,
    &mtu_size,
    &physical_address_msw,
    &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
    successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1116">See Also</span></span>

- <span data-ttu-id="112c2-1117">nx_ip_interface_address_get, nx_ip_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1117">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="112c2-1118">nx_ip_interface_attach, nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-1118">nx_ip_interface_attach, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="112c2-1119">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1119">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_status_check"></a><span data-ttu-id="112c2-1120">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-1120">nx_ip_interface_status_check</span></span>

<span data-ttu-id="112c2-1121">IP 인스턴스의 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1121">Check status of an IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="112c2-1122">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1122">Prototype</span></span>

```C
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-1123">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1123">Description</span></span>

<span data-ttu-id="112c2-1124">이 서비스는 이전에 만든 IP 인스턴스의 네트워크 인터페이스 상태를 확인하고 선택적으로 지정된 상태가 될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1124">This service checks and optionally waits for the specified status of the network interface of a previously created IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1125">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1125">Parameters</span></span>

- <span data-ttu-id="112c2-1126">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1126">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1127">**interface_index** 인터페이스 인덱스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1127">**interface_index** Interface index number</span></span>
- <span data-ttu-id="112c2-1128">**needed_status** 요청된 IP 상태이며 다음과 같이 비트맵 형식으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1128">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
    - <span data-ttu-id="112c2-1129">NX_IP_INITIALIZE_DONE(0x0001)</span><span class="sxs-lookup"><span data-stu-id="112c2-1129">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
    - <span data-ttu-id="112c2-1130">NX_IP_ADDRESS_RESOLVED(0x0002)</span><span class="sxs-lookup"><span data-stu-id="112c2-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
    - <span data-ttu-id="112c2-1131">NX_IP_LINK_ENABLED(0x0004)</span><span class="sxs-lookup"><span data-stu-id="112c2-1131">NX_IP_LINK_ENABLED (0x0004)</span></span>
    - <span data-ttu-id="112c2-1132">NX_IP_ARP_ENABLED(0x0008)</span><span class="sxs-lookup"><span data-stu-id="112c2-1132">NX_IP_ARP_ENABLED (0x0008)</span></span>
    - <span data-ttu-id="112c2-1133">NX_IP_UDP_ENABLED(0x0010)</span><span class="sxs-lookup"><span data-stu-id="112c2-1133">NX_IP_UDP_ENABLED (0x0010)</span></span>
    - <span data-ttu-id="112c2-1134">NX_IP_TCP_ENABLED(0x0020)</span><span class="sxs-lookup"><span data-stu-id="112c2-1134">NX_IP_TCP_ENABLED (0x0020)</span></span>
    - <span data-ttu-id="112c2-1135">NX_IP_IGMP_ENABLED(0x0040)</span><span class="sxs-lookup"><span data-stu-id="112c2-1135">NX_IP_IGMP_ENABLED (0x0040)</span></span>
    - <span data-ttu-id="112c2-1136">NX_IP_RARP_COMPLETE(0x0080)</span><span class="sxs-lookup"><span data-stu-id="112c2-1136">NX_IP_RARP_COMPLETE (0x0080)</span></span>
    - <span data-ttu-id="112c2-1137">NX_IP_INTERFACE_LINK_ENABLED(0x0100)</span><span class="sxs-lookup"><span data-stu-id="112c2-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="112c2-1138">**actual_status** 설정된 실제 비트 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1138">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="112c2-1139">**wait_option** 요청된 상태 비트를 사용할 수 없는 경우 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1139">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="112c2-1140">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1140">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="112c2-1141">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1141">NX_NO_WAIT (0x00000000)</span></span>
    - <span data-ttu-id="112c2-1142">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="112c2-1143">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-1143">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1144">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1144">Return Values</span></span>

- <span data-ttu-id="112c2-1145">**NX_SUCCESS**(0x00) IP 상태 확인에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1145">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="112c2-1146">**NX_NOT_SUCCESSFUL**(0x43) 지정된 시간 제한 내에 상태 요청이 충족되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1146">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="112c2-1147">**NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었거나 잘못된 상태였거나, 실제 상태 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1147">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="112c2-1148">**NX_OPTION_ERROR**(0x0a) 필요한 상태 옵션이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1148">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="112c2-1149">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1149">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-1150">**NX_INVALID_INTERFACE**(0x4C) Interface_index가 범위를 벗어났습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1150">**NX_INVALID_INTERFACE** (0x4C) Interface_index is out of range.</span></span> <span data-ttu-id="112c2-1151">또는 인터페이스가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1151">or the interface is not valid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1152">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1152">Allowed From</span></span>

<span data-ttu-id="112c2-1153">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1153">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1154">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1154">Preemption Possible</span></span>

<span data-ttu-id="112c2-1155">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1155">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1156">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1156">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1157">See Also</span></span>

- <span data-ttu-id="112c2-1158">nx_ip_interface_address_get, nx_ip_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1158">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="112c2-1159">nx_ip_interface_attach, nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1159">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="112c2-1160">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1160">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_link_status_change_notify_set"></a><span data-ttu-id="112c2-1161">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1161">nx_ip_link_status_change_notify_set</span></span>

<span data-ttu-id="112c2-1162">링크 상태 변경 알림 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1162">Set the link status change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1163">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1163">Prototype</span></span>

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a><span data-ttu-id="112c2-1164">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1164">Description</span></span>

<span data-ttu-id="112c2-1165">이 서비스는 링크 상태 변경 알림 콜백 함수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1165">This service configures the link status change notify callback function.</span></span> <span data-ttu-id="112c2-1166">기본 또는 보조 인터페이스 상태가 변경되는 경우(예: IP 주소가 변경되는 경우) 사용자 제공 *link_status_change_notify* 루틴이 호출됩니다. *link_status_change_notify* 가 NULL인 경우 링크 상태 변경 알림 콜백 기능이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1166">The user-supplied *link_status_change_notify* routine is invoked when either the primary or secondary interface status is changed (such as IP address is changed.) If *link_status_change_notify* is NULL, the link status change notify callback feature is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1167">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1167">Parameters</span></span>

- <span data-ttu-id="112c2-1168">**ip_ptr** IP 제어 블록 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1168">**ip_ptr** IP control block pointer</span></span>
- <span data-ttu-id="112c2-1169">**link_status_change_notify** 실제 인터페이스 변경 시 호출되는 사용자 제공 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1169">**link_status_change_notify** User-supplied callback function to be called upon a change to the physical interface.</span></span>


### <a name="return-values"></a><span data-ttu-id="112c2-1170">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1170">Return Values</span></span>

- <span data-ttu-id="112c2-1171">**NX_SUCCESS**(0x00) 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1171">**NX_SUCCESS** (0x00) Successful set</span></span>
- <span data-ttu-id="112c2-1172">**NX_PTR_ERROR**(0x07) 잘못된 IP 제어 블록 포인터 또는 새 물리적 주소 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1172">**NX_PTR_ERROR** (0x07) Invalid IP control block pointer or new physical address pointer</span></span>
- <span data-ttu-id="112c2-1173">**NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1173">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="112c2-1174">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1174">Allowed From</span></span>

<span data-ttu-id="112c2-1175">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1175">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1176">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1176">Preemption Possible</span></span>

<span data-ttu-id="112c2-1177">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1177">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1178">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1178">Example</span></span>

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1179">See Also</span></span>

- <span data-ttu-id="112c2-1180">nx_ip_interface_address_get, nx_ip_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1180">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="112c2-1181">nx_ip_interface_attach, nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1181">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="112c2-1182">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-1182">nx_ip_interface_status_check</span></span>

## <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="112c2-1183">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-1183">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="112c2-1184">원시 패킷 송신/수신을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1184">Disable raw packet sending/receiving</span></span>


### <a name="prototype"></a><span data-ttu-id="112c2-1185">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1185">Prototype</span></span>

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-1186">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1186">Description</span></span>

<span data-ttu-id="112c2-1187">이 서비스는 이 IP 인스턴스의 원시 IP 패킷 전송 및 수신을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1187">This service disables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="112c2-1188">이전에 원시 패킷 서비스를 사용하도록 설정했으며 수신 큐에 원시 패킷이 있는 경우 이 서비스는 수신된 원시 패킷을 모두 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1188">If the raw packet service was previously enabled, and there are raw packets in the receive queue, this service will release any received raw packets.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1189">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1189">Parameters</span></span>

- <span data-ttu-id="112c2-1190">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1190">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1191">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1191">Return Values</span></span>

- <span data-ttu-id="112c2-1192">**NX_SUCCESS**(0x00) IP 원시 패킷을 사용하지 않도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1192">**NX_SUCCESS** (0x00) Successful IP raw packet disable.</span></span>
- <span data-ttu-id="112c2-1193">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1193">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-1194">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1194">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1195">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1195">Allowed From</span></span>

<span data-ttu-id="112c2-1196">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1196">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1197">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1197">Preemption Possible</span></span>

<span data-ttu-id="112c2-1198">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1198">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1199">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1199">Example</span></span>

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1200">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1200">See Also</span></span>

- <span data-ttu-id="112c2-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="112c2-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="112c2-1203">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-1203">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="112c2-1204">원시 패킷 처리를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1204">Enable raw packet processing</span></span>


### <a name="prototype"></a><span data-ttu-id="112c2-1205">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1205">Prototype</span></span>

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-1206">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1206">Description</span></span>

<span data-ttu-id="112c2-1207">이 서비스는 이 IP 인스턴스에 대해 원시 IP 패킷 전송 및 수신을 사용할 수 있도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1207">This service enables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="112c2-1208">수신 TCP, UDP, ICMP 및 IGMP 패킷은 여전히 NetX에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1208">Incoming TCP, UDP, ICMP, and IGMP packets are still processed by NetX.</span></span> <span data-ttu-id="112c2-1209">상위 계층 프로토콜 유형을 알 수 없는 패킷은 원시 패킷 수신 루틴에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1209">Packets with unknown upper layer protocol types are processed by raw packet reception routine.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1210">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1210">Parameters</span></span>

- <span data-ttu-id="112c2-1211">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1211">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1212">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1212">Return Values</span></span>

- <span data-ttu-id="112c2-1213">**NX_SUCCESS**(0x00) IP 원시 패킷을 사용하도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1213">**NX_SUCCESS** (0x00) Successful IP raw packet enable.</span></span>
- <span data-ttu-id="112c2-1214">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1214">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-1215">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1215">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1216">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1216">Allowed From</span></span>

<span data-ttu-id="112c2-1217">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1217">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1218">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1218">Preemption Possible</span></span>

<span data-ttu-id="112c2-1219">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1219">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1220">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1220">Example</span></span>

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1221">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1221">See Also</span></span>

- <span data-ttu-id="112c2-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="112c2-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_interface_send"></a><span data-ttu-id="112c2-1224">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1224">nx_ip_raw_packet_interface_send</span></span>

<span data-ttu-id="112c2-1225">지정된 네트워크 인터페이스를 통해 원시 IP 패킷을 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1225">Send raw IP packet through specified network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1226">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1226">Prototype</span></span>

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="112c2-1227">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1227">Description</span></span>

<span data-ttu-id="112c2-1228">이 서비스는 지정된 로컬 IP 주소를 원본 주소로 사용하고 연결된 네트워크 인터페이스를 통해 원시 IP 패킷을 대상 IP 주소로 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1228">This service sends a raw IP packet to the destination IP address using the specified local IP address as the source address, and through the associated network interface.</span></span> <span data-ttu-id="112c2-1229">이 루틴은 즉시 반환되므로 IP 패킷이 실제로 송신되었는지를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1229">Note that this routine returns immediately, and it is, therefore, not known if the IP packet has actually been sent.</span></span> <span data-ttu-id="112c2-1230">네트워크 드라이버는 전송이 완료되면 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1230">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span> <span data-ttu-id="112c2-1231">이 서비스는 패킷이 실제로 송신되었는지를 알 방법이 없다는 점에서 다른 서비스와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1231">This service differs from other services in that there is no way of knowing if the packet was actually sent.</span></span> <span data-ttu-id="112c2-1232">패킷이 인터넷에서 손실될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1232">It could get lost on the Internet.</span></span>

<span data-ttu-id="112c2-1233">원시 IP 처리는 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1233">*Note that raw IP processing must be enabled.*</span></span>

<span data-ttu-id="112c2-1234">이 서비스는 애플리케이션이 지정된 실제 인터페이스에서 원시 IP 패킷을 송신하도록 허용하는 점을 제외하고는 **nx_ip_raw_packet_send** 와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1234">*This service is similar to **nx_ip_raw_packet_send**, except that this service allows an application to send raw IP packet from a specified physical interfaces.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1235">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1235">Parameters</span></span>

- <span data-ttu-id="112c2-1236">**ip_ptr** 이전에 만든 IP 작업에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1236">**ip_ptr** Pointer to previously created IP task.</span></span>
- <span data-ttu-id="112c2-1237">**packet_ptr** 전송할 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1237">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="112c2-1238">**destination_ip** 패킷을 송신할 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1238">**destination_ip** IP address to send packet.</span></span>
- <span data-ttu-id="112c2-1239">**address_index** 패킷을 송신할 인터페이스 주소 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1239">**address_index** Index of the address of the interface to send packet out on.</span></span>
- <span data-ttu-id="112c2-1240">**type_of_service** 패킷 서비스 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1240">**type_of_service** Type of service for packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1241">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1241">Return Values</span></span>

- <span data-ttu-id="112c2-1242">**NX_SUCCESS**(0x00) 패킷이 성공적으로 전송되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1242">**NX_SUCCESS** (0x00) Packet successfully transmitted.</span></span>
- <span data-ttu-id="112c2-1243">**NX_IP_ADDRESS_ERROR**(0x21) 사용할 수 있는 적절한 발신 인터페이스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1243">**NX_IP_ADDRESS_ERROR** (0x21) No suitable outgoing interface available.</span></span>
- <span data-ttu-id="112c2-1244">**NX_NOT_ENABLED**(0x14) 원시 IP 패킷 처리가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1244">**NX_NOT_ENABLED** (0x14) Raw IP packet processing not enabled.</span></span>
- <span data-ttu-id="112c2-1245">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1245">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-1246">**NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1246">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="112c2-1247">**NX_OPTION_ERROR**(0x0A) 잘못된 유형의 서비스가 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1247">**NX_OPTION_ERROR** (0x0A) Invalid type of service specified.</span></span>
- <span data-ttu-id="112c2-1248">**NX_OVERFLOW**(0x03) 잘못된 패킷 앞에 추가 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1248">**NX_OVERFLOW** (0x03) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="112c2-1249">**NX_UNDERFLOW**(0x02) 잘못된 패킷 앞에 추가 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1249">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="112c2-1250">**NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스 인덱스가 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1250">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1251">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1251">Allowed From</span></span>

<span data-ttu-id="112c2-1252">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1252">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1253">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1253">Preemption Possible</span></span>

<span data-ttu-id="112c2-1254">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1254">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1255">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1255">Example</span></span>

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1256">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1256">See Also</span></span>

- <span data-ttu-id="112c2-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="112c2-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span></span>

## <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="112c2-1259">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-1259">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="112c2-1260">원시 IP 패킷을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1260">Receive raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1261">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1261">Prototype</span></span>

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-1262">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1262">Description</span></span>

<span data-ttu-id="112c2-1263">이 서비스는 지정된 IP 인스턴스에서 원시 IP 패킷을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1263">This service receives a raw IP packet from the specified IP instance.</span></span> <span data-ttu-id="112c2-1264">원시 패킷 수신 큐에 IP 패킷이 있는 경우 첫 번째(가장 오래된) 패킷이 호출자에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1264">If there are IP packets on the raw packet receive queue, the first (oldest) packet is returned to the caller.</span></span> <span data-ttu-id="112c2-1265">그러지 않고 사용할 수 있는 패킷이 없는 경우 대기 옵션에 지정된 대로 호출자가 일시 중단될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1265">Otherwise, if no packets are available, the caller may suspend as specified by the wait option.</span></span>

<span data-ttu-id="112c2-1266">*NX_SUCCESS* 가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 이 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1266">*If NX_SUCCESS, is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1267">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1267">Parameters</span></span>

- <span data-ttu-id="112c2-1268">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1268">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1269">**packet_ptr** 수신된 원시 IP 패킷이 배치될 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1269">**packet_ptr** Pointer to pointer to place the received raw IP packet in.</span></span>
- <span data-ttu-id="112c2-1270">**wait_option** 사용할 수 있는 원시 IP 패킷이 없는 경우 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1270">**wait_option** Defines how the service behaves if there are no raw IP packets available.</span></span> <span data-ttu-id="112c2-1271">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1271">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-1272">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1272">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-1273">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-1274">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-1274">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1275">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1275">Return Values</span></span>

- <span data-ttu-id="112c2-1276">**NX_SUCCESS**(0x00) IP 원시 패킷 수신에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1276">**NX_SUCCESS** (0x00) Successful IP raw packet receive.</span></span>
- <span data-ttu-id="112c2-1277">**NX_NO_PACKET**(0x01) 사용할 수 있는 패킷이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1277">**NX_NO_PACKET** (0x01) No packet was available.</span></span>
- <span data-ttu-id="112c2-1278">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1278">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="112c2-1279">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1279">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="112c2-1280">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 반환 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1280">**NX_PTR_ERROR** (0x07) Invalid IP or return packet pointer.</span></span>
- <span data-ttu-id="112c2-1281">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1281">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1282">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1282">Allowed From</span></span>

<span data-ttu-id="112c2-1283">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1283">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1284">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1284">Preemption Possible</span></span>

<span data-ttu-id="112c2-1285">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1285">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1286">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1286">Example</span></span>

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1287">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1287">See Also</span></span>

- <span data-ttu-id="112c2-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="112c2-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="112c2-1290">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1290">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="112c2-1291">원시 IP 패킷을 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1291">Send raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1292">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1292">Prototype</span></span>

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="112c2-1293">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1293">Description</span></span>

<span data-ttu-id="112c2-1294">이 서비스는 원시 IP 패킷을 대상 IP 주소로 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1294">This service sends a raw IP packet to the destination IP address.</span></span> <span data-ttu-id="112c2-1295">이 루틴은 즉시 반환되므로 IP 패킷이 실제로 송신되었는지를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1295">Note that this routine returns immediately, and it is therefore not known whether the IP packet has actually been sent.</span></span> <span data-ttu-id="112c2-1296">네트워크 드라이버는 전송이 완료되면 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1296">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span>

<span data-ttu-id="112c2-1297">멀티홈 시스템의 경우 NetX는 대상 IP 주소를 사용하여 적절한 네트워크 인터페이스를 찾고 인터페이스의 IP 주소를 원본 주소로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1297">For a multihome system, NetX uses the destination IP address to find an appropriate network interface and uses the IP address of the interface as the source address.</span></span> <span data-ttu-id="112c2-1298">대상 IP 주소가 브로드캐스트 또는 멀티캐스트면 유효한 첫 번째 인터페이스가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1298">If the destination IP address is broadcast or multicast, the first valid interface is used.</span></span> <span data-ttu-id="112c2-1299">이 경우 애플리케이션은 ***nx_ip_raw_packet_interface_send*** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1299">Applications use the ***nx_ip_raw_packet_interface_send*** in this case.</span></span>

<span data-ttu-id="112c2-1300">오류가 반환되지 않는 한 이 호출 후 애플리케이션은 패킷을 해제하면 안 됩니다. 애플리케이션이 패킷을 해제하면 전송 후 네트워크 드라이버가 패킷을 해제하므로 예측할 수 없는 결과가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1300">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1301">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1301">Parameters</span></span>

- <span data-ttu-id="112c2-1302">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1302">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1303">**packet_ptr** 송신할 원시 IP 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1303">**packet_ptr** Pointer to the raw IP packet to send.</span></span>
- <span data-ttu-id="112c2-1304">**destination_ip** 대상 IP 주소로, 특정 호스트 IP 주소나 네트워크 브로드캐스트, 내부 루프백, 멀티캐스트 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1304">**destination_ip** Destination IP address, which can be a specific host IP address, a network broadcast, an internal loop-back, or a multicast address.</span></span>
- <span data-ttu-id="112c2-1305">**type_of_service** 전송할 서비스 유형을 정의합니다. 올바른 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1305">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
- <span data-ttu-id="112c2-1306">NX_IP_NORMAL(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1306">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="112c2-1307">NX_IP_MIN_DELAY(0x00100000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1307">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="112c2-1308">NX_IP_MAX_DATA(0x00080000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1308">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="112c2-1309">NX_IP_MAX_RELIABLE(0x00040000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1309">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="112c2-1310">NX_IP_MIN_COST(0x00020000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1310">NX_IP_MIN_COST (0x00020000)</span></span>


### <a name="return-values"></a><span data-ttu-id="112c2-1311">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1311">Return Values</span></span>

- <span data-ttu-id="112c2-1312">**NX_SUCCESS**(0x00) IP 원시 패킷 송신에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1312">**NX_SUCCESS** (0x00) Successful IP raw packet send initiated.</span></span>
- <span data-ttu-id="112c2-1313">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1313">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="112c2-1314">**NX_NOT_ENABLED**(0x14) 원시 IP 기능이 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1314">**NX_NOT_ENABLED** (0x14) Raw IP feature is not enabled.</span></span>
- <span data-ttu-id="112c2-1315">**NX_OPTION_ERROR**(0x0A) 잘못된 유형의 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1315">**NX_OPTION_ERROR** (0x0A) Invalid type of service.</span></span>
- <span data-ttu-id="112c2-1316">**NX_UNDERFLOW**(0x02) 공간이 부족하여 패킷에서 IP 헤더를 앞에 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1316">**NX_UNDERFLOW** (0x02) Not enough room to prepend an IP header on the packet.</span></span>
- <span data-ttu-id="112c2-1317">**NX_OVERFLOW**(0x03) 패킷 뒤에 추가 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1317">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="112c2-1318">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1318">**NX_PTR_ERROR** (0x07) Invalid IP or packet pointer.</span></span>
- <span data-ttu-id="112c2-1319">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1319">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1320">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1320">Allowed From</span></span>

<span data-ttu-id="112c2-1321">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1321">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1322">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1322">Preemption Possible</span></span>

<span data-ttu-id="112c2-1323">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1323">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1324">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1324">Example</span></span>

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1325">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1325">See Also</span></span>

- <span data-ttu-id="112c2-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="112c2-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send,</span></span>
- <span data-ttu-id="112c2-1328">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1328">nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_static_route_add"></a><span data-ttu-id="112c2-1329">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="112c2-1329">nx_ip_static_route_add</span></span>

<span data-ttu-id="112c2-1330">라우팅 테이블에 고정 경로를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1330">Add static route to the routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1331">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1331">Prototype</span></span>

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a><span data-ttu-id="112c2-1332">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1332">Description</span></span>

<span data-ttu-id="112c2-1333">이 서비스는 고정 라우팅 테이블에 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1333">This service adds an entry to the static routing table.</span></span> <span data-ttu-id="112c2-1334">로컬 네트워크 디바이스 중 하나에서 *next_hop* 주소에 직접 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1334">Note that the *next_hop* address must be directly accessible from one of the local network devices.</span></span>

<span data-ttu-id="112c2-1335">이 서비스를 사용하려면 ip_ptr이 유효한 NetX IP 구조를 가리켜야 하며 NX_ENABLE_IP_STATIC_ROUTING이 정의된 NetX 라이브러리가 빌드되어 있어야 합니다. 기본적으로 NetX는 NX_ENABLE_IP_STATIC_ROUTING이 정의되지 않은 상태로 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1335">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1336">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1336">Parameters</span></span>

- <span data-ttu-id="112c2-1337">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1337">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1338">**network_address** 호스트 바이트 순서대로 표시된 대상 네트워크 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1338">**network_address** Target network address, in host byte order</span></span>
- <span data-ttu-id="112c2-1339">**net_mask** 호스트 바이트 순서대로 표시된 대상 네트워크 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1339">**net_mask** Target network mask, in host byte order</span></span>
- <span data-ttu-id="112c2-1340">**next_hop** 호스트 바이트 순서대로 표시된 대상 네트워크의 다음 홉 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1340">**next_hop** Next hop address for the target network, in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1341">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1341">Return Values</span></span>

- <span data-ttu-id="112c2-1342">**NX_SUCCESS**(0x00) 항목이 고정 라우팅 테이블에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1342">**NX_SUCCESS** (0x00) Entry is added to the static routing table.</span></span>
- <span data-ttu-id="112c2-1343">**NX_OVERFLOW**(0x03) 고정 라우팅 테이블이 꽉 찼습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1343">**NX_OVERFLOW** (0x03) Static routing table is full.</span></span>
- <span data-ttu-id="112c2-1344">**NX_NOT_SUPPORTED**(0x4B) 이 기능은 컴파일되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1344">**NX_NOT_SUPPORTED** (0x4B) This feature is not compiled in.</span></span>
- <span data-ttu-id="112c2-1345">**NX_IP_ADDRESS_ERROR**(0x21) 로컬 인터페이스를 통해 다음 홉에 직접 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1345">**NX_IP_ADDRESS_ERROR** (0x21) Next hop is not directly accessible via local interfaces.</span></span>
- <span data-ttu-id="112c2-1346">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1346">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-1347">**NX_PTR_ERROR**(0x07) 잘못된 ip_ptr 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1347">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1348">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1348">Allowed From</span></span>

<span data-ttu-id="112c2-1349">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1349">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1350">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1350">Preemption Possible</span></span>

<span data-ttu-id="112c2-1351">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1352">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1352">Example</span></span>

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1353">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1353">See Also</span></span>

- <span data-ttu-id="112c2-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_static_route_delete"></a><span data-ttu-id="112c2-1355">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-1355">nx_ip_static_route_delete</span></span>

<span data-ttu-id="112c2-1356">라우팅 테이블에서 고정 경로를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1356">Delete static route from routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1357">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1357">Prototype</span></span>

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a><span data-ttu-id="112c2-1358">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1358">Description</span></span>

<span data-ttu-id="112c2-1359">이 서비스는 고정 라우팅 테이블에서 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1359">This service deletes an entry from the static routing table.</span></span>

<span data-ttu-id="112c2-1360">이 서비스를 사용하려면 ip_ptr이 유효한 NetX IP 구조를 가리켜야 하며 NX_ENABLE_IP_STATIC_ROUTING이 정의된 NetX 라이브러리가 빌드되어 있어야 합니다. 기본적으로 NetX는 NX_ENABLE_IP_STATIC_ROUTING이 정의되지 않은 상태로 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1360">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1361">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1361">Parameters</span></span>

- <span data-ttu-id="112c2-1362">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1362">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1363">**network_address** 호스트 바이트 순서대로 표시된 대상 네트워크 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1363">**network_address** Target network address, in host byte order.</span></span>
- <span data-ttu-id="112c2-1364">**net_mask** 호스트 바이트 순서대로 표시된 대상 네트워크 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1364">**net_mask** Target network mask, in host byte order.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1365">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1365">Allowed From</span></span>

<span data-ttu-id="112c2-1366">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1366">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1367">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1367">Preemption Possible</span></span>

<span data-ttu-id="112c2-1368">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1368">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1369">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1369">Example</span></span>

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1370">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1370">See Also</span></span>

- <span data-ttu-id="112c2-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="112c2-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span></span>

## <a name="nx_ip_status_check"></a><span data-ttu-id="112c2-1372">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-1372">nx_ip_status_check</span></span>

<span data-ttu-id="112c2-1373">IP 인스턴스의 상태를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1373">Check status of an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1374">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1374">Prototype</span></span>

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-1375">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1375">Description</span></span>

<span data-ttu-id="112c2-1376">이 서비스는 이전에 만든 IP 인스턴스의 기본 네트워크 인터페이스 상태를 확인하고 선택적으로 지정된 상태가 될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1376">This service checks and optionally waits for the specified status of the primary network interface of a previously created IP instance.</span></span> <span data-ttu-id="112c2-1377">보조 인터페이스에 대한 상태를 가져오려면 애플리케이션은 ***nx_ip_interface_status_check*** 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1377">To obtain status on secondary interfaces, applications shall use the service ***nx_ip_interface_status_check.***</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1378">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1378">Parameters</span></span>

- <span data-ttu-id="112c2-1379">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1379">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1380">**needed_status** 요청된 IP 상태이며 다음과 같이 비트맵 형식으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1380">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
- <span data-ttu-id="112c2-1381">NX_IP_INITIALIZE_DONE(0x0001)</span><span class="sxs-lookup"><span data-stu-id="112c2-1381">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
- <span data-ttu-id="112c2-1382">NX_IP_ADDRESS_RESOLVED(0x0002)</span><span class="sxs-lookup"><span data-stu-id="112c2-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
- <span data-ttu-id="112c2-1383">NX_IP_LINK_ENABLED(0x0004)</span><span class="sxs-lookup"><span data-stu-id="112c2-1383">NX_IP_LINK_ENABLED (0x0004)</span></span>
- <span data-ttu-id="112c2-1384">NX_IP_ARP_ENABLED(0x0008)</span><span class="sxs-lookup"><span data-stu-id="112c2-1384">NX_IP_ARP_ENABLED (0x0008)</span></span>
- <span data-ttu-id="112c2-1385">NX_IP_UDP_ENABLED(0x0010)</span><span class="sxs-lookup"><span data-stu-id="112c2-1385">NX_IP_UDP_ENABLED (0x0010)</span></span>
- <span data-ttu-id="112c2-1386">NX_IP_TCP_ENABLED(0x0020)</span><span class="sxs-lookup"><span data-stu-id="112c2-1386">NX_IP_TCP_ENABLED (0x0020)</span></span>
- <span data-ttu-id="112c2-1387">NX_IP_IGMP_ENABLED(0x0040)</span><span class="sxs-lookup"><span data-stu-id="112c2-1387">NX_IP_IGMP_ENABLED (0x0040)</span></span>
- <span data-ttu-id="112c2-1388">NX_IP_RARP_COMPLETE(0x0080)</span><span class="sxs-lookup"><span data-stu-id="112c2-1388">NX_IP_RARP_COMPLETE (0x0080)</span></span>
- <span data-ttu-id="112c2-1389">NX_IP_INTERFACE_LINK_ENABLED(0x0100)</span><span class="sxs-lookup"><span data-stu-id="112c2-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="112c2-1390">**actual_status** 설정된 실제 비트 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1390">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="112c2-1391">**wait_option** 요청된 상태 비트를 사용할 수 없는 경우 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1391">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="112c2-1392">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1392">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-1393">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1393">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-1394">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-1395">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-1395">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1396">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1396">Return Values</span></span>

- <span data-ttu-id="112c2-1397">**NX_SUCCESS**(0x00) IP 상태 확인에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1397">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="112c2-1398">**NX_NOT_SUCCESSFUL**(0x43) 지정된 시간 제한 내에 상태 요청이 충족되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1398">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="112c2-1399">**NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었거나 잘못된 상태였거나, 실제 상태 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1399">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="112c2-1400">**NX_OPTION_ERROR**(0x0a) 필요한 상태 옵션이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1400">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="112c2-1401">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1401">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1402">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1402">Allowed From</span></span>

<span data-ttu-id="112c2-1403">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1403">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1404">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1404">Preemption Possible</span></span>

<span data-ttu-id="112c2-1405">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1405">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1406">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1406">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1407">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1407">See Also</span></span>

- <span data-ttu-id="112c2-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="112c2-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="112c2-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="112c2-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span></span>

## <a name="nx_packet_allocate"></a><span data-ttu-id="112c2-1413">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="112c2-1413">nx_packet_allocate</span></span>

<span data-ttu-id="112c2-1414">지정된 풀에서 패킷을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1414">Allocate packet from specified pool</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1415">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1415">Prototype</span></span>

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-1416">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1416">Description</span></span>

<span data-ttu-id="112c2-1417">이 서비스는 지정된 풀의 패킷을 할당하고 지정된 패킷의 유형에 따라 패킷의 앞에 추가 포인터를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1417">This service allocates a packet from the specified pool and adjusts the prepend pointer in the packet according to the type of packet specified.</span></span> <span data-ttu-id="112c2-1418">사용할 수 있는 패킷이 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1418">If no packet is available, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1419">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1419">Parameters</span></span>

- <span data-ttu-id="112c2-1420">**pool_ptr** 이전에 만든 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1420">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="112c2-1421">**packet_ptr** 할당된 패킷 포인터의 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1421">**packet_ptr** Pointer to the pointer of the allocated packet pointer.</span></span>
- <span data-ttu-id="112c2-1422">**packet_type** 요청된 패킷의 유형을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1422">**packet_type** Defines the type of packet requested.</span></span> <span data-ttu-id="112c2-1423">지원되는 패킷 유형 목록은 3장의 49페이지에서 “패킷 풀”을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="112c2-1423">See “Packet Pools” on page 49 in Chapter 3 for a list of supported packet types.</span></span>
- <span data-ttu-id="112c2-1424">**wait_option** 패킷 풀에서 사용할 수 있는 패킷이 없는 경우의 틱 단위 대기 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1424">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="112c2-1425">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1425">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-1426">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1426">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-1427">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-1428">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-1428">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1429">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1429">Return Values</span></span>

- <span data-ttu-id="112c2-1430">**NX_SUCCESS**(0x00) 패킷 할당에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1430">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="112c2-1431">**NX_NO_PACKET**(0x01) 사용할 수 있는 패킷이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1431">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="112c2-1432">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1432">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="112c2-1433">**NX_INVALID_PARAMETERS**(0x4D) 패킷 크기가 프로토콜을 지원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1433">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="112c2-1434">**NX_OPTION_ERROR**(0x0A) 잘못된 패킷 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1434">**NX_OPTION_ERROR** (0x0A) Invalid packet type.</span></span>
- <span data-ttu-id="112c2-1435">**NX_PTR_ERROR**(0x07) 잘못된 풀 또는 패킷 반환 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1435">**NX_PTR_ERROR** (0x07) Invalid pool or packet return pointer.</span></span>
- <span data-ttu-id="112c2-1436">**NX_CALLER_ERROR**(0x11) 비스레드의 대기 옵션이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1436">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1437">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1437">Allowed From</span></span>

<span data-ttu-id="112c2-1438">초기화, 스레드, 타이머, ISR(애플리케이션 네트워크 드라이버)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1438">Initialization, threads, timers, and ISRs (application network drivers).</span></span> <span data-ttu-id="112c2-1439">ISR 또는 타이머 컨텍스트에서 사용되는 경우 대기 옵션은 NX_NO_WAIT여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1439">Wait option must be NX_NO_WAIT when used in ISR or in timer context.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1440">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1440">Preemption Possible</span></span>

<span data-ttu-id="112c2-1441">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1441">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1442">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1442">Example</span></span>

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1443">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1443">See Also</span></span>

- <span data-ttu-id="112c2-1444">nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="112c2-1444">nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="112c2-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="112c2-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="112c2-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="112c2-1447">nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1447">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="112c2-1448">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1448">nx_packet_transmit_release</span></span>

## <a name="nx_packet_copy"></a><span data-ttu-id="112c2-1449">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="112c2-1449">nx_packet_copy</span></span>

<span data-ttu-id="112c2-1450">패킷을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1450">Copy packet</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1451">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1451">Prototype</span></span>

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-1452">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1452">Description</span></span>

<span data-ttu-id="112c2-1453">이 서비스는 제공된 패킷 풀에서 할당된 하나 이상의 새 패킷에 제공된 패킷의 정보를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1453">This service copies the information in the supplied packet to one or more new packets that are allocated from the supplied packet pool.</span></span> <span data-ttu-id="112c2-1454">성공하면 새 패킷에 대한 포인터가 **new_packet_ptr** 에서 가리키는 대상에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1454">If successful, the pointer to the new packet is returned in destination pointed to by **new_packet_ptr**.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1455">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1455">Parameters</span></span>

- <span data-ttu-id="112c2-1456">**packet_ptr** 원본 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1456">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="112c2-1457">**new_packet_ptr** 패킷의 새 복사본에 대한 포인터를 반환할 위치 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1457">**new_packet_ptr** Pointer to the destination of where to return the pointer to the new copy of the packet.</span></span>
- <span data-ttu-id="112c2-1458">**pool_ptr** 복사본에 대해 패킷을 하나 이상 할당하는 데 사용되는, 이전에 만든 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1458">**pool_ptr** Pointer to the previously created packet pool that is used to allocate one or more packets for the copy.</span></span>
- <span data-ttu-id="112c2-1459">**wait_option** 사용할 수 있는 패킷이 없는 경우 서비스가 대기하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1459">**wait_option** Defines how the service waits if there are no packets available.</span></span> <span data-ttu-id="112c2-1460">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1460">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-1461">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1461">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-1462">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-1463">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-1463">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1464">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1464">Return Values</span></span>
- <span data-ttu-id="112c2-1465">**NX_SUCCESS**(0x00) 패킷 복사에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1465">**NX_SUCCESS** (0x00) Successful packet copy.</span></span>
- <span data-ttu-id="112c2-1466">**NX_NO_PACKET**(0x01) 패킷을 복사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1466">**NX_NO_PACKET** (0x01) Packet not available for copy.</span></span>
- <span data-ttu-id="112c2-1467">**NX_INVALID_PACKET**(0x12) 원본 패킷이 비어 있거나 복사하는 데 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1467">**NX_INVALID_PACKET** (0x12) Empty source packet or copy failed.</span></span>
- <span data-ttu-id="112c2-1468">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1468">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="112c2-1469">**NX_INVALID_PARAMETERS**(0x4D) 패킷 크기가 프로토콜을 지원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1469">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="112c2-1470">**NX_PTR_ERROR**(0x07) 잘못된 풀, 패킷 또는 대상 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1470">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or destination pointer.</span></span>
- <span data-ttu-id="112c2-1471">**NX_UNDERFLOW**(0x02) 잘못된 패킷 앞에 추가 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1471">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="112c2-1472">**NX_OVERFLOW**(0x03) 잘못된 패킷 뒤에 추가 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1472">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="112c2-1473">**NX_CALLER_ERROR**(0x11) 초기화 또는 ISR에 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1473">**NX_CALLER_ERROR** (0x11) A wait option was specified in initialization or in an ISR.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1474">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1474">Allowed From</span></span>

<span data-ttu-id="112c2-1475">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="112c2-1475">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1476">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1476">Preemption Possible</span></span>

<span data-ttu-id="112c2-1477">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1477">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1478">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1478">Example</span></span>

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1479">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1479">See Also</span></span>

- <span data-ttu-id="112c2-1480">nx_packet_allocate, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="112c2-1480">nx_packet_allocate, nx_packet_data_append,</span></span>
- <span data-ttu-id="112c2-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="112c2-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="112c2-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="112c2-1483">nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1483">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="112c2-1484">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1484">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_append"></a><span data-ttu-id="112c2-1485">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="112c2-1485">nx_packet_data_append</span></span>

<span data-ttu-id="112c2-1486">패킷 끝에 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1486">Append data to end of packet</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1487">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1487">Prototype</span></span>

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-1488">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1488">Description</span></span>

<span data-ttu-id="112c2-1489">이 서비스는 지정된 패킷 끝에 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1489">This service appends data to the end of the specified packet.</span></span> <span data-ttu-id="112c2-1490">제공된 데이터 영역은 패킷으로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1490">The supplied data area is copied into the packet.</span></span> <span data-ttu-id="112c2-1491">사용할 수 있는 메모리가 부족하며 연결된 패킷 기능이 사용하도록 설정된 경우 패킷을 하나 이상 할당하여 요청을 충족합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1491">If there is not enough memory available, and the chained packet feature is enabled, one or more packets will be allocated to satisfy the request.</span></span> <span data-ttu-id="112c2-1492">연결된 패킷 기능이 사용하도록 설정되지 않는 경우 *NX_SIZE_ERROR* 가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1492">If the chained packet feature is not enabled, *NX_SIZE_ERROR* is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1493">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1493">Parameters</span></span>

- <span data-ttu-id="112c2-1494">**packet_ptr** 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1494">**packet_ptr** Packet pointer.</span></span>
- <span data-ttu-id="112c2-1495">**data_start** 패킷 뒤에 추가할 사용자 데이터 영역 시작 부분에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1495">**data_start** Pointer to the start of the user’s data area to append to the packet.</span></span>
- <span data-ttu-id="112c2-1496">**data_size** 사용자 데이터 영역 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1496">**data_size** Size of user’s data area.</span></span>
- <span data-ttu-id="112c2-1497">**pool_ptr** 현재 패킷에 공간이 충분하지 않은 경우 다른 패킷을 할당할 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1497">**pool_ptr** Pointer to packet pool from which to allocate another packet if there is not enough room in the current packet.</span></span>
- <span data-ttu-id="112c2-1498">**wait_option** 사용할 수 있는 패킷이 없는 경우 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1498">**wait_option** Defines how the service behaves if there are no packets available.</span></span> <span data-ttu-id="112c2-1499">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1499">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-1500">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1500">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-1501">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-1502">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-1502">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1503">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1503">Return Values</span></span>

- <span data-ttu-id="112c2-1504">**NX_SUCCESS**(0x00) 패킷 뒤에 추가에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1504">**NX_SUCCESS** (0x00) Successful packet append.</span></span>
- <span data-ttu-id="112c2-1505">**NX_NO_PACKET**(0x01) 사용할 수 있는 패킷이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1505">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="112c2-1506">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 *tx_thread_wait_abort* 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1506">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="112c2-1507">**NX_INVALID_PARAMETERS**(0x4D) 패킷 크기가 프로토콜을 지원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1507">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="112c2-1508">**NX_UNDERFLOW**(0x02) 앞에 추가 포인터가 페이로드 시작보다 먼저입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1508">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="112c2-1509">**NX_OVERFLOW**(0x03) 뒤에 추가 포인터가 페이로드 종료보다 나중입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1509">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>
- <span data-ttu-id="112c2-1510">**NX_PTR_ERROR**(0x07) 잘못된 풀, 패킷 또는 데이터 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1510">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or data Pointer.</span></span>
- <span data-ttu-id="112c2-1511">**NX_SIZE_ERROR**(0x09) 잘못된 데이터 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1511">**NX_SIZE_ERROR** (0x09) Invalid data size.</span></span>
- <span data-ttu-id="112c2-1512">**NX_CALLER_ERROR**(0x11) 비스레드의 대기 옵션이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1512">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1513">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1513">Allowed From</span></span>

<span data-ttu-id="112c2-1514">초기화, 스레드, 타이머, ISR(애플리케이션 네트워크 드라이버)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1514">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1515">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1515">Preemption Possible</span></span>

<span data-ttu-id="112c2-1516">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1516">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1517">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1517">Example</span></span>

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a><span data-ttu-id="112c2-1518">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1518">See Also</span></span>

- <span data-ttu-id="112c2-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="112c2-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,</span></span>
- <span data-ttu-id="112c2-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="112c2-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="112c2-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="112c2-1522">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1522">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_extract_offset"></a><span data-ttu-id="112c2-1523">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="112c2-1523">nx_packet_data_extract_offset</span></span>

<span data-ttu-id="112c2-1524">오프셋을 통해 패킷에서 데이터를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1524">Extract data from packet via an offset</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1525">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1525">Prototype</span></span>

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="112c2-1526">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1526">Description</span></span>

<span data-ttu-id="112c2-1527">이 서비스는 패킷 앞에 추가 포인터의 지정된 오프셋에서 시작하여 지정된 크기(바이트)의 NetX 패킷(또는 패킷 체인) 데이터를 지정된 버퍼에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1527">This service copies data from a NetX packet (or packet chain) starting at the specified offset from the packet prepend pointer of the specified size in bytes into the specified buffer.</span></span> <span data-ttu-id="112c2-1528">실제로 복사된 바이트 수는 *bytes_copied* 로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1528">The number of bytes actually copied is returned in *bytes_copied.*</span></span> <span data-ttu-id="112c2-1529">이 서비스는 패킷에서 데이터를 제거하지 않으며 앞에 추가 포인터 또는 다른 내부 상태 정보도 조정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1529">This service does not remove data from the packet, nor does it adjust the prepend pointer or other internal state information.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1530">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1530">Parameters</span></span>

- <span data-ttu-id="112c2-1531">**packet_ptr** 추출할 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1531">**packet_ptr** Pointer to packet to extract</span></span>
- <span data-ttu-id="112c2-1532">**offset** 현재 앞에 추가 포인터의 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1532">**offset** Offset from the current prepend pointer.</span></span>
- <span data-ttu-id="112c2-1533">**buffer_start** 저장 버퍼 시작 부분에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1533">**buffer_start** Pointer to start of save buffer</span></span>
- <span data-ttu-id="112c2-1534">**buffer_length** 복사할 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1534">**buffer_length** Number of bytes to copy</span></span>
- <span data-ttu-id="112c2-1535">**bytes_copied** 실제로 복사된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1535">**bytes_copied** Number of bytes actually copied</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1536">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1536">Return Values</span></span>

- <span data-ttu-id="112c2-1537">**NX_SUCCESS**(0x00) 패킷 복사에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1537">**NX_SUCCESS** (0x00) Successful packet copy</span></span>
- <span data-ttu-id="112c2-1538">**NX_PACKET_OFFSET_ERROR**(0x53) 잘못된 오프셋 값을 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1538">**NX_PACKET_OFFSET_ERROR** (0x53) Invalid offset value was supplied</span></span>
- <span data-ttu-id="112c2-1539">**NX_PTR_ERROR**(0x07) 잘못된 패킷 포인터 또는 버퍼 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1539">**NX_PTR_ERROR** (0x07) Invalid packet pointer or buffer pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1540">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1540">Allowed From</span></span>

<span data-ttu-id="112c2-1541">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="112c2-1541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1542">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1542">Preemption Possible</span></span>

<span data-ttu-id="112c2-1543">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1543">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1544">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1544">Example</span></span>

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1545">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1545">See Also</span></span>

- <span data-ttu-id="112c2-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="112c2-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="112c2-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="112c2-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="112c2-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="112c2-1549">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1549">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_retrieve"></a><span data-ttu-id="112c2-1550">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="112c2-1550">nx_packet_data_retrieve</span></span>

<span data-ttu-id="112c2-1551">패킷에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1551">Retrieve data from packet</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1552">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1552">Prototype</span></span>

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="112c2-1553">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1553">Description</span></span>

<span data-ttu-id="112c2-1554">이 서비스는 제공된 패킷의 데이터를 제공된 버퍼에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1554">This service copies data from the supplied packet into the supplied buffer.</span></span> <span data-ttu-id="112c2-1555">복사된 실제 바이트 수는 **bytes_copied** 가 가리키는 대상에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1555">The actual number of bytes copied is returned in the destination pointed to by **bytes_copied**.</span></span>

<span data-ttu-id="112c2-1556">이 서비스는 패킷의 내부 상태를 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1556">Note that this service does not change internal state of the packet.</span></span> <span data-ttu-id="112c2-1557">검색되는 데이터는 패킷에서 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1557">The data being retrieved is still available in the packet.</span></span>

<span data-ttu-id="112c2-1558">‘대상 버퍼는 패킷 콘텐츠를 포함할 수 있도록 크기가 충분히 커야 합니다. 그러지 않으면 메모리가 손상되어 예기치 않은 결과가 발생합니다.’</span><span class="sxs-lookup"><span data-stu-id="112c2-1558">*The destination buffer must be large enough to hold the packet's contents. If not, memory will be corrupted causing unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1559">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1559">Parameters</span></span>

- <span data-ttu-id="112c2-1560">**packet_ptr** 원본 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1560">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="112c2-1561">**buffer_start** 버퍼 영역의 시작 부분에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1561">**buffer_start** Pointer to the start of the buffer area.</span></span>
- <span data-ttu-id="112c2-1562">**bytes_copied** 복사된 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1562">**bytes_copied** Pointer to the destination for the number of bytes copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1563">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1563">Return Values</span></span>

- <span data-ttu-id="112c2-1564">**NX_SUCCESS**(0x00) 패킷 데이터 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1564">**NX_SUCCESS** (0x00) Successful packet data retrieve.</span></span>
- <span data-ttu-id="112c2-1565">**NX_INVALID_PACKET**(0x12) 잘못된 패킷입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1565">**NX_INVALID_PACKET** (0x12) Invalid packet.</span></span>
- <span data-ttu-id="112c2-1566">**NX_PTR_ERROR**(0x07) 패킷, 버퍼 시작 또는 복사된 바이트 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1566">**NX_PTR_ERROR** (0x07) Invalid packet, buffer start, or bytes copied pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1567">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1567">Allowed From</span></span>

<span data-ttu-id="112c2-1568">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="112c2-1568">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1569">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1569">Preemption Possible</span></span>

<span data-ttu-id="112c2-1570">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1570">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1571">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1571">Example</span></span>

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1572">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1572">See Also</span></span>

- <span data-ttu-id="112c2-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="112c2-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="112c2-1574">nx_packet_data_extract_offset, nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1574">nx_packet_data_extract_offset, nx_packet_length_get,</span></span>
- <span data-ttu-id="112c2-1575">nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-1575">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="112c2-1576">nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1576">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="112c2-1577">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1577">nx_packet_transmit_release</span></span>

## <a name="nx_packet_length_get"></a><span data-ttu-id="112c2-1578">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1578">nx_packet_length_get</span></span>

<span data-ttu-id="112c2-1579">패킷 데이터의 길이를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1579">Get length of packet data</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1580">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1580">Prototype</span></span>

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a><span data-ttu-id="112c2-1581">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1581">Description</span></span>

<span data-ttu-id="112c2-1582">이 서비스는 지정된 패킷에서 데이터의 길이를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1582">This service gets the length of the data in the specified packet.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1583">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1583">Parameters</span></span>

- <span data-ttu-id="112c2-1584">**packet_ptr** 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1584">**packet_ptr** Pointer to the packet.</span></span>
- <span data-ttu-id="112c2-1585">**length** 패킷 길이 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1585">**length** Destination for the packet length.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1586">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1586">Allowed From</span></span>

<span data-ttu-id="112c2-1587">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="112c2-1587">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1588">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1588">Preemption Possible</span></span>

<span data-ttu-id="112c2-1589">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1589">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1590">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1590">Example</span></span>

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1591">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1591">See Also</span></span>

- <span data-ttu-id="112c2-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="112c2-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="112c2-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="112c2-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="112c2-1594">nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-1594">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="112c2-1595">nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1595">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="112c2-1596">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1596">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_create"></a><span data-ttu-id="112c2-1597">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="112c2-1597">nx_packet_pool_create</span></span>

<span data-ttu-id="112c2-1598">지정된 메모리 영역에 패킷 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1598">Create packet pool in specified memory area</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1599">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1599">Prototype</span></span>

```C
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="112c2-1600">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1600">Description</span></span>

<span data-ttu-id="112c2-1601">이 서비스는 사용자가 제공한 메모리 영역에 지정된 패킷 크기의 패킷 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1601">This service creates a packet pool of the specified packet size in the memory area supplied by the user.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1602">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1602">Parameters</span></span>

- <span data-ttu-id="112c2-1603">**pool_ptr** 패킷 풀 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1603">**pool_ptr** Pointer to packet pool control block.</span></span>
- <span data-ttu-id="112c2-1604">**name** 패킷 풀의 애플리케이션 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1604">**name** Pointer to application’s name for the packet pool.</span></span>
- <span data-ttu-id="112c2-1605">**payload_size** 풀에 있는 각 패킷의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1605">**payload_size** Number of bytes in each packet in the pool.</span></span> <span data-ttu-id="112c2-1606">이 값은 40바이트 이상이어야 하며 4로 균등하게 나뉘어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1606">This value must be at least 40 bytes and must also be evenly divisible by 4.</span></span>
- <span data-ttu-id="112c2-1607">**memory_ptr** 패킷 풀을 배치할 메모리 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1607">**memory_ptr** Pointer to the memory area to place the packet pool in.</span></span> <span data-ttu-id="112c2-1608">이 포인터는 ULONG 경계에 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1608">The pointer should be aligned on an ULONG boundary.</span></span>
- <span data-ttu-id="112c2-1609">**memory_size** 풀 메모리 영역의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1609">**memory_size** Size of the pool memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1610">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1610">Return Values</span></span>

- <span data-ttu-id="112c2-1611">**NX_SUCCESS**(0x00) 패킷 풀을 만드는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1611">**NX_SUCCESS** (0x00) Successful packet pool create.</span></span>
- <span data-ttu-id="112c2-1612">**NX_PTR_ERROR**(0x07) 잘못된 풀 또는 메모리 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1612">**NX_PTR_ERROR** (0x07) Invalid pool or memory pointer.</span></span>
- <span data-ttu-id="112c2-1613">**NX_SIZE_ERROR**(0x09) 잘못된 블록 또는 메모리 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1613">**NX_SIZE_ERROR** (0x09) Invalid block or memory size.</span></span>
- <span data-ttu-id="112c2-1614">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1614">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1615">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1615">Allowed From</span></span>

<span data-ttu-id="112c2-1616">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1616">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1617">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1617">Preemption Possible</span></span>

<span data-ttu-id="112c2-1618">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1618">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1619">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1619">Example</span></span>

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1620">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1620">See Also</span></span>

- <span data-ttu-id="112c2-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="112c2-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="112c2-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="112c2-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="112c2-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,</span></span>
- <span data-ttu-id="112c2-1624">nx_packet_release, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1624">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_delete"></a><span data-ttu-id="112c2-1625">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-1625">nx_packet_pool_delete</span></span>

<span data-ttu-id="112c2-1626">이전에 만든 패킷 풀을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1626">Delete previously created packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1627">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1627">Prototype</span></span>

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-1628">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1628">Description</span></span>

<span data-ttu-id="112c2-1629">이 서비스는 이전에 만든 패킷 풀을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1629">This service deletes a previously-created packet pool.</span></span> <span data-ttu-id="112c2-1630">NetX는 패킷 풀의 패킷에서 현재 일시 중단된 스레드가 있는지 확인하고 일시 중단을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1630">NetX checks for any threads currently suspended on packets in the packet pool and clears the suspension.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1631">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1631">Parameters</span></span>

- <span data-ttu-id="112c2-1632">**pool_ptr** 패킷 풀 제어 블록 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1632">**pool_ptr** Packet pool control block pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1633">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1633">Return Values</span></span>

- <span data-ttu-id="112c2-1634">**NX_SUCCESS**(0x00) 패킷 풀 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1634">**NX_SUCCESS** (0x00) Successful packet pool delete.</span></span>
- <span data-ttu-id="112c2-1635">**NX_PTR_ERROR**(0x07) 잘못된 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1635">**NX_PTR_ERROR** (0x07) Invalid pool pointer.</span></span>
- <span data-ttu-id="112c2-1636">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1636">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1637">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1637">Allowed From</span></span>

<span data-ttu-id="112c2-1638">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1638">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1639">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1639">Preemption Possible</span></span>

<span data-ttu-id="112c2-1640">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1640">Yes</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1641">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1641">Example</span></span>

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1642">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1642">See Also</span></span>

- <span data-ttu-id="112c2-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="112c2-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="112c2-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="112c2-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="112c2-1645">nx_packet_length_get, nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="112c2-1645">nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="112c2-1646">nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1646">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="112c2-1647">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1647">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_info_get"></a><span data-ttu-id="112c2-1648">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1648">nx_packet_pool_info_get</span></span>

<span data-ttu-id="112c2-1649">패킷 풀에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1649">Retrieve information about a packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1650">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1650">Prototype</span></span>

```C
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```

### <a name="description"></a><span data-ttu-id="112c2-1651">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1651">Description</span></span>

<span data-ttu-id="112c2-1652">이 서비스는 지정된 패킷 풀에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1652">This service retrieves information about the specified packet pool.</span></span>

<span data-ttu-id="112c2-1653">대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1653">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1654">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1654">Parameters</span></span>

- <span data-ttu-id="112c2-1655">**pool_ptr** 이전에 만든 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1655">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="112c2-1656">**total_packets** 풀의 총 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1656">**total_packets** Pointer to destination for the total number of packets in the pool.</span></span>
- <span data-ttu-id="112c2-1657">**free_packets** 현재 사용 가능한 총 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1657">**free_packets** Pointer to destination for the total number of currently free packets.</span></span>
- <span data-ttu-id="112c2-1658">**empty_pool_requests** 풀이 비어 있는 경우의 총 할당 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1658">**empty_pool_requests** Pointer to destination of the total number of allocation requests when the pool was empty.</span></span>
- <span data-ttu-id="112c2-1659">**empty_pool_suspensions** 비어 있는 풀의 총 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1659">**empty_pool_suspensions** Pointer to destination of the total number of empty pool suspensions.</span></span>
- <span data-ttu-id="112c2-1660">**invalid_packet_releases** 잘못된 총 패킷 해제 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1660">**invalid_packet_releases** Pointer to destination of the total number of invalid packet releases.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1661">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1661">Return Values</span></span>

- <span data-ttu-id="112c2-1662">**NX_SUCCESS**(0x00) 패킷 풀 정보를 검색하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1662">**NX_SUCCESS** (0x00) Successful packet pool information retrieval.</span></span>
- <span data-ttu-id="112c2-1663">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1663">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-1664">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1664">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1665">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1665">Allowed From</span></span>

<span data-ttu-id="112c2-1666">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="112c2-1666">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1667">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1667">Preemption Possible</span></span>

<span data-ttu-id="112c2-1668">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1668">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1669">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1669">Example</span></span>

```C
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
    &total_packets,
    &free_packets,
    &empty_pool_requests,
    &empty_pool_suspensions,
    &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1670">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1670">See Also</span></span>

- <span data-ttu-id="112c2-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="112c2-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="112c2-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="112c2-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="112c2-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span></span>
- <span data-ttu-id="112c2-1674">nx_packet_release, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1674">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_release"></a><span data-ttu-id="112c2-1675">nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1675">nx_packet_release</span></span>

<span data-ttu-id="112c2-1676">이전에 할당된 패킷을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1676">Release previously allocated packet</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1677">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1677">Prototype</span></span>

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-1678">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1678">Description</span></span>

<span data-ttu-id="112c2-1679">이 서비스는 지정된 패킷에 연결된 추가 패킷을 포함하여 패킷을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1679">This service releases a packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="112c2-1680">다른 스레드가 패킷 할당에서 차단된 경우 이 서비스가 해당 패킷에 제공되고 계속 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1680">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span>

<span data-ttu-id="112c2-1681">패킷을 두 번 이상 해제하면 예기치 않은 결과가 발생할 수 있으므로 애플리케이션은 패킷을 한 번만 해제하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1681">*The application must prevent releasing a packet more than once, because doing so will cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1682">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1682">Parameters</span></span>

- <span data-ttu-id="112c2-1683">**packet_ptr** 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1683">**packet_ptr** Packet pointer.</span></span>


### <a name="return-values"></a><span data-ttu-id="112c2-1684">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1684">Return Values</span></span>
- <span data-ttu-id="112c2-1685">**NX_SUCCESS**(0x00) 패킷 해제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1685">**NX_SUCCESS** (0x00) Successful packet release.</span></span>
- <span data-ttu-id="112c2-1686">**NX_PTR_ERROR**(0x07) 잘못된 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1686">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="112c2-1687">**NX_UNDERFLOW**(0x02) 앞에 추가 포인터가 페이로드 시작보다 먼저입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1687">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="112c2-1688">**NX_OVERFLOW**(0x03) 뒤에 추가 포인터가 페이로드 종료보다 나중입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1688">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1689">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1689">Allowed From</span></span>

<span data-ttu-id="112c2-1690">초기화, 스레드, 타이머, ISR(애플리케이션 네트워크 드라이버)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1690">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1691">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1691">Preemption Possible</span></span>

<span data-ttu-id="112c2-1692">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1692">Yes</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1693">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1693">Example</span></span>

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1694">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1694">See Also</span></span>

- <span data-ttu-id="112c2-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="112c2-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="112c2-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="112c2-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="112c2-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="112c2-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span></span>

## <a name="nx_packet_transmit_release"></a><span data-ttu-id="112c2-1699">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1699">nx_packet_transmit_release</span></span>

<span data-ttu-id="112c2-1700">전송된 패킷을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1700">Release a transmitted packet</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1701">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1701">Prototype</span></span>

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-1702">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1702">Description</span></span>

<span data-ttu-id="112c2-1703">TCP가 아닌 패킷의 경우 이 서비스는 지정된 패킷에 연결된 추가 패킷을 포함하여 전송된 패킷을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1703">For non-TCP packets, this service releases a transmitted packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="112c2-1704">다른 스레드가 패킷 할당에서 차단된 경우 이 서비스가 해당 패킷에 제공되고 계속 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1704">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span> <span data-ttu-id="112c2-1705">전송된 TCP 패킷의 경우 패킷이 전송 중으로 표시되지만 패킷이 확인될 때까지 해제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1705">For a transmitted TCP packet, the packet is marked as being transmitted but not released till the packet is acknowledged.</span></span> <span data-ttu-id="112c2-1706">이 서비스는 일반적으로 패킷이 전송된 후 애플리케이션 네트워크 드라이버에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1706">This service is typically called from the application's network driver after a packet is transmitted.</span></span>

<span data-ttu-id="112c2-1707">네트워크 드라이버는 이 서비스를 호출하기 전에 실제 미디어 헤더를 제거하고 패킷 길이를 조정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1707">*The network driver should remove the physical media header and adjust the length of the packet before calling this service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1708">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1708">Parameters</span></span>

- <span data-ttu-id="112c2-1709">**packet_ptr** 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1709">**packet_ptr** Packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1710">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1710">Return Values</span></span>

- <span data-ttu-id="112c2-1711">**NX_SUCCESS**(0x00) 전송 패킷 해제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1711">**NX_SUCCESS** (0x00) Successful transmit packet release.</span></span>
- <span data-ttu-id="112c2-1712">**NX_PTR_ERROR**(0x07) 잘못된 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1712">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="112c2-1713">**NX_UNDERFLOW**(0x02) 앞에 추가 포인터가 페이로드 시작보다 먼저입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1713">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="112c2-1714">**NX_OVERFLOW**(0x03) 뒤에 추가 포인터가 페이로드 종료보다 나중입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1714">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1715">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1715">Allowed From</span></span>

<span data-ttu-id="112c2-1716">초기화, 스레드, 타이머, 애플리케이션 네트워크 드라이버(ISR 포함)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1716">Initialization, threads, timers, Application network drivers (including ISRs)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1717">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1717">Preemption Possible</span></span>

<span data-ttu-id="112c2-1718">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1718">Yes</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1719">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1719">Example</span></span>

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1720">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1720">See Also</span></span>

- <span data-ttu-id="112c2-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="112c2-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="112c2-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="112c2-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="112c2-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="112c2-1724">nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="112c2-1724">nx_packet_pool_info_get, nx_packet_release</span></span>

## <a name="nx_rarp_disable"></a><span data-ttu-id="112c2-1725">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-1725">nx_rarp_disable</span></span>

<span data-ttu-id="112c2-1726">RARP(역주소 확인 프로토콜)를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1726">Disable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1727">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1727">Prototype</span></span>

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-1728">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1728">Description</span></span>

<span data-ttu-id="112c2-1729">이 서비스는 특정 IP 인스턴스에 대해 NetX의 RARP 구성 요소를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1729">This service disables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="112c2-1730">멀티홈 시스템의 경우 이 서비스는 모든 인터페이스에서 RARP를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1730">For a multihome system, this service disables RARP on all interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1731">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1731">Parameters</span></span>

- <span data-ttu-id="112c2-1732">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1732">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1733">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1733">Return Values</span></span>

- <span data-ttu-id="112c2-1734">**NX_SUCCESS**(0x00) RARP를 사용하지 않도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1734">**NX_SUCCESS** (0x00) Successful RARP disable.</span></span>
- <span data-ttu-id="112c2-1735">**NX_NOT_ENABLED**(0x14) RARP가 사용하지 않도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1735">**NX_NOT_ENABLED** (0x14) RARP was not enabled.</span></span>
- <span data-ttu-id="112c2-1736">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1736">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-1737">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1737">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1738">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1738">Allowed From</span></span>

<span data-ttu-id="112c2-1739">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1739">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1740">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1740">Preemption Possible</span></span>

<span data-ttu-id="112c2-1741">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1741">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1742">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1742">Example</span></span>

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1743">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1743">See Also</span></span>

- <span data-ttu-id="112c2-1744">nx_rarp_enable, nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1744">nx_rarp_enable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_enable"></a><span data-ttu-id="112c2-1745">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-1745">nx_rarp_enable</span></span>

<span data-ttu-id="112c2-1746">RARP(역주소 확인 프로토콜)를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1746">Enable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1747">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1747">Prototype</span></span>

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-1748">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1748">Description</span></span>

<span data-ttu-id="112c2-1749">이 서비스는 특정 IP 인스턴스에 대해 NetX의 RARP 구성 요소를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1749">This service enables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="112c2-1750">RARP 구성 요소는 모든 연결된 네트워크 인터페이스에서 0으로 된 IP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1750">The RARP components searches through all attached network interfaces for zero IP address.</span></span> <span data-ttu-id="112c2-1751">0으로 된 IP 주소는 인터페이스에 IP 주소 할당이 아직 없는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1751">A zero IP address indicates the interface does not have IP address assignment yet.</span></span> <span data-ttu-id="112c2-1752">RARP는 해당 인터페이스에서 RARP 프로세스를 사용하도록 설정하여 IP 주소를 확인하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1752">RARP attempts to resolve the IP address by enabling RARP process on that interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1753">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1753">Parameters</span></span>

- <span data-ttu-id="112c2-1754">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1754">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1755">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1755">Return Values</span></span>

- <span data-ttu-id="112c2-1756">**NX_SUCCESS**(0x00) RARP를 사용하도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1756">**NX_SUCCESS** (0x00) Successful RARP enable.</span></span>
- <span data-ttu-id="112c2-1757">**NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 이미 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1757">**NX_IP_ADDRESS_ERROR** (0x21) IP address is already valid.</span></span>
- <span data-ttu-id="112c2-1758">**NX_ALREADY_ENABLED**(0x15) RARP가 이미 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1758">**NX_ALREADY_ENABLED** (0x15) RARP was already enabled.</span></span>
- <span data-ttu-id="112c2-1759">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1759">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-1760">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1760">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1761">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1761">Allowed From</span></span>

<span data-ttu-id="112c2-1762">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="112c2-1762">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1763">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1763">Preemption Possible</span></span>

<span data-ttu-id="112c2-1764">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1764">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1765">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1765">Example</span></span>

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1766">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1766">See Also</span></span>

- <span data-ttu-id="112c2-1767">nx_rarp_disable, nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1767">nx_rarp_disable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_info_get"></a><span data-ttu-id="112c2-1768">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1768">nx_rarp_info_get</span></span>

<span data-ttu-id="112c2-1769">RARP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1769">Retrieve information about RARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1770">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1770">Prototype</span></span>

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="112c2-1771">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1771">Description</span></span>

<span data-ttu-id="112c2-1772">이 서비스는 지정된 IP 인스턴스의 RARP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1772">This service retrieves information about RARP activities for the specified IP instance.</span></span>

<span data-ttu-id="112c2-1773">대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1773">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1774">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1774">Parameters</span></span>

- <span data-ttu-id="112c2-1775">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1775">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1776">**rarp_requests_sent** 송신된 총 RARP 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1776">**rarp_requests_sent** Pointer to destination for the total number of RARP requests sent.</span></span>
- <span data-ttu-id="112c2-1777">**rarp_responses_received** 수신된 총 RARP 응답 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1777">**rarp_responses_received** Pointer to destination for the total number of RARP responses received.</span></span>
- <span data-ttu-id="112c2-1778">**rarp_invalid_messages** 잘못된 총 메시지 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1778">**rarp_invalid_messages** Pointer to destination of the total number of invalid messages.</span></span>


### <a name="return-values"></a><span data-ttu-id="112c2-1779">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1779">Return Values</span></span>
- <span data-ttu-id="112c2-1780">**NX_SUCCESS**(0x00) RARP 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1780">**NX_SUCCESS** (0x00) Successful RARP information retrieval.</span></span>
- <span data-ttu-id="112c2-1781">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1781">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-1782">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1782">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="112c2-1783">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1784">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1784">Allowed From</span></span>

<span data-ttu-id="112c2-1785">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1785">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1786">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1786">Preemption Possible</span></span>

<span data-ttu-id="112c2-1787">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1787">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1788">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1788">Example</span></span>

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1789">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1789">See Also</span></span>

- <span data-ttu-id="112c2-1790">nx_rarp_disable, nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-1790">nx_rarp_disable, nx_rarp_enable</span></span>

## <a name="nx_system_initialize"></a><span data-ttu-id="112c2-1791">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="112c2-1791">nx_system_initialize</span></span>

<span data-ttu-id="112c2-1792">NetX 시스템을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1792">Initialize NetX System</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1793">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1793">Prototype</span></span>

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="112c2-1794">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1794">Description</span></span>

<span data-ttu-id="112c2-1795">이 서비스는 사용을 위한 준비로 기본 NetX 시스템 리소스를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1795">This service initializes the basic NetX system resources in preparation for use.</span></span> <span data-ttu-id="112c2-1796">초기화 중 다른 NetX 호출이 수행되기 전에 애플리케이션에서 이 서비스가 호출되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1796">It should be called by the application during initialization and before any other NetX call are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1797">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1797">Parameters</span></span>

<span data-ttu-id="112c2-1798">None</span><span class="sxs-lookup"><span data-stu-id="112c2-1798">None</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1799">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1799">Return Values</span></span>

<span data-ttu-id="112c2-1800">None</span><span class="sxs-lookup"><span data-stu-id="112c2-1800">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1801">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1801">Allowed From</span></span>

<span data-ttu-id="112c2-1802">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="112c2-1802">Initialization, threads, timers, ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1803">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1803">Preemption Possible</span></span>

<span data-ttu-id="112c2-1804">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1804">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1805">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1805">Example</span></span>

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1806">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1806">See Also</span></span>

- <span data-ttu-id="112c2-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="112c2-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="112c2-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="112c2-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="112c2-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="112c2-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="112c2-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="112c2-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span></span>

## <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="112c2-1812">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-1812">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="112c2-1813">클라이언트 TCP 소켓을 TCP 포트에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1813">Bind client TCP socket to TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1814">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1814">Prototype</span></span>

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-1815">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1815">Description</span></span>

<span data-ttu-id="112c2-1816">이 서비스는 이전에 만든 TCP 클라이언트 소켓을 지정된 TCP 포트에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1816">This service binds the previously created TCP client socket to the specified TCP port.</span></span> <span data-ttu-id="112c2-1817">유효한 TCP 소켓 범위는 0에서 0xFFFF까지입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1817">Valid TCP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="112c2-1818">지정된 TCP 포트를 사용할 수 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1818">If the specified TCP port is unavailable, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1819">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1819">Parameters</span></span>

- <span data-ttu-id="112c2-1820">**socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1820">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="112c2-1821">**port** 바인딩할 포트 번호(1-0xFFFF)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1821">**port** Port number to bind (1 through 0xFFFF).</span></span> <span data-ttu-id="112c2-1822">포트 번호가 NX_ANY_PORT(0x0000)인 경우 IP 인스턴스는 가능한 다음 포트를 검색하여 바인딩에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1822">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="112c2-1823">**wait_option** 포트가 이미 다른 소켓에 바인딩되어 있는 경우 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1823">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="112c2-1824">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1824">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-1825">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1825">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-1826">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-1827">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-1827">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1828">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1828">Return Values</span></span>

- <span data-ttu-id="112c2-1829">**NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1829">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="112c2-1830">**NX_ALREADY_BOUND**(0x22) 이 소켓은 다른 TCP 포트에 이미 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1830">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another TCP port.</span></span>
- <span data-ttu-id="112c2-1831">**NX_PORT_UNAVAILABLE**(0x23) 포트가 이미 다른 소켓에 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1831">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="112c2-1832">**NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1832">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="112c2-1833">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 *tx_thread_wait_abort* 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1833">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="112c2-1834">**NX_INVALID_PORT**(0x46) 잘못된 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1834">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="112c2-1835">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1835">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-1836">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1836">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-1837">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1837">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1838">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1838">Allowed From</span></span>

<span data-ttu-id="112c2-1839">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1839">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1840">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1840">Preemption Possible</span></span>

<span data-ttu-id="112c2-1841">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1841">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1842">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1842">Example</span></span>

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1843">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1843">See Also</span></span>

- <span data-ttu-id="112c2-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="112c2-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="112c2-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="112c2-1846">nx_tcp_info_get, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="112c2-1846">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="112c2-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="112c2-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="112c2-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="112c2-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="112c2-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-1853">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-1853">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="112c2-1854">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-1854">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="112c2-1855">클라이언트 TCP 소켓을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1855">Connect client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1856">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1856">Prototype</span></span>

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-1857">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1857">Description</span></span>

<span data-ttu-id="112c2-1858">이 서비스는 이전에 만든 바인딩된 TCP 클라이언트 소켓을 지정된 서버 포트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1858">This service connects the previously-created and bound TCP client socket to the specified server's port.</span></span> <span data-ttu-id="112c2-1859">유효한 TCP 서버 포트의 범위는 0에서 0xFFFF까지입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1859">Valid TCP server ports range from 0 through 0xFFFF.</span></span> <span data-ttu-id="112c2-1860">연결이 즉시 완료되지 않으면 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1860">If the connection does not complete immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1861">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1861">Parameters</span></span>

- <span data-ttu-id="112c2-1862">**socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1862">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="112c2-1863">**server_ip** 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1863">**server_ip** Server’s IP address.</span></span>
- <span data-ttu-id="112c2-1864">**server_port** 연결할 서버 포트 번호(1-0xFFFF)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1864">**server_port** Server port number to connect to (1 through 0xFFFF).</span></span>
- <span data-ttu-id="112c2-1865">**wait_option** 연결이 설정되는 동안 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1865">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="112c2-1866">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1866">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-1867">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-1867">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-1868">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-1869">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-1869">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1870">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1870">Return Values</span></span>

- <span data-ttu-id="112c2-1871">**NX_SUCCESS**(0x00) 소켓 연결에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1871">**NX_SUCCESS** (0x00) Successful socket connect.</span></span>
- <span data-ttu-id="112c2-1872">**NX_NOT_BOUND**(0x24) 소켓이 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1872">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="112c2-1873">**NX_NOT_CLOSED**(0x35) 소켓이 닫힘 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1873">**NX_NOT_CLOSED** (0x35) Socket is not in a closed state.</span></span>
- <span data-ttu-id="112c2-1874">**NX_IN_PROGRESS**(0x37) 대기하도록 지정되지 않았으며, 연결하려고 시도하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1874">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="112c2-1875">**NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스가 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1875">**NX_INVALID_INTERFACE** (0x4C) Invalid interface supplied.</span></span>
- <span data-ttu-id="112c2-1876">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1876">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="112c2-1877">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 서버 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1877">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address.</span></span>
- <span data-ttu-id="112c2-1878">**NX_INVALID_PORT**(0x46) 잘못된 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1878">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="112c2-1879">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1879">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-1880">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1880">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-1881">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1881">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1882">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1882">Allowed From</span></span>

<span data-ttu-id="112c2-1883">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1883">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1884">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1884">Preemption Possible</span></span>

<span data-ttu-id="112c2-1885">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1885">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1886">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1886">Example</span></span>

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1887">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1887">See Also</span></span>

- <span data-ttu-id="112c2-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="112c2-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="112c2-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="112c2-1890">nx_tcp_info_get, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="112c2-1890">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="112c2-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="112c2-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="112c2-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="112c2-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="112c2-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span></span>
- <span data-ttu-id="112c2-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-1897">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-1897">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="112c2-1898">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="112c2-1898">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="112c2-1899">클라이언트 TCP 소켓에 바인딩된 포트 번호를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1899">Get port number bound to client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1900">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1900">Prototype</span></span>

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-1901">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1901">Description</span></span>

<span data-ttu-id="112c2-1902">이 서비스는 소켓에 연결된 포트 번호를 검색합니다. 소켓이 바인딩될 때 NX_ANY_PORT가 지정된 경우 NetX에서 할당한 포트를 찾는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1902">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1903">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1903">Parameters</span></span>

- <span data-ttu-id="112c2-1904">**socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1904">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="112c2-1905">**port_ptr** 반환 포트 번호 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1905">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="112c2-1906">유효한 포트 번호는 (1-0xFFFF)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1906">Valid port numbers are (1 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1907">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1907">Return Values</span></span>

- <span data-ttu-id="112c2-1908">**NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1908">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="112c2-1909">**NX_NOT_BOUND**(0x24) 이 소켓은 포트에 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1909">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="112c2-1910">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터 또는 포트 반환 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1910">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="112c2-1911">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1911">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-1912">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1912">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1913">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1913">Allowed From</span></span>

<span data-ttu-id="112c2-1914">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1914">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1915">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1915">Preemption Possible</span></span>

<span data-ttu-id="112c2-1916">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1916">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1917">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1917">Example</span></span>

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1918">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1918">See Also</span></span>

- <span data-ttu-id="112c2-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="112c2-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="112c2-1921">nx_tcp_info_get, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="112c2-1921">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="112c2-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="112c2-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="112c2-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="112c2-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="112c2-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-1928">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-1928">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="112c2-1929">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-1929">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="112c2-1930">TCP 포트에서 TCP 클라이언트 소켓 바인딩을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1930">Unbind TCP client socket from TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1931">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1931">Prototype</span></span>

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-1932">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1932">Description</span></span>

<span data-ttu-id="112c2-1933">이 서비스는 TCP 클라이언트 소켓과 TCP 포트 간에 바인딩을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1933">This service releases the binding between the TCP client socket and a TCP port.</span></span> <span data-ttu-id="112c2-1934">다른 소켓을 동일한 포트 번호에 바인딩하려고 대기 중인 다른 스레드가 있는 경우 첫 번째 일시 중단된 스레드가 이 포트에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1934">If there are other threads waiting to bind another socket to the same port number, the first suspended thread is then bound to this port.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1935">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1935">Parameters</span></span>

- <span data-ttu-id="112c2-1936">**socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1936">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1937">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1937">Return Values</span></span>

- <span data-ttu-id="112c2-1938">**NX_SUCCESS**(0x00) 소켓을 바인딩 해제하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1938">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="112c2-1939">**NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1939">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="112c2-1940">**NX_NOT_CLOSED**(0x35) 소켓이 연결 해제되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1940">**NX_NOT_CLOSED** (0x35) Socket has not been disconnected.</span></span>
- <span data-ttu-id="112c2-1941">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1941">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-1942">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1942">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-1943">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1943">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1944">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1944">Allowed From</span></span>

<span data-ttu-id="112c2-1945">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-1945">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1946">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1946">Preemption Possible</span></span>

<span data-ttu-id="112c2-1947">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1947">Yes</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1948">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1948">Example</span></span>

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1949">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1949">See Also</span></span>

- <span data-ttu-id="112c2-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="112c2-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="112c2-1952">nx_tcp_info_get, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="112c2-1952">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="112c2-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="112c2-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="112c2-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="112c2-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="112c2-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-1959">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-1959">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_enable"></a><span data-ttu-id="112c2-1960">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-1960">nx_tcp_enable</span></span>

<span data-ttu-id="112c2-1961">NetX의 TCP 구성 요소를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1961">Enable TCP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1962">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1962">Prototype</span></span>

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-1963">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1963">Description</span></span>

<span data-ttu-id="112c2-1964">이 서비스는 NetX의 TCP(Transmission Control Protocol) 구성 요소를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1964">This service enables the Transmission Control Protocol (TCP) component of NetX.</span></span> <span data-ttu-id="112c2-1965">사용하도록 설정하면 애플리케이션에서 TCP 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1965">After enabled, TCP connections may be established by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1966">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1966">Parameters</span></span>

- <span data-ttu-id="112c2-1967">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1967">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-1968">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-1968">Return Values</span></span>

- <span data-ttu-id="112c2-1969">**NX_SUCCESS**(0x00) TCP를 사용하도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1969">**NX_SUCCESS** (0x00) Successful TCP enable.</span></span>
- <span data-ttu-id="112c2-1970">**NX_ALREADY_ENABLED**(0x15) TCP는 이미 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1970">**NX_ALREADY_ENABLED** (0x15) TCP is already enabled.</span></span>
- <span data-ttu-id="112c2-1971">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1971">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-1972">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1972">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-1973">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-1973">Allowed From</span></span>

<span data-ttu-id="112c2-1974">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="112c2-1974">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-1975">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-1975">Preemption Possible</span></span>

<span data-ttu-id="112c2-1976">예</span><span class="sxs-lookup"><span data-stu-id="112c2-1976">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-1977">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-1977">Example</span></span>

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-1978">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-1978">See Also</span></span>

- <span data-ttu-id="112c2-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="112c2-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="112c2-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="112c2-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="112c2-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="112c2-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="112c2-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-1988">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-1988">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_free_port_find"></a><span data-ttu-id="112c2-1989">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="112c2-1989">nx_tcp_free_port_find</span></span>

<span data-ttu-id="112c2-1990">사용할 수 있는 다음 TCP 포트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1990">Find next available TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-1991">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-1991">Prototype</span></span>

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-1992">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-1992">Description</span></span>

<span data-ttu-id="112c2-1993">이 서비스는 애플리케이션 제공 포트에서 시작하여 사용 가능한 TCP 포트(바인딩되지 않은 포트)를 찾으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1993">This service attempts to locate a free TCP port (unbound) starting from the application supplied port.</span></span> <span data-ttu-id="112c2-1994">검색에서 최대 포트 값인 0xFFFF에 도달하면 검색 논리가 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1994">The search logic will wrap around if the search happens to reach the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="112c2-1995">검색에 성공하면 *free_port_ptr* 이 가리키는 변수에 사용 가능한 포트가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1995">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="112c2-1996">이 서비스는 다른 스레드에서 호출될 수 있으며 동일한 포트를 반환할 수 있습니다. 이러한 경합 상태를 방지하기 위해 애플리케이션은 이 서비스 및 실제 클라이언트 소켓 바인딩에 뮤텍스 보호가 적용되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1996">*This service can be called from another thread and have the same port returned. To prevent this race condition, the application may wish to place this service and the actual client socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-1997">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-1997">Parameters</span></span>

- <span data-ttu-id="112c2-1998">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1998">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-1999">**port** 검색을 시작할 포트 번호(1-0xFFFF)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-1999">**port** Port number to start search at (1 through 0xFFFF).</span></span>
- <span data-ttu-id="112c2-2000">**free_port_ptr** 사용 가능한 포트 반환 값 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2000">**free_port_ptr** Pointer to the destination free port return value.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2001">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2001">Return Values</span></span>

- <span data-ttu-id="112c2-2002">**NX_SUCCESS**(0x00) 사용 가능한 포트를 찾는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2002">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="112c2-2003">**NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2003">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="112c2-2004">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2004">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-2005">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2006">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="112c2-2007">**NX_INVALID_PORT**(0x46) 지정된 포트 번호가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2007">**NX_INVALID_PORT** (0x46) The specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2008">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2008">Allowed From</span></span>

<span data-ttu-id="112c2-2009">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2009">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2010">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2010">Preemption Possible</span></span>

<span data-ttu-id="112c2-2011">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2011">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2012">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2012">Example</span></span>

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2013">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2013">See Also</span></span>

- <span data-ttu-id="112c2-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="112c2-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="112c2-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="112c2-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="112c2-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-2023">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2023">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_info_get"></a><span data-ttu-id="112c2-2024">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2024">nx_tcp_info_get</span></span>

<span data-ttu-id="112c2-2025">TCP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2025">Retrieve information about TCP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2026">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2026">Prototype</span></span>

```C
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```

### <a name="description"></a><span data-ttu-id="112c2-2027">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2027">Description</span></span>

<span data-ttu-id="112c2-2028">이 서비스는 지정된 IP 인스턴스의 TCP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2028">This service retrieves information about TCP activities for the specified IP instance.</span></span>

<span data-ttu-id="112c2-2029">대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2029">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2030">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2030">Parameters</span></span>

- <span data-ttu-id="112c2-2031">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2031">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-2032">**tcp_packets_sent** 송신된 총 TCP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2032">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent.</span></span>
- <span data-ttu-id="112c2-2033">**tcp_bytes_sent** 송신된 총 TCP 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2033">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent.</span></span>
- <span data-ttu-id="112c2-2034">**tcp_packets_received** 수신된 총 TCP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2034">**tcp_packets_received** Pointer to destination of the total number of TCP packets received.</span></span>
- <span data-ttu-id="112c2-2035">**tcp_bytes_received** 수신된 총 TCP 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2035">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received.</span></span>
- <span data-ttu-id="112c2-2036">**tcp_invalid_packets** 잘못된 총 TCP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2036">**tcp_invalid_packets** Pointer to destination of the total number of invalid TCP packets.</span></span>
- <span data-ttu-id="112c2-2037">**tcp_receive_packets_dropped** 삭제된 총 TCP 수신 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2037">**tcp_receive_packets_dropped** Pointer to destination of the total number of TCP receive packets dropped.</span></span>
- <span data-ttu-id="112c2-2038">**tcp_checksum_errors** 체크섬 오류가 있는 총 TCP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2038">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors.</span></span>
- <span data-ttu-id="112c2-2039">**tcp_connections** 총 TCP 연결 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2039">**tcp_connections** Pointer to destination of the total number of TCP connections.</span></span>
- <span data-ttu-id="112c2-2040">**tcp_disconnections** 총 TCP 연결 해제 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2040">**tcp_disconnections** Pointer to destination of the total number of TCP disconnections.</span></span>
- <span data-ttu-id="112c2-2041">**tcp_connections_dropped** 삭제된 총 TCP 연결 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2041">**tcp_connections_dropped** Pointer to destination of the total number of TCP connections dropped.</span></span>
- <span data-ttu-id="112c2-2042">**tcp_retransmit_packets** 재전송된 총 TCP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2042">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packets retransmitted.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2043">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2043">Return Values</span></span>

- <span data-ttu-id="112c2-2044">**NX_SUCCESS**(0x00) TCP 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2044">**NX_SUCCESS** (0x00) Successful TCP information retrieval.</span></span>
- <span data-ttu-id="112c2-2045">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2045">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-2046">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2046">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2047">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2047">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2048">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2048">Allowed From</span></span>

<span data-ttu-id="112c2-2049">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2049">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2050">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2050">Preemption Possible</span></span>

<span data-ttu-id="112c2-2051">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2051">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2052">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2052">Example</span></span>

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
status = nx_tcp_info_get(&ip_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_invalid_packets,
    &tcp_receive_packets_dropped,
    &tcp_checksum_errors,
    &tcp_connections,
    &tcp_disconnections
    &tcp_connections_dropped,
    &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2053">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2053">See Also</span></span>

- <span data-ttu-id="112c2-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="112c2-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="112c2-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="112c2-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="112c2-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-2063">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2063">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="112c2-2064">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="112c2-2064">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="112c2-2065">TCP 연결을 수락합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2065">Accept TCP connection</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2066">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2066">Prototype</span></span>

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-2067">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2067">Description</span></span>

<span data-ttu-id="112c2-2068">이 서비스는 이전에 수신 대기에 사용하도록 설정한 포트에 대한 TCP 클라이언트 소켓 연결 요청을 수락하거나 수락하기 위해 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2068">This service accepts (or prepares to accept) a TCP client socket connection request for a port that was previously set up for listening.</span></span> <span data-ttu-id="112c2-2069">애플리케이션이 수신 대기 또는 다시 수신 대기 서비스를 호출한 직후 이 서비스가 호출될 수도 있고, 클라이언트 연결이 실제로 있을 때 수신 콜백 루틴을 호출한 직후 이 서비스가 호출될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2069">This service may be called immediately after the application calls the listen or re-listen service, or after the listen callback routine is called when the client connection is actually present.</span></span> <span data-ttu-id="112c2-2070">즉시 연결을 설정할 수 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2070">If a connection cannot not be established right away, the service suspends according to the supplied wait option.</span></span>

<span data-ttu-id="112c2-2071">연결이 더 이상 필요하지 않으면 서버 포트에 대한 서버 소켓 바인딩을 제거하도록 애플리케이션이 ***nx_tcp_server_socket_unaccept*** 를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2071">*The application must call **nx_tcp_server_socket_unaccept** after the connection is no longer needed to remove the server socket's binding to the server port.*</span></span>

<span data-ttu-id="112c2-2072">애플리케이션 콜백 루틴은 IP 도우미 스레드 내에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2072">*Application callback routines are called from within the IP's helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2073">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2073">Parameters</span></span>

- <span data-ttu-id="112c2-2074">**socket_ptr** TCP 서버 소켓 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2074">**socket_ptr** Pointer to the TCP server socket control block.</span></span>
- <span data-ttu-id="112c2-2075">**wait_option** 연결이 설정되는 동안 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2075">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="112c2-2076">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2076">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-2077">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-2077">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-2078">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-2079">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-2079">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>


### <a name="return-values"></a><span data-ttu-id="112c2-2080">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2080">Return Values</span></span>
- <span data-ttu-id="112c2-2081">**NX_SUCCESS**(0x00) TCP 서버 소켓을 수락(수동 연결)하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2081">**NX_SUCCESS** (0x00) Successful TCP server socket accept (passive connect).</span></span>
- <span data-ttu-id="112c2-2082">**NX_NOT_LISTEN_STATE**(0x36) 제공된 서버 소켓이 수신 대기 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2082">**NX_NOT_LISTEN_STATE** (0x36) The server socket supplied is not in a listen state.</span></span>
- <span data-ttu-id="112c2-2083">**NX_IN_PROGRESS**(0x37) 대기하도록 지정되지 않았으며, 연결하려고 시도하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2083">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="112c2-2084">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 *tx_thread_wait_abort* 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2084">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="112c2-2085">**NX_PTR_ERROR**(0x07) 소켓 포인터 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2085">**NX_PTR_ERROR** (0x07) Socket pointer error.</span></span>
- <span data-ttu-id="112c2-2086">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2086">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2087">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2087">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2088">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2088">Allowed From</span></span>

<span data-ttu-id="112c2-2089">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2089">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2090">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2090">Preemption Possible</span></span>

<span data-ttu-id="112c2-2091">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2091">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2092">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2092">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;
    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
                message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
            again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="112c2-2093">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2093">See Also</span></span>

- <span data-ttu-id="112c2-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="112c2-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="112c2-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-2103">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2103">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="112c2-2104">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="112c2-2104">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="112c2-2105">TCP 포트에서 클라이언트 연결 수신 대기를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2105">Enable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2106">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2106">Prototype</span></span>

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a><span data-ttu-id="112c2-2107">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2107">Description</span></span>

<span data-ttu-id="112c2-2108">이 서비스는 지정된 TCP 포트에서 클라이언트 연결 요청 수신 대기를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2108">This service enables listening for a client connection request on the specified TCP port.</span></span> <span data-ttu-id="112c2-2109">클라이언트 연결 요청이 수신되면 제공된 서버 소켓이 지정된 포트에 바인딩되고 제공된 수신 대기 콜백 함수가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2109">When a client connection request is received, the supplied server socket is bound to the specified port and the supplied listen callback function is called.</span></span>

<span data-ttu-id="112c2-2110">수신 대기 콜백 루틴 처리는 애플리케이션에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2110">The listen callback routine's processing is completely up to the application.</span></span> <span data-ttu-id="112c2-2111">수락 작업에 이어 수행되는 애플리케이션 스레드 절전 모드 해제 논리가 포함되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2111">It may contain logic to wake up an application thread that subsequently performs an accept operation.</span></span> <span data-ttu-id="112c2-2112">이 소켓에 대해 수락 처리가 일시 중단된 스레드가 이미 애플리케이션에 있는 경우 수신 대기 콜백 루틴이 필요하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2112">If the application already has a thread suspended on accept processing for this socket, the listen callback routine may not be needed.</span></span>

<span data-ttu-id="112c2-2113">애플리케이션이 동일한 포트에서 추가 클라이언트 연결을 처리하려는 경우 다음 연결에 사용할 수 있는 소켓(CLOSED 상태의 소켓)이 포함된 ***nx_tcp_server_socket_relisten*** 을 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2113">If the application wishes to handle additional client connections on the same port, the ***nx_tcp_server_socket_relisten*** must be called with an available socket (a socket in the CLOSED state) for the next connection.</span></span> <span data-ttu-id="112c2-2114">다시 수신 대기 서비스가 호출될 때까지 추가 클라이언트 연결은 큐에 대기됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2114">Until the re-listen service is called, additional client connections are queued.</span></span> <span data-ttu-id="112c2-2115">최대 큐 크기를 초과하는 경우 새 연결 요청이 큐에 대기될 수 있도록 가장 오래된 연결 요청이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2115">When the maximum queue depth is exceeded, the oldest connection request is dropped in favor of queuing the new connection request.</span></span> <span data-ttu-id="112c2-2116">최대 큐 크기는 이 서비스에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2116">The maximum queue depth is specified by this service.</span></span>

<span data-ttu-id="112c2-2117">애플리케이션 콜백 루틴은 내부 IP 도우미 스레드에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2117">*Application callback routines are called from the internal IP helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2118">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2118">Parameters</span></span>

- <span data-ttu-id="112c2-2119">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2119">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-2120">**port** 수신 대기할 포트 번호(1-0xFFFF)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2120">**port** Port number to listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="112c2-2121">**socket_ptr** 연결에 사용할 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2121">**socket_ptr** Pointer to socket to use for the connection.</span></span>
- <span data-ttu-id="112c2-2122">**listen_queue_size** 큐에 대기될 수 있는 클라이언트 연결 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2122">**listen_queue_size** Number of client connection requests that can be queued.</span></span>
- <span data-ttu-id="112c2-2123">**listen_callback** 연결이 수신되면 호출할 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2123">**listen_callback** Application function to call when the connection is received.</span></span> <span data-ttu-id="112c2-2124">NULL을 지정하면 수신 대기 콜백 기능을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2124">If a NULL is specified, the listen callback feature is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2125">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2125">Return Values</span></span>

- <span data-ttu-id="112c2-2126">**NX_SUCCESS**(0x00) TCP 포트 수신 대기를 사용하도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2126">**NX_SUCCESS** (0x00) Successful TCP port listen enable.</span></span>
- <span data-ttu-id="112c2-2127">**NX_MAX_LISTEN**(0x33) 수신 대기 요청 구조를 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2127">**NX_MAX_LISTEN** (0x33) No more listen request structures are available.</span></span> <span data-ttu-id="112c2-2128">nx_api.h의 상수 NX_MAX_LISTEN_REQUESTS는 가능한 활성 수신 대기 요청 수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2128">The constant NX_MAX_LISTEN_REQUESTS in nx_api.h defines how many active listen requests are possible.</span></span>
- <span data-ttu-id="112c2-2129">**NX_NOT_CLOSED**(0x35) 제공된 서버 소켓이 닫힘 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2129">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="112c2-2130">**NX_ALREADY_BOUND**(0x22) 제공된 서버 소켓이 이미 포트에 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2130">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="112c2-2131">**NX_DUPLICATE_LISTEN**(0x34) 이 포트의 활성 수신 대기 요청이 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2131">**NX_DUPLICATE_LISTEN** (0x34) There is already an active listen request for this port.</span></span>
- <span data-ttu-id="112c2-2132">**NX_INVALID_PORT**(0x46) 잘못된 포트가 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2132">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="112c2-2133">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="112c2-2134">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2135">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2136">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2136">Allowed From</span></span>

<span data-ttu-id="112c2-2137">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2138">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2138">Preemption Possible</span></span>

<span data-ttu-id="112c2-2139">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2139">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2140">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2140">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket.
        This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created
        and the link is enabled "my_pool" packet pool has already
        been created.
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
        Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

    /* Wait for 200 ticks for the client socket connection
        to complete. */
    status = nx_tcp_server_socket_accept(&server_socket, 200);

    /* Check for a successful connection. */
    if (status == NX_SUCCESS)
    {
        /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
        nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
            NX_WAIT_FOREVER);

        /* Place "Hello_and_Goodbye" in the packet. */
        nx_packet_data_append(my_packet, "Hello_and_Goodbye",
            sizeof("Hello_and_Goodbye"),
            &my_pool,
            NX_WAIT_FOREVER);

        /* Send "Hello_and_Goodbye" to client. */
        nx_tcp_socket_send(&server_socket, my_packet, 200);

        /* Check for an error. */
        if (status)
        {
            /* Error, release the packet. */
            nx_packet_release(my_packet);
        }
        /* Now disconnect the server socket from the client. */
        nx_tcp_socket_disconnect(&server_socket, 200);
    }

    /* Unaccept the server socket. Note that unaccept is called
        even if disconnect or accept fails. */
    nx_tcp_server_socket_unaccept(&server_socket);

    /* Setup server socket for listening with this socket
    again. */
    nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
}

/* We are now done so unlisten on server port 12. */
nx_tcp_server_socket_unlisten(&my_ip, 12);

/* Delete the server socket. */
nx_tcp_socket_delete(&server_socket);
```

### <a name="see-also"></a><span data-ttu-id="112c2-2141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2141">See Also</span></span>

- <span data-ttu-id="112c2-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="112c2-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="112c2-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-2151">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2151">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="112c2-2152">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2152">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="112c2-2153">TCP 포트에서 클라이언트 연결을 위해 다시 수신 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2153">Re-listen for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2154">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2154">Prototype</span></span>

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-2155">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2155">Description</span></span>

<span data-ttu-id="112c2-2156">이전에 수신 대기에 사용하도록 설정한 포트에서 연결을 수신하면 이 서비스가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2156">This service is called after a connection has been received on a port that was setup previously for listening.</span></span> <span data-ttu-id="112c2-2157">이 서비스는 다음 클라이언트 연결에 사용하도록 새 서버 소켓을 제공하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2157">The main purpose of this service is to provide a new server socket for the next client connection.</span></span> <span data-ttu-id="112c2-2158">연결 요청이 큐에 있는 경우 이 서비스 호출 중에 바로 연결이 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2158">If a connection request is queued, the connection will be processed immediately during this service call.</span></span>

<span data-ttu-id="112c2-2159">새 서버 소켓에 대한 연결이 있는 경우 원래 수신 대기 요청에서 지정한 것과 동일한 콜백 루틴도 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2159">*The same callback routine specified by the original listen request is also called when a connection is present for this new server socket.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2160">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2160">Parameters</span></span>

- <span data-ttu-id="112c2-2161">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2161">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-2162">**port** 다시 수신 대기할 포트 번호(1-0xFFFF)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2162">**port** Port number to re-listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="112c2-2163">**socket_ptr** 다음 클라이언트 연결에 사용할 소켓입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2163">**socket_ptr** Socket to use for the next client connection.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2164">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2164">Return Values</span></span>
- <span data-ttu-id="112c2-2165">**NX_SUCCESS**(0x00) TCP 포트 다시 수신 대기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2165">**NX_SUCCESS** (0x00) Successful TCP port re-listen.</span></span>
- <span data-ttu-id="112c2-2166">**NX_NOT_CLOSED**(0x35) 제공된 서버 소켓이 닫힘 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2166">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="112c2-2167">**NX_ALREADY_BOUND**(0x22) 제공된 서버 소켓이 이미 포트에 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2167">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="112c2-2168">**NX_INVALID_RELISTEN**(0x47) 이 포트에 유효한 소켓 포인터가 이미 있거나 지정된 포트에 활성 수신 대기 요청이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2168">**NX_INVALID_RELISTEN** (0x47) There is already a valid socket pointer for this port or the port specified does not have a listen request active.</span></span>
- <span data-ttu-id="112c2-2169">**NX_CONNECTION_PENDING**(0x48) 큐에 대기된 연결 요청이 있었고 이 호출 중에 처리되었던 것을 제외하면 NX_SUCCESS와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2169">**NX_CONNECTION_PENDING** (0x48) Same as NX_SUCCESS, except there was a queued connection request and it was processed during this call.</span></span>
- <span data-ttu-id="112c2-2170">**NX_INVALID_PORT**(0x46) 잘못된 포트가 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2170">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="112c2-2171">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 수신 대기 콜백 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2171">**NX_PTR_ERROR** (0x07) Invalid IP or listen callback pointer.</span></span>
- <span data-ttu-id="112c2-2172">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2172">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2173">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2173">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2174">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2174">Allowed From</span></span>

<span data-ttu-id="112c2-2175">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2175">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2176">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2176">Preemption Possible</span></span>

<span data-ttu-id="112c2-2177">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2177">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2178">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2178">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
    }

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
    "port_12_semaphore" has already been created with an initial
        count of 0.
        "my_ip" has already been created and the link is enabled.
        "my_pool" packet pool has already been created. */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);
    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
        complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is
        called even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
        again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="112c2-2179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2179">See Also</span></span>

- <span data-ttu-id="112c2-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="112c2-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="112c2-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="112c2-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-2189">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2189">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="112c2-2190">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="112c2-2190">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="112c2-2191">수신 대기 포트와 소켓 간 연결을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2191">Remove socket association with listening port</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2192">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2192">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-2193">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2193">Description</span></span>

<span data-ttu-id="112c2-2194">이 서비스는 이 서버 소켓과 지정된 서버 포트 간 연결을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2194">This service removes the association between this server socket and the specified server port.</span></span> <span data-ttu-id="112c2-2195">애플리케이션은 연결 해제 후 또는 호출 수락 실패 후 이 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2195">The application must call this service after a disconnection or after an unsuccessful accept call.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2196">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2196">Parameters</span></span>

- <span data-ttu-id="112c2-2197">**socket_ptr** 이전에 설정한 서버 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2197">**socket_ptr** Pointer to previously setup server socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2198">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2198">Return Values</span></span>

- <span data-ttu-id="112c2-2199">**NX_SUCCESS**(0x00) 서버 소켓을 수락하지 않는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2199">**NX_SUCCESS** (0x00) Successful server socket unaccept.</span></span>
- <span data-ttu-id="112c2-2200">**NX_NOT_LISTEN_STATE**(0x36) 서버 소켓이 부적절한 상태이며 연결 해제되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2200">**NX_NOT_LISTEN_STATE** (0x36) Server socket is in an improper state, and is probably not disconnected.</span></span>
- <span data-ttu-id="112c2-2201">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2201">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2202">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2202">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2203">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2203">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2204">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2204">Allowed From</span></span>

<span data-ttu-id="112c2-2205">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2206">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2206">Preemption Possible</span></span>

<span data-ttu-id="112c2-2207">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2207">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2208">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2208">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
        */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request
            is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet,
                "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called even
            if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="112c2-2209">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2209">See Also</span></span>

- <span data-ttu-id="112c2-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,</span></span>
- <span data-ttu-id="112c2-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="112c2-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="112c2-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="112c2-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-2218">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2218">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="112c2-2219">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="112c2-2219">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="112c2-2220">TCP 포트에서 클라이언트 연결 수신 대기를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2220">Disable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2221">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2221">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a><span data-ttu-id="112c2-2222">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2222">Description</span></span>

<span data-ttu-id="112c2-2223">이 서비스는 지정된 TCP 포트에서 클라이언트 연결 요청 수신 대기를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2223">This service disables listening for a client connection request on the specified TCP port.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2224">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2224">Parameters</span></span>

- <span data-ttu-id="112c2-2225">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2225">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-2226">**port** 수신 대기를 사용하지 않도록 설정할 포트 번호(0-0xFFFF)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2226">**port** Number of port to disable listening (0 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2227">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2227">Return Values</span></span>

- <span data-ttu-id="112c2-2228">**NX_SUCCESS**(0x00) TCP 수신 대기를 사용하지 않도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2228">**NX_SUCCESS** (0x00) Successful TCP listen disable.</span></span>
- <span data-ttu-id="112c2-2229">**NX_ENTRY_NOT_FOUND**(0x16) 지정된 포트의 수신 대기가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2229">**NX_ENTRY_NOT_FOUND** (0x16) Listening was not enabled for the specified port.</span></span>
- <span data-ttu-id="112c2-2230">**NX_INVALID_PORT**(0x46) 잘못된 포트가 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2230">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="112c2-2231">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2231">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-2232">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2232">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2233">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2233">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2234">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2234">Allowed From</span></span>

<span data-ttu-id="112c2-2235">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2235">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2236">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2236">Preemption Possible</span></span>

<span data-ttu-id="112c2-2237">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2237">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2238">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2238">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request is
            present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"), &my_pool,
                NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }
            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }
        /* Unaccept the server socket. Note that unaccept is called even if
        disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="112c2-2239">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2239">See Also</span></span>

- <span data-ttu-id="112c2-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="112c2-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="112c2-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="112c2-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="112c2-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-2249">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2249">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="112c2-2250">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2250">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="112c2-2251">검색에 사용할 수 있는 바이트 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2251">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2252">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2252">Prototype</span></span>

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="112c2-2253">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2253">Description</span></span>

<span data-ttu-id="112c2-2254">이 서비스는 지정된 TCP 소켓에서 검색에 사용할 수 있는 바이트 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2254">This service obtains the number of bytes available for retrieval in the specified TCP socket.</span></span> <span data-ttu-id="112c2-2255">TCP 소켓은 이미 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2255">Note that the TCP socket must already be connected.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2256">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2256">Parameters</span></span>

- <span data-ttu-id="112c2-2257">**socket_ptr** 이전에 만들고 연결한 TCP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2257">**socket_ptr** Pointer to previously created and connected TCP socket.</span></span>
- <span data-ttu-id="112c2-2258">**bytes_available** 사용할 수 있는 바이트 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2258">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2259">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2259">Return Values</span></span>

- <span data-ttu-id="112c2-2260">**NX_SUCCESS**(0x00) 서비스가 성공적으로 실행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2260">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="112c2-2261">읽을 수 있는 바이트 수가 호출자에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2261">Number of bytes available for read is returned to the caller.</span></span>
- <span data-ttu-id="112c2-2262">**NX_NOT_CONNECTED**(0x38) 소켓이 연결된 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2262">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="112c2-2263">**NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2263">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="112c2-2264">**NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2264">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="112c2-2265">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2265">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2266">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2266">Allowed From</span></span>

<span data-ttu-id="112c2-2267">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2267">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2268">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2268">Preemption Possible</span></span>

<span data-ttu-id="112c2-2269">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2269">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2270">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2270">Example</span></span>

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2271">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2271">See Also</span></span>

- <span data-ttu-id="112c2-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="112c2-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="112c2-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="112c2-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="112c2-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-2281">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2281">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_create"></a><span data-ttu-id="112c2-2282">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2282">nx_tcp_socket_create</span></span>

<span data-ttu-id="112c2-2283">TCP 클라이언트 또는 서버 소켓을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2283">Create TCP client or server socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2284">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2284">Prototype</span></span>

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="112c2-2285">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2285">Description</span></span>

<span data-ttu-id="112c2-2286">이 서비스는 지정된 IP 인스턴스의 TCP 클라이언트 또는 서버 소켓을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2286">This service creates a TCP client or server socket for the specified IP instance.</span></span>

<span data-ttu-id="112c2-2287">애플리케이션 콜백 루틴은 이 IP 인스턴스와 연결된 스레드에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2287">*Application callback routines are called from the thread associated with this IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2288">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2288">Parameters</span></span>

- <span data-ttu-id="112c2-2289">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2289">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-2290">**socket_ptr** 새 TCP 소켓 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2290">**socket_ptr** Pointer to new TCP socket control block.</span></span>
- <span data-ttu-id="112c2-2291">**name** 이 TCP 소켓의 애플리케이션 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2291">**name** Application name for this TCP socket.</span></span>
- <span data-ttu-id="112c2-2292">**type_of_service** 전송할 서비스 유형을 정의합니다. 올바른 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2292">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>

- <span data-ttu-id="112c2-2293">NX_IP_NORMAL(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-2293">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="112c2-2294">NX_IP_MIN_DELAY(0x00100000)</span><span class="sxs-lookup"><span data-stu-id="112c2-2294">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="112c2-2295">NX_IP_MAX_DATA(0x00080000)</span><span class="sxs-lookup"><span data-stu-id="112c2-2295">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="112c2-2296">NX_IP_MAX_RELIABLE(0x00040000)</span><span class="sxs-lookup"><span data-stu-id="112c2-2296">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="112c2-2297">NX_IP_MIN_COST(0x00020000)</span><span class="sxs-lookup"><span data-stu-id="112c2-2297">NX_IP_MIN_COST (0x00020000)</span></span>

- <span data-ttu-id="112c2-2298">**fragment** IP 조각화 허용 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2298">**fragment**  Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="112c2-2299">NX_FRAGMENT_OKAY(0x0)가 지정되면 IP 조각화가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2299">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="112c2-2300">NX_DONT_FRAGMENT(0x4000)가 지정되면 IP 조각화가 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2300">If  NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="112c2-2301">**time_to_live** 이 패킷이 제거되기 전까지 통과할 수 있는 라우터 수를 정의하는 8비트 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2301">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="112c2-2302">기본값은 NX_IP_TIME_TO_LIVE로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2302">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="112c2-2303">**window_size** 이 소켓의 수신 큐에 허용되는 최대 바이트 수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2303">**window_size** Defines the maximum number of bytes allowed in the receive queue for this socket</span></span>
- <span data-ttu-id="112c2-2304">**urgent_data_callback** 수신 스트림에서 긴급 데이터가 검색될 때마다 호출되는 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2304">**urgent_data_callback** Application function that is called whenever urgent data is detected in the receive stream.</span></span> <span data-ttu-id="112c2-2305">이 값이 NX_NULL이면 긴급 데이터는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2305">If this value is NX_NULL, urgent data is ignored.</span></span>
- <span data-ttu-id="112c2-2306">**disconnect_callback** 연결의 다른 쪽 끝에 있는 소켓이 연결을 해제할 때마다 호출되는 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2306">**disconnect_callback** Application function that is called whenever a disconnect is issued by the socket at the other end of the connection.</span></span> <span data-ttu-id="112c2-2307">이 값이 NX_NULL이면 연결 해제 콜백 함수는 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2307">If this value is NX_NULL, the disconnect callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2308">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2308">Return Values</span></span>
- <span data-ttu-id="112c2-2309">**NX_SUCCESS**(0x00) TCP 클라이언트 소켓 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2309">**NX_SUCCESS** (0x00) Successful TCP client socket create.</span></span>
- <span data-ttu-id="112c2-2310">**NX_OPTION_ERROR**(0x0A) type-of-service, fragment, window size 또는 time-tolive 옵션이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2310">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, invalid window size, or time-tolive option.</span></span>
- <span data-ttu-id="112c2-2311">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2311">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="112c2-2312">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2312">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2313">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2313">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2314">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2314">Allowed From</span></span>

<span data-ttu-id="112c2-2315">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2315">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2316">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2316">Preemption Possible</span></span>

<span data-ttu-id="112c2-2317">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2317">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2318">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2318">Example</span></span>

```C
/* Create a TCP client socket on the previously created IP instance,
    with normal delivery, IP fragmentation enabled, 0x80 time to
    live, a 200-byte receive window, no urgent callback routine, and
    the "client_disconnect" routine to handle disconnection initiated
    from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
    "Client Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY,
    0x80, 200, NX_NULL
    client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
    to be bound. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2319">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2319">See Also</span></span>

- <span data-ttu-id="112c2-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="112c2-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="112c2-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="112c2-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="112c2-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-2329">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2329">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_delete"></a><span data-ttu-id="112c2-2330">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-2330">nx_tcp_socket_delete</span></span>

<span data-ttu-id="112c2-2331">TCP 소켓을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2331">Delete TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2332">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2332">Prototype</span></span>

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-2333">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2333">Description</span></span>

<span data-ttu-id="112c2-2334">이 서비스는 이전에 만든 TCP 소켓을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2334">This service deletes a previously created TCP socket.</span></span> <span data-ttu-id="112c2-2335">소켓이 여전히 바인딩되어 있거나 연결되어 있으면 서비스는 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2335">If the socket is still bound or connected, the service returns an error code.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2336">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2336">Parameters</span></span>

- <span data-ttu-id="112c2-2337">**socket_ptr** 이전에 만든 TCP 소켓입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2337">**socket_ptr** Previously created TCP socket</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2338">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2338">Return Values</span></span>

- <span data-ttu-id="112c2-2339">**NX_SUCCESS**(0x00) 소켓을 삭제하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2339">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="112c2-2340">**NX_NOT_CREATED**(0x27) 소켓이 만들어지지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2340">**NX_NOT_CREATED** (0x27) Socket was not created.</span></span>
- <span data-ttu-id="112c2-2341">**NX_STILL_BOUND**(0x42) 소켓이 여전히 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2341">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="112c2-2342">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2342">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2343">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2343">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2344">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2344">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2345">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2345">Allowed From</span></span>

<span data-ttu-id="112c2-2346">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2346">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2347">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2347">Preemption Possible</span></span>

<span data-ttu-id="112c2-2348">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2348">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2349">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2349">Example</span></span>

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2350">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2350">See Also</span></span>

- <span data-ttu-id="112c2-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="112c2-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="112c2-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="112c2-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="112c2-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="112c2-2360">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2360">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="112c2-2361">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2361">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="112c2-2362">클라이언트 및 서버 소켓 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2362">Disconnect client and server socket connections</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2363">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2363">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-2364">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2364">Description</span></span>

<span data-ttu-id="112c2-2365">이 서비스는 설정된 클라이언트 또는 서버 소켓 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2365">This service disconnects an established client or server socket connection.</span></span> <span data-ttu-id="112c2-2366">먼저 요청을 거부한 후 서버 소켓 연결을 해제해야 하며 연결이 해제된 클라이언트 소켓은 다른 연결 요청에 사용할 준비가 된 상태로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2366">A disconnect of a server socket should be followed by an unaccept request, while a client socket that is disconnected is left in a state ready for another connection request.</span></span> <span data-ttu-id="112c2-2367">연결 해제 프로세스를 즉시 완료할 수 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2367">If the disconnect process cannot finish immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2368">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2368">Parameters</span></span>

- <span data-ttu-id="112c2-2369">**socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2369">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="112c2-2370">**wait_option** 연결 해제가 진행 중인 동안 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2370">**wait_option** Defines how the service behaves while the disconnection is in progress.</span></span> <span data-ttu-id="112c2-2371">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2371">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-2372">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-2372">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-2373">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-2374">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-2374">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2375">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2375">Return Values</span></span>

- <span data-ttu-id="112c2-2376">**NX_SUCCESS**(0x00) 소켓 연결 해제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2376">**NX_SUCCESS** (0x00) Successful socket disconnect.</span></span>
- <span data-ttu-id="112c2-2377">**NX_NOT_CONNECTED**(0x38) 지정된 소켓이 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2377">**NX_NOT_CONNECTED** (0x38) Specified socket is not connected.</span></span>
- <span data-ttu-id="112c2-2378">**NX_IN_PROGRESS**(0x37) 대기 안 함으로 지정되었으므로 연결 해제가 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2378">**NX_IN_PROGRESS** (0x37) Disconnect is in progress, no wait was specified.</span></span>
- <span data-ttu-id="112c2-2379">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2379">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="112c2-2380">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2380">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2381">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2381">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2382">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2382">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2383">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2383">Allowed From</span></span>

<span data-ttu-id="112c2-2384">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2384">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2385">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2385">Preemption Possible</span></span>

<span data-ttu-id="112c2-2386">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2386">Yes</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2387">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2387">Example</span></span>

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2388">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2388">See Also</span></span>

- <span data-ttu-id="112c2-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="112c2-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="112c2-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="112c2-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="112c2-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="112c2-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect_complete_notify"></a><span data-ttu-id="112c2-2398">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2398">nx_tcp_socket_disconnect_complete_notify</span></span>

<span data-ttu-id="112c2-2399">TCP 연결 해제 완료 알림 콜백 함수를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2399">Install TCP disconnect complete notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2400">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2400">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="112c2-2401">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2401">Description</span></span>

<span data-ttu-id="112c2-2402">이 서비스는 소켓 연결 해제 작업이 완료된 후 호출되는 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2402">This service registers a callback function which is invoked after a socket disconnect operation is completed.</span></span> <span data-ttu-id="112c2-2403">TCP 소켓 연결 해제 완료 콜백 함수는 옵션</span><span class="sxs-lookup"><span data-stu-id="112c2-2403">The TCP socket disconnect complete callback function is available if NetX is built with the option</span></span>

- <span data-ttu-id="112c2-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** 가 정의된 NetX가 빌드되어 있는 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2405">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2405">Parameters</span></span>

- <span data-ttu-id="112c2-2406">**socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2406">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="112c2-2407">**tcp_disconnect_complete_notify** 설치할 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2407">**tcp_disconnect_complete_notify** The callback function to be installed.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2408">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2408">Return Values</span></span>
- <span data-ttu-id="112c2-2409">**NX_SUCCESS**(0x00) 콜백 함수를 성공적으로 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2409">**NX_SUCCESS** (0x00) Successfully registered the callback function.</span></span>
- <span data-ttu-id="112c2-2410">**NX_NOT_SUPPORTED**(0x4B) 확장된 알림 기능은 NetX 라이브러리에 빌드되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2410">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="112c2-2411">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2411">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2412">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2412">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2413">**NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2413">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2414">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2414">Allowed From</span></span>

<span data-ttu-id="112c2-2415">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2415">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2416">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2416">Preemption Possible</span></span>

<span data-ttu-id="112c2-2417">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2417">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2418">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2418">Example</span></span>

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a><span data-ttu-id="112c2-2419">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2419">See Also</span></span>

- <span data-ttu-id="112c2-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,</span></span>
- <span data-ttu-id="112c2-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="112c2-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="112c2-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="112c2-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="112c2-2424">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="112c2-2424">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="112c2-2425">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2425">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_establish_notify"></a><span data-ttu-id="112c2-2426">nx_tcp_socket_establish_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2426">nx_tcp_socket_establish_notify</span></span>

<span data-ttu-id="112c2-2427">TCP 설정 알림 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2427">Set TCP establish notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2428">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2428">Prototype</span></span>

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="112c2-2429">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2429">Description</span></span>

<span data-ttu-id="112c2-2430">이 서비스는 콜백 함수를 등록합니다. 이 함수는 TCP 소켓이 연결된 후 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2430">This service registers a callback function, which is called after a TCP socket makes a connection.</span></span> <span data-ttu-id="112c2-2431">TCP 소켓 설정 콜백 함수는 옵션 ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** 가 정의된 NetX가 빌드되어 있는 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2431">The TCP socket establish callback function is available if NetX is built with the option ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2432">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2432">Parameters</span></span>

- <span data-ttu-id="112c2-2433">**socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2433">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="112c2-2434">**tcp_establish_notify** TCP 연결이 설정된 후 호출되는 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2434">**tcp_establish_notify** Callback function invoked after a TCP connection is established.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2435">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2435">Return Values</span></span>

- <span data-ttu-id="112c2-2436">**NX_SUCCESS**(0x00) 알림 함수를 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2436">**NX_SUCCESS** (0x00) Successfully sets the notify function.</span></span>
- <span data-ttu-id="112c2-2437">**NX_NOT_SUPPORTED**(0x4B) 확장된 알림 기능은 NetX 라이브러리에 빌드되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2437">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="112c2-2438">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2438">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2439">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2439">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2440">**NX_NOT_ENABLED**(0x14) 애플리케이션에서 TCP를 사용하도록 설정하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2440">**NX_NOT_ENABLED** (0x14) TCP has not been enabled by the application.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2441">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2441">Allowed From</span></span>

<span data-ttu-id="112c2-2442">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2442">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2443">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2443">Preemption Possible</span></span>

<span data-ttu-id="112c2-2444">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2444">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2445">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2445">Example</span></span>

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="112c2-2446">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2446">See Also</span></span>

- <span data-ttu-id="112c2-2447">nx_tcp_enable, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2447">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="112c2-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="112c2-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="112c2-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="112c2-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="112c2-2452">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2452">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="112c2-2453">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2453">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="112c2-2454">TCP 소켓 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2454">Retrieve information about TCP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2455">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2455">Prototype</span></span>

```C
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```

### <a name="description"></a><span data-ttu-id="112c2-2456">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2456">Description</span></span>

<span data-ttu-id="112c2-2457">이 서비스는 지정된 TCP 소켓 인스턴스의 TCP 소켓 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2457">This service retrieves information about TCP socket activities for the specified TCP socket instance.</span></span>

<span data-ttu-id="112c2-2458">대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2458">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2459">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2459">Parameters</span></span>

- <span data-ttu-id="112c2-2460">**socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2460">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="112c2-2461">**tcp_packets_sent** 소켓의 송신된 총 TCP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2461">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent on socket.</span></span>
- <span data-ttu-id="112c2-2462">**tcp_bytes_sent** 소켓의 송신된 총 TCP 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2462">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent on socket.</span></span>
- <span data-ttu-id="112c2-2463">**tcp_packets_received** 소켓의 수신된 총 TCP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2463">**tcp_packets_received** Pointer to destination of the total number of TCP packets received on socket.</span></span>
- <span data-ttu-id="112c2-2464">**tcp_bytes_received** 소켓의 수신된 총 TCP 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2464">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received on socket.</span></span>
- <span data-ttu-id="112c2-2465">**tcp_retransmit_packets** 총 TCP 패킷 재전송 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2465">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packet retransmissions.</span></span>
- <span data-ttu-id="112c2-2466">**tcp_packets_queued** 소켓의 큐에 대기된 총 TCP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2466">**tcp_packets_queued** Pointer to destination of the total number of queued TCP packets on socket.</span></span>
- <span data-ttu-id="112c2-2467">**tcp_checksum_errors** 소켓의 체크섬 오류가 있는 총 TCP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2467">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors on socket.</span></span>
- <span data-ttu-id="112c2-2468">**tcp_socket_state** 소켓의 현재 상태 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2468">**tcp_socket_state** Pointer to destination of the socket’s current state.</span></span>
- <span data-ttu-id="112c2-2469">**tcp_transmit_queue_depth** 여전히 큐에서 ACK를 대기 중인 총 전송 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2469">**tcp_transmit_queue_depth** Pointer to destination of the total number of transmit packets still queued waiting for ACK.</span></span>
- <span data-ttu-id="112c2-2470">**tcp_transmit_window** 현재 전송 창 크기 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2470">**tcp_transmit_window** Pointer to destination of the current transmit window size.</span></span>
- <span data-ttu-id="112c2-2471">**tcp_receive_window** 현재 수신 창 크기 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2471">**tcp_receive_window** Pointer to destination of the current receive window size.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2472">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2472">Return Values</span></span>

- <span data-ttu-id="112c2-2473">**NX_SUCCESS**(0x00) TCP 소켓 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2473">**NX_SUCCESS** (0x00) Successful TCP socket information retrieval.</span></span>
- <span data-ttu-id="112c2-2474">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2474">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2475">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2475">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2476">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2476">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2477">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2477">Return Values</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="allowed-from"></a><span data-ttu-id="112c2-2478">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2478">Allowed From</span></span>

<span data-ttu-id="112c2-2479">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2479">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2480">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2480">Preemption Possible</span></span>

<span data-ttu-id="112c2-2481">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2481">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2482">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2482">Example</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2483">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2483">See Also</span></span>

- <span data-ttu-id="112c2-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="112c2-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="112c2-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="112c2-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="112c2-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="112c2-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="112c2-2493">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2493">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="112c2-2494">소켓의 MSS를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2494">Get MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2495">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2495">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="112c2-2496">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2496">Description</span></span>

<span data-ttu-id="112c2-2497">이 서비스는 지정된 소켓의 로컬 MSS(최대 세그먼트 크기)를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2497">This service retrieves the specified socket's local Maximum Segment Size (MSS).</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2498">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2498">Parameters</span></span>

- <span data-ttu-id="112c2-2499">**socket_ptr** 이전에 만든 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2499">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="112c2-2500">**mss** MSS 반환 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2500">**mss** Destination for returning MSS.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2501">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2501">Return Values</span></span>

- <span data-ttu-id="112c2-2502">**NX_SUCCESS**(0x00) MSS를 가져오는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2502">**NX_SUCCESS** (0x00) Successful MSS get.</span></span>
- <span data-ttu-id="112c2-2503">**NX_PTR_ERROR**(0x07) 잘못된 소켓 또는 MSS 대상 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2503">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="112c2-2504">**NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2504">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="112c2-2505">**NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2505">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2506">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2506">Allowed From</span></span>

<span data-ttu-id="112c2-2507">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2508">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2508">Preemption Possible</span></span>

<span data-ttu-id="112c2-2509">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2509">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2510">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2510">Example</span></span>

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2511">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2511">See Also</span></span>

- <span data-ttu-id="112c2-2512">nx_tcp_enable, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2512">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2513">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2513">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="112c2-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="112c2-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="112c2-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="112c2-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="112c2-2517">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="112c2-2517">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="112c2-2518">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2518">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="112c2-2519">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2519">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="112c2-2520">피어 TCP 소켓의 MSS를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2520">Get MSS of the peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2521">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2521">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="112c2-2522">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2522">Description</span></span>

<span data-ttu-id="112c2-2523">이 서비스는 피어 소켓에서 보급한 MSS(최대 세그먼트 크기)를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2523">This service retrieves the Maximum Segment Size (MSS) advertised by the peer socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2524">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2524">Parameters</span></span>

- <span data-ttu-id="112c2-2525">**socket_ptr** 이전에 만들고 연결한 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2525">**socket_ptr** Pointer to previously created and connected socket.</span></span>
- <span data-ttu-id="112c2-2526">**mss** MSS를 반환하는 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2526">**mss** Destination for returning the MSS.</span></span>


### <a name="return-values"></a><span data-ttu-id="112c2-2527">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2527">Return Values</span></span>

- <span data-ttu-id="112c2-2528">**NX_SUCCESS**(0x00) 피어 MSS를 가져오는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2528">**NX_SUCCESS** (0x00) Successful peer MSS get.</span></span>
- <span data-ttu-id="112c2-2529">**NX_PTR_ERROR**(0x07) 잘못된 소켓 또는 MSS 대상 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2529">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="112c2-2530">**NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2530">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="112c2-2531">**NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2531">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2532">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2532">Allowed From</span></span>

<span data-ttu-id="112c2-2533">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2533">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2534">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2534">Preemption Possible</span></span>

<span data-ttu-id="112c2-2535">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2535">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2536">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2536">Example</span></span>

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2537">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2537">See Also</span></span>

- <span data-ttu-id="112c2-2538">nx_tcp_enable, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2538">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2539">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2539">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="112c2-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="112c2-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="112c2-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="112c2-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="112c2-2543">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="112c2-2543">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="112c2-2544">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2544">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="112c2-2545">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2545">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="112c2-2546">소켓의 MSS를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2546">Set MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2547">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2547">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a><span data-ttu-id="112c2-2548">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2548">Description</span></span>

<span data-ttu-id="112c2-2549">이 서비스는 지정된 소켓의 MSS(최대 세그먼트 크기)를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2549">This service sets the specified socket's Maximum Segment Size (MSS).</span></span> <span data-ttu-id="112c2-2550">MSS 값은 네트워크 인터페이스 IP MTU 내에 있어야 하며 IP 및 TCP 헤더 공간이 허용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2550">Note the MSS value must be within the network interface IP MTU, allowing room for IP and TCP headers.</span></span>

<span data-ttu-id="112c2-2551">TCP 소켓이 연결 프로세스를 시작하기 전에 이 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2551">This service should be used before a TCP socket starts the connection process.</span></span> <span data-ttu-id="112c2-2552">TCP 연결이 설정된 후 이 서비스를 사용하면 새 값이 연결에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2552">If the service is used after a TCP connection is established, the new value has no effect on the connection.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2553">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2553">Parameters</span></span>

- <span data-ttu-id="112c2-2554">**socket_ptr** 이전에 만든 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2554">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="112c2-2555">**mss** 설정할 MSS 값입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2555">**mss** Value of MSS to set.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2556">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2556">Return Values</span></span>

- <span data-ttu-id="112c2-2557">**NX_SUCCESS**(0x00) MSS 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2557">**NX_SUCCESS** (0x00) Successful MSS set.</span></span>
- <span data-ttu-id="112c2-2558">**NX_SIZE_ERROR**(0x09) 지정된 MSS 값이 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2558">**NX_SIZE_ERROR** (0x09) Specified MSS value is too large.</span></span>
- <span data-ttu-id="112c2-2559">**NX_NOT_CONNECTED**(0x38) TCP 연결이 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2559">**NX_NOT_CONNECTED** (0x38) TCP connection has not been established</span></span>
- <span data-ttu-id="112c2-2560">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2560">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2561">**NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2561">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="112c2-2562">**NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2562">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2563">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2563">Allowed From</span></span>

<span data-ttu-id="112c2-2564">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2564">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2565">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2565">Preemption Possible</span></span>

<span data-ttu-id="112c2-2566">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2566">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2567">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2567">Example</span></span>

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2568">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2568">See Also</span></span>

- <span data-ttu-id="112c2-2569">nx_tcp_enable, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2569">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2570">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2570">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="112c2-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="112c2-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="112c2-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="112c2-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="112c2-2574">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="112c2-2574">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="112c2-2575">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2575">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="112c2-2576">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2576">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="112c2-2577">피어 TCP 소켓에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2577">Retrieve information about peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2578">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2578">Prototype</span></span>

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a><span data-ttu-id="112c2-2579">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2579">Description</span></span>

<span data-ttu-id="112c2-2580">이 서비스는 IP 네트워크를 통해 연결된 TCP 소켓의 피어 IP 주소 및 포트 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2580">This service retrieves peer IP address and port information for the connected TCP socket over IP network.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2581">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2581">Parameters</span></span>

- <span data-ttu-id="112c2-2582">**socket_ptr** 이전에 만든 TCP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2582">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="112c2-2583">**peer_ip_address** 호스트 바이트 순서대로 표시된 피어 IP 주소 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2583">**peer_ip_address** Pointer to destination for peer IP address, in host byte order.</span></span>
- <span data-ttu-id="112c2-2584">**peer_port** 호스트 바이트 순서대로 표시된 피어 포트 번호 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2584">**peer_port** Pointer to destination for peer port number, in host byte order.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2585">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2585">Return Values</span></span>

- <span data-ttu-id="112c2-2586">**NX_SUCCESS**(0x00) 서비스가 성공적으로 실행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2586">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="112c2-2587">피어 IP 주소와 포트 번호는 호출자에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2587">Peer IP address and port number are returned to the caller.</span></span>
- <span data-ttu-id="112c2-2588">**NX_NOT_CONNECTED**(0x38) 소켓이 연결된 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2588">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="112c2-2589">**NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2589">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="112c2-2590">**NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2590">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="112c2-2591">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2591">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2592">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2592">Allowed From</span></span>

<span data-ttu-id="112c2-2593">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2593">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2594">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2594">Preemption Possible</span></span>

<span data-ttu-id="112c2-2595">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2595">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2596">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2596">Example</span></span>

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2597">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2597">See Also</span></span>

- <span data-ttu-id="112c2-2598">nx_tcp_enable, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2598">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2599">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2599">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="112c2-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="112c2-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="112c2-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="112c2-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="112c2-2603">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="112c2-2603">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="112c2-2604">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2604">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_receive"></a><span data-ttu-id="112c2-2605">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2605">nx_tcp_socket_receive</span></span>

<span data-ttu-id="112c2-2606">TCP 소켓에서 데이터를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2606">Receive data from TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2607">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2607">Prototype</span></span>

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-2608">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2608">Description</span></span>

<span data-ttu-id="112c2-2609">이 서비스는 지정된 소켓에서 TCP 데이터를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2609">This service receives TCP data from the specified socket.</span></span> <span data-ttu-id="112c2-2610">지정된 소켓에 큐에 대기된 데이터가 없으면 제공된 대기 옵션에 따라 호출자가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2610">If no data are queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="112c2-2611">*NX_SUCCESS* 가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 해당 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2611">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2612">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2612">Parameters</span></span>

- <span data-ttu-id="112c2-2613">**socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2613">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="112c2-2614">**packet_ptr** TCP 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2614">**packet_ptr** Pointer to TCP packet pointer.</span></span>
- <span data-ttu-id="112c2-2615">**wait_option** 현재 이 소켓에 큐에 대기된 데이터가 없는 경우 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2615">**wait_option** Defines how the service behaves if no data are currently queued on this socket.</span></span> <span data-ttu-id="112c2-2616">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2616">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-2617">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-2617">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-2618">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-2619">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-2619">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2620">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2620">Return Values</span></span>
- <span data-ttu-id="112c2-2621">**NX_SUCCESS**(0x00) 소켓 데이터 수신에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2621">**NX_SUCCESS** (0x00) Successful socket data receive.</span></span>
- <span data-ttu-id="112c2-2622">**NX_NOT_BOUND**(0x24) 소켓이 아직 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2622">**NX_NOT_BOUND** (0x24) Socket is not bound yet.</span></span>
- <span data-ttu-id="112c2-2623">**NX_NO_PACKET**(0x01) 수신된 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2623">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="112c2-2624">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2624">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="112c2-2625">**NX_NOT_CONNECTED**(0x38) 소켓이 더 이상 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2625">**NX_NOT_CONNECTED** (0x38) The socket is no longer connected.</span></span>
- <span data-ttu-id="112c2-2626">**NX_PTR_ERROR**(0x07) 잘못된 소켓 또는 반환 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2626">**NX_PTR_ERROR** (0x07) Invalid socket or return packet pointer.</span></span>
- <span data-ttu-id="112c2-2627">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2627">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2628">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2628">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2629">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2629">Allowed From</span></span>

<span data-ttu-id="112c2-2630">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2630">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2631">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2631">Preemption Possible</span></span>

<span data-ttu-id="112c2-2632">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2632">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2633">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2633">Example</span></span>

<span data-ttu-id="112c2-2634">/\* Receive a packet from the previously created and connected TCP client socket.</span><span class="sxs-lookup"><span data-stu-id="112c2-2634">/\* Receive a packet from the previously created and connected TCP client socket.</span></span> <span data-ttu-id="112c2-2635">If no packet is available, wait for 200 timer ticks before giving up.</span><span class="sxs-lookup"><span data-stu-id="112c2-2635">If no packet is available, wait for 200 timer ticks before giving up.</span></span> <span data-ttu-id="112c2-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span><span class="sxs-lookup"><span data-stu-id="112c2-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span></span>

<span data-ttu-id="112c2-2637">/\* If status is NX_SUCCESS, the received packet is pointed to by "packet_ptr".</span><span class="sxs-lookup"><span data-stu-id="112c2-2637">/\* If status is NX_SUCCESS, the received packet is pointed to by "packet_ptr".</span></span> */

### <a name="see-also"></a><span data-ttu-id="112c2-2638">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2638">See Also</span></span>

- <span data-ttu-id="112c2-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="112c2-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="112c2-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="112c2-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="112c2-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="112c2-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="112c2-2648">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2648">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="112c2-2649">수신된 패킷에 대해 애플리케이션에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2649">Notify application of received packets</span></span>


### <a name="prototype"></a><span data-ttu-id="112c2-2650">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2650">Prototype</span></span>

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="112c2-2651">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2651">Description</span></span>

<span data-ttu-id="112c2-2652">이 서비스는 애플리케이션에서 지정한 콜백 함수를 사용하여 수신 알림 함수 포인터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2652">This service configures the receive notify function pointer with the callback function specified by the application.</span></span> <span data-ttu-id="112c2-2653">그러면 소켓에 하나 이상의 패킷이 수신될 때마다 이 콜백 함수가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2653">This callback function is then called whenever one or more packets are received on the socket.</span></span> <span data-ttu-id="112c2-2654">NX_NULL 포인터를 제공하면 알림 함수를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2654">If a NX_NULL pointer is supplied, the notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2655">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2655">Parameters</span></span>

- <span data-ttu-id="112c2-2656">**socket_ptr** TCP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2656">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="112c2-2657">**tcp_receive_notify** 소켓에 하나 이상의 패킷이 수신되면 호출되는 애플리케이션 콜백 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2657">**tcp_receive_notify** Application callback function pointer that is called when one or more packets are received on the socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2658">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2658">Return Values</span></span>

- <span data-ttu-id="112c2-2659">**NX_SUCCESS**(0x00) 소켓 수신 알림에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2659">**NX_SUCCESS** (0x00) Successful socket receive notify.</span></span>
- <span data-ttu-id="112c2-2660">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2660">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2661">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2661">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2662">**NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2662">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2663">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2663">Allowed From</span></span>

<span data-ttu-id="112c2-2664">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2664">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2665">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2665">Preemption Possible</span></span>

<span data-ttu-id="112c2-2666">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2666">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2667">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2667">Example</span></span>

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2668">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2668">See Also</span></span>

- <span data-ttu-id="112c2-2669">nx_tcp_enable, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2669">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2670">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2670">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="112c2-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="112c2-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="112c2-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="112c2-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="112c2-2674">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="112c2-2674">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="112c2-2675">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2675">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_send"></a><span data-ttu-id="112c2-2676">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2676">nx_tcp_socket_send</span></span>

<span data-ttu-id="112c2-2677">TCP 소켓을 통해 데이터를 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2677">Send data through a TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2678">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2678">Prototype</span></span>

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-2679">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2679">Description</span></span>

<span data-ttu-id="112c2-2680">이 서비스는 이전에 연결된 TCP 소켓을 통해 TCP 데이터를 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2680">This service sends TCP data through a previously connected TCP socket.</span></span> <span data-ttu-id="112c2-2681">마지막으로 보급된 수신기 창 크기가 이 요청 미만이면 지정된 대기 옵션에 따라 선택적으로 서비스가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2681">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait option specified.</span></span> <span data-ttu-id="112c2-2682">이 서비스는 MSS를 초과하는 패킷 데이터가 IP 계층으로 송신되지 않도록 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2682">This service guarantees that no packet data larger than MSS is sent to the IP layer.</span></span>

<span data-ttu-id="112c2-2683">오류가 반환되지 않는 경우 애플리케이션은 이 호출 후에 패킷을 해제하면 안 됩니다. 해제하면 네트워크 드라이버가 전송 후에도 패킷을 해제하려고 하므로 예측할 수 없는 결과가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2683">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will also try to release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2684">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2684">Parameters</span></span>

- <span data-ttu-id="112c2-2685">**socket_ptr** 이전에 연결된 TCP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2685">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="112c2-2686">**packet_ptr** TCP 데이터 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2686">**packet_ptr** TCP data packet pointer.</span></span>
- <span data-ttu-id="112c2-2687">**wait_option** 요청이 수신기 창 크기를 초과하는 경우 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2687">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span> <span data-ttu-id="112c2-2688">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2688">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-2689">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-2689">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-2690">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-2691">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-2691">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2692">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2692">Return Values</span></span>

- <span data-ttu-id="112c2-2693">**NX_SUCCESS**(0x00) 소켓 송신에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2693">**NX_SUCCESS** (0x00) Successful socket send.</span></span>
- <span data-ttu-id="112c2-2694">**NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2694">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="112c2-2695">**NX_NO_INTERFACE_ADDRESS**(0x50) 적절한 송신 인터페이스를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2695">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface found.</span></span>
- <span data-ttu-id="112c2-2696">**NX_NOT_CONNECTED**(0x38) 소켓이 더 이상 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2696">**NX_NOT_CONNECTED** (0x38) Socket is no longer connected.</span></span>
- <span data-ttu-id="112c2-2697">**NX_WINDOW_OVERFLOW**(0x39) 요청이 보급된 수신기 창 크기(바이트)를 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2697">**NX_WINDOW_OVERFLOW** (0x39) Request is greater than receiver’s advertised window size in bytes.</span></span>
- <span data-ttu-id="112c2-2698">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2698">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="112c2-2699">**NX_INVALID_PACKET**(0x12) 패킷이 할당되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2699">**NX_INVALID_PACKET** (0x12) Packet is not allocated.</span></span>
- <span data-ttu-id="112c2-2700">**NX_TX_QUEUE_DEPTH**(0x49) 최대 전송 큐 크기에 도달했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2700">**NX_TX_QUEUE_DEPTH** (0x49) Maximum transmit queue depth has been reached.</span></span>
- <span data-ttu-id="112c2-2701">**NX_OVERFLOW**(0x03) 패킷 뒤에 추가 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2701">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="112c2-2702">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2702">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2703">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2703">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2704">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2704">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="112c2-2705">**NX_UNDERFLOW**(0x02) 패킷 앞에 추가 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2705">**NX_UNDERFLOW** (0x02) Packet prepend pointer is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2706">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2706">Allowed From</span></span>

<span data-ttu-id="112c2-2707">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2707">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2708">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2708">Preemption Possible</span></span>

<span data-ttu-id="112c2-2709">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2709">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2710">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2710">Example</span></span>

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2711">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2711">See Also</span></span>

- <span data-ttu-id="112c2-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="112c2-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="112c2-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="112c2-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="112c2-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span></span>

### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="112c2-2721">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="112c2-2721">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="112c2-2722">TCP 소켓이 특정 상태가 될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2722">Wait for TCP socket to enter specific state</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2723">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2723">Prototype</span></span>

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="112c2-2724">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2724">Description</span></span>

<span data-ttu-id="112c2-2725">이 서비스는 소켓이 원하는 상태가 될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2725">This service waits for the socket to enter the desired state.</span></span> <span data-ttu-id="112c2-2726">소켓이 원하는 상태가 아닌 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2726">If the socket is not in the desired state, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2727">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2727">Parameters</span></span>

- <span data-ttu-id="112c2-2728">**socket_ptr** 이전에 연결된 TCP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2728">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="112c2-2729">**desired_state** 원하는 TCP 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2729">**desired_state** Desired TCP state.</span></span> <span data-ttu-id="112c2-2730">유효한 TCP 소켓 상태는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2730">Valid TCP socket states are defined as follows:</span></span>
- <span data-ttu-id="112c2-2731">NX_TCP_CLOSED(0x01)</span><span class="sxs-lookup"><span data-stu-id="112c2-2731">NX_TCP_CLOSED (0x01)</span></span>
- <span data-ttu-id="112c2-2732">NX_TCP_LISTEN_STATE(0x02)</span><span class="sxs-lookup"><span data-stu-id="112c2-2732">NX_TCP_LISTEN_STATE (0x02)</span></span>
- <span data-ttu-id="112c2-2733">NX_TCP_SYN_SENT(0x03)</span><span class="sxs-lookup"><span data-stu-id="112c2-2733">NX_TCP_SYN_SENT (0x03)</span></span>
- <span data-ttu-id="112c2-2734">NX_TCP_SYN_RECEIVED(0x04)</span><span class="sxs-lookup"><span data-stu-id="112c2-2734">NX_TCP_SYN_RECEIVED (0x04)</span></span>
- <span data-ttu-id="112c2-2735">NX_TCP_ESTABLISHED(0x05)</span><span class="sxs-lookup"><span data-stu-id="112c2-2735">NX_TCP_ESTABLISHED (0x05)</span></span>
- <span data-ttu-id="112c2-2736">NX_TCP_CLOSE_WAIT(0x06)</span><span class="sxs-lookup"><span data-stu-id="112c2-2736">NX_TCP_CLOSE_WAIT (0x06)</span></span>
- <span data-ttu-id="112c2-2737">NX_TCP_FIN_WAIT_1(0x07)</span><span class="sxs-lookup"><span data-stu-id="112c2-2737">NX_TCP_FIN_WAIT_1 (0x07)</span></span>
- <span data-ttu-id="112c2-2738">NX_TCP_FIN_WAIT_2(0x08)</span><span class="sxs-lookup"><span data-stu-id="112c2-2738">NX_TCP_FIN_WAIT_2 (0x08)</span></span>
- <span data-ttu-id="112c2-2739">NX_TCP_CLOSING(0x09)</span><span class="sxs-lookup"><span data-stu-id="112c2-2739">NX_TCP_CLOSING (0x09)</span></span>
- <span data-ttu-id="112c2-2740">NX_TCP_TIMED_WAIT(0x0A)</span><span class="sxs-lookup"><span data-stu-id="112c2-2740">NX_TCP_TIMED_WAIT (0x0A)</span></span>
- <span data-ttu-id="112c2-2741">NX_TCP_LAST_ACK(0x0B)</span><span class="sxs-lookup"><span data-stu-id="112c2-2741">NX_TCP_LAST_ACK (0x0B)</span></span>
- <span data-ttu-id="112c2-2742">**wait_option** 요청된 상태가 아닌 경우 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2742">**wait_option** Defines how the service behaves if the requested state is not present.</span></span> <span data-ttu-id="112c2-2743">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2743">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-2744">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-2744">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-2745">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-2746">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-2746">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2747">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2747">Return Values</span></span>
- <span data-ttu-id="112c2-2748">**NX_SUCCESS**(0x00) 상태 대기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2748">**NX_SUCCESS** (0x00) Successful state wait.</span></span>
- <span data-ttu-id="112c2-2749">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2749">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2750">**NX_NOT_SUCCESSFUL**(0x43) 지정된 대기 시간 내에 해당 상태가 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2750">**NX_NOT_SUCCESSFUL** (0x43) State not present within the specified wait time.</span></span>
- <span data-ttu-id="112c2-2751">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2751">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="112c2-2752">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2752">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2753">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2753">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="112c2-2754">**NX_OPTION_ERROR**(0x0A) 원하는 소켓 상태가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2754">**NX_OPTION_ERROR** (0x0A) The desired socket state is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2755">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2755">Allowed From</span></span>

<span data-ttu-id="112c2-2756">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2756">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2757">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2757">Preemption Possible</span></span>

<span data-ttu-id="112c2-2758">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2758">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2759">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2759">Example</span></span>

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2760">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2760">See Also</span></span>

- <span data-ttu-id="112c2-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="112c2-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="112c2-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="112c2-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="112c2-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="112c2-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="112c2-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="112c2-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="112c2-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="112c2-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span></span>

## <a name="nx_tcp_socket_timed_wait_callback"></a><span data-ttu-id="112c2-2770">nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="112c2-2770">nx_tcp_socket_timed_wait_callback</span></span>

<span data-ttu-id="112c2-2771">시간이 지정된 대기 상태 콜백을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2771">Install callback for timed wait state</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2772">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2772">Prototype</span></span>

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="112c2-2773">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2773">Description</span></span>

<span data-ttu-id="112c2-2774">이 서비스는 TCP 소켓이 시간이 지정된 대기 상태인 경우 호출되는 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2774">This service registers a callback function which is invoked when the TCP socket is in timed wait state.</span></span> <span data-ttu-id="112c2-2775">이 서비스를 사용하려면 옵션 ***NX_ENABLE_EXTENDED_NOTIFY*** 가 정의된 NetX 라이브러리가 빌드되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2775">To use this service, the NetX library must be built with the option ***NX_ENABLE_EXTENDED_NOTIFY*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2776">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2776">Parameters</span></span>

- <span data-ttu-id="112c2-2777">**socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2777">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="112c2-2778">**tcp_timed_wait_callback** 시간이 지정된 대기 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2778">**tcp_timed_wait_callback** The timed wait callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2779">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2779">Return Values</span></span>

- <span data-ttu-id="112c2-2780">**NX_SUCCESS**(0x00) 콜백 함수 소켓을 성공적으로 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2780">**NX_SUCCESS** (0x00) Successfully registers the callback function socket</span></span>
- <span data-ttu-id="112c2-2781">**NX_NOT_SUPPORTED**(0x4B) 확장 알림 기능을 사용하도록 설정하지 않은 상태로 NetX 라이브러리가 빌드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2781">**NX_NOT_SUPPORTED** (0x4B) NetX library is built without the extended notify feature enabled.</span></span>
- <span data-ttu-id="112c2-2782">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2782">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2783">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2784">**NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2784">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2785">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2785">Allowed From</span></span>

<span data-ttu-id="112c2-2786">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2786">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2787">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2787">Preemption Possible</span></span>

<span data-ttu-id="112c2-2788">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2788">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2789">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2789">Example</span></span>

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="112c2-2790">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2790">See Also</span></span>

- <span data-ttu-id="112c2-2791">nx_tcp_enable, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2791">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2792">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2792">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="112c2-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="112c2-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="112c2-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="112c2-2796">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="112c2-2796">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="112c2-2797">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2797">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="112c2-2798">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="112c2-2798">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="112c2-2799">소켓의 전송 매개 변수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2799">Configure socket's transmit parameters</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2800">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2800">Prototype</span></span>

```C
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```

### <a name="description"></a><span data-ttu-id="112c2-2801">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2801">Description</span></span>

<span data-ttu-id="112c2-2802">이 서비스는 지정된 TCP 소켓의 다양한 전송 매개 변수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2802">This service configures various transmit parameters of the specified TCP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2803">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2803">Parameters</span></span>

- <span data-ttu-id="112c2-2804">**socket_ptr** TCP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2804">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="112c2-2805">**max_queue_depth** 전송을 위해 큐에 대기될 수 있는 최대 패킷 수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2805">**max_queue_depth** Maximum number of packets allowed to be queued for transmission.</span></span>
- <span data-ttu-id="112c2-2806">**timeout** 패킷을 다시 송신하기 전에 ACK를 기다리는 ThreadX 타이머 틱 수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2806">**timeout** Number of ThreadX timer ticks an ACK is waited for before the packet is sent again.</span></span>
- <span data-ttu-id="112c2-2807">**max_retries** 허용되는 최대 재시도 수입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2807">**max_retries** Maximum number of retries allowed.</span></span>
- <span data-ttu-id="112c2-2808">**timeout_shift** 각 후속 재시도에 대한 시간 제한을 변경하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2808">**timeout_shift** Value to shift the timeout for each subsequent retry.</span></span> <span data-ttu-id="112c2-2809">값이 0이면 이어지는 재시도 간 시간 제한이 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2809">A value of 0, results in the same timeout between successive retries.</span></span> <span data-ttu-id="112c2-2810">값이 1이면 재시도 간 시간 제한이 두 배가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2810">A value of 1, doubles the timeout between retries.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2811">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2811">Return Values</span></span>
- <span data-ttu-id="112c2-2812">**NX_SUCCESS**(0x00) 전송 소켓 구성에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2812">**NX_SUCCESS** (0x00) Successful transmit socket configure.</span></span>
- <span data-ttu-id="112c2-2813">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2813">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-2814">**NX_OPTION_ERROR**(0x0a) 잘못된 큐 깊이 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2814">**NX_OPTION_ERROR** (0x0a) Invalid queue depth option.</span></span>
- <span data-ttu-id="112c2-2815">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2815">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2816">**NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2816">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2817">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2817">Allowed From</span></span>

<span data-ttu-id="112c2-2818">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2818">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2819">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2819">Preemption Possible</span></span>

<span data-ttu-id="112c2-2820">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2820">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2821">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2821">Example</span></span>

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2822">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2822">See Also</span></span>

- <span data-ttu-id="112c2-2823">nx_tcp_enable, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2823">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2824">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2824">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="112c2-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="112c2-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="112c2-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="112c2-2828">nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="112c2-2828">nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="112c2-2829">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2829">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_window_update_notify_set"></a><span data-ttu-id="112c2-2830">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2830">nx_tcp_socket_window_update_notify_set</span></span>

<span data-ttu-id="112c2-2831">애플리케이션에 창 크기 업데이트에 대해 알립니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2831">Notify application of window size updates</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2832">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2832">Prototype</span></span>

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="112c2-2833">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2833">Description</span></span>

<span data-ttu-id="112c2-2834">이 서비스는 소켓 창 업데이트 콜백 루틴을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2834">This service installs a socket window update callback routine.</span></span> <span data-ttu-id="112c2-2835">지정된 소켓이 원격 호스트 창 크기 증가를 나타내는 패킷을 수신할 때마다 자동으로 이 루틴이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2835">This routine is called automatically whenever the specified socket receives a packet indicating an increase in the window size of the remote host.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2836">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2836">Parameters</span></span>

- <span data-ttu-id="112c2-2837">**socket_ptr** 이전에 만든 TCP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2837">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="112c2-2838">**tcp_window_update_notify** 창 크기가 변경되면 호출되는 콜백 루틴입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2838">**tcp_window_update_notify** Callback routine to be called when the window size changes.</span></span> <span data-ttu-id="112c2-2839">값이 NULL이면 창 변경 업데이트를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2839">A value of NULL disables the window change update.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2840">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2840">Return Values</span></span>
- <span data-ttu-id="112c2-2841">**NX_SUCCESS**(0x00) 콜백 루틴이 소켓에 설치되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2841">**NX_SUCCESS** (0x00) Callback routine is installed on the socket.</span></span>
- <span data-ttu-id="112c2-2842">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2842">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2843">**NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2843">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="112c2-2844">**NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2844">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="112c2-2845">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2845">Allowed From</span></span>

<span data-ttu-id="112c2-2846">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2846">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2847">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2847">Preemption Possible</span></span>

<span data-ttu-id="112c2-2848">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2848">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2849">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2849">Example</span></span>

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a><span data-ttu-id="112c2-2850">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2850">See Also</span></span>

- <span data-ttu-id="112c2-2851">nx_tcp_enable, nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-2851">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="112c2-2852">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2852">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="112c2-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="112c2-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="112c2-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="112c2-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="112c2-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="112c2-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span></span>

## <a name="nx_udp_enable"></a><span data-ttu-id="112c2-2857">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-2857">nx_udp_enable</span></span>

<span data-ttu-id="112c2-2858">NetX의 UDP 구성 요소를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2858">Enable UDP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2859">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2859">Prototype</span></span>

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-2860">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2860">Description</span></span>

<span data-ttu-id="112c2-2861">이 서비스는 NetX의 UDP(User Datagram Protocol) 구성 요소를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2861">This service enables the User Datagram Protocol (UDP) component of NetX.</span></span> <span data-ttu-id="112c2-2862">사용하도록 설정하면 애플리케이션에서 UDP 데이터그램을 송신하고 수신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2862">After enabled, UDP datagrams may be sent and received by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2863">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2863">Parameters</span></span>

- <span data-ttu-id="112c2-2864">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2864">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2865">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2865">Return Values</span></span>

- <span data-ttu-id="112c2-2866">**NX_SUCCESS**(0x00) UDP를 사용하도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2866">**NX_SUCCESS** (0x00) Successful UDP enable.</span></span>
- <span data-ttu-id="112c2-2867">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2867">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-2868">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2868">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2869">**NX_ALREADY_ENABLED**(0x15) 이 구성 요소는 이미 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2869">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2870">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2870">Allowed From</span></span>

<span data-ttu-id="112c2-2871">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="112c2-2871">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2872">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2872">Preemption Possible</span></span>

<span data-ttu-id="112c2-2873">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2873">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2874">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2874">Example</span></span>

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2875">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2875">See Also</span></span>

- <span data-ttu-id="112c2-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="112c2-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="112c2-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-2880">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2880">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2881">nx_udp_socket_receive_notify, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2881">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2883">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-2883">nx_udp_source_extract</span></span>

## <a name="nx_udp_free_port_find"></a><span data-ttu-id="112c2-2884">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="112c2-2884">nx_udp_free_port_find</span></span>

<span data-ttu-id="112c2-2885">사용할 수 있는 다음 UDP 포트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2885">Find next available UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2886">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2886">Prototype</span></span>

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-2887">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2887">Description</span></span>

<span data-ttu-id="112c2-2888">이 서비스는 애플리케이션 제공 포트 번호에서 시작하여 사용 가능한 UDP 포트(바인딩되지 않은 포트)를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2888">This service looks for a free UDP port (unbound) starting from the application supplied port number.</span></span> <span data-ttu-id="112c2-2889">검색에서 최대 포트 값인 0xFFFF에 도달하면 검색 논리가 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2889">The search logic will wrap around if the search reaches the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="112c2-2890">검색에 성공하면 *free_port_ptr* 이 가리키는 변수에 사용 가능한 포트가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2890">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="112c2-2891">이 서비스는 다른 스레드에서 호출될 수 있으며 동일한 포트를 반환할 수 있습니다. 이러한 경합 상태를 방지하기 위해 애플리케이션은 이 서비스 및 실제 소켓 바인딩에 뮤텍스 보호가 적용되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2891">*This service can be called from another thread and can have the same port returned. To prevent this race condition, the application may wish to place this service and the actual socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2892">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2892">Parameters</span></span>

- <span data-ttu-id="112c2-2893">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2893">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-2894">**port** 검색을 시작할 포트 번호(1-0xFFFF)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2894">**port** Port number to start search (1 through 0xFFFF).</span></span>
- <span data-ttu-id="112c2-2895">**free_port_ptr** 사용 가능한 포트 반환 변수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2895">**free_port_ptr** Pointer to the destination free port return variable.</span></span>


### <a name="return-values"></a><span data-ttu-id="112c2-2896">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2896">Return Values</span></span>

- <span data-ttu-id="112c2-2897">**NX_SUCCESS**(0x00) 사용 가능한 포트를 찾는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2897">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="112c2-2898">**NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2898">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="112c2-2899">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2899">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-2900">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2900">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2901">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2901">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="112c2-2902">**NX_INVALID_PORT**(0x46) 지정된 포트 번호가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2902">**NX_INVALID_PORT** (0x46) Specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2903">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2903">Allowed From</span></span>

<span data-ttu-id="112c2-2904">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2904">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2905">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2905">Preemption Possible</span></span>

<span data-ttu-id="112c2-2906">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2906">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2907">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2907">Example</span></span>

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2908">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2908">See Also</span></span>

- <span data-ttu-id="112c2-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="112c2-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="112c2-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-2913">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2913">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2914">nx_udp_socket_receive_notify, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2914">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2916">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-2916">nx_udp_source_extract</span></span>

## <a name="nx_udp_info_get"></a><span data-ttu-id="112c2-2917">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2917">nx_udp_info_get</span></span>

<span data-ttu-id="112c2-2918">UDP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2918">Retrieve information about UDP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2919">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2919">Prototype</span></span>

```C
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="112c2-2920">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2920">Description</span></span>

<span data-ttu-id="112c2-2921">이 서비스는 지정된 IP 인스턴스의 UDP 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2921">This service retrieves information about UDP activities for the specified IP instance.</span></span>

<span data-ttu-id="112c2-2922">대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2922">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2923">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2923">Parameters</span></span>

- <span data-ttu-id="112c2-2924">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2924">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-2925">**udp_packets_sent** 송신된 총 UDP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2925">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent.</span></span>
- <span data-ttu-id="112c2-2926">**udp_bytes_sent** 송신된 총 UDP 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2926">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent.</span></span>
- <span data-ttu-id="112c2-2927">**udp_packets_received** 수신된 총 UDP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2927">**udp_packets_received** Pointer to destination of the total number of UDP packets received.</span></span>
- <span data-ttu-id="112c2-2928">**udp_bytes_received** 수신된 총 UDP 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2928">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received.</span></span>
- <span data-ttu-id="112c2-2929">**udp_invalid_packets** 잘못된 총 UDP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2929">**udp_invalid_packets** Pointer to destination of the total number of invalid UDP packets.</span></span>
- <span data-ttu-id="112c2-2930">**udp_receive_packets_dropped** 삭제된 총 UDP 수신 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2930">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped.</span></span>
- <span data-ttu-id="112c2-2931">**udp_checksum_errors** 체크섬 오류가 있는 총 UDP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2931">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2932">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2932">Return Values</span></span>

- <span data-ttu-id="112c2-2933">**NX_SUCCESS**(0x00) UDP 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2933">**NX_SUCCESS** (0x00) Successful UDP information retrieval.</span></span>
- <span data-ttu-id="112c2-2934">**NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2934">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="112c2-2935">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2935">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-2936">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2936">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="112c2-2937">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2937">Allowed From</span></span>

<span data-ttu-id="112c2-2938">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="112c2-2938">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2939">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2939">Preemption Possible</span></span>

<span data-ttu-id="112c2-2940">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2940">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2941">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2941">Example</span></span>

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_invalid_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2942">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2942">See Also</span></span>

- <span data-ttu-id="112c2-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="112c2-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="112c2-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-2947">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2947">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2948">nx_udp_socket_receive_notify, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2948">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2950">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-2950">nx_udp_source_extract</span></span>

## <a name="nx_udp_packet_info_extract"></a><span data-ttu-id="112c2-2951">nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-2951">nx_udp_packet_info_extract</span></span>

<span data-ttu-id="112c2-2952">UDP 패킷에서 네트워크 매개 변수를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2952">Extract network parameters from UDP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2953">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2953">Prototype</span></span>

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="112c2-2954">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2954">Description</span></span>

<span data-ttu-id="112c2-2955">이 서비스는 수신 인터페이스의 수신된 패킷에서 IP 주소, 피어 포트 번호, 프로토콜 유형(이 서비스는 항상 UDP 유형을 반환함) 같은 네트워크 매개 변수를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2955">This service extracts network parameters, such as IP address, peer port number, protocol type (this service always returns UDP type) from a packet received on an incoming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2956">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2956">Parameters</span></span>

- <span data-ttu-id="112c2-2957">**packet_ptr** 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2957">**packet_ptr** Pointer to packet.</span></span>
- <span data-ttu-id="112c2-2958">**ip_address** 송신기 IP 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2958">**ip_address** Pointer to sender IP address.</span></span>
- <span data-ttu-id="112c2-2959">**protocol** 프로토콜(UDP)에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2959">**protocol** Pointer to protocol (UDP).</span></span>
- <span data-ttu-id="112c2-2960">**port** 송신기 포트 번호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2960">**port** Pointer to sender’s port number.</span></span>
- <span data-ttu-id="112c2-2961">**interface_index** 수신 인터페이스 인덱스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2961">**interface_index** Pointer to receiving interface index.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2962">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2962">Return Values</span></span>

- <span data-ttu-id="112c2-2963">**NX_SUCCESS**(0x00) 패킷 인터페이스 데이터를 성공적으로 추출했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2963">**NX_SUCCESS** (0x00) Packet interface data successfully extracted.</span></span>
- <span data-ttu-id="112c2-2964">**NX_INVALID_PACKET**(0x12) 패킷에 IP 프레임이 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2964">**NX_INVALID_PACKET** (0x12) Packet does not contain IP frame.</span></span>
- <span data-ttu-id="112c2-2965">**NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2965">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="112c2-2966">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2966">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-2967">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-2967">Allowed From</span></span>

<span data-ttu-id="112c2-2968">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-2968">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-2969">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-2969">Preemption Possible</span></span>

<span data-ttu-id="112c2-2970">예</span><span class="sxs-lookup"><span data-stu-id="112c2-2970">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-2971">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-2971">Example</span></span>

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-2972">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-2972">See Also</span></span>

- <span data-ttu-id="112c2-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="112c2-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-2977">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-2977">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-2978">nx_udp_socket_receive_notify, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-2978">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="112c2-2980">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-2980">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bind"></a><span data-ttu-id="112c2-2981">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-2981">nx_udp_socket_bind</span></span>

<span data-ttu-id="112c2-2982">UDP 소켓을 UDP 포트에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2982">Bind UDP socket to UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-2983">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-2983">Prototype</span></span>

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-2984">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-2984">Description</span></span>

<span data-ttu-id="112c2-2985">이 서비스는 이전에 만든 UDP 소켓을 지정된 UDP 포트에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2985">This service binds the previously created UDP socket to the specified UDP port.</span></span> <span data-ttu-id="112c2-2986">유효한 UDP 소켓 범위는 0에서 0xFFFF까지입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2986">Valid UDP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="112c2-2987">요청된 포트 번호가 다른 소켓에 바인딩되어 있으면 이 서비스는 지정된 시간 동안 해당 소켓이 해당 포트 번호에서 바인딩을 해제할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2987">If the requested port number is bound to another socket, this service waits for specified period of time for the socket to unbind from the port number.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-2988">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-2988">Parameters</span></span>

- <span data-ttu-id="112c2-2989">**socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2989">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="112c2-2990">**port** 바인딩할 포트 번호(1-0xFFFF)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2990">**port** Port number to bind to (1 through 0xFFFF).</span></span> <span data-ttu-id="112c2-2991">포트 번호가 NX_ANY_PORT(0x0000)인 경우 IP 인스턴스는 가능한 다음 포트를 검색하여 바인딩에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2991">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="112c2-2992">**wait_option** 포트가 이미 다른 소켓에 바인딩되어 있는 경우 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2992">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="112c2-2993">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2993">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-2994">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-2994">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-2995">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-2996">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-2996">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-2997">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-2997">Return Values</span></span>

- <span data-ttu-id="112c2-2998">**NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2998">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="112c2-2999">**NX_ALREADY_BOUND**(0x22) 이 소켓은 다른 포트에 이미 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-2999">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another port.</span></span>
- <span data-ttu-id="112c2-3000">**NX_PORT_UNAVAILABLE**(0x23) 포트가 이미 다른 소켓에 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3000">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="112c2-3001">**NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3001">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="112c2-3002">**NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3002">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="112c2-3003">**NX_INVALID_PORT**(0x46) 잘못된 포트가 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3003">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="112c2-3004">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3004">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-3005">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-3006">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3007">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3007">Allowed From</span></span>

<span data-ttu-id="112c2-3008">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-3008">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3009">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3009">Preemption Possible</span></span>

<span data-ttu-id="112c2-3010">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3010">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3011">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3011">Example</span></span>

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a><span data-ttu-id="112c2-3012">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3012">See Also</span></span>

- <span data-ttu-id="112c2-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="112c2-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="112c2-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-3017">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-3017">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-3018">nx_udp_socket_receive_notify, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3018">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="112c2-3020">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3020">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="112c2-3021">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="112c2-3021">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="112c2-3022">검색에 사용할 수 있는 바이트 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3022">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3023">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3023">Prototype</span></span>

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="112c2-3024">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3024">Description</span></span>

<span data-ttu-id="112c2-3025">이 서비스는 지정된 UDP 소켓에서 수신용으로 사용할 수 있는 바이트 수를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3025">This service retrieves number of bytes available for reception in the specified UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3026">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3026">Parameters</span></span>

- <span data-ttu-id="112c2-3027">**socket_ptr** 이전에 만든 UDP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3027">**socket_ptr** Pointer to previously created UDP socket.</span></span>
- <span data-ttu-id="112c2-3028">**bytes_available** 사용할 수 있는 바이트 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3028">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-3029">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-3029">Return Values</span></span>

- <span data-ttu-id="112c2-3030">**NX_SUCCESS**(0x00) 사용할 수 있는 바이트 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3030">**NX_SUCCESS** (0x00) Successful bytes available retrieval.</span></span>
- <span data-ttu-id="112c2-3031">**NX_NOT_SUCCESSFUL**(0x43) 소켓이 포트에 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3031">**NX_NOT_SUCCESSFUL** (0x43) Socket not bound to a port.</span></span>
- <span data-ttu-id="112c2-3032">**NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3032">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="112c2-3033">**NX_NOT_ENABLED**(0x14) UDP 기능이 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3033">**NX_NOT_ENABLED** (0x14) UDP feature is not enabled.</span></span>
- <span data-ttu-id="112c2-3034">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3034">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3035">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3035">Allowed From</span></span>

<span data-ttu-id="112c2-3036">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-3036">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3037">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3037">Preemption Possible</span></span>

<span data-ttu-id="112c2-3038">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3038">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3039">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3039">Example</span></span>

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="112c2-3040">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3040">See Also</span></span>

- <span data-ttu-id="112c2-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3042">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3042">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="112c2-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-3045">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-3045">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-3046">nx_udp_socket_receive_notify, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3046">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="112c2-3048">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3048">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="112c2-3049">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3049">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="112c2-3050">UDP 소켓 체크섬을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3050">Disable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3051">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3051">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-3052">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3052">Description</span></span>

<span data-ttu-id="112c2-3053">이 서비스는 지정된 UDP 소켓에서 패킷을 송신하고 수신하는 데 체크섬 논리를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3053">This service disables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="112c2-3054">체크섬 논리를 사용하지 않도록 설정하면 이 소켓을 통해 송신되는 모든 패킷의 UDP 헤더 체크섬 필드에 0값이 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3054">When the checksum logic is disabled, a value of zero is loaded into the UDP header's checksum field for all packets sent through this socket.</span></span> <span data-ttu-id="112c2-3055">UDP 헤더의 체크섬 값이 0이면 해당 패킷에 대해 체크섬이 계산되지 않음을 수신기에서 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3055">A zero-value checksum value in the UDP header signals the receiver that checksum is not computed for this packet.</span></span>

<span data-ttu-id="112c2-3056">또한, \***NX_DISABLE_UDP_RX_CHECKSUM** _ 및 _ \*_NX_DISABLE_UDP_TX_CHECKSUM_\*\*이 각각 정의된 경우에도 UDP 패킷을 수신하고 송신할 때 아무런 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3056">Also note that this has no effect if ***NX_DISABLE_UDP_RX_CHECKSUM** _ and _ *_NX_DISABLE_UDP_TX_CHECKSUM_** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3057">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3057">Parameters</span></span>

- <span data-ttu-id="112c2-3058">**socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3058">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-3059">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-3059">Return Values</span></span>

- <span data-ttu-id="112c2-3060">**NX_SUCCESS**(0x00) 소켓 체크섬을 사용하지 않도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3060">**NX_SUCCESS** (0x00) Successful socket checksum disable.</span></span>
- <span data-ttu-id="112c2-3061">**NX_NOT_BOUND**(0x24) 소켓이 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3061">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="112c2-3062">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3062">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-3063">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3063">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-3064">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3064">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3065">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3065">Allowed From</span></span>

<span data-ttu-id="112c2-3066">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="112c2-3066">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3067">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3067">Preemption Possible</span></span>

<span data-ttu-id="112c2-3068">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3068">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3069">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3069">Example</span></span>

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-3070">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3070">See Also</span></span>

- <span data-ttu-id="112c2-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3072">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3072">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-3075">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-3075">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-3076">nx_udp_socket_receive_notify, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3076">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="112c2-3078">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3078">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="112c2-3079">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="112c2-3079">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="112c2-3080">UDP 소켓 체크섬을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3080">Enable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3081">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3081">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-3082">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3082">Description</span></span>

<span data-ttu-id="112c2-3083">이 서비스는 지정된 UDP 소켓에서 패킷을 송신하고 수신하는 데 체크섬 논리를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3083">This service enables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="112c2-3084">체크섬은 전체 UDP 데이터 영역 및 의사 IP 헤더에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3084">The checksum covers the entire UDP data area as well as a pseudo IP header.</span></span>

<span data-ttu-id="112c2-3085">또한, **NX_DISABLE_UDP_RX_CHECKSUM** 및 **NX_DISABLE_UDP_TX_CHECKSUM** 이 각각 정의된 경우에도 UDP 패킷을 수신하고 송신할 때 아무런 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3085">Also note that this has no effect if **NX_DISABLE_UDP_RX_CHECKSUM** and **NX_DISABLE_UDP_TX_CHECKSUM** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3086">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3086">Parameters</span></span>

- <span data-ttu-id="112c2-3087">**socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3087">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-3088">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-3088">Return Values</span></span>

- <span data-ttu-id="112c2-3089">**NX_SUCCESS**(0x00) 소켓 체크섬을 사용하도록 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3089">**NX_SUCCESS** (0x00) Successful socket checksum enable.</span></span>
- <span data-ttu-id="112c2-3090">**NX_NOT_BOUND**(0x24) 소켓이 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3090">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="112c2-3091">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3091">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-3092">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3092">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-3093">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3093">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3094">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3094">Allowed From</span></span>

<span data-ttu-id="112c2-3095">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="112c2-3095">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3096">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3096">Preemption Possible</span></span>

<span data-ttu-id="112c2-3097">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3097">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3098">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3098">Example</span></span>

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-3099">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3099">See Also</span></span>

- <span data-ttu-id="112c2-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3101">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3101">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-3104">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-3104">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-3105">nx_udp_socket_receive_notify, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3105">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="112c2-3107">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3107">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_create"></a><span data-ttu-id="112c2-3108">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-3108">nx_udp_socket_create</span></span>

<span data-ttu-id="112c2-3109">UDP 소켓을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3109">Create UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3110">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3110">Prototype</span></span>

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a><span data-ttu-id="112c2-3111">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3111">Description</span></span>

<span data-ttu-id="112c2-3112">이 서비스는 지정된 IP 인스턴스의 UDP 소켓을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3112">This service creates a UDP socket for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3113">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3113">Parameters</span></span>

- <span data-ttu-id="112c2-3114">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3114">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="112c2-3115">**socket_ptr** 새 UDP 소켓 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3115">**socket_ptr** Pointer to new UDP socket control bloc.</span></span>
- <span data-ttu-id="112c2-3116">**name** 이 UDP 소켓의 애플리케이션 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3116">**name** Application name for this UDP socket.</span></span>
- <span data-ttu-id="112c2-3117">**type_of_service** 전송할 서비스 유형을 정의합니다. 올바른 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3117">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
    - <span data-ttu-id="112c2-3118">NX_IP_NORMAL(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-3118">NX_IP_NORMAL (0x00000000)</span></span>
    - <span data-ttu-id="112c2-3119">NX_IP_MIN_DELAY(0x00100000)</span><span class="sxs-lookup"><span data-stu-id="112c2-3119">NX_IP_MIN_DELAY (0x00100000)</span></span>
    - <span data-ttu-id="112c2-3120">NX_IP_MAX_DATA(0x00080000)</span><span class="sxs-lookup"><span data-stu-id="112c2-3120">NX_IP_MAX_DATA (0x00080000)</span></span>
    - <span data-ttu-id="112c2-3121">NX_IP_MAX_RELIABLE(0x00040000)</span><span class="sxs-lookup"><span data-stu-id="112c2-3121">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
    - <span data-ttu-id="112c2-3122">NX_IP_MIN_COST(0x00020000)</span><span class="sxs-lookup"><span data-stu-id="112c2-3122">NX_IP_MIN_COST (0x00020000)</span></span>
- <span data-ttu-id="112c2-3123">**fragment** IP 조각화 허용 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3123">**fragment** Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="112c2-3124">NX_FRAGMENT_OKAY(0x0)가 지정되면 IP 조각화가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3124">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="112c2-3125">NX_DONT_FRAGMENT(0x4000)가 지정되면 IP 조각화가 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3125">If NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="112c2-3126">**time_to_live** 이 패킷이 제거되기 전까지 통과할 수 있는 라우터 수를 정의하는 8비트 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3126">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="112c2-3127">기본값은 NX_IP_TIME_TO_LIVE로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3127">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="112c2-3128">**queue_maximum** 이 소켓에 대해 큐에 대기될 수 있는 최대 UDP 데이터그램 수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3128">**queue_maximum** Defines the maximum number of UDP datagrams that can be queued for this socket.</span></span> <span data-ttu-id="112c2-3129">큐 제한에 도달하면 수신된 모든 새 패킷의 가장 오래된 UDP 패킷이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3129">After the queue limit is reached, for every new packet received the oldest UDP packet is released.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-3130">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-3130">Return Values</span></span>

- <span data-ttu-id="112c2-3131">**NX_SUCCESS**(0x00) UDP 소켓 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3131">**NX_SUCCESS** (0x00) Successful UDP socket create.</span></span>
- <span data-ttu-id="112c2-3132">**NX_OPTION_ERROR**(0x0A) type-of-service, fragment 또는 time-to-live 옵션이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3132">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, or time-to-live option.</span></span>
- <span data-ttu-id="112c2-3133">**NX_PTR_ERROR**(0x07) 잘못된 IP 또는 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="112c2-3134">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-3135">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3136">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3136">Allowed From</span></span>

<span data-ttu-id="112c2-3137">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-3137">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3138">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3138">Preemption Possible</span></span>

<span data-ttu-id="112c2-3139">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3139">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3140">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3140">Example</span></span>

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-3141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3141">See Also</span></span>

- <span data-ttu-id="112c2-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3143">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3143">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete,</span></span>
- <span data-ttu-id="112c2-3146">nx_udp_socket_info_get, nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3146">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="112c2-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="112c2-3148">nx_udp_socket_send, nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3148">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="112c2-3149">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3149">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_delete"></a><span data-ttu-id="112c2-3150">nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="112c2-3150">nx_udp_socket_delete</span></span>

<span data-ttu-id="112c2-3151">UDP 소켓을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3151">Delete UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3152">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3152">Prototype</span></span>

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-3153">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3153">Description</span></span>

<span data-ttu-id="112c2-3154">이 서비스는 이전에 만든 UDP 소켓을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3154">This service deletes a previously created UDP socket.</span></span> <span data-ttu-id="112c2-3155">소켓이 포트에 바인딩된 경우 먼저 소켓 바인딩을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3155">If the socket was bound to a port, the socket must be unbound first.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3156">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3156">Parameters</span></span>

- <span data-ttu-id="112c2-3157">**socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3157">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-3158">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-3158">Return Values</span></span>

- <span data-ttu-id="112c2-3159">**NX_SUCCESS**(0x00) 소켓을 삭제하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3159">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="112c2-3160">**NX_STILL_BOUND**(0x42) 소켓이 여전히 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3160">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="112c2-3161">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3161">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-3162">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3162">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-3163">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3163">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3164">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3164">Allowed From</span></span>

<span data-ttu-id="112c2-3165">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-3165">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3166">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3166">Preemption Possible</span></span>

<span data-ttu-id="112c2-3167">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3167">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3168">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3168">Example</span></span>

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-3169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3169">See Also</span></span>

- <span data-ttu-id="112c2-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3171">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3171">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="112c2-3174">nx_udp_socket_info_get, nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3174">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="112c2-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="112c2-3176">nx_udp_socket_send, nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3176">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="112c2-3177">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3177">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_info_get"></a><span data-ttu-id="112c2-3178">nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3178">nx_udp_socket_info_get</span></span>

<span data-ttu-id="112c2-3179">UDP 소켓 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3179">Retrieve information about UDP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3180">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3180">Prototype</span></span>

```C
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="112c2-3181">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3181">Description</span></span>

<span data-ttu-id="112c2-3182">이 서비스는 지정된 UDP 소켓 인스턴스의 UDP 소켓 활동에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3182">This service retrieves information about UDP socket activities for the specified UDP socket instance.</span></span>

<span data-ttu-id="112c2-3183">대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3183">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3184">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3184">Parameters</span></span>

- <span data-ttu-id="112c2-3185">**socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3185">**socket_ptr** Pointer to previously-created UDP socket instance.</span></span>
- <span data-ttu-id="112c2-3186">**udp_packets_sent** 소켓의 송신된 총 UDP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3186">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent on socket.</span></span>
- <span data-ttu-id="112c2-3187">**udp_bytes_sent** 소켓의 송신된 총 UDP 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3187">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent on socket.</span></span>
- <span data-ttu-id="112c2-3188">**udp_packets_received** 소켓의 수신된 총 UDP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3188">**udp_packets_received** Pointer to destination of the total number of UDP packets received on socket.</span></span>
- <span data-ttu-id="112c2-3189">**udp_bytes_received** 소켓의 수신된 총 UDP 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3189">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received on socket.</span></span>
- <span data-ttu-id="112c2-3190">**udp_packets_queued** 소켓의 큐에 대기된 총 UDP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3190">**udp_packets_queued** Pointer to destination of the total number of queued UDP packets on socket.</span></span>
- <span data-ttu-id="112c2-3191">**udp_receive_packets_dropped** 큐 크기 초과로 인해 삭제된, 소켓의 총 UDP 수신 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3191">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped for socket due to queue size being exceeded.</span></span>
- <span data-ttu-id="112c2-3192">**udp_checksum_errors** 소켓의 체크섬 오류가 있는 총 UDP 패킷 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3192">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors on socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-3193">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-3193">Return Values</span></span>

- <span data-ttu-id="112c2-3194">**NX_SUCCESS**(0x00) UDP 소켓 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3194">**NX_SUCCESS** (0x00) Successful UDP socket information retrieval.</span></span>
- <span data-ttu-id="112c2-3195">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3195">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-3196">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3196">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-3197">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3197">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3198">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3198">Allowed From</span></span>

<span data-ttu-id="112c2-3199">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="112c2-3199">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3200">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3200">Preemption Possible</span></span>

<span data-ttu-id="112c2-3201">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3201">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3202">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3202">Example</span></span>

```C
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
    &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_queued_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="112c2-3203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3203">See Also</span></span>

- <span data-ttu-id="112c2-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3205">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3205">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="112c2-3208">nx_udp_socket_delete, nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3208">nx_udp_socket_delete, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="112c2-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="112c2-3210">nx_udp_socket_send, nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3210">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="112c2-3211">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3211">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_port_get"></a><span data-ttu-id="112c2-3212">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3212">nx_udp_socket_port_get</span></span>

<span data-ttu-id="112c2-3213">UDP 소켓에 바인딩된 포트 번호를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3213">Pick up port number bound to UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3214">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3214">Prototype</span></span>

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-3215">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3215">Description</span></span>

<span data-ttu-id="112c2-3216">이 서비스는 소켓에 연결된 포트 번호를 검색합니다. 소켓이 바인딩될 때 NX_ANY_PORT가 지정된 경우 NetX에서 할당한 포트를 찾는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3216">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3217">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3217">Parameters</span></span>

- <span data-ttu-id="112c2-3218">**socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3218">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="112c2-3219">**port_ptr** 반환 포트 번호 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3219">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="112c2-3220">유효한 포트 번호는 (1-0xFFFF)입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3220">Valid port numbers are (1- 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-3221">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-3221">Return Values</span></span>

- <span data-ttu-id="112c2-3222">**NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3222">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="112c2-3223">**NX_NOT_BOUND**(0x24) 이 소켓은 포트에 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3223">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="112c2-3224">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터 또는 포트 반환 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3224">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="112c2-3225">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3225">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-3226">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3226">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3227">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3227">Allowed From</span></span>

<span data-ttu-id="112c2-3228">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-3228">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3229">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3229">Preemption Possible</span></span>

<span data-ttu-id="112c2-3230">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3230">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3231">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3231">Example</span></span>

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-3232">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3232">See Also</span></span>

- <span data-ttu-id="112c2-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3234">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3234">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="112c2-3237">nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3237">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="112c2-3239">nx_udp_socket_send, nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3239">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="112c2-3240">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3240">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive"></a><span data-ttu-id="112c2-3241">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-3241">nx_udp_socket_receive</span></span>

<span data-ttu-id="112c2-3242">UDP 소켓에서 데이터그램을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3242">Receive datagram from UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3243">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3243">Prototype</span></span>

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="112c2-3244">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3244">Description</span></span>

<span data-ttu-id="112c2-3245">이 서비스는 지정된 소켓에서 UDP 데이터그램을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3245">This service receives an UDP datagram from the specified socket.</span></span> <span data-ttu-id="112c2-3246">지정된 소켓에 큐에 대기된 데이터그램이 없는 경우 제공된 대기 옵션에 따라 호출자가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3246">If no datagram is queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="112c2-3247">*NX_SUCCESS* 가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 해당 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3247">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3248">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3248">Parameters</span></span>

- <span data-ttu-id="112c2-3249">**socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3249">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="112c2-3250">**packet_ptr** UDP 데이터그램 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3250">**packet_ptr** Pointer to UDP datagram packet pointer.</span></span>
- <span data-ttu-id="112c2-3251">**wait_option** 현재 이 소켓에 큐에 대기된 데이터그램이 없는 경우 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3251">**wait_option** Defines how the service behaves if a datagram is not currently queued on this socket.</span></span> <span data-ttu-id="112c2-3252">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3252">The wait options are defined as follows:</span></span>
- <span data-ttu-id="112c2-3253">NX_NO_WAIT(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="112c2-3253">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="112c2-3254">NX_WAIT_FOREVER(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="112c2-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="112c2-3255">틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="112c2-3255">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3256">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3256">Allowed From</span></span>

<span data-ttu-id="112c2-3257">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-3257">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3258">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3258">Preemption Possible</span></span>

<span data-ttu-id="112c2-3259">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3259">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3260">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3260">Example</span></span>

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-3261">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3261">See Also</span></span>

- <span data-ttu-id="112c2-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3263">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3263">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="112c2-3266">nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3266">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="112c2-3268">nx_udp_socket_send, nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3268">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="112c2-3269">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3269">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="112c2-3270">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="112c2-3270">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="112c2-3271">수신된 각 패킷에 대해 애플리케이션에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3271">Notify application of each received packet</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3272">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3272">Prototype</span></span>

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="112c2-3273">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3273">Description</span></span>

<span data-ttu-id="112c2-3274">이 서비스는 애플리케이션에서 지정한 콜백 함수를 가리키는 수신 알림 함수 포인터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3274">This service sets the receive notify function pointer to the callback function specified by the application.</span></span> <span data-ttu-id="112c2-3275">그러면 소켓에 패킷이 수신될 때마다 이 콜백 함수가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3275">This callback function is then called whenever a packet is received on the socket.</span></span> <span data-ttu-id="112c2-3276">NX_NULL 포인터를 제공하면 수신 알림 함수를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3276">If a NX_NULL pointer is supplied, the receive notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3277">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3277">Parameters</span></span>

- <span data-ttu-id="112c2-3278">**socket_ptr** UDP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3278">**socket_ptr** Pointer to the UDP socket.</span></span>
- <span data-ttu-id="112c2-3279">**udp_receive_notify** 소켓에 패킷이 수신되면 호출되는 애플리케이션 콜백 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3279">**udp_receive_notify** Application callback function pointer that is called when a packet is received on the socket.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3280">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3280">Allowed From</span></span>

<span data-ttu-id="112c2-3281">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="112c2-3281">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3282">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3282">Preemption Possible</span></span>

<span data-ttu-id="112c2-3283">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3283">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3284">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3284">Example</span></span>

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a><span data-ttu-id="112c2-3285">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3285">See Also</span></span>

- <span data-ttu-id="112c2-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3287">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3287">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="112c2-3290">nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3290">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="112c2-3293">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3293">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_send"></a><span data-ttu-id="112c2-3294">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3294">nx_udp_socket_send</span></span>

<span data-ttu-id="112c2-3295">UDP 데이터그램을 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3295">Send a UDP Datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3296">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3296">Prototype</span></span>

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="112c2-3297">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3297">Description</span></span>

<span data-ttu-id="112c2-3298">이 서비스는 이전에 만들고 바인딩한 UDP 소켓을 통해 UDP 데이터그램을 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3298">This service sends a UDP datagram through a previously created and bound UDP socket.</span></span> <span data-ttu-id="112c2-3299">NetX는 대상 IP 주소를 기반으로 하여 원본 주소로 적합한 로컬 IP 주소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3299">NetX finds a suitable local IP address as source address based on the destination IP address.</span></span> <span data-ttu-id="112c2-3300">특정 인터페이스와 원본 IP 주소를 지정하려면 애플리케이션에서 **nx_udp_socket_interface_send** 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3300">To specify a specific interface and source IP address, the application should use the **nx_udp_socket_interface_send** service.</span></span>

<span data-ttu-id="112c2-3301">이 서비스는 UDP 데이터그램이 성공적으로 송신되었는지 여부에 관계없이 즉시 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3301">Note that this service returns immediately regardless of whether the UDP datagram was successfully sent.</span></span>

<span data-ttu-id="112c2-3302">소켓은 로컬 포트에 바인딩되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3302">The socket must be bound to a local port.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3303">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3303">Parameters</span></span>

- <span data-ttu-id="112c2-3304">**socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3304">**socket_ptr** Pointer to previously created UDP socket instance</span></span>
- <span data-ttu-id="112c2-3305">**packet_ptr** UDP 데이터그램 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3305">**packet_ptr** UDP datagram packet pointer</span></span>
- <span data-ttu-id="112c2-3306">**ip_address** 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3306">**ip_address** Destination IP address</span></span>
- <span data-ttu-id="112c2-3307">**port** 호스트 바이트 순서대로 표시된 1에서 0xFFFF 사이의 유효한 대상 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3307">**port** Valid destination port number between 1 and 0xFFFF), in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-3308">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-3308">Return Values</span></span>

- <span data-ttu-id="112c2-3309">**NX_SUCCESS**(0x00) UDP 소켓 송신에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3309">**NX_SUCCESS** (0x00) Successful UDP socket send</span></span>
- <span data-ttu-id="112c2-3310">**NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3310">**NX_NOT_BOUND** (0x24) Socket not bound to any port</span></span>
- <span data-ttu-id="112c2-3311">**NX_NO_INTERFACE_ADDRESS**(0x50) 적절한 송신 인터페이스를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3311">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface can be found.</span></span>
- <span data-ttu-id="112c2-3312">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 서버 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3312">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address</span></span>
- <span data-ttu-id="112c2-3313">**NX_UNDERFLOW**(0x02) 패킷에 UDP 헤더를 위한 공간이 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3313">**NX_UNDERFLOW** (0x02) Not enough room for UDP header in the packet</span></span>
- <span data-ttu-id="112c2-3314">**NX_OVERFLOW**(0x03) 패킷 뒤에 추가 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3314">**NX_OVERFLOW** (0x03) Packet append pointer is invalid</span></span>
- <span data-ttu-id="112c2-3315">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3315">**NX_PTR_ERROR** (0x07) Invalid socket pointer</span></span>
- <span data-ttu-id="112c2-3316">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3316">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="112c2-3317">**NX_NOT_ENABLED**(0x14) UDP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3317">**NX_NOT_ENABLED** (0x14) UDP has not been enabled</span></span>
- <span data-ttu-id="112c2-3318">**NX_INVALID_PORT**(0x46) 포트 번호가 유효한 범위 내에 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3318">**NX_INVALID_PORT** (0x46) Port number is not within a valid range</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3319">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3319">Allowed From</span></span>

<span data-ttu-id="112c2-3320">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-3320">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3321">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3321">Preemption Possible</span></span>

<span data-ttu-id="112c2-3322">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3322">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3323">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3323">Example</span></span>

```C
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
    server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
    the packet out the UDP socket to its peer. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-3324">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3324">See Also</span></span>

- <span data-ttu-id="112c2-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3326">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3326">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="112c2-3329">nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3329">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-3330">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-3330">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="112c2-3332">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3332">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_interface_send"></a><span data-ttu-id="112c2-3333">nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3333">nx_udp_socket_interface_send</span></span>

<span data-ttu-id="112c2-3334">UDP 소켓을 통해 데이터그램을 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3334">Send datagram through UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3335">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3335">Prototype</span></span>

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a><span data-ttu-id="112c2-3336">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3336">Description</span></span>

<span data-ttu-id="112c2-3337">이 서비스는 지정된 IP 주소를 원본 주소로 사용하여 네트워크 인터페이스에서 이전에 만들고 바인딩한 UDP 소켓을 통해 UDP 데이터그램을 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3337">This service sends a UDP datagram through a previously created and bound UDP socket through the network interface with the specified IP address as the source address.</span></span> <span data-ttu-id="112c2-3338">이 서비스는 UDP 데이터그램이 성공적으로 송신되었는지 여부에 관계없이 즉시 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3338">Note that service returns immediately, regardless of whether or not the UDP datagram was successfully sent.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3339">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3339">Parameters</span></span>

- <span data-ttu-id="112c2-3340">**socket_ptr** 패킷을 전송할 소켓입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3340">**socket_ptr** Socket to transmit the packet out on.</span></span>
- <span data-ttu-id="112c2-3341">**packet_ptr** 전송할 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3341">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="112c2-3342">**ip_address** 패킷을 송신할 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3342">**ip_address** Destination IP address to send packet.</span></span>
- <span data-ttu-id="112c2-3343">**port** 대상 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3343">**port** Destination port.</span></span>
- <span data-ttu-id="112c2-3344">**address_index** 패킷을 송신할 인터페이스와 연결된 주소 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3344">**address_index** Index of the address associated with the interface to send packet on.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-3345">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-3345">Return Values</span></span>

- <span data-ttu-id="112c2-3346">**NX_SUCCESS**(0x00) 패킷이 성공적으로 송신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3346">**NX_SUCCESS** (0x00) Packet successfully sent.</span></span>
- <span data-ttu-id="112c2-3347">**NX_NOT_BOUND**(0x24) 소켓이 포트에 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3347">**NX_NOT_BOUND** (0x24) Socket not bound to a port.</span></span>
- <span data-ttu-id="112c2-3348">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3348">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="112c2-3349">**NX_NOT_ENABLED**(0x14) UDP 처리가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3349">**NX_NOT_ENABLED** (0x14) UDP processing not enabled.</span></span>
- <span data-ttu-id="112c2-3350">**NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3350">**NX_PTR_ERROR** (0x07) Invalid pointer.</span></span>
- <span data-ttu-id="112c2-3351">**NX_OVERFLOW**(0x03) 잘못된 패킷 뒤에 추가 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3351">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="112c2-3352">**NX_UNDERFLOW**(0x02) 잘못된 패킷 앞에 추가 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3352">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="112c2-3353">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3353">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-3354">**NX_INVALID_INTERFACE**(0x4C) 잘못된 주소 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3354">**NX_INVALID_INTERFACE** (0x4C) Invalid address index.</span></span>
- <span data-ttu-id="112c2-3355">**NX_INVALID_PORT**(0x46) 포트 번호가 최대 포트 번호를 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3355">**NX_INVALID_PORT** (0x46) Port number exceeds maximum port number.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3356">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3356">Allowed From</span></span>

<span data-ttu-id="112c2-3357">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-3357">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3358">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3358">Preemption Possible</span></span>

<span data-ttu-id="112c2-3359">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3359">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3360">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3360">Example</span></span>

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-3361">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3361">See Also</span></span>

- <span data-ttu-id="112c2-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3363">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3363">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="112c2-3366">nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3366">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-3367">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-3367">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-3368">nx_udp_socket_receive_notify, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3368">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-3369">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-3369">nx_udp_socket_unbind</span></span>

## <a name="nx_udp_socket_unbind"></a><span data-ttu-id="112c2-3370">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-3370">nx_udp_socket_unbind</span></span>

<span data-ttu-id="112c2-3371">UDP 포트에서 UDP 소켓 바인딩을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3371">Unbind UDP socket from UDP port.</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3372">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3372">Prototype</span></span>

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="112c2-3373">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3373">Description</span></span>

<span data-ttu-id="112c2-3374">이 서비스는 UDP 소켓 및 UDP 포트 간 바인딩을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3374">This service releases the binding between the UDP socket and a UDP port.</span></span> <span data-ttu-id="112c2-3375">수신 큐에 저장된 모든 수신된 패킷은 바인딩 해제 작업의 일부로 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3375">Any received packets stored in the receive queue are released as part of the unbind operation.</span></span>

<span data-ttu-id="112c2-3376">다른 소켓을 바인딩 해제된 포트에 바인딩하려고 대기 중인 다른 스레드가 있는 경우 첫 번째 일시 중단된 스레드가 새로 바인딩 해제된 포트에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3376">If there are other threads waiting to bind another socket to the unbound port, the first suspended thread is then bound to the newly unbound port.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3377">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3377">Parameters</span></span>

- <span data-ttu-id="112c2-3378">**socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3378">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-3379">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-3379">Return Values</span></span>

- <span data-ttu-id="112c2-3380">**NX_SUCCESS**(0x00) 소켓을 바인딩 해제하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3380">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="112c2-3381">**NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3381">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="112c2-3382">**NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3382">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="112c2-3383">**NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3383">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="112c2-3384">**NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3384">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3385">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3385">Allowed From</span></span>

<span data-ttu-id="112c2-3386">스레드</span><span class="sxs-lookup"><span data-stu-id="112c2-3386">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3387">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3387">Preemption Possible</span></span>

<span data-ttu-id="112c2-3388">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3388">Yes</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3389">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3389">Example</span></span>

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a><span data-ttu-id="112c2-3390">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3390">See Also</span></span>

- <span data-ttu-id="112c2-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3392">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3392">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="112c2-3395">nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3395">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-3396">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-3396">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-3397">nx_udp_socket_receive_notify, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3397">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span></span>

## <a name="nx_udp_source_extract"></a><span data-ttu-id="112c2-3399">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="112c2-3399">nx_udp_source_extract</span></span>

<span data-ttu-id="112c2-3400">UDP 데이터그램에서 IP 및 송신 포트를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3400">Extract IP and sending port from UDP datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="112c2-3401">프로토타입</span><span class="sxs-lookup"><span data-stu-id="112c2-3401">Prototype</span></span>

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a><span data-ttu-id="112c2-3402">Description</span><span class="sxs-lookup"><span data-stu-id="112c2-3402">Description</span></span>

<span data-ttu-id="112c2-3403">이 서비스는 제공된 UDP 데이터그램의 IP 및 UDP 헤더에서 송신기 IP 및 포트 번호를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3403">This service extracts the sender's IP and port number from the IP and UDP headers of the supplied UDP datagram.</span></span>

### <a name="parameters"></a><span data-ttu-id="112c2-3404">매개 변수</span><span class="sxs-lookup"><span data-stu-id="112c2-3404">Parameters</span></span>

- <span data-ttu-id="112c2-3405">**packet_ptr** UDP 데이터그램 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3405">**packet_ptr** UDP datagram packet pointer.</span></span>
- <span data-ttu-id="112c2-3406">**ip_address** 반환 IP 주소 변수를 가리키는 유효한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3406">**ip_address** Valid pointer to the return IP address variable.</span></span>
- <span data-ttu-id="112c2-3407">**port** 반환 포트 변수를 가리키는 유효한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3407">**port** Valid pointer to the return port variable.</span></span>

### <a name="return-values"></a><span data-ttu-id="112c2-3408">반환 값</span><span class="sxs-lookup"><span data-stu-id="112c2-3408">Return Values</span></span>

- <span data-ttu-id="112c2-3409">**NX_SUCCESS**(0x00) 원본 IP/포트 추출에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3409">**NX_SUCCESS** (0x00) Successful source IP/port extraction.</span></span>
- <span data-ttu-id="112c2-3410">**NX_INVALID_PACKET**(0x12) 제공된 패킷이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3410">**NX_INVALID_PACKET** (0x12) The supplied packet is invalid.</span></span>
- <span data-ttu-id="112c2-3411">**NX_PTR_ERROR**(0x07) 패킷이나 IP 또는 포트 대상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="112c2-3411">**NX_PTR_ERROR** (0x07) Invalid packet or IP or port destination.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="112c2-3412">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="112c2-3412">Allowed From</span></span>

<span data-ttu-id="112c2-3413">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="112c2-3413">Initialization, threads, timers, ISR</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="112c2-3414">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="112c2-3414">Preemption Possible</span></span>

<span data-ttu-id="112c2-3415">예</span><span class="sxs-lookup"><span data-stu-id="112c2-3415">No</span></span>

### <a name="example"></a><span data-ttu-id="112c2-3416">예제</span><span class="sxs-lookup"><span data-stu-id="112c2-3416">Example</span></span>

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a><span data-ttu-id="112c2-3417">참고 항목</span><span class="sxs-lookup"><span data-stu-id="112c2-3417">See Also</span></span>

- <span data-ttu-id="112c2-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="112c2-3419">nx_udp_packet_info_extract, nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="112c2-3419">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="112c2-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="112c2-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="112c2-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="112c2-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="112c2-3422">nx_udp_socket_delete, nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="112c2-3422">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="112c2-3423">nx_udp_socket_port_get, nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="112c2-3423">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="112c2-3424">nx_udp_socket_receive_notify, nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="112c2-3424">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="112c2-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="112c2-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span></span>