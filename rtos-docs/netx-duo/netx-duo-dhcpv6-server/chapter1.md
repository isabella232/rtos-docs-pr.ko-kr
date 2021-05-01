---
title: 챕터 1 - Azure RTOS NetX Duo DHCPv6 서버 소개
description: 이 문서에서는 NetX Duo DHCPv6 서버에서 IPv6 주소를 DHCPv6 클라이언트에 할당하는 방법에 대해 자세히 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6cf7baa91b1804876b97b1d75d1872d1120ad028
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810860"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-server"></a>챕터 1 - Azure RTOS NetX Duo DHCPv6 서버 소개

IPv6 네트워크에서 DHCPv6은 클라이언트에서 IPv6 주소를 가져오는 데 필요합니다. IPv4 주소를 제공하지 않는다는 점에서 IPv4로 제한된 DHCP를 대체하지 않습니다. DHCPv6에는 DHCP와 비슷한 기능과 향상된 많은 기능이 있습니다. IPv6 상태 비저장 주소 자동 구성을 사용하지 않거나 사용할 수 없는 클라이언트는 DHCPv6을 사용하여 DHCPv6 서버에서 고유한 전역 IPv6 주소를 할당받을 수 있습니다.

NetX Duo는 IPv6 네트워크 기반 애플리케이션 및 DHCPv6과 같은 네트워크 프로토콜을 지원하기 위해 개발되었습니다. 이 문서에서는 NetX Duo DHCPv6 서버에서 IPv6 주소를 DHCPv6 클라이언트에 할당하는 방법에 대해 자세히 설명합니다.

## <a name="dhcpv6-communication"></a>DHCPv6 통신

**DHCPv6 메시지 구조**

메시지 콘텐츠에는 기본적으로 메시지 헤더 뒤에 하나 이상의(일반적으로 더 많은) 옵션 블록이 있습니다. 각 블록이 1바이트를 나타내는 기본 구조는 다음과 같습니다.

![DHCPv6 메시지 및 옵션 블록 구조를 보여 주는 다이어그램](media/image2.jpg)

**그림 1. DHCPv6 메시지 및 옵션 블록 구조**

1바이트 메시지 유형 필드는 DHCPv6 메시지 유형을 나타냅니다. 3바이트 트랜잭션 ID 필드는 클라이언트에서 설정합니다. 이는 임의의 문자 시퀀스일 수 있지만 서버에 대한 각 클라이언트 메시지에 대해 고유해야 합니다(클라이언트에서 보낸 중복 메시지에서 보존됨). 서버는 클라이언트에 대한 각 응답에 대해 해당 트랜잭션 ID를 사용하여 패킷이 네트워크에서 지연되거나 삭제되는 경우 클라이언트에서 서버 메시지를 일치시킬 수 있도록 합니다. 트랜잭션 ID 필드 다음에는 클라이언트에서 요청하는 항목을 표시하는 데 사용되는 하나 이상의 DHCPv6 옵션이 있습니다.

DHCPv6 옵션 구조는 옵션 코드, 옵션 길이 필드(길이 또는 코드 필드를 포함하지 않음), 마지막으로 옵션 데이터 자체(클라이언트에서 요청하는 데이터에 대한 하나 이상의 2바이트 옵션 코드 필드)로 구성됩니다.

일부 옵션 블록에는 중첩된 옵션이 있습니다. 예를 들어 *IANA(비임시 주소에 대한 ID 연결)* 옵션에는 IPv6 주소를 요청하는 하나 이상의 *IA(ID 연결)* 옵션이 포함되어 있습니다. 서버 응답 메시지에 반환된 *IANA* 옵션에는 서버에서 부여한 IPv6 주소 및 임대 시간과 동일한 *IA* 옵션과 클라이언트 주소 요청에 오류가 있는지 여부를 나타내는 *상태* 옵션이 포함되어 있습니다.

모든 옵션 블록의 목록 및 해당 설명은 **부록 A** 에 나와 있습니다.

**DHCPv6 메시지 유형**

