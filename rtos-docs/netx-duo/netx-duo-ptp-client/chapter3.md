---
title: 챕터 3 - Azure RTOS NetX Duo PTP 클라이언트 서비스 설명
description: 이 챕터에서는 모든 NetX Duo PTP 클라이언트 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810620"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a><span data-ttu-id="8baaa-103">챕터 3 - Azure RTOS NetX Duo PTP 클라이언트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="8baaa-103">Chapter 3 - Description of Azure RTOS NetX Duo PTP Client Services</span></span>

<span data-ttu-id="8baaa-104">이 챕터에서는 아래에 나열된 모든 NetX Duo PTP 클라이언트 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-104">This chapter contains a description of all NetX Duo PTP client services (listed below) in alphabetical order.</span></span>

[!NOTE]
> <span data-ttu-id="8baaa-105">*다음 API 함수 설명의 **반환 값** 섹션에서 **굵게 표시된** 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용할 수 없게 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="8baaa-105">*In the **Return Values** section in the following API function descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.*</span></span>

## <a name="nx_ptp_client_create"></a><span data-ttu-id="8baaa-106">nx_ptp_client_create</span><span class="sxs-lookup"><span data-stu-id="8baaa-106">nx_ptp_client_create</span></span>

<span data-ttu-id="8baaa-107">PTP 클라이언트 인스턴스 만들기.</span><span class="sxs-lookup"><span data-stu-id="8baaa-107">Create a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-108">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-108">Prototype</span></span>

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a><span data-ttu-id="8baaa-109">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-109">Description</span></span>

<span data-ttu-id="8baaa-110">이 서비스는 PTP 클라이언트의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-110">This service creates an instance of the PTP client.</span></span>

<span data-ttu-id="8baaa-111">애플리케이션에서 패킷을 전송하기 위해 먼저 PTP 클라이언트에 대한 IP 인스턴스 및 패킷 풀을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-111">Note that the  application must first create an IP instance and a packet pool for the PTP client to transmit packets.</span></span> <span data-ttu-id="8baaa-112">패킷 풀의 경우 애플리케이션은 IP 인스턴스에서 동일한 패킷 풀을 사용할 수 있습니다. 또는 PTP 클라이언트에 대한 전용 패킷 풀을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-112">For the packet pool, application may use the same packet pool in the IP instance; or it can create a dedicated packet pool for PTP client.</span></span>  <span data-ttu-id="8baaa-113">전용 패킷 풀 접근 방식은 작은 패킷(IPv6을 사용하는 경우 128바이트 패킷 또는 IPv4 전용의 경우 108바이트)을 사용하는 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-113">The dedicated packet pool approach has the advantage of using small packets (128 bytes packets if IPv6 is used, or 108 bytes for IPv4-only).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-114">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-114">Input Parameters</span></span>
* <span data-ttu-id="8baaa-115">**client_ptr** 만들 PTP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-115">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8baaa-116">**ip_ptr** IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-116">**ip_ptr** Pointer to IP instance</span></span>
* <span data-ttu-id="8baaa-117">**interface_index** PTP 네트워크 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="8baaa-117">**interface_index** Index of PTP network interface</span></span>
* <span data-ttu-id="8baaa-118">**packet_pool_ptr** 클라이언트 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-118">**packet_pool_ptr** Pointer to client packet pool</span></span>
* <span data-ttu-id="8baaa-119">**thread_priority**  PTP 스레드의 우선 순위</span><span class="sxs-lookup"><span data-stu-id="8baaa-119">**thread_priority**  Priority of PTP thread</span></span>
* <span data-ttu-id="8baaa-120">**thread_stack** 스레드 스택에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-120">**thread_stack** Pointer to thread stack</span></span>
* <span data-ttu-id="8baaa-121">**stack_size** 스레드 스택의 크기</span><span class="sxs-lookup"><span data-stu-id="8baaa-121">**stack_size** Size of thread stack</span></span>
* <span data-ttu-id="8baaa-122">**clock_callback** PTP 클록 콜백</span><span class="sxs-lookup"><span data-stu-id="8baaa-122">**clock_callback** PTP clock callback</span></span>
* <span data-ttu-id="8baaa-123">**clock_callback_data** 클록 콜백에 대한 데이터</span><span class="sxs-lookup"><span data-stu-id="8baaa-123">**clock_callback_data** Data for the clock callback</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-124">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-124">Return Values</span></span>
* <span data-ttu-id="8baaa-125">**NX_SUCCESS** (0x00) 클라이언트를 만듦</span><span class="sxs-lookup"><span data-stu-id="8baaa-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="8baaa-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) 패킷 페이로드가 너무 작음</span><span class="sxs-lookup"><span data-stu-id="8baaa-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) Packet payload too small</span></span>
* <span data-ttu-id="8baaa-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) 클록 콜백 실패</span><span class="sxs-lookup"><span data-stu-id="8baaa-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Failure on clock callback</span></span>
* <span data-ttu-id="8baaa-128">**status** NetX Duo 및 ThreadX 서비스 호출의 완료 상태</span><span class="sxs-lookup"><span data-stu-id="8baaa-128">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="8baaa-129">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-129">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
* <span data-ttu-id="8baaa-130">NX_INVALID_INTERFACE (0x4C) 잘못된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8baaa-130">NX_INVALID_INTERFACE (0x4C) Invalid interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-131">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-131">Allowed From</span></span>
<span data-ttu-id="8baaa-132">스레드</span><span class="sxs-lookup"><span data-stu-id="8baaa-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-133">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-133">Example</span></span>
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a><span data-ttu-id="8baaa-134">nx_ptp_client_delete</span><span class="sxs-lookup"><span data-stu-id="8baaa-134">nx_ptp_client_delete</span></span>

