---
title: 챕터 3 - Azure RTOS NetX Duo DHCP 클라이언트 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX Duo DHCP 클라이언트 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f143a443221ae08848316a458a630a0790108198
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810933"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="ecd63-103">챕터 3 - Azure RTOS NetX Duo DHCP 클라이언트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="ecd63-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="ecd63-104">이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX Duo DHCP 클라이언트 서비스에 대해 알파벳 순서로 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-104">This chapter contains a description of all Azure RTOS NetX Duo DHCP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="ecd63-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ecd63-106">**nx_dhcp_create**: *DHCP 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>
- <span data-ttu-id="ecd63-107">**nx_dhcp_clear_broadcast_flag**: *클라이언트 메시지에서 브로드캐스트 플래그 지우기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-107">**nx_dhcp_clear_broadcast_flag**: *Clear broadcast flag on Client messages*</span></span>
- <span data-ttu-id="ecd63-108">**nx_dhcp_delete**: *DHCP 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="ecd63-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>
- <span data-ttu-id="ecd63-109">**nx_dhcp_force_renew**: *강제 갱신 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-109">**nx_dhcp_force_renew**: *Send a force renew message*</span></span>
- <span data-ttu-id="ecd63-110">**nx_dhcp_packet_pool_set**: *DHCP 클라이언트 패킷 풀 설정*</span><span class="sxs-lookup"><span data-stu-id="ecd63-110">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>
- <span data-ttu-id="ecd63-111">**nx_dhcp_decline**: *서버에 거부 메시지* 보내기</span><span class="sxs-lookup"><span data-stu-id="ecd63-111">**nx_dhcp_decline**: Send *Decline message to server*</span></span>
- <span data-ttu-id="ecd63-112">**nx_dhcp_release**: *서버에 릴리스 메시지* 보내기</span><span class="sxs-lookup"><span data-stu-id="ecd63-112">**nx_dhcp_release**: Send *Release message to server*</span></span>
- <span data-ttu-id="ecd63-113">**nx_dhcp_reinitialize**: *DHCP 클라이언트 네트워크 매개 변수 지우기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>
- <span data-ttu-id="ecd63-114">**nx_dhcp_request_client_ip**: *특정 IP 주소 지정*</span><span class="sxs-lookup"><span data-stu-id="ecd63-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>
- <span data-ttu-id="ecd63-115">**nx_dhcp_send_request**: *서버에 DHCP 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>
- <span data-ttu-id="ecd63-116">**nx_dhcp_start**: *DHCP 클라이언트 처리 시작*</span><span class="sxs-lookup"><span data-stu-id="ecd63-116">**nx_dhcp_start**: *Start the DHCP Client processing*</span></span>
- <span data-ttu-id="ecd63-117">**nx_dhcp_stop**: *DHCP 클라이언트 처리 중지*</span><span class="sxs-lookup"><span data-stu-id="ecd63-117">**nx_dhcp_stop**: *Stop the DHCP Client processing*</span></span>
- <span data-ttu-id="ecd63-118">**nx_dhcp_set_interface_index**: *DHCP 클라이언트를 실행하는 인터페이스 설정*</span><span class="sxs-lookup"><span data-stu-id="ecd63-118">**nx_dhcp_set_interface_index**: *Set the interface to run DHCP Client*</span></span>
- <span data-ttu-id="ecd63-119">**nx_dhcp_server_address_get**: *DHCP 서버 IP 주소 가져오기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-119">**nx_dhcp_server_address_get**: *Get the DHCP server IP address*</span></span>
- <span data-ttu-id="ecd63-120">**nx_dhcp_state_change_notify**: *DHCP 상태가 변경될 때 콜백 함수 설정*</span><span class="sxs-lookup"><span data-stu-id="ecd63-120">**nx_dhcp_state_change_notify**: *Set the callback function when DHCP state changes*</span></span>
- <span data-ttu-id="ecd63-121">**nx_dhcp_user_option_retrieve**: *지정된 DHCP 옵션 검색*</span><span class="sxs-lookup"><span data-stu-id="ecd63-121">**nx_dhcp_user_option_retrieve**: *Retrieve the specified DHCP option*</span></span>
- <span data-ttu-id="ecd63-122">**nx_dhcp_user_option_convert**: *4바이트를 ULONG으로 변환*</span><span class="sxs-lookup"><span data-stu-id="ecd63-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="ecd63-123">인터페이스 특정 DHCP 클라이언트 서비스:</span><span class="sxs-lookup"><span data-stu-id="ecd63-123">Interface specific DHCP Client services:</span></span>
 
- <span data-ttu-id="ecd63-124">**nx_dhcp_interface_clear_broadcast_flag**: *지정된 인터페이스의 클라이언트 메시지에서 브로드캐스트 플래그 지우기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>
- <span data-ttu-id="ecd63-125">**nx_dhcp_interface_enable**: *지정된 인터페이스에서 DHCP를 실행하는 인터페이스 사용*</span><span class="sxs-lookup"><span data-stu-id="ecd63-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="ecd63-126">**nx_dhcp_interface_disable**: *지정된 인터페이스에서 DHCP를 실행하는 인터페이스 사용 안 함*</span><span class="sxs-lookup"><span data-stu-id="ecd63-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="ecd63-127">**nx_dhcp_interface_decline**: *지정된 인터페이스에서 서버에 거부 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>
- <span data-ttu-id="ecd63-128">**nx_dhcp_interface_force_renew**: *지정된 인터페이스에서 강제 갱신 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>
- <span data-ttu-id="ecd63-129">**nx_dhcp_interface_reinitialize**: *지정된 인터페이스에서 DHCP 클라이언트 네트워크 매개 변수 지우기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>
- <span data-ttu-id="ecd63-130">**nx_dhcp_interface_release**: *지정된 인터페이스에서 서버에 릴리스 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-130">**nx_dhcp_interface_release**: *Send Release message to server on the specified interface*</span></span>
- <span data-ttu-id="ecd63-131">**nx_dhcp_interface_request_client_ip**: *지정된 인터페이스에서 특정 IP 주소 지정*</span><span class="sxs-lookup"><span data-stu-id="ecd63-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>
- <span data-ttu-id="ecd63-132">**nx_dhcp_interface_send_request**: *지정된 인터페이스에서 서버에 DHCP 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>
- <span data-ttu-id="ecd63-133">**nx_dhcp_interface_server_address_get**: *지정된 인터페이스에서 DHCP 서버 IP 주소 가져오기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>
- <span data-ttu-id="ecd63-134">**nx_dhcp_interface_start**: *지정된 인터페이스에서 DHCP 클라이언트 처리 시작*</span><span class="sxs-lookup"><span data-stu-id="ecd63-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="ecd63-135">**nx_dhcp_interface_stop**: *지정된 인터페이스에서 DHCP 클라이언트 처리 중지*</span><span class="sxs-lookup"><span data-stu-id="ecd63-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="ecd63-136">**nx_dhcp_interface_state_change_notify**: *지정된 인터페이스에서 DHCP 상태가 변경될 때 콜백 함수 설정*</span><span class="sxs-lookup"><span data-stu-id="ecd63-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>
- <span data-ttu-id="ecd63-137">**nx_dhcp_interface_user_option_retrieve**: *지정된 인터페이스에서 지정된 DHCP 옵션 검색*</span><span class="sxs-lookup"><span data-stu-id="ecd63-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="ecd63-138">NX_DHCP_CLIENT_RESORE_STATE가 정의된 경우 DHCP 클라이언트 서비스:</span><span class="sxs-lookup"><span data-stu-id="ecd63-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="ecd63-139">**nx_dhcp_resume**: *이전에 설정된 DHCP 클라이언트 상태 다시 시작*</span><span class="sxs-lookup"><span data-stu-id="ecd63-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>
- <span data-ttu-id="ecd63-140">**nx_dhcp_suspend**: *DHCP 클라이언트 상태 처리 일시 중단*</span><span class="sxs-lookup"><span data-stu-id="ecd63-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>
- <span data-ttu-id="ecd63-141">**nx_dhcp_client_get_record**: *DHCP 클라이언트 상태에 대한 레코드 만들기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>
- <span data-ttu-id="ecd63-142">**nx_dhcp_client_restore_record**: *이전에 저장된 레코드를 DHCP 클라이언트에 복원*</span><span class="sxs-lookup"><span data-stu-id="ecd63-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>
- <span data-ttu-id="ecd63-143">**nx_dhcp_client_update_time_remaining**: *남아 있는 현재 DHCP 상태 시간 업데이트*</span><span class="sxs-lookup"><span data-stu-id="ecd63-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="ecd63-144">NX_DHCP_CLIENT_RESORE_STATE가 정의된 경우 인터페이스 특정 DHCP 클라이언트 서비스:</span><span class="sxs-lookup"><span data-stu-id="ecd63-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="ecd63-145">**nx_dhcp_client_interface_get_record**: *지정된 인터페이스에서 DHCP 클라이언트 상태에 대한 레코드 만들기*</span><span class="sxs-lookup"><span data-stu-id="ecd63-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>
- <span data-ttu-id="ecd63-146">**nx_dhcp_client_interface_restore_record**: *지정된 인터페이스에서 이전에 저장된 레코드를 DHCP 클라이언트에 복원*</span><span class="sxs-lookup"><span data-stu-id="ecd63-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>
- <span data-ttu-id="ecd63-147">**nx_dhcp_client_interface_update_time_remaining**: *지정된 인터페이스에서 남아 있는 현재 DHCP 상태 시간 업데이트*</span><span class="sxs-lookup"><span data-stu-id="ecd63-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="ecd63-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="ecd63-148">nx_dhcp_create</span></span>

