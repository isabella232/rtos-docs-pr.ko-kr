---
title: 3장 - Azure RTOS NetX PPPoE 서버 서비스 설명
description: 이 장에서는 아래에 나열된 모든 Azure RTOS NetX PPPoE 서버 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811418"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a><span data-ttu-id="8638f-103">3장 - Azure RTOS NetX PPPoE 서버 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="8638f-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Server Services</span></span>

<span data-ttu-id="8638f-104">이 장에서는 아래에 나열된 모든 Azure RTOS NetX PPPoE 서버 서비스에 대해 알파벳 순서로 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-104">This chapter contains a description of all Azure RTOS NetX PPPoE Server services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="8638f-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="8638f-106">**nx_pppoe_server_create**: *PPPoE 서버 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="8638f-106">**nx_pppoe_server_create**: *Create a PPPoE Server instance*</span></span>

- <span data-ttu-id="8638f-107">**nx_pppoe_server_ac_name_set**: *액세스 집중 장치 이름 설정*</span><span class="sxs-lookup"><span data-stu-id="8638f-107">**nx_pppoe_server_ac_name_set**: *Set Access Concentrator name*</span></span>

- <span data-ttu-id="8638f-108">**nx_pppoe_server_delete**: *PPPoE 서버 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="8638f-108">**nx_pppoe_server_delete**: *Delete a PPPoE Server instance*</span></span>

- <span data-ttu-id="8638f-109">**nx_pppoe_server_enable**: *PPPoE 서버 서비스를 사용하도록 설정*</span><span class="sxs-lookup"><span data-stu-id="8638f-109">**nx_pppoe_server_enable**: *Enable PPPoE Server services*</span></span>

- <span data-ttu-id="8638f-110">**nx_pppoe_server_disable**: *PPPoE 서버 서비스를 사용하지 않도록 설정*</span><span class="sxs-lookup"><span data-stu-id="8638f-110">**nx_pppoe_server_disable**: *Disable PPPoE Server services*</span></span>

- <span data-ttu-id="8638f-111">**nx_pppoe_server_callback_notify_set**: *PPPoE 서버 콜백 알림 함수 설정*</span><span class="sxs-lookup"><span data-stu-id="8638f-111">**nx_pppoe_server_callback_notify_set**: *Set PPPoE Server callback notify functions*</span></span>

- <span data-ttu-id="8638f-112">**nx_pppoe_server_service_name_set**: *PPPoE 서버 서비스 이름 설정*</span><span class="sxs-lookup"><span data-stu-id="8638f-112">**nx_pppoe_server_service_name_set**: *Set PPPoE Server service name*</span></span>

- <span data-ttu-id="8638f-113">**nx_pppoe_server_session_send**: *지정 된 세션에 PPPoE 서버 데이터 보내기*</span><span class="sxs-lookup"><span data-stu-id="8638f-113">**nx_pppoe_server_session_send**: *Send PPPoE Server data to specified session*</span></span>

- <span data-ttu-id="8638f-114">**nx_pppoe_server_session_packet_send**: *지정된 세션에 PPPoE 서버 패킷 보내기*</span><span class="sxs-lookup"><span data-stu-id="8638f-114">**nx_pppoe_server_session_packet_send**: *Send PPPoE Server packet to specified session*</span></span>

- <span data-ttu-id="8638f-115">**nx_pppoe_server_session_terminate**: *지정된 PPPoE 세션 종료*</span><span class="sxs-lookup"><span data-stu-id="8638f-115">**nx_pppoe_server_session_terminate**: *Terminate the specified PPPoE session*</span></span>

- <span data-ttu-id="8638f-116">**nx_pppoe_server_session_get**: *지정된 세션 정보 가져오기*</span><span class="sxs-lookup"><span data-stu-id="8638f-116">**nx_pppoe_server_session_get**: *Get the specified session information*</span></span>

## <a name="nx_pppoe_server_create"></a><span data-ttu-id="8638f-117">nx_pppoe_server_create</span><span class="sxs-lookup"><span data-stu-id="8638f-117">nx_pppoe_server_create</span></span>

<span data-ttu-id="8638f-118">PPPoE 서버 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="8638f-118">Create a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-119">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-119">Prototype</span></span>

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a><span data-ttu-id="8638f-120">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-120">Description</span></span>

<span data-ttu-id="8638f-121">이 서비스는 지정된 NetX IP 인스턴스에 대한 사용자 입력 링크 드라이버를 통해 PPPoE 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-121">This service creates a PPPoE Server instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="8638f-122">링크 드라이버가 초기화되지 않고 사용하도록 설정된 경우 PPPoE 서버 소프트웨어는 링크 드라이버를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-122">If link driver has not been initialized, and enabled, PPPoE sever software is responsible initializing the link driver.</span></span>

