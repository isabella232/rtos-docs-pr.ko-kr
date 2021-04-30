---
title: 챕터 3 - Azure RTOS NetX Duo MQTT 클라이언트 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 NetX Duo MQTT 클라이언트 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810711"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a>챕터 3 - Azure RTOS NetX Duo MQTT 클라이언트 서비스 설명

이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX Duo MQTT 클라이언트 서비스를 알파벳 순서로 설명합니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- **nxd_mqtt_client_create** *Create MQTT 클라이언트 인스턴스 만들기*
- **nxd_mqtt_client_will_message_set** *will 메시지 설정*
- **nxd_mqtt_client_client_login_set** *MQTT 클라이언트 사용자 이름 및 암호 설정*
- **nxd_mqtt_client_connect** *MQTT 클라이언트를 broker에 연결*
- **nxd_mqtt_client_secure_connect** *TLS 보안을 사용하여 MQTT 클라이언트를 broker에 연결*
- **nxd_mqtt_client_publish** *broker를 통해 메시지 게시*
- **nxd_mqtt_client_subscribe** *토픽 구독*
- **nxd_mqtt_client_unsubscribe** *토픽 구독 취소*
- **nxd_mqtt_client_receive_notify_set** *MQTT 메시지 수신 알림 콜백 함수 설정*
- **nxd_mqtt_client_message_get** *broker에서 메시지 검색*
- **nxd_mqtt_client_disconnect_notify_set** *MQTT 메시지 연결 해제 알림 콜백 함수 설정*
- **nxd_mqtt_client_disconnect** *broker에서 MQTT 클라이언트 연결 해제*
- **nxd_mqtt_client_delete** *MQTT 클라이언트 인스턴스 삭제*

## <a name="nxd_mqtt_client_create"></a>nxd_mqtt_client_create

MQTT 클라이언트 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a>설명

이 서비스는 지정된 IP 인스턴스에 MQTT 클라이언트 인스턴스를 만듭니다. *client_id* 문자열은 MQTT 연결 단계 중에 *클라이언트 식별자(ClientId)* 로 서버에 전달됩니다. 또한 필요한 ThreadX 리소스(MQTT 클라이언트 작업 스레드, 뮤텍스, 이벤트 플래그 그룹 및 TCP 소켓)를 생성합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.
- **client_name** 클라이언트 이름 문자열입니다.
- **client_id** 연결 단계 중에 사용되는 클라이언트 ID 문자열입니다. MQTT broker는 이 client_id를 사용하여 클라이언트를 고유하게 식별합니다.
- **client_id_length** 클라이언트 ID 문자열의 길이(바이트)입니다.
- **ip_ptr** IP 인스턴스에 대한 포인터입니다.
- **pool_ptr** MQTT 클라이언트가 작업에 사용하는 패킷 풀에 대한 포인터입니다.
- **stack_ptr** MQTT 클라이언트 스레드의 스택 영역입니다.
- **stack_size** 스택 영역의 크기(바이트)입니다.
- **mqtt_thread_priority** MQTT 스레드의 우선 순위입니다.
- **memory_ptr** 사용되지 않습니다. 더 이상 사용 되지 않습니다.
- **memory_size** 사용되지 않습니다. 더 이상 사용 되지 않습니다.

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) MQTT 클라이언트를 성공적으로 만들었습니다.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류
- NX_PTR_ERROR (0x07) 잘못된 MQTT 컨트롤 블록, ip_ptr 또는 패킷 풀 포인터입니다.
- NXD_MQTT_INVALID_PARAMETER (0x10009) 잘못된 will 토픽 문자열, will_retrain_flag 또는 will_QoS 값입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a>nxd_mqtt_client_will_message_set

Will 메시지를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a>설명

이 서비스는 클라이언트가 서버에 연결하기 전에 선택적인 will 토픽과 will 메시지를 설정합니다. will 토픽은 UTF-8 인코딩 문자열이어야 합니다.

