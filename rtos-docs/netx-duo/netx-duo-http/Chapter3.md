---
title: 3장 - Azure RTOS NetX Duo HTTP 서비스 설명
description: 이 장에는 동일한 서비스에 해당하는 ‘NetX’(IPv4만 해당)가 함께 쌍을 이루는 경우를 제외하고 모든 Azure RTOS NetX Duo HTTP 서비스(아래 참조)에 대한 설명이 알파벳 순서로 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 09add7bb20a8e104ba41583c0dbf4d574b8e6c9e6b3a3deed71d8fa8c8942ce2
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796483"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a>3장 - Azure RTOS NetX Duo HTTP 서비스 설명

이 장에는 동일한 서비스에 해당하는 ‘NetX’(IPv4만 해당)가 함께 쌍을 이루는 경우를 제외하고 모든 Azure RTOS NetX Duo HTTP 서비스(아래 참조)에 대한 설명이 알파벳 순서로 포함되어 있습니다.

다음 API 설명의 “반환 값” 섹션에서 BOLD로 표시된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의에 영향을 받지 않으며, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

**HTTP 클라이언트 서비스:**

- **nx_http_client_create** *HTTP 클라이언트 인스턴스를 만듭니다.*
- **nx_http_client_delete** *HTTP 클라이언트 인스턴스를 삭제합니다.*
- **nx_http_client_get_start** *HTTP GET 요청을 시작합니다(IPv4만 해당).*
- **nx_http_client_get_start_extended** *HTTP GET 요청을 시작합니다(IPv4만 해당).*
- **nxd_http_client_get_start** *HTTP GET 요청을 시작합니다(IPv4 또는 IPv6).*
- **nxd_http_client_get_start_extended** *HTTP GET 요청을 시작합니다(IPv4 또는 IPv6).*
- **nx_http_client_get_packet** *다음 리소스 데이터 패킷을 가져옵니다.*
- **nx_http_client_put_start** *HTTP PUT 요청을 시작합니다(IPv4만 해당).*
- **nx_http_client_put_start_extended** *HTTP PUT 요청을 시작합니다(IPv4만 해당).*
- **nxd_http_client_put_start** *HTTP PUT 요청을 시작합니다(IPv4 또는 IPv6).*
- **nxd_http_client_put_start_extended** *HTTP PUT 요청을 시작합니다(IPv4 또는 IPv6).*
- **nx_http_client_put_packet** *다음 리소스 데이터 패킷을 전송합니다.*
- **nx_http_client_set_connect_port** *HTTP 서버에 연결하도록 포트를 변경합니다.*

**HTTP 서버 서비스:**

- **nx_http_server_cache_info_callback_set** *지정된 URL의 기간 및 마지막 수정 날짜를 검색하도록 콜백을 설정합니다.*
- **nx_http_server_callback_data_send** *콜백 함수에서 HTTP 데이터를 보냅니다.*
- **nx_http_server_callback_generate_response_header** *콜백 함수에 응답 헤더를 만듭니다.*
- **nx_http_server_callback_generate_response_header_extended** *콜백 함수에 응답 헤더를 만듭니다.*
- **nx_http_server_callback_packet_send** *HTTP 콜백에서 HTTP 패킷을 보냅니다.*
- **nx_http_server_callback_response_send** *콜백 함수에서 응답을 보냅니다.*
- **nx_http_server_callback_response_send_extended** *콜백 함수에서 응답을 보냅니다.*
- **nx_http_server_content_get** *요청에서 콘텐츠를 가져옵니다.*
- **nx_http_server_content_get_extended** *요청에서 콘텐츠를 가져옵니다. 비어 있는(콘텐츠 길이가 0인) 요청을 지원합니다.*
- **nx_http_server_content_length_get** *요청에서 콘텐츠 길이를 가져옵니다.*
- **nx_http_server_content_length_get_extended** *요청에서 콘텐츠 길이를 가져옵니다. 비어 있는(콘텐츠 길이가 0인) 요청을 지원합니다.*
- **nx_http_server_create** *HTTP 서버 인스턴스를 만듭니다.*
- **nx_http_server_delete** *HTTP 서버 인스턴스를 삭제합니다.*
- **nx_http_server_get_entity_content** *URL에서 엔터티의 크기 및 위치를 반환합니다.*
- **nx_http_server_get_entity_header** *URL 엔터티 헤더를 지정된 버퍼로 추출합니다.*
- **nx_http_server_gmt_callback_set** *GMT 날짜 및 시간을 검색하도록 콜백을 설정합니다.*
- **nx_http_server_invalid_userpassword_notify_set** *클라이언트 요청에서 잘못된 사용자 이름 및 암호를 받은 경우에 대한 콜백을 설정합니다.*
- **nx_http_server_mime_maps_additional_set** *HTML에 대한 추가 MIME 맵을 정의합니다.*
- **nx_http_server_packet_content_find** *HTTP 헤더에서 콘텐츠 길이를 추출하고 콘텐츠 데이터 시작 부분으로 포인터를 설정합니다.*
- **nx_http_server_packet_get** *클라이언트 패킷을 직접 수신합니다.*
- **nx_http_server_param_get** *요청에서 매개 변수를 가져옵니다.*
- **nx_http_server_query_get** *요청에서 쿼리를 가져옵니다.*
- **nx_http_server_start** *HTTP 서버를 시작합니다.*
- **nx_http_server_stop** *HTTP 서버를 중지합니다.*
- **nx_http_server_type_get (deprecated)** *헤더에서 HTTP 형식(예: 텍스트/일반)을 추출합니다.*
- **nx_http_server_type_get_extended** *헤더에서 HTTP 형식(예: 텍스트/일반)을 추출합니다.*
- **nx_http_server_digest_authenticate_notify_set** *다이제스트 인증 콜백 함수를 설정합니다.*
- **nx_http_server_authentication_check_set** *인증 확인 콜백 함수를 설정합니다.*

## <a name="nx_http_client_create"></a>nx_http_client_create

PPPoE 클라이언트 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에 HTTP 클라이언트 인스턴스를 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
 - **client_name** HTTP 클라이언트 인스턴스의 이름입니다.
 - **ip_ptr** IP 인스턴스에 대한 포인터입니다.
 - **pool_ptr** 기본 패킷 풀에 대한 포인터입니다. 이 풀의 패킷에는 전체 응답 헤더를 처리할 수 있을 만큼 큰 페이로드가 있어야 합니다. 이것은 *nx_http.h* 의 NX_HTTP_CLIENT_MIN_PACKET_SIZE에 의해 정의됩니다.
 - **window_size** 클라이언트의 TCP 소켓 수신 창의 크기입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 만듦
 - NX_PTR_ERROR (0x07) 잘못된 HTTP, ip_ptr 또는 패킷 풀 포인터입니다.
 - NX_HTTP_POOL_ERROR (0xE9) 패킷 풀의 잘못된 페이로드 크기입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a>nx_http_client_delete

