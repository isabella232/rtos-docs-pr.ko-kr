---
title: 4장 - Azure RTOS NetX Duo DHCPv6 클라이언트 서비스
description: 이 장에서는 아래에 나열된 모든 Azure RTOS NetX Duo DHCPv6 클라이언트 서비스에 대해 사전순으로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6caf943f990f8fe5cbd2cd6139a1253fcaf47dc207141963e31a9e31864ef839
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791740"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a>4장 - Azure RTOS NetX Duo DHCPv6 클라이언트 서비스

이 장에서는 아래에 나열된 모든 Azure RTOS NetX Duo DHCPv6 클라이언트 서비스에 대해 사전순으로 설명합니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- **nx_dhcpv6_client_create:** *DHCPv6 클라이언트 인스턴스 만들기* 

- **nx_dhcpv6_client_delete:** *DHCPv6 클라이언트 인스턴스 삭제* 

- **nx_dhcpv6_create_ client_duid:** *DHCPv6 클라이언트 DUID 만들기* 

- **nx_dhcpv6 _add_client_ia:** *DHCPv6 클라이언트 IA(ID 주소) 추가* 

- **nx_dhcpv6 _create_client_ia:** (*DHCPv6 클라이언트 IA(ID 주소) 추가의 레거시)* 

- **nx_dhcpv6_create_client_iana:** *IANA(비 임시 주소용 ID 연결)에 대해 DHCPv6 클라이언트 ID 연결 만들기* 

- **nx_dhcpv6_get_client_duid_time_id:** *DHCPv6 클라이언트 DUID에서 시간 ID 가져오기* 

- **nx_dhcpv6_client_set_interface:** *DHCPv6 서버와 통신하기 위해 클라이언트 네트워크 인터페이스 설정* 

- **nx_dhcpv6_get_IP_address:** *DHCPv6 클라이언트에 할당된 전역 IPv6 주소 가져오기* 

- **nx_dhcpv6_get_lease_time_data:** *클라이언트 전역 IPv6 주소에 대한 T1, T2, 유효한 수명, 기본 설정 수명 가져오기*

- **nx_dhcpv6_get_valid_ip_address_lease_time:** *주소 인덱스별로 DHCPv6 클라이언트 IPv6 주소에 대한 T1, T2, 유효한 수명, 기본 설정 수명 가져오기* 

- **nx_dhcpv6_get_iana_lease_time:** *DHCPv6 클라이언트에 임대된 ID 연결(IANA)의 T1 및 T2 가져오기* 

- **nx_dhcpv6_get_other_option_data:** *도메인 이름 또는 표준 시간대 서버와 같은 지정된 옵션 데이터 가져오기* 

- **nx_dhcpv6_get_DNS_server_address:** *지정된 인덱스의 DNS 서버 주소를 DHCPv6 클라이언트 DNS 서버 목록으로 가져오기* 

- **nx_dhcpv6_get_time_accrued:** *전역 IPv6 주소 임대가 DHCPv6 클라이언트에 바인딩되어 있는 누적 시간 가져오기* 

- **nx_dhcpv6_get_time_server_address:** *지정된 인덱스의 시간 서버 주소를 DHCPv6 클라이언트 시간 서버 목록으로 가져오기*

- **nx_dhcpv6_get_valid_ip_address_count:** *DHCPv6 클라이언트에 할당된 IPv6 주소 수 가져오기* 

- **nx_dhcpv6_reinitialize:** *DHCPv6 클라이언트 상태 시스템을 다시 시작하고 DHCPv6 프로토콜을 다시 실행하기 위해 DHCPv6 다시 초기화* 

- **nx_dhcpv6_request_confirm:** *서버에 CONFIRM 요청 보내기* 

- **nx_dhcpv6_request_inform_request:** 서 *버에 INFORM REQUEST 메시지 보내기* 

- **nx_dhcpv6_request_release:** *서버에 RELEASE 요청 보내기* 

- **nx_dhcpv6_request_option_DNS_server:** *서버에 대한 요청 메시지의 클라이언트 옵션 요청 데이터에 DNS 서버 옵션 추가* 

