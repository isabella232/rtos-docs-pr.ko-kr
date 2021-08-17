---
title: 부록 A - Azure RTOS NetX Secure DTLS 반환/오류 코드
description: Azure RTOS NetX Secure DTLS 서비스로 반환될 수 있는 가능한 오류 코드를 나열합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: reference
ms.service: rtos
ms.openlocfilehash: f4994a5014d3691b4a78f225fb68b475bf5a8cdab630162a94130f321be09da5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782441"
---
# <a name="appendix-a-azure-rtos-netx-secure-dtls-returnerror-codes"></a>부록 A: Azure RTOS NetX Secure DTLS 반환/오류 코드

## <a name="netx-secure-tlsdtls-return-codes"></a>NetX Secure TLS/DTLS 반환 코드

아래의 표 1은 Azure RTOS NetX Secure DTLS 서비스로 반환될 수 있는 가능한 오류 코드를 나열합니다. 서비스가 UDP 또는 IP 오류 코드를 반환할 수도 있습니다. TLS 값은 0x101에서 시작하고 TCP/IP/UDP 값은 0x100 이하입니다. X.509 반환 값은 0x181에서 시작합니다. IP 및 UDP 반환 값에 대한 정보는 NetX TCP/IP/UDP 문서를 참조하고 X.509 값은 아래를 참조하세요.

