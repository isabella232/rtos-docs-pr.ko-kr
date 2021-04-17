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
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a>1장 - Azure RTOS NetX LWM2M 소개

Azure RTOS NetX LWM2M 프로토콜은 간단한 머신 간 프로토콜 표준의 클라이언트 부분을 구현합니다.

## <a name="netx-lwm2m-requirements"></a>NetX LWM2M 요구 사항

NetX LWM2M 런타임 라이브러리가 제대로 작동하려면 NetX IP 인스턴스가 이미 생성되어 있어야 합니다. NetX LWM2M 패키지에는 추가 요구 사항이 없습니다.

## <a name="netx-lwm2m-rfcs"></a>NetX LWM2M RFC

NetX LWM2M은 OMA-TS-LightweightM2M-V1_0-20170208-A 및 CoAP(제약이 있는 애플리케이션 프로토콜)와 관련된 다음 RFC와 호환됩니다.

- **RFC 7252**: CoAP(제약이 있는 애플리케이션 프로토콜)

- **RFC 7641**: CoAP(제약이 있는 애플리케이션 프로토콜)에서 리소스 관찰

- **RFC 6690**: CoRE(제약이 있는 RESTful 환경) 링크 형식