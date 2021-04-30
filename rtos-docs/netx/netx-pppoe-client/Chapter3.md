---
title: 3장 - Azure RTOS NetX PPPoE 클라이언트 서비스 설명
description: 이 장에서는 아래에 나열된 모든 Azure RTOS NetX PPPoE 클라이언트 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 246115fc97d7597246f7fd5b4fb88cb615baab33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810405"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a><span data-ttu-id="f7ff4-103">3장 - Azure RTOS NetX PPPoE 클라이언트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="f7ff4-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Client Services</span></span>

<span data-ttu-id="f7ff4-104">이 장에서는 아래에 나열된 모든 Azure RTOS NetX PPPoE 클라이언트 서비스에 대해 알파벳 순서로 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-104">This chapter contains a description of all Azure RTOS NetX PPPoE Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="f7ff4-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="f7ff4-106">**nx_pppoe_client_create** *PPPoE 클라이언트 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="f7ff4-106">**nx_pppoe_client_create** *Create a PPPoE Client instance*</span></span>
- <span data-ttu-id="f7ff4-107">**nx_pppoe_client_delete** *PPPoE 클라이언트 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="f7ff4-107">**nx_pppoe_client_delete** *Delete a PPPoE Client instance*</span></span>
- <span data-ttu-id="f7ff4-108">**nx_pppoe_client_host_uniq_set** *PPPoE 클라이언트에 대한 고유한 호스트 설정*</span><span class="sxs-lookup"><span data-stu-id="f7ff4-108">**nx_pppoe_client_host_uniq_set** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="f7ff4-109">**nx_pppoe_client_host_uniq_set_extended** *PPPoE 클라이언트에 대한 고유한 호스트 설정*</span><span class="sxs-lookup"><span data-stu-id="f7ff4-109">**nx_pppoe_client_host_uniq_set_extended** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="f7ff4-110">**nx_pppoe_client_service_name_set** *PPPoE 클라이언트에 대한 서비스 이름 설정*</span><span class="sxs-lookup"><span data-stu-id="f7ff4-110">**nx_pppoe_client_service_name_set** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="f7ff4-111">**nx_pppoe_client_service_name_set_extended** *PPPoE 클라이언트에 대한 서비스 이름 설정*</span><span class="sxs-lookup"><span data-stu-id="f7ff4-111">**nx_pppoe_client_service_name_set_extended** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="f7ff4-112">**nx_pppoe_client_session_connect** *PPPoE 서버에 PPPoE 클라이언트 세션 연결*</span><span class="sxs-lookup"><span data-stu-id="f7ff4-112">**nx_pppoe_client_session_connect** *Connect PPPoE Client session to PPPoE Server*</span></span>
- <span data-ttu-id="f7ff4-113">**nx_pppoe_client_session_packet_send** *PPPoE 세션 패킷 전송*</span><span class="sxs-lookup"><span data-stu-id="f7ff4-113">**nx_pppoe_client_session_packet_send** *Send PPPoE session packet*</span></span>
- <span data-ttu-id="f7ff4-114">**nx_pppoe_client_session_terminate** *PPPoE 세션 종료*</span><span class="sxs-lookup"><span data-stu-id="f7ff4-114">**nx_pppoe_client_session_terminate** *Terminate the PPPoE session*</span></span>
- <span data-ttu-id="f7ff4-115">**nx_pppoe_client_session_get** *지정된 PPPoE 세션 inf 가져오기*</span><span class="sxs-lookup"><span data-stu-id="f7ff4-115">**nx_pppoe_client_session_get** *Get the specified PPPoE session inf*</span></span>

## <a name="nx_pppoe_client_create"></a><span data-ttu-id="f7ff4-116">nx_pppoe_client_create</span><span class="sxs-lookup"><span data-stu-id="f7ff4-116">nx_pppoe_client_create</span></span>

<span data-ttu-id="f7ff4-117">PPPoE 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="f7ff4-117">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f7ff4-118">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7ff4-118">Prototype</span></span>

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="f7ff4-119">Description</span><span class="sxs-lookup"><span data-stu-id="f7ff4-119">Description</span></span>

