---
title: 챕터 3 - Azure RTOS NetX Duo MQTT 클라이언트 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 NetX Duo MQTT 클라이언트 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810711"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a><span data-ttu-id="5463c-103">챕터 3 - Azure RTOS NetX Duo MQTT 클라이언트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="5463c-103">Chapter 3 - Description of Azure RTOS NetX Duo MQTT client services</span></span>

<span data-ttu-id="5463c-104">이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX Duo MQTT 클라이언트 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-104">This chapter contains a description of all Azure RTOS NetX Duo MQTT client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="5463c-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="5463c-106">**nxd_mqtt_client_create** *Create MQTT 클라이언트 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="5463c-106">**nxd_mqtt_client_create** *Create MQTT client instance*</span></span>
- <span data-ttu-id="5463c-107">**nxd_mqtt_client_will_message_set** *will 메시지 설정*</span><span class="sxs-lookup"><span data-stu-id="5463c-107">**nxd_mqtt_client_will_message_set** *Set the will message*</span></span>
- <span data-ttu-id="5463c-108">**nxd_mqtt_client_client_login_set** *MQTT 클라이언트 사용자 이름 및 암호 설정*</span><span class="sxs-lookup"><span data-stu-id="5463c-108">**nxd_mqtt_client_client_login_set** *Set MQTT client login username and password*</span></span>
- <span data-ttu-id="5463c-109">**nxd_mqtt_client_connect** *MQTT 클라이언트를 broker에 연결*</span><span class="sxs-lookup"><span data-stu-id="5463c-109">**nxd_mqtt_client_connect** *Connect MQTT Client to the broker*</span></span>
- <span data-ttu-id="5463c-110">**nxd_mqtt_client_secure_connect** *TLS 보안을 사용하여 MQTT 클라이언트를 broker에 연결*</span><span class="sxs-lookup"><span data-stu-id="5463c-110">**nxd_mqtt_client_secure_connect** *Connect MQTT client to the broker with TLS security*</span></span>
- <span data-ttu-id="5463c-111">**nxd_mqtt_client_publish** *broker를 통해 메시지 게시*</span><span class="sxs-lookup"><span data-stu-id="5463c-111">**nxd_mqtt_client_publish** *Publish a message through the broker.*</span></span>
- <span data-ttu-id="5463c-112">**nxd_mqtt_client_subscribe** *토픽 구독*</span><span class="sxs-lookup"><span data-stu-id="5463c-112">**nxd_mqtt_client_subscribe** *Subscribe to a topic*</span></span>
- <span data-ttu-id="5463c-113">**nxd_mqtt_client_unsubscribe** *토픽 구독 취소*</span><span class="sxs-lookup"><span data-stu-id="5463c-113">**nxd_mqtt_client_unsubscribe** *Unsubscribe from a topic*</span></span>
- <span data-ttu-id="5463c-114">**nxd_mqtt_client_receive_notify_set** *MQTT 메시지 수신 알림 콜백 함수 설정*</span><span class="sxs-lookup"><span data-stu-id="5463c-114">**nxd_mqtt_client_receive_notify_set** *Set MQTT message receive notify callback function*</span></span>
- <span data-ttu-id="5463c-115">**nxd_mqtt_client_message_get** *broker에서 메시지 검색*</span><span class="sxs-lookup"><span data-stu-id="5463c-115">**nxd_mqtt_client_message_get** *Retrieve a message from the broker*</span></span>
- <span data-ttu-id="5463c-116">**nxd_mqtt_client_disconnect_notify_set** *MQTT 메시지 연결 해제 알림 콜백 함수 설정*</span><span class="sxs-lookup"><span data-stu-id="5463c-116">**nxd_mqtt_client_disconnect_notify_set** *Set MQTT message disconnect notify callback function*</span></span>
- <span data-ttu-id="5463c-117">**nxd_mqtt_client_disconnect** *broker에서 MQTT 클라이언트 연결 해제*</span><span class="sxs-lookup"><span data-stu-id="5463c-117">**nxd_mqtt_client_disconnect** *Disconnect MQTT client from the broker*</span></span>
- <span data-ttu-id="5463c-118">**nxd_mqtt_client_delete** *MQTT 클라이언트 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="5463c-118">**nxd_mqtt_client_delete** *Delete the MQTT client instance*</span></span>

## <a name="nxd_mqtt_client_create"></a><span data-ttu-id="5463c-119">nxd_mqtt_client_create</span><span class="sxs-lookup"><span data-stu-id="5463c-119">nxd_mqtt_client_create</span></span>

<span data-ttu-id="5463c-120">MQTT 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="5463c-120">Create MQTT Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-121">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-121">Prototype</span></span>

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="5463c-122">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-122">Description</span></span>

<span data-ttu-id="5463c-123">이 서비스는 지정된 IP 인스턴스에 MQTT 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-123">This service creates an MQTT Client instance on the specified IP instance.</span></span> <span data-ttu-id="5463c-124">*client_id* 문자열은 MQTT 연결 단계 중에 *클라이언트 식별자(ClientId)* 로 서버에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-124">The *client_id* string is passed to the server during MQTT connection phase as the *Client Identifier (ClientId)*.</span></span> <span data-ttu-id="5463c-125">또한 필요한 ThreadX 리소스(MQTT 클라이언트 작업 스레드, 뮤텍스, 이벤트 플래그 그룹 및 TCP 소켓)를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-125">It also creates the necessary ThreadX resources (MQTT Client task thread, mutex, event flag group, and TCP socket).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-126">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-126">Input Parameters</span></span>

