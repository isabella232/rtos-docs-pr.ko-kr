---
title: 1장 - Azure RTOS NetX Duo MQTT 소개
description: NetX Duo MQTT 클라이언트 패키지를 사용하려면 NetX Duo(버전 5.10 이상)를 설치하여 올바르게 구성하고, IP 인스턴스를 만들어야 합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e13b997f987e2fd82569bcb1904218908313d70
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810728"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mqtt"></a><span data-ttu-id="636bd-103">1장 - Azure RTOS NetX Duo MQTT 소개</span><span class="sxs-lookup"><span data-stu-id="636bd-103">Chapter 1 - Introduction to Azure RTOS NetX Duo MQTT</span></span>

## <a name="netx-duo-mqtt-requirements"></a><span data-ttu-id="636bd-104">NetX Duo MQTT 요구 사항</span><span class="sxs-lookup"><span data-stu-id="636bd-104">NetX Duo MQTT Requirements</span></span>

<span data-ttu-id="636bd-105">Azure RTOS NetX Duo MQTT 클라이언트 패키지를 사용하려면 NetX Duo(버전 5.10 이상)를 설치하여 올바르게 구성하고, IP 인스턴스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-105">The Azure RTOS NetX Duo MQTT client package requires that NetX Duo (version 5.10 or later) be installed, properly configured, and the IP instance has been created.</span></span> <span data-ttu-id="636bd-106">시스템에서 TCP 모듈을 사용하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-106">The TCP module must be enabled in the system.</span></span> <span data-ttu-id="636bd-107">또한 TLS 보안이 필요한 경우 broker에서 요구하는 보안 매개 변수에 따라 NetX Secure TLS 모듈을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-107">In addition, if TLS security is required, the NetX Secure TLS module needs to be configured according to the security parameter required by the broker.</span></span>

## <a name="netx-duo-mqtt-specification"></a><span data-ttu-id="636bd-108">NetX Duo MQTT 사양</span><span class="sxs-lookup"><span data-stu-id="636bd-108">NetX Duo MQTT Specification</span></span>

<span data-ttu-id="636bd-109">NetX Duo MQTT 클라이언트 구현은 OASIS MQTT 버전 3.1.1 2014년 10월 29<sup>일</sup>을 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-109">NetX Duo MQTT client implement is compliant with OASIS MQTT Version 3.1.1 Oct 29<sup>th</sup> 2014.</span></span> <span data-ttu-id="636bd-110">이 사양은 다음에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-110">The specification can be found at:</span></span>

