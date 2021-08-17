---
title: 챕터 2 - Azure RTOS NetX Duo DHCPv6 클라이언트 설치 및 사용
description: 이 챕터에서는 Azure RTOS NetX Duo DHCPv6 클라이언트의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 481e29cc674edfa7e437e8e14253172b89aeae6856114192f4ca5b35717c91e0
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791536"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcpv6-client"></a>챕터 2 - Azure RTOS NetX Duo DHCPv6 클라이언트 설치 및 사용

이 챕터에서는 Azure RTOS NetX Duo DHCPv6 클라이언트의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

NetX Duo DHCPv6 클라이언트는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 얻을 수 있습니다. 이 패키지에는 다음과 같이 소스 파일 두 개와 이 문서가 포함된 PDF 파일이 들어 있습니다.

- **nxd_dhcpv6_client.h** NetX DuoDHCPv6 클라이언트의 헤더 파일

- **nxd_dhcpv6_client.c** NetX Duo DHCPv6 클라이언트의 소스 코드 파일

- **demo_netxduo_dhcpv6_client.c** NetX Duo DHCPv6 클라이언트의 설정을 보여 주는 샘플 프로그램

- **nxd_dhcpv6_client.pdf** NetX Duo DHCPv6 클라이언트에 대한 PDF 설명

## <a name="netx-duo-dhcpv6-client-installation"></a>NetX Duo DHCPv6 클라이언트 설치

NetX Duo DHCPv6 클라이언트 API를 사용하기 위해 위에서 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사할 수 있습니다. 예를 들어 NetX Duo가 " *\threadx\arm7\green*" 디렉터리에 설치된 경우 *nxd_dhcpv6_client.h* 및 *nxd_dhpcv6_client.c* 파일을 이 디렉터리에 복사할 수 있습니다.

## <a name="using-the-netx-duo-dhcpv6-client"></a>NetX Duo DHCPv6 클라이언트 사용

기본적으로 애플리케이션 코드는 DHCPv6 클라이언트, ThreadX 및 NetX Duo 서비스를 각각 사용할 수 있도록 *tx_api.h* 및 *nx_api.h* 를 포함한 후에 *nxd_dhcpv6_client.h* 를 포함해야 합니다. *nxd_dhcpv6_client.c* 는 다른 애플리케이션 파일의 프로젝트와 동일한 방식으로 컴파일되어야 하며 해당 개체 형식은 애플리케이션의 파일과 함께 연결되어야 합니다.

### <a name="span-classunderlineclient-dhcp-unique-identifier-duidspan"></a><span class="underline">클라이언트 DUID(DHCP 고유 식별자)</span>

클라이언트 DUID는 네트워크의 각 클라이언트를 고유하게 정의합니다. 애플리케이션은 서버의 IPv6 주소를 요청하기 전에 클라이언트 DUID를 만들어야 합니다. 클라이언트 DUID는 서버로 보내는 모든 메시지에 자동으로 포함됩니다. 애플리케이션은 DUID를 만들기 위해 *nx_dhcpv6_create_client_duid* 서비스를 호출합니다.
```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT duid_type, 
                                  UINT hardware_type, ULONG time);
```

애플리케이션은 이 서비스를 호출하고 DUID 유형(링크 계층만 또는 링크 계층+시간)을 지정합니다. 링크 계층+시간 DUID의 경우, 시간 입력이 지정되지 않으면 이 서비스에서 시간 필드를 제공합니다.

다시 부팅된 후 이전에 할당된 IPv6 주소 임대를 사용하려는 디바이스의 경우, 애플리케이션이 IPv6 주소를 할당했을 때 사용한 클라이언트 DUID를 만들어야 합니다. 링크 계층 클라이언트 DUID를 만들려면 링크 계층 주소만 있으면 됩니다. 디바이스가 링크 계층 주소에 액세스할 수 있는 경우에는 이전의 비휘발성 메모리 스토리지가 필요하지 않습니다. 시간 형식의 DUID의 경우 애플리케이션이 이전 DUID 생성에 사용된 것과 동일한 시간 데이터에 액세스할 수 있어야 하며, 이 경우 비휘발성 메모리가 필요합니다. 안정적인 스토리지가 없는 클라이언트는 시간 형식의 DUID를 사용하지 않아야 합니다.

