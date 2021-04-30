---
title: 챕터 1 - Azure RTOS NetX Duo HTTP 소개
description: 이 챕터에서는 Azure RTOS NetX Duo HTTP 모듈을 소개합니다.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 442149536ac6847808fbba183b96ac78832a82c0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810788"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-http"></a>챕터 1 - Azure RTOS NetX Duo HTTP 소개

HTTP(Hypertext Transfer Protocol)는 웹에서 콘텐츠를 전송하기 위해 설계된 프로토콜입니다. HTTP는 콘텐츠 전송 기능을 수행하기 위해 신뢰할 수 있는 TCP(Transmission Control Protocol) 서비스를 사용하는 간단한 프로토콜입니다. 따라서 HTTP는 매우 안정적인 콘텐츠 전송 프로토콜입니다. HTTP는 가장 많이 사용되는 애플리케이션 프로토콜 중 하나입니다. 웹의 모든 작업에 HTTP 프로토콜이 사용됩니다. Azure RTOS NetX Duo HTTP는 IPv4 및 IPv6 네트워크를 모두 수용합니다. IPv6는 HTTP 프로토콜을 직접 변경하지 않지만, 원본 Azure RTOS NetX HTTP API에서 IPv6를 수용하려면 몇 가지 부분을 변경해야 하며, 해당 내용은 이 문서에서 설명합니다.

## <a name="http-requirements"></a>HTTP 요구 사항

NetX Duo HTTP 패키지가 올바르게 작동하기 위해서는 NetX Duo(버전 5.2 이상)가 설치되어 있어야 합니다. 또한 IP 인스턴스가 이미 생성되어 있어야 하며, 해당 IP 인스턴스에서 TCP를 사용하도록 설정해야 합니다. IPv6 호스트 애플리케이션은 IPv6 API 및/또는 DHCPv6를 사용하여 링크로컬 및 글로벌 IPv6 주소를 설정해야 합니다. **챕터 2** 에서 “작은 예제 시스템” 섹션의 데모 파일은 이를 수행하는 방법을 보여 줍니다.

NetX Duo HTTP 패키지의 HTTP 클라이언트 부분에는 추가 요구 사항이 없습니다.

NetX Duo HTTP 패키지의 HTTP 서버 부분에는 여러 추가 요구 사항이 있습니다. 먼저 모든 클라이언트 HTTP 요청을 처리하려면 TCP의 잘 알려진 포트 80에 대한 완전한 액세스 권한이 필요합니다. 또한 HTTP 서버는 File 포함된 파일 시스템에 사용하도록 설계되었습니다. FileX를 사용할 수 없으면 사용자가 사용된 FileX 부분을 자신의 고유 환경으로 이식할 수 있습니다. 이에 대해서는 이 가이드의 이후 섹션에서 설명합니다.

## <a name="http-constraints"></a>HTTP 제약 조건

NetX Duo HTTP 프로토콜은 HTTP 1.0 표준을 구현합니다. 그러나 다음과 같은 제약 조건이 있습니다.

1.  영구 연결이 지원되지 않습니다.
2.  요청 파이프라인이 지원되지 않습니다.
3.  HTTP 서버는 기본 및 MD5 다이제스트 인증을 모두 지원하지만 MD5-sess는 지원하지 않습니다. 현재 HTTP 클라이언트는 기본 인증만 지원합니다.
4.  콘텐츠 압축은 지원되지 않습니다.
5.  TRACE, OPTIONS 및 CONNECT 요청은 지원되지 않습니다.
6.  HTTP 서버 또는 클라이언트와 연결된 패킷 풀은 전체 HTTP 헤더를 저장하도록 충분히 커야 합니다.
7.  HTTP 클라이언트 서비스는 콘텐츠 전송용으로만 사용되며, 이 패키지에 제공되는 디스플레이 유틸리티는 없습니다.

## <a name="http-url-resource-names"></a>HTTP URL(리소스 이름)