<span data-ttu-id="8baaa-135">PTP 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-135">Deletes a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-136">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-136">Prototype</span></span>

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="8baaa-137">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-137">Description</span></span>

<span data-ttu-id="8baaa-138">이 서비스는 PTP 클라이언트의 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-138">This service deletes an instance of the PTP client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-139">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-139">Input Parameters</span></span>
* <span data-ttu-id="8baaa-140">**client_ptr** 삭제할 PTP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-140">**client_ptr** Pointer to PTP client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-141">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-141">Return Values</span></span>
* <span data-ttu-id="8baaa-142">**NX_SUCCESS** (0x00) 클라이언트를 삭제함</span><span class="sxs-lookup"><span data-stu-id="8baaa-142">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
* <span data-ttu-id="8baaa-143">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-143">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-144">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-144">Allowed From</span></span>
<span data-ttu-id="8baaa-145">스레드</span><span class="sxs-lookup"><span data-stu-id="8baaa-145">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-146">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-146">Example</span></span>
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a><span data-ttu-id="8baaa-147">nx_ptp_client_master_info_get</span><span class="sxs-lookup"><span data-stu-id="8baaa-147">nx_ptp_client_master_info_get</span></span>

<span data-ttu-id="8baaa-148">마스터 클록 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-148">Get master clock information.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-149">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-149">Prototype</span></span>

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a><span data-ttu-id="8baaa-150">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-150">Description</span></span>
<span data-ttu-id="8baaa-151">이 서비스는 마스터 클록의 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-151">This service gets information of master clock.</span></span> <span data-ttu-id="8baaa-152">마스터 제어 블록은 이벤트 콜백 함수를 통해 사용자 애플리케이션에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-152">The master control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-153">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-153">Input Parameters</span></span>
* <span data-ttu-id="8baaa-154">**master_ptr** PTP 마스터 클록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-154">**master_ptr** Pointer to PTP master clock</span></span>
* <span data-ttu-id="8baaa-155">**주소** 마스터 클록의 주소</span><span class="sxs-lookup"><span data-stu-id="8baaa-155">**address** Address of master clock</span></span>
* <span data-ttu-id="8baaa-156">**port_identity** PTP 마스터 포트 및 ID</span><span class="sxs-lookup"><span data-stu-id="8baaa-156">**port_identity** PTP master port and identity</span></span>
* <span data-ttu-id="8baaa-157">**port_identity_length** PTP 마스터 포트 및 ID의 길이</span><span class="sxs-lookup"><span data-stu-id="8baaa-157">**port_identity_length** Length of PTP master port and identity</span></span>
* <span data-ttu-id="8baaa-158">**priority1** PTP 마스터 클록의 Priority1</span><span class="sxs-lookup"><span data-stu-id="8baaa-158">**priority1** Priority1 of PTP master clock</span></span>
* <span data-ttu-id="8baaa-159">**priority2** PTP 마스터 클록의 Priority2</span><span class="sxs-lookup"><span data-stu-id="8baaa-159">**priority2** Priority2 of PTP master clock</span></span>
* <span data-ttu-id="8baaa-160">**clock_class** PTP 마스터 클록의 클래스</span><span class="sxs-lookup"><span data-stu-id="8baaa-160">**clock_class** Class of PTP master clock</span></span>
* <span data-ttu-id="8baaa-161">**clock_accuracy** PTP 마스터 클록의 정확도</span><span class="sxs-lookup"><span data-stu-id="8baaa-161">**clock_accuracy** Accuracy of PTP master clock</span></span>
* <span data-ttu-id="8baaa-162">**clock_variance** PTP 마스터 클록의 분산</span><span class="sxs-lookup"><span data-stu-id="8baaa-162">**clock_variance** Variance of PTP master clock</span></span>
* <span data-ttu-id="8baaa-163">**grandmaster_identity** Grandmaster 클록의 ID</span><span class="sxs-lookup"><span data-stu-id="8baaa-163">**grandmaster_identity** Identity of grandmaster clock</span></span>
* <span data-ttu-id="8baaa-164">**grandmaster_identity_length** Grandmaster ID의 길이</span><span class="sxs-lookup"><span data-stu-id="8baaa-164">**grandmaster_identity_length** Length of grandmaster Identity</span></span>
* <span data-ttu-id="8baaa-165">**steps_removed** PTP 헤더에서 제거된 단계</span><span class="sxs-lookup"><span data-stu-id="8baaa-165">**steps_removed** Steps removed from PTP header</span></span>
* <span data-ttu-id="8baaa-166">**time_source** Grandmaster 클록에서 사용하는 타이머의 소스입니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-166">**time_source** The source of timer used by grandmaster clock</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-167">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-167">Return Values</span></span>
* <span data-ttu-id="8baaa-168">**NX_SUCCESS** (0x00) 마스터 클록 정보 가져오기에 성공</span><span class="sxs-lookup"><span data-stu-id="8baaa-168">**NX_SUCCESS** (0x00) Get master clock information successfully</span></span>
* <span data-ttu-id="8baaa-169">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-169">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-170">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-170">Allowed From</span></span>
<span data-ttu-id="8baaa-171">스레드</span><span class="sxs-lookup"><span data-stu-id="8baaa-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-172">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-172">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a><span data-ttu-id="8baaa-173">nx_ptp_client_packet_timestamp_notify</span><span class="sxs-lookup"><span data-stu-id="8baaa-173">nx_ptp_client_packet_timestamp_notify</span></span>

