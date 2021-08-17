---
title: 6장 - Azure RTOS ThreadX SMP에 대한 데모 시스템
description: 이 장에는 모든 Azure RTOS ThreadX SMP 프로세서 지원 패키지와 함께 제공되는 데모 시스템에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5da4c12cf3c035e59dcd1abef063d5ae40a657d6fd91bbd29f51cf7d46813154
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784056"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx-smp"></a>6장 - Azure RTOS ThreadX SMP에 대한 데모 시스템

이 장에는 모든 Azure RTOS ThreadX SMP 프로세서 지원 패키지와 함께 제공되는 데모 시스템에 대한 설명이 포함되어 있습니다. 

## <a name="overview"></a>개요

각 ThreadX SMP 제품 배포에는 지원되는 모든 마이크로프로세서에서 실행되는 데모 시스템이 포함되어 있습니다.

이 예제 시스템은 배포 파일 ***demo_threadx.c*** 에 정의되어 있으며, ThreadX SMP가 포함된 다중 스레드 환경에서 어떻게 사용되는지 보여 주기 위해 설계되었습니다. 이 데모는 초기화, 8개의 스레드, 1바이트 풀, 하나의 블록 풀, 하나의 큐, 하나의 세마포, 하나의 뮤텍스 및 하나의 이벤트 플래그 그룹으로 구성됩니다.

> [!IMPORTANT]
> 스레드의 스택 크기를 제외하고 데모 애플리케이션은 모든 ThreadX SMP 지원 프로세서에서 동일합니다.

이 장의 나머지 부분에서 참조되는 줄 번호를 포함하는 ***demo_threadx.c*** 의 전체 목록은 324 페이지 이후에 나와있습니다.

## <a name="application-define"></a>애플리케이션 정의

***tx_application_define*** 함수는 기본 ThreadX SMP 초기화가 완료된 후에 실행됩니다. 스레드, 큐, 세마포, 뮤텍스, 이벤트 플래그 및 메모리 풀을 비롯한 모든 초기 시스템 리소스를 설정해야 합니다.

데모 시스템의 ***tx_application_define** _(_줄 번호 60-164*)은 데모 개체를 다음 순서로 만듭니다.

```C
byte_pool_0
thread_0
thread_1
thread_2
thread_3
thread_4
thread_5
thread_6
thread_7
queue_0
semaphore_0
event_flags_0
mutex_0
block_pool_0
```
데모 시스템은 다른 추가적인 ThreadX SMP 개체를 만들지 않습니다. 그러나 실제 애플리케이션은 실행 중인 스레드 내에서 런타임 중에 시스템 개체를 만들 수 있습니다.

### <a name="initial-execution"></a>초기 실행 
모든 스레드는 **TX_AUTO_START** 옵션을 사용하여 생성됩니다. 이렇게 하면 처음에 실행할 준비가 된 것입니다. **_tx_application_define_** 이 완료되면 컨트롤이 스레드 스케줄러에 전송되며 거기서 각 개별 스레드로 전달됩니다.

스레드가 실행되는 순서는 우선 순위 및 생성된 순서에 따라 결정됩니다. 데모 시스템에서 ***thread_0** 은 우선 순위가 가장 높고(_우선 순위 1*로 만듦) 먼저 실행됩니다. ***Thread_0**_ 이 일시 중단되면, _*_thread_5_*_ 가 실행된 다음, _*_thread_3_*_, _*_thread_4_*_ , _*_thread_6_*_ , _*_thread_7_*_ , _*_thread_1_*_ 및 마지막으로 _*_thread_2_**가 실행됩니다.

> [!IMPORTANT]
> **Thread_3** 및 **thread_4** 가 동일한 우선 순위라 하더라고(둘 다 우선 순위가 8로 생성됨), **thread_3** 이 먼저 실행됩니다. 이는 **thread_3** 이 만들어지고 **thread_4** 전에 준비되었기 때문입니다. 우선 순위가 같은 스레드는 FIFO 방식으로 실행됩니다.

## <a name="thread-0"></a>Thread 0

