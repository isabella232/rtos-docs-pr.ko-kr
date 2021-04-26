---
title: 3장 - Azure RTOS NetX Duo SNTP 클라이언트 서비스 설명
description: 이 장에서는 아래에 나열된 모든 NetX Duo SNTP 클라이언트 서비스를 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810561"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a><span data-ttu-id="114c9-103">3장 - Azure RTOS NetX Duo SNTP 클라이언트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="114c9-103">Chapter 3 - Description of Azure RTOS NetX Duo SNTP Client Services</span></span>

<span data-ttu-id="114c9-104">이 장에서는 아래에 나열된 모든 Azure RTOS NetX Duo SNTP 클라이언트 서비스를 알파벳 순서로 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-104">This chapter contains a description of all Azure RTOS NetX Duo SNTP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="114c9-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="114c9-106">**nx_sntp_client_create**: *SNTP 클라이언트 만들기*</span><span class="sxs-lookup"><span data-stu-id="114c9-106">**nx_sntp_client_create**: *Create the SNTP Client*</span></span>
- <span data-ttu-id="114c9-107">**nx_sntp_client_delete**: *SNTP 클라이언트 삭제*</span><span class="sxs-lookup"><span data-stu-id="114c9-107">**nx_sntp_client_delete**: *Delete the SNTP Client*</span></span>
- <span data-ttu-id="114c9-108">**nx_sntp_client_get_local_time**: *SNTP 클라이언트 로컬 시간 가져오기*</span><span class="sxs-lookup"><span data-stu-id="114c9-108">**nx_sntp_client_get_local_time**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="114c9-109">**nx_sntp_client_get_local_time_extended**: *SNTP 클라이언트 로컬 시간 가져오기*</span><span class="sxs-lookup"><span data-stu-id="114c9-109">**nx_sntp_client_get_local_time_extended**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="114c9-110">**nx_sntp_client_initialize_broadcast**: *IPv4 브로드캐스트 작업을 위해 클라이언트 초기화*</span><span class="sxs-lookup"><span data-stu-id="114c9-110">**nx_sntp_client_initialize_broadcast**: *Initialize Client for IPv4 broadcast operation*</span></span>
- <span data-ttu-id="114c9-111">**nxd_sntp_client_initialize_broadcast**: *IPv6 또는 IPv4 브로드캐스트 작업을 위해 클라이언트 초기화*</span><span class="sxs-lookup"><span data-stu-id="114c9-111">**nxd_sntp_client_initialize_broadcast**: *Initialize Client for IPv6 or IPv4 broadcast operation*</span></span>
- <span data-ttu-id="114c9-112">**nx_sntp_client_initialize_unicast**: *IPv4 유니캐스트 작업을 위해 클라이언트 초기화*</span><span class="sxs-lookup"><span data-stu-id="114c9-112">**nx_sntp_client_initialize_unicast**: *Initialize Client for IPv4 unicast operation*</span></span>
- <span data-ttu-id="114c9-113">**nxd_sntp_client_initialize_unicast**: *IPv4 또는 IPv6 유니캐스트 작업을 위해 클라이언트 초기화*</span><span class="sxs-lookup"><span data-stu-id="114c9-113">**nxd_sntp_client_initialize_unicast**: *Initialize Client for IPv4 or IPv6 unicast operation*</span></span>
- <span data-ttu-id="114c9-114">**nx_sntp_client_receiving_udpates**: *클라이언트가 현재 유효한 SNTP 업데이트를 받고 있음*</span><span class="sxs-lookup"><span data-stu-id="114c9-114">**nx_sntp_client_receiving_udpates**: *Client is currently receiving valid SNTP updates*</span></span>
- <span data-ttu-id="114c9-115">**nx_sntp_client_request_unicast_time**: *유니캐스트 요청을 NTP 서버로 직접 보내기*</span><span class="sxs-lookup"><span data-stu-id="114c9-115">**nx_sntp_client_request_unicast_time**: *Send a unicast request directly to the NTP Server*</span></span>
- <span data-ttu-id="114c9-116">**nx_sntp_client_run_broadcast**: *브로드캐스트 모드로 클라이언트 실행* .</span><span class="sxs-lookup"><span data-stu-id="114c9-116">**nx_sntp_client_run_broadcast**: *Run the Client in broadcast mode*</span></span>
- <span data-ttu-id="114c9-117">**nx_sntp_client_run_unicast**: *클라이언트를 유니캐스트 모드로 실행*</span><span class="sxs-lookup"><span data-stu-id="114c9-117">**nx_sntp_client_run_unicast**: *Run the Client in unicast mode*</span></span>
- <span data-ttu-id="114c9-118">**nx_sntp_client_set_local_time**: *SNTP 클라이언트 초기 로컬 시간 설정*</span><span class="sxs-lookup"><span data-stu-id="114c9-118">**nx_sntp_client_set_local_time**: *Set SNTP Client initial local time*</span></span>
- <span data-ttu-id="114c9-119">**nx_SNTP_client_set_time_update_notify**: *SNTP 업데이트 콜백 설정*</span><span class="sxs-lookup"><span data-stu-id="114c9-119">**nx_sntp_client_set_time_update_notify**: *Set the SNTP update callback*</span></span>
- <span data-ttu-id="114c9-120">**nx_SNTP_client_stop**: *SNTP 클라이언트 스레드 중지*</span><span class="sxs-lookup"><span data-stu-id="114c9-120">**nx_sntp_client_stop**: *Stop the SNTP Client thread*</span></span>
- <span data-ttu-id="114c9-121">**nx_sntp_client_utility_display_date_and_time**: *NTP 시간(초) 표시*</span><span class="sxs-lookup"><span data-stu-id="114c9-121">**nx_sntp_client_utility_display_date_and_time**: *Display NTP time in seconds*</span></span>
- <span data-ttu-id="114c9-122">**nx_sntp_client_utility_msecs_to_fraction**: *밀리초를 NTP 분율 구성 요소로 변환*</span><span class="sxs-lookup"><span data-stu-id="114c9-122">**nx_sntp_client_utility_msecs_to_fraction**: *Convert milliseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="114c9-123">**nx_sntp_client_utility_usecs_to_fraction**: *마이크로초를 NTP 분율 구성 요소로 변환*</span><span class="sxs-lookup"><span data-stu-id="114c9-123">**nx_sntp_client_utility_usecs_to_fraction**: *Convert microseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="114c9-124">**nx_sntp_client_utility_fraction_to_usecs**: *NTP 분율 구성 요소를 마이크로초로 변환*</span><span class="sxs-lookup"><span data-stu-id="114c9-124">**nx_sntp_client_utility_fraction_to_usecs**: *Convert an NTP fraction component to microseconds*</span></span>


