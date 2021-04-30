---
title: 챕터 4 - Azure RTOS NetX Crypto API 설명
description: Azure RTOS NetX Crypto API 설명
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04e732bc1fd6012636aab3a57391829f529724cf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811628"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a><span data-ttu-id="c7269-103">챕터 4 - Azure RTOS NetX Crypto API 설명</span><span class="sxs-lookup"><span data-stu-id="c7269-103">Chapter 4 - Azure RTOS NetX Crypto API description</span></span>

## <a name="nx_crypto_initialize"></a><span data-ttu-id="c7269-104">nx_crypto_initialize</span><span class="sxs-lookup"><span data-stu-id="c7269-104">nx_crypto_initialize</span></span>

<span data-ttu-id="c7269-105">NetX Secure 라이브러리 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-105">Initializes the NetX Secure Library</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-106">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-106">Prototype</span></span>

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="c7269-107">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-107">Description</span></span>

<span data-ttu-id="c7269-108">이 함수는 Azure RTOS NetX Crypto 라이브러리 모듈을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-108">This function initializes the Azure RTOS NetX Crypto library module.</span></span> <span data-ttu-id="c7269-109">다른 암호화 함수를 사용하기 전에 애플리케이션에서 이 함수를 호출하여 초기화를 수행하고 라이브러리의 무결성을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-109">Before using any of the other cryptographic functions, the application must call this function to perform initialization and to validate the integrity of the library.</span></span> <span data-ttu-id="c7269-110">다른 NetX Crypto 서비스를 사용하기 전에 이 함수를 호출하지 못하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-110">Failure to call this function before using other NetX Crypto services will result in errors being returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-111">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-111">Parameters</span></span>

- <span data-ttu-id="c7269-112">**없음**</span><span class="sxs-lookup"><span data-stu-id="c7269-112">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-113">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-113">Return Values</span></span>

- <span data-ttu-id="c7269-114">**NX_CRYPTO_SUCCESS** (0x00) NetX Crypto 라이브러리를 성공적으로 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-114">**NX_CRYPTO_SUCCESS** (0x00) Successful initialized NetX Crypto library.</span></span> <span data-ttu-id="c7269-115">이제 라이브러리 함수가 준비되었으며 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-115">The library functions are now ready, and can be used.</span></span>
- <span data-ttu-id="c7269-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 초기화되지 않거나 무결성 검사에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library fails to initialize, or fails the integrity check.</span></span> <span data-ttu-id="c7269-117">애플리케이션에서 이 라이브러리를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-117">Application cannot use this library.</span></span>

### <a name="example"></a><span data-ttu-id="c7269-118">예제</span><span class="sxs-lookup"><span data-stu-id="c7269-118">Example</span></span>

<span data-ttu-id="c7269-119">TODO</span><span class="sxs-lookup"><span data-stu-id="c7269-119">TODO</span></span>

## <a name="nx_crypto_module_state_get"></a><span data-ttu-id="c7269-120">nx_crypto_module_state_get</span><span class="sxs-lookup"><span data-stu-id="c7269-120">nx_crypto_module_state_get</span></span>

<span data-ttu-id="c7269-121">FIPS 사용 모듈의 현재 상태를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-121">Retrieve the current status of the FIPS-enabled module</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-122">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-122">Prototype</span></span>

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a><span data-ttu-id="c7269-123">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-123">Description</span></span>

<span data-ttu-id="c7269-124">이 서비스는 FIPS 빌드 라이브러리에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-124">This service is only available in the FIPS build library.</span></span> <span data-ttu-id="c7269-125">NetX Crypto 라이브러리의 현재 상태 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-125">It returns the state of the current state of the NetX Crypto library.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-126">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-126">Parameters</span></span>

- <span data-ttu-id="c7269-127">**없음**</span><span class="sxs-lookup"><span data-stu-id="c7269-127">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-128">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-128">Return Values</span></span>

- <span data-ttu-id="c7269-129">**상태 플래그:**</span><span class="sxs-lookup"><span data-stu-id="c7269-129">**Status Flag:**</span></span>
  - <span data-ttu-id="c7269-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span><span class="sxs-lookup"><span data-stu-id="c7269-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span></span>
  - <span data-ttu-id="c7269-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span><span class="sxs-lookup"><span data-stu-id="c7269-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span></span>
  - <span data-ttu-id="c7269-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span><span class="sxs-lookup"><span data-stu-id="c7269-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span></span>
  - <span data-ttu-id="c7269-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span><span class="sxs-lookup"><span data-stu-id="c7269-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span></span>
  - <span data-ttu-id="c7269-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span><span class="sxs-lookup"><span data-stu-id="c7269-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span></span>
- <span data-ttu-id="c7269-135">**다른 모든 값이 올바르지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="c7269-135">**All other values are invalid.**</span></span>

### <a name="example"></a><span data-ttu-id="c7269-136">예제</span><span class="sxs-lookup"><span data-stu-id="c7269-136">Example</span></span>

<span data-ttu-id="c7269-137">TODO</span><span class="sxs-lookup"><span data-stu-id="c7269-137">TODO</span></span>

## <a name="_nx_crypto_method_aes_init"></a><span data-ttu-id="c7269-138">_nx_crypto_method_aes_init</span><span class="sxs-lookup"><span data-stu-id="c7269-138">_nx_crypto_method_aes_init</span></span>

<span data-ttu-id="c7269-139">AES 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-139">Initializes the AES crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-140">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-140">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-141">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-141">Description</span></span>

<span data-ttu-id="c7269-142">이 함수는 제공된 키 문자열을 사용하여 AES 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-142">This function initializes the AES control block with the given key string.</span></span> <span data-ttu-id="c7269-143">AES 제어 블록이 초기화되면 후속 AES 작업에서 동일한 키 및 키 크기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-143">Once the AES control block is initialized, subsequent AES operation will be using the same key and key size.</span></span>

<span data-ttu-id="c7269-144">애플리케이션에서는 각각 세션을 나타내는 여러 AES 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-144">Application may create multiple AES control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-145">키는 제어 블록에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-145">A key is assigned to a control block.</span></span> <span data-ttu-id="c7269-146">후속 암호화 또는 암호 해독 작업에서는 AES 제어 블록을 다시 초기화할 필요 없이 동일한 AES 제어 블록을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-146">Subsequent encryption or decryption operation can reference to the same AES control block without the need to re-initialize the AES control block.</span></span> <span data-ttu-id="c7269-147">세션의 키가 변경되면 애플리케이션에서는 업데이트된 키를 사용하여 AES 제어 블록을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-147">If the key for the session is changed, application needs to re-initialize AES control block with the updated key.</span></span>

<span data-ttu-id="c7269-148">_ *nx_crypto_method_aes_init()* 를 호출하면 이전에 구성된 키와 키 크기가 새 키로 자동 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-148">Calling _ *nx_crypto_method_aes_init()* automatically updates a previously configured key and key size to the new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-149">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-149">Parameters</span></span>

- <span data-ttu-id="c7269-150">**method** 유효한 AES 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-150">**method** Pointer to a valid AES crypto method control block.</span></span> <span data-ttu-id="c7269-151">다음과 같은 미리 정의된 AES 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-151">The following pre-defined AES crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-152">*crypto_method_aes_cbc_128*</span><span class="sxs-lookup"><span data-stu-id="c7269-152">*crypto_method_aes_cbc_128*</span></span>
  - <span data-ttu-id="c7269-153">*crypto_method_aes_cbc_192*</span><span class="sxs-lookup"><span data-stu-id="c7269-153">*crypto_method_aes_cbc_192*</span></span>
  - <span data-ttu-id="c7269-154">*crypto_method_aes_cbc_256*</span><span class="sxs-lookup"><span data-stu-id="c7269-154">*crypto_method_aes_cbc_256*</span></span>
  - <span data-ttu-id="c7269-155">*crypto_method_aes_ctr_128*</span><span class="sxs-lookup"><span data-stu-id="c7269-155">*crypto_method_aes_ctr_128*</span></span>
  - <span data-ttu-id="c7269-156">*crypto_method_aes_ctr_192*</span><span class="sxs-lookup"><span data-stu-id="c7269-156">*crypto_method_aes_ctr_192*</span></span>
  - <span data-ttu-id="c7269-157">*crypto_method_aes_ctr_256*</span><span class="sxs-lookup"><span data-stu-id="c7269-157">*crypto_method_aes_ctr_256*</span></span>
  - <span data-ttu-id="c7269-158">*crypto_method_aes_xcbc_128*</span><span class="sxs-lookup"><span data-stu-id="c7269-158">*crypto_method_aes_xcbc_128*</span></span>
  - <span data-ttu-id="c7269-159">*crypto_method_aes_ccm_8_128*</span><span class="sxs-lookup"><span data-stu-id="c7269-159">*crypto_method_aes_ccm_8_128*</span></span>
- <span data-ttu-id="c7269-160">**key** AES 키가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-160">**key** Points to a buffer containing the AES key</span></span>
- <span data-ttu-id="c7269-161">**key_size_in_bits** 키의 크기(비트)</span><span class="sxs-lookup"><span data-stu-id="c7269-161">**key_size_in_bits** Size of the key, in bits.</span></span> <span data-ttu-id="c7269-162">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-162">Valid values are:</span></span>
  - <span data-ttu-id="c7269-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span><span class="sxs-lookup"><span data-stu-id="c7269-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span></span>
  - <span data-ttu-id="c7269-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span><span class="sxs-lookup"><span data-stu-id="c7269-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span></span>
  - <span data-ttu-id="c7269-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span><span class="sxs-lookup"><span data-stu-id="c7269-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span></span>
  - <span data-ttu-id="c7269-166">**다른 모든 값이 올바르지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="c7269-166">**All other values are invalid.**</span></span>
- <span data-ttu-id="c7269-167">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-167">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-168">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-168">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-169">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-169">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-170">**crypto_metadata** AES 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-170">**crypto_metadata** Pointer to a valid memory space for the AES control block.</span></span> <span data-ttu-id="c7269-171">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-171">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-172">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-172">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-173">AES의 경우 메타데이터 크기가 *sizeof(NX_AES)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-173">For AES, the metadata size must be *sizeof(NX_AES)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-174">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-174">Return Values</span></span>

- <span data-ttu-id="c7269-175">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 AES 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-175">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the AES control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-177">**NX_PTR_ERROR (0x07)** 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-177">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) 키 크기가 AES에 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for AES.</span></span>

## <a name="_nx_crypto_method_aes_operation"></a><span data-ttu-id="c7269-179">_nx_crypto_method_aes_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-179">_nx_crypto_method_aes_operation</span></span>

<span data-ttu-id="c7269-180">AES 작업(암호화 또는 암호 해독)을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-180">Perform an AES operation (encryption or decryption).</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-181">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-181">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a><span data-ttu-id="c7269-182">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-182">Description</span></span>

<span data-ttu-id="c7269-183">이 함수는 AES 암호화 또는 암호 해독 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-183">This function performs AES encryption or decryption operation.</span></span> <span data-ttu-id="c7269-184">AES 제어 블록은 _ *nx_crypto_method_aes_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-184">The AES control block must have been initialized with _ *nx_crypto_method_aes_init()*.</span></span> <span data-ttu-id="c7269-185">수행할 AES 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-185">The AES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-186">입력 버퍼 크기는 16바이트의 배수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-186">The input buffer size must be a multiple of 16 bytes.</span></span> <span data-ttu-id="c7269-187">암호 해독된 데이터의 크기는 입력 데이터 크기와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-187">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="c7269-188">암호화된 데이터가 AES 블록 크기의 짝수 배수가 되도록 패딩된 경우 패딩이 출력 버퍼에 포함되며 애플리케이션에서 패딩을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-188">If the encrypted data was padded to achieve an even multiple of the AES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="c7269-189">이 작업은 상태 정보를 유지하지 않으며, AES 제어 블록의 키 자료를 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-189">This operation does not keep state information, and does not alter the key material in the AES control block.</span></span>

<span data-ttu-id="c7269-190">op가 NX_CRYPTO_SET_ADDITIONAL_DATA이고 알고리즘이 AES-CCM8이면 입력은 추가 데이터를 가리키고 input_length_in_byte는 추가 데이터의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-190">When the op is NX_CRYPTO_SET_ADDITIONAL_DATA and algoritm is AES-CCM8, the input points to additional data and input_length_in_byte is the length of additional data.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-191">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-191">Parameters</span></span>

- <span data-ttu-id="c7269-192">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-192">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-193">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-193">Valid opertions are:</span></span>
  - <span data-ttu-id="c7269-194">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="c7269-194">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="c7269-195">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="c7269-195">*NX_CRYPTO_DECRYPT*</span></span>
  - <span data-ttu-id="c7269-196">*NX_CRYPTO_AUTHENTICATE(AES-XCBC만 해당)*</span><span class="sxs-lookup"><span data-stu-id="c7269-196">*NX_CRYPTO_AUTHENTICATE (AES-XCBC only)*</span></span>
  - <span data-ttu-id="c7269-197">*NX_CRYPTO_SET_ADDITIONAL_DATA(AES-CCM8만 해당)*</span><span class="sxs-lookup"><span data-stu-id="c7269-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (AES-CCM8 only)*</span></span>
