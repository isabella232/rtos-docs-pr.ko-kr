---
title: 2장 - Azure RTOS NetX AutoIP 설치 및 사용
description: 이 장에서는 Azure RTOS NetX AutoIP 구성 요소의 설치, 설정, 사용과 관련된 다양한 문제를 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 269a3b4e9754fdc19e2cf1482d483fad2b841de9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810428"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-autoip"></a>2장 - Azure RTOS NetX AutoIP 설치 및 사용

이 장에서는 Azure RTOS NetX AutoIP 구성 요소의 설치, 설정, 사용과 관련된 다양한 문제를 설명합니다.

## <a name="product-distribution"></a>제품 배포

NetX AutoIP는 [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx)에서 사용할 수 있습니다. 패키지에는 다음과 같이 3개의 원본 파일과 하나의 포함 파일, 이 문서가 포함된 PDF 파일이 있습니다.

- **nx_auto_ip.h**: NetX AutoIP의 헤더 파일입니다.
- **nx_auto_ip.c**: NetX AutoIP의 C 원본 파일입니다.
- **demo_netx_auto_ip.c**: NetX AutoIP 데모의 C 원본 파일입니다.
- **nx_auto_ip.pdf**: NetX AutoIP에 대한 PDF 설명입니다.

## <a name="autoip-installation"></a>AutoIP 설치

NetX AutoIP를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 디렉터리에 복사해야 합니다. 예를 들어 NetX가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 *nx_auto_ip.h*, *nx_auto_ip.c*, *demo_netx_auto_ip.c* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="using-autoip"></a>AutoIP 사용

NetX AutoIP를 사용하는 것은 쉽습니다. 기본적으로 애플리케이션 코드는 ThreadX 및 NetX를 사용하기 위해 *tx_api.h* 및 *nx_api.h* 를 포함한 후 *nx_auto_ip.h* 를 포함해야 합니다. *nx_auto_ip.h* 를 포함하면 애플리케이션 코드가 이 가이드의 뒷부분에 지정된 AutoIP 함수를 호출할 수 있습니다. 애플리케이션은 *nx_auto_ip.c* 도 빌드 프로세스에 포함해야 합니다. 이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 개체 양식이 애플리케이션의 파일과 함께 연결되어야 합니다. 이렇게 간단하게 NetX AutoIP를 사용할 수 있습니다.

> [!NOTE]
> AutoIP는 NetX ARP 서비스를 활용하므로 AutoIP를 사용하기 전에 *nx_arp_enable* 호출로 ARP를 사용하도록 설정해야 합니다.

## <a name="small-example-system"></a>간단한 예제 시스템

NetX AutoIP를 사용하는 것이 얼마나 쉬운지 보여 주는 예가 아래에 표시된 그림 1.1에 설명되어 있습니다. 이 예에서는 002 줄에서 AutoIP 포함 파일 *nx_auto_ip.h* 를 가져옵니다. 그런 다음, 090 줄에서 “*tx_application_define*”에 NetX AutoIP 인스턴스를 만듭니다. NetX AutoIP 제어 블록 “auto_ip_0”은 이전에 015 줄에서 전역 변수로 정의되었습니다. 인스턴스가 성공적으로 생성되면 098 줄에서 NetX AutoIP가 시작됩니다. IP 주소 변경 콜백 함수 처리는 105 줄에서 시작되며, 이후 충돌 또는 가능한 DHCP 주소 확인을 처리하는 데 사용합니다.

> [!NOTE]
> 아래 예에서는 호스트 디바이스가 단일 홈 디바이스인 것으로 가정합니다. 멀티홈 디바이스의 경우 호스트 애플리케이션은 NetX AutoIP 서비스 *nx_auto_ip_interface_* set을 사용하여 IP 주소를 검색할 보조 네트워크 인터페이스를 지정할 수 있습니다. 멀티홈 애플리케이션 설정에 대한 자세한 내용은 **NetX 사용자 가이드** 를 참조하세요. 호스트 애플리케이션에서 NetX API *nx_status_ip_interface_check* 를 사용하여 AutoIP가 IP 주소를 얻었는지 확인해야 합니다.

## <a name="example-of-autoip-use-with-netx"></a>NetX에서의 AutoIP 사용 예