- [http://mqtt.org/](http://mqtt.org/)

## <a name="netx-duo-mqtt-basic-operation"></a><span data-ttu-id="636bd-111">NetX Duo MQTT 기본 작업</span><span class="sxs-lookup"><span data-stu-id="636bd-111">NetX Duo MQTT Basic Operation</span></span>

<span data-ttu-id="636bd-112">MQTT(메시지 큐 원격 분석 전송)는 게시자-구독자 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-112">MQTT (Message Queue Telemetry Transport) is based on publisher-subscriber model.</span></span> <span data-ttu-id="636bd-113">클라이언트는 broker를 통해 다른 클라이언트에 정보를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-113">A client can publish information to other clients through a broker.</span></span> <span data-ttu-id="636bd-114">토픽에 관심이 있는 클라이언트는 broker를 통해 토픽을 구독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-114">A client, if interested in a topic, can subscribe to the topic through the broker.</span></span> <span data-ttu-id="636bd-115">Broker는 게시된 메시지를, 토픽을 구독하는 클라이언트에 배달합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-115">A broker is responsible for delivering published messages to its clients who subscribe to the topic.</span></span> <span data-ttu-id="636bd-116">이 게시자-구독자 모델에서는 여러 클라이언트가 동일한 토픽으로 데이터를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-116">In this publisher-subscriber model, multiple clients may publish data with the same topic.</span></span> <span data-ttu-id="636bd-117">클라이언트가 동일한 토픽을 구독하는 경우, 게시한 메시지를 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-117">A client will receive a message it publishes if the client subscribes to the same topic.</span></span>

<span data-ttu-id="636bd-118">사용 사례에 따라 클라이언트는 메시지를 게시할 때 다음과 같이 세 가지 QoS 수준 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-118">Depending on the use case, a client may choose one of the 3 QoS levels when publishing a message:</span></span>

- <span data-ttu-id="636bd-119">**QoS 0**: 메시지가 최대 한 번 배달됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-119">**QoS 0**: The message is delivered at most once.</span></span> <span data-ttu-id="636bd-120">QoS 0으로 전송된 메시지는 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-120">Messages sent with QoS 0 may be lost.</span></span>
- <span data-ttu-id="636bd-121">**QoS 1**: 메시지가 한 번 이상 배달됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-121">**QoS 1**: The message is delivered at least once.</span></span> <span data-ttu-id="636bd-122">QoS 1로 전송된 메시지는 두 번 이상 배달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-122">Messages sent with QoS 1 may be delivered more than once.</span></span>
- <span data-ttu-id="636bd-123">**QoS 2**: 메시지가 정확히 한 번 배달됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-123">**QoS 2**: The message is delivered exactly once.</span></span> <span data-ttu-id="636bd-124">QoS 2로 보낸 메시지는 중복 없이 배달이 보장됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-124">Messages sent with QoS 2 is guaranteed to be delivered, with no duplication.</span></span>

> [!NOTE]
> <span data-ttu-id="636bd-125">이 MQTT 클라이언트 구현은 QoS 수준 2 메시지를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-125">This implementation of MQTT client does not support QoS level 2 messages.</span></span>

<span data-ttu-id="636bd-126">QoS 1 및 QoS 2는 배달이 보장되므로 broker는 각 클라이언트에 전송된 QoS 1 및 QoS 2 메시지의 상태를 계속 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-126">Since QoS 1 and QoS 2 are guaranteed to be delivered, the broker keeps track the state of QoS 1 and QoS 2 messages sent to each client.</span></span> <span data-ttu-id="636bd-127">이는 QoS1 또는 QoS 2 메시지를 기대하는 클라이언트에서 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-127">This is particularly important for clients that expect QoS1 or QoS 2 messages.</span></span> <span data-ttu-id="636bd-128">클라이언트를 broker에서 끊을 수 있습니다(예: 클라이언트 다시 부팅, 통신 링크의 일시적 손실 등의 경우).</span><span class="sxs-lookup"><span data-stu-id="636bd-128">The client may be disconnected from the broker (for example when the client reboots, or the communication link is temporarily lost).</span></span> <span data-ttu-id="636bd-129">Broker는 클라이언트가 broker에 다시 연결되면 메시지를 배달할 수 있도록 QoS 1 및 QoS 2 메시지를 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-129">The broker must store QoS 1 and QoS 2 messages so the messages can be delivered later once the client is reconnected to the broker.</span></span> <span data-ttu-id="636bd-130">그러나 다시 연결한 후 클라이언트가 broker에서 오래된 메시지를 수신하지 않도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-130">However, the client may choose not to receive any stale messages from the broker after reconnection.</span></span> <span data-ttu-id="636bd-131">클라이언트는 \***NX_TRUE** _로 설정된 *clean_session* 플래그를 시작하여 이렇게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-131">The client can do so by initiating the connection with the *clean_session* flag set to \***NX_TRUE** _.</span></span> <span data-ttu-id="636bd-132">이 경우 MQTT CONNECT 메시지를 받으면 broker는 이 클라이언트와 연결된 모든 세션 정보를 삭제해야 합니다. 여기에는 배달되지 않거나 확인되지 않은 QoS 1 또는 QoS 2가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-132">In this case, upon receiving the MQTT CONNECT message, the broker shall discard any session information associated with this client, including undelivered or unconfirmed QoS 1 or QoS 2 messages.</span></span> <span data-ttu-id="636bd-133">_clean_session\* 플래그가 \***NX_FALSE**_ 이면 서버는 QoS 1 및 QoS 2 메시지를 다시 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-133">If the _clean_session\* flag is to \***NX_FALSE**_, the server shall resend the QoS 1 and QoS 2 messages.</span></span> <span data-ttu-id="636bd-134">_clean_session\*이 ***NX_TRUE*** 로 설정된 경우 MQTT 클라이언트는 미승인 메시지도 다시 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-134">The MQTT Client also resends any un-acknowledged messages if _clean_session\* is set to \***NX_TRUE\*.**</span></span> <span data-ttu-id="636bd-135">이 승인은 TCP 계층 ACK처럼 발생하지만 그와는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-135">This acknowledgment is different from the TCP layer ACK, although that happens as well.</span></span> <span data-ttu-id="636bd-136">MQTT 클라이언트는 broker에 승인을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-136">The MQTT client sends an acknowledgment to the broker.</span></span>

<span data-ttu-id="636bd-137">애플리케이션은 \***nxd_mqtt_client_create()** _를 호출하여 MQTT클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-137">An application creates an MQTT client instance by calling \***nxd_mqtt_client_create()** _.</span></span> <span data-ttu-id="636bd-138">클라이언트를 만든 후에는 애플리케이션에서 _*_nxd_mqtt_client_connect()_*_ 를 호출하여 broker에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-138">Once the client is created, the application can connect to the broker by calling _*_nxd_mqtt_client_connect()_*_.</span></span> <span data-ttu-id="636bd-139">Broker에 연결한 후 클라이언트는 _*_nxd_mqtt_client_subscribe()_*_ 를 호출하여 토픽을 구독하거나, _\*_nxd_mqtt_client_publish()_ \*\*를 호출하여 토픽을 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-139">After connecting to the broker, the client can subscribe to a topic by calling _*_nxd_mqtt_client_subscribe()_*_, or publish a topic by calling _\*_nxd_mqtt_client_publish()_\*\*.</span></span>

<span data-ttu-id="636bd-140">들어오는 MQTT 메시지는 MQTT 클라이언트 인스턴스의 수신 큐에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-140">Incoming MQTT messages are stored in the receive queue in the MQTT client instance.</span></span> <span data-ttu-id="636bd-141">애플리케이션은 ***nxd_mqtt_client_message_get()*** 을 호출하여 이러한 메시지를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-141">Application retrieves these message by calling ***nxd_mqtt_client_message_get()***.</span></span> <span data-ttu-id="636bd-142">수신 큐에 메시지가 있으면 큐의 첫 번째 메시지(예: 가장 오래된 메시지)를 호출자에게 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-142">If there are messages in the receive queue, the first message (e.g. the oldest) from the queue is returned to the caller.</span></span> <span data-ttu-id="636bd-143">메시지의 토픽 문자열도 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-143">The topic string from the message is also returned.</span></span>

> [!NOTE]
> <span data-ttu-id="636bd-144">MQTT 클라이언트 수신 큐가 비어 있는 경우 \***nxd_mqtt_client_message_get()** _ 함수가 차단하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-144">The function \***nxd_mqtt_client_message_get()** _ does not block if the MQTT client receive queue is empty.</span></span> <span data-ttu-id="636bd-145">이 함수는 반환 코드 _\*_NXD_MQTT_NO_MESSAGE_\*\*를 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-145">The function returns immediately with the return code _\*_NXD_MQTT_NO_MESSAGE_\*\*.</span></span> <span data-ttu-id="636bd-146">애플리케이션은 이 반환 값을 오류가 아니라, 수신 큐가 비어 있음을 나타내는 표시로 취급해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-146">The application shall treat this return value as an indication that the receive queue is empty, not an error.</span></span>

<span data-ttu-id="636bd-147">들어오는 메시지에 대한 수신 큐 폴링을 방지하기 위해 애플리케이션은 ***nxd_mqtt_client_recieve_notify_set()*** 을 호출하여 MQTT 클라이언트에 콜백 함수를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-147">To avoid polling the receive queue for incoming messages, the application can register a callback function with the MQTT client by calling ***nxd_mqtt_client_recieve_notify_set()***.</span></span> <span data-ttu-id="636bd-148">콜백 함수는 다음과 같이 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-148">The callback function is declared as:</span></span>

```c
VOID (*receive_notify_callback)(NXD_MQTT_CLIENT *client_ptr, 
    UINT message_count);
```

<span data-ttu-id="636bd-149">함수가 설정된 경우 MQTT 클라이언트는 broker에서 메시지를 받을 때 콜백 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-149">As the MQTT client receives messages from the broker, it invokes the callback function if the function is set.</span></span> <span data-ttu-id="636bd-150">콜백 함수는 포인터를 클라이언트 제어 블록과 메시지 수 값에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-150">The callback function passes the pointer to the client control block and a message count value.</span></span> <span data-ttu-id="636bd-151">메시지 수 값은 수신 큐에 있는 MQTT 메시지의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-151">The message count value indicates the number of MQTT messages in the receive queue.</span></span> <span data-ttu-id="636bd-152">이 콜백 함수는 MQTT 클라이언트 스레드 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-152">Note that this callback function executes in the MQTT client thread context.</span></span> <span data-ttu-id="636bd-153">따라서 콜백 함수는 MQTT 클라이언트 스레드를 차단할 수 있는 프로시저를 실행해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-153">Therefore, the callback function should not execute any procedures that may block the MQTT client thread.</span></span> <span data-ttu-id="636bd-154">콜백 함수는 메시지를 검색하기 위해 ***nxd_mqtt_client_message_get()*** 을 호출하는 애플리케이션 스레드를 트리거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-154">The callback function should trigger the application thread to call ***nxd_mqtt_client_message_get()*** to retrieve the messages.</span></span>

<span data-ttu-id="636bd-155">MQTT 클라이언트 서비스의 연결을 해제하고 종료하려면 애플리케이션이 ***nxd_mqtt_client_disconnect()** _ 및 _*_nxd_mqtt_client_delete()_\*_ 를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-155">To disconnect and terminate the MQTT client service, the application shall use the service ***nxd_mqtt_client_disconnect()** _ and _*_nxd_mqtt_client_delete()._\*_</span></span> <span data-ttu-id="636bd-156">_*_nxd_mqtt_client_disconnect()_*_ 를 호출하면 broker에 대한 TCP 연결이 끊깁니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-156">Calling _*_nxd_mqtt_client_disconnect()_*_ simply disconnects the TCP connection to the broker.</span></span> <span data-ttu-id="636bd-157">이미 수신되어 수신 큐에 저장된 메시지를 릴리스합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-157">It releases messages already received and stored in the receive queue.</span></span> <span data-ttu-id="636bd-158">그러나 전송 큐의 QoS 수준 1 메시지는 릴리스하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-158">However, it does not release QoS level 1 messages in the transmit queue.</span></span> <span data-ttu-id="636bd-159">_*_clean_session_*_ 플래그가 _ \*_NX_FALSE_\*\*로 설정되었다면 QoS 수준 1 메시지는 연결 시 다시 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-159">QoS level 1 messages are retransmitted upon connection, assuming the _*_clean_session_*_ flag is set to _ *_NX_FALSE._*\*</span></span>

<span data-ttu-id="636bd-160">Broker는 클라이언트와의 연결을 끊을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-160">The broker may also disconnect from the client.</span></span> <span data-ttu-id="636bd-161">클라이언트와 broker 간의 TCP 연결이 종료되면 연결 끊기 알림 기능을 통해 애플리케이션에 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-161">When the TCP connection between the client and the broker is terminated, the application can be notified by the disconnect notify function.</span></span> <span data-ttu-id="636bd-162">알림 메커니즘을 사용하기 위해 애플리케이션은 ***nxd_mqtt_client_disconnect_notify_set*** 을 호출하여 연결 끊기 알림 함수를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-162">To use the notification mechanism, application installs the disconnect notify function by calling \***nxd_mqtt_client_disconnect_notify_set\*.**</span></span> <span data-ttu-id="636bd-163">TCP 연결 끊기가 관찰되고 MQTT 세션이 만들어지면 알림 함수가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-163">Once a TCP disconnect is observed and the MQTT session has been created, the notification function is invoked.</span></span>

<span data-ttu-id="636bd-164">***Nxd_mqtt_client_delete()*** 를 호출하면 전송 큐와 수신 큐의 모든 메시지 블록이 릴리스됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-164">Calling ***nxd_mqtt_client_delete()*** releases all message blocks in the transmit queue and the receive queue.</span></span> <span data-ttu-id="636bd-165">미승인 QoS 수준 1 메시지도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-165">Unacknowledged QoS level 1 messages are also deleted.</span></span>

## <a name="secure-mqtt-connection"></a><span data-ttu-id="636bd-166">보안 MQTT 연결</span><span class="sxs-lookup"><span data-stu-id="636bd-166">Secure MQTT Connection</span></span>

<span data-ttu-id="636bd-167">MQTT 클라이언트는 NetX Secure TLS 모듈을 사용하여 broker에 대한 보안 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-167">The MQTT client makes a secure connection to the broker using the NetX Secure TLS module.</span></span> <span data-ttu-id="636bd-168">TLS 보안에 대한 MQTT의 기본 포트 번호는 8883으로, ***NXD_MQTT_TLS_PORT*** 에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-168">The default port number for MQTT with TLS security is 8883, defined in ***NXD_MQTT_TLS_PORT***.</span></span>

<span data-ttu-id="636bd-169">Broker에 대한 보안 MQTT 연결을 만들려면, 먼저 TCP 연결 설정 후 TLS 세션을 협상해야 MQTT CONNECT 메시지를 broker에 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-169">To create a secure MQTT connection to the broker, a TLS session needs to be negotiated after a TCP connection is established, before MQTT CONNECT messages can be sent to the broker.</span></span> <span data-ttu-id="636bd-170">TLS 세션 설정은 ***nxd_mqtt_client_secure_connect()*** 를 호출하고 사용자 정의 TLS 설정 콜백 함수를 전달하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-170">The TLS session set up is accomplished by calling ***nxd_mqtt_client_secure_connect()*** and passing in a user-defined TLS setup callback function.</span></span> <span data-ttu-id="636bd-171">MQTT 연결 단계에서는 TCP 연결이 설정되면 클라이언트가 TLS 설정 콜백 함수를 호출하여 적절한 TLS 핸드셰이크 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-171">During the MQTT connection phase, once the TCP connection is established, the client invokes the TLS setup callback function to start a proper TLS handshake process.</span></span> <span data-ttu-id="636bd-172">TLS 세션이 설정되면 클라이언트는 보안 채널을 통해 MQTT CONNECT 메시지를 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-172">After the TLS session is established, the client continues the MQTT CONNECT message over the secure channel.</span></span>

<span data-ttu-id="636bd-173">사용자 정의 콜백 함수는 5개의 입력 값을 사용하며 다음과 같이 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-173">The user defined callback function takes five input values and is declared as:</span></span>

```c
UINT tls_Setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_cerfiticate);
```

<span data-ttu-id="636bd-174">입력 매개 변수 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-174">Below is a description of the input parameters:</span></span>

- <span data-ttu-id="636bd-175">**client_ptr**: MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-175">**client_ptr**: Pointer to the MQTT client control block.</span></span>
- <span data-ttu-id="636bd-176">**session_ptr**: TLS 세션 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-176">**session_ptr**: Pointer to the TLS session control block.</span></span>
- <span data-ttu-id="636bd-177">**certificate_ptr**: 인증서 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-177">**certificate_ptr**: Pointer to the certificate control block.</span></span> <span data-ttu-id="636bd-178">설정 함수는 이 인증서를 Broker에 보내기 전에 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-178">The setup function configures this certificate before sending it to the broker.</span></span>
- <span data-ttu-id="636bd-179">**trusted_certificate_ptr**: 신뢰할 수 있는 인증서에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-179">**trusted_certificate_ptr**: Pointer to the trusted certificate.</span></span> <span data-ttu-id="636bd-180">TLS 설정 함수는 서버 인증을 위해 신뢰할 수 있는 인증서를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-180">TLS setup function configures the trusted certificate to authenticate the server.</span></span>

<span data-ttu-id="636bd-181">TLS 설정 함수에서는 애플리케이션이 TLS 세션을 만들고 올바른 인증서를 통한 세션 구성을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-181">In the TLS setup function, the application is responsible for creating a TLS session, and configuring the session with a proper certificate.</span></span> <span data-ttu-id="636bd-182">다음 의사 코드는 일반적인 TLS 세션 시작 절차를 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-182">The following pseudo code outlines a typical TLS session start up procedure.</span></span> <span data-ttu-id="636bd-183">TLS API 사용에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="636bd-183">The reader is referred to the NetX Secure TLS User Guide for details on using TLS APIs.</span></span>

<span data-ttu-id="636bd-184">다음은 TLS 설정 콜백의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-184">Below is an example TLS setup callback:</span></span>

```c
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_pt
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certrifcate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate_ptr)
{
    /* Initialize TLS module */
    nx_secure_tls_initialize();

    /* Create a TLS session */
    nx_secure_tls_session_create(session_ptr, …);

    /* Need to allocate space for the certificate coming in from the broker. */
    memset(certificate_ptr), 0, sizeof(NX_SECURE_TLS_CERTIFICATE));

    nx_secure_tls_remote_certificate_allocate(session_ptr, certificate_ptr);

    /* Add a CA Certificate to our trusted store for verifying incomingserver certificates. */
    nx_secure_tls_certificate_initialize(
        trusted_certificate_ptr,
        ca_cert_der,
        ca_cert_der_len, NULL, 0);
    nx_secure_tls_trusted_certificate_add(session_ptr,
        trusted_certificate));
}
```

## <a name="known-limitations-of-the-netx-duo-mqtt-client"></a><span data-ttu-id="636bd-185">NetX Duo MQTT 클라이언트의 알려진 제한 사항</span><span class="sxs-lookup"><span data-stu-id="636bd-185">Known Limitations of the NetX Duo MQTT Client</span></span>

- <span data-ttu-id="636bd-186">NetX Duo MQTT는 QoS 수준 2 메시지의 보내기 또는 받기를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-186">NetX Duo MQTT does not support sending or receiving QoS level 2 messages.</span></span>
- <span data-ttu-id="636bd-187">NetX Duo MQTT는 체인 연결된 패킷을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="636bd-187">NetX Duo MQTT does not support chained-packets.</span></span>