- <span data-ttu-id="c7269-198">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-198">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-199">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-199">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-200">**method** 유효한 AES 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-200">**method** Pointer to the valid AES crypto method.</span></span> <span data-ttu-id="c7269-201">여기서 사용하는 암호화 메서드를 *nx_crypto_method_aes_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-201">The crypto method used here must be the same used in the *nx_crypto_method_aes_init().*</span></span>
- <span data-ttu-id="c7269-202">**input_data** 암호화된 텍스트 데이터가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-202">**input_data** Points to a buffer containing encrypted text data.</span></span> <span data-ttu-id="c7269-203">입력 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-203">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c7269-204">**input_data_size** 입력 데이터의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-204">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="c7269-205">입력 데이터 크기는 16바이트의 배수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-205">The input data size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="c7269-206">**iv_ptr** 초기 벡터에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-206">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="c7269-207">IV 버퍼 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-207">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="c7269-208">**iv_size** 초기 벡터 블록의 크기(바이트). 이 필드는 16이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-208">**iv_size** Size of the Initial Vector block, in bytes This field must be 16.</span></span>
- <span data-ttu-id="c7269-209">**output_buffer** 일반 텍스트 데이터를 저장하는 AES의 메모리 영역에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-209">**output_buffer** Pointer to the memory area for AES to store the clear text data.</span></span> <span data-ttu-id="c7269-210">애플리케이션에서 출력 버퍼에 사용할 공간을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-210">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="c7269-211">출력 버퍼가 입력 버퍼와 겹칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-211">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="c7269-212">출력 버퍼와 입력 버퍼가 동일한 시작 주소를 공유하는 경우에는 출력 버퍼가 입력 버퍼와 겹칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-212">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="c7269-213">**output_buffer_size** 출력 버퍼의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-213">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c7269-214">출력 버퍼 크기는 적어도 입력 버퍼 크기와 동일해야 하며, 출력 버퍼 크기는 16바이트의 배수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-214">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="c7269-215">**crypto_metadata** *_nx_crypto_method_aes_init()\*에 사용되는 AES 제어 블록에 대한 포인터.\**</span><span class="sxs-lookup"><span data-stu-id="c7269-215">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>
- <span data-ttu-id="c7269-216">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-216">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-217">AES의 경우 메타데이터 크기가 *sizeof(NX_AES)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-217">For AES, the metadata size must *sizeof(NX_AES)*</span></span>
- <span data-ttu-id="c7269-218">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-218">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-219">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-219">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-220">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-220">**nx_crypto_hw_process_callback** - This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-221">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-221">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-222">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-222">Return Values</span></span>

- <span data-ttu-id="c7269-223">**NX_CRYPTO_SUCCESS** (0x00) AES 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-223">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the AES operation.</span></span>
- <span data-ttu-id="c7269-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-225">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-225">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 AES 알고리즘이 지정되었습니다\*\*.</span><span class="sxs-lookup"><span data-stu-id="c7269-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid AES algorithm being specified\*\*.</span></span>

## <a name="_nx_crypto_method_aes_cleanup"></a><span data-ttu-id="c7269-227">_nx_crypto_method_aes_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-227">_nx_crypto_method_aes_cleanup</span></span>

<span data-ttu-id="c7269-228">AES 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-228">Clean up the AES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-229">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-229">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-230">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-230">Description</span></span>

<span data-ttu-id="c7269-231">애플리케이션에서는 이 AES 세션이 더 이상 필요 없다고 확인되면 AES 제어 블록을 정리하기 위해 이 함수를 호출합니다</span><span class="sxs-lookup"><span data-stu-id="c7269-231">Application calls this function to clean up the AES control block after it determines this AES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-232">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-232">Parameters</span></span>

- <span data-ttu-id="c7269-233">**crypto_metadata** *_nx_crypto_method_aes_init()\*에 사용되는 AES 제어 블록에 대한 포인터.\**</span><span class="sxs-lookup"><span data-stu-id="c7269-233">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-234">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-234">Return Values</span></span>

- <span data-ttu-id="c7269-235">**NX_CRYPTO_SUCCESS** (0x00) AES 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-235">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the AES session.</span></span>
- <span data-ttu-id="c7269-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_3des_init"></a><span data-ttu-id="c7269-237">_nx_crypto_method_3des_init</span><span class="sxs-lookup"><span data-stu-id="c7269-237">_nx_crypto_method_3des_init</span></span>

<span data-ttu-id="c7269-238">3DES 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-238">Initialize the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-239">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-239">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-240">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-240">Description</span></span>

<span data-ttu-id="c7269-241">이 함수는 제공된 3개의 키 문자열로 3DES(Triple DES) 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-241">This function initializes the Triple DES (3DES) control block with the given three key strings.</span></span> <span data-ttu-id="c7269-242">키 문자열은 각각 8바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-242">The key strings must be 8 bytes each.</span></span> <span data-ttu-id="c7269-243">3개의 DES 키는 24바이트 버퍼의 연속 메모리에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-243">The three DES keys must be concatenated into contiguous memory of 24-byte buffer.</span></span> <span data-ttu-id="c7269-244">FIPS 규격 빌드의 경우 세 키가 서로 달라야 합니다. 그렇지 않으면 함수에서 NX_CRYPTO_INVALID_KEY 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-244">For FIPS-compliant build, the three keys must be different from each or the function will return the NX_CRYPTO_INVALID_KEY error.</span></span> <span data-ttu-id="c7269-245">3DES 제어 블록이 초기화되면 후속 3DES 작업에서 동일한 키가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-245">Once the 3DES control block is initialized, subsequent 3DES operations will use the same keys.</span></span>

<span data-ttu-id="c7269-246">애플리케이션에서는 각각 세션을 나타내는 여러 3DES 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-246">An application may create multiple 3DES control blocks, each representing a session.</span></span> <span data-ttu-id="c7269-247">키는 제어 블록에 할당되며, 후속 암호화 또는 해독 작업에서는 다시 초기화할 필요 없이 동일한 제어 블록을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-247">A key is assigned to a control block and subsequent encryption or decryption operations can reference the same control block without needing to re-initialize.</span></span> <span data-ttu-id="c7269-248">세션의 키가 변경되면 애플리케이션에서는 업데이트된 키를 사용하여 제어 블록을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-248">If the key for a session is changed, the application will need to re-initialize the control block with the updated key.</span></span>

<span data-ttu-id="c7269-249">_ *nx_crypto_method_3des_init()* 를 호출하면 이전에 구성된 키가 새 키로 자동 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-249">Calling _ *nx_crypto_method_3des_init()* automatically updates a previously configured key to the new keys.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-250">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-250">Parameters</span></span>

- <span data-ttu-id="c7269-251">**method** 유효한 3DES 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-251">**method** Pointer to a valid 3DES crypto method control block.</span></span> <span data-ttu-id="c7269-252">미리 정의된 3DES 암호화 메서드 ***crypto_method_3des*** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-252">The following pre-defined 3DES crypto method is available: ***crypto_method_3des***</span></span>
- <span data-ttu-id="c7269-253">**key** 3개의 DES 키가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-253">**key** Points to a buffer containing the three (3) DES key</span></span>
- <span data-ttu-id="c7269-254">**key_size_in_bits** 192여야 합니다(키 3개, 각각 64비트).</span><span class="sxs-lookup"><span data-stu-id="c7269-254">**key_size_in_bits** Must be 192 (3 keys, each 64 bits).</span></span>
- <span data-ttu-id="c7269-255">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-255">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-256">핸들은 초기화 중인 3DES 제어 블록을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-256">The handle identifies the 3DES control block being initialized.</span></span> <span data-ttu-id="c7269-257">후속 3DES 작업(암호화, 암호 해독 및 정리)에서는 이 핸들을 사용하여 3DES 제어 블록에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-257">Subsequent 3DES operations (encryption, decryption, and cleanup) use this handle to access the 3DES control block</span></span>
- <span data-ttu-id="c7269-258">**crypto_metadata** 3DES 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-258">**crypto_metadata** Pointer to a valid memory space for the 3DES control block.</span></span> <span data-ttu-id="c7269-259">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-259">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-260">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-260">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-261">3DES의 경우 메타데이터 크기가 *sizeof(NX_3DES)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-261">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>

### <a name="return-value"></a><span data-ttu-id="c7269-262">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-262">Return Value</span></span>

- <span data-ttu-id="c7269-263">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 3DES 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-263">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-265">**NX_PTR_ERROR (0x07)** 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-265">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) 키 크기가 3DES에 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for 3DES.</span></span>

## <a name="_nx_crypto_method_3des_operation"></a><span data-ttu-id="c7269-267">_nx_crypto_method_3des_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-267">_nx_crypto_method_3des_operation</span></span>

<span data-ttu-id="c7269-268">3DES로 암호화하거나 암호를 해독합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-268">Encrypt or Decrypt with 3DES.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-269">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-269">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c7269-270">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-270">Description</span></span>

<span data-ttu-id="c7269-271">이 함수는 3DES 암호화 또는 암호 해독 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-271">This function performs 3DES encryption or decryption operation.</span></span> <span data-ttu-id="c7269-272">3DES 제어 블록은 _ *nx_crypto_method_3des_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-272">The 3DES control block must have been initialized with _ *nx_crypto_method_3des_init()*.</span></span> <span data-ttu-id="c7269-273">수행할 3DES 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-273">The 3DES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-274">입력 버퍼 크기는 8바이트의 배수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-274">The input buffer size must be a multiple of 8 bytes.</span></span> <span data-ttu-id="c7269-275">암호 해독된 데이터의 크기는 입력 데이터 크기와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-275">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="c7269-276">암호화된 데이터가 3DES 블록 크기의 짝수 배수가 되도록 패딩된 경우 패딩이 출력 버퍼에 포함되며 애플리케이션에서 패딩을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-276">If the encrypted data was padded to achieve an even multiple of the 3DES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="c7269-277">이 작업은 상태 정보를 유지하지 않으며, 3DES 제어 블록의 키 자료를 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-277">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-278">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-278">Parameters</span></span>

- <span data-ttu-id="c7269-279">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-279">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-280">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-280">Valid operations are:</span></span>
  - <span data-ttu-id="c7269-281">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="c7269-281">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="c7269-282">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="c7269-282">*NX_CRYPTO_DECRYPT*</span></span>
- <span data-ttu-id="c7269-283">**handle** *_nx_crypto_method_3des_init()* 를 통해 초기화된 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-283">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="c7269-284">**method** 유효한 3DES 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-284">**method** Pointer to the valid 3DES crypto method.</span></span> <span data-ttu-id="c7269-285">여기서 사용하는 암호화 메서드를 *nx_crypto_method_3des_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-285">The crypto method used here must be the same used in the *nx_crypto_method_3des_init().*</span></span>
- <span data-ttu-id="c7269-286">**input_data** 암호화된 텍스트 데이터가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-286">**input_data** Points to a buffer containing encrypted text data.</span></span>
<span data-ttu-id="c7269-287">입력 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-287">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c7269-288">**input_data_size** 입력 데이터의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-288">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="c7269-289">입력 데이터 크기는 8바이트의 배수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-289">The input data size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="c7269-290">**iv_ptr** 초기 벡터에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-290">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="c7269-291">IV 버퍼 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-291">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="c7269-292">**iv_size** 초기 벡터 블록의 크기(바이트)입니다. 이 필드는 8이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-292">**iv_size** Size of the Initial Vector block, in bytes This field must be 8.</span></span>
- <span data-ttu-id="c7269-293">**output_buffer** 일반 텍스트 데이터를 저장하는 3DES의 메모리 영역에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-293">**output_buffer** Pointer to the memory area for 3DES to store the clear text data.</span></span> <span data-ttu-id="c7269-294">애플리케이션에서 출력 버퍼에 사용할 공간을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-294">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="c7269-295">출력 버퍼가 입력 버퍼와 겹칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-295">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="c7269-296">출력 버퍼와 입력 버퍼가 동일한 시작 주소를 공유하는 경우에는 출력 버퍼가 입력 버퍼와 겹칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-296">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="c7269-297">**output_buffer_size** 출력 버퍼의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-297">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c7269-298">출력 버퍼 크기는 적어도 입력 버퍼 크기와 동일해야 하며, 출력 버퍼 크기는 8바이트의 배수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-298">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="c7269-299">**crypto_metadata** *_nx_crypto_method_3des_init()* 에 사용되는 3DES 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-299">**crypto_metadata** Pointer to the 3DES control block used in *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="c7269-300">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-300">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-301">3DES의 경우 메타데이터 크기가 *sizeof(NX_3DES)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-301">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>
- <span data-ttu-id="c7269-302">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-302">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-303">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-303">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-304">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-304">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-305">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-305">Any values passed in are silently ignored.</span></span>

### <a name="description"></a><span data-ttu-id="c7269-306">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-306">Description</span></span>

<span data-ttu-id="c7269-307">이 함수는 3DES 암호화를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-307">This function performs 3DES encryption.</span></span> <span data-ttu-id="c7269-308">3DES 제어 블록은 _ *nx_crypto_moethod_3des_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-308">The 3DES control block must have been initialized with _ *nx_crypto_moethod_3des_init()*.</span></span> <span data-ttu-id="c7269-309">이 작업은 상태 정보를 유지하지 않으며, 3DES 제어 블록의 키 자료를 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-309">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span> <span data-ttu-id="c7269-310">이 함수는 패딩을 추가하지 않으므로 호출자는 패딩을 처리한 후 암호화 작업을 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-310">Note that padding is not added by this function so the caller will need to handle padding before invoking the encryption operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-311">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-311">Return Values</span></span>

- <span data-ttu-id="c7269-312">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 3DES 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-312">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-314">**NX_PTR_ERROR (0x07)** 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-314">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_3des_cleanup"></a><span data-ttu-id="c7269-315">_nx_crypto_method_3des_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-315">_nx_crypto_method_3des_cleanup</span></span>

<span data-ttu-id="c7269-316">3DES 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-316">Clean up the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-317">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-317">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-318">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-318">Description</span></span>

