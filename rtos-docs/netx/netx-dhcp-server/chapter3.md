---
title: 3장 - Azure RTOS NetX DHCP 서버 서비스 설명
description: 이 장에는 모든 Azure RTOS NetX DHCP 서버 서비스 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d24c69cf6b8c2bb84b7155e49a54e8296ee662f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811599"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a><span data-ttu-id="dfc59-103">3장 - Azure RTOS NetX DHCP 서버 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="dfc59-103">Chapter 3 - Description of Azure RTOS NetX DHCP Server services</span></span>

<span data-ttu-id="dfc59-104">이 장에는 모든 NetX DHCP 서버 서비스 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-104">This chapter contains a description of all NetX DHCP Server services.</span></span>

<span data-ttu-id="dfc59-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="dfc59-106">**nx_dhcp_server_create**: *DHCP 서버 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="dfc59-106">**nx_dhcp_server_create**: *Create a DHCP Server instance*</span></span>
- <span data-ttu-id="dfc59-107">**nx_dhcp_set_interface_network_parameters**: *지정된 인터페이스의 중요한 네트워크 매개 변수에 대한 DHCP 서버 옵션 설정*</span><span class="sxs-lookup"><span data-stu-id="dfc59-107">**nx_dhcp_set_interface_network_parameters**: *Set DHCP Server options for critical network parameters for specified interface*</span></span>
- <span data-ttu-id="dfc59-108">**nx_dhcp_create_server_ip_address_list**: *DHCP 클라이언트 인터페이스에 할당할 사용 가능한 IP 주소 풀 만들기*</span><span class="sxs-lookup"><span data-stu-id="dfc59-108">**nx_dhcp_create_server_ip_address_list**: *Create pool of available IP addresses to assign to DHCP Clients interface*</span></span>
- <span data-ttu-id="dfc59-109">**nx_dhcp_clear_client_record**: *서버 데이터베이스에서 클라이언트 레코드 제거*</span><span class="sxs-lookup"><span data-stu-id="dfc59-109">**nx_dhcp_clear_client_record**: *Remove Client record in the Server database*</span></span>
- <span data-ttu-id="dfc59-110">**nx_dhcp_server_delete**: *DHCP 서버 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="dfc59-110">**nx_dhcp_server_delete**: *Delete a DHCPServer instance*</span></span>
- <span data-ttu-id="dfc59-111">**nx_dhcp_server_start**: *DHCP 서버 처리 시작 또는 다시 시작*</span><span class="sxs-lookup"><span data-stu-id="dfc59-111">**nx_dhcp_server_start**: *Start or resume DHCP Server processing*</span></span>
- <span data-ttu-id="dfc59-112">**nx_dhcp_server_stop**: *DHCP 서버 처리 중지*</span><span class="sxs-lookup"><span data-stu-id="dfc59-112">**nx_dhcp_server_stop**: *Stop DHCP server processing*</span></span>

## <a name="nx_dhcp_server_create"></a><span data-ttu-id="dfc59-113">nx_dhcp_server_create</span><span class="sxs-lookup"><span data-stu-id="dfc59-113">nx_dhcp_server_create</span></span>

<span data-ttu-id="dfc59-114">DHCP 서버 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="dfc59-114">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="dfc59-115">프로토타입</span><span class="sxs-lookup"><span data-stu-id="dfc59-115">Prototype</span></span>

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="dfc59-116">Description</span><span class="sxs-lookup"><span data-stu-id="dfc59-116">Description</span></span>

<span data-ttu-id="dfc59-117">이 서비스는 이전에 만든 IP 인스턴스로 DHCP 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-117">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dfc59-118">애플리케이션은 IP 만들기 서비스에 대해 생성된 패킷 풀에 UDP, IP 및 이더넷 헤더를 포함하지 않고 최소 548바이트 페이로드가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-118">The application must make sure the packet pool created for the IP create service has a minimum548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dfc59-119">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="dfc59-119">Input Parameters</span></span>

