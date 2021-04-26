---
title: 4장 - Azure RTOS NetX Secure 서비스 설명
description: 이 장에서는 알파벳 순서로 아래 나열된 모든 NetX Secure 서비스에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89761ec3438b1b16c1a603764bf7d4e1eac1b4ea
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811766"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a>4장 - Azure RTOS NetX Secure 서비스 설명

이 장에서는 알파벳 순서로 아래 나열된 모든 Azure RTOS NetX Secure 서비스에 대해 설명합니다.

다음 API 설명의 "반환 값" 섹션에서, **BOLD** 의 값은 API 오류 검사를 해제하는 데 사용되는 **NX_SECURE_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 해제됩니다.

- [nx_secure_crypto_table_self_test](#nx_secure_crypto_table_self_test)
  - 암호화 방법에 대해 self_test 수행
- [nx_secure_module_hash_compute](#nx_secure_module_hash_compute)
  - user_supplied hash 함수를 사용하여 해시 값 계산
- [nx_secure_tls_active_certificate_set](#nx_secure_tls_active_certificate_set)
  - NetX Secure TLS 세션에 대해 활성 ID 인증서 설정
- [nx_secure_tls_client_psk_set](#nx_secure_tls_client_psk_set)
  - NetX Secure TLS 클라이언트 세션에 대해 Pre_Shared 키 설정
- [nx_secure_tls_initialize](#nx_secure_tls_initialize)
  - NetX Secure TLS 모듈 초기화
- [nx_secure_tls_local_certificate_add](#nx_secure_tls_local_certificate_add)
  - NetX Secure TLS 세션에 로컬 인증서 추가
- [nx_secure_tls_local_certificate_find](#nx_secure_tls_local_certificate_find)
  - 일반 이름으로 NetX Secure TLS 세션에서 로컬 인증서 찾기
- [nx_secure_tls_local_certificate_remove](#nx_secure_tls_local_certificate_remove)
  - NetX Secure TLS 세션에서 로컬 인증서 제거
- [nx_secure_tls_metadata_size_calculate](#nx_secure_tls_metadata_size_calculate)
  - NetX Secure TLS 세션의 암호화 메타데이터 크기 계산
- [nx_secure_tls_packet_allocate](#nx_secure_tls_packet_allocate)
  - NetX Secure TLS 세션에 대한 패킷 할당
- [nx_secure_tls_psk_add](#nx_secure_tls_psk_add)
  - NetX Secure TLS 세션에 Pre_Shared 키 추가
- [nx_secure_tls_remote_certificate_allocate](#nx_secure_tls_remote_certificate_allocate)
  - 원격 TLS 호스트에서 제공하는 인증서를 위한 공간 할당
- [nx_secure_tls_remote_certificate_buffer_allocate](#nx_secure_tls_remote_certificate_buffer_allocate)
  - 원격 TLS 호스트에서 제공하는 모든 인증서를 위한 공간 할당
- [nx_secure_tls_remote_certificate_free_all](#nx_secure_tls_remote_certificate_free_all)
  - 수신 인증서에 대해 할당된 사용 가능한 공간
- [nx_secure_tls_server_certificate_add](#nx_secure_tls_server_certificate_add)
  - 숫자 식별자를 사용하여 TLS 서버 전용 인증서 추가
- [nx_secure_tls_server_certificate_find](#nx_secure_tls_server_certificate_find)
  - 숫자 식별자를 사용하여 인증서 찾기
- [nx_secure_tls_server_certificate_remove](#nx_secure_tls_server_certificate_remove)
  - 숫자 식별자를 사용하여 로컬 서버 인증서 제거
- [nx_secure_tls_session_certificate_callback_set](#nx_secure_tls_session_certificate_callback_set)
  - 추가 인증서 유효성 검사에 사용할 TLS에 대한 콜백 설정
- [nx_secure_tls_session_client_callback_set](#nx_secure_tls_session_client_callback_set)
  - TlS가 TLS 클라이언트 핸드셰이크 시작 시 호출할 콜백 설정
- [nx_secure_tls_session_x509_client_verify_configure](#nx_secure_tls_session_x509_client_verify_configure)
  - 클라이언트 X.509 확인을 사용하도록 설정하고 클라이언트 인증서에 대해 공간 할당
- [nx_secure_tls_session_client_verify_disable](#nx_secure_tls_session_client_verify_disable)
  - NetX Secure TLS 세션에 대해 클라이언트 인증서 인증를 사용하지 않도록 설정
- [nx_secure_tls_session_client_verify_enable](#nx_secure_tls_session_client_verify_enable)
  - NetX Secure TLS 세션에 대해 클라이언트 인증서 인증를 사용하도록 설정
- [nx_secure_tls_session_create](#nx_secure_tls_session_create)
  - 보안 통신용 NetX Secure TLS 세션 만들기
- [nx_secure_tls_session_delete](#nx_secure_tls_session_delete)
  - NetX Secure TLS 세션 삭제
- [nx_secure_tls_session_end](#nx_secure_tls_session_end)
  - 활성 NetX Secure TLS 세션 종료
- [nx_secure_tls_session_packet_buffer_set](#nx_secure_tls_session_packet_buffer_set)
  - NetX Secure TLS 세션에 대한 패킷 리어셈블리 버퍼 설정
- [nx_secure_tls_session_protocol_version_override](#nx_secure_tls_session_protocol_version_override)
  - NetX Seure TLS 세션의 기본 TLS 프로토콜 버전 재정의
- [nx_secure_tls_session_receive](#nx_secure_tls_session_receive)
  - NetX Secure TLS 세션에서 데이터 받기
- [nx_secure_tls_session_renegotiate_callback_set](#nx_secure_tls_session_renegotiate_callback_set)
  - 세션 다시 협상을 시작할 때 호출될 콜백 할당
- [nx_secure_tls_session_renegotiate](#nx_secure_tls_session_renegotiate)
  - 원격 호스트와의 세션 재협상 핸드셰이크 시작
- [nx_secure_tls_session_reset](#nx_secure_tls_session_reset)
  - NetX Secure TLS 세션 지우기 및 다시 설정
- [nx_secure_tls_session_send](#nx_secure_tls_session_send)
  - NetX Secure TLS 세션을 통해 데이터 보내기
- [nx_secure_tls_session_server_callback_set](#nx_secure_tls_session_server_callback_set)
  - TlS가 TLS 서버 핸드셰이크 시작 시 호출할 콜백 설정
- [nx_secure_tls_session_sni_extension_parse](#nx_secure_tls_session_sni_extension_parse)
  - TLS 클라이언트에서 받은 SNI(서버 이름 표시) 확장 구문 분석
- [nx_secure_tls_session_sni_extension_set](#nx_secure_tls_session_sni_extension_set)
  - 원격 서버로 전송할 SNI(서버 이름 표시) 확장 DNS 이름 설정
- [nx_secure_tls_session_start](#nx_secure_tls_session_start)
  - NetX Secure TLS 세션 시작
- [nx_secure_tls_session_time_function_set](#nx_secure_tls_session_time_function_set)
  - NetX Secure TLS 세션에 타임스탬프 함수 할당
- [nx_secure_tls_trusted_certificate_add](#nx_secure_tls_trusted_certificate_add)
  - NetX Secure TLS 세션에 신뢰할 수 있는 인증서 추가
- [nx_secure_tls_trusted_certificate_remove](#nx_secure_tls_trusted_certificate_remove)
  - NetX Secure TLS 세션에서 신뢰할 수 있는 인증서 제거
- [nx_secure_x509_certificate_initialize](#nx_secure_x509_certificate_initialize)
  - NetX Secure TLS에 대한 X.509 인증서 초기화
- [nx_secure_x509_common_name_dns_check](#nx_secure_x509_common_name_dns_check)
  - X.509 인증서에서 DNS 이름 확인
- [nx_secure_x509_crl_revocation_check](#nx_secure_x509_crl_revocation_check)
  - 제공된 CRL(인증서 해지 목록)에서 X.509 인증서 확인
- [nx_secure_x509_dns_name_initialize](#nx_secure_x509_dns_name_initialize)
  - X.509 DNS 이름 구조 초기화
- [nx_secure_x509_extended_key_usage_extension_parse](#nx_secure_x509_extended_key_usage_extension_parse)
  - X.509 인증서에서 X.509 확장 키 사용 확장 찾기 및 구문 분석
- [nx_secure_x509_extension_find](#nx_secure_x509_extension_find)
  - X.509 인증서에서 X.509 확장 찾기 및 반환
- [nx_secure_x509_key_usage_extension_parse](#nx_secure_x509_key_usage_extension_parse)
  - X.509 인증서에서 X.509 키 사용 확장 찾기 및 구문 분석

## <a name="nx_secure_crypto_table_self_test"></a>nx_secure_crypto_table_self_test

암호화 방법에 대한 자체 테스트 수행

### <a name="prototype"></a>프로토타입

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a>Description

이 서비스는 유효성을 검사하기 위한 암호화 방법 자체 테스트를 통해 실행됩니다. 자체 테스트는 NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK 기호를 정의한 상태로 NetX Secure 라이브러리를 빌드한 경우에만 사용할 수 있습니다.

지원되는 각 암호화 방법에 대해 자체 테스트는 미리 정의된 입력 데이터를 제공하고 출력이 미리 정의된 예상 값과 일치하는지 확인합니다.

NetX Secure 암호화 자체 테스트는 다음 알고리즘 및 키 크기를 지원합니다.

- DES: 암호화 및 암호 해독
- 3DES(Triple DES): 암호화 및 암호 해독
- AES: CBC 모드 및 카운터 모드에서 128, 192, 256비트 키 크기, 암호화 및 암호 해독
- HMAC-MD5: 인증 및 해시 계산
- HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, 인증 및 해시 계산
- MD5: 인증
- PRF(의사 난수 함수): PRF_HMAC_SHA1 및 PRF_HMAC_SHA2-256
- RSA: 1024, 2048, 4096비트 RSA 전원-모듈러스 작업
- SHA: SHA1(96비트 및 160비트), SHA2(256비트, 384비트, 512비트) 인증

이 함수에는 위에 나열된 암호화 알고리즘에 대한 기본 제공 벡터가 있습니다. 그러나 이 함수에 전달된 *cipher_table* 에 나열된 항목만 테스트합니다. 예를 들어, TLS 세션의 경우는 암호 그룹 TLS_RSA_WITH_AES_128_CBC_SHA만 사용합니다. 이 함수는 RSA(1024, 2048, 4096비트), AES-CBC(128비트) 및 SHA1에서 자체 테스트를 수행합니다.

### <a name="parameters"></a>매개 변수

- **crypto_table** TLS 세션에서 사용 중인 암호화 테이블에 대한 포인터입니다. 이것은 **_nx_secure_tls_session_create()_** 호출에 전달되는 것과 동일한 crypto_table입니다.
- **metadata** 암호화 메타데이터 영역 공간에 대한 포인터입니다. .
- **crypto_metadata_size** 메타데이터 버퍼의 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SECURE_TLS_SUCCESS**(0x00) 제공된 암호화 방법을 테스트했습니다.
- **NX_PTR_ERROR**(0X07) 잘못된 암호화 방법 구조
- **NX_NOT_SUCCESSFUL**(0x43) 암호화 자체 테스트가 실패합니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

사용자 제공 해시 함수를 사용하여 해시 값 계산

### <a name="prototype"></a>프로토타입

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a>Description

이 함수는 제공된 HMAC 암호화 방법과 키 문자열을 사용하여 지정된 메모리 영역에 있는 데이터 스트림의 해시 값을 계산합니다. 모듈 해시 계산 함수는 NetX Secure 라이브러리가 NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK 기호를 정의하여 빌드된 경우에만 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **hmac_ptr** 해시 값 계산에 사용되는 HMAC 암호화 방법에 대한 포인터입니다.
- **start_address** 데이터 버퍼의 시작 주소입니다.
- **end_address** 데이터 버퍼의 끝 주소입니다. 해시 계산은 이 end_address의 데이터를 포함하지 않습니다.
- **key** HMAC 계산에 사용되는 키 문자열입니다.
- **key_length** 문자열의 크기(바이트)입니다.
- **metadata** HMAC 알고리즘에서 사용하는 공간에 대한 포인터입니다.
- **crypto_metadata_size** 메타데이터 버퍼의 크기입니다.
- **output_buffer** 해시 출력이 저장되는 메모리 위치입니다.
- **output_buffer_size** 출력 버퍼의 사용 가능한 공간(바이트)입니다.
- **actual_size** output_buffer에 기록되는 실제 바이트 수를 나타내는 함수에서 반환됩니다.

### <a name="return-values"></a>반환 값

- **0** 해시 값을 계산했습니다.
- **1** 해시 계산에 실패했습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_crypto_method_self_test

## <a name="nx_secure_tls_active_certificate_set"></a>nx_secure_tls_active_certificate_set

NetX Secure TLS 세션에 대해 활성 ID 인증서 설정

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Description

이 서비스는 세션 콜백 내에서 호출됩니다(nx_secure_tls_session_client_callback_set 및 nx_secure_tls_session_server_callback_set 참조). 이전에 초기화된 NX_SECURE_X509_CERT 구조체를 사용하여 호출하는 경우 기본 ID 인증서 대신 해당 인증서가 사용됩니다. 대부분의 경우 인증서를 로컬 저장소에 추가해야 합니다(nx_secure_tls_local_certificate_add 참조). 그러지 않으면 TLS 핸드셰이크가 실패할 수 있습니다.

이 서비스는 TLS에서 여러 ID 인증서를 지원할 수 있도록 하기 위해 고안되었습니다. 이 서비스는 여러 네트워크 주소를 제공하는 TLS 서버에 유용합니다. 이러한 서버는 클라이언트의 진입점에 따라 원격 클라이언트에 제공할 적절한 인증서를 선택할 수 있기 때문입니다. TLS 클라이언트의 경우 이 루틴을 사용하여 서버가 TLS 핸드셰이크에서 자신을 식별한 후에 런타임에 원격 서버로 전송되는 인증서를 변경할 수 있습니다(TLS 서버 사용 사례보다 더 드문 경우).

여러 인증서가 동일한 X.509 고유 이름을 공유할 수 있는 경우 인증서와는 별개인 숫자 식별자를 도입하는 nx_secure_tls_server_certificate_add를 사용하여 인증서를 추가해야 합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 세션 콜백에 전달되는 TLS 세션 인스턴스에 대한 포인터입니다.
- **certificate** 현재 세션에 사용할 초기화된 X.509 인증서에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 세션에 인증서를 할당했습니다.
- **NX_PTR_ERROR**(0X07) 잘못된 TLS 세션 또는 인증서 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_client_psk_set"></a>nx_secure_tls_client_psk_set

NetX Secure TLS 클라이언트 세션에 대해 미리 공유한 키 설정

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a>Description

이 서비스는 PSK(미리 공유한 키), 해당 ID 문자열 및 ID 힌트를 TLS 세션 제어 블록에 추가하고, 해당 PSK를 후속 TLS 클라이언트 연결에서 사용하도록 설정합니다. PSK는 PSK 암호 그룹을 설정하고 사용할 때 디지털 인증서 대신 사용됩니다.

이 경우 PSK는 TLS 클라이언트가 통신하려는 특정 원격 TLS 서버와 연결됩니다. 이 API를 통해 설정된 PSK는 다음 TLS 핸드셰이크 중에 원격 TLS 서버 호스트에 제공됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **pre_shared_key** 실제 PSK 값입니다.
- **psk_length** PSK 값의 길이입니다.
- **psk_identity** 이 PSK 값을 식별하는 데 사용되는 문자열입니다.
- **identity_length** PSK ID의 길이입니다.
- **hint** TLS 서버에서 선택할 PSK 그룹을 나타내는 데 사용되는 문자열입니다.
- **hint_length** 힌트 문자열의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) PSK를 추가했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE**(0x125) 다른 PSK를 추가할 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_tls_psk_add
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_initialize"></a>nx_secure_tls_initialize

NetX Secure TLS 모듈 초기화

### <a name="prototype"></a>프로토타입

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a>Description

이 서비스는 NetX Secure TLS 모듈을 초기화합니다. 다른 NetX Secure 서비스에 액세스하려면 먼저 이 서비스를 호출해야 합니다.

### <a name="parameters"></a>매개 변수

없음

### <a name="return-values"></a>반환 값

없음

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create

## <a name="nx_secure_tls_local_certificate_add"></a>nx_secure_tls_local_certificate_add

NetX Secure TLS 세션에 로컬 인증서 추가

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Description

이 서비스는 초기화된 NX_SECURE_X509_CERT 구조체 인스턴스를 TLS 세션의 로컬 저장소에 추가합니다. 이 인증서는 nx_secure_x509_certificate_initialize를 사용하여 인증서 구조를 초기화하는 동안 ID 인증서로 표시되었거나 TLS 핸드셰이크 중에 원격 호스트에 제공되는 인증서 체인의 일부로 발급자로서 표시된 경우 TLS 스택에서 TLS 핸드셰이크 중에 디바이스를 식별하는 데 사용할 수 있습니다.

동일한 일반 이름을 가진 여러 로컬 인증서가 필요한 경우 *nx_secure_tls_server_certificate_add* 서비스를 사용하여 인증서를 추가할 수 있습니다(아래 경고 참조).

TLS 서버 모드에서는 인증서가 **필수** 입니다.

TLS 클라이언트 모드에서는 인증서가 *선택 사항* 입니다.

> [!IMPORTANT]
> 를 사용하는 경우 이 API를 동일한 TLS 세션에서 사용하면 안 됩니다. 서버 인증서 API는 X.509 일반 이름에 따라 각 인증서에 대한 고유한 숫자 식별자 및 nx_secure_tls_local_certificate_add 인덱스를 사용합니다. 로컬 인증서 서비스는 단일 ID 인증서만 사용하는 애플리케이션에 숫자 식별자에 대한 편리한 대안을 제공합니다. 즉, 일반적인 이름을 사용하면 애플리케이션에서 숫자 식별자를 추적하지 않아도 됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **certificate_ptr** 초기화된 TLS 인증서 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인증서를 추가했습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 잘못되었거나 중복된 인증서를 추가하려고 했습니다.
- **NX_PTR_ERROR**(0X07) 잘못된 TLS 세션 또는 인증서 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_find

## <a name="nx_secure_tls_local_certificate_find"></a>nx_secure_tls_local_certificate_find

일반 이름으로 NetX Secure TLS 세션에서 로컬 인증서 찾기

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a>Description

이 서비스는 TLS 세션의 로컬 디바이스 인증서 저장소에서 인증서를 찾고, 저장소의 NX_SECURE_X509_CERT 구조체에 대한 포인터를 반환합니다. common_name 매개 변수 및 해당 길이(name_length)는 인증서의 X.509 주체 일반 이름 필드와 일치시켜 저장소에서 인증서를 식별하는 데 사용됩니다.

동일한 일반 이름을 가진 인증서가 두 개 이상 있는 경우 첫 번째 인증서만 반환됩니다. 대신 *nx_secure_tls_server_certificate_find* 를 사용합니다.

> [!IMPORTANT]
> 를 사용하는 경우 이 API를 동일한 TLS 세션에서 사용하면 안 됩니다. 서버 인증서 API는 X.509 일반 이름에 따라 각 인증서에 대한 고유한 숫자 식별자 및 nx_secure_tls_local_certificate_add 인덱스를 사용합니다. 로컬 인증서 서비스는 단일 ID 인증서만 사용하는 애플리케이션에 숫자 식별자에 대한 편리한 대안을 제공합니다. 즉, 일반적인 이름을 사용하면 애플리케이션에서 숫자 식별자를 추적하지 않아도 됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **certificate** 일치하는 인증서에 대한 포인터를 반환합니다.
- **common_name** 일치시킬 일반 이름 문자열(DNS 이름)입니다.
- **common_name_length** common_name 문자열 데이터의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인증서를 찾았으며 "certificate" 매개 변수에서 포인터가 반환되었습니다.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0x119) 제공된 일반 이름을 가진 인증서를 찾을 수 없습니다.
- **NX_PTR_ERROR**(0X07) 잘못된 TLS 세션, 인증서 포인터 또는 일반 이름 문자열입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_local_certificate_remove"></a>nx_secure_tls_local_certificate_remove

NetX Secure TLS 세션에서 로컬 인증서 제거

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a>Description

이 서비스는 인증서의 일반 이름 필드에 입력된 TLS 세션에서 로컬 인증서 인스턴스를 제거합니다.

> [!IMPORTANT]
> 를 사용하는 경우 이 API를 동일한 TLS 세션에서 사용하면 안 됩니다. 서버 인증서 API는 X.509 일반 이름에 따라 각 인증서에 대한 고유한 숫자 식별자 및 nx_secure_tls_local_certificate_add 인덱스를 사용합니다. 로컬 인증서 서비스는 단일 ID 인증서만 사용하는 애플리케이션에 숫자 식별자에 대한 편리한 대안을 제공합니다. 즉, 일반적인 이름을 사용하면 애플리케이션에서 숫자 식별자를 추적하지 않아도 됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **common_name** 제거할 인증서의 일반 이름 값입니다.
- **common_name_length** 일반 이름 문자열의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인증서를 추가했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0x119) 인증서를 찾을 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_metadata_size_calculate"></a>nx_secure_tls_metadata_size_calculate

NetX Secure TLS 세션의 암호화 메타데이터 크기 계산

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a>Description

이 서비스는 특정 TLS 세션 및 TLS 암호화 테이블에 필요한 암호화 메타데이터의 크기를 계산하고 반환합니다(암호화 테이블에 대한 자세한 내용은 "암호화 방법으로 TLS 초기화" 섹션 참조).

nx_secure_tls_session_create에 전달되는 메타데이터 버퍼의 크기를 계산하려면 원하는 암호화 테이블을 사용하여 이 서비스를 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **crypto_table** 전체 NetX Secure TLS 암호화 테이블에 대한 포인터입니다.
- **metadata_size** 크기 계산의 출력(바이트)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 메타데이터 크기를 계산했습니다.
- **NX_PTR_ERROR**(0X07) 잘못된 암호화 테이블 또는 반환 크기 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

NetX Secure 라이브러리 루틴의 해시 값 계산

### <a name="prototype"></a>프로토타입

```C
VOID nx_secure_module_hash_compute(VOID);
```

### <a name="description"></a>Description

이 서비스는 NetX Secure TLS 모듈을 초기화합니다. 다른 NetX Secure 서비스에 액세스하려면 먼저 이 서비스를 호출해야 합니다.

### <a name="parameters"></a>매개 변수

없음

### <a name="return-values"></a>반환 값

없음

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create

## <a name="nx_secure_tls_packet_allocate"></a>nx_secure_tls_packet_allocate

NetX Secure TLS 세션에 대한 패킷 할당

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 NX_PACKET_POOL의 지정된 활성 TLS 세션에 대한 NX_PACKET을 할당합니다. 애플리케이션에서 이 서비스를 호출하여 TLS 연결을 통해 보낼 데이터 패킷을 할당해야 합니다. 이 서비스를 호출하려면 먼저 TLS 세션을 초기화해야 합니다.

패킷 데이터가 채워진 후 TLS 머리글 및 바닥글 데이터를 추가할 수 있도록 할당된 패킷이 올바르게 초기화됩니다. 그렇지 않으면 이 동작은 *nx_packet_allocate* 와 동일합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **pool_ptr** 패킷을 할당할 NX_PACKET_POOL에 대한 포인터입니다.
- **packet_ptr** 새로 할당된 패킷에 대한 출력 포인터입니다.
- **wait_option** 패킷 할당의 일시 중단 옵션입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷을 할당했습니다.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**(0x111) 기본 패킷을 할당하지 못했습니다.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED**(0x101) 제공된 TLS 세션이 초기화되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_psk_add"></a>nx_secure_tls_psk_add

NetX Secure TLS 세션에 미리 공유한 키 추가

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Description

이 서비스는 PSK(미리 공유한 키), 해당 ID 문자열 및 ID 힌트를 TLS 세션 제어 블록에 추가합니다. PSK는 PSK 암호 그룹을 설정하고 사용할 때 디지털 인증서 대신 사용됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **pre_shared_key** 실제 PSK 값입니다.
- **psk_length** PSK 값의 길이입니다.
- **psk_identity** 이 PSK 값을 식별하는 데 사용되는 문자열입니다.
- **identity_length** PSK ID의 길이입니다.
- **hint** TLS 서버에서 선택할 PSK 그룹을 나타내는 데 사용되는 문자열입니다.
- **hint_length** 힌트 문자열의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) PSK를 추가했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE**(0x125) 다른 PSK를 추가할 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_tls_client_psk_set
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_remote_certificate_allocate"></a>nx_secure_tls_remote_certificate_allocate

원격 TLS 호스트에서 제공하는 인증서를 위한 공간 할당

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a>Description

이 서비스는 TLS 세션 중에 원격 호스트에서 제공하는 인증서를 위한 공간을 할당하기 위해 초기화되지 않은 NX_SECURE_X509_CERT 구조체 인스턴스를 TLS 세션에 추가합니다. 원격 인증서 데이터는 NetX Secure TLS에서 구문 분석되며 해당 정보는 이 함수에 제공된 인증서 구조 인스턴스를 채우는 데 사용됩니다. 이러한 방식으로 추가된 인증서는 연결된 목록에 배치됩니다.

원격 호스트가 여러 인증서를 제공할 것으로 예상되는 경우 이 함수를 반복적으로 호출하여 모든 인증서에 대한 공간을 할당해야 합니다. 인증서 연결 목록의 끝에 추가 인증서가 추가됩니다.

PSK(미리 공유한 키) 암호 그룹이 사용되고 있지 않을 경우 원격 인증서를 할당하지 못하므로 TLS 핸드셰이크 동안 TLS 클라이언트 모드가 실패합니다.

*raw_certificate_buffer* 매개 변수는 수신 원격 인증서를 저장하기 위해 할당된 공간을 가리킵니다. 서명에 대해 SHA-256을 사용하는 2048비트의 RSA 키를 포함하는 일반적인 인증서의 범위는 1000-2000바이트입니다. 버퍼는 적어도 해당 크기를 보유할 수 있을 만큼 커야 하지만 원격 호스트 인증서에 따라 훨씬 더 작거나 클 수 있습니다. 버퍼가 너무 작아서 수신 인증서를 저장할 수 없는 경우 TLS 핸드셰이크는 오류를 발생하면서 종료됩니다.

TLS 서버 모드의 경우에는 클라이언트 인증서 인증을 사용하도록 설정한 경우에만 원격 인증서를 할당해야 합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **certificate_ptr** 초기화되지 않은 X.509 인증서 인스턴스에 대한 포인터입니다.
- **raw_certificate_buffer** 원격 호스트에서 받은 구문 분석되지 않은 인증서를 저장할 버퍼에 대한 포인터입니다.
- **raw_buffer_size** 원시 인증서 버퍼의 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인증서를 할당했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**(0x12D) 제공된 버퍼가 너무 작습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 잘못된 인증서를 추가하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize,
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a>nx_secure_tls_remote_certificate_buffer_allocate

원격 TLS 호스트에서 제공하는 모든 인증서를 위한 공간 할당

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Description

이 서비스는 TLS 클라이언트 인스턴스에서 X.509 인증 및 검증을 수행하기 위해 원격 서버 호스트에서 수신 인증서 체인을 처리하기 위한 공간을 할당합니다. TLS 서버 모드의 경우 클라이언트 X.509 인증서 인증을 사용하도록 설정하는 경우에만 원격 인증서를 할당해야 합니다. TLS 서버 인스턴스의 경우 서비스 *nx_secure_tls_session_x509_client_verify_configure* 를 대신 사용해야 합니다.

PSK(미리 공유한 키) 암호 그룹이 사용되고 있지 않을 경우 원격 인증서를 할당하지 못하므로 TLS 핸드셰이크 동안 TLS 클라이언트 모드가 실패합니다.

*certificate_buffer* 매개 변수는 수신 원격 인증서 및 해당 인증서에 필요한 제어 블록을 저장하기 위해 할당된 공간을 가리킵니다. 버퍼는 각 인증서에 지정된 것과 같은 부분이 있는 인증서 수(*certs_number*)로 나뉩니다. *buffer_size* 매개 변수는 버퍼의 크기를 나타냅니다. 필요한 공간은 다음 수식을 사용하여 구할 수 있습니다.

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

서명에 대해 SHA-256을 사용하는 2048비트의 RSA 키를 포함하는 일반적인 인증서의 범위는 1000-2000바이트입니다. 버퍼는 적어도 각 인증서에 대한 해당 크기를 보유할 수 있을 만큼 커야 하지만 원격 호스트 인증서에 따라 훨씬 더 작거나 클 수 있습니다. 버퍼가 너무 작아서 수신 인증서를 저장할 수 없는 경우 TLS 핸드셰이크는 오류를 발생하면서 종료됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **certs_number** 제공된 버퍼에서 할당할 인증서의 수입니다.
- **certificate_buffer** 원격 호스트에서 받은 인증서를 저장할 버퍼에 대한 포인터입니다.
- **buffer_size** 인증서 버퍼의 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인증서를 할당했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 또는 버퍼 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**(0x12D) 제공된 버퍼가 너무 작습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 버퍼가 너무 작아서 원하는 수의 인증서를 보유할 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_free_all"></a>nx_secure_tls_remote_certificate_free_all

수신 인증서에 대해 할당된 사용 가능한 공간

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

이 서비스는 nx_secure_tls_remote_certificate_allocated를 통해 특정 TLS 세션에 할당된 모든 인증서 버퍼를 해당 세션의 사용 가능한 인증서 공간으로 반환하여 사용 가능한 상태로 해제하는 데 사용됩니다. 이 서비스가 있으면 애플리케이션은 nx_secure_tls_session_delete 및 nx_secure_tls_session_create를 사용하여 TLS 세션 개체를 삭제했다가 다시 만들 필요가 없이, TLS 세션 개체를 다시 사용할 수 있습니다.

nx_secure_tls_session_end에서 수행되는 것처럼 TLS 세션이 다시 설정될 때 원격 인증서 공간이 자동으로 복구되므로 대부분의 애플리케이션은 이 서비스를 호출할 필요가 없습니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 작업에 성공했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 내부 오류 – 인증서 저장소가 손상되었을 수 있습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_end

## <a name="nx_secure_tls_server_certificate_add"></a>nx_secure_tls_server_certificate_add

숫자 식별자를 사용하여 TLS 서버 전용 인증서 추가

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a>Description

이 서비스는 인증서 내에서 X.509 주체(일반 이름)를 사용하여 저장소를 인덱싱하는 대신, 숫자 식별자를 사용하여 TLS 세션의 로컬 저장소에 인증서를 추가하는 데 사용됩니다(nx_secure_tls_local_certificate_add 참조). 숫자 식별자는 인증서와 별개이며 여러 인증서를 TLS 서버에 ID 인증서로 추가할 수 있으며 동일한 일반 이름을 가진 여러 인증서를 동일한 TLS 세션 로컬 저장소에 추가할 수 있습니다. 이러한 동일한 서비스를 클라이언트 인증서에 사용할 수 있지만 TLS 클라이언트에 여러 개의 ID 인증서가 있는 경우는 거의 없습니다.

cert_id 매개 변수는 애플리케이션에서 할당된 0이 아닌 양의 정수입니다. 실제 값은 중요하지 않지만(0이 아님) 제공된 TLS 세션의 저장소에서 고유해야 합니다. cert_id 값은 nx_secure_tls_server_certificate_find 및 nx_secure_tls_server_certificate_remove를 사용하여 로컬 저장소에서 인증서를 찾아 제거하는 데 사용할 수 있습니다.

> [!IMPORTANT]
> nx_secure_tls_local_certificate_add를 사용하는 경우 이 API는 동일한 TLS 세션에서 사용하면 안 됩니다. nx_secure_tls_server_certificate_add API는 각 인증서에 고유한 숫자 식별자를 사용하고 X.509 일반 이름에 따라 로컬 인증서 서비스 인덱스를 사용합니다. 서버 인증서 서비스를 사용하면 공유 데이터(특히 일반 이름)가 포함된 여러 인증서가 동일한 로컬 저장소에 있을 수 있습니다. 이러한 특성은 여러 ID가 있는 서버에 유용합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **certificate** 이전에 초기화된 X.509 인증서 인스턴스에 대한 포인터입니다.
- **cert_id** 0이 아닌 양수로 나타낸 상대적으로 고유한 인증서 ID 번호입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 작업에 성공했습니다.
- **NX_PTR_ERROR**(0X07) 잘못된 TLS 세션 또는 인증서 포인터입니다.
- **NX_SECURE_TLS_CERT_ID_INVALID**(0x138) 제공된 인증서 ID의 값(0일 수 있음)이 잘못되었습니다.
- **NX_SECURE_TLS_CERT_ID_DUPLICATE**(0x139) 제공된 인증서 ID가 로컬 저장소에 이미 있습니다.
- **NX_INVALID_PARAMETERS(0x4D)** 내부 오류 – 인증서 저장소가 손상되었을 수 있습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_server_certificate_find"></a>nx_secure_tls_server_certificate_find

숫자 식별자를 사용하여 인증서 찾기

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a>Description

이 서비스는 인증서 내에서 X.509 주체(일반 이름)를 사용하여 저장소를 인덱싱하는 대신, 숫자 식별자를 사용하여 TLS 세션의 로컬 저장소에서 인증서를 찾는 데 사용됩니다(nx_secure_tls_local_certificate_add 참조).

cert_id 매개 변수는 nx_secure_tls_server_certificate_add를 사용하여 TLS 세션 로컬 저장소에 인증서를 추가할 때 애플리케이션에서 할당하는 0이 아닌 양의 정수입니다.

> [!IMPORTANT]
> nx_secure_tls_local_certificate_add를 사용하는 경우 이 API는 동일한 TLS 세션에서 사용하면 안 됩니다. nx_secure_tls_server_certificate_add API는 각 인증서에 고유한 숫자 식별자를 사용하고 X.509 일반 이름에 따라 로컬 인증서 서비스 인덱스를 사용합니다. 서버 인증서 서비스를 사용하면 공유 데이터(특히 일반 이름)가 포함된 여러 인증서가 동일한 로컬 저장소에 있을 수 있습니다. 이러한 특성은 여러 ID가 있는 서버에 유용합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **certificate** 찾은 인증서에 대한 참조를 반환하는 X.509 인증서 포인터에 대한 포인터입니다.
- **cert_id** 0이 아닌 양의 인증서 ID 값입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 작업에 성공했습니다.
- **NX_PTR_ERROR**(0X07) 잘못된 TLS 세션 또는 인증서 포인터입니다.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0x119) 제공된 인증서 ID가 제공된 TLS 세션의 로컬 저장소의 ID와 일치하지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_remove

##  <a name="nx_secure_tls_server_certificate_remove"></a>nx_secure_tls_server_certificate_remove

숫자 식별자를 사용하여 로컬 서버 인증서 제거

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a>Description

이 서비스는 인증서 내에서 X.509 주체(일반 이름)를 사용하여 저장소를 인덱싱하는 대신, 숫자 식별자를 사용하여 TLS 세션에서 저장소를 제거하는 데 사용됩니다(nx_secure_tls_local_certificate_add 참조).

cert_id 매개 변수는 nx_secure_tls_server_certificate_add를 사용하여 TLS 세션 로컬 저장소에 인증서를 추가할 때 애플리케이션에서 할당하는 0이 아닌 양의 정수입니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **cert_id** 0이 아닌 양의 인증서 ID 값입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 작업에 성공했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션이 올바르지 않습니다.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0x119) 제공된 인증서 ID가 제공된 TLS 세션의 로컬 저장소의 ID와 일치하지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_alert_value_get"></a>nx_secure_tls_session_alert_value_get

원격 호스트가 보낸 TLS 경고 값 및 수준 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a>Description

이 서비스는 원격 호스트가 일부 문제나 오류에 대한 응답으로 경고를 보낼 때 TLS 경고 수준 및 값을 검색하는 데 사용됩니다.

alert_level 및 alert_value 매개 변수의 값은 원격 호스트에서 경고가 수신되었음을 나타내는 NX_SECURE_TLS_ALERT_RECEIVED(0x114) 상태를 반환하는 TLS API 호출 바로 다음에 이 함수가 호출되는 경우에만 유효합니다.

로컬 호스트 TLS에서 경고를 보내는 경우 반환되는 오류 코드는 TLS 경고 자체보다 실제 오류에 대한 설명을 포함합니다. 특정 유형의 공격을 방지하기 위해 TLS 경고 값은 의도적으로 모호하게 표시되기 때문입니다(예: "오라클 패딩" 공격 또는 유사한 공격).

경고 수준에는 NX_SECURE_TLS_ALERT_LEVEL_WARNING(0x1) 또는 NX_SECURE_TLS_ALERT_LEVEL_FATAL(0x2)의 두 값 중 하나만 사용됩니다. 일반적으로 일부 확장 구성 상황도 경고로 간주될 수 있지만 CloseNotify 경고(TLS 세션의 성공적인 종료를 표시하는 데 사용됨)에만 "경고" 수준이 지정됩니다. 대부분의 경고는 잠재적인 보안 오류를 나타내는 "치명적"이며 TLS 연결(핸드셰이크 또는 세션)은 즉시 종료됩니다.

TLS 경고 값은 TLS RFC에 정의되어 있습니다. 다음은 참조용으로 제공되는 RFC 5246(TLSv 1.2)의 목록입니다.

| 경고 이름                     | 값 | Description                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| close_notify                  | 0     | 오류 없음, 성공한 세션 종료 표시                                                                                                                   |
| unexpected_message            | 10    | TLS에서 예기치 않았거나 순서가 잘못된 메시지를 받았습니다.                                                                                                           |
| bad_record_mac               | 20    | 암호 해독 및/또는 MAC 확인이 실패했습니다.                                                                                                                    |
| decryption_failed_RESERVED   | 21    | **DEPRECATED** 암호 해독이 실패했습니다(오라클 패딩 공격으로 인해 더 이상 사용되지 않음).                                                                                      |
| record_overflow               | 22    | TLS 최대 레코드 크기보다 큰 레코드를 수신했습니다.                                                                                        |
| decompression_failure         | 30    | TLS 레코드 압축/압축 해제에서 문제가 발생했습니다.                                                                                       |
| handshake_failure             | 40    | 다른 경고에 해당되지 않는 일부 지정되지 않은 핸드셰이크 오류가 발생했습니다.                                                                            |
| no_certificate_RESERVED      | 41    | TLS에서 **더 이상 사용되지 않습니다**(SSL만 해당).                                                                                                                                 |
| bad_certificate               | 42    | 받은 인증서에 잘못된 서식 또는 서명이 포함되어 있습니다.                                                                                   |
| unsupported_certificate       | 43    | 잘못된 형식의 인증서를 받았습니다(예: TLS 서버 인증에 사용되는 서명 전용 인증서).                                    |
| certificate_revoked           | 44    | CRL 또는 OCSP에서 제공한 인증서 상태가 "해지됨"으로 표시되었습니다.                                                                       |
| certificate_expired           | 45    | 받은 인증서가 유효한 날짜 범위를 벗어났습니다(유효하지 않거나 만료됨).                                                                 |
| certificate_unknown           | 46    | 다른 경고에 해당되지 않는 일부 알 수 없는 인증서 문제가 발생했습니다.                                                                          |
| illegal_parameter             | 47    | TLS 핸드셰이크의 일부 구성 또는 협상된 값이 잘못되었거나 범위를 벗어났습니다.                                                                      |
| unknown_ca                    | 48    | 받은 ID 인증서를 신뢰할 수 있는 루트 CA 인증서에 대한 인증서 체인을 통해 추적할 수 없습니다.                                              |
| access_denied                 | 49    | 유효한 인증서를 받았지만 애플리케이션 액세스 제어에서 인증서가 요청된 리소스에 대해 유효하지 않음을 나타냅니다.            |
| decode_error                  | 50    | TLS 헤더 또는 핸드셰이크 메시지의 일부 필드 또는 값이 범위를 벗어났거나 올바르지 않으므로 TLS 레코드를 디코딩하는 데 실패했습니다.                      |
| decrypt_error                 | 51    | TLS 핸드셰이크 중에 서명 또는 완료된 메시지 해시를 확인할 수 없습니다.                                                                         |
| export_restriction_RESERVED  | 60    | TLSv 1.2에서 더 이상 사용되지 않습니다.                                                                                                                                        |
| protocol_version              | 70    | 핸드셰이크 동안 협상된 TLS 프로토콜 버전이 인식되지만 지원되지 않습니다(예: TLSv 1.0이 제공되었지만 사용하도록 설정되지 않음).                       |
| insufficient_security         | 71    | 보안 암호화가 부족하여 핸드셰이크가 실패할 때마다 전송됩니다(예: 애플리케이션 요구 사항에 비해 키 크기가 너무 작음).                                |
| internal_error                | 80    | 일부 TLS 이외의 오류(예: 메모리 할당 문제, 애플리케이션 문제)가 발생하여 TLS 세션이 손상되었습니다.                                         |
| user_canceled                 | 90    | 핸드셰이크가 완료되기 전에 사용자 또는 애플리케이션이 TLS 세션을 취소하는 경우 반환됩니다(CloseNotify와 유사).                                 |
| no_renegotiation              | 100   | 원격 호스트가 재협상 요청에 대한 응답으로 TLS 재협상 핸드셰이크를 수행하지 않을 것임을 나타냅니다.                                 |
| unsupported_extension         | 110   | TLS 클라이언트가 초기 ClientHello에서 명시적으로 요청하지 않은 확장을 포함하는 ServerHello를 수신하는 경우 전송됩니다(서버에 문제가 있음을 나타냄). |

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **alert_level** 받은 경고의 수준(경고 또는 치명적)을 반환합니다.
- **alert_value** 받은 경고의 값을 반환합니다(표 참조).

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 작업에 성공했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션이 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_start
- nx_secure_tls_session_send
- nx_secure_tls_session_receive

## <a name="nx_secure_tls_session_certificate_callback_set"></a>nx_secure_tls_session_certificate_callback_set

추가 인증서 유효성 검사에 사용할 TLS에 대한 콜백 설정

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a>Description

이 서비스는 원격 호스트에서 인증서를 받을 때 TLS에서 호출하는 TLS 세션에 함수 포인터를 할당하여 애플리케이션에서 DNS 유효성 검사, 인증서 해지, 인증서 정책 적용 등의 유효성 검사를 수행할 수 있도록 합니다.

NetX Secure TLS는 콜백을 호출하기 전에 인증서에 대해 기본 X.509 경로 유효성 검사를 수행하여 인증서를 TLS에서 신뢰할 수 있는 인증서 저장소의 인증서로 추적할 수 있도록 하지만 다른 모든 유효성 검사는 이 콜백에서 처리됩니다.

콜백은 TLS 세션 포인터와 원격 호스트 ID 인증서에 대한 포인터(인증서 체인의 리프)를 제공합니다. 모든 유효성 검사가 성공하면 콜백이 NX_SUCCESS을 반환합니다. 그렇지 않으면 유효성 검사 오류를 나타내는 오류 코드를 반환합니다. NX_SUCCESS 이외의 값을 지정하면 TLS 핸드셰이크가 즉시 중단됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **func_ptr** 인증서 유효성 검사 콜백 함수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 함수 포인터를 할당했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_tls_session_client_callback_set"></a>nx_secure_tls_session_client_callback_set

TlS가 TLS 클라이언트 핸드셰이크 시작 시 호출할 콜백 설정

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a>Description

이 서비스는 TLS 클라이언트 핸드셰이크가 ServerHelloDone 메시지를 받았을 때 TLS에서 호출하는 TLS 세션에 함수 포인터를 할당합니다. 콜백 함수를 사용하면 애플리케이션은 수신된 ServerHello 메시지에서 입력 또는 의사 결정이 필요한 모든 TLS 확장을 처리할 수 있습니다.

호출하는 TLS 세션 제어 블록과 NX_SECURE_TLS_HELLO_EXTENSION 개체의 배열로 콜백이 실행됩니다. 확장 개체의 배열은 특정 확장을 찾아서 구문 분석하는 도우미 함수에 전달됩니다. 현재 NetX Secure에서는 TLS 클라이언트 입력이 필요한 특정 확장이 지원되지 않지만 애플리케이션 디자이너에서 사용자 지정 또는 새 확장을 처리하기 위해 콜백을 사용할 수 있습니다. Hello 메시지에 제공된 TLS 확장을 구문 분석하는 도우미 함수 예제는 *nx_secure_tls_session_sni_extension_parse* 를 참조하세요.

또한 원격 서버에서 인증서를 요청했으며 TLS 클라이언트에서 특정 인증서를 선택할 수 있도록 하기 위한 정보를 제공한 경우, TLS 클라이언트에 대해 *nx_secure_tls_active_certificate_set* 를 사용하여 활성 ID 인증서를 선택하는 데 클라이언트 콜백을 사용할 수도 있습니다. 자세한 내용은 nx_secure_tls_active_certificate_set에 대한 참조를 참조하세요.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **func_ptr** TLS 클라이언트 콜백 함수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 함수 포인터를 할당했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a>nx_secure_tls_session_x509_client_verify_configure

클라이언트 X.509 확인을 사용하도록 설정하고 클라이언트 인증서에 대해 공간 할당

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Description

이 서비스는 TLS 서버 인스턴스에 대한 선택적 X.509 클라이언트 인증을 사용하도록 설정합니다. 또한 원격 클라이언트 호스트에서 들어오는 인증서 체인을 처리하는 데 필요한 공간도 할당합니다. 원격 클라이언트에서 제공하는 인증서는 서비스 nx_secure_tls_trusted_certificate_add를 통해 할당된 TLS 서버 인스턴스의 신뢰할 수 있는 인증서를 기준으로 확인됩니다.

TLS 클라이언트 모드의 경우 원격 인증서 할당이 필요하며, 대신 서비스 nx_secure_tls_remote_certificate_buffer_allocate를 사용해야 합니다. TLS 클라이언트 인스턴스에서 X.509 클라이언트 인증을 사용하도록 설정해도 아무런 영향을 주지 않습니다.

certificate_buffer 매개 변수는 수신 원격 인증서 및 해당 인증서에 필요한 제어 블록을 저장하기 위해 할당된 공간을 가리킵니다. 버퍼는 각 인증서에 지정된 것과 같은 부분이 있는 인증서 수(certs_number)로 나뉩니다. buffer_size 매개 변수는 버퍼의 크기를 나타냅니다. 필요한 공간은 다음 수식을 사용하여 구할 수 있습니다.

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

서명에 대해 SHA-256을 사용하는 2048비트의 RSA 키를 포함하는 일반적인 인증서의 범위는 1000-2000바이트입니다. 버퍼는 적어도 각 인증서에 대한 해당 크기를 보유할 수 있을 만큼 커야 하지만 원격 호스트 인증서에 따라 훨씬 더 작거나 클 수 있습니다. 버퍼가 너무 작아서 수신 인증서를 저장할 수 없는 경우 TLS 핸드셰이크는 오류를 발생하면서 종료됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **certs_number** 제공된 버퍼에서 할당할 인증서의 수입니다.
- **certificate_buffer** 원격 호스트에서 받은 인증서를 저장할 버퍼에 대한 포인터입니다.
- **buffer_size** 인증서 버퍼의 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인증서를 할당했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 또는 버퍼 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**(0x12D) 제공된 버퍼가 너무 작습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 버퍼가 너무 작아서 원하는 수의 인증서를 보유할 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_buffer_allocate

## <a name="nx_secure_tls_session_client_verify_disable"></a>nx_secure_tls_session_client_verify_disable

NetX Secure TLS 세션에 대해 클라이언트 인증서 인증를 사용하지 않도록 설정

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

이 서비스는 특정 TLS 세션에 대해 클라이언트 인증서 인증을 사용하지 않도록 설정합니다. 자세한 내용은 nx_secure_tls_session_client_verify_enable을 참조하세요.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 상태 변경에 성공했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_client_verify_enable"></a>nx_secure_tls_session_client_verify_enable

NetX Secure TLS 세션에 대해 클라이언트 인증서 인증를 사용하도록 설정

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

이 서비스는 특정 TLS 세션에 대해 클라이언트 인증서 인증을 사용하도록 설정합니다. TLS 서버 인스턴스에 대해 클라이언트 인증서 인증을 사용하도록 설정하면 초기 TLS 핸드셰이크 중에 TLS 서버는 원격 TLS 클라이언트의 인증서를 요청합니다. 원격 TLS 클라이언트에서 받은 인증서는 클라이언트가 인증서를 소유하고 있는지(해당 인증서와 연결된 프라이빗 키에 대해 액세스 권한이 있음) 확인하기 위해 TLS 서버에서 사용하는 CertificateVerify 메시지와 함께 제공됩니다.

제공된 인증서를 확인하고 X.509 인증서 체인을 통해 TLS 서버의 신뢰할 수 있는 인증서 저장소에 있는 인증서로 다시 추적할 수 있으면 원격 TLS 클라이언트가 인증되고 핸드셰이크가 진행됩니다. 인증서 또는 CertificateVerify 메시지를 처리하는 동안 오류가 발생하는 경우 TLS 핸드셰이크는 오류와 함께 종료됩니다.

> [!NOTE]
> *TLS 서버의 신뢰할 수 있는 저장소에 있는 하나 이상의 인증서가 nx_secure_tls_trusted_certificate_add를 통해 추가되어야 하며 그렇지 않으면 인증이 항상 실패합니다.*

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 상태 변경에 성공했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_tls_session_create"></a>nx_secure_tls_session_create

보안 통신용 NetX Secure TLS 세션 만들기

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a>Description

이 서비스는 네트워크 연결을 통해 보안 TLS 통신을 설정하는 데 사용할 NX_SECURE_TLS_SESSION 구조체 인스턴스를 초기화합니다.

이 메서드는 TLS에 사용할 수 있는 암호화 메서드로 채워지는 NX_SECURE_TLS_CRYPTO 개체를 사용합니다. *encryption_metadata_area* 는 TLS가 NX_SECURE_TLS_CRYPTO 테이블의 암호화 메서드가 계산에 사용하는 "메타데이터"를 저장하기 위해 사용하도록 할당된 버퍼를 가리킵니다. 테이블 크기는 nx_secure_tls_metadata_size_calculate 서비스를 사용하여 확인할 수 있습니다. 자세한 내용은 3장에서 "NetX Secure TLS의 암호화" 섹션을 참조하세요.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **cipher_table** TLS 암호화 메서드에 대한 포인터입니다.
- **encryption_metadata_area** 암호화 메타데이터 공간에 대한 포인터입니다.
- **encryption_metadata_size** 메타데이터 버퍼의 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 지정된 메서드에 비해 메타데이터 버퍼가 너무 작습니다.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER**(0x106) 사용하도록 설정된 TLS 버전에 필요한 암호화 메서드가 암호화 테이블에 제공되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_metadata_size_calculate
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_delete
- 3장에서 NetX Secure TLS의 암호화

## <a name="nx_secure_tls_session_delete"></a>nx_secure_tls_session_delete

NetX Secure TLS 세션 삭제

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

이 서비스는 NX_SECURE_TLS_SESSION 구조체 인스턴스로 표시되는 TLS 세션을 삭제하고 해당 세션 인스턴스가 소유하는 모든 시스템 리소스를 해제합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_end"></a>nx_secure_tls_session_end

활성 NetX Secure TLS 세션 종료

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 TLS CloseNotify 메시지를 원격 호스트로 보내 NX_SECURE_TLS_SESSION 구조체 인스턴스로 표시되는 TLS 세션을 종료합니다. 그런 다음, 서비스는 원격 호스트가 자체 CloseNotify 메시지에 응답할 때까지 기다립니다.

원격 호스트에서 CloseNotify 메시지를 보내지 않는 경우 TLS는 이 오류와 가능한 보안 위반을 고려하므로 보안 연결을 위해서는 반환 값을 확인하는 것이 중요합니다. **wait_option** 매개 변수를 사용하여 서비스에서 호출 스레드에 제어를 반환하기 전에 응답을 기다리는 시간을 제어할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **wait_option** 서비스가 원격 호스트의 응답을 기다리는 기간을 나타냅니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.
- **NX_SECURE_TLS_NO_CLOSE_RESPONSE**(0x113) 제한 시간을 초과하기 전에 원격 호스트에서 응답을 받지 못했습니다.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**(0x111) CloseNotify 메시지를 보낼 패킷을 할당할 수 없습니다.
- **NX_SECURE_TLS_TCP_SEND_FAILED**(0x109) TCP 소켓을 통해 CloseNotify 메시지를 보낼 수 없습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_packet_buffer_set"></a>nx_secure_tls_session_packet_buffer_set

NetX Secure TLS 세션에 대한 패킷 리어셈블리 버퍼 설정

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a>Description

이 서비스는 패킷 리어셈블리 버퍼를 TLS 세션에 연결합니다. 수신 TLS 레코드를 해독하고 구문 분석하려면 각 레코드의 데이터를 기본 TCP 패킷에서 조합해야 합니다. TLS 레코드 크기가 최대 16KB가 되어(일반적으로는 크기가 훨씬 작음) 단일 TCP 패킷에 맞지 않을 수 있습니다.

수신 메시지 크기가 16KB의 TLS 레코드 제한보다 작으면 버퍼 크기를 더 작게 만들 수 있지만 알 수 없는 수신 데이터를 처리하기 위해 버퍼를 최대한 크게 만들어야 합니다. 수신 레코드가 제공된 버퍼보다 큰 경우 TLS 세션이 오류를 나타내며 종료됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **buffer_ptr** TLS에서 패킷 리어셈블리에 사용할 버퍼에 대한 포인터입니다.
- **buffer_size** 제공된 버퍼의 크기(바이트)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 버퍼 또는 TLS 세션 포인터가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_protocol_version_override"></a>nx_secure_tls_session_protocol_version_override

NetX Seure TLS 세션의 기본 TLS 프로토콜 버전 재정의

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a>Description

이 서비스는 특정 세션에서 사용하는 기본(최신) TLS 프로토콜 버전을 재정의합니다. 이 서비스를 통해 NetX Secure TLS는 컴파일 시간에 최신 TLS 버전을 사용하지 않도록 설정하지 않고도 특정 TLS 세션에 이전 버전의 TLS를 사용할 수 있습니다. 이 서비스는 최신 버전의 TLS를 지원하지 않는 이전 호스트와 통신해야 하는 애플리케이션에 유용할 수 있습니다.

> [!IMPORTANT]
> *버전 5.11SP3의 NetX Secure TLS는 RFC 7507(아래 참고 참조)을 지원하며 이 API를 통해 이전 버전으로 재정의하면 ClientHello에서 대체 SCSV가 전송됩니다. 서버에서 최신 버전의 TLS를 지원하고 대체 SCSV이 ClientHello에 포함된 경우 해당 서버는 "부적절한 대체" 경고를 나타내며 TLS 핸드셰이크를 중단합니다. SCSV는 버전 재정의가 사용하도록 설정된 것보다 이전 버전의 TLS인 경우에만 전송됩니다. 예를 들어 버전을 TLS 1.2로 재정의하면 SCSV가 전송되지 않습니다.*

protocol_version 매개 변수에 대한 유효한 값은 매크로 NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 및 NX_SECURE_TLS_VERSION_TLS_1_2입니다.

매크로 NX_SECURE_TLS_DISABLE_TLS_1_1 및 NX_SECURE_TLS_ENABLE_TLS_1_0을 사용하여 애플리케이션으로 컴파일되는 TLS 버전을 제어할 수 있습니다. TLS 버전 1.2는 항상 사용하도록 설정됩니다.

원격 호스트에서 제공된 버전을 지원하지 않는 경우 연결이 실패합니다. 제공된 재정의 버전만 NetX Secure TLS에서 협상됩니다.

> [!IMPORTANT]
> RFC 7507: TLS 대체 SCSV. 이 RFC는 원래 프로토콜 다운그레이드 협상을 부적절하게 처리하고 대신 유효한 ClientHello 메시지를 거부한 서버로 인해 야기된 보안 문제를 완화하기 위해 도입되었습니다. 이러한 이전 서버와 호환되는 상태를 유지하려는 경우 일부 TLS 클라이언트 애플리케이션은 이전 TLS 버전을 사용하여 실패한 핸드셰이크를 다시 시도합니다(예: TLS 1.2가 실패하므로 TLS 1.1 시도). 그러나 이 해결 방법에는 새로운 문제가 야기되었습니다. 공격자는 서버가 최신 TLS 버전을 지원하는 경우에도 서버 연결 실패를 야기하는 네트워크 또는 패킷 오류를 인위적으로 도입하여 클라이언트를 강제로 다운그레이드하도록 할 수 있습니다. 이전 버전으로 다운그레이드하면 공격자가 해당 버전의 약점을 악용할 수 있습니다(특히 SSLv3<sup>21</sup>은 POODLE 공격에 취약). 이러한 상황을 방지하기 위해 RFC 7507은 TLS 클라이언트에서 지원하는 최신 버전이 아닌 TLS 버전을 사용할 때 TLS 서버에 알리는 ClientHello를 통해 전송되는 의사 암호 그룹<sup>22</sup>인 "대체 SCSV"를 도입했습니다. 이러한 방식으로 최신 버전을 지원하는 서버는 대체 SCSV를 포함하는 ClientHello를 거부하고 다운그레이드 공격이 성공하지 않도록 할 수 있습니다.

21. NetX Secure는 POODLE과 같은 알려진 심각한 약점 때문에 SSLv3를 구현하지 않습니다.

22. 의사 암호 그룹 또는 SCSV(Signaling Cipher Suite Value)는 이전 TLS 버전에서 사용할 수 없던 기능에 대해 사용하도록 설정된 TLS 구현을 신호로 알리는 데 사용되는 예약된 암호 그룹 번호입니다. 대체 SCSV 및 TLS_EMPTY_RENEGOTIATION_INFO_SCSV(RFC 5746)를 예로 들 수 있습니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **protocol_version** 사용할 특정 TLS 버전에 대한 TLS 버전 매크로입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 상태 변경에 성공했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION**(0x110) 알려져 있지만 지원되지 않는 TLS 버전입니다.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION**(0x10F) 프로토콜 버전이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_receive"></a>nx_secure_tls_session_receive

NetX Secure TLS 세션에서 데이터 받기

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 활성 TLS 세션에서 데이터를 수신하고, NX_PACKET 매개 변수에서 호출자에게 제공하기 전에 해당 데이터의 암호 해독을 처리합니다. 지정된 세션에 대기 중인 데이터가 없는 경우에는 제공된 대기 옵션에 따라 호출이 일시 중단됩니다.

> [!IMPORTANT]
> NX_SUCCESS가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 해당 패킷을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **packet_ptr** 할당된 TLS 패킷 포인터에 대한 포인터입니다.
- **wait_option** 서비스에서 반환 전에 원격 호스트에서 패킷을 대기해야 하는 기간을 나타냅니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.
- **NX_NO_PACKET** (0x01) 수신된 데이터가 없습니다.
- **NX_NOT_CONNECTED**(0x38) 기본 TCP 소켓이 더 이상 연결되어 있지 않습니다.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE**(0x108) 받은 메시지의 인증 해시 확인에 실패했습니다.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION**(0x10F) 받은 메시지의 헤더에 알 수 없는 프로토콜 버전이 있습니다.
- **NX_SECURE_TLS_ALERT_RECEIVED**(0x114) 원격 호스트에서 TLS 경고를 받았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED**(0x101) 제공된 TLS 세션이 초기화되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a>nx_secure_tls_session_renegotiate_callback_set

세션 다시 협상을 시작할 때 호출될 콜백 할당

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a>Description

이 서비스는 세션 재협상 핸드셰이크의 첫 번째 메시지가 원격 호스트에서 수신될 때마다 호출되는 TLS 세션에 콜백을 할당합니다.

콜백 함수는 재협상 핸드셰이크가 시작될 것이라는 알림으로 애플리케이션에 전달됩니다. 애플리케이션은 콜백에서 0이 아닌 값을 반환하여 TLS 세션을 종료하도록 선택할 수 있습니다. 이로 인해 TLS 세션은 오류를 나타내며 종료됩니다. 애플리케이션에서 재협상을 계속하려는 경우 콜백이 NX_SUCCESS를 반환해야 합니다.

> [!NOTE]
> *TLS 재협상의 의미 체계 때문에, 원격 서버에서 HelloRequest가 수신될 때마다 NetX Secure TLS 클라이언트에 대해 콜백이 호출되지만 클라이언트에서 재협상을 시작할 때는 콜백이 호출되지 않습니다. NetX Secure TLS 서버에서 재협상 ClientHello(활성 TLS 세션의 컨텍스트에서 수신된 ClientHello)가 수신될 때마다 콜백이 호출됩니다. 즉, TLS 서버에서 원격 클라이언트가 응답할 HelloRequest를 보내기 때문에 원격 호스트 또는 로컬 애플리케이션에서 재협상을 시작했는지 여부에 관계 없이 콜백이 호출됩니다.*

NetX Secure TLS는 재협상 핸드셰이크가 중간자(man-in-the-middle) 공격을 받지 않도록 하기 위해 RFC 5746의 보안 재협상 표시 확장을 구현합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **callback** 콜백 함수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 콜백을 할당했습니다.
- **NX_PTR_ERROR**(0x07) 콜백 함수 또는 TLS 세션에 대해 잘못된 포인터를 사용하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiate

## <a name="nx_secure_tls_session_renegotiate"></a>nx_secure_tls_session_renegotiate

원격 호스트와의 세션 재협상 핸드셰이크 시작

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a>Description

이 서비스는 연결된 원격 TLS 호스트를 사용하여 세션 재협상 핸드셰이크를 시작합니다. 재협상은 이전에 설정된 TLS 세션의 컨텍스트 내에서 두 번째 TLS 핸드셰이크로 구성됩니다. 각각의 새 핸드셰이크 메시지는 새 세션 키가 생성되고 ChangeCipherSpec 메시지가 교환될 때까지 TLS 세션을 사용하여 암호화됩니다. 이때 새 키를 사용하여 모든 메시지를 암호화할 수 있습니다.

재협상은 TLS 세션이 설정되면 언제든지 시작할 수 있습니다. TLS 핸드셰이크 도중이나 TLS 세션이 설정되기 전에 재협상을 시도하면 아무 작업도 수행되지 않습니다.

> [!NOTE]
> 이 서비스가 호출될 때 전체 TLS 핸드셰이크가 수행되므로 완료 시간과 반환되는 상태는 현재 TLS 설정 및 세션 매개 변수에 따라 달라집니다.

NetX Secure TLS는 재협상 핸드셰이크가 중간자(man-in-the-middle) 공격을 받지 않도록 하기 위해 RFC 5746의 보안 재협상 표시 확장을 구현합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **wait_option** 서비스에서 반환 전에 원격 호스트에서 패킷을 대기해야 하는 기간을 나타냅니다. 이 매개 변수는 TLS 내의 모든 NetX 서비스에 전달됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 재협상에 성공했습니다.
- **NX_NO_PACKET** (0x01) 수신된 데이터가 없습니다.
- **NX_NOT_CONNECTED**(0x38) 기본 TCP 소켓이 더 이상 연결되어 있지 않습니다.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE**(0x108) 받은 메시지의 인증 해시 확인에 실패했습니다.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION**(0x10F) 받은 메시지의 헤더에 알 수 없는 프로토콜 버전이 있습니다.
- **NX_SECURE_TLS_ALERT_RECEIVED**(0x114) 원격 호스트에서 TLS 경고를 받았습니다.
- **NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE**(0x134) 로컬 또는 원격 TLS 세션이 비활성 상태이므로 재협상이 불가능해집니다.
- **NX_SECURE_TLS_RENEGOTIATION_FAILURE**(0x13A) 원격 호스트가 SCSV 또는 보안 재협상 확장을 제공하지 않았으므로 재협상을 수행할 수 없습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED**(0x101) 제공된 TLS 세션이 초기화되지 않았습니다.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**(0x111) 기본 패킷을 할당하지 못했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiation_callback_set

## <a name="nx_secure_tls_session_reset"></a>nx_secure_tls_session_reset

NetX Secure TLS 세션 지우기 및 다시 설정

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

이 서비스는 기존 TLS 세션 개체를 새 세션에 다시 사용할 수 있도록 TLS 세션을 지운 후 세션이 방금 만들어진 것처럼 상태를 다시 설정합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.
- **NX_INVALID_PARAMETERS**(0x4D) TLS 세션 포인터가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_send"></a>nx_secure_tls_session_send

NetX Secure TLS 세션을 통해 데이터 보내기

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 활성 TLS 세션을 사용하여 제공된 NX_PACKET에서 데이터를 보내고, 원격 호스트에 전송하기 전에 해당 데이터의 암호화를 처리합니다. 마지막으로 보급된 수신기 창 크기가 이 요청 미만이면 지정된 대기 옵션에 따라 선택적으로 서비스가 일시 중단됩니다.

> [!IMPORTANT]
> 오류가 반환되지 않는 한 이 호출 후 애플리케이션은 패킷을 해제하면 안 됩니다. 애플리케이션이 패킷을 해제하면 전송 후 네트워크 드라이버가 패킷을 해제하므로 예측할 수 없는 결과가 발생합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **packet_ptr** 전송할 데이터를 포함하는 TLS 패킷에 대한 포인터입니다.
- **wait_option** 요청이 수신기 창 크기를 초과하는 경우 서비스가 작동하는 방식을 정의합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.
- **NX_NO_PACKET** (0x01) 수신된 데이터가 없습니다.
- **NX_NOT_CONNECTED**(0x38) 기본 TCP 소켓이 더 이상 연결되어 있지 않습니다.
- **NX_SECURE_TLS_TCP_SEND_FAILED**(0x109) 기본 TCP 소켓 보내기가 실패했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED**(0x101) 제공된 TLS 세션이 초기화되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_server_callback_set"></a>nx_secure_tls_session_server_callback_set

TlS가 TLS 서버 핸드셰이크 시작 시 호출할 콜백 설정

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a>Description

이 서비스는 TLS 서버 핸드셰이크가 ClientHello 메시지를 받았을 때 TLS에서 호출하는 TLS 세션에 함수 포인터를 할당합니다. 콜백 함수를 사용하면 애플리케이션은 수신된 ClientHello 메시지에서 입력 또는 의사 결정이 필요한 모든 TLS 확장을 처리할 수 있습니다.

호출하는 TLS 세션 제어 블록과 NX_SECURE_TLS_HELLO_EXTENSION 개체의 배열로 콜백이 실행됩니다. 확장 개체의 배열은 특정 확장을 찾아서 구문 분석하는 도우미 함수에 전달됩니다. Hello 메시지에 제공된 TLS 확장을 구문 분석하는 도우미 함수 예제는 *nx_secure_tls_session_sni_extension_parse* 를 참조하세요.

서버 콜백을 TLS 서버에 대한 *nx_secure_tls_active_certificate_set* 을 사용하여 활성 ID 인증서를 선택하는 데 사용할 수도 있습니다. 이러한 작업은 주로 SNI(서버 이름 표시) 확장에 대한 응답으로 발생하며, 이를 통해 TLS 클라이언트는 연결하려는 서버를 나타낼 수 있습니다. 자세한 내용은   nx_secure_tls_session_sni_extension_parse 및 nx_secure_tls_active_certificate_set을 참조하세요.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **func_ptr** TLS 서버 콜백 함수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 함수 포인터를 할당했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_active_certificate_set
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_sni_extension_parse"></a>nx_secure_tls_session_sni_extension_parse

TLS 클라이언트에서 받은 SNI(서버 이름 표시) 확장 구문 분석

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Description

이 서비스는 nx_secure_tls_session_server_callback_set을 사용하여 TLS 세션에 추가되는 TLS 서버 세션 콜백 내에서 호출되도록 고안되었습니다. 콜백은 원격 TLS 클라이언트에서 ClientHello 메시지를 수신한 이후에 호출되며, 사용 가능한 확장의 배열(및 배열의 확장 개수)이 제공됩니다. 해당 배열 및 길이를 이 루틴에 직접 전달하여 SNI 확장이 있는지 확인할 수 있습니다. 그렇지 않으면 클라이언트가 SNI 확장을 제공하지 않기로 선택했음을 나타내기 위해 NX_SECURE_TLS_EXTENSION_NOT_FOUND가 반환됩니다(이것은 오류가 아님).

SNI 확장이 있으면 TLS 클라이언트에서 제공하는 X.509 DNS 이름이 dns_name 구조체로 반환됩니다. 현재 SNI 확장은 단일 DNS 이름 항목만 제공합니다. 이 항목은 TLS 서버에서 원격 클라이언트에 보낼 ID 인증서를 결정하는 데 사용할 수 있습니다.**

NX_SECURE_X509_DNS_NAME 구조체에는 필드 nx_secure_x509_dns_name에 UCHAR 문자열로 DNS 이름이 포함되고 nx_secure_x509_dns_name_length에 이름 문자열 길이가 포함됩니다. 매크로 NX_SECURE_X509_DNS_NAME_MAX는 nx_secure_x509_dns_name 버퍼의 크기를 제어합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **extensions** TLS Hello 확장 배열에 대한 포인터입니다(세션 콜백).
- **num_extensions** 배열의 확장 수입니다(세션 콜백).
- **dns_name** SNI 확장에 제공된 DNS 이름을 반환합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 확장을 성공적으로 구문 분석했습니다.
- **NX_PTR_ERROR**(0x07) 확장 배열 또는 TLS 세션 포인터가 잘못되었습니다.
- **NX_SECURE_TLS_EXTENSION_NOT_FOUND**(0x136) SNI 확장을 찾을 수 없습니다.
- **NX_SECURE_TLS_SNI_EXTENSION_INVALID**(0x137) SNI 확장 형식이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_server_callback_set
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_sni_extension_set"></a>nx_secure_tls_session_sni_extension_set

원격 서버로 전송할 SNI(서버 이름 표시) 확장 DNS 이름 설정

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Description

이 서비스를 통해 TLS 클라이언트 애플리케이션은 SNI(서버 이름 표시) TLS 확장을 사용하여 기본 서버 DNS 이름을 원격 TLS 서버에 제공할 수 있습니다. SNI 확장을 사용하면 서버는 클라이언트의 표시된 서버 기본 설정에 따라 적절한 ID 인증서 및 매개 변수를 선택할 수 있습니다. SNI 확장은 현재 전송될 단일 DNS 이름만 지원하므로 단일 이름 매개 변수입니다. dns_name 매개 변수는 nx_secure_x509_dns_name_initialize를 사용하여 초기화해야 하며 클라이언트의 기본 설정 서버를 포함합니다. 확장 이름을 설정 해제하려면 NX_NULL의 "dns_name" 매개 변수 값으로 이 서비스를 호출하면 됩니다.

NX_SECURE_X509_DNS_NAME 구조체에는 필드 nx_secure_x509_dns_name에 UCHAR 문자열로 DNS 이름이 포함되고 nx_secure_x509_dns_name_length에 이름 문자열 길이가 포함됩니다. 매크로 NX_SECURE_X509_DNS_NAME_MAX는 nx_secure_x509_dns_name 버퍼의 크기를 제어합니다.

> [!NOTE]
> nx_secure_tls_session_start를 호출하기 전에 이 루틴을 호출해야 하며 그러지 않으면 ClientHello에 SNI 확장이 포함되지 않게 됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **dns_name** 애플리케이션에서 제공하는 DNS 이름입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) DNS 서버 이름을 추가했습니다.
- **NX_PTR_ERROR**(0X07) DNS 이름 또는 TLS 세션 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_start
- nx_secure_x509_dns_name_initialize

## <a name="nx_secure_tls_session_start"></a>nx_secure_tls_session_start

NetX Secure TLS 세션 시작

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 제공된 TLS 세션 제어 블록 및 연결된 TCP 소켓을 사용하여 TLS 세션을 시작합니다. nx_tcp_client_socket_connect 또는 nx_tcp_server_socket_accept를 성공적으로 호출한 후에는 TCP 연결을 이미 완료했어야 합니다.

이 서비스는 TCP 소켓에서 TLS 세션의 유형(클라이언트 또는 서버)을 결정합니다.

대기 옵션은 TLS 핸드셰이크가 진행 중인 동안 서비스가 동작하는 방식을 정의합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **tcp_socket_ptr** 연결된 TCP 소켓에 대한 포인터입니다.
- **wait_option** 은 TLS 핸드셰이크가 진행 중인 동안 서비스가 동작하는 방식을 정의합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.
- **NX_NOT_CONNECTED**(0x38) 기본 TCP 소켓이 더 이상 연결되어 있지 않습니다.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**(0x102) 받은 TLS 메시지 유형이 올바르지 않습니다.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER**(0x106) 원격 호스트에서 제공하는 암호화가 지원되지 않습니다.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE**(0x107) TLS 핸드셰이크 중 메시지 처리가 실패했습니다.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE**(0x108) 들어오는 메시지가 해시 MAC 검사에 실패했습니다.
- **NX_SECURE_TLS_TCP_SEND_FAILED**(0x109) 기본 TCP 소켓 보내기가 실패했습니다.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH**(0x10A) 들어오는 메시지의 길이 필드가 올바르지 않습니다.
- **NX_SECURE_TLS_BAD_CIPHERSPEC**(0x10B) 들어오는 ChangeCipherSpec 메시지가 올바르지 않습니다.
- **NX_SECURE_TLS_INVALID_SERVER_CERT**(0x10C) 들어오는 TLS 인증서를 원격 TLS 서버 식별에 사용할 수 없습니다.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER**(0x10D) 원격 호스트에서 제공하는 공개 키 암호가 지원되지 않습니다.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS**(0x10E) NetX Secure TLS 스택에서 지원하는 암호 그룹이 없다고 원격 호스트에서 알렸습니다.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION**(0x10F) 받은 TLS 메시지의 헤더에 알 수 없는 TLS 버전이 있습니다.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION**(0x110) 받은 TLS 메시지의 헤더에 알고 있지만 지원되지 않는 TLS 버전이 있습니다.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**(0x111) 내부 TLS 패킷을 할당하지 못했습니다.
- **NX_SECURE_TLS_INVALID_CERTIFICATE**(0x112) 원격 호스트에서 제공한 인증서가 올바르지 않습니다.
- **NX_SECURE_TLS_ALERT_RECEIVED**(0x114) 원격 호스트가 오류를 알리는 경고를 보내고 TLS 세션을 종료했습니다.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE**(0x13B) 암호 그룹 테이블의 항목에 NULL 함수 포인터가 있습니다.
- **NX_SECURE_TLS_INAPPROPRIATE_FALLBACK**(0x146) 원격 TLS ClientHello는 대체 SCSV를 포함하며 버전 대체를 시도했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_send
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_end
- nx_secure_tls_session_create
- nx_tcp_socket_accept
- nx_tcp_socket_listen
- nx_tcp_socket_disconnect
- nx_tcp_socket_unaccept
- nx_tcp_socket_relisten
- nx_tcp_socket_delete
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset

## <a name="nx_secure_tls_session_time_function_set"></a>nx_secure_tls_session_time_function_set

NetX Secure TLS 세션에 타임스탬프 함수 할당

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a>Description

이 함수는 현재 시간을 가져와야 할 때 TLS가 호출할 함수 포인터를 설정합니다. 이 함수는 다양한 TLS 핸드셰이크 메시지에서, 인증서 확인을 위해 사용됩니다.

이 함수는 TLS RFC 5246의 ClientHello 요구 사항에 따라 현재 GMT를 UNIX 32비트 형식으로 반환해야 합니다(UTC로 1970년 1월 1일부터 시작해서 자정 이후의 시간(초)이며, 윤초는 무시함).

타임스탬프 함수를 할당하지 않으면 TLS 핸드셰이크의 타임스탬프에 대한 값 0이 사용되고 인증서 만료 확인이 작동하지 않습니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** TLS 세션 인스턴스에 대한 포인터입니다.
- **time_func_ptr** UNIX 32비트 형식의 현재 시간(GMT)을 반환하는 함수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.
- **NX_INVALID_PARAMETERS**(0x4D) TLS 세션 포인터가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_sendnx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_trusted_certificate_add"></a>nx_secure_tls_trusted_certificate_add

NetX Secure TLS 세션에 신뢰할 수 있는 인증서 추가

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Description

이 서비스는 초기화된 NX_SECURE_X509_CERT 구조체 인스턴스를 TLS 세션에 추가합니다. 이 인증서는 TLS 스택에서 TLS 핸드셰이크 중에 원격 호스트에서 제공하는 인증서를 확인하는 데 사용됩니다.

TLS 클라이언트 모드에는 신뢰할 수 있는 인증서가 필요합니다.

클라이언트 인증서 인증을 사용하도록 설정한 경우에는 TLS 서버 모드에서만 신뢰할 수 있는 인증서가 필요합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **certificate_ptr** 초기화된 TLS 인증서 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인증서를 추가했습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 잘못된 인증서를 추가하려고 했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_remove

## <a name="nx_secure_tls_trusted_certificate_remove"></a>nx_secure_tls_trusted_certificate_remove

NetX Secure TLS 세션에서 신뢰할 수 있는 인증서 제거

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a>Description

이 서비스는 인증서의 일반 이름 필드에 입력된 TLS 세션에서 신뢰할 수 있는 인증서를 제거합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** 이전에 만든 TLS 세션 인스턴스에 대한 포인터입니다.
- **common_name** 제거할 인증서의 일반 이름 값입니다.
- **common_name_length** 일반 이름 문자열의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인증서를 추가했습니다.
- **NX_PTR_ERROR**(0x07) TLS 세션 포인터가 올바르지 않습니다.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0x119) 인증서를 찾을 수 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_x509_certificate_initialize"></a>nx_secure_x509_certificate_initialize

NetX Secure TLS에 대한 X.509 인증서 초기화

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 서비스는 TLS 세션에서 사용하기 위해 이진으로 인코딩된 X.509 디지털 인증서에서 NX_SECURE_X509_CERT 구조체를 초기화합니다.

인증서 데이터는 DER로 인코딩된 이진 형식의 유효한 X.509 디지털 인증서 **여야 합니다.** 데이터는 해당 데이터에 대한 UCHAR 포인터가 제공되는 한, 어떤 소스(예: 파일 시스템, 컴파일된 상수 버퍼 등)에서도 가져올 수 있습니다.

*raw_data_buffer* 매개 변수 및 해당 크기는 구문 분석 전에 인증서 데이터가 복사되는 전용 버퍼를 지정하는 선택적 매개 변수입니다. raw_data_buffer가 NX_NULL로 전달되는 경우 NX_SECURE_X509_CERT 구조체가 certificate_data 배열을 직접 가리킵니다(이 경우 buffer_size는 무시됨). raw_data_buffer가 NX_NULL로 전달되는 경우 certificate_data 포인터가 가리키는 데이터를 수정하지 ***않아야 합니다***. 데이터를 수정하면 인증서 처리가 실패할 수 있습니다.

프라이빗 키 매개 변수는 로컬 ID 인증서에 사용됩니다. 서버는 클라이언트에서 들어오는 키 데이터(서버의 퍼블릭 키를 사용하여 암호화됨) 암호를 해독하는 데, 클라이언트는 서버에서 클라이언트 인증서를 요청할 때 서버에 대한 ID를 확인하는 데 프라이빗 키를 사용합니다. 이 API를 사용하여 프라이빗 키를 추가하면 연결된 인증서가 자동으로 TLS 애플리케이션에 대한 ID 인증서로 표시됩니다. 다른 용도(예: 신뢰할 수 있는 저장소)로 인증서를 초기화하는 경우 private_key_data 매개 변수는 NULL로 전달되고, private_key_data_length는 0으로 전달되고, private_key_type은 NX_SECURE_X509_KEY_TYPE_NONE으로 전달되어야 합니다.

*private_key_type* 매개 변수는 프라이빗 키의 서식을 나타냅니다. 예를 들어, 프라이빗 키가 DER로 인코딩된 PKCS#1 형식 RSA 프라이빗 키인 경우 private_key_type를 NetX Secure에 알려진 형식으로, 즉시 구문 분석된 후 나중에 사용하기 위해 저장되는 NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER로 전달해야 합니다.

또한 이 private_key_type은 특정 키 형식이나 다른 요구 사항이 있는 플랫폼 및 애플리케이션에 대한 사용자 정의 키 형식<sup>23</sup>을 지원합니다. 예를 들어, 하드웨어 기반 암호화 엔진은 NetX Secure 소프트웨어에서 인식하지 않는 특정 형식을 사용할 수 있으며, 프라이빗 키는 TPM(신뢰할 수 있는 플랫폼 모듈) 또는 PKCS#11 암호화 하드웨어를 사용하는 경우와 마찬가지로 암호화하거나 암호화 토큰으로 나타낼 수 있습니다. 사용자 정의 키 형식이 사용될 때 키 데이터는 적절한 암호화 루틴으로 있는 그대로 전달됩니다. 예를 들어, RSA 프라이빗 키는 구문 분석 또는 처리 없이 암호 그룹 테이블의 TLS에 제공되는 RSA 암호화 루틴으로 직접 전달됩니다. 사용자 정의 키 형식이 암호화 루틴에도 전달됩니다(RSA의 경우 "op" 매개 변수임).

사용자 정의 키의 범위는 0x0001 0000-0xFFFF FFFF에 해당하는 32비트 부호 없는 정수의 위쪽 절반을 포함합니다. 0x0001 0000보다 작은 값은 NetX Secure에서 사용하도록 예약됩니다.

사용자 정의 키 형식은 원시 개인 키 데이터를 처리하기 위해 사용자 지정 암호화 루틴에 필요한 고급 기능입니다. 이 기능이 필요한 경우 Express 논리 담당자에게 문의하세요.

### <a name="parameters"></a>매개 변수

- **certificate_ptr** 초기화되지 않은 X.509 인증서 인스턴스에 대한 포인터입니다.
- **certificate_data** DER로 인코딩된 X.509 이진 데이터에 대한 포인터입니다.
- **raw_data_buffer** 선택적 전용 인증서 데이터 버퍼에 대한 포인터입니다.
- **buffer_size** 선택적 전용 인증서 데이터 버퍼의 크기입니다.
- **certificate_data_length** 인증서 이진 데이터의 길이(바이트)입니다.
- **private_key_data** 선택적 프라이빗 키 데이터에 대한 포인터입니다.
- **private_key_data_length** 프라이빗 키 데이터의 길이입니다.
- **private_key_type** 키 형식 식별자입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인증서를 추가했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.
- **NX_SECURE_TLS_INVALID_CERTIFICATE**(0x112) 인증서 데이터에 DER로 인코딩된 X.509 인증서가 포함되어 있지 않습니다.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER**(0x10D) 인증서에 NetX Secure에서 지원하는 퍼블릭 키 암호가 없습니다.
- **NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE**(0x186) 프라이빗 키 또는 인증서에 유효한 ASN.1 시퀀스가 포함되어 있지 않습니다.
- **NX_SECURE_PKCS1_INVALID_PRIVATE_KEY**(0x18A) 제공된 프라이빗 키가 유효한 PKCS#1 RSA 키가 아닙니다.
- **NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE**(0x19D) 제공된 프라이빗 키 형식이 사용자 정의 형식이 아니며 알려진 형식과 일치하지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a>참고 항목

- nx_secure_local_certificate_add
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- 3장의 NetX Secure로 X.509 인증서 가져오기

## <a name="nx_secure_x509_common_name_dns_check"></a>nx_secure_x509_common_name_dns_check

X.509 인증서에서 DNS 이름 확인

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a>Description

이 서비스는 원격 호스트의 DNS 유효성 검사를 위해 호출자가 제공한 TLD(최상위 도메인 이름)를 기준으로 인증서의 일반 이름을 확인합니다. 이 유틸리티 함수는 애플리케이션에서 제공하는 인증서 유효성 검사 콜백 루틴 내에서 호출해야 합니다. TLD 이름은 원격 호스트에 액세스하는 데 사용되는 URL의 맨 위 부분 이어야 합니다(첫 번째 슬래시 앞의 문자열이 "."로 구분됨). 일반 이름에 와일드카드가 포함되어 있으면(예: .example.com) 와일드카드는 접미사가 같은 항목을 찾습니다. 발견된(오른쪽에서 왼쪽으로 읽음) 첫 번째 와일드카드("")만 와일드카드 일치로 고려됩니다. 예를 들어, abc.*.example.com은 ".example.com"으로 끝나는 모든 이름을 일치 항목으로 검색합니다.

일반 이름이 제공된 문자열과 일치하지 않으면 "subjectAltName" 확장이 구문 분석되고(인증서에 있는 경우) DNSName 항목도 비교됩니다. 일치하는 항목이 없는 경우 오류가 반환됩니다.

예상된 인증서에서 일반 이름(및 subjectAltName 항목)의 형식을 이해하는 것이 중요 합니다. 예를 들어, 일부 인증서는 원시 IP 주소 또는 와일드 카드를 사용할 수 있습니다. 수신된 인증서의 예상 값과 일치하도록 DNS TLD 문자열의 형식을 지정해야 합니다.

### <a name="parameters"></a>매개 변수

- **certificate_ptr** X.509 인증서 인스턴스에 대한 포인터입니다.
- **dns_tld** 비교할 최상위 도메인 이름입니다.
- **dns_tld_length** TLD 문자열의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 일반 이름 또는 subjectAltName과 성공적으로 비교되었습니다.
- **NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH**(0x195) 일치하는 이름을 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_x509_crl_revocation_check"></a>nx_secure_x509_crl_revocation_check

제공된 CRL(인증서 해지 목록)에서 x.509 인증서 확인

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Description

이 서비스는 DER로 인코딩된 인증서 해지 목록을 사용하고 해당 목록에서 특정 인증서를 검색합니다. CRL의 발급자는 제공된 인증서 저장소를 기준으로 유효성이 검사되고, CRL 발급자는 확인하려는 인증서의 발급자와 동일한지 검사되며, 의심되는 인증서의 일련 번호을 해지된 인증서 목록에서 검색합니다. 발급자가 일치하면 서명이 체크 아웃되고 인증서가 목록에 **없으면** 호출은 성공적으로 수행됩니다. 다른 모든 경우에는 오류가 반환됩니다.

### <a name="parameters"></a>매개 변수

- **crl_data** DER로 인코딩된 CRL에 대한 포인터입니다.
- **crl_length** CRL 데이터의 길이(바이트)입니다.
- **store** X.509 인증서 저장소에 대한 포인터입니다.
- **certificate_ptr** X.509 인증서 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인증서가 해지되지 않았음을 확인했습니다.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**(0X119) CRL 발급자 인증서를 찾을 수 없습니다.
- **NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND**(0x11B) 인증서 발급자 인증서를 찾을 수 없습니다.
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**(0x182) CRL ASN.1에 잘못된 길이 필드가 포함되어 있습니다.
- **NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** CRL에 잘못된 ASN.1이 포함되어 있습니다.
- **NX_SECURE_X509_CHAIN_VERIFY_FAILURE**(0x18c) 인증서 체인을 확인하지 못했습니다.
- **NX_SECURE_X509_CRL_ISSUER_MISMATCH**(0x197) CRL 및 인증서 발급자가 일치하지 않습니다.
- **NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED**(0x198) CRL 서명이 잘못되었습니다.
- **NX_SECURE_X509_CRL_CERTIFICATE_REVOKED**(0x199) 확인 중인 인증서가 CRL에서 발견되었으며 해지됩니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_common_name_dns_check

## <a name="nx_secure_x509_dns_name_initialize"></a>nx_secure_x509_dns_name_initialize

X.509 DNS 이름 구조 초기화

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a>Description

이 서비스는 특정 이름 형식이 필요한 특정 API 서비스에서 사용할 X.509 DNS 이름을 초기화합니다. 예를 들어 TLS 핸드셰이크 중에 원격 호스트가 제공하는 이름과 일치하는 이름을 서버 이름 표시 확장에서 찾으려면 nx_secure_tls_sni_extension_parse 서비스에 NX_SECURE_X509_DNS_NAME 개체가 필요합니다. DNS 이름은 단순히 길이가 지정된 문자열입니다. DNS 이름의 최대 허용 길이(및 NX_SECURE_X509_DNS_NAME의 내부 버퍼 크기)는 매크로 NX_SECURE_X509_DNS_NAME_MAX(기본값 100바이트)로 제어됩니다.

### <a name="parameters"></a>매개 변수

- **dns_name** 초기화할 DNS 이름 구조입니다.
- **name_string** DNS 이름 문자열 데이터입니다.
- **length** 이름 문자열의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적으로 초기화했습니다.
- **NX_SECURE_X509_NAME_STRING_TOO_LONG**(0x19E) 지정된 이름 문자열이 NX_SECURE_X509_DNS_NAME_MAX를 초과했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터를 사용하려고 했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_create
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_session_sni_extension_set

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a>nx_secure_x509_extended_key_usage_extension_parse

X.509 인증서에서 X.509 확장 키 사용 확장 찾기 및 구문 분석

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a>Description

이 서비스는 인증서 확인 콜백 내에서 호출되어야 합니다(*nx_secure_tls_session_certificate_callback_set* 참조). X.509 인증서 내에서 특정 확장 키 사용 OID를 검색하고 OID가 있는지 여부를 반환합니다. key_usage 매개 변수는 가변 길이 OID 문자열을 매개 변수로 전달하지 않도록 하기 위해 NetX Secure X.509 및 TLS에서 내부적으로 사용하는 OID의 정수 매핑입니다.

확장 키 사용 확장에 대한 관련 OID는 아래 표에 제공됩니다. 수신된 TLS 서버 인증서에서 확장 키 사용을 확인하려는 일반적인 TLS 클라이언트 구현은 OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH가 있는지 확인합니다. 확장은 있지만 해당 OID가 없는 경우 인증서는 호스트를 TLS 서버로 식별하기에 유효하지 않은 것으로 간주되며 인증서 확인 콜백에서 오류를 반환합니다. 확장 자체가 없으면 TLS 핸드셰이크를 계속할지 여부는 애플리케이션에 달려 있습니다.

인증서 확인 콜백에서 오류 반환 코드 NX_SECURE_X509_KEY_USAGE_ERROR가 애플리케이션 사용을 위해 예약됩니다. 키 사용을 확인하는 동안 오류가 발생하면 콜백에서 이 값을 반환하여 실패 이유를 나타낼 수 있습니다.

| NetX Secure 식별자                                | OID 값         | Description                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH   | 1.3.6.1.5.5.7.3.1 | 인증서를 사용하여 TLS 서버를 식별할 수 있습니다. |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH   | 1.3.6.1.5.5.7.3.2 | 인증서를 사용하여 TLS 클라이언트를 식별할 수 있습니다. |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING  | 1.3.6.1.5.5.7.3.3 | 인증서를 사용하여 코드에 서명할 수 있습니다.             |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT | 1.3.6.1.5.5.7.3.4 | 인증서를 사용하여 메일에 서명할 수 있습니다.           |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING | 1.3.6.1.5.5.7.3.8 | 인증서를 사용하여 타임스탬프에 서명할 수 있습니다.       |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING  | 1.3.6.1.5.5.7.3.9 | 인증서를 사용하여 OCSP 응답에 서명할 수 있습니다.   |

X.509 확장 키 사용 확장에 대한 OID 및 매핑

### <a name="parameters"></a>매개 변수

- **certificate** 확인할 인증서에 대한 포인터입니다.
- **key_usage** 위 표에 제공되는 OID 정수 매핑입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 지정된 키 사용 OID를 찾았습니다.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**(0x181) ASN.1 멀티바이트 태그가 나타났습니다(지원되지 않는 인증서).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**(0x182) 잘못된 ASN.1 필드가 나타났습니다(잘못된 인증서).
- **NX_SECURE_X509_INVALID_TAG_CLASS**(0x190) 잘못된 ASN.1 태그 클래스가 나타났습니다(잘못된 인증서).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**(0x192) 잘못된 확장이 나타났습니다(잘못된 인증서).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND**(0x19b) 제공된 인증서에서 확장 키 사용 확장을 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) 인증서 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find

## <a name="nx_secure_x509_extension_find"></a>nx_secure_x509_extension_find

X.509 인증서에서 X.509 확장 찾기 및 반환

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a>Description

이 서비스는 인증서 확인 콜백 내에서 호출되어야 하며(*nx_secure_tls_session_certificate_callback_set* 참조) 고급 X.509 서비스입니다.

함수는 OID를 기준으로 X.509 인증서 내에서 특정 확장을 검색하고, OID가 있는지 여부를 반환하며, 관련 원시 확장 데이터에 대한 참조를 포함하는 구조체를 반환합니다. extension_id 매개 변수는 가변 길이 OID 문자열을 매개 변수로 전달하지 않도록 하기 위해 NetX Secure X.509 및 TLS에서 내부적으로 사용하는 OID의 정수 매핑입니다.

특정 확장(예: nx_secure_x509_key_usage_extension_parse)에 대해 제공된 도우미 함수는 내부적으로 nx_secure_x509_extension_find를 호출하여 확장 데이터를 가져옵니다.

알려진 X.509 확장에 대한 관련 OID는 아래 표에 제공됩니다.

NX_SECURE_X509_EXTENSION 구조체에는 nx_secure_x509_key_usage_extension_parse와 같은 도우미 함수를 사용하여 DER로 인코딩된 원시 확장 ASN.1 데이터를 빠르게 디코딩할 수 있도록 하는 X.509 인증서에 대한 포인터가 포함되어 있습니다.

특정 확장에 대한 내용은 RFC 5280(X.509 사양) 또는 적절한 도우미 함수에 대한 참조(사용 가능한 경우)를 참조하세요.

NetX Secure X.509의 현재 버전은 X.509 확장을 제한적으로 지원합니다. 추가 도우미 함수는 나중에 추가될 예정입니다.

> [!IMPORTANT]
> 이 서비스는 X.509 확장 및 DER로 인코딩된 ASN.1에 익숙한 사용자를 위한 고급 기능입니다. 이 기능은 이러한 사용자들이 NetX Secure X.509가 현재 도우미 함수를 제공하지 않는 확장에 액세스할 수 있도록 하기 위해 제공됩니다. 도우미 함수를 사용하지 않는 확장의 경우 DER로 인코딩된 원시 ASN.1을 직접 구문 분석해야 합니다.

| NetX Secure 식별자                              | OID 값 | Description                                                                    | 도우미 함수 |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES  | 2.5.29.9  | 디렉터리 특성 – 인증서 주체에 대한 기본 정보 특성  | 예               |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID       | 2.5.29.14 | 특정 공개 키를 식별하는 데 사용                                         | 예               |
| NX_SECURE_TLS_X509_TYPE_KEY_USAGE             | 2.5.29.15 | 인증서 공개 키에 대한 유효한 사용 정보 제공              | 예              |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME     | 2.5.29.17 | 인증서를 식별하기 위한 대체 DNS 이름 제공                     | 예<sup>24</sup>        |
| NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME      | 2.5.29.18 | 인증서 발급자를 식별하기 위한 대체 DNS 이름 제공            | 예               |
| NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS     | 2.5.29.19 | 기본 인증서 사용 제약 조건 정보 제공                        | 예               |
| NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS      | 2.5.29.30 | 인증서 이름을 특정 도메인으로 제한하는 데 사용                        | 예               |
| NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION      | 2.5.29.31 | CRL 배포를 위한 URI 제공                                             | 예               |
| NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES  | 2.5.29.32 | 대규모 PKI 시스템에 대한 인증서 정책 목록                             | 예               |
| NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS | 2.5.29.33 | CA 인증서 정책 목록                                                | 예               |
| NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID     | 2.5.29.35 | 인증서 시그니처와 연결된 특정 공개 키를 식별하는 데 사용 | 예               |
| NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS    | 2.5.29.36 | CA 정책 제약 조건                                                          | 예               |
| NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE   | 2.5.29.37 | 추가 OID 기반 키 사용 정보                                     | 예              |
| NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL          | 2.5.29.46 | 델타 CRL을 얻기 위한 정보 제공                                  | 예               |
| NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY     | 2.5.29.54 | AnyPolicy를 사용할 수 없음을 나타내는 CA 인증서 필드                  | 예               |

X.509 확장에 대한 OID 및 매핑

24. SubjectAltName 확장은 서비스 nx_secure_x509_common_name_dns_check에서 DNS 이름 확인의 일부로 구문 분석됩니다.

### <a name="parameters"></a>매개 변수

- **certificate** 확인할 인증서에 대한 포인터입니다.
- **extension** 확장 데이터 포인터 및 길이를 포함하는 반환 구조체입니다.
- **extension_id** 위 테이블의 OID 정수 매핑입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 지정된 확장 OID를 찾았으며 데이터가 반환되었습니다.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**(0x181) ASN.1 멀티바이트 태그가 나타났습니다(지원되지 않는 인증서).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**(0x182) 잘못된 ASN.1 필드가 나타났습니다(잘못된 인증서).
- **NX_SECURE_X509_INVALID_TAG_CLASS**(0x190) 잘못된 ASN.1 태그 클래스가 나타났습니다(잘못된 인증서).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**(0x192) 잘못된 확장이 나타났습니다.
- **NX_SECURE_X509_EXTENSION_NOT_FOUND**(0x19b) 제공된 인증서에서 지정된 확장 OID를 찾을 수 없습니다.
- **NX_PTR_ERROR** (0x07) 인증서 또는 확장 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extended_key_usage_extension_parse

## <a name="nx_secure_x509_key_usage_extension_parse"></a>nx_secure_x509_key_usage_extension_parse

X.509 인증서에서 X.509 키 사용 확장 찾기 및 구문 분석

### <a name="prototype"></a>프로토타입

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a>Description

이 서비스는 인증서 확인 콜백 내에서 호출되어야 합니다(*nx_secure_tls_session_certificate_callback_set* 참조). 키 사용 확장을 검색하고, 찾으면 "bitfield" 매개 변수에 키 사용 비트 필드를 반환합니다.

X.509 사양(RFC 5280)에서 정의한 비트는 아래 표에 제공됩니다. 적절한 비트 마스크(및 값이 0이 아님)가 있는 비트 AND는 각 비트의 값을 제공합니다.

비트 필드의 DER 인코딩은 불필요한 0을 제거하므로 원시 인증서 데이터의 실제 비트 위치는 디코딩된 비트 필드의 위치와 다를 수 있습니다. 제공된 비트 마스크는 DER로 인코딩된 원시 인증서 데이터가 아닌 nx_secure_x509_key_usage_extension_parse를 통해 반환된 디코딩된 비트 필드에서만 사용해야 합니다.

인증서 확인 콜백에서 오류 반환 코드 NX_SECURE_X509_KEY_USAGE_ERROR가 애플리케이션 사용을 위해 예약됩니다. 키 사용을 확인하는 동안 오류가 발생하면 콜백에서 이 값을 반환하여 실패 이유를 나타낼 수 있습니다.

| NetX Secure 식별자                            | 비트 위치 | Description                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE  | 0            | 디지털 서명에 인증서를 사용할 수 있습니다.                                                                                                               |
| NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION    | 1            | 인증서를 사용하여 인증서 및 CRL에 대한 디지털 서명 이외의 디지털 서명을 확인할 수 있습니다.                                                              |
| NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT   | 2            | 인증서를 사용하여 대칭 키(키 전송)를 암호화할 수 있습니다.                                                                                            |
| NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT  | 3            | 인증서를 사용하여 원시 사용자 데이터를 직접 암호화할 수 있습니다(일반적이지 않음).                                                                                         |
| NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT      | 4            | 인증서를 키 규약(Diffie-Hellman과 유사)에 사용할 수 있습니다.                                                                                           |
| NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN     | 5            | 인증서를 사용하여 다른 인증서에 서명하고 확인할 수 있습니다(인증서가 CA 또는 ICA 인증서임).                                                  |
| NX_SECURE_X509_KEY_USAGE_CRL_SIGN           | 6            | 인증서 퍼블릭 키를 사용하여 CRL에서 서명을 확인합니다.                                                                                                  |
| NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY      | 7            | 키 계약 비트(비트 4)와 함께 사용됩니다. 설정 시, 키 계약 중에 암호화할 때만 인증서 키를 사용할 수 있습니다. 키 계약 비트가 설정되지 않은 경우 정의되지 않습니다. |
| NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY      | 8            | 키 계약 비트(비트 4)와 함께 사용됩니다. 설정 시, 키 계약 중에 암호를 해독할 때만 인증서 키를 사용할 수 있습니다. 키 계약 비트가 설정되지 않은 경우 정의되지 않습니다. |

X.509 키 사용 확장에 대한 비트 마스크 및 값

### <a name="parameters"></a>매개 변수

- **certificate** 확인할 인증서에 대한 포인터입니다.
- **bitfield** 확장에서 전체 비트 필드를 반환합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 키 사용 확장을 찾았으며 비트 필드를 반환했습니다.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**(0x181) ASN.1 멀티바이트 태그가 나타났습니다(지원되지 않는 인증서).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**(0x182) 잘못된 ASN.1 필드가 나타났습니다(잘못된 인증서).
- **NX_SECURE_X509_INVALID_TAG_CLASS**(0x190) 잘못된 ASN.1 태그 클래스가 나타났습니다(잘못된 인증서).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**(0x192) 잘못된 확장이 나타났습니다(잘못된 인증서).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND**(0x19b) 제공된 인증서에서 키 사용 확장을 찾을 수 없습니다.
- **NX_PTR_ERROR** (0x07) 인증서 또는 비트 필드 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_extended_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find
