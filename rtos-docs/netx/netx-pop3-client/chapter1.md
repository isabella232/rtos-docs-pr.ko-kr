---
title: 1장 - Azure RTOS NetX POP3 클라이언트 소개
description: Azure RTOS NetX POP3 클라이언트 API는 소규모 워크스테이션이 클라이언트 메일 검색을 위해 POP3 서버에서 클라이언트 maildrop에 액세스할 수 있게 메일 전송 시스템을 제공합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 135530f11f8f54acd6d093a05332056dbdc32be3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811485"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3-client"></a><span data-ttu-id="db729-103">1장 - Azure RTOS NetX POP3 클라이언트 소개</span><span class="sxs-lookup"><span data-stu-id="db729-103">Chapter 1 - Introduction to Azure RTOS NetX POP3 Client</span></span>

<span data-ttu-id="db729-104">POP3(Post Office Protocol 버전 3)는 작은 워크스테이션이 클라이언트 메일을 검색하기 위해 POP3 서버의 클라이언트 maildrop에 액세스할 수 있는 메일 전송 시스템을 제공하도록 설계된 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="db729-104">The Post Office Protocol Version 3 (POP3) is a protocol designed to provide a mail transport system for small workstations to access Client maildrops on POP3 Servers for retrieving Client mail.</span></span> <span data-ttu-id="db729-105">POP3에서는 TCP(전송 제어 프로토콜) 서비스를 활용하여 메일 전송을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-105">POP3 utilizes Transmission Control Protocol (TCP) services to perform mail transfer.</span></span> <span data-ttu-id="db729-106">따라서 POP3는 매우 안정적인 콘텐츠 전송 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="db729-106">Because of this, POP3 is a highly reliable content transfer protocol.</span></span>

<span data-ttu-id="db729-107">그러나 POP3는 메일 처리에 대한 광범위한 작업을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-107">However, POP3 is does not provide extensive operations on mail handling.</span></span> <span data-ttu-id="db729-108">일반적으로 메일은 클라이언트에서 다운로드된 다음, 서버의 maildrop에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="db729-108">Typically, mail is downloaded by the Client and then deleted from the Server's maildrop.</span></span>

## <a name="netx-pop3-client-requirements"></a><span data-ttu-id="db729-109">NetX POP3 클라이언트 요구 사항</span><span class="sxs-lookup"><span data-stu-id="db729-109">NetX POP3 Client Requirements</span></span>

### <a name="client-requirements"></a><span data-ttu-id="db729-110">클라이언트 요구 사항</span><span class="sxs-lookup"><span data-stu-id="db729-110">Client Requirements</span></span>

<span data-ttu-id="db729-111">Azure RTOS NetX POP3 클라이언트 API에는 *nx_ip_create* 를 사용하여 이전에 만든 NetX IP 인스턴스와 *nx_packet_pool_create* 를 사용하여 이전에 만든 NetX 패킷 풀이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-111">The Azure RTOS NetX POP3 Client API requires a previously created NetX IP instance using *nx_ip_create* and a previously created NetX packet pool using *nx_packet_pool_create*.</span></span> <span data-ttu-id="db729-112">NetX POP3 클라이언트는 TCP 서비스를 사용하므로, 동일한 IP 인스턴스에서 NetX POP3 클라이언트 서비스를 사용하기 전에 *nx_tcp_enable* 호출을 통해 TCP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-112">Because the NetX POP3 Client utilizes TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using the NetX POP3 Client services on that same IP instance.</span></span> <span data-ttu-id="db729-113">POP3 클라이언트는 TCP 소켓을 사용하여 서버의 POP3 포트에서 POP3 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-113">The POP3 Client uses a TCP socket to connect to a POP3 Server on the Server's POP3 port.</span></span> <span data-ttu-id="db729-114">이는 일반적으로 *잘 알려진 포트 110에서 설정되지만 이 포트를 사용하는 데는 POP3 클라이언트나 서버가 필요하지 않습니다.*</span><span class="sxs-lookup"><span data-stu-id="db729-114">This is typically set at the *well-known port 110, though neither POP3 Client nor Server is required to use this port.*</span></span>

