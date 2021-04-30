---
title: 2장 - Azure RTOS NetX Duo MQTT 클라이언트 설치 및 사용
description: 이 장에서는 NetX Duo MQTT 클라이언트 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cde19a0e84f369f1199ea4027fa09e6bd038e837
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810723"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a><span data-ttu-id="f2c2c-103">2장 - Azure RTOS NetX Duo MQTT 클라이언트 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="f2c2c-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo MQTT client</span></span>

<span data-ttu-id="f2c2c-104">이 장에서는 Azure RTOS NetX Duo MQTT 클라이언트 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo MQTT client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="f2c2c-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="f2c2c-105">Product Distribution</span></span>

<span data-ttu-id="f2c2c-106">NetX Duo용 MQTT 에이전트는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-106">MQTT Client for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="f2c2c-107">패키지에는 다음과 같이 2개의 원본 파일, 하나의 포함 파일 및 이 문서를 포함하는 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-107">The package includes two source files, one include file, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="f2c2c-108">**nxd_mqtt_client.h** NetX Duo의 MQTT 클라이언트에 대한 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="f2c2c-108">**nxd_mqtt_client.h** Header file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="f2c2c-109">**nxd_mqtt_client.c** NetX Duo의 MQTT 클라이언트에 대한 C 원본 파일</span><span class="sxs-lookup"><span data-stu-id="f2c2c-109">**nxd_mqtt_client.c** C Source file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="f2c2c-110">**nxd_mqtt_client.pdf** NetX Duo의 MQTT 클라이언트에 대한 설명</span><span class="sxs-lookup"><span data-stu-id="f2c2c-110">**nxd_mqtt_client.pdf** Description of MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="f2c2c-111">**demo_mqtt_client.c** NetX Duo MQTT 데모</span><span class="sxs-lookup"><span data-stu-id="f2c2c-111">**demo_mqtt_client.c** NetX Duo MQTT demonstration</span></span>

## <a name="mqtt-client-installation"></a><span data-ttu-id="f2c2c-112">MQTT 클라이언트 설치</span><span class="sxs-lookup"><span data-stu-id="f2c2c-112">MQTT Client Installation</span></span>

<span data-ttu-id="f2c2c-113">NetX Duo용 MQTT 클라이언트를 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-113">In order to use MQTT Client for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="f2c2c-114">예를 들어 NetX Duo가 " *\threadx\arm7\green*" 디렉터리에 설치된 경우 NetX Duo MQTT 클라이언트에 대한 *nxd_mqtt_client.h* 및 *nxd_mqtt_client.c* 를 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-114">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_mqtt_client.h* and *nxd_mqtt_client.c* for NetX Duo MQTT Client need to be copied into this directory.</span></span>

## <a name="using-mqtt-client"></a><span data-ttu-id="f2c2c-115">MQTT 클라이언트 사용</span><span class="sxs-lookup"><span data-stu-id="f2c2c-115">Using MQTT Client</span></span>

<span data-ttu-id="f2c2c-116">NetX Duo에 MQTT 클라이언트를 사용하는 것은 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-116">Using MQTT Client for NetX Duo is easy.</span></span> <span data-ttu-id="f2c2c-117">기본적으로 ThreadX 및 NetX Duo를 각각 사용하기 위해서는 애플리케이션 코드에는 *tx_api.h* 및 *nx_api.h* 가 포함된 후 *nxd_mqtt_client.h* 가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-117">Basically, the application code must include *nxd_mqtt_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX, and NetX Duo, respectively.</span></span> <span data-ttu-id="f2c2c-118">MQTT 클라이언트 헤더 파일이 포함되면 애플리케이션 코드는 이 가이드의 뒷부분에서 설명하는 MQTT 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-118">Once the MQTT Client header files are included, the application code is then able to use the MQTT services described later in this guide.</span></span> <span data-ttu-id="f2c2c-119">애플리케이션은 빌드 프로세스에 *nxd_mqtt_client.c* 도 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-119">The application must also include *nxd_mqtt_client.c* in the build process.</span></span> <span data-ttu-id="f2c2c-120">이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 해당 개체 형식을 애플리케이션의 파일에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="f2c2c-121">이는 NetX Duo MQTT 클라이언트를 사용하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-121">This is all that is required to use NetX Duo MQTT Client.</span></span>

