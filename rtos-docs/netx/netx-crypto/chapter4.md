---
title: 챕터 4 - Azure RTOS NetX Crypto API 설명
description: Azure RTOS NetX Crypto API 설명
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5bd4cdae28a293ec9ef259bbd29fdb8f8d6dc43f964cbc184290b82ee8f590a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788805"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a>챕터 4 - Azure RTOS NetX Crypto API 설명

## <a name="nx_crypto_initialize"></a>nx_crypto_initialize

NetX Secure 라이브러리 초기화

### <a name="prototype"></a>프로토타입

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a>Description

이 함수는 Azure RTOS NetX Crypto 라이브러리 모듈을 초기화합니다. 다른 암호화 함수를 사용하기 전에 애플리케이션에서 이 함수를 호출하여 초기화를 수행하고 라이브러리의 무결성을 확인해야 합니다. 다른 NetX Crypto 서비스를 사용하기 전에 이 함수를 호출하지 못하면 오류가 반환됩니다.

### <a name="parameters"></a>매개 변수

- **없음**

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) NetX Crypto 라이브러리를 성공적으로 초기화했습니다. 이제 라이브러리 함수가 준비되었으며 사용할 수 있습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 초기화되지 않거나 무결성 검사에 실패합니다. 애플리케이션에서 이 라이브러리를 사용할 수 없습니다.

### <a name="example"></a>예제

TODO

## <a name="nx_crypto_module_state_get"></a>nx_crypto_module_state_get

FIPS 사용 모듈의 현재 상태를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a>Description

이 서비스는 FIPS 빌드 라이브러리에서만 사용할 수 있습니다. NetX Crypto 라이브러리의 현재 상태 상태를 반환합니다.

### <a name="parameters"></a>매개 변수

- **없음**

### <a name="return-values"></a>반환 값

- **상태 플래그:**
  - NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001
  - NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002
  - NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004
  - NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008
  - NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000
- **다른 모든 값이 올바르지 않습니다.**

### <a name="example"></a>예제

TODO

## <a name="_nx_crypto_method_aes_init"></a>_nx_crypto_method_aes_init

AES 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 AES 제어 블록을 초기화합니다. AES 제어 블록이 초기화되면 후속 AES 작업에서 동일한 키 및 키 크기를 사용합니다.

애플리케이션에서는 각각 세션을 나타내는 여러 AES 제어 블록을 만들 수 있습니다. 키는 제어 블록에 할당됩니다. 후속 암호화 또는 암호 해독 작업에서는 AES 제어 블록을 다시 초기화할 필요 없이 동일한 AES 제어 블록을 참조할 수 있습니다. 세션의 키가 변경되면 애플리케이션에서는 업데이트된 키를 사용하여 AES 제어 블록을 다시 초기화해야 합니다.

_ *nx_crypto_method_aes_init()* 를 호출하면 이전에 구성된 키와 키 크기가 새 키로 자동 업데이트됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 AES 암호화 메서드 제어 블록에 대한 포인터. 다음과 같은 미리 정의된 AES 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_aes_cbc_128*
  - *crypto_method_aes_cbc_192*
  - *crypto_method_aes_cbc_256*
  - *crypto_method_aes_ctr_128*
  - *crypto_method_aes_ctr_192*
  - *crypto_method_aes_ctr_256*
  - *crypto_method_aes_xcbc_128*
  - *crypto_method_aes_ccm_8_128*
- **key** AES 키가 포함된 버퍼를 가리킵니다.
- **key_size_in_bits** 키의 크기(비트) 유효한 값은 다음과 같습니다.
  - *NX_CRYPTO_AES_KEY_SIZE_128_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_192_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_256_BITS*
  - **다른 모든 값이 올바르지 않습니다.**
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** AES 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). AES의 경우 메타데이터 크기가 *sizeof(NX_AES)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 AES 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR (0x07)** 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) 키 크기가 AES에 적합하지 않습니다.

## <a name="_nx_crypto_method_aes_operation"></a>_nx_crypto_method_aes_operation

AES 작업(암호화 또는 암호 해독)을 수행합니다.

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 AES 암호화 또는 암호 해독 작업을 수행합니다. AES 제어 블록은 _ *nx_crypto_method_aes_init()* 를 사용하여 초기화해야 합니다. 수행할 AES 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

입력 버퍼 크기는 16바이트의 배수여야 합니다. 암호 해독된 데이터의 크기는 입력 데이터 크기와 동일합니다. 암호화된 데이터가 AES 블록 크기의 짝수 배수가 되도록 패딩된 경우 패딩이 출력 버퍼에 포함되며 애플리케이션에서 패딩을 처리해야 합니다.

이 작업은 상태 정보를 유지하지 않으며, AES 제어 블록의 키 자료를 변경하지 않습니다.

op가 NX_CRYPTO_SET_ADDITIONAL_DATA이고 알고리즘이 AES-CCM8이면 입력은 추가 데이터를 가리키고 input_length_in_byte는 추가 데이터의 길이입니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
  - *NX_CRYPTO_AUTHENTICATE(AES-XCBC만 해당)*
  - *NX_CRYPTO_SET_ADDITIONAL_DATA(AES-CCM8만 해당)*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 AES 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 *nx_crypto_method_aes_init()* 에서도 동일하게 사용해야 합니다.
- **input_data** 암호화된 텍스트 데이터가 포함된 버퍼를 가리킵니다. 입력 버퍼에 대한 제한은 없습니다.
- **input_data_size** 입력 데이터의 크기(바이트). 입력 데이터 크기는 16바이트의 배수여야 합니다.
- **iv_ptr** 초기 벡터에 대한 포인터. IV 버퍼 대한 제한은 없습니다.
- **iv_size** 초기 벡터 블록의 크기(바이트). 이 필드는 16이어야 합니다.
- **output_buffer** 일반 텍스트 데이터를 저장하는 AES의 메모리 영역에 대한 포인터. 애플리케이션에서 출력 버퍼에 사용할 공간을 할당해야 합니다. 출력 버퍼가 입력 버퍼와 겹칠 수 있습니다. 출력 버퍼와 입력 버퍼가 동일한 시작 주소를 공유하는 경우에는 출력 버퍼가 입력 버퍼와 겹칠 수 있습니다.
- **output_buffer_size** 출력 버퍼의 크기(바이트). 출력 버퍼 크기는 적어도 입력 버퍼 크기와 동일해야 하며, 출력 버퍼 크기는 16바이트의 배수여야 합니다.
- **crypto_metadata** *_nx_crypto_method_aes_init()\*에 사용되는 AES 제어 블록에 대한 포인터.\**
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). AES의 경우 메타데이터 크기가 *sizeof(NX_AES)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) AES 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 AES 알고리즘이 지정되었습니다**.