<span data-ttu-id="ecd63-149">DHCP 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-150">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-150">Prototype</span></span>

```c
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="ecd63-151">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-151">Description</span></span>

<span data-ttu-id="ecd63-152">이 서비스는 이전에 만든 IP 인스턴스에 대한 DHCP 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="ecd63-153">기본적으로 기본 인터페이스가 DHCP를 실행하는 데 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="ecd63-154">이름 입력은 DHCP 클라이언트의 NetX Duo 구현에서 사용되지 않지만 호스트 이름에 대한 RFC 1035 조건을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-154">The name input, while not used in the NetX Duo implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="ecd63-155">총 길이는 255자를 초과할 수 없으며, 점으로 구분된 레이블은 문자로 시작하고 문자 또는 숫자로 끝나야 하며, 하이픈은 포함할 수 있지만 영숫자가 아닌 다른 문자는 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="ecd63-156">애플리케이션에서 IP 인스턴스에 등록된 다른 인터페이스인 DHCP를 실행하려는 경우(*nx_ip_interface_attach* 사용) 애플리케이션에서 *nx_dhcp_set_interface_index* 를 호출하여 해당 인터페이스에서만 DHCP를 실행하거나 *nx_dhcp_interface_enable* 을 호출하여 해당 인터페이스에서도 DHCP를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="ecd63-157">자세한 내용은 이러한 서비스에 대한 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-157">See description of these services for more details.</span></span>

>[!NOTE]
> <span data-ttu-id="ecd63-158">애플리케이션에서 DHCP 클라이언트 패킷 풀 페이로드가 RFC 2131 섹션 2(548바이트의 DHCP 메시지 데이터와 UDP, IP 및 실제 네트워크 프레임 헤더)에서 지정한 최소 DHCP 메시지 크기를 지원할 수 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-159">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-159">Input Parameters</span></span>

- <span data-ttu-id="ecd63-160">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-160">**dhcp_ptr**: Pointer to DHCP control block.</span></span> 
- <span data-ttu-id="ecd63-161">**ip_ptr**: 이전에 만든 IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-161">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="ecd63-162">**name_ptr**: DHCP 인스턴스의 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-162">**name_ptr**: Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-163">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-163">Return Values</span></span>

- <span data-ttu-id="ecd63-164">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="ecd63-164">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="ecd63-165">**NX_DHCP_INVALID_NAME**: (0xA8) 잘못된 호스트 이름</span><span class="sxs-lookup"><span data-stu-id="ecd63-165">**NX_DHCP_INVALID_NAME**: (0xA8) Invalid host name</span></span>
- <span data-ttu-id="ecd63-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) DHCP 메시지에 대한 페이로드가 너무 작음</span><span class="sxs-lookup"><span data-stu-id="ecd63-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) Payload too small for DHCP message</span></span>
- <span data-ttu-id="ecd63-167">NX_PTR_ERROR: (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-167">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-168">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-168">Allowed From</span></span>

<span data-ttu-id="ecd63-169">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="ecd63-169">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-170">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-170">Example</span></span>

```c
/* Create a DHCP instance.  */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created.  */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="ecd63-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="ecd63-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="ecd63-172">DHCP를 실행하도록 지정된 인터페이스를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="ecd63-173">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-173">Prototype</span></span>

```c
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ecd63-174">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-174">Description</span></span>

<span data-ttu-id="ecd63-175">이 서비스를 사용하면 지정된 인터페이스에서 DHCP를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="ecd63-176">기본적으로 기본 인터페이스가 DHCP 클라이언트에 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="ecd63-177">이 시점에서 *nx_dhcp_interface_start* 를 호출하여 이 인터페이스에서 DHCP를 시작하거나 사용하도록 설정된 모든 *nx_dhcp_start* 인터페이스에서 DHCP를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

>[!NOTE] 
> <span data-ttu-id="ecd63-178">애플리케이션에서 먼저 *nx_ip_interface_attach.* 를 사용하여 이 인터페이스를 IP 인스턴스에 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-178">The application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="ecd63-179">또한 이 인터페이스를 사용하도록 설정된 인터페이스 목록에 추가하려면 사용 가능한 DHCP 클라이언트 인터페이스 '레코드'가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="ecd63-180">기본적으로 NX_DHCP_CLIENT_MAX_RECORDS가 1로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="ecd63-181">이 옵션을 DHCP 클라이언트를 동시에 실행하는 데 필요한 최대 인터페이스 수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="ecd63-182">일반적으로 NX_DHCP_CLIENT_MAX_RECORDS는 NX_MAX_PHYSICAL_INTERFACES와 동일합니다. 그러나 DHCP 클라이언트를 실행하는 데 필요한 것보다 더 많은 실제 인터페이스가 디바이스에 있는 경우 NX_DHCP_CLIENT_MAX_RECORDS를 해당 숫자보다 작게 설정하여 메모리를 절약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="ecd63-183">실제 인터페이스와 DHCP 클라이언트 인터페이스 레코드의 일대일 매핑이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="ecd63-184">이 서비스와 *nx_dhcp_set_interface_index* 의 차이점은 후자는 DHCP를 실행하는 단일 인터페이스만 설정하는 반면, 이 서비스는 지정된 인터페이스를 DHCP에 사용하도록 설정된 클라이언트 인터페이스 목록에 추가한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="ecd63-185">DHCP에 대한 인터페이스를 사용하지 않도록 설정하기 위해 애플리케이션에서</span><span class="sxs-lookup"><span data-stu-id="ecd63-185">To disable an interface for DHCP, the application can call the</span></span>

<span data-ttu-id="ecd63-186">*nx_dhcp_interface_disable* 서비스를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-186">*nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-187">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-187">Input Parameters</span></span>

- <span data-ttu-id="ecd63-188">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-188">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ecd63-189">**interface_index**: DHCP를 사용하도록 설정하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-189">**interface_index**: Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-190">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-190">Return Values</span></span>

- <span data-ttu-id="ecd63-191">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 사용하도록 설정함</span><span class="sxs-lookup"><span data-stu-id="ecd63-191">**NX_SUCCESS**: (0x00) Successful DHCP enable</span></span>
- <span data-ttu-id="ecd63-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) DHCP에 사용하도록 설정할 다른 인터페이스에 사용할 수 있는 레코드가 없음</span><span class="sxs-lookup"><span data-stu-id="ecd63-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another Interface to be enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) DHCP에 사용하도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-194">NX_PTR_ERROR: (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-194">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="ecd63-195">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-195">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-196">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-196">Allowed From</span></span>

<span data-ttu-id="ecd63-197">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="ecd63-197">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-198">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-198">Example</span></span>

```c
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface.  NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled.  */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1.  */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="ecd63-199">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="ecd63-199">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="ecd63-200">DHCP를 실행하도록 지정된 인터페이스를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-200">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="ecd63-201">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-201">Prototype</span></span>

```c

UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ecd63-202">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-202">Description</span></span>

<span data-ttu-id="ecd63-203">이 서비스를 사용하지 않으면 지정된 인터페이스에서 DHCP를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-203">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="ecd63-204">이 인터페이스에서 DHCP 클라이언트를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-204">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="ecd63-205">DHCP 클라이언트를 다시 시작하려면 애플리케이션에서 *nx_dhcp_interface_enable* 을 사용하여 인터페이스를 다시 사용하도록 설정하고 *nx_dhcp_interface_start* 를 호출하여 DHCP를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-205">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-206">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-206">Input Parameters</span></span>

- <span data-ttu-id="ecd63-207">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-207">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ecd63-208">**interface_index**: DHCP를 사용하지 않도록 설정하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-208">**interface_index**: Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-209">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-209">Return Values</span></span>

- <span data-ttu-id="ecd63-210">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="ecd63-210">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="ecd63-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-212">NX_PTR_ERROR: (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-212">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="ecd63-213">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-213">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="ecd63-214">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-214">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-215">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-215">Allowed From</span></span>

<span data-ttu-id="ecd63-216">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-216">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-217">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-217">Example</span></span>

```c
/* Disable DHCP on a secondary interface. */

status =  nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled.  */
```
## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="ecd63-218">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="ecd63-218">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="ecd63-219">DHCP 브로드캐스트 플래그를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-219">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-220">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-220">Prototype</span></span>

```c
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="ecd63-221">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-221">Description</span></span>

<span data-ttu-id="ecd63-222">이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스에 대한 DHCP 메시지 헤더의 브로드캐스트 플래그를 설정하거나 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-222">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ecd63-223">일부 DHCP 메시지(예: DISCOVER)의 경우 클라이언트에 IP 주소가 없으므로 브로드캐스트 플래그가 브로드캐스트로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-223">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="ecd63-224">clear_flag 값:</span><span class="sxs-lookup"><span data-stu-id="ecd63-224">clear_flag values:</span></span> 

