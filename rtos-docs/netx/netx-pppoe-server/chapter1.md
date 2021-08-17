---
title: 1장 - Azure RTOS NetX PPPoE Server 소개
description: 이 문서에서는 Azure RTOS NetX PPPoE 모듈의 세부 정보를 집중적으로 다룹니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2f79cba35991555f7f8d10e589aa251387ce25c48c3b729da371b548f13321bd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798322"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-server"></a>1장 - Azure RTOS NetX PPPoE Server 소개

PPPoE(PPP over Ethernet)를 사용하면 호스트가 기존의 문자 기반 직렬 회선 통신 대신 이더넷을 통해 PPP 서버에 연결할 수 있습니다. PPPoE의 기술 세부 정보는 RFC 2516: PPPoE(PPP over Ethernet)를 전송하는 방법에 설명되어 있습니다. 이 문서에서는 Azure RTOS NetX PPPoE 모듈의 세부 정보를 집중적으로 다룹니다.

이더넷을 통한 지점 간 연결을 제공하려면 PPP 세션이 원격 피어의 이더넷 주소를 학습하고 고유한 세션 식별자를 설정해야 합니다.

RFC 2516에 따르면 PPPoE는 검색 단계와 PPPoE 세션 단계의 두 단계로 구성됩니다. 호스트(클라이언트)에서 PPP 세션을 시작하려면 먼저 검색을 수행하여 PPPoE 서버를 찾아야 합니다. 또한 이 단계를 통해 서버와 클라이언트는 나머지 PPP 세션에 사용될 이더넷 MAC 주소와 SESSION_ID를 식별할 수 있습니다.

이더넷 프레임은 다음과 같습니다.

![이더넷 프레임을 보여주는 다이어그램.](media/netx-pppoe-server-01.png)

PPPoE의 이더넷 페이로드는 다음과 같습니다.

![PPPoE의 이더넷 페이로드를 보여주는 다이어그램.](media/netx-pppoe-server-02.png)

## <a name="pppoe-discovery-stage"></a>PPPoE 검색 단계

PPPoE 검색 단계를 통해 클라이언트는 네트워크에 있는 사용 가능한 모든 서버에서 서버를 선택하여 PPP 프레임을 교환하기 전에 세션을 효과적으로 만들 수 있습니다. 검색 단계가 끝나면 클라이언트와 서버가 모두 고유한 세션 ID에 동의하고 양쪽 모두 피어의 MAC 주소를 알아야 합니다.

| 검색 메시지                                  | 코드 | Direction                                     |
| -------------------------------------------------- | ---- | --------------------------------------------- |
| PADI(PPPoE 활성 검색 시작)           | 0x09 | 클라이언트에서 브로드캐스트로                      |
| PADO(PPPoE 활성 검색 제안)                | 0x07 | 서버에서 클라이언트로                         |
| PADR(PPPoE 활성 검색 요청)              | 0x19 | 클라이언트에서 서버로                         |
| PADS(PPPOE 활성 검색 세션 확인) | 0x65 | 서버에서 클라이언트로                         |
| PADT(PPPoE 활성 검색 종료)            | 0xa7 | 서버 또는 클라이언트에서 시작할 수 있습니다. |

모든 검색 이더넷 프레임에는 ETHER_TYPE 필드가 0x8863 값으로 설정되어 있습니다.

## <a name="pppoe-session-message"></a>PPPoE 세션 메시지

클라이언트와 서버에서 세션을 만든 후에 PPP 프레임을 PPPoE 세션 메시지로 전송할 수 있습니다. 세션 중에 SESSION_ID는 변경되지 않아야 하며 검색 단계 중에 서버가 할당한 값이어야 합니다.

모든 PPPoE 세션 이더넷 프레임에는 ETHER_TYPE 필드가 0x8864 값으로 설정되어 있습니다.