<span data-ttu-id="f7ff4-120">이 서비스는 지정된 NetX IP 인스턴스의 사용자 제공 링크 드라이버를 사용하여 PPPoE 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-120">This service creates a PPPoE Client instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="f7ff4-121">링크 드라이버가 초기화되지 않고 사용하도록 설정된 경우 PPPoE 클라이언트 소프트웨어는 링크 드라이버를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-121">If link driver has not been initialized, and enabled, PPPoE Client software is responsible initializing the link driver.</span></span>

<span data-ttu-id="f7ff4-122">또한 애플리케이션은 내부 패킷 할당에 사용할 PPPoE 클라이언트 인스턴스에 대해 이전에 만든 패킷 풀을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-122">In addition, the application must supply a previously created packet pool for the PPPoE Client instance to use for internal packet allocation.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ff4-123">일반적으로는 PPPoE 클라이언트 스레드 우선 순위보다 우선 순위가 높은 NetX IP 스레드를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-123">Generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Client thread priority.</span></span> <span data-ttu-id="f7ff4-124">IP 스레드 우선 순위를 지정하는 방법에 대한 자세한 내용은 *nx_ip_create* 서비스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-124">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7ff4-125">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7ff4-125">Input Parameters</span></span>

 - <span data-ttu-id="f7ff4-126">**pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-126">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="f7ff4-127">**name** 이 PPPoE 클라이언트 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-127">**name** Name of this PPPoE Client instance.</span></span>
 - <span data-ttu-id="f7ff4-128">**ip_ptr** IP 인스턴스의 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-128">**ip_ptr** Pointer to control block for IP instance.</span></span>
 - <span data-ttu-id="f7ff4-129">**interface_index** 인터페이스 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-129">**interface_index** Interface index.</span></span>
 - <span data-ttu-id="f7ff4-130">**pool_ptr** 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-130">**pool_ptr** Pointer to packet pool.</span></span>
 - <span data-ttu-id="f7ff4-131">**stack_ptr** PPPoE 클라이언트 스레드의 스택 영역 시작에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-131">**stack_ptr** Pointer to start of PPPoE Client thread’s stack area.</span></span>
 - <span data-ttu-id="f7ff4-132">**stack_size** 스레드의 스택에 있는 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-132">**stack_size** Size in bytes in the thread’s stack.</span></span>
 - <span data-ttu-id="f7ff4-133">**priority** 내부 PPPoE 클라이언트 스레드의 우선 순위(1-31)입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-133">**priority** Priority of internal PPPoE Client threads (1-31).</span></span>
 - <span data-ttu-id="f7ff4-134">**pppoe_link_driver** 사용자가 제공한 링크 드라이버입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-134">**pppoe_link_driver** User supplied link driver.</span></span>
 - <span data-ttu-id="f7ff4-135">**pppoe_packet_receive** 사용자가 제공한 패킷 수신 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-135">**pppoe_packet_receive** User supplied packet receive function.</span></span>

### <a name="return-values"></a><span data-ttu-id="f7ff4-136">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7ff4-136">Return Values</span></span>

 - <span data-ttu-id="f7ff4-137">**NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 만들기입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-137">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client create.</span></span>
 - <span data-ttu-id="f7ff4-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) 잘못된 PPPoE 클라이언트, IP, 패킷 풀 또는 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client, IP, packet pool, or stack pointer.</span></span>
 - <span data-ttu-id="f7ff4-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) 인터페이스가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Invalid interface.</span></span>
 - <span data-ttu-id="f7ff4-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) 패킷 풀의 페이로드 크기가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid payload size of packet pool.</span></span>
 - <span data-ttu-id="f7ff4-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) 메모리 크기가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Invalid memory size.</span></span>
 - <span data-ttu-id="f7ff4-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) PPPoE 클라이언트 스레드의 우선 순위가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Invalid priority of PPPoE Client thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7ff4-143">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7ff4-143">Allowed From</span></span>

<span data-ttu-id="f7ff4-144">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f7ff4-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f7ff4-145">예제</span><span class="sxs-lookup"><span data-stu-id="f7ff4-145">Example</span></span>

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a><span data-ttu-id="f7ff4-146">nx_pppoe_client_delete</span><span class="sxs-lookup"><span data-stu-id="f7ff4-146">nx_pppoe_client_delete</span></span>

