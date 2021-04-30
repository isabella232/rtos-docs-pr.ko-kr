---
title: 2장 - Azure RTOS NetX DNS 클라이언트 설치 및 사용
description: 이 장에서는 Azure RTOS NetX DNS 클라이언트의 설치, 설정 및 사용과 관련된 다양한 이슈에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 054b7366eb9a28bc0dc2fb8c4b2479c12532499b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811569"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dns-client"></a><span data-ttu-id="f7f69-103">2장 - Azure RTOS NetX DNS 클라이언트 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="f7f69-103">Chapter 2 - Installation and Use of Azure RTOS NetX DNS Client</span></span>

<span data-ttu-id="f7f69-104">이 장에서는 Azure RTOS NetX DNS 클라이언트의 설치, 설정 및 사용과 관련된 다양한 이슈에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DNS Client.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="f7f69-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="f7f69-105">Product Distribution</span></span>

<span data-ttu-id="f7f69-106">NetX DNS 클라이언트는 <https://github.com/azure-rtos/netx>에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-106">The NetX DNS Client is available at <https://github.com/azure-rtos/netx>.</span></span> <span data-ttu-id="f7f69-107">이 패키지에는 다음과 같은 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-107">The package includes the following files:</span></span>

- <span data-ttu-id="f7f69-108">**nx_dns.h**: NetX DNS 클라이언트에 대한 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="f7f69-108">**nx_dns.h**: Header file for NetX DNS Client</span></span>
- <span data-ttu-id="f7f69-109">**nx_dns.c**: NetX DNS 클라이언트에 대한 C 소스 파일</span><span class="sxs-lookup"><span data-stu-id="f7f69-109">**nx_dns.c**: C Source file for NetX DNS Client</span></span>
- <span data-ttu-id="f7f69-110">**nx_dns.pdf**: NetX DNS 클라이언트에 대한 PDF 설명</span><span class="sxs-lookup"><span data-stu-id="f7f69-110">**nx_dns.pdf**: PDF description of NetX DNS Client</span></span>

## <a name="dns-client-installation"></a><span data-ttu-id="f7f69-111">DNS 클라이언트 설치</span><span class="sxs-lookup"><span data-stu-id="f7f69-111">DNS Client Installation</span></span>

<span data-ttu-id="f7f69-112">NetX DNS 클라이언트를 사용하려면 소스 코드 파일 *nx_dns.c* 및 *nx_dns.h* 를 NetX와 같은 설치 디렉터리에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-112">To use NetX DNS Client, copy the source code files *nx_dns.c* and *nx_dns.h* to the same directory where NetX is installed.</span></span> <span data-ttu-id="f7f69-113">예를 들어 NetX가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 *nx_dns.h* 및 *nx_dns.c* 파일을 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-113">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_dns.h* and *nx_dns.c* files should be copied into this directory.</span></span>

## <a name="using-the-dns-client"></a><span data-ttu-id="f7f69-114">DNS 클라이언트 사용</span><span class="sxs-lookup"><span data-stu-id="f7f69-114">Using the DNS Client</span></span>

<span data-ttu-id="f7f69-115">NetX DNS 클라이언트는 사용하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-115">Using NetX DNS Client is easy.</span></span> <span data-ttu-id="f7f69-116">기본적으로 ThreadX 및 NetX를 사용하기 위해 애플리케이션 코드는 각각 *tx_api.h* 및 *nx_api.h* 를 포함한 다음, *nx_dns.h* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-116">Basically, the application code must include *nx_dns.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="f7f69-117">*nx_dns.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 DNS 함수 호출을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-117">Once *nx_dns.h* is included, the application code is then able to make the DNS function calls specified later in this guide.</span></span> <span data-ttu-id="f7f69-118">또한 애플리케이션에서 빌드 프로세스에 *nx_dns.c* 도 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-118">The application must also add *nx_dns.c* to the build process.</span></span> <span data-ttu-id="f7f69-119">이 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일해야 하며, 해당 개체 형식은 애플리케이션의 파일과 함께 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-119">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="f7f69-120">이렇게 간단하게 NetX DNS를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-120">This is all that is required to use NetX DNS.</span></span>

