---
title: 챕터 2 - Azure RTOS NetX Duo DHCP 클라이언트 설치 및 사용
description: 이 챕터에서는 Azure RTOS NetX Duo DHCP 클라이언트의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c3df64be337b557f492617c1ef20adc7c0f8d6e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810939"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcp-client"></a>챕터 2 - Azure RTOS NetX Duo DHCP 클라이언트 설치 및 사용

이 챕터에서는 Azure RTOS NetX Duo DHCP 클라이언트의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS NetX Duo는 <https://github.com/azure-rtos/netxduo>에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다. 이 패키지에는 다음과 같은 파일이 포함되어 있습니다.

- **nxd_dhcp_client.h**: NetX Duo DHCP용 헤더 파일
- **nxd_dhcp_client.c**: DHCP NetX Duo용 C 원본 파일
- **nxd_dhcp_client.pdf**: NetX Duo DHCP 사용자 가이드 
    - **demo_netxduo_dhcp.c**: NetX Duo DHCP 클라이언트 데모
    - **demo_netxduo_multihome_dhcp_client.c**: 여러 인터페이스에서 DHCP의 NetX Duo DHCP 클라이언트 데모

## <a name="dhcp-installation"></a>DHCP 설치

NetX Duo DHCP 클라이언트를 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX Duo가 " *\threadx\arm7\green*" 디렉터리에 설치된 경우 *nxd_dhcp_client.h* 및 *nxd_dhcp_client.c* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="using-dhcp"></a>DHCP 사용

DHCP는 NetX Duo에 쉽게 사용할 수 있습니다. 기본적으로 애플리케이션 코드는 ThreadX 및 NetX Duo를 사용할 수 있도록 *tx_api.h* 및 *nx_api.h* 를 포함한 후에 *nxd_dhcp_client.h* 를 포함해야 합니다. *nxd_dhcp_client.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 DHCP 함수 호출을 수행할 수 있습니다. 애플리케이션에서도 *nxd_dhcp_client.c* 를 빌드 프로세스에 포함해야 합니다. 이 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일해야 하며, 해당 개체 형식은 애플리케이션의 파일과 함께 연결해야 합니다. 이것이 NetX DHCP를 사용하는 데 필요한 모든 것입니다.

DHCP는 NetX Duo UDP 서비스를 활용하므로 DHCP를 사용하기 전에 *nx_udp_enable* 호출을 사용하여 UDP를 사용하도록 설정해야 합니다.

이전에 할당된 IP 주소를 가져오기 위해 DHCP 클라이언트에서 DHCP 서버에 대한 요청 메시지 및 50 "요청된 IP 주소" 옵션을 사용하여 DHCP 프로세스를 시작할 수 있습니다. DHCP 서버에서 IP 주소를 클라이언트에 부여하면 ACK 메시지를 사용하여 응답하고, 거부하면 NACK를 사용하여 응답합니다. 후자의 경우 DHCP 클라이언트에서 요청된 IP 주소가 없이 검색 메시지를 사용하여 Init 상태에서 DHCP 프로세스를 다시 시작합니다. 호스트 애플리케이션은 먼저 DHCP 클라이언트를 만든 다음, *nx_dhcp_request_client_ip* API 서비스를 호출하여 요청된 IP 주소를 설정한 후에 *nx_dhcp_start* 를 사용하여 DHCP 프로세스를 시작합니다. 자세한 내용은 이 문서의 다른 부분에 DHCP 애플리케이션 예제가 나와 있습니다.

## <a name="in-the-bound-state"></a>바인딩된 상태에서

DHCP 클라이언트가 바인딩 상태에 있는 동안 DHCP 클라이언트 스레드에서 간격당 한 번씩(NX_DHCP_TIME_INTERVAL에서 지정한 대로) 클라이언트 상태를 처리하고 클라이언트에 할당된 IP 임대에 남아 있는 시간을 줄입니다. 갱신 시간이 경과하면 DHCP 클라이언트 상태가 클라이언트에서 DHCP 서버에 갱신을 요청하는 RENEW 상태로 업데이트됩니다.