<span data-ttu-id="f7ff4-147">PPPoE 클라이언트 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="f7ff4-147">Delete a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f7ff4-148">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7ff4-148">Prototype</span></span>

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="f7ff4-149">Description</span><span class="sxs-lookup"><span data-stu-id="f7ff4-149">Description</span></span>

<span data-ttu-id="f7ff4-150">이 서비스는 이전에 만든 PPPoE 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-150">This service deletes the previously created PPPoE Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7ff4-151">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7ff4-151">Input Parameters</span></span>

 - <span data-ttu-id="f7ff4-152">**pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-152">**pppoe_client_ptr** Pointer to PPPoE Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="f7ff4-153">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7ff4-153">Return Values</span></span>

 - <span data-ttu-id="f7ff4-154">**NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 삭제입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-154">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client delete.</span></span>
 - <span data-ttu-id="f7ff4-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7ff4-156">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7ff4-156">Allowed From</span></span>

<span data-ttu-id="f7ff4-157">스레드</span><span class="sxs-lookup"><span data-stu-id="f7ff4-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f7ff4-158">예제</span><span class="sxs-lookup"><span data-stu-id="f7ff4-158">Example</span></span>

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a><span data-ttu-id="f7ff4-159">nx_pppoe_client_host_uniq_set</span><span class="sxs-lookup"><span data-stu-id="f7ff4-159">nx_pppoe_client_host_uniq_set</span></span>

<span data-ttu-id="f7ff4-160">PPPoE 클라이언트 호스트 고유 설정</span><span class="sxs-lookup"><span data-stu-id="f7ff4-160">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="f7ff4-161">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7ff4-161">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a><span data-ttu-id="f7ff4-162">Description</span><span class="sxs-lookup"><span data-stu-id="f7ff4-162">Description</span></span>

<span data-ttu-id="f7ff4-163">이 서비스는 고유한 PPPoE 클라이언트 호스트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-163">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="f7ff4-164">Host-Uniq는 호스트에서 액세스 집중 장치를 특정 호스트 요청에 고유하게 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-164">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="f7ff4-165">호스트에서 선택하는 값과 길이의 이진 데이터일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-165">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ff4-166">고유한 호스트는 Null로 끝나는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-166">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ff4-167">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-167">This service is deprecated.</span></span> <span data-ttu-id="f7ff4-168">개발자는 *nx_pppoe_client_host_uniq_set_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-168">Developers are encouraged to migrate to *nx_pppoe_client_host_uniq_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7ff4-169">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7ff4-169">Input Parameters</span></span>

 - <span data-ttu-id="f7ff4-170">**pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-170">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="f7ff4-171">**host_uniq** 고유한 호스트에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-171">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="f7ff4-172">고유한 호스트는 Null로 끝나는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-172">Host unique must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="f7ff4-173">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7ff4-173">Return Values</span></span>

 - <span data-ttu-id="f7ff4-174">**NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 호스트 고유 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-174">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="f7ff4-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7ff4-176">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7ff4-176">Allowed From</span></span>

<span data-ttu-id="f7ff4-177">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f7ff4-177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f7ff4-178">예제</span><span class="sxs-lookup"><span data-stu-id="f7ff4-178">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a><span data-ttu-id="f7ff4-179">nx_pppoe_client_host_uniq_set_extended</span><span class="sxs-lookup"><span data-stu-id="f7ff4-179">nx_pppoe_client_host_uniq_set_extended</span></span>

<span data-ttu-id="f7ff4-180">PPPoE 클라이언트 호스트 고유 설정</span><span class="sxs-lookup"><span data-stu-id="f7ff4-180">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="f7ff4-181">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7ff4-181">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a><span data-ttu-id="f7ff4-182">Description</span><span class="sxs-lookup"><span data-stu-id="f7ff4-182">Description</span></span>

