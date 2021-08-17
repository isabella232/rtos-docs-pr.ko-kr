---
title: 2장 - NAT의 설치 및 사용
description: 이 장에서는 NetX Duo NAT 서비스를 설치, 설정 및 사용하는 방법에 대한 설명을 포함합니다.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e1eb96e53f600eac56f8a82f3ca02ccfdaabf5cc12d95989e1e38e87775ff24f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797384"
---
# <a name="chapter-2---installation-and-use-of-nat"></a>2장 - NAT의 설치 및 사용

이 장에서는 NetX Duo NAT 서비스를 설치, 설정 및 사용하는 방법에 대한 설명을 포함합니다.

## <a name="netx-duo-nat-installation"></a>NetX Duo NAT 설치

NetX Duo NAT는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 사용할 수 있습니다. NetX Duo NAT 패키지에는 다음과 같이 하나의 원본 파일과 하나의 헤더 파일, 데모 애플리케이션 파일 및 이 문서에 대한 PDF 파일이 포함됩니다.

- **nx_nat.c** NetX Duo NAT에 대한 C 원본 파일
- **nx_nat.h** NetX Duo NAT에 대한 C 헤더 파일
- **demo_netx_nat.c** 예제 호스트 NetX Duo C 원본 파일
- **nx_nat.docx** NetX Duo NAT 사용자 가이드에 대한 설명(이 문서)

NetX Duo 및 ThreadX가 설치된 동일한 디렉터리에 NetX Duo NAT 소스 코드 파일을 복사합니다. 예를 들어 NetX Duo 및 ThreadX가 “ *\threadx\mcf5485\green*” 디렉터리에 설치된 경우에는 *nx_nat.c*, *nx_nat.h 및 수정된 NetX Duo 파일* 을 이 디렉터리에 복사해야 합니다. 기존 NetX Duo 파일을 통해 수정된 NetX Duo 파일을 복사합니다. 이더넷 컨트롤러 드라이버 파일을 이 디렉터리에도 복사합니다.

NetX Duo NAT 애플리케이션을 빌드하려면 다음을 수행합니다.

- NetX Duo 라이브러리 *nxduo.a* 는 NX_NAT_ENABLED가 정의된 상태로 빌드되어야 합니다. *nx_user.h* 에서 이 작업을 수행할 수 있습니다.(*nx_user.h* 의 구성 옵션이 빌드에 포함되도록 NX_INCLUDE_USER_DEFINE_FILE도 정의되어 있는지 확인합니다.)
- 애플리케이션 프로젝트는 *tx_api.h* 및 *nx_api.h 뒤에 *nx_nat.h* 를 포함해야 합니다. 후자의 두 헤더 파일은 ThreadX 및 NetX Duo 서비스를 사용하는 데 필요합니다.*
- 그런 다음, 애플리케이션은 *nx_nat_enable* 서비스를 사용하여 이전에 만든 IP 인스턴스에서 NAT를 사용하도록 설정합니다.
- 애플리케이션 코드는 *nx_nat_enable* 및 *nx_nat_disable* 서비스를 호출하여 NAT를 동적으로 사용하거나 사용하지 않도록 설정할 수 있습니다.
- 애플리케이션 프로젝트 코드를 컴파일하고 NAT 사용 NetX Duo 라이브러리와 연결하여 실행 파일을 만듭니다.
- TCP, UDP 또는 ICMP 프로토콜을 사용하는 NAT 연결을 지원하려면 해당 프로토콜을 지원하도록 NetX Duo를 사용하도록 설정해야 합니다. 이 작업은 이전에 만든 IP 인스턴스에 대해 각각 *nx_tcp_enable, nx_udp_enable* 및 *nx_icmp_enable* 을 호출하여 수행됩니다.

## <a name="small-example-demo-nat-setup"></a>간단한 예제 데모 NAT 설정

애플리케이션이 NetX Duo NAT를 설정하는 방법의 예제는 아래 그림 4의 *tx_application_define* 함수에 나와 있습니다. 설치 CD에 배포된 대부분의 NetX Duo 데모 파일과 달리 이 데모는 가상 네트워크 드라이버 *_nx_ram_network_driver*()를 사용하는 Windows PC 대신 두 개의 이더넷 컨트롤러를 사용하는 실제 프로세서 보드에서 실행됩니다. NAT 디바이스는 해당 로컬 인터페이스에서 로컬 스위치를 통해 로컬 도메인에 연결되고 외부 인터페이스에서는 두 번째 스위치를 통해 외부 네트워크에 연결됩니다.

