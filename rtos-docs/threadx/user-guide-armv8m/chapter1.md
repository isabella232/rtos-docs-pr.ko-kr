---
title: 챕터 1 - ARMv8-M의 Azure RTOS ThreadX 소개입니다.
description: 이 챕터는 ARMv8-M의 Azure RTOS ThreadX 추록 읽기를 위한 시작 지점입니다.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f0d87ec562c7fcfa6af5d2240655ef526f6e0611d509fe60c745436371413d7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798251"
---
# <a name="chapter-1--overview"></a>챕터 1 - 개요

ARMv8-M 아키텍처는 메모리를 안전하거나 안전하지 않은 태그로 지정할 수 있는 TrustZone을 포함하여 새 보안 기능을 도입합니다. ARM의 지침에 따라 ThreadX(및 사용자 애플리케이션)는 비보안 모드에서 실행되도록 설계되었습니다. ThreadX(및 사용자 애플리케이션)는 보안 모드에서도 실행할 수 있습니다. 보안 모드 소프트웨어를 사용하여 접속하기 위해 몇 가지 새 ThreadX API가 필요합니다. 이 문서는 Cortex-M23, Cortex-M33, Cortex-M35P 및 Cortex-M55를 포함하여 ARMv8-M 아키텍처와 관련된 ThreadX 서비스에 대해 설명합니다.
