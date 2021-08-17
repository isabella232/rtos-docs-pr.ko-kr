---
title: 2장 - Azure RTOS NetX Duo TFTP 설치 및 사용
description: 이 챕터에서는 Azure RTOS NetX Duo TFTP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ae4e82a0f878af06bd178035cb9429cfe2a14d0bc4bbf848db7d321463586a20
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801260"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-tftp"></a>2장 - Azure RTOS NetX Duo TFTP 설치 및 사용

이 챕터에서는 Azure RTOS NetX Duo TFTP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS NetX Duo는 https://github.com/azure-rtos/netxduo/에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다. 패키지에는 다음 파일이 포함되어 있습니다.


- **nxd_tftp_client.h** NetX Duo TFTP 클라이언트에 대한 헤더 파일

- **nxd_tftp_client.c** NetX Duo TFTP 클라이언트에 대한 C 원본 파일

- **nxd_tftp_server.h** NetX Duo TFTP 서버에 대한 헤더 파일

- **nxd_tftp_server.c** NetX Duo TFTP 서버에 대한 C 원본 파일

- **filex_stub.h** FileX가 없는 경우 스텁 파일

- **nxd_tftp.pdf** NetX Duo TFTP에 대한 PDF 설명

- **demo_netxduo_tftp.c** NetX Duo TFTP 데모

## <a name="tftp-installation"></a>TFTP 설치

NetX Duo TFTP를 사용하기 위해 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사할 수 있습니다. 예를 들어 NetX Duo가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 *nxd_tftp_client.h*, *nxd_tftp_client.c*, *nxd_tftp_server.h* 및 *nxd_tftp_server.c* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="using-tftp"></a>TFTP 사용

TFTP 애플리케이션을 실행하려면 애플리케이션 코드에는 각각 ThreadX, FileX 및 NetX Duo를 사용하기 위해 *tx_api.h, fx_api.h,* 및 *nx_api.h* 가 포함된 후 *nxd_tftp_client.h* 및/또는 nxd_tftp_server.h가 포함되어야 합니다. 애플리케이션 프로젝트에는 빌드 프로세스에 *nxd_tftp_client.c* 및/또는 *nxd_tftp_server.c* 도 포함되어야 합니다. 이 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일해야 하며, 해당 개체 형식은 애플리케이션의 파일과 함께 연결해야 합니다. 이렇게 간단하게 NetX Duo TFTP를 사용할 수 있습니다. *헤더 파일이* 포함되면 애플리케이션 코드는 TFTP 서비스를 사용할 수 있습니다.

> [!NOTE]
> TFTP는 NetX Duo UDP 서비스를 활용하므로 TFTP를 사용하기 전에 *nx_udp_enable* 호출을 통해 UDP를 사용하도록 설정해야 합니다.

## <a name="small-example-system"></a>작은 예제 시스템

NetX Duo TFTP를 사용하는 것이 얼마나 쉬운지 보여 주는 예제가 아래에 표시된 그림 1.1에 설명되어 있습니다. 이 예제에서 TFTP 포함 파일 *nxd_tftp_client.h* 및 *nxd_tftp_server.h* 는 19줄 및 20줄에서 가져옵니다. 다음으로, TFTP 서버는 179줄의 “*tx_application_define*”에서 만들어집니다. 

> [!NOTE]
> TFTP 서버 제어 블록 “*server*”가 이전에 45줄에서 전역 변수로 정의되었습니다. 이 데모에서는 14줄의 TFTP 통신에 IPv4를 사용하도록 선택합니다. 성공적으로 만든 후에는 TFTP 서버가 304줄에서 시작됩니다. 411줄에 TFTP 클라이언트가 만들어집니다. 마지막으로 클라이언트는 450줄에서 파일을 기록하고 485줄에서 다시 파일을 읽습니다.

TFTP 서버 스레드 작업이 중지되고 TFTP 서버가 324줄에서 삭제됩니다. 애플리케이션은 fx_media_close(331줄)를 호출하여 모든 파일을 닫고, 파일 및 디렉터리 데이터를 USB 미디어에 업데이트해야 합니다.

