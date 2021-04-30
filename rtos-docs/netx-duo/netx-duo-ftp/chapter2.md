---
title: 2장 - FTP의 설치 및 사용
description: 이 장에서는 NetX Duo FTP 서비스의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ac58658af93f59556d99d340ae38570908d63fc1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810794"
---
# <a name="chapter-2---installation-and-use-of-ftp"></a><span data-ttu-id="4c7d1-103">2장 - FTP의 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="4c7d1-103">Chapter 2 - Installation and use of FTP</span></span>

<span data-ttu-id="4c7d1-104">이 장에서는 NetX Duo FTP 서비스의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-104">This chapter contains a description of various issues related to installation, set up, and usage of the NetX Duo FTP services.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="4c7d1-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="4c7d1-105">Product Distribution</span></span>

<span data-ttu-id="4c7d1-106">NetX Duo FTP는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-106">NetX Duo FTP is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="4c7d1-107">패키지에는 다음과 같이 이 문서를 포함하는 두 개의 원본 파일과 PDF 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="4c7d1-108">**nxd_ftp_client.h** NetX Duo FTP 클라이언트에 대한 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="4c7d1-108">**nxd_ftp_client.h** Header file for NetX Duo FTP Client</span></span>
- <span data-ttu-id="4c7d1-109">**nxd_ftp_client.c** NetX Duo FTP 클라이언트에 대한 C 원본 파일</span><span class="sxs-lookup"><span data-stu-id="4c7d1-109">**nxd_ftp_client.c** C Source file for NetX Duo FTP Client</span></span>
- <span data-ttu-id="4c7d1-110">**nxd_ftp_server.h** NetX Duo FTP 서버에 대한 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="4c7d1-110">**nxd_ftp_server.h** Header file for NetX Duo FTP Server</span></span>
- <span data-ttu-id="4c7d1-111">**nxd_ftp_server.c** NetX Duo FTP 서버에 대한 C 원본 파일</span><span class="sxs-lookup"><span data-stu-id="4c7d1-111">**nxd_ftp_server.c** C Source file for NetX Duo FTP Server</span></span>
- <span data-ttu-id="4c7d1-112">**filex_stub.h** FileX가 없는 경우 스텁 파일</span><span class="sxs-lookup"><span data-stu-id="4c7d1-112">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="4c7d1-113">**nxd_ftp.pdf** NetX Duo용 FTP에 대한 PDF 설명서</span><span class="sxs-lookup"><span data-stu-id="4c7d1-113">**nxd_ftp.pdf** PDF description of FTP for NetX Duo</span></span>
- <span data-ttu-id="4c7d1-114">**demo_netxduo_ftp.c** FTP 데모 시스템</span><span class="sxs-lookup"><span data-stu-id="4c7d1-114">**demo_netxduo_ftp.c** FTP demonstration system</span></span>

## <a name="netx-duo-ftp-installation"></a><span data-ttu-id="4c7d1-115">NetX Duo FTP 설치</span><span class="sxs-lookup"><span data-stu-id="4c7d1-115">NetX Duo FTP Installation</span></span>

<span data-ttu-id="4c7d1-116">NetX Duo FTP API를 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-116">In order to use the NetX Duo FTP API, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="4c7d1-117">예를 들어 NetX Duo가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 *nxd_ftp_client.h* 및 *nxd_ftp_client.c* 를 FTP 클라이언트 애플리케이션에 대한 이 디렉터리에 복사하고 *nxd_ftp_server.h* 및 *nxd_ftp_server.c* 파일을 FTP 서버 애플리케이션에 대한 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-117">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_ftp_client.h* and *nxd_ftp_client.c* should be copied into this directory for FTP Client applications, and *nxd_ftp_server.h* and *nxd_ftp_server.c* files should be copied into this directory for FTP Server applications.</span></span>

## <a name="using-netx-duo-ftp"></a><span data-ttu-id="4c7d1-118">NetX Duo FTP 사용</span><span class="sxs-lookup"><span data-stu-id="4c7d1-118">Using NetX Duo FTP</span></span>