## <a name="_nx_crypto_method_aes_cleanup"></a>_nx_crypto_method_aes_cleanup

AES 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 AES 세션이 더 이상 필요 없다고 확인되면 AES 제어 블록을 정리하기 위해 이 함수를 호출합니다

### <a name="parameters"></a>매개 변수

- **crypto_metadata** *_nx_crypto_method_aes_init()\*에 사용되는 AES 제어 블록에 대한 포인터.\**

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) AES 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.

## <a name="_nx_crypto_method_3des_init"></a>_nx_crypto_method_3des_init

3DES 제어 블록을 초기화합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 3개의 키 문자열로 3DES(Triple DES) 제어 블록을 초기화합니다. 키 문자열은 각각 8바이트여야 합니다. 3개의 DES 키는 24바이트 버퍼의 연속 메모리에 연결되어야 합니다. FIPS 규격 빌드의 경우 세 키가 서로 달라야 합니다. 그렇지 않으면 함수에서 NX_CRYPTO_INVALID_KEY 오류를 반환합니다. 3DES 제어 블록이 초기화되면 후속 3DES 작업에서 동일한 키가 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 3DES 제어 블록을 만들 수 있습니다. 키는 제어 블록에 할당되며, 후속 암호화 또는 해독 작업에서는 다시 초기화할 필요 없이 동일한 제어 블록을 참조할 수 있습니다. 세션의 키가 변경되면 애플리케이션에서는 업데이트된 키를 사용하여 제어 블록을 다시 초기화해야 합니다.

_ *nx_crypto_method_3des_init()* 를 호출하면 이전에 구성된 키가 새 키로 자동 업데이트됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 3DES 암호화 메서드 제어 블록에 대한 포인터. 미리 정의된 3DES 암호화 메서드 ***crypto_method_3des*** 를 사용할 수 있습니다.
- **key** 3개의 DES 키가 포함된 버퍼를 가리킵니다.
- **key_size_in_bits** 192여야 합니다(키 3개, 각각 64비트).
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 초기화 중인 3DES 제어 블록을 식별합니다. 후속 3DES 작업(암호화, 암호 해독 및 정리)에서는 이 핸들을 사용하여 3DES 제어 블록에 액세스합니다.
- **crypto_metadata** 3DES 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). 3DES의 경우 메타데이터 크기가 *sizeof(NX_3DES)* 여야 합니다.

### <a name="return-value"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 3DES 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR (0x07)** 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) 키 크기가 3DES에 적합하지 않습니다.

## <a name="_nx_crypto_method_3des_operation"></a>_nx_crypto_method_3des_operation

3DES로 암호화하거나 암호를 해독합니다.

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 3DES 암호화 또는 암호 해독 작업을 수행합니다. 3DES 제어 블록은 _ *nx_crypto_method_3des_init()* 를 사용하여 초기화해야 합니다. 수행할 3DES 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

입력 버퍼 크기는 8바이트의 배수여야 합니다. 암호 해독된 데이터의 크기는 입력 데이터 크기와 동일합니다. 암호화된 데이터가 3DES 블록 크기의 짝수 배수가 되도록 패딩된 경우 패딩이 출력 버퍼에 포함되며 애플리케이션에서 패딩을 처리해야 합니다.

이 작업은 상태 정보를 유지하지 않으며, 3DES 제어 블록의 키 자료를 변경하지 않습니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
- **handle** *_nx_crypto_method_3des_init()* 를 통해 초기화된 핸들입니다.
- **method** 유효한 3DES 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 *nx_crypto_method_3des_init()* 에서도 동일하게 사용해야 합니다.
- **input_data** 암호화된 텍스트 데이터가 포함된 버퍼를 가리킵니다.
입력 버퍼에 대한 제한은 없습니다.
- **input_data_size** 입력 데이터의 크기(바이트). 입력 데이터 크기는 8바이트의 배수여야 합니다.
- **iv_ptr** 초기 벡터에 대한 포인터. IV 버퍼 대한 제한은 없습니다.
- **iv_size** 초기 벡터 블록의 크기(바이트)입니다. 이 필드는 8이어야 합니다.
- **output_buffer** 일반 텍스트 데이터를 저장하는 3DES의 메모리 영역에 대한 포인터. 애플리케이션에서 출력 버퍼에 사용할 공간을 할당해야 합니다. 출력 버퍼가 입력 버퍼와 겹칠 수 있습니다. 출력 버퍼와 입력 버퍼가 동일한 시작 주소를 공유하는 경우에는 출력 버퍼가 입력 버퍼와 겹칠 수 있습니다.
- **output_buffer_size** 출력 버퍼의 크기(바이트). 출력 버퍼 크기는 적어도 입력 버퍼 크기와 동일해야 하며, 출력 버퍼 크기는 8바이트의 배수여야 합니다.
- **crypto_metadata** *_nx_crypto_method_3des_init()* 에 사용되는 3DES 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). 3DES의 경우 메타데이터 크기가 *sizeof(NX_3DES)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="description"></a>Description

이 함수는 3DES 암호화를 수행합니다. 3DES 제어 블록은 _ *nx_crypto_moethod_3des_init()* 를 사용하여 초기화해야 합니다. 이 작업은 상태 정보를 유지하지 않으며, 3DES 제어 블록의 키 자료를 변경하지 않습니다. 이 함수는 패딩을 추가하지 않으므로 호출자는 패딩을 처리한 후 암호화 작업을 호출해야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 3DES 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR (0x07)** 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