> [!NOTE]
> 이 예제에서는 TFTP 클라이언트 파일 요청을 수신하고 다운로드하는 TFTP 서버 처리에 FileX를 사용합니다. 그러나 NX_TFTP_NO_FILEX가 정의된 경우에는 애플리케이션에 fx_api.h 대신 file_stub.h가 포함될 수 있습니다.
>
> 또한 기존 NetX TFTP 클라이언트 및 서버 애플리케이션은 NetX Duo TFTP와 함께 작동합니다. 그러나 애플리케이션 개발자는 NetX TFTP 애플리케이션을 NetX Duo로 이식하는 것이 좋습니다. 해당하는 NetX TFTP 서비스는 다음과 같습니다.

- *nxd_tftp_server_start*

- *nxd_tftp_server_stop*

- *nxd_tftp_client_file_read*

- *nxd_tftp_client_file_write*

- *nxd_tftp_client_file_open*

```C
/* This is a small demo of TFTP on the high-performance NetX TCP/IP stack. This demo
   relies on ThreadX and NetX Duo, to show a simple file transfer from the client
   and then back to the server. */



/* Indicate if using IPv6. */
#define USE_DUO

/* If the host application is using NetX Duo, determine which IP version to use.
   Make sure IPv6 in NetX Duo is enabled if planning to use TFTP over IPv6 */
#ifdef USE_DUO
#define     IP_TYPE     6
#endif /* USE_DUO        */

#include    "tx_api.h"
#include    "nx_api.h"
#include    "nxd_tftp_client.h"
#include    "nxd_tftp_server.h"
#ifndef     NX_TFTP_NO_FILEX
#include    "fx_api.h"
#endif


#define     DEMO_STACK_SIZE         4096

/* To use another file storage utility define this symbol:
#define NX_TFTP_NO_FILEX
*/

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;

/* Define the NetX TFTP object control blocks. */

NX_TFTP_CLIENT          client;
NX_TFTP_SERVER          server;

/* Define the application global variables */

#define                 CLIENT_ADDRESS  IP_ADDRESS(1, 2, 3, 5)
#define                 SERVER_ADDRESS  IP_ADDRESS(1, 2, 3, 4)

NXD_ADDRESS             server_ip_address;
NXD_ADDRESS             client_ip_address;

UINT                    error_counter = 0;

/* Define buffer used in the demo application. */
UCHAR                   buffer[255];
ULONG                   data_length;


/* Define the memory area for the FileX RAM disk. */
#ifndef NX_TFTP_NO_FILEX
UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];
#endif


/* Define function prototypes. */

VOID    _fx_ram_driver(FX_MEDIA *media_ptr);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
void    client_thread_entry(ULONG thread_input);
void    server_thread_entry(ULONG thread_input);


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
UCHAR   *pointer;


    /* Setup the working pointer. */
    pointer =  (UCHAR *) first_unused_memory;


    /* Create the main TFTP server thread. */
    status = tx_thread_create(&server_thread, "TFTP Server Thread", server_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              4,4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the main TFTP client thread at a slightly lower priority. */
    status = tx_thread_create(&client_thread, "TFTP Client Thread", client_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              5, 5, TX_NO_TIME_SLICE, TX_DONT_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&server_pool, "TFTP Server Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the TFTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status =  nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&server_ip);

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the TFTP server. */
#ifdef USE_DUO
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
    /* Specify the tftp server global address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x102;
#endif
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_ADDRESS;

#endif

    status =  nxd_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#else
    status =  nx_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#endif

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for errors for the server. */
    if (status)
        error_counter++;

    /* Create a packet pool for the TFTP client. */

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&client_pool, "TFTP Client Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the TFTP client. */
    status = nx_ip_create(&client_ip, "TFTP Client IP Instance", CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    status =  nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable UDP for client IP instance. */
    status |=  nx_udp_enable(&client_ip);
    status |= nx_icmp_enable(&client_ip);

    tx_thread_resume(&client_thread);
}

void server_thread_entry(ULONG thread_input)
{

UINT        status, running;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#ifndef  NX_TFTP_NO_FILEX

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry             */
                            ram_disk_memory,                 /* RAM disk memory pointer  */
                            ram_disk_sector_cache,           /* Media buffer pointer     */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size        */
                            "MY_RAM_DISK",                   /* Volume Name              */
                            1,                               /* Number of FATs           */
                            32,                              /* Directory Entries        */
                            0,                               /* Hidden sectors           */
                            256,                            /* Total sectors            */
                            128,                             /* Sector size              */
                            1,                               /* Sectors per cluster      */
                            1,                               /* Heads                    */
                            1);                              /* Sectors per track        */

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory, ram_disk_sector_cache,
                               sizeof(ram_disk_sector_cache));

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

#endif /*  NX_TFTP_NO_FILEX */

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ICMPv6 services. */
    status |= nxd_icmp_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the server. */
    status = nxd_ipv6_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for DAD to validate the address. */
    tx_thread_sleep(500);
#endif

#endif /* IP_TYPE == 6 */

    /* Start the NetX TFTP server. */
#ifdef USE_DUO
    status =  nxd_tftp_server_start(&server);
#else
    status =  nx_tftp_server_start(&server);
#endif

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Run for a while */
    running = NX_TRUE;
    while(running)
        tx_thread_sleep(200);


    /* Stop and delete the TFTP server. */
#ifdef USE_DUO
    nxd_tftp_server_delete(&server);
#else
    nx_tftp_server_delete(&server);
#endif

    /* Close all open files and ensure directory information is also written out to the media.
    This will also flush the file data to USB media*/
    status = fx_media_close(&ram_disk);

    if (status)
    {
        error_counter++;
    }

    return;

}


/* Define the TFTP client thread. */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
UINT        all_done = NX_FALSE;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ECMPv6 services for the client. */
    status = nxd_icmp_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the client. */
    status = nxd_ipv6_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the Client IPv6 address */
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_address.v6[1] = 0xf101;
    client_ip_address.nxd_ip_address.v6[2] = 0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for the link local and global addresses to be validated. */
    tx_thread_sleep(500);
#endif
#endif /*(IP_TYPE == 6) */


    /* The TFTP services used below include the NetX equivalent service which will work with
       NetX Duo TFTP. However, it is recommended for developers to port their applications
       to the newer services that take the NXD_ADDRESS type and support both IPv4 and IPv6
       communication.
    */

    /* Create a TFTP client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool, IP_TYPE);
#else
    status =  nx_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool);
#endif

    /* Check status. */
    if (status)
        return;

    /* Open a TFTP file for writing. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_WRITE, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_WRITE, 100);
#endif

    /* Check status. */
    if (status)
        return;

    /* Allocate a TFTP packet. */
#ifdef USE_DUO
    status =  nxd_tftp_client_packet_allocate(&client_pool, &my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_packet_allocate(&client_pool, &my_packet, 100);
#endif
    /* Check status. */
    if (status)
        error_counter++;

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write this packet to the file via TFTP. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_write(&client, my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_write(&client, my_packet, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Close this file. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Open the same file for reading. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_READ, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_READ, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;
    do
    {

    /* Read the file back. */
#ifdef USE_DUO
        status =  nxd_tftp_client_file_read(&client, &my_packet, 100, IP_TYPE);
#else
        status =  nx_tftp_client_file_read(&client, &my_packet, 100);
#endif
        /* Check for retranmission/dropped packet error. Benign. Try again... */
        if (status == NX_TFTP_INVALID_BLOCK_NUMBER)
        {

            continue;
        }
        else if (status == NX_TFTP_END_OF_FILE)
        {

            /* All done. */
            all_done = NX_TRUE;
        }
        else if (status != NX_SUCCESS)
        {

            /* Internal error, invalid packet or error on read. */
            break;
        }


        /* Do something with the packet data and release when done. */
        nx_packet_data_retrieve(my_packet, buffer, &data_length);
        buffer[data_length] = 0;
        printf("Receive data: %s\n", buffer);

        printf("release packet in demo.\n");

        nx_packet_release(my_packet);

    } while (all_done == NX_FALSE);

    /* Close the file again. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Delete the client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_delete(&client);
#else
    status =  nx_tftp_client_delete(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    return;
}
```