## <a name="using-mqtt-client-with-netx-secure-tls"></a><span data-ttu-id="f2c2c-122">NetX Secure TLS에서 MQTT 클라이언트 사용</span><span class="sxs-lookup"><span data-stu-id="f2c2c-122">Using MQTT Client with NetX Secure TLS</span></span>

<span data-ttu-id="f2c2c-123">NetX Secure TLS 모듈에서 MQTT 클라이언트를 사용하려면 애플리케이션에 NetX Secure TLS 모듈이 설치되어 있어야 하고, *nx_secure_tls_api.h* 및 *nx_crypto.h* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-123">To use MQTT client with NetX Secure TLS module, application must have NetX Secure TLS module installed, and include *nx_secure_tls_api.h* and *nx_crypto.h*.</span></span> <span data-ttu-id="f2c2c-124">***NX_SECURE_ENABLE*** 정의된 기호를 사용하여 MQTT 라이브러리를 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-124">The MQTT library must be built with the symbol ***NX_SECURE_ENABLE*** defined.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="f2c2c-125">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="f2c2c-125">Configuration Options</span></span>

<span data-ttu-id="f2c2c-126">NetX Duo용 MQTT 클라이언트를 빌드하기 위한 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-126">There are several configuration options for building MQTT client for NetX Duo.</span></span> <span data-ttu-id="f2c2c-127">다음은 각각에 대해 자세히 설명된 모든 옵션의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-127">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="f2c2c-128">기본값이 나열되지만 *nxd_mqtt_client.h.* 를 포함하기 전에 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-128">The default values are listed, but can be redefined prior to inclusion of *nxd_mqtt_client.h.*</span></span>