DHCPv6은 DHCP의 기능을 크게 향상시키지만 DHCP와 동일한 수의 메시지를 사용하며 DHCP와 동일한 공급업체 옵션을 지원합니다. DHCPv6 메시지 목록은 다음과 같습니다.

- SOLICT (1)(클라이언트에서 보냄)
- ADVERTISE (2)(서버에서 보냄)
- REQUEST (3)(클라이언트에서 보냄)
- REPLY (7)(서버에서 보냄)
- CONFIRM (4)(클라이언트에서 보냄)(클라이언트에서 보냄)
- RENEW (5)(클라이언트에서 보냄)
- REBIND (6)(클라이언트에서 보냄)
- RELEASE (8)(클라이언트에서 보냄)
- DECLINE (9)(클라이언트에서 보냄)
- INFORM_REQUEST (11)(클라이언트에서 보냄)
- RECONFIGURE* (10)(서버에서 보냄)

*RECONFIGURE는 NetX Duo DHCPv6 서버에서 지원되지 않습니다.

괄호 안에 동등한 DHCPv4 메시지 유형이 있는 기본 DHCPv6 요청 시퀀스는 다음과 같습니다.

클라이언트 ***간청** _ (_검색 *) 서버 **보급 알림** (* 제안 *) 클라이언트 **요청** (* 요청 *) 서버 **회신** (* DHCPAck*)

클라이언트 **갱신**(동일함) 서버 **회신** (*DHCPAck*)

## <a name="dhcpv6-message-validation"></a>DHCPv6 메시지 유효성 검사

트랜잭션 ID: 클라이언트에서 서버에 보내는 각 메시지에 대해 트랜잭션 ID를 생성해야 합니다. DHCPv6 서버는 이 트랜잭션 ID와 일치하지 않는 클라이언트의 메시지를 거부합니다. 서버는 클라이언트에 반환하는 응답에서 동일한 트랜잭션 ID를 사용해야 합니다.

**DUID(DHCPv6 고유 식별자)**

모든 서버 메시지도 각 메시지에 DUID(DHCPv6 고유 식별자)를 포함해야 합니다. 그렇지 않으면 DHCPv6 클라이언트에서 메시지를 수락하지 않아야 합니다. LL(링크 계층) DUID는 클라이언트 MAC 주소, 하드웨어 유형 및 DUID 유형을 포함하는 제어 블록입니다. LLT(링크 계층 시간) DUID는 호스트 네트워크에서 DUID가 고유하지 않을 가능을 줄이는 시간 필드를 추가로 포함합니다. 이러한 이유로 RFC 3315는 LL DUID보다 LLT DUID를 권장합니다. 호스트 애플리케이션에서 고유한 시간 값을 만들지 않는 경우 NetX Duo DHCPv6에서 기본 시간 값을 제공합니다. 세 번째 유형의 DUID는 엔터프라이즈 ID(IANA에 등록된 경우와 동일) 및 프라이빗 데이터(예를 들어 메모리 크기, 기타 하드웨어 구성의 운영 체제 유형에 따라 형식과 길이가 달라짐)를 포함하는 엔터프라이즈(공급업체 할당) DUID입니다. 서버 공급업체 할당 및 프라이빗 ID 값을 설정하려면 이 문서의 다른 부분에 있는 구성 옵션 목록을 참조하세요.

또한 클라이언트는 INFORM_REQUEST를 제외하고는 서버에 보내는 메시지에 DUID를 포함해야 합니다. 그렇지 않으면 서버에서 메시지를 거부합니다.

**DHCPv6 클라이언트 서버 세션**

DHCPv6 클라이언트와 서버는 UDP를 통해 메시지를 교환합니다. 클라이언트는 546 포트를 사용하여 DHCPv6 메시지를 보내고 받고, 서버는 547 포트를 사용합니다. 클라이언트는 처음에 링크-로컬 주소를 사용하여 DHCPv6 메시지를 보내고 받습니다. *All_DHCP_Relay_Agents_and_Servers* 멀티캐스트 주소 *(FF02::01:02)* 로 알려진 예약된 링크 범위 멀티캐스트 주소를 사용하여 모든 메시지를 DHCPv6 서버에 보냅니다.

