---
title: 2장 - mDNS의 설치 및 사용
description: 이 장에서는 NetX Duo mDNS 모듈의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b27671f82c100db4e6a70a568e8a68f14b3ab45e3a33f46dd1f2e1852010f500
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796432"
---
# <a name="chapter-2---installation-and-use-of-mdns"></a>2장 - mDNS의 설치 및 사용

이 장에서는 NetX Duo mDNS 모듈의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

NetX Duo mDNS는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 사용할 수 있습니다. 패키지에는 다음과 같이 이 문서를 포함하는 두 개의 원본 파일과 PDF 파일이 포함되어 있습니다.

- **nxd_mdns.h** NetX Duo mDNS 모듈에 대한 헤더 파일
- **nxd_mdns.c** NetX Duo mDNS 모듈에 대한 C 원본 파일
- **nxd_mdns.pdf** NetX Duo용 mDNS에 대한 PDF 설명
- **demo_netxduo_mdns.c** mDNS에서 제공하는 서비스를 보여 주는 간단한 데모 프로그램

## <a name="netx-duo-mdns-installation"></a>NetX Duo mDNS 설치

NetX Duo mDNS API를 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX Duo가 “*c:\netxduo*” 디렉터리에 설치된 경우 *nxd_mdns.h* 및 *nxd_mdns.c* 를 이 디렉터리에 복사해야 합니다.

## <a name="using-netx-duo-mdns"></a>NetX Duo mDNS 사용

NetX Duo mDNS 모듈을 사용하는 것은 쉽습니다. 기본적으로 ThreadX 및 NetX Duo를 각각 사용하기 위해 애플리케이션 코드는 *tx_api.h 및* *nx_api.h* 를 포함한 후, *nxd_mdns.h* 를 포함해야 합니다. 빌드 프로젝트는 mDNS 소스 코드와 애플리케이션 파일, ThreadX 및 NetX 라이브러리 파일을 포함해야 합니다. 이렇게 간단하게 NetX Duo mDNS를 사용할 수 있습니다.

## <a name="configuration-options"></a>구성 옵션

NetX Duo mDNS 모듈을 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 기본값이 나열되어 있지만, 각 정의는 지정된 NetX Duo mDNS 헤더 파일을 포함하기 전에 애플리케이션에서 설정할 수 있습니다. 다음 목록에서 각각에 대해 자세히 설명합니다.