- **nx_dhcpv6_request_option_FQDN:** *서버에 대한 요청 메시지의 클라이언트 옵션 요청 데이터에 FQDN 옵션 추가* 

- **nx_dhcpv6_request_option_domain_name:** *서버에 대한 요청 메시지의 클라이언트 옵션 요청 데이터에 도메인 이름 옵션 추가* 

- **nx_dhcpv6_request_option_time_server:** *서버에 대한 요청 메시지의 클라이언트 옵션 요청 데이터에 시간 서버 옵션 추가* 

- **nx_dhcpv6_request_option_timezone:** *서버에 대한 요청 메시지의 클라이언트 옵션 요청 데이터에 표준 시간대 옵션 추가* 

- **nx_dhcpv6_request_solicit:** *클라이언트 네트워크(브로드캐스트)의 모든 서버에 DHCPv6 SOLICIT 요청 보내기* 

- **nx_dhcpv6_request_solicit_rapid:** *빠른 커밋 옵션이 설정된 클라이언트 네트워크(브로드캐스트)의 모든 서버에 DHCPv6 SOLICIT 요청 보내기* 

- **nx_dhcpv6_resume:** *DHCPv6 클라이언트 처리 다시 시작* 

- **nx_dhcpv6_start:** *DHCPv6 클라이언트 스레드 작업 시작. 이 작업은 DHCPv6 상태 시스템을 시작하는 것과 동일하지 않으며 SOLICIT 요청을 보내지 않습니다.* 

- **nx_dhcpv6_stop:** *DHCPv6 클라이언트 스레드 작업 중지* 

- **nx_dhcpv6_suspend:** *DHCPv6 클라이언트 스레드 작업 일시 중단* 

- **nx_dhcpv6_set_time_accrued:** *클라이언트 레코드에서 전역 클라이언트 IPv6 주소 임대의 누적 시간 설정*

## <a name="nx_dhcpv6_client_create"></a>nx_dhcpv6_client_create

DHCPv6 클라이언트 인스턴스 만들기

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 서비스는 콜백 함수를 포함하는 DHCPv6 클라이언트 인스턴스를 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 제어 블록에 대한 포인터  

- **client_ptr** 클라이언트 인스턴스에 대한 포인터  

- **name_ptr** DHCPv6 인스턴스의 이름에 대한 포인터

- **packet_pool_ptr** 클라이언트 패킷 풀에 대한 포인터

- **stack_ptr** 클라이언트 스택 메모리에 대한 포인터

- **stack_size** 클라이언트 스택 메모리의 크기

- **dhcpv6_state_change_notify** 클라이언트가 서버에 대한 새 DHCPv6 요청을 시작할 때 호출되는 콜백 함수에 대한 포인터

- **dhcpv6_server_error_handler** 클라이언트가 서버에서 오류 상태를 받을 때 호출되는 콜백 함수에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적으로 클라이언트 생성

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_client_delete

## <a name="nx_dhcpv6_client_delete"></a>nx_dhcpv6_client_delete

DHCPv6 클라이언트 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 DHCPv6 클라이언트 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적인 DHCPv6 삭제

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_client_create

## <a name="nx_dhcpv6_client_set_interface"></a>nx_dhcpv6_client_set_interface

DHCPv6에 대한 클라이언트의 네트워크 인터페이스 설정

### <a name="prototype"></a>프로토타입

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a>Description

이 서비스는 DHCPv6 서버와 통신하기 위한 클라이언트의 네트워크 인터페이스를 지정된 입력 인터페이스 인덱스로 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **interface_index** 네트워크 인터페이스를 지정하는 인덱스

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 인터페이스가 성공적으로 설정됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_INVALID_INTERFACE (0x4C) 잘못된 인터페이스 인덱스

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_client _create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_client_set_destination_address"></a>nx_dhcpv6_client_set_destination_address

DHCPv6 메시지를 보낼 대상 주소 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a>Description