IPv6 주소 할당 요청의 경우 DHCPv6 서버는 *All_DHCP_Relay_Agents_and_Servers* 주소로 보내는  *간청* 메시지를 수신 대기합니다. *간청* 요청에서 클라이언트는 특정 IPv6 주소를 할당하도록 요청하거나 서버에서 하나를 선택하도록 할 수 있습니다. 또한 서버에서 다른 네트워크 구성 정보를 요청할 수도 있습니다.

DHCPv6 서버에서 유효한 *간청* 메시지를 추출하고 IPv6 주소를 클라이언트에 할당할 수 있는 경우 클라이언트에 부여할 IPv6 주소, IPv6 주소 임대 시간 및 클라이언트에서 요청한 추가 정보가 포함된 *보급* 메시지를 사용하여 응답합니다. 클라이언트에서 서버 제안을 수락하는 경우 해당 클라이언트는 서버에서 IPv6 주소를 수락하는 것을 인식할 수 있도록 하는 *요청* 메시지를 사용하여 응답합니다. 서버는 클라이언트가 *회신* 메시지를 사용하여 IPv6 주소에 바인딩되었는지 확인합니다.

클라이언트 DHCPv6 메시지가 잘못된 경우 서버에서 메시지를 자동으로 삭제합니다. 서버에서 요청을 허용할 수 없는 경우 IP 주소 IANA 옵션의 상태 필드에 문제를 표시하는 *회신* 메시지를 보냅니다. 중복 클라이언트 요청을 받으면 서버는 클라이언트에서 단순히 패킷을 받지 않았다고 가정하고 이전 DHCPv6 응답을 다시 보냅니다.

클라이언트는 중복 주소 검색과 같은 다양한 IPv6 프로토콜을 사용하여 서버에서 할당된 IPv6 주소가 시스템의 다른 호스트에 할당되지 않았는지 확인해야 합니다. 주소가 고유하지 않은 경우 클라이언트에서 *거부* 메시지를 서버에 보냅니다. 서버는 IP 임대 테이블을 이 정보로 업데이트하여 주소가 이미 할당되었음을 기록합니다. 한편 클라이언트는 다른 *간청* 메시지를 사용하여 DHCPv6 요청 프로세스를 다시 시작해야 합니다.

클라이언트는 IPv6 주소 외에도 DNS 서버 및 네트워크 도메인 이름과 같은 다른 네트워크 정보도 인식해야 합니다. DHCPv6은 *간청* 및 *요청* 메시지에서 옵션 요청을 사용하거나 별도로 *정보 요청* 메시지에서 옵션 요청을 사용하여 이 정보를 요청하는 방법을 제공합니다. DHCPv6 옵션은 이 챕터의 뒷부분에서 설명합니다.

**IPv6 임대 기간**

서버에서 IPv6 주소를 클라이언트에 부여하는 경우 클라이언트에서 *갱신* 및 *리바인딩* 메시지를 사용하여 해당 IPv6 주소를 갱신(T1) 또는 리바인딩(T2)하도록 권장하는 시점에 대한 임대 기간(수명)도 IANA 옵션에 할당합니다. 둘 사이의 차이점은 클라이언트에서 서버 DUID를 *갱신* 요청에 포함하여 *갱신* 메시지를 서버에 보낸다는 것입니다. 그러나 서버를 지정하지 않으므로 서버 DUID가 *All_DHCP_Relay_Agents_and_Servers* 주소에 대한 *리바인딩* 메시지에 포함되지 않습니다. 서버에서 클라이언트에 부여하는 실제 IPv6 주소를 포함하는 IA 옵션에는 임대된 IPv6 주소가 각각 더 이상 사용되지 않거나 더 이상 사용되지 않거나 쓸모없는(유효하지 않은) 경우에도 기본 설정 및 유효 수명이 포함됩니다.

