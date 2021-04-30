---
title: 3장 - SMTP 클라이언트 서비스의 클라이언트 설명
description: 이 장에서는 일반적인 SMTP 클라이언트 애플리케이션에서 사용량의 순서대로 모든 NetX Duo SMTP 클라이언트 서비스(아래에 나열됨)에 대한 설명을 포함합니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f590ba5a4c020b4a0aec6628a89c0e5f0f8579d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810603"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a>3장 - SMTP 클라이언트 서비스의 클라이언트 설명

이 장에서는 일반적인 SMTP 클라이언트 애플리케이션에서 사용량의 순서대로 모든 NetX Duo SMTP 클라이언트 서비스(아래에 나열됨)에 대한 설명을 포함합니다.

> [!NOTE]
> 다음 API 설명의 “반환 값” 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **_NX_DISABLE_ERROR_CHECKING_** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

## <a name="nxd_smtp_client_create"></a>nxd_smtp_client_create

SMTP 클라이언트 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에서 SMTP 클라이언트 인스턴스를 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터
- **ip_ptr** IP 인스턴스에 대한 포인터
- **packet_pool_ptr** 클라이언트 패킷 풀에 대한 포인터
- **username** 인증을 위해 NULL로 종료되는** 사용자 이름
- **password** 인증을 위해 NULL로 종료되는 암호
- **from_address** NULL로 종료되는 발신자의 주소
- **client_domain** NULL로 종료되는 도메인 이름
- **authentication_type** 클라이언트 인증 유형 지원되는 형식은
  - NX_SMTP_CLIENT_AUTH_LOGIN
  - NX_SMTP_CLIENT_AUTH_PLAIN
  - NX_SMTP_CLIENT_AUTH_NONE
- **server_address** SMTP 서버 IP 주소에 대한 포인터
- **server_port** SMTP 서버 TCP 포트

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) SMTP 클라이언트를 성공적으로 만들었습니다. TCP 소켓 만들기 상태
- NX_SMTP_INVALID_PARAM (0xA5) 잘못된 포인터가 아닌 입력
- NX_IP_ADDRESS_ERROR (0x21) 잘못된 IP 주소 유형
- NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용 위치

응용 프로그램 코드

### <a name="example"></a>예제

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a>nx_smtp_client_delete

SMTP 클라이언트 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 SMTP 클라이언트 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 클라이언트를 성공적으로 삭제함
- NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a>nx_smtp_mail_send

SMTP 메일 항목 만들기 및 보내기

### <a name="prototype"></a>프로토타입

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a>Description

이 서비스는 SMTP 메일 항목을 만들고 보냅니다. SMTP 클라이언트는 SMTP 서버와의 TCP 연결을 설정하고 일련의 SMTP 명령을 보냅니다. 오류가 발생하지 않으면 메일 메시지를 서버로 전송합니다. 메일이 전송되었는지 여부에 관계 없이 TCP 연결이 종료되고 메일 전송 결과를 나타내는 상태가 반환됩니다. 애플리케이션은 제한 없이 전송해야 하는 만큼의 메일 메시지에 대해 이 서비스를 호출할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트에 대한 포인터
- **recipient_address** NULL로 종료되는 받는 사람 주소입니다.
- **subject** NULL로 종료되는 제목 줄 텍스트
- **priority** 메일이 배달되는 우선 순위 수준
- **mail_body** 메일 메시지에 대한 포인터
- **mail_body_length** 메일 메시지의 크기

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 메일을 성공적으로 보냄
- **NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) SMTP 세션의 SMTP 세션 상태 결과에 대해 초기화되지 않은 SMTP 클라이언트 인스턴스
- NX_PTR_ERROR (0x07) 잘못된 포인터 매개 변수
- NX_SMTP_INVALID_PARAM (0xA5) 잘못된 포인터가 아닌 입력
- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
