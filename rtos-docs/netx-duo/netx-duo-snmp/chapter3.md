---
title: 3장 - Azure RTOS NetX Duo SNMP 에이전트 서비스 설명
description: 이 장에서는 아래에 나열된 모든 NetX Duo SNMP 에이전트 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810584"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a>3장 - Azure RTOS NetX Duo SNMP 에이전트 서비스 설명

이 장에서는 아래에 나열된 모든 Azure RTOS NetX Duo SNMP 에이전트 서비스를 알파벳 순서로 설명합니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- [nx_snmp_agent_auth_trap_key_use](#nx_snmp_agent_auth_trap_key_use)
   - 트랩 메시지의 인증 키(SNMP v3만 해당) 지정
- [nx_snmp_agent_authenticate_key_use](#nx_snmp_agent_authenticate_key_use)
   - 응답 메시지의 인증 키(SNMP v3만 해당) 지정
- [nx_snmp_agent_community_get](#nx_snmp_agent_community_get)
   - 커뮤니티 이름 검색
- [nx_snmp_agent_context_engine_set](#nx_snmp_agent_context_engine_set)
   - 컨텍스트 엔진 설정(SNMP v3만 해당)
- [nx_snmp_agent_context_name_set](#nx_snmp_agent_context_name_set)
   - 컨텍스트 이름 설정(SNMP v3만 해당)
- [nx_snmp_agent_create](#nx_snmp_agent_create)
   - SNMP 에이전트 만들기
- [nx_snmp_agent_current_version_get](#nx_snmp_agent_current_version_get)
   - 수신된 패킷의 SNMP 버전 가져오기
- [nx_snmp_agent_request_get_type_test](#nx_snmp_agent_request_get_type_test)
   - 마지막 SNMP 요청이 GET 형식인지 또는 SET 형식인지 지정
- [nx_snmp_agent_private_string_test](#nx_snmp_agent_private_string_test)
   - 문자열이 에이전트 프라이빗 문자열과 일치하는지 확인
- [nx_snmp_agent_public_string_test](#nx_snmp_agent_public_string_test)
   - 문자열이 에이전트 퍼블릭 문자열과 일치하는지 확인
- [nx_snmp_agent_set_interface](#nx_snmp_agent_set_interface)
   - SNMP 메시징에 대한 네트워크 인터페이스 설정
- [nx_snmp_agent_private_string_set](#nx_snmp_agent_private_string_set)
   - SNMP 에이전트 프라이빗 커뮤니티 문자열 설정
- [nx_snmp_agent_public_string_set](#nx_snmp_agent_public_string_set)
   - SNMP 에이전트 퍼블릭 커뮤니티 문자열 설정
- [nx_snmp_agent_version_set](#nx_snmp_agent_version_set)
   - 모든 SNMP 버전의 SNMP 에이전트 상태 설정
- [nx_snmp_agent_delete](#nx_snmp_agent_delete)
   - SNMP 에이전트 삭제
- [nx_snmp_agent_md5_key_create](#nx_snmp_agent_md5_key_create)
   - md5 키 만들기(SNMP v3만 해당)
- [nx_snmp_agent_md5_key_create_extended](#nx_snmp_agent_md5_key_create_extended)
   - md5 키 만들기(SNMP v3만 해당)
- [nx_snmp_agent_priv_trap_key_use](#nx_snmp_agent_priv_trap_key_use)
   - 트랩 메시지의 암호화 키(SNMP v3만 해당) 지정
- [nx_snmp_agent_privacy_key_use](#nx_snmp_agent_privacy_key_use)
   - 응답 메시지의 암호화 키(SNMP v3만 해당) 지정
- [nx_snmp_agent_sha_key_create](#nx_snmp_agent_sha_key_create)
   - sha 키 만들기(SNMP v3만 해당)
- [nx_snmp_agent_sha_key_create_extended](#nx_snmp_agent_sha_key_create_extended)
   - sha 키 만들기(SNMP v3만 해당)
- [nx_snmp_agent_start](#nx_snmp_agent_start)
   - SNMP 에이전트 시작
- [nx_snmp_agent_stop](#nx_snmp_agent_stop)
   - SNMP 에이전트 중지
- [nx_snmp_agent_trap_send](#nx_snmp_agent_trap_send)
   - SNMP v1 트랩 보내기(IPv4만 해당)
- [nx_snmp_agent_trapv2_send](#nx_snmp_agent_trapv2_send)
   - SNMP v2 트랩 보내기(IPv4만 해당)
- [nx_snmp_agent_trapv2_oid_send](#nx_snmp_agent_trapv2_oid_send)
   - OID를 지정하여 SNMP v2 트랩 보내기(IPv4만 해당)
- [nx_snmp_agent_trapv3_send](#nx_snmp_agent_trapv3_send)
   - SNMP v3 트랩 보내기(IPv4만 해당)
- [nx_snmp_agent_trapv3_oid_send](#nx_snmp_agent_trapv3_oid_send)
   - OID를 지정하여 SNMP v2 트랩 보내기(IPv4만 해당)
- [nxd_snmp_agent_trap_send](#nxd_snmp_agent_trap_send)
   - SNMP v1 트랩 보내기(IPv4 및 IPv6)
- [nxd_snmp_agent_trapv2_send](#nxd_snmp_agent_trapv2_send)
   - SNMP v2 트랩 보내기(IPv4 및 IPv6)
- [nxd_snmp_agent_trapv2_oid_send](#nxd_snmp_agent_trapv2_oid_send)
   - OID를 지정하여 SNMP v2 트랩 보내기(IPv4/IPv6)
- [nxd_snmp_agent_trapv3_send](#nxd_snmp_agent_trapv3_send)
   - SNMP v3 트랩 보내기(IPv4 및 IPv6)
- [nxd_snmp_agent_trapv3_oid_send](#nxd_snmp_agent_trapv3_oid_send)
   - OID를 지정하여 SNMP v2 트랩 보내기(IPv4/IPv6)
- [nx_snmp_agent_v3_context_boots_set](#nx_snmp_agent_v3_context_boots_set)
   - 다시 부팅 수 설정
- [nx_snmp_object_compare](#nx_snmp_object_compare)
   - 두 개체 비교
- [nx_snmp_object_compare_extended](#nx_snmp_object_compare_extended)
   - 두 개체 비교
- [nx_snmp_object_copy](#nx_snmp_object_copy)
   - 개체 복사
- [nx_snmp_object_copy_extended](#nx_snmp_object_copy_extended)
   - 개체 복사
- [nx_snmp_object_counter_get](#nx_snmp_object_counter_get)
   - 카운터 개체 가져오기
- [nx_snmp_object_counter_set](#nx_snmp_object_counter_set)
   - 카운터 개체 설정
- [nx_snmp_object_counter64_get](#nx_snmp_object_counter64_get)
   - 64비트 카운터 개체 가져오기
- [nx_snmp_object_counter64_set](#nx_snmp_object_counter64_set)
   - 64비트 카운터 개체 설정
- [nx_snmp_object_end_of_mib](#nx_snmp_object_end_of_mib)
   - end-of-mib 값 설정
- [nx_snmp_object_gauge_get](#nx_snmp_object_gauge_get)
   - 계기 개체 가져오기
- [nx_snmp_object_gauge_set](#nx_snmp_object_gauge_set)
   - 계기 개체 설정
- [nx_snmp_object_id_get](#nx_snmp_object_id_get)
   - 개체 ID 가져오기
- [nx_snmp_object_id_set](#nx_snmp_object_id_set)
   - 개체 ID 설정
- [nx_snmp_object_integer_get](#nx_snmp_object_integer_get)
   - 정수 개체 가져오기
- [nx_snmp_object_integer_set](#nx_snmp_object_integer_set)
   - 정수 개체 설정
- [nx_snmp_object_ip_address_get](#nx_snmp_object_ip_address_get)
   - IP 주소 개체 가져오기(IPv4만 해당)
- [nx_snmp_object_ip_address_set](#nx_snmp_object_ip_address_set)
   - IP 주소 개체 설정(IPv4만 해당)
- [nx_snmp_object_ipv6_address_get](#nx_snmp_object_ipv6_address_get)
   - IP 주소 개체 가져오기(IPv6만 해당)
- [nx_snmp_object_ipv6_address_set](#nx_snmp_object_ipv6_address_set)
   - IP 주소 개체 설정(IPv6만 해당)
- [nx_snmp_object_no_instance](#nx_snmp_object_no_instance)
   - no-instance 값 설정
- [nx_snmp_object_not_found](#nx_snmp_object_not_found)
   - not-found 값 설정
- [nx_snmp_object_octet_string_get](#nx_snmp_object_octet_string_get)
   - 옥텟 문자열 개체 가져오기
- [nx_snmp_object_octet_string_set](#nx_snmp_object_octet_string_set)
   - 옥텟 문자열 개체 설정
- [nx_snmp_object_string_get](#nx_snmp_object_string_get)
   - ASCII 문자열 개체 가져오기
- [nx_snmp_object_string_set](#nx_snmp_object_string_set)
   - ASCII 문자열 개체 설정
- [nx_snmp_object_timetics_get](#nx_snmp_object_timetics_get)
   - timetics 개체 가져오기
- [nx_snmp_object_timetics_set](#nx_snmp_object_timetics_set)
   - timetics 개체 설정

## <a name="nx_snmp_agent_auth_trap_key_use"></a>nx_snmp_agent_auth_trap_key_use
트랩 메시지의 인증 키 지정

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Description

이 서비스는 트랩 메시지의 SNMPv3 보안 헤더에서 인증 매개 변수를 설정하는 데 사용할 키를 지정합니다. 키에 대해 NX_NULL 값을 제공하면 인증이 사용하지 않도록 설정됩니다.

> [!NOTE]
> 이 키는 미리 만들어야 합니다. nx_snmp_agent_md5_key_create 또는 nx_snmp_agent_sha_key_create를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **key** 이전에 만든 MD5 또는 SHA 키에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 성공적인 인증 키 설정입니다.
- **NX_NOT_ENABLED**(0X14) SNMP 보안이 사용하지 않도록 설정됩니다. 
- **NX_PTR_ERROR**(0X07) 잘못된 SNMP 에이전트 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a>nx_snmp_agent_authenticate_key_use
응답 메시지의 인증 키 지정

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Description

이 서비스는 설정된 후에 수행된 모든 요청에 대해 SNMPv3 보안 매개 변수의 인증 매개 변수에 사용할 키를 지정합니다. 키에 대해 NX_NULL 값을 제공하면 인증이 사용하지 않도록 설정됩니다.

> [!NOTE]
> 이 키는 미리 만들어야 합니다. nx_snmp_agent_md5_key_create 또는 nx_snmp_agent_sha_key_create를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **key** 이전에 만든 MD5 또는 SHA 키에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 키 설정입니다.
- **NX_NOT_ENABLED**(0X14) SNMP 보안이 사용하지 않도록 설정됩니다.
- **NX_PTR_ERROR**(0X07) 잘못된 SNMP 에이전트 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a>nx_snmp_agent_community_get
커뮤니티 이름 검색

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a>Description

이 서비스는 SNMP 에이전트에서 받은 가장 최근의 SNMP 요청에서 커뮤니티 이름을 검색합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **community_string_ptr** SNMP 에이전트 커뮤니티 문자열을 반환할 문자열 포인터에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 커뮤니티 가져오기입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a>nx_snmp_agent_request_get_type_test
마지막 SNMP 요청이 GET 형식인지 또는 SET 형식인지 지정

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a>Description

이 서비스는 SNMP 관리자의 가장 최근 요청이 GET 형식(GET, GETNEXT 또는 GETBULK)인지 또는 SET 형식인지를 나타냅니다. SNMPv1 또는 SNMPv2 애플리케이션에서 요청이 GET 형식이면 수신된 커뮤니티 문자열을 SNMP 에이전트 퍼블릭 문자열과 비교하고, SET 형식이면 SNMP 에이전트 프라이빗 문자열과 비교하려는 사용자 이름 콜백과 함께 사용하기 위한 것입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **is_get_type** 요청 형식 상태에 대한 포인터로, 다음과 같습니다.  
GET 형식이면 NX_TRUE  
SET 형식이면 NX_FALSE

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적으로 반환된 형식입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a>nx_snmp_agent_context_engine_set
컨텍스트 엔진 설정(SNMP v3만 해당)

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a>Description

이 서비스는 SNMP 에이전트의 컨텍스트 엔진을 설정합니다. SNMPv3 처리에만 적용됩니다. 컨텍스트 엔진 ID가 키 만들기 프로세스에서 사용되므로 애플리케이션이 인증 및 암호화를 사용하는 경우 보안 키를 만들기 전에 호출해야 합니다. 그러지 않으면 NetX Duo SNMP는 *nxd_snmp.c* 맨 위에 기본 컨텍스트 엔진 ID를 제공합니다.

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **context_engine** 컨텍스트 엔진 문자열에 대한 포인터입니다.
- **context_engine_size** 컨텍스트 엔진 문자열의 크기입니다. 컨텍스트 엔진의 최대 바이트 수는 NX_SNMP_MAX_CONTEXT_STRING으로 정의됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 성공적인 SNMP 컨텍스트 엔진 세트입니다.
- **NX_NOT_ENABLED**(0x14) SNMPv3가 사용하도록 설정되지 않습니다.
- **NX_SNMP_ERROR**(0X100) 컨텍스트 엔진 크기 오류입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a>nx_snmp_agent_context_name_set
컨텍스트 이름 설정(SNMP v3만 해당)

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a>Description

이 서비스는 SNMP 에이전트의 컨텍스트 이름을 설정합니다. SNMPv3 처리에만 적용됩니다. 호출하지 않으면 NetX Duo SNMP 에이전트는 컨텍스트 이름을 비워 둡니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **context_name** 컨텍스트 이름 문자열에 대한 포인터입니다.
- **context_name_size** 컨텍스트 이름 문자열의 크기입니다. 컨텍스트 이름의 최대 바이트 수는 NX_SNMP_MAX_CONTEXT_STRING으로 정의됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 성공적인 SNMP 컨텍스트 이름 설정입니다.
- **NX_SNMP_ERROR**(0X100) 컨텍스트 이름 크기 오류입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a>nx_snmp_agent_create
SNMP 에이전트 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에 SNMP 에이전트를 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **snmp_agent_name** SNMP 에이전트 이름 문자열에 대한 포인터입니다.
- **ip_ptr** IP 인스턴스에 대한 포인터입니다.
- **stack_ptr** SNMP 에이전트 스레드 스택 포인터에 대한 포인터입니다.
- **stack_size** 스택 크기(바이트)입니다.
- **pool_ptr** 이 SNMP 에이전트의 기본 패킷 풀에 대한 포인터입니다.
- **snmp_agent_username_process** 애플리케이션의 사용자 이름 처리 루틴에 대한 함수 포인터입니다.
- **snmp_agent_get_process** 애플리케이션의 GET 요청 처리 루틴에 대한 함수 포인터입니다.
- **snmp_agent_getnext_process** 애플리케이션의 GETNEXT 요청 처리 루틴에 대한 함수 포인터입니다.
- **snmp_agent_set_process** 애플리케이션의 SET 요청 처리 루틴에 대한 함수 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 에이전트 만들기입니다.
- **NX_SNMP_ERROR**(0X100) SNMP 에이전트 만들기 오류입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a>nx_snmp_agent_current_version_get
SNMP 패킷 버전 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a>Description

이 서비스는 가장 최근에 받은 SNMP 패킷에서 구문 분석된 SNMP 버전을 검색합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **version** 수신된 SNMP 패킷에서 구문 분석된 SNMP 버전에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 버전 가져오기입니다.
- **NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a>nx_snmp_agent_private_string_test
프라이빗 문자열이 에이전트 프라이빗 문자열과 일치하는지 확인

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a>Description

이 서비스는 null 종료 입력 커뮤니티 문자열과 SNMP 에이전트 프라이빗 문자열을 비교하고 일치하는지 여부를 나타냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **community_string** 비교할 문자열에 대한 포인터입니다.
- **is_private** 비교 결과에 대한 포인터입니다.  
NX_TRUE - 문자열 일치  
NX_FALSE - 문자열이 일치하지 않음

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 비교 성공
- **NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a>nx_snmp_agent_public_string_test
수신되는 퍼블릭 문자열이 에이전트의 퍼블릭 문자열과 일치하는지 확인합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a>Description

이 서비스는 null 종료 입력 커뮤니티 문자열과 SNMP 에이전트 퍼블릭 문자열을 비교하고 일치하는지 여부를 나타냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **community_string** 비교할 문자열에 대한 포인터입니다.
- **is_public** 비교 결과에 대한 포인터입니다.  
NX_TRUE - 문자열 일치  
NX_FALSE - 문자열이 일치하지 않음

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 비교 성공
- **NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a>nx_snmp_agent_version_set
각 SNMP 버전의 SNMP 에이전트 상태 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a>Description

이 서비스는 SNMP 에이전트의 각 SNMP 버전인 V1, V2 및 V3에 대해 상태(사용/사용 안 함)를 설정합니다. 사용자 구성 가능 옵션, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 및 NX_SNMP_DISABLE_V3는 이러한 런타임 설정을 재정의합니다. 기본적으로 SNMP 에이전트는 세 가지 버전 모두에 대해 사용하도록 설정됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **enabled_v1** SNMP V1에 대한 enabled 상태를 on/off로 설정합니다.
- **enabled_v2** SNMP V2에 대한 enabled 상태를 on/off로 설정합니다.
- **enabled_v3** SNMP V3에 대한 enabled 상태를 on/off로 설정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 버전 설정입니다.
- **NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a>nx_snmp_agent_private_string_set
SNMP 에이전트 프라이빗 문자열 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a>Description

이 서비스는 입력 null 종료 문자열을 사용하여 SNMP 에이전트 프라이빗 커뮤니티 문자열을 설정합니다. 기본값은 NULL(프라이빗 문자열이 설정되지 않음)이며, 이 경우 "프라이빗" 커뮤니티 문자열과 함께 수신된 모든 SNMP 패킷이 읽기/쓰기 액세스를 위해 SNMP 에이전트에서 허용되지 않습니다. 입력 문자열은 사용자가 구성할 수 있는 NX_SNMP_MAX_USER_NAME(null 종료를 위한 공간 허용) 크기보다 작거나 같아야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **community_string** 할당할 프라이빗 문자열에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 프라이빗 문자열을 설정했습니다.
- **NX_SNMP_ERROR_TOOBIG**(0X01) 문자열 크기가 너무 큽니다. 
- **NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a>nx_snmp_agent_public_string_set
SNMP 에이전트 퍼블릭 문자열 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a>Description

이 서비스는 입력 null 종료 문자열을 사용하여 SNMP 에이전트 퍼블릭 커뮤니티 문자열을 설정합니다. 커뮤니티 문자열은 사용자가 구성할 수 있는 NX_SNMP_MAX_USER_NAME(null 종료를 위한 공간 허용) 크기보다 작거나 같아야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **community_string** 할당할 퍼블릭 문자열에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 퍼블릭 문자열을 설정했습니다.
- **NX_SNMP_ERROR_TOOBIG**(0X01) 문자열 크기가 너무 큽니다.
- **NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a>nx_snmp_agent_delete
SNMP 에이전트 삭제

### <a name="prototype"></a>프로토타입

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Description

이 서비스는 이전에 만든 SNMP 에이전트를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 에이전트 삭제입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a>nx_snmp_agent_set_interface
SNMP 에이전트 네트워크 인터페이스 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a>Description

이 서비스는 입력 인터페이스 인덱스로 지정된 SNMP 에이전트의 SNMP 네트워크 인터페이스를 설정합니다. 여러 네트워크 인터페이스를 지원하는 NetX Duo 5.6 이상인 SNMP 호스트 애플리케이션에만 유용합니다. 기본 인터페이스에 대해 호스트에서 지정하지 않은 경우 기본값은 0입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **If_index** SNMP 인터페이스를 지정하는 인덱스입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 인터페이스 설정입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a>nx_snmp_agent_md5_key_create
md5 키 만들기(SNMP v3만 해당)

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a>Description

이 서비스는 인증 및 암호화에 사용할 수 있는 MD5 키를 만듭니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 nx_snmp_agent_md5_key_create_extended()로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **password** 암호 문자열에 대한 포인터입니다.
- **destination_key** SNMP 키 데이터 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 키 만들기입니다.
- **NX_NOT_ENABLED**(0x14) 보안이 사용하지 않도록 설정되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a>nx_snmp_agent_md5_key_create_extended
md5 키 만들기(SNMP v3만 해당)

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a>Description

이 서비스는 인증 및 암호화에 사용할 수 있는 MD5 키를 만듭니다.

이 서비스는 nx_snmp_agent_md5_key_create()를 대신합니다. 이 버전을 사용하려면 호출자가 암호 길이를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **password** 암호 문자열에 대한 포인터입니다.
- **password_length** 암호 문자열의 길이입니다.
- **destination_key** SNMP 키 데이터 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 키 만들기입니다.
- **NX_NOT_ENABLED**(0x14) 보안이 사용하지 않도록 설정되었습니다.
- **NX_SNMP_FAILED**(0x102) SNMP가 실패했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a>nx_snmp_agent_priv_trap_key_use
트랩 메시지의 암호화 키 지정

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 프라이빗 키를 SNMPv3 트랩 메시지의 암호화 및 암호 해독에 사용하도록 지정합니다.

> [!NOTE]
> 이전에 인증 키를 만들어야 합니다. SNMP v3 개인 정보 보호(암호화)를 사용하려면 인증이 필요합니다. 자세한 내용은 nx_snmp_agent_auth_trap_key_use를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **key** 이전에 키를 만들기 위한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 성공적인 프라이빗 키 설정입니다.
- **NX_NOT_ENABLED**(0x14) 보안이 사용하지 않도록 설정되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a>nx_snmp_agent_privacy_key_use
응답 메시지에 대한 암호화 키 지정

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Description

이 서비스는 이전에 만든 키를 SNMPv3 응답 메시지의 암호화 및 암호 해독에 사용하도록 지정합니다.

> [!NOTE]
> 이전에 인증 키를 지정했어야 합니다. SNMP v3 암호화를 위해서는 인증 키도 만들어야 합니다. 자세한 내용은 nx_snmp_agent_authentiation_key_use를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **key** 이전에 키를 만들기 위한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 성공적인 프라이빗 키 설정입니다.
- **NX_NOT_ENABLED**(0x14) 보안이 사용하지 않도록 설정되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a>nx_snmp_agent_sha_key_create
SHA 키 만들기(SNMP v3만 해당)

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a>Description

이 서비스는 인증 및 암호화에 사용할 수 있는 SHA 키를 만듭니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 nx_snmp_agent_sha_key_create_extended()로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **password** 암호 문자열에 대한 포인터입니다.
- **destination_key** SNMP 키 데이터 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 키 만들기입니다.
- **NX_SNMP_ERROR**(0x100) 키 만들기 오류입니다.
- **NX_PTR_ERROR**(0X07) 잘못된 SNMP 에이전트 또는 키 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a>nx_snmp_agent_sha_key_create_extended
SHA 키 만들기(SNMP v3만 해당)

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a>Description

이 서비스는 인증 및 암호화에 사용할 수 있는 SHA 키를 만듭니다.

이 서비스는 nx_snmp_agent_sha_key_create()를 대신합니다. 이 버전을 사용하려면 호출자가 암호 길이를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **password** 암호 문자열에 대한 포인터입니다.
- **password_length** 암호 문자열의 길이입니다.
- **destination_key** SNMP 키 데이터 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 키 만들기입니다.
- **NX_SNMP_ERROR**(0x100) 키 만들기 오류입니다.
- **NX_SNMP_FAILED**(0x102) 키를 만들지 못했습니다.
- **NX_PTR_ERROR**(0X07) 잘못된 SNMP 에이전트 또는 키 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a>nx_snmp_agent_start
SNMP 에이전트 시작 

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Description

이 서비스는 UDP 소켓을 SNMP 포트 161에 바인딩하고 SNMP 에이전트 스레드 작업을 시작합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) SNMP 에이전트를 성공적으로 시작합니다.
- **NX_SNMP_ERROR**(0X100) SNMP 에이전트 시작 오류입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a>nx_snmp_agent_stop
SNMP 에이전트 중지 

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Description

이 서비스는 SNMP 에이전트 스레드 작업을 중지하고 SNMP 포트에 대한 UDP 소켓 바인딩을 해제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) SNMP 에이전트를 성공적으로 중지합니다.
- **NX_PTR_ERROR**(0X07) 잘못된 SNMP 에이전트 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a>nx_snmp_agent_trap_send
SNMPv1 트랩 보내기(IPv4만 해당)

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Description

이 서비스는 SNMP 트랩을 지정된 IPv4 주소의 SNMP 관리자로 보냅니다. NetX Duo에서 SNMP 트랩을 전송하는 기본 방법은 nxd_snmp_agent_trap_send 서비스를 사용하는 것입니다. 기존 NetX SNMP 에이전트 애플리케이션을 지원하기 위해 nx_snmp_agent_trap_send가 NetX Duo에 포함되어 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **ip_address** SNMP 관리자의 IPv4 주소입니다.
- **enterprise** 엔터프라이즈 개체 ID 문자열(sysObectID)입니다.
- **trap_type** 다음과 같은 요청된 트랩의 유형입니다.  
   - NX_SNMP_TRAP_COLDSTART (0)  
   - NX_SNMP_TRAP_WARMSTART (1)  
   - NX_SNMP_TRAP_LINKDOWN (2)  
   - NX_SNMP_TRAP_LINKUP (3)  
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)  
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  

- **trap_code** 트랩 코드를 지정합니다.
- **elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).
- **object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다. 목록은 NX_NULL 로 종료됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.
- **NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.
- **NX_NOT_ENABLED**(0x14) SNMPv1이 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a>nxd_snmp_agent_trap_send
SNMPv1 트랩 보내기(IPv4 및 IPv6)

### <a name="prototype"></a>프로토타입

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Description

이 서비스는 SNMP 트랩을 지정된 IP 주소의 SNMP 관리자로 보냅니다. NetX에서 SNMP 트랩을 전송하는 것과 동일한 방법은 nxd_snmp_agent_trap_send 서비스입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **ip_address** SNMP 관리자의 IPv4 또는 IPv6 주소입니다.
- **enterprise** 엔터프라이즈 개체 ID 문자열(sysObectID)입니다.
- **trap_type** 다음과 같은 요청된 트랩의 유형입니다.  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

- **trap_code** 트랩 코드를 지정합니다.
- **elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).
- **object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다. 목록은 NX_NULL 로 종료됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.
- **NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.
- **NX_NOT_ENABLED**(0x14) SNMPv1이 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a>nx_snmp_agent_trapv2_send
SNMPv2 트랩 보내기(IPv4만 해당)

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Description

이 서비스는 SNMPv2 트랩을 지정된 IPv4 주소의 SNMP 관리자로 보냅니다. NetX Duo에서 SNMP 트랩을 전송하는 기본 방법은 nxd_snmp_agent_trapv2_send 서비스를 사용하는 것입니다. 기존 NetX SNMP 에이전트 애플리케이션을 지원하기 위해 nx_snmp_agent_trapv2_send가 NetX Duo에 포함되어 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **ip_address** SNMP 관리자의 IPv4 주소입니다.
- **community** 커뮤니티 이름(사용자 이름)입니다.
- **trap_type**  
   요청된 트랩의 유형입니다. 표준 이벤트는 다음과 같습니다.  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   소유 데이터의 경우:  
   - NX_SNMP_TRAP_CUSTOM(0xFFFFFFFF)(nxd_snmp.h에 정의됨)
   
- **elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).
- **object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다. 목록은 NX_NULL 로 종료됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.
- **NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.
- **NX_NOT_ENABLED**(0x14) SNMPv2가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a>nx_snmp_agent_trapv2_oid_send
OID를 직접 지정하는 SNMPv2 트랩 보내기 

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 주소(IPv4만 해당)에서 SNMP 관리자에 SNMPv2 트랩을 보내고 호출자가 OID를 직접 지정할 수 있도록 허용합니다. NetX Duo에서 지정된 OID를 사용하여 SNMP 트랩을 전송하는 기본 방법은 nxd_snmp_agent_trapv2_oid_send 서비스를 사용하는 것입니다. 기존 NetX SNMP 에이전트 애플리케이션을 지원하기 위해 nx_snmp_agent_trapv2_oid_ send가 NetX Duo에 포함되어 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **ip_address** SNMP 관리자의 IP 주소입니다.
- **community** 커뮤니티 이름(사용자 이름)입니다.
- **oid** OID를 포함하는 버퍼에 대한 포인터입니다.
- **elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).
- **object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다. 목록은 NX_NULL 로 종료됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.
- **NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.
- **NX_PTR_ERROR**(0x16) 잘못된 SNMP 에이전트 또는 매개 변수 포인터입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 대상 IP 주소입니다.
- **NX_OPTION_ERROR**(0x0A) 잘못된 매개 변수입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a>nxd_snmp_agent_trapv2_send
SNMPv2 트랩 보내기(IPv4 및 IPv6)

### <a name="prototype"></a>프로토타입

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 주소의 SNMP 관리자에 SNMP V2 트랩을 보냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **ip_address** SNMP 관리자의 IP(IPv4 또는 IPv6) 주소입니다.
- **community** 커뮤니티 이름(사용자 이름)입니다.
- **trap_type**  
   요청된 트랩의 유형입니다. 표준 이벤트는 다음과 같습니다.  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   소유 데이터의 경우:

   - NX_SNMP_TRAP_CUSTOM(0xFFFFFFFF)(nxd_snmp.h에 정의됨)

- **elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).
- **object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다. 목록은 NX_NULL 로 종료됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.
- **NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.
- **NX_NOT_ENABLED**(0x14) SNMPv2가 사용하도록 설정되지 않았습니다.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR**(0x104) 지원되지 않는 IP 버전입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a>nxd_snmp_agent_trapv2_oid_send
OID를 직접 지정하는 SNMPv2 트랩 보내기 

### <a name="prototype"></a>프로토타입

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 주소(IPv4/IPv6)의 SNMP 관리자에 SNMP v2 트랩을 보내고 호출자가 직접 OID를 지정할 수 있도록 허용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **ip_address** SNMP 관리자의 IP 주소입니다(IPv4/IPv6).
- **community** 커뮤니티 이름(사용자 이름)입니다.
- **oid** OID를 포함하는 버퍼에 대한 포인터입니다.
- **elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).
- **object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다. 목록은 NX_NULL 로 종료됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.
- **NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.
- **NX_PTR_ERROR**(0x16) 잘못된 SNMP 에이전트 또는 매개 변수 포인터입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 대상 IP 주소입니다.
- **NX_OPTION_ERROR**(0x0A) 잘못된 매개 변수입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a>nx_snmp_agent_trapv3_send
SNMPv3 트랩 보내기(IPv4만 해당)

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Description

이 서비스는 SNMPv3 트랩을 지정된 IPv4 주소의 SNMP 관리자로 보냅니다. NetX Duo에서 SNMP 트랩을 전송하는 기본 방법은 nxd_snmp_agent_trapv3_send 서비스를 사용하는 것입니다. 기존 NetX SNMP 에이전트 애플리케이션을 지원하기 위해 nx_snmp_agent_trapv3_send가 NetX Duo에 포함되어 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **ip_address** SNMP 관리자의 IPv4 주소입니다.
- **username** 커뮤니티 이름(사용자 이름)입니다.
- **trap_type**  
   요청된 트랩의 유형입니다. 표준 이벤트는 다음과 같습니다.  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   소유 데이터의 경우:
   - NX_SNMP_TRAP_CUSTOM(0xFFFFFFFF)(nxd_snmp.h에 정의됨)

- **elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).
- **object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다. 목록은 NX_NULL 로 종료됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.
- **NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.
- **NX_NOT_ENABLED**(0x14) SNMPv3가 사용하도록 설정되지 않습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a>nx_snmp_agent_trapv3_oid_send
OID를 직접 지정하는 SNMPv3 트랩 보내기 

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 주소(IPv4만 해당)에서 SNMP 관리자에 SNMPv3 트랩을 보내고 호출자가 OID를 직접 지정할 수 있도록 허용합니다. NetX Duo에서 지정된 OID를 사용하여 SNMP 트랩을 전송하는 기본 방법은 nxd_snmp_agent_trapv3_oid_send 서비스를 사용하는 것입니다. 기존 NetX SNMP 에이전트 애플리케이션을 지원하기 위해 nx_snmp_agent_trapv3_oid_ send가 NetX Duo에 포함되어 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **ip_address** SNMP 관리자의 IP 주소입니다.
- **username** 커뮤니티 이름(사용자 이름)입니다.
- **oid** OID를 포함하는 버퍼에 대한 포인터입니다.
- **elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).
- **object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다. 목록은 NX_NULL 로 종료됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.
- **NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.
- **NX_PTR_ERROR**(0x16) 잘못된 SNMP 에이전트 또는 매개 변수 포인터입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 대상 IP 주소입니다.
- **NX_OPTION_ERROR**(0x0A) 잘못된 매개 변수입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a>nxd_snmp_agent_trapv3_send
SNMPv3 트랩 보내기(IPv4 및 IPv6)

### <a name="prototype"></a>프로토타입

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Description

이 서비스는 SNMP 트랩을 지정된 IP 주소의 SNMP 관리자로 보냅니다. 이 트랩은 SNMP v3 PDU에 포함된 트랩 메시지 형식을 제외하고 기본적으로 SNMP v2 트랩과 동일합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **ip_address** SNMP 관리자의 IP(IPv4 또는 IPv6) 주소입니다.
- **username** 커뮤니티 이름(사용자 이름)입니다.
- **trap_type**  
   요청된 트랩의 유형입니다. 표준 이벤트는 다음과 같습니다.
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  
   소유 데이터의 경우:
   - NX_SNMP_TRAP_CUSTOM(0xFFFFFFFF)(nxd_snmp.h에 정의됨)

- **elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).
- **object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다. 목록은 NX_NULL 로 종료됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.
- **NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.
- **NX_NOT_ENABLED**(0x14) SNMPv3가 사용하도록 설정되지 않습니다.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR**(0x104) 지원되지 않는 IP 버전입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a>nxd_snmp_agent_trapv3_oid_send
OID를 직접 지정하는 SNMPv3 트랩 보내기 

### <a name="prototype"></a>프로토타입

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 주소(IPv4/IPv6)의 SNMP 관리자에 SNMPv3 트랩을 보내고 호출자가 직접 OID를 지정할 수 있도록 허용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **ip_address** SNMP 관리자의 IP 주소에 대한 포인터입니다.
- **username** 사용자 이름(커뮤니티 이름)입니다.
- **oid** OID를 포함하는 버퍼에 대한 포인터입니다.
- **elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).
- **object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다. 목록은 NX_NULL 로 종료됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.
- **NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.
- **NX_PTR_ERROR**(0x16) 잘못된 SNMP 에이전트 또는 매개 변수 포인터입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 대상 IP 주소입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a>nx_snmp_agent_v3_context_boots_set
다시 부팅 수 설정(SNMPv3를 사용하도록 설정한 경우)

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a>Description

이 서비스는 SNMP 에이전트가 기록한 다시 부팅 횟수를 설정합니다. 이 서비스는 부팅 수가 SNMPv3 프로토콜에서만 사용되므로 SNMP 에이전트에 대해 SNMPv3를 사용하도록 설정한 경우에만 사용할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.
- **boots** SNMP 에이전트 부팅 횟수를 설정할 값입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 부팅 횟수를 설정했습니다.
- **NX_SNMP_ERROR**(0X100) 부팅 횟수 설정 오류
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a>nx_snmp_object_compare
두 개체 비교 

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a>Description

이 서비스는 제공된 개체 ID를 참조 개체 ID와 비교합니다. 두 개체 ID는 모두 ASCII SMI-S 표기법으로 되어 있습니다. 예를 들어, 두 개체는 모두 ASCII 문자열 "1.3.6"으로 시작해야 합니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 nx_snmp_object_compare_extended()로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **object** 개체 ID에 대한 포인터입니다.
- **reference_object** 참조 개체 ID에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 개체가 참조 개체와 일치합니다.
- **NX_SNMP_NEXT_ENTRY**(0x101) 개체가 참조 개체보다 작습니다.
- **NX_SNMP_ERROR**(0x100) 개체가 참조 개체보다 큽니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a>nx_snmp_object_compare_extended
두 개체 비교 

### <a name="prototype"></a>프로토타입

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a>Description

이 서비스는 제공된 개체 ID를 참조 개체 ID와 비교합니다. 두 개체 ID는 모두 ASCII SMI-S 표기법으로 되어 있습니다. 예를 들어, 두 개체는 모두 ASCII 문자열 "1.3.6"으로 시작해야 합니다.

이 서비스는 nx_snmp_object_compare()를 대신합니다. 이 버전을 사용하려면 호출자가 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **request_object** 요청 개체 ID에 대한 포인터입니다.
- **request_object_length** 요청 개체 ID의 길이입니다.
- **reference_object** 참조 개체 ID에 대한 포인터입니다.
- **reference_object_length** 참조 개체 ID의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 개체가 참조 개체와 일치합니다.
- **NX_SNMP_NEXT_ENTRY**(0x101) 개체가 참조 개체보다 작습니다.
- **NX_SNMP_ERROR**(0x100) 개체가 참조 개체보다 큽니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a>nx_snmp_object_copy
개체 복사 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a>Description

이 서비스는 ASCII SIM 표기법의 소스 개체를 대상 개체로 복사합니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_object_name** 소스 개체 ID에 대한 포인터입니다.
- **destination_object_name** 대상 개체 ID에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **size** 대상 이름으로 복사할 바이트 수입니다. 오류가 발생하면 0이 반환됩니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a>nx_snmp_object_copy_extended
개체 복사 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a>Description

이 서비스는 ASCII SIM 표기법의 소스 개체를 대상 개체로 복사합니다.

이 서비스는 nx_snmp_object_copy()를 대신합니다. 이 버전을 사용하려면 호출자가 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_object_name** 소스 개체 ID에 대한 포인터입니다.
- **source_object_name_length** 소스 개체 ID의 길이입니다.
- **destination_object_name_buffer** 대상 개체 버퍼에 대한 포인터입니다.
- **destination_object_name_buffer_size** 대상 개체 버퍼의 크기입니다.

### <a name="return-values"></a>반환 값

- **size** 대상 이름으로 복사할 바이트 수입니다. 오류가 발생하면 0이 반환됩니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a>nx_snmp_object_counter_get
카운터 개체 가져오기 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Description

이 서비스는 소스 포인터로 지정된 주소에서 카운터 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다. 이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_ptr** 카운터 소스에 대한 포인터입니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 카운터 개체가 검색되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a>nx_snmp_object_counter_set
카운터 개체 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 대상 포인터로 지정된 주소의 카운터를 NetX 개체 데이터 구조의 카운터 값으로 설정합니다. 이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **destination_ptr** 카운터 대상에 대한 포인터입니다.
- **object_data** 카운터 소스 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 카운터 개체가 설정되었습니다.
- **NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a>nx_snmp_object_counter64_get
64비트 카운터 개체 가져오기 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 소스 포인터로 지정된 주소에서 64비트 카운터 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다. 이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_ptr** 카운터 소스에 대한 포인터입니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 카운터 개체가 검색되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a>nx_snmp_object_counter64_set
64비트 카운터 개체 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Description

이 서비스는 대상 포인터로 지정된 주소의 64비트 카운터를 NetX 개체 데이터 구조의 카운터 값으로 설정합니다. 이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **destination_ptr** 카운터 대상에 대한 포인터입니다.
- **object_data** 카운터 소스 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 카운터 개체가 설정되었습니다.
- **NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a>nx_snmp_object_end_of_mib
end-of-mib 값 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 MIB의 끝에 신호를 보내는 개체를 만들며 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **not_used_ptr** 포인터가 사용되지 않습니다. NX_NULL이어야 합니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) end-of-mib 개체가 빌드되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a>nx_snmp_object_gauge_get
계기 개체 가져오기 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 소스 포인터로 지정된 주소에서 계기 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다. 이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_ptr** 계기 소스에 대한 포인터입니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 계기 개체가 검색되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a>nx_snmp_object_gauge_set
계기 개체 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 대상 포인터로 지정된 주소의 계기를 NetX 개체 데이터 구조의 계기 값으로 설정합니다. 이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **destination_ptr** 계기 대상에 대한 포인터입니다.
- **object_data** 계기 소스 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 계기 개체가 설정되었습니다.
- **NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a>nx_snmp_object_id_get
개체 ID 가져오기 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 소스 포인터로 지정된 주소에서 개체 ID(ASCII SIM 표기법)를 검색한 후 NetX 개체 데이터 구조에 배치합니다. 이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_ptr** 개체 ID 소스에 대한 포인터입니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 개체 ID가 검색되었습니다.
- **NX_SNMP_ERROR**(0X100) 잘못된 개체 길이
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a>nx_snmp_object_id_set
개체 ID 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 대상 포인터로 지정된 주소의 개체 ID(ASCII SIM 표기법)를 NetX 개체 데이터 구조의 개체 ID로 설정합니다. 이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **destination_ptr** 개체 ID 대상에 대한 포인터입니다.
- **object_data** 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 개체 ID가 설정되었습니다.
- **NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a>nx_snmp_object_integer_get
정수 개체 가져오기 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 소스 포인터로 지정된 주소에서 정수 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다. 이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_ptr** 정수 소스에 대한 포인터입니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 정수 개체가 검색되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a>nx_snmp_object_integer_set
정수 개체 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 대상 포인터로 지정된 주소의 정수를 NetX 개체 데이터 구조의 정수 값으로 설정합니다. 이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **destination_ptr** 정수 대상에 대한 포인터입니다.
- **object_data** 정수 소스 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 정수 개체가 설정되었습니다.
- **NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a>nx_snmp_object_ip_address_get
IP 주소 개체 가져오기(IPv4만 해당)

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 소스 포인터로 지정된 주소에서 IP 주소 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다. 이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_ptr** IPv4 주소 소스에 대한 포인터입니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 주소 개체가 검색되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a>nx_snmp_object_ipv6_address_get
IP 주소 개체 가져오기(IPv6만 해당)

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a>Description

이 서비스는 소스 포인터로 지정된 주소에서 IPv6 주소 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다.
이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_ptr** IPv6 주소 소스에 대한 포인터입니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 주소 개체가 검색되었습니다.
- **NX_SNMP_ERROR_WRONGTYPE**(0X07) 잘못된 입력 SNMP 개체 코드
- **NX_NOT_ENABLED**(0x14) IPv6가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a>nx_snmp_object_ip_address_set
IPv4 주소 개체 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 대상 포인터로 지정된 주소의 IPv4 주소를 NetX 개체 데이터 구조의 IP 주소로 설정합니다. 이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **destination_ptr** 설정할 IP 주소에 대한 포인터입니다.
- **object_data** IP 주소 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 주소 개체가 설정되었습니다.
- **NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a>nx_snmp_object_ipv6_address_set
IPv6 주소 개체 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a>Description

이 서비스는 대상 포인터로 지정된 주소의 IPv6 주소를 NetX 개체 데이터 구조의 IP 주소로 설정합니다. 이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **destination_ptr** 설정할 IP 주소에 대한 포인터입니다.
- **object_data** IP 주소 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IPv6 주소가 설정되었습니다.
- **NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.
- **NX_NOT_ENABLED**(0x14) IPv6가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a>nx_snmp_object_no_instance
no-instance 개체 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 지정된 개체의 인스턴스가 없음을 신호로 알리는 개체를 만들며 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **not_used_ptr** 포인터가 사용되지 않습니다. NX_NULL이어야 합니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) no-instance 개체가 빌드되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a>nx_snmp_object_not_found
not-found 개체 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 개체를 찾을 수 없다는 신호를 보내는 개체를 만들며 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **not_used_ptr** 포인터가 사용되지 않습니다. NX_NULL이어야 합니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) not-found 개체가 빌드되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a>nx_snmp_object_octet_string_get
옥텟 문자열 개체 가져오기 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a>Description

이 서비스는 소스 포인터로 지정된 주소에서 옥텟 문자열을 검색한 후 NetX 개체 데이터 구조에 배치합니다. 이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_ptr** 옥텟 문자열 소스에 대한 포인터입니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.
- **length** 옥텟 문자열의 바이트 수입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 옥텟 문자열 개체가 검색되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a>nx_snmp_object_octet_string_set
옥텟 문자열 개체 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 대상 포인터로 지정된 주소의 옥텟 문자열을 NetX 개체 데이터 구조의 옥텟 문자열로 설정합니다. 이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **destination_ptr** 옥텟 문자열 대상에 대한 포인터입니다.
- **object_data** 옥텟 문자열 소스 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 옥텟 문자열 개체가 설정되었습니다.
- **NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a>nx_snmp_object_string_get
ASCII 문자열 개체 가져오기 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 소스 포인터로 지정된 주소에서 ASCII 문자열을 검색한 후 NetX 개체 데이터 구조에 배치합니다. 이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_ptr** ASCII 문자열 소스에 대한 포인터입니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ASCII 문자열 개체가 검색되었습니다.
- **NX_SNMP_ERROR**(0X100) 문자열이 너무 큽니다.  
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a>nx_snmp_object_string_set
ASCII 문자열 개체 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 대상 포인터로 지정된 주소의 ASCII 문자열을 NetX 개체 데이터 구조의 ASCII 문자열로 설정합니다. 이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **destination_ptr** ASCII 문자열 대상에 대한 포인터입니다.
- **object_data** ASCII 문자열 소스 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ASCII 문자열 개체가 설정되었습니다.
- **NX_SNMP_ERROR**(0X100) 문자열이 너무 큽니다.
- **NX_SNMP_ERROR_BADVALUE**(0x03) 문자열에 잘못된 문자가 있습니다.
- **NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a>nx_snmp_object_timetics_get
timetics 개체 가져오기 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 소스 포인터로 지정된 주소에서 timetics를 검색한 후 NetX 개체 데이터 구조에 배치합니다. 이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **source_ptr** timetics 소스에 대한 포인터입니다.
- **object_data** 대상 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) timetics 개체가 검색되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a>nx_snmp_object_timetics_set
timetics 개체 설정 

### <a name="prototype"></a>프로토타입

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Description

이 서비스는 대상 포인터로 지정된 주소의 timetics 변수를 NetX 개체 데이터 구조의 timetics로 설정합니다.
이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **destination_ptr** timetics 대상에 대한 포인터입니다.
- **object_data** timetics 소스 개체 구조에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) timetics 개체가 설정되었습니다.
- **NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```