HTTP 프로토콜은 웹에서 콘텐츠를 전송하도록 설계되었습니다. 요청된 콘텐츠는 URL(Universal Resource Locator)로 지정됩니다. 이는 모든 HTTP 요청의 기본 구성 요소입니다. URL은 항상 *“/”* 문자로 시작하며 일반적으로 HTTP 서버에 있는 파일을 가리킵니다. 일반적인 HTTP 파일 확장자는 다음과 같습니다.

| 확장명 | 의미 |
| --------- | ------- |
| .htm(또는 .html) | HTML(Hypertext Markup Language) |
| .txt | 일반 ASCII 텍스트 |
| .gif | 이진 GIF 이미지 |
| .xbm | 이진 Xbitmap 이미지 |

## <a name="http-client-requests"></a>HTTP 클라이언트 요청

HTTP에는 웹 콘텐츠 요청을 위한 간단한 메커니즘이 포함되어 있습니다. 기본적으로 TCP의 *잘 알려진 포트 80* 에서 연결이 성공적으로 설정된 후 클라이언트에서 실행되는 표준 HTTP 명령 세트가 있습니다. 다음은 기본 HTTP 명령 중 일부를 보여줍니다.

| HTTP 명령 | 의미 |
| ------------ | ------- |
| GET resource HTTP/1.0 | *지정된 리소스를 가져옵니다.* |
| POST resource HTTP/1.0 | *지정된 리소스를 가져오고 연결된 입력을 HTTP 서버에 전달합니다.* |
| HEAD resource HTTP/1.0 | *GET과 비슷하게 취급되지만 콘텐츠가 HTTP 서버에서 반환되지 않습니다.* |
| PUT resource HTTP/1.0 | *HTTP 서버에 리소스를 배치합니다.* |
| DELETE resource HTTP/1.0 | *서버에서 리소스를 삭제합니다.* |

이러한 ASCII 명령은 HTTP 서버로 HTTP 작업을 수행하기 위해 웹 브라우저 및 NetX HTTP 클라이언트 서비스에서 내부적으로 생성됩니다.

> [!NOTE]
> HTTP 클라이언트 애플리케이션의 기본 연결 포트는 80입니다. 그러나 nx_http_client_set_connect_port 서비스를 사용하여 런타임에 HTTP 서버에 대한 연결 포트를 변경할 수 있습니다. 이 서비스에 대한 자세한 내용은 챕터 4를 참조하세요. 이는 때때로 클라이언트 연결에 대체 포트를 사용하는 웹 서버를 수용하기 위한 것입니다.

## <a name="http-server-responses"></a>HTTP 서버 응답

HTTP 서버는 동일한 *잘 알려진 TCP 포트 80* 을 사용하여 클라이언트 명령 응답을 보냅니다. HTTP 서버는 클라이언트 명령을 처리한 후 3자릿수 숫자 상태 코드가 포함된 ASCII 응답 문자열을 반환합니다. 이 숫자 응답은 HTTP 클라이언트 소프트웨어가 작업 성공 또는 실패 여부를 확인하는 데 사용됩니다. 다음은 클라이언트 명령에 대한 여러 HTTP 서버 응답 목록입니다.

| 숫자 필드 | 의미 |
| ------------- | ------- |
| *200* | *요청이 성공했습니다.* |
| *400* |   *요청이 올바르게 구성되지 않았습니다.* |
| *401* | *권한이 없는 요청입니다. 클라이언트가 인증을 보내야 합니다.* |
| *404* | *요청에 지정된 리소스를 찾을 수 없습니다.* |
| *500* | *내부 HTTP 서버 오류입니다.* |
| *501* | *HTTP 서버에서 요청이 구현되지 않았습니다.* |
| *502* | *서비스를 사용할 수 없습니다.* |

예를 들어 “test.htm” 파일을 PUT하기 위한 클라이언트 요청에 성공하면 “HTTP/1.0 200 OK” 응답 메시지가 수신됩니다.

## <a name="http-communication"></a>HTTP 통신

