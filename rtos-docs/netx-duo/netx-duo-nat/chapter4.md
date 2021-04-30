---
title: 4장 - NAT 서비스 설명
description: 이 장에서는 모든 NetX Duo NAT API 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8bdbdfcb2da6425fb99cadc7b2f6815dedc12953
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810668"
---
# <a name="chapter-4---description-of-nat-services"></a><span data-ttu-id="62602-103">4장 - NAT 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="62602-103">Chapter 4 - Description of NAT services</span></span>

<span data-ttu-id="62602-104">이 장에서는 아래에 나열된 모든 NetX Duo NAT API 서비스에 대해 알파벳 순서로 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62602-104">This chapter contains a description of all NetX Duo NAT API services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="62602-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="62602-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_nat_create"></a><span data-ttu-id="62602-106">nx_nat_create</span><span class="sxs-lookup"><span data-stu-id="62602-106">nx_nat_create</span></span>

<span data-ttu-id="62602-107">NAT 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="62602-107">Create a NAT Server</span></span>

### <a name="prototype"></a><span data-ttu-id="62602-108">프로토타입</span><span class="sxs-lookup"><span data-stu-id="62602-108">Prototype</span></span>

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a><span data-ttu-id="62602-109">Description</span><span class="sxs-lookup"><span data-stu-id="62602-109">Description</span></span>

<span data-ttu-id="62602-110">이 서비스는 NAT 서버의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="62602-110">This service creates an instance of the NAT server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62602-111">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-111">Input Parameters</span></span>

- <span data-ttu-id="62602-112">**nat_ptr** 만들 NAT 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="62602-112">**nat_ptr** Pointer to NAT instance to create</span></span>
- <span data-ttu-id="62602-113">**ip_ptr** IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="62602-113">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="62602-114">**global_interface_index** 글로벌 네트워크 인터페이스에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="62602-114">**global_interface_index** Index to the global network interface</span></span>
- <span data-ttu-id="62602-115">**dynamic_cache_memory** NAT 테이블에 대한 포인터 메모리 영역</span><span class="sxs-lookup"><span data-stu-id="62602-115">**dynamic_cache_memory** Pointer memory area to NAT table</span></span>
- <span data-ttu-id="62602-116">**dynamic_cache_size** NAT 테이블에 대한 메모리 영역 크기</span><span class="sxs-lookup"><span data-stu-id="62602-116">**dynamic_cache_size** Size of memory area for NAT table</span></span>

### <a name="return-values"></a><span data-ttu-id="62602-117">반환 값</span><span class="sxs-lookup"><span data-stu-id="62602-117">Return Values</span></span>

- <span data-ttu-id="62602-118">**NX_SUCCESS** (0x00) NAT 서버를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="62602-118">**NX_SUCCESS** (0x00) NAT server successfully created</span></span>
- <span data-ttu-id="62602-119">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-119">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="62602-120">NX_NAT_PARAM_ERROR (0xD01) 잘못된 포인터가 아닌 입력</span><span class="sxs-lookup"><span data-stu-id="62602-120">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>
- <span data-ttu-id="62602-121">NX_NAT_CACHE_ERROR (0xD02) 잘못된 캐시 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="62602-121">NX_NAT_CACHE_ERROR (0xD02) Invalid cache pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62602-122">허용 위치</span><span class="sxs-lookup"><span data-stu-id="62602-122">Allowed From</span></span>

<span data-ttu-id="62602-123">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="62602-123">Application code</span></span>

### <a name="example"></a><span data-ttu-id="62602-124">예제</span><span class="sxs-lookup"><span data-stu-id="62602-124">Example</span></span>

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a><span data-ttu-id="62602-125">nx_nat_delete</span><span class="sxs-lookup"><span data-stu-id="62602-125">nx_nat_delete</span></span>

<span data-ttu-id="62602-126">NAT 서버 삭제</span><span class="sxs-lookup"><span data-stu-id="62602-126">Delete a NAT Server</span></span>

### <a name="prototype"></a><span data-ttu-id="62602-127">프로토타입</span><span class="sxs-lookup"><span data-stu-id="62602-127">Prototype</span></span>

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="62602-128">Description</span><span class="sxs-lookup"><span data-stu-id="62602-128">Description</span></span>

<span data-ttu-id="62602-129">이 서비스는 이전에 만든 NAT 서버를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="62602-129">This service deletes a previously created NAT Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62602-130">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-130">Input Parameters</span></span>

