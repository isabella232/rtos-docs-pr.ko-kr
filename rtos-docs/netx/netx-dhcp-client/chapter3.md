---
title: 챕터 3 - Azure RTOS NetX DHCP 클라이언트 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX DHCP 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8a614d22eca4fe693209751d72958b7d975c64c2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811611"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a><span data-ttu-id="e6cd1-103">챕터 3 - Azure RTOS NetX DHCP 클라이언트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="e6cd1-103">Chapter 3 - Description of Azure RTOS NetX DHCP Client services</span></span>

<span data-ttu-id="e6cd1-104">이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX DHCP 서비스에 대해 알파벳 순서로 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-104">This chapter contains a description of all Azure RTOS NetX DHCP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="e6cd1-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="e6cd1-106">**nx_dhcp_create**: *DHCP 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>

- <span data-ttu-id="e6cd1-107">**nx_dhcp_clear_broadcast_flag**: 클라이언트 메시지에서 브로드캐스트 플래그 지우기</span><span class="sxs-lookup"><span data-stu-id="e6cd1-107">**nx_dhcp_clear_broadcast_flag**: Clear broadcast flag on Client messages</span></span>

- <span data-ttu-id="e6cd1-108">**nx_dhcp_delete**: *DHCP 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>

- <span data-ttu-id="e6cd1-109">**nx_dhcp_decline**: *서버에 거부 메시지* 보내기</span><span class="sxs-lookup"><span data-stu-id="e6cd1-109">**nx_dhcp_decline**: Send *Decline message to server*</span></span>

- <span data-ttu-id="e6cd1-110">**nx_dhcp_force_renew**: *강제 갱신 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-110">**nx_dhcp_force_renew**: *Send force renew message*</span></span>

- <span data-ttu-id="e6cd1-111">**nx_dhcp_packet_pool_set**: *DHCP 클라이언트 패킷 풀 설정*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-111">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>

- <span data-ttu-id="e6cd1-112">**nx_dhcp_release**: *서버에 릴리스 메시지* 보내기</span><span class="sxs-lookup"><span data-stu-id="e6cd1-112">**nx_dhcp_release**: Send *Release message to server*</span></span>

- <span data-ttu-id="e6cd1-113">**nx_dhcp_reinitialize**: *DHCP 클라이언트 네트워크 매개 변수 지우기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>

- <span data-ttu-id="e6cd1-114">**nx_dhcp_request_client_ip**: *특정 IP 주소 지정*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>

- <span data-ttu-id="e6cd1-115">**nx_dhcp_send_request**: *서버에 DHCP 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>

- <span data-ttu-id="e6cd1-116">**nx_dhcp_server_address_get**: *DHCP 클라이언트의 DHCP 서버 주소 검색*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-116">**nx_dhcp_server_address_get**: *Retrieve DHCP Client’s DHCP server address*</span></span>

- <span data-ttu-id="e6cd1-117">**nx_dhcp_set_interface_index**: *클라이언트 네트워크 인터페이스 지정*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-117">**nx_dhcp_set_interface_index**: *Specify the Client network interface*</span></span>

- <span data-ttu-id="e6cd1-118">**nx_dhcp_start**: *DHCP 처리 시작*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-118">**nx_dhcp_start**: *Start DHCP processing*</span></span>

- <span data-ttu-id="e6cd1-119">**nx_dhcp_state_change_notify**: *애플리케이션에 DHCP 상태 변경 알림*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-119">**nx_dhcp_state_change_notify**: *Notify application of DHCP state change*</span></span>

- <span data-ttu-id="e6cd1-120">**nx_dhcp_stop**: *DHCP 처리 중지*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-120">**nx_dhcp_stop**: *Stop DHCP processing*</span></span>

- <span data-ttu-id="e6cd1-121">**nx_dhcp_user_option_retrieve**: *DHCP 옵션 검색*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-121">**nx_dhcp_user_option_retrieve**: *Retrieve DHCP option*</span></span>

- <span data-ttu-id="e6cd1-122">**nx_dhcp_user_option_convert**: *4바이트를 ULONG으로 변환*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="e6cd1-123">인터페이스 특정 DHCP 클라이언트 서비스:</span><span class="sxs-lookup"><span data-stu-id="e6cd1-123">Interface specific DHCP Client services:</span></span>

- <span data-ttu-id="e6cd1-124">**nx_dhcp_interface_clear_broadcast_flag**: *지정된 인터페이스의 클라이언트 메시지에서 브로드캐스트 플래그 지우기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>

- <span data-ttu-id="e6cd1-125">**nx_dhcp_interface_enable**: *지정된 인터페이스에서 DHCP를 실행하는 인터페이스 사용*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-126">**nx_dhcp_interface_disable**: *지정된 인터페이스에서 DHCP를 실행하는 인터페이스 사용 안 함*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-127">**nx_dhcp_interface_decline**: *지정된 인터페이스에서 서버에 거부 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-128">**nx_dhcp_interface_force_renew**: *지정된 인터페이스에서 강제 갱신 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-129">**nx_dhcp_interface_reinitialize**: *지정된 인터페이스에서 DHCP 클라이언트 네트워크 매개 변수 지우기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-130">**nx_dhcp_interface_release**: *지정된 인터페이스에서 서버에 릴리스 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-130">**nx_dhcp_interface_release**: *Send Release message to server  on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-131">**nx_dhcp_interface_request_client_ip**: *지정된 인터페이스에서 특정 IP 주소 지정*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-132">**nx_dhcp_interface_send_request**: *지정된 인터페이스에서 서버에 DHCP 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-133">**nx_dhcp_interface_server_address_get**: *지정된 인터페이스에서 DHCP 서버 IP 주소 가져오기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-134">**nx_dhcp_interface_start**: *지정된 인터페이스에서 DHCP 클라이언트 처리 시작*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-135">**nx_dhcp_interface_stop**: *지정된 인터페이스에서 DHCP 클라이언트 처리 중지*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-136">**nx_dhcp_interface_state_change_notify**: *지정된 인터페이스에서 DHCP 상태가 변경될 때 콜백 함수 설정*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-137">**nx_dhcp_interface_user_option_retrieve**: *지정된 인터페이스에서 지정된 DHCP 옵션 검색*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="e6cd1-138">NX_DHCP_CLIENT_RESORE_STATE가 정의된 경우 DHCP 클라이언트 서비스:</span><span class="sxs-lookup"><span data-stu-id="e6cd1-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="e6cd1-139">**nx_dhcp_resume**: *이전에 설정된 DHCP 클라이언트 상태 다시 시작*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>

- <span data-ttu-id="e6cd1-140">**nx_dhcp_suspend**: *DHCP 클라이언트 상태 처리 일시 중단*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>

- <span data-ttu-id="e6cd1-141">**nx_dhcp_client_get_record**: *DHCP 클라이언트 상태에 대한 레코드 만들기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>

- <span data-ttu-id="e6cd1-142">**nx_dhcp_client_restore_record**: *이전에 저장된 레코드를 DHCP 클라이언트에 복원*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>

- <span data-ttu-id="e6cd1-143">**nx_dhcp_client_update_time_remaining**: *남아 있는 현재 DHCP 상태 시간 업데이트*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="e6cd1-144">NX_DHCP_CLIENT_RESORE_STATE가 정의된 경우 인터페이스 특정 DHCP 클라이언트 서비스:</span><span class="sxs-lookup"><span data-stu-id="e6cd1-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="e6cd1-145">**nx_dhcp_client_interface_get_record**: *지정된 인터페이스에서 DHCP 클라이언트 상태에 대한 레코드 만들기*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-146">**nx_dhcp_client_interface_restore_record**: *지정된 인터페이스에서 이전에 저장된 레코드를 DHCP 클라이언트에 복원*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>

- <span data-ttu-id="e6cd1-147">**nx_dhcp_client_interface_update_time_remaining**: *지정된 인터페이스에서 남아 있는 현재 DHCP 상태 시간 업데이트*</span><span class="sxs-lookup"><span data-stu-id="e6cd1-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="e6cd1-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="e6cd1-148">nx_dhcp_create</span></span>

<span data-ttu-id="e6cd1-149">DHCP 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-150">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-150">Prototype</span></span>

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="e6cd1-151">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-151">Description</span></span>