- <span data-ttu-id="dfc59-120">**dhcp_ptr**: DHCP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-120">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="dfc59-121">**ip_ptr**: DHCP 서버 IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-121">**ip_ptr**: Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="dfc59-122">**stack_ptr**: 포인터 DHCP 서버 스택 위치</span><span class="sxs-lookup"><span data-stu-id="dfc59-122">**stack_ptr**: Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="dfc59-123">**stack_size**: DHCP 서버 스택 크기</span><span class="sxs-lookup"><span data-stu-id="dfc59-123">**stack_size**: Size of DHCP Server stack</span></span>
- <span data-ttu-id="dfc59-124">**input_address_list**: 서버의 IP 주소 목록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-124">**input_address_list**: Pointer to Server's list of IP addresses</span></span>
- <span data-ttu-id="dfc59-125">**name_ptr**: DHCP 서버 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-125">**name_ptr**: Pointer to DHCP Server name</span></span>
- <span data-ttu-id="dfc59-126">**packet_pool_ptr**: DHCP 서버 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-126">**packet_pool_ptr**: Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="dfc59-127">반환 값</span><span class="sxs-lookup"><span data-stu-id="dfc59-127">Return Values</span></span>

- <span data-ttu-id="dfc59-128">**NX_SUCCESS**: (0x00) DHCP 서버를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-128">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="dfc59-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) 패킷 페이로드가 너무 작음 오류</span><span class="sxs-lookup"><span data-stu-id="dfc59-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="dfc59-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) 서버 옵션 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="dfc59-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) Server option list is empty</span></span>
- <span data-ttu-id="dfc59-131">NX_DHCP_PARAMETER_ERROR: (0x92) 잘못된 포인터가 아닌 입력</span><span class="sxs-lookup"><span data-stu-id="dfc59-131">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="dfc59-132">NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="dfc59-132">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="dfc59-133">NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-133">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dfc59-134">허용 위치</span><span class="sxs-lookup"><span data-stu-id="dfc59-134">Allowed From</span></span>

<span data-ttu-id="dfc59-135">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="dfc59-135">Application</span></span>

### <a name="example"></a><span data-ttu-id="dfc59-136">예제</span><span class="sxs-lookup"><span data-stu-id="dfc59-136">Example</span></span>

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="dfc59-137">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="dfc59-137">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="dfc59-138">IP 주소 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="dfc59-138">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="dfc59-139">프로토타입</span><span class="sxs-lookup"><span data-stu-id="dfc59-139">Prototype</span></span>

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="dfc59-140">Description</span><span class="sxs-lookup"><span data-stu-id="dfc59-140">Description</span></span>

<span data-ttu-id="dfc59-141">이 서비스는 할당할 지정된 DHCP 서버에 사용할 수 있는 IP 주소의 네트워크 인터페이스 특정 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-141">This service creates a networkinterface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="dfc59-142">시작 IP 주소와 끝 IP 주소는 지정된 네트워크 인터페이스와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-142">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="dfc59-143">IP 주소 목록의 크기가 충분히 크지 않은 경우(사용자 구성 가능 *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* 매개 변수에 설정됨) 추가된 실제 IP 주소 수가 총 주소 수보다 적을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-143">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dfc59-144">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="dfc59-144">Input Parameters</span></span>

- <span data-ttu-id="dfc59-145">**dhcp_ptr** DHCP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-145">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="dfc59-146">**iface_index**: 네트워크 인터페이스에 해당하는 인덱스</span><span class="sxs-lookup"><span data-stu-id="dfc59-146">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="dfc59-147">**start_ip_address**: 사용 가능한 첫 번째 IP 주소</span><span class="sxs-lookup"><span data-stu-id="dfc59-147">**start_ip_address**: First available IP address</span></span>
- <span data-ttu-id="dfc59-148">**end_ip_address**: 사용 가능한 마지막 IP 주소</span><span class="sxs-lookup"><span data-stu-id="dfc59-148">**end_ip_address**: Last of the available IP address</span></span>
- <span data-ttu-id="dfc59-149">**addresses_added**: 목록에 추가된 IP 주소 수</span><span class="sxs-lookup"><span data-stu-id="dfc59-149">**addresses_added**: Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="dfc59-150">반환 값</span><span class="sxs-lookup"><span data-stu-id="dfc59-150">Return Values</span></span>