| **오류 이름**                                        | **값** | **설명**                                                                                                                                               |
| ----------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_TLS_SUCCESS                              | 0x00      | 함수가 성공적으로 반환되었습니다. (NX_SUCCESS와 동일).                                                                                                        |
| NX_SECURE_TLS_SESSION_UNINITIALIZED               | 0x101     | 초기화되지 않은 소켓으로 TLS 주 루프가 호출되었습니다.                                                                                                               |
| NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE          | 0x102     | TLS 레코드 계층에 인식할 수 없는 메시지 유형이 수신되었습니다.                                                                                                       |
| NX_SECURE_TLS_INVALID_STATE                       | 0x103     | 내부 오류 - 인식할 수 없는 상태입니다.                                                                                                                        |
| NX_SECURE_TLS_INVALID_PACKET                      | 0x104     | 내부 오류 - 수신된 패킷에 TLS 데이터가 포함되지 않았습니다.                                                                                                    |
| NX_SECURE_TLS_UNKNOWN_CIPHERSUITE                 | 0x105     | 선택한 암호 그룹이 지원되지 않습니다. 서버의 경우 내부 오류입니다. 클라이언트의 경우에는 원격 호스트가 잘못된 암호 그룹(오류 또는 공격)을 보냈습니다.            |
| NX_SECURE_TLS_UNSUPPORTED_CIPHER                  | 0x106     | 암호화 또는 암호 해독을 수행할 때 선택한 암호가 사용하지 않도록 설정되었거나 사용할 수 없습니다.                                                                           |
| NX_SECURE_TLS_HANDSHAKE_FAILURE                   | 0x107     | 핸드셰이크 중 메시지를 처리할 때 작업이 실패했습니다.                                                                                              |
| NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE           | 0x108     | 들어오는 레코드에 생성한 것과 일치하지 않는 MAC이 있습니다.                                                                                         |
| NX_SECURE_TLS_TCP_SEND_FAILED                    | 0x109     | 어떤 이유로 인해 레코드의 나가는 TCP 전송이 실패했습니다.                                                                                                     |
| NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH           | 0x10A     | 들어오는 메시지의 길이가 잘못되었습니다(일반적으로 인증서 메시지에서와 같이 헤더의 길이가 아닌 길이).                               |
| NX_SECURE_TLS_BAD_CIPHERSPEC                      | 0x10B     | 들어오는 ChangeCipherSpec 메시지가 잘못되었습니다.                                                                                                           |
| NX_SECURE_TLS_INVALID_SERVER_CERT                | 0x10C     | 들어오는 서버 인증서가 올바르게 구문 분석되지 않았습니다.                                                                                                       |
| NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER          | 0x10D     | 서버에서 제공하는 인증서가 공개 키 작업을 지원하지 않습니다.                                                                        |
| NX_SECURE_TLS_NO_SUPPORTED_CIPHERS               | 0x10E     | 지원되는 암호 그룹이 없는 ClientHello가 수신되었습니다.                                                                                                        |
| NX_SECURE_TLS_UNKNOWN_TLS_VERSION                | 0x10F     | 들어오는 레코드에 인식되지 않은 TLS 버전이 포함되었습니다.                                                                                                   |
| NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION            | 0x110     | 들어오는 레코드에 유효한 TLS 버전이 있지만 지원되지 않습니다.                                                                                     |
| NX_SECURE_TLS_ALLOCATE_PACKET_FAILED             | 0x111     | TLS 메시지에 대한 내부 패킷 할당이 실패했습니다.                                                                                                       |
| NX_SECURE_TLS_INVALID_CERTIFICATE                 | 0x112     | X509 인증서가 올바르게 구문 분석되지 않았습니다.                                                                                                                  |
| NX_SECURE_TLS_NO_CLOSE_RESPONSE                  | 0x113     | TLS 세션을 닫는 동안 원격 호스트에서 CloseNotify가 수신되지 않았습니다.                                                                               |
| NX_SECURE_TLS_ALERT_RECEIVED                      | 0x114     | 원격 호스트가 오류를 나타내는 경고를 보냈습니다. 연결이 닫힙니다.                                                                                |
| NX_SECURE_TLS_FINISHED_HASH_FAILURE              | 0x115     | 수신된 완료 메시지 해시가 로컬에서 생성된 해시와 일치하지 않습니다. 핸드셰이크 손상입니다.                                                              |
| NX_SECURE_TLS_UNKNOWN_CERT_SIG_ALGORITHM        | 0x116     | 확인 중 인증서에 지원되지 않는 서명 알고리즘이 포함되었습니다.                                                                                     |
| NX_SECURE_TLS_CERTIFICATE_SIG_CHECK_FAILED      | 0x117     | 인증서 서명 확인에 실패했습니다. 인증서 데이터가 서명과 일치하지 않았습니다.                                                                 |
| NX_SECURE_TLS_BAD_COMPRESSION_METHOD             | 0x118     | 지원되지 않는 압축 메서드가 사용된 Hello 메시지가 수신되었습니다.                                                                                              |
| NX_SECURE_TLS_CERTIFICATE_NOT_FOUND              | 0x119     | 인증서 목록의 작업에서 일치하는 인증서를 찾을 수 없습니다.                                                                                     |
| NX_SECURE_TLS_INVALID_SELF_SIGNED_CERT          | 0x11A     | 원격 호스트가 자체 서명된 인증서를 보냈지만 NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES가 정의되지 않았습니다.                                              |
| NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND      | 0x11B     | 원격 인증서가 신뢰할 수 있는 로컬 저장소에 없는 발급자와 함께 수신되었습니다.                                                                              |
| NX_SECURE_TLS_OUT_OF_ORDER_MESSAGE              | 0x11C     | DTLS 메시지가 잘못된 순서로 수신되었습니다. 삭제된 데이터그램이 원인일 수 있습니다.                                                                    |
| NX_SECURE_TLS_INVALID_REMOTE_HOST                | 0x11D     | 인식할 수 없는 원격 호스트에서 패킷이 수신되었습니다.                                                                                            |
| NX_SECURE_TLS_INVALID_EPOCH                       | 0x11E     | DTLS 메시지가 수신되었고 DTLS 세션과 일치하지만 잘못된 epoch가 포함되어 무시해야 합니다.                                                   |
| NX_SECURE_TLS_REPEAT_MESSAGE_RECEIVED            | 0x11F     | 이미 확인된 시퀀스 번호의 DTLS 메시지가 수신되었습니다. 무시합니다.                                                                           |
| NX_SECURE_TLS_NEED_DTLS_SESSION                  | 0x120     | DTLS용으로 초기화되지 않은 TLS 세션이 DTLS API에 사용되었습니다.                                                                                       |
| NX_SECURE_TLS_NEED_TLS_SESSION                   | 0x121     | DTLS용으로 초기화되었고 TLS용으로 초기화되지 않은 TLS 세션이 TLS API에 사용되었습니다.                                                                                |
| NX_SECURE_TLS_SEND_ADDRESS_MISMATCH              | 0x122     | 호출자가 세션과 일치하지 않는 IP 주소 또는 포트를 사용하여 DTLS 세션으로 데이터를 보내려고 시도했습니다.                                                  |
| NX_SECURE_TLS_NO_FREE_DTLS_SESSIONS             | 0x123     | 새 연결이 캐시에서 DTLS 세션을 가져오려고 시도했지만 사용 가능한 항목이 없었습니다.                                                                        |
| NX_SECURE_DTLS_SESSION_NOT_FOUND                 | 0x124     | 호출자가 DTLS 세션을 검색했지만 제공된 IP 주소 및 포트가 캐시에 있는 항목과 일치하지 않았습니다.                                             |
| NX_SECURE_TLS_NO_MORE_PSK_SPACE                 | 0x125     | 호출자가 PSK를 TLS 세션에 추가하려고 시도했지만 지정된 세션에 공간이 더 이상 없습니다.                                                          |
| NX_SECURE_TLS_NO_MATCHING_PSK                    | 0x126     | 원격 호스트가 로컬 저장소 항목과 일치하지 않는 PSK ID 힌트를 제공했습니다.                                                                         |
| NX_SECURE_TLS_CLOSE_NOTIFY_RECEIVED              | 0x127     | TLS 세션이 원격 호스트에서 세션이 완료되었음을 나타내는 CloseNotify 경고를 수신했습니다.                                                           |
| NX_SECURE_TLS_NO_AVAILABLE_SESSIONS              | 0x128     | TLS 개체에 연결 처리를 위해 사용할 수 있는 TLS 세션이 없습니다.                                                                                         |
| NX_SECURE_TLS_NO_CERT_SPACE_ALLOCATED           | 0x129     | 들어오는 원격 인증서에 할당된 인증서 공간이 없습니다.                                                                                          |
| NX_SECURE_TLS_PADDING_CHECK_FAILED               | 0x12A     | 들어오는 메시지의 암호화 패딩이 올바르지 않습니다.                                                                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_TYPE        | 0x12B     | CertificateVerifyRequest를 처리할 때 원격 서버에서 지원되는 인증서 형식이 제공되지 않았습니다.                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_ALG         | 0x12C     | CertificateVerifyRequest를 처리할 때 원격 서버에서 지원되는 서명 알고리즘이 제공되지 않았습니다.                                                 |
| NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE            | 0x12D     | 인증서에 할당된 인증서 버퍼 공간이 충분하지 않습니다.                                                                                              |
| NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED           | 0x12E     | 들어오는 TLS 레코드의 프로토콜 버전이 설정된 세션의 버전과 일치하지 않았습니다.                                                          |
| NX_SECURE_TLS_NO_RENEGOTIATION_ERROR             | 0x12F     | HelloRequest 메시지가 수신되었지만 다시 협상하지 않습니다.                                                                                           |
| NX_SECURE_TLS_UNSUPPORTED_FEATURE                 | 0x130     | 사용하지 않도록 설정된 기능이 TLS 세션 또는 핸드셰이크 중에 발생했습니다.                                                                                |
| NX_SECURE_TLS_CERTIFICATE_VERIFY_FAILURE         | 0x131     | 원격 클라이언트의 CertificateVerify 메시지에서 클라이언트 인증서를 확인하지 못했습니다.                                                                     |
| NX_SECURE_TLS_EMPTY_REMOTE_CERTIFICATE_RECEIVED | 0x132     | 원격 호스트가 빈 인증서 메시지를 보냈습니다.                                                                                                            |
| NX_SECURE_TLS_RENEGOTIATION_EXTENSION_ERROR      | 0x133     | 보안 재협상 표시 확장을 처리하거나 보낼 때 오류가 발생했습니다.                                                                     |
| NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE     | 0x134     | 활성 상태가 아닌 TLS 세션으로 세션 재협상을 시도했습니다.                                                                                |
| NX_SECURE_TLS_PACKET_BUFFER_TOO_SMALL           | 0x135     | TLS가 할당된 패킷 버퍼에 비해 너무 큰 레코드를 수신했습니다. 레코드를 처리할 수 없습니다.                                                   |
| NX_SECURE_TLS_EXTENSION_NOT_FOUND                | 0x136     | TLS 핸드셰이크 중 지정된 확장이 원격 호스트에서 수신되지 않았습니다.                                                                         |
| NX_SECURE_TLS_SNI_EXTENSION_INVALID              | 0x137     | 잘못된 서버 이름 표시 확장이 TLS에 수신되었습니다.                                                                                                     |
| NX_SECURE_TLS_CERT_ID_INVALID                    | 0x138     | 애플리케이션이 잘못된 인증서 ID 값(예: 0)으로 서버 인증서를 추가하려고 시도했습니다.                                                                |
| NX_SECURE_TLS_CERT_ID_DUPLICATE                  | 0x139     | 애플리케이션이 로컬 저장소에 이미 있는 인증서 ID로 서버 인증서를 추가하려고 시도했습니다.                                                       |
| NX_SECURE_TLS_RENEGOTIATION_FAILURE               | 0x13A     | 원격 호스트가 보안 재협상 표시 확장 또는 SCSV 의사 암호 그룹을 제공하지 않았기 때문에 보안 재협상을 수행할 수 없습니다.     |
| NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE             | 0x13B     | 암호화 작업을 수행하려고 시도하는 중 암호 그룹 테이블의 항목 중 하나(또는 해당 함수 포인터 중 하나)가 NULL로 잘못 설정되었습니다. |