<span data-ttu-id="c7269-319">애플리케이션에서는 이 3DES 세션이 더 이상 필요 없다고 확인되면 3DES 제어 블록을 정리하기 위해 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-319">Application calls this function to clean up the 3DES control block after it determines this 3DES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-320">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-320">Parameters</span></span>

- <span data-ttu-id="c7269-321">**handle** *_nx_crypto_method_3des_init()* 를 통해 초기화된 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-321">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-322">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-322">Return Values</span></span>

- <span data-ttu-id="c7269-323">**NX_CRYPTO_SUCCESS** (0x00) 3DES 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-323">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the 3DES session.</span></span>
- <span data-ttu-id="c7269-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_drbg_init"></a><span data-ttu-id="c7269-325">_nx_crypto_method_drbg_init</span><span class="sxs-lookup"><span data-stu-id="c7269-325">_nx_crypto_method_drbg_init</span></span>

<span data-ttu-id="c7269-326">DRBG 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-326">Initializes the DRBG crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-327">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-327">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-328">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-328">Description</span></span>

<span data-ttu-id="c7269-329">이 함수는 제공된 키 문자열을 사용하여 DRBG 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-329">This function initializes the DRBG control block with the given key string.</span></span> <span data-ttu-id="c7269-330">DRBG 제어 블록이 초기화되면 후속 DRBG 작업에서 동일한 제어 블록이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-330">Once the DRBG control block is initialized, subsequent DRBG operation shall be using the same control block.</span></span>

<span data-ttu-id="c7269-331">애플리케이션에서는 각각 세션을 나타내는 여러 DRBG 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-331">Application may create multiple DRBG control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-332">DRBG 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-332">Initializing the DRBG control block starts a new hash computation session.</span></span> <span data-ttu-id="c7269-333">DRBG 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-333">Re-initializing the DRBG control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-334">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-334">Parameters</span></span>

- <span data-ttu-id="c7269-335">**method** 유효한 DRBG 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-335">**method** Pointer to a valid DRBG crypto method control block.</span></span> <span data-ttu-id="c7269-336">다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-336">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-337">*crypto_method_drbg*</span><span class="sxs-lookup"><span data-stu-id="c7269-337">*crypto_method_drbg*</span></span>
- <span data-ttu-id="c7269-338">**key** DRBG에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-338">**key** This field is not used for DRBG.</span></span>
- <span data-ttu-id="c7269-339">**key_size_in_bits** DRBG에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-339">**key_size_in_bits** This field is not used for DRBG.</span></span>
- <span data-ttu-id="c7269-340">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-340">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-341">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-341">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-342">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-342">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-343">**crypto_metadata** DRBG 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-343">**crypto_metadata** Pointer to a valid memory space for the DRBG control block.</span></span> <span data-ttu-id="c7269-344">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-344">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-345">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-345">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-346">DRBG의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_DRBG)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-346">For DRBG, the metadata size must be *sizeof(NX_CRYPTO_DRBG)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-347">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-347">Return Values</span></span>

- <span data-ttu-id="c7269-348">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 DRBG 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-348">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the DRBG control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-350">**NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-350">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_drbg_operation"></a><span data-ttu-id="c7269-351">_nx_crypto_method_drbg_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-351">_nx_crypto_method_drbg_operation</span></span>

<span data-ttu-id="c7269-352">DRBG 작업 수행</span><span class="sxs-lookup"><span data-stu-id="c7269-352">Perform DRBG operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-353">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-353">Prototype</span></span>

