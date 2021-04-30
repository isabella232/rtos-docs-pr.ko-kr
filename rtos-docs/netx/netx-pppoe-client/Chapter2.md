---
title: 2장 - Azure RTOS NetX PPPoE 클라이언트의 설치 및 사용
description: 이 장에서는 Azure RTOS NetX PPPoE 클라이언트 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 17d910647db7b207280b3fbd9e90c468293a8e67
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811454"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-client"></a>2장 - Azure RTOS NetX PPPoE 클라이언트의 설치 및 사용

이 장에서는 Azure RTOS NetX PPPoE 클라이언트 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

NetX용 PPPoE 클라이언트는 [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx)에서 사용할 수 있습니다. 패키지에는 다음 파일이 포함되어 있습니다.

 - **nx_pppoe_client.h** NetX용 PPPoE 클라이언트의 헤더 파일
 - **nx_pppoe_client.c** NetX용 PPPoE 클라이언트의 C 원본 파일
 - **nx_pppoe_client.pdf** NetX용 PPPoE 클라이언트의 PDF 설명
 - **demo_netx_pppoe_client.c** NetX PPPoE 클라이언트 데모

## <a name="pppoe-client-installation"></a>PPPoE 클라이언트 설치

NetX용 PPPoE 클라이언트를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX가 *“\threadx\arm7\green”* 디렉터리에 설치된 경우 *nx_pppoe_client.h* 및 *nx_pppoe_client.c* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="using-pppoe-client"></a>PPPoE 클라이언트 사용

NetX용 PPPoE 클라이언트를 사용하는 것은 쉽습니다. 기본적으로 애플리케이션 코드는 ThreadX 및 NetX를 각각 사용하기 위해 *tx_api.h* 및 *nx_api.h* 를 포함한 후 *nx_pppoe_client.h* 를 포함해야 합니다. *nx_pppoe_client.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 PPPoE 클라이언트 함수 호출을 수행할 수 있습니다. 애플리케이션은 빌드 프로세스에 *nx_pppoe_client.c* 도 포함해야 합니다. 이 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 해당 개체 형식은 애플리케이션의 파일과 함께 연결되어야 합니다. 이것이 NetX PPPoE 클라이언트를 사용하는 데 필요한 전부입니다.

## <a name="small-example-system"></a>간단한 예제 시스템

다음은 NetX PPPoE 클라이언트를 사용하는 방법을 보여 주는 예제로 그림 1.1에 설명되어 있습니다. 이 예제에서 PPPoE 클라이언트는 50줄에서 가져온 파일 *nx_pppoe_client.h* 를 포함합니다. 다음으로, PPPoE 클라이언트는 238줄에서 *”thread_0_entry”* 에 만들어집니다. IP 인스턴스를 만든 후에는 PPPoE 클라이언트를 만들어야 합니다. IP 인스턴스와 PPP 인스턴스가 생성되고 142-220줄이 초기화됩니다. PPPoE 클라이언트 제어 블록 *“pppoe_client”* 가 이전에 75줄에서 전역 변수로 정의되었습니다. 송신 및 수신 함수는 238줄에 설정됩니다.

일반적으로 PPPoE 모듈은 PPP 모듈과 함께 사용해야 합니다. 이 예제에서는 PPP 클라이언트 포함 파일 *nx_ppp.h* 를 49줄에서 가져옵니다. 다음으로, 164줄에 PPP 클라이언트가 생성됩니다. 172줄은 PPP 패킷을 보내도록 함수를 설정합니다. 179-190줄은 IP 주소를 설정하고 pap 프로토콜을 정의합니다. 104-129줄은 pap 프로토콜에 대한 사용자 이름 및 암호를 설정합니다.

PPPoE 세션이 설정된 후. 애플리케이션은 *nx_pppoe_client_session_get* 을 호출하여 264줄에서 세션 정보(서버 MAC 주소 및 세션 ID)를 호출할 수 있습니다. PPP 또는 애플리케이션은 *nx_pppoe_client_session_packet_send* 를 호출하여 283줄에서 PPPoE 패킷을 보낼 수 있습니다.

애플리케이션이 더 이상 PPP 트래픽을 처리하지 않을 경우 애플리케이션은 *nx_pppoe_client_session_terminate* 를 호출하여 PPPoE 세션을 종료할 수 있습니다.

이 예제에서 PPPoE 클라이언트는 동시에 일반 IP 스택에서 작업하고 하나의 이더넷 드라이버를 공유합니다. 155줄의 일반 IP 인스턴스와 298줄의 PPPoE 클라이언트 인스턴스에 대해 동일한 이더넷 드라이버를 전달합니다.

