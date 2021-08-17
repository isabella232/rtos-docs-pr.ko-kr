---
title: 1장 - Azure RTOS NetX Duo mDNS/DNS-SD 소개
description: Azure RTOS NetX Duo mDNS/DNS-SD는 기존 DNS 서비스를 보강합니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7cde8e81809dcc74ee5d0b09d8e7a8d2ae96850cd84250a5bf003fdd5763925a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796449"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a>1장 - Azure RTOS NetX Duo mDNS/DNS-SD 소개

mDNS 및 DNS-SD는 기존 DNS 서비스를 보강하기 위해 설계된 프로토콜입니다. mDNS는 로컬 네트워크의 노드에 호스트 이름 및 서비스 조회를 제공합니다. 각 노드는 IPv4 또는 IPv6 멀티캐스트 채널을 사용하여 그것을 해당 환경에 제공하는 서비스를 알리고, 그 환경으로부터의 쿼리에 응답하며, 애플리케이션의 동작에 대한 쿼리를 보냅니다. 기본적으로 mDNS는 분산된 환경에서 작동하므로 중앙 서버를 제거합니다.

DNS-SD는 mDNS 맨 위에 빌드됩니다. DNS-SD는 노드를 통해 로컬 네트워크에 제공하는 서비스를 발표하거나 로컬 네트워크의 다른 노드에서 제공하는 서비스를 검색할 수 있습니다. 문서 전체에서 *mDNS* 라는 용어는 mDNS 사양과 DNS-SD 사양을 모두 포함하는 서비스를 의미합니다.

## <a name="mdns-standard"></a>mDNS 표준

NetX Duo mDNS/DNS-SD 구현은 다음 RFC를 따릅니다.

- RFC 6762: mDNS 사양
- RFC 6763: DNS-SD 사양