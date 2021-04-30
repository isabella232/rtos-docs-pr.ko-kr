---
title: 3장 - Azure RTOS NetX Duo DHCPv6 구성 옵션
description: Azure RTOS NetX Duo DHCPv6을 빌드하기 위한 몇 가지 구성 옵션이 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5396b1c04581b5f79d337462368c4718ba9bb16
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810903"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a><span data-ttu-id="eab85-103">3장 - Azure RTOS NetX Duo DHCPv6 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="eab85-103">Chapter 3 - Azure RTOS NetX Duo DHCPv6 configuration options</span></span>

<span data-ttu-id="eab85-104">Azure RTOS NetX Duo DHCPv6을 빌드하기 위한 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-104">There are several configuration options for building Azure RTOS NetX Duo DHCPv6.</span></span> <span data-ttu-id="eab85-105">다음 목록에서 각각에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-105">The following list describes each in detail:</span></span>  
  
  
- <span data-ttu-id="eab85-106">**NX_DHCPV6_THREAD_PRIORITY** 클라이언트 스레드의 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-106">**NX_DHCPV6_THREAD_PRIORITY** Priority of the Client thread.</span></span> <span data-ttu-id="eab85-107">기본적으로 이 값은 클라이언트 스레드가 우선 순위 2에서 실행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-107">By   default, this value specifies that   the Client thread runs at priority   2.</span></span>

- <span data-ttu-id="eab85-108">**NX_DHCPV6_MUTEX_WAIT** DHCPv6 클라이언트 뮤텍스의 배타적 잠금을 얻기 위한 제한 시간 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-108">**NX_DHCPV6_MUTEX_WAIT** Time out option for obtaining an exclusive lock on a DHCPv6 Client mutex.</span></span> <span data-ttu-id="eab85-109">기본값은 TX_WAIT_FOREVER입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-109">The default value is TX_WAIT_FOREVER.</span></span>