- <span data-ttu-id="5463c-127">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-127">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5463c-128">**client_name** 클라이언트 이름 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-128">**client_name** Client name string.</span></span>
- <span data-ttu-id="5463c-129">**client_id** 연결 단계 중에 사용되는 클라이언트 ID 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-129">**client_id** Client ID string used during connection phase.</span></span> <span data-ttu-id="5463c-130">MQTT broker는 이 client_id를 사용하여 클라이언트를 고유하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-130">MQTT broker uses this client_id to uniquely identify a client.</span></span>
- <span data-ttu-id="5463c-131">**client_id_length** 클라이언트 ID 문자열의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-131">**client_id_length** Length of the client ID string, in bytes.</span></span>
- <span data-ttu-id="5463c-132">**ip_ptr** IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-132">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="5463c-133">**pool_ptr** MQTT 클라이언트가 작업에 사용하는 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-133">**pool_ptr** Pointer to a packet pool MQTT client uses for its operation.</span></span>
- <span data-ttu-id="5463c-134">**stack_ptr** MQTT 클라이언트 스레드의 스택 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-134">**stack_ptr** Stack area for the MQTT Client thread.</span></span>
- <span data-ttu-id="5463c-135">**stack_size** 스택 영역의 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-135">**stack_size** Size of the stack area, in bytes.</span></span>
- <span data-ttu-id="5463c-136">**mqtt_thread_priority** MQTT 스레드의 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-136">**mqtt_thread_priority** The priority of the MQTT Thread.</span></span>
- <span data-ttu-id="5463c-137">**memory_ptr** 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-137">**memory_ptr** Deprecated.</span></span> <span data-ttu-id="5463c-138">더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-138">Not used anymore.</span></span>
- <span data-ttu-id="5463c-139">**memory_size** 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-139">**memory_size** Deprecated.</span></span> <span data-ttu-id="5463c-140">더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-140">Not used anymore.</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-141">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-141">Return Values</span></span>

- <span data-ttu-id="5463c-142">**NXD_MQTT_SUCCESS** (0x00) MQTT 클라이언트를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-142">**NXD_MQTT_SUCCESS** (0x00) Successfully created MQTT client.</span></span>
- <span data-ttu-id="5463c-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류</span><span class="sxs-lookup"><span data-stu-id="5463c-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5463c-144">NX_PTR_ERROR (0x07) 잘못된 MQTT 컨트롤 블록, ip_ptr 또는 패킷 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-144">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer.</span></span>
- <span data-ttu-id="5463c-145">NXD_MQTT_INVALID_PARAMETER (0x10009) 잘못된 will 토픽 문자열, will_retrain_flag 또는 will_QoS 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-145">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-146">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-146">Allowed From</span></span>

<span data-ttu-id="5463c-147">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-148">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-148">Example</span></span>

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a><span data-ttu-id="5463c-149">nxd_mqtt_client_will_message_set</span><span class="sxs-lookup"><span data-stu-id="5463c-149">nxd_mqtt_client_will_message_set</span></span>

<span data-ttu-id="5463c-150">Will 메시지를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-150">Sets the Will message</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-151">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-151">Prototype</span></span>

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a><span data-ttu-id="5463c-152">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-152">Description</span></span>

<span data-ttu-id="5463c-153">이 서비스는 클라이언트가 서버에 연결하기 전에 선택적인 will 토픽과 will 메시지를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-153">This service sets the optional will topic and will message before the client connects to the server.</span></span> <span data-ttu-id="5463c-154">will 토픽은 UTF-8 인코딩 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-154">Will topic must be UTF-8 encoded string.</span></span>

<span data-ttu-id="5463c-155">설정된 경우, will 메시지는 CONNECT 메시지의 일부로 broker에게 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-155">The will message, if set, is transmitted to the broker as part of the CONNECT message.</span></span> <span data-ttu-id="5463c-156">따라서 will 메시지를 사용하려는 애플리케이션은 MQTT 연결을 설정하기 전에 이 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-156">Therefore application wishing to use will message must use this service before the MQTT connection is make.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-157">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-157">Input Parameters</span></span>

- <span data-ttu-id="5463c-158">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-158">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5463c-159">**will_topic** UTF-8로 인코딩된 will 토픽 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-159">**will_topic** UTF-8 encoded will topic string.</span></span> <span data-ttu-id="5463c-160">will 토픽이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-160">Will topic must be present.</span></span> <span data-ttu-id="5463c-161">호출자는 *nx_mqtt_client_connect* 를 호출할 때까지 will_topic 문자열을 유효하게 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-161">Caller must keep the will_topic string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="5463c-162">**will_topic_length** will 토픽 문자열의 바이트 수</span><span class="sxs-lookup"><span data-stu-id="5463c-162">**will_topic_length** Number of bytes in the will topic string</span></span>
- <span data-ttu-id="5463c-163">**will_message** 애플리케이션이 will 메시지를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-163">**will_message** Application defined will message.</span></span> <span data-ttu-id="5463c-164">will 메시지가 필요하지 않을 경우 애플리케이션은 이 필드를 *NX_NULL* 로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-164">If will message is not required, application can set this field to *NX_NULL.*</span></span>
- <span data-ttu-id="5463c-165">**will_message_length** will 메시지 문자열의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-165">**will_message_length** Number of bytes in the will message string.</span></span> <span data-ttu-id="5463c-166">will_message가 NULL로 설정된 경우 will_message_length를 0으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-166">If will_message is set to NULL, will_message_length must be set to 0.</span></span>
- <span data-ttu-id="5463c-167">**will_retain_flag** 서버가 will 메시지를 보존 메시지로 게시할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-167">**will_retain_flag** Whether the server publishes the will message as a retained message.</span></span> <span data-ttu-id="5463c-168">유효한 값은 *NX_TRUE* 또는 *NX_FALSE* 입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-168">Valid values are *NX_TRUE* or *NX_FALSE.*</span></span>
- <span data-ttu-id="5463c-169">**will_QoS** will 메시지를 보낼 때 서버에서 사용하는 QoS 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-169">**will_QoS** QoS value used by the server when sending will message.</span></span> <span data-ttu-id="5463c-170">유효한 값은 0 또는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-170">Valid values are 0 or 1.</span></span>  

### <a name="return-values"></a><span data-ttu-id="5463c-171">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-171">Return Values</span></span>

- <span data-ttu-id="5463c-172">**NXD_MQTT_SUCCESS** (0x00) will 메시지가 성공적으로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-172">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="5463c-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS 수준 2 메시지는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="5463c-174">NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-174">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="5463c-175">NXD_MQTT_INVALID_PARAMETER (0x10009) 잘못된 will 토픽 문자열, will_retrain_flag 또는 will_QoS 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-175">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-176">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-176">Allowed From</span></span>

