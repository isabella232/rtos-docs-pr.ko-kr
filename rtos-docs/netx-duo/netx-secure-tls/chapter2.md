---
title: 2장 - Azure RTOS NetX Secure의 설치 및 사용
description: 이 장에서는 NetX Secure 구성 요소의 설치, 설정, 사용과 관련된 다양한 문제에 관해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b3ef82bd113518b35105fb2eefe23bd3e755ca06
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811767"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-secure"></a>2장 - Azure RTOS NetX Secure의 설치 및 사용

이 장에서는 Azure RTOS NetX Secure 구성 요소의 설치, 설정, 사용과 관련된 다양한 문제에 관해 설명합니다.

## <a name="product-version-number"></a>제품 버전 번호

사용자는 nx_secure_tls.h에서 다음 기호를 찾아 제품 버전 번호를 확인할 수 있습니다.

***NETX_SECURE_MAJOR_VERSION***

***NETX_SECURE_MINOR_VERSION***

서비스 팩 번호를 나타내기 위해 서비스 팩 릴리스에는 다음 기호가 정의되어 있습니다.

***NETX_SECURE_SERVICE_PACK_VERSION***

## <a name="product-distribution"></a>제품 배포

NetX Secure는 [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx)에서 얻을 수 있습니다. 패키지에는 다음과 같이 이 문서를 포함하는 원본 파일, 포함 파일, PDF 파일이 포함되어 있습니다.

- **nx_secure_tls_api.h** NetX Secure TLS의 퍼블릭 API 헤더 파일
- **nx_secure_tls_user.h** 사용자가 NetX Secure TLS의 헤더 파일을 정의함
- **nx_secure_tls_port.h** NetX Secure에 대한 플랫폼별 정의
- **nx_secure_tls.h** NetX Secure TLS의 헤더 파일
- **nx_secure_tls&#42;.c/h** NetX Secure TLS의 C/H 원본 파일
- **nx_crypto&#42;.c/h** NetX Secure Cryptography에 대한 C/H 원본 파일
- **nx_secure_x509&#42;.c/h** X.509 디지털 인증서의 C/H 원본 파일
- **demo_netx_secure_tls.c** NetX Secure TLS Demo의 C 원본 파일
- **NetX_Secure_User_Guide.pdf** NetX Secure 제품의 PDF 설명서

> [!NOTE]
> NetX Secure 부모 디렉터리의 하위 디렉터리에 있는 다른 하드웨어 플랫폼에 대한 nx_crypto* 파일이 제공됩니다.

## <a name="netx-secure-installation"></a>NetX Secure 설치

NetX Secure를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리 수준에 복사해야 합니다. 예를 들어, NetX가 디렉터리 “ *\threadx\arm7\NetX*”에 설치되면 *nx_secure**.* 디렉터리를 “ *\threadx\arm7\NetXSecure*”로 복사해야 합니다.

## <a name="using-netx-secure"></a>NetX Secure 사용

NetX Secure TLS는 간단하게 사용할 수 있습니다. 기본적으로 애플리케이션 코드에는 ThreadX와 NetX를 각각 사용하기 위해 *tx_api.h* 와 *nx_api.h* 가 포함된 후 *nx_secure_tls_api.h* 가 포함되어야 합니다. *nx_secure_tls_api.h* 가 포함되면 애플리케이션 코드는 이 가이드의 뒷부분에 지정된 NetX Secure 함수를 호출할 수 있습니다. 또한 애플리케이션은 *nx_secure**.* 파일을 NetXSecure 라이브러리로, 플랫폼별 *nx_crypto**.* 파일을 NetXCrypto 라이브러리로 가져와야 합니다.

## <a name="small-example-system-tls-client"></a>간단한 예제 시스템(TLS 클라이언트)

