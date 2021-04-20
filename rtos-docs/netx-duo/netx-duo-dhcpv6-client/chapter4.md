---
title: 4장 - Azure RTOS NetX Duo DHCPv6 클라이언트 서비스
description: 이 장에서는 아래에 나열된 모든 Azure RTOS NetX Duo DHCPv6 클라이언트 서비스에 대해 사전순으로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40fbfa7319ca95af65c92b12582d4bbb05005dc0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810890"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a><span data-ttu-id="4b992-103">4장 - Azure RTOS NetX Duo DHCPv6 클라이언트 서비스</span><span class="sxs-lookup"><span data-stu-id="4b992-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 Client services</span></span>

<span data-ttu-id="4b992-104">이 장에서는 아래에 나열된 모든 Azure RTOS NetX Duo DHCPv6 클라이언트 서비스에 대해 사전순으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-104">This chapter contains a description of all Azure RTOS NetX Duo DHCPv6 Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="4b992-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="4b992-106">**nx_dhcpv6_client_create:** *DHCPv6 클라이언트 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="4b992-106">**nx_dhcpv6_client_create:** *Create a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="4b992-107">**nx_dhcpv6_client_delete:** *DHCPv6 클라이언트 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="4b992-107">**nx_dhcpv6_client_delete:** *Delete a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="4b992-108">**nx_dhcpv6_create_ client_duid:** *DHCPv6 클라이언트 DUID 만들기*</span><span class="sxs-lookup"><span data-stu-id="4b992-108">**nx_dhcpv6_create_ client_duid:** *Create a DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="4b992-109">**nx_dhcpv6 _add_client_ia:** *DHCPv6 클라이언트 IA(ID 주소) 추가*</span><span class="sxs-lookup"><span data-stu-id="4b992-109">**nx_dhcpv6 _add_client_ia:** *Add a DHCPv6 Client Identity Address (IA)*</span></span> 

- <span data-ttu-id="4b992-110">**nx_dhcpv6 _create_client_ia:** (*DHCPv6 클라이언트 IA(ID 주소) 추가의 레거시)*</span><span class="sxs-lookup"><span data-stu-id="4b992-110">**nx_dhcpv6 _create_client_ia:** (*Legacy Add a DHCPv6 Client Identity Address (IA))*</span></span> 

- <span data-ttu-id="4b992-111">**nx_dhcpv6_create_client_iana:** *IANA(비 임시 주소용 ID 연결)에 대해 DHCPv6 클라이언트 ID 연결 만들기*</span><span class="sxs-lookup"><span data-stu-id="4b992-111">**nx_dhcpv6_create_client_iana:** *Create a DHCPv6 Client Identity Association for Non Temporary Addresses (IANA)*</span></span> 

- <span data-ttu-id="4b992-112">**nx_dhcpv6_get_client_duid_time_id:** *DHCPv6 클라이언트 DUID에서 시간 ID 가져오기*</span><span class="sxs-lookup"><span data-stu-id="4b992-112">**nx_dhcpv6_get_client_duid_time_id:** *Get the time ID from DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="4b992-113">**nx_dhcpv6_client_set_interface:** *DHCPv6 서버와 통신하기 위해 클라이언트 네트워크 인터페이스 설정*</span><span class="sxs-lookup"><span data-stu-id="4b992-113">**nx_dhcpv6_client_set_interface:** *Set the Client network interface for communications with the DHCPv6 Server*</span></span> 

- <span data-ttu-id="4b992-114">**nx_dhcpv6_get_IP_address:** *DHCPv6 클라이언트에 할당된 전역 IPv6 주소 가져오기*</span><span class="sxs-lookup"><span data-stu-id="4b992-114">**nx_dhcpv6_get_IP_address:** *Get the global IPv6 address assigned to the DHCPv6 client*</span></span> 

- <span data-ttu-id="4b992-115">**nx_dhcpv6_get_lease_time_data:** *클라이언트 전역 IPv6 주소에 대한 T1, T2, 유효한 수명, 기본 설정 수명 가져오기*</span><span class="sxs-lookup"><span data-stu-id="4b992-115">**nx_dhcpv6_get_lease_time_data:** *Get T1, T2, valid and preferred lifetimes for the Client global IPv6 address*</span></span>

- <span data-ttu-id="4b992-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *주소 인덱스별로 DHCPv6 클라이언트 IPv6 주소에 대한 T1, T2, 유효한 수명, 기본 설정 수명 가져오기*</span><span class="sxs-lookup"><span data-stu-id="4b992-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *Get T1, T2, valid and preferred lifetimes for the DHCPv6 Client IPv6 address by address index*</span></span> 

- <span data-ttu-id="4b992-117">**nx_dhcpv6_get_iana_lease_time:** *DHCPv6 클라이언트에 임대된 ID 연결(IANA)의 T1 및 T2 가져오기*</span><span class="sxs-lookup"><span data-stu-id="4b992-117">**nx_dhcpv6_get_iana_lease_time:** *Get T1 and T2 in the Identity Association (IANA) leased to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="4b992-118">**nx_dhcpv6_get_other_option_data:** *도메인 이름 또는 표준 시간대 서버와 같은 지정된 옵션 데이터 가져오기*</span><span class="sxs-lookup"><span data-stu-id="4b992-118">**nx_dhcpv6_get_other_option_data:** *Get the specified option data e.g. domain name or time zone server*</span></span> 

- <span data-ttu-id="4b992-119">**nx_dhcpv6_get_DNS_server_address:** *지정된 인덱스의 DNS 서버 주소를 DHCPv6 클라이언트 DNS 서버 목록으로 가져오기*</span><span class="sxs-lookup"><span data-stu-id="4b992-119">**nx_dhcpv6_get_DNS_server_address:** *Get DNS Server address at the specified index into the DHCPv6 Client DNS server list*</span></span> 

- <span data-ttu-id="4b992-120">**nx_dhcpv6_get_time_accrued:** *전역 IPv6 주소 임대가 DHCPv6 클라이언트에 바인딩되어 있는 누적 시간 가져오기*</span><span class="sxs-lookup"><span data-stu-id="4b992-120">**nx_dhcpv6_get_time_accrued:** *Get the time accrued the global IPv6 address lease has been bound to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="4b992-121">**nx_dhcpv6_get_time_server_address:** *지정된 인덱스의 시간 서버 주소를 DHCPv6 클라이언트 시간 서버 목록으로 가져오기*</span><span class="sxs-lookup"><span data-stu-id="4b992-121">**nx_dhcpv6_get_time_server_address:** *Get Time Server address at the specified index into the DHCPv6 Client Time server list*</span></span>

- <span data-ttu-id="4b992-122">**nx_dhcpv6_get_valid_ip_address_count:** *DHCPv6 클라이언트에 할당된 IPv6 주소 수 가져오기*</span><span class="sxs-lookup"><span data-stu-id="4b992-122">**nx_dhcpv6_get_valid_ip_address_count:** *Get the number of IPv6 addresses assigned to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="4b992-123">**nx_dhcpv6_reinitialize:** *DHCPv6 클라이언트 상태 시스템을 다시 시작하고 DHCPv6 프로토콜을 다시 실행하기 위해 DHCPv6 다시 초기화*</span><span class="sxs-lookup"><span data-stu-id="4b992-123">**nx_dhcpv6_reinitialize:** *Reinitialize the DHCPv6 for restarting the DHCPv6 Client state machine and rerunning the DHCPv6 protocol*</span></span> 

- <span data-ttu-id="4b992-124">**nx_dhcpv6_request_confirm:** *서버에 CONFIRM 요청 보내기*</span><span class="sxs-lookup"><span data-stu-id="4b992-124">**nx_dhcpv6_request_confirm:** *Send a CONFIRM request to the Server*</span></span> 

- <span data-ttu-id="4b992-125">**nx_dhcpv6_request_inform_request:** 서 *버에 INFORM REQUEST 메시지 보내기*</span><span class="sxs-lookup"><span data-stu-id="4b992-125">**nx_dhcpv6_request_inform_request:** S *end an INFORM REQUEST message to the Server*</span></span> 

- <span data-ttu-id="4b992-126">**nx_dhcpv6_request_release:** *서버에 RELEASE 요청 보내기*</span><span class="sxs-lookup"><span data-stu-id="4b992-126">**nx_dhcpv6_request_release:** *Send a RELEASE request to the Server*</span></span> 

- <span data-ttu-id="4b992-127">**nx_dhcpv6_request_option_DNS_server:** *서버에 대한 요청 메시지의 클라이언트 옵션 요청 데이터에 DNS 서버 옵션 추가*</span><span class="sxs-lookup"><span data-stu-id="4b992-127">**nx_dhcpv6_request_option_DNS_server:** *Add the DNS server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="4b992-128">**nx_dhcpv6_request_option_FQDN:** *서버에 대한 요청 메시지의 클라이언트 옵션 요청 데이터에 FQDN 옵션 추가*</span><span class="sxs-lookup"><span data-stu-id="4b992-128">**nx_dhcpv6_request_option_FQDN:** *Add the FQDN option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="4b992-129">**nx_dhcpv6_request_option_domain_name:** *서버에 대한 요청 메시지의 클라이언트 옵션 요청 데이터에 도메인 이름 옵션 추가*</span><span class="sxs-lookup"><span data-stu-id="4b992-129">**nx_dhcpv6_request_option_domain_name:** *Add the domain name option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="4b992-130">**nx_dhcpv6_request_option_time_server:** *서버에 대한 요청 메시지의 클라이언트 옵션 요청 데이터에 시간 서버 옵션 추가*</span><span class="sxs-lookup"><span data-stu-id="4b992-130">**nx_dhcpv6_request_option_time_server:** *Add the time server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="4b992-131">**nx_dhcpv6_request_option_timezone:** *서버에 대한 요청 메시지의 클라이언트 옵션 요청 데이터에 표준 시간대 옵션 추가*</span><span class="sxs-lookup"><span data-stu-id="4b992-131">**nx_dhcpv6_request_option_timezone:** *Add the time zone option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="4b992-132">**nx_dhcpv6_request_solicit:** *클라이언트 네트워크(브로드캐스트)의 모든 서버에 DHCPv6 SOLICIT 요청 보내기*</span><span class="sxs-lookup"><span data-stu-id="4b992-132">**nx_dhcpv6_request_solicit:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast)*</span></span> 

- <span data-ttu-id="4b992-133">**nx_dhcpv6_request_solicit_rapid:** *빠른 커밋 옵션이 설정된 클라이언트 네트워크(브로드캐스트)의 모든 서버에 DHCPv6 SOLICIT 요청 보내기*</span><span class="sxs-lookup"><span data-stu-id="4b992-133">**nx_dhcpv6_request_solicit_rapid:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast) with the Rapid Commit option set*</span></span> 

- <span data-ttu-id="4b992-134">**nx_dhcpv6_resume:** *DHCPv6 클라이언트 처리 다시 시작*</span><span class="sxs-lookup"><span data-stu-id="4b992-134">**nx_dhcpv6_resume:** *Resume DHCPv6 Client processing*</span></span> 

