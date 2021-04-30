---
title: 챕터 3 - Azure RTOS NetX DNS 클라이언트 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX DNS 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 18e059e79f9742eaaafffbf15b55b4b5063363f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811568"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a><span data-ttu-id="5ec22-103">챕터 3 - Azure RTOS NetX DNS 클라이언트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="5ec22-103">Chapter 3 - Description of Azure RTOS NetX DNS Client Services</span></span>

<span data-ttu-id="5ec22-104">이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX DNS 서비스에 대해 알파벳 순서로 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="5ec22-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="5ec22-106">**nx_dns_authority_zone_start_get**: *지정된 호스트 이름과 연결된 권한 영역의 시작 조회*</span><span class="sxs-lookup"><span data-stu-id="5ec22-106">**nx_dns_authority_zone_start_get**: *Look up the start of a zone of authority associated with the specified host name*</span></span>
- <span data-ttu-id="5ec22-107">**nx_dns_cache_initialize**: *DNS 캐시 초기화*</span><span class="sxs-lookup"><span data-stu-id="5ec22-107">**nx_dns_cache_initialize**: *Initialize a DNS Cache.*</span></span>
- <span data-ttu-id="5ec22-108">**nx_dns_cache_notify_clear**: *캐시 전체 알림 함수 지우기*</span><span class="sxs-lookup"><span data-stu-id="5ec22-108">**nx_dns_cache_notify_clear**: *Clear the cache full notify function.*</span></span>
- <span data-ttu-id="5ec22-109">**nx_dns_cache_notify_set**: *캐시 전체 알림 함수 설정*</span><span class="sxs-lookup"><span data-stu-id="5ec22-109">**nx_dns_cache_notify_set**: *Set the cache full notify function.*</span></span>
- <span data-ttu-id="5ec22-110">**nx_dns_cname_get**: *입력 도메인 이름 별칭에 대한 정식 도메인 이름 조회*</span><span class="sxs-lookup"><span data-stu-id="5ec22-110">**nx_dns_cname_get**: *Look up the canonical domain name for the input domain name alias*</span></span>
- <span data-ttu-id="5ec22-111">**nx_dns_create**: *DNS 클라이언트 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="5ec22-111">**nx_dns_create**: *Create a DNS Client instance*</span></span>
- <span data-ttu-id="5ec22-112">**nx_dns_delete**: *DNS 클라이언트 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="5ec22-112">**nx_dns_delete**: *Delete a DNS Client instance*</span></span>
- <span data-ttu-id="5ec22-113">**nx_dns_domain_name_server_get**: *입력 도메인 영역에 대한 권한 있는 이름 서버 조회*</span><span class="sxs-lookup"><span data-stu-id="5ec22-113">**nx_dns_domain_name_server_get**: *Look up the authoritative name servers for the input domain zone*</span></span>
- <span data-ttu-id="5ec22-114">**nx_dns_domain_mail_exchange_get**: *지정된 호스트 이름과 연결된 메일 교환 조회*</span><span class="sxs-lookup"><span data-stu-id="5ec22-114">**nx_dns_domain_mail_exchange_get**: *Look up the mail exchange associated the specified host name.*</span></span>
- <span data-ttu-id="5ec22-115">**nx_dns_domain_service_get**: *지정된 호스트 이름과 연결된 서비스 조회*</span><span class="sxs-lookup"><span data-stu-id="5ec22-115">**nx_dns_domain_service_get**: *Look up the service(s) associated with the specified host name*</span></span>
- <span data-ttu-id="5ec22-116">**nx_dns_get_serverlist_size**: *DNS 클라이언트 서버 목록의 크기 반환*</span><span class="sxs-lookup"><span data-stu-id="5ec22-116">**nx_dns_get_serverlist_size**: *Return the size of the DNS Client server list*</span></span>
- <span data-ttu-id="5ec22-117">**nx_dns_info_by_name_get**: *IP 주소 반환, 입력 호스트 이름에 대한 포트 쿼리*</span><span class="sxs-lookup"><span data-stu-id="5ec22-117">**nx_dns_info_by_name_get**: *Return IP address, port querying on input host name*</span></span>
- <span data-ttu-id="5ec22-118">**nx_dns_ipv4_address_by_name_get**: *지정된 호스트 이름에서 IPv4 주소 조회*</span><span class="sxs-lookup"><span data-stu-id="5ec22-118">**nx_dns_ipv4_address_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="5ec22-119">**nx_dns_host_by_address_get**: *지정된 IP 주소에서 호스트 이름 조회*</span><span class="sxs-lookup"><span data-stu-id="5ec22-119">**nx_dns_host_by_address_get**: *Look up a host name from a specified IP address*</span></span>
- <span data-ttu-id="5ec22-120">**nx_dns_host_by_name_get**: *지정된 호스트 이름에서 IPv4 주소 조회*</span><span class="sxs-lookup"><span data-stu-id="5ec22-120">**nx_dns_host_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="5ec22-121">**nx_dns_host_text_get**: *입력 도메인 이름에 대한 텍스트 데이터 조회*</span><span class="sxs-lookup"><span data-stu-id="5ec22-121">**nx_dns_host_text_get**: *Look up the text data for the input domain name*</span></span>
- <span data-ttu-id="5ec22-122">**nx_dns_packet_pool_set**: *DNS 클라이언트 패킷 풀 설정*</span><span class="sxs-lookup"><span data-stu-id="5ec22-122">**nx_dns_packet_pool_set**: *Set the DNS Client packet pool*</span></span>
- <span data-ttu-id="5ec22-123">**nx_dns_server_add**: *클라이언트 목록에 지정된 주소의 DNS 서버 추가*</span><span class="sxs-lookup"><span data-stu-id="5ec22-123">**nx_dns_server_add**: *Add a DNS Server at the specified address to the Client list*</span></span>
- <span data-ttu-id="5ec22-124">**nx_dns_server_get**: *클라이언트 목록에서 DNS 서버 반환*</span><span class="sxs-lookup"><span data-stu-id="5ec22-124">**nx_dns_server_get**: *Return the DNS Server in the Client list*</span></span>
- <span data-ttu-id="5ec22-125">**nx_dns_server_remove**: *클라이언트 목록에서 DNS 서버 제거*</span><span class="sxs-lookup"><span data-stu-id="5ec22-125">**nx_dns_server_remove**: *Remove a DNS Server from the Client list*</span></span>
- <span data-ttu-id="5ec22-126">**nx_dns_server_remove_all**: *클라이언트 목록에서 모든 DNS 서버 제거*</span><span class="sxs-lookup"><span data-stu-id="5ec22-126">**nx_dns_server_remove_all**: *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="5ec22-127">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="5ec22-127">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="5ec22-128">입력 호스트에 대한 권한 영역의 시작을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-128">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-129">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-129">Prototype</span></span>

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="5ec22-130">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-130">Description</span></span>

