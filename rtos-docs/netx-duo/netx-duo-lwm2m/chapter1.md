---
title: 1장 - Azure RTOS NetX Duo LWM2M 클라이언트 소개
description: 이 장에서는 Azure RTOS NetX Duo 경량 머신 간 프로토콜 클라이언트에 대해 소개합니다.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a2722daac76632e492d0f9345103c45da9ba1b321e91c9c04e04c76463984c3a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783478"
---
# <a name="chapter-1--introduction-to-lwm2m-client"></a>1장: LWM2M 클라이언트 소개

Azure RTOS NetX Duo LWM2M 클라이언트 프로토콜은 간단한 머신 간 프로토콜 표준의 클라이언트 부분을 구현합니다. (LWM2M 1.0-20170208A)

## <a name="netx-lwm2m-client-requirements"></a>NetX LWM2M 클라이언트 요구 사항

LWM2M 클라이언트 런타임 라이브러리가 제대로 작동하려면 NetX IP 인스턴스가 이미 생성되어 있어야 합니다. NetX LWM2M 클라이언트 패키지에는 추가 요구 사항이 없습니다.

## <a name="netx-lwm2m-client-rfcs"></a>NetX LWM2M 클라이언트 RFC

LWM2M 클라이언트는 OMA-TS-LightweightM2M-V1\_0-20170208-A 및 CoAP(제약이 있는 애플리케이션 프로토콜)와 관련된 다음 RFC와 호환됩니다.

* RFC 7252 CoAP(제약이 있는 애플리케이션 프로토콜)

* RFC 7641 CoAP(제약이 있는 애플리케이션 프로토콜)에서 리소스 관찰

* RFC 6690 CoRE(제약이 있는 RESTful 환경) 링크 형식

자세한 내용은 [OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf)를 참조하세요.