NetX Secure를 사용하기가 얼마나 쉬운지 보여 주는 예제는 아래에 표시된 그림 1.1에 나와 있습니다. 이 예제는 암호화에 소프트웨어 암호화 모듈(하드웨어에 국한되지 않음)을 사용하는 간단한 TLS 클라이언트를 보여줍니다. 이 클라이언트는 OpenSSL 역방향 반향 서버(openssl s_server -rev)에서 작동하도록 설계되었습니다.

이 예제를 실행하려면 대상 서버의 인증서를 인증하기 위해 x.509 CA 인증서가 필요합니다. OpenSSL 예제에서는 간단한 2수준 PKI(루트 CA 인증서-> >서버 인증서)로 충분합니다. DER로 인코딩된 이진 버전의 CA 인증서로 “Trusted_ca_data” 배열을 채우고, 인증서의 실제 길이를 반영하도록 “trusted_ca_length” 변수를 업데이트해야 합니다.

하드웨어용 네트워크 드라이버도 필요합니다. nx_ip_create 호출에서 “nx_driver_xx” 매개 변수를 바꾸세요.

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

/* Define the size of our application stack. */
#define     DEMO_STACK_SIZE             4096

/* Define the remote server IP address using NetX IP_ADDRESS macro. */
#define     REMOTE_SERVER_IP_ADDRESS    IP_ADDRESS(192, 168, 1, 1)

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS           IP_ADDRESS(192, 168, 1, 2)

/* Define the remote server port. 443 is the HTTPS default. */
#define     REMOTE_SERVER_PORT          443

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define an HTTP request to be sent to the HTTPS web server not defined here but
  represented by the ellipsis. */
UCHAR http_request[] = { "GET /example.html HTTP/1.1"  };

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];

/* Define the TLS Client thread.  */
ULONG             tls_client_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_client_thread;
void              client_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Client X.509 trusted root CA certificate, ASN.1 DER-
   encoded. A trusted certificate must be provided for TLS Client applications
   (unless X.509 authentication is disabled) or TLS will treat all certificates as
   untrusted and the handshake will fail.
*/

/* DER-encoded binary certificate, not defined here but represented by the ellipsis,
   for the sake of brevity. */
const UCHAR trusted_ca_data[] = { … };
const UINT trusted_ca_length = 0x574;

/* Define the application – initialize drivers and TCP/IP setup.
   NOTE: the variable “status” should be checked after every API call. Most error
         checking has been omitted for clarity. */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;

   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create a packet pool. Check status for errors. */
   status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                   (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                   NX_PACKET_POOL_SIZE);

   /* Create an IP instance for the specific target. Check status for errors. This
      call is not completely defined. Please see other demo files for proper usage
      of the nx_ip_create call. */
   status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                         DEVICE_IP_ADDRESS ,
                         0xFFFFFF00UL,
                         &pool_0, nx_driver_xx,
                         (UCHAR*)ip_thread_stack,
                         sizeof(ip_thread_stack),
                         1);

   /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
       errors. */
   status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

   /* Enable TCP traffic. Check status for errors. */
   status =  nx_tcp_enable(&ip_0);

   status =  nx_ip_fragment_enable(&ip_0);

   /* Initialize the NetX Secure TLS system.  */
   nx_secure_tls_initialize();

    /* Create the TLS client thread to start handling incoming requests. */
   tx_thread_create(&tls_client_thread, "TLS Client thread", client_thread_entry, 0,
                     tls_client_thread_stack, sizeof(tls_client_thread_stack),
                     16, 16, 4, TX_AUTO_START);
   return;
}

