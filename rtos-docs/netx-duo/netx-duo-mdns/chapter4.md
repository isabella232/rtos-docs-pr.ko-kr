---
title: 챕터 4 - mDNS 서비스 설명
description: 이 챕터에는 모든 NetX mDNS 서비스에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89df0ab5f09be8ad50a27d23bae8b20d71caa0b4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810734"
---
# <a name="chapter-4---description-of-mdns-services"></a><span data-ttu-id="a6906-103">챕터 4 - mDNS 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="a6906-103">Chapter 4 - Description of mDNS services</span></span>

<span data-ttu-id="a6906-104">이 챕터에는 모든 NetX mDNS 서비스에 대한 설명이 포함되어 있습니다(아래 참조).</span><span class="sxs-lookup"><span data-stu-id="a6906-104">This chapter contains a description of all NetX mDNS services (listed below).</span></span>

> [!NOTE]
> <span data-ttu-id="a6906-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_mdns_create"></a><span data-ttu-id="a6906-106">nx_mdns_create</span><span class="sxs-lookup"><span data-stu-id="a6906-106">nx_mdns_create</span></span>

<span data-ttu-id="a6906-107">mDNS 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="a6906-107">Create an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-108">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-108">Prototype</span></span>

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a><span data-ttu-id="a6906-109">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-109">Description</span></span>

<span data-ttu-id="a6906-110">이 서비스는 특정 IP 인스턴스 및 관련 리소스에 mDNS 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-110">This service creates an mDNS instance on the specific IP instance and associated resources.</span></span> <span data-ttu-id="a6906-111">들어오는 mDNS 메시지를 처리하고, 쿼리에 응답하고, 쿼리 메시지를 정기적으로 전송하는 스레드도 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-111">A thread is also created to handle incoming mDNS messages, to respond to queries, and to periodically transmit query messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-112">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-112">Input Parameters</span></span>

- <span data-ttu-id="a6906-113">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-113">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-114">**ip_ptr** 연결된 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-114">**ip_ptr** Pointer to the associated IP instance.</span></span>
- <span data-ttu-id="a6906-115">**packet_pool** 유효한 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-115">**packet_pool** Pointer to a valid packet pool.</span></span>
- <span data-ttu-id="a6906-116">**priority** mDNS 스레드의 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-116">**priority** Priority of the mDNS thread.</span></span>
- <span data-ttu-id="a6906-117">**stack_ptr** mDNS 스레드의 스택 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-117">**stack_ptr** Pointer to the stack area for the mDNS thread</span></span>
- <span data-ttu-id="a6906-118">**stack_size** 스택 영역의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-118">**stack_size** Size of the stack area.</span></span>
- <span data-ttu-id="a6906-119">**host_name** 이 노드에 할당된 호스트 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-119">**host_name** Host name assigned to this node.</span></span>
- <span data-ttu-id="a6906-120">**local_service_cache** 로컬 등록 서비스에 대한 스토리지 공간입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-120">**local_service_cache** Storage space for local registered services.</span></span>
- <span data-ttu-id="a6906-121">**local_service_cache_size** 로컬 서비스 캐시의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-121">**local_service_cache_size** Size of the local service cache.</span></span>
- <span data-ttu-id="a6906-122">**peer_service_cache** 수신된 서비스 정보에 대한 스토리지 공간입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-122">**peer_service_cache** Storage space for service information received</span></span>
- <span data-ttu-id="a6906-123">**peer_service_cache_size** 피어 서비스 캐시의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-123">**peer_service_cache_size** Size of the peer service cache</span></span>
- <span data-ttu-id="a6906-124">**probing_notify** 검색 작업이 끝날 때 호출되는 선택적 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-124">**probing_notify** Optional callback function invoked at the end of the probing operation.</span></span> <span data-ttu-id="a6906-125">호스트 이름(로컬 인터페이스에서 mDNS를 사용하도록 설정하는 경우) 또는 서비스 이름(서비스를 등록한 후)이 고유한지 여부를 애플리케이션에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-125">It notifies the application whether or not the host name (when enabling mDNS on a local interface), or the service name (after registering a service) is unique.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-126">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-126">Return Values</span></span>

- <span data-ttu-id="a6906-127">**NX_SUCCESS** (0x00) mDNS 인스턴스를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-127">**NX_SUCCESS** (0x00) Successfully created mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-128">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-128">Allowed From</span></span>

<span data-ttu-id="a6906-129">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-130">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-130">Example</span></span>

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a><span data-ttu-id="a6906-131">nx_mdns_delete</span><span class="sxs-lookup"><span data-stu-id="a6906-131">nx_mdns_delete</span></span>

<span data-ttu-id="a6906-132">mDNS 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="a6906-132">Delete an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-133">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-133">Prototype</span></span>

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="a6906-134">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-134">Description</span></span>

<span data-ttu-id="a6906-135">이 서비스는 mDNS 인스턴스를 삭제하고 해당 리소스를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-135">This service deletes the mDNS instance and frees its resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-136">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-136">Input Parameters</span></span>

- <span data-ttu-id="a6906-137">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-137">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-138">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-138">Return Values</span></span>

- <span data-ttu-id="a6906-139">**NX_SUCCESS** (0x00) mDNS 인스턴스를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-139">**NX_SUCCESS** (0x00) Successfully deleted the mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-140">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-140">Allowed From</span></span>

<span data-ttu-id="a6906-141">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-142">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-142">Example</span></span>

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a><span data-ttu-id="a6906-143">nx_mdns_enable</span><span class="sxs-lookup"><span data-stu-id="a6906-143">nx_mdns_enable</span></span>

