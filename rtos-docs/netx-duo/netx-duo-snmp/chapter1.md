---
title: 1장 - Azure RTOS NetX Duo SNMP 소개
description: NetX Duo SNMP 구현은 SNMP 에이전트의 구현입니다. 에이전트는 SNMP 관리자의 명령에 응답하고 이벤트 기반 트랩을 전송하는 역할을 담당합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810597"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a>1장 - Azure RTOS NetX Duo SNMP 소개

SNMP(Simple Network Management Protocol)는 인터넷에서 디바이스를 관리하기 위해서 설계된 프로토콜입니다. SNMP는 연결 없는 UDP(User Datagram Protocol) 서비스를 활용하여 관리 기능을 수행하는 프로토콜입니다. Azure RTOS NetX Duo SNMP 구현은 SNMP 에이전트의 구현입니다. 에이전트는 SNMP 관리자의 명령에 응답하고 이벤트 기반 트랩을 전송하는 역할을 담당합니다. 

NetX Duo SNMP는 SNMP 관리자와의 IPv4 및 IPv6 통신을 모두 지원합니다. NetX SNMP 애플리케이션은 NetX Duo SNMP에서 컴파일하고 실행해야 합니다. 그러나 개발자는 기존 SNMP 애플리케이션을 동등한 “Duo” 서비스를 사용하여 포팅하는 것이 좋습니다. 예를 들어 SNMP 트랩 메시지를 보낼 때 다음과 같은 ‘Duo’ 서비스는 NetX와 동등한 서비스를 대체해야 합니다.

*nxd_snmp_object_trap_send*

*nxd_snmp_object_trapv2_send*

*nxd_snmp_object_trapv3_send*

자세한 내용은 이 사용자 가이드의 다른 장에 있는 **SNMP 에이전트 서비스에 대한 설명** 을 참조하세요.

## <a name="netx-duo-snmp-agent-requirements"></a>NetX Duo SNMP 에이전트 요구 사항

NetX Duo SNMP 패키지를 사용하려면 IP 인스턴스가 이미 만들어져 있어야 합니다. 또한 동일한 IP 인스턴스에서 UDP를 사용하도록 설정해야 합니다.

NetX Duo SNMP 에이전트에는 몇 가지 추가 요구 사항이 있습니다. 먼저 모든 SNMP 관리자 요청을 처리하려면 포트 161에 대한 액세스 권한이 필요합니다. 또한 트랩 메시지를 관리자에게 보내려면 포트 162에 대한 액세스 권한이 필요합니다.

IPv6와 함께 NetX Duo SNMP 에이전트를 사용하고 IPv6 개체를 얻으려면 NetX Duo에서 IPv6를 사용하도록 설정해야 합니다. IPv6 서비스의 IP 인스턴스를 사용하도록 설정하기 위한 자세한 내용은 ***NetX Duo 사용자 가이드*** 를 참조하세요.

## <a name="netx-duo-snmp-constraints"></a>NetX Duo SNMP 제약 조건

NetX Duo SNMP 프로토콜은 SNMP 버전 1, 2, 3을 구현합니다. SNMP 버전 3 구현에서는 MD5 및 SHA 인증과 DES 암호화를 지원합니다. 이 버전의 NetX Duo SNMP 에이전트에는 다음과 같은 제약 조건이 있습니다.

1. NetX IP 인스턴스 당 하나의 SNMP 에이전트
2. RMON 지원 안 함
3. SNMP 버전 3 알림 메시지가 지원되지 않음
4. OPAQUE 및 NSAP 데이터 형식은 지원되지 않음
5. IPv6 주소는 옥텟 문자열로 정의되며 형식 확인은 애플리케이션에서 처리합니다.

## <a name="snmp-object-names"></a>SNMP 개체 이름

SNMP 프로토콜은 인터넷에서 디바이스를 관리하도록 설계되었습니다. 이를 위해 각 SNMP 관리 디바이스에는 RFC 1155에서 정의한 SMI(관리 정보 구조)에 의해 정의되는 개체 세트가 있습니다. 구조는 다음과 같은 계층 구조 트리 형식의 구조입니다.

![관리 정보 구조의 다이어그램입니다.](media/image3.png)

트리에 있는 각 노드는 개체입니다. 트리에서 “dod” 개체는 1.3.6 표기법으로 식별되는 반면 트리에서 “internet” 개체는 1.3.6.1 표기법으로 식별됩니다. 모든 SNMP 개체 이름은 1.3.6 표기법으로 시작합니다.

