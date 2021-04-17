---
title: 1장 - Azure RTOS NetX Duo LWM2M 클라이언트 소개
description: 이 장에서는 Azure RTOS NetX Duo 경량 머신 간 프로토콜 클라이언트에 대해 소개합니다.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 12f13c154668b3cadfae0924e59b55631dc27424
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810771"
---
# <a name="chapter-1--introduction-to-lwm2m-client"></a><span data-ttu-id="11d86-103">1장: LWM2M 클라이언트 소개</span><span class="sxs-lookup"><span data-stu-id="11d86-103">Chapter 1  Introduction to LWM2M Client</span></span>

<span data-ttu-id="11d86-104">Azure RTOS NetX Duo LWM2M 클라이언트 프로토콜은 간단한 머신 간 프로토콜 표준의 클라이언트 부분을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="11d86-104">The Azure RTOS NetX Duo LWM2M Client Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span> <span data-ttu-id="11d86-105">(LWM2M 1.0-20170208A)</span><span class="sxs-lookup"><span data-stu-id="11d86-105">(LWM2M 1.0-20170208A)</span></span>

## <a name="netx-lwm2m-client-requirements"></a><span data-ttu-id="11d86-106">NetX LWM2M 클라이언트 요구 사항</span><span class="sxs-lookup"><span data-stu-id="11d86-106">NetX LWM2M Client Requirements</span></span>

<span data-ttu-id="11d86-107">LWM2M 클라이언트 런타임 라이브러리가 제대로 작동하려면 NetX IP 인스턴스가 이미 생성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11d86-107">In order to function properly, the LWM2M Client run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="11d86-108">NetX LWM2M 클라이언트 패키지에는 추가 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11d86-108">The NetX LWM2M Client package has no further requirements.</span></span>

## <a name="netx-lwm2m-client-rfcs"></a><span data-ttu-id="11d86-109">NetX LWM2M 클라이언트 RFC</span><span class="sxs-lookup"><span data-stu-id="11d86-109">NetX LWM2M Client RFCs</span></span>

<span data-ttu-id="11d86-110">LWM2M 클라이언트는 OMA-TS-LightweightM2M-V1\_0-20170208-A 및 CoAP(제약이 있는 애플리케이션 프로토콜)와 관련된 다음 RFC와 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="11d86-110">LWM2M Client is compliant with OMA-TS-LightweightM2M-V1\_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP).</span></span>

* <span data-ttu-id="11d86-111">RFC 7252 CoAP(제약이 있는 애플리케이션 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="11d86-111">RFC 7252 The Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="11d86-112">RFC 7641 CoAP(제약이 있는 애플리케이션 프로토콜)에서 리소스 관찰</span><span class="sxs-lookup"><span data-stu-id="11d86-112">RFC 7641 Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="11d86-113">RFC 6690 CoRE(제약이 있는 RESTful 환경) 링크 형식</span><span class="sxs-lookup"><span data-stu-id="11d86-113">RFC 6690 Constrained RESTful Environments (CoRE) Link Format</span></span>

<span data-ttu-id="11d86-114">자세한 내용은 [OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="11d86-114">For more information, please see [OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).</span></span>