- <span data-ttu-id="f2c2c-129">**NX_DISABLE_ERROR_CHECKING**: 정의된 이 옵션은 기본 MQTT 클라이언트 오류 검사를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-129">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic MQTT client error checking.</span></span> <span data-ttu-id="f2c2c-130">일반적으로 애플리케이션이 디버깅된 후에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-130">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="f2c2c-131">**NX_SECURE_ENABLE**: 정의된 MQTT 클라이언트는 TLS 지원으로 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-131">**NX_SECURE_ENABLE**: Defined, MQTT Client is built with TLS support.</span></span>
<span data-ttu-id="f2c2c-132">이 기호를 정의하려면 NetX Secure TLS 모듈이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-132">Defining this symbol requires NetX Secure TLS module to be installed.</span></span>
<span data-ttu-id="f2c2c-133">*NX_SECURE_ENABLE* 은 기본적으로 사용하도록 설정되어 있지 않습니다.\*\*</span><span class="sxs-lookup"><span data-stu-id="f2c2c-133">*NX_SECURE_ENABLE* is not enabled by default.\*\*</span></span>
- <span data-ttu-id="f2c2c-134">**NXD_MQTT_REQUIRE_TLS**: 정의된 애플리케이션은 TLS를 사용하여 MQTT broker에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-134">**NXD_MQTT_REQUIRE_TLS**: Defined, application must use TLS to connect to MQTT broker.</span></span> <span data-ttu-id="f2c2c-135">이 기능을 사용하려면 *NX_SECURE_ENABLE* 을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-135">This feature requires *NX_SECURE_ENABLE* defined.</span></span> <span data-ttu-id="f2c2c-136">기본적으로 이 기호는 정의되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-136">By default, this symbol is not defined.</span></span>
- <span data-ttu-id="f2c2c-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="f2c2c-138">**NXD_MQTT_MAX_MESSAGE_LENGTH**: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-138">**NXD_MQTT_MAX_MESSAGE_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="f2c2c-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE**: MQTT 타이머 전송률(ThreadX 타이머 틱)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE**: Defines the MQTT timer rate, in ThreadX timer ticks.</span></span> <span data-ttu-id="f2c2c-140">이 타이머는 마지막 MQTT 제어 메시지를 보낸 이후 시간을 추적하는 데 사용되며, 연결 유지 시간이 만료되기 전에 MQTT PINGREQ 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-140">This timer is used to keep track of the time since last MQTT control message was sent, and sends out an MQTT PINGREQ message before the keep-alive time expires.</span></span> <span data-ttu-id="f2c2c-141">클라이언트에서 연결 유지 타이머 값을 설정하여 broker에 연결하면 이 타이머가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-141">This timer is activated if the client connects to the broker with a keep-alive timer value set.</span></span> <span data-ttu-id="f2c2c-142">기본값은 1초 타이머인 TX_TIMER_TICKS_PER_SECOND입니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-142">The default value is TX_TIMER_TICKS_PER_SECOND, which is a one-second timer.</span></span>
- <span data-ttu-id="f2c2c-143">**NXD_MQTT_PING_TIMEOUT_DELAY**: MQTT 클라이언트에서 MQTT PINGREQ를 전송하고 나면 broker에서 PINGRESP를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-143">**NXD_MQTT_PING_TIMEOUT_DELAY**: Defines the time the MQTT client waits for PINGRESP from the broker after it sends out MQTT PINGREQ.</span></span> <span data-ttu-id="f2c2c-144">이 시간 제한 지연 후에 PINGRESP가 수신되지 않으면 클라이언트는 broker를 응답성이 아닌 것으로 처리하고 브로커에서 자체의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-144">If no PINGRESP is received after this timeout delay, the client treats the broker as non-responsive and disconnects itself from the broker.</span></span> <span data-ttu-id="f2c2c-145">기본 PING 시간 제한 지연은 1초인 TX_TIMER_TICKS_PER_SECOND입니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-145">The default PING timeout delay is TX_TIMER_TICKS_PER_SECOND, which is one second.</span></span>
- <span data-ttu-id="f2c2c-146">**NXD_MQTT_SOCKET_TIMEOUT**: 타이머 틱의 MQTT 서버에서 연결을 끊을 때 TCP 소켓 연결 끊기 호출의 제한 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-146">**NXD_MQTT_SOCKET_TIMEOUT**: Defines the time out in the TCP socket disconnect call when disconnecting from the MQTT server in timer ticks.</span></span> <span data-ttu-id="f2c2c-147">기본값은 NX_WAIT_FOREVER입니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-147">The default value is NX_WAIT_FOREVER.</span></span>

## <a name="sample-mqtt-program"></a><span data-ttu-id="f2c2c-148">샘플 MQTT 프로그램</span><span class="sxs-lookup"><span data-stu-id="f2c2c-148">Sample MQTT program</span></span>

<span data-ttu-id="f2c2c-149">다음 프로그램은 간단한 MQTT 애플리케이션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-149">The following program illustrates a simple MQTT application.</span></span> <span data-ttu-id="f2c2c-150">편의상 반환 코드는 성공한 것으로 간주되므로 추가 오류 검사가 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2c2c-150">For simplicity, the return codes are assumed to be successful, therefore no further error checking is done.</span></span>