그림 1.1 NetX Duo에서의 TFTP 사용 예제

## <a name="configuration-options"></a>구성 옵션

NetX Duo TFTP를 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음 목록에서 각각에 대해 자세히 설명합니다. 별도로 지정하지 않는 한 이러한 옵션은 *nxd_tftp_client.h* 및 *nxd_tftp_server.h* 에서 확인할 수 있습니다.


- **NX_DISABLE_ERROR_CHECKING** 정의된 경우 이 옵션은 기본 TFTP 오류 검사를 제거합니다. 일반적으로 애플리케이션이 디버깅된 후에 사용됩니다.

- **NX_TFTP_SERVER_PRIORITY** TFTP 서버 스레드의 우선 순위입니다. 기본적으로 이 값은 우선 순위 16을 지정하는 16으로 정의되어 있습니다.

- **NX_TFTP_SERVER_TIME_SLICE** 동일한 우선 순위의 다른 스레드에 생성하기 전에 TFTP 서버를 실행하는 시간 조각입니다. 기본값은 2입니다.

- **NX_TFTP_MAX_CLIENTS** 서버에서 한 번에 처리할 수 있는 최대 클라이언트 수입니다. 기본적으로 이 값은 10으로, 한 번에 10개의 클라이언트를 지원합니다.

