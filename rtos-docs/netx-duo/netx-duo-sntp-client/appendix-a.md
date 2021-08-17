---
title: 부록 A - Azure RTOS NetX Duo SNTP 치명적인 오류 코드
description: 다음 오류 코드로 인해 Azure RTOS NetX Duo SNTP 클라이언트가 현재 서버와의 시간 업데이트를 중단합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e0152c1342b3edffd42f7442c51e7c5d62b199a5b38085dac06b4c0dbee9e9a8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790108"
---
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a>부록 A - Azure RTOS NetX Duo SNTP 치명적인 오류 코드

다음 오류 코드로 인해 Azure RTOS NetX Duo SNTP 클라이언트가 현재 서버와의 시간 업데이트를 중단합니다. 애플리케이션은 SNTP 클라이언트의 사용 가능한 서버 목록에서 현재 서버를 제거할지 결정하거나 서버 목록의 사용 가능한 다음 서버로 전환합니다. 각 오류 상태의 정의는 *nxd_sntp_client.h에 정의되어 있습니다. *

SNTP 클라이언트가 아래 목록의 오류를 애플리케이션으로 반환하면 서버를 다른 서버로 바꿔야 합니다. NX_SNTP_KOD_REMOVE_SERVER 오류 상태는 SNTP 클라이언트 KOD(Kiss of Death) 처리기(콜백 함수)에 표시되어 다음을 설정합니다.

- NX_SNTP_KOD_REMOVE_SERVER 0xD0C  
- NX_SNTP_SERVER_AUTH_FAIL 0xD0D  
- NX_SNTP_INVALID_NTP_VERSION 0xD11  
- NX_SNTP_INVALID_SERVER_MODE 0xD12  
- NX_SNTP_INVALID_SERVER_STRATUM 0xD15  

SNTP 클라이언트가 아래 목록의 오류를 애플리케이션으로 반환하면 서버가 일시적으로 유효한 시간 업데이트를 제공하지 못할 수 있지만 서버를 제거할 필요는 없습니다.

- HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09  
- NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B  
- NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17  
- NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16  
- NX_SNTP_INVALID_RTT_TIME 0xD21  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24