<span data-ttu-id="db729-115">POP3 클라이언트를 만드는 데 사용되는 패킷 풀의 크기는 패킷 페이로드의 측면에서 사용자 구성 가능하고 사용 가능한 패킷 수와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-115">The size of the packet pool used in creating the POP3 Client is user configurable in terms of packet payload and number of packets available.</span></span> <span data-ttu-id="db729-116">패킷이 POP3 클라이언트 만들기 서비스에서만 사용되는 경우 사용자 이름 및 암호의 길이 또는 APOP 다이제스트의 길이에 따라 패킷 페이로드가 100-120바이트를 초과할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-116">If the packet is used only in the POP3 Client create service, the packet payload need not be more than 100-120 bytes depending on the length of username and password, or APOP digest.</span></span> <span data-ttu-id="db729-117">로컬 호스트의 사용자 이름이 있는 USER 명령은 POP3 클라이언트에서 보낸 가장 큰 메시지일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-117">The USER command with the local host's user name is probably the largest message sent by the POP3 Client.</span></span> <span data-ttu-id="db729-118">IP 내부 작업은 TCP 제어 데이터를 보내고 받는 데 매우 큰 패킷 페이로드가 필요하지 않으므로 nx_ip_create(IP 기본 패킷 풀)에서 동일한 패킷 풀을 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-118">It is possible to share the same packet pool in the nx_ip_create (IP default packet pool) since the IP internal operations do not require a very large packet payload for sending and receiving TCP control data.</span></span>

<span data-ttu-id="db729-119">그러나 이더넷 드라이버가 POP3 클라이언트 패킷 풀과 동일한 패킷 풀을 사용하는 것이 유용하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-119">However, it may not be advantageous for the network driver to use the same packet pool as the POP3 Client packet pool.</span></span> <span data-ttu-id="db729-120">일반적으로 수신 패킷 풀 페이로드의 페이로드는 POP3 클라이언트 메시지보다 훨씬 큰 네트워크 인터페이스의 IP 인스턴스 MTU(일반적으로 1500바이트)를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-120">Generally, the payload of the receive packet pool payload is set the IP instance MTU (typically 1500 bytes) of the network interface which is much larger than POP3 Client messages.</span></span> <span data-ttu-id="db729-121">들어오는 POP3 메시지는 일반적으로 나가는 POP3 클라이언트 메시지보다 훨씬 더 큰 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="db729-121">Incoming POP3 messages would usually be much larger data then outgoing POP3 Client messages</span></span>

## <a name="netx-pop3-client-creation"></a><span data-ttu-id="db729-122">NetX POP3 클라이언트 만들기</span><span class="sxs-lookup"><span data-stu-id="db729-122">NetX POP3 Client Creation</span></span>

<span data-ttu-id="db729-123">POP3 클라이언트 만들기 서비스 *nx_pop3_client_create* 는 TCP 소켓을 만들고 POP3 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-123">The POP3 Client create service, *nx_pop3_client_create* create the TCP socket and connect with the POP3 server.</span></span>

<span data-ttu-id="db729-124">POP3 서버와 연결한 후 POP3 클라이언트 애플리케이션은 *nx_pop3_client _mail_items_get* 을 호출하여 해당 maildrop 상자에 있는 메일 항목 수를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-124">After connecting with the POP3 server, the POP3 Client application can call *nx_pop3_client _mail_items_get* to obtain the number of mail items sitting in its maildrop box:</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

<span data-ttu-id="db729-125">하나 이상의 항목이 클라이언트 maildrop에 있는 경우 애플리케이션은 *nx_pop3_client_get_mail_item* 서비스를 사용하여 특정 메일 항목의 크기를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-125">If one or more items are in the Client maildrop, the application can obtain the size of a specific mail item, using the *nx_pop3_client_get_mail_item* service:</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item,
                                ULONG *item_size)
```

<span data-ttu-id="db729-126">maildrop의 첫 번째 메일 항목은 인덱스 1에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-126">The first mail item in the maildrop is at index 1.</span></span>

<span data-ttu-id="db729-127">실제 메일 메시지를 가져오기 위해 애플리케이션은 서비스에서 final_packet 입력 인수가 마지막 패킷을 수신했음을 확인할 때까지 *nx_pop3_client_mail_item_get_message_data* 서비스를 호출하여 메일 메시지 패킷을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-127">To get the actual mail message, the application can call the *nx_pop3_client_mail_item_get_message_data* service to retrieve the mail message packets until the service indicates the last packet is received by the final_packet input argument:</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                        NX_POP3_CLIENT *client_ptr,
                        NX_PACKET **recv_packet_ptr,
                        ULONG *bytes_retrieved,
                        UINT *final_packet)
```

