---
title: 챕터 4 - Azure RTOS NetX Secure DTLS 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX Secure DTLS 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e795a5fa35a4590e508c7fe2eec53f5494809657
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810506"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a>챕터 4: Azure RTOS NetX Secure DTLS 서비스 설명

이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX Secure DTLS 서비스를 알파벳 순서로 설명합니다.

다음 API 설명의 "반환 값" 섹션에서, **BOLD** 의 값은 API 오류 검사를 해제하는 데 사용되는 **NX_SECURE_DISABLE_ERROR_CHECKING** 매크로의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 해제됩니다.

- [nx_secure_dtls_client_session_start](#nx_secure_dtls_client_session_start)
- [nx_secure_dtls_packet_allocate](#nx_secure_dtls_packet_allocate)
- [nx_secure_dtls_psk_add](#nx_secure_dtls_psk_add)
- [nx_secure_dtls_server_create](#nx_secure_dtls_server_create)
- [nx_secure_dtls_server_delete](#nx_secure_dtls_server_delete)
- [nx_secure_dtls_server_local_certificate_add](#nx_secure_dtls_server_local_certificate_add)
- [nx_secure_dtls_server_local_certificate_remove](#nx_secure_dtls_server_local_certificate_remove)
- [nx_secure_dtls_server_notify_set](#nx_secure_dtls_server_notify_set)
- [nx_secure_dtls_server_psk_add](#nx_secure_dtls_server_psk_add)
- [nx_secure_dtls_server_session_send](#nx_secure_dtls_server_session_send)
- [nx_secure_dtls_server_session_start](#nx_secure_dtls_server_session_start)
- [nx_secure_dtls_server_start](#nx_secure_dtls_server_start)
- [nx_secure_dtls_server_stop](#nx_secure_dtls_server_stop)
- [nx_secure_dtls_server_trusted_certificate_add](#nx_secure_dtls_server_trusted_certificate_add)
- [nx_secure_dtls_server_trusted_certificate_remove](#nx_secure_dtls_server_trusted_certificate_remove)
- [nx_secure_dtls_server_x509_client_verify_configure](#nx_secure_dtls_server_x509_client_verify_configure)
- [nx_secure_dtls_server_x509_client_verify_disable](#nx_secure_dtls_server_x509_client_verify_disable)
- [nx_secure_dtls_session_client_info_get](#nx_secure_dtls_session_client_info_get)
- [nx_secure_dtls_session_create](#nx_secure_dtls_session_create)
- [nx_secure_dtls_session_delete](#nx_secure_dtls_session_delete)
- [nx_secure_dtls_session_end](#nx_secure_dtls_session_end)
- [nx_secure_dtls_session_local_certificate_add](#nx_secure_dtls_session_local_certificate_add)
- [nx_secure_dtls_session_local_certificate_remove](#nx_secure_dtls_session_local_certificate_remove)
- [nx_secure_dtls_session_receive](#nx_secure_dtls_session_receive)
- [nx_secure_dtls_session_reset](#nx_secure_dtls_session_reset)
- [nx_secure_dtls_ session_send](#nx_secure_dtls_-session_send)
- [nx_secure_dtls_session_trusted_certificate_add](#nx_secure_dtls_session_trusted_certificate_add)
- [nx_secure_dtls_session_trusted_certificate_remove](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a>nx_secure_dtls_client_session_start

NetX Secure DTLS 클라이언트 세션 시작

### <a name="prototype"></a>프로토타입

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a>Description

이 서비스는 DTLS 클라이언트 세션을 시작하고, 제공된 IP 주소 및 UDP 포트의 서버에 연결하고, 제공된 UDP 소켓을 네트워크 통신에 사용합니다.

nx_secure_dtls_session_create를 사용하여 이 서비스를 호출하려면 먼저 DTLS 세션 제어 블록을 초기화해야 합니다. 또한 DTLS 클라이언트는 nx_secure_dtls_session_trusted_certificate_add를 사용하여 세션에 하나 이상의 신뢰할 수 있는 CA 인증서를 추가하거나 미리 공유한 키를 사용하도록 설정하고 구성해야 합니다.

### <a name="parameters"></a>매개 변수

- **dtls_session** 이전에 초기화된 DTLS 세션 구조에 대한 포인터
- **udp_socket** 초기화된 UDP 소켓으로, 원격 DTLS 서버와의 네트워크 통신을 설정하는 데 사용됩니다.
- **ip_address** 원격 DTLS 서버의 주소를 포함하는 IP 주소 구조에 대한 포인터
- **port** 초기화된 UDP 소켓으로, 원격 DTLS 서버와의 네트워크 통신을 설정하는 데 사용됩니다.
- **wait_option** 연결 시도의 일시 중단 옵션

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 세션에 인증서를 할당했습니다.
- **NX_NOT_CONNECTED** (0x38) 지정된 주소 및 포트에서 서버에 연결할 수 없습니다.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) 받은 TLS/DTLS 메시지 유형이 올바르지 않습니다.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) 원격 호스트에서 제공하는 암호화가 지원되지 않습니다.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) TLS 핸드셰이크 중 메시지 처리가 실패했습니다.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) 들어오는 메시지가 해시 MAC 검사에 실패했습니다.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 기본 TCP 소켓 보내기가 실패했습니다.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 들어오는 메시지의 길이 필드가 올바르지 않습니다.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) 들어오는 ChangeCipherSpec 메시지가 올바르지 않습니다.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) 들어오는 TLS 인증서를 원격 DTLS 서버 식별에 사용할 수 없습니다.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) 원격 호스트에서 제공하는 공개 키 암호가 지원되지 않습니다.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) NetX Secure DTLS 스택에서 지원하는 ciphersuite가 없다고 원격 호스트에서 알렸습니다.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) 받은 DTLS 메시지의 헤더에 알 수 없는 DTLS 버전이 있습니다.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) 받은 DTLS 메시지의 헤더에 알고 있지만 지원되지 않는 DTLS 버전이 있습니다.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) 내부 TLS 패킷을 할당하지 못했습니다.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) 원격 호스트에서 제공한 인증서가 올바르지 않습니다.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) 원격 호스트가 오류를 알리는 경고를 보내고 TLS 세션을 종료했습니다.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) ciphersuite 테이블의 항목에 NULL 함수 포인터가 있습니다.
- **NX_PTR_ERROR** (0x07) 세션, 소켓 또는 주소 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                           &nx_crypto_tls_ciphers,
                                           crypto_metadata,
                                           sizeof(crypto_metadata),
                                           packet_buffer,
                                           sizeof(packet_buffer),
                                           REMOTE_CERT_NUMBER,
                                           remote_certs_buffer,
                                           sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
       Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                      trusted_cert_der,
                                      trusted_cert_der_len,
                                      NX_NULL, 0, NX_NULL, 0,
                                      NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                   &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                  &udp_socket, &server_ip,
                                                  4443,
                                                  NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
      /* Error! */
      return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_session_receive, nx_secure_dtls_session_send
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_packet_allocate"></a>nx_secure_dtls_packet_allocate

NetX Secure DTLS 세션에 대한 패킷 할당

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a>Description

이 서비스는 지정된 NX_PACKET_POOL의 지정된 활성 DTLS 세션에 대한 NX_PACKET을 할당합니다. 애플리케이션에서 이 서비스를 호출하여 DTLS 연결을 통해 보낼 데이터 패킷을 할당해야 합니다. 이 서비스를 호출하려면 먼저 DTLS 세션을 초기화해야 합니다.

패킷 데이터가 채워진 후 DTLS 헤더 및 바닥글 데이터를 추가할 수 있도록 할당된 패킷이 올바르게 초기화됩니다. 그렇지 않으면 이 동작은 *nx_packet_allocate* 와 동일합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** DTLS 세션 인스턴스에 대한 포인터
- **pool_ptr** 패킷을 할당할 NX_PACKET_POOL에 대한 포인터
- **packet_ptr** 새로 할당된 패킷에 대한 출력 포인터
- **wait_option** 패킷 할당의 일시 중단 옵션


### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 패킷을 할당했습니다.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) 기본 패킷을 할당하지 못했습니다.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) 제공된 DTLS 세션이 초기화되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create
- nx_secure_dtls_session_trusted_certificate_add
- nx_secure_dtls_session_send, nx_secure_dtls_session_receive
- nx_secure_dtls_session_end, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_psk_add"></a>nx_secure_dtls_psk_add

NetX Secure DTLS 세션에 미리 공유한 키 추가

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Description

이 서비스는 PSK(미리 공유한 키), 해당 ID 문자열 및 ID 힌트를 DTLS 세션 제어 블록에 추가합니다. PSK는 PSK ciphersuite를 설정하고 사용할 때 디지털 인증서 대신 사용됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **pre_shared_key** 실제 PSK 값
- **psk_length** PSK 값의 길이
- **psk_identity** 이 PSK 값을 식별하는 데 사용되는 문자열
- **identity_length** PSK ID의 길이
- **hint** TLS 서버에서 선택할 PSK 그룹을 나타내는 데 사용되는 문자열
- **hint_length** 힌트 문자열의 길이

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) PSK를 추가했습니다.
- **NX_PTR_ERROR** (0x07) DTLS 세션 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) 다른 PSK를 추가할 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create

## <a name="nx_secure_dtls_server_create"></a>nx_secure_dtls_server_create

NetX Secure DTLS 서버 만들기

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_create(
                NX_SECURE_DTLS_SERVER *server_ptr, NX_IP *ip_ptr,
                UINT port, ULONG timeout, VOID *session_buffer,
                UINT session_buffer_size,
                const NX_SECURE_TLS_CRYPTO *crypto_table,
                VOID *crypto_metadata_buffer, ULONG crypto_metadata_size,
                UCHAR *packet_reassembly_buffer,
                UINT packet_reassembly_buffer_size,
                UINT (*connect_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session,
                              NXD_ADDRESS *ip_address, UINT port),
                UINT (*receive_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session)));

```

### <a name="description"></a>Description

이 서비스는 특정 UDP 포트에서 들어오는 DTLS 요청을 처리하는 DTLS 서버 인스턴스를 만듭니다. UDP가 상태 비저장이기 때문에 여러 클라이언트의 DTLS 요청은 단일 포트에서 들어올 수 있지만 다른 DTLS 세션은 활성 상태입니다. 따라서 서버는 활성 세션을 유지하고 들어오는 메시지를 적절한 처리기로 적절하게 라우팅해야 합니다.

ip_ptr 매개 변수는 DTLS 서버와 연결되어 있는(그리고 NX_SECURE_DTLS_SERVER 제어 블록에 저장된) 내부 UDP 소켓에 사용되는 NX_IP 인스턴스를 가리킵니다. IP 인스턴스와 포트는 nx_secure_dtls_server_start 서비스를 사용하여 서버를 인스턴스화하는 UDP 인터페이스를 정의하는 데 사용됩니다.

세션 버퍼 매개 변수는 DTLS 서버에 대해 가능한 모든 동시 DTLS 세션의 제어 블록을 보관하는 데 사용됩니다. NX_SECURE_DTLS_SESSION 제어 블록 구조 크기의 짝수 배수로 할당해야 합니다.

nx_secure_tls_metadata_size_calculate API를 사용하여 필요한 메타데이터 크기를 계산할 수 있습니다.

packet_reassembly_buffer 매개 변수는 DTLS에서 암호 해독을 위해 UDP 데이터그램을 완전한 DTLS 레코드로 다시 어셈블하는 데 사용되며, 예상되는 최대 DTLS 레코드(DTLS 최대 레코드 크기는 16KB이지만 단일 레코드에 이렇게 많은 데이터를 보내는 애플리케이션은 많지 않음)를 수용할 만큼 충분히 커야 합니다.

connect_notify 콜백 루틴은 새 DTLS 클라이언트가 서버에 연결할 때마다 호출됩니다. 그러면 애플리케이션에서 *nx_secure_dtls_server_session_start* 서비스를 사용하여 DTLS 세션을 시작합니다. 콜백 자체에서 세션을 시작할 수도 있지만, 모든 하위 수준 네트워크 프로세싱을 처리하는 데 사용되는 IP 스레드(예: UDP)를 통해 콜백이 호출될 때에만 콜백을 사용하여 애플리케이션 스레드(또는 애플리케이션에서 만든 전용 DTLS 스레드)에 연결을 알리는 것이 좋습니다. DTLS 세션 매개 변수(콜백에 매개 변수로 제공됨)를 저장하고 다른 스레드에서 nx_secure_dtls_server_session_start를 호출하는 간단한 방법으로 알릴 수 있습니다. connect_notify 콜백은 일반적으로 NX_SUCCESS을 반환해야 합니다.

receive_notify 콜백 루틴은 기존에 설정된 DTLS 세션과 일치하는 DTLS 레코드를 받을 때마다 호출됩니다(원격 호스트 IP 주소와 포트는 기존 세션을 식별하는 데 사용됨). 이는 DTLS를 통해 암호화된 후 전송되는 "애플리케이션 데이터"를 나타냅니다. 애플리케이션은 제공된 DTLS 세션에서 *nx_secure_dtls_session_receive* 서비스를 호출하여 수신한 데이터를 검색해야 합니다. connect_receive 콜백과 마찬가지로, 콜백이 IP 스레드에서 호출될 때 세션을 다른 스레드에 전달하여 메시지 프로세싱을 처리하는 것이 좋습니다. receive_notify 콜백은 일반적으로 NX_SUCCESS을 반환해야 합니다.

### <a name="parameters"></a>매개 변수

- **server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **ip_ptr** 초기화된 NX_IP 제어 블록에 대한 포인터로, DTLS 서버의 네트워크 인터페이스로 사용됩니다.
- **port** DTLS 서버 UDP 소켓이 바인딩된 로컬 UDP 포트입니다.
- **timeout** 네트워크 작업에 사용할 제한 시간 값
- **session_buffer** 이 DTLS 서버 인스턴스에 할당된 모든 NX_SECURE_DTLS_SESSION 인스턴스의 제어 블록을 포함하는 버퍼 공간
- **session_buffer_size** 세션 버퍼의 크기. DTLS 서버에 할당되는 DTLS 세션 수를 결정합니다.
- **crypto_table** 모든 암호화 작업에 사용되는 TLS/DTLS 암호화 테이블 구조에 대한 포인터
- **crypto_metadata_buffer** 암호화 작업 계산 및 상태 정보에 사용되는 버퍼 공간
- **crypto_metadata_size** 메타데이터 버퍼의 크기
- **packet_reassembly_buffer** 암호 해독을 위해 DTLS에서 UDP 데이터를 DTLS 레코드로 다시 어셈블할 때 사용하는 버퍼
- **packet_reassembly_buffer_size** 리어셈블리 버퍼의 크기. 일반적으로 16KB보다 커야 하지만 애플리케이션에 따라 더 작을 수도 있습니다.
- **connect_notify** 원격 DTLS 클라이언트가 이 DTLS 서버에 연결하려고 할 때마다 호출되는 콜백 루틴
- **receive_notify** 기존 DTLS 세션을 통해 애플리케이션 데이터를 받을 때마다 호출되는 콜백

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DTLS 서버를 만들었습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_INVALID_PARAMETERS** (0x4D) 세션, 패킷 리어셈블리 또는 암호화를 위한 버퍼 공간이 부족합니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
    *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE, dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                        device_cert_der_len, NX_NULL, 0,
                        device_cert_key_der, device_cert_key_der_len,
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                           NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                                                   &send_packet, NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data,
        let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done, stop the server
    instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_delete"></a>nx_secure_dtls_server_delete

NetX Secure DTLS 서버에서 사용하는 리소스 해제

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Description

이 서비스는 서버에서 사용하는 내부 UDP 소켓을 포함하여 DTLS 서버 인스턴스에 할당된 리소스를 해제합니다.

### <a name="parameters"></a>매개 변수

- **server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 서버를 삭제했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_STILL_BOUND** (0x42) UDP 소켓이 여전히 바인딩되어 있습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
*ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer, sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);


    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                         NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                        &packet_pool,
                                                        &send_packet,
                                                        NX_IP_PERIODIC_RATE);

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_local_certificate_add"></a>nx_secure_dtls_server_local_certificate_add

NetX Secure DTLS 서버에 로컬 서버 ID 인증서 추가

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a>Description

이 서비스는 DTLS 서버 인스턴스에 로컬 서버 ID 인증서를 추가합니다. 대체 인증 메커니즘(예: 미리 공유한 키)을 사용하지 않는 한, 클라이언트에서 DTLS 서버에 연결하려면 하나 이상의 ID 인증서가 필요합니다.

cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다. 이렇게 하면 DTLS 서버 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다. X.509 서버 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.

### <a name="parameters"></a>매개 변수

- **server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **certificate** 이전에 초기화된 X.509 인증서 구조에 대한 포인터
- **cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DTLS 서버에 인증서를 추가했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_INVALID_PARAMETERS** (0x4D) 인증서 ID 0이 전달되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

*보다 완전한 예제는 *nx_secure_dtls_server_create* 에 대한 참조를 확인하세요.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                            certificate_der_data,
                            sizeof(certificate_der_data),
                            NX_NULL, 0,
                            certificate_key_der_data,
                            sizeof(certificate_key_der_data),
                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_local_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_local_certificate_remove"></a>nx_secure_dtls_server_local_certificate_remove

NetX Secure DTLS 서버에서 로컬 서버 ID 인증서 제거

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a>Description

이 서비스는 DTLS 서버 인스턴스에서 로컬 서버 ID 인증서를 제거합니다. 대체 인증 메커니즘(예: 미리 공유한 키)을 사용하지 않는 한, 클라이언트에서 DTLS 서버에 연결하려면 하나 이상의 ID 인증서가 필요합니다.

제거할 인증서는 해당 X.509 일반 이름 또는 *nx_secure_dtls_server_local_certificate_add* 호출에서 할당된 숫자 cert_id를 통해 식별할 수 있습니다. cert_id는 인증서 식별에만 사용되며 애플리케이션에서 유지 관리합니다. 숫자 인증서 식별자 대신 일반 이름을 사용하는 경우에는 cert_id 매개 변수를 0으로 설정해야 합니다.

> [!NOTE]
> DTLS 핸드셰이크를 처리하는 동안 인증서를 제거하면 예기치 않은 동작이 발생합니다. *nx_secure_dtls_server_stop* 서비스는 인증서를 제거하기 전에 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **common_name** 제거할 인증서의 X.509 CommonName. 사용할 경우 cert_id를 0으로 전달해야 합니다.
- **common_name_length** common_name 문자열의 길이(바이트)
- **cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자 사용할 경우 common_name 매개 변수에 NX_NULL를 전달해야 합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DTLS 서버에서 인증서를 제거했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 지정된 DTLS 서버에서 cert_id 또는 common_name과 일치하는 인증서를 찾을 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        certificate_der_data,
                                        sizeof(certificate_der_data),
                                        NX_NULL, 0, certificate_key_der_data,
                                        sizeof(certificate_key_der_data),
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                     &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);

    /* At some point in the future we decide to remove the certificate we added.
    We can use the certificate identifier we passed into the call to
    nx_secure_dtls_local_certificate_add (value = 1); */
    status = nx_secure_dtls_server_local_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_notify_set"></a>nx_secure_dtls_server_notify_set

NetX Secure DTLS 서버에 선택적 알림 콜백 루틴 할당

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a>Description

이 서비스를 사용하여 DTLS 서버에 선택적 알림 콜백 루틴을 추가할 수 있습니다. 콜백 매개 변수 중 하나만 사용하려면 콜백 매개 변수 중 하나를 NX_NULL로 전달하면 됩니다.

disconnect_notify 콜백은 원격 클라이언트가 DTLS 세션을 종료할 때 호출됩니다. dtls_session 매개 변수는 닫힌 세션 인스턴스입니다. 콜백은 일반적으로 NX_SUCCESS를 반환해야 합니다.

error_notify 콜백은 DTLS 오류가 발생하거나 시간이 초과될 때마다 호출됩니다. dtls_session 매개 변수는 오류가 발생한 세션 인스턴스이고, error_code는 문제를 일으킨 오류의 숫자 상태 코드입니다.

반환될 수 있는 오류 코드 목록은 부록 A) NetX Secure 반환/오류 코드를 참조하세요. 콜백은 일반적으로 NX_SUCCESS를 반환해야 합니다.

### <a name="parameters"></a>매개 변수

- **server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **disconnect_notify** 원격 클라이언트 호스트가 DTLS 세션을 닫을 때마다 호출되는 콜백 루틴
- **error_notify** DTLS에서 오류 또는 시간 초과가 발생할 때마다 호출되는 콜백 루틴

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 콜백 루틴을 할당했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

UINT disconnect_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
NXD_ADDRESS client_ip_addr;
UINT client_port;
UINT local_port;

    /* We have received a disconnection notice (CloseNotify message) from a
       remote client. Application can use the dtls_session parameter for any
       desired processing. */

    /* See what client disconnected by extracting its IP address and port.
       NOTE: depending on how the session ended, the client information may
             no longer be available. */
    status  = nx_secure_dtls_session_client_info_get(dtls_session,
                                                    &ip_addr,
                                                    &client_port,
                                                    &local_port);

    return(NX_SUCCESS);
}

UINT error_notify(NX_SECURE_DTLS_SESSION *dtls_session, UINT error_code)
{
    /* The DTLS server has encountered an error or timeout condition. We
    can use the error_code parameter to determine the error and we
    can insect the dtls_session for more information. */

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Other setup (e.g. certificates) goes here … */

    status = nx_secure_dtls_server_notify_set(&dtls_server, disconnect_notify,
                                                                 error_notify);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop

## <a name="nx_secure_dtls_server_psk_add"></a>nx_secure_dtls_server_psk_add

NetX Secure DTLS 서버에 미리 공유한 키 추가

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a>Description

이 서비스는 PSK(미리 공유한 키), 해당 ID 문자열 및 ID 힌트를 DTLS 서버 제어 블록에 추가합니다. PSK는 PSK ciphersuite를 설정하고 사용할 때 디지털 인증서 대신 사용됩니다.

추가된 PSK는 nx_secure_dtls_server_create 호출에 지정된 세션 버퍼를 통해 DTLS 서버에 할당된 모든 DTLS 세션에서 복제됩니다.

### <a name="parameters"></a>매개 변수

- **server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **pre_shared_key** 실제 PSK 값
- **psk_length** PSK 값의 길이
- **psk_identity** 이 PSK 값을 식별하는 데 사용되는 문자열
- **identity_length** PSK ID의 길이
- **hint** TLS 서버에서 선택할 PSK 그룹을 나타내는 데 사용되는 문자열
- **hint_length** 힌트 문자열의 길이

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) PSK를 추가했습니다.
- **NX_PTR_ERROR** (0x07) DTLS 서버 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) 다른 PSK를 추가할 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_psk_add, nx_secure_dtls_server_create

## <a name="nx_secure_dtls_server_session_send"></a>nx_secure_dtls_server_session_send

NetX Secure DTLS 서버를 사용하여 설정된 DTLS 세션을 통해 데이터 보내기

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a>Description

이 서비스는 설정된 DTLS 서버 세션을 통해 원격 DTLS 클라이언트 호스트로 데이터 패킷을 보냅니다. 사용되는 세션은 nx_secure_dtls_session_create에 제공된 receive_notify 콜백 루틴에서 가져옵니다.

패킷에 제공된 데이터(*nx_secure_dtls_packet_allocate* 를 사용하여 할당해야 함)는 DTLS 세션 암호화 매개 변수 및 루틴을 사용하여 암호화된 후 DTLS 서버 내부 UDP 포트를 통해 연결된 클라이언트의 IP 주소 및 포트에 전송됩니다(DTLS 세션에 저장됨).

### <a name="parameters"></a>매개 변수

- **session_ptr** 애플리케이션에서 제공하는 receive_notify 콜백 루틴에서 얻은 DTLS 세션 인스턴스에 대한 포인터
- **packet_ptr** 이전에 할당되어 애플리케이션 데이터로 채워진 NX_PACKET 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DTLS 서버를 만들었습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 기본 UDP 전송 작업에서 오류가 발생했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;


/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key
    and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        device_cert_der,
                                        device_cert_der_len,
                                        NX_NULL,
                                        0, device_cert_key_der,
                                        device_cert_key_der_len,
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

}

/* If not processing connections or received data, let the thread sleep. */
if(!connect_flag && !receive_flag)
{
    tx_thread_sleep(100);
}
    }

    /* Server processing is done, stop the server instance
    from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create
- nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_session_start"></a>nx_secure_dtls_server_session_start

NetX Secure DTLS 서버에서 DTLS 세션 시작

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a>Description

이 서비스는 원격 DTLS 클라이언트가 서버에 연결하여 DTLS 연결을 요청할 때 서버 쪽 DTLS 핸드셰이크를 수행하여 DTLS 서버 세션을 시작합니다.

DTLS 세션은 nx_secure_dtls_server_create에 제공된 connect_notify 콜백 루틴에서 가져옵니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** DTLS 서버 connect_notify 콜백에서 가져온 DTLS 세션 인스턴스에 대한 포인터
- **wait_option** 네트워크 작업에 사용할 ThreadX 대기 값

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DTLS 서버를 만들었습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) DTLS 핸드셰이크 패킷을 할당할 수 없습니다(패킷 풀이 비어 있음).
- **NX_SECURE_TLS_INVALID_PACKET** (0x104) 수신한 데이터가 유효한 DTLS 레코드가 아닙니다.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) DTLS 레코드를 올바르게 해시하지 못했습니다(암호화 오류).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) 암호화 패딩 검사가 실패했습니다.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) DTLS 핸드셰이크 중에 원격 호스트에서 경고를 받았습니다.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) DTLS 핸드셰이크 중에 인식할 수 없는 메시지를 받았습니다.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 받은 DTLS 레코드의 길이가 올바르지 않습니다.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) 받은 ClientHello가 DTLS ciphersuite를 지원하지 않습니다.
- **NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) 받은 ClientHello의 압축 방법을 알 수 없습니다.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) 일반적인(지정되지 않은) 핸드셰이크 오류가 발생했습니다. 대부분 확장 처리 문제로 발생합니다.
- **NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) DTLS 핸드셰이크 중에 아직 지원되지 않는 기능이 호출되었습니다.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) 알 수 없는 ciphersuite가 발생했습니다(내부 암호화 오류가 표시됨).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) 받은 DTLS 레코드의 DTLS 버전이 일치하지 않습니다.
- **NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) DTLS 핸드셰이크 해시의 유효성을 검사하지 못했습니다. 세션이 잘못되었습니다.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 내부 UDP 전송이 실패했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
* DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len, NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                    &packet_pool, &send_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done,
    stop the server instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_start"></a>nx_secure_dtls_server_start

구성된 UDP 포트에서 수신 대기하는 NetX Secure DTLS 서버 인스턴스 시작

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a>Description

이 서비스는 DTLS 서버를 시작합니다. 호출이 반환되면 서버가 활성 상태이고 DTLS 클라이언트에서 들어오는 요청을 처리하기 시작합니다. 서버 인스턴스는 *nx_secure_dtls_server_create* 서비스를 사용하여 구성되어야 합니다.

> [!NOTE]
> 이 서비스는 내부 DTLS 서버 UDP 포트를 구성된 로컬 포트에 바인딩하므로, 발생하는 대부분의 문제는 UDP 통신 및 네트워크 구성과 관련이 있습니다.

### <a name="parameters"></a>매개 변수

- **server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 서버를 시작했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_NOT_ENABLED** (0x14) UDP가 사용하도록 설정되지 않았습니다.
- **NX_NO_FREE_PORTS** (0x45) 사용 가능한 UDP 포트가 없습니다.
- **NX_INVALID_PORT** (0x46) UDP 포트가 올바르지 않습니다.
- **NX_ALREADY_BOUND** (0x22) UDP 포트가 이미 바인딩되어 있습니다.
- **NX_PORT_UNAVAILABLE** (0x23) UDP 포트를 사용할 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                &send_packet, NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
                (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_stop, nx_secure_dtls_server_create
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive
- nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_stop"></a>nx_secure_dtls_server_stop

활성 NetX Secure DTLS 서버 인스턴스 중지

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Description

이 서비스는 구성된 UDP 포트에서 DTLS 서버가 수신 대기하는 것을 중지하고, 연결된 모든 DTLS 세션을 초기화하고, 진행 중인 DTLS 통신을 중지합니다.

### <a name="parameters"></a>매개 변수

- **server_ptr** 활성 DTLS 서버 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 서버를 중지했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* We have exited the processing loop, stop the server. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive
- nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a>nx_secure_dtls_server_trusted_certificate_add

NetX Secure DTLS 서버에 신뢰할 수 있는 CA 인증서 추가

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Description

이 서비스는 DTLS 서버 인스턴스에 신뢰할 수 있는 CA 또는 중간 CA 인증서를 추가하고 모든 내부 DTLS 서버 세션에 할당합니다. *nx_secure_dtls_server_x509_client_verify_configure* 를 사용하여 X.509 클라이언트 인증서 인증을 사용하도록 설정한 경우에만 필요합니다. 추가된 인증서는 들어오는 클라이언트 X.509 인증서를 확인하는 데 사용됩니다.

cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다. 이렇게 하면 DTLS 서버 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다. X.509 서버 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.

### <a name="parameters"></a>매개 변수

- **server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **certificate** 이전에 초기화된 X.509 인증서 구조에 대한 포인터
- **cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DTLS 서버에 인증서를 추가했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_INVALID_PARAMETERS** (0x4D) 인증서 ID 0이 전달되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

*보다 완전한 예제는 *nx_secure_dtls_server_create* 에 대한 참조를 확인하세요.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0, NX_NULL,
                                            0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add trusted CA certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_local_certificate_add
- nx_secure_dtls_server_trusted_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a>nx_secure_dtls_server_trusted_certificate_remove

NetX Secure DTLS 서버에서 신뢰할 수 있는 CA 인증서 제거

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a>Description

이 서비스는 DTLS 서버 인스턴스에서 신뢰할 수 있는 CA 인증서를 제거합니다. 신뢰할 수 있는 CA 인증서는 *nx_secure_dtls_server_x509_client_verify_configure* 를 호출하여 X.509 클라이언트 인증서 확인을 사용하도록 설정한 DTLS 서버에만 필요합니다.

제거할 인증서는 X.509 일반 이름 또는 *nx_secure_dtls_server_trusted_certificate_add* 호출에서 할당된 숫자 cert_id를 통해 식별할 수 있습니다. cert_id는 인증서 식별에만 사용되며 애플리케이션에서 유지 관리합니다. 숫자 인증서 식별자 대신 일반 이름을 사용하는 경우에는 cert_id 매개 변수를 0으로 설정해야 합니다.

> [!NOTE]
> DTLS 핸드셰이크를 처리하는 동안 인증서를 제거하면 예기치 않은 동작이 발생할 수 있습니다. *nx_secure_dtls_server_stop* 서비스는 인증서를 제거하기 전에 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **common_name** 제거할 인증서의 X.509 CommonName. 사용할 경우 cert_id를 0으로 전달해야 합니다.
- **common_name_length** common_name 문자열의 길이(바이트)
- **cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자 사용할 경우 common_name 매개 변수에 NX_NULL를 전달해야 합니다.


### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DTLS 서버에서 인증서를 제거했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 지정된 DTLS 서버에서 cert_id 또는 common_name과 일치하는 인증서를 찾을 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                                    certificate_der_data,
                                                    sizeof(certificate_der_data),
                                                    NX_NULL, 0, NX_NULL, 0,
                                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                       &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);


/* At some point in the future we decide to remove the certificate we added. We can
       use the certificate identifier we passed into the call to
       nx_secure_dtls_trusted_certificate_add (value = 1); */
    status = nx_secure_dtls_server_trusted_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_trusted_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a>nx_secure_dtls_server_x509_client_verify_configure

클라이언트 인증서를 요청하고 확인하도록 NetX Secure DTLS 서버 구성

### <a name="prototype"></a>프로토타입

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a>Description

이 서비스는 DTLS 클라이언트 인증서를 요청하고 확인하도록 DTLS 서버를 구성합니다. 이 선택적 기능은 클라이언트 인증에 다른 메커니즘(예: 미리 공유한 키) 대신 X.509 인증서가 필요한 경우에 사용됩니다.

> [!IMPORTANT]
> *이 서비스를 사용하여 클라이언트 인증서를 확인하도록 DTLS 서버를 구성한 경우 nx_secure_dtls_server_trusted_certificate_add를 사용하여 신뢰할 수 있는 CA 인증서를 하나 이상 서버에 추가해야 합니다. 그렇지 않으면 서버는 신뢰할 수 있는 저장소와 대조하여 클라이언트 인증서를 확인할 수 없기 때문에 들어오는 모든 클라이언트 연결을 거부합니다.*

이 서비스를 호출하면 DTLS 서버 인스턴스가 (시작된 후) DTLS 핸드셰이크의 일부로 클라이언트 인증서를 요청합니다. ID 인증서(및 해당하는 경우 연결된 인증서 체인)를 사용하여 클라이언트를 적절하게 구성하면 DTLS 서버에서는 클라이언트 인증서 데이터를 처리하기 위한 메모리 할당을 요구합니다. 이 메모리는 *certs_buffer* 매개 변수로 전달됩니다.

certs_buffer는 DTLS 클라이언트에서 예상되는 가장 큰 인증서 체인을 수용할 수 있는 크기에 *DTLS 서버 세션 수를 곱한 값* 이어야 합니다. 버퍼는 클라이언트 인증서 체인에서 예상되는 최대 인증서 수를 나타내는 *certs_per_session* 매개 변수를 통해 사용 가능한 세션 간에 분할됩니다. 또한 버퍼는 인증서 데이터를 구문 분석하는 데 사용되는 NX_SECURE_X509_CERT 데이터 구조를 위한 공간을 제공해야 합니다.

적절한 버퍼 크기는 다음 수식으로 계산할 수 있습니다.

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- DTLS 세션 수는 nx_secure_dtls_server_create에 전달되는 세션 버퍼의 크기에 따라 결정됩니다.
- certs_per_session은 클라이언트 인증서 체인에서 예상되는 최대 인증서 수로 설정해야 합니다.
- 예상되는 최대 인증서 크기는 애플리케이션, 키 크기 및 기타 요인에 따라 다르지만 일반적으로 2KB면 충분합니다.

### <a name="parameters"></a>매개 변수

- **server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **certs_per_session** 각 DTLS 서버 세션에 할당할 인증서 수
- **certs_buffer** 들어오는 인증서 데이터의 버퍼 공간
- **buffer_size** 인증서 버퍼의 크기

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) X.509 클라이언트 확인을 구성했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_INVALID_PARAMETERS** (0x4D) 인증서 저장소가 올바르지 않습니다(DTLS 서버 인스턴스가 초기화되었나요?).

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                                    sizeof(certificate_der_data),
                                    NX_NULL, 0,
                                    NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_x509_client_verify_disable
- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_trusted_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a>nx_secure_dtls_server_x509_client_verify_disable

NetX Secure DTLS 서버에 클라이언트 X.509 인증서 확인을 사용하지 않도록 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Description

이 서비스는 DTLS 서버에서 X.509 클라이언트 인증서 확인을 사용하지 않도록 설정합니다. X.509 클라이언트 인증서 확인이 사용되지 않으면 이 서비스는 아무 영향도 미치지 않습니다.

> [!NOTE]
> 활성 DTLS 서버 인스턴스에서 클라이언트 인증을 사용하지 않도록 설정하면 예기치 않은 동작이 발생할 수 있습니다. 서버 상태를 변경하기 전에 nx_secure_dtls_server_stop 서비스를 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) X.509 클라이언트 인증을 사용하지 않도록 설정했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                        sizeof(certificate_der_data), NX_NULL, 0,
                        NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before changing state. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* Disable X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_disable(&dtls_server);

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_x509_client_verify_configure
- nx_secure_dtls_server_start, nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_trusted_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_client_info_get"></a>nx_secure_dtls_session_client_info_get

DTLS 서버 세션에서 원격 클라이언트 정보 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a>Description

이 서비스는 특정 DTLS 서버 세션에 연결된 DTLS 클라이언트에 대한 네트워크 정보를 반환합니다. 반환된 정보는 원격 클라이언트의 IP 주소 및 UDP 포트와 클라이언트가 연결된 로컬 서버 포트로 구성됩니다.

일반적으로 DTLS 세션 인스턴스는 DTLS 알림 콜백 루틴(예: nx_secure_dtls_server_create에 전달된 connect_notify 또는 receive_notify 콜백) 중 하나를 호출할 때 가져온 것입니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 활성 DTLS 서버 세션 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 서버를 삭제했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_INVALID_SOCKET** (0x13) 연결된 UDP 소켓이 올바르지 않습니다(세션이 초기화되었나요?).
- **NX_NOT_CONNECTED** (0x38) UDP 소켓이 연결되지 않았습니다. 클라이언트 연결이 끊어졌거나 아직 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array
   or list in case a new connection is
   attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
                                                            *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    NXD_ADDRESS client_ip;
    UINT client_port, server_port;

    /* Get DTLS client information which can be used in filtering or associating
       the DTLS session with application data (e.g. a session pointer table). */
    status = nx_secure_dtls_session_client_info_get(dtls_session, &client_ip,
   &client_port, &server_port);

    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_server_start, nx_secure_dtls_server_stop
- nx_secure_dtls_server_create, nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_session_create"></a>nx_secure_dtls_session_create

NetX Secure DTLS 세션 만들기 및 구성

### <a name="prototype"></a>프로토타입

```C
UINT nx_secure_dtls_session_create(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        VOID *metadata_buffer, ULONG metadata_size,
                        UCHAR *packet_reassembly_buffer,
                        UINT packet_reassembly_buffer_size,
                        UINT certs_number,
                        UCHAR *remote_certificate_buffer,
                        ULONG remote_certificate_buffer_size));

```

### <a name="description"></a>Description

이 서비스는 DTLS 세션을 만들고 구성합니다. DTLS 서버 세션이 DTLS 서버 메커니즘을 통해 관리되므로 이 서비스는 일반적으로 DTLS 클라이언트 세션을 만드는 데 사용되지만(*nx_secure_dtls_server_create* 참조), 애플리케이션에서 단일 독립 실행형 DTLS 서버 세션 인스턴스를 만들어야 하는 경우가 있습니다. 이 경우 이 서비스를 사용할 수 있습니다<sup>7</sup>.

매개 변수는 DTLS 세션을 인스턴스화하는 데 필요한 정보 및 메모리 할당을 구성합니다. crypto_table 매개 변수는 TLS/DTLS 암호화 및 인증에 필요한 모든 암호화 루틴을 포함하는 TLS 테이블입니다. metadata_buffer는 암호화 계산에 사용되고(NetX Secure TLS 사용자 가이드의 nx_secure_tls_metadata_size_calculate 참조), packet_reassembly_buffer는 암호를 해독하기 위해 UDP 데이터그램을 완전한 DTLS 레코드로 리어셈블하는 데 사용됩니다.

certs_number 및 remote_certificate_buffer는 DTLS 클라이언트에 필요하며, 이 클라이언트는 들어오는 DTLS 서버 인증서 체인을 저장하고 처리하기 위한 공간이 필요합니다. 버퍼는 연결할 서버에서 예상되는 최대 인증서 체인 크기를 수용할 수 있어야 합니다. 버퍼는 예상되는 인증서 수(certs_number 매개 변수)만큼 분할되며 인증서마다 하나의 NX_SECURE_X509_CERT 구조를 저장할 수 있을 만큼 커야 합니다. 버퍼 크기는 다음 수식을 사용하여 결정할 수 있습니다.

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- certs_number는 서버 인증서 체인에서 예상되는 최대 인증서 수입니다.
- 최대 인증서 크기는 사용되는 키의 크기와 인증서의 정보에 따라 다르지만 일반적으로 2KB면 충분합니다.

**7** 이 루틴을 사용하여 DTLS 서버 세션을 만드는 방법은 권장하지 않으며 몇 가지 제한 사항이 있습니다. 주된 문제는 세션이 추가 클라이언트 연결을 정상적으로 처리하지 않는다는 것입니다. UDP는 비연결형이므로 이전 DTLS 세션이 아직 활성 상태인 경우 두 번째 클라이언트가 서버의 UDP 포트에 데이터를 합법적으로 전송할 수 있으므로 서버 세션이 오류와 함께 종료될 수 있습니다.

### <a name="parameters"></a>매개 변수

- **dtls_session** 초기화되지 않은 DTLS 세션 구조에 대한 포인터
- **crypto_table** 모든 암호화 작업에 사용되는 TLS/DTLS 암호화 테이블 구조에 대한 포인터
- **crypto_metadata_buffer** 암호화 작업 계산 및 상태 정보에 사용되는 버퍼 공간
- **crypto_metadata_size** 메타데이터 버퍼의 크기
- **packet_reassembly_buffer** 암호 해독을 위해 DTLS에서 UDP 데이터를 DTLS 레코드로 다시 어셈블할 때 사용하는 버퍼
- **packet_reassembly_buffer_size** 리어셈블리 버퍼의 크기. 일반적으로 16KB보다 커야 하지만 애플리케이션에 따라 더 작을 수도 있습니다.
- **certs_number** 원격 서버의 인증서 체인에서 예상되는 최대 인증서 수
- **remote_certificate_buffer** 들어오는 인증서 데이터의 버퍼 공간
- **remote_certificate_buffer_size** 인증서 버퍼의 크기


### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 세션을 만들었습니다.
- **NX_PTR_ERROR** (0x07) 세션 또는 버퍼 포인터가 올바르지 않습니다.
- **NX_INVALID_PARAMETERS** (0x4D) 패킷 리어셈블리, 인증서 또는 암호화를 위한 버퍼 공간이 부족합니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
    &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                            &udp_socket, &server_ip,
                                            4443,
                                            NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session,
                                            &receive_packet,
                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive
- nx_secure_dtls_session_send

## <a name="nx_secure_dtls_session_delete"></a>nx_secure_dtls_session_delete

NetX Secure DTLS 세션에서 사용하는 리소스 해제

### <a name="prototype"></a>프로토타입

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a>Description

이 서비스는 DTLS 세션을 삭제하고, 생성 시 할당된 모든 리소스를 해제합니다.

### <a name="parameters"></a>매개 변수

- **dtls_session** 이전에 초기화된 DTLS 세션 구조에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 세션을 삭제했습니다.
- **NX_PTR_ERROR** (0x07) 세션 또는 버퍼 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                        trusted_cert_der,
                                        trusted_cert_der_len,
                                        NX_NULL, 0, NX_NULL, 0,
                                        NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                    &udp_socket,
                                                    &server_ip, 4443,
                                                    NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                &receive_packet,
                                                NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_end"></a>nx_secure_dtls_session_end

활성 NetX Secure DTLS 세션 종료

### <a name="prototype"></a>프로토타입

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a>Description

이 서비스는 원격 호스트에 TLS/DTLS CloseNotify 경고를 보내서 활성 DTLS 세션을 종료합니다. 이전에 nx_secure_dtls_session_send를 호출할 때 사용한 IP 주소 및 포트를 사용합니다.

### <a name="parameters"></a>매개 변수

- **dtls_session** 이전에 초기화된 DTLS 세션 구조에 대한 포인터
- **wait_option** 네트워크 작업에 사용할 ThreadX 대기 값

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 세션을 삭제했습니다.
- **NX_PTR_ERROR** (0x07) 세션 또는 버퍼 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) CloseNotify 경고에 대한 패킷을 할당할 수 없습니다.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) 내부 오류일 가능성이 높습니다. 암호화 루틴이 인식되지 않습니다.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 기본 UDP 전송이 실패했습니다.
- **NX_IP_ADDRESS_ERROR** (0x21) 원격 호스트 IP 주소에 오류가 있습니다.
- **NX_NOT_BOUND** (0x24) 기본 UDP 소켓이 포트에 바인딩되지 않았습니다.
- **NX_INVALID_PORT** (0x46) UDP 포트가 올바르지 않습니다.
- **NX_PORT_UNAVAILABLE** (0x23) UDP 포트를 사용할 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session,
                                        NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

    }

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_local_certificate_add"></a>nx_secure_dtls_session_local_certificate_add

NetX Secure DTLS 세션에 로컬 ID 인증서 추가

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a>Description

이 서비스는 DTLS 세션 인스턴스에 로컬 ID 인증서를 추가합니다. 일반적으로 DTLS 클라이언트 세션이 원격 서버 호스트에 ID 인증서를 제공해야 하는 경우에 이 서비스를 사용합니다. DTLS에 대한 선택적 구성이므로 일반적으로 DTLS 클라이언트에 인증서가 꼭 필요하지는 않습니다. ID 인증서는 연결된 프라이빗 키가 필요합니다.

cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다. 이렇게 하면 DTLS 인증서 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다. X.509 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **certificate** 이전에 초기화된 X.509 인증서 구조에 대한 포인터
- **cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DTLS 세션에 인증서를 추가했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_INVALID_PARAMETERS** (0x4D) 인증서 ID 0이 전달되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

*보다 완전한 예제는 *nx_secure_dtls_session_create* 에 대한 참조를 확인하세요.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity
certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

/* Create a TLS session for our socket. Ciphers and metadata defined
   elsewhere. See nx_secure_tls_session_create reference for more
   information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
{
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
}

/* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

/* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                              &certificate, 1);

    /* Initialize local server identity certificate with key and
    add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                        certificate_der_data,
                        sizeof(certificate_der_data),
                        NX_NULL, 0,
                        certificate_key_der_data,
                        sizeof(certificate_key_der_data),
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                    &certificate, 1);

/* Set up IP address of remote host. */
server_ip.nxd_ip_version = NX_IP_VERSION_V4;
server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


/* Now we can start the DTLS session as normal. */
status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                    &udp_socket, &server_ip, 4443,
                                    NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_start
- nx_secure_dtls_session_local_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_local_certificate_remove"></a>nx_secure_dtls_session_local_certificate_remove

NetX Secure DTLS 세션에서 로컬 ID 인증서 제거

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Description

이 서비스는 nx_secure_dtls_session_local_certificate_add를 사용하여 인증서를 추가할 때 할당된 인증서 ID 번호 또는 X.509 CommonName 필드를 사용하여 DTLS 세션 인스턴스에서 로컬 ID 인증서를 제거합니다.

인증서를 매칭하기 위해 common_name을 사용하는 경우 cert_id 매개 변수를 0으로 설정해야 합니다. cert_id를 사용하는 경우에는 common_name에 NX_NULL 값을 전달해야 합니다.

cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다. 이렇게 하면 DTLS 인증서 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다. X.509 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **common_name** 매칭할 CommonName 문자열에 대한 포인터
- **common_name_length** common_name 문자열의 길이
- **cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DTLS 세션에서 인증서를 제거했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 지정된 DTLS 세션에서 cert_id 또는 common_name과 일치하는 인증서를 찾을 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

*보다 완전한 예제는 *nx_secure_dtls_session_create* 에 대한 참조를 확인하세요.

```C

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

        /* Initialize local server identity certificate with key
        and add to server. */
        status = nx_secure_x509_certificate_initialize(&certificate,
                                certificate_der_data,
                                sizeof(certificate_der_data),
                                NX_NULL, 0,
                                certificate_key_der_data,
                                sizeof(certificate_key_der_data),
                                NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

        /* Add local server identity certificate to DTLS server with ID of 1. */
        status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                            &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
        &udp_socket, &server_ip, 4443,
        NX_IP_PERIODIC_RATE);

        /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
        status = nx_secure_dtls_session_local_certificate_remove(&client_dtls_session,
                                                                NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_start
- nx_secure_dtls_session_local_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_receive"></a>nx_secure_dtls_session_receive

설정된 NetX Secure DTLS 세션을 통해 애플리케이션 데이터 받기

### <a name="prototype"></a>프로토타입

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a>Description

이 서비스는 활성 DTLS 세션에서 받은 애플리케이션 데이터를 반환합니다. DTLS 세션은 DTLS 서버 세션(DTLS 서버 인스턴스에서 관리) 또는 DTLS 클라이언트 세션입니다. 반환된 패킷은 아무 NX_PACKET API 서비스를 사용하여 처리할 수 있습니다(자세한 내용은 NetX 설명서 참조).

### <a name="parameters"></a>매개 변수

- **dtls_session** 이전에 초기화된 DTLS 세션 구조에 대한 포인터
- **packet_ptr_ptr** 반환 패킷의 NX_PACKET 포인터에 대한 포인터
- **wait_option** 네트워크 작업에 사용할 ThreadX 대기 값

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 애플리케이션에서 데이터 패킷을 받았습니다.
- **NX_PTR_ERROR** (0x07) 세션 또는 패킷 포인터가 올바르지 않습니다.
- **NX_NOT_ENABLED** (0x14) UDP가 사용하도록 설정되지 않았습니다.
- **NX_NOT_BOUND** (0x24) UDP 소켓이 포트에 바인딩되지 않았습니다.
- **NX_SECURE_TLS_INVALID_PACKET** (0x104) 수신한 데이터가 유효한 DTLS 레코드가 아닙니다.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) DTLS 레코드를 올바르게 해시하지 못했습니다(암호화 오류).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) 암호화 패딩 검사가 실패했습니다.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) 원격 호스트에서 경고를 받았습니다.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) 인식할 수 없는 메시지를 받았습니다.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 받은 DTLS 레코드의 길이가 올바르지 않습니다.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) 알 수 없는 ciphersuite가 발생했습니다(내부 암호화 오류가 표시됨).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) 받은 DTLS 레코드의 DTLS 버전이 일치하지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_end
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_reset"></a>nx_secure_dtls_session_reset

NetX Secure DTLS 세션 인스턴스의 데이터 지우기

### <a name="prototype"></a>프로토타입

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a>Description

이 서비스는 DTLS 세션을 초기화하고, 모든 임시 암호화 데이터를 지우고, 구조를 새 세션에 다시 사용할 수 있도록 허용합니다. nx_secure_dtls_session_create를 반복적으로 호출할 필요가 없도록 영구 데이터(예: 인증서 저장소)는 유지됩니다.

### <a name="parameters"></a>매개 변수

- **dtls_session** 이전에 초기화된 DTLS 세션 구조에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 세션을 초기화했습니다.
- **NX_PTR_ERROR** (0x07) 세션 또는 버퍼 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_reset(&client_dtls_session);

    /* A new session can now be started using the same structure. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,



    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_-session_send"></a>nx_secure_dtls_ session_send

DTLS 세션을 통해 데이터 보내기

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a>Description

이 서비스는 설정된 DTLS 세션을 통해 데이터 패킷을 지정된 IP 주소 및 포트의 원격 DTLS 호스트에 보냅니다. 활성 DTLS 클라이언트 세션이 사용됩니다. IP 주소와 포트는 UDP의 상태 비저장 특성 때문에 제공되지만 일반적으로 nx_secure_dtls_session_start에서 세션을 시작하는 데 사용되는 주소 및 포트와 일치해야 합니다.

패킷에 제공된 데이터(*nx_secure_dtls_packet_allocate* 를 사용하여 할당해야 함)는 DTLS 세션 암호화 매개 변수 및 루틴을 사용하여 암호화된 후 다음 DTLS 세션의 UDP 소켓을 통해 원격 호스트로 전송됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 활성 DTLS 클라이언트 세션 인스턴스에 대한 포인터
- **packet_ptr** 이전에 할당되어 애플리케이션 데이터로 채워진 NX_PACKET 인스턴스에 대한 포인터
- **ip_address** 원격 호스트의 IP 주소를 포함하는 NXD_ADDRESS 구조에 대한 포인터
- **port** 원격 호스트의 UDP 포트

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 패킷을 보냈습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 기본 UDP 전송 작업에서 오류가 발생했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
    /* Error! */
    return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a>nx_secure_dtls_session_trusted_certificate_add

NetX Secure DTLS 세션에 신뢰할 수 있는 CA 인증서 추가

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Description

이 서비스는 DTLS 세션 인스턴스에 신뢰할 수 있는 CA 또는 중간 CA X.509 인증서를 추가합니다. 대체 인증 메커니즘(예: 미리 공유한 키)을 사용하지 않는 한, DTLS 클라이언트에서 원격 서버 인증서의 유효성을 검사하려면 신뢰할 수 있는 인증서가 하나 이상 필요합니다. 신뢰할 수 있는 인증서에는 일반적으로 프라이빗 키가 없습니다.

cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다. 이렇게 하면 DTLS 인증서 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다. X.509 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **certificate** 이전에 초기화된 X.509 인증서 구조에 대한 포인터
- **cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DTLS 세션에 인증서를 추가했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_INVALID_PARAMETERS** (0x4D) 인증서 ID 0이 전달되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

*보다 완전한 예제는 *nx_secure_dtls_session_create* 에 대한 참조를 확인하세요.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                            trusted_cert_der,
                                            trusted_cert_der_len,
                                            NX_NULL, 0, NX_NULL, 0,
                                            NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the trusted store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                      &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);

    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
         &udp_socket, &server_ip, 4443,
         NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_start
- nx_secure_dtls_session_trusted_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a>nx_secure_dtls_session_trusted_certificate_remove

NetX Secure DTLS 세션에서 신뢰할 수 있는 CA 인증서 제거

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Description

이 서비스는 nx_secure_dtls_session_local_certificate_add를 사용하여 인증서를 추가할 때 할당된 인증서 ID 번호 또는 X.509 CommonName 필드를 사용하여 DTLS 세션 인스턴스에서 신뢰할 수 있는 CA 인증서를 제거합니다.

인증서를 매칭하기 위해 common_name을 사용하는 경우 cert_id 매개 변수를 0으로 설정해야 합니다. cert_id를 사용하는 경우에는 common_name에 NX_NULL 값을 전달해야 합니다.

cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다. 이렇게 하면 DTLS 인증서 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다. X.509 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터
- **common_name** 매칭할 CommonName 문자열에 대한 포인터
- **common_name_length** common_name 문자열의 길이
- **cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자


### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DTLS 세션에서 인증서를 제거했습니다.
- **NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 지정된 DTLS 세션에서 cert_id 또는 common_name과 일치하는 인증서를 찾을 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

*보다 완전한 예제는 *nx_secure_dtls_session_create* 에 대한 참조를 확인하세요.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL, 0,
                                    NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
    status = nx_secure_dtls_session_trusted_certificate_remove(&client_dtls_session,
                                                                    NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>참고 항목

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive
- nx_secure_dtls_session_send, nx_secure_dtls_session_start
- nx_secure_dtls_session_trusted_certificate_add
- nx_secure_x509_certificate_initialize