NetX Duo DHCPv6 서버는 클라이언트 메시지 간의 시간을 추적하기 위해 각 클라이언트의 세션 시간 제한을 유지합니다. 이는 클라이언트 호스트의 연결이 끊기거나 네트워크 작동이 중단되는 경우에 필요합니다. 세션 시간 제한이 만료되면 클라이언트에서 더 이상 관심이 없거나 서버의 DHCPv6 요청을 수행할 수 있다고 가정합니다. 서버는 클라이언트 레코드를 삭제하고 임시로 할당된 IPv6 주소를 사용 가능한 풀로 다시 반환합니다. 세션 시간 제한 대기는 사용자가 구성할 수 있는 옵션입니다.

클라이언트에서 IPv6 주소를 해제하려고 하거나 DHCPv6 서버에서 할당한 IPv6 주소가 이미 사용되고 있음을 검색하는 경우 각각 *릴리스* 또는 *거부* 메시지를 보냅니다. *릴리스* 메시지의 경우 서버는 해당 IPv6 주소 상태를 사용 가능한 풀로 다시 반환합니다. *거부* 메시지의 경우 해당 IP 임대 테이블을 업데이트하여 이 IPv6 주소를 사용할 수 없음을 나타냅니다(네트워크의 다른 엔터티에서 소유함).

**IPv6 임대 및 클라이언트 레코드 데이터**

DHCPv6 서버는 클라이언트 요청 수락을 시작하면 IPv6 주소를 요청하거나 할당된 활성 클라이언트 목록을 유지합니다. 서버는 클라이언트 임대 기간을 주기적으로 업데이트하는 임대 타이머를 통해 IP 임대 만료를 확인합니다. 기간이 유효 수명을 초과하면 서버에서 클라이언트 레코드를 지우고 IPv6 주소를 사용 가능한 풀로 다시 반환합니다. 이 문제가 발생하기 전에 클라이언트에서 갱신/리바인딩 프로세스를 시작해야 합니다!

NetX Duo DHCPv6 서버 클라이언트 레코드 테이블에는 클라이언트를 식별하기 위한 정보 및 DHCPv6 클라이언트 요청의 유효성을 검사하고 IPv6 주소를 할당하거나 다시 할당하기 위한 '상태' 정보가 포함되어 있습니다. 이러한 정보에 포함되는 항목은 다음과 같습니다.

- 네트워크의 각 클라이언트 호스트를 고유하게 정의하는 클라이언트 DUID(DHCPv6 고유 식별자). 클라이언트는 모든 DHCPv6 메시지에 대해 항상 동일한 DUID를 사용해야 합니다.

- 클라이언트 IPv6 주소 할당 매개 변수를 정의하는 누적된 클라이언트 IANA(비임시 주소에 대한 ID 연결) 및 IA(ID 연결) IPv6 주소

- 클라이언트 옵션 요청(DNS 서버, 도메인 이름 등)

- 최신 DHCPv6 요청의 클라이언트 IPv6 원본 주소(설정된 경우) 및 대상 주소(멀티캐스트가 아닌 경우)

- 클라이언트의 최신 메시지 유형 및 DHCPv6 '상태'

## <a name="netx-duo-dhcpv6-server-requirements-and-constraints"></a>NetX Duo DHCPv6 서버 요구 사항 및 제약 조건

NetX Duo DHCPv6 서버 API를 사용하려면 ThreadX 5.1 이상 및 NetX Duo 5.5 이상이 필요합니다.

**요구 사항**

***IP 스레드 작업 설정***

NetX Duo DHCPv6 서버는 메시지를 네트워크 링크에서 DHCPv6으로 보내고 받기 위한 IP 인스턴스를 만들어야 합니다. 이는 *nx_ip_create* 서비스를 사용하여 수행됩니다. NetX Duo DHCPv6 서버 자체를 만들어야 합니다. 이는 *nx_dhcpv6_server_create* 서비스를 사용하여 수행됩니다.

DHCPv6는 NetX Duo, ICMPv6 및 UDP를 활용합니다. 따라서 DHCPv6 서버를 사용하려면 먼저 다음 NetX Duo 서비스를 호출하여 IPv6을 사용하도록 설정해야 합니다.