앞에서 설명한 대로, HTTP 서버는 잘 알려진 TCP 포트 80을 활용하여 클라이언트 요청을 처리합니다. HTTP 클라이언트는 사용 가능한 모든 TCP 포트를 이용할 수 있습니다. HTTP 이벤트의 일반 시퀀스는 다음과 같습니다.

### <a name="http-get-request"></a>HTTP GET 요청:

1.  클라이언트가 서버 포트 80에 TCP 연결을 수행합니다.
2.  클라이언트가 “**GET resource HTTP/1.0**” 요청을 보냅니다(다른 헤더 정보 포함).
3.  서버가 추가 정보 바로 다음에 리소스 콘텐츠(있는 경우)가 포함된 “**HTTP/1.0 200 OK**” 메시지를 작성합니다.
4.  서버가 연결 해제를 수행합니다.
5.  클라이언트가 연결 해제를 수행합니다.

### <a name="http-put-request"></a>HTTP PUT 요청:

1.  클라이언트가 서버 포트 80에 TCP 연결을 수행합니다.
2.  클라이언트가 다른 헤더 정보 다음에 리소스 콘텐츠가 포함된 “**PUT resource HTTP/1.0**” 요청을 보냅니다.
3.  서버가 추가 정보 바로 다음에 리소스 콘텐츠가 포함된 “**HTTP/1.0 200 OK**” 메시지를 작성합니다.
4.  서버가 연결 해제를 수행합니다.
5.  클라이언트가 연결 해제를 수행합니다.

> [!NOTE]
>앞에서 설명한 것처럼, HTTP 클라이언트는 대체 포트를 사용하여 클라이언트에 연결하는 웹 서버에 *nx_http_client_set_connect_port* 를 사용하여 기본 연결 포트를 80에서 다른 포트로 변경할 수 있습니다.

## <a name="http-authentication"></a>HTTP 인증

HTTP 인증은 선택 사항이며 모든 웹 요청에 필요한 것은 아닙니다. 인증에는 기본 및 다이제스트라는 두 가지 종류가 있습니다. 기본 인증은 많은 프로토콜에서 사용되는 이름 및 암호 인증과 동일합니다. HTTP 기본 인증에서는 이름 및 암호가 연결되고 base64 형식으로 인코딩됩니다. 기본 인증의 주요 단점은 이름 및 암호가 요청에서 공개적으로 전송된다는 것입니다. 따라서 이름 및 암호를 쉽게 도난당할 수 있습니다. 다이제스트 인증은 이름 및 암호를 요청으로 전송하지 않는 방식으로 이 문제를 해결합니다. 대신, 이름, 암호 및 기타 정보로부터 128비트 키 또는 다이제스트를 파생하기 위한 알고리즘이 사용됩니다. NetX HTTP 서버는 표준 MD5 다이제스트 알고리즘을 지원합니다.

인증은 언제 필요한가요? 기본적으로 HTTP 서버는 요청된 리소스에 인증이 필요한지 여부를 결정합니다. 인증이 필요하고 클라이언트 요청에 적합한 인증이 포함되지 않았으면 필요한 인증 유형이 포함된 “HTTP/1.0 401 권한 없음” 응답이 클라이언트에 전송됩니다. 그러면 클라이언트는 적절한 인증으로 새 요청을 만들어야 합니다.

## <a name="http-authentication-callback"></a>HTTP 인증 콜백

앞에서 설명한 것처럼, HTTP 인증은 선택 사항이며 모든 웹 전송에 필요한 것은 아닙니다. 또한 인증은 일반적으로 리소스에 따라 달라집니다. 서버에서 일부 리소스는 액세스할 때 인증이 필요하지만, 다른 리소스는 인증이 필요하지 않습니다. NetX HTTP 서버 패키지는 애플리케이션이 *nx_http_server_create* 호출을 통해 각 HTTP 클라이언트 요청 처리를 시작할 때 호출되는 인증 콜백 루틴을 지정하도록 허용합니다.