### <a name="span-classunderlineclient-identity-association-for-non-temporary-addresses-ianaspan"></a><span class="underline">비임시 주소(IANA)에 대한 클라이언트 ID 연결</span>

애플리케이션은 IPv6 주소를 요청하기 전에 IANA를 만들고, 필요에 따라 하나 이상의 IA 주소를 만들어야 합니다. 이를 위해 애플리케이션은 *nx_dhcpv6_create_client_iana* 서비스를 호출합니다. IA 주소 옵션을 만들기 위해 애플리케이션은 요청된 IPv6 주소 및 수명 값을 서버에 대한 힌트로 사용하여 *nx_dhcpv6_add_client_ia* 서비스를 호출합니다.

IANA 및 해당 IA는 클라이언트 IPv6 주소 할당 매개 변수를 점증적으로 정의합니다.

DHCPv6 클라이언트 애플리케이션은 DHCPv6 클라이언트를 시작하기 전에 *nx_dhcpv6_create_client_iana* 서비스를 사용하여 IANA를 만듭니다.

```C
UINT    nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                     UINT IA_ident, ULONG T1, ULONG T2);
```

또한 DHCPv6 클라이언트를 시작하기 전에 *nx_dhcpv6_create_client_ia* 서비스와 요청된 IPv6 주소를 사용하여 하나 이상의 IA를 만들어야 합니다.

```C
UINT    nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                                NXD_ADDRESS *ipv6_address, 
                                ULONG preferred_lifetime, 
                                ULONG valid_lifetime);
```

> [!NOTE]
> 애플리케이션에서 만드는 IA 주소의 수는 NX_DHCPV6_MAX_IA_ADDRESS 매개 변수(기본값 1)를 초과할 수 없습니다.

NetX Duo DHCPv6 클라이언트는 레거시 DHCPv6 클라이언트 애플리케이션에 *nx_dhcpv6_create_client_ia* 를 지원합니다. 이는 *nx_dhcpv6_add_client_ia* 와 동일하지만 개발자는 *nx_dhcpv6_add_client_ia* 서비스를 사용하는 것이 좋습니다.

이러한 서비스는 이 챕터의 다른 부분에 있는 "작은 예제 시스템"에 설명되어 있습니다.

### <a name="span-classunderlinenon-volatile-memory-considerations-to-reuse-ianas-and-iasspan"></a><span class="underline">IANA 및 IA를 재사용하기 위한 비휘발성 메모리 고려 사항</span>

재부팅 시 동일한 주소를 사용하려는 경우 애플리케이션은 IANA 매개 변수 T1, T2 및 IANA 식별자를 비휘발성 메모리에 저장해야 합니다. 또한 애플리케이션은 IPv6 주소를 포함하는 IA를 비휘발성 메모리에 저장해야 합니다.

또한 애플리케이션은 할당된 IPv6 주소 임대에 바인딩된 후 경과한 시간도 종료 시 비휘발성 메모리에 저장해야 합니다. 이를 위해 DHCPv6 클라이언트를 중지하기 전에 *nx_dhcpv6_get_time_accrued* 서비스를 호출합니다.

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, 
                                ULONG *time_accrued);
```

애플리케이션이 중지되었다가 재부팅된 후 DHCPv6 클라이언트를 다시 시작하기까지의 시간 간격을 추적하는 독립된 클록이 애플리케이션에 있다면 중지하기 전에 누적된 IPv6 임대 시간에 이 경과 시간을 추가합니다. 이제 IPv6 임대에 바인딩된 후의 총 경과 시간을 아래의 nv_time 입력으로 사용하여 클라이언트 스레드 작업을 시작합니다.

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr, ULONG nv_time);
```