<span data-ttu-id="5ec22-131">NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 SOA 형식의 쿼리를 보내 입력 도메인 이름에 대한 권한 영역의 시작을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-131">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="5ec22-132">DNS 클라이언트에서 DNS 서버 응답에 반환된 SOA 레코드를 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-132">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 
>[!NOTE]
> <span data-ttu-id="5ec22-133">데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-133">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="5ec22-134">NetX DNS 클라이언트에서 NX_DNS_SOA_ENTRY SOA 레코드 유형은 7개의 4바이트 매개 변수(총 28바이트)로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-134">In NetX DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="5ec22-135">**nx_dns_soa_host_mname_ptr**: 이 영역의 기본 데이터 원본에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-135">**nx_dns_soa_host_mname_ptr**: Pointer to primary source of data for this zone</span></span>
- <span data-ttu-id="5ec22-136">**nx_dns_soa_host_rname_ptr**: 이 영역을 담당하는 사서함에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-136">**nx_dns_soa_host_rname_ptr**: Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="5ec22-137">**nx_dns_soa_serial**: 영역 버전 번호</span><span class="sxs-lookup"><span data-stu-id="5ec22-137">**nx_dns_soa_serial**: Zone version number</span></span>
- <span data-ttu-id="5ec22-138">**nx_dns_soa_refresh**: 새로 고침 간격</span><span class="sxs-lookup"><span data-stu-id="5ec22-138">**nx_dns_soa_refresh**: Refresh interval</span></span>
- <span data-ttu-id="5ec22-139">**nx_dns_soa_retry**: SOA 쿼리 다시 시도 간 간격</span><span class="sxs-lookup"><span data-stu-id="5ec22-139">**nx_dns_soa_retry**: Interval between SOA query retries</span></span>
- <span data-ttu-id="5ec22-140">**nx_dns_soa_expire**: SOA가 만료되는 기간</span><span class="sxs-lookup"><span data-stu-id="5ec22-140">**nx_dns_soa_expire**: Time duration when SOA expires</span></span>
- <span data-ttu-id="5ec22-141">**nx_dns_soa_minmum**: SOA 호스트 이름 DNS 회신 메시지의 최소 TTL 필드</span><span class="sxs-lookup"><span data-stu-id="5ec22-141">**nx_dns_soa_minmum**: Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="5ec22-142">두 개의 SOA 레코드에 대한 저장은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-142">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="5ec22-143">고정 길이 데이터가 포함된 SOA 레코드는 버퍼의 맨 위에서 시작하여 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-143">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="5ec22-144">MNAME 및 RNAME 포인터는 버퍼의 아래쪽에 저장된 가변 길이 데이터(호스트 이름)를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-144">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="5ec22-145">추가 SOA 레코드는 첫 번째 레코드("추가 SOA 레코드...") 뒤에 입력되며, 해당 가변 길이 데이터는 마지막 항목의 가변 길이 데이터("추가 SOA 가변 길이 데이터") 위에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-145">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![두 개의 SOA 레코드에 대한 저장을 나타내는 다이어그램](media/image2.png)

<span data-ttu-id="5ec22-147">*record_buffer* 입력에서 서버 회신의 모든 SOA 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-147">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="5ec22-148">\**record_count* 에서 반환된 SOA 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 데이터를 구문 분석하고 영역 권한 호스트 이름 문자열의 시작을 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-148">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-149">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-149">Input Parameters</span></span>

- <span data-ttu-id="5ec22-150">**dns_ptr**: DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-150">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="5ec22-151">**host_name**: SOA 데이터를 가져오는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-151">**host_name**: Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="5ec22-152">**record_buffer**: SOA 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-152">**record_buffer**: Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="5ec22-153">**buffer_size**: SOA 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="5ec22-153">**buffer_size**: Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="5ec22-154">**record_count**: 검색된 SOA 레코드 수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-154">**record_count**: Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="5ec22-155">**wait_option**: DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="5ec22-155">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-156">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-156">Return Values</span></span>