<span data-ttu-id="a6906-144">mDNS 서비스 시작</span><span class="sxs-lookup"><span data-stu-id="a6906-144">Start the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-145">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-145">Prototype</span></span>

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="a6906-146">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-146">Description</span></span>

<span data-ttu-id="a6906-147">이 API는 특정 실제 인터페이스에서 mDNS 서비스를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-147">This API enables mDNS service on specific physical interface.</span></span> <span data-ttu-id="a6906-148">서비스를 사용하도록 설정하면 mDNS 모듈이 인터페이스에서 받은 쿼리에 응답하기 전에 먼저 네트워크에서 모든 고유한 서비스 이름을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-148">Once the service is enabled, the mDNS module first probes all its unique service names on the network before responding to queries received on the interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-149">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-149">Input Parameters</span></span>

- <span data-ttu-id="a6906-150">**mdns_ptr** mDNS 인스턴스 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-150">**mdns_ptr** Pointer to the mDNS instance control block.</span></span>
- <span data-ttu-id="a6906-151">**interface_index** 서비스를 사용하도록 설정할 인터페이스에 대한 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-151">**interface_index** Index to the interface where the service is to be enabled</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-152">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-152">Return Values</span></span>

- <span data-ttu-id="a6906-153">**NX_SUCCESS** (0x00)에서 서비스를 성공적으로 사용하도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-153">**NX_SUCCESS** (0x00) Successfully enabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-154">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-154">Allowed From</span></span>

<span data-ttu-id="a6906-155">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-155">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-156">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-156">Example</span></span>

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a><span data-ttu-id="a6906-157">nx_mdns_disable</span><span class="sxs-lookup"><span data-stu-id="a6906-157">nx_mdns_disable</span></span>

<span data-ttu-id="a6906-158">mDNS 서비스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="a6906-158">Disable the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-159">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-159">Prototype</span></span>

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="a6906-160">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-160">Description</span></span>

<span data-ttu-id="a6906-161">이 API는 특정 실제 인터페이스에서 mDNS 서비스를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-161">This API disables mDNS service on the specific physical interface.</span></span> <span data-ttu-id="a6906-162">서비스를 사용하지 않도록 설정하면 mDNS가 인터페이스에 연결된 네트워크에 모든 로컬 서비스에 대한 "종료" 메시지를 보내므로 인접 노드에 알림이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-162">Once the service is disabled, the mDNS sends "goodbye" messages for every local service to the network that is attached to the interface, so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-163">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-163">Input Parameters</span></span>

- <span data-ttu-id="a6906-164">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-164">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-165">**interface_index** 서비스를 사용하지 않도록 설정할 인터페이스에 대한 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-165">**interface_index** Index to the interface where the service is to be disabled</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-166">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-166">Return Values</span></span>

- <span data-ttu-id="a6906-167">**NX_SUCCESS** (0x00)에서 서비스를 성공적으로 사용하지 않도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-167">**NX_SUCCESS** (0x00) Successfully disabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-168">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-168">Allowed From</span></span>

<span data-ttu-id="a6906-169">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-170">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-170">Example</span></span>

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a><span data-ttu-id="a6906-171">nx_mdns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="a6906-171">nx_mdns_cache_notify_set</span></span>

<span data-ttu-id="a6906-172">mDNS 캐시 가득참 알림 함수</span><span class="sxs-lookup"><span data-stu-id="a6906-172">Installs the mDNS cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-173">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-173">Prototype</span></span>

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a><span data-ttu-id="a6906-174">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-174">Description</span></span>

<span data-ttu-id="a6906-175">이 서비스는 로컬 서비스 캐시 또는 피어 서비스 캐시가 가득찰 때 호출되는 사용자 제공 콜백 함수를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-175">This service installs a user-supplied callback function, which is invoked when either the local service cache or peer service cache becomes full.</span></span> <span data-ttu-id="a6906-176">서비스 캐시가 가득차면 더 이상 mDNS 리소스 레코드를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-176">When the service cache is full, no more mDNS Resource Record can be added.</span></span> <span data-ttu-id="a6906-177">다양한 문자열 길이의 서비스를 추가 및 제거하면 내부 조각화로 인해 서비스 캐시가 가득찰 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-177">Note that the service cache may become full as a result of internal fragmentation, when services with various string lengths are added and removed.</span></span> <span data-ttu-id="a6906-178">피어 서비스 캐시에 대한 캐시 가득참 알림이 수신되면 애플리케이션이 "*nx_mdns_service_cache_clear"* 서비스를 사용하여 피어 서비스 캐시의 모든 항목을 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-178">On receiving a cache full notification on peer service cache, the application may use the service "*nx_mdns_service_cache_clear"* to erase all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-179">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-179">Input Parameters</span></span>

- <span data-ttu-id="a6906-180">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-180">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-181">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-181">Return Values</span></span>

- <span data-ttu-id="a6906-182">**NX_SUCCESS** (0x00) mDNS 캐시 알림 콜백 함수를 성공적으로 설치했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-182">**NX_SUCCESS** (0x00) Successfully installed the mDNS cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-183">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-183">Allowed From</span></span>

<span data-ttu-id="a6906-184">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-185">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-185">Example</span></span>

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a><span data-ttu-id="a6906-186">nx_mdns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="a6906-186">nx_mdns_cache_notify_clear</span></span>

<span data-ttu-id="a6906-187">mDNS 서비스 캐시 가득참 알림 함수 지우기</span><span class="sxs-lookup"><span data-stu-id="a6906-187">Clear the mDNS service cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-188">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-188">Prototype</span></span>

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="a6906-189">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-189">Description</span></span>