설정된 경우, will 메시지는 CONNECT 메시지의 일부로 broker에게 전송됩니다. 따라서 will 메시지를 사용하려는 애플리케이션은 MQTT 연결을 설정하기 전에 이 서비스를 사용해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.
- **will_topic** UTF-8로 인코딩된 will 토픽 문자열입니다. will 토픽이 있어야 합니다. 호출자는 *nx_mqtt_client_connect* 를 호출할 때까지 will_topic 문자열을 유효하게 유지해야 합니다.
- **will_topic_length** will 토픽 문자열의 바이트 수
- **will_message** 애플리케이션이 will 메시지를 정의합니다. will 메시지가 필요하지 않을 경우 애플리케이션은 이 필드를 *NX_NULL* 로 설정할 수 있습니다.
- **will_message_length** will 메시지 문자열의 바이트 수입니다. will_message가 NULL로 설정된 경우 will_message_length를 0으로 설정해야 합니다.
- **will_retain_flag** 서버가 will 메시지를 보존 메시지로 게시할지 여부를 지정합니다. 유효한 값은 *NX_TRUE* 또는 *NX_FALSE* 입니다.
- **will_QoS** will 메시지를 보낼 때 서버에서 사용하는 QoS 값입니다. 유효한 값은 0 또는 1입니다.  

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) will 메시지가 성공적으로 설정되었습니다.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS 수준 2 메시지는 지원되지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록입니다.
- NXD_MQTT_INVALID_PARAMETER (0x10009) 잘못된 will 토픽 문자열, will_retrain_flag 또는 will_QoS 값입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a>nxd_mqtt_client_login_set

MQTT 클라이언트 로그인 사용자 이름 및 암호를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a>설명

이 서비스는 로그인 인증 목적으로 MQTT 연결 단계에서 사용되는 사용자 이름과 암호를 설정합니다.

사용자 이름 및 암호를 사용하는 MQTT 클라이언트 로그인은 선택 사항입니다. 서버에 사용자 이름과 암호가 필요한 상황에서는 연결을 설정하기 전에 사용자 이름과 암호를 설정해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.
- **username** UTF-8로 인코딩된 사용자 이름 문자열입니다. 호출자는 *nx_mqtt_client_connect* 를 호출할 때까지 사용자 이름 문자열을 유효하게 유지해야 합니다.
- **username_length** 사용자 이름 문자열의 바이트 수
- **password** 암호 문자열입니다. 암호가 필요하지 않은 경우에는 이 필드를 NX_NULL로 설정할 수 있습니다.

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) will 메시지가 성공적으로 설정되었습니다.
- NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록입니다.
- NXD_MQTT_INVALID_PARAMETER (0x10009) 잘못된 사용자 이름 문자열 또는 암호 문자열입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a>nxd_mqtt_client_connect

MQTT 클라이언트를 broker에 연결

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>설명

이 서비스는 broker에 대한 연결을 시작합니다. 먼저 TCP 소켓을 바인딩한 다음, TCP 연결을 설정합니다. 이 작업이 성공했다고 가정하면 MQTT 연결 유지 기능이 활성화된 경우 타이머가 생성됩니다. 그런 다음, MQTT 서버(broker)와 연결합니다.

이 서비스는 TLS 보호 없이 MQTT 연결을 생성합니다. 보안 MQTT 연결을 생성하기 위해 애플리케이션은 ***nxd_mqtt_client_secure_connect()*** 서비스를 사용해야 합니다.

연결 시 클라이언트가 *clean_session* 을 NX_FALSE로 설정하면 클라이언트는 아직 승인되지 않은 저장된 모든 메시지를 재전송합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.
- **server_ip** broker IP 주소입니다.
- **server_port** broker 포트 번호입니다. MQTT의 기본 포트는 **_NXD_MQTT_PORT_**(1883)으로 정의됩니다.
- **keep_alive** 세션 중에 사용할 연결 유지 값(초)입니다. 이 값은 broker가 이 클라이언트의 시간을 초과하기 전에 broker로 전송되는 두 MQTT 제어 메시지 사이의 최대 시간을 나타냅니다. 값 0은 연결 유지 기능을 해제합니다.
- **clean_session** 서버가 이 세션을 새로 시작할지 여부를 지정합니다. 유효한 옵션은 **_NX_TRUE_ *_ 또는 _* _NX_FALSE_** 입니다.
- **wait_option** 연결 대기 시간입니다.

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) 성공한 MQTT 연결
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) 클라이언트가 broker에 이미 연결되어 있습니다.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT 뮤텍스를 가져오지 못함 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류
- **NXD_MQTT_CONNECT_FAILURE** (0x10005) broker에 연결하지 못했습니다.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) broker로 메시지를 보낼 수 없습니다.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) 서버가 오류로 응답
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) 서버 응답 코드
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) 서버 응답 코드
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) 서버 응답 코드
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) 서버 응답 코드
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) 서버 응답 코드
- NX_PTR_ERROR (0x07) 잘못된 MQTT 컨트롤 블록, ip_ptr 또는 패킷 풀 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a>nxd_mqtt_client_secure_connect