SNMP 관리자는 이 개체 표기법을 사용하여 디바이스에서 가져오거나 설정하려는 개체를 지정합니다. NetX Duo SNMP 에이전트는 관리자 요청을 해석하고 애플리케이션이 요청한 작업을 수행할 수 있는 메커니즘을 제공합니다.

## <a name="snmp-manager-requests"></a>SNMP 관리자 요청

SNMP에는 디바이스를 관리하기 위한 간단한 메커니즘이 있습니다. SNMP 관리자에서 ‘포트 161’의 SNMP 디바이스에 실행한 표준 SNMP 명령 세트가 있습니다. 다음은 SNMP 관리자 기본 명령입니다.

| SNMP 명령 | 의미                                                        |
|--------------|----------------------------------------------------------------|
| GET          | 지정한 개체 가져오기                                       |
| GETNEXT      | 지정한 개체 ID 뒤에 있는 다음 논리 개체 가져오기      |
| GETBULK      | 지정한 개체 ID 뒤에 있는 여러 논리 개체 가져오기 |
| SET          | 지정한 개체 설정                                       |

해당 명령은 ASN 1(Abstract Syntax Notation One) 형식으로 인코딩되고 SNMP 관리자에서 보낸 UDP 패킷의 페이로드에 위치합니다. NetX Duo SNMP 에이전트는 요청을 처리한 다음 ***nx_snmp_agent_create*** 호출에 지정된 해당 처리 루틴을 호출합니다.

## <a name="netx-duo-snmp-agent-traps"></a>NetX Duo SNMP 에이전트 트랩

NetX Duo SNMP 에이전트는 SNMP 관리자에게 비동기적으로 이벤트를 경고하는 기능도 제공합니다. 이 기능은 SNMP 트랩 명령을 통해 수행됩니다. SNMP 관리자에게 트랩을 보내기 위한 각 버전의 SNMP에 대한 고유한 API가 있습니다. 기본적으로 트랩은 포트 162의 SNMP 관리자에게 전송됩니다.

NetX Duo SNMP 에이전트는 SNMP 버전 3 트랩 메시지에 대해 별도의 보안 키를 제공합니다. 이렇게 하려면 SNMP 애플리케이션은 관리자 요청에 대한 응답에 적용되는 키 세트에서 별도의 키 세트를 만들어야 합니다. 트랩 보안을 사용하면 SNMP 에이전트가 인증 및 개인 정보에 동일한 암호 또는 다른 암호를 사용할 수 있습니다. 보안 키를 만드는 방법에 대한 자세한 내용은 다음 섹션의 **NetX Duo SNMP 인증 및 암호화** 를 참조하세요.

표준 SNMP 트랩 변수 목록은 nxd_snmp.h 맨 위에 열거됩니다.

| 변수                                 | 값  |
|-------------------------------------------|---|
| #define NX_SNMP_TRAP_COLDSTART            | 0 |
| #define NX_SNMP_TRAP_WARMSTART            | 1 |
| #define NX_SNMP_TRAP_LINKDOWN             | 2 |
| #define NX_SNMP_TRAP_LINKUP               | 3 |
| #define NX_SNMP_TRAP_AUTHENTICATE_FAILURE | 4 |
| #define NX_SNMP_TRAP_EGPNEIGHBORLOSS      | 5 |
| #define NX_SNMP_TRAP_ENTERPRISESPECIFIC   | 6 |

변수를 트랩 메시지에 포함하려면 *nx_snmp_agent_trapv2_send*(SNMPv2) 또는 *nx_snmp_agent_trapv3_send*(SNMPv3)의 trap_type 입력 인수를 변수의 열거된 값으로 설정합니다. 다음 아래는 SNMP 버전 2가 콜드 부팅 이벤트를 SNMP 관리자에게 알리는 예제입니다.

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

트랩 메시지에 전용 변수를 포함하기 위해 trap_type 입력 인수는 NX_SNMP_TRAP_CUSTOM으로 설정되고 트랩 목록 입력 인수는 전용 데이터를 포함합니다. 트랩 메시지에는 시스템 작동 시간(1.3.6.1.6.3.1.1.4.1.0)이 포함됩니다. 다음 아래는 SNMP 버전 2에 대한 예제입니다.

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a>NetX Duo SNMP 인증 및 암호화

인증에는 ‘기본’ 및 ‘다이제스트’의 두 가지 종류가 있습니다.  기본 인증은 많은 프로토콜에서 볼 수 있는 간단한 일반 텍스트 ‘사용자 이름’ 인증과 동일합니다. SNMP 기본 인증에서 사용자는 제공된 사용자 이름이 SNMP 작업 수행에 유효한지 확인만 하면 됩니다. 기본 인증은 SNMP 버전 1과 버전 2에 대한 유일한 옵션입니다.