<span data-ttu-id="f7ff4-183">이 서비스는 고유한 PPPoE 클라이언트 호스트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-183">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="f7ff4-184">Host-Uniq는 호스트에서 액세스 집중 장치를 특정 호스트 요청에 고유하게 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-184">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="f7ff4-185">호스트에서 선택하는 값과 길이의 이진 데이터일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-185">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ff4-186">고유한 호스트는 Null로 끝나는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-186">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ff4-187">이 서비스는 *nx_pppoe_client_host_uniq_set()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-187">This service replaces *nx_pppoe_client_host_uniq_set()*.</span></span> <span data-ttu-id="f7ff4-188">이 버전은 추가 길이 정보를 서비스에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-188">This version supplies additional length information to the service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7ff4-189">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7ff4-189">Input Parameters</span></span>

 - <span data-ttu-id="f7ff4-190">**pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-190">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="f7ff4-191">**host_uniq** 고유한 호스트에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-191">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="f7ff4-192">고유한 호스트는 Null로 끝나는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-192">Host unique must be Null-terminated string.</span></span>
 - <span data-ttu-id="f7ff4-193">**host_uniq_length** host_uniq의 길이</span><span class="sxs-lookup"><span data-stu-id="f7ff4-193">**host_uniq_length** Length of host_uniq</span></span>

### <a name="return-values"></a><span data-ttu-id="f7ff4-194">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7ff4-194">Return Values</span></span>

 - <span data-ttu-id="f7ff4-195">**NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 호스트 고유 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-195">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="f7ff4-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="f7ff4-197">**NX_SIZE_ERROR** (0x09) host_uniq_length 실패 확인</span><span class="sxs-lookup"><span data-stu-id="f7ff4-197">**NX_SIZE_ERROR** (0x09) Check host_uniq_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7ff4-198">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7ff4-198">Allowed From</span></span>

<span data-ttu-id="f7ff4-199">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f7ff4-199">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f7ff4-200">예제</span><span class="sxs-lookup"><span data-stu-id="f7ff4-200">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a><span data-ttu-id="f7ff4-201">nx_pppoe_client_service_name_set</span><span class="sxs-lookup"><span data-stu-id="f7ff4-201">nx_pppoe_client_service_name_set</span></span>

<span data-ttu-id="f7ff4-202">PPPoE 클라이언트 서비스 이름 설정</span><span class="sxs-lookup"><span data-stu-id="f7ff4-202">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="f7ff4-203">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7ff4-203">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a><span data-ttu-id="f7ff4-204">Description</span><span class="sxs-lookup"><span data-stu-id="f7ff4-204">Description</span></span>

<span data-ttu-id="f7ff4-205">이 서비스는 PPPoE 클라이언트 서비스 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-205">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="f7ff4-206">호스트에서 요청하는 서비스를 나타내는 Service-Name입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-206">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="f7ff4-207">Service-Name이 설정되지 않은 경우 호스트가 원하는 수의 서비스를 허용함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-207">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ff4-208">서비스 이름은 Null로 끝나는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-208">service name must be Null-terminated string</span></span>

> [!NOTE]
> <span data-ttu-id="f7ff4-209">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-209">This service is deprecated.</span></span> <span data-ttu-id="f7ff4-210">개발자는 *nx_pppoe_client_service_name_set_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-210">Developers are encouraged to migrate to *nx_pppoe_client_service_name_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7ff4-211">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7ff4-211">Input Parameters</span></span>

 - <span data-ttu-id="f7ff4-212">**pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-212">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="f7ff4-213">**service_name** 서비스 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-213">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="f7ff4-214">서비스 이름은 Null로 끝나는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-214">Service name must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="f7ff4-215">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7ff4-215">Return Values</span></span>

 - <span data-ttu-id="f7ff4-216">**NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 서비스 이름 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-216">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="f7ff4-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7ff4-218">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7ff4-218">Allowed From</span></span>

<span data-ttu-id="f7ff4-219">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f7ff4-219">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f7ff4-220">예제</span><span class="sxs-lookup"><span data-stu-id="f7ff4-220">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a><span data-ttu-id="f7ff4-221">nx_pppoe_client_service_name_set_extended</span><span class="sxs-lookup"><span data-stu-id="f7ff4-221">nx_pppoe_client_service_name_set_extended</span></span>

<span data-ttu-id="f7ff4-222">PPPoE 클라이언트 서비스 이름 설정</span><span class="sxs-lookup"><span data-stu-id="f7ff4-222">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="f7ff4-223">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7ff4-223">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a><span data-ttu-id="f7ff4-224">Description</span><span class="sxs-lookup"><span data-stu-id="f7ff4-224">Description</span></span>