>[!NOTE]
> <span data-ttu-id="f7f69-121">DNS는 NetX UDP 서비스를 사용하므로 DNS를 사용하기 전에 *nx_udp_enable* 호출을 통해 UDP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-121">Since DNS utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DNS.</span></span>

## <a name="small-example-system-for-dns-client"></a><span data-ttu-id="f7f69-122">DNS 클라이언트용 작은 예제 시스템</span><span class="sxs-lookup"><span data-stu-id="f7f69-122">Small Example System for DNS Client</span></span> 

<span data-ttu-id="f7f69-123">이 섹션에서 제공하는 예제 DNS 애플리케이션 프로그램에서는 *nx_dns.h* 가 6행에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-123">In the example DNS application program provided in this section, *nx_dns.h* is included at line 6.</span></span> <span data-ttu-id="f7f69-124">DNS 클라이언트 애플리케이션이 DNS 클라이언트용 패킷 풀을 만들 수 있게 하는 NX_DNS_CLIENT_USER_CREATE_PACKET_POOL는 21-23행에 선언되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-124">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, which allows the DNS Client application to create the packet pool for the DNS Client, is declared on lines 21-23.</span></span> <span data-ttu-id="f7f69-125">이 패킷 풀은 DNS 메시지를 보내기 위한 패킷을 할당하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-125">This packet pool is used for allocating packets for sending DNS messages.</span></span> <span data-ttu-id="f7f69-126">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL을 정의한 경우 패킷 풀은 71-91행에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-126">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined, a packet pool is created in lines 71-91.</span></span> <span data-ttu-id="f7f69-127">이 옵션을 사용하지 않는 경우 DNS 클라이언트는 *nx_dns.h* 의 구성 매개 변수가 설정한 패킷 페이로드 및 풀 크기에 따라 자체 패킷 풀을 만듭니다. 이에 대해서는 이 장의 다른 부분에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-127">If this option is not enabled, the DNS Client creates its own packet pool as per the packet payload and pool size set by configuration parameters in *nx_dns.h* and described elsewhere in this chapter.</span></span>

<span data-ttu-id="f7f69-128">내부 NetX 작업에 사용되는 클라이언트 IP 인스턴스에 대해 93-105행에서 다른 패킷 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-128">Another packet pool is created in lines 93-105 for the Client IP instance which is used for internal NetX operations.</span></span> <span data-ttu-id="f7f69-129">그런 다음, 107-119행에서 *nx_ip_create* 호출을 사용하여 IP 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-129">Next the IP instance is created using the *nx_ip_create* call in line 107-119.</span></span> <span data-ttu-id="f7f69-130">IP 작업과 DNS 클라이언트가 동일한 패킷 풀을 공유할 수는 있으나, 일반적으로 DNS 클라이언트는 IP 작업에서 보낸 제어 패킷보다 큰 메시지를 전송하므로 별도의 패킷 풀을 사용하면 메모리를 더 효율적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-130">It is possible for the IP task and the DNS Client to share the same packet pool, but since the DNS Client typically sends out larger messages than the control packets sent by the IP task, using separate packet pools makes more efficient use of memory.</span></span>

<span data-ttu-id="f7f69-131">ARP 및 UDP(IPv4 네트워크에서 사용)는 각각 122행과 134행에서 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-131">ARP and UDP (which is used by IPv4 networks) are enabled in lines 122 and 134 respectively.</span></span>