```c
000 #include "tx_api.h"
001 #include "nx_api.h"
002 #include "nx_auto_ip.h"
003
004 #define         DEMO_STACK_SIZE         4096
005
006 /* Define the ThreadX and NetX object control blocks... */
007
008 TX_THREAD         thread_0;
009 NX_PACKET_POOL    pool_0;
010 NX_IP             ip_0;
011
012
013 /* Define the AUTO IP structures for the IP instance. */
014
015 NX_AUTO_IP         auto_ip_0;
016
017
018 /* Define the counters used in the demo application... */
019
020 ULONG             thread_0_counter;
021 ULONG             address_changes;
022 ULONG             error_counter;
023
024
025 /* Define thread prototypes. */
026
027 void     thread_0_entry(ULONG thread_input);
028 void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
029 void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
030
031
032 /* Define main entry point. */
033
034 int main()
035 {
036
037     /* Enter the ThreadX kernel. */
038     tx_kernel_enter();
039 }
040
041
042 /* Define what the initial system looks like. */
043
044 void     tx_application_define(void *first_unused_memory)
045 {
046
047 CHAR     *pointer;
048 UINT     status;
049
050
051     /* Setup the working pointer. */
052     pointer = (CHAR *) first_unused_memory;
053
054     /* Create the main thread. */
055     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
056                     pointer, DEMO_STACK_SIZE,
057                     16, 16, 1, TX_AUTO_START);
058
059     pointer = pointer + DEMO_STACK_SIZE;
060
061     /* Initialize the NetX system. */
062     nx_system_initialize();
063
064     /* Create a packet pool. */
065     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
066                                     pointer, 4096);
067                                     pointer = pointer + 4096;
068
069     if (status)
070         error_counter++;
071
072     /* Create an IP instance. */
073     status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
074                             0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
075                             pointer, 4096, 1);
076                             pointer = pointer + 4096;
077
078     if (status)
079         error_counter++;
080
081     /* Enable ARP and supply ARP cache memory for IP Instance 0. */
082     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
083     pointer = pointer + 1024;
084
085     /* Check ARP enable status. */
086     if (status)
087         error_counter++;
088
089     /* Create the AutoIP instance for IP Instance 0. */
090     status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
091     pointer = pointer + 4096;
092
093     /* Check AutoIP create status. */
094     if (status)
095         error_counter++;
096
097     /* Start AutoIP instances. */
098     status = nx_auto_ip_start(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);
099
100     /* Check AutoIP start status. */
101     if (status)
102         error_counter++;
103
104     /* Register an IP address change function for IP Instance 0. */
105     status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
106                                         (void *) &auto_ip_0);
107
108     /* Check IP address change notify status. */
109     if (status)
110         error_counter++;
111     }
112
113
114     /* Define the test thread. */
115
116     void thread_0_entry(ULONG thread_input)
117     {
118
119     UINT      status;
120     ULONG     actual_status;
121
122
123          /* Wait for IP address to be resolved. */
124         do
125         {
126
127             /* Call IP status check routine. */
128             status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
129                                         &actual_status, 10000);
130
131         } while (status != NX_SUCCESS);
132
133         /* Since the IP address is resolved at this point, the application
134         can now fully utilize NetX! */
135
136         while(1)
137         {
138
139
140
141             /* Increment thread 0's counter. */
142             thread_0_counter++;
143
144             /* Sleep... */
145             tx_thread_sleep(10);
146         }
147     }
148
149
150     void ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
151     {
152
153     ULONG         ip_address;
154     ULONG         network_mask;
155     NX_AUTO_IP    *auto_ip_ptr;
156
157
158     /* Setup pointer to auto IP instance. */
159     auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;
160
161     /* Pickup the current IP address. */
162     nx_ip_address_get(ip_ptr, &ip_address, &network_mask);
163
164     /* Determine if the IP address has changed back to zero. If so,
165     make sure the AutoIP instance is started. */
166     if (ip_address == 0)
167     {
168
169         /* Get the last AutoIP address for this node. */
170         nx_auto_ip_get_address(auto_ip_ptr, &ip_address);
171
172         /* Start this AutoIP instance. */
173         nx_auto_ip_start(auto_ip_ptr, ip_address);
174     }
175
176     /* Determine if IP address has transitioned to a non local IP address. */
177     else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
178     {
179
180         /* Stop the AutoIP processing. */
181         nx_auto_ip_stop(auto_ip_ptr);
182     }
183
184     /* Increment a counter. */
185     address_changes++;
186 }
```

## <a name="configuration-options"></a>구성 옵션

NetX AutoIP를 빌드하는 데 사용되는 여러 구성 옵션이 있습니다. 다음은 각 옵션에 대한 자세한 설명입니다.

- **NX_DISABLE_ERROR_CHECKING**: 이 옵션을 정의하면 기본 AutoIP 오류 검사를 제거합니다. 일반적으로 애플리케이션이 디버그된 후에 사용됩니다.
- **NX_AUTO_IP_PROBE_WAIT**: 첫 번째 프로브 송신 전 대기 시간(초)입니다. 기본적으로 이 값은 1로 정의됩니다.
- **NX_AUTO_IP_PROBE_NUM**: 송신할 ARP 프로브 수입니다. 기본적으로 이 값은 3으로 정의됩니다.
- **NX_AUTO_IP_PROBE_MIN**: 프로브 송신 간 최소 대기 시간(초)입니다. 기본적으로 이 값은 1로 정의됩니다.
- **NX_AUTO_IP_PROBE_MAX**: 프로브 송신 간 최대 대기 시간(초)입니다. 기본적으로 이 값은 2로 정의됩니다.
- **NX_AUTO_IP_MAX_CONFLICTS**: 처리 지연을 늘리기 전 AutoIP 충돌 수입니다. 기본적으로 이 값은 10으로 정의됩니다.
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL**: 총 충돌 수를 초과하는 경우 연장할 대기 시간(초)입니다. 기본적으로 이 값은 60으로 정의됩니다.
- **NX_AUTO_IP_ANNOUNCE_WAIT**: 알림 송신 전 대기 시간(초)입니다. 기본적으로 이 값은 2로 정의됩니다.
- **NX_AUTO_IP_ANNOUNCE_NUM**: 송신할 ARP 알림 수입니다. 기본적으로 이 값은 2로 정의됩니다.
- **NX_AUTO_IP_ANNOUNCE_INTERVAL**: 알림 송신 간 대기 시간(초)입니다. 기본적으로 이 값은 2로 정의됩니다.
- **NX_AUTO_IP_DEFEND_INTERVAL**: 방어 알림 간 대기 시간(초)입니다. 기본적으로 이 값은 10으로 정의됩니다.