## <a name="sending-dhcp-messages-to-the-server"></a>서버에 DHCP 메시지 보내기

DHCP 클라이언트에는 호스트 애플리케이션에서 메시지를 DHCP 서버에 보낼 수 있도록 하는 API 서비스가 있습니다. 이러한 서비스는 호스트 애플리케이션에서 DHCP 클라이언트 프로토콜을 수동으로 실행하기 위한 것이 아닙니다.

  - *nx_dhcp_release*: 호스트 애플리케이션이 네트워크에서 나가거나 IP 주소를 해제해야 하는 경우 RELEASE 메시지를 서버에 보냅니다.
  - *nx_dhcp_decline*: 호스트 애플리케이션이 DHCP 클라이언트와 독립적으로 해당 IP 주소를 이미 사용하고 있음을 확인하는 경우 DECLINE 메시지를 서버에 보냅니다.
  - *nx_dhcp_forcerenew*: FORCERENEW 메시지를 서버에 보냅니다.
  - *nx_dhcp_send_request*: *nxd_dhcp_client.h* 에서 지정한 대로 DHCP 메시지 유형을 인수로 사용하여 메시지를 서버에 보냅니다. 이는 주로 DHCP INFORM 메시지를 보내기 위한 것입니다.

이러한 서비스에 대한 자세한 내용은 [DHCP 서비스 설명](chapter3.md)을 참조하세요. 

## <a name="starting-and-stopping-the-dhcp-client"></a>DHCP 클라이언트 시작 및 중지

DHCP 클라이언트가 바인딩 상태에 도달했는지 여부에 관계없이 DHCP 클라이언트를 중지하려면 호스트 애플리케이션에서 *nx_dhcp_stop* 을 호출합니다.

DHCP 클라이언트를 다시 시작하려면 먼저 호스트 애플리케이션에서 위에서 설명한 *nx_dhcp_stop* 서비스를 사용하여 DHCP 클라이언트를 중지해야 합니다. 그러면 호스트에서 *nx_dhcp_start* 를 호출하여 DHCP 클라이언트를 다시 시작할 수 있습니다. 예를 들어 호스트 애플리케이션이 이전 DHCP 클라이언트 프로필(예: 다른 네트워크의 이전 DHCP 서버에서 가져온 프로필)을 지우려는 경우 호스트 애플리케이션에서 *nx_dhcp_start* 를 호출하기 전에 내부적으로 이 작업을 수행하기 위해 *nx_dhcp_reinitialize* 를 호출해야 합니다.

일반적인 시퀀스는 다음과 같을 수 있습니다.

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

단일 DHCP 인터페이스에서만 실행되는 DHCP 애플리케이션의 경우 DHCP 클라이언트를 중지하면 DHCP 클라이언트 타이머도 비활성화됩니다. 따라서 IP 임대에 남아 있는 시간을 더 이상 추적하지 않습니다. 특정 인터페이스에서 DHCP 클라이언트를 중지하면 DHCP 클라이언트 타이머가 비활성화되지 않지만, 해당 인터페이스의 IP 임대에 남아 있는 시간에 대한 타이머 업데이트가 중지됩니다.

따라서 호스트 애플리케이션에서 다시 부팅하거나 네트워크를 전환해야 하는 경우가 아니면 DHCP 클라이언트를 중지하지 않는 것이 좋습니다.

## <a name="using-the-dhcp-client-with-auto-ip"></a>자동 IP를 통해 DHCP 클라이언트 사용

NetX Duo DHCP 클라이언트는 DHCP 서버에서 사용할 수 있거나 응답할 수 있다고 보장되지 않는 주소를 DHCP 및 자동 IP를 통해 보장하는 애플리케이션의 자동 IP 프로토콜과 동시에 작동합니다. 그러나 호스트에서 서버를 검색하거나 IP 주소를 할당할 수 없는 경우 로컬 IP 주소에 대해 자동 IP 프로토콜로 전환할 수 있습니다. 이렇게 하려면 먼저 자동 IP가 "프로브" 및 "방어" 단계를 거치는 동안 DHCP 클라이언트를 일시적으로 중지하는 것이 좋습니다. 자동 IP 주소가 호스트에 할당되면 DHCP 클라이언트를 다시 시작할 수 있고, DHCP 서버를 사용할 수 있게 되면 애플리케이션이 실행되는 동안 DHCP 서버에서 제공하는 IP 주소를 호스트 IP 주소에서 수락할 수 있습니다.