>[!NOTE]
> <span data-ttu-id="f7f69-132">이 데모에서는 37행에 선언되고 *nx_ip_create* 호출에 사용 되는 ‘ram’ 드라이버를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-132">This demo uses the ‘ram’ driver declared on line 37 and used in the *nx_ip_create* call.</span></span> <span data-ttu-id="f7f69-133">이 RAM 드라이버는 NetX 소스 코드와 함께 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-133">This ram driver is distributed with the NetX source code.</span></span> <span data-ttu-id="f7f69-134">실제로 DNS 클라이언트를 실행하려면 애플리케이션이 DNS 서버로부터의 패킷 송수신을 위해 실제 네트워크 드라이버를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-134">To actually run the DNS Client the application must supply an actual physical network driver to transmit and receive packets from the DNS server.</span></span>

<span data-ttu-id="f7f69-135">클라이언트 스레드 입력 함수 *thread_client_entry* 는 *tx_application_define* 함수 아래에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-135">The Client thread entry function *thread_client_entry* is defined below the *tx_application_define* function.</span></span> <span data-ttu-id="f7f69-136">처음에는 네트워크 드라이버에서 IP 작업 스레드를 초기화할 수 있도록 시스템에 제어 권한을 내어줍니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-136">It initially relinquishes control to the system to allow the IP task thread to be initialized by the network driver.</span></span>

<span data-ttu-id="f7f69-137">그런 다음, 176-187행에서 DNS 클라이언트를 만들고, 189-200행에서 캐시를 초기화하며, 202-217행에서 이전에 만든 패킷 풀을 DNS 클라이언트 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-137">It then creates the DNS Client on lines 176-187, initializes the cache on lines 189-200, and sets the packet pool previously created to the DNS Client instance on lines 202-217.</span></span> <span data-ttu-id="f7f69-138">다음으로 220-229행에서 IPv4 DNS 서버를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-138">It then adds an IPv4 DNS server on lines 220-229.</span></span>

<span data-ttu-id="f7f69-139">예제 프로그램의 나머지 부분에서는 DNS 클라이언트 서비스를 사용하여 DNS 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-139">The remainder of the example program uses the DNS Client services to make DNS queries.</span></span> <span data-ttu-id="f7f69-140">호스트 IP 주소 조회는 240 및 262행에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-140">Host IP address lookups are performed on lines 240 and 262.</span></span> <span data-ttu-id="f7f69-141">이 두 서비스 *nx_dns_host_by_name_get* 과 *nx_dns_ipv4_address_by_name_get* 에서, 전자는 한 IP 주소만 저장하지만 후자는 DNS 서버가 답할 경우 여러 주소를 저장한다는 점이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-141">The difference between these two services, *nx_dns_host_by_name_get* and *nx_dns_ipv4_address_by_name_get*, is that the former only saves one IP address, while the latter saves multiple addresses if DNS Server replied.</span></span>

<span data-ttu-id="f7f69-142">역방향 조회(IP 주소의 호스트 이름)는 354행(*nx_dns_host_by_address_get*)에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-142">Reverse lookups (host name from IP address) are performed on lines 354 (*nx_dns_host_by_address_get*).</span></span>

<span data-ttu-id="f7f69-143">DNS 조회를 위한 다른 두 서비스인 CNAME 및 TXT는 입력 도메인 이름에 대해 CNAME 및 TXT를 검색하기 위해 각각 375행과 420행에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-143">Two more services for DNS lookups, CNAME and TXT, are demonstrated on lines 375 and 420 respectively, to discover CNAME and TXT for the input domain name.</span></span> <span data-ttu-id="f7f69-144">NetX DNS 클라이언트는 다른 레코드 형식(예: NS, MX, SRV 및 SOA)에 대해 유사하게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-144">NetX DNS Client as similar services for other record types, e.g. NS, MX, SRV and SOA.</span></span> <span data-ttu-id="f7f69-145">NetX DNS 클라이언트에서 사용할 수 있는 모든 레코드 형식 조회에 대한 자세한 설명은 3장을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7f69-145">See Chapter 3 for detailed descriptions of all record type lookups available in NetX DNS Client.</span></span>

