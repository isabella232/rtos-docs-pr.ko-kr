---
title: 3장 - 내부 서비스 캐시 설명
description: NetX Duo mDNS 모듈은 로컬 서비스 캐시와 피어 서비스 캐시 등, 두 가지 내부 서비스 캐시를 관리합니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 007f1080a076730cfbcdedc9f063ac0c427a414c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810729"
---
# <a name="chapter-3---description-of-internal-service-cache"></a>3장 - 내부 서비스 캐시 설명

NetX Duo mDNS 모듈은 로컬 서비스 캐시와 피어 서비스 캐시 등, 두 가지 내부 서비스 캐시를 관리합니다. 로컬 서비스 캐시는 노드에서 실행 중인 애플리케이션에서 제공하는 서비스와 관련한 리소스 레코드를 저장합니다. 들어오는 쿼리의 경우 질문이 제공된 서비스와 일치하면 mDNS가 로컬 서비스 캐시에 저장된 답변으로 응답합니다. 애플리케이션은 API *nx_mdns_service_add()* 를 호출하여 서비스를 등록합니다. 서비스를 제거하려면 애플리케이션이 API *nx_mdns_service_delete()* 를 사용합니다. 그러면 로컬 서비스 캐시에서 해당 항목을 제거하기 전에 "goodbye" 메시지를 보냅니다.

서비스가 추가되면 mDNS가 로컬 서비스 캐시에 SRV, PTR, TXT 등, 최소 3개의 리소스 레코드를 유지 관리합니다. 서비스 형식에 하위 형식이 포함된 경우 추가 PTR 리소스 레코드가 더해질 수 있습니다. 예를 들어 애플리케이션이 다음과 같이 서비스를 등록합니다.

```
*name*._*subtype*._sub._*type*._tcp.local,
```

두 PTR 리소스 레코드 두 개는 로컬 서비스 캐시에 추가됩니다. 한 개 -

```
“*_subtype._*sub*._type._*tcp.local *PTR name.type._*tcp*.*local”
```

및 다른 한 개 -

```
*“_type._*tcp*.*local *PTR name.type._*tcp*.*local”.
```

피어 서비스 캐시는 인접 노드에서 받은 mDNS 리소스 레코드를 포함합니다. mDNS 모듈은 네트워크의 다른 노드에서 알린 리소스 레코드를 수집하고, 수신한 정보를 피어 서비스 캐시에 저장합니다. 애플리케이션에서 호스트 IPv4 또는 IPv6 주소 등과 같은 정보를 쿼리하면 mDNS는 피어 서비스 캐시에서 로컬에 캐시된 응답을 검색합니다. 애플리케이션이 피어에서 제공되는 서비스를 쿼리하면 mDNS는 캐시에서 관련 PTR, SRV, TXT 및 IPv4/IPv6 주소 레코드를 검색합니다. 피어 서비스 캐시도 노드에 보낸 쿼리를 저장합니다. 예를 들어 애플리케이션이 *nx_mdns_service_one_shot_query* 를 호출하여 특정 서비스를 요청할 수 있습니다. 피어 서비스 캐시에 서비스가 없을 경우 mDNS는 피어 서비스 캐시에 쿼리 질문(PTR, SRV 및 TXT)을 만듭니다. 이러한 쿼리 질문은 서비스가 확인되거나 시간 초과될 때까지 정기적으로 네트워크에 보낼 수 있습니다. 마찬가지로 애플리케이션은 API *nx_mdns_service_continous_query()* 를 사용하여 장기간에 걸친 특정 서비스를 요청할 수 있습니다(애플리케이션이 API *nx_mdns_service_query_stop()* 을 사용하여 이전에 실행한 연속 쿼리 취소). 네트워크에 쿼리를 보내지 않고 피어 서비스 캐시에서 특정 서비스를 검색하기 위해 애플리케이션은 API *nx_mdns_serivce_lookup()* 을 사용할 수 있습니다. 이 API는 피어 서비스 캐시의 리소스 레코드만 검색합니다.

각 리소스 레코드는 서비스 캐시의 *NX_MDNS_RR* 데이터 구조에 저장됩니다. 리소스 레코드의 문자열은 가변 길이이므로 *NX_MDNS_RR* 구조에 저장되지 않습니다. 리소스 레코드에는 문자열이 저장된 실제 메모리 위치에 대한 포인터가 들어 있습니다. 문자열 테이블과 리소스 레코드는 서비스 캐시를 공유합니다. 리소스 레코드는 서비스 캐시 시작 부분에 저장되며 캐시 끝 방향으로 확장됩니다. 문자열 테이블은 서비스 캐시 끝에서 시작하여 캐시 시작 방향으로 확장됩니다. 문자열 테이블의 각 문자열에는 길이 필드와 카운터 필드가 포함됩니다. 문자열이 문자열 테이블에 추가될 때 테이블에 동일한 문자열이 이미 있으면 카운터 값이 증가하고 해당 문자열에 대해 메모리가 할당되지 않습니다. 서비스 캐시에 새 문자열 또는 그 이상의 리소스 레코드를 추가할 수 없으면 서비스 캐시가 가득 찬 것으로 간주됩니다.