<span data-ttu-id="8baaa-174">PTP 클라이언트에 패킷의 타임스탬프를 알립니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-174">Notify PTP client the timestamp of the packet.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-175">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-175">Prototype</span></span>

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a><span data-ttu-id="8baaa-176">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-176">Description</span></span>
<span data-ttu-id="8baaa-177">이 서비스는 패킷이 타임스탬프와 함께 전송됨을 PTP 클라이언트에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-177">This service notifies the PTP client that packet is transmitted with timestamp.</span></span> <span data-ttu-id="8baaa-178">이 서비스는 네트워크 드라이버용으로 설계되었으며 패킷이 전송될 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-178">This service is designed for network driver and invoked when the packet is transmitted.</span></span> <span data-ttu-id="8baaa-179">일반적으로 하드웨어가 타임스탬프를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-179">The timestamp is usually generated by hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-180">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-180">Input Parameters</span></span>
* <span data-ttu-id="8baaa-181">**client_ptr** 만들 PTP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-181">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8baaa-182">**packet_ptr** 전송되는 PTP 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-182">**packet_ptr** Pointer to PTP packet that is transmitted</span></span>
* <span data-ttu-id="8baaa-183">**timestamp_ptr** PTP 패킷의 타임스탬프에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-183">**timestamp_ptr** Pointer to timestamp of PTP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-184">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-184">Return Values</span></span>
<span data-ttu-id="8baaa-185">없음</span><span class="sxs-lookup"><span data-stu-id="8baaa-185">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-186">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-186">Allowed From</span></span>
<span data-ttu-id="8baaa-187">스레드</span><span class="sxs-lookup"><span data-stu-id="8baaa-187">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-188">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-188">Example</span></span>
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a><span data-ttu-id="8baaa-189">nx_ptp_client_soft_clock_callback</span><span class="sxs-lookup"><span data-stu-id="8baaa-189">nx_ptp_client_soft_clock_callback</span></span>