- *nx_udp_enable*
- *nxd_ipv6_enable*
- *nxd_icmp_enable*

또한 DHCPv6 서버를 시작하기 전에 다음과 같은 몇 가지 설정 작업을 수행해야 합니다.

- 해당 링크 로컬 및 IPv6 전역 주소를 만들고 유효성을 검사합니다. 주소 유효성 검사는 사용하도록 설정된 경우 NetX Duo에서 중복 주소 검색을 사용하여 자동으로 수행됩니다. 링크 로컬 및 전역 IP 주소 유효성 검사에 대한 자세한 내용은 *NetX Duo 사용자 설명서* 를 참조하세요.

- DHCPv6 인터페이스에 대한 네트워크 인터페이스 인덱스를 설정합니다.

- 할당 가능한 IPv6 주소에 대한 IP 주소 범위를 만듭니다. 또는 이전 서버 DHCPv6 세션의 데이터가 있는 경우 해당 세션의 IPv6 임대 테이블 및 클라이언트 레코드를 비휘발성 메모리에서 DHCPv6 서버로 업로드해야 합니다. 이 문서의 다른 부분에 있는 간단한 예제 시스템에서는 이 요구 사항을 충족하기 위한 DHCPv6 서버 서비스를 보여 줍니다.

- 서버 DUID를 설정합니다. 서버가 이전 세션에서 DUID를 만든 경우 동일한 데이터를 사용하여 해당 클라이언트에 보내는 메시지에 대해 동일한 DUID를 만들어야 합니다. 이 문서의 다른 부분에 있는 간단한 예제 시스템에서 이 요구 사항이 충족되는 방법을 보여 줍니다.

이 시점에서 DHCPv6 서버를 실행할 준비가 되었습니다. 내부적으로 NetX Duo DHCPv6 서버는 547 포트에 바인딩된 UDP 소켓을 만들고 클라이언트 요청에 대한 수신 대기를 시작합니다.

***패킷 풀 요구 사항***

NetX Duo DHCPv6 서버에는 DHCPv6 메시지를 보내기 위한 패킷 풀이 필요합니다. 패킷 페이로드 및 사용 가능한 패킷 수와 관련된 패킷 풀의 크기는 사용자가 구성할 수 있으며, 호스트 애플리케이션에서 보내는 DHCPv6 메시지 및 기타 전송의 예상 양에 따라 달라집니다.

일반적인 DHCPv6 메시지는 클라이언트에서 요청하는 추가 옵션 수와 서버에서 사용할 수 있는 정보에 따라 약 200-300바이트입니다.

***DHCPv6 서버 인터페이스 설정***

DHCPv6 서버는 기본적으로 클라이언트 요청을 수락하는 인터페이스인 기본 네트워크 인터페이스로 설정됩니다. 그러나 호스트 애플리케이션에서 여전히 서버 전역 주소를 만드는 데 사용한 전역 주소 인덱스를 설정해야 합니다. DHCPv6 인터페이스 인덱스 및 전역 주소 인덱스는 *nx_dhcpv6_server_interface_set* 서비스를 사용하여 설정됩니다. 이는 이 문서의 "간단한 예제"에서도 설명합니다.

***서버 다시 부팅에서 DHCPv6 DUID 저장***

DHCPv6 프로토콜을 사용하려면 서버에서 여러 번 다시 부팅할 때 동일한 DUID를 사용해야 합니다. 따라서 DUID를 만드는 데 사용되는 모든 데이터는 이 요구 사항을 위해 비휘발성 메모리에서 저장하고 검색해야 합니다. 실시간 시계에 액세스해야 하는 링크 계층 및 시간 DUID를 사용하는 호스트의 경우 NetX Duo DHCPv6 호스트 애플리케이션은 초기 서버 DUID를 만들기에 대한 시간 값을 생성하기 위한 실시간 데이터 액세스를 포함하고 후속 서버 세션에서 다시 사용할 수 있도록 해당 데이터를 저장해야 합니다. 그런 다음, *nx_dhcpv6_set_server_duid* 에서 DUID 데이터를 인수로 사용하고 DUID 유형에 따라 구성 옵션을 사용하여 고유한 DUID를 생성(또는 재생성)합니다.

