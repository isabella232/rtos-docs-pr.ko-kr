---
title: 챕터 4 - Azure RTOS NetX Duo DHCPv6 서버 서비스
description: 이 챕터에는 모든 NetX Duo DHCPv6 서버 서비스에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d45139031b5a687baacf86c7a2e0a53c90533be
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810843"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a><span data-ttu-id="12816-103">챕터 4 - Azure RTOS NetX Duo DHCPv6 서버 서비스</span><span class="sxs-lookup"><span data-stu-id="12816-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 server services</span></span>

<span data-ttu-id="12816-104">이 챕터에는 모든 NetX Duo DHCPv6 서버 서비스(아래 참조)에 대한 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-104">This chapter contains a description of all NetX Duo DHCPv6Server services (listed below).</span></span>

<span data-ttu-id="12816-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="12816-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="12816-106">nx_dhcpv6_server_create *DHCPv6 서버 인스턴스를 만듭니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-106">nx_dhcpv6_server_create *Create a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="12816-107">nx_dhcpv6_server_delete *DHCPv6 서버 인스턴스를 삭제합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-107">nx_dhcpv6_server_delete *Delete a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="12816-108">nx_dhcpv6_server_start *DHCPv6 서버 작업을 시작합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-108">nx_dhcpv6_server_start *Start the DHCPv6 server task*</span></span>
- <span data-ttu-id="12816-109">nx_dhcpv6_server_suspend *DHCPv6 서버 작업을 일시 중단합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-109">nx_dhcpv6_server_suspend *Suspend the DHCPv6 server task*</span></span>
- <span data-ttu-id="12816-110">nx_dhcpv6_server_resume *DHCPv6 클라이언트 처리를 계속합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-110">nx_dhcpv6_server_resume *Resume DHCPv6 client processing*</span></span>
- <span data-ttu-id="12816-111">nx_dhcpv6_server_suspend *DHCPv6 클라이언트 처리를 일시 중단합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-111">nx_dhcpv6_server_suspend *Suspend DHCPv6 client processing*</span></span>
- <span data-ttu-id="12816-112">nx_dhcpv6_create_dns_address *옵션 요청 대상 DNS 서버를 설정합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-112">nx_dhcpv6_create_dns_address *Set the DNS server for option requests*</span></span>
- <span data-ttu-id="12816-113">nx_dhcpv6_create_ip_address_range *임대할 IP 주소 범위를 만듭니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-113">nx_dhcpv6_create_ip_address_range *Create the range of IP addresses to lease*</span></span>
- <span data-ttu-id="12816-114">nx_dhcpv6_reserve_ip_address_range *서버 목록의 IP 주소 범위를 예약합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-114">nx_dhcpv6_reserve_ip_address_range *Reserve range of IP addresses in server list*</span></span>
- <span data-ttu-id="12816-115">nx_dhcpv6_set_server_duid *DHCPv6 패킷의 서버 DUID를 설정합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-115">nx_dhcpv6_set_server_duid *Set the Server DUID for DHCPv6 packets*</span></span>
- <span data-ttu-id="12816-116">nx_dhcpv6_add_ip_address_lease *DHCPv6 서버 테이블에 임대 레코드를 추가합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-116">nx_dhcpv6_add_ip_address_lease *Add a lease record to the DHCPv6 server table*</span></span>
- <span data-ttu-id="12816-117">Nx_dhcpv6_retrieve_ip_address_lease *서버 테이블에서 IP 임대 레코드를 검색합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-117">Nx_dhcpv6_retrieve_ip_address_lease *Retrieve an IP lease record from the Server table*</span></span>
- <span data-ttu-id="12816-118">nx_dhcpv6_add_client_record *서버 테이블에 DHCPv6 클라이언트 레코드를 추가합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-118">nx_dhcpv6_add_client_record *Add a DHCPv6 Client record to the Server table*</span></span>
- <span data-ttu-id="12816-119">nx_dhcpv6_retrieve_client_record *서버 테이블에서 클라이언트 레코드를 검색합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-119">nx_dhcpv6_retrieve_client_record *Retrieve a client record from the Server table*</span></span>
- <span data-ttu-id="12816-120">nx_dhcpv6_server_interface_set *서버 DHCPv6 서비스의 인터페이스 인덱스를 설정합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-120">nx_dhcpv6_server_interface_set *Set the interface index for Server DHCPv6 services*</span></span>
- <span data-ttu-id="12816-121">nx_dhcpv6_server_option_request_handler_set *옵션 요청 처리기를 설정합니다.*</span><span class="sxs-lookup"><span data-stu-id="12816-121">nx_dhcpv6_server_option_request_handler_set *Set the option request handler*</span></span>

## <a name="nx_dhcpv6_create_dns_address"></a><span data-ttu-id="12816-122">nx_dhcpv6_create_dns_address</span><span class="sxs-lookup"><span data-stu-id="12816-122">nx_dhcpv6_create_dns_address</span></span>

### <a name="set-the-network-dns-server"></a><span data-ttu-id="12816-123">네트워크 DNS 서버를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-123">Set the network DNS server</span></span>

<span data-ttu-id="12816-124">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-124">**Prototype**</span></span>

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

<span data-ttu-id="12816-125">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-125">**Description**</span></span>

<span data-ttu-id="12816-126">이 서비스는 서버 DHCPv6 네트워크 인터페이스의 DNS 서버 주소를 사용하여 DHCPv6 서버를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-126">This service loads the DHCPv6 Server with the DNS server address for the Server DHCPv6 network interface.</span></span>

<span data-ttu-id="12816-127">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-127">**Input Parameters**</span></span>

- <span data-ttu-id="12816-128">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-128">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-129">**dns_ipv6_address** DNS 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-129">**dns_ipv6_address** Pointer to the DNS server</span></span>

<span data-ttu-id="12816-130">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-130">**Return Values**</span></span>

- <span data-ttu-id="12816-131">**NX_SUCCESS** (0x00) DNS 서버가 DHCPv6 서버 인스턴스에 저장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-131">**NX_SUCCESS** (0x00) DNS Serversaved to DHCPv6 Server instance</span></span>
- <span data-ttu-id="12816-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 잘못된 주소가 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="12816-133">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-133">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-134">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-134">**Allowed From**</span></span>