<span data-ttu-id="a6906-190">이 서비스는 사용자 제공 서비스 캐시 알림 콜백 함수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-190">This service clears a user-supplied service cache notify callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-191">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-191">Input Parameters</span></span>

- <span data-ttu-id="a6906-192">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-192">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-193">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-193">Return Values</span></span>

- <span data-ttu-id="a6906-194">**NX_SUCCESS** (0x00) mDNS 서비스 캐시 알림 콜백 함수를 성공적으로 지웠습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-194">**NX_SUCCESS** (0x00) Successfully cleared the mDNS service cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-195">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-195">Allowed From</span></span>

<span data-ttu-id="a6906-196">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-197">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-197">Example</span></span>

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a><span data-ttu-id="a6906-198">nx_mdns_domain_name_set</span><span class="sxs-lookup"><span data-stu-id="a6906-198">nx_mdns_domain_name_set</span></span>

<span data-ttu-id="a6906-199">도메인 이름 설정</span><span class="sxs-lookup"><span data-stu-id="a6906-199">Sets the domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-200">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-200">Prototype</span></span>

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="a6906-201">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-201">Description</span></span>

<span data-ttu-id="a6906-202">이 서비스는 기본 로컬 도메인 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-202">This service sets up the default local domain name.</span></span> <span data-ttu-id="a6906-203">mDNS 인스턴스를 만들 때 기본 로컬 도메인 이름은 ".local"로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-203">When the mDNS instance is created, the default local domain name is set to “.local”.</span></span> <span data-ttu-id="a6906-204">이 API를 사용하면 애플리케이션에서 기본 로컬 도메인 이름을 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-204">This API allows an application to overwrite the default local domain name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-205">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-205">Input Parameters</span></span>

- <span data-ttu-id="a6906-206">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-206">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-207">**domain_name** 사용할 도메인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-207">**domain_name** The domain name to be used.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-208">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-208">Return Values</span></span>

- <span data-ttu-id="a6906-209">**NX_SUCCESS** (0x00)에서 로컬 도메인을 성공적으로 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-209">**NX_SUCCESS** (0x00) Successfully configured local domain.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-210">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-210">Allowed From</span></span>

<span data-ttu-id="a6906-211">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-212">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-212">Example</span></span>

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a><span data-ttu-id="a6906-213">nx_mdns_service_announcement_timing_set</span><span class="sxs-lookup"><span data-stu-id="a6906-213">nx_mdns_service_announcement_timing_set</span></span>

<span data-ttu-id="a6906-214">서비스 공지 메시지의 타이밍 매개 변수 설정</span><span class="sxs-lookup"><span data-stu-id="a6906-214">Sets the timing parameters for service announcement messages</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-215">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-215">Prototype</span></span>

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a><span data-ttu-id="a6906-216">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-216">Description</span></span>

<span data-ttu-id="a6906-217">이 서비스는 서비스 공지를 보낼 때 mDNS에서 사용하는 타이밍 매개 변수를 재구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-217">This service reconfigures the timing parameters employed by mDNS when sending the service announcements.</span></span> <span data-ttu-id="a6906-218">게시 기간은 *t* 틱에서 시작되고 2의 *k* 계수 제곱으로 망원식으로 확장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-218">Publish period starts from *t* ticks and can be expanded telescopically with 2 to the power of *k* factor.</span></span> <span data-ttu-id="a6906-219">보급 알림당 반복 횟수는 *p* 이고, 반복되는 각 보급 알림 사이의 간격은 *interval* 틱이며, 공지 기간 수는 max_time입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-219">The number of repetitions per advertisement is *p*, the interval between each repeated advertisement is *interval* ticks, and the number of announcement period is max_time.</span></span> <span data-ttu-id="a6906-220">기본적으로 초기 기간은 k = 1(기간이 두 배씩 증가), *p = 1*(반복 안 함), retrans_interval = 0(시간 간격 없음), period_interval = 0xFFFFFFFF(최대 기간 간격) 및 max_time = 3(보급 알림 수)을 사용하여 1초로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-220">By default, the initial period is set to 1 second, with k = 1 (the period doubles each time), *p = 1* (no repetition), retrans_interval = 0(no time interval), period_interval = 0xFFFFFFFF(max period interval) and max_time = 3(number of advertisement).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-221">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-221">Input Parameters</span></span>

- <span data-ttu-id="a6906-222">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-222">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-223">**t** 초기 기간의 틱 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-223">**t** Number of ticks for the initial period.</span></span> <span data-ttu-id="a6906-224">기본값은 100틱(1초)입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-224">Default is 100 ticks for 1 second.</span></span>
- <span data-ttu-id="a6906-225">**p** 반복 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-225">**p** Number of repetitions.</span></span> <span data-ttu-id="a6906-226">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-226">Default value is 1.</span></span>
- <span data-ttu-id="a6906-227">**k** 망원식 계수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-227">**k** Telescopic factor.</span></span> <span data-ttu-id="a6906-228">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-228">Default value is 1.</span></span>
- <span data-ttu-id="a6906-229">**retrans_interval** 반복된 공지 메시지를 보내기 전에 대기할 틱 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-229">**retrans_interval** Number of ticks to wait before sending out repeated announcement messages.</span></span> <span data-ttu-id="a6906-230">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-230">Default value is 0.</span></span>
- <span data-ttu-id="a6906-231">**period_interval** 두 공지 기간 사이의 틱 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-231">**period_interval** Number of ticks between two announcement period.</span></span> <span data-ttu-id="a6906-232">기본값은 0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-232">Default value is 0xFFFFFFFF.</span></span>
- <span data-ttu-id="a6906-233">**max_time** 보급 알림에 사용할 공지 기간의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-233">**max_time** Number of announcement period to use for the advertisement.</span></span> <span data-ttu-id="a6906-234">*max_time* 공지 기간 후에는 더 이상 공지 메시지가 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-234">After the *max_time* announcement periods, no more announcement messages are sent.</span></span> <span data-ttu-id="a6906-235">기본값은 3입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-235">Default value is 3.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-236">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-236">Return Values</span></span>

