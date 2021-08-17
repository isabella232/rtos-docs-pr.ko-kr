---
title: 1장 - Azure RTOS NetX Crypto 소개
description: NetX Crypto는 데이터 암호화 및 인증 서비스를 제공하도록 설계된 암호화 알고리즘의 고성능 실시간 구현입니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1b5ee0336ba9e867a628dc5db4f0c029f68ff45c81d68ceb6299e3469d5e2b49
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796806"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-crypto"></a>1장 - Azure RTOS NetX Crypto 소개

Azure RTOS NetX Crypto는 데이터 암호화 및 인증 서비스를 제공하도록 설계된 암호화 알고리즘의 고성능 실시간 구현입니다. NetX Crypto는 NetX Secure TLS, DTLS 및 IPsec 모듈을 연결하도록 설계되었습니다. 애플리케이션은 네트워크 보안 외부의 독립 실행형 모듈로 NetX Crypto를 사용할 수도 있습니다.

## <a name="netx-crypto-unique-features"></a>NetX Crypto 고유 기능

NetX Crypto는 거의 모든 C/C++ 컴파일러와 호환되는 표준 C 언어(C99)로 구현됩니다. 모듈식 디자인을 통해 애플리케이션에서 사용해야 하는 암호화 알고리즘에서만 링크할 수 있으므로 코드 크기를 최소화할 수 있습니다. 구현은 대부분의 32비트 마이크로프로세서에서 작동하고 기본 수학 연산(더하기, 빼기, 곱하기, 나누기, 논리 AND, OR, NOR 및 비트 시프트 작업)만 사용하도록 설계되었습니다. 이러한 모든 작업은 32비트 수량에서 사용되며, 대부분의 32비트 마이크로프로세서에서 NetX Crypto를 이식할 수 있습니다. 구현은 특히 임베디드 애플리케이션을 대상으로 하는 리소스 제한 마이크로프로세서에서 실행되도록 최적화되었습니다.

## <a name="algorithms-supported-by-netx-crypto"></a>NetX Crypto에서 지원되는 알고리즘

NetX Crypto는 다음과 같은 암호화 알고리즘을 지원합니다. NetX Crypto는 작은 메모리 사용 공간과 효율적인 실행이 요구되는 실시간 운영 체제 및 플랫폼의 제약 조건 내에서 모든 일반 권장 사항과 기본 요구 사항을 따릅니다.

| 알고리즘       | 키 길이(비트)      |
| --------------- | ---------------------- |
| AES(CBC, CTR)   | 128, 192, 256          |
| AES(XCBC)       | 128                    |
| AES-CCM 8       | 128                    |
| 3DES(CBC)       | 192                    |
| HMAC-SHA1       | 모든 길이             |
| HMAC-SHA224     | 모든 길이             |
| HMAC-SHA256     | 모든 길이             |
| HMAC-SHA384     | 모든 길이             |
| HMAC-SHA512     | 모든 길이             |
| HMAC-SHA512/224 | 모든 길이             |
| HMAC-SHA512/256 | 모든 길이             |
| HMAC-MD5        | 모든 길이             |
| RSA             | 1024, 2048, 3072, 4096 |

| 알고리즘       | 다이제스트 길이(비트) | 블록 크기(비트) |
| --------------- | -------------------- | ----------------- |
| SHA1            | 160                  | 512               |
| SHA224          | 224                  | 512               |
| SHA256          | 256                  | 512               |
| SHA384          | 384                  | 1024              |
| SHA512          | 512                  | 1024              |
| MD5             | 128                  | 512               |
| HMAC-SHA1       | 160                  | 512               |
| HMAC-SHA224     | 224                  | 512               |
| HMAC-SHA256     | 256                  | 512               |
| HMAC-SHA384     | 384                  | 1024              |
| HMAC-SHA512     | 512                  | 1024              |
| HMAC-SHA512/224 | 224                  | 1024              |
| HMAC-SHA512/256 | 256                  | 1024              |
| HMAC-MD5        | 128                  | 512               |
| 타원 곡선(Elliptic Curve)  | P192/224/256/384/521 |                   |

## <a name="netx-crypto-requirements"></a>NetX Crypto 요구 사항

TBD: 메모리 요구 사항. 인터럽트/재진입이 안전한가요? 토론 필요

## <a name="netx-crypto-constraints"></a>NetX Crypto 제약 조건

없음
