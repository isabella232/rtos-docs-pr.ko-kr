---
title: 4장 - Azure RTOS NetX Secure 서비스 설명
description: 이 장에서는 알파벳 순서로 아래 나열된 모든 NetX Secure 서비스에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80ec22058ab64ed0c6258bb3d9364ec44f9a741b
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223395"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a><span data-ttu-id="7ddf6-103">4장 - Azure RTOS NetX Secure 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="7ddf6-103">Chapter 4 - Description of Azure RTOS NetX Secure services</span></span>

<span data-ttu-id="7ddf6-104">이 장에서는 알파벳 순서로 아래 나열된 모든 Azure RTOS NetX Secure 서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-104">This chapter contains a description of all Azure RTOS NetX Secure services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="7ddf6-105">다음 API 설명의 "반환 값" 섹션에서, **BOLD** 의 값은 API 오류 검사를 해제하는 데 사용되는 **NX_SECURE_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="7ddf6-106">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="7ddf6-106">nx_secure_crypto_table_self_test</span></span>](#nx_secure_crypto_table_self_test)
  - <span data-ttu-id="7ddf6-107">암호화 방법에 대해 self_test 수행</span><span class="sxs-lookup"><span data-stu-id="7ddf6-107">Perform self_test on the crypto methods</span></span>