- **NX_TFTP_ERROR_STRING_MAX** 오류 문자열의 최대 문자 수입니다. 기본적으로 이 값은 64입니다.

- **NX_TFTP_NO_FILEX** 정의된 경우 이 옵션은 FileX 종속성에 대한 스텁을 제공합니다. 이 옵션이 정의된 경우 TFTP 클라이언트는 변경 없이 작동합니다. TFTP 서버는 제대로 작동하기 위해 수정되거나 사용자가 몇 가지 FileX 서비스를 만들어야 합니다.

- **NX_TFTP_TYPE_OF_SERVICE** TFTP UDP 요청에 필요한 서비스 유형입니다. 기본적으로 이 값은 NX_IP_NORMAL로 정의되어 정상적인 IP 패킷 서비스를 나타냅니다.

- **NX_TFTP_FRAGMENT_OPTION** TFTP UDP 요청에 대한 조각을 사용하도록 설정합니다. 기본적으로 이 값은 TFTP UDP 조각화를 사용하지 않도록 설정하는 NX_DONT_FRAGMENT입니다.

- **NX_TFTP_TIME_TO_LIVE** 이 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다. 기본값은 0x80으로 설정됩니다.

- **NX_TFTP_SOURCE_PORT** 이 옵션을 선택하면 TFTP 클라이언트 애플리케이션에서 TFTP 클라이언트 UDP 소켓 포트를 지정할 수 있습니다. 기본값은 NX_ANY_PORT입니다.

- ***NX_TFTP_SERVER_RETRANSMIT_ENABLE*** TFTP 서버의 타이머가 최근 작업(ACK 또는 데이터 패킷)에 대해 각 TFTP 클라이언트 세션을 확인할 수 있도록 합니다. 최대 횟수 이후에 세션 제한 시간이 만료되면 연결이 끊어진 것으로 간주됩니다. 서버는 클라이언트 요청을 지우고 열려 있는 모든 파일을 닫고 다음 클라이언트에서 연결 요청을 사용할 수 있도록 합니다. 기본 설정은 사용 안 함입니다.

- **NX_TFTP_SERVER_TIMEOUT_PERIOD** TFTP 서버 타이머 항목 함수가 패킷 수신에 대한 클라이언트 연결을 확인하는 간격을 지정합니다. 기본값은 20(타이머 틱)입니다.

- **NX_TFTP_SERVER_RETRANSMIT_TIMEOUT** 클라이언트에서 유효한 ACK 또는 데이터 패킷을 수신하는 시간 제한입니다. 기본값은 200(타이머 틱)입니다 *.*

- **NX_TFTP_SERVER_MAX_RETRIES** 클라이언트 세션 재전송 제한 시간을 갱신하는 최대 횟수를 지정합니다. 그런 다음, 서버에서 세션을 닫습니다.

- **NX_TFTP_MAX_CLIENT_RETRANSMITS** 클라이언트에게 오류 메시지 전송 및 세션 닫기 없이 서버가 삭제하는 클라이언트로부터 중복된 ACK 또는 데이터 패킷을 수신하는 최대 횟수를 지정합니다. NX_TFTP_SERVER_RETRANSMIT_ENABLE이 정의된 경우에는 영향을 주지 않습니다.
