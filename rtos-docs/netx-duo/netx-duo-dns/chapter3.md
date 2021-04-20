---
title: 3장 - Azure RTOS NetX Duo DNS 클라이언트 서비스 설명
description: 이 장에서는 아래에 나열된 모든 Azure RTOS NetX Duo DNS 서비스에 대해 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9634adab3944c29f64d26dd688b5053dc1bd9bcb
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810831"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a><span data-ttu-id="8c08d-103">3장 - Azure RTOS NetX Duo DNS 클라이언트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="8c08d-103">Chapter 3 - Description of Azure RTOS NetX Duo DNS Client Services</span></span>

<span data-ttu-id="8c08d-104">이 장에서는 아래에 나열된 모든 Azure RTOS NetX DNS 서비스에 대해 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="8c08d-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="8c08d-106">**nx_dns_authority_zone_start_get** *지정된 호스트 이름과 연결된 권한 영역의 시작 조회*</span><span class="sxs-lookup"><span data-stu-id="8c08d-106">**nx_dns_authority_zone_start_get** *Look up the start of a zone of authority associated with the specified host name*</span></span>

- <span data-ttu-id="8c08d-107">**nx_dns_cache_initialize** *DNS 캐시 초기화*</span><span class="sxs-lookup"><span data-stu-id="8c08d-107">**nx_dns_cache_initialize** *Initialize a DNS Cache.*</span></span>

- <span data-ttu-id="8c08d-108">**nx_dns_cache_notify_clear** *캐시 전체 알림 함수 지우기*</span><span class="sxs-lookup"><span data-stu-id="8c08d-108">**nx_dns_cache_notify_clear** *Clear the cache full notify function.*</span></span>

- <span data-ttu-id="8c08d-109">**nx_dns_cache_notify_set** *캐시 전체 알림 함수 설정*</span><span class="sxs-lookup"><span data-stu-id="8c08d-109">**nx_dns_cache_notify_set** *Set the cache full notify function.*</span></span>

- <span data-ttu-id="8c08d-110">**nx_dns_cname_get** *입력 도메인 이름 별칭에 대한 정식 도메인 이름 조회*</span><span class="sxs-lookup"><span data-stu-id="8c08d-110">**nx_dns_cname_get** *Look up the canonical domain name for the input domain name alias*</span></span>

- <span data-ttu-id="8c08d-111">**nx_dns_create** *DNS 클라이언트 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="8c08d-111">**nx_dns_create** *Create a DNS Client instance*</span></span>

- <span data-ttu-id="8c08d-112">**nx_dns_delete** *DNS 클라이언트 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="8c08d-112">**nx_dns_delete** *Delete a DNS Client instance*</span></span>

- <span data-ttu-id="8c08d-113">**nx_dns_domain_name_server_get** *입력 도메인 영역에 대한 권한 있는 이름 서버 조회*</span><span class="sxs-lookup"><span data-stu-id="8c08d-113">**nx_dns_domain_name_server_get** *Look up the authoritative name servers for the input domain zone*</span></span>

- <span data-ttu-id="8c08d-114">**nx_dns_domain_mail_exchange_get** *지정된 호스트 이름과 연결된 메일 교환 조회*</span><span class="sxs-lookup"><span data-stu-id="8c08d-114">**nx_dns_domain_mail_exchange_get** *Look up the mail exchange associated the specified host name.*</span></span>

- <span data-ttu-id="8c08d-115">**nx_dns_domain_service_get** *지정된 호스트 이름과 연결된 서비스 조회*</span><span class="sxs-lookup"><span data-stu-id="8c08d-115">**nx_dns_domain_service_get** *Look up the service(s) associated with the specified host name*</span></span>

- <span data-ttu-id="8c08d-116">**nx_dns_get_serverlist_size** *DNS 클라이언트 서버 목록의 크기 반환*</span><span class="sxs-lookup"><span data-stu-id="8c08d-116">**nx_dns_get_serverlist_size** *Return the size of the DNS Client server list*</span></span>

- <span data-ttu-id="8c08d-117">**nx_dns_info_by_name_get** *IP 주소 반환, 입력 호스트 이름에 대한 포트 쿼리*</span><span class="sxs-lookup"><span data-stu-id="8c08d-117">**nx_dns_info_by_name_get** *Return IP address, port querying on input host name*</span></span>

- <span data-ttu-id="8c08d-118">**nx_dns_ipv4_address_by_name_get** *지정된 호스트 이름에서 IPv4 주소 조회*</span><span class="sxs-lookup"><span data-stu-id="8c08d-118">**nx_dns_ipv4_address_by_name_get** *Look up the IPv4 address from the specified host name*</span></span>

- <span data-ttu-id="8c08d-119">**nxd_dns_ipv6_address_by_name_get** *지정된 호스트 이름에서 IPv6 주소 조회*</span><span class="sxs-lookup"><span data-stu-id="8c08d-119">**nxd_dns_ipv6_address_by_name_get** *Look up the IPv6 address from the specified host name*</span></span>

- <span data-ttu-id="8c08d-120">**nx_dns_host_by_address_get** *nxd_dns_host_by_address_get이 지정된 IP 주소에서 호스트 이름을 조회하는 래퍼 기능(IPv4 주소만 지원)*</span><span class="sxs-lookup"><span data-stu-id="8c08d-120">**nx_dns_host_by_address_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from a specified IP address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="8c08d-121">**nxd_dns_host_by_address_get** *입력 호스트 이름에서 IP 주소 조회(IPv4 및 IPv6 주소 모두 지원)*</span><span class="sxs-lookup"><span data-stu-id="8c08d-121">**nxd_dns_host_by_address_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="8c08d-122">**nx_dns_host_by_name_get** *nxd_dns_host_by_address_get이 지정된 주소에서 호스트 이름을 조회하는 래퍼 기능(IPv4 주소만 지원)*</span><span class="sxs-lookup"><span data-stu-id="8c08d-122">**nx_dns_host_by_name_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from the specified address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="8c08d-123">**nxd_dns_host_by_name_get** *입력 호스트 이름에서 IP 주소 조회(IPv4 및 IPv6 주소 모두 지원)*</span><span class="sxs-lookup"><span data-stu-id="8c08d-123">**nxd_dns_host_by_name_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="8c08d-124">**nx_dns_host_text_get** *입력 도메인 이름에 대한 텍스트 데이터 조회*</span><span class="sxs-lookup"><span data-stu-id="8c08d-124">**nx_dns_host_text_get** *Look up the text data for the input domain name*</span></span>

- <span data-ttu-id="8c08d-125">**nx_dns_packet_pool_set** *DNS 클라이언트 패킷 풀 설정*</span><span class="sxs-lookup"><span data-stu-id="8c08d-125">**nx_dns_packet_pool_set** *Set the DNS Client packet pool*</span></span>

- <span data-ttu-id="8c08d-126">**nx_dns_server_add** *n* xd_dns_server_add *가 클라이언트 목록에 지정된 주소의 DNS 서버를 추가하는 래퍼 기능(IPv4만 지원)*</span><span class="sxs-lookup"><span data-stu-id="8c08d-126">**nx_dns_server_add** *Wrapper function for* nxd_dns_server_add *to add a DNS Server at the specified address to the Client list (supports only IPv4)*</span></span>

- <span data-ttu-id="8c08d-127">**nxd_dns_server_add** *클라이언트 서버 목록에 지정된 IP 주소의 DNS 서버 추가(IPv4 또는 IPv6 주소 모두 지원)*</span><span class="sxs-lookup"><span data-stu-id="8c08d-127">**nxd_dns_server_add** *Add a DNS Server of the specified IP address to the Client server list (supports both IPv4 or IPv6 addresses)*</span></span>