이 서비스는 DHCPv6 메시지를 보내야 하는 대상 주소를 설정합니다. 기본적으로 ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2)입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **destination_address** 대상 주소

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 인터페이스가 성공적으로 설정됨

- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

- NX_DHCPV6_PARAM_ERROR (0xE93) 매개 변수 오류

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_client _create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_create_client_duid"></a>nx_dhcpv6_create_client_duid

클라이언트 DUID 개체 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a>Description

이 서비스는 입력 매개 변수를 사용하여 클라이언트 DUID를 만듭니다. 입력이 제공되지 않고 DUID 형식이 시간이 포함된 링크 계층을 나타내는 경우 이 함수는 고유성을 위해 임의로 선택할 요소가 포함된 시간을 제공합니다. 공급업체에서 할당한 (엔터프라이즈) DUID 형식은 지원되지 않습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **duid_type** DUID 형식(하드웨어, 엔터프라이즈 등)

- **hardware_type** 네트워크 하드웨어, 예: IEEE 802

- **시간** 고유 식별자를 만드는 데 사용되는 값

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적으로 클라이언트가 생성됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력

- NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID 형식을 알 수 없거나 해당 형식이 지원되지 않음 

- NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID 하드웨어 형식을 알 수 없거나 해당 형식이 지원되지 않음

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_create_client_ia
- nx_dhcpv6_create_client_iana
- nx_dhcpv6_create_server_duid

## <a name="nx_dhcpv6_create_client_ia"></a>nx_dhcpv6_create_client_ia

클라이언트에 ID 연결 추가

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a>Description

이 서비스는 *nx_dhcpv6_add_client_ia* 서비스와 동일합니다. 클라이언트 레코드를 제공된 매개 변수로 채워서 클라이언트 ID 연결을 추가합니다. 최대 기본 설정 수명 및 유효한 수명을 요청하려면 이러한 매개 변수를 infinity로 설정합니다. 하나 이상의 IA를 DHCPv6 클라이언트에 추가하려면 NX_DHCPV6_MAX_IA_ADDRESS를 기본값인 1보다 큰 값으로 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **ipv6_address** NetX Duo IP 주소 블록에 대한 포인터

- **preferred_lifetime** IP 주소가 더 이상 사용되지 않게 될 때까지의 시간

- **valid_lifetime** IP 주소가 만료될 때까지의 시간

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적으로 클라이언트 IA가 추가됨

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST**(0xEAF) 중복 IA 주소 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS**(0xEAE) IA가 클라이언트에서 저장할 수 있는 최대 IA 수를 초과함

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) IA의 잘못된(예: Null) IA 주소

- NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력


### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_add_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_create_client_iana"></a>nx_dhcpv6_create_client_iana

클라이언트에 대한 ID 연결(비 임시) 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a>Description

이 서비스는 제공된 매개 변수에서 클라이언트 IANA(비 임시 주소용 ID 연결)를 만듭니다. DHCPv6 클라이언트 요청에서 T1 및 T2 시간을 최대(infinity)로 설정하려면 이러한 매개 변수를 NX_DHCPV6_INFINITE_LEASE로 설정합니다. 

> [!NOTE]
> 클라이언트에는 IANA가 하나만 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **IA_ident** ID 연결 고유 식별자

- **T1** 클라이언트가 IPv6 주소 갱신을 시작해야 하는 시간

- **T2** 클라이언트가 theIPv6 주소 리바인딩을 시작해야 하는 시간

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적으로 IANA가 생성됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_add_client_ia

## <a name="nx_dhcpv6_add_client_ia"></a>nx_dhcpv6_add_client_ia 

클라이언트에 ID 연결 추가

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 레코드를 제공된 매개 변수로 채워서 클라이언트 ID 연결을 추가합니다. 최대 기본 설정 수명 및 유효한 수명을 요청하려면 이러한 매개 변수를 infinity로 설정합니다. 하나 이상의 IA를 DHCPv6 클라이언트에 추가하려면 NX_DHCPV6_MAX_IA_ADDRESS를 기본값인 1보다 큰 값으로 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **ipv6_address** NetX Duo IP 주소 블록에 대한 포인터

