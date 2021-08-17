---
title: 3장 - Azure RTOS NetX Duo Telnet 서비스 설명
description: 이 장에서는 아래 알파벳 순서로 나열된 모든 Azure RTOS NetX Duo Telnet 서비스에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 70bf4016793572d7327d12be182750316659c3c4260d2f7db8acddbba00c5601
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791995"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a>3장 - Azure RTOS NetX Duo Telnet 서비스 설명

이 장에서는 아래 알파벳 순서로 나열된 모든 Azure RTOS NetX Duo Telnet 서비스에 대해 설명합니다.

다음 API 설명의 “반환 값” 섹션에서 **굵게 표시** 된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않으며, 굵게 표시되지 않은 값은 완전히 사용할 수 없습니다.

- **nx_telnet_client_connect**: IPv4 주소를 사용하여 텔넷 클라이언트 연결
- **nxd_telnet_client_connect**: IPv6 주소를 사용하여 IPv6 텔넷 클라이언트 연결
- **nx_telnet_client_create**: 텔넷 클라이언트 만들기
- **nx_telnet_client_delete**: 텔넷 클라이언트 삭제
- **nx_telnet_client_disconnect**: 텔넷 클라이언트 연결 끊기
- **nx_telnet_client_packet_receive**: 텔넷 클라이언트를 통해 패킷 수신
- **nx_telnet_client_packet_send**: 텔넷 클라이언트를 통해 패킷 전송
- **nx_telnet_server_create**: 텔넷 서버 만들기
- **nx_telnet_server_delete**: 텔넷 서버 삭제
- **nx_telnet_server_disconnect**: 텔넷 클라이언트 연결 끊기
- **nx_telnet_server_get_open_connection_count**: 열린 연결 수 검색
- **nx_telnet_server_packet_send**: 클라이언트 연결을 통해 패킷 전송
- **nx_telnet_server_packet_pool_set**: 패킷 풀을 텔넷 서버 패킷 풀로 설정
- **nx_telnet_server_start**: 텔넷 서버 시작
- **nx_telnet_server_stop**: 텔넷 서버 중지

## <a name="nx_telnet_client_connect"></a>nx_telnet_client_connect

IPv4 주소를 사용하여 텔넷 클라이언트 연결

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 텔넷 서버의 IPv4 주소를 사용하여 이전에 만든 텔넷 클라이언트 인스턴스를 지정된 IP 및 포트의 서버에 연결하려 합니다. 이 서비스는 ULONG 서버 IP 주소를 NXD_ADDRESS 제어 블록에 삽입하고, 아래에 설명된 *nxd_telnet_client_connect* 서비스를 호출하기 전에 IP 버전을 4로 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.
- **server_ip**: 텔넷 서버의 IPv4 주소입니다.
- **server_port**: 서버의 TCP 포트입니다(텔넷 서버: 포트 23).
- **wait_option**: 서비스에서 텔넷 클라이언트 연결을 대기할 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.

    - **시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 클라이언트를 성공적으로 연결했습니다.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) 클라이언트가 이미 연결되어 있습니다.
- NX_PTR_ERROR: (0x07) 클라이언트 포인터가 잘못되었습니다.
- NX_IP_ADDRESS_ERROR: (0x21) IP 주소가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a>nxd_telnet_client_connect

IPv6 또는 IPv4 주소를 사용하여 텔넷 클라이언트 연결

### <a name="prototype"></a>프로토타입

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 텔넷 서버의 IPv6 주소를 사용하여 이전에 만든 텔넷 클라이언트 인스턴스를 지정된 IP 및 포트의 서버에 연결하려 합니다. 이 서비스는 IPv4 또는 IPv6 주소를 사용할 수 있지만 NXD_ADDRESS 변수 *server_ip_address* 에 포함되어야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.
- **server_ip_address**: 서버의 IP 주소입니다.
- **server_port**: 서버의 TCP 포트입니다(텔넷 서버: 포트 23).
- **wait_option**: 서비스에서 텔넷 클라이언트 연결을 대기할 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.

    - **시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 클라이언트를 성공적으로 연결했습니다.
