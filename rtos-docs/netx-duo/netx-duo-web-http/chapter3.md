---
title: 챕터 3 - HTTP 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 NetX 웹 HTTP 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f7d711a67b6e129b87dc08bfd54857ffc4bc3d26c34001fe336d2b673fc53752
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801736"
---
# <a name="chapter-3---description-of-http-services"></a>챕터 3 - HTTP 서비스 설명

이 챕터에서는 아래에 나열된 모든 NetX 웹 HTTP 서비스를 알파벳 순서로 설명합니다.

> [!NOTE]
> 다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

## <a name="http-and-https-client-api"></a>HTTP 및 HTTPS 클라이언트 API

## <a name="nx_web_http_client_connect"></a>nx_web_http_client_connect

사용자 지정 요청을 위해 HTTP 서버에 대한 일반 텍스트 소켓을 엽니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **일반 텍스트** HTTP에 사용됩니다.

이 서비스는 HTTP 서버에 대한 일반 텍스트 TCP 소켓을 열지만 요청을 보내지는 않습니다. 요청은 n *x_web_http_client_request_initialize()* 를 사용하여 만들어지고 *nx_web_http_client_request_send()* 를 사용하여 전송됩니다. *nx_web_http_client_request_header_add()* 를 사용하여 사용자 지정 HTTP 헤더를 요청에 추가할 수 있습니다.

이 서비스를 사용하면 애플리케이션에서 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다. **이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.**

> [!NOTE]
> nx_web_http_client_*_start 메서드는 편의를 위해 제공되며(예: *nx_web_http_client_get_start*()) 요청 생성 및 소켓 연결을 처리합니다. 요청에 사용자 지정 HTTP 헤더가 필요하지 않은 경우에는 *nx_web_http_client_connect()* 대신 이러한 서비스 및 관련 루틴을 사용할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **server_ip** 원격 HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트(예: HTTP의 경우 80)
- **wait_option** 서비스가 기본 네트워크 작업을 대기하는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) TCP 소켓이 연결되었습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_WEB_HTTP_NOT_READY (0x3000A) 다른 요청이 이미 진행 중입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a>nx_web_http_client_create

HTTP 클라이언트 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에서 HTTP 클라이언트 인스턴스를 만듭니다. 클라이언트 인스턴스는 HTTP 또는 HTTPS에 사용할 수 있습니다. HTTP 또는 HTTPS 인스턴스를 시작하는 방법에 대한 자세한 내용은 *nx_web_http_client_connect()* 및 *nx_web_http_client_secure_connect()* 서비스를 참조하세요. GET, PUT 및 POST 메서드를 간단하게 호출하는 방법은 *nx_web_http_client_get_**, *nx_web_http_client_put_**, *nx_web_http_client_post_** 에 대한 API를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **client_name** HTTP 클라이언트 인스턴스의 이름입니다.
- **ip_ptr** IP 인스턴스에 대한 포인터입니다.
- **pool_ptr** 기본 패킷 풀에 대한 포인터입니다. 이 풀의 패킷에는 전체 응답 헤더를 처리할 수 있을 만큼 큰 페이로드가 있어야 합니다. *nx_web_http_client.h* 의 *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* 에서 정의합니다.
- **window_size** 클라이언트의 TCP 소켓 수신 창의 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 만듦
- NX_PTR_ERROR (0x16) 잘못된 HTTP, ip_ptr 또는 패킷 풀 포인터
- NX_WEB_HTTP_POOL_ERROR (0x30009) 패킷 풀의 페이로드 크기가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a>nx_web_http_client_delete

HTTP 클라이언트 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 삭제함
- NX_PTR_ERROR (0x16) 잘못된 HTTP 포인터
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a>nx_web_http_client_delete_start

일반 텍스트 HTTP DELETE 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **일반 텍스트** HTTP에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 삭제(DELETE)하는 요청을 보내려고 시도합니다. 이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 서버의 응답을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

이 API는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_client_delete_start_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 DELETE 요청 메시지를 보냈습니다.
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a>nx_web_http_client_delete_start_extended

일반 텍스트 HTTP DELETE 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **일반 텍스트** HTTP에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 삭제(DELETE)하는 요청을 보내려고 시도합니다. 이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 서버의 응답을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_client_delete_start* ()를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **resource_length** 요청된 리소스의 문자열 길이
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **host_length** 호스트의 문자열 길이
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **username_length** 인증을 위한 사용자 이름의 문자열 길이
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **password_length** 인증을 위한 암호의 문자열 길이
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 DELETE 요청 메시지를 보냈습니다.
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a>nx_web_http_client_delete_secure_start

암호화된 HTTPS DELETE 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 삭제(DELETE)하는 요청을 보내려고 시도합니다. 이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 서버의 응답을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_client_delete_secure_start_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터 리소스는 NULL로 종료되어야 합니다.
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **tls_setup** TLS 구성을 설정하는 데 사용되는 콜백. 애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 DELETE 요청 메시지를 보냈습니다.
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a>nx_web_http_client_delete_secure_start_extended

암호화된 HTTPS DELETE 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 삭제(DELETE)하는 요청을 보내려고 시도합니다. 이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 서버의 응답을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_client_delete_secure_start* ()를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터 리소스는 NULL로 종료되어야 합니다.
- **resource_length** 요청된 리소스의 문자열 길이
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **host_length** 호스트의 문자열 길이
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **username_length** 인증을 위한 사용자 이름의 문자열 길이
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **password_length** 인증을 위한 암호의 문자열 길이
- **tls_setup** TLS 구성을 설정하는 데 사용되는 콜백. 애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 DELETE 요청 메시지를 보냈습니다.
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.


### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a>nx_web_http_client_get_start

일반 텍스트 HTTP GET 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **일반 텍스트** HTTP에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 가져오려고(GET) 시도합니다. 이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_client_get_start_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 GET 시작 메시지를 성공적으로 보냄
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a>nx_web_http_client_get_start_extended

일반 텍스트 HTTP GET 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **일반 텍스트** HTTP에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 가져오려고(GET) 시도합니다. 이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_client_get_start*()를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **resource_length** 요청된 리소스의 문자열 길이
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **host_length** 호스트의 문자열 길이
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **username_length** 인증을 위한 사용자 이름의 문자열 길이
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **password_length** 인증을 위한 암호의 문자열 길이
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 GET 시작 메시지를 성공적으로 보냄
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a>nx_web_http_client_get_secure_start

암호화된 HTTPS GET 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 가져오려고(GET) 시도합니다. 이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_client_get_secure_start_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **tls_setup** TLS 구성을 설정하는 데 사용되는 콜백. 애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 GET 시작 메시지를 성공적으로 보냄
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a>nx_web_http_client_get_secure_start_extended

암호화된 HTTPS GET 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 가져오려고(GET) 시도합니다. 이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_client_secure_start*()를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **resource_length** 요청된 리소스의 문자열 길이
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **host_length** 호스트의 문자열 길이
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **username_length** 인증을 위한 사용자 이름의 문자열 길이
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **password_length** 인증을 위한 암호의 문자열 길이
- **tls_setup** TLS 구성을 설정하는 데 사용되는 콜백. 애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 GET 시작 메시지를 성공적으로 보냄
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a>nx_web_http_client_head_start

일반 텍스트 HTTP HEAD 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **일반 텍스트** HTTP에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스의 HEAD 메타데이터를 검색하려고 시도합니다. 이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 응답을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_client_head_start_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 HEAD 요청 메시지를 보냈습니다.
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a>nx_web_http_client_head_start_extended

일반 텍스트 HTTP HEAD 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **일반 텍스트** HTTP에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스의 HEAD 메타데이터를 검색하려고 시도합니다. 이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 응답을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_client_head_start*()를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **resource_length** 요청된 리소스의 문자열 길이
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **host_length** 호스트의 문자열 길이
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **username_length** 인증을 위한 사용자 이름의 문자열 길이
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **password_length** 인증을 위한 암호의 문자열 길이
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 HEAD 요청 메시지를 보냈습니다.
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a>nx_web_http_client_head_secure_start