NetX Duo 자동 IP에는 IP 주소가 변경되는 경우 호스트에서 해당 작업을 모니터링할 수 있는 주소 변경 알림이 있습니다.

## <a name="packet-chaining"></a>패킷 체인

패킷 풀 및 메모리 리소스를 더 효율적으로 사용하기 위해 DHCP 클라이언트는 이더넷 드라이버에서 들어오는 연결된 패킷(드라이버 MTU를 초과하는 데이터그램)을 처리할 수 있습니다. 이 기능이 드라이버에 있으면 애플리케이션에서 패킷을 받기 위한 패킷 풀을 필수 NX_DHCP_PACKET_PAYLOAD 바이트 미만으로 설정할 수 있습니다. NX_DHCP_PACKET_PAYLOAD는 실제 네트워크(일반적으로 이더넷) 프레임과 548바이트의 DHCP 메시지 데이터, IP 및 UDP를 수용할 수 있어야 합니다.

애플리케이션은 DHCP 클라이언트의 일부이며 DHCP 메시지를 보내는 데 사용되는 패킷 풀의 패킷 페이로드 및 패킷 수를 최적화할 수 있습니다. DHCP 클라이언트 메시지의 예상 사용량 및 크기에 따라 크기를 최적화할 수 있습니다.

## <a name="small-example-system"></a>간단한 예제 시스템

NetX Duo를 사용하는 방법에 대한 예제는 아래 그림 1.1에 나와 있습니다. "*my_thread_entry*" 애플리케이션 스레드 입력 함수는 줄 101에서 만들어집니다. 성공적으로 만들어지면 줄 108에서 *nx_dhcp_start* 호출을 통해 DHCP 처리가 시작됩니다. 이 시점에서 DHCP 클라이언트 스레드 작업은 DHCP 서버에 대한 개별적으로 시도합니다. 이 프로세스를 진행하는 동안 애플리케이션 코드는 줄 95에서 *nx_ip_status_check* 서비스(또는 보조 인터페이스의 경우 *nx_ip_interface_status_check*)를 사용하여 유효한 IP 주소가 IP 인스턴스에 등록될 때까지 기다립니다. 이는 일반적으로 대기 옵션이 짧은 루프에서 수행됩니다.

줄 127 이후 DHCP는 유효한 IP 주소를 받고 NetX Duo TCP/IP 서비스를 원하는 대로 활용하여 애플리케이션을 진행할 수 있습니다.

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */
intmain()
{
  /* Enter the ThreadX kernel.  */
  tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;
    
    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create “my_thread”.  */
      tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                        pointer, DEMO_STACK_SIZE, 2, 2, 
                        TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

    /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                          0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
                          DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
 }


 /* Define my thread.  */

 void    my_thread_entry(ULONG thread_input)
 {

 UINT        status;
 ULONG       actual_status;
 NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
    /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                                     &actual_status, 100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
      error_counter++;
      return;
    }
    else
    {

  /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.
    }
 }

