---
title: 1장 - Azure RTOS NetX POP3 소개
description: NetX Duo POP3 클라이언트 API는 클라이언트 메일을 검색하기 위해 POP3 서버에서 클라이언트 maildrops에 액세스할 수 있는 소규모 워크스테이션에 메일 전송 시스템을 제공하도록 설계되었습니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0143b142a39bbda28ae20d41adf08119b8b2f8f99d510a456743b4f447802833
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797231"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3"></a>1장 - Azure RTOS NetX POP3 소개

POP3(Post Office Protocol 버전 3)은 작은 워크스테이션이 클라이언트 메일을 검색하기 위해 POP3 서버의 클라이언트 maildrops에 액세스할 수 있는 메일 전송 시스템을 제공하도록 설계된 프로토콜입니다. POP3에서는 TCP(전송 제어 프로토콜) 서비스를 활용하여 메일 전송을 수행합니다. 따라서 POP3는 매우 안정적인 콘텐츠 전송 프로토콜입니다.

그러나 POP3은 메일 처리에 대한 광범위한 작업을 제공하지 않습니다. 일반적으로 메일은 클라이언트에서 다운로드된 다음, 서버의 maildrop에서 삭제됩니다.

## <a name="netx-duo-pop3-client-requirements"></a>NetX Duo POP3 클라이언트 요구 사항

### <a name="client-requirements"></a>클라이언트 요구 사항

NetX POP3 Client API에는 *nx_ip_create* 를 사용하여 이전에 만든 NetX Duo IP 인스턴스와 *nx_packet_pool_create* 를 사용하여 이전에 만든 NetX 패킷 풀이 필요합니다. NetX Duo POP3 클라이언트는 TCP 서비스를 활용하기 때문에 동일한 IP 인스턴스에서 NetX Duo POP3 클라이언트 API를 사용하기 전에 *nx_tcp_enable* 호출을 사용하여 TCP를 사용하도록 설정해야 합니다. POP3 클라이언트는 TCP 소켓을 사용하여 서버의 POP3 포트에서 POP3 서버에 연결합니다. 이는 일반적으로 *잘 알려진 포트 110에서 설정되지만 이 포트를 사용하는 데는 POP3 클라이언트와 서버 모두 필요하지 않습니다.*

POP3 클라이언트를 만드는 데 사용되는 패킷 풀의 크기는 패킷 페이로드의 측면에서 사용자 구성 가능하고 사용 가능한 패킷 수와 동일합니다. 패킷이 POP3 클라이언트 만들기 서비스에서만 사용되는 경우 사용자 이름 및 암호의 길이 또는 APOP 다이제스트의 길이에 따라 패킷 페이로드가 100-120바이트를 초과할 필요가 없습니다. 로컬 호스트의 사용자 이름이 있는 USER 명령은 POP3 클라이언트에서 보낸 가장 큰 메시지일 수 있습니다. IP 내부 작업은 TCP 제어 데이터를 보내고 받는 데 매우 큰 패킷 페이로드가 필요하지 않으므로 nx_ip_create(IP 기본 패킷 풀)에서 동일한 패킷 풀을 공유할 수 있습니다.

그러나 일반적으로는 이더넷 드라이버가 POP3 클라이언트 패킷 풀과 동일한 패킷 풀을 사용하는 것은 유용하지 않습니다. 일반적으로 수신 패킷 풀 페이로드의 페이로드는 POP3 클라이언트 메시지보다 훨씬 큰 네트워크 인터페이스의 IP 인스턴스 MTU(일반적으로 1500바이트)를 설정합니다. 들어오는 POP3 메시지는 일반적으로 나가는 POP3 클라이언트 메시지보다 훨씬 더 큰 데이터 크기입니다.

## <a name="netx-duo-pop3-client-creation"></a>NetX Duo POP3 클라이언트 만들기

POP3 클라이언트를 만들기 위한 두 가지 서비스가 있습니다. 권장되는 서비스는 POP3 서버의 IPv4 또는 IPv6 주소를 허용하는 NXD_ADDRESS 주소 데이터 형식을 사용하는 *nxd_pop3_client_create* 입니다. 다른 POP3 클라이언트 만들기 서비스인 *nx_pop3_client_create* 는 POP3 서버에 대한 IPv4 주소만 허용합니다. 두 서비스는 TCP 소켓 포트를 바인딩하고 POP3 서버와 연결합니다.

