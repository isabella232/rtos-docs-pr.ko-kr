---
title: 2장 - Azure RTOS NetX Duo AutoIP의 설치 및 사용
description: 이 장에서는 Azure RTOS NetX Duo AutoIP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 42c58a4cdec34a03eda9f42315438e5fbe2ea594
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810986"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a>2장 - Azure RTOS NetX Duo AutoIP의 설치 및 사용

이 장에서는 Azure RTOS NetX Duo AutoIP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS NetX AutoIP는 [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/)에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다. 패키지에는 다음과 같이 3개의 원본 파일, 하나의 포함 파일 및 이 문서를 포함하는 PDF 파일이 포함되어 있습니다.

- **nx_auto_ip.h**: NetX AutoIP의 헤더 파일
- **nx_auto_ip.c**: NetX AutoIP의 C 원본 파일
- **demo_netx_auto_ip.c**: NetX AutoIP 데모의 C 원본 파일
- **nx_auto_ip.pdf**: NetX AutoIP의 PDF 설명

## <a name="autoip-installation"></a>AutoIP 설치

NetX AutoIP를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX가 " *\threadx\arm7\green*" 디렉터리에 설치된 경우 *nx_auto_ip.h*, *nx_auto_ip.c* 및 *demo_netx_auto_ip.c* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="using-autoip"></a>AutoIP 사용

NetX AutoIP를 사용하는 것은 쉽습니다. 기본적으로 애플리케이션 코드는 ThreadX 및 NetX를 사용하기 위해 *tx_api.h* 및 *nx_api.h* 를 포함한 후 *nx_auto_ip.h* 를 포함해야 합니다. *nx_auto_ip.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 AutoIP 함수 호출을 수행할 수 있습니다. 애플리케이션은 빌드 프로세스에 *nx_auto_ip.c* 도 포함해야 합니다. 이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 해당 개체 형식을 애플리케이션의 파일에 연결해야 합니다. 이는 NetX AutoIP를 사용하는 데 필요합니다.

> [!NOTE]
> AutoIP는 NetX ARP 서비스를 활용하므로 AutoIP를 사용하기 전에 *nx_arp_enable* 호출로 ARP를 사용하도록 설정해야 합니다.

## <a name="small-example-system"></a>간단한 예제 시스템

NetX AutoIP를 사용하는 것이 얼마나 쉬운지 보여 주는 예제는 아래에 표시된 그림 1.1에 설명되어 있습니다. 이 예제에서 AutoIP 포함 파일 *nx_auto_ip.h* 는 002줄에서 가져옵니다. 그런 다음, NetX AutoIP 인스턴스가 090줄에서 "*tx_application_define*"에 만들어집니다. NetX AutoIP 제어 블록 "auto_ip_0"은 이전에 015줄에서 전역 변수로 정의되었습니다. 생성이 완료되면 NetX AutoIP가 098줄에서 시작됩니다. IP 주소 변경 콜백 함수 처리는 이후 충돌 또는 가능한 DHCP 주소 확인을 처리하는 데 사용되는 105줄에서 시작됩니다.