```
## <a name="multi-server-environments"></a>다중 서버 환경

둘 이상의 DHCP 서버가 있는 네트워크에서 DHCP 클라이언트는 처음 받은 DHCP 서버 제안 메시지를 수락하고, 요청 상태로 이동하며, 받은 다른 모든 제안을 무시합니다.

## <a name="arp-probes"></a>ARP 프로브

DHCP 클라이언트는 DHCP 서버에서 IP 주소를 할당한 후 하나 이상의 ARP 프로브를 보내 IP 주소가 이미 사용되고 있지 않은지 확인하도록 구성할 수 있습니다. ARP 프로브 단계는 RFC 2131에서 권장하며, 둘 이상의 DHCP 서버가 있는 환경에서 특히 중요합니다. 호스트 애플리케이션에서 NX_DHCP_CLIENT_SEND_ARP_PROBE 옵션을 사용하도록 설정하면(추가 ARP 프로브 옵션은 챕터 2의 **구성 옵션** 참조) DHCP 클라이언트는 '자체 주소가 지정된' ARP 프로브를 보내고 응답을 위해 지정된 시간 동안 기다립니다. 받은 항목이 없으면 DHCP 클라이언트가 바인딩됨 상태로 이동합니다. 응답을 받으면 DHCP 클라이언트에서 주소가 이미 사용 중이라고 가정합니다. 자동으로 DECLINE 메시지를 서버에 보내고, 클라이언트를 다시 초기화하여 INIT 상태에서 DHCP 프로브를 다시 시작합니다. 그러면 DHCP 상태 시스템이 다시 시작되고 클라이언트에서 다른 DISCOVER 메시지를 서버에 보냅니다.

## <a name="bootp-protocol"></a>BOOTP 프로토콜

DHCP 클라이언트는 BOOTP 프로토콜과 DHCP 프로토콜도 지원합니다. 이 옵션을 사용하도록 설정하고 DHCP 대신 BOOTP를 사용하려면 호스트 애플리케이션에서 NX_DHCP_BOOTP_ENABLE 구성 옵션을 설정해야 합니다. 호스트 애플리케이션은 BOOTP 프로토콜에서 특정 IP 주소를 계속 요청할 수 있습니다. 그러나 BOOTP가 때때로 사용되므로 DHCP 클라이언트는 호스트 운영 체제 로드를 지원하지 않습니다.

## <a name="dhcp-on-a-secondary-interface"></a>보조 인터페이스의 DHCP

NetX Duo DHCP 클라이언트는 기본 인터페이스가 아닌 보조 인터페이스에서 실행할 수 있습니다.

보조 네트워크 인터페이스에서 NetX Duo DHCP 클라이언트를 실행하려면 호스트 애플리케이션에서 *nx_dhcp_set_interface_index* API 서비스를 사용하여 DHCP 클라이언트의 인터페이스 인덱스를 보조 인터페이스로 설정해야 합니다. 인터페이스는 *nx_ip_interface_attach* 서비스를 사용하여 기본 네트워크 인터페이스에 이미 연결되어 있어야 합니다. 보조 인터페이스를 연결하는 방법에 대한 자세한 내용은 NetX Duo 사용자 가이드를 참조하세요.

호스트 애플리케이션이 보조 인터페이스에서 DHCP 서버에 연결하는 예제 시스템(그림 1.2)은 다음과 같습니다. 줄 65에서 보조 인터페이스는 null IP 주소를 사용하여 IP 작업에 연결됩니다. 줄 104에서 DHCP 클라이언트 인스턴스가 만들어지면 후에 *nx_dhcp_set_interface_index* 를 호출하여 DHCP 클라이언트 인터페이스 인덱스가 1(예: 자체가 인덱스 0인 기본 인터페이스의 오프셋)로 설정됩니다. 그러면 줄 108에서 DHCP 클라이언트를 시작할 준비가 됩니다.

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */

intmain()
{
  /* Enter the ThreadX kernel.  */
  tx_kernel_enter();
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create “my_thread”.  */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                      pointer, DEMO_STACK_SIZE, 
                      2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

  /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                           0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    status =  _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                                       0xFFFFFF00UL, my_netx_driver);

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}


void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       status;
NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
      /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Set the DHCP client interface to the secondary interface. */
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
        error_counter++;
        return;
    }
    else
    {
    /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.*/
    }
}
```

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a>동시에 여러 인터페이스의 DHCP 클라이언트

여러 인터페이스에서 DHCP 클라이언트를 실행하려면 *nx_api.h* 의 NX_MAX_PHYSICAL_INTERFACES를 디바이스에 연결된 실제 인터페이스 수로 설정해야 합니다. 기본적으로 이 값은 1(예: 기본 인터페이스)입니다. 추가 인터페이스를 IP 인스턴스에 등록하려면 *nx_ip_interface_attach* 서비스를 사용합니다. 보조 인터페이스를 연결하는 방법에 대한 자세한 내용은 NetX Duo 사용자 가이드를 참조하세요.

