---
title: Azure RTOS USBX 디바이스 스택 사용자 가이드
description: 이 가이드에서는 Microsoft의 고성능 USB 기반 소프트웨어인 Azure RTOS USBX에 대한 포괄적인 정보를 제공합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: c8e9360c8b72adbc41f840a48e333668c489399e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810243"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a><span data-ttu-id="64022-103">Azure RTOS USBX 디바이스 스택 사용자 가이드</span><span class="sxs-lookup"><span data-stu-id="64022-103">Azure RTOS USBX Device Stack User Guide</span></span>

<span data-ttu-id="64022-104">이 가이드에서는 Microsoft의 고성능 USB 기반 소프트웨어인 Azure RTOS USBX에 대한 포괄적인 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64022-104">This guide provides comprehensive information about Azure RTOS USBX, the high performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="64022-105">임베디드 실시간 소프트웨어 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="64022-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="64022-106">개발자는 표준 실시간 운영 체제 함수, USB 사양 및 C 프로그래밍 언어에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64022-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="64022-107">USB와 관련된 기술 정보는 https://www.USB.org/developers 에서 다운로드할 수 있는 USB 사양 및 USB 클래스 사양을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="64022-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at https://www.USB.org/developers</span></span>

## <a name="organization"></a><span data-ttu-id="64022-108">조직</span><span class="sxs-lookup"><span data-stu-id="64022-108">Organization</span></span>

- <span data-ttu-id="64022-109">[**1장**](usbx-device-stack-1.md) - Azure RTOS USBX에 대한 소개가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64022-109">[**Chapter 1**](usbx-device-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="64022-110">[**2장**](usbx-device-stack-2.md) - ThreadX 애플리케이션에서 Azure RTOS USBX를 설치하고 사용하기 위한 기본 단계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64022-110">[**Chapter 2**](usbx-device-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your ThreadX application</span></span>

- <span data-ttu-id="64022-111">[**3장**](usbx-device-stack-3.md) - Azure RTOS USBX 디바이스 스택의 기능 구성 요소를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="64022-111">[**Chapter 3**](usbx-device-stack-3.md) - describes the functional components of the Azure RTOS USBX device stack</span></span>

- <span data-ttu-id="64022-112">[**4장**](usbx-device-stack-4.md) - Azure RTOS USBX 디바이스 스택 서비스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="64022-112">[**Chapter 4**](usbx-device-stack-4.md) - describes the Azure RTOS USBX device stack services</span></span>

- <span data-ttu-id="64022-113">[**5장**](usbx-device-stack-5.md) - API를 포함하여 각 Azure RTOS USBX 디바이스 클래스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="64022-113">[**Chapter 5**](usbx-device-stack-5.md) - describes each Azure RTOS USBX device class including their APIs</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="64022-114">고객 지원 센터</span><span class="sxs-lookup"><span data-stu-id="64022-114">Customer Support Center</span></span>

<span data-ttu-id="64022-115">다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요.</span><span class="sxs-lookup"><span data-stu-id="64022-115">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="64022-116">지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.</span><span class="sxs-lookup"><span data-stu-id="64022-116">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="64022-117">발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="64022-117">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="64022-118">문제가 발생하기 전의 애플리케이션 및/또는 Azure RTOS ThreadX의 변경 내용에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="64022-118">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="64022-119">배포의 **_tx_port.h_** 파일에 있는 **_tx_version_id** 문자열의 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="64022-119">The contents of the **_tx_version_id** string found in the **_tx_port.h_** file of your distribution.</span></span> <span data-ttu-id="64022-120">이 문자열은 런타임 환경에 대한 유용한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64022-120">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="64022-121">*_tx_build_options* **ULONG** 변수의 RAM에 있는 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="64022-121">The contents in RAM of the *_tx_build_options* **ULONG** variable.</span></span> <span data-ttu-id="64022-122">이 변수는 Azure RTOS ThreadX 라이브러리가 빌드되는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64022-122">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