## <a name="_nx_crypto_method_3des_cleanup"></a>_nx_crypto_method_3des_cleanup

3DES 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 3DES 세션이 더 이상 필요 없다고 확인되면 3DES 제어 블록을 정리하기 위해 이 함수를 호출합니다.

### <a name="parameters"></a>매개 변수

- **handle** *_nx_crypto_method_3des_init()* 를 통해 초기화된 핸들입니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 3DES 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.

## <a name="_nx_crypto_method_drbg_init"></a>_nx_crypto_method_drbg_init

DRBG 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 DRBG 제어 블록을 초기화합니다. DRBG 제어 블록이 초기화되면 후속 DRBG 작업에서 동일한 제어 블록이 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 DRBG 제어 블록을 만들 수 있습니다. DRBG 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다. DRBG 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 DRBG 암호화 메서드 제어 블록에 대한 포인터. 다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_drbg*
- **key** DRBG에는 이 필드가 사용되지 않습니다.
- **key_size_in_bits** DRBG에는 이 필드가 사용되지 않습니다.
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** DRBG 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). DRBG의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_DRBG)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 DRBG 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

## <a name="_nx_crypto_method_drbg_operation"></a>_nx_crypto_method_drbg_operation

DRBG 작업 수행

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 DRBG 작업을 수행합니다. DRBG 제어 블록은 _ *nx_crypto_method_drbg_init()* 를 사용하여 초기화해야 합니다. 수행할 DRBG 알고리즘은 *메서드* 제어 블록에 지정된 알고리즘을 기반으로 합니다. 기본적으로 DRBG에는 AES-128이 사용됩니다.

작업이 NX_CRYPTO_DRBG_OPTIONS_SET이면 입력은 NX_CRYPTO_DRBG_OPTIONS 구조를 가리킵니다. 작업이 NX_CRYPTO_DRBG_INSTANTIATE이면 키는 nonce를 가리키고 입력은 개인 설정 문자열을 가리킵니다. 작업이 NX_CRYPTO_DRBG_RESEED 또는 NX_CRYPTO_DRBG_GENERATE이면 입력은 추가 입력을 가리킵니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_DRBG_OPTIONS_SET*
  - *NX_CRYPTO_DRBG_INSTANTIATE*
  - *NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 DRBG 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_drbg_init()* 에서도 동일하게 사용해야 합니다.
- **key** 인스턴스화 작업의 nonce에 대한 포인터. 이 필드는 다른 작업에는 사용되지 않습니다.
- **key_size_in_bits** nonce의 크기(비트). 이 필드는 다른 작업에는 사용되지 않습니다.
- **input** op가 NX_CRYPTO_DRBG_OPTIONS_SET이면 이 필드는 DRBG 옵션을 가리킵니다. op가 NX_CRYPTO_DRBG_INSTANTIATE이면 이 필드는 개인 설정 문자열을 가리킵니다. op가 NX_CRYPTO_DRBG_RESEED 또는 NX_CRYPTO_DRBG_GENERATE이면 이 필드는 추가 입력 데이터를 가리킵니다.
- **input_length_in_byte** 입력 데이터의 크기(바이트)
- **iv_ptr** DRBG에는 이 필드가 사용되지 않습니다.
- **output** op가 NX_CRYPTO_DRBG_GENERATE이면 이 필드는 생성된 DRBG의 메모리 영역을 가리킵니다. 그렇지 않으면 이 필드는 사용되지 않습니다.
- **output_length_in_byte** 출력 버퍼의 크기(바이트)
- **crypto_metadata** *_nx_crypto_method_aes_init()* 에 사용되는 DRBG 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). DRBG의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_DRBG)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) DRBG 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 DRBG 알고리즘이 지정되었습니다.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.

## <a name="_nx_crypto_method_drbg_cleanup"></a>_nx_crypto_method_drbg_cleanup

DRBG 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 DRBG 세션이 더 이상 필요 없다고 확인되면 DRBG 제어 블록을 정리하기 위해 이 함수를 호출합니다.

### <a name="parameters"></a>매개 변수

- **crypto_metadata** *_nx_crypto_method_aes_init()* 에 사용되는 DRBG 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) DRBG 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.

## <a name="_nx_crypto_method_ecdh_init"></a>_nx_crypto_method_ecdh_init

ECDH 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 ECDH 제어 블록을 초기화합니다. ECDH 제어 블록이 초기화되면 후속 ECDH 작업에서 동일한 제어 블록이 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 ECDH 제어 블록을 만들 수 있습니다. ECDH 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다. ECDH 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 ECDH 암호화 메서드 제어 블록에 대한 포인터. 다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_ecdh*
- **key** ECDH에는 이 필드가 사용되지 않습니다.
- **key_size_in_bits** ECDH에는 이 필드가 사용되지 않습니다.
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** ECDH 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). ECDH의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_ECDH)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 ECDH 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

## <a name="_nx_crypto_method_ecdh_operation"></a>_nx_crypto_method_ecdh_operation

ECDH 작업 수행

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 ECDH 작업을 수행합니다. ECDH 제어 블록은 _ *nx_crypto_method_ecdh_init()* 를 사용하여 초기화해야 합니다. 수행할 ECDH 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