- <span data-ttu-id="4b992-135">**nx_dhcpv6_start:** *DHCPv6 클라이언트 스레드 작업 시작. 이 작업은 DHCPv6 상태 시스템을 시작하는 것과 동일하지 않으며 SOLICIT 요청을 보내지 않습니다.*</span><span class="sxs-lookup"><span data-stu-id="4b992-135">**nx_dhcpv6_start:** *Start the DHCPv6 Client thread task. Note this is not equivalent to starting the DHCPv6 state machine and does not send a SOLICIT request*</span></span> 

- <span data-ttu-id="4b992-136">**nx_dhcpv6_stop:** *DHCPv6 클라이언트 스레드 작업 중지*</span><span class="sxs-lookup"><span data-stu-id="4b992-136">**nx_dhcpv6_stop:** *Stop the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="4b992-137">**nx_dhcpv6_suspend:** *DHCPv6 클라이언트 스레드 작업 일시 중단*</span><span class="sxs-lookup"><span data-stu-id="4b992-137">**nx_dhcpv6_suspend:** *Suspend the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="4b992-138">**nx_dhcpv6_set_time_accrued:** *클라이언트 레코드에서 전역 클라이언트 IPv6 주소 임대의 누적 시간 설정*</span><span class="sxs-lookup"><span data-stu-id="4b992-138">**nx_dhcpv6_set_time_accrued:** *Set the time accrued on the global Client IPv6 address lease in the Client record.*</span></span>

## <a name="nx_dhcpv6_client_create"></a><span data-ttu-id="4b992-139">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="4b992-139">nx_dhcpv6_client_create</span></span>

<span data-ttu-id="4b992-140">DHCPv6 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="4b992-140">Create a DHCPv6 client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-141">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-141">Prototype</span></span>

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a><span data-ttu-id="4b992-142">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-142">Description</span></span>

<span data-ttu-id="4b992-143">이 서비스는 콜백 함수를 포함하는 DHCPv6 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-143">This service creates a DHCPv6 client instance including callback functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-144">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-144">Input Parameters</span></span>

- <span data-ttu-id="4b992-145">**dhcpv6_ptr** DHCPv6 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-145">**dhcpv6_ptr** Pointer to DHCPv6 control block</span></span>  

- <span data-ttu-id="4b992-146">**client_ptr** 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-146">**ip_ptr** Pointer to Client IP instance</span></span>  

- <span data-ttu-id="4b992-147">**name_ptr** DHCPv6 인스턴스의 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-147">**name_ptr** Pointer to name for DHCPv6 instance</span></span>

- <span data-ttu-id="4b992-148">**packet_pool_ptr** 클라이언트 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-148">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="4b992-149">**stack_ptr** 클라이언트 스택 메모리에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-149">**stack_ptr** Pointer to Client stack memory</span></span>

- <span data-ttu-id="4b992-150">**stack_size** 클라이언트 스택 메모리의 크기</span><span class="sxs-lookup"><span data-stu-id="4b992-150">**stack_size** Size of Client stack memory</span></span>

- <span data-ttu-id="4b992-151">**dhcpv6_state_change_notify** 클라이언트가 서버에 대한 새 DHCPv6 요청을 시작할 때 호출되는 콜백 함수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-151">**dhcpv6_state_change_notify** Pointer to callback function invoked when the Client initiates a new DHCPv6 request to the server</span></span>

- <span data-ttu-id="4b992-152">**dhcpv6_server_error_handler** 클라이언트가 서버에서 오류 상태를 받을 때 호출되는 콜백 함수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-152">**dhcpv6_server_error_handler** Pointer to callback function invoked when the Client receives an error status from the server</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-153">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-153">Return Values</span></span>

- <span data-ttu-id="4b992-154">**NX_SUCCESS**: (0x00) 성공적으로 클라이언트 생성</span><span class="sxs-lookup"><span data-stu-id="4b992-154">**NX_SUCCESS** (0x00) Successful Client create</span></span>

- <span data-ttu-id="4b992-155">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-155">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-156">NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-156">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-157">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-157">Allowed From</span></span>

<span data-ttu-id="4b992-158">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-159">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-159">Example</span></span>

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a><span data-ttu-id="4b992-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-160">See Also</span></span>

- <span data-ttu-id="4b992-161">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="4b992-161">nx_dhcpv6_client_delete</span></span>

## <a name="nx_dhcpv6_client_delete"></a><span data-ttu-id="4b992-162">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="4b992-162">nx_dhcpv6_client_delete</span></span>

<span data-ttu-id="4b992-163">DHCPv6 클라이언트 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="4b992-163">Delete a DHCPv6 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-164">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-164">Prototype</span></span>

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-165">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-165">Description</span></span>

<span data-ttu-id="4b992-166">이 서비스는 이전에 만든 DHCPv6 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-166">This service deletes a previously created DHCPv6 client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-167">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-167">Input Parameters</span></span>

- <span data-ttu-id="4b992-168">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-168">**dhcpv6_ptr** Pointer to DHCPv6 client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-169">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-169">Return Values</span></span>

- <span data-ttu-id="4b992-170">**NX_SUCCESS**: (0x00) 성공적인 DHCPv6 삭제</span><span class="sxs-lookup"><span data-stu-id="4b992-170">**NX_SUCCESS** (0x00) Successful DHCPv6 deletion</span></span>

- <span data-ttu-id="4b992-171">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-171">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-172">NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-172">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-173">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-173">Allowed From</span></span>

<span data-ttu-id="4b992-174">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-175">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-175">Example</span></span>

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="4b992-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-176">See Also</span></span>

- <span data-ttu-id="4b992-177">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="4b992-177">nx_dhcpv6_client_create</span></span>

## <a name="nx_dhcpv6_client_set_interface"></a><span data-ttu-id="4b992-178">nx_dhcpv6_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="4b992-178">nx_dhcpv6_client_set_interface</span></span>

<span data-ttu-id="4b992-179">DHCPv6에 대한 클라이언트의 네트워크 인터페이스 설정</span><span class="sxs-lookup"><span data-stu-id="4b992-179">Sets Client’s Network Interface for DHCPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-180">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-180">Prototype</span></span>

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="4b992-181">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-181">Description</span></span>

<span data-ttu-id="4b992-182">이 서비스는 DHCPv6 서버와 통신하기 위한 클라이언트의 네트워크 인터페이스를 지정된 입력 인터페이스 인덱스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-182">This service sets the Client’s network interface for communicating with the DHCPv6 Server(s) to the specified input interface index.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-183">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-183">Input Parameters</span></span>

- <span data-ttu-id="4b992-184">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-184">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-185">**interface_index** 네트워크 인터페이스를 지정하는 인덱스</span><span class="sxs-lookup"><span data-stu-id="4b992-185">**interface_index** Index indicating network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-186">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-186">Return Values</span></span>

- <span data-ttu-id="4b992-187">**NX_SUCCESS**: (0x00) 인터페이스가 성공적으로 설정됨</span><span class="sxs-lookup"><span data-stu-id="4b992-187">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="4b992-188">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-188">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-189">NX_INVALID_INTERFACE (0x4C) 잘못된 인터페이스 인덱스</span><span class="sxs-lookup"><span data-stu-id="4b992-189">NX_INVALID_INTERFACE (0x4C) Invalid interface index input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-190">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-190">Allowed From</span></span>

<span data-ttu-id="4b992-191">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-192">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-192">Example</span></span>

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a><span data-ttu-id="4b992-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-193">See Also</span></span>

- <span data-ttu-id="4b992-194">nx_dhcpv6_client _create</span><span class="sxs-lookup"><span data-stu-id="4b992-194">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="4b992-195">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="4b992-195">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_client_set_destination_address"></a><span data-ttu-id="4b992-196">nx_dhcpv6_client_set_destination_address</span><span class="sxs-lookup"><span data-stu-id="4b992-196">nx_dhcpv6_client_set_destination_address</span></span>

<span data-ttu-id="4b992-197">DHCPv6 메시지를 보낼 대상 주소 설정</span><span class="sxs-lookup"><span data-stu-id="4b992-197">Sets the destination address where DHCPv6 message should be sent to</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-198">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-198">Prototype</span></span>

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a><span data-ttu-id="4b992-199">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-199">Description</span></span>

<span data-ttu-id="4b992-200">이 서비스는 DHCPv6 메시지를 보내야 하는 대상 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-200">This service sets the destination address where DHCPv6 message should be sent to.</span></span> <span data-ttu-id="4b992-201">기본적으로 ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2)입니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-201">By default is ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-202">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-202">Input Parameters</span></span>

- <span data-ttu-id="4b992-203">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-203">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-204">**destination_address** 대상 주소</span><span class="sxs-lookup"><span data-stu-id="4b992-204">**destination_address** Destination address</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-205">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-205">Return Values</span></span>

- <span data-ttu-id="4b992-206">**NX_SUCCESS**: (0x00) 인터페이스가 성공적으로 설정됨</span><span class="sxs-lookup"><span data-stu-id="4b992-206">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="4b992-207">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-207">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-208">NX_DHCPV6_PARAM_ERROR (0xE93) 매개 변수 오류</span><span class="sxs-lookup"><span data-stu-id="4b992-208">NX_DHCPV6_PARAM_ERROR (0xE93) Parament error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-209">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-209">Allowed From</span></span>

<span data-ttu-id="4b992-210">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-210">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-211">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-211">Example</span></span>

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-212">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-212">See Also</span></span>

- <span data-ttu-id="4b992-213">nx_dhcpv6_client _create</span><span class="sxs-lookup"><span data-stu-id="4b992-213">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="4b992-214">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="4b992-214">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_create_client_duid"></a><span data-ttu-id="4b992-215">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="4b992-215">nx_dhcpv6_create_client_duid</span></span>

<span data-ttu-id="4b992-216">클라이언트 DUID 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="4b992-216">Create Client DUID object</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-217">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-217">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a><span data-ttu-id="4b992-218">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-218">Description</span></span>

<span data-ttu-id="4b992-219">이 서비스는 입력 매개 변수를 사용하여 클라이언트 DUID를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-219">This service creates the Client DUID with the input parameters.</span></span> <span data-ttu-id="4b992-220">입력이 제공되지 않고 DUID 형식이 시간이 포함된 링크 계층을 나타내는 경우 이 함수는 고유성을 위해 임의로 선택할 요소가 포함된 시간을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-220">If the time input is not supplied and the duid type indicates link layer with time, this function will supply a time which includes a randomizing factor for uniqueness.</span></span> <span data-ttu-id="4b992-221">공급업체에서 할당한 (엔터프라이즈) DUID 형식은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-221">Vendor assigned (enterprise) duid types are not supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-222">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-222">Input Parameters</span></span>

- <span data-ttu-id="4b992-223">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-223">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-224">**duid_type** DUID 형식(하드웨어, 엔터프라이즈 등)</span><span class="sxs-lookup"><span data-stu-id="4b992-224">**duid_type** Type of DUID (hardware, enterprise etc)</span></span>

- <span data-ttu-id="4b992-225">**hardware_type** 네트워크 하드웨어, 예: IEEE 802</span><span class="sxs-lookup"><span data-stu-id="4b992-225">**hardware_type** Network hardware e.g. IEEE 802</span></span>

- <span data-ttu-id="4b992-226">**시간** 고유 식별자를 만드는 데 사용되는 값</span><span class="sxs-lookup"><span data-stu-id="4b992-226">**time** Value used in creating unique identifier</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-227">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-227">Return Values</span></span>

