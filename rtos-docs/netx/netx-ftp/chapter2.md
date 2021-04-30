---
title: 2장 - Azure RTOS NetX FTP 설치 및 사용
description: 이 장에서는 Azure RTOS NetX FTP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 812422566b9761baac5f9c2477dba1f0fcc0a778
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811539"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-ftp"></a>2장 - Azure RTOS NetX FTP 설치 및 사용

이 장에서는 Azure RTOS NetX FTP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS NetX는 [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/])에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다. 이 패키지에는 다음과 같이 두 개의 원본 파일과 이 문서가 포함된 PDF 파일이 포함되어 있습니다.

- **nx_ftp.h**: NetX용 FTP에 대한 헤더 파일
- **nx_ftp_client.c** NetX용 FTP 클라이언트에 대한 C 원본 파일
- **nx_ftp_server.c** NetX용 FTP 서버에 대한 C 원본 파일
- **filex_stub.h**: FileX가 없는 경우 스텁 파일
- **nx_ftp.pdf** NetX용 FTP에 대한 PDF 설명서
- **demo_netx_ftp.c**: FTP 데모 시스템

## <a name="ftp-installation"></a>FTP 설치

NetX용 FTP를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX가 " *\threadx\arm7\green*" 디렉터리에 설치된 경우 *nx_ftp.h*, *nx_ftp_client.c* 및 *nx_ftp_server.c* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="using-ftp"></a>FTP 사용

NetX용 FTP를 사용하는 것은 쉽습니다. 기본적으로 애플리케이션 코드는 ThreadX, FileX 및 NetX를 각각 사용하기 위해 *tx_api.h, fx_api.h* 및 *nx_api.h* 를 포함한 후 *nx_ftp.h* 를 포함해야 합니다. *nx_ftp.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 FTP 함수 호출을 수행할 수 있습니다. 또한 애플리케이션에서는 *nx_ftp_client.c* 및 *nx_ftp_server.c* 를 빌드 프로세스에 포함해야 합니다. 이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 해당 개체 형식을 애플리케이션의 파일에 연결해야 합니다. 이는 NetX FTP를 사용하는 데 필요합니다.

> [!NOTE]
> FTP는 NetX TCP 서비스를 활용하므로 FTP를 사용하기 전에 *nx_tcp_enable* 호출을 통해 TCP를 사용하도록 설정해야 합니다.

## <a name="small-example-system"></a>간단한 예제 시스템

NetX FTP를 사용하는 것이 얼마나 쉬운지 보여 주는 예제가 아래에 표시된 그림 1.1에 설명되어 있습니다.

> [!NOTE]
> 이는 단일 네트워크 인터페이스가 있는 호스트 디바이스에 사용됩니다.

이 예제에서 FTP 포함 파일 *nx_ftp_client.h* 및 *nx_ftp_server.h* 는 10줄과 11줄에서 가져옵니다. 다음으로, FTP 서버는 134줄의 "*tx_application_define*"에서 만들어집니다. FTP 서버 제어 블록 "*Server*"가 이전에 31줄에서 전역 변수로 정의되었습니다. 성공적으로 만든 후에는 FTP 서버가 363줄에서 시작됩니다. 183줄에 FTP 클라이언트가 만들어집니다. 마지막으로 클라이언트는 229줄에서 파일을 기록하고 318줄에서 다시 파일을 읽습니다.

