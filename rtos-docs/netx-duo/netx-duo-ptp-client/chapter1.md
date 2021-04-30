---
title: 1장 - Azure RTOS NetX Duo PTP 클라이언트 소개
description: 이 장에서는 Azure RTOS NetX Duo PTP 클라이언트를 소개합니다.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5beec64bd6d74e3bed06be15255d6bd4a940ba64
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810621"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a><span data-ttu-id="f19ca-103">1장 - Azure RTOS NetX Duo PTP 클라이언트 소개</span><span class="sxs-lookup"><span data-stu-id="f19ca-103">Chapter 1 - Introduction to Azure RTOS NetX Duo PTP Client</span></span>

<span data-ttu-id="f19ca-104">Azure RTOS NetX Duo PTP는 PTP(Precision Time Protocol, 정밀 시각 프로토콜) 버전 2, IEEE 1588-2008의 클라이언트 부분을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-104">The Azure RTOS NetX Duo PTP implements the client part of the Precision Time Protocol (PTP) version 2, IEEE 1588-2008.</span></span> <span data-ttu-id="f19ca-105">IPv4 또는 IPv6 멀티 캐스트 패킷을 통해 서로 통신하여 로컬 네트워크의 MCU 간에 클록을 동기화하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-105">It is used to synchronize clocks among MCUs on the local network by communicating each other via IPv4 or IPv6 multicast packets.</span></span>

## <a name="netx-duo-ptp-client-setup"></a><span data-ttu-id="f19ca-106">NetX Duo PTP 클라이언트 설정</span><span class="sxs-lookup"><span data-stu-id="f19ca-106">NetX Duo PTP Client Setup</span></span>

<span data-ttu-id="f19ca-107">제대로 작동하기 위해 PTP 클라이언트 패키지에 NetX Duo IP 인스턴스가 이미 생성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-107">In order to function properly, the PTP client package requires that a NetX Duo IP instance has already been created.</span></span>

<span data-ttu-id="f19ca-108">기본적으로 PTP 클라이언트는 IPv4 멀티캐스트 그룹을 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-108">By default, the PTP client joins IPv4 multicast group.</span></span> <span data-ttu-id="f19ca-109">IPv6 네트워크에서 PTP 클라이언트를 실행하려면 NetX Duo 라이브러리를 빌드할 때 `NX_ENABLE_IPV6_MULTICAST`를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-109">In order to run the PTP client on an IPv6 network, `NX_ENABLE_IPV6_MULTICAST` must be defined when building NetX Duo library.</span></span>

<span data-ttu-id="f19ca-110">PTP 클라이언트를 만들 때 애플리케이션은 들어오고 나가는 패킷의 타임스탬프를 처리하는 콜백 함수를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-110">When creating the PTP client, the application must provide a callback function to handle timestamps of incoming and outgoing packets.</span></span> <span data-ttu-id="f19ca-111">높은 해상도를 얻기 위해 애플리케이션에서 고해상도 타이머를 사용하여 타임스탬프를 생성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-111">To achieve high resolution, we recommend applications to generate timestamps using a high resolution timer.</span></span> <span data-ttu-id="f19ca-112">시뮬레이터에서 PTP를 실행하기 위해 소프트웨어 기반 구현 `nx_ptp_client_soft_clock_callback`이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-112">To run the PTP on simulator, a software-based implementation `nx_ptp_client_soft_clock_callback` is provided.</span></span>

<span data-ttu-id="f19ca-113">PTP 클라이언트는 PTP 메시지를 전송하기 위한 패킷 풀이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-113">The PTP client requires a packet pool for transmitting PTP messages.</span></span> <span data-ttu-id="f19ca-114">패킷 풀의 페이로드 크기는 `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` 이상이어야 합니다. 즉, IPv4의 경우 108바이트이고 IPv6이 사용되는 경우에는 128바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-114">The payload size of packet pool must be no less than `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE`, which is 108 bytes for IPv4, and 128 bytes if IPv6 is enabled.</span></span>

<span data-ttu-id="f19ca-115">PTP 클라이언트를 만든 후 애플리케이션은 PTP 클라이언트를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-115">After creating the PTP Client, the application can start the PTP client.</span></span> <span data-ttu-id="f19ca-116">동기화는 PTP 도우미 스레드에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-116">The synchronization is done in the PTP helper thread.</span></span> <span data-ttu-id="f19ca-117">이벤트 콜백 함수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-117">An event callback function can be specified.</span></span> <span data-ttu-id="f19ca-118">다음 이벤트 중 하나가 발생하면 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-118">It will be invoked when any one of the following events happen.</span></span>
* <span data-ttu-id="f19ca-119">마스터가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-119">A master is selected;</span></span> 
* <span data-ttu-id="f19ca-120">시간이 보정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-120">The time is calibrated.</span></span>
* <span data-ttu-id="f19ca-121">마스터 시간이 초과됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-121">A master times out.</span></span>

