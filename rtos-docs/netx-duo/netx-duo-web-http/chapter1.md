---
title: 1장 - HTTP 및 HTTPS 소개
description: 이 장에서는 웹 모듈을 위한 Azure RTOS NetX Duo HTTP/HTTPS를 소개합니다.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5f50419be3171d3df8544d1b34d603822f339785923f8a8199dc5b5ddcac281
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801756"
---
# <a name="chapter-1---introduction-to-http-and-https"></a>1장 - HTTP 및 HTTPS 소개

HTTP(Hypertext Transfer Protocol)는 웹에서 콘텐츠를 전송하기 위해 설계된 프로토콜입니다. HTTP는 콘텐츠 전송 기능을 수행하기 위해 신뢰할 수 있는 TCP(Transmission Control Protocol) 서비스를 사용하는 간단한 프로토콜입니다. 따라서 HTTP는 매우 안정적인 콘텐츠 전송 프로토콜입니다. HTTP는 가장 많이 사용되는 애플리케이션 프로토콜 중 하나입니다. 웹의 모든 작업에 HTTP 프로토콜이 사용됩니다.

HTTPS는 HTTP 프로토콜의 보안 버전이며, 기본 TCP 연결을 보호하기 위해 TLS(전송 계층 보안)를 사용하여 HTTP를 구현합니다. TLS 설정에 필요한 추가 구성을 제외하고 HTTPS는 HTTP와 기본적으로 동일합니다.

## <a name="general-http-requirements"></a>일반 HTTP 요구 사항

NetX Web HTTP 패키지가 올바르게 작동하기 위해서는 NetX Duo(버전 5.10 이상)가 설치되어 있어야 합니다. 또한 IP 인스턴스를 만들고 동일한 IP 인스턴스에서 TCP를 사용하도록 설정해야 합니다. HTTPS 지원을 위해서는 NetX Secure TLS(버전 5.11 이상)도 설치해야 합니다(다음 섹션 참조). **2장** 의 “작은 예제 시스템” 섹션에 있는 데모 파일은 이를 수행하는 방법을 보여줍니다.

NetX Web HTTP 패키지의 HTTP 클라이언트 부분에는 추가 요구 사항이 없습니다.

NetX Web HTTP 패키지의 HTTP 서버 부분에는 여러 추가 요구 사항이 있습니다. 먼저 모든 클라이언트 HTTP 요청을 처리하기 위해 TCP의 *잘 알려진 포트 80* 에 대한 전체 액세스 권한이 필요합니다(애플리케이션이 다른 유효한 TCP 포트로 변경할 수 있음). 또한 HTTP 서버는 FileX 포함된 파일 시스템에 사용하도록 설계되었습니다. FileX를 사용할 수 없으면 사용자가 사용된 FileX 부분을 자신의 고유 환경으로 이식할 수 있습니다. 이에 대해서는 이 가이드의 이후 섹션에서 설명합니다.

## <a name="https-requirements"></a>HTTPS 요구 사항

HTTPS가 올바르게 작동하기 위해서는 NetX Web HTTP 패키지에 NetX Duo(버전 5.10 이상) 및 NetX Secure TLS(버전 5.11 이상)가 모두 설치되어 있어야 합니다. 또한 IP 인스턴스를 만들고 TLS에 사용하도록 동일한 IP 인스턴스에서 TCP를 사용하도록 설정해야 합니다. 적합한 암호화 루틴, 신뢰할 수 있는 CA 인증서를 사용하여 TLS 세션을 초기화하고, TLS 핸드셰이크 중 원격 서버 호스트로 제공되는 인증서에 대해 공간을 할당해야 합니다. **2장** 의 “작은 예제 HTTPS 시스템” 섹션에 있는 데모 파일은 이를 수행하는 방법을 보여줍니다.

NetX Web HTTP 패키지의 HTTPS 클라이언트 부분에는 추가 요구 사항이 없습니다.

