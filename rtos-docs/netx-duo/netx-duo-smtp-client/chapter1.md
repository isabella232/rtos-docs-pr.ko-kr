---
title: 1장 - Azure RTOS NetX Duo SMTP 클라이언트 소개
description: SMTP(Simple Mail Transfer Protocol)는 네트워크와 인터넷 간의 메일 전송을 위한 프로토콜입니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: df8c6b6920577ebfc18ed9252761401c30822c034e30d7ae95b25778707f53d5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797825"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-smtp-client"></a>1장 - Azure RTOS NetX Duo SMTP 클라이언트 소개

SMTP(Simple Mail Transfer Protocol)는 네트워크와 인터넷 간의 메일 전송을 위한 프로토콜입니다. 신뢰할 수 있는 TCP(Transmission Control Protocol) 서비스를 사용하여 콘텐츠 전송 기능을 수행합니다.

## <a name="netx-duo-smtp-client-requirements"></a>NetX Duo SMTP 클라이언트 요구 사항

NetX Duo SMTP 클라이언트를 사용하려면 NetX Duo IP 인스턴스 및 NetX Duo 패킷 풀을 만들어야 합니다. SMTP 클라이언트는 TCP 소켓을 사용하여 *잘 알려진 포트 25* 로 SMTP 서버에 연결합니다. 따라서 이전에 생성된 IP 인스턴스에서 *nx_tcp_enable* 서비스를 호출하여 먼저 TCP를 사용하도록 설정해야 합니다.

SMTP 클라이언트 만들기 호출(nxd_smtp_client_create)을 수행하려면 실제 메일 메시지를 전송하는 것 외에도 SMTP 명령을 서버로 전송하기 위해 이전에 만든 패킷 풀이 필요합니다. 패킷 페이로드는 메일 콘텐츠의 예상 크기에 따라 달라지며 TCP, IP 헤더 및 MAC 헤더를 허용해야 합니다. (IPv6 헤더는 40바이트이고 IPv4 헤더는 20바이트입니다.)

전체 메일 메시지가 한 패킷에 들어갈 수 없으면 SMTP 클라이언트가 메시지 나머지를 포함할 추가 패킷을 할당합니다.

## <a name="netx-duo-smtp-client-constraints"></a>NetX Duo SMTP 클라이언트 제약 조건

NetX Duo SMTP 프로토콜은 RFC 2821 및 2554 표준을 구현하지만 몇 가지 제약 조건이 있습니다.

1. NetX Duo SMTP 클라이언트는 LOGIN 및 PLAIN 인증만 지원하고 CRAM-MD5 다이제스트 인증을 지원하지 않습니다.
2. NetX Duo SMTP 클라이언트 메시지는 메일 항목당 한 명의 수신자로 제한되고 SMTP 서버와의 TCP 연결당 하나의 메일 메시지로만 제한됩니다.
3. VRFY, SEND, SOML, EXPN, SAML, ETRN, TURN 및 SIZE SMTP 옵션은 지원되지 않습니다.
4. SMTP 클라이언트는 일반적으로 메일 메시지를 만들기 위해 사용되는 메일 브라우저(“메일 사용자 에이전트”)가 아닙니다. “메일 전송 에이전트”에만 해당합니다. RFC 2821에 지정된 대로 SMTP 전송을 위해 메일 메시지의 필수 처리를 제공합니다. 콘텐츠에서 수신자 및 역방향 경로와 같은 올바른 구문을 확인하지 않습니다. MIME 데이터 또는 일반 텍스트 메시지와 같이 메일 버퍼에 들어가는 내용은 제한이 없습니다. 헤더 및 메시지 본문을 포함하기 위해 RFC 2822에 지정된 메일 메시지 형식은 SMTP 클라이언트 API의 범위를 벗어납니다.

## <a name="commands-supported-by-netx-duo-smtp-client"></a>NetX Duo SMTP 클라이언트에서 지원되는 명령

NetX Duo SMTP 클라이언트는 SMTP 서버와의 메일 세션 중 다음 명령을 사용합니다.