/* Thread to handle the TLS Client instance. */
void client_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG       actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;
ULONG server_ipv4_address;

    /* We are not using the thread input parameter so suppress compiler warning. */
    NX_PARAMETER_NOT_USED(thread_input);

   /* Ensure the IP instance has been initialized.  */
   status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

   /* Create a TCP socket to use for our TLS session.  */
   status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Client Socket",
                                  NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                  NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

   /* Create a TLS session for our socket. This sets up the TLS session object for
          later use */
   status =  nx_secure_tls_session_create(&tls_session,
                                          &nx_crypto_tls_ciphers_ecc,
                                          tls_crypto_metadata,
                                          sizeof(tls_crypto_metadata));

   /* Initialize ECC parameters for this session. */
   status = nx_secure_tls_ecc_initialize(&tls_session,
                                             nx_crypto_ecc_supported_groups,
                                             nx_crypto_ecc_supported_groups_size,
                                             nx_crypto_ecc_curves);

   /* Set the packet reassembly buffer for this TLS session. */
   status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                    sizeof(tls_packet_buffer));

   /* Initialize an X.509 certificate with our CA root certificate data. */
   nx_secure_x509_certificate_initialize(&certificate, trusted_ca_data,
                                         trusted_ca_length, NX_NULL, 0, NX_NULL, 0,
                                         NX_SECURE_X509_KEY_TYPE_NONE);

   /* Add the initialized certificate as a trusted root certificate. */
   nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);

   /* Setup this thread to open a connection on the TCP socket to a remote server.
      The IP address can be used directly or it can be obtained via DNS or other
      means.*/
   server_ipv4_address = REMOTE_SERVER_IP_ADDRESS;
   status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
                                         REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

   /* Start the TLS Session using the connected TCP socket. This function will
      ascertain from the TCP socket state that this is a TLS Client session. */
   status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                         NX_WAIT_FOREVER);

    /* Allocate a TLS packet to send an HTTP request over TLS (HTTPS). */
    status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                          NX_WAIT_FOREVER);

    /* Populate the packet with our HTTP request. */
    nx_packet_data_append(send_packet, http_request, sizeof(http_request), &pool_0,
                          NX_WAIT_FOREVER);


   /* Send the HTTP request over the TLS Session, turning it into HTTPS. */
   status = nx_secure_tls_session_send(&tls_session, send_packet, NX_WAIT_FOREVER);

   /* If the send fails, you must release the packet.  */
   if (status != NX_SUCCESS)
   {
         /* Release the packet since the packet was not sent.  */
         nx_packet_release(send_packet);
   }

   /* Receive the HTTP response and any data from the server. */
   status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
   NX_WAIT_FOREVER);
   if (status == NX_SUCCESS)
   {
       /* Extract the data we received from the remote server. */
       status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                             100,  &bytes);
        /* Display the response data. */
       receive_buffer[bytes] = 0;
       printf("Received data: %s\n", receive_buffer);

        /* Release the packet when done with it. */
       nx_packet_release(receive_packet);
   }

   /* End the TLS session now that we have received our HTTPS/HTML response. */
   status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

   /* Check for errors to make sure the session ended cleanly. */

   /* Disconnect the TCP socket. */
   status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

}
```

**그림 1.1 NetX에서 NetX Secure 사용의 예제**

## <a name="small-example-system-tls-web-server"></a>간단한 예제 시스템(TLS 웹 서버)

NetX Secure를 사용하기가 얼마나 쉬운지 보여 주는 예제는 아래에 표시되는 그림 1.1에 나와 있으며 간단한 TLS 웹 서버(HTTPS)를 보여줍니다.

이 예제를 실행하려면 TLS 클라이언트에서 서버를 식별하기 위해 x.509 인증서가 필요합니다. 대부분의 웹 브라우저에서는 간단한 자체 서명된 인증서로 충분합니다. 브라우저에서 서버를 인증할 수 없다고 응답하고 경우에 따라 개발자 서버에 대한 TLS/HTTPS 연결을 설정하지 못할 수 있습니다<sup>3</sup>. 서버 인증서의 DER로 인코딩된 이진 버전으로 “certificate_data” 배열을 채우고, 인증서의 실제 길이를 반영하도록 “certificate_length” 변수를 업데이트해야 합니다. 또한 RSA 키의 경우 PKCS#1을, ECC 키의 경우 RFC 5915를 사용하여 형식이 지정된, DER로 인코딩된 버전의 인증서 프라이빗 키로 “private_key” 배열을 채워야 합니다. 키 데이터의 실제 길이로 “private_key_length” 변수를 채웁니다.

> [!IMPORTANT]
> 일부 브라우저(특히, Chrome 브라우저의 일부 버전)는 자체 서명된 인증서를 거부할 수 있습니다. 이 경우 서버 인증서에 서명하는 데 사용되는 루트 CA 인증서를 사용하여 2수준 PKI를 만들 수 있습니다. 현재 상황에서는 루트 CA 인증서가 브라우저에 신뢰할 수 있는 루트 인증서로 설치되어 있습니다. !!! 중요 – 완료한 후에는 브라우저에서 루트 CA 인증서를 제거하고 프로덕션 애플리케이션에 사용하지 마세요.

하드웨어용 네트워크 드라이버도 필요합니다. nx_ip_create 호출에서 “nx_driver_xx” 매개 변수를 바꾸세요.

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

#define     DEMO_STACK_SIZE         4096

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS             IP_ADDRESS(192, 168, 1, 2)

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];


/* Define the TLS Server thread.  */
ULONG             tls_server_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_server_thread;
void              server_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Server X.509 certificate, ASN.1 DER-encoded. Note that the
   certificate data and private key data is represented by an ellipsis for the sake
   of brevity.
*/
const UCHAR certificate_data[] = { … }; /* DER-encoded binary certificate. */
const UINT certificate_length = 0x574;

/* Binary data for the TLS Server Private Key, from private key
   file generated at the time of the X.509 certificate creation. ASN.1 DER-encoded. */
const UCHAR private_key[] = { … }; /* DER-encoded private key file (PKCS#1 RSA or ECC) */
const UINT private_key_length = 0x40;

/* Define some HTML data (web page) with an HTTPS header to serve to connecting
   clients. */
UCHAR html_data[] = { "HTTP/1.1 200 OK\r\n" \
        "Date: Tue, 19 May 2020 23:59:59 GMT\r\n" \
        "Content-Type: text/html\r\n" \
        "Content-Length: 200\r\n\r\n" \
        "<html>\r\n"\
        "<body>\r\n"\
        "<b>Hello NetX Secure User!</b>\r\n"\
        "This is a simple webpage\r\n"\
        "served up using NetX Secure!\r\n"\
        "</body>\r\n"\
        "</html>\r\n" };

/* Define the application – initialize drivers and TCP/IP setup.  */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;


    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create a packet pool. Check status for errors. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                    (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                    NX_PACKET_POOL_SIZE);

    /* Create an IP instance for the specific target. Check status for errors. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                          DEVICE_IP_ADDRESS,
                          0xFFFFFF00UL,
                          &pool_0, nx_driver_xx,
                          (UCHAR*)ip_thread_stack,
                          sizeof(ip_thread_stack),
                          1);

    /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
         errors. */
    status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

    /* Enable TCP traffic. Check status for errors. */
    status =  nx_tcp_enable(&ip_0);

    status =  nx_ip_fragment_enable(&ip_0);

    /* Initialize the NetX Secure TLS system.  */
    nx_secure_tls_initialize();

    /* Create the TLS server thread to start handling incoming requests. */
    tx_thread_create(&tls_server_thread, "TLS Server thread", server_thread_entry, 0,
                   tls_server_thread_stack, sizeof(tls_server_thread_stack),
                   16, 16, 4, TX_AUTO_START);
    return;
}

/* Thread to handle the TLS Server instance. */
void server_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG      actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;

    NX_PARAMETER_NOT_USED(thread_input);

    /* Ensure the IP instance has been initialized.  */
    status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

    /* Create a TCP socket to use for our TLS session.  */
    status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket",
                                   NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                   NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

    /* Create a TLS session for our socket.  */
    status =  nx_secure_tls_session_create(&tls_session,
                                        &nx_crypto_tls_ciphers_ecc,
                                        tls_crypto_metadata,
                                        sizeof(tls_crypto_metadata));

    status = nx_secure_tls_ecc_initialize(&tls_session,
                                          nx_crypto_ecc_supported_groups,
                                          nx_crypto_ecc_supported_groups_size,
                                          nx_crypto_ecc_curves);

     /* Set the packet reassembly buffer for this TLS session. */
     status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                      sizeof(tls_packet_buffer));

    /* Initialize an X.509 certificate and private ECC key for our TLS Session. */
    nx_secure_x509_certificate_initialize(&certificate, certificate_data, NX_NULL, 0,
                                          certificate_length, private_key,
                                          private_key_length,
                                          NX_SECURE_X509_KEY_TYPE_EC_DER);

    /* Add the initialized certificate as a local identity certificate. */
    nx_secure_tls_local_certificate_add(&tls_session, &certificate);


    /* Setup this thread to listen on the TCP socket.
       Port 443 is standard for HTTPS. */
    status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

    while(1)
     {
         /* Accept a client TCP socket connection.  */
         status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

         /* Start the TLS Session using the connected TCP socket. */
         status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                              NX_WAIT_FOREVER);

         /* Receive the HTTPS request. */
         status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
                                                NX_WAIT_FOREVER);

if (status == NX_SUCCESS)
      {
         /* Extract the HTTP request information from the HTTPS request. */
            status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                                  100, &bytes);
         /* Display the HTTP request data. */
            receive_buffer[bytes] = 0;
            printf("Received data: %s\n", receive_buffer);

         /* Release the packet when done with it */
            nx_packet_release(receive_packet);
      }

         /* Allocate a TLS packet to send HTML data back to client. */
         status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                                NX_WAIT_FOREVER);

         /* Populate the packet with our HTTP response and HTML web page data. */
         nx_packet_data_append(send_packet, html_data, sizeof(html_data), &pool_0,
                               NX_WAIT_FOREVER);

         /* Send the HTTP response over the TLS Session, turning it into HTTPS. */
         status = nx_secure_tls_session_send(&tls_session, send_packet,
                                                 NX_WAIT_FOREVER);

         /* If the send fails, you must release the packet.  */
         if (status != NX_SUCCESS)
         {
              /* Release the packet since it was not sent.  */
              nx_packet_release(send_packet);
         }

         /* End the TLS session now that we have sent our HTTPS/HTML response. */
         status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

         /* Check for errors to make sure the session ended cleanly! */

         /* Disconnect the TCP socket so we can be ready for the next request. */
         status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

         /* Unaccept the server socket.  */
         status =  nx_tcp_server_socket_unaccept(&tcp_socket);

         /* Setup server socket for listening again.  */
         status =  nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
     }
}
```