<span data-ttu-id="4c7d1-119">NetX Duo FTP API를 사용하는 것은 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-119">Using the NetX Duo FTP API is easy.</span></span> <span data-ttu-id="4c7d1-120">기본적으로 애플리케이션 코드는 각각 ThreadX, FileX 및 NetX Duo를 사용하기 위해 *tx_api.h, fx_api.h* 및 *nx_api.h* 를 포함한 후 FTP 클라이언트 애플리케이션을 위한 *nxd_ftp_client.h* 또는 FTP 서버 애플리케이션을 위한 *nxd_ftp_server* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-120">Basically, the application code must include either *nxd_ftp_client.h* for FTP Client applications or *nxd_ftp_server* for FTP Server applications, after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX Duo, respectively.</span></span> <span data-ttu-id="4c7d1-121">빌드 프로젝트는 FTP 소스 코드와 호스트 애플리케이션 파일, ThreadX 및 NetX 라이브러리 파일을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-121">The build project must include the FTP source code and the host application file, and of course the ThreadX and NetX library files.</span></span> <span data-ttu-id="4c7d1-122">이렇게 간단하게 NetX Duo FTP를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-122">This is all that is required to use NetX Duo FTP.</span></span>

<span data-ttu-id="4c7d1-123">또한 FTP는 NetX Duo TCP 서비스를 활용하므로 FTP를 사용하기 전에 *nx_tcp_enable* 호출을 통해 TCP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-123">Note that since FTP utilizes NetX Duo TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using FTP.</span></span>

<span data-ttu-id="4c7d1-124">NetX Duo 라이브러리는 IPv6에 대해 사용하도록 설정되어 있지만 여전히 IPv4 네트워크도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-124">Note that the NetX Duo library can be enabled for IPv6 and still support IPv4 networks.</span></span> <span data-ttu-id="4c7d1-125">단, NetX Duo는 IPv6을 사용하도록 설정한 경우에만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-125">However, NetX Duo cannot support IPv6 unless it is enabled.</span></span> <span data-ttu-id="4c7d1-126">NetX Duo에서 IPv6 처리를 사용하지 않도록 설정하려면 **NX_DISABLE_IPV6** 을 *nx_user.h* 파일에서 정의해야 하며, 해당 파일은 *nx_port.h* 파일에서 **NX_INCLUDE_USER_DEFINE_FILE** 을 정의하여 NetX Duo 라이브러리 빌드에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-126">To disable IPv6 processing in NetX Duo, the **NX_DISABLE_IPV6** must be defined in the *nx_user.h* file, and that file must be included in the NetX Duo library build by defining **NX_INCLUDE_USER_DEFINE_FILE** in the *nx_port.h* file.</span></span> <span data-ttu-id="4c7d1-127">기본적으로 **NX_DISABLE_IPV6** 은 정의되어 있지 않습니다(IPv6이 사용하도록 설정됨).</span><span class="sxs-lookup"><span data-stu-id="4c7d1-127">By default, **NX_DISABLE_IPV6** is not defined (IPv6 is enabled).</span></span> <span data-ttu-id="4c7d1-128">이는 IP 작업에서 IPv6 프로토콜 및 서비스를 설정하는 *nxd_ipv6_enable* 서비스와 다르며 **NX_DISABLE_IPV6** 을 정의하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-128">This is different from the *nxd_ipv6_enable* service that sets up the IPv6 protocols and services on the IP task, and requires **NX_DISABLE_IPV6** to be not defined.</span></span>

## <a name="small-example-system-of-netx-duo-ftp"></a><span data-ttu-id="4c7d1-129">NetX Duo FTP의 작은 예제 시스템</span><span class="sxs-lookup"><span data-stu-id="4c7d1-129">Small Example System of NetX Duo FTP</span></span>