<span data-ttu-id="f7f69-146">594행에서 DNS 클라이언트가 *Nx_dns_delete* 서비스를 사용하여 삭제되었을 때, DNS 클라이언트가 자체 패킷 풀을 만든 경우가 아니라면 DNS 클라이언트에 대한 패킷 풀이 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-146">When the DNS Client is deleted on line 594, using the *nx_dns_delete* service, the packet pool for the DNS Client is not deleted unless the DNS Client created its own packet pool.</span></span> <span data-ttu-id="f7f69-147">이 경우 더 이상 사용하지 않으려는 패킷 풀을 애플리케이션이 직접 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-147">Otherwise, it is up to the application to delete the packet pool if it has no further use for it.</span></span>

```c
/* This is a small demo of DNS Client for the high-performance NetX TCP/IP stack.*/
#include "tx_api.h"
#include "nx_api.h"
#include "nx_udp.h"
#include "nx_dns.h"

#define     DEMO_STACK_SIZE         4096
#define     NX_PACKET_PAYLOAD       1536
#define     NX_PACKET_POOL_SIZE     30 * NX_PACKET_PAYLOAD
#define     LOCAL_CACHE_SIZE        2048

/* Define the ThreadX and NetX object control blocks... */

NX_DNS             client_dns;
TX_THREAD          client_thread;
NX_IP              client_ip;
NX_PACKET_POOL     main_pool;

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL
    NX_PACKET_POOL client_pool;
#endif

UCHAR       local_cache[LOCAL_CACHE_SIZE];
UINT        error_counter = 0;
#define     CLIENT_ADDRESS IP_ADDRESS(192,168,0,11)
#define     DNS_SERVER_ADDRESS IP_ADDRESS(192,168,0,1)

/* Define thread prototypes. */
void        thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern     VOID _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define main entry point. */
int main()
{
/* Enter the ThreadX kernel. */
    tx_kernel_enter();
}
/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    CHAR     *pointer;
    UINT     status;
    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;
    /* Create the main thread. */
    tx_thread_create(&client_thread, "Client thread", 
                     thread_client_entry, 0, pointer, 
                     DEMO_STACK_SIZE, 4, 4, TX_NO_TIME_SLICE, 
                     TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /*Create the packet pool for the DNS Client to send packets. If the DNS Client is configured for letting the host application create the DNS packet pool, 
        (see NX_DNS_CLIENT_USER_CREATE_PACKET_POOL option), see 77 nx_dns_create() for guidelines on packet payload size and pool size. 
        packet traffic for NetX processes.
    */

    status = nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                   NX_DNS_PACKET_PAYLOAD, pointer, 
                                   NX_DNS_PACKET_POOL_SIZE);

    pointer = pointer + NX_DNS_PACKET_POOL_SIZE;
    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

#endif
/* Create the packet pool which the IP task will use to send packets. Also available to the host 94 application to send packet. */

    status = nx_packet_pool_create(&main_pool, "Main Packet Pool", 
                                   NX_PACKET_PAYLOAD, pointer, 
                                   NX_PACKET_POOL_SIZE);
    pointer = pointer + NX_PACKET_POOL_SIZE;

/* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

/* Create an IP instance for the DNS Client. */
    status = nx_ip_create(&client_ip, "DNS Client IP Instance", 
                          CLIENT_ADDRESS, 0xFFFFFF00UL, 
                          &main_pool, _nx_ram_network_driver, 
                          pointer, 2048, 1);
    pointer = pointer + 2048;

/* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }
/* Enable ARP and supply ARP cache memory for the DNS Client IP. */
    status = nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

/* Check for ARP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }
/* Enable UDP traffic because DNS is a UDP based protocol. */

    status = nx_udp_enable(&client_ip);
/* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

}

#define BUFFER_SIZE 200
#define RECORD_COUNT 10

/* Define the Client thread. */
void thread_client_entry(ULONG thread_input)
{
    UCHAR         record_buffer[200];
    UINT          record_count;
    UINT          status;
    ULONG         host_ip_address;
    UINT          i;
    ULONG         *ipv4_address_ptr[RECORD_COUNT];

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
    NX_DNS_NS_ENTRY    *nx_dns_ns_entry_ptr[RECORD_COUNT];
    NX_DNS_MX_ENTRY    *nx_dns_mx_entry_ptr[RECORD_COUNT];
    NX_DNS_SRV_ENTRY    *nx_dns_srv_entry_ptr[RECORD_COUNT];
    NX_DNS_SOA_ENTRY    *nx_dns_soa_entry_ptr;
    ULONG                host_address;
    USHORT               host_port;
#endif

    /* Give NetX IP task a chance to get initialized . */
    tx_thread_sleep(100);
    /* Create a DNS instance for the Client. Note this function will create the DNS Client packet pool for creating DNS message packets intended for querying its DNS server. */
    status = nx_dns_create(&client_dns, &client_ip, (UCHAR *)"DNS Client");

    /* Check for DNS create error. */
    if (status)
    {
        error_counter++;
        return;
    }

#ifdef NX_DNS_CACHE_ENABLE
    /* Initialize the cache. */
    status = nx_dns_cache_initialize(&client_dns, local_cache, LOCAL_CACHE_SIZE);

    /* Check for DNS cache error. */
    if (status)
    {
        error_counter++;
        return;
    }
#endif

/* Is the DNS client configured for the host application to create the pecket pool? */
#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /* Yes, use the packet pool created above which has appropriate payload size for DNS messages. */
    status = nx_dns_packet_pool_set(&client_dns, &client_pool);
    /* Check for set DNS packet pool error. */
        
    if (status)
    {
        error_counter++;
        return;
    }
#endif /* NX_DNS_CLIENT_USER_CREATE_PACKET_POOL */

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);
    /* Check for DNS add server error. */
    if (status)
    {
        error_counter++;
        return;
    }
/********************************************************************************/
/* Type A */
/* Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/

    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }
    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, &record_count, 400);
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test A: ");
        printf("record_count = %d \n", record_count);
    }
    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
               *ipv4_address_ptr[i] >> 24,
               *ipv4_address_ptr[i] >> 16 & 0xFF,
               *ipv4_address_ptr[i] >> 8 & 0xFF,
               *ipv4_address_ptr[i] & 0xFF);
    }
/********************************************************************************/
/* Type A + CNAME response */
/* Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/
    
    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test A + CNAME response: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }

    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, 
                                             &record_count, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test Test A + CNAME response: ");
        printf("record_count = %d \n", record_count);
    }
    
    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }

/********************************************************************************/
/* Type PTR */
/* Send PTR type DNS Query to its DNS server and get the host name. */
/********************************************************************************/

    /* Look up host name over IPv4. */
    host_ip_address = IP_ADDRESS(74, 125, 71, 106);
    status = nx_dns_host_by_address_get(&client_dns, host_ip_address, &record_buffer[0], BUFFER_SIZE, 450);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test PTR: %s\n", record_buffer);
    }

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
/********************************************************************************/
/* Type CNAME */
/* Send CNAME type DNS Query to its DNS server and get the canonical name . */
/********************************************************************************/

    /* Send CNAME type to record the canonical name of host in record_buffer. */

    status = nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com", 
                              &record_buffer[0], BUFFER_SIZE, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test CNAME: %s\n", record_buffer);
    }
/********************************************************************************/
/* Type TXT */
/* Send TXT type DNS Query to its DNS server and get descriptive text. */
/********************************************************************************/

    /* Send TXT type to record the descriptive test of host in record_buffer. */
    status = nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test TXT: %s\n", record_buffer);
    }

/********************************************************************************/
/* Type NS */
/* Send NS type DNS Query to its DNS server and get the domain name server. */
/********************************************************************************/

    /* Send NS type to record multiple name servers in record_buffer and return the name server count. If the DNS response includes the IPv4 addresses of name server, record it similarly in record_buffer. */

    status = nx_dns_domain_name_server_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                           &record_buffer[0], BUFFER_SIZE, 
                                           &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test NS: ");
        printf("record_count = %d \n", record_count);
    }
    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY));
        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
            printf("hostname = %s\n", nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/* Type MX */
/* Send MX type DNS Query to its DNS server and get the domain mail exchange. */
/********************************************************************************/

    /* Send MX DNS query type to record multiple mail exchanges in record_buffer and return the mail exchange count. If the DNS response includes the IPv4 addresses of mail exchange, record it similarly in record_buffer. */

    status = nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test MX: ");
        printf("record_count = %d \n", record_count);
    }
    /* Get the mail exchange. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)(record_buffer + i * sizeof(NX_DNS_MX_ENTRY));
        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/* Type SRV */
/* Send SRV type DNS Query to its DNS server and get the location of services. */
/********************************************************************************/

    /* Send SRV DNS query type to record the location of services in record_buffer and return count. If the DNS response includes the IPv4 addresses of service name, record it similarly in record_buffer. */

    status = nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                       &record_buffer[0], BUFFER_SIZE, &record_count, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);
    }
    
    /* Get the location of services. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY));
        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);

        printf("port number = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
        printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
        printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );

        if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
            printf("hostname = %s\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

    /* Get the service info, NetX old API.*/
    status = nx_dns_info_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                     &host_address, &host_port, 200);
    /* Check for DNS add server error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test SRV: ");
        printf("IP address: %d.%d.%d.%d\n",
                host_address >> 24,
                host_address >> 16 & 0xFF,
                host_address >> 8 & 0xFF,
                host_address & 0xFF);
        printf("port number = %d\n", host_port);
    }
    
/********************************************************************************/
/* Type SOA */
/* Send SOA type DNS Query to its DNS server and get zone of start of authority.*/
/********************************************************************************/

    /* Send SOA DNS query type to record the zone of start of authority in record_buffer. */

    status = nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    
    /* Get the loc*/
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
    printf("------------------------------------------------------> n");
    printf("Test SOA: \n");
    printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
    printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
    printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
    printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
    printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
        printf("host mname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
    else
        printf("host mame is not set\n");
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
        printf("host rname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
    else
        printf("host rname is not set\n");
    #endif

    /* Shutting down...*/
    /* Terminate the DNS Client thread. */
    status = nx_dns_delete(&client_dns);
    return;
}
```