**표 1 - NetX Secure TLS 오류 반환 코드**

## <a name="netx-secure-x509-return-codes"></a>NetX Secure X.509 반환 코드

아래의 표 2에서는 NetX Secure X.509 서비스로 반환될 수 있는 오류 코드를 보여줍니다. 서비스가 다른 오류 코드를 반환할 수도 있습니다. X.509 반환 값은 0x181에서 시작하고 TLS 값은 0x101에서 시작하며, TCP/IP 값은 0x100 이하입니다. TCP/IP 반환 값에 대한 자세한 내용은 NetX TCP/IP 문서를 참조하고 TLS 반환 값은 위 내용을 참조하세요.

| **오류 이름**                                   | **값** | **설명**                                                                                                        |
| ------------------------------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_SUCCESS                        | 0x00      | 성공적인 반환 상태입니다. (NX_SUCCESS와 동일)                                                                        |
| NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED    | 0x181     | 현재 지원되지 않는 다중 바이트 ASN.1 태그를 발견했습니다.                                                       |
| NX_SECURE_X509_ASN1_LENGTH_TOO_LONG        | 0x182     | 처리할 수 있는 것보다 긴 길이의 값을 발견했습니다.                                                                  |
| NX_SECURE_X509_FOUND_NON_ZERO_PADDING      | 0x183     | 패딩 값이 0이어야 하지만, 다른 값을 발견했습니다.                                                               |
| NX_SECURE_X509_MISSING_PUBLIC_KEY           | 0x184     | X509에 공개 키가 필요하지만 찾을 수 없습니다.                                                                        |
| NX_SECURE_X509_INVALID_PUBLIC_KEY           | 0x185     | 공개 키를 찾았지만 키가 잘못되었거나 형식이 잘못되었습니다.                                                      |
| NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE | 0x186     | 최상위 ASN.1 블록이 시퀀스가 아닙니다. 잘못된 X509 인증서입니다.                                                |
| NX_SECURE_X509_MISSING_SIGNATURE_ALGORITHM  | 0x187     | 서명 알고리즘 식별자가 필요하지만 찾을 수 없습니다.                                                           |
| NX_SECURE_X509_INVALID_CERTIFICATE_DATA     | 0x188     | 인증서 ID 데이터가 잘못된 형식입니다.                                                                     |
| NX_SECURE_X509_UNEXPECTED_ASN1_TAG          | 0x189     | X509 형식에 대해 특정 ASN.1 태그가 필요하지만 다른 항목이 발견되었습니다.                                      |
| NX_SECURE_PKCS1_INVALID_PRIVATE_KEY         | 0x18A     | PKCS#1 프라이빗 키 파일이 전달되었지만 형식이 잘못되었습니다.                                            |
| NX_SECURE_X509_CHAIN_TOO_SHORT              | 0x18B     | X509 인증서 체인이 체인 빌드 중 전체 체인을 저장하기에 너무 짧습니다.                                |
| NX_SECURE_X509_CHAIN_VERIFY_FAILURE         | 0x18C     | X509 인증서 체인을 확인할 수 없습니다(범용 오류).                                                 |
| NX_SECURE_X509_PKCS7_PARSING_FAILED         | 0x18D     | X.509 PKCS#7로 인코딩된 서명을 구문 분석하지 못했습니다.                                                                     |
| NX_SECURE_X509_CERTIFICATE_NOT_FOUND        | 0x18E     | 인증서를 조회할 때 일치하는 항목이 발견되지 않았습니다.                                                              |
| NX_SECURE_X509_INVALID_VERSION               | 0x18F     | 지정된 버전과 호환되지 않는 필드가 인증서에 포함되었습니다.                                           |
| NX_SECURE_X509_INVALID_TAG_CLASS            | 0x190     | 잘못된 태그 클래스 값이 있는 ASN.1 태그가 인증서에 포함되었습니다.                                                   |
| NX_SECURE_X509_INVALID_EXTENSIONS            | 0x191     | 인증서에 확장 TLV가 포함되었지만 시퀀스가 포함되지 않았습니다.                                          |
| NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE   | 0x192     | 인증서에 잘못된 X.509 확장 시퀀스가 포함되어 있습니다.                                                   |
| NX_SECURE_X509_CERTIFICATE_EXPIRED           | 0x193     | 인증서에 현재 시간보다 적은 "not after" 필드가 있습니다.                                             |
| NX_SECURE_X509_CERTIFICATE_NOT_YET_VALID   | 0x194     | 인증서에 현재 시간보다 큰 "not before" 필드가 있습니다.                                         |
| NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH     | 0x195     | 인증서 일반 이름 또는 주체 대체 이름이 지정된 DNS TLD와 일치하지 않습니다.                                           |
| NX_SECURE_X509_INVALID_DATE_FORMAT          | 0x196     | 인증서에 인식된 형식이 아닌 날짜 필드가 포함되어 있습니다.                                               |
| NX_SECURE_X509_CRL_ISSUER_MISMATCH          | 0x197     | 제공된 CRL 및 인증서가 동일한 인증 기관에서 발급되지 않았습니다.                                      |
| NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED  | 0x198     | 발급자에 대한 CRL 서명 확인에 실패했습니다.                                                                       |
| NX_SECURE_X509_CRL_CERTIFICATE_REVOKED      | 0x199     | 유효한 CRL에서 인증서를 찾아 해지되었습니다.                                                 |
| NX_SECURE_X509_WRONG_SIGNATURE_METHOD       | 0x19A     | 서명의 유효성을 검사할 때 서명 메서드가 필요한 메서드와 일치하지 않습니다.                          |
| NX_SECURE_X509_EXTENSION_NOT_FOUND          | 0x19B     | 확장을 찾는 동안 일치하는 ID를 가진 확장을 찾을 수 없습니다.                                                |
| NX_SECURE_X509_ALT_NAME_NOT_FOUND          | 0x19C     | subjectAltName 확장에서 이름을 검색했지만 찾을 수 없습니다.                                               |
| NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE    | 0x19D     | 지정된 프라이빗 키 형식이 알 수 없거나 잘못된 형식입니다.                                                                         |
| NX_SECURE_X509_NAME_STRING_TOO_LONG        | 0x19E     | 내부 버퍼에 너무 긴 이름 문자열을 전달했습니다(DNS 이름 등).                                        |
| NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND    | 0x19F     | 확장 키 사용 확장을 검색할 때 지정된 키 사용 OID를 찾을 수 없습니다.                               |
| NX_SECURE_X509_KEY_USAGE_ERROR              | 0x1A0     | 인증서 검사 확인 중 키 사용에 오류가 있는 경우 애플리케이션 콜백으로 반환됩니다. |

**표 2 - NetX Secure X.509 오류 반환 코드**