## <a name="netx-duo-ptp-client-messages"></a><span data-ttu-id="f19ca-122">NetX Duo PTP 클라이언트 메시지</span><span class="sxs-lookup"><span data-stu-id="f19ca-122">NetX Duo PTP Client Messages</span></span>

<span data-ttu-id="f19ca-123">NetX Duo PTP 클라이언트는 지연 요청-응답 메커니즘만 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-123">The NetX Duo PTP client implements the delay request-response mechanism only.</span></span> <span data-ttu-id="f19ca-124">PTP 클라이언트는 두 개의 UDP 포트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-124">The PTP client  opens two UDP ports.</span></span> <span data-ttu-id="f19ca-125">**이벤트** 메시지의 경우 *319* 이고 **일반** 메시지의 경우 *320* 입니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-125">*319* for **event** message and *320* for **general** message.</span></span> <span data-ttu-id="f19ca-126">이 메커니즘에는 다섯 가지 유형의 메시지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-126">There are five types of message for this mechanism.</span></span>

* <span data-ttu-id="f19ca-127">**Announce**.</span><span class="sxs-lookup"><span data-stu-id="f19ca-127">**Announce**.</span></span> <span data-ttu-id="f19ca-128">이는 이벤트 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-128">This is an event message.</span></span> <span data-ttu-id="f19ca-129">마스터 클록 선택에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-129">It is used for master clock selection.</span></span>
* <span data-ttu-id="f19ca-130">**Sync**. 이는 이벤트 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-130">**Sync**. This is an event message.</span></span> <span data-ttu-id="f19ca-131">원본 타임스탬프를 보내고 마스터에서 클라이언트로의 경로 지연을 계산하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-131">It is used to send origin timestamp and calculate the path delay from master to client.</span></span>
* <span data-ttu-id="f19ca-132">**Follow_Up**.</span><span class="sxs-lookup"><span data-stu-id="f19ca-132">**Follow_Up**.</span></span> <span data-ttu-id="f19ca-133">이는 일반 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-133">This is a general message.</span></span> <span data-ttu-id="f19ca-134">이는 선택 사항이며 관련된 Sync 메시지에서 원본 타임스탬프를 수정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-134">It is optional and used to correct the origin timestamp in related Sync message.</span></span> <span data-ttu-id="f19ca-135">Sync 플래그에서 두 단계 비트가 설정된 경우에만 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-135">It is sent only when the two step bit in Sync flag is set.</span></span>
* <span data-ttu-id="f19ca-136">**Delay_Req**.</span><span class="sxs-lookup"><span data-stu-id="f19ca-136">**Delay_Req**.</span></span> <span data-ttu-id="f19ca-137">이는 이벤트 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-137">This is an event message.</span></span> <span data-ttu-id="f19ca-138">Delay_Resp 수신 시 클라이언트에서 마스터로의 경로 지연을 계산하기 위해 PTP 클라이언트에서 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-138">It is sent from PTP client to calculate the path delay from client to master, on receiving Delay_Resp.</span></span>
* <span data-ttu-id="f19ca-139">**Delay_Resp**.</span><span class="sxs-lookup"><span data-stu-id="f19ca-139">**Delay_Resp**.</span></span> <span data-ttu-id="f19ca-140">이는 이벤트 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-140">This is an event message.</span></span> <span data-ttu-id="f19ca-141">클라이언트에서 마스터로의 경로 지연을 계산하기 위해 마스터에서 클라이언트로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-141">It is sent from master to client to calculate the path delay from client to master.</span></span>

<span data-ttu-id="f19ca-142">*“Best master clock” 알고리즘이 구현되어 있지 않습니다. PTP 클라이언트가 수신 대기 상태인 경우 첫 번째 마스터 클록만 수락됩니다.*</span><span class="sxs-lookup"><span data-stu-id="f19ca-142">*Note, "best master clock" algorithm is not implemented. Only the first master clock is accepted when the PTP client is in listening state.*</span></span>

