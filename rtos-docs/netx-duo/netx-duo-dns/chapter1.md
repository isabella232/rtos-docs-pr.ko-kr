---
title: 챕터 1 - Azure RTOS NetX Duo DNS 클라이언트 소개
description: DNS는 도메인 이름과 물리적 IP 주소 사이의 매핑을 포함하는 분산 데이터베이스를 제공합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4c07d6e3183d421c637874dcdeff3767554fca78
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810842"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-dns-client"></a>챕터 1 - Azure RTOS NetX Duo DNS 클라이언트 소개

DNS는 도메인 이름과 물리적 IP 주소 사이의 매핑을 포함하는 분산 데이터베이스를 제공합니다. 이 데이터베이스는 인터넷에서 전체 매핑을 포함하는 단일 엔터티가 없기 때문에 *분산* 이라고 부릅니다. 매핑 부분을 유지 관리하는 엔터티를 DNS 서버라고 부릅니다. 인터넷은 무수히 많은 DNS 서버들로 구성됩니다. 이러한 각 서버에는 데이터베이스 하위 집합이 포함되어 있습니다. 또한 DNS 서버는 서버에 요청된 매핑이 포함된 경우에만 도메인 이름 매핑 정보에 대한 DNS 클라이언트 요청에 응답합니다.

NetX Duo용 DNS 클라이언트 프로토콜은 하나 이상의 DNS 서버에서 매핑 정보를 요청하기 위해 애플리케이션에 서비스를 제공합니다.

## <a name="dns-client-setup"></a>DNS 클라이언트 설정

DNS 클라이언트 패키지가 제대로 작동하기 위해서는 NetX Duo IP 인스턴스가 이미 생성되어 있어야 합니다.

DNS 클라이언트를 만든 후 애플리케이션이 DNS 클라이언트에서 유지 관리되는 서버 목록에 하나 이상의 DNS 서버를 추가해야 합니다. DNS 서버를 추가하기 위해 애플리케이션은 *nxd_dns_server_add* 서비스를 사용합니다. NetX Duo DNS 클라이언트 서비스 *nx_dns_server_add* 를 사용하여 서버를 추가할 수도 있습니다. 그러나 IPv4 주소만 허용하므로 개발자가 *nxd_dns_server_add* 서비스를 대신 사용하는 것이 좋습니다.

NX_DNS_IP_GATEWAY_SERVER 옵션이 사용하도록 설정되었고, IP 인스턴스 게이트웨이 주소가 0이 아니면 IP 인스턴스 게이트웨이가 주 DNS 서버로 자동으로 추가됩니다. DNS 서버 정보가 정적으로 알려지지 않았으면 NetX Duo용 DHCP(Dynamic Host Configuration Protocol)를 통해 파생될 수도 있습니다. 자세한 내용은 NetX Duo DHCP 사용자 가이드를 참조하세요.

DNS 클라이언트에는 DNS 메시지를 전송하기 위한 패킷 풀이 필요합니다. 기본적으로 DNS 클라이언트는 *nx_dns_create* 서비스가 호출될 때 이 패킷 풀을 만듭니다. NX_DNS_PACKET_PAYLOAD_UNALIGNED 및 NX_DNS_PACKET_POOL_SIZE 구성 옵션을 통해 애플리케이션이 이 패킷 풀의 각 패킷 페이로드 및 패킷 풀 크기(예: 패킷 수)를 확인할 수 있습니다. 이러한 옵션에 대해서는 챕터 2의 “구성 옵션” 섹션에 설명되어 있습니다.

고유 패킷 풀을 만드는 DNS 클라이언트에 대한 대안은 애플리케이션이 패킷 풀을 만들고 *nx_dns_packet_pool_set* 서비스를 사용하여 DNS 클라이언트의 패킷 풀로 설정하도록 하는 것입니다. 이렇게 하려면 NX_DNS_CLIENT_USER_CREATE_PACKET_POOL 옵션을 정의해야 합니다. 또한 이 옵션에서는 *nx_packet_pool_create* 를 *nx_dns_packet_pool_set* 에 대한 패킷 풀 포인터 입력으로 사용하여 이전에 생성된 패킷 풀이 필요합니다. DNS 클라이언트 인스턴스가 삭제되면 NX_DNS_CLIENT_USER_CREATE_PACKET_POOL을 사용하도록 설정된 경우 더 이상 필요하지 않을 때 애플리케이션이 DNS 클라이언트 패킷 풀 삭제를 담당합니다.

> [!NOTE] 
> NX_DNS_CLIENT_USER_CREATE_PACKET_POOL 옵션을 사용하여 고유 패킷 풀을 제공하도록 선택하는 애플리케이션의 경우 UDP 헤더, IPv4 또는 IPv6 헤더 및 MAC 헤더를 위한 공간을 포함하여 DNS 최대 메시지 크기(512바이트)를 저장할 수 있는 패킷 크기가 필요합니다.