작업이 NX_CRYPTO_EC_CURVE_SET이면 입력은 Elliptic Curve 암호화 메서드를 가리킵니다. 작업이 NX_CRYPTO_EC_KEY_PAIR_GENERATE이면 출력은 NX_CRYPTO_EXTENDED_OUTPUT 구조를 가리키고 키 쌍이 nx_crypto_extended_output_data에 복사됩니다. 작업이 NX_CRYPTO_DH_SETUP이면 공개 키가 nx_crypto_extended_output_data에 반환됩니다. 작업이 NX_CRYPTO_DH_KEY_PAIR_IMPORT이면 입력은 공개 키를 가리키고 키는 프라이빗 키를 가리킵니다. 작업이 NX_CRYPTO_DH_PRIVATE_KEY_EXPORT이면 프라이빗 키가 nx_crypto_extended_output_data에 복사됩니다. 작업이 NX_CRYPTO_DH_CALCULATE이면 입력은 원격 공개 키를 가리키고 공유 비밀이 nx_crypto_extended_output_data에 복사됩니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_DH_SETUP*
  - *NX_CRYPTO_DH_CALCULATE*
  - *NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*
  - *NX_CRYPTO_DH_KEY_PAIR_GENERATE*
  - *NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 ECDH 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_ecdh_init()* 에서도 동일하게 사용해야 합니다.
- **key** op가 NX_CRYPTO_DH_IMPORT_KEY_PAIR이면 이 필드는 프라이빗 키를 가리킵니다. 그렇지 않으면 이 필드는 ECDH에 사용되지 않습니다.
- **key_size_in_bits** 키의 크기(비트)
- **input** op가 NX_CRYPTO_EC_CURVE_SET이면 이 필드는 Elliptic Curve 암호화 메서드를 가리킵니다. op가 NX_CRYPTO_DH_SETUP이면 이 필드는 사용되지 않습니다. op가 NX_CRYPTO_DH_CALCULATE이면 이 필드는 입력 텍스트 데이터를 포함하는 버퍼를 가리킵니다. op가 NX_CRYPTO_DH_IMPORT_KEY_PAIR이면 이 필드는 공개 키를 가리킵니다.
- **input_length_in_byte** 입력 데이터의 크기(바이트)
- **iv_ptr** ECDH에는 이 필드가 사용되지 않습니다.
- **output** op가 NX_CRYPTO_EC_CURVE_SET 또는 NX_CRYPTO_DH_IMPORT_KEY_PAIR이면 이 필드는 사용되지 않습니다. op가 NX_CRYPTO_DH_SETUP이면 이 필드는 생성된 ECDH 공개 키의 메모리 영역을 가리킵니다. op가 NX_CRYPTO_DH_CALCULATE이면 이 필드는 생성된 ECDH 공유 비밀의 메모리 영역을 가리킵니다.
- **output_length_in_byte** 출력 버퍼의 크기(바이트)
- **crypto_metadata** *_nx_crypto_method_ecdh_init()* 에 사용되는 ECDH 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). ECDH의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_ECDH)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) ECDH 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 ECDH 알고리즘이 지정되었습니다.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.

## <a name="_nx_crypto_method_ecdh_cleanup"></a>_nx_crypto_method_ecdh_cleanup

ECDH 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 ECDH 세션이 더 이상 필요 없다고 확인되면 ECDH 제어 블록을 정리하기 위해 이 함수를 호출합니다.

### <a name="parameters"></a>매개 변수

- **crypto_metadata** *_nx_crypto_method_ecdh_init()* 에 사용되는 ECDH 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) ECDH 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.

## <a name="_nx_crypto_method_ecdsa_init"></a>_nx_crypto_method_ecdsa_init

ECDSA 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 ECDSA 제어 블록을 초기화합니다. ECDSA 제어 블록이 초기화되면 후속 ECDSA 작업에서 동일한 제어 블록이 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 ECDSA 제어 블록을 만들 수 있습니다. ECDSA 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다. ECDSA 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 ECDSA 암호화 메서드 제어 블록에 대한 포인터. 다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_ecdsa*
- **key** ECDSA에는 이 필드가 사용되지 않습니다.
- **key_size_in_bits** ECDSA에는 이 필드가 사용되지 않습니다.
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** ECDSA 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). ECDSA의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_ECDSA)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 ECDSA 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

## <a name="_nx_crypto_method_ecdsa_operation"></a>_nx_crypto_method_ecdsa_operation

ECDSA 작업 수행

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 ECDSA 작업을 수행합니다. ECDSA 제어 블록은 _ *nx_crypto_method_ecdsa_init()* 를 사용하여 초기화해야 합니다. 수행할 ECDSA 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

작업이 NX_CRYPTO_EC_CURVE_SET이면 입력은 Elliptic Curve 암호화 메서드를 가리킵니다. 작업이 NX_CRYPTO_EC_KEY_PAIR_GENERATE이면 출력은 NX_CRYPTO_EXTENDED_OUTPUT 구조를 가리키고 키 쌍이 nx_crypto_extended_output_data에 복사됩니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_AUTHENTICATE*
  - *NX_CRYPTO_VERIFY*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 ECDSA 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_ecdsa_init()* 에서도 동일하게 사용해야 합니다.
- **key** op가 NX_CRYPTO_VERIFY이면 이 필드는 키를 가리킵니다. 키 버퍼에 대한 제한은 없습니다. 이 필드는 다른 op 값에는 사용되지 않습니다.
- **key_size_in_bits** 키의 크기(비트)
- **input** op가 NX_CRYPTO_EC_CURVE_SET이면 이 필드는 Elliptic Curve 암호화 메서드를 가리킵니다. 그렇지 않으면 이 필드는 입력 텍스트 데이터를 포함하는 버퍼를 가리킵니다.
- **input_length_in_byte** 입력 데이터의 크기(바이트)
- **iv_ptr** ECDSA에는 이 필드가 사용되지 않습니다.
- **output** op가 NX_CRYPTO_EC_CURVE_SET이면 이 필드는 사용되지 않습니다. op가 NX_CRYPTO_AUTHENTICATE이면 이 필드는 생성된 ECDSA 서명의 메모리 영역을 가리킵니다. op가 NX_CRYPTO_VERIFY이면 이 필드는 확인된 ECDSA 서명의 메모리 영역을 가리킵니다.
- **output_length_in_byte** 출력 버퍼의 크기(바이트)
- **crypto_metadata** *_nx_crypto_method_ecdsa_init()* 에 사용되는 ECDSA 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). ECDSA의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_ECDSA)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) ECDSA 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 ECDSA 알고리즘이 지정되었습니다.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.