<span data-ttu-id="8638f-123">또한 애플리케이션은 내부 패킷 할당에 사용할 PPPoE 서버 인스턴스에 대해 이전에 만든 패킷 풀을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-123">In addition, the application must supply a previously created packet pool for the PPPoE Server instance to use for internal packet allocation.</span></span>

<span data-ttu-id="8638f-124">일반적으로는 PPPoE 서버 스레드 우선 순위보다 우선 순위가 높은 NetX IP 스레드를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-124">Note that it is generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Server thread priority.</span></span> <span data-ttu-id="8638f-125">IP 스레드 우선 순위를 지정하는 방법에 대한 자세한 내용은 *nx_ip_create* 서비스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8638f-125">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-126">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-126">Input Parameters</span></span>

- <span data-ttu-id="8638f-127">**pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-127">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="8638f-128">**name**: 이 PPPoE 서버 인스턴스의 이름</span><span class="sxs-lookup"><span data-stu-id="8638f-128">**name**: Name of this PPPoE Server instance.</span></span>
- <span data-ttu-id="8638f-129">**ip_ptr**: IP 인스턴스용 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-129">**ip_ptr**: Pointer to control block for IP instance.</span></span>
- <span data-ttu-id="8638f-130">**interface_index**: 인터페이스 인덱스</span><span class="sxs-lookup"><span data-stu-id="8638f-130">**interface_index**: Interface index.</span></span>
- <span data-ttu-id="8638f-131">**pppoe_link_driver** 사용자가 제공한 링크 드라이버</span><span class="sxs-lookup"><span data-stu-id="8638f-131">**pppoe_link_driver**: User supplied link driver.</span></span>
- <span data-ttu-id="8638f-132">**pool_ptr**: 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-132">**pool_ptr**: Pointer to packet pool.</span></span>
- <span data-ttu-id="8638f-133">**stack_ptr**: PPPoE 서버 스레드의 스택 영역 시작 부분에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-133">**stack_ptr**: Pointer to start of PPPoE Server thread's stack area.</span></span>
- <span data-ttu-id="8638f-134">**stack_size**: 스레드 스택의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="8638f-134">**stack_size**: Size in bytes in the thread's stack.</span></span>
- <span data-ttu-id="8638f-135">**priority**: 내부 PPPoE 서버 인스턴스의 우선 순위(1-31)</span><span class="sxs-lookup"><span data-stu-id="8638f-135">**priority**: Priority of internal PPPoE Server threads (1-31).</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-136">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-136">Return Values</span></span>

- <span data-ttu-id="8638f-137">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 만들기 성공</span><span class="sxs-lookup"><span data-stu-id="8638f-137">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server create.</span></span>
- <span data-ttu-id="8638f-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버, IP, 패킷 풀 또는 스택 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="8638f-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) 잘못된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8638f-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Invalid interface.</span></span>
- <span data-ttu-id="8638f-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) 잘못된 패킷 풀 페이로드 크기</span><span class="sxs-lookup"><span data-stu-id="8638f-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid payload size of packet pool.</span></span>
- <span data-ttu-id="8638f-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) 잘못된 메모리 크기</span><span class="sxs-lookup"><span data-stu-id="8638f-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Invalid memory size.</span></span>
- <span data-ttu-id="8638f-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) 잘못된 PPPoE 서버 스레드 우선 순위</span><span class="sxs-lookup"><span data-stu-id="8638f-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) Invalid priority of PPPoE Server thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-143">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-143">Allowed From</span></span>

<span data-ttu-id="8638f-144">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-145">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-145">Example</span></span>

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a><span data-ttu-id="8638f-146">nx_pppoe_server_delete</span><span class="sxs-lookup"><span data-stu-id="8638f-146">nx_pppoe_server_delete</span></span>

<span data-ttu-id="8638f-147">PPPoE 서버 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="8638f-147">Delete a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-148">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-148">Prototype</span></span>

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="8638f-149">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-149">Description</span></span>

<span data-ttu-id="8638f-150">이 서비스는 이전에 만든 PPPoE 서버 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-150">This service deletes the previously created PPPoE Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-151">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-151">Input Parameters</span></span>

- <span data-ttu-id="8638f-152">**pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-152">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-153">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-153">Return Values</span></span>

- <span data-ttu-id="8638f-154">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공</span><span class="sxs-lookup"><span data-stu-id="8638f-154">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="8638f-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-156">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-156">Allowed From</span></span>

<span data-ttu-id="8638f-157">스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-158">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-158">Example</span></span>

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a><span data-ttu-id="8638f-159">nx_pppoe_server_enable</span><span class="sxs-lookup"><span data-stu-id="8638f-159">nx_pppoe_server_enable</span></span>

<span data-ttu-id="8638f-160">PPPoE 서버 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="8638f-160">Enable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-161">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-161">Prototype</span></span>

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="8638f-162">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-162">Description</span></span>