- <span data-ttu-id="4b992-228">**NX_SUCCESS**: (0x00) 성공적으로 클라이언트가 생성됨</span><span class="sxs-lookup"><span data-stu-id="4b992-228">**NX_SUCCESS** (0x00) Successful Client DUID created</span></span>

- <span data-ttu-id="4b992-229">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-229">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-230">NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-230">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="4b992-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID 형식을 알 수 없거나 해당 형식이 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="4b992-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID type unknown or not supported</span></span> 

- <span data-ttu-id="4b992-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID 하드웨어 형식을 알 수 없거나 해당 형식이 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="4b992-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID hardware type unknown or not supported</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-233">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-233">Allowed From</span></span>

<span data-ttu-id="4b992-234">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-234">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-235">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-235">Example</span></span>

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="4b992-236">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-236">See Also</span></span>

- <span data-ttu-id="4b992-237">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="4b992-237">nx_dhcpv6_create_client_ia</span></span>
- <span data-ttu-id="4b992-238">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="4b992-238">nx_dhcpv6_create_client_iana</span></span>
- <span data-ttu-id="4b992-239">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="4b992-239">nx_dhcpv6_create_server_duid</span></span>

## <a name="nx_dhcpv6_create_client_ia"></a><span data-ttu-id="4b992-240">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="4b992-240">nx_dhcpv6_create_client_ia</span></span>

<span data-ttu-id="4b992-241">클라이언트에 ID 연결 추가</span><span class="sxs-lookup"><span data-stu-id="4b992-241">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-242">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-242">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="4b992-243">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-243">Description</span></span>

<span data-ttu-id="4b992-244">이 서비스는 *nx_dhcpv6_add_client_ia* 서비스와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-244">This service is identical to the *nx_dhcpv6_add_client_ia* service.</span></span> <span data-ttu-id="4b992-245">클라이언트 레코드를 제공된 매개 변수로 채워서 클라이언트 ID 연결을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-245">It adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="4b992-246">최대 기본 설정 수명 및 유효한 수명을 요청하려면 이러한 매개 변수를 infinity로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-246">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="4b992-247">하나 이상의 IA를 DHCPv6 클라이언트에 추가하려면 NX_DHCPV6_MAX_IA_ADDRESS를 기본값인 1보다 큰 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-247">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-248">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-248">Input Parameters</span></span>

- <span data-ttu-id="4b992-249">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-249">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-250">**ipv6_address** NetX Duo IP 주소 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-250">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="4b992-251">**preferred_lifetime** IP 주소가 더 이상 사용되지 않게 될 때까지의 시간</span><span class="sxs-lookup"><span data-stu-id="4b992-251">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="4b992-252">**valid_lifetime** IP 주소가 만료될 때까지의 시간</span><span class="sxs-lookup"><span data-stu-id="4b992-252">**valid_lifetime** Length of time before IP address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-253">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-253">Return Values</span></span>

- <span data-ttu-id="4b992-254">**NX_SUCCESS**: (0x00) 성공적으로 클라이언트 IA가 추가됨</span><span class="sxs-lookup"><span data-stu-id="4b992-254">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="4b992-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST**(0xEAF) 중복 IA 주소</span><span class="sxs-lookup"><span data-stu-id="4b992-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="4b992-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS**(0xEAE) IA가 클라이언트에서 저장할 수 있는 최대 IA 수를 초과함</span><span class="sxs-lookup"><span data-stu-id="4b992-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="4b992-257">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-257">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) IA의 잘못된(예: Null) IA 주소</span><span class="sxs-lookup"><span data-stu-id="4b992-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="4b992-259">NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-259">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>


### <a name="allowed-from"></a><span data-ttu-id="4b992-260">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-260">Allowed From</span></span>

<span data-ttu-id="4b992-261">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-261">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-262">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-262">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="4b992-263">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-263">See Also</span></span>

- <span data-ttu-id="4b992-264">nx_dhcpv6_add_client_duid</span><span class="sxs-lookup"><span data-stu-id="4b992-264">nx_dhcpv6_add_client_duid</span></span>
- <span data-ttu-id="4b992-265">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="4b992-265">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="4b992-266">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="4b992-266">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_create_client_iana"></a><span data-ttu-id="4b992-267">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="4b992-267">nx_dhcpv6_create_client_iana</span></span>

<span data-ttu-id="4b992-268">클라이언트에 대한 ID 연결(비 임시) 만들기</span><span class="sxs-lookup"><span data-stu-id="4b992-268">Create an Identity Association (Non Temporary) for the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-269">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-269">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a><span data-ttu-id="4b992-270">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-270">Description</span></span>

<span data-ttu-id="4b992-271">이 서비스는 제공된 매개 변수에서 클라이언트 IANA(비 임시 주소용 ID 연결)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-271">This service creates a Client Non Temporary Identity Association (IANA) from the supplied parameters.</span></span> <span data-ttu-id="4b992-272">DHCPv6 클라이언트 요청에서 T1 및 T2 시간을 최대(infinity)로 설정하려면 이러한 매개 변수를 NX_DHCPV6_INFINITE_LEASE로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-272">To set the T1 and T2 times to maximum (infinity) in the DHCPv6 Client requests, set these parameters to NX_DHCPV6_INFINITE_LEASE.</span></span> 

> [!NOTE]
> <span data-ttu-id="4b992-273">클라이언트에는 IANA가 하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-273">A Client has only one IANA.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-274">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-274">Input Parameters</span></span>

- <span data-ttu-id="4b992-275">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-275">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-276">**IA_ident** ID 연결 고유 식별자</span><span class="sxs-lookup"><span data-stu-id="4b992-276">**IA_ident** Identity Association unique identifier</span></span>

- <span data-ttu-id="4b992-277">**T1** 클라이언트가 IPv6 주소 갱신을 시작해야 하는 시간</span><span class="sxs-lookup"><span data-stu-id="4b992-277">**T1** When the Client must start the IPv6 address renewal</span></span>

- <span data-ttu-id="4b992-278">**T2** 클라이언트가 theIPv6 주소 리바인딩을 시작해야 하는 시간</span><span class="sxs-lookup"><span data-stu-id="4b992-278">**T2** When the Client must start theIPv6 address rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-279">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-279">Return Values</span></span>

- <span data-ttu-id="4b992-280">**NX_SUCCESS**(0x00) 성공적으로 IANA가 생성됨</span><span class="sxs-lookup"><span data-stu-id="4b992-280">**NX_SUCCESS** (0x00) Successfully created the IANA</span></span>

- <span data-ttu-id="4b992-281">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-281">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-282">NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-282">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-283">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-283">Allowed From</span></span>

<span data-ttu-id="4b992-284">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-285">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-285">Example</span></span>

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="4b992-286">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-286">See Also</span></span>

- <span data-ttu-id="4b992-287">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="4b992-287">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="4b992-288">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="4b992-288">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="4b992-289">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="4b992-289">nx_dhcpv6_add_client_ia</span></span>

## <a name="nx_dhcpv6_add_client_ia"></a><span data-ttu-id="4b992-290">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="4b992-290">nx_dhcpv6_add_client_ia</span></span> 

<span data-ttu-id="4b992-291">클라이언트에 ID 연결 추가</span><span class="sxs-lookup"><span data-stu-id="4b992-291">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-292">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-292">Prototype</span></span>

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="4b992-293">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-293">Description</span></span>

<span data-ttu-id="4b992-294">이 서비스는 클라이언트 레코드를 제공된 매개 변수로 채워서 클라이언트 ID 연결을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-294">This service adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="4b992-295">최대 기본 설정 수명 및 유효한 수명을 요청하려면 이러한 매개 변수를 infinity로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-295">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="4b992-296">하나 이상의 IA를 DHCPv6 클라이언트에 추가하려면 NX_DHCPV6_MAX_IA_ADDRESS를 기본값인 1보다 큰 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-296">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-297">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-297">Input Parameters</span></span>

- <span data-ttu-id="4b992-298">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-298">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-299">**ipv6_address** NetX Duo IP 주소 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-299">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="4b992-300">**preferred_lifetime** IP 주소가 더 이상 사용되지 않게 될 때까지의 시간</span><span class="sxs-lookup"><span data-stu-id="4b992-300">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="4b992-301">**valid_lifetime** IP 주소가 만료될 때까지의 시간</span><span class="sxs-lookup"><span data-stu-id="4b992-301">**valid_lifetime** Length of time before IP address is expired</span></span> 

### <a name="return-values"></a><span data-ttu-id="4b992-302">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-302">Return Values</span></span>

- <span data-ttu-id="4b992-303">**NX_SUCCESS**: (0x00) 성공적으로 클라이언트 IA가 추가됨</span><span class="sxs-lookup"><span data-stu-id="4b992-303">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="4b992-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST**(0xEAF) 중복 IA 주소</span><span class="sxs-lookup"><span data-stu-id="4b992-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="4b992-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS**(0xEAE) IA가 클라이언트에서 저장할 수 있는 최대 IA 수를 초과함</span><span class="sxs-lookup"><span data-stu-id="4b992-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="4b992-306">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-306">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) IA의 잘못된(예: Null) IA 주소</span><span class="sxs-lookup"><span data-stu-id="4b992-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="4b992-308">NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-308">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

 
### <a name="allowed-from"></a><span data-ttu-id="4b992-309">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-309">Allowed From</span></span>

<span data-ttu-id="4b992-310">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-311">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-311">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="4b992-312">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-312">See Also</span></span>

- <span data-ttu-id="4b992-313">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="4b992-313">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="4b992-314">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="4b992-314">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="4b992-315">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="4b992-315">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_get_client_duid_time_id"></a><span data-ttu-id="4b992-316">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="4b992-316">nx_dhcpv6_get_client_duid_time_id</span></span>

<span data-ttu-id="4b992-317">클라이언트 DUID에서 시간 ID 검색</span><span class="sxs-lookup"><span data-stu-id="4b992-317">Retrieves time ID from Client DUID</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-318">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-318">Prototype</span></span>

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a><span data-ttu-id="4b992-319">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-319">Description</span></span>

<span data-ttu-id="4b992-320">이 서비스는 클라이언트 DUID에서 시간 ID 필드를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-320">This service retrieves the time ID field from the Client DUID.</span></span> <span data-ttu-id="4b992-321">애플리케이션에서 먼저 *nx_dhcpv6_create_client_duid* 를 호출해야 하는 경우에는 DHCPv6 클라이언트 인스턴스에서 클라이언트 DUID를 채웁니다. 그러지 않으면 이 필드에 Null 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-321">If the application must first call *nx_dhcpv6_create_client_duid*, to fill in the Client DUID in the DHCPv6 Client instance or it will have a null value for this field.</span></span> <span data-ttu-id="4b992-322">이 작업의 목적은 애플리케이션에서 이 데이터를 저장하고 여러 번의 다시 부팅에 걸쳐 시간 필드를 포함하여 동일한 클라이언트 DUID를 서버에 제공하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-322">The intent is for the application to save this data and present the same Client DUID to the server, including the time field, across reboots.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-323">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-323">Input Parameters</span></span>

- <span data-ttu-id="4b992-324">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-324">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-325">**time_id** 클라이언트 DUID 시간 필드에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-325">**time_id** Pointer to Client DUID time field</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-326">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-326">Return Values</span></span>