- <span data-ttu-id="eab85-110">**NX_DHCPV6_TICKS_PER_SECOND** 틱 비율(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-110">**NX_DHCPV6_TICKS_PER_SECOND** Ratio of ticks to seconds.</span></span> <span data-ttu-id="eab85-111">이는 프로세서에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-111">This is processor dependent.</span></span> <span data-ttu-id="eab85-112">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-112">The default value is 100.</span></span>

- <span data-ttu-id="eab85-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL** IP 수명 타이머가 현재 IP 주소를 클라이언트에 할당한 시간을 업데이트하는 시간 간격(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Time interval in seconds at which the IP lifetime timer updates the length of time the current IP address has been assigned to the Client.</span></span> <span data-ttu-id="eab85-114">기본적으로 이 값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-114">By default, this value is 1.</span></span>

- <span data-ttu-id="eab85-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL** 세션 타이머에서 클라이언트가 서버와 통신하는 세션의 시간을 업데이트하는 시간 간격(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**  Time interval in seconds at which the session timer updates the length of time the Client has been in session communicating with the Server.</span></span> <span data-ttu-id="eab85-116">기본적으로 이 값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-116">By default, this value is 1.</span></span>

- <span data-ttu-id="eab85-117">**NX_DHCPV6_MAX_IA_ADDRESS** 클라이언트 레코드에 추가할 수 있는 최대 IA 주소 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-117">**NX_DHCPV6_MAX_IA_ADDRESS** The maximum number of IA addresses that can be added to the Client record.</span></span> <span data-ttu-id="eab85-118">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-118">The default value is 1.</span></span> 

- <span data-ttu-id="eab85-119">**NX_DHCPV6_NUM_DNS_SERVERS** 클라이언트 레코드에 저장할 DNS 서버 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-119">**NX_DHCPV6_NUM_DNS_SERVERS** Number of DNS servers to store to the client record.</span></span> <span data-ttu-id="eab85-120">기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-120">The default value is 2.</span></span>

- <span data-ttu-id="eab85-121">**NX_DHCPV6_NUM_TIME_SERVERS** 클라이언트 레코드에 저장할 시간 서버 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-121">**NX_DHCPV6_NUM_TIME_SERVERS** Number of time servers to store to the client record.</span></span> <span data-ttu-id="eab85-122">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-122">The default value is 1.</span></span>

- <span data-ttu-id="eab85-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE** 클라이언트의 네트워크 도메인 이름을 보관할 클라이언트 레코드의 버퍼 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Size of the buffer in the Client record to hold the client’s network domain name.</span></span> <span data-ttu-id="eab85-124">기본값은 30입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-124">The default value is 30.</span></span>

- <span data-ttu-id="eab85-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE** 클라이언트의 표준 시간대를 보관할 클라이언트 레코드의 버퍼 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Size of the buffer in the Client record to hold the Client’s time zone.</span></span> <span data-ttu-id="eab85-126">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-126">The default value is 10.</span></span>

- <span data-ttu-id="eab85-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** 서버 회신의 옵션 상태 메시지를 보관할 클라이언트 레코드의 버퍼 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** Size of the buffer in the Client record to hold the option status message in a Server reply.</span></span> <span data-ttu-id="eab85-128">기본값은 100바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-128">The default value is 100 bytes.</span></span>

- <span data-ttu-id="eab85-129">**NX_DHCPV6_PACKET_TIME_OUT** 클라이언트 패킷 풀에서 패킷을 할당하는 제한 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-129">**NX_DHCPV6_PACKET_TIME_OUT** Time out in seconds for allocating a packet from the Client packet pool.</span></span> <span data-ttu-id="eab85-130">기본값은 3초입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-130">The default value is 3 seconds.</span></span>

- <span data-ttu-id="eab85-131">**NX_DHCPV6_TYPE_OF_SERVICE** 이는 DHCPv6 클라이언트 소켓에서 UDP 패킷 전송에 대한 서비스의 유형을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-131">**NX_DHCPV6_TYPE_OF_SERVICE** This defines the type of service for UDP packet transmission from the DHCPv6 Client socket.</span></span> <span data-ttu-id="eab85-132">기본값은 **NX_IP_NORMAL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-132">The default value is **NX_IP_NORMAL**.</span></span>

- <span data-ttu-id="eab85-133">**NX_DHCPV6_TIME_TO_LIVE** 패킷이 삭제되기 전에 네트워크 라우터에서 클라이언트 패킷이 전달되는 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-133">**NX_DHCPV6_TIME_TO_LIVE** The number of times a Client packet is forwarded by a network router before the packet is discarded.</span></span> <span data-ttu-id="eab85-134">기본값은 0x80입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-134">The default value is 0x80.</span></span>

- <span data-ttu-id="eab85-135">**NX_DHCPV6_QUEUE_DEPTH** NetX Duo가 패킷을 삭제하기 전에 클라이언트 UDP 소켓 수신 큐에 유지할 패킷 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-135">**NX_DHCPV6_QUEUE_DEPTH** Specifies the number of packets to keep in the Client UDP socket receive queue before NetX Duo discards packets.</span></span> <span data-ttu-id="eab85-136">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-136">The default value is 5.</span></span>

## <a name="dhcpv6-message-transmission"></a><span data-ttu-id="eab85-137">DHCPv6 메시지 전송</span><span class="sxs-lookup"><span data-stu-id="eab85-137">DHCPv6 Message Transmission</span></span>

<span data-ttu-id="eab85-138">DHCPv6 메시지 전송에 매개 변수를 설정하기 위한 DHCPv6 클라이언트 옵션 세트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-138">There are a set of DHCPv6 Client options for setting parameters on DHCPv6 message transmission.</span></span> <span data-ttu-id="eab85-139">이러한 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-139">These are:</span></span> 

  - <span data-ttu-id="eab85-140">초기 시간 제한</span><span class="sxs-lookup"><span data-stu-id="eab85-140">initial timeout</span></span>

  - <span data-ttu-id="eab85-141">첫 번째 전송에 대한 최대 지연</span><span class="sxs-lookup"><span data-stu-id="eab85-141">maximum delay on the first transmission</span></span>

  - <span data-ttu-id="eab85-142">최대 재전송 시간 제한</span><span class="sxs-lookup"><span data-stu-id="eab85-142">maximum retransmission timeout</span></span> 

  - <span data-ttu-id="eab85-143">최대 재전송 횟수</span><span class="sxs-lookup"><span data-stu-id="eab85-143">maximum number of retransmissions</span></span> 

  - <span data-ttu-id="eab85-144">서버 응답을 대기하는 최대 기간</span><span class="sxs-lookup"><span data-stu-id="eab85-144">maximum duration to wait for server response</span></span>

<span data-ttu-id="eab85-145">이러한 매개 변수는 각 DHCPv6 클라이언트 메시지에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-145">These parameters apply to each of the DHCPv6 Client messages:</span></span>

- <span data-ttu-id="eab85-146">SOLICIT</span><span class="sxs-lookup"><span data-stu-id="eab85-146">SOLICIT</span></span>

- <span data-ttu-id="eab85-147">REQUEST</span><span class="sxs-lookup"><span data-stu-id="eab85-147">REQUEST</span></span>

- <span data-ttu-id="eab85-148">RENEW</span><span class="sxs-lookup"><span data-stu-id="eab85-148">RENEW</span></span>

- <span data-ttu-id="eab85-149">REBIND</span><span class="sxs-lookup"><span data-stu-id="eab85-149">REBIND</span></span>

- <span data-ttu-id="eab85-150">RELEASE</span><span class="sxs-lookup"><span data-stu-id="eab85-150">RELEASE</span></span>

- <span data-ttu-id="eab85-151">DECLINE</span><span class="sxs-lookup"><span data-stu-id="eab85-151">DECLINE</span></span>

- <span data-ttu-id="eab85-152">확인</span><span class="sxs-lookup"><span data-stu-id="eab85-152">CONFIRM</span></span>

- <span data-ttu-id="eab85-153">INFORM</span><span class="sxs-lookup"><span data-stu-id="eab85-153">INFORM</span></span>

<span data-ttu-id="eab85-154">다음은 이러한 구성 가능한 옵션과 해당 기본값의 전체 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-154">The following is a complete list of these configurable options and their default</span></span> 

<span data-ttu-id="eab85-155">values:</span><span class="sxs-lookup"><span data-stu-id="eab85-155">values:</span></span>

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

<span data-ttu-id="eab85-156">재전송 제한 시간에 제한이 없으면 메시지 재전송 횟수를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-156">For no limit on a retransmission timeout, set the message retransmission count to 0.</span></span> <span data-ttu-id="eab85-157">DHCPv6 클라이언트 메시지를 다시 전송하는 횟수에 제한이 없는 경우(다시 시도) 메시지 재전송 횟수를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-157">For no limit on the number of times a DHCPv6 Client message is retransmitted (retries), set the message retransmission count to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="eab85-158">제한 시간 또는 다시 시도 횟수에 관계 없이, IPv6 주소 유효 수명이 만료되면 IP 주소 테이블에서 제거되고 더 이상 클라이언트에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-158">Regardless of length of timeout or number of retries, when an IPv6 address valid lifetime expires, it is removed from the IP address table and can no longer be used by the Client.</span></span> <span data-ttu-id="eab85-159">NetX Duo DHCPv6 클라이언트는 새 IPv6 주소를 요청하는 SOLICIT 메시지 요청 전송을 자동으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="eab85-159">The NetX Duo DHCPv6 Client will automatically begin sending SOLICIT messages requesting a new IPv6 address.</span></span>