<span data-ttu-id="5463c-177">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-178">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-178">Example</span></span>

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a><span data-ttu-id="5463c-179">nxd_mqtt_client_login_set</span><span class="sxs-lookup"><span data-stu-id="5463c-179">nxd_mqtt_client_login_set</span></span>

<span data-ttu-id="5463c-180">MQTT 클라이언트 로그인 사용자 이름 및 암호를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-180">Sets MQTT client login username and password</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-181">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-181">Prototype</span></span>

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a><span data-ttu-id="5463c-182">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-182">Description</span></span>

<span data-ttu-id="5463c-183">이 서비스는 로그인 인증 목적으로 MQTT 연결 단계에서 사용되는 사용자 이름과 암호를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-183">This service sets the username and password, which is used during MQTT connection phase for log in authentication purpose.</span></span>

<span data-ttu-id="5463c-184">사용자 이름 및 암호를 사용하는 MQTT 클라이언트 로그인은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-184">The MQTT client login with username and password is optional.</span></span> <span data-ttu-id="5463c-185">서버에 사용자 이름과 암호가 필요한 상황에서는 연결을 설정하기 전에 사용자 이름과 암호를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-185">In situations where the server requires a user name and password, the user name and password must be set before the connection is established.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-186">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-186">Input Parameters</span></span>

- <span data-ttu-id="5463c-187">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-187">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5463c-188">**username** UTF-8로 인코딩된 사용자 이름 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-188">**username** UTF-8 encoded user name string.</span></span> <span data-ttu-id="5463c-189">호출자는 *nx_mqtt_client_connect* 를 호출할 때까지 사용자 이름 문자열을 유효하게 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-189">Caller must keep the username string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="5463c-190">**username_length** 사용자 이름 문자열의 바이트 수</span><span class="sxs-lookup"><span data-stu-id="5463c-190">**username_length** Number of bytes in the username string</span></span>
- <span data-ttu-id="5463c-191">**password** 암호 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-191">**password** Password string.</span></span> <span data-ttu-id="5463c-192">암호가 필요하지 않은 경우에는 이 필드를 NX_NULL로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-192">If password is not required, this field may be set to NX_NULL.</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-193">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-193">Return Values</span></span>

- <span data-ttu-id="5463c-194">**NXD_MQTT_SUCCESS** (0x00) will 메시지가 성공적으로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-194">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="5463c-195">NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-195">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="5463c-196">NXD_MQTT_INVALID_PARAMETER (0x10009) 잘못된 사용자 이름 문자열 또는 암호 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-196">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid username string or the password string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-197">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-197">Allowed From</span></span>

<span data-ttu-id="5463c-198">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-199">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-199">Example</span></span>

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a><span data-ttu-id="5463c-200">nxd_mqtt_client_connect</span><span class="sxs-lookup"><span data-stu-id="5463c-200">nxd_mqtt_client_connect</span></span>

<span data-ttu-id="5463c-201">MQTT 클라이언트를 broker에 연결</span><span class="sxs-lookup"><span data-stu-id="5463c-201">Connect MQTT Client to the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-202">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-202">Prototype</span></span>

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="5463c-203">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-203">Description</span></span>

<span data-ttu-id="5463c-204">이 서비스는 broker에 대한 연결을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-204">This service initiates a connection to the broker.</span></span> <span data-ttu-id="5463c-205">먼저 TCP 소켓을 바인딩한 다음, TCP 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-205">First it binds a TCP socket, then makes a TCP connection.</span></span> <span data-ttu-id="5463c-206">이 작업이 성공했다고 가정하면 MQTT 연결 유지 기능이 활성화된 경우 타이머가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-206">Assuming that succeeds, it creates a timer if the MQTT keep alive feature is enabled.</span></span> <span data-ttu-id="5463c-207">그런 다음, MQTT 서버(broker)와 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-207">Then it connects with the MQTT server (broker).</span></span>

<span data-ttu-id="5463c-208">이 서비스는 TLS 보호 없이 MQTT 연결을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-208">Note that this service creates an MQTT connection with no TLS protection.</span></span> <span data-ttu-id="5463c-209">보안 MQTT 연결을 생성하기 위해 애플리케이션은 ***nxd_mqtt_client_secure_connect()*** 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-209">To create a secure MQTT connection, the application shall use the service ***nxd_mqtt_client_secure_connect().***</span></span>

<span data-ttu-id="5463c-210">연결 시 클라이언트가 *clean_session* 을 NX_FALSE로 설정하면 클라이언트는 아직 승인되지 않은 저장된 모든 메시지를 재전송합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-210">Upon the connection, if the client sets the *clean_session* to NX_FALSE, the client will retransmit any messages stored that have not been acknowledged yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-211">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-211">Input Parameters</span></span>

