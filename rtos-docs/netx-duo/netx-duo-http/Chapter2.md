---
title: 2장 - Azure RTOS NetX Duo HTTP 설치 및 사용
description: 이 장에서는 Azure RTOS NetX Duo HTTP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 이슈에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9a3ea37b180ab57a8dcd269092638fa74589836a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810782"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-http"></a>2장 - Azure RTOS NetX Duo HTTP 설치 및 사용

이 장에서는 Azure RTOS NetX Duo HTTP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 이슈에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS NetX Duo는 [https://github.com/azure-rtos/netxduo/](https://github.com/azure-rtos/netxduo/)에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다.

 - **nxd_http_client.h** NetX Duo용 HTTP 클라이언트의 헤더 파일
 - **nxd_http_server.h** NetX Duo용 HTTP 서버의 헤더 파일
 - **nxd_http_client.c** NetX Duo용 HTTP 클라이언트의 C 원본 파일
 - **nxd_http_server.c** NetX Duo용 HTTP 서버의 C 원본 파일
 - **nx_md5.c** MD5 다이제스트 알고리즘
 - **filex_stub.h** FileX가 없는 경우 스텁 파일
 - **nx_http.pdf** NetX Duo용 HTTP의 설명
 - **demo_netxduo_http.c** NetX Duo HTTP 데모

## <a name="http-installation"></a>HTTP 설치

NetX Duo용 HTTP를 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX Duo가 *“\threadx\arm7\green”* 디렉터리에 설치된 경우 *nxd_http_client.h* 및 *nxd_http_client.c*(NetX Duo HTTP 클라이언트 애플리케이션용)와, *nxd_http_server.h* 및 *nxd_http_server.c*(NetX Duo HTTP 서버 애플리케이션용)입니다. *nx_md5.c* 를 이 디렉터리에 복사해야 합니다. 데모 ‘ram 드라이버’ 애플리케이션 NetX Duo HTTP 클라이언트와 서버 파일을 동일한 디렉터리에 복사해야 합니다.

## <a name="using-http"></a>HTTP 사용

HTTP는 NetX Duo에 쉽게 사용할 수 있습니다. 기본적으로 ThreadX, FileX 및 NetX를 사용하기 위해서는 애플리케이션 코드에 각각 *tx_api.h*, *fx_api.h* 및 *nx_api.h* 를 포함한 후 *nxd_http_client.h* 및/또는 *nxd_http_server.h* 를 포함해야 합니다. HTTP 헤더 파일이 포함되면 애플리케이션 코드는 이 가이드의 뒷부분에 지정된 HTTP 함수 호출을 만들 수 있습니다. 애플리케이션은 빌드 프로세스에 *nxd_http_client.c*, *nxd_http_server.c* 및 *md5.c* 도 포함해야 합니다. 이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 해당 개체 형식을 애플리케이션의 파일에 연결해야 합니다. 이렇게 간단하게 NetX Duo HTTP를 사용할 수 있습니다.

> [!NOTE]
> 빌드 프로세스에서 NX_HTTP_DIGEST_ENABLE이 지정되지 않은 경우에는 md5.c 파일을 애플리케이션에 추가할 필요가 없습니다. 마찬가지로, HTTP 클라이언트 기능이 필요하지 않은 경우에는 *nxd_http_client.c* 파일을 생략할 수 있습니다.

> [!NOTE]
> HTTP는 NetX Duo TCP 서비스를 활용하므로 HTTP를 사용하기 전에 *nx_tcp_enable* 호출을 통해 TCP를 사용하도록 설정해야 합니다.

## <a name="small-example-system"></a>간단한 예제 시스템

NetX Duo HTTP를 사용하는 것이 얼마나 쉬운지 보여 주는 예제가 아래에 표시된 그림 1.1에 설명되어 있습니다. 이 예제는 23행에서 #define USE_DUO의 NetX Duo HTTP 위치에서 사용할 수 있는 ‘duo’ 서비스에서 작동합니다. 그렇지 않으면 레거시 NetX HTTP 동급(IPv4만으로 제한)을 사용합니다. 개발자는 NetX Duo HTTP 서비스를 사용하도록 기존 애플리케이션을 마이그레이션하는 것이 좋습니다.

IPv6 통신을 지정하기 위해 애플리케이션은 24행에 IPTYPE을 IPv6으로 정의합니다.

이 예제에서는 HTTP 포함 파일 *nxd_http_client.h* 및 *nxd_http_server.h* 를 8행과 9행에 불러옵니다. 그런 다음, 89-112행에서 도우미 HTTP 서버 스레드, 패킷 풀 및 IP 인스턴스를 만듭니다. HTTP 서버 IP는 137행에서처럼 TCP를 사용하도록 설정해야 합니다. 그러면 HTTP 서버가 159행에 그대로 만들어집니다.

다음으로 HTTP 클라이언트를 만듭니다. 먼저 172행에서 클라이언트 스레드를 만들고 이후 패킷 풀과 IP 인스턴스를 만듭니다. 186-200행의 HTTP 서버와 유사합니다. 다시 HTTP 클라이언트 IP 인스턴스는 TCP를 사용하도록 설정해야 합니다(217행).

HTTP 서버 스레드가 실행되고, 첫 번째 작업은 423-450행에서 수행하는 NetX Duo에서의 IP 주소 유효성 검사입니다. 이제 HTTP 서버가 요청을 받을 준비가 되었습니다.

HTTP 클라이언트 스레드의 첫 번째 작업은 FileX 미디어(236 및 260행)를 만들고 포맷하는 것입니다. 미디어 초기화 후 271행에서 HTTP 클라이언트를 만듭니다. HTTP 서버에서 HTTP 요청을 처리할 수 있으려면 먼저 이 작업이 필요합니다. 그런 다음, 282 – 316행에서 NetX Duo에서의 IP 주소 유효성 검사를 수행합니다. 다음으로 HTTP 클라이언트가 client_test.html 파일을 만들어 HTTP 서버에 보내고 잠깐 대기했다가 HTTP 서버에서 파일을 다시 읽으려 시도합니다.

> [!NOTE]
> IPv6을 사용하지 않도록 설정한 경우 HTTP 클라이언트 API는 다른 서비스를 사용합니다(343행의 *nx_http_client_put_start*, 399행의 *nx_http_client_get_start*). 이렇게 하면 NetX Duo에서 기존 NetX HTTP 클라이언트 애플리케이션을 지원할 수 있습니다.

> [!NOTE]
> HTTP 클라이언트 API 호출은 상대적으로 짧은 시간 제한으로 수행됩니다. HTTP 클라이언트가 더 느린 프로세스에서 사용 중인 서버 또는 원격 서버와 통신하는 경우 이런 시간 제한을 연장해야 할 수 있습니다.

```c
1    /* This is a small demo of the NetX Duo HTTP Client Server API running on a
2       high-performance NetX Duo TCP/IP stack. This demo is applicable for
3       either IPv4 or IPv6 enabled applications. */
4    
5    #include   "tx_api.h"
6    #include   "fx_api.h"
7    #include   "nx_api.h"
8    #include   "nxd_http_client.h"
9    #include   "nxd_http_server.h"
10   
11   #define     DEMO_STACK_SIZE         2048  
12   
13   /* Set up FileX and file memory resources. */
14   CHAR            *ram_disk_memory;
15   FX_MEDIA        ram_disk;
16   unsigned char   media_memory[512];
17      
18   /* Define device drivers. */
19   extern void _fx_ram_driver(FX_MEDIA *media_ptr);
20   VOID        _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
22   
23   #define USE_DUO        /* Use the duo service (not legacy netx) */
24   #define IPTYPE   6       /* Send packets over IPv6 */
25
26   /* Set up the HTTP client. */
27   TX_THREAD       client_thread;
28   NX_PACKET_POOL  client_pool;
29   NX_HTTP_CLIENT  my_client;
30   NX_IP           client_ip;
31   #define         CLIENT_PACKET_SIZE  (NX_HTTP_SERVER_MIN_PACKET_SIZE * 2)
32   void            thread_client_entry(ULONG thread_input);
33   
34   #define HTTP_SERVER_ADDRESS  IP_ADDRESS(1,2,3,4)
35   #define HTTP_CLIENT_ADDRESS  IP_ADDRESS(1,2,3,5)
36   
37   /* Set up the HTTP server */
38   
39   NX_HTTP_SERVER  my_server;
40   NX_PACKET_POOL  server_pool;
41   TX_THREAD       server_thread;
42   NX_IP           server_ip;
43   #define         SERVER_PACKET_SIZE  (NX_HTTP_SERVER_MIN_PACKET_SIZE * 2)
44   
45   void            thread_server_entry(ULONG thread_input);
46   #ifdef FEATURE_NX_IPV6
47   NXD_ADDRESS     server_ip_address;
48   #endif
49   
50   
51   /* Define the application's authentication check. This is called by
52      the HTTP server whenever a new request is received. */
53   UINT  authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
54               CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
55   {
56   
57       /* Just use a simple name, password, and realm for all
58          requests and resources. */
59       *name =     "name";
60       *password = "password";
61       *realm =    "NetX Duo HTTP demo";
62   
63       /* Request basic authentication. */
64       return(NX_HTTP_BASIC_AUTHENTICATE);
65   }
66   
67   /* Define main entry point. */
68   
69   int main()
70   {
71   
72       /* Enter the ThreadX kernel. */
73       tx_kernel_enter();
74   }
75   
76   
77   /* Define what the initial system looks like. */
78   void    tx_application_define(void *first_unused_memory)
79   {
80   
81   CHAR    *pointer;
82   UINT    status;
83   
84       
85       /* Setup the working pointer. */
86       pointer =  (CHAR *) first_unused_memory;
87   
88       /* Create a helper thread for the server. */
89       tx_thread_create(&server_thread, "HTTP Server thread", thread_server_entry, 0,  
90                        pointer, DEMO_STACK_SIZE,
91                        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
92   
93       pointer =  pointer + DEMO_STACK_SIZE;
94   
95       /* Initialize the NetX system. */
96       nx_system_initialize();
97   
98       /* Create the server packet pool. */
99       status =  nx_packet_pool_create(&server_pool, "HTTP Server Packet Pool",
        SERVER_PACKET_SIZE, pointer, SERVER_PACKET_SIZE*4);
100
101  
102      pointer = pointer + SERVER_PACKET_SIZE * 4;
103  
104      /* Check for pool creation error. */
105      if (status)
106      {
107  
108          return;
109      }
110  
111      /* Create an IP instance. */
112      status = nx_ip_create(&server_ip, "HTTP Server IP", HTTP_SERVER_ADDRESS,
113                            0xFFFFFF00UL, &server_pool, _nx_ram_network_driver,
114                            pointer, 4096, 1);
115  
116      pointer =  pointer + 4096;
117  
118      /* Check for IP create errors. */
119      if (status)
120      {
121          printf("nx_ip_create failed. Status 0x%x\n", status);
122          return;
123      }
124  
125      /* Enable ARP and supply ARP cache memory for the server IP instance. */
126      status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
127  
128      /* Check for ARP enable errors. */
129      if (status)
130      {
131          return;
132      }
133  
134      pointer = pointer + 1024;
135  
136       /* Enable TCP traffic. */
137      status = nx_tcp_enable(&server_ip);
138  
139      if (status)
140      {
141          return;
142      }
143  
144  #if (IP_TYPE==6)
145  
146      /* Set up HTTPv6 server, but we have to wait till its address has been
147         validated before we can start the thread_server_entry thread. */
148  
149      /* Set up the server's IPv6 address here. */
150      server_ip_address.nxd_ip_address.v6[3] = 0x105;
151      server_ip_address.nxd_ip_address.v6[2] = 0x0;
152      server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
153      server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
154      server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
155  
156  #endif
157  
158      /* Create the NetX HTTP Server. */
159      status = nx_http_server_create(&my_server, "My HTTP Server", &server_ip,
            &ram_disk, pointer, 2048, &server_pool, authentication_check,
            NX_NULL);
160
161      if (status)
162      {
163          return;
164      }
165  
166      pointer =  pointer + 2048;
167  
168      /* Save the memory pointer for the RAM disk. */
169      ram_disk_memory =  pointer;
170  
171      /* Create the HTTP client thread. */
172      status = tx_thread_create(&client_thread, "HTTP Client", thread_client_entry, 0,  
173                       pointer, DEMO_STACK_SIZE,
174                       2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
175  
176      pointer =  pointer + DEMO_STACK_SIZE;
177  
178      /* Check for thread create error. */
179      if (status)
180      {
181  
182          return;
183      }
184  
185      /* Create the Client packet pool. */
186      status =  nx_packet_pool_create(&client_pool, "HTTP Client Packet Pool",
 SERVER_PACKET_SIZE, pointer, SERVER_PACKET_SIZE*4);

187
188  
189      pointer = pointer + SERVER_PACKET_SIZE * 4;
190  
191      /* Check for pool creation error. */
192      if (status)
193      {
194  
195          return;
196      }
197  
198  
199      /* Create an IP instance. */
200      status = nx_ip_create(&client_ip, "HTTP Client IP", HTTP_CLIENT_ADDRESS,
201                            0xFFFFFF00UL, &client_pool, _nx_ram_network_driver,
202                            pointer, 2048, 1);
203  
204      pointer =  pointer + 2048;
205  
206      /* Check for IP create errors. */
207      if (status)
208      {
209          return;
210      }
211  
212      nx_arp_enable(&client_ip, (void *) pointer, 1024);
213  
214      pointer =  pointer + 2048;
215  
216       /* Enable TCP traffic. */
217      nx_tcp_enable(&client_ip);
218  
219      return;
220  }
221  
222  
223  VOID thread_client_entry(ULONG thread_input)
224  {
225  
226  UINT            status;
227  NX_PACKET       *my_packet;
228  #ifdef FEATURE_NX_IPV6
229  NXD_ADDRESS     client_ip_address;
230  UINT            address_index;
230  #endif
231  
232  
233      /* Format the RAM disk - the memory for the RAM disk was setup in
234        tx_application_define above. This must be set up before the client(s) start
235        sending requests. */
236      status = fx_media_format(&ram_disk,
237                              _fx_ram_driver,         // Driver entry
238                              ram_disk_memory,        // RAM disk memory pointer
239                              media_memory,           // Media buffer pointer
240                              sizeof(media_memory),   // Media buffer size
241                              "MY_RAM_DISK",          // Volume Name
242                              1,                      // Number of FATs
243                              32,                     // Directory Entries
244                              0,                      // Hidden sectors
245                              256,                    // Total sectors
246                              128,                    // Sector size   
247                              1,                      // Sectors per cluster
248                              1,                      // Heads
249                              1);                     // Sectors per track
250  
251      /* Check the media format status. */
252      if (status != FX_SUCCESS)
253      {
254  
255          /* Error, bail out. */
256          return ;
257      }
258  
259      /* Open the RAM disk. */
260      status =  fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
                media_memory, sizeof(media_memory));
261  
262      /* Check the media open status. */
263      if (status != FX_SUCCESS)
264      {
265  
266          /* Error, bail out. */
267          return ;
268      }
269  
270      /* Create an HTTP client instance. */
271      status = nx_http_client_create(&my_client, "HTTP Client", &client_ip,
                    &client_pool, 600);
272  
273      /* Check status. */
274      if (status != NX_SUCCESS)
275      {
276          return;
277      }
278  
279      /* Attempt to upload a file to the HTTP server. */
280  
281  
282  #if (IPTYPE== 6)
283  
284      /* Relinquish control so the HTTP server can get set up...*/
285      tx_thread_relinquish();
286  
287      /* Set up the client's IPv6 address here. */
288      client_ip_address.nxd_ip_address.v6[3] = 0x101;
289      client_ip_address.nxd_ip_address.v6[2] = 0x0;
290      client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
291      client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
292      client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
293                 
294      /* Here's where we make the HTTP Client IPv6 enabled. */
295  
296      nxd_ipv6_enable(&client_ip);
298      nxd_icmp_enable(&client_ip);     
299      
300      /* Wait till the IP task thread has set the device MAC address. */
302      tx_thread_sleep(100);
303  
305      /* Now update NetX Duo the Client's link local and global IPv6 address. */
306      nxd_ipv6_address_set(&server_ip, 0, NX_NULL, 10, &address_index)
307      nxd_ipv6_ address_set(&server_ip, 0, &client_ip_address, 64, &address_index);
311
313      /* Then make sure NetX Duo has had time to validate the addresses. */
314      
316      tx_thread_sleep(400);
317  
321      /* Now upload an HTML file to the HTTPv6 server. */
322      status =  nxd_http_client_put_start(&my_client, &server_ip_address,
323         "/client_test.htm", "name", "password", 103, 500);
324
325
326      /* Check status. */
327      if (status != NX_SUCCESS)
328      {
329
330          return;
331      }
332      
333
334  #else
335  
336      /* Relinquish control so the HTTP server can get set up...*/
337      tx_thread_relinquish();
338  
339      do
340      {
341      
342          /* Attempt to upload to the HTTP IPv4 server. */
343          status =  nx_http_client_put_start(&my_client, HTTP_SERVER_ADDRESS,
            "/client_test.htm", "name", "password", 103, 500);
344
345  
346          /* Check status. */
347          if (status != NX_SUCCESS)
348          {
349              tx_thread_sleep(100);
350          }
351  
352      } while (status != NX_SUCCESS);
353  
354  
355  #endif  /* (IPTYPE== 6) */
356  
357  
358      /* Allocate a packet. */
359      status =  nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET,
                        NX_WAIT_FOREVER);
360  
361      /* Check status. */
362      if (status != NX_SUCCESS)
363      {
364          return;
365      }
366  
367      /* Build a simple 103-byte HTML page. */
368      nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
369                          &client_pool, NX_WAIT_FOREVER);
370      nx_packet_data_append(my_packet,
371                   "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
372                          &client_pool, NX_WAIT_FOREVER);
373      nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
374                          &client_pool, NX_WAIT_FOREVER);
375      nx_packet_data_append(my_packet, "<H1>Another NetX Test Page!</H1>\r\n", 25,
376                          &client_pool, NX_WAIT_FOREVER);
377      nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
378                          &client_pool, NX_WAIT_FOREVER);
379      nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
380                          &client_pool, NX_WAIT_FOREVER);
381  
382      /* Complete the PUT by writing the total length. */
383      status =  nx_http_client_put_packet(&my_client, my_packet, 50);
384  
385      /* Check status. */
386      if (status != NX_SUCCESS)
387      {
388          return;
389      }
390  
391      /* Now GET the test file  */
392  
393  #ifdef USE_DUO
394  
395      status =  nxd_http_client_get_start(&my_client, &server_ip_address,
396                     "/client_test.htm", NX_NULL, 0, "name", "password", 50);
397  #else
398  
399      status =  nx_http_client_get_start(&my_client, HTTP_SERVER_ADDRESS,
                 "/client_test.htm",  NX_NULL, 0, "name", "password", 50);
400
401  #endif
402  
403      /* Check status. */
404      if (status != NX_SUCCESS)
405      {
406          return;
407      }
408  
409      status = nx_http_client_delete(&my_client);
410  
411      return;
413  }
414  
416  /* Define the helper HTTP server thread. */
417  void    thread_server_entry(ULONG thread_input)
418  {
419  
420  UINT            status;
421  #if (IPTYPE == 6)
422  UINT            address_index
423  NXD_ADDRESS     ip_address
424  
425      /* Allow time for the IP task to initialize the driver. */
426      tx_thread_sleep(100);
427
428    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
429    ip_address.nxd_ip_address.v6[0] = 0x20010000;
430    ip_address.nxd_ip_address.v6[1] = 0;
431    ip_address.nxd_ip_address.v6[2] = 0;
432    ip_address.nxd_ip_address.v6[3] = 4;
433  
434      /* Here's where we make the HTTP server IPv6 enabled. */
435      nxd_ipv6_enable(&server_ip);
436      nxd_icmp_enable(&server_ip);
437  
438      /* Wait till the IP task thread has set the device MAC address. */
439      while (server_ip.nx_ip_arp_physical_address_msw == 0 ||
440             server_ip.nx_ip_arp_physical_address_lsw == 0)
441      {
442          tx_thread_sleep(30);
443      }
444  
445      nxd_ipv6_address_set(&server_ip, 0, NX_NULL, 10, &address_index)
446      nxd_ipv6_ address_set(&server_ip, 0, &ip_address, 64, &address_index);
447  
448      /* Wait for NetX Duo to validate server address. */
449      tx_thread_sleep(400);
450  
451  #endif  /* (IPTYPE == 6) */
452  
453      /* OK to start the HTTPv6 Server. */
454      status = nx_http_server_start(&my_server);
455  
456      if (status != NX_SUCCESS)
457      {
458          return;
459      }
460  
461      /* HTTP server ready to take requests! */
462  
463      /* Let the IP threads execute. */
464      tx_thread_relinquish();
465  
466      return;
467  }
```

**그림 1.1 NetX Duo에서의 HTTP 사용 예제**

## <a name="configuration-options"></a>구성 옵션

NetX Duo용 HTTP를 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음은 각 옵션에 대한 자세한 설명입니다. 기본값은 나열되지만 *nxd_http_client.h* 및 *nxd_http_server.h* 를 포함하기 전에 다시 정의할 수 있습니다.

 - **NX_DISABLE_ERROR_CHECKING** 정의된 경우 이 옵션은 기본 HTTP 오류 검사를 제거합니다. 일반적으로 애플리케이션이 디버깅된 후에 사용됩니다.
 - **NX_HTTP_SERVER_PRIORITY** HTTP 서버 스레드의 우선 순위입니다. 기본적으로 이 값은 우선 순위 16을 지정하는 16으로 정의되어 있습니다.
 - **NX_HTTP_NO_FILEX** 정의된 경우 이 옵션은 FileX 종속성에 대한 스텁을 제공합니다. 이 옵션이 정의된 경우 HTTP 클라이언트는 변경 없이 작동합니다. HTTP 서버는 제대로 작동하기 위해 수정되거나 사용자가 몇 가지 FileX 서비스를 만들어야 합니다.
 - **NX_HTTP_TYPE_OF_SERVICE** HTTP TCP 요청에 필요한 서비스 유형입니다. 기본적으로 이 값은 일반 IP 패킷 서비스를 나타내는 NX_IP_NORMAL로 정의됩니다.
  - **NX_HTTP_SERVER_THREAD_TIME_SLICE** 동일한 우선 순위의 스레드에 발생하기 전에 서버 스레드를 실행할 수 있는 타이머 틱 수입니다. 기본값은 2입니다.
 - **NX_HTTP_FRAGMENT_OPTION** HTTP TCP 요청에 대해 조각을 사용합니다. 기본적으로 이 값은 HTTP TCP 조각화를 사용하지 않도록 설정하는 NX_DONT_FRAGMENT입니다.
 - **NX_HTTP_SERVER_WINDOW_SIZE** 서버 소켓 창 크기입니다. 기본적으로 이 값은 2048바이트입니다.
 - **NX_HTTP_TIME_TO_LIVE** 이 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다. 기본값은 0x80으로 설정됩니다.
 - **NX_HTTP_SERVER_TIMEOUT** 내부 서비스가 일시 중단할 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 * NX_IP_PERIODIC_RATE)로 설정됩니다.
 - **NX_HTTP_SERVER_TIMEOUT_ACCEPT** 내부 *nx_tcp_server_socket_accept* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 10 * NX_IP_PERIODIC_RATE로 설정됩니다.
 - **NX_HTTP_SERVER_TIMEOUT_DISCONNECT** 내부 *nx_tcp_socket_disconnect* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 * NX_IP_PERIODIC_RATE)로 설정됩니다.
 - **NX_HTTP_SERVER_TIMEOUT_RECEIVE** 내부 *nx_tcp_socket_receive* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 * NX_IP_PERIODIC_RATE)로 설정됩니다.
 - **NX_HTTP_SERVER_TIMEOUT_SEND** 내부 *nx_tcp_socket_send* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 * NX_IP_PERIODIC_RATE)로 설정됩니다.
 - **NX_HTTP_MAX_HEADER_FIELD** HTTP 헤더 필드의 최대 크기를 지정합니다. 기본값은 256입니다.
 - **NX_HTTP_MULTIPART_ENABLE** 정의된 경우 HTTP 서버가 다중 파트 HTTP 요청을 지원할 수 있습니다.
 - **NX_HTTP_SERVER_MAX_PENDING** HTTP 서버에 대해 큐에 대기할 수 있는 연결 수를 지정합니다. 기본값은 5로 설정됩니다.
 - **NX_HTTP_MAX_RESOURCE** 클라이언트에서 제공하는 *리소스 이름* 에 허용되는 바이트 수를 지정합니다. 기본값은 40으로 설정됩니다.
 - **NX_HTTP_MAX_NAME** 클라이언트에서 제공하는 *사용자 이름* 에 허용되는 바이트 수를 지정합니다. 기본값은 20으로 설정됩니다.
 - **NX_HTTP_MAX_PASSWORD** 클라이언트에서 제공하는 *암호* 에 허용되는 바이트 수를 지정합니다. 기본값은 20으로 설정됩니다.
 - **NX_HTTP_SERVER_MIN_PACKET_SIZE** 서버를 만들 때 지정된 풀에 있는 패킷의 최소 크기를 지정합니다. 전체 HTTP 헤더를 하나의 패킷에 포함될 수 있도록 하려면 최소 크기가 필요합니다. 기본값은 600으로 설정됩니다.
 - **NX_HTTP_CLIENT_MIN_PACKET_SIZE** 클라이언트를 만들 때 지정된 풀에 있는 패킷의 최소 크기를 지정합니다. 전체 HTTP 헤더를 하나의 패킷에 포함될 수 있도록 하려면 최소 크기가 필요합니다. 기본값은 300으로 설정됩니다.
 - **NX_HTTP_SERVER_RETRY_SECONDS** 서버 소켓 재전송 시간 제한(초)을 설정합니다. 기본값은 2로 설정됩니다.
 - **NX_HTTP_SERVER_ RETRY_MAX** 서버 소켓의 최대 재전송 수를 설정합니다. 기본값은 10으로 설정됩니다.
 - **NX_HTTP_SERVER_ RETRY_SHIFT** 이 값은 다음 재전송 시간 제한을 설정하는 데 사용됩니다. 현재 시간 제한에는 소켓 제한 시간 이동의 값으로 이동하여 지금까지의 재전송 횟수를 곱합니다. 제한 시간을 두 배로 설정하기 위해 기본값은 1로 설정됩니다.
 - **NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH** 서버 소켓 재전송 큐에서 큐에 넣을 수 있는 최대 패킷 수를 지정합니다. 큐에 넣은 패킷 수가 이 수에 도달하면 하나 이상의 큐에 넣은 패킷을 해제할 때까지 더 이상 패킷을 전송할 수 없습니다. 기본값은 20으로 설정됩니다.