> [!NOTE]
> 실제 헤더를 채우는 데 충분한 공간을 확보하기 위해 **NX_PHYSICAL_HEADER** 를 24로 다시 정의합니다. 실제 헤더: 14(이더넷 헤더) + 6(PPPoE 헤더) + 2(PPP 헤더) + 2(4바이트 정렬).

```c
  1 /**************************************************************************/
  2 /**************************************************************************/
  3 /**                                                                       */
  4 /** NetX PPPoE Client stack Component                                     */
  5 /**                                                                       */
  6 /**   This is a small demo of the high-performance NetX PPPoE Client      */
  7 /**   stack. This demo includes IP instance, PPPoE Client and PPP Client  */
  8 /**   stack. Create one IP instance includes two interfaces to support    */
  9 /**   for normal IP stack and PPPoE Client, PPPoE Client can use the      */
 10 /**   mutex of IP instance to send PPPoE message when share one Ethernet  */
 11 /**   driver. PPPoE Client work with normal IP instance at the same time. */
 12 /**                                                                       */
 13 /**   Note1: Substitute your Ethernet driver instead of                   */
 14 /**   _nx_ram_network_driver before run this demo                         */
 15 /**                                                                       */
 16 /**   Note2: Prerequisite for using PPPoE.                                */
 17 /**   Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling*/
 18 /**   in physical header. Physical header:14(Ethernet header)             */
 19 /**    + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)          */
 20 /**                                                                       */
 21 /**************************************************************************/
 22 /**************************************************************************/
 23
 24
 25       /*****************************************************************/
 26       /*                          NetX Stack                           */
 27       /*****************************************************************/
 28
 29                                             /***************************/
 30                                             /*        PPP Client       */
 31                                             /***************************/
 32
 33                                             /***************************/
 34                                             /*       PPPoE Client      */
 35                                             /***************************/
 36       /***************************/         /***************************/
 37       /*    Normal Ethernet Type */         /*    PPPoE Ethernet Type  */
 38       /***************************/         /***************************/
 39       /***************************/         /***************************/
 40       /*       Interface 0       */         /*       Interface 1       */
 41       /***************************/         /***************************/
 42
 43       /*****************************************************************/
 44       /*                       Ethernet Dirver                         */
 45       /*****************************************************************/
 46
 47 #include   "tx_api.h"
 48 #include   "nx_api.h"
 49 #include   "nx_ppp.h"
 50 #include   "nx_pppoe_client.h"
 51
 52 /* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified
       to match PPPoE moduler under this definition.  */
 53 #ifdef NX_PPP_PPPOE_ENABLE
 54
 55 /* If the driver is not initialized in other module, define NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE
       to initialize the driver in PPPoE module .
 56    In this demo, the driver has been initialized in IP module.  */
 57 #ifndef NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE
 58
 59 /* Define the block size.  */
 60 #define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
 61 #define     DEMO_STACK_SIZE         2048
 62 #define     PPPOE_THREAD_SIZE       2048
 63
 64 /* Define the ThreadX and NetX object control blocks...  */
 65 TX_THREAD               thread_0;
 66
 67 /* Define the packet pool and IP instance for normal IP instnace.  */
 68 NX_PACKET_POOL          pool_0;
 69 NX_IP                   ip_0;
 70
71 /* Define the PPP Client instance.  */
 72 NX_PPP                  ppp_client;
 73
 74 /* Define the PPPoE Client instance.  */
 75 NX_PPPOE_CLIENT         pppoe_client;
 76
 77 /* Define the counters.  */
 78 CHAR                    *pointer;
 79 ULONG                   error_counter;
 80
 81 /* Define thread prototypes.  */
 82 void    thread_0_entry(ULONG thread_input);
 83
 84 /***** Substitute your PPP driver entry function here *********/
 85 extern void    _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);
 86
 87 /***** Substitute your Ethernet driver entry function here *********/
 88 extern void    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
 89
 90 /* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP.
 91    Functions to be provided by PPP for calling by the PPPoE Stack.  */
 92 void    ppp_client_packet_send(NX_PACKET *packet_ptr);
 93 void    pppoe_client_packet_receive(NX_PACKET *packet_ptr);
 94
 95 /* Define main entry point.  */
 96
 97 int main()
 98 {
 99
100     /* Enter the ThreadX kernel.  */
101     tx_kernel_enter();
102 }
103
104 UINT generate_login(CHAR *name, CHAR *password)
105 {
106
107     /* Make a name and password, called "myname" and "mypassword".  */
108     name[0] = 'm';
109     name[1] = 'y';
110     name[2] = 'n';
111     name[3] = 'a';
112     name[4] = 'm';
113     name[5] = 'e';
114     name[6] = (CHAR) 0;
115
116     password[0] = 'm';
117     password[1] = 'y';
118     password[2] = 'p';
119     password[3] = 'a';
120     password[4] = 's';
121     password[5] = 's';
122     password[6] = 'w';
123     password[7] = 'o';
124     password[8] = 'r';
125     password[9] = 'd';
126     password[10] = (CHAR) 0;
127
128     return(NX_SUCCESS);
129 }
130
131 /* Define what the initial system looks like.  */
132
133 void    tx_application_define(void *first_unused_memory)
134 {
135
136 UINT    status;
137
138     /* Setup the working pointer.  */
139     pointer =  (CHAR *) first_unused_memory;
140
141     /* Initialize the NetX system.  */
142     nx_system_initialize();
143
144     /* Create a packet pool for normal IP instance.  */
145     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
146                                    (1536 + sizeof(NX_PACKET)),
147                                    pointer, NX_PACKET_POOL_SIZE);
148     pointer = pointer + NX_PACKET_POOL_SIZE;
149
150     /* Check for error.  */
151     if (status)
152         error_counter++;
153
154     /* Create an normal IP instance.  */
155     status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 44), 0xFFFFFF00UL,
156                           &pool_0, _nx_ram_network_driver, pointer, 2048, 1);
157     pointer = pointer + 2048;
158
159     /* Check for error.  */
160     if (status)
161         error_counter++;
162
163     /* Create the PPP instance.  */
164     status = nx_ppp_create(&ppp_client, "PPP Instance", &ip_0, pointer, 2048, 1,
165                            &pool_0, NX_NULL, NX_NULL); pointer = pointer + 2048;
166
167     /* Check for PPP create error.   */
168     if (status)
169         error_counter++;
170
171     /* Set the PPP packet send function.  */
172     status = nx_ppp_packet_send_set(&ppp_client, ppp_client_packet_send);
173
174     /* Check for PPP packet send function set error.   */
175     if (status)
176         error_counter++;
177
178     /* Define IP address. This PPP instance is effectively the client since it doesn't have
           any IP addresses. */
179     status = nx_ppp_ip_address_assign(&ppp_client, IP_ADDRESS(0, 0, 0, 0), IP_ADDRESS(0, 0, 0, 0));
180
181     /* Check for PPP IP address assign error.   */
182     if (status)
183         error_counter++;
184
185     /* Setup PAP, this PPP instance is effectively the since it generates the name and password
           for the peer..  */
186     status = nx_ppp_pap_enable(&ppp_client, generate_login, NX_NULL);
187
188     /* Check for PPP PAP enable error.  */
189     if (status)
190         error_counter++;
191
192     /* Attach an interface for PPP.  */
193     status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", IP_ADDRESS(0, 0, 0, 0), 0,
                                        nx_ppp_driver);
194
195     /* Check for error.  */
196     if (status)
197         error_counter++;
198
199     /* Enable ARP and supply ARP cache memory for Normal IP Instance.  */
200     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
201     pointer = pointer + 1024;
202
203     /* Check for ARP enable errors.  */
204     if (status)
205         error_counter++;
206
207     /* Enable ICMP */
208     status = nx_icmp_enable(&ip_0);
209     if(status)
210         error_counter++;
211
212     /* Enable UDP traffic.  */
213     status =  nx_udp_enable(&ip_0);
214     if (status)
215         error_counter++;
216
217     /* Enable TCP traffic.  */
218     status =  nx_tcp_enable(&ip_0);
219     if (status)
220         error_counter++;
221
222     /* Create the main thread.  */
223     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
224                      pointer, DEMO_STACK_SIZE,
225                      4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
226     pointer =  pointer + DEMO_STACK_SIZE;
227
228 }
229
230 /* Define the test threads.  */
231
232 void    thread_0_entry(ULONG thread_input)
233 {
234 UINT    status;
235 ULONG   ip_status;
236
237     /* Create the PPPoE instance.  */
238     status =  nx_pppoe_client_create(&pppoe_client, (UCHAR *)"PPPoE Client",  &ip_0,  0,
        &pool_0, pointer, PPPOE_THREAD_SIZE, 4, _nx_ram_network_driver, pppoe_client_packet_receive);
239     pointer = pointer + PPPOE_THREAD_SIZE;
240     if (status)
241     {
242         error_counter++;
243         return;
244     }
245
246     /* Establish PPPoE Client sessione.  */
247     status = nx_pppoe_client_session_connect(&pppoe_client, NX_WAIT_FOREVER);
248     if (status)
249     {
250         error_counter++;
251         return;
252     }
253
254     /* Wait for the link to come up.  */
255     status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                              &ip_status, NX_WAIT_FOREVER);
256     if (status)
257     {
258         error_counter++;
259         return;
260     }
261
262     /* Get the PPPoE Server physical address and Session ID after establish PPPoE Session.  */
263     /*
264     status = nx_pppoe_client_session_get(&pppoe_client, &server_mac_msw,
                                             &server_mac_lsw, &session_id);
265     if (status)
266         error_counter++;
267     */
268 }
269
270 /* PPPoE Client receive function.  */
271 void    pppoe_client_packet_receive(NX_PACKET *packet_ptr)
272 {
273
274     /* Call PPP Client to receive the PPP data fame.  */
275     nx_ppp_packet_receive(&ppp_client, packet_ptr);
276 }
277
278 /* PPP Client send function.  */
279 void    ppp_client_packet_send(NX_PACKET *packet_ptr)
280 {
281
282     /* Directly Call PPPoE send function to send out the data through PPPoE module.  */
283     nx_pppoe_client_session_packet_send(&pppoe_client, packet_ptr);
284 }
285 #endif /* NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE  */
286
287 #endif /* NX_PPP_PPPOE_ENABLE  */
```

