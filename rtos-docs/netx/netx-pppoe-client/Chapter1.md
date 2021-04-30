---
title: 1장 - Azure RTOS NetX PPPoE 클라이언트 소개
description: 이 장에서는 Azure RTOS NetX PPPoE 모듈의 세부 정보를 포함합니다.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bbf1e064bb38754bd67b279a0fd60d46d3d6d557
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811460"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-client"></a><span data-ttu-id="81078-103">1장 - Azure RTOS NetX PPPoE 클라이언트 소개</span><span class="sxs-lookup"><span data-stu-id="81078-103">Chapter 1 - Introduction to Azure RTOS NetX PPPoE Client</span></span>

<span data-ttu-id="81078-104">PPPoE(PPP over Ethernet)를 사용하면 호스트가 기존의 문자 기반 직렬 회선 통신 대신 이더넷을 통해 PPP 서버에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81078-104">PPP over Ethernet (PPPoE) allows hosts to connect to PPP server via Ethernet instead of the traditional character-based serial line communication.</span></span>  <span data-ttu-id="81078-105">PPPoE의 기술 세부 정보는 RFC 2516: PPPoE(PPP over Ethernet)를 전송하는 방법에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81078-105">The technical details of PPPoE are described in RFC 2516:  A Method for Transmitting PPP over Ethernet (PPPoE).</span></span> <span data-ttu-id="81078-106">이 문서에서는 Azure RTOS NetX PPPoE 모듈의 세부 정보를 집중적으로 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="81078-106">This document focuses on the details of  Azure RTOS NetX PPPoE module.</span></span>

<span data-ttu-id="81078-107">이더넷을 통한 지점 간 연결을 제공하려면 PPP 세션이 원격 피어의 이더넷 주소를 학습하고 고유한 세션 식별자를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81078-107">To provide a point-to-point connection over Ethernet, each PPP session must learn the Ethernet address of the remote peer, as well as establish a unique session identifier.</span></span>

<span data-ttu-id="81078-108">RFC 2516에 따르면 PPPoE는 검색 단계와 PPPoE 세션 단계의 두 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="81078-108">According to RFC 2516, PPPoE consists of two stages: the Discovery stage, and PPPoE Session stage.</span></span> <span data-ttu-id="81078-109">호스트(클라이언트)에서 PPP 세션을 시작하려면 먼저 검색을 수행하여 PPPoE 서버를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81078-109">When a host (client) wishes to start a PPP session, it must first perform Discovery to find PPPoE server.</span></span> <span data-ttu-id="81078-110">또한 이 단계를 통해 서버와 클라이언트는 나머지 PPP 세션에 사용될 이더넷 MAC 주소와 SESSION_ID를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81078-110">This step also allows the server and the client to identify each other’s Ethernet MAC address and SESSION_ID, which will be used for the rest of the PPP session.</span></span>

<span data-ttu-id="81078-111">이더넷 프레임은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="81078-111">An Ethernet frame is as follows:</span></span>

![이더넷 프레임](media/ethernet-frame.png)

<span data-ttu-id="81078-113">PPPoE의 이더넷 페이로드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="81078-113">The Ethernet payload for PPPoE is as follows:</span></span>

![이더넷 페이로드](media/ethernet-payload.png)

## <a name="pppoe-discovery-stage"></a><span data-ttu-id="81078-115">PPPoE 검색 단계</span><span class="sxs-lookup"><span data-stu-id="81078-115">PPPoE Discovery Stage</span></span>

<span data-ttu-id="81078-116">PPPoE 검색 단계를 통해 클라이언트는 네트워크에 있는 사용 가능한 모든 서버에서 서버를 선택하여 PPP 프레임을 교환하기 전에 세션을 효과적으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81078-116">The PPPoE Discovery stage allows clients to select a server from all available servers on the network, effectively to create a session prior to PPP frames being exchanged.</span></span>  <span data-ttu-id="81078-117">검색 단계가 끝나면 클라이언트와 서버가 모두 고유한 세션 ID에 동의하고 양쪽 모두 피어의 MAC 주소를 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81078-117">At the end of the discovery stage, both the client and the server shall agree on a unique session ID, and both sides need to know peer’s MAC address.</span></span>