NetX Web HTTP 패키지의 HTTPS 서버 부분에는 몇 가지 추가 요구 사항이 있습니다. 첫째, 모든 클라이언트 HTTPS 요청을 처리하기 위해 TCP의 *잘 알려진 포트 443* 에 대한 전체 액세스 권한이 필요합니다(일반 텍스트 HTTP와 마찬가지로 이 포트도 애플리케이션이 변경할 수 있음). 둘째, 적절한 암호화 루틴 및 서버 ID 인증서(또는 사전 공유 키)를 사용하여 TLS 세션을 초기화해야 합니다. 또한 HTTPS 서버는 FileX 포함된 파일 시스템에 사용하도록 설계되었습니다. FileX를 사용할 수 없으면 사용자가 사용된 FileX 부분을 자신의 고유 환경으로 이식할 수 있습니다. FileX 사용에 대해서는 이 가이드의 이후 섹션에서 설명합니다.

TLS의 구성 옵션에 대한 자세한 내용은 NetX 보안 문서를 참조하세요.

특별한 언급이 없으면 이 문서에 설명된 모든 HTTP 기능이 HTTPS에도 적용됩니다.

## <a name="http-and-https-constraints"></a>HTTP 및 HTTPS 제약 조건

NetX Web HTTP는 HTTP 1.1 표준을 구현합니다. 하지만 다음과 같은 제약 조건이 있습니다.

1. 요청 파이프라인이 지원되지 않음
1. HTTP 서버가 기본 및 MD5 다이제스트 인증을 모두 지원하지만 MD5-sess는 지원하지 않습니다. 현재까지 HTTP 클라이언트는 기본 인증만 지원합니다. HTTPS에 TLS를 사용할 때에도 HTTP 인증을 계속 사용할 수 있습니다.
1. 콘텐츠 압축은 지원되지 않습니다.
1. TRACE, OPTIONS 및 CONNECT 요청은 지원되지 않습니다.
1. HTTP 서버 또는 클라이언트와 연결된 패킷 풀은 전체 HTTP 헤더를 저장할 수 있을 만큼 커야 합니다.
1. HTTP 클라이언트 서비스는 콘텐츠 전송용으로만 제공되며, 이 패키지에는 디스플레이 유틸리티가 제공되지 않습니다.

## <a name="http-url-resource-names"></a>HTTP URL(리소스 이름)

HTTP 프로토콜은 웹에서 콘텐츠를 전송하도록 설계되었습니다. 요청된 콘텐츠는 URL(Universal Resource Locator)로 지정됩니다. 이것은 모든 HTTP 요청의 기본 구성 요소입니다. URL은 항상 “/” 문자로 시작하며 일반적으로 HTTP 서버에 있는 파일을 가리킵니다. 일반적인 HTTP 파일 확장자는 다음과 같습니다.

- **.htm**(또는 **.html**) HTML(Hypertext Markup Language)
- **.txt** 일반 ASCII 텍스트
- **.gif** 이진 GIF 이미지
- **.xbm** 이진 Xbitmap 이미지

## <a name="http-client-requests"></a>HTTP 클라이언트 요청

HTTP에는 웹 콘텐츠 요청을 위한 간단한 메커니즘이 포함되어 있습니다. TCP의 *잘 알려진 포트 80(HTTPS의 경우 포트 443)* 에서 연결이 성공적으로 설정된 후 클라이언트에서 실행되는 표준 HTTP 명령 세트가 있습니다. 다음은 기본 HTTP 명령 중 일부를 보여줍니다.

- **GET *resource* HTTP/1.1** 지정된 리소스를 가져옵니다.
- **POST *resource* HTTP/1.1** 지정된 리소스를 가져오고 연결된 입력을 HTTP 서버에 전달합니다.
- **HEAD *resource* HTTP/1.1** GET와 비슷하게 취급되지만 콘텐츠가 HTTP 서버에서 반환되지 않습니다.
- **PUT *resource* HTTP/1.1** 리소스를 HTTP 서버에 배치합니다.
- **DELETE *resource* HTTP/1.1** 서버에서 리소스를 삭제합니다.