콜백 루틴은 NetX HTTP 서버에 사용자 이름, 암호 및 리소스와 연결된 영역 문자열을 제공하고 필요한 인증 유형을 반환합니다. 리소스에 인증이 필요하지 않으면 인증 콜백이 **NX_HTTP_DONT_AUTHENTICATE** 값을 반환합니다. 그렇지 않고, 지정된 리소스에 대해 기본 인증이 필요하면 루틴이 **NX_HTTP_BASIC_AUTHENTICATE** 를 반환합니다. 그리고 마지막으로 MD5 다이제스트 인증이 필요하면 콜백 루틴이 **NX_HTTP_DIGEST_AUTHENTICATE** 를 반환합니다. HTTP 서버에서 제공되는 리소스에 인증이 필요하지 않으면 콜백이 필요하지 않고 HTTP 서버 만들기 호출에 NULL 포인터를 제공할 수 있습니다.

애플리케이션 인증 콜백 루틴의 형식은 매우 간단하며 아래에 정의되어 있습니다.

```c
UINT nx_http_server_authentication_check(NX_HTTP_SERVER *server_ptr,
                                          UINT request_type, CHAR *resource,
                                          CHAR **name, CHAR **password,
                                          CHAR **realm);
```
입력 매개 변수는 다음과 같이 정의됩니다.

| 매개 변수 | 의미 |
| --------- | --------|
| *request_type* | HTTP 클라이언트 요청을 지정합니다. 유효한 요청은 다음과 같이 정의됩니다. <br/> **NX_HTTP_SERVER_GET_REQUEST**<br/>**NX_HTTP_SERVER_POST_REQUEST**<br/>**NX_HTTP_SERVER_HEAD_REQUEST**<br/>**NX_HTTP_SERVER_PUT_REQUEST**<br/>**NX_HTTP_SERVER_DELETE_REQUEST** |
| *resource* | 요청된 특정 리소스입니다. |
| *name* | 필요한 사용자 이름에 대한 포인터의 대상입니다. |
| *password* | 필요한 암호에 대한 포인터의 대상입니다. |
| *realm* | 이 인증의 영역에 대한 포인터의 대상입니다. |

인증 루틴의 반환 값은 인증이 필요한지 여부를 지정합니다. **NX_HTTP_DONT_AUTHENTICATE** 가 인증 콜백 루틴으로 반환된 경우 ```name, password, and realm``` 포인터가 사용되지 않습니다. 그렇지 않으면 HTTP 서버 개발자가 *nxd_http_server.h* 에 정의된 **NX_HTTP_MAX_USERNAME** 및 **NX_HTTP_MAX_PASSWORD** 가 인증 콜백에 지정된 사용자 이름 및 암호에 맞게 충분히 큰지 확인해야 합니다. 이는 모두 기본적으로 20자로 설정됩니다.

## <a name="http-invalid-usernamepassword-callback"></a>HTTP 잘못된 사용자 이름/암호 콜백

HTTP 서버가 클라이언트 요청에서 잘못된 사용자 이름 및 암호 조합을 수신하면 NetX HTTP 서버에서 선택적인 잘못된 사용자 이름/암호 콜백이 호출됩니다. HTTP 서버 애플리케이션이 HTTP 서버에 콜백을 등록하면 *nx_http_server_get_process*, *nx_http_server_put_process* 또는 *nx_ttp_server_delete_process* 에서 기본 또는 다이제스트 인증이 실패할 경우 콜백이 호출됩니다.

HTTP 서버에 콜백을 등록하기 위해 NetX Duo HTTP 서버에 다음 서비스가 정의됩니다.

```c
UINT nx_http_server_invalid_userpassword_notify_set(
                   NX_HTTP_SERVER *http_server_ptr,
                   UINT *invalid_username_password_callback)
                            (CHAR *resource,
                             NXD_ADDRESS *client_nxd_address,
                             UINT request_type))
```

요청 유형은 다음과 같이 정의됩니다.
 - **NX_HTTP_SERVER_GET_REQUEST**
 - **NX_HTTP_SERVER_POST_REQUEST**
 - **NX_HTTP_SERVER_HEAD_REQUEST**
 - **NX_HTTP_SERVER_PUT_REQUEST**
 - **NX_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>HTTP GMT 날짜 헤더 삽입 콜백