- <span data-ttu-id="5463c-212">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-212">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5463c-213">**server_ip** broker IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-213">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="5463c-214">**server_port** broker 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-214">**server_port** Broker port number.</span></span> <span data-ttu-id="5463c-215">MQTT의 기본 포트는 **_NXD_MQTT_PORT_**(1883)으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-215">The default port for MQTT is defined as **_NXD_MQTT_PORT_** (1883).</span></span>
- <span data-ttu-id="5463c-216">**keep_alive** 세션 중에 사용할 연결 유지 값(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-216">**keep_alive** The keep alive value, in seconds, to be used during the session.</span></span> <span data-ttu-id="5463c-217">이 값은 broker가 이 클라이언트의 시간을 초과하기 전에 broker로 전송되는 두 MQTT 제어 메시지 사이의 최대 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-217">The value indicates the maximum time between two MQTT control messages being sent to the broker before the broker times out this client.</span></span> <span data-ttu-id="5463c-218">값 0은 연결 유지 기능을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-218">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="5463c-219">**clean_session** 서버가 이 세션을 새로 시작할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-219">**clean_session** Whether the server shall start this session clean.</span></span> <span data-ttu-id="5463c-220">유효한 옵션은 **_NX_TRUE_ *_ 또는 _* _NX_FALSE_** 입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-220">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="5463c-221">**wait_option** 연결 대기 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-221">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-222">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-222">Return Values</span></span>

- <span data-ttu-id="5463c-223">**NXD_MQTT_SUCCESS** (0x00) 성공한 MQTT 연결</span><span class="sxs-lookup"><span data-stu-id="5463c-223">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT connection</span></span>
- <span data-ttu-id="5463c-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) 클라이언트가 broker에 이미 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="5463c-225">**NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT 뮤텍스를 가져오지 못함</span><span class="sxs-lookup"><span data-stu-id="5463c-225">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="5463c-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류</span><span class="sxs-lookup"><span data-stu-id="5463c-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5463c-227">**NXD_MQTT_CONNECT_FAILURE** (0x10005) broker에 연결하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-227">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="5463c-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) broker로 메시지를 보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="5463c-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) 서버가 오류로 응답</span><span class="sxs-lookup"><span data-stu-id="5463c-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error</span></span>
- <span data-ttu-id="5463c-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) 서버 응답 코드</span><span class="sxs-lookup"><span data-stu-id="5463c-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="5463c-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) 서버 응답 코드</span><span class="sxs-lookup"><span data-stu-id="5463c-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="5463c-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) 서버 응답 코드</span><span class="sxs-lookup"><span data-stu-id="5463c-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="5463c-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) 서버 응답 코드</span><span class="sxs-lookup"><span data-stu-id="5463c-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="5463c-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) 서버 응답 코드</span><span class="sxs-lookup"><span data-stu-id="5463c-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="5463c-235">NX_PTR_ERROR (0x07) 잘못된 MQTT 컨트롤 블록, ip_ptr 또는 패킷 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-235">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-236">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-236">Allowed From</span></span>

<span data-ttu-id="5463c-237">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-238">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-238">Example</span></span>

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a><span data-ttu-id="5463c-239">nxd_mqtt_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="5463c-239">nxd_mqtt_client_secure_connect</span></span>

<span data-ttu-id="5463c-240">TLS 보안을 사용하여 MQTT 클라이언트를 broker에 연결</span><span class="sxs-lookup"><span data-stu-id="5463c-240">Connect MQTT client to the broker with TLS security</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-241">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-241">Prototype</span></span>

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="5463c-242">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-242">Description</span></span>

<span data-ttu-id="5463c-243">이 서비스는 연결이 TCP 대신 TLS 계층을 통과한다는 점을 제외하면 ***nxd_mqtt_client_connect*** 와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-243">This service is identical to ***nxd_mqtt_client_connect*** except that the connection goes through TLS layer instead of TCP.</span></span> <span data-ttu-id="5463c-244">따라서 클라이언트와 broker 간의 통신은 보안이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-244">Therefore, communication between the client and the broker is secured.</span></span>

<span data-ttu-id="5463c-245">사용자 정의된 *tls_setup* 은 MQTT 클라이언트 연결을 설정하기 전에 MQTT 클라이언트가 사용하는 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-245">The user-defined *tls_setup* is a callback function that the MQTT client uses prior to making a MQTT client connection.</span></span> <span data-ttu-id="5463c-246">애플리케이션은 NetX Secure TLS를 초기화하고, 보안 매개 변수를 구성하고, TLS 핸드셰이크 중에 사용할 관련 인증서를 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-246">The application shall initialize NetX Secure TLS, configure security parameters, and load relevant certificates to be used during TLS handshake.</span></span> <span data-ttu-id="5463c-247">실제 TLS 핸드셰이크는 브로커의 MQTT TLS 포트(기본 TCP 포트 8883)에서 TCP 연결이 설정된 후에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-247">The actual TLS handshake happens after a TCP connection is established on the broker's MQTT TLS port (default TCP port 8883).</span></span> <span data-ttu-id="5463c-248">TLS 핸드셰이크가 성공하면 MQTT CONNECT 제어 패킷이 TLS를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-248">Once the TLS handshake is successful, the MQTT CONNECT control packet is sent via TLS.</span></span>

<span data-ttu-id="5463c-249">보안 연결을 설정하려면 NetX Secure TLS 라이브러리를 사용할 수 있어야 하며, NetX Duo MQTT 클라이언트는 ***NX_SECURE_ENABLE*** 이 정의된 상태로 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-249">To make secure connections, the NetX Secure TLS library must be available, and the NetX Duo MQTT client must be built with ***NX_SECURE_ENABLE*** defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-250">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-250">Input Parameters</span></span>

- <span data-ttu-id="5463c-251">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-251">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5463c-252">**server_ip** broker IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-252">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="5463c-253">**server_port** broker 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-253">**server_port** Broker port number.</span></span> <span data-ttu-id="5463c-254">MQTT의 기본 포트는 **_NXD_MQTT_TLS_PORT_**(8883)으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-254">The default port for MQTT isdefined as **_NXD_MQTT_TLS_PORT_** (8883).</span></span>
- <span data-ttu-id="5463c-255">**tls_setup** 사용자가 제공한 TLS 설정 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-255">**tls_setup** User-provided TLS Setup callback function.</span></span> <span data-ttu-id="5463c-256">이 콜백 함수는 TLS 클라이언트 연결 매개 변수를 설정하기 위해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-256">This callback function is invoked to set up TLS client connection parameters.</span></span>
- <span data-ttu-id="5463c-257">**keep_alive** 세션 중에 사용할 연결 유지 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-257">**keep_alive** The keep-alive value to be used during the session.</span></span> <span data-ttu-id="5463c-258">값 0은 연결 유지 기능을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-258">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="5463c-259">**clean_session** 서버가 이 세션을 새로 시작할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-259">**clean_session** Whether or not the server shall start this session clean.</span></span> <span data-ttu-id="5463c-260">유효한 옵션은 **_NX_TRUE_ *_ 또는 _* _NX_FALSE_** 입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-260">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="5463c-261">**wait_option** 연결 대기 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-261">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-262">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-262">Return Values</span></span>