이러한 ASCII 명령은 HTTP 서버로 HTTP 작업을 수행하기 위해 웹 브라우저 및 NetX Web HTTP 클라이언트 서비스에서 내부적으로 생성됩니다.

HTTP 클라이언트 애플리케이션에는 포트 80 또는 포트 443(HTTPS가 사용된 경우)이 사용됩니다. 클라이언트 및 서버 HTTP API는 모두 포트를 매개 변수로 사용합니다. 매크로 NX_WEB_HTTP_SERVER_PORT(포트 80) 및 NX_WEB_HTTPS_SERVER_PORT(포트 443)는 편의를 위해 정의됩니다. 또한 *nx_web_http_client_set_connect_port()* 서비스를 사용하여 런타임에 HTTP 서버 포트를 변경할 수도 있습니다. 이 서비스에 대한 자세한 내용은 4장을 참조하세요.

## <a name="http-server-responses"></a>HTTP 서버 응답

HTTP 서버는 동일한 *잘 알려진 TCP 포트 80(HTTPS의 경우 443)* 을 사용하여 클라이언트 명령 응답을 보냅니다. HTTP 서버가 클라이언트 명령을 처리하면 3자리 숫자 상태 코드가 포함된 ASCII 응답 문자열을 반환합니다. 이 숫자 응답은 HTTP 클라이언트 소프트웨어에서 작업의 성공 또는 실패 여부를 결정하는 데 사용됩니다. 다음은 클라이언트 명령에 대한 여러 HTTP 서버 응답 목록입니다.

- **200** 요청이 성공했습니다.
- **400** 요청이 올바르게 구성되지 않았습니다.
- **401** 권한이 없는 요청입니다. 클라이언트가 인증을 보내야 합니다.
- **404** 요청에 지정된 리소스를 찾을 수 없습니다.
- **500** 내부 HTTP 서버 오류입니다.
- **501** HTTP 서버에서 요청이 구현되지 않았습니다.
- **502** 서비스를 사용할 수 없습니다.

예를 들어, “test.htm” 파일을 PUT하기 위한 성공적인 클라이언트 요청은 “HTTP/1.1 200 OK” 메시지로 응답됩니다.

## <a name="http-communication"></a>HTTP 통신

앞에서 설명한 것처럼 HTTP 서버는 클라이언트 요청 처리를 위해 *잘 알려진 TCP 포트 80(HTTPS의 경우 443)* 을 사용합니다. HTTP 클라이언트는 진행 중인 연결에 대해 사용 가능한 모든 TCP 포트를 사용할 수 있습니다. HTTP 이벤트의 일반 시퀀스는 다음과 같습니다.

**HTTP GET 요청**:

1. 클라이언트가 서버 포트 80(또는 HTTPS의 경우 443)에 TCP 연결을 수행합니다.
1. HTTPS를 사용하는 경우 TCP 연결 후 TLS 핸드셰이크를 통해 서버를 인증하고 보안 채널을 설정합니다.
1. 클라이언트가 “**GET *resource* HTTP/1.1**” 요청을 보냅니다(다른 헤더 정보 포함).
1. 서버가 추가 정보 바로 다음에 리소스 콘텐츠(있는 경우)가 포함된 “**HTTP/1.1 200 OK**” 메시지를 작성합니다.
1. 서버가 클라이언트에서 연결을 해제합니다(HTTPS를 사용하는 경우 TLS가 종료됨).
1. 클라이언트가 소켓에서 연결을 해제합니다(TLS가 종료되고 서버의 연결 해제 경고가 표시됨).

**HTTP PUT 요청**:

1. 클라이언트가 서버 포트 80(또는 443)에 TCP 연결을 수행합니다.
1. HTTPS를 사용하는 경우 TCP 연결 후 TLS 핸드셰이크를 통해 서버를 인증하고 보안 채널을 설정합니다.
1. 클라이언트가 다른 헤더 정보와 함께 “PUT resource HTTP/1.1” 요청을 보낸 다음, 리소스 콘텐츠를 보냅니다.
1. 서버가 추가 정보 바로 다음에 리소스 콘텐츠가 포함된 “HTTP/1.1 200 OK” 메시지를 작성합니다.
1. 서버가 연결 해제를 수행합니다.
1. 클라이언트가 연결 해제를 수행합니다.