**그림 1.2 NetX에서 NetX Secure 사용의 예제**

## <a name="a-note-on-tls-session-error-recovery"></a>TLS 세션 오류 복구에 대한 참고 사항

위에서 설명한 예제 시스템은 각각 TLS 클라이언트와 서버에 대한 기본 개요를 보여 주지만 명확한 설명을 위해 오류 처리 부분은 생략되었습니다. 그러나 TLS에서 제공하는 보안의 일부는 오류 조건의 적절한 처리에 따라 달라집니다. 일반적으로 가장 심각한 잠재적인 문제는 TLS 스택 자체 내에서 처리되지만 TLS 애플리케이션이 TLS 구현 내에서 처리되지 않는 TLS 오류에 적절하게 대응하고 해당 오류에서 복구해야 합니다.

적절한 오류 처리에 필요한 논리를 보여 주기 위해 다음 함수는 TLS 오류를 올바르게 처리하고 오류 조건이 발생한 후에 TLS 상태를 명확하게 다시 설정하는 데 사용할 수 있는 API 서비스의 일반적인 컬렉션을 보여 줍니다. 여기서 나온 섹션 이외에 해당 논리는 TLS 클라이언트와 TLS 서버 인스턴스에 적용됩니다.

함수에서 가장 중요한 API 호출은 TLS 세션 또는 핸드셰이크를 완전히 종료하는 *nx_secure_tls_session_end* 서비스와 새 TLS 세션에 tls_session 제어 구조 인스턴스를 다시 사용할 수 있도록 TLS 세션 상태를 지우는 *nx_secure_tls_session_reset* 서비스에 대한 호출입니다. 또한 *nx_secure_tls_session_reset* 은 사용자가 구성한 상태(예: 인증서 또는 할당된 버퍼)를 지우지 않기 때문에 *nx_secure_tls_session_create* 를 다시 호출하지 않아도 세션을 다시 사용할 수 있습니다. 모든 TLS 세션 상태를 완전히 지우려면 *nx_secure_tls_session_delete* 서비스를 대신 사용할 수 있습니다.