<span data-ttu-id="e6cd1-152">이 서비스는 이전에 만든 IP 인스턴스에 대한 DHCP 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="e6cd1-153">기본적으로 기본 인터페이스가 DHCP를 실행하는 데 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="e6cd1-154">이름 입력은 DHCP 클라이언트의 NetX 구현에서 사용되지 않지만 호스트 이름에 대한 RFC 1035 조건을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-154">The name input, while not used in the NetX implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="e6cd1-155">총 길이는 255자를 초과할 수 없으며, 점으로 구분된 레이블은 문자로 시작하고 문자 또는 숫자로 끝나야 하며, 하이픈은 포함할 수 있지만 영숫자가 아닌 다른 문자는 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="e6cd1-156">애플리케이션에서 IP 인스턴스에 등록된 다른 인터페이스인 DHCP를 실행하려는 경우(*nx_ip_interface_attach* 사용) 애플리케이션에서 *nx_dhcp_set_interface_index* 를 호출하여 해당 인터페이스에서만 DHCP를 실행하거나 *nx_dhcp_interface_enable* 을 호출하여 해당 인터페이스에서도 DHCP를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="e6cd1-157">자세한 내용은 이러한 서비스에 대한 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-157">See description of these services for more details.</span></span>

> [!NOTE]
> <span data-ttu-id="e6cd1-158">애플리케이션에서 DHCP 클라이언트 패킷 풀 페이로드가 RFC 2131 섹션 2(548바이트의 DHCP 메시지 데이터와 UDP, IP 및 실제 네트워크 프레임 헤더)에서 지정한 최소 DHCP 메시지 크기를 지원할 수 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-159">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-159">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-160">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-160">**dhcp_ptr** Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="e6cd1-161">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-161">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="e6cd1-162">**name_ptr** DHCP 인스턴스의 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-162">**name_ptr** Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-163">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-163">Return Values</span></span>

- <span data-ttu-id="e6cd1-164">**NX_SUCCESS** (0x00) DHCP를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="e6cd1-164">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="e6cd1-165">**NX_DHCP_INVALID_NAME** (0xA8) 잘못된 호스트 이름</span><span class="sxs-lookup"><span data-stu-id="e6cd1-165">**NX_DHCP_INVALID_NAME** (0xA8) Invalid host name</span></span>

- <span data-ttu-id="e6cd1-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) DHCP 메시지에 대한 페이로드가 너무 작음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) Payload too small for DHCP message</span></span>

- <span data-ttu-id="e6cd1-167">NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-167">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-168">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-168">Allowed From</span></span>

<span data-ttu-id="e6cd1-169">**스레드,** 초기화</span><span class="sxs-lookup"><span data-stu-id="e6cd1-169">**Threads,** Initialization</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-170">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-170">Example</span></span>

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="e6cd1-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="e6cd1-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="e6cd1-172">DHCP를 실행하도록 지정된 인터페이스를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="e6cd1-173">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-173">Prototype</span></span>

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="e6cd1-174">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-174">Description</span></span>

<span data-ttu-id="e6cd1-175">이 서비스를 사용하면 지정된 인터페이스에서 DHCP를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="e6cd1-176">기본적으로 기본 인터페이스가 DHCP 클라이언트에 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="e6cd1-177">이 시점에서 *nx_dhcp_interface_start* 를 호출하여 이 인터페이스에서 DHCP를 시작하거나 사용하도록 설정된 모든 *nx_dhcp_start* 인터페이스에서 DHCP를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

<span data-ttu-id="e6cd1-178">애플리케이션에서 먼저 *nx_ip_interface_attach.* 를 사용하여 이 인터페이스를 IP 인스턴스에 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-178">Note the application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="e6cd1-179">또한 이 인터페이스를 사용하도록 설정된 인터페이스 목록에 추가하려면 사용 가능한 DHCP 클라이언트 인터페이스 '레코드'가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="e6cd1-180">기본적으로 NX_DHCP_CLIENT_MAX_RECORDS가 1로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="e6cd1-181">이 옵션을 DHCP 클라이언트를 동시에 실행하는 데 필요한 최대 인터페이스 수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="e6cd1-182">일반적으로 NX_DHCP_CLIENT_MAX_RECORDS는 NX_MAX_PHYSICAL_INTERFACES와 동일합니다. 그러나 DHCP 클라이언트를 실행하는 데 필요한 것보다 더 많은 실제 인터페이스가 디바이스에 있는 경우 NX_DHCP_CLIENT_MAX_RECORDS를 해당 숫자보다 작게 설정하여 메모리를 절약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="e6cd1-183">실제 인터페이스와 DHCP 클라이언트 인터페이스 레코드의 일대일 매핑이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="e6cd1-184">이 서비스와 *nx_dhcp_set_interface_index* 의 차이점은 후자는 DHCP를 실행하는 단일 인터페이스만 설정하는 반면, 이 서비스는 지정된 인터페이스를 DHCP에 사용하도록 설정된 클라이언트 인터페이스 목록에 추가한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="e6cd1-185">DHCP에 대한 인터페이스를 사용하지 않도록 설정하기 위해 애플리케이션에서 *nx_dhcp_interface_disable* 서비스를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-185">To disable an interface for DHCP, the application can call the *nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-186">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-186">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-187">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-187">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="e6cd1-188">**interface_index** DHCP를 사용하도록 설정하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-188">**interface_index** Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-189">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-189">Return Values</span></span>

- <span data-ttu-id="e6cd1-190">**NX_SUCCESS** (0x00) DHCP를 성공적으로 사용하도록 설정함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-190">**NX_SUCCESS** (0x00) Successful DHCP enable</span></span>

- <span data-ttu-id="e6cd1-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) DHCP에 사용하도록 설정할 다른 인터페이스에 사용할 수 있는 레코드가 없음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another Interface to be enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) DHCP에 사용하도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-193">NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-193">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-194">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-194">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-195">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-195">Allowed From</span></span>

<span data-ttu-id="e6cd1-196">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="e6cd1-196">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-197">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-197">Example</span></span>

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="e6cd1-198">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="e6cd1-198">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="e6cd1-199">DHCP를 실행하도록 지정된 인터페이스를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-199">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="e6cd1-200">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-200">Prototype</span></span>

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="e6cd1-201">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-201">Description</span></span>

<span data-ttu-id="e6cd1-202">이 서비스를 사용하지 않으면 지정된 인터페이스에서 DHCP를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-202">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="e6cd1-203">이 인터페이스에서 DHCP 클라이언트를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-203">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="e6cd1-204">DHCP 클라이언트를 다시 시작하려면 애플리케이션에서 *nx_dhcp_interface_enable* 을 사용하여 인터페이스를 다시 사용하도록 설정하고 *nx_dhcp_interface_start* 를 호출하여 DHCP를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-204">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-205">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-205">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-206">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-206">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="e6cd1-207">**interface_index** DHCP를 사용하지 않도록 설정하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-207">**interface_index** Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-208">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-208">Return Values</span></span>

- <span data-ttu-id="e6cd1-209">**NX_SUCCESS** (0x00) DHCP를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="e6cd1-209">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="e6cd1-210">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-210">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-211">NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-211">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-212">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="e6cd1-212">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="e6cd1-213">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-213">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-214">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-214">Allowed From</span></span>

<span data-ttu-id="e6cd1-215">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-216">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-216">Example</span></span>

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="e6cd1-217">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="e6cd1-217">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="e6cd1-218">DHCP 브로드캐스트 플래그를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-218">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-219">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-219">Prototype</span></span>

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="e6cd1-220">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-220">Description</span></span>

<span data-ttu-id="e6cd1-221">이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스에 대한 DHCP 메시지 헤더의 브로드캐스트 플래그를 설정하거나 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-221">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="e6cd1-222">일부 DHCP 메시지(예: DISCOVER)의 경우 클라이언트에 IP 주소가 없으므로 브로드캐스트 플래그가 브로드캐스트로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-222">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="e6cd1-223">__clear_flag__</span><span class="sxs-lookup"><span data-stu-id="e6cd1-223">__clear_flag__</span></span>


- <span data-ttu-id="e6cd1-224">**NX_TRUE** 브로드캐스트 플래그가 지워짐(요청 유니캐스트 응답)</span><span class="sxs-lookup"><span data-stu-id="e6cd1-224">**NX_TRUE** broadcast flag is cleared (request unicast response)</span></span>

- <span data-ttu-id="e6cd1-225">**NX_FALSE** 브로드캐스트 플래그가 설정됨(요청 브로드캐스트 응답)</span><span class="sxs-lookup"><span data-stu-id="e6cd1-225">**NX_FALSE** broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="e6cd1-226">이 서비스는 라우터를 통해 DHCP 서버에 도달해야 하는 DHCP 클라이언트를 위한 것입니다. 여기서 라우터는 브로드캐스트 메시지 전달을 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-226">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-227">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-227">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-228">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-228">**dhcp_ptr** Pointer to DHCP control block</span></span>  