> [!NOTE]
> 앞에서 설명한 것처럼 HTTP 서버는 클라이언트에 연결하기 위해 대체 포트를 사용하는 웹 서버에 대해 *nx_web_http_client_set_connect_port()* 를 사용하여 런타임에 다른 포트로 기본 연결 포트(80 또는 443)를 변경할 수 있습니다.

## <a name="http-authentication"></a>HTTP 인증

HTTP 인증은 선택 사항이며 모든 웹 요청에 필요하지 않습니다. 인증에는 *기본* 및 *다이제스트* 라는 두 가지 종류가 있습니다. 기본 인증은 많은 프로토콜에서 사용되는 *이름* 및 *암호* 인증과 동일합니다. HTTP 기본 인증에서 이름 및 암호가 연결되고 base64 형식으로 인코딩됩니다. 기본 인증의 주요 단점은 이름 및 암호가 요청에서 공개적으로 전송된다는 것입니다. 따라서 이름 및 암호를 쉽게 도난당할 수 있습니다. 다이제스트 인증은 이름 및 암호를 요청으로 전송하지 않는 방식으로 이 문제를 해결합니다. 대신 이름, 암호 및 기타 정보로부터 128비트 다이제스트를 파생하기 위한 알고리즘이 사용됩니다. NetX Web HTTP 서버는 표준 MD5 다이제스트 알고리즘을 지원합니다.

인증은 언제 필요한가요? HTTP 서버는 요청된 리소스에 인증이 필요한지 여부를 결정합니다. 인증이 필요하고 클라이언트 요청에 적합한 인증이 포함되지 않은 경우 필요한 인증 유형이 포함된 “HTTP/1.1 401 권한 없음” 응답이 클라이언트에 전송됩니다. 그런 다음, 클라이언트는 적절한 인증으로 새 요청을 만들어야 합니다.

HTTPS를 사용하는 경우에도 HTTPS 서버는 HTTP 인증을 계속 사용할 수 있습니다. 이 경우 TLS는 모든 HTTP 트래픽을 암호화하는 데 사용되므로 *기본* HTTP 인증을 사용하는 경우 보안 위험이 발생하지 않습니다. *다이제스트* 인증도 허용되지만 TLS를 통한 기본 인증에 비해 크게 향상된 보안 기능을 제공하지는 않습니다.

## <a name="http-authentication-callback"></a>HTTP 인증 콜백

앞에서 설명한 것처럼 HTTP 인증은 선택 사항이며 모든 웹 전송에 필요한 것은 아닙니다. 또한 인증은 일반적으로 리소스에 따라 달라집니다. 서버에서 일부 리소스는 액세스할 때 인증이 필요하지만, 다른 리소스는 인증이 필요하지 않습니다. NetX Web HTTP 서버 패키지는 애플리케이션이 ***nx_web_http_server_create*** 호출을 통해 각 HTTP 클라이언트 요청 처리를 시작할 때 호출되는 인증 콜백 루틴을 지정하도록 허용합니다.

콜백 루틴은 NetX Web HTTP 서버에 사용자 이름, 암호 및 리소스와 연결된 영역 문자열을 제공하고 필요한 인증 유형을 반환합니다. 리소스에 인증이 필요하지 않으면 인증 콜백이 **NX_WEB_HTTP_DONT_AUTHENTICATE** 값을 반환합니다. 그렇지 않고, 지정된 리소스에 대해 기본 인증이 필요하면 루틴이 **NX_WEB_HTTP_BASIC_AUTHENTICATE** 를 반환합니다. 그리고 마지막으로 MD5 다이제스트 인증이 필요하면 콜백 루틴이 **NX_WEB_HTTP_DIGEST_AUTHENTICATE** 를 반환합니다. HTTP 서버에서 제공되는 리소스에 인증이 필요하지 않으면 콜백이 필요하지 않고 HTTP 서버 만들기 호출에 NULL 포인터를 제공할 수 있습니다.