- **preferred_lifetime** IP 주소가 더 이상 사용되지 않게 될 때까지의 시간

- **valid_lifetime** IP 주소가 만료될 때까지의 시간 

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적으로 클라이언트 IA가 추가됨

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST**(0xEAF) 중복 IA 주소 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS**(0xEAE) IA가 클라이언트에서 저장할 수 있는 최대 IA 수를 초과함

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) IA의 잘못된(예: Null) IA 주소

- NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력

 
### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_get_client_duid_time_id"></a>nx_dhcpv6_get_client_duid_time_id

클라이언트 DUID에서 시간 ID 검색

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 DUID에서 시간 ID 필드를 검색합니다. 애플리케이션에서 먼저 *nx_dhcpv6_create_client_duid* 를 호출해야 하는 경우에는 DHCPv6 클라이언트 인스턴스에서 클라이언트 DUID를 채웁니다. 그러지 않으면 이 필드에 Null 값이 포함됩니다. 이 작업의 목적은 애플리케이션에서 이 데이터를 저장하고 여러 번의 다시 부팅에 걸쳐 시간 필드를 포함하여 동일한 클라이언트 DUID를 서버에 제공하기 위한 것입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **time_id** 클라이언트 DUID 시간 필드에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 임대 데이터가 성공적으로 검색됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_time_lease_data
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_ip_address"></a>nx_dhcpv6_get_IP_address

클라이언트의 전역 IPv6 주소 검색

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a>Description

이 서비스는 클라이언트의 전역 IPv6 주소를 검색합니다. 클라이언트에 유효한 주소가 없으면 오류 상태가 반환됩니다. 클라이언트에 두 개 이상의 전역 IPv6 주소가 있는 경우 주 IPv6 주소가 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **ip_address** IPv6 주소에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IPv6 주소가 성공적으로 할당됨

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID**(0xEAD) IPv6 주소가 유효하지 않음

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_lease_time_data"></a>nx_dhcpv6_get_lease_time_data

클라이언트의 IA 주소 임대 시간 데이터 검색

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a>Description

이 서비스는 클라이언트의 전역 IA 주소 시간 데이터를 검색합니다. 클라이언트 IA 주소 상태가 잘못된 경우 시간 데이터가 0으로 설정되고 성공적인 완료 상태가 반환됩니다. 클라이언트에 두 개 이상의 전역 IPv6 주소가 있는 경우 주 IA 주소 데이터가 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **T1** IA 주소 갱신 시간에 대한 포인터

- **T2** IA 주소의 다시 바인딩 시간에 대한 포인터

- **preferred_lifetime** IA 주소가 더 이상 사용되지 않게 되는 시간에 대한 포인터

- **valid_lifetime** IA 주소가 만료되는 시간에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IA 임대 데이터가 성공적으로 검색됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_iana_lease_time

## <a name="nx_dhcpv6_get_iana-lease_time"></a>nx_dhcpv6_get_iana lease_time

클라이언트의 IANA 임대 시간 데이터 검색

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a>Description

이 서비스는 클라이언트의 전역 IA-NA 임대 시간 데이터(T1 및 T2)를 검색합니다. 클라이언트 IA-NA 주소에 유효한 주소 상태가 없는 경우 시간 데이터가 0으로 설정되고 성공적인 완료 상태가 반환됩니다. 클라이언트에 두 개 이상의 전역 IPv6 주소가 있는 경우 주 IA 주소 데이터가 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **T1** 임대 갱신을 시작하는 시간에 대한 포인터

- **T2** 임대 다시 바인딩 시작 시간에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IANA 임대 데이터가 성공적으로 검색됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a>nx_dhcpv6_get_valid_ip_address_count

클라이언트의 유효한 IA 주소 수 검색

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a>Description