암호화된 HTTPS HEAD 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스의 HEAD 메타데이터를 검색하려고 시도합니다. 이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 호출하여 요청된 리소스 콘텐츠에 해당하는 서버의 응답을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_client_head_secure_start_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **tls_setup** TLS 구성을 설정하는 데 사용되는 콜백. 애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 HEAD 요청 메시지를 보냈습니다.
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a>nx_web_http_client_head_secure_start_extended

암호화된 HTTPS HEAD 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스의 HEAD 메타데이터를 검색하려고 시도합니다. 이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 호출하여 요청된 리소스 콘텐츠에 해당하는 서버의 응답을 검색할 수 있습니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_client_head_secure_start*()를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **resource_length** 요청된 리소스의 문자열 길이
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **host_length** 호스트의 문자열 길이
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **username_length** 인증을 위한 사용자 이름의 문자열 길이
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **password_length** 인증을 위한 암호의 문자열 길이
- **tls_setup** TLS 구성을 설정하는 데 사용되는 콜백. 애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 HEAD 요청 메시지를 보냈습니다.
- **NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a>nx_web_http_client_request_packet_allocate

HTTP(S) 패킷을 할당

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 클라이언트 HTTP(S)에 사용할 패킷을 할당하려고 시도합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **packet_ptr** 할당된 패킷에 대한 포인터
- **wait_option** 패킷 풀에 사용 가능한 패킷이 없는 경우 대기 시간을 틱 단위로 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **NX_NO_WAIT** (0x00000000)
  - **NX_WAIT_FOREVER** (0xFFFFFFFF)
  - **timeout in ticks** (0x00000001 ~ 0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 패킷을 할당했습니다.
- **NX_NO_PACKET** (0x01) 사용 가능한 패킷이 없습니다.
- **NX_WAIT_ABORTED** (0x1A) 요청된 일시 중단이 *tx_thread_wait_abort* 호출 때문에 중단되었습니다.
- **NX_INVALID_PARAMETERS** (0x4D) 프로토콜을 지원하지 않는 패킷 크기입니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a>nx_web_http_client_post_start

HTTP POST 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **일반 텍스트** HTTP에 사용됩니다.

이 서비스는 지정된 리소스가 포함된 POST 요청을, 제공된 IP 주소 및 포트의 HTTP 서버에 보내려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_client_post_start_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 TCP 포트
- **resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **total_bytes** 전송 중인 리소스의 총 바이트 수. 후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) POST 요청을 보냈습니다.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a>nx_web_http_client_post_start_extended

HTTP POST 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **일반 텍스트** HTTP에 사용됩니다.

이 서비스는 지정된 리소스가 포함된 POST 요청을, 제공된 IP 주소 및 포트의 HTTP 서버에 보내려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_client_post_start* ()를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 TCP 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **resource_length** 요청된 리소스의 문자열 길이
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **host_length** 호스트의 문자열 길이
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **username_length** 인증을 위한 사용자 이름의 문자열 길이
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **password_length** 인증을 위한 암호의 문자열 길이
- **total_bytes** 전송 중인 리소스의 총 바이트 수. 후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) POST 요청을 보냈습니다.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a>nx_web_http_client_post_secure_start

암호화된 HTTPS POST 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.

이 서비스는 지정된 리소스가 포함된 POST 요청을, 제공된 IP 주소 및 포트의 HTTPS 서버에 보내려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_client_post_secure_start_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 TCP 포트
- **resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **total_bytes** 전송 중인 리소스의 총 바이트 수. 후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.
- **tls_setup** TLS 구성을 설정하는 데 사용되는 콜백. 애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) POST 요청을 보냈습니다.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a>nx_web_http_client_post_secure_start_extended

암호화된 HTTPS POST 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.

이 서비스는 지정된 리소스가 포함된 POST 요청을, 제공된 IP 주소 및 포트의 HTTPS 서버에 보내려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_client_post_secure_start* ()를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 TCP 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **resource_length** 요청된 리소스의 문자열 길이
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **host_length** 호스트의 문자열 길이
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **username_length** 인증을 위한 사용자 이름의 문자열 길이
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **password_length** 인증을 위한 암호의 문자열 길이
- **total_bytes** 전송 중인 리소스의 총 바이트 수. 후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.
- **tls_setup** TLS 구성을 설정하는 데 사용되는 콜백. 애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) POST 요청을 보냈습니다.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a>nx_web_http_client_put_start

HTTP PUT 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **일반 텍스트** HTTP에 사용됩니다.

이 서비스는 지정된 리소스가 포함된 PUT 요청을, 제공된 IP 주소 및 포트의 HTTP 서버에 보내려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_client_put_start_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 TCP 포트
- **resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **total_bytes** 전송 중인 리소스의 총 바이트 수. 후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a>nx_web_http_client_put_start_extended

HTTP PUT 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **일반 텍스트** HTTP에 사용됩니다.

이 서비스는 지정된 리소스가 포함된 PUT 요청을, 제공된 IP 주소 및 포트의 HTTP 서버에 보내려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_client_put_start* ()를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 TCP 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **resource_length** 요청된 리소스의 문자열 길이
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **host_length** 호스트의 문자열 길이
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **username_length** 인증을 위한 사용자 이름의 문자열 길이
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **password_length** 인증을 위한 암호의 문자열 길이
- **total_bytes** 전송 중인 리소스의 총 바이트 수. 후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a>nx_web_http_client_put_secure_start

암호화된 HTTPS PUT 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.

이 서비스는 지정된 리소스가 포함된 PUT 요청을, 제공된 IP 주소 및 포트의 HTTPS 서버에 보내려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_client_put_secure_start_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 TCP 포트
- **resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **total_bytes** 전송 중인 리소스의 총 바이트 수. 후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.
- **tls_setup** TLS 구성을 설정하는 데 사용되는 콜백. 애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a>nx_web_http_client_put_secure_start_extended

암호화된 HTTPS PUT 요청 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.

이 서비스는 지정된 리소스가 포함된 PUT 요청을, 제공된 IP 주소 및 포트의 HTTPS 서버에 보내려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.

리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_client_put_secure_start*()를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **ip_address** HTTP 서버의 IP 주소
- **server_port** 원격 HTTP 서버의 TCP 포트
- **resource** 요청된 리소스의 URL 문자열에 대한 포인터
- **resource_length** 요청된 리소스의 문자열 길이
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **host_length** 호스트의 문자열 길이
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **username_length** 인증을 위한 사용자 이름의 문자열 길이
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **password_length** 인증을 위한 암호의 문자열 길이
- **total_bytes** 전송 중인 리소스의 총 바이트 수. 후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.
- **tls_setup** TLS 구성을 설정하는 데 사용되는 콜백. 애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a>nx_web_http_client_put_packet

다음 리소스 데이터 패킷 보내기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 PUT 및 POST 작업에서 리소스 콘텐츠의 다음 패킷을 HTTP 서버로 보내려고 시도합니다. 전송된 모든 패킷의 총 길이가 위의 *nx_web_http_client_put_start()* 또는 *nx_web_http_client_post_start()* 호출(또는 해당하는 보안 버전)에 지정된 "total_bytes"와 같을 때까지 이 루틴을 반복적으로 호출해야 합니다.

또한 이 서비스는 HTTP(또는 HTTPS) 연결 설정에 문제가 있는 경우에 서버의 응답을 확인합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **packet_ptr** HTTP 서버에 보내는 리소스의 다음 콘텐츠에 대한 포인터
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 패킷을 성공적으로 보냄
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.
- **NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE**(0x3000E) 서버 오류 코드가 수신되었습니다.**
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) 패킷 길이가 올바르지 않습니다.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) PUT이 완료되기 전에 서버가 응답합니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_INVALID_PACKET (0x12) 패킷이 TCP 헤더에 비해 너무 작음
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a>nx_web_http_client_request_chunked_set