- **NX_TELNET_ERROR**: (0xF0) 클라이언트 연결 오류입니다.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) 클라이언트가 이미 연결되어 있습니다.
- NX_PTR_ERROR: (0x07) 클라이언트 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.
- NX_TELNET_INVALID_PARAMETER: (0xF5) 포인터가 아닌 입력이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a>nx_telnet_client_create

텔넷 클라이언트 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a>Description

이 서비스는 텔넷 클라이언트 인스턴스를 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.
- **client_name**: 클라이언트 인스턴스의 이름입니다.
- **ip_ptr**: IP 인스턴스에 대한 포인터입니다.
- **window_size**: 이 클라이언트의 TCP 수신 창 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 클라이언트를 성공적으로 만들었습니다.
- **NX_TELNET_ERROR**: (0xF0) 소켓 만들기 오류입니다.
- NX_PTR_ERROR: (0x07) 클라이언트 또는 IP 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a>nx_telnet_client_delete

텔넷 클라이언트 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 텔넷 클라이언트 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 클라이언트를 성공적으로 삭제했습니다.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) 클라이언트가 아직 연결되어 있습니다.
- NX_PTR_ERROR: (0x07) 클라이언트 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a>nx_telnet_client_disconnect

텔넷 클라이언트 연결 끊기

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 연결된 텔넷 클라이언트 인스턴스의 연결을 끊습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.
- **wait_option**: 서비스에서 텔넷 클라이언트 연결을 끊을 때까지 대기할 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.

    - **시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 클라이언트 연결을 성공적으로 끊었습니다.
- **NX_TELNET_NOT_CONNECTED**: (0xF3) 클라이언트가 연결되지 않았습니다.
- NX_PTR_ERROR: (0x07) 클라이언트 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.


### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a>nx_telnet_client_packet_receive

텔넷 클라이언트를 통해 패킷 수신

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 연결된 텔넷 클라이언트 인스턴스에서 패킷을 수신합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.
- **packet_ptr**: 수신된 패킷의 대상에 대한 포인터입니다.
- **wait_option**: 서비스에서 텔넷 클라이언트 패킷 수신을 대기할 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 클라이언트 패킷을 성공적으로 수신했습니다.
- NX_PTR_ERROR: (0x07) 포인터 입력이 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a>nx_telnet_client_packet_send

텔넷 클라이언트를 통해 패킷 전송

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 연결된 텔넷 클라이언트 인스턴스를 통해 패킷을 전송합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.
- **packet_ptr**: 전송할 패킷에 대한 포인터입니다.
- **wait_option**: 서비스에서 텔넷 클라이언트 패킷 전송을 대기할 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 클라이언트 패킷을 성공적으로 전송했습니다.
- **NX_TELNET_ERROR**: (0xF0) 패킷 전송 실패 - 호출자가 패킷을 해제해야 합니다.
- NX_PTR_ERROR: (0x07) 포인터 입력이 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a>nx_telnet_server_create

텔넷 서버 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에 텔넷 서버 인스턴스를 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.
- **server_name**: 텔넷 서버 인스턴스의 이름입니다.
- **ip_ptr**: 연결된 IP 인스턴스에 대한 포인터입니다.
- **stack_ptr**: 내부 서버 스레드의 스택에 대한 포인터입니다.
- **sack_size**: 스택의 크기(바이트)입니다.
- **new_connection**: 애플리케이션 콜백 루틴 함수 포인터입니다. 이 루틴은 서버가 새 텔넷 클라이언트 연결 요청을 검색할 때마다 호출됩니다.
- **receive_data**: 애플리케이션 콜백 루틴 함수 포인터입니다. 이 루틴은 연결에 새 텔넷 클라이언트 데이터가 있을 때마다 호출되며 패킷을 해제하는 역할을 담당합니다.
- **end_connection**: 애플리케이션 콜백 루틴 함수 포인터입니다. 클라이언트에서 텔넷 클라이언트 연결을 끊거나 클라이언트 연결 시간이 초과할 때마다 이 루틴을 호출합니다(“작업 시간 초과” 만료). 서버는 아래에 설명된 *nx_telnet_server_disconnect* 서비스를 통해 연결을 끊을 수도 있습니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 서버를 성공적으로 만들었습니다.
- NX_PTR_ERROR: (0x07) 서버, IP, 스택 또는 애플리케이션 콜백 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a>nx_telnet_server_delete

