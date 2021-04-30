---
title: 2장 - Azure RTOS NetX BSD 설치 및 사용
description: 이 장에서는 Azure RTOS NetX BSD 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7539565ccd4956c5354be45000efab8318dc606c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811659"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-bsd"></a>2장 - Azure RTOS NetX BSD 설치 및 사용

이 장에서는 Azure RTOS NetX BSD 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS NetX BSD는 [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/)에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다. 패키지에는 다음과 같이 이 문서를 포함하는 두 개의 원본 파일과 PDF 파일이 포함되어 있습니다.

- **nx_bsd.h**: NetX BSD용 헤더 파일
- **nx_bsd.c**: NetX BSD용 C 원본 파일
- **nx_bsd.pdf**: NetX BSD용 사용자 가이드

데모 파일:
- **bsd_demo_tcp.c**
- **bsd_demo_udp.c**

## <a name="netx-bsd-installation"></a>NetX BSD 설치

NetX BSD를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 *nx_bsd.h* 및 *nx_bsd.c* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="building-the-threadx-and-netx-components-of-a-bsd-application"></a>BSD 애플리케이션의 ThreadX 및 NetX 구성 요소 빌드

### <a name="threadx"></a>ThreadX

ThreadX 라이브러리는 스레드 로컬 스토리지에서 *bsd_errno* 를 정의해야 합니다. 다음 절차를 수행하는 것이 좋습니다.

1. *tx_port.h* 에서 TX_THREAD_EXTENSION 매크로 중 하나를 다음과 같이 설정합니다.

  ```c
  #define TX_THREAD_EXTENSION_3     int bsd_errno
  ```

2. ThreadX 라이브러리를 다시 빌드합니다.

> [!NOTE]
> TX_THREAD_EXTENSION_3이 이미 사용되는 경우 사용자는 다른 TX_THREAD_EXTENSION 매크로 중 하나를 자유롭게 사용할 수 있습니다.

### <a name="netx"></a>NetX

NetX BSD 서비스를 사용하기 전에 NX_ENABLE_EXTENDED_NOTIFY_SUPPORT가 정의된 NetX 라이브러리를 빌드해야 합니다(예: *nx_user.h* 에서). 기본적으로 정의되어 있지 않습니다.

## <a name="using-netx-bsd"></a>NetX BSD 사용

NetX용 BSD를 사용하는 것은 쉽습니다. 기본적으로 애플리케이션 코드에는 ThreadX 및 NetX를 각각 사용하기 위해 *tx_api.h* 및 *nx_api.h* 가 포함된 후 *nx_bsd.h* 가 포함되어야 합니다. *nx_bsd.h* 가 포함되고 나면 애플리케이션 코드는 이 가이드의 뒷부분에 지정된 BSD 서비스를 사용할 수 있습니다. 애플리케이션에서도 *nx_bsd.c* 를 빌드 프로세스에 포함해야 합니다. 이 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일해야 하며, 해당 개체 형식은 애플리케이션의 파일과 함께 연결해야 합니다. 이렇게 간단하게 NetX BSD를 사용할 수 있습니다.

NetX BSD 서비스를 활용하려면 애플리케이션에서 *bsd_initialize* 를 호출하여 IP 인스턴스, 패킷 풀을 만들고 BSD 서비스를 초기화해야 합니다. 이는 이 가이드의 뒷부분에 나오는 “작은 예제” 섹션에서 설명합니다. 프로토타입은 다음과 같습니다.

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                  CHAR *free_memory_ptr, ULONG bsd_thread_stack_size,
                  UINT bsd_thread_priority);