## <a name="dns-messages"></a>DNS 메시지

DNS에는 호스트 이름과 IP 주소 사이에 매핑을 얻기 위한 매우 간단한 메커니즘이 있습니다. 매핑을 얻기 위해 DNS 클라이언트는 확인해야 하는 이름 또는 IP 주소가 포함된 DNS 쿼리 메시지를 준비합니다. 그런 후 서버 목록에서 첫 번째 DNS 서버에 메시지가 전송됩니다. 서버에 이러한 매핑이 있으면 요청된 매핑 정보가 포함된 DNS 응답 메시지를 사용하여 DNS 클라이언트에 회신합니다. 서버가 응답하지 않으면 모든 DNS 서버에 쿼리가 수행될 때까지 DNS 클라이언트가 목록에 있는 다음 서버에 쿼리를 수행합니다. 모든 DNS 서버에서 응답이 수신되지 않을 경우 DNS 클라이언트는 재시도 논리를 사용하여 DNS 메시지를 다시 전송합니다. DNS 쿼리를 다시 보낼 때는 재전송 시간 제한이 두 배가 됩니다. 이 프로세스는 최대 전송 시간 제한(*nxd_dns.h* 에서 NX_DNS_MAX_RETRANS_TIMEOUT으로 정의됨)에 도달하거나 서버로부터 성공 응답이 수신될 때까지 계속됩니다.

NetX Duo DNS 클라이언트는 *nxd_dns_host_by_name_get* 호출에 IP 주소 버전을 지정하여 IPv6 주소 조회(AAAA 유형) 및 IPv4 주소 조회(유형 A)를 모두 수행할 수 있습니다. DNS 클라이언트는 *nxd_dns_host_by_address_get* 을 사용하여 웹 호스트 이름을 가져오기 위해 IP 주소의 역방향 조회(PTR 형식 쿼리)를 수행할 수 있습니다. NetX Duo DNS 클라이언트는 동일한 서비스이지만 IPv4 네트워크 통신으로 제한되는 *nx_dns_host_by_name_get* 및 *nx_dns_host_by_address_get* 도 지원합니다. 그러나 개발자는 기존 DNS 클라이언트 애플리케이션을 *nxd_dns_host_by_name_get* 및 *nxd_dns_host_by_address_get* 서비스로 이동하는 것이 좋습니다.

DNS 메시징은 UDP 프로토콜을 사용하여 요청 및 필드 응답을 보냅니다. DNS 서버는 클라이언트의 쿼리에 대해 포트 번호 53에서 수신 대기합니다. 따라서 이전에 생성된 IP 인스턴스(_*_nx_ip_create_**)에서 ***nx_udp_enable** _ 서비스를 사용하여 NetX Duo에 UDP 서비스가 사용하도록 설정되어 있어야 합니다.

이제 DNS 클라이언트가 애플리케이션에서 요청을 수락하고 DNS 쿼리를 보낼 준비가 되었습니다.

## <a name="extended-dns-resource-record-types"></a>확장된 DNS 리소스 레코드 형식

NX_DNS_ENABLE_EXTENDED_RR_TYPES가 사용하도록 설정된 경우 NetX Duo DNS 클라이언트는 다음 레코드 형식 쿼리도 지원합니다.

- CNAME: 별칭의 표준 형식 이름을 포함합니다.
- TXT: 텍스트 문자열을 포함합니다.
- NS: 권한이 있는 이름 서버를 포함합니다.
- SOA: 권한 영역의 시작을 포함합니다.
- MX: 메일 교환에 사용됩니다.
- SRV: 도메인에서 제공되는 서비스에 대한 정보를 포함합니다.

CNAME 및 TXT 레코드 형식을 제외하고 DNS 데이터 레코드를 수신하기 위해 애플리케이션이 4바이트로 정렬된 버퍼를 제공해야 합니다.

NetX Duo DNS 클라이언트에서 레코드 데이터는 버퍼 공간을 가장 효율적으로 사용할 수 있는 방식으로 저장됩니다.

고정 길이(AAAA 레코드 유형)의 레코드 버퍼 예제는 다음과 같습니다.

![고정 길이의 레코드 버퍼](media/image2.png)