<span data-ttu-id="8638f-163">이 서비스는 PPPoE 서버 서비스를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-163">This service enables the PPPoE Server services.</span></span>

> [!NOTE]
> <span data-ttu-id="8638f-164">이 함수는 *nx_pppoe_server_create* 및 *nx_pppoe_server_callback_notify_set* 다음에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-164">This function must be called after *nx_pppoe_server_create* and *nx_pppoe_server_callback_notify_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-165">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-165">Input Parameters</span></span>

- <span data-ttu-id="8638f-166">**pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-166">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-167">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-167">Return Values</span></span>

- <span data-ttu-id="8638f-168">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공</span><span class="sxs-lookup"><span data-stu-id="8638f-168">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="8638f-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-170">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-170">Allowed From</span></span>

<span data-ttu-id="8638f-171">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-171">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-172">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-172">Example</span></span>

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a><span data-ttu-id="8638f-173">nx_pppoe_server_disable</span><span class="sxs-lookup"><span data-stu-id="8638f-173">nx_pppoe_server_disable</span></span>

<span data-ttu-id="8638f-174">PPPoE 서버 서비스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="8638f-174">Disable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-175">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-175">Prototype</span></span>

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="8638f-176">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-176">Description</span></span>

<span data-ttu-id="8638f-177">이 서비스는 PPPoE 서버 서비스를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-177">This service disables the PPPoE Server services.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-178">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-178">Input Parameters</span></span>

- <span data-ttu-id="8638f-179">**pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-179">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-180">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-180">Return Values</span></span>

- <span data-ttu-id="8638f-181">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공</span><span class="sxs-lookup"><span data-stu-id="8638f-181">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="8638f-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-183">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-183">Allowed From</span></span>

<span data-ttu-id="8638f-184">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-184">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-185">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-185">Example</span></span>

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a><span data-ttu-id="8638f-186">nx_pppoe_server_callback_notify_set</span><span class="sxs-lookup"><span data-stu-id="8638f-186">nx_pppoe_server_callback_notify_set</span></span>

<span data-ttu-id="8638f-187">PPPoE 서버 콜백 알림 함수 설정</span><span class="sxs-lookup"><span data-stu-id="8638f-187">Set PPPoE Server callback notify functions</span></span> 

### <a name="prototype"></a><span data-ttu-id="8638f-188">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-188">Prototype</span></span>

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a><span data-ttu-id="8638f-189">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-189">Description</span></span>

<span data-ttu-id="8638f-190">이 서비스는 PPPoE 서버 콜백 알림 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-190">This service sets PPPoE Server callback notify functions.</span></span>

> [!NOTE]
> <span data-ttu-id="8638f-191">이 함수는 *nx_pppoe_server_enabl 및* pppoe_data_receive_notify 함수 포인터가 설정되기 전에 호출해야 하며, 그렇지 않으면 *nx_pppoe_server_enable* 이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-191">This function must be called before *nx_pppoe_server_enabl, and* the pppoe_data_receive_notify function pointer must be set, if not, *nx_pppoe_server_enable* will be failure.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-192">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-192">Input Parameters</span></span>

- <span data-ttu-id="8638f-193">**pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-193">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="8638f-194">**pppoe_discover_initiation_notify**: PPPoE 검색 시작 메시지를 받을 때마다 호출되는 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-194">**pppoe_discover_initiation_notify**: Application function that is called whenever PPPoE discover initiation message is received.</span></span> <span data-ttu-id="8638f-195">이 값이 NULL 인 경우 검색 시작 콜백 함수를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-195">If this value is NULL, discover initiation callback function is disabled.</span></span>
- <span data-ttu-id="8638f-196">**pppoe_discover_request_notify**: PPPoE 검색 요청 메시지를 받을 때마다 호출되는 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-196">**pppoe_discover_request_notify**: Application function that is called whenever PPPoE discover request message is received.</span></span> <span data-ttu-id="8638f-197">이 값이 NULL인 경우 검색 요청 콜백 함수를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-197">If this value is NULL, discover request callback function is disabled.</span></span>
- <span data-ttu-id="8638f-198">**pppoe_discover_terminate_notify**: PPPoE 검색 종료 메시지를 받을 때마다 호출되는 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-198">**pppoe_discover_terminate_notify**: Application function that is called whenever PPPoE discover terminate message is received.</span></span> <span data-ttu-id="8638f-199">이 값이 NULL인 경우 검색 종료 콜백 함수를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-199">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="8638f-200">**pppoe_discover_terminate_confirm**: PPPoE 검색 종료 메시지를 보낼 때마다 호출되는 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-200">**pppoe_discover_terminate_confirm**: Application function that is called whenever PPPoE discover terminate message is sent.</span></span> <span data-ttu-id="8638f-201">이 값이 NULL인 경우 검색 종료 콜백 함수를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-201">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="8638f-202">**pppoe_data_receive_notify**: PPPoE 데이터 메시지를 받을 때마다 호출되는 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-202">**pppoe_data_receive_notify**: Application function that is called whenever PPPoE data message is received.</span></span> <span data-ttu-id="8638f-203">이 값은 0이 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-203">This value must not be zero.</span></span>
- <span data-ttu-id="8638f-204">**pppoe_data_send_notify**: PPPoE 데이터 메시지를 보낼 때마다 호출되는 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-204">**pppoe_data_send_notify**: Application function that is called whenever PPPoE data message is sent.</span></span> <span data-ttu-id="8638f-205">이 값이 NULL 이면 데이터 보내기 콜백 함수를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-205">If this value is NULL, data send callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-206">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-206">Return Values</span></span>

