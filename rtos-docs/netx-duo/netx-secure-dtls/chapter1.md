---
title: 1장 - Azure RTOS NetX Secure DTLS 소개
description: Azure RTOS NetX Secure DTLS는 임베디드 ThreadX 기반 애플리케이션용으로 설계된 데이터그램 전송 계층 보안 프로토콜의 실시간 구현입니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a7fe51fd1e141c0c525a98986ca3058732b61843f8bd79bf24fc5ac986147501
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797044"
---
# <a name="chapter-1-introduction-to-azure-rtos-netx-secure-dtls"></a>1장: Azure RTOS NetX Secure DTLS 소개

Azure RTOS NetX Secure DTLS는 임베디드 ThreadX 기반 애플리케이션 전용으로 설계된 데이터그램 전송 계층 보안 프로토콜의 고성능 실시간 구현입니다. 이 장에는 NetX Secure DTLS에 대한 소개와 해당 애플리케이션 및 혜택에 대한 설명이 포함되어 있습니다.

## <a name="netx-secure-unique-features"></a>NetX Secure 고유 기능

대부분의 다른 TLS/DTLS 구현과 달리 NetX Secure는 광범위한 임베디드 하드웨어 플랫폼을 지원하도록 처음부터 설계되었으며 소형 마이크로 컨트롤러 애플리케이션에서 사용 가능한 가장 강력한 임베디드 프로세서로 쉽게 확장할 수 있습니다. 이 코드는 임베디드 시스템의 제한된 리소스를 염두에 두고 작성되었으며, TLS 또는 DTLS를 통한 보안 네트워크 통신을 제공하는 데 필요한 메모리 공간을 줄이기 위한 다양한 구성 옵션을 제공합니다.

## <a name="rfcs-supported-by-netx-secure"></a>NetX Secure에서 지원되는 RFC

NetX Secure는 TLS 및 DTLS와 관련된 다음 프로토콜을 지원합니다. TLS/DTLS 및 암호화와 관련된 다양한 RFC가 있으므로 목록은 포괄적이지 않을 수 있습니다. NetX Secure는 작은 메모리 사용 공간과 효율적인 실행으로 실시간 운영 체제의 제약 조건 내에서 모든 일반 권장 사항 및 기본 요구 사항을 따릅니다.


| RFC | Description |
| --- | ----------- |
| RFC 6347 | 데이터그램 전송 계층 보안 버전 1.2 |
| RFC 2246 | TLS 프로토콜 버전 1.0|
| RFC 4346 | TLS(전송 계층 보안) 프로토콜 버전 1.1 |
| RFC 5246 | TLS(전송 계층 보안) 프로토콜 버전 1.2 |
| RFC 5280 | X.509 PKI 인증서(v3) |
| RFC 3268 | TLS(전송 계층 보안)에 대한 AES(Advanced Encryption Standard) Ciphersuites |
| RFC 3447 | PKCS(공개 키 암호화 표준) #1: RSA 암호화 사양 버전 2.1 |
| RFC 2104 | HMAC: 메시지 인증을 위한 키 해싱 |
| RFC 6234 | 미국 보안 해시 알고리즘(SHA 및 SHA 기반 HMAC 및 HKDF) |
| RFC 4279 | TLS용 미리 공유 키 Ciphersuites |

## <a name="netx-secure-dtls-requirements"></a>NetX Secure DTLS 요구 사항

NetX Secure 런타임 라이브러리가 제대로 작동하려면 NetX IP 인스턴스가 이미 생성되어 있어야 합니다. 또한 애플리케이션에 따라 TLS/DTLS 인스턴스를 식별하거나 원격 호스트에서 들어오는 인증서를 확인하려면 하나 이상의 DER 인코딩 X.509 디지털 인증서가 필요합니다. NetX Secure 패키지에는 추가 요구 사항이 없습니다.

## <a name="netx-secure-dtls-constraints"></a>NetX Secure DTLS 제약 조건

NetX Secure DTLS 프로토콜은 DTLS 1.2에 대한 RFC 6347 표준 요구 사항을 구현합니다. 그러나 다음과 같은 제약 조건이 있습니다.

1. 임베디드 디바이스의 특성으로 인해 일부 애플리케이션에는 최대 TLS/DTLS 레코드 크기인 16KB를 지원하는 리소스가 없을 수 있습니다. NetX Secure는 충분한 리소스가 있는 디바이스에서 16KB 레코드를 처리할 수 있습니다.
2. 최소 인증서 확인. NetX Secure는 인증서에 대해 기본 X.509 체인 확인을 수행하여 인증서가 유효하고 신뢰할 수 있는 인증 기관에 의해 서명되었는지 확인하고, 원격 호스트의 최상위 도메인 이름과 비교할 애플리케이션의 인증서 일반 이름을 제공할 수 있습니다. 그러나 인증서 확장 및 기타 데이터 확인은 애플리케이션 구현자의 책임입니다.
3. 소프트웨어 기반 암호화는 프로세서 집약적입니다. NetX Secure 소프트웨어 기반 암호화 루틴은 성능에 맞게 최적화되었지만 대상 프로세서의 성능에 따라 매우 긴 작업이 발생할 수 있습니다. 하드웨어 기반 암호화를 사용할 수 있는 경우 NetX Secure DTLS의 성능을 최적화하는 데 사용해야 합니다.