HTTP(S) 요청에 대한 청크 분할 전송 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

이 서비스는 청크 분할 전송 코딩을 사용하여 이전에 원격 호스트에 대한 소켓 연결을 설정한 *nx_web_http_client_connect()* 또는 *nx_web_http_client_secure_connect()* 호출에서 지정한 서버로 사용자 지정 HTTP(S) 요청을 보냅니다.

> [!NOTE]
> 애플리케이션에서 청크 분할 전송 코딩을 사용하여 요청 데이터 패킷을 보내는 경우 애플리케이션에서 *nx_web_http_client_request_packet_allocate*()를 호출한 후, 그리고 *nx_web_http_client_reqeust_packet_send* ()를 호출하기 전에 이 서비스를 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **chunk_size** 청크 데이터의 크기(8진수)
- **packet_ptr** HTTP(S) 요청 데이터 패킷 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 청크 분할을 설정했습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a>nx_web_http_client_request_header_add

사용자 지정 HTTP 요청에 사용자 지정 헤더 추가

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a>Description

이 서비스는 n *x_web_http_client_request_initialize()* 를 사용하여 만든 사용자 지정 HTTP 요청에 사용자 지정 헤더를 (필드 이름 및 값 형식으로) 추가합니다.

이 서비스를 사용하면 애플리케이션에서 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다. **이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.**

> [!NOTE]
> 편의를 위해 nx_web_http_client_\*_start 메서드가 제공됩니다. 이 모든 함수는 내부적으로(*nx_web_http_client_request_initialize()와 함께)* 이 루틴을 사용하여 HTTP 요청을 만들고 보냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **field_name** 필드 이름 문자열(예: "Content-Type")
- **name_length** 필드 이름 문자열의 길이(바이트)
- **field_value** 필드 값 문자열(예: "application/octet-stream")
- **value_length** 값 문자열의 길이(바이트)
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 헤더를 요청에 추가했습니다
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a>nx_web_http_client_request_initialize

사용자 지정 HTTP 요청 초기화

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a>Description

이 서비스는 사용자 지정 HTTP 요청을 만들고 HTTP 클라이언트 인스턴스에 연결합니다. 간단한 *nx_web_http_client_get_start()* 와 달리(해당 API의 PUT, POST 및 관련 보안 버전에 대한 메서드 포함), 사용자 지정 요청은 *nx_web_http_client_request_send()* 서비스를 호출할 때까지 전송되지 않습니다.

이 서비스를 사용하면 애플리케이션에서 ***nx_web_http_client_request_header_add()*** 서비스를 사용하여 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다. 이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.

> [!NOTE]
> 편의를 위해 nx_web_http_client_\*_start 메서드가 제공됩니다. 이 모든 함수는 내부적으로(*nx_web_http_client_request_send()와 함께)* 이 루틴을 사용하여 HTTP 요청을 만들고 보냅니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_client_request_initialize_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **method** 사용할 HTTP 요청 메서드. 옵션은 다음과 같이 정의됩니다.
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resource** 전송되는 리소스의 이름
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **input_size** PUT 및 POST 작업의 입력 데이터 크기. 다른 작업에는 0을 전달합니다.
- **transfer_encoding_trunked** 향후 트렁크 전송을 지원하기 위해 예약된 매개 변수
- **username** 보호된 리소스의 사용자 이름
- **password** 보호된 리소스의 암호
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 요청을 초기화했습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_WEB_HTTP_METHOD_ERROR (0x30014) 필요한 일부 정보가 누락되었습니다(예: PUT 또는 POST 작업의 input_size).

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a>nx_web_http_client_request_initialize_extended

사용자 지정 HTTP 요청 초기화

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_request_initialize_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, UINT method,
    CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, UINT username_length,
    CHAR *password, UINT password_length, UINT wait_option);