<span data-ttu-id="db729-128">특정 메일 항목을 삭제하기 위해 애플리케이션은 위의 *nx_pop3_client_get_mail_item* 호출에서 사용되는 것과 동일한 인덱스를 사용하여 *nx_pop3_client_mail_item_delete* 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-128">To delete a specific mail item, the application calls *nx_pop3_client_mail_item_delete* with the same index as used in the preceding *nx_pop3_client_get_mail_item* call.</span></span>

<span data-ttu-id="db729-129">클라이언트는 *nx_pop3_client_delete* 서비스를 사용하여 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-129">The Client can be deleted using the *nx_pop3_client_delete* service.</span></span> <span data-ttu-id="db729-130">애플리케이션에서 *nx_packet_pool_delete* 서비스를 사용하여 POP3 클라이언트 패킷 풀을 삭제하는 것은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-130">Note it is up to the application to delete the POP3 Client packet pool using the *nx_packet_pool_delete* service there is no longer has any use for it.</span></span>

## <a name="netx-pop3-client-constraints"></a><span data-ttu-id="db729-131">NetX POP3 클라이언트 제약 조건</span><span class="sxs-lookup"><span data-stu-id="db729-131">NetX POP3 Client Constraints</span></span>

<span data-ttu-id="db729-132">NetX POP3 클라이언트 구현에는 다음과 같은 몇 가지 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-132">There are some constraints in the NetX POP3 Client implementation:</span></span>

1. <span data-ttu-id="db729-133">NetX POP3 클라이언트는 AUTH 명령을 지원하지 않습니다. 단, 클라이언트 서버 인증 교환에는 DIGEST-MD5를 사용하여 APOP 인증을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-133">The NetX POP3 Client does not support the AUTH command although it does implement APOP authentication using DIGEST-MD5 for the Client Server authentication exchange.</span></span>

1. <span data-ttu-id="db729-134">NetX POP3 클라이언트는 모든 POP3 명령(예: TOP 또는 UIDL 명령)을 구현하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-134">NetX POP3 Client does not implement all POP3 commands (e.g. the TOP or UIDL commands).</span></span> <span data-ttu-id="db729-135">다음은 지원되는 명령 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="db729-135">Below is a list of commands it does support:</span></span>
   - <span data-ttu-id="db729-136">NOOP</span><span class="sxs-lookup"><span data-stu-id="db729-136">NOOP</span></span>
   - <span data-ttu-id="db729-137">RSET</span><span class="sxs-lookup"><span data-stu-id="db729-137">RSET</span></span>

## <a name="netx-pop3-client-login"></a><span data-ttu-id="db729-138">NetX POP3 클라이언트 로그인</span><span class="sxs-lookup"><span data-stu-id="db729-138">NetX POP3 Client Login</span></span>

<span data-ttu-id="db729-139">NetX POP3 클라이언트는 maildrop에 액세스하기 위해 자체(로그인)를 POP3 서버에 인증해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-139">A NetX POP3 Client must authenticate itself (login) to a POP3 Server to access a maildrop.</span></span> <span data-ttu-id="db729-140">USER/PASS 명령을 사용하고 POP3 서버에 알려진 사용자 이름과 암호를 제공하거나 아래에 설명된 APOP 명령 및 MD5 다이제스트를 사용하여 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-140">It can do so either by using the USER/PASS commands and providing a username and password known to the POP3 Server, or by using the APOP command and MD5 digest described below.</span></span>

<span data-ttu-id="db729-141">사용자 이름은 일반적으로 정규화된 도메인 이름입니다. 여기에는 ‘@’ 문자로 구분된 로컬 부분과 도메인 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="db729-141">The username is typically a fully qualified domain name (contains a local-part and a domain name, separated by an '@' character).</span></span> <span data-ttu-id="db729-142">POP3 명령 USER 및 PASS를 사용하는 경우 클라이언트는 인터넷을 통해 암호화되지 않은 해당 사용자 이름과 암호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="db729-142">When using the POP3 commands USER and PASS, the Client is sending its username and password unencrypted over the Internet.</span></span>

<span data-ttu-id="db729-143">일반 텍스트 사용자 이름 및 암호의 보안 위험을 방지하기 위해 *nxd_pop3_client_create* 서비스에서 *APOP_authentication* 매개 변수를 설정하여 APOP 인증을 사용하도록 NetX POP3 클라이언트를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-143">To avoid the security risk of clear texting username and password, the NetX POP3 Client can be configured to use APOP authentication by setting the *APOP_authentication* parameter in the *nx_pop3_client_create* service:</span></span>