- <span data-ttu-id="dfc59-151">**NX_SUCCESS**: (0x00) DHCP 서버를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-151">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="dfc59-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) 인덱스가 주소와 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="dfc59-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="dfc59-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) 잘못된 주소 입력</span><span class="sxs-lookup"><span data-stu-id="dfc59-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) Invalid address input</span></span>
- <span data-ttu-id="dfc59-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) 비논리적 시작/종료 주소</span><span class="sxs-lookup"><span data-stu-id="dfc59-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="dfc59-155">NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-155">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dfc59-156">허용 위치</span><span class="sxs-lookup"><span data-stu-id="dfc59-156">Allowed From</span></span>

<span data-ttu-id="dfc59-157">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="dfc59-157">Application</span></span>

### <a name="example"></a><span data-ttu-id="dfc59-158">예제</span><span class="sxs-lookup"><span data-stu-id="dfc59-158">Example</span></span>

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="dfc59-159">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="dfc59-159">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="dfc59-160">서버 데이터베이스에서 클라이언트 레코드 제거</span><span class="sxs-lookup"><span data-stu-id="dfc59-160">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="dfc59-161">프로토타입</span><span class="sxs-lookup"><span data-stu-id="dfc59-161">Prototype</span></span>

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="dfc59-162">Description</span><span class="sxs-lookup"><span data-stu-id="dfc59-162">Description</span></span>

<span data-ttu-id="dfc59-163">이 서비스는 서버 데이터베이스에서 클라이언트 레코드를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-163">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dfc59-164">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="dfc59-164">Input Parameters</span></span>

- <span data-ttu-id="dfc59-165">**dhcp_ptr**: DHCP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-165">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="dfc59-166">**dhcp_client_ptr**: 제거할 DHCP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-166">**dhcp_client_ptr**: Pointer to DHCP Client to remove</span></span>

### <a name="return-values"></a><span data-ttu-id="dfc59-167">반환 값</span><span class="sxs-lookup"><span data-stu-id="dfc59-167">Return Values</span></span>

- <span data-ttu-id="dfc59-168">**NX_SUCCESS**: (0x00) DHCP 서버를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-168">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="dfc59-169">NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-169">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="dfc59-170">NX_CALLER_ERROR: (0x11) 스레드가 아닌 서비스의 호출자</span><span class="sxs-lookup"><span data-stu-id="dfc59-170">NX_CALLER_ERROR: (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dfc59-171">허용 위치</span><span class="sxs-lookup"><span data-stu-id="dfc59-171">Allowed From</span></span>

<span data-ttu-id="dfc59-172">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="dfc59-172">Application</span></span>

### <a name="example"></a><span data-ttu-id="dfc59-173">예제</span><span class="sxs-lookup"><span data-stu-id="dfc59-173">Example</span></span>

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="dfc59-174">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="dfc59-174">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="dfc59-175">DHCP 옵션에 대한 네트워크 매개 변수 설정</span><span class="sxs-lookup"><span data-stu-id="dfc59-175">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="dfc59-176">프로토타입</span><span class="sxs-lookup"><span data-stu-id="dfc59-176">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="dfc59-177">Description</span><span class="sxs-lookup"><span data-stu-id="dfc59-177">Description</span></span>

<span data-ttu-id="dfc59-178">이 서비스는 지정된 인터페이스의 네트워크 중요 매개 변수에 대한 기본값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-178">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="dfc59-179">DHCP 서버는 DHCP 클라이언트에 대한 OFFER 및 ACK 회신에 이러한 옵션을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-179">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="dfc59-180">호스트가 실행 중인 DHCP 서버에 인터페이스 매개 변수를 설정하는 경우 매개 변수는 DHCP 서버 자체에 대한 기본 인터페이스 게이트웨이로 설정된 라우터, DHCP 서버 자체에 대한 DNS 서버 주소 및 DHCP 서버 인터페이스와 동일하게 구성된 서브넷 마스크와 같이 기본값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-180">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dfc59-181">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="dfc59-181">Input Parameters</span></span>

- <span data-ttu-id="dfc59-182">**dhcp_ptr**: DHCP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-182">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="dfc59-183">**iface_index**: 네트워크 인터페이스에 해당하는 인덱스</span><span class="sxs-lookup"><span data-stu-id="dfc59-183">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="dfc59-184">**subnet_mask**: 클라이언트 네트워크에 대한 서브넷 마스크</span><span class="sxs-lookup"><span data-stu-id="dfc59-184">**subnet_mask**: Subnet mask for Client network</span></span>
- <span data-ttu-id="dfc59-185">**default_gateway_address**: 클라이언트의 라우터 IP 주소</span><span class="sxs-lookup"><span data-stu-id="dfc59-185">**default_gateway_address**: Client's router IP address</span></span>
- <span data-ttu-id="dfc59-186">**dns_server_address**: 클라이언트 네트워크에 대한 DNS 서버</span><span class="sxs-lookup"><span data-stu-id="dfc59-186">**dns_server_address**: DNS server for Client's network</span></span>

### <a name="return-values"></a><span data-ttu-id="dfc59-187">반환 값</span><span class="sxs-lookup"><span data-stu-id="dfc59-187">Return Values</span></span>

- <span data-ttu-id="dfc59-188">**NX_SUCCESS**: (0x00) DHCP 서버를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-188">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="dfc59-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) 인덱스가 주소와 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="dfc59-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="dfc59-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) 잘못된 네트워크 매개 변수</span><span class="sxs-lookup"><span data-stu-id="dfc59-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="dfc59-191">NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-191">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dfc59-192">허용 위치</span><span class="sxs-lookup"><span data-stu-id="dfc59-192">Allowed From</span></span>