- <span data-ttu-id="ecd63-225">**NX_TRUE**: 브로드캐스트 플래그가 지워짐(요청 유니캐스트 응답)</span><span class="sxs-lookup"><span data-stu-id="ecd63-225">**NX_TRUE**: broadcast flag is cleared (request unicast response)</span></span>
- <span data-ttu-id="ecd63-226">**NX_FALSE**: 브로드캐스트 플래그가 설정됨(요청 브로드캐스트 응답)</span><span class="sxs-lookup"><span data-stu-id="ecd63-226">**NX_FALSE**: broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="ecd63-227">이 서비스는 라우터를 통해 DHCP 서버에 도달해야 하는 DHCP 클라이언트를 위한 것입니다. 여기서 라우터는 브로드캐스트 메시지 전달을 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-227">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-228">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-228">Input Parameters</span></span>

- <span data-ttu-id="ecd63-229">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-229">**dhcp_ptr**: Pointer to DHCP control block</span></span>  
- <span data-ttu-id="ecd63-230">**clear_flag**: 브로드캐스트 플래그를 설정하는 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-230">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-231">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-231">Return Values</span></span>

- <span data-ttu-id="ecd63-232">**NX_SUCCESS**: (0x00) 플래그를 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="ecd63-232">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="ecd63-233">NX_PTR_ERROR: (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-233">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-234">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-234">Allowed From</span></span>

<span data-ttu-id="ecd63-235">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="ecd63-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-236">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-236">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response).  */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="ecd63-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="ecd63-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="ecd63-238">지정된 인터페이스에서 브로드캐스트 플래그를 설정하거나 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-239">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-239">Prototype</span></span>

```c
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr, 
                                            UINT interface_index, 
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="ecd63-240">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-240">Description</span></span>

<span data-ttu-id="ecd63-241">이 서비스를 사용하면 DHCP 클라이언트 호스트 애플리케이션이 DHCP 클라이언트 메시지의 브로드캐스트 플래그를 지정된 인터페이스의 DHCP 서버로 설정하거나 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="ecd63-242">자세한 내용은 **nx_dhcp_clear_broadcast_flag** 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-242">For more details see **nx_dhcp_clear_broadcast_flag**.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-243">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-243">Input Parameters</span></span>

- <span data-ttu-id="ecd63-244">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-244">**dhcp_ptr**: Pointer to DHCP control block</span></span>
- <span data-ttu-id="ecd63-245">**interface_index**: 브로드캐스트 플래그를 설정하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-245">**interface_index**: Index of interface to set the broadcast flag</span></span>
- <span data-ttu-id="ecd63-246">**clear_flag**: 브로드캐스트 플래그를 설정하는 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-246">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-247">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-247">Return Values</span></span>

- <span data-ttu-id="ecd63-248">**NX_SUCCESS**: (0x00) 플래그를 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="ecd63-248">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="ecd63-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-250">NX_PTR_ERROR: (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-250">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="ecd63-251">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-251">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-252">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-252">Allowed From</span></span>

<span data-ttu-id="ecd63-253">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="ecd63-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-254">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-254">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface.  */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="ecd63-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="ecd63-255">nx_dhcp_delete</span></span>

<span data-ttu-id="ecd63-256">DHCP 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-257">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-257">Prototype</span></span>

```c
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ecd63-258">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-258">Description</span></span>

<span data-ttu-id="ecd63-259">이 서비스는 이전에 만든 DHCP 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-260">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-260">Input Parameters</span></span>

- <span data-ttu-id="ecd63-261">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-261">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-262">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-262">Return Values</span></span>

- <span data-ttu-id="ecd63-263">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="ecd63-263">**NX_SUCCESS**: (0x00) Successful DHCP delete.</span></span>
- <span data-ttu-id="ecd63-264">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-264">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ecd63-265">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-265">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-266">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-266">Allowed From</span></span>

<span data-ttu-id="ecd63-267">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-268">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-268">Example</span></span>

```c
/* Delete a DHCP instance.  */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted.  */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="ecd63-269">nx_dhcp_ force_renew</span><span class="sxs-lookup"><span data-stu-id="ecd63-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="ecd63-270">강제 갱신 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="ecd63-271">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-271">Prototype</span></span>

```c
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ecd63-272">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-272">Description</span></span>

<span data-ttu-id="ecd63-273">이 서비스를 사용하면 DHCP에 사용하도록 설정된 호스트 애플리케이션의 모든 인터페이스에서 강제 갱신 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ecd63-274">DHCP 클라이언트는 BOUND 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="ecd63-275">이 함수는 T1 시간 제한이 만료되기 전에 DHCP 클라이언트에서 갱신을 시도하도록 상태를 RENEW로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="ecd63-276">여러 인터페이스에서 DHCP를 사용하도록 설정된 경우 특정 인터페이스에서 강제 갱신을 보내려면 *nx_dhcp_interface_force_renew* 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-277">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-277">Input Parameters</span></span>

- <span data-ttu-id="ecd63-278">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-278">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-279">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-279">Return Values</span></span>

- <span data-ttu-id="ecd63-280">**NX_SUCCESS**: (0x00) 강제 갱신을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="ecd63-280">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>
- <span data-ttu-id="ecd63-281">**NX_DHCP_NOT_BOUND**: (0x94) 클라이언트 IP 주소가 바인딩되지 않음</span><span class="sxs-lookup"><span data-stu-id="ecd63-281">**NX_DHCP_NOT_BOUND**: (0x94) Client IP address not bound.</span></span>  
- <span data-ttu-id="ecd63-282">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-282">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ecd63-283">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-283">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-284">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-284">Allowed From</span></span>

<span data-ttu-id="ecd63-285">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-285">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-286">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-286">Example</span></span>

```c
/* Send a force renew message from the Client.  */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="ecd63-287">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="ecd63-287">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="ecd63-288">지정된 인터페이스에서 강제 갱신 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-288">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-289">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-289">Prototype</span></span>

```c
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr, 
                                   UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ecd63-290">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-290">Description</span></span>

<span data-ttu-id="ecd63-291">이 서비스를 사용하면 입력 인터페이스가 DHCP에 사용하도록 설정된 경우 호스트 애플리케이션의 해당 인터페이스에서 강제 갱신 메시지를 보낼 수 있습니다(*nx_dhcp_interface_enable* 참조).</span><span class="sxs-lookup"><span data-stu-id="ecd63-291">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ecd63-292">지정된 인터페이스의 DHCP 클라이언트가 BOUND 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-292">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="ecd63-293">이 함수는 T1 시간 제한이 만료되기 전에 DHCP 클라이언트에서 갱신을 시도하도록 상태를 RENEW로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-293">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-294">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-294">Input Parameters</span></span>

- <span data-ttu-id="ecd63-295">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-295">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-296">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-296">Return Values</span></span>

- <span data-ttu-id="ecd63-297">**NX_SUCCESS**: (0x00) 강제 갱신을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="ecd63-297">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>  
- <span data-ttu-id="ecd63-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-299">NX_PTR_ERROR: (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-299">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="ecd63-300">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-300">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-301">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-301">Allowed From</span></span>

<span data-ttu-id="ecd63-302">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-303">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-303">Example</span></span>

```c
/* Send a force renew message to the server on interface 1.  */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);


/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="ecd63-304">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="ecd63-304">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="ecd63-305">DHCP 클라이언트 패킷 풀을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-305">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-306">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-306">Prototype</span></span>

```c
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ecd63-307">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-307">Description</span></span>

<span data-ttu-id="ecd63-308">이 서비스를 사용하면 애플리케이션에서 포인터를 이 서비스 호출의 이전에 만든 패킷 풀에 전달하여 DHCP 클라이언트 패킷 풀을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-308">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="ecd63-309">이 기능을 사용하려면 호스트 애플리케이션에서 NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-309">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="ecd63-310">정의되면 *nx_dhcp_create* 서비스에서 클라이언트의 패킷 풀을 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-310">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> 

>[!NOTE] 
> <span data-ttu-id="ecd63-311">애플리케이션에서 패킷 풀을 만들 때 *nxd_dhcp_client.h* 에서 NX_DHCP_PACKET_PAYLOAD로 정의된 DHCP 클라이언트 패킷 풀 페이로드에 대한 기본값을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-311">The application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nxd_dhcp_client.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-312">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-312">Input Parameters</span></span>

- <span data-ttu-id="ecd63-313">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-313">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ecd63-314">**packet_pool_ptr**: 이전에 만든 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-314">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-315">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-315">Return Values</span></span>

- <span data-ttu-id="ecd63-316">**NX_SUCCESS**: (0x00) DHCP 클라이언트 패킷 풀이 설정됨</span><span class="sxs-lookup"><span data-stu-id="ecd63-316">**NX_SUCCESS**: (0x00) DHCP Client packet pool is set</span></span>
- <span data-ttu-id="ecd63-317">**NX_NOT_ENABLED**: (0x14) 서비스가 사용하도록 설정되지 않음</span><span class="sxs-lookup"><span data-stu-id="ecd63-317">**NX_NOT_ENABLED**: (0x14) Service is not enabled</span></span>
- <span data-ttu-id="ecd63-318">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-318">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ecd63-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) 페이로드가 너무 작음</span><span class="sxs-lookup"><span data-stu-id="ecd63-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-320">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-320">Allowed From</span></span>

<span data-ttu-id="ecd63-321">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="ecd63-321">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-322">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-322">Example</span></span>

```c
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
                                 NX_DHCP_PACKET_PAYLOAD, pointer, 
                                 (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool.  */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set.  */

```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="ecd63-323">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="ecd63-323">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="ecd63-324">DHCP 인스턴스에 대해 요청된 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-324">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-325">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-325">Prototype</span></span>

```c
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr, 
                               ULONG client_ip_address, 
                               UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="ecd63-326">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-326">Description</span></span>

<span data-ttu-id="ecd63-327">이 서비스는 DHCP 클라이언트 레코드의 DHCP에 사용하도록 설정된 첫 번째 인터페이스의 DHCP 서버에서 요청할 DHCP 클라이언트에 대한 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-327">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="ecd63-328">*skip_discover_message* 플래그가 설정되면 DHCP 클라이언트에서 검색 메시지를 건너뛰고 요청 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-328">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="ecd63-329">특정 인터페이스에서 DHCP 메시지의 특정 IP에 대한 요청을 설정하려면 *nx_dhcp_interface_request_client_ip* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-329">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-330">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-330">Input Parameters</span></span>

- <span data-ttu-id="ecd63-331">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-331">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ecd63-332">**client_ip_address**: DHCP 서버에서 요청하는 IP 주소</span><span class="sxs-lookup"><span data-stu-id="ecd63-332">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="ecd63-333">**skip_discover_message**:</span><span class="sxs-lookup"><span data-stu-id="ecd63-333">**skip_discover_message**:</span></span> 
    - <span data-ttu-id="ecd63-334">true이면 DHCP 클라이언트에서 요청 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-334">If true, DHCP Client sends Request message</span></span>
    - <span data-ttu-id="ecd63-335">false이면 검색 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-335">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-336">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-336">Return Values</span></span>

- <span data-ttu-id="ecd63-337">**NX_SUCCESS**: (0x00) 요청된 IP 주소가 설정됨</span><span class="sxs-lookup"><span data-stu-id="ecd63-337">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="ecd63-338">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-338">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ecd63-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) NULL IP 주소가 요청됨</span><span class="sxs-lookup"><span data-stu-id="ecd63-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) NULL IP address requested</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-340">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-340">Allowed From</span></span>

<span data-ttu-id="ecd63-341">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-342">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-342">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message.  */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */

```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="ecd63-343">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="ecd63-343">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="ecd63-344">지정된 인터페이스에서 DHCP 인스턴스에 대해 요청된 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-344">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-345">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-345">Prototype</span></span>

```c
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr, UINT  interface_index, 
                                         ULONG client_ip_address, UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="ecd63-346">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-346">Description</span></span>

<span data-ttu-id="ecd63-347">인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 지정된 인터페이스에서 DHCP 서버로부터 요청할 DHCP 클라이언트에 대한 IP 주소를 설정합니다(*nx_dhcp_interface_enable* 참조).</span><span class="sxs-lookup"><span data-stu-id="ecd63-347">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ecd63-348">*skip_discover_message* 플래그가 설정되면 DHCP 클라이언트에서 검색 메시지를 건너뛰고 요청 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-348">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-349">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-349">Input Parameters</span></span>

- <span data-ttu-id="ecd63-350">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-350">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="ecd63-351">**Interface_index**: IP 주소를 요청하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-351">**Interface_index**: Index of interface to request IP address on</span></span>
- <span data-ttu-id="ecd63-352">**client_ip_address**: DHCP 서버에서 요청하는 IP 주소</span><span class="sxs-lookup"><span data-stu-id="ecd63-352">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="ecd63-353">**skip_discover_message**: true이면 DHCP 클라이언트에서 요청 메시지를 보냅니다. 그렇지 않으면 검색 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-353">**skip_discover_message**: If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-354">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-354">Return Values</span></span>

- <span data-ttu-id="ecd63-355">**NX_SUCCESS**: (0x00) 요청된 IP 주소가 설정됨</span><span class="sxs-lookup"><span data-stu-id="ecd63-355">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="ecd63-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-357">NX_PTR_ERROR: (0x16) 잘못된 IP 또는 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-357">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="ecd63-358">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-358">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-359">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-359">Allowed From</span></span>

<span data-ttu-id="ecd63-360">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-361">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-361">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0.  */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="ecd63-362">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ecd63-362">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="ecd63-363">DHCP 클라이언트 네트워크 매개 변수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-363">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="ecd63-364">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-364">Prototype</span></span>

```c
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ecd63-365">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-365">Description</span></span>

<span data-ttu-id="ecd63-366">이 서비스는 호스트 애플리케이션 네트워크 매개 변수(IP 주소, 네트워크 주소 및 네트워크 마스크)를 지우고, DHCP에 사용하도록 설정된 모든 인터페이스에서 DHCP 클라이언트 상태를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-366">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ecd63-367">DHCP 상태 시스템을 '다시 시작'하기 위해 *nx_dhcp_stop* 및 *nx_dhcp_start* 와 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-367">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span>

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="ecd63-368">여러 인터페이스가 DHCP에 사용하도록 설정된 경우 특정 인터페이스에서 DHCP 클라이언트를 다시 초기화하려면 *nx_dhcp_interface_reinitialize* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-368">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-369">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-369">Input Parameters</span></span>

- <span data-ttu-id="ecd63-370">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-370">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-371">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-371">Return Values</span></span>

- <span data-ttu-id="ecd63-372">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 다시 초기화함</span><span class="sxs-lookup"><span data-stu-id="ecd63-372">**NX_SUCCESS**: (0x00) DHCP successfully reinitialized</span></span> 
- <span data-ttu-id="ecd63-373">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-373">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-374">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-374">Allowed From</span></span>

<span data-ttu-id="ecd63-375">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-376">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-376">Example</span></span>

```c
/* Reinitialize the previously started DHCP client.  */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="ecd63-377">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ecd63-377">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="ecd63-378">지정된 인터페이스에서 DHCP 클라이언트 네트워크 매개 변수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-378">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="ecd63-379">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-379">Prototype</span></span>

```c
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr, 
                                     UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ecd63-380">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-380">Description</span></span>

<span data-ttu-id="ecd63-381">해당 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 지정된 인터페이스에서 네트워크 매개 변수(IP 주소, 네트워크 주소 및 네트워크 마스크)를 지웁니다(*nx_dhcp_interface_enable* 참조).</span><span class="sxs-lookup"><span data-stu-id="ecd63-381">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ecd63-382">자세한 내용은 *nx_dhcp_reinitialize* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-382">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-383">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-383">Input Parameters</span></span>

- <span data-ttu-id="ecd63-384">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-384">**dhcp_ptr**: Pointer to previously created DHCP instance</span></span>
- <span data-ttu-id="ecd63-385">**interface_index** 다시 초기화하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-385">**interface_index**: Index of interface to reinitialize</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-386">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-386">Return Values</span></span>

- <span data-ttu-id="ecd63-387">**NX_SUCCESS**: (0x00) 인터페이스를 성공적으로 다시 초기화함</span><span class="sxs-lookup"><span data-stu-id="ecd63-387">**NX_SUCCESS**: (0x00) Interface successfully reinitialized</span></span>
- <span data-ttu-id="ecd63-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-389">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-389">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ecd63-390">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-390">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ecd63-391">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-391">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-392">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-392">Allowed From</span></span>

<span data-ttu-id="ecd63-393">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-393">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-394">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-394">Example</span></span>

```c
/* Reinitialize the previously started DHCP client on interface 1.  */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="ecd63-395">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="ecd63-395">nx_dhcp_release</span></span>

<span data-ttu-id="ecd63-396">임대 IP 주소를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-396">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-397">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-397">Prototype</span></span>

```c
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ecd63-398">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-398">Description</span></span>

<span data-ttu-id="ecd63-399">이 서비스는 RELEASE 메시지를 DHCP 서버로 보내 해당 서버에서 가져온 IP 주소를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-399">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="ecd63-400">그런 다음, DHCP 클라이언트를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-400">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="ecd63-401">이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-401">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="ecd63-402">애플리케이션에서 *nx_dhcp_start* 호출하여 DHCP 클라이언트를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-402">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="ecd63-403">특정 인터페이스에서 주소를 DHCP 서버로 다시 해제하려면 *nx_dhcp_interface_release* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-403">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-404">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-404">Input Parameters</span></span>

- <span data-ttu-id="ecd63-405">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-405">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-406">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-406">Return Values</span></span>

- <span data-ttu-id="ecd63-407">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 해제함</span><span class="sxs-lookup"><span data-stu-id="ecd63-407">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>  
- <span data-ttu-id="ecd63-408">**NX_DHCP_NOT_BOUND**: (0x94) IP 주소가 임대되지 않았으므로 해제할 수 없음</span><span class="sxs-lookup"><span data-stu-id="ecd63-408">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="ecd63-409">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-409">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ecd63-410">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-410">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-411">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-411">Allowed From</span></span>

<span data-ttu-id="ecd63-412">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-413">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-413">Example</span></span>

```c
/* Release the previously leased IP address.  */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="ecd63-414">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="ecd63-414">nx_dhcp_interface_release</span></span>

<span data-ttu-id="ecd63-415">지정된 인터페이스에서 IP 주소를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-415">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-416">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-416">Prototype</span></span>

```c
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ecd63-417">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-417">Description</span></span>

<span data-ttu-id="ecd63-418">이 서비스는 지정된 인터페이스에서 가져온 DHCP 서버의 IP 주소를 해제하고 DHCP 클라이언트를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-418">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="ecd63-419">DHCP 클라이언트는 *nx_dhcp_start* 를 호출하여 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-419">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-420">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-420">Input Parameters</span></span>

- <span data-ttu-id="ecd63-421">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-421">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-422">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-422">Return Values</span></span>

- <span data-ttu-id="ecd63-423">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 해제함</span><span class="sxs-lookup"><span data-stu-id="ecd63-423">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>
- <span data-ttu-id="ecd63-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-425">**NX_DHCP_NOT_BOUND**: (0x94) IP 주소가 임대되지 않았으므로 해제할 수 없음</span><span class="sxs-lookup"><span data-stu-id="ecd63-425">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="ecd63-426">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-426">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ecd63-427">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-427">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ecd63-428">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-428">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-429">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-429">Allowed From</span></span>

<span data-ttu-id="ecd63-430">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-430">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-431">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-431">Example</span></span>

```c
/* Release the previously leased IP address on interface 1.  */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="ecd63-432">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="ecd63-432">nx_dhcp_decline</span></span>

<span data-ttu-id="ecd63-433">DHCP 서버에서 IP 주소를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-433">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-434">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-434">Prototype</span></span>

```c
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ecd63-435">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-435">Description</span></span>

<span data-ttu-id="ecd63-436">이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스의 DHCP 서버에서 임대된 IP 주소를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-436">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ecd63-437">NX_DHCP_CLIENT_ SEND_ ARP_PROBE가 정의된 경우 IP 주소를 이미 사용하고 있음을 검색하면 DHCP 클라이언트에서 DECLINE 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-437">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="ecd63-438">NetX Duo DHCP 클라이언트에서 ARP 프로브 구성에 대한 자세한 내용은 챕터 1의 **ARP 프로브** 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-438">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX Duo DHCP Client.</span></span>

<span data-ttu-id="ecd63-439">주소를 다른 방법으로 사용하고 있음을 검색하는 경우 애플리케이션에서 이 서비스를 사용하여 IP 주소를 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-439">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="ecd63-440">이 서비스는 *nx_dhcp_start* 를 호출하여 다시 시작할 수 있도록 DHCP 클라이언트를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-440">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-441">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-441">Input Parameters</span></span>

- <span data-ttu-id="ecd63-442">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-442">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-443">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-443">Return Values</span></span>

- <span data-ttu-id="ecd63-444">**NX_SUCCESS**: (0x00) 거부를 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="ecd63-444">**NX_SUCCESS**: (0x00) Decline successfully sent</span></span>  
- <span data-ttu-id="ecd63-445">**NX_DHCP_NOT_BOUND**: (0x94) DHCP 클라이언트가 바인딩되지 않음</span><span class="sxs-lookup"><span data-stu-id="ecd63-445">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="ecd63-446">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-446">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ecd63-447">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-447">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-448">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-448">Allowed From</span></span>

<span data-ttu-id="ecd63-449">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-449">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-450">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-450">Example</span></span>

```c

/* Decline the IP address offered by the DHCP server.  */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="ecd63-451">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="ecd63-451">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="ecd63-452">지정된 인터페이스에서 DHCP 서버의 IP 주소를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-452">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-453">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-453">Prototype</span></span>

```c
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ecd63-454">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-454">Description</span></span>

<span data-ttu-id="ecd63-455">이 서비스는 DHCP 서버에서 할당한 IP 주소를 거부하기 위해 DECLINE 메시지를 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-455">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="ecd63-456">또한 DHCP 클라이언트를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-456">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="ecd63-457">자세한 내용은 *nx_dhcp_decline* 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-457">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-458">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-458">Input Parameters</span></span>

- <span data-ttu-id="ecd63-459">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-459">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ecd63-460">**Interface_index**: IP 주소를 거부하는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-460">**Interface_index**: Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-461">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-461">Return Values</span></span>

- <span data-ttu-id="ecd63-462">**NX_SUCCESS**: (0x00) DHCP 거부 메시지를 보냄</span><span class="sxs-lookup"><span data-stu-id="ecd63-462">**NX_SUCCESS**: (0x00) DHCP decline message sent</span></span>  
- <span data-ttu-id="ecd63-463">**NX_DHCP_NOT_BOUND**: (0x94) DHCP 클라이언트가 바인딩되지 않음</span><span class="sxs-lookup"><span data-stu-id="ecd63-463">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="ecd63-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-465">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-465">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ecd63-466">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-466">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ecd63-467">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-467">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-468">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-468">Allowed From</span></span>

<span data-ttu-id="ecd63-469">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-470">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-470">Example</span></span>

```c
/* Decline the IP address offered by the DHCP server on interface 2.  */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```
## <a name="nx_dhcp_send_request"></a><span data-ttu-id="ecd63-471">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="ecd63-471">nx_dhcp_send_request</span></span>

<span data-ttu-id="ecd63-472">DHCP 메시지를 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-472">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-473">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-473">Prototype</span></span>

```c
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);

```

### <a name="description"></a><span data-ttu-id="ecd63-474">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-474">Description</span></span>

<span data-ttu-id="ecd63-475">이 서비스는 DHCP 클라이언트 레코드에 있는 DHCP에 사용하도록 설정된 첫 번째 인터페이스에서 지정된 DHCP 메시지를 DHCP 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-475">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="ecd63-476">RELEASE 또는 DECLINE 메시지를 보내려면 애플리케이션에서 *nx_dhcp[_interface]_release*() 또는 *nx_dhcp_interface_decline()* 서비스를 각각 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-476">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="ecd63-477">INFORM_REQUEST 메시지 유형을 보내는 경우를 제외하고 이 서비스를 사용하려면 DHCP 클라이언트를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-477">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

>[!NOTE]
> <span data-ttu-id="ecd63-478">이 서비스는 호스트 애플리케이션에서 DHCP 클라이언트 상태 시스템을 '구동'하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-478">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-479">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-479">Input Parameters</span></span>

- <span data-ttu-id="ecd63-480">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-480">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ecd63-481">**dhcp_message_type**: 메시지 요청(*nxd_dhcp_client.h* 에서 정의됨)</span><span class="sxs-lookup"><span data-stu-id="ecd63-481">**dhcp_message_type**: Message request (defined in *nxd_dhcp_client.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-482">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-482">Return Values</span></span>

- <span data-ttu-id="ecd63-483">**NX_SUCCESS**: (0x00) DHCP 메시지를 보냄</span><span class="sxs-lookup"><span data-stu-id="ecd63-483">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="ecd63-484">**NX_DHCP_NOT_STARTED**: (0x96) 잘못된 인터페이스 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-484">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="ecd63-485">**NX_DHCP_INVALID_MESSAGE**: (0x9B) 잘못된 보내는 메시지 유형</span><span class="sxs-lookup"><span data-stu-id="ecd63-485">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="ecd63-486">NX_PTR_ERROR: (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="ecd63-486">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-487">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-487">Allowed From</span></span>

<span data-ttu-id="ecd63-488">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-488">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-489">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-489">Example</span></span>

```c
/* Send the DHCP INFORM REQUEST message to the server.  */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="ecd63-490">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="ecd63-490">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="ecd63-491">특정 인터페이스에서 DHCP 메시지를 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-491">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-492">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-492">Prototype</span></span>

```c
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr, 
                                    UINT interface_index, 
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="ecd63-493">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-493">Description</span></span>

<span data-ttu-id="ecd63-494">지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 메시지를 DHCP 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-494">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ecd63-495">RELEASE 또는 DECLINE 메시지를 보내려면 애플리케이션에서 *nx_dhcp[_interface]_release*() 또는 *nx_dhcp_interface_decline()* 서비스를 각각 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-495">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="ecd63-496">DHCP INFORM REQUEST 메시지 유형을 보내는 경우를 제외하고 이 서비스를 사용하려면 DHCP 클라이언트를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-496">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="ecd63-497">이 서비스는 호스트 애플리케이션에서 DHCP 클라이언트 상태 시스템을 '구동'하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-497">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-498">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-498">Input Parameters</span></span>

- <span data-ttu-id="ecd63-499">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-499">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="ecd63-500">**Interface_index**: 메시지를 보내는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-500">**Interface_index**: Index of interface to send message on</span></span>
- <span data-ttu-id="ecd63-501">**dhcp_message_type**: 메시지 요청(nxd_dhcp_client.h에서 정의됨)</span><span class="sxs-lookup"><span data-stu-id="ecd63-501">**dhcp_message_type**: Message request (defined in nxd_dhcp_client.h)</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-502">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-502">Return Values</span></span>

- <span data-ttu-id="ecd63-503">**NX_SUCCESS**: (0x00) DHCP 메시지를 보냄</span><span class="sxs-lookup"><span data-stu-id="ecd63-503">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="ecd63-504">**NX_DHCP_NOT_STARTED**: (0x96) 잘못된 인터페이스 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-504">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="ecd63-505">**NX_DHCP_INVALID_MESSAGE**: (0x9B) 잘못된 보내는 메시지 유형</span><span class="sxs-lookup"><span data-stu-id="ecd63-505">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="ecd63-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-507">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-507">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ecd63-508">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-508">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ecd63-509">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-509">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-510">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-510">Allowed From</span></span>

<span data-ttu-id="ecd63-511">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-511">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-512">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-512">Example</span></span>

```c
/* Send the INFORM REQUEST message to the server on the primary interface.  */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="ecd63-513">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="ecd63-513">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="ecd63-514">DHCP 클라이언트의 DHCP 서버 IP 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-514">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-515">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-515">Prototype</span></span>

```c
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr, 
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ecd63-516">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-516">Description</span></span>

<span data-ttu-id="ecd63-517">이 서비스는 DHCP 클라이언트 레코드에 있는 DHCP에 사용하도록 설정된 첫 번째 인터페이스에서 DHCP 클라이언트 DHCP 서버 IP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-517">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="ecd63-518">호출자는 DHCP 클라이언트가 DHCP 서버에서 할당한 IP 주소에 바인딩된 후에만 이 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-518">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="ecd63-519">호스트 애플리케이션에서 *nx_ip_status_check* 서비스를 사용하여 IP 주소가 설정되어 있는지 확인하거나 nx *_dhcp_state_change_notify* 를 사용하여 DHCP 클라이언트 상태가 NX_DHCP_STATE_BOUND인지 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-519">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the nx *_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="ecd63-520">상태 변경 콜백 함수를 설정하는 방법에 대한 자세한 내용은 *nx_dhcp_state_change_notify* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-520">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="ecd63-521">여러 인터페이스가 DHCP 클라이언트에 사용하도록 설정된 경우 특정 인터페이스에서 DHCP 서버를 찾으려면 *nx_dhcp_interface_server_address_get* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-521">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-522">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-522">Input Parameters</span></span>

- <span data-ttu-id="ecd63-523">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-523">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="ecd63-524">**server_address**: 서버 IP 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-524">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-525">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-525">Return Values</span></span>

- <span data-ttu-id="ecd63-526">**NX_SUCCESS**: (0x00) DHCP 서버 주소가 반환됨</span><span class="sxs-lookup"><span data-stu-id="ecd63-526">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="ecd63-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP에 사용하도록 설정된 인터페이스가 없음</span><span class="sxs-lookup"><span data-stu-id="ecd63-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-528">NX_PTR_ERROR: (0x16) 잘못된 입력 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-528">NX_PTR_ERROR: (0x16) Invalid input pointer</span></span>
- <span data-ttu-id="ecd63-529">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-529">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-530">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-530">Allowed From</span></span>

<span data-ttu-id="ecd63-531">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-532">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-532">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the bound state and get its DHCP server IP address.*/

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{
ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
        }

}
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="ecd63-533">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="ecd63-533">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="ecd63-534">지정된 인터페이스에서 DHCP 클라이언트의 DHCP 서버 IP 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-534">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-535">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-535">Prototype</span></span>

```c
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr, 
                                          UINT interface_index,
                                          ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ecd63-536">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-536">Description</span></span>

<span data-ttu-id="ecd63-537">지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 DHCP 클라이언트 DHCP 서버 IP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-537">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ecd63-538">DHCP 클라이언트는 바인딩됨 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-538">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="ecd63-539">해당 인터페이스에서 DHCP 클라이언트를 시작하면 호스트 애플리케이션에서 *nx_ip_status_check* 서비스를 사용하여 IP 주소가 설정되어 있는지 확인하거나 DHCP 클라이언트 상태 변경 콜백을 사용하여 DHCP 클라이언트 상태가 NX_DHCP_STATE_BOUND인지 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-539">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="ecd63-540">상태 변경 콜백 함수를 설정하는 방법에 대한 자세한 내용은 *nx_dhcp_state_change_notify* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-540">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-541">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-541">Input Parameters</span></span>

- <span data-ttu-id="ecd63-542">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-542">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="ecd63-543">**Interface_index**: IP 주소를 가져오는 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-543">**Interface_index**: Index of interface to obtain IP address</span></span>
- <span data-ttu-id="ecd63-544">**server_address**: 서버 IP 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-544">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-545">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-545">Return Values</span></span>

- <span data-ttu-id="ecd63-546">**NX_SUCCESS**: (0x00) DHCP 서버 주소가 반환됨</span><span class="sxs-lookup"><span data-stu-id="ecd63-546">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="ecd63-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP에 사용하도록 설정된 인터페이스가 없음</span><span class="sxs-lookup"><span data-stu-id="ecd63-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-548">**NX_DHCP_NOT_BOUND**: (0x94) DHCP 클라이언트가 바인딩되지 않음</span><span class="sxs-lookup"><span data-stu-id="ecd63-548">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="ecd63-549">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-549">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="ecd63-550">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-550">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ecd63-551">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-551">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-552">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-552">Allowed From</span></span>

<span data-ttu-id="ecd63-553">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-553">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-554">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-554">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. */

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

/* Get the DHCP server IP address on interface 1 */
if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
         status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                       &server_address);
        }
}
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="ecd63-555">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="ecd63-555">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="ecd63-556">DHCP 인스턴스에 대한 네트워크 인터페이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-556">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-557">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-557">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="ecd63-558">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-558">Description</span></span>

<span data-ttu-id="ecd63-559">이 서비스는 단일 네트워크 인터페이스에 대해 구성된 DHCP 클라이언트를 실행할 때 DHCP 인스턴스에서 DHCP 서버에 연결하는 네트워크 인터페이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-559">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="ecd63-560">기본적으로 DHCP 클라이언트가 기본 인터페이스에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-560">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="ecd63-561">보조 서비스에서 DHCP를 실행하려면 이 서비스를 사용하여 보조 인터페이스를 DHCP 클라이언트 인터페이스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-561">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="ecd63-562">애플리케이션에서 이전에 *nx_ip_interface_attach* 서비스를 사용하여 지정된 인터페이스를 IP 인스턴스에 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-562">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

>[!NOTE]
> <span data-ttu-id="ecd63-563">이 서비스는 하나의 인터페이스에서만 DHCP 클라이언트를 실행하려는 애플리케이션을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-563">This service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="ecd63-564">여러 인터페이스에서 DHCP를 실행하는 방법에 대한 자세한 내용은 *nx_dhcp_interface_enable* 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-564">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-565">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-565">Input Parameters</span></span>

- <span data-ttu-id="ecd63-566">**dhcp_ptr**: DHCP 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-566">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ecd63-567">**index**: 디바이스 네트워크 인터페이스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-567">**index**: Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-568">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-568">Return Values</span></span>

- <span data-ttu-id="ecd63-569">**NX_SUCCESS**: (0x00) 인터페이스를 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="ecd63-569">**NX_SUCCESS**: (0x00) Interface is successfully set.</span></span>
- <span data-ttu-id="ecd63-570">**NX_INVALID_INTERFACE**: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-570">**NX_INVALID_INTERFACE**: (0x4C) Invalid network interface</span></span>
- <span data-ttu-id="ecd63-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) DHCP에 사용하도록 설정된 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) 다른 레코드에 사용할 수 있는 레코드가 없음</span><span class="sxs-lookup"><span data-stu-id="ecd63-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another</span></span> 
- <span data-ttu-id="ecd63-573">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-573">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-574">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-574">Allowed From</span></span>

<span data-ttu-id="ecd63-575">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-575">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-576">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-576">Example</span></span>

```c
/* Set the DHCP Client interface to the secondary interface (index 1).  */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set.  */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="ecd63-577">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="ecd63-577">nx_dhcp_start</span></span>

<span data-ttu-id="ecd63-578">DHCP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-578">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-579">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-579">Prototype</span></span>

```c
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ecd63-580">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-580">Description</span></span>

<span data-ttu-id="ecd63-581">이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스에서 DHCP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-581">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ecd63-582">기본적으로 애플리케이션에서 *nx_dhcp_create* 를 호출할 때 기본 인터페이스가 DHCP에 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-582">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="ecd63-583">IP 인스턴스가 DHCP 클라이언트 인터페이스의 IP 주소에 바인딩되어 있는지 확인하려면 *nx_ip_status_check* 를 사용하여 IP 주소가 유효한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-583">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="ecd63-584">이미 DHCP를 실행하는 다른 인터페이스가 있는 경우 이 서비스는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-584">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="ecd63-585">여러 인터페이스가 사용하도록 설정된 경우 특정 인터페이스에서 DHCP를 시작하려면 *nx_dhcp_interface_start* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-585">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-586">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-586">Input Parameters</span></span>

- <span data-ttu-id="ecd63-587">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-587">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-588">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-588">Return Values</span></span>

- <span data-ttu-id="ecd63-589">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 시작함</span><span class="sxs-lookup"><span data-stu-id="ecd63-589">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span>  
- <span data-ttu-id="ecd63-590">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP가 이미 시작됨</span><span class="sxs-lookup"><span data-stu-id="ecd63-590">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="ecd63-591">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-591">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ecd63-592">NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-592">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-593">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-593">Allowed From</span></span>

<span data-ttu-id="ecd63-594">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-595">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-595">Example</span></span>

```c
/* Start the DHCP processing for this IP instance.  */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="ecd63-596">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="ecd63-596">nx_dhcp_interface_start</span></span>

<span data-ttu-id="ecd63-597">지정된 인터페이스에서 DHCP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-597">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-598">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-598">Prototype</span></span>

```c
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ecd63-599">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-599">Description</span></span>

<span data-ttu-id="ecd63-600">지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 DHCP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-600">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ecd63-601">인터페이스를 DHCP에 사용하도록 설정하는 방법에 대한 자세한 내용은 *nx_dhcp_interface_enable*()을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-601">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="ecd63-602">기본적으로 애플리케이션에서 *nx_dhcp_create* 를 호출할 때 기본 인터페이스가 DHCP에 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-602">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="ecd63-603">DHCP 클라이언트를 실행하는 다른 인터페이스가 없는 경우 이 서비스는 DHCP 클라이언트 스레드를 시작/다시 시작하고 DHCP 클라이언트 타이머를 (다시) 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-603">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="ecd63-604">애플리케이션에서 *nx_ip_status_check* 를 사용하여 IP 주소를 가져왔는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-604">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-605">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-605">Input Parameters</span></span>

- <span data-ttu-id="ecd63-606">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-606">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ecd63-607">**Interface_index**: DHCP 클라이언트를 시작하는 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-607">**Interface_index**: Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-608">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-608">Return Values</span></span>

- <span data-ttu-id="ecd63-609">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 시작함</span><span class="sxs-lookup"><span data-stu-id="ecd63-609">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span> 
- <span data-ttu-id="ecd63-610">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP가 이미 시작됨</span><span class="sxs-lookup"><span data-stu-id="ecd63-610">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="ecd63-611">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-611">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ecd63-612">NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-612">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ecd63-613">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-613">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-614">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-614">Allowed From</span></span>

<span data-ttu-id="ecd63-615">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-615">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-616">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-616">Example</span></span>

```c
/* Start the DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="ecd63-617">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="ecd63-617">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="ecd63-618">DHCP 상태 변경 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-618">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-619">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-619">Prototype</span></span>

```c
UINT nx_dhcp_state_change_notify(NX_DHCP *dhcp_ptr, 
                                 VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="ecd63-620">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-620">Description</span></span>

<span data-ttu-id="ecd63-621">이 서비스는 DHCP 상태 변경을 애플리케이션에 알리기 위해 지정된 dhcp_state_change_notify 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-621">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="ecd63-622">콜백 함수는 DHCP 클라이언트가 전환된 상태를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-622">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="ecd63-623">다양한 DHCP 상태와 관련된 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-623">Following are values associated with the various DHCP states:</span></span>

- <span data-ttu-id="ecd63-624">NX_DHCP_STATE_BOOT: 1</span><span class="sxs-lookup"><span data-stu-id="ecd63-624">NX_DHCP_STATE_BOOT: 1</span></span>
- <span data-ttu-id="ecd63-625">NX_DHCP_STATE_INIT: 2</span><span class="sxs-lookup"><span data-stu-id="ecd63-625">NX_DHCP_STATE_INIT: 2</span></span>
- <span data-ttu-id="ecd63-626">NX_DHCP_STATE_SELECTING: 3</span><span class="sxs-lookup"><span data-stu-id="ecd63-626">NX_DHCP_STATE_SELECTING: 3</span></span>
- <span data-ttu-id="ecd63-627">NX_DHCP_STATE_REQUESTING: 4</span><span class="sxs-lookup"><span data-stu-id="ecd63-627">NX_DHCP_STATE_REQUESTING: 4</span></span>
- <span data-ttu-id="ecd63-628">NX_DHCP_STATE_BOUND: 5</span><span class="sxs-lookup"><span data-stu-id="ecd63-628">NX_DHCP_STATE_BOUND: 5</span></span>
- <span data-ttu-id="ecd63-629">NX_DHCP_STATE_RENEWING: 6</span><span class="sxs-lookup"><span data-stu-id="ecd63-629">NX_DHCP_STATE_RENEWING: 6</span></span>
- <span data-ttu-id="ecd63-630">NX_DHCP_STATE_REBINDING: 7</span><span class="sxs-lookup"><span data-stu-id="ecd63-630">NX_DHCP_STATE_REBINDING: 7</span></span>
- <span data-ttu-id="ecd63-631">NX_DHCP_STATE_FORCERENEW: 8</span><span class="sxs-lookup"><span data-stu-id="ecd63-631">NX_DHCP_STATE_FORCERENEW: 8</span></span>
- <span data-ttu-id="ecd63-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span><span class="sxs-lookup"><span data-stu-id="ecd63-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-633">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-633">Input Parameters</span></span>

- <span data-ttu-id="ecd63-634">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-634">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ecd63-635">**dhcp_state_change_notify**: 상태 변경 콜백 함수 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-635">**dhcp_state_change_notify**: State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-636">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-636">Return Values</span></span>

- <span data-ttu-id="ecd63-637">**NX_SUCCESS**: (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="ecd63-637">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="ecd63-638">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-638">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ecd63-639">NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-639">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-640">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-640">Allowed From</span></span>

<span data-ttu-id="ecd63-641">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="ecd63-641">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-642">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-642">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change, assuming DHCP has alreadybeen created.  */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="ecd63-643">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="ecd63-643">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="ecd63-644">지정된 인터페이스에서 DHCP 상태 변경 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-644">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-645">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-645">Prototype</span></span>

```c
UINT nx_dhcp_interface_state_change_notify(NX_DHCP *dhcp_ptr, UINT interface_index,
                                           VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                                                            UINT interface_index,
                                                                            UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="ecd63-646">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-646">Description</span></span>

<span data-ttu-id="ecd63-647">이 서비스는 DHCP 상태 변경을 애플리케이션에 알리기 위해 지정된 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-647">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="ecd63-648">콜백 함수 입력 인수는 인터페이스 인덱스 및 DHCP 클라이언트가 해당 인터페이스에서 전환된 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-648">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="ecd63-649">상태 변경 함수에 대한 자세한 내용은 *nx_dhcp_state_change_notify*()를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-649">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-650">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-650">Input Parameters</span></span>

- <span data-ttu-id="ecd63-651">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-651">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ecd63-652">**dhcp_interface_state_change_notify**: 애플리케이션 콜백 함수 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-652">**dhcp_interface_state_change_notify**: Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-653">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-653">Return Values</span></span>

- <span data-ttu-id="ecd63-654">**NX_SUCCESS**: (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="ecd63-654">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="ecd63-655">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-655">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-656">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-656">Allowed From</span></span>

<span data-ttu-id="ecd63-657">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="ecd63-657">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-658">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-658">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change,   
   assuming DHCP has alreadybeen created.  */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                  UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="ecd63-659">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="ecd63-659">nx_dhcp_stop</span></span>

<span data-ttu-id="ecd63-660">DHCP 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-660">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-661">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-661">Prototype</span></span>

```c
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ecd63-662">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-662">Description</span></span>

<span data-ttu-id="ecd63-663">이 서비스는 DHCP 처리를 시작한 모든 인터페이스에서 DHCP 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-663">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="ecd63-664">DHCP를 처리하는 인터페이스가 없는 경우 이 서비스는 DHCP 클라이언트 스레드를 일시 중단하고 DHCP 클라이언트 타이머를 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-664">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="ecd63-665">여러 인터페이스가 DHCP에 사용하도록 설정된 경우 특정 인터페이스에서 DHCP를 중지하려면 *nx_dhcp_interface_stop* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-665">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-666">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-666">Input Parameters</span></span>

- <span data-ttu-id="ecd63-667">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-667">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-668">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-668">Return Values</span></span>

- <span data-ttu-id="ecd63-669">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 중지함</span><span class="sxs-lookup"><span data-stu-id="ecd63-669">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="ecd63-670">**NX_DHCP_NOT_STARTED**: (0x96) DHCP 인스턴스가 시작되지 않음</span><span class="sxs-lookup"><span data-stu-id="ecd63-670">**NX_DHCP_NOT_STARTED**: (0x96) The DHCP instance not started.</span></span>
- <span data-ttu-id="ecd63-671">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-671">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ecd63-672">NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-672">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-673">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-673">Allowed From</span></span>

<span data-ttu-id="ecd63-674">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-675">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-675">Example</span></span>

```c
/* Stop the DHCP processing for this IP instance.  */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="ecd63-676">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="ecd63-676">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="ecd63-677">지정된 인터페이스에서 DHCP 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-677">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-678">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-678">Prototype</span></span>

```c
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ecd63-679">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-679">Description</span></span>

<span data-ttu-id="ecd63-680">DHCP가 이미 시작된 경우 이 서비스는 지정된 인터페이스에서 DHCP 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-680">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="ecd63-681">DHCP를 실행하는 다른 인터페이스가 없는 경우 DHCP 스레드 및 타이머가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-681">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-682">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-682">Input Parameters</span></span>

- <span data-ttu-id="ecd63-683">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-683">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ecd63-684">**Interface_index**: DHCP 처리를 중지하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-684">**Interface_index**: Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-685">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-685">Return Values</span></span>

- <span data-ttu-id="ecd63-686">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 중지함</span><span class="sxs-lookup"><span data-stu-id="ecd63-686">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="ecd63-687">**NX_DHCP_NOT_STARTED**: (0x96) DHCP가 시작되지 않음</span><span class="sxs-lookup"><span data-stu-id="ecd63-687">**NX_DHCP_NOT_STARTED**: (0x96) DHCP not started.</span></span>
- <span data-ttu-id="ecd63-688">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-688">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ecd63-689">NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-689">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ecd63-690">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-690">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-691">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-691">Allowed From</span></span>

<span data-ttu-id="ecd63-692">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-693">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-693">Example</span></span>

```c
/* Stop DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="ecd63-694">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="ecd63-694">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="ecd63-695">마지막 서버 응답에서 DHCP 옵션을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-695">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-696">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-696">Prototype</span></span>

```c
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, UINT request_option, 
                                  UCHAR *destination_ptr, UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="ecd63-697">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-697">Description</span></span>

<span data-ttu-id="ecd63-698">이 서비스는 DHCP 클라이언트 레코드에 있는 DHCP에 사용하도록 설정된 첫 번째 인터페이스에서 DHCP 옵션 버퍼로부터 지정된 DHCP 옵션을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-698">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="ecd63-699">성공하면 옵션 데이터가 지정된 버퍼에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-699">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-700">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-700">Input Parameters</span></span>

- <span data-ttu-id="ecd63-701">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-701">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>  
- <span data-ttu-id="ecd63-702">**request_option**: RFC에서 지정한 DHCP 옵션.</span><span class="sxs-lookup"><span data-stu-id="ecd63-702">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="ecd63-703">*nxd_dhcp_client.h* 의 NX_DHCP_OPTION 옵션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-703">See the NX_DHCP_OPTION option in *nxd_dhcp_client.h*.</span></span>
- <span data-ttu-id="ecd63-704">**destination_ptr**: 응답 문자열의 대상에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-704">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="ecd63-705">**destination_size**: 대상 및 반환 시 반환되는 바이트 수를 저장할 대상의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-705">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-706">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-706">Return Values</span></span>

- <span data-ttu-id="ecd63-707">**NX_SUCCESS**: (0x00) 옵션을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="ecd63-707">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="ecd63-708">**NX_DHCP_NOT_BOUND**: (0x94) DHCP 클라이언트가 바인딩되지 않음</span><span class="sxs-lookup"><span data-stu-id="ecd63-708">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound.</span></span>
- <span data-ttu-id="ecd63-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP에 사용하도록 설정된 인터페이스가 없음</span><span class="sxs-lookup"><span data-stu-id="ecd63-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="ecd63-710">**NX_DHCP_DEST_TO_SMALL**: (0x95) 대상이 너무 작아서 응답을 보유할 수 없음</span><span class="sxs-lookup"><span data-stu-id="ecd63-710">**NX_DHCP_DEST_TO_SMALL**: (0x95) Destination is too small to hold response.</span></span>
- <span data-ttu-id="ecd63-711">**NX_DHCP_PARSE_ERROR**: (0x97) 서버 응답에 옵션이 없음</span><span class="sxs-lookup"><span data-stu-id="ecd63-711">**NX_DHCP_PARSE_ERROR**: (0x97) Option not found in Server response.</span></span>
- <span data-ttu-id="ecd63-712">NX_PTR_ERROR: (0x16) 잘못된 입력 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-712">NX_PTR_ERROR: (0x16) Invalid input pointer.</span></span>
- <span data-ttu-id="ecd63-713">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-713">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-714">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-714">Allowed From</span></span>

<span data-ttu-id="ecd63-715">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-715">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-716">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-716">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
                                        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="ecd63-717">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="ecd63-717">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="ecd63-718">지정한 인터페이스에서 마지막 서버 응답으로부터 DHCP 옵션을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-718">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-719">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-719">Prototype</span></span>

```c
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT request_option, UCHAR *destination_ptr,
                                            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="ecd63-720">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-720">Description</span></span>

<span data-ttu-id="ecd63-721">지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 DHCP 옵션 버퍼로부터 지정된 DHCP 옵션을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-721">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ecd63-722">성공하면 옵션 데이터가 지정된 버퍼에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-722">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-723">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-723">Input Parameters</span></span>

- <span data-ttu-id="ecd63-724">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-724">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ecd63-725">**Interface_index**: 지정된 옵션을 검색하는 인덱스</span><span class="sxs-lookup"><span data-stu-id="ecd63-725">**Interface_index**: Index on which to retrieve the specified option</span></span>
- <span data-ttu-id="ecd63-726">**request_option**: RFC에서 지정한 DHCP 옵션.</span><span class="sxs-lookup"><span data-stu-id="ecd63-726">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="ecd63-727">*nxd_dhcp_client.h* 의 NX_DHCP_OPTION 옵션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecd63-727">See the NX_DHCP_OPTION option: in *nxd_dhcp_client.h*.</span></span>  
- <span data-ttu-id="ecd63-728">**destination_ptr**: 응답 문자열의 대상에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-728">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="ecd63-729">**destination_size**: 대상 및 반환 시 반환되는 바이트 수를 저장할 대상의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-729">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-730">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-730">Return Values</span></span>

- <span data-ttu-id="ecd63-731">**NX_SUCCESS**: (0x00) 옵션을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="ecd63-731">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="ecd63-732">**NX_DHCP_NOT_BOUND**: (0x94) IP 주소가 할당되지 않음</span><span class="sxs-lookup"><span data-stu-id="ecd63-732">**NX_DHCP_NOT_BOUND**: (0x94) IP address not assigned</span></span>
- <span data-ttu-id="ecd63-733">**NX_DHCP_DEST_TO_SMALL**: (0x95) 버퍼가 너무 작음</span><span class="sxs-lookup"><span data-stu-id="ecd63-733">**NX_DHCP_DEST_TO_SMALL**: (0x95) Buffer is too small</span></span>
- <span data-ttu-id="ecd63-734">**NX_DHCP_PARSE_ERROR**: (0x97) 서버 응답에 DHCP 옵션이 없음</span><span class="sxs-lookup"><span data-stu-id="ecd63-734">**NX_DHCP_PARSE_ERROR**: (0x97) DHCP Option not found in Server response.</span></span>
- <span data-ttu-id="ecd63-735">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-735">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="ecd63-736">NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="ecd63-736">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="ecd63-737">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ecd63-737">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-738">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-738">Allowed From</span></span>

<span data-ttu-id="ecd63-739">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-740">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-740">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
                                                  dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="ecd63-741">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="ecd63-741">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="ecd63-742">4바이트를 ULONG으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-742">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-743">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-743">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="ecd63-744">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-744">Description</span></span>

<span data-ttu-id="ecd63-745">이 서비스는 "option_string_ptr"에서 가리키는 4개 문자를 서명되지 않은 long 값으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-745">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="ecd63-746">특히 IP 주소가 있는 경우</span><span class="sxs-lookup"><span data-stu-id="ecd63-746">It is especially useful when IP addresses are</span></span>  
<span data-ttu-id="ecd63-747">유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-747">present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-748">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-748">Input Parameters</span></span>

- <span data-ttu-id="ecd63-749">**option_string_ptr**: 이전에 검색한 옵션 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-749">**option_string_ptr**: Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-750">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-750">Return Values</span></span>

- <span data-ttu-id="ecd63-751">**Value**: 처음 4바이트의 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-751">**Value**: Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-752">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-752">Allowed From</span></span>

<span data-ttu-id="ecd63-753">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-753">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-754">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-754">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="ecd63-755">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="ecd63-755">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="ecd63-756">사용자 제공 옵션을 추가하기 위한 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-756">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="ecd63-757">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ecd63-757">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
                                           UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                                                        UINT iface_index, 
                                                                        UINT message_type, 
                                                                        UCHAR *user_option_ptr, 
                                                                        UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="ecd63-758">Description</span><span class="sxs-lookup"><span data-stu-id="ecd63-758">Description</span></span>

<span data-ttu-id="ecd63-759">이 서비스는 사용자 제공 옵션을 추가하기 위해 지정된 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-759">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="ecd63-760">콜백 함수가 지정된 경우 애플리케이션에서 사용자가 제공한 옵션을 iface_index 및 message_type별로 패킷에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-760">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

>[!NOTE] 
> <span data-ttu-id="ecd63-761">사용자의 루틴에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-761">In user’s routine.</span></span> <span data-ttu-id="ecd63-762">사용자가 제공한 옵션을 추가하는 경우 애플리케이션에서 DHCP 옵션 형식을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-762">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="ecd63-763">사용자 옵션의 총 크기는 user_option_length보다 작거나 같아야 하며, user_option_length를 실제 옵션 길이로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-763">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="ecd63-764">옵션이 성공적으로 추가되면 NX_TRUE를 반환하고, 그렇지 않으면 NX_FALSE를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ecd63-764">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ecd63-765">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ecd63-765">Input Parameters</span></span>

- <span data-ttu-id="ecd63-766">**ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-766">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="ecd63-767">**dhcp_user_option_add**: 사용자 옵션 추가 함수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-767">**dhcp_user_option_add**: Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="ecd63-768">반환 값</span><span class="sxs-lookup"><span data-stu-id="ecd63-768">Return Values</span></span>

- <span data-ttu-id="ecd63-769">**NX_SUCCESS**: (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="ecd63-769">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>
- <span data-ttu-id="ecd63-770">NX_PTR_ERROR: (0x16) 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="ecd63-770">NX_PTR_ERROR: (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ecd63-771">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="ecd63-771">Allowed From</span></span>

<span data-ttu-id="ecd63-772">스레드</span><span class="sxs-lookup"><span data-stu-id="ecd63-772">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ecd63-773">예제</span><span class="sxs-lookup"><span data-stu-id="ecd63-773">Example</span></span>

```c
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created.  */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered.  */

```