<span data-ttu-id="12816-135">응용 프로그램 코드</span><span class="sxs-lookup"><span data-stu-id="12816-135">Application Code</span></span>

<span data-ttu-id="12816-136">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-136">**Example**</span></span>

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a><span data-ttu-id="12816-137">nx_dhcpv6_create_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="12816-137">nx_dhcpv6_create_ip_address_range</span></span>

### <a name="create-the-server-ip-address-list"></a><span data-ttu-id="12816-138">서버 IP 주소 목록 만들기</span><span class="sxs-lookup"><span data-stu-id="12816-138">Create the Server IP address list</span></span>

<span data-ttu-id="12816-139">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-139">**Prototype**</span></span>

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

<span data-ttu-id="12816-140">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-140">**Description**</span></span>

<span data-ttu-id="12816-141">이 서비스는 서버의 할당 가능한 주소 범위의 시작 주소와 끝 주소로 지정된 IP 주소 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12816-141">This service creates the IP address list specified by the start and end addresses of the Server’s assignable address range.</span></span> <span data-ttu-id="12816-142">시작 주소와 끝 주소는 서버 인터페이스 주소 접두사와 일치해야 합니다(서버 DHCPv6 인터페이스와 동일한 링크에 있어야 함).</span><span class="sxs-lookup"><span data-stu-id="12816-142">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 interface).</span></span> <span data-ttu-id="12816-143">실제로 추가된 주소 수가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="12816-143">The number of addresses actually added is returned.</span></span>

<span data-ttu-id="12816-144">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-144">**Input Parameters**</span></span>

- <span data-ttu-id="12816-145">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-145">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-146">**start_ipv6_address** 추가할 주소의 시작 부분</span><span class="sxs-lookup"><span data-stu-id="12816-146">**start_ipv6_address** Start of addresses to add</span></span>
- <span data-ttu-id="12816-147">**end_ipv6_address** 추가할 주소 끝 부분</span><span class="sxs-lookup"><span data-stu-id="12816-147">**end_ipv6_address** End of addresses to add</span></span>
- <span data-ttu-id="12816-148">\***addresses_added** 추가된 주소 출력</span><span class="sxs-lookup"><span data-stu-id="12816-148">\***addresses_added** Output of addresses added</span></span>

<span data-ttu-id="12816-149">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-149">**Return Values**</span></span>

- <span data-ttu-id="12816-150">**NX_SUCCESS** (0x00) IP 주소 목록을 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-150">**NX_SUCCESS** (0x00) IP address list successfully created</span></span>
- <span data-ttu-id="12816-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 잘못된 주소가 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="12816-152">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-152">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-153">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-153">**Allowed From**</span></span>

<span data-ttu-id="12816-154">응용 프로그램 코드</span><span class="sxs-lookup"><span data-stu-id="12816-154">Application Code</span></span>

<span data-ttu-id="12816-155">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-155">**Example**</span></span>

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a><span data-ttu-id="12816-156">nx_dhcpv6_reserve_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="12816-156">nx_dhcpv6_reserve_ip_address_range</span></span>

### <a name="reserve-specified-range-of-ip-addresses"></a><span data-ttu-id="12816-157">지정된 IP 주소 범위 예약</span><span class="sxs-lookup"><span data-stu-id="12816-157">Reserve specified range of IP addresses</span></span>

<span data-ttu-id="12816-158">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-158">**Prototype**</span></span>

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

<span data-ttu-id="12816-159">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-159">**Description**</span></span>

<span data-ttu-id="12816-160">이 서비스는 시작 주소와 끝 주소로 지정된 IP 주소 범위를 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-160">This service reserves the IP address range specified by the start and end addresses.</span></span> <span data-ttu-id="12816-161">이러한 주소는 이전에 만든 서버 IP 주소 범위 내에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-161">These addresses must be within in the previously created server IP address range.</span></span> <span data-ttu-id="12816-162">이러한 주소는 DHCPv6 서버에서 클라이언트에 할당하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-162">These addresses will not be assigned to any Clients by the DHCPv6 Server.</span></span> <span data-ttu-id="12816-163">시작 주소와 끝 주소는 서버 인터페이스 주소 접두사와 일치해야 합니다(서버 DHCPv6 네트워크 인터페이스와 동일한 링크에 있어야 함).</span><span class="sxs-lookup"><span data-stu-id="12816-163">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 network interface).</span></span> <span data-ttu-id="12816-164">실제로 예약된 주소 수가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="12816-164">The number of addresses actually reserved is returned.</span></span>

<span data-ttu-id="12816-165">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-165">**Input Parameters**</span></span>

- <span data-ttu-id="12816-166">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-166">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-167">**start_ipv6_address** 예약할 주소의 시작 부분</span><span class="sxs-lookup"><span data-stu-id="12816-167">**start_ipv6_address** Start of addresses to reserve</span></span>
- <span data-ttu-id="12816-168">**end_ipv6_address** 예약할 주소 끝 부분</span><span class="sxs-lookup"><span data-stu-id="12816-168">**end_ipv6_address** End of addresses to reserve</span></span>
- <span data-ttu-id="12816-169">\***addresses_reserved** 예약된 주소 수</span><span class="sxs-lookup"><span data-stu-id="12816-169">\***addresses_reserved** Number of addresses reserved</span></span>

<span data-ttu-id="12816-170">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-170">**Return Values**</span></span>

- <span data-ttu-id="12816-171">**NX_SUCCESS** (0x00) RELEASE 메시지가 성공적으로 생성 및 처리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-171">**NX_SUCCESS** (0x00) RELEASE message successfully created and processed</span></span>
- <span data-ttu-id="12816-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 잘못된 주소가 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="12816-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) 시작 주소가 서버 주소 목록에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) Starting address not found in Server address list.</span></span>
- <span data-ttu-id="12816-174">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-174">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-175">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-175">**Allowed From**</span></span>

<span data-ttu-id="12816-176">응용 프로그램 코드</span><span class="sxs-lookup"><span data-stu-id="12816-176">Application Code</span></span>

<span data-ttu-id="12816-177">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-177">**Example**</span></span>

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a><span data-ttu-id="12816-178">nx_dhcpv6_server_create</span><span class="sxs-lookup"><span data-stu-id="12816-178">nx_dhcpv6_server_create</span></span>