- <span data-ttu-id="e6cd1-229">**clear_flag** 브로드캐스트 플래그를 설정하는 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-229">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-230">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-230">Return Values</span></span>

- <span data-ttu-id="e6cd1-231">**NX_SUCCESS** (0x00) 브로드캐스트 플래그를 성공적으로 업데이트함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-231">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="e6cd1-232">NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-232">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-233">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="e6cd1-233">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-234">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-234">Allowed From</span></span>

<span data-ttu-id="e6cd1-235">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="e6cd1-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-236">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-236">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="e6cd1-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="e6cd1-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="e6cd1-238">지정된 인터페이스에서 브로드캐스트 플래그를 설정하거나 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-239">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-239">Prototype</span></span>

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="e6cd1-240">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-240">Description</span></span>

<span data-ttu-id="e6cd1-241">이 서비스를 사용하면 DHCP 클라이언트 호스트 애플리케이션이 DHCP 클라이언트 메시지의 브로드캐스트 플래그를 지정된 인터페이스의 DHCP 서버로 설정하거나 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="e6cd1-242">자세한 내용은 **nx_dhcp_clear_broadcast_flag** 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-242">For more details see **nx_dhcp_clear_broadcast_flag**</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-243">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-243">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-244">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-244">**dhcp_ptr** Pointer to DHCP control block</span></span>

- <span data-ttu-id="e6cd1-245">**interface_index** 브로드캐스트 플래그를 설정하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-245">**interface_index** Index of interface to set the broadcast flag</span></span>  

- <span data-ttu-id="e6cd1-246">**clear_flag** 브로드캐스트 플래그를 설정하는 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-246">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-247">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-247">Return Values</span></span>

- <span data-ttu-id="e6cd1-248">**NX_SUCCESS** (0x00) 브로드캐스트 플래그를 성공적으로 업데이트함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-248">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="e6cd1-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-250">NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-250">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-251">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-251">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-252">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-252">Allowed From</span></span>

<span data-ttu-id="e6cd1-253">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="e6cd1-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-254">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-254">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="e6cd1-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="e6cd1-255">nx_dhcp_delete</span></span>

<span data-ttu-id="e6cd1-256">DHCP 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-257">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-257">Prototype</span></span>

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="e6cd1-258">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-258">Description</span></span>

<span data-ttu-id="e6cd1-259">이 서비스는 이전에 만든 DHCP 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-260">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-260">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-261">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-261">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-262">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-262">Return Values</span></span>

- <span data-ttu-id="e6cd1-263">**NX_SUCCESS** (0x00) DHCP를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-263">**NX_SUCCESS** (0x00) Successful DHCP delete.</span></span>

- <span data-ttu-id="e6cd1-264">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-264">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="e6cd1-265">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-265">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-266">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-266">Allowed From</span></span>

<span data-ttu-id="e6cd1-267">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-268">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-268">Example</span></span>

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="e6cd1-269">nx_dhcp_ force_renew</span><span class="sxs-lookup"><span data-stu-id="e6cd1-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="e6cd1-270">강제 갱신 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="e6cd1-271">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-271">Prototype</span></span>

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="e6cd1-272">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-272">Description</span></span>

<span data-ttu-id="e6cd1-273">이 서비스를 사용하면 DHCP에 사용하도록 설정된 호스트 애플리케이션의 모든 인터페이스에서 강제 갱신 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="e6cd1-274">DHCP 클라이언트는 BOUND 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="e6cd1-275">이 함수는 T1 시간 제한이 만료되기 전에 DHCP 클라이언트에서 갱신을 시도하도록 상태를 RENEW로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="e6cd1-276">여러 인터페이스에서 DHCP를 사용하도록 설정된 경우 특정 인터페이스에서 강제 갱신을 보내려면 *nx_dhcp_interface_force_renew* 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-277">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-277">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-278">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-278">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-279">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-279">Return Values</span></span>

- <span data-ttu-id="e6cd1-280">**NX_SUCCESS** (0x00) 강제 갱신을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="e6cd1-280">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="e6cd1-281">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-281">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="e6cd1-282">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-282">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-283">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-283">Allowed From</span></span>

<span data-ttu-id="e6cd1-284">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-285">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-285">Example</span></span>

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="e6cd1-286">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="e6cd1-286">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="e6cd1-287">지정된 인터페이스에서 강제 갱신 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-287">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-288">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-288">Prototype</span></span>

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="e6cd1-289">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-289">Description</span></span>

<span data-ttu-id="e6cd1-290">이 서비스를 사용하면 입력 인터페이스가 DHCP에 사용하도록 설정된 경우 호스트 애플리케이션의 해당 인터페이스에서 강제 갱신 메시지를 보낼 수 있습니다(*nx_dhcp_interface_enable* 참조).</span><span class="sxs-lookup"><span data-stu-id="e6cd1-290">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="e6cd1-291">지정된 인터페이스의 DHCP 클라이언트가 BOUND 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-291">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="e6cd1-292">이 함수는 T1 시간 제한이 만료되기 전에 DHCP 클라이언트에서 갱신을 시도하도록 상태를 RENEW로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-292">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-293">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-293">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-294">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-294">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-295">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-295">Return Values</span></span>

- <span data-ttu-id="e6cd1-296">**NX_SUCCESS** (0x00) 강제 갱신을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="e6cd1-296">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="e6cd1-297">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-297">**NX_DHCP_INTERFACE_NOT_ENABLED**  (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-298">NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-298">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-299">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-299">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-300">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-300">Allowed From</span></span>

<span data-ttu-id="e6cd1-301">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-302">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-302">Example</span></span>

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="e6cd1-303">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="e6cd1-303">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="e6cd1-304">DHCP 클라이언트 패킷 풀을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-304">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-305">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-305">Prototype</span></span>

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="e6cd1-306">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-306">Description</span></span>

<span data-ttu-id="e6cd1-307">이 서비스를 사용하면 애플리케이션에서 포인터를 이 서비스 호출의 이전에 만든 패킷 풀에 전달하여 DHCP 클라이언트 패킷 풀을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-307">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="e6cd1-308">이 기능을 사용하려면 호스트 애플리케이션에서 NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-308">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="e6cd1-309">정의되면 *nx_dhcp_create* 서비스에서 클라이언트의 패킷 풀을 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-309">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> <span data-ttu-id="e6cd1-310">애플리케이션에서 패킷 풀을 만들 때 *nx_dhcp.h* 에서 NX_DHCP_PACKET_PAYLOAD로 정의된 DHCP 클라이언트 패킷 풀 페이로드에 대한 기본값을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-310">Note that the application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nx_dhcp.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-311">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-311">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-312">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-312">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="e6cd1-313">**packet_pool_ptr** 이전에 만든 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-313">**packet_pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-314">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-314">Return Values</span></span>

- <span data-ttu-id="e6cd1-315">**NX_SUCCESS** (0x00) DHCP 클라이언트 패킷 풀이 설정됨</span><span class="sxs-lookup"><span data-stu-id="e6cd1-315">**NX_SUCCESS** (0x00) DHCP Client packet pool is set</span></span>

- <span data-ttu-id="e6cd1-316">**NX_NOT_ENABLED** (0x14) 서비스가 사용하도록 설정되지 않음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-316">**NX_NOT_ENABLED** (0x14) Service is not enabled</span></span>

- <span data-ttu-id="e6cd1-317">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-317">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-318">NX_DHCP_INVALID_PAYLOAD (0x9C) 페이로드가 너무 작음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-318">NX_DHCP_INVALID_PAYLOAD (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-319">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-319">Allowed From</span></span>

<span data-ttu-id="e6cd1-320">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-320">Application code</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-321">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-321">Example</span></span>

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="e6cd1-322">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="e6cd1-322">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="e6cd1-323">DHCP 인스턴스에 대해 요청된 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-323">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-324">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-324">Prototype</span></span>

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="e6cd1-325">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-325">Description</span></span>

<span data-ttu-id="e6cd1-326">이 서비스는 DHCP 클라이언트 레코드의 DHCP에 사용하도록 설정된 첫 번째 인터페이스의 DHCP 서버에서 요청할 DHCP 클라이언트에 대한 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-326">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="e6cd1-327">*skip_discover_message* 플래그가 설정되면 DHCP 클라이언트에서 검색 메시지를 건너뛰고 요청 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-327">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="e6cd1-328">특정 인터페이스에서 DHCP 메시지의 특정 IP에 대한 요청을 설정하려면 *nx_dhcp_interface_request_client_ip* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-328">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-329">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-329">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-330">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-330">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="e6cd1-331">**client_ip_address** DHCP 서버에서 요청하는 IP 주소</span><span class="sxs-lookup"><span data-stu-id="e6cd1-331">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="e6cd1-332">**skip_discover_message** true이면 DHCP 클라이언트에서 요청 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-332">**skip_discover_message** If true, DHCP Client sends Request message</span></span>  
<span data-ttu-id="e6cd1-333">false이면 검색 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-333">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-334">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-334">Return Values</span></span>