TLS 보안을 사용하여 MQTT 클라이언트를 broker에 연결

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>설명

이 서비스는 연결이 TCP 대신 TLS 계층을 통과한다는 점을 제외하면 ***nxd_mqtt_client_connect*** 와 동일합니다. 따라서 클라이언트와 broker 간의 통신은 보안이 유지됩니다.

사용자 정의된 *tls_setup* 은 MQTT 클라이언트 연결을 설정하기 전에 MQTT 클라이언트가 사용하는 콜백 함수입니다. 애플리케이션은 NetX Secure TLS를 초기화하고, 보안 매개 변수를 구성하고, TLS 핸드셰이크 중에 사용할 관련 인증서를 로드해야 합니다. 실제 TLS 핸드셰이크는 브로커의 MQTT TLS 포트(기본 TCP 포트 8883)에서 TCP 연결이 설정된 후에 발생합니다. TLS 핸드셰이크가 성공하면 MQTT CONNECT 제어 패킷이 TLS를 통해 전송됩니다.

보안 연결을 설정하려면 NetX Secure TLS 라이브러리를 사용할 수 있어야 하며, NetX Duo MQTT 클라이언트는 ***NX_SECURE_ENABLE*** 이 정의된 상태로 빌드해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.
- **server_ip** broker IP 주소입니다.
- **server_port** broker 포트 번호입니다. MQTT의 기본 포트는 **_NXD_MQTT_TLS_PORT_**(8883)으로 정의됩니다.
- **tls_setup** 사용자가 제공한 TLS 설정 콜백 함수입니다. 이 콜백 함수는 TLS 클라이언트 연결 매개 변수를 설정하기 위해 호출됩니다.
- **keep_alive** 세션 중에 사용할 연결 유지 값입니다. 값 0은 연결 유지 기능을 해제합니다.
- **clean_session** 서버가 이 세션을 새로 시작할지 여부를 지정합니다. 유효한 옵션은 **_NX_TRUE_ *_ 또는 _* _NX_FALSE_** 입니다.
- **wait_option** 연결 대기 시간입니다.

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) TLS를 통해 MQTT 클라이언트 연결이 성공적으로 설정되었습니다.
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) 클라이언트가 broker에 이미 연결되어 있습니다.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT 뮤텍스를 가져오지 못함 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류
- **NXD_MQTT_CONNECT_FAILURE** (0x10005) broker에 연결하지 못했습니다.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) broker로 메시지를 보낼 수 없습니다.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) 서버가 오류 메시지로 응답했습니다.
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) 서버 응답 코드
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) 서버 응답 코드
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) 서버 응답 코드
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) 서버 응답 코드
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) 서버 응답 코드
- NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록 또는 서버 주소 구조입니다.
- NX_INVALID_PORT (0x46) 서버 포트는 0일 수 없습니다.
- NXD_MQTT_INVALID_PARAMETER (0x10009) 입력 매개 변수 오류
- NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT 스레드가 아직 실행되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a>nxd_mqtt_client_publish

broker를 통해 메시지 게시

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a>설명

이 서비스는 broker를 통해 메시지를 게시합니다. QoS 수준 2 메시지 게시는 아직 지원되지 않습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.
- **topic_name** 게시할 토픽입니다.
- **topic_name_length** 토픽의 길이(바이트)입니다.
- **message** 메시지 버퍼에 대한 포인터입니다.
- **message_length** 메시지의 크기(바이트)입니다.
- **retain** broker가 메시지를 보존할지 여부를 결정합니다.
- **QoS** 바람직한 QoS 값은 0 또는 1입니다.
- **timeout** 시간 제한 값

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) MQTT 클라이언트 만들기 성공
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류입니다.
- **NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) 패킷 풀에서 패킷을 가져오지 못했습니다.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) broker와 통신하지 못했습니다.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS 수준 2 메시지는 지원되지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 MQTT 컨트롤 블록, ip_ptr 또는 패킷 풀 포인터입니다.
- NXD_MQTT_INVALID_PARAMETER (0x10009) 입력 매개 변수 오류

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a>nxd_mqtt_client_subscribe