```c
UINT __nx_crypto_method_drbg_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c7269-354">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-354">Description</span></span>

<span data-ttu-id="c7269-355">이 함수는 DRBG 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-355">This function performs DRBG operation.</span></span> <span data-ttu-id="c7269-356">DRBG 제어 블록은 _ *nx_crypto_method_drbg_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-356">The DRBG control block must have been initialized with _ *nx_crypto_method_drbg_init()*.</span></span> <span data-ttu-id="c7269-357">수행할 DRBG 알고리즘은 *메서드* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-357">The DRBG algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span> <span data-ttu-id="c7269-358">기본적으로 DRBG에는 AES-128이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-358">By default AES-128 is used for DRBG.</span></span>

<span data-ttu-id="c7269-359">작업이 NX_CRYPTO_DRBG_OPTIONS_SET이면 입력은 NX_CRYPTO_DRBG_OPTIONS 구조를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-359">When the operation is NX_CRYPTO_DRBG_OPTIONS_SET, the input points to NX_CRYPTO_DRBG_OPTIONS structure.</span></span> <span data-ttu-id="c7269-360">작업이 NX_CRYPTO_DRBG_INSTANTIATE이면 키는 nonce를 가리키고 입력은 개인 설정 문자열을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-360">When the operation is NX_CRYPTO_DRBG_INSTANTIATE, the key points to nonce, input points to personalization string.</span></span> <span data-ttu-id="c7269-361">작업이 NX_CRYPTO_DRBG_RESEED 또는 NX_CRYPTO_DRBG_GENERATE이면 입력은 추가 입력을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-361">When the operation is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, the input points to additional input.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-362">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-362">Parameters</span></span>

- <span data-ttu-id="c7269-363">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-363">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-364">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-364">Valid operation is:</span></span>
  - <span data-ttu-id="c7269-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span><span class="sxs-lookup"><span data-stu-id="c7269-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span></span>
  - <span data-ttu-id="c7269-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span></span>
  - <span data-ttu-id="c7269-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span></span>
- <span data-ttu-id="c7269-368">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-368">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-369">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-369">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-370">**method** 유효한 DRBG 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-370">**method** Pointer to the valid DRBG crypto method.</span></span> <span data-ttu-id="c7269-371">여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_drbg_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-371">The crypto method used here must be the same used in the _ *nx_crypto_method_drbg_init().*</span></span>
- <span data-ttu-id="c7269-372">**key** 인스턴스화 작업의 nonce에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-372">**key** Pointer to the the nonce for the instantiate operation.</span></span> <span data-ttu-id="c7269-373">이 필드는 다른 작업에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-373">This field is not used for other operations.</span></span>
- <span data-ttu-id="c7269-374">**key_size_in_bits** nonce의 크기(비트).</span><span class="sxs-lookup"><span data-stu-id="c7269-374">**key_size_in_bits** Size of the nonce, in bits.</span></span> <span data-ttu-id="c7269-375">이 필드는 다른 작업에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-375">This field is not used for other operations.</span></span>
- <span data-ttu-id="c7269-376">**input** op가 NX_CRYPTO_DRBG_OPTIONS_SET이면 이 필드는 DRBG 옵션을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-376">**input** When op is NX_CRYPTO_DRBG_OPTIONS_SET, this field points to DRBG options.</span></span> <span data-ttu-id="c7269-377">op가 NX_CRYPTO_DRBG_INSTANTIATE이면 이 필드는 개인 설정 문자열을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-377">When op is NX_CRYPTO_DRBG_INSTANTIATE, this field points to personalization string.</span></span> <span data-ttu-id="c7269-378">op가 NX_CRYPTO_DRBG_RESEED 또는 NX_CRYPTO_DRBG_GENERATE이면 이 필드는 추가 입력 데이터를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-378">When op is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, this field points to additional input data.</span></span>
- <span data-ttu-id="c7269-379">**input_length_in_byte** 입력 데이터의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-379">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c7269-380">**iv_ptr** DRBG에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-380">**iv_ptr** This field is not used for DRBG.</span></span>
- <span data-ttu-id="c7269-381">**output** op가 NX_CRYPTO_DRBG_GENERATE이면 이 필드는 생성된 DRBG의 메모리 영역을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-381">**output** When op is NX_CRYPTO_DRBG_GENERATE, this field points to the memory area for the generated DRBG.</span></span> <span data-ttu-id="c7269-382">그렇지 않으면 이 필드는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-382">Otherwise, this field is not used.</span></span>
- <span data-ttu-id="c7269-383">**output_length_in_byte** 출력 버퍼의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-383">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c7269-384">**crypto_metadata** *_nx_crypto_method_aes_init()* 에 사용되는 DRBG 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-384">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>
- <span data-ttu-id="c7269-385">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-385">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-386">DRBG의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_DRBG)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-386">For DRBG, the metadata size must *sizeof(NX_CRYPTO_DRBG)*</span></span>
- <span data-ttu-id="c7269-387">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-387">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-388">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-388">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-389">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-389">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-390">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-390">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-391">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-391">Return Values</span></span>

- <span data-ttu-id="c7269-392">**NX_CRYPTO_SUCCESS** (0x00) DRBG 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-392">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the DRBG operation.</span></span>
- <span data-ttu-id="c7269-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-394">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-394">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 DRBG 알고리즘이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid DRBG algorithm being specified.</span></span>
- <span data-ttu-id="c7269-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_drbg_cleanup"></a><span data-ttu-id="c7269-397">_nx_crypto_method_drbg_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-397">_nx_crypto_method_drbg_cleanup</span></span>

<span data-ttu-id="c7269-398">DRBG 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-398">Clean up the DRBG control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-399">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-399">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-400">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-400">Description</span></span>

<span data-ttu-id="c7269-401">애플리케이션에서는 이 DRBG 세션이 더 이상 필요 없다고 확인되면 DRBG 제어 블록을 정리하기 위해 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-401">Application calls this function to clean up the DRBG control block after it determines this DRBG session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-402">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-402">Parameters</span></span>

- <span data-ttu-id="c7269-403">**crypto_metadata** *_nx_crypto_method_aes_init()* 에 사용되는 DRBG 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-403">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-404">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-404">Return Values</span></span>

- <span data-ttu-id="c7269-405">**NX_CRYPTO_SUCCESS** (0x00) DRBG 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-405">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the DRBG session.</span></span>
- <span data-ttu-id="c7269-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdh_init"></a><span data-ttu-id="c7269-407">_nx_crypto_method_ecdh_init</span><span class="sxs-lookup"><span data-stu-id="c7269-407">_nx_crypto_method_ecdh_init</span></span>

<span data-ttu-id="c7269-408">ECDH 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-408">Initializes the ECDH crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-409">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-409">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-410">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-410">Description</span></span>

<span data-ttu-id="c7269-411">이 함수는 제공된 키 문자열을 사용하여 ECDH 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-411">This function initializes the ECDH control block with the given key string.</span></span> <span data-ttu-id="c7269-412">ECDH 제어 블록이 초기화되면 후속 ECDH 작업에서 동일한 제어 블록이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-412">Once the ECDH control block is initialized, subsequent ECDH operation shall be using the same control block.</span></span>

<span data-ttu-id="c7269-413">애플리케이션에서는 각각 세션을 나타내는 여러 ECDH 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-413">Application may create multiple ECDH control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-414">ECDH 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-414">Initializing the ECDH control block starts a new hash computation session.</span></span> <span data-ttu-id="c7269-415">ECDH 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-415">Re-initializing the ECDH control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-416">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-416">Parameters</span></span>

- <span data-ttu-id="c7269-417">**method** 유효한 ECDH 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-417">**method** Pointer to a valid ECDH crypto method control block.</span></span> <span data-ttu-id="c7269-418">다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-418">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-419">*crypto_method_ecdh*</span><span class="sxs-lookup"><span data-stu-id="c7269-419">*crypto_method_ecdh*</span></span>
- <span data-ttu-id="c7269-420">**key** ECDH에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-420">**key** This field is not used for ECDH.</span></span>
- <span data-ttu-id="c7269-421">**key_size_in_bits** ECDH에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-421">**key_size_in_bits** This field is not used for ECDH.</span></span>
- <span data-ttu-id="c7269-422">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-422">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-423">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-423">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-424">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-424">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-425">**crypto_metadata** ECDH 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-425">**crypto_metadata** Pointer to a valid memory space for the ECDH control block.</span></span> <span data-ttu-id="c7269-426">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-426">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-427">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-427">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-428">ECDH의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_ECDH)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-428">For ECDH, the metadata size must be *sizeof(NX_CRYPTO_ECDH)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-429">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-429">Return Values</span></span>

- <span data-ttu-id="c7269-430">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 ECDH 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-430">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDH control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-432">**NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-432">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdh_operation"></a><span data-ttu-id="c7269-433">_nx_crypto_method_ecdh_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-433">_nx_crypto_method_ecdh_operation</span></span>

<span data-ttu-id="c7269-434">ECDH 작업 수행</span><span class="sxs-lookup"><span data-stu-id="c7269-434">Perform ECDH operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-435">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-435">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c7269-436">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-436">Description</span></span>

<span data-ttu-id="c7269-437">이 함수는 ECDH 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-437">This function performs ECDH operation.</span></span> <span data-ttu-id="c7269-438">ECDH 제어 블록은 _ *nx_crypto_method_ecdh_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-438">The ECDH control block must have been initialized with _ *nx_crypto_method_ecdh_init()*.</span></span> <span data-ttu-id="c7269-439">수행할 ECDH 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-439">The ECDH algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-440">작업이 NX_CRYPTO_EC_CURVE_SET이면 입력은 Elliptic Curve 암호화 메서드를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-440">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="c7269-441">작업이 NX_CRYPTO_EC_KEY_PAIR_GENERATE이면 출력은 NX_CRYPTO_EXTENDED_OUTPUT 구조를 가리키고 키 쌍이 nx_crypto_extended_output_data에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-441">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="c7269-442">작업이 NX_CRYPTO_DH_SETUP이면 공개 키가 nx_crypto_extended_output_data에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-442">When the operation is NX_CRYPTO_DH_SETUP, the public key is returned to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="c7269-443">작업이 NX_CRYPTO_DH_KEY_PAIR_IMPORT이면 입력은 공개 키를 가리키고 키는 프라이빗 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-443">When the operation is NX_CRYPTO_DH_KEY_PAIR_IMPORT, the input points to public key and key points to private key.</span></span> <span data-ttu-id="c7269-444">작업이 NX_CRYPTO_DH_PRIVATE_KEY_EXPORT이면 프라이빗 키가 nx_crypto_extended_output_data에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-444">When the operation is NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, the private key is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="c7269-445">작업이 NX_CRYPTO_DH_CALCULATE이면 입력은 원격 공개 키를 가리키고 공유 비밀이 nx_crypto_extended_output_data에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-445">When the operation is NX_CRYPTO_DH_CALCULATE, the input points to remote public key and the shared secret is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-446">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-446">Parameters</span></span>

- <span data-ttu-id="c7269-447">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-447">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-448">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-448">Valid operation is:</span></span>
  - <span data-ttu-id="c7269-449">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="c7269-449">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="c7269-450">*NX_CRYPTO_DH_SETUP*</span><span class="sxs-lookup"><span data-stu-id="c7269-450">*NX_CRYPTO_DH_SETUP*</span></span>
  - <span data-ttu-id="c7269-451">*NX_CRYPTO_DH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-451">*NX_CRYPTO_DH_CALCULATE*</span></span>
  - <span data-ttu-id="c7269-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span><span class="sxs-lookup"><span data-stu-id="c7269-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span></span>
  - <span data-ttu-id="c7269-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span></span>
  - <span data-ttu-id="c7269-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span><span class="sxs-lookup"><span data-stu-id="c7269-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span></span>
- <span data-ttu-id="c7269-455">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-455">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-456">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-456">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-457">**method** 유효한 ECDH 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-457">**method** Pointer to the valid ECDH crypto method.</span></span> <span data-ttu-id="c7269-458">여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_ecdh_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-458">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdh_init().*</span></span>
- <span data-ttu-id="c7269-459">**key** op가 NX_CRYPTO_DH_IMPORT_KEY_PAIR이면 이 필드는 프라이빗 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-459">**key** When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to private key.</span></span> <span data-ttu-id="c7269-460">그렇지 않으면 이 필드는 ECDH에 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-460">Otherwise, this field is not used for ECDH.</span></span>
- <span data-ttu-id="c7269-461">**key_size_in_bits** 키의 크기(비트)</span><span class="sxs-lookup"><span data-stu-id="c7269-461">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c7269-462">**input** op가 NX_CRYPTO_EC_CURVE_SET이면 이 필드는 Elliptic Curve 암호화 메서드를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-462">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="c7269-463">op가 NX_CRYPTO_DH_SETUP이면 이 필드는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-463">When op is NX_CRYPTO_DH_SETUP, this field is not used.</span></span> <span data-ttu-id="c7269-464">op가 NX_CRYPTO_DH_CALCULATE이면 이 필드는 입력 텍스트 데이터를 포함하는 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-464">When op is NX_CRYPTO_DH_CALCULATE, this field points to a buffer containing input text data.</span></span> <span data-ttu-id="c7269-465">op가 NX_CRYPTO_DH_IMPORT_KEY_PAIR이면 이 필드는 공개 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-465">When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to public key.</span></span>
- <span data-ttu-id="c7269-466">**input_length_in_byte** 입력 데이터의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-466">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c7269-467">**iv_ptr** ECDH에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-467">**iv_ptr** This field is not used for ECDH.</span></span>
- <span data-ttu-id="c7269-468">**output** op가 NX_CRYPTO_EC_CURVE_SET 또는 NX_CRYPTO_DH_IMPORT_KEY_PAIR이면 이 필드는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-468">**output** When op is NX_CRYPTO_EC_CURVE_SET or NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field is not used.</span></span> <span data-ttu-id="c7269-469">op가 NX_CRYPTO_DH_SETUP이면 이 필드는 생성된 ECDH 공개 키의 메모리 영역을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-469">When op is NX_CRYPTO_DH_SETUP, this field points to the memory area for the generated ECDH public key.</span></span> <span data-ttu-id="c7269-470">op가 NX_CRYPTO_DH_CALCULATE이면 이 필드는 생성된 ECDH 공유 비밀의 메모리 영역을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-470">When op is NX_CRYPTO_DH_CALCULATE, this field points to the memory area for the generated ECDH shared secret.</span></span>
- <span data-ttu-id="c7269-471">**output_length_in_byte** 출력 버퍼의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-471">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c7269-472">**crypto_metadata** *_nx_crypto_method_ecdh_init()* 에 사용되는 ECDH 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-472">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>
- <span data-ttu-id="c7269-473">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-473">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-474">ECDH의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_ECDH)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-474">For ECDH, the metadata size must *sizeof(NX_CRYPTO_ECDH)*</span></span>
- <span data-ttu-id="c7269-475">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-475">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-476">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-476">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-477">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-477">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-478">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-478">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-479">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-479">Return Values</span></span>

- <span data-ttu-id="c7269-480">**NX_CRYPTO_SUCCESS** (0x00) ECDH 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-480">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDH operation.</span></span>
- <span data-ttu-id="c7269-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-482">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-482">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 ECDH 알고리즘이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDH algorithm being specified.</span></span>
- <span data-ttu-id="c7269-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdh_cleanup"></a><span data-ttu-id="c7269-485">_nx_crypto_method_ecdh_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-485">_nx_crypto_method_ecdh_cleanup</span></span>

<span data-ttu-id="c7269-486">ECDH 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-486">Clean up the ECDH control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-487">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-487">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-488">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-488">Description</span></span>

<span data-ttu-id="c7269-489">애플리케이션에서는 이 ECDH 세션이 더 이상 필요 없다고 확인되면 ECDH 제어 블록을 정리하기 위해 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-489">Application calls this function to clean up the ECDH control block after it determines this ECDH session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-490">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-490">Parameters</span></span>

- <span data-ttu-id="c7269-491">**crypto_metadata** *_nx_crypto_method_ecdh_init()* 에 사용되는 ECDH 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-491">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-492">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-492">Return Values</span></span>

- <span data-ttu-id="c7269-493">**NX_CRYPTO_SUCCESS** (0x00) ECDH 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-493">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDH session.</span></span>
- <span data-ttu-id="c7269-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdsa_init"></a><span data-ttu-id="c7269-495">_nx_crypto_method_ecdsa_init</span><span class="sxs-lookup"><span data-stu-id="c7269-495">_nx_crypto_method_ecdsa_init</span></span>

<span data-ttu-id="c7269-496">ECDSA 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-496">Initializes the ECDSA crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-497">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-497">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-498">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-498">Description</span></span>

<span data-ttu-id="c7269-499">이 함수는 제공된 키 문자열을 사용하여 ECDSA 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-499">This function initializes the ECDSA control block with the given key string.</span></span> <span data-ttu-id="c7269-500">ECDSA 제어 블록이 초기화되면 후속 ECDSA 작업에서 동일한 제어 블록이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-500">Once the ECDSA control block is initialized, subsequent ECDSA operation shall be using the same control block.</span></span>

<span data-ttu-id="c7269-501">애플리케이션에서는 각각 세션을 나타내는 여러 ECDSA 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-501">Application may create multiple ECDSA control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-502">ECDSA 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-502">Initializing the ECDSA control block starts a new hash computation session.</span></span> <span data-ttu-id="c7269-503">ECDSA 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-503">Re-initializing the ECDSA control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-504">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-504">Parameters</span></span>

- <span data-ttu-id="c7269-505">**method** 유효한 ECDSA 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-505">**method** Pointer to a valid ECDSA crypto method control block.</span></span> <span data-ttu-id="c7269-506">다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-506">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-507">*crypto_method_ecdsa*</span><span class="sxs-lookup"><span data-stu-id="c7269-507">*crypto_method_ecdsa*</span></span>
- <span data-ttu-id="c7269-508">**key** ECDSA에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-508">**key** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="c7269-509">**key_size_in_bits** ECDSA에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-509">**key_size_in_bits** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="c7269-510">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-510">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-511">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-511">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-512">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-512">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-513">**crypto_metadata** ECDSA 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-513">**crypto_metadata** Pointer to a valid memory space for the ECDSA control block.</span></span> <span data-ttu-id="c7269-514">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-514">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-515">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-515">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-516">ECDSA의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_ECDSA)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-516">For ECDSA, the metadata size must be *sizeof(NX_CRYPTO_ECDSA)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-517">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-517">Return Values</span></span>

- <span data-ttu-id="c7269-518">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 ECDSA 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-518">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDSA control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-520">**NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-520">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdsa_operation"></a><span data-ttu-id="c7269-521">_nx_crypto_method_ecdsa_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-521">_nx_crypto_method_ecdsa_operation</span></span>

<span data-ttu-id="c7269-522">ECDSA 작업 수행</span><span class="sxs-lookup"><span data-stu-id="c7269-522">Perform ECDSA operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-523">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-523">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c7269-524">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-524">Description</span></span>

<span data-ttu-id="c7269-525">이 함수는 ECDSA 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-525">This function performs ECDSA operation.</span></span> <span data-ttu-id="c7269-526">ECDSA 제어 블록은 _ *nx_crypto_method_ecdsa_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-526">The ECDSA control block must have been initialized with _ *nx_crypto_method_ecdsa_init()*.</span></span> <span data-ttu-id="c7269-527">수행할 ECDSA 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-527">The ECDSA algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-528">작업이 NX_CRYPTO_EC_CURVE_SET이면 입력은 Elliptic Curve 암호화 메서드를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-528">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="c7269-529">작업이 NX_CRYPTO_EC_KEY_PAIR_GENERATE이면 출력은 NX_CRYPTO_EXTENDED_OUTPUT 구조를 가리키고 키 쌍이 nx_crypto_extended_output_data에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-529">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-530">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-530">Parameters</span></span>

- <span data-ttu-id="c7269-531">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-531">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-532">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-532">Valid operation is:</span></span>
  - <span data-ttu-id="c7269-533">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="c7269-533">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="c7269-534">*NX_CRYPTO_AUTHENTICATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-534">*NX_CRYPTO_AUTHENTICATE*</span></span>
  - <span data-ttu-id="c7269-535">*NX_CRYPTO_VERIFY*</span><span class="sxs-lookup"><span data-stu-id="c7269-535">*NX_CRYPTO_VERIFY*</span></span>
- <span data-ttu-id="c7269-536">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-536">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-537">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-537">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-538">**method** 유효한 ECDSA 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-538">**method** Pointer to the valid ECDSA crypto method.</span></span> <span data-ttu-id="c7269-539">여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_ecdsa_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-539">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdsa_init().*</span></span>
- <span data-ttu-id="c7269-540">**key** op가 NX_CRYPTO_VERIFY이면 이 필드는 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-540">**key** Points to the key when op is NX_CRYPTO_VERIFY.</span></span> <span data-ttu-id="c7269-541">키 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-541">There are not restrictions on key buffer.</span></span> <span data-ttu-id="c7269-542">이 필드는 다른 op 값에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-542">This field is not used for other values of op.</span></span>
- <span data-ttu-id="c7269-543">**key_size_in_bits** 키의 크기(비트)</span><span class="sxs-lookup"><span data-stu-id="c7269-543">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c7269-544">**input** op가 NX_CRYPTO_EC_CURVE_SET이면 이 필드는 Elliptic Curve 암호화 메서드를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-544">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="c7269-545">그렇지 않으면 이 필드는 입력 텍스트 데이터를 포함하는 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-545">Otherwise, this field points to a buffer containing input text data.</span></span>
- <span data-ttu-id="c7269-546">**input_length_in_byte** 입력 데이터의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-546">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c7269-547">**iv_ptr** ECDSA에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-547">**iv_ptr** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="c7269-548">**output** op가 NX_CRYPTO_EC_CURVE_SET이면 이 필드는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-548">**output** When op is NX_CRYPTO_EC_CURVE_SET, this field is not used.</span></span> <span data-ttu-id="c7269-549">op가 NX_CRYPTO_AUTHENTICATE이면 이 필드는 생성된 ECDSA 서명의 메모리 영역을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-549">When op is NX_CRYPTO_AUTHENTICATE, this field points to the memory area for the generated ECDSA signature.</span></span> <span data-ttu-id="c7269-550">op가 NX_CRYPTO_VERIFY이면 이 필드는 확인된 ECDSA 서명의 메모리 영역을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-550">When op is NX_CRYPTO_VERIFY, this field points to the memory area for the verified ECDSA signature.</span></span>
- <span data-ttu-id="c7269-551">**output_length_in_byte** 출력 버퍼의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-551">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c7269-552">**crypto_metadata** *_nx_crypto_method_ecdsa_init()* 에 사용되는 ECDSA 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-552">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>
- <span data-ttu-id="c7269-553">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-553">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-554">ECDSA의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_ECDSA)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-554">For ECDSA, the metadata size must *sizeof(NX_CRYPTO_ECDSA)*</span></span>
- <span data-ttu-id="c7269-555">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-555">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-556">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-556">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-557">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-557">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-558">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-558">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-559">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-559">Return Values</span></span>

- <span data-ttu-id="c7269-560">**NX_CRYPTO_SUCCESS** (0x00) ECDSA 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-560">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDSA operation.</span></span>
- <span data-ttu-id="c7269-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-562">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-562">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 ECDSA 알고리즘이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDSA algorithm being specified.</span></span>
- <span data-ttu-id="c7269-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdsa_cleanup"></a><span data-ttu-id="c7269-565">_nx_crypto_method_ecdsa_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-565">_nx_crypto_method_ecdsa_cleanup</span></span>

<span data-ttu-id="c7269-566">ECDSA 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-566">Clean up the ECDSA control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-567">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-567">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-568">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-568">Description</span></span>

<span data-ttu-id="c7269-569">애플리케이션에서는 이 ECDSA 세션이 더 이상 필요 없다고 확인되면 ECDSA 제어 블록을 정리하기 위해 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-569">Application calls this function to clean up the ECDSA control block after it determines this ECDSA session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-570">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-570">Parameters</span></span>

- <span data-ttu-id="c7269-571">**crypto_metadata** *_nx_crypto_method_ecdsa_init()* 에 사용되는 ECDSA 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-571">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-572">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-572">Return Values</span></span>

- <span data-ttu-id="c7269-573">**NX_CRYPTO_SUCCESS** (0x00) ECDSA 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-573">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDSA session.</span></span>
- <span data-ttu-id="c7269-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_md5_init"></a><span data-ttu-id="c7269-575">_nx_crypto_method_hmac_md5_init</span><span class="sxs-lookup"><span data-stu-id="c7269-575">_nx_crypto_method_hmac_md5_init</span></span>

<span data-ttu-id="c7269-576">HMAC MD5 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-576">Initializes the HMAC MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-577">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-577">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-578">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-578">Description</span></span>

<span data-ttu-id="c7269-579">이 함수는 제공된 키 문자열을 사용하여 HMAC MD5 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-579">This function initializes the HMAC MD5 control block with the given key string.</span></span> <span data-ttu-id="c7269-580">HMAC MD5 제어 블록이 초기화되면 후속 HMAC MD5 작업에서 동일한 제어 블록이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-580">Once the HMAC MD5 control block is initialized, subsequent HMAC MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="c7269-581">애플리케이션에서는 각각 세션을 나타내는 여러 HMAC MD5 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-581">Application may create multiple HMAC MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-582">HMAC MD5 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-582">Initializing the HMAC MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="c7269-583">HMAC MD5 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-583">Re-initializing the HMAC MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-584">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-584">Parameters</span></span>

- <span data-ttu-id="c7269-585">**method** 유효한 HMAC MD5 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-585">**method** Pointer to a valid HMAC MD5 crypto method control block.</span></span>
<span data-ttu-id="c7269-586">다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-586">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-587">*crypto_method_hmac_md5*</span><span class="sxs-lookup"><span data-stu-id="c7269-587">*crypto_method_hmac_md5*</span></span>
- <span data-ttu-id="c7269-588">**key** 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-588">**key** Points to the key.</span></span> <span data-ttu-id="c7269-589">키 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-589">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c7269-590">**key_size_in_bits** 키의 크기(비트)</span><span class="sxs-lookup"><span data-stu-id="c7269-590">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c7269-591">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-591">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-592">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-592">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-593">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-593">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-594">**crypto_metadata** HMAC MD5 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-594">**crypto_metadata** Pointer to a valid memory space for the HMAC MD5 control block.</span></span> <span data-ttu-id="c7269-595">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-595">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-596">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-596">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-597">HMAC MD5의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_MD5_HMAC)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-597">For HMAC MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-598">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-598">Return Values</span></span>

- <span data-ttu-id="c7269-599">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 HMAC MD5 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-599">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-601">**NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-601">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_md5_operation"></a><span data-ttu-id="c7269-602">_nx_crypto_method_hmac_md5_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-602">_nx_crypto_method_hmac_md5_operation</span></span>

<span data-ttu-id="c7269-603">HMAC MD5 해시 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-603">Perform an HMAC MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-604">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-604">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c7269-605">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-605">Description</span></span>

<span data-ttu-id="c7269-606">이 함수는 HMAC MD5 해시 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-606">This function performs HMAC MD5 hash operation.</span></span> <span data-ttu-id="c7269-607">HMAC MD5 제어 블록은 _ *nx_crypto_method_hmac_md5_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-607">The HMAC MD5 control block must have been initialized with _ *nx_crypto_method_hmac_md5_init()*.</span></span> <span data-ttu-id="c7269-608">수행할 HMAC MD5 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-608">The HMAC MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-609">최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 출력 버퍼 크기가 16바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-609">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="c7269-610">이 작업은 상태 정보를 유지하지 않으며, HMAC MD5 제어 블록의 키 자료를 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-610">This operation does not keep state information, and does not alter the key material in the HMAC MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-611">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-611">Parameters</span></span>

- <span data-ttu-id="c7269-612">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-612">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-613">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-613">Valid operation is:</span></span>
  - <span data-ttu-id="c7269-614">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c7269-614">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c7269-615">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-615">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c7269-616">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-616">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c7269-617">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-617">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-618">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-618">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-619">**method** 유효한 HMAC MD5 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-619">**method** Pointer to the valid HMAC MD5 crypto method.</span></span> <span data-ttu-id="c7269-620">여기서 사용하는 암호화 메서드를 *nx_crypto_method_hmac_md5_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-620">The crypto method used here must be the same used in the *nx_crypto_method_hmac_md5_init().*</span></span>
- <span data-ttu-id="c7269-621">**key** 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-621">**key** Points to the key.</span></span> <span data-ttu-id="c7269-622">키 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-622">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c7269-623">**key_size_in_bits** 키의 크기(비트)</span><span class="sxs-lookup"><span data-stu-id="c7269-623">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c7269-624">**input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-624">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c7269-625">입력 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-625">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c7269-626">**input_data_size** 입력 데이터의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-626">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c7269-627">**iv_ptr** HMAC MD5에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-627">**iv_ptr** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="c7269-628">**iv_size** HMAC MD5에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-628">**iv_size** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="c7269-629">**output_buffer** 생성된 HMAC MD5 해시의 메모리 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-629">**output_buffer** Pointer to the memory area for the generated HMAC MD5 hash.</span></span>
- <span data-ttu-id="c7269-630">**output_buffer_size** 출력 버퍼의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-630">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c7269-631">**crypto_metadata** *_nx_crypto_method_hmac_md5_init()* 에 사용되는 HMAC MD5 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-631">**crypto_metadata** Pointer to the HMAC MD5 control block used in *_nx_crypto_method_hmac_md5_init()*.</span></span>
- <span data-ttu-id="c7269-632">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-632">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-633">HMAC MD5의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_MD5_HMAC)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-633">For HMAC MD5, the metadata size must *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>
- <span data-ttu-id="c7269-634">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-634">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-635">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-635">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-636">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-636">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-637">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-637">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-638">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-638">Return Values</span></span>

- <span data-ttu-id="c7269-639">**NX_CRYPTO_SUCCESS** (0x00) HMAC MD5 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-639">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC MD5 operation.</span></span>
- <span data-ttu-id="c7269-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-641">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-641">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 HMAC MD5 알고리즘이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC MD5 algorithm being specified.</span></span>
- <span data-ttu-id="c7269-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_init"></a><span data-ttu-id="c7269-644">_nx_crypto_method_hmac_sha1_init</span><span class="sxs-lookup"><span data-stu-id="c7269-644">_nx_crypto_method_hmac_sha1_init</span></span>

<span data-ttu-id="c7269-645">HMAC SHA1 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-645">Initializes the HMAC SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-646">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-646">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-647">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-647">Description</span></span>

<span data-ttu-id="c7269-648">이 함수는 제공된 키 문자열을 사용하여 HMAC SHA1 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-648">This function initializes the HMAC SHA1 control block with the given key string.</span></span> <span data-ttu-id="c7269-649">HMAC SHA1 제어 블록이 초기화되면 후속 HMAC SHA1 작업에서 동일한 제어 블록이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-649">Once the HMAC SHA1 control block is initialized, subsequent HMAC SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="c7269-650">애플리케이션에서는 각각 세션을 나타내는 여러 HMAC SHA1 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-650">Application may create multiple HMAC SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-651">HMAC SHA1 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-651">Initializing the HMAC SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="c7269-652">HMAC SHA1 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-652">Re-initializing the HMAC SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-653">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-653">Parameters</span></span>

- <span data-ttu-id="c7269-654">**method** 유효한 HMAC SHA1 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-654">**method** Pointer to a valid HMAC SHA1 crypto method control block.</span></span> <span data-ttu-id="c7269-655">다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-655">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-656">*crypto_method_hmac_sha1*</span><span class="sxs-lookup"><span data-stu-id="c7269-656">*crypto_method_hmac_sha1*</span></span>
- <span data-ttu-id="c7269-657">**key** 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-657">**key** Points to the key.</span></span> <span data-ttu-id="c7269-658">키 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-658">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c7269-659">**key_size_in_bits** 키의 크기(비트)</span><span class="sxs-lookup"><span data-stu-id="c7269-659">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c7269-660">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-660">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-661">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-661">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-662">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-662">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-663">**crypto_metadata** HMAC SHA1 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-663">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA1 control block.</span></span> <span data-ttu-id="c7269-664">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-664">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-665">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-665">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-666">HMAC SHA1의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA1_HMAC)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-666">For HMAC SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-667">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-667">Return Values</span></span>

- <span data-ttu-id="c7269-668">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 HMAC SHA1 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-668">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-670">**NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-670">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_operation"></a><span data-ttu-id="c7269-671">_nx_crypto_method_hmac_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-671">_nx_crypto_method_hmac_sha1_operation</span></span>

<span data-ttu-id="c7269-672">HMAC SHA1 해시 작업 수행</span><span class="sxs-lookup"><span data-stu-id="c7269-672">Perform HMAC SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-673">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-673">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c7269-674">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-674">Description</span></span>

<span data-ttu-id="c7269-675">이 함수는 HMAC SHA1 해시 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-675">This function performs HMAC SHA1 hash operation.</span></span> <span data-ttu-id="c7269-676">HMAC SHA1 제어 블록은 _ *nx_crypto_method_hmac_sha1_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-676">The HMAC SHA1 control block must have been initialized with _ *nx_crypto_method_hmac_sha1_init()*.</span></span> <span data-ttu-id="c7269-677">수행할 HMAC SHA1 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-677">The HMAC SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-678">최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 출력 버퍼 크기가 20바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-678">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-679">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-679">Parameters</span></span>

- <span data-ttu-id="c7269-680">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-680">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-681">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-681">Valid operation is:</span></span>
  - <span data-ttu-id="c7269-682">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c7269-682">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c7269-683">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-683">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c7269-684">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-684">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c7269-685">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-685">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-686">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-686">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-687">**method** 유효한 HMAC SHA1 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-687">**method** Pointer to the valid HMAC SHA1 crypto method.</span></span> <span data-ttu-id="c7269-688">여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_hmac_sha1_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-688">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha1_init().*</span></span>
- <span data-ttu-id="c7269-689">**key** 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-689">**key** Points to the key.</span></span> <span data-ttu-id="c7269-690">키 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-690">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c7269-691">**key_size_in_bits** 키의 크기(비트)</span><span class="sxs-lookup"><span data-stu-id="c7269-691">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c7269-692">**input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-692">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c7269-693">입력 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-693">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c7269-694">**input_data_size** 입력 데이터의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-694">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c7269-695">**iv_ptr** HMAC SHA1에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-695">**iv_ptr** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="c7269-696">**iv_size** HMAC SHA1에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-696">**iv_size** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="c7269-697">**output_buffer** 생성된 HMAC SHA1 해시의 메모리 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-697">**output_buffer** Pointer to the memory area for the generated HMAC SHA1 hash.</span></span>
- <span data-ttu-id="c7269-698">**output_buffer_size** 출력 버퍼의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-698">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c7269-699">**crypto_metadata** *_nx_crypto_method_hmac_sha1_init()* 에 사용되는 HMAC SHA1 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-699">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>
- <span data-ttu-id="c7269-700">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-700">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-701">HMAC SHA1의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA1_HMAC)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-701">For HMAC SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>
- <span data-ttu-id="c7269-702">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-702">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-703">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-703">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-704">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-704">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-705">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-705">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-706">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-706">Return Values</span></span>

- <span data-ttu-id="c7269-707">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA1 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-707">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA1 operation.</span></span>
- <span data-ttu-id="c7269-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-709">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-709">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 HMAC SHA1 알고리즘이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="c7269-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a><span data-ttu-id="c7269-712">_nx_crypto_method_hmac_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-712">_nx_crypto_method_hmac_sha1_cleanup</span></span>

<span data-ttu-id="c7269-713">HMAC SHA1 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-713">Clean up the HMAC SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-714">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-714">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-715">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-715">Description</span></span>

<span data-ttu-id="c7269-716">애플리케이션에서는 이 HMAC SHA1 세션이 더 이상 필요 없다고 확인되면 HMAC SHA1 제어 블록을 정리하기 위해 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-716">Application calls this function to clean up the HMAC SHA1 control block after it determines this HMAC SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-717">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-717">Parameters</span></span>

- <span data-ttu-id="c7269-718">**crypto_metadata** *_nx_crypto_method_hmac_sha1_init()* 에 사용되는 HMAC SHA1 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-718">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-719">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-719">Return Values</span></span>

- <span data-ttu-id="c7269-720">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA1 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-720">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA1 session.</span></span>
- <span data-ttu-id="c7269-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_init"></a><span data-ttu-id="c7269-722">_nx_crypto_method_hmac_sha256_init</span><span class="sxs-lookup"><span data-stu-id="c7269-722">_nx_crypto_method_hmac_sha256_init</span></span>

<span data-ttu-id="c7269-723">HMAC SHA256 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-723">Initializes the HMAC SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-724">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-724">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-725">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-725">Description</span></span>

<span data-ttu-id="c7269-726">이 함수는 제공된 키 문자열을 사용하여 HMAC SHA256 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-726">This function initializes the HMAC SHA256 control block with the given key string.</span></span> <span data-ttu-id="c7269-727">HMAC SHA256 제어 블록이 초기화되면 후속 HMAC SHA256 작업에서 동일한 제어 블록이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-727">Once the HMAC SHA256 control block is initialized, subsequent HMAC SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="c7269-728">애플리케이션에서는 각각 세션을 나타내는 여러 HMAC SHA256 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-728">Application may create multiple HMAC SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-729">HMAC SH256 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-729">Initializing the HMAC SH256 control block starts a new hash computation session.</span></span> <span data-ttu-id="c7269-730">HMAC SHA256 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 키를 사용하여 새 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-730">Re-initializing the HMAC SHA256 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-731">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-731">Parameters</span></span>

- <span data-ttu-id="c7269-732">**method** 유효한 HMAC SHA256 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-732">**method** Pointer to a valid HMAC SHA256 crypto method control block.</span></span> <span data-ttu-id="c7269-733">다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-733">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-734">*crypto_method_hmac_sha224*</span><span class="sxs-lookup"><span data-stu-id="c7269-734">*crypto_method_hmac_sha224*</span></span>
  - <span data-ttu-id="c7269-735">*crypto_method_hmac_sha256*</span><span class="sxs-lookup"><span data-stu-id="c7269-735">*crypto_method_hmac_sha256*</span></span>
- <span data-ttu-id="c7269-736">**key** 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-736">**key** Points to the key.</span></span> <span data-ttu-id="c7269-737">키 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-737">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c7269-738">**key_size_in_bits** 키의 크기(비트)</span><span class="sxs-lookup"><span data-stu-id="c7269-738">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c7269-739">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-739">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-740">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-740">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-741">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-741">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-742">**crypto_metadata** HMAC SHA256 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-742">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA256 control block.</span></span> <span data-ttu-id="c7269-743">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-743">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-744">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-744">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-745">HMAC SHA256의 경우 메타데이터 크기가 *sizeof(NX_CRYTPO_SHA256_HMAC)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-745">For HMAC SHA256, the metadata size must be *sizeof(NX_CRYTPO_SHA256_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-746">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-746">Return Values</span></span>

- <span data-ttu-id="c7269-747">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 HMAC SHA256 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-747">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-749">**NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-749">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_operation"></a><span data-ttu-id="c7269-750">_nx_crypto_method_hmac_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-750">_nx_crypto_method_hmac_sha256_operation</span></span>

<span data-ttu-id="c7269-751">HMAC SHA256 해시 작업 수행</span><span class="sxs-lookup"><span data-stu-id="c7269-751">Perform HMAC SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-752">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-752">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c7269-753">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-753">Description</span></span>

<span data-ttu-id="c7269-754">이 함수는 HMAC SHA256 해시 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-754">This function performs HMAC SHA256 hash operation.</span></span> <span data-ttu-id="c7269-755">HMAC SHA256 제어 블록은 _ *nx_crypto_method_hmac_sha256_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-755">The HMAC SHA256 control block must have been initialized with _ *nx_crypto_method_hmac_sha256_init()*.</span></span> <span data-ttu-id="c7269-756">수행할 HMAC SHA256 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-756">The HMAC SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-757">최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 SHA256의 출력 버퍼 크기는 32바이트여야 하고 SHA224의 출력 버퍼 크기는 28바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-757">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-758">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-758">Parameters</span></span>

- <span data-ttu-id="c7269-759">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-759">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-760">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-760">Valid operation is:</span></span>
  - <span data-ttu-id="c7269-761">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c7269-761">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c7269-762">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-762">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c7269-763">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-763">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c7269-764">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-764">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-765">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-765">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-766">**method** 유효한 HMAC SHA256 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-766">**method** Pointer to the valid HMAC SHA256 crypto method.</span></span> <span data-ttu-id="c7269-767">여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_hmac_sha256_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-767">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha256_init().*</span></span>
- <span data-ttu-id="c7269-768">**key** 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-768">**key** Points to the key.</span></span> <span data-ttu-id="c7269-769">키 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-769">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c7269-770">**key_size_in_bits** 키의 크기(비트)</span><span class="sxs-lookup"><span data-stu-id="c7269-770">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c7269-771">**input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-771">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c7269-772">입력 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-772">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c7269-773">**input_data_size** 입력 데이터의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-773">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c7269-774">**iv_ptr** HMAC SHA256에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-774">**iv_ptr** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="c7269-775">**iv_size** HMAC SHA256에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-775">**iv_size** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="c7269-776">**output_buffer** 생성된 HMAC SHA256 해시의 메모리 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-776">**output_buffer** Pointer to the memory area for the generated HMAC SHA256 hash.</span></span>
- <span data-ttu-id="c7269-777">**output_buffer_size** 출력 버퍼의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-777">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c7269-778">**crypto_metadata** *_nx_crypto_method_hmac_sha256_init()* 에 사용되는 HMAC SHA256 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-778">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>
- <span data-ttu-id="c7269-779">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-779">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-780">HMAC SHA256의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA256_HMAC)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-780">For HMAC SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256_HMAC)*</span></span>
- <span data-ttu-id="c7269-781">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-781">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-782">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-782">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-783">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-783">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-784">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-784">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-785">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-785">Return Values</span></span>

- <span data-ttu-id="c7269-786">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA256 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-786">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA256 operation.</span></span>
- <span data-ttu-id="c7269-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-788">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-788">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 HMAC SHA256 알고리즘이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="c7269-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a><span data-ttu-id="c7269-791">_nx_crypto_method_hmac_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-791">_nx_crypto_method_hmac_sha256_cleanup</span></span>

<span data-ttu-id="c7269-792">HMAC SHA256 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-792">Clean up the HMAC SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-793">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-793">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-794">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-794">Description</span></span>

<span data-ttu-id="c7269-795">애플리케이션에서는 이 HMAC SHA256 세션이 더 이상 필요 없다고 확인되면 HMAC SHA256 제어 블록을 정리하기 위해 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-795">Application calls this function to clean up the HMAC SHA256 control block after it determines this HMAC SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-796">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-796">Parameters</span></span>

- <span data-ttu-id="c7269-797">**crypto_metadata** *_nx_crypto_method_hmac_sha256_init()* 에 사용되는 HMAC SHA256 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-797">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-798">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-798">Return Values</span></span>

- <span data-ttu-id="c7269-799">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA256 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-799">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA256 session.</span></span>
- <span data-ttu-id="c7269-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_init"></a><span data-ttu-id="c7269-801">_nx_crypto_method_hmac_sha512_init</span><span class="sxs-lookup"><span data-stu-id="c7269-801">_nx_crypto_method_hmac_sha512_init</span></span>

<span data-ttu-id="c7269-802">HMAC SHA512 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-802">Initializes the HMAC SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-803">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-803">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-804">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-804">Description</span></span>

<span data-ttu-id="c7269-805">이 함수는 제공된 키 문자열을 사용하여 HMAC SHA512 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-805">This function initializes the HMAC SHA512 control block with the given key string.</span></span> <span data-ttu-id="c7269-806">HMAC SHA512 제어 블록이 초기화되면 후속 HMAC SHA512 작업에서 동일한 제어 블록이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-806">Once the HMAC SHA512 control block is initialized, subsequent HMAC SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="c7269-807">애플리케이션에서는 각각 세션을 나타내는 여러 HMAC SHA512 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-807">Application may create multiple HMAC SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-808">HMAC SH512 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-808">Initializing the HMAC SH512 control block starts a new hash computation session.</span></span> <span data-ttu-id="c7269-809">HMAC SHA512 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 키를 사용하여 새 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-809">Re-initializing the HMAC SHA512 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-810">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-810">Parameters</span></span>

- <span data-ttu-id="c7269-811">**method** 유효한 HMAC SHA512 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-811">**method** Pointer to a valid HMAC SHA512 crypto method control block.</span></span> <span data-ttu-id="c7269-812">다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-812">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-813">*crypto_method_hmac_sha384*</span><span class="sxs-lookup"><span data-stu-id="c7269-813">*crypto_method_hmac_sha384*</span></span>
  - <span data-ttu-id="c7269-814">*crypto_method_hmac_sha512*</span><span class="sxs-lookup"><span data-stu-id="c7269-814">*crypto_method_hmac_sha512*</span></span>
- <span data-ttu-id="c7269-815">**key** 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-815">**key** Points to the key.</span></span> <span data-ttu-id="c7269-816">키 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-816">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c7269-817">**key_size_in_bits** 키의 크기(비트)</span><span class="sxs-lookup"><span data-stu-id="c7269-817">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c7269-818">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-818">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-819">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-819">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-820">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-820">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-821">**crypto_metadata** HMAC SHA512 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-821">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA512 control block.</span></span> <span data-ttu-id="c7269-822">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-822">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-823">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-823">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-824">HMAC SHA512의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA512_HMAC)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-824">For HMAC SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-825">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-825">Return Values</span></span>

- <span data-ttu-id="c7269-826">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 HMAC SHA512 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-826">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-828">**NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-828">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_operation"></a><span data-ttu-id="c7269-829">_nx_crypto_method_hmac_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-829">_nx_crypto_method_hmac_sha512_operation</span></span>

<span data-ttu-id="c7269-830">HMAC SHA512 해시 작업 수행</span><span class="sxs-lookup"><span data-stu-id="c7269-830">Perform HMAC SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-831">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-831">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c7269-832">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-832">Description</span></span>

<span data-ttu-id="c7269-833">이 함수는 HMAC SHA512 해시 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-833">This function performs HMAC SHA512 hash operation.</span></span> <span data-ttu-id="c7269-834">HMAC SHA512 제어 블록은 _ *nx_crypto_method_hmac_sha512_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-834">The HMAC SHA512 control block must have been initialized with _ *nx_crypto_method_hmac_sha512_init()*.</span></span> <span data-ttu-id="c7269-835">수행할 HMAC SHA512 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-835">The HMAC SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-836">최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 SHA512의 출력 버퍼 크기는 64바이트여야 하고 SHA384의 출력 버퍼 크기는 48바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-836">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-837">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-837">Parameters</span></span>

- <span data-ttu-id="c7269-838">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-838">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-839">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-839">Valid operation is:</span></span>
  - <span data-ttu-id="c7269-840">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c7269-840">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c7269-841">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-841">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c7269-842">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-842">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c7269-843">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-843">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-844">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-844">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-845">**method** 유효한 HMAC SHA512 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-845">**method** Pointer to the valid HMAC SHA512 crypto method.</span></span> <span data-ttu-id="c7269-846">여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_hmac_sha512_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-846">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha512_init().*</span></span>
- <span data-ttu-id="c7269-847">**key** 키를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-847">**key** Points to the key.</span></span> <span data-ttu-id="c7269-848">키 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-848">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="c7269-849">**key_size_in_bits** 키의 크기(비트)</span><span class="sxs-lookup"><span data-stu-id="c7269-849">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="c7269-850">**input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-850">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c7269-851">입력 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-851">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c7269-852">**input_data_size** 입력 데이터의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-852">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c7269-853">**iv_ptr** HMAC SHA512에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-853">**iv_ptr** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="c7269-854">**iv_size** HMAC SHA512에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-854">**iv_size** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="c7269-855">**output_buffer** 생성된 HMAC SHA512 해시의 메모리 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-855">**output_buffer** Pointer to the memory area for the generated HMAC SHA512 hash.</span></span>
- <span data-ttu-id="c7269-856">**output_buffer_size** 출력 버퍼의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-856">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="c7269-857">**crypto_metadata** *_nx_crypto_method_hmac_sha512_init()* 에 사용되는 HMAC SHA512 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-857">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>
- <span data-ttu-id="c7269-858">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-858">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-859">HMAC SHA512의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA512_HMAC)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-859">For HMAC SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>
- <span data-ttu-id="c7269-860">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-860">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-861">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-861">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-862">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-862">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-863">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-863">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-864">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-864">Return Values</span></span>

- <span data-ttu-id="c7269-865">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA512 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-865">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA512 operation.</span></span>
- <span data-ttu-id="c7269-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-867">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-867">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 HMAC SHA512 알고리즘이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="c7269-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a><span data-ttu-id="c7269-870">_nx_crypto_method_hmac_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-870">_nx_crypto_method_hmac_sha512_cleanup</span></span>

<span data-ttu-id="c7269-871">HMAC SHA512 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-871">Clean up the HMAC SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-872">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-872">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-873">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-873">Description</span></span>

<span data-ttu-id="c7269-874">애플리케이션에서는 이 HMAC SHA512 세션이 더 이상 필요 없다고 확인되면 HMAC SHA512 제어 블록을 정리하기 위해 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-874">Application calls this function to clean up the HMAC SHA512 control block after it determines this HMAC SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-875">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-875">Parameters</span></span>

- <span data-ttu-id="c7269-876">**crypto_metadata** *_nx_crypto_method_hmac_sha512_init()* 에 사용되는 HMAC SHA512 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-876">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-877">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-877">Return Values</span></span>

- <span data-ttu-id="c7269-878">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA512 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-878">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA512 session.</span></span>
- <span data-ttu-id="c7269-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

### <a name="example"></a><span data-ttu-id="c7269-880">예제</span><span class="sxs-lookup"><span data-stu-id="c7269-880">Example</span></span> 

## <a name="_nx_crypto_method_md5_init"></a><span data-ttu-id="c7269-881">_nx_crypto_method_md5_init</span><span class="sxs-lookup"><span data-stu-id="c7269-881">_nx_crypto_method_md5_init</span></span>

<span data-ttu-id="c7269-882">MD5 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-882">Initializes the MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-883">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-883">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-884">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-884">Description</span></span>

<span data-ttu-id="c7269-885">이 함수는 제공된 키 문자열을 사용하여 MD5 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-885">This function initializes the MD5 control block with the given key string.</span></span> <span data-ttu-id="c7269-886">MD5 제어 블록이 초기화되면 후속 MD5 작업에서 동일한 제어 블록이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-886">Once the MD5 control block is initialized, subsequent MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="c7269-887">애플리케이션에서는 각각 세션을 나타내는 여러 MD5 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-887">Application may create multiple MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-888">MD5 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-888">Initializing the MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="c7269-889">MD5 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-889">Re-initializing the MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-890">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-890">Parameters</span></span>

- <span data-ttu-id="c7269-891">**method** 유효한 MD5 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-891">**method** Pointer to a valid MD5 crypto method control block.</span></span> <span data-ttu-id="c7269-892">다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-892">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-893">*crypto_method_md5*</span><span class="sxs-lookup"><span data-stu-id="c7269-893">*crypto_method_md5*</span></span>
- <span data-ttu-id="c7269-894">**key** MD5에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-894">**key** This field is not used for MD5.</span></span>
- <span data-ttu-id="c7269-895">**key_size_in_bits** MD5에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-895">**key_size_in_bits** This field is not used for MD5</span></span>
- <span data-ttu-id="c7269-896">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-896">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-897">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-897">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-898">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-898">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-899">**crypto_metadata** MD5 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-899">**crypto_metadata** Pointer to a valid memory space for the MD5 control block.</span></span> <span data-ttu-id="c7269-900">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-900">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-901">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-901">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-902">MD5의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_MD5)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-902">For MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-903">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-903">Return Values</span></span>

- <span data-ttu-id="c7269-904">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 MD5 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-904">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-906">**NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-906">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

### <a name="example"></a><span data-ttu-id="c7269-907">예제</span><span class="sxs-lookup"><span data-stu-id="c7269-907">Example</span></span>

## <a name="_nx_crypto_method_md5_operation"></a><span data-ttu-id="c7269-908">_nx_crypto_method_md5_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-908">_nx_crypto_method_md5_operation</span></span>

<span data-ttu-id="c7269-909">MD5 해시 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-909">Perform an MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-910">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-910">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c7269-911">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-911">Description</span></span>

<span data-ttu-id="c7269-912">이 함수는 MD5 해시 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-912">This function performs MD5 hash operation.</span></span> <span data-ttu-id="c7269-913">MD5 제어 블록은 _ *nx_crypto_method_md5_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-913">The MD5 control block must have been initialized with _ *nx_crypto_method_md5_init()*.</span></span> <span data-ttu-id="c7269-914">수행할 MD5 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-914">The MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-915">최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 출력 버퍼 크기가 16바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-915">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="c7269-916">이 작업은 상태 정보를 유지하지 않으며, MD5 제어 블록의 키 자료를 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-916">This operation does not keep state information and does not alter the key material in the MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-917">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-917">Parameters</span></span>

- <span data-ttu-id="c7269-918">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-918">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-919">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-919">Valid operation is:</span></span>
  - <span data-ttu-id="c7269-920">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c7269-920">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c7269-921">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-921">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c7269-922">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-922">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c7269-923">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-923">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-924">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-924">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-925">**method** 유효한 MD5 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-925">**method** Pointer to the valid MD5 crypto method.</span></span> <span data-ttu-id="c7269-926">여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_md5_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-926">The crypto method used here must be the same used in the _ *nx_crypto_method_md5_init().*</span></span>
- <span data-ttu-id="c7269-927">**input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-927">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c7269-928">입력 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-928">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c7269-929">**input_data_size** 입력 데이터의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-929">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c7269-930">**iv_ptr** MD5에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-930">**iv_ptr** This field is not used for MD5.</span></span>
- <span data-ttu-id="c7269-931">**iv_size** MD5에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-931">**iv_size** This field is not used for MD5.</span></span>
- <span data-ttu-id="c7269-932">**output_buffer** 생성된 MD5 해시의 메모리 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-932">**output_buffer** Pointer to the memory area for the generated MD5 hash.</span></span>
- <span data-ttu-id="c7269-933">**output_buffer_size** 출력 버퍼의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-933">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c7269-934">MD5의 경우 버퍼 크기는 16바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-934">For MD5 the buffer size must be 16 bytes.</span></span>
- <span data-ttu-id="c7269-935">**crypto_metadata** *_nx_crypto_method_md5_init()* 에 사용되는 MD5 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-935">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>
- <span data-ttu-id="c7269-936">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-936">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-937">MD5의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_MD5)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-937">For MD5, the metadata size must *sizeof(NX_CRYPTO_MD5)*</span></span>
- <span data-ttu-id="c7269-938">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-938">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-939">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-939">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-940">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-940">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-941">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-941">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-942">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-942">Return Values</span></span>

- <span data-ttu-id="c7269-943">**NX_CRYPTO_SUCCESS** (0x00) MD5 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-943">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the MD5 operation.</span></span>
- <span data-ttu-id="c7269-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-945">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-945">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 MD5 알고리즘이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid MD5 algorithm being specified.</span></span>
- <span data-ttu-id="c7269-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_md5_cleanup"></a><span data-ttu-id="c7269-948">_nx_crypto_method_md5_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-948">_nx_crypto_method_md5_cleanup</span></span>

<span data-ttu-id="c7269-949">MD5 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-949">Clean up the MD5 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-950">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-950">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-951">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-951">Description</span></span>

<span data-ttu-id="c7269-952">애플리케이션에서는 이 MD5 세션이 더 이상 필요 없다고 확인되면 MD5 제어 블록을 정리하기 위해 이 함수를 호출합니다</span><span class="sxs-lookup"><span data-stu-id="c7269-952">Application calls this function to clean up the MD5 control block after it determines this MD5 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-953">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-953">Parameters</span></span>

- <span data-ttu-id="c7269-954">**crypto_metadata** *_nx_crypto_method_md5_init()* 에 사용되는 MD5 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-954">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-955">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-955">Return Values</span></span>

- <span data-ttu-id="c7269-956">**NX_CRYPTO_SUCCESS** (0x00) MD5 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-956">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the MD5 session.</span></span>
- <span data-ttu-id="c7269-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha1_init"></a><span data-ttu-id="c7269-958">_nx_crypto_method_sha1_init</span><span class="sxs-lookup"><span data-stu-id="c7269-958">_nx_crypto_method_sha1_init</span></span>

<span data-ttu-id="c7269-959">SHA1 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-959">Initializes the SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-960">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-960">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-961">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-961">Description</span></span>

<span data-ttu-id="c7269-962">이 함수는 제공된 키 문자열을 사용하여 SHA1 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-962">This function initializes the SHA1 control block with the given key string.</span></span> <span data-ttu-id="c7269-963">SHA1 제어 블록이 초기화되면 후속 SHA1 작업에서 동일한 제어 블록이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-963">Once the SHA1 control block is initialized, subsequent SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="c7269-964">애플리케이션에서는 각각 세션을 나타내는 여러 SHA1 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-964">Application may create multiple SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-965">SHA1 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-965">Initializing the SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="c7269-966">SHA1 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-966">Re-initializing the SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-967">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-967">Parameters</span></span>

- <span data-ttu-id="c7269-968">**method** 유효한 SHA1 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-968">**method** Pointer to a valid SHA1 crypto method control block.</span></span> <span data-ttu-id="c7269-969">다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-969">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-970">*crypto_method_sha1*</span><span class="sxs-lookup"><span data-stu-id="c7269-970">*crypto_method_sha1*</span></span>
- <span data-ttu-id="c7269-971">**key** SHA1에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-971">**key** This field is not used for SHA1.</span></span>
- <span data-ttu-id="c7269-972">**key_size_in_bits** SHA1에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-972">**key_size_in_bits** This field is not used for SHA1</span></span>
- <span data-ttu-id="c7269-973">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-973">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-974">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-974">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-975">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-975">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-976">**crypto_metadata** SHA1 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-976">**crypto_metadata** Pointer to a valid memory space for the SHA1 control block.</span></span> <span data-ttu-id="c7269-977">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-977">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-978">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-978">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-979">SHA1의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA1)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-979">For SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-980">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-980">Return Values</span></span>

- <span data-ttu-id="c7269-981">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 SHA1 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-981">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-983">**NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-983">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha1_operation"></a><span data-ttu-id="c7269-984">_nx_crypto_method_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-984">_nx_crypto_method_sha1_operation</span></span>

<span data-ttu-id="c7269-985">SHA1 해시 작업 수행</span><span class="sxs-lookup"><span data-stu-id="c7269-985">Perform SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-986">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-986">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c7269-987">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-987">Description</span></span>

<span data-ttu-id="c7269-988">이 함수는 SHA1 해시 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-988">This function performs SHA1 hash operation.</span></span> <span data-ttu-id="c7269-989">SHA1 제어 블록은 _ *nx_crypto_method_sha1_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-989">The SHA1 control block must have been initialized with _ *nx_crypto_method_sha1_init()*.</span></span> <span data-ttu-id="c7269-990">수행할 SHA1 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-990">The SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-991">최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 출력 버퍼 크기가 20바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-991">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-992">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-992">Parameters</span></span>

- <span data-ttu-id="c7269-993">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-993">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-994">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-994">Valid operation is:</span></span>
  - <span data-ttu-id="c7269-995">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c7269-995">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c7269-996">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-996">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c7269-997">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-997">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c7269-998">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-998">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-999">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-999">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-1000">**method** 유효한 SHA1 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-1000">**method** Pointer to the valid SHA1 crypto method.</span></span> <span data-ttu-id="c7269-1001">여기서 사용하는 암호화 메서드를 *nx_crypto_method_sha1_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1001">The crypto method used here must be the same used in the *nx_crypto_method_sha1_init().*</span></span>
- <span data-ttu-id="c7269-1002">**input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1002">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c7269-1003">입력 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1003">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c7269-1004">**input_data_size** 입력 데이터의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-1004">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c7269-1005">**iv_ptr** SHA1에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1005">**iv_ptr** This field is not used for SHA1.</span></span>
- <span data-ttu-id="c7269-1006">**iv_size** SHA1에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1006">**iv_size** This field is not used for SHA1.</span></span>
- <span data-ttu-id="c7269-1007">**output_buffer** 생성된 SHA1 해시의 메모리 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-1007">**output_buffer** Pointer to the memory area for the generated SHA1 hash.</span></span>
- <span data-ttu-id="c7269-1008">**output_buffer_size** 출력 버퍼의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-1008">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c7269-1009">SHA1의 경우 버퍼 크기는 20바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1009">For SHA1 the buffer size must be 20 bytes.</span></span>
- <span data-ttu-id="c7269-1010">**crypto_metadata** *_nx_crypto_method_sha1_init()* 에 사용되는 SHA1 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-1010">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>
- <span data-ttu-id="c7269-1011">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-1011">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-1012">SHA1의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA1)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1012">For SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1)*</span></span>
- <span data-ttu-id="c7269-1013">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1013">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-1014">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1014">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-1015">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1015">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-1016">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1016">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-1017">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-1017">Return Values</span></span>

- <span data-ttu-id="c7269-1018">**NX_CRYPTO_SUCCESS** (0x00) SHA1 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1018">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA1 operation.</span></span>
- <span data-ttu-id="c7269-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-1020">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1020">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 SHA1 알고리즘이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="c7269-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

### <a name="example"></a><span data-ttu-id="c7269-1023">예제</span><span class="sxs-lookup"><span data-stu-id="c7269-1023">Example</span></span>

## <a name="_nx_crypto_method_sha1_cleanup"></a><span data-ttu-id="c7269-1024">_nx_crypto_method_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-1024">_nx_crypto_method_sha1_cleanup</span></span>

<span data-ttu-id="c7269-1025">SHA1 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1025">Clean up the SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-1026">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-1026">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-1027">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-1027">Description</span></span>

<span data-ttu-id="c7269-1028">애플리케이션에서는 이 SHA1 세션이 더 이상 필요 없다고 확인되면 SHA1 제어 블록을 정리하기 위해 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1028">Application calls this function to clean up the SHA1 control block after it determines this SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-1029">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-1029">Parameters</span></span>

- <span data-ttu-id="c7269-1030">**crypto_metadata** *_nx_crypto_method_sha1_init()* 에 사용되는 SHA1 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-1030">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-1031">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-1031">Return Values</span></span>

- <span data-ttu-id="c7269-1032">**NX_CRYPTO_SUCCESS** (0x00) SHA1 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1032">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA1 session.</span></span>
- <span data-ttu-id="c7269-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha256_init"></a><span data-ttu-id="c7269-1034">_nx_crypto_method_sha256_init</span><span class="sxs-lookup"><span data-stu-id="c7269-1034">_nx_crypto_method_sha256_init</span></span>

<span data-ttu-id="c7269-1035">SHA256 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-1035">Initializes the SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-1036">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-1036">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a><span data-ttu-id="c7269-1037">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-1037">Description</span></span>

<span data-ttu-id="c7269-1038">이 함수는 제공된 키 문자열을 사용하여 SHA256 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1038">This function initializes the SHA256 control block with the given key string.</span></span> <span data-ttu-id="c7269-1039">SHA256 제어 블록이 초기화되면 후속 SHA256 작업에서 동일한 제어 블록이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1039">Once the SHA256 control block is initialized, subsequent SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="c7269-1040">애플리케이션에서는 각각 세션을 나타내는 여러 SHA256 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1040">Application may create multiple SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-1041">SHA256 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1041">Initializing the SHA256 control block starts a new hash computation session.</span></span> <span data-ttu-id="c7269-1042">SHA256 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1042">Re-initializing the SHA256 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-1043">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-1043">Parameters</span></span>

- <span data-ttu-id="c7269-1044">**method** 유효한 SHA256 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-1044">**method** Pointer to a valid SHA256 crypto method control block.</span></span> <span data-ttu-id="c7269-1045">다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1045">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-1046">*crypto_method_sha256*</span><span class="sxs-lookup"><span data-stu-id="c7269-1046">*crypto_method_sha256*</span></span>
  - <span data-ttu-id="c7269-1047">*crypto_method_sha224*</span><span class="sxs-lookup"><span data-stu-id="c7269-1047">*crypto_method_sha224*</span></span>
- <span data-ttu-id="c7269-1048">**key** SHA256에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1048">**key** This field is not used for SHA256.</span></span>
- <span data-ttu-id="c7269-1049">**key_size_in_bits** SHA256에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1049">**key_size_in_bits** This field is not used for SHA256</span></span>
- <span data-ttu-id="c7269-1050">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1050">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-1051">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1051">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-1052">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1052">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-1053">**crypto_metadata** SHA256 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-1053">**crypto_metadata** Pointer to a valid memory space for the SHA256 control block.</span></span> <span data-ttu-id="c7269-1054">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1054">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-1055">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-1055">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-1056">SHA256의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA256)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1056">For SHA256, the metadata size must be *sizeof(NX_CRYPTO_SHA256)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-1057">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-1057">Return Values</span></span>

- <span data-ttu-id="c7269-1058">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 SHA256 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1058">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-1060">**NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1060">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha256_operation"></a><span data-ttu-id="c7269-1061">_nx_crypto_method_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-1061">_nx_crypto_method_sha256_operation</span></span>

<span data-ttu-id="c7269-1062">SHA256 해시 작업 수행</span><span class="sxs-lookup"><span data-stu-id="c7269-1062">Perform SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-1063">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-1063">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="c7269-1064">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-1064">Description</span></span>

<span data-ttu-id="c7269-1065">이 함수는 SHA256 해시 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1065">This function performs SHA256 hash operation.</span></span> <span data-ttu-id="c7269-1066">SHA256 제어 블록은 _ ***nx_crypto_method_sha256_init()*** 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1066">The SHA256 control block must have been initialized with _ ***nx_crypto_method_sha256_init()***.</span></span> <span data-ttu-id="c7269-1067">수행할 SHA256 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1067">The SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-1068">최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 SHA256의 출력 버퍼 크기는 32바이트여야 하고 SHA224의 출력 버퍼 크기는 28바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1068">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-1069">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-1069">Parameters</span></span>

- <span data-ttu-id="c7269-1070">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-1070">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-1071">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1071">Valid operation is:</span></span>
  - <span data-ttu-id="c7269-1072">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c7269-1072">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c7269-1073">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-1073">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c7269-1074">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-1074">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c7269-1075">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1075">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-1076">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1076">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-1077">**method** 유효한 SHA256 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-1077">**method** Pointer to the valid SHA256 crypto method.</span></span> <span data-ttu-id="c7269-1078">여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_sha256_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1078">The crypto method used here must be the same used in the _ *nx_crypto_method_sha256_init().*</span></span>
- <span data-ttu-id="c7269-1079">**input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1079">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c7269-1080">입력 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1080">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c7269-1081">**input_data_size** 입력 데이터의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-1081">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c7269-1082">**iv_ptr** SHA256에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1082">**iv_ptr** This field is not used for SHA256.</span></span>
- <span data-ttu-id="c7269-1083">**iv_size** SHA256에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1083">**iv_size** This field is not used for SHA256.</span></span>
- <span data-ttu-id="c7269-1084">**output_buffer** 생성된 SHA256 해시의 메모리 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-1084">**output_buffer** Pointer to the memory area for the generated SHA256 hash.</span></span>
- <span data-ttu-id="c7269-1085">**output_buffer_size** 출력 버퍼의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-1085">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c7269-1086">SHA256의 경우 버퍼 크기는 32바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1086">For SHA256 the buffer size must be 32 bytes.</span></span> <span data-ttu-id="c7269-1087">SHA224의 경우 버퍼 크기는 28바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1087">For SHA224 the buffer size must be 28 bytes.</span></span>
- <span data-ttu-id="c7269-1088">**crypto_metadata** *_nx_crypto_method_sha2_init()* 에 사용되는 SHA2 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-1088">**crypto_metadata** Pointer to the SHA2 control block used in *_nx_crypto_method_sha2_init()*.</span></span>
- <span data-ttu-id="c7269-1089">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-1089">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-1090">SHA256의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA256)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1090">For SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256)*</span></span>
- <span data-ttu-id="c7269-1091">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1091">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-1092">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1092">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-1093">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1093">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-1094">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1094">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-1095">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-1095">Return Values</span></span>

- <span data-ttu-id="c7269-1096">**NX_CRYPTO_SUCCESS** (0x00) SHA256 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1096">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA256 operation.</span></span>
- <span data-ttu-id="c7269-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-1098">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1098">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 SHA256 알고리즘이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="c7269-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha256_cleanup"></a><span data-ttu-id="c7269-1101">_nx_crypto_method_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-1101">_nx_crypto_method_sha256_cleanup</span></span>

<span data-ttu-id="c7269-1102">SHA256 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1102">Clean up the SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-1103">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-1103">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-1104">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-1104">Description</span></span>

<span data-ttu-id="c7269-1105">애플리케이션에서는 이 SHA256 세션이 더 이상 필요 없다고 확인되면 SHA256 제어 블록을 정리하기 위해 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1105">Application calls this function to clean up the SHA256 control block after it determines this SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-1106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-1106">Parameters</span></span>

- <span data-ttu-id="c7269-1107">**crypto_metadata** *_nx_crypto_method_sha256_init()* 에 사용되는 SHA256 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-1107">**crypto_metadata** Pointer to the SHA256 control block used in *_nx_crypto_method_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-1108">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-1108">Return Values</span></span>

- <span data-ttu-id="c7269-1109">**NX_CRYPTO_SUCCESS** (0x00) SHA256 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1109">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA256 session.</span></span>
- <span data-ttu-id="c7269-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha512_init"></a><span data-ttu-id="c7269-1111">_nx_crypto_method_sha512_init</span><span class="sxs-lookup"><span data-stu-id="c7269-1111">_nx_crypto_method_sha512_init</span></span>

<span data-ttu-id="c7269-1112">SHA512 암호화 제어 블록을 초기화</span><span class="sxs-lookup"><span data-stu-id="c7269-1112">Initializes the SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-1113">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-1113">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="c7269-1114">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-1114">Description</span></span>

<span data-ttu-id="c7269-1115">이 함수는 제공된 키 문자열을 사용하여 SHA512 제어 블록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1115">This function initializes the SHA512 control block with the given key string.</span></span> <span data-ttu-id="c7269-1116">SHA512 제어 블록이 초기화되면 후속 SHA512 작업에서 동일한 제어 블록이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1116">Once the SHA512 control block is initialized, subsequent SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="c7269-1117">애플리케이션에서는 각각 세션을 나타내는 여러 SHA512 제어 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1117">Application may create multiple SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="c7269-1118">SHA512 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1118">Initializing the SHA512 control block starts a new hash computation session.</span></span> <span data-ttu-id="c7269-1119">SHA512 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1119">Re-initializing the SHA512 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-1120">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-1120">Parameters</span></span>

- <span data-ttu-id="c7269-1121">**method** 유효한 SHA512 암호화 메서드 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-1121">**method** Pointer to a valid SHA512 crypto method control block.</span></span> <span data-ttu-id="c7269-1122">다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1122">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="c7269-1123">*crypto_method_sha512*</span><span class="sxs-lookup"><span data-stu-id="c7269-1123">*crypto_method_sha512*</span></span>
  - <span data-ttu-id="c7269-1124">*crypto_method_sha384*</span><span class="sxs-lookup"><span data-stu-id="c7269-1124">*crypto_method_sha384*</span></span>
- <span data-ttu-id="c7269-1125">**key** SHA512에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1125">**key** This field is not used for SHA512.</span></span>
- <span data-ttu-id="c7269-1126">**key_size_in_bits** SHA512에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1126">**key_size_in_bits** This field is not used for SHA512</span></span>
- <span data-ttu-id="c7269-1127">**handle** 이 서비스는 호출자에게 핸들을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1127">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="c7269-1128">핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1128">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="c7269-1129">애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1129">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="c7269-1130">**crypto_metadata** SHA512 제어 블록의 유효한 메모리 공간에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-1130">**crypto_metadata** Pointer to a valid memory space for the SHA512 control block.</span></span> <span data-ttu-id="c7269-1131">메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1131">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="c7269-1132">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-1132">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-1133">SHA512의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA512)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1133">For SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512)*</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-1134">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-1134">Return Values</span></span>

- <span data-ttu-id="c7269-1135">**NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 SHA512 제어 블록을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1135">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="c7269-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-1137">**NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1137">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha512_operation"></a><span data-ttu-id="c7269-1138">_nx_crypto_method_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="c7269-1138">_nx_crypto_method_sha512_operation</span></span>

<span data-ttu-id="c7269-1139">SHA512 해시 작업 수행</span><span class="sxs-lookup"><span data-stu-id="c7269-1139">Perform SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-1140">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-1140">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a><span data-ttu-id="c7269-1141">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-1141">Description</span></span>

<span data-ttu-id="c7269-1142">이 함수는 SHA512 해시 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1142">This function performs SHA512 hash operation.</span></span> <span data-ttu-id="c7269-1143">SHA512 제어 블록은 _ *nx_crypto_method_sha512_init()* 를 사용하여 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1143">The SHA512 control block must have been initialized with _ *nx_crypto_method_sha512_init()*.</span></span> <span data-ttu-id="c7269-1144">수행할 SHA512 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1144">The SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="c7269-1145">최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 SHA512의 출력 버퍼 크기는 64바이트여야 하고 SHA384의 출력 버퍼 크기는 48바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1145">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-1146">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-1146">Parameters</span></span>

- <span data-ttu-id="c7269-1147">**op** 수행할 작업의 유형.</span><span class="sxs-lookup"><span data-stu-id="c7269-1147">**op** Type of operation to perform.</span></span> <span data-ttu-id="c7269-1148">유효한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1148">Valid operation is:</span></span>
  - <span data-ttu-id="c7269-1149">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="c7269-1149">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="c7269-1150">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-1150">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="c7269-1151">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="c7269-1151">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="c7269-1152">**handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1152">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-1153">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1153">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-1154">**method** 유효한 SHA512 암호화 메서드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="c7269-1154">**method** Pointer to the valid SHA512 crypto method.</span></span> <span data-ttu-id="c7269-1155">여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_sha512_init()* 에서도 동일하게 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1155">The crypto method used here must be the same used in the _ *nx_crypto_method_sha512_init().*</span></span>
- <span data-ttu-id="c7269-1156">**input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1156">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="c7269-1157">입력 버퍼에 대한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1157">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="c7269-1158">**input_data_size** 입력 데이터의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="c7269-1158">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="c7269-1159">**iv_ptr** SHA512에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1159">**iv_ptr** This field is not used for SHA512.</span></span>
- <span data-ttu-id="c7269-1160">**iv_size** SHA512에는 이 필드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1160">**iv_size** This field is not used for SHA512.</span></span>
- <span data-ttu-id="c7269-1161">**output_buffer** 생성된 SHA512 해시의 메모리 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-1161">**output_buffer** Pointer to the memory area for the generated SHA512 hash.</span></span>
- <span data-ttu-id="c7269-1162">**output_buffer_size** 출력 버퍼의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-1162">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="c7269-1163">SHA512의 경우 버퍼 크기는 64바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1163">For SHA512 the buffer size must be 64 bytes.</span></span> <span data-ttu-id="c7269-1164">SHA384의 경우 버퍼 크기는 48바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1164">For SHA384 the buffer size must be 48 bytes.</span></span>
- <span data-ttu-id="c7269-1165">**crypto_metadata** *_nx_crypto_method_sha512_init()* 에 사용되는 SHA512 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-1165">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>
- <span data-ttu-id="c7269-1166">**crypto_metadata_size** crypto_metadata 영역의 크기(바이트).</span><span class="sxs-lookup"><span data-stu-id="c7269-1166">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="c7269-1167">SHA512의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA512)* 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1167">For SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512)*</span></span>
- <span data-ttu-id="c7269-1168">**packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1168">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-1169">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1169">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="c7269-1170">**nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1170">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="c7269-1171">전달된 모든 값은 자동으로 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1171">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-1172">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-1172">Return Values</span></span>

- <span data-ttu-id="c7269-1173">**NX_CRYPTO_SUCCESS** (0x00) SHA512 작업을 성공적으로 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1173">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA512 operation.</span></span>
- <span data-ttu-id="c7269-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="c7269-1175">**NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1175">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="c7269-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 SHA512 알고리즘이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="c7269-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha512_cleanup"></a><span data-ttu-id="c7269-1178">_nx_crypto_method_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="c7269-1178">_nx_crypto_method_sha512_cleanup</span></span>

<span data-ttu-id="c7269-1179">SHA512 제어 블록을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1179">Clean up the SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="c7269-1180">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c7269-1180">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="c7269-1181">Description</span><span class="sxs-lookup"><span data-stu-id="c7269-1181">Description</span></span>

<span data-ttu-id="c7269-1182">애플리케이션에서는 이 SHA512 세션이 더 이상 필요 없다고 확인되면 SHA512 제어 블록을 정리하기 위해 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1182">Application calls this function to clean up the SHA512 control block after it determines this SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c7269-1183">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7269-1183">Parameters</span></span>

- <span data-ttu-id="c7269-1184">**crypto_metadata** *_nx_crypto_method_sha512_init()* 에 사용되는 SHA512 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="c7269-1184">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="c7269-1185">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7269-1185">Return Values</span></span>

- <span data-ttu-id="c7269-1186">**NX_CRYPTO_SUCCESS** (0x00) SHA512 세션이 정리되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1186">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA512 session.</span></span>
- <span data-ttu-id="c7269-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7269-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>