## <a name="nx_sntp_client_create"></a><span data-ttu-id="114c9-125">nx_sntp_client_create</span><span class="sxs-lookup"><span data-stu-id="114c9-125">nx_sntp_client_create</span></span>

<span data-ttu-id="114c9-126">SNTP 클라이언트 만들기</span><span class="sxs-lookup"><span data-stu-id="114c9-126">Create an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-127">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-127">Prototype</span></span>

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a><span data-ttu-id="114c9-128">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-128">Description</span></span>

<span data-ttu-id="114c9-129">이 서비스는 SNTP 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-129">This service creates an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-130">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-130">Input Parameters</span></span>

- <span data-ttu-id="114c9-131">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-131">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="114c9-132">**client_ptr** 클라이언트 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-132">**ip_ptr** Pointer to Client IP instance</span></span>

- <span data-ttu-id="114c9-133">**iface_index** SNTP 네트워크 인터페이스에 대한 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-133">**iface_index** Index to SNTP network interface</span></span>

- <span data-ttu-id="114c9-134">**packet_pool_ptr** 클라이언트 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-134">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="114c9-135">**leap_second_handler** 임박한 윤초에 대한 애플리케이션 응답의 콜백입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-135">**leap_second_handler** Callback for application response to impending leap second</span></span>

- <span data-ttu-id="114c9-136">**kiss_of_death_handler** 수신 Kiss of Death 패킷에 대한 애플리케이션 응답의 콜백입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-136">**kiss_of_death_handler** Callback for application response to receiving Kiss of Death packet</span></span>

- <span data-ttu-id="114c9-137">**random_number_generator** 난수 생성기 서비스에 대한 콜백입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-137">**random_number_generator** Callback to random number generator service</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-138">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-138">Return Values</span></span>

- <span data-ttu-id="114c9-139">**NX_SUCCESS**(0x00) 클라이언트를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-139">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="114c9-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD**(0xD2A) 잘못된 포인터가 아닌 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) Invalid non pointer input</span></span>