### <a name="create-the-dhcpv6-server-instance"></a><span data-ttu-id="12816-179">DHCPv6 서버 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="12816-179">Create the DHCPv6 Server instance</span></span> 

<span data-ttu-id="12816-180">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-180">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

<span data-ttu-id="12816-181">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-181">**Description**</span></span>

<span data-ttu-id="12816-182">이 서비스는 지정된 입력을 사용하여 DHCPv6 서버 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12816-182">This service creates the DHCPv6 Server task with the specified input.</span></span> <span data-ttu-id="12816-183">콜백 처리기는 선택적 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="12816-183">The callback handlers are optional input.</span></span> <span data-ttu-id="12816-184">스택 포인터, IP 인스턴스 및 패킷 풀 입력은 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="12816-184">The stack pointer, IP instance and packet pool input are required.</span></span> <span data-ttu-id="12816-185">IP 인스턴스 및 패킷 풀이 이미 생성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-185">The IP instance and packet pool must already be created.</span></span>

<span data-ttu-id="12816-186">사용자는 nx_dhcpv6_server_option_request_handler_set를 호출하여 옵션 요청 처리기를 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-186">User is encouraged to call nx_dhcpv6_server_option_request_handler_set to set the option request handler.</span></span>

<span data-ttu-id="12816-187">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-187">**Input Parameters**</span></span>

- <span data-ttu-id="12816-188">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-188">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-189">**ip_ptr** IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-189">**ip_ptr** Pointer to the IP instance</span></span>
- <span data-ttu-id="12816-190">**name_str** 서버 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-190">**name_str** Pointer to Server name</span></span>
- <span data-ttu-id="12816-191">**packet_pool_ptr** 서버 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-191">**packet_pool_ptr** Pointer to Server packet pool</span></span>
- <span data-ttu-id="12816-192">**stack_ptr** 서버 스택 메모리에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-192">**stack_ptr** Pointer to Server stack memory</span></span>
- <span data-ttu-id="12816-193">**stack_size** 서버 스택 메모리의 크기</span><span class="sxs-lookup"><span data-stu-id="12816-193">**stack_size** Size of Server stack memory</span></span>
- <span data-ttu-id="12816-194">**dhcpv6_address_declined_handler** 클라이언트 거부 또는 해제 메시지 처리기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-194">**dhcpv6_address_declined_handler** Pointer to Client Decline or Release message handler</span></span>
- <span data-ttu-id="12816-195">**dhcpv6_option_request_handler** 옵션 요청 옵션 처리기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-195">**dhcpv6_option_request_handler** Pointer to options request option handler</span></span>

<span data-ttu-id="12816-196">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-196">**Return Values**</span></span>

- <span data-ttu-id="12816-197">**NX_SUCCESS** (0x00) 서버를 성공적으로 다시 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-197">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="12816-198">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-198">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="12816-199">NX_DHCPV6_PARAM_ERROR 잘못된 비 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-199">NX_DHCPV6_PARAM_ERROR Invalid non pointer input</span></span>

<span data-ttu-id="12816-200">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-200">**Allowed From**</span></span>

<span data-ttu-id="12816-201">응용 프로그램 코드</span><span class="sxs-lookup"><span data-stu-id="12816-201">Application Code</span></span>

<span data-ttu-id="12816-202">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-202">**Example**</span></span>

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a><span data-ttu-id="12816-203">nx_dhcpv6_server_delete</span><span class="sxs-lookup"><span data-stu-id="12816-203">nx_dhcpv6_server_delete</span></span>

### <a name="delete-the-dhcpv6-server"></a><span data-ttu-id="12816-204">DHCPv6 서버 삭제</span><span class="sxs-lookup"><span data-stu-id="12816-204">Delete the DHCPv6 Server</span></span>

<span data-ttu-id="12816-205">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-205">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="12816-206">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-206">**Description**</span></span>

<span data-ttu-id="12816-207">이 서비스는 DHCPv6 서버 작업 및 서버가 처리하는 모든 요청을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-207">This service deletes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="12816-208">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-208">**Input Parameters**</span></span>

- <span data-ttu-id="12816-209">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-209">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="12816-210">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-210">**Return Values**</span></span>

- <span data-ttu-id="12816-211">**NX_SUCCESS** (0x00) 서버를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="12816-211">**NX_SUCCESS** (0x00) Server successfully deleted</span></span>
- <span data-ttu-id="12816-212">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-212">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-213">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-213">**Allowed From**</span></span>

<span data-ttu-id="12816-214">스레드</span><span class="sxs-lookup"><span data-stu-id="12816-214">Threads</span></span>

<span data-ttu-id="12816-215">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-215">**Example**</span></span>

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a><span data-ttu-id="12816-216">nx_dhcpv6_server_resume</span><span class="sxs-lookup"><span data-stu-id="12816-216">nx_dhcpv6_server_resume</span></span>

### <a name="resume-dhcpv6-server-task"></a><span data-ttu-id="12816-217">DHCPv6 서버 작업 다시 시작</span><span class="sxs-lookup"><span data-stu-id="12816-217">Resume DHCPv6 Server task</span></span> 

<span data-ttu-id="12816-218">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-218">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="12816-219">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-219">**Description**</span></span>

<span data-ttu-id="12816-220">이 서비스는 DHCPv6 서버 작업 및 서버가 처리하는 모든 요청을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-220">This service resumes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="12816-221">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-221">**Input Parameters**</span></span>

- <span data-ttu-id="12816-222">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-222">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="12816-223">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-223">**Return Values**</span></span>

- <span data-ttu-id="12816-224">**NX_SUCCESS** (0x00) 서버를 성공적으로 다시 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-224">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="12816-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) 서버가 이미 실행되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="12816-226">**status**(변수) ThreadX 및 NetX Duo 오류 상태</span><span class="sxs-lookup"><span data-stu-id="12816-226">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="12816-227">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-227">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-228">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-228">**Allowed From**</span></span>

<span data-ttu-id="12816-229">스레드</span><span class="sxs-lookup"><span data-stu-id="12816-229">Threads</span></span>

