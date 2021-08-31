---
title: 1장 - Azure RTOS NetX Duo Iperf 소개
description: Iperf 샘플은 TCP 및 UDP 네트워크 처리량을 테스트하는 네트워크 테스트 프로그램입니다.
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9d67aa182c19d84ad90fd82824d72888fbda8d25
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2021
ms.locfileid: "122609794"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-iperf"></a>1장 - Azure RTOS NetX Duo Iperf 소개

Iperf는 Windows 및 Linux 호스트 모두에서 실행되는 표준 네트워크 테스트 프로그램입니다. Iperf는 TCP 및 UDP 네트워크 처리량을 테스트하도록 설계되었습니다. 이 문서의 예는 Jperf라는 Java 기반 Iperf 구현을 기반으로 합니다. Iperf에 대한 자세한 내용은 Wikipedia 링크를 참조하세요.

> [http://en.wikipedia.org/wiki/Iperf](http://en.wikipedia.org/wiki/Iperf)

NetX Duo Iperf 데모는 NetX Duo 성능과 기본 하드웨어의 성능을 평가하기 위해 다양한 평가 보드를 실행하도록 설계되었습니다. 이 데모는 NetX Duo를 사용하여 일부 제한된 네트워크 프로그래밍을 수행하기 위한 일반 플랫폼으로도 사용될 수 있습니다.