- <span data-ttu-id="4b992-327">**NX_SUCCESS**(0x00) IP 임대 데이터가 성공적으로 검색됨</span><span class="sxs-lookup"><span data-stu-id="4b992-327">**NX_SUCCESS** (0x00) IP lease data successfully retrieved</span></span>

- <span data-ttu-id="4b992-328">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-328">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-329">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-329">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-330">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-330">Allowed From</span></span>

<span data-ttu-id="4b992-331">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-331">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-332">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-332">Example</span></span>

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-333">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-333">See Also</span></span>

- <span data-ttu-id="4b992-334">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="4b992-334">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="4b992-335">nx_dhcpv6_get_time_lease_data</span><span class="sxs-lookup"><span data-stu-id="4b992-335">nx_dhcpv6_get_time_lease_data</span></span>
- <span data-ttu-id="4b992-336">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="4b992-336">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="4b992-337">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="4b992-337">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_ip_address"></a><span data-ttu-id="4b992-338">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="4b992-338">nx_dhcpv6_get_IP_address</span></span>

<span data-ttu-id="4b992-339">클라이언트의 전역 IPv6 주소 검색</span><span class="sxs-lookup"><span data-stu-id="4b992-339">Retrieves Client’s global IPv6 address</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-340">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-340">Prototype</span></span>

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a><span data-ttu-id="4b992-341">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-341">Description</span></span>

<span data-ttu-id="4b992-342">이 서비스는 클라이언트의 전역 IPv6 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-342">This service retrieves the Client’s global IPv6 address.</span></span> <span data-ttu-id="4b992-343">클라이언트에 유효한 주소가 없으면 오류 상태가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-343">If the Client does not have a valid address, an error status is returned.</span></span> <span data-ttu-id="4b992-344">클라이언트에 두 개 이상의 전역 IPv6 주소가 있는 경우 주 IPv6 주소가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-344">If a Client has more than one global IPv6 address, the primary IPv6 address is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-345">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-345">Input Parameters</span></span>

- <span data-ttu-id="4b992-346">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-346">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-347">**ip_address** IPv6 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-347">**ip_address** Pointer to IPv6 address</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-348">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-348">Return Values</span></span>

- <span data-ttu-id="4b992-349">**NX_SUCCESS**(0x00) IPv6 주소가 성공적으로 할당됨</span><span class="sxs-lookup"><span data-stu-id="4b992-349">**NX_SUCCESS** (0x00) IPv6 address successfully assigned</span></span>

- <span data-ttu-id="4b992-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID**(0xEAD) IPv6 주소가 유효하지 않음</span><span class="sxs-lookup"><span data-stu-id="4b992-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) IPv6 address is not valid</span></span>

- <span data-ttu-id="4b992-351">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-351">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-352">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-352">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-353">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-353">Allowed From</span></span>

<span data-ttu-id="4b992-354">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-354">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-355">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-355">Example</span></span>

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a><span data-ttu-id="4b992-356">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-356">See Also</span></span>

- <span data-ttu-id="4b992-357">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="4b992-357">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="4b992-358">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="4b992-358">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="4b992-359">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="4b992-359">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="4b992-360">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="4b992-360">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_lease_time_data"></a><span data-ttu-id="4b992-361">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="4b992-361">nx_dhcpv6_get_lease_time_data</span></span>

<span data-ttu-id="4b992-362">클라이언트의 IA 주소 임대 시간 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="4b992-362">Retrieves Client’s IA address lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-363">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-363">Prototype</span></span>

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="4b992-364">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-364">Description</span></span>

<span data-ttu-id="4b992-365">이 서비스는 클라이언트의 전역 IA 주소 시간 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-365">This service retrieves the Client’s global IA address time data.</span></span> <span data-ttu-id="4b992-366">클라이언트 IA 주소 상태가 잘못된 경우 시간 데이터가 0으로 설정되고 성공적인 완료 상태가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-366">If the Client IA address status is invalid, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="4b992-367">클라이언트에 두 개 이상의 전역 IPv6 주소가 있는 경우 주 IA 주소 데이터가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-367">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-368">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-368">Input Parameters</span></span>

- <span data-ttu-id="4b992-369">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-369">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-370">**T1** IA 주소 갱신 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-370">**T1** Pointer to IA address renew time</span></span>

- <span data-ttu-id="4b992-371">**T2** IA 주소의 다시 바인딩 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-371">**T2** Pointer to IA address rebind time</span></span>

- <span data-ttu-id="4b992-372">**preferred_lifetime** IA 주소가 더 이상 사용되지 않게 되는 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-372">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="4b992-373">**valid_lifetime** IA 주소가 만료되는 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-373">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-374">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-374">Return Values</span></span>

- <span data-ttu-id="4b992-375">**NX_SUCCESS**(0x00) IA 임대 데이터가 성공적으로 검색됨</span><span class="sxs-lookup"><span data-stu-id="4b992-375">**NX_SUCCESS** (0x00) IA lease data successfully retrieved</span></span>

- <span data-ttu-id="4b992-376">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-376">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-377">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-377">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-378">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-378">Allowed From</span></span>

<span data-ttu-id="4b992-379">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-380">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-380">Example</span></span>

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="4b992-381">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-381">See Also</span></span>

- <span data-ttu-id="4b992-382">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="4b992-382">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="4b992-383">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="4b992-383">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="4b992-384">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="4b992-384">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="4b992-385">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="4b992-385">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="4b992-386">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="4b992-386">nx_dhcpv6_get_iana_lease_time</span></span>

## <a name="nx_dhcpv6_get_iana-lease_time"></a><span data-ttu-id="4b992-387">nx_dhcpv6_get_iana lease_time</span><span class="sxs-lookup"><span data-stu-id="4b992-387">nx_dhcpv6_get_iana lease_time</span></span>

<span data-ttu-id="4b992-388">클라이언트의 IANA 임대 시간 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="4b992-388">Retrieve the Client’s IANA lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-389">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-389">Prototype</span></span>

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a><span data-ttu-id="4b992-390">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-390">Description</span></span>

<span data-ttu-id="4b992-391">이 서비스는 클라이언트의 전역 IA-NA 임대 시간 데이터(T1 및 T2)를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-391">This service retrieves the Client’s global IA-NA lease time data (T1 and T2).</span></span> <span data-ttu-id="4b992-392">클라이언트 IA-NA 주소에 유효한 주소 상태가 없는 경우 시간 데이터가 0으로 설정되고 성공적인 완료 상태가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-392">If none of the Client IA-NA addresses have a valid address status, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="4b992-393">클라이언트에 두 개 이상의 전역 IPv6 주소가 있는 경우 주 IA 주소 데이터가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-393">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-394">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-394">Input Parameters</span></span>

- <span data-ttu-id="4b992-395">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-395">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-396">**T1** 임대 갱신을 시작하는 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-396">**T1** Pointer to time for starting lease renewal</span></span>

- <span data-ttu-id="4b992-397">**T2** 임대 다시 바인딩 시작 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-397">**T2** Pointer to time for starting lease rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-398">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-398">Return Values</span></span>

- <span data-ttu-id="4b992-399">**NX_SUCCESS**(0x00) IANA 임대 데이터가 성공적으로 검색됨</span><span class="sxs-lookup"><span data-stu-id="4b992-399">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="4b992-400">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-400">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-401">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-401">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-402">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-402">Allowed From</span></span>

<span data-ttu-id="4b992-403">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-403">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-404">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-404">Example</span></span>

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="4b992-405">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-405">See Also</span></span>

- <span data-ttu-id="4b992-406">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="4b992-406">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="4b992-407">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="4b992-407">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="4b992-408">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="4b992-408">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="4b992-409">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="4b992-409">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="4b992-410">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="4b992-410">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a><span data-ttu-id="4b992-411">nx_dhcpv6_get_valid_ip_address_count</span><span class="sxs-lookup"><span data-stu-id="4b992-411">nx_dhcpv6_get_valid_ip_address_count</span></span>

<span data-ttu-id="4b992-412">클라이언트의 유효한 IA 주소 수 검색</span><span class="sxs-lookup"><span data-stu-id="4b992-412">Retrieve a count of Client’s valid IA addresses</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-413">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-413">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a><span data-ttu-id="4b992-414">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-414">Description</span></span>

<span data-ttu-id="4b992-415">이 서비스는 클라이언트의 유효한 IPv6 주소 수를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-415">This service retrieves the count of the Client’s valid IPv6 addresses.</span></span> <span data-ttu-id="4b992-416">유효한 IPv6 주소는 클라이언트에 바인딩(할당)되고 IP 인스턴스에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-416">A valid IPv6 address is bound (assigned) to the Client and registered with the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-417">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-417">Input Parameters</span></span>

- <span data-ttu-id="4b992-418">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-418">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-419">**address_count** 반환할 주소 수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-419">**address_count** Pointer to address count to return</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-420">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-420">Return Values</span></span>

- <span data-ttu-id="4b992-421">**NX_SUCCESS**(0x00) IANA 임대 데이터가 성공적으로 검색됨</span><span class="sxs-lookup"><span data-stu-id="4b992-421">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="4b992-422">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-422">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-423">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-423">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-424">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-424">Allowed From</span></span>

<span data-ttu-id="4b992-425">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-425">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-426">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-426">Example</span></span>

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a><span data-ttu-id="4b992-427">nx_dhcpv6_get_valid_ip_address_lease_time</span><span class="sxs-lookup"><span data-stu-id="4b992-427">nx_dhcpv6_get_valid_ip_address_lease_time</span></span>

<span data-ttu-id="4b992-428">주소 인덱스를 기준으로 클라이언트 IA 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="4b992-428">Retrieve the Client IA data by address index</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-429">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-429">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="4b992-430">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-430">Description</span></span>

<span data-ttu-id="4b992-431">이 서비스는 클라이언트의 IA 주소를 검색하고 주소 인덱스를 기준으로 데이터를 임대합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-431">This service retrieves the Client’s IA address and lease data by address index.</span></span> <span data-ttu-id="4b992-432">잘못된 인덱스를 제공하거나 해당 인덱스의 IPv6 주소가 잘못된 경우 서비스는 NX_DHCPV6_IA_ADDRESS_NOT_VALID 오류 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-432">If an invalid index is supplied, or the IPv6 address at that index is not valid, the service returns an NX_DHCPV6_IA_ADDRESS_NOT_VALID error status.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-433">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-433">Input Parameters</span></span>

- <span data-ttu-id="4b992-434">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-434">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-435">**address_index** DHCPv6 IA 테이블로 인덱싱</span><span class="sxs-lookup"><span data-stu-id="4b992-435">**address_index** Index into DHCPv6 IA table</span></span>

- <span data-ttu-id="4b992-436">**ip_address** 검색할 IPv6 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-436">**ip_address** Pointer to IPv6 address to retrieve</span></span>

- <span data-ttu-id="4b992-437">**preferred_lifetime** IA 주소가 더 이상 사용되지 않게 되는 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-437">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="4b992-438">**valid_lifetime** IA 주소가 만료되는 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-438">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-439">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-439">Return Values</span></span>

- <span data-ttu-id="4b992-440">**NX_SUCCESS**(0x00) IANA 데이터가 성공적으로 검색됨</span><span class="sxs-lookup"><span data-stu-id="4b992-440">**NX_SUCCESS** (0x00) IANA data successfully retrieved</span></span>