- <span data-ttu-id="5463c-263">**NXD_MQTT_SUCCESS** (0x00) TLS를 통해 MQTT 클라이언트 연결이 성공적으로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-263">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT client connection established via TLS.</span></span>
- <span data-ttu-id="5463c-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) 클라이언트가 broker에 이미 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="5463c-265">**NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT 뮤텍스를 가져오지 못함</span><span class="sxs-lookup"><span data-stu-id="5463c-265">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="5463c-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류</span><span class="sxs-lookup"><span data-stu-id="5463c-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5463c-267">**NXD_MQTT_CONNECT_FAILURE** (0x10005) broker에 연결하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-267">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="5463c-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) broker로 메시지를 보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="5463c-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) 서버가 오류 메시지로 응답했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error message.</span></span>
- <span data-ttu-id="5463c-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) 서버 응답 코드</span><span class="sxs-lookup"><span data-stu-id="5463c-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="5463c-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) 서버 응답 코드</span><span class="sxs-lookup"><span data-stu-id="5463c-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="5463c-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) 서버 응답 코드</span><span class="sxs-lookup"><span data-stu-id="5463c-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="5463c-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) 서버 응답 코드</span><span class="sxs-lookup"><span data-stu-id="5463c-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="5463c-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) 서버 응답 코드</span><span class="sxs-lookup"><span data-stu-id="5463c-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="5463c-275">NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록 또는 서버 주소 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-275">NX_PTR_ERROR (0x07) Invalid MQTT control block or sever address structure.</span></span>
- <span data-ttu-id="5463c-276">NX_INVALID_PORT (0x46) 서버 포트는 0일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-276">NX_INVALID_PORT (0x46) Server port cannot be 0.</span></span>
- <span data-ttu-id="5463c-277">NXD_MQTT_INVALID_PARAMETER (0x10009) 입력 매개 변수 오류</span><span class="sxs-lookup"><span data-stu-id="5463c-277">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>
- <span data-ttu-id="5463c-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT 스레드가 아직 실행되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT Thread has not started running yet.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-279">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-279">Allowed From</span></span>

<span data-ttu-id="5463c-280">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-281">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-281">Example</span></span>

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a><span data-ttu-id="5463c-282">nxd_mqtt_client_publish</span><span class="sxs-lookup"><span data-stu-id="5463c-282">nxd_mqtt_client_publish</span></span>

<span data-ttu-id="5463c-283">broker를 통해 메시지 게시</span><span class="sxs-lookup"><span data-stu-id="5463c-283">Publish a message through the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-284">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-284">Prototype</span></span>

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a><span data-ttu-id="5463c-285">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-285">Description</span></span>

<span data-ttu-id="5463c-286">이 서비스는 broker를 통해 메시지를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-286">This service publishes a message through the broker.</span></span> <span data-ttu-id="5463c-287">QoS 수준 2 메시지 게시는 아직 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-287">Publishing QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-288">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-288">Input Parameters</span></span>

- <span data-ttu-id="5463c-289">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-289">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5463c-290">**topic_name** 게시할 토픽입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-290">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="5463c-291">**topic_name_length** 토픽의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-291">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="5463c-292">**message** 메시지 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-292">**message** Pointer to the message buffer.</span></span>
- <span data-ttu-id="5463c-293">**message_length** 메시지의 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-293">**message_length** Size of the message, in bytes</span></span>
- <span data-ttu-id="5463c-294">**retain** broker가 메시지를 보존할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-294">**retain** Determines if the broker shall retain the message.</span></span>
- <span data-ttu-id="5463c-295">**QoS** 바람직한 QoS 값은 0 또는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-295">**QoS** The desired QoS value: 0 or 1.</span></span>
- <span data-ttu-id="5463c-296">**timeout** 시간 제한 값</span><span class="sxs-lookup"><span data-stu-id="5463c-296">**timeout** Timeout value</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-297">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-297">Return Values</span></span>

- <span data-ttu-id="5463c-298">**NXD_MQTT_SUCCESS** (0x00) MQTT 클라이언트 만들기 성공</span><span class="sxs-lookup"><span data-stu-id="5463c-298">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT Client create</span></span>
- <span data-ttu-id="5463c-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error.</span></span>
- <span data-ttu-id="5463c-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) 패킷 풀에서 패킷을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) Failed to obtain packet from the packet pool.</span></span>
- <span data-ttu-id="5463c-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) broker와 통신하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Failed to communication with the broker.</span></span>
- <span data-ttu-id="5463c-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS 수준 2 메시지는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="5463c-303">NX_PTR_ERROR (0x07) 잘못된 MQTT 컨트롤 블록, ip_ptr 또는 패킷 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-303">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="5463c-304">NXD_MQTT_INVALID_PARAMETER (0x10009) 입력 매개 변수 오류</span><span class="sxs-lookup"><span data-stu-id="5463c-304">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-305">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-305">Allowed From</span></span>

<span data-ttu-id="5463c-306">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-307">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-307">Example</span></span>

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a><span data-ttu-id="5463c-308">nxd_mqtt_client_subscribe</span><span class="sxs-lookup"><span data-stu-id="5463c-308">nxd_mqtt_client_subscribe</span></span>

<span data-ttu-id="5463c-309">토픽 구독</span><span class="sxs-lookup"><span data-stu-id="5463c-309">Subscribe to a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-310">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-310">Prototype</span></span>

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a><span data-ttu-id="5463c-311">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-311">Description</span></span>

<span data-ttu-id="5463c-312">이 서비스는 특정 토픽을 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-312">This service subscribes to a specific topic.</span></span> <span data-ttu-id="5463c-313">QoS 수준 2 메시지 구독은 아직 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-313">Subscribing to QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-314">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-314">Input Parameters</span></span>

- <span data-ttu-id="5463c-315">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-315">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5463c-316">**topic_name** 게시할 토픽입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-316">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="5463c-317">**topic_name_length** 토픽의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-317">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="5463c-318">**QoS** 바람직한 QoS 수준은 0 또는 1입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-318">**QoS The desired QoS level:** 0 or 1.</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-319">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-319">Return Values</span></span>

