---
title: 3장 - Azure RTOS NetX PPPoE 서버 서비스 설명
description: 이 장에서는 아래에 나열된 모든 Azure RTOS NetX PPPoE 서버 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811418"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a>3장 - Azure RTOS NetX PPPoE 서버 서비스 설명

이 장에서는 아래에 나열된 모든 Azure RTOS NetX PPPoE 서버 서비스에 대해 알파벳 순서로 설명하고 있습니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- **nx_pppoe_server_create**: *PPPoE 서버 인스턴스 만들기*

- **nx_pppoe_server_ac_name_set**: *액세스 집중 장치 이름 설정*

- **nx_pppoe_server_delete**: *PPPoE 서버 인스턴스 삭제*

- **nx_pppoe_server_enable**: *PPPoE 서버 서비스를 사용하도록 설정*

- **nx_pppoe_server_disable**: *PPPoE 서버 서비스를 사용하지 않도록 설정*

- **nx_pppoe_server_callback_notify_set**: *PPPoE 서버 콜백 알림 함수 설정*

- **nx_pppoe_server_service_name_set**: *PPPoE 서버 서비스 이름 설정*

- **nx_pppoe_server_session_send**: *지정 된 세션에 PPPoE 서버 데이터 보내기*

- **nx_pppoe_server_session_packet_send**: *지정된 세션에 PPPoE 서버 패킷 보내기*

- **nx_pppoe_server_session_terminate**: *지정된 PPPoE 세션 종료*

- **nx_pppoe_server_session_get**: *지정된 세션 정보 가져오기*

## <a name="nx_pppoe_server_create"></a>nx_pppoe_server_create

PPPoE 서버 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a>Description

이 서비스는 지정된 NetX IP 인스턴스에 대한 사용자 입력 링크 드라이버를 통해 PPPoE 서버 인스턴스를 만듭니다. 링크 드라이버가 초기화되지 않고 사용하도록 설정된 경우 PPPoE 서버 소프트웨어는 링크 드라이버를 초기화합니다.

또한 애플리케이션은 내부 패킷 할당에 사용할 PPPoE 서버 인스턴스에 대해 이전에 만든 패킷 풀을 제공해야 합니다.

일반적으로는 PPPoE 서버 스레드 우선 순위보다 우선 순위가 높은 NetX IP 스레드를 만드는 것이 좋습니다. IP 스레드 우선 순위를 지정하는 방법에 대한 자세한 내용은 *nx_ip_create* 서비스를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터
- **name**: 이 PPPoE 서버 인스턴스의 이름
- **ip_ptr**: IP 인스턴스용 제어 블록에 대한 포인터
- **interface_index**: 인터페이스 인덱스
- **pppoe_link_driver** 사용자가 제공한 링크 드라이버
- **pool_ptr**: 패킷 풀에 대한 포인터
- **stack_ptr**: PPPoE 서버 스레드의 스택 영역 시작 부분에 대한 포인터
- **stack_size**: 스레드 스택의 크기(바이트)
- **priority**: 내부 PPPoE 서버 인스턴스의 우선 순위(1-31)

### <a name="return-values"></a>반환 값

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 만들기 성공
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버, IP, 패킷 풀 또는 스택 포인터
- NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) 잘못된 인터페이스
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) 잘못된 패킷 풀 페이로드 크기
- NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) 잘못된 메모리 크기
- NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) 잘못된 PPPoE 서버 스레드 우선 순위

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a>nx_pppoe_server_delete

PPPoE 서버 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 PPPoE 서버 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a>nx_pppoe_server_enable

PPPoE 서버 서비스 사용

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 PPPoE 서버 서비스를 사용하도록 설정합니다.

> [!NOTE]
> 이 함수는 *nx_pppoe_server_create* 및 *nx_pppoe_server_callback_notify_set* 다음에 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a>nx_pppoe_server_disable

PPPoE 서버 서비스 사용 안 함

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 PPPoE 서버 서비스를 사용하지 않도록 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a>nx_pppoe_server_callback_notify_set

PPPoE 서버 콜백 알림 함수 설정 

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a>Description

이 서비스는 PPPoE 서버 콜백 알림 함수를 설정합니다.