- <span data-ttu-id="8638f-207">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공</span><span class="sxs-lookup"><span data-stu-id="8638f-207">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="8638f-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터 또는 함수 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer or function pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-209">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-209">Allowed From</span></span>

<span data-ttu-id="8638f-210">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-210">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-211">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-211">Example</span></span>

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a><span data-ttu-id="8638f-212">nx_pppoe_server_ac_name_set</span><span class="sxs-lookup"><span data-stu-id="8638f-212">nx_pppoe_server_ac_name_set</span></span>

<span data-ttu-id="8638f-213">액세스 집중 장치 이름 설정</span><span class="sxs-lookup"><span data-stu-id="8638f-213">Set Access Concentrator name</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-214">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-214">Prototype</span></span>

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a><span data-ttu-id="8638f-215">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-215">Description</span></span>

<span data-ttu-id="8638f-216">이 함수는 액세스 집중 장치 이름 함수 호출을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-216">This function set Access Concentrator name function call.</span></span>

> [!NOTE]
> <span data-ttu-id="8638f-217">ac_name 문자열은 NULL로 종결되고 ac_name 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-217">The string of ac_name must be NULL-terminated and length of ac_name matches the length specified in the argument list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-218">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-218">Input Parameters</span></span>

- <span data-ttu-id="8638f-219">**pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-219">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="8638f-220">**ac_name**: 액세스 집중 장치 이름</span><span class="sxs-lookup"><span data-stu-id="8638f-220">**ac_name**: Access Concentrator name.</span></span>
- <span data-ttu-id="8638f-221">**ac_name_length**: ac_ame의 길이</span><span class="sxs-lookup"><span data-stu-id="8638f-221">**ac_name_length**: Length of ac_ame.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-222">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-222">Return Values</span></span>

- <span data-ttu-id="8638f-223">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 설정 성공</span><span class="sxs-lookup"><span data-stu-id="8638f-223">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server set.</span></span>
- <span data-ttu-id="8638f-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) 잘못된 PPPoE 서버, IP, 패킷 풀 또는 스택 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="8638f-225">**NX_SIZE_ERROR**: (0x09) name_length 확인 실패</span><span class="sxs-lookup"><span data-stu-id="8638f-225">**NX_SIZE_ERROR**: (0x09) Check name_length fail.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-226">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-226">Allowed From</span></span>

<span data-ttu-id="8638f-227">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-227">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-228">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-228">Example</span></span>

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a><span data-ttu-id="8638f-229">nx_pppoe_server_service_name_set</span><span class="sxs-lookup"><span data-stu-id="8638f-229">nx_pppoe_server_service_name_set</span></span>

<span data-ttu-id="8638f-230">PPPoE 서버 서비스 이름 설정</span><span class="sxs-lookup"><span data-stu-id="8638f-230">Set PPPoE Server service name</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-231">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-231">Prototype</span></span>

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a><span data-ttu-id="8638f-232">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-232">Description</span></span>

<span data-ttu-id="8638f-233">이 서비스는 PPPoE 서버 서비스 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-233">This service sets PPPoE Server service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-234">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-234">Input Parameters</span></span>

- <span data-ttu-id="8638f-235">**pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-235">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-236">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-236">Return Values</span></span>

- <span data-ttu-id="8638f-237">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공</span><span class="sxs-lookup"><span data-stu-id="8638f-237">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="8638f-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-239">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-239">Allowed From</span></span>

<span data-ttu-id="8638f-240">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-240">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-241">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-241">Example</span></span>

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a><span data-ttu-id="8638f-242">nx_pppoe_server_session_send</span><span class="sxs-lookup"><span data-stu-id="8638f-242">nx_pppoe_server_session_send</span></span>

<span data-ttu-id="8638f-243">PPPoE 서버 데이터를 지정된 세션에 보내기</span><span class="sxs-lookup"><span data-stu-id="8638f-243">Send PPPoE Server data to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-244">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-244">Prototype</span></span>

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a><span data-ttu-id="8638f-245">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-245">Description</span></span>

<span data-ttu-id="8638f-246">이 서비스는 지정된 세션 ID를 사용하여 PPPoE 프레임을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-246">This service sends PPPoE frame using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-247">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-247">Input Parameters</span></span>

