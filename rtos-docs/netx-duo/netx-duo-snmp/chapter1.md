---
title: 1장 - Azure RTOS NetX Duo SNMP 소개
description: NetX Duo SNMP 구현은 SNMP 에이전트의 구현입니다. 에이전트는 SNMP 관리자의 명령에 응답하고 이벤트 기반 트랩을 전송하는 역할을 담당합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810597"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a><span data-ttu-id="8d3a0-104">1장 - Azure RTOS NetX Duo SNMP 소개</span><span class="sxs-lookup"><span data-stu-id="8d3a0-104">Chapter 1 - Introduction to Azure RTOS NetX Duo SNMP</span></span>

<span data-ttu-id="8d3a0-105">SNMP(Simple Network Management Protocol)는 인터넷에서 디바이스를 관리하기 위해서 설계된 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-105">The Simple Network Management Protocol (SNMP) is a protocol designed for managing devices on the internet.</span></span> <span data-ttu-id="8d3a0-106">SNMP는 연결 없는 UDP(User Datagram Protocol) 서비스를 활용하여 관리 기능을 수행하는 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-106">SNMP is a protocol that utilizes the connectionless User Datagram Protocol (UDP) services to perform its management function.</span></span> <span data-ttu-id="8d3a0-107">Azure RTOS NetX Duo SNMP 구현은 SNMP 에이전트의 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-107">The Azure RTOS NetX Duo SNMP implementation is that of an SNMP Agent.</span></span> <span data-ttu-id="8d3a0-108">에이전트는 SNMP 관리자의 명령에 응답하고 이벤트 기반 트랩을 전송하는 역할을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-108">An agent is responsible for responding to SNMP Manager’s commands and sending event driven traps.</span></span> 

<span data-ttu-id="8d3a0-109">NetX Duo SNMP는 SNMP 관리자와의 IPv4 및 IPv6 통신을 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-109">NetX Duo SNMP supports both IPv4 and IPv6 communication with SNMP Managers.</span></span> <span data-ttu-id="8d3a0-110">NetX SNMP 애플리케이션은 NetX Duo SNMP에서 컴파일하고 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-110">NetX SNMP applications should compile and run in NetX Duo SNMP.</span></span> <span data-ttu-id="8d3a0-111">그러나 개발자는 기존 SNMP 애플리케이션을 동등한 “Duo” 서비스를 사용하여 포팅하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-111">However, the developer is encouraged to port existing SNMP applications to using the equivalent “duo” services.</span></span> <span data-ttu-id="8d3a0-112">예를 들어 SNMP 트랩 메시지를 보낼 때 다음과 같은 ‘Duo’ 서비스는 NetX와 동등한 서비스를 대체해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-112">For example, when sending SNMP trap messages, the following ‘duo’ services should replace their NetX equivalent:</span></span>

<span data-ttu-id="8d3a0-113">*nxd_snmp_object_trap_send*</span><span class="sxs-lookup"><span data-stu-id="8d3a0-113">*nxd_snmp_object_trap_send*</span></span>

<span data-ttu-id="8d3a0-114">*nxd_snmp_object_trapv2_send*</span><span class="sxs-lookup"><span data-stu-id="8d3a0-114">*nxd_snmp_object_trapv2_send*</span></span>

<span data-ttu-id="8d3a0-115">*nxd_snmp_object_trapv3_send*</span><span class="sxs-lookup"><span data-stu-id="8d3a0-115">*nxd_snmp_object_trapv3_send*</span></span>

<span data-ttu-id="8d3a0-116">자세한 내용은 이 사용자 가이드의 다른 장에 있는 **SNMP 에이전트 서비스에 대한 설명** 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-116">For more details, see **Description of SNMP Agent Services** elsewhere in this User Guide for more details.</span></span>

## <a name="netx-duo-snmp-agent-requirements"></a><span data-ttu-id="8d3a0-117">NetX Duo SNMP 에이전트 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8d3a0-117">NetX Duo SNMP Agent Requirements</span></span>

<span data-ttu-id="8d3a0-118">NetX Duo SNMP 패키지를 사용하려면 IP 인스턴스가 이미 만들어져 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-118">The NetX Duo SNMP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="8d3a0-119">또한 동일한 IP 인스턴스에서 UDP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-119">In addition, UDP must be enabled on that same IP instance.</span></span>

<span data-ttu-id="8d3a0-120">NetX Duo SNMP 에이전트에는 몇 가지 추가 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-120">The NetX Duo SNMP Agent has several additional requirements.</span></span> <span data-ttu-id="8d3a0-121">먼저 모든 SNMP 관리자 요청을 처리하려면 포트 161에 대한 액세스 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-121">First, it requires access to port 161 for handling all SNMP manager requests.</span></span> <span data-ttu-id="8d3a0-122">또한 트랩 메시지를 관리자에게 보내려면 포트 162에 대한 액세스 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-122">It also requires access to port 162 for sending trap messages to the Manager.</span></span>

<span data-ttu-id="8d3a0-123">IPv6와 함께 NetX Duo SNMP 에이전트를 사용하고 IPv6 개체를 얻으려면 NetX Duo에서 IPv6를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-123">To use NetX Duo SNMP Agent with over IPv6 and to obtain IPv6 objects, IPv6 must be enabled in NetX Duo.</span></span> <span data-ttu-id="8d3a0-124">IPv6 서비스의 IP 인스턴스를 사용하도록 설정하기 위한 자세한 내용은 ***NetX Duo 사용자 가이드*** 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-124">See the ***NetX Duo User Guide*** for details on enabling the IP instance for IPv6 services.</span></span>

## <a name="netx-duo-snmp-constraints"></a><span data-ttu-id="8d3a0-125">NetX Duo SNMP 제약 조건</span><span class="sxs-lookup"><span data-stu-id="8d3a0-125">NetX Duo SNMP Constraints</span></span>