```c
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack. This demo
relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
and then back to the server. */

#include     "tx_api.h"
#include     "fx_api.h"
#include     "nx_api.h"
#include     "nx_ftp_client.h"
#include     "nx_ftp_server.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD          server_thread;
TX_THREAD          client_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_PACKET_POOL     client_pool;
NX_IP              client_ip;
FX_MEDIA           ram_disk;

/* Define the NetX FTP object control blocks. */

NX_FTP_CLIENT     ftp_client;
NX_FTP_SERVER     ftp_server;

/* Define the counters used in the demo application... */

ULONG     error_counter = 0;

/* Define the memory area for the FileX RAM disk. */

UCHAR     ram_disk_memory[32000];
UCHAR     ram_disk_sector_cache[512];

#define FTP_SERVER_ADDRESS IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS IP_ADDRESS(1,2,3,5)

extern UINT _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                    VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                    CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                    UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                    UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions. */
VOID     _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

void     client_thread_entry(ULONG thread_input);
void     thread_server_entry(ULONG thread_input);

/* Define server login/logout functions. These are stubs for functions that would
validate a client login request. */

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port, CHAR *name,
                CHAR *password, CHAR *extra_info);

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port, CHAR *name,
                    CHAR *password, CHAR *extra_info);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry,
                    0, pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize NetX. */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server. */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance",
                        FTP_SERVER_ADDRESS, 0xFFFFFF00UL, &server_pool,
                        _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance. */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP. */
    nx_tcp_enable(&server_ip);

    /* Create the FTP server. */
    status = nx_ftp_server_create(&ftp_server, "FTP Server Instance",
                    &server_ip, &ram_disk, pointer, DEMO_STACK_SIZE,
                    &server_pool, server_login, server_logout);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread. */
    status = tx_thread_create(&client_thread, "FTP Client thread ",
                            client_thread_entry, 0,
                            pointer, DEMO_STACK_SIZE,
                            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client. */
    status = nx_packet_pool_create(&client_pool, "NetX Client Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance for the FTP client. */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS,
            0xFFFFFF00UL, &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP. */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance. */
    nx_tcp_enable(&client_ip);

    return;
}

/* Define the FTP client thread. */
void     client_thread_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = _fx_media_format(&ram_disk,
            _fx_ram_driver, /* Driver entry */
            ram_disk_memory, /* RAM disk memory pointer */
            ram_disk_sector_cache, /* Media buffer pointer */
            sizeof(ram_disk_sector_cache), /* Media buffer size */
            "MY_RAM_DISK", /* Volume Name */
            1, /* Number of FATs */
            32, /* Directory Entries */
            0, /* Hidden sectors */
            256, /* Total sectors */
            128, /* Sector size */
            1, /* Sectors per cluster */
            1, /* Heads */
            1); /* Sectors per track */

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
                            ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

     /* Let the IP threads and driver initialize the system. */
    tx_thread_sleep(100);

    /* Create an FTP client. */
    status = nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Created the FTP Client\n");

    /* Now connect with the NetX FTP (IPv4) server. */
    status = nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS,
                                    "name", "password", 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet. */
    status = nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Write ABCs into the packet payload! */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length = 28;
    my_packet -> nx_packet_append_ptr = my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt. */
    status = nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");

    /* Close the file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");

    /* Now open the same file for reading. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file. */
    status = nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
        printf("Reread the FTP client test.txt file\n");
        nx_packet_release(my_packet);
    }

    /* Close this file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server. */
    status = nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    /* Delete the FTP client. */
    status = nx_ftp_client_delete(&ftp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
}

/* Define the helper FTP server thread. */
void     thread_server_entry(ULONG thread_input)
{

UINT     status;

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

    /* OK to start the FTP Server. */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute. */
    tx_thread_relinquish();

    return;
}

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port,
                CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success. */
    return(NX_SUCCESS);
}

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success. */
    return(NX_SUCCESS);
}
```

그림 1.1 NetX(단일 네트워크 인터페이스 호스트)를 사용하는 FTP 클라이언트 및 서버의 예제

## <a name="configuration-options"></a>구성 옵션

NetX용 FTP를 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음 목록에서 각각에 대해 자세히 설명합니다.  

- **NX_FTP_SERVER_PRIORITY**: FTP 서버 스레드의 우선 순위입니다. 기본적으로 이 값은 우선 순위 16을 지정하는 16으로 정의되어 있습니다.