기본 인증의 주요 단점은 사용자 이름이 일반 텍스트로 전송된다는 것입니다. SNMP 버전 3 다이제스트 인증은 사용자 이름을 일반 텍스트로 전송하지 않음으로써 이 문제를 해결해 줍니다. 대신 알고리즘을 사용하여 사용자 이름, 컨텍스트 엔진 및 기타 정보에서 96비트 ‘다이제스트’를 파생합니다. NetX Duo SNMP 에이전트는 MD5 및 SHA 다이제스트 알고리즘을 모두 지원합니다.

인증을 사용하려면 SNMP 에이전트가 *nx_snmp_agent_context_engine_set* 서비스를 사용하여 컨텍스트 엔진 ID를 설정해야 합니다. 컨텍스트 엔진 ID는 인증 키를 만드는 데 사용됩니다.

DES 알고리즘을 사용하여 SNMP 버전 3 데이터의 암호화를 사용할 수 있습니다. 암호화는 인증을 사용하도록 설정해야 합니다. 인증 매개 변수를 설정하지 않으면 데이터를 암호화할 수 없습니다.

인증 및 개인 키를 만들려면 다음과 같은 API가 사용됩니다.

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

그런 다음, 해당 키를 사용하도록 SNMP 에이전트를 구성해야 합니다. SNMP 에이전트에 키를 등록하려면 다음과 같은 API가 사용됩니다.

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

트랩 메시지에 대한 별도의 키를 만들 수 있습니다. 트랩 메시지에 키를 적용하려면 다음 API를 사용할 수 있습니다.

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

응답 메시지 및 트랩 전송에 대한 인증 또는 암호화를 사용하지 않으려면 키 포인터 입력이 NULL로 설정된 서비스를 사용하세요.

## <a name="netx-duo-snmp-community-strings"></a>NetX Duo SNMP 커뮤니티 문자열

NetX Duo SNMP 에이전트는 퍼블릭 및 프라이빗 커뮤니티 문자열을 모두 지원합니다. 퍼블릭 문자열은 *nx_snmp_agent _public_string_set* 서비스를 사용하여 설정됩니다. NetX Duo SNMP 에이전트 프라이빗 문자열은 *nx_snmp_agent_private_string_set* 서비스를 사용하여 설정됩니다.

## <a name="netx-duo-snmp-username-callback"></a>NetX Duo SNMP 사용자 이름 콜백

NetX Duo SNMP 에이전트 패키지를 사용하면 애플리케이션에서 각 SNMP 클라이언트 요청을 처리하기 시작할 때 호출되는 사용자 이름 콜백을 ***nx_snmp_agent_create*** 호출을 통해 지정할 수 있습니다.

콜백 루틴은 NetX Duo SNMP 에이전트에게 사용자 이름을 제공합니다. 제공된 사용자 이름이 유효하거나 요청에 응답하는 데 사용자 이름 확인이 필요하지 않은 경우 사용자 이름 콜백에서 **NX_SUCCESS** 의 값을 반환해야 합니다. 그러지 않은 경우 루틴은 지정된 사용자 이름이 잘못되었음을 나타내는 **NX_SNMP_ERROR** 를 반환해야 합니다.

애플리케이션 사용자 이름 콜백 루틴의 형식은 다음과 같이 정의됩니다.

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

입력 매개 변수는 다음과 같이 정의됩니다.

| 매개 변수 | 의미                                              |
|-----------|------------------------------------------------------|
| *agent_ptr* | SNMP 에이전트 호출에 대한 포인터                        |
| 사용자 이름  | 필요한 사용자 이름에 대한 포인터의 대상 |

SNMP 버전 1 및 SNMP 버전 2/버전 2C 세션의 경우 애플리케이션은 들어오는 SNMP 요청의 커뮤니티 문자열을 검사하여 SNMP 요청에 유효한 커뮤니티 문자열이 있는지 확인해야 합니다. SNMP 애플리케이션에서 이 작업을 수행할 수 있는 몇 가지 서비스가 있습니다.

SNMP 애플리케이션은 현재 SNMP 관리자 요청이 GET(예: GET, GETNEXT 또는 GETBULK)인지 또는 이 서비스를 사용하는 SET 형식의 요청인지를 조회할 수 있습니다.

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

요청이 GET 형식인 경우 애플리케이션에서 입력 커뮤니티 문자열을 SNMP 에이전트의 퍼블릭 문자열과 비교하려고 합니다.

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