```C
/* Define a helper function to clean up a broken TLS session (to be called on any
   error from nx_secure_tls_session_start onwards). Note that the variables
   tls_session, tcp_socket, and ip_0 are global in the above examples. */
VOID tls_session_error_cleanup(VOID)
{
UINT status;
UINT alert_level, alert_value;

      /* If we got an error back from a TLS API call, there may be an alert from the
         remote host. Extract the alert level and value to print out. Note that the TLS
         API will return NX_SECURE_TLS_ALERT_RECEIVED (0x114) if an alert was received.
         For other error codes the alert value and level are not valid. */
      status = nx_secure_tls_session_alert_value_get(&tls_session, &alert_level,
                                                     &alert_value);
      if(status)
      {
         printf("Pointer error in getting alert value.\n");
      }
      else
      {
         printf("Alert recieved. Value: %d, Level: %d\n", alert_value, alert_level);
      }

      /* End the TLS session. This is required to properly shut down the TLS
         connection. */
      status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

      /* If the session did not shut down cleanly, this is a possible security issue. */
      if (status)
      {
         printf("Error in TLS session end: %x\n", status);
      }

      /* Reset the TLS session to re-use the control structure for the next connection.
         This API service resets the TLS session state but does not remove user-
         configured options such as certificates, PSKs, buffers, and cipher routines. */
      nx_secure_tls_session_reset(&tls_session);

      /* Disconnect the TCP socket, closing the connection. */
      status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket close: %x\n", status);
      }

   /* The following code applies only to a TLS server instance. */
   #if NX_SECURE_TLS_SERVER
      /* Unaccept the server socket.  */
      status =  nx_tcp_server_socket_unaccept(&tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket unaccept: %x\n", status);
      }

      /* Setup server socket for listening again.  */
      status =  nx_tcp_server_socket_relisten(&ip_0, DEVICE_SERVER_PORT, &tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket relisten: %x\n", status);
      }
#endif
} /* End function. */
```