```

마지막 세 매개 변수는 TCP 이벤트 확인 및 스레드 스택 공간 정의와 같이 주기적인 작업을 수행하기 위한 스레드를 만드는 데 사용됩니다.

> [!NOTE]
> 네트워크 바이트 순서에서 작동하는 BSD 소켓과 달리, NetX는 호스트 프로세서의 호스트 바이트 순서로 작동합니다. 원본 호환성의 이유로 매크로 htons(), ntohs(), htonl(), ntohl()이 정의되었지만, 전달된 인수를 수정하지는 않습니다.

## <a name="netx-bsd-limitations"></a>NetX BSD 제한 사항

성능 및 아키텍처 문제로 인해 NetX BSD는 모든 BSD 4.3 소켓 기능을 지원하지 않습니다.

INT 플래그는 *send, recv, sendto* 및 *recvfrom* 호출에 지원되지 않습니다.

## <a name="netx-bsd-with-dns-support"></a>DNS를 지원하는 NetX BSD

NX_BSD_ENABLE_DNS가 정의된 경우 NetX BSD에서 DNS 쿼리를 보내 호스트 이름 또는 호스트 IP 정보를 가져올 수 있습니다. 이 기능을 사용하려면 이전에 *nx_dns_create* 서비스를 사용하여 만든 NetX DNS 클라이언트가 필요합니다. 서버 주소를 추가하는 *nx_dns_server_add* 를 사용하여 하나 이상의 알려진 DNS 서버 IP 주소를 DNS 인스턴스에 등록해야 합니다.

DNS 서비스 및 메모리 할당은 *getaddrinfo* 및 *getnameinfo* 서비스에서 사용됩니다.

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
              const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
              char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

BSD 애플리케이션에서 호스트 이름을 사용하여 *getaddrinfo* 를 호출하면 NetX BSD는 아래 서비스 중 하나를 호출하여 IP 주소를 가져옵니다.

- nx_dns_ipv4_address_by_name_get
- nx_dns_cname_get

*nx_dns_ipv4_address_by_name_get* 에서 NetX BSD는 ipv4_addr_buffer 메모리 영역을 사용합니다. 이러한 버퍼의 크기는 (`NX_BSD_IPV4_ADDR_PER_HOST * 4`)로 정의됩니다.

*getaddrinfo* 에서 주소 정보를 반환하기 위해 NetX BSD는 *nx_bsd_addrinfo_pool_memory* ThreadX 블록 메모리 테이블을 사용합니다. 이 테이블의 메모리 영역은 구성 가능한 다른 옵션 세트인 *NX_BSD_IPV4_ADDR_MAX_NUM* 에서 정의됩니다.

위의 구성 옵션에 대한 자세한 내용은 **구성 옵션** 을 참조하세요.

또한 NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의되고 호스트 입력이 정규 이름인 경우 NetX BSD는 이전에 만든 블록 풀 *_nx_bsd_cname_block_pool* 에서 메모리를 동적으로 할당합니다.

> [!NOTE]
> *getaddrinfo* 가 호출되면 BSD 애플리케이션은 *freeaddrinfo* 서비스를 사용하여 res 인수에서 가리키는 메모리를 블록 테이블로 다시 해제해야 합니다.

## <a name="configuration-options"></a>구성 옵션

*nx_bsd.h* 의 사용자 구성 가능한 옵션을 사용하면 애플리케이션에서 특정 요구 사항에 맞게 NetX BSD 소켓을 미세 조정할 수 있습니다. 이러한 매개 변수의 목록은 다음과 같습니다.

- **NX_BSD_TCP_WINDOW**: TCP 소켓 만들기 호출에 사용됩니다. 65535는 100Mb 이더넷의 일반적인 창 크기입니다. 기본값은 65535입니다.
- **NX_BSD_SOCKFD_START** BSD 소켓 파일 설명자 시작 값에 대한 논리적 인덱스입니다. 기본적으로 이 옵션은 32입니다.
- **NX_BSD_MAX_SOCKETS** BSD 계층에서 사용할 수 있는 총 소켓의 최대 수를 지정하며, 32의 배수여야 합니다. 기본값은 32입니다.
- **NX_BSD_SOCKET_QUEUE_MAX** 수신 소켓 큐에 저장되는 최대 UDP 패킷 수를 지정합니다. 기본값은 5입니다.
- **NX_BSD_MAX_LISTEN_BACKLOG** BSD TCP 소켓에 대한 수신 대기 큐(‘백로그’)의 크기를 지정합니다. 기본값은 5입니다.
- **NX_MICROSECOND_PER_CPU_TICK** 타이머 인터럽트당 마이크로초 수를 지정합니다.
- **NX_BSD_TIMEOUT** BSD에 필요한 NetX 내부 호출 시 시간 제한(타이머 틱)을 지정합니다. 기본값은 20 * NX_IP_PERIODIC_RATE입니다.
- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: NetX 연결 끊기 호출 시 시간 제한(타이머 틱)을 지정합니다. 기본값은 1입니다.
- **NX_BSD_PRINT_ERRORS** 설정된 경우 BSD 함수의 오류 상태 반환에서 줄 번호 및 오류 유형(예: 오류가 발생하는 NX_SOC_ERROR)을 반환합니다. 이렇게 하려면 애플리케이션 개발자가 디버그 출력을 정의해야 합니다. 기본 설정이 사용하지 않도록 설정되고 *nx_bsd.h* 에 디버그 출력이 지정되지 않습니다.
- **NX_BSD_TIMER_RATE** BSD 주기적 타이머 작업이 실행되는 간격입니다. 기본값은 1초(1 * NX_IP_PERIODIC_RATE)입니다.
- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER** 설정된 경우 이 옵션을 통해 BSD 시간 제한 프로세스를 시스템 타이머 컨텍스트에서 실행할 수 있습니다. 기본 동작은 사용하지 않도록 설정됩니다. 이 기능은 2장 “NetX BSD 설치 및 사용”에서 자세히 설명합니다.
- **NX_BSD_ENABLE_DNS** 사용하도록 설정된 경우 NetX BSD에서 호스트 이름 또는 호스트 IP 주소에 대한 DNS 쿼리를 보냅니다. 이전에 DNS 클라이언트 인스턴스를 만들고 시작해야 합니다. 기본적으로 사용하지 않도록 설정됩니다.
- **NX_BSD_IPV4_ADDR_MAX_NUM** *getaddrinfo* 에서 반환하는 최대 IPv4 주소 수입니다. 이는 NX_BSD_IPV4_ADDR_MAX_NUM과 함께 메모리를 *getaddrinfo* 의 주소 정보 스토리지에 동적으로 할당하기 위한 nx_bsd_addrinfo_block_pool NetX BSD 블록 풀의 크기를 정의합니다. 기본값은 5입니다.
- **NX_BSD_IPV4_ADDR_PER_HOST**: DNS 쿼리당 저장되는 최대 IPv4 주소 수를 정의합니다. 기본값은 5입니다.

## <a name="bsd-socket-options"></a>BSD 소켓 옵션

다음 NetX BSD 소켓 옵션의 목록은 *setsockopt* 서비스를 사용하여 런타임 시 소켓 단위로 사용하거나 사용하지 않도록 설정할 수 있습니다.

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, const
                void *option_value, INT option_length);
```