<span data-ttu-id="4c7d1-130">NetX Duo FTP를 사용하는 것이 얼마나 쉬운지 보여 주는 예제가 아래에 표시된 그림 1.1에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-130">An example of how easy it is to use NetX Duo FTP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="4c7d1-131">이 예제에서는 FTP 서버와 FTP 클라이언트를 모두 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-131">In this example, both an FTP Server and an FTP Client are created.</span></span> <span data-ttu-id="4c7d1-132">따라서 FTP 포함 파일 *nxd_ftp_client.h와 nxd_ftp_server.h* 는 모두 10줄 및 11줄에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-132">Therefore both FTP include files *nxd_ftp_client.h and nxd_ftp_server.h are* brought in at line 10 and 11.</span></span> <span data-ttu-id="4c7d1-133">다음으로, FTP 서버는 99줄의 “*tx_application_define*”에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-133">Next, the FTP Server is created in “*tx_application_define*” at line 99.</span></span> <span data-ttu-id="4c7d1-134">FTP 서버 및 클라이언트 제어 블록은 이전의 26줄에서 전역 변수로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-134">Note that the FTP Server and Client control blocks are defined as global variables at line 26 previously.</span></span>

<span data-ttu-id="4c7d1-135">이 데모에서는 NetX Duo FTP 및 레거시 IPv4 제한 FTP 서비스에서 제공되는 Duo 함수를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-135">This demo shows how to use the duo functions available in NetX Duo FTP as well as the legacy IPv4 limited FTP services.</span></span> <span data-ttu-id="4c7d1-136">이 데모에서는 IPv6 함수를 사용하기 위해 16줄에서 USE_IPV6을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-136">To use the IPv6 functions, the demo defines USE_IPV6 in line 16</span></span>

<span data-ttu-id="4c7d1-137">162줄에서 호스트 애플리케이션에서 IPv4 및 IPv6을 모두 지원하는 USE_IPV6을 정의하는 경우 FTP 서버가 \***nxd_ftp_server_create** _로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-137">At line 162 the FTP Server is created with \***nxd_ftp_server_create** _ if the host application defines USE_IPV6 which supports both IPv4 and IPv6.</span></span> <span data-ttu-id="4c7d1-138">그렇지 않으면 FTP 서버는 IPv4 제한 서비스를 사용하여 166줄에서 _ \*_nx_ftp_server_create_\*\*로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-138">If it is not, the FTP Server is created with _ *_nx_ftp_server_create_*\* on line 166 with the IPv4 limited service.</span></span> <span data-ttu-id="4c7d1-139">Duo 함수는 IPv4 서비스와는 다른 로그인 및 로그아웃 함수 인수를 사용합니다. 두 함수는 모두 534-568줄에서 파일의 맨 아래에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-139">Note that the ‘duo’ function uses different login and logout function arguments than the IPv4 service, both of which are defined at the bottom of the file on lines 534 -568.</span></span>

<span data-ttu-id="4c7d1-140">그런 다음, FTP 서버는 FTP 서버 스레드 입력 함수의 466줄에서 시작하여 NetX Duo를 통해 IPv6 주소(글로벌 및 링크 로컬)를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-140">The FTP server must then establish its IPv6 address (global and link local) with NetX Duo, starting at line 466 in the FTP server thread entry function.</span></span> <span data-ttu-id="4c7d1-141">그러면 FTP 서버가 518줄에서 시작되고 FTP 클라이언트 요청에 대해 준비됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-141">The FTP server is then started on line 518 and is ready for FTP client requests.</span></span>

<span data-ttu-id="4c7d1-142">FTP 클라이언트는 316줄에 생성되어 FTP 서버와 동일한 프로세스를 거칩니다. FTP 클라이언트 IP 작업 IPv6이 사용하도록 설정되며 해당 IPv6 주소는 263-313줄부터 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-142">The FTP Client is created in line 316 and goes through the same process as the FTP Server to get the FTP Client IP task IPv6 enabled, and its IPv6 addresses validated starting on lines 263-313.</span></span>

