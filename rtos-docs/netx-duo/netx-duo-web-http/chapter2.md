---
title: 2장 - HTTP 및 HTTPS의 설치와 사용
description: 이 장에서는 NetX 웹 HTTP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 이슈에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99e649781588b56e72b509c2aa077c38423379d1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810519"
---
# <a name="chapter-2---installation-and-use-of-http-and-https"></a>2장 - HTTP 및 HTTPS의 설치와 사용

이 장에서는 NetX 웹 HTTP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 이슈에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

NetX용 HTTP는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 사용할 수 있습니다. 패키지에는 다음과 같이 원본 파일 3개, 포함 파일 2개 및 이 문서가 포함되어 있습니다.

- **nx_web_http_common. h** NetX 웹 HTTP에 대한 공용 헤더 파일
- **nx_http_client.h** NetX 웹용 HTTP 클라이언트의 헤더 파일
- **nx_web_http_server.h** NetX 웹용 HTTP 서버의 헤더 파일
- **nx_web_http_client.c** NetX 웹용 HTTP 클라이언트의 C 원본 파일
- **nx_web_http_server.h** NetX 웹용 HTTP 서버의 C 원본 파일
- **nx_tcpserver. c** 다중 TCP 소켓용 C 원본 파일
- **nx_tcpserver. h** HTTPS 서버 기호를 정의하는 헤더 파일
- **nx_md5.c** MD5 다이제스트 알고리즘
- **filex_stub.h** FileX가 없는 경우 스텁 파일
- **nx_web_http.pdf** NetX 웹용 HTTP의 설명
- **demo_netx_web_http.c** NetX 웹 HTTP 데모

## <a name="http-installation"></a>HTTP 설치

NetX 웹 HTTP를 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX Duo가 " *\threadx\arm7\green*" 디렉터리에 설치된 경우 *nx_web_http_client.h* 및 *nx_web_http_client.c(NetX 웹 HTTP 클라이언트 애플리케이션용)와, nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c 및 nx_tcpserver.h(NetX 웹 HTTP 서버 애플리케이션)용입니다. 클라이언트와 서버 애플리케이션 모두에 대해 nx_web_http_common.h도 이 디렉터리에 있어야 합니다. 다이제스트 인증을 사용하는 경우에는 nx_md5.c* 도 이 디렉터리에 복사해야 합니다. 데모 ‘ram 드라이버’ 애플리케이션 HTTP 클라이언트와 서버 파일을 동일한 디렉터리에 복사해야 합니다.

TLS를 사용하는 경우 TLS 원본 파일을 포함하는 별도의 NetX 보안 디렉터리가 있어야 합니다.

## <a name="using-http"></a>HTTP 사용

NetX 웹 HTTP는 쉽게 사용할 수 있습니다. 기본적으로 애플리케이션 코드는 *tx_api.h, fx_api.h,* 및 *nx_api.h* 를 포함한 뒤 *nx_web_http_client.h* 및/또는 *nx_web_http_server.h* 를 포함해야 합니다(*nx_web_http_common.h* 자동 포함). 이러한 헤더를 통해 애플리케이션이 각각 ThreadX, FileX 및 NetX Duo를 사용할 수 있습니다. HTTPS 지원을 위해서는 *nx_secure_tls* 파일을 포함한 후 헤더를 포함하여 TLS 지원을 적용해야 합니다.

HTTP 헤더 파일이 포함되면 애플리케이션 코드는 이 가이드의 뒷부분에 지정된 HTTP 함수 호출을 만들 수 있습니다. 또한 빌드 프로세스에서 애플리케이션을 *nx_web_http_client.c(HTTP(S) 클라이언트용)* , *nx_web_http_server.c 및 nx_tcpserver.c(HTTP(S) 서버용)* 및 *nx_md5.c(다이제스트 인증용)* 에 연결해야 합니다. 이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 해당 개체 형식을 애플리케이션의 파일에 연결해야 합니다. 이렇게 간단하게 NetX 웹 HTTP를 사용할 수 있습니다.