이 서비스는 클라이언트의 유효한 IPv6 주소 수를 검색합니다. 유효한 IPv6 주소는 클라이언트에 바인딩(할당)되고 IP 인스턴스에 등록됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **address_count** 반환할 주소 수에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IANA 임대 데이터가 성공적으로 검색됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a>nx_dhcpv6_get_valid_ip_address_lease_time

주소 인덱스를 기준으로 클라이언트 IA 데이터 검색

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a>Description

이 서비스는 클라이언트의 IA 주소를 검색하고 주소 인덱스를 기준으로 데이터를 임대합니다. 잘못된 인덱스를 제공하거나 해당 인덱스의 IPv6 주소가 잘못된 경우 서비스는 NX_DHCPV6_IA_ADDRESS_NOT_VALID 오류 상태를 반환합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **address_index** DHCPv6 IA 테이블로 인덱싱

- **ip_address** 검색할 IPv6 주소에 대한 포인터

- **preferred_lifetime** IA 주소가 더 이상 사용되지 않게 되는 시간에 대한 포인터

- **valid_lifetime** IA 주소가 만료되는 시간에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IANA 데이터가 성공적으로 검색됨

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID**(0xEAD) 잘못된 인덱스 또는 제공된 인덱스에 유효한 IPv6 주소 없음 

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_iana_lease_time
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_dns_server_address"></a>nx_dhcpv6_get_DNS_server_address

DNS 서버 주소 검색 

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 목록의 지정된 인덱스에 있는 DNS 서버 IPv6 주소 데이터를 검색합니다. 목록이 인덱스에 서버 주소를 포함하지 않는 경우 오류가 반환됩니다. 인덱스는 사용자 구성 가능한 옵션인 NX_DHCPV6_NUM_DNS_SERVERS로 지정된 DNS 서버 목록의 크기를 초과할 수 없습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **index** DNS 서버 목록에 대한 인덱스

- **server_address** 서버 주소 버퍼에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 주소가 성공적으로 검색됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_other_option_data"></a>nx_dhcpv6_get_other_option_data

DHCPv6 옵션 데이터 검색 

### <a name="prototype"></a>프로토타입

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a>Description

이 서비스는 지정된 옵션 코드에 대해 DHCPv6 메시지에서 DHCPv6 옵션 데이터를 검색합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **option** 코드 검색할 데이터가 있는 옵션 코드

- **buffer** 데이터를 복사할 버퍼에 대한 포인터 

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 옵션 데이터가 성공적으로 검색됨

- **NX_DHCPV6_UNKNOWN_OPTION**(0xEAB) 알 수 없거나 지원되지 않는 옵션 코드

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_DHCPV6_PARAM_ERROR (0xE93) 잘못된 비 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_time_accrued"></a>nx_dhcpv6_get_time_accrued

클라이언트의 IP 주소 임대의 누적 시간 검색

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a>Description

이 서비스는 클라이언트의 IPv6 주소 임대의 누적 시간을 검색합니다. 함수는 첫 번째 유효한 주소의 클라이언트에 할당된 모든 IPv6 주소를 확인합니다. 유효한 주소가 없으면 누적 시간에 대해 0 값이 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **time_accrued** IP 임대에서 누적 시간에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 누적 시간이 성공적으로 검색됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_set_time_accrued

## <a name="nx_dhcpv6_get_time_server_address"></a>nx_dhcpv6_get_time_server_address

시간 서버 주소 검색 

### <a name="prototype"></a>프로토타입

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 목록의 지정된 인덱스에 있는 시간 서버 IPv6 주소 데이터를 검색합니다. 목록이 인덱스에 서버 주소를 포함하지 않는 경우 오류가 반환됩니다. 인덱스는 사용자 구성 가능한 옵션인 NX_DHCPV6_NUM_TIME_SERVERS로 지정된 시간 서버 목록의 크기를 초과할 수 없습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **index** 시간 서버 목록에 대한 인덱스

- **server_address** 서버 주소 버퍼에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 주소가 성공적으로 검색됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_DNS_server_address

## <a name="nx_dhcpv6_reinitialize"></a>nx_dhcpv6_reinitialize