함수 ***thread_0_entry** 는 스레드의 진입점을 표시합니다 _(줄 167-190*). ***Thread_0**_ 은 데모 시스템에서 실행할 첫 번째 스레드입니다. 해당 프로세스는 간단합니다. 카운터를 증가시키고, 10개 타이머 틱에 대해 대기하고, _*_thread_5_**를 해제하도록 이벤트 플래그를 설정한 다음, 시퀀스를 반복합니다.

***Thread_0*** 은 시스템에서 가장 높은 우선 순위 스레드입니다. 요청된 일시 중지가 만료되면 데모에서 다른 실행 스레드를 선점합니다.

## <a name="thread-1"></a>Thread 1

함수 ***thread_1_entry** 는 스레드의 진입점을 표시합니다 _(줄 193-216*). ***Thread_1**_ 은 데모 시스템에서 마지막에서 두 번째 스레드로 실행됩니다. 해당 프로세스는 카운터를 증가시키고, _*_thread_2_*_ 으로 메시지를 보내고(_****queue_0**_ 을 통해), 시퀀스를 반복하는 것으로 구성됩니다. _*_thread_1_*_ 은 _*_queue_0_*_ 이 가득 찰 때마다(_줄 207*) 일시 중단됩니다.

## <a name="thread-2"></a>Thread 2

함수 ***thread_2_entry** 는 스레드의 진입점 _을 표시합니다(줄 219-243*). ***Thread_2**_ 는 데모 시스템에서 실행할 마지막 스레드입니다. 해당 프로세스는 카운터를 증가시키고, _*_thread_1_*_ 에서 메시지를 가져오고(_*_queue_0_*_ 을 통해), 시퀀스를 반복하는 것으로 구성됩니다. _*_thread_2_*_ 는 _*_queue_0_*_ 이 비어 있을 때마다 일시 중단됩니다(_줄 233*).

***thread_1** _ 및 _*_thread_2_*_ 가 데모 시스템(_우선 순위 16 *)에서 가장 낮은 우선 순위를 공유하지만 대부분의 시간 동안 실행할 준비가 된 유일한 스레드이기도 합니다. 또한 시간 조각화(* 줄 87 및 93*)를 사용하여 만든 유일한 스레드입니다. 각 스레드는 다른 스레드가 실행되기 전에 최대 4개의 타이머 틱을 실행할 수 있습니다.

## <a name="threads-3-and-4"></a>Thread 3 및 4

***thread_3_and_4_entry** _ 함수는 _*_thread_3_*_ 과 _*_thread_4_*_ 의 진입점을 표시합니다 _(줄 246-280*). 두 스레드 모두 우선 순위 8을 가지며, 이를 통해 데모 시스템에서 세 번째와 네 번째 스레드를 실행할 수 있습니다. 각 스레드에 대한 처리는 카운터의 동일한 증가, ***semaphore_0** 가져오기_, 2개 타이머 틱 일시 중지하기, _*_semaphore_0_*_ 해제하기 및 시퀀스 반복하기입니다. _*_semaphore_0_*_ 을 사용할 수 없을 때마다(_줄 264) 각 스레드가 일시 중단됩니다.

또한 두 스레드 모두 주 프로세스에 동일한 함수를 사용합니다. 여기에는 자체의 고유한 스택이 있고 C가 기본적으로 재진입되기 때문에 문제가 발생하지 않습니다. 각 스레드는 스레드 입력 매개 변수를 검사하여 어떤 스레드인지 결정하며(*줄 258*), 이는 생성될 때 설정됩니다(*줄 102 및 줄 109*).

> [!IMPORTANT]
> 스레드를 실행하는 동안 현재 스레드 지점을 가져와서 이를 제어 블록의 주소와 비교하여 스레드 ID를 확인하는 것도 합리적입니다.

## <a name="thread-5"></a>Thread 5