> [!NOTE]
> 빌드 프로세스에 NX_WEB_HTTP_DIGEST_ENABLE이 지정되지 않은 경우에는 *md5.c* 파일을 애플리케이션에 추가할 필요가 없습니다. 마찬가지로 HTTP 클라이언트 기능이 필요하지 않은 경우 *nx_web_http_client.c* 파일을, HTTP 서버 기능이 필요하지 않은 경우 *nx_web_http_server.c* 를 생략할 수 있습니다.
>
> NX_WEB_HTTPS_ENABLE을 정의하여 일반 텍스트 HTTP만 사용하는 대신 HTTPS를 사용하도록 설정하지 않았다면 NetX Secure TLS를 빌드에 포함할 필요가 없습니다.
>
> HTTP는 NetX TCP 서비스를 활용하므로 HTTP를 사용하기 전에 *nx_tcp_enable()* 호출을 통해 TCP를 사용하도록 설정해야 합니다.
>
> NetX Secure TLS와 함께 HTTPS를 사용하는 경우 HTTPS 루틴을 호출하기 전에 *nx_secure_tls_initialize()* 를 통해 TLS를 초기화해야 합니다.

## <a name="small-example-system"></a>간단한 예제 시스템

NetX 웹 HTTP 사용 방법의 예제는 아래 그림 1.1에서 설명합니다.

> [!CAUTION]
> 이는 오직 데모용으로 제공되며 그대로 컴파일되거나 실행된다고 보증하지 않습니다.
>
> 네이티브 Express Logic 환경에서 올바르게 빌드되는 데모 소스 코드 파일은 NetX Duo HTTPS 릴리스 코드 배포를 참조하세요.  또한 이 데모는 새 사용자에게 HTTPS 및/또는 NetX Duo HTTPS 애플리케이션을 소개하기 위한 것이므로 의도적으로 매우 간단하게 유지됩니다.

이 예제에서는 HTTP 포함 파일 *nx_web_http_client.h 및 nx_web_http_server.h* 를 가져왔습니다(*netx_web_http_common.h* 자동 포함). 다음으로, HTTP 서버가 “*tx_application_define*”에 만들어집니다. HTTP 서버 제어 블록 “*Server*”가 이전에 전역 변수로 정의되었습니다. 만들기 성공 후에는 HTTPS 서버가 시작됩니다. 그런 다음, HTTPS 클라이언트를 만듭니다. 파일을 쓰고 파일을 다시 읽습니다.

> [!NOTE]
> NX_WEB_HTTPS_ENABLE이 이 시스템에 정의되어 있습니다.