```c
UINT  nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            NXD_ADDRESS *server_ip_address, ULONG server_port,
                            CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="db729-144">또는 IPv4 전용 애플리케이션의 경우 *nx_pop3_client_create* 서비스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-144">Or for IPv4 only applications, the *nx_pop3_client_create* service:</span></span>

```c
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            ULONG server_ip_address,
                            ULONG server_port, CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="db729-145">클라이언트가 APOP 명령을 보내면 서버 인사말로부터 추출된 서버 도메인, 로컬 시간 및 프로세스 ID를 포함하는 MD5 다이제스트와, 클라이언트 암호를 취합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-145">When the Client sends the APOP command, it takes an MD5 digest containing the server domain, local time and process ID extracted from the Server greeting, plus the Client password.</span></span> <span data-ttu-id="db729-146">POP3 서버는 동일한 정보를 포함하는 MD5 다이제스트를 만들며 해당 MD5 다이제스트가 클라이언트의 MD5 다이제스트와 일치하는 경우 클라이언트가 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="db729-146">The POP3 Server will create an MD5 digest containing the same information and if its MD5 digest matches the Client's MD5 digest, the Client is authenticated.</span></span>

<span data-ttu-id="db729-147">APOP 인증이 실패하는 경우 NetX POP3 클라이언트는 USER/PASS 인증을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-147">If APOP authentication fails, NetX POP3 Client will attempt USER/PASS authentication.</span></span>

## <a name="the-pop3-client-maildrop"></a><span data-ttu-id="db729-148">POP3 클라이언트 Maildrop</span><span class="sxs-lookup"><span data-stu-id="db729-148">The POP3 Client Maildrop</span></span>

<span data-ttu-id="db729-149">클라이언트 메일은 POP3 서버에 사서함 또는 “maildrop”으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="db729-149">Client mail is stored on a POP3 Server in a mailbox or "maildrop."</span></span> <span data-ttu-id="db729-150">POP3 서버의 클라이언트 maildrop은 1개의 기반 메일 항목 목록으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db729-150">A Client maildrop on a POP3 Server is represented as a 1 based list of mail items.</span></span> <span data-ttu-id="db729-151">즉, 각 메일은 인덱스 1(0이 아님)의 첫 번째 메일 항목을 사용하여 maildrop 목록의 해당 인덱스에 의해 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="db729-151">That is, each mail is referred to by its index in the maildrop list with the first mail item at index 1 (not zero).</span></span> <span data-ttu-id="db729-152">POP3 명령은 이 목록에서 해당 인덱스별로 특정 메일 항목을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-152">POP3 commands refer to specific mail items by their index in this list.</span></span>

## <a name="the-pop3-protocol-state-machine"></a><span data-ttu-id="db729-153">POP3 프로토콜 상태 시스템</span><span class="sxs-lookup"><span data-stu-id="db729-153">The POP3 Protocol State Machine</span></span>

<span data-ttu-id="db729-154">POP3 프로토콜을 사용하려면 클라이언트와 서버 모두에서 POP3 세션의 상태를 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-154">The POP3 protocol requires that both Client and Server maintain the state of the POP3 session.</span></span> <span data-ttu-id="db729-155">먼저 클라이언트가 POP3 서버에 연결을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-155">First, the Client attempts to connect to the POP3 Server.</span></span> <span data-ttu-id="db729-156">성공하면 RFC 1939에 정의된 세 가지 고유한 상태를 가진 POP3 프로토콜에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-156">If successful it enters into the POP3 protocol which has three distinct states defined by RFC 1939.</span></span> <span data-ttu-id="db729-157">초기 상태는 서버에서 자신을 식별해야 하는 권한 부여 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="db729-157">The initial state is the Authorization state in which it must identify itself to the Server.</span></span> <span data-ttu-id="db729-158">권한 부여 상태에서 POP3 클라이언트는 USER 및 PASS 명령, 해당 순서 또는 APOP 명령만 발급할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-158">In the Authorization state, the POP3 Client can only issue the USER and the PASS commands, and in that order, or the APOP command.</span></span>

<span data-ttu-id="db729-159">POP3 클라이언트가 인증되면 클라이언트 세션이 트랜잭션 상태로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="db729-159">Once the POP3 Client is authenticated, the Client session enters the Transaction state.</span></span> <span data-ttu-id="db729-160">이 상태에서 클라이언트는 메일 삭제를 다운로드하고 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-160">In this state, the Client can download and request mail deletion.</span></span> <span data-ttu-id="db729-161">트랜잭션 상태에서 허용되는 명령은 LIST, STAT, RETR, DELE, RSET 및 QUIT입니다.</span><span class="sxs-lookup"><span data-stu-id="db729-161">The commands allowed in the Transaction state are LIST, STAT, RETR, DELE, RSET and QUIT.</span></span> <span data-ttu-id="db729-162">일반적으로 POP3 클라이언트는 STAT 명령과 일련의 RETR 명령을 차례로 보냅니다(해당 maildrop의 각 메일 항목에 대해 하나씩).</span><span class="sxs-lookup"><span data-stu-id="db729-162">Typically the POP3 Client sends a STAT command followed by a series of RETR commands (one for each mail item in its maildrop).</span></span>