<span data-ttu-id="12816-230">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-230">**Example**</span></span>

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a><span data-ttu-id="12816-231">nx_dhcpv6_server_suspend</span><span class="sxs-lookup"><span data-stu-id="12816-231">nx_dhcpv6_server_suspend</span></span>

### <a name="suspend-dhcpv6-server-task"></a><span data-ttu-id="12816-232">DHCPv6 서버 작업 일시 중단</span><span class="sxs-lookup"><span data-stu-id="12816-232">Suspend DHCPv6 Server task</span></span> 

<span data-ttu-id="12816-233">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-233">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="12816-234">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-234">**Description**</span></span>

<span data-ttu-id="12816-235">이 서비스는 DHCPv6 서버 작업 및 서버가 처리하는 모든 요청을 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-235">This service suspends the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="12816-236">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-236">**Input Parameters**</span></span>

- <span data-ttu-id="12816-237">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-237">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="12816-238">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-238">**Return Values**</span></span>

- <span data-ttu-id="12816-239">**NX_SUCCESS** (0x00) 서버를 성공적으로 다시 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-239">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="12816-240">**NX_DHCPV6_NOT_STARTED** (0xE92) 서버가 시작되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-240">**NX_DHCPV6_NOT_STARTED** (0xE92) Server is not started</span></span> 
- <span data-ttu-id="12816-241">**Status**(변수) ThreadX 및 NetX Duo 오류 상태</span><span class="sxs-lookup"><span data-stu-id="12816-241">**Status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="12816-242">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-242">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-243">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-243">**Allowed From**</span></span>

<span data-ttu-id="12816-244">스레드</span><span class="sxs-lookup"><span data-stu-id="12816-244">Threads</span></span>

<span data-ttu-id="12816-245">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-245">**Example**</span></span>

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a><span data-ttu-id="12816-246">nx_dhcpv6_server_start</span><span class="sxs-lookup"><span data-stu-id="12816-246">nx_dhcpv6_server_start</span></span>

### <a name="start-the-dhcpv6-server-task"></a><span data-ttu-id="12816-247">DHCPv6 서버 작업 시작</span><span class="sxs-lookup"><span data-stu-id="12816-247">Start the DHCPv6 Server task</span></span> 

<span data-ttu-id="12816-248">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-248">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="12816-249">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-249">**Description**</span></span>

<span data-ttu-id="12816-250">이 서비스는 DHCPv6 서버 작업을 시작하고 서버가 DHCPv6 클라이언트 메시지 수신에 대한 애플리케이션 요청을 처리할 수 있게 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-250">This service starts the DHCPv6 Server task and readies the Server to process application requests for receiving DHCPv6 Client messages.</span></span> <span data-ttu-id="12816-251">서버 인스턴스에 충분한 정보(서버 DUID)가 있는지 확인하고, DHCPv6 메시지를 보내고 받기 위한 UDP 소켓을 만들고 바인딩하며, 세션 시간 및 IP 임대 만료 시간을 추적하는 타이머를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-251">It verifies the Server instance has sufficient information (Server DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages, and activates timers for keeping track of session time and IP lease expiration.</span></span>

>[!NOTE] 
> <span data-ttu-id="12816-252">호스트 애플리케이션은 DHCPv6 서버를 실행하기 전에 서버에서 IP 주소를 할당할 수 있는 IP 주소 범위를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-252">Before the DHCPv6 Server can run, the host application is responsible for creating the IP address range from which the Server can assign IP addresses.</span></span> <span data-ttu-id="12816-253">또한 서버 DUID 및 DHCPv6 인터페이스를 설정해야 합니다(각각 *nx_dhcpv6_server_duid_set* 및 *nx_dhcpv6_server_interface_set* 참조).</span><span class="sxs-lookup"><span data-stu-id="12816-253">It is also responsible for setting the Server DUID and DHCPv6 interface (see *nx_dhcpv6_server_duid_set* and *nx_dhcpv6_server_interface_set* respectively.</span></span>

<span data-ttu-id="12816-254">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-254">**Input Parameters**</span></span>

- <span data-ttu-id="12816-255">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-255">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="12816-256">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-256">**Return Values**</span></span>

- <span data-ttu-id="12816-257">**NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-257">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="12816-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) 서버가 이미 실행되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="12816-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) 서버에 임대할 할당 가능한 주소가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) Server has no assignable addresses to lease</span></span>
- <span data-ttu-id="12816-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) 글로벌 주소 인덱스를 설정하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Global address index not set</span></span>
- <span data-ttu-id="12816-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) 서버 DUID가 생성되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) No Server DUID created</span></span> 
- <span data-ttu-id="12816-262">**status**(변수) ThreadX 및 NetX Duo 오류 상태</span><span class="sxs-lookup"><span data-stu-id="12816-262">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="12816-263">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-263">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-264">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-264">**Allowed From**</span></span>

<span data-ttu-id="12816-265">스레드</span><span class="sxs-lookup"><span data-stu-id="12816-265">Threads</span></span>

<span data-ttu-id="12816-266">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-266">**Example**</span></span>

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a><span data-ttu-id="12816-267">nx_dhcpv6_retrieve_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="12816-267">nx_dhcpv6_retrieve_ip_address_lease</span></span>

### <a name="get-an-ip-address-lease-from-the-server-table"></a><span data-ttu-id="12816-268">서버 테이블에서 IP 주소 임대 가져오기</span><span class="sxs-lookup"><span data-stu-id="12816-268">Get an IP address lease from the Server table</span></span>

<span data-ttu-id="12816-269">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-269">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

<span data-ttu-id="12816-270">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-270">**Description**</span></span>

<span data-ttu-id="12816-271">이 서비스는 지정된 테이블 인덱스 위치의 서버 테이블에서 IP 주소 임대 레코드를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-271">This service retrieves an IP address lease record from the Server table at the specified table index location.</span></span> <span data-ttu-id="12816-272">클라이언트 레코드 데이터 검색 전후로 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-272">This can be done before or after retrieving Client record data.</span></span>

