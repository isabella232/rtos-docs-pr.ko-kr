---
title: 1장 - Azure RTOS NetX Duo mDNS/DNS-SD 소개
description: Azure RTOS NetX Duo mDNS/DNS-SD는 기존 DNS 서비스를 보강합니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b46539ee4d502fa4c90fb3392e25cd3bee40dc5b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810741"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a><span data-ttu-id="afd94-103">1장 - Azure RTOS NetX Duo mDNS/DNS-SD 소개</span><span class="sxs-lookup"><span data-stu-id="afd94-103">Chapter 1 - Introduction to Azure RTOS NetX Duo mDNS/DNS-SD</span></span>

<span data-ttu-id="afd94-104">mDNS 및 DNS-SD는 기존 DNS 서비스를 보강하기 위해 설계된 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="afd94-104">The mDNS and DNS-SD are protocols designed to augment the traditional DNS service.</span></span> <span data-ttu-id="afd94-105">mDNS는 로컬 네트워크의 노드에 호스트 이름 및 서비스 조회를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="afd94-105">mDNS provides host name and service lookup to the nodes on the local network.</span></span> <span data-ttu-id="afd94-106">각 노드는 IPv4 또는 IPv6 멀티캐스트 채널을 사용하여 그것을 해당 환경에 제공하는 서비스를 알리고, 그 환경으로부터의 쿼리에 응답하며, 애플리케이션의 동작에 대한 쿼리를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="afd94-106">Each node uses IPv4 or IPv6 multicast channel to announce services it offers to its neighbors, responds to queries from its neighbors, and sends queries on behave of its applications.</span></span> <span data-ttu-id="afd94-107">기본적으로 mDNS는 분산된 환경에서 작동하므로 중앙 서버를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="afd94-107">By design, mDNS operates in a distributed environment, thus eliminates a centralized serve.</span></span>

<span data-ttu-id="afd94-108">DNS-SD는 mDNS 맨 위에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="afd94-108">DNS-SD is built on top of mDNS.</span></span> <span data-ttu-id="afd94-109">DNS-SD는 노드를 통해 로컬 네트워크에 제공하는 서비스를 발표하거나 로컬 네트워크의 다른 노드에서 제공하는 서비스를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afd94-109">DNS-SD allows nodes to announce services they provide to the local network or to discover services offered by other nodes on the local network.</span></span> <span data-ttu-id="afd94-110">문서 전체에서 *mDNS* 라는 용어는 mDNS 사양과 DNS-SD 사양을 모두 포함하는 서비스를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="afd94-110">Throughout the document, the term *mDNS* refers to the services that cover both the mDNS specification and the DNS-SD specification.</span></span>

## <a name="mdns-standard"></a><span data-ttu-id="afd94-111">mDNS 표준</span><span class="sxs-lookup"><span data-stu-id="afd94-111">mDNS Standard</span></span>

<span data-ttu-id="afd94-112">NetX Duo mDNS/DNS-SD 구현은 다음 RFC를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="afd94-112">NetX Duo mDNS/DNS-SD implementation conforms to the following RFCs:</span></span>

- <span data-ttu-id="afd94-113">RFC 6762: mDNS 사양</span><span class="sxs-lookup"><span data-stu-id="afd94-113">RFC 6762: mDNS Specification</span></span>
- <span data-ttu-id="afd94-114">RFC 6763: DNS-SD 사양</span><span class="sxs-lookup"><span data-stu-id="afd94-114">RFC 6763: DNS-SD Specification</span></span>