다음 단계는 *nxd_dhcp_client.h* 의 NX_DHCP_CLIENT_MAX_RECORDS를 동시에 DHCP를 실행하는 데 필요한 최대 인터페이스 수로 설정하는 것입니다. NX_DHCP_CLIENT_MAX_RECORDS는 NX_MAX_PHYSICAL_INTERFACES와 같을 필요가 없습니다. 예를 들어 NX_MAX_PHYSICAL_INTERFACES는 3이고, NX_DHCP_CLIENT_MAX_RECORDS는 2일 수 있습니다. 이 구성에서는 세 개의 실제 인터페이스 중 두 개의 인터페이스(그리고 언제든지 세 개의 물리적 인터페이스 중 두 개가 될 수 있음)만 DHCP를 한 번에 실행할 수 있습니다. DHCP 클라이언트 레코드에는 네트워크 인터페이스에 대한 일대일 매핑이 없습니다. 예를 들어 클라이언트 레코드 1은 실제 인터페이스 인덱스 1과 자동으로 상호 연결되지 않습니다.

NX_DHCP_CLIENT_MAX_RECORDS를 NX_MAX_PHYSICAL_INTERFACES보다 더 크게 설정할 수도 있지만, 이렇게 하면 사용되지 않는 클라이언트 레코드를 만들고 메모리를 비효율적으로 사용하게 됩니다.

인터페이스에서 DHCP를 시작하려면 먼저 애플리케이션에서 *nx_dhcp_interface_enable* 을 호출하여 해당 인터페이스를 사용하도록 설정해야 합니다. 예외는 *nx_dhcp_create* 호출에서 자동으로 사용하도록 설정되는 기본 인터페이스입니다. 이는 아래에서 설명하는 *nx_dhcp_interface_disable* 서비스를 사용하여 사용하지 않도록 설정할 수 있습니다.

언제든지 DHCP에 대해 인터페이스를 사용하지 않도록 설정하거나 DHCP를 실행하는 다른 인터페이스와 독립적으로 해당 인터페이스에서 DHCP를 중지할 수 있습니다.

위에서 설명한 대로 특정 인터페이스를 DHCP에 사용하도록 설정하려면 *nx_dhcp_interface_enable* 서비스를 사용하고 입력 인수에서 실제 인터페이스 인덱스를 지정합니다. 인터페이스 인덱스 입력 인수가 NX_MAX_PHYSICAL_INTERFACES 인터페이스보다 작다는 유일한 제한을 사용하여 최대 NX_DHCP_CLIENT_MAX_RECORDS 인터페이스를 사용하도록 설정할 수 있습니다.

특정 인터페이스에서 DHCP를 시작하려면 *nx_dhcp_interface_start* 서비스를 사용합니다. 사용하도록 설정된 모든 인터페이스에서 DHCP를 시작하려면 *nx_dhcp_start* 서비스를 사용합니다. (이미 DHCP를 시작한 인터페이스는 *nx_dhcp_start* 의 영향을 받지 않습니다.)

인터페이스에서 DHCP를 중지하려면 *nx_dhcp_interface_stop* 서비스를 사용합니다. DHCP가 해당 인터페이스에서 이미 시작되어 있어야 합니다. 그렇지 않으면 오류 상태가 반환됩니다. 사용하도록 설정된 모든 인터페이스에서 DHCP를 중지하려면 *nx_dhcp_stop* 서비스를 사용합니다. DHCP는 언제든지 다른 인터페이스와 독립적으로 중지할 수 있습니다.

대부분의 기존 DHCP 클라이언트 서비스에는 'interface'와 동일한 항목이 있습니다. 예를 들어 *nx_dhcp_interface_release* 는 *nx_dhcp_release* 와 동일한 인터페이스입니다. DHCP 클라이언트가 단일 인터페이스에 대해 구성된 경우 동일한 작업을 수행합니다.

