---
title: GUIX Studio 사용자 가이드
description: 이 가이드는 Microsoft의 GUIX 런타임 라이브러리용으로 특별히 설계된 Microsoft Windows 기반의 빠른 UI 개발 환경인 GUIX Studio에 대한 포괄적인 정보를 제공합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6a5d628581d4c6b44ff093bac45790d6e2755349
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811988"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a>1장: Azure RTOS GUIX Studio 소개

Azure RTOS GUIX Studio는 Microsoft의 GUIX 런타임 라이브러리용으로 특별히 설계된 Microsoft Windows 기반의 빠른 UI 개발 환경입니다.

포함된 UI 개발자는 GUIX Studio WYSIWYG 화면 디자이너를 활용하여 GUIX 런타임 환경을 사용하여 포함된 UI를 신속하게 만들고 업데이트할 수 있습니다. GUIX Studio 디자인은 확장명이 .gxp인 GUIX Studio 프로젝트 파일에 저장되고 유지 관리됩니다. 디자인을 대상에서 실행할 준비가 되면 GUIX Studio는 필요한 모든 UI 정보 및 코드가 포함된 C 코드를 생성합니다.

## <a name="guix-studio-requirements"></a>GUIX Studio 요구 사항

제대로 작동하기 위해 Microsoft의 GUIX Studio에는 *Windows XP*(이상)가 필요합니다. 시스템에는 최소 200MB의 RAM, 2GB의 사용 가능한 하드 디스크 공간 및 256색이 포함된 1024x768 최소 디스플레이가 있어야 합니다. 또한 포함된 애플리케이션은 *ThreadX/GUIX V6.0* 이상에서 실행되어야 합니다.

포함된 UI 애플리케이션을 독립 실행형 Microsoft Windows 실행 파일로 빌드하고 실행할 수 있게 하려는 경우에는 Microsoft Windows 실행 파일을 생성할 C 소스 코드를 컴파일할 수 있는 컴파일러 또는 빌드 환경도 필요합니다. GUIX Studio에 포함된 평가 패키지에는 제공된 각 예제 애플리케이션에 대한 Visual Studio 2019 호환 프로젝트 파일 및 솔루션도 포함되어 있습니다. 다른 컴파일러를 사용하는 경우 사용자 고유의 프로젝트 파일을 만들거나 예제 애플리케이션을 빌드하기 위해 파일을 만들거나 https://aka.ms/azrtos-support 에서 지원에 문의해야 합니다.

## <a name="guix-studio-constraints"></a>GUIX Studio 제약 조건

GUIX Studio UI 디자인 도구에는 다음과 같은 몇 가지 제약 조건이 있습니다.

- 프로젝트당 최대 4개의 디스플레이
- GUIX Studio 프로젝트당 최대 10만 위젯
- 최대 10만의 고유 리소스(예: 색, 글꼴, pixelmap, 문자열 등)