- **NX_MDNS_DISABLE_SERVER** mDNS/DNS-SD 서버 기능을 사용하지 않도록 설정합니다. 서버 기능을 사용하지 않으면 mDNS/DNS-SD 모듈은 로컬 호스트에서 제공하는 서비스를 알리지 않으며 mDNS 문의에도 응답하지 않습니다. 이 기호는 기본적으로 정의되어 있지 않습니다.
- **NX_MDNS_DISABLE_CLIENT** mDNS/DNS-SD 클라이언트 기능을 사용하지 않도록 설정합니다. 클라이언트 기능이 없으면 mDNS/DNS-SD는 쿼리를 전송하지 않으며 네트워크를 통해 받은 mDNS 쿼리 응답을 유지하지 않습니다.
- **NX_MDNS_ENABLE_ADDRESS_CHECK** 정의된 경우, mDNS 모듈은 받은 mDNS 메시지에서 주소(원본 주소, 대상 주소 및 포트 번호)의 유효성 검사를 수행합니다. 이 기호는 기본적으로 정의되어 있습니다.
- **NX_MDNS_ENABLE_CLIENT_POOF** 정의된 경우, mDNS 모듈은 오류에 대한 수동 관찰을 수행하고, mDNS/DNS_SD 클라이언트(쿼리자)는 네트워크의 다른 호스트에서 발급한 멀티 캐스트 쿼리를 관찰합니다. 이 기호는 기본적으로 정의되어 있습니다.
- **NX_MDNS_ENABLE_SERVER_NEGATIVE_RESPONSES** 정의된 경우 mDNS/DNS-SD 서버(응답자)는 합법적인 소유권이 있는 쿼리에 대해 부정 응답을 생성합니다. 이 기호는 기본적으로 정의되어 있습니다.
- **NX_MDNS_ENABLE_IPV6** 정의된 경우 mDNS/DNS-SD는 IPv6 주소를 통해 mDNS 메시지를 송신/처리합니다. 이 기호는 기본적으로 정의되어 있지 않습니다.
- **NX_MDNS_IPV6_ADDRESS_COUNT** 호스트의 최대 IPv6 주소 수입니다. 기본값은 2입니다.
- **NX_MDNS_HOST_NAME_MAX** 호스트 이름에 대한 최대 문자열 크기입니다. 기본값은 64입니다. NULL 종결자를 포함하지 않습니다.
- **NX_MDNS_SERVICE_NAME_MAX** 서비스 이름에 대한 최대 문자열 크기입니다. 기본값은 64입니다. NULL 종결자를 포함하지 않습니다.
- **NX_MDNS_DOMAIN_NAME_MAX** 도메인 이름에 대한 최대 문자열 크기입니다. 기본값은 16입니다. NULL 종결자를 포함하지 않습니다.
- **NX_MDNS_CONFLICT_COUNT** 호스트 이름 또는 서비스 이름에 대한 최대 충돌 횟수입니다. 기본값은 8입니다.
- **NX_MDNS_RR_TTL_HOST** 호스트 이름이 포함된 리소스 레코드에 대한 TTL 값(초)입니다. 기본값은 120초에 해당하는 120입니다.
- **NX_MDNS_RR_TTL_OTHER** 다른 리소스 레코드에 대한 TTL 값(초)입니다. 기본값은 75분에 해당하는 4500입니다.
- **NX_MDNS_PROBING_TIMER_COUNT** mDNS 프로빙 메시지 간 시간 간격(틱)입니다. 기본값은 250ms에 해당하는 25틱입니다.
- **NX_MDNS_ANNOUNCING_TIMER_COUNT** mDNS 공지 메시지 간 시간 간격(틱)입니다. 기본값은 250ms에 해당하는 25틱입니다.
- **NX_MDNS_GOODBYE_TIMER_COUNT** 반복된 “goodbye” 메시지 간 시간 간격(틱)입니다. 기본값은 250ms에 해당하는 25틱입니다.
- **NX_MDNS_QUERY_MIN_TIMER_COUNT** 두 쿼리 사이의 최소 시간 간격(틱)입니다. 기본값은 1초에 해당하는 100틱입니다.
- **NX_MDNS_QUERY_MAX_TIMER_COUNT** 두 쿼리 사이의 최대 시간 간격(틱)입니다. 기본값은 60초에 해당하는 360000입니다.
- **NX_MDNS_QUERY_DELAY_MIN** 첫 번째 쿼리 전송에 대한 최소 지연(틱)입니다. 기본값은 20ms에 해당하는 2틱입니다.
- **NX_MDNS_QUERY_DELAY_RANGE** 첫 번째 쿼리 전송에 대한 지연 범위(틱)입니다. 기본값은 100ms에 해당하는 10틱입니다.
- **NX_MDNS_RESPONSE_INTERVAL** 마지막으로 레코드가 멀티캐스트된 후 시간 간격을 1s로 이상으로 유지하기 위해 쿼리에 응답하는 시간 간격(틱)입니다. 기본값은 100틱입니다.
- **NX_MDNS_RESPONSE_PROBING_TIMER_OUT** 마지막으로 레코드가 멀티캐스트된 후 간격을 250ms로 이상으로 유지하기 위해 프로브 쿼리에 응답하는 시간 간격(틱)입니다. 기본값은 25틱입니다.
- **NX_MDNS_RESPONSE_UNIQUE_DELAY** 로컬 네트워크에 고유한 서비스에 대한 쿼리에 응답하는 지연 시간(틱)입니다. 기본값은 10ms에 해당하는 1틱입니다.
- **NX_MDNS_RESPONSE_SHARED_DELAY_MIN** 공유 리소스에 대한 쿼리에 응답하는 최소 지연 시간(틱)입니다. 기본값은 20ms에 해당하는 2틱입니다.
- **NX_MDNS_RESPONSE_SHARED_DELAY_RANGE** 공유 리소스에 대한 쿼리에 응답하는 지연 시간(틱)입니다. 기본값은 100ms에 해당하는 10틱입니다.
- **NX_MDNS_RESPONSE_TC_DELAY_MIN** TC 비트를 사용한 쿼리에 응답하는 최소 지연 시간(틱)입니다. 기본값은 400ms에 해당하는 40틱입니다.
- **NX_MDNS_RESPONSE_TC_DELAY_RANGE** TC 비트를 사용한 쿼리에 응답하는 지연 시간(틱)입니다. 기본값은 100ms에 해당하는 10틱입니다.
- **NX_MDNS_TIMER_COUNT_RANGE** mDNS 응답을 전송할 때 패킷에는 이 타이머 카운터 범위 내에서 다른 방법으로 전송되는 응답이 포함되어 있습니다. 타이머 수 범위는 틱으로 표현됩니다. 기본값은 120ms에 해당하는 12입니다. 이 값을 사용하면 각 틱이 10ms인 경우 다음 120ms 범위 내에 전송되는 메시지를 응답에 포함할 수 있습니다.
- **NX_MDNS_PROBING_RETRANSMIT_COUNT** 재전송된 프로빙 메시지 수입니다. 기본값은 3입니다.
- **NX_MDNS_GOODBYE_RETRANSMIT_COUNT** 재전송된 “goodbye” 메시지 수입니다. 기본값은 1입니다.
- **NX_MDNS_POOF_MIN_COUNT** 멀티캐스트 응답이 없는 쿼리 수로, 호스트에서는 레코드가 더 이상 유효하지 않을 수 있음을 나타내는 표시로 받아들일 수 있습니다. 기본값은 2입니다.
- **NX_MDNS_POOF_TIME_COUNT** 두 개 이상의 쿼리를 확인한 후 캐시에서 레코드를 삭제하는 시간과 예상되는 대답을 포함하는 멀티캐스트 응답을 확인하는 시간 간격(틱)입니다. 기본값은 10초에 해당하는 1000틱입니다.
- **NX_MDNS_RR_DELETE_DELAY_TIMER_COUNT** 이 레코드의 TTL이 0일 때 리소스 레코드 삭제에 대한 지연 시간(틱)입니다. 기본값은 1초에 해당하는 100틱입니다.
