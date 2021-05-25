---
title: 2장 - Azure RTOS NetX Crypto 설치 및 사용
description: 이 장에서는 NetX Crypto 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd736cf6bbe15e1f407d1812072a4308435c8007
ms.sourcegitcommit: c2f5da5d6c7b230799f8fbd77885e9940acfbab4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2021
ms.locfileid: "110236155"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a>2장 - Azure RTOS NetX Crypto 설치 및 사용

이 장에서는 Azure RTOS NetX Crypto 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS NetX Crypto는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 사용할 수 있습니다. 패키지에는 다음과 같이 이 문서를 포함하는 원본 파일, 포함 파일 및 PDF 파일이 포함되어 있습니다.

- **nx_crypto.h**: 공용 API 헤더 파일 NetX Crypto 모듈
- **nx_crypto_*.c/h**: NetX Crypto에 대한 C/H 원본 파일
- **nx_crypto_port.h**: 모든 개발 도구 및 대상 특정 데이터 정의 및 구조를 포함하는 C 헤더 파일
- **NetX_Crypto_User_Guide.pdf**: NetX Crypto 모듈의 PDF 설명

## <a name="netx-crypto-installation"></a>NetX Crypto 설치

이전에 언급한 전체 배포는 NetX Duo 리포지토리의 루트 수준에 있는 **crypto_libraries** 디렉터리에서 사용할 수 있습니다.

NetX Crypto를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리 수준에 복사해야 합니다. 예를 들어 NetX가 "\threadx\arm7\NetX" 디렉터리에 설치된 경우 nx_crypto입니다 *.* 디렉터리를 "\threadx\arm7\NetXCrypto"로 복사해야 합니다.

NetX Crypto를 독립 실행형 모드에서 사용하려면 이전에 언급한 전체 배포를 애플리케이션 프로젝트에 복사해야 합니다. 예를 들어 **crypto_libraries** 디렉터리를 애플리케이션 프로젝트에 복사하거나 **crypto_libraries** 디렉터리가 있는 라이브러리 프로젝트를 만들고 애플리케이션 프로젝트에 연결해야 합니다. 

## <a name="using-netx-crypto"></a>NetX Crypto 사용

이 챕터에서는 Azure RTOS NetX Crypto 구성 요소의 설치, 설정 및 사용법을 설명합니다. 기본적으로 애플리케이션 코드는 *nx_crypto.h* 를 포함해야 합니다.  *nx_crypto.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 NetX Crypto 함수 호출을 수행할 수 있습니다.

## <a name="configuration-options"></a>구성 옵션

NetX Crypto를 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음은 각각에 대해 자세히 설명된 모든 옵션의 목록입니다.

- **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: 정의된 경우 이 옵션은 예상되는 최대 RSA 모듈러스(비트)를 제공합니다. 4096비트 모듈러스의 기본값은 4096입니다. 다른 값은 3072, 2048 또는 1024(권장하지 않음)일 수 있습니다.
- **NX_CRYPTO_SELF_TEST**: 정의되면 NetX Crypto 모듈에 대한 자체 테스트를 사용할 수 있습니다. 이제 **NX_CRYPTO_FIPS** 기호가 더 이상 사용되지 않으며 이름이 **NX_CRYPTO_SELF_TEST** 로 변경되었습니다.
- **NX_CRYPTO_STANDALONE_ENABLE**: 정의 된 경우 NetX Crypto는 독립 실행형 모드(Azure RTOS 제외)에서 사용할 수 있습니다. 기본적으로 이 기호는 정의되어 있지 않습니다.