<span data-ttu-id="8d3a0-126">NetX Duo SNMP 프로토콜은 SNMP 버전 1, 2, 3을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-126">The NetX Duo SNMP protocol implements SNMP Version 1, 2, and 3.</span></span> <span data-ttu-id="8d3a0-127">SNMP 버전 3 구현에서는 MD5 및 SHA 인증과 DES 암호화를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-127">The SNMPv3 implementation supports MD5 and SHA authentication, and DES encryption.</span></span> <span data-ttu-id="8d3a0-128">이 버전의 NetX Duo SNMP 에이전트에는 다음과 같은 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-128">This version of the NetX Duo SNMP Agent has the following constraints:</span></span>

1. <span data-ttu-id="8d3a0-129">NetX IP 인스턴스 당 하나의 SNMP 에이전트</span><span class="sxs-lookup"><span data-stu-id="8d3a0-129">One SNMP Agent per NetX IP Instance</span></span>
2. <span data-ttu-id="8d3a0-130">RMON 지원 안 함</span><span class="sxs-lookup"><span data-stu-id="8d3a0-130">No support for RMON</span></span>
3. <span data-ttu-id="8d3a0-131">SNMP 버전 3 알림 메시지가 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="8d3a0-131">SNMP v3 Inform messages are not supported</span></span>
4. <span data-ttu-id="8d3a0-132">OPAQUE 및 NSAP 데이터 형식은 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="8d3a0-132">OPAQUE and NSAP data types are not supported</span></span>
5. <span data-ttu-id="8d3a0-133">IPv6 주소는 옥텟 문자열로 정의되며 형식 확인은 애플리케이션에서 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-133">IPv6 addresses are defined as octet strings, and format checking is left to the application.</span></span>

## <a name="snmp-object-names"></a><span data-ttu-id="8d3a0-134">SNMP 개체 이름</span><span class="sxs-lookup"><span data-stu-id="8d3a0-134">SNMP Object Names</span></span>

<span data-ttu-id="8d3a0-135">SNMP 프로토콜은 인터넷에서 디바이스를 관리하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-135">The SNMP protocol is designed to manage devices on the internet.</span></span> <span data-ttu-id="8d3a0-136">이를 위해 각 SNMP 관리 디바이스에는 RFC 1155에서 정의한 SMI(관리 정보 구조)에 의해 정의되는 개체 세트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-136">To accomplish this, each SNMP managed device has a set of objects that are defined by the Structure of Management Information (SMI) as defined by RFC 1155.</span></span> <span data-ttu-id="8d3a0-137">구조는 다음과 같은 계층 구조 트리 형식의 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-137">The structure is a hierarchical tree type of structure that looks like the following:</span></span>

![관리 정보 구조의 다이어그램입니다.](media/image3.png)

<span data-ttu-id="8d3a0-139">트리에 있는 각 노드는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-139">Each node in the tree is an object.</span></span> <span data-ttu-id="8d3a0-140">트리에서 “dod” 개체는 1.3.6 표기법으로 식별되는 반면 트리에서 “internet” 개체는 1.3.6.1 표기법으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-140">The “dod” object in the tree is identified by the notation 1.3.6, while the “internet” object in the tree is identified by the notation 1.3.6.1.</span></span> <span data-ttu-id="8d3a0-141">모든 SNMP 개체 이름은 1.3.6 표기법으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-141">All SNMP object names begin with the notation 1.3.6.</span></span>

<span data-ttu-id="8d3a0-142">SNMP 관리자는 이 개체 표기법을 사용하여 디바이스에서 가져오거나 설정하려는 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-142">An SNMP Manager uses this object notation to specify what object in the device it wishes to get or set.</span></span> <span data-ttu-id="8d3a0-143">NetX Duo SNMP 에이전트는 관리자 요청을 해석하고 애플리케이션이 요청한 작업을 수행할 수 있는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-143">The NetX Duo SNMP Agent interprets such manager requests and provides mechanisms for the application to perform the requested operation.</span></span>

## <a name="snmp-manager-requests"></a><span data-ttu-id="8d3a0-144">SNMP 관리자 요청</span><span class="sxs-lookup"><span data-stu-id="8d3a0-144">SNMP Manager Requests</span></span>

<span data-ttu-id="8d3a0-145">SNMP에는 디바이스를 관리하기 위한 간단한 메커니즘이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-145">The SNMP has a simple mechanism for managing devices.</span></span> <span data-ttu-id="8d3a0-146">SNMP 관리자에서 ‘포트 161’의 SNMP 디바이스에 실행한 표준 SNMP 명령 세트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-146">There is a set of standard SNMP commands that are issued by the SNMP Manager to the SNMP device on *port 161*.</span></span> <span data-ttu-id="8d3a0-147">다음은 SNMP 관리자 기본 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-147">The following shows some of the basic SNMP Manager commands:</span></span>