- <span data-ttu-id="4b992-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID**(0xEAD) 잘못된 인덱스 또는 제공된 인덱스에 유효한 IPv6 주소 없음</span><span class="sxs-lookup"><span data-stu-id="4b992-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) An invalid index or no valid IPv6 address at the supplied index</span></span> 

- <span data-ttu-id="4b992-442">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-442">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-443">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-443">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-444">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-444">Allowed From</span></span>

<span data-ttu-id="4b992-445">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-445">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-446">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-446">Example</span></span>

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="4b992-447">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-447">See Also</span></span>

- <span data-ttu-id="4b992-448">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="4b992-448">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="4b992-449">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="4b992-449">nx_dhcpv6_get_iana_lease_time</span></span>
- <span data-ttu-id="4b992-450">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="4b992-450">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_dns_server_address"></a><span data-ttu-id="4b992-451">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="4b992-451">nx_dhcpv6_get_DNS_server_address</span></span>

<span data-ttu-id="4b992-452">DNS 서버 주소 검색</span><span class="sxs-lookup"><span data-stu-id="4b992-452">Retrieves DNS Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="4b992-453">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-453">Prototype</span></span>

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="4b992-454">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-454">Description</span></span>

<span data-ttu-id="4b992-455">이 서비스는 클라이언트 목록의 지정된 인덱스에 있는 DNS 서버 IPv6 주소 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-455">This service retrieves the DNS server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="4b992-456">목록이 인덱스에 서버 주소를 포함하지 않는 경우 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-456">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="4b992-457">인덱스는 사용자 구성 가능한 옵션인 NX_DHCPV6_NUM_DNS_SERVERS로 지정된 DNS 서버 목록의 크기를 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-457">The index may not exceed the size of the DNS Server list is specified by the user configurable option NX_DHCPV6_NUM_DNS_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-458">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-458">Input Parameters</span></span>

- <span data-ttu-id="4b992-459">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-459">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-460">**index** DNS 서버 목록에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="4b992-460">**index** Index into the DNS Server list</span></span>

- <span data-ttu-id="4b992-461">**server_address** 서버 주소 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-461">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-462">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-462">Return Values</span></span>

- <span data-ttu-id="4b992-463">**NX_SUCCESS**(0x00) 주소가 성공적으로 검색됨</span><span class="sxs-lookup"><span data-stu-id="4b992-463">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="4b992-464">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-464">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-465">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-465">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-466">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-466">Allowed From</span></span>

<span data-ttu-id="4b992-467">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-467">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-468">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-468">Example</span></span>

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-469">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-469">See Also</span></span>

- <span data-ttu-id="4b992-470">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="4b992-470">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="4b992-471">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="4b992-471">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="4b992-472">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="4b992-472">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_other_option_data"></a><span data-ttu-id="4b992-473">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="4b992-473">nx_dhcpv6_get_other_option_data</span></span>

<span data-ttu-id="4b992-474">DHCPv6 옵션 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="4b992-474">Retrieves DHCPv6 option data</span></span> 

### <a name="prototype"></a><span data-ttu-id="4b992-475">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-475">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="4b992-476">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-476">Description</span></span>

<span data-ttu-id="4b992-477">이 서비스는 지정된 옵션 코드에 대해 DHCPv6 메시지에서 DHCPv6 옵션 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-477">This service retrieves DHCPv6 option data from a DHCPv6 message for the specified option code.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-478">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-478">Input Parameters</span></span>

- <span data-ttu-id="4b992-479">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-479">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-480">**option** 코드 검색할 데이터가 있는 옵션 코드</span><span class="sxs-lookup"><span data-stu-id="4b992-480">**option** code Option code for which data to retrieve</span></span>

- <span data-ttu-id="4b992-481">**buffer** 데이터를 복사할 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-481">**buffer** Pointer to buffer to copy data to</span></span> 

### <a name="return-values"></a><span data-ttu-id="4b992-482">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-482">Return Values</span></span>

- <span data-ttu-id="4b992-483">**NX_SUCCESS**(0x00) 옵션 데이터가 성공적으로 검색됨</span><span class="sxs-lookup"><span data-stu-id="4b992-483">**NX_SUCCESS** (0x00) Option data successfully retrieved</span></span>

- <span data-ttu-id="4b992-484">**NX_DHCPV6_UNKNOWN_OPTION**(0xEAB) 알 수 없거나 지원되지 않는 옵션 코드</span><span class="sxs-lookup"><span data-stu-id="4b992-484">**NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Unknown/unsupported option code</span></span>

- <span data-ttu-id="4b992-485">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-485">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-486">NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-486">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="4b992-487">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-487">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-488">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-488">Allowed From</span></span>

<span data-ttu-id="4b992-489">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-489">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-490">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-490">Example</span></span>

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-491">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-491">See Also</span></span>

- <span data-ttu-id="4b992-492">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="4b992-492">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="4b992-493">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="4b992-493">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="4b992-494">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="4b992-494">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_accrued"></a><span data-ttu-id="4b992-495">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="4b992-495">nx_dhcpv6_get_time_accrued</span></span>

<span data-ttu-id="4b992-496">클라이언트의 IP 주소 임대의 누적 시간 검색</span><span class="sxs-lookup"><span data-stu-id="4b992-496">Retrieves time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-497">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-497">Prototype</span></span>

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a><span data-ttu-id="4b992-498">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-498">Description</span></span>

<span data-ttu-id="4b992-499">이 서비스는 클라이언트의 IPv6 주소 임대의 누적 시간을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-499">This service retrieves the time accrued on the Client’s IPv6 address lease.</span></span> <span data-ttu-id="4b992-500">함수는 첫 번째 유효한 주소의 클라이언트에 할당된 모든 IPv6 주소를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-500">The function checks all the IPv6 addresses assigned to the Client for the first valid address.</span></span> <span data-ttu-id="4b992-501">유효한 주소가 없으면 누적 시간에 대해 0 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-501">If no valid addresses are found, a zero value for time accrued is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-502">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-502">Input Parameters</span></span>

- <span data-ttu-id="4b992-503">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-503">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-504">**time_accrued** IP 임대에서 누적 시간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-504">**time_accrued** Pointer to time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-505">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-505">Return Values</span></span>

- <span data-ttu-id="4b992-506">**NX_SUCCESS**(0x00) 누적 시간이 성공적으로 검색됨</span><span class="sxs-lookup"><span data-stu-id="4b992-506">**NX_SUCCESS** (0x00) Accrued time successfully retrieved</span></span>

- <span data-ttu-id="4b992-507">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-507">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-508">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-508">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-509">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-509">Allowed From</span></span>

<span data-ttu-id="4b992-510">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-510">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-511">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-511">Example</span></span>

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-512">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-512">See Also</span></span>

- <span data-ttu-id="4b992-513">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="4b992-513">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="4b992-514">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="4b992-514">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="4b992-515">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="4b992-515">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="4b992-516">nx_dhcpv6_set_time_accrued</span><span class="sxs-lookup"><span data-stu-id="4b992-516">nx_dhcpv6_set_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_server_address"></a><span data-ttu-id="4b992-517">nx_dhcpv6_get_time_server_address</span><span class="sxs-lookup"><span data-stu-id="4b992-517">nx_dhcpv6_get_time_server_address</span></span>

<span data-ttu-id="4b992-518">시간 서버 주소 검색</span><span class="sxs-lookup"><span data-stu-id="4b992-518">Retrieves Time Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="4b992-519">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-519">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="4b992-520">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-520">Description</span></span>

<span data-ttu-id="4b992-521">이 서비스는 클라이언트 목록의 지정된 인덱스에 있는 시간 서버 IPv6 주소 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-521">This service retrieves the Time server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="4b992-522">목록이 인덱스에 서버 주소를 포함하지 않는 경우 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-522">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="4b992-523">인덱스는 사용자 구성 가능한 옵션인 NX_DHCPV6_NUM_TIME_SERVERS로 지정된 시간 서버 목록의 크기를 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-523">The index may not exceed the size of the Time Server list is specified by the user configurable option NX_DHCPV6_NUM_TIME_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-524">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-524">Input Parameters</span></span>

- <span data-ttu-id="4b992-525">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-525">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-526">**index** 시간 서버 목록에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="4b992-526">**index** Index into the Time Server list</span></span>

- <span data-ttu-id="4b992-527">**server_address** 서버 주소 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-527">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-528">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-528">Return Values</span></span>

- <span data-ttu-id="4b992-529">**NX_SUCCESS**(0x00) 주소가 성공적으로 검색됨</span><span class="sxs-lookup"><span data-stu-id="4b992-529">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="4b992-530">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-530">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-531">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-531">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-532">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-532">Allowed From</span></span>

<span data-ttu-id="4b992-533">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-533">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-534">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-534">Example</span></span>

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-535">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-535">See Also</span></span>

- <span data-ttu-id="4b992-536">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="4b992-536">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="4b992-537">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="4b992-537">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="4b992-538">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="4b992-538">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="4b992-539">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="4b992-539">nx_dhcpv6_get_DNS_server_address</span></span>

## <a name="nx_dhcpv6_reinitialize"></a><span data-ttu-id="4b992-540">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="4b992-540">nx_dhcpv6_reinitialize</span></span>

<span data-ttu-id="4b992-541">IP 테이블에서 클라이언트 IP 주소 제거</span><span class="sxs-lookup"><span data-stu-id="4b992-541">Remove the Client IP address from the IP table</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-542">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-542">Prototype</span></span>

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-543">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-543">Description</span></span>

<span data-ttu-id="4b992-544">이 서비스는 DHCPv6 상태 시스템을 다시 시작하고 DHCPv6 프로토콜을 다시 실행하기 위해 클라이언트를 다시 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-544">This service reinitializes the Client for restarting the DHCPv6 state machine and re-running the DHCPv6 protocol.</span></span> <span data-ttu-id="4b992-545">클라이언트에서 이전에 DHPCv6 상태 시스템을 시작하지 않았거나 IPv6 주소가 할당된 경우에는 이 작업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-545">This is not necessary if the Client has not previously started the DHPCv6 state machine or been assigned any IPv6 addresses.</span></span> <span data-ttu-id="4b992-546">DHCPv6 클라이언트에 저장되고 IP 인스턴스에 등록된 주소는 모두 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-546">The addresses saved to the DHCPv6 Client as well as registered with the IP instance are both cleared.</span></span>

> [!NOTE]
> <span data-ttu-id="4b992-547">애플리케이션은 여전히 *nx_dhcpv6_start 서비스* 를 사용하여 DHCPv6 클라이언트를 시작하고 *nx_dhcpv6_request_solicit* 를 호출하여 IPv6 주소 할당에 대한 요청을 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-547">The application must still start the DHCPv6 Client using the *nx_dhcpv6_start service* and begin the request for IPv6 address assignment by calling *nx_dhcpv6_request_solicit*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-548">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-548">Input Parameters</span></span>

- <span data-ttu-id="4b992-549">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-549">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-550">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-550">Return Values</span></span>

- <span data-ttu-id="4b992-551">**NX_SUCCESS**(0x00) 주소가 성공적으로 제거됨</span><span class="sxs-lookup"><span data-stu-id="4b992-551">**NX_SUCCESS** (0x00) Address successfully removed</span></span>