```c
/* This is a small demo of HTTPS on the high-performance NetX Duo TCP/IP stack.
   This demo relies on ThreadX, NetX Duo, and FileX to show an HTML
   transfer from the client and then back from the server.  */

#include  "tx_api.h"
#include  "fx_api.h"
#include  "nx_api.h"
#include  “nx_crypto.h”
#include  “nx_secure_tls_api.h”
#include  “nx_secure_x509.h”
#include  "nx_web_http_client.h"
#include  "nx_web_http_server.h"
#define    DEMO_STACK_SIZE         4096


/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
TX_THREAD               thread_1;
NX_PACKET_POOL          pool_0;
NX_PACKET_POOL          pool_1;
NX_IP                   ip_0;
NX_IP                   ip_1;
FX_MEDIA                ram_disk;

/* Define HTTP objects.  */

NX_WEB_HTTP_SERVER      my_server;
NX_WEB_HTTP_CLIENT      my_client;

/* Define the counters used in the demo application...  */

ULONG                   error_counter;


/* Define the RAM disk memory.  */

UCHAR                   ram_disk_memory[32000];

/* Include cryptographic routines for TLS. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Define TLS data for HTTPS. */
CHAR crypto_metadata[8928 * NX_WEB_HTTP_SESSION_MAX];
UCHAR tls_packet_buffer[16500];

/* NX_WEB_HTTP_SERVER_SESSION_MAX defaults to 2 in nx_web_http_server.h */
UCHAR server_tls_packet_buffer[16500 * NX_WEB_HTTP_SERVER_SESSION_MAX];

/* Define certificate containers. The server certificate is used to identify the NetX
   Web HTTPS server and the trusted certificate is used by the client to verify the
   server’s identity certificate.  */
NX_SECURE_X509_CERT server_certificate;
NX_SECURE_X509_CERT trusted_certificate;

/* Remote certificates need both an NX_SECURE_X509_CERT container and an associated
   buffer. The number of certificates depends on the remote host, but usually at least
   two certificates will be sent – the identity certificate for the host and the
   certificate that issued the identity certificate. */
NX_SECURE_X509_CERT remote_certificate, remote_issuer;

UCHAR remote_cert_buffer[2000];
UCHAR remote_issuer_buffer[2000];

/* Certificate information for server and client (see NetX Secure TLS reference on X.509
    certificates for more information). Arrays are populated with binary versions Of
    certificates and keys and the corresponding “len” variables are assigned the lengths
    of that data. Trusted certificates do not need a private key. */
const UCHAR server_cert_der[] = { … };
const UINT  server_cert_derlen = … ;
const UCHAR server_cert_key_der[] = { … };
const UINT  server_cert_key_derlen = … ;

const UCHAR trusted_cert_der[] = { … };
const UINT  trusted_cert_derlen = … ;


/* Define function prototypes.  */

void    thread_0_entry(ULONG thread_input);
VOID    _fx_ram_driver(FX_MEDIA *media_ptr) ;
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT    authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
             CHAR *resource, CHAR **name, CHAR **password, CHAR **realm);
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
   NX_SECURE_TLS_SESSION *tls_session);

/* Define the application's authentication check.  This is called by
   the HTTP server whenever a new request is received.  */
UINT  authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
            CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
{
    /* Just use a simple name, password, and realm for all
       requests and resources.  */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Web HTTP demo";

    /* Request basic authentication.  */
    return(NX_WEB_HTTP_BASIC_AUTHENTICATE);
}

/* Define the TLS setup callback for HTTPS Client. This function is invoked when the
   HTTPS client is started – all TLS per-session initialization should go in here. */
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
  NX_SECURE_TLS_SESSION *tls_session)
{
    UINT status;

    /* Initialize and create TLS session. */
    nx_secure_tls_session_create(tls_session, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata));

    /* Allocate space for packet reassembly. */
    nx_secure_tls_session_packet_buffer_set(tls_session, tls_packet_buffer,
        sizeof(tls_packet_buffer));


    /* Add a CA Certificate to our trusted store for verifying incoming server
        certificates. */
    nx_secure_x509_certificate_initialize(&trusted_certificate, trusted_cert_der,
        trusted_cert_der_len, NX_NULL, 0, NULL, 0,
        NX_SECURE_X509_KEY_TYPE_NONE);
    nx_secure_tls_trusted_certificate_add(tls_session, &trusted_certificate);

    /* Need to allocate space for the certificate coming in from the remote host. */
    nx_secure_tls_remote_certificate_allocate(tls_session, &remote_certificate,
        remote_cert_buffer, sizeof(remote_cert_buffer));
    nx_secure_tls_remote_certificate_allocate(tls_session,
        &remote_issuer, remote_issuer_buffer,
        sizeof(remote_issuer_buffer));

    return(NX_SUCCESS);
 }

/* Define main entry point.  */

 int main()
 {
     /* Enter the ThreadX kernel.  */
     tx_kernel_enter();
 }

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    CHAR    *pointer;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread.  */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create packet pool.  */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
        600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance.  */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer =  pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create another IP instance.  */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
        0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk.  */
    fx_media_open(&ram_disk, "RAM DISK",
        _fx_ram_driver, ram_disk_memory, pointer, 4096);
    pointer += 4096;

    /* Create the NetX Web HTTP Server.  */
    nx_web_http_server_create(&my_server, "My HTTP Server", &ip_1,
        NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
        pointer, 4096, &pool_1, authentication_check, NX_NULL);
    pointer = pointer + 4096;

    /* The TLS server needs an identity certificate which is imported as a binary DER-
        encoded X.509 certificate and its associated private key (e.g. DER-encoded PKCS#1
        RSA private key). */
    nx_secure_x509_certificate_initialize(&server_certificate, server_cert_der,
        server_cert_der_len, NX_NULL, 0,
        server_cert_key_der, server_cert_key_der_len,
        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Setup TLS session data for the TCP server.
        This enables TLS and HTTPS for the server.  */
    nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata), server_tls_packet_buffer,
        sizeof(server_tls_packet_buffer), &server_certificate, NX_NULL, 0,
        NX_NULL, 0, NX_NULL, 0);

    /* Start the HTTP Server.  */
    nx_web_http_server_start(&my_server);
}

/* Define the test thread.  */
void    thread_0_entry(ULONG thread_input)
{
    NX_PACKET   *my_packet;
    UINT        status;

    /* Create an HTTP client instance.  */
    status = nx_web_http_client_create(&my_client, "My Client", &ip_0, &pool_0, 600);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server over HTTPS.  */
    status = nx_web_http_client_put_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm", "name", "password", 103, tls_setup_callback, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Allocate a packet.  */
     tatus = nx_web_http_client_request_packet_allocate(&pool_0, &my_packet,
        NX_TCP_PACKET, NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page.  */
    nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet,
        "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<H1>NetX Test Page</H1>\r\n", 25,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
        &pool_0, NX_WAIT_FOREVER);

    /* Complete the PUT by writing the total length.  */
    status =  nx_web_http_client_put_packet(&my_client, my_packet, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Now GET the file back!  */
    status =  nx_web_http_client_get_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm",
        "name", "password", tls_setup_callback, 50);
 
    /* Check status.  */
    if (status)
        error_counter++;

    /* Get a packet.  */
    status =  nx_web_http_client_response_body_get(&my_client, &my_packet, 20);

    /* Check for an error.  */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet.  */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it!  */
        nx_packet_release(my_packet);
    }

    /* Make sure TLS shuts down properly. */
    nx_web_http_client_delete(&my_client);

    /* Flush the media.  */
    fx_media_flush(&ram_disk);
}
```