| <span data-ttu-id="8d3a0-148">SNMP 명령</span><span class="sxs-lookup"><span data-stu-id="8d3a0-148">SNMP Command</span></span> | <span data-ttu-id="8d3a0-149">의미</span><span class="sxs-lookup"><span data-stu-id="8d3a0-149">Meaning</span></span>                                                        |
|--------------|----------------------------------------------------------------|
| <span data-ttu-id="8d3a0-150">GET</span><span class="sxs-lookup"><span data-stu-id="8d3a0-150">GET</span></span>          | <span data-ttu-id="8d3a0-151">지정한 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="8d3a0-151">*Get the specified object*</span></span>                                       |
| <span data-ttu-id="8d3a0-152">GETNEXT</span><span class="sxs-lookup"><span data-stu-id="8d3a0-152">GETNEXT</span></span>      | <span data-ttu-id="8d3a0-153">지정한 개체 ID 뒤에 있는 다음 논리 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="8d3a0-153">*Get the next logical object after the specified object ID*</span></span>      |
| <span data-ttu-id="8d3a0-154">GETBULK</span><span class="sxs-lookup"><span data-stu-id="8d3a0-154">GETBULK</span></span>      | <span data-ttu-id="8d3a0-155">지정한 개체 ID 뒤에 있는 여러 논리 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="8d3a0-155">*Get the multiple logical objects after the specified object ID*</span></span> |
| <span data-ttu-id="8d3a0-156">SET</span><span class="sxs-lookup"><span data-stu-id="8d3a0-156">SET</span></span>          | <span data-ttu-id="8d3a0-157">지정한 개체 설정</span><span class="sxs-lookup"><span data-stu-id="8d3a0-157">*Set the specified object*</span></span>                                       |

<span data-ttu-id="8d3a0-158">해당 명령은 ASN 1(Abstract Syntax Notation One) 형식으로 인코딩되고 SNMP 관리자에서 보낸 UDP 패킷의 페이로드에 위치합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-158">These commands are encoded in the Abstract Syntax Notation One (ASN.1) format and reside in the payload of the UDP packet sent by the SNMP Manager.</span></span> <span data-ttu-id="8d3a0-159">NetX Duo SNMP 에이전트는 요청을 처리한 다음 ***nx_snmp_agent_create*** 호출에 지정된 해당 처리 루틴을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-159">The NetX Duo SNMP Agent processes the request and then calls the corresponding handling routine specified in the ***nx_snmp_agent_create*** call.</span></span>

## <a name="netx-duo-snmp-agent-traps"></a><span data-ttu-id="8d3a0-160">NetX Duo SNMP 에이전트 트랩</span><span class="sxs-lookup"><span data-stu-id="8d3a0-160">NetX Duo SNMP Agent Traps</span></span>

<span data-ttu-id="8d3a0-161">NetX Duo SNMP 에이전트는 SNMP 관리자에게 비동기적으로 이벤트를 경고하는 기능도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-161">The NetX Duo SNMP Agent provides the ability to also alert an SNMP Manager of events asynchronously.</span></span> <span data-ttu-id="8d3a0-162">이 기능은 SNMP 트랩 명령을 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-162">This is done via an SNMP trap command.</span></span> <span data-ttu-id="8d3a0-163">SNMP 관리자에게 트랩을 보내기 위한 각 버전의 SNMP에 대한 고유한 API가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-163">There is a unique API for each version of SNMP for sending traps to an SNMP Manager.</span></span> <span data-ttu-id="8d3a0-164">기본적으로 트랩은 포트 162의 SNMP 관리자에게 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-164">By default, the traps are sent to the SNMP Manager on port 162.</span></span>

<span data-ttu-id="8d3a0-165">NetX Duo SNMP 에이전트는 SNMP 버전 3 트랩 메시지에 대해 별도의 보안 키를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-165">The NetX Duo SNMP Agent provides separate security keys for SNMPv3 trap messages.</span></span> <span data-ttu-id="8d3a0-166">이렇게 하려면 SNMP 애플리케이션은 관리자 요청에 대한 응답에 적용되는 키 세트에서 별도의 키 세트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-166">To do so, the SNMP application must create a separate set of keys from those applied to responses to Manager requests.</span></span> <span data-ttu-id="8d3a0-167">트랩 보안을 사용하면 SNMP 에이전트가 인증 및 개인 정보에 동일한 암호 또는 다른 암호를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-167">Trap security enables the SNMP Agent to use the same or different passwords for authentication and privacy.</span></span> <span data-ttu-id="8d3a0-168">보안 키를 만드는 방법에 대한 자세한 내용은 다음 섹션의 **NetX Duo SNMP 인증 및 암호화** 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-168">For more information on creating security keys, see **NetX Duo SNMP Authentication and Encryption** in the next section.</span></span>

<span data-ttu-id="8d3a0-169">표준 SNMP 트랩 변수 목록은 nxd_snmp.h 맨 위에 열거됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-169">A list of standard SNMP trap variables is enumerated at the top of *nxd_snmp.h:*</span></span>

| <span data-ttu-id="8d3a0-170">변수</span><span class="sxs-lookup"><span data-stu-id="8d3a0-170">Variables</span></span>                                 | <span data-ttu-id="8d3a0-171">값</span><span class="sxs-lookup"><span data-stu-id="8d3a0-171">Value</span></span>  |
|-------------------------------------------|---|
| <span data-ttu-id="8d3a0-172">#define NX_SNMP_TRAP_COLDSTART</span><span class="sxs-lookup"><span data-stu-id="8d3a0-172">#define NX_SNMP_TRAP_COLDSTART</span></span>            | <span data-ttu-id="8d3a0-173">0</span><span class="sxs-lookup"><span data-stu-id="8d3a0-173">0</span></span> |
| <span data-ttu-id="8d3a0-174">#define NX_SNMP_TRAP_WARMSTART</span><span class="sxs-lookup"><span data-stu-id="8d3a0-174">#define NX_SNMP_TRAP_WARMSTART</span></span>            | <span data-ttu-id="8d3a0-175">1</span><span class="sxs-lookup"><span data-stu-id="8d3a0-175">1</span></span> |
| <span data-ttu-id="8d3a0-176">#define NX_SNMP_TRAP_LINKDOWN</span><span class="sxs-lookup"><span data-stu-id="8d3a0-176">#define NX_SNMP_TRAP_LINKDOWN</span></span>             | <span data-ttu-id="8d3a0-177">2</span><span class="sxs-lookup"><span data-stu-id="8d3a0-177">2</span></span> |
| <span data-ttu-id="8d3a0-178">#define NX_SNMP_TRAP_LINKUP</span><span class="sxs-lookup"><span data-stu-id="8d3a0-178">#define NX_SNMP_TRAP_LINKUP</span></span>               | <span data-ttu-id="8d3a0-179">3</span><span class="sxs-lookup"><span data-stu-id="8d3a0-179">3</span></span> |
| <span data-ttu-id="8d3a0-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span><span class="sxs-lookup"><span data-stu-id="8d3a0-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span></span> | <span data-ttu-id="8d3a0-181">4</span><span class="sxs-lookup"><span data-stu-id="8d3a0-181">4</span></span> |
| <span data-ttu-id="8d3a0-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span><span class="sxs-lookup"><span data-stu-id="8d3a0-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span></span>      | <span data-ttu-id="8d3a0-183">5</span><span class="sxs-lookup"><span data-stu-id="8d3a0-183">5</span></span> |
| <span data-ttu-id="8d3a0-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span><span class="sxs-lookup"><span data-stu-id="8d3a0-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span></span>   | <span data-ttu-id="8d3a0-185">6</span><span class="sxs-lookup"><span data-stu-id="8d3a0-185">6</span></span> |