*option_level* 에는 두 가지 다른 설정이 있습니다.

런타임 소켓 옵션의 첫 번째 형식은 소켓 수준 옵션에 대한 SOL_SOCKET입니다. 소켓 수준 옵션을 사용하도록 설정하려면 option_level이 SOL_SOCKET으로 설정되고 option_name이 특정 옵션(예: SO_BROADCAST)으로 설정된 *setsockopt* 를 호출합니다. 옵션 설정을 검색하려면 option_level이 SOL_SOCKET으로 다시 설정된 option_name에 대해 *getsockopt* 를 호출합니다.

런타임 소켓 수준 옵션의 목록은 다음과 같습니다.

- **SO_BROADCAST**: 설정된 경우 NetX 소켓에서 브로드캐스트 패킷을 보내고 받을 수 있습니다. 이는 NetX의 기본 동작입니다. 모든 소켓에는 이 기능이 있습니다.
- **SO_ERROR**: *getsockopt* 서비스를 사용하여 지정된 소켓의 이전 소켓 작업에 대한 소켓 상태를 가져오는 데 사용됩니다. 모든 소켓에는 이 기능이 있습니다.
- **SO_KEEPALIVE**: 설정된 경우 TCP Keep Alive(연결 유지) 기능을 사용하도록 설정합니다. 이렇게 하려면 *nx_user.h* 에 NX_TCP_ENABLE_KEEPALIVE가 정의된 NetX 라이브러리를 빌드해야 합니다. 기본적으로 이 기능은 사용하지 않도록 설정됩니다.
- **SO_RCVTIMEO**: NetX BSD 소켓에서 패킷을 받기 위한 대기 옵션(초)을 설정합니다. 기본값은 NX_WAIT_FOREVER (0xFFFFFFFF) 또는 비차단이 사용하도록 설정된 경우 NX_NO_WAIT (0x0)입니다.
- **SO_RCVBUF**: TCP 소켓의 창 크기를 설정합니다. 기본값인 NX_BSD_TCP_WINDOW는 BSD TCP 소켓에 대해 64k로 설정됩니다. 65535보다 큰 크기를 설정하려면 NX_TCP_ENABLE_WINDOW_SCALING이 정의된 NetX 라이브러리를 빌드해야 합니다.
- **SO_REUSEADDR**: 설정된 경우 여러 소켓을 하나의 포트에 매핑할 수 있습니다. 일반적으로 TCP 서버 소켓에 사용됩니다. 이는 NetX 소켓의 기본 동작입니다.