- <span data-ttu-id="a6906-237">**NX_SUCCESS** (0x00) 타이밍 값을 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-237">**NX_SUCCESS** (0x00) Successfully sets the timing values.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-238">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-238">Allowed From</span></span>

<span data-ttu-id="a6906-239">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-240">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-240">Example</span></span>

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a><span data-ttu-id="a6906-241">nx_mdns_service_add</span><span class="sxs-lookup"><span data-stu-id="a6906-241">nx_mdns_service_add</span></span>

<span data-ttu-id="a6906-242">로컬 서비스 추가</span><span class="sxs-lookup"><span data-stu-id="a6906-242">Add a local service</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-243">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-243">Prototype</span></span>

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="a6906-244">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-244">Description</span></span>

<span data-ttu-id="a6906-245">이 API는 애플리케이션에서 제공하는 서비스를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-245">This API registers a service offered by the application.</span></span> <span data-ttu-id="a6906-246">*is_unique* 플래그를 설정하면 mDNS가 네트워크에서 서비스를 알리기 전에 로컬 네트워크에서 서비스 이름을 검색하여 고유한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-246">If the flag *is_unique* is set, mDNS probes the service name to make sure it is unique on the local network before starting to announce the service on the network.</span></span> <span data-ttu-id="a6906-247">*Instance* 는 서비스 이름의 인스턴스 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-247">*Instance* is the instance portion of the service name.</span></span> <span data-ttu-id="a6906-248">*service* 는 서비스 이름의 서비스 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-248">The *service* is the service portion of the service name.</span></span> <span data-ttu-id="a6906-249">예를 들어 "_http._tcp"는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-249">For example “_http._tcp” is a service.</span></span> <span data-ttu-id="a6906-250">하위 유형으로 서비스를 설명하려면 호출자가 *subtype* 매개 변수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-250">To describe a service with subtype, caller must use the *subtype* parameter.</span></span> <span data-ttu-id="a6906-251">예를 들어 원하는 서비스가 “_printer._sub._http._tcp”이면 서비스 필드는 “_http._tcp:”이고, 하위 유형 필드는 “_printer”입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-251">For example, if the desired service is “_printer._sub._http._tcp”, the service field is “_http._tcp:, and the subtype field is “_printer”.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-252">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-252">Input Parameters</span></span>

- <span data-ttu-id="a6906-253">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-253">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-254">**instance** 서비스의 인스턴스 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-254">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="a6906-255">**service** 하위 유형 정보를 제외한 mDNS 서비스 유형에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-255">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="a6906-256">**subtype** mDNS 서비스의 하위 유형 부분에 대한 포인터입니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a6906-256">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="a6906-257">**priority** 서비스 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-257">**priority** Service priority</span></span>
- <span data-ttu-id="a6906-258">**weight** 서비스 가중치입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-258">**weight** Service weight</span></span>
- <span data-ttu-id="a6906-259">**port** 서비스에서 사용하는 TCP 또는 UDP 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-259">**port** TCP or UDP port number the service uses</span></span>
- <span data-ttu-id="a6906-260">**text** 추가 텍스트 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-260">**text** Additional text information</span></span>
- <span data-ttu-id="a6906-261">**is_unique** 서비스가 공유되는지, 고유한지를 나타내는 부울 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-261">**is_unique** Boolean flag indicating whether the service is shared or unique.</span></span> <span data-ttu-id="a6906-262">고유한 것으로 등록된 서비스의 경우 mDNS가 서비스를 제공하기 전에 네트워크에서 서비스를 검색해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-262">For services registered as unique, mDNS must probe the service on the network before starting offering it.</span></span>
- <span data-ttu-id="a6906-263">**Interface_index** 서비스가 제공되는 실제 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-263">**Interface_index** Physical interface the service is offered through.</span></span> <span data-ttu-id="a6906-264">연결된 서비스를 통해 제공되는 서비스의 경우 *NX_MDNS_ALL_INTERFACES* 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-264">For a service that is offered through any of the attached services, the value *NX_MDNS_ALL_INTERFACES* is used.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-265">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-265">Return Values</span></span>

- <span data-ttu-id="a6906-266">**NX_SUCCESS** (0x00) 서비스를 성공적으로 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-266">**NX_SUCCESS** (0x00) Successfully registered the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-267">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-267">Allowed From</span></span>

<span data-ttu-id="a6906-268">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-269">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-269">Example</span></span>

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a><span data-ttu-id="a6906-270">nx_mdns_service_delete</span><span class="sxs-lookup"><span data-stu-id="a6906-270">nx_mdns_service_delete</span></span>

<span data-ttu-id="a6906-271">이전에 등록된 서비스 제거</span><span class="sxs-lookup"><span data-stu-id="a6906-271">Remove a previous registered service</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-272">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-272">Prototype</span></span>

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="a6906-273">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-273">Description</span></span>

<span data-ttu-id="a6906-274">이 API는 이전에 등록된 서비스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-274">This API deletes a previous registered service.</span></span> <span data-ttu-id="a6906-275">서비스가 삭제되면 "종료" 메시지가 로컬 네트워크로 전송되어 인접 노드에 알림이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-275">As the service is deleted, "goodbye" messages are sent to the local network so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-276">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-276">Input Parameters</span></span>