<span data-ttu-id="8d3a0-186">변수를 트랩 메시지에 포함하려면 *nx_snmp_agent_trapv2_send*(SNMPv2) 또는 *nx_snmp_agent_trapv3_send*(SNMPv3)의 trap_type 입력 인수를 변수의 열거된 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-186">To include these variables in the trap message, the trap_type input argument in *nx_snmp_agent_trapv2_send* (SNMPv2) or *nx_snmp_agent_trapv3_send* (SNMPv3) is set to the enumerated value of these variables.</span></span> <span data-ttu-id="8d3a0-187">다음 아래는 SNMP 버전 2가 콜드 부팅 이벤트를 SNMP 관리자에게 알리는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-187">An example is shown below for SNMPv2 to notify the SNMP Manager of a cold start event:</span></span>

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

<span data-ttu-id="8d3a0-188">트랩 메시지에 전용 변수를 포함하기 위해 trap_type 입력 인수는 NX_SNMP_TRAP_CUSTOM으로 설정되고 트랩 목록 입력 인수는 전용 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-188">To include proprietary variables in the trap message, the trap_type input argument is set to NX_SNMP_TRAP_CUSTOM and the trap list input argument contains the proprietary data.</span></span> <span data-ttu-id="8d3a0-189">트랩 메시지에는 시스템 작동 시간(1.3.6.1.6.3.1.1.4.1.0)이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-189">Note that the trap message will contain as the system up time (1.3.6.1.6.3.1.1.4.1.0).</span></span> <span data-ttu-id="8d3a0-190">다음 아래는 SNMP 버전 2에 대한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-190">An example is shown below for SNMPv2:</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a><span data-ttu-id="8d3a0-191">NetX Duo SNMP 인증 및 암호화</span><span class="sxs-lookup"><span data-stu-id="8d3a0-191">NetX Duo SNMP Authentication and Encryption</span></span>

<span data-ttu-id="8d3a0-192">인증에는 ‘기본’ 및 ‘다이제스트’의 두 가지 종류가 있습니다. </span><span class="sxs-lookup"><span data-stu-id="8d3a0-192">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="8d3a0-193">기본 인증은 많은 프로토콜에서 볼 수 있는 간단한 일반 텍스트 ‘사용자 이름’ 인증과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-193">Basic authentication is equivalent to a simple plain text *username* authentication found in many protocols.</span></span> <span data-ttu-id="8d3a0-194">SNMP 기본 인증에서 사용자는 제공된 사용자 이름이 SNMP 작업 수행에 유효한지 확인만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-194">In SNMP basic authentication, the user simply verifies that the supplied username is valid for performing SNMP operations.</span></span> <span data-ttu-id="8d3a0-195">기본 인증은 SNMP 버전 1과 버전 2에 대한 유일한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-195">Basic authentication is the only option for SNMP versions 1 and 2.</span></span>

<span data-ttu-id="8d3a0-196">기본 인증의 주요 단점은 사용자 이름이 일반 텍스트로 전송된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-196">The main disadvantage of basic authentication is the username is transmitted in plain text.</span></span> <span data-ttu-id="8d3a0-197">SNMP 버전 3 다이제스트 인증은 사용자 이름을 일반 텍스트로 전송하지 않음으로써 이 문제를 해결해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-197">The SNMPv3 digest authentication addresses this problem by never transmitting the username in plain text.</span></span> <span data-ttu-id="8d3a0-198">대신 알고리즘을 사용하여 사용자 이름, 컨텍스트 엔진 및 기타 정보에서 96비트 ‘다이제스트’를 파생합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-198">Instead, an algorithm is used to derive a 96-bit ‘digest’ from the username, context engine, and other information.</span></span> <span data-ttu-id="8d3a0-199">NetX Duo SNMP 에이전트는 MD5 및 SHA 다이제스트 알고리즘을 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-199">The NetX Duo SNMP Agent supports both MD5 and SHA digest algorithms.</span></span>

<span data-ttu-id="8d3a0-200">인증을 사용하려면 SNMP 에이전트가 *nx_snmp_agent_context_engine_set* 서비스를 사용하여 컨텍스트 엔진 ID를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-200">To enable authentication, the SNMP Agent must set its Context Engine ID using the *nx_snmp_agent_context_engine_set* service.</span></span> <span data-ttu-id="8d3a0-201">컨텍스트 엔진 ID는 인증 키를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-201">The Context Engine ID is used in the creation of the authentication key.</span></span>