이 시점부터 DHCPv6 클라이언트 스레드 작업이 누적된 IPv6 임대 시간을 모니터링하여 임대 갱신 시점을 파악하는 작업을 인수합니다.

### <a name="span-classunderlinesetting-dhcpv6-option-dataspan"></a><span class="underline">DHCPv6 옵션 데이터 설정</span>

애플리케이션은 IPv6 임대를 요청하기 전에 DNS 서버 및 시간 서버와 같은 다른 네트워크 매개 변수 데이터를 요청할 수 있습니다. 이러한 매개 변수 중 일부에는 특정 서비스가 있습니다. 다음은 몇 가지 예제입니다.

```C
UINT  nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT enable)

UINT  nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr, 
                                           UINT enable);
```

### <a name="span-classunderlineinitiating-the-ipv6-address-requestspan"></a><span class="underline">IPv6 주소 요청 시작</span>

애플리케이션이 0시간 입력이 지정된 *nx_dhcpv6_start* 서비스를 호출하여 DHCPv6 클라이언트 스레드를 시작합니다. IPv6 주소를 요청하는 DHCPv6 프로토콜을 시작하기 위해 애플리케이션이 *nx_dhcpv6_request_solicit* 를 호출합니다.

이전에 할당된 IPv6 임대를 사용하려는 애플리케이션은 0이 아닌 시간 입력이 지정된 *nx_dhcpv6_start* 를 호출합니다. *nx_dhcpv6_request_solicit* 를 호출해서는 안 됩니다.

그 후 애플리케이션은 더 이상 작업을 수행할 필요가 없으며, DHCPv6 클라이언트가 IPv6 주소를 갱신하거나 다시 바인딩할 시기를 자동으로 모니터링합니다.

## <a name="small-example-system"></a>작은 예제 시스템

DHCPv6 클라이언트 및 가상 “RAM” 드라이버를 사용하는 아래의 간단한 예제는 NetX Duo DHCPv6 클라이언트를 얼마나 쉽게 사용할 수 있는지 보여 줍니다. 이 데모에서는 단일 실제 네트워크 인터페이스만 있는 디바이스를 가정합니다.

*tx_application_define* 은 DHCPv6 클라이언트에서 DHCPv6 메시지를 보내는 데 사용할 패킷 풀을 만듭니다. 또한 애플리케이션 스레드와 IP 인스턴스를 만듭니다. 그런 다음, IP에 UDP 및 ICMP를 사용하도록 설정합니다(130~148줄). 상태 변경(*dhcpv6_state_change_notify*) 및 서버 오류(*dhcpv6_server_error_handler*) 콜백 함수를 사용하여 DHCPv6 클라이언트가 생성됩니다(151줄).

클라이언트 스레드 입력 함수 *thread_client_entry* 에 링크 로컬 주소를 사용하여 클라이언트 IP가 설정되고, IPv6 및 ICMPv6 서비스에 대해 사용하도록 설정됩니다(202~217줄). 애플리케이션은 DHCPv6 클라이언트를 시작하기 전에 클라이언트 DUID, IANA 옵션 및 IA 주소 옵션을 만듭니다(219~303줄). 클라이언트가 서버에 IPv6 주소와 유효 및 기본 수명을 요청하려는 경우 IA 주소 옵션은 선택 사항입니다. 서버는 요청된 IPv6 주소 또는 임대 시간을 허용하거나 허용하지 않을 수 있습니다. 애플리케이션은 여러 글로벌 주소를 할당하기 위해 더 많은 IA 옵션(최대 NX_DHCPV6_MAX_IA_ADDRESS)을 추가할 수 있습니다.