- <span data-ttu-id="114c9-141">NX_PTR_ERROR (0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-141">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="114c9-142">NX_INVALID_INTERFACE(0x4C) 잘못된 네트워크 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-142">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-143">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-143">Allowed From</span></span>

<span data-ttu-id="114c9-144">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-145">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-145">Example</span></span>

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a><span data-ttu-id="114c9-146">nx_sntp_client_delete</span><span class="sxs-lookup"><span data-stu-id="114c9-146">nx_sntp_client_delete</span></span>

<span data-ttu-id="114c9-147">SNTP 클라이언트 삭제</span><span class="sxs-lookup"><span data-stu-id="114c9-147">Delete an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-148">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-148">Prototype</span></span>

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="114c9-149">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-149">Description</span></span>

<span data-ttu-id="114c9-150">이 서비스는 SNTP 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-150">This service deletes an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-151">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-151">Input Parameters</span></span>

- <span data-ttu-id="114c9-152">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-152">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-153">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-153">Return Values</span></span>

- <span data-ttu-id="114c9-154">**NX_SUCCESS**(0x00) 클라이언트를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-154">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="114c9-155">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-155">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="114c9-156">NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-156">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-157">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-157">Allowed From</span></span>

<span data-ttu-id="114c9-158">스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-159">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-159">Example</span></span>

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a><span data-ttu-id="114c9-160">nx_sntp_client_get_local_time</span><span class="sxs-lookup"><span data-stu-id="114c9-160">nx_sntp_client_get_local_time</span></span>

<span data-ttu-id="114c9-161">SNTP 클라이언트 로컬 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="114c9-161">Get the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-162">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-162">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a><span data-ttu-id="114c9-163">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-163">Description</span></span>

<span data-ttu-id="114c9-164">이 서비스는 문자열 메시지 형식으로 데이터를 수신하는 옵션 버퍼 포인터 입력을 사용하여 SNTP 클라이언트 로컬 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-164">This service gets the SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

<span data-ttu-id="114c9-165">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-165">This service is deprecated.</span></span> <span data-ttu-id="114c9-166">개발자는 nx_SNTP_client_get_local_time_extended()로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-166">Developers are encouraged to migrate to *nx_sntp_client_get_local_time_extended*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-167">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-167">Input Parameters</span></span>

- <span data-ttu-id="114c9-168">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-168">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="114c9-169">**seconds** 로컬 시간(초)에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-169">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="114c9-170">**fraction** 로컬 시간 분율 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-170">**fraction** Local time fraction component</span></span>

- <span data-ttu-id="114c9-171">**buffer** 시간 데이터를 쓸 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-171">**buffer** Pointer to buffer to write time data</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-172">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-172">Return Values</span></span>

- <span data-ttu-id="114c9-173">**NX_SUCCESS**(0x00) 클라이언트를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-173">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="114c9-174">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-174">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="114c9-175">NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-175">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-176">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-176">Allowed From</span></span>

<span data-ttu-id="114c9-177">스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-178">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-178">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a><span data-ttu-id="114c9-179">nx_sntp_client_get_local_time_extended</span><span class="sxs-lookup"><span data-stu-id="114c9-179">nx_sntp_client_get_local_time_extended</span></span>

<span data-ttu-id="114c9-180">확장된 SNTP 클라이언트 로컬 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="114c9-180">Get the extended SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-181">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-181">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a><span data-ttu-id="114c9-182">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-182">Description</span></span>

<span data-ttu-id="114c9-183">이 서비스는 문자열 메시지 형식으로 데이터를 수신하는 옵션 버퍼 포인터 입력을 사용하여 확장된 SNTP 클라이언트 로컬 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-183">This service gets the extended SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-184">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-184">Input Parameters</span></span>

- <span data-ttu-id="114c9-185">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-185">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="114c9-186">**seconds** 로컬 시간(초)에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-186">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="114c9-187">**fraction** 분율 구성 요소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-187">**fraction** Pointer to fraction component</span></span>

- <span data-ttu-id="114c9-188">**buffer** 시간 데이터를 쓸 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-188">**buffer** Pointer to buffer to write time data</span></span>

- <span data-ttu-id="114c9-189">**buffer_size** 버퍼의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-189">**buffer_size** Length of buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-190">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-190">Return Values</span></span>

- <span data-ttu-id="114c9-191">**NX_SUCCESS**(0x00) 클라이언트를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-191">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="114c9-192">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-192">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="114c9-193">NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-193">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

- <span data-ttu-id="114c9-194">NX_SIZE_ERROR(0x09) 버퍼 크기 검사가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-194">NX_SIZE_ERROR (0x09) Check buffer_size fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-195">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-195">Allowed From</span></span>

<span data-ttu-id="114c9-196">스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-197">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-197">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a><span data-ttu-id="114c9-198">nx_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="114c9-198">nx_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="114c9-199">브로드캐스트 작업을 위해 클라이언트를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-199">Initialize the Client for broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-200">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-200">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a><span data-ttu-id="114c9-201">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-201">Description</span></span>

<span data-ttu-id="114c9-202">이 서비스는 SNTP 서버 IP 주소를 설정하고 SNTP 시작 매개 변수 및 시간 제한을 초기화하여 브로드캐스트 작업을 위해 클라이언트를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-202">This service initializes the Client for broadcast operation by setting the the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="114c9-203">멀티캐스트 및 브로드캐스트 주소 중 하나라도 null이 아니면 멀티캐스트 주소가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-203">If both multicast and broadcast addresses are non-null, the multicast address is selected.</span></span> <span data-ttu-id="114c9-204">두 가지 주소가 모두 null이면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-204">If both addresses are null an error is returned.</span></span> <span data-ttu-id="114c9-205">참고로, IPv4 서버 주소만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-205">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-206">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-206">Input Parameters</span></span>

- <span data-ttu-id="114c9-207">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-207">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="114c9-208">**multicast_server_address** SNTP 멀티캐스트 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-208">**multicast_server_address** SNTP multicast address</span></span>

- <span data-ttu-id="114c9-209">**broadcast_time_server** SNTP 서버 브로드캐스트 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-209">**broadcast_time_server** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-210">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-210">Return Values</span></span>

- <span data-ttu-id="114c9-211">**NX_SUCCESS**(0x00) 클라이언트를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-211">**NX_SUCCESS** (0x00) Successful Client Creation</span></span>

- <span data-ttu-id="114c9-212">**NX_INVALID_PARAMETERS**(0x4D) 비포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-212">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="114c9-213">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-213">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="114c9-214">NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-214">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-215">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-215">Allowed From</span></span>

<span data-ttu-id="114c9-216">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-216">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-217">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-217">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a><span data-ttu-id="114c9-218">nxd_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="114c9-218">nxd_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="114c9-219">IPv4 또는 IPv6 브로드캐스트 작업을 위해 클라이언트 초기화</span><span class="sxs-lookup"><span data-stu-id="114c9-219">Initialize the Client for IPv4 or IPv6 broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-220">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-220">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a><span data-ttu-id="114c9-221">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-221">Description</span></span>

<span data-ttu-id="114c9-222">이 서비스는 SNTP 서버 IP 주소를 설정하고 SNTP 시작 매개 변수 및 시간 제한을 초기화하여 브로드캐스트 작업을 위해 클라이언트를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-222">This service initializes the Client for broadcast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="114c9-223">브로드캐스트 및 멀티캐스트 주소 포인터 중 하나라도 null이 아닌 경우 멀티캐스트 주소가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-223">If both broadcast and multicast address pointers are non null, the multicast address is selected.</span></span> <span data-ttu-id="114c9-224">두 주소 포인터가 모두 null이면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-224">If both address pointers are null, an error is returned.</span></span> <span data-ttu-id="114c9-225">IPv4 및 IPv6 주소 유형이 모두 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-225">This supports both IPv4 and IPv6 address types.</span></span> <span data-ttu-id="114c9-226">IPv6에서는 브로드캐스트를 지원하지 않으므로 브로드캐스트 주소 포인터가 IPv6로 설정되면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-226">Note that IPv6 does not support broadcast, so the broadcast address pointer is set to IPv6, an error is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-227">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-227">Input Parameters</span></span>

- <span data-ttu-id="114c9-228">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-228">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="114c9-229">**multicast_server_address** SNTP 서버 멀티캐스트 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-229">**multicast_server_address** SNTP server multicast address</span></span>

- <span data-ttu-id="114c9-230">**broadcast_server_address** SNTP 서버 브로드캐스트 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-230">**broadcast_server_address** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-231">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-231">Return Values</span></span>

- <span data-ttu-id="114c9-232">**NX_SUCCESS**(0x00) 클라이언트를 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-232">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="114c9-233">NX_SNTP_PARAM_ERROR(0xD0D) 잘못된 비포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-233">NX_SNTP_PARAM_ERROR (0xD0D) Invalid non pointer input</span></span>

- <span data-ttu-id="114c9-234">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-234">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="114c9-235">NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-235">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="114c9-236">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-236">Allowed From</span></span>

<span data-ttu-id="114c9-237">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-237">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-238">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-238">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a><span data-ttu-id="114c9-239">nx_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="114c9-239">nx_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="114c9-240">유니캐스트에서 실행되도록 SNTP 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="114c9-240">Set up the SNTP Client to run in unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-241">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-241">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a><span data-ttu-id="114c9-242">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-242">Description</span></span>

<span data-ttu-id="114c9-243">이 서비스는 SNTP 서버 IP 주소를 설정하고 SNTP 시작 매개 변수 및 시간 제한을 초기화하여 유니캐스트 작업을 위해 클라이언트를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-243">This service initializes the Client for unicast operation by setting the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="114c9-244">참고로, IPv4 서버 주소만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-244">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-245">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-245">Input Parameters</span></span>

- <span data-ttu-id="114c9-246">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-246">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="114c9-247">**unicast_time_server** SNTP 서버 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-247">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-248">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-248">Return Values</span></span>

- <span data-ttu-id="114c9-249">**NX_SUCCESS**(0x00) 클라이언트를 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-249">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="114c9-250">NX_INVALID_PARAMETERS(0x4D) 비포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-250">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="114c9-251">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-251">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="114c9-252">NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-252">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-253">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-253">Allowed From</span></span>

<span data-ttu-id="114c9-254">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-254">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-255">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-255">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a><span data-ttu-id="114c9-256">nxd_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="114c9-256">nxd_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="114c9-257">IPv4 또는 IPv6 유니캐스트에서 실행되도록 SNTP 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="114c9-257">Set up the SNTP Client to run in IPv4 or IPv6 unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-258">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-258">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a><span data-ttu-id="114c9-259">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-259">Description</span></span>

<span data-ttu-id="114c9-260">이 서비스는 SNTP 서버 IP 주소를 설정하고 SNTP 시작 매개 변수 및 시간 제한을 초기화하여 유니캐스트 작업을 위해 클라이언트를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-260">This service initializes the Client for unicast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="114c9-261">IPv4 및 IPv6 주소 유형이 모두 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-261">This supports both IPv4 and IPv6 address types.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-262">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-262">Input Parameters</span></span>

- <span data-ttu-id="114c9-263">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-263">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="114c9-264">**unicast_time_server** SNTP 서버 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-264">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-265">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-265">Return Values</span></span>

- <span data-ttu-id="114c9-266">**NX_SUCCESS**(0x00) 클라이언트를 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-266">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="114c9-267">NX_INVALID_PARAMETERS(0x4D) 비포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-267">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="114c9-268">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-268">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="114c9-269">NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-269">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-270">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-270">Allowed From</span></span>

<span data-ttu-id="114c9-271">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-271">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-272">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-272">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a><span data-ttu-id="114c9-273">nx_sntp_client_receiving_updates</span><span class="sxs-lookup"><span data-stu-id="114c9-273">nx_sntp_client_receiving_updates</span></span>

<span data-ttu-id="114c9-274">클라이언트에서 유효한 업데이트를 받는지 여부 표시</span><span class="sxs-lookup"><span data-stu-id="114c9-274">Indicate if Client is receiving valid updates</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-275">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-275">Prototype</span></span>

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a><span data-ttu-id="114c9-276">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-276">Description</span></span>

<span data-ttu-id="114c9-277">이 서비스는 클라이언트가 유효한 SNTP 업데이트를 수신하고 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-277">This service indicates if the Client is receiving valid SNTP updates.</span></span> <span data-ttu-id="114c9-278">유효한 업데이트 없이 최대 시간이 경과하거나 잘못된 연속 업데이트에 대한 제한을 초과하면 수신 상태가 false로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-278">If the maximum time lapse without a valid update or limit on consecutive invalid updates is exceeded, the receive status is returned as false.</span></span> <span data-ttu-id="114c9-279">SNTP 클라이언트가 아직 실행 중이고, 애플리케이션이 다른 유니캐스트 또는 브로드캐스트/멀티캐스트 서버를 사용하여 SNTP 클라이언트를 다시 시작하려고 하면  서비스를 사용하여 SNTP 클라이언트를 중지하고, 다른 서버에서 초기화 서비스 중 하나를 사용하여 클라이언트를 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-279">Note that the SNTP Client is still running and if the application wishes to restart the SNTP Client with another unicast or broadcast/multicast server it must stop the SNTP Client using the *nx_sntp_client_stop* service, reinitialize the Client using one of the initialize services with another server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-280">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-280">Input Parameters</span></span>

- <span data-ttu-id="114c9-281">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-281">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="114c9-282">**receive_status** 클라이언트가 유효한 업데이트를 수신하는지 나타내기 위한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-282">**receive_status** Pointer to indicator if Client is receiving valid updates.</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-283">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-283">Return Values</span></span>

- <span data-ttu-id="114c9-284">**NX_SUCCESS**(0X00) 클라이언트가 업데이트 상태를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-284">**NX_SUCCESS** (0x00) Client successfully received update status</span></span>

- <span data-ttu-id="114c9-285">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-285">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-286">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-286">Allowed From</span></span>

<span data-ttu-id="114c9-287">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-287">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-288">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-288">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a><span data-ttu-id="114c9-289">nx_sntp_client_request_unicast_time</span><span class="sxs-lookup"><span data-stu-id="114c9-289">nx_sntp_client_request_unicast_time</span></span>

<span data-ttu-id="114c9-290">유니캐스트 요청을 NTP 서버로 직접 보내기</span><span class="sxs-lookup"><span data-stu-id="114c9-290">Send a unicast request directly to the NTP Server</span></span>


### <a name="prototype"></a><span data-ttu-id="114c9-291">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-291">Prototype</span></span>

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="114c9-292">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-292">Description</span></span>

<span data-ttu-id="114c9-293">이 서비스를 사용하여 애플리케이션에서는 SNTP 클라이언트 스레드 작업과는 비동기식으로 유니캐스트 요청을 NTP 서버로 직접 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-293">This service allows the application to directly send a unicast request to the NTP server asynchronously from the SNTP Client thread task.</span></span> <span data-ttu-id="114c9-294">대기 옵션은 응답을 대기하는 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-294">The wait option specifies how long to wait for a response.</span></span> <span data-ttu-id="114c9-295">성공하면 애플리케이션은 다른 SNTP 클라이언트 서비스를 사용하여 최신 시간을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-295">If successful, the application can use other SNTP Client services to obtain the latest time.</span></span> <span data-ttu-id="114c9-296">자세한 내용은 **SNTP 비동기 유니캐스트 요청** 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="114c9-296">See section **SNTP Asynchronous Unicast Requests** for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-297">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-297">Input Parameters</span></span>

- <span data-ttu-id="114c9-298">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-298">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="114c9-299">**Wait_option** NTP 응답(타이머 틱)에 대한 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-299">**Wait_option** Wait option for NTP response in timer ticks.</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-300">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-300">Return Values</span></span>

- <span data-ttu-id="114c9-301">**NX_SUCCESS**(0X00) 클라이언트가 유니캐스트 업데이트를 성공적으로 보내고 받습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-301">**NX_SUCCESS** (0x00) Client successfully sends and receives unicast update</span></span>

- <span data-ttu-id="114c9-302">**NX_SNTP_CLIENT_NOT_STARTED**(0xD0B) 클라이언트 스레드가 시작되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-302">**NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) Client thread not started</span></span>

- <span data-ttu-id="114c9-303">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-303">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="114c9-304">NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-304">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-305">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-305">Allowed From</span></span>

<span data-ttu-id="114c9-306">스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-307">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-307">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a><span data-ttu-id="114c9-308">nx_sntp_client_run_broadcast</span><span class="sxs-lookup"><span data-stu-id="114c9-308">nx_sntp_client_run_broadcast</span></span>

<span data-ttu-id="114c9-309">브로드캐스트 모드로 클라이언트 실행</span><span class="sxs-lookup"><span data-stu-id="114c9-309">Run the Client in broadcast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-310">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-310">Prototype</span></span>

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="114c9-311">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-311">Description</span></span>

<span data-ttu-id="114c9-312">이 서비스는 클라이언트를 브로드캐스트 모드로 시작하여 SNTP 서버의 브로드캐스트를 수신 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-312">This service starts the Client in broadcast mode where it will wait to receive broadcasts from the SNTP server.</span></span> <span data-ttu-id="114c9-313">유효한 브로드캐스트 SNTP 메시지가 수신되면 업데이트 없는 최대 시간 경과에 대한 SNTP 클라이언트 제한 시간 및 수신된 잘못된 연속 메시지 수가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-313">If a valid broadcast SNTP message is received, the SNTP client timeout for maximum lapse without an update and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="114c9-314">이러한 한도를 초과하는 경우 SNTP 클라이언트는 업데이트 수신을 계속 대기하지만 서버 상태를 잘못됨으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-314">If the either of these limits are exceeded, the SNTP Client sets the server status to invalid although it will still wait to receive updates.</span></span> <span data-ttu-id="114c9-315">애플리케이션은 SNTP 클라이언트 작업에서 서버 상태를 폴링할 수 있으며, 잘못된 경우 SNTP 클라이언트를 중지하고 다른 SNTP 브로드캐스트 주소를 사용하여 다시 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-315">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP broadcast address.</span></span> <span data-ttu-id="114c9-316">유니캐스트 SNTP 서버로 전환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-316">It can also switch to a unicast SNTP server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-317">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-317">Input Parameters</span></span>

- <span data-ttu-id="114c9-318">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-318">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-319">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-319">Return Values</span></span>

- <span data-ttu-id="114c9-320">**status** --------실제 완료 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-320">**status** -------- Actual completion status</span></span>

- <span data-ttu-id="114c9-321">**NX_SNTP_CLIENT_ALREADY_STARTED**(0XD0C) 클라이언트가 이미 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-321">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="114c9-322">**NX_SNTP_CLIENT_NOT_INITIALIZED**(0xD01) 클라이언트가 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-322">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="114c9-323">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-323">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="114c9-324">NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-324">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-325">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-325">Allowed From</span></span>

<span data-ttu-id="114c9-326">스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-326">Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-327">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-327">Example</span></span>

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a><span data-ttu-id="114c9-328">nx_sntp_client_run_unicast</span><span class="sxs-lookup"><span data-stu-id="114c9-328">nx_sntp_client_run_unicast</span></span>

<span data-ttu-id="114c9-329">유니캐스트 모드에서 클라이언트 실행</span><span class="sxs-lookup"><span data-stu-id="114c9-329">Run the Client in unicast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-330">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-330">Prototype</span></span>

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="114c9-331">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-331">Description</span></span>

<span data-ttu-id="114c9-332">이 서비스는 시간 업데이트를 위해 SNTP 서버에 유니캐스트 요청을 주기적으로 전송하는 유니캐스트 모드로 클라이언트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-332">This service starts the Client in unicast mode where it periodically sends a unicast request to its SNTP Server for a time update.</span></span> <span data-ttu-id="114c9-333">유효한 SNTP 메시지가 수신되면 업데이트 없는 최대 시간 경과에 대한 SNTP 클라이언트 제한 시간, 초기 폴링 간격 및 수신된 잘못된 연속 메시지 수가 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-333">If a valid SNTP message is received, the SNTP client timeout for maximum lapse without an update, initial polling interval and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="114c9-334">이러한 한도를 초과하는 경우 SNTP 클라이언트는 계속해서 폴링하고 업데이트 수신을 대기하지만 서버 상태를 잘못됨으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-334">If the either of these limits are exceeded, the SNTP Client sets the Server status to invalid although it will still poll and wait to receive updates.</span></span> <span data-ttu-id="114c9-335">애플리케이션은 SNTP 클라이언트 작업에서 서버 상태를 폴링할 수 있으며, 잘못된 경우 SNTP 클라이언트를 중지하고 다른 SNTP 유니캐스트 주소를 사용하여 다시 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-335">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP unicast address.</span></span> <span data-ttu-id="114c9-336">브로드캐스트 SNTP 서버로 전환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-336">It can also switch to a broadcast SNTP server.</span></span>

<span data-ttu-id="114c9-337">.</span><span class="sxs-lookup"><span data-stu-id="114c9-337">.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-338">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-338">Input Parameters</span></span>

- <span data-ttu-id="114c9-339">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-339">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-340">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-340">Return Values</span></span>

- <span data-ttu-id="114c9-341">**NX_SUCCESS**(0x00) 유니캐스트 모드로 클라이언트를 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-341">**NX_SUCCESS** (0x00) Successfully started Client in unicast mode</span></span>

- <span data-ttu-id="114c9-342">**NX_SNTP_CLIENT_ALREADY_STARTED**(0XD0C) 클라이언트가 이미 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-342">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="114c9-343">**NX_SNTP_CLIENT_NOT_INITIALIZED**(0xD01) 클라이언트가 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-343">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="114c9-344">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-344">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="114c9-345">NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-345">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="114c9-346">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-346">Allowed From</span></span>

<span data-ttu-id="114c9-347">스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-347">Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-348">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-348">Example</span></span>

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a><span data-ttu-id="114c9-349">nx_sntp_client_set_local_time</span><span class="sxs-lookup"><span data-stu-id="114c9-349">nx_sntp_client_set_local_time</span></span>

<span data-ttu-id="114c9-350">SNTP 클라이언트 로컬 시간 설정</span><span class="sxs-lookup"><span data-stu-id="114c9-350">Set the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-351">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-351">Prototype</span></span>

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a><span data-ttu-id="114c9-352">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-352">Description</span></span>

<span data-ttu-id="114c9-353">이 서비스는 SNTP 형식(예: 초 및 초의 분율을 16진수 형식으로 입력하는 형식인 '분율')의 입력 시간을 사용하여 SNTP 클라이언트 로컬 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-353">This service sets the SNTP Client local time with the input time, in SNTP format e.g. seconds and ‘fraction’ which is the format for putting fractions of a second in hexadecimal format.</span></span> <span data-ttu-id="114c9-354">이 서비스는 실시간 클록과 같은 독립적인 시간 키퍼에서 SNTP 클라이언트 로컬 시간을 업데이트하기 위해 고안되었습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-354">It is intended for updating the SNTP Client local time from an independent time keeper, e.g. a real time clock.</span></span> <span data-ttu-id="114c9-355">SNTP 프로토콜은 SNTP 시간 업데이트가 있을 때 로컬 클록 시간이 '드리프트'되지 않도록 하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-355">The SNTP protocol is intended for SNTP time updates to keep local clock time from ‘drifting’.</span></span> <span data-ttu-id="114c9-356">SNTP 서버 시간 업데이트는 SNTP 클라이언트 로컬 시간에 대한 유일한 입력일 수 있지만, 애플리케이션 디바이스에 독립적인 시간 키퍼가 없는 경우라면 유일한 입력이 아닐 것입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-356">SNTP server time updates can be, but are not intended to be the sole input to the SNTP Client local time if there is no independent time keeper on the application device.</span></span>

<span data-ttu-id="114c9-357">이 API를 사용하여 SNTP 클라이언트 스레드를 시작하기 전에 SNTP 클라이언트에 기본 시간을 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-357">This API can also be used to give the SNTP Client a base time before starting the SNTP Client thread.</span></span> <span data-ttu-id="114c9-358">SNTP 클라이언트 로컬 시간이 유효한 시간 데이터에 대해 수신된 업데이트와 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-358">The SNTP Client local time is compared to received updates for valid time data.</span></span> <span data-ttu-id="114c9-359">업데이트를 처음 받을 때는 매우 큰 차이가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-359">For the first time update received, there might be a very large discrepancy.</span></span> <span data-ttu-id="114c9-360">따라서 SNTP 클라이언트가 첫 번째 업데이트에서 불일치를 무시하는 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-360">Therefore there is an option for the SNTP Client to ignore the discrepancy on the first update.</span></span> <span data-ttu-id="114c9-361">이러한 방식으로, 기본 시간 없이 SNTP 클라이언트를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-361">In this manner, the SNTP Client can start without a base time.</span></span> <span data-ttu-id="114c9-362">입력 시간은 알려진 Epoch 시간(일반적으로 인터넷에서 사용 가능)에서 얻을 수 있으며, 1900년 1월 1일 이후부터 새 'Epoch'가 시작될 2036년까지의 초 수로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-362">Input time can be obtained from known epoch times (usually available on the Internet) and are computed as the number of seconds since January 1, 1900 (until 2036 when a new ‘epoch’ will be started.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-363">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-363">Input Parameters</span></span>

- <span data-ttu-id="114c9-364">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-364">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="114c9-365">**seconds** 시간 입력의 초 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-365">**seconds** Seconds component of the time input</span></span>

- <span data-ttu-id="114c9-366">**fraction** SNTP 분율 형식의 하위 초 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-366">**fraction** Subseconds component in the SNTP fraction format</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-367">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-367">Return Values</span></span>

- <span data-ttu-id="114c9-368">**NX_SUCCESS**(0x00) 로컬 시간을 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-368">**NX_SUCCESS** (0x00) Successfully set local time</span></span>

- <span data-ttu-id="114c9-369">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-369">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-370">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-370">Allowed From</span></span>

<span data-ttu-id="114c9-371">초기화</span><span class="sxs-lookup"><span data-stu-id="114c9-371">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="114c9-372">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-372">Example</span></span>

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a><span data-ttu-id="114c9-373">nx_sntp_client_set_time_update_notify</span><span class="sxs-lookup"><span data-stu-id="114c9-373">nx_sntp_client_set_time_update_notify</span></span>

<span data-ttu-id="114c9-374">SNTP 업데이트 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="114c9-374">Set the SNTP update callback</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-375">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-375">Prototype</span></span>

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a><span data-ttu-id="114c9-376">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-376">Description</span></span>

<span data-ttu-id="114c9-377">이 서비스는 SNTP 클라이언트가 유효한 시간 업데이트를 받을 때 애플리케이션에 알리도록 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-377">This service sets callback to notify the application when the SNTP Client receives a valid time update.</span></span> <span data-ttu-id="114c9-378">실제 SNTP 메시지와 SNTP 클라이언트의 로컬 시간(일반적으로 동일함)을 NTP 형식으로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-378">It supplies the actual SNTP message and the SNTP Client’s local time (usually the same) in NTP format.</span></span> <span data-ttu-id="114c9-379">애플리케이션은 NTP 데이터를 직접 사용하거나 nx_sntp_client_utility_display_date_time 서비스를 호출하여 시간을 사람이 읽을 수 있는 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-379">The application can use the NTP data directly or call the *nx_sntp_client_utility_display_date_time service* to convert the time to human readable format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-380">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-380">Input Parameters</span></span>

- <span data-ttu-id="114c9-381">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-381">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="114c9-382">**time_update_cb** 콜백 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-382">**time_update_cb** Pointer to callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-383">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-383">Return Values</span></span>

- <span data-ttu-id="114c9-384">**NX_SUCCESS**(0x00) 콜백을 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-384">**NX_SUCCESS** (0x00) Successfully set callback</span></span>

- <span data-ttu-id="114c9-385">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-385">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-386">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-386">Allowed From</span></span>

<span data-ttu-id="114c9-387">초기화</span><span class="sxs-lookup"><span data-stu-id="114c9-387">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="114c9-388">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-388">Example</span></span>

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a><span data-ttu-id="114c9-389">nx_sntp_client_stop</span><span class="sxs-lookup"><span data-stu-id="114c9-389">nx_sntp_client_stop</span></span>

<span data-ttu-id="114c9-390">SNTP 클라이언트 스레드 중지</span><span class="sxs-lookup"><span data-stu-id="114c9-390">Stop the SNTP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-391">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-391">Prototype</span></span>

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="114c9-392">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-392">Description</span></span>

<span data-ttu-id="114c9-393">이 서비스는 SNTP 클라이언트 스레드를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-393">This service stops the SNTP Client thread.</span></span> <span data-ttu-id="114c9-394">무한 루프로 실행되는 SNTP 클라이언트 스레드 작업은 모든 반복에서 일시 중지하여 SNTP 클라이언트 상태의 제어를 해제하고 애플리케이션이 SNTP 클라이언트에서 API 호출을 수행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-394">The SNTP Client thread tasks, which runs in an infinite loop, pauses on every iteration to release control of the SNTP Client state and allow applications to make API calls on the SNTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-395">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-395">Input Parameters</span></span>

- <span data-ttu-id="114c9-396">**client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-396">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-397">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-397">Return Values</span></span>

- <span data-ttu-id="114c9-398">**NX_SUCCESS**(0X00) 클라이언트 스레드를 중지했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-398">**NX_SUCCESS** (0x00) Successful stopped Client thread</span></span>

- <span data-ttu-id="114c9-399">**NX_SNTP_CLIENT_NOT_STARTED**(0xDB) SNTP 클라이언트 스레드가 시작되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-399">**NX_SNTP_CLIENT_NOT_STARTED** (0xDB) SNTP Client thread not started</span></span>

- <span data-ttu-id="114c9-400">NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-400">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-401">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-401">Allowed From</span></span>

<span data-ttu-id="114c9-402">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-402">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-403">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-403">Example</span></span>

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a><span data-ttu-id="114c9-404">nx_sntp_client_utility_display_date_time</span><span class="sxs-lookup"><span data-stu-id="114c9-404">nx_sntp_client_utility_display_date_time</span></span>

<span data-ttu-id="114c9-405">NTP 시간을 날짜 및 시간 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="114c9-405">Convert an NTP Time to Date and Time string</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-406">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-406">Prototype</span></span>

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a><span data-ttu-id="114c9-407">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-407">Description</span></span>

<span data-ttu-id="114c9-408">이 서비스는 SNTP 클라이언트 로컬 시간을 년월일 형식으로 변환하고 제공 된 버퍼의 날짜를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-408">This service converts the SNTP Client local time to a year month date format and returns the date in the supplied buffer.</span></span> <span data-ttu-id="114c9-409">NX_SNTP_CURRENT_YEAR는 현재 클라이언트 시간과 같은 연도일 필요는 없지만 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-409">The NX_SNTP_CURRENT_YEAR need not be the same year as the current Client time but it must be defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-410">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-410">Input Parameters</span></span>

- <span data-ttu-id="114c9-411">**client_ptr** SMTP 클라이언트에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-411">**client_ptr Pointer to SNTP Client**</span></span>

- <span data-ttu-id="114c9-412">**buffer** 날짜를 저장할 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-412">**buffer** Pointer to buffer to store date</span></span>

- <span data-ttu-id="114c9-413">**length** 입력 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-413">**length** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-414">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-414">Return Values</span></span>

- <span data-ttu-id="114c9-415">**NX_SUCCESS**(0x00) 변환에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-415">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="114c9-416">**NX_SNTP_ERROR_CONVERTING_DATETIME**(0xD08) NX_SNTP_CURRENT_YEAR가 정의되지 않았거나 로컬 클라이언트 시간이 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR not defined or no local client time established</span></span>

- <span data-ttu-id="114c9-417">**NX_SNTP_INVALID_DATETIME_BUFFER**(0xD07) 버퍼 길이가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) Insufficient buffer length</span></span>


### <a name="allowed-from"></a><span data-ttu-id="114c9-418">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-418">Allowed From</span></span>

<span data-ttu-id="114c9-419">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-419">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-420">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-420">Example</span></span>

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a><span data-ttu-id="114c9-421">nx_sntp_client_utility_msecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="114c9-421">nx_sntp_client_utility_msecs_to_fraction</span></span>

<span data-ttu-id="114c9-422">밀리초를 NTP 분율 구성 요소로 변환</span><span class="sxs-lookup"><span data-stu-id="114c9-422">Convert milliseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-423">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-423">Prototype</span></span>

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a><span data-ttu-id="114c9-424">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-424">Description</span></span>

<span data-ttu-id="114c9-425">이 서비스는 입력 밀리초를 NTP 분율 구성 요소로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-425">This service converts the input milliseconds to the NTP fraction component.</span></span> <span data-ttu-id="114c9-426">이 서비스는 SNTP 클라이언트에 대한 시작 기반 시간이 있지만 NTP 초/분율 형식은 아닌 애플리케이션에서 사용하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-426">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="114c9-427">유효한 분율을 만들려면 밀리초 수가 1,000 미만이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-427">The number of milliseconds must be less than 1000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-428">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-428">Input Parameters</span></span>

- <span data-ttu-id="114c9-429">**milliseconds** 변환할 밀리초 수입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-429">**milliseconds Milliseconds to convert**</span></span>

- <span data-ttu-id="114c9-430">**fraction** 분율로 변환된 밀리초에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-430">**fraction** Pointer to milliseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-431">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-431">Return Values</span></span>

- <span data-ttu-id="114c9-432">**NX_SUCCESS**(0x00) 변환에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-432">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="114c9-433">**NX_SNTP_OVERFLOW_ERROR**(0x32) 시간을 날짜로 변환하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-433">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="114c9-434">NX_SNTP_INVALID_TIME(0xD30) 잘못된 SNTP 데이터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-434">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-435">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-435">Allowed From</span></span>

<span data-ttu-id="114c9-436">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-436">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-437">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-437">Example</span></span>

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a><span data-ttu-id="114c9-438">nx_sntp_client_utility_usecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="114c9-438">nx_sntp_client_utility_usecs_to_fraction</span></span>

<span data-ttu-id="114c9-439">마이크로초를 NTP 분율 구성 요소로 변환</span><span class="sxs-lookup"><span data-stu-id="114c9-439">Convert microseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-440">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-440">Prototype</span></span>

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a><span data-ttu-id="114c9-441">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-441">Description</span></span>

<span data-ttu-id="114c9-442">이 서비스는 입력 마이크로초를 NTP 분율 구성 요소로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-442">This service converts the input microseconds to the NTP fraction component.</span></span> <span data-ttu-id="114c9-443">이 서비스는 SNTP 클라이언트에 대한 시작 기반 시간이 있지만 NTP 초/분율 형식은 아닌 애플리케이션에서 사용하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-443">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="114c9-444">유효한 분율을 만들려면 마이크로초 수가 1,000,000 미만이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-444">The number of microseconds must be less than 1000000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-445">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-445">Input Parameters</span></span>

- <span data-ttu-id="114c9-446">**microseconds** 변환할 마이크로초입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-446">**microseconds** Microseconds to convert</span></span>

- <span data-ttu-id="114c9-447">**fraction** 분율로 변환된 마이크로초에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-447">**fraction** Pointer to microseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-448">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-448">Return Values</span></span>

- <span data-ttu-id="114c9-449">**NX_SUCCESS**(0x00) 변환에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-449">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="114c9-450">**NX_SNTP_OVERFLOW_ERROR**(0x32) 시간을 날짜로 변환하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-450">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="114c9-451">NX_SNTP_INVALID_TIME(0xD30) 잘못된 SNTP 데이터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-451">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-452">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-452">Allowed From</span></span>

<span data-ttu-id="114c9-453">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-453">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-454">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-454">Example</span></span>

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a><span data-ttu-id="114c9-455">nx_sntp_client_utility_fraction_to_usecs</span><span class="sxs-lookup"><span data-stu-id="114c9-455">nx_sntp_client_utility_fraction_to_usecs</span></span>

<span data-ttu-id="114c9-456">NTP 분율 구성 요소를 마이크로초로 변환</span><span class="sxs-lookup"><span data-stu-id="114c9-456">Convert an NTP fraction component to microseconds</span></span>

### <a name="prototype"></a><span data-ttu-id="114c9-457">프로토타입</span><span class="sxs-lookup"><span data-stu-id="114c9-457">Prototype</span></span>

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a><span data-ttu-id="114c9-458">Description</span><span class="sxs-lookup"><span data-stu-id="114c9-458">Description</span></span>

<span data-ttu-id="114c9-459">이 서비스는 입력 NTP 분율 구성 요소를 마이크로초로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-459">This service converts the input NTP fraction component to microseconds.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="114c9-460">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="114c9-460">Input Parameters</span></span>

- <span data-ttu-id="114c9-461">**fraction** 변환할 분율입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-461">**fraction Fraction to convert**</span></span>

- <span data-ttu-id="114c9-462">**microseconds** 마이크로초로 변환된 분율에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-462">**microseconds** Pointer to fraction converted to microseconds</span></span>

### <a name="return-values"></a><span data-ttu-id="114c9-463">반환 값</span><span class="sxs-lookup"><span data-stu-id="114c9-463">Return Values</span></span>

- <span data-ttu-id="114c9-464">**NX_SUCCESS**(0x00) 변환에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-464">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="114c9-465">NX_SNTP_INVALID_TIME(0xD30) 잘못된 SNTP 데이터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="114c9-465">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="114c9-466">허용 위치</span><span class="sxs-lookup"><span data-stu-id="114c9-466">Allowed From</span></span>

<span data-ttu-id="114c9-467">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="114c9-467">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="114c9-468">예제</span><span class="sxs-lookup"><span data-stu-id="114c9-468">Example</span></span>

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```