애플리케이션 인증 콜백 루틴의 형식은 매우 간단하며 아래에 정의되어 있습니다.

```C
UINT nx_web_http_server_authentication_check(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type, CHAR *resource,
    CHAR **name, CHAR **password,
    CHAR **realm);
```

입력 매개 변수는 다음과 같이 정의됩니다.

- **request_type** HTTP 클라이언트 요청을 지정합니다. 유효한 요청은 다음과 같이 정의됩니다.
  - **NX_WEB_HTTP_SERVER_GET_REQUEST**
  - **NX_WEB_HTTP_SERVER_POST_REQUEST**
  - **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
  - **NX_WEB_HTTP_SERVER_PUT_REQUEST**
  - **NX_WEB_HTTP_SERVER_DELETE_REQUEST**
- **resource** 요청된 특정 리소스입니다.
- **name** 필요한 사용자 이름에 대한 포인터의 대상입니다.
- **password** 필요한 암호에 대한 포인터의 대상입니다.
- **realm** 이 인증의 영역에 대한 포인터의 대상입니다.

인증 루틴의 반환 값은 인증이 필요한지 여부를 지정합니다. **NX_WEB_HTTP_DONT_AUTHENTICATE** 가 인증 콜백 루틴으로 반환된 경우 이름, 암호 및 영역 포인터가 사용되지 않습니다. 그렇지 않으면 HTTP 서버 개발자가 *nx_web_http_server.h* 에 정의된 **NX_WEB_HTTP_MAX_USERNAME** 및 **NX_WEB_HTTP_MAX_PASSWORD** 가 인증 콜백에 지정된 사용자 이름 및 암호에 대해 충분히 큰지 확인해야 합니다. 이러한 두 값 모두 기본 크기는 20자입니다.

## <a name="http-invalid-usernamepassword-callback"></a>HTTP 잘못된 사용자 이름/암호 콜백

HTTP 서버가 클라이언트 요청에서 잘못된 사용자 이름 및 암호 조합을 수신하는 경우 NetX Web HTTP 서버에서 잘못된 사용자 이름/암호 콜백(선택 사항)이 호출됩니다. HTTP 서버 애플리케이션이 HTTP 서버에 콜백을 등록하는 경우 기본 또는 다이제스트 인증이 *nx_web_http_server_get_process()* , *nx_web_http_server_put_process()* 또는 *nx_web_http_server_delete_process()* 에서 실패할 경우에 호출됩니다.

HTTP 서버에 콜백을 등록하기 위해 NetX Web HTTP 서버에 대해 다음 서비스가 정의됩니다.

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource, ULONG *client_nx_address,
        UINT request_type));
```

요청 유형은 다음과 같이 정의됩니다.

- **NX_WEB_HTTP_SERVER_GET_REQUEST**
- **NX_WEB_HTTP_SERVER_POST_REQUEST**
- **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
- **NX_WEB_HTTP_SERVER_PUT_REQUEST**
- **NX_WEB_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>HTTP GMT 날짜 헤더 삽입 콜백

NetX Web HTTP 서버에는 응답 메시지에 날짜 헤더를 삽입하기 위한 선택적인 콜백이 있습니다. 이 콜백은 HTTP 서버가 put 또는 get 요청에 응답할 때 호출됩니다.

GMT 날짜 콜백을 HTTP 서버에 등록하기 위해 다음 서비스가 정의됩니다.

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

NX_WEB_HTTP_SERVER_DATE 데이터 형식은 다음과 같이 정의됩니다.

```C
typedef struct NX_WEB_HTTP_SERVER_DATE_STRUCT
{
    USHORT nx_web_http_server_year; /* Year */
    UCHAR nx_web_http_server_month; /* Month */
    UCHAR nx_web_http_server_day; /* Day */
    UCHAR nx_web_http_server_hour; /* Hour */
    UCHAR nx_web_http_server_minute; /* Minute */
    UCHAR nx_web_http_server_second; /* Second */
    UCHAR nx_web_http_server_weekday; /* Weekday */
} NX_WEB_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>HTTP 캐시 정보 가져오기 콜백