## <a name="_nx_crypto_method_ecdsa_cleanup"></a>_nx_crypto_method_ecdsa_cleanup

ECDSA 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 ECDSA 세션이 더 이상 필요 없다고 확인되면 ECDSA 제어 블록을 정리하기 위해 이 함수를 호출합니다.

### <a name="parameters"></a>매개 변수

- **crypto_metadata** *_nx_crypto_method_ecdsa_init()* 에 사용되는 ECDSA 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) ECDSA 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.

## <a name="_nx_crypto_method_hmac_md5_init"></a>_nx_crypto_method_hmac_md5_init

HMAC MD5 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 HMAC MD5 제어 블록을 초기화합니다. HMAC MD5 제어 블록이 초기화되면 후속 HMAC MD5 작업에서 동일한 제어 블록이 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 HMAC MD5 제어 블록을 만들 수 있습니다. HMAC MD5 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다. HMAC MD5 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 HMAC MD5 암호화 메서드 제어 블록에 대한 포인터.
다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_hmac_md5*
- **key** 키를 가리킵니다. 키 버퍼에 대한 제한은 없습니다.
- **key_size_in_bits** 키의 크기(비트)
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** HMAC MD5 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). HMAC MD5의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_MD5_HMAC)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 HMAC MD5 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

## <a name="_nx_crypto_method_hmac_md5_operation"></a>_nx_crypto_method_hmac_md5_operation

HMAC MD5 해시 작업을 수행합니다.

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 HMAC MD5 해시 작업을 수행합니다. HMAC MD5 제어 블록은 _ *nx_crypto_method_hmac_md5_init()* 를 사용하여 초기화해야 합니다. 수행할 HMAC MD5 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 출력 버퍼 크기가 16바이트여야 합니다.

이 작업은 상태 정보를 유지하지 않으며, HMAC MD5 제어 블록의 키 자료를 변경하지 않습니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 HMAC MD5 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 *nx_crypto_method_hmac_md5_init()* 에서도 동일하게 사용해야 합니다.
- **key** 키를 가리킵니다. 키 버퍼에 대한 제한은 없습니다.
- **key_size_in_bits** 키의 크기(비트)
- **input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다. 입력 버퍼에 대한 제한은 없습니다.
- **input_data_size** 입력 데이터의 크기(바이트)
- **iv_ptr** HMAC MD5에는 이 필드가 사용되지 않습니다.
- **iv_size** HMAC MD5에는 이 필드가 사용되지 않습니다.
- **output_buffer** 생성된 HMAC MD5 해시의 메모리 영역에 대한 포인터
- **output_buffer_size** 출력 버퍼의 크기(바이트)
- **crypto_metadata** *_nx_crypto_method_hmac_md5_init()* 에 사용되는 HMAC MD5 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). HMAC MD5의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_MD5_HMAC)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) HMAC MD5 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 HMAC MD5 알고리즘이 지정되었습니다.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.

## <a name="_nx_crypto_method_hmac_sha1_init"></a>_nx_crypto_method_hmac_sha1_init

HMAC SHA1 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 HMAC SHA1 제어 블록을 초기화합니다. HMAC SHA1 제어 블록이 초기화되면 후속 HMAC SHA1 작업에서 동일한 제어 블록이 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 HMAC SHA1 제어 블록을 만들 수 있습니다. HMAC SHA1 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다. HMAC SHA1 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 HMAC SHA1 암호화 메서드 제어 블록에 대한 포인터. 다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_hmac_sha1*
- **key** 키를 가리킵니다. 키 버퍼에 대한 제한은 없습니다.
- **key_size_in_bits** 키의 크기(비트)
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** HMAC SHA1 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). HMAC SHA1의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA1_HMAC)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 HMAC SHA1 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

## <a name="_nx_crypto_method_hmac_sha1_operation"></a>_nx_crypto_method_hmac_sha1_operation

HMAC SHA1 해시 작업 수행

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 HMAC SHA1 해시 작업을 수행합니다. HMAC SHA1 제어 블록은 _ *nx_crypto_method_hmac_sha1_init()* 를 사용하여 초기화해야 합니다. 수행할 HMAC SHA1 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 출력 버퍼 크기가 20바이트여야 합니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 HMAC SHA1 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_hmac_sha1_init()* 에서도 동일하게 사용해야 합니다.
- **key** 키를 가리킵니다. 키 버퍼에 대한 제한은 없습니다.
- **key_size_in_bits** 키의 크기(비트)
- **input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다. 입력 버퍼에 대한 제한은 없습니다.
- **input_data_size** 입력 데이터의 크기(바이트)
- **iv_ptr** HMAC SHA1에는 이 필드가 사용되지 않습니다.
- **iv_size** HMAC SHA1에는 이 필드가 사용되지 않습니다.
- **output_buffer** 생성된 HMAC SHA1 해시의 메모리 영역에 대한 포인터
- **output_buffer_size** 출력 버퍼의 크기(바이트)
- **crypto_metadata** *_nx_crypto_method_hmac_sha1_init()* 에 사용되는 HMAC SHA1 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). HMAC SHA1의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA1_HMAC)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA1 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 HMAC SHA1 알고리즘이 지정되었습니다.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a>_nx_crypto_method_hmac_sha1_cleanup

HMAC SHA1 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 HMAC SHA1 세션이 더 이상 필요 없다고 확인되면 HMAC SHA1 제어 블록을 정리하기 위해 이 함수를 호출합니다.

### <a name="parameters"></a>매개 변수

- **crypto_metadata** *_nx_crypto_method_hmac_sha1_init()* 에 사용되는 HMAC SHA1 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA1 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.

## <a name="_nx_crypto_method_hmac_sha256_init"></a>_nx_crypto_method_hmac_sha256_init

HMAC SHA256 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 HMAC SHA256 제어 블록을 초기화합니다. HMAC SHA256 제어 블록이 초기화되면 후속 HMAC SHA256 작업에서 동일한 제어 블록이 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 HMAC SHA256 제어 블록을 만들 수 있습니다. HMAC SH256 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다. HMAC SHA256 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 키를 사용하여 새 세션이 시작됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 HMAC SHA256 암호화 메서드 제어 블록에 대한 포인터. 다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_hmac_sha224*
  - *crypto_method_hmac_sha256*