텔넷 서버 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 텔넷 서버 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 서버를 성공적으로 삭제했습니다.
- NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a>nx_telnet_server_disconnect

텔넷 클라이언트 연결 끊기

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a>Description

이 서비스는 해당 텔넷 서버 인스턴스에서 이전에 연결된 클라이언트 연결을 끊습니다. 이 루틴은 일반적으로 수신된 데이터에서 검색된 조건에 응답하여 애플리케이션의 수신 데이터 콜백 함수에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.
- **logical_connection**: 이 서버의 클라이언트 연결에 해당하는 논리적 연결입니다. 유효한 값 범위는 0에서 NX_TELENET_MAX_CLIENTS까지입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 서버 연결을 성공적으로 끊었습니다.
- **NX_TELNET_ERROR**: (0xF0) 서버 연결을 끊지 못했습니다.
- NX_OPTION_ERROR: (0x0A) 논리적 연결이 잘못되었습니다.
- NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a>nx_telnet_server_get_open_connection_count

현재 열린 연결 수를 반환합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a>Description

이 서비스는 현재 연결된 텔넷 클라이언트의 수를 반환합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.
- **Connection_count**: 연결 수를 저장할 메모리에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적으로 완료되었습니다.
- NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a>nx_telnet_server_packet_send

클라이언트 연결을 통해 패킷 전송

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 해당 텔넷 서버 인스턴스의 클라이언트 연결에 패킷을 전송합니다. 이 루틴은 일반적으로 수신된 데이터에서 검색된 조건에 응답하여 애플리케이션의 수신 데이터 콜백 함수에서 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.
- **logical_connection**: 이 서버의 클라이언트 연결에 해당하는 논리적 연결입니다. 유효한 값 범위는 0에서 NX_TELENET_MAX_CLIENTS까지입니다.
- **packet_ptr**: 수신된 패킷에 대한 포인터입니다.
- **wait_option**: 서비스에서 텔넷 서버 패킷 전송을 대기할 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다. 

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 패킷을 성공적으로 전송했습니다.
- **NX_TELNET_FAILED**: (0xF2) TCP 소켓을 전송하지 못했습니다.
- NX_OPTION_ERROR: (0x0A) 논리적 연결이 잘못되었습니다.
- NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a>nx_telnet_server_packet_pool_set

이전에 만든 패킷 풀을 텔넷 서버 풀로 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a>Description

NX_TELNET_SERVER_USER_CREATE_PACKET_POOL이 정의된 경우 이 서비스는 이전에 만든 패킷 풀을 텔넷 서버 패킷 풀로 설정합니다. 또한 텔넷 서버가 텔넷 옵션을 텔넷 클라이언트로 전송하는 데 패킷 풀이 필요하도록 NX_TELNET_SERVER_OPTION_DISABLE을 정의하지 않아야 합니다.

이렇게 하면 애플리케이션은 텔넷 서버 스택과 다른 메모리(예: 캐시가 없는 메모리)에 패킷 풀을 만들 수 있습니다. 이 함수는 텔넷 서버 패킷 풀이 이미 설정되어 있는지 확인하지 않습니다. null이 아닌 텔넷 서버 패킷 풀 포인터에서 호출되는 경우 이를 덮어쓰고 기존 패킷 풀을 입력 포인터가 가리키는 패킷 풀로 바꿉니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.
- **packet_pool_ptr**: 이전에 만든 패킷 풀에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 풀을 성공적으로 설정했습니다.
- NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a>nx_telnet_server_start

텔넷 서버 시작

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a>Description

이 서비스는 이전에 만든 텔넷 서버 인스턴스를 시작합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적으로 시작했습니다.
- **NX_TELNET_NO_PACKET_POOL**: (0xF6) 패킷 풀이 설정되지 않았습니다.
- NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a>nx_telnet_server_stop

텔넷 서버 중지

### <a name="prototype"></a>프로토타입

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만들어 시작한 텔넷 서버 인스턴스를 중지합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적으로 중지되었습니다.
- NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```