<span data-ttu-id="8baaa-190">PTP 클록의 소프트웨어 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-190">Software implementation of a PTP clock.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-191">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-191">Prototype</span></span>

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a><span data-ttu-id="8baaa-192">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-192">Description</span></span>
<span data-ttu-id="8baaa-193">이 콜백 함수는 시뮬레이션된 낮은 해상도의 PTP 클록 원본으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-193">This callback function serves as a simulated low resolution clock source for PTP.</span></span> <span data-ttu-id="8baaa-194">이 루틴은 참조로 제공되며 프로덕션에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-194">This routine is provided as a reference and cannot be used for production.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-195">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-195">Input Parameters</span></span>
* <span data-ttu-id="8baaa-196">**client_ptr** 만들 PTP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-196">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8baaa-197">**작업** 콜백 작업, 유효한 값은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-197">**operation** Callback operation, valid values are defined as:</span></span>
  * <span data-ttu-id="8baaa-198">**NX_PTP_CLIENT_CLOCK_INIT** 클록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-198">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="8baaa-199">**NX_PTP_CLIENT_CLOCK_SET** `time_ptr`(으)로 지정된 현재 타임스탬프를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-199">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="8baaa-200">**NX_PTP_CLIENT_CLOCK_GET** `time_ptr`(으)로 현재 타임스탬프를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-200">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="8baaa-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** `packet_ptr`에서 `time_ptr`(으)로 타임스탬프를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="8baaa-202">**NX_PTP_CLIENT_CLOCK_ADJUST** 현재 타임스탬프를 *1* 초 미만으로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-202">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="8baaa-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** 전송 시 PTP 클라이언트에 타임스탬프를 알리도록 하는 `packet_ptr`을(를) 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="8baaa-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** 소프트 타이머를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="8baaa-205">하드웨어 클록에서 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-205">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="8baaa-206">**time_ptr** 타임스탬프를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-206">**time_ptr** Pointer to timestamp.</span></span>
* <span data-ttu-id="8baaa-207">**packet_ptr** 패킷을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-207">**packet_ptr** Pointer to packet.</span></span>
* <span data-ttu-id="8baaa-208">**callback_data** 불투명 콜백 데이터를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-208">**callback_data** Pointer to opaque callback data.</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-209">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-209">Return Values</span></span>
* <span data-ttu-id="8baaa-210">**NX_SUCCESS** (0X00) 작업 성공</span><span class="sxs-lookup"><span data-stu-id="8baaa-210">**NX_SUCCESS** (0x00) Operation successfully</span></span>
* <span data-ttu-id="8baaa-211">**NX_PTP_PARAM_ERROR** (0xD03) 잘못된 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-211">**NX_PTP_PARAM_ERROR** (0xD03) Invalid parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-212">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-212">Allowed From</span></span>
<span data-ttu-id="8baaa-213">PTP 내부</span><span class="sxs-lookup"><span data-stu-id="8baaa-213">PTP internal</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-214">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-214">Example</span></span>
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a><span data-ttu-id="8baaa-215">nx_ptp_client_start</span><span class="sxs-lookup"><span data-stu-id="8baaa-215">nx_ptp_client_start</span></span>