- **EHLO** 클라이언트가 SMTP 서버에서 제공되는 일부 또는 모든 확장 프로토콜 SMTP 서비스를 포함하는 세션을 시작하려고 합니다. 이것이 기본값입니다.
- **HELO** 클라이언트가 기본 SMTP 서비스로 제한되는 세션을 시작하려고 합니다.
- **MAIL** 클라이언트는 서버가 클라이언트 메일을 수신하도록 합니다.
- **AUTH** 클라이언트가 서버의 인증을 시작하려고 합니다.
- **RCPT** 클라이언트가 메일을 전달하려는 다른 호스트의 사서함을 제출하려고 합니다.
- **DATA** 클라이언트가 서버에 메일 메시지 데이터 전송을 시작하려고 합니다.
- **QUIT** 클라이언트가 세션을 종료하려고 합니다.

## <a name="getting-started"></a>시작하기

SMTP 클라이언트 애플리케이션은 IP 인스턴스를 만들고 이 IP 인스턴스에서 TCP를 사용하도록 설정합니다. 그런 다음, 다음 서비스를 사용하여 SMTP 클라이언트를 만듭니다.

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type,
    NXD_ADDRESS *server_address, UINT port);
```

*client_packet_pool_ptr* 은 SMTP 클라이언트가 SMTP 서버에 메시지를 보내기 위해 사용하는 이전에 생성된 패킷 풀에 대한 포인터입니다.

애플리케이션은 로컬 디바이스에 대한 *from_address* 와 서버 IP 주소를 제공해야 합니다. 모든 주소는 정규화된 도메인 이름이어야 합니다. 정규화된 도메인 이름에는 ‘@’ 문자로 구분된 로컬 부분과 도메인 이름이 포함됩니다. SMTP 클라이언트는 아래 nx_smtp_mail_send 서비스에서 *from_address* 또는 *recipient_address* 의 구문을 확인하지 않습니다.

SMTP 클라이언트가 생성된 후 SMTP 클라이언트 애플리케이션은 올바른 형식의 SMTP 메일 메시지를 사용하여 메일 항목을 만들고, 다음 API를 사용하여 SMTP 클라이언트에 대해 메일 항목 보내기 요청을 수행합니다.

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address, UINT priority,
    CHAR *subject, CHAR *mail_body,
    UINT mail_body_length);
```

기본적으로 사용자 관점에서 볼 때는 IPv4 또는 IPv6으로 SMTP 클라이언트를 실행할 때 차이가 없습니다. 두 IP 프로토콜 간의 차이는 기본 NetX Duo 레이어에서 처리됩니다.

메일을 보내려는 애플리케이션은 *nx_smtp_client_mail* 호출에 수신자 주소를 제공해야 합니다.

인증을 위해서는 사용자 이름이 정규화된 도메인 이름이거나 사용자 이름을 표시할 수 있습니다. 이것은 서버의 인증 수행 방법에 따라 달라집니다.

이 사용자 가이드의 뒷부분에 나오는 작은 예제 섹션의 데모에서는 메시지의 형식 지정 방법을 보여줍니다. 메일 항목 보내기에 성공한 경우 상태는 NX_SUCCESS입니다. 내부 오류, 중단된 TCP 연결, 서버 회신 오류 코드 수신과 같은 오류가 발생하면 *nx_smtp_mail_send* 가 0이 아닌 오류 상태를 반환합니다.

메일 항목을 전송할 때 NetX Duo SMTP 클라이언트는 SMTP 서버와 새로운 TCP 연결을 만들고 SMTP 세션을 시작합니다. 이 세션에서 클라이언트는 SMTP 프로토콜의 일부로 SMTP 서버에 일련의 명령을 보내고, 실제 메일 메시지 전송을 완료합니다. 그런 다음, SMTP 세션의 결과에 관계없이 TCP 연결이 종료됩니다.

성공 또는 실패에 관계없이 메일 전송 후 SMTP 클라이언트가 ‘초기’ 상태로 돌아가고, 다른 메일 전송 세션에 사용될 수 있습니다.

## <a name="netx-duo-smtp-authentication"></a>NetX Duo SMTP 인증