- <span data-ttu-id="a6906-277">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-277">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-278">**instance** 서비스의 인스턴스 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-278">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="a6906-279">**service** 하위 유형 정보를 제외한 mDNS 서비스 유형에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-279">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="a6906-280">**subtype** mDNS 서비스의 하위 유형 부분에 대한 포인터입니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a6906-280">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-281">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-281">Return Values</span></span>

- <span data-ttu-id="a6906-282">**NX_SUCCESS** (0x00) 서비스를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-282">**NX_SUCCESS** (0x00) Successfully deleted the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-283">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-283">Allowed From</span></span>

<span data-ttu-id="a6906-284">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-285">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-285">Example</span></span>

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a><span data-ttu-id="a6906-286">nx_mdns_service_one_shot_query</span><span class="sxs-lookup"><span data-stu-id="a6906-286">nx_mdns_service_one_shot_query</span></span>

<span data-ttu-id="a6906-287">원샷 서비스 검색 시작</span><span class="sxs-lookup"><span data-stu-id="a6906-287">Initiate one-shot service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-288">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-288">Prototype</span></span>

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a6906-289">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-289">Description</span></span>

<span data-ttu-id="a6906-290">이 서비스는 원샷 mDNS 쿼리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-290">This service performs a one-shot mDNS query.</span></span> <span data-ttu-id="a6906-291">지정된 서비스가 피어 서비스 캐시에서 발견되면 첫 번째 인스턴스가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-291">If the specified service is found in the peer service cache, the first instance is returned.</span></span> <span data-ttu-id="a6906-292">로컬 피어 서비스 캐시에서 서비스를 찾을 수 없는 경우 mDNS 모듈은 쿼리 명령을 실행하고 응답을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-292">If no services are found in the local peer service cache, the mDNS module issues a query command and wait for response.</span></span> <span data-ttu-id="a6906-293">첫 번째 응답이 수신되거나 쿼리 시간이 초과될 때까지 서비스가 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-293">The service is blocked till either the first answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-294">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-294">Input Parameters</span></span>

- <span data-ttu-id="a6906-295">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-295">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-296">**instance** 서비스의 인스턴스 이름에 대한 포인터입니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a6906-296">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="a6906-297">**service** 하위 유형 정보를 제외한 mDNS 서비스 유형에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-297">**service** Pointer to the mDNS service type, excluding subtype information.</span></span> <span data-ttu-id="a6906-298">애플리케이션이 서비스 유형을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-298">the application must specify the service type.</span></span>
- <span data-ttu-id="a6906-299">**subtype** mDNS 서비스의 하위 유형 부분에 대한 포인터입니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a6906-299">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="a6906-300">**service_ptr** 쿼리 결과를 저장하는 NX_MDNS_SERVICE 구조체에 대한 사용자 제공 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-300">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the query results.</span></span>
- <span data-ttu-id="a6906-301">**wait_option** 응답을 기다리는 시간(틱)입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-301">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-302">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-302">Return Values</span></span>

- <span data-ttu-id="a6906-303">**NX_SUCCESS** (0x00) 서비스 정보를 성공적으로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-303">**NX_SUCCESS** (0x00) Successfully obtained service information.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-304">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-304">Allowed From</span></span>

<span data-ttu-id="a6906-305">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-305">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-306">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-306">Example</span></span>

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a><span data-ttu-id="a6906-307">nx_mdns_service_continuous_query</span><span class="sxs-lookup"><span data-stu-id="a6906-307">nx_mdns_service_continuous_query</span></span>

<span data-ttu-id="a6906-308">연속 서비스 검색 시작</span><span class="sxs-lookup"><span data-stu-id="a6906-308">Initiate continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-309">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-309">Prototype</span></span>

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="a6906-310">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-310">Description</span></span>

<span data-ttu-id="a6906-311">이 서비스는 연속 쿼리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-311">This service starts a continuous query.</span></span> <span data-ttu-id="a6906-312">서비스는 즉시 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-312">Note that the service returns immediately.</span></span> <span data-ttu-id="a6906-313">연속 쿼리를 실행하면 애플리케이션이 API *nx_mdns_service_lookup* 을 사용하여 서비스 레코드를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-313">After issuing a continuous query, the application may retrieve service record by using the API *nx_mdns_service_lookup*.</span></span> <span data-ttu-id="a6906-314">애플리케이션은 연속 쿼리를 중지할 때 API *nx_mdns_service_query_stop* 을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-314">To stop the continuous query, the application may use the API *nx_mdns_service_query_stop*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-315">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-315">Input Parameters</span></span>

- <span data-ttu-id="a6906-316">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-316">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-317">**instance** 서비스의 인스턴스 이름에 대한 포인터입니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a6906-317">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="a6906-318">**service** 하위 유형 정보를 제외한 mDNS 서비스 유형에 대한 포인터입니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a6906-318">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="a6906-319">**subtype** mDNS 서비스의 하위 유형 부분에 대한 포인터입니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a6906-319">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-320">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-320">Return Values</span></span>

- <span data-ttu-id="a6906-321">**NX_SUCCESS** (0x00) 연속 쿼리를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-321">**NX_SUCCESS** (0x00) Successfully started continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-322">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-322">Allowed From</span></span>

<span data-ttu-id="a6906-323">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-323">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-324">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-324">Example</span></span>

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a><span data-ttu-id="a6906-325">nx_mdns_service_query_stop</span><span class="sxs-lookup"><span data-stu-id="a6906-325">nx_mdns_service_query_stop</span></span>

<span data-ttu-id="a6906-326">이전에 실행된 연속 서비스 검색 중단</span><span class="sxs-lookup"><span data-stu-id="a6906-326">Cease a previously issued continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-327">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-327">Prototype</span></span>

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="a6906-328">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-328">Description</span></span>