- <span data-ttu-id="e6cd1-335">**NX_SUCCESS** (0x00) 요청된 IP 주소가 설정됨</span><span class="sxs-lookup"><span data-stu-id="e6cd1-335">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="e6cd1-336">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-336">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-337">NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-337">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-338">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-338">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="e6cd1-339">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-339">Allowed From</span></span>

<span data-ttu-id="e6cd1-340">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-340">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-341">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-341">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="e6cd1-342">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="e6cd1-342">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="e6cd1-343">지정된 인터페이스에서 DHCP 인스턴스에 대해 요청된 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-343">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-344">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-344">Prototype</span></span>

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="e6cd1-345">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-345">Description</span></span>

<span data-ttu-id="e6cd1-346">인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 지정된 인터페이스에서 DHCP 서버로부터 요청할 DHCP 클라이언트에 대한 IP 주소를 설정합니다(*nx_dhcp_interface_enable* 참조).</span><span class="sxs-lookup"><span data-stu-id="e6cd1-346">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="e6cd1-347">*skip_discover_message* 플래그가 설정되면 DHCP 클라이언트에서 검색 메시지를 건너뛰고 요청 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-347">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-348">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-348">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-349">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-349">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="e6cd1-350">**Interface_index** IP 주소를 요청하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-350">**Interface_index** Index of interface to request IP address on</span></span>

- <span data-ttu-id="e6cd1-351">**client_ip_address** DHCP 서버에서 요청하는 IP 주소</span><span class="sxs-lookup"><span data-stu-id="e6cd1-351">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="e6cd1-352">**skip_discover_message** true이면 DHCP 클라이언트에서 요청 메시지를 보냅니다. 그렇지 않으면 검색 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-352">**skip_discover_message** If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-353">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-353">Return Values</span></span>

- <span data-ttu-id="e6cd1-354">**NX_SUCCESS** (0x00) 요청된 IP 주소가 설정됨</span><span class="sxs-lookup"><span data-stu-id="e6cd1-354">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="e6cd1-355">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-355">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-356">NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-356">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-357">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-357">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>


### <a name="allowed-from"></a><span data-ttu-id="e6cd1-358">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-358">Allowed From</span></span>

<span data-ttu-id="e6cd1-359">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-360">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-360">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="e6cd1-361">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="e6cd1-361">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="e6cd1-362">DHCP 클라이언트 네트워크 매개 변수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-362">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="e6cd1-363">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-363">Prototype</span></span>

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="e6cd1-364">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-364">Description</span></span>

<span data-ttu-id="e6cd1-365">이 서비스는 호스트 애플리케이션 네트워크 매개 변수(IP 주소, 네트워크 주소 및 네트워크 마스크)를 지우고, DHCP에 사용하도록 설정된 모든 인터페이스에서 DHCP 클라이언트 상태를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-365">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="e6cd1-366">DHCP 상태 시스템을 '다시 시작'하기 위해 *nx_dhcp_stop* 및 *nx_dhcp_start* 와 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-366">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span> 

