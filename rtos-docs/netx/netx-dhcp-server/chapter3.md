---
title: 3장 - Azure RTOS NetX DHCP 서버 서비스 설명
description: 이 장에는 모든 Azure RTOS NetX DHCP 서버 서비스 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 702499184b12484fa5862ba83ff3fadb8fccea31089b6bf8b71daf267e8c84a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799526"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a>3장 - Azure RTOS NetX DHCP 서버 서비스 설명

이 장에는 모든 NetX DHCP 서버 서비스 설명이 포함되어 있습니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- **nx_dhcp_server_create**: *DHCP 서버 인스턴스 만들기*
- **nx_dhcp_set_interface_network_parameters**: *지정된 인터페이스의 중요한 네트워크 매개 변수에 대한 DHCP 서버 옵션 설정*
- **nx_dhcp_create_server_ip_address_list**: *DHCP 클라이언트 인터페이스에 할당할 사용 가능한 IP 주소 풀 만들기*
- **nx_dhcp_clear_client_record**: *서버 데이터베이스에서 클라이언트 레코드 제거*
- **nx_dhcp_server_delete**: *DHCP 서버 인스턴스 삭제*
- **nx_dhcp_server_start**: *DHCP 서버 처리 시작 또는 다시 시작*
- **nx_dhcp_server_stop**: *DHCP 서버 처리 중지*

## <a name="nx_dhcp_server_create"></a>nx_dhcp_server_create

DHCP 서버 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 IP 인스턴스로 DHCP 서버 인스턴스를 만듭니다.

> [!IMPORTANT]
> 애플리케이션은 IP 만들기 서비스에 대해 생성된 패킷 풀에 UDP, IP 및 이더넷 헤더를 포함하지 않고 최소 548바이트 페이로드가 있는지 확인해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr**: DHCP 서버 제어 블록에 대한 포인터  
- **ip_ptr**: DHCP 서버 IP 인스턴스에 대한 포인터
- **stack_ptr**: 포인터 DHCP 서버 스택 위치
- **stack_size**: DHCP 서버 스택 크기
- **input_address_list**: 서버의 IP 주소 목록에 대한 포인터
- **name_ptr**: DHCP 서버 이름에 대한 포인터
- **packet_pool_ptr**: DHCP 서버 패킷 풀에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DHCP 서버를 성공적으로 만들었습니다.
- **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) 패킷 페이로드가 너무 작음 오류
- **NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) 서버 옵션 목록이 비어 있음
- NX_DHCP_PARAMETER_ERROR: (0x92) 잘못된 포인터가 아닌 입력
- NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자
- NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

애플리케이션

### <a name="example"></a>예제

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a>nx_dhcp_create_server_ip_address_list

IP 주소 풀 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a>Description

이 서비스는 할당할 지정된 DHCP 서버에 사용할 수 있는 IP 주소의 네트워크 인터페이스 특정 풀을 만듭니다. 시작 IP 주소와 끝 IP 주소는 지정된 네트워크 인터페이스와 일치해야 합니다. IP 주소 목록의 크기가 충분히 크지 않은 경우(사용자 구성 가능 *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* 매개 변수에 설정됨) 추가된 실제 IP 주소 수가 총 주소 수보다 적을 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 서버 제어 블록에 대한 포인터  
- **iface_index**: 네트워크 인터페이스에 해당하는 인덱스
- **start_ip_address**: 사용 가능한 첫 번째 IP 주소
- **end_ip_address**: 사용 가능한 마지막 IP 주소
- **addresses_added**: 목록에 추가된 IP 주소 수

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DHCP 서버를 성공적으로 만들었습니다.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) 인덱스가 주소와 일치하지 않음
- **NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) 잘못된 주소 입력
- NX_DHCP_INVALID_IP_ADDRESS: (0x9B) 비논리적 시작/종료 주소
- NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

애플리케이션

### <a name="example"></a>예제

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a>nx_dhcp_clear_client_record

서버 데이터베이스에서 클라이언트 레코드 제거

### <a name="prototype"></a>프로토타입

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a>Description

이 서비스는 서버 데이터베이스에서 클라이언트 레코드를 지웁니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr**: DHCP 서버 제어 블록에 대한 포인터  
- **dhcp_client_ptr**: 제거할 DHCP 클라이언트에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DHCP 서버를 성공적으로 만들었습니다.
- NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 스레드가 아닌 서비스의 호출자

### <a name="allowed-from"></a>허용 위치

애플리케이션

### <a name="example"></a>예제

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a>nx_dhcp_set_interface_network_parameters

DHCP 옵션에 대한 네트워크 매개 변수 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a>Description

이 서비스는 지정된 인터페이스의 네트워크 중요 매개 변수에 대한 기본값을 설정합니다. DHCP 서버는 DHCP 클라이언트에 대한 OFFER 및 ACK 회신에 이러한 옵션을 포함합니다. 호스트가 실행 중인 DHCP 서버에 인터페이스 매개 변수를 설정하는 경우 매개 변수는 DHCP 서버 자체에 대한 기본 인터페이스 게이트웨이로 설정된 라우터, DHCP 서버 자체에 대한 DNS 서버 주소 및 DHCP 서버 인터페이스와 동일하게 구성된 서브넷 마스크와 같이 기본값으로 설정됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr**: DHCP 서버 제어 블록에 대한 포인터  
- **iface_index**: 네트워크 인터페이스에 해당하는 인덱스
- **subnet_mask**: 클라이언트 네트워크에 대한 서브넷 마스크
- **default_gateway_address**: 클라이언트의 라우터 IP 주소
- **dns_server_address**: 클라이언트 네트워크에 대한 DNS 서버

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DHCP 서버를 성공적으로 만들었습니다.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) 인덱스가 주소와 일치하지 않음
- **NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) 잘못된 네트워크 매개 변수
- NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

애플리케이션

### <a name="example"></a>예제

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a>nx_dhcp_server_delete

DHCP 서버 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 DHCP 서버 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr**: DHCP 서버 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DHCP 서버를 성공적으로 삭제함
- NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.
- NX_DHCP_PARAMETER_ERROR: (0x92) 잘못된 포인터가 아닌 입력
- NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a>nx_dhcp_server_start

DHCP 서버 처리 시작

### <a name="prototype"></a>프로토타입

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCP 서버 처리를 시작합니다. 여기에는 서버 UDP 소켓을 만들고, DHCP 포트를 바인딩하고 클라이언트 DHCP 요청을 받기 위해 대기하는 작업이 포함됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr**: 이전에 만든 DHCP 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 서버를 성공적으로 시작했습니다.  
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP가 이미 시작됨
- NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자
- NX_DHCP_PARAMETER_ERROR: (0x92) 잘못된 포인터가 아닌 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a>참고 항목

nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert

## <a name="nx_dhcp_server_stop"></a>nx_dhcp_server_stop

DHCP 서버 처리 중지

### <a name="prototype"></a>프로토타입

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCP 클라이언트 요청 수신을 포함하는 DHCP 서버 처리를 중지합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr**: DHCP 서버 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DHCP를 성공적으로 중지함
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP가 이미 시작됨
- NX_PTR_ERROR: (0x16) 포인터 입력이 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 서비스의 잘못된 호출자
- NX_DHCP_PARAMETER_ERROR: (0x92) 잘못된 포인터가 아닌 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