<span data-ttu-id="a6906-329">이 API는 이전에 실행된 연속 서비스 검색을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-329">This API terminates a previous issued continuous service discovery.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-330">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-330">Input Parameters</span></span>

- <span data-ttu-id="a6906-331">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-331">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-332">**instance** 서비스의 인스턴스 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-332">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="a6906-333">**service** 하위 유형 정보를 제외한 mDNS 서비스 유형에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-333">**service** Pointer to the mDNS service type, subtype information.</span></span>
- <span data-ttu-id="a6906-334">**subtype** mDNS 서비스의 하위 유형 부분에 대한 포인터입니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a6906-334">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-335">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-335">Return Values</span></span>

- <span data-ttu-id="a6906-336">**NX_SUCCESS** (0x00) 연속 쿼리를 성공적으로 중지했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-336">**NX_SUCCESS** (0x00) Successfully stopped continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-337">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-337">Allowed From</span></span>

<span data-ttu-id="a6906-338">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-338">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-339">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-339">Example</span></span>

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a><span data-ttu-id="a6906-340">nx_mdns_service_lookup</span><span class="sxs-lookup"><span data-stu-id="a6906-340">nx_mdns_service_lookup</span></span>

<span data-ttu-id="a6906-341">로컬 피어 서비스 캐시에서 서비스 검색</span><span class="sxs-lookup"><span data-stu-id="a6906-341">Retrieves the service from the local peer service cache</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-342">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-342">Prototype</span></span>

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a><span data-ttu-id="a6906-343">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-343">Description</span></span>

<span data-ttu-id="a6906-344">이 서비스는 로컬 피어 서비스 캐시에서 인스턴스 이름(제공된 경우) 및 서비스 유형과 일치하는 서비스를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-344">This service looks up services matching the instance name (if provided) and the type of service in the local peer service cache.</span></span> <span data-ttu-id="a6906-345">애플리케이션은 캐시에서 설명과 일치하는 첫 번째 서비스를 찾기 위해 0으로 설정된 *instance_index* 를 사용하여 서비스 조회를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-345">Application shall start the service lookup with *instance_index* set to zero for the first service in the cache that matches the description.</span></span> <span data-ttu-id="a6906-346">서비스가 캐시의 끝을 나타내는 *NX_NO_MORE_ENTRIES* 를 반환할 때까지, 애플리케이션은 캐시에서 추가 서비스를 검색할 때마다 *instance_index* 값을 늘려 가면서 이 서비스를 계속 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-346">Application shall keep using this service with increasing *instance_index* value for additional services found in the cache, till the service returns *NX_NO_MORE_ENTRIES*, which indicates the end of the cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-347">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-347">Input Parameters</span></span>