함수 ***thread_5_entry** _는 스레드의 진입점을 표시합니다 _(줄 283-305*). ***Thread_5**_ 는 시연 시스템에서 두 번째 스레드로 실행할 수 있습니다. 해당 프로세스는 카운터를 증가시키고, _*_thread_0_*_ 에서 이벤트 플래그를 가져오고(_*_event_flags_0_*_ 을 통해), 시퀀스를 반복하는 것으로 구성됩니다. _*_event_flags_0_*_ 의 이벤트 플래그를 사용할 수 없을 때(_줄 298), _*_thread_5_*_ 가 일시 중단됩니다.

## <a name="threads-6-and-7"></a>Thread 6 및 7

함수 ***Thread_6_and_7_entry** 는 _*_thread_6_*_ 과 _*_thread_7_*_ 의 진입점을 표시합니다 _(줄 307-358*). 두 스레드 모두 우선 순위 8을 가지며, 이를 통해 데모 시스템에서 다섯 번째 및 여섯 번째 스레드를 실행할 수 있습니다. 각 스레드에 대한 처리는 동일합니다. 카운터를 증가시키고, ***mutex_0**_ 을 두 번 가져오고, 타이머 틱 2개에 대해 일시 중지하고, _*_mutex_0_*_ 두 번 해제하고, 시퀀스를 반복하는 것입니다. _*_mutex_0_*_ 을 사용할 수 없을 때마다 각 스레드가 일시 중단됩니다(_줄 325*).

또한 두 스레드 모두 주 프로세스에 동일한 함수를 사용합니다. 여기에는 자체의 고유한 스택이 있고 C가 기본적으로 재진입되기 때문에 문제가 발생하지 않습니다. 각 스레드는 스레드 입력 매개 변수를 검사하여(*줄 319*) 어떤 스레드인지 결정하며, 이는 생성될 때 설정됩니다(*줄 126 및 줄 133*).

## <a name="observing-the-demonstration"></a>데모 관찰

각 데모 스레드는 고유한 카운터를 증가시킵니다. 다음 카운터를 검사하여 데모의 작업을 확인할 수 있습니다.

```C
thread_0_counter
thread_1_counter
thread_2_counter
thread_3_counter
thread_4_counter
thread_5_counter
thread_6_counter
thread_7_counter
```

이러한 각 카운터는 데모를 실행할 때 계속 증가해야 하며, ***thread_1_counter** _ 및 *_thread_2_counter_**가 가장 빠른 속도로 증가합니다.

## <a name="distribution-file-demo_threadxc"></a>배포 파일: demo_threadx.c

이 섹션에는 이 장 전반에 걸쳐 참조되는 줄 번호를 포함하는 ***demo_threadx.c*** 의 전체 목록이 나와 있습니다.

