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
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a>챕터 3 - Azure RTOS NetX DNS 클라이언트 서비스 설명

이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX DNS 서비스에 대해 알파벳 순서로 설명하고 있습니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- **nx_dns_authority_zone_start_get**: *지정된 호스트 이름과 연결된 권한 영역의 시작 조회*
- **nx_dns_cache_initialize**: *DNS 캐시 초기화*
- **nx_dns_cache_notify_clear**: *캐시 전체 알림 함수 지우기*
- **nx_dns_cache_notify_set**: *캐시 전체 알림 함수 설정*
- **nx_dns_cname_get**: *입력 도메인 이름 별칭에 대한 정식 도메인 이름 조회*
- **nx_dns_create**: *DNS 클라이언트 인스턴스 만들기*
- **nx_dns_delete**: *DNS 클라이언트 인스턴스 삭제*
- **nx_dns_domain_name_server_get**: *입력 도메인 영역에 대한 권한 있는 이름 서버 조회*
- **nx_dns_domain_mail_exchange_get**: *지정된 호스트 이름과 연결된 메일 교환 조회*
- **nx_dns_domain_service_get**: *지정된 호스트 이름과 연결된 서비스 조회*
- **nx_dns_get_serverlist_size**: *DNS 클라이언트 서버 목록의 크기 반환*
- **nx_dns_info_by_name_get**: *IP 주소 반환, 입력 호스트 이름에 대한 포트 쿼리*
- **nx_dns_ipv4_address_by_name_get**: *지정된 호스트 이름에서 IPv4 주소 조회*
- **nx_dns_host_by_address_get**: *지정된 IP 주소에서 호스트 이름 조회*
- **nx_dns_host_by_name_get**: *지정된 호스트 이름에서 IPv4 주소 조회*
- **nx_dns_host_text_get**: *입력 도메인 이름에 대한 텍스트 데이터 조회*
- **nx_dns_packet_pool_set**: *DNS 클라이언트 패킷 풀 설정*
- **nx_dns_server_add**: *클라이언트 목록에 지정된 주소의 DNS 서버 추가*
- **nx_dns_server_get**: *클라이언트 목록에서 DNS 서버 반환*
- **nx_dns_server_remove**: *클라이언트 목록에서 DNS 서버 제거*
- **nx_dns_server_remove_all**: *클라이언트 목록에서 모든 DNS 서버 제거*

## <a name="nx_dns_authority_zone_start_get"></a>nx_dns_authority_zone_start_get

입력 호스트에 대한 권한 영역의 시작을 조회합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a>Description

NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 SOA 형식의 쿼리를 보내 입력 도메인 이름에 대한 권한 영역의 시작을 가져옵니다. DNS 클라이언트에서 DNS 서버 응답에 반환된 SOA 레코드를 *record_buffer* 메모리 위치에 복사합니다. 
>[!NOTE]
> 데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.

NetX DNS 클라이언트에서 NX_DNS_SOA_ENTRY SOA 레코드 유형은 7개의 4바이트 매개 변수(총 28바이트)로 저장됩니다.

- **nx_dns_soa_host_mname_ptr**: 이 영역의 기본 데이터 원본에 대한 포인터
- **nx_dns_soa_host_rname_ptr**: 이 영역을 담당하는 사서함에 대한 포인터
- **nx_dns_soa_serial**: 영역 버전 번호
- **nx_dns_soa_refresh**: 새로 고침 간격
- **nx_dns_soa_retry**: SOA 쿼리 다시 시도 간 간격
- **nx_dns_soa_expire**: SOA가 만료되는 기간
- **nx_dns_soa_minmum**: SOA 호스트 이름 DNS 회신 메시지의 최소 TTL 필드

두 개의 SOA 레코드에 대한 저장은 다음과 같습니다. 고정 길이 데이터가 포함된 SOA 레코드는 버퍼의 맨 위에서 시작하여 입력됩니다. MNAME 및 RNAME 포인터는 버퍼의 아래쪽에 저장된 가변 길이 데이터(호스트 이름)를 가리킵니다. 추가 SOA 레코드는 첫 번째 레코드("추가 SOA 레코드...") 뒤에 입력되며, 해당 가변 길이 데이터는 마지막 항목의 가변 길이 데이터("추가 SOA 가변 길이 데이터") 위에 저장됩니다.