**그림 1.1 NetX에서의 PPPoE 클라이언트 사용 예제**

## <a name="configuration-options"></a>구성 옵션

NetX용 PPPoE 클라이언트를 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음 목록에서 각각에 대해 자세히 설명합니다.

- **NX_DISABLE_ERROR_CHECKING**: 정의된 이 옵션은 기본 PPPoE 클라이언트 오류 검사를 제거합니다. 일반적으로 애플리케이션이 디버깅된 후에 사용됩니다.
- **NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE** 정의된 경우 PPPoE 모듈의 이더넷 드라이버를 초기화하는 기능을 사용하도록 설정합니다. 기본적으로는 사용하지 않도록 설정되어 있습니다.
- **NX_PPPOE_CLIENT_THREAD_TIME_SLICE** PPPoE 클라이언트 스레드에 대한 시간 조각 옵션입니다. 기본적으로 이 값은 TX_NO_TIME_SLICE입니다.
- **NX_PPPOE_CLIENT_PADI_INIT_TIMEOUT** 이는 초기 PADI 패킷을 재전송하기 위한 대기 시간을 정의합니다. 기본적으로 이 값은 1초입니다.
- **NX_PPPOE_CLIENT_PADI_COUNT** 연결이 끊긴 것으로 간주되기 전에 허용되는 PADI 전송 사용 중지 수를 정의합니다. 기본적으로 이 값은 4입니다.
- **NX_PPPOE_CLIENT_PADR_INIT_TIMEOUT** 초기 PADR 패킷을 재전송하기 위한 대기 시간을 정의합니다. 기본적으로 이 값은 1초입니다.
- **NX_PPPOE_CLIENT_PADR_COUNT** 연결이 끊긴 것으로 간주되기 전에 허용되는 PADR 전송 사용 중지 수를 정의합니다. 기본적으로 이 값은 4입니다.
- **NX_PPPOE_CLIENT_MAX_AC_NAME_SIZE** 최대 크기의 AC 이름을 정의합니다. 기본적으로 이 값은 32입니다.
- **NX_PPPOE_CLIENT_MAX_AC_COOKIE_SIZE** 최대 크기의 AC 쿠키를 정의합니다. 기본적으로 이 값은 32입니다.
- **NX_PPPOE_CLIENT_MAX_RELAY_SESSION_ID_SIZE** 릴레이 세션 ID의 최대 크기를 정의합니다. 기본적으로 이 값은 12입니다.
- **NX_PPPOE_CLIENT_MIN_PACKET_PAYLOAD_SIZE** PPPoE 클라이언트에 대한 최소 패킷 페이로드 크기를 지정합니다. 패킷 페이로드 크기가 이 값보다 크면, 연결된 패킷을 피할 수 있습니다. 기본적으로 이 값은 1520(이더넷 1500, 이더넷 헤더 14, CRC 2 및 4바이트 정렬 4의 최대 페이로드 크기)입니다.