## <a name="configuration-options"></a><span data-ttu-id="f7f69-148">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="f7f69-148">Configuration Options</span></span>

<span data-ttu-id="f7f69-149">NetX용 DNS를 빌드하기 위한 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-149">There are several configuration options for building DNS for NetX.</span></span> <span data-ttu-id="f7f69-150">이러한 옵션은 *nx_dns.h* 에서 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-150">These options can be redefined in *nx_dns.h.*</span></span> <span data-ttu-id="f7f69-151">다음 목록에서 각각에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-151">The following list describes each in detail:</span></span>  

- <span data-ttu-id="f7f69-152">**NX_DNS_TYPE_OF_SERVICE**: DNS UDP 요청에 필요한 서비스 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-152">**NX_DNS_TYPE_OF_SERVICE**: Type of service required for the DNS UDP requests.</span></span> <span data-ttu-id="f7f69-153">기본적으로 이 값은 일반 IP 패킷 서비스에 대한 NX_IP_NORMAL로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-153">By default, this value is defined as NX_IP_NORMAL for normal IP packet service.</span></span>

- <span data-ttu-id="f7f69-154">**NX_DNS_TIME_TO_LIVE**: 패킷을 버리기 전까지 패킷이 통과할 수 있는 최대 라우터 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-154">**NX_DNS_TIME_TO_LIVE**: Specifies the maximum number of routers a packet can pass before it is discarded.</span></span> <span data-ttu-id="f7f69-155">기본값은 0x80입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-155">The default value is 0x80</span></span>