- <span data-ttu-id="4b992-552">**NX_DHCPV6_ALREADY_STARTED**(0xE91) DHCPv6 클라이언트가 이미 실행 중임</span><span class="sxs-lookup"><span data-stu-id="4b992-552">**NX_DHCPV6_ALREADY_STARTED** (0xE91) DHCPv6 Client is already running</span></span>

- <span data-ttu-id="4b992-553">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-553">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-554">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-554">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-555">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-555">Allowed From</span></span>

<span data-ttu-id="4b992-556">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-556">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-557">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-557">Example</span></span>

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-558">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-558">See Also</span></span>

- <span data-ttu-id="4b992-559">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="4b992-559">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="4b992-560">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="4b992-560">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_request_confirm"></a><span data-ttu-id="4b992-561">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="4b992-561">nx_dhcpv6_request_confirm</span></span>

<span data-ttu-id="4b992-562">클라이언트의 CONFIRM 상태 처리</span><span class="sxs-lookup"><span data-stu-id="4b992-562">Process the Client’s CONFIRM state</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-563">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-563">Prototype</span></span>

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-564">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-564">Description</span></span>

<span data-ttu-id="4b992-565">이 서비스는 CONFIRM 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-565">This service sends a CONFIRM request.</span></span> <span data-ttu-id="4b992-566">서버에서 회신을 받으면 DHCPv6 클라이언트가 받은 데이터를 사용하여 임대 매개 변수를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-566">If a reply is received from the Server, the DHCPv6 Client updates its lease parameters with the received data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-567">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-567">Input Parameters</span></span>

- <span data-ttu-id="4b992-568">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-568">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-569">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-569">Return Values</span></span>

- <span data-ttu-id="4b992-570">**NX_SUCCESS**(0x00) CONFIRM 메시지가 성공적으로 전송 및 처리됨</span><span class="sxs-lookup"><span data-stu-id="4b992-570">**NX_SUCCESS** (0x00) CONFIRM message successfully sent and processed</span></span>

- <span data-ttu-id="4b992-571">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-571">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-572">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-572">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-573">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-573">Allowed From</span></span>

<span data-ttu-id="4b992-574">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-574">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-575">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-575">Example</span></span>

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-576">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-576">See Also</span></span>

- <span data-ttu-id="4b992-577">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="4b992-577">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="4b992-578">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="4b992-578">nx_dhcpv6_request_release</span></span>
- <span data-ttu-id="4b992-579">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="4b992-579">nx_dhcpv6_request_solicit</span></span>


## <a name="nx_dhcpv6_request_inform_request"></a><span data-ttu-id="4b992-580">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="4b992-580">nx_dhcpv6_request_inform_request</span></span>

<span data-ttu-id="4b992-581">클라이언트의 INFORM REQUEST 상태 처리</span><span class="sxs-lookup"><span data-stu-id="4b992-581">Process the Client’s INFORM REQUEST state</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-582">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-582">Prototype</span></span>

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-583">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-583">Description</span></span>

<span data-ttu-id="4b992-584">이 서비스는 INFORM REQUEST 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-584">This service sends an INFORM REQUEST message.</span></span> <span data-ttu-id="4b992-585">회신을 받으면 회신이 유효하며 서버에서 요청을 허용했는지 확인하도록 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-585">If a reply is received, When one is received, the reply is processed to determine it is valid and the server granted the request.</span></span> <span data-ttu-id="4b992-586">그런 다음, 필요에 따라 클라이언트 인스턴스가 서버 정보로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-586">The Client instance is then updated with the server information as needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-587">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-587">Input Parameters</span></span>

- <span data-ttu-id="4b992-588">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-588">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-589">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-589">Return Values</span></span>

- <span data-ttu-id="4b992-590">**NX_SUCCESS**(0x00) INFORM REQUEST 메시지가 성공적으로 생성 및 처리되었음</span><span class="sxs-lookup"><span data-stu-id="4b992-590">**NX_SUCCESS** (0x00) INFORM REQUEST message successfully created and processed</span></span>

- <span data-ttu-id="4b992-591">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-591">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-592">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-592">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-593">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-593">Allowed From</span></span>

<span data-ttu-id="4b992-594">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-595">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-595">Example</span></span>

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-596">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-596">See Also</span></span>

- <span data-ttu-id="4b992-597">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="4b992-597">nx_dhcpv6_request_confirm</span></span>

## <a name="nx_dhcpv6_request_option_dns_server"></a><span data-ttu-id="4b992-598">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="4b992-598">nx_dhcpv6_request_option_DNS_server</span></span>

<span data-ttu-id="4b992-599">DHCPv6 옵션 요청에 DNS 서버 추가</span><span class="sxs-lookup"><span data-stu-id="4b992-599">Add DNS Server to DHCPv6 Option request</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-600">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-600">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-601">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-601">Description</span></span>

<span data-ttu-id="4b992-602">이 서비스는 DHCPv6 옵션 요청에 DNS 서버 정보를 요청하기 위한 옵션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-602">This service adds the option for requesting DNS server information to the DHCPv6 option request.</span></span> <span data-ttu-id="4b992-603">서버 회신에 DNS 서버 데이터가 포함되는 경우 저장할 공간이 있으면 클라이언트에서 DNS 서버를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-603">If the Server reply includes DNS server data, the Client will store the DNS server if it has room to do so.</span></span> <span data-ttu-id="4b992-604">클라이언트가 저장할 수 있는 DNS 서버 수는 구성 가능한 옵션인 NX_DHCPV6_NUM_DNS_SERVERS에 의해 결정됩니다. 기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-604">The number of DNS servers the Client can store is determined by the configurable option NX_DHCPV6_NUM_DNS_SERVERS whose default value is 2.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-605">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-605">Input Parameters</span></span>

- <span data-ttu-id="4b992-606">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-606">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-607">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-607">Return Values</span></span>

- <span data-ttu-id="4b992-608">**NX_SUCCESS**(0x00) DNS 서버 옵션이 포함됨</span><span class="sxs-lookup"><span data-stu-id="4b992-608">**NX_SUCCESS** (0x00) DNS server option is included</span></span>

- <span data-ttu-id="4b992-609">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-609">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-610">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-610">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-611">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-611">Allowed From</span></span>

<span data-ttu-id="4b992-612">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-613">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-613">Example</span></span>

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="4b992-614">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-614">See Also</span></span>

- <span data-ttu-id="4b992-615">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="4b992-615">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="4b992-616">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="4b992-616">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="4b992-617">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="4b992-617">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_fqdn"></a><span data-ttu-id="4b992-618">nx_dhcpv6_request_option_FQDN</span><span class="sxs-lookup"><span data-stu-id="4b992-618">nx_dhcpv6_request_option_FQDN</span></span>

<span data-ttu-id="4b992-619">옵션 요청 목록에 정규화된 도메인 이름 옵션 추가</span><span class="sxs-lookup"><span data-stu-id="4b992-619">Add Fully Qualified Domain Name option to Option request list</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-620">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-620">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a><span data-ttu-id="4b992-621">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-621">Description</span></span>

<span data-ttu-id="4b992-622">이 서비스는 DHCPv6 옵션 요청에 클라이언트 정규화된 도메인 이름을 추가하기 위한 옵션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-622">This service adds the option for adding the Client Fully Qualified Domain Name to the DHCPv6 option request.</span></span> <span data-ttu-id="4b992-623">FQDN 옵션에는 다음과 같은 세 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-623">There are three options for the FQDN option:</span></span>

- <span data-ttu-id="4b992-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 클라이언트에서 사용하는 FQDN 및 주소에 대한 FQDN-IPv6 주소 매핑을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client.</span></span>

- <span data-ttu-id="4b992-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 클라이언트에서 서버에 사용하는 FQDN 및 주소에 대한 FQDN-IPv6 주소 매핑을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client to the server.</span></span>

- <span data-ttu-id="4b992-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 서버가 클라이언트를 대신하여 DNS 업데이트를 수행하지 않도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Request the server perform no DNS updates on the Client’s behalf.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-627">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-627">Input Parameters</span></span>

- <span data-ttu-id="4b992-628">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-628">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-629">**domain_name** 도메인 이름을 포함하는 문자열</span><span class="sxs-lookup"><span data-stu-id="4b992-629">**domain_name** String holding the domain name</span></span>

- <span data-ttu-id="4b992-630">**op** 적용할 FQDN 옵션 유형(위의 목록 참조)</span><span class="sxs-lookup"><span data-stu-id="4b992-630">**op** Type of FQDN option to apply (see list above)</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-631">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-631">Return Values</span></span>

- <span data-ttu-id="4b992-632">**NX_SUCCESS**(0x00) FQDN 옵션이 포함됨</span><span class="sxs-lookup"><span data-stu-id="4b992-632">**NX_SUCCESS** (0x00) FQDN option is included</span></span>

- <span data-ttu-id="4b992-633">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-633">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-634">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-634">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-635">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-635">Allowed From</span></span>

<span data-ttu-id="4b992-636">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-637">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-637">Example</span></span>

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a><span data-ttu-id="4b992-638">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-638">See Also</span></span>

- <span data-ttu-id="4b992-639">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="4b992-639">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="4b992-640">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="4b992-640">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="4b992-641">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="4b992-641">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_domain_name"></a><span data-ttu-id="4b992-642">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="4b992-642">nx_dhcpv6_request_option_domain_name</span></span>

<span data-ttu-id="4b992-643">DHCPv6 옵션 요청에 도메인 이름 옵션 추가</span><span class="sxs-lookup"><span data-stu-id="4b992-643">Add domain name option to DHCPv6 option request</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-644">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-644">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-645">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-645">Description</span></span>

<span data-ttu-id="4b992-646">이 서비스는 클라이언트 요청 메시지의 옵션 요청에 도메인 이름 옵션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-646">This service adds the domain name option to the option request in Client request messages.</span></span> <span data-ttu-id="4b992-647">서버 회신이 도메인 이름 데이터를 포함하는 경우 도메인 이름의 크기가 도메인 이름을 보유할 수 있는 버퍼 크기 내에 있으면 클라이언트에서 도메인 이름 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-647">If the Server reply includes domain name data, the Client will store the domain name information if the size of the domain name is within the buffer size for holding the domain name.</span></span> <span data-ttu-id="4b992-648">이 버퍼 크기는 구성 가능한 옵션(NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE)이며 기본 값은 30바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-648">This buffer size is a configurable option (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) with a default value of 30 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-649">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-649">Input Parameters</span></span>

- <span data-ttu-id="4b992-650">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-650">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-651">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-651">Return Values</span></span>

- <span data-ttu-id="4b992-652">**NX_SUCCESS**(0x00) 도메인 이름 옵션이 설정됨</span><span class="sxs-lookup"><span data-stu-id="4b992-652">**NX_SUCCESS** (0x00) Domain name option set</span></span>

- <span data-ttu-id="4b992-653">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-653">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-654">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-654">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-655">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-655">Allowed From</span></span>

<span data-ttu-id="4b992-656">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-657">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-657">Example</span></span>

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="4b992-658">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-658">See Also</span></span>