- **NX_FTP_MAX_CLIENTS**: 서버에서 한 번에 처리할 수 있는 최대 클라이언트 수입니다. 기본적으로 이 값은 4로, 한 번에 4개의 클라이언트를 지원합니다.

- **NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: TCP, IP 및 네트워크 프레임 헤더와 HTTP 데이터를 비롯한 서버 패킷 풀 페이로드의 최소 크기(바이트)입니다. 기본값은 256(FileX의 최대 파일 이름 길이) + 12바이트(파일 정보) 및 NX_PHYSICAL_TRAILER입니다.

- **NX_FTP_NO_FILEX**: 정의된 경우 이 옵션은 FileX 종속성에 대한 스텁을 제공합니다. 이 옵션이 정의된 경우 FTP 클라이언트는 변경 없이 작동합니다. FTP 서버는 제대로 작동하기 위해 수정되거나 사용자가 몇 가지 FileX 서비스를 만들어야 합니다.

- **NX_FTP_CONTROL_TOS**: FTP TCP 제어 요청에 필요한 서비스 유형입니다. 기본적으로 이 값은 일반 IP 패킷 서비스를 나타내는 NX_IP_NORMAL로 정의됩니다. 이 정의는 *nx_ftp.h* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.

- **NX_FTP_DATA_TOS**: FTP TCP 데이터 요청에 필요한 서비스 유형입니다. 기본적으로 이 값은 일반 IP 패킷 서비스를 나타내는 NX_IP_NORMAL로 정의됩니다. 이 정의는 *nx_ftp.h* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.

- **NX_FTP_FRAGMENT_OPTION**: FTP TCP 요청에 대해 조각을 사용합니다. 기본적으로 이 값은 FTP TCP 조각화를 사용하지 않도록 설정하는 NX_DONT_FRAGMENT입니다. 이 정의는 *nx_ftp.h* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.

- **NX_FTP_CONTROL_WINDOW_SIZE**: 제어 소켓 창 크기입니다. 기본적으로 이 값은 400바이트입니다. 이 정의는 *nx_ftp.h* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.

- **NX_FTP_DATA_WINDOW_SIZE**: 데이터 소켓 창 크기입니다. 기본적으로 이 값은 2048바이트입니다. 이 정의는 *nx_ftp.h* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.

- **NX_FTP_TIME_TO_LIVE**: 이 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다. 기본값은 0x80으로 설정되지만 *nx_ftp.h* 를 포함하기 전에 다시 정의할 수 있습니다.

- **NX_FTP_SERVER_TIMEOUT**: 내부 서비스가 일시 중단할 ThreadX 틱 수를 지정합니다. 기본값은 100으로 설정되지만 *nx_ftp.h* 를 포함하기 전에 다시 정의할 수 있습니다.

- **NX_FTP_USERNAME_SIZE**: 클라이언트에서 제공한 *사용자 이름* 에 허용되는 바이트 수를 지정합니다. 기본값은 20으로 설정되지만 *nx_ftp.h* 를 포함하기 전에 다시 정의할 수 있습니다.

- **NX_FTP_PASSWORD_SIZE**: 클라이언트에서 제공한 *암호* 에 허용되는 바이트 수를 지정합니다. 기본값은 20으로 설정되지만 *nx_ftp.h* 를 포함하기 전에 다시 정의할 수 있습니다.

- **NX_FTP_ACTIVITY_TIMEOUT**: 작업이 없는 경우 클라이언트 연결을 유지 관리하는 시간(초)을 지정합니다. 기본값은 240으로 설정되지만 *nx_ftp.h* 를 포함하기 전에 다시 정의할 수 있습니다.

- **NX_FTP_TIMEOUT_PERIOD**: 서버에서 클라이언트 비활성을 확인하는 간격(초)을 지정합니다. 기본값은 60으로 설정되지만 *nx_ftp.h* 를 포함하기 전에 다시 정의할 수 있습니다.
