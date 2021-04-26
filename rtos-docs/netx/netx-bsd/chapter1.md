---
title: 1장 - Azure RTOS NetX BSD 소개
description: Azure RTOS NetX BSD Sockets API Compliancy Wrapper는 몇 가지 제한 사항이 있는 기본 BSD Sockets API 호출 중 일부를 지원하며, 그 아래에 있는 NetX 기본 요소를 활용합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fce781ac97ae75c4148614453eeb35c3064f8849
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810423"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a><span data-ttu-id="f201d-103">1장 - Azure RTOS NetX BSD 소개</span><span class="sxs-lookup"><span data-stu-id="f201d-103">Chapter 1 - Introduction to Azure RTOS NetX BSD</span></span>

<span data-ttu-id="f201d-104">NetX BSD Sockets API Compliancy Wrapper는 몇 가지 제한 사항이 있는 기본 BSD Sockets API 호출 중 일부를 지원하며, 그 아래에 있는 NetX 기본 요소를 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="f201d-104">The NetX BSD Sockets API Compliancy Wrapper supports some of the basic BSD Sockets API calls with some limitations and utilizes NetX primitives underneath.</span></span> <span data-ttu-id="f201d-105">BSD 소켓 API 호환성 계층은 내부 NetX 기본 형식을 활용하고 기본적인 NetX 오류 검사를 건너뛰므로 이 래퍼는 일반적인 BSD 구현보다 약간 빠르거나 동일한 속도로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f201d-105">This BSD Sockets API compatibility layer should perform as fast or slightly faster than typical BSD implementations, since this Wrapper utilizes internal NetX primitives and bypasses basic NetX error checking.</span></span>

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a><span data-ttu-id="f201d-106">BSD Socket API Compliancy Wrapper 원본</span><span class="sxs-lookup"><span data-stu-id="f201d-106">BSD Sockets API Compliancy Wrapper Source</span></span>

<span data-ttu-id="f201d-107">BSD 래퍼 소스 코드는 간단한 설명을 위해 작성되었으며 *nx_bsd.h* 및 *nx_bsd.c* 의 2개 파일로만 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f201d-107">The BSD Wrapper source code is designed for simplicity and is comprised of only two files, *nx_bsd.h* and *nx_bsd.c*.</span></span> <span data-ttu-id="f201d-108">‘nx_bsd.h’ 파일은 필요한 모든 BSD Socket API 래퍼 상수와 서브루틴 프로토타입을 정의하는 반면, ‘nx_bsd.c’에는 실제 BSD Socket API 호환성 소스 코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f201d-108">The *nx_bsd.h* file defines all the necessary BSD Sockets API Wrapper constants and subroutine prototypes, while *nx_bsd.c* contains the actual BSD Sockets API compatibility source code.</span></span> <span data-ttu-id="f201d-109">이러한 BSD 래퍼 소스 파일은 모든 NetX 지원 패키지에 공통적으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f201d-109">These BSD Wrapper source files are common to all NetX support packages.</span></span>

<span data-ttu-id="f201d-110">패키지는 다음으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f201d-110">The package consists of:</span></span>

- <span data-ttu-id="f201d-111">**nx_bsd.c**: 래퍼 소스 코드</span><span class="sxs-lookup"><span data-stu-id="f201d-111">**nx_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="f201d-112">**nx_bsd.h**: 주 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="f201d-112">**nx_bsd.h**: Main header file</span></span>

<span data-ttu-id="f201d-113">샘플 데모 프로그램:</span><span class="sxs-lookup"><span data-stu-id="f201d-113">Sample demo programs:</span></span>

- <span data-ttu-id="f201d-114">**bsd_demo_tcp.c**: 단일 TCP 서버 및 클라이언트가 있는 데모</span><span class="sxs-lookup"><span data-stu-id="f201d-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="f201d-115">**bsd_demo_udp.c**: 두 개의 UDP 클라이언트와 1개의 UDP 서버를 포함하는 데모</span><span class="sxs-lookup"><span data-stu-id="f201d-115">**bsd_demo_udp.c**: *Demo with two UDP clients and a UDP server*</span></span>