- <span data-ttu-id="4b992-659">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="4b992-659">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="4b992-660">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="4b992-660">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="4b992-661">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="4b992-661">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_time_server"></a><span data-ttu-id="4b992-662">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="4b992-662">nx_dhcpv6_request_option_time_server</span></span>

<span data-ttu-id="4b992-663">시간 서버 데이터를 선택적 요청으로 설정</span><span class="sxs-lookup"><span data-stu-id="4b992-663">Set time server data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-664">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-664">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-665">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-665">Description</span></span>

<span data-ttu-id="4b992-666">이 서비스는 클라이언트 요청 메시지의 옵션 요청에 시간 서버 정보에 대한 옵션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-666">This service adds the option for time server information to the option request of Client request messages.</span></span> <span data-ttu-id="4b992-667">서버 응답이 시간 서버 데이터를 포함하는 경우 클라이언트가 시간 서버를 저장할 공간이 있는 경우 시간 서버를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-667">If the Server reply includes tim server data, the Client will store the time server if it has room to do so.</span></span> <span data-ttu-id="4b992-668">클라이언트가 저장할 수 있는 시간 서버 수는 구성 가능한 옵션에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-668">The number of time servers the Client can store is determined by the configurable option</span></span>

<span data-ttu-id="4b992-669">이 옵션은 NX_DHCPV6_NUM_TIME _SERVERS이며 기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-669">NX_DHCPV6_NUM_TIME _SERVERS whose default value is 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-670">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-670">Input Parameters</span></span>

- <span data-ttu-id="4b992-671">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-671">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-672">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-672">Return Values</span></span>

- <span data-ttu-id="4b992-673">**NX_SUCCESS**(0x00) 시간 서버 옵션이 추가됨</span><span class="sxs-lookup"><span data-stu-id="4b992-673">**NX_SUCCESS** (0x00) Time server option added</span></span>

- <span data-ttu-id="4b992-674">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-674">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-675">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-675">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-676">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-676">Allowed From</span></span>

<span data-ttu-id="4b992-677">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-677">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-678">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-678">Example</span></span>

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="4b992-679">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-679">See Also</span></span>

- <span data-ttu-id="4b992-680">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="4b992-680">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="4b992-681">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="4b992-681">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="4b992-682">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="4b992-682">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_timezone"></a><span data-ttu-id="4b992-683">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="4b992-683">nx_dhcpv6_request_option_timezone</span></span>

<span data-ttu-id="4b992-684">표준 시간대 데이터를 선택적 요청으로 설정</span><span class="sxs-lookup"><span data-stu-id="4b992-684">Set time zone data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-685">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-685">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-686">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-686">Description</span></span>

<span data-ttu-id="4b992-687">이 서비스는 클라이언트 옵션 요청에 표준 시간대 정보를 요청하는 옵션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-687">This service adds the option for requesting time zone information to the Client option request.</span></span> <span data-ttu-id="4b992-688">서버 회신에 표준 시간대 데이터가 포함된 경우 표준 시간대의 크기가 표준 시간대를 보유할 수 있는 버퍼 크기 내에 있으면 클라이언트가 표준 시간대 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-688">If the Server reply includes time zone data, the Client will store the time zone information if the size of the time zone is within the buffer size for holding the time zone.</span></span> <span data-ttu-id="4b992-689">이 버퍼 크기는 구성 가능한 옵션(NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE)이며 기본값은 10 바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-689">This buffer size is a configurable option (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) with a default value of 10 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-690">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-690">Input Parameters</span></span>

- <span data-ttu-id="4b992-691">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-691">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-692">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-692">Return Values</span></span>

- <span data-ttu-id="4b992-693">**NX_SUCCESS**(0x00) 표준 시간대 옵션이 추가됨</span><span class="sxs-lookup"><span data-stu-id="4b992-693">**NX_SUCCESS** (0x00) Time zone option added</span></span>

- <span data-ttu-id="4b992-694">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-694">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-695">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-695">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-696">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-696">Allowed From</span></span>

<span data-ttu-id="4b992-697">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-698">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-698">Example</span></span>

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="4b992-699">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-699">See Also</span></span>

- <span data-ttu-id="4b992-700">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="4b992-700">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="4b992-701">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="4b992-701">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="4b992-702">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="4b992-702">nx_dhcpv6_request_option_time_server</span></span>

## <a name="nx_dhcpv6_request_release"></a><span data-ttu-id="4b992-703">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="4b992-703">nx_dhcpv6_request_release</span></span>

<span data-ttu-id="4b992-704">DHCPv6 RELEASE 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="4b992-704">Send a DHCPv6 RELEASE message</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-705">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-705">Prototype</span></span>

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-706">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-706">Description</span></span>

<span data-ttu-id="4b992-707">이 서비스는 클라이언트 네트워크에서 RELEASE 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-707">This service sends a RELEASE message on the Client network.</span></span> <span data-ttu-id="4b992-708">메시지가 성공적으로 전송되면 성공적인 상태가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-708">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="4b992-709">성공적인 완료가 클라이언트에서 응답을 수신했거나 IPv6 주소를 부여했음을 의미하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-709">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="4b992-710">DHCPv6 클라이언트 스레드 작업은 DHCPv6 서버의 응답을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-710">The DHCPv6 Client thread task waits for a reply from a DHCPv6 Server.</span></span> <span data-ttu-id="4b992-711">회신을 받으면 회신이 유효한지 확인하고 데이터를 클라이언트 레코드에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-711">If one is received, it checks the reply is valid and stores the data to the Client record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-712">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-712">Input Parameters</span></span>

- <span data-ttu-id="4b992-713">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-713">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-714">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-714">Return Values</span></span>

- <span data-ttu-id="4b992-715">**NX_SUCCESS**(0x00) RELEASE 메시지가 성공적으로 전송됨</span><span class="sxs-lookup"><span data-stu-id="4b992-715">**NX_SUCCESS** (0x00) RELEASE message successfully sent</span></span>

- <span data-ttu-id="4b992-716">**NX_DHCPV6_NOT_STARTED**(0xE92) DHCPv6 클라이언트 작업이 시작되지 않음</span><span class="sxs-lookup"><span data-stu-id="4b992-716">**NX_DHCPV6_NOT_STARTED** (0xE92) DHCPv6 Client task not started</span></span>

- <span data-ttu-id="4b992-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID**(0xEAD) 클라이언트에 바인딩되지 않은 주소</span><span class="sxs-lookup"><span data-stu-id="4b992-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Address not bound to Client</span></span>

- <span data-ttu-id="4b992-718">**NX_INVALID_INTERFACE**(0x4C) IP 주소 테이블에서 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="4b992-718">**NX_INVALID_INTERFACE** (0x4C) Not found in IP address table</span></span>

- <span data-ttu-id="4b992-719">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-719">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-720">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-720">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-721">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-721">Allowed From</span></span>

<span data-ttu-id="4b992-722">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-722">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-723">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-723">Example</span></span>

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-724">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-724">See Also</span></span>

- <span data-ttu-id="4b992-725">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="4b992-725">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="4b992-726">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="4b992-726">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="4b992-727">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="4b992-727">nx_dhcpv6_request_solicit</span></span>

## <a name="nx_dhcpv6_request_solicit"></a><span data-ttu-id="4b992-728">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="4b992-728">nx_dhcpv6_request_solicit</span></span>

<span data-ttu-id="4b992-729">SOLICIT 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="4b992-729">Send a SOLICIT message</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-730">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-730">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-731">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-731">Description</span></span>

<span data-ttu-id="4b992-732">이 서비스는 네트워크에서 SOLICIT 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-732">This service sends a SOLICIT message out on the network.</span></span> <span data-ttu-id="4b992-733">메시지가 성공적으로 전송되면 성공적인 상태가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-733">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="4b992-734">성공적인 완료가 클라이언트에서 응답을 수신했거나 IPv6 주소를 부여했음을 의미하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-734">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="4b992-735">DHCPv6 클라이언트 스레드 작업은 DHCPv6 서버의 회신(ADVERTISE 메시지)을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-735">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="4b992-736">회신을 받으면 회신이 유효한지 확인하고, 데이터를 클라이언트 레코드에 저장하며, 클라이언트를 REQUEST 상태로 승격합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-736">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the REQUEST state.</span></span>

> [!NOTE] 
> <span data-ttu-id="4b992-737">빠른 커밋 옵션이 설정된 경우 올바른 서버 ADVERTISE 메시지를 수신하면 DHCPv6 클라이언트가 바인딩된 상태로 바로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-737">If the Rapid Commit option is set, the DHCPv6 Client will go directly to the Bound state if it receives a valid Server ADVERTISE message.</span></span> <span data-ttu-id="4b992-738">자세한 내용은 *nx_dhcpv6_request_solicit_rapid* 에 대한 서비스 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b992-738">See the service description for *nx_dhcpv6_request_solicit_rapid* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-739">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-739">Input Parameters</span></span>

- <span data-ttu-id="4b992-740">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-740">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-741">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-741">Return Values</span></span>

- <span data-ttu-id="4b992-742">**NX_SUCCESS**(0x00) SOLICIT 메시지가 전송됨</span><span class="sxs-lookup"><span data-stu-id="4b992-742">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="4b992-743">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-743">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-744">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-744">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-745">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-745">Allowed From</span></span>

<span data-ttu-id="4b992-746">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-746">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-747">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-747">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a><span data-ttu-id="4b992-748">nx_dhcpv6_request_solicit_rapid</span><span class="sxs-lookup"><span data-stu-id="4b992-748">nx_dhcpv6_request_solicit_rapid</span></span>

<span data-ttu-id="4b992-749">빠른 커밋 옵션을 사용하여 SOLICIT 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="4b992-749">Send a SOLICIT message with the Rapid Commit option</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-750">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-750">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-751">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-751">Description</span></span>

<span data-ttu-id="4b992-752">이 서비스는 빠른 커밋 옵션을 설정하여 네트워크에서 SOLICIT 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-752">This service sends a SOLICIT message out on the network with the Rapid Commit option set.</span></span> <span data-ttu-id="4b992-753">메시지가 성공적으로 전송되면 성공적인 상태가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-753">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="4b992-754">성공적인 완료가 클라이언트에서 응답을 수신했거나 IPv6 주소를 부여했음을 의미하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-754">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="4b992-755">DHCPv6 클라이언트 스레드 작업은 DHCPv6 서버의 회신(ADVERTISE 메시지)을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-755">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="4b992-756">회신을 받으면 회신이 유효한지 확인하고, 데이터를 클라이언트 레코드에 저장하며, 클라이언트를 BOUND 상태로 승격합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-756">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the BOUND state.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-757">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-757">Input Parameters</span></span>

- <span data-ttu-id="4b992-758">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-758">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-759">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-759">Return Values</span></span>

- <span data-ttu-id="4b992-760">**NX_SUCCESS**(0x00) SOLICIT 메시지가 전송됨</span><span class="sxs-lookup"><span data-stu-id="4b992-760">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="4b992-761">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-761">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-762">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-762">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-763">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-763">Allowed From</span></span>

<span data-ttu-id="4b992-764">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-765">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-765">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-766">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-766">See Also</span></span>

- <span data-ttu-id="4b992-767">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="4b992-767">nx_dhcpv6_request_solicit</span></span>
- <span data-ttu-id="4b992-768">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="4b992-768">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="4b992-769">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="4b992-769">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="4b992-770">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="4b992-770">nx_dhcpv6_request_release</span></span>

