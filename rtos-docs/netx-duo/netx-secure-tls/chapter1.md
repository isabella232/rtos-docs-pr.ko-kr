---
title: 1장 - Azure RTOS NetX Secure 소개
description: 이 장에는 Azure RTOS NetX Secure에 대한 소개와 해당 애플리케이션 및 혜택에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8f4c7a97564cd2f702f9887181b36297b42fa492
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810500"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-secure"></a>1장 - Azure RTOS NetX Secure 소개

Azure RTOS NetX Secure는 포함된 ThreadX 기반 애플리케이션용으로 설계된 TLS/SSL을 비롯한 암호화 네트워크 보안 표준의 고성능 실시간 구현입니다. 이 장에는 NetX Secure에 대한 소개와 해당 애플리케이션 및 혜택에 대한 설명이 포함되어 있습니다.

## <a name="netx-secure-unique-features"></a>NetX Secure 고유 기능

대부분의 다른 TLS 구현과 달리 NetX Secure는 광범위한 임베디드 하드웨어 플랫폼을 지원하도록 처음부터 설계되었으며 소형 마이크로 컨트롤러 애플리케이션에서 사용 가능한 가장 강력한 임베디드 프로세서로 쉽게 확장할 수 있습니다. 이 코드는 임베디드 시스템의 제한된 리소스를 염두에 두고 작성되었으며, TLS를 통한 보안 네트워크 통신을 제공하는 데 필요한 메모리 공간을 줄이기 위한 다양한 구성 옵션을 제공합니다.

## <a name="rfcs-supported-by-netx-secure"></a>NetX Secure에서 지원되는 RFC 

NetX Secure는 TLS와 관련된 다음과 같은 프로토콜을 지원합니다. TLS 및 암호화와 관련된 다양한 RFC가 있으므로 목록은 포괄적이지 않을 수 있습니다. NetX Secure는 작은 메모리 사용 공간과 효율적인 실행으로 실시간 운영 체제의 제약 조건 내에서 모든 일반 권장 사항 및 기본 요구 사항을 따릅니다.

| RFC      | Description                                                                                                 | 페이지 |
|----------|-------------------------------------------------------------------------------------------------------------|------|
| RFC 2104 | HMAC: 메시지 인증을 위한 키 해싱                                                              | 33   |
| RFC 2246 | TLS 프로토콜 버전 1.0                                                                                | 19   |
| RFC 3268 | TLS(전송 계층 보안)에 대한 AES(Advanced Encryption Standard) Ciphersuites                          | 31   |
| RFC 3447 | PKCS(공개 키 암호화 표준) #1: RSA 암호화 사양 버전 2.1                    | 32   |
| RFC 4279 | TLS용 미리 공유 키 Ciphersuites                                                                         | 39   |
| RFC 4346 | TLS(전송 계층 보안) 프로토콜 버전 1.1                                                     | 19   |
| RFC 5246 | TLS(전송 계층 보안) 프로토콜 버전 1.2                                                     | 19   |
| RFC 5280 | X.509 PKI 인증서(v3)                                                                                 | 41   |
| RFC 5746 | TLS(전송 계층 보안) 재협상 표시 확장                                           |      |
| RFC 5869 | HKDF(HMAC 기반 추출 및 확장 키 파생 함수)                                                | 19   |
| RFC 6066<sup>1</sup> | TLS(전송 계층 보안) 확장: 확장 정의                                            | 19   |
| RFC 6234 | 미국 보안 해시 알고리즘(SHA 및 SHA 기반 HMAC 및 HKDF)                                                 | 33   |
| RFC 8443 | TLS(Transport Layer Security) 버전 1.2 및 이전 버전에 대한 ECC(타원 곡선 암호화) Cipher Suite |      |
| RFC 8446 | TLS(전송 계층 보안) 프로토콜 버전 1.3                                                     | 19   |

1. 버전 6.0부터 RFC 6066의 SNI(서버 이름 표시) 확장만 완전히 지원됩니다.

## <a name="netx-secure-requirements"></a>NetX Secure 요구 사항

NetX Secure 런타임 라이브러리가 제대로 작동하려면 NetX IP 인스턴스가 이미 생성되어 있어야 합니다. 또한 애플리케이션에 따라 TLS 인스턴스를 식별하거나 원격 호스트에서 들어오는 인증서를 확인하려면 하나 이상의 DER 인코딩 X.509 디지털 인증서가 필요합니다. NetX Secure 패키지에는 추가 요구 사항이 없습니다.

## <a name="netx-secure-constraints"></a>NetX Secure 제약 조건