HTTP 서버에는 특정 리소스에 대해 HTTP 애플리케이션에서 최대 사용 기간 및 날짜를 요청하기 위한 콜백이 있습니다. 이 정보는 HTTP 서버가 클라이언트 Get 요청에 대한 응답으로 전체 페이지를 보내는지 여부를 확인하기 위해 사용됩니다. 클라이언트 요청에서 “이후 수정 여부”를 찾을 수 없거나 캐시 가져오기 콜백으로 반환된 “마지막 수정” 날짜와 일치하지 않으면 전체 페이지가 전송됩니다.

콜백을 HTTP 서버에 등록하기 위해 다음 서비스가 정의됩니다.

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)
    (CHAR *, UINT *, NX_WEB_HTTP_SERVER_DATE *));
```

## <a name="http-chunked-transfer-coding-support"></a>HTTP 청크 분할 전송 코딩 지원

HTTP 메시지를 보내기 전에 전체 길이를 확인할 수 없는 경우 청크 분할 전송 코딩 기능을 사용하여 “Content-Length” 헤더 필드 없이 메시지를 일련의 청크로 보낼 수 있습니다. 이 기능은 모든 HTTP 요청 및 응답 메시지에서 지원됩니다. 이 기능은 받는 사람에게 지원되며 청크 헤더는 내부 논리에 의해 투명하게 처리됩니다. 보낸 사람인 경우에는 클라이언트와 서버에서 각각 API *nx_web_http_client_request_chunked_set* 및 *nx_web_http_server_response_chunked_set* 를 호출해야 합니다.

```C
UINT nx_web_http_client_request_chunked_set(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);

UINT nx_web_http_server_response_chunked_set(NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);
```

이러한 서비스에 대한 자세한 내용은 3장 “HTTP 서비스 설명”을 참조하세요.

## <a name="http-multipart-support"></a>HTTP 다중 파트 지원

MIME(Multipurpose Internet Mail Extensions)는 처음에 SMTP 프로토콜을 위해 만들어졌지만 사용 범위가 HTTP로 확장되었습니다. MIME를 사용하면 동일한 메시지 내에 혼합된 메시지 유형(예: 이미지/jpg 및 텍스트/일반)을 포함할 수 있습니다. NetX Web HTTP 서버에는 클라이언트의 MIME를 포함하는 HTTP 메시지에서 콘텐츠 유형을 확인하기 위한 서비스가 포함되어 있습니다. HTTP 다중 파트 지원을 사용하도록 설정하고 이러한 서비스를 사용하기 위해서는 구성 옵션 **NX_WEB_HTTP_MULTIPART_ENABLE** 이 정의되어 있어야 합니다.

```C
UINT nx_web_http_server_get_entity_header(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);

UINT nx_web_http_server_get_entity_content(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

이러한 서비스 사용에 대한 자세한 내용은 3장 “HTTP 서비스 설명”을 참조하세요.

## <a name="http-multi-thread-support"></a>HTTP 다중 스레드 지원

NetX Web HTTP 클라이언트 서비스는 다중 스레드에서 동시에 호출될 수 있습니다. 하지만 특정 HTTP 클라이언트 인스턴스에 대한 읽기 또는 쓰기 요청은 동일한 스레드에서 순차적으로 수행되어야 합니다.

HTTPS를 사용하는 경우 NetX Web HTTP 클라이언트 서비스는 다중 스레드에서 호출될 수 있지만, 기본 TLS 기능이 복잡해지지 않도록 각 스레드에는 독립적인 단일 HTTP 클라이언트 인스턴스(NX_WEB_HTTP_CLIENT 컨트롤 구조)가 있어야 합니다.

## <a name="http-rfcs"></a>HTTP RFC

NetX Web HTTP는 RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2616 “Hypertext Transfer Protocol – HTTP/1.1”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts” 및 관련 RFC를 준수합니다.

HTTPS의 경우 NetX Web HTTP는 RFC 2818 “HTTP over TLS”를 준수합니다.