- <span data-ttu-id="62602-131">**nat_ptr** 삭제할 NAT 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="62602-131">**nat_ptr** Pointer to NAT instance to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="62602-132">반환 값</span><span class="sxs-lookup"><span data-stu-id="62602-132">Return Values</span></span>

- <span data-ttu-id="62602-133">**NX_SUCCESS** (0x00) NAT를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="62602-133">**NX_SUCCESS** (0x00) NAT successfully deleted</span></span>
- <span data-ttu-id="62602-134">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-134">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62602-135">허용 위치</span><span class="sxs-lookup"><span data-stu-id="62602-135">Allowed From</span></span>

<span data-ttu-id="62602-136">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="62602-136">Application code</span></span>

### <a name="example"></a><span data-ttu-id="62602-137">예제</span><span class="sxs-lookup"><span data-stu-id="62602-137">Example</span></span>

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a><span data-ttu-id="62602-138">nx_nat_enable</span><span class="sxs-lookup"><span data-stu-id="62602-138">nx_nat_enable</span></span>

<span data-ttu-id="62602-139">NAT에 대한 IP 인스턴스 사용</span><span class="sxs-lookup"><span data-stu-id="62602-139">Enable the IP instance for NAT</span></span>

### <a name="prototype"></a><span data-ttu-id="62602-140">프로토타입</span><span class="sxs-lookup"><span data-stu-id="62602-140">Prototype</span></span>

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="62602-141">Description</span><span class="sxs-lookup"><span data-stu-id="62602-141">Description</span></span>

<span data-ttu-id="62602-142">이 서비스는 NAT에 대한 IP 인스턴스를 사용하도록 설정합니다(예: NAT 서버에 받은 패킷을 전달).</span><span class="sxs-lookup"><span data-stu-id="62602-142">This service enables the IP instance for NAT (e.g. forward received packets to the NAT server).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62602-143">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-143">Input Parameters</span></span>

- <span data-ttu-id="62602-144">**nat_ptr** NAT 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="62602-144">**nat_ptr** Pointer to NAT instance</span></span>

### <a name="return-values"></a><span data-ttu-id="62602-145">반환 값</span><span class="sxs-lookup"><span data-stu-id="62602-145">Return Values</span></span>

- <span data-ttu-id="62602-146">**NX_SUCCESS** (0x00) NAT를 성공적으로 사용하도록 설정함</span><span class="sxs-lookup"><span data-stu-id="62602-146">**NX_SUCCESS** (0x00) NAT successfully enabled</span></span>
- <span data-ttu-id="62602-147">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-147">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62602-148">허용 위치</span><span class="sxs-lookup"><span data-stu-id="62602-148">Allowed From</span></span>

<span data-ttu-id="62602-149">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="62602-149">Application code</span></span>

### <a name="example"></a><span data-ttu-id="62602-150">예제</span><span class="sxs-lookup"><span data-stu-id="62602-150">Example</span></span>

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a><span data-ttu-id="62602-151">nx_nat_disable</span><span class="sxs-lookup"><span data-stu-id="62602-151">nx_nat_disable</span></span>

<span data-ttu-id="62602-152">NAT에 대한 IP 인스턴스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="62602-152">Disable the IP instance for NAT</span></span>

### <a name="prototype"></a><span data-ttu-id="62602-153">프로토타입</span><span class="sxs-lookup"><span data-stu-id="62602-153">Prototype</span></span>

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="62602-154">Description</span><span class="sxs-lookup"><span data-stu-id="62602-154">Description</span></span>

<span data-ttu-id="62602-155">이 서비스는 IP 인스턴스에서 NAT를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="62602-155">This service disables NAT on the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62602-156">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-156">Input Parameters</span></span>

- <span data-ttu-id="62602-157">**nat_ptr** NAT 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="62602-157">**nat_ptr** Pointer to NAT instance</span></span>

### <a name="return-values"></a><span data-ttu-id="62602-158">반환 값</span><span class="sxs-lookup"><span data-stu-id="62602-158">Return Values</span></span>

- <span data-ttu-id="62602-159">**NX_SUCCESS** (0x00) NAT를 성공적으로 사용하지 않도록 설정함</span><span class="sxs-lookup"><span data-stu-id="62602-159">**NX_SUCCESS** (0x00) NAT successfully disabled</span></span>
- <span data-ttu-id="62602-160">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-160">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62602-161">허용 위치</span><span class="sxs-lookup"><span data-stu-id="62602-161">Allowed From</span></span>