- <span data-ttu-id="5463c-320">**NXD_MQTT_SUCCESS** (0x00) 토픽을 성공적으로 구독했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-320">**NXD_MQTT_SUCCESS** (0x00) Successfully subscribed to the topic.</span></span>
- <span data-ttu-id="5463c-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) 클라이언트가 broker에 연결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="5463c-322">**NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT 뮤텍스를 가져오지 못함</span><span class="sxs-lookup"><span data-stu-id="5463c-322">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span>
- <span data-ttu-id="5463c-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류</span><span class="sxs-lookup"><span data-stu-id="5463c-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5463c-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) broker로 메시지를 보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="5463c-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS 수준 2 메시지는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2messages are not supported.</span></span>
- <span data-ttu-id="5463c-326">NX_PTR_ERROR (0x07) 잘못된 MQTT 컨트롤 블록, ip_ptr 또는 패킷 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-326">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="5463c-327">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name이 설정되지 않았거나, topic_name_length가 0이거나, QoS 값이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-327">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero, or QoS is value is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-328">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-328">Allowed From</span></span>

<span data-ttu-id="5463c-329">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-330">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-330">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a><span data-ttu-id="5463c-331">nxd_mqtt_client_unsubscribe</span><span class="sxs-lookup"><span data-stu-id="5463c-331">nxd_mqtt_client_unsubscribe</span></span>

<span data-ttu-id="5463c-332">토픽 구독 취소</span><span class="sxs-lookup"><span data-stu-id="5463c-332">Unsubscribe from a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-333">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-333">Prototype</span></span>

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a><span data-ttu-id="5463c-334">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-334">Description</span></span>

<span data-ttu-id="5463c-335">이 서비스는 토픽 구독을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-335">This service unsubscribes from a topic.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-336">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-336">Input Parameters</span></span>

- <span data-ttu-id="5463c-337">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-337">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5463c-338">**topic_name** 구독을 취소할 토픽입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-338">**topic_name** Topic to unsubscribe from.</span></span>
- <span data-ttu-id="5463c-339">**topic_name_length** 토픽의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-339">**topic_name_length** Length of the topic, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-340">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-340">Return Values</span></span>

- <span data-ttu-id="5463c-341">**NXD_MQTT_SUCCESS** (0x00) 토픽을 성공적으로 구독 취소했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-341">**NXD_MQTT_SUCCESS** (0x00) Successfully unsubscribed from the topic.</span></span>
- <span data-ttu-id="5463c-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) 클라이언트가 broker에 연결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="5463c-343">**NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT 뮤텍스를 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-343">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="5463c-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류</span><span class="sxs-lookup"><span data-stu-id="5463c-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5463c-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) broker로 메시지를 보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="5463c-346">NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-346">NX_PTR_ERROR (0x07) Invalid MQTT control block pointer</span></span>
- <span data-ttu-id="5463c-347">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name이 설정되지 않았거나 topic_name_length가 0입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-347">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-348">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-348">Allowed From</span></span>

<span data-ttu-id="5463c-349">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-350">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-350">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a><span data-ttu-id="5463c-351">nxd_mqtt_client_receive_notify_set</span><span class="sxs-lookup"><span data-stu-id="5463c-351">nxd_mqtt_client_receive_notify_set</span></span>

<span data-ttu-id="5463c-352">MQTT 메시지 수신 알림 콜백 함수 설정</span><span class="sxs-lookup"><span data-stu-id="5463c-352">Set MQTT message receive notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-353">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-353">Prototype</span></span>

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a><span data-ttu-id="5463c-354">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-354">Description</span></span>

<span data-ttu-id="5463c-355">이 서비스는 MQTT 클라이언트를 사용하여 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-355">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="5463c-356">broker가 게시한 메시지를 수신하면 MQTT 클라이언트는 메시지를 수신 큐에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-356">Upon receiving a message published by the broker, MQTT client stores the message in the receive queue.</span></span> <span data-ttu-id="5463c-357">콜백 함수가 설정된 경우 콜백 함수가 호출되어 애플리케이션에 메시지를 검색할 준비가 되었음을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-357">If the callback function is set, the callback function is invoked to notify the application that a message is ready to be retrieved.</span></span> <span data-ttu-id="5463c-358">수신 알림 함수는 포인터를 MQTT 클라이언트 제어 블록으로 가져가며, 수신 큐에서 사용할 수 있는 메시지 수를 나타내는 *message_count* 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-358">The receive notify function takes a pointer to the MQTT client control block, and a *message_count* indicating the number of messages available in the receive queue.</span></span> <span data-ttu-id="5463c-359">새 메시지가 간격에 도착했을 수 있으므로 수신 알림과 애플리케이션이 이러한 메시지를 검색하는 시점 사이에 번호가 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-359">Note that the number may change between the receive notification and when the application retrieves these messages, as new messages may have arrived in the interval.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-360">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-360">Input Parameters</span></span>

- <span data-ttu-id="5463c-361">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-361">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5463c-362">**receive_notify** 메시지 수신 시 호출되는 사용자 제공 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-362">**receive_notify** User supplied callback function to be invoked on receiving a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-363">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-363">Return Values</span></span>

- <span data-ttu-id="5463c-364">**NXD_MQTT_SUCCESS** (0x00) 수신 알림 함수를 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-364">**NXD_MQTT_SUCCESS** (0x00) Successfully set the receive notify function.</span></span>
- <span data-ttu-id="5463c-365">NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-365">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-366">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-366">Allowed From</span></span>

<span data-ttu-id="5463c-367">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-368">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-368">Example</span></span>

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a><span data-ttu-id="5463c-369">nxd_mqtt_client_message_get</span><span class="sxs-lookup"><span data-stu-id="5463c-369">nxd_mqtt_client_message_get</span></span>

<span data-ttu-id="5463c-370">broker에서 메시지 검색</span><span class="sxs-lookup"><span data-stu-id="5463c-370">Retrieve a message from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-371">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-371">Prototype</span></span>

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a><span data-ttu-id="5463c-372">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-372">Description</span></span>