NetX Secure 프로토콜은 TLS 1.2의 경우 RFC 5246 표준, TLS 1.3의 경우 RFC 8446의 요구 사항을 구현하며, RFC 4346(TLS 1.1) 및 2246(TLS 1.0)과의 이전 버전과의 호환성을 제공합니다(기본적으로 사용하지 않도록 설정됨). 단, 다음과 같은 제약 조건이 있습니다.

- SHA-256을 사용하는 Ciphersuite는 TLS 1.2 및 TLS 1.3에 대해 지원됩니다. TLS 1.2 이전 버전에서 TLS 핸드셰이크는 고정 해시 루틴을 사용하여 TLS 핸드셰이크 메시지가 변조되지 않았는지 확인합니다. 버전 1.2부터 핸드셰이크는 Ciphersuite와 함께 제공되는 해시 루틴을 사용합니다. TLS는 어떤 해시 루틴이 사용되는지 미리 알 수 없으며 핸드셰이크 메시지를 캐시해야 합니다. SHA-256에 대한 해시를 수정하면 NetX Secure TLS는 다른 TLS 구현보다 더 작은 RAM 공간으로 작동할 수 있습니다. 메모리 사용을 적절하게 처리할 수 있게 되면 이후 버전에서 이 제한이 제거됩니다. *중요 정보: 이 제한은 Ciphersuite 선택에 **한해서만** 적용됩니다. X.509 인증서 서명에는 동일한 제한이 적용되지 않으며 지원되는 해시 루틴이 모두 사용될 수 있습니다.
- 임베디드 디바이스의 특성으로 인해 일부 애플리케이션에는 최대 TLS 레코드 크기인 16KB를 지원하는 리소스가 없을 수 있습니다. NetX Secure는 충분한 리소스가 있는 디바이스에서 16KB의 레코드를 처리할 수 있습니다. TLS 리어셈블리 버퍼(*nx_secure_tls_session_packet_buffer_set* 에 대한 API 참조)는 상호 운용성 문제가 발생할 경우 16KB보다 작은 크기로 설정할 **수도 있습니다**. 리어셈블리 버퍼보다 큰 유효한 TLS 레코드가 수신되면 NetX Secure TLS는 오류가 발생한 TLS 세션을 중단합니다. 일반적으로 버퍼는 항상 18KB(암호화 패딩에 대해 16KB TLS 레코드 크기 + 2KB)로 설정되어야 하고 제어되는 설정에서 더 작게 설정됩니다(예: 원격 호스트는 최대 TLS 레코드 크기를 보장함).
  > [!NOTE]
  > 일반적으로 패킷 리어셈블리 버퍼는 TLS 최대 레코드 크기보다 작을 수 없습니다. 그러나 원격 호스트의 특성을 잘 알고 있는 경우(예: 완전히 닫힌 시스템) 크기를 줄여서 일부 RAM 공간을 다시 확보할 수 있습니다.
- 최소 인증서 확인. NetX Secure는 인증서에 대해 기본 X.509 체인 확인을 수행하여 인증서가 유효하고 신뢰할 수 있는 인증 기관에 의해 서명되었는지 확인하고, 원격 호스트의 최상위 도메인 이름과 비교할 애플리케이션의 인증서 일반 이름을 제공할 수 있습니다. 실시간 클록을 사용할 수 있는 경우 인증서 만료 날짜를 확인하는 데 사용할 수 있습니다(API nx_secure_tls_session_time_function_set 참조). 단, 인증서 확장 및 기타 데이터의 확인은 애플리케이션 구현자의 책임입니다.
- 소프트웨어 기반 암호화는 프로세서 집약적입니다. NetX Secure 소프트웨어 기반 암호화 루틴은 성능에 맞게 최적화되었지만 대상 프로세서의 성능에 따라 매우 긴 작업이 발생할 수 있습니다. 하드웨어 기반 암호화를 사용할 수 있는 경우 NetX Secure TLS의 성능을 최적화하는 데 사용해야 합니다.
- TLS 핸드셰이크 레코드 조각화는 지원되지 않습니다. 특정 TLS 핸드셰이크 레코드 메시지가 너무 크면 여러 TLS 레코드 간에 분할될 수 있습니다. 현재 NetX Secure TLS는 이를 오류로 처리합니다. 임베디드 시스템의 메모리 요구 사항에 따라 더 큰 핸드셰이크 레코드 메시지는 처리할 수 없지만, 과도하게 큰 인증서 체인을 사용하는 특정 TLS 호스트와 통신할 때 제한으로 인해 오류가 발생할 수 있습니다.
- TLS 서버는 로컬 저장소에 여러 인증서가 있는 경우 동적 인증서 선택을 지원하지 않습니다. 
- X509 인증서 KeyUsage는 관찰되지 않습니다. 
- ECDH 기반 Ciphersuite은 지원되지 않습니다. 대신 ECDHE를 사용합니다.