- <span data-ttu-id="8638f-248">**pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-248">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="8638f-249">**session_index**: 세션의 인덱스</span><span class="sxs-lookup"><span data-stu-id="8638f-249">**session_index**: The index of session.</span></span>
- <span data-ttu-id="8638f-250">**data_ptr**: PPPoE 서버 데이터 프레임의 시작에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-250">**data_ptr**: Pointer to start of PPPoE Server data frame.</span></span>
- <span data-ttu-id="8638f-251">**data_length**: PPPoE 서버 데이터 프레임의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-251">**data_length**: Length of PPPoE Server data frame.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-252">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-252">Return Values</span></span>

- <span data-ttu-id="8638f-253">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공</span><span class="sxs-lookup"><span data-stu-id="8638f-253">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="8638f-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="8638f-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE 서버 서비스를 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="8638f-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) 잘못된 PPPoE 세션 인덱스</span><span class="sxs-lookup"><span data-stu-id="8638f-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="8638f-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE 세션이 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-258">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-258">Allowed From</span></span>

<span data-ttu-id="8638f-259">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-259">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-260">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-260">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a><span data-ttu-id="8638f-261">nx_pppoe_server_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="8638f-261">nx_pppoe_server_session_packet_send</span></span>

<span data-ttu-id="8638f-262">지정된 세션에 PPPoE 서버 패킷 보내기</span><span class="sxs-lookup"><span data-stu-id="8638f-262">Send PPPoE Server packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-263">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-263">Prototype</span></span>

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="8638f-264">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-264">Description</span></span>

<span data-ttu-id="8638f-265">이 서비스는 지정된 세션 ID를 사용하여 PPPoE 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-265">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-266">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-266">Input Parameters</span></span>

- <span data-ttu-id="8638f-267">**pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-267">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="8638f-268">**session_index**: 세션의 인덱스</span><span class="sxs-lookup"><span data-stu-id="8638f-268">**session_index**: The index of session.</span></span>
- <span data-ttu-id="8638f-269">**packet_ptr**: PPPoE 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-269">**packet_ptr**: Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-270">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-270">Return Values</span></span>

- <span data-ttu-id="8638f-271">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공</span><span class="sxs-lookup"><span data-stu-id="8638f-271">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="8638f-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="8638f-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) 잘못된 PPPoE 서버 패킷</span><span class="sxs-lookup"><span data-stu-id="8638f-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid PPPoE Server packet.</span></span>
- <span data-ttu-id="8638f-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE 서버 서비스를 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="8638f-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) 잘못된 PPPoE 세션 인덱스</span><span class="sxs-lookup"><span data-stu-id="8638f-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="8638f-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE 세션이 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-277">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-277">Allowed From</span></span>

<span data-ttu-id="8638f-278">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-278">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-279">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-279">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a><span data-ttu-id="8638f-280">nx_pppoe_server_session_terminate</span><span class="sxs-lookup"><span data-stu-id="8638f-280">nx_pppoe_server_session_terminate</span></span>

<span data-ttu-id="8638f-281">지정된 PPPoE 세션 종료</span><span class="sxs-lookup"><span data-stu-id="8638f-281">Terminate the specified PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-282">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-282">Prototype</span></span>

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a><span data-ttu-id="8638f-283">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-283">Description</span></span>

<span data-ttu-id="8638f-284">이 서비스는 지정된 PPPoE 세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-284">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-285">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-285">Input Parameters</span></span>

- <span data-ttu-id="8638f-286">**pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-286">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="8638f-287">**session_index**: 세션의 인덱스</span><span class="sxs-lookup"><span data-stu-id="8638f-287">**session_index**: The index of session.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-288">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-288">Return Values</span></span>

- <span data-ttu-id="8638f-289">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공</span><span class="sxs-lookup"><span data-stu-id="8638f-289">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="8638f-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="8638f-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE 서버 서비스를 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="8638f-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) 잘못된 PPPoE 세션 인덱스</span><span class="sxs-lookup"><span data-stu-id="8638f-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="8638f-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE 세션이 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-294">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-294">Allowed From</span></span>

<span data-ttu-id="8638f-295">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-296">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-296">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a><span data-ttu-id="8638f-297">nx_pppoe_server_session_get</span><span class="sxs-lookup"><span data-stu-id="8638f-297">nx_pppoe_server_session_get</span></span>

<span data-ttu-id="8638f-298">지정된 PPPoE 세션 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="8638f-298">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-299">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-299">Prototype</span></span>

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="8638f-300">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-300">Description</span></span>

<span data-ttu-id="8638f-301">이 서비스는 지정된 PPPoE 세션 정보, 클라이언트 실제 주소, 세션 ID를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-301">This service gets the specified PPPoE session information, client physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-302">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-302">Input Parameters</span></span>