<span data-ttu-id="5463c-373">이 서비스는 broker가 게시한 메시지를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-373">This service retrieves a message published by the broker.</span></span> <span data-ttu-id="5463c-374">들어오는 모든 메시지는 수신 큐에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-374">All incoming messages are stored in the receive queue.</span></span> <span data-ttu-id="5463c-375">애플리케이션은 이 서비스를 사용하여 이러한 메시지를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-375">The application uses this service to retrieve these messages.</span></span> <span data-ttu-id="5463c-376">이 호출은 차단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-376">This call is non-blocking.</span></span> <span data-ttu-id="5463c-377">수신 큐가 비어 있는 경우 이 서비스는 \***NXD_MQTT_NO_MESSAGE** _을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-377">If the receive queue is empty, this service returns \***NXD_MQTT_NO_MESSAGE** _.</span></span> <span data-ttu-id="5463c-378">들어오는 메시지에 대한 알림을 받으려는 애플리케이션은 _ *_nxd_mqtt_client_receive_notify_set_*\* 서비스를 호출하여 수신 콜백 함수를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-378">An application wishing to be notified of incoming message can call the service _ *_nxd_mqtt_client_receive_notify_set_*\* to register a receive callback function.</span></span>

<span data-ttu-id="5463c-379">호출자는 토픽 문자열과 메시지 본문에 대한 메모리 공간을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-379">The caller needs to provide memory space for the topic string and the message body.</span></span> <span data-ttu-id="5463c-380">이러한 두 버퍼의 크기는 *topic_buffer_size* 및 *message_buffer_size* 를 사용하여 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-380">The sizes of these two buffers are passed in using *topic_buffer_size* and *message_buffer_size*.</span></span> <span data-ttu-id="5463c-381">토픽 문자열과 메시지 본문의 실제 바이트 수는 *actual_topic_length* 및 *actual_message_length* 로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-381">The actual number of bytes in the topic string and the message body are returned in *actual_topic_length* and *actual_message_length*.</span></span> <span data-ttu-id="5463c-382">토픽 길이 또는 메시지 길이가 제공된 버퍼 공간보다 큰 경우 이 서비스는 오류 코드 *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-382">If topic length or massage length is greater than the buffer space provided, this service returns error code *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span></span>

<span data-ttu-id="5463c-383">애플리케이션이 더 큰 버퍼를 할당하고 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-383">The application shall allocate a bigger buffer and try again.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-384">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-384">Input Parameters</span></span>

- <span data-ttu-id="5463c-385">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-385">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5463c-386">**topic_buffer** 토픽 문자열이 복사되는 메모리 위치에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-386">**topic_buffer** Pointer to the memory location where the topic string is copied into.</span></span>
- <span data-ttu-id="5463c-387">**topic_buffer_size** 토픽 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-387">**topic_buffer_size** Size of the topic buffer.</span></span>
- <span data-ttu-id="5463c-388">**actual_topic_length** 실제 토픽 길이가 반환되는 메모리 위치에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-388">**actual_topic_length** Pointer to the memory location where the actual topic length is returned.</span></span>
- <span data-ttu-id="5463c-389">**topic_buffer** 토픽 문자열이 복사되는 메모리 위치에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-389">**message_buffer** Pointer to the memory location where the message string is copied into.</span></span>
- <span data-ttu-id="5463c-390">**message_buffer_size** 메시지 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-390">**message_buffer_size** Size of the message buffer.</span></span>
- <span data-ttu-id="5463c-391">**actual_topic_length** 메시지 길이가 반환되는 메모리 위치에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-391">**actual_message_length** Pointer to the memory location where the message length is returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-392">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-392">Return Values</span></span>

- <span data-ttu-id="5463c-393">**NXD_MQTT_SUCCESS** (0x00) 메시지를 성공적으로 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-393">**NXD_MQTT_SUCCESS** (0x00) Successfully retrieved message.</span></span>
- <span data-ttu-id="5463c-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) 내부 논리 오류</span><span class="sxs-lookup"><span data-stu-id="5463c-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5463c-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) 수신 큐가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) The receive queue is empty.</span></span>
- <span data-ttu-id="5463c-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) 토픽 버퍼 또는 메시지 버퍼가 너무 작아서 토픽 또는 메시지에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) Topic buffer or message buffer is too small for the topic or the message.</span></span>
- <span data-ttu-id="5463c-397">NX_PTR_ERROR (0x07) 잘못된 MQTT 컨트롤 블록, ip_ptr 또는 패킷 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-397">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="5463c-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer 또는 topic_buffer 포인터가 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer or topic_buffer pointer is NULL</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-399">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-399">Allowed From</span></span>

<span data-ttu-id="5463c-400">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-401">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-401">Example</span></span>

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a><span data-ttu-id="5463c-402">nxd_mqtt_client_disconnect_notify_set</span><span class="sxs-lookup"><span data-stu-id="5463c-402">nxd_mqtt_client_disconnect_notify_set</span></span>

<span data-ttu-id="5463c-403">MQTT 메시지 연결 해제 알림 콜백 함수 설정</span><span class="sxs-lookup"><span data-stu-id="5463c-403">Set MQTT message disconnect notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-404">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-404">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a><span data-ttu-id="5463c-405">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-405">Description</span></span>

<span data-ttu-id="5463c-406">이 서비스는 MQTT 클라이언트를 사용하여 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-406">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="5463c-407">MQTT가 broker와의 연결이 끊어진 것을 감지하면 이 알림 함수를 호출하여 애플리케이션에 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-407">When MQTT detects the connection to the broker is lost, it calls this notify function to alert the application.</span></span> <span data-ttu-id="5463c-408">따라서 애플리케이션은 이 콜백 함수를 사용하여 끊어진 연결을 감지하고 broker에 대한 연결을 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-408">Therefore, the application can use this callback function to detect a lost connection, and to be able to re-establish connection to the broker.</span></span>

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a><span data-ttu-id="5463c-409">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-409">Input Parameters</span></span>

- <span data-ttu-id="5463c-410">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-410">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5463c-411">**disconnect_notify** MQTT가 브로커와의 연결이 끊어진 것을 감지했을 때 호출할 사용자 제공 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-411">**disconnect_notify** User supplied callback function to be invoked when MQTT detects the connection to the broker is lost.</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-412">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-412">Return Values</span></span>

