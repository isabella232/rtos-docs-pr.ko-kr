---
title: 1장 - Azure RTOS TraceX 소개
description: Azure RTOS TraceX는 포함된 대상에서 실행되는 ThreadX에서 수집된 시스템 이벤트 정보를 표시하는 Microsoft 시스템 분석 도구입니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 3009d13388b3b7e8eca041dc6ede569a5caf5e9b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812499"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a>1장 - Azure RTOS TraceX 소개

Azure RTOS TraceX는 포함된 대상에서 실행되는 ThreadX에서 수집된 시스템 이벤트 정보를 표시하는 Microsoft 시스템 분석 도구입니다. 사용자는 포함된 대상의 RAM에 저장된 추적 버퍼를 호스트 컴퓨터의 이진 파일로 전송할 책임이 있습니다. 그런 다음, 사용자는 TraceX를 사용하여 이 파일을 열고 대상 이벤트를 그래픽으로 분석하여 시스템 문제를 진단하고, 작업 애플리케이션을 조정하여 성능 및 리소스 관리를 개선할 수 있습니다.

## <a name="tracex-requirements"></a>TraceX 요구 사항

TraceX에는 Windows XP 이상이 필요합니다. 시스템에는 최소 192MB의 RAM, 2GB의 사용 가능한 하드 디스크 공간 및 256 색이 포함된 1024x768 최소 디스플레이가 있어야 합니다. 또한 애플리케이션은 ThreadX V5.0 이상에서 실행되어야 합니다.

또한 TraceX를 사용하려면 TraceX 설치 관리자가 자동으로 수행하는 Microsoft .NET 프레임워크가 설치되어 있어야 합니다.

## <a name="tracex-constraints"></a>TraceX 제약 조건

TraceX에는 다음과 같은 제약 조건이 있습니다.

- TraceX 파일은 최대 32,768개의 이벤트(약 1MB)로 제한됩니다.
- 타임스탬프 원본은 해상도가 적당해야 합니다. 해상도가 너무 낮으면 이벤트가 겹칩니다. 해상도가 너무 높으면 이벤트 사이에 긴 간격이 발생할 수 있습니다.
- TraceX는 타이머 기간보다 큰 이벤트 사이의 간격을 정확하게 측정할 수 없습니다.