<span data-ttu-id="12816-273">DHCPv6 서버와 비휘발성 메모리 간에 데이터를 저장하고 검색하는 기능은 DHCPv6 프로토콜의 요구 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12816-273">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="12816-274">IP 임대 데이터와 클라이언트 레코드 데이터를 비휘발성 메모리에 저장하는 순서에는 차이가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-274">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="12816-275">먼저 DHCPv6 서버를 중지하거나 일시 중단하지 않고 서버 테이블 간에 데이터를 복사하는 것은 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-275">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="12816-276">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-276">**Input Parameters**</span></span>

- <span data-ttu-id="12816-277">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-277">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-278">**table_index** 임대를 저장할 테이블 인덱스</span><span class="sxs-lookup"><span data-stu-id="12816-278">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="12816-279">**lease_IP_address** 클라이언트에 임대된 IP 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-279">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="12816-280">**T1** 클라이언트에서 요청한 갱신 시간</span><span class="sxs-lookup"><span data-stu-id="12816-280">**T1** Client requested renew time</span></span>
- <span data-ttu-id="12816-281">**T2** 클라이언트에서 요청한 재바인딩 시간</span><span class="sxs-lookup"><span data-stu-id="12816-281">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="12816-282">**valid_lifetime** 클라이언트 임대가 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-282">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="12816-283">**preferred_lifetime** 클라이언트 임대가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-283">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="12816-284">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-284">**Return Values**</span></span>

- <span data-ttu-id="12816-285">**NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-285">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="12816-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) 잘못된 IP 임대 데이터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="12816-287">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-287">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-288">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-288">**Allowed From**</span></span>

<span data-ttu-id="12816-289">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="12816-289">Application code</span></span>

<span data-ttu-id="12816-290">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-290">**Example**</span></span>

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a><span data-ttu-id="12816-291">nx_dhcpv6_add_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="12816-291">nx_dhcpv6_add_ip_address_lease</span></span>

### <a name="add-an-ip-address-lease-to-the-server-table"></a><span data-ttu-id="12816-292">서버 테이블에 IP 주소 임대 추가</span><span class="sxs-lookup"><span data-stu-id="12816-292">Add an IP address lease to the Server table</span></span>

<span data-ttu-id="12816-293">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-293">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

<span data-ttu-id="12816-294">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-294">**Description**</span></span>

<span data-ttu-id="12816-295">이 서비스는 이전 DHCPv6 서버 세션의 IP 임대 데이터를 비휘발성 메모리에서 서버 임대 테이블로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-295">This service loads IP lease data from a previous DHCPv6 Server session from non volatile memory to the Server lease table.</span></span> <span data-ttu-id="12816-296">서버가 처음으로 실행 중이고 이전 임대 데이터가 없는 경우에는 이 작업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-296">This is not necessary if the Server is running for the first time and has no previous lease data.</span></span> <span data-ttu-id="12816-297">이 경우 호스트 애플리케이션은 *nx_dhcpv6_create_ip_address_range* 서비스를 사용하여 IP 주소를 할당하기 위한 IP 주소 범위를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-297">If this is the case the host application must create an IP address range for assigning IP addresses, using the *nx_dhcpv6_create_ip_address_range* service.</span></span> <span data-ttu-id="12816-298">이 데이터는 DHCPv6 임대 레코드를 다시 생성하기에 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-298">The data is sufficient to reconstruct a DHCPv6 lease record.</span></span> <span data-ttu-id="12816-299">테이블 인덱스를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-299">The table index need not be specified.</span></span> <span data-ttu-id="12816-300">0xFFFFFFFF(무한대)로 설정되면 DHCPv6 서버가 데이터를 복사하기 위해 다음으로 사용 가능한 슬롯을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-300">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will find the next available slot to copy the data to.</span></span>

>[!NOTE] 
> <span data-ttu-id="12816-301">클라이언트 레코드를 업로드하려면 먼저 IP 임대 데이터를 업로드해야 합니다. 둘 다 DHCPv6 서버를 시작하기 전에 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-301">Uploading IP lease data MUST be done before uploading Client records; both MUST be done before (re)starting the DHCPv6 Server.</span></span>

<span data-ttu-id="12816-302">DHCPv6 서버와 비휘발성 메모리 간에 데이터를 저장하고 검색하는 기능은 DHCPv6 프로토콜의 요구 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12816-302">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="12816-303">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-303">**Input Parameters**</span></span>

- <span data-ttu-id="12816-304">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-304">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-305">**table_index** 임대를 저장할 테이블 인덱스</span><span class="sxs-lookup"><span data-stu-id="12816-305">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="12816-306">**lease_IP_address** 클라이언트에 임대된 IP 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-306">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="12816-307">**T1** 클라이언트에서 요청한 갱신 시간</span><span class="sxs-lookup"><span data-stu-id="12816-307">**T1** Client requested renew time</span></span>
- <span data-ttu-id="12816-308">**T2** 클라이언트에서 요청한 재바인딩 시간</span><span class="sxs-lookup"><span data-stu-id="12816-308">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="12816-309">**valid_lifetime** 클라이언트 임대가 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-309">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="12816-310">**preferred_lifetime** 클라이언트 임대가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-310">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="12816-311">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-311">**Return Values**</span></span>

- <span data-ttu-id="12816-312">**NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-312">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="12816-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) 추가 임대 데이터를 위한 공간이 없습니다.\*\*</span><span class="sxs-lookup"><span data-stu-id="12816-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) No room for more lease data\*\*</span></span>
- <span data-ttu-id="12816-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 임대 데이터가 서버 DHCPv6 인터페이스와 연결된 것 같지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Lease data does not appear to be on link with Server DHCPv6 interface</span></span>
- <span data-ttu-id="12816-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) 잘못된 IP 임대 데이터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="12816-316">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-316">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-317">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-317">**Allowed From**</span></span>

<span data-ttu-id="12816-318">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="12816-318">Application code</span></span>

<span data-ttu-id="12816-319">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-319">**Example**</span></span>

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a><span data-ttu-id="12816-320">nx_dhcpv6_add_client_record</span><span class="sxs-lookup"><span data-stu-id="12816-320">nx_dhcpv6_add_client_record</span></span>

### <a name="add-a-client-record-to-the-server-table"></a><span data-ttu-id="12816-321">서버 테이블에 클라이언트 레코드 추가</span><span class="sxs-lookup"><span data-stu-id="12816-321">Add a Client record to the Server table</span></span>

