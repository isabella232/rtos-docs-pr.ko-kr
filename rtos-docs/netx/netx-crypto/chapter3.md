---
title: 3장 - Azure RTOS NetX Crypto의 기능 설명
description: 이 장은 NetX Crypto의 기능 설명을 포함합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4ecdbfe99daa000d109908f834b139dcaf321491
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810410"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-crypto"></a><span data-ttu-id="ab191-103">3장 - Azure RTOS NetX Crypto의 기능 설명</span><span class="sxs-lookup"><span data-stu-id="ab191-103">Chapter 3 - Functional description of Azure RTOS NetX Crypto</span></span>

## <a name="execution-overview"></a><span data-ttu-id="ab191-104">실행 개요</span><span class="sxs-lookup"><span data-stu-id="ab191-104">Execution Overview</span></span>

<span data-ttu-id="ab191-105">이 장은 Azure RTOS NetX Crypto의 기능 설명을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-105">This chapter contains a functional description of Azure RTOS NetX Crypto.</span></span> <span data-ttu-id="ab191-106">NetX Crypto 애플리케이션에는 초기화 및 애플리케이션 인터페이스 호출이라는 두 가지 주요 유형의 프로그램 실행이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-106">There are two primary types of program execution in a NetX Crypto application: initialization and application interface calls.</span></span>

<span data-ttu-id="ab191-107">*NetX Crypto는 독립 실행형 암호화 라이브러리로 사용하거나 ThreadX, NetX 및/또는 NetX Secure와 함께 사용할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="ab191-107">*NetX Crypto can be used as a standalone cryptographic library, or can be used with ThreadX, NetX, and/or NetX Secure.*</span></span>

## <a name="aes"></a><span data-ttu-id="ab191-108">AES</span><span class="sxs-lookup"><span data-stu-id="ab191-108">AES</span></span>

