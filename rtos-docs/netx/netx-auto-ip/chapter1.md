---
title: 1장 - Azure RTOS NetX AutoIP 소개
description: Azure RTOS NetX AutoIP 프로토콜은 로컬 네트워크에서 IPv4 주소를 동적으로 구성하기 위해 설계된 프로토콜입니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c26b4112814bb586e056246d68c2597d56df6085
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811665"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-autoip"></a><span data-ttu-id="c4e83-103">1장 - Azure RTOS NetX AutoIP 소개</span><span class="sxs-lookup"><span data-stu-id="c4e83-103">Chapter 1 - Introduction to Azure RTOS NetX AutoIP</span></span>
  
<span data-ttu-id="c4e83-104">Azure RTOS NetX AutoIP 프로토콜은 로컬 네트워크에서 IPv4 주소를 동적으로 구성하기 위해 설계된 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-104">The Azure RTOS NetX AutoIP Protocol is a protocol designed for dynamically configuring IPv4 addresses on a local network.</span></span> <span data-ttu-id="c4e83-105">AutoIP는 ARP 기능을 활용하여 자동 IP 주소 할당 기능을 수행하는 간단한 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-105">AutoIP is a simple protocol that utilizes ARP capabilities to perform its automatic IP address assignment function.</span></span> <span data-ttu-id="c4e83-106">AutoIP는 169.254.1.0 ~ 169.254.254.255 범위의 주소를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-106">AutoIP allocates addresses in the range of 169.254.1.0 through 169.254.254.255.</span></span>

## <a name="autoip-requirements"></a><span data-ttu-id="c4e83-107">AutoIP 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c4e83-107">AutoIP Requirements</span></span>

<span data-ttu-id="c4e83-108">NetX AutoIP 패키지를 제대로 작동하려면 NetX IP 인스턴스가 이미 생성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-108">In order to function properly, the NetX AutoIP package requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="c4e83-109">또한 동일한 IP 인스턴스에서 ARP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-109">In addition, ARP must be enabled on that same IP instance.</span></span> <span data-ttu-id="c4e83-110">NetX AutoIP 패키지에는 추가 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-110">The NetX AutoIP package has no further requirements.</span></span>

## <a name="autoip-constraints"></a><span data-ttu-id="c4e83-111">AutoIP 제약 조건</span><span class="sxs-lookup"><span data-stu-id="c4e83-111">AutoIP Constraints</span></span> 

<span data-ttu-id="c4e83-112">NetX AutoIP 프로토콜은 RFC3927 표준의 요구 사항을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-112">The NetX AutoIP protocol implements the requirements of the RFC3927 standard.</span></span> <span data-ttu-id="c4e83-113">그러나 다음과 같은 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-113">However, there are the following constraints:</span></span>

1. <span data-ttu-id="c4e83-114">NetX DHCP를 사용하는 경우 NetX IP 인스턴스 스레드와 AutoIP 스레드보다 우선 순위가 높은 DHCP 스레드를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-114">If NetX DHCP is used, the DHCP thread must be created with a higher priority than both the NetX IP instance thread and the AutoIP thread.</span></span>
1. <span data-ttu-id="c4e83-115">NetX AutoIP는 기존 IP 주소를 계속 사용할 수 있는 메커니즘을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-115">NetX AutoIP does not provide a mechanism for old IP addresses to continue being used.</span></span>
1. <span data-ttu-id="c4e83-116">IP 주소가 변경되면 애플리케이션은 기존 TCP 연결을 해제하고 새 IP 주소에 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-116">When the IP address changes, the application is responsible for tearing down any existing TCP connections and re-establishing them on the new IP address.</span></span>

## <a name="autoip-protocol-implementation"></a><span data-ttu-id="c4e83-117">AutoIP 프로토콜 구현</span><span class="sxs-lookup"><span data-stu-id="c4e83-117">AutoIP Protocol Implementation</span></span>

<span data-ttu-id="c4e83-118">NetX AutoIP 프로토콜은 먼저 169.254.1.0 ~ 169.254.254.255의 AutoIP IPv4 주소 범위 내에서 임의 주소를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-118">The NetX AutoIP protocol first selects a random address within the AutoIP IPv4 address range of 169.254.1.0 through 169.254.254.255.</span></span> <span data-ttu-id="c4e83-119">또는 애플리케이션에서 ***nx_auto_ip_start*** 함수에 제공하여 시작 IP 주소를 강제로 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-119">Alternatively, the application may force a starting IP address by providing it to the ***nx_auto_ip_start*** function.</span></span> <span data-ttu-id="c4e83-120">이는 AutoIP 주소가 이전 실행에서 성공적으로 사용된 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-120">This is useful in situations where an AutoIP address was successfully used in a prior run.</span></span>

