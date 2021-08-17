---
title: 부록 A – Azure RTOS NetX Duo DHCPv6 옵션 코드
description: 이 챕터에서는 모든 NetX Duo DHCPv6 옵션 코드에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 58b6e36fab4de02a9fb973894500a48f2656809ec2baa3dfc65fcd80ae33b832
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791834"
---
# <a name="appendix-a--azure-rtos-netx-duo-dhcpv6-option-codes"></a>부록 A – Azure RTOS NetX Duo DHCPv6 옵션 코드

| 옵션              | 코드            | Description |
| ------------------- | ------------------- | --------------- |
| 클라이언트 식별자 DUID | 1 | 네트워크에서 클라이언트 호스트를 고유하게 식별합니다. |
| 서버 식별자(DUID) | 2 | 네트워크에서 DHCPv6Server 호스트를 고유하게 식별합니다. |
| 비 임시 주소(IANA)에 대한 ID 연결 | 3 | 일시적이지 않은 IP 주소 할당에 대한 매개 변수 |
| 임시 주소(IATA)에 대한 ID 연결 | 4 | 임시 IP 주소 할당에 대한 매개 변수 |
| IA 주소 | 5 | 클라이언트에 할당되는 실제 IPv6 주소 및 IPv6 주소 수명 |
| 옵션 요청 | 6 | DNS 서버 및 기타 네트워크 구성 매개 변수와 같은 네트워크 정보를 얻기 위한 정보 요청 목록입니다. |
| 기본 설정 | 7 | 클라이언트에서 선택한 서버에 영향을 주도록 클라이언트의 서버 알림 메시지에 포함합니다. 클라이언트는 다른 서버보다 기본 설정 값이 높은 서버를 선택해야 합니다. 255는 최댓값이지만 0은 클라이언트에서 해당 서버에 회신하는 모든 서버를 선택할 수 있음을 나타냅니다. |
| 경과된 시간 | 8 | 클라이언트가 서버와 함께 DHCPv6 교환을 시작하는 시간(0.01초)을 포함합니다. 보조 서버에서 주 서버가 클라이언트 요청에 시간 내에 응답하는지 확인하는 데 사용됩니다. |
| 릴레이 메시지 | 9 | 릴레이 메시지의 원래 메시지를 포함합니다. | 
| 인증 | 11 | DHCPv6 메시지의 ID와 콘텐츠를 인증하는 정보를 포함합니다. |
| 서버 유니캐스트 | 12 | 서버는 멀티캐스트 대신 클라이언트에서 직접 유니캐스트 메시지를 수락하는 것을 클라이언트가 알 수 있도록 이 옵션을 보냅니다. |

이 버전의 NetX Duo DHCPv6 서버에서는 IATA, Relay 메시지, 인증 및 서버 유니캐스트 옵션이 지원되지 않습니다. 현재 DHCPv6 프로토콜 옵션 코드 10은 RFC 3315에 정의되어 있지 않습니다.