> [!NOTE]
> 이 함수는 *nx_pppoe_server_enabl 및* pppoe_data_receive_notify 함수 포인터가 설정되기 전에 호출해야 하며, 그렇지 않으면 *nx_pppoe_server_enable* 이 실패합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터
- **pppoe_discover_initiation_notify**: PPPoE 검색 시작 메시지를 받을 때마다 호출되는 애플리케이션 함수입니다. 이 값이 NULL 인 경우 검색 시작 콜백 함수를 사용하지 않습니다.
- **pppoe_discover_request_notify**: PPPoE 검색 요청 메시지를 받을 때마다 호출되는 애플리케이션 함수입니다. 이 값이 NULL인 경우 검색 요청 콜백 함수를 사용하지 않습니다.
- **pppoe_discover_terminate_notify**: PPPoE 검색 종료 메시지를 받을 때마다 호출되는 애플리케이션 함수입니다. 이 값이 NULL인 경우 검색 종료 콜백 함수를 사용하지 않습니다.
- **pppoe_discover_terminate_confirm**: PPPoE 검색 종료 메시지를 보낼 때마다 호출되는 애플리케이션 함수입니다. 이 값이 NULL인 경우 검색 종료 콜백 함수를 사용하지 않습니다.
- **pppoe_data_receive_notify**: PPPoE 데이터 메시지를 받을 때마다 호출되는 애플리케이션 함수입니다. 이 값은 0이 될 수 없습니다.
- **pppoe_data_send_notify**: PPPoE 데이터 메시지를 보낼 때마다 호출되는 애플리케이션 함수입니다. 이 값이 NULL 이면 데이터 보내기 콜백 함수를 사용하지 않습니다.

### <a name="return-values"></a>반환 값

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터 또는 함수 포인터

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a>nx_pppoe_server_ac_name_set

액세스 집중 장치 이름 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a>Description

이 함수는 액세스 집중 장치 이름 함수 호출을 설정합니다.

> [!NOTE]
> ac_name 문자열은 NULL로 종결되고 ac_name 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터
- **ac_name**: 액세스 집중 장치 이름
- **ac_name_length**: ac_ame의 길이

### <a name="return-values"></a>반환 값

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 설정 성공
- **NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) 잘못된 PPPoE 서버, IP, 패킷 풀 또는 스택 포인터
- **NX_SIZE_ERROR**: (0x09) name_length 확인 실패

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a>nx_pppoe_server_service_name_set

PPPoE 서버 서비스 이름 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a>Description

이 서비스는 PPPoE 서버 서비스 이름을 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a>nx_pppoe_server_session_send

PPPoE 서버 데이터를 지정된 세션에 보내기

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a>Description

이 서비스는 지정된 세션 ID를 사용하여 PPPoE 프레임을 보냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터
- **session_index**: 세션의 인덱스
- **data_ptr**: PPPoE 서버 데이터 프레임의 시작에 대한 포인터입니다.
- **data_length**: PPPoE 서버 데이터 프레임의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE 서버 서비스를 사용하도록 설정되지 않았습니다.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) 잘못된 PPPoE 세션 인덱스
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE 세션이 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a>nx_pppoe_server_session_packet_send

지정된 세션에 PPPoE 서버 패킷 보내기

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 세션 ID를 사용하여 PPPoE 패킷을 보냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터
- **session_index**: 세션의 인덱스
- **packet_ptr**: PPPoE 패킷에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) 잘못된 PPPoE 서버 패킷
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE 서버 서비스를 사용하도록 설정되지 않았습니다.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) 잘못된 PPPoE 세션 인덱스
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE 세션이 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a>nx_pppoe_server_session_terminate

지정된 PPPoE 세션 종료

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a>Description

이 서비스는 지정된 PPPoE 세션을 종료합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터
- **session_index**: 세션의 인덱스

### <a name="return-values"></a>반환 값

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE 서버 서비스를 사용하도록 설정되지 않았습니다.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) 잘못된 PPPoE 세션 인덱스
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE 세션이 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a>nx_pppoe_server_session_get

지정된 PPPoE 세션 정보 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Description

이 서비스는 지정된 PPPoE 세션 정보, 클라이언트 실제 주소, 세션 ID를 가져옵니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pppoe_server_ptr**: PPPoE 서버 제어 블록에 대한 포인터
- **session_index**: 세션의 인덱스
- **client_mac_msw**: 클라이언트 실제 주소 MSW 포인터
- **client_mac_lsw**: 클라이언트 실제 주소 MSW 포인터
- **session_id**: 세션 ID 포인터

### <a name="return-values"></a>반환 값

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) PPPoE 서버 삭제 성공
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) 잘못된 PPPoE 서버 포인터
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) 잘못된 PPPoE 세션 인덱스
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE 세션이 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a>PppInitInd

기본 서비스 이름 구성

### <a name="prototype"></a>프로토타입

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a>Description