POP3 서버와 연결한 후 POP3 클라이언트 애플리케이션은 *nx_pop3_client _mail_items_get* 을 호출하여 해당 maildrop 상자에 있는 메일 항목 수를 가져올 수 있습니다.

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items, ULONG *maildrop_total_size);
```

하나 이상의 항목이 클라이언트 maildrop에 있는 경우 애플리케이션은 *nx_pop3_client_get_mail_item* 서비스를 사용하여 특정 메일 항목의 크기를 가져올 수 있습니다.

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

maildrop의 첫 번째 메일 항목은 인덱스 1에 있습니다.

실제 메일 메시지를 가져오기 위해 애플리케이션은 서비스에서 final_packet 입력 인수가 마지막 패킷을 수신했음을 확인할 때까지 *nx_pop3_client_mail_item_get_message_data* 서비스를 호출하여 메일 메시지 패킷을 검색할 수 있습니다.

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

특정 메일 항목을 삭제하기 위해 애플리케이션은 위의 *nx_pop3_client_get_mail_item* 호출에서 사용되는 것과 동일한 인덱스를 사용하여 *nx_pop3_client_mail_item_delete* 를 호출합니다.

클라이언트는 *nx_pop3_client_delete* 서비스를 사용하여 삭제할 수 있습니다. 애플리케이션에서 *nx_packet_pool_delete* 서비스를 사용하여 POP3 클라이언트 패킷 풀을 삭제하는 것은 더 이상 사용되지 않습니다.

## <a name="netx-duo-pop3-client-constraints"></a>NetX Duo POP3 클라이언트 제약 조건

NetX Duo POP3 클라이언트 구현에는 다음과 같은 몇 가지 제약 조건이 있습니다.

1. NetX Duo POP3 클라이언트는 AUTH 명령을 지원하지 않습니다. 단, 클라이언트 서버 인증 교환에는 DIGEST-MD5를 사용하여 APOP 인증을 구현합니다.
2. NetX Duo POP3 클라이언트는 모든 POP3 명령(예: TOP 또는 UIDL 명령)을 구현하지 않습니다. 다음은 지원되는 명령 목록입니다.
   - NOOP
   - RSET

## <a name="netx-duo-pop3-client-login"></a>NetX Duo POP3 클라이언트 로그인

NetX Duo POP3 클라이언트는 maildrop에 액세스하기 위해 자체(로그인)를 POP3 서버에 인증해야 합니다. USER/PASS 명령을 사용하고 POP3 서버에 알려진 사용자 이름과 암호를 제공하거나 아래에 설명된 APOP 명령 및 MD5 다이제스트를 사용하여 이 작업을 수행할 수 있습니다.

사용자 이름은 일반적으로 정규화된 도메인 이름입니다. 여기에는 ‘@’ 문자로 구분된 로컬 부분과 도메인 이름이 포함됩니다. POP3 명령 USER 및 PASS를 사용하는 경우 클라이언트는 인터넷을 통해 암호화되지 않은 해당 사용자 이름과 암호를 보냅니다.

일반 텍스트 사용자 이름 및 암호의 보안 위험을 방지하기 위해 *nxd_pop3_client_create* 서비스에서 *APOP_authentication* 매개 변수를 설정하여 APOP 인증을 사용하도록 NetX Duo POP3 클라이언트를 구성할 수 있습니다.

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address, ULONG server_port,
    CHAR *client_name,
    CHAR *client_password);
```

또는 IPv4 전용 애플리케이션의 경우 *nx_pop3_client_create* 서비스는 다음과 같습니다.

```C
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address,
    ULONG server_port, CHAR *client_name,
    CHAR *client_password);
```

클라이언트가 APOP 명령을 보내는 경우 서버 도메인을 포함하는 MD5 다이제스트, 서버 인사말에서 추출된 로컬 시간 및 프로세스 ID 및 클라이언트 암호가 유일한 인수로 사용됩니다. POP3 서버는 동일한 정보를 포함하는 MD5 다이제스트를 만들며 해당 MD5 다이제스트가 클라이언트의 MD5 다이제스트와 일치하는 경우 클라이언트가 인증됩니다.

