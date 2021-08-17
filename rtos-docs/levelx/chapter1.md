---
title: 1장 - Azure RTOS LevelX 개요
description: Azure RTOS LevelX는 포함된 애플리케이션에 NAND 및 NOR 플래시 마모 평준화 기능을 제공합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73c06d48b98081291d83635e049e6cf8641714c87efe815f9399f3fbab3a6211
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790601"
---
# <a name="chapter-1---overview-of-azure-rtos-levelx"></a>1장 - Azure RTOS LevelX 개요

Azure RTOS LevelX는 포함된 애플리케이션에 NAND 및 NOR 플래시 마모 평준화 기능을 제공합니다. NAND 및 NOR 플래시 메모리는 모두 한정된 횟수만 지울 수 있으므로 플래시 메모리 사용을 균등하게 분산하는 것이 중요합니다. 이를 일반적으로 "마모 평준화"라고 하며, 이는 LevelX를 사용하는 목적입니다.

재사용할 플래시 블록을 선택하는 알고리즘은 주로 지우기 수를 기반으로 하지만 완전히 그렇지는 않습니다. 최소 지우기 개수에서 허용되는 델타 내에 지우기 수가 있고 사용되지 않는 매핑의 개수가 더 많은 다른 블록이 있는 경우 지우기 수가 가장 적은 블록을 선택하지 못할 수 있습니다. 이러한 경우 사용되지 않는 매핑의 수가 가장 많은 블록을 지우고 다시 사용하므로 올바른 매핑 항목 이동에 대한 오버 헤드가 절약됩니다.

LevelX는 NAND 및/또는 NOR 파트의 여러 인스턴스를 지원합니다. 즉, 애플리케이션은 동일한 애플리케이션 내에서 LevelX의 개별 인스턴스를 활용할 수 있습니다. 각 인스턴스에는 애플리케이션 뿐만 아니라 자체 플래시 드라이버에서 제공하는 자체 제어 블록이 필요합니다.

LevelX는 사용자에게 LevelX 내의 실제 플래시 메모리에 매핑되는 논리 섹터의 배열을 제공합니다. 성능 향상을 위해 LevelX는 가장 최근 논리적 섹터 매핑의 캐시도 제공합니다. 이 캐시의 크기는 프로그래머에 의해 정의됩니다. 애플리케이션은 FileX와 함께 LevelX를 사용하거나 논리적 섹터를 직접 읽거나 쓸 수 있습니다. LevelX는 FileX에 대한 종속성이 없으며 ThreadX에 대한 종속성이 거의 없습니다(기본 ThreadX 데이터 형식만 사용됨).

LevelX는 내결함성을 위해 설계되었습니다. 플래시 업데이트는 각 단계에서 중단될 수 있는 다중 단계 프로세스에서 수행됩니다. LevelX는 다음 작업을 수행하는 동안 최적 상태로 자동으로 복구됩니다.

LevelX를 사용하려면 기본 플래시 메모리에 물리적으로 액세스하기 위한 플래시 드라이버가 필요합니다. 예제 NAND 및 NOR 시뮬레이션된 드라이버가 제공되며 실제 LevelX 드라이버를 구현하기 위한 좋은 출발점으로 사용할 수 있습니다. 또한 드라이버 요구 사항은 이 설명서의 뒷부분에 자세히 설명되어 있습니다.

다음 장에서는 NAND 및 NOR LevelX 지원에 대한 기능 작업을 설명합니다.