***할당 가능한 IPv6 주소 목록 만들기***

DHCPv6 서버를 만든 후 이전에 저장된 IP 주소 목록 데이터가 없는 경우 서버 호스트 애플리케이션에서 할당 가능한 IPv6 전역 주소 범위를 만들어야 합니다. 이는 시작 주소 및 끝 IPv6 주소를 입력으로 사용하는 *nx_dhcpv6_create_ip_address_range* 서비스를 사용하여 수행됩니다.

***DHCPv6 할당 가능 주소 및 클라이언트 데이터 저장***

DHCPv6 프로토콜을 사용하려면 서버를 다시 부팅하는 경우 DHCPv6 서버에서 클라이언트 및 IPv6 주소 데이터를 비휘발성 스토리지에 저장해야 합니다. NetX Duo DHCPv6 서버에는 클라이언트 및 IPv6 주소 데이터를 각각 DHCPv6 서버에서 업로드 및 다운로드하는 다음과 같은 몇 가지 API가 있습니다.

*nx_dhcpv6_add_client_record*

*nx_dhcpv6_add_ip_address_lease*

*nx_dhcpv6_retrieve_client_record*

*nx_dhcpv6_retrieve_ip_address_lease*

서버를 다시 시작하기 전에 데이터를 서버에 업로드해야 합니다. 데이터 다운로드는 DHCPv6 서버가 중지(또는 일시 중단)된 후에만 수행해야 합니다. 이를 수행하는 서비스는 이 문서의 뒷부분에서 자세히 설명합니다. 그러나 NetX Duo DHCPv6에서 제공하는 비휘발성 스토리지에 대한 액세스는 정의하지 않습니다. 이는 호스트 애플리케이션에서 처리해야 합니다. 간단한 예제에서는 호스트 애플리케이션에서 이 작업을 수행하는 방법을 보여 줍니다.

***서버 DUID(DHCP 고유 식별자)***

서버 DUID는 네트워크에서 DHCPv6 서버 호스트를 고유하게 정의합니다. 서버에서 이전에 DUID를 만들지 않은 경우 *nx_dhcpv6_server_set_duid* 를 사용하여 하나를 만들 수 있습니다. RFC 3315에 따라 서버가 다시 부팅된 후 검색할 수 있도록 DHCPv6 서버에서 이 DUID를 비휘발성 메모리에 저장해야 합니다. DHCPv6 서버는 링크 계층, 링크 계층 시간 및 엔터프라이즈(공급업체 할당) DUID 유형을 지원합니다. 클라이언트는 공급업체 유형 DUID를 직접 보내야 합니다. 공급업체 유형 DUID(17)에 대한 옵션은 NetX Duo DHPv6 서버에서 직접 지원하지 않습니다.

DHCPv6 서버 호스트 애플리케이션에는 임대 시간 제한을 포함하여 IPv6 주소 할당에 대한 기본값이 있습니다. 이러한 옵션을 설정하는 방법은 이 문서 뒷부분에 있는 구성 가능한 옵션을 참조하세요. :

*IANA* 제어 블록에는 T1 및 T2 필드가 포함됩니다. *IANA* 제어 블록의 *IA* 블록에는 기본 설정 및 유효 수명 필드가 포함됩니다. 호스트 애플리케이션에는 이러한 옵션을 설정하기 위해 이 문서의 다른 부분에서 정의된 구성 가능한 옵션이 있습니다. 이러한 옵션은 모든 클라이언트 IPv6 주소 요청에 할당됩니다.

이러한 DHCPv6 IP 임대 매개 변수는 아래에 정의되어 있습니다.

T1 – 클라이언트가 IPv6 주소를 할당한 서버에서 해당 IPv6 주소의 갱신을 시작해야 하는 시간(초)입니다.

T2 – 갱신이 실패하는 경우 클라이언트가 해당 링크에 있는 서버를 사용하여 IPv6 주소 리바인딩을 시작해야 하는 시간(초)입니다.