- <span data-ttu-id="ab191-109">**알고리즘 표준:** : NetX Crypto는 NIST FIPS 197에 따라 AES를 구현합니다. 이에 대해서는 [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-109">**Algorithm Standard:**:  NetX Crypto implements AES according to NIST FIPS 197, which can be found at: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)</span></span>
- <span data-ttu-id="ab191-110">**지원되는 키 길이**: 128, 192, 256</span><span class="sxs-lookup"><span data-stu-id="ab191-110">**Key Lengths Supported**: 128, 192, 256</span></span>
- <span data-ttu-id="ab191-111">**지원되는 모드**:</span><span class="sxs-lookup"><span data-stu-id="ab191-111">**Modes Supported**:</span></span>
  - <span data-ttu-id="ab191-112">CBC, CTR(키 길이 128-, 192-, 256비트)</span><span class="sxs-lookup"><span data-stu-id="ab191-112">CBC, CTR, (Key length 128-, 192-, 256-bit)</span></span>
  - <span data-ttu-id="ab191-113">XCBC(키 길이 128비트만),</span><span class="sxs-lookup"><span data-stu-id="ab191-113">XCBC (key length 128-bit only),</span></span>
  - <span data-ttu-id="ab191-114">CCM8(키 길이 128비트만)</span><span class="sxs-lookup"><span data-stu-id="ab191-114">CCM8 (key length 128-bit only)</span></span>
- <span data-ttu-id="ab191-115">**메모리 요구 사항**: 애플리케이션은 입력 버퍼와 출력 버퍼, 그리고 AES 제어 구조를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-115">**Memory Requirements**: Application specifies input buffer and output buffer and an AES control structure.</span></span> <span data-ttu-id="ab191-116">AES 제어 구조는 API에 대한 호출 사이에서 AES 알고리즘 상태를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-116">The AES control structure maintains AES algorithm state between calls to the API.</span></span> <span data-ttu-id="ab191-117">입력 버퍼에는 암호화하거나 해독할 데이터가 포함되며 임의의 크기를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-117">The input buffer contains data to be encrypted or decrypted, and can be arbitrary size.</span></span> <span data-ttu-id="ab191-118">출력 버퍼는 AES에서 처리되는 데이터를 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-118">The output buffer is used by AES to store data being processed by AES.</span></span> <span data-ttu-id="ab191-119">출력 버퍼 크기는 입력 버퍼 크기보다 작아야 하며, 16바이트의 배수(AES 블록 크기)여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-119">The output buffer size must be no smaller than the input buffer size, and must be a multiple of 16 bytes, the AES block size.</span></span> <span data-ttu-id="ab191-120">입력 및 출력 버퍼는 인접한 메모리여야 하고, 내부에서(in-place) 암호화하는 특별한 경우(입력 및 출력에 동일한 메모리를 사용)를 제외하고는 겹칠 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-120">The input and output buffers must be contiguous memory and may not overlap, except in the special case of encrypting in-place (using the same memory for input and output).</span></span> <span data-ttu-id="ab191-121">내부에서(in-place) 암호화하는 경우 출력 버퍼는 입력 버퍼와 정확히 동일한 위치에서 시작하고 입력 버퍼보다 작아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-121">When encrypting in-place, the output buffer starts at exactly the same location as the input buffer, and must be no smaller than the input buffer.</span></span> <span data-ttu-id="ab191-122">AES 암호화가 내부에서(in-place) 작동하는 경우 추가 스크래치 메모리가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-122">When AES encryption operates in-place no extra scratch memory is required.</span></span>

## <a name="3des"></a><span data-ttu-id="ab191-123">3DES</span><span class="sxs-lookup"><span data-stu-id="ab191-123">3DES</span></span>

- <span data-ttu-id="ab191-124">**알고리즘 표준**: NetX Crypto는 NIST 특별 간행물 800-67 수정 버전 2: *“Recommendataion for the Triple Data Encryption Algorithm (TDES) Block Cipher”* , ([https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final)에서 확인할 수 있음)에 따라 Tripple DES(TDES, 3DES라고도 함)를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-124">**Algorithm Standard**: NetX Crypto implements Tripple DES(TDES, also known as 3DES) according to NIST Special Publication 800-67 rev 2: *"Recommendataion for the Triple Data Encryption Algorithm (TDES) Block Cipher"*, which can be found at: [https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final)</span></span>
- <span data-ttu-id="ab191-125">**지원되는 키 길이**: 64 \* 3 = 192</span><span class="sxs-lookup"><span data-stu-id="ab191-125">**Key Length Supported**: 64 \* 3 = 192</span></span>
- <span data-ttu-id="ab191-126">**메모리 요구 사항:** : 없음</span><span class="sxs-lookup"><span data-stu-id="ab191-126">**Memory Requreiment:**: None</span></span>

<span data-ttu-id="ab191-127">NetX Crypto에서 “3DES”라는 용어는 “TDES”와 교체 사용이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-127">In NetX Crypto, the term "3DES" is used interchangeably with "TDES".</span></span>

## <a name="md5"></a><span data-ttu-id="ab191-128">MD5</span><span class="sxs-lookup"><span data-stu-id="ab191-128">MD5</span></span>

- <span data-ttu-id="ab191-129">**알고리즘 표준**: NetX Crypto는 RFC 1321: *“The MD5 Message-Digest Algorithm”* 에 따라 MD5를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-129">**Algorithm Standard**: NetX Crypto implements MD5 according to RFC 1321: *"The MD5 Message-Digest Algorithm"*</span></span>
- <span data-ttu-id="ab191-130">**메모리 요구 사항**: 애플리케이션은 MD5 작업 간의 상태를 유지하는 데 사용되는 MD5 제어 블록 구조를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-130">**Memory Requirement**: The application must supply an MD5 control block structure, used to maintain state between MD5 operations.</span></span>

## <a name="sha1-sha256512"></a><span data-ttu-id="ab191-131">SHA1, SHA256/512</span><span class="sxs-lookup"><span data-stu-id="ab191-131">SHA1, SHA256/512</span></span>

- <span data-ttu-id="ab191-132">**알고리즘 표준:** NetX Crypto는 NIST FIPS 간행물 180-4: “*Secure Hash Standard*”([http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)에서 찾을 수 있음)에 따라 SHA1/256/512를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-132">**Algorithm Standard:** NetX Crypto implements SHA1/256/512 according to NIST FIPS publication 180-4: "*Secure Hash Standard*", which can be found at: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)</span></span>
- <span data-ttu-id="ab191-133">**해시 블록 크기:** :</span><span class="sxs-lookup"><span data-stu-id="ab191-133">**Hash block size:**:</span></span>
  - <span data-ttu-id="ab191-134">SHA1: 160비트 해시 값</span><span class="sxs-lookup"><span data-stu-id="ab191-134">SHA1: 160 bits hash value</span></span>
  - <span data-ttu-id="ab191-135">SHA 224: 224비트 해시 값</span><span class="sxs-lookup"><span data-stu-id="ab191-135">SHA 224: 224 bits hash value</span></span>
  - <span data-ttu-id="ab191-136">SHA 256: 256비트 해시 값</span><span class="sxs-lookup"><span data-stu-id="ab191-136">SHA 256: 256 bits hash value</span></span>
  - <span data-ttu-id="ab191-137">SHA 384: 384비트 해시 값</span><span class="sxs-lookup"><span data-stu-id="ab191-137">SHA 384: 384 bits hash value</span></span>
  - <span data-ttu-id="ab191-138">SHA 512: 512비트 해시 값</span><span class="sxs-lookup"><span data-stu-id="ab191-138">SHA 512: 512 bits hash value</span></span>
  - <span data-ttu-id="ab191-139">SHA 512/224: 224비트 해시 값</span><span class="sxs-lookup"><span data-stu-id="ab191-139">SHA 512/224: 224 bits hash value</span></span>
  - <span data-ttu-id="ab191-140">SHA 512/256: 256비트 해시 값</span><span class="sxs-lookup"><span data-stu-id="ab191-140">SHA 512/256: 256 bits hash value</span></span>

  <span data-ttu-id="ab191-141">NetX Crypto에서 SHA256 루틴은 SHA256 및 SHA224를 전달하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-141">In NetX Crypto, SHA256 routines are used to hadn SHA256 and SHA224.</span></span> <span data-ttu-id="ab191-142">SHA512 루틴은 SHA512, SHA384, SHA512/224 및 SHA512/256을 전달하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-142">SHA512 routines are used to hand SHA512, SHA384, SHA512/224 and SHA512/256.</span></span>
- <span data-ttu-id="ab191-143">**메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하기 위해 SHA 제어 블록 구조를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-143">**Memory Requirement:** The application must provide a SHA control block structure for maintaining state between operations.</span></span>

## <a name="rsa"></a><span data-ttu-id="ab191-144">RSA</span><span class="sxs-lookup"><span data-stu-id="ab191-144">RSA</span></span>

- <span data-ttu-id="ab191-145">**표준:** NetX Crypto는 표준 “*PKCS #1 v2.2: RSA Cryptography Standard*”에 따라 RSA를 구현합니다. 이는 RFC 8017로 게시되어 있으며 [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-145">**Standard:** NetX Crypto implements RSA according to the standard "*PKCS #1 v2.2: RSA Cryptography Standard*", which is published as RFC 8017 and can also be found at: [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf)</span></span>
- <span data-ttu-id="ab191-146">**메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하고 중간 계산에 필요한 “스크래치” 버퍼 공간을 제공하기 위해 RSA 제어 블록 구조를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-146">**Memory Requirement:** The application must provide an RSA control block structure for maintaining state between operations and to provide necessary "scratch" buffer space for intermediate calculations.</span></span>

## <a name="hmac"></a><span data-ttu-id="ab191-147">HMAC</span><span class="sxs-lookup"><span data-stu-id="ab191-147">HMAC</span></span>

- <span data-ttu-id="ab191-148">**표준:** NetX Crypto는 FIPS 간행물 198-1: “*HMAC(Keyed-Hash Message Authentication Code)* ”에 따라 HMAC를 구현합니다. 이는 [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-148">**Standard:** NetX Crypto implements HMAC according to FIPS PUB 198-1: "*The Keyed-Hash Message Authentication Code (HMAC)*", which can be found at: [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf)</span></span>
- <span data-ttu-id="ab191-149">**메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하기 위해 HMAC 제어 블록 구조를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-149">**Memory Requirement:** The application must provide an HMAC control block structure for maintaining state between operations.</span></span> <span data-ttu-id="ab191-150">제공되는 실제 제어 블록은 원하는 기본 해시 작업(예: SHA1, MD5)에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-150">The actual control block supplied depends on the desired underlying hash operation (e.g. SHA1, MD5).</span></span>

## <a name="elliptic-curve"></a><span data-ttu-id="ab191-151">타원 곡선(Elliptic Curve)</span><span class="sxs-lookup"><span data-stu-id="ab191-151">Elliptic Curve</span></span>

- <span data-ttu-id="ab191-152">**표준:** NetX Crypto는 타원 곡선을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-152">**Standard:** NetX Crypto implements Elliptic Curve.</span></span> <span data-ttu-id="ab191-153">지원되는 명명된 곡선은 다음과 같습니다(소수 필드에만 해당).</span><span class="sxs-lookup"><span data-stu-id="ab191-153">The supported named curves are (prime field only):</span></span>
  - <span data-ttu-id="ab191-154">P-192</span><span class="sxs-lookup"><span data-stu-id="ab191-154">P-192</span></span>
  - <span data-ttu-id="ab191-155">P-224</span><span class="sxs-lookup"><span data-stu-id="ab191-155">P-224</span></span>
  - <span data-ttu-id="ab191-156">P-256</span><span class="sxs-lookup"><span data-stu-id="ab191-156">P-256</span></span>
  - <span data-ttu-id="ab191-157">P-384</span><span class="sxs-lookup"><span data-stu-id="ab191-157">P-384</span></span>
  - <span data-ttu-id="ab191-158">P-521</span><span class="sxs-lookup"><span data-stu-id="ab191-158">P-521</span></span>

   > [!TIP]
   > <span data-ttu-id="ab191-159">압축되지 않은 형식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-159">Uncompressed format is supported.</span></span> <span data-ttu-id="ab191-160">SEC1-v1의 2.3.3 및 2.3.4 섹션을 참조하세요. [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)</span><span class="sxs-lookup"><span data-stu-id="ab191-160">See section 2.3.3 and 2.3.4 of SEC1-v1: [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)</span></span>

- <span data-ttu-id="ab191-161">**메모리 요구 사항:** 없음</span><span class="sxs-lookup"><span data-stu-id="ab191-161">**Memory Requirement:** None</span></span>

## <a name="ecdsa"></a><span data-ttu-id="ab191-162">ECDSA</span><span class="sxs-lookup"><span data-stu-id="ab191-162">ECDSA</span></span>

- <span data-ttu-id="ab191-163">**표준:** NetX Crypto는 FIPS 간행물 186-4: “*DSS(디지털 서명 표준)* ”에 따라 ECDSA를 구현합니다. 이는 [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-163">**Standard:** NetX Crypto implements ECDSA according to FIPS PUB 186-4: "*Digital Signature Standard (DSS)*", which can be found at: [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf)</span></span>
- <span data-ttu-id="ab191-164">**메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하기 위해 ECDSA 제어 블록 구조를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-164">**Memory Requirement:** The application must provide an ECDSA control block structure for maintaining state between operations.</span></span>

## <a name="ecdh"></a><span data-ttu-id="ab191-165">ECDH</span><span class="sxs-lookup"><span data-stu-id="ab191-165">ECDH</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab191-166">Azure RTOS 6.0에서 ECDH 루틴은 정적 프라이빗 키를 사용하는 ECDH가 입력 지점 유효성 검사를 안전하게 수행해야 하므로 ECDHE 암호화에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-166">In Azure RTOS 6.0, ECDH routines should only be used for ECDHE cryptography as ECDH with a static private key requires input point validation to be secure.</span></span>

- <span data-ttu-id="ab191-167">**표준:** NetX Crypto는 FIPS 간행물 800-56Ar2: “Recommendation for Pair-Wise Key Establishment Schemes Using Discrete Logarithm Cryptography”에 따라 ECDH를 구현합니다. 이는 [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-167">**Standard:** NetX Crypto implements ECDH according to FIPS PUB 800-56Ar2: "Recommendation for Pair-Wise Key Establishment Schemes Using Discrete Logarithm Cryptography", which can be found at: [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf)</span></span>
- <span data-ttu-id="ab191-168">**메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하기 위해 ECDH 제어 블록 구조를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-168">**Memory Requirement:** The application must provide an ECDH control block structure for maintaining state between operations.</span></span>

## <a name="drbg"></a><span data-ttu-id="ab191-169">DRBG</span><span class="sxs-lookup"><span data-stu-id="ab191-169">DRBG</span></span>

- <span data-ttu-id="ab191-170">**표준:** NetX Crypto는 FIPS 간행물 800-90Ar1: “Recommendation for Random Number Generation Using Deterministic Random Bit Generators”에 따라 DRBG를 구현합니다. 이는 [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-170">**Standard:** NetX Crypto implements DRBG according to FIPS PUB 800-90Ar1: "Recommendation for Random Number Generation Using Deterministic Random Bit Generators", which can be found at: [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf)</span></span>
- <span data-ttu-id="ab191-171">**메모리 요구 사항:** 애플리케이션은 작업 간의 상태를 유지 관리하기 위해 DRBG 제어 블록 구조를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab191-171">**Memory Requirement:** The application must provide an DRBG control block structure for maintaining state between operations.</span></span>

## <a name="fips-compliant"></a><span data-ttu-id="ab191-172">FIPS 규격</span><span class="sxs-lookup"><span data-stu-id="ab191-172">FIPS-Compliant</span></span>

<span data-ttu-id="ab191-173">NetX Crypto FIPS 140-2</span><span class="sxs-lookup"><span data-stu-id="ab191-173">NetX Crypto FIPS 140-2</span></span>