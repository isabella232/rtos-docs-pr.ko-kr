---
title: 3장 - Azure RTOS NetX Crypto의 기능 설명
description: 이 장은 NetX Crypto의 기능 설명을 포함합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8aa49c130dc2802e95620ccdd4f4d9398c3fd2e55f5896d004e47baa72829848
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796751"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-crypto"></a>3장 - Azure RTOS NetX Crypto의 기능 설명

## <a name="execution-overview"></a>실행 개요

이 장은 Azure RTOS NetX Crypto의 기능 설명을 포함합니다. NetX Crypto 애플리케이션에는 초기화 및 애플리케이션 인터페이스 호출이라는 두 가지 주요 유형의 프로그램 실행이 있습니다.

*NetX Crypto는 독립 실행형 암호화 라이브러리로 사용하거나 ThreadX, NetX 및/또는 NetX Secure와 함께 사용할 수 있습니다.*

## <a name="aes"></a>AES

- **알고리즘 표준:** : NetX Crypto는 NIST FIPS 197에 따라 AES를 구현합니다. 이에 대해서는 [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)에서 찾을 수 있습니다.
- **지원되는 키 길이**: 128, 192, 256
- **지원되는 모드**:
  - CBC, CTR(키 길이 128-, 192-, 256비트)
  - XCBC(키 길이 128비트만),
  - CCM8(키 길이 128비트만)
- **메모리 요구 사항**: 애플리케이션은 입력 버퍼와 출력 버퍼, 그리고 AES 제어 구조를 지정합니다. AES 제어 구조는 API에 대한 호출 사이에서 AES 알고리즘 상태를 유지 관리합니다. 입력 버퍼에는 암호화하거나 해독할 데이터가 포함되며 임의의 크기를 지정할 수 있습니다. 출력 버퍼는 AES에서 처리되는 데이터를 저장하는 데 사용됩니다. 출력 버퍼 크기는 입력 버퍼 크기보다 작아야 하며, 16바이트의 배수(AES 블록 크기)여야 합니다. 입력 및 출력 버퍼는 인접한 메모리여야 하고, 내부에서(in-place) 암호화하는 특별한 경우(입력 및 출력에 동일한 메모리를 사용)를 제외하고는 겹칠 수 없습니다. 내부에서(in-place) 암호화하는 경우 출력 버퍼는 입력 버퍼와 정확히 동일한 위치에서 시작하고 입력 버퍼보다 작아야 합니다. AES 암호화가 내부에서(in-place) 작동하는 경우 추가 스크래치 메모리가 필요하지 않습니다.

## <a name="3des"></a>3DES

- **알고리즘 표준**: NetX Crypto는 NIST 특별 간행물 800-67 수정 버전 2: *“Recommendataion for the Triple Data Encryption Algorithm (TDES) Block Cipher”* , ([https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final)에서 확인할 수 있음)에 따라 Tripple DES(TDES, 3DES라고도 함)를 구현합니다.
- **지원되는 키 길이**: 64 * 3 = 192
- **메모리 요구 사항:** : 없음

NetX Crypto에서 “3DES”라는 용어는 “TDES”와 교체 사용이 가능합니다.

## <a name="md5"></a>MD5

- **알고리즘 표준**: NetX Crypto는 RFC 1321: *“The MD5 Message-Digest Algorithm”* 에 따라 MD5를 구현합니다.
- **메모리 요구 사항**: 애플리케이션은 MD5 작업 간의 상태를 유지하는 데 사용되는 MD5 제어 블록 구조를 제공해야 합니다.

## <a name="sha1-sha256512"></a>SHA1, SHA256/512

- **알고리즘 표준:** NetX Crypto는 NIST FIPS 간행물 180-4: “*Secure Hash Standard*”([http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)에서 찾을 수 있음)에 따라 SHA1/256/512를 구현합니다.
- **해시 블록 크기:** :
  - SHA1: 160비트 해시 값
  - SHA 224: 224비트 해시 값
  - SHA 256: 256비트 해시 값
  - SHA 384: 384비트 해시 값
  - SHA 512: 512비트 해시 값
  - SHA 512/224: 224비트 해시 값
  - SHA 512/256: 256비트 해시 값

  NetX Crypto에서 SHA256 루틴은 SHA256 및 SHA224를 전달하는 데 사용됩니다. SHA512 루틴은 SHA512, SHA384, SHA512/224 및 SHA512/256을 전달하는 데 사용됩니다.
- **메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하기 위해 SHA 제어 블록 구조를 제공해야 합니다.

## <a name="rsa"></a>RSA

- **표준:** NetX Crypto는 표준 “*PKCS #1 v2.2: RSA Cryptography Standard*”에 따라 RSA를 구현합니다. 이는 RFC 8017로 게시되어 있으며 [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf)에서 확인할 수 있습니다.
- **메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하고 중간 계산에 필요한 “스크래치” 버퍼 공간을 제공하기 위해 RSA 제어 블록 구조를 제공해야 합니다.

## <a name="hmac"></a>HMAC

- **표준:** NetX Crypto는 FIPS 간행물 198-1: “*HMAC(Keyed-Hash Message Authentication Code)* ”에 따라 HMAC를 구현합니다. 이는 [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf)에서 확인할 수 있습니다.
- **메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하기 위해 HMAC 제어 블록 구조를 제공해야 합니다. 제공되는 실제 제어 블록은 원하는 기본 해시 작업(예: SHA1, MD5)에 따라 달라집니다.

## <a name="elliptic-curve"></a>타원 곡선(Elliptic Curve)

- **표준:** NetX Crypto는 타원 곡선을 구현합니다. 지원되는 명명된 곡선은 다음과 같습니다(소수 필드에만 해당).
  - P-192
  - P-224
  - P-256
  - P-384
  - P-521

   > [!TIP]
   > 압축되지 않은 형식이 지원됩니다. SEC1-v1의 2.3.3 및 2.3.4 섹션을 참조하세요. [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)

- **메모리 요구 사항:** 없음

## <a name="ecdsa"></a>ECDSA

- **표준:** NetX Crypto는 FIPS 간행물 186-4: “*DSS(디지털 서명 표준)* ”에 따라 ECDSA를 구현합니다. 이는 [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf)에서 확인할 수 있습니다.
- **메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하기 위해 ECDSA 제어 블록 구조를 제공해야 합니다.

## <a name="ecdh"></a>ECDH

> [!IMPORTANT]
> Azure RTOS 6.0에서 ECDH 루틴은 정적 프라이빗 키를 사용하는 ECDH가 입력 지점 유효성 검사를 안전하게 수행해야 하므로 ECDHE 암호화에만 사용해야 합니다.

- **표준:** NetX Crypto는 FIPS 간행물 800-56Ar2: “Recommendation for Pair-Wise Key Establishment Schemes Using Discrete Logarithm Cryptography”에 따라 ECDH를 구현합니다. 이는 [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf)에서 확인할 수 있습니다.
- **메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하기 위해 ECDH 제어 블록 구조를 제공해야 합니다.

## <a name="drbg"></a>DRBG

- **표준:** NetX Crypto는 FIPS 간행물 800-90Ar1: “Recommendation for Random Number Generation Using Deterministic Random Bit Generators”에 따라 DRBG를 구현합니다. 이는 [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf)에서 확인할 수 있습니다.
- **메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하기 위해 DRBG 제어 블록 구조를 제공해야 합니다.

## <a name="fips-compliant"></a>FIPS 규격

NetX Crypto FIPS 140-2