기본 설정 수명 – 클라이언트가 갱신하거나 리바인딩하지 않은 경우 클라이언트 주소가 더 이상 사용되지 않는 시간(초)입니다. 클라이언트는 이 주소를 계속 사용할 수 있습니다.

유효 수명 – 클라이언트 IP 주소가 만료되고 네트워크 전송에서 이 주소를 사용하지 않아야 하는 시간(초)입니다.

RFC는 각각 클라이언트 *IANA* 옵션의 기본 설정 수명의 0.5 및 0.8인 T1 및 T2 시간을 권장합니다. 서버에 기본 설정이 없으면 서버는 이러한 시간을 0으로 설정해야 합니다. 서버 회신에 T1 및 T2 시간이 0으로 설정되어 있으면 클라이언트에서 자체 T1 및 T2 시간을 설정하도록 합니다.

**제약 조건**

NetX Duo DHCPv6 서버에서 지원하지 않는 DHCPv6 옵션은 다음과 같습니다.

  - DHCPv6 주소 요청 프로세스를 간청 및 회신 메시지 교환으로만 최적화하는 빠른 커밋 옵션

  - 서버에서 클라이언트의 IP 주소 상태 변경을 시작할 수 있도록 하는 다시 구성 옵션

  - 유니캐스트 옵션. 모든 클라이언트 메시지는 DHCPv6 서버가 아닌 *All_DHCP_Relay_Agents_and_Servers* 멀티캐스트 주소로 직접 보내야 합니다.

  - 클라이언트에 부여된 임시 IP 주소인 IA_TA(임시 주소에 대한 ID) 옵션

  - 클라이언트 요청당 여러 IA(IPv6 주소) 옵션

  - DHCPv6 클라이언트와 서버(예: 클라이언트 및 서버) 간의 릴레이 호스트는 동일한 네트워크에 있어야 합니다.

  - IPSec 및 인증은 DHCPv6 메시징에서 지원되지 않습니다. 그러나 IP 인스턴스는 사용 중인 NetX Duo 버전에 따라 IPSec을 사용하도록 설정할 수 있습니다.

  - NetX Duo DHCPv6 서버는 DNS 서버 옵션 요청만 직접 지원합니다. 이는 후속 릴리스에서 변경될 수 있습니다.

  - 접두사 위임 옵션은 지원되지 않습니다.

  - DHCPv6 메시지 인증. 그러나 기본 NetX Duo 환경에서 IPSec을 사용하도록 설정할 수 있습니다. NetX Duo DHCPv6 서버도 클라이언트에 대한 릴레이 연결을 지원하지 않습니다. 모든 클라이언트 요청은 서버 네트워크의 호스트에서 시작한다고 가정합니다.

## <a name="netx-duo-dhcpv6-server-callback-functions"></a>NetX Duo DHCPv6 서버 콜백 함수

*nx_dhcpv6_IP_address_declined_handler*

DHCPv6 클라이언트에서 거부 메시지를 보내면 NetX Duo DHCPv6 서버는 해당 주소를 IPv6 주소 테이블에서 사용할 수 없는 것으로 표시합니다. 이 메시지의 서버 처리를 사용자 지정할 수 있도록 *nx_dhcpv6_IP_address_declined_handler* 가 제공됩니다 *.* 그러나 이 콜백은 현재 구현되어 있지 않습니다.

*nx_dhcpv6_server_option_request_handler*

옵션 요청 데이터가 DHCPv6 클라이언트 메시지에 포함된 경우 NetX Duo DHCPv6 서버는 정의된 경우 각 옵션 요청 옵션 코드를 이 사용자 콜백에 전달합니다. 이렇게 하면 사용자 정의 콜백에서 데이터를 채울 수 있도록 하는 기능이 NetX Duo 서버에 제공됩니다. 그러나 이 기능은 현재 구현되어 있지 않습니다.

## <a name="supported-dhcpv6-rfcs"></a>지원되는 DHCPv6 RFC

NetX Duo DHCPv6은 RFC3315, RFC3646 및 관련 RFC를 준수합니다.