```C
000 /* This is a small demo of the high-performance ThreadX SMP kernel. It includes examples of eight
001 threads of different priorities, using a message queue, semaphore, mutex, event flags group,
002 byte pool, and block pool. */
003
004 #include "tx_api.h"
005
006 #define DEMO_STACK_SIZE         1024
007 #define DEMO_BYTE_POOL_SIZE     9120
008 #define DEMO_BLOCK_POOL_SIZE    100
009 #define DEMO_QUEUE_SIZE         100
010
011 /* Define the ThreadX SMP object control blocks...  */
012
013 TX_THREAD               thread_0;
014 TX_THREAD               thread_1;
015 TX_THREAD               thread_2;
016 TX_THREAD               thread_3;
017 TX_THREAD               thread_4;
018 TX_THREAD               thread_5;
019 TX_THREAD               thread_6;
020 TX_THREAD               thread_7;
021 TX_QUEUE                queue_0;
022 TX_SEMAPHORE            semaphore_0;
023 TX_MUTEX                mutex_0;
024 TX_EVENT_FLAGS_GROUP    event_flags_0;
025 TX_BYTE_POOL            byte_pool_0;
026 TX_BLOCK_POOL           block_pool_0;
027
028 /* Define the counters used in the demo application...  */
029
030 ULONG                    thread_0_counter;
031 ULONG                    thread_1_counter;
032 ULONG                    thread_1_messages_sent;
033 ULONG                    thread_2_counter;
034 ULONG                    thread_2_messages_received;
035 ULONG                    thread_3_counter;
036 ULONG                    thread_4_counter;
037 ULONG                    thread_5_counter;
038 ULONG                    thread_6_counter;
039 ULONG                    thread_7_counter;
040
041 /* Define thread prototypes.  */
042
043 void    thread_0_entry(ULONG thread_input);
044 void    thread_1_entry(ULONG thread_input);
045 void    thread_2_entry(ULONG thread_input);
046 void    thread_3_and_4_entry(ULONG thread_input);
047 void    thread_5_entry(ULONG thread_input);
048 void    thread_6_and_7_entry(ULONG thread_input);
049
050
051 /* Define main entry point.  */
052
053 int main()
054 {
055
056     /* Enter the ThreadX SMP kernel. */
057     tx_kernel_enter();
058 }
059
060 /* Define what the initial system looks like. */
061 void    tx_application_define(void *first_unused_memory)
062 {
063
064 CHAR    *pointer;
065
066    /* Create a byte memory pool from which to allocate the thread stacks. */
067    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
068                               DEMO_BYTE_POOL_SIZE);
069
070    /* Put system definition stuff in here, e.g., thread creates and other assorted
071       create information. */
072
073    /* Allocate the stack for thread 0. */
074    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
075
076    /* Create the main thread. */
077    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
078                               pointer, DEMO_STACK_SIZE,
079                               1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
080
081    /* Allocate the stack for thread 1. */
082    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
083
084    /* Create threads 1 and 2. These threads pass information through a ThreadX SMP
085       message queue. It is also interesting to note that these threads have a time
086       slice. */
087    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
088                              pointer, DEMO_STACK_SIZE,
089                              16, 16, 4, TX_AUTO_START);
090
091    /* Allocate the stack for thread 2. */
092    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
093    tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
094                              pointer, DEMO_STACK_SIZE,
095                              16, 16, 4, TX_AUTO_START);
096
097    /* Allocate the stack for thread 3. */
098    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
099
100    /* Create threads 3 and 4. These threads compete for a ThreadX SMP counting semaphore.
101       An interesting thing here is that both threads share the same instruction area. */
102    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
103                              pointer, DEMO_STACK_SIZE,
104                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
105
106    /* Allocate the stack for thread 4. */
107    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
108
109    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
110                              pointer, DEMO_STACK_SIZE,
111                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
112
113    /* Allocate the stack for thread 5. */
114    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
115
116    /* Create thread 5. This thread simply pends on an event flag, which will be set
117       by thread_0. */
118    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
119                              pointer, DEMO_STACK_SIZE,
120                              4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
121
122    /* Allocate the stack for thread 6. */
123    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
124
125    /* Create threads 6 and 7. These threads compete for a ThreadX SMP mutex. */
126    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
127                              pointer, DEMO_STACK_SIZE,
128                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
129
130    /* Allocate the stack for thread 7. */
131    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
132
133    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
134                              pointer, DEMO_STACK_SIZE,
135                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
136
137    /* Allocate the message queue. */
138    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);
139
140    /* Create the message queue shared by threads 1 and 2. */
141    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));
142
143    /* Create the semaphore used by threads 3 and 4. */
144    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);
145
146    /* Create the event flags group used by threads 1 and 5. */
147    tx_event_flags_create(&event_flags_0, "event flags 0");
148
149    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
150    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);
151
152    /* Allocate the memory for a small block pool. */
153    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);
154
155    /* Create a block memory pool to allocate a message buffer from. */
156    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
157                 DEMO_BLOCK_POOL_SIZE);
158
159    /* Allocate a block and release the block memory. */
160    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);
161
162    /* Release the block back to the pool. */
163    tx_block_release(pointer);
164 }
165
166    /* Define the test threads. */
167    void thread_0_entry(ULONG thread_input)
168 {
169
170 UINT status;
171
172
173    /* This thread simply sits in while-forever-sleep loop. */
174     while(1)
175    {
176
177    /* Increment the thread counter. */
178    thread_0_counter++;
179
180    /* Sleep for 10 ticks. */
181    tx_thread_sleep(10);
182
183    /* Set event flag 0 to wakeup thread 5. */
184    status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);
185
186    /* Check status. */
187    if (status != TX_SUCCESS)
188       break;
189    }
190 }
191
192
193 void    thread_1_entry(ULONG thread_input)
194 {
195
196 UINT    status;
197
198
199    /* This thread simply sends messages to a queue shared by thread 2. */
200    while(1)
201    {
202
203         /* Increment the thread counter. */
204         thread_1_counter++;
205
206         /* Send message to queue 0. */
207         status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);
208
209         /* Check completion status. */
210         if (status != TX_SUCCESS)
211            break;
212
213         /* Increment the message sent. */
214         thread_1_messages_sent++;
215    }
216 }
217
218
219 void     thread_2_entry(ULONG thread_input)
220 {
221
222 ULONG     received_message;
223 UINT      status;
224
225     /* This thread retrieves messages placed on the queue by thread 1. */
226     while(1)
227     {
228
229         /* Increment the thread counter. */
230         thread_2_counter++;
231
232         /* Retrieve a message from the queue. */
233         status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);
234
235         /* Check completion status and make sure the message is what we
236            expected. */
237         if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
238            break;
239
240         /* Otherwise, all is okay. Increment the received message count. */
241         thread_2_messages_received++;
242      }
243 }
244
245
246 void     thread_3_and_4_entry(ULONG thread_input)
247 {
248
249 UINT     status;
250
251
252     /* This function is executed from thread 3 and thread 4. As the loop
253        below shows, these function compete for ownership of semaphore_0. */
254     while(1)
255     {
256
257         /* Increment the thread counter. */
258         if (thread_input == 3)
259            thread_3_counter++;
260         else
261            thread_4_counter++;
262
263         /* Get the semaphore with suspension. */
264         status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);
265
266         /* Check status. */
267         if (status != TX_SUCCESS)
268            break;
269
270         /* Sleep for 2 ticks to hold the semaphore. */
271         tx_thread_sleep(2);
272
273         /* Release the semaphore. */
274         status = tx_semaphore_put(&semaphore_0);
275
276         /* Check status. */
277         if (status != TX_SUCCESS)
278             break;
279     }
280 }
281
282
283 void     thread_5_entry(ULONG thread_input)
284 {
285
286 UINT     status;
287 ULONG    actual_flags;
288
289
290     /* This thread simply waits for an event in a forever loop. */
291     while(1)
292     {
293
294         /* Increment the thread counter. */
295         thread_5_counter++;
296
297         /* Wait for event flag 0. */
298         status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
299                                &actual_flags, TX_WAIT_FOREVER);
300
301         /* Check status. */
302         if ((status != TX_SUCCESS) || (actual_flags != 0x1))
303            break;
304     }
305 }
306
307 void     thread_6_and_7_entry(ULONG thread_input)
308 {
309
310 UINT     status;
311
312
313     /* This function is executed from thread 6 and thread 7. As the loop
314         below shows, these function compete for ownership of mutex_0. */
315     while(1)
316     {
317
318         /* Increment the thread counter. */
319         if (thread_input == 6)
320            thread_6_counter++;
321         else
322            thread_7_counter++;
323
324         /* Get the mutex with suspension. */
325         status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);
326
327         /* Check status. */
328         if (status != TX_SUCCESS)
329            break;
330
331         /* Get the mutex again with suspension. This shows
332            that an owning thread may retrieve the mutex it
333            owns multiple times. */
334         status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);
335
336         /* Check status. */
337         if (status != TX_SUCCESS)
338             break;
339
340         /* Sleep for 2 ticks to hold the mutex. */
341         tx_thread_sleep(2);
342
343         /* Release the mutex. */
344         status = tx_mutex_put(&mutex_0);
345
346         /* Check status. */
347         if (status != TX_SUCCESS)
348            break;
349
350         /* Release the mutex again. This will actually
351            release ownership since it was obtained twice. */
352         status = tx_mutex_put(&mutex_0);
353
354         /* Check status. */
355         if (status != TX_SUCCESS)
356            break;
357     }
358 }
```