- <span data-ttu-id="8638f-303">**pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-303">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="8638f-304">**session_index**: 세션의 인덱스</span><span class="sxs-lookup"><span data-stu-id="8638f-304">**session_index**: The index of session.</span></span>
- <span data-ttu-id="8638f-305">**client_mac_msw**: 클라이언트 실제 주소 MSW 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-305">**client_mac_msw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="8638f-306">**client_mac_lsw**: 클라이언트 실제 주소 MSW 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-306">**client_mac_lsw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="8638f-307">**session_id**: 세션 ID 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-307">**session_id**: Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-308">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-308">Return Values</span></span>

- <span data-ttu-id="8638f-309">**NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공</span><span class="sxs-lookup"><span data-stu-id="8638f-309">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="8638f-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="8638f-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) 잘못된 PPPoE 세션 인덱스</span><span class="sxs-lookup"><span data-stu-id="8638f-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="8638f-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE 세션이 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-313">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-313">Allowed From</span></span>

<span data-ttu-id="8638f-314">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-314">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-315">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-315">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a><span data-ttu-id="8638f-316">PppInitInd</span><span class="sxs-lookup"><span data-stu-id="8638f-316">PppInitInd</span></span>

<span data-ttu-id="8638f-317">기본 서비스 이름 구성</span><span class="sxs-lookup"><span data-stu-id="8638f-317">Configure the default Service Name</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-318">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-318">Prototype</span></span>

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="8638f-319">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-319">Description</span></span>

<span data-ttu-id="8638f-320">PPPoE 소프트웨어는 TTP의 소프트웨어가, PPPoE가 들어오는 PADI 요청을 필터링하는 데 사용할 ‘기본 서비스 이름’을 구성할 수 있게 이 함수를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-320">The PPPoE software will expose this function to allow TTP's software to configure the 'default Service Name' that the PPPoE should use to filter incoming PADI requests.</span></span> <span data-ttu-id="8638f-321">PPPoE 소프트웨어는 이 정보를 기억했다가 일치하는 서비스 이름이 포함된 PADI 패킷을 수신했을 때 PppDiscoverReq를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-321">The PPPoE software should remember this information, and if a PADI packet is received containing a service name that matches then it should call PppDiscoverReq.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-322">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-322">Input Parameters</span></span>

- <span data-ttu-id="8638f-323">**length**: 기본 서비스 이름의 길이</span><span class="sxs-lookup"><span data-stu-id="8638f-323">**length**: Length of default service name.</span></span>
- <span data-ttu-id="8638f-324">**aData**: 기본 서비스 이름</span><span class="sxs-lookup"><span data-stu-id="8638f-324">**aData**: Default service name.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-325">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-325">Return Values</span></span>

<span data-ttu-id="8638f-326">**없음**</span><span class="sxs-lookup"><span data-stu-id="8638f-326">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-327">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-327">Allowed From</span></span>

<span data-ttu-id="8638f-328">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-329">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-329">Example</span></span>

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a><span data-ttu-id="8638f-330">PppDiscoverCnf</span><span class="sxs-lookup"><span data-stu-id="8638f-330">PppDiscoverCnf</span></span>

<span data-ttu-id="8638f-331">PADO 패킷의 서비스 이름 필드 정의</span><span class="sxs-lookup"><span data-stu-id="8638f-331">Define the Service Name field of the PADO packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-332">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-332">Prototype</span></span>

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="8638f-333">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-333">Description</span></span>

<span data-ttu-id="8638f-334">PPPoE 소프트웨어는 TTP의 소프트웨어가 PADO 패킷의 서비스 이름 필드를 정의할 수 있도록 이 함수를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-334">The PPPoE software will expose this function to allow TTP's software to define the Service Name field of the PADO packet.</span></span> <span data-ttu-id="8638f-335">PPPoE 소프트웨어는 PppDiscoverCnf가 호출될 때까지 PADO를 보내지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-335">The PPPoE software should not send the PADO until the PppDiscoverCnf is called.</span></span>

<span data-ttu-id="8638f-336">PADO 패킷에는 PPPoE 소프트웨어 초기화에서 정의한 대로 액세스 집중 장치 이름(RFC2516에서 정의한 대로 태그 ID 0x0102 사용)이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-336">The PADO packet shall contain an access concentrator name (using the tag id 0x0102 as defined in RFC2516), defined on initialisation of the PPPoE software.</span></span>

<span data-ttu-id="8638f-337">aData에서 여러 서비스 이름을 전달할 수 있으며 각 이름은 null로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-337">Multiple service names can be passed in aData, with each name to be null terminated.</span></span>

<span data-ttu-id="8638f-338">다른 명령을 서비스 이름의 일부로 전달해야 할 경우 Null 문자를 구분 기호로 사용하여 유연성을 극대화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-338">Null character is used as a separator to provide maximum flexibility in case other commands need to be passed in as part of the service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-339">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-339">Input Parameters</span></span>