마찬가지로 요청이 SET 형식인 경우 애플리케이션은 입력 커뮤니티 문자열을 SNMP 에이전트의 프라이빗 문자열과 비교하려고 합니다.

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

is_public 및 is_private 반환 값은 입력 커뮤니티 문자열이 유효한 퍼블릭 또는 프라이빗 커뮤니티 문자열인지 여부를 각각 나타냅니다.

사용자 이름 콜백 루틴의 반환 값은 사용자 이름이 유효한지 여부를 나타냅니다. 사용자 이름이 유효한 경우 **NX_SUCCESS** 값이 반환되고, 사용자 이름이 잘못된 경우 **NX_SNMP_ERROR** 값이 반환됩니다.

## <a name="netx-duo-snmp-agent-get-callback"></a>NetX Duo SNMP 에이전트 GET 콜백

애플리케이션은 SNMP 관리자에서 GET 개체 요청을 처리하기 위한 콜백 루틴을 설정해야 합니다. 콜백은 요청에 지정된 개체의 값을 검색합니다.

애플리케이션 GET 요청 콜백 루틴은 아래와 같이 정의됩니다.

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

입력 매개 변수는 다음과 같이 정의됩니다.

| 매개 변수        | 의미 |
|------------------|----------------------------------|
| *agent_ptr*        | SNMP 에이전트 호출에 대한 포인터 |
| object_requested | GET 작업이 사용되는 개체 ID를 나타내는 ASCII 문자열입니다. |
| object_data      | 콜백에서 검색한 값을 저장할 데이터 구조입니다. 이는 아래에서 설명하는 일련의 NetX Duo SNMP API를 사용하여 설정할 수 있습니다. |

> [!NOTE]
> 옥텟 문자열의 경우 콜백 자체에 길이 인수가 없기 때문에 내부 함수가 길이를 알 수 있도록 개체에 길이를 할당해야 합니다.

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

데이터 형식이 GET 콜백에 알려지지 않았기 때문에 데이터 형식을 확인할 필요가 없습니다. 길이는 null로 구분된 숫자 형식 또는 문자열에 영향을 주지 않습니다.

그런 다음, 내부 함수를 호출합니다.

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

콜백 함수에서 요청된 개체를 찾을 수 없는 경우 **NX_SNMP_ERROR_NOSUCHNAME** 오류 코드가 반환됩니다. 다른 오류가 검색되면 **NX_SNMP_ERROR** 는 반환됩니다.

## <a name="netx-duo-snmp-agent-getnext-callback"></a>NetX Duo SNMP 에이전트 GETNEXT 콜백

또한 애플리케이션은 SNMP 관리자에서 GETNEXT 개체 요청에 대한 콜백 루틴을 설정해야 합니다. GETNEXT 콜백은 요청에 의해 지정된 다음 개체의 값을 검색합니다.

애플리케이션 GETNEXT 요청 콜백 루틴은 아래와 같이 정의됩니다.

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

입력 매개 변수는 다음과 같이 정의됩니다.

| 매개 변수        | 의미 |
|------------------|-------------------------------------------|
| *agent_ptr*        | SNMP 에이전트 호출에 대한 포인터 |
| object_requested | GETNEXT 작업이 사용되는 개체 ID를 나타내는 ASCII 문자열입니다. |
| object_data      | 콜백에서 검색한 값을 저장할 데이터 구조입니다. 이는 아래에서 설명하는 일련의 NetX Duo SNMP API를 사용하여 설정할 수 있습니다. |

GET 콜백의 경우와 마찬가지로, 콜백 자체에 길이 인수가 없기 때문에 내부 함수에서 길이를 알 수 있도록 옥텟 문자열 데이터가 있는 개체에 길이를 할당해야 합니다.

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

데이터 형식이 GET 콜백에 알려지지 않았기 때문에 데이터 형식을 확인할 필요가 없습니다. 길이는 null로 구분된 숫자 형식 또는 문자열에 영향을 주지 않습니다.

그런 다음, 내부 함수를 호출합니다.

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

콜백 함수에서 요청된 개체를 찾을 수 없는 경우 **NX_SNMP_ERROR_NOSUCHNAME** 오류 코드가 반환됩니다. 다른 오류가 검색되면 **NX_SNMP_ERROR** 는 반환됩니다.

## <a name="netx-duo-snmp-agent-set-callback"></a>NetX Duo SNMP 에이전트 SET 콜백