<span data-ttu-id="4c7d1-143">그런 다음, 클라이언트가 USE_IPV6을 정의한 경우 334줄에서 또는 IPv4 제한된 서비스 \*_nx_ftp_client_connect_\*\*를 사용하는 경우 340줄에서 \***nxd_ftp_client_connect** _를 사용하여 FTP 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-143">Then the Client connects to the FTP Server using ***nxd_ftp_client_connect** _ in line 334 if it has defined USE_IPV6, or line 340 if it is using the IPv4 limited service _*_nx_ftp_client_connect_\*\*.</span></span> <span data-ttu-id="4c7d1-144">FTP 클라이언트 스레드 함수를 통해 FTP 서버에 파일을 기록하고 연결을 끊기 전에 다시 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-144">Over the course of the FTP Client thread function, it writes a file to the FTP server and reads it back before disconnecting.</span></span>

```C
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack.  This demo
   relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
   and then back to the server.  */



#include    "tx_api.h"
#include    "fx_api.h"
#include    "nx_api.h"
#include    "nxd_ftp_client.h"
#include    "nxd_ftp_server.h"

#define     DEMO_STACK_SIZE         4096

#ifdef FEATURE_NX_IPV6
#define USE_IPV6
#endif /* FEATURE_NX_IPV6 */


/* Define the ThreadX, NetX, and FileX object control blocks...  */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;


/* Define the NetX FTP object control blocks.  */

NX_FTP_CLIENT           ftp_client;
NX_FTP_SERVER           ftp_server;


/* Define the counters used in the demo application...  */

ULONG                   error_counter = 0;


/* Define the memory area for the FileX RAM disk.  */

UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];


#define FTP_SERVER_ADDRESS  IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS  IP_ADDRESS(1,2,3,5)

extern UINT  _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                        VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                        CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                        UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                        UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions.  */
VOID    _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);


void    client_thread_entry(ULONG thread_input);
void    thread_server_entry(ULONG thread_input);


#ifdef USE_IPV6
/* Define NetX Duo IP address for the NetX Duo FTP Server and Client. */
NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;
endif


/* Define server login/logout functions.  These are stubs for functions that would
   validate a client login request.   */

#ifdef USE_IPV6
UINT    server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
#else
UINT    server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
#endif


/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return(0);
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

    UINT    status;
    UCHAR   *pointer;


    /* Setup the working pointer.  */
    pointer =  (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry, 0,
                     pointer, DEMO_STACK_SIZE,
                     4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize NetX.  */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server.  */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool", 256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors.  */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server.  */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", FTP_SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance.  */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP.  */
    nx_tcp_enable(&server_ip);

#ifdef USE_IPV6

    /* Next set the NetX Duo FTP Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Create the FTP server.  */
    status =  nxd_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login6, server_logout6);
#else
    /* Create the FTP server.  */
    status =  nx_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login, server_logout);
#endif
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread.  */
    status = tx_thread_create(&client_thread, "FTP Client thread ", client_thread_entry, 0,
            pointer, DEMO_STACK_SIZE,
            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE ;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client.  */
    status =  nx_packet_pool_create(&client_pool, "NetX Client Packet Pool", 256, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the FTP client.  */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP.  */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance.  */
    nx_tcp_enable(&client_ip);

    return;

}

/* Define the FTP client thread.  */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;

#ifdef USE_IPV6
UINT        iface_index, address_index;
#endif


    /* Format the RAM disk - the memory for the RAM disk was defined above.  */
    status = _fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry                */
                            ram_disk_memory,                 /* RAM disk memory pointer     */
                            ram_disk_sector_cache,           /* Media buffer pointer        */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size           */
                            "MY_RAM_DISK",                   /* Volume Name                 */
                            1,                               /* Number of FATs              */
                            32,                              /* Directory Entries           */
                            0,                               /* Hidden sectors              */
                            256,                             /* Total sectors               */
                            128,                             /* Sector size                 */
                            1,                               /* Sectors per cluster         */
                            1,                               /* Heads                       */
                            1);                              /* Sectors per track           */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk.  */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
        ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Let the IP threads and driver initialize the system.    */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP Client IPv6 enabled. */
    status = nxd_ipv6_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    status = nxd_icmp_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Set the Client link local and global addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Let NetX Duo validate the addresses. */
    tx_thread_sleep(400);

#endif  /* USE_IPV6 */

    /* Create an FTP client.  */
    status =  nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Created the FTP Client\n");

#ifdef USE_IPV6

    do
    {

        /* Now connect with the NetX Duo FTP (IPv6) server. */
        status =  nxd_ftp_client_connect(&ftp_client, &server_ip_address, "name", "password", 100);
    } while (status != NX_SUCCESS);

#else

    /* Now connect with the NetX FTP (IPv4) server. */
    status =  nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS, "name", "password", 100);

#endif  /* USE_IPV6 */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet.  */
    status =  nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer.  */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt.  */
    status =  nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");


    /* Close the file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");


    /* Now open the same file for reading.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file.  */
    status =  nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
            printf("Reread the FTP client test.txt file\n");
            nx_packet_release(my_packet);
    }

    /* Close this file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server.  */
    status =  nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;


    /* Delete the FTP client.  */
    status =  nx_ftp_client_delete(&ftp_client);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
}


/* Define the helper FTP server thread.  */
void    thread_server_entry(ULONG thread_input)
{

    UINT            status;
#ifdef  USE_IPV6
    UINT            iface_index, address_index;
#endif

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP server IPv6 enabled. */
    status = nxd_ipv6_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    status = nxd_icmp_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the link local address with the host MAC address. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Wait while NetX Duo validates the link local and global address. */
    tx_thread_sleep(500);

#endif /* USE_IPV6 */

    /* OK to start the FTP Server.   */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute.    */
    tx_thread_relinquish();

    return;
}


#ifdef USE_IPV6
UINT  server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    NXD_ADDRESS *client_ipduo_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged in6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
                     UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#else
UINT  server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#endif  /* USE_IPV6 */
```