- **key** 키를 가리킵니다. 키 버퍼에 대한 제한은 없습니다.
- **key_size_in_bits** 키의 크기(비트)
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** HMAC SHA256 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). HMAC SHA256의 경우 메타데이터 크기가 *sizeof(NX_CRYTPO_SHA256_HMAC)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 HMAC SHA256 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

## <a name="_nx_crypto_method_hmac_sha256_operation"></a>_nx_crypto_method_hmac_sha256_operation

HMAC SHA256 해시 작업 수행

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 HMAC SHA256 해시 작업을 수행합니다. HMAC SHA256 제어 블록은 _ *nx_crypto_method_hmac_sha256_init()* 를 사용하여 초기화해야 합니다. 수행할 HMAC SHA256 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 SHA256의 출력 버퍼 크기는 32바이트여야 하고 SHA224의 출력 버퍼 크기는 28바이트여야 합니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 HMAC SHA256 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_hmac_sha256_init()* 에서도 동일하게 사용해야 합니다.
- **key** 키를 가리킵니다. 키 버퍼에 대한 제한은 없습니다.
- **key_size_in_bits** 키의 크기(비트)
- **input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다. 입력 버퍼에 대한 제한은 없습니다.
- **input_data_size** 입력 데이터의 크기(바이트)
- **iv_ptr** HMAC SHA256에는 이 필드가 사용되지 않습니다.
- **iv_size** HMAC SHA256에는 이 필드가 사용되지 않습니다.
- **output_buffer** 생성된 HMAC SHA256 해시의 메모리 영역에 대한 포인터
- **output_buffer_size** 출력 버퍼의 크기(바이트)
- **crypto_metadata** *_nx_crypto_method_hmac_sha256_init()* 에 사용되는 HMAC SHA256 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). HMAC SHA256의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA256_HMAC)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA256 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 HMAC SHA256 알고리즘이 지정되었습니다.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a>_nx_crypto_method_hmac_sha256_cleanup

HMAC SHA256 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 HMAC SHA256 세션이 더 이상 필요 없다고 확인되면 HMAC SHA256 제어 블록을 정리하기 위해 이 함수를 호출합니다.

### <a name="parameters"></a>매개 변수

- **crypto_metadata** *_nx_crypto_method_hmac_sha256_init()* 에 사용되는 HMAC SHA256 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA256 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.

## <a name="_nx_crypto_method_hmac_sha512_init"></a>_nx_crypto_method_hmac_sha512_init

HMAC SHA512 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 HMAC SHA512 제어 블록을 초기화합니다. HMAC SHA512 제어 블록이 초기화되면 후속 HMAC SHA512 작업에서 동일한 제어 블록이 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 HMAC SHA512 제어 블록을 만들 수 있습니다. HMAC SH512 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다. HMAC SHA512 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 키를 사용하여 새 세션이 시작됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 HMAC SHA512 암호화 메서드 제어 블록에 대한 포인터. 다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_hmac_sha384*
  - *crypto_method_hmac_sha512*
- **key** 키를 가리킵니다. 키 버퍼에 대한 제한은 없습니다.
- **key_size_in_bits** 키의 크기(비트)
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** HMAC SHA512 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). HMAC SHA512의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA512_HMAC)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 HMAC SHA512 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

## <a name="_nx_crypto_method_hmac_sha512_operation"></a>_nx_crypto_method_hmac_sha512_operation

HMAC SHA512 해시 작업 수행

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 HMAC SHA512 해시 작업을 수행합니다. HMAC SHA512 제어 블록은 _ *nx_crypto_method_hmac_sha512_init()* 를 사용하여 초기화해야 합니다. 수행할 HMAC SHA512 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 SHA512의 출력 버퍼 크기는 64바이트여야 하고 SHA384의 출력 버퍼 크기는 48바이트여야 합니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 HMAC SHA512 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_hmac_sha512_init()* 에서도 동일하게 사용해야 합니다.
- **key** 키를 가리킵니다. 키 버퍼에 대한 제한은 없습니다.
- **key_size_in_bits** 키의 크기(비트)
- **input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다. 입력 버퍼에 대한 제한은 없습니다.
- **input_data_size** 입력 데이터의 크기(바이트)
- **iv_ptr** HMAC SHA512에는 이 필드가 사용되지 않습니다.
- **iv_size** HMAC SHA512에는 이 필드가 사용되지 않습니다.
- **output_buffer** 생성된 HMAC SHA512 해시의 메모리 영역에 대한 포인터
- **output_buffer_size** 출력 버퍼의 크기(바이트)
- **crypto_metadata** *_nx_crypto_method_hmac_sha512_init()* 에 사용되는 HMAC SHA512 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). HMAC SHA512의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA512_HMAC)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA512 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 HMAC SHA512 알고리즘이 지정되었습니다.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a>_nx_crypto_method_hmac_sha512_cleanup

HMAC SHA512 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 HMAC SHA512 세션이 더 이상 필요 없다고 확인되면 HMAC SHA512 제어 블록을 정리하기 위해 이 함수를 호출합니다.

### <a name="parameters"></a>매개 변수

- **crypto_metadata** *_nx_crypto_method_hmac_sha512_init()* 에 사용되는 HMAC SHA512 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA512 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.

### <a name="example"></a>예제 

## <a name="_nx_crypto_method_md5_init"></a>_nx_crypto_method_md5_init

MD5 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 MD5 제어 블록을 초기화합니다. MD5 제어 블록이 초기화되면 후속 MD5 작업에서 동일한 제어 블록이 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 MD5 제어 블록을 만들 수 있습니다. MD5 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다. MD5 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 MD5 암호화 메서드 제어 블록에 대한 포인터. 다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_md5*
- **key** MD5에는 이 필드가 사용되지 않습니다.
- **key_size_in_bits** MD5에는 이 필드가 사용되지 않습니다.
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** MD5 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). MD5의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_MD5)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 MD5 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