- <span data-ttu-id="f7f69-156">**NX_DNS_FRAGMENT_OPTION**: 나가는 패킷의 조각화를 허용하거나 금지하도록 소켓 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-156">**NX_DNS_FRAGMENT_OPTION**: Sets the socket property to allow or disallow fragmentation of outgoing packets.</span></span> <span data-ttu-id="f7f69-157">기본값은 NX_DONT_FRAGMENT입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-157">The default value is NX_DONT_FRAGMENT.</span></span>

- <span data-ttu-id="f7f69-158">**NX_DNS_QUEUE_DEPTH**: 소켓 수신 큐에 저장할 최대 패킷 수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-158">**NX_DNS_QUEUE_DEPTH**: Sets the maximum number of packets to store on the socket receive queue.</span></span> <span data-ttu-id="f7f69-159">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-159">The default value is 5.</span></span>

- <span data-ttu-id="f7f69-160">**NX_DNS_MAX_SERVERS**: 클라이언트 서버 목록에서 최대 DNS 서버 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-160">**NX_DNS_MAX_SERVERS**: Specifies the maximum number of DNS Servers in the Client server list.</span></span>

- <span data-ttu-id="f7f69-161">**NX_DNS_MESSAGE_MAX**: DNS 쿼리를 보내기 위한 최대 DNS 메시지 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-161">**NX_DNS_MESSAGE_MAX**: The maximum DNS message size for sending DNS queries.</span></span> <span data-ttu-id="f7f69-162">기본값은 512입니다 .이 값은 RFC 1035 섹션 2.3.4에 지정된 최대 크기이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-162">The default value is 512, which is also the maximum size specified in RFC 1035 Section 2.3.4.</span></span>

