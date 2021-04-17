---
title: 3장 - NAT 구성 옵션
description: 다음 목록에는 모든 옵션과 해당 함수가 자세히 설명되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9c10d6f0d2f36d2794ab1229081799f0032cada8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810675"
---
# <a name="chapter-3---nat-configuration-options"></a>3장 - NAT 구성 옵션

NetX Duo NAT API에 대한 구성 가능한 옵션은 *nx_nat.c* 에서 찾을 수 있는 첫 번째 옵션인 **NX_DISABLE_ERROR_CHECKING** 을 제외하고 *nx_nat.h* 에서 찾을 수 있습니다. 다음 목록에는 모든 옵션과 해당 함수가 자세히 설명되어 있습니다.

- **NX_NAT_DISABLE_ERROR_CHECKING** 이 옵션이 정의된 경우 기본 NAT 오류 검사를 제거합니다. 일반적으로 애플리케이션이 디버깅된 후에 사용됩니다. 기본 NetX Duo NAT 상태가 정의됩니다(활성화).
- **NX_NAT_ENABLE_REPLACEMENT** 이 옵션이 정의된 경우 NAT 캐시가 가득 차면 자동 교체를 활성화합니다.
  > [!NOTE]
  > 가장 오래된 비 TCP 세션만 바꿉니다.
- **NX_NAT_MIN_ENTRY_COUNT** 이 옵션은 번역 항목의 최소 개수를 설정합니다. 기본 개수는 3입니다.
- **NX_NAT_TCP_SESSION_TIMEOUT** 이 옵션은 TCP 세션에 대한 변환 항목의 제한 시간을 설정합니다. 기본 시간 제한은 24시간입니다.
- **NX_NAT_NON_TCP_SESSION_TIMEOUT** 이 옵션은 비 TCP 세션에 대한 변환 항목의 제한 시간을 설정합니다. 기본 제한 시간은 240초입니다.
- **NX_NAT_START_TCP_PORT** 이 옵션은 사용하지 않는 TCP 포트를 검색하는 시작 값을 설정하여 아웃바운드 TCP 패킷을 할당합니다. 기본값은 20000입니다.
- **NX_NAT_END_TCP_PORT** 이 옵션은 TCP 포트의 상한을 설정하여 아웃바운드 TCP 패킷을 할당합니다. 기본값은 30000입니다.
- **NX_NAT_START_UDP_PORT** 이 옵션은 사용하지 않는 UDP 포트를 검색하는 시작 값을 설정하여 아웃바운드 UDP 패킷을 할당합니다. 기본값은 20000입니다.
- **NX_NAT_END_UDP_PORT** 이 옵션은 아웃바운드 UDP 패킷을 할당하도록 UDP 포트의 상한을 설정합니다. 기본값은 30000입니다.
- **NX_NAT_START_ICMP_QUERY_ID** 이 옵션은 사용하지 않는 쿼리 ID를 검색하는 시작 값을 설정하여 아웃바운드 ICMP 쿼리 패킷을 할당합니다. 기본값은 20000입니다.
- **NX_NAT_END_ICMP_QUERY_ID** 이 옵션은 아웃바운드 ICMP 쿼리 패킷을 할당할 쿼리 ID의 상한을 설정합니다. 기본값은 30000입니다.