마지막으로, 애플리케이션은 DHCPv6 서버에 네트워크 매개 변수를 요청하는 다양한 옵션을 메시지에 설정합니다. *nx_dhcpv6_start* 를 호출하여 DHCPv6 클라이언트 작업이 시작되고(306줄), *nx_dhcpv6_request_solicit* 에 대한 호출을 사용하여 SOLICIT 상태로 실제 DHCPv6 프로토콜이 시작됩니다(317줄). 그러면 DHCPv6 클라이언트가 주소에 바인딩되거나 오류가 발생할 때까지 DHCPv6 프로토콜을 통해 클라이언트 상태의 승격을 자동으로 처리합니다. 이 시간 동안 애플리케이션은 프로토콜이 완료될 때까지 대기하고, IP 인스턴스가 DAD(기본 구성)를 사용하도록 구성된 경우에는 DAD(중복 주소 검색)도 완료될 때까지 대기합니다.

애플리케이션은 tx_thread_sleep 호출 후 상태 변경 콜백에 설정된 글로벌 매개 변수를 확인하여 DHCPv6 클라이언트 작업이 IPv6 임대를 할당 받는데 성공했는지 확인하고, 성공한 경우에는 DAD 고유성 검사에 성공했는지 확인합니다. 이 작업은 상태 변경 및 서버 오류 콜백 함수에 설정된 카운터를 사용하여 수행됩니다. 애플리케이션은 address_not_assigned, address_expired 및 server_errors의 0이 아닌 개수를 폴링하여 실패한 주소 할당을 확인합니다. bound_addresses 개수가 0이 아닌 경우(적어도 하나 이상의 주소가 할당됨) 0이 아닌 address_failed_dad를 확인하여 실패한 DAD 검사를 찾습니다. 상태 변경 및 서버 오류 콜백에 대한 설명은 다음과 같습니다.

상태 변경 콜백 *dhcpv6_state_change_notify* 는 이전 및 현재 DHCPv6 클라이언트 상태를 통해 클라이언트에서 유효한 서버 응답을 받았는지 확인합니다.

  - *dhcpv6_state_change_notify* 는 SOLICIT에서 INIT로의 직접 전환을 확인하고, 직접 전환이 확인되면 DHCPv6 클라이언트의 카운터를 증분하여 서버에서 응답을 받지 않습니다.

다음으로, *dhcpv6_state_change_notify* 는 클라이언트가 하나 이상의 IPv6 주소에 할당(바인딩)되었는지 확인합니다.

  - 새 상태가 BOUND일 경우 클라이언트에 바인딩된 주소 카운터를 증분합니다.
    
또한 *dhcpv6_state_change_notify* 는 실패한 DAD 검사를 확인합니다.

  - 상태가 DECLINE에서 INIT로 전환되면 DHCPv6 클라이언트가 할당된 주소 중 하나에 대한 DAD 검사에 실패한 것이며, 실패한 주소 할당의 개수를 증분합니다.
    
이 예제에서 *dhcpv6_state_change_notify* 가 마지막으로 확인하는 항목은 DAD 검사를 통과하여 성공적으로 할당된 주소가 갱신 또는 다시 바인딩에 실패한 경우입니다.

  - 상태가 REBIND에서 INIT로 변경되는 경우 클라이언트는 RENEW 또는 REBIND 요청에 대한 응답을 받지 않으며 *dhcpv6_state_change_notify* 가 만료된 주소 수를 증분합니다.

클라이언트 작업이 *dhcpv6_server_error_handler* 에 DHCPv6 서버에서 받은 오류 상태를 알려주면 서버 오류 개수가 증분됩니다.

모든 일이 잘되면 애플리케이션이 DHCPv6 클라이언트에 임대 시간을 포함한 주소 데이터를 쿼리합니다. *nx_dhcpv6_get_valid_ip_address_count* 서비스를 호출하여 유효한(성공적으로 할당된) 주소 개수를 가져오고, *nx_dhcpv6_get_iana_lease_time* 을 호출하여 할당된 모든 IA 주소에 적용되는 IANA의 갱신 시기를 가져옵니다(372~392줄). 그런 다음, DHCPv6 클라이언트에 각 IA 옵션을 쿼리하여 IPv6 주소와 주소 인덱스별 임대 시간을 확인합니다.