<span data-ttu-id="e6cd1-367">nx_dhcp_stop(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="e6cd1-367">nx_dhcp_stop(&my_dhcp);</span></span>  
<span data-ttu-id="e6cd1-368">nx_dhcp_reinitialize(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="e6cd1-368">nx_dhcp_reinitialize(&my_dhcp);</span></span>  
<span data-ttu-id="e6cd1-369">nx_dhcp_start(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="e6cd1-369">nx_dhcp_start(&my_dhcp);</span></span>


<span data-ttu-id="e6cd1-370">여러 인터페이스가 DHCP에 사용하도록 설정된 경우 특정 인터페이스에서 DHCP 클라이언트를 다시 초기화하려면 *nx_dhcp_interface_reinitialize* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-370">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-371">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-371">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-372">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-372">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-373">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-373">Return Values</span></span>

- <span data-ttu-id="e6cd1-374">**NX_SUCCESS** (0x00) DHCP를 성공적으로 다시 초기화함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-374">**NX_SUCCESS** (0x00) DHCP successfully reinitialized</span></span> 

- <span data-ttu-id="e6cd1-375">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-375">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-376">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-376">Allowed From</span></span>

<span data-ttu-id="e6cd1-377">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-377">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-378">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-378">Example</span></span>

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="e6cd1-379">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="e6cd1-379">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="e6cd1-380">지정된 인터페이스에서 DHCP 클라이언트 네트워크 매개 변수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-380">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="e6cd1-381">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-381">Prototype</span></span>

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="e6cd1-382">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-382">Description</span></span>

<span data-ttu-id="e6cd1-383">해당 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 지정된 인터페이스에서 네트워크 매개 변수(IP 주소, 네트워크 주소 및 네트워크 마스크)를 지웁니다(*nx_dhcp_interface_enable* 참조).</span><span class="sxs-lookup"><span data-stu-id="e6cd1-383">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="e6cd1-384">자세한 내용은 *nx_dhcp_reinitialize* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-384">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-385">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-385">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-386">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-386">**dhcp_ptr** Pointer to previously created DHCP instance</span></span>

- <span data-ttu-id="e6cd1-387">**interface_index** 다시 초기화하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-387">**interface_index** Index of interface to reinitialize.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-388">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-388">Return Values</span></span>

- <span data-ttu-id="e6cd1-389">**NX_SUCCESS** (0x00) 인터페이스를 성공적으로 다시 초기화함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-389">**NX_SUCCESS** (0x00) Interface successfully reinitialized</span></span>

- <span data-ttu-id="e6cd1-390">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-390">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-391">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-391">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-392">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-392">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="e6cd1-393">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-393">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-394">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-394">Allowed From</span></span>

<span data-ttu-id="e6cd1-395">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-395">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-396">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-396">Example</span></span>

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="e6cd1-397">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="e6cd1-397">nx_dhcp_release</span></span>

<span data-ttu-id="e6cd1-398">임대 IP 주소를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-398">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-399">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-399">Prototype</span></span>

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="e6cd1-400">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-400">Description</span></span>

<span data-ttu-id="e6cd1-401">이 서비스는 RELEASE 메시지를 DHCP 서버로 보내 해당 서버에서 가져온 IP 주소를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-401">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="e6cd1-402">그런 다음, DHCP 클라이언트를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-402">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="e6cd1-403">이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-403">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="e6cd1-404">애플리케이션에서 *nx_dhcp_start* 호출하여 DHCP 클라이언트를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-404">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="e6cd1-405">특정 인터페이스에서 주소를 DHCP 서버로 다시 해제하려면 *nx_dhcp_interface_release* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-405">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-406">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-406">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-407">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-407">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-408">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-408">Return Values</span></span>

- <span data-ttu-id="e6cd1-409">**NX_SUCCESS** (0x00) DHCP를 성공적으로 해제함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-409">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>  

- <span data-ttu-id="e6cd1-410">**NX_DHCP_NOT_BOUND** (0x94) IP 주소가 임대되지 않았으므로 해제할 수 없음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-410">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="e6cd1-411">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-411">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="e6cd1-412">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-412">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-413">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-413">Allowed From</span></span>

<span data-ttu-id="e6cd1-414">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-414">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-415">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-415">Example</span></span>

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="e6cd1-416">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="e6cd1-416">nx_dhcp_interface_release</span></span>

<span data-ttu-id="e6cd1-417">지정된 인터페이스에서 IP 주소를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-417">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-418">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-418">Prototype</span></span>

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="e6cd1-419">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-419">Description</span></span>

<span data-ttu-id="e6cd1-420">이 서비스는 지정된 인터페이스에서 가져온 DHCP 서버의 IP 주소를 해제하고 DHCP 클라이언트를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-420">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="e6cd1-421">DHCP 클라이언트는 *nx_dhcp_start* 를 호출하여 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-421">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-422">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-422">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-423">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-423">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-424">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-424">Return Values</span></span>

- <span data-ttu-id="e6cd1-425">**NX_SUCCESS** (0x00) DHCP를 성공적으로 해제함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-425">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>

- <span data-ttu-id="e6cd1-426">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-426">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-427">**NX_DHCP_NOT_BOUND** (0x94) IP 주소가 임대되지 않았으므로 해제할 수 없음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-427">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="e6cd1-428">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-428">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-429">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-429">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="e6cd1-430">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-430">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-431">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-431">Allowed From</span></span>

<span data-ttu-id="e6cd1-432">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-432">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-433">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-433">Example</span></span>

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="e6cd1-434">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="e6cd1-434">nx_dhcp_decline</span></span>

<span data-ttu-id="e6cd1-435">DHCP 서버에서 IP 주소를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-435">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-436">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-436">Prototype</span></span>

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="e6cd1-437">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-437">Description</span></span>

<span data-ttu-id="e6cd1-438">이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스의 DHCP 서버에서 임대된 IP 주소를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-438">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="e6cd1-439">NX_DHCP_CLIENT_ SEND_ ARP_PROBE가 정의된 경우 IP 주소를 이미 사용하고 있음을 검색하면 DHCP 클라이언트에서 DECLINE 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-439">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="e6cd1-440">NetX DHCP 클라이언트에서 ARP 프로브 구성에 대한 자세한 내용은 챕터 1의 **ARP 프로브** 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-440">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX DHCP Client.</span></span>

<span data-ttu-id="e6cd1-441">주소를 다른 방법으로 사용하고 있음을 검색하는 경우 애플리케이션에서 이 서비스를 사용하여 IP 주소를 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-441">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="e6cd1-442">이 서비스는 *nx_dhcp_start* 를 호출하여 다시 시작할 수 있도록 DHCP 클라이언트를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-442">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-443">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-443">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-444">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-444">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-445">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-445">Return Values</span></span>

- <span data-ttu-id="e6cd1-446">**NX_SUCCESS** (0x00) 거부를 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="e6cd1-446">**NX_SUCCESS** (0x00) Decline successfully sent</span></span>  

- <span data-ttu-id="e6cd1-447">**NX_DHCP_NOT_STARTED** (0x96) DHCP 인스턴스가 시작되지 않음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-447">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started</span></span>

- <span data-ttu-id="e6cd1-448">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-448">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-449">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="e6cd1-449">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-450">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-450">Allowed From</span></span>

<span data-ttu-id="e6cd1-451">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-452">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-452">Example</span></span>

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="e6cd1-453">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="e6cd1-453">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="e6cd1-454">지정된 인터페이스에서 DHCP 서버의 IP 주소를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-454">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-455">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-455">Prototype</span></span>

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="e6cd1-456">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-456">Description</span></span>

<span data-ttu-id="e6cd1-457">이 서비스는 DHCP 서버에서 할당한 IP 주소를 거부하기 위해 DECLINE 메시지를 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-457">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="e6cd1-458">또한 DHCP 클라이언트를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-458">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="e6cd1-459">자세한 내용은 *nx_dhcp_decline* 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-459">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-460">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-460">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-461">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-461">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="e6cd1-462">**Interface_index** IP 주소를 거부하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-462">**Interface_index** Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-463">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-463">Return Values</span></span>

- <span data-ttu-id="e6cd1-464">**NX_SUCCESS** (0x00) DHCP 거부 메시지를 보냄</span><span class="sxs-lookup"><span data-stu-id="e6cd1-464">**NX_SUCCESS** (0x00) DHCP decline message sent</span></span>  

- <span data-ttu-id="e6cd1-465">**NX_DHCP_NOT_BOUND** (0x94) DHCP 클라이언트가 바인딩되지 않음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-465">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="e6cd1-466">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-466">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-467">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-467">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-468">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="e6cd1-469">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-469">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-470">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-470">Allowed From</span></span>

<span data-ttu-id="e6cd1-471">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-471">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-472">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-472">Example</span></span>
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a><span data-ttu-id="e6cd1-473">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="e6cd1-473">nx_dhcp_send_request</span></span>

<span data-ttu-id="e6cd1-474">DHCP 메시지를 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-474">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-475">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-475">Prototype</span></span>

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="e6cd1-476">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-476">Description</span></span>

<span data-ttu-id="e6cd1-477">이 서비스는 DHCP 클라이언트 레코드에 있는 DHCP에 사용하도록 설정된 첫 번째 인터페이스에서 지정된 DHCP 메시지를 DHCP 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-477">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="e6cd1-478">RELEASE 또는 DECLINE 메시지를 보내려면 애플리케이션에서 *nx_dhcp[_interface]_release*() 또는 *nx_dhcp_interface_decline()* 서비스를 각각 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-478">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="e6cd1-479">INFORM_REQUEST 메시지 유형을 보내는 경우를 제외하고 이 서비스를 사용하려면 DHCP 클라이언트를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-479">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

> [!NOTE] 
> <span data-ttu-id="e6cd1-480">이 서비스는 호스트 애플리케이션에서 DHCP 클라이언트 상태 시스템을 '구동'하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-480">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-481">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-481">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-482">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-482">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="e6cd1-483">**dhcp_message_type** 메시지 요청(*nx_dhcp.h* 에서 정의됨)</span><span class="sxs-lookup"><span data-stu-id="e6cd1-483">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-484">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-484">Return Values</span></span>

- <span data-ttu-id="e6cd1-485">**NX_SUCCESS** (0x00) DHCP 메시지를 보냄</span><span class="sxs-lookup"><span data-stu-id="e6cd1-485">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="e6cd1-486">**NX_DHCP_NOT_STARTED** (0x96) 잘못된 인터페이스 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-486">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="e6cd1-487">**NX_DHCP_INVALID_MESSAGE** (0x9B) 잘못된 보내는 메시지 유형</span><span class="sxs-lookup"><span data-stu-id="e6cd1-487">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="e6cd1-488">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="e6cd1-488">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-489">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-489">Allowed From</span></span>

<span data-ttu-id="e6cd1-490">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-491">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-491">Example</span></span>

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="e6cd1-492">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="e6cd1-492">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="e6cd1-493">특정 인터페이스에서 DHCP 메시지를 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-493">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-494">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-494">Prototype</span></span>

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="e6cd1-495">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-495">Description</span></span>

<span data-ttu-id="e6cd1-496">지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 메시지를 DHCP 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-496">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="e6cd1-497">RELEASE 또는 DECLINE 메시지를 보내려면 애플리케이션에서 *nx_dhcp[_interface]_release*() 또는 *nx_dhcp_interface_decline()* 서비스를 각각 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-497">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="e6cd1-498">DHCP INFORM REQUEST 메시지 유형을 보내는 경우를 제외하고 이 서비스를 사용하려면 DHCP 클라이언트를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-498">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="e6cd1-499">이 서비스는 호스트 애플리케이션에서 DHCP 클라이언트 상태 시스템을 '구동'하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-499">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-500">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-500">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-501">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-501">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="e6cd1-502">**Interface_index** 메시지를 보내는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-502">**Interface_index** Index of interface to send message on</span></span>  

- <span data-ttu-id="e6cd1-503">**dhcp_message_type** 메시지 요청(*nx_dhcp.h* 에서 정의됨)</span><span class="sxs-lookup"><span data-stu-id="e6cd1-503">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-504">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-504">Return Values</span></span>

- <span data-ttu-id="e6cd1-505">**NX_SUCCESS** (0x00) DHCP 메시지를 보냄</span><span class="sxs-lookup"><span data-stu-id="e6cd1-505">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="e6cd1-506">**NX_DHCP_NOT_STARTED** (0x96) 잘못된 인터페이스 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-506">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="e6cd1-507">**NX_DHCP_INVALID_MESSAGE** (0x9B) 잘못된 보내는 메시지 유형</span><span class="sxs-lookup"><span data-stu-id="e6cd1-507">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="e6cd1-508">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-508">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-509">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-509">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-510">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-510">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="e6cd1-511">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-511">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-512">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-512">Allowed From</span></span>

<span data-ttu-id="e6cd1-513">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-513">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-514">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-514">Example</span></span>

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="e6cd1-515">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="e6cd1-515">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="e6cd1-516">DHCP 클라이언트의 DHCP 서버 IP 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-516">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-517">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-517">Prototype</span></span>

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="e6cd1-518">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-518">Description</span></span>

<span data-ttu-id="e6cd1-519">이 서비스는 DHCP 클라이언트 레코드에 있는 DHCP에 사용하도록 설정된 첫 번째 인터페이스에서 DHCP 클라이언트 DHCP 서버 IP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-519">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="e6cd1-520">호출자는 DHCP 클라이언트가 DHCP 서버에서 할당한 IP 주소에 바인딩된 후에만 이 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-520">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="e6cd1-521">호스트 애플리케이션에서 *nx_ip_status_check* 서비스를 사용하여 IP 주소가 설정되어 있는지 확인하거나 *nx_dhcp_state_change_notify* 를 사용하여 DHCP 클라이언트 상태가 NX_DHCP_STATE_BOUND인지 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-521">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the *nx_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="e6cd1-522">상태 변경 콜백 함수를 설정하는 방법에 대한 자세한 내용은 *nx_dhcp_state_change_notify* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-522">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="e6cd1-523">여러 인터페이스가 DHCP 클라이언트에 사용하도록 설정된 경우 특정 인터페이스에서 DHCP 서버를 찾으려면 *nx_dhcp_interface_server_address_get* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-523">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-524">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-524">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-525">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-525">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="e6cd1-526">**server_address** 서버 IP 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-526">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-527">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-527">Return Values</span></span>

- <span data-ttu-id="e6cd1-528">**NX_SUCCESS** (0x00) DHCP 서버 주소가 반환됨</span><span class="sxs-lookup"><span data-stu-id="e6cd1-528">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="e6cd1-529">NX_PTR_ERROR (0x16) 잘못된 입력 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-529">NX_PTR_ERROR (0x16) Invalid input pointer</span></span>

- <span data-ttu-id="e6cd1-530">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-530">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-531">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-531">Allowed From</span></span>

<span data-ttu-id="e6cd1-532">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-533">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-533">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="e6cd1-534">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="e6cd1-534">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="e6cd1-535">지정된 인터페이스에서 DHCP 클라이언트의 DHCP 서버 IP 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-535">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-536">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-536">Prototype</span></span>

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="e6cd1-537">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-537">Description</span></span>

<span data-ttu-id="e6cd1-538">지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 DHCP 클라이언트 DHCP 서버 IP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-538">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="e6cd1-539">DHCP 클라이언트는 바인딩됨 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-539">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="e6cd1-540">해당 인터페이스에서 DHCP 클라이언트를 시작하면 호스트 애플리케이션에서 *nx_ip_status_check* 서비스를 사용하여 IP 주소가 설정되어 있는지 확인하거나 DHCP 클라이언트 상태 변경 콜백을 사용하여 DHCP 클라이언트 상태가 NX_DHCP_STATE_BOUND인지 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-540">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="e6cd1-541">상태 변경 콜백 함수를 설정하는 방법에 대한 자세한 내용은 *nx_dhcp_state_change_notify* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-541">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-542">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-542">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-543">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-543">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="e6cd1-544">**Interface_index** IP 주소를 가져오는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-544">**Interface_index** Index of interface to obtain IP address</span></span>  

- <span data-ttu-id="e6cd1-545">**server_address** 서버 IP 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-545">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-546">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-546">Return Values</span></span>

- <span data-ttu-id="e6cd1-547">**NX_SUCCESS** (0x00) DHCP 서버 주소가 반환됨</span><span class="sxs-lookup"><span data-stu-id="e6cd1-547">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="e6cd1-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP에 사용하도록 설정된 인터페이스가 없음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-549">**NX_DHCP_NOT_BOUND** (0x94) DHCP 클라이언트가 바인딩되지 않음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-549">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="e6cd1-550">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-550">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="e6cd1-551">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-551">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="e6cd1-552">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-552">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-553">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-553">Allowed From</span></span>

<span data-ttu-id="e6cd1-554">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-555">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-555">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="e6cd1-556">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="e6cd1-556">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="e6cd1-557">DHCP 인스턴스에 대한 네트워크 인터페이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-557">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-558">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-558">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="e6cd1-559">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-559">Description</span></span>

<span data-ttu-id="e6cd1-560">이 서비스는 단일 네트워크 인터페이스에 대해 구성된 DHCP 클라이언트를 실행할 때 DHCP 인스턴스에서 DHCP 서버에 연결하는 네트워크 인터페이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-560">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="e6cd1-561">기본적으로 DHCP 클라이언트가 기본 인터페이스에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-561">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="e6cd1-562">보조 서비스에서 DHCP를 실행하려면 이 서비스를 사용하여 보조 인터페이스를 DHCP 클라이언트 인터페이스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-562">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="e6cd1-563">애플리케이션에서 이전에 *nx_ip_interface_attach* 서비스를 사용하여 지정된 인터페이스를 IP 인스턴스에 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-563">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

<span data-ttu-id="e6cd1-564">이 서비스는 하나의 인터페이스에서만 DHCP 클라이언트를 실행하려는 애플리케이션을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-564">Note that this service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="e6cd1-565">여러 인터페이스에서 DHCP를 실행하는 방법에 대한 자세한 내용은 *nx_dhcp_interface_enable* 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-565">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-566">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-566">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-567">**dhcp_ptr** DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-567">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="e6cd1-568">**index** 디바이스 네트워크 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-568">**index** Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-569">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-569">Return Values</span></span>

- <span data-ttu-id="e6cd1-570">**NX_SUCCESS** (0x00) 인터페이스를 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-570">**NX_SUCCESS** (0x00) Interface is successfully set.</span></span>

- <span data-ttu-id="e6cd1-571">**NX_INVALID_INTERFACE** (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-571">**NX_INVALID_INTERFACE** (0x4C) Invalid network interface</span></span>

- <span data-ttu-id="e6cd1-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) DHCP에 사용하도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) 다른 레코드에 사용할 수 있는 레코드가 없음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another</span></span>

- <span data-ttu-id="e6cd1-574">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-574">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-575">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-575">Allowed From</span></span>

<span data-ttu-id="e6cd1-576">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-576">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-577">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-577">Example</span></span>

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="e6cd1-578">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="e6cd1-578">nx_dhcp_start</span></span>

<span data-ttu-id="e6cd1-579">DHCP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-579">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-580">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-580">Prototype</span></span>

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="e6cd1-581">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-581">Description</span></span>

<span data-ttu-id="e6cd1-582">이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스에서 DHCP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-582">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="e6cd1-583">기본적으로 애플리케이션에서 *nx_dhcp_create* 를 호출할 때 기본 인터페이스가 DHCP에 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-583">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="e6cd1-584">IP 인스턴스가 DHCP 클라이언트 인터페이스의 IP 주소에 바인딩되어 있는지 확인하려면 *nx_ip_status_check* 를 사용하여 IP 주소가 유효한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-584">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="e6cd1-585">이미 DHCP를 실행하는 다른 인터페이스가 있는 경우 이 서비스는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-585">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="e6cd1-586">여러 인터페이스가 사용하도록 설정된 경우 특정 인터페이스에서 DHCP를 시작하려면 *nx_dhcp_interface_start* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-586">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-587">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-587">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-588">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-588">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-589">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-589">Return Values</span></span>

- <span data-ttu-id="e6cd1-590">**NX_SUCCESS** (0x00) DHCP를 성공적으로 시작함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-590">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="e6cd1-591">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP가 이미 시작됨</span><span class="sxs-lookup"><span data-stu-id="e6cd1-591">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>

- <span data-ttu-id="e6cd1-592">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-592">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="e6cd1-593">NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="e6cd1-593">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-594">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-594">Allowed From</span></span>

<span data-ttu-id="e6cd1-595">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-595">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-596">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-596">Example</span></span>

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="e6cd1-597">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="e6cd1-597">nx_dhcp_interface_start</span></span>

<span data-ttu-id="e6cd1-598">지정된 인터페이스에서 DHCP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-598">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-599">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-599">Prototype</span></span>

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="e6cd1-600">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-600">Description</span></span>

<span data-ttu-id="e6cd1-601">지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 DHCP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-601">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="e6cd1-602">인터페이스를 DHCP에 사용하도록 설정하는 방법에 대한 자세한 내용은 *nx_dhcp_interface_enable*()을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-602">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="e6cd1-603">기본적으로 애플리케이션에서 *nx_dhcp_create* 를 호출할 때 기본 인터페이스가 DHCP에 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-603">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="e6cd1-604">DHCP 클라이언트를 실행하는 다른 인터페이스가 없는 경우 이 서비스는 DHCP 클라이언트 스레드를 시작/다시 시작하고 DHCP 클라이언트 타이머를 (다시) 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-604">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="e6cd1-605">애플리케이션에서 *nx_ip_status_check* 를 사용하여 IP 주소를 가져왔는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-605">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-606">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-606">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-607">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-607">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="e6cd1-608">**Interface_index** DHCP 클라이언트를 시작하는 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-608">**Interface_index** Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-609">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-609">Return Values</span></span>

- <span data-ttu-id="e6cd1-610">**NX_SUCCESS** (0x00) DHCP를 성공적으로 시작함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-610">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="e6cd1-611">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP 인스턴스가 이미 시작됨</span><span class="sxs-lookup"><span data-stu-id="e6cd1-611">**NX_DHCP_ALREADY_STARTED** (0x93) The DHCP instance has already been started.</span></span>

- <span data-ttu-id="e6cd1-612">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-612">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="e6cd1-613">NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="e6cd1-613">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="e6cd1-614">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-614">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-615">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-615">Allowed From</span></span>

<span data-ttu-id="e6cd1-616">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-616">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-617">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-617">Example</span></span>

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="e6cd1-618">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="e6cd1-618">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="e6cd1-619">DHCP 상태 변경 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-619">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-620">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-620">Prototype</span></span>

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="e6cd1-621">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-621">Description</span></span>

<span data-ttu-id="e6cd1-622">이 서비스는 DHCP 상태 변경을 애플리케이션에 알리기 위해 지정된 dhcp_state_change_notify 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-622">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="e6cd1-623">콜백 함수는 DHCP 클라이언트가 전환된 상태를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-623">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="e6cd1-624">다양한 DHCP 상태와 관련된 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-624">Following are values associated with the various DHCP states:</span></span>

| <span data-ttu-id="e6cd1-625">주</span><span class="sxs-lookup"><span data-stu-id="e6cd1-625">State</span></span>                             | <span data-ttu-id="e6cd1-626">값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-626">Value</span></span> |
|-----------------------------------|-------|
| <span data-ttu-id="e6cd1-627">NX\_DHCP\_STATE\_BOOT</span><span class="sxs-lookup"><span data-stu-id="e6cd1-627">NX\_DHCP\_STATE\_BOOT</span></span>             | <span data-ttu-id="e6cd1-628">1</span><span class="sxs-lookup"><span data-stu-id="e6cd1-628">1</span></span>     |
| <span data-ttu-id="e6cd1-629">NX\_DHCP\_STATE\_INIT</span><span class="sxs-lookup"><span data-stu-id="e6cd1-629">NX\_DHCP\_STATE\_INIT</span></span>             | <span data-ttu-id="e6cd1-630">2</span><span class="sxs-lookup"><span data-stu-id="e6cd1-630">2</span></span>     |
| <span data-ttu-id="e6cd1-631">NX\_DHCP\_STATE\_SELECTING</span><span class="sxs-lookup"><span data-stu-id="e6cd1-631">NX\_DHCP\_STATE\_SELECTING</span></span>        | <span data-ttu-id="e6cd1-632">3</span><span class="sxs-lookup"><span data-stu-id="e6cd1-632">3</span></span>     |
| <span data-ttu-id="e6cd1-633">NX\_DHCP\_STATE\_REQUESTING</span><span class="sxs-lookup"><span data-stu-id="e6cd1-633">NX\_DHCP\_STATE\_REQUESTING</span></span>       | <span data-ttu-id="e6cd1-634">4</span><span class="sxs-lookup"><span data-stu-id="e6cd1-634">4</span></span>     |
| <span data-ttu-id="e6cd1-635">NX\_DHCP\_STATE\_BOUND</span><span class="sxs-lookup"><span data-stu-id="e6cd1-635">NX\_DHCP\_STATE\_BOUND</span></span>            | <span data-ttu-id="e6cd1-636">5</span><span class="sxs-lookup"><span data-stu-id="e6cd1-636">5</span></span>     |
| <span data-ttu-id="e6cd1-637">NX\_DHCP\_STATE\_RENEWING</span><span class="sxs-lookup"><span data-stu-id="e6cd1-637">NX\_DHCP\_STATE\_RENEWING</span></span>         | <span data-ttu-id="e6cd1-638">6</span><span class="sxs-lookup"><span data-stu-id="e6cd1-638">6</span></span>     |
| <span data-ttu-id="e6cd1-639">NX\_DHCP\_STATE\_REBINDING</span><span class="sxs-lookup"><span data-stu-id="e6cd1-639">NX\_DHCP\_STATE\_REBINDING</span></span>        | <span data-ttu-id="e6cd1-640">7</span><span class="sxs-lookup"><span data-stu-id="e6cd1-640">7</span></span>     |
| <span data-ttu-id="e6cd1-641">NX_DHCP_STATE_FORCERENEW</span><span class="sxs-lookup"><span data-stu-id="e6cd1-641">NX_DHCP_STATE_FORCERENEW</span></span>          | <span data-ttu-id="e6cd1-642">8</span><span class="sxs-lookup"><span data-stu-id="e6cd1-642">8</span></span>     |
| <span data-ttu-id="e6cd1-643">NX\_DHCP\_STATE\_ADDRESS\_PROBING</span><span class="sxs-lookup"><span data-stu-id="e6cd1-643">NX\_DHCP\_STATE\_ADDRESS\_PROBING</span></span> | <span data-ttu-id="e6cd1-644">9</span><span class="sxs-lookup"><span data-stu-id="e6cd1-644">9</span></span>     |


### <a name="input-parameters"></a><span data-ttu-id="e6cd1-645">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-645">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-646">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-646">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="e6cd1-647">**dhcp_state_change_notify** 상태 변경 콜백 함수 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-647">**dhcp_state_change_notify** State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-648">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-648">Return Values</span></span>

- <span data-ttu-id="e6cd1-649">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-649">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="e6cd1-650">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-650">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="e6cd1-651">NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="e6cd1-651">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-652">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-652">Allowed From</span></span>

<span data-ttu-id="e6cd1-653">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="e6cd1-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-654">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-654">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="e6cd1-655">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="e6cd1-655">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="e6cd1-656">지정된 인터페이스에서 DHCP 상태 변경 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-656">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-657">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-657">Prototype</span></span>

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="e6cd1-658">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-658">Description</span></span>

<span data-ttu-id="e6cd1-659">이 서비스는 DHCP 상태 변경을 애플리케이션에 알리기 위해 지정된 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-659">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="e6cd1-660">콜백 함수 입력 인수는 인터페이스 인덱스 및 DHCP 클라이언트가 해당 인터페이스에서 전환된 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-660">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="e6cd1-661">상태 변경 함수에 대한 자세한 내용은 *nx_dhcp_state_change_notify*()를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-661">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-662">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-662">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-663">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-663">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="e6cd1-664">**dhcp_interface_state_change_notify** 애플리케이션 콜백 함수 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-664">**dhcp_interface_state_change_notify** Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-665">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-665">Return Values</span></span>

- <span data-ttu-id="e6cd1-666">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-666">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="e6cd1-667">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-667">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-668">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-668">Allowed From</span></span>

<span data-ttu-id="e6cd1-669">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="e6cd1-669">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-670">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-670">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="e6cd1-671">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="e6cd1-671">nx_dhcp_stop</span></span>

<span data-ttu-id="e6cd1-672">DHCP 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-672">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-673">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-673">Prototype</span></span>

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="e6cd1-674">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-674">Description</span></span>

<span data-ttu-id="e6cd1-675">이 서비스는 DHCP 처리를 시작한 모든 인터페이스에서 DHCP 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-675">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="e6cd1-676">DHCP를 처리하는 인터페이스가 없는 경우 이 서비스는 DHCP 클라이언트 스레드를 일시 중단하고 DHCP 클라이언트 타이머를 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-676">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="e6cd1-677">여러 인터페이스가 DHCP에 사용하도록 설정된 경우 특정 인터페이스에서 DHCP를 중지하려면 *nx_dhcp_interface_stop* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-677">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-678">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-678">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-679">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-679">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-680">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-680">Return Values</span></span>

- <span data-ttu-id="e6cd1-681">**NX_SUCCESS** (0x00) DHCP를 성공적으로 중지함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-681">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="e6cd1-682">**NX_DHCP_NOT_STARTED** (0x96) DHCP 인스턴스가 시작되지 않음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-682">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started.</span></span>

- <span data-ttu-id="e6cd1-683">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-683">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="e6cd1-684">NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="e6cd1-684">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-685">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-685">Allowed From</span></span>

<span data-ttu-id="e6cd1-686">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-686">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-687">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-687">Example</span></span>

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="e6cd1-688">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="e6cd1-688">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="e6cd1-689">지정된 인터페이스에서 DHCP 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-689">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-690">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-690">Prototype</span></span>

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="e6cd1-691">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-691">Description</span></span>

<span data-ttu-id="e6cd1-692">DHCP가 이미 시작된 경우 이 서비스는 지정된 인터페이스에서 DHCP 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-692">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="e6cd1-693">DHCP를 실행하는 다른 인터페이스가 없는 경우 DHCP 스레드 및 타이머가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-693">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-694">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-694">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-695">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-695">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="e6cd1-696">**Interface_index** DHCP 처리를 중지하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-696">**Interface_index** Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-697">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-697">Return Values</span></span>

- <span data-ttu-id="e6cd1-698">**NX_SUCCESS** (0x00) DHCP를 성공적으로 중지함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-698">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="e6cd1-699">**NX_DHCP_NOT_STARTED** (0x96) DHCP가 시작되지 않음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-699">**NX_DHCP_NOT_STARTED** (0x96) DHCP not started.</span></span>

- <span data-ttu-id="e6cd1-700">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-700">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="e6cd1-701">NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="e6cd1-701">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="e6cd1-702">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-702">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-703">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-703">Allowed From</span></span>

<span data-ttu-id="e6cd1-704">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-704">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-705">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-705">Example</span></span>

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="e6cd1-706">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="e6cd1-706">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="e6cd1-707">마지막 서버 응답에서 DHCP 옵션을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-707">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-708">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-708">Prototype</span></span>

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="e6cd1-709">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-709">Description</span></span>

<span data-ttu-id="e6cd1-710">이 서비스는 DHCP 클라이언트 레코드에 있는 DHCP에 사용하도록 설정된 첫 번째 인터페이스에서 DHCP 옵션 버퍼로부터 지정된 DHCP 옵션을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-710">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="e6cd1-711">성공하면 옵션 데이터가 지정된 버퍼에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-711">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-712">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-712">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-713">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-713">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>  

- <span data-ttu-id="e6cd1-714">**request_option** RFC에서 지정한 DHCP 옵션.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-714">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="e6cd1-715">*nx_dhcp.h* 의 NX_DHCP_OPTION 옵션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-715">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>

- <span data-ttu-id="e6cd1-716">**destination_ptr** 응답 문자열의 대상에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-716">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="e6cd1-717">**destination_size** 대상 및 반환 시 반환되는 바이트 수를 저장할 대상의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-717">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-718">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-718">Return Values</span></span>

- <span data-ttu-id="e6cd1-719">**NX_SUCCESS** (0x00) 옵션을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-719">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="e6cd1-720">**NX_DHCP_NOT_BOUND** (0x94) DHCP 클라이언트가 바인딩되지 않음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-720">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound.</span></span>

- <span data-ttu-id="e6cd1-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP에 사용하도록 설정된 인터페이스가 없음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="e6cd1-722">**NX_DHCP_DEST_TO_SMALL** (0x95) 대상이 너무 작아서 응답을 보유할 수 없음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-722">**NX_DHCP_DEST_TO_SMALL** (0x95) Destination is too small to hold response.</span></span>

- <span data-ttu-id="e6cd1-723">**NX_DHCP_PARSE_ERROR** (0x97) 서버 응답에 DHCP 옵션이 없음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-723">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="e6cd1-724">NX_PTR_ERROR (0x16) 잘못된 입력 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-724">NX_PTR_ERROR (0x16) Invalid input pointer.</span></span>

- <span data-ttu-id="e6cd1-725">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-725">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-726">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-726">Allowed From</span></span>

<span data-ttu-id="e6cd1-727">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-727">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-728">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-728">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="e6cd1-729">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="e6cd1-729">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="e6cd1-730">지정한 인터페이스에서 마지막 서버 응답으로부터 DHCP 옵션을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-730">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-731">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-731">Prototype</span></span>

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="e6cd1-732">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-732">Description</span></span>

<span data-ttu-id="e6cd1-733">지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 DHCP 옵션 버퍼로부터 지정된 DHCP 옵션을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-733">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="e6cd1-734">성공하면 옵션 데이터가 지정된 버퍼에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-734">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-735">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-735">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-736">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-736">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="e6cd1-737">**Interface_index** 지정된 옵션을 검색하는 인덱스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-737">**Interface_index** Index on which to retrieve the specified option</span></span>  

- <span data-ttu-id="e6cd1-738">**request_option** RFC에서 지정한 DHCP 옵션.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-738">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="e6cd1-739">*nx_dhcp.h* 의 NX_DHCP_OPTION 옵션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-739">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>  

- <span data-ttu-id="e6cd1-740">**destination_ptr** 응답 문자열의 대상에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-740">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="e6cd1-741">**destination_size** 대상 및 반환 시 반환되는 바이트 수를 저장할 대상의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-741">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-742">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-742">Return Values</span></span>

- <span data-ttu-id="e6cd1-743">**NX_SUCCESS** (0x00) 옵션을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-743">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="e6cd1-744">**NX_DHCP_NOT_BOUND** (0x94) IP 주소가 할당되지 않음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-744">**NX_DHCP_NOT_BOUND** (0x94) IP address not assigned</span></span>

- <span data-ttu-id="e6cd1-745">**NX_DHCP_DEST_TO_SMALL** (0x95) 버퍼가 너무 작음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-745">**NX_DHCP_DEST_TO_SMALL** (0x95) Buffer is too small</span></span>

- <span data-ttu-id="e6cd1-746">**NX_DHCP_PARSE_ERROR** (0x97) 서버 응답에 DHCP 옵션이 없음</span><span class="sxs-lookup"><span data-stu-id="e6cd1-746">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="e6cd1-747">NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-747">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="e6cd1-748">NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="e6cd1-748">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="e6cd1-749">NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6cd1-749">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-750">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-750">Allowed From</span></span>

<span data-ttu-id="e6cd1-751">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-752">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-752">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="e6cd1-753">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="e6cd1-753">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="e6cd1-754">4바이트를 ULONG으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-754">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-755">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-755">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="e6cd1-756">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-756">Description</span></span>

<span data-ttu-id="e6cd1-757">이 서비스는 "option_string_ptr"에서 가리키는 4개 문자를 서명되지 않은 long 값으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-757">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="e6cd1-758">특히 IP 주소가 있는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-758">It is especially useful when IP addresses are present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-759">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-759">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-760">**option_string_ptr** 이전에 검색한 옵션 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-760">**option_string_ptr** Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-761">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-761">Return Values</span></span>

- <span data-ttu-id="e6cd1-762">**Value** 처음 4바이트의 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-762">**Value** Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-763">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-763">Allowed From</span></span>

<span data-ttu-id="e6cd1-764">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-765">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-765">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="e6cd1-766">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="e6cd1-766">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="e6cd1-767">사용자 제공 옵션을 추가하기 위한 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-767">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="e6cd1-768">프로토타입</span><span class="sxs-lookup"><span data-stu-id="e6cd1-768">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="e6cd1-769">Description</span><span class="sxs-lookup"><span data-stu-id="e6cd1-769">Description</span></span>

<span data-ttu-id="e6cd1-770">이 서비스는 사용자 제공 옵션을 추가하기 위해 지정된 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-770">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="e6cd1-771">콜백 함수가 지정된 경우 애플리케이션에서 사용자가 제공한 옵션을 iface_index 및 message_type별로 패킷에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-771">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

> [!NOTE]
> <span data-ttu-id="e6cd1-772">사용자의 루틴에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-772">In user’s routine.</span></span> <span data-ttu-id="e6cd1-773">사용자가 제공한 옵션을 추가하는 경우 애플리케이션에서 DHCP 옵션 형식을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-773">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="e6cd1-774">사용자 옵션의 총 크기는 user_option_length보다 작거나 같아야 하며, user_option_length를 실제 옵션 길이로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-774">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="e6cd1-775">옵션이 성공적으로 추가되면 NX_TRUE를 반환하고, 그렇지 않으면 NX_FALSE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e6cd1-775">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6cd1-776">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e6cd1-776">Input Parameters</span></span>

- <span data-ttu-id="e6cd1-777">**ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-777">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="e6cd1-778">**dhcp_user_option_add** 사용자 옵션 추가 함수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-778">**dhcp_user_option_add** Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6cd1-779">반환 값</span><span class="sxs-lookup"><span data-stu-id="e6cd1-779">Return Values</span></span>

- <span data-ttu-id="e6cd1-780">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="e6cd1-780">**NX_SUCCESS** (0x00) Successful callback set.</span></span>

- <span data-ttu-id="e6cd1-781">NX_PTR_ERROR (0x16) 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="e6cd1-781">NX_PTR_ERROR (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6cd1-782">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="e6cd1-782">Allowed From</span></span>

<span data-ttu-id="e6cd1-783">스레드</span><span class="sxs-lookup"><span data-stu-id="e6cd1-783">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6cd1-784">예제</span><span class="sxs-lookup"><span data-stu-id="e6cd1-784">Example</span></span>

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
