---
title: 1장 - Azure RTOS NetX Duo BSD 소개
description: BSD Socket API Compliancy Wrapper는 몇 가지 제한 사항이 있는 기본 BSD Socket API 호출 중 일부를 지원하며, 그 아래에 있는 Azure RTOS NetX Duo 기본 요소를 활용합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e89018dffd2f9f9065efab2ecabdf4364c4f89a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810975"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="ffcae-103">1장 - Azure RTOS NetX Duo BSD 소개</span><span class="sxs-lookup"><span data-stu-id="ffcae-103">Chapter 1 - Introduction to Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="ffcae-104">BSD Socket API Compliancy Wrapper는 몇 가지 제한 사항이 있는 기본 BSD Socket API 호출 중 일부를 지원하며, 그 아래에 있는 Azure RTOS NetX Duo 기본 요소를 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="ffcae-104">The BSD Socket API Compliancy Wrapper supports some of the basic BSD Socket API calls, with some limitations and utilizes Azure RTOS NetX Duo primitives underneath.</span></span>

## <a name="bsd-socket-api-compliancy-wrapper-source"></a><span data-ttu-id="ffcae-105">BSD Socket API Compliancy Wrapper 원본</span><span class="sxs-lookup"><span data-stu-id="ffcae-105">BSD Socket API Compliancy Wrapper Source</span></span>

<span data-ttu-id="ffcae-106">Wrapper 소스 코드는 단순성을 위해 설계되었으며 *nxd_bsd.h* 및 *nxd_bsd.c* 라는 두 개의 파일로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffcae-106">The Wrapper source code is designed for simplicity and is comprised of two files, namely *nxd_bsd.h* and *nxd_bsd.c*.</span></span> <span data-ttu-id="ffcae-107">*nxd_bsd.h* 파일은 필요한 모든 BSD Socket API 래퍼 상수와 서브루틴 프로토타입을 정의하는 반면, *nxd_bsd.c* 에는 실제 BSD Socket API 호환성 소스 코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffcae-107">The *nxd_bsd.h* file defines all the necessary BSD Socket API wrapper constants and subroutine prototypes, while *nxd_bsd.c* contains the actual BSD Socket API compatibility source code.</span></span> <span data-ttu-id="ffcae-108">이러한 Wrapper 원본 파일은 모든 NetX Duo 지원 패키지에 공통적으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffcae-108">These Wrapper source files are common to all NetX Duo support packages.</span></span>

<span data-ttu-id="ffcae-109">패키지는 다음으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffcae-109">The package consists of:</span></span>

- <span data-ttu-id="ffcae-110">**nxd_bsd.c**: Wrapper 소스 코드</span><span class="sxs-lookup"><span data-stu-id="ffcae-110">**nxd_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="ffcae-111">**nxd_bsd.h**: 주 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="ffcae-111">**nxd_bsd.h**: Main header file</span></span>

<span data-ttu-id="ffcae-112">샘플 데모 프로그램:</span><span class="sxs-lookup"><span data-stu-id="ffcae-112">Sample demo programs:</span></span>

- <span data-ttu-id="ffcae-113">**bsd_demo_udp.c**: *두 개의 UDP 피어가 있는 데모(IPv4 전용)*</span><span class="sxs-lookup"><span data-stu-id="ffcae-113">**bsd_demo_udp.c**: *Demo with two UDP peers (IPv4 only)*</span></span>
- <span data-ttu-id="ffcae-114">**bsd_demo_tcp.c**: *단일 TCP 서버 및 클라이언트가 있는 데모*</span><span class="sxs-lookup"><span data-stu-id="ffcae-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="ffcae-115">**bsd_demo_raw.c**: *두 개의 RAW 피어가 있는 데모*</span><span class="sxs-lookup"><span data-stu-id="ffcae-115">**bsd_demo_raw.c**: *Demo with two RAW peers*</span></span>