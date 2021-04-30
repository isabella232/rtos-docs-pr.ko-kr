---
title: 2장 - Azure RTOS NetX Crypto 설치 및 사용
description: 이 장에서는 NetX Crypto 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1616667c5efd73229ed69bcd4e5de5f80e5826f9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811634"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a><span data-ttu-id="5e2cb-103">2장 - Azure RTOS NetX Crypto 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="5e2cb-103">Chapter 2 - Installation and use of Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="5e2cb-104">이 장에서는 Azure RTOS NetX Crypto 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="5e2cb-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="5e2cb-105">Product Distribution</span></span>

<span data-ttu-id="5e2cb-106">Azure RTOS NetX Crypto는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-106">Azure RTOS NetX Crypto is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="5e2cb-107">패키지에는 다음과 같이 이 문서를 포함하는 원본 파일, 포함 파일 및 PDF 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="5e2cb-108">**nx_crypto.h**: 공용 API 헤더 파일 NetX Crypto 모듈</span><span class="sxs-lookup"><span data-stu-id="5e2cb-108">**nx_crypto.h**: Public API header file NetX Crypto module</span></span>
- <span data-ttu-id="5e2cb-109">**nx_crypto_\*.c/h**: NetX Crypto에 대한 C/H 원본 파일</span><span class="sxs-lookup"><span data-stu-id="5e2cb-109">**nx_crypto_\*.c/h**: C/H Source files for NetX Crypto</span></span>
- <span data-ttu-id="5e2cb-110">**nx_crypto_port.h**: 모든 개발 도구 및 대상 특정 데이터 정의 및 구조를 포함하는 C 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="5e2cb-110">**nx_crypto_port.h**: C header file containing all development-tool and target specific data definitions and structures.</span></span>
- <span data-ttu-id="5e2cb-111">**NetX_Crypto_User_Guide.pdf**: NetX Crypto 모듈의 PDF 설명</span><span class="sxs-lookup"><span data-stu-id="5e2cb-111">**NetX_Crypto_User_Guide.pdf**: PDF description of NetX Crypto Module.</span></span>

## <a name="netx-crypto-installation"></a><span data-ttu-id="5e2cb-112">NetX Crypto 설치</span><span class="sxs-lookup"><span data-stu-id="5e2cb-112">NetX Crypto Installation</span></span>

<span data-ttu-id="5e2cb-113">이전에 언급한 전체 배포는 NetX Duo 리포지토리의 루트 수준에 있는 **crypto_libraries** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-113">The entire distribution mentioned previously is available in **crypto_libraries** directory, present at root level of NetX Duo repository.</span></span>

<span data-ttu-id="5e2cb-114">NetX Crypto를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리 수준에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-114">In order to use NetX Crypto, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="5e2cb-115">예를 들어 NetX가 "\threadx\arm7\NetX" 디렉터리에 설치된 경우 nx_crypto입니다 *.*</span><span class="sxs-lookup"><span data-stu-id="5e2cb-115">For example, if NetX is installed in the directory "\threadx\arm7\NetX" then the nx_crypto *.*</span></span> <span data-ttu-id="5e2cb-116">디렉터리를 "\threadx\arm7\NetXCrypto"로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-116">directories should be copied into "\threadx\arm7\NetXCrypto".</span></span>

<span data-ttu-id="5e2cb-117">NetX Crypto를 독립 실행형 모드에서 사용하려면 이전에 언급한 전체 배포를 애플리케이션 프로젝트에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-117">For NetX Crypto to be used in standalone mode, the entire distribution mentioned previously should be copied to the application project.</span></span> <span data-ttu-id="5e2cb-118">예를 들어 **crypto_libraries** 디렉터리를 애플리케이션 프로젝트에 복사하거나 **crypto_libraries** 디렉터리가 있는 라이브러리 프로젝트를 만들고 애플리케이션 프로젝트에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-118">For example **crypto_libraries** directory should be copied to the application project or a library project with **crypto_libraries** directory should be created and linked to the application project.</span></span> 

## <a name="using-netx-crypto"></a><span data-ttu-id="5e2cb-119">NetX Crypto 사용</span><span class="sxs-lookup"><span data-stu-id="5e2cb-119">Using NetX Crypto</span></span>

<span data-ttu-id="5e2cb-120">NetX Crypto를 사용하는 것은 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-120">Using NetX Crypto is easy.</span></span> <span data-ttu-id="5e2cb-121">기본적으로 애플리케이션 코드는 *nx_crypto.h* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-121">Basically, the application code must include the *nx_crypto.h*.</span></span>  <span data-ttu-id="5e2cb-122">*nx_crypto.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 NetX Crypto 함수 호출을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-122">Once *nx_crypto.h* is included, the application code is then able to make the NetX Crypto function calls specified later in this guide.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="5e2cb-123">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="5e2cb-123">Configuration Options</span></span>

<span data-ttu-id="5e2cb-124">NetX Crypto를 빌드하기 위한 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-124">There are several configuration options for building NetX Crypto.</span></span> <span data-ttu-id="5e2cb-125">다음은 각각에 대해 자세히 설명된 모든 옵션의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-125">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="5e2cb-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: 정의된 경우 이 옵션은 예상되는 최대 RSA 모듈러스(비트)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="5e2cb-127">4096비트 모듈러스의 기본값은 4096입니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-127">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="5e2cb-128">다른 값은 3072, 2048 또는 1024(권장하지 않음)일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-128">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>
- <span data-ttu-id="5e2cb-129">**NX_CRYPTO_FIPS**: 정의된 경우 이 옵션을 사용하면 FIPS 규격 사용에 필요한 추가 보안 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-129">**NX_CRYPTO_FIPS**: Defined, this option enables extra security features required for FIPS-Compliant usage.</span></span> <span data-ttu-id="5e2cb-130">FIPS가 아닌 빌드에는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-130">This option is not enabled for non-FIPS build.</span></span>
- <span data-ttu-id="5e2cb-131">**NX_CRYPTO_STANDALONE_ENABLE**: 정의 된 경우 NetX Crypto는 독립 실행형 모드(Azure RTOS 제외)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-131">**NX_CRYPTO_STANDALONE_ENABLE**: Defined enables NetX Crypto to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="5e2cb-132">기본적으로 이 기호는 정의되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e2cb-132">By default this symbol is not defined.</span></span>