<span data-ttu-id="12816-322">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-322">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

<span data-ttu-id="12816-323">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-323">**Description**</span></span>

<span data-ttu-id="12816-324">이 서비스는 비휘발성 메모리의 클라이언트 데이터를 한 번에 한 레코드씩 서버 테이블로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-324">This service copies Client data from non volatile memory to the Server table one record at a time.</span></span> <span data-ttu-id="12816-325">서버가 다시 부팅되며 이전 세션의 클라이언트 데이터가 메모리에서 복원되는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-325">This is only necessary if the Server is being rebooted and has Client data from a previous session to restore from memory.</span></span> <span data-ttu-id="12816-326">서버에 이전 데이터가 없으면 DHCPv6 서버에서 클라이언트 테이블을 초기화하여 클라이언트 레코드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-326">If a Server has no previous data, the DHCPv6 Server will initialize the Client table to be able for adding Client records.</span></span>

<span data-ttu-id="12816-327">테이블 인덱스를 지정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-327">It is not necessary to specify the table index.</span></span> <span data-ttu-id="12816-328">0xFFFFFFFF(무한대)로 설정되면 DHCPv6 서버는 사용 가능한 다음 슬롯을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-328">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will locate the next available slot.</span></span> <span data-ttu-id="12816-329">DHCPv6 서버는 이 데이터로 클라이언트 레코드를 다시 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-329">The DHCPv6 Server can reconstruct a Client record from this data.</span></span>

>[!NOTE] 
> <span data-ttu-id="12816-330">클라이언트에서 데이터를 기록하기 전에 호스트 애플리케이션에서 IP 임대 데이터를 업로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-330">The host application MUST upload the IP lease data BEFORE the Client record data.</span></span> <span data-ttu-id="12816-331">그러면 각 클라이언트 레코드가 해당 테이블의 해당 IP 임대 레코드와 조인되도록 DHCPv6 서버에서 내부적으로 테이블을 교차 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-331">This is so that internally the DHCPv6 Server can cross link the tables so that each Client record is joined with its corresponding IP lease record in their respective tables.</span></span> <span data-ttu-id="12816-332">메모리에서 IP 임대 데이터를 업로드하는 방법에 대한 자세한 내용은 *nx_dhcpv6_add_ip_address_lease* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12816-332">See *nx_dhcpv6_add_ip_address_lease* for details on uploading IP lease data from memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="12816-333">DUID 유형에 따라 모든 데이터를 제공해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="12816-333">Depending on DUID type, not all data must be supplied.</span></span> <span data-ttu-id="12816-334">예를 들어 클라이언트에 공급업체에서 할당한 DUID 유형이 있는 경우, DUID 링크 계층 매개 변수(MAC 주소, 하드웨어 종류, DUID 시간)에 0으로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-334">For example if a Client has a vendor assigned DUID type, it can send in zero for DUID Link Layer parameters (MAC address, hardware type, DUID time).</span></span>

<span data-ttu-id="12816-335">DHCPv6 서버와 비휘발성 메모리 간에 데이터를 저장하고 검색하는 기능은 DHCPv6 프로토콜의 요구 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12816-335">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="12816-336">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-336">**Input Parameters**</span></span>

- <span data-ttu-id="12816-337">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-337">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="12816-338">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-338">**Return Values**</span></span>

- <span data-ttu-id="12816-339">**NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-339">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="12816-340">**NX_ INVALID_PARAMETERS** (0x4D) 잘못된 비포인터 입력\*\*</span><span class="sxs-lookup"><span data-stu-id="12816-340">**NX_ INVALID_PARAMETERS** (0x4D) Invalid non pointer input\*\*</span></span>
- <span data-ttu-id="12816-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) 다른 클라이언트 레코드를 추가할 빈 슬롯이 남아 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) No empty slots left for adding another Client record</span></span>
- <span data-ttu-id="12816-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) 서버 임대 테이블에서 클라이언트 할당 주소를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) Client assigned address not found in Server lease table.</span></span>
- <span data-ttu-id="12816-343">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-343">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-344">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-344">**Allowed From**</span></span>

<span data-ttu-id="12816-345">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="12816-345">Application code</span></span>

<span data-ttu-id="12816-346">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-346">**Example**</span></span>

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a><span data-ttu-id="12816-347">nx_dhcpv6_retrieve_client_record</span><span class="sxs-lookup"><span data-stu-id="12816-347">nx_dhcpv6_retrieve_client_record</span></span>

### <a name="retrieve-a-client-record-from-the-server-table"></a><span data-ttu-id="12816-348">서버 테이블에서 클라이언트 레코드 검색</span><span class="sxs-lookup"><span data-stu-id="12816-348">Retrieve a Client record from the Server table</span></span>

<span data-ttu-id="12816-349">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-349">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

<span data-ttu-id="12816-350">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-350">**Description**</span></span>

<span data-ttu-id="12816-351">이 서비스는 서버의 클라이언트 레코드 테이블에서 비휘발성 메모리에 저장할 필수 데이터를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-351">This service copies the essential data from the Server’s Client record table for storage to non-volatile memory.</span></span> <span data-ttu-id="12816-352">서버는 역방향 프로세스(서버 테이블에 데이터 업로드)로 해당 데이터의 적절한 클라이언트 레코드를 다시 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-352">The Server can reconstruct an adequate Client record from such data in the reverse process (uploading data to the Server table).</span></span> <span data-ttu-id="12816-353">DUID 유형에 관계없이 모든 포인터는 NULL 포인터가 될 수 없습니다. 데이터는 모든 매개 변수에서 0으로 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="12816-353">Regardless of the DUID type, none of the pointers can be NULL pointers; data is initialized to zero for all parameters.</span></span> <span data-ttu-id="12816-354">예를 들어 클라이언트 DUID 유형이 링크 계층+시간인 경우 공급업체 번호는 0으로 반환되고 프라이빗 ID는 빈 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="12816-354">For example, if the Client DUID type is Link Layer Plus Time, the vendor number is returned as zero and the private ID is an empty string.</span></span>