<span data-ttu-id="8baaa-216">PTP 클라이언트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-216">Start PTP client.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-217">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-217">Prototype</span></span>

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a><span data-ttu-id="8baaa-218">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-218">Description</span></span>
<span data-ttu-id="8baaa-219">이 서비스는 이전에 만든 PTP 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-219">This service starts a previously created PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-220">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-220">Input Parameters</span></span>
* <span data-ttu-id="8baaa-221">**client_ptr** 만들 PTP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-221">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8baaa-222">**client_port_identity_ptr** 클라이언트 포트 및 ID에 대한 포인터입니다. NULL이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-222">**client_port_identity_ptr** Pointer to client port and identity, it can be NULL</span></span>
* <span data-ttu-id="8baaa-223">**client_port_identity_length** 클라이언트 포트 및 ID의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-223">**client_port_identity_length** Length of client port and identity.</span></span> <span data-ttu-id="8baaa-224">client_port_identity_ptr이 NULL이거나 NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)인 경우 0이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-224">It must be 0 if client_port_identity_ptr is NULL or NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span></span>
* <span data-ttu-id="8baaa-225">**도메인** PTP 클록 도메인</span><span class="sxs-lookup"><span data-stu-id="8baaa-225">**domain** PTP clock domain</span></span>
* <span data-ttu-id="8baaa-226">**transport_specific** 4비트 전송 관련</span><span class="sxs-lookup"><span data-stu-id="8baaa-226">**transport_specific** 4 bits of transport specific</span></span>
* <span data-ttu-id="8baaa-227">**event_callback** 이벤트에서 호출되는 콜백 함수</span><span class="sxs-lookup"><span data-stu-id="8baaa-227">**event_callback** Callback function invoked on event</span></span>
* <span data-ttu-id="8baaa-228">**event_callback_data** 이벤트 콜백에 대한 데이터</span><span class="sxs-lookup"><span data-stu-id="8baaa-228">**event_callback_data** Data for the event callback</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-229">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-229">Return Values</span></span>
* <span data-ttu-id="8baaa-230">**NX_SUCCESS** (0x00) 클라이언트가 시작됨</span><span class="sxs-lookup"><span data-stu-id="8baaa-230">**NX_SUCCESS** (0x00) Client successfully started</span></span>
* <span data-ttu-id="8baaa-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP 클라이언트가 이미 시작됨</span><span class="sxs-lookup"><span data-stu-id="8baaa-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="8baaa-232">**status** NetX Duo 및 ThreadX 서비스 호출의 완료 상태</span><span class="sxs-lookup"><span data-stu-id="8baaa-232">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="8baaa-233">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-233">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-234">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-234">Allowed From</span></span>
<span data-ttu-id="8baaa-235">스레드</span><span class="sxs-lookup"><span data-stu-id="8baaa-235">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-236">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-236">Example</span></span>
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a><span data-ttu-id="8baaa-237">nx_ptp_client_stop</span><span class="sxs-lookup"><span data-stu-id="8baaa-237">nx_ptp_client_stop</span></span>

<span data-ttu-id="8baaa-238">PTP 클라이언트를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-238">Stop PTP client.</span></span>  <span data-ttu-id="8baaa-239">PTP 클라이언트를 중지한 후에는 PTP 패킷을 처리 하지 않으며 PTP 패킷을 전송하지도 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-239">After the PTP client is stopped, it does not process PTP packets, nor does it transmit PTP packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-240">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-240">Prototype</span></span>

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="8baaa-241">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-241">Description</span></span>
<span data-ttu-id="8baaa-242">이 서비스는 이전에 만들어서 시작한 PTP 클라이언트 인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-242">This service stops a previously created and started PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-243">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-243">Input Parameters</span></span>
* <span data-ttu-id="8baaa-244">**client_ptr** 중지할 PTP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-244">**client_ptr** Pointer to PTP client to stop</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-245">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-245">Return Values</span></span>
* <span data-ttu-id="8baaa-246">**NX_SUCCESS** (0x00) 클라이언트를 만듦</span><span class="sxs-lookup"><span data-stu-id="8baaa-246">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>
* <span data-ttu-id="8baaa-247">**NX_PTP_CLIENT_NOT_STARTED** (0xD01) 클라이언트가 시작되지 않음</span><span class="sxs-lookup"><span data-stu-id="8baaa-247">**NX_PTP_CLIENT_NOT_STARTED** (0xD01) Client not started</span></span>
* <span data-ttu-id="8baaa-248">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-248">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-249">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-249">Allowed From</span></span>
<span data-ttu-id="8baaa-250">스레드</span><span class="sxs-lookup"><span data-stu-id="8baaa-250">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-251">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-251">Example</span></span>
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a><span data-ttu-id="8baaa-252">nx_ptp_client_sync_info_get</span><span class="sxs-lookup"><span data-stu-id="8baaa-252">nx_ptp_client_sync_info_get</span></span>