APOP 인증이 실패하는 경우 NetX Duo POP3 클라이언트는 USER/PASS 인증을 시도합니다.

## <a name="the-pop3-client-maildrop"></a>POP3 클라이언트 Maildrop

클라이언트 메일은 POP3 서버에 사서함 또는 “maildrop”으로 저장됩니다. POP3 서버의 클라이언트 maildrop은 1개의 기반 메일 항목 목록으로 표시됩니다. 즉, 각 메일은 인덱스 1(0이 아님)의 첫 번째 메일 항목을 사용하여 maildrop 목록의 해당 인덱스에 의해 참조됩니다. POP3 명령은 이 목록에서 해당 인덱스별로 특정 메일 항목을 참조합니다.

## <a name="the-pop3-protocol-state-machine"></a>POP3 프로토콜 상태 시스템

POP3 프로토콜을 사용하려면 클라이언트와 서버 모두에서 POP3 세션의 상태를 유지해야 합니다. 먼저 클라이언트가 POP3 서버에 연결을 시도합니다. 성공하면 RFC 1939에 정의된 세 가지 고유한 상태를 가진 POP3 프로토콜에 입력합니다. 초기 상태는 서버에서 자신을 식별해야 하는 권한 부여 상태입니다. 권한 부여 상태에서 POP3 클라이언트는 USER 및 PASS 명령, 해당 순서 또는 APOP 명령만 발급할 수 있습니다.

POP3 클라이언트가 인증되면 클라이언트 세션이 트랜잭션 상태로 전환됩니다. 이 상태에서 클라이언트는 메일 삭제를 다운로드하고 요청할 수 있습니다. 트랜잭션 상태에서 허용되는 명령은 LIST, STAT, RETR, DELE, RSET 및 QUIT입니다. 일반적으로 POP3 클라이언트는 STAT 명령과 일련의 RETR 명령을 차례로 보냅니다(해당 maildrop의 각 메일 항목에 대해 하나씩).

클라이언트가 QUIT 명령을 실행하면 POP3 세션이 서버에서 TCP 연결 끊기를 시작하는 업데이트 상태를 입력합니다. 다른 시간에 메일을 다운로드하기 위해 POP3 클라이언트 애플리케이션은 nx_pop3_client_mail_items_get을 호출하여 maildrop에서 새 메일을 확인할 수 있습니다.

### <a name="pop3-server-reply-codes"></a>POP3 서버 회신 코드

- +OK 서버에서 이 회신을 사용하여 Client 명령을 수락합니다. 서버는 ‘+OK’ 이후의 추가 정보를 포함할 수 있지만 메일 메시지 데이터를 다운로드하는 경우나 LIST 또는 DELE 명령을 제외하고 클라이언트가 이 정보를 처리한다고 간주할 수는 없습니다. 후자의 경우 명령 뒤의 '인수'는 클라이언트 maildrop에서 메일 항목의 인덱스를 참조합니다.
- -ERR 서버에서 이 회신을 사용하여 Client 명령을 거부합니다. 서버는 ‘-ERR’ 다음에 추가 정보를 보낼 수 있지만 클라이언트가 이 정보를 처리한다고 간주할 수는 없습니다.

### <a name="sample-pop3-client---server-session"></a>샘플 POP3 클라이언트 - 서버 세션

**USER/PASS를 사용하는 기본 POP3 예제:**

```
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: USER mrose
S: +OK mrose is valid
C: PASS mvan99
S: +OK mrose is logged in
C: STAT
S: +OK 2 320
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

**APOP를 사용하는 기본 POP3 예제(및 STAT 대신 LIST):**

```
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: APOP mrose c4c9334bac560ecc979e58001b3e22fb
S: +OK mrose's maildrop has 2 messages (320 octets)
C: LIST
S: +OK 2 messages (320 octets)
S: 1 120
S: 2 200
S: .
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK dewey POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

## <a name="rfcs-supported-by-netx-duo-pop3-client"></a>NetX Duo POP3 클라이언트에서 지원하는 RFC

NetX Duo Client POP3은 RFC 1939를 준수합니다.