인증은 SMTP 클라이언트가 SMTP 서버에 대해 자신의 ID를 입증하고 신뢰할 수 있는 사용자로서 자신의 메일이 전달될 수 있게 해주는 방법입니다. 대부분의 상용 SMTP 서버에서는 클라이언트가 인증을 받아야 합니다.

일반적으로 인증 데이터는 보낸 사람의 사용자 이름과 암호로 구성됩니다. 인증 질문 중에 서버가 이 정보를 요청하고 클라이언트는 인코딩된 형식으로 요청된 데이터를 전송하여 응답합니다. 서버는 데이터를 디코딩하고 사용자 데이터베이스에서 일치하는 항목을 찾습니다. 항목이 있으면 서버에서 인증이 성공했음을 나타냅니다. SMTP 인증은 [RFC 2554](http://www.ietf.org/rfc/rfc2554.txt)에 정의되어 있습니다.

인증에는 *기본* 및 *다이제스트* 라는 두 가지 종류가 있습니다. 다이제스트는 현재 NetX Duo SMTP 클라이언트에서 지원되지 않으며 여기에서 다루지 않습니다. 기본 인증은 위에서 설명한 *이름* 및 *암호* 인증과 동일합니다. SMTP 기본 인증에서 이름과 암호는 base64로 인코딩됩니다. 기본 인증의 장점은 구현이 쉽고 널리 사용된다는 것입니다. 기본 인증의 주요 단점은 이름과 암호가 요청에서 공개적으로 전송된다는 것입니다.

### <a name="plain-authentication"></a>일반 인증

NetX Duo SMTP 클라이언트는 PLAIN 매개 변수로 AUTH 명령을 보냅니다. NetX Duo SMTP 서버가 이 유형의 인증을 지원할 경우 334 회신 코드로 회신합니다. 클라이언트는 단일 base64로 인코딩된 사용자 이름 및 암호 메시지로 서버에 회신합니다. 서버에서 클라이언트 인증이 성공한 것으로 확인되면 235 성공 코드로 응답합니다.

### <a name="login-authentication"></a>로그인 인증

NetX Duo SMTP 클라이언트는 LOGIN 매개 변수로 AUTH 명령을 보냅니다. NetX Duo SMTP 서버가 이 유형의 인증을 지원할 경우 인증 ‘질문’이 시작될 때 334 회신 코드로 회신합니다. 일반적으로 “사용자 이름”인 base64로 인코딩된 프롬프트를 클라이언트로 다시 보냅니다. 클라이언트가 프롬프트를 디코딩하고 base64로 인코딩된 사용자 이름으로 회신합니다. 서버가 클라이언트 사용자 이름을 수락하면 클라이언트 암호에 대해 base64로 인코딩된 프롬프트를 보냅니다. 클라이언트가 base64로 인코딩된 암호로 응답합니다. 서버에서 클라이언트 인증이 성공한 것으로 확인되면 235 성공 코드로 응답합니다.

### <a name="no-authentication"></a>인증 없음

일부 SMTP 서버는 인증 없이 구성됩니다. 그럴 경우 클라이언트 EHLO 메시지에 대한 250 응답에는 인증 유형이 나열되지 않습니다. 하지만 나열된 인증 유형이 없다고 해서 서버에 반드시 인증이 필요하지 않거나 인증이 지원되지 않는 것은 아닙니다. 이러한 상황에서 클라이언트가 PLAIN 또는 LOGIN 인증으로 구성된 경우 NetX Duo 클라이언트 스레드 작업은 기본적으로 PLAIN으로 설정됩니다. 클라이언트가 NONE으로 구성된 경우 인증 단계를 건너뛰고 SMTP 상태가 MAIL 상태로 이동합니다.

클라이언트가 인증 없음으로 구성되었고 SMTP 서버가 인증을 지원하지 않을 경우 클라이언트 인증 유형이 PLAIN으로 전환됩니다.

## <a name="rfcs-supported-by-netx-duo-smtp-client"></a>NetX Duo SMTP 클라이언트에서 지원되는 RFC

NetX Duo SMTP 클라이언트 API는 RFC2821 “Simple Mail Transfer Protocol” 및 RFC 2554 “인증에 대한 SMTP 서비스 확장을 준수합니다. “