<span data-ttu-id="f7ff4-225">이 서비스는 PPPoE 클라이언트 서비스 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-225">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="f7ff4-226">호스트에서 요청하는 서비스를 나타내는 Service-Name입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-226">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="f7ff4-227">Service-Name이 설정되지 않은 경우 호스트가 원하는 수의 서비스를 허용함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-227">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ff4-228">서비스 이름은 Null로 끝나는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-228">service name must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ff4-229">이 서비스는 *nx_pppoe_client_service_name_set()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-229">This service replaces *nx_pppoe_client_service_name_set()*.</span></span> <span data-ttu-id="f7ff4-230">이 버전은 추가 서비스 이름 길이 정보를 함수에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-230">This version supplies additional service name length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7ff4-231">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7ff4-231">Input Parameters</span></span>

 - <span data-ttu-id="f7ff4-232">**pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-232">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="f7ff4-233">**service_name** 서비스 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-233">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="f7ff4-234">서비스 이름은 Null로 끝나는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-234">Service name must be Null-terminated string.</span></span>
 - <span data-ttu-id="f7ff4-235">**service_name_length** service_name의 길이</span><span class="sxs-lookup"><span data-stu-id="f7ff4-235">**service_name_length** Length of service_name</span></span>

### <a name="return-values"></a><span data-ttu-id="f7ff4-236">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7ff4-236">Return Values</span></span>

 - <span data-ttu-id="f7ff4-237">**NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 서비스 이름 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-237">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="f7ff4-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="f7ff4-239">**NX_SIZE_ERROR** (0x09) service_name_length 실패 확인</span><span class="sxs-lookup"><span data-stu-id="f7ff4-239">**NX_SIZE_ERROR** (0x09) Check service_name_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7ff4-240">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7ff4-240">Allowed From</span></span>

<span data-ttu-id="f7ff4-241">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f7ff4-241">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f7ff4-242">예제</span><span class="sxs-lookup"><span data-stu-id="f7ff4-242">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a><span data-ttu-id="f7ff4-243">nx_pppoe_client_session_connect</span><span class="sxs-lookup"><span data-stu-id="f7ff4-243">nx_pppoe_client_session_connect</span></span>

<span data-ttu-id="f7ff4-244">PPPoE 클라이언트 세션 연결</span><span class="sxs-lookup"><span data-stu-id="f7ff4-244">Connect PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="f7ff4-245">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7ff4-245">Prototype</span></span>

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f7ff4-246">Description</span><span class="sxs-lookup"><span data-stu-id="f7ff4-246">Description</span></span>

<span data-ttu-id="f7ff4-247">이 서비스는 이전에 만든 PPPoE 클라이언트를 사용하여 지정된 PPPoE 서버에 PPPoE 세션 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-247">This service makes PPPoE session connection using a previously created PPPoE Client to the specified PPPoE Server.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ff4-248">이 함수는 *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* 및 *nx_pppoe_client_service_name_set* 후에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-248">This function must be called after *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* and *nx_pppoe_client_service_name_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7ff4-249">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7ff4-249">Input Parameters</span></span>

 - <span data-ttu-id="f7ff4-250">**pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-250">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="f7ff4-251">**wait_option** 연결이 설정되는 동안 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-251">**wait_option** Wait option while the connection is being established.</span></span>

### <a name="return-values"></a><span data-ttu-id="f7ff4-252">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7ff4-252">Return Values</span></span>

 - <span data-ttu-id="f7ff4-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 세션 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session connect.</span></span>
 - <span data-ttu-id="f7ff4-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7ff4-255">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7ff4-255">Allowed From</span></span>

<span data-ttu-id="f7ff4-256">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f7ff4-256">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f7ff4-257">예제</span><span class="sxs-lookup"><span data-stu-id="f7ff4-257">Example</span></span>

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a><span data-ttu-id="f7ff4-258">nx_pppoe_client_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="f7ff4-258">nx_pppoe_client_session_packet_send</span></span>