<span data-ttu-id="8d3a0-202">DES 알고리즘을 사용하여 SNMP 버전 3 데이터의 암호화를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-202">Encryption of SNMPv3 data is available using the DES algorithm.</span></span> <span data-ttu-id="8d3a0-203">암호화는 인증을 사용하도록 설정해야 합니다. 인증 매개 변수를 설정하지 않으면 데이터를 암호화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-203">Encryption requires that authentication be enabled (one cannot encrypt data without setting the authentication parameters).</span></span>

<span data-ttu-id="8d3a0-204">인증 및 개인 키를 만들려면 다음과 같은 API가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-204">To create authentication and privacy keys, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

<span data-ttu-id="8d3a0-205">그런 다음, 해당 키를 사용하도록 SNMP 에이전트를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-205">Next, the SNMP agent must be configured to use these keys.</span></span> <span data-ttu-id="8d3a0-206">SNMP 에이전트에 키를 등록하려면 다음과 같은 API가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-206">To register a key with the SNMP agent, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="8d3a0-207">트랩 메시지에 대한 별도의 키를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-207">Separate keys can be created for trap messages.</span></span> <span data-ttu-id="8d3a0-208">트랩 메시지에 키를 적용하려면 다음 API를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-208">To apply keys for trap messages the following API are available:</span></span>

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="8d3a0-209">응답 메시지 및 트랩 전송에 대한 인증 또는 암호화를 사용하지 않으려면 키 포인터 입력이 NULL로 설정된 서비스를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-209">To disable authentication or encryption for response messages and sending traps, use these services with the key pointer input set to NULL.</span></span>

## <a name="netx-duo-snmp-community-strings"></a><span data-ttu-id="8d3a0-210">NetX Duo SNMP 커뮤니티 문자열</span><span class="sxs-lookup"><span data-stu-id="8d3a0-210">NetX Duo SNMP Community Strings</span></span>

<span data-ttu-id="8d3a0-211">NetX Duo SNMP 에이전트는 퍼블릭 및 프라이빗 커뮤니티 문자열을 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-211">The NetX Duo SNMP Agent supports both public and private community strings.</span></span> <span data-ttu-id="8d3a0-212">퍼블릭 문자열은 *nx_snmp_agent _public_string_set* 서비스를 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-212">The public string is set with the *nx_snmp_agent _public_string_set* service.</span></span> <span data-ttu-id="8d3a0-213">NetX Duo SNMP 에이전트 프라이빗 문자열은 *nx_snmp_agent_private_string_set* 서비스를 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-213">The NetX Duo SNMP Agent private string is set using the *nx_snmp_agent_private_string_set* service.</span></span>

## <a name="netx-duo-snmp-username-callback"></a><span data-ttu-id="8d3a0-214">NetX Duo SNMP 사용자 이름 콜백</span><span class="sxs-lookup"><span data-stu-id="8d3a0-214">NetX Duo SNMP Username Callback</span></span>

<span data-ttu-id="8d3a0-215">NetX Duo SNMP 에이전트 패키지를 사용하면 애플리케이션에서 각 SNMP 클라이언트 요청을 처리하기 시작할 때 호출되는 사용자 이름 콜백을 ***nx_snmp_agent_create*** 호출을 통해 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-215">The NetX Duo SNMP Agent package allows the application to specify (via the ***nx_snmp_agent_create*** call) a username callback  that is called at the beginning of handling each SNMP Client request.</span></span>

<span data-ttu-id="8d3a0-216">콜백 루틴은 NetX Duo SNMP 에이전트에게 사용자 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-216">The callback routine provides the NetX Duo SNMP Agent with the username.</span></span> <span data-ttu-id="8d3a0-217">제공된 사용자 이름이 유효하거나 요청에 응답하는 데 사용자 이름 확인이 필요하지 않은 경우 사용자 이름 콜백에서 **NX_SUCCESS** 의 값을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-217">If the supplied username is valid or if no username check is necessary for the responding to the request, the username callback should return the value of **NX_SUCCESS**.</span></span> <span data-ttu-id="8d3a0-218">그러지 않은 경우 루틴은 지정된 사용자 이름이 잘못되었음을 나타내는 **NX_SNMP_ERROR** 를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-218">Otherwise, the routine should return **NX_SNMP_ERROR** to indicate the specified username is invalid.</span></span>

<span data-ttu-id="8d3a0-219">애플리케이션 사용자 이름 콜백 루틴의 형식은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-219">The format of the application username callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

<span data-ttu-id="8d3a0-220">입력 매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-220">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="8d3a0-221">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8d3a0-221">Parameter</span></span> | <span data-ttu-id="8d3a0-222">의미</span><span class="sxs-lookup"><span data-stu-id="8d3a0-222">Meaning</span></span>                                              |
|-----------|------------------------------------------------------|
| <span data-ttu-id="8d3a0-223">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="8d3a0-223">*agent_ptr*</span></span> | <span data-ttu-id="8d3a0-224">SNMP 에이전트 호출에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8d3a0-224">Pointer to calling SNMP agent</span></span>                        |
| <span data-ttu-id="8d3a0-225">사용자 이름</span><span class="sxs-lookup"><span data-stu-id="8d3a0-225">username</span></span>  | <span data-ttu-id="8d3a0-226">필요한 사용자 이름에 대한 포인터의 대상</span><span class="sxs-lookup"><span data-stu-id="8d3a0-226">Destination for the pointer to the required username</span></span> |

<span data-ttu-id="8d3a0-227">SNMP 버전 1 및 SNMP 버전 2/버전 2C 세션의 경우 애플리케이션은 들어오는 SNMP 요청의 커뮤니티 문자열을 검사하여 SNMP 요청에 유효한 커뮤니티 문자열이 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-227">For SNMPv1 and SNMPv2/v2C sessions, the application will want to examine the community string on an incoming SNMP request to determine if the SNMP request has a valid community string.</span></span> <span data-ttu-id="8d3a0-228">SNMP 애플리케이션에서 이 작업을 수행할 수 있는 몇 가지 서비스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-228">There are several services for the SNMP application to do this.</span></span>