NetX Duo HTTP 서버에는 응답 메시지에 날짜 헤더를 삽입하기 위한 선택적인 콜백이 있습니다. 이 콜백은 HTTP 서버가 put 또는 get 요청에 응답할 때 호출됩니다.

NetX Duo HTTP 서버에는 응답 메시지에 날짜 헤더를 삽입하기 위한 선택적인 콜백이 있습니다. 이 콜백은 HTTP 서버가 put 또는 get 요청에 응답할 때 호출됩니다.

HTTP 서버에 GMT 날짜 콜백을 등록하기 위해 NetX Duo HTTP 서버에 다음 서비스가 정의됩니다.

```c
UINT  _nx_http_server_gmt_callback_set(
                    NX_HTTP_SERVER *server_ptr,
                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date)
```

NX_HTTP_SERVER_DATE 데이터 형식은 다음과 같이 정의됩니다.

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT          nx_http_server_year;           /* Year                 */
    UCHAR           nx_http_server_month;          /* Month                */
    UCHAR           nx_http_server_day;            /* Day                  */
    UCHAR           nx_http_server_hour;           /* Hour              */
    UCHAR           nx_http_server_minute;         /* Minute               */
    UCHAR           nx_http_server_second;         /* Second               */
    UCHAR           nx_http_server_weekday;        /* Weekday              */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>HTTP 캐시 정보 가져오기 콜백

HTTP 서버에는 HTTP 애플리케이션에서 특정 리소스의 최대 기간 및 날짜를 요청하기 위한 콜백이 있습니다. 이 정보는 HTTP 서버가 클라이언트 Get 요청에 대한 응답으로 전체 페이지를 보내는지 여부를 확인하기 위해 사용됩니다. 클라이언트 요청에서 “if modified since”가 없거나 캐시 가져오기 콜백으로 반환된 “last modified” 날짜와 일치하지 않으면 전체 페이지가 전송됩니다.

콜백을 HTTP 서버에 등록하기 위해 다음 서비스가 정의됩니다.

```c
UINT  _nx_http_server_cache_info_callback_set(
                              NX_HTTP_SERVER *server_ptr,
                              UINT (*cache_info_get)
                                    (CHAR *, UINT *, NX_HTTP_SERVER_DATE *))
```

## <a name="http-multipart-support"></a>HTTP 다중 파트 지원

MIME(Multipurpose Internet Mail Extensions)은 처음에 SMTP 프로토콜을 위해 만들어졌지만 사용 범위가 HTTP로 확장되었습니다. MIME을 사용하면 동일한 메시지 내에 혼합된 메시지 유형(예: 이미지/jpg 및 텍스트/일반)을 포함할 수 있습니다. NetX Duo HTTP 서버에는 클라이언트의 MIME을 포함하는 HTTP 메시지에서 콘텐츠 유형을 확인하기 위한 추가 서비스가 포함되어 있습니다. HTTP 다중 파트 지원을 사용하도록 설정하고 이러한 서비스를 사용하기 위해서는 구성 옵션 **NX_HTTP_MULTIPART_ENABLE** 이 정의되어 있어야 합니다.

```c
UINT  nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       UCHAR *entity_header_buffer,
                                       ULONG buffer_size);

UINT  nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_pptr,
                                        ULONG *available_offset,
                                        ULONG *available_length)
```

이러한 서비스 사용에 대한 자세한 내용은 3장 “HTTP 서비스 설명”을 참조하세요.

## <a name="http-multi-thread-support"></a>HTTP 다중 스레드 지원

NetX HTTP 클라이언트 서비스는 다중 스레드에서 동시에 호출할 수 있습니다. 하지만 특정 HTTP 클라이언트 인스턴스에 대한 읽기 또는 쓰기 요청은 동일한 스레드에서 순차적으로 수행되어야 합니다.

## <a name="http-rfcs"></a>HTTP RFC

NetX HTTP는 RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts” 및 관련 RFC와 호환됩니다.
