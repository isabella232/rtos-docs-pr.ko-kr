---
title: 1장 - Azure RTOS NetX LWM2M 소개
description: Azure RTOS NetX LWM2M 프로토콜은 간단한 머신 간 프로토콜 표준의 클라이언트 부분을 구현합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c29af430975266eed684bd1de38d9e5d7e2586a6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811526"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a><span data-ttu-id="aa145-103">1장 - Azure RTOS NetX LWM2M 소개</span><span class="sxs-lookup"><span data-stu-id="aa145-103">Chapter 1 - Introduction to Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="aa145-104">Azure RTOS NetX LWM2M 프로토콜은 간단한 머신 간 프로토콜 표준의 클라이언트 부분을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="aa145-104">The Azure RTOS NetX LWM2M Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span>

## <a name="netx-lwm2m-requirements"></a><span data-ttu-id="aa145-105">NetX LWM2M 요구 사항</span><span class="sxs-lookup"><span data-stu-id="aa145-105">NetX LWM2M Requirements</span></span>

<span data-ttu-id="aa145-106">NetX LWM2M 런타임 라이브러리가 제대로 작동하려면 NetX IP 인스턴스가 이미 생성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa145-106">In order to function properly, the NetX LWM2M run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="aa145-107">NetX LWM2M 패키지에는 추가 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa145-107">The NetX LWM2M package has no further requirements.</span></span>

## <a name="netx-lwm2m-rfcs"></a><span data-ttu-id="aa145-108">NetX LWM2M RFC</span><span class="sxs-lookup"><span data-stu-id="aa145-108">NetX LWM2M RFCs</span></span>

<span data-ttu-id="aa145-109">NetX LWM2M은 OMA-TS-LightweightM2M-V1_0-20170208-A 및 CoAP(제약이 있는 애플리케이션 프로토콜)와 관련된 다음 RFC와 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa145-109">NetX LWM2M is compliant with OMA-TS-LightweightM2M-V1_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP):</span></span>

- <span data-ttu-id="aa145-110">**RFC 7252**: CoAP(제약이 있는 애플리케이션 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="aa145-110">**RFC 7252**: The Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="aa145-111">**RFC 7641**: CoAP(제약이 있는 애플리케이션 프로토콜)에서 리소스 관찰</span><span class="sxs-lookup"><span data-stu-id="aa145-111">**RFC 7641**: Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="aa145-112">**RFC 6690**: CoRE(제약이 있는 RESTful 환경) 링크 형식</span><span class="sxs-lookup"><span data-stu-id="aa145-112">**RFC 6690**: Constrained RESTful Environments (CoRE) Link Format</span></span>