NetXDuo 기본 구성은 demo_netx_nat.c에 표시되어 있습니다. 개인 네트워크는 192.168.2.xx로 정의되고 두 개의 로컬 호스트 노드를 포함합니다. 글로벌 네트워크는 192.168.0.xx로 정의되며 네트워크 패킷을 제외하는 게이트웨이를 192.168.0.1로 정의합니다. NetX Duo IP 인스턴스는 118-171줄에 만들어지고 ‘ram’ 드라이버를 호출합니다. 두 인터페이스를 연결하는 nat_ip 인스턴스는 NAT 라우터 역할을 하며, 인터페이스에 연결된 local_ip 인스턴스는 로컬 호스트로 작동합니다. 하나의 인터페이스가 연결된 external_ip 인스턴스는 외부 호스트 역할을 합니다.

NAT가 252줄에 만들어지고 동적 번역 항목을 저장하는 캐시를 호출합니다. 319줄에서 NAT 기능을 사용하도록 설정하면 362줄에서 정적 번역 항목(인바운드 항목)이 생성되어 외부 호스트에서 로컬 호스트에 액세스할 수 있습니다.

```C
/*
   demo_netx_nat.c

   This is a small demo of NAT (Network Address Translation) on the high-performance
   NetX TCP/IP stack.  This demo relies on ThreadX, NetX and NAT APIs to perform network
   address translation for IP packets traveling between private and external networks.
   this demo concentrates on the ICMP ping operation.
*/

#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_nat.h"

extern void    test_control_return(UINT status);
#if defined NX_NAT_ENABLE && defined __PRODUCT_NETXDUO__ && (NX_MAX_PHYSICAL_INTERFACES >= 2)

#define     DEMO_STACK_SIZE         2048

/* Define the ThreadX and NetX object control blocks...  */

static TX_THREAD                    ntest_0;

/* Set up the NAT components. */

/* Create a NAT instance, packet pool and translation table. */

NX_NAT_DEVICE                       nat_server;
NX_IP                               nat_ip;
NX_IP                               local_ip;
NX_IP                               external_ip;
NX_PACKET_POOL                      nat_packet_pool;
UINT                                error_counter = 0;


/* Configure the NAT network parameters. */

/* Set NetX IP packet pool packet size. This should be less than the Maximum Transmit Unit (MTU) of
   the driver (allow enough room for the Ethernet header plus padding bytes for frame alignment).  */
#define NX_NAT_PACKET_SIZE                          1536


/* Set the size of the NAT IP packet pool.  */
#define NX_NAT_PACKET_POOL_SIZE                     (NX_NAT_PACKET_SIZE * 10)

/* Set NetX IP helper thread stack size. */
#define NX_NAT_IP_THREAD_STACK_SIZE                 2048

/* Set the server IP thread priority */
#define NX_NAT_IP_THREAD_PRIORITY                   2

/* Set ARP cache size of a NAT ip instance. */
#define NX_NAT_ARP_CACHE_SIZE                       1024

/* Set NAT entries memory size. */
#define NX_NAT_ENTRY_CACHE_SIZE                     1024

/* Define NAT IP addresses, local host private IP addresses and external host IP address. */
#define NX_NAT_LOCAL_IPADR              (IP_ADDRESS(192, 168, 2, 1))
#define NX_NAT_LOCAL_HOST1              (IP_ADDRESS(192, 168, 2, 3))
#define NX_NAT_LOCAL_HOST2              (IP_ADDRESS(192, 168, 2, 10))
#define NX_NAT_LOCAL_GATEWAY            (IP_ADDRESS(192, 168, 2, 1))
#define NX_NAT_LOCAL_NETMASK            (IP_ADDRESS(255, 255, 255, 0))
#define NX_NAT_EXTERNAL_IPADR           (IP_ADDRESS(192, 168, 0, 10))
#define NX_NAT_EXTERNAL_HOST            (IP_ADDRESS(192, 168, 0, 100))
#define NX_NAT_EXTERNAL_GATEWAY         (IP_ADDRESS(192, 168, 0, 1))
#define NX_NAT_EXTERNAL_NETMASK         (IP_ADDRESS(255, 255, 255, 0))

/* Create NAT structures for creating NAT tables with static
   entries for local server hosts. */
NX_NAT_TRANSLATION_ENTRY            server_inbound_entry_icmp;

/* Define thread prototypes.  */
static void     ntest_0_entry(ULONG thread_input);
extern void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

    UINT     status;
    UCHAR    *pointer;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Setup the pointer to unallocated memory.  */
    pointer =  (UCHAR *) first_unused_memory;

    /* Create the main thread.  */
    tx_thread_create(&ntest_0, "thread 0", ntest_0_entry, 0,
                     pointer, DEMO_STACK_SIZE,
                     4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Create NAT packet pool. */
    status =  nx_packet_pool_create(&nat_packet_pool, "NAT Packet Pool",
                                    NX_NAT_PACKET_SIZE, pointer,
                                    NX_NAT_PACKET_POOL_SIZE);

    /* Update pointer to unallocated (free) memory. */
    pointer = pointer + NX_NAT_PACKET_POOL_SIZE;

    /* Check status.  */
    if (status)
        return;

    /* Create IP instances for NAT server (global network) */
    status = nx_ip_create(&nat_ip, "NAT IP Instance", NX_NAT_EXTERNAL_IPADR, NX_NAT_EXTERNAL_NETMASK,
                          &nat_packet_pool, _nx_ram_network_driver, pointer,
                          NX_NAT_IP_THREAD_STACK_SIZE, NX_NAT_IP_THREAD_PRIORITY);

    /* Update pointer to unallocated (free) memory. */
    pointer =  pointer + NX_NAT_IP_THREAD_STACK_SIZE;

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the private interface(private network).  */
    status += nx_ip_interface_attach(&nat_ip, "Private Interface", NX_NAT_LOCAL_IPADR,
        NX_NAT_LOCAL_NETMASK, _nx_ram_network_driver);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create IP instances for Local network IP instance */
    status = nx_ip_create(&local_ip, "Local IP Instance", NX_NAT_LOCAL_HOST1, NX_NAT_LOCAL_NETMASK,
                          &nat_packet_pool, _nx_ram_network_driver, pointer,
                          NX_NAT_IP_THREAD_STACK_SIZE, NX_NAT_IP_THREAD_PRIORITY);

    /* Update pointer to unallocated (free) memory. */
    pointer =  pointer + NX_NAT_IP_THREAD_STACK_SIZE;

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create IP instances for external network IP instance */
    status = nx_ip_create(&external_ip, "External IP Instance", NX_NAT_EXTERNAL_HOST,
                        NX_NAT_EXTERNAL_NETMASK,
                        &nat_packet_pool, _nx_ram_network_driver, pointer,
                        NX_NAT_IP_THREAD_STACK_SIZE, NX_NAT_IP_THREAD_PRIORITY);

    /* Update pointer to unallocated (free) memory. */
    pointer =  pointer + NX_NAT_IP_THREAD_STACK_SIZE;

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the global network gateway for NAT IP instance.  */
    status = nx_ip_gateway_address_set(&nat_ip, NX_NAT_EXTERNAL_GATEWAY);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the global network gateway for Local IP instance.  */
    status = nx_ip_gateway_address_set(&local_ip, NX_NAT_LOCAL_GATEWAY);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the global network gateway for External IP instance.  */
    status = nx_ip_gateway_address_set(&external_ip, NX_NAT_EXTERNAL_GATEWAY);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }


    /* Enable ARP and supply ARP cache memory for NAT IP isntance. */
    status =  nx_arp_enable(&nat_ip, (void **) pointer,
                            NX_NAT_ARP_CACHE_SIZE);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    pointer = pointer + NX_NAT_ARP_CACHE_SIZE;

    /* Enable ARP and supply ARP cache memory for Local IP isntance. */
    status =  nx_arp_enable(&local_ip, (void **) pointer,
                            NX_NAT_ARP_CACHE_SIZE);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    pointer = pointer + NX_NAT_ARP_CACHE_SIZE;

    /* Enable ARP and supply ARP cache memory for External IP isntance. */
    status =  nx_arp_enable(&external_ip, (void **) pointer,
                            NX_NAT_ARP_CACHE_SIZE);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    pointer = pointer + NX_NAT_ARP_CACHE_SIZE;

    /* Enable ICMP. */
    nx_icmp_enable(&nat_ip);
    nx_icmp_enable(&local_ip);
    nx_icmp_enable(&external_ip);

    /* Create a NetX NAT server and cache with a global interface index.  */
    status =  nx_nat_create(&nat_server, &nat_ip, 0, pointer, NX_NAT_ENTRY_CACHE_SIZE);

    /* Check status.  */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    pointer = pointer + NX_NAT_ENTRY_CACHE_SIZE;
}

/* Define the test threads.  */

static void    ntest_0_entry(ULONG thread_input)
{

UINT        status;
NX_PACKET   *my_packet;

    /***********************************/
    /*       Disable NAT feature       */
    /***********************************/
    /* Local Host ping External Host address.  */
    status =  nx_icmp_ping(&local_ip, NX_NAT_EXTERNAL_HOST,
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ", 28, &my_packet, 100);

    /* Check status.  */
    if (status == NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Check the NAT forwarded count.  */
#ifndef NX_DISABLE_NAT_INFO
    if ((nat_server.forwarded_packets_received != 0) ||
        (nat_server.forwarded_packets_sent != 0) ||
        (nat_server.arded_packets_dropped != 0))
    {
        error_counter++;
        return;
    }
#endif

    /* External Host ping NAT External address, NAT IP instance will response the requet.  */
    status = nx_icmp_ping(&external_ip, NX_NAT_EXTERNAL_IPADR,
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ", 28, &my_packet, 100);

    /* Check status.  */
    if ((status != NX_SUCCESS) || (my_packet == NX_NULL) || (my_packet -> nx_packet_length != 28))
    {
        error_counter++;
        return;

    /* Check the NAT forwarded count.  */
#ifndef NX_DISABLE_NAT_INFO
    if ((nat_server.forwarded_packets_received != 0) ||
        (nat_server.forwarded_packets_sent != 0) ||
        (nat_server.arded_packets_dropped != 0))
    {
        error_counter++;
        return;
    }
#endif
    }

    /***********************************/
    /*       Enable NAT feature        */
    /***********************************/

    /* Enable the NAT service.  */
    nx_nat_enable(&nat_server);

    /* Local Host ping External Host address.  */
    status =  nx_icmp_ping(&local_ip, NX_NAT_EXTERNAL_HOST,
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ", 28, &my_packet, 100);

    if ((status != NX_SUCCESS) || (my_packet == NX_NULL) || (my_packet -> nx_packet_length != 28))
    {
        error_counter++;
        return;
    }

    /* Check the NAT forwarded count.  */
#ifndef NX_DISABLE_NAT_INFO
    if ((nat_server.forwarded_packets_received != 2) ||
        (nat_server.forwarded_packets_sent != 2) ||
        (nat_server.arded_packets_dropped != 0))
    {
        error_counter++;
        return;
    }
#endif

    /* External Host ping NAT External address, NAT IP instance will response the requet.  */
    status =  nx_icmp_ping(&external_ip, NX_NAT_EXTERNAL_IPADR,
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ", 28, &my_packet, 100);

    if ((status != NX_SUCCESS) || (my_packet == NX_NULL) || (my_packet -> nx_packet_length != 28))
    {
        error_counter++;
        return;
    }

    /* Check the NAT forwarded count.  NAT receive the ping request,
        but can not forward this packet to local network.  discard it.  
#ifndef NX_DISABLE_NAT_INFO
    if ((nat_server.forwarded_packets_received != 3) ||
        (nat_server.forwarded_packets_sent != 2) ||
        (nat_server.arded_packets_dropped != 1))
    {
        error_counter++;
        return;
    }
#endif

    /**********************************************/
    /*       Create an inbound entry for ICMP     */
    /**********************************************/

    /* Calling NAT API to create a inbound entry.  */
    status = nx_nat_inbound_entry_create(&nat_server, &server_inbound_entry_icmp,
        NX_NAT_LOCAL_HOST1, 0, 0, NX_PROTOCOL_ICMP);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* External Host ping NAT External address, LOCAL HOST1 will
        response all inbound icmp request from external network.  */
    status =  nx_icmp_ping(&external_ip, NX_NAT_EXTERNAL_IPADR,
        "ABCDEFGHIJKLMNOPQRSTUVWXYZ", 28, &my_packet, 100);

    if ((status != NX_SUCCESS) || (my_packet == NX_NULL) || (my_packet -> nx_packet_length != 28))
    {
        error_counter++;
        return;
    }

    /* Check the NAT forwarded count.  */
#ifndef NX_DISABLE_NAT_INFO
    if ((nat_server.forwarded_packets_received != 5) ||
        (nat_server.forwarded_packets_sent != 4) ||
        (nat_server.arded_packets_dropped != 1))
    {
        error_counter++;
        return;
    }
#endif
}
#endif
```

**그림 5 - NetX Duo NAT 설정**