<span data-ttu-id="62602-162">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="62602-162">Application code</span></span>

### <a name="example"></a><span data-ttu-id="62602-163">예제</span><span class="sxs-lookup"><span data-stu-id="62602-163">Example</span></span>

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a><span data-ttu-id="62602-164">nx_nat_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="62602-164">nx_nat_cache_notify_set</span></span>

<span data-ttu-id="62602-165">캐시 전체 알림 콜백 함수 설정</span><span class="sxs-lookup"><span data-stu-id="62602-165">Set a cache full notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="62602-166">프로토타입</span><span class="sxs-lookup"><span data-stu-id="62602-166">Prototype</span></span>

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a><span data-ttu-id="62602-167">Description</span><span class="sxs-lookup"><span data-stu-id="62602-167">Description</span></span>

<span data-ttu-id="62602-168">이 서비스는 사용자 정의 캐시 전체 알림 함수를 가리키는 cache_full_notify_cb 입력 함수 포인터를 사용하여 캐시 전체 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="62602-168">This service registers the cache full callback with the input function pointer cache_full_notify_cb which points to a user defined cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62602-169">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-169">Input Parameters</span></span>

- <span data-ttu-id="62602-170">**nat_ptr** NAT 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="62602-170">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="62602-171">**cache_full_notify_cb** 캐시 전체 알림 함수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="62602-171">**cache_full_notify_cb** Pointer to cache full notify function</span></span>

### <a name="return-values"></a><span data-ttu-id="62602-172">반환 값</span><span class="sxs-lookup"><span data-stu-id="62602-172">Return Values</span></span>

- <span data-ttu-id="62602-173">**NX_SUCCESS** (0x00) 캐시 전체 알림 함수가 성공적으로 설정됨</span><span class="sxs-lookup"><span data-stu-id="62602-173">**NX_SUCCESS** (0x00) Cache full notify function successfully set</span></span>
- <span data-ttu-id="62602-174">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-174">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="62602-175">NX_NAT_PARAM_ERROR (0xD01) 잘못된 포인터가 아닌 입력</span><span class="sxs-lookup"><span data-stu-id="62602-175">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62602-176">허용 위치</span><span class="sxs-lookup"><span data-stu-id="62602-176">Allowed From</span></span>

<span data-ttu-id="62602-177">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="62602-177">Application code</span></span>

### <a name="example"></a><span data-ttu-id="62602-178">예제</span><span class="sxs-lookup"><span data-stu-id="62602-178">Example</span></span>

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a><span data-ttu-id="62602-179">nx_nat_inbound_entry_create</span><span class="sxs-lookup"><span data-stu-id="62602-179">nx_nat_inbound_entry_create</span></span>

<span data-ttu-id="62602-180">NAT 변환 테이블에서 인바운드 항목 만들기</span><span class="sxs-lookup"><span data-stu-id="62602-180">Create an inbound entry in the NAT translation table</span></span>

### <a name="prototype"></a><span data-ttu-id="62602-181">프로토타입</span><span class="sxs-lookup"><span data-stu-id="62602-181">Prototype</span></span>

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a><span data-ttu-id="62602-182">Description</span><span class="sxs-lookup"><span data-stu-id="62602-182">Description</span></span>

<span data-ttu-id="62602-183">이 서비스는 인바운드 항목을 정적(영구 입력, 만료되지 않음)으로 만들고 NAT 변환 테이블에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="62602-183">This service creates an inbound entry as static (permanent entry, never expires) and adds it to the NAT translation table.</span></span> <span data-ttu-id="62602-184">이러한 항목은 일반적으로 외부 네트워크의 호스트에서 연결이 시작되는 로컬 호스트 서버에 대해 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="62602-184">These entries are usually created for local host servers where a connection is initiated from a host on the outside network.</span></span> <span data-ttu-id="62602-185">NAT 서버는 외부 포트가 이미 변환 테이블에 사용되고 있지 않거나 동일한 프로토콜의 이전의 기존 NetX Duo 소켓에 의해 바인딩되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="62602-185">The NAT server checks that the external port is not already in use in the translation table or bound by a previously existing NetX Duo socket of the same protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62602-186">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-186">Input Parameters</span></span>