- <span data-ttu-id="8638f-340">**length**: 기본 서비스 이름의 길이</span><span class="sxs-lookup"><span data-stu-id="8638f-340">**length**: Length of default service name.</span></span>
- <span data-ttu-id="8638f-341">**aData**: 기본 서비스 이름</span><span class="sxs-lookup"><span data-stu-id="8638f-341">**aData**: Default service name.</span></span>
- <span data-ttu-id="8638f-342">**interfaceHandle**: 인터페이스 핸들</span><span class="sxs-lookup"><span data-stu-id="8638f-342">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-343">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-343">Return Values</span></span>

<span data-ttu-id="8638f-344">**없음**</span><span class="sxs-lookup"><span data-stu-id="8638f-344">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-345">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-345">Allowed From</span></span>

<span data-ttu-id="8638f-346">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-346">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-347">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-347">Example</span></span>

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a><span data-ttu-id="8638f-348">PppOpenCnf</span><span class="sxs-lookup"><span data-stu-id="8638f-348">PppOpenCnf</span></span>

<span data-ttu-id="8638f-349">PPPoE 세션 수락 또는 거절</span><span class="sxs-lookup"><span data-stu-id="8638f-349">Accept or reject the PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-350">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-350">Prototype</span></span>

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="8638f-351">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-351">Description</span></span>

<span data-ttu-id="8638f-352">PPPoE 소프트웨어는 TTP의 소프트웨어가 PPPoE 세션을 수락 또는 거절할 수 있게 이 함수를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-352">The PPPoE software will expose this function to allow TTP's software to accept or reject the PPPoE session.</span></span>  <span data-ttu-id="8638f-353">이에 대한 응답으로 PPPoE 스택은 연결을 수락하고 interfaceHandle과 연결된 고유한 PPPoE Session_ID 번호를 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-353">In response to this the PPPoE stack should accept the connection and assign a unique PPPoE Session_ID number associated with the interfaceHandle.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-354">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-354">Input Parameters</span></span>

- <span data-ttu-id="8638f-355">**accept**: NX_TRUE이면 연결을 수락합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-355">**accept**: NX_TRUE if the connection is to be accepted.</span></span>
- <span data-ttu-id="8638f-356">**interfaceHandle**: 인터페이스 핸들</span><span class="sxs-lookup"><span data-stu-id="8638f-356">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-357">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-357">Return Values</span></span>

<span data-ttu-id="8638f-358">**없음**</span><span class="sxs-lookup"><span data-stu-id="8638f-358">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-359">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-359">Allowed From</span></span>

<span data-ttu-id="8638f-360">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-360">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-361">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-361">Example</span></span>

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a><span data-ttu-id="8638f-362">PppCloseInd</span><span class="sxs-lookup"><span data-stu-id="8638f-362">PppCloseInd</span></span>

<span data-ttu-id="8638f-363">PPPoE 세션 종료</span><span class="sxs-lookup"><span data-stu-id="8638f-363">Close a PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-364">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-364">Prototype</span></span>

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a><span data-ttu-id="8638f-365">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-365">Description</span></span>

<span data-ttu-id="8638f-366">PPPoE 소프트웨어는 TTP의 소프트웨어가 PPPoE 세션을 닫을 수 있게 이 함수를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-366">The PPPoE software will expose this function to allow TTP's software to close a PPPoE session.</span></span>

<span data-ttu-id="8638f-367">PPPoE 소프트웨어는 PADT 메시지에서 Generic-Error 태그(0x0203)의 원인 코드 문자열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-367">The PPPoE software will indicate the cause code string in the Generic-Error tag (0x0203) in the PADT message</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-368">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-368">Input Parameters</span></span>

- <span data-ttu-id="8638f-369">**interfaceHandle**: 인터페이스 핸들</span><span class="sxs-lookup"><span data-stu-id="8638f-369">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="8638f-370">**causeCode**: PPPoE 서버로부터 연결 종료 사유에 대한 정보를 보내기 위한 Null 종료 문자열</span><span class="sxs-lookup"><span data-stu-id="8638f-370">**causeCode**: Null terminated string for sending information about the reason for closing the connection from the PPPoE Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-371">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-371">Return Values</span></span>

<span data-ttu-id="8638f-372">**없음**</span><span class="sxs-lookup"><span data-stu-id="8638f-372">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-373">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-373">Allowed From</span></span>

<span data-ttu-id="8638f-374">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-374">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-375">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-375">Example</span></span>

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a><span data-ttu-id="8638f-376">PppCloseCnf</span><span class="sxs-lookup"><span data-stu-id="8638f-376">PppCloseCnf</span></span>

<span data-ttu-id="8638f-377">핸들이 해제되었음을 확인</span><span class="sxs-lookup"><span data-stu-id="8638f-377">Confirm that the handle has been freed</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-378">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-378">Prototype</span></span>

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="8638f-379">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-379">Description</span></span>