| <span data-ttu-id="81078-118">검색 메시지</span><span class="sxs-lookup"><span data-stu-id="81078-118">Discovery Message</span></span> | <span data-ttu-id="81078-119">코드</span><span class="sxs-lookup"><span data-stu-id="81078-119">Code</span></span> | <span data-ttu-id="81078-120">Direction</span><span class="sxs-lookup"><span data-stu-id="81078-120">Direction</span></span> |
| ----------------- | ---- | --------- |
| <span data-ttu-id="81078-121">PADI(PPPoE 활성 검색 시작)</span><span class="sxs-lookup"><span data-stu-id="81078-121">PPPoE Active Discovery Initiation (PADI)</span></span> | <span data-ttu-id="81078-122">0x09</span><span class="sxs-lookup"><span data-stu-id="81078-122">0x09</span></span> | <span data-ttu-id="81078-123">클라이언트에서 브로드캐스트로</span><span class="sxs-lookup"><span data-stu-id="81078-123">From Client to broadcast</span></span> |
| <span data-ttu-id="81078-124">PADO(PPPoE 활성 검색 제안)</span><span class="sxs-lookup"><span data-stu-id="81078-124">PPPoE Active Discovery Offer (PADO)</span></span> | <span data-ttu-id="81078-125">0x07</span><span class="sxs-lookup"><span data-stu-id="81078-125">0x07</span></span> | <span data-ttu-id="81078-126">서버에서 클라이언트로</span><span class="sxs-lookup"><span data-stu-id="81078-126">From Server to Client</span></span> |
| <span data-ttu-id="81078-127">PADR(PPPoE 활성 검색 요청)</span><span class="sxs-lookup"><span data-stu-id="81078-127">PPPoE Active Discovery Request (PADR)</span></span> | <span data-ttu-id="81078-128">0x19</span><span class="sxs-lookup"><span data-stu-id="81078-128">0x19</span></span> | <span data-ttu-id="81078-129">클라이언트에서 서버로</span><span class="sxs-lookup"><span data-stu-id="81078-129">From Client to Server</span></span> |
| <span data-ttu-id="81078-130">PADS(PPPOE 활성 검색 세션 확인)</span><span class="sxs-lookup"><span data-stu-id="81078-130">PPPOE Active Discovery Session-confirmation (PADS)</span></span> | <span data-ttu-id="81078-131">0x65</span><span class="sxs-lookup"><span data-stu-id="81078-131">0x65</span></span> | <span data-ttu-id="81078-132">서버에서 클라이언트로</span><span class="sxs-lookup"><span data-stu-id="81078-132">From Server to Client</span></span> |
| <span data-ttu-id="81078-133">PADT(PPPoE 활성 검색 종료)</span><span class="sxs-lookup"><span data-stu-id="81078-133">PPPoE Active Discovery Terminate (PADT)</span></span> | <span data-ttu-id="81078-134">0xa7</span><span class="sxs-lookup"><span data-stu-id="81078-134">0xa7</span></span> | <span data-ttu-id="81078-135">서버 또는 클라이언트에서 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81078-135">Can be initiated from either server or client</span></span> |

<span data-ttu-id="81078-136">모든 검색 이더넷 프레임에는 ETHER_TYPE 필드가 0x8863 값으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81078-136">All Discovery Ethernet frames have the ETHER_TYPE field set to the value 0x8863.</span></span>

## <a name="pppoe-session-message"></a><span data-ttu-id="81078-137">PPPoE 세션 메시지</span><span class="sxs-lookup"><span data-stu-id="81078-137">PPPoE Session Message</span></span>

<span data-ttu-id="81078-138">클라이언트와 서버에서 세션을 만든 후에 PPP 프레임을 PPPoE 세션 메시지로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81078-138">After the client and the server create a session, PPP frames can be transferred as PPPoE Session messages.</span></span>  <span data-ttu-id="81078-139">세션 중에 SESSION_ID는 변경되지 않아야 하며 검색 단계 중에 서버가 할당한 값이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81078-139">During a session, the SESSION_ID must not change and must be the value the server assigned during the Discovery stage.</span></span>

<span data-ttu-id="81078-140">모든 PPPoE 세션 이더넷 프레임에는 ETHER_TYPE 필드가 0x8864 값으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81078-140">All PPPoE Session Ethernet frames have the ETHER_TYPE field set to the value 0x8864.</span></span>