- <span data-ttu-id="62602-187">**nat_ptr** NAT 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="62602-187">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="62602-188">**entry_ptr** 번역 항목에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="62602-188">**entry_ptr** Pointer to translation entry</span></span>
- <span data-ttu-id="62602-189">**local_ip_address** 로컬 호스트 IP 주소</span><span class="sxs-lookup"><span data-stu-id="62602-189">**local_ip_address** Local host IP address</span></span>
- <span data-ttu-id="62602-190">**external_port** 외부 네트워크의 대상 포트</span><span class="sxs-lookup"><span data-stu-id="62602-190">**external_port** Destination port on the external network</span></span>
- <span data-ttu-id="62602-191">**local_port** 원본 (로컬 호스트) 포트</span><span class="sxs-lookup"><span data-stu-id="62602-191">**local_port** Source (local host) port</span></span>
- <span data-ttu-id="62602-192">**protocol** 패킷 프로토콜(예: TCP)</span><span class="sxs-lookup"><span data-stu-id="62602-192">**protocol** Packet protocol (e.g TCP)</span></span>

### <a name="return-values"></a><span data-ttu-id="62602-193">반환 값</span><span class="sxs-lookup"><span data-stu-id="62602-193">Return Values</span></span>

- <span data-ttu-id="62602-194">**NX_SUCCESS** (0x00) 항목을 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="62602-194">**NX_SUCCESS** (0x00) Entry successfully created</span></span>
- <span data-ttu-id="62602-195">**NX_NAT_PORT_UNAVAILABLE** (0xD0D) 잘못된 외부 포트</span><span class="sxs-lookup"><span data-stu-id="62602-195">**NX_NAT_PORT_UNAVAILABLE** (0xD0D) Invalid external port</span></span>
- <span data-ttu-id="62602-196">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-196">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="62602-197">NX_NAT_PARAM_ERROR (0xD01) 잘못된 포인터가 아닌 입력</span><span class="sxs-lookup"><span data-stu-id="62602-197">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62602-198">허용 위치</span><span class="sxs-lookup"><span data-stu-id="62602-198">Allowed From</span></span>

<span data-ttu-id="62602-199">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="62602-199">Application code</span></span>

### <a name="example"></a><span data-ttu-id="62602-200">예제</span><span class="sxs-lookup"><span data-stu-id="62602-200">Example</span></span>

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a><span data-ttu-id="62602-201">nx_nat_inbound_entry_delete</span><span class="sxs-lookup"><span data-stu-id="62602-201">nx_nat_inbound_entry_delete</span></span>

<span data-ttu-id="62602-202">NAT 변환 테이블에서 인바운드 항목 삭제</span><span class="sxs-lookup"><span data-stu-id="62602-202">Delete an inbound entry in the NAT translation table</span></span>

### <a name="prototype"></a><span data-ttu-id="62602-203">프로토타입</span><span class="sxs-lookup"><span data-stu-id="62602-203">Prototype</span></span>

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a><span data-ttu-id="62602-204">Description</span><span class="sxs-lookup"><span data-stu-id="62602-204">Description</span></span>

<span data-ttu-id="62602-205">이 서비스는 번역 테이블에서 지정된 인바운드 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="62602-205">This service deletes the specified inbound entry from the translation table.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62602-206">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-206">Input Parameters</span></span>

- <span data-ttu-id="62602-207">**nat_ptr** NAT 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="62602-207">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="62602-208">**delete_entry_ptr** NAT 변환 항목에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="62602-208">**delete_entry_ptr** Pointer to the NAT translation entry</span></span>

### <a name="return-values"></a><span data-ttu-id="62602-209">반환 값</span><span class="sxs-lookup"><span data-stu-id="62602-209">Return Values</span></span>

- <span data-ttu-id="62602-210">**NX_SUCCESS** (0x00) 항목을 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="62602-210">**NX_SUCCESS** (0x00) Entry successfully deleted</span></span>
- <span data-ttu-id="62602-211">**NX_NAT_ENTRY_NOT_FOUND** (0xD04) 항목을 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="62602-211">**NX_NAT_ENTRY_NOT_FOUND** (0xD04) Entry does not found</span></span>
- <span data-ttu-id="62602-212">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="62602-212">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="62602-213">NX_NAT_ENTRY_TYPE_ERROR (0xD0C) 잘못된 변환 형식</span><span class="sxs-lookup"><span data-stu-id="62602-213">NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Invalid translation type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62602-214">허용 위치</span><span class="sxs-lookup"><span data-stu-id="62602-214">Allowed From</span></span>

<span data-ttu-id="62602-215">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="62602-215">Application code</span></span>

### <a name="example"></a><span data-ttu-id="62602-216">예제</span><span class="sxs-lookup"><span data-stu-id="62602-216">Example</span></span>

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