토픽 구독

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a>설명

이 서비스는 특정 토픽을 구독합니다. QoS 수준 2 메시지 구독은 아직 지원되지 않습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.
- **topic_name** 게시할 토픽입니다.
- **topic_name_length** 토픽의 길이(바이트)입니다.
- **QoS** 바람직한 QoS 수준은 0 또는 1입니다.

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) 토픽을 성공적으로 구독했습니다.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) 클라이언트가 broker에 연결되지 않습니다.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT 뮤텍스를 가져오지 못함
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) broker로 메시지를 보낼 수 없습니다.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS 수준 2 메시지는 지원되지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 MQTT 컨트롤 블록, ip_ptr 또는 패킷 풀 포인터입니다.
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name이 설정되지 않았거나, topic_name_length가 0이거나, QoS 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a>nxd_mqtt_client_unsubscribe

토픽 구독 취소

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a>설명

이 서비스는 토픽 구독을 취소합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.
- **topic_name** 구독을 취소할 토픽입니다.
- **topic_name_length** 토픽의 길이(바이트)입니다.

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) 토픽을 성공적으로 구독 취소했습니다.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) 클라이언트가 broker에 연결되지 않습니다.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT 뮤텍스를 가져오지 못했습니다.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) broker로 메시지를 보낼 수 없습니다.
- NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록 포인터입니다.
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name이 설정되지 않았거나 topic_name_length가 0입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a>nxd_mqtt_client_receive_notify_set

MQTT 메시지 수신 알림 콜백 함수 설정

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a>설명

이 서비스는 MQTT 클라이언트를 사용하여 콜백 함수를 등록합니다. broker가 게시한 메시지를 수신하면 MQTT 클라이언트는 메시지를 수신 큐에 저장합니다. 콜백 함수가 설정된 경우 콜백 함수가 호출되어 애플리케이션에 메시지를 검색할 준비가 되었음을 알립니다. 수신 알림 함수는 포인터를 MQTT 클라이언트 제어 블록으로 가져가며, 수신 큐에서 사용할 수 있는 메시지 수를 나타내는 *message_count* 를 표시합니다. 새 메시지가 간격에 도착했을 수 있으므로 수신 알림과 애플리케이션이 이러한 메시지를 검색하는 시점 사이에 번호가 변경될 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.
- **receive_notify** 메시지 수신 시 호출되는 사용자 제공 콜백 함수입니다.

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) 수신 알림 함수를 성공적으로 설정했습니다.
- NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a>nxd_mqtt_client_message_get

broker에서 메시지 검색

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a>설명

이 서비스는 broker가 게시한 메시지를 검색합니다. 들어오는 모든 메시지는 수신 큐에 저장됩니다. 애플리케이션은 이 서비스를 사용하여 이러한 메시지를 검색합니다. 이 호출은 차단되지 않습니다. 수신 큐가 비어 있는 경우 이 서비스는 ***NXD_MQTT_NO_MESSAGE** _을 반환합니다. 들어오는 메시지에 대한 알림을 받으려는 애플리케이션은 _ *_nxd_mqtt_client_receive_notify_set_** 서비스를 호출하여 수신 콜백 함수를 등록할 수 있습니다.

호출자는 토픽 문자열과 메시지 본문에 대한 메모리 공간을 제공해야 합니다. 이러한 두 버퍼의 크기는 *topic_buffer_size* 및 *message_buffer_size* 를 사용하여 전달됩니다. 토픽 문자열과 메시지 본문의 실제 바이트 수는 *actual_topic_length* 및 *actual_message_length* 로 반환됩니다. 토픽 길이 또는 메시지 길이가 제공된 버퍼 공간보다 큰 경우 이 서비스는 오류 코드 *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE* 를 반환합니다.