> [!NOTE]
> 아래 예제에서는 호스트 디바이스가 단일 홈 디바이스인 것으로 가정합니다. 멀티홈 디바이스의 경우 호스트 애플리케이션은 NetX AutoIP 서비스 *nx_auto_ip_interface_* 집합을 사용하여 IP 주소를 검색하는 보조 네트워크 인터페이스를 지정할 수 있습니다. 멀티홈 애플리케이션 설정에 대한 자세한 내용은 [NetX 사용자 가이드](https://docs.microsoft.com/azure/rtos/netx/about-this-guide)를 참조하세요. 호스트 애플리케이션에서 NetX API *nx_status_ip_interface_check* 를 사용하여 AutoIP가 IP 주소를 가져왔는지 확인해야 합니다.

```c
#include "tx_api.h"
#include "nx_api.h"
#include "nx_auto_ip.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD              thread_0;
NX_PACKET_POOL         pool_0;
NX_IP                  ip_0;

/* Define the AUTO IP structures for the IP instance. */

NX_AUTO_IP             auto_ip_0;

/* Define the counters used in the demo application... */

ULONG                 thread_0_counter;
ULONG                 address_changes;
ULONG                 error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);
void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    16, 16, 1, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
                                    pointer, 4096);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Create an IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
        error_counter++;

    /* Create the AutoIP instance for IP Instance 0. */
    status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Check AutoIP create status. */
    if (status)
        error_counter++;

    /* Start AutoIP instances. */
    status = **nx_auto_ip_start**(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);

    /* Check AutoIP start status. */
    if (status)
        error_counter++;

    /* Register an IP address change function for IP Instance 0. */
    status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
                                        (void *) &auto_ip_0);

    /* Check IP address change notify status. */
    if (status)
        error_counter++;
}

/* Define the test thread. */

void     thread_0_entry(ULONG thread_input)
{

UINT     status;
ULONG    actual_status;

    /* Wait for IP address to be resolved. */
    do
    {

        /* Call IP status check routine. */
        status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
            &actual_status, 10000);

    } while (status != NX_SUCCESS);

    /* Since the IP address is resolved at this point, the application can now fully utilize NetX! */

    while(1)
    {

        /* Increment thread 0's counter. */
        thread_0_counter++;

        /* Sleep... */
        tx_thread_sleep(10);
    }
}

void          ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
{

ULONG         ip_address;
ULONG         network_mask;
NX_AUTO_IP    *auto_ip_ptr;

    /* Setup pointer to auto IP instance. */
    auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;

    /* Pickup the current IP address. */
    nx_ip_address_get(ip_ptr, &ip_address, &network_mask);

    /* Determine if the IP address has changed back to zero. If so, make sure the AutoIP instance is started. */
    if (ip_address == 0)
    {

        /* Get the last AutoIP address for this node. */
        nx_auto_ip_get_address(auto_ip_ptr, &ip_address);

        /* Start this AutoIP instance. */
        nx_auto_ip_start(auto_ip_ptr, ip_address);
        }

    /* Determine if IP address has transitioned to a non local IP address. */
    else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
    {

        /* Stop the AutoIP processing. */
        nx_auto_ip_stop(auto_ip_ptr);
    }

    /* Increment a counter. */
    address_changes++;
}
```

그림 1.1 NetX에서의 AutoIP 사용 예제

## <a name="configuration-options"></a>구성 옵션

NetX AutoIP를 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음은 각각에 대해 자세히 설명된 모든 옵션의 목록입니다.

- **NX_DISABLE_ERROR_CHECKING**: 정의된 이 옵션은 기본 AutoIP 오류 검사를 제거합니다. 일반적으로 애플리케이션이 디버깅된 후에 사용됩니다.
- **NX_AUTO_IP_PROBE_WAIT**: 첫 번째 프로브를 보내기 전에 대기하는 시간(초)입니다. 기본적으로 이 값은 1로 정의됩니다.
- **NX_AUTO_IP_PROBE_NUM**: 보낼 ARP 프로브 수입니다. 기본적으로 이 값은 3으로 정의됩니다.
- **NX_AUTO_IP_PROBE_MIN**: 전송 프로브 사이에 대기하는 최소 시간(초)입니다. 기본적으로 이 값은 1로 정의됩니다.
- **NX_AUTO_IP_PROBE_MAX**: 전송 프로브 사이에 대기하는 최대 시간(초)입니다. 기본적으로 이 값은 2로 정의됩니다.
- **NX_AUTO_IP_MAX_CONFLICTS**: 처리 지연을 증가시키기 전에 AutoIP 충돌 수입니다. 기본적으로 이 값은 10으로 정의됩니다.
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL**: 총 충돌 수를 초과하는 경우 대기 기간을 연장하는 시간(초)입니다. 기본적으로 이 값은 60으로 정의됩니다.
- **NX_AUTO_IP_ANNOUNCE_WAIT**: 알림을 보내기 전에 대기하는 시간(초)입니다. 기본적으로 이 값은 2로 정의됩니다.
- **NX_AUTO_IP_ANNOUNCE_NUM**: 보낼 ARP 알림의 수입니다. 기본적으로 이 값은 2로 정의됩니다.
- **NX_AUTO_IP_ANNOUNCE_INTERVAL**: 알림 전송 사이에 대기하는 시간(초)입니다. 기본적으로 이 값은 2로 정의됩니다.
- **NX_AUTO_IP_DEFEND_INTERVAL**: 방어 알림 사이에 대기하는 시간(초)입니다. 기본적으로 이 값은 10으로 정의됩니다.