<span data-ttu-id="8d3a0-229">SNMP 애플리케이션은 현재 SNMP 관리자 요청이 GET(예: GET, GETNEXT 또는 GETBULK)인지 또는 이 서비스를 사용하는 SET 형식의 요청인지를 조회할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-229">The SNMP application can inquire if the current SNMP Manager request is a GET (e.g. GET, GETNEXT, or GETBULK) or SET type of request using this service:</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

<span data-ttu-id="8d3a0-230">요청이 GET 형식인 경우 애플리케이션에서 입력 커뮤니티 문자열을 SNMP 에이전트의 퍼블릭 문자열과 비교하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-230">If the request is a GET type, the application will want to compare the input community string to the SNMP Agent’s public string:</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

<span data-ttu-id="8d3a0-231">마찬가지로 요청이 SET 형식인 경우 애플리케이션은 입력 커뮤니티 문자열을 SNMP 에이전트의 프라이빗 문자열과 비교하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-231">Similarly if the request is a SET type, the application will want to compare the input community string to the SNMP Agent’s private string:</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

<span data-ttu-id="8d3a0-232">is_public 및 is_private 반환 값은 입력 커뮤니티 문자열이 유효한 퍼블릭 또는 프라이빗 커뮤니티 문자열인지 여부를 각각 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-232">The is_public and is_private return values indicate respectively if the input community string is a valid public or private community string.</span></span>

<span data-ttu-id="8d3a0-233">사용자 이름 콜백 루틴의 반환 값은 사용자 이름이 유효한지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-233">The return value of the username callback routine indicates if the username is valid.</span></span> <span data-ttu-id="8d3a0-234">사용자 이름이 유효한 경우 **NX_SUCCESS** 값이 반환되고, 사용자 이름이 잘못된 경우 **NX_SNMP_ERROR** 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-234">The value **NX_SUCCESS** is returned if the username is valid, or **NX_SNMP_ERROR** if the username is invalid.</span></span>

## <a name="netx-duo-snmp-agent-get-callback"></a><span data-ttu-id="8d3a0-235">NetX Duo SNMP 에이전트 GET 콜백</span><span class="sxs-lookup"><span data-stu-id="8d3a0-235">NetX Duo SNMP Agent GET Callback</span></span>

<span data-ttu-id="8d3a0-236">애플리케이션은 SNMP 관리자에서 GET 개체 요청을 처리하기 위한 콜백 루틴을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-236">The application must set a callback routine for handling GET object requests from the SNMP Manager.</span></span> <span data-ttu-id="8d3a0-237">콜백은 요청에 지정된 개체의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-237">The callback retrieves the value of the object specified in the request.</span></span>

<span data-ttu-id="8d3a0-238">애플리케이션 GET 요청 콜백 루틴은 아래와 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-238">The application GET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="8d3a0-239">입력 매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-239">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="8d3a0-240">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8d3a0-240">Parameter</span></span>        | <span data-ttu-id="8d3a0-241">의미</span><span class="sxs-lookup"><span data-stu-id="8d3a0-241">Meaning</span></span> |
|------------------|----------------------------------|
| <span data-ttu-id="8d3a0-242">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="8d3a0-242">*agent_ptr*</span></span>        | <span data-ttu-id="8d3a0-243">SNMP 에이전트 호출에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8d3a0-243">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="8d3a0-244">object_requested</span><span class="sxs-lookup"><span data-stu-id="8d3a0-244">object_requested</span></span> | <span data-ttu-id="8d3a0-245">GET 작업이 사용되는 개체 ID를 나타내는 ASCII 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-245">ASCII string representing the object ID the GET operation is for.</span></span> |
| <span data-ttu-id="8d3a0-246">object_data</span><span class="sxs-lookup"><span data-stu-id="8d3a0-246">object_data</span></span>      | <span data-ttu-id="8d3a0-247">콜백에서 검색한 값을 저장할 데이터 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-247">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="8d3a0-248">이는 아래에서 설명하는 일련의 NetX Duo SNMP API를 사용하여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-248">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

> [!NOTE]
> <span data-ttu-id="8d3a0-249">옥텟 문자열의 경우 콜백 자체에 길이 인수가 없기 때문에 내부 함수가 길이를 알 수 있도록 개체에 길이를 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-249">*For octet strings, the object must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:*</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="8d3a0-250">데이터 형식이 GET 콜백에 알려지지 않았기 때문에 데이터 형식을 확인할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-250">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="8d3a0-251">길이는 null로 구분된 숫자 형식 또는 문자열에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-251">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="8d3a0-252">그런 다음, 내부 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-252">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="8d3a0-253">콜백 함수에서 요청된 개체를 찾을 수 없는 경우 **NX_SNMP_ERROR_NOSUCHNAME** 오류 코드가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-253">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="8d3a0-254">다른 오류가 검색되면 **NX_SNMP_ERROR** 는 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-254">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-getnext-callback"></a><span data-ttu-id="8d3a0-255">NetX Duo SNMP 에이전트 GETNEXT 콜백</span><span class="sxs-lookup"><span data-stu-id="8d3a0-255">NetX Duo SNMP Agent GETNEXT Callback</span></span>

<span data-ttu-id="8d3a0-256">또한 애플리케이션은 SNMP 관리자에서 GETNEXT 개체 요청에 대한 콜백 루틴을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-256">The application must also set the callback routine for GETNEXT object requests from the SNMP Manager.</span></span> <span data-ttu-id="8d3a0-257">GETNEXT 콜백은 요청에 의해 지정된 다음 개체의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-257">The GETNEXT callback retrieves the value of the next object specified by the request.</span></span>