IP 테이블에서 클라이언트 IP 주소 제거

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCPv6 상태 시스템을 다시 시작하고 DHCPv6 프로토콜을 다시 실행하기 위해 클라이언트를 다시 초기화합니다. 클라이언트에서 이전에 DHPCv6 상태 시스템을 시작하지 않았거나 IPv6 주소가 할당된 경우에는 이 작업이 필요하지 않습니다. DHCPv6 클라이언트에 저장되고 IP 인스턴스에 등록된 주소는 모두 지워집니다.

> [!NOTE]
> 애플리케이션은 여전히 *nx_dhcpv6_start 서비스* 를 사용하여 DHCPv6 클라이언트를 시작하고 *nx_dhcpv6_request_solicit* 를 호출하여 IPv6 주소 할당에 대한 요청을 시작해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 주소가 성공적으로 제거됨

- **NX_DHCPV6_ALREADY_STARTED**(0xE91) DHCPv6 클라이언트가 이미 실행 중임

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_stop
- nx_dhcpv6_start

## <a name="nx_dhcpv6_request_confirm"></a>nx_dhcpv6_request_confirm

클라이언트의 CONFIRM 상태 처리

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 CONFIRM 요청을 보냅니다. 서버에서 회신을 받으면 DHCPv6 클라이언트가 받은 데이터를 사용하여 임대 매개 변수를 업데이트합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) CONFIRM 메시지가 성공적으로 전송 및 처리됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release
- nx_dhcpv6_request_solicit


## <a name="nx_dhcpv6_request_inform_request"></a>nx_dhcpv6_request_inform_request

클라이언트의 INFORM REQUEST 상태 처리

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 INFORM REQUEST 메시지를 보냅니다. 회신을 받으면 회신이 유효하며 서버에서 요청을 허용했는지 확인하도록 처리됩니다. 그런 다음, 필요에 따라 클라이언트 인스턴스가 서버 정보로 업데이트 됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) INFORM REQUEST 메시지가 성공적으로 생성 및 처리되었음

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_request_confirm

## <a name="nx_dhcpv6_request_option_dns_server"></a>nx_dhcpv6_request_option_DNS_server

DHCPv6 옵션 요청에 DNS 서버 추가

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCPv6 옵션 요청에 DNS 서버 정보를 요청하기 위한 옵션을 추가합니다. 서버 회신에 DNS 서버 데이터가 포함되는 경우 저장할 공간이 있으면 클라이언트에서 DNS 서버를 저장합니다. 클라이언트가 저장할 수 있는 DNS 서버 수는 구성 가능한 옵션인 NX_DHCPV6_NUM_DNS_SERVERS에 의해 결정됩니다. 기본값은 2입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) DNS 서버 옵션이 포함됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_fqdn"></a>nx_dhcpv6_request_option_FQDN

옵션 요청 목록에 정규화된 도메인 이름 옵션 추가

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a>Description

이 서비스는 DHCPv6 옵션 요청에 클라이언트 정규화된 도메인 이름을 추가하기 위한 옵션을 추가합니다. FQDN 옵션에는 다음과 같은 세 가지 옵션이 있습니다.

- NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 클라이언트에서 사용하는 FQDN 및 주소에 대한 FQDN-IPv6 주소 매핑을 업데이트합니다.

- NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 클라이언트에서 서버에 사용하는 FQDN 및 주소에 대한 FQDN-IPv6 주소 매핑을 업데이트합니다.

- NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 서버가 클라이언트를 대신하여 DNS 업데이트를 수행하지 않도록 요청합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **domain_name** 도메인 이름을 포함하는 문자열

- **op** 적용할 FQDN 옵션 유형(위의 목록 참조)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) FQDN 옵션이 포함됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_domain_name"></a>nx_dhcpv6_request_option_domain_name