두 번째 형식의 런타임 소켓 옵션은 IP 옵션 수준입니다. IP 수준 옵션을 사용하도록 설정하려면 option_level이 IP_PROTO로 설정되고 option_name이 IP_MULTICAST_TTL과 같은 옵션으로 설정된 *setsockopt* 를 호출합니다. 옵션 설정을 검색하려면 option_level이 IP_PROTO로 다시 설정된 option_name에 대해 *getsockopt* 를 호출합니다.

런타임 IP 수준 옵션의 목록은 다음과 같습니다.

- **IP_MULTICAST_TTL**: UDP 소켓의 TTL(Time to Live)을 설정합니다. 소켓이 만들어질 때 기본값은 NX_IP_TIME_TO_LIVE (0x80)입니다. 이 값은 이 소켓 옵션으로 *setsockopt* 를 호출하여 재정의할 수 있습니다.
- **IP_ADD_MEMBERSHIP**: 설정된 경우 이 옵션을 통해 BSD 소켓(UDP 소켓에만 적용)이 지정된 IGMP 그룹에 조인할 수 있습니다.
- **IP_DROP_MEMBERSHIP**: 설정된 경우 이 옵션을 통해 BSD 소켓(UDP 소켓에만 적용)이 지정된 IGMP 그룹에서 나갈 수 있습니다.

## <a name="small-example-system"></a>작은 예제 시스템

NetX BSD를 사용하는 방법에 대한 예제는 아래 그림 1.0에 나와 있습니다. 이 예제에서 포함 파일 *nx_bsd.h* 는 7줄에서 가져옵니다. 다음으로, *bsd_ip* IP 인스턴스 및 *bsd_pool* 패킷 풀은 20줄 및 21줄에서 전역 변수로 만들어집니다. 이 데모에서는 RAM(가상) 네트워크 드라이버(41줄)를 사용합니다. 이 예제에서 클라이언트와 서버는 단일 IP 인스턴스에서 동일한 IP 주소를 공유합니다.

클라이언트 및 서버 스레드는 애플리케이션을 설정하고 293-361줄에 정의된 *tx_application_define* 의 303 및 309줄에서 생성됩니다. 327줄에서 IP 인스턴스를 성공적으로 만든 후에는 350줄에서 TCP 서비스에 대해 IP 인스턴스를 사용하도록 설정됩니다. BSD 서비스를 사용하기 위한 마지막 요구 사항은 360줄에서 *bsd_initialize* 를 호출하여 BSD에 필요한 모든 데이터 구조와 NetX 및 ThreadX 리소스를 설정하는 것입니다.

381-397줄에 정의된 *thread_1_entry* 서버 스레드 입력 함수에서 애플리케이션은 드라이버가 네트워크 매개 변수를 사용하여 NetX를 초기화할 때까지 기다립니다. 이 작업이 완료되면 146-253줄에 정의된 *tcpServer* 를 호출하여 TCP 서버 소켓 설정의 세부 정보를 처리합니다.

*tcpServer* 는 159줄에서 *socket* 서비스를 호출하여 마스터 소켓을 만들고, 176줄에서 *bind* 호출을 사용하여 수신 대기 소켓에 바인딩합니다. 그런 다음, 191줄에서 연결 요청을 수신 대기하도록 구성됩니다. 마스터 소켓은 연결 요청을 수락하지 않습니다. 연결 요청을 검색할 때마다 *select* 를 호출하는 연속 루프로 실행됩니다. BSD 소켓 배열에서 선택된 보조 BSD 소켓이 218줄에서 *accept* 서비스를 호출한 후 연결 요청이 할당됩니다.

클라이언트 쪽에서 366-377줄에 정의된 클라이언트 스레드 입력 함수인 *thread_0_entry* 는 드라이버에 의해 NetX가 초기화될 때까지 기다려야 합니다. 여기에서 서버 쪽이 수행할 때까지 기다립니다. 그런 다음, 54-142줄에 정의된 *tcpClient* 를 호출하여 TCP 클라이언트 소켓 설정 및 TCP 연결 요청에 대한 세부 정보를 처리합니다.