- <span data-ttu-id="a6906-348">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-348">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-349">**instance** 서비스의 인스턴스 이름에 대한 포인터입니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a6906-349">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="a6906-350">**service** 하위 유형 정보를 제외한 mDNS 서비스 유형에 대한 포인터입니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a6906-350">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="a6906-351">**subtype** mDNS 서비스의 하위 유형 부분에 대한 포인터입니다(해당하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a6906-351">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="a6906-352">**Instance_index** 반환할 인스턴스의 인덱스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-352">**Instance_index** Index number to the instance to be returned.</span></span>
- <span data-ttu-id="a6906-353">**service_ptr** 조회 결과를 저장하는 NX_MDNS_SERVICE 구조체에 대한 사용자 제공 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-353">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the lookup results.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-354">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-354">Return Values</span></span>

- <span data-ttu-id="a6906-355">**NX_SUCCESS** (0x00) 서비스를 성공적으로 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-355">**NX_SUCCESS** (0x00) Successfully retrieved the service</span></span>
- <span data-ttu-id="a6906-356">**NX_NO_MORE_ENTRIES** (0x17) 지정된 인덱스 번호에서 서비스 항목을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-356">**NX_NO_MORE_ENTRIES** (0x17) No service entry is found at the specified index number.</span></span> <span data-ttu-id="a6906-357">이 오류 코드는 검색의 끝을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-357">This error code indicates the end of the search.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-358">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-358">Allowed From</span></span>

<span data-ttu-id="a6906-359">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-360">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-360">Example</span></span>

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a><span data-ttu-id="a6906-361">nx_mdns_service_ignore_set</span><span class="sxs-lookup"><span data-stu-id="a6906-361">nx_mdns_service_ignore_set</span></span>

<span data-ttu-id="a6906-362">서비스 무시 집합 구성</span><span class="sxs-lookup"><span data-stu-id="a6906-362">Configures a service ignore set</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-363">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-363">Prototype</span></span>

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a><span data-ttu-id="a6906-364">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-364">Description</span></span>

<span data-ttu-id="a6906-365">이 API는 *service_mask* 비트 마스크로 지정된 서비스를 무시하도록 마스크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-365">This API configures a mask to ignore services specified by the *service_mask* bitmask.</span></span> <span data-ttu-id="a6906-366">사용자는 필요에 따라 service_mask를 사용하여 캐시하지 않으려는 서비스 유형을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-366">User may optionally use the service_mask to select service types it does not wish to be cached.</span></span> <span data-ttu-id="a6906-367">서비스 목록은 *nxd_mdns.c* 의 *nx_mdns_service_types* 테이블에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-367">A list of services is defined in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span> <span data-ttu-id="a6906-368">nx_mdns_service_types[]에서 첫 번째 서비스 형식의 해당 마스크는 0x00000001이고, 두 번째 서비스 형식의 마스크는 0x00000002인 식입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-368">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-369">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-369">Input Parameters</span></span>

- <span data-ttu-id="a6906-370">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-370">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-371">**service_mask** 무시할 사용자 정의 서비스 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-371">**service_mask** User-defined service types to ignore.</span></span> <span data-ttu-id="a6906-372">마스크는 32비트 ULONG 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-372">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="a6906-373">각 비트는 사용자 정의 *nx_mdns_service_types* 배열의 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-373">Each bit represents an entry in the user-defined *nx_mdns_service_types* array.</span></span> <span data-ttu-id="a6906-374">비트가 설정되면 *nx_mdns_service_type* 배열에 지정된 해당 서비스 형식이 피어 서비스 캐시에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-374">If a bit is set, the corresponding service type specified in the *nx_mdns_service_type* array will not store in the peer service cache.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-375">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-375">Return Values</span></span>

- <span data-ttu-id="a6906-376">**NX_SUCCESS** (0x00) 서비스 무시 마스크를 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-376">**NX_SUCCESS** (0x00) Successfully sets the service ignore mask.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-377">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-377">Allowed From</span></span>

<span data-ttu-id="a6906-378">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-378">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-379">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-379">Example</span></span>

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a><span data-ttu-id="a6906-380">nx_mdns_service_notify_set</span><span class="sxs-lookup"><span data-stu-id="a6906-380">nx_mdns_service_notify_set</span></span>

<span data-ttu-id="a6906-381">서비스 변경 알림 콜백 함수 구성</span><span class="sxs-lookup"><span data-stu-id="a6906-381">Configures a service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-382">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-382">Prototype</span></span>

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a><span data-ttu-id="a6906-383">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-383">Description</span></span>

<span data-ttu-id="a6906-384">이 API는 서비스 변경 알림 콜백 함수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-384">This API configures a service change notify callback function.</span></span> <span data-ttu-id="a6906-385">이 콜백 함수는 네트워크의 다른 노드에서 제공하는 서비스가 추가, 변경되거나 더 이상 사용할 수 없을 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-385">This callback function is invoked when a service offered by other nodes on the network is added, changed or is no longer available.</span></span> <span data-ttu-id="a6906-386">사용자는 필요에 따라 service_mask를 사용하여 모니터링하려는 서비스 유형을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-386">User may optionally use the service_mask to select service types it wishes to monitor.</span></span> <span data-ttu-id="a6906-387">모니터링되는 서비스 목록은 *nxd_mdns.c* 의 *nx_mdns_service_types* 테이블에 하드 코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-387">A list of services being monitored are hard-coded in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span>

<span data-ttu-id="a6906-388">nx_mdns_service_types[]에서 첫 번째 서비스 형식의 해당 마스크는 0x00000001이고, 두 번째 서비스 형식의 마스크는 0x00000002인 식입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-388">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-389">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-389">Input Parameters</span></span>

- <span data-ttu-id="a6906-390">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-390">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-391">**service_mask** 모니터링할 사용자 정의 서비스 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-391">**service_mask** User-defined service types to monitor.</span></span> <span data-ttu-id="a6906-392">마스크는 32비트 ULONG 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-392">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="a6906-393">각 비트는 *nx_mdns_service_types* 배열의 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-393">Each bit represents an entry in the *nx_mdns_service_types* array.</span></span>
- <span data-ttu-id="a6906-394">**service_change_notify** 지정된 서비스가 변경될 때 호출되는 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-394">**service_change_notify** The callback function to be invoked when the specified service is changed.</span></span> <span data-ttu-id="a6906-395">자세한 서비스 정보는 *service_ptr* 이 가리키는 메모리에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-395">The detailed service information is returned in the memory pointed to by *service_ptr.*</span></span> <span data-ttu-id="a6906-396">알림 콜백 함수에서 반환된 메모리의 콘텐츠는 더 이상 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-396">Note that the content in the memory is invalid after returning from the notify callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-397">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-397">Return Values</span></span>

- <span data-ttu-id="a6906-398">**NX_SUCCESS** (0x00) 콜백 함수를 성공적으로 설치했습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-398">**NX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-399">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-399">Allowed From</span></span>

<span data-ttu-id="a6906-400">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-401">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-401">Example</span></span>

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a><span data-ttu-id="a6906-402">nx_mdns_service_notify_clear</span><span class="sxs-lookup"><span data-stu-id="a6906-402">nx_mdns_service_notify_clear</span></span>

<span data-ttu-id="a6906-403">서비스 변경 알림 콜백 함수 지우기</span><span class="sxs-lookup"><span data-stu-id="a6906-403">Clear the service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-404">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-404">Prototype</span></span>

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="a6906-405">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-405">Description</span></span>

<span data-ttu-id="a6906-406">이 API는 서비스 변경 알림 콜백 함수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-406">This API clears the service change notify callback function and the .</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-407">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-407">Input Parameters</span></span>

- <span data-ttu-id="a6906-408">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-408">**mdns_ptr** Pointer to mDNS control block..</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-409">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-409">Return Values</span></span>

- <span data-ttu-id="a6906-410">**NX_SUCCESS** (0x00) 콜백 함수를 성공적으로 지웠습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-410">**NX_SUCCESS** (0x00) Successfully cleared the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-411">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-411">Allowed From</span></span>

<span data-ttu-id="a6906-412">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-413">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-413">Example</span></span>

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a><span data-ttu-id="a6906-414">nx_mdns_host_address_get</span><span class="sxs-lookup"><span data-stu-id="a6906-414">nx_mdns_host_address_get</span></span>

<span data-ttu-id="a6906-415">호스트 주소 가져오기</span><span class="sxs-lookup"><span data-stu-id="a6906-415">Get the host address</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-416">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-416">Prototype</span></span>

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a6906-417">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-417">Description</span></span>

<span data-ttu-id="a6906-418">이 서비스는 호스트 IPv4 및 IPv6 주소에 대한 mDNS 쿼리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-418">This service performs a mDNS query on host IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="a6906-419">지정된 호스트 이름의 주소가 피어 서비스 캐시에 있으면 주소가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-419">If the address of specified host name is found in peer service cache, the address is returned.</span></span> <span data-ttu-id="a6906-420">피어 서비스 캐시에서 주소를 찾을 수 없는 경우 mDNS 모듈은 A 및 AAAA 형식 쿼리를 실행하고 응답을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-420">If no address is found in the peer service cache, the mDNS module issues A and AAAA type queries and wait for response.</span></span> <span data-ttu-id="a6906-421">이 API는 응답이 수신되거나 쿼리 시간이 초과될 때까지 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-421">This API blocks until either an answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-422">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-422">Input Parameters</span></span>

- <span data-ttu-id="a6906-423">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-423">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="a6906-424">**host_name** 호스트 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-424">**host_name** Pointer to host name.</span></span>
- <span data-ttu-id="a6906-425">**ipv4_address** IPv4 주소 스토리지 공간의 4바이트 정렬 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-425">**ipv4_address** Pointer to a 4-byte aligned address for IPv4 address storage space.</span></span> <span data-ttu-id="a6906-426">사용자는 IPv4 주소에 대해 4바이트의 공간을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-426">User shall allocate 4 bytes of space for the IPv4 - address.</span></span> <span data-ttu-id="a6906-427">애플리케이션에서 IPv4 주소를 검색할 필요가 없는 경우 NX_NULL 주소를 이 API에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-427">NX_NULL address can be passed into this API if application does not need to retrieve IPv4 address.</span></span>
- <span data-ttu-id="a6906-428">**ipv6_address** IPv6 주소 스토리지 공간의 4바이트 정렬 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-428">**ipv6_address** Pointer to the 4-byte aligned address for IPv6 address storage space.</span></span> <span data-ttu-id="a6906-429">사용자는 IPv6 주소에 대해 16바이트의 공간을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-429">User shall allocate 16 bytes of space for the - IPv6 address.</span></span> <span data-ttu-id="a6906-430">애플리케이션에서 IPv6 주소를 검색할 필요가 없는 경우 NX_NULL 주소를 이 API에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-430">NX_NULL address can be passed into this API if application does not need to retrieve IPv6 address.</span></span>
- <span data-ttu-id="a6906-431">**wait_option** 응답을 기다리는 시간(틱)입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-431">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-432">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-432">Return Values</span></span>

- <span data-ttu-id="a6906-433">**NX_SUCCESS** (0x00) 호스트 주소를 성공적으로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-433">**NX_SUCCESS** (0x00) Successfully obtained host address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-434">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-434">Allowed From</span></span>

<span data-ttu-id="a6906-435">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-436">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-436">Example</span></span>

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a><span data-ttu-id="a6906-437">nx_mdns_local_cache_clear</span><span class="sxs-lookup"><span data-stu-id="a6906-437">nx_mdns_local_cache_clear</span></span>

<span data-ttu-id="a6906-438">모든 로컬 서비스 지우기</span><span class="sxs-lookup"><span data-stu-id="a6906-438">Erase all local services</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-439">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-439">Prototype</span></span>

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="a6906-440">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-440">Description</span></span>

<span data-ttu-id="a6906-441">이 서비스는 종료 메시지를 보낸 후 로컬 서비스 캐시에서 모든 항목을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-441">This service clears all entries in the local service cache after send the Goodbye message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-442">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-442">Input Parameters</span></span>

- <span data-ttu-id="a6906-443">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-443">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-444">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-444">Return Values</span></span>

- <span data-ttu-id="a6906-445">**NX_SUCCESS** (0x00) 캐시의 모든 항목을 성공적으로 지웠습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-445">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-446">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-446">Allowed From</span></span>

<span data-ttu-id="a6906-447">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-447">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-448">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-448">Example</span></span>

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a><span data-ttu-id="a6906-449">nx_mdns_peer_cache_clear</span><span class="sxs-lookup"><span data-stu-id="a6906-449">nx_mdns_peer_cache_clear</span></span>

<span data-ttu-id="a6906-450">검색된 모든 서비스 지우기</span><span class="sxs-lookup"><span data-stu-id="a6906-450">Erase all the discovered services</span></span>

### <a name="prototype"></a><span data-ttu-id="a6906-451">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a6906-451">Prototype</span></span>

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="a6906-452">Description</span><span class="sxs-lookup"><span data-stu-id="a6906-452">Description</span></span>

<span data-ttu-id="a6906-453">이 서비스는 피어 서비스 캐시의 모든 항목을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-453">This service clears all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a6906-454">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a6906-454">Input Parameters</span></span>

- <span data-ttu-id="a6906-455">**mdns_ptr** mDNS 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-455">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a6906-456">반환 값</span><span class="sxs-lookup"><span data-stu-id="a6906-456">Return Values</span></span>

- <span data-ttu-id="a6906-457">**NX_SUCCESS** (0x00) 캐시의 모든 항목을 성공적으로 지웠습니다.</span><span class="sxs-lookup"><span data-stu-id="a6906-457">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a6906-458">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="a6906-458">Allowed From</span></span>

<span data-ttu-id="a6906-459">스레드</span><span class="sxs-lookup"><span data-stu-id="a6906-459">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a6906-460">예제</span><span class="sxs-lookup"><span data-stu-id="a6906-460">Example</span></span>

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