HTTP 클라이언트 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 삭제함
 - NX_PTR_ERROR (0x07) 잘못된 HTTP 포인터입니다.
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a>nx_http_client_get_start

IPv4를 통해 HTTP GET 요청을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 생성된 HTTP 클라이언트 인스턴스에서 “리소스” 포인터로 지정된 리소스를 사용해서 GET 요청을 만들고 전송하려고 시도합니다. 이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_http_client_get_packet* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.

> [!NOTE]
> 리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 GET 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.

이 서비스는 IPv4 네트워크에서만 작동합니다. IPv6 네트워크 연결이 필요한 애플리케이션의 경우 *nxd_http_client_get_start_extended()* 를 사용해야 합니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_http_client_get_start_extended()* 또는 *nxd_http_client_get_start_extended()* 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
 - **ip_address** HTTP 서버의 IP 주소
 - **resource** 요청된 리소스의 URL 문자열에 대한 포인터
 - **input_ptr** GET 요청의 추가 데이터에 대한 포인터입니다. 선택 사항입니다. 유효한 경우 지정된 입력이 메시지의 콘텐츠 영역에 배치되고 GET 작업 대신 POST가 사용됩니다.
 - **input_size** ```input_ptr```에서 가리키는 선택적 추가 입력의 바이트 수입니다.
 - **username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.
 - **password** 인증을 위한 선택적 암호에 대한 포인터
 - **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.

    - **시간 제한 값** (0x00000001~0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

    숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 전송했습니다. 시작 메시지를 가져옵니다.
 - **NX_HTTP_ERROR** (0xE0) 내부 HTTP 클라이언트 오류
 - **NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음
 - **NX_HTTP_FAILED** (0xE2) HTTP 서버와 통신하는 중 HTTP 클라이언트 오류가 발생했습니다.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 및/또는 암호
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                           NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                            POST_MESSAGE, sizeof(POST_MESSAGE),
                            “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_start_extended"></a>nx_http_client_get_start_extended

IPv4를 통해 HTTP GET 요청을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 생성된 HTTP 클라이언트 인스턴스에서 “리소스” 포인터로 지정된 리소스를 사용해서 GET 요청을 만들고 전송하려고 시도합니다. 이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_http_client_get_packet* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.

> [!NOTE]
> 리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 GET 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.

이 서비스는 IPv4 네트워크에서만 작동합니다. IPv6 네트워크 연결이 필요한 애플리케이션의 경우 *nxd_http_client_get_start_extended()* 를 사용해야 합니다.

이 서비스는 *nx_http_client_get_start()* 를 대체합니다. 호출자가 리소스, 사용자 이름 및 암호의 길이를 지정해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
 - **ip_address** HTTP 서버의 IP 주소입니다.
 - **resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.
 - **resource_length** 요청된 리소스에 대한 URL 문자열의 길이입니다.
 - **input_ptr** GET 요청의 추가 데이터에 대한 포인터입니다. 선택 사항입니다. 유효한 경우 지정된 입력이 메시지의 콘텐츠 영역에 배치되고 GET 작업 대신 POST가 사용됩니다.
 - **input_size** ```input_ptr```에서 가리키는 선택적 추가 입력의 바이트 수입니다.
 - **username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.
 - **username_length** 인증을 위한 선택적 사용자 이름의 길이입니다.
 - **password** 인증을 위한 선택적 암호에 대한 포인터
 - **password_length** 인증을 위한 선택적 암호의 길이입니다.
 - **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값** (0x00000001~0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

    숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 전송했습니다. GET 시작 메시지
 - **NX_HTTP_ERROR** (0xE0) 내부 HTTP 클라이언트 오류
 - **NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음
 - **NX_HTTP_FAILED** (0xE2) HTTP 서버와 통신하는 중 HTTP 클라이언트 오류가 발생했습니다.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 및/또는 암호
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                     9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                     “myname”, 6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nxd_http_client_get_start"></a>nxd_http_client_get_start

HTTP GET 요청 보내기(IPv4 또는 IPv6)

### <a name="prototype"></a>프로토타입

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 생성된 HTTP 클라이언트 인스턴스에서 “리소스” 포인터로 지정된 리소스를 사용해서 GET 요청을 만들고 전송하려고 시도합니다. IPv4 또는 IPv6 네트워크에 연결하기 위해 사용될 수 있습니다. 이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_http_client_get_packet* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.

> [!NOTE]
>리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 GET 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nxd_http_client_get_start_extended()* 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.
 - **Server_ip** HTTP 서버의 IP 주소입니다.
 - **resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.
 - **input_ptr** GET 요청의 추가 데이터에 대한 포인터입니다. 선택 사항입니다. 유효한 경우 지정된 입력이 메시지의 콘텐츠 영역에 배치되고 GET 작업 대신 POST가 사용됩니다.
 - **input_size** ```input_ptr```에서 가리키는 선택적 추가 입력의 바이트 수입니다.
 - **username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.
 - **username_length** 인증을 위한 선택적 사용자 이름의 길이입니다.
 - **password** 인증을 위한 선택적 암호에 대한 포인터
 - **password_length** 인증을 위한 선택적 암호의 길이입니다.
 - **wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값** (0x00000001~0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

    숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) GET 요청을 성공적으로 보냈습니다.
 - **NX_HTTP_PASSWORD_TOO_LONG** (0xF0) 암호가 버퍼 크기를 초과합니다.
 - **NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음
 - **NX_HTTP_FAILED** (0xE2) 잘못된 패킷 매개 변수입니다.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 또는 암호입니다.
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start(&my_client, server_ip_address, “/TEST.HTM”,
NX_NULL, 0, “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nxd_http_client_get_start_extended"></a>nxd_http_client_get_start_extended

HTTP GET 요청 보내기(IPv4 또는 IPv6)

### <a name="prototype"></a>프로토타입

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 생성된 HTTP 클라이언트 인스턴스에서 “리소스” 포인터로 지정된 리소스를 사용해서 GET 요청을 만들고 전송하려고 시도합니다. IPv4 또는 IPv6 네트워크에 연결하기 위해 사용될 수 있습니다. 이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_http_client_get_packet* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.

> [!NOTE]
> 리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 GET 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.

이 서비스는 *nxd_http_client_get_start()* 를 대체합니다. 호출자가 리소스, 사용자 이름 및 암호의 길이를 지정해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.
 - **Server_ip** HTTP 서버의 IP 주소입니다.
 - **resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.
 - **resource_length** 요청된 리소스에 대한 URL 문자열의 길이입니다.
 - **input_ptr** GET 요청의 추가 데이터에 대한 포인터입니다. 선택 사항입니다. 유효한 경우 지정된 입력이 메시지의 콘텐츠 영역에 배치되고 GET 작업 대신 POST가 사용됩니다.
 - **input_size** ```input_ptr```에서 가리키는 선택적 추가 입력의 바이트 수입니다.
 - **username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.
 - **username_length** 인증을 위한 선택적 사용자 이름의 길이입니다.
 - **password** 인증을 위한 선택적 암호에 대한 포인터
 - **password_length** 인증을 위한 선택적 암호의 길이입니다.
 - **wait_option** HTTP 클라이언트 GET을 처리하기 위해 서비스가 내부적으로 기다려야 하는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값** (0x00000001~0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

    숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) GET 요청을 성공적으로 보냈습니다.
 - **NX_HTTP_PASSWORD_TOO_LONG** (0xF0) 암호가 버퍼 크기를 초과합니다.
 - **NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음
 - **NX_HTTP_FAILED** (0xE2) 잘못된 패킷 매개 변수입니다.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 또는 암호입니다.
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start_extended(&my_client, server_ip_address,
                                             “/TEST.HTM”, 9, NX_NULL, 0, “myname”,
        6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_http_client_get_packet"></a>nx_http_client_get_packet

다음 리소스 데이터 패킷 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전 *nx_http_client_get_start* 호출에서 요청한 리소스 콘텐츠의 다음 패킷을 검색합니다. NX_HTTP_GET_DONE의 반환 상태를 받을 때까지 이 루틴에 대한 연속 호출을 수행해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
 - **packet_ptr** 부분 리소스 콘텐츠가 포함된 패킷 포인터의 대상
 - **wait_option** 서비스에서 HTTP 클라이언트 GET 패킷을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값** (0x00000001~0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

    숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 클라이언트 GET 패킷을 성공적으로 수행합니다.
 - **NX_HTTP_GET_DONE** (0xEC) HTTP 클라이언트 GET 패킷이 완료됨
 - **NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 GET 모드가 아님
 - **NX_HTTP_BAD_PACKET_LENGTH** (0xED) 잘못된 패킷 길이
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a>nx_http_client_put_start

IPv4를 통해 HTTP PUT 요청을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 리소스가 포함된 PUT 요청을 제공된 IP 주소의 HTTP 서버에 보내려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_http_client_put_packet()* 루틴을 연속적으로 호출하여 실제로 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

> [!NOTE]
> 리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 PUT 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_http_client_put_start_extended()* 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
 - **ip_address** HTTP 서버의 IP 주소
 - **resource** 요청된 리소스의 URL 문자열에 대한 포인터
 - **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
 - **password** 인증을 위한 선택적 암호에 대한 포인터
 - **total_bytes** 전송 중인 리소스의 총 바이트 수입니다. *nx_http_client_put_packet* 에 대한 후속 호출을 통해 전송된 모든 패킷의 결합된 길이는 이 값과 같아야 합니다.
 - **wait_option** 서비스에서 HTTP 클라이언트 PUT 시작을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값** (0x00000001~0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

    숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄
 - **NX_HTTP_USERNAME_TOO_LONG** (0xF1) 사용자 이름이 버퍼에 비해 너무 큼
 - **NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a>nx_http_client_put_start_extended

IPv4를 통해 HTTP PUT 요청을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 리소스가 포함된 PUT 요청을 제공된 IP 주소의 HTTP 서버에 보내려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_http_client_put_packet()* 루틴을 연속적으로 호출하여 실제로 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

> [!NOTE]
> 리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 PUT 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.

이 서비스는 *nx_http_client_put_start()* 를 대체합니다. 호출자가 리소스, 사용자 이름 및 암호의 길이를 지정해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
 - **ip_address** HTTP 서버의 IP 주소
 - **resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.
 - **resource_length** 서버에 보내는 리소스에 대한 URL 문자열의 길이입니다.
 - **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
 - **username_length** 인증을 위한 선택적 사용자 이름의 길이입니다.
 - **password** 인증을 위한 선택적 암호에 대한 포인터
 - **password_length** 인증을 위한 선택적 암호의 길이입니다.
 - **total_bytes** 전송 중인 리소스의 총 바이트 수입니다. *nx_http_client_put_packet* 에 대한 후속 호출을 통해 전송된 모든 패킷의 결합된 길이는 이 값과 같아야 합니다.
 - **wait_option** 서비스에서 HTTP 클라이언트 PUT 시작을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값** (0x00000001~0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

    숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄
 - **NX_HTTP_USERNAME_TOO_LONG** (0xF1) 사용자 이름이 버퍼에 비해 너무 큼
 - **NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a>nxd_http_client_put_start

HTTP PUT 요청을 시작합니다(IPv4 또는 IPv6).

### <a name="prototype"></a>프로토타입

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 IPv6를 통해 제공된 IP 주소에서 HTTP 서버의 지정된 리소스를 PUT(전송)하려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_http_client_put_packet()* 루틴을 연속적으로 호출하여 실제로 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

> [!NOTE]
> 리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 PUT 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_http_client_put_start_extended()* 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.
 - **server_ip** HTTP 서버의 IP 주소입니다.
 - **resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터입니다.
 - **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
 - **password** 인증을 위한 선택적 암호에 대한 포인터
 - **total_bytes** 전송 중인 리소스의 총 바이트 수입니다. *nx_http_client_put_packet* 에 대한 후속 호출을 통해 전송된 모든 패킷의 결합된 길이는 이 값과 같아야 합니다.
 - **wait_option** 서비스에서 HTTP 클라이언트 PUT 시작을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값** (0x00000001~0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

    숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 클라이언트 PUT 요청을 성공적으로 보냈습니다.
 - **NX_HTTP_ERROR** (0xE0) HTTP 클라이언트 내부 오류입니다.
 - **NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음
 - **NX_HTTP_FAILED** (0xE2) HTTP 서버와 통신하는 중 HTTP 클라이언트 오류가 발생했습니다.
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start(&my_client, &server_ip_address,
                                    "/client_test.htm", "name", "password", 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nxd_http_client_put_start_extended"></a>nxd_http_client_put_start_extended

HTTP PUT 요청을 시작합니다(IPv4 또는 IPv6).

### <a name="prototype"></a>프로토타입

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 IPv6를 통해 제공된 IP 주소에서 HTTP 서버의 지정된 리소스를 PUT(전송)하려고 시도합니다. 이 루틴이 성공하면 애플리케이션 코드에서 *nx_http_client_put_packet()* 루틴을 연속적으로 호출하여 실제로 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.

> [!NOTE]
> 리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 PUT 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.

이 서비스는 *nxd_http_client_put_start()* 를 대체합니다. 호출자가 리소스, 사용자 이름 및 암호의 길이를 지정해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
 - **ip_address** HTTP 서버의 IP 주소
 - **resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.
 - **resource_length** 서버에 보내는 리소스에 대한 URL 문자열의 길이입니다.
 - **username** 인증을 위한 선택적 사용자 이름에 대한 포인터
 - **username_length** 인증을 위한 선택적 사용자 이름의 길이입니다.
 - **password** 인증을 위한 선택적 암호에 대한 포인터
 - **password_length** 인증을 위한 선택적 암호의 길이입니다.
 - **total_bytes** 전송 중인 리소스의 총 바이트 수입니다. *nx_http_client_put_packet* 에 대한 후속 호출을 통해 전송된 모든 패킷의 결합된 길이는 이 값과 같아야 합니다.
 - **wait_option** 서비스에서 HTTP 클라이언트 PUT 시작을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값** (0x00000001~0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

    숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 클라이언트 PUT 요청을 성공적으로 보냈습니다.
 - **NX_HTTP_ERROR** (0xE0) HTTP 클라이언트 내부 오류입니다.
 - **NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음
 - NX_HTTP_FAILED (0xE2) HTTP 서버와 통신하는 중 HTTP 클라이언트 오류가 발생했습니다.
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start_extended(&my_client, &server_ip_address,
                                            "/client_test.htm", 16, "name", 4, "password", 8, 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nx_http_client_put_packet"></a>nx_http_client_put_packet

다음 리소스 데이터 패킷 보내기

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 리소스 콘텐츠의 다음 패킷을 HTTP 서버에 보내려고 시도합니다.

> [!NOTE]
> 이 루틴은 전송된 패킷의 결합된 길이가 이전 *nx_http_client_put_start()* 호출에 지정된 "total_bytes"와 같아질 때까지 반복적으로 호출되어야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
 - **packet_ptr** HTTP 서버에 보내는 리소스의 다음 콘텐츠에 대한 포인터
 - **wait_option** 서비스에서 HTTP 클라이언트 PUT 패킷을 처리하기 위해 내부적으로 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **시간 제한 값** (0x00000001~0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

    숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 클라이언트 패킷을 성공적으로 보냄
 - **NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음
 - **NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) 서버 오류 코드가 수신되었습니다.
 - **NX_HTTP_BAD_PACKET_LENGTH** (0xED) 잘못된 패킷 길이
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 및/또는 암호
 - **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) PUT이 완료되기 전에 서버에서 응답함
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_INVALID_PACKET (0x12) 패킷이 TCP 헤더에 비해 너무 작음
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a>nx_http_client_set_connect_port

서버에 대한 연결 포트를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a>Description

이 서비스는 런타임에 지정된 포트에서 HTTP 서버에 연결할 때 연결 포트를 변경합니다. 그렇지 않으면 연결 포트의 기본값은 80입니다. 이는 *nx_http_client_get_start()* 및 *nx_http_client_put_start()* 전에 호출해야 합니다(예: HTTP 클라이언트에서 서버에 연결하는 경우).

### <a name="input-parameters"></a>입력 매개 변수

 - **client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터
 - **port** 서버에 연결하기 위한 포트입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 포트를 성공적으로 변경했습니다.
 - NX_INVALID_PORT (0x46) 포트가 최댓값(0xFFFF)을 초과하거나 0입니다.
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드, 초기화

### <a name="example"></a>예제

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a>nx_http_server_cache_info_callback_set

URL 최대 기간 및 날짜를 검색하는 콜백 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
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
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

초기화

### <a name="example"></a>예제

```c
NX_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
                           NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP  
   server is set by nx_http_server_start(), set the cache info callback: */

status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);


/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a>nx_http_server_callback_data_send

콜백 함수에서 데이터를 보냅니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션의 콜백 루틴에서 제공된 패킷의 데이터를 보냅니다. 일반적으로 GET/POST 요청과 연결된 동적 데이터를 보내는 데 사용됩니다.

> [!NOTE]
> 이 함수를 사용할 경우 콜백 루틴에서 전체 응답을 적절한 형식으로 보내야 합니다. 또한 콜백 루틴에서 NX_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버 제어 블록에 대한 포인터
 - **data_ptr** 보내는 데이터에 대한 포인터입니다.
 - **data_length** 보낼 바이트 수입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 서버 데이터를 성공적으로 보냄
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
  CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
                (strcmp(resource, "/test.htm") == 0))
    {

        /* Found it, override the GET processing by sending the resource
    contents directly. */

        nx_http_server_callback_data_send(server_ptr,
    "HTTP/1.0 200 \r\nContent-Length:
    103\r\nContent-Type: text/html\r\n\r\n",
    63);

        nx_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX
    HTTP Test </TITLE></HEAD>\r\n
    <BODY>\r\n<H1>NetX Test Page
    </H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a>nx_http_server_callback_generate_response_header

콜백 함수에서 응답 헤더 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Description

이 서비스는 HTTP 서버에서 클라이언트 GET, PUT 및 DELETE 요청에 응답할 때 *_nx_http_server_generate_response_header* 내부 함수를 호출합니다. HTTP 서버 애플리케이션에서 클라이언트에 대한 응답을 설계하는 경우 HTTP 서버 콜백 함수에서 사용하기 위한 것입니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nxd_http_server_callback_generate_response_header_extended()* 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버 제어 블록에 대한 포인터
 - **packet_pptr** 메시지에 할당된 패킷 포인터에 대한 포인터입니다.
 - **status_code** 리소스 상태를 표시합니다. 예제:
    - **NX_HTTP_STATUS_OK**
    - **NX_HTTP_STATUS_MODIFIED**
    - **NX_HTTP_STATUS_INTERNAL_ERROR**
 - **content_length** 콘텐츠의 크기입니다(바이트).
 - **content_type** HTTP 형식입니다(예: "텍스트/일반").
 - **additional_header** 추가 헤더 텍스트에 대한 포인터

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 헤더를 성공적으로 만듦
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
            Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
                  &resp_packet_ptr, NX_HTTP_STATUS_OK,
                  length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a>nx_http_server_callback_generate_response_header_extended

콜백 함수에서 응답 헤더 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_callback_generate_response_header_extended(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT status_code_length,
                        UINT content_length,
                        CHAR *content_type, UINT content_type_length,
                        CHAR *additional_header,
                        UINT additional_header_length);
```

### <a name="description"></a>Description

이 서비스는 HTTP 서버에서 클라이언트 GET, PUT 및 DELETE 요청에 응답할 때 *_nx_http_server_generate_response_header()* 내부 함수를 호출합니다. HTTP 서버 애플리케이션에서 클라이언트에 대한 응답을 설계하는 경우 HTTP 서버 콜백 함수에서 사용하기 위한 것입니다.

이 서비스는 *nx_http_server_callback_generate_response_header()* 를 대체합니다. 이 버전은 추가 길이 정보를 콜백 함수에 제공합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버 제어 블록에 대한 포인터
 - **packet_pptr** 메시지에 할당된 패킷 포인터에 대한 포인터입니다.
 - **status_code** 리소스 상태를 표시합니다. 예제:
    - **NX_HTTP_STATUS_OK**
    - **NX_HTTP_STATUS_MODIFIED**
    - **NX_HTTP_STATUS_INTERNAL_ERROR**
 - **status_code** 상태 코드의 길이입니다.
 - **content_length** 콘텐츠의 크기입니다(바이트).
 - **content_type** HTTP 형식입니다(예: "텍스트/일반").
 - **content_type_length** HTTP 형식의 길이입니다.
 - **additional_header** 추가 헤더 텍스트에 대한 포인터
 - **additional_header_length** 추가 헤더 텍스트의 길이입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 헤더를 성공적으로 만듦
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
     Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header_extended(
                             http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
              sizeof(NX_HTTP_STATUS_OK) - 1, length,
              temp_string, string_length, NX_NULL, 0);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_packet_send"></a>nx_http_server_callback_packet_send

콜백 함수에서 HTTP 패킷을 보냅니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

이 서비스는 HTTP 콜백에서 전체 HTTP 서버 응답을 보냅니다. HTTP 서버는 NX_HTTP_SERVER _TIMEOUT_SEND를 사용하여 패킷을 보냅니다. HTTP 헤더와 데이터는 패킷에 추가해야 합니다. 반환 상태에서 오류가 표시되는 경우 HTTP 애플리케이션에서 패킷을 해제해야 합니다.

콜백에서 NX_HTTP_CALLBACK_COMPLETED를 반환해야 합니다.

자세한 예제는 *nx_http_server_callback_generate_response_header()* 를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.
 - **packet_ptr** 전송할 패킷에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 서버 패킷을 성공적으로 보냈습니다.
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* The packet is appended with HTTP header and data and is ready to send to the
   Client directly. */

   status = nx_http_server_callback_response_send(server_ptr, packet_ptr);

   if (status != NX_SUCCESS)
   {

    nx_packet_release(packet_ptr);
   }

    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a>nx_http_server_callback_response_send

콜백 함수에서 응답을 보냅니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션의 콜백 루틴에서 제공된 응답 정보를 보냅니다. 일반적으로 GET/POST 요청과 연결된 사용자 지정 응답을 보내는 데 사용됩니다.

> [!NOTE]
> 이 함수를 사용하는 경우 콜백 루틴에서 NX_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nxd_http_server_callback_response_send_extended()* 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버 제어 블록에 대한 포인터
 - **header** 응답 헤더 문자열에 대한 포인터입니다.
 - **information** 정보 문자열에 대한 포인터
 - **additional_info** 추가 정보 문자열에 대한 포인터

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 서버 응답을 성공적으로 보냄

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send(server_ptr,
                      "HTTP/1.0 404 ",
                      "NetX HTTP Server unable to find  
                       file: ", resource);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a>nx_http_server_callback_response_send_extended

콜백 함수에서 응답을 보냅니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_callback_response_send_extended(
                                          NX_HTTP_SERVER *server_ptr,
                                          CHAR *header,
                                          UINT header_length,
                                          CHAR *information,
                                          UINT information_length,
                                          CHAR *additional_info,
                                          UINT additional_info_length);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션의 콜백 루틴에서 제공된 응답 정보를 보냅니다. 일반적으로 GET/POST 요청과 연결된 사용자 지정 응답을 보내는 데 사용됩니다.

> [!NOTE]
> 이 함수를 사용하는 경우 콜백 루틴에서 NX_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.

이 서비스는 *nx_http_server_callback_response_send()* 를 대체합니다. 이 버전은 추가 길이 정보를 인수로 가져옵니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버 제어 블록에 대한 포인터
 - **header** 응답 헤더 문자열에 대한 포인터입니다.
 - **header_length** 응답 헤더 문자열의 길이입니다.
 - **information** 정보 문자열에 대한 포인터
 - **information_length** 정보 문자열의 길이입니다.
 - **additional_info** 추가 정보 문자열에 대한 포인터
 - **additional_info_length** 추가 정보 문자열의 길이입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 서버 응답을 성공적으로 보냄

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send_extended(
                                             server_ptr,
                      "HTTP/1.0 404 ", 12,
                      "NetX HTTP Server unable to find  
                       file: ", 38, resource, 9);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a>nx_http_server_content_get

요청에서 콘텐츠 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a>Description

이 서비스는 POST 또는 PUT HTTP 클라이언트 요청에서 지정된 양의 콘텐츠를 검색하려고 시도합니다. HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create*)에서 호출해야 합니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_http_server_content_get_extended()* 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버 제어 블록에 대한 포인터
 - **packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다. 이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.
 - **byte_offset** 콘텐츠 영역으로 오프셋할 바이트 수입니다.
 - **destination_ptr** 콘텐츠의 대상 영역에 대한 포인터입니다.
 - **destination_size** 대상 영역에서 사용 가능한 최대 바이트 수입니다.
 - **actual_size** 복사된 콘텐츠의 실제 크기로 설정되는 대상 변수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 서버 콘텐츠를 성공적으로 가져옴
 - **NX_HTTP_ERROR** (0xE0) HTTP 서버 내부 오류
 - **NX_HTTP_DATA_END** (0xE7) 요청 콘텐츠의 끝
 - **NX_HTTP_TIMEOUT** (0xE1) 콘텐츠의 다음 패킷을 가져오는 중에 HTTP 서버 시간이 초과됨
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a>nx_http_server_content_get_extended

요청에서 콘텐츠 가져오기/길이가 0인 콘텐츠 길이 지원

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a>Description

이 서비스는 *nx_http_server_content_get();* 과 거의 동일하며, POST 또는 PUT HTTP 클라이언트 요청에서 지정된 양의 콘텐츠를 검색하려고 시도합니다. 그러나 콘텐츠 길이 값이 0인 요청('빈 요청')을 유효한 요청으로 처리합니다. HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create()* )에서 호출해야 합니다.

이 서비스는 *nx_http_server_content_get()* 을 대체합니다. 이 버전을 사용하려면 호출자가 추가 길이 정보를 제공해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버 제어 블록에 대한 포인터
 - **packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다. 이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.
 - **byte_offset** 콘텐츠 영역으로 오프셋할 바이트 수입니다.
 - **destination_ptr** 콘텐츠의 대상 영역에 대한 포인터입니다.
 - **destination_size** 대상 영역에서 사용 가능한 최대 바이트 수입니다.
 - **actual_size** 복사된 콘텐츠의 실제 크기로 설정되는 대상 변수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 콘텐츠를 성공적으로 가져옴
 - **NX_HTTP_ERROR** (0xE0) HTTP 서버 내부 오류
 - **NX_HTTP_DATA_END** (0xE7) 요청 콘텐츠의 끝
 - **NX_HTTP_TIMEOUT** (0xE1) 다음 패킷을 가져오는 중에 HTTP 서버 시간이 초과됨
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력입니다.
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a>nx_http_server_content_length_get

요청에서 콘텐츠 길이를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

이 서비스는 제공된 패킷에서 HTTP 콘텐츠 길이를 검색하려고 시도합니다. HTTP 콘텐츠가 없는 경우 이 루틴은 0 값을 반환합니다. HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create()* )에서 호출해야 합니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_http_server_content_length_get_extended()* 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다. 이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.

### <a name="return-values"></a>반환 값

 - **content length** 오류 시 값 0이 반환됩니다.  

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a>nx_http_server_content_length_get_extended

요청에서 콘텐츠 길이를 가져오고 콘텐츠 길이 값(0)을 지원합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a>Description

이 서비스는 *nx_http_server_content_length_get;* 과 비슷하며, 제공된 패킷에서 HTTP 콘텐츠 길이를 검색하려고 시도합니다. 그러나 반환 값은 성공적인 완료 상태를 나타내며, 실제 길이 값은 ```content_length``` 입력 포인터에 반환됩니다. HTTP 콘텐츠가 없거나 콘텐츠 길이가 0인 경우에도 이 루틴에서 여전히 성공적인 완료 상태를 반환하며 content_length 입력 포인터가 유효한 길이(0)를 가리킵니다. HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create*)에서 호출해야 합니다.

이 서비스는 *nx_http_server_content_length_get()* 을 대체합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다. 이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.
 - **content_length** 콘텐츠 길이 필드에서 검색된 값에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 서버 콘텐츠를 성공적으로 가져왔습니다.
 - **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) 잘못된 HTTP 헤더 형식
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a>nx_http_server_create

HTTP 서버 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
      CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
      VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, CHAR **name,
            CHAR **password, CHAR **realm),
      UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Description

이 서비스는 자체 ThreadX 스레드의 컨텍스트에서 실행되는 HTTP 서버 인스턴스를 만듭니다. 선택적 *authentication_check* 및 request_notify 애플리케이션 콜백 루틴은 HTTP 서버의 기본 작업에 대한 애플리케이션 소프트웨어 제어를 제공합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **http_server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.
 - **http_server_name** HTTP 서버 이름에 대한 포인터입니다.
 - **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터
 - **media_ptr** 이전에 만든 FileX 미디어 인스턴스에 대한 포인터
 - **stack_ptr** HTTP 서버 스레드 스택 영역에 대한 포인터입니다.
 - **stack_size** HTTP 서버 스레드 스택 크기에 대한 포인터입니다.
 - **authentication_check** 애플리케이션의 인증 확인 루틴에 대한 함수 포인터입니다. 지정된 경우 이 루틴은 각 HTTP 클라이언트 요청에 대해 호출됩니다. 이 매개 변수가 NULL이면 인증이 수행되지 않습니다.
 - **request_notify** 애플리케이션의 요청 알림 루틴에 대한 함수 포인터입니다. 지정된 경우 HTTP 서버에서 요청을 처리하기 전에 이 루틴이 호출됩니다. 이렇게 하면 HTTP 클라이언트 요청을 완료하기 전에 리소스 이름을 리디렉션하거나 리소스 내의 필드를 업데이트할 수 있습니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 서버를 성공적으로 만듦
 - NX_PTR_ERROR (0x07) 잘못된 HTTP 서버, IP, 미디어, 스택 또는 패킷 풀 포인터
 - NX_HTTP_POOL_ERROR (0xE9) 풀의 패킷 페이로드가 전체 HTTP 요청을 포함할 만큼 충분히 크지 않음

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a>nx_http_server_delete

HTTP 서버 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
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

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a>nx_http_server_get_entity_content

엔터티 데이터의 위치 및 길이 검색

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a>Description

이 서비스는 받은 클라이언트 메시지의 현재 다중 파트 엔터티 내의 데이터 시작 위치 및 경계 문자열이 포함되지 않는 데이터 길이를 결정합니다. 내부적으로 HTTP 서버는 여러 엔터티가 있는 메시지에 대해 동일한 클라이언트 데이터그램에서 이 함수를 다시 호출할 수 있도록 자체 오프셋을 업데이트합니다. 패킷 포인터는 클라이언트 메시지가 다중 패킷 데이터그램인 다음 패킷으로 업데이트됩니다.

> [!NOTE]
> 이 서비스를 사용하려면 NX_HTTP_MULTIPART_ENABLE을 사용하도록 설정해야 합니다.

자세한 내용은 [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header)를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버에 대한 포인터입니다.
 - **packet_pptr** 패킷 포인터의 위치에 대한 포인터입니다. 애플리케이션에서 이 패킷을 해제하면 안 됩니다.
 - **available_offset** 패킷 선행 포인터에서 엔터티 데이터의 오프셋에 대한 포인터
 - **available_length** 엔터티 데이터의 길이에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 엔터티 콘텐츠의 크기와 위치를 성공적으로 검색함
 - **NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) HTTP 서버 내부 다중 파트 표식에 대한 콘텐츠가 이미 있습니다.
 - NX_HTTP_ERROR (0xE0) 내부 HTTP 오류
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_HTTP_SERVER my_server;

UINT        offset, length;
NX_PACKET  *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
   the entity header to determine details about the multipart data. If
   successful, it then calls this service to get the location of entity data: */

status =  nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
&length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
   entity data. */
```

## <a name="nx_http_server_get_entity_header"></a>nx_http_server_get_entity_header

엔터티 헤더의 콘텐츠 검색

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a>Description

이 서비스는 지정된 버퍼에서 엔터티 헤더를 검색합니다. 다중 엔터티 헤더가 있는 클라이언트 데이터그램에서 다음 다중 파트 엔터티를 찾도록 HTTP 서버에서 내부적으로 자체 포인터를 업데이트합니다. 패킷 포인터는 클라이언트 메시지가 다중 패킷 데이터그램인 다음 패킷으로 업데이트됩니다.

> [!NOTE]
> 이 서비스를 사용하려면 NX_HTTP_MULTIPART_ENABLE을 사용하도록 설정해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버에 대한 포인터입니다.
 - **packet_pptr** 패킷 포인터의 위치에 대한 포인터입니다. 애플리케이션에서 이 패킷을 해제하면 안 됩니다.
 - **entity_header_buffer** 엔터티 헤더를 저장하는 위치에 대한 포인터
 - **buffer_size** 입력 버퍼의 크기입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 엔터티 헤더를 성공적으로 검색함
 - **NX_HTTP_NOT_FOUND** **(0xE6)** 엔터티 헤더 필드를 찾을 수 없습니다.
 - **NX_HTTP_TIMEOUT** **(0xE1)** 다중 패킷 클라이언트 메시지에 대한 다음 패킷을 받는 시간이 만료되었습니다.
 - NX_HTTP_ERROR (0xE0) 내부 HTTP 오류
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, NX_PACKET *packet_ptr)
      {

        NX_PACKET   *sresp_packet_ptr;
        UINT        offset, length;
        NX_PACKET   *response_pkt;
        UCHAR       buffer[1440];

        /* Process multipart data. */
        if(request_type == NX_HTTP_SERVER_POST_REQUEST)
        {

       /* Get the content header. */
       while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                         sizeof(buffer)) == NX_SUCCESS)
   {

      /* Header obtained successfully. Get the content data location. */
      while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                              &length) == NX_SUCCESS)
      {
           /* Write content data to buffer. */
           nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
           buffer[length] = 0;
      }

    }

    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
                         &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
                         "Server: NetXDuo HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
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
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a>nx_http_server_gmt_callback_set

GMT 날짜 및 시간을 가져오는 콜백 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 HTTP 서버에서 GMT 날짜 및 시간을 가져오는 콜백을 설정합니다. 이 서비스는 HTTP 서버가 클라이언트에 대한 HTTP 서버 응답에 헤더를 만들 때 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버에 대한 포인터입니다.
 - **gmt_getv** GMT 콜백에 대한 포인터입니다.
 - **datev** 검색된 날짜에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함
 - NX_PTR_ERROR (0x07) 잘못된 패킷 또는 매개 변수 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the GMT
   retrieve callback: */

status =  nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
   response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a>nx_http_server_invalid_userpassword_notify_set

잘못된 사용자/암호를 처리하는 콜백을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a>Description

이 서비스는 다이제스트 또는 기본 인증을 통해 클라이언트 GET, PUT 또는 DELETE 요청에서 잘못된 사용자 이름 및 암호를 받을 때 호출되는 콜백을 설정합니다. HTTP 서버는 이전에 만들어야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버에 대한 포인터입니다.
 - **invalid_username_password_callback** 잘못된 사용자/전달 콜백에 대한 포인터입니다.
 - **resource** 클라이언트에서 지정한 리소스에 대한 포인터입니다.
 - **client_address** 클라이언트 주소에 대한 포인터입니다. IPv4 또는 IPv6일 수 있습니다.
 - **request_type** 클라이언트 요청 유형을 표시합니다. 다음과 같습니다.
    - NX_HTTP_SERVER_GET_REQUEST
    - NX_HTTP_SERVER_POST_REQUEST
    - NX_HTTP_SERVER_HEAD_REQUEST
    - NX_HTTP_SERVER_PUT_REQUEST
    - NX_HTTP_SERVER_DELETE_REQUEST

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                         NXD_ADDRESS *client_address,
                                         UINT   request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the invalid
   username password callback: */

status =  nx_http_server_gmt_callback_set(&my_server,
                                          invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
   will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a>nx_http_server_mime_maps_additional_set

HTML에 대한 추가 MIME 맵 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a>Description

이 서비스를 통해 HTTP 애플리케이션 개발자는 NetX Duo HTTP 서버에서 제공하는 기본 MIME 형식에서 추가 MIME 형식을 추가할 수 있습니다(정의된 형식 목록은 *nx_http_server_get_type* 참조).

클라이언트 요청(예: GET 요청)이 수신된 경우 HTTP 서버에서 우선적으로 추가 MIME 맵 집합을 사용하여 HTTP 헤더에서 요청된 파일 형식을 구문 분석하고, 일치하는 항목이 없는 경우 HTTP 서버의 기본 MIME 맵에서 일치 항목을 찾습니다. 일치하는 항목이 없으면 MIME 형식은 기본적으로 "텍스트/일반"으로 설정됩니다.

요청 알림 함수가 HTTP 서버에 등록된 경우 요청 알림 콜백에서 *nx_http_server_type_retrieve()* 를 호출하여 파일 형식을 구문 분석할 수 있습니다.

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

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc",      "yourtype/abc"},
    {"xyz",      "mytype/xyz"},
};

status =  nx_http_server_mime_maps_additional_set(&my_server,
                                                  &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP  
  server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a>nx_http_server_packet_content_find

콘텐츠 길이를 추출하고 데이터 시작에 대한 포인터를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a>Description

이 서비스는 HTTP 헤더에서 콘텐츠 길이를 추출합니다. 또한 제공된 패킷을 다음과 같이 업데이트합니다. 패킷 선행 포인터(쓸 패킷 버퍼의 시작 위치)가 HTTP 헤더를 방금 전달한 HTTP 콘텐츠(데이터)로 설정됩니다.

현재 패킷에서 콘텐츠의 시작 위치를 찾을 수 없는 경우 함수에서 NX_HTTP_SERVER_TIMEOUT_RECEIVE 대기 옵션을 사용하여 다음 패킷을 받을 때까지 기다립니다.

> [!NOTE]
> 이 서비스는 엔터티 헤더를 지나 선행 포인터를 수정하므로 *nx_http_server_get_entity_header* 를 호출하기 전에 호출하면 안 됩니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.
 - **packet_ptr** 업데이트된 선행 포인터를 사용하여 패킷을 반환하는 패킷 포인터에 대한 포인터입니다.
 - **content_length** 추출된 ```content_length```에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 콘텐츠 길이가 있고 패킷을 성공적으로 업데이트함
 - **NX_HTTP_TIMEOUT** (0xE1) 다음 패킷을 기다리는 시간이 만료됨
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function
registered with the HTTP server. */

UINT content_length;

status =  nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                             &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
   and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a>nx_http_server_packet_get

다음 HTTP 패킷 받기

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a>Description

이 서비스는 HTTP 서버 소켓에서 받은 다음 패킷을 반환합니다. 패킷 수신 대기 옵션은 NX_HTTP_SERVER_TIMEOUT_RECEIVE입니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.
 - **packet_ptr** 받은 패킷에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 다음 패킷을 성공적으로 받았습니다.
 - **NX_HTTP_TIMEOUT** (0xE1) 다음 패킷을 기다리는 시간이 만료됨
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a>nx_http_server_param_get

요청에서 매개 변수 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a>Description

이 서비스는 제공된 요청 패킷에서 지정된 HTTP URL 매개 변수를 검색하려고 시도합니다. 요청된 HTTP 매개 변수가 없는 경우 이 루틴에서 NX_HTTP_NOT_FOUND 상태를 반환합니다. 이 루틴은 HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create*)에서 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다. 애플리케이션에서 이 패킷을 해제하면 안 됩니다.
 - **param_number** 매개 변수 목록에서 왼쪽에서 오른쪽으로 0에서 시작하는 매개 변수의 논리적 번호입니다.
 - **param_ptr** 매개 변수를 복사하는 대상 영역
 - **max_param_size** 매개 변수 대상 영역의 최대 크기

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 서버 매개 변수를 성공적으로 가져옴
 - **NX_HTTP_NOT_FOUND** (0xE6) 지정된 매개 변수가 없음
 - **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) 요청 매개 변수가 제대로 종료되지 않음
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a>nx_http_server_query_get

요청에서 쿼리 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a>Description

이 서비스는 제공된 요청 패킷에서 지정된 HTTP URL 쿼리를 검색하려고 시도합니다. 요청된 HTTP 쿼리가 없는 경우 이 루틴에서 NX_HTTP_NOT_FOUND 상태를 반환합니다. 이 루틴은 HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create*)에서 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다. 애플리케이션에서 이 패킷을 해제하면 안 됩니다.
 - **query_number** 쿼리 목록에서 왼쪽에서 오른쪽으로 0에서 시작하는 매개 변수의 논리적 번호입니다.
 - **query_ptr** 쿼리를 복사하는 대상 영역
 - **max_query_size** 쿼리 대상 영역의 최대 크기입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) HTTP 서버 쿼리를 성공적으로 가져옴
 - **NX_HTTP_FAILED** (0xE2) 쿼리 크기가 너무 작습니다.
 - **NX_HTTP_NOT_FOUND** (0xE6) 지정된 쿼리가 없음
 - **NX_HTTP_NO_QUERY_PARSED** (0xF2) 쿼리가 클라이언트 요청에 없음
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a>nx_http_server_start

HTTP 서버 시작

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 HTTP 서버 인스턴스를 시작합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a>nx_http_server_stop

HTTP 서버 중지

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 HTTP 서버 인스턴스를 중지합니다. 이 루틴은 HTTP 서버 인스턴스를 삭제하기 전에 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 서버를 성공적으로 중지했습니다.
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력
 - NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a>nx_http_server_type_get

클라이언트 HTTP 요청에서 파일 형식 추출

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a>Description

> [!NOTE]
> 이 서비스는 더 이상 사용되지 않습니다. 사용자는 *nx_http_server_type_retrieve()* 서비스를 사용하는 것이 좋습니다.

이 서비스는 http_type_string 버퍼에서 HTTP 요청 유형을 추출하고, 입력 버퍼 이름(일반적으로 URL)에서 반환 값의 길이를 추출합니다. MIME 맵이 없는 경우 기본적으로 "텍스트/일반" 형식으로 설정됩니다. 그렇지 않으면 추출된 형식을 HTTP 서버 기본 MIME 맵과 비교하여 일치시킵니다. NetX Duo HTTP 서버의 기본 MIME 맵은 다음과 같습니다.

 - **html** text/html
 - **htm** text/html
 - **txt** text/plain
 - **gif** image/gif
 - **jpg** image/jpeg
 - **ico** image/x-icon

제공되는 경우 사용자 정의 추가 MIME 맵 집합도 검색합니다. 사용자 정의 맵에 대한 자세한 내용은 *nx_http_server_mime_maps_addtional_set()* 를 참조하세요.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 *nx_http_server_type_get_extended()* 로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.
 - **name** 검색할 버퍼에 대한 포인터입니다.
 - **http_type_string** (추출된 HTML 형식에 대한 포인터)

### <a name="return-values"></a>반환 값

 - **문자열 길이(바이트)** 0이 아닌 값은 성공입니다. 0은 오류를 나타냅니다.

### <a name="allowed-from"></a>허용 위치

애플리케이션

### <a name="example"></a>예제

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

## <a name="nx_http_server_type_get_extended"></a>nx_http_server_type_get_extended

클라이언트 HTTP 요청에서 파일 형식 추출

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a>Description

이 서비스는 *http_type_string* 버퍼에서 HTTP 요청 유형을 추출하고, 입력 버퍼 *이름*(일반적으로 URL)에서 반환 값의 길이를 추출합니다. MIME 맵이 없는 경우 기본적으로 "텍스트/일반" 형식으로 설정됩니다. 그렇지 않으면 추출된 형식을 HTTP 서버 기본 MIME 맵과 비교하여 일치시킵니다. NetX Duo HTTP 서버의 기본 MIME 맵은 다음과 같습니다.

 - **html** text/html
 - **htm** text/html
 - **txt** text/plain
 - **gif** image/gif
 - **jpg** image/jpeg
 - **ico** image/x-icon

제공되는 경우 사용자 정의 추가 MIME 맵 집합도 검색합니다. 사용자 정의 맵에 대한 자세한 내용은 *nx_http_server_mime_maps_addtional_set()* 를 참조하세요.

이 서비스는 *nx_http_server_type_get()* 을 대체합니다. 이 버전은 추가 길이 정보를 제공합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터
 - **name** 검색할 버퍼에 대한 포인터입니다.
 - **name_length** 검색할 버퍼의 길이입니다.
 - **http_type_string** (추출된 HTML 형식에 대한 포인터)
 - **http_type_string_max_size** http_type_string 버퍼의 크기입니다.

### <a name="return-values"></a>반환 값

 - **문자열 길이(바이트)** 0이 아닌 값은 성공입니다. 0은 오류를 나타냅니다.

### <a name="allowed-from"></a>허용 위치

애플리케이션

### <a name="example"></a>예제

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
                    my_server.nx_http_server_request_resource, &resource_length,
                    sizeof(my_server.nx_http_server_request_resource) - 1))
           {
               return;
           }

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get_extended(&my_server,
               my_server.nx_http_server_request_resource, resource_length,
               temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

자세한 예제는 [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header)에 대한 설명을 참조하세요.

## <a name="nx_http_server_digest_authenticate_notify_set"></a>nx_http_server_digest_authenticate_notify_set

다이제스트 인증 콜백 함수 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_digest_authenticate_notify_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                            CHAR *name_ptr,
                                            CHAR *realm_ptr,
                                            CHAR *password_ptr,
                                            CHAR *method,
                                            CHAR *authorization_uri,
                                            CHAR *authorization_nc,
                                            CHAR *authorization_cnonce
                                           ));
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

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                  CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
                                  CHAR *authorization_uri, CHAR *authorization_nc,
                                  CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the digest authenticate callback: */

status =  nx_http_server_digest_authenticate_notify_set (&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
   will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a>nx_http_server_authentication_check_set

인증 확인 콜백 함수를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_http_server_authentication_check_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*authentication_check_extended)(
                                            NX_HTTP_SERVER *server_ptr,
                                            UINT request_type,
                                            CHAR *resource,
                                            CHAR **name,
                                            UINT *name_length,
                                            CHAR **password,
                                            UINT *password_length,
                                            CHAR **realm,
                                            UINT *realm_length
                                            ));
```

### <a name="description"></a>Description

이 서비스는 인증 확인 콜백 함수를 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

 - **http_server_ptr** HTTP 서버 인스턴스에 대한 포인터
 - **authentication_check_extended** 애플리케이션의 인증 확인에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

 - **NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함
 - NX_PTR_ERROR (0x07) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

애플리케이션

### <a name="example"></a>예제

```c
static UINT  authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                           UINT request_type, CHAR *resource,
                                           CHAR **name, UINT *name_length,
                                           CHAR **password, UINT *password_length,
                                           CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
       requests and resources. */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the
   authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                         authentication_check_extended);
```
