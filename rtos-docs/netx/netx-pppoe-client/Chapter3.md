---
title: 3장 - Azure RTOS NetX PPPoE 클라이언트 서비스 설명
description: 이 장에서는 아래에 나열된 모든 Azure RTOS NetX PPPoE 클라이언트 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8310006b7c188fa63402c931459ffd84ebb776c207dc520959208449862fe27f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790210"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a>3장 - Azure RTOS NetX PPPoE 클라이언트 서비스 설명

이 장에서는 아래에 나열된 모든 Azure RTOS NetX PPPoE 클라이언트 서비스에 대해 알파벳 순서로 설명하고 있습니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- **nx_pppoe_client_create** *PPPoE 클라이언트 인스턴스 만들기*
- **nx_pppoe_client_delete** *PPPoE 클라이언트 인스턴스 삭제*
- **nx_pppoe_client_host_uniq_set** *PPPoE 클라이언트에 대한 고유한 호스트 설정*
- **nx_pppoe_client_host_uniq_set_extended** *PPPoE 클라이언트에 대한 고유한 호스트 설정*
- **nx_pppoe_client_service_name_set** *PPPoE 클라이언트에 대한 서비스 이름 설정*
- **nx_pppoe_client_service_name_set_extended** *PPPoE 클라이언트에 대한 서비스 이름 설정*
- **nx_pppoe_client_session_connect** *PPPoE 서버에 PPPoE 클라이언트 세션 연결*
- **nx_pppoe_client_session_packet_send** *PPPoE 세션 패킷 전송*
- **nx_pppoe_client_session_terminate** *PPPoE 세션 종료*
- **nx_pppoe_client_session_get** *지정된 PPPoE 세션 inf 가져오기*

## <a name="nx_pppoe_client_create"></a>nx_pppoe_client_create

PPPoE 클라이언트 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a>Description

이 서비스는 지정된 NetX IP 인스턴스의 사용자 제공 링크 드라이버를 사용하여 PPPoE 클라이언트 인스턴스를 만듭니다. 링크 드라이버가 초기화되지 않고 사용하도록 설정된 경우 PPPoE 클라이언트 소프트웨어는 링크 드라이버를 초기화합니다.

또한 애플리케이션은 내부 패킷 할당에 사용할 PPPoE 클라이언트 인스턴스에 대해 이전에 만든 패킷 풀을 제공해야 합니다.

> [!NOTE]
> 일반적으로는 PPPoE 클라이언트 스레드 우선 순위보다 우선 순위가 높은 NetX IP 스레드를 만드는 것이 좋습니다. IP 스레드 우선 순위를 지정하는 방법에 대한 자세한 내용은 *nx_ip_create* 서비스를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

 - **pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.
 - **name** 이 PPPoE 클라이언트 인스턴스의 이름입니다.
 - **ip_ptr** IP 인스턴스의 제어 블록에 대한 포인터입니다.
 - **interface_index** 인터페이스 인덱스입니다.
 - **pool_ptr** 패킷 풀에 대한 포인터입니다.
 - **stack_ptr** PPPoE 클라이언트 스레드의 스택 영역 시작에 대한 포인터입니다.
 - **stack_size** 스레드의 스택에 있는 크기(바이트)입니다.
 - **priority** 내부 PPPoE 클라이언트 스레드의 우선 순위(1-31)입니다.
 - **pppoe_link_driver** 사용자가 제공한 링크 드라이버입니다.
 - **pppoe_packet_receive** 사용자가 제공한 패킷 수신 함수입니다.

### <a name="return-values"></a>반환 값

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 만들기입니다.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) 잘못된 PPPoE 클라이언트, IP, 패킷 풀 또는 스택 포인터입니다.
 - NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) 인터페이스가 유효하지 않습니다.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) 패킷 풀의 페이로드 크기가 유효하지 않습니다.
 - NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) 메모리 크기가 유효하지 않습니다.
 - NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) PPPoE 클라이언트 스레드의 우선 순위가 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a>nx_pppoe_client_delete

PPPoE 클라이언트 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 PPPoE 클라이언트 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 삭제입니다.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a>nx_pppoe_client_host_uniq_set

PPPoE 클라이언트 호스트 고유 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a>Description

이 서비스는 고유한 PPPoE 클라이언트 호스트를 설정합니다. Host-Uniq는 호스트에서 액세스 집중 장치를 특정 호스트 요청에 고유하게 연결하는 데 사용됩니다.
호스트에서 선택하는 값과 길이의 이진 데이터일 수 있습니다.

> [!NOTE]
> 고유한 호스트는 Null로 끝나는 문자열이어야 합니다.

> [!NOTE]
> 이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_pppoe_client_host_uniq_set_extended()* 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.
 - **host_uniq** 고유한 호스트에 대한 포인터입니다. 고유한 호스트는 Null로 끝나는 문자열이어야 합니다.