<span data-ttu-id="dfc59-193">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="dfc59-193">Application</span></span>

### <a name="example"></a><span data-ttu-id="dfc59-194">예제</span><span class="sxs-lookup"><span data-stu-id="dfc59-194">Example</span></span>

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="dfc59-195">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="dfc59-195">nx_dhcp_server_delete</span></span>

<span data-ttu-id="dfc59-196">DHCP 서버 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="dfc59-196">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="dfc59-197">프로토타입</span><span class="sxs-lookup"><span data-stu-id="dfc59-197">Prototype</span></span>

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="dfc59-198">Description</span><span class="sxs-lookup"><span data-stu-id="dfc59-198">Description</span></span>

<span data-ttu-id="dfc59-199">이 서비스는 이전에 만든 DHCP 서버 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-199">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dfc59-200">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="dfc59-200">Input Parameters</span></span>

- <span data-ttu-id="dfc59-201">**dhcp_ptr**: DHCP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-201">**dhcp_ptr**: Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="dfc59-202">반환 값</span><span class="sxs-lookup"><span data-stu-id="dfc59-202">Return Values</span></span>

- <span data-ttu-id="dfc59-203">**NX_SUCCESS**: (0x00) DHCP 서버를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="dfc59-203">**NX_SUCCESS**: (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="dfc59-204">NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-204">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="dfc59-205">NX_DHCP_PARAMETER_ERROR: (0x92) 잘못된 포인터가 아닌 입력</span><span class="sxs-lookup"><span data-stu-id="dfc59-205">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="dfc59-206">NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="dfc59-206">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dfc59-207">허용 위치</span><span class="sxs-lookup"><span data-stu-id="dfc59-207">Allowed From</span></span>

<span data-ttu-id="dfc59-208">스레드</span><span class="sxs-lookup"><span data-stu-id="dfc59-208">Threads</span></span>

### <a name="example"></a><span data-ttu-id="dfc59-209">예제</span><span class="sxs-lookup"><span data-stu-id="dfc59-209">Example</span></span>

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="dfc59-210">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="dfc59-210">nx_dhcp_server_start</span></span>

<span data-ttu-id="dfc59-211">DHCP 서버 처리 시작</span><span class="sxs-lookup"><span data-stu-id="dfc59-211">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="dfc59-212">프로토타입</span><span class="sxs-lookup"><span data-stu-id="dfc59-212">Prototype</span></span>

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="dfc59-213">Description</span><span class="sxs-lookup"><span data-stu-id="dfc59-213">Description</span></span>

<span data-ttu-id="dfc59-214">이 서비스는 DHCP 서버 처리를 시작합니다. 여기에는 서버 UDP 소켓을 만들고, DHCP 포트를 바인딩하고 클라이언트 DHCP 요청을 받기 위해 대기하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-214">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dfc59-215">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="dfc59-215">Input Parameters</span></span>

- <span data-ttu-id="dfc59-216">**dhcp_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-216">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="dfc59-217">반환 값</span><span class="sxs-lookup"><span data-stu-id="dfc59-217">Return Values</span></span>

- <span data-ttu-id="dfc59-218">**NX_SUCCESS**: (0x00) 서버를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-218">**NX_SUCCESS**: (0x00) Successful Server start.</span></span>  
- <span data-ttu-id="dfc59-219">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP가 이미 시작됨</span><span class="sxs-lookup"><span data-stu-id="dfc59-219">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="dfc59-220">NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-220">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="dfc59-221">NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="dfc59-221">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="dfc59-222">NX_DHCP_PARAMETER_ERROR: (0x92) 잘못된 포인터가 아닌 입력</span><span class="sxs-lookup"><span data-stu-id="dfc59-222">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dfc59-223">허용 위치</span><span class="sxs-lookup"><span data-stu-id="dfc59-223">Allowed From</span></span>

<span data-ttu-id="dfc59-224">스레드</span><span class="sxs-lookup"><span data-stu-id="dfc59-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="dfc59-225">예제</span><span class="sxs-lookup"><span data-stu-id="dfc59-225">Example</span></span>

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="dfc59-226">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dfc59-226">See Also</span></span>

<span data-ttu-id="dfc59-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="dfc59-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span></span>

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="dfc59-228">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="dfc59-228">nx_dhcp_server_stop</span></span>

<span data-ttu-id="dfc59-229">DHCP 서버 처리 중지</span><span class="sxs-lookup"><span data-stu-id="dfc59-229">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="dfc59-230">프로토타입</span><span class="sxs-lookup"><span data-stu-id="dfc59-230">Prototype</span></span>

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="dfc59-231">Description</span><span class="sxs-lookup"><span data-stu-id="dfc59-231">Description</span></span>

<span data-ttu-id="dfc59-232">이 서비스는 DHCP 클라이언트 요청 수신을 포함하는 DHCP 서버 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-232">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dfc59-233">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="dfc59-233">Input Parameters</span></span>

- <span data-ttu-id="dfc59-234">**dhcp_ptr**: DHCP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="dfc59-234">**dhcp_ptr**: Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="dfc59-235">반환 값</span><span class="sxs-lookup"><span data-stu-id="dfc59-235">Return Values</span></span>

- <span data-ttu-id="dfc59-236">**NX_SUCCESS**: (0x00) DHCP를 성공적으로 중지함</span><span class="sxs-lookup"><span data-stu-id="dfc59-236">**NX_SUCCESS**: (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="dfc59-237">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP가 이미 시작됨</span><span class="sxs-lookup"><span data-stu-id="dfc59-237">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="dfc59-238">NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dfc59-238">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="dfc59-239">NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="dfc59-239">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="dfc59-240">NX_DHCP_PARAMETER_ERROR: (0x92) 잘못된 포인터가 아닌 입력</span><span class="sxs-lookup"><span data-stu-id="dfc59-240">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dfc59-241">허용 위치</span><span class="sxs-lookup"><span data-stu-id="dfc59-241">Allowed From</span></span>

<span data-ttu-id="dfc59-242">스레드</span><span class="sxs-lookup"><span data-stu-id="dfc59-242">Threads</span></span>

### <a name="example"></a><span data-ttu-id="dfc59-243">예제</span><span class="sxs-lookup"><span data-stu-id="dfc59-243">Example</span></span>

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