<span data-ttu-id="8baaa-253">동기화 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-253">Get Sync information.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-254">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-254">Prototype</span></span>

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a><span data-ttu-id="8baaa-255">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-255">Description</span></span>
<span data-ttu-id="8baaa-256">이 서비스는 동기화 메시지에 대한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-256">This service gets information of Sync message.</span></span> <span data-ttu-id="8baaa-257">동기화 제어 블록은 이벤트 콜백 함수를 통해 사용자 애플리케이션에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-257">The Sync control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-258">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-258">Input Parameters</span></span>
* <span data-ttu-id="8baaa-259">**client_ptr** 만들 PTP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-259">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8baaa-260">**플래그** 동기화 메시지의 플래그</span><span class="sxs-lookup"><span data-stu-id="8baaa-260">**flags** Flags in Sync message</span></span>
* <span data-ttu-id="8baaa-261">**utc_offset** TAI와 UTC 사이의 오프셋</span><span class="sxs-lookup"><span data-stu-id="8baaa-261">**utc_offset** Offset between TAI and UTC</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-262">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-262">Return Values</span></span>
* <span data-ttu-id="8baaa-263">**NX_SUCCESS** (0X00) 동기화 정보를 가져옴</span><span class="sxs-lookup"><span data-stu-id="8baaa-263">**NX_SUCCESS** (0x00) Get Sync information successfully</span></span>
* <span data-ttu-id="8baaa-264">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-264">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-265">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-265">Allowed From</span></span>
<span data-ttu-id="8baaa-266">스레드</span><span class="sxs-lookup"><span data-stu-id="8baaa-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-267">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-267">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a><span data-ttu-id="8baaa-268">nx_ptp_client_time_get</span><span class="sxs-lookup"><span data-stu-id="8baaa-268">nx_ptp_client_time_get</span></span>

<span data-ttu-id="8baaa-269">현재 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-269">Get current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-270">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-270">Prototype</span></span>

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="8baaa-271">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-271">Description</span></span>
<span data-ttu-id="8baaa-272">이 서비스는 PTP 클록의 현재 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-272">This service gets the current value of the PTP clock.</span></span> <span data-ttu-id="8baaa-273">이는 PTP 클라이언트를 마스터 클록과 동기화하지 않아도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-273">It is available no matter PTP client is synchronized with master clock or not.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-274">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-274">Input Parameters</span></span>
* <span data-ttu-id="8baaa-275">**client_ptr** 만들 PTP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-275">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8baaa-276">**time_ptr** PTP 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-276">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-277">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-277">Return Values</span></span>
* <span data-ttu-id="8baaa-278">**NX_SUCCESS** (0x00) 클라이언트를 만듦</span><span class="sxs-lookup"><span data-stu-id="8baaa-278">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="8baaa-279">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-279">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-280">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-280">Allowed From</span></span>
<span data-ttu-id="8baaa-281">스레드</span><span class="sxs-lookup"><span data-stu-id="8baaa-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-282">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-282">Example</span></span>
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a><span data-ttu-id="8baaa-283">nx_ptp_client_time_set</span><span class="sxs-lookup"><span data-stu-id="8baaa-283">nx_ptp_client_time_set</span></span>

<span data-ttu-id="8baaa-284">현재 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-284">Set current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-285">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-285">Prototype</span></span>

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="8baaa-286">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-286">Description</span></span>
<span data-ttu-id="8baaa-287">이 서비스는 PTP 클록의 현재 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-287">This service sets the current value of the PTP clock.</span></span> <span data-ttu-id="8baaa-288">이는 PTP 클라이언트를 시작하기 전에 호출되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-288">It must be invoked before PTP client starts.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-289">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-289">Input Parameters</span></span>
* <span data-ttu-id="8baaa-290">**client_ptr** 만들 PTP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-290">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="8baaa-291">**time_ptr** PTP 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-291">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-292">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-292">Return Values</span></span>
* <span data-ttu-id="8baaa-293">**NX_SUCCESS** (0x00) 클라이언트를 만듦</span><span class="sxs-lookup"><span data-stu-id="8baaa-293">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="8baaa-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP 클라이언트가 이미 시작됨</span><span class="sxs-lookup"><span data-stu-id="8baaa-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="8baaa-295">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-295">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-296">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-296">Allowed From</span></span>
<span data-ttu-id="8baaa-297">스레드</span><span class="sxs-lookup"><span data-stu-id="8baaa-297">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-298">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-298">Example</span></span>
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a><span data-ttu-id="8baaa-299">nx_ptp_client_utility_convert_time_to_date</span><span class="sxs-lookup"><span data-stu-id="8baaa-299">nx_ptp_client_utility_convert_time_to_date</span></span>