- <span data-ttu-id="5463c-413">**NXD_MQTT_SUCCESS** (0x00) 연결 해제 알림 함수를 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-413">**NXD_MQTT_SUCCESS** (0x00) Successfully set the disconnect notify function.</span></span>
- <span data-ttu-id="5463c-414">NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-414">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-415">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-415">Allowed From</span></span>

<span data-ttu-id="5463c-416">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-417">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-417">Example</span></span>

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a><span data-ttu-id="5463c-418">nxd_mqtt_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="5463c-418">nxd_mqtt_client_disconnect</span></span>

<span data-ttu-id="5463c-419">broker에서 MQTT 클라이언트 연결 해제</span><span class="sxs-lookup"><span data-stu-id="5463c-419">Disconnect MQTT client from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-420">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-420">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="5463c-421">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-421">Description</span></span>

<span data-ttu-id="5463c-422">이 서비스는 broker에서 클라이언트 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-422">This service disconnects the client from the broker.</span></span> <span data-ttu-id="5463c-423">수신 큐의 메시지가 릴리스됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-423">Note that messages on the receive queue are released.</span></span> <span data-ttu-id="5463c-424">전송 큐에 QoS 1이 있는 메시지는 릴리스되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-424">Messages with QoS 1 in the transmit queue are not released.</span></span> <span data-ttu-id="5463c-425">클라이언트가 서버에 다시 연결되면 클라이언트가 *clean_session* 플래그를 ***NX_TRUE*** 로 설정하여 서버에 다시 연결하지 않는 한 QoS 1 메시지를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-425">After the client reconnects to the server, QoS 1 messages can be processed, unless the client reconnects to the server with *clean_session* flag set to ***NX_TRUE***.</span></span>

<span data-ttu-id="5463c-426">TLS 보안 보호를 사용하여 연결한 경우 이 서비스는 TCP 연결을 해제하기 전에 TLS 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-426">If the connection was made with TLS security protection, this service will close the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="5463c-427">실제 TCP 소켓 연결 해제 호출에는 NXD_MQTT_SOCKET_TIMEOUT(타이머 틱)에 의해 정의된 대기 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-427">The actual TCP socket disconnect call has a wait option defined by NXD_MQTT_SOCKET_TIMEOUT (timer ticks).</span></span> <span data-ttu-id="5463c-428">기본값은 NX_WAIT_FOREVER입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-428">The default value is NX_WAIT_FOREVER.</span></span> <span data-ttu-id="5463c-429">네트워크 연결이 끊어지거나 서버가 응답하지 않는 경우 무기한 중단을 방지하려면 이 옵션을 유한 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-429">To avoid indefinite suspension in the event that the network connection is lost or the server is not responding, set this option to a finite value.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-430">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-430">Input Parameters</span></span>

- <span data-ttu-id="5463c-431">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-431">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-432">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-432">Return Values</span></span>

- <span data-ttu-id="5463c-433">**NXD_MQTT_SUCCESS** (0x00) 브로커와의 연결이 성공적으로 해제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-433">**NXD_MQTT_SUCCESS** (0x00) Successfully disconnected from broker</span></span>
- <span data-ttu-id="5463c-434">**NXD_MQTT_MUTEX_FAILURE** (0x10003) MQTT 뮤텍스를 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-434">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="5463c-435">NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록</span><span class="sxs-lookup"><span data-stu-id="5463c-435">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-436">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-436">Allowed From</span></span>

<span data-ttu-id="5463c-437">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-438">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-438">Example</span></span>

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a><span data-ttu-id="5463c-439">nxd_mqtt_client_delete</span><span class="sxs-lookup"><span data-stu-id="5463c-439">nxd_mqtt_client_delete</span></span>

<span data-ttu-id="5463c-440">MQTT 클라이언트 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="5463c-440">Delete the MQTT client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5463c-441">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5463c-441">Prototype</span></span>

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="5463c-442">설명</span><span class="sxs-lookup"><span data-stu-id="5463c-442">Description</span></span>

<span data-ttu-id="5463c-443">이 서비스는 MQTT 클라이언트 인스턴스를 삭제하고 내부 리소스를 릴리스합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-443">This service deletes the MQTT client instance and releases internal resources.</span></span> <span data-ttu-id="5463c-444">이 서비스는 클라이언트가 여전히 연결되어 있는 경우 자동으로 broker와 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-444">This service automatically disconnects the client from the broker if it is still connected.</span></span> <span data-ttu-id="5463c-445">아직 전송되지 않았거나 확인되지 않은 메시지가 릴리스됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-445">Messages not yet transmitted or not been acknowledged are released.</span></span> <span data-ttu-id="5463c-446">애플리케이션에서 수신되었지만 검색되지 않은 메시지도 릴리스됩니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-446">Messages received but not retrieved by the application are also released.</span></span>

<span data-ttu-id="5463c-447">TLS 보안 보호를 사용하여 연결한 경우 이 서비스는 TCP 연결을 해제하기 전에 TLS 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-447">If the connection was made with TLS security protection, this service closes the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="5463c-448">클라이언트가 삭제된 후 MQTT 서비스를 사용하려는 애플리케이션은 새 인스턴스를 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-448">After the client is deleted, an application wishing to use MQTT service needs to create a new instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5463c-449">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5463c-449">Input Parameters</span></span>

- <span data-ttu-id="5463c-450">**client_ptr** MQTT 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-450">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5463c-451">반환 값</span><span class="sxs-lookup"><span data-stu-id="5463c-451">Return Values</span></span>

- <span data-ttu-id="5463c-452">**NXD_MQTT_SUCCESS** (0x00) MQTT 클라이언트를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="5463c-452">**NXD_MQTT_SUCCESS** (0x00) Successfully deleted MQTT client.</span></span>
- <span data-ttu-id="5463c-453">NX_PTR_ERROR (0x07) 잘못된 MQTT 제어 블록</span><span class="sxs-lookup"><span data-stu-id="5463c-453">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5463c-454">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5463c-454">Allowed From</span></span>

<span data-ttu-id="5463c-455">스레드</span><span class="sxs-lookup"><span data-stu-id="5463c-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5463c-456">예제</span><span class="sxs-lookup"><span data-stu-id="5463c-456">Example</span></span>

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