## <a name="netx-duo-ptp-client-clock-callback"></a><span data-ttu-id="f19ca-143">NetX Duo PTP 클라이언트 클록 콜백</span><span class="sxs-lookup"><span data-stu-id="f19ca-143">NetX Duo PTP Client Clock Callback</span></span>
<span data-ttu-id="f19ca-144">마스터에서 클록을 동기화하려면 PTP 클라이언트에 로컬 클록이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-144">To synchronize clock from master, PTP client needs a local clock.</span></span> <span data-ttu-id="f19ca-145">클록 콜백 함수는 만드는 동안 PTP 클라이언트에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-145">A clock callback function is passed into PTP client during creation.</span></span> <span data-ttu-id="f19ca-146">클록 콜백 루틴의 형식은 아래에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-146">The format of the clock callback routine is  defined below.</span></span>
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
<span data-ttu-id="f19ca-147">입력 매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-147">The input parameters are defined as follows:</span></span>
* <span data-ttu-id="f19ca-148">*client_ptr* 은 PTP 클라이언트를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-148">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="f19ca-149">*operation* 은 콜백 작업을 지정합니다. 유효한 값은 아래 목록에 표시된 것처럼 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-149">*operation* specifies the callback operation, valid values are defined as shown in the list below.</span></span>
  * <span data-ttu-id="f19ca-150">**NX_PTP_CLIENT_CLOCK_INIT** 클록을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-150">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="f19ca-151">**NX_PTP_CLIENT_CLOCK_SET** `time_ptr`로 지정된 현재 타임스탬프를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-151">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="f19ca-152">**NX_PTP_CLIENT_CLOCK_GET** `time_ptr`로 현재 타임스탬프를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-152">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="f19ca-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** `packet_ptr`에서 `time_ptr`로 타임스탬프를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="f19ca-154">**NX_PTP_CLIENT_CLOCK_ADJUST** 현재 타임스탬프를 *1* 초 미만으로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-154">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="f19ca-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** 전송 시 PTP 클라이언트에 타임스탬프를 알려야 하는 `packet_ptr`을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="f19ca-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** 소프트 타이머를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="f19ca-157">하드웨어 클록에서 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-157">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="f19ca-158">*time_ptr* 은 타임스탬프를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-158">*time_ptr* points to timestamp.</span></span>
* <span data-ttu-id="f19ca-159">*packet_ptr* 은 패킷을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-159">*packet_ptr* points to packet.</span></span>
* <span data-ttu-id="f19ca-160">*callback_data* 는 불투명 콜백 데이터를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-160">*callback_data* points to opaque callback data.</span></span>

<span data-ttu-id="f19ca-161">NX_PTP_TIME 데이터 형식은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-161">The NX_PTP_TIME data type is defined as follows.</span></span>
```C
typedef struct NX_PTP_TIME_STRUCT
{
    /* The MSB of the number of seconds */
    LONG  second_high;

    /* The LSB of the number of seconds */
    ULONG second_low;

    /* The number of nanoseconds */
    LONG  nanosecond;
} NX_PTP_TIME;
```

## <a name="netx-duo-ptp-client-event-callback"></a><span data-ttu-id="f19ca-162">NetX Duo PTP 클라이언트 이벤트 콜백</span><span class="sxs-lookup"><span data-stu-id="f19ca-162">NetX Duo PTP Client Event Callback</span></span>
<span data-ttu-id="f19ca-163">애플리케이션에 PTP 클라이언트 상태를 알리도록 이벤트 콜백 함수를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-163">The event callback function can be setup to notify application the state of PTP client.</span></span> <span data-ttu-id="f19ca-164">이벤트 콜백 루틴의 형식은 아래와 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-164">The format of the event callback routine is defined as shown below.</span></span>
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
<span data-ttu-id="f19ca-165">입력 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-165">The input parameters are.</span></span>
* <span data-ttu-id="f19ca-166">*client_ptr* 은 PTP 클라이언트를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-166">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="f19ca-167">*event* 는 콜백 이벤트를 지정하며 유효한 값은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-167">*event* specifies the callback event, valid values are defined as:</span></span>
  * <span data-ttu-id="f19ca-168">**NX_PTP_CLIENT_EVENT_MASTER** 마스터 클록이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-168">**NX_PTP_CLIENT_EVENT_MASTER** A master clock is selected.</span></span>
  * <span data-ttu-id="f19ca-169">**NX_PTP_CLIENT_EVENT_SYNC** PTP 클라이언트가 보정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-169">**NX_PTP_CLIENT_EVENT_SYNC** PTP client is calibrated.</span></span>
  * <span data-ttu-id="f19ca-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** 마스터 클록의 시간이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** Master clock is timeout.</span></span>
