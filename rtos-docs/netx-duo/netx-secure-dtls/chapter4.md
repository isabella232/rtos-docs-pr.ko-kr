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
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a><span data-ttu-id="0869c-103">챕터 4: Azure RTOS NetX Secure DTLS 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="0869c-103">Chapter 4: Description of Azure RTOS NetX Secure DTLS services</span></span>

<span data-ttu-id="0869c-104">이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX Secure DTLS 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-104">This chapter contains a description of all Azure RTOS NetX Secure DTLS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="0869c-105">다음 API 설명의 "반환 값" 섹션에서, **BOLD** 의 값은 API 오류 검사를 해제하는 데 사용되는 **NX_SECURE_DISABLE_ERROR_CHECKING** 매크로의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="0869c-106">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-106">nx_secure_dtls_client_session_start</span></span>](#nx_secure_dtls_client_session_start)
- [<span data-ttu-id="0869c-107">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="0869c-107">nx_secure_dtls_packet_allocate</span></span>](#nx_secure_dtls_packet_allocate)
- [<span data-ttu-id="0869c-108">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="0869c-108">nx_secure_dtls_psk_add</span></span>](#nx_secure_dtls_psk_add)
- [<span data-ttu-id="0869c-109">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-109">nx_secure_dtls_server_create</span></span>](#nx_secure_dtls_server_create)
- [<span data-ttu-id="0869c-110">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-110">nx_secure_dtls_server_delete</span></span>](#nx_secure_dtls_server_delete)
- [<span data-ttu-id="0869c-111">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-111">nx_secure_dtls_server_local_certificate_add</span></span>](#nx_secure_dtls_server_local_certificate_add)
- [<span data-ttu-id="0869c-112">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-112">nx_secure_dtls_server_local_certificate_remove</span></span>](#nx_secure_dtls_server_local_certificate_remove)
- [<span data-ttu-id="0869c-113">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="0869c-113">nx_secure_dtls_server_notify_set</span></span>](#nx_secure_dtls_server_notify_set)
- [<span data-ttu-id="0869c-114">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="0869c-114">nx_secure_dtls_server_psk_add</span></span>](#nx_secure_dtls_server_psk_add)
- [<span data-ttu-id="0869c-115">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-115">nx_secure_dtls_server_session_send</span></span>](#nx_secure_dtls_server_session_send)
- [<span data-ttu-id="0869c-116">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-116">nx_secure_dtls_server_session_start</span></span>](#nx_secure_dtls_server_session_start)
- [<span data-ttu-id="0869c-117">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="0869c-117">nx_secure_dtls_server_start</span></span>](#nx_secure_dtls_server_start)
- [<span data-ttu-id="0869c-118">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="0869c-118">nx_secure_dtls_server_stop</span></span>](#nx_secure_dtls_server_stop)
- [<span data-ttu-id="0869c-119">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-119">nx_secure_dtls_server_trusted_certificate_add</span></span>](#nx_secure_dtls_server_trusted_certificate_add)
- [<span data-ttu-id="0869c-120">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-120">nx_secure_dtls_server_trusted_certificate_remove</span></span>](#nx_secure_dtls_server_trusted_certificate_remove)
- [<span data-ttu-id="0869c-121">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="0869c-121">nx_secure_dtls_server_x509_client_verify_configure</span></span>](#nx_secure_dtls_server_x509_client_verify_configure)
- [<span data-ttu-id="0869c-122">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="0869c-122">nx_secure_dtls_server_x509_client_verify_disable</span></span>](#nx_secure_dtls_server_x509_client_verify_disable)
- [<span data-ttu-id="0869c-123">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="0869c-123">nx_secure_dtls_session_client_info_get</span></span>](#nx_secure_dtls_session_client_info_get)
- [<span data-ttu-id="0869c-124">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="0869c-124">nx_secure_dtls_session_create</span></span>](#nx_secure_dtls_session_create)
- [<span data-ttu-id="0869c-125">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-125">nx_secure_dtls_session_delete</span></span>](#nx_secure_dtls_session_delete)
- [<span data-ttu-id="0869c-126">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="0869c-126">nx_secure_dtls_session_end</span></span>](#nx_secure_dtls_session_end)
- [<span data-ttu-id="0869c-127">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-127">nx_secure_dtls_session_local_certificate_add</span></span>](#nx_secure_dtls_session_local_certificate_add)
- [<span data-ttu-id="0869c-128">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-128">nx_secure_dtls_session_local_certificate_remove</span></span>](#nx_secure_dtls_session_local_certificate_remove)
- [<span data-ttu-id="0869c-129">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-129">nx_secure_dtls_session_receive</span></span>](#nx_secure_dtls_session_receive)
- [<span data-ttu-id="0869c-130">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="0869c-130">nx_secure_dtls_session_reset</span></span>](#nx_secure_dtls_session_reset)
- [<span data-ttu-id="0869c-131">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-131">nx_secure_dtls_ session_send</span></span>](#nx_secure_dtls_-session_send)
- [<span data-ttu-id="0869c-132">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-132">nx_secure_dtls_session_trusted_certificate_add</span></span>](#nx_secure_dtls_session_trusted_certificate_add)
- [<span data-ttu-id="0869c-133">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-133">nx_secure_dtls_session_trusted_certificate_remove</span></span>](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a><span data-ttu-id="0869c-134">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-134">nx_secure_dtls_client_session_start</span></span>

<span data-ttu-id="0869c-135">NetX Secure DTLS 클라이언트 세션 시작</span><span class="sxs-lookup"><span data-stu-id="0869c-135">Start a NetX Secure DTLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-136">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-136">Prototype</span></span>

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="0869c-137">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-137">Description</span></span>

<span data-ttu-id="0869c-138">이 서비스는 DTLS 클라이언트 세션을 시작하고, 제공된 IP 주소 및 UDP 포트의 서버에 연결하고, 제공된 UDP 소켓을 네트워크 통신에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-138">This service starts a DTLS Client session, connecting to the server at the provided IP address and UDP port, using the provided UDP socket for network communications.</span></span>

<span data-ttu-id="0869c-139">nx_secure_dtls_session_create를 사용하여 이 서비스를 호출하려면 먼저 DTLS 세션 제어 블록을 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-139">The DTLS session control block must be initialized prior to calling this service using nx_secure_dtls_session_create.</span></span> <span data-ttu-id="0869c-140">또한 DTLS 클라이언트는 nx_secure_dtls_session_trusted_certificate_add를 사용하여 세션에 하나 이상의 신뢰할 수 있는 CA 인증서를 추가하거나 미리 공유한 키를 사용하도록 설정하고 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-140">Additionally, the DTLS Client requires that at least one trusted CA certificate has been added to the session using nx_secure_dtls_session_trusted_certificate_add or Pre-Shared Keys are enabled and configured.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-141">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-141">Parameters</span></span>

- <span data-ttu-id="0869c-142">**dtls_session** 이전에 초기화된 DTLS 세션 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-142">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="0869c-143">**udp_socket** 초기화된 UDP 소켓으로, 원격 DTLS 서버와의 네트워크 통신을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-143">**udp_socket** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="0869c-144">**ip_address** 원격 DTLS 서버의 주소를 포함하는 IP 주소 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-144">**ip_address** Pointer to IP address structure containing the address of the remote DTLS server.</span></span>
- <span data-ttu-id="0869c-145">**port** 초기화된 UDP 소켓으로, 원격 DTLS 서버와의 네트워크 통신을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-145">**port** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="0869c-146">**wait_option** 연결 시도의 일시 중단 옵션</span><span class="sxs-lookup"><span data-stu-id="0869c-146">**wait_option** Suspension option for connection attempt.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-147">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-147">Return Values</span></span>

- <span data-ttu-id="0869c-148">**NX_SUCCESS** (0x00) 세션에 인증서를 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-148">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="0869c-149">**NX_NOT_CONNECTED** (0x38) 지정된 주소 및 포트에서 서버에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-149">**NX_NOT_CONNECTED** (0x38) The server cannot be reached at the given address and port.</span></span>
- <span data-ttu-id="0869c-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) 받은 TLS/DTLS 메시지 유형이 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS/DTLS message type is incorrect.</span></span>
- <span data-ttu-id="0869c-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) 원격 호스트에서 제공하는 암호화가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="0869c-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) TLS 핸드셰이크 중 메시지 처리가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="0869c-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) 들어오는 메시지가 해시 MAC 검사에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="0869c-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 기본 TCP 소켓 보내기가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="0869c-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 들어오는 메시지의 길이 필드가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="0869c-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) 들어오는 ChangeCipherSpec 메시지가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="0869c-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) 들어오는 TLS 인증서를 원격 DTLS 서버 식별에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote DTLS server.</span></span>
- <span data-ttu-id="0869c-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) 원격 호스트에서 제공하는 공개 키 암호가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="0869c-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) NetX Secure DTLS 스택에서 지원하는 ciphersuite가 없다고 원격 호스트에서 알렸습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure DTLS stack.</span></span>
- <span data-ttu-id="0869c-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) 받은 DTLS 메시지의 헤더에 알 수 없는 DTLS 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received DTLS message had an unknown DTLS version in its header.</span></span>
- <span data-ttu-id="0869c-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) 받은 DTLS 메시지의 헤더에 알고 있지만 지원되지 않는 DTLS 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received DTLS message had a known but unsupported DTLS version in its header.</span></span>
- <span data-ttu-id="0869c-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) 내부 TLS 패킷을 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="0869c-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) 원격 호스트에서 제공한 인증서가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="0869c-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) 원격 호스트가 오류를 알리는 경고를 보내고 TLS 세션을 종료했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="0869c-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) ciphersuite 테이블의 항목에 NULL 함수 포인터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="0869c-166">**NX_PTR_ERROR** (0x07) 세션, 소켓 또는 주소 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-166">**NX_PTR_ERROR** (0x07) Invalid session, socket, or address pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-167">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-167">Allowed From</span></span>

<span data-ttu-id="0869c-168">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-169">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-169">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-170">See Also</span></span>

- <span data-ttu-id="0869c-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send,</span></span>
- <span data-ttu-id="0869c-172">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="0869c-172">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_packet_allocate"></a><span data-ttu-id="0869c-173">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="0869c-173">nx_secure_dtls_packet_allocate</span></span>

<span data-ttu-id="0869c-174">NetX Secure DTLS 세션에 대한 패킷 할당</span><span class="sxs-lookup"><span data-stu-id="0869c-174">Allocate a packet for a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-175">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-175">Prototype</span></span>

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="0869c-176">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-176">Description</span></span>

<span data-ttu-id="0869c-177">이 서비스는 지정된 NX_PACKET_POOL의 지정된 활성 DTLS 세션에 대한 NX_PACKET을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-177">This service allocates an NX_PACKET for the specified active DTLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="0869c-178">애플리케이션에서 이 서비스를 호출하여 DTLS 연결을 통해 보낼 데이터 패킷을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-178">This service should be called by the application to allocate data packets to be sent over a DTLS connection.</span></span> <span data-ttu-id="0869c-179">이 서비스를 호출하려면 먼저 DTLS 세션을 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-179">The DTLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="0869c-180">패킷 데이터가 채워진 후 DTLS 헤더 및 바닥글 데이터를 추가할 수 있도록 할당된 패킷이 올바르게 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-180">The allocated packet is properly initialized so that DTLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="0869c-181">그렇지 않으면 이 동작은 *nx_packet_allocate* 와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-181">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-182">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-182">Parameters</span></span>

- <span data-ttu-id="0869c-183">**session_ptr** DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-183">**session_ptr** Pointer to a DTLS Session instance.</span></span>
- <span data-ttu-id="0869c-184">**pool_ptr** 패킷을 할당할 NX_PACKET_POOL에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-184">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="0869c-185">**packet_ptr** 새로 할당된 패킷에 대한 출력 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-185">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="0869c-186">**wait_option** 패킷 할당의 일시 중단 옵션</span><span class="sxs-lookup"><span data-stu-id="0869c-186">**wait_option** Suspension option for packet allocation.</span></span>


### <a name="return-values"></a><span data-ttu-id="0869c-187">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-187">Return Values</span></span>

- <span data-ttu-id="0869c-188">**NX_SUCCESS** (0x00) 패킷을 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-188">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="0869c-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) 기본 패킷을 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="0869c-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) 제공된 DTLS 세션이 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied DTLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-191">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-191">Allowed From</span></span>

<span data-ttu-id="0869c-192">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-192">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-193">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-193">Example</span></span>

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a><span data-ttu-id="0869c-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-194">See Also</span></span>

- <span data-ttu-id="0869c-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="0869c-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,</span></span>
- <span data-ttu-id="0869c-196">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-196">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="0869c-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_psk_add"></a><span data-ttu-id="0869c-199">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="0869c-199">nx_secure_dtls_psk_add</span></span>

<span data-ttu-id="0869c-200">NetX Secure DTLS 세션에 미리 공유한 키 추가</span><span class="sxs-lookup"><span data-stu-id="0869c-200">Add a Pre-Shared Key to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-201">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-201">Prototype</span></span>

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="0869c-202">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-202">Description</span></span>

<span data-ttu-id="0869c-203">이 서비스는 PSK(미리 공유한 키), 해당 ID 문자열 및 ID 힌트를 DTLS 세션 제어 블록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-203">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Session control block.</span></span> <span data-ttu-id="0869c-204">PSK는 PSK ciphersuite를 설정하고 사용할 때 디지털 인증서 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-204">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-205">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-205">Parameters</span></span>

- <span data-ttu-id="0869c-206">**session_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-206">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="0869c-207">**pre_shared_key** 실제 PSK 값</span><span class="sxs-lookup"><span data-stu-id="0869c-207">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="0869c-208">**psk_length** PSK 값의 길이</span><span class="sxs-lookup"><span data-stu-id="0869c-208">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="0869c-209">**psk_identity** 이 PSK 값을 식별하는 데 사용되는 문자열</span><span class="sxs-lookup"><span data-stu-id="0869c-209">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="0869c-210">**identity_length** PSK ID의 길이</span><span class="sxs-lookup"><span data-stu-id="0869c-210">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="0869c-211">**hint** TLS 서버에서 선택할 PSK 그룹을 나타내는 데 사용되는 문자열</span><span class="sxs-lookup"><span data-stu-id="0869c-211">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="0869c-212">**hint_length** 힌트 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="0869c-212">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-213">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-213">Return Values</span></span>

- <span data-ttu-id="0869c-214">**NX_SUCCESS** (0x00) PSK를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-214">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="0869c-215">**NX_PTR_ERROR** (0x07) DTLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-215">**NX_PTR_ERROR** (0x07) Invalid DTLS session pointer.</span></span>
- <span data-ttu-id="0869c-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) 다른 PSK를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-217">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-217">Allowed From</span></span>

<span data-ttu-id="0869c-218">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-218">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-219">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-219">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a><span data-ttu-id="0869c-220">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-220">See Also</span></span>

- <span data-ttu-id="0869c-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span><span class="sxs-lookup"><span data-stu-id="0869c-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span></span>

## <a name="nx_secure_dtls_server_create"></a><span data-ttu-id="0869c-222">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-222">nx_secure_dtls_server_create</span></span>

<span data-ttu-id="0869c-223">NetX Secure DTLS 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="0869c-223">Create a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-224">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-224">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="0869c-225">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-225">Description</span></span>

<span data-ttu-id="0869c-226">이 서비스는 특정 UDP 포트에서 들어오는 DTLS 요청을 처리하는 DTLS 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-226">This service creates an instance of a DTLS server to handle incoming DTLS requests on a particular UDP port.</span></span> <span data-ttu-id="0869c-227">UDP가 상태 비저장이기 때문에 여러 클라이언트의 DTLS 요청은 단일 포트에서 들어올 수 있지만 다른 DTLS 세션은 활성 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-227">Due to the fact that UDP is stateless, DTLS requests from multiple clients can come in on a single port while other DTLS sessions are active.</span></span> <span data-ttu-id="0869c-228">따라서 서버는 활성 세션을 유지하고 들어오는 메시지를 적절한 처리기로 적절하게 라우팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-228">Thus, the server is needed to maintain active sessions and properly route incoming messages to the proper handler.</span></span>

<span data-ttu-id="0869c-229">ip_ptr 매개 변수는 DTLS 서버와 연결되어 있는(그리고 NX_SECURE_DTLS_SERVER 제어 블록에 저장된) 내부 UDP 소켓에 사용되는 NX_IP 인스턴스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-229">The ip_ptr parameter points to an NX_IP instance to be used for the internal UDP socket associated with the DTLS Server (and stored in the NX_SECURE_DTLS_SERVER control block).</span></span> <span data-ttu-id="0869c-230">IP 인스턴스와 포트는 nx_secure_dtls_server_start 서비스를 사용하여 서버를 인스턴스화하는 UDP 인터페이스를 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-230">The IP instance and port are used to define the UDP interface upon which the server is instantiated with the nx_secure_dtls_server_start service.</span></span>

<span data-ttu-id="0869c-231">세션 버퍼 매개 변수는 DTLS 서버에 대해 가능한 모든 동시 DTLS 세션의 제어 블록을 보관하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-231">The session buffer parameter is used to hold the control blocks for all the possible simultaneous DTLS sessions for the DTLS server.</span></span> <span data-ttu-id="0869c-232">NX_SECURE_DTLS_SESSION 제어 블록 구조 크기의 짝수 배수로 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-232">It should be allocated with a size that is an even multiple of the size of the NX_SECURE_DTLS_SESSION control block structure.</span></span>

<span data-ttu-id="0869c-233">nx_secure_tls_metadata_size_calculate API를 사용하여 필요한 메타데이터 크기를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-233">To calculate the necessary metadata size, the API nx_secure_tls_metadata_size_calculate may be used.</span></span>

<span data-ttu-id="0869c-234">packet_reassembly_buffer 매개 변수는 DTLS에서 암호 해독을 위해 UDP 데이터그램을 완전한 DTLS 레코드로 다시 어셈블하는 데 사용되며, 예상되는 최대 DTLS 레코드(DTLS 최대 레코드 크기는 16KB이지만 단일 레코드에 이렇게 많은 데이터를 보내는 애플리케이션은 많지 않음)를 수용할 만큼 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-234">The packet_reassembly_buffer parameter is used by DTLS to reassemble UDP datagrams into a complete DTLS record for the purposes of decryption and should be large enough to accommodate the largest expected DTLS record (16KB is the DTLS maximum record size but many applications don’t send that much data in a single record).</span></span>

<span data-ttu-id="0869c-235">connect_notify 콜백 루틴은 새 DTLS 클라이언트가 서버에 연결할 때마다 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-235">The connect_notify callback routine is invoked whenever a new DTLS client connects to the server.</span></span> <span data-ttu-id="0869c-236">그러면 애플리케이션에서 *nx_secure_dtls_server_session_start* 서비스를 사용하여 DTLS 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-236">It is up to the application to then start the DTLS session using the service *nx_secure_dtls_server_session_start*.</span></span> <span data-ttu-id="0869c-237">콜백 자체에서 세션을 시작할 수도 있지만, 모든 하위 수준 네트워크 프로세싱을 처리하는 데 사용되는 IP 스레드(예: UDP)를 통해 콜백이 호출될 때에만 콜백을 사용하여 애플리케이션 스레드(또는 애플리케이션에서 만든 전용 DTLS 스레드)에 연결을 알리는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-237">While the session may be started in the callback itself, it is recommended that the callback only be used to notify the application thread (or dedicated DTLS thread created by the application) of the connection as the callback is invoked by the IP thread which is used to process all lower-level network processing (e.g. UDP).</span></span> <span data-ttu-id="0869c-238">DTLS 세션 매개 변수(콜백에 매개 변수로 제공됨)를 저장하고 다른 스레드에서 nx_secure_dtls_server_session_start를 호출하는 간단한 방법으로 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-238">This can be as simple as saving the DTLS session parameter (provided as a parameter to the callback) and invoking nx_secure_dtls_server_session_start in the other thread.</span></span> <span data-ttu-id="0869c-239">connect_notify 콜백은 일반적으로 NX_SUCCESS을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-239">The connect_notify callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="0869c-240">receive_notify 콜백 루틴은 기존에 설정된 DTLS 세션과 일치하는 DTLS 레코드를 받을 때마다 호출됩니다(원격 호스트 IP 주소와 포트는 기존 세션을 식별하는 데 사용됨).</span><span class="sxs-lookup"><span data-stu-id="0869c-240">The receive_notify callback routine is invoked whenever a DTLS record is received that matches an existing established DTLS session (the remote host IP address and port are used to identify an existing session).</span></span> <span data-ttu-id="0869c-241">이는 DTLS를 통해 암호화된 후 전송되는 "애플리케이션 데이터"를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-241">This represents the “application data” that is encrypted and sent over DTLS.</span></span> <span data-ttu-id="0869c-242">애플리케이션은 제공된 DTLS 세션에서 *nx_secure_dtls_session_receive* 서비스를 호출하여 수신한 데이터를 검색해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-242">The application must call the service *nx_secure_dtls_session_receive* on the provided DTLS session to retrieve the received data.</span></span> <span data-ttu-id="0869c-243">connect_receive 콜백과 마찬가지로, 콜백이 IP 스레드에서 호출될 때 세션을 다른 스레드에 전달하여 메시지 프로세싱을 처리하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-243">As with the connect_receive callback, it is recommended that the session be passed to another thread to handle the message processing as the callback is invoked from the IP thread.</span></span> <span data-ttu-id="0869c-244">receive_notify 콜백은 일반적으로 NX_SUCCESS을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-244">The receive_notify callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-245">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-245">Parameters</span></span>

- <span data-ttu-id="0869c-246">**server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-246">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="0869c-247">**ip_ptr** 초기화된 NX_IP 제어 블록에 대한 포인터로, DTLS 서버의 네트워크 인터페이스로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-247">**ip_ptr** Pointer to an initialized NX_IP control block to use as the network interface for the DTLS server.</span></span>
- <span data-ttu-id="0869c-248">**port** DTLS 서버 UDP 소켓이 바인딩된 로컬 UDP 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-248">**port** The local UDP port to which the DTLS server UDP socket is bound.</span></span>
- <span data-ttu-id="0869c-249">**timeout** 네트워크 작업에 사용할 제한 시간 값</span><span class="sxs-lookup"><span data-stu-id="0869c-249">**timeout** Timeout value to use for network operations.</span></span>
- <span data-ttu-id="0869c-250">**session_buffer** 이 DTLS 서버 인스턴스에 할당된 모든 NX_SECURE_DTLS_SESSION 인스턴스의 제어 블록을 포함하는 버퍼 공간</span><span class="sxs-lookup"><span data-stu-id="0869c-250">**session_buffer** Buffer space to contain control blocks for all instances of NX_SECURE_DTLS_SESSION assigned to this DTLS Server instance.</span></span>
- <span data-ttu-id="0869c-251">**session_buffer_size** 세션 버퍼의 크기.</span><span class="sxs-lookup"><span data-stu-id="0869c-251">**session_buffer_size** Size of the session buffer.</span></span> <span data-ttu-id="0869c-252">DTLS 서버에 할당되는 DTLS 세션 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-252">This determines the number of DTLS sessions assigned to the DTLS Server.</span></span>
- <span data-ttu-id="0869c-253">**crypto_table** 모든 암호화 작업에 사용되는 TLS/DTLS 암호화 테이블 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-253">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="0869c-254">**crypto_metadata_buffer** 암호화 작업 계산 및 상태 정보에 사용되는 버퍼 공간</span><span class="sxs-lookup"><span data-stu-id="0869c-254">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="0869c-255">**crypto_metadata_size** 메타데이터 버퍼의 크기</span><span class="sxs-lookup"><span data-stu-id="0869c-255">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="0869c-256">**packet_reassembly_buffer** 암호 해독을 위해 DTLS에서 UDP 데이터를 DTLS 레코드로 다시 어셈블할 때 사용하는 버퍼</span><span class="sxs-lookup"><span data-stu-id="0869c-256">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="0869c-257">**packet_reassembly_buffer_size** 리어셈블리 버퍼의 크기.</span><span class="sxs-lookup"><span data-stu-id="0869c-257">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="0869c-258">일반적으로 16KB보다 커야 하지만 애플리케이션에 따라 더 작을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-258">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="0869c-259">**connect_notify** 원격 DTLS 클라이언트가 이 DTLS 서버에 연결하려고 할 때마다 호출되는 콜백 루틴</span><span class="sxs-lookup"><span data-stu-id="0869c-259">**connect_notify** Callback routine invoked whenever a remote DTLS Client attempts to connect to this DTLS server.</span></span>
- <span data-ttu-id="0869c-260">**receive_notify** 기존 DTLS 세션을 통해 애플리케이션 데이터를 받을 때마다 호출되는 콜백</span><span class="sxs-lookup"><span data-stu-id="0869c-260">**receive_notify** Callback invoked whenever application data is received over an existing DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-261">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-261">Return Values</span></span>

- <span data-ttu-id="0869c-262">**NX_SUCCESS** (0x00) DTLS 서버를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-262">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="0869c-263">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-263">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-264">**NX_INVALID_PARAMETERS** (0x4D) 세션, 패킷 리어셈블리 또는 암호화를 위한 버퍼 공간이 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-264">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for sessions, packet reassembly, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-265">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-265">Allowed From</span></span>

<span data-ttu-id="0869c-266">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-267">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-267">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-268">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-268">See Also</span></span>

- <span data-ttu-id="0869c-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="0869c-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="0869c-271">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-271">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="0869c-272">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="0869c-272">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="0869c-273">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-273">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_delete"></a><span data-ttu-id="0869c-274">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-274">nx_secure_dtls_server_delete</span></span>

<span data-ttu-id="0869c-275">NetX Secure DTLS 서버에서 사용하는 리소스 해제</span><span class="sxs-lookup"><span data-stu-id="0869c-275">Free up resources used by a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-276">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-276">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="0869c-277">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-277">Description</span></span>

<span data-ttu-id="0869c-278">이 서비스는 서버에서 사용하는 내부 UDP 소켓을 포함하여 DTLS 서버 인스턴스에 할당된 리소스를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-278">This service frees up the resources allocated to a DTLS Server instance, including the internal UDP socket used by the server.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-279">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-279">Parameters</span></span>

- <span data-ttu-id="0869c-280">**server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-280">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-281">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-281">Return Values</span></span>

- <span data-ttu-id="0869c-282">**NX_SUCCESS** (0x00) 서버를 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-282">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="0869c-283">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-283">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-284">**NX_STILL_BOUND** (0x42) UDP 소켓이 여전히 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-284">**NX_STILL_BOUND** (0x42) UDP socket is still bound.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-285">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-285">Allowed From</span></span>

<span data-ttu-id="0869c-286">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-287">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-287">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-288">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-288">See Also</span></span>

- <span data-ttu-id="0869c-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="0869c-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="0869c-291">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-291">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_local_certificate_add"></a><span data-ttu-id="0869c-292">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-292">nx_secure_dtls_server_local_certificate_add</span></span>

<span data-ttu-id="0869c-293">NetX Secure DTLS 서버에 로컬 서버 ID 인증서 추가</span><span class="sxs-lookup"><span data-stu-id="0869c-293">Add a local server identity certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-294">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-294">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="0869c-295">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-295">Description</span></span>

<span data-ttu-id="0869c-296">이 서비스는 DTLS 서버 인스턴스에 로컬 서버 ID 인증서를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-296">This service adds a local server identity certificate to a DTLS Server instance.</span></span> <span data-ttu-id="0869c-297">대체 인증 메커니즘(예: 미리 공유한 키)을 사용하지 않는 한, 클라이언트에서 DTLS 서버에 연결하려면 하나 이상의 ID 인증서가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-297">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="0869c-298">cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-298">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="0869c-299">이렇게 하면 DTLS 서버 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-299">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="0869c-300">X.509 서버 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-300">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-301">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-301">Parameters</span></span>

- <span data-ttu-id="0869c-302">**server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-302">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="0869c-303">**certificate** 이전에 초기화된 X.509 인증서 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-303">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="0869c-304">**cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자</span><span class="sxs-lookup"><span data-stu-id="0869c-304">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-305">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-305">Return Values</span></span>

- <span data-ttu-id="0869c-306">**NX_SUCCESS** (0x00) DTLS 서버에 인증서를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-306">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="0869c-307">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-307">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-308">**NX_INVALID_PARAMETERS** (0x4D) 인증서 ID 0이 전달되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-308">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-309">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-309">Allowed From</span></span>

<span data-ttu-id="0869c-310">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-311">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-311">Example</span></span>

<span data-ttu-id="0869c-312">\*보다 완전한 예제는 *nx_secure_dtls_server_create* 에 대한 참조를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-312">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-313">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-313">See Also</span></span>

- <span data-ttu-id="0869c-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="0869c-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="0869c-316">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-316">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="0869c-317">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-317">nx_secure_dtls_server_local_certificate_remove,</span></span>
- <span data-ttu-id="0869c-318">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="0869c-318">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_local_certificate_remove"></a><span data-ttu-id="0869c-319">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-319">nx_secure_dtls_server_local_certificate_remove</span></span>

<span data-ttu-id="0869c-320">NetX Secure DTLS 서버에서 로컬 서버 ID 인증서 제거</span><span class="sxs-lookup"><span data-stu-id="0869c-320">Remove a local server identity certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-321">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-321">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="0869c-322">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-322">Description</span></span>

<span data-ttu-id="0869c-323">이 서비스는 DTLS 서버 인스턴스에서 로컬 서버 ID 인증서를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-323">This service removes a local server identity certificate from a DTLS Server instance.</span></span> <span data-ttu-id="0869c-324">대체 인증 메커니즘(예: 미리 공유한 키)을 사용하지 않는 한, 클라이언트에서 DTLS 서버에 연결하려면 하나 이상의 ID 인증서가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-324">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="0869c-325">제거할 인증서는 해당 X.509 일반 이름 또는 *nx_secure_dtls_server_local_certificate_add* 호출에서 할당된 숫자 cert_id를 통해 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-325">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_local_certificate_add*.</span></span> <span data-ttu-id="0869c-326">cert_id는 인증서 식별에만 사용되며 애플리케이션에서 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-326">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="0869c-327">숫자 인증서 식별자 대신 일반 이름을 사용하는 경우에는 cert_id 매개 변수를 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-327">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="0869c-328">DTLS 핸드셰이크를 처리하는 동안 인증서를 제거하면 예기치 않은 동작이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-328">Removing a certificate while a DTLS handshake is being processed will result in unexpected behavior.</span></span> <span data-ttu-id="0869c-329">*nx_secure_dtls_server_stop* 서비스는 인증서를 제거하기 전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-329">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-330">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-330">Parameters</span></span>

- <span data-ttu-id="0869c-331">**server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-331">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="0869c-332">**common_name** 제거할 인증서의 X.509 CommonName.</span><span class="sxs-lookup"><span data-stu-id="0869c-332">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="0869c-333">사용할 경우 cert_id를 0으로 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-333">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="0869c-334">**common_name_length** common_name 문자열의 길이(바이트)</span><span class="sxs-lookup"><span data-stu-id="0869c-334">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="0869c-335">**cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자</span><span class="sxs-lookup"><span data-stu-id="0869c-335">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="0869c-336">사용할 경우 common_name 매개 변수에 NX_NULL를 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-336">If this is used, pass NX_NULL for the common_name parameter.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-337">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-337">Return Values</span></span>

- <span data-ttu-id="0869c-338">**NX_SUCCESS** (0x00) DTLS 서버에서 인증서를 제거했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-338">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="0869c-339">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-339">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 지정된 DTLS 서버에서 cert_id 또는 common_name과 일치하는 인증서를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-341">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-341">Allowed From</span></span>

<span data-ttu-id="0869c-342">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-343">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-343">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-344">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-344">See Also</span></span>

- <span data-ttu-id="0869c-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="0869c-346">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-346">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="0869c-347">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="0869c-347">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="0869c-348">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-348">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="0869c-349">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="0869c-349">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_notify_set"></a><span data-ttu-id="0869c-350">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="0869c-350">nx_secure_dtls_server_notify_set</span></span>

<span data-ttu-id="0869c-351">NetX Secure DTLS 서버에 선택적 알림 콜백 루틴 할당</span><span class="sxs-lookup"><span data-stu-id="0869c-351">Assign optional notification callback routines to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-352">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-352">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a><span data-ttu-id="0869c-353">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-353">Description</span></span>

<span data-ttu-id="0869c-354">이 서비스를 사용하여 DTLS 서버에 선택적 알림 콜백 루틴을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-354">This service can be used to add optional notification callback routines to a DTLS server.</span></span> <span data-ttu-id="0869c-355">콜백 매개 변수 중 하나만 사용하려면 콜백 매개 변수 중 하나를 NX_NULL로 전달하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-355">Either callback parameter may be passed as NX_NULL if only one callback is desired.</span></span>

<span data-ttu-id="0869c-356">disconnect_notify 콜백은 원격 클라이언트가 DTLS 세션을 종료할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-356">The disconnect_notify callback is invoked when a remote client ends a DTLS session.</span></span> <span data-ttu-id="0869c-357">dtls_session 매개 변수는 닫힌 세션 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-357">The dtls_session parameter is the session instance that was closed.</span></span> <span data-ttu-id="0869c-358">콜백은 일반적으로 NX_SUCCESS를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-358">The callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="0869c-359">error_notify 콜백은 DTLS 오류가 발생하거나 시간이 초과될 때마다 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-359">The error_notify callback is invoked whenever a DTLS error or timeout occurs.</span></span> <span data-ttu-id="0869c-360">dtls_session 매개 변수는 오류가 발생한 세션 인스턴스이고, error_code는 문제를 일으킨 오류의 숫자 상태 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-360">The dtls_session parameter is the session instance for which the error occurred, and error_code is the numeric status code for the error that caused the issue (see Appendix A)</span></span>

<span data-ttu-id="0869c-361">반환될 수 있는 오류 코드 목록은 부록 A) NetX Secure 반환/오류 코드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-361">NetX Secure Return/Error Codes for a list of error codes that may be returned).</span></span> <span data-ttu-id="0869c-362">콜백은 일반적으로 NX_SUCCESS를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-362">The callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-363">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-363">Parameters</span></span>

- <span data-ttu-id="0869c-364">**server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-364">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="0869c-365">**disconnect_notify** 원격 클라이언트 호스트가 DTLS 세션을 닫을 때마다 호출되는 콜백 루틴</span><span class="sxs-lookup"><span data-stu-id="0869c-365">**disconnect_notify** Callback routine invoked whenever a remote client host closes a DTLS session.</span></span>
- <span data-ttu-id="0869c-366">**error_notify** DTLS에서 오류 또는 시간 초과가 발생할 때마다 호출되는 콜백 루틴</span><span class="sxs-lookup"><span data-stu-id="0869c-366">**error_notify** Callback routine invoked whenever DTLS encounters an error or timeout.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-367">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-367">Return Values</span></span>

- <span data-ttu-id="0869c-368">**NX_SUCCESS** (0x00) 콜백 루틴을 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-368">**NX_SUCCESS** (0x00) Successful assignment of callback routines.</span></span>
- <span data-ttu-id="0869c-369">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-369">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-370">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-370">Allowed From</span></span>

<span data-ttu-id="0869c-371">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-371">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-372">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-372">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-373">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-373">See Also</span></span>

- <span data-ttu-id="0869c-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="0869c-375">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-375">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="0869c-376">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="0869c-376">nx_secure_dtls_server_session_stop</span></span>

## <a name="nx_secure_dtls_server_psk_add"></a><span data-ttu-id="0869c-377">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="0869c-377">nx_secure_dtls_server_psk_add</span></span>

<span data-ttu-id="0869c-378">NetX Secure DTLS 서버에 미리 공유한 키 추가</span><span class="sxs-lookup"><span data-stu-id="0869c-378">Add a Pre-Shared Key to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-379">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-379">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a><span data-ttu-id="0869c-380">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-380">Description</span></span>

<span data-ttu-id="0869c-381">이 서비스는 PSK(미리 공유한 키), 해당 ID 문자열 및 ID 힌트를 DTLS 서버 제어 블록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-381">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Server control block.</span></span> <span data-ttu-id="0869c-382">PSK는 PSK ciphersuite를 설정하고 사용할 때 디지털 인증서 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-382">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="0869c-383">추가된 PSK는 nx_secure_dtls_server_create 호출에 지정된 세션 버퍼를 통해 DTLS 서버에 할당된 모든 DTLS 세션에서 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-383">The PSK that is added is replicated across all the DTLS sessions assigned to the DTLS Server (via the session buffer given in the call to nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-384">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-384">Parameters</span></span>

- <span data-ttu-id="0869c-385">**server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-385">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="0869c-386">**pre_shared_key** 실제 PSK 값</span><span class="sxs-lookup"><span data-stu-id="0869c-386">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="0869c-387">**psk_length** PSK 값의 길이</span><span class="sxs-lookup"><span data-stu-id="0869c-387">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="0869c-388">**psk_identity** 이 PSK 값을 식별하는 데 사용되는 문자열</span><span class="sxs-lookup"><span data-stu-id="0869c-388">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="0869c-389">**identity_length** PSK ID의 길이</span><span class="sxs-lookup"><span data-stu-id="0869c-389">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="0869c-390">**hint** TLS 서버에서 선택할 PSK 그룹을 나타내는 데 사용되는 문자열</span><span class="sxs-lookup"><span data-stu-id="0869c-390">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="0869c-391">**hint_length** 힌트 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="0869c-391">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-392">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-392">Return Values</span></span>

- <span data-ttu-id="0869c-393">**NX_SUCCESS** (0x00) PSK를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-393">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="0869c-394">**NX_PTR_ERROR** (0x07) DTLS 서버 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-394">**NX_PTR_ERROR** (0x07) Invalid DTLS server pointer.</span></span>
- <span data-ttu-id="0869c-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) 다른 PSK를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-396">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-396">Allowed From</span></span>

<span data-ttu-id="0869c-397">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-398">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-398">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a><span data-ttu-id="0869c-399">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-399">See Also</span></span>

- <span data-ttu-id="0869c-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span></span>

## <a name="nx_secure_dtls_server_session_send"></a><span data-ttu-id="0869c-401">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-401">nx_secure_dtls_server_session_send</span></span>

<span data-ttu-id="0869c-402">NetX Secure DTLS 서버를 사용하여 설정된 DTLS 세션을 통해 데이터 보내기</span><span class="sxs-lookup"><span data-stu-id="0869c-402">Send data over a DTLS session established with a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-403">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-403">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="0869c-404">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-404">Description</span></span>

<span data-ttu-id="0869c-405">이 서비스는 설정된 DTLS 서버 세션을 통해 원격 DTLS 클라이언트 호스트로 데이터 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-405">This service sends a packet of data over an established DTLS Server session to a remote DTLS Client host.</span></span> <span data-ttu-id="0869c-406">사용되는 세션은 nx_secure_dtls_session_create에 제공된 receive_notify 콜백 루틴에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-406">The session used is obtained in the receive_notify callback routine provided to nx_secure_dtls_session_create.</span></span>

<span data-ttu-id="0869c-407">패킷에 제공된 데이터(*nx_secure_dtls_packet_allocate* 를 사용하여 할당해야 함)는 DTLS 세션 암호화 매개 변수 및 루틴을 사용하여 암호화된 후 DTLS 서버 내부 UDP 포트를 통해 연결된 클라이언트의 IP 주소 및 포트에 전송됩니다(DTLS 세션에 저장됨).</span><span class="sxs-lookup"><span data-stu-id="0869c-407">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Server internal UDP port to the attached client’s IP address and port (stored in the DTLS Session).</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-408">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-408">Parameters</span></span>

- <span data-ttu-id="0869c-409">**session_ptr** 애플리케이션에서 제공하는 receive_notify 콜백 루틴에서 얻은 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-409">**session_ptr** Pointer to a DTLS session instance obtained from the receive_notify callback routine provided by the application.</span></span>
- <span data-ttu-id="0869c-410">**packet_ptr** 이전에 할당되어 애플리케이션 데이터로 채워진 NX_PACKET 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-410">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-411">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-411">Return Values</span></span>

- <span data-ttu-id="0869c-412">**NX_SUCCESS** (0x00) DTLS 서버를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-412">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="0869c-413">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-413">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 기본 UDP 전송 작업에서 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-415">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-415">Allowed From</span></span>

<span data-ttu-id="0869c-416">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-417">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-417">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-418">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-418">See Also</span></span>

- <span data-ttu-id="0869c-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="0869c-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create</span><span class="sxs-lookup"><span data-stu-id="0869c-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,</span></span>
- <span data-ttu-id="0869c-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="0869c-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="0869c-422">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-422">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_session_start"></a><span data-ttu-id="0869c-423">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-423">nx_secure_dtls_server_session_start</span></span>

<span data-ttu-id="0869c-424">NetX Secure DTLS 서버에서 DTLS 세션 시작</span><span class="sxs-lookup"><span data-stu-id="0869c-424">Start a DTLS Session from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-425">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-425">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="0869c-426">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-426">Description</span></span>

<span data-ttu-id="0869c-427">이 서비스는 원격 DTLS 클라이언트가 서버에 연결하여 DTLS 연결을 요청할 때 서버 쪽 DTLS 핸드셰이크를 수행하여 DTLS 서버 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-427">This service starts a DTLS Server session by performing the server-side DTLS handshake when a remote DTLS Client has connected to the server and requested a DTLS connection.</span></span>

<span data-ttu-id="0869c-428">DTLS 세션은 nx_secure_dtls_server_create에 제공된 connect_notify 콜백 루틴에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-428">The DTLS Session is obtained in the connect_notify callback routine provided to nx_secure_dtls_server_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-429">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-429">Parameters</span></span>

- <span data-ttu-id="0869c-430">**session_ptr** DTLS 서버 connect_notify 콜백에서 가져온 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-430">**session_ptr** Pointer to a DTLS Session instance obtained from a DTLS Server connect_notify callback.</span></span>
- <span data-ttu-id="0869c-431">**wait_option** 네트워크 작업에 사용할 ThreadX 대기 값</span><span class="sxs-lookup"><span data-stu-id="0869c-431">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-432">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-432">Return Values</span></span>

- <span data-ttu-id="0869c-433">**NX_SUCCESS** (0x00) DTLS 서버를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-433">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="0869c-434">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-434">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) DTLS 핸드셰이크 패킷을 할당할 수 없습니다(패킷 풀이 비어 있음).</span><span class="sxs-lookup"><span data-stu-id="0869c-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a DTLS handshake packet (packet pool empty).</span></span>
- <span data-ttu-id="0869c-436">**NX_SECURE_TLS_INVALID_PACKET** (0x104) 수신한 데이터가 유효한 DTLS 레코드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-436">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="0869c-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) DTLS 레코드를 올바르게 해시하지 못했습니다(암호화 오류).</span><span class="sxs-lookup"><span data-stu-id="0869c-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="0869c-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) 암호화 패딩 검사가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="0869c-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) DTLS 핸드셰이크 중에 원격 호스트에서 경고를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host during the DTLS handshake.</span></span>
- <span data-ttu-id="0869c-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) DTLS 핸드셰이크 중에 인식할 수 없는 메시지를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Received an unrecognized message during the DTLS handshake.</span></span>
- <span data-ttu-id="0869c-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 받은 DTLS 레코드의 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="0869c-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) 받은 ClientHello가 DTLS ciphersuite를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Received a ClientHello with no supported DTLS ciphersuites.</span></span>
- <span data-ttu-id="0869c-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) 받은 ClientHello의 압축 방법을 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) Recevied a ClientHello with a unknown compression method.</span></span>
- <span data-ttu-id="0869c-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) 일반적인(지정되지 않은) 핸드셰이크 오류가 발생했습니다. 대부분 확장 처리 문제로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Generic (unspecified) handshake failure, usually due to problems with extension processing.</span></span>
- <span data-ttu-id="0869c-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) DTLS 핸드셰이크 중에 아직 지원되지 않는 기능이 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) A feature that is not yet supported was invoked during the DTLS handshake.</span></span>
- <span data-ttu-id="0869c-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) 알 수 없는 ciphersuite가 발생했습니다(내부 암호화 오류가 표시됨).</span><span class="sxs-lookup"><span data-stu-id="0869c-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicated internal cryptography error).</span></span>
- <span data-ttu-id="0869c-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) 받은 DTLS 레코드의 DTLS 버전이 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>
- <span data-ttu-id="0869c-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) DTLS 핸드셰이크 해시의 유효성을 검사하지 못했습니다. 세션이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) Failed to validate the DTLS handshake hash, session is invalid.</span></span>
- <span data-ttu-id="0869c-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 내부 UDP 전송이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Internal UDP send failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-450">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-450">Allowed From</span></span>

<span data-ttu-id="0869c-451">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-452">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-452">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-453">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-453">See Also</span></span>

- <span data-ttu-id="0869c-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="0869c-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="0869c-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="0869c-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="0869c-457">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-457">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_start"></a><span data-ttu-id="0869c-458">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="0869c-458">nx_secure_dtls_server_start</span></span>

<span data-ttu-id="0869c-459">구성된 UDP 포트에서 수신 대기하는 NetX Secure DTLS 서버 인스턴스 시작</span><span class="sxs-lookup"><span data-stu-id="0869c-459">Start a NetX Secure DTLS Server instance listening on the configured UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-460">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-460">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="0869c-461">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-461">Description</span></span>

<span data-ttu-id="0869c-462">이 서비스는 DTLS 서버를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-462">This service starts a DTLS Server.</span></span> <span data-ttu-id="0869c-463">호출이 반환되면 서버가 활성 상태이고 DTLS 클라이언트에서 들어오는 요청을 처리하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-463">After the call returns, the server is active and will begin processing incoming requests from DTLS clients.</span></span> <span data-ttu-id="0869c-464">서버 인스턴스는 *nx_secure_dtls_server_create* 서비스를 사용하여 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-464">The server instance must have been configured with the service *nx_secure_dtls_server_create*.</span></span>

> [!NOTE]
> <span data-ttu-id="0869c-465">이 서비스는 내부 DTLS 서버 UDP 포트를 구성된 로컬 포트에 바인딩하므로, 발생하는 대부분의 문제는 UDP 통신 및 네트워크 구성과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-465">This service binds the internal DTLS Server UDP port to the configured local port so most issues encountered will have to do with UDP communications and network configuration.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-466">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-466">Parameters</span></span>

- <span data-ttu-id="0869c-467">**server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-467">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-468">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-468">Return Values</span></span>

- <span data-ttu-id="0869c-469">**NX_SUCCESS** (0x00) 서버를 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-469">**NX_SUCCESS** (0x00) Successful start of server.</span></span>
- <span data-ttu-id="0869c-470">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-470">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-471">**NX_NOT_ENABLED** (0x14) UDP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-471">**NX_NOT_ENABLED** (0x14) UDP not enabled.</span></span>
- <span data-ttu-id="0869c-472">**NX_NO_FREE_PORTS** (0x45) 사용 가능한 UDP 포트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-472">**NX_NO_FREE_PORTS** (0x45) No available UDP ports.</span></span>
- <span data-ttu-id="0869c-473">**NX_INVALID_PORT** (0x46) UDP 포트가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-473">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="0869c-474">**NX_ALREADY_BOUND** (0x22) UDP 포트가 이미 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-474">**NX_ALREADY_BOUND** (0x22) UDP port already bound.</span></span>
- <span data-ttu-id="0869c-475">**NX_PORT_UNAVAILABLE** (0x23) UDP 포트를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-475">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-476">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-476">Allowed From</span></span>

<span data-ttu-id="0869c-477">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-478">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-478">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-479">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-479">See Also</span></span>

- <span data-ttu-id="0869c-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="0869c-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-482">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-482">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="0869c-483">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-483">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_stop"></a><span data-ttu-id="0869c-484">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="0869c-484">nx_secure_dtls_server_stop</span></span>

<span data-ttu-id="0869c-485">활성 NetX Secure DTLS 서버 인스턴스 중지</span><span class="sxs-lookup"><span data-stu-id="0869c-485">Stop an active NetX Secure DTLS Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-486">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-486">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="0869c-487">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-487">Description</span></span>

<span data-ttu-id="0869c-488">이 서비스는 구성된 UDP 포트에서 DTLS 서버가 수신 대기하는 것을 중지하고, 연결된 모든 DTLS 세션을 초기화하고, 진행 중인 DTLS 통신을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-488">This service stops a DTLS Server from listening on the configure UDP port and resets all the associated DTLS sessions, halting any in-progress DTLS communications.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-489">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-489">Parameters</span></span>

- <span data-ttu-id="0869c-490">**server_ptr** 활성 DTLS 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-490">**server_ptr** Pointer to an active DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-491">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-491">Return Values</span></span>

- <span data-ttu-id="0869c-492">**NX_SUCCESS** (0x00) 서버를 중지했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-492">**NX_SUCCESS** (0x00) Successful stop of server.</span></span>
- <span data-ttu-id="0869c-493">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-493">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-494">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-494">Allowed From</span></span>

<span data-ttu-id="0869c-495">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-495">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-496">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-496">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-497">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-497">See Also</span></span>

- <span data-ttu-id="0869c-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="0869c-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-500">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-500">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="0869c-501">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-501">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a><span data-ttu-id="0869c-502">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-502">nx_secure_dtls_server_trusted_certificate_add</span></span>

<span data-ttu-id="0869c-503">NetX Secure DTLS 서버에 신뢰할 수 있는 CA 인증서 추가</span><span class="sxs-lookup"><span data-stu-id="0869c-503">Add a trusted CA certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-504">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-504">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="0869c-505">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-505">Description</span></span>

<span data-ttu-id="0869c-506">이 서비스는 DTLS 서버 인스턴스에 신뢰할 수 있는 CA 또는 중간 CA 인증서를 추가하고 모든 내부 DTLS 서버 세션에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-506">This service adds a trusted CA or intermediate CA certificate to a DTLS Server instance and assigned to all the internal DTLS server sessions.</span></span> <span data-ttu-id="0869c-507">*nx_secure_dtls_server_x509_client_verify_configure* 를 사용하여 X.509 클라이언트 인증서 인증을 사용하도록 설정한 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-507">This is only necessary if X.509 Client certificate authentication is enabled using *nx_secure_dtls_server_x509_client_verify_configure*.</span></span> <span data-ttu-id="0869c-508">추가된 인증서는 들어오는 클라이언트 X.509 인증서를 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-508">The added certificate will be used to verify incoming Client X.509 certificates.</span></span>

<span data-ttu-id="0869c-509">cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-509">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="0869c-510">이렇게 하면 DTLS 서버 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-510">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="0869c-511">X.509 서버 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-511">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-512">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-512">Parameters</span></span>

- <span data-ttu-id="0869c-513">**server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-513">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="0869c-514">**certificate** 이전에 초기화된 X.509 인증서 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-514">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="0869c-515">**cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자</span><span class="sxs-lookup"><span data-stu-id="0869c-515">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-516">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-516">Return Values</span></span>

- <span data-ttu-id="0869c-517">**NX_SUCCESS** (0x00) DTLS 서버에 인증서를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-517">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="0869c-518">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-518">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-519">**NX_INVALID_PARAMETERS** (0x4D) 인증서 ID 0이 전달되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-519">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-520">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-520">Allowed From</span></span>

<span data-ttu-id="0869c-521">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-521">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-522">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-522">Example</span></span>

<span data-ttu-id="0869c-523">\*보다 완전한 예제는 *nx_secure_dtls_server_create* 에 대한 참조를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-523">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-524">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-524">See Also</span></span>

- <span data-ttu-id="0869c-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="0869c-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="0869c-527">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-527">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="0869c-528">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-528">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="0869c-529">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-529">nx_secure_dtls_server_trusted_certificate_remove,</span></span>
- <span data-ttu-id="0869c-530">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="0869c-530">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a><span data-ttu-id="0869c-531">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-531">nx_secure_dtls_server_trusted_certificate_remove</span></span>

<span data-ttu-id="0869c-532">NetX Secure DTLS 서버에서 신뢰할 수 있는 CA 인증서 제거</span><span class="sxs-lookup"><span data-stu-id="0869c-532">Remove a trusted CA certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-533">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-533">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="0869c-534">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-534">Description</span></span>

<span data-ttu-id="0869c-535">이 서비스는 DTLS 서버 인스턴스에서 신뢰할 수 있는 CA 인증서를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-535">This service removes a trusted CA certificate from a DTLS Server instance.</span></span> <span data-ttu-id="0869c-536">신뢰할 수 있는 CA 인증서는 *nx_secure_dtls_server_x509_client_verify_configure* 를 호출하여 X.509 클라이언트 인증서 확인을 사용하도록 설정한 DTLS 서버에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-536">Trusted CA certificates are only necessary for a DTLS Server for which X.509 Client certificate verification has been enabled by calling *nx_secure_dtls_server_x509_client_verify_configure*.</span></span>

<span data-ttu-id="0869c-537">제거할 인증서는 X.509 일반 이름 또는 *nx_secure_dtls_server_trusted_certificate_add* 호출에서 할당된 숫자 cert_id를 통해 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-537">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_trusted_certificate_add*.</span></span> <span data-ttu-id="0869c-538">cert_id는 인증서 식별에만 사용되며 애플리케이션에서 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-538">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="0869c-539">숫자 인증서 식별자 대신 일반 이름을 사용하는 경우에는 cert_id 매개 변수를 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-539">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="0869c-540">DTLS 핸드셰이크를 처리하는 동안 인증서를 제거하면 예기치 않은 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-540">Removing a certificate while a DTLS handshake is being processed may result in unexpected behavior.</span></span> <span data-ttu-id="0869c-541">*nx_secure_dtls_server_stop* 서비스는 인증서를 제거하기 전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-541">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-542">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-542">Parameters</span></span>

- <span data-ttu-id="0869c-543">**server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-543">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="0869c-544">**common_name** 제거할 인증서의 X.509 CommonName.</span><span class="sxs-lookup"><span data-stu-id="0869c-544">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="0869c-545">사용할 경우 cert_id를 0으로 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-545">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="0869c-546">**common_name_length** common_name 문자열의 길이(바이트)</span><span class="sxs-lookup"><span data-stu-id="0869c-546">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="0869c-547">**cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자</span><span class="sxs-lookup"><span data-stu-id="0869c-547">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="0869c-548">사용할 경우 common_name 매개 변수에 NX_NULL를 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-548">If this is used, pass NX_NULL for the common_name parameter.</span></span>


### <a name="return-values"></a><span data-ttu-id="0869c-549">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-549">Return Values</span></span>

- <span data-ttu-id="0869c-550">**NX_SUCCESS** (0x00) DTLS 서버에서 인증서를 제거했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-550">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="0869c-551">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-551">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 지정된 DTLS 서버에서 cert_id 또는 common_name과 일치하는 인증서를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-553">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-553">Allowed From</span></span>

<span data-ttu-id="0869c-554">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-555">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-555">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-556">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-556">See Also</span></span>

- <span data-ttu-id="0869c-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="0869c-558">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-558">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="0869c-559">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="0869c-559">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="0869c-560">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-560">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="0869c-561">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="0869c-561">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a><span data-ttu-id="0869c-562">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="0869c-562">nx_secure_dtls_server_x509_client_verify_configure</span></span>

<span data-ttu-id="0869c-563">클라이언트 인증서를 요청하고 확인하도록 NetX Secure DTLS 서버 구성</span><span class="sxs-lookup"><span data-stu-id="0869c-563">Configure a NetX Secure DTLS Server to request and verify client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-564">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-564">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a><span data-ttu-id="0869c-565">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-565">Description</span></span>

<span data-ttu-id="0869c-566">이 서비스는 DTLS 클라이언트 인증서를 요청하고 확인하도록 DTLS 서버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-566">This service configures a DTLS Server to request and verify DTLS Client certificates.</span></span> <span data-ttu-id="0869c-567">이 선택적 기능은 클라이언트 인증에 다른 메커니즘(예: 미리 공유한 키) 대신 X.509 인증서가 필요한 경우에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-567">This optional feature is used when X.509 certificates are desired for client authentication in place of other mechanisms (e.g. a Pre-Shared Key).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0869c-568">*이 서비스를 사용하여 클라이언트 인증서를 확인하도록 DTLS 서버를 구성한 경우 nx_secure_dtls_server_trusted_certificate_add를 사용하여 신뢰할 수 있는 CA 인증서를 하나 이상 서버에 추가해야 합니다. 그렇지 않으면 서버는 신뢰할 수 있는 저장소와 대조하여 클라이언트 인증서를 확인할 수 없기 때문에 들어오는 모든 클라이언트 연결을 거부합니다.*</span><span class="sxs-lookup"><span data-stu-id="0869c-568">*When a DTLS Server is configured to verify client certificates using this service, at least one trusted CA certificate must be added to the server using nx_secure_dtls_server_trusted_certificate_add or the server will reject all incoming client connections because it will be unable to verify client certificates against the trusted store.*</span></span>

<span data-ttu-id="0869c-569">이 서비스를 호출하면 DTLS 서버 인스턴스가 (시작된 후) DTLS 핸드셰이크의 일부로 클라이언트 인증서를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-569">Upon calling this service, the DTLS Server instance will (once started) request client certificates as part of the DTLS handshake.</span></span> <span data-ttu-id="0869c-570">ID 인증서(및 해당하는 경우 연결된 인증서 체인)를 사용하여 클라이언트를 적절하게 구성하면 DTLS 서버에서는 클라이언트 인증서 데이터를 처리하기 위한 메모리 할당을 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-570">Assuming the client is properly configured with an identity certificate (and associated certificate chain when applicable), the DTLS Server requires memory to be allocated to process the client certificate data.</span></span> <span data-ttu-id="0869c-571">이 메모리는 *certs_buffer* 매개 변수로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-571">This memory is passed in as the *certs_buffer* parameter.</span></span>

<span data-ttu-id="0869c-572">certs_buffer는 DTLS 클라이언트에서 예상되는 가장 큰 인증서 체인을 수용할 수 있는 크기에 *DTLS 서버 세션 수를 곱한 값* 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-572">The certs_buffer must be sized to accommodate the largest expected certificate chain from a DTLS client, *times the number of DTLS server sessions*.</span></span> <span data-ttu-id="0869c-573">버퍼는 클라이언트 인증서 체인에서 예상되는 최대 인증서 수를 나타내는 *certs_per_session* 매개 변수를 통해 사용 가능한 세션 간에 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-573">The buffer is divided amongst the available sessions using the *certs_per_session* parameter which represents the maximum expected number of certificates in a Client certificate chain.</span></span> <span data-ttu-id="0869c-574">또한 버퍼는 인증서 데이터를 구문 분석하는 데 사용되는 NX_SECURE_X509_CERT 데이터 구조를 위한 공간을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-574">The buffer also needs to provide space for the NX_SECURE_X509_CERT data structure which is used to parse the certificate data.</span></span>

<span data-ttu-id="0869c-575">적절한 버퍼 크기는 다음 수식으로 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-575">Calculating the proper buffer size can be done with the following formula:</span></span>

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- <span data-ttu-id="0869c-576">DTLS 세션 수는 nx_secure_dtls_server_create에 전달되는 세션 버퍼의 크기에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-576">The number of DTLS sessions is determined by the size of the session buffer passed into nx_secure_dtls_server_create.</span></span>
- <span data-ttu-id="0869c-577">certs_per_session은 클라이언트 인증서 체인에서 예상되는 최대 인증서 수로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-577">certs_per_session should be set to the maximum expected number of certificates in any client certificate chain.</span></span>
- <span data-ttu-id="0869c-578">예상되는 최대 인증서 크기는 애플리케이션, 키 크기 및 기타 요인에 따라 다르지만 일반적으로 2KB면 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-578">The maximum expected certificate size is dependent on the application, key sizes, and other factors but 2KB is generally sufficient.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-579">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-579">Parameters</span></span>

- <span data-ttu-id="0869c-580">**server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-580">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="0869c-581">**certs_per_session** 각 DTLS 서버 세션에 할당할 인증서 수</span><span class="sxs-lookup"><span data-stu-id="0869c-581">**certs_per_session** Number of certificates to allocate to each DTLS server session.</span></span>
- <span data-ttu-id="0869c-582">**certs_buffer** 들어오는 인증서 데이터의 버퍼 공간</span><span class="sxs-lookup"><span data-stu-id="0869c-582">**certs_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="0869c-583">**buffer_size** 인증서 버퍼의 크기</span><span class="sxs-lookup"><span data-stu-id="0869c-583">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-584">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-584">Return Values</span></span>

- <span data-ttu-id="0869c-585">**NX_SUCCESS** (0x00) X.509 클라이언트 확인을 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-585">**NX_SUCCESS** (0x00) Successful configuration of X.509 Client verification.</span></span>
- <span data-ttu-id="0869c-586">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-586">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-587">**NX_INVALID_PARAMETERS** (0x4D) 인증서 저장소가 올바르지 않습니다(DTLS 서버 인스턴스가 초기화되었나요?).</span><span class="sxs-lookup"><span data-stu-id="0869c-587">**NX_INVALID_PARAMETERS** (0x4D) Invalid certificate store (DTLSserver instance not initalized?).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-588">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-588">Allowed From</span></span>

<span data-ttu-id="0869c-589">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-590">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-590">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-591">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-591">See Also</span></span>

- <span data-ttu-id="0869c-592">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="0869c-592">nx_secure_dtls_server_x509_client_verify_disable,</span></span>
- <span data-ttu-id="0869c-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="0869c-594">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-594">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="0869c-595">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="0869c-595">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="0869c-596">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-596">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="0869c-597">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="0869c-597">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a><span data-ttu-id="0869c-598">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="0869c-598">nx_secure_dtls_server_x509_client_verify_disable</span></span>

<span data-ttu-id="0869c-599">NetX Secure DTLS 서버에 클라이언트 X.509 인증서 확인을 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="0869c-599">Disables client X.509 certificate verification for a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-600">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-600">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="0869c-601">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-601">Description</span></span>

<span data-ttu-id="0869c-602">이 서비스는 DTLS 서버에서 X.509 클라이언트 인증서 확인을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-602">This service disables X.509 Client certificate verification on a DTLS Server.</span></span> <span data-ttu-id="0869c-603">X.509 클라이언트 인증서 확인이 사용되지 않으면 이 서비스는 아무 영향도 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-603">The service has no effect if X.509 Client certificate verification is not enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="0869c-604">활성 DTLS 서버 인스턴스에서 클라이언트 인증을 사용하지 않도록 설정하면 예기치 않은 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-604">Disabling client authentication on an active DTLS Server instance may result in unpredictable behavior.</span></span> <span data-ttu-id="0869c-605">서버 상태를 변경하기 전에 nx_secure_dtls_server_stop 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-605">The nx_secure_dtls_server_stop service should be called before changing server state.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-606">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-606">Parameters</span></span>

- <span data-ttu-id="0869c-607">**server_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-607">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-608">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-608">Return Values</span></span>

- <span data-ttu-id="0869c-609">**NX_SUCCESS** (0x00) X.509 클라이언트 인증을 사용하지 않도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-609">**NX_SUCCESS** (0x00) Successful disabling of X.509 client authentication.</span></span>
- <span data-ttu-id="0869c-610">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-610">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-611">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-611">Allowed From</span></span>

<span data-ttu-id="0869c-612">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-613">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-613">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-614">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-614">See Also</span></span>

- <span data-ttu-id="0869c-615">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="0869c-615">nx_secure_dtls_server_x509_client_verify_configure,</span></span>
- <span data-ttu-id="0869c-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="0869c-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="0869c-617">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-617">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="0869c-618">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="0869c-618">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="0869c-619">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-619">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="0869c-620">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="0869c-620">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_client_info_get"></a><span data-ttu-id="0869c-621">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="0869c-621">nx_secure_dtls_session_client_info_get</span></span>

<span data-ttu-id="0869c-622">DTLS 서버 세션에서 원격 클라이언트 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="0869c-622">Get remote client information from a DTLS Server session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-623">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-623">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a><span data-ttu-id="0869c-624">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-624">Description</span></span>

<span data-ttu-id="0869c-625">이 서비스는 특정 DTLS 서버 세션에 연결된 DTLS 클라이언트에 대한 네트워크 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-625">This service returns the network information about a DTLS Client that is connected to a particular DTLS Server session.</span></span> <span data-ttu-id="0869c-626">반환된 정보는 원격 클라이언트의 IP 주소 및 UDP 포트와 클라이언트가 연결된 로컬 서버 포트로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-626">The information returned consists of the remote client’s IP address and UDP port, as well as the local server port to which the client is connected.</span></span>

<span data-ttu-id="0869c-627">일반적으로 DTLS 세션 인스턴스는 DTLS 알림 콜백 루틴(예: nx_secure_dtls_server_create에 전달된 connect_notify 또는 receive_notify 콜백) 중 하나를 호출할 때 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-627">In general, the DTLS session instance will be the one obtained in the invocation of one of the DTLS notification callback routines (e.g. the connect_notify or receive_notify callbacks passed into nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-628">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-628">Parameters</span></span>

- <span data-ttu-id="0869c-629">**session_ptr** 활성 DTLS 서버 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-629">**session_ptr** Pointer to an active DTLS server session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-630">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-630">Return Values</span></span>

- <span data-ttu-id="0869c-631">**NX_SUCCESS** (0x00) 서버를 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-631">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="0869c-632">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-632">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-633">**NX_INVALID_SOCKET** (0x13) 연결된 UDP 소켓이 올바르지 않습니다(세션이 초기화되었나요?).</span><span class="sxs-lookup"><span data-stu-id="0869c-633">**NX_INVALID_SOCKET** (0x13) The associated UDP socket is not valid (session not initialized?).</span></span>
- <span data-ttu-id="0869c-634">**NX_NOT_CONNECTED** (0x38) UDP 소켓이 연결되지 않았습니다. 클라이언트 연결이 끊어졌거나 아직 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-634">**NX_NOT_CONNECTED** (0x38) UDP socket is not connected – client connection dropped or not yet established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-635">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-635">Allowed From</span></span>

<span data-ttu-id="0869c-636">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-637">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-637">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-638">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-638">See Also</span></span>

- <span data-ttu-id="0869c-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="0869c-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop,</span></span>
- <span data-ttu-id="0869c-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="0869c-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="0869c-642">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-642">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_session_create"></a><span data-ttu-id="0869c-643">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="0869c-643">nx_secure_dtls_session_create</span></span>

<span data-ttu-id="0869c-644">NetX Secure DTLS 세션 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="0869c-644">Create and configure a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-645">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-645">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="0869c-646">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-646">Description</span></span>

<span data-ttu-id="0869c-647">이 서비스는 DTLS 세션을 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-647">This service creates and configures a DTLS session.</span></span> <span data-ttu-id="0869c-648">DTLS 서버 세션이 DTLS 서버 메커니즘을 통해 관리되므로 이 서비스는 일반적으로 DTLS 클라이언트 세션을 만드는 데 사용되지만(*nx_secure_dtls_server_create* 참조), 애플리케이션에서 단일 독립 실행형 DTLS 서버 세션 인스턴스를 만들어야 하는 경우가 있습니다. 이 경우 이 서비스를 사용할 수 있습니다<sup>7</sup>.</span><span class="sxs-lookup"><span data-stu-id="0869c-648">Generally, this will be used to create DTLS Client sessions as DTLS Server sessions are managed with the DTLS Server mechanism (see *nx_secure_dtls_server_create*), but there may be instances where an application needs to create a single stand-alone DTLS Server session instance in which case this service may be used<sup>7</sup>.</span></span>

<span data-ttu-id="0869c-649">매개 변수는 DTLS 세션을 인스턴스화하는 데 필요한 정보 및 메모리 할당을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-649">The parameters configure the information and memory allocation needed to instantiate a DTLS session.</span></span> <span data-ttu-id="0869c-650">crypto_table 매개 변수는 TLS/DTLS 암호화 및 인증에 필요한 모든 암호화 루틴을 포함하는 TLS 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-650">The crypto_table parameter is a TLS table containing all of the cryptographic routines needed for TLS/DTLS encryption and authentication.</span></span> <span data-ttu-id="0869c-651">metadata_buffer는 암호화 계산에 사용되고(NetX Secure TLS 사용자 가이드의 nx_secure_tls_metadata_size_calculate 참조), packet_reassembly_buffer는 암호를 해독하기 위해 UDP 데이터그램을 완전한 DTLS 레코드로 리어셈블하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-651">The metadata_buffer is used for encryption caclulations (see nx_secure_tls_metadata_size_calculate in the NetX Secure TLS User Guide), and the packet_reassembly_buffer is used to reassemble UDP datagrams into a complete DTLS record for decryption.</span></span>

<span data-ttu-id="0869c-652">certs_number 및 remote_certificate_buffer는 DTLS 클라이언트에 필요하며, 이 클라이언트는 들어오는 DTLS 서버 인증서 체인을 저장하고 처리하기 위한 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-652">The certs_number and remote_certificate_buffer are required for DTLS Clients which need space to store and process the incoming DTLS Server certificate chain.</span></span> <span data-ttu-id="0869c-653">버퍼는 연결할 서버에서 예상되는 최대 인증서 체인 크기를 수용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-653">The buffer must be able to accommodate the maximum expected size of the certificate chain for any server to which it will connect.</span></span> <span data-ttu-id="0869c-654">버퍼는 예상되는 인증서 수(certs_number 매개 변수)만큼 분할되며 인증서마다 하나의 NX_SECURE_X509_CERT 구조를 저장할 수 있을 만큼 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-654">The buffer is divided up by the number of expected certificates (certs_number parameter) and must also be large enough to hold one NX_SECURE_X509_CERT structure per certificate.</span></span> <span data-ttu-id="0869c-655">버퍼 크기는 다음 수식을 사용하여 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-655">The buffer size can be determined using the following formula:</span></span>

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- <span data-ttu-id="0869c-656">certs_number는 서버 인증서 체인에서 예상되는 최대 인증서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-656">certs_number is the expected maximum number of certificates in the server’s certificate chain</span></span>
- <span data-ttu-id="0869c-657">최대 인증서 크기는 사용되는 키의 크기와 인증서의 정보에 따라 다르지만 일반적으로 2KB면 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-657">Maximum certificate size is dependent on the size of keys being used and the information in the certificate, but 2KB is generally sufficient.</span></span>

<span data-ttu-id="0869c-658">**7** 이 루틴을 사용하여 DTLS 서버 세션을 만드는 방법은 권장하지 않으며 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-658">**7** Creating DTLS Server sessions with this routine is not recommended and comes with some limitations.</span></span> <span data-ttu-id="0869c-659">주된 문제는 세션이 추가 클라이언트 연결을 정상적으로 처리하지 않는다는 것입니다. UDP는 비연결형이므로 이전 DTLS 세션이 아직 활성 상태인 경우 두 번째 클라이언트가 서버의 UDP 포트에 데이터를 합법적으로 전송할 수 있으므로 서버 세션이 오류와 함께 종료될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-659">The primary issue is that the session will not handle additional client connections gracefully – since UDP is connectionless a second client can legally send data to the server’s UDP port when a previous DTLS session is still active which would cause the server session to end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-660">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-660">Parameters</span></span>

- <span data-ttu-id="0869c-661">**dtls_session** 초기화되지 않은 DTLS 세션 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-661">**dtls_session** Pointer to an uninitialized DTLS Session structure.</span></span>
- <span data-ttu-id="0869c-662">**crypto_table** 모든 암호화 작업에 사용되는 TLS/DTLS 암호화 테이블 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-662">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="0869c-663">**crypto_metadata_buffer** 암호화 작업 계산 및 상태 정보에 사용되는 버퍼 공간</span><span class="sxs-lookup"><span data-stu-id="0869c-663">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="0869c-664">**crypto_metadata_size** 메타데이터 버퍼의 크기</span><span class="sxs-lookup"><span data-stu-id="0869c-664">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="0869c-665">**packet_reassembly_buffer** 암호 해독을 위해 DTLS에서 UDP 데이터를 DTLS 레코드로 다시 어셈블할 때 사용하는 버퍼</span><span class="sxs-lookup"><span data-stu-id="0869c-665">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="0869c-666">**packet_reassembly_buffer_size** 리어셈블리 버퍼의 크기.</span><span class="sxs-lookup"><span data-stu-id="0869c-666">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="0869c-667">일반적으로 16KB보다 커야 하지만 애플리케이션에 따라 더 작을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-667">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="0869c-668">**certs_number** 원격 서버의 인증서 체인에서 예상되는 최대 인증서 수</span><span class="sxs-lookup"><span data-stu-id="0869c-668">**certs_number** Maximum expected number of certificates in the remote server’s certificate chain.</span></span>
- <span data-ttu-id="0869c-669">**remote_certificate_buffer** 들어오는 인증서 데이터의 버퍼 공간</span><span class="sxs-lookup"><span data-stu-id="0869c-669">**remote_certificate_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="0869c-670">**remote_certificate_buffer_size** 인증서 버퍼의 크기</span><span class="sxs-lookup"><span data-stu-id="0869c-670">**remote_certificate_buffer_size** Size of the certificate buffer.</span></span>


### <a name="return-values"></a><span data-ttu-id="0869c-671">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-671">Return Values</span></span>

- <span data-ttu-id="0869c-672">**NX_SUCCESS** (0x00) 세션을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-672">**NX_SUCCESS** (0x00) Successful creation of session.</span></span>
- <span data-ttu-id="0869c-673">**NX_PTR_ERROR** (0x07) 세션 또는 버퍼 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-673">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="0869c-674">**NX_INVALID_PARAMETERS** (0x4D) 패킷 리어셈블리, 인증서 또는 암호화를 위한 버퍼 공간이 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-674">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for packet reassembly, certificates, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-675">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-675">Allowed From</span></span>

<span data-ttu-id="0869c-676">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-677">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-677">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-678">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-678">See Also</span></span>

- <span data-ttu-id="0869c-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-680">nx_secure_dtls_session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-680">nx_secure_dtls_session_send</span></span>

## <a name="nx_secure_dtls_session_delete"></a><span data-ttu-id="0869c-681">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-681">nx_secure_dtls_session_delete</span></span>

<span data-ttu-id="0869c-682">NetX Secure DTLS 세션에서 사용하는 리소스 해제</span><span class="sxs-lookup"><span data-stu-id="0869c-682">Free up resources used by a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-683">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-683">Prototype</span></span>

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a><span data-ttu-id="0869c-684">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-684">Description</span></span>

<span data-ttu-id="0869c-685">이 서비스는 DTLS 세션을 삭제하고, 생성 시 할당된 모든 리소스를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-685">This service deletes a DTLS session, freeing up any resources that were allocated when it was created.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-686">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-686">Parameters</span></span>

- <span data-ttu-id="0869c-687">**dtls_session** 이전에 초기화된 DTLS 세션 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-687">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-688">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-688">Return Values</span></span>

- <span data-ttu-id="0869c-689">**NX_SUCCESS** (0x00) 세션을 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-689">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="0869c-690">**NX_PTR_ERROR** (0x07) 세션 또는 버퍼 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-690">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-691">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-691">Allowed From</span></span>

<span data-ttu-id="0869c-692">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-693">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-693">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-694">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-694">See Also</span></span>

- <span data-ttu-id="0869c-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_end"></a><span data-ttu-id="0869c-697">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="0869c-697">nx_secure_dtls_session_end</span></span>

<span data-ttu-id="0869c-698">활성 NetX Secure DTLS 세션 종료</span><span class="sxs-lookup"><span data-stu-id="0869c-698">Shut down an active NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-699">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-699">Prototype</span></span>

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="0869c-700">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-700">Description</span></span>

<span data-ttu-id="0869c-701">이 서비스는 원격 호스트에 TLS/DTLS CloseNotify 경고를 보내서 활성 DTLS 세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-701">This service ends an active DTLS session by sending a TLS/DTLS CloseNotify alert to the remote host.</span></span> <span data-ttu-id="0869c-702">이전에 nx_secure_dtls_session_send를 호출할 때 사용한 IP 주소 및 포트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-702">The IP address and port used are those used in the previous call to nx_secure_dtls_session_send.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-703">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-703">Parameters</span></span>

- <span data-ttu-id="0869c-704">**dtls_session** 이전에 초기화된 DTLS 세션 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-704">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="0869c-705">**wait_option** 네트워크 작업에 사용할 ThreadX 대기 값</span><span class="sxs-lookup"><span data-stu-id="0869c-705">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-706">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-706">Return Values</span></span>

- <span data-ttu-id="0869c-707">**NX_SUCCESS** (0x00) 세션을 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-707">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="0869c-708">**NX_PTR_ERROR** (0x07) 세션 또는 버퍼 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-708">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="0869c-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) CloseNotify 경고에 대한 패킷을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate packet(s) for CloseNotify alert.</span></span>
- <span data-ttu-id="0869c-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) 내부 오류일 가능성이 높습니다. 암호화 루틴이 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Likely internal error – cryptographic routine not recognized.</span></span>
- <span data-ttu-id="0869c-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 기본 UDP 전송이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Underlying UDP send failed.</span></span>
- <span data-ttu-id="0869c-712">**NX_IP_ADDRESS_ERROR** (0x21) 원격 호스트 IP 주소에 오류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-712">**NX_IP_ADDRESS_ERROR** (0x21) Error with remote host IP address.</span></span>
- <span data-ttu-id="0869c-713">**NX_NOT_BOUND** (0x24) 기본 UDP 소켓이 포트에 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-713">**NX_NOT_BOUND** (0x24) Underlying UDP socket not bound to port.</span></span>
- <span data-ttu-id="0869c-714">**NX_INVALID_PORT** (0x46) UDP 포트가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-714">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="0869c-715">**NX_PORT_UNAVAILABLE** (0x23) UDP 포트를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-715">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-716">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-716">Allowed From</span></span>

<span data-ttu-id="0869c-717">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-717">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-718">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-718">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-719">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-719">See Also</span></span>

- <span data-ttu-id="0869c-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_local_certificate_add"></a><span data-ttu-id="0869c-722">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-722">nx_secure_dtls_session_local_certificate_add</span></span>

<span data-ttu-id="0869c-723">NetX Secure DTLS 세션에 로컬 ID 인증서 추가</span><span class="sxs-lookup"><span data-stu-id="0869c-723">Add a local identity certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-724">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-724">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="0869c-725">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-725">Description</span></span>

<span data-ttu-id="0869c-726">이 서비스는 DTLS 세션 인스턴스에 로컬 ID 인증서를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-726">This service adds a local identity certificate to a DTLS Session instance.</span></span> <span data-ttu-id="0869c-727">일반적으로 DTLS 클라이언트 세션이 원격 서버 호스트에 ID 인증서를 제공해야 하는 경우에 이 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-727">In general, this service will be used when a DTLS Client session needs to provide an identity certificate to a remote server host.</span></span> <span data-ttu-id="0869c-728">DTLS에 대한 선택적 구성이므로 일반적으로 DTLS 클라이언트에 인증서가 꼭 필요하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-728">This is an optional configuration for DTLS so a certificate is not generally required for DTLS Clients.</span></span> <span data-ttu-id="0869c-729">ID 인증서는 연결된 프라이빗 키가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-729">An identity certificate requires an associated private key.</span></span>

<span data-ttu-id="0869c-730">cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-730">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="0869c-731">이렇게 하면 DTLS 인증서 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-731">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="0869c-732">X.509 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-732">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-733">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-733">Parameters</span></span>

- <span data-ttu-id="0869c-734">**session_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-734">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="0869c-735">**certificate** 이전에 초기화된 X.509 인증서 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-735">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="0869c-736">**cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자</span><span class="sxs-lookup"><span data-stu-id="0869c-736">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-737">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-737">Return Values</span></span>

- <span data-ttu-id="0869c-738">**NX_SUCCESS** (0x00) DTLS 세션에 인증서를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-738">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="0869c-739">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-739">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-740">**NX_INVALID_PARAMETERS** (0x4D) 인증서 ID 0이 전달되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-740">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-741">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-741">Allowed From</span></span>

<span data-ttu-id="0869c-742">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-742">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-743">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-743">Example</span></span>

<span data-ttu-id="0869c-744">\*보다 완전한 예제는 *nx_secure_dtls_session_create* 에 대한 참조를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-744">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-745">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-745">See Also</span></span>

- <span data-ttu-id="0869c-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="0869c-748">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-748">nx_secure_dtls_session_local_certificate_remove,</span></span>
- <span data-ttu-id="0869c-749">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="0869c-749">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_local_certificate_remove"></a><span data-ttu-id="0869c-750">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-750">nx_secure_dtls_session_local_certificate_remove</span></span>

<span data-ttu-id="0869c-751">NetX Secure DTLS 세션에서 로컬 ID 인증서 제거</span><span class="sxs-lookup"><span data-stu-id="0869c-751">Remove a local identity certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-752">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-752">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="0869c-753">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-753">Description</span></span>

<span data-ttu-id="0869c-754">이 서비스는 nx_secure_dtls_session_local_certificate_add를 사용하여 인증서를 추가할 때 할당된 인증서 ID 번호 또는 X.509 CommonName 필드를 사용하여 DTLS 세션 인스턴스에서 로컬 ID 인증서를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-754">This service removes a local identity certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_local_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="0869c-755">인증서를 매칭하기 위해 common_name을 사용하는 경우 cert_id 매개 변수를 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-755">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="0869c-756">cert_id를 사용하는 경우에는 common_name에 NX_NULL 값을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-756">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="0869c-757">cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-757">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="0869c-758">이렇게 하면 DTLS 인증서 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-758">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="0869c-759">X.509 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-759">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-760">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-760">Parameters</span></span>

- <span data-ttu-id="0869c-761">**session_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-761">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="0869c-762">**common_name** 매칭할 CommonName 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-762">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="0869c-763">**common_name_length** common_name 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="0869c-763">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="0869c-764">**cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자</span><span class="sxs-lookup"><span data-stu-id="0869c-764">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-765">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-765">Return Values</span></span>

- <span data-ttu-id="0869c-766">**NX_SUCCESS** (0x00) DTLS 세션에서 인증서를 제거했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-766">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="0869c-767">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-767">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 지정된 DTLS 세션에서 cert_id 또는 common_name과 일치하는 인증서를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-769">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-769">Allowed From</span></span>

<span data-ttu-id="0869c-770">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-770">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-771">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-771">Example</span></span>

<span data-ttu-id="0869c-772">\*보다 완전한 예제는 *nx_secure_dtls_session_create* 에 대한 참조를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-772">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-773">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-773">See Also</span></span>

- <span data-ttu-id="0869c-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="0869c-776">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-776">nx_secure_dtls_session_local_certificate_add,</span></span>
- <span data-ttu-id="0869c-777">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="0869c-777">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_receive"></a><span data-ttu-id="0869c-778">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-778">nx_secure_dtls_session_receive</span></span>

<span data-ttu-id="0869c-779">설정된 NetX Secure DTLS 세션을 통해 애플리케이션 데이터 받기</span><span class="sxs-lookup"><span data-stu-id="0869c-779">Receive application data over an established NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-780">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-780">Prototype</span></span>

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="0869c-781">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-781">Description</span></span>

<span data-ttu-id="0869c-782">이 서비스는 활성 DTLS 세션에서 받은 애플리케이션 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-782">This service returns application data received by an active DTLS Session.</span></span> <span data-ttu-id="0869c-783">DTLS 세션은 DTLS 서버 세션(DTLS 서버 인스턴스에서 관리) 또는 DTLS 클라이언트 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-783">The DTLS Session may be either a DTLS Server session (managed by a DTLS Server instance) or a DTLS Client session.</span></span> <span data-ttu-id="0869c-784">반환된 패킷은 아무 NX_PACKET API 서비스를 사용하여 처리할 수 있습니다(자세한 내용은 NetX 설명서 참조).</span><span class="sxs-lookup"><span data-stu-id="0869c-784">The returned packet may be processed using any of the NX_PACKET API services (see the NetX documentation for more information).</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-785">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-785">Parameters</span></span>

- <span data-ttu-id="0869c-786">**dtls_session** 이전에 초기화된 DTLS 세션 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-786">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="0869c-787">**packet_ptr_ptr** 반환 패킷의 NX_PACKET 포인터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-787">**packet_ptr_ptr** Pointer to an NX_PACKET pointer for the return packet.</span></span>
- <span data-ttu-id="0869c-788">**wait_option** 네트워크 작업에 사용할 ThreadX 대기 값</span><span class="sxs-lookup"><span data-stu-id="0869c-788">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-789">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-789">Return Values</span></span>

- <span data-ttu-id="0869c-790">**NX_SUCCESS** (0x00) 애플리케이션에서 데이터 패킷을 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-790">**NX_SUCCESS** (0x00) Successful receipt of application data packet.</span></span>
- <span data-ttu-id="0869c-791">**NX_PTR_ERROR** (0x07) 세션 또는 패킷 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-791">**NX_PTR_ERROR** (0x07) Invalid session or packet pointer.</span></span>
- <span data-ttu-id="0869c-792">**NX_NOT_ENABLED** (0x14) UDP가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-792">**NX_NOT_ENABLED** (0x14) UDP is not enabled.</span></span>
- <span data-ttu-id="0869c-793">**NX_NOT_BOUND** (0x24) UDP 소켓이 포트에 바인딩되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-793">**NX_NOT_BOUND** (0x24) UDP socket not bound to port.</span></span>
- <span data-ttu-id="0869c-794">**NX_SECURE_TLS_INVALID_PACKET** (0x104) 수신한 데이터가 유효한 DTLS 레코드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-794">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="0869c-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) DTLS 레코드를 올바르게 해시하지 못했습니다(암호화 오류).</span><span class="sxs-lookup"><span data-stu-id="0869c-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="0869c-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) 암호화 패딩 검사가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="0869c-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) 원격 호스트에서 경고를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host.</span></span>
- <span data-ttu-id="0869c-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) 인식할 수 없는 메시지를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0x102) Received an unrecognized message.</span></span>
- <span data-ttu-id="0869c-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 받은 DTLS 레코드의 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="0869c-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) 알 수 없는 ciphersuite가 발생했습니다(내부 암호화 오류가 표시됨).</span><span class="sxs-lookup"><span data-stu-id="0869c-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicates internal cryptography error).</span></span>
- <span data-ttu-id="0869c-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) 받은 DTLS 레코드의 DTLS 버전이 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-802">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-802">Allowed From</span></span>

<span data-ttu-id="0869c-803">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-804">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-804">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-805">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-805">See Also</span></span>

- <span data-ttu-id="0869c-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="0869c-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,</span></span>
- <span data-ttu-id="0869c-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_reset"></a><span data-ttu-id="0869c-808">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="0869c-808">nx_secure_dtls_session_reset</span></span>

<span data-ttu-id="0869c-809">NetX Secure DTLS 세션 인스턴스의 데이터 지우기</span><span class="sxs-lookup"><span data-stu-id="0869c-809">Clear data in an NetX Secure DTLS Session instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-810">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-810">Prototype</span></span>

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a><span data-ttu-id="0869c-811">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-811">Description</span></span>

<span data-ttu-id="0869c-812">이 서비스는 DTLS 세션을 초기화하고, 모든 임시 암호화 데이터를 지우고, 구조를 새 세션에 다시 사용할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-812">This service resets a DTLS session, clearing all ephemeral cryptographic data and allowing the structure to be re-used for a new session.</span></span> <span data-ttu-id="0869c-813">nx_secure_dtls_session_create를 반복적으로 호출할 필요가 없도록 영구 데이터(예: 인증서 저장소)는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-813">Persistent data (e.g. certificate stores) are maintained so that nx_secure_dtls_session_create need not be called repeatedly.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-814">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-814">Parameters</span></span>

- <span data-ttu-id="0869c-815">**dtls_session** 이전에 초기화된 DTLS 세션 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-815">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-816">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-816">Return Values</span></span>

- <span data-ttu-id="0869c-817">**NX_SUCCESS** (0x00) 세션을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-817">**NX_SUCCESS** (0x00) Successful reset of session.</span></span>
- <span data-ttu-id="0869c-818">**NX_PTR_ERROR** (0x07) 세션 또는 버퍼 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-818">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-819">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-819">Allowed From</span></span>

<span data-ttu-id="0869c-820">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-820">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-821">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-821">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-822">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-822">See Also</span></span>

- <span data-ttu-id="0869c-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="0869c-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_-session_send"></a><span data-ttu-id="0869c-825">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="0869c-825">nx_secure_dtls_ session_send</span></span>

<span data-ttu-id="0869c-826">DTLS 세션을 통해 데이터 보내기</span><span class="sxs-lookup"><span data-stu-id="0869c-826">Send data over a DTLS session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-827">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-827">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a><span data-ttu-id="0869c-828">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-828">Description</span></span>

<span data-ttu-id="0869c-829">이 서비스는 설정된 DTLS 세션을 통해 데이터 패킷을 지정된 IP 주소 및 포트의 원격 DTLS 호스트에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-829">This service sends a packet of data over an established DTLS Session to a remote DTLS host at the given IP address and port.</span></span> <span data-ttu-id="0869c-830">활성 DTLS 클라이언트 세션이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-830">The session used is an active DTLS Client session.</span></span> <span data-ttu-id="0869c-831">IP 주소와 포트는 UDP의 상태 비저장 특성 때문에 제공되지만 일반적으로 nx_secure_dtls_session_start에서 세션을 시작하는 데 사용되는 주소 및 포트와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-831">Note that the IP address and port are provided due to the stateless nature of UDP but should generally match the address and port used to start the session in nx_secure_dtls_session_start.</span></span>

<span data-ttu-id="0869c-832">패킷에 제공된 데이터(*nx_secure_dtls_packet_allocate* 를 사용하여 할당해야 함)는 DTLS 세션 암호화 매개 변수 및 루틴을 사용하여 암호화된 후 다음 DTLS 세션의 UDP 소켓을 통해 원격 호스트로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-832">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Session’s UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-833">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-833">Parameters</span></span>

- <span data-ttu-id="0869c-834">**session_ptr** 활성 DTLS 클라이언트 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-834">**session_ptr** Pointer to an active DTLS client session instance.</span></span>
- <span data-ttu-id="0869c-835">**packet_ptr** 이전에 할당되어 애플리케이션 데이터로 채워진 NX_PACKET 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-835">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>
- <span data-ttu-id="0869c-836">**ip_address** 원격 호스트의 IP 주소를 포함하는 NXD_ADDRESS 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-836">**ip_address** Pointer to an NXD_ADDRESS structure containing the IP address of the remote host.</span></span>
- <span data-ttu-id="0869c-837">**port** 원격 호스트의 UDP 포트</span><span class="sxs-lookup"><span data-stu-id="0869c-837">**port** UDP port on the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-838">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-838">Return Values</span></span>

- <span data-ttu-id="0869c-839">**NX_SUCCESS** (0x00) 패킷을 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-839">**NX_SUCCESS** (0x00) Successful send of packet.</span></span>
- <span data-ttu-id="0869c-840">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-840">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 기본 UDP 전송 작업에서 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-842">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-842">Allowed From</span></span>

<span data-ttu-id="0869c-843">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-843">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-844">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-844">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-845">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-845">See Also</span></span>

- <span data-ttu-id="0869c-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-847">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="0869c-847">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a><span data-ttu-id="0869c-848">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-848">nx_secure_dtls_session_trusted_certificate_add</span></span>

<span data-ttu-id="0869c-849">NetX Secure DTLS 세션에 신뢰할 수 있는 CA 인증서 추가</span><span class="sxs-lookup"><span data-stu-id="0869c-849">Add a trusted CA certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-850">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-850">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="0869c-851">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-851">Description</span></span>

<span data-ttu-id="0869c-852">이 서비스는 DTLS 세션 인스턴스에 신뢰할 수 있는 CA 또는 중간 CA X.509 인증서를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-852">This service adds a trusted CA or intermediate CA X.509 certificate to a DTLS Session instance.</span></span> <span data-ttu-id="0869c-853">대체 인증 메커니즘(예: 미리 공유한 키)을 사용하지 않는 한, DTLS 클라이언트에서 원격 서버 인증서의 유효성을 검사하려면 신뢰할 수 있는 인증서가 하나 이상 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-853">A DTLS Client requires at least one trusted certificate in order to validate remote server certificates unless an alternative authentication mechanism is used (e.g. Pre-Shared Keys).</span></span> <span data-ttu-id="0869c-854">신뢰할 수 있는 인증서에는 일반적으로 프라이빗 키가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-854">A trusted certificate does not usually have a private key.</span></span>

<span data-ttu-id="0869c-855">cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-855">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="0869c-856">이렇게 하면 DTLS 인증서 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-856">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="0869c-857">X.509 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-857">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-858">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-858">Parameters</span></span>

- <span data-ttu-id="0869c-859">**session_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-859">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="0869c-860">**certificate** 이전에 초기화된 X.509 인증서 구조에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-860">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="0869c-861">**cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자</span><span class="sxs-lookup"><span data-stu-id="0869c-861">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="0869c-862">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-862">Return Values</span></span>

- <span data-ttu-id="0869c-863">**NX_SUCCESS** (0x00) DTLS 세션에 인증서를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-863">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="0869c-864">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-864">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-865">**NX_INVALID_PARAMETERS** (0x4D) 인증서 ID 0이 전달되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-865">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-866">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-866">Allowed From</span></span>

<span data-ttu-id="0869c-867">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-868">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-868">Example</span></span>

<span data-ttu-id="0869c-869">\*보다 완전한 예제는 *nx_secure_dtls_session_create* 에 대한 참조를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-869">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-870">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-870">See Also</span></span>

- <span data-ttu-id="0869c-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="0869c-873">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-873">nx_secure_dtls_session_trusted_certificate_remove,</span></span>
- <span data-ttu-id="0869c-874">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="0869c-874">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a><span data-ttu-id="0869c-875">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="0869c-875">nx_secure_dtls_session_trusted_certificate_remove</span></span>

<span data-ttu-id="0869c-876">NetX Secure DTLS 세션에서 신뢰할 수 있는 CA 인증서 제거</span><span class="sxs-lookup"><span data-stu-id="0869c-876">Remove a trusted CA certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="0869c-877">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0869c-877">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="0869c-878">Description</span><span class="sxs-lookup"><span data-stu-id="0869c-878">Description</span></span>

<span data-ttu-id="0869c-879">이 서비스는 nx_secure_dtls_session_local_certificate_add를 사용하여 인증서를 추가할 때 할당된 인증서 ID 번호 또는 X.509 CommonName 필드를 사용하여 DTLS 세션 인스턴스에서 신뢰할 수 있는 CA 인증서를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-879">This service removes a trusted CA certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_trusted_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="0869c-880">인증서를 매칭하기 위해 common_name을 사용하는 경우 cert_id 매개 변수를 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-880">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="0869c-881">cert_id를 사용하는 경우에는 common_name에 NX_NULL 값을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-881">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="0869c-882">cert_id 매개 변수는 인증서에 대한 0이 아닌 숫자 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-882">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="0869c-883">이렇게 하면 DTLS 인증서 저장소에 X.509 일반 이름이 동일한 ID 인증서가 여러 개 있을 때 인증서를 쉽게 제거하거나 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-883">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="0869c-884">X.509 인증서에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-884">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="0869c-885">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0869c-885">Parameters</span></span>

- <span data-ttu-id="0869c-886">**session_ptr** 이전에 만든 DTLS 세션 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-886">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="0869c-887">**common_name** 매칭할 CommonName 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="0869c-887">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="0869c-888">**common_name_length** common_name 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="0869c-888">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="0869c-889">**cert_id** 이 DTLS 서버의 이 인증서에 대한 0이 아닌 고유한 숫자 식별자</span><span class="sxs-lookup"><span data-stu-id="0869c-889">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>


### <a name="return-values"></a><span data-ttu-id="0869c-890">반환 값</span><span class="sxs-lookup"><span data-stu-id="0869c-890">Return Values</span></span>

- <span data-ttu-id="0869c-891">**NX_SUCCESS** (0x00) DTLS 세션에서 인증서를 제거했습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-891">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="0869c-892">**NX_PTR_ERROR (0x07)** 전달된 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-892">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="0869c-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 지정된 DTLS 세션에서 cert_id 또는 common_name과 일치하는 인증서를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0869c-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0869c-894">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0869c-894">Allowed From</span></span>

<span data-ttu-id="0869c-895">스레드</span><span class="sxs-lookup"><span data-stu-id="0869c-895">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0869c-896">예제</span><span class="sxs-lookup"><span data-stu-id="0869c-896">Example</span></span>

<span data-ttu-id="0869c-897">\*보다 완전한 예제는 *nx_secure_dtls_session_create* 에 대한 참조를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0869c-897">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="0869c-898">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0869c-898">See Also</span></span>

- <span data-ttu-id="0869c-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="0869c-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="0869c-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="0869c-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="0869c-901">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="0869c-901">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="0869c-902">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="0869c-902">nx_secure_x509_certificate_initialize</span></span>