DHCPv6 옵션 요청에 도메인 이름 옵션 추가

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 요청 메시지의 옵션 요청에 도메인 이름 옵션을 추가합니다. 서버 회신이 도메인 이름 데이터를 포함하는 경우 도메인 이름의 크기가 도메인 이름을 보유할 수 있는 버퍼 크기 내에 있으면 클라이언트에서 도메인 이름 정보를 저장합니다. 이 버퍼 크기는 구성 가능한 옵션(NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE)이며 기본 값은 30바이트입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 도메인 이름 옵션이 설정됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_time_server"></a>nx_dhcpv6_request_option_time_server

시간 서버 데이터를 선택적 요청으로 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 요청 메시지의 옵션 요청에 시간 서버 정보에 대한 옵션을 추가합니다. 서버 응답이 시간 서버 데이터를 포함하는 경우 클라이언트가 시간 서버를 저장할 공간이 있는 경우 시간 서버를 저장합니다. 클라이언트가 저장할 수 있는 시간 서버 수는 구성 가능한 옵션에 따라 결정됩니다.

이 옵션은 NX_DHCPV6_NUM_TIME _SERVERS이며 기본값은 1입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 시간 서버 옵션이 추가됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_timezone"></a>nx_dhcpv6_request_option_timezone

표준 시간대 데이터를 선택적 요청으로 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 옵션 요청에 표준 시간대 정보를 요청하는 옵션을 추가합니다. 서버 회신에 표준 시간대 데이터가 포함된 경우 표준 시간대의 크기가 표준 시간대를 보유할 수 있는 버퍼 크기 내에 있으면 클라이언트가 표준 시간대 정보를 저장합니다. 이 버퍼 크기는 구성 가능한 옵션(NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE)이며 기본값은 10 바이트입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 표준 시간대 옵션이 추가됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server

## <a name="nx_dhcpv6_request_release"></a>nx_dhcpv6_request_release

DHCPv6 RELEASE 메시지 보내기

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 네트워크에서 RELEASE 메시지를 보냅니다. 메시지가 성공적으로 전송되면 성공적인 상태가 반환됩니다. 성공적인 완료가 클라이언트에서 응답을 수신했거나 IPv6 주소를 부여했음을 의미하지는 않습니다. DHCPv6 클라이언트 스레드 작업은 DHCPv6 서버의 응답을 기다립니다. 회신을 받으면 회신이 유효한지 확인하고 데이터를 클라이언트 레코드에 저장합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) RELEASE 메시지가 성공적으로 전송됨

- **NX_DHCPV6_NOT_STARTED**(0xE92) DHCPv6 클라이언트 작업이 시작되지 않음

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID**(0xEAD) 클라이언트에 바인딩되지 않은 주소

- **NX_INVALID_INTERFACE**(0x4C) IP 주소 테이블에서 찾을 수 없음

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_solicit

## <a name="nx_dhcpv6_request_solicit"></a>nx_dhcpv6_request_solicit

SOLICIT 메시지 보내기

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 네트워크에서 SOLICIT 메시지를 보냅니다. 메시지가 성공적으로 전송되면 성공적인 상태가 반환됩니다. 성공적인 완료가 클라이언트에서 응답을 수신했거나 IPv6 주소를 부여했음을 의미하지는 않습니다. DHCPv6 클라이언트 스레드 작업은 DHCPv6 서버의 회신(ADVERTISE 메시지)을 기다립니다. 회신을 받으면 회신이 유효한지 확인하고, 데이터를 클라이언트 레코드에 저장하며, 클라이언트를 REQUEST 상태로 승격합니다.

> [!NOTE] 
> 빠른 커밋 옵션이 설정된 경우 올바른 서버 ADVERTISE 메시지를 수신하면 DHCPv6 클라이언트가 바인딩된 상태로 바로 이동됩니다. 자세한 내용은 *nx_dhcpv6_request_solicit_rapid* 에 대한 서비스 설명을 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) SOLICIT 메시지가 전송됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a>nx_dhcpv6_request_solicit_rapid