호스트 이름이 가변 길이인 NS 레코드와 같이 레코드 형식에 가변 데이터 길이가 포함된 쿼리의 경우 NetX Duo DNS 클라이언트가 데이터를 다음과 같이 저장합니다. DNS 클라이언트 쿼리에 제공된 버퍼는 고정 길이 데이터 영역과 비구조적 메모리 영역으로 구성됩니다. 메모리 버퍼 위쪽은 4바이트로 정렬된 레코드 항목으로 구성됩니다. 각 레코드 항목에는 IP 주소와 해당 IP 주소의 가변 길이 데이터에 대한 포인터가 포함됩니다. 각 IP 주소의 가변 길이 데이터는 메모리 버퍼 끝에서 시작하는 비구조적 영역 메모리에 저장됩니다. 연속된 각 레코드 항목의 가변 길이 데이터는 이전 레코드 항목 가변 데이터에 인접한 다음 영역 메모리에 저장됩니다. 따라서 다른 레코드 항목 및 가변 데이터를 저장하기에 메모리가 부족해질 때까지 레코드 항목을 포함하는 메모리의 구조적 영역으로 가변 데이터가 ‘증가’합니다.

이는 아래 그림과 같습니다.

![그림 2](media/image3.png)

DNS 도메인 이름(NS) 데이터 스토리지의 예는 위에 나와 있습니다.

레코드 스토리지 형식을 사용하는 NetX Duo DNS 클라이언트 쿼리는 레코드 버퍼에 저장된 레코드 수를 반환합니다. 이 정보에 따라 애플리케이션이 레코드 버퍼에서 NS 레코드를 추출할 수 있습니다.

이 레코드 스토리지 형식을 사용하여 가변 길이 DNS 데이터를 저장하는 DNS 클라이언트 쿼리 예제는 다음과 같습니다.

```C
UINT  _nx_dns_domain_name_server_get(NX_DNS *dns_ptr, 
                    UCHAR *host_name, VOID *record_buffer, 
                    UINT buffer_size, UINT *record_count, 
                    ULONG wait_option);
```


자세한 내용은 챕터 3 “DNS 클라이언트 서비스 설명”을 참조하십시오.

## <a name="dns-cache"></a>DNS 캐시

NX_DNS_CACHE_ENABLE이 사용하도록 설정된 경우 NetX Duo DNS 클라이언트가 DNS 캐시 기능을 지원합니다. DNS 클라이언트를 만든 후 애플리케이션이 API *nx_dns_cache_initialize()* 를 호출하여 특별한 DNS 캐시를 설정할 수 있습니다. DNS 캐시 기능을 사용하도록 설정하면 DNS 클라이언트가 DNS 쿼리 전송을 시작하기 전 DNS 캐시에서 사용 가능한 답변을 찾을 수 있습니다. 사용 가능한 답변을 찾으면 애플리케이션에 답변을 직접 반환하고, 그렇지 않으면 DNS 클라이언트가 DNS 서버에 쿼리 메시지를 보내고 회신을 기다립니다. DNS 클라이언트가 응답 메시지를 가져오고 사용 가능한 캐시가 있으면 DNS 클라이언트가 답변을 애플리케이션에 반환하고 DNS 캐시에도 리소스 레코드로 답변을 추가합니다.

각 항목은 캐시의 데이터 구조 *NX_DNS_RR*(리소스 레코드)에 답변합니다. 레코드의 문자열(리소스 레코드 이름 및 데이터)는 가변 길이이므로 NX_DNS_RR 구조에 저장되지 않습니다. 레코드에는 문자열이 저장되는 실제 메모리 위치에 대한 포인터가 포함됩니다. 문자열 테이블 및 레코드는 캐시를 공유합니다. 레코드는 캐시 시작 부분에서 저장되며 캐시 끝을 향해 증가합니다. 문자열 테이블은 캐시 끝에서 시작하여 캐시 시작 부분을 향해 증가합니다. 문자열 테이블의 각 문자열에는 길이 필드와 카운터 필드가 포함됩니다. 문자열이 문자열 테이블에 추가될 때 테이블에 동일한 문자열이 이미 있으면 카운터 값이 증가하고 해당 문자열에 대해 메모리가 할당되지 않습니다. 캐시에 새 문자열 또는 그 이상의 리소스 레코드를 추가할 수 없으면 캐시가 가득 찬 것으로 간주됩니다.

## <a name="dns-client-limitations"></a>DNS 클라이언트 제한 사항

DNS 클라이언트는 한 번에 하나의 DNS 요청을 지원합니다. 다른 DNS 요청을 수행하려고 시도하는 스레드는 이전 DNS 요청이 완료될 때까지 일시적으로 차단됩니다.

NetX Duo DNS 클라이언트는 정식 답변의 데이터를 사용하여 추가 DNS 쿼리를 다른 DNS 서버로 전달하지 않습니다.

## <a name="dns-rfcs"></a>DNS RFC

NetX Duo DNS는 다음 RFC와 호환됩니다.

- RFC1034 도메인 이름 - 개념 및 기능
- RFC1035 도메인 이름 - 구현 및 사양
- RFC1480 미국 도메인
- RFC 2782 서비스 위치를 지정하기 위한 DNS RR(DNS SRV)
- RFC 3596 IP 버전 6을 지원하는 DNS 확장