<span data-ttu-id="c4e83-121">AutoIP 주소가 선택되면 NetX AutoIP는 선택한 주소에 대해 일련의 ARP 프로브를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-121">Once an AutoIP address is selected, NetX AutoIP sends out a series of ARP probes for the selected address.</span></span> <span data-ttu-id="c4e83-122">ARP 프로브는 보낸 사람 주소가 0.0.0.0으로 설정되고 대상 주소가 원하는 AutoIP 주소로 설정된 ARP 요청 메시지로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-122">An ARP probe consists of an ARP request message with the sender address set to 0.0.0.0 and the target address set to the desired AutoIP address.</span></span> <span data-ttu-id="c4e83-123">이러한 일련의 ARP 프로브가 전송됩니다(실제 숫자는 정의된 NX_AUTO_IP_PROBE_NUM에 의해 결정됨).</span><span class="sxs-lookup"><span data-stu-id="c4e83-123">A series of these ARP probes are sent (the actual number is determined by the define NX_AUTO_IP_PROBE_NUM).</span></span> <span data-ttu-id="c4e83-124">다른 네트워크 노드가 이 프로브에 응답하거나 동일한 주소에 대해 동일한 프로브를 보내면 AutoIP IPv4 주소 범위 내에서 새 AutoIP 주소가 임의로 선택되고 프로브 처리가 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-124">If another network node responds to this probe or sends an identical probe for the same address, a new AutoIP address is randomly selected within the AutoIP IPv4 address range and the probe processing repeats.</span></span>

<span data-ttu-id="c4e83-125">NX_AUTO_IP_PROBE_NUM 프로브가 응답 없이 전송되면 NetX AutoIP는 선택한 주소에 대해 일련의 ARP 알림을 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-125">If NX_AUTO_IP_PROBE_NUM probes are sent without any responses, NetX AutoIP issues a series of ARP announcements for the selected address.</span></span> <span data-ttu-id="c4e83-126">ARP 알림은 AutoIP 주소로 설정된 ARP 메시지의 보낸 사람 및 대상 주소가 모두 포함된 ARP 요청 메시지로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-126">An ARP announcement consists of an ARP request message with both the sender and target address in the ARP message set to the selected AutoIP address.</span></span> <span data-ttu-id="c4e83-127">NX_AUTO_IP_ANNOUNCE_NUM 정의에 해당하는 일련의 ARP 알림 메시지가 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-127">A series of ARP announcement messages are sent, corresponding to the define NX_AUTO_IP_ANNOUNCE_NUM.</span></span> <span data-ttu-id="c4e83-128">다른 네트워크 노드가 알림 메시지에 응답하거나 동일한 주소에 대해 동일한 알림을 보내는 경우 AutoIP IPv4 주소 범위 내에서 새 AutoIP 주소가 임의로 선택되고 프로브 처리가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-128">If another network node responds to an announce message or sends an identical announcement for the same address, a new AutoIP address is randomly selected within the AutoIP IPv4 address range and the probe processing starts over.</span></span>

<span data-ttu-id="c4e83-129">검색된 충돌 없이 프로브 및 알림이 완료되면 선택한 AutoIP 주소가 유효한 것으로 간주되고 연결된 IP 인스턴스는 이 주소로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-129">When the probe and announcement completes without any detected conflicts, the selected AutoIP address is considered valid and the associated IP instance is setup with this address.</span></span>

## <a name="autoip-address-change"></a><span data-ttu-id="c4e83-130">AutoIP 주소 변경</span><span class="sxs-lookup"><span data-stu-id="c4e83-130">AutoIP Address Change</span></span>

<span data-ttu-id="c4e83-131">앞서 언급했듯이 NetX AutoIP는 프로브 및 알림 처리가 성공한 후 IP 인스턴스 주소를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-131">As mentioned before, NetX AutoIP changes the IP instance address after successful probe and announcement processing.</span></span> <span data-ttu-id="c4e83-132">이 경우 모니터링은 그다지 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-132">Monitoring for this case is not terribly important.</span></span> <span data-ttu-id="c4e83-133">그러나 나중에 자동 AutoIP 주소를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-133">However, it is possible to have the AutoIP address change in the future.</span></span> <span data-ttu-id="c4e83-134">잠재적인 원인에는 DHCP 주소 확인뿐만 아니라 향후 AutoIP 주소 충돌이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-134">Potential causes include future AutoIP address conflicts as well as DHCP address resolution.</span></span> <span data-ttu-id="c4e83-135">이러한 잠재적 상황을 적절히 처리하기 위해 애플리케이션은 다음 NetX API를 사용하여 모든 IP 주소 변경을 경고해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-135">In order to process these potential situations properly, the application should use the following NetX API to alert it of any and all IP address changes:</span></span>

```c
nx_ip_address_change_notify(NX_IP *ip_ptr,
                            VOID (*ip_address_change_notify)(NX_IP *,VOID*),
                            VOID *additional_info);
```

<span data-ttu-id="c4e83-136">제공된 *ip_address_change_notify* 함수의 처리는 NetX AutoIP 프로세서를 다시 시작하거나 DHCP가 나중에 IP 주소를 확인한 경우 비활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-136">The processing in the supplied *ip_address_change_notify* function must either restart the NetX AutoIP processor or disable it if DHCP has subsequently resolved the IP address.</span></span> <span data-ttu-id="c4e83-137">샘플 처리는 *작은 예제 시스템* 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c4e83-137">Please refer to the *Small Example System* section for sample processing.</span></span>

## <a name="autoip-rfcs"></a><span data-ttu-id="c4e83-138">AutoIP RFC</span><span class="sxs-lookup"><span data-stu-id="c4e83-138">AutoIP RFCs</span></span>

<span data-ttu-id="c4e83-139">NetX AutoIP는 RFC3927 및 관련 RFC와 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4e83-139">NetX AutoIP is compliant with RFC3927 and related RFCs.</span></span>