빠른 커밋 옵션을 사용하여 SOLICIT 메시지 보내기

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 빠른 커밋 옵션을 설정하여 네트워크에서 SOLICIT 메시지를 보냅니다. 메시지가 성공적으로 전송되면 성공적인 상태가 반환됩니다. 성공적인 완료가 클라이언트에서 응답을 수신했거나 IPv6 주소를 부여했음을 의미하지는 않습니다. DHCPv6 클라이언트 스레드 작업은 DHCPv6 서버의 회신(ADVERTISE 메시지)을 기다립니다. 회신을 받으면 회신이 유효한지 확인하고, 데이터를 클라이언트 레코드에 저장하며, 클라이언트를 BOUND 상태로 승격합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) SOLICIT 메시지가 전송됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_request_solicit
- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release

## <a name="nx_dhcpv6_resume"></a>nx_dhcpv6_resume

DHCPv6 클라이언트 작업 다시 시작 

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCPv6 클라이언트 스레드 작업을 다시 시작합니다. 현재 DHCPv6 클라이언트 상태(예: Bound Solicit)가 처리됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트가 성공적으로 다시 시작됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_start
- nx_dhcpv6_stop
- nx_dhcpv6_suspend

## <a name="nx_dhcpv6_set_-time_accrued"></a>nx_dhcpv6_set_ time_accrued

클라이언트의 IP 주소 임대에 대한 누적 시간 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a>Description

이 서비스는 서버에서 할당된 이후 클라이언트의 전역 IP 주소에 대한 누적 시간을 설정합니다. 클라이언트가 현재 할당된 IPv6 주소에 바인딩되어 있는 경우에만 사용해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

- **time_accrued** IP 임대의 시간 누적

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 시간 누적이 성공적으로 설정됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_start"></a>nx_dhcpv6_start

DHCPv6 클라이언트 작업 시작 

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCPv6 클라이언트 작업을 시작하고 DHCPv6 프로토콜 실행을 위해 클라이언트를 준비합니다. 클라이언트 인스턴스에 충분한 정보(예: 클라이언트 DUID)가 있는지 확인하고, DHCPv6 메시지를 보내고 받기 위한 UDP 소켓을 만들고 바인딩하며, 세션 시간을 추적하고 현재 IPv6 임대가 만료되는 시간을 추적하는 타이머를 활성화합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트가 성공적으로 시작됨

- **NX_DHCPV6_MISSING_REQUIRED_OPTIONS**(0xEA9) 클라이언트에 필수 옵션이 없음

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_stop
- nx_dhcpv6_reinitialize

## <a name="nx_dhcpv6_stop"></a>nx_dhcpv6_stop

DHCPv6 클라이언트 작업 중지 

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCPv6 클라이언트 작업을 중지하고 재전송 횟수와 최대 재전송 간격을 지우고 세션 및 임대 만료 타이머를 비활성화하고 DHCPv6 클라이언트 소켓 포트를 바인딩 해제합니다. 클라이언트를 다시 시작하려면 먼저 DHCPv6 서버를 사용하여 다른 세션을 시작하기 전에 클라이언트를 중지하고 필요에 따라 다시 초기화해야 합니다. 자세한 내용은 간단한 예제 섹션을 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트가 성공적으로 중지됨

- **NX_DHCPV6_NOT_STARTED**(0xE92) 클라이언트 스레드가 시작되지 않음

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함


### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_reinitialize
- nx_dhcpv6_start

## <a name="nx_dhcpv6_suspend"></a>nx_dhcpv6_suspend

DHCPv6 클라이언트 작업 일시 중단 

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCPv6 클라이언트 작업 및 처리 중이었던 요청을 일시 중단합니다. 타이머가 비활성화되고 클라이언트 상태가 실행 중이 아닌 것으로 설정됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcpv6_ptr** DHCPv6 클라이언트 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트가 성공적으로 일시 중단됨

- **NX_DHCPV6_NOT_STARTED**(0xE92) 클라이언트가 실행되고 있지 않으므로 일시 중단할 수 없음

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

- NX_CALLER_ERROR (0x11) 스레드에서 호출되어야 함

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a>참고 항목

- nx_dhcpv6_resume
- nx_dhcpv6_start
- nx_dhcpv6_reinitialize
- nx_dhcpv6_stop