일반적으로 인터페이스가 아닌 특정 DHCP 클라이언트 서비스는 모든 인터페이스에 적용되지만 전부는 아닙니다. 후자의 경우 인터페이스가 아닌 특정 서비스가 인터페이스 레코드의 DHCP 클라이언트 목록을 검색할 때 찾은 첫 번째 DHCP 사용 인터페이스에 적용됩니다. DHCP에 대해 여러 인터페이스가 사용하도록 설정되는 경우 인터페이스가 아닌 특정 서비스에서 수행하는 방법은 챕터 3의 **서비스 설명** 을 참조하세요.

아래 예제 시퀀스에서 IP 인스턴스는 두 개의 네트워크 인터페이스를 포함하고 먼저 보조 인터페이스에서 DHCP를 실행합니다. 잠시 후 기본 인터페이스에서 DHCP를 시작합니다. 그런 다음, 기본 인터페이스에서 IP 주소를 해제하고, 기본 인터페이스에서 DHCP를 다시 시작합니다.

```c
nx_dhcp_create(&my_dhcp_client); /* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); /* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); /* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); /* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is restarted on primary interface. */
```

인터페이스 관련 서비스의 전체 목록은 챕터 3의 **서비스 설명** 을 참조하세요.

## <a name="configuration-options"></a>구성 옵션

*nxd_dhcp_client.h* 의 사용자 구성 가능한 DHCP 옵션을 사용하면 호스트 애플리케이션에서 특정 요구 사항에 맞게 DHCP 클라이언트를 미세 조정할 수 있습니다. 이러한 매개 변수의 목록은 다음과 같습니다.  
  