<span data-ttu-id="8638f-380">PPPoE 소프트웨어는 TTP의 소프트웨어가 핸들이 해제되었음을 확인할 수 있게 이 함수를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-380">The PPPoE software will expose this function to allow TTP's software to confirm that the handle has been freed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-381">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-381">Input Parameters</span></span>

- <span data-ttu-id="8638f-382">**interfaceHandle**: 인터페이스 핸들</span><span class="sxs-lookup"><span data-stu-id="8638f-382">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-383">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-383">Return Values</span></span>

<span data-ttu-id="8638f-384">**없음**</span><span class="sxs-lookup"><span data-stu-id="8638f-384">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-385">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-385">Allowed From</span></span>

<span data-ttu-id="8638f-386">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-386">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-387">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-387">Example</span></span>

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a><span data-ttu-id="8638f-388">PppTransmitDataCnf</span><span class="sxs-lookup"><span data-stu-id="8638f-388">PppTransmitDataCnf</span></span>

<span data-ttu-id="8638f-389">앞의 PPP 데이터를 승인할 수 있게 허용</span><span class="sxs-lookup"><span data-stu-id="8638f-389">Allow a preceding PPP data to be acknowledged</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-390">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-390">Prototype</span></span>

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a><span data-ttu-id="8638f-391">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-391">Description</span></span>

<span data-ttu-id="8638f-392">PPPoE 소프트웨어는 이전 PppTransmitDataReq를 승인할 수 있도록 이 함수를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-392">The PPPoE software will expose this function to allow a preceding PppTransmitDataReq to be acknowledged.</span></span>  <span data-ttu-id="8638f-393">TTP의 소프트웨어가 PPPoE의 새 PPP 프레임을 사용할 준비가 되었음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-393">It implies that TTP's software is ready for a new PPP frame from PPPoE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-394">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-394">Input Parameters</span></span>

- <span data-ttu-id="8638f-395">**interfaceHandle**: 인터페이스 핸들</span><span class="sxs-lookup"><span data-stu-id="8638f-395">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="8638f-396">**aData**: 수락된 PPP 데이터 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8638f-396">**aData**: Pointer the PPP data buffer that has been accepted.</span></span>
- <span data-ttu-id="8638f-397">**Packet_id**: 패킷 식별자</span><span class="sxs-lookup"><span data-stu-id="8638f-397">**Packet_id**: Packet identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-398">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-398">Return Values</span></span>

<span data-ttu-id="8638f-399">**없음**</span><span class="sxs-lookup"><span data-stu-id="8638f-399">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-400">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-400">Allowed From</span></span>

<span data-ttu-id="8638f-401">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-401">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-402">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-402">Example</span></span>

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a><span data-ttu-id="8638f-403">PppReceiveDataInd</span><span class="sxs-lookup"><span data-stu-id="8638f-403">PppReceiveDataInd</span></span>

<span data-ttu-id="8638f-404">이더넷을 통한 전송에서 데이터 수신</span><span class="sxs-lookup"><span data-stu-id="8638f-404">Receive data from transmission over Ethernet</span></span>

### <a name="prototype"></a><span data-ttu-id="8638f-405">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8638f-405">Prototype</span></span>

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="8638f-406">Description</span><span class="sxs-lookup"><span data-stu-id="8638f-406">Description</span></span>

<span data-ttu-id="8638f-407">PPPoE 소프트웨어는 이더넷을 통한 송신용 데이터를 수신하기 위해 이 함수를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="8638f-407">The PPPoE software will expose this function to receive data for transmission over Ethernet</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8638f-408">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8638f-408">Input Parameters</span></span>

- <span data-ttu-id="8638f-409">**interfaceHandle**: 인터페이스 핸들</span><span class="sxs-lookup"><span data-stu-id="8638f-409">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="8638f-410">**length**: aData의 바이트 수</span><span class="sxs-lookup"><span data-stu-id="8638f-410">**length**: The number of bytes in aData.</span></span>
- <span data-ttu-id="8638f-411">**aData**: PPP 데이터의 프레임을 포함하는 데이터 버퍼</span><span class="sxs-lookup"><span data-stu-id="8638f-411">**aData**: Data buffer containing the frame of PPP data.</span></span>

### <a name="return-values"></a><span data-ttu-id="8638f-412">반환 값</span><span class="sxs-lookup"><span data-stu-id="8638f-412">Return Values</span></span>

<span data-ttu-id="8638f-413">**없음**</span><span class="sxs-lookup"><span data-stu-id="8638f-413">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8638f-414">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8638f-414">Allowed From</span></span>

<span data-ttu-id="8638f-415">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8638f-415">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="8638f-416">예제</span><span class="sxs-lookup"><span data-stu-id="8638f-416">Example</span></span>

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```