<span data-ttu-id="db729-163">클라이언트가 QUIT 명령을 실행하면 POP3 세션이 서버에서 TCP 연결 끊기를 시작하는 업데이트 상태를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-163">Once the Client issues the QUIT command, the POP3 session enters the Update state in which it initiates the TCP disconnect from the Server.</span></span> <span data-ttu-id="db729-164">나중에 메일을 다운로드하기 위해 POP3 클라이언트 애플리케이션이 언제든 `nx_pop3_client_mail_items_get`을 호출하여 maildrop의 새 메일을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-164">To download mail later, the POP3 Client application may call `nx_pop3_client_mail_items_get` at any time to check for new mail in the maildrop.</span></span>

### <a name="pop3-server-reply-codes"></a><span data-ttu-id="db729-165">POP3 서버 회신 코드</span><span class="sxs-lookup"><span data-stu-id="db729-165">POP3 Server Reply Codes</span></span>

- <span data-ttu-id="db729-166">**+OK**: 서버에서 이 회신을 사용하여 클라이언트 명령을 수락합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-166">**+OK**: The Server uses this reply to accept a Client command.</span></span> <span data-ttu-id="db729-167">서버는 ‘+OK’ 이후의 추가 정보를 포함할 수 있지만 메일 메시지 데이터를 다운로드하는 경우나 LIST 또는 DELE 명령을 제외하고 클라이언트가 이 정보를 처리한다고 간주할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-167">The Server can include additional information after the '+OK' but cannot assume the Client will process this information, except in the case of downloading mail message data or the LIST or DELE commands.</span></span> <span data-ttu-id="db729-168">후자의 경우 명령 뒤의 '인수'는 클라이언트 maildrop에서 메일 항목의 인덱스를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-168">In the latter case, the 'argument' after the command references the index of the mail item in the Client maildrop.</span></span>

- <span data-ttu-id="db729-169">**-ERR**: 서버에서 이 회신을 사용하여 클라이언트 명령을 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-169">**-ERR**: The Server uses this reply to reject a Client command.</span></span> <span data-ttu-id="db729-170">서버는 ‘-ERR’ 다음에 추가 정보를 보낼 수 있지만 클라이언트가 이 정보를 처리한다고 간주할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db729-170">The Server may send additional information following the '-ERR' but cannot assume the Client will process this information.</span></span>

### <a name="sample-pop3-client---server-session"></a><span data-ttu-id="db729-171">샘플 POP3 클라이언트 - 서버 세션</span><span class="sxs-lookup"><span data-stu-id="db729-171">Sample POP3 Client - Server Session</span></span>

<span data-ttu-id="db729-172">**USER/PASS를 사용하는 기본 POP3 예제:**</span><span class="sxs-lookup"><span data-stu-id="db729-172">**Basic POP3 example using USER/PASS:**</span></span>

```c
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: USER mrose
S: +OK mrose is valid
C: PASS mvan99
S: +OK mrose is logged in
C: STAT
S: +OK 2 320
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

<span data-ttu-id="db729-173">**APOP(STAT 대신 LIST)를 사용하는 기본 POP3 예제:**</span><span class="sxs-lookup"><span data-stu-id="db729-173">**Basic POP3 example using APOP (and LIST instead of STAT):**</span></span>

```c
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: APOP mrose c4c9334bac560ecc979e58001b3e22fb
S: +OK mrose's maildrop has 2 messages (320 octets)
C: LIST
S: +OK 2 messages (320 octets)
S: 1 120
S: 2 200
S: .
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK dewey POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

## <a name="rfcs-supported-by-netx-pop3-client"></a><span data-ttu-id="db729-174">NetX POP3 클라이언트에서 지원하는 RFC</span><span class="sxs-lookup"><span data-stu-id="db729-174">RFCs Supported by NetX POP3 Client</span></span>

<span data-ttu-id="db729-175">NetX POP3는 RFC 1939를 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="db729-175">NetX Client POP3 is compliant with RFC 1939.</span></span>