- <span data-ttu-id="8c08d-128">**nx_dns_server_get** *클라이언트 목록에서 DNS 서버 반환(IPv4 주소만 지원)*</span><span class="sxs-lookup"><span data-stu-id="8c08d-128">**nx_dns_server_get** *Return the DNS Server in the Client list (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="8c08d-129">**nxd_dns_server_get** *클라이언트 목록에 DNS 서버 반환(IPv4 및 IPv6 주소 모두 지원)*</span><span class="sxs-lookup"><span data-stu-id="8c08d-129">**nxd_dns_server_get** *Return the DNS Server in the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="8c08d-130">**nx_dns_server_remove** *nxd_dns_server_remove가 클라이언트 목록에서 DNS 서버를 제거하는 래퍼 함수*</span><span class="sxs-lookup"><span data-stu-id="8c08d-130">**nx_dns_server_remove** *Wrapper function for nxd_dns_server_remove to remove a DNS Server from the Client list*</span></span>

- <span data-ttu-id="8c08d-131">**nxd_dns_server_remove** *클라이언트 목록에서 지정된 IP 주소의 DNS 서버 제거(IPv4 및 IPv6 주소 모두 지원)*</span><span class="sxs-lookup"><span data-stu-id="8c08d-131">**nxd_dns_server_remove** *Remove a DNS Server of the specified IP address from the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="8c08d-132">**nx_dns_server_remove_all** *클라이언트 목록에서 모든 DNS 서버 제거*</span><span class="sxs-lookup"><span data-stu-id="8c08d-132">**nx_dns_server_remove_all** *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="8c08d-133">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-133">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="8c08d-134">입력 호스트에 대한 권한 영역의 시작을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-134">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-135">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-135">Prototype</span></span>
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="8c08d-136">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-136">Description</span></span>

<span data-ttu-id="8c08d-137">NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 SOA 형식의 쿼리를 보내 입력 도메인 이름에 대한 권한 영역의 시작을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-137">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="8c08d-138">DNS 클라이언트에서 DNS 서버 응답에 반환된 SOA 레코드를 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-138">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="8c08d-139">데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-139">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="8c08d-140">NetX Duo DNS 클라이언트에서 NX_DNS_SOA_ENTRY SOA 레코드 유형은 7개의 4바이트 매개 변수(총 28바이트)로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-140">In NetX Duo DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="8c08d-141">**nx_dns_soa_host_mname_ptr** 이 영역의 기본 데이터 원본에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-141">**nx_dns_soa_host_mname_ptr** Pointer to primary source of data for this zone.</span></span>
- <span data-ttu-id="8c08d-142">**nx_dns_soa_host_rname_ptr** 이 영역을 담당하는 사서함에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-142">**nx_dns_soa_host_rname_ptr** Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="8c08d-143">**nx_dns_soa_serial** 영역 버전 번호</span><span class="sxs-lookup"><span data-stu-id="8c08d-143">**nx_dns_soa_serial** Zone version number</span></span>
- <span data-ttu-id="8c08d-144">**nx_dns_soa_refresh** 새로 고침 간격</span><span class="sxs-lookup"><span data-stu-id="8c08d-144">**nx_dns_soa_refresh** Refresh interval</span></span>
- <span data-ttu-id="8c08d-145">**nx_dns_soa_retry** SOA 쿼리 다시 시도 간 간격</span><span class="sxs-lookup"><span data-stu-id="8c08d-145">**nx_dns_soa_retry** Interval between SOA query retries</span></span>
- <span data-ttu-id="8c08d-146">**nx_dns_soa_expire** SOA가 만료되는 기간</span><span class="sxs-lookup"><span data-stu-id="8c08d-146">**nx_dns_soa_expire** Time duration when SOA expires</span></span>
- <span data-ttu-id="8c08d-147">**nx_dns_soa_minmum** SOA 호스트 이름 DNS 회신 메시지의 최소 TTL 필드</span><span class="sxs-lookup"><span data-stu-id="8c08d-147">**nx_dns_soa_minmum** Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="8c08d-148">두 SOA 레코드의 스토리지는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-148">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="8c08d-149">고정 길이 데이터가 포함된 SOA 레코드는 버퍼의 맨 위에서 시작하여 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-149">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="8c08d-150">MNAME 및 RNAME 포인터는 버퍼의 아래쪽에 저장된 가변 길이 데이터(호스트 이름)를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-150">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="8c08d-151">추가 SOA 레코드는 첫 번째 레코드("추가 SOA 레코드...") 뒤에 입력되며, 해당 가변 길이 데이터는 마지막 항목의 가변 길이 데이터("추가 SOA 가변 길이 데이터") 위에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-151">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![두 SOA 레코드의 스토리지](media/image4.png)

<span data-ttu-id="8c08d-153">*record_buffer* 입력에서 서버 회신의 모든 SOA 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-153">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="8c08d-154">\**record_count* 에서 반환된 SOA 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 데이터를 구문 분석하고 영역 권한 호스트 이름 문자열의 시작을 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-154">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-155">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-155">Input Parameters</span></span>

- <span data-ttu-id="8c08d-156">**dns_ptr** DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-156">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="8c08d-157">**host_name** SOA 데이터를 가져오는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-157">**host_name** Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="8c08d-158">**record_buffer** SOA 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-158">**record_buffer** Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="8c08d-159">**buffer_size** SOA 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="8c08d-159">**buffer_size** Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="8c08d-160">**record_count** 검색된 SOA 레코드 수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-160">**record_count** Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="8c08d-161">**wait_option** DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="8c08d-161">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-162">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-162">Return Values</span></span>

- <span data-ttu-id="8c08d-163">**NX_SUCCESS**(0x00) SOA 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="8c08d-163">**NX_SUCCESS** (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="8c08d-164">**NX_DNS_NO_SERVER**(0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="8c08d-164">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="8c08d-165">**NX_DNS_QUERY_FAILED**(0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-165">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="8c08d-166">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-166">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="8c08d-167">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8c08d-168">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-168">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-169">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-169">Allowed From</span></span>

<span data-ttu-id="8c08d-170">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-170">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-171">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-171">Example</span></span>
```C
UCHAR  record_buffer[50];
UINT   record_count;   
NX_DNS_SOA_ENTRY *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host. */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",  
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
         error_counter++;
}
else 
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SOA data 
       is returned in soa_buffer. */

    /* Set a local pointer to the SOA buffer. */
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;

    printf("------------------------------------------------------\n");
    printf("Test SOA: \n");
    printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
    printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
    printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
    printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
    printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );

    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
    {
        printf("host mname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
    }
    else
    {
        printf("host mame is not set\n");
    }

    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
    {
        printf("host rname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
    }
    else
    {
     
        printf("host rname is not set\n");
    }
}

[Output]
----------------------------------------------------
Test SOA: 
serial = 2012111212
refresh = 7200
retry = 1800
expire = 1209600
minmum = 300
host mname = ns1.www.my_example.com
host rname = dns-admin.www.my_example.com
```

## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="8c08d-172">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="8c08d-172">nx_dns_cache_initialize</span></span>

<span data-ttu-id="8c08d-173">DNS 캐시를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-173">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-174">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-174">Prototype</span></span>
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a><span data-ttu-id="8c08d-175">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-175">Description</span></span>

<span data-ttu-id="8c08d-176">이 서비스는 DNS 캐시를 만들고 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-176">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-177">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-177">Input Parameters</span></span>

- <span data-ttu-id="8c08d-178">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-178">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="8c08d-179">**cache_ptr** DNS 캐시에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-179">**cache_ptr** Pointer to DNS Cache.</span></span>
- <span data-ttu-id="8c08d-180">**cache_size** DNS 캐시 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="8c08d-180">**cache_size** Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-181">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-181">Return Values</span></span>

- <span data-ttu-id="8c08d-182">**NX_SUCCESS**(0x00) DNS 캐시를 성공적으로 초기화함</span><span class="sxs-lookup"><span data-stu-id="8c08d-182">**NX_SUCCESS** (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="8c08d-183">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-183">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="8c08d-184">NX_DNS_CACHE_ERROR (0xB7) 잘못된 캐시 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-184">NX_DNS_CACHE_ERROR (0xB7) Invalid Cache pointer.</span></span>
- <span data-ttu-id="8c08d-185">NX_PTR_ERROR (0x07) 잘못된 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-185">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span> 
- <span data-ttu-id="8c08d-186">NX_DNS_ERROR (0xA0) 캐시가 4바이트로 정렬되지 않음</span><span class="sxs-lookup"><span data-stu-id="8c08d-186">NX_DNS_ERROR (0xA0) Cache is not 4-byte aligned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-187">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-187">Allowed From</span></span>

<span data-ttu-id="8c08d-188">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-188">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-189">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-189">Example</span></span>
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="8c08d-190">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="8c08d-190">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="8c08d-191">DNS 캐시 전체 알림 함수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-191">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-192">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-192">Prototype</span></span>
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="8c08d-193">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-193">Description</span></span>

<span data-ttu-id="8c08d-194">이 서비스는 캐시 전체 알림 함수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-194">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-195">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-195">Input Parameters</span></span>

- <span data-ttu-id="8c08d-196">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-196">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-197">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-197">Return Values</span></span>

- <span data-ttu-id="8c08d-198">**NX_SUCCESS**(0x00) DNS 캐시 알림을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="8c08d-198">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="8c08d-199">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-199">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="8c08d-200">NX_PTR_ERROR (0x07) 잘못된 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-200">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-201">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-201">Allowed From</span></span>

<span data-ttu-id="8c08d-202">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-203">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-203">Example</span></span>
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="8c08d-204">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="8c08d-204">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="8c08d-205">DNS 캐시 전체 알림 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-205">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-206">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-206">Prototype</span></span>
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="8c08d-207">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-207">Description</span></span>

<span data-ttu-id="8c08d-208">이 서비스는 캐시 전체 알림 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-208">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-209">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-209">Input Parameters</span></span>

- <span data-ttu-id="8c08d-210">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-210">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="8c08d-211">**cache_full_notify_cb** 캐시가 가득 찰 때 호출하는 콜백 함수</span><span class="sxs-lookup"><span data-stu-id="8c08d-211">**cache_full_notify_cb** The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-212">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-212">Return Values</span></span>

- <span data-ttu-id="8c08d-213">**NX_SUCCESS**(0x00) DNS 캐시 알림을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="8c08d-213">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="8c08d-214">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-214">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="8c08d-215">NX_PTR_ERROR (0x07) 잘못된 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-215">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-216">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-216">Allowed From</span></span>

<span data-ttu-id="8c08d-217">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-218">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-218">Example</span></span>
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="8c08d-219">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-219">nx_dns_cname_get</span></span>

<span data-ttu-id="8c08d-220">입력 호스트 이름에 대한 정식 이름을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-220">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-221">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-221">Prototype</span></span>
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8c08d-222">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-222">Description</span></span>

<span data-ttu-id="8c08d-223">NX_DNS_ENABLE_EXTENDED_RR_TYPES가 *nxd_dns.h* 에 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 CNAME 형식의 쿼리를 보내 정식 도메인 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-223">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nxd_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="8c08d-224">DNS 클라이언트에서 DNS 서버 응답에 반환된 CNAME 문자열을 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-224">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-225">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-225">Input Parameters</span></span>

- <span data-ttu-id="8c08d-226">**dns_ptr** DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-226">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="8c08d-227">**host_name** CNAME 데이터를 가져오는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-227">**host_name** Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="8c08d-228">**record_buffer** CNAME 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-228">**record_buffer** Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="8c08d-229">**buffer_size** CNAME 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="8c08d-229">**buffer_size** Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="8c08d-230">**wait_option** DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="8c08d-230">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-231">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-231">Return Values</span></span>

- <span data-ttu-id="8c08d-232">**NX_SUCCESS**(0x00) CNAME 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="8c08d-232">**NX_SUCCESS** (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="8c08d-233">**NX_DNS_NO_SERVER**(0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="8c08d-233">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="8c08d-234">**NX_DNS_QUERY_FAILED**(0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-234">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="8c08d-235">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-235">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="8c08d-236">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-236">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8c08d-237">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-237">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-238">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-238">Allowed From</span></span>

<span data-ttu-id="8c08d-239">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-240">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-240">Example</span></span>
```C
CHAR            record _buffer[50];

/* Request the canonical name for the specified host. */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                   record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and 
   the canonical host name is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 

[Output]
----------------------------------------------------
Test CNAME: my_example.com
```

##  <a name="nx_dns_create"></a><span data-ttu-id="8c08d-241">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="8c08d-241">nx_dns_create</span></span>

<span data-ttu-id="8c08d-242">DNS 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-242">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-243">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-243">Prototype</span></span>
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a><span data-ttu-id="8c08d-244">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-244">Description</span></span>

<span data-ttu-id="8c08d-245">이 서비스는 이전에 만든 IP 인스턴스에 대한 DNS 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-245">This service creates a DNS Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c08d-246">애플리케이션에서 DNS 클라이언트가 사용하는 패킷 풀의 패킷 페이로드가 최대 512바이트의 DNS 메시지와 UDP, IP 및 이더넷 헤더를 수용할 수 있을 만큼 충분히 큰지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-246">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="8c08d-247">DNS 클라이언트에서 자체 패킷 풀을 만드는 경우 이 풀은 NX_DNS_PACKET_PAYLOAD 및 NX_DNS_PACKET_POOL_SIZE에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-247">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_PAYLOAD and NX_DNS_PACKET_POOL_SIZE.</span></span>

<span data-ttu-id="8c08d-248">DNS 클라이언트 애플리케이션에서 이전에 만든 패킷 풀을 제공하는 것을 선호하는 경우 IPv4 DNS 클라이언트에 대한 페이로드는 최대 DNS의 경우 512바이트, IP 헤더의 경우 20바이트, UDP 헤더의 경우 8바이트 및 이더넷 헤더의 경우 14바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-248">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span> <span data-ttu-id="8c08d-249">IPv6의 경우 유일한 차이점은 IP 헤더가 40바이트이므로 패킷은 40바이트의 IPv6 헤더를 수용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-249">For IPv6 the only difference is the IP header is 40 bytes, therefore the packet needs to accommodate the IPv6 header of 40 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-250">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-250">Input Parameters</span></span>

- <span data-ttu-id="8c08d-251">**dns_ptr** DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-251">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="8c08d-252">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-252">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="8c08d-253">**domain_name** DNS 인스턴스의 도메인 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-253">**domain_name** Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-254">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-254">Return Values</span></span>

- <span data-ttu-id="8c08d-255">**NX_SUCCESS**(0x00) DNS를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="8c08d-255">**NX_SUCCESS** (0x00) Successful DNS create</span></span>
- <span data-ttu-id="8c08d-256">**NX_DNS_ERROR**(0xA0) DNS 만들기 오류</span><span class="sxs-lookup"><span data-stu-id="8c08d-256">**NX_DNS_ERROR** (0xA0) DNS create error</span></span>
- <span data-ttu-id="8c08d-257">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-257">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="8c08d-258">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-258">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-259">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-259">Allowed From</span></span>

<span data-ttu-id="8c08d-260">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-260">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-261">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-261">Example</span></span>
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a><span data-ttu-id="8c08d-262">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="8c08d-262">nx_dns_delete</span></span>

<span data-ttu-id="8c08d-263">DNS 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-263">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-264">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-264">Prototype</span></span>
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="8c08d-265">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-265">Description</span></span>

<span data-ttu-id="8c08d-266">이 서비스는 이전에 만든 DNS 클라이언트 인스턴스를 삭제하고 해당 리소스를 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-266">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 

> [!NOTE]
> <span data-ttu-id="8c08d-267">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL이 정의되고 DNS 클라이언트에 사용자 정의 패킷 풀이 할당된 경우 더 이상 필요하지 않은 DNS 클라이언트 패킷 풀은 애플리케이션에서 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-267">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-268">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-268">Input Parameters</span></span>

- <span data-ttu-id="8c08d-269">**dns_ptr** 이전에 만든 DNS 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-269">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-270">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-270">Return Values</span></span>

- <span data-ttu-id="8c08d-271">**NX_SUCCESS**(0x00) DNS 클라이언트를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="8c08d-271">**NX_SUCCESS** (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="8c08d-272">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 클라이언트 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-272">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="8c08d-273">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-273">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-274">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-274">Allowed From</span></span>

<span data-ttu-id="8c08d-275">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-275">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-276">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-276">Example</span></span>
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="8c08d-277">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-277">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="8c08d-278">입력 도메인 영역에 대한 권한 있는 이름 서버를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-278">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-279">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-279">Prototype</span></span>
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8c08d-280">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-280">Description</span></span>

<span data-ttu-id="8c08d-281">NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 NS 형식의 쿼리를 보내 입력 도메인 이름에 대한 권한 있는 이름 서버를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-281">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="8c08d-282">DNS 클라이언트에서 DNS 서버 응답에 반환된 NS 레코드를 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-282">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="8c08d-283">데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-283">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="8c08d-284">NetX Duo DNS 클라이언트에서 NX_DNS_NS_ENTRY NS 데이터 형식은 2개의 4바이트 매개 변수로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-284">In NetX Duo DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="8c08d-285">**nx_dns_ns_ipv4_address** 이름 서버의 IPv4 주소</span><span class="sxs-lookup"><span data-stu-id="8c08d-285">**nx_dns_ns_ipv4_address** Name server’s IPv4 address</span></span>
- <span data-ttu-id="8c08d-286">**nx_dns_ns_hostname_ptr** 이름 서버의 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-286">**nx_dns_ns_hostname_ptr** Pointer to the name server’s hostname</span></span>

<span data-ttu-id="8c08d-287">아래에 표시된 버퍼에는 4개의 NX_DNS_NS_ENTRY 레코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-287">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="8c08d-288">각 항목의 호스트 이름 문자열에 대한 포인터는 버퍼의 아래쪽 절반에 있는 해당 호스트 이름 문자열을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-288">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![4개의 NX_DNS_NS_ENTRY 레코드를 포함합니다.](media/image5.png)

<span data-ttu-id="8c08d-290">*record_buffer* 입력에서 서버 회신의 모든 NS 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-290">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="8c08d-291">\**record_count* 에서 반환된 NS 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 각 레코드의 IP 주소와 호스트 이름을 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-291">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-292">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-292">Input Parameters</span></span>

- <span data-ttu-id="8c08d-293">**dns_ptr** DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-293">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="8c08d-294">**host_name** NS 데이터를 가져오는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-294">**host_name** Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="8c08d-295">**record_buffer** NS 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-295">**record_buffer** Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="8c08d-296">**buffer_size** NS 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="8c08d-296">**buffer_size** Size of buffer to hold NS data</span></span>
- <span data-ttu-id="8c08d-297">**record_count** 검색된 NS 레코드 수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-297">**record_count** Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="8c08d-298">**wait_option** DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="8c08d-298">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-299">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-299">Return Values</span></span>

- <span data-ttu-id="8c08d-300">**NX_SUCCESS**(0x00) NS 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="8c08d-300">**NX_SUCCESS** (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="8c08d-301">**NX_DNS_NO_SERVER**(0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="8c08d-301">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="8c08d-302">**NX_DNS_QUERY_FAILED**(0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-302">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="8c08d-303">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-303">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="8c08d-304">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-304">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="8c08d-305">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-305">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-306">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-306">Allowed From</span></span>

<span data-ttu-id="8c08d-307">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-308">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-308">Example</span></span>
```C
#define RECORD_COUNT    10

ULONG  record_buffer[50];
UINT   record_count;          
NX_DNS_NS_ENTRY  *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host. */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and NS data
   is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)
                               (record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                      nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address  >> 24,
                      nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,                   
                      nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                     nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
        {
            printf("hostname = %s\n", 
                    nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
                }
        else
            printf("hostname is not set\n");
    }
}

[Output]
------------------------------------------------------
Test NS: record_count = 4 
record 0: IP address: 192.2.2.10
hostname = ns2.www.my_example.com
record 1: IP address: 192.2.2.11
hostname = ns1.www.my_example.com
record 2: IP address: 192.2.2.12
hostname = ns3.www.my_example.com
record 3: IP address: 192.2.2.13
hostname = ns4.www.my_example.com
```

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="8c08d-309">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-309">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="8c08d-310">입력 호스트 이름에 대한 메일 교환을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-310">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-311">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-311">Prototype</span></span>
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8c08d-312">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-312">Description</span></span>

<span data-ttu-id="8c08d-313">NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 MX 형식의 쿼리를 보내 입력 도메인 이름에 대한 메일 교환을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-313">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="8c08d-314">DNS 클라이언트에서 DNS 서버 응답에 반환된 MX 레코드를 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-314">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="8c08d-315">데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-315">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="8c08d-316">NetX Duo DNS 클라이언트에서 NX_DNS_MAIL_EXCHANGE_ENTRY 메일 교환 레코드 유형은 4개의 매개 변수(총 12바이트)로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-316">In NetX Duo DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="8c08d-317">**nx_dns_mx_ipv4_address** 메일 교환 IPv4 주소 4바이트</span><span class="sxs-lookup"><span data-stu-id="8c08d-317">**nx_dns_mx_ipv4_address** Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="8c08d-318">**nx_dns_mx_preference** 기본 설정 2바이트</span><span class="sxs-lookup"><span data-stu-id="8c08d-318">**nx_dns_mx_preference** Preference 2 bytes</span></span>
- <span data-ttu-id="8c08d-319">**nx_dns_mx_reserved0** 예약 2바이트</span><span class="sxs-lookup"><span data-stu-id="8c08d-319">**nx_dns_mx_reserved0** Reserved 2 bytes</span></span>
- <span data-ttu-id="8c08d-320">**nx_dns_mx_hostname_ptr** 메일 교환 서버 호스트 이름 4바이트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-320">**nx_dns_mx_hostname_ptr** Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="8c08d-321">4개의 MX 레코드가 포함된 버퍼는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-321">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="8c08d-322">각 레코드에는 위 목록의 고정 길이 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-322">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="8c08d-323">메일 교환 서버 호스트 이름에 대한 포인터는 버퍼 아래쪽에 있는 해당 호스트 이름을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-323">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![4개의 MX 레코드를 포함하는 버퍼입니다.](media/image6.png)

<span data-ttu-id="8c08d-325">*record_buffer* 입력에서 서버 회신의 모든 MX 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-325">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="8c08d-326">\**record_count* 에서 반환된 MX 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 각 레코드의 메일 호스트 이름을 포함하여 MX 매개 변수를 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-326">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-327">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-327">Input Parameters</span></span>

- <span data-ttu-id="8c08d-328">**dns_ptr** DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-328">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="8c08d-329">**host_name** MX 데이터를 가져오는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-329">**host_name** Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="8c08d-330">**record_buffer** MX 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-330">**record_buffer** Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="8c08d-331">**buffer_size** MX 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="8c08d-331">**buffer_size** Size of buffer to hold MX data</span></span>
- <span data-ttu-id="8c08d-332">**record_count** 검색된 MX 레코드 수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-332">**record_count** Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="8c08d-333">**wait_option** DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="8c08d-333">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-334">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-334">Return Values</span></span>

- <span data-ttu-id="8c08d-335">**NX_SUCCESS**(0x00) MX 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="8c08d-335">**NX_SUCCESS** (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="8c08d-336">**NX_DNS_NO_SERVER**(0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="8c08d-336">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="8c08d-337">**NX_DNS_QUERY_FAILED**(0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-337">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="8c08d-338">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-338">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="8c08d-339">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-339">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="8c08d-340">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-340">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-341">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-341">Allowed From</span></span>

<span data-ttu-id="8c08d-342">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-343">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-343">Example</span></span>
```C
#define MAX_RECORD_COUNT 10

ULONG  record_buffer[50];
UINT   record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host. */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and MX
   data is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)
               (record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", 
                    nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
}


[Output]

-----------------------------------------------------
Test MX: record_count = 5 
record 0: IP address: 192.2.2.10
preference = 40 
hostname = alt3.aspmx.l.www.my_example.com
record 1: IP address: 192.2.2.11
preference = 50 
hostname = alt4.aspmx.l.www.my_example.com
record 2: IP address: 192.2.2.12
preference = 10 
hostname = aspmx.l.www.my_example.com
record 3: IP address: 192.2.2.13
preference = 20 
hostname = alt1.aspmx.l.www.my_example.com
record 4: IP address: 192.2.2.14
preference = 30 
hostname = alt2.aspmx.l.www.my_example.com
```

## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="8c08d-344">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-344">nx_dns_domain_service_get</span></span>

<span data-ttu-id="8c08d-345">입력 호스트 이름에서 제공하는 서비스를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-345">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-346">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-346">Prototype</span></span>
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8c08d-347">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-347">Description</span></span>

<span data-ttu-id="8c08d-348">NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 SRV 형식의 쿼리를 보내 지정된 도메인과 연결된 서비스 및 해당 포트 번호를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-348">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="8c08d-349">DNS 클라이언트에서 DNS 서버 응답에 반환된 SRV 레코드를 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-349">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="8c08d-350">데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-350">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="8c08d-351">NetX Duo DNS 클라이언트에서 NX_DNS_SRV_ENTRY 서비스 레코드 유형은 6개의 매개 변수(총 16바이트)로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-351">In NetX Duo DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="8c08d-352">이렇게 하면 가변 길이 SRV 데이터를 메모리 효율적인 방식으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-352">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="8c08d-353">**Server IPv4 address** nx_dns_srv_ipv4_address 4바이트</span><span class="sxs-lookup"><span data-stu-id="8c08d-353">**Server IPv4 address** nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="8c08d-354">**Server priority** nx_dns_srv_priority 2바이트</span><span class="sxs-lookup"><span data-stu-id="8c08d-354">**Server priority** nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="8c08d-355">**Server weight** nx_dns_srv_weight 2바이트</span><span class="sxs-lookup"><span data-stu-id="8c08d-355">**Server weight** nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="8c08d-356">**Service port number** nx_dns_srv_port_number 2바이트</span><span class="sxs-lookup"><span data-stu-id="8c08d-356">**Service port number** nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="8c08d-357">**Reserved for 4-byte alignment** nx_dns_srv_reserved0 2바이트</span><span class="sxs-lookup"><span data-stu-id="8c08d-357">**Reserved for 4-byte alignment** nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="8c08d-358">**Pointer to server host name** \*nx_dns_srv_hostname_ptr 4바이트</span><span class="sxs-lookup"><span data-stu-id="8c08d-358">**Pointer to server host name** \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="8c08d-359">4개의 SRV 레코드가 제공된 버퍼에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-359">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="8c08d-360">각 NX_DNS_SRV_ENTRY 레코드에는 레코드 버퍼의 아래쪽에 있는 해당 호스트 이름 문자열을 가리키는 *nx_dns_srv_hostname_ptr* 포인터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-360">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![SRV 레코드의 경우](media/image7.png)

<span data-ttu-id="8c08d-362">*record_buffer* 입력에서 서버 회신의 모든 SRV 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-362">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="8c08d-363">\**record_count* 에서 반환된 SRV 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 각 레코드의 서버 호스트 이름을 포함하여 SRV 매개 변수를 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-363">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-364">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-364">Input Parameters</span></span>

- <span data-ttu-id="8c08d-365">**dns_ptr** DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-365">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="8c08d-366">**host_name** SRV 데이터를 가져오는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-366">**host_name** Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="8c08d-367">**record_buffer** SRV 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-367">**record_buffer** Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="8c08d-368">**buffer_size** SRV 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="8c08d-368">**buffer_size** Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="8c08d-369">**record_count** 검색된 SRV 레코드 수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-369">**record_count** Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="8c08d-370">**wait_option** DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="8c08d-370">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-371">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-371">Return Values</span></span>

- <span data-ttu-id="8c08d-372">**NX_SUCCESS**(0x00) SRV 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="8c08d-372">**NX_SUCCESS** (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="8c08d-373">**NX_DNS_NO_SERVER**(0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="8c08d-373">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="8c08d-374">**NX_DNS_QUERY_FAILED**(0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-374">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="8c08d-375">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-375">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>
- <span data-ttu-id="8c08d-376">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-376">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="8c08d-377">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-377">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-378">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-378">Allowed From</span></span>

<span data-ttu-id="8c08d-379">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-380">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-380">Example</span></span>
```C
#define MAX_RECORD_COUNT  10

UCHAR  record_buffer[50];
UINT   record_count;          
NX_DNS_SRV_ENTRY *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host. */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data
       is returned in record_buffer. */

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);      

           
        /* Get the location of services. */
        for(i =0; i< record_count; i++)
        {
            nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)
                                    (record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

            printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,                   
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);

           printf("port number = %d\n", 
                   nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
           printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
           printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );

           if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
           {
                printf("hostname = %s\n", 
                        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
            }
           else
                printf("hostname is not set\n");
        }
}

[Output]
----------------------------------------------------
Test SRV: record_count = 3 
record 0: IP address: 192.2.2.10
port number = 5222
priority = 20
weight = 0
hostname = alt4.xmpp.l.www.my_example.com
record 1: IP address: 192.2.2.11
port number = 5222
priority = 5
weight = 0
hostname = xmpp.l.www.my_example.com
record 2: IP address: 192.2.2.12
port number = 5222
priority = 20
weight = 0
hostname = alt1.xmpp.l.www.my_example.com
```

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="8c08d-381">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="8c08d-381">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="8c08d-382">DNS 클라이언트의 서버 목록 크기를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-382">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-383">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-383">Prototype</span></span>
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a><span data-ttu-id="8c08d-384">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-384">Description</span></span>

<span data-ttu-id="8c08d-385">이 서비스는 클라이언트 목록에 있는 유효한 DNS 서버(IPv4 및 IPv6 모두)의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-385">This service returns the number of valid DNS Servers (both IPv4 and IPv6) in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-386">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-386">Input Parameters</span></span>

- <span data-ttu-id="8c08d-387">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-387">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="8c08d-388">**size** 목록의 서버 수 반환</span><span class="sxs-lookup"><span data-stu-id="8c08d-388">**size** Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-389">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-389">Return Values</span></span>

- <span data-ttu-id="8c08d-390">**NX_SUCCESS**(0x00) DNS 서버 목록 크기를 반환함</span><span class="sxs-lookup"><span data-stu-id="8c08d-390">**NX_SUCCESS** (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="8c08d-391">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-391">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="8c08d-392">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-392">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-393">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-393">Allowed From</span></span>

<span data-ttu-id="8c08d-394">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-394">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-395">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-395">Example</span></span>
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="8c08d-396">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-396">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="8c08d-397">호스트 이름으로 DNS 서버의 IP 주소 및 포트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-397">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-398">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-398">Prototype</span></span>
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8c08d-399">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-399">Description</span></span>

<span data-ttu-id="8c08d-400">이 서비스는 DNS 쿼리를 통해 입력 호스트 이름에 따라 서버 IP 및 포트(서비스 레코드)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-400">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="8c08d-401">서비스 레코드가 없는 경우 이 루틴은 입력 주소 포인터의 IP 주소를 0으로 반환하고, 오류 신호를 보내기 위해 0이 아닌 오류 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-401">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-402">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-402">Input Parameters</span></span>

- <span data-ttu-id="8c08d-403">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-403">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="8c08d-404">**host_name** 호스트 이름 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-404">**host_name** Pointer to host name buffer</span></span>
- <span data-ttu-id="8c08d-405">**host_address_ptr** 반환하는 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-405">**host_address_ptr** Pointer to address to return</span></span>
- <span data-ttu-id="8c08d-406">**host_port_ptr** 반환할 포트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-406">**host_port_ptr** Pointer to port to return</span></span>
- <span data-ttu-id="8c08d-407">**wait_option** DNS 응답에 대한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="8c08d-407">**wait_option** Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-408">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-408">Return Values</span></span>

- <span data-ttu-id="8c08d-409">**NX_SUCCESS**(0x00) DNS 서버 레코드를 성공적으로 반환함</span><span class="sxs-lookup"><span data-stu-id="8c08d-409">**NX_SUCCESS** (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="8c08d-410">**NX_DNS_NO_SERVER**(0xA1) 호스트 이름에 쿼리를 보내기 위해 클라이언트에 등록된 DNS 서버가 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-410">**NX_DNS_NO_SERVER** (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="8c08d-411">**NX_DNS_QUERY_FAILED**(0xA3) DNS 쿼리가 실패함. 클라이언트 목록의 DNS 서버에서 응답이 없거나 입력 호스트 이름에 사용할 수 있는 서비스 레코드가 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-411">**NX_DNS_QUERY_FAILED** (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="8c08d-412">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-412">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="8c08d-413">NX_CALLER_ERROR (0x11) 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-413">NX_CALLER_ERROR (0x11) Invalid caller</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-414">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-414">Allowed From</span></span>

<span data-ttu-id="8c08d-415">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-415">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-416">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-416">Example</span></span>
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="8c08d-417">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-417">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="8c08d-418">입력 호스트 이름에 대한 IPv4 주소를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-418">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-419">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-419">Prototype</span></span>
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8c08d-420">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-420">Description</span></span>

<span data-ttu-id="8c08d-421">이 서비스는 지정된 호스트 이름이 포함된 A 형식의 쿼리를 보내 입력 호스트 이름에 대한 IP 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-421">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="8c08d-422">DNS 클라이언트에서 DNS 서버 응답에 반환된 A 레코드의 IPv4 주소를 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-422">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="8c08d-423">데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-423">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="8c08d-424">아래와 같이 여러 IPv4 주소가 4바이트로 정렬된 버퍼에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-424">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![여러 주소 4바이트 정렬 버퍼](media/image8.png)

<span data-ttu-id="8c08d-426">제공된 버퍼에서 모든 IP 주소 데이터를 보유할 수 없는 경우 나머지 A 레코드는 *record_buffer* 에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-426">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="8c08d-427">이렇게 하면 애플리케이션에서 서버 회신에서 사용 가능한 IP 주소 데이터 중 하나, 일부 또는 모두를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-427">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="8c08d-428">\**record_count* 에서 반환된 A 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 IPv4 주소 데이터를 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-428">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-429">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-429">Input Parameters</span></span>

- <span data-ttu-id="8c08d-430">**dns_ptr** DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-430">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="8c08d-431">**host_name_ptr** IPv4 주소를 가져올 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-431">**host_name_ptr** Pointer to host name to obtain IPv4 address</span></span>
- <span data-ttu-id="8c08d-432">**buffer** IPv4 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-432">**buffer** Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="8c08d-433">**buffer_size** IPv4 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="8c08d-433">**buffer_size** Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="8c08d-434">**wait_option** DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="8c08d-434">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-435">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-435">Return Values</span></span>

- <span data-ttu-id="8c08d-436">**NX_SUCCESS**(0x00) IPv4 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="8c08d-436">**NX_SUCCESS** (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="8c08d-437">**NX_DNS_NO_SERVER**(0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="8c08d-437">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="8c08d-438">**NX_DNS_QUERY_FAILED**(0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-438">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="8c08d-439">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-439">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="8c08d-440">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-440">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8c08d-441">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-441">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-442">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-442">Allowed From</span></span>

<span data-ttu-id="8c08d-443">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-444">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-444">Example</span></span>
```C
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4
       address(es) is returned in record_buffer. */

          
            printf("------------------------------------------------------\n");
            printf("Test A: ");
            printf("record_count = %d \n", record_count);      


           /* Get the IPv4 addresses of host. */
           for(i =0; i< record_count; i++)
           {
                ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG)); 
                printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                    *ipv4_address_ptr[i] >> 24,
                    *ipv4_address_ptr[i] >> 16 & 0xFF,                   
                    *ipv4_address_ptr[i] >> 8 & 0xFF,
                    *ipv4_address_ptr[i] & 0xFF);
            }

}

[Output]

------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nxd_dns_ipv6_address_by_name_get"></a><span data-ttu-id="8c08d-445">nxd_dns_ipv6_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-445">nxd_dns_ipv6_address_by_name_get</span></span>

<span data-ttu-id="8c08d-446">입력 호스트 이름에 대한 IPv6 주소를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-446">Look up the IPv6 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-447">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-447">Prototype</span></span>
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8c08d-448">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-448">Description</span></span>

<span data-ttu-id="8c08d-449">이 서비스는 지정된 도메인 이름이 포함된 AAAA 형식의 쿼리를 보내 입력 도메인 이름에 대한 IP 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-449">This service sends a query of type AAAA with the specified domain name to obtain the IP addresses for the input domain name.</span></span> <span data-ttu-id="8c08d-450">DNS 클라이언트에서 DNS 서버 응답에 반환된 AAAA 레코드의 IPv6 주소를 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-450">The DNS Client copies the IPv6 address from the AAAA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="8c08d-451">데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-451">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="8c08d-452">4바이트 정렬된 버퍼에 저장되는 IPv6 주소의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-452">The format of IPv6 addresses stored in the 4-byte aligned buffer is shown below:</span></span>

![IPv6 형식 4바이트 정렬 버퍼](media/image9.png)

<span data-ttu-id="8c08d-454">*record_buffer* 입력에서 서버 회신의 모든 AAAA 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-454">If the input *record_buffer* cannot hold all the AAAA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="8c08d-455">\**record_count* 에서 반환된 AAAA 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 각 레코드의 IPv6 주소를 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-455">With the number of AAAA records returned in \**record_count,* the application can parse the IPv6 addresses from each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-456">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-456">Input Parameters</span></span>

- <span data-ttu-id="8c08d-457">**dns_ptr** DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-457">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="8c08d-458">**host_name_ptr** IPv6 주소를 가져올 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-458">**host_name_ptr** Pointer to host name to obtain IPv6 address</span></span>
- <span data-ttu-id="8c08d-459">**buffer** IPv6 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-459">**buffer** Pointer to location to extract IPv6 data into</span></span>
- <span data-ttu-id="8c08d-460">**buffer_size** IPv6 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="8c08d-460">**buffer_size** Size of buffer to hold IPv6 data</span></span>
- <span data-ttu-id="8c08d-461">**wait_option** DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="8c08d-461">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-462">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-462">Return Values</span></span>

- <span data-ttu-id="8c08d-463">**NX_SUCCESS**(0x00) IPv6 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="8c08d-463">**NX_SUCCESS** (0x00) Successfully obtained IPv6 data</span></span>
- <span data-ttu-id="8c08d-464">**NX_DNS_NO_SERVER**(0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="8c08d-464">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="8c08d-465">**NX_DNS_QUERY_FAILED**(0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-465">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="8c08d-466">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-466">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="8c08d-467">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8c08d-468">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-468">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-469">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-469">Allowed From</span></span>

<span data-ttu-id="8c08d-470">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-471">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-471">Example</span></span>
```C
#define      MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
NXD_ADDRESS    *ipv6_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nxd_dns_ipv6_address_by_name_get(&client_dns, 
                                           (UCHAR *)"www.my_example.com", 
                                           record__buffer,                  
                                           sizeof(record_buffer), 
                                           &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed the IPv6 
    address(es) is (are) returned in record_buffer. */
      
    printf("------------------------------------------------------\n");
    printf("Test AAAA: ");
    printf("record_count = %d \n", record_count);      

    /* Get the IPv6 addresses of host. */
    for(i =0; i< record_count; i++)
    {

        ipv6_address_ptr[i] = 
            (NX_DNS_IPV6_ADDRESS *)(record_buffer + i * sizeof(NX_DNS_IPV6_ADDRESS)); 
             
        printf("record %d: IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", i, 
                ipv6_address_ptr[i] -> ipv6_address[0]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[0]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  & 0xFFFF);
            }
}


[Output]
------------------------------------------------------
Test AAAA: record_count = 1 
record 0: IP address: 2001:0db8:0000:f101: 0000: 0000: 0000:01003
```

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="8c08d-472">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-472">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="8c08d-473">IP 주소에서 호스트 이름을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-473">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-474">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-474">Prototype</span></span>
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8c08d-475">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-475">Description</span></span>

<span data-ttu-id="8c08d-476">이 서비스는 애플리케이션에서 이전에 지정한 하나 이상의 DNS 서버에서 제공된 IP 주소에 대한 이름 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-476">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="8c08d-477">성공하면 NULL로 끝나는 호스트 이름이 *host_name_ptr* 에서 지정한 문자열에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-477">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span> <span data-ttu-id="8c08d-478">*Nxd_dns_host_by_address_get* 서비스에 대한 래퍼 함수이며 IPv6 주소를 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-478">This is a wrapper function for *nxd_dns_host_by_address_get* service and does not accept IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-479">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-479">Input Parameters</span></span>

- <span data-ttu-id="8c08d-480">**dns_ptr** 이전에 만든 DNS 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-480">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="8c08d-481">**ip_address** 이름으로 확인할 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8c08d-481">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="8c08d-482">**host_name_ptr** 호스트 이름의 대상 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-482">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="8c08d-483">**max_host_name_size** 호스트 이름에 대한 대상 영역의 크기</span><span class="sxs-lookup"><span data-stu-id="8c08d-483">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="8c08d-484">**wait_option** 서비스에서 각 DNS 쿼리 및 쿼리 다시 시도를 수행한 후 DNS 서버 응답을 기다리는 시간(타이머 틱 수)을 정의함</span><span class="sxs-lookup"><span data-stu-id="8c08d-484">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="8c08d-485">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-485">The wait options are defined as follows:</span></span>

  <span data-ttu-id="8c08d-486">시간 제한 값 (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8c08d-486">timeout value (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="8c08d-487">TX_WAIT_FOREVER를 선택하면 DNS 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-487">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="8c08d-488">숫자 값(1-0xFFFFFFFE)을 선택하면 DNS 확인을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-488">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-489">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-489">Return Values</span></span>

- <span data-ttu-id="8c08d-490">**NX_SUCCESS**(0x00) DNS를 성공적으로 확인함</span><span class="sxs-lookup"><span data-stu-id="8c08d-490">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="8c08d-491">**NX_DNS_TIMEOUT**(0xA2) DNS 뮤텍스를 가져오는 데 시간이 초과됨</span><span class="sxs-lookup"><span data-stu-id="8c08d-491">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="8c08d-492">**NX_DNS_NO_SERVER**(0xA1) DNS 서버 주소가 지정되지 않음</span><span class="sxs-lookup"><span data-stu-id="8c08d-492">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="8c08d-493">**NX_DNS_QUERY_FAILED**(0xA3) 쿼리에 대한 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-493">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="8c08d-494">**NX_DNS_BAD_ADDRESS_ERROR**(0xA4) Null 입력 주소</span><span class="sxs-lookup"><span data-stu-id="8c08d-494">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="8c08d-495">**NX_DNS_INVALID_ADDRESS_TYPE**(0xB2) 인덱스에서 잘못된 주소 유형(예: IPv6)을 가리킴</span><span class="sxs-lookup"><span data-stu-id="8c08d-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="8c08d-496">**NX_DNS_PARAM_ERROR**(0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-496">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="8c08d-497">**NX_DNS_IPV6_NOT_SUPPORTED**(0xB3) IPv6을 사용할 수 없는 경우 레코드를 처리할 수 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="8c08d-498">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-498">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8c08d-499">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-499">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-500">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-500">Allowed From</span></span>

<span data-ttu-id="8c08d-501">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-501">Threads</span></span>

<span data-ttu-id="8c08d-502">**예제**</span><span class="sxs-lookup"><span data-stu-id="8c08d-502">**Example**</span></span>
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a><span data-ttu-id="8c08d-503">nxd_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-503">nxd_dns_host_by_address_get</span></span>

<span data-ttu-id="8c08d-504">IP 주소에서 호스트 이름을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-504">Look up a host name from the IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-505">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-505">Prototype</span></span>
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8c08d-506">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-506">Description</span></span>

<span data-ttu-id="8c08d-507">이 서비스는 이전에 애플리케이션에서 지정한 하나 이상의 DNS 서버에서 *ip_address* 입력 인수에서 IPv6 또는 IPv4 주소의 이름 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-507">This service requests name resolution of the IPv6 or IPv4 address in the *ip_address* input argument from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="8c08d-508">성공하면 NULL로 끝나는 호스트 이름이 *host_name_ptr* 에서 지정한 문자열에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-508">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-509">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-509">Input Parameters</span></span>

- <span data-ttu-id="8c08d-510">**dns_ptr** 이전에 만든 DNS 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-510">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="8c08d-511">**ip_address** 이름으로 확인할 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8c08d-511">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="8c08d-512">**host_name_ptr** 호스트 이름의 대상 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-512">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="8c08d-513">**max_host_name_size** 호스트 이름에 대한 대상 영역의 크기</span><span class="sxs-lookup"><span data-stu-id="8c08d-513">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="8c08d-514">**wait_option** 서비스에서 각 DNS 쿼리 및 쿼리 다시 시도를 수행한 후 DNS 서버 응답을 기다리는 시간(타이머 틱 수)을 정의함</span><span class="sxs-lookup"><span data-stu-id="8c08d-514">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="8c08d-515">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-515">The wait options are defined as follows:</span></span>

  <span data-ttu-id="8c08d-516">시간 제한 값 (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8c08d-516">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="8c08d-517">TX_WAIT_FOREVER를 선택하면 DNS 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-517">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="8c08d-518">숫자 값(1-0xFFFFFFFE)을 선택하면 DNS 확인을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-518">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-519">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-519">Return Values</span></span>

- <span data-ttu-id="8c08d-520">**NX_SUCCESS**(0x00) DNS를 성공적으로 확인함</span><span class="sxs-lookup"><span data-stu-id="8c08d-520">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="8c08d-521">**NX_DNS_TIMEOUT**(0xA2) DNS 뮤텍스를 가져오는 데 시간이 초과됨</span><span class="sxs-lookup"><span data-stu-id="8c08d-521">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="8c08d-522">**NX_DNS_NO_SERVER**(0xA1) DNS 서버 주소가 지정되지 않음</span><span class="sxs-lookup"><span data-stu-id="8c08d-522">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="8c08d-523">**NX_DNS_QUERY_FAILED**(0xA3) 쿼리에 대한 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-523">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="8c08d-524">**NX_DNS_BAD_ADDRESS_ERROR**(0xA4) Null 입력 주소</span><span class="sxs-lookup"><span data-stu-id="8c08d-524">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="8c08d-525">**NX_DNS_IPV6_NOT_SUPPORTED**(0xB3) IPv6을 사용할 수 없는 경우 레코드를 처리할 수 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="8c08d-526">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-526">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="8c08d-527">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-527">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8c08d-528">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-528">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-529">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-529">Allowed From</span></span>

<span data-ttu-id="8c08d-530">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-530">Threads</span></span>

<span data-ttu-id="8c08d-531">**예제**</span><span class="sxs-lookup"><span data-stu-id="8c08d-531">**Example**</span></span>
```C
UCHAR   resolved_name[200];
NXD_ADDRESS host_address;

host_address.nxd_ip_version = NX_IP_VERISON_V6;
host_address.nxd_ip_address.v6[0] = 0x20010db8;
host_address.nxd_ip_address.v6[1] = 0x0;
host_address.nxd_ip_address.v6[2] = 0xf101;
host_address.nxd_ip-address.v6[3] = 0x108;

/* Get the name associated with theinput host_address. */
status =  nxd_dns_host_by_address_get(&my_dns, &host_address,
                                      resolved_name, sizeof(resolved_name), 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}     
else     
{
     printf("------------------------------------------------------\n");
     printf("Test PTR: %s\n", record_buffer);
}

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable. */


[Output]

 ------------------------------------------------------
 Test PTR: my_example.net
```

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="8c08d-532">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-532">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="8c08d-533">호스트 이름에서 IP 주소를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-533">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-534">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-534">Prototype</span></span>
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8c08d-535">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-535">Description</span></span>

<span data-ttu-id="8c08d-536">이 서비스는 애플리케이션에서 이전에 지정한 하나 이상의 DNS 서버에서 제공된 이름에 대한 이름 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-536">This service requests name resolution of the supplied name from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="8c08d-537">성공하면 연결된 IP 주소가 host_address_ptr가 가리키는 대상에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-537">If successful, the associated IP address is returned in the destination pointed to by host_address_ptr.</span></span> <span data-ttu-id="8c08d-538">*nxd_dns_host_by_name_get* 서비스에 대한 래퍼 함수이며 IPv4 주소 입력으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-538">This is a wrapper function for the *nxd_dns_host_by_name_get* service, and is limited to IPv4 address input.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-539">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-539">Input Parameters</span></span>

- <span data-ttu-id="8c08d-540">**dns_ptr** 이전에 만든 DNS 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-540">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="8c08d-541">**host_name** 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-541">**host_name** Pointer to host name</span></span>
- <span data-ttu-id="8c08d-542">**host_address_ptr** DNS 서버 IP 주소 반환됨</span><span class="sxs-lookup"><span data-stu-id="8c08d-542">**host_address_ptr** DNS Server IP address returned</span></span>
- <span data-ttu-id="8c08d-543">**wait_option** 서비스에서 DNS 확인을 기다리는 시간 정의</span><span class="sxs-lookup"><span data-stu-id="8c08d-543">**wait_option** Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="8c08d-544">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-544">The wait options are defined as follows:</span></span>

  <span data-ttu-id="8c08d-545">시간 제한 값 (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8c08d-545">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="8c08d-546">TX_WAIT_FOREVER를 선택하면 DNS 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-546">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="8c08d-547">숫자 값(1-0xFFFFFFFE)을 선택하면 DNS 확인을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-547">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-548">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-548">Return Values</span></span>

- <span data-ttu-id="8c08d-549">**NX_SUCCESS**(0x00) DNS를 성공적으로 확인함</span><span class="sxs-lookup"><span data-stu-id="8c08d-549">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="8c08d-550">**NX_DNS_NO_SERVER**(0xA1) DNS 서버 주소가 지정되지 않음</span><span class="sxs-lookup"><span data-stu-id="8c08d-550">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="8c08d-551">**NX_DNS_QUERY_FAILED**(0xA3) 쿼리에 대한 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-551">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="8c08d-552">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-552">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="8c08d-553">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-553">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8c08d-554">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-554">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-555">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-555">Allowed From</span></span>

<span data-ttu-id="8c08d-556">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-556">Threads</span></span>

<span data-ttu-id="8c08d-557">**예제**</span><span class="sxs-lookup"><span data-stu-id="8c08d-557">**Example**</span></span>
```C
ULONG host_address;

/* Get the IP address for the name “www.my_example.com”. */
   status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &host_address, 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found 
        in the “ip_address” variable. */
        
    printf("------------------------------------------------------\n");
    printf("Test A: \n");
    printf("IP address: %d.%d.%d.%d\n",
    host_address >> 24,
    host_address >> 16 & 0xFF,                   
    host_address >> 8 & 0xFF,
    host_address & 0xFF);
}

[Output]
 ------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nxd_dns_host_by_name_get"></a><span data-ttu-id="8c08d-558">nxd_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-558">nxd_dns_host_by_name_get</span></span>

<span data-ttu-id="8c08d-559">호스트 이름에서 IP 주소를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-559">Lookup an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-560">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-560">Prototype</span></span>
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a><span data-ttu-id="8c08d-561">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-561">Description</span></span>

<span data-ttu-id="8c08d-562">이 서비스는 애플리케이션에서 이전에 지정한 하나 이상의 DNS 서버에서 제공된 IP 주소에 대한 이름 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-562">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="8c08d-563">성공하면 연결된 IP 주소가 *host_address_ptr* 가 가리키는 NXD_ADDRESS에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-563">If successful, the associated IP address is returned in an NXD_ADDRESS pointed to by *host_address_ptr*.</span></span> <span data-ttu-id="8c08d-564">호출자가 lookup_type 입력을 NX_IP_VERSION_V6으로 설정하면 이 서비스는 호스트 IPv6 주소(AAAA 레코드)에 대한 쿼리를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-564">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V6, this service will send out query for a host IPv6 address (AAAA record).</span></span> <span data-ttu-id="8c08d-565">호출자가 lookup_type 입력을 NX_IP_VERSION_V4로 설정하면 이 서비스는 호스트 IPv4 주소(A 레코드)에 대한 쿼리를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-565">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V4, this service will send out query for a host IPv4 address (A record).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-566">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-566">Input Parameters</span></span>

- <span data-ttu-id="8c08d-567">**dns_ptr** 이전에 만든 DNS 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-567">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="8c08d-568">**host_name** IP 주소를 찾을 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-568">**host_name** Pointer to host name to find an IP address of</span></span>
- <span data-ttu-id="8c08d-569">**host_address_ptr** IP 주소를 포함하는 NXD_ADDRESS의 대상에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-569">**host_address_ptr** Pointer to destination for NXD_ADDRESS containing the IP address</span></span>
- <span data-ttu-id="8c08d-570">**wait_option** 각 쿼리 전송 및 재전송에 대한 DNS 서버 응답에 대한 타이머 틱에서 서비스가 대기하는 시간 정의</span><span class="sxs-lookup"><span data-stu-id="8c08d-570">**wait_option** Defines how long the service will wait in timer ticks for the DNS Server response for each query transmission and retransmission.</span></span> <span data-ttu-id="8c08d-571">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-571">The wait options are defined as follows:</span></span>

  <span data-ttu-id="8c08d-572">시간 제한 값 (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8c08d-572">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="8c08d-573">TX_WAIT_FOREVER를 선택하면 DNS 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-573">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS Server responds to the request.</span></span>

  <span data-ttu-id="8c08d-574">숫자 값(1-0xFFFFFFFE)을 선택하면 DNS 확인을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-574">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

- <span data-ttu-id="8c08d-575">**lookup_type** 조회 유형을 나타냄(A 대 AAAA)</span><span class="sxs-lookup"><span data-stu-id="8c08d-575">**lookup_type** Indicate type of lookup (A vs AAAA).</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-576">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-576">Return Values</span></span>

- <span data-ttu-id="8c08d-577">**NX_SUCCESS**(0x00) DNS를 성공적으로 확인함</span><span class="sxs-lookup"><span data-stu-id="8c08d-577">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="8c08d-578">**NX_DNS_NO_SERVER**(0xA1) DNS 서버 주소가 지정되지 않음</span><span class="sxs-lookup"><span data-stu-id="8c08d-578">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="8c08d-579">**NX_DNS_QUERY_FAILED**(0xA3) 쿼리에 대한 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-579">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="8c08d-580">**NX_DNS_BAD_ADDRESS_ERROR**(0xA4) Null 입력 주소</span><span class="sxs-lookup"><span data-stu-id="8c08d-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="8c08d-581">**NX_DNS_IPV6_NOT_SUPPORTED**(0xB3) IPv6을 사용할 수 없는 경우 레코드를 처리할 수 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="8c08d-582">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-582">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8c08d-583">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-583">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8c08d-584">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-584">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-585">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-585">Allowed From</span></span>

<span data-ttu-id="8c08d-586">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-586">Threads</span></span>

<span data-ttu-id="8c08d-587">**예제**</span><span class="sxs-lookup"><span data-stu-id="8c08d-587">**Example**</span></span>
```C
NXD_ADDRESS host_ipduo_address;

/* Create an AAAA query to obtain the IPv6 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, 
                                   &host_ipduo_address, 4000, 
                                   NX_IP_VERSION_V6);

if (status != NX_SUCCESS)
{
        error_counter++;
}
else
{
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */

    printf("------------------------------------------------------\n");
    printf("Test AAAA: \n");

    printf("IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", 
           host_ipduo_address.nxd_ip_address.v6[0]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[0]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  & 0xFFFF);
}

[Output]

------------------------------------------------------
Test AAAA: 
IP address: 2607:f8b0:4007:800:0:0:0:1008
```

<span data-ttu-id="8c08d-588">이 시간 서비스를 사용하는 또 다른 예(이번에는 IPv4 주소 및 A 레코드 유형 사용)는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-588">Another example of using this time service, this time using IPv4 addresses and A record types, is shown below:</span></span>
```C
/* Create a query to obtain the IPv4 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000, 
                                   NX_IP_VERSION_V4);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{   
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */
  
     printf("------------------------------------------------------\n");
     printf("Test A: \n");
     printf("IP address: %d.%d.%d.%d\n",
            host_ipduo_address.nxd_ip_address.v4 >> 24,
            host_ipduo_address.nxd_ip_address.v4 >> 16 & 0xFF,                   
            host_ipduo_address.nxd_ip_address.v4 >> 8 & 0xFF,
            host_ipduo_address.nxd_ip_address.v4 & 0xFF);
 }

[Output]

------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="8c08d-589">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-589">nx_dns_host_text_get</span></span>

<span data-ttu-id="8c08d-590">입력 도메인 이름에 대한 텍스트 문자열을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-590">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-591">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-591">Prototype</span></span>
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8c08d-592">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-592">Description</span></span>

<span data-ttu-id="8c08d-593">이 서비스는 지정된 호스트 이름 및 버퍼가 포함된 TXT 형식의 쿼리를 보내 임의의 문자열 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-593">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="8c08d-594">DNS 클라이언트에서 DNS 서버 응답에 반환된 TXT 레코드의 텍스트 문자열을 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-594">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="8c08d-595">데이터를 받기 위해 record_buffer를 4바이트로 정렬할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-595">The record_buffer does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-596">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-596">Input Parameters</span></span>

- <span data-ttu-id="8c08d-597">**dns_ptr** DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-597">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="8c08d-598">**host_name** 검색하는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-598">**host_name** Pointer to name of host to search on</span></span>
- <span data-ttu-id="8c08d-599">**record_buffer** TXT 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-599">**record_buffer** Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="8c08d-600">**buffer_size** TXT 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="8c08d-600">**buffer_size** Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="8c08d-601">**wait_option** DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="8c08d-601">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-602">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-602">Return Values</span></span>

- <span data-ttu-id="8c08d-603">**NX_SUCCESS**(0x00) TXT 문자열을 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="8c08d-603">**NX_SUCCESS** (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="8c08d-604">**NX_DNS_NO_SERVER**(0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="8c08d-604">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="8c08d-605">**NX_DNS_QUERY_FAILED**(0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="8c08d-605">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="8c08d-606">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-606">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8c08d-607">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-607">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8c08d-608">NX_DNS_PARAM_ERROR (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-608">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-609">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-609">Allowed From</span></span>

<span data-ttu-id="8c08d-610">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-610">Threads</span></span>

######   
<span data-ttu-id="8c08d-611">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-611">Example</span></span>
```C
CHAR            record_buffer[50];

/* Request the text string for the specified host. */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                               record_buffer, 
                               sizeof(record_buffer), 500);


/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and the
       text string is returned in record_buffer. */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 


[Output]

------------------------------------------------------
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="8c08d-612">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="8c08d-612">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="8c08d-613">DNS 클라이언트 패킷 풀 설정</span><span class="sxs-lookup"><span data-stu-id="8c08d-613">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-614">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-614">Prototype</span></span>
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="8c08d-615">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-615">Description</span></span>

<span data-ttu-id="8c08d-616">이 서비스는 이전에 만든 패킷 풀을 DNS 클라이언트 패킷 풀로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-616">This service sets a previously created packet pool as the DNS Client packet pool.</span></span> <span data-ttu-id="8c08d-617">DNS 클라이언트에서 이 패킷 풀을 사용하여 DNS 쿼리를 보내므로 패킷 페이로드는 이더넷, IP 및 UDP 헤더를 포함하고 *nxd_dns.h* 에 정의된 NX_DNS_PACKET_PAYLOAD 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-617">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD which includes the Ethernet, IP and UDP headers and is defined in *nxd_dns.h.*</span></span> 

> [!NOTE]
> <span data-ttu-id="8c08d-618">*D* NS 클라이언트가 삭제되면 패킷 풀이 함께 삭제되지 않으며, 더 이상 필요하지 않은 패킷 풀은 애플리케이션에서 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-618">*W* hen the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>
>
> <span data-ttu-id="8c08d-619">이 서비스는 NX_DNS_CLIENT_USER_CREATE_PACKET_POOL 구성 옵션이 *nxd_dns.h* 에 정의된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-619">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nxd_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-620">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-620">Input Parameters</span></span>

- <span data-ttu-id="8c08d-621">**dns_ptr** 이전에 만든 DNS 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-621">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="8c08d-622">**pool_ptr** 이전에 만든 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-622">**pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-623">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-623">Return Values</span></span>

- <span data-ttu-id="8c08d-624">**NX_SUCCESS**(0x00) 성공적으로 완료됨</span><span class="sxs-lookup"><span data-stu-id="8c08d-624">**NX_SUCCESS** (0x00) Successful completion.</span></span>
- <span data-ttu-id="8c08d-625">**NX_NOT_ENABLED**(0x14) 클라이언트가 이 옵션에 대해 구성되지 않음</span><span class="sxs-lookup"><span data-stu-id="8c08d-625">**NX_NOT_ENABLED** (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="8c08d-626">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 클라이언트 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-626">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="8c08d-627">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-627">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-628">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-628">Allowed From</span></span>

<span data-ttu-id="8c08d-629">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-629">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-630">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-630">Example</span></span>
```C
NXD_DNS my_dns;
NX_PACKET_POOL client_pool;
NX_IP *ip_ptr;


/* Create the DNS Client. */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client. */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool. */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set. */
```

## <a name="nx_dns_server_add"></a><span data-ttu-id="8c08d-631">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="8c08d-631">nx_dns_server_add</span></span>

<span data-ttu-id="8c08d-632">DNS 서버 IP 주소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-632">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-633">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-633">Prototype</span></span>
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="8c08d-634">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-634">Description</span></span>

<span data-ttu-id="8c08d-635">이 서비스는 IPv4 DNS 서버를 서버 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-635">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-636">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-636">Input Parameters</span></span>

- <span data-ttu-id="8c08d-637">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-637">**dns_ptr** Pointer to DNS control block.</span></span>  
- <span data-ttu-id="8c08d-638">**server_address** DNS 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8c08d-638">**server_address** IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-639">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-639">Return Values</span></span>

- <span data-ttu-id="8c08d-640">**NX_SUCCESS**(0x00) 서버를 성공적으로 추가함</span><span class="sxs-lookup"><span data-stu-id="8c08d-640">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="8c08d-641">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="8c08d-641">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="8c08d-642">**NX_NO_MORE_ENTRIES**(0x17) 더 이상 DNS 서버가 허용되지 않음(목록이 가득 참)</span><span class="sxs-lookup"><span data-stu-id="8c08d-642">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="8c08d-643">**NX_DNS_PARAM_ERROR**(0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-643">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="8c08d-644">**NX_DNS_IPV6_NOT_SUPPORTED**(0xB3) IPv6을 사용할 수 없는 경우 레코드를 처리할 수 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="8c08d-645">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-645">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8c08d-646">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-646">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8c08d-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null 서버 주소 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-648">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-648">Allowed From</span></span>

<span data-ttu-id="8c08d-649">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-650">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-650">Example</span></span>
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a><span data-ttu-id="8c08d-651">nxd_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="8c08d-651">nxd_dns_server_add</span></span>

<span data-ttu-id="8c08d-652">클라이언트 목록에 DNS 서버 추가</span><span class="sxs-lookup"><span data-stu-id="8c08d-652">Add DNS Server to the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-653">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-653">Prototype</span></span>
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="8c08d-654">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-654">Description</span></span>

<span data-ttu-id="8c08d-655">이 서비스는 DNS 서버의 IP 주소를 DNS 클라이언트 서버 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-655">This service adds the IP address of a DNS server to the DNS Client server list.</span></span> <span data-ttu-id="8c08d-656">server_address는 IPv4 또는 IPv6 주소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-656">The server_address may be either an IPv4 or IPv6 address.</span></span> <span data-ttu-id="8c08d-657">클라이언트가 IPv4 주소 또는 IPv6 주소로 동일한 서버에 액세스하려면 두 IP 주소 모두 서버 목록에 항목으로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-657">If the Client wishes to be able to access the same server by either its IPv4 address or IPv6 address it should add both IP addresses as entries to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-658">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-658">Input Parameters</span></span>

- <span data-ttu-id="8c08d-659">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-659">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="8c08d-660">**server_address** DNS 서버의 서버 IP 주소를 포함하는 NXD_ADDRESS에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-660">**server_address** Pointer to the NXD_ADDRESS containing the server IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-661">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-661">Return Values</span></span>

- <span data-ttu-id="8c08d-662">**NX_SUCCESS**(0x00) 서버를 성공적으로 추가함</span><span class="sxs-lookup"><span data-stu-id="8c08d-662">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="8c08d-663">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="8c08d-663">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="8c08d-664">**NX_NO_MORE_ENTRIES**(0x17) 더 이상 DNS 서버가 허용되지 않음(목록이 가득 참)</span><span class="sxs-lookup"><span data-stu-id="8c08d-664">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers allowed (list is full)</span></span> 
- <span data-ttu-id="8c08d-665">**NX_DNS_IPV6_NOT_SUPPORTED**(0xB3) IPv6을 사용할 수 없는 경우 레코드를 처리할 수 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="8c08d-666">**NX_DNS_PARAM_ERROR**(0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-666">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="8c08d-667">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-667">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8c08d-668">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-668">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8c08d-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null 서버 주소 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>
- <span data-ttu-id="8c08d-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) 인덱스에서 잘못된 주소 유형(예: IPv6)을 가리킴</span><span class="sxs-lookup"><span data-stu-id="8c08d-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-671">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-671">Allowed From</span></span>

<span data-ttu-id="8c08d-672">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-672">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-673">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-673">Example</span></span>
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Add a DNS Server with the IP address pointed to by the server_address input. */
status =  nxd_dns_server_add(&my_dns, &server_address);

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nx_dns_server_get"></a><span data-ttu-id="8c08d-674">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-674">nx_dns_server_get</span></span>

<span data-ttu-id="8c08d-675">클라이언트 목록에서 IPv4 DNS 서버를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-675">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-676">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-676">Prototype</span></span>
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="8c08d-677">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-677">Description</span></span>

<span data-ttu-id="8c08d-678">이 서비스는 지정된 인덱스의 서버 목록에서 IPv4 DNS 서버 주소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-678">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="8c08d-679">인덱스는 0부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-679">The index is zero based.</span></span> <span data-ttu-id="8c08d-680">입력 인덱스가 DNS 클라이언트 목록의 크기를 초과하는 경우 해당 인덱스에서 IPv6 주소가 발견되거나 지정된 인덱스에서 Null 주소가 발견되면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-680">If the input index exceeds the size of the DNS Client list, an IPv6 address is found at that index or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="8c08d-681">*nx_dns_get_serverlist_size* 서비스를 먼저 호출하여 클라이언트 목록의 DNS 서버 수를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-681">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

<span data-ttu-id="8c08d-682">이 서비스는 IPv4 주소만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-682">This service does only supports IPv4 addresses.</span></span> <span data-ttu-id="8c08d-683">IPv4 및 IPv6 주소를 모두 지원하는 *nxd_dns_server_get* 서비스를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-683">It calls the *nxd_dns_server_get* service which supports both IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-684">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-684">Input Parameters</span></span>

- <span data-ttu-id="8c08d-685">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-685">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="8c08d-686">**index** DNS 클라이언트의 서버 목록에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="8c08d-686">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="8c08d-687">**dns_server_address** DNS 서버의 IP 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-687">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-688">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-688">Return Values</span></span>

- <span data-ttu-id="8c08d-689">**NX_SUCCESS**(0x00) 서버를 성공적으로 반환함</span><span class="sxs-lookup"><span data-stu-id="8c08d-689">**NX_SUCCESS** (0x00) Successful server returned</span></span>
- <span data-ttu-id="8c08d-690">**NX_DNS_SERVER_NOT_FOUND**(0xA9) 인덱스에서 빈 슬롯을 가리킴</span><span class="sxs-lookup"><span data-stu-id="8c08d-690">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="8c08d-691">**NX_DNS_BAD_ADDRESS_ERROR**(0xA4) 인덱스에서 Null 주소를 가리킴</span><span class="sxs-lookup"><span data-stu-id="8c08d-691">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="8c08d-692">**NX_DNS_INVALID_ADDRESS_TYPE**(0xB2) 인덱스에서 잘못된 주소 유형(예: IPv6)을 가리킴</span><span class="sxs-lookup"><span data-stu-id="8c08d-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="8c08d-693">**NX_DNS_PARAM_ERROR**(0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-693">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="8c08d-694">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-694">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="8c08d-695">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-695">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-696">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-696">Allowed From</span></span>

<span data-ttu-id="8c08d-697">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-698">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-698">Example</span></span>
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a><span data-ttu-id="8c08d-699">nxd_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="8c08d-699">nxd_dns_server_get</span></span>

<span data-ttu-id="8c08d-700">클라이언트 목록에서 DNS 서버를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-700">Return a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-701">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-701">Prototype</span></span>
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="8c08d-702">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-702">Description</span></span>

<span data-ttu-id="8c08d-703">이 서비스는 지정된 인덱스의 서버 목록에서 DNS 서버 IP 주소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-703">This service returns the DNS Server IP address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="8c08d-704">인덱스는 0부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-704">The index is zero based.</span></span> <span data-ttu-id="8c08d-705">입력 인덱스가 DNS 클라이언트 목록의 크기를 초과하는 경우 지정된 인덱스에서 Null 주소가 발견되면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-705">If the input index exceeds the size of the DNS Client list, or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="8c08d-706">*nx_dns_get_serverlist_size* 서비스를 먼저 호출하여 서버 목록의 DNS 서버 수를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-706">The *nx_dns_get_serverlist_size* service may be called first to obtain the number of DNS servers in the server list.</span></span>

<span data-ttu-id="8c08d-707">이 서비스는 IPv4 및 IPv6 주소를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-707">This service supports IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-708">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-708">Input Parameters</span></span>

- <span data-ttu-id="8c08d-709">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-709">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="8c08d-710">**index** DNS 클라이언트의 서버 목록에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="8c08d-710">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="8c08d-711">**dns_server_address** DNS 서버의 IP 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-711">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-712">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-712">Return Values</span></span>

- <span data-ttu-id="8c08d-713">**NX_SUCCESS**(0x00) 서버 IP 주소를 성공적으로 반환함</span><span class="sxs-lookup"><span data-stu-id="8c08d-713">**NX_SUCCESS** (0x00) Successfully returned server IP address</span></span>
- <span data-ttu-id="8c08d-714">**NX_DNS_SERVER_NOT_FOUND**(0xA9) 인덱스에서 빈 슬롯을 가리킴</span><span class="sxs-lookup"><span data-stu-id="8c08d-714">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="8c08d-715">**NX_DNS_BAD_ADDRESS_ERROR**(0xA4) 인덱스에서 Null 서버 주소를 가리킴</span><span class="sxs-lookup"><span data-stu-id="8c08d-715">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to null server address</span></span>
- <span data-ttu-id="8c08d-716">**NX_DNS_INVALID_ADDRESS_TYPE**(0xB2) 인덱스에서 잘못된 주소 유형(예: IPv6)을 가리킴</span><span class="sxs-lookup"><span data-stu-id="8c08d-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="8c08d-717">**NX_DNS_PARAM_ERROR**(0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-717">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="8c08d-718">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-718">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="8c08d-719">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-719">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-720">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-720">Allowed From</span></span>

<span data-ttu-id="8c08d-721">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-721">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-722">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-722">Example</span></span>
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="8c08d-723">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="8c08d-723">nx_dns_server_remove</span></span>

<span data-ttu-id="8c08d-724">클라이언트 목록에서 IPv4 DNS 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-724">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-725">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-725">Prototype</span></span>
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="8c08d-726">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-726">Description</span></span>

<span data-ttu-id="8c08d-727">이 서비스는 클라이언트 목록에서 IPv4 DNS 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-727">This service removes an IPv4 DNS Server from the Client list.</span></span> <span data-ttu-id="8c08d-728">*Nxd_dns_server_remove* 에 대한 래퍼 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-728">It is a wrapper function for *nxd_dns_server_remove*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-729">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-729">Input Parameters</span></span>

- <span data-ttu-id="8c08d-730">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-730">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="8c08d-731">**server_address** DNS 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8c08d-731">**server_address** IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-732">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-732">Return Values</span></span>

- <span data-ttu-id="8c08d-733">**NX_SUCCESS**(0x00) DNS 서버를 성공적으로 제거함</span><span class="sxs-lookup"><span data-stu-id="8c08d-733">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="8c08d-734">**NX_DNS_SERVER_NOT_FOUND**(0xA9) 서버가 클라이언트 목록에 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-734">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="8c08d-735">**NX_DNS_BAD_ADDRESS_ERROR**(0xA4) Null 서버 주소 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="8c08d-736">**NX_DNS_IPV6_NOT_SUPPORTED**(0xB3) IPv6을 사용할 수 없는 경우 레코드를 처리할 수 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="8c08d-737">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-737">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="8c08d-738">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-738">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-739">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-739">Allowed From</span></span>

<span data-ttu-id="8c08d-740">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-740">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-741">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-741">Example</span></span>
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a><span data-ttu-id="8c08d-742">nxd_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="8c08d-742">nxd_dns_server_remove</span></span>

<span data-ttu-id="8c08d-743">클라이언트 목록에서 DNS 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-743">Remove a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-744">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-744">Prototype</span></span>
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="8c08d-745">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-745">Description</span></span>

<span data-ttu-id="8c08d-746">이 서비스는 클라이언트 목록에서 지정된 IP 주소의 DNS 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-746">This service removes a DNS Server of the specified IP address from the Client list.</span></span> <span data-ttu-id="8c08d-747">입력된 IP 주소는 IPv4 및 IPv6 주소를 모두 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-747">The input IP address accepts both IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="8c08d-748">서버를 제거하면 나머지 서버는 목록에서 한 인덱스 아래로 이동하여 빈 슬롯을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-748">After the server is removed, the remaining servers move down one index in the list to fill the vacated slot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-749">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-749">Input Parameters</span></span>

- <span data-ttu-id="8c08d-750">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-750">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="8c08d-751">**server_address** 서버 IP 주소를 포함하는 DNS 서버 NXD_ADDRESS 데이터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-751">**server_address** Pointer to DNS Server NXD_ADDRESS data containing server IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-752">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-752">Return Values</span></span>

- <span data-ttu-id="8c08d-753">**NX_SUCCESS**(0x00) DNS 서버를 성공적으로 제거함</span><span class="sxs-lookup"><span data-stu-id="8c08d-753">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="8c08d-754">**NX_DNS_SERVER_NOT_FOUND**(0xA9) 서버가 클라이언트 목록에 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-754">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="8c08d-755">**NX_DNS_BAD_ADDRESS_ERROR**(0xA4) Null 서버 주소 입력</span><span class="sxs-lookup"><span data-stu-id="8c08d-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="8c08d-756">**NX_DNS_IPV6_NOT_SUPPORTED**(0xB3) IPv6을 사용할 수 없는 경우 레코드를 처리할 수 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="8c08d-757">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-757">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="8c08d-758">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-758">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8c08d-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) 인덱스에서 잘못된 주소 유형(예: IPv6)을 가리킴</span><span class="sxs-lookup"><span data-stu-id="8c08d-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-760">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-760">Allowed From</span></span>

<span data-ttu-id="8c08d-761">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-761">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-762">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-762">Example</span></span>
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Remove the DNS Server at the specified IP address from the Client list. */
status =  nxd_dns_server_remove(&my_dns,&server_ADDRESS);

/* If status is NX_SUCCESS a DNS Server was successfully removed. */
```

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="8c08d-763">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="8c08d-763">nx_dns_server_remove_all</span></span>

<span data-ttu-id="8c08d-764">클라이언트 목록에서 모든 DNS 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-764">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="8c08d-765">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8c08d-765">Prototype</span></span>
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="8c08d-766">Description</span><span class="sxs-lookup"><span data-stu-id="8c08d-766">Description</span></span>

<span data-ttu-id="8c08d-767">이 서비스는 클라이언트 목록에서 모든 DNS 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8c08d-767">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8c08d-768">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8c08d-768">Input Parameters</span></span>

- <span data-ttu-id="8c08d-769">**dns_ptr** DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-769">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8c08d-770">반환 값</span><span class="sxs-lookup"><span data-stu-id="8c08d-770">Return Values</span></span>

- <span data-ttu-id="8c08d-771">**NX_SUCCESS**(0x00) DNS 서버를 성공적으로 제거함</span><span class="sxs-lookup"><span data-stu-id="8c08d-771">**NX_SUCCESS** (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="8c08d-772">**NX_DNS_ERROR**(0xA0) 보호 뮤텍스를 가져올 수 없음</span><span class="sxs-lookup"><span data-stu-id="8c08d-772">**NX_DNS_ERROR** (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="8c08d-773">NX_PTR_ERROR (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="8c08d-773">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="8c08d-774">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8c08d-774">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8c08d-775">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="8c08d-775">Allowed From</span></span>

<span data-ttu-id="8c08d-776">스레드</span><span class="sxs-lookup"><span data-stu-id="8c08d-776">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8c08d-777">예제</span><span class="sxs-lookup"><span data-stu-id="8c08d-777">Example</span></span>
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```