```c
#define LOCAL_SERVER_ADDRESS (IP_ADDRESS(192, 168, 1, 81))

/*******************************************************/
/* IOT MQTT Client Example                             */
/*******************************************************/
#define DEMO_STACK_SIZE 2048
#define CLIENT_ID_STRING "mytestclient"
#define MQTT_CLIENT_STACK_SIZE 4096
#define STRLEN(p) (sizeof(p) - 1)

/* Declare the MQTT thread stack space. */
static ULONG mqtt_client_stack[MQTT_CLIENT_STACK_SIZE / sizeof(ULONG)];

/* Declare the MQTT client control block. */
static NXD_MQTT_CLIENT mqtt_client;

/* Define the symbol for signaling a received message. */

/* Define the test threads. */

#define TOPIC_NAME "topic"

#define MESSAGE_STRING "This is a message. "

/* Define the priority of the MQTT internal thread. */
#define MQTT_THREAD_PRIORTY 2

/* Define the MQTT keep alive timer for 5 minutes */
#define MQTT_KEEP_ALIVE_TIMER 300
#define QOS0 0
#define QOS1 1

/* Declare event flag, which is used in this demo. */
TX_EVENT_FLAGS_GROUP mqtt_app_flag;
#define DEMO_MESSAGE_EVENT 1
#define DEMO_ALL_EVENTS 3

/* Declare buffers to hold message and topic. */
static UCHAR message_buffer[NXD_MQTT_MAX_MESSAGE_LENGTH];
static UCHAR topic_buffer[NXD_MQTT_MAX_TOPIC_NAME_LENGTH];

/* Declare the disconnect notify function. */
static VOID my_disconnect_func(NXD_MQTT_CLIENT *client_ptr)
{
    printf("client disconnected from server\n");
}

static VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr, UINT number_of_messages)
{
    tx_event_flags_set(&mqtt_app_flag, DEMO_MESSAGE_EVENT, TX_OR);
    return;
}

static ULONG error_counter;
void demo_mqtt_client_local(NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr)
{
    UINT status;
    NXD_ADDRESS server_ip;
    ULONG events;
    UINT topic_length, message_length;

    /* Create MQTT client instance. */
    nxd_mqtt_client_create(&mqtt_client, "my_client",
        CLIENT_ID_STRING, STRLEN(CLIENT_ID_STRING), ip_ptr, pool_ptr,
        (VOID*)mqtt_client_stack, sizeof(mqtt_client_stack),
        MQTT_THREAD_PRIORTY, NX_NULL, 0);

    /* Register the disconnect notification function. */
    nxd_mqtt_client_disconnect_notify_set(&mqtt_client, my_disconnect_func);

    /* Create an event flag for this demo. */
    status = tx_event_flags_create(&mqtt_app_flag, "my app event");
    server_ip.nxd_ip_version = 4;
    server_ip.nxd_ip_address.v4 = LOCAL_SERVER_ADDRESS;

    /* Start the connection to the server. */
    nxd_mqtt_client_connect(&mqtt_client, &server_ip, NXD_MQTT_PORT, 
        MQTT_KEEP_ALIVE_TIMER, 0, NX_WAIT_FOREVER);

    /* Subscribe to the topic with QoS level 0. */
    nxd_mqtt_client_subscribe(&mqtt_client, TOPIC_NAME, STRLEN(TOPIC_NAME),
        QOS0);

    /* Set the receive notify function. */
    nxd_mqtt_client_receive_notify_set(&mqtt_client, my_notify_func);

    /* Publish a message with QoS Level 1. */
    nxd_mqtt_client_publish(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME), (CHAR*)MESSAGE_STRING, 
        STRLEN(MESSAGE_STRING), 0, QOS1, NX_WAIT_FOREVER);

    /* Now wait for the broker to publish the message. */
    tx_event_flags_get(&mqtt_app_flag, DEMO_ALL_EVENTS,
        TX_OR_CLEAR, &events, TX_WAIT_FOREVER);

    if(events & DEMO_MESSAGE_EVENT)
    {
        nxd_mqtt_client_message_get(&mqtt_client, topic_buffer,
            sizeof(topic_buffer), &topic_length, message_buffer,
            sizeof(message_buffer), &message_length);

        topic_buffer[topic_length] = 0;

        message_buffer[message_length] = 0;

        printf("topic = %s, message = %s\n", topic_buffer, message_buffer);
    }

    /* Now unsubscribe the topic. */
    nxd_mqtt_client_unsubscribe(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME));

    /* Disconnect from the broker. */
    nxd_mqtt_client_disconnect(&mqtt_client);

    /* Delete the client instance, release all the resources. */
    nxd_mqtt_client_delete(&mqtt_client);
    return;
}
```