<span data-ttu-id="f7ff4-259">지정된 세션에 PPPoE 클라이언트 패킷 보내기</span><span class="sxs-lookup"><span data-stu-id="f7ff4-259">Send PPPoE Client packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="f7ff4-260">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7ff4-260">Prototype</span></span>

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="f7ff4-261">Description</span><span class="sxs-lookup"><span data-stu-id="f7ff4-261">Description</span></span>

<span data-ttu-id="f7ff4-262">이 서비스는 지정된 세션 ID를 사용하여 PPPoE 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-262">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7ff4-263">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7ff4-263">Input Parameters</span></span>

 - <span data-ttu-id="f7ff4-264">**pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-264">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="f7ff4-265">**packet_ptr** PPPoE 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-265">**packet_ptr** Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="f7ff4-266">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7ff4-266">Return Values</span></span>

 - <span data-ttu-id="f7ff4-267">**NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 패킷 전송입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-267">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client packet send.</span></span>
 - <span data-ttu-id="f7ff4-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="f7ff4-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) PPPoE 클라이언트 패킷이 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid PPPoE Client packet.</span></span>
 - <span data-ttu-id="f7ff4-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE 세션이 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7ff4-271">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7ff4-271">Allowed From</span></span>

<span data-ttu-id="f7ff4-272">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f7ff4-272">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f7ff4-273">예제</span><span class="sxs-lookup"><span data-stu-id="f7ff4-273">Example</span></span>

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a><span data-ttu-id="f7ff4-274">nx_pppoe_client_session_terminate</span><span class="sxs-lookup"><span data-stu-id="f7ff4-274">nx_pppoe_client_session_terminate</span></span>

<span data-ttu-id="f7ff4-275">PPPoE 클라이언트 세션 종료</span><span class="sxs-lookup"><span data-stu-id="f7ff4-275">Terminate PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="f7ff4-276">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7ff4-276">Prototype</span></span>

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="f7ff4-277">Description</span><span class="sxs-lookup"><span data-stu-id="f7ff4-277">Description</span></span>

<span data-ttu-id="f7ff4-278">이 서비스는 지정된 PPPoE 세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-278">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7ff4-279">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7ff4-279">Input Parameters</span></span>

 - <span data-ttu-id="f7ff4-280">**pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-280">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f7ff4-281">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7ff4-281">Return Values</span></span>

 - <span data-ttu-id="f7ff4-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 세션 종료입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session terminate.</span></span>
 - <span data-ttu-id="f7ff4-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7ff4-284">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7ff4-284">Allowed From</span></span>

<span data-ttu-id="f7ff4-285">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f7ff4-285">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f7ff4-286">예제</span><span class="sxs-lookup"><span data-stu-id="f7ff4-286">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a><span data-ttu-id="f7ff4-287">nx_pppoe_client_session_get</span><span class="sxs-lookup"><span data-stu-id="f7ff4-287">nx_pppoe_client_session_get</span></span>

<span data-ttu-id="f7ff4-288">지정된 PPPoE 세션 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="f7ff4-288">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="f7ff4-289">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7ff4-289">Prototype</span></span>

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="f7ff4-290">Description</span><span class="sxs-lookup"><span data-stu-id="f7ff4-290">Description</span></span>

<span data-ttu-id="f7ff4-291">이 서비스는 지정된 PPPoE 세션 정보, 서버 실제 주소 및 세션 ID를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-291">This service gets the specified PPPoE session information, server physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7ff4-292">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7ff4-292">Input Parameters</span></span>

 - <span data-ttu-id="f7ff4-293">**pppoe_server_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-293">**pppoe_server_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="f7ff4-294">**server_mac_msw** 서버 실제 주소 MSW 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-294">**server_mac_msw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="f7ff4-295">**server_mac_msw** 서버 실제 주소 MSW 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-295">**server_mac_lsw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="f7ff4-296">**session_id** Session ID 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-296">**session_id** Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f7ff4-297">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7ff4-297">Return Values</span></span>

 - <span data-ttu-id="f7ff4-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 세션 가져오기입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session get.</span></span>
 - <span data-ttu-id="f7ff4-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="f7ff4-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE 세션이 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ff4-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7ff4-301">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7ff4-301">Allowed From</span></span>

<span data-ttu-id="f7ff4-302">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f7ff4-302">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="f7ff4-303">예제</span><span class="sxs-lookup"><span data-stu-id="f7ff4-303">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