- <span data-ttu-id="5ec22-157">**NX_SUCCESS**: (0x00) SOA 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="5ec22-157">**NX_SUCCESS**: (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="5ec22-158">**NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="5ec22-158">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="5ec22-159">**NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="5ec22-159">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="5ec22-160">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-160">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="5ec22-161">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-161">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="5ec22-162">NX_DNS_PARAM_ERROR: (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-162">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-163">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-163">Allowed From</span></span>

<span data-ttu-id="5ec22-164">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-164">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-165">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-165">Example</span></span>
```c
UCHAR                  record_buffer[50];
UINT                   record_count;   
NX_DNS_SOA_ENTRY       *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host.  */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else 
{
/* If status is NX_SUCCESS a DNS query was successfully completed and SOA data is returned in soa_buffer.  */

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

```

```Output
Test SOA:
serial = 2012111212
refresh = 7200
retry = 1800
expire = 1209600
minmum = 300
host mname = ns1.www.my_example.com
host rname = dns-admin.www.my_example.com
```


## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="5ec22-166">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="5ec22-166">nx_dns_cache_initialize</span></span>

<span data-ttu-id="5ec22-167">DNS 캐시를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-167">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-168">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-168">Prototype</span></span>

```c
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                             VOID *cache_ptr, UINT cache_size);

```
### <a name="description"></a><span data-ttu-id="5ec22-169">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-169">Description</span></span>

<span data-ttu-id="5ec22-170">이 서비스는 DNS 캐시를 만들고 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-170">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-171">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-171">Input Parameters</span></span>

- <span data-ttu-id="5ec22-172">**dns_ptr**: DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-172">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="5ec22-173">**cache_ptr**: DNS 캐시에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-173">**cache_ptr**: Pointer to DNS Cache.</span></span>
- <span data-ttu-id="5ec22-174">**cache_size**: DNS 캐시 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="5ec22-174">**cache_size**: Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-175">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-175">Return Values</span></span>

- <span data-ttu-id="5ec22-176">**NX_SUCCESS**: (0x00) DNS 캐시를 성공적으로 초기화함</span><span class="sxs-lookup"><span data-stu-id="5ec22-176">**NX_SUCCESS**: (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="5ec22-177">NX_DNS_ERROR: (0xA0) 캐시가 4바이트로 정렬되지 않음</span><span class="sxs-lookup"><span data-stu-id="5ec22-177">NX_DNS_ERROR: (0xA0) Cache is not 4-byte aligned.</span></span>
- <span data-ttu-id="5ec22-178">NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID</span><span class="sxs-lookup"><span data-stu-id="5ec22-178">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="5ec22-179">NX_PTR_ERROR: (0x07) 잘못된 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-179">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>
- <span data-ttu-id="5ec22-180">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-180">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-181">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-181">Allowed From</span></span>

<span data-ttu-id="5ec22-182">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-183">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-183">Example</span></span>
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="5ec22-184">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="5ec22-184">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="5ec22-185">DNS 캐시 전체 알림 함수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-185">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-186">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-186">Prototype</span></span>

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="5ec22-187">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-187">Description</span></span>

<span data-ttu-id="5ec22-188">이 서비스는 캐시 전체 알림 함수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-188">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-189">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-189">Input Parameters</span></span>

- <span data-ttu-id="5ec22-190">**dns_ptr**: DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-190">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-191">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-191">Return Values</span></span>

- <span data-ttu-id="5ec22-192">**NX_SUCCESS**: (0x00) DNS 캐시 알림을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="5ec22-192">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="5ec22-193">NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID</span><span class="sxs-lookup"><span data-stu-id="5ec22-193">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="5ec22-194">NX_PTR_ERROR: (0x07) 잘못된 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-194">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-195">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-195">Allowed From</span></span>

<span data-ttu-id="5ec22-196">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-197">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-197">Example</span></span>

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="5ec22-198">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="5ec22-198">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="5ec22-199">DNS 캐시 전체 알림 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-199">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-200">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-200">Prototype</span></span>

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="5ec22-201">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-201">Description</span></span>

<span data-ttu-id="5ec22-202">이 서비스는 캐시 전체 알림 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-202">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-203">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-203">Input Parameters</span></span>

- <span data-ttu-id="5ec22-204">**dns_ptr**: DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-204">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="5ec22-205">**cache_full_notify_cb**: 캐시가 가득 찰 때 호출하는 콜백 함수</span><span class="sxs-lookup"><span data-stu-id="5ec22-205">**cache_full_notify_cb**: The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-206">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-206">Return Values</span></span>

- <span data-ttu-id="5ec22-207">**NX_SUCCESS**: (0x00) DNS 캐시 알림을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="5ec22-207">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="5ec22-208">NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID</span><span class="sxs-lookup"><span data-stu-id="5ec22-208">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="5ec22-209">NX_PTR_ERROR: (0x07) 잘못된 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-209">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-210">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-210">Allowed From</span></span>

<span data-ttu-id="5ec22-211">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-212">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-212">Example</span></span>

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="5ec22-213">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="5ec22-213">nx_dns_cname_get</span></span>

<span data-ttu-id="5ec22-214">입력 호스트 이름에 대한 정식 이름을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-214">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-215">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-215">Prototype</span></span>
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5ec22-216">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-216">Description</span></span>

<span data-ttu-id="5ec22-217">NX_DNS_ENABLE_EXTENDED_RR_TYPES가 *nx_dns.h* 에 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 CNAME 형식의 쿼리를 보내 정식 도메인 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-217">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nx_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="5ec22-218">DNS 클라이언트에서 DNS 서버 응답에 반환된 CNAME 문자열을 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-218">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-219">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-219">Input Parameters</span></span>

- <span data-ttu-id="5ec22-220">**dns_ptr**: DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-220">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="5ec22-221">**host_name**: CNAME 데이터를 가져오는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-221">**host_name**: Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="5ec22-222">**record_buffer**: CNAME 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-222">**record_buffer**: Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="5ec22-223">**buffer_size**: CNAME 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="5ec22-223">**buffer_size**: Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="5ec22-224">**wait_option**: DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="5ec22-224">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-225">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-225">Return Values</span></span>

- <span data-ttu-id="5ec22-226">**NX_SUCCESS**: (0x00) CNAME 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="5ec22-226">**NX_SUCCESS**: (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="5ec22-227">**NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="5ec22-227">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="5ec22-228">**NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="5ec22-228">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="5ec22-229">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-229">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="5ec22-230">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-230">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="5ec22-231">NX_DNS_PARAM_ERROR: (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-231">NX_DNS_PARAM_ERROR: (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-232">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-232">Allowed From</span></span>

<span data-ttu-id="5ec22-233">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-234">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-234">Example</span></span>

```c
CHAR            record _buffer[50];

/* Request the canonical name for the specified host.  */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                            record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the canonical host name is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 
```

```Output
Test CNAME: **my_example**.com
```

## <a name="nx_dns_create"></a><span data-ttu-id="5ec22-235">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="5ec22-235">nx_dns_create</span></span>

<span data-ttu-id="5ec22-236">DNS 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-236">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-237">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-237">Prototype</span></span>

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="5ec22-238">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-238">Description</span></span>

<span data-ttu-id="5ec22-239">이 서비스는 이전에 만든 IP 인스턴스에 대한 DNS 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-239">This service creates a DNS Client instance for the previously created IP instance.</span></span>

>[!NOTE]
><span data-ttu-id="5ec22-240">애플리케이션에서 DNS 클라이언트가 사용하는 패킷 풀의 패킷 페이로드가 최대 512바이트의 DNS 메시지와 UDP, IP 및 이더넷 헤더를 수용할 수 있을 만큼 충분히 큰지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-240">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="5ec22-241">DNS 클라이언트에서 자체 패킷 풀을 만드는 경우 이 풀은 NX_DNS_PACKET_POOL_SIZE 및 NX_DNS_PACKET_PAYLOAD에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-241">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_POOL_SIZE and NX_DNS_PACKET_PAYLOAD.</span></span> <span data-ttu-id="5ec22-242">DNS 클라이언트 애플리케이션에서 이전에 만든 패킷 풀을 제공하는 것을 선호하는 경우 IPv4 DNS 클라이언트에 대한 페이로드는 최대 DNS의 경우 512바이트, IP 헤더의 경우 20바이트, UDP 헤더의 경우 8바이트 및 이더넷 헤더의 경우 14바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-242">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-243">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-243">Input Parameters</span></span>

- <span data-ttu-id="5ec22-244">**dns_ptr**: DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-244">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="5ec22-245">**ip_ptr**: 이전에 만든 IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-245">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="5ec22-246">**domain_name**: DNS 인스턴스의 도메인 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-246">**domain_name**: Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-247">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-247">Return Values</span></span>

- <span data-ttu-id="5ec22-248">**NX_SUCCESS**: (0x00) DNS를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="5ec22-248">**NX_SUCCESS**: (0x00) Successful DNS create</span></span>
- <span data-ttu-id="5ec22-249">**NX_DNS_ERROR**: (0xA0) DNS 만들기 오류</span><span class="sxs-lookup"><span data-stu-id="5ec22-249">**NX_DNS_ERROR**: (0xA0) DNS create error</span></span>
- <span data-ttu-id="5ec22-250">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-250">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="5ec22-251">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-251">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-252">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-252">Allowed From</span></span>

<span data-ttu-id="5ec22-253">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-253">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-254">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-254">Example</span></span>

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a><span data-ttu-id="5ec22-255">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="5ec22-255">nx_dns_delete</span></span>

<span data-ttu-id="5ec22-256">DNS 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-256">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-257">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-257">Prototype</span></span>

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="5ec22-258">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-258">Description</span></span>

<span data-ttu-id="5ec22-259">이 서비스는 이전에 만든 DNS 클라이언트 인스턴스를 삭제하고 해당 리소스를 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-259">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 
>[!NOTE]
> <span data-ttu-id="5ec22-260">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** 이 정의되고 DNS 클라이언트에 사용자 정의 패킷 풀이 할당된 경우 더 이상 필요하지 않은 DNS 클라이언트 패킷 풀은 애플리케이션에서 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-260">If **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-261">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-261">Input Parameters</span></span>

- <span data-ttu-id="5ec22-262">**dns_ptr**: 이전에 만든 DNS **클라이언트** 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-262">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-263">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-263">Return Values</span></span>

- <span data-ttu-id="5ec22-264">**NX_SUCCESS**: (0x00) DNS 클라이언트를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="5ec22-264">**NX_SUCCESS**: (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="5ec22-265">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 클라이언트 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-265">NX_PTR_ERROR: (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="5ec22-266">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-266">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-267">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-267">Allowed From</span></span>

<span data-ttu-id="5ec22-268">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-269">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-269">Example</span></span>

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="5ec22-270">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="5ec22-270">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="5ec22-271">입력 도메인 영역에 대한 권한 있는 이름 서버를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-271">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-272">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-272">Prototype</span></span>

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5ec22-273">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-273">Description</span></span>

<span data-ttu-id="5ec22-274">NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 NS 형식의 쿼리를 보내 입력 도메인 이름에 대한 권한 있는 이름 서버를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-274">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="5ec22-275">DNS 클라이언트에서 DNS 서버 응답에 반환된 NS 레코드를 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-275">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="5ec22-276">데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-276">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="5ec22-277">NetX DNS 클라이언트에서 NX_DNS_NS_ENTRY NS 데이터 형식은 두 개의 4바이트 매개 변수로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-277">In NetX DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="5ec22-278">**nx_dns_ns_ipv4_address**: 이름 서버의 IPv4 주소</span><span class="sxs-lookup"><span data-stu-id="5ec22-278">**nx_dns_ns_ipv4_address**: Name server’s IPv4 address</span></span>
- <span data-ttu-id="5ec22-279">**nx_dns_ns_hostname_ptr**: 이름 서버의 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-279">**nx_dns_ns_hostname_ptr**: Pointer to the name server’s hostname</span></span>

<span data-ttu-id="5ec22-280">아래에 표시된 버퍼에는 4개의 NX_DNS_NS_ENTRY 레코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-280">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="5ec22-281">각 항목의 호스트 이름 문자열에 대한 포인터는 버퍼의 아래쪽 절반에 있는 해당 호스트 이름 문자열을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-281">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![4개의 NX DNS NS 항목 레코드가 포함된 버퍼에 대한 다이어그램](media/image3.png)

<span data-ttu-id="5ec22-283">*record_buffer* 입력에서 서버 회신의 모든 NS 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-283">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="5ec22-284">\**record_count* 에서 반환된 NS 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 각 레코드의 IP 주소와 호스트 이름을 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-284">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-285">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-285">Input Parameters</span></span>

- <span data-ttu-id="5ec22-286">**dns_ptr**: DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-286">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="5ec22-287">**host_name**: NS 데이터를 가져오는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-287">**host_name**: Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="5ec22-288">**record_buffer**: NS 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-288">**record_buffer**: Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="5ec22-289">**buffer_size**: NS 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="5ec22-289">**buffer_size**: Size of buffer to hold NS data</span></span>
- <span data-ttu-id="5ec22-290">**record_count**: 검색된 NS 레코드 수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-290">**record_count**: Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="5ec22-291">**wait_option**: DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="5ec22-291">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-292">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-292">Return Values</span></span>

- <span data-ttu-id="5ec22-293">**NX_SUCCESS**: (0x00) NS 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="5ec22-293">**NX_SUCCESS**: (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="5ec22-294">**NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="5ec22-294">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="5ec22-295">**NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="5ec22-295">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="5ec22-296">NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID</span><span class="sxs-lookup"><span data-stu-id="5ec22-296">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="5ec22-297">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-297">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="5ec22-298">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-298">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-299">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-299">Allowed From</span></span>

<span data-ttu-id="5ec22-300">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-300">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-301">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-301">Example</span></span>
```c
#define RECORD_COUNT        10

ULONG                      record_buffer[50];
UINT                       record_count;          
NX_DNS_NS_ENTRY            *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host.  */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and NS data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

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
```

```Output
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

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="5ec22-302">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="5ec22-302">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="5ec22-303">입력 호스트 이름에 대한 메일 교환을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-303">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-304">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-304">Prototype</span></span>
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="5ec22-305">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-305">Description</span></span>

<span data-ttu-id="5ec22-306">NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 MX 형식의 쿼리를 보내 입력 도메인 이름에 대한 메일 교환을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-306">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="5ec22-307">DNS 클라이언트에서 DNS 서버 응답에 반환된 MX 레코드를 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-307">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

>[!NOTE]
><span data-ttu-id="5ec22-308">데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-308">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="5ec22-309">NetX DNS 클라이언트에서 NX_DNS_MAIL_EXCHANGE_ENTRY 메일 교환 레코드 유형은 4개의 매개 변수(총 12바이트)로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-309">In NetX DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="5ec22-310">**nx_dns_mx_ipv4_address**: 메일 교환 IPv4 주소 4바이트</span><span class="sxs-lookup"><span data-stu-id="5ec22-310">**nx_dns_mx_ipv4_address**: Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="5ec22-311">**nx_dns_mx_preference**: 기본 설정 2바이트</span><span class="sxs-lookup"><span data-stu-id="5ec22-311">**nx_dns_mx_preference**: Preference 2 bytes</span></span>
- <span data-ttu-id="5ec22-312">**nx_dns_mx_reserved0**: 예약 2바이트</span><span class="sxs-lookup"><span data-stu-id="5ec22-312">**nx_dns_mx_reserved0**: Reserved 2 bytes</span></span>
- <span data-ttu-id="5ec22-313">**nx_dns_mx_hostname_ptr**: 메일 교환 서버 호스트 이름 4바이트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-313">**nx_dns_mx_hostname_ptr**: Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="5ec22-314">4개의 MX 레코드가 포함된 버퍼는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-314">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="5ec22-315">각 레코드에는 위 목록의 고정 길이 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-315">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="5ec22-316">메일 교환 서버 호스트 이름에 대한 포인터는 버퍼 아래쪽에 있는 해당 호스트 이름을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-316">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![4개의 MX 레코드가 포함된 버퍼를 보여 주는 다이어그램](media/image4.png)

<span data-ttu-id="5ec22-318">*record_buffer* 입력에서 서버 회신의 모든 MX 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-318">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="5ec22-319">\**record_count* 에서 반환된 MX 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 각 레코드의 메일 호스트 이름을 포함하여 MX 매개 변수를 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-319">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-320">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-320">Input Parameters</span></span>

- <span data-ttu-id="5ec22-321">**dns_ptr**: DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-321">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="5ec22-322">**host_name**: MX 데이터를 가져오는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-322">**host_name**: Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="5ec22-323">**record_buffer**: MX 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-323">**record_buffer**: Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="5ec22-324">**buffer_size**: MX 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="5ec22-324">**buffer_size**: Size of buffer to hold MX data</span></span>
- <span data-ttu-id="5ec22-325">**record_count**: 검색된 MX 레코드 수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-325">**record_count**: Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="5ec22-326">**wait_option**: DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="5ec22-326">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-327">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-327">Return Values</span></span>

- <span data-ttu-id="5ec22-328">**NX_SUCCESS**: (0x00) MX 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="5ec22-328">**NX_SUCCESS**: (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="5ec22-329">**NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="5ec22-329">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="5ec22-330">**NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="5ec22-330">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="5ec22-331">NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID</span><span class="sxs-lookup"><span data-stu-id="5ec22-331">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="5ec22-332">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-332">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="5ec22-333">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-333">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-334">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-334">Allowed From</span></span>

<span data-ttu-id="5ec22-335">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-335">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-336">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-336">Example</span></span>
```c
#define           MAX_RECORD_COUNT 10

ULONG             record_buffer[50];
UINT              record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host.  */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and MX data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)(record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
    }
}
```

```Output
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


## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="5ec22-337">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="5ec22-337">nx_dns_domain_service_get</span></span>

<span data-ttu-id="5ec22-338">입력 호스트 이름에서 제공하는 서비스를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-338">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-339">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-339">Prototype</span></span>

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5ec22-340">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-340">Description</span></span>

<span data-ttu-id="5ec22-341">NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 SRV 형식의 쿼리를 보내 지정된 도메인과 연결된 서비스 및 해당 포트 번호를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-341">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="5ec22-342">DNS 클라이언트에서 DNS 서버 응답에 반환된 SRV 레코드를 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-342">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="5ec22-343">데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-343">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="5ec22-344">NetX DNS 클라이언트에서 NX_DNS_SRV_ENTRY 서비스 레코드 유형은 6개의 매개 변수(총 16바이트)로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-344">In NetX DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="5ec22-345">이렇게 하면 가변 길이 SRV 데이터를 메모리 효율적인 방식으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-345">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="5ec22-346">**Server IPv4 address**: nx_dns_srv_ipv4_address 4바이트</span><span class="sxs-lookup"><span data-stu-id="5ec22-346">**Server IPv4 address**: nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="5ec22-347">**Server priority**: nx_dns_srv_priority 2바이트</span><span class="sxs-lookup"><span data-stu-id="5ec22-347">**Server priority**: nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="5ec22-348">**Server weight**: nx_dns_srv_weight 2바이트</span><span class="sxs-lookup"><span data-stu-id="5ec22-348">**Server weight**: nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="5ec22-349">**Service port number**: nx_dns_srv_port_number 2바이트</span><span class="sxs-lookup"><span data-stu-id="5ec22-349">**Service port number**: nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="5ec22-350">**Reserved for 4-byte alignment**: nx_dns_srv_reserved0 2바이트</span><span class="sxs-lookup"><span data-stu-id="5ec22-350">**Reserved for 4-byte alignment**: nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="5ec22-351">**Pointer to server host name**: \*nx_dns_srv_hostname_ptr 4바이트</span><span class="sxs-lookup"><span data-stu-id="5ec22-351">**Pointer to server host name**: \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="5ec22-352">4개의 SRV 레코드가 제공된 버퍼에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-352">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="5ec22-353">각 NX_DNS_SRV_ENTRY 레코드에는 레코드 버퍼의 아래쪽에 있는 해당 호스트 이름 문자열을 가리키는 *nx_dns_srv_hostname_ptr* 포인터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-353">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![제공된 버퍼에 저장된 4개의 SRV 레코드에 대한 다이어그램](media/image5.png)

<span data-ttu-id="5ec22-355">*record_buffer* 입력에서 서버 회신의 모든 SRV 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-355">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="5ec22-356">\**record_count* 에서 반환된 SRV 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 각 레코드의 서버 호스트 이름을 포함하여 SRV 매개 변수를 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-356">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-357">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-357">Input Parameters</span></span>

- <span data-ttu-id="5ec22-358">**dns_ptr**: DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-358">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="5ec22-359">**host_name**: SRV 데이터를 가져오는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-359">**host_name**: Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="5ec22-360">**record_buffer**: SRV 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-360">**record_buffer**: Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="5ec22-361">**buffer_size**: SRV 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="5ec22-361">**buffer_size**: Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="5ec22-362">**record_count**: 검색된 SRV 레코드 수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-362">**record_count**: Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="5ec22-363">**wait_option**: DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="5ec22-363">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-364">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-364">Return Values</span></span>

- <span data-ttu-id="5ec22-365">**NX_SUCCESS**: (0x00) SRV 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="5ec22-365">**NX_SUCCESS**: (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="5ec22-366">**NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="5ec22-366">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="5ec22-367">**NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="5ec22-367">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="5ec22-368">NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID</span><span class="sxs-lookup"><span data-stu-id="5ec22-368">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="5ec22-369">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-369">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="5ec22-370">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-371">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-371">Allowed From</span></span>

<span data-ttu-id="5ec22-372">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-373">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-373">Example</span></span>

```c
#define MAX_RECORD_COUNT  10

UCHAR                  record_buffer[50];
UINT                   record_count;
NX_DNS_SRV_ENTRY       *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host.  */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test SRV: ");
    printf("record_count = %d \n", record_count);      

       
    /* Get the location of services.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

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
```

```Output
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

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="5ec22-374">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="5ec22-374">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="5ec22-375">DNS 클라이언트의 서버 목록 크기를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-375">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-376">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-376">Prototype</span></span>

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a><span data-ttu-id="5ec22-377">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-377">Description</span></span>

<span data-ttu-id="5ec22-378">이 서비스는 클라이언트 목록에 있는 유효한 DNS 서버의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-378">This service returns the number of valid DNS Servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-379">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-379">Input Parameters</span></span>

- <span data-ttu-id="5ec22-380">**dns_ptr**: DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-380">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="5ec22-381">**size**: 목록의 서버 수 반환</span><span class="sxs-lookup"><span data-stu-id="5ec22-381">**size**: Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-382">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-382">Return Values</span></span>

- <span data-ttu-id="5ec22-383">**NX_SUCCESS**: (0x00) DNS 서버 목록 크기를 반환함</span><span class="sxs-lookup"><span data-stu-id="5ec22-383">**NX_SUCCESS**: (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="5ec22-384">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-384">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="5ec22-385">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-385">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-386">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-386">Allowed From</span></span>

<span data-ttu-id="5ec22-387">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-388">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-388">Example</span></span>

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="5ec22-389">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="5ec22-389">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="5ec22-390">호스트 이름으로 DNS 서버의 IP 주소 및 포트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-390">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-391">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-391">Prototype</span></span>

```c
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5ec22-392">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-392">Description</span></span>

<span data-ttu-id="5ec22-393">이 서비스는 DNS 쿼리를 통해 입력 호스트 이름에 따라 서버 IP 및 포트(서비스 레코드)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-393">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="5ec22-394">서비스 레코드가 없는 경우 이 루틴은 입력 주소 포인터의 IP 주소를 0으로 반환하고, 오류 신호를 보내기 위해 0이 아닌 오류 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-394">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-395">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-395">Input Parameters</span></span>

- <span data-ttu-id="5ec22-396">**dns_ptr**: DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-396">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="5ec22-397">**host_name**: 호스트 이름 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-397">**host_name**: Pointer to host name buffer</span></span>
- <span data-ttu-id="5ec22-398">**host_address_ptr**: 반환하는 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-398">**host_address_ptr**: Pointer to address to return</span></span>
- <span data-ttu-id="5ec22-399">**host_port_ptr**: DNS 응답에 대한 wait_option 대기 옵션을 반환하는 포트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-399">**host_port_ptr**: Pointer to port to return wait_option Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-400">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-400">Return Values</span></span>

- <span data-ttu-id="5ec22-401">**NX_SUCCESS**: (0x00) DNS 서버 레코드를 성공적으로 반환함</span><span class="sxs-lookup"><span data-stu-id="5ec22-401">**NX_SUCCESS**: (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="5ec22-402">**NX_DNS_NO_SERVER**: (0xA1) 호스트 이름에 쿼리를 보내기 위해 클라이언트에 등록된 DNS 서버가 없음</span><span class="sxs-lookup"><span data-stu-id="5ec22-402">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="5ec22-403">**NX_DNS_QUERY_FAILED**: (0xA3) DNS 쿼리가 실패함. 클라이언트 목록의 DNS 서버에서 응답이 없거나 입력 호스트 이름에 사용할 수 있는 서비스 레코드가 없음</span><span class="sxs-lookup"><span data-stu-id="5ec22-403">**NX_DNS_QUERY_FAILED**: (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="5ec22-404">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-404">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="5ec22-405">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-405">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-406">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-406">Allowed From</span></span>

<span data-ttu-id="5ec22-407">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-407">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-408">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-408">Example</span></span>
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="5ec22-409">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="5ec22-409">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="5ec22-410">입력 호스트 이름에 대한 IPv4 주소를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-410">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-411">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-411">Prototype</span></span>

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5ec22-412">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-412">Description</span></span>

<span data-ttu-id="5ec22-413">이 서비스는 지정된 호스트 이름이 포함된 A 형식의 쿼리를 보내 입력 호스트 이름에 대한 IP 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-413">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="5ec22-414">DNS 클라이언트에서 DNS 서버 응답에 반환된 A 레코드의 IPv4 주소를 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-414">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="5ec22-415">데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-415">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="5ec22-416">아래와 같이 여러 IPv4 주소가 4바이트로 정렬된 버퍼에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-416">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![4바이트로 정렬되는 버퍼에 저장된 여러 IPv4 주소의 다이어그램](media/image6.png)

<span data-ttu-id="5ec22-418">제공된 버퍼에서 모든 IP 주소 데이터를 보유할 수 없는 경우 나머지 A 레코드는 *record_buffer* 에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-418">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="5ec22-419">이렇게 하면 애플리케이션에서 서버 회신에서 사용 가능한 IP 주소 데이터 중 하나, 일부 또는 모두를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-419">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="5ec22-420">\**record_count* 에서 반환된 A 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 IPv4 주소 데이터를 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-420">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-421">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-421">Input Parameters</span></span>

- <span data-ttu-id="5ec22-422">**dns_ptr**: DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-422">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="5ec22-423">**host_name_ptr**: IPv4 주소 버퍼를 가져오는 호스트 이름에 대한 포인터 및 IPv4 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-423">**host_name_ptr**: Pointer to host name to obtain IPv4 address buffer Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="5ec22-424">**buffer_size**: IPv4 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="5ec22-424">**buffer_size**: Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="5ec22-425">**wait_option**: DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="5ec22-425">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-426">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-426">Return Values</span></span>

- <span data-ttu-id="5ec22-427">**NX_SUCCESS**: (0x00) IPv4 데이터를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="5ec22-427">**NX_SUCCESS**: (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="5ec22-428">**NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="5ec22-428">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="5ec22-429">**NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="5ec22-429">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="5ec22-430">NX_DNS_PARAM_ERROR: (0xA8) 잘못된 입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-430">NX_DNS_PARAM_ERROR: (0xA8) Invalid input parameter.</span></span>
- <span data-ttu-id="5ec22-431">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-431">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="5ec22-432">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-432">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-433">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-433">Allowed From</span></span>

<span data-ttu-id="5ec22-434">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-434">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-435">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-435">Example</span></span>

```c
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host.  */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

        /* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4 address(es) is returned in record_buffer.  */
    printf("------------------------------------------------------\n");
    printf("Test A: ");
    printf("record_count = %d \n", record_count);      


    /* Get the IPv4 addresses of host.  */
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
```

```Output
------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="5ec22-436">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="5ec22-436">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="5ec22-437">IP 주소에서 호스트 이름을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-437">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-438">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-438">Prototype</span></span>

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5ec22-439">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-439">Description</span></span>

<span data-ttu-id="5ec22-440">이 서비스는 애플리케이션에서 이전에 지정한 하나 이상의 DNS 서버에서 제공된 IP 주소에 대한 이름 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-440">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="5ec22-441">성공하면 NULL로 끝나는 호스트 이름이 *host_name_ptr* 에서 지정한 문자열에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-441">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-442">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-442">Input Parameters</span></span>

- <span data-ttu-id="5ec22-443">**dns_ptr**: 이전에 만든 DNS 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-443">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="5ec22-444">**ip_address**: 이름으로 확인할 IP 주소</span><span class="sxs-lookup"><span data-stu-id="5ec22-444">**ip_address**: IP address to resolve into a name</span></span>
- <span data-ttu-id="5ec22-445">**host_name_ptr**: 호스트 이름의 대상 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-445">**host_name_ptr**: Pointer to destination area for host name</span></span>
- <span data-ttu-id="5ec22-446">**max_host_name_size**: 호스트 이름에 대한 대상 영역의 크기</span><span class="sxs-lookup"><span data-stu-id="5ec22-446">**max_host_name_size**: Size of destination area for host name</span></span>
- <span data-ttu-id="5ec22-447">**wait_option**: 서비스에서 각 DNS 쿼리 및 쿼리 다시 시도를 수행한 후 DNS 서버 응답을 기다리는 시간(타이머 틱 수)을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-447">**wait_option**: Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry The wait options are defined as follows:</span></span>
    - <span data-ttu-id="5ec22-448">**시간 제한 값**: (0x00000001-0xFFFFFFFE) 숫자 값(1-0xFFFFFFFE)을 선택하면 DNS 확인을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-448">**timeout value**: (0x00000001-0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="5ec22-449">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 DNS 서버에서 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-449">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-450">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-450">Return Values</span></span>

- <span data-ttu-id="5ec22-451">**NX_SUCCESS**: (0x00) DNS를 성공적으로 확인함</span><span class="sxs-lookup"><span data-stu-id="5ec22-451">**NX_SUCCESS**: (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="5ec22-452">**NX_DNS_TIMEOUT**: (0xA2) DNS 뮤텍스를 가져오는 데 시간이 초과됨</span><span class="sxs-lookup"><span data-stu-id="5ec22-452">**NX_DNS_TIMEOUT**: (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="5ec22-453">**NX_DNS_NO_SERVER**: (0xA1) DNS 서버 주소가 지정 되지 않음</span><span class="sxs-lookup"><span data-stu-id="5ec22-453">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="5ec22-454">**NX_DNS_QUERY_FAILED**: (0xA3) 쿼리에 대한 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="5ec22-454">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="5ec22-455">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null 입력 주소</span><span class="sxs-lookup"><span data-stu-id="5ec22-455">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null input address</span></span>
- <span data-ttu-id="5ec22-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) 인덱스에서 잘못된 주소 유형(예: IPv6)을 가리킴</span><span class="sxs-lookup"><span data-stu-id="5ec22-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="5ec22-457">**NX_DNS_PARAM_ERROR**: (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-457">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="5ec22-458">NX_PTR_ERROR: (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-458">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5ec22-459">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-459">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-460">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-460">Allowed From</span></span>

<span data-ttu-id="5ec22-461">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-461">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-462">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-462">Example</span></span>

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="5ec22-463">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="5ec22-463">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="5ec22-464">호스트 이름에서 IP 주소를 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-464">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-465">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-465">Prototype</span></span>

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5ec22-466">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-466">Description</span></span>

<span data-ttu-id="5ec22-467">이 서비스는 애플리케이션에서 이전에 지정한 하나 이상의 DNS 서버에서 *host_name* 이 가리키는 제공된 이름에 대한 이름 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-467">This service requests name resolution of the supplied name, pointed to by *host_name*, from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="5ec22-468">성공하면 연결된 IP 주소가 *host_address_ptr* 이 가리키는 대상에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-468">If successful, the associated IP address is returned in the destination pointed to by *host_address_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-469">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-469">Input Parameters</span></span>

- <span data-ttu-id="5ec22-470">**dns_ptr**: 이전에 만든 DNS 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-470">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="5ec22-471">**host_name**: 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-471">**host_name**: Pointer to host name</span></span>
- <span data-ttu-id="5ec22-472">**host_address_ptr**: DNS 호스트 IP 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-472">**host_address_ptr**: Pointer to DNS host IP address</span></span>
- <span data-ttu-id="5ec22-473">**wait_option**: 서비스에서 DNS 확인을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-473">**wait_option**: Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="5ec22-474">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-474">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="5ec22-475">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE) 숫자 값(1-0xFFFFFFFE)을 선택하면 DNS 확인을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-475">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="5ec22-476">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 DNS 서버에서 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-476">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-477">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-477">Return Values</span></span>

- <span data-ttu-id="5ec22-478">**NX_SUCCESS**: (0x00) DNS를 성공적으로 확인함</span><span class="sxs-lookup"><span data-stu-id="5ec22-478">**NX_SUCCESS**: (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="5ec22-479">**NX_DNS_NO_SERVER**: (0xA1) DNS 서버 주소가 지정 되지 않음</span><span class="sxs-lookup"><span data-stu-id="5ec22-479">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="5ec22-480">**NX_DNS_QUERY_FAILED**: (0xA3) 쿼리에 대한 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="5ec22-480">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="5ec22-481">NX_DNS_PARAM_ERROR: (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-481">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="5ec22-482">NX_PTR_ERROR: (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-482">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5ec22-483">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-483">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-484">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-484">Allowed From</span></span>

<span data-ttu-id="5ec22-485">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-485">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-486">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-486">Example</span></span>
```c
ULONG ip_address;

    /* Get the IP address for the name “www.my_example.com”.  */
    status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000);

    /* Check for DNS query error.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else     
    {

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found in the “ip_address” variable.  */
        
        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %d.%d.%d.%d\n",
                host_ip_address >> 24,
                host_ip_address >> 16 & 0xFF,                   
                host_ip_address >> 8 & 0xFF,
                host_ip_address & 0xFF);
    }
```

```Output
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="5ec22-487">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="5ec22-487">nx_dns_host_text_get</span></span>

<span data-ttu-id="5ec22-488">입력 도메인 이름에 대한 텍스트 문자열을 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-488">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-489">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-489">Prototype</span></span>

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5ec22-490">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-490">Description</span></span>

<span data-ttu-id="5ec22-491">이 서비스는 지정된 호스트 이름 및 버퍼가 포함된 TXT 형식의 쿼리를 보내 임의의 문자열 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-491">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="5ec22-492">DNS 클라이언트에서 DNS 서버 응답에 반환된 TXT 레코드의 텍스트 문자열을 *record_buffer* 메모리 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-492">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="5ec22-493">데이터를 받기 위해 *record_buffer* 를 4바이트로 정렬할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-493">The *record_buffer* does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-494">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-494">Input Parameters</span></span>

- <span data-ttu-id="5ec22-495">**dns_ptr**: DNS 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-495">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="5ec22-496">**host_name**: 검색하는 호스트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-496">**host_name**: Pointer to name of host to search on</span></span>
- <span data-ttu-id="5ec22-497">**record_buffer**: TXT 데이터를 추출하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-497">**record_buffer**: Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="5ec22-498">**buffer_size**: TXT 데이터를 보유하는 버퍼 크기</span><span class="sxs-lookup"><span data-stu-id="5ec22-498">**buffer_size**: Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="5ec22-499">**wait_option**: DNS 서버 응답을 받기 위한 대기 옵션</span><span class="sxs-lookup"><span data-stu-id="5ec22-499">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-500">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-500">Return Values</span></span>

- <span data-ttu-id="5ec22-501">**NX_SUCCESS**: (0x00) TXT 문자열을 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="5ec22-501">**NX_SUCCESS**: (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="5ec22-502">**NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음</span><span class="sxs-lookup"><span data-stu-id="5ec22-502">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="5ec22-503">**NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함</span><span class="sxs-lookup"><span data-stu-id="5ec22-503">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="5ec22-504">NX_PTR_ERROR: (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-504">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5ec22-505">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-505">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="5ec22-506">NX_DNS_PARAM_ERROR: (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-506">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-507">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-507">Allowed From</span></span>

<span data-ttu-id="5ec22-508">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-508">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-509">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-509">Example</span></span>

```c
CHAR            record_buffer[50];

/* Request the text string for the specified host.  */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                record_buffer, 
                                sizeof(record_buffer), 500);


/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the text string is returned in record_buffer.  */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 
```

```Output
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="5ec22-510">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="5ec22-510">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="5ec22-511">DNS 클라이언트 패킷 풀을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-511">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-512">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-512">Prototype</span></span>

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="5ec22-513">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-513">Description</span></span>

<span data-ttu-id="5ec22-514">이 서비스는 이전에 만든 패킷 풀을 DNS **클라이언트** 패킷 풀로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-514">This service sets a previously created packet pool as the DNS **Client** packet pool.</span></span> <span data-ttu-id="5ec22-515">DNS 클라이언트에서 이 패킷 풀을 사용하여 DNS 쿼리를 보내므로 패킷 페이로드는 이더넷 프레임, IP 및 UDP 헤더를 포함하고 *nx_dns.h* 에 정의된 NX_DNS_PACKET_PAYLOAD_UNALIGNED 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-515">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD_UNALIGNED which includes the Ethernet frame, IP and UDP headers and is defined in *nx_dns.h*.</span></span>
 
>[!NOTE]
><span data-ttu-id="5ec22-516">DNS 클라이언트가 삭제되면 패킷 풀이 함께 삭제되지 않으며, 더 이상 필요하지 않은 패킷 풀은 애플리케이션에서 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-516">When the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>

>[!NOTE]
><span data-ttu-id="5ec22-517">이 서비스는 NX_DNS_CLIENT_USER_CREATE_PACKET_POOL 구성 옵션이 *nx_dns.h* 에 정의된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-517">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nx_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-518">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-518">Input Parameters</span></span>

- <span data-ttu-id="5ec22-519">**dns_ptr**: 이전에 만든 DNS **클라이언트** 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-519">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>
- <span data-ttu-id="5ec22-520">**pool_ptr** 이전에 만든 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-520">**pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-521">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-521">Return Values</span></span>

- <span data-ttu-id="5ec22-522">**NX_SUCCESS**: (0x00) 성공적으로 완료함</span><span class="sxs-lookup"><span data-stu-id="5ec22-522">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="5ec22-523">**NX_NOT_ENABLED**: (0x14) 클라이언트가 이 옵션에 대해 구성되지 않음</span><span class="sxs-lookup"><span data-stu-id="5ec22-523">**NX_NOT_ENABLED**: (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="5ec22-524">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS **클라이언트** 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-524">NX_PTR_ERROR: (0x07) Invalid IP or DNS **Client** pointer.</span></span>
- <span data-ttu-id="5ec22-525">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-525">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-526">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-526">Allowed From</span></span>

<span data-ttu-id="5ec22-527">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-527">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-528">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-528">Example</span></span>
```c
NX_DNS             my_dns;
NX_PACKET_POOL     client_pool;
NX_IP             *ip_ptr;


/* Create the DNS Client.  */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client.  */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                 NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                 NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool.  */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set.  */
```

## <a name="nx_dns_server_add"></a><span data-ttu-id="5ec22-529">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="5ec22-529">nx_dns_server_add</span></span>

<span data-ttu-id="5ec22-530">DNS 서버 IP 주소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-530">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-531">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-531">Prototype</span></span>

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="5ec22-532">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-532">Description</span></span>

<span data-ttu-id="5ec22-533">이 서비스는 IPv4 DNS 서버를 서버 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-533">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-534">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-534">Input Parameters</span></span>

- <span data-ttu-id="5ec22-535">**dns_ptr**: DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-535">**dns_ptr**: Pointer to DNS control block.</span></span>  
- <span data-ttu-id="5ec22-536">**server_address**: DNS 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="5ec22-536">**server_address**: IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-537">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-537">Return Values</span></span>

- <span data-ttu-id="5ec22-538">**NX_SUCCESS**: (0x00) 서버를 성공적으로 추가함</span><span class="sxs-lookup"><span data-stu-id="5ec22-538">**NX_SUCCESS**: (0x00) Server successfully added</span></span>
- <span data-ttu-id="5ec22-539">**NX_DNS_DUPLICATE_ENTRY** 또는 **NX_NO_MORE_ENTRIES**: (0x17) DNS 서버가 더 이상 허용되지 않음(목록이 가득 참)</span><span class="sxs-lookup"><span data-stu-id="5ec22-539">**NX_DNS_DUPLICATE_ENTRY** or **NX_NO_MORE_ENTRIES**: (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="5ec22-540">**NX_DNS_PARAM_ERROR**: (0xA8) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-540">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="5ec22-541">NX_PTR_ERROR: (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-541">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5ec22-542">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-542">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="5ec22-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) Null 서버 주소 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-544">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-544">Allowed From</span></span>

<span data-ttu-id="5ec22-545">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-545">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-546">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-546">Example</span></span>

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a><span data-ttu-id="5ec22-547">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="5ec22-547">nx_dns_server_get</span></span>

<span data-ttu-id="5ec22-548">클라이언트 목록에서 IPv4 DNS 서버를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-548">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-549">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-549">Prototype</span></span>

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="5ec22-550">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-550">Description</span></span>

<span data-ttu-id="5ec22-551">이 서비스는 지정된 인덱스의 서버 목록에서 IPv4 DNS 서버 주소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-551">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> <span data-ttu-id="5ec22-552">인덱스는 0부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-552">Note that the index is zero based.</span></span> <span data-ttu-id="5ec22-553">입력 인덱스가 DNS 클라이언트 목록의 크기를 초과하는 경우 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-553">If the input index exceeds the size of the DNS Client list, an error is returned.</span></span> <span data-ttu-id="5ec22-554">*nx_dns_get_serverlist_size* 서비스를 먼저 호출하여 클라이언트 목록의 DNS 서버 수를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-554">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-555">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-555">Input Parameters</span></span>

- <span data-ttu-id="5ec22-556">**dns_ptr**: DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-556">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="5ec22-557">**index**: DNS 클라이언트의 서버 목록에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="5ec22-557">**index**: Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="5ec22-558">**dns_server_address**: DNS 서버의 IP 주소에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-558">**dns_server_address**: Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-559">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-559">Return Values</span></span>

- <span data-ttu-id="5ec22-560">**NX_SUCCESS**: (0x00) 서버를 성공적으로 반환함</span><span class="sxs-lookup"><span data-stu-id="5ec22-560">**NX_SUCCESS**: (0x00) Successful server returned</span></span>
- <span data-ttu-id="5ec22-561">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) 인덱스에서 빈 슬롯을 가리킴</span><span class="sxs-lookup"><span data-stu-id="5ec22-561">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="5ec22-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) 인덱스에서 Null 주소를 가리킴</span><span class="sxs-lookup"><span data-stu-id="5ec22-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="5ec22-563">**NX_DNS_PARAM_ERROR**: (0xA8) 인덱스에서 목록의 크기를 초과함</span><span class="sxs-lookup"><span data-stu-id="5ec22-563">**NX_DNS_PARAM_ERROR**: (0xA8) Index exceeds size of list</span></span>
- <span data-ttu-id="5ec22-564">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-564">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="5ec22-565">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-565">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-566">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-566">Allowed From</span></span>

<span data-ttu-id="5ec22-567">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-568">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-568">Example</span></span>

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="5ec22-569">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="5ec22-569">nx_dns_server_remove</span></span>

<span data-ttu-id="5ec22-570">클라이언트 목록에서 IPv4 DNS 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-570">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-571">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-571">Prototype</span></span>

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="5ec22-572">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-572">Description</span></span>

<span data-ttu-id="5ec22-573">이 서비스는 클라이언트 목록에서 IPv4 DNS 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-573">This service removes an IPv4 DNS Server from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-574">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-574">Input Parameters</span></span>

- <span data-ttu-id="5ec22-575">**dns_ptr**: DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-575">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="5ec22-576">**server_address**: DNS 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="5ec22-576">**server_address**: IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-577">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-577">Return Values</span></span>

- <span data-ttu-id="5ec22-578">**NX_SUCCESS**: (0x00) DNS 서버를 성공적으로 제거함</span><span class="sxs-lookup"><span data-stu-id="5ec22-578">**NX_SUCCESS**: (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="5ec22-579">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) 서버가 클라이언트 목록에 없음</span><span class="sxs-lookup"><span data-stu-id="5ec22-579">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="5ec22-580">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null 서버 주소 입력</span><span class="sxs-lookup"><span data-stu-id="5ec22-580">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null server address input</span></span>
- <span data-ttu-id="5ec22-581">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-581">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="5ec22-582">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-582">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-583">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-583">Allowed From</span></span>

<span data-ttu-id="5ec22-584">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-585">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-585">Example</span></span>

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="5ec22-586">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="5ec22-586">nx_dns_server_remove_all</span></span>

<span data-ttu-id="5ec22-587">클라이언트 목록에서 모든 DNS 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-587">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="5ec22-588">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ec22-588">Prototype</span></span>

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="5ec22-589">Description</span><span class="sxs-lookup"><span data-stu-id="5ec22-589">Description</span></span>

<span data-ttu-id="5ec22-590">이 서비스는 클라이언트 목록에서 모든 DNS 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec22-590">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ec22-591">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ec22-591">Input Parameters</span></span>

- <span data-ttu-id="5ec22-592">**dns_ptr**: DNS 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-592">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ec22-593">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ec22-593">Return Values</span></span>

- <span data-ttu-id="5ec22-594">**NX_SUCCESS**: (0x00) DNS 서버를 성공적으로 제거함</span><span class="sxs-lookup"><span data-stu-id="5ec22-594">**NX_SUCCESS**: (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="5ec22-595">**NX_DNS_ERROR**: (0xA0) 보호 뮤텍스를 가져올 수 없음</span><span class="sxs-lookup"><span data-stu-id="5ec22-595">**NX_DNS_ERROR**: (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="5ec22-596">NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터</span><span class="sxs-lookup"><span data-stu-id="5ec22-596">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="5ec22-597">NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="5ec22-597">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ec22-598">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="5ec22-598">Allowed From</span></span>

<span data-ttu-id="5ec22-599">스레드</span><span class="sxs-lookup"><span data-stu-id="5ec22-599">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5ec22-600">예제</span><span class="sxs-lookup"><span data-stu-id="5ec22-600">Example</span></span>

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```