- **NX_DHCP_ENABLE_BOOTP**: 정의되면 이 옵션을 통해 DHCP 대신 BOOTP 프로토콜을 사용할 수 있습니다. 기본값은 사용 안 함입니다.
- **NX_DHCP_CLIENT_RESTORE_STATE**: 정의되면 DHCP 클라이언트에서 임대에 남아 있는 시간을 포함하여 현재 DHCP 클라이언트 라이선스 '상태'를 저장하고 DHCP 클라이언트 애플리케이션 다시 부팅 간에 이 상태를 복원할 수 있습니다. 기본값은 사용 안 함입니다.
- **NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: 설정되면 DHCP 클라이언트에서 자체 패킷 풀을 만들지 않습니다. 호스트 애플리케이션에서 *nx_dhcp_packet_pool_set* 서비스를 사용하여 DHCP 클라이언트 패킷 풀을 설정해야 합니다. 기본값은 사용 안 함입니다.
- **NX_DHCP_CLIENT_SEND_ARP_PROBE**: 정의되면 IP 주소 할당 후 DHCP 클라이언트에서 ARP 프로브를 보내 할당된 DHCP 주소를 다른 호스트에서 소유하고 있지 않은지 확인할 수 있습니다. 이 옵션은 기본적으로 사용되지 않습니다.
- **NX_DHCP_ARP_PROBE_WAIT**: ARP 프로브를 보낸 후 DHCP 클라이언트에서 응답을 기다리는 기간을 정의합니다. 기본값은 1초(1 * NX_IP_PERIODIC_RATE)입니다.
- **NX_DHCP_ARP_PROBE_MIN**: ARP 프로브 전송 간격의 최소 변동을 정의합니다. 기본값은 1초입니다.
- **NX_DHCP_ARP_PROBE_MAX**: ARP 프로브 전송 간격의 최대 변동을 정의합니다. 기본값은 2초입니다.
- **NX_DHCP_ARP_PROBE_NUM**: DHCP 서버에서 할당한 IP 주소를 이미 사용하고 있는지 확인하기 위해 보내는 ARP 프로브 수를 정의합니다. 기본값은 3개 프로브입니다.
- **NX_DHCP_RESTART_WAIT**: DHCP 클라이언트에 할당된 IP 주소를 이미 사용하고 있는 경우 DHCP 클라이언트에서 DHCP를 다시 시작하기 위해 기다리는 시간을 정의합니다. 기본값은 10초입니다.
- **NX_DHCP_CLIENT_MAX_RECORDS**: DHCP 클라이언트 인스턴스에 저장하는 최대 인터페이스 레코드 수를 지정합니다. DHCP 클라이언트 인터페이스 레코드는 특정 인터페이스에서 실행되는 DHCP 클라이언트의 레코드입니다. 기본값은 실제 인터페이스 수(NX_MAX_PHYSICAL_INTERFACES)로 설정됩니다.
- **NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: 정의되면 DHCP 클라이언트에서 최대 DHCP 메시지 크기 옵션을 보낼 수 있습니다. 이 옵션은 기본적으로 사용되지 않습니다.
- **NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: 정의되면 DHCP 클라이언트에서 nx_dhcp_create 호출의 입력 호스트 이름에 잘못된 문자 또는 길이가 있는지 확인할 수 있습니다. 이 옵션은 기본적으로 사용되지 않습니다.
- **NX_DHCP_THREAD_PRIORITY**: DHCP 스레드의 우선 순위입니다. 기본적으로 이 값은 DHCP 스레드가 우선 순위 3에서 실행되도록 지정합니다.
- **NX_DHCP_THREAD_STACK_SIZE**: DHCP 스레드 스택의 크기입니다. 기본값은 2,048바이트입니다.
- **NX_DHCP_TIME_INTERVAL**: DHCP 클라이언트 타이머 만료 함수가 실행되는 간격(초)입니다. 이 함수는 DHCP 프로세스의 모든 간 제한을 업데이트합니다(예: 메시지를 다시 전송해야 하거나 DHCP 클라이언트 상태를 변경해야 하는 경우). 기본값은 1초입니다.
- **NX_DHCP_OPTIONS_BUFFER_SIZE**: DHCP 옵션 버퍼의 크기입니다. 기본값은 312바이트입니다.
- **NX_DHCP_PACKET_PAYLOAD**: DHCP 클라이언트 패킷 페이로드의 크기(바이트)를 지정합니다. 기본값은 NX_DHCP_MINIMUM_IP_DATAGRAM + 실제 헤더 크기입니다. 유선 네트워크의 실제 헤더 크기는 일반적으로 이더넷 프레임 크기입니다.
- **NX_DHCP_PACKET_POOL_SIZE**: DHCP 클라이언트 패킷 풀의 크기를 지정합니다. 기본값은 (5 * NX_DHCP_PACKET_PAYLOAD)이며, 4개의 패킷과 내부 패킷 풀 오버헤드를 위한 공간을 제공합니다.
- **NX_DHCP_MIN_RETRANS_TIMEOUT**: 메시지를 다시 전송하기 전에 클라이언트 메시지에 대한 DHCP 서버 회신을 받기 위한 최소 대기 옵션을 지정합니다. 기본값은 4초(RFC 2131 권장)입니다.
- **NX_DHCP_MAX_RETRANS_TIMEOUT**: 메시지를 다시 전송하기 전에 클라이언트 메시지에 대한 DHCP 서버 회신을 받기 위한 최대 대기 옵션을 지정합니다. 기본값은 64초입니다.
- **NX_DHCP_MIN_RENEW_TIMEOUT**: DHCP 클라이언트가 IP 주소에 바인딩된 후 DHCP 서버 메시지를 받고 갱신 요청을 보내기 위한 최소 대기 옵션을 지정합니다. 기본값은 60초입니다. 그러나 DHCP 클라이언트는 최소 갱신 시간 제한을 기본값으로 설정하기 전에 DHCP 서버 메시지의 갱신 및 리바인딩 만료 시간을 사용합니다.
- **NX_DHCP_TYPE_OF_SERVICE**: DHCP UDP 요청에 필요한 서비스 유형입니다. 기본적으로 이 값은 일반 IP 패킷 서비스를 나타내는 NX_IP_NORMAL로 정의됩니다.
- **NX_DHCP_FRAGMENT_OPTION**: DHCP UDP 요청에 대한 조각을 사용하도록 설정합니다. 기본적으로 이 값은 DHCP UDP 조각화를 사용하지 않도록 설정하는 NX_DONT_FRAGMENT입니다.
- **NX_DHCP_TIME_TO_LIVE**: 이 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다. 기본값은 0x80으로 설정됩니다.
- **NX_DHCP_QUEUE_DEPTH**: 수신 큐의 최대 깊이 수를 지정합니다. 기본값은 4로 설정됩니다.