애플리케이션이 더 큰 버퍼를 할당하고 다시 시도합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.
- **topic_buffer** 토픽 문자열이 복사되는 메모리 위치에 대한 포인터입니다.
- **topic_buffer_size** 토픽 버퍼의 크기입니다.
- **actual_topic_length** 실제 토픽 길이가 반환되는 메모리 위치에 대한 포인터입니다.
- **topic_buffer** 토픽 문자열이 복사되는 메모리 위치에 대한 포인터입니다.
- **message_buffer_size** 메시지 버퍼의 크기입니다.
- **actual_topic_length** 메시지 길이가 반환되는 메모리 위치에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) 메시지를 성공적으로 검색했습니다.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류
- **NXD_MQTT_NO_MESSAGE** (0x1000A) 수신 큐가 비어 있습니다.
- **NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) 토픽 버퍼 또는 메시지 버퍼가 너무 작아서 토픽 또는 메시지에 사용할 수 없습니다.
- NX_PTR_ERROR (0x07) 잘못된 MQTT 컨트롤 블록, ip_ptr 또는 패킷 풀 포인터입니다.
- NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer 또는 topic_buffer 포인터가 NULL입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a>nxd_mqtt_client_disconnect_notify_set

MQTT 메시지 연결 해제 알림 콜백 함수 설정

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a>설명

이 서비스는 MQTT 클라이언트를 사용하여 콜백 함수를 등록합니다. MQTT가 broker와의 연결이 끊어진 것을 감지하면 이 알림 함수를 호출하여 애플리케이션에 경고합니다. 따라서 애플리케이션은 이 콜백 함수를 사용하여 끊어진 연결을 감지하고 broker에 대한 연결을 다시 설정할 수 있습니다.

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.
- **disconnect_notify** MQTT가 브로커와의 연결이 끊어진 것을 감지했을 때 호출할 사용자 제공 콜백 함수입니다.

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) 연결 해제 알림 함수를 성공적으로 설정했습니다.
- NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a>nxd_mqtt_client_disconnect

broker에서 MQTT 클라이언트 연결 해제

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>설명

이 서비스는 broker에서 클라이언트 연결을 해제합니다. 수신 큐의 메시지가 릴리스됩니다. 전송 큐에 QoS 1이 있는 메시지는 릴리스되지 않습니다. 클라이언트가 서버에 다시 연결되면 클라이언트가 *clean_session* 플래그를 ***NX_TRUE*** 로 설정하여 서버에 다시 연결하지 않는 한 QoS 1 메시지를 처리할 수 있습니다.

TLS 보안 보호를 사용하여 연결한 경우 이 서비스는 TCP 연결을 해제하기 전에 TLS 세션을 닫습니다.

실제 TCP 소켓 연결 해제 호출에는 NXD_MQTT_SOCKET_TIMEOUT(타이머 틱)에 의해 정의된 대기 옵션이 있습니다. 기본값은 NX_WAIT_FOREVER입니다. 네트워크 연결이 끊어지거나 서버가 응답하지 않는 경우 무기한 중단을 방지하려면 이 옵션을 유한 값으로 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) 브로커와의 연결이 성공적으로 해제되었습니다.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT 뮤텍스를 가져오지 못했습니다.
- NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a>nxd_mqtt_client_delete

MQTT 클라이언트 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>설명

이 서비스는 MQTT 클라이언트 인스턴스를 삭제하고 내부 리소스를 릴리스합니다. 이 서비스는 클라이언트가 여전히 연결되어 있는 경우 자동으로 broker와 연결을 해제합니다. 아직 전송되지 않았거나 확인되지 않은 메시지가 릴리스됩니다. 애플리케이션에서 수신되었지만 검색되지 않은 메시지도 릴리스됩니다.

TLS 보안 보호를 사용하여 연결한 경우 이 서비스는 TCP 연결을 해제하기 전에 TLS 세션을 닫습니다.

클라이언트가 삭제된 후 MQTT 서비스를 사용하려는 애플리케이션은 새 인스턴스를 생성해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NXD_MQTT_SUCCESS** (0x00) MQTT 클라이언트를 성공적으로 삭제했습니다.
- NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