### <a name="example"></a>예제

## <a name="_nx_crypto_method_md5_operation"></a>_nx_crypto_method_md5_operation

MD5 해시 작업을 수행합니다.

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 MD5 해시 작업을 수행합니다. MD5 제어 블록은 _ *nx_crypto_method_md5_init()* 를 사용하여 초기화해야 합니다. 수행할 MD5 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 출력 버퍼 크기가 16바이트여야 합니다.

이 작업은 상태 정보를 유지하지 않으며, MD5 제어 블록의 키 자료를 변경하지 않습니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 MD5 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_md5_init()* 에서도 동일하게 사용해야 합니다.
- **input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다. 입력 버퍼에 대한 제한은 없습니다.
- **input_data_size** 입력 데이터의 크기(바이트)
- **iv_ptr** MD5에는 이 필드가 사용되지 않습니다.
- **iv_size** MD5에는 이 필드가 사용되지 않습니다.
- **output_buffer** 생성된 MD5 해시의 메모리 영역에 대한 포인터
- **output_buffer_size** 출력 버퍼의 크기(바이트). MD5의 경우 버퍼 크기는 16바이트여야 합니다.
- **crypto_metadata** *_nx_crypto_method_md5_init()* 에 사용되는 MD5 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). MD5의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_MD5)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) MD5 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 MD5 알고리즘이 지정되었습니다.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.

## <a name="_nx_crypto_method_md5_cleanup"></a>_nx_crypto_method_md5_cleanup

MD5 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 MD5 세션이 더 이상 필요 없다고 확인되면 MD5 제어 블록을 정리하기 위해 이 함수를 호출합니다

### <a name="parameters"></a>매개 변수

- **crypto_metadata** *_nx_crypto_method_md5_init()* 에 사용되는 MD5 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) MD5 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.

## <a name="_nx_crypto_method_sha1_init"></a>_nx_crypto_method_sha1_init

SHA1 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 SHA1 제어 블록을 초기화합니다. SHA1 제어 블록이 초기화되면 후속 SHA1 작업에서 동일한 제어 블록이 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 SHA1 제어 블록을 만들 수 있습니다. SHA1 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다. SHA1 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 SHA1 암호화 메서드 제어 블록에 대한 포인터. 다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_sha1*
- **key** SHA1에는 이 필드가 사용되지 않습니다.
- **key_size_in_bits** SHA1에는 이 필드가 사용되지 않습니다.
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** SHA1 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). SHA1의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA1)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 SHA1 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

## <a name="_nx_crypto_method_sha1_operation"></a>_nx_crypto_method_sha1_operation

SHA1 해시 작업 수행

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 SHA1 해시 작업을 수행합니다. SHA1 제어 블록은 _ *nx_crypto_method_sha1_init()* 를 사용하여 초기화해야 합니다. 수행할 SHA1 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 출력 버퍼 크기가 20바이트여야 합니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 SHA1 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 *nx_crypto_method_sha1_init()* 에서도 동일하게 사용해야 합니다.
- **input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다. 입력 버퍼에 대한 제한은 없습니다.
- **input_data_size** 입력 데이터의 크기(바이트)
- **iv_ptr** SHA1에는 이 필드가 사용되지 않습니다.
- **iv_size** SHA1에는 이 필드가 사용되지 않습니다.
- **output_buffer** 생성된 SHA1 해시의 메모리 영역에 대한 포인터
- **output_buffer_size** 출력 버퍼의 크기(바이트). SHA1의 경우 버퍼 크기는 20바이트여야 합니다.
- **crypto_metadata** *_nx_crypto_method_sha1_init()* 에 사용되는 SHA1 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). SHA1의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA1)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) SHA1 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 SHA1 알고리즘이 지정되었습니다.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.

### <a name="example"></a>예제

## <a name="_nx_crypto_method_sha1_cleanup"></a>_nx_crypto_method_sha1_cleanup

SHA1 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 SHA1 세션이 더 이상 필요 없다고 확인되면 SHA1 제어 블록을 정리하기 위해 이 함수를 호출합니다.

### <a name="parameters"></a>매개 변수

- **crypto_metadata** *_nx_crypto_method_sha1_init()* 에 사용되는 SHA1 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) SHA1 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.

## <a name="_nx_crypto_method_sha256_init"></a>_nx_crypto_method_sha256_init

SHA256 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 SHA256 제어 블록을 초기화합니다. SHA256 제어 블록이 초기화되면 후속 SHA256 작업에서 동일한 제어 블록이 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 SHA256 제어 블록을 만들 수 있습니다. SHA256 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다. SHA256 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 SHA256 암호화 메서드 제어 블록에 대한 포인터. 다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_sha256*
  - *crypto_method_sha224*
- **key** SHA256에는 이 필드가 사용되지 않습니다.
- **key_size_in_bits** SHA256에는 이 필드가 사용되지 않습니다.
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** SHA256 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). SHA256의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA256)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 SHA256 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

## <a name="_nx_crypto_method_sha256_operation"></a>_nx_crypto_method_sha256_operation

SHA256 해시 작업 수행

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 SHA256 해시 작업을 수행합니다. SHA256 제어 블록은 _ ***nx_crypto_method_sha256_init()*** 를 사용하여 초기화해야 합니다. 수행할 SHA256 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 SHA256의 출력 버퍼 크기는 32바이트여야 하고 SHA224의 출력 버퍼 크기는 28바이트여야 합니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 SHA256 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_sha256_init()* 에서도 동일하게 사용해야 합니다.
- **input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다. 입력 버퍼에 대한 제한은 없습니다.
- **input_data_size** 입력 데이터의 크기(바이트)
- **iv_ptr** SHA256에는 이 필드가 사용되지 않습니다.
- **iv_size** SHA256에는 이 필드가 사용되지 않습니다.
- **output_buffer** 생성된 SHA256 해시의 메모리 영역에 대한 포인터
- **output_buffer_size** 출력 버퍼의 크기(바이트). SHA256의 경우 버퍼 크기는 32바이트여야 합니다. SHA224의 경우 버퍼 크기는 28바이트여야 합니다.
- **crypto_metadata** *_nx_crypto_method_sha2_init()* 에 사용되는 SHA2 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). SHA256의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA256)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) SHA256 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 SHA256 알고리즘이 지정되었습니다.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.