<span data-ttu-id="8baaa-300">PTP 시간을 UTC 날짜 및 시간으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-300">Convert PTP time to a UTC date and time.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-301">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-301">Prototype</span></span>

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a><span data-ttu-id="8baaa-302">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-302">Description</span></span>
<span data-ttu-id="8baaa-303">이 서비스는 PTP 시간을 UTC 날짜 및 시간으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-303">This service converts PTP time to a UTC date and time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-304">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-304">Input Parameters</span></span>
* <span data-ttu-id="8baaa-305">**time_ptr** PTP 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-305">**time_ptr** Pointer to PTP time</span></span>
* <span data-ttu-id="8baaa-306">**오프셋** PTP 시간을 추가하기 위한 부호가 있는 두 번째 오프셋</span><span class="sxs-lookup"><span data-stu-id="8baaa-306">**offset** Signed second offset to add the PTP time</span></span>
* <span data-ttu-id="8baaa-307">**date_time_ptr** 결과 날짜에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-307">**date_time_ptr** Pointer to resulting date</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-308">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-308">Return Values</span></span>
* <span data-ttu-id="8baaa-309">**NX_SUCCESS** (0x00) 클라이언트를 만듦</span><span class="sxs-lookup"><span data-stu-id="8baaa-309">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="8baaa-310">**결과 날짜에 대한 포인터** (0xD03) 잘못된 입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-310">**Pointer to resulting date** (0xD03) Invalid input parameter</span></span>
* <span data-ttu-id="8baaa-311">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-311">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-312">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-312">Allowed From</span></span>
<span data-ttu-id="8baaa-313">스레드</span><span class="sxs-lookup"><span data-stu-id="8baaa-313">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-314">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-314">Example</span></span>
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a><span data-ttu-id="8baaa-315">nx_ptp_client_utility_time_diff</span><span class="sxs-lookup"><span data-stu-id="8baaa-315">nx_ptp_client_utility_time_diff</span></span>

<span data-ttu-id="8baaa-316">두 개의 PTP 시간을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-316">Diff two PTP times.</span></span>

### <a name="prototype"></a><span data-ttu-id="8baaa-317">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8baaa-317">Prototype</span></span>

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a><span data-ttu-id="8baaa-318">Description</span><span class="sxs-lookup"><span data-stu-id="8baaa-318">Description</span></span>
<span data-ttu-id="8baaa-319">이 서비스는 두 PTP 시간 사이의 차이를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="8baaa-319">This service computes the difference between two PTP times.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8baaa-320">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-320">Input Parameters</span></span>
* <span data-ttu-id="8baaa-321">**time1_ptr** 첫 번째 PTP 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-321">**time1_ptr** Pointer to first PTP time</span></span>
* <span data-ttu-id="8baaa-322">**time2_ptr** 두 번째 PTP 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-322">**time2_ptr** Pointer to second PTP time</span></span>
* <span data-ttu-id="8baaa-323">**result_ptr** 결과 time1-time2에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8baaa-323">**result_ptr** Pointer to result time1-time2</span></span>

### <a name="return-values"></a><span data-ttu-id="8baaa-324">반환 값</span><span class="sxs-lookup"><span data-stu-id="8baaa-324">Return Values</span></span>
* <span data-ttu-id="8baaa-325">**NX_SUCCESS** (0x00) 클라이언트를 만듦</span><span class="sxs-lookup"><span data-stu-id="8baaa-325">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="8baaa-326">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8baaa-326">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8baaa-327">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="8baaa-327">Allowed From</span></span>
<span data-ttu-id="8baaa-328">스레드</span><span class="sxs-lookup"><span data-stu-id="8baaa-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8baaa-329">예제</span><span class="sxs-lookup"><span data-stu-id="8baaa-329">Example</span></span>
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```