### <a name="return-values"></a>반환 값

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 호스트 고유 집합입니다.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a>nx_pppoe_client_host_uniq_set_extended

PPPoE 클라이언트 호스트 고유 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a>Description

이 서비스는 고유한 PPPoE 클라이언트 호스트를 설정합니다. Host-Uniq는 호스트에서 액세스 집중 장치를 특정 호스트 요청에 고유하게 연결하는 데 사용됩니다.
호스트에서 선택하는 값과 길이의 이진 데이터일 수 있습니다.

> [!NOTE]
> 고유한 호스트는 Null로 끝나는 문자열이어야 합니다.

> [!NOTE]
> 이 서비스는 *nx_pppoe_client_host_uniq_set()* 를 대체합니다. 이 버전은 추가 길이 정보를 서비스에 제공합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.
 - **host_uniq** 고유한 호스트에 대한 포인터입니다. 고유한 호스트는 Null로 끝나는 문자열이어야 합니다.
 - **host_uniq_length** host_uniq의 길이

### <a name="return-values"></a>반환 값

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 호스트 고유 집합입니다.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.
 - **NX_SIZE_ERROR** (0x09) host_uniq_length 실패 확인

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a>nx_pppoe_client_service_name_set

PPPoE 클라이언트 서비스 이름 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a>Description

이 서비스는 PPPoE 클라이언트 서비스 이름을 설정합니다. 호스트에서 요청하는 서비스를 나타내는 Service-Name입니다. Service-Name이 설정되지 않은 경우 호스트가 원하는 수의 서비스를 허용함을 나타냅니다.

> [!NOTE]
> 서비스 이름은 Null로 끝나는 문자열이어야 합니다.

> [!NOTE]
> 이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_pppoe_client_service_name_set_extended()* 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.
 - **service_name** 서비스 이름에 대한 포인터입니다. 서비스 이름은 Null로 끝나는 문자열이어야 합니다.

### <a name="return-values"></a>반환 값

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 서비스 이름 집합입니다.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a>nx_pppoe_client_service_name_set_extended

PPPoE 클라이언트 서비스 이름 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a>Description

이 서비스는 PPPoE 클라이언트 서비스 이름을 설정합니다. 호스트에서 요청하는 서비스를 나타내는 Service-Name입니다. Service-Name이 설정되지 않은 경우 호스트가 원하는 수의 서비스를 허용함을 나타냅니다.

> [!NOTE]
> 서비스 이름은 Null로 끝나는 문자열이어야 합니다.

> [!NOTE]
> 이 서비스는 *nx_pppoe_client_service_name_set()* 를 대체합니다. 이 버전은 추가 서비스 이름 길이 정보를 함수에 제공합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.
 - **service_name** 서비스 이름에 대한 포인터입니다. 서비스 이름은 Null로 끝나는 문자열이어야 합니다.
 - **service_name_length** service_name의 길이

### <a name="return-values"></a>반환 값

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 서비스 이름 집합입니다.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.
 - **NX_SIZE_ERROR** (0x09) service_name_length 실패 확인

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a>nx_pppoe_client_session_connect

PPPoE 클라이언트 세션 연결

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 PPPoE 클라이언트를 사용하여 지정된 PPPoE 서버에 PPPoE 세션 연결을 만듭니다.

> [!NOTE]
> 이 함수는 *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* 및 *nx_pppoe_client_service_name_set* 후에 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.
 - **wait_option** 연결이 설정되는 동안 대기 옵션입니다.

### <a name="return-values"></a>반환 값

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 세션 연결입니다.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a>nx_pppoe_client_session_packet_send

지정된 세션에 PPPoE 클라이언트 패킷 보내기

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 세션 ID를 사용하여 PPPoE 패킷을 보냅니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.
 - **packet_ptr** PPPoE 패킷에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 패킷 전송입니다.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) PPPoE 클라이언트 패킷이 유효하지 않습니다.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE 세션이 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a>nx_pppoe_client_session_terminate

PPPoE 클라이언트 세션 종료

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 PPPoE 세션을 종료합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **pppoe_client_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 세션 종료입니다.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a>nx_pppoe_client_session_get

지정된 PPPoE 세션 정보 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Description

이 서비스는 지정된 PPPoE 세션 정보, 서버 실제 주소 및 세션 ID를 가져옵니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **pppoe_server_ptr** PPPoE 클라이언트 제어 블록에 대한 포인터입니다.
 - **server_mac_msw** 서버 실제 주소 MSW 포인터입니다.
 - **server_mac_msw** 서버 실제 주소 MSW 포인터입니다.
 - **session_id** Session ID 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) 성공한 PPPoE 클라이언트 세션 가져오기입니다.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) PPPoE 클라이언트 포인터가 유효하지 않습니다.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE 세션이 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