## <a name="_nx_crypto_method_sha256_cleanup"></a>_nx_crypto_method_sha256_cleanup

SHA256 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 SHA256 세션이 더 이상 필요 없다고 확인되면 SHA256 제어 블록을 정리하기 위해 이 함수를 호출합니다.

### <a name="parameters"></a>매개 변수

- **crypto_metadata** *_nx_crypto_method_sha256_init()* 에 사용되는 SHA256 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) SHA256 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.

## <a name="_nx_crypto_method_sha512_init"></a>_nx_crypto_method_sha512_init

SHA512 암호화 제어 블록을 초기화

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

이 함수는 제공된 키 문자열을 사용하여 SHA512 제어 블록을 초기화합니다. SHA512 제어 블록이 초기화되면 후속 SHA512 작업에서 동일한 제어 블록이 사용됩니다.

애플리케이션에서는 각각 세션을 나타내는 여러 SHA512 제어 블록을 만들 수 있습니다. SHA512 제어 블록을 초기화하면 새 해시 계산 세션이 시작됩니다. SHA512 제어 블록을 다시 초기화하면 현재 세션이 중단되고 새 세션이 시작됩니다.

### <a name="parameters"></a>매개 변수

- **method** 유효한 SHA512 암호화 메서드 제어 블록에 대한 포인터. 다음과 같은 미리 정의된 암호화 메서드를 사용할 수 있습니다.
  - *crypto_method_sha512*
  - *crypto_method_sha384*
- **key** SHA512에는 이 필드가 사용되지 않습니다.
- **key_size_in_bits** SHA512에는 이 필드가 사용되지 않습니다.
- **handle** 이 서비스는 호출자에게 핸들을 반환합니다. 핸들은 구현에 따라 다르며, 이 구현에서는 사용되지 않습니다. 애플리케이션에서는 핸들에 대해 NULL을 전달해야 합니다.
- **crypto_metadata** SHA512 제어 블록의 유효한 메모리 공간에 대한 포인터. 메모리 공간의 시작 주소는 4바이트로 맞춰야 합니다.
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). SHA512의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA512)* 여야 합니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) 키와 키 크기를 사용하여 SHA512 제어 블록을 초기화했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 키의 포인터가 올바르지 않거나, crypto_metadata 또는 crypto_metadata_size가 올바르지 않거나, crypto_metadata를 4바이트로 맞추지 않았습니다.

## <a name="_nx_crypto_method_sha512_operation"></a>_nx_crypto_method_sha512_operation

SHA512 해시 작업 수행

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 함수는 SHA512 해시 작업을 수행합니다. SHA512 제어 블록은 _ *nx_crypto_method_sha512_init()* 를 사용하여 초기화해야 합니다. 수행할 SHA512 알고리즘은 *method* 제어 블록에 지정된 알고리즘을 기반으로 합니다.

최종 *NX_CRYPTO_HASH_CALCULATE* 작업의 경우 SHA512의 출력 버퍼 크기는 64바이트여야 하고 SHA384의 출력 버퍼 크기는 48바이트여야 합니다.

### <a name="parameters"></a>매개 변수

- **op** 수행할 작업의 유형. 유효한 작업은 다음과 같습니다.
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **method** 유효한 SHA512 암호화 메서드에 대한 포인터. 여기서 사용하는 암호화 메서드를 _ *nx_crypto_method_sha512_init()* 에서도 동일하게 사용해야 합니다.
- **input_data** 입력 텍스트 데이터가 포함된 버퍼를 가리킵니다. 입력 버퍼에 대한 제한은 없습니다.
- **input_data_size** 입력 데이터의 크기(바이트)
- **iv_ptr** SHA512에는 이 필드가 사용되지 않습니다.
- **iv_size** SHA512에는 이 필드가 사용되지 않습니다.
- **output_buffer** 생성된 SHA512 해시의 메모리 영역에 대한 포인터
- **output_buffer_size** 출력 버퍼의 크기(바이트). SHA512의 경우 버퍼 크기는 64바이트여야 합니다. SHA384의 경우 버퍼 크기는 48바이트여야 합니다.
- **crypto_metadata** *_nx_crypto_method_sha512_init()* 에 사용되는 SHA512 제어 블록에 대한 포인터
- **crypto_metadata_size** crypto_metadata 영역의 크기(바이트). SHA512의 경우 메타데이터 크기가 *sizeof(NX_CRYPTO_SHA512)* 여야 합니다.
- **packet_ptr** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.
- **nx_crypto_hw_process_callback** 이 필드는 NetX Crypto 라이브러리의 소프트웨어 구현에는 사용되지 않습니다. 전달된 모든 값은 자동으로 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) SHA512 작업을 성공적으로 실행했습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.
- **NX_PTR_ERROR** (0x07) 입력 포인터 또는 길이가 올바르지 않습니다.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 잘못된 SHA512 알고리즘이 지정되었습니다.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 출력 버퍼 크기가 올바르지 않습니다.

## <a name="_nx_crypto_method_sha512_cleanup"></a>_nx_crypto_method_sha512_cleanup

SHA512 제어 블록을 정리합니다.

### <a name="prototype"></a>프로토타입

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

애플리케이션에서는 이 SHA512 세션이 더 이상 필요 없다고 확인되면 SHA512 제어 블록을 정리하기 위해 이 함수를 호출합니다.

### <a name="parameters"></a>매개 변수

- **crypto_metadata** *_nx_crypto_method_sha512_init()* 에 사용되는 SHA512 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_CRYPTO_SUCCESS** (0x00) SHA512 세션이 정리되었습니다.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) 암호화 라이브러리가 잘못된 상태이므로 사용할 수 없습니다.