- <span data-ttu-id="f7f69-163">**NX_DNS_PACKET_PAYLOAD_UNALIGNED**: 정의되지 않은 경우 이더넷, IP(또는 IPv6) 및 UDP 헤더에서 정의한 클라이언트 패킷 페이로드의 크기와, NX_DNS_MESSAGE_MAX에서 지정한 최대 DNS 메시지 크기의 합입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-163">**NX_DNS_PACKET_PAYLOAD_UNALIGNED**: If not defined, the size of the Client packet payload which includes the Ethernet, IP (or IPv6), and UDP headers plus the maximum DNS message size specified by NX_DNS_MESSAGE_MAX.</span></span> <span data-ttu-id="f7f69-164">정의 여부와 관계없이 패킷 페이로드는 NX_DNS_PACKET_PAYLOAD에 4바이트로 맞춰져 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-164">Regardless if defined, the packet payload is the 4-byte aligned and stored in NX_DNS_PACKET_PAYLOAD.</span></span>

- <span data-ttu-id="f7f69-165">**NX_DNS_PACKET_POOL_SIZE**: NX_DNS_CLIENT_USER_CREATE_PACKET_POOL을 정의하지 않은 경우, DNS 쿼리를 보내기 위한 클라이언트 패킷 풀의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-165">**NX_DNS_PACKET_POOL_SIZE**: Size of the Client packet pool for sending DNS queries if NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is not defined.</span></span> <span data-ttu-id="f7f69-166">기본값은 NX_DNS_PACKET_PAYLOAD에서 정의한 페이로드 크기의 패킷 16개에 충분할 만큼 크며, 4 바이트로 맞춰집니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-166">The default value is large enough for 16 packets of payload size defined by NX_DNS_PACKET_PAYLOAD, and is 4-byte aligned.</span></span>