<span data-ttu-id="8d3a0-258">애플리케이션 GETNEXT 요청 콜백 루틴은 아래와 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-258">The application GETNEXT request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="8d3a0-259">입력 매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-259">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="8d3a0-260">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8d3a0-260">Parameter</span></span>        | <span data-ttu-id="8d3a0-261">의미</span><span class="sxs-lookup"><span data-stu-id="8d3a0-261">Meaning</span></span> |
|------------------|-------------------------------------------|
| <span data-ttu-id="8d3a0-262">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="8d3a0-262">*agent_ptr*</span></span>        | <span data-ttu-id="8d3a0-263">SNMP 에이전트 호출에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8d3a0-263">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="8d3a0-264">object_requested</span><span class="sxs-lookup"><span data-stu-id="8d3a0-264">object_requested</span></span> | <span data-ttu-id="8d3a0-265">GETNEXT 작업이 사용되는 개체 ID를 나타내는 ASCII 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-265">ASCII string representing the object ID the GETNEXT operation is for.</span></span> |
| <span data-ttu-id="8d3a0-266">object_data</span><span class="sxs-lookup"><span data-stu-id="8d3a0-266">object_data</span></span>      | <span data-ttu-id="8d3a0-267">콜백에서 검색한 값을 저장할 데이터 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-267">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="8d3a0-268">이는 아래에서 설명하는 일련의 NetX Duo SNMP API를 사용하여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-268">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="8d3a0-269">GET 콜백의 경우와 마찬가지로, 콜백 자체에 길이 인수가 없기 때문에 내부 함수에서 길이를 알 수 있도록 옥텟 문자열 데이터가 있는 개체에 길이를 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-269">Same as is true for GET callbacks, objects with octet string data must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="8d3a0-270">데이터 형식이 GET 콜백에 알려지지 않았기 때문에 데이터 형식을 확인할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-270">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="8d3a0-271">길이는 null로 구분된 숫자 형식 또는 문자열에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-271">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="8d3a0-272">그런 다음, 내부 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-272">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="8d3a0-273">콜백 함수에서 요청된 개체를 찾을 수 없는 경우 **NX_SNMP_ERROR_NOSUCHNAME** 오류 코드가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-273">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="8d3a0-274">다른 오류가 검색되면 **NX_SNMP_ERROR** 는 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-274">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-set-callback"></a><span data-ttu-id="8d3a0-275">NetX Duo SNMP 에이전트 SET 콜백</span><span class="sxs-lookup"><span data-stu-id="8d3a0-275">NetX Duo SNMP Agent SET Callback</span></span>

<span data-ttu-id="8d3a0-276">애플리케이션은 SNMP 관리자에서 SET 개체 요청을 처리하기 위한 콜백 루틴을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-276">The application should set the callback routine for handling SET object requests from the SNMP Manager.</span></span> <span data-ttu-id="8d3a0-277">SET 콜백은 요청에 의해 지정된 개체의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-277">The SET callback sets the value of the object specified by the request.</span></span>

<span data-ttu-id="8d3a0-278">애플리케이션 SET 요청 콜백 루틴은 아래와 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-278">The application SET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="8d3a0-279">입력 매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-279">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="8d3a0-280">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8d3a0-280">Parameter</span></span>        | <span data-ttu-id="8d3a0-281">의미</span><span class="sxs-lookup"><span data-stu-id="8d3a0-281">Meaning</span></span> |
|------------------|-------- |
| <span data-ttu-id="8d3a0-282">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="8d3a0-282">*agent_ptr*</span></span>      | <span data-ttu-id="8d3a0-283">SNMP 에이전트 호출에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8d3a0-283">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="8d3a0-284">object_requested</span><span class="sxs-lookup"><span data-stu-id="8d3a0-284">object_requested</span></span> | <span data-ttu-id="8d3a0-285">SET 작업이 사용되는 개체 ID를 나타내는 ASCII 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-285">ASCII string representing the object ID the SET operation is for.</span></span> |
| <span data-ttu-id="8d3a0-286">object_data</span><span class="sxs-lookup"><span data-stu-id="8d3a0-286">object_data</span></span>      | <span data-ttu-id="8d3a0-287">지정된 개체에 대한 새 값을 포함하는 데이터 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-287">Data structure that contains the new value for the specified object.</span></span> <span data-ttu-id="8d3a0-288">실제 작업은 아래에 설명된 NetX Duo SNMP API를 사용하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-288">The actual operation can be done using the NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="8d3a0-289">옥텟 문자열의 경우 SNMP 에이전트가 데이터를 구문 분석했고 형식과 길이를 알고 있기 때문에 SET 콜백은 데이터의 길이로 MIB 테이블을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-289">Note that for octet strings, the SET callback should update the MIB table with the length of the data since the SNMP Agent has parsed the data and knows the type and length:</span></span>

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

<span data-ttu-id="8d3a0-290">콜백 함수에서 요청된 개체를 찾을 수 없는 경우 **NX_SNMP_ERROR_NOSUCHNAME** 오류 코드가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-290">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span>

<span data-ttu-id="8d3a0-291">NetX Duo SNMP 호스트가 프라이빗 커뮤니티 문자열을 만들었으나 SET 요청의 SNMP 발신자에 일치하는 프라이빗 문자열이 없으면 **NX_SNMP_ERROR_NOACCESS** 오류를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-291">If the NetX Duo SNMP host has created private community strings, and the SNMP sender of the SET request does not have the matching private string, it may return an **NX_SNMP_ERROR_NOACCESS** error.</span></span> <span data-ttu-id="8d3a0-292">다른 오류가 검색되면 **NX_SNMP_ERROR** 는 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-292">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