## <a name="nx_dhcpv6_resume"></a><span data-ttu-id="4b992-771">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="4b992-771">nx_dhcpv6_resume</span></span>

<span data-ttu-id="4b992-772">DHCPv6 클라이언트 작업 다시 시작</span><span class="sxs-lookup"><span data-stu-id="4b992-772">Resume DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="4b992-773">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-773">Prototype</span></span>

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-774">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-774">Description</span></span>

<span data-ttu-id="4b992-775">이 서비스는 DHCPv6 클라이언트 스레드 작업을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-775">This service resumes the DHCPv6 Client thread task.</span></span> <span data-ttu-id="4b992-776">현재 DHCPv6 클라이언트 상태(예: Bound Solicit)가 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-776">The current DHCPv6 Client state will be processed (e.g. Bound, Solicit)</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-777">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-777">Input Parameters</span></span>

- <span data-ttu-id="4b992-778">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-778">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-779">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-779">Return Values</span></span>

- <span data-ttu-id="4b992-780">**NX_SUCCESS**(0x00) 클라이언트가 성공적으로 다시 시작됨</span><span class="sxs-lookup"><span data-stu-id="4b992-780">**NX_SUCCESS** (0x00) Client successfully resumed</span></span>

- <span data-ttu-id="4b992-781">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-781">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-782">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-782">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-783">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-783">Allowed From</span></span>

<span data-ttu-id="4b992-784">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-784">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-785">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-785">Example</span></span>

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-786">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-786">See Also</span></span>

- <span data-ttu-id="4b992-787">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="4b992-787">nx_dhcpv6_start</span></span>
- <span data-ttu-id="4b992-788">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="4b992-788">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="4b992-789">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="4b992-789">nx_dhcpv6_suspend</span></span>

## <a name="nx_dhcpv6_set_-time_accrued"></a><span data-ttu-id="4b992-790">nx_dhcpv6_set_ time_accrued</span><span class="sxs-lookup"><span data-stu-id="4b992-790">nx_dhcpv6_set_ time_accrued</span></span>

<span data-ttu-id="4b992-791">클라이언트의 IP 주소 임대에 대한 누적 시간 설정</span><span class="sxs-lookup"><span data-stu-id="4b992-791">Sets time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="4b992-792">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-792">Prototype</span></span>

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a><span data-ttu-id="4b992-793">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-793">Description</span></span>

<span data-ttu-id="4b992-794">이 서비스는 서버에서 할당된 이후 클라이언트의 전역 IP 주소에 대한 누적 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-794">This service sets the time accrued on the Client’s global IP address since it was assigned by the server.</span></span> <span data-ttu-id="4b992-795">클라이언트가 현재 할당된 IPv6 주소에 바인딩되어 있는 경우에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-795">This should only be used if a Client is currently bound to an assigned IPv6 address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-796">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-796">Input Parameters</span></span>

- <span data-ttu-id="4b992-797">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-797">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="4b992-798">**time_accrued** IP 임대의 시간 누적</span><span class="sxs-lookup"><span data-stu-id="4b992-798">**time_accrued** Time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-799">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-799">Return Values</span></span>

- <span data-ttu-id="4b992-800">**NX_SUCCESS**(0x00) 시간 누적이 성공적으로 설정됨</span><span class="sxs-lookup"><span data-stu-id="4b992-800">**NX_SUCCESS** (0x00) Time accrued successfully set</span></span>

- <span data-ttu-id="4b992-801">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-801">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-802">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-802">Allowed From</span></span>

<span data-ttu-id="4b992-803">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-804">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-804">Example</span></span>

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-805">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-805">See Also</span></span>

- <span data-ttu-id="4b992-806">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="4b992-806">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="4b992-807">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="4b992-807">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="4b992-808">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="4b992-808">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="4b992-809">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="4b992-809">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_start"></a><span data-ttu-id="4b992-810">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="4b992-810">nx_dhcpv6_start</span></span>

<span data-ttu-id="4b992-811">DHCPv6 클라이언트 작업 시작</span><span class="sxs-lookup"><span data-stu-id="4b992-811">Start the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="4b992-812">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-812">Prototype</span></span>

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-813">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-813">Description</span></span>

<span data-ttu-id="4b992-814">이 서비스는 DHCPv6 클라이언트 작업을 시작하고 DHCPv6 프로토콜 실행을 위해 클라이언트를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-814">This service starts the DHCPv6 Client task and prepares the Client for running the DHCPv6 protocol.</span></span> <span data-ttu-id="4b992-815">클라이언트 인스턴스에 충분한 정보(예: 클라이언트 DUID)가 있는지 확인하고, DHCPv6 메시지를 보내고 받기 위한 UDP 소켓을 만들고 바인딩하며, 세션 시간을 추적하고 현재 IPv6 임대가 만료되는 시간을 추적하는 타이머를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-815">It verifies the Client instance has sufficient information (such as a Client DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages and activates timers for keeping track of session time and when the current IPv6 lease expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-816">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-816">Input Parameters</span></span>

- <span data-ttu-id="4b992-817">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-817">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-818">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-818">Return Values</span></span>

- <span data-ttu-id="4b992-819">**NX_SUCCESS**(0x00) 클라이언트가 성공적으로 시작됨</span><span class="sxs-lookup"><span data-stu-id="4b992-819">**NX_SUCCESS** (0x00) Client successfully started</span></span>

- <span data-ttu-id="4b992-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS**(0xEA9) 클라이언트에 필수 옵션이 없음</span><span class="sxs-lookup"><span data-stu-id="4b992-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Client missing required options</span></span>

- <span data-ttu-id="4b992-821">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-821">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-822">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-822">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-823">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-823">Allowed From</span></span>

<span data-ttu-id="4b992-824">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-824">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-825">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-825">Example</span></span>

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-826">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-826">See Also</span></span>

- <span data-ttu-id="4b992-827">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="4b992-827">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="4b992-828">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="4b992-828">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="4b992-829">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="4b992-829">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="4b992-830">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="4b992-830">nx_dhcpv6_reinitialize</span></span>

## <a name="nx_dhcpv6_stop"></a><span data-ttu-id="4b992-831">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="4b992-831">nx_dhcpv6_stop</span></span>

<span data-ttu-id="4b992-832">DHCPv6 클라이언트 작업 중지</span><span class="sxs-lookup"><span data-stu-id="4b992-832">Stop the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="4b992-833">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-833">Prototype</span></span>

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-834">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-834">Description</span></span>

<span data-ttu-id="4b992-835">이 서비스는 DHCPv6 클라이언트 작업을 중지하고 재전송 횟수와 최대 재전송 간격을 지우고 세션 및 임대 만료 타이머를 비활성화하고 DHCPv6 클라이언트 소켓 포트를 바인딩 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-835">This service stops the DHCPv6 Client task, and clears retransmission counts, maximum retransmission intervals, deactivates the session and lease expiration timers, and unbinds the DHCPv6 Client socket port.</span></span> <span data-ttu-id="4b992-836">클라이언트를 다시 시작하려면 먼저 DHCPv6 서버를 사용하여 다른 세션을 시작하기 전에 클라이언트를 중지하고 필요에 따라 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-836">To restart the Client, one must first stop and optionally reinitialize the Client before starting another session with any DHCPv6 server.</span></span> <span data-ttu-id="4b992-837">자세한 내용은 간단한 예제 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b992-837">See the Small Example section for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-838">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-838">Input Parameters</span></span>

- <span data-ttu-id="4b992-839">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-839">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-840">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-840">Return Values</span></span>

- <span data-ttu-id="4b992-841">**NX_SUCCESS**(0x00) 클라이언트가 성공적으로 중지됨</span><span class="sxs-lookup"><span data-stu-id="4b992-841">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>

- <span data-ttu-id="4b992-842">**NX_DHCPV6_NOT_STARTED**(0xE92) 클라이언트 스레드가 시작되지 않음</span><span class="sxs-lookup"><span data-stu-id="4b992-842">**NX_DHCPV6_NOT_STARTED** (0xE92) Client thread not started</span></span>

- <span data-ttu-id="4b992-843">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-843">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-844">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-844">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>


### <a name="allowed-from"></a><span data-ttu-id="4b992-845">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-845">Allowed From</span></span>

<span data-ttu-id="4b992-846">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-847">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-847">Example</span></span>

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-848">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-848">See Also</span></span>

- <span data-ttu-id="4b992-849">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="4b992-849">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="4b992-850">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="4b992-850">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="4b992-851">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="4b992-851">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="4b992-852">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="4b992-852">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_suspend"></a><span data-ttu-id="4b992-853">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="4b992-853">nx_dhcpv6_suspend</span></span>

<span data-ttu-id="4b992-854">DHCPv6 클라이언트 작업 일시 중단</span><span class="sxs-lookup"><span data-stu-id="4b992-854">Suspend the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="4b992-855">프로토타입</span><span class="sxs-lookup"><span data-stu-id="4b992-855">Prototype</span></span>

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="4b992-856">Description</span><span class="sxs-lookup"><span data-stu-id="4b992-856">Description</span></span>

<span data-ttu-id="4b992-857">이 서비스는 DHCPv6 클라이언트 작업 및 처리 중이었던 요청을 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-857">This service suspends the DHCPv6 client task and any request it was in the middle of processing.</span></span> <span data-ttu-id="4b992-858">타이머가 비활성화되고 클라이언트 상태가 실행 중이 아닌 것으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b992-858">Timers are deactivated and the Client state is set to non-running.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4b992-859">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4b992-859">Input Parameters</span></span>

- <span data-ttu-id="4b992-860">**dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="4b992-860">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="4b992-861">반환 값</span><span class="sxs-lookup"><span data-stu-id="4b992-861">Return Values</span></span>

- <span data-ttu-id="4b992-862">**NX_SUCCESS**(0x00) 클라이언트가 성공적으로 일시 중단됨</span><span class="sxs-lookup"><span data-stu-id="4b992-862">**NX_SUCCESS** (0x00) Client successfully suspended</span></span>

- <span data-ttu-id="4b992-863">**NX_DHCPV6_NOT_STARTED**(0xE92) 클라이언트가 실행되고 있지 않으므로 일시 중단할 수 없음</span><span class="sxs-lookup"><span data-stu-id="4b992-863">**NX_DHCPV6_NOT_STARTED** (0XE92) Client not running so cannot be suspended</span></span>

- <span data-ttu-id="4b992-864">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="4b992-864">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="4b992-865">NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함</span><span class="sxs-lookup"><span data-stu-id="4b992-865">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4b992-866">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="4b992-866">Allowed From</span></span>

<span data-ttu-id="4b992-867">스레드</span><span class="sxs-lookup"><span data-stu-id="4b992-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="4b992-868">예제</span><span class="sxs-lookup"><span data-stu-id="4b992-868">Example</span></span>

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a><span data-ttu-id="4b992-869">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b992-869">See Also</span></span>

- <span data-ttu-id="4b992-870">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="4b992-870">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="4b992-871">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="4b992-871">nx_dhcpv6_start</span></span>
- <span data-ttu-id="4b992-872">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="4b992-872">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="4b992-873">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="4b992-873">nx_dhcpv6_stop</span></span>