**그림 1.1 NetX 및 NetX Secure TLS를 사용하는 HTTPS 사용 예제**

## <a name="configuration-options"></a>구성 옵션

NetX용 HTTP를 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음은 각 옵션에 대한 자세한 설명입니다. 기본값은 나열되지만 *nx_web_http_client.h 및 nx_web_http_server.h* 를 포함하기 전에 다시 정의할 수 있습니다.

- **NX_DISABLE_ERROR_CHECKING** 정의된 경우 이 옵션은 기본 HTTP 오류 검사를 제거합니다. 일반적으로 애플리케이션이 디버깅 된 후에 사용됩니다.
- **NX_WEB_HTTP_DIGEST_ENABLE** 정의된 경우 MD5 다이제스트를 사용하는 인증은 HTTPS 서버에서 사용하도록 설정됩니다. 기본적으로 정의되어 있지 않습니다.
- **NX_WEB_HTTP_SERVER_PRIORITY** HTTPS 서버 스레드의 우선 순위입니다. 기본적으로 이 값은 우선 순위 16을 지정하는 16으로 정의되어 있습니다.
- **NX_WEB_HTTP_NO_FILEX** 정의된 경우 이 옵션은 FileX 종속성에 대한 스텁을 제공합니다. 이 옵션이 정의된 경우 HTTPS 클라이언트는 변동 없이 작동합니다. HTTPS 서버가 제대로 작동하려면 수정하거나, 사용자가 몇 가지 FileX 서비스를 만들어야 합니다.
- **NX_WEB_HTTP_TYPE_OF_SERVICE** HTTPS TCP 요청에 필요한 서비스 유형입니다. 기본적으로 이 값은 일반 IP 패킷 서비스를 나타내는 NX_IP_NORMAL로 정의됩니다.
- **NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** 동일한 우선 순위의 스레드에 발생하기 전에 서버 스레드를 실행할 수 있는 타이머 틱 수입니다. 기본값은 2입니다. 이 옵션은 사용되지 않습니다.
- **NX_WEB_HTTP_FRAGMENT_OPTION** HTTP TCP 요청에 대해 조각을 사용합니다. 기본적으로 이 값은 HTTP TCP 조각화를 사용하지 않도록 설정하는 NX_DONT_FRAGMENT입니다.
- **NX_WEB_HTTP_SERVER_WINDOW_SIZE** 서버 소켓 창 크기입니다. 기본적으로 이 값은 2048바이트입니다.
- **NX_WEB_HTTP_TIME_TO_LIVE** 이 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다. 기본값은 0x80으로 설정됩니다.
- **NX_WEB_HTTP_SERVER_TIMEOUT** 내부 서비스가 일시 중단할 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 \* *NX_IP_PERIODIC_RATE*)로 설정됩니다.
- **NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** 내부 *nx_tcp_server_socket_accept()* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 (10 \* *NX_IP_PERIODIC_RATE*)로 설정됩니다.
- **NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** 내부 *nx_tcp_socket_disconnect()* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 \* *NX_IP_PERIODIC_RATE*)로 설정됩니다.
- **NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** 내부 *nx_tcp_socket_receive()* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 \* *NX_IP_PERIODIC_RATE*)로 설정됩니다.
- **NX_WEB_HTTP_SERVER_TIMEOUT_SEND** 내부 *nx_tcp_socket_send()* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 \* *NX_IP_PERIODIC_RATE*)로 설정됩니다.
- **NX_WEB_HTTP_MAX_HEADER_FIELD**  **HTTP 헤더 필드의 최대 크기를 지정합니다. 기본값은 256입니다.**
- **NX_WEB_HTTP_MULTIPART_ENABLE ** ** 정의된 경우 HTTPS 서버가 다중 파트 HTTP 요청을 지원할 수 있습니다. **
- **NX_WEB_HTTP_SERVER_MAX_PENDING** HTTPS 서버에 대해 큐에 대기할 수 있는 연결 수를 지정합니다. 기본값은 최대 서버 세션 수의 두 배로 설정됩니다.
- **NX_WEB_HTTP_MAX_RESOURCE** 클라이언트에서 제공하는 *리소스 이름* 에 허용되는 바이트 수를 지정합니다. 기본값은 40으로 설정됩니다.
- **NX_WEB_HTTP_MAX_NAME** 클라이언트에서 제공하는 *사용자 이름* 에 허용되는 바이트 수를 지정합니다. 기본값은 20으로 설정됩니다.
- **NX_WEB_HTTP_MAX_PASSWORD** 클라이언트에서 제공하는 *암호* 에 허용되는 바이트 수를 지정합니다. 기본값은 20으로 설정됩니다.
- **NX_WEB_HTTP_SERVER_SESSION_MAX** HTTP 또는 HTTPS 서버에 대한 동시 세션 수를 지정합니다. 각 세션에 대해 TCP 소켓과 TLS 세션(HTTPS를 사용하도록 설정한 경우)이 할당됩니다. 기본값은 2로 설정됩니다.
- **NX_WEB_HTTPS_ENABLE** 정의된 경우 이 매크로는 TLS 및 HTTPS를 사용하도록 설정합니다. 일반 텍스트 HTTP만 필요한 경우에는 리소스 확보를 위해 정의되지 않은 상태로 둡니다. 기본적으로 이 매크로는 정의되지 않았습니다.
- **NX_WEB_HTTPS_KEEPALIVE_DISABLE** 정의된 경우 이 매크로는 HTTP 연결 유지 기능을 사용하지 않도록 설정합니다. 기본적으로 이 매크로는 정의되지 않았습니다.
- **NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** 서버를 만들 때 지정된 풀에 있는 패킷의 최소 크기를 지정합니다. 전체 HTTP 헤더를 하나의 패킷에 포함될 수 있도록 하려면 최소 크기가 필요합니다. 기본값은 600으로 설정됩니다.
- **NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** 클라이언트를 만들 때 지정된 풀에 있는 패킷의 최소 크기를 지정합니다. 전체 HTTP 헤더를 하나의 패킷에 포함될 수 있도록 하려면 최소 크기가 필요합니다. 기본값은 600으로 설정됩니다.
- **NX_WEB_HTTP_SERVER_RETRY_SECONDS** 서버 소켓 재전송 시간 제한(초)을 설정합니다. 기본값은 2로 설정됩니다.
- **NX_WEB_HTTP_ SERVER_RETRY_MAX** 서버 소켓의 최대 재전송 수를 설정합니다. 기본값은 10으로 설정됩니다.
- **NX_WEB_HTTP_ SERVER_RETRY_SHIFT** 이 값은 다음 재전송 시간 제한을 설정하는 데 사용됩니다. 현재 시간 제한에는 소켓 제한 시간 이동의 값으로 이동하여 지금까지의 재전송 횟수를 곱합니다. 제한 시간을 두 배로 설정하기 위해 기본값은 1로 설정됩니다.
- **NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** 서버 소켓 재전송 큐에서 큐에 넣을 수 있는 최대 패킷 수를 지정합니다. 큐에 넣은 패킷 수가 이 수에 도달하면 하나 이상의 큐에 넣은 패킷을 해제할 때까지 더 이상 패킷을 전송할 수 없습니다. 기본값은 20으로 설정됩니다.