```

### <a name="description"></a>Description

이 서비스는 사용자 지정 HTTP 요청을 만들고 HTTP 클라이언트 인스턴스에 연결합니다. 간단한 *nx_web_http_client_get_start()* 와 달리(해당 API의 PUT, POST 및 관련 보안 버전에 대한 메서드 포함), 사용자 지정 요청은 *nx_web_http_client_request_send()* 서비스를 호출할 때까지 전송되지 않습니다.

이 서비스를 사용하면 애플리케이션에서 ***nx_web_http_client_request_header_add()*** 서비스를 사용하여 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다. 이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.

> [!NOTE]
> 편의를 위해 nx_web_http_client_\*_start 메서드가 제공됩니다. 이 모든 함수는 내부적으로(*nx_web_http_client_request_send()와 함께)* 이 루틴을 사용하여 HTTP 요청을 만들고 보냅니다.

리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_client_request_initialize*()를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **method** 사용할 HTTP 요청 메서드. 옵션은 다음과 같이 정의됩니다.
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resource** 전송되는 리소스의 이름
- **resource_length** 요청된 리소스의 문자열 길이
- **host** 서버 도메인 이름의 Null 종료 문자열. 이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다. 호스트 문자열은 NULL일 수 없습니다.
- **host_length** 호스트의 문자열 길이
- **input_size** PUT 및 POST 작업의 입력 데이터 크기. 다른 작업에는 0을 전달합니다.
- **transfer_encoding_trunked** 향후 트렁크 전송을 지원하기 위해 예약된 매개 변수
- **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
- **username_length** 인증을 위한 사용자 이름의 문자열 길이
- **password** 인증을 위한 선택적 암호에 대한 포인터
- **password_length** 인증을 위한 암호의 문자열 길이
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 요청을 초기화했습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_WEB_HTTP_METHOD_ERROR (0x30014) 필요한 일부 정보가 누락되었습니다(예: PUT 또는 POST 작업의 input_size).

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a>nx_web_http_client_request_packet_send

HTTP(S) 요청 데이터 패킷을 원격 서버에 보내기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 *nx_web_http_client_request_packet_allocate* ()를 사용하여 만든 사용자 지정 HTTP(S) 요청 데이터 패킷을, 이전에 원격 호스트에 대한 소켓 연결을 설정한 *nx_web_http_client_connect()* 또는 *nx_web_http_client_secure_connect(* ) 호출에서 지정한 서버로 보냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **packet_ptr** HTTP(S) 요청 데이터 패킷 포인터
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 요청 데이터 패킷을 보냈습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a>nx_web_http_client_request_send

사용자 지정 HTTP 요청 보내기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a>Description

이 서비스는 *nx_web_http_client_request_initialize()* 를 사용하여 만든 사용자 지정 HTTP 요청을, 이전에 원격 호스트에 대한 소켓 연결을 설정한 *nx_web_http_client_connect()* 또는 *nx_web_http_client_secure_connect(* ) 호출에서 지정한 서버로 보냅니다.

이 서비스를 사용하면 애플리케이션에서 ***nx_web_http_client_request_header_add()*** 서비스를 사용하여 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다. 이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.

> [!NOTE]
> 편의를 위해 nx_web_http_client_\*_start 메서드가 제공됩니다. 이 모든 함수는 내부적으로(*nx_web_http_client_request_initialize()와 함께)* 이 루틴을 사용하여 HTTP 요청을 만들고 보냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 요청을 보냈습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a>nx_web_http_client_response_body_get

다음 리소스 데이터 패킷 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a>설명

이 서비스는 이전 요청에서 요청한 리소스 콘텐츠의 다음 패킷을 검색합니다. NX_WEB_HTTP_GET_DONE의 반환 상태를 받을 때까지 이 루틴을 연속적으로 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **packet_ptr** 부분 리소스 콘텐츠가 포함된 패킷 포인터의 대상
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 클라이언트 패킷을 가져왔습니다.
- **NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP 클라이언트 GET 패킷이 완료됨
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 가져오기 모드로 설정되지 않았습니다.
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) 패킷 길이가 올바르지 않습니다.
- **NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP 상태 코드 100 계속
- **NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP 상태 코드 101 프로토콜 전환
- **NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP 상태 코드 201 생성됨
- **NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP 상태 코드 202 수락됨
- **NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP 상태 코드 203 신뢰할 수 없는 정보
- **NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP 상태 코드 204 콘텐츠 없음
- **NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP 상태 코드 205 콘텐츠 다시 설정
- **NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP 상태 코드 206 부분 콘텐츠
- **NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP 상태 코드 300 여러 선택 항목
- **NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP 상태 코드 301 영구적으로 이동됨
- **NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP 상태 코드 302 있음
- **NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP 상태 코드 303 기타 참조
- **NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP 상태 코드 304 수정되지 않음
- **NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP 상태 코드 305 프록시 사용
- **NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP 상태 코드 307 임시 리디렉션
- **NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP 상태 코드 400 잘못된 요청
- **NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP 상태 코드 401 권한 없음
- **NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP 상태 코드 402 결제 필요
- **NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP 상태 코드 403 사용할 수 없음
- **NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP 상태 코드 404 찾을 수 없음
- **NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP 상태 코드 405 메서드를 사용할 수 없음
- **NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP 상태 코드 406 허용 안 됨
- **NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP 상태 코드 407 프록시 인증 필요
- **NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP 상태 코드 408 요청 시간 제한
- **NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP 상태 코드 409 충돌
- **NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP 상태 코드 410 없음
- **NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP 상태 코드 411 길이가 필요함
- **NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP 상태 코드 412 사전 조건 실패
- **NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP 상태 코드 413 요청 엔터티가 너무 큼
- **NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP 상태 코드 414 요청 URL이 너무 큼
- **NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP 상태 코드 415 지원되지 않는 미디어 형식
- **NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP 상태 코드 416 요청한 범위가 충분하지 않음
- **NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP 상태 코드 417 예상 실패
- **NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP 상태 코드 500 내부 서버 오류
- **NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP 상태 코드 501 구현되지 않음
- **NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP 상태 코드 502 잘못된 게이트웨이
- **NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP 상태 코드 503 서비스를 사용할 수 없음
- **NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP 상태 코드 504 게이트웨이 시간 제한
- **NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) http 상태 코드 505 지원되지 않는 HTTP 버전
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a>nx_web_http_client_response_header_callback_set

HTTP 헤더를 처리할 때 호출할 콜백 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a>Description

이 서비스는 NetX 웹 HTTP 클라이언트가 원격 HTTP 서버에서 들어오는 응답의 HTTP 헤더를 처리할 때마다 호출되는 콜백을 할당합니다. 콜백은 처리되는 응답의 헤더마다 한 번씩 호출됩니다. 콜백은 HTTP 애플리케이션이 HTTP 서버 응답의 각 헤더에 액세스하여 NetX 웹 HTTP 클라이언트의 기본 처리 작업 이상의 작업을 수행하는 것을 허용합니다.

### <a name="input-parameters"></a>입력 매개 변수

**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터

**callback_function** 응답 헤더를 처리하는 동안 호출되는 콜백. 콜백은 필드 이름과 값을 문자열(및 해당 길이)로 사용하여 호출됩니다. 예를 들어 "Content-Length: 100"이라는 헤더를 사용하면 *field_name* 은 "Content-Length"이고 *field_value* 는 문자열 "100"인 함수가 호출됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 콜백을 할당했습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a>nx_web_http_client_secure_connect

사용자 지정 요청을 위해 HTTPS 서버에 대한 TLS 세션을 엽니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a>Description

이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.

이 서비스는 HTTPS 서버에 대한 보안 TLS 세션을 열지만 요청을 보내지는 않습니다. 요청은 n *x_web_http_client_request_initialize()* 를 사용하여 만들어지고 *nx_web_http_client_request_send()* 를 사용하여 전송됩니다. *nx_web_http_client_request_header_add()* 를 사용하여 사용자 지정 HTTP 헤더를 요청에 추가할 수 있습니다.

이 서비스를 사용하면 애플리케이션에서 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다. **이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.**

> [!NOTE]
> 편의를 위해 nx_web_http_client_\*_start 메서드가 제공됩니다. 이 모든 함수는 내부적으로(*nx_web_http_client_request_initialize()와 함께)* 이 루틴을 사용하여 HTTP 요청을 만들고 보냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **server_ip** 원격 HTTPS 서버의 IP 주소
- **server_port** 원격 HTTPS 서버의 포트(예: HTTPS의 경우 443)
- **tls_setup** TLS 구성을 설정하는 데 사용되는 콜백. 애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.
- **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) TLS 세션이 연결되었습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_WEB_HTTP_NOT_READY (0x3000A) 다른 요청이 이미 진행 중입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a>HTTP 및 HTTPS 서버 API

## <a name="nx_web_http_server_cache_info_callback_set"></a>nx_web_http_server_cache_info_callback_set

URL 최대 기간 및 날짜를 검색하는 콜백 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a>Description

이 서비스는 지정된 리소스의 최대 사용 기간 및 마지막으로 수정한 날짜를 가져오기 위해 호출되는 콜백 서비스를 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 제어 블록에 대한 포인터
- **cache_info_get** 콜백에 대한 포인터입니다.
- **max_age** 리소스의 최대 사용 기간에 대한 포인터입니다.
- **data** 반환된 마지막 수정 날짜에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함
- **NX_PTR_ERROR** (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

초기화

### <a name="example"></a>예제

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a>nx_web_http_server_callback_data_send

콜백 함수의 데이터 보내기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션의 콜백 루틴에서 제공된 패킷의 데이터를 보냅니다. 일반적으로 GET/POST 요청과 연결된 동적 데이터를 보내는 데 사용됩니다. 이 함수를 사용할 경우 콜백 루틴에서 전체 응답을 적절한 형식으로 보내야 합니다. 또한 콜백 루틴에서 NX_WEB_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 제어 블록에 대한 포인터
- **data_ptr** 보내는 데이터에 대한 포인터
- **data_length** 보내는 바이트 수

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 서버 데이터를 성공적으로 보냄
- **NX_PTR_ERROR** (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a>nx_web_http_server_callback_generate_response_header

콜백 함수에서 응답 헤더 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Description

이 서비스는 http 응답 헤더를 생성하기 위해 (애플리케이션에서 정의한) HTTP(S) 서버 콜백 루틴에 사용됩니다. HTTP 응답이 필요한 클라이언트 GET, PUT 및 DELETE 요청에 HTTP 서버가 응답할 때 서버 콜백 루틴이 호출됩니다. 이 함수는 애플리케이션의 응답 정보를 사용하여 적절한 응답 헤더를 생성합니다. 서버 요청 콜백 루틴에 대한 자세한 내용은 *nx_web_http_server_create()* 서비스를 참조하세요.

이 API는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_server_callback_generate_response_header_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 제어 블록에 대한 포인터
- **packet_pptr** 메시지에 할당된 패킷 포인터에 대한 포인터입니다.
- **status_code** 리소스 상태를 표시합니다. 예제:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **content_length** 콘텐츠 크기(바이트)
- **content_type** HTTP 형식(예: "텍스트/일반")
- **additional_header** 추가 헤더 텍스트에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTML 헤더를 성공적으로 만듦
- **NX_PTR_ERROR** (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a>nx_web_http_server_callback_generate_response_header_extended

콜백 함수에서 응답 헤더 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a>Description

이 서비스는 http 응답 헤더를 생성하기 위해 (애플리케이션에서 정의한) HTTP(S) 서버 콜백 루틴에 사용됩니다. HTTP 응답이 필요한 클라이언트 GET, PUT 및 DELETE 요청에 HTTP 서버가 응답할 때 서버 콜백 루틴이 호출됩니다. 이 함수는 애플리케이션의 응답 정보를 사용하여 적절한 응답 헤더를 생성합니다. 서버 요청 콜백 루틴에 대한 자세한 내용은 *nx_web_http_server_create()* 서비스를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 제어 블록에 대한 포인터
- **packet_pptr** 메시지에 할당된 패킷 포인터에 대한 포인터입니다.
- **status_code** 리소스 상태를 표시합니다. 예제:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **status_code_length** 상태 코드의 문자열 길이
- **content_length** 콘텐츠 크기(바이트)
- **content_type** HTTP 형식(예: "텍스트/일반")
- **content_type_length** 콘텐츠 형식의 문자열 길이
- **additional_header** 추가 헤더 텍스트에 대한 포인터
- **additional_header_length** 추가 헤더 텍스트의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTML 헤더를 성공적으로 만듦
- **NX_PTR_ERROR** (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a>nx_web_http_server_callback_packet_send

콜백 함수의 HTTP 패킷 보내기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

이 서비스는 HTTP 콜백의 전체 HTTP 서버 응답을 보냅니다. HTTP 서버는 NX_WEB_HTTP_SERVER _TIMEOUT_SEND를 사용하여 패킷을 보냅니다. HTTP 헤더와 데이터는 패킷에 추가해야 합니다. 반환 상태에서 오류가 표시되는 경우 HTTP 애플리케이션에서 패킷을 해제해야 합니다.

콜백에서 NX_WEB_HTTP_CALLBACK_COMPLETED를 반환해야 합니다.

자세한 예제는 *nx_web_http_server_callback_generate_response_header()* 를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 제어 블록에 대한 포인터
- **packet_ptr** 보내는 패킷에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버 패킷을 성공적으로 보냄
- **NX_PTR_ERROR** (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a>nx_web_http_server_callback_response_send

콜백 함수의 응답 보내기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션의 콜백 루틴에서 제공된 응답 정보를 보냅니다. 일반적으로 GET/POST 요청과 연결된 사용자 지정 응답을 보내는 데 사용됩니다. 이 함수를 사용하는 경우 콜백 루틴에서 NX_WEB_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_web_http_server_callback_response_send_extended()* 를 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 제어 블록에 대한 포인터
- **header** 응답 헤더 문자열에 대한 포인터입니다.
- **information** 정보 문자열에 대한 포인터
- **additional_info** 추가 정보 문자열에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버 응답을 성공적으로 보냄

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a>nx_web_http_server_callback_response_send_extended

콜백 함수의 응답 보내기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션의 콜백 루틴에서 제공된 응답 정보를 보냅니다. 일반적으로 GET/POST 요청과 연결된 사용자 지정 응답을 보내는 데 사용됩니다. 이 함수를 사용하는 경우 콜백 루틴에서 NX_WEB_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.

헤더, 정보 및 추가 정보의 문자열은 NULL로 종결되어야 하고 각 문자열의 길이가 인수 목록에 지정된 길이와 일치해야 합니다.

이 서비스는 *nx_web_http_server_callback_response_send()* 를 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 제어 블록에 대한 포인터
- **header** 응답 헤더 문자열에 대한 포인터입니다.
- **header_length** 응답 헤더 문자열의 길이입니다.
- **information** 정보 문자열에 대한 포인터
- **information_length** 정보 문자열의 길이
- **additional_info** 추가 정보 문자열에 대한 포인터
- **additional_info_length** 추가 정보 문자열의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버 응답을 성공적으로 보냄

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a>nx_web_http_server_content_get

요청에서 콘텐츠 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Description

이 서비스는 POST 또는 PUT HTTP 클라이언트 요청에서 지정된 양의 콘텐츠를 검색하려고 시도합니다. HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_web_http_server_create()* )에서 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 제어 블록에 대한 포인터
- **packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다. 이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.
- **byte_offset** 콘텐츠 영역으로 오프셋할 바이트 수입니다.
- **destination_ptr** 콘텐츠의 대상 영역에 대한 포인터입니다.
- **destination_size** 대상 영역에서 사용 가능한 최대 바이트 수입니다.
- **actual_size** 복사된 콘텐츠의 실제 크기로 설정되는 대상 변수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버 콘텐츠를 가져왔습니다.
- **NX_WEB_HTTP_ERROR** (0x30000) HTTP 서버 내부 오류가 발생했습니다.
- **NX_WEB_HTTP_DATA_END** (0x30007) 요청 콘텐츠의 끝입니다.
- **NX_WEB_HTTP_TIMEOUT** (0x30001) 콘텐츠의 다음 패킷을 가져오는 중에 HTTP 서버 시간이 초과되었습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a>nx_web_http_server_content_get_extended

요청에서 콘텐츠 가져오기/길이가 0인 콘텐츠 길이 지원

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Description

이 서비스는 *nx_web_http_server_content_get()* 과 거의 동일하며, POST 또는 PUT HTTP 클라이언트 요청에서 지정된 양의 콘텐츠를 검색하려고 시도합니다. 그러나 콘텐츠 길이가 0인 요청('빈 요청')을 유효한 요청으로 처리합니다. HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_web_http_server_create()* )에서 호출해야 합니다.

이 서비스는 *nx_web_http_server_content_get()* 을 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 제어 블록에 대한 포인터
- **packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다. 이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.
- **byte_offset** 콘텐츠 영역으로 오프셋할 바이트 수입니다.
- **destination_ptr** 콘텐츠의 대상 영역에 대한 포인터입니다.
- **destination_size** 대상 영역에서 사용 가능한 최대 바이트 수입니다.
- **actual_size** 복사된 콘텐츠의 실제 크기로 설정되는 대상 변수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 콘텐츠를 성공적으로 가져옴
- **NX_WEB_HTTP_ERROR** (0x30000) HTTP 서버 내부 오류가 발생했습니다.
- **NX_WEB_HTTP_DATA_END** (0x30007) 요청 콘텐츠의 끝입니다.
- **NX_WEB_HTTP_TIMEOUT** (0x30001) 다음 패킷을 가져오는 중에 HTTP 서버 시간이 초과되었습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a>nx_web_http_server_content_length_get

요청에서 콘텐츠 길이 가져오기/콘텐츠 길이 0 지원

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Description

이 서비스는 제공된 패킷에서 HTTP 콘텐츠 길이를 검색하려고 시도합니다. 반환 값은 성공적인 완료 상태를 나타내며, 실제 길이 값은 content_length 입력 포인터에 반환됩니다. HTTP 콘텐츠가 없거나 콘텐츠 길이가 0인 경우에도 이 루틴에서 여전히 성공적인 완료 상태를 반환하며 content_length 입력 포인터가 유효한 길이(0)를 가리킵니다. HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_web_http_server_create()* )에서 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다. 이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.
- **content_length** 콘텐츠 길이 필드에서 검색된 값에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버 콘텐츠 길이를 가져왔습니다.
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) HTTP 헤더 형식이 올바르지 않습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a>nx_web_http_server_create

HTTP 서버 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Description

이 서비스는 자체 ThreadX 스레드의 컨텍스트에서 실행되는 HTTP 서버 인스턴스를 만듭니다. 선택적 *authentication_check* 및 *request_notify* 애플리케이션 콜백 루틴은 HTTP 서버의 기본 작업에 대한 애플리케이션 소프트웨어 제어를 제공합니다.

이 서비스는 일반 텍스트 HTTP 서버와 TLS 보안 HTTPS 서버를 만드는 데 사용됩니다. TLS를 통해 HTTPS를 사용하도록 설정하려면 *nx_web_http_server_secure_configure()* 서비스를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **http_server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.
- **http_server_name** HTTP 서버 이름에 대한 포인터입니다.
- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터
- **server_port** 서버 인스턴스의 TCP 수신 대기 포트
- **media_ptr** 이전에 만든 FileX 미디어 인스턴스에 대한 포인터
- **stack_ptr** HTTP 서버 스레드 스택 영역에 대한 포인터입니다.
- **stack_size** HTTP 서버 스레드 스택 크기에 대한 포인터입니다.
- **authentication_check** 애플리케이션의 인증 확인 루틴에 대한 함수 포인터입니다. 지정된 경우 이 루틴은 각 HTTP 클라이언트 요청에 대해 호출됩니다. 이 매개 변수가 NULL이면 인증이 수행되지 않습니다. 이 매개 변수는 사용되지 않습니다. 대신 *nx_web_http_server_authenticate_check_set*()를 호출하세요.
- **request_notify** 애플리케이션의 요청 알림 루틴에 대한 함수 포인터. 지정된 경우 HTTP 서버에서 요청을 처리하기 전에 이 루틴이 호출됩니다. 이렇게 하면 HTTP 클라이언트 요청을 완료하기 전에 리소스 이름을 리디렉션하거나 리소스 내의 필드를 업데이트할 수 있습니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버를 성공적으로 만듦
- NX_PTR_ERROR (0x07) 잘못된 HTTP 서버, IP, 미디어, 스택 또는 패킷 풀 포인터
- NX_WEB_HTTP_POOL_ERROR (0x30009) 풀의 패킷 페이로드가 전체 HTTP 요청을 포함할 만큼 충분히 크지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a>nx_web_http_server_delete

HTTP 서버 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 HTTP 서버 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **http_server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버를 성공적으로 삭제함
- NX_PTR_ERROR (0x07) 잘못된 HTTP 서버 포인터
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a>nx_web_http_server_get_entity_content

엔터티 데이터의 위치 및 길이 검색

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a>Description

이 서비스는 받은 클라이언트 메시지의 현재 다중 파트 엔터티 내의 데이터 시작 위치 및 경계 문자열이 포함되지 않는 데이터 길이를 결정합니다. 내부적으로 HTTP 서버는 여러 엔터티가 있는 메시지에 대해 동일한 클라이언트 데이터그램에서 이 함수를 다시 호출할 수 있도록 자체 오프셋을 업데이트합니다. 패킷 포인터를 클라이언트 메시지가 다중 패킷 데이터그램인 다음 패킷으로 업데이트합니다.

이 서비스를 사용하려면 NX_WEB_HTTP_MULTIPART_ENABLE을 사용하도록 설정해야 합니다. 또한 packet_pptr을 사용하여 가리킨 패킷을 애플리케이션에서 해제하면 안 됩니다. 이 작업은 HTTP 서버에서 내부적으로 수행합니다.

자세한 내용은 *nx_web_http_server_get_entity_header()* 를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버에 대한 포인터입니다.
- **packet_pptr** 패킷 포인터의 위치에 대한 포인터 애플리케이션에서 이 패킷을 해제하면 안 됩니다.
- **available_offset** 패킷 선행 포인터에서 엔터티 데이터의 오프셋에 대한 포인터
- **available_length** 엔터티 데이터의 길이에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 엔터티 콘텐츠의 크기와 위치를 성공적으로 검색함
- **NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) HTTP 서버 내부 다중 파트 표식에 대한 콘텐츠가 이미 있습니다.
- NX_WEB_HTTP_ERROR(0x30000) HTTP 서버 내부 오류가 발생했습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a>nx_web_http_server_get_entity_header

엔터티 헤더의 콘텐츠 검색

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a>Description

이 서비스는 지정된 버퍼에서 엔터티 헤더를 검색합니다. 다중 엔터티 헤더가 있는 클라이언트 데이터그램에서 다음 다중 파트 엔터티를 찾도록 HTTP 서버에서 내부적으로 자체 포인터를 업데이트합니다. 패킷 포인터를 클라이언트 메시지가 다중 패킷 데이터그램인 다음 패킷으로 업데이트합니다.

이 서비스를 사용하려면 NX_WEB_HTTP_MULTIPART_ENABLE을 사용하도록 설정해야 합니다. 또한 packet_pptr을 사용하여 가리킨 패킷을 애플리케이션에서 해제하면 안 됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버에 대한 포인터입니다.
- **packet_pptr** 패킷 포인터의 위치에 대한 포인터 애플리케이션에서 이 패킷을 해제하면 안 됩니다.
- **entity_header_buffer** 엔터티 헤더를 저장하는 위치에 대한 포인터
- **buffer_size** 입력 버퍼의 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 엔터티 헤더를 검색했습니다.
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) 엔터티 헤더 필드가 없습니다.
- **NX_WEB_HTTP_TIMEOUT** (0x30001) 다중 패킷 클라이언트 메시지에 대한 다음 패킷을 받는 시간이 만료되었습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자
- NX_WEB_HTTP_ERROR (0x30000) 내부 HTTP 오류가 발생했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
                NX_SUCCESS)
            {
                nx_packet_release(response_pkt);
            }
        }
    }
    else
    {
        /* Indicate we have not processed the response to client yet.*/
        return(NX_SUCCESS);
    }

    /* Indicate the response to client is transmitted. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a>nx_web_http_server_gmt_callback_set

GMT 날짜 및 시간을 가져오는 콜백 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 HTTP 서버에서 GMT 날짜 및 시간을 가져오는 콜백을 설정합니다. 이 서비스는 HTTP 서버가 클라이언트에 대한 HTTP 서버 응답에 헤더를 만들 때 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버에 대한 포인터
- **gmt_get** GMT 콜백에 대한 포인터
- **date** 검색된 날짜에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함
- NX_PTR_ERROR (0x07) 잘못된 패킷 또는 매개 변수 포인터

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a>nx_web_http_server_invalid_userpassword_notify_set

잘못된 사용자/암호를 처리하는 콜백 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a>Description

이 서비스는 다이제스트 또는 기본 인증을 통해 클라이언트 GET, PUT 또는 DELETE 요청에서 잘못된 사용자 이름 및 암호를 받을 때 호출되는 콜백을 설정합니다. HTTP 서버는 이전에 만들어야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버에 대한 포인터입니다.
- **invalid_username_password_callback** 잘못된 사용자/전달 콜백에 대한 포인터입니다.
- **resource** 클라이언트에서 지정한 리소스에 대한 포인터
- **client_address** 클라이언트 주소
- **request_type** 클라이언트 요청 유형을 표시합니다. 다음과 같은 유형이 있습니다.
  - *NX_WEB_HTTP_SERVER_GET_REQUEST*
  - *NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*
  - *NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a>nx_web_http_server_mime_maps_additional_set

HTML에 대한 추가 MIME 맵 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a>Description

이 서비스를 통해 HTTP 애플리케이션 개발자는 NetX 웹 HTTP 서버에서 제공하는 기본 MIME 형식의 MIME 형식을 추가할 수 있습니다. 정의된 형식 목록은 *nx_web_http_server_get_type()* 을 참조하세요.

클라이언트 요청(예: GET 요청)을 받으면 HTTP 서버에서 우선적으로 추가 MIME 맵 세트를 사용하여 HTTP 헤더에서 요청된 파일 형식을 구문 분석하고, 일치하는 항목이 없는 경우 HTTP 서버의 기본 MIME 맵에서 일치 항목을 찾습니다. 일치하는 항목이 없으면 MIME 형식은 기본적으로 "텍스트/일반"으로 설정됩니다.

요청 알림 함수가 HTTP 서버에 등록된 경우 요청 알림 콜백에서 *nx_web_http_server_type_get_extended()* 를 호출하여 파일 형식을 구문 분석할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.
- **mime_maps** MIME 맵 배열에 대한 포인터입니다.
- **mime_map_num** 배열의 MIME 맵 수입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버 MIME 맵을 성공적으로 설정함
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a>nx_web_http_server_response_packet_allocate

HTTP(S) 패킷 할당

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 HTTP(S) 서버용 패킷을 할당하려고 시도합니다.

이 패킷을 입력으로 사용하는 후속 NetX 또는 HTTP 서버 API(예: nx_packet_data_append 또는 **nx_web_http_server_callback_packet_send)가 **실패** 하는 경우 애플리케이션에서 패킷을 해제해야 합니다. **

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 제어 블록에 대한 포인터
- **packet_ptr** 할당된 패킷에 대한 포인터
- **wait_option** 패킷 풀에 사용 가능한 패킷이 없는 경우 대기 시간을 틱 단위로 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **NX_NO_WAIT** (0x00000000) NX_NO_WAIT를 선택하면 요청을 수행할 수 없는 경우 호출 스레드가 즉시 반환됩니다.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.
  - **timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 패킷을 할당했습니다.
- **NX_NO_PACKET** (0x01) 사용 가능한 패킷이 없습니다.
- **NX_WAIT_ABORTED** (0x1A) 요청된 일시 중단이 *tx_thread_wait_abort* 호출 때문에 중단되었습니다.
- **NX_INVALID_PARAMETERS** (0x4D) 프로토콜을 지원하지 않는 패킷 크기입니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a>nx_web_http_server_packet_content_find

콘텐츠 길이를 추출하고 데이터 시작에 대한 포인터 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Description

이 서비스는 HTTP 헤더에서 콘텐츠 길이를 추출합니다. 또한 제공된 패킷을 다음과 같이 업데이트합니다. 패킷 선행 포인터(쓸 패킷 버퍼의 시작 위치)가 HTTP 헤더를 방금 전달한 HTTP 콘텐츠(데이터)로 설정됩니다.

현재 패킷에서 콘텐츠의 시작 위치를 찾을 수 없는 경우 함수에서 NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE 대기 옵션을 사용하여 다음 패킷을 받을 때까지 기다립니다.

이 서비스는 엔터티 헤더 앞의 패킷 선행 포인터를 수정하므로 *nx_web_http_server_get_entity_header()* 를 호출하기 전에 호출하지 않아야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.
- **packet_ptr** 업데이트된 선행 포인터를 사용하여 패킷을 반환하는 패킷 포인터에 대한 포인터
- **content_length** 추출된 content_length에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 콘텐츠 길이가 있고 패킷을 성공적으로 업데이트함
- **NX_WEB_HTTP_TIMEOUT**(0x30001) 다음 패킷을 기다리는 시간이 만료되었습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a>nx_web_http_server_packet_get

다음 HTTP 패킷 받기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a>Description

이 서비스는 HTTP 서버 소켓에서 받은 다음 패킷을 반환합니다. 패킷 수신 대기 옵션은 NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE입니다.

성공하면 애플리케이션에서 패킷을 해제해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.
- **packet_ptr** 받은 패킷에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 다음 HTTP 패킷을 성공적으로 받음
- **NX_WEB_HTTP_TIMEOUT**(0x30001) 다음 패킷을 기다리는 시간이 만료되었습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a>nx_web_http_server_param_get

요청에서 매개 변수 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a>Description

이 서비스는 제공된 요청 패킷에서 지정된 HTTP URL 매개 변수를 검색하려고 시도합니다. 요청된 HTTP 매개 변수가 없는 경우 이 루틴에서 NX_WEB_HTTP_NOT_FOUND 상태를 반환합니다. 이 루틴은 HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_web_http_server_create()* )에서 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다. 애플리케이션에서 이 패킷을 해제하면 안 됩니다.
- **param_number** 매개 변수 목록에서 왼쪽에서 오른쪽으로 0에서 시작하는 매개 변수의 논리적 번호입니다.
- **param_ptr** 매개 변수를 복사하는 대상 영역
- **param_size** 총 매개 변수 데이터 길이(바이트)를 반환합니다.
- **max_param_size** 매개 변수 대상 영역의 최대 크기

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버 매개 변수를 성공적으로 가져옴
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) 지정된 매개 변수가 없습니다.
- **NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) 요청 매개 변수가 제대로 종료되지 않았습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a>nx_web_http_server_query_get

요청에서 쿼리 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a>Description

이 서비스는 제공된 요청 패킷에서 지정된 HTTP URL 쿼리를 검색하려고 시도합니다. 요청된 HTTP 쿼리가 없는 경우 이 루틴에서 NX_WEB_HTTP_NOT_FOUND 상태를 반환합니다. 이 루틴은 HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_web_http_server_create()* )에서 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다. 애플리케이션에서 이 패킷을 해제하면 안 됩니다.
- **query_number** 쿼리 목록에서 왼쪽에서 오른쪽으로 0에서 시작하는 매개 변수의 논리적 번호입니다.
- **query_ptr** 쿼리를 복사하는 대상 영역
- **query_size** 쿼리 데이터 크기(바이트)를 반환 합니다.
- **max_query_size** 쿼리 대상 영역의 최대

크기

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버 쿼리를 성공적으로 가져옴
- **NX_WEB_HTTP_FAILED** (0x30002) 쿼리 크기가 너무 작습니다.
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) 지정된 쿼리가 없습니다.
- **NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) 클라이언트 요청에 쿼리가 없습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a>nx_web_http_server_response_chunked_set

HTTP(S) 응답에 대한 청크 분할 전송 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

이 서비스는 *nx_web_http_server_response_packet_allocate*()를 사용하여 만든 사용자 지정 HTTP(S) 응답 데이터 패킷을 클라이언트에 보내기 위해 청크 분할 전송 코딩을 사용합니다.

> [!NOTE]
> 애플리케이션에서 청크 분할 전송 코딩을 사용하여 응답 데이터 패킷을 보내는 경우 애플리케이션에서 *nx_web_http_server_response_packet_allocate*()를 호출한 후, 그리고 *nx_web_http_server_callback_packet_send*()를 호출하기 전에 이 서비스를 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
- **chunk_size** 청크 데이터의 크기(8진수)
- **packet_ptr** HTTP(S) 요청 데이터 패킷 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 청크 분할을 설정했습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a>nx_web_http_server_secure_configure

보안 HTTPS에 TLS를 사용하도록 HTTP 서버 구성

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a>Description

이 서비스는 보안 HTTPS 통신에 TLS를 사용하도록 이전에 만든 NetX 웹 HTTP 서버 인스턴스를 구성합니다. 들어오는 각 HTTPS 클라이언트에서 일관적인 동작을 경험할 수 있도록, 매개 변수는 상태가 같은 모든 TLS 세션을 구성하는 데 사용됩니다. TLS 세션 수는 NX_WEB_HTTP_SESSION_MAX 매크로를 사용하여 제어합니다.

암호화 루틴 테이블(ciphersuite 테이블)은 함수 포인터만 포함하므로 모든 TLS 세션 간에 공유됩니다.

메타데이터 및 패킷 리어셈블리 버퍼는 모든 TLS 세션 간에 균등하게 분할됩니다. 버퍼 크기를 세션 수로 균등하게 나눌 수 없는 경우 나머지 버퍼는 사용되지 않습니다.

전달된 ID 인증서는 모든 세션에서 사용됩니다. TLS 작업 중에는 서버 ID 인증서를 읽기만 하므로 각 세션에 복사본이 필요하지 않습니다.

신뢰할 수 있는 인증서는 HTTPS 서버의 각 TLS 세션에 추가됩니다. 이러한 인증서는 원격 인증서 공간이 제공될 때 자동으로 사용하도록 설정되는 클라이언트 인증서 인증에 사용됩니다.

원격 인증서 배열 및 버퍼는 기본적으로 모든 TLS 세션 간에 공유됩니다. 원격 인증서는 원격 인증서 수가 0이 아닌 경우에 자동으로 사용하도록 설정되는 클라이언트 인증서 인증에 사용됩니다. 버퍼를 공유하기 때문에 인증서의 유효성을 검사하는 동안 일부 세션이 차단될 수 있습니다.

클라이언트 인증서 인증을 사용하지 않도록 설정하려면 remote_certificates 매개 변수에 NX_NULL을 전달하고 remote_certs_num 매개 변수에 0 값을 전달합니다.

반환 값에는 TLS 세션 구성의 문제로 인한 모든 TLS 오류 코드가 포함됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터
- **crypto_table** TLS ciphersuite 테이블에 대한 포인터
- **metadata_buffer** 암호화 메타데이터 버퍼에 대한 포인터
- **metadata_size** 암호화 메타데이터 버퍼의 크기
- **packet_buffer** TLS 패킷 리어셈블리 버퍼
- **packet_buffer** TLS 패킷 버퍼의 크기 - (<원하는 TLS 버퍼 크기 * NX_WEB_HTTP_SESSION_MAX)와 같아야 합니다.
- **identity_certificate** TLS 서버 ID 인증서 - 모든 HTTPS 서버 세션에 사용됩니다.
- **trusted_certificates** *remote_certs_num* 매개 변수에 0이 아닌 값을 전달하여 클라이언트 인증서 인증을 사용하도록 설정한 경우 들어오는 클라이언트 인증서의 유효성을 검사하는 데 사용되는 NX_SECURE_X509_CERT 개체 배열에 대한 포인터
- **trusted_certs_num** *trusted_certificates* 배열에 들어 있는 신뢰할 수 있는 인증서의 수
- **remote_certificates** 들어오는 클라이언트 인증서에 사용되는 NX_SECURE_X509_CERT 개체 배열에 대한 포인터
- **remote_certs_num** 원격 인증서의 수. 클라이언트에서 예상되는 최대 인증서 수여야 합니다. 이 값이 0이 아니면 자동으로 클라이언트 인증서 인증을 사용하도록 설정됩니다.
- **remote_certificate_buffer** 클라이언트 인증서 인증을 사용하는 경우 클라이언트에서 들어오는 원격 인증서를 포함하는 버퍼 remote_cert_buffer_size 원격 인증서 버퍼의 크기. (<예상하는 최대 인증서 크기 \* remote_certs_num)과 같아야 합니다.


### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.
- **NX_NOT_CONNECTED** (0x38) 기본 TCP 소켓이 더 이상 연결되어 있지 않습니다.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) 받은 TLS 메시지 유형이 올바르지 않습니다.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) 원격 호스트에서 제공하는 암호화가 지원되지 않습니다.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) TLS 핸드셰이크 중 메시지 처리가 실패했습니다.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) 들어오는 메시지가 해시 MAC 검사에 실패했습니다.
- **NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) 기본 TCP 소켓 보내기가 실패했습니다.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 들어오는 메시지의 길이 필드가 올바르지 않습니다.
- **NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) 들어오는 ChangeCipherSpec 메시지가 올바르지 않습니다.
- **NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) 들어오는 TLS 인증서를 원격 TLS 서버 식별에 사용할 수 없습니다.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) 원격 호스트에서 제공하는 공개 키 암호가 지원되지 않습니다.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) NetX Secure TLS 스택에서 지원하는 ciphersuite가 없다고 원격 호스트에서 알렸습니다.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) 받은 TLS 메시지의 헤더에 알 수 없는 TLS 버전이 있습니다.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) 받은 TLS 메시지의 헤더에 알고 있지만 지원되지 않는 TLS 버전이 있습니다.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) 내부 TLS 패킷을 할당하지 못했습니다.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) 원격 호스트에서 제공한 인증서가 올바르지 않습니다.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) 원격 호스트가 오류를 알리는 경고를 보내고 TLS 세션을 종료했습니다.
- **NX_PTR_ERROR** (0x07) 잘못된 포인터를 사용하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a>nx_web_http_server_start

HTTP 서버 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 HTTP 또는 HTTPS 서버 인스턴스를 시작합니다.

HTTPS 서버는 HTTP와 동일한 API를 공유합니다. HTTP 서버에서 TLS를 통해 HTTPS를 사용하도록 설정하려면 *nx_web_http_server_secure_configure()* 서비스를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버를 시작했습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a>nx_web_http_server_stop

HTTP 서버 중지

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 HTTP 서버 인스턴스를 중지합니다. 이 루틴은 HTTP 서버 인스턴스를 삭제하기 전에 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) HTTP 서버를 중지했습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a>nx_web_http_server_type_get

클라이언트 HTTP 요청에서 파일 형식 추출

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a>Description

> [!NOTE]
> 이 서비스는 더 이상 사용되지 않습니다. 사용자는 *nx_web_http_server_type_get_extended()* 서비스를 사용하는 것이 좋습니다.

이 서비스는 *http_type_string* 버퍼에서 HTTP 요청 유형을 추출하고, 입력 버퍼 *name*(일반적으로 URL)의 *string_size* 에서 길이를 추출합니다. MIME 맵이 없으면 기본적으로 "텍스트/일반" 형식으로 설정됩니다. MIME 맵이 있으면 추출된 형식을 HTTP 서버 기본 MIME 맵과 비교하여 매칭합니다. NetX 웹 HTTP 서버의 기본 MIME 맵은 다음과 같습니다.

- html text/html
- htm text/html
- txt text/plain
- gif image/gif
- jpg image/jpeg
- ico image/x-icon

제공할 경우 사용자 정의 추가 MIME 맵 세트도 검색합니다. 사용자 정의 맵에 대한 자세한 내용은 *nx_web_http_server_mime_maps_addtional_set()* 를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터
- **name** 검색할 버퍼에 대한 포인터
- **http_type_string** 추출된 HTML 형식 문자열에 대한 포인터
- **string_size** 추출된 HTML 형식 문자열 길이를 반환하는 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 형식을 추출했습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) 기본 "텍스트/일반" 형식이 반환되었습니다.

### <a name="allowed-from"></a>허용 위치

애플리케이션

### <a name="example"></a>예제

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a>nx_web_http_server_type_get_extended

클라이언트 HTTP 요청에서 파일 형식 추출

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a>Description

이 서비스는 *http_type_string* 버퍼에서 HTTP 요청 유형을 추출하고, 입력 버퍼 *name*(일반적으로 URL)의 *string_size* 에서 길이를 추출합니다. MIME 맵이 없으면 기본적으로 "텍스트/일반" 형식으로 설정됩니다. MIME 맵이 있으면 추출된 형식을 HTTP 서버 기본 MIME 맵과 비교하여 매칭합니다. NetX 웹 HTTP 서버의 기본 MIME 맵은 다음과 같습니다.

- html text/html
- htm text/html
- txt text/plain
- gif image/gif
- jpg image/jpeg
- ico image/x-icon

제공할 경우 사용자 정의 추가 MIME 맵 세트도 검색합니다. 사용자 정의 맵에 대한 자세한 내용은 *nx_web_http_server_mime_maps_addtional_set()* 를 참조하세요.

이 서비스는 *nx_web_http_server_type_get()* 을 대체합니다. 이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터
- **name** 검색할 버퍼에 대한 포인터
- **name_length** 이름 길이
- **http_type_string** 추출된 HTML 형식 문자열에 대한 포인터
- **http_type_string_max_size** http_type_string 버퍼의 크기
- **string_size** 추출된 HTML 형식 문자열 길이를 반환하는

포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 형식을 추출했습니다.
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) 기본 "텍스트/일반" 형식이 반환되었습니다.

### <a name="allowed-from"></a>허용 위치

애플리케이션

### <a name="example"></a>예제

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a>nx_web_http_server_digest_authenticate_notify_set

다이제스트 인증 콜백 함수 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a>Description

이 서비스는 다이제스트 인증을 수행할 때 호출되는 콜백을 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터
- **digest_authenticate_callback** 다이제스트 인증 콜백에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력
- NX_NOT_SUPPORTED (0x4B) 다이제스트 인증을 사용하도록 설정되지 않음

### <a name="allowed-from"></a>허용 위치

애플리케이션

### <a name="example"></a>예제

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a>nx_web_http_server_authenticate_check_set

다이제스트 인증 콜백 함수 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a>Description

이 서비스는 인증 검사를 수행할 때 호출되는 콜백을 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터
- **authenticate_check_externded** 인증 검사 콜백에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함
- NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

애플리케이션

### <a name="example"></a>예제

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
