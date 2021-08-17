---
title: 부록 B - Azure RTOS NetX Duo DHCPv6 서버 상태 코드
description: 이 장에서는 모든 NetX Duo DHCPv6 서버 상태 코드에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8b9795607c0fed80646ee01e36edf4ecd2aaadad7f0a023e6979e123b81e1660
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791774"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a>부록 B - Azure RTOS NetX Duo DHCPv6 서버 상태 코드

| 이름              | 코드            | Description |
| ------------------- | ------------------- | --------------- |
| Success | 0 | 성공 |
| Unspecified Failure | 1 | 실패, 이유가 지정되지 않았습니다. 이 상태 코드는 다른 코드와 일치하지 않는 클라이언트 요청을 승인하는 데 일반적인 오류를 나타내기 위해 서버에서 설정됩니다. |
| NoAddress Available | 2 | 서버에는 클라이언트에 할당할 수 있는 주소가 없습니다. |
| NoBinding | 3 | 클라이언트 IA 주소(바인딩)를 사용할 수 없습니다. 예를 들어 요청된 IP 주소를 서버가 임대하거나 다른 클라이언트에 할당할 수 없습니다. |
| NotOnLink | 4 | 주소의 접두사는 IP 주소가 온링크 주소가 아님을 나타냅니다. |
| UseMulticast | 5 | *All_DHCP_Relay_Agents_and_Servers* 멀티캐스트 주소 대신 서버 유니캐스트 주소를 사용하여 클라이언트 메시지 수신에 대한 응답으로 서버에서 보냅니다. |