## <a name="configuration-options"></a>구성 옵션

NetX Secure를 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음은 각 옵션에 대한 자세한 설명입니다.

| 정의 | 의미 |
|----------------------|------------------------------------------------|
| **NX_SECURE_DISABLE_ERROR_CHECKING**                | 정의된 경우, 이 옵션은 기본 NetX Secure 오류 검사를 제거합니다. 일반적으로 애플리케이션이 디버그된 후에 사용됩니다. |
| **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**                  | 정의된 경우, 이 옵션은 예상되는 최대 RSA 모듈러스(비트)를 제공합니다. 4096비트 모듈러스의 기본값은 4096입니다. 다른 값은 3072, 2048 또는 1024(권장하지 않음)일 수 있습니다. |
| **NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**        | 정의된 경우, 이 옵션은 TLS가 원격 호스트의 자체 서명된 인증서를 수락하도록 허용합니다. 기본적으로 TLS는 보안 예방 조치로 자체 서명된 서버 인증서를 거부합니다. 이 매크로를 정의하면 수락을 위해 자체 서명된 인증서를 신뢰할 수 있는 저장소에 추가해야 합니다. |
| **NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**      | 정의된 경우, 이 옵션은 TLS 서버에 대한 선택적 X.509 클라이언트 인증서 확인을 사용하도록 설정합니다<sup>4</sup>.  |
| **NX_SECURE_ENABLE_PSK_CIPHERSUITES**               | 정의된 경우, 이 옵션은 PSK(미리 공유한 키) 기능을 사용하도록 설정합니다. 디지털 인증서를 사용하지 않도록 설정하는 것은 아닙니다. |
| **NX_SECURE_TLS_CLIENT_DISABLED**                   | 정의된 경우, 이 옵션은 TLS 클라이언트 모드와 관련된 모든 TLS 스택 코드를 제거하여 코드와 데이터 사용량을 줄입니다. |
| **NX_SECURE_TLS_SERVER_DISABLED**                   | 정의된 경우, 이 옵션은 TLS 서버 모드와 관련된 모든 TLS 스택 코드를 제거하여 코드와 데이터 사용량을 줄입니다.  |
| **NX_SECURE_DISABLE_ECC_CIPHERSUITE**               | 정의된 경우, 이 옵션은 ECC(타원 곡선 암호화) 암호화 도구 모음의 모든 TLS 논리를 제거합니다. 해당 암호화 도구 모음은 TLS 1.2 및 이전 버전에서는 선택 사항이며, 사용하지 않도록 설정하면 코드와 데이터 크기를 크게 줄일 수 있습니다.|
| **NX_SECURE_TLS_ENABLE_TLS_1_3**                    | 정의된 경우 이 옵션은 TLSv1.3 모드를 사용하도록 설정합니다. TLS 1.3은 최신 버전의 TLS이며 기본적으로 사용하지 않도록 설정되어 있습니다. |
| **NX_SECURE_TLS_ENABLE_TLS_1_0**                    | 정의된 경우 이 옵션은 레거시 TLSv1.0 모드를 사용하도록 설정합니다. TLSv1.0은 더 이상 사용되지 않는 것으로 간주되므로 이전 애플리케이션의 이전 버전과의 호환성을 위해서만 사용하도록 설정해야 합니다. |
| **NX_SECURE_TLS_ENABLE_TLS_1_1**                    | 정의된 경우 이 옵션은 레거시 TLSv1.1 모드를 사용하도록 설정합니다. TLSv1.1은 더 이상 사용되지 않는 것으로 간주되므로 이전 애플리케이션의 이전 버전과의 호환성을 위해서만 사용하도록 설정해야 합니다. |
| **NX_SECURE_TLS_DISABLE_TLS_1_1**                   | 정의된 경우 이 옵션은 TLSv1.1 모드를 사용하도록 설정합니다. 기본적으로 정의되어 있습니다. 보다 안전한 TLSv1.2만 사용하도록 하기 위해 TLSv1.1은 사용하지 않도록 설정되어 있습니다<sup>5</sup>.  |
| **NX_SECURE_X509_STRICT_NAME_COMPARE**              | 정의된 경우 이 옵션은 인증서 검색과 확인을 위해 X.509 인증서에 대해 엄격한 고유 이름 비교가 가능합니다. 기본값은 일반 이름 필드와 고유 이름을 비교만 합니다.|
| **NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES** | 정의된 경우 이 옵션은 X.509 인증서에 추가 메모리를 사용하는 대신 선택적 X.509 고유 이름 필드를 사용할 수 있습니다. |

4. 이 옵션을 사용하면 코드를 애플리케이션에 연결할 수만 있습니다. 클라이언트 인증서 확인을 사용하려면 이 기능을 API 서비스 nx_secure_tls_session_client_verify_enable을 통해 사용하도록 설정하거나 nx_secure_tls_session_x509_client_verify_configure를 사용하여 구성해야 합니다.

5. TLS 1.0 또는 TLS 1.1만 사용하는 경우 TLSv1.2를 사용하지 않도록 설정할 수 있습니다. 그러나 이 방법은 권장되지 않으며 직접 지원되지 않습니다.