애플리케이션은 SNMP 관리자에서 SET 개체 요청을 처리하기 위한 콜백 루틴을 설정해야 합니다. SET 콜백은 요청에 의해 지정된 개체의 값을 설정합니다.

애플리케이션 SET 요청 콜백 루틴은 아래와 같이 정의됩니다.

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

입력 매개 변수는 다음과 같이 정의됩니다.

| 매개 변수        | 의미 |
|------------------|-------- |
| *agent_ptr*      | SNMP 에이전트 호출에 대한 포인터 |
| object_requested | SET 작업이 사용되는 개체 ID를 나타내는 ASCII 문자열입니다. |
| object_data      | 지정된 개체에 대한 새 값을 포함하는 데이터 구조입니다. 실제 작업은 아래에 설명된 NetX Duo SNMP API를 사용하여 수행할 수 있습니다. |

옥텟 문자열의 경우 SNMP 에이전트가 데이터를 구문 분석했고 형식과 길이를 알고 있기 때문에 SET 콜백은 데이터의 길이로 MIB 테이블을 업데이트해야 합니다.

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

콜백 함수에서 요청된 개체를 찾을 수 없는 경우 **NX_SNMP_ERROR_NOSUCHNAME** 오류 코드가 반환됩니다.

NetX Duo SNMP 호스트가 프라이빗 커뮤니티 문자열을 만들었으나 SET 요청의 SNMP 발신자에 일치하는 프라이빗 문자열이 없으면 **NX_SNMP_ERROR_NOACCESS** 오류를 반환할 수 있습니다. 다른 오류가 검색되면 **NX_SNMP_ERROR** 는 반환됩니다.

> [!NOTE]
> NetX Duo SNMP 에이전트는 배포에 SNMP MIB 데이터베이스를 함께 제공하지만, 주로 테스트 및 개발을 목적으로 사용됩니다. 개발자는 전문 SNMP 애플리케이션을 위한 전용 MIB 데이터베이스가 필요할 수 있습니다.

## <a name="changing-snmp-version-at-run-time"></a>런타임에 SNMP 버전 변경

SNMP 에이전트 호스트는 런타임에 *nx_snmp_agent_set_version* 서비스를 사용하여 세 버전 각각에 대한 SNMP 버전을 변경할 수 있습니다. SNMP 에이전트는 *nx_snmp_agent_create* 에서 SNMP 에이전트가 만들어지면 세 가지 버전 모두에 대해 기본적으로 사용할 수 있도록 설정됩니다. 그러나 애플리케이션은 이를 모든 버전의 하위 집합으로 제한할 수 있습니다.

> [!NOTE]
> NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 및/또는 NX_SNMP_DISABLE_V3 구성 옵션이 정의된 경우 이 함수는 영향을 받는 버전을 사용하도록 설정하지 않습니다.

SNMP 에이전트는 *nx_snmp_agent_get_current_version* 서비스를 사용하여 수신된 최신 SNMP 패킷의 SNMP 버전을 검색할 수 있습니다.

## <a name="snmpv3-discovery"></a>SNMP 버전 3 검색

SNMP 버전 3에 대해 사용하도록 설정된 경우 SNMP 에이전트는 SNMP 관리자의 검색 요청에 응답합니다. 해당 요청에는 신뢰할 수 있는 엔진 ID, 사용자 이름, 부팅 횟수 및 부팅 시간에 대한 null 값을 포함한 보안 매개 변수 데이터가 포함됩니다. 인증 매개 변수는 검색 메시지에 적용되지 않습니다. 요청의 변수 바인딩 목록이 비어있습니다(항목 0개 포함). SNMP 에이전트는 0번의 부팅 시간 및 횟수 및 알 수 없는(null) 엔진 ID로 받은 요청인 1개 항목(*usmStatsUnknownEngineIDs*)을 포함하는 변수 바인딩 목록으로 응답합니다. 브라우저/관리자의 후속 GETNEXT 요청에는 보안을 사용하도록 설정된 경우에만 부팅 데이터 및 보안 매개 변수가 입력됩니다. 이 경우에는 PDU에서 NotInTime 데이터 업데이트도 전송합니다. 인증과 같은 보안 매개 변수는 에이전트 ID를 관리자에게 증명합니다.

SNMP 버전 3 인증에 대한 자세한 내용은 RFC 3414 “SNMPv3(Simple Network Management Protocol 버전 3)에 대한 USM(사용자 기반 보안 모델)”에서 확인할 수 있습니다.

## <a name="netx-duo-snmp-rfcs"></a>NetX Duo SNMP RFC

NetX Duo SNMP는 RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 및 관련 RFC를 준수합니다.