- [<span data-ttu-id="7ddf6-108">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="7ddf6-108">nx_secure_module_hash_compute</span></span>](#nx_secure_module_hash_compute)
  - <span data-ttu-id="7ddf6-109">user_supplied hash 함수를 사용하여 해시 값 계산</span><span class="sxs-lookup"><span data-stu-id="7ddf6-109">Computes hash value using user_supplied hash function</span></span>
- [<span data-ttu-id="7ddf6-110">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-110">nx_secure_tls_active_certificate_set</span></span>](#nx_secure_tls_active_certificate_set)
  - <span data-ttu-id="7ddf6-111">NetX Secure TLS 세션에 대해 활성 ID 인증서 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-111">Set the active identity certificate for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-112">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-112">nx_secure_tls_client_psk_set</span></span>](#nx_secure_tls_client_psk_set)
  - <span data-ttu-id="7ddf6-113">NetX Secure TLS 클라이언트 세션에 대해 Pre_Shared 키 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-113">Set a Pre_Shared Key for a NetX Secure TLS Client Session</span></span>
- [<span data-ttu-id="7ddf6-114">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-114">nx_secure_tls_initialize</span></span>](#nx_secure_tls_initialize)
  - <span data-ttu-id="7ddf6-115">NetX Secure TLS 모듈 초기화</span><span class="sxs-lookup"><span data-stu-id="7ddf6-115">Initializes the NetX Secure TLS module]</span></span>
- [<span data-ttu-id="7ddf6-116">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-116">nx_secure_tls_local_certificate_add</span></span>](#nx_secure_tls_local_certificate_add)
  - <span data-ttu-id="7ddf6-117">NetX Secure TLS 세션에 로컬 인증서 추가</span><span class="sxs-lookup"><span data-stu-id="7ddf6-117">Add a local certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-118">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-118">nx_secure_tls_local_certificate_find</span></span>](#nx_secure_tls_local_certificate_find)
  - <span data-ttu-id="7ddf6-119">일반 이름으로 NetX Secure TLS 세션에서 로컬 인증서 찾기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-119">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>
- [<span data-ttu-id="7ddf6-120">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-120">nx_secure_tls_local_certificate_remove</span></span>](#nx_secure_tls_local_certificate_remove)
  - <span data-ttu-id="7ddf6-121">NetX Secure TLS 세션에서 로컬 인증서 제거</span><span class="sxs-lookup"><span data-stu-id="7ddf6-121">Remove local certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-122">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-122">nx_secure_tls_metadata_size_calculate</span></span>](#nx_secure_tls_metadata_size_calculate)
  - <span data-ttu-id="7ddf6-123">NetX Secure TLS 세션의 암호화 메타데이터 크기 계산</span><span class="sxs-lookup"><span data-stu-id="7ddf6-123">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-124">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-124">nx_secure_tls_packet_allocate</span></span>](#nx_secure_tls_packet_allocate)
  - <span data-ttu-id="7ddf6-125">NetX Secure TLS 세션에 대한 패킷 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-125">Allocate a packet for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-126">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-126">nx_secure_tls_psk_add</span></span>](#nx_secure_tls_psk_add)
  - <span data-ttu-id="7ddf6-127">NetX Secure TLS 세션에 Pre_Shared 키 추가</span><span class="sxs-lookup"><span data-stu-id="7ddf6-127">Add a Pre_Shared Key to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-128">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-128">nx_secure_tls_remote_certificate_allocate</span></span>](#nx_secure_tls_remote_certificate_allocate)
  - <span data-ttu-id="7ddf6-129">원격 TLS 호스트에서 제공하는 인증서를 위한 공간 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-129">Allocate space for the certificate provided by a remote TLS host</span></span>
- [<span data-ttu-id="7ddf6-130">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-130">nx_secure_tls_remote_certificate_buffer_allocate</span></span>](#nx_secure_tls_remote_certificate_buffer_allocate)
  - <span data-ttu-id="7ddf6-131">원격 TLS 호스트에서 제공하는 모든 인증서를 위한 공간 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-131">Allocate space for all certificates provided by a remote TLS host</span></span>
- [<span data-ttu-id="7ddf6-132">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="7ddf6-132">nx_secure_tls_remote_certificate_free_all</span></span>](#nx_secure_tls_remote_certificate_free_all)
  - <span data-ttu-id="7ddf6-133">수신 인증서에 대해 할당된 사용 가능한 공간</span><span class="sxs-lookup"><span data-stu-id="7ddf6-133">Free space allocated for incoming certificates</span></span>
- [<span data-ttu-id="7ddf6-134">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-134">nx_secure_tls_server_certificate_add</span></span>](#nx_secure_tls_server_certificate_add)
  - <span data-ttu-id="7ddf6-135">숫자 식별자를 사용하여 TLS 서버 전용 인증서 추가</span><span class="sxs-lookup"><span data-stu-id="7ddf6-135">Add a certificate specifically for TLS servers using a numeric identifier</span></span>
- [<span data-ttu-id="7ddf6-136">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-136">nx_secure_tls_server_certificate_find</span></span>](#nx_secure_tls_server_certificate_find)
  - <span data-ttu-id="7ddf6-137">숫자 식별자를 사용하여 인증서 찾기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-137">Find a certificate using a numeric identifier</span></span>
- [<span data-ttu-id="7ddf6-138">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-138">nx_secure_tls_server_certificate_remove</span></span>](#nx_secure_tls_server_certificate_remove)
  - <span data-ttu-id="7ddf6-139">숫자 식별자를 사용하여 로컬 서버 인증서 제거</span><span class="sxs-lookup"><span data-stu-id="7ddf6-139">Remove a local server certificate using a numeric identifier</span></span>
- [<span data-ttu-id="7ddf6-140">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-140">nx_secure_tls_session_certificate_callback_set</span></span>](#nx_secure_tls_session_certificate_callback_set)
  - <span data-ttu-id="7ddf6-141">추가 인증서 유효성 검사에 사용할 TLS에 대한 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-141">Set up a callback for TLS to use for additional certificate validation</span></span>
- [<span data-ttu-id="7ddf6-142">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-142">nx_secure_tls_session_client_callback_set</span></span>](#nx_secure_tls_session_client_callback_set)
  - <span data-ttu-id="7ddf6-143">TlS가 TLS 클라이언트 핸드셰이크 시작 시 호출할 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-143">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>
- [<span data-ttu-id="7ddf6-144">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="7ddf6-144">nx_secure_tls_session_x509_client_verify_configure</span></span>](#nx_secure_tls_session_x509_client_verify_configure)
  - <span data-ttu-id="7ddf6-145">클라이언트 X.509 확인을 사용하도록 설정하고 클라이언트 인증서에 대해 공간 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-145">Enable client X.509 verification and allocate space for client certificates</span></span>
- [<span data-ttu-id="7ddf6-146">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="7ddf6-146">nx_secure_tls_session_client_verify_disable</span></span>](#nx_secure_tls_session_client_verify_disable)
  - <span data-ttu-id="7ddf6-147">NetX Secure TLS 세션에 대해 클라이언트 인증서 인증를 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-147">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-148">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="7ddf6-148">nx_secure_tls_session_client_verify_enable</span></span>](#nx_secure_tls_session_client_verify_enable)
  - <span data-ttu-id="7ddf6-149">NetX Secure TLS 세션에 대해 클라이언트 인증서 인증를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-149">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-150">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-150">nx_secure_tls_session_create</span></span>](#nx_secure_tls_session_create)
  - <span data-ttu-id="7ddf6-151">보안 통신용 NetX Secure TLS 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-151">Create a NetX Secure TLS Session for secure communications</span></span>
- [<span data-ttu-id="7ddf6-152">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-152">nx_secure_tls_session_delete</span></span>](#nx_secure_tls_session_delete)
  - <span data-ttu-id="7ddf6-153">NetX Secure TLS 세션 삭제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-153">Delete a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-154">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7ddf6-154">nx_secure_tls_session_end</span></span>](#nx_secure_tls_session_end)
  - <span data-ttu-id="7ddf6-155">활성 NetX Secure TLS 세션 종료</span><span class="sxs-lookup"><span data-stu-id="7ddf6-155">End an active NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-156">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-156">nx_secure_tls_session_packet_buffer_set</span></span>](#nx_secure_tls_session_packet_buffer_set)
  - <span data-ttu-id="7ddf6-157">NetX Secure TLS 세션에 대한 패킷 리어셈블리 버퍼 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-157">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-158">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="7ddf6-158">nx_secure_tls_session_protocol_version_override</span></span>](#nx_secure_tls_session_protocol_version_override)
  - <span data-ttu-id="7ddf6-159">NetX Seure TLS 세션의 기본 TLS 프로토콜 버전 재정의</span><span class="sxs-lookup"><span data-stu-id="7ddf6-159">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-160">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-160">nx_secure_tls_session_receive</span></span>](#nx_secure_tls_session_receive)
  - <span data-ttu-id="7ddf6-161">NetX Secure TLS 세션에서 데이터 받기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-161">Receive data from a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-162">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-162">nx_secure_tls_session_renegotiate_callback_set</span></span>](#nx_secure_tls_session_renegotiate_callback_set)
  - <span data-ttu-id="7ddf6-163">세션 다시 협상을 시작할 때 호출될 콜백 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-163">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>
- [<span data-ttu-id="7ddf6-164">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-164">nx_secure_tls_session_renegotiate</span></span>](#nx_secure_tls_session_renegotiate)
  - <span data-ttu-id="7ddf6-165">원격 호스트와의 세션 재협상 핸드셰이크 시작</span><span class="sxs-lookup"><span data-stu-id="7ddf6-165">Initiate a session renegotiation handshake with the remote host</span></span>
- [<span data-ttu-id="7ddf6-166">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="7ddf6-166">nx_secure_tls_session_reset</span></span>](#nx_secure_tls_session_reset)
  - <span data-ttu-id="7ddf6-167">NetX Secure TLS 세션 지우기 및 다시 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-167">Clear out and reset a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-168">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-168">nx_secure_tls_session_send</span></span>](#nx_secure_tls_session_send)
  - <span data-ttu-id="7ddf6-169">NetX Secure TLS 세션을 통해 데이터 보내기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-169">Send data through a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-170">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-170">nx_secure_tls_session_server_callback_set</span></span>](#nx_secure_tls_session_server_callback_set)
  - <span data-ttu-id="7ddf6-171">TlS가 TLS 서버 핸드셰이크 시작 시 호출할 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-171">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>
- [<span data-ttu-id="7ddf6-172">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-172">nx_secure_tls_session_sni_extension_parse</span></span>](#nx_secure_tls_session_sni_extension_parse)
  - <span data-ttu-id="7ddf6-173">TLS 클라이언트에서 받은 SNI(서버 이름 표시) 확장 구문 분석</span><span class="sxs-lookup"><span data-stu-id="7ddf6-173">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>
- [<span data-ttu-id="7ddf6-174">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-174">nx_secure_tls_session_sni_extension_set</span></span>](#nx_secure_tls_session_sni_extension_set)
  - <span data-ttu-id="7ddf6-175">원격 서버로 전송할 SNI(서버 이름 표시) 확장 DNS 이름 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-175">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>
- [<span data-ttu-id="7ddf6-176">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-176">nx_secure_tls_session_start</span></span>](#nx_secure_tls_session_start)
  - <span data-ttu-id="7ddf6-177">NetX Secure TLS 세션 시작</span><span class="sxs-lookup"><span data-stu-id="7ddf6-177">Start a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-178">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-178">nx_secure_tls_session_time_function_set</span></span>](#nx_secure_tls_session_time_function_set)
  - <span data-ttu-id="7ddf6-179">NetX Secure TLS 세션에 타임스탬프 함수 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-179">Assign a timestamp function to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-180">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-180">nx_secure_tls_trusted_certificate_add</span></span>](#nx_secure_tls_trusted_certificate_add)
  - <span data-ttu-id="7ddf6-181">NetX Secure TLS 세션에 신뢰할 수 있는 인증서 추가</span><span class="sxs-lookup"><span data-stu-id="7ddf6-181">Add trusted certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-182">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-182">nx_secure_tls_trusted_certificate_remove</span></span>](#nx_secure_tls_trusted_certificate_remove)
  - <span data-ttu-id="7ddf6-183">NetX Secure TLS 세션에서 신뢰할 수 있는 인증서 제거</span><span class="sxs-lookup"><span data-stu-id="7ddf6-183">Remove trusted certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7ddf6-184">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-184">nx_secure_x509_certificate_initialize</span></span>](#nx_secure_x509_certificate_initialize)
  - <span data-ttu-id="7ddf6-185">NetX Secure TLS에 대한 X.509 인증서 초기화</span><span class="sxs-lookup"><span data-stu-id="7ddf6-185">Initialize X.509 Certificate for NetX Secure TLS</span></span>
- [<span data-ttu-id="7ddf6-186">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-186">nx_secure_x509_common_name_dns_check</span></span>](#nx_secure_x509_common_name_dns_check)
  - <span data-ttu-id="7ddf6-187">X.509 인증서에서 DNS 이름 확인</span><span class="sxs-lookup"><span data-stu-id="7ddf6-187">Check DNS name against X.509 Certificate</span></span>
- [<span data-ttu-id="7ddf6-188">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-188">nx_secure_x509_crl_revocation_check</span></span>](#nx_secure_x509_crl_revocation_check)
  - <span data-ttu-id="7ddf6-189">제공된 CRL(인증서 해지 목록)에서 X.509 인증서 확인</span><span class="sxs-lookup"><span data-stu-id="7ddf6-189">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)]</span></span>
- [<span data-ttu-id="7ddf6-190">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-190">nx_secure_x509_dns_name_initialize</span></span>](#nx_secure_x509_dns_name_initialize)
  - <span data-ttu-id="7ddf6-191">X.509 DNS 이름 구조 초기화</span><span class="sxs-lookup"><span data-stu-id="7ddf6-191">Initialize an X.509 DNS name structure</span></span>
- [<span data-ttu-id="7ddf6-192">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-192">nx_secure_x509_extended_key_usage_extension_parse</span></span>](#nx_secure_x509_extended_key_usage_extension_parse)
  - <span data-ttu-id="7ddf6-193">X.509 인증서에서 X.509 확장 키 사용 확장 찾기 및 구문 분석</span><span class="sxs-lookup"><span data-stu-id="7ddf6-193">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>
- [<span data-ttu-id="7ddf6-194">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-194">nx_secure_x509_extension_find</span></span>](#nx_secure_x509_extension_find)
  - <span data-ttu-id="7ddf6-195">X.509 인증서에서 X.509 확장 찾기 및 반환</span><span class="sxs-lookup"><span data-stu-id="7ddf6-195">Find and return an X.509 extension in an X.509 certificate</span></span>
- [<span data-ttu-id="7ddf6-196">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-196">nx_secure_x509_key_usage_extension_parse</span></span>](#nx_secure_x509_key_usage_extension_parse)
  - <span data-ttu-id="7ddf6-197">X.509 인증서에서 X.509 키 사용 확장 찾기 및 구문 분석</span><span class="sxs-lookup"><span data-stu-id="7ddf6-197">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

## <a name="nx_secure_crypto_table_self_test"></a><span data-ttu-id="7ddf6-198">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="7ddf6-198">nx_secure_crypto_table_self_test</span></span>

<span data-ttu-id="7ddf6-199">암호화 방법에 대한 자체 테스트 수행</span><span class="sxs-lookup"><span data-stu-id="7ddf6-199">Perform self-test on the crypto methods</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-200">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-200">Prototype</span></span>

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a><span data-ttu-id="7ddf6-201">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-201">Description</span></span>

<span data-ttu-id="7ddf6-202">이 서비스는 유효성을 검사하기 위한 암호화 방법 자체 테스트를 통해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-202">This service runs through the crypto method self tests to validate.</span></span> <span data-ttu-id="7ddf6-203">자체 테스트는 NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK 기호를 정의한 상태로 NetX Secure 라이브러리를 빌드한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-203">The self test is available only if NetX Secure library is built with the symbol NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK defined.</span></span>

<span data-ttu-id="7ddf6-204">지원되는 각 암호화 방법에 대해 자체 테스트는 미리 정의된 입력 데이터를 제공하고 출력이 미리 정의된 예상 값과 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-204">For each supported crypto method, the self test provides pre-defined input data, and verified the output matches the pre-defined expected value.</span></span>

<span data-ttu-id="7ddf6-205">NetX Secure 암호화 자체 테스트는 다음 알고리즘 및 키 크기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-205">NetX Secure crypto self test supports the following algorithms and key sizes:</span></span>

- <span data-ttu-id="7ddf6-206">DES: 암호화 및 암호 해독</span><span class="sxs-lookup"><span data-stu-id="7ddf6-206">DES: encryption and decryption</span></span>
- <span data-ttu-id="7ddf6-207">3DES(Triple DES): 암호화 및 암호 해독</span><span class="sxs-lookup"><span data-stu-id="7ddf6-207">Triple DES (3DES): encryption and decryption</span></span>
- <span data-ttu-id="7ddf6-208">AES: CBC 모드 및 카운터 모드에서 128, 192, 256비트 키 크기, 암호화 및 암호 해독</span><span class="sxs-lookup"><span data-stu-id="7ddf6-208">AES: 128-, 192-, 256-bit key size, encryption and decryption, in CBC mode and counter mode.</span></span>
- <span data-ttu-id="7ddf6-209">HMAC-MD5: 인증 및 해시 계산</span><span class="sxs-lookup"><span data-stu-id="7ddf6-209">HMAC-MD5: authentication and hash computation</span></span>
- <span data-ttu-id="7ddf6-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, 인증 및 해시 계산</span><span class="sxs-lookup"><span data-stu-id="7ddf6-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, authentication and hash computation</span></span>
- <span data-ttu-id="7ddf6-211">MD5: 인증</span><span class="sxs-lookup"><span data-stu-id="7ddf6-211">MD5: authentication</span></span>
- <span data-ttu-id="7ddf6-212">PRF(의사 난수 함수): PRF_HMAC_SHA1 및 PRF_HMAC_SHA2-256</span><span class="sxs-lookup"><span data-stu-id="7ddf6-212">Pseudo-random Function (PRF): PRF_HMAC_SHA1 and PRF_HMAC_SHA2-256</span></span>
- <span data-ttu-id="7ddf6-213">RSA: 1024, 2048, 4096비트 RSA 전원-모듈러스 작업</span><span class="sxs-lookup"><span data-stu-id="7ddf6-213">RSA: 1024-, 2048-, 4096-bit RSA power-modulus operation</span></span>
- <span data-ttu-id="7ddf6-214">SHA: SHA1(96비트 및 160비트), SHA2(256비트, 384비트, 512비트) 인증</span><span class="sxs-lookup"><span data-stu-id="7ddf6-214">SHA: SHA1 (96- and 160-bit), SHA2 (256bit, 384bit, 512bit) authentication</span></span>

<span data-ttu-id="7ddf6-215">이 함수에는 위에 나열된 암호화 알고리즘에 대한 기본 제공 벡터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-215">This function has the built-in vectors for the crypto algorithms listed above.</span></span> <span data-ttu-id="7ddf6-216">그러나 이 함수에 전달된 *cipher_table* 에 나열된 항목만 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-216">However it only tests the ones listed in the *cipher_table* passed into this function.</span></span> <span data-ttu-id="7ddf6-217">예를 들어, TLS 세션의 경우는 암호 그룹 TLS_RSA_WITH_AES_128_CBC_SHA만 사용합니다. 이 함수는 RSA(1024, 2048, 4096비트), AES-CBC(128비트) 및 SHA1에서 자체 테스트를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-217">For example, for a TLS session uses only the ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, this function will perform self test on the RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) and SHA1.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-218">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-218">Parameters</span></span>

- <span data-ttu-id="7ddf6-219">**crypto_table** TLS 세션에서 사용 중인 암호화 테이블에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-219">**crypto_table** Pointer to the crypto table being used by the TLS session.</span></span> <span data-ttu-id="7ddf6-220">이것은 **_nx_secure_tls_session_create()_** 호출에 전달되는 것과 동일한 crypto_table입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-220">This is the same crypto_table being passed into the **_nx_secure_tls_session_create()_** call.</span></span>
- <span data-ttu-id="7ddf6-221">**metadata** 암호화 메타데이터 영역 공간에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-221">**metadata** Pointer to space for cryptography metadata area.</span></span> <span data-ttu-id="7ddf6-222">.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-222">.</span></span>
- <span data-ttu-id="7ddf6-223">**crypto_metadata_size** 메타데이터 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-223">**metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-224">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-224">Return Values</span></span>

- <span data-ttu-id="7ddf6-225">**NX_SECURE_TLS_SUCCESS**(0x00) 제공된 암호화 방법을 테스트했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-225">**NX_SECURE_TLS_SUCCESS** (0x00) Successfully tested the crypto methods provided.</span></span>
- <span data-ttu-id="7ddf6-226">**NX_PTR_ERROR**(0X07) 잘못된 암호화 방법 구조</span><span class="sxs-lookup"><span data-stu-id="7ddf6-226">**NX_PTR_ERROR** (0x07) Invalid crypto method structure</span></span>
- <span data-ttu-id="7ddf6-227">**NX_NOT_SUCCESSFUL**(0x43) 암호화 자체 테스트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-228">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-228">Allowed From</span></span>

<span data-ttu-id="7ddf6-229">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-229">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-230">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-230">Example</span></span>

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-231">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-231">See Also</span></span>

- <span data-ttu-id="7ddf6-232">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-232">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="7ddf6-233">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="7ddf6-233">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="7ddf6-234">사용자 제공 해시 함수를 사용하여 해시 값 계산</span><span class="sxs-lookup"><span data-stu-id="7ddf6-234">Computes hash value using user-supplied hash function</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-235">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-235">Prototype</span></span>

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="7ddf6-236">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-236">Description</span></span>

<span data-ttu-id="7ddf6-237">이 함수는 제공된 HMAC 암호화 방법과 키 문자열을 사용하여 지정된 메모리 영역에 있는 데이터 스트림의 해시 값을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-237">This function computes the hash value of the data stream in the specified memory area, using supplied HMAC crypto method and the key string.</span></span> <span data-ttu-id="7ddf6-238">모듈 해시 계산 함수는 NetX Secure 라이브러리가 NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK 기호를 정의하여 빌드된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-238">The module hash compute function is available only if NetX Secure library is built with the following symbol being defined: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-239">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-239">Parameters</span></span>

- <span data-ttu-id="7ddf6-240">**hmac_ptr** 해시 값 계산에 사용되는 HMAC 암호화 방법에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-240">**hmac_ptr** Pointer to the HMAC crypto method being used for the hash value computation.</span></span>
- <span data-ttu-id="7ddf6-241">**start_address** 데이터 버퍼의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-241">**start_address** The starting address of the data buffer</span></span>
- <span data-ttu-id="7ddf6-242">**end_address** 데이터 버퍼의 끝 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-242">**end_address** The ending address of the data buffer.</span></span> <span data-ttu-id="7ddf6-243">해시 계산은 이 end_address의 데이터를 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-243">Note that hash computation does not cover the data at this end_address.</span></span>
- <span data-ttu-id="7ddf6-244">**key** HMAC 계산에 사용되는 키 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-244">**key** The key string being used in the HMAC computation.</span></span>
- <span data-ttu-id="7ddf6-245">**key_length** 문자열의 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-245">**key_length** The size of the key string, in bytes</span></span>
- <span data-ttu-id="7ddf6-246">**metadata** HMAC 알고리즘에서 사용하는 공간에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-246">**metadata** Pointer to space used by the HMAC algorithm.</span></span>
- <span data-ttu-id="7ddf6-247">**crypto_metadata_size** 메타데이터 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-247">**metadata_size** Size of the metadata buffer.</span></span>
- <span data-ttu-id="7ddf6-248">**output_buffer** 해시 출력이 저장되는 메모리 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-248">**output_buffer** The memory location where the hash output is being stored at.</span></span>
- <span data-ttu-id="7ddf6-249">**output_buffer_size** 출력 버퍼의 사용 가능한 공간(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-249">**output_buffer_size** The available space of the output buffer, in bytes</span></span>
- <span data-ttu-id="7ddf6-250">**actual_size** output_buffer에 기록되는 실제 바이트 수를 나타내는 함수에서 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-250">**actual_size** Returned by the function indicating the actual number of bytes being written into the output_buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-251">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-251">Return Values</span></span>

- <span data-ttu-id="7ddf6-252">**0** 해시 값을 계산했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-252">**0** Successfully computed the hash value.</span></span>
- <span data-ttu-id="7ddf6-253">**1** 해시 계산에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-253">**1** The hash computation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-254">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-254">Allowed From</span></span>

<span data-ttu-id="7ddf6-255">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-255">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-256">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-256">Example</span></span>

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-257">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-257">See Also</span></span>

- <span data-ttu-id="7ddf6-258">nx_secure_crypto_method_self_test</span><span class="sxs-lookup"><span data-stu-id="7ddf6-258">nx_secure_crypto_method_self_test</span></span>

## <a name="nx_secure_tls_active_certificate_set"></a><span data-ttu-id="7ddf6-259">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-259">nx_secure_tls_active_certificate_set</span></span>

<span data-ttu-id="7ddf6-260">NetX Secure TLS 세션에 대해 활성 ID 인증서 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-260">Set the active identity certificate for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-261">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-261">Prototype</span></span>

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="7ddf6-262">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-262">Description</span></span>

<span data-ttu-id="7ddf6-263">이 서비스는 세션 콜백 내에서 호출됩니다(nx_secure_tls_session_client_callback_set 및 nx_secure_tls_session_server_callback_set 참조).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-263">This service is intended to be called from within a session callback (see nx_secure_tls_session_client_callback_set and nx_secure_tls_session_server_callback_set).</span></span> <span data-ttu-id="7ddf6-264">이전에 초기화된 NX_SECURE_X509_CERT 구조체를 사용하여 호출하는 경우 기본 ID 인증서 대신 해당 인증서가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-264">When called with a previously-initialized NX_SECURE_X509_CERT structure, that certificate will be used instead of the default identity certificate.</span></span> <span data-ttu-id="7ddf6-265">대부분의 경우 인증서를 로컬 저장소에 추가해야 합니다(nx_secure_tls_local_certificate_add 참조). 그러지 않으면 TLS 핸드셰이크가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-265">In most cases, the certificate must have been added to the local store (see nx_secure_tls_local_certificate_add) or the TLS handshake may fail.</span></span>

<span data-ttu-id="7ddf6-266">이 서비스는 TLS에서 여러 ID 인증서를 지원할 수 있도록 하기 위해 고안되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-266">This service is intended to allow TLS to support multiple identity certificates.</span></span> <span data-ttu-id="7ddf6-267">이 서비스는 여러 네트워크 주소를 제공하는 TLS 서버에 유용합니다. 이러한 서버는 클라이언트의 진입점에 따라 원격 클라이언트에 제공할 적절한 인증서를 선택할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-267">This is useful for a TLS server that services multiple network addresses so the server can pick an appropriate certificate to provide to the remote client depending on the client's entrypoint.</span></span> <span data-ttu-id="7ddf6-268">TLS 클라이언트의 경우 이 루틴을 사용하여 서버가 TLS 핸드셰이크에서 자신을 식별한 후에 런타임에 원격 서버로 전송되는 인증서를 변경할 수 있습니다(TLS 서버 사용 사례보다 더 드문 경우).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-268">For a TLS client, this routine may be used to change the certificate sent to a remote server at runtime after the server has identified itself in the TLS handshake (this is more rare than the TLS server use-case).</span></span>

<span data-ttu-id="7ddf6-269">여러 인증서가 동일한 X.509 고유 이름을 공유할 수 있는 경우 인증서와는 별개인 숫자 식별자를 도입하는 nx_secure_tls_server_certificate_add를 사용하여 인증서를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-269">In the case where multiple certificates may share the same X.509 distinguished name, certificates will need to be added using nx_secure_tls_server_certificate_add, which introduces a numeric identifier separate from the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-270">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-270">Parameters</span></span>

- <span data-ttu-id="7ddf6-271">**session_ptr** 세션 콜백에 전달되는 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-271">**session_ptr** Pointer to a TLS Session instance passed into the session callback.</span></span>
- <span data-ttu-id="7ddf6-272">**certificate** 현재 세션에 사용할 초기화된 X.509 인증서에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-272">**certificate** Pointer to an initialized X.509 certificate that is to be used for the current session.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-273">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-273">Return Values</span></span>

- <span data-ttu-id="7ddf6-274">**NX_SUCCESS**(0x00) 세션에 인증서를 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-274">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="7ddf6-275">**NX_PTR_ERROR**(0X07) 잘못된 TLS 세션 또는 인증서 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-275">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-276">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-276">Allowed From</span></span>

<span data-ttu-id="7ddf6-277">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-278">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-278">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-279">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-279">See Also</span></span>

- <span data-ttu-id="7ddf6-280">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-280">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-281">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-281">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="7ddf6-282">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-282">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="7ddf6-283">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-283">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="7ddf6-284">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-284">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="7ddf6-285">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-285">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="7ddf6-286">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-286">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_client_psk_set"></a><span data-ttu-id="7ddf6-287">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-287">nx_secure_tls_client_psk_set</span></span>

<span data-ttu-id="7ddf6-288">NetX Secure TLS 클라이언트 세션에 대해 미리 공유한 키 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-288">Set a Pre-Shared Key for a NetX Secure TLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-289">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-289">Prototype</span></span>

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a><span data-ttu-id="7ddf6-290">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-290">Description</span></span>

<span data-ttu-id="7ddf6-291">이 서비스는 PSK(미리 공유한 키), 해당 ID 문자열 및 ID 힌트를 TLS 세션 제어 블록에 추가하고, 해당 PSK를 후속 TLS 클라이언트 연결에서 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-291">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block, and sets that PSK to be used in subsequent TLS Client connections.</span></span> <span data-ttu-id="7ddf6-292">PSK는 PSK 암호 그룹을 설정하고 사용할 때 디지털 인증서 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-292">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="7ddf6-293">이 경우 PSK는 TLS 클라이언트가 통신하려는 특정 원격 TLS 서버와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-293">In this case, the PSK is associated with a specific remote TLS Server with which the TLS Client wishes to communicate.</span></span> <span data-ttu-id="7ddf6-294">이 API를 통해 설정된 PSK는 다음 TLS 핸드셰이크 중에 원격 TLS 서버 호스트에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-294">The PSK set through this API will be provided to the remote TLS Server host during the next TLS handshake.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-295">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-295">Parameters</span></span>

- <span data-ttu-id="7ddf6-296">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-296">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-297">**pre_shared_key** 실제 PSK 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-297">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="7ddf6-298">**psk_length** PSK 값의 길이</span><span class="sxs-lookup"><span data-stu-id="7ddf6-298">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="7ddf6-299">**psk_identity** 이 PSK 값을 식별하는 데 사용되는 문자열</span><span class="sxs-lookup"><span data-stu-id="7ddf6-299">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="7ddf6-300">**identity_length** PSK ID의 길이</span><span class="sxs-lookup"><span data-stu-id="7ddf6-300">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="7ddf6-301">**hint** TLS 서버에서 선택할 PSK 그룹을 나타내는 데 사용되는 문자열</span><span class="sxs-lookup"><span data-stu-id="7ddf6-301">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="7ddf6-302">**hint_length** 힌트 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="7ddf6-302">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-303">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-303">Return Values</span></span>

- <span data-ttu-id="7ddf6-304">**NX_SUCCESS**(0x00) PSK를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-304">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="7ddf6-305">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-305">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7ddf6-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE**(0x125) 다른 PSK를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-307">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-307">Allowed From</span></span>

<span data-ttu-id="7ddf6-308">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-308">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-309">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-309">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-310">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-310">See Also</span></span>

- <span data-ttu-id="7ddf6-311">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-311">nx_secure_tls_psk_add</span></span>
- <span data-ttu-id="7ddf6-312">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-312">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-313">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-313">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-314">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-314">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-315">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-315">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_initialize"></a><span data-ttu-id="7ddf6-316">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-316">nx_secure_tls_initialize</span></span>

<span data-ttu-id="7ddf6-317">NetX Secure TLS 모듈 초기화</span><span class="sxs-lookup"><span data-stu-id="7ddf6-317">Initializes the NetX Secure TLS module</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-318">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-318">Prototype</span></span>

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="7ddf6-319">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-319">Description</span></span>

<span data-ttu-id="7ddf6-320">이 서비스는 NetX Secure TLS 모듈을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-320">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="7ddf6-321">다른 NetX Secure 서비스에 액세스하려면 먼저 이 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-321">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-322">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-322">Parameters</span></span>

<span data-ttu-id="7ddf6-323">없음</span><span class="sxs-lookup"><span data-stu-id="7ddf6-323">None</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-324">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-324">Return Values</span></span>

<span data-ttu-id="7ddf6-325">없음</span><span class="sxs-lookup"><span data-stu-id="7ddf6-325">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-326">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-326">Allowed From</span></span>

<span data-ttu-id="7ddf6-327">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-327">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-328">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-328">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-329">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-329">See Also</span></span>

- <span data-ttu-id="7ddf6-330">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-330">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_local_certificate_add"></a><span data-ttu-id="7ddf6-331">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-331">nx_secure_tls_local_certificate_add</span></span>

<span data-ttu-id="7ddf6-332">NetX Secure TLS 세션에 로컬 인증서 추가</span><span class="sxs-lookup"><span data-stu-id="7ddf6-332">Add a local certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-333">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-333">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="7ddf6-334">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-334">Description</span></span>

<span data-ttu-id="7ddf6-335">이 서비스는 초기화된 NX_SECURE_X509_CERT 구조체 인스턴스를 TLS 세션의 로컬 저장소에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-335">This service adds an initialized NX_SECURE_X509_CERT structure instance to the local store of a TLS session.</span></span> <span data-ttu-id="7ddf6-336">이 인증서는 nx_secure_x509_certificate_initialize를 사용하여 인증서 구조를 초기화하는 동안 ID 인증서로 표시되었거나 TLS 핸드셰이크 중에 원격 호스트에 제공되는 인증서 체인의 일부로 발급자로서 표시된 경우 TLS 스택에서 TLS 핸드셰이크 중에 디바이스를 식별하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-336">This certificate may used by the TLS stack to identify the device during the TLS handshake (if it was marked as an identity certificate during initialization of the certificate structure using nx_secure_x509_certificate_initialize), or as an issuer as part of a certificate chain provided to the remote host during the TLS handshake.</span></span>

<span data-ttu-id="7ddf6-337">동일한 일반 이름을 가진 여러 로컬 인증서가 필요한 경우 *nx_secure_tls_server_certificate_add* 서비스를 사용하여 인증서를 추가할 수 있습니다(아래 경고 참조).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-337">If multiple local certificates with the same Common Name are needed, certificates may be added using the *nx_secure_tls_server_certificate_add* service (see warning below).</span></span>

<span data-ttu-id="7ddf6-338">TLS 서버 모드에서는 인증서가 **필수** 입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-338">A certificate is **required** for TLS Server mode.</span></span>

<span data-ttu-id="7ddf6-339">TLS 클라이언트 모드에서는 인증서가 *선택 사항* 입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-339">A certificate is *optional* for TLS Client mode.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddf6-340">를 사용하는 경우 이 API를 동일한 TLS 세션에서 사용하면 안 됩니다. 서버 인증서 API는 X.509 일반 이름에 따라 각 인증서에 대한 고유한 숫자 식별자 및 nx_secure_tls_local_certificate_add 인덱스를 사용합니다. 로컬 인증서 서비스는 단일 ID 인증서만 사용하는 애플리케이션에 숫자 식별자에 대한 편리한 대안을 제공합니다. 즉, 일반적인 이름을 사용하면 애플리케이션에서 숫자 식별자를 추적하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-340">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-341">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-341">Parameters</span></span>

- <span data-ttu-id="7ddf6-342">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-342">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-343">**certificate_ptr** 초기화된 TLS 인증서 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-343">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-344">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-344">Return Values</span></span>

- <span data-ttu-id="7ddf6-345">**NX_SUCCESS**(0x00) 인증서를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="7ddf6-346">**NX_INVALID_PARAMETERS**(0x4D) 잘못되었거나 중복된 인증서를 추가하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-346">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid or duplicate certificate.</span></span>
- <span data-ttu-id="7ddf6-347">**NX_PTR_ERROR**(0X07) 잘못된 TLS 세션 또는 인증서 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-347">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-348">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-348">Allowed From</span></span>

<span data-ttu-id="7ddf6-349">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-350">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-350">Example</span></span>

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-351">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-351">See Also</span></span>

- <span data-ttu-id="7ddf6-352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-355">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-355">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="7ddf6-356">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-356">nx_secure_tls_local_certificate_find</span></span>

## <a name="nx_secure_tls_local_certificate_find"></a><span data-ttu-id="7ddf6-357">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-357">nx_secure_tls_local_certificate_find</span></span>

<span data-ttu-id="7ddf6-358">일반 이름으로 NetX Secure TLS 세션에서 로컬 인증서 찾기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-358">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-359">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-359">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a><span data-ttu-id="7ddf6-360">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-360">Description</span></span>

<span data-ttu-id="7ddf6-361">이 서비스는 TLS 세션의 로컬 디바이스 인증서 저장소에서 인증서를 찾고, 저장소의 NX_SECURE_X509_CERT 구조체에 대한 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-361">This service finds a certificate in the local device certificate store of a TLS session and returns a pointer to the NX_SECURE_X509_CERT structure in the store.</span></span> <span data-ttu-id="7ddf6-362">common_name 매개 변수 및 해당 길이(name_length)는 인증서의 X.509 주체 일반 이름 필드와 일치시켜 저장소에서 인증서를 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-362">The common_name parameter and it's length (name_length) are used to identify the certificate in the store by matching the certificate's X.509 Subject Common Name field.</span></span>

<span data-ttu-id="7ddf6-363">동일한 일반 이름을 가진 인증서가 두 개 이상 있는 경우 첫 번째 인증서만 반환됩니다. 대신 *nx_secure_tls_server_certificate_find* 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-363">If more than one certificate with the same Common Name is present, only the first one will be returned – use *nx_secure_tls_server_certificate_find* instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddf6-364">를 사용하는 경우 이 API를 동일한 TLS 세션에서 사용하면 안 됩니다. 서버 인증서 API는 X.509 일반 이름에 따라 각 인증서에 대한 고유한 숫자 식별자 및 nx_secure_tls_local_certificate_add 인덱스를 사용합니다. 로컬 인증서 서비스는 단일 ID 인증서만 사용하는 애플리케이션에 숫자 식별자에 대한 편리한 대안을 제공합니다. 즉, 일반적인 이름을 사용하면 애플리케이션에서 숫자 식별자를 추적하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-364">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-365">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-365">Parameters</span></span>

- <span data-ttu-id="7ddf6-366">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-366">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-367">**certificate** 일치하는 인증서에 대한 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-367">**certificate** Return Pointer to matched certificate.</span></span>
- <span data-ttu-id="7ddf6-368">**common_name** 일치시킬 일반 이름 문자열(DNS 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-368">**common_name** Common Name string to match (DNS name).</span></span>
- <span data-ttu-id="7ddf6-369">**common_name_length** common_name 문자열 데이터의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-369">**name_length** Length of common_name string data.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-370">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-370">Return Values</span></span>

- <span data-ttu-id="7ddf6-371">**NX_SUCCESS**(0x00) 인증서를 찾았으며 "certificate" 매개 변수에서 포인터가 반환되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-371">**NX_SUCCESS** (0x00) Certificate was found and pointer returned in "certificate" parameter.</span></span>
- <span data-ttu-id="7ddf6-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0x119) 제공된 일반 이름을 가진 인증서를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate with the supplied Common Name was found.</span></span>
- <span data-ttu-id="7ddf6-373">**NX_PTR_ERROR**(0X07) 잘못된 TLS 세션, 인증서 포인터 또는 일반 이름 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-373">**NX_PTR_ERROR** (0x07) Invalid TLS session, certificate pointer, or common name string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-374">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-374">Allowed From</span></span>

<span data-ttu-id="7ddf6-375">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-376">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-376">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-377">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-377">See Also</span></span>

- <span data-ttu-id="7ddf6-378">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-378">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-379">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-379">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-380">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-380">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-381">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-381">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="7ddf6-382">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-382">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_local_certificate_remove"></a><span data-ttu-id="7ddf6-383">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-383">nx_secure_tls_local_certificate_remove</span></span>

<span data-ttu-id="7ddf6-384">NetX Secure TLS 세션에서 로컬 인증서 제거</span><span class="sxs-lookup"><span data-stu-id="7ddf6-384">Remove local certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-385">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-385">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a><span data-ttu-id="7ddf6-386">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-386">Description</span></span>

<span data-ttu-id="7ddf6-387">이 서비스는 인증서의 일반 이름 필드에 입력된 TLS 세션에서 로컬 인증서 인스턴스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-387">This service removes a local certificate instance from a TLS session, keyed on the Common Name field in the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddf6-388">를 사용하는 경우 이 API를 동일한 TLS 세션에서 사용하면 안 됩니다. 서버 인증서 API는 X.509 일반 이름에 따라 각 인증서에 대한 고유한 숫자 식별자 및 nx_secure_tls_local_certificate_add 인덱스를 사용합니다. 로컬 인증서 서비스는 단일 ID 인증서만 사용하는 애플리케이션에 숫자 식별자에 대한 편리한 대안을 제공합니다. 즉, 일반적인 이름을 사용하면 애플리케이션에서 숫자 식별자를 추적하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-388">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-389">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-389">Parameters</span></span>

- <span data-ttu-id="7ddf6-390">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-390">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-391">**common_name** 제거할 인증서의 일반 이름 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-391">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="7ddf6-392">**common_name_length** 일반 이름 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-392">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-393">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-393">Return Values</span></span>

- <span data-ttu-id="7ddf6-394">**NX_SUCCESS**(0x00) 인증서를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-394">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="7ddf6-395">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-395">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7ddf6-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0x119) 인증서를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-397">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-397">Allowed From</span></span>

<span data-ttu-id="7ddf6-398">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-399">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-399">Example</span></span>

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-400">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-400">See Also</span></span>

- <span data-ttu-id="7ddf6-401">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-401">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-402">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-402">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-403">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-403">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-404">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-404">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_metadata_size_calculate"></a><span data-ttu-id="7ddf6-405">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-405">nx_secure_tls_metadata_size_calculate</span></span>

<span data-ttu-id="7ddf6-406">NetX Secure TLS 세션의 암호화 메타데이터 크기 계산</span><span class="sxs-lookup"><span data-stu-id="7ddf6-406">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-407">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-407">Prototype</span></span>

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a><span data-ttu-id="7ddf6-408">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-408">Description</span></span>

<span data-ttu-id="7ddf6-409">이 서비스는 특정 TLS 세션 및 TLS 암호화 테이블에 필요한 암호화 메타데이터의 크기를 계산하고 반환합니다(암호화 테이블에 대한 자세한 내용은 "암호화 방법으로 TLS 초기화" 섹션 참조).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-409">This service calculates and returns the size of the cryptographic metadata needed for a particular TLS session and TLS cryptography table (see the section "Initializing TLS with Cryptographic Methods" for more information on the cryptographic cipher table).</span></span>

<span data-ttu-id="7ddf6-410">nx_secure_tls_session_create에 전달되는 메타데이터 버퍼의 크기를 계산하려면 원하는 암호화 테이블을 사용하여 이 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-410">This service should be called with the desired cryptographic table to calculate the size of the metadata buffer passed into nx_secure_tls_session_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-411">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-411">Parameters</span></span>

- <span data-ttu-id="7ddf6-412">**crypto_table** 전체 NetX Secure TLS 암호화 테이블에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-412">**crypto_table** Pointer to a complete NetX Secure TLS cryptography table.</span></span>
- <span data-ttu-id="7ddf6-413">**metadata_size** 크기 계산의 출력(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-413">**metadata_size** The output of the size calculation in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-414">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-414">Return Values</span></span>

- <span data-ttu-id="7ddf6-415">**NX_SUCCESS**(0x00) 메타데이터 크기를 계산했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-415">**NX_SUCCESS** (0x00) Successful calculation of metadata size.</span></span>
- <span data-ttu-id="7ddf6-416">**NX_PTR_ERROR**(0X07) 잘못된 암호화 테이블 또는 반환 크기 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-416">**NX_PTR_ERROR** (0x07) Invalid crypto table or return size pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-417">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-417">Allowed From</span></span>

<span data-ttu-id="7ddf6-418">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-418">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-419">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-419">Example</span></span>

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-420">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-420">See Also</span></span>

- <span data-ttu-id="7ddf6-421">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-421">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_packet_allocate"></a><span data-ttu-id="7ddf6-422">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-422">nx_secure_tls_packet_allocate</span></span>

<span data-ttu-id="7ddf6-423">NetX Secure TLS 세션에 대한 패킷 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-423">Allocate a packet for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-424">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-424">Prototype</span></span>

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7ddf6-425">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-425">Description</span></span>

<span data-ttu-id="7ddf6-426">이 서비스는 지정된 NX_PACKET_POOL의 지정된 활성 TLS 세션에 대한 NX_PACKET을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-426">This service allocates an NX_PACKET for the specified active TLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="7ddf6-427">애플리케이션에서 이 서비스를 호출하여 TLS 연결을 통해 보낼 데이터 패킷을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-427">This service should be called by the application to allocate data packets to be sent over a TLS connection.</span></span> <span data-ttu-id="7ddf6-428">이 서비스를 호출하려면 먼저 TLS 세션을 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-428">The TLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="7ddf6-429">패킷 데이터가 채워진 후 TLS 머리글 및 바닥글 데이터를 추가할 수 있도록 할당된 패킷이 올바르게 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-429">The allocated packet is properly initialized so that TLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="7ddf6-430">그렇지 않으면 이 동작은 *nx_packet_allocate* 와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-430">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-431">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-431">Parameters</span></span>

- <span data-ttu-id="7ddf6-432">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-432">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-433">**pool_ptr** 패킷을 할당할 NX_PACKET_POOL에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-433">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="7ddf6-434">**packet_ptr** 새로 할당된 패킷에 대한 출력 포인터</span><span class="sxs-lookup"><span data-stu-id="7ddf6-434">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="7ddf6-435">**wait_option** 패킷 할당의 일시 중단 옵션</span><span class="sxs-lookup"><span data-stu-id="7ddf6-435">**wait_option** Suspension option for packet allocation.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-436">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-436">Return Values</span></span>

- <span data-ttu-id="7ddf6-437">**NX_SUCCESS** (0x00) 패킷을 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-437">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="7ddf6-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**(0x111) 기본 패킷을 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="7ddf6-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED**(0x101) 제공된 TLS 세션이 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-440">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-440">Allowed From</span></span>

<span data-ttu-id="7ddf6-441">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-442">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-442">Example</span></span>

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-443">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-443">See Also</span></span>

- <span data-ttu-id="7ddf6-444">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-444">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="7ddf6-445">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-445">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-446">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-446">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-447">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-447">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-448">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-448">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7ddf6-449">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-449">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7ddf6-450">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-450">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7ddf6-451">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7ddf6-451">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7ddf6-452">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-452">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_psk_add"></a><span data-ttu-id="7ddf6-453">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-453">nx_secure_tls_psk_add</span></span>

<span data-ttu-id="7ddf6-454">NetX Secure TLS 세션에 미리 공유한 키 추가</span><span class="sxs-lookup"><span data-stu-id="7ddf6-454">Add a Pre-Shared Key to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-455">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-455">Prototype</span></span>

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="7ddf6-456">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-456">Description</span></span>

<span data-ttu-id="7ddf6-457">이 서비스는 PSK(미리 공유한 키), 해당 ID 문자열 및 ID 힌트를 TLS 세션 제어 블록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-457">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block.</span></span> <span data-ttu-id="7ddf6-458">PSK는 PSK 암호 그룹을 설정하고 사용할 때 디지털 인증서 대신 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-458">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-459">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-459">Parameters</span></span>

- <span data-ttu-id="7ddf6-460">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-460">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-461">**pre_shared_key** 실제 PSK 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-461">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="7ddf6-462">**psk_length** PSK 값의 길이</span><span class="sxs-lookup"><span data-stu-id="7ddf6-462">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="7ddf6-463">**psk_identity** 이 PSK 값을 식별하는 데 사용되는 문자열</span><span class="sxs-lookup"><span data-stu-id="7ddf6-463">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="7ddf6-464">**identity_length** PSK ID의 길이</span><span class="sxs-lookup"><span data-stu-id="7ddf6-464">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="7ddf6-465">**hint** TLS 서버에서 선택할 PSK 그룹을 나타내는 데 사용되는 문자열</span><span class="sxs-lookup"><span data-stu-id="7ddf6-465">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="7ddf6-466">**hint_length** 힌트 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="7ddf6-466">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-467">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-467">Return Values</span></span>

- <span data-ttu-id="7ddf6-468">**NX_SUCCESS**(0x00) PSK를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-468">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="7ddf6-469">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-469">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7ddf6-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE**(0x125) 다른 PSK를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125)  Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-471">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-471">Allowed From</span></span>

<span data-ttu-id="7ddf6-472">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-473">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-473">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-474">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-474">See Also</span></span>

- <span data-ttu-id="7ddf6-475">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-475">nx_secure_tls_client_psk_set</span></span>
- <span data-ttu-id="7ddf6-476">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-476">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-477">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-477">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-478">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-478">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-479">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-479">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_remote_certificate_allocate"></a><span data-ttu-id="7ddf6-480">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-480">nx_secure_tls_remote_certificate_allocate</span></span>

<span data-ttu-id="7ddf6-481">원격 TLS 호스트에서 제공하는 인증서를 위한 공간 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-481">Allocate space for the certificate provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-482">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-482">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a><span data-ttu-id="7ddf6-483">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-483">Description</span></span>

<span data-ttu-id="7ddf6-484">이 서비스는 TLS 세션 중에 원격 호스트에서 제공하는 인증서를 위한 공간을 할당하기 위해 초기화되지 않은 NX_SECURE_X509_CERT 구조체 인스턴스를 TLS 세션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-484">This service adds an uninitialized NX_SECURE_X509_CERT structure instance to a TLS session for the purpose of allocating space for certificates provided by a remote host during a TLS session.</span></span> <span data-ttu-id="7ddf6-485">원격 인증서 데이터는 NetX Secure TLS에서 구문 분석되며 해당 정보는 이 함수에 제공된 인증서 구조 인스턴스를 채우는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-485">The remote certificate data is parsed by NetX Secure TLS and that information is used to populate the certificate structure instance provided to this function.</span></span> <span data-ttu-id="7ddf6-486">이러한 방식으로 추가된 인증서는 연결된 목록에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-486">Certificates added in this manner are placed in a linked list.</span></span>

<span data-ttu-id="7ddf6-487">원격 호스트가 여러 인증서를 제공할 것으로 예상되는 경우 이 함수를 반복적으로 호출하여 모든 인증서에 대한 공간을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-487">If it is expected that the remote host will provide multiple certificates, this function should be called repeatedly to allocate space for all certificates.</span></span> <span data-ttu-id="7ddf6-488">인증서 연결 목록의 끝에 추가 인증서가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-488">The additional certificates are added to the end of the certificate linked list.</span></span>

<span data-ttu-id="7ddf6-489">PSK(미리 공유한 키) 암호 그룹이 사용되고 있지 않을 경우 원격 인증서를 할당하지 못하므로 TLS 핸드셰이크 동안 TLS 클라이언트 모드가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-489">Failure to allocate a remote certificate will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="7ddf6-490">*raw_certificate_buffer* 매개 변수는 수신 원격 인증서를 저장하기 위해 할당된 공간을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-490">The *raw_certificate_buffer* parameter points to space allocated to store the incoming remote certificate.</span></span> <span data-ttu-id="7ddf6-491">서명에 대해 SHA-256을 사용하는 2048비트의 RSA 키를 포함하는 일반적인 인증서의 범위는 1000-2000바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-491">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="7ddf6-492">버퍼는 적어도 해당 크기를 보유할 수 있을 만큼 커야 하지만 원격 호스트 인증서에 따라 훨씬 더 작거나 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-492">The buffer should be large enough to at least hold that size, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="7ddf6-493">버퍼가 너무 작아서 수신 인증서를 저장할 수 없는 경우 TLS 핸드셰이크는 오류를 발생하면서 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-493">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

<span data-ttu-id="7ddf6-494">TLS 서버 모드의 경우에는 클라이언트 인증서 인증을 사용하도록 설정한 경우에만 원격 인증서를 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-494">For TLS Server mode, a remote certificate allocation is needed only if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-495">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-495">Parameters</span></span>

- <span data-ttu-id="7ddf6-496">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-496">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-497">**certificate_ptr** 초기화되지 않은 X.509 인증서 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-497">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="7ddf6-498">**raw_certificate_buffer** 원격 호스트에서 받은 구문 분석되지 않은 인증서를 저장할 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-498">**raw_certificate_buffer** Pointer to a buffer to hold the un-parsed certificate received from the remote host.</span></span>
- <span data-ttu-id="7ddf6-499">**raw_buffer_size** 원시 인증서 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-499">**raw_buffer_size** Size of the raw certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-500">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-500">Return Values</span></span>

- <span data-ttu-id="7ddf6-501">**NX_SUCCESS**(0x00) 인증서를 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-501">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="7ddf6-502">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-502">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7ddf6-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**(0x12D) 제공된 버퍼가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="7ddf6-504">**NX_INVALID_PARAMETERS**(0x4D) 잘못된 인증서를 추가하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-504">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-505">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-505">Allowed From</span></span>

<span data-ttu-id="7ddf6-506">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-507">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-507">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-508">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-508">See Also</span></span>

- <span data-ttu-id="7ddf6-509">nx_secure_x509_certificate_initialize,</span><span class="sxs-lookup"><span data-stu-id="7ddf6-509">nx_secure_x509_certificate_initialize,</span></span>
- <span data-ttu-id="7ddf6-510">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-510">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a><span data-ttu-id="7ddf6-511">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-511">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

<span data-ttu-id="7ddf6-512">원격 TLS 호스트에서 제공하는 모든 인증서를 위한 공간 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-512">Allocate space for all certificates provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-513">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-513">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="7ddf6-514">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-514">Description</span></span>

<span data-ttu-id="7ddf6-515">이 서비스는 TLS 클라이언트 인스턴스에서 X.509 인증 및 검증을 수행하기 위해 원격 서버 호스트에서 수신 인증서 체인을 처리하기 위한 공간을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-515">This service allocates space to process incoming certificate chains from remote server hosts in order to perform X.509 authentication and verification in a TLS Client instance.</span></span> <span data-ttu-id="7ddf6-516">TLS 서버 모드의 경우 클라이언트 X.509 인증서 인증을 사용하도록 설정하는 경우에만 원격 인증서를 할당해야 합니다. TLS 서버 인스턴스의 경우 서비스 *nx_secure_tls_session_x509_client_verify_configure* 를 대신 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-516">For TLS Server mode, remote certificate allocation is needed only if client X.509 certificate authentication is enabled – for TLS Server instances the service *nx_secure_tls_session_x509_client_verify_configure* should be used instead.</span></span>

<span data-ttu-id="7ddf6-517">PSK(미리 공유한 키) 암호 그룹이 사용되고 있지 않을 경우 원격 인증서를 할당하지 못하므로 TLS 핸드셰이크 동안 TLS 클라이언트 모드가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-517">Failure to allocate remote certificates will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="7ddf6-518">*certificate_buffer* 매개 변수는 수신 원격 인증서 및 해당 인증서에 필요한 제어 블록을 저장하기 위해 할당된 공간을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-518">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="7ddf6-519">버퍼는 각 인증서에 지정된 것과 같은 부분이 있는 인증서 수(*certs_number*)로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-519">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="7ddf6-520">*buffer_size* 매개 변수는 버퍼의 크기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-520">The *buffer_size*  parameter indicates the size of the buffer.</span></span> <span data-ttu-id="7ddf6-521">필요한 공간은 다음 수식을 사용하여 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-521">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="7ddf6-522">서명에 대해 SHA-256을 사용하는 2048비트의 RSA 키를 포함하는 일반적인 인증서의 범위는 1000-2000바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-522">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="7ddf6-523">버퍼는 적어도 각 인증서에 대한 해당 크기를 보유할 수 있을 만큼 커야 하지만 원격 호스트 인증서에 따라 훨씬 더 작거나 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-523">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="7ddf6-524">버퍼가 너무 작아서 수신 인증서를 저장할 수 없는 경우 TLS 핸드셰이크는 오류를 발생하면서 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-524">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-525">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-525">Parameters</span></span>

- <span data-ttu-id="7ddf6-526">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-526">**session_ptr** Pointer to a previously created TLS Session  instance.</span></span>
- <span data-ttu-id="7ddf6-527">**certs_number** 제공된 버퍼에서 할당할 인증서의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-527">**certs_number** Number of certificates to allocate from the  provided buffer.</span></span>
- <span data-ttu-id="7ddf6-528">**certificate_buffer** 원격 호스트에서 받은 인증서를 저장할 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-528">**certificate_buffer** Pointer to a buffer to hold certificates received  from a remote host.</span></span>
- <span data-ttu-id="7ddf6-529">**buffer_size** 인증서 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-529">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-530">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-530">Return Values</span></span>

- <span data-ttu-id="7ddf6-531">**NX_SUCCESS**(0x00) 인증서를 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-531">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="7ddf6-532">**NX_PTR_ERROR**(0x07) TLS 세션 또는 버퍼 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-532">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="7ddf6-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**(0x12D) 제공된 버퍼가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="7ddf6-534">**NX_INVALID_PARAMETERS**(0x4D) 버퍼가 너무 작아서 원하는 수의 인증서를 보유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-534">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold  the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-535">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-535">Allowed From</span></span>

<span data-ttu-id="7ddf6-536">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-536">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-537">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-537">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-538">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-538">See Also</span></span>

- <span data-ttu-id="7ddf6-539">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-539">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-540">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-540">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_free_all"></a><span data-ttu-id="7ddf6-541">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="7ddf6-541">nx_secure_tls_remote_certificate_free_all</span></span>

<span data-ttu-id="7ddf6-542">수신 인증서에 대해 할당된 사용 가능한 공간</span><span class="sxs-lookup"><span data-stu-id="7ddf6-542">Free space allocated for incoming certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-543">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-543">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7ddf6-544">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-544">Description</span></span>

<span data-ttu-id="7ddf6-545">이 서비스는 nx_secure_tls_remote_certificate_allocated를 통해 특정 TLS 세션에 할당된 모든 인증서 버퍼를 해당 세션의 사용 가능한 인증서 공간으로 반환하여 사용 가능한 상태로 해제하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-545">This service is used to free all of the certificate buffers allocated to a particular TLS Session by nx_secure_tls_remote_certificate_allocated by returning them to that session's free certificate space.</span></span> <span data-ttu-id="7ddf6-546">이 서비스가 있으면 애플리케이션은 nx_secure_tls_session_delete 및 nx_secure_tls_session_create를 사용하여 TLS 세션 개체를 삭제했다가 다시 만들 필요가 없이, TLS 세션 개체를 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-546">This may be necessary if an application reuses a TLS session object without deleting it and recreating it with nx_secure_tls_session_delete and nx_secure_tls_session_create.</span></span>

<span data-ttu-id="7ddf6-547">nx_secure_tls_session_end에서 수행되는 것처럼 TLS 세션이 다시 설정될 때 원격 인증서 공간이 자동으로 복구되므로 대부분의 애플리케이션은 이 서비스를 호출할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-547">Note that the remote certificate space is recovered automatically when the TLS session is reset as happens in nx_secure_tls_session_end so most applications should not need to call this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-548">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-548">Parameters</span></span>

- <span data-ttu-id="7ddf6-549">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-549">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-550">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-550">Return Values</span></span>

- <span data-ttu-id="7ddf6-551">**NX_SUCCESS** (0x00) 작업에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-551">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="7ddf6-552">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-552">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7ddf6-553">**NX_INVALID_PARAMETERS**(0x4D) 내부 오류 – 인증서 저장소가 손상되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-553">**NX_INVALID_PARAMETERS** (0x4D) Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-554">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-554">Allowed From</span></span>

<span data-ttu-id="7ddf6-555">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-555">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-556">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-556">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-557">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-557">See Also</span></span>

- <span data-ttu-id="7ddf6-558">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-558">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-559">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-559">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-560">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-560">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-561">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7ddf6-561">nx_secure_tls_session_end</span></span>

## <a name="nx_secure_tls_server_certificate_add"></a><span data-ttu-id="7ddf6-562">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-562">nx_secure_tls_server_certificate_add</span></span>

<span data-ttu-id="7ddf6-563">숫자 식별자를 사용하여 TLS 서버 전용 인증서 추가</span><span class="sxs-lookup"><span data-stu-id="7ddf6-563">Add a certificate specifically for TLS servers using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-564">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-564">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="7ddf6-565">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-565">Description</span></span>

<span data-ttu-id="7ddf6-566">이 서비스는 인증서 내에서 X.509 주체(일반 이름)를 사용하여 저장소를 인덱싱하는 대신, 숫자 식별자를 사용하여 TLS 세션의 로컬 저장소에 인증서를 추가하는 데 사용됩니다(nx_secure_tls_local_certificate_add 참조).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-566">This service is used to add a certificate to a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span> <span data-ttu-id="7ddf6-567">숫자 식별자는 인증서와 별개이며 여러 인증서를 TLS 서버에 ID 인증서로 추가할 수 있으며 동일한 일반 이름을 가진 여러 인증서를 동일한 TLS 세션 로컬 저장소에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-567">The numeric identifier is separate from the certificate and allows multiple certificates to be added as identity certificates to a TLS server, as well as allowing multiple certificates with the same Common Name to be added to the same TLS session local store.</span></span> <span data-ttu-id="7ddf6-568">이러한 동일한 서비스를 클라이언트 인증서에 사용할 수 있지만 TLS 클라이언트에 여러 개의 ID 인증서가 있는 경우는 거의 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-568">This same service can be used for client certificates, but it is rare for a TLS client to have multiple identity certificates.</span></span>

<span data-ttu-id="7ddf6-569">cert_id 매개 변수는 애플리케이션에서 할당된 0이 아닌 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-569">The cert_id parameter is a non-zero positive integer assigned by the application.</span></span> <span data-ttu-id="7ddf6-570">실제 값은 중요하지 않지만(0이 아님) 제공된 TLS 세션의 저장소에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-570">The actual value does not matter (other than zero) but it must be unique in the store for the provided TLS session.</span></span> <span data-ttu-id="7ddf6-571">cert_id 값은 nx_secure_tls_server_certificate_find 및 nx_secure_tls_server_certificate_remove를 사용하여 로컬 저장소에서 인증서를 찾아 제거하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-571">The cert_id value can be used to find and remove certificates from the local store using nx_secure_tls_server_certificate_find and nx_secure_tls_server_certificate_remove, respectively.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddf6-572">nx_secure_tls_local_certificate_add를 사용하는 경우 이 API는 동일한 TLS 세션에서 사용하면 안 됩니다. nx_secure_tls_server_certificate_add API는 각 인증서에 고유한 숫자 식별자를 사용하고 X.509 일반 이름에 따라 로컬 인증서 서비스 인덱스를 사용합니다. 서버 인증서 서비스를 사용하면 공유 데이터(특히 일반 이름)가 포함된 여러 인증서가 동일한 로컬 저장소에 있을 수 있습니다. 이러한 특성은 여러 ID가 있는 서버에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-572">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-573">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-573">Parameters</span></span>

- <span data-ttu-id="7ddf6-574">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-574">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-575">**certificate** 이전에 초기화된 X.509 인증서 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-575">**certificate** Pointer to a previously initialized X.509 certificate instance.</span></span>
- <span data-ttu-id="7ddf6-576">**cert_id** 0이 아닌 양수로 나타낸 상대적으로 고유한 인증서 ID 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-576">**cert_id** Positive, non-zero, relatively unique certificate ID number.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-577">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-577">Return Values</span></span>

- <span data-ttu-id="7ddf6-578">**NX_SUCCESS**(0x00) 작업에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-578">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="7ddf6-579">**NX_PTR_ERROR**(0X07) 잘못된 TLS 세션 또는 인증서 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-579">**NX_PTR_ERROR** (0x07) Invalid TLS session orcertificate pointer.</span></span>
- <span data-ttu-id="7ddf6-580">**NX_SECURE_TLS_CERT_ID_INVALID**(0x138) 제공된 인증서 ID의 값(0일 수 있음)이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-580">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) The provided certificate ID had An invalid value (likely 0).</span></span>
- <span data-ttu-id="7ddf6-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE**(0x139) 제공된 인증서 ID가 로컬 저장소에 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) The provided certificate ID was already present in the local store.</span></span>
- <span data-ttu-id="7ddf6-582">**NX_INVALID_PARAMETERS(0x4D)** 내부 오류 – 인증서 저장소가 손상되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-582">**NX_INVALID_PARAMETERS(0x4D)** Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-583">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-583">Allowed From</span></span>

<span data-ttu-id="7ddf6-584">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-585">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-585">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-586">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-586">See Also</span></span>

- <span data-ttu-id="7ddf6-587">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-587">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-588">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-588">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="7ddf6-589">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-589">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="7ddf6-590">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-590">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="7ddf6-591">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-591">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_server_certificate_find"></a><span data-ttu-id="7ddf6-592">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-592">nx_secure_tls_server_certificate_find</span></span>

<span data-ttu-id="7ddf6-593">숫자 식별자를 사용하여 인증서 찾기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-593">Find a certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-594">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-594">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="7ddf6-595">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-595">Description</span></span>

<span data-ttu-id="7ddf6-596">이 서비스는 인증서 내에서 X.509 주체(일반 이름)를 사용하여 저장소를 인덱싱하는 대신, 숫자 식별자를 사용하여 TLS 세션의 로컬 저장소에서 인증서를 찾는 데 사용됩니다(nx_secure_tls_local_certificate_add 참조).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-596">This service is used to find a certificate in a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="7ddf6-597">cert_id 매개 변수는 nx_secure_tls_server_certificate_add를 사용하여 TLS 세션 로컬 저장소에 인증서를 추가할 때 애플리케이션에서 할당하는 0이 아닌 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-597">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddf6-598">nx_secure_tls_local_certificate_add를 사용하는 경우 이 API는 동일한 TLS 세션에서 사용하면 안 됩니다. nx_secure_tls_server_certificate_add API는 각 인증서에 고유한 숫자 식별자를 사용하고 X.509 일반 이름에 따라 로컬 인증서 서비스 인덱스를 사용합니다. 서버 인증서 서비스를 사용하면 공유 데이터(특히 일반 이름)가 포함된 여러 인증서가 동일한 로컬 저장소에 있을 수 있습니다. 이러한 특성은 여러 ID가 있는 서버에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-598">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-599">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-599">Parameters</span></span>

- <span data-ttu-id="7ddf6-600">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-600">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-601">**certificate** 찾은 인증서에 대한 참조를 반환하는 X.509 인증서 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-601">**certificate** Pointer to an X.509 certificate pointer to return a reference to the found certificate.</span></span>
- <span data-ttu-id="7ddf6-602">**cert_id** 0이 아닌 양의 인증서 ID 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-602">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-603">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-603">Return Values</span></span>

- <span data-ttu-id="7ddf6-604">**NX_SUCCESS**(0x00) 작업에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-604">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="7ddf6-605">**NX_PTR_ERROR**(0X07) 잘못된 TLS 세션 또는 인증서 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-605">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>
- <span data-ttu-id="7ddf6-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0x119) 제공된 인증서 ID가 제공된 TLS 세션의 로컬 저장소의 ID와 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-607">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-607">Allowed From</span></span>

<span data-ttu-id="7ddf6-608">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-608">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-609">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-609">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-610">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-610">See Also</span></span>

- <span data-ttu-id="7ddf6-611">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-611">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-612">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-612">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="7ddf6-613">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-613">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="7ddf6-614">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-614">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="7ddf6-615">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-615">nx_secure_tls_server_certificate_remove</span></span>

##  <a name="nx_secure_tls_server_certificate_remove"></a><span data-ttu-id="7ddf6-616">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-616">nx_secure_tls_server_certificate_remove</span></span>

<span data-ttu-id="7ddf6-617">숫자 식별자를 사용하여 로컬 서버 인증서 제거</span><span class="sxs-lookup"><span data-stu-id="7ddf6-617">Remove a local server certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-618">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-618">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="7ddf6-619">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-619">Description</span></span>

<span data-ttu-id="7ddf6-620">이 서비스는 인증서 내에서 X.509 주체(일반 이름)를 사용하여 저장소를 인덱싱하는 대신, 숫자 식별자를 사용하여 TLS 세션에서 저장소를 제거하는 데 사용됩니다(nx_secure_tls_local_certificate_add 참조).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-620">This service is used to remove a certificate from a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="7ddf6-621">cert_id 매개 변수는 nx_secure_tls_server_certificate_add를 사용하여 TLS 세션 로컬 저장소에 인증서를 추가할 때 애플리케이션에서 할당하는 0이 아닌 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-621">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-622">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-622">Parameters</span></span>

- <span data-ttu-id="7ddf6-623">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-623">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-624">**cert_id** 0이 아닌 양의 인증서 ID 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-624">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-625">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-625">Return Values</span></span>

- <span data-ttu-id="7ddf6-626">**NX_SUCCESS**(0x00) 작업에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-626">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="7ddf6-627">**NX_PTR_ERROR**(0x07) TLS 세션이 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-627">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>
- <span data-ttu-id="7ddf6-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0x119) 제공된 인증서 ID가 제공된 TLS 세션의 로컬 저장소의 ID와 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-629">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-629">Allowed From</span></span>

<span data-ttu-id="7ddf6-630">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-630">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-631">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-631">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-632">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-632">See Also</span></span>

- <span data-ttu-id="7ddf6-633">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-633">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-634">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-634">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="7ddf6-635">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-635">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="7ddf6-636">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-636">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="7ddf6-637">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-637">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_alert_value_get"></a><span data-ttu-id="7ddf6-638">nx_secure_tls_session_alert_value_get</span><span class="sxs-lookup"><span data-stu-id="7ddf6-638">nx_secure_tls_session_alert_value_get</span></span>

<span data-ttu-id="7ddf6-639">원격 호스트가 보낸 TLS 경고 값 및 수준 가져오기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-639">Get the TLS alert value and level sent by the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-640">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-640">Prototype</span></span>

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a><span data-ttu-id="7ddf6-641">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-641">Description</span></span>

<span data-ttu-id="7ddf6-642">이 서비스는 원격 호스트가 일부 문제나 오류에 대한 응답으로 경고를 보낼 때 TLS 경고 수준 및 값을 검색하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-642">This service is used to retrieve the TLS alert level and value when the remote host sends an alert in response to some problem or error.</span></span>

<span data-ttu-id="7ddf6-643">alert_level 및 alert_value 매개 변수의 값은 원격 호스트에서 경고가 수신되었음을 나타내는 NX_SECURE_TLS_ALERT_RECEIVED(0x114) 상태를 반환하는 TLS API 호출 바로 다음에 이 함수가 호출되는 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-643">The values of the alert_level and alert_value parameters are only valid if this function is called immediately following a TLS API call that returned a status of NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicating that an alert was received from the remote host.</span></span>

<span data-ttu-id="7ddf6-644">로컬 호스트 TLS에서 경고를 보내는 경우 반환되는 오류 코드는 TLS 경고 자체보다 실제 오류에 대한 설명을 포함합니다. 특정 유형의 공격을 방지하기 위해 TLS 경고 값은 의도적으로 모호하게 표시되기 때문입니다(예: "오라클 패딩" 공격 또는 유사한 공격).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-644">Note that if the local host TLS sends an alert, the returned error codes are far more descriptive of the actual error than the TLS alert itself because TLS alert values are intentionally left ambiguous to prevent certain types of attack (such as a "padding oracle" attack or similar).</span></span>

<span data-ttu-id="7ddf6-645">경고 수준에는 NX_SECURE_TLS_ALERT_LEVEL_WARNING(0x1) 또는 NX_SECURE_TLS_ALERT_LEVEL_FATAL(0x2)의 두 값 중 하나만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-645">The alert level only takes one of two values: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) or NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span></span> <span data-ttu-id="7ddf6-646">일반적으로 일부 확장 구성 상황도 경고로 간주될 수 있지만 CloseNotify 경고(TLS 세션의 성공적인 종료를 표시하는 데 사용됨)에만 "경고" 수준이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-646">In general, only the CloseNotify Alert (used to indicate a successful end to a TLS session) will be given a level of "Warning" though some extension configuration situations may also be considered warnings.</span></span> <span data-ttu-id="7ddf6-647">대부분의 경고는 잠재적인 보안 오류를 나타내는 "치명적"이며 TLS 연결(핸드셰이크 또는 세션)은 즉시 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-647">The vast majority of alerts will be "Fatal" indicating a potential security failure and resulting in immediate closure of the TLS connection (handshake or session).</span></span>

<span data-ttu-id="7ddf6-648">TLS 경고 값은 TLS RFC에 정의되어 있습니다. 다음은 참조용으로 제공되는 RFC 5246(TLSv 1.2)의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-648">The TLS alert values are defined in the TLS RFCs, here is the list from RFC 5246 (TLSv1.2) for reference:</span></span>

| <span data-ttu-id="7ddf6-649">경고 이름</span><span class="sxs-lookup"><span data-stu-id="7ddf6-649">Alert Name</span></span>                     | <span data-ttu-id="7ddf6-650">값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-650">Value</span></span> | <span data-ttu-id="7ddf6-651">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-651">Description</span></span>                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="7ddf6-652">close_notify</span><span class="sxs-lookup"><span data-stu-id="7ddf6-652">close_notify</span></span>                  | <span data-ttu-id="7ddf6-653">0</span><span class="sxs-lookup"><span data-stu-id="7ddf6-653">0</span></span>     | <span data-ttu-id="7ddf6-654">오류 없음, 성공한 세션 종료 표시</span><span class="sxs-lookup"><span data-stu-id="7ddf6-654">No error, indicates successful session end</span></span>                                                                                                                   |
| <span data-ttu-id="7ddf6-655">unexpected_message</span><span class="sxs-lookup"><span data-stu-id="7ddf6-655">unexpected_message</span></span>            | <span data-ttu-id="7ddf6-656">10</span><span class="sxs-lookup"><span data-stu-id="7ddf6-656">10</span></span>    | <span data-ttu-id="7ddf6-657">TLS에서 예기치 않았거나 순서가 잘못된 메시지를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-657">TLS received an unexpected or out-of-order message</span></span>                                                                                                           |
| <span data-ttu-id="7ddf6-658">bad_record_mac</span><span class="sxs-lookup"><span data-stu-id="7ddf6-658">bad_record_mac</span></span>               | <span data-ttu-id="7ddf6-659">20</span><span class="sxs-lookup"><span data-stu-id="7ddf6-659">20</span></span>    | <span data-ttu-id="7ddf6-660">암호 해독 및/또는 MAC 확인이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-660">Decryption and/or MAC verification failed</span></span>                                                                                                                    |
| <span data-ttu-id="7ddf6-661">decryption_failed_RESERVED</span><span class="sxs-lookup"><span data-stu-id="7ddf6-661">decryption_failed_RESERVED</span></span>   | <span data-ttu-id="7ddf6-662">21</span><span class="sxs-lookup"><span data-stu-id="7ddf6-662">21</span></span>    | <span data-ttu-id="7ddf6-663">**DEPRECATED** 암호 해독이 실패했습니다(오라클 패딩 공격으로 인해 더 이상 사용되지 않음).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-663">**DEPRECATED** Decryption failed (deprecated due to padding oracle attacks)</span></span>                                                                                      |
| <span data-ttu-id="7ddf6-664">record_overflow</span><span class="sxs-lookup"><span data-stu-id="7ddf6-664">record_overflow</span></span>               | <span data-ttu-id="7ddf6-665">22</span><span class="sxs-lookup"><span data-stu-id="7ddf6-665">22</span></span>    | <span data-ttu-id="7ddf6-666">TLS 최대 레코드 크기보다 큰 레코드를 수신했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-666">A record was received that is larger than the TLS maximum record size</span></span>                                                                                        |
| <span data-ttu-id="7ddf6-667">decompression_failure</span><span class="sxs-lookup"><span data-stu-id="7ddf6-667">decompression_failure</span></span>         | <span data-ttu-id="7ddf6-668">30</span><span class="sxs-lookup"><span data-stu-id="7ddf6-668">30</span></span>    | <span data-ttu-id="7ddf6-669">TLS 레코드 압축/압축 해제에서 문제가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-669">A problem was encountered in compression/decompression of a TLS record</span></span>                                                                                       |
| <span data-ttu-id="7ddf6-670">handshake_failure</span><span class="sxs-lookup"><span data-stu-id="7ddf6-670">handshake_failure</span></span>             | <span data-ttu-id="7ddf6-671">40</span><span class="sxs-lookup"><span data-stu-id="7ddf6-671">40</span></span>    | <span data-ttu-id="7ddf6-672">다른 경고에 해당되지 않는 일부 지정되지 않은 핸드셰이크 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-672">Some unspecified handshake error occurred that isn't covered by a different alert</span></span>                                                                            |
| <span data-ttu-id="7ddf6-673">no_certificate_RESERVED</span><span class="sxs-lookup"><span data-stu-id="7ddf6-673">no_certificate_RESERVED</span></span>      | <span data-ttu-id="7ddf6-674">41</span><span class="sxs-lookup"><span data-stu-id="7ddf6-674">41</span></span>    | <span data-ttu-id="7ddf6-675">TLS에서 **더 이상 사용되지 않습니다**(SSL만 해당).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-675">**DEPRECATED** in TLS (SSL only)</span></span>                                                                                                                                 |
| <span data-ttu-id="7ddf6-676">bad_certificate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-676">bad_certificate</span></span>               | <span data-ttu-id="7ddf6-677">42</span><span class="sxs-lookup"><span data-stu-id="7ddf6-677">42</span></span>    | <span data-ttu-id="7ddf6-678">받은 인증서에 잘못된 서식 또는 서명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-678">A certificate that was received contained invalid formatting or signatures</span></span>                                                                                   |
| <span data-ttu-id="7ddf6-679">unsupported_certificate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-679">unsupported_certificate</span></span>       | <span data-ttu-id="7ddf6-680">43</span><span class="sxs-lookup"><span data-stu-id="7ddf6-680">43</span></span>    | <span data-ttu-id="7ddf6-681">잘못된 형식의 인증서를 받았습니다(예: TLS 서버 인증에 사용되는 서명 전용 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-681">A certificate was received that was of an invalid type (e.g. signing-only certificate used for TLS server authentication)</span></span>                                    |
| <span data-ttu-id="7ddf6-682">certificate_revoked</span><span class="sxs-lookup"><span data-stu-id="7ddf6-682">certificate_revoked</span></span>           | <span data-ttu-id="7ddf6-683">44</span><span class="sxs-lookup"><span data-stu-id="7ddf6-683">44</span></span>    | <span data-ttu-id="7ddf6-684">CRL 또는 OCSP에서 제공한 인증서 상태가 "해지됨"으로 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-684">The certificate status (as provided by a CRL or OCSP) was indicated as being "revoked"</span></span>                                                                       |
| <span data-ttu-id="7ddf6-685">certificate_expired</span><span class="sxs-lookup"><span data-stu-id="7ddf6-685">certificate_expired</span></span>           | <span data-ttu-id="7ddf6-686">45</span><span class="sxs-lookup"><span data-stu-id="7ddf6-686">45</span></span>    | <span data-ttu-id="7ddf6-687">받은 인증서가 유효한 날짜 범위를 벗어났습니다(유효하지 않거나 만료됨).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-687">The received certificate was outside it's valid date range (either not valid yet or expired)</span></span>                                                                 |
| <span data-ttu-id="7ddf6-688">certificate_unknown</span><span class="sxs-lookup"><span data-stu-id="7ddf6-688">certificate_unknown</span></span>           | <span data-ttu-id="7ddf6-689">46</span><span class="sxs-lookup"><span data-stu-id="7ddf6-689">46</span></span>    | <span data-ttu-id="7ddf6-690">다른 경고에 해당되지 않는 일부 알 수 없는 인증서 문제가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-690">Some unknown certificate issue was encountered that was not covered by other alerts</span></span>                                                                          |
| <span data-ttu-id="7ddf6-691">illegal_parameter</span><span class="sxs-lookup"><span data-stu-id="7ddf6-691">illegal_parameter</span></span>             | <span data-ttu-id="7ddf6-692">47</span><span class="sxs-lookup"><span data-stu-id="7ddf6-692">47</span></span>    | <span data-ttu-id="7ddf6-693">TLS 핸드셰이크의 일부 구성 또는 협상된 값이 잘못되었거나 범위를 벗어났습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-693">Some configuration or negotiated value in the TLS handshake was invalid or out of range</span></span>                                                                      |
| <span data-ttu-id="7ddf6-694">unknown_ca</span><span class="sxs-lookup"><span data-stu-id="7ddf6-694">unknown_ca</span></span>                    | <span data-ttu-id="7ddf6-695">48</span><span class="sxs-lookup"><span data-stu-id="7ddf6-695">48</span></span>    | <span data-ttu-id="7ddf6-696">받은 ID 인증서를 신뢰할 수 있는 루트 CA 인증서에 대한 인증서 체인을 통해 추적할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-696">The received identity certificate could not be traced via a certificate chain to a trusted root CA certificate.</span></span>                                              |
| <span data-ttu-id="7ddf6-697">access_denied</span><span class="sxs-lookup"><span data-stu-id="7ddf6-697">access_denied</span></span>                 | <span data-ttu-id="7ddf6-698">49</span><span class="sxs-lookup"><span data-stu-id="7ddf6-698">49</span></span>    | <span data-ttu-id="7ddf6-699">유효한 인증서를 받았지만 애플리케이션 액세스 제어에서 인증서가 요청된 리소스에 대해 유효하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-699">Indicates a valid certificate was received but application access control indicated that the certificate was invalid for the requested resources.</span></span>            |
| <span data-ttu-id="7ddf6-700">decode_error</span><span class="sxs-lookup"><span data-stu-id="7ddf6-700">decode_error</span></span>                  | <span data-ttu-id="7ddf6-701">50</span><span class="sxs-lookup"><span data-stu-id="7ddf6-701">50</span></span>    | <span data-ttu-id="7ddf6-702">TLS 헤더 또는 핸드셰이크 메시지의 일부 필드 또는 값이 범위를 벗어났거나 올바르지 않으므로 TLS 레코드를 디코딩하는 데 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-702">Some field or value in a TLS header or handshake message was out of range or invalid, leading to a failure in decoding of a TLS record.</span></span>                      |
| <span data-ttu-id="7ddf6-703">decrypt_error</span><span class="sxs-lookup"><span data-stu-id="7ddf6-703">decrypt_error</span></span>                 | <span data-ttu-id="7ddf6-704">51</span><span class="sxs-lookup"><span data-stu-id="7ddf6-704">51</span></span>    | <span data-ttu-id="7ddf6-705">TLS 핸드셰이크 중에 서명 또는 완료된 메시지 해시를 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-705">A signature or Finished message hash during the TLS handshake could not be verified.</span></span>                                                                         |
| <span data-ttu-id="7ddf6-706">export_restriction_RESERVED</span><span class="sxs-lookup"><span data-stu-id="7ddf6-706">export_restriction_RESERVED</span></span>  | <span data-ttu-id="7ddf6-707">60</span><span class="sxs-lookup"><span data-stu-id="7ddf6-707">60</span></span>    | <span data-ttu-id="7ddf6-708">TLSv 1.2에서 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-708">DEPRECATED in TLSv1.2</span></span>                                                                                                                                        |
| <span data-ttu-id="7ddf6-709">protocol_version</span><span class="sxs-lookup"><span data-stu-id="7ddf6-709">protocol_version</span></span>              | <span data-ttu-id="7ddf6-710">70</span><span class="sxs-lookup"><span data-stu-id="7ddf6-710">70</span></span>    | <span data-ttu-id="7ddf6-711">핸드셰이크 동안 협상된 TLS 프로토콜 버전이 인식되지만 지원되지 않습니다(예: TLSv 1.0이 제공되었지만 사용하도록 설정되지 않음).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-711">The TLS protocol version negotiated during the handshake is recognized but not supported (e.g. TLSv1.0 was presented but not enabled).</span></span>                       |
| <span data-ttu-id="7ddf6-712">insufficient_security</span><span class="sxs-lookup"><span data-stu-id="7ddf6-712">insufficient_security</span></span>         | <span data-ttu-id="7ddf6-713">71</span><span class="sxs-lookup"><span data-stu-id="7ddf6-713">71</span></span>    | <span data-ttu-id="7ddf6-714">보안 암호화가 부족하여 핸드셰이크가 실패할 때마다 전송됩니다(예: 애플리케이션 요구 사항에 비해 키 크기가 너무 작음).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-714">Sent whenever a handshake fails due to a lack of secure ciphers (e.g. key size is too small for the application requirements)</span></span>                                |
| <span data-ttu-id="7ddf6-715">internal_error</span><span class="sxs-lookup"><span data-stu-id="7ddf6-715">internal_error</span></span>                | <span data-ttu-id="7ddf6-716">80</span><span class="sxs-lookup"><span data-stu-id="7ddf6-716">80</span></span>    | <span data-ttu-id="7ddf6-717">일부 TLS 이외의 오류(예: 메모리 할당 문제, 애플리케이션 문제)가 발생하여 TLS 세션이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-717">Some non-TLS error (e.g. memory allocation problems, application issues) occurred resulting in a broken TLS session.</span></span>                                         |
| <span data-ttu-id="7ddf6-718">user_canceled</span><span class="sxs-lookup"><span data-stu-id="7ddf6-718">user_canceled</span></span>                 | <span data-ttu-id="7ddf6-719">90</span><span class="sxs-lookup"><span data-stu-id="7ddf6-719">90</span></span>    | <span data-ttu-id="7ddf6-720">핸드셰이크가 완료되기 전에 사용자 또는 애플리케이션이 TLS 세션을 취소하는 경우 반환됩니다(CloseNotify와 유사).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-720">Returned if the TLS session is cancelled by a user or application before the handshake is complete (similar to CloseNotify).</span></span>                                 |
| <span data-ttu-id="7ddf6-721">no_renegotiation</span><span class="sxs-lookup"><span data-stu-id="7ddf6-721">no_renegotiation</span></span>              | <span data-ttu-id="7ddf6-722">100</span><span class="sxs-lookup"><span data-stu-id="7ddf6-722">100</span></span>   | <span data-ttu-id="7ddf6-723">원격 호스트가 재협상 요청에 대한 응답으로 TLS 재협상 핸드셰이크를 수행하지 않을 것임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-723">Indiates that the remote host is not willing to perform TLS renegotiation handshakes in response to a renegotiation request.</span></span>                                 |
| <span data-ttu-id="7ddf6-724">unsupported_extension</span><span class="sxs-lookup"><span data-stu-id="7ddf6-724">unsupported_extension</span></span>         | <span data-ttu-id="7ddf6-725">110</span><span class="sxs-lookup"><span data-stu-id="7ddf6-725">110</span></span>   | <span data-ttu-id="7ddf6-726">TLS 클라이언트가 초기 ClientHello에서 명시적으로 요청하지 않은 확장을 포함하는 ServerHello를 수신하는 경우 전송됩니다(서버에 문제가 있음을 나타냄).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-726">Sent if a TLS Client receives a ServerHello containing extensions not explicitly asked for in the initial ClientHello (indicating the server has a problem).</span></span> |

### <a name="parameters"></a><span data-ttu-id="7ddf6-727">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-727">Parameters</span></span>

- <span data-ttu-id="7ddf6-728">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-728">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-729">**alert_level** 받은 경고의 수준(경고 또는 치명적)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-729">**alert_level** Return the level of the received alert (warning or fatal).</span></span>
- <span data-ttu-id="7ddf6-730">**alert_value** 받은 경고의 값을 반환합니다(표 참조).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-730">**alert_value** Return the value of the received alert (see table).</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-731">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-731">Return Values</span></span>

- <span data-ttu-id="7ddf6-732">**NX_SUCCESS** (0x00) 작업에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-732">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="7ddf6-733">**NX_PTR_ERROR**(0x07) TLS 세션이 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-733">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-734">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-734">Allowed From</span></span>

<span data-ttu-id="7ddf6-735">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-736">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-736">Example</span></span>

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-737">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-737">See Also</span></span>

- <span data-ttu-id="7ddf6-738">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-738">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-739">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-739">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7ddf6-740">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-740">nx_secure_tls_session_receive</span></span>

## <a name="nx_secure_tls_session_certificate_callback_set"></a><span data-ttu-id="7ddf6-741">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-741">nx_secure_tls_session_certificate_callback_set</span></span>

<span data-ttu-id="7ddf6-742">추가 인증서 유효성 검사에 사용할 TLS에 대한 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-742">Set up a callback for TLS to use for additional certificate validation</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-743">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-743">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a><span data-ttu-id="7ddf6-744">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-744">Description</span></span>

<span data-ttu-id="7ddf6-745">이 서비스는 원격 호스트에서 인증서를 받을 때 TLS에서 호출하는 TLS 세션에 함수 포인터를 할당하여 애플리케이션에서 DNS 유효성 검사, 인증서 해지, 인증서 정책 적용 등의 유효성 검사를 수행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-745">This service assigns a function pointer to a TLS session that TLS will invoke when a certificate is received from a remote host, allowing the application to perform validation checks such as DNS validation, certificate revocation, and certificate policy enforcement.</span></span>

<span data-ttu-id="7ddf6-746">NetX Secure TLS는 콜백을 호출하기 전에 인증서에 대해 기본 X.509 경로 유효성 검사를 수행하여 인증서를 TLS에서 신뢰할 수 있는 인증서 저장소의 인증서로 추적할 수 있도록 하지만 다른 모든 유효성 검사는 이 콜백에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-746">NetX Secure TLS will perform basic X.509 path validation on the certificate before invoking the callback to assure that the certificate can be traced to a certificate in the TLS trusted certificate store, but all other validation will be handled by this callback.</span></span>

<span data-ttu-id="7ddf6-747">콜백은 TLS 세션 포인터와 원격 호스트 ID 인증서에 대한 포인터(인증서 체인의 리프)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-747">The callback provides the TLS session pointer and a pointer to the remote host identity certificate (the leaf in the certificate chain).</span></span> <span data-ttu-id="7ddf6-748">모든 유효성 검사가 성공하면 콜백이 NX_SUCCESS을 반환합니다. 그렇지 않으면 유효성 검사 오류를 나타내는 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-748">The callback should return NX_SUCCESS if all validation is successful, otherwise it should return an error code indicating the validation failure.</span></span> <span data-ttu-id="7ddf6-749">NX_SUCCESS 이외의 값을 지정하면 TLS 핸드셰이크가 즉시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-749">Any value other than NX_SUCCESS will cause the TLS handshake to immediately abort.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-750">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-750">Parameters</span></span>

- <span data-ttu-id="7ddf6-751">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-751">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-752">**func_ptr** 인증서 유효성 검사 콜백 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-752">**func_ptr** Pointer to the certificate validation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-753">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-753">Return Values</span></span>

- <span data-ttu-id="7ddf6-754">**NX_SUCCESS**(0X00) 함수 포인터를 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-754">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="7ddf6-755">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-755">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-756">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-756">Allowed From</span></span>

<span data-ttu-id="7ddf6-757">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-757">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-758">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-758">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-759">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-759">See Also</span></span>

- <span data-ttu-id="7ddf6-760">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-760">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-761">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-761">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="7ddf6-762">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-762">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_tls_session_client_callback_set"></a><span data-ttu-id="7ddf6-763">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-763">nx_secure_tls_session_client_callback_set</span></span>

<span data-ttu-id="7ddf6-764">TlS가 TLS 클라이언트 핸드셰이크 시작 시 호출할 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-764">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-765">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-765">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="7ddf6-766">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-766">Description</span></span>

<span data-ttu-id="7ddf6-767">이 서비스는 TLS 클라이언트 핸드셰이크가 ServerHelloDone 메시지를 받았을 때 TLS에서 호출하는 TLS 세션에 함수 포인터를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-767">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Client handshake has received a ServerHelloDone message.</span></span> <span data-ttu-id="7ddf6-768">콜백 함수를 사용하면 애플리케이션은 수신된 ServerHello 메시지에서 입력 또는 의사 결정이 필요한 모든 TLS 확장을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-768">The callback function allows an application to process any TLS extensions from the received ServerHello message that require input or decision making.</span></span>

<span data-ttu-id="7ddf6-769">호출하는 TLS 세션 제어 블록과 NX_SECURE_TLS_HELLO_EXTENSION 개체의 배열로 콜백이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-769">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="7ddf6-770">확장 개체의 배열은 특정 확장을 찾아서 구문 분석하는 도우미 함수에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-770">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="7ddf6-771">현재 NetX Secure에서는 TLS 클라이언트 입력이 필요한 특정 확장이 지원되지 않지만 애플리케이션 디자이너에서 사용자 지정 또는 새 확장을 처리하기 위해 콜백을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-771">Currently, there are no specific extensions supported in NetX Secure that require TLS Client input, but the callback is available for application designers to handle custom or new extensions that may become available.</span></span> <span data-ttu-id="7ddf6-772">Hello 메시지에 제공된 TLS 확장을 구문 분석하는 도우미 함수 예제는 *nx_secure_tls_session_sni_extension_parse* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-772">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="7ddf6-773">또한 원격 서버에서 인증서를 요청했으며 TLS 클라이언트에서 특정 인증서를 선택할 수 있도록 하기 위한 정보를 제공한 경우, TLS 클라이언트에 대해 *nx_secure_tls_active_certificate_set* 를 사용하여 활성 ID 인증서를 선택하는 데 클라이언트 콜백을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-773">The client callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Client in the event that the remote server has requested a certificate and provided information to allow the TLS Client to select a specific certificate.</span></span> <span data-ttu-id="7ddf6-774">자세한 내용은 nx_secure_tls_active_certificate_set에 대한 참조를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-774">See the reference for nx_secure_tls_active_certificate_set for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-775">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-775">Parameters</span></span>

- <span data-ttu-id="7ddf6-776">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-776">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-777">**func_ptr** TLS 클라이언트 콜백 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-777">**func_ptr** Pointer to the TLS Client callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-778">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-778">Return Values</span></span>

- <span data-ttu-id="7ddf6-779">**NX_SUCCESS**(0X00) 함수 포인터를 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-779">**NX_SUCCESS** (0x00) Successful allocation of function pointer.</span></span>
- <span data-ttu-id="7ddf6-780">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-780">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-781">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-781">Allowed From</span></span>

<span data-ttu-id="7ddf6-782">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-782">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-783">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-783">Example</span></span>

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-784">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-784">See Also</span></span>

- <span data-ttu-id="7ddf6-785">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-785">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-786">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-786">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="7ddf6-787">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-787">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a><span data-ttu-id="7ddf6-788">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="7ddf6-788">nx_secure_tls_session_x509_client_verify_configure</span></span>

<span data-ttu-id="7ddf6-789">클라이언트 X.509 확인을 사용하도록 설정하고 클라이언트 인증서에 대해 공간 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-789">Enable client X.509 verification and allocate space for client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-790">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-790">Prototype</span></span>

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="7ddf6-791">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-791">Description</span></span>

<span data-ttu-id="7ddf6-792">이 서비스는 TLS 서버 인스턴스에 대한 선택적 X.509 클라이언트 인증을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-792">This service enables the optional X.509 Client Authentication for a TLS Server instance.</span></span> <span data-ttu-id="7ddf6-793">또한 원격 클라이언트 호스트에서 들어오는 인증서 체인을 처리하는 데 필요한 공간도 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-793">It also allocates the space needed to process incoming certificate chains from the remote client host.</span></span> <span data-ttu-id="7ddf6-794">원격 클라이언트에서 제공하는 인증서는 서비스 nx_secure_tls_trusted_certificate_add를 통해 할당된 TLS 서버 인스턴스의 신뢰할 수 있는 인증서를 기준으로 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-794">The certificates supplied by the remote client will be verified against the TLS server instance's trusted certificates, assigned with the service *nx_secure_tls_trusted_certificate_add.*</span></span>

<span data-ttu-id="7ddf6-795">TLS 클라이언트 모드의 경우 원격 인증서 할당이 필요하며, 대신 서비스 nx_secure_tls_remote_certificate_buffer_allocate를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-795">For TLS Client mode, remote certificate allocation is required and the service *nx_secure_tls_remote_certificate_buffer_allocate* should be used instead.</span></span> <span data-ttu-id="7ddf6-796">TLS 클라이언트 인스턴스에서 X.509 클라이언트 인증을 사용하도록 설정해도 아무런 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-796">Enabling X.509 Client Authentication on a TLS Client instance will have no effect.</span></span>

<span data-ttu-id="7ddf6-797">certificate_buffer 매개 변수는 수신 원격 인증서 및 해당 인증서에 필요한 제어 블록을 저장하기 위해 할당된 공간을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-797">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="7ddf6-798">버퍼는 각 인증서에 지정된 것과 같은 부분이 있는 인증서 수(certs_number)로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-798">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="7ddf6-799">buffer_size 매개 변수는 버퍼의 크기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-799">The *buffer_size* parameter indicates the size of the buffer.</span></span> <span data-ttu-id="7ddf6-800">필요한 공간은 다음 수식을 사용하여 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-800">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="7ddf6-801">서명에 대해 SHA-256을 사용하는 2048비트의 RSA 키를 포함하는 일반적인 인증서의 범위는 1000-2000바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-801">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="7ddf6-802">버퍼는 적어도 각 인증서에 대한 해당 크기를 보유할 수 있을 만큼 커야 하지만 원격 호스트 인증서에 따라 훨씬 더 작거나 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-802">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="7ddf6-803">버퍼가 너무 작아서 수신 인증서를 저장할 수 없는 경우 TLS 핸드셰이크는 오류를 발생하면서 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-803">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-804">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-804">Parameters</span></span>

- <span data-ttu-id="7ddf6-805">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-805">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-806">**certs_number** 제공된 버퍼에서 할당할 인증서의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-806">**certs_number** Number of certificates to allocate from the provided buffer.</span></span>
- <span data-ttu-id="7ddf6-807">**certificate_buffer** 원격 호스트에서 받은 인증서를 저장할 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-807">**certificate_buffer** Pointer to a buffer to hold certificates received from a remote host.</span></span>
- <span data-ttu-id="7ddf6-808">**buffer_size** 인증서 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-808">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-809">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-809">Return Values</span></span>

- <span data-ttu-id="7ddf6-810">**NX_SUCCESS**(0x00) 인증서를 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-810">**NX_SUCCESS** (0x00)Successful allocation of certificate.</span></span>
- <span data-ttu-id="7ddf6-811">**NX_PTR_ERROR**(0x07) TLS 세션 또는 버퍼 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-811">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="7ddf6-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**(0x12D) 제공된 버퍼가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="7ddf6-813">**NX_INVALID_PARAMETERS**(0x4D) 버퍼가 너무 작아서 원하는 수의 인증서를 보유할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-813">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-814">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-814">Allowed From</span></span>

<span data-ttu-id="7ddf6-815">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-815">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-816">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-816">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-817">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-817">See Also</span></span>

- <span data-ttu-id="7ddf6-818">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-818">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-819">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-819">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-820">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-820">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

## <a name="nx_secure_tls_session_client_verify_disable"></a><span data-ttu-id="7ddf6-821">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="7ddf6-821">nx_secure_tls_session_client_verify_disable</span></span>

<span data-ttu-id="7ddf6-822">NetX Secure TLS 세션에 대해 클라이언트 인증서 인증를 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-822">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-823">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-823">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7ddf6-824">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-824">Description</span></span>

<span data-ttu-id="7ddf6-825">이 서비스는 특정 TLS 세션에 대해 클라이언트 인증서 인증을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-825">This service disables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="7ddf6-826">자세한 내용은 nx_secure_tls_session_client_verify_enable을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-826">See nx_secure_tls_session_client_verify_enable for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-827">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-827">Parameters</span></span>

- <span data-ttu-id="7ddf6-828">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-828">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-829">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-829">Return Values</span></span>

- <span data-ttu-id="7ddf6-830">**NX_SUCCESS** (0x00) 상태 변경에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-830">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="7ddf6-831">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-831">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-832">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-832">Allowed From</span></span>

<span data-ttu-id="7ddf6-833">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-834">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-834">Example</span></span>

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-835">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-835">See Also</span></span>

- <span data-ttu-id="7ddf6-836">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="7ddf6-836">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="7ddf6-837">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-837">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-838">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-838">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_client_verify_enable"></a><span data-ttu-id="7ddf6-839">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="7ddf6-839">nx_secure_tls_session_client_verify_enable</span></span>

<span data-ttu-id="7ddf6-840">NetX Secure TLS 세션에 대해 클라이언트 인증서 인증를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-840">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-841">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-841">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7ddf6-842">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-842">Description</span></span>

<span data-ttu-id="7ddf6-843">이 서비스는 특정 TLS 세션에 대해 클라이언트 인증서 인증을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-843">This service enables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="7ddf6-844">TLS 서버 인스턴스에 대해 클라이언트 인증서 인증을 사용하도록 설정하면 초기 TLS 핸드셰이크 중에 TLS 서버는 원격 TLS 클라이언트의 인증서를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-844">Enabling Client Certificate Authentication for a TLS Server instance will cause the TLS Server to request a certificate from any remote TLS Client during the initial TLS handshake.</span></span> <span data-ttu-id="7ddf6-845">원격 TLS 클라이언트에서 받은 인증서는 클라이언트가 인증서를 소유하고 있는지(해당 인증서와 연결된 프라이빗 키에 대해 액세스 권한이 있음) 확인하기 위해 TLS 서버에서 사용하는 CertificateVerify 메시지와 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-845">The certificate received from the remote TLS Client is accompanied by a CertificateVerify message, which the TLS Server uses to verify that the Client owns the certificate (has access to the private key associated with that certificate).</span></span>

<span data-ttu-id="7ddf6-846">제공된 인증서를 확인하고 X.509 인증서 체인을 통해 TLS 서버의 신뢰할 수 있는 인증서 저장소에 있는 인증서로 다시 추적할 수 있으면 원격 TLS 클라이언트가 인증되고 핸드셰이크가 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-846">If the provided certificate can be verified and traced back to a certificate in the TLS Server trusted certificate store via an X.509 certificate chain, the remote TLS Client is authenticated and the handshake proceeds.</span></span> <span data-ttu-id="7ddf6-847">인증서 또는 CertificateVerify 메시지를 처리하는 동안 오류가 발생하는 경우 TLS 핸드셰이크는 오류와 함께 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-847">In case of any errors in processing the certificate or CertificateVerify message, the TLS handshake ends with an error.</span></span>

> [!NOTE]
> <span data-ttu-id="7ddf6-848">*TLS 서버의 신뢰할 수 있는 저장소에 있는 하나 이상의 인증서가 nx_secure_tls_trusted_certificate_add를 통해 추가되어야 하며 그렇지 않으면 인증이 항상 실패합니다.*</span><span class="sxs-lookup"><span data-stu-id="7ddf6-848">*The TLS Server must have at least one certificate in its trusted store added with nx_secure_tls_trusted_certificate_add or authentication will always fail.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-849">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-849">Parameters</span></span>

- <span data-ttu-id="7ddf6-850">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-850">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-851">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-851">Return Values</span></span>

- <span data-ttu-id="7ddf6-852">**NX_SUCCESS** (0x00) 상태 변경에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-852">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="7ddf6-853">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-853">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-854">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-854">Allowed From</span></span>

<span data-ttu-id="7ddf6-855">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-855">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-856">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-856">Example</span></span>

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-857">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-857">See Also</span></span>

- <span data-ttu-id="7ddf6-858">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="7ddf6-858">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="7ddf6-859">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-859">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-860">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-860">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-861">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-861">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_tls_session_create"></a><span data-ttu-id="7ddf6-862">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-862">nx_secure_tls_session_create</span></span>

<span data-ttu-id="7ddf6-863">보안 통신용 NetX Secure TLS 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-863">Create a NetX Secure TLS Session for secure communications</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-864">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-864">Prototype</span></span>

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a><span data-ttu-id="7ddf6-865">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-865">Description</span></span>

<span data-ttu-id="7ddf6-866">이 서비스는 네트워크 연결을 통해 보안 TLS 통신을 설정하는 데 사용할 NX_SECURE_TLS_SESSION 구조체 인스턴스를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-866">This service initializes an NX_SECURE_TLS_SESSION structure instance for use in establishing secure TLS communications over a network connection.</span></span>

<span data-ttu-id="7ddf6-867">이 메서드는 TLS에 사용할 수 있는 암호화 메서드로 채워지는 NX_SECURE_TLS_CRYPTO 개체를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-867">The method takes a NX_SECURE_TLS_CRYPTO object that is populated with the available cryptographic methods to be used for TLS.</span></span> <span data-ttu-id="7ddf6-868">*encryption_metadata_area* 는 TLS가 NX_SECURE_TLS_CRYPTO 테이블의 암호화 메서드가 계산에 사용하는 "메타데이터"를 저장하기 위해 사용하도록 할당된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-868">The *encryption_metadata_area* points to a buffer allocated for use by TLS for the "metadata" used by the cryptographic methods in the NX_SECURE_TLS_CRYPTO table for calculations.</span></span> <span data-ttu-id="7ddf6-869">테이블 크기는 nx_secure_tls_metadata_size_calculate 서비스를 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-869">The size of the table can be determined by using the nx_secure_tls_metadata_size_calculate service.</span></span> <span data-ttu-id="7ddf6-870">자세한 내용은 3장에서 "NetX Secure TLS의 암호화" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-870">See the section "Cryptography in NetX Secure TLS" in Chapter 3 for more details.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-871">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-871">Parameters</span></span>

- <span data-ttu-id="7ddf6-872">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-872">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-873">**cipher_table** TLS 암호화 메서드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-873">**cipher_table** Pointer to TLS cryptographic methods.</span></span>
- <span data-ttu-id="7ddf6-874">**encryption_metadata_area** 암호화 메타데이터 공간에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-874">**encryption_metadata_area** Pointer to space for cryptography metadata.</span></span>
- <span data-ttu-id="7ddf6-875">**encryption_metadata_size** 메타데이터 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-875">**encryption_metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-876">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-876">Return Values</span></span>

- <span data-ttu-id="7ddf6-877">**NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-877">**NX_SUCCESS** (0x00)Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7ddf6-878">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-878">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="7ddf6-879">**NX_INVALID_PARAMETERS**(0x4D) 지정된 메서드에 비해 메타데이터 버퍼가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-879">**NX_INVALID_PARAMETERS** (0x4D) The metadata buffer was too small for the given methods.</span></span>
- <span data-ttu-id="7ddf6-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER**(0x106) 사용하도록 설정된 TLS 버전에 필요한 암호화 메서드가 암호화 테이블에 제공되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A required cipher method for the enabled version of TLS was not supplied in the cipher table.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-881">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-881">Allowed From</span></span>

<span data-ttu-id="7ddf6-882">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-882">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-883">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-883">Example</span></span>

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-884">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-884">See Also</span></span>

- <span data-ttu-id="7ddf6-885">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-885">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-886">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-886">nx_secure_tls_metadata_size_calculate</span></span>
- <span data-ttu-id="7ddf6-887">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-887">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-888">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-888">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-889">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7ddf6-889">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7ddf6-890">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-890">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7ddf6-891">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-891">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7ddf6-892">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-892">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7ddf6-893">3장에서 NetX Secure TLS의 암호화</span><span class="sxs-lookup"><span data-stu-id="7ddf6-893">Cryptography in NetX Secure TLS in Chapter 3</span></span>

## <a name="nx_secure_tls_session_delete"></a><span data-ttu-id="7ddf6-894">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-894">nx_secure_tls_session_delete</span></span>

<span data-ttu-id="7ddf6-895">NetX Secure TLS 세션 삭제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-895">Delete a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-896">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-896">Prototype</span></span>

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7ddf6-897">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-897">Description</span></span>

<span data-ttu-id="7ddf6-898">이 서비스는 NX_SECURE_TLS_SESSION 구조체 인스턴스로 표시되는 TLS 세션을 삭제하고 해당 세션 인스턴스가 소유하는 모든 시스템 리소스를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-898">This service deletes a TLS session represented by an NX_SECURE_TLS_SESSION structure instance and releases all system resources owned by that session instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-899">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-899">Parameters</span></span>

- <span data-ttu-id="7ddf6-900">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-900">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-901">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-901">Return Values</span></span>

- <span data-ttu-id="7ddf6-902">**NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-902">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7ddf6-903">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-903">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-904">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-904">Allowed From</span></span>

<span data-ttu-id="7ddf6-905">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-905">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-906">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-906">Example</span></span>

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-907">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-907">See Also</span></span>

- <span data-ttu-id="7ddf6-908">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-908">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-909">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-909">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-910">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-910">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-911">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7ddf6-911">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7ddf6-912">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-912">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7ddf6-913">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-913">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7ddf6-914">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-914">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_end"></a><span data-ttu-id="7ddf6-915">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7ddf6-915">nx_secure_tls_session_end</span></span>

<span data-ttu-id="7ddf6-916">활성 NetX Secure TLS 세션 종료</span><span class="sxs-lookup"><span data-stu-id="7ddf6-916">End an active NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-917">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-917">Prototype</span></span>

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7ddf6-918">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-918">Description</span></span>

<span data-ttu-id="7ddf6-919">이 서비스는 TLS CloseNotify 메시지를 원격 호스트로 보내 NX_SECURE_TLS_SESSION 구조체 인스턴스로 표시되는 TLS 세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-919">This service ends a TLS session represented by an NX_SECURE_TLS_SESSION structure instance by sending the TLS CloseNotify message to the remote host.</span></span> <span data-ttu-id="7ddf6-920">그런 다음, 서비스는 원격 호스트가 자체 CloseNotify 메시지에 응답할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-920">The service then waits for the remote host to respond with its own CloseNotify message.</span></span>

<span data-ttu-id="7ddf6-921">원격 호스트에서 CloseNotify 메시지를 보내지 않는 경우 TLS는 이 오류와 가능한 보안 위반을 고려하므로 보안 연결을 위해서는 반환 값을 확인하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-921">If the remote host does not send a CloseNotify message, TLS considers this an error and a possible security breach, so checking the return value is important for a secure connection.</span></span> <span data-ttu-id="7ddf6-922">**wait_option** 매개 변수를 사용하여 서비스에서 호출 스레드에 제어를 반환하기 전에 응답을 기다리는 시간을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-922">The **wait_option** parameter can be used to control how long the service should wait for the response before returning control to the calling thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-923">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-923">Parameters</span></span>

- <span data-ttu-id="7ddf6-924">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-924">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-925">**wait_option** 서비스가 원격 호스트의 응답을 기다리는 기간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-925">**wait_option** Indicates how long the service should wait for the response from the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-926">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-926">Return Values</span></span>

- <span data-ttu-id="7ddf6-927">**NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-927">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7ddf6-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE**(0x113) 제한 시간을 초과하기 전에 원격 호스트에서 응답을 받지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Did not receive a response from the remote host before timing out.</span></span>
- <span data-ttu-id="7ddf6-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**(0x111) CloseNotify 메시지를 보낼 패킷을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a packet to send the CloseNotify message.</span></span>
- <span data-ttu-id="7ddf6-930">**NX_SECURE_TLS_TCP_SEND_FAILED**(0x109) TCP 소켓을 통해 CloseNotify 메시지를 보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-930">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Could not send the CloseNotify message over the TCP socket.</span></span>
- <span data-ttu-id="7ddf6-931">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-931">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-932">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-932">Allowed From</span></span>

<span data-ttu-id="7ddf6-933">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-933">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-934">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-934">Example</span></span>

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-935">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-935">See Also</span></span>

- <span data-ttu-id="7ddf6-936">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-936">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-937">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-937">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-938">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-938">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-939">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-939">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7ddf6-940">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-940">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7ddf6-941">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-941">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7ddf6-942">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-942">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_packet_buffer_set"></a><span data-ttu-id="7ddf6-943">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-943">nx_secure_tls_session_packet_buffer_set</span></span>

<span data-ttu-id="7ddf6-944">NetX Secure TLS 세션에 대한 패킷 리어셈블리 버퍼 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-944">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-945">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-945">Prototype</span></span>

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="7ddf6-946">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-946">Description</span></span>

<span data-ttu-id="7ddf6-947">이 서비스는 패킷 리어셈블리 버퍼를 TLS 세션에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-947">This service associates a packet reassembly buffer to a TLS session.</span></span> <span data-ttu-id="7ddf6-948">수신 TLS 레코드를 해독하고 구문 분석하려면 각 레코드의 데이터를 기본 TCP 패킷에서 조합해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-948">In order to decrypt and parse incoming TLS records, the data in each record must be assembled from the underlying TCP packets.</span></span> <span data-ttu-id="7ddf6-949">TLS 레코드 크기가 최대 16KB가 되어(일반적으로는 크기가 훨씬 작음) 단일 TCP 패킷에 맞지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-949">TLS records can be up to 16KB in size (though typically are much smaller) so may not fit into a single TCP packet.</span></span>

<span data-ttu-id="7ddf6-950">수신 메시지 크기가 16KB의 TLS 레코드 제한보다 작으면 버퍼 크기를 더 작게 만들 수 있지만 알 수 없는 수신 데이터를 처리하기 위해 버퍼를 최대한 크게 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-950">If you know the incoming message size will be smaller than the TLS record limit of 16KB, the buffer size can be made smaller, but in order to handle unknown incoming data the buffer should be made as large as possible.</span></span> <span data-ttu-id="7ddf6-951">수신 레코드가 제공된 버퍼보다 큰 경우 TLS 세션이 오류를 나타내며 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-951">If an incoming record is larger than the supplied buffer, the TLS session will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-952">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-952">Parameters</span></span>

- <span data-ttu-id="7ddf6-953">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-953">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-954">**buffer_ptr** TLS에서 패킷 리어셈블리에 사용할 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-954">**buffer_ptr** Pointer to buffer for TLS to use for packet reassembly.</span></span>
- <span data-ttu-id="7ddf6-955">**buffer_size** 제공된 버퍼의 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-955">**buffer_size** Size of the supplied buffer in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-956">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-956">Return Values</span></span>

- <span data-ttu-id="7ddf6-957">**NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-957">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7ddf6-958">**NX_INVALID_PARAMETERS**(0x4D) 버퍼 또는 TLS 세션 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-958">**NX_INVALID_PARAMETERS** (0x4D) Invalid buffer or TLS session pointer.</span></span>
- <span data-ttu-id="7ddf6-959">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-959">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-960">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-960">Allowed From</span></span>

<span data-ttu-id="7ddf6-961">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-961">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-962">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-962">Example</span></span>

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-963">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-963">See Also</span></span>

- <span data-ttu-id="7ddf6-964">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-964">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-965">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-965">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-966">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-966">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-967">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-967">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7ddf6-968">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-968">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7ddf6-969">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-969">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7ddf6-970">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-970">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_protocol_version_override"></a><span data-ttu-id="7ddf6-971">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="7ddf6-971">nx_secure_tls_session_protocol_version_override</span></span>

<span data-ttu-id="7ddf6-972">NetX Seure TLS 세션의 기본 TLS 프로토콜 버전 재정의</span><span class="sxs-lookup"><span data-stu-id="7ddf6-972">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-973">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-973">Prototype</span></span>

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a><span data-ttu-id="7ddf6-974">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-974">Description</span></span>

<span data-ttu-id="7ddf6-975">이 서비스는 특정 세션에서 사용하는 기본(최신) TLS 프로토콜 버전을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-975">This service overrides the default (newest) TLS protocol version used by a particular session.</span></span> <span data-ttu-id="7ddf6-976">이 서비스를 통해 NetX Secure TLS는 컴파일 시간에 최신 TLS 버전을 사용하지 않도록 설정하지 않고도 특정 TLS 세션에 이전 버전의 TLS를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-976">This enables NetX Secure TLS to use an older version of TLS for a specific TLS Session without disabling newer TLS versions at compile time.</span></span> <span data-ttu-id="7ddf6-977">이 서비스는 최신 버전의 TLS를 지원하지 않는 이전 호스트와 통신해야 하는 애플리케이션에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-977">This may be useful in applications that may need to communicate with an older host that does not support the newest version of TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddf6-978">*버전 5.11SP3의 NetX Secure TLS는 RFC 7507(아래 참고 참조)을 지원하며 이 API를 통해 이전 버전으로 재정의하면 ClientHello에서 대체 SCSV가 전송됩니다. 서버에서 최신 버전의 TLS를 지원하고 대체 SCSV이 ClientHello에 포함된 경우 해당 서버는 "부적절한 대체" 경고를 나타내며 TLS 핸드셰이크를 중단합니다. SCSV는 버전 재정의가 사용하도록 설정된 것보다 이전 버전의 TLS인 경우에만 전송됩니다. 예를 들어 버전을 TLS 1.2로 재정의하면 SCSV가 전송되지 않습니다.*</span><span class="sxs-lookup"><span data-stu-id="7ddf6-978">*As of version 5.11SP3, NetX Secure TLS supports RFC 7507 (see note below) and any override to an older version with this API will result in a fallback SCSV being sent in the ClientHello. If the server supports a newer version of TLS and the fallback SCSV is included in the ClientHello, that server will abort the TLS handshake with an "Inappropriate Fallback" alert. The SCSV is only sent when the version override is an older version of TLS than is enabled (e.g. if you override the version to TLS 1.2, no SCSV will be sent).*</span></span>

<span data-ttu-id="7ddf6-979">protocol_version 매개 변수에 대한 유효한 값은 매크로 NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 및 NX_SECURE_TLS_VERSION_TLS_1_2입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-979">Valid values for the protocol_version parameter are the following macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1, and NX_SECURE_TLS_VERSION_TLS_1_2.</span></span>

<span data-ttu-id="7ddf6-980">매크로 NX_SECURE_TLS_DISABLE_TLS_1_1 및 NX_SECURE_TLS_ENABLE_TLS_1_0을 사용하여 애플리케이션으로 컴파일되는 TLS 버전을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-980">The macros NX_SECURE_TLS_DISABLE_TLS_1_1 and NX_SECURE_TLS_ENABLE_TLS_1_0 can be used to control the versions of TLS that are compiled into the application.</span></span> <span data-ttu-id="7ddf6-981">TLS 버전 1.2는 항상 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-981">TLS version 1.2 is always enabled.</span></span>

<span data-ttu-id="7ddf6-982">원격 호스트에서 제공된 버전을 지원하지 않는 경우 연결이 실패합니다. 제공된 재정의 버전만 NetX Secure TLS에서 협상됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-982">Note that if the remote host does not support the supplied version, the connection will fail – only the supplied override version will be negotiated by NetX Secure TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddf6-983">RFC 7507: TLS 대체 SCSV.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-983">RFC 7507: TLS Fallback SCSV.</span></span> <span data-ttu-id="7ddf6-984">이 RFC는 원래 프로토콜 다운그레이드 협상을 부적절하게 처리하고 대신 유효한 ClientHello 메시지를 거부한 서버로 인해 야기된 보안 문제를 완화하기 위해 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-984">This RFC was introduced to mitigate a security problem that was originally caused by servers that improperly handled protocol downgrade negotiation and instead rejected otherwise valid ClientHello messages.</span></span> <span data-ttu-id="7ddf6-985">이러한 이전 서버와 호환되는 상태를 유지하려는 경우 일부 TLS 클라이언트 애플리케이션은 이전 TLS 버전을 사용하여 실패한 핸드셰이크를 다시 시도합니다(예: TLS 1.2가 실패하므로 TLS 1.1 시도).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-985">In an attempt to remain compatible with these old servers, some TLS client applications started to retry failed handshakes with and older TLS version (e.g. TLS 1.2 failed so try TLS 1.1).</span></span> <span data-ttu-id="7ddf6-986">그러나 이 해결 방법에는 새로운 문제가 야기되었습니다. 공격자는 서버가 최신 TLS 버전을 지원하는 경우에도 서버 연결 실패를 야기하는 네트워크 또는 패킷 오류를 인위적으로 도입하여 클라이언트를 강제로 다운그레이드하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-986">This workaround however introduced a new problem – an attacker could force a client to downgrade by artificially introducing a network or packet error causing the server connection to fail – even when the server supported the newer TLS version.</span></span> <span data-ttu-id="7ddf6-987">이전 버전으로 다운그레이드하면 공격자가 해당 버전의 약점을 악용할 수 있습니다(특히 SSLv3<sup>21</sup>은 POODLE 공격에 취약).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-987">By downgrading to an older version the attacker could exploit weaknesses in that version (SSLv3<sup>21</sup> in particular is weak to the POODLE attack).</span></span> <span data-ttu-id="7ddf6-988">이러한 상황을 방지하기 위해 RFC 7507은 TLS 클라이언트에서 지원하는 최신 버전이 아닌 TLS 버전을 사용할 때 TLS 서버에 알리는 ClientHello를 통해 전송되는 의사 암호 그룹<sup>22</sup>인 "대체 SCSV"를 도입했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-988">To prevent this situation, RFC 7507 introdued the "fallback SCSV," a pseudo-ciphersuite<sup>22</sup> sent in the ClientHello that notifies a TLS server when a TLS client is using a TLS version that is not the newest version it supports.</span></span> <span data-ttu-id="7ddf6-989">이러한 방식으로 최신 버전을 지원하는 서버는 대체 SCSV를 포함하는 ClientHello를 거부하고 다운그레이드 공격이 성공하지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-989">This way, a server that supports a newer version can reject a ClientHello containing the fallback SCSV and prevent the downgrade attack from succeeding.</span></span>

21. <span data-ttu-id="7ddf6-990">NetX Secure는 POODLE과 같은 알려진 심각한 약점 때문에 SSLv3를 구현하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-990">NetX Secure does not implement SSLv3 due to the existence of known serious weaknesses such as POODLE.</span></span>

22. <span data-ttu-id="7ddf6-991">의사 암호 그룹 또는 SCSV(Signaling Cipher Suite Value)는 이전 TLS 버전에서 사용할 수 없던 기능에 대해 사용하도록 설정된 TLS 구현을 신호로 알리는 데 사용되는 예약된 암호 그룹 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-991">A pseudo-ciphersuite, or SCSV (Signaling Cipher Suite Value), is a reserved ciphersuite number that is used to signal enabled TLS implementations about features that were not available in older TLS versions.</span></span> <span data-ttu-id="7ddf6-992">대체 SCSV 및 TLS_EMPTY_RENEGOTIATION_INFO_SCSV(RFC 5746)를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-992">The fallback SCSV and the TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) are examples.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-993">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-993">Parameters</span></span>

- <span data-ttu-id="7ddf6-994">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-994">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-995">**protocol_version** 사용할 특정 TLS 버전에 대한 TLS 버전 매크로입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-995">**protocol_version** TLS version macro for the specific TLS version to use.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-996">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-996">Return Values</span></span>

- <span data-ttu-id="7ddf6-997">**NX_SUCCESS** (0x00) 상태 변경에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-997">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="7ddf6-998">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-998">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7ddf6-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION**(0x110) 알려져 있지만 지원되지 않는 TLS 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Known but unsupported TLS version.</span></span>
- <span data-ttu-id="7ddf6-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION**(0x10F) 프로토콜 버전이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Invalid protocol version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1001">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1001">Allowed From</span></span>

<span data-ttu-id="7ddf6-1002">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1002">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1003">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1003">Example</span></span>

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1004">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1004">See Also</span></span>

- <span data-ttu-id="7ddf6-1005">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1005">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-1006">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1006">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_receive"></a><span data-ttu-id="7ddf6-1007">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1007">nx_secure_tls_session_receive</span></span>

<span data-ttu-id="7ddf6-1008">NetX Secure TLS 세션에서 데이터 받기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1008">Receive data from a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1009">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1009">Prototype</span></span>

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1010">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1010">Description</span></span>

<span data-ttu-id="7ddf6-1011">이 서비스는 지정된 활성 TLS 세션에서 데이터를 수신하고, NX_PACKET 매개 변수에서 호출자에게 제공하기 전에 해당 데이터의 암호 해독을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1011">This service receives data from the specified active TLS session, handling the decryption of that data before providing it to the caller in the NX_PACKET parameter.</span></span> <span data-ttu-id="7ddf6-1012">지정된 세션에 대기 중인 데이터가 없는 경우에는 제공된 대기 옵션에 따라 호출이 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1012">If no data is queued in the specified session, the call suspends based on the supplied wait option.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddf6-1013">NX_SUCCESS가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 해당 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1013">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1014">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1014">Parameters</span></span>

- <span data-ttu-id="7ddf6-1015">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1015">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-1016">**packet_ptr** 할당된 TLS 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1016">**packet_ptr** Pointer to an allocated TLS packet pointer.</span></span>
- <span data-ttu-id="7ddf6-1017">**wait_option** 서비스에서 반환 전에 원격 호스트에서 패킷을 대기해야 하는 기간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1017">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1018">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1018">Return Values</span></span>

- <span data-ttu-id="7ddf6-1019">**NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1019">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7ddf6-1020">**NX_NO_PACKET** (0x01) 수신된 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1020">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="7ddf6-1021">**NX_NOT_CONNECTED**(0x38) 기본 TCP 소켓이 더 이상 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1021">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="7ddf6-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE**(0x108) 받은 메시지의 인증 해시 확인에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="7ddf6-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION**(0x10F) 받은 메시지의 헤더에 알 수 없는 프로토콜 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="7ddf6-1024">**NX_SECURE_TLS_ALERT_RECEIVED**(0x114) 원격 호스트에서 TLS 경고를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1024">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="7ddf6-1025">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1025">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="7ddf6-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED**(0x101) 제공된 TLS 세션이 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1027">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1027">Allowed From</span></span>

<span data-ttu-id="7ddf6-1028">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1028">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1029">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1029">Example</span></span>

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1030">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1030">See Also</span></span>

- <span data-ttu-id="7ddf6-1031">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1031">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="7ddf6-1032">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1032">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-1033">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1033">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-1034">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1034">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-1035">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1035">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7ddf6-1036">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1036">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7ddf6-1037">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1037">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7ddf6-1038">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1038">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a><span data-ttu-id="7ddf6-1039">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1039">nx_secure_tls_session_renegotiate_callback_set</span></span>

<span data-ttu-id="7ddf6-1040">세션 다시 협상을 시작할 때 호출될 콜백 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1040">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1041">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1041">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a><span data-ttu-id="7ddf6-1042">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1042">Description</span></span>

<span data-ttu-id="7ddf6-1043">이 서비스는 세션 재협상 핸드셰이크의 첫 번째 메시지가 원격 호스트에서 수신될 때마다 호출되는 TLS 세션에 콜백을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1043">This service assigns a callback to a TLS session that will be invoked whenever the first message of a session renegotiation handshake is received from the remote host.</span></span>

<span data-ttu-id="7ddf6-1044">콜백 함수는 재협상 핸드셰이크가 시작될 것이라는 알림으로 애플리케이션에 전달됩니다. 애플리케이션은 콜백에서 0이 아닌 값을 반환하여 TLS 세션을 종료하도록 선택할 수 있습니다. 이로 인해 TLS 세션은 오류를 나타내며 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1044">The callback function is intended as a notification to the application that a renegotiation handshake is beginning – the application may choose to terminate the TLS session by returning any non-zero value from the callback which will cause TLS to end the TLS session with an error.</span></span> <span data-ttu-id="7ddf6-1045">애플리케이션에서 재협상을 계속하려는 경우 콜백이 NX_SUCCESS를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1045">If the application wishes to proceed with the renegotiation, the callback should return NX_SUCCESS.</span></span>

> [!NOTE]
> <span data-ttu-id="7ddf6-1046">*TLS 재협상의 의미 체계 때문에, 원격 서버에서 HelloRequest가 수신될 때마다 NetX Secure TLS 클라이언트에 대해 콜백이 호출되지만 클라이언트에서 재협상을 시작할 때는 콜백이 호출되지 않습니다. NetX Secure TLS 서버에서 재협상 ClientHello(활성 TLS 세션의 컨텍스트에서 수신된 ClientHello)가 수신될 때마다 콜백이 호출됩니다. 즉, TLS 서버에서 원격 클라이언트가 응답할 HelloRequest를 보내기 때문에 원격 호스트 또는 로컬 애플리케이션에서 재협상을 시작했는지 여부에 관계 없이 콜백이 호출됩니다.*</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1046">*Due to the semantics of TLS renegotiation, the callback will be invoked for NetX Secure TLS Clients whenever a HelloRequest is received from the remote server, but not when the client initiates the renegotiation. On NetX Secure TLS Servers, the callback will be invoked whenever a renegotiation ClientHello is received (any ClientHello received in the context of an active TLS session). This means that the callback will be invoked whether the remote host or the local application has initiated the renegotiation because the TLS server will send a HelloRequest to which the remote client will respond.*</span></span>

<span data-ttu-id="7ddf6-1047">NetX Secure TLS는 재협상 핸드셰이크가 중간자(man-in-the-middle) 공격을 받지 않도록 하기 위해 RFC 5746의 보안 재협상 표시 확장을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1047">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1048">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1048">Parameters</span></span>

- <span data-ttu-id="7ddf6-1049">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1049">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-1050">**callback** 콜백 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1050">**func_ptr** Pointer to callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1051">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1051">Return Values</span></span>

- <span data-ttu-id="7ddf6-1052">**NX_SUCCESS**(0x00) 콜백을 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1052">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="7ddf6-1053">**NX_PTR_ERROR**(0x07) 콜백 함수 또는 TLS 세션에 대해 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1053">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer for the callback function or TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1054">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1054">Allowed From</span></span>

<span data-ttu-id="7ddf6-1055">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1055">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1056">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1056">Example</span></span>

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1057">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1057">See Also</span></span>

- <span data-ttu-id="7ddf6-1058">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1058">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-1059">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1059">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-1060">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1060">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7ddf6-1061">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1061">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7ddf6-1062">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1062">nx_secure_tls_session_renegotiate</span></span>

## <a name="nx_secure_tls_session_renegotiate"></a><span data-ttu-id="7ddf6-1063">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1063">nx_secure_tls_session_renegotiate</span></span>

<span data-ttu-id="7ddf6-1064">원격 호스트와의 세션 재협상 핸드셰이크 시작</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1064">Initiate a session renegotiation handshake with the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1065">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1065">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1066">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1066">Description</span></span>

<span data-ttu-id="7ddf6-1067">이 서비스는 연결된 원격 TLS 호스트를 사용하여 세션 재협상 핸드셰이크를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1067">This service initiates a session *renegotiation* handshake with a connected remote TLS host.</span></span> <span data-ttu-id="7ddf6-1068">재협상은 이전에 설정된 TLS 세션의 컨텍스트 내에서 두 번째 TLS 핸드셰이크로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1068">A renegotiation consists of a second TLS handshake within the context of a previously-established TLS session.</span></span> <span data-ttu-id="7ddf6-1069">각각의 새 핸드셰이크 메시지는 새 세션 키가 생성되고 ChangeCipherSpec 메시지가 교환될 때까지 TLS 세션을 사용하여 암호화됩니다. 이때 새 키를 사용하여 모든 메시지를 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1069">Each of the new handshake messages is encrypted using the TLS session until new session keys are generated and ChangeCipherSpec messages are exchanged, at which time the new keys are used to encrypt all messages.</span></span>

<span data-ttu-id="7ddf6-1070">재협상은 TLS 세션이 설정되면 언제든지 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1070">A renegotiation can be initiated at any time once a TLS session is established.</span></span> <span data-ttu-id="7ddf6-1071">TLS 핸드셰이크 도중이나 TLS 세션이 설정되기 전에 재협상을 시도하면 아무 작업도 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1071">If a renegotiation is attempted during a TLS handshake or before a TLS session is established no action will be taken.</span></span>

> [!NOTE]
> <span data-ttu-id="7ddf6-1072">이 서비스가 호출될 때 전체 TLS 핸드셰이크가 수행되므로 완료 시간과 반환되는 상태는 현재 TLS 설정 및 세션 매개 변수에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1072">*An entire TLS handshake will be performed when this service is invoked so the time to completion and returned status will vary depending on the current TLS settings and session parameters.*</span></span>

<span data-ttu-id="7ddf6-1073">NetX Secure TLS는 재협상 핸드셰이크가 중간자(man-in-the-middle) 공격을 받지 않도록 하기 위해 RFC 5746의 보안 재협상 표시 확장을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1073">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1074">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1074">Parameters</span></span>

- <span data-ttu-id="7ddf6-1075">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1075">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-1076">**wait_option** 서비스에서 반환 전에 원격 호스트에서 패킷을 대기해야 하는 기간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1076">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span> <span data-ttu-id="7ddf6-1077">이 매개 변수는 TLS 내의 모든 NetX 서비스에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1077">This is passed to all NetX services within TLS.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1078">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1078">Return Values</span></span>

- <span data-ttu-id="7ddf6-1079">**NX_SUCCESS**(0x00) 재협상에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1079">**NX_SUCCESS** (0x00) Successful renegotiation.</span></span>
- <span data-ttu-id="7ddf6-1080">**NX_NO_PACKET** (0x01) 수신된 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1080">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="7ddf6-1081">**NX_NOT_CONNECTED**(0x38) 기본 TCP 소켓이 더 이상 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1081">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="7ddf6-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE**(0x108) 받은 메시지의 인증 해시 확인에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="7ddf6-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION**(0x10F) 받은 메시지의 헤더에 알 수 없는 프로토콜 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="7ddf6-1084">**NX_SECURE_TLS_ALERT_RECEIVED**(0x114) 원격 호스트에서 TLS 경고를 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1084">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="7ddf6-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE**(0x134) 로컬 또는 원격 TLS 세션이 비활성 상태이므로 재협상이 불가능해집니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) The local or remote TLS session is inactive, making renegotiation impossible.</span></span>
- <span data-ttu-id="7ddf6-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE**(0x13A) 원격 호스트가 SCSV 또는 보안 재협상 확장을 제공하지 않았으므로 재협상을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) The remote host did not provide either the SCSV or Secure Renegotiation Extension and thus renegotiation cannot be performed.</span></span>
- <span data-ttu-id="7ddf6-1087">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1087">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="7ddf6-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED**(0x101) 제공된 TLS 세션이 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>
- <span data-ttu-id="7ddf6-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**(0x111) 기본 패킷을 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1090">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1090">Allowed From</span></span>

<span data-ttu-id="7ddf6-1091">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1091">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1092">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1092">Example</span></span>

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1093">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1093">See Also</span></span>

- <span data-ttu-id="7ddf6-1094">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1094">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-1095">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1095">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-1096">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1096">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7ddf6-1097">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1097">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7ddf6-1098">nx_secure_tls_session_renegotiation_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1098">nx_secure_tls_session_renegotiation_callback_set</span></span>

## <a name="nx_secure_tls_session_reset"></a><span data-ttu-id="7ddf6-1099">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1099">nx_secure_tls_session_reset</span></span>

<span data-ttu-id="7ddf6-1100">NetX Secure TLS 세션 지우기 및 다시 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1100">Clear out and reset a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1101">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1101">Prototype</span></span>

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1102">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1102">Description</span></span>

<span data-ttu-id="7ddf6-1103">이 서비스는 기존 TLS 세션 개체를 새 세션에 다시 사용할 수 있도록 TLS 세션을 지운 후 세션이 방금 만들어진 것처럼 상태를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1103">This service clears out a TLS session and resets the state as if the session had just been created so an existing TLS session object can be re-used for a new session.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1104">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1104">Parameters</span></span>

- <span data-ttu-id="7ddf6-1105">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1105">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1106">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1106">Return Values</span></span>

- <span data-ttu-id="7ddf6-1107">**NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1107">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7ddf6-1108">**NX_INVALID_PARAMETERS**(0x4D) TLS 세션 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1108">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7ddf6-1109">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1109">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1110">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1110">Allowed From</span></span>

<span data-ttu-id="7ddf6-1111">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1111">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1112">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1112">Example</span></span>

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1113">See Also</span></span>

- <span data-ttu-id="7ddf6-1114">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1114">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-1115">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1115">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-1116">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1116">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-1117">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1117">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7ddf6-1118">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1118">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7ddf6-1119">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1119">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7ddf6-1120">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1120">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_send"></a><span data-ttu-id="7ddf6-1121">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1121">nx_secure_tls_session_send</span></span>

<span data-ttu-id="7ddf6-1122">NetX Secure TLS 세션을 통해 데이터 보내기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1122">Send data through a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1123">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1123">Prototype</span></span>

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1124">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1124">Description</span></span>

<span data-ttu-id="7ddf6-1125">이 서비스는 지정된 활성 TLS 세션을 사용하여 제공된 NX_PACKET에서 데이터를 보내고, 원격 호스트에 전송하기 전에 해당 데이터의 암호화를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1125">This service sends data in the supplied NX_PACKET, using the specified active TLS session, and handling the encryption of that data before sending it to the remote host.</span></span> <span data-ttu-id="7ddf6-1126">마지막으로 보급된 수신기 창 크기가 이 요청 미만이면 지정된 대기 옵션에 따라 선택적으로 서비스가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1126">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait options specified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddf6-1127">오류가 반환되지 않는 한 이 호출 후 애플리케이션은 패킷을 해제하면 안 됩니다. 애플리케이션이 패킷을 해제하면 전송 후 네트워크 드라이버가 패킷을 해제하므로 예측할 수 없는 결과가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1127">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1128">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1128">Parameters</span></span>

- <span data-ttu-id="7ddf6-1129">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1129">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-1130">**packet_ptr** 전송할 데이터를 포함하는 TLS 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1130">**packet_ptr** Pointer to a TLS packet containing data to be sent.</span></span>
- <span data-ttu-id="7ddf6-1131">**wait_option** 요청이 수신기 창 크기를 초과하는 경우 서비스가 작동하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1131">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1132">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1132">Return Values</span></span>

- <span data-ttu-id="7ddf6-1133">**NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1133">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7ddf6-1134">**NX_NO_PACKET** (0x01) 수신된 데이터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1134">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="7ddf6-1135">**NX_NOT_CONNECTED**(0x38) 기본 TCP 소켓이 더 이상 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1135">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="7ddf6-1136">**NX_SECURE_TLS_TCP_SEND_FAILED**(0x109) 기본 TCP 소켓 보내기가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) The underlying TCP socket send failed.</span></span>
- <span data-ttu-id="7ddf6-1137">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1137">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="7ddf6-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED**(0x101) 제공된 TLS 세션이 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1139">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1139">Allowed From</span></span>

<span data-ttu-id="7ddf6-1140">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1140">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1141">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1141">Example</span></span>

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1142">See Also</span></span>

- <span data-ttu-id="7ddf6-1143">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1143">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="7ddf6-1144">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1144">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-1145">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1145">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-1146">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1146">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="7ddf6-1147">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1147">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-1148">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1148">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7ddf6-1149">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1149">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7ddf6-1150">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1150">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7ddf6-1151">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1151">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_server_callback_set"></a><span data-ttu-id="7ddf6-1152">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1152">nx_secure_tls_session_server_callback_set</span></span>

<span data-ttu-id="7ddf6-1153">TlS가 TLS 서버 핸드셰이크 시작 시 호출할 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1153">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1154">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1154">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="7ddf6-1155">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1155">Description</span></span>

<span data-ttu-id="7ddf6-1156">이 서비스는 TLS 서버 핸드셰이크가 ClientHello 메시지를 받았을 때 TLS에서 호출하는 TLS 세션에 함수 포인터를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1156">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Server handshake has received a ClientHello message.</span></span> <span data-ttu-id="7ddf6-1157">콜백 함수를 사용하면 애플리케이션은 수신된 ClientHello 메시지에서 입력 또는 의사 결정이 필요한 모든 TLS 확장을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1157">The callback function allows an application to process any TLS extensions from the received ClientHello message that require input or decision making.</span></span>

<span data-ttu-id="7ddf6-1158">호출하는 TLS 세션 제어 블록과 NX_SECURE_TLS_HELLO_EXTENSION 개체의 배열로 콜백이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1158">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="7ddf6-1159">확장 개체의 배열은 특정 확장을 찾아서 구문 분석하는 도우미 함수에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1159">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="7ddf6-1160">Hello 메시지에 제공된 TLS 확장을 구문 분석하는 도우미 함수 예제는 *nx_secure_tls_session_sni_extension_parse* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1160">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="7ddf6-1161">서버 콜백을 TLS 서버에 대한 *nx_secure_tls_active_certificate_set* 을 사용하여 활성 ID 인증서를 선택하는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1161">The server callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Server.</span></span> <span data-ttu-id="7ddf6-1162">이러한 작업은 주로 SNI(서버 이름 표시) 확장에 대한 응답으로 발생하며, 이를 통해 TLS 클라이언트는 연결하려는 서버를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1162">This will most often occur in response to a Server Name Indication (SNI) extension which allows a TLS Client to indicate which server it is attempting to contact.</span></span> <span data-ttu-id="7ddf6-1163">자세한 내용은   nx_secure_tls_session_sni_extension_parse 및 nx_secure_tls_active_certificate_set을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1163">See the references for *nx_secure_tls_session_sni_extension_parse* and *nx_secure_tls_active_certificate_set* for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1164">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1164">Parameters</span></span>

- <span data-ttu-id="7ddf6-1165">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1165">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-1166">**func_ptr** TLS 서버 콜백 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1166">**func_ptr** Pointer to the TLS Server callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1167">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1167">Return Values</span></span>

- <span data-ttu-id="7ddf6-1168">**NX_SUCCESS**(0X00) 함수 포인터를 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1168">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="7ddf6-1169">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1169">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1170">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1170">Allowed From</span></span>

<span data-ttu-id="7ddf6-1171">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1172">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1172">Example</span></span>

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1173">See Also</span></span>

- <span data-ttu-id="7ddf6-1174">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1174">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-1175">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1175">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="7ddf6-1176">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1176">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="7ddf6-1177">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1177">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="7ddf6-1178">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1178">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="7ddf6-1179">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1179">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_sni_extension_parse"></a><span data-ttu-id="7ddf6-1180">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1180">nx_secure_tls_session_sni_extension_parse</span></span>

<span data-ttu-id="7ddf6-1181">TLS 클라이언트에서 받은 SNI(서버 이름 표시) 확장 구문 분석</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1181">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1182">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1182">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1183">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1183">Description</span></span>

<span data-ttu-id="7ddf6-1184">이 서비스는 nx_secure_tls_session_server_callback_set을 사용하여 TLS 세션에 추가되는 TLS 서버 세션 콜백 내에서 호출되도록 고안되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1184">This service is intended to be called from within a TLS Server session callback, added to a TLS session using nx_secure_tls_session_server_callback_set.</span></span> <span data-ttu-id="7ddf6-1185">콜백은 원격 TLS 클라이언트에서 ClientHello 메시지를 수신한 이후에 호출되며, 사용 가능한 확장의 배열(및 배열의 확장 개수)이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1185">The callback is invoked following the reception of a ClientHello message from a remote TLS client and is supplied an array of available extensions (and the number of extensions in the array).</span></span> <span data-ttu-id="7ddf6-1186">해당 배열 및 길이를 이 루틴에 직접 전달하여 SNI 확장이 있는지 확인할 수 있습니다. 그렇지 않으면 클라이언트가 SNI 확장을 제공하지 않기로 선택했음을 나타내기 위해 NX_SECURE_TLS_EXTENSION_NOT_FOUND가 반환됩니다(이것은 오류가 아님).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1186">That array and its length can be passed directly to this routine to determine if there is an SNI extension present – if not, NX_SECURE_TLS_EXTENSION_NOT_FOUND is returned indicating simply that the client opted not to provice the SNI extension (this is not an error).</span></span>

<span data-ttu-id="7ddf6-1187">SNI 확장이 있으면 TLS 클라이언트에서 제공하는 X.509 DNS 이름이 dns_name 구조체로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1187">If the SNI extension is found, the X.509 DNS name supplied by the TLS client is returned in the dns_name structure.</span></span> <span data-ttu-id="7ddf6-1188">현재 SNI 확장은 단일 DNS 이름 항목만 제공합니다. 이 항목은 TLS 서버에서 원격 클라이언트에 보낼 ID 인증서를 결정하는 데 사용할 수 있습니다.\*\*</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1188">Currently, the SNI extension only supplies a single DNS name entry, which may be used by the TLS server to determine which identity certificate to send to the remote client.\*\*</span></span>

<span data-ttu-id="7ddf6-1189">NX_SECURE_X509_DNS_NAME 구조체에는 필드 nx_secure_x509_dns_name에 UCHAR 문자열로 DNS 이름이 포함되고 nx_secure_x509_dns_name_length에 이름 문자열 길이가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1189">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="7ddf6-1190">매크로 NX_SECURE_X509_DNS_NAME_MAX는 nx_secure_x509_dns_name 버퍼의 크기를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1190">The macro NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1191">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1191">Parameters</span></span>

- <span data-ttu-id="7ddf6-1192">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1192">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-1193">**extensions** TLS Hello 확장 배열에 대한 포인터입니다(세션 콜백).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1193">**extensions** Pointer to an array of TLS Hello extensions (from session callback).</span></span>
- <span data-ttu-id="7ddf6-1194">**num_extensions** 배열의 확장 수입니다(세션 콜백).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1194">**num_extensions** Number of extensions in array (from session callback).</span></span>
- <span data-ttu-id="7ddf6-1195">**dns_name** SNI 확장에 제공된 DNS 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1195">**dns_name** Return DNS name supplied in the SNI extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1196">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1196">Return Values</span></span>

- <span data-ttu-id="7ddf6-1197">**NX_SUCCESS**(0x00) 확장을 성공적으로 구문 분석했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1197">**NX_SUCCESS** (0x00) Successful parsing of the extension.</span></span>
- <span data-ttu-id="7ddf6-1198">**NX_PTR_ERROR**(0x07) 확장 배열 또는 TLS 세션 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1198">**NX_PTR_ERROR** (0x07) Invalid extensions array or TLS session pointer.</span></span>
- <span data-ttu-id="7ddf6-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND**(0x136) SNI 확장을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI extension not found.</span></span>
- <span data-ttu-id="7ddf6-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID**(0x137) SNI 확장 형식이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI extension format was invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1201">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1201">Allowed From</span></span>

<span data-ttu-id="7ddf6-1202">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1203">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1203">Example</span></span>

### <a name="see-also"></a><span data-ttu-id="7ddf6-1204">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1204">See Also</span></span>

- <span data-ttu-id="7ddf6-1205">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1205">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="7ddf6-1206">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1206">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="7ddf6-1207">nx_secure_tls_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1207">nx_secure_tls_server_callback_set</span></span>
- <span data-ttu-id="7ddf6-1208">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1208">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_sni_extension_set"></a><span data-ttu-id="7ddf6-1209">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1209">nx_secure_tls_session_sni_extension_set</span></span>

<span data-ttu-id="7ddf6-1210">원격 서버로 전송할 SNI(서버 이름 표시) 확장 DNS 이름 설정</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1210">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1211">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1211">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1212">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1212">Description</span></span>

<span data-ttu-id="7ddf6-1213">이 서비스를 통해 TLS 클라이언트 애플리케이션은 SNI(서버 이름 표시) TLS 확장을 사용하여 기본 서버 DNS 이름을 원격 TLS 서버에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1213">This service allows a TLS Client application to provide a preferred server DNS name to a remote TLS server using the Server Name Indication (SNI) TLS extension.</span></span> <span data-ttu-id="7ddf6-1214">SNI 확장을 사용하면 서버는 클라이언트의 표시된 서버 기본 설정에 따라 적절한 ID 인증서 및 매개 변수를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1214">The SNI extension allows the server to select the proper identity certificate and parameters based on the client's indicated server preference.</span></span> <span data-ttu-id="7ddf6-1215">SNI 확장은 현재 전송될 단일 DNS 이름만 지원하므로 단일 이름 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1215">The SNI extension currently only supports a single DNS name to be sent, hence the singular name parameter.</span></span> <span data-ttu-id="7ddf6-1216">dns_name 매개 변수는 nx_secure_x509_dns_name_initialize를 사용하여 초기화해야 하며 클라이언트의 기본 설정 서버를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1216">The dns_name parameter must be initialized with *nx_secure_x509_dns_name_initialize* and will contain the client's preferred server.</span></span> <span data-ttu-id="7ddf6-1217">확장 이름을 설정 해제하려면 NX_NULL의 "dns_name" 매개 변수 값으로 이 서비스를 호출하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1217">To unset the extension name, simply call this service with a "dns_name" parameter value of NX_NULL.</span></span>

<span data-ttu-id="7ddf6-1218">NX_SECURE_X509_DNS_NAME 구조체에는 필드 nx_secure_x509_dns_name에 UCHAR 문자열로 DNS 이름이 포함되고 nx_secure_x509_dns_name_length에 이름 문자열 길이가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1218">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field  *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="7ddf6-1219">매크로 NX_SECURE_X509_DNS_NAME_MAX는 nx_secure_x509_dns_name 버퍼의 크기를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1219">The macro  NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="7ddf6-1220">nx_secure_tls_session_start를 호출하기 전에 이 루틴을 호출해야 하며 그러지 않으면 ClientHello에 SNI 확장이 포함되지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1220">*This routine must be called before nx_secure_tls_session_start is invoked or the ClientHello will not contain the SNI extension.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1221">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1221">Parameters</span></span>

- <span data-ttu-id="7ddf6-1222">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1222">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-1223">**dns_name** 애플리케이션에서 제공하는 DNS 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1223">**dns_name** DNS name supplied by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1224">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1224">Return Values</span></span>

- <span data-ttu-id="7ddf6-1225">**NX_SUCCESS**(0x00) DNS 서버 이름을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1225">**NX_SUCCESS** (0x00) Successful addition of DNS server name.</span></span>
- <span data-ttu-id="7ddf6-1226">**NX_PTR_ERROR**(0X07) DNS 이름 또는 TLS 세션 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1226">**NX_PTR_ERROR** (0x07) Invalid DNS name or TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1227">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1227">Allowed From</span></span>

<span data-ttu-id="7ddf6-1228">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1228">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1229">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1229">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1230">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1230">See Also</span></span>

- <span data-ttu-id="7ddf6-1231">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1231">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-1232">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1232">nx_secure_x509_dns_name_initialize</span></span>

## <a name="nx_secure_tls_session_start"></a><span data-ttu-id="7ddf6-1233">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1233">nx_secure_tls_session_start</span></span>

<span data-ttu-id="7ddf6-1234">NetX Secure TLS 세션 시작</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1234">Start a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1235">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1235">Prototype</span></span>

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1236">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1236">Description</span></span>

<span data-ttu-id="7ddf6-1237">이 서비스는 제공된 TLS 세션 제어 블록 및 연결된 TCP 소켓을 사용하여 TLS 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1237">This service starts a TLS session using the supplied TLS session control block and a connected TCP socket.</span></span> <span data-ttu-id="7ddf6-1238">nx_tcp_client_socket_connect 또는 nx_tcp_server_socket_accept를 성공적으로 호출한 후에는 TCP 연결을 이미 완료했어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1238">The TCP connection must already be complete following a successful call to either nx_tcp_client_socket_connect or nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="7ddf6-1239">이 서비스는 TCP 소켓에서 TLS 세션의 유형(클라이언트 또는 서버)을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1239">This service will determine the type of TLS session (Client or Server) from the TCP socket.</span></span>

<span data-ttu-id="7ddf6-1240">대기 옵션은 TLS 핸드셰이크가 진행 중인 동안 서비스가 동작하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1240">The wait option defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1241">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1241">Parameters</span></span>

- <span data-ttu-id="7ddf6-1242">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1242">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-1243">**tcp_socket_ptr** 연결된 TCP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1243">**tcp_socket_ptr** Pointer to a connected TCP socket.</span></span>
- <span data-ttu-id="7ddf6-1244">**wait_option** 은 TLS 핸드셰이크가 진행 중인 동안 서비스가 동작하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1244">**wait_option** Defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1245">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1245">Return Values</span></span>

- <span data-ttu-id="7ddf6-1246">**NX_SUCCESS** (0x00) TLS 세션을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1246">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7ddf6-1247">**NX_NOT_CONNECTED** (0x38) 기본 TCP 소켓이 더 이상 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1247">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="7ddf6-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) 받은 TLS 메시지 유형이 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="7ddf6-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) 원격 호스트에서 제공하는 암호화가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="7ddf6-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) TLS 핸드셰이크 중 메시지 처리가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="7ddf6-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) 들어오는 메시지가 해시 MAC 검사에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="7ddf6-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 기본 TCP 소켓 보내기가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="7ddf6-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 들어오는 메시지의 길이 필드가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="7ddf6-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC**(0x10B) 들어오는 ChangeCipherSpec 메시지가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="7ddf6-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT**(0x10C) 들어오는 TLS 인증서를 원격 TLS 서버 식별에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="7ddf6-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER**(0x10D) 원격 호스트에서 제공하는 공개 키 암호가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="7ddf6-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) NetX Secure TLS 스택에서 지원하는 ciphersuite가 없다고 원격 호스트에서 알렸습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="7ddf6-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) 받은 TLS 메시지의 헤더에 알 수 없는 TLS 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="7ddf6-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) 받은 TLS 메시지의 헤더에 알고 있지만 지원되지 않는 TLS 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="7ddf6-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) 내부 TLS 패킷을 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="7ddf6-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) 원격 호스트에서 제공한 인증서가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="7ddf6-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) 원격 호스트가 오류를 알리는 경고를 보내고 TLS 세션을 종료했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="7ddf6-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE**(0x13B) 암호 그룹 테이블의 항목에 NULL 함수 포인터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="7ddf6-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK**(0x146) 원격 TLS ClientHello는 대체 SCSV를 포함하며 버전 대체를 시도했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) A remote TLS ClientHello included the fallback SCSV andattempted a version fallback.</span></span>
- <span data-ttu-id="7ddf6-1265">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1265">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1266">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1266">Allowed From</span></span>

<span data-ttu-id="7ddf6-1267">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1268">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1268">Example</span></span>

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1269">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1269">See Also</span></span>

- <span data-ttu-id="7ddf6-1270">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1270">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="7ddf6-1271">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1271">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-1272">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1272">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-1273">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1273">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7ddf6-1274">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1274">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7ddf6-1275">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1275">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7ddf6-1276">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1276">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="7ddf6-1277">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1277">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7ddf6-1278">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1278">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-1279">nx_tcp_socket_accept</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1279">nx_tcp_socket_accept</span></span>
- <span data-ttu-id="7ddf6-1280">nx_tcp_socket_listen</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1280">nx_tcp_socket_listen</span></span>
- <span data-ttu-id="7ddf6-1281">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1281">nx_tcp_socket_disconnect</span></span>
- <span data-ttu-id="7ddf6-1282">nx_tcp_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1282">nx_tcp_socket_unaccept</span></span>
- <span data-ttu-id="7ddf6-1283">nx_tcp_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1283">nx_tcp_socket_relisten</span></span>
- <span data-ttu-id="7ddf6-1284">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1284">nx_tcp_socket_delete</span></span>
- <span data-ttu-id="7ddf6-1285">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1285">nx_packet_allocate</span></span>
- <span data-ttu-id="7ddf6-1286">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1286">nx_packet_data_append</span></span>
- <span data-ttu-id="7ddf6-1287">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1287">nx_packet_data_extract_offset</span></span>

## <a name="nx_secure_tls_session_time_function_set"></a><span data-ttu-id="7ddf6-1288">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1288">nx_secure_tls_session_time_function_set</span></span>

<span data-ttu-id="7ddf6-1289">NetX Secure TLS 세션에 타임스탬프 함수 할당</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1289">Assign a timestamp function to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1290">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1290">Prototype</span></span>

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a><span data-ttu-id="7ddf6-1291">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1291">Description</span></span>

<span data-ttu-id="7ddf6-1292">이 함수는 현재 시간을 가져와야 할 때 TLS가 호출할 함수 포인터를 설정합니다. 이 함수는 다양한 TLS 핸드셰이크 메시지에서, 인증서 확인을 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1292">This function sets up a function pointer that TLS will invoke when it needs to get the current time, which is used in various TLS handshake messages and for verification of certificates.</span></span>

<span data-ttu-id="7ddf6-1293">이 함수는 TLS RFC 5246의 ClientHello 요구 사항에 따라 현재 GMT를 UNIX 32비트 형식으로 반환해야 합니다(UTC로 1970년 1월 1일부터 시작해서 자정 이후의 시간(초)이며, 윤초는 무시함).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1293">The function is expected to return the current GMT in UNIX 32-bit format (seconds since the midnight starting Jan 1, 1970, UTC, ignoring leap seconds), as per the ClientHello requirements in the TLS RFC 5246.</span></span>

<span data-ttu-id="7ddf6-1294">타임스탬프 함수를 할당하지 않으면 TLS 핸드셰이크의 타임스탬프에 대한 값 0이 사용되고 인증서 만료 확인이 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1294">If no timestamp function is assigned, a value of 0 for the timestamp in the TLS handshake will be used and certificate expiration checking will not work.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1295">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1295">Parameters</span></span>

- <span data-ttu-id="7ddf6-1296">**session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1296">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-1297">**time_func_ptr** UNIX 32비트 형식의 현재 시간(GMT)을 반환하는 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1297">**time_func_ptr** Pointer to a function that returns the current time (GMT) in UNIX 32-bit format.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1298">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1298">Return Values</span></span>

- <span data-ttu-id="7ddf6-1299">**NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1299">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7ddf6-1300">**NX_INVALID_PARAMETERS**(0x4D) TLS 세션 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1300">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7ddf6-1301">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1301">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1302">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1302">Allowed From</span></span>

<span data-ttu-id="7ddf6-1303">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1303">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1304">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1304">Example</span></span>

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1305">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1305">See Also</span></span>

- <span data-ttu-id="7ddf6-1306">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1306">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-1307">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1307">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-1308">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1308">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7ddf6-1309">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1309">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7ddf6-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7ddf6-1311">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1311">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_trusted_certificate_add"></a><span data-ttu-id="7ddf6-1312">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1312">nx_secure_tls_trusted_certificate_add</span></span>

<span data-ttu-id="7ddf6-1313">NetX Secure TLS 세션에 신뢰할 수 있는 인증서 추가</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1313">Add trusted certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1314">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1314">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1315">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1315">Description</span></span>

<span data-ttu-id="7ddf6-1316">이 서비스는 초기화된 NX_SECURE_X509_CERT 구조체 인스턴스를 TLS 세션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1316">This service adds an initialized NX_SECURE_X509_CERT structure instance to a TLS session.</span></span> <span data-ttu-id="7ddf6-1317">이 인증서는 TLS 스택에서 TLS 핸드셰이크 중에 원격 호스트에서 제공하는 인증서를 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1317">This certificate is used by the TLS stack to verify certificates supplied by the remote host during the TLS handshake.</span></span>

<span data-ttu-id="7ddf6-1318">TLS 클라이언트 모드에는 신뢰할 수 있는 인증서가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1318">Trusted certificates are required for TLS Client mode.</span></span>

<span data-ttu-id="7ddf6-1319">클라이언트 인증서 인증을 사용하도록 설정한 경우에는 TLS 서버 모드에서만 신뢰할 수 있는 인증서가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1319">Trusted certificates are only required for TLS Server mode if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1320">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1320">Parameters</span></span>

- <span data-ttu-id="7ddf6-1321">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1321">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-1322">**certificate_ptr** 초기화된 TLS 인증서 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1322">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1323">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1323">Return Values</span></span>

- <span data-ttu-id="7ddf6-1324">**NX_SUCCESS**(0x00) 인증서를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1324">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="7ddf6-1325">**NX_INVALID_PARAMETERS**(0x4D) 잘못된 인증서를 추가하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1325">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>
- <span data-ttu-id="7ddf6-1326">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1326">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1327">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1327">Allowed From</span></span>

<span data-ttu-id="7ddf6-1328">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1329">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1329">Example</span></span>

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1330">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1330">See Also</span></span>

- <span data-ttu-id="7ddf6-1331">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1331">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-1332">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1332">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-1333">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1333">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-1334">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1334">nx_secure_tls_trusted_certificate_remove</span></span>

## <a name="nx_secure_tls_trusted_certificate_remove"></a><span data-ttu-id="7ddf6-1335">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1335">nx_secure_tls_trusted_certificate_remove</span></span>

<span data-ttu-id="7ddf6-1336">NetX Secure TLS 세션에서 신뢰할 수 있는 인증서 제거</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1336">Remove trusted certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1337">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1337">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1338">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1338">Description</span></span>

<span data-ttu-id="7ddf6-1339">이 서비스는 인증서의 일반 이름 필드에 입력된 TLS 세션에서 신뢰할 수 있는 인증서를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1339">This service removes a trusted certificate from a TLS session, keyed on the Common Name field in the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1340">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1340">Parameters</span></span>

- <span data-ttu-id="7ddf6-1341">**session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1341">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7ddf6-1342">**common_name** 제거할 인증서의 일반 이름 값입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1342">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="7ddf6-1343">**common_name_length** 일반 이름 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1343">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1344">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1344">Return Values</span></span>

- <span data-ttu-id="7ddf6-1345">**NX_SUCCESS**(0x00) 인증서를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="7ddf6-1346">**NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1346">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7ddf6-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0x119) 인증서를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1348">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1348">Allowed From</span></span>

<span data-ttu-id="7ddf6-1349">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1350">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1350">Example</span></span>

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1351">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1351">See Also</span></span>

- <span data-ttu-id="7ddf6-1352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7ddf6-1353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-1354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-1355">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1355">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_x509_certificate_initialize"></a><span data-ttu-id="7ddf6-1356">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1356">nx_secure_x509_certificate_initialize</span></span>

<span data-ttu-id="7ddf6-1357">NetX Secure TLS에 대한 X.509 인증서 초기화</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1357">Initialize X.509 Certificate for NetX Secure TLS</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1358">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1358">Prototype</span></span>

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1359">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1359">Description</span></span>

<span data-ttu-id="7ddf6-1360">이 서비스는 TLS 세션에서 사용하기 위해 이진으로 인코딩된 X.509 디지털 인증서에서 NX_SECURE_X509_CERT 구조체를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1360">This service initializes an NX_SECURE_X509_CERT structure from a binary-encoded X.509 digital certificate for use in a TLS session.</span></span>

<span data-ttu-id="7ddf6-1361">인증서 데이터는 DER로 인코딩된 이진 형식의 유효한 X.509 디지털 인증서 **여야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1361">The certificate data **must** be a valid X.509 digital certificate in DER-encoded binary format.</span></span> <span data-ttu-id="7ddf6-1362">데이터는 해당 데이터에 대한 UCHAR 포인터가 제공되는 한, 어떤 소스(예: 파일 시스템, 컴파일된 상수 버퍼 등)에서도 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1362">The data can some from any source (e.g. file system, compiled constant buffer, etc.) as long as a UCHAR pointer to that data is provided.</span></span>

<span data-ttu-id="7ddf6-1363">*raw_data_buffer* 매개 변수 및 해당 크기는 구문 분석 전에 인증서 데이터가 복사되는 전용 버퍼를 지정하는 선택적 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1363">The *raw_data_buffer* parameter and its size are optional parameters that specify a dedicated buffer into which the certificate data is copied before parsing.</span></span> <span data-ttu-id="7ddf6-1364">raw_data_buffer가 NX_NULL로 전달되는 경우 NX_SECURE_X509_CERT 구조체가 certificate_data 배열을 직접 가리킵니다(이 경우 buffer_size는 무시됨).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1364">If raw_data_buffer is passed as NX_NULL then the NX_SECURE_X509_CERT structure will point directly into the certificate_data array (buffer_size is ignored in this case).</span></span> <span data-ttu-id="7ddf6-1365">raw_data_buffer가 NX_NULL로 전달되는 경우 certificate_data 포인터가 가리키는 데이터를 수정하지 ***않아야 합니다***. 데이터를 수정하면 인증서 처리가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1365">If raw_data_buffer is passed as NX_NULL, ***do not*** modify the data pointed to by the certificate_data pointer or certificate processing will likely fail!</span></span>

<span data-ttu-id="7ddf6-1366">프라이빗 키 매개 변수는 로컬 ID 인증서에 사용됩니다. 서버는 클라이언트에서 들어오는 키 데이터(서버의 퍼블릭 키를 사용하여 암호화됨) 암호를 해독하는 데, 클라이언트는 서버에서 클라이언트 인증서를 요청할 때 서버에 대한 ID를 확인하는 데 프라이빗 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1366">The private key parameter is for local identity certificates – the private key is used by servers to decrypt the incoming key data from a client (encrypted using the server's public key) and by clients to verify their identity to a server when the server requests a client certificate.</span></span> <span data-ttu-id="7ddf6-1367">이 API를 사용하여 프라이빗 키를 추가하면 연결된 인증서가 자동으로 TLS 애플리케이션에 대한 ID 인증서로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1367">Adding a private key with this API will automatically mark the associated certificate as being an identity certificate for a TLS application.</span></span> <span data-ttu-id="7ddf6-1368">다른 용도(예: 신뢰할 수 있는 저장소)로 인증서를 초기화하는 경우 private_key_data 매개 변수는 NULL로 전달되고, private_key_data_length는 0으로 전달되고, private_key_type은 NX_SECURE_X509_KEY_TYPE_NONE으로 전달되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1368">When initializing certificates for other purposes (e.g. the trusted store), the *private_key_data* parameter should be passed as NULL, the *private_key_data_length* as 0, and the *private_key_type* should be passed as NX_SECURE_X509_KEY_TYPE_NONE.</span></span>

<span data-ttu-id="7ddf6-1369">*private_key_type* 매개 변수는 프라이빗 키의 서식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1369">The *private_key_type* parameter indicates the formatting of the private key.</span></span> <span data-ttu-id="7ddf6-1370">예를 들어, 프라이빗 키가 DER로 인코딩된 PKCS#1 형식 RSA 프라이빗 키인 경우 private_key_type를 NetX Secure에 알려진 형식으로, 즉시 구문 분석된 후 나중에 사용하기 위해 저장되는 NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER로 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1370">For example, if the private key is a DER-encoded PKCS#1-format RSA private key, the private_key_type should be passed as NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, a type known to NetX Secure which will be parsed immediately and saved for later use.</span></span>

<span data-ttu-id="7ddf6-1371">또한 이 private_key_type은 특정 키 형식이나 다른 요구 사항이 있는 플랫폼 및 애플리케이션에 대한 사용자 정의 키 형식<sup>23</sup>을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1371">The private_key_type also supports user-defined key types<sup>23</sup> for platforms and applications that have specific key formats or other needs.</span></span> <span data-ttu-id="7ddf6-1372">예를 들어, 하드웨어 기반 암호화 엔진은 NetX Secure 소프트웨어에서 인식하지 않는 특정 형식을 사용할 수 있으며, 프라이빗 키는 TPM(신뢰할 수 있는 플랫폼 모듈) 또는 PKCS#11 암호화 하드웨어를 사용하는 경우와 마찬가지로 암호화하거나 암호화 토큰으로 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1372">For example, a hardware-based encryption engine may use a specific format not understood by the NetX Secure software, or a private key may be encrypted or represented by a cryptographic token as might be the case with a Trusted Platform Module (TPM) or PKCS#11 cryptographic hardware.</span></span> <span data-ttu-id="7ddf6-1373">사용자 정의 키 형식이 사용될 때 키 데이터는 적절한 암호화 루틴으로 있는 그대로 전달됩니다. 예를 들어, RSA 프라이빗 키는 구문 분석 또는 처리 없이 암호 그룹 테이블의 TLS에 제공되는 RSA 암호화 루틴으로 직접 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1373">When a user-defined key type is used, the key data is passed verbatim to the appropriate cryptographic routine - for example, an RSA private key would be passed, without any parsing or processing, directly to the RSA cryptographic routine provided to TLS in the ciphersuite table.</span></span> <span data-ttu-id="7ddf6-1374">사용자 정의 키 형식이 암호화 루틴에도 전달됩니다(RSA의 경우 "op" 매개 변수임).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1374">The user-defined key type is also passed to the cryptographic routine (in the case of RSA, this is the "op" parameter).</span></span>

<span data-ttu-id="7ddf6-1375">사용자 정의 키의 범위는 0x0001 0000-0xFFFF FFFF에 해당하는 32비트 부호 없는 정수의 위쪽 절반을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1375">The range of user-defined keys covers the top half of a 32-bit unsigned integer, from 0x0001 0000-0xFFFF FFFF.</span></span> <span data-ttu-id="7ddf6-1376">0x0001 0000보다 작은 값은 NetX Secure에서 사용하도록 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1376">Values less than 0x0001 0000 are reserved for NetX Secure use.</span></span>

<span data-ttu-id="7ddf6-1377">사용자 정의 키 형식은 원시 개인 키 데이터를 처리하기 위해 사용자 지정 암호화 루틴에 필요한 고급 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1377">User-defined key types are an advanced feature that requires custom cryptographic routines to handle the raw private key data.</span></span> <span data-ttu-id="7ddf6-1378">이 기능이 필요한 경우 Express 논리 담당자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1378">Please contact your Express Logic representative if you have need of this feature.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1379">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1379">Parameters</span></span>

- <span data-ttu-id="7ddf6-1380">**certificate_ptr** 초기화되지 않은 X.509 인증서 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1380">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="7ddf6-1381">**certificate_data** DER로 인코딩된 X.509 이진 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1381">**certificate_data** Pointer to DER-encoded X.509 binary data.</span></span>
- <span data-ttu-id="7ddf6-1382">**raw_data_buffer** 선택적 전용 인증서 데이터 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1382">**raw_data_buffer** Pointer to optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="7ddf6-1383">**buffer_size** 선택적 전용 인증서 데이터 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1383">**buffer_size** Size of optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="7ddf6-1384">**certificate_data_length** 인증서 이진 데이터의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1384">**certificate_data_length** Length of certificate binary data in bytes.</span></span>
- <span data-ttu-id="7ddf6-1385">**private_key_data** 선택적 프라이빗 키 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1385">**private_key_data** Pointer to optional private key data.</span></span>
- <span data-ttu-id="7ddf6-1386">**private_key_data_length** 프라이빗 키 데이터의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1386">**private_key_data_length** Length of private key data.</span></span>
- <span data-ttu-id="7ddf6-1387">**private_key_type** 키 형식 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1387">**private_key_type** Key type identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1388">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1388">Return Values</span></span>

- <span data-ttu-id="7ddf6-1389">**NX_SUCCESS**(0x00) 인증서를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1389">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="7ddf6-1390">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1390">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="7ddf6-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE**(0x112) 인증서 데이터에 DER로 인코딩된 X.509 인증서가 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate.</span></span>
- <span data-ttu-id="7ddf6-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER**(0x10D) 인증서에 NetX Secure에서 지원하는 퍼블릭 키 암호가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Certificate did not have a public-key cipher that is supported by NetX Secure.</span></span>
- <span data-ttu-id="7ddf6-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE**(0x186) 프라이빗 키 또는 인증서에 유효한 ASN.1 시퀀스가 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Private key or certificate did not contain a valid ASN.1 sequence.</span></span>
- <span data-ttu-id="7ddf6-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY**(0x18A) 제공된 프라이빗 키가 유효한 PKCS#1 RSA 키가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) The provided private key was not a valid PKCS#1 RSA key.</span></span>
- <span data-ttu-id="7ddf6-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE**(0x19D) 제공된 프라이빗 키 형식이 사용자 정의 형식이 아니며 알려진 형식과 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) The private key type provided was not user-defined and did not match any known type.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1396">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1396">Allowed From</span></span>

<span data-ttu-id="7ddf6-1397">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1398">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1398">Example</span></span>

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1399">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1399">See Also</span></span>

- <span data-ttu-id="7ddf6-1400">nx_secure_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1400">nx_secure_local_certificate_add</span></span>
- <span data-ttu-id="7ddf6-1401">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1401">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-1402">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1402">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7ddf6-1403">3장의 NetX Secure로 X.509 인증서 가져오기</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1403">Importing X.509 Certificates into NetX Secure in Chapter 3.</span></span>

## <a name="nx_secure_x509_common_name_dns_check"></a><span data-ttu-id="7ddf6-1404">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1404">nx_secure_x509_common_name_dns_check</span></span>

<span data-ttu-id="7ddf6-1405">X.509 인증서에서 DNS 이름 확인</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1405">Check DNS name against X.509 Certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1406">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1406">Prototype</span></span>

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1407">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1407">Description</span></span>

<span data-ttu-id="7ddf6-1408">이 서비스는 원격 호스트의 DNS 유효성 검사를 위해 호출자가 제공한 TLD(최상위 도메인 이름)를 기준으로 인증서의 일반 이름을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1408">This service checks a certificate's Common Name against a Top- Domain name (TLD) provided by the caller for the purposes of DNS validation of a remote host.</span></span> <span data-ttu-id="7ddf6-1409">이 유틸리티 함수는 애플리케이션에서 제공하는 인증서 유효성 검사 콜백 루틴 내에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1409">This utility function is intended to be called from within a certificate validation callback routine provided by the application.</span></span> <span data-ttu-id="7ddf6-1410">TLD 이름은 원격 호스트에 액세스하는 데 사용되는 URL의 맨 위 부분 이어야 합니다(첫 번째 슬래시 앞의 문자열이 "."로 구분됨).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1410">The TLD name should be the top part of the URL used to access the remote host (the "."-separated string before the first slash).</span></span> <span data-ttu-id="7ddf6-1411">일반 이름에 와일드카드가 포함되어 있으면(예: .example.com) 와일드카드는 접미사가 같은 항목을 찾습니다. 발견된(오른쪽에서 왼쪽으로 읽음) 첫 번째 와일드카드("")만 와일드카드 일치로 고려됩니다. 예를 들어, abc.\*.example.com은 ".example.com"으로 끝나는 모든 이름을 일치 항목으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1411">If the Common Name contains a wildcard (such as *.example.com), the wildcard will match any with the same suffix. Note that only the first wildcard ("*") encountered (reading right-to-left) will be considered for wildcard matching – for example, abc.\*.example.com will match *any* name ending in ".example.com".</span></span>

<span data-ttu-id="7ddf6-1412">일반 이름이 제공된 문자열과 일치하지 않으면 "subjectAltName" 확장이 구문 분석되고(인증서에 있는 경우) DNSName 항목도 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1412">If the Common Name does not match the provided string, the "subjectAltName" extension is parsed (if it exists in the certificate) and any DNSName entries are also compared.</span></span> <span data-ttu-id="7ddf6-1413">일치하는 항목이 없는 경우 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1413">If none of those entries match, an error is returned.</span></span>

<span data-ttu-id="7ddf6-1414">예상된 인증서에서 일반 이름(및 subjectAltName 항목)의 형식을 이해하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1414">It is important to understand the format of the common name (and subjectAltName entries) in expected certificates.</span></span> <span data-ttu-id="7ddf6-1415">예를 들어, 일부 인증서는 원시 IP 주소 또는 와일드 카드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1415">For example, some certificates may use a raw IP address or a wild card.</span></span> <span data-ttu-id="7ddf6-1416">수신된 인증서의 예상 값과 일치하도록 DNS TLD 문자열의 형식을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1416">The DNS TLD string must be formatted such that it will match the expected values in received certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1417">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1417">Parameters</span></span>

- <span data-ttu-id="7ddf6-1418">**certificate_ptr** X.509 인증서 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1418">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>
- <span data-ttu-id="7ddf6-1419">**dns_tld** 비교할 최상위 도메인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1419">**dns_tld** Top-Level Domain name to compare against.</span></span>
- <span data-ttu-id="7ddf6-1420">**dns_tld_length** TLD 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1420">**dns_tld_length** Length of TLD string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1421">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1421">Return Values</span></span>

- <span data-ttu-id="7ddf6-1422">**NX_SUCCESS**(0x00) 일반 이름 또는 subjectAltName과 성공적으로 비교되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1422">**NX_SUCCESS** (0x00) Successful comparison with Common Name or subjectAltName.</span></span>
- <span data-ttu-id="7ddf6-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH**(0x195) 일치하는 이름을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) No matching name found.</span></span>
- <span data-ttu-id="7ddf6-1424">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1424">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1425">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1425">Allowed From</span></span>

<span data-ttu-id="7ddf6-1426">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1426">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1427">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1427">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1428">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1428">See Also</span></span>

- <span data-ttu-id="7ddf6-1429">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1429">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-1430">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1430">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="7ddf6-1431">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1431">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_x509_crl_revocation_check"></a><span data-ttu-id="7ddf6-1432">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1432">nx_secure_x509_crl_revocation_check</span></span>

<span data-ttu-id="7ddf6-1433">제공된 CRL(인증서 해지 목록)에서 x.509 인증서 확인</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1433">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1434">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1434">Prototype</span></span>

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1435">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1435">Description</span></span>

<span data-ttu-id="7ddf6-1436">이 서비스는 DER로 인코딩된 인증서 해지 목록을 사용하고 해당 목록에서 특정 인증서를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1436">This service takes a DER-encoded Certificate Revocation List and searches for a specific certificate in that list.</span></span> <span data-ttu-id="7ddf6-1437">CRL의 발급자는 제공된 인증서 저장소를 기준으로 유효성이 검사되고, CRL 발급자는 확인하려는 인증서의 발급자와 동일한지 검사되며, 의심되는 인증서의 일련 번호을 해지된 인증서 목록에서 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1437">The issuer of the CRL is validated against a supplied certificate store, the CRL issuer is validated to be the same as the one for the certificate being checked, and the serial number of the certificate in question is used to search the revoked certificates list.</span></span> <span data-ttu-id="7ddf6-1438">발급자가 일치하면 서명이 체크 아웃되고 인증서가 목록에 **없으면** 호출은 성공적으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1438">If the issuers match, the signature checks out, and the certificate is **not** present in the list, the call is successful.</span></span> <span data-ttu-id="7ddf6-1439">다른 모든 경우에는 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1439">All other cases cause an error to be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1440">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1440">Parameters</span></span>

- <span data-ttu-id="7ddf6-1441">**crl_data** DER로 인코딩된 CRL에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1441">**crl_data** Pointer to a DER-encoded CRL.</span></span>
- <span data-ttu-id="7ddf6-1442">**crl_length** CRL 데이터의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1442">**crl_length** Length in bytes of CRL data.</span></span>
- <span data-ttu-id="7ddf6-1443">**store** X.509 인증서 저장소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1443">**store** Pointer to an X.509 Certificate store.</span></span>
- <span data-ttu-id="7ddf6-1444">**certificate_ptr** X.509 인증서 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1444">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1445">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1445">Return Values</span></span>

- <span data-ttu-id="7ddf6-1446">**NX_SUCCESS**(0x00) 인증서가 해지되지 않았음을 확인했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1446">**NX_SUCCESS** (0x00) Successful validation that the certificate was not revoked.</span></span>
- <span data-ttu-id="7ddf6-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0X119) CRL 발급자 인증서를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) CRL issuer certificate not found.</span></span>
- <span data-ttu-id="7ddf6-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND**(0x11B) 인증서 발급자 인증서를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificate issuer certificate not found.</span></span>
- <span data-ttu-id="7ddf6-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**(0x182) CRL ASN.1에 잘못된 길이 필드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) The CRL ASN.1 contained an invalid length field.</span></span>
- <span data-ttu-id="7ddf6-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** CRL에 잘못된 ASN.1이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** The CRL contained invalid ASN.1.</span></span>
- <span data-ttu-id="7ddf6-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE**(0x18c) 인증서 체인을 확인하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) A certificate chain verification failed.</span></span>
- <span data-ttu-id="7ddf6-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH**(0x197) CRL 및 인증서 발급자가 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL and certificate issuers did not match.</span></span>
- <span data-ttu-id="7ddf6-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED**(0x198) CRL 서명이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) The CRL signature was invalid.</span></span>
- <span data-ttu-id="7ddf6-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED**(0x199) 확인 중인 인증서가 CRL에서 발견되었으며 해지됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) The certificate being checked was found in the CRL and is therefore revoked.</span></span>
- <span data-ttu-id="7ddf6-1455">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1455">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1456">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1456">Allowed From</span></span>

<span data-ttu-id="7ddf6-1457">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1458">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1458">Example</span></span>

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1459">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1459">See Also</span></span>

- <span data-ttu-id="7ddf6-1460">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1460">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-1461">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1461">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="7ddf6-1462">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1462">nx_secure_x509_common_name_dns_check</span></span>

## <a name="nx_secure_x509_dns_name_initialize"></a><span data-ttu-id="7ddf6-1463">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1463">nx_secure_x509_dns_name_initialize</span></span>

<span data-ttu-id="7ddf6-1464">X.509 DNS 이름 구조 초기화</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1464">Initialize an X.509 DNS name structure</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1465">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1465">Prototype</span></span>

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1466">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1466">Description</span></span>

<span data-ttu-id="7ddf6-1467">이 서비스는 특정 이름 형식이 필요한 특정 API 서비스에서 사용할 X.509 DNS 이름을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1467">This service initializes an X.509 DNS name for use with certain API services requiring a specific name format.</span></span> <span data-ttu-id="7ddf6-1468">예를 들어 TLS 핸드셰이크 중에 원격 호스트가 제공하는 이름과 일치하는 이름을 서버 이름 표시 확장에서 찾으려면 nx_secure_tls_sni_extension_parse 서비스에 NX_SECURE_X509_DNS_NAME 개체가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1468">For example, the *nx_secure_tls_sni_extension_parse* service expects an NX_SECURE_X509_DNS_NAME object in order to match the name provided by a remote host in the Server Name Indication extension during the TLS handshake.</span></span> <span data-ttu-id="7ddf6-1469">DNS 이름은 단순히 길이가 지정된 문자열입니다. DNS 이름의 최대 허용 길이(및 NX_SECURE_X509_DNS_NAME의 내부 버퍼 크기)는 매크로 NX_SECURE_X509_DNS_NAME_MAX(기본값 100바이트)로 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1469">A DNS name is simply a charater string with a length – the maximum allowed length of a DNS name (and the size of the internal buffer in NX_SECURE_X509_DNS_NAME) is controlled by the macro NX_SECURE_X509_DNS_NAME_MAX (default 100 bytes).</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1470">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1470">Parameters</span></span>

- <span data-ttu-id="7ddf6-1471">**dns_name** 초기화할 DNS 이름 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1471">**dns_name** DNS name structure to initialize.</span></span>
- <span data-ttu-id="7ddf6-1472">**name_string** DNS 이름 문자열 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1472">**name_string** DNS name string data.</span></span>
- <span data-ttu-id="7ddf6-1473">**length** 이름 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1473">**length** Length of name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1474">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1474">Return Values</span></span>

- <span data-ttu-id="7ddf6-1475">**NX_SUCCESS**(0x00) 성공적으로 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1475">**NX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="7ddf6-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG**(0x19E) 지정된 이름 문자열이 NX_SECURE_X509_DNS_NAME_MAX를 초과했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) The given name string exceeded NX_SECURE_X509_DNS_NAME_MAX.</span></span>
- <span data-ttu-id="7ddf6-1477">**NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1477">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1478">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1478">Allowed From</span></span>

<span data-ttu-id="7ddf6-1479">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1480">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1480">Example</span></span>

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1481">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1481">See Also</span></span>

- <span data-ttu-id="7ddf6-1482">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1482">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7ddf6-1483">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1483">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="7ddf6-1484">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1484">nx_secure_tls_session_sni_extension_set</span></span>

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a><span data-ttu-id="7ddf6-1485">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1485">nx_secure_x509_extended_key_usage_extension_parse</span></span>

<span data-ttu-id="7ddf6-1486">X.509 인증서에서 X.509 확장 키 사용 확장 찾기 및 구문 분석</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1486">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1487">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1487">Prototype</span></span>

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1488">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1488">Description</span></span>

<span data-ttu-id="7ddf6-1489">이 서비스는 인증서 확인 콜백 내에서 호출되어야 합니다(*nx_secure_tls_session_certificate_callback_set* 참조).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1489">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="7ddf6-1490">X.509 인증서 내에서 특정 확장 키 사용 OID를 검색하고 OID가 있는지 여부를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1490">It will search for a specific extended key usage OID within an X.509 certificate and return whether the OID is present.</span></span> <span data-ttu-id="7ddf6-1491">key_usage 매개 변수는 가변 길이 OID 문자열을 매개 변수로 전달하지 않도록 하기 위해 NetX Secure X.509 및 TLS에서 내부적으로 사용하는 OID의 정수 매핑입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1491">The key_usage parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="7ddf6-1492">확장 키 사용 확장에 대한 관련 OID는 아래 표에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1492">The relevant OIDs for the extended key usage extension are given in the table below.</span></span> <span data-ttu-id="7ddf6-1493">수신된 TLS 서버 인증서에서 확장 키 사용을 확인하려는 일반적인 TLS 클라이언트 구현은 OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH가 있는지 확인합니다. 확장은 있지만 해당 OID가 없는 경우 인증서는 호스트를 TLS 서버로 식별하기에 유효하지 않은 것으로 간주되며 인증서 확인 콜백에서 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1493">A typical TLS Client implementation wishing to check extended key usage in a received TLS server certificate would check for the existence of the OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – if the extension is present but that OID is not, then the certificate would be considered invalid for identifiying the host as a TLS server and the certificate verification callback should return an error.</span></span> <span data-ttu-id="7ddf6-1494">확장 자체가 없으면 TLS 핸드셰이크를 계속할지 여부는 애플리케이션에 달려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1494">If the extension itself is missing, then it is up to the application whether or not to proceed with the TLS handshake.</span></span>

<span data-ttu-id="7ddf6-1495">인증서 확인 콜백에서 오류 반환 코드 NX_SECURE_X509_KEY_USAGE_ERROR가 애플리케이션 사용을 위해 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1495">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="7ddf6-1496">키 사용을 확인하는 동안 오류가 발생하면 콜백에서 이 값을 반환하여 실패 이유를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1496">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="7ddf6-1497">NetX Secure 식별자</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1497">NetX Secure Identifier</span></span>                                | <span data-ttu-id="7ddf6-1498">OID 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1498">OID Value</span></span>         | <span data-ttu-id="7ddf6-1499">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1499">Description</span></span>                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| <span data-ttu-id="7ddf6-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span></span>   | <span data-ttu-id="7ddf6-1501">1.3.6.1.5.5.7.3.1</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1501">1.3.6.1.5.5.7.3.1</span></span> | <span data-ttu-id="7ddf6-1502">인증서를 사용하여 TLS 서버를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1502">Certificate can be used to identify a TLS server</span></span> |
| <span data-ttu-id="7ddf6-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span></span>   | <span data-ttu-id="7ddf6-1504">1.3.6.1.5.5.7.3.2</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1504">1.3.6.1.5.5.7.3.2</span></span> | <span data-ttu-id="7ddf6-1505">인증서를 사용하여 TLS 클라이언트를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1505">Certificate can be used to identify a TLS client</span></span> |
| <span data-ttu-id="7ddf6-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span></span>  | <span data-ttu-id="7ddf6-1507">1.3.6.1.5.5.7.3.3</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1507">1.3.6.1.5.5.7.3.3</span></span> | <span data-ttu-id="7ddf6-1508">인증서를 사용하여 코드에 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1508">Certificate can be used to sign code</span></span>             |
| <span data-ttu-id="7ddf6-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span></span> | <span data-ttu-id="7ddf6-1510">1.3.6.1.5.5.7.3.4</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1510">1.3.6.1.5.5.7.3.4</span></span> | <span data-ttu-id="7ddf6-1511">인증서를 사용하여 메일에 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1511">Certificate can be used to sign emails</span></span>           |
| <span data-ttu-id="7ddf6-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span></span> | <span data-ttu-id="7ddf6-1513">1.3.6.1.5.5.7.3.8</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1513">1.3.6.1.5.5.7.3.8</span></span> | <span data-ttu-id="7ddf6-1514">인증서를 사용하여 타임스탬프에 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1514">Certificate can be used to sign timestamps</span></span>       |
| <span data-ttu-id="7ddf6-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span></span>  | <span data-ttu-id="7ddf6-1516">1.3.6.1.5.5.7.3.9</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1516">1.3.6.1.5.5.7.3.9</span></span> | <span data-ttu-id="7ddf6-1517">인증서를 사용하여 OCSP 응답에 서명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1517">Certificate can be used to sign OCSP responses</span></span>   |

<span data-ttu-id="7ddf6-1518">X.509 확장 키 사용 확장에 대한 OID 및 매핑</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1518">OIDs and mappings for X.509 Extended Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1519">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1519">Parameters</span></span>

- <span data-ttu-id="7ddf6-1520">**certificate** 확인할 인증서에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1520">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="7ddf6-1521">**key_usage** 위 표에 제공되는 OID 정수 매핑입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1521">**key_usage** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1522">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1522">Return Values</span></span>

- <span data-ttu-id="7ddf6-1523">**NX_SUCCESS**(0x00) 지정된 키 사용 OID를 찾았습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1523">**NX_SUCCESS** (0x00) Specified key usage OID found.</span></span>
- <span data-ttu-id="7ddf6-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**(0x181) ASN.1 멀티바이트 태그가 나타났습니다(지원되지 않는 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="7ddf6-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**(0x182) 잘못된 ASN.1 필드가 나타났습니다(잘못된 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="7ddf6-1526">**NX_SECURE_X509_INVALID_TAG_CLASS**(0x190) 잘못된 ASN.1 태그 클래스가 나타났습니다(잘못된 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="7ddf6-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**(0x192) 잘못된 확장이 나타났습니다(잘못된 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="7ddf6-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND**(0x19b) 제공된 인증서에서 확장 키 사용 확장을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The Extended Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="7ddf6-1529">**NX_PTR_ERROR**(0x07) 인증서 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1529">**NX_PTR_ERROR** (0x07) Invalid certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1530">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1530">Allowed From</span></span>

<span data-ttu-id="7ddf6-1531">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1532">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1532">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1533">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1533">See Also</span></span>

- <span data-ttu-id="7ddf6-1534">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1534">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="7ddf6-1535">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1535">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="7ddf6-1536">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1536">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="7ddf6-1537">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1537">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="7ddf6-1538">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1538">nx_secure_x509_extension_find</span></span>

## <a name="nx_secure_x509_extension_find"></a><span data-ttu-id="7ddf6-1539">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1539">nx_secure_x509_extension_find</span></span>

<span data-ttu-id="7ddf6-1540">X.509 인증서에서 X.509 확장 찾기 및 반환</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1540">Find and return an X.509 extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1541">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1541">Prototype</span></span>

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1542">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1542">Description</span></span>

<span data-ttu-id="7ddf6-1543">이 서비스는 인증서 확인 콜백 내에서 호출되어야 하며(*nx_secure_tls_session_certificate_callback_set* 참조) 고급 X.509 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1543">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)* and is an advanced X.509 service.</span></span>

<span data-ttu-id="7ddf6-1544">함수는 OID를 기준으로 X.509 인증서 내에서 특정 확장을 검색하고, OID가 있는지 여부를 반환하며, 관련 원시 확장 데이터에 대한 참조를 포함하는 구조체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1544">The function will search for a specific extension within an X.509 certificate based on an OID and return whether the OID is present, along with a structure containing references to the relevant raw extension data.</span></span> <span data-ttu-id="7ddf6-1545">extension_id 매개 변수는 가변 길이 OID 문자열을 매개 변수로 전달하지 않도록 하기 위해 NetX Secure X.509 및 TLS에서 내부적으로 사용하는 OID의 정수 매핑입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1545">The extension_id parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="7ddf6-1546">특정 확장(예: nx_secure_x509_key_usage_extension_parse)에 대해 제공된 도우미 함수는 내부적으로 nx_secure_x509_extension_find를 호출하여 확장 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1546">The helper functions provided for specific extensions (such as *nx_secure_x509_key_usage_extension_parse*) call nx_secure_x509_extension_find internally to obtain the extension data.</span></span>

<span data-ttu-id="7ddf6-1547">알려진 X.509 확장에 대한 관련 OID는 아래 표에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1547">The relevant OIDs for known X.509 extensions are given in the table below.</span></span>

<span data-ttu-id="7ddf6-1548">NX_SECURE_X509_EXTENSION 구조체에는 nx_secure_x509_key_usage_extension_parse와 같은 도우미 함수를 사용하여 DER로 인코딩된 원시 확장 ASN.1 데이터를 빠르게 디코딩할 수 있도록 하는 X.509 인증서에 대한 포인터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1548">The NX_SECURE_X509_EXTENSION structure contains pointers into the X.509 certificate that allow helper functions such as *nx_secure_x509_key_usage_extension_parse* to quickly decode the raw extension DER-encoded ASN.1 data.</span></span>

<span data-ttu-id="7ddf6-1549">특정 확장에 대한 내용은 RFC 5280(X.509 사양) 또는 적절한 도우미 함수에 대한 참조(사용 가능한 경우)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1549">For information on specific extensions, see RFC 5280 (X.509 specification) or the reference for the appropriate helper functions if available.</span></span>

<span data-ttu-id="7ddf6-1550">NetX Secure X.509의 현재 버전은 X.509 확장을 제한적으로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1550">The current version of NetX Secure X.509 has limited support for X.509 extensions.</span></span> <span data-ttu-id="7ddf6-1551">추가 도우미 함수는 나중에 추가될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1551">More helper functions will be added in the future.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddf6-1552">이 서비스는 X.509 확장 및 DER로 인코딩된 ASN.1에 익숙한 사용자를 위한 고급 기능입니다. 이 기능은 이러한 사용자들이 NetX Secure X.509가 현재 도우미 함수를 제공하지 않는 확장에 액세스할 수 있도록 하기 위해 제공됩니다. 도우미 함수를 사용하지 않는 확장의 경우 DER로 인코딩된 원시 ASN.1을 직접 구문 분석해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1552">*This service is an advanced feature for users familiar with X.509 extensions and DER-encoded ASN.1. It is provided to enable those users to access extensions for which NetX Secure X.509 does not currently provide helper functions. For those extensions without helper functions, you will have to parse the raw DER-encoded ASN.1 yourself.*</span></span>

| <span data-ttu-id="7ddf6-1553">NetX Secure 식별자</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1553">NetX Secure Identifier</span></span>                              | <span data-ttu-id="7ddf6-1554">OID 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1554">OID Value</span></span> | <span data-ttu-id="7ddf6-1555">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1555">Description</span></span>                                                                    | <span data-ttu-id="7ddf6-1556">도우미 함수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1556">Helper function?</span></span> |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| <span data-ttu-id="7ddf6-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span></span>  | <span data-ttu-id="7ddf6-1558">2.5.29.9</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1558">2.5.29.9</span></span>  | <span data-ttu-id="7ddf6-1559">디렉터리 특성 – 인증서 주체에 대한 기본 정보 특성</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1559">Directory Attributes – basic information attributes about certificate subject</span></span>  | <span data-ttu-id="7ddf6-1560">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1560">No</span></span>               |
| <span data-ttu-id="7ddf6-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span></span>       | <span data-ttu-id="7ddf6-1562">2.5.29.14</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1562">2.5.29.14</span></span> | <span data-ttu-id="7ddf6-1563">특정 공개 키를 식별하는 데 사용</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1563">Used to identify a specific public key</span></span>                                         | <span data-ttu-id="7ddf6-1564">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1564">No</span></span>               |
| <span data-ttu-id="7ddf6-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span></span>             | <span data-ttu-id="7ddf6-1566">2.5.29.15</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1566">2.5.29.15</span></span> | <span data-ttu-id="7ddf6-1567">인증서 공개 키에 대한 유효한 사용 정보 제공</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1567">Provides information on valid uses for the certificate public key</span></span>              | <span data-ttu-id="7ddf6-1568">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1568">Yes</span></span>              |
| <span data-ttu-id="7ddf6-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span></span>     | <span data-ttu-id="7ddf6-1570">2.5.29.17</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1570">2.5.29.17</span></span> | <span data-ttu-id="7ddf6-1571">인증서를 식별하기 위한 대체 DNS 이름 제공</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1571">Provides alternative DNS names to identify the certificate</span></span>                     | <span data-ttu-id="7ddf6-1572">예<sup>24</sup></span><span class="sxs-lookup"><span data-stu-id="7ddf6-1572">Yes<sup>24</sup></span></span>        |
| <span data-ttu-id="7ddf6-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span></span>      | <span data-ttu-id="7ddf6-1574">2.5.29.18</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1574">2.5.29.18</span></span> | <span data-ttu-id="7ddf6-1575">인증서 발급자를 식별하기 위한 대체 DNS 이름 제공</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1575">Provides alternative DNS names to identify the certificate's issuer</span></span>            | <span data-ttu-id="7ddf6-1576">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1576">No</span></span>               |
| <span data-ttu-id="7ddf6-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span></span>     | <span data-ttu-id="7ddf6-1578">2.5.29.19</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1578">2.5.29.19</span></span> | <span data-ttu-id="7ddf6-1579">기본 인증서 사용 제약 조건 정보 제공</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1579">Provides basic certificate usage constraint information</span></span>                        | <span data-ttu-id="7ddf6-1580">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1580">No</span></span>               |
| <span data-ttu-id="7ddf6-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span></span>      | <span data-ttu-id="7ddf6-1582">2.5.29.30</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1582">2.5.29.30</span></span> | <span data-ttu-id="7ddf6-1583">인증서 이름을 특정 도메인으로 제한하는 데 사용</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1583">Used to constrain certificate names to specific domains</span></span>                        | <span data-ttu-id="7ddf6-1584">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1584">No</span></span>               |
| <span data-ttu-id="7ddf6-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span></span>      | <span data-ttu-id="7ddf6-1586">2.5.29.31</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1586">2.5.29.31</span></span> | <span data-ttu-id="7ddf6-1587">CRL 배포를 위한 URI 제공</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1587">Provides URIs for CRL distribution</span></span>                                             | <span data-ttu-id="7ddf6-1588">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1588">No</span></span>               |
| <span data-ttu-id="7ddf6-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span></span>  | <span data-ttu-id="7ddf6-1590">2.5.29.32</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1590">2.5.29.32</span></span> | <span data-ttu-id="7ddf6-1591">대규모 PKI 시스템에 대한 인증서 정책 목록</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1591">List of certificate policies for large PKI systems</span></span>                             | <span data-ttu-id="7ddf6-1592">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1592">No</span></span>               |
| <span data-ttu-id="7ddf6-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span></span> | <span data-ttu-id="7ddf6-1594">2.5.29.33</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1594">2.5.29.33</span></span> | <span data-ttu-id="7ddf6-1595">CA 인증서 정책 목록</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1595">List of CA certificate policies</span></span>                                                | <span data-ttu-id="7ddf6-1596">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1596">No</span></span>               |
| <span data-ttu-id="7ddf6-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span></span>     | <span data-ttu-id="7ddf6-1598">2.5.29.35</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1598">2.5.29.35</span></span> | <span data-ttu-id="7ddf6-1599">인증서 시그니처와 연결된 특정 공개 키를 식별하는 데 사용</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1599">Used to identify a specific public key associated with a certificate signature</span></span> | <span data-ttu-id="7ddf6-1600">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1600">No</span></span>               |
| <span data-ttu-id="7ddf6-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span></span>    | <span data-ttu-id="7ddf6-1602">2.5.29.36</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1602">2.5.29.36</span></span> | <span data-ttu-id="7ddf6-1603">CA 정책 제약 조건</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1603">CA policy constraints</span></span>                                                          | <span data-ttu-id="7ddf6-1604">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1604">No</span></span>               |
| <span data-ttu-id="7ddf6-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span></span>   | <span data-ttu-id="7ddf6-1606">2.5.29.37</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1606">2.5.29.37</span></span> | <span data-ttu-id="7ddf6-1607">추가 OID 기반 키 사용 정보</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1607">Additional OID-based key usage information</span></span>                                     | <span data-ttu-id="7ddf6-1608">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1608">Yes</span></span>              |
| <span data-ttu-id="7ddf6-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span></span>          | <span data-ttu-id="7ddf6-1610">2.5.29.46</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1610">2.5.29.46</span></span> | <span data-ttu-id="7ddf6-1611">델타 CRL을 얻기 위한 정보 제공</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1611">Provides information for obtaining delta CRLs</span></span>                                  | <span data-ttu-id="7ddf6-1612">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1612">No</span></span>               |
| <span data-ttu-id="7ddf6-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span></span>     | <span data-ttu-id="7ddf6-1614">2.5.29.54</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1614">2.5.29.54</span></span> | <span data-ttu-id="7ddf6-1615">AnyPolicy를 사용할 수 없음을 나타내는 CA 인증서 필드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1615">CA certificate field indicating that AnyPolicy cannot be used</span></span>                  | <span data-ttu-id="7ddf6-1616">예</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1616">No</span></span>               |

<span data-ttu-id="7ddf6-1617">X.509 확장에 대한 OID 및 매핑</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1617">OIDs and mappings for X.509 Extensions</span></span>

24. <span data-ttu-id="7ddf6-1618">SubjectAltName 확장은 서비스 nx_secure_x509_common_name_dns_check에서 DNS 이름 확인의 일부로 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1618">The SubjectAltName extension is parsed as part of the DNS name check in the service nx_secure_x509_common_name_dns_check.</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1619">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1619">Parameters</span></span>

- <span data-ttu-id="7ddf6-1620">**certificate** 확인할 인증서에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1620">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="7ddf6-1621">**extension** 확장 데이터 포인터 및 길이를 포함하는 반환 구조체입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1621">**extension** Return structure containing extension data pointer and length.</span></span>
- <span data-ttu-id="7ddf6-1622">**extension_id** 위 테이블의 OID 정수 매핑입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1622">**extension_id** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1623">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1623">Return Values</span></span>

- <span data-ttu-id="7ddf6-1624">**NX_SUCCESS**(0x00) 지정된 확장 OID를 찾았으며 데이터가 반환되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1624">**NX_SUCCESS** (0x00) Specified extension OID found and data returned.</span></span>
- <span data-ttu-id="7ddf6-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**(0x181) ASN.1 멀티바이트 태그가 나타났습니다(지원되지 않는 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="7ddf6-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**(0x182) 잘못된 ASN.1 필드가 나타났습니다(잘못된 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="7ddf6-1627">**NX_SECURE_X509_INVALID_TAG_CLASS**(0x190) 잘못된 ASN.1 태그 클래스가 나타났습니다(잘못된 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="7ddf6-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**(0x192) 잘못된 확장이 나타났습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered</span></span>
- <span data-ttu-id="7ddf6-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND**(0x19b) 제공된 인증서에서 지정된 확장 OID를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The given extension OID was not found in the provided certificate.</span></span>
- <span data-ttu-id="7ddf6-1630">**NX_PTR_ERROR** (0x07) 인증서 또는 확장 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1630">**NX_PTR_ERROR** (0x07) Invalid certificate or extension pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1631">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1631">Allowed From</span></span>

<span data-ttu-id="7ddf6-1632">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1632">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1633">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1633">Example</span></span>

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1634">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1634">See Also</span></span>

- <span data-ttu-id="7ddf6-1635">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1635">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="7ddf6-1636">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1636">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="7ddf6-1637">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1637">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="7ddf6-1638">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1638">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="7ddf6-1639">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1639">nx_secure_x509_extended_key_usage_extension_parse</span></span>

## <a name="nx_secure_x509_key_usage_extension_parse"></a><span data-ttu-id="7ddf6-1640">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1640">nx_secure_x509_key_usage_extension_parse</span></span>

<span data-ttu-id="7ddf6-1641">X.509 인증서에서 X.509 키 사용 확장 찾기 및 구문 분석</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1641">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="7ddf6-1642">프로토타입</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1642">Prototype</span></span>

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a><span data-ttu-id="7ddf6-1643">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1643">Description</span></span>

<span data-ttu-id="7ddf6-1644">이 서비스는 인증서 확인 콜백 내에서 호출되어야 합니다(*nx_secure_tls_session_certificate_callback_set* 참조).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1644">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="7ddf6-1645">키 사용 확장을 검색하고, 찾으면 "bitfield" 매개 변수에 키 사용 비트 필드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1645">It will search for the Key Usage extension and if found, will return the Key Usage bitfield in the "bitfield" parameter.</span></span>

<span data-ttu-id="7ddf6-1646">X.509 사양(RFC 5280)에서 정의한 비트는 아래 표에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1646">The bits, as defined by the X.509 specification (RFC 5280) are given in the table below.</span></span> <span data-ttu-id="7ddf6-1647">적절한 비트 마스크(및 값이 0이 아님)가 있는 비트 AND는 각 비트의 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1647">A bitwise AND with the appropriate bitmask (and checking for non-zero) will give the value of each bit.</span></span>

<span data-ttu-id="7ddf6-1648">비트 필드의 DER 인코딩은 불필요한 0을 제거하므로 원시 인증서 데이터의 실제 비트 위치는 디코딩된 비트 필드의 위치와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1648">Note that the DER-encoding of the bitfield eliminates extra zeroes so the actual position of the bits in the raw certificate data will likely be different from their positions in the decoded bitfield.</span></span> <span data-ttu-id="7ddf6-1649">제공된 비트 마스크는 DER로 인코딩된 원시 인증서 데이터가 아닌 nx_secure_x509_key_usage_extension_parse를 통해 반환된 디코딩된 비트 필드에서만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1649">The supplied bitmasks are only intended to be used on the decoded bitfield returned by *nx_secure_x509_key_usage_extension_parse* and not with the raw DER-encoded certificate data.</span></span>

<span data-ttu-id="7ddf6-1650">인증서 확인 콜백에서 오류 반환 코드 NX_SECURE_X509_KEY_USAGE_ERROR가 애플리케이션 사용을 위해 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1650">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="7ddf6-1651">키 사용을 확인하는 동안 오류가 발생하면 콜백에서 이 값을 반환하여 실패 이유를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1651">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="7ddf6-1652">NetX Secure 식별자</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1652">NetX Secure Identifier</span></span>                            | <span data-ttu-id="7ddf6-1653">비트 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1653">Bit position</span></span> | <span data-ttu-id="7ddf6-1654">Description</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1654">Description</span></span>                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="7ddf6-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span></span>  | <span data-ttu-id="7ddf6-1656">0</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1656">0</span></span>            | <span data-ttu-id="7ddf6-1657">디지털 서명에 인증서를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1657">Certificate can be used for digital signatures</span></span>                                                                                                               |
| <span data-ttu-id="7ddf6-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span></span>    | <span data-ttu-id="7ddf6-1659">1</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1659">1</span></span>            | <span data-ttu-id="7ddf6-1660">인증서를 사용하여 인증서 및 CRL에 대한 디지털 서명 이외의 디지털 서명을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1660">Certificate can be used to verify digital signatures other than those for certificates and CRLs</span></span>                                                              |
| <span data-ttu-id="7ddf6-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span></span>   | <span data-ttu-id="7ddf6-1662">2</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1662">2</span></span>            | <span data-ttu-id="7ddf6-1663">인증서를 사용하여 대칭 키(키 전송)를 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1663">Certificate can be used to encrypt symmetric keys (key transport)</span></span>                                                                                            |
| <span data-ttu-id="7ddf6-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span></span>  | <span data-ttu-id="7ddf6-1665">3</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1665">3</span></span>            | <span data-ttu-id="7ddf6-1666">인증서를 사용하여 원시 사용자 데이터를 직접 암호화할 수 있습니다(일반적이지 않음).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1666">Certificate can be used to directly encrypt raw user data (uncommon)</span></span>                                                                                         |
| <span data-ttu-id="7ddf6-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span></span>      | <span data-ttu-id="7ddf6-1668">4</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1668">4</span></span>            | <span data-ttu-id="7ddf6-1669">인증서를 키 규약(Diffie-Hellman과 유사)에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1669">Certificate can be used for key agreement (as with Diffie-Hellman)</span></span>                                                                                           |
| <span data-ttu-id="7ddf6-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span></span>     | <span data-ttu-id="7ddf6-1671">5</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1671">5</span></span>            | <span data-ttu-id="7ddf6-1672">인증서를 사용하여 다른 인증서에 서명하고 확인할 수 있습니다(인증서가 CA 또는 ICA 인증서임).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1672">Certificate can be used to sign and verify other certificates (the certificate is a CA or ICA certificate).</span></span>                                                  |
| <span data-ttu-id="7ddf6-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span></span>           | <span data-ttu-id="7ddf6-1674">6</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1674">6</span></span>            | <span data-ttu-id="7ddf6-1675">인증서 퍼블릭 키를 사용하여 CRL에서 서명을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1675">Certificate public key is used to verify signatures on CRLs</span></span>                                                                                                  |
| <span data-ttu-id="7ddf6-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span></span>      | <span data-ttu-id="7ddf6-1677">7</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1677">7</span></span>            | <span data-ttu-id="7ddf6-1678">키 계약 비트(비트 4)와 함께 사용됩니다. 설정 시, 키 계약 중에 암호화할 때만 인증서 키를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1678">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to encrypt during key agreement.</span></span> <span data-ttu-id="7ddf6-1679">키 계약 비트가 설정되지 않은 경우 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1679">Undefined if Key Agreement bit is not set.</span></span> |
| <span data-ttu-id="7ddf6-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span></span>      | <span data-ttu-id="7ddf6-1681">8</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1681">8</span></span>            | <span data-ttu-id="7ddf6-1682">키 계약 비트(비트 4)와 함께 사용됩니다. 설정 시, 키 계약 중에 암호를 해독할 때만 인증서 키를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1682">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to decrypt during key agreement.</span></span> <span data-ttu-id="7ddf6-1683">키 계약 비트가 설정되지 않은 경우 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1683">Undefined if Key Agreement bit is not set.</span></span> |

<span data-ttu-id="7ddf6-1684">X.509 키 사용 확장에 대한 비트 마스크 및 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1684">Bitmasks and values for X.509 Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="7ddf6-1685">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1685">Parameters</span></span>

- <span data-ttu-id="7ddf6-1686">**certificate** 확인할 인증서에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1686">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="7ddf6-1687">**bitfield** 확장에서 전체 비트 필드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1687">**bitfield** Return the entire bitfield from the extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="7ddf6-1688">반환 값</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1688">Return Values</span></span>

- <span data-ttu-id="7ddf6-1689">**NX_SUCCESS**(0X00) 키 사용 확장을 찾았으며 비트 필드를 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1689">**NX_SUCCESS** (0x00) Key usage extension found and bitfield returned.</span></span>
- <span data-ttu-id="7ddf6-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**(0x181) ASN.1 멀티바이트 태그가 나타났습니다(지원되지 않는 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="7ddf6-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**(0x182) 잘못된 ASN.1 필드가 나타났습니다(잘못된 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="7ddf6-1692">**NX_SECURE_X509_INVALID_TAG_CLASS**(0x190) 잘못된 ASN.1 태그 클래스가 나타났습니다(잘못된 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="7ddf6-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**(0x192) 잘못된 확장이 나타났습니다(잘못된 인증서).</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="7ddf6-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND**(0x19b) 제공된 인증서에서 키 사용 확장을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)The Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="7ddf6-1695">**NX_PTR_ERROR** (0x07) 인증서 또는 비트 필드 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1695">**NX_PTR_ERROR** (0x07) Invalid certificate or bitfield pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7ddf6-1696">허용 위치</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1696">Allowed From</span></span>

<span data-ttu-id="7ddf6-1697">스레드</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7ddf6-1698">예제</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1698">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="7ddf6-1699">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1699">See Also</span></span>

- <span data-ttu-id="7ddf6-1700">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1700">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="7ddf6-1701">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1701">nx_secure_x509_extended_key_usage_extension_parse</span></span>
- <span data-ttu-id="7ddf6-1702">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1702">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="7ddf6-1703">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1703">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="7ddf6-1704">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="7ddf6-1704">nx_secure_x509_extension_find</span></span>