PPPoE 소프트웨어는 TTP의 소프트웨어가, PPPoE가 들어오는 PADI 요청을 필터링하는 데 사용할 ‘기본 서비스 이름’을 구성할 수 있게 이 함수를 노출합니다. PPPoE 소프트웨어는 이 정보를 기억했다가 일치하는 서비스 이름이 포함된 PADI 패킷을 수신했을 때 PppDiscoverReq를 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **length**: 기본 서비스 이름의 길이
- **aData**: 기본 서비스 이름

### <a name="return-values"></a>반환 값

**없음**

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a>PppDiscoverCnf

PADO 패킷의 서비스 이름 필드 정의

### <a name="prototype"></a>프로토타입

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a>Description

PPPoE 소프트웨어는 TTP의 소프트웨어가 PADO 패킷의 서비스 이름 필드를 정의할 수 있도록 이 함수를 노출합니다. PPPoE 소프트웨어는 PppDiscoverCnf가 호출될 때까지 PADO를 보내지 않아야 합니다.

PADO 패킷에는 PPPoE 소프트웨어 초기화에서 정의한 대로 액세스 집중 장치 이름(RFC2516에서 정의한 대로 태그 ID 0x0102 사용)이 있어야 합니다.

aData에서 여러 서비스 이름을 전달할 수 있으며 각 이름은 null로 종료됩니다.

다른 명령을 서비스 이름의 일부로 전달해야 할 경우 Null 문자를 구분 기호로 사용하여 유연성을 극대화할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **length**: 기본 서비스 이름의 길이
- **aData**: 기본 서비스 이름
- **interfaceHandle**: 인터페이스 핸들

### <a name="return-values"></a>반환 값

**없음**

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a>PppOpenCnf

PPPoE 세션 수락 또는 거절

### <a name="prototype"></a>프로토타입

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a>Description

PPPoE 소프트웨어는 TTP의 소프트웨어가 PPPoE 세션을 수락 또는 거절할 수 있게 이 함수를 노출합니다.  이에 대한 응답으로 PPPoE 스택은 연결을 수락하고 interfaceHandle과 연결된 고유한 PPPoE Session_ID 번호를 할당해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **accept**: NX_TRUE이면 연결을 수락합니다.
- **interfaceHandle**: 인터페이스 핸들

### <a name="return-values"></a>반환 값

**없음**

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a>PppCloseInd

PPPoE 세션 종료

### <a name="prototype"></a>프로토타입

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a>Description

PPPoE 소프트웨어는 TTP의 소프트웨어가 PPPoE 세션을 닫을 수 있게 이 함수를 노출합니다.

PPPoE 소프트웨어는 PADT 메시지에서 Generic-Error 태그(0x0203)의 원인 코드 문자열을 표시합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **interfaceHandle**: 인터페이스 핸들
- **causeCode**: PPPoE 서버로부터 연결 종료 사유에 대한 정보를 보내기 위한 Null 종료 문자열

### <a name="return-values"></a>반환 값

**없음**

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a>PppCloseCnf

핸들이 해제되었음을 확인

### <a name="prototype"></a>프로토타입

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a>Description

PPPoE 소프트웨어는 TTP의 소프트웨어가 핸들이 해제되었음을 확인할 수 있게 이 함수를 노출합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **interfaceHandle**: 인터페이스 핸들

### <a name="return-values"></a>반환 값

**없음**

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a>PppTransmitDataCnf

앞의 PPP 데이터를 승인할 수 있게 허용

### <a name="prototype"></a>프로토타입

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a>Description

PPPoE 소프트웨어는 이전 PppTransmitDataReq를 승인할 수 있도록 이 함수를 노출합니다.  TTP의 소프트웨어가 PPPoE의 새 PPP 프레임을 사용할 준비가 되었음을 의미합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **interfaceHandle**: 인터페이스 핸들
- **aData**: 수락된 PPP 데이터 버퍼에 대한 포인터
- **Packet_id**: 패킷 식별자

### <a name="return-values"></a>반환 값

**없음**

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a>PppReceiveDataInd

이더넷을 통한 전송에서 데이터 수신

### <a name="prototype"></a>프로토타입

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a>Description

PPPoE 소프트웨어는 이더넷을 통한 송신용 데이터를 수신하기 위해 이 함수를 노출합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **interfaceHandle**: 인터페이스 핸들
- **length**: aData의 바이트 수
- **aData**: PPP 데이터의 프레임을 포함하는 데이터 버퍼

### <a name="return-values"></a>반환 값

**없음**

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```