<span data-ttu-id="4c7d1-145">**그림 1.1 NetX Duo FTP의 예제**</span><span class="sxs-lookup"><span data-stu-id="4c7d1-145">**Figure 1.1 Example of NetX Duo FTP**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="4c7d1-146">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="4c7d1-146">Configuration Options</span></span>

<span data-ttu-id="4c7d1-147">NetX FTP 및 NetX Duo FTP를 빌드하기 위한 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-147">There are several configuration options for building NetX FTP and NetX Duo FTP.</span></span> <span data-ttu-id="4c7d1-148">기본값은 나열되지만 각 정의는</span><span class="sxs-lookup"><span data-stu-id="4c7d1-148">The default values are listed, but each define can be set by the</span></span>

<span data-ttu-id="4c7d1-149">지정된 NetX Duo FTP 헤더 파일을 포함하기 전의 애플리케이션에 의해 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-149">application prior to inclusion of the specified NetX Duo FTP header file.</span></span> <span data-ttu-id="4c7d1-150">헤더 파일을 지정하지 않은 경우에는 *nxd_ftp_client.h와 nxd_ftp_server.h* 모두에서 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-150">If no header file is specified, the option is available in both *nxd_ftp_client.h and nxd_ftp_server.h*.</span></span> <span data-ttu-id="4c7d1-151">다음 목록에서 각각에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-151">The following list describes each in detail:</span></span>