> [!NOTE]
> <span data-ttu-id="8d3a0-293">NetX Duo SNMP 에이전트는 배포에 SNMP MIB 데이터베이스를 함께 제공하지만, 주로 테스트 및 개발을 목적으로 사용됩니다. 개발자는 전문 SNMP 애플리케이션을 위한 전용 MIB 데이터베이스가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-293">*Although NetX Duo SNMP Agent supplies an SNMP MIB database with the distribution, it is primarily for testing and development purposes. The developer will likely require a proprietary MIB database for a professional SNMP application.*</span></span>

## <a name="changing-snmp-version-at-run-time"></a><span data-ttu-id="8d3a0-294">런타임에 SNMP 버전 변경</span><span class="sxs-lookup"><span data-stu-id="8d3a0-294">Changing SNMP Version at Run Time</span></span>

<span data-ttu-id="8d3a0-295">SNMP 에이전트 호스트는 런타임에 *nx_snmp_agent_set_version* 서비스를 사용하여 세 버전 각각에 대한 SNMP 버전을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-295">The SNMP Agent host can change SNMP version for each of the three versions at run time using the *nx_snmp_agent_set_version* service.</span></span> <span data-ttu-id="8d3a0-296">SNMP 에이전트는 *nx_snmp_agent_create* 에서 SNMP 에이전트가 만들어지면 세 가지 버전 모두에 대해 기본적으로 사용할 수 있도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-296">The SNMP Agent is by default enabled for all three versions when the SNMP Agent is created in *nx_snmp_agent_create*.</span></span> <span data-ttu-id="8d3a0-297">그러나 애플리케이션은 이를 모든 버전의 하위 집합으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-297">However, the application can limit that to a subset of all versions.</span></span>

> [!NOTE]
> <span data-ttu-id="8d3a0-298">NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 및/또는 NX_SNMP_DISABLE_V3 구성 옵션이 정의된 경우 이 함수는 영향을 받는 버전을 사용하도록 설정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-298">*If the configuration options NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 and/or NX_SNMP_DISABLE_V3 are defined, this function will have no effect enabling the effected versions.*</span></span>

<span data-ttu-id="8d3a0-299">SNMP 에이전트는 *nx_snmp_agent_get_current_version* 서비스를 사용하여 수신된 최신 SNMP 패킷의 SNMP 버전을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-299">The SNMP Agent can retrieve the SNMP version of the latest SNMP packet received using the *nx_snmp_agent_get_current_version* service.</span></span>

## <a name="snmpv3-discovery"></a><span data-ttu-id="8d3a0-300">SNMP 버전 3 검색</span><span class="sxs-lookup"><span data-stu-id="8d3a0-300">SNMPv3 Discovery</span></span>

<span data-ttu-id="8d3a0-301">SNMP 버전 3에 대해 사용하도록 설정된 경우 SNMP 에이전트는 SNMP 관리자의 검색 요청에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-301">The SNMP Agent, if enabled for SNMPv3, will respond to discovery requests from the SNMP Manager.</span></span> <span data-ttu-id="8d3a0-302">해당 요청에는 신뢰할 수 있는 엔진 ID, 사용자 이름, 부팅 횟수 및 부팅 시간에 대한 null 값을 포함한 보안 매개 변수 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-302">Such a request contains security parameter data with null values for Authoritative Engine ID, user name, boot count and boot time.</span></span> <span data-ttu-id="8d3a0-303">인증 매개 변수는 검색 메시지에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-303">Authentication parameters are not applied to the DISCOVERY message.</span></span> <span data-ttu-id="8d3a0-304">요청의 변수 바인딩 목록이 비어있습니다(항목 0개 포함).</span><span class="sxs-lookup"><span data-stu-id="8d3a0-304">The variable binding list in the request is empty (contains zero items).</span></span> <span data-ttu-id="8d3a0-305">SNMP 에이전트는 0번의 부팅 시간 및 횟수 및 알 수 없는(null) 엔진 ID로 받은 요청인 1개 항목(*usmStatsUnknownEngineIDs*)을 포함하는 변수 바인딩 목록으로 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-305">The SNMP agent responds with a zero boot time and count, and the variable binding list containing 1 item, *usmStatsUnknownEngineIDs*, which is the count of requests received with an unknown (null) engine ID.</span></span> <span data-ttu-id="8d3a0-306">브라우저/관리자의 후속 GETNEXT 요청에는 보안을 사용하도록 설정된 경우에만 부팅 데이터 및 보안 매개 변수가 입력됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-306">On the subsequent GETNEXT request from the Browser/Manager, the boot data and security parameters are filled in only if security is enabled.</span></span> <span data-ttu-id="8d3a0-307">이 경우에는 PDU에서 NotInTime 데이터 업데이트도 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-307">If so it will also send a NotInTime data update in the PDU.</span></span> <span data-ttu-id="8d3a0-308">인증과 같은 보안 매개 변수는 에이전트 ID를 관리자에게 증명합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-308">The security parameters, e.g. authentication prove the identity of the Agent to the Manager.</span></span>

<span data-ttu-id="8d3a0-309">SNMP 버전 3 인증에 대한 자세한 내용은 RFC 3414 “SNMPv3(Simple Network Management Protocol 버전 3)에 대한 USM(사용자 기반 보안 모델)”에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-309">More detailed information on SNMPv3 authentication is available in RFC 3414 “User-based Security Model (USM) for version 3 of the Simple Network Management Protocol (SNMPv3)”.</span></span>

## <a name="netx-duo-snmp-rfcs"></a><span data-ttu-id="8d3a0-310">NetX Duo SNMP RFC</span><span class="sxs-lookup"><span data-stu-id="8d3a0-310">NetX Duo SNMP RFCs</span></span>

<span data-ttu-id="8d3a0-311">NetX Duo SNMP는 RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 및 관련 RFC를 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="8d3a0-311">NetX Duo SNMP is compliant with RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 and related RFCs.</span></span>