<span data-ttu-id="12816-355">DHCPv6 서버와 비휘발성 메모리 간에 데이터를 저장하고 검색하는 기능은 DHCPv6 프로토콜의 요구 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12816-355">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="12816-356">IP 임대 데이터와 클라이언트 레코드 데이터를 비휘발성 메모리에 저장하는 순서에는 차이가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-356">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="12816-357">먼저 DHCPv6 서버를 중지하거나 일시 중단하지 않고 서버 테이블 간에 데이터를 복사하는 것은 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-357">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="12816-358">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-358">**Input Parameters**</span></span>

- <span data-ttu-id="12816-359">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-359">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-360">**table_index** 서버의 클라이언트 테이블에 인덱스</span><span class="sxs-lookup"><span data-stu-id="12816-360">**table_index** Index into Server’s client table</span></span>
- <span data-ttu-id="12816-361">**message_xid** 클라이언트 서버 트랜잭션 ID</span><span class="sxs-lookup"><span data-stu-id="12816-361">**message_xid** Client Server Transaction ID</span></span>
- <span data-ttu-id="12816-362">**client_address** 클라이언트에 임대되는 IPv6 주소</span><span class="sxs-lookup"><span data-stu-id="12816-362">**client_address** IPv6 address leased to Client</span></span>
- <span data-ttu-id="12816-363">**client_state** 클라이언트 DHCPv6 상태(예: bound)</span><span class="sxs-lookup"><span data-stu-id="12816-363">**client_state** Client DHCPv6 state (e.g. bound)</span></span>
- <span data-ttu-id="12816-364">**IP_lease_time_accrued** 임대 시간이 이미 만료되었습니다. **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-364">**IP_lease_time_accrued** Time expired on lease already **dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-365">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-365">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="12816-366">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-366">**Return Values**</span></span>

- <span data-ttu-id="12816-367">**NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-367">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="12816-368">**NX_DHCPV6_INVALID_DUID** (0xECC) 유효하지 않거나 일치하지 않는 DUID 데이터</span><span class="sxs-lookup"><span data-stu-id="12816-368">**NX_DHCPV6_INVALID_DUID** (0xECC) Invalid or inconsistent DUID data</span></span>
- <span data-ttu-id="12816-369">**NX_PTR_ERROR** (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-369">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="12816-370">NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-370">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

<span data-ttu-id="12816-371">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-371">**Allowed From**</span></span>

<span data-ttu-id="12816-372">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="12816-372">Application code</span></span>

<span data-ttu-id="12816-373">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-373">**Example**</span></span>

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a><span data-ttu-id="12816-374">nx_dhcpv6_server_interface_set</span><span class="sxs-lookup"><span data-stu-id="12816-374">nx_dhcpv6_server_interface_set</span></span>

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a><span data-ttu-id="12816-375">서버 DHCPv6 인터페이스의 인터페이스 인덱스 설정</span><span class="sxs-lookup"><span data-stu-id="12816-375">Setthe interface index for Server DHCPv6 interface</span></span>

<span data-ttu-id="12816-376">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-376">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

<span data-ttu-id="12816-377">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-377">**Description**</span></span>

<span data-ttu-id="12816-378">이 서비스는 DHCPv6 서버가 DHCPv6 클라이언트 요청을 처리하는 네트워크 인터페이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-378">This service sets the network interface on which the DHCPv6 Server handles DHCPv6 Client requests.</span></span> <span data-ttu-id="12816-379">멀티홈을 지원하지 않는 NetX Duo 버전의 경우 인터페이스 값이 기본적으로 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="12816-379">Not that for versions of NetX Duo that do not support multihome, the interface value is defaulted to zero.</span></span> <span data-ttu-id="12816-380">해당 DHCPv6 인터페이스에서 서버 글로벌 주소를 가져오려면 글로벌 주소 인덱스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-380">The global address index is necessary to obtain the Server global address on its DHCPv6 interface.</span></span> <span data-ttu-id="12816-381">이는 DHCPv6 논리에서 임대 주소 및 기타 DHCPv6 데이터가 DHCPv6 서버와 연결되어 있는지 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="12816-381">This is used by the DHCPv6 logic to ensure that lease addresses and other DHCPv6 data is on link with the DHCPv6 Server.</span></span>

<span data-ttu-id="12816-382">단일 홈 디바이스에 설치되어 있거나 멀티홈을 지원하지 않는 애플리케이션의 경우에도 DHCPv6 서버를 시작하기 전에 이를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-382">This must be called before the DHCPv6 server is started, even for applications on single homed devices or without multihome support.</span></span>

<span data-ttu-id="12816-383">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-383">**Input Parameters**</span></span>

- <span data-ttu-id="12816-384">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-384">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-385">**iface_index** 서버 DHCPv6 서버 인터페이스</span><span class="sxs-lookup"><span data-stu-id="12816-385">**iface_index** Server DHCPv6 Server interface</span></span>
- <span data-ttu-id="12816-386">**ga_address_index** 서버 IP 인스턴스 주소 테이블의 서버 글로벌 주소 인덱스</span><span class="sxs-lookup"><span data-stu-id="12816-386">**ga_address_index** Index of Server global address in the Server IP instance address table</span></span>

<span data-ttu-id="12816-387">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-387">**Return Values**</span></span>

- <span data-ttu-id="12816-388">**NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-388">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="12816-389">**NX_INVALID_INTERFACE** (0x4C) 인터페이스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-389">**NX_INVALID_INTERFACE** (0x4C) Interface does not exist</span></span>
- <span data-ttu-id="12816-390">NX_NO_INTERFACE_ADDRESS (0x50) 글로벌 인덱스가 IP 인스턴스 최대 IPv6 주소(NX_MAX_IPV6_ADDRESSES)를 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-390">NX_NO_INTERFACE_ADDRESS (0x50) Global index exceeds the IP instance maximum IPv6 addresses (NX_MAX_IPV6_ADDRESSES)</span></span>
- <span data-ttu-id="12816-391">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-391">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-392">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-392">**Allowed From**</span></span>

<span data-ttu-id="12816-393">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="12816-393">Application code</span></span>

<span data-ttu-id="12816-394">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-394">**Example**</span></span>

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a><span data-ttu-id="12816-395">nx_dhcpv6_set_server_duid</span><span class="sxs-lookup"><span data-stu-id="12816-395">nx_dhcpv6_set_server_duid</span></span>

### <a name="set-the-server-duid-for-dhcpv6-packets"></a><span data-ttu-id="12816-396">DHCPv6 패킷의 서버 DUID 설정</span><span class="sxs-lookup"><span data-stu-id="12816-396">Set the Server DUID for DHCPv6 packets</span></span>

<span data-ttu-id="12816-397">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-397">**Prototype**</span></span>

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

<span data-ttu-id="12816-398">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-398">**Description**</span></span>

<span data-ttu-id="12816-399">이 서비스는 서버 DUID를 설정하며, 호스트 애플리케이션에서 서버를 시작하기 전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-399">This service sets the Server DUID and must be called before the host application starts the Server.</span></span> <span data-ttu-id="12816-400">링크 계층 및 링크 계층 시간 DUID 유형의 경우, 호스트 애플리케이션이 하드웨어 유형과 MAC 주소 데이터를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-400">For link layer and link layer time DUID types, the host application must supply the hardware type and MAC address data.</span></span> <span data-ttu-id="12816-401">링크 계층 시간 DUID의 경우, 시간 포인터가 유효한 시간을 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-401">For link layer time DUIDs, the time pointer must point to a valid time.</span></span> <span data-ttu-id="12816-402">2000년 1월 1일 이후 경과된 시간(초)이 일반적인 시드 값입니다.</span><span class="sxs-lookup"><span data-stu-id="12816-402">The number of seconds since Jan 1, 2000 is a typical seed value.</span></span> <span data-ttu-id="12816-403">서버 DUID 유형이 엔터프라이즈, 공급업체에서 할당한 형식인 경우에는 사용자가 구성할 수 있는 옵션 NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID 및 NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID로 DUID가 생성되고, 시간 및 MAC 주소 값을 NULL로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-403">If the Server DUID type is the enterprise, vendor assigned type, the DUID will be created from the user configurable options NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID and NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, and the time and MAC address values can be set to NULL.</span></span>

>[!NOTE] 
> <span data-ttu-id="12816-404">호스트 애플리케이션은 재부팅 후에도 클라이언트에 보내는 메시지에 동일한 DUID를 사용할 수 있도록 서버 DUID 매개 변수를 비휘발성 메모리에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-404">It is the host application’s responsibility to save the Server DUID parameters to nonvolatile memory such that it uses the same DUID in messages to Clients between reboots.</span></span> <span data-ttu-id="12816-405">이는 DHCPv6 프로토콜(RFC 3315)의 요구 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="12816-405">This is a requirement of the DHCPv6 protocol (RFC 3315).</span></span>

<span data-ttu-id="12816-406">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-406">**Input Parameters**</span></span>

- <span data-ttu-id="12816-407">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-407">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-408">**duid_type** DHCPv6 서버 DUID 유형</span><span class="sxs-lookup"><span data-stu-id="12816-408">**duid_type** DHCPv6 Server DUID type</span></span>
- <span data-ttu-id="12816-409">**hardware_type** 하드웨어 유형(예: 이더넷)</span><span class="sxs-lookup"><span data-stu-id="12816-409">**hardware_type** Hardware type (e.g. Ethernet)</span></span>
- <span data-ttu-id="12816-410">**mac_address_msw** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-410">**mac_address_msw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-411">**mac_address_lsw** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-411">**mac_address_lsw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-412">**time** DUID의 시간 값</span><span class="sxs-lookup"><span data-stu-id="12816-412">**time** Time value for DUID</span></span>

<span data-ttu-id="12816-413">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-413">**Return Values**</span></span>

- <span data-ttu-id="12816-414">**NX_SUCCESS** (0x00) 서버를 성공적으로 일시 중단했습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-414">**NX_SUCCESS** (0x00) Server successfully suspended</span></span>
- <span data-ttu-id="12816-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) 알 수 없거나 지원되지 않는 DUID 유형</span><span class="sxs-lookup"><span data-stu-id="12816-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) Unknown or unsupported DUID type</span></span>
- <span data-ttu-id="12816-416">**NX_INVALID_PARAMETERS** (0x4D) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-416">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>
- <span data-ttu-id="12816-417">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-417">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-418">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-418">**Allowed From**</span></span>