일부 DHCPv6 클라이언트 서비스(*nx_dhcpv6_get_lease_time_data, nx_dhcpv6_get_IP_address*)는 주소 인덱스를 입력으로 요구하지 않으며, 기본 클라이언트 글로벌 주소에 대한 DHCPv6 매개 변수를 반환합니다. *nx_dhcpv6_get_valid_ip_address_lease_time* 을 호출할 때 단일 글로벌 IPv6 주소를 사용하는 클라이언트에 적합합니다(384줄).

DHCPv6 클라이언트 구성인 NX_DHCPV6_CLIENT_RESTORE_STATE를 사용하면 시스템이 재부팅된 후에도 Bound 상태에서 이전에 만든 DHCPv6 클라이언트를 복원할 수 있습니다. 시스템이 재부팅된 후 DHCPv6 클라이언트 레코드를 가져오기 위해 *nx_dhcpv6_client_get_record* 를 호출하고(434줄), 시스템 전원이 켜진 후 DHCPv6 클라이언트 레코드를 저장하기 위해 *nx_dhcpv6_client_restore_record* 를 호출합니다(525줄).

그런 다음, 애플리케이션은 *nx_dhcpv6_request_release* 서비스를 사용하여 할당된 주소를 해제합니다(552줄). 시스템을 다시 시작하기 위해 애플리케이션이 *nx_dhcpv6_client_stop* 서비스를 사용하여 DHCPv6 클라이언트를 중지하고(567줄), DHCPv6 클라이언트를 통해 구성된 IP 인스턴스에 등록된 모든 IPv6 주소를 지웁니다. 이를 위해 *nx_dhcpv6_reinitialize* 를 호출합니다(578줄). 그런 다음, 이전과 같이 *nx_dhcpv6_start* 및 *nx_dhcpv6_request_solicit* 서비스를 사용하여 DHCPv6 클라이언트 작업을 다시 시작합니다.

*nx_dhcpv6_delete* 에 대한 호출로 DHCPv6 클라이언트가 삭제됩니다(626줄). DHCPv6 클라이언트용으로 생성된 패킷 풀 *은* IP 인스턴스에서도 사용되므로 삭제되지 않습니다. 하지만 더 이상 사용하지 않는 경우에는 NetX Duo *nx_packet_pool_delete* 서비스를 사용하여 패킷 풀을 삭제해야 합니다.