* <span data-ttu-id="f19ca-171">*event_data* 는 이벤트와 관련된 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-171">*event_data* specifies the data related to event.</span></span> <span data-ttu-id="f19ca-172">이벤트가 **NX_PTP_CLIENT_EVENT_MASTER** 인 경우 event_data는 `NX_PTP_CLIENT_MASTER` 인스턴스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-172">When event is **NX_PTP_CLIENT_EVENT_MASTER**, event_data points to `NX_PTP_CLIENT_MASTER` instance.</span></span> <span data-ttu-id="f19ca-173">이벤트가 **NX_PTP_CLIENT_EVENT_SYNC** 인 경우 event data는 `NX_PTP_CLIENT_SYNC` 인스턴스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-173">When event is **NX_PTP_CLIENT_EVENT_SYNC**, event data points to `NX_PTP_CLIENT_SYNC` instance.</span></span>

## <a name="netx-duo-ptp-client-communication"></a><span data-ttu-id="f19ca-174">NetX Duo PTP 클라이언트 통신</span><span class="sxs-lookup"><span data-stu-id="f19ca-174">NetX Duo PTP Client Communication</span></span>
<span data-ttu-id="f19ca-175">앞에서 설명한 대로 NetX Duo PTP 클라이언트는 지연 요청-응답 메커니즘만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-175">As mentioned previously, NetX Duo PTP client only supports delay request-response mechanism.</span></span> <span data-ttu-id="f19ca-176">이 메커니즘은 아래와 같이 클라이언트와 마스터 클록 사이의 평균 경로 지연을 측정합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-176">This mechanism measures the mean path delay between the client and the master clock as below:</span></span>
1. <span data-ttu-id="f19ca-177">클라이언트가 마스터로부터 *Announce* 메시지를 수신하고 가장 적합한 마스터로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-177">Client receives *Announce* message from master and select it as best master.</span></span>
1. <span data-ttu-id="f19ca-178">클라이언트가 마스터로부터 *Sync* 메시지를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-178">Client receives *Sync* message from master.</span></span> <span data-ttu-id="f19ca-179">타임스탬프 *t1* 은 이 메시지의 원본 타임스탬프입니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-179">The timestamp *t1* is the origin timestamp in this message.</span></span> <span data-ttu-id="f19ca-180">이 메시지가 수신되면 타임스탬프 *t2* 를 로컬 클록에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-180">The timestamp *t2* is read from local clock when this message is received.</span></span>
1. <span data-ttu-id="f19ca-181">클라이언트가 마스터로부터 *Follow_Up* 메시지를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-181">Client receives *Follow_Up* message from master.</span></span> <span data-ttu-id="f19ca-182">이 메시지는 선택 사항이며 *Sync* 플래그의 두 단계가 설정된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-182">This message is optional and valid only when two step in *Sync* flag is set.</span></span> <span data-ttu-id="f19ca-183">그런 다음, 타임스탬프 *t1* 이 이 메시지의 원본 타임스탬프로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-183">Then the timestamp *t1* is updated to the origin timestamp in this message.</span></span>
1. <span data-ttu-id="f19ca-184">클라이언트가 *Delay_Req* 메시지를 마스터로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-184">Client sends *Delay_Req* message to master.</span></span> <span data-ttu-id="f19ca-185">메시지가 전송될 때 로컬 클록에서 타임스탬프 *t3* 을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-185">The timestamp *t3* is read from local clock when the message is transmitted.</span></span>
1. <span data-ttu-id="f19ca-186">클라이언트가 마스터로부터 *Delay_Resp* 메시지를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-186">Client receives *Delay_Resp* message from master.</span></span> <span data-ttu-id="f19ca-187">타임스탬프 *t4* 는 이 메시지의 수신 타임스탬프입니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-187">The timestamp *t4* is the receive timestamp in this message.</span></span>

<span data-ttu-id="f19ca-188">평균 경로 지연은 다음과 같이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-188">The mean path delay is computed as shown below.</span></span>
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
<span data-ttu-id="f19ca-189">마스터의 오프셋은 아래와 같이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="f19ca-189">The offset from master is computed as shown below.</span></span>
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> <span data-ttu-id="f19ca-190">\***correctionField** _는 계산 도중에 무시됩니다._</span><span class="sxs-lookup"><span data-stu-id="f19ca-190">\*The \***correctionField** _ is ignored during the calculation._</span></span>