<span data-ttu-id="12816-419">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="12816-419">Application code</span></span>

<span data-ttu-id="12816-420">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-420">**Example**</span></span>

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a><span data-ttu-id="12816-421">nx_dhcpv6_server_option_request_handler_set</span><span class="sxs-lookup"><span data-stu-id="12816-421">nx_dhcpv6_server_option_request_handler_set</span></span>

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a><span data-ttu-id="12816-422">DHCPv6 서버 인스턴스의 옵션 요청 처리기 설정</span><span class="sxs-lookup"><span data-stu-id="12816-422">Set the option request handler for DHCPv6 Server instance</span></span> 

<span data-ttu-id="12816-423">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="12816-423">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

<span data-ttu-id="12816-424">**설명**</span><span class="sxs-lookup"><span data-stu-id="12816-424">**Description**</span></span>

<span data-ttu-id="12816-425">이 서비스는 DHCPv6 서버 확장 옵션 요청 처리기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="12816-425">This service sets the DHCPv6 Server extended option request handler.</span></span>

<span data-ttu-id="12816-426">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="12816-426">**Input Parameters**</span></span>

- <span data-ttu-id="12816-427">**dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-427">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="12816-428">**dhcpv6_option_request_handler_extended** 확장 옵션 요청 처리기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="12816-428">**dhcpv6_option_request_handler_extended** Pointer to extended options request handler</span></span>

<span data-ttu-id="12816-429">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="12816-429">**Return Values**</span></span>

- <span data-ttu-id="12816-430">**NX_SUCCESS** (0x00) 서버를 성공적으로 다시 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="12816-430">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="12816-431">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="12816-431">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="12816-432">**허용된 원본**</span><span class="sxs-lookup"><span data-stu-id="12816-432">**Allowed From**</span></span>

<span data-ttu-id="12816-433">응용 프로그램 코드</span><span class="sxs-lookup"><span data-stu-id="12816-433">Application Code</span></span>

<span data-ttu-id="12816-434">**예제**</span><span class="sxs-lookup"><span data-stu-id="12816-434">**Example**</span></span>

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```