```C
/* This is a small demo of the NetX Duo DHCPv6 Client for the high-performance NetX Duo stack. */

#include    <stdio.h>
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcpv6_client.h"

#ifdef FEATURE_NX_IPV6
#define     DEMO_STACK_SIZE         2048

/* Set the client address, and request these address from DHCPv6 Server. */
/*
#define     NX_DHCPV6_REQUEST_IA_ADDRESS
*/

/* Set the list of DHCPv6 option data (timezone, DNS server, timer server, domain name)to get from the DHCPv6 server. */

#define     NX_DHCPV6_REQUEST_OPTION


/* Add the fully qualified domain name to request whether the DHCPv6 server SHOULD or SHOULD NOT perform the AAAA RR or DNS updates. */

#define     NX_DHCPV6_REQUEST_FQDN_OPTION


/* Define the ThreadX and NetX object control blocks... */

NX_PACKET_POOL          pool_0;
TX_THREAD               thread_client;
NX_IP                   client_ip;

/* Define the Client and Server instances. */

NX_DHCPV6               dhcp_client;

/* Define the error counter used in the demo application... */
ULONG                   error_counter;
CHAR                    *pointer;

/* Define thread prototypes. */
void    thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Declare DHCPv6 Client callbacks */
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state);
VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type);

/* Set up globals for tracking changes to DHCPv6 Client from callback services. */
UINT state_changes = 0;
UINT address_expired = 0;
UINT address_failed_dad = 0;
UINT bound_addresses = 0;
UINT address_not_assigned = 0;
UINT server_errors = 0;

/* Define some DHCPv6 parameters. */

#define DHCPV6_IANA_ID      0xC0DEDBAD
#define DHCPV6_T1           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_T2           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_RENEW_TIME   NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_REBIND_TIME  NX_DHCPV6_INFINITE_LEASE
#define PACKET_PAYLOAD      500
#define PACKET_POOL_SIZE    (5*PACKET_PAYLOAD)

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

UINT    status;

    /* Setup the working pointer. */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the Client thread. */
    status = tx_thread_create(&thread_client, "Client thread", thread_client_entry, 0,
                              pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1024,  pointer, PACKET_POOL_SIZE);

    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create a Client IP instance. */
    status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                          0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                          pointer, 2048, 1);

    pointer =  pointer + 2048;

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable UDP traffic for sending DHCPv6 messages. */
    status =  nx_udp_enable(&client_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable ICMP. */
    status =  nx_icmp_enable(&client_ip);

    /* Check for ICMP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 Client. */
    status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                      &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                      dhcpv6_server_error_handler);

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update the stack pointer because we need it again. */
    pointer = pointer + 2048;

    /* Yield control to DHCPv6 threads and ThreadX. */
    return;
}


/* Define the Client host application thread. */

void    thread_client_entry(ULONG thread_input)
{

UINT        status;
ULONG       T1, T2;
UINT        address_count;
UINT        address_index = 0;
NXD_ADDRESS valid_ipv6_address;
ULONG       preferred_lifetime;
ULONG       valid_lifetime;
UINT        ia_count = 1;

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
NXD_ADDRESS ipv6_address;
#endif

#ifdef NX_DHCPV6_REQUEST_OPTION
UCHAR       buffer[200];
NXD_ADDRESS dns_server;
#endif

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE
ULONG       current_time;
ULONG       elapsed_time;
NX_DHCPV6_CLIENT_RECORD dhcpv6_client_record;
#endif


    state_changes = 0;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address of 0x1122334456. */
    status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

    if (status)
    {
        error_counter++;
        return;
    }

    /* Let NetX Duo get initialized. */
    tx_thread_sleep(50);

    /* Enable the Client IP for IPv6 and ICMPv6 services. */
    nxd_ipv6_enable(&client_ip);
    nxd_icmp_enable(&client_ip);

    /* Create a Link Layer Plus Time DUID for the DHCPv6 Client. Set time ID field
       to NULL; the DHCPv6 Client API will supply one. */
    status = nx_dhcpv6_create_client_duid(&dhcp_client, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                          NX_DHCPV6_HW_TYPE_IEEE_802, 0);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 client's Identity Association (IA-NA) now.

       Note that if this host had already been assigned in IPv6 lease, it
       would have to use the assigned T1 and T2 values in loading the DHCPv6
       client with an IANA block.
    */
    status = nx_dhcpv6_create_client_iana(&dhcp_client, DHCPV6_IANA_ID, DHCPV6_T1,  DHCPV6_T2);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
    memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
    ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
    ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
    ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
    ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
    ipv6_address.nxd_ip_address.v6[3] = 0x0000abcd;

    /* Create an IA address option.
        Note that if this host had already been assigned in IPv6 lease, it
        would have to use the assigned IPv6 address, preferred and valid lifetime
        values in loading the DHCPv6 Client with an IA block.
    */
    status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address,DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* If the DHCPv6 Client is configured for a maximum number of IA addresses
       greater than 1, we can add another IA address if the device requires
       multiple global IPv6 addresses. */
    if(NX_DHCPV6_MAX_IA_ADDRESS >= 2)
    {
        memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
        ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
        ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
        ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
        ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
        ipv6_address.nxd_ip_address.v6[3] = 0x00001234;

        /* Add another  IA address option. */
        status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address, DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            return;
        }
    }
#endif /* NX_DHCPV6_REQUEST_IA_ADDRESS  */

#ifdef NX_DHCPV6_REQUEST_OPTION
    /* Set the list of DHCPv6 option data to get from the DHCPv6 server if needed. */
    nx_dhcpv6_request_option_timezone(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_DNS_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_time_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_domain_name(&dhcp_client, NX_TRUE);
#endif /* NX_DHCPV6_REQUEST_OPTION */


#ifdef NX_DHCPV6_REQUEST_FQDN_OPTION
    /* Set the DHCPv6 Client FQDN option.
       operation: NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR         DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client.
                  NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE   DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client to the server.
                  NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE   DHCPv6 Client choose to request that the server perform no DNS updatest on its behalf. */
    nx_dhcpv6_request_option_FQDN(&dhcp_client, "DHCPv6-Client", NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR);
#endif /* NX_DHCPV6_REQUEST_FQDN_OPTION */

    /* Start up the NetX DHCPv6 Client thread task. */
    status =  nx_dhcpv6_start(&dhcp_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start the DHCPv6 by sending a Solicit message out on the network. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Is the DHCPv6 Client request for address assignment successfully started? */
    if (status == NX_SUCCESS)
    {

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Check the bound address. */
        if (bound_addresses != ia_count)
        {

            /* Attempt to find out why DHCPv6 failed, where...*/

            if (server_errors > 0)
            {
                /* Actually you would compare server_error count with number of IA's added
                   to determine if any addresses were assigned. */
                printf("Server error, not all address assigned\n");
            }

            if (address_not_assigned > 0)
            {
                /* Actually you would compare address not assigned count with number of IA's added
                   to determine if any addresses were assigned. */

                printf("No servers responded to some or all of our IAs\n");
            }

        }

        /* Regardless if the DHCPv6 Client achieved a bound state, check for DAD
           failures. */
        if (address_failed_dad > 0)
        {
            /* Actually you would compare failed dad count with number of IA's added
               to determine if any addresses were assigned. */

            printf("Some or all of our IAs failed DAD\n");

        }

        /* Successfully assigned IPv6 addresses! */

        /* Get the count of valid IPv6 address obtained by DHCPv6. */
        status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_client, &address_count);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IPv6 address and related lifetimes by address index. This index is the
           index into the DHCPv6 Client address table. Not to be confused with the IP
           instance address table! */
        status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_client, address_index,
                                                           &valid_ipv6_address, 
                                                               &preferred_lifetime,
                                                           &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IANA options for when to start renew/rebind requests. These time
           parameters are the same for all IPv6 addresses assigned in the Client
           e.g. IANA returned from Server. */
        status = nx_dhcpv6_get_iana_lease_time(&dhcp_client, &T1, &T2);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /*****************************************************************************/
        /* These are 'legacy' DHCPv6 services and are for the most part identical to the services
           above except they default to the primary global IPv6 address regardless if the
           Client was assigned more than one global IPv6 address. */

        /* Now check the assigned lease times. */
        status = nx_dhcpv6_get_lease_time_data(&dhcp_client, &T1, &T2,
                                               &preferred_lifetime, &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IP address. */
        status = nx_dhcpv6_get_IP_address(&dhcp_client, &valid_ipv6_address);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Bound state. */

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE

        /* Get the DHCPv6 Client record. */
        nx_dhcpv6_client_get_record(&dhcp_client, &dhcpv6_client_record);

        /* Delete DHCPv6 instance. */
        nx_dhcpv6_client_delete(&dhcp_client);

        /* Delete IP instance. */
        status = nx_ip_delete(&client_ip);

        /* Check for error. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Create a Client IP instance. */
        status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                              0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                              pointer, 2048, 1);

        pointer =  pointer + 2048;

        /* Check for IP create errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable UDP traffic for sending DHCPv6 messages. */
        status =  nx_udp_enable(&client_ip);

        /* Check for UDP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable ICMP. */
        status =  nx_icmp_enable(&client_ip);

        /* Check for ICMP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable the Client IP for IPv6 and ICMPv6 services. */
        status = nxd_ipv6_enable(&client_ip);
        status += nxd_icmp_enable(&client_ip);

        /* Check for IPv6 and ICMPv6 enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Establish the link local address for the host. The RAM driver creates
           a virtual MAC address of 0x1122334456. */
        status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

        if (status)
        {
            error_counter++;
            return;
        }

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Create the DHCPv6 Client. */
        status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                          &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                          dhcpv6_server_error_handler);

        /* Check for errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Update the stack pointer because we need it again. */
        pointer = pointer + 2048;

        /* Restore the DHCPv6 record. */
        nx_dhcpv6_client_restore_record(&dhcp_client, &dhcpv6_client_record, 5);

        /* Resume the DHCPv6 service. */
        nx_dhcpv6_resume(&dhcp_client);
#endif


#ifdef NX_DHCPV6_REQUEST_OPTION

        /* Get the DNS Server address. */
        nx_dhcpv6_get_DNS_server_address(&dhcp_client, 0, &dns_server);

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_DOMAIN_NAME_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        /* Get the time zone. */
        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_NEW_POSIX_TIMEZONE_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server
#endif

        /* At some point, we may wish to release the IPv6 address lease e.g. the device
           is leaving the network or powering down. In that case we inform the
           DHCPv6 Server that we are releasing the address lease. */
        status = nx_dhcpv6_request_release(&dhcp_client);

        /* Check status. */
        if (status != NX_SUCCESS)
        {

            error_counter++;
            return;
        }

        /* Send the release message. */
        tx_thread_sleep(100);
    }

    /* Stopping the Client task. */
    status = nx_dhcpv6_stop(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Clear the previously assigned IPv6 addresses from the Client and IP address table. */
    status = nx_dhcpv6_reinitialize(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start up the Client task again. */
    status = nx_dhcpv6_start(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Begin the request process by sending a Solicit message with the IA created above
       with our preferred IPv6 address. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);
    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Wait a bit before releasing the IP address and terminating the client. */
    tx_thread_sleep(500);

    /* Ok, lets stop the application. Again we DO NOT plan
       to keep the IPv6 address we were assigned and need to release it
       back to the DHCPv6 server. */
    status = nx_dhcpv6_request_release(&dhcp_client);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* Now delete the DHCPv6 client and release ThreadX and
       NetX Duo resources back to the system. */
    nx_dhcpv6_client_delete(&dhcp_client);


    return;

}


/* This is the notification from the DHCPv6 Client task that it has changed
   state in the DHCPv6 protocol, for example getting assigned an IPv6 lease and
   achieving the bound state or an IPv6 lease expires and being reset to
   the init state.
*/
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state)
{


    /* Increment state change counter. */
    state_changes++;

    /* Check if the Client attempted to request an IPv6 lease but no servers
       responded. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_SOLICIT) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that either DAD failed or IP lease expired. */
        address_not_assigned++;
    }

    /* Check if the Client has been assigned an IPv6 lease. */
    if (new_state == NX_DHCPV6_STATE_BOUND_TO_ADDRESS)
    {
        bound_addresses++;
    }

   /* Check if the Client was bound, but failed the uniqueness check
       (Duplicate Address Detection) and was reset to the INIT state. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_DECLINE) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that DAD failed on Client IA. */
        address_failed_dad++;
    }

    /* Check if the Client was bound, attempted renew the lease but the
       IPv6 address renewal/rebinding failed. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_REBIND) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that the IP lease expired. */
        address_expired++;
    }



    /* Other checks are possible. */

}

/* This is the notification from the DHCPv6 Client task that it received an error
   from the server (status code) in response to the Client's last DHCPv6 message.
*/

VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type)
{

    /* Increment the server error count. */
    server_errors++;

    /* This should distinguish between receiving a server error and no server
       available to assign the Client an IPv6 address if the Client fails
       to get assigned an address. */
}

#endif /* FEATURE_NX_IPV6 */
```