![두 개의 SOA 레코드에 대한 저장을 나타내는 다이어그램](media/image2.png)

*record_buffer* 입력에서 서버 회신의 모든 SOA 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.

**record_count* 에서 반환된 SOA 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 데이터를 구문 분석하고 영역 권한 호스트 이름 문자열의 시작을 추출할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 클라이언트에 대한 포인터  
- **host_name**: SOA 데이터를 가져오는 호스트 이름에 대한 포인터
- **record_buffer**: SOA 데이터를 추출하는 위치에 대한 포인터
- **buffer_size**: SOA 데이터를 보유하는 버퍼 크기
- **record_count**: 검색된 SOA 레코드 수에 대한 포인터
- **wait_option**: DNS 서버 응답을 받기 위한 대기 옵션

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) SOA 데이터를 성공적으로 가져옴
- **NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음
- **NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자
- NX_DNS_PARAM_ERROR: (0xA8) 잘못된 비포인터 입력

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제
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


## <a name="nx_dns_cache_initialize"></a>nx_dns_cache_initialize

DNS 캐시를 초기화합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                             VOID *cache_ptr, UINT cache_size);

```
### <a name="description"></a>Description

이 서비스는 DNS 캐시를 만들고 초기화합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 제어 블록에 대한 포인터
- **cache_ptr**: DNS 캐시에 대한 포인터
- **cache_size**: DNS 캐시 크기(바이트)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 캐시를 성공적으로 초기화함
- NX_DNS_ERROR: (0xA0) 캐시가 4바이트로 정렬되지 않음
- NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID
- NX_PTR_ERROR: (0x07) 잘못된 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a>nx_dns_cache_notify_clear

DNS 캐시 전체 알림 함수를 지웁니다.

### <a name="prototype"></a>프로토타입

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a>Description

이 서비스는 캐시 전체 알림 함수를 지웁니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 캐시 알림을 성공적으로 설정함
- NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID
- NX_PTR_ERROR: (0x07) 잘못된 DNS 포인터

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a>nx_dns_cache_notify_set

DNS 캐시 전체 알림 함수를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a>Description

이 서비스는 캐시 전체 알림 함수를 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 제어 블록에 대한 포인터
- **cache_full_notify_cb**: 캐시가 가득 찰 때 호출하는 콜백 함수

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 캐시 알림을 성공적으로 설정함
- NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID
- NX_PTR_ERROR: (0x07) 잘못된 DNS 포인터

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a>nx_dns_cname_get

입력 호스트 이름에 대한 정식 이름을 조회합니다.

### <a name="prototype"></a>프로토타입
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a>Description

NX_DNS_ENABLE_EXTENDED_RR_TYPES가 *nx_dns.h* 에 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 CNAME 형식의 쿼리를 보내 정식 도메인 이름을 가져옵니다. DNS 클라이언트에서 DNS 서버 응답에 반환된 CNAME 문자열을 *record_buffer* 메모리 위치에 복사합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 클라이언트에 대한 포인터  
- **host_name**: CNAME 데이터를 가져오는 호스트 이름에 대한 포인터
- **record_buffer**: CNAME 데이터를 추출하는 위치에 대한 포인터
- **buffer_size**: CNAME 데이터를 보유하는 버퍼 크기
- **wait_option**: DNS 서버 응답을 받기 위한 대기 옵션

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) CNAME 데이터를 성공적으로 가져옴
- **NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음
- **NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자
- NX_DNS_PARAM_ERROR: (0xA8) 잘못된 비포인터 입력

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

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

## <a name="nx_dns_create"></a>nx_dns_create

DNS 클라이언트 인스턴스를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 IP 인스턴스에 대한 DNS 클라이언트 인스턴스를 만듭니다.

>[!NOTE]
>애플리케이션에서 DNS 클라이언트가 사용하는 패킷 풀의 패킷 페이로드가 최대 512바이트의 DNS 메시지와 UDP, IP 및 이더넷 헤더를 수용할 수 있을 만큼 충분히 큰지 확인해야 합니다. DNS 클라이언트에서 자체 패킷 풀을 만드는 경우 이 풀은 NX_DNS_PACKET_POOL_SIZE 및 NX_DNS_PACKET_PAYLOAD에서 정의됩니다. DNS 클라이언트 애플리케이션에서 이전에 만든 패킷 풀을 제공하는 것을 선호하는 경우 IPv4 DNS 클라이언트에 대한 페이로드는 최대 DNS의 경우 512바이트, IP 헤더의 경우 20바이트, UDP 헤더의 경우 8바이트 및 이더넷 헤더의 경우 14바이트여야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 클라이언트에 대한 포인터  
- **ip_ptr**: 이전에 만든 IP 인스턴스에 대한 포인터  
- **domain_name**: DNS 인스턴스의 도메인 이름에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS를 성공적으로 만듦
- **NX_DNS_ERROR**: (0xA0) DNS 만들기 오류
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a>nx_dns_delete

DNS 클라이언트 인스턴스를 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 DNS 클라이언트 인스턴스를 삭제하고 해당 리소스를 확보합니다. 
>[!NOTE]
> **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** 이 정의되고 DNS 클라이언트에 사용자 정의 패킷 풀이 할당된 경우 더 이상 필요하지 않은 DNS 클라이언트 패킷 풀은 애플리케이션에서 삭제해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: 이전에 만든 DNS **클라이언트** 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 클라이언트를 성공적으로 삭제함
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 클라이언트 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a>nx_dns_domain_name_server_get

입력 도메인 영역에 대한 권한 있는 이름 서버를 조회합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Description

NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 NS 형식의 쿼리를 보내 입력 도메인 이름에 대한 권한 있는 이름 서버를 가져옵니다. DNS 클라이언트에서 DNS 서버 응답에 반환된 NS 레코드를 *record_buffer* 메모리 위치에 복사합니다. 

>[!NOTE]
>데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.

NetX DNS 클라이언트에서 NX_DNS_NS_ENTRY NS 데이터 형식은 두 개의 4바이트 매개 변수로 저장됩니다.

- **nx_dns_ns_ipv4_address**: 이름 서버의 IPv4 주소
- **nx_dns_ns_hostname_ptr**: 이름 서버의 호스트 이름에 대한 포인터

아래에 표시된 버퍼에는 4개의 NX_DNS_NS_ENTRY 레코드가 포함되어 있습니다. 각 항목의 호스트 이름 문자열에 대한 포인터는 버퍼의 아래쪽 절반에 있는 해당 호스트 이름 문자열을 가리킵니다.

![4개의 NX DNS NS 항목 레코드가 포함된 버퍼에 대한 다이어그램](media/image3.png)

*record_buffer* 입력에서 서버 회신의 모든 NS 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.

**record_count* 에서 반환된 NS 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 각 레코드의 IP 주소와 호스트 이름을 구문 분석할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 클라이언트에 대한 포인터  
- **host_name**: NS 데이터를 가져오는 호스트 이름에 대한 포인터
- **record_buffer**: NS 데이터를 추출하는 위치에 대한 포인터
- **buffer_size**: NS 데이터를 보유하는 버퍼 크기
- **record_count**: 검색된 NS 레코드 수에 대한 포인터
- **wait_option**: DNS 서버 응답을 받기 위한 대기 옵션

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) NS 데이터를 성공적으로 가져옴
- **NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음
- **NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함
- NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제
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

## <a name="nx_dns_domain_mail_exchange_get"></a>nx_dns_domain_mail_exchange_get

입력 호스트 이름에 대한 메일 교환을 조회합니다.

### <a name="prototype"></a>프로토타입
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a>Description

NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 MX 형식의 쿼리를 보내 입력 도메인 이름에 대한 메일 교환을 가져옵니다. DNS 클라이언트에서 DNS 서버 응답에 반환된 MX 레코드를 *record_buffer* 메모리 위치에 복사합니다.

>[!NOTE]
>데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.

NetX DNS 클라이언트에서 NX_DNS_MAIL_EXCHANGE_ENTRY 메일 교환 레코드 유형은 4개의 매개 변수(총 12바이트)로 저장됩니다.

- **nx_dns_mx_ipv4_address**: 메일 교환 IPv4 주소 4바이트
- **nx_dns_mx_preference**: 기본 설정 2바이트
- **nx_dns_mx_reserved0**: 예약 2바이트
- **nx_dns_mx_hostname_ptr**: 메일 교환 서버 호스트 이름 4바이트에 대한 포인터

4개의 MX 레코드가 포함된 버퍼는 다음과 같습니다. 각 레코드에는 위 목록의 고정 길이 데이터가 포함됩니다. 메일 교환 서버 호스트 이름에 대한 포인터는 버퍼 아래쪽에 있는 해당 호스트 이름을 가리킵니다.

![4개의 MX 레코드가 포함된 버퍼를 보여 주는 다이어그램](media/image4.png)

*record_buffer* 입력에서 서버 회신의 모든 MX 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.

**record_count* 에서 반환된 MX 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 각 레코드의 메일 호스트 이름을 포함하여 MX 매개 변수를 구문 분석할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 클라이언트에 대한 포인터  
- **host_name**: MX 데이터를 가져오는 호스트 이름에 대한 포인터
- **record_buffer**: MX 데이터를 추출하는 위치에 대한 포인터
- **buffer_size**: MX 데이터를 보유하는 버퍼 크기
- **record_count**: 검색된 MX 레코드 수에 대한 포인터
- **wait_option**: DNS 서버 응답을 받기 위한 대기 옵션

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) MX 데이터를 성공적으로 가져옴
- **NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음
- **NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함
- NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제
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


## <a name="nx_dns_domain_service_get"></a>nx_dns_domain_service_get

입력 호스트 이름에서 제공하는 서비스를 조회합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Description

NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의된 경우 이 서비스는 지정된 도메인 이름이 포함된 SRV 형식의 쿼리를 보내 지정된 도메인과 연결된 서비스 및 해당 포트 번호를 조회합니다. DNS 클라이언트에서 DNS 서버 응답에 반환된 SRV 레코드를 *record_buffer* 메모리 위치에 복사합니다. 

>[!NOTE]
>데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.

NetX DNS 클라이언트에서 NX_DNS_SRV_ENTRY 서비스 레코드 유형은 6개의 매개 변수(총 16바이트)로 저장됩니다. 이렇게 하면 가변 길이 SRV 데이터를 메모리 효율적인 방식으로 저장할 수 있습니다.

- **Server IPv4 address**: nx_dns_srv_ipv4_address 4바이트
- **Server priority**: nx_dns_srv_priority 2바이트
- **Server weight**: nx_dns_srv_weight 2바이트
- **Service port number**: nx_dns_srv_port_number 2바이트
- **Reserved for 4-byte alignment**: nx_dns_srv_reserved0 2바이트
- **Pointer to server host name**: *nx_dns_srv_hostname_ptr 4바이트

4개의 SRV 레코드가 제공된 버퍼에 저장됩니다. 각 NX_DNS_SRV_ENTRY 레코드에는 레코드 버퍼의 아래쪽에 있는 해당 호스트 이름 문자열을 가리키는 *nx_dns_srv_hostname_ptr* 포인터가 포함되어 있습니다.

![제공된 버퍼에 저장된 4개의 SRV 레코드에 대한 다이어그램](media/image5.png)

*record_buffer* 입력에서 서버 회신의 모든 SRV 데이터를 보유할 수 없는 경우 *record_buffer* 는 필요한 만큼의 레코드를 보유하고 버퍼의 레코드 수를 반환합니다.

**record_count* 에서 반환된 SRV 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 각 레코드의 서버 호스트 이름을 포함하여 SRV 매개 변수를 구문 분석할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 클라이언트에 대한 포인터  
- **host_name**: SRV 데이터를 가져오는 호스트 이름에 대한 포인터
- **record_buffer**: SRV 데이터를 추출하는 위치에 대한 포인터
- **buffer_size**: SRV 데이터를 보유하는 버퍼 크기
- **record_count**: 검색된 SRV 레코드 수에 대한 포인터
- **wait_option**: DNS 서버 응답을 받기 위한 대기 옵션

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) SRV 데이터를 성공적으로 가져옴
- **NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음
- **NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함
- NX_DNS_PARAM_ERROR: (0xA8) 잘못된 DNS ID
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

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

## <a name="nx_dns_get_serverlist_size"></a>nx_dns_get_serverlist_size

DNS 클라이언트의 서버 목록 크기를 반환합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 목록에 있는 유효한 DNS 서버의 수를 반환합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 제어 블록에 대한 포인터  
- **size**: 목록의 서버 수 반환

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 서버 목록 크기를 반환함
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a>nx_dns_info_by_name_get

호스트 이름으로 DNS 서버의 IP 주소 및 포트를 반환합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 DNS 쿼리를 통해 입력 호스트 이름에 따라 서버 IP 및 포트(서비스 레코드)를 반환합니다. 서비스 레코드가 없는 경우 이 루틴은 입력 주소 포인터의 IP 주소를 0으로 반환하고, 오류 신호를 보내기 위해 0이 아닌 오류 상태를 반환합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 제어 블록에 대한 포인터  
- **host_name**: 호스트 이름 버퍼에 대한 포인터
- **host_address_ptr**: 반환하는 주소에 대한 포인터
- **host_port_ptr**: DNS 응답에 대한 wait_option 대기 옵션을 반환하는 포트에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 서버 레코드를 성공적으로 반환함
- **NX_DNS_NO_SERVER**: (0xA1) 호스트 이름에 쿼리를 보내기 위해 클라이언트에 등록된 DNS 서버가 없음
- **NX_DNS_QUERY_FAILED**: (0xA3) DNS 쿼리가 실패함. 클라이언트 목록의 DNS 서버에서 응답이 없거나 입력 호스트 이름에 사용할 수 있는 서비스 레코드가 없음
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a>nx_dns_ipv4_address_by_name_get

입력 호스트 이름에 대한 IPv4 주소를 조회합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 호스트 이름이 포함된 A 형식의 쿼리를 보내 입력 호스트 이름에 대한 IP 주소를 가져옵니다. DNS 클라이언트에서 DNS 서버 응답에 반환된 A 레코드의 IPv4 주소를 *record_buffer* 메모리 위치에 복사합니다. 

>[!NOTE]
>데이터를 받으려면 *record_buffer* 를 4바이트로 정렬해야 합니다.

아래와 같이 여러 IPv4 주소가 4바이트로 정렬된 버퍼에 저장됩니다.

![4바이트로 정렬되는 버퍼에 저장된 여러 IPv4 주소의 다이어그램](media/image6.png)

제공된 버퍼에서 모든 IP 주소 데이터를 보유할 수 없는 경우 나머지 A 레코드는 *record_buffer* 에 저장되지 않습니다. 이렇게 하면 애플리케이션에서 서버 회신에서 사용 가능한 IP 주소 데이터 중 하나, 일부 또는 모두를 검색할 수 있습니다.

**record_count* 에서 반환된 A 레코드 수를 사용하면 애플리케이션에서 *record_buffer* 에 있는 IPv4 주소 데이터를 구문 분석할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 클라이언트에 대한 포인터  
- **host_name_ptr**: IPv4 주소 버퍼를 가져오는 호스트 이름에 대한 포인터 및 IPv4 데이터를 추출하는 위치에 대한 포인터
- **buffer_size**: IPv4 데이터를 보유하는 버퍼 크기
- **wait_option**: DNS 서버 응답을 받기 위한 대기 옵션

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) IPv4 데이터를 성공적으로 가져옴
- **NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음
- **NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함
- NX_DNS_PARAM_ERROR: (0xA8) 잘못된 입력 매개 변수
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

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

## <a name="nx_dns_host_by_address_get"></a>nx_dns_host_by_address_get

IP 주소에서 호스트 이름을 조회합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션에서 이전에 지정한 하나 이상의 DNS 서버에서 제공된 IP 주소에 대한 이름 확인을 요청합니다. 성공하면 NULL로 끝나는 호스트 이름이 *host_name_ptr* 에서 지정한 문자열에 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: 이전에 만든 DNS 인스턴스에 대한 포인터
- **ip_address**: 이름으로 확인할 IP 주소
- **host_name_ptr**: 호스트 이름의 대상 영역에 대한 포인터
- **max_host_name_size**: 호스트 이름에 대한 대상 영역의 크기
- **wait_option**: 서비스에서 각 DNS 쿼리 및 쿼리 다시 시도를 수행한 후 DNS 서버 응답을 기다리는 시간(타이머 틱 수)을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값**: (0x00000001-0xFFFFFFFE) 숫자 값(1-0xFFFFFFFE)을 선택하면 DNS 확인을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 DNS 서버에서 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단되도록 합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS를 성공적으로 확인함  
- **NX_DNS_TIMEOUT**: (0xA2) DNS 뮤텍스를 가져오는 데 시간이 초과됨
- **NX_DNS_NO_SERVER**: (0xA1) DNS 서버 주소가 지정 되지 않음
- **NX_DNS_QUERY_FAILED**: (0xA3) 쿼리에 대한 응답을 받지 못함
- **NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null 입력 주소
- **NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) 인덱스에서 잘못된 주소 유형(예: IPv6)을 가리킴
- **NX_DNS_PARAM_ERROR**: (0xA8) 잘못된 비포인터 입력
- NX_PTR_ERROR: (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a>nx_dns_host_by_name_get

호스트 이름에서 IP 주소를 조회합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션에서 이전에 지정한 하나 이상의 DNS 서버에서 *host_name* 이 가리키는 제공된 이름에 대한 이름 확인을 요청합니다. 성공하면 연결된 IP 주소가 *host_address_ptr* 이 가리키는 대상에 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: 이전에 만든 DNS 인스턴스에 대한 포인터
- **host_name**: 호스트 이름에 대한 포인터
- **host_address_ptr**: DNS 호스트 IP 주소에 대한 포인터
- **wait_option**: 서비스에서 DNS 확인을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE) 숫자 값(1-0xFFFFFFFE)을 선택하면 DNS 확인을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 DNS 서버에서 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단되도록 합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS를 성공적으로 확인함
- **NX_DNS_NO_SERVER**: (0xA1) DNS 서버 주소가 지정 되지 않음
- **NX_DNS_QUERY_FAILED**: (0xA3) 쿼리에 대한 응답을 받지 못함
- NX_DNS_PARAM_ERROR: (0xA8) 잘못된 비포인터 입력
- NX_PTR_ERROR: (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제
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

## <a name="nx_dns_host_text_get"></a>nx_dns_host_text_get

입력 도메인 이름에 대한 텍스트 문자열을 조회합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 호스트 이름 및 버퍼가 포함된 TXT 형식의 쿼리를 보내 임의의 문자열 데이터를 가져옵니다.

DNS 클라이언트에서 DNS 서버 응답에 반환된 TXT 레코드의 텍스트 문자열을 *record_buffer* 메모리 위치에 복사합니다. 

>[!NOTE]
>데이터를 받기 위해 *record_buffer* 를 4바이트로 정렬할 필요가 없습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 클라이언트에 대한 포인터  
- **host_name**: 검색하는 호스트 이름에 대한 포인터
- **record_buffer**: TXT 데이터를 추출하는 위치에 대한 포인터
- **buffer_size**: TXT 데이터를 보유하는 버퍼 크기
- **wait_option**: DNS 서버 응답을 받기 위한 대기 옵션

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) TXT 문자열을 성공적으로 가져옴
- **NX_DNS_NO_SERVER**: (0xA1) 클라이언트 서버 목록이 비어 있음
- **NX_DNS_QUERY_FAILED**: (0xA3) 올바른 DNS 응답을 받지 못함
- NX_PTR_ERROR: (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자
- NX_DNS_PARAM_ERROR: (0xA8) 잘못된 비포인터 입력

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

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

## <a name="nx_dns_packet_pool_set"></a>nx_dns_packet_pool_set

DNS 클라이언트 패킷 풀을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Description

이 서비스는 이전에 만든 패킷 풀을 DNS **클라이언트** 패킷 풀로 설정합니다. DNS 클라이언트에서 이 패킷 풀을 사용하여 DNS 쿼리를 보내므로 패킷 페이로드는 이더넷 프레임, IP 및 UDP 헤더를 포함하고 *nx_dns.h* 에 정의된 NX_DNS_PACKET_PAYLOAD_UNALIGNED 이상이어야 합니다.
 
>[!NOTE]
>DNS 클라이언트가 삭제되면 패킷 풀이 함께 삭제되지 않으며, 더 이상 필요하지 않은 패킷 풀은 애플리케이션에서 삭제해야 합니다.

>[!NOTE]
>이 서비스는 NX_DNS_CLIENT_USER_CREATE_PACKET_POOL 구성 옵션이 *nx_dns.h* 에 정의된 경우에만 사용할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: 이전에 만든 DNS **클라이언트** 인스턴스에 대한 포인터
- **pool_ptr** 이전에 만든 패킷 풀에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적으로 완료함
- **NX_NOT_ENABLED**: (0x14) 클라이언트가 이 옵션에 대해 구성되지 않음
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS **클라이언트** 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제
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

## <a name="nx_dns_server_add"></a>nx_dns_server_add

DNS 서버 IP 주소를 추가합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a>Description

이 서비스는 IPv4 DNS 서버를 서버 목록에 추가합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 제어 블록에 대한 포인터  
- **server_address**: DNS 서버의 IP 주소

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 서버를 성공적으로 추가함
- **NX_DNS_DUPLICATE_ENTRY** 또는 **NX_NO_MORE_ENTRIES**: (0x17) DNS 서버가 더 이상 허용되지 않음(목록이 가득 참)
- **NX_DNS_PARAM_ERROR**: (0xA8) 잘못된 비포인터 입력
- NX_PTR_ERROR: (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자
- NX_DNS_BAD_ADDRESS_ERROR: (0xA4) Null 서버 주소 입력

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a>nx_dns_server_get

클라이언트 목록에서 IPv4 DNS 서버를 반환합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a>Description

이 서비스는 지정된 인덱스의 서버 목록에서 IPv4 DNS 서버 주소를 반환합니다. 인덱스는 0부터 시작합니다. 입력 인덱스가 DNS 클라이언트 목록의 크기를 초과하는 경우 오류가 반환됩니다. *nx_dns_get_serverlist_size* 서비스를 먼저 호출하여 클라이언트 목록의 DNS 서버 수를 가져올 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 제어 블록에 대한 포인터  
- **index**: DNS 클라이언트의 서버 목록에 대한 인덱스
- **dns_server_address**: DNS 서버의 IP 주소에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 서버를 성공적으로 반환함
- **NX_DNS_SERVER_NOT_FOUND**: (0xA9) 인덱스에서 빈 슬롯을 가리킴
- **NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) 인덱스에서 Null 주소를 가리킴
- **NX_DNS_PARAM_ERROR**: (0xA8) 인덱스에서 목록의 크기를 초과함
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a>nx_dns_server_remove

클라이언트 목록에서 IPv4 DNS 서버를 제거합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 목록에서 IPv4 DNS 서버를 제거합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 제어 블록에 대한 포인터
- **server_address**: DNS 서버의 IP 주소

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 서버를 성공적으로 제거함
- **NX_DNS_SERVER_NOT_FOUND**: (0xA9) 서버가 클라이언트 목록에 없음
- **NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null 서버 주소 입력
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a>nx_dns_server_remove_all

클라이언트 목록에서 모든 DNS 서버를 제거합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 목록에서 모든 DNS 서버를 제거합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dns_ptr**: DNS 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 서버를 성공적으로 제거함
- **NX_DNS_ERROR**: (0xA0) 보호 뮤텍스를 가져올 수 없음
- NX_PTR_ERROR: (0x07) 잘못된 IP 또는 DNS 포인터
- NX_CALLER_ERROR: (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```