TCP 클라이언트 소켓이 68줄에 생성됩니다. 소켓이 지정된 IP 주소에 바인딩되고 84줄에서 *connect* 를 호출하여 TCP 서버에 연결을 시도합니다. 이제 패킷을 보내고 받을 준비가 되었습니다.

```c
1 /*  This is a small demo of BSD Wrapper for the high-performance NetX TCP/IP stack.
2     This demo demonstrate TCP connection, disconnection, sending, and receiving using
3     ARP and a simulated Ethernet driver. */
4
5 #include     "tx_api.h"
6 #include     "nx_api.h"
7 #include     "nx_bsd.h"
8 #include     <string.h>
9 #include     <stdlib.h>
10
11 #define         DEMO_STACK_SIZE         (16*1024)
12
13
14 /* Define the ThreadX and NetX object control blocks... */
15
16 TX_THREAD       thread_0;
17 TX_THREAD       thread_1;
18
19
20 NX_PACKET_POOL  bsd_pool;
21 NX_IP           bsd_ip;
22
23
24 /* Define the counters used in the demo application... */
25
26 ULONG           error_counter;
27
28 /* Define fd_set for select call */
29 fd_set          master_list,read_ready,read_ready1;
30
31
32 /* Define thread prototypes. */
33
34 VOID            thread_0_entry(ULONG thread_input);
35 VOID            thread_1_entry(ULONG thread_input);
36
37 VOID            tcpClient(CHAR *msg0);
38 VOID            tcpServer(VOID);
39 INT             HandleClient(INT sock);
40
41 VOID            _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
42
43
44 /* Define main entry point. */
45
46 int main()
47 {
48
49     /* Enter the ThreadX kernel. */
50     tx_kernel_enter();
51 }
52
53
54 VOID tcpClient(CHAR *msg0)
55 {
56
57 INT     status,status1,send_counter;
58 INT     sock_tcp_1,length,length1;
59 struct  sockaddr_in echoServAddr;       /* Echo server address */
60 struct  sockaddr_in localAddr;          /* Local address */
61 struct  sockaddr_in remoteAddr;         /* Remote address */
62
63 UINT    echoServPort; /* Echo Server Port */
64 CHAR    rcvBuffer1[32]
65
66
67     /* Create BSD TCP Socket */
68     sock_tcp_1 = **socket**( PF_INET, SOCK_STREAM, IPPROTO_TCP);
69     if (sock_tcp_1 == -1)
70     {
71         printf("\nError: BSD TCP Client socket create \n");
72         return;
73     }
74
75     printf("\nBSD TCP Client socket created %lu \n", sock_tcp_1);
76     /* Fill destination port and IP address */
77     echoServPort = 12;
78     memset(&echoServAddr, 0, sizeof(echoServAddr));
79     echoServAddr.sin_family = PF_INET;
80     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
81     echoServAddr.sin_port = echoServPort;
82
83     /* Now connect this client the server */
84     status1 = connect(sock_tcp_1, (struct sockaddr *)&echoServAddr, sizeof(echoServAddr));
85     /* Check for error. */
86     if (status1 != OK)
87     {
88         printf("\nError: BSD TCP Client socket Connect, %d \n",sock_tcp_1);
89         status = soc_close(sock_tcp_1);
90         if (status != ERROR)
91             printf("\nConnect ERROR so BSD Client Socket Closed: %d\n",sock_tcp_1);
92         else
93             printf("\nError: BSD Client Socket close %d\n",sock_tcp_1);
94         return;
95     }
96     /* Get and print source and destination information */
97     printf("\nBSD TCP Client socket: %d connected \n", sock_tcp_1);
98
99     status = getsockname(sock_tcp_1, (struct sockaddr *)&localAddr, &length);
100    printf("Client port = %lu , Client = %lu,", 
            localAddr.sin_port, localAddr.sin_addr.s_addr);
101    status = getpeername( sock_tcp_1, (struct sockaddr *) &remoteAddr, &length1);
102    printf("Remote port = %lu, Remote IP = %lu \n", 
            remoteAddr.sin_port remoteAddr.sin_addr.s_addr);
103
104    send_counter = 1;
105
106    /* Now receive the echoed packet from the server */
107    while(1)
108    {
109        tx_thread_sleep(2);
110
111        printf("\nClient sock: %d Sending packet No: %d to
                server\n",sock_tcp_1,send_counter);
112        status = send(sock_tcp_1,msg0, sizeof(msg0), 0);
113        if (status == ERROR)
114            printf("Error: BSD Client Socket send %d\n",sock_tcp_1);
115        else
116        {
117            printf("\nMessage sent: %s\n",msg0);
118            send_counter++;
119        }
120
121        status = recv(sock_tcp_1, (VOID *)rcvBuffer1, 31,0);
122        if (status == 0)
123            break;
124
125        rcvBuffer1[status] = 0;
126
127        if (status != ERROR)
128            printf("\nBSD Client Socket: %d received %lu bytes: %s ", 
                        sock_tcp_1,(ULONG)status,rcvBuffer1);
129        else
130            printf("\nError: BSD Client Socket receive %d \n",sock_tcp_1);
131
132    }
133
134    /* close this client socket */
135    status = soc_close(sock_tcp_1);
136    if (status != ERROR)
137        printf("\nBSD Client Socket Closed %d\n",sock_tcp_1);
138    else
139        printf("\nError: BSD Client Socket close %d \n",sock_tcp_1);
140
141    /* End */
142 }
143
144
145
146 void tcpServer(void)
147 {
148
149 INT         status,status1,sock,sock_tcp_2,i;
150 struct      sockaddr_in echoServAddr; /* Echo server address */
151 struct      sockaddr_in ClientAddr;
152
153 INT         Clientlen;
154 UINT        echoServPort; /* Echo Server Port */
155
156 INT         maxfd;
157
158 /* Create BSD TCP Server Socket */
159     sock_tcp_2 = socket( PF_INET, SOCK_STREAM, IPPROTO_TCP);
160     if (sock_tcp_2 == -1)
161     {
162         printf("Error: BSD TCP Server socket create\n");
163         return;
164     }
165     else
166         printf("BSD TCP Server socket created \n");
167
168     /* Now fill server side information */
169     echoServPort = 12;
170     memset(&echoServAddr, 0, sizeof(echoServAddr));
171     echoServAddr.sin_family = PF_INET;
172     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
173     echoServAddr.sin_port = echoServPort;
174
175     /* Bind this server socket */
176         status = bind(sock_tcp_2, (struct sockaddr *) &echoServAddr, sizeof(echoServAddr));
177     if (status < 0)
178     {
179         printf("Error: BSD TCP Server Socket Bind \n");
180         return;
181     }
182     else
183         printf("BSD TCP Server Socket bound \n");
184
185     FD_ZERO(&master_list);
186     FD_ZERO(&read_ready);
187     FD_SET(sock_tcp_2,&master_list);
188     maxfd = sock_tcp_2;
189
190     /* Now listen for any client connections for this server socket */
191     status = listen(sock_tcp_2,5);
192     if (status < 0)
193     {
194         printf("Error: BSD TCP Server Socket Listen\n");
195         return;
196     }
197     else
198         printf("BSD TCP Server Socket Listen complete, ");
199
200     /* All set to accept client connections */
201     printf("Now accepting client connections\n");
202
203     /* Loop to create and establish server connections. */
204     while(1)
205     {
206
207         read_ready = master_list;
208         tx_thread_sleep(2); /* Allow some time to other threads too */
209         status = select(maxfd+1,&read_ready,0,0,0);
210         if (status == ERROR)
211         {
212             continue;
213         }
214
215         status = FD_ISSET(sock_tcp_2,&read_ready);
216         if(status)
217         {
218             sock = accept(sock_tcp_2,(struct sockaddr*)&ClientAddr, &Clientlen);
219
220             /* Add this new connection to our master list */
221             FD_SET(sock,&master_list);
222             if ( sock \maxfd)
223             {
224                 maxfd = sock;
225             }
226
227             continue;
228         }
229         for (i = 0; i < (maxfd+1); i++)
230         {
231             if (( i != sock_tcp_2) && (FD_ISSET(i,&master_list)) && 
                    (FD_ISSET(i,&read_ready)))
232             {
233                 status1 = HandleClient(i);
234                 if (status1 == 0)
235                 {
236                     status1 = soc_close(i);
237                     if (status1 == OK)
238                     {
239                         FD_CLR(i,&master_list);
240                         printf("\nBSD Server Socket:%d closed\n",i);
241                     }
242                     else
243                         printf("\nError:BSD Server Socket:%d close\n",i);
244                 }
245
246             }
247         }
248
249         /* Loop back to check any next client connection */
250
251     } /* While(1) ends */
252
253 }
254
255 CHAR     rcvBuffer[128];
256
257 INT     HandleClient(INT sock)
258 {
259
260 INT     status;
261
262
263     status = recv(sock, (VOID *)rcvBuffer, 128,0);
264     if (status == ERROR )
265     {
266         printf("\n BSD Server Socket:%d receive \n",sock);
267         return(ERROR);
268     }
269
270     /* a zero return from a recv() call indicates client is terminated! */
271     if (status == 0)
272     {
273         /* Done with this client , close this secondary server socket */
274         return(status);
275     }
276
277     /* print data received from the client */
278     printf("\nBSD Server Socket:%d received %lu bytes: %s \n", sock, (ULONG)status,rcvBuffer);
279
280     /* And echo the same data to the client */
281     status = send(sock,rcvBuffer, status + 1, 0);
282     if (status == ERROR )
283     {
284         printf("\nError: BSD Server Socket:%d send \n",sock);
285         return(ERROR);
286     }
287     return(status);
288 }
289
290
291 /* Define what the initial system looks like. */
292
293 void     tx_application_define(void *first_unused_memory)
294 {
295
296 CHAR     *pointer;
297 UINT     status;
298
299     /* Setup the working pointer. */
300     pointer = (CHAR *) first_unused_memory;
301
302     /* Create a client thread. */
303     tx_thread_create(&thread_0, "Client1", thread_0_entry, 0,
304         pointer, DEMO_STACK_SIZE, 2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
305
306     pointer = pointer + DEMO_STACK_SIZE;
307
308     /* Create a server thread. */
309     tx_thread_create(&thread_1, "Server", thread_1_entry, 0,
310         pointer, DEMO_STACK_SIZE,1,1, TX_NO_TIME_SLICE, TX_AUTO_START);
311
312     pointer = pointer + DEMO_STACK_SIZE;
313
314     /* Initialize the NetX system. */
315     nx_system_initialize();
316
317     /* Create a BSD packet pool. */
318     status = nx_packet_pool_create(&bsd_pool,"NetX BSD Packet Pool", 128
                                        pointer, 16384);
319     pointer = pointer + 16384;
320     if (status)
321     {
322         error_counter++;
323         printf("Error in creating BSD packet pool\n!");
324     }
325
326     /* Create an IP instance for BSD. */
327     status = nx_ip_create(&bsd_ip, "NetX IP Instance 2", IP_ADDRESS(1, 2, 3, 4),
                              0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                              pointer, 2048, 1);
328
329     pointer = pointer + 2048;
330
331     if (status)
332     {
333         error_counter++;
334         printf("Error creating BSD IP instance\n!");
335     }
336
337     /* Enable ARP and supply ARP cache memory for BSD IP Instance */
338     status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
339     pointer = pointer + 1024;
340
341     /* Check ARP enable status. */
342     if (status)
343     {
344         error_counter++;
345         printf("Error in Enable ARP and supply ARP cache memory to BSD IP instance\n");
346     }
347
348     /* Enable TCP processing for BSD IP instances. */
349
350     status = nx_tcp_enable(&bsd_ip);
351
352     /* Check TCP enable status. */
353     if (status)
354     {
355         error_counter++;
356         printf("Error in Enable TCP \n");
357     }
358
359     /* Now initialize BSD Scoket Wrapper */
360     status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 1);
361 }
362
363
364 /* Define the test threads. */
365
366 void     thread_0_entry)ULONG thread_input)
367 {
368
369 CHAR     *msg0 = "Client 1:
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<> \
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";
370
371     /* Wait till Server side is all set */
372     tx_thread_sleep(2);
373     while (1)
374     {
375         tcpClient(msg0);
376         tx_thread_sleep(1);
377     }
378 }
379
380 /* Define the server thread entry function. */
381 void     thread_1_entry(ULONG thread_input)
382 {
383
384 UINT     status;
385 ULONG    actual_status;
386
387 /* Ensure the IP instance has been initialized. */
388 status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE, &actual_status, 100);
389
390 /* Check status... */
391 if (status != NX_SUCCESS)
392 {
393     error_counter++;
394     return;
395 }
396 /* Start a TCP Server */
397 tcpServer();
398 }
399
```