- <span data-ttu-id="f7f69-167">**NX_DNS_MAX_RETRIES**: DNS 클라이언트가 다른 서버를 시도하거나 DNS 쿼리를 중단하기 전까지, 현재 DNS 서버를 쿼리하는 최대 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-167">**NX_DNS_MAX_RETRIES**: The maximum number of times the DNS Client will query the current DNS server before trying another server or aborting the DNS query.</span></span>

- <span data-ttu-id="f7f69-168">**NX_DNS_MAX_RETRANS_TIMEOUT**: DNS 쿼리에서 특정 DNS 서버에 대한 최대 재전송 시간 제한입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-168">**NX_DNS_MAX_RETRANS_TIMEOUT**: The maximum retransmission timeout on a DNS query to a specific DNS server.</span></span> <span data-ttu-id="f7f69-169">기본값은 64초(64 \*NX_IP_PERIODIC_RATE)입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-169">The default value is 64 seconds (64 \*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="f7f69-170">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER**: 정의된 상태에서 클라이언트 IPv4 게이트웨이 주소가 0이 아닌 경우, DNS 클라이언트는 IPv4 게이트웨이를 클라이언트의 주 DNS 서버로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-170">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER**: If defined and the Client IPv4 gateway address is non zero, the DNS Client sets the IPv4 gateway as the Client’s primary DNS server.</span></span> <span data-ttu-id="f7f69-171">기본값은 사용 안 함입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-171">The default value is disabled.</span></span>

- <span data-ttu-id="f7f69-172">**NX_DNS_PACKET_ALLOCATE_TIMEOUT**: DNS 클라이언트 패킷 풀에서 패킷을 할당하는 제한 시간 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-172">**NX_DNS_PACKET_ALLOCATE_TIMEOUT**: This sets the timeout option for allocating a packet from the DNS client packet pool.</span></span> <span data-ttu-id="f7f69-173">기본값은 1초(1\*NX_IP_PERIODIC_RATE)입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-173">The default value is 1 second (1\*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="f7f69-174">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL**: DNS 클라이언트에서 애플리케이션이 DNS 클라이언트 패킷 풀을 만들고 설정하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-174">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL**: This enables the DNS Client to let the application create and set the DNS Client packet pool.</span></span> <span data-ttu-id="f7f69-175">기본적으로 이 옵션은 사용하지 않도록 설정되어 있고 DNS 클라이언트는 *nx_dns_create* 에서 자체 패킷 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-175">By default this option is disabled, and the DNS Client creates its own packet pool in *nx_dns_create*.</span></span>

- <span data-ttu-id="f7f69-176">**NX_DNS_CLIENT_CLEAR_QUEUE**: DNS 클라이언트가 새 쿼리를 보내기 전에 수신 큐의 오래된 DNS 메시지를 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-176">**NX_DNS_CLIENT_CLEAR_QUEUE**: This enables the DNS Client to clear old DNS messages off the receive queue before sending a new query.</span></span> <span data-ttu-id="f7f69-177">이러한 이전 DNS 쿼리의 패킷을 제거하면 DNS 클라이언트 소켓 큐에서 오버플로 및 유효 패킷 폐기를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-177">Removing these packets from previous DNS queries prevents the DNS Client socket queue from overflowing and dropping valid packets.</span></span>

- <span data-ttu-id="f7f69-178">**NX_DNS_ENABLE_EXTENDED_RR_TYPES**: DNS 클라이언트가 다른 DNS 레코드 형식(예: CNAME, NS, MX, SOA, SRV 및 TXT)에 대해 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-178">**NX_DNS_ENABLE_EXTENDED_RR_TYPES**: This enables the DNS Client to query on additional DNS record types in (e.g. CNAME, NS, MX, SOA, SRV and TXT).</span></span>

- <span data-ttu-id="f7f69-179">**NX_DNS_CACHE_ENABLE**: DNS 클라이언트가 DNS 캐시에 응답 레코드를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f69-179">**NX_DNS_CACHE_ENABLE**: This enables the DNS Client to store the answer records into DNS cache.</span></span>