애플리케이션은 두 가지 방법으로 로컬 네트워크에서 제공하는 서비스를 찾습니다. 일회용 쿼리를 통해 특정 서비스 조회를 실행하거나, 연속 쿼리를 시작하여 네트워크의 작업을 “모니터링”할 수 있습니다. 일회용 쿼리 시나리오에서는 애플리케이션이 서비스 형식을 지정해야 합니다. mDNS는 로컬 서비스 캐시와 피어 서비스 캐시를 검색합니다. 서비스 인스턴스를 찾은 경우 일회용 쿼리는 리소스 레코드에 있는 정보로 쿼리를 반환합니다. 로컬 서비스 캐시나 피어 서비스 캐시에 레코드가 없는 경우 mDNS는 쿼리 메시지를 내보냅니다. 인스턴스 이름을 지정한 경우 특정 인스턴스 이름을 갖는 *모든* 형식(SRV 및 TXT 형식 쿼리)이 "name.type.local" 형태로 로컬 네트워크로 전송됩니다. 인스턴스 이름을 지정하지 않으면 쿼리의 PTR 형식이 로컬 네트워크로 전송됩니다. 수신한 첫 번째 전체 서비스가 호출자에게 반환됩니다.

연속 쿼리는 다르게 작동합니다. 연속 쿼리의 일반적인 사용 사례는 로컬 네트워크에서의 특정 서비스 모니터링입니다(예: 로컬 네트워크에서 인쇄 서비스의 지속적인 검색). 이 경우 애플리케이션은 특정 서비스 형식에 대한 검색 쿼리를 실행합니다(API *nx_mdns_service_continious_* query 사용). 호출자는 일반적으로 특정 응답을 기다리지 않습니다. 연속 쿼리로 제출된 쿼리의 경우 mDNS 모듈은 지수로 늘어나는 간격으로 쿼리를 정기적으로 전송합니다. 쿼리를 중지하려면 애플리케이션이 API *nx_mdns_service_query_stop* 을 사용하여 해당 쿼리에서 내부 타이머를 중지해야 합니다. 쿼리 형식은 NULL이 될 수 있습니다. 이 경우 쿼리 형식이 특수 PTR 형식 “_services._dns-sd._udp.local”로 설정됩니다. 이 서비스 형식은 로컬 네트워크에서 사용할 수 있는 모든 서비스를 검색하기 위한 방법으로 mDNS에서 정의됩니다. 인스턴스 이름을 제공한 경우 특정 인스턴스 이름 “name.type.local”을 갖는 모든 형식(SRV 및 TXT 형식 쿼리)을 로컬 네트워크로 보냅니다. 인스턴스 이름이 NULL이면 쿼리의 PTR 형식이 로컬 네트워크로 전송됩니다.

원치 않는 쿼리의 응답을 비롯한 모든 응답은 피어 서비스 캐시에 기록됩니다. 나중에 애플리케이션이 API *nx_mdns_service_lookup* 을 사용하여 피어 서비스 캐시에서 특정 서비스를 검색합니다.

조각화 관련 특별 정보: 각 *NX_MDNS_RR* 구조는 크기가 고정이므로 mDNS의 RR 추가 및 삭제에 따른 조각화 대상이 아닙니다. 그러나 문자열은 가변 길이입니다. 문자열 삭제 후에는 해당 공간이 사용할 수 있게 되며, 부합하는 새 문자열이 있으면 해당 문자열에 사용할 수 있습니다. 그러나 이 작업에서는 메모리가 조각화됩니다. 서비스가 추가 및 제거되면 문자열 테이블이 조각화되어, 서비스 캐시에 사용하지 않은 문자열용 바이트가 충분히 있더라도 새 문자열을 추가하지 못할 수 있습니다. 로컬 애플리케이션이 보통 더 안정적이고 예측 가능합니다. 따라서 로컬 서비스 캐시에서는 조각화 문제가 발생할 가능성이 더 낮습니다. 반면 피어 서비스 캐시는 서비스가 사용할 수 있게 되면 지속적으로 RR을 추가하거나, 네트워크의 노드에서 서비스가 삭제되면 RR을 제거합니다. 네트워크에서 서비스가 들어오고 나가면 문자열 테이블에서 할당/삭제 작업이 더 빈번하게 일어납니다. 시간이 지날수록 문자열 테이블이 조각화될 수 있습니다. 이러한 상황이 발생했을 때 간단한 해결 방법은 전체 피어 서비스 캐시를 플러시하는 것입니다. API *nx_mdns_peer_cache_clear()* 를 호출하여 이 작업을 수행할 수 있습니다. 이 API는 처리 중인 연속 쿼리를 자동으로 종료합니다.