- <span data-ttu-id="4c7d1-152">**NX_FTP_SERVER_PRIORITY** FTP 서버 스레드의 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-152">**NX_FTP_SERVER_PRIORITY** The priority of the FTP Server thread.</span></span> <span data-ttu-id="4c7d1-153">기본적으로 이 값은 우선 순위 16을 지정하는 16으로 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-153">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="4c7d1-154">**NX_FTP_MAX_CLIENTS** 서버에서 한 번에 처리할 수 있는 최대 클라이언트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-154">**NX_FTP_MAX_CLIENTS** The maximum number of Clients the Server can handle at one time.</span></span> <span data-ttu-id="4c7d1-155">기본적으로 이 값은 4로, 한 번에 4개의 클라이언트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-155">By default, this value is 4 to support 4 Clients at once.</span></span>
- <span data-ttu-id="4c7d1-156">**NX_FTP_SERVER_MIN_PACKET_PAYLOAD** TCP, IP 및 네트워크 프레임 헤더와 HTTP 데이터를 비롯한 서버 패킷 풀 페이로드의 최소 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-156">**NX_FTP_SERVER_MIN_PACKET_PAYLOAD** The minimum size of the Server packet pool payload in bytes, including TCP, IP and network frame headers plus HTTP data.</span></span> <span data-ttu-id="4c7d1-157">기본값은 256(FileX의 최대 파일 이름 길이) + 12바이트(파일 정보) 및 NX_PHYSICAL_TRAILER입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-157">The default value is 256 (maximum length of filename in FileX) + 12 bytes for file information, and NX_PHYSICAL_TRAILER.</span></span>
- <span data-ttu-id="4c7d1-158">**NX_FTP_SERVER_TIMEOUT** 내부 서비스가 일시 중단할 ThreadX 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-158">**NX_FTP_SERVER_TIMEOUT** Specifies the number of ThreadX  ticks that internal services will  suspend for.</span></span> <span data-ttu-id="4c7d1-159">기본값은 1초(1 \* NX_IP_PERIODIC_RATE)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-159">The default value  is set to 1 second (1 \*  NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="4c7d1-160">**NX_FTP_ACTIVITY_TIMEOUT** 작업이 없는 경우 클라이언트 연결을 유지 관리하는 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-160">**NX_FTP_ACTIVITY_TIMEOUT** Specifies the number of seconds  a Client connection is maintained  if there is no activity.</span></span> <span data-ttu-id="4c7d1-161">기본값은 240으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-161">The default  value is set to 240.</span></span>
- <span data-ttu-id="4c7d1-162">**NX_FTP_TIMEOUT_PERIOD** 서버에서 클라이언트 작업을 확인하는 간격(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-162">**NX_FTP_TIMEOUT_PERIOD** Specifies the intervals in seconds  when the Server checks for  Client activity.</span></span> <span data-ttu-id="4c7d1-163">기본값은 60으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-163">The default value is set to 60.</span></span>
- <span data-ttu-id="4c7d1-164">**NX_FTP_SERVER_RETRY_SECONDS** 서버 응답을 재전송하기까지의 초기 제한 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-164">**NX_FTP_SERVER_RETRY_SECONDS** Specifies the initial timeout in seconds before retransmitting server response.</span></span> <span data-ttu-id="4c7d1-165">기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-165">The default value is 2.</span></span>
- <span data-ttu-id="4c7d1-166">**NX_FTP_SERVER_TRANSMIT_QUEUE_DEPTH** 서버 소켓에서 대기 중인 전송 패킷의 최대 깊이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-166">**NX_FTP_SERVER_TRANSMIT_QUEUE_DEPTH** Specifies the maximum of depth of queued transmit packets on Server socket.</span></span> <span data-ttu-id="4c7d1-167">기본값은 20입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-167">The default value is 20.</span></span>
- <span data-ttu-id="4c7d1-168">**NX_FTP_SERVER_RETRY_MAX** 패킷당 최대 다시 시도 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-168">**NX_FTP_SERVER_RETRY_MAX** Specifies the maximum retries per packet.</span></span> <span data-ttu-id="4c7d1-169">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-169">The default value is 10.</span></span>
- <span data-ttu-id="4c7d1-170">**NX_FTP_SERVER_RETRY_SHIFT** 재시도 시간 제한을 설정할 때 이동할 비트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-170">**NX_FTP_SERVER_RETRY_SHIFT** Specifies the number of bits to shift in setting the retry timeout.</span></span> <span data-ttu-id="4c7d1-171">기본값은 2입니다. 예를 들어 모든 재시도 시간 제한은 이전 재시도 시간의 두 배입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-171">The default value is 2, e.g. every retry timeout is twice as long as the previous retry.</span></span>
- <span data-ttu-id="4c7d1-172">**NX_FTP_NO_FILEX** 정의된 경우 이 옵션은 FileX 종속성에 대한 스텁을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-172">**NX_FTP_NO_FILEX** Defined, this option provides a  stub for FileX dependencies.</span></span> <span data-ttu-id="4c7d1-173">이 옵션이 정의된 경우 FTP 클라이언트는 변경 없이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-173">The  FTP Client will function without  any change if this option is  defined.</span></span> <span data-ttu-id="4c7d1-174">FTP 서버는 제대로 작동하기 위해 수정되거나 사용자가 몇 가지 FileX 서비스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-174">The FTP Server will  need to either be modified or the  user will have to create a handful  of FileX services in order to  function properly.</span></span>
- <span data-ttu-id="4c7d1-175">**NX_FTP_CONTROL_TOS** FTP 제어 요청에 필요한 서비스 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-175">**NX_FTP_CONTROL_TOS** Type of service required for the FTP control requests.</span></span> <span data-ttu-id="4c7d1-176">기본적으로 이 값은 NX_IP_NORMAL로 정의되어 정상적인 IP 패킷 서비스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-176">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="4c7d1-177">**NX_FTP_DATA_TOS** FTP 데이터 요청에 필요한 서비스 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-177">**NX_FTP_DATA_TOS** Type of service required for the FTP data requests.</span></span> <span data-ttu-id="4c7d1-178">기본적으로 이 값은 NX_IP_NORMAL로 정의되어 정상적인 IP 패킷 서비스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-178">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="4c7d1-179">**NX_FTP_FRAGMENT_OPTION** FTP 요청에 대해 조각을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-179">**NX_FTP_FRAGMENT_OPTION** Fragment enable for FTP requests.</span></span> <span data-ttu-id="4c7d1-180">기본적으로 이 값은 FTP TCP 조각화를 사용하지 않도록 설정하는 NX_DONT_FRAGMENT입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-180">By default, this value is NX_DONT_FRAGMENT to disable FTP TCP fragmenting.</span></span>
- <span data-ttu-id="4c7d1-181">**NX_FTP_CONTROL_WINDOW_SIZE** TCP 제어 소켓 창 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-181">**NX_FTP_CONTROL_WINDOW_SIZE** TCP Control socket window size.</span></span> <span data-ttu-id="4c7d1-182">기본적으로 이 값은 400바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-182">By default, this value is 400 bytes.</span></span>
- <span data-ttu-id="4c7d1-183">**NX_FTP_DATA_WINDOW_SIZE** TCP 데이터 소켓 창 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-183">**NX_FTP_DATA_WINDOW_SIZE** TCP Data socket window size.</span></span> <span data-ttu-id="4c7d1-184">기본적으로 이 값은 2048바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-184">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="4c7d1-185">**NX_FTP_TIME_TO_LIVE** 이 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-185">**NX_FTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="4c7d1-186">기본값은 0x80으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-186">The default value is set to 0x80.</span></span>
- <span data-ttu-id="4c7d1-187">**NX_FTP_USERNAME_SIZE** 클라이언트에서 제공한 *사용자 이름* 에 허용되는 바이트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-187">**NX_FTP_USERNAME_SIZE** Specifies the number of bytes allowed in a Client supplied *username*.</span></span> <span data-ttu-id="4c7d1-188">기본값은 20으로 설정되어 있습니다 *.*</span><span class="sxs-lookup"><span data-stu-id="4c7d1-188">The default value is set to 20 *.*</span></span>
- <span data-ttu-id="4c7d1-189">**NX_FTP_PASSWORD_SIZE** 클라이언트에서 제공한 *암호* 에 허용되는 바이트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-189">**NX_FTP_PASSWORD_SIZE** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="4c7d1-190">기본값은 20으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c7d1-190">The default value is set to 20.</span></span>
