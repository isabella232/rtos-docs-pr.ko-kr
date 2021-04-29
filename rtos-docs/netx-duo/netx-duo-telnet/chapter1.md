---
title: 1장 - Azure RTOS NetX Duo Telnet 소개
description: Azure RTOS NetX Duo Telnet은 인터넷에서 두 노드 간에 명령과 응답을 전송하기 위해 설계된 프로토콜입니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d25f5ca4a7bf1ecf4c3d0c68ef6c8aeda7800098
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810549"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-telnet"></a><span data-ttu-id="1cac4-103">1장 - Azure RTOS NetX Duo Telnet 소개</span><span class="sxs-lookup"><span data-stu-id="1cac4-103">Chapter 1 - Introduction to the Azure RTOS NetX Duo Telnet</span></span>

<span data-ttu-id="1cac4-104">Azure RTOS NetX Duo Telnet은 인터넷에서 두 노드 간에 명령과 응답을 전송하기 위해 설계된 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-104">The Azure RTOS NetX Duo Telnet is a protocol designed for transferring commands and responses between two nodes on the Internet.</span></span> <span data-ttu-id="1cac4-105">텔넷은 신뢰할 수 있는 TCP(Transmission Control Protocol) 서비스를 활용하여 전송 기능을 수행하는 간단한 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-105">Telnet is a simple protocol that utilizes reliable Transmission Control Protocol (TCP) services to perform its transfer function.</span></span> <span data-ttu-id="1cac4-106">따라서 텔넷은 매우 신뢰할 수 있는 전송 프로토콜이며,</span><span class="sxs-lookup"><span data-stu-id="1cac4-106">Because of this, Telnet is a highly reliable transfer protocol.</span></span> <span data-ttu-id="1cac4-107">가장 많이 사용되는 애플리케이션 프로토콜 중 하나이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-107">Telnet is also one of the most used application protocols.</span></span>

## <a name="telnet-requirements"></a><span data-ttu-id="1cac4-108">텔넷 요구 사항</span><span class="sxs-lookup"><span data-stu-id="1cac4-108">Telnet Requirements</span></span>

<span data-ttu-id="1cac4-109">NetX Duo Telnet 패키지를 제대로 작동하려면 NetX IP 인스턴스가 이미 만들어져 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-109">In order to function properly, the NetX Duo Telnet package requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="1cac4-110">또한 동일한 IP 인스턴스에서 TCP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-110">In addition, TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="1cac4-111">NetX Duo Telnet 패키지의 텔넷 클라이언트 부분에는 추가 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-111">The Telnet Client portion of the NetX Duo Telnet package has no further requirements.</span></span>

<span data-ttu-id="1cac4-112">NetX Duo Telnet 패키지의 텔넷 서버 부분에는 추가 요구 사항이 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-112">The Telnet Server portion of the NetX Duo Telnet package has one additional requirement.</span></span> <span data-ttu-id="1cac4-113">모든 클라이언트 텔넷 요청을 처리하려면 TCP의 ‘잘 알려진 포트 23’에 대한 완전한 액세스 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-113">It requires complete access to TCP *well-known port 23* for handling all Client Telnet requests.</span></span>

## <a name="telnet-constraints"></a><span data-ttu-id="1cac4-114">텔넷 제약 조건</span><span class="sxs-lookup"><span data-stu-id="1cac4-114">Telnet Constraints</span></span> 

<span data-ttu-id="1cac4-115">NetX Duo Telnet 프로토콜은 텔넷 표준을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-115">The NetX Duo Telnet protocol implements the Telnet standard.</span></span> <span data-ttu-id="1cac4-116">그러나 값이 255인 바이트로 표시되는 텔넷 명령의 해석 및 응답은 애플리케이션이 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-116">However,the interpretation and response of Telnet commands, indicated by a byte with the value of 255, is the responsibility of the application.</span></span> <span data-ttu-id="1cac4-117">다양한 텔넷 명령 및 명령 매개 변수는 *nxd_telnet_client.h, nxd_telnet_server.h* 파일에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-117">The various Telnet commands and command parameters are defined in the *nxd_telnet_client.h and nxd_telnet_server.h* files.</span></span>

## <a name="telnet-communication"></a><span data-ttu-id="1cac4-118">텔넷 통신</span><span class="sxs-lookup"><span data-stu-id="1cac4-118">Telnet Communication</span></span>

<span data-ttu-id="1cac4-119">앞에서 설명한 대로 텔넷 서버는 ‘잘 알려진 TCP 포트 23’을 활용하여 클라이언트 요청을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-119">As mentioned previously, the Telnet Server utilizes the *well-known TCP port 23* to field Client requests.</span></span> <span data-ttu-id="1cac4-120">텔넷 클라이언트는 사용 가능한 모든 TCP 포트를 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-120">Telnet Clients may use any available TCP port.</span></span>

## <a name="telnet-authentication"></a><span data-ttu-id="1cac4-121">텔넷 인증</span><span class="sxs-lookup"><span data-stu-id="1cac4-121">Telnet Authentication</span></span>

<span data-ttu-id="1cac4-122">텔넷 인증은 애플리케이션의 텔넷 서버 콜백 함수가 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-122">Telnet authentication is the responsibility of the application’s Telnet Server callback function.</span></span> <span data-ttu-id="1cac4-123">애플리케이션의 텔넷 서버 “새 연결” 콜백은 일반적으로 클라이언트에 이름 및/또는 암호를 묻는 프롬프트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-123">The application’s Telnet Server “new connection” callback would typically prompt the Client for name and/or password.</span></span> <span data-ttu-id="1cac4-124">그러면 클라이언트는 정보를 제공하는 역할을 담당하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-124">The Client would then be responsible for providing the information.</span></span> <span data-ttu-id="1cac4-125">그런 다음, 서버는 “데이터 수신” 콜백의 정보를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-125">The Server would then process the information in the “receive data” callback.</span></span> <span data-ttu-id="1cac4-126">여기서 애플리케이션 서버 코드는 정보를 인증하고 그 정보가 유효한지 여부를 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-126">This is where the application Server code would have to authenticate the information and decide whether or not it is valid.</span></span>

## <a name="telnet-new-connection-callback"></a><span data-ttu-id="1cac4-127">텔넷 새 연결 콜백</span><span class="sxs-lookup"><span data-stu-id="1cac4-127">Telnet New Connection Callback</span></span>

<span data-ttu-id="1cac4-128">NetX Duo Telnet 서버는 새 텔넷 클라이언트 요청이 수신될 때마다 애플리케이션 지정 콜백 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-128">The NetX Duo Telnet Server calls the application specified callback function whenever a new Telnet Client request is received.</span></span> <span data-ttu-id="1cac4-129">애플리케이션은 ***nx_telnet_server_create*** 함수를 통해 텔넷 서버를 만들 때 콜백 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-129">The application specifies the callback function when the Telnet Server is created via the ***nx_telnet_server_create*** function.</span></span> <span data-ttu-id="1cac4-130">“새 연결” 콜백의 일반적인 작업에는 클라이언트에 배너 또는 프롬프트를 보내는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-130">Typical actions of the “new connection” callback include sending a banner or prompt to the Client.</span></span> <span data-ttu-id="1cac4-131">여기에는 로그인 정보에 대한 프롬프트를 매우 잘 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-131">This could very well include a prompt for login information.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cac4-132">프로토타입</span><span class="sxs-lookup"><span data-stu-id="1cac4-132">Prototype</span></span>

```c
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a><span data-ttu-id="1cac4-133">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1cac4-133">Input Parameters</span></span>

- <span data-ttu-id="1cac4-134">**server_ptr**: 호출하는 텔넷 서버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-134">**server_ptr**: Pointer to the calling Telnet Server.</span></span>
- <span data-ttu-id="1cac4-135">**logical_connection**: 텔넷 서버에 대한 내부 논리적 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-135">**logical_connection**: The internal logical connection for the Telnet Server.</span></span> <span data-ttu-id="1cac4-136">이는 애플리케이션에서 각 클라이언트 연결에 특정된 버퍼 및/또는 데이터 구조에 대한 인덱스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-136">This can be used by the application as an index into buffers and/or data structures specific for each Client connection.</span></span> <span data-ttu-id="1cac4-137">값 범위는 0에서 NX_TELNET_MAX_CLIENTS - 1까지입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-137">Its value ranges from 0 through NX_TELNET_MAX_CLIENTS - 1.</span></span>

## <a name="telnet-receive-data-callback"></a><span data-ttu-id="1cac4-138">텔넷 데이터 수신 콜백</span><span class="sxs-lookup"><span data-stu-id="1cac4-138">Telnet Receive Data Callback</span></span>

<span data-ttu-id="1cac4-139">NetX Duo Telnet 서버는 새 텔넷 클라이언트 데이터가 수신될 때마다 애플리케이션 지정 콜백 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-139">The NetX Duo Telnet Server calls the application specified callback function whenever a new Telnet Client data is received.</span></span> <span data-ttu-id="1cac4-140">애플리케이션은 ***nx_telnet_server_create*** 함수를 통해 텔넷 서버를 만들 때 콜백 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-140">The application specifies the callback function when the Telnet Server is created via the ***nx_telnet_server_create*** function.</span></span> <span data-ttu-id="1cac4-141">“새 연결” 콜백의 일반적인 작업에는 데이터를 다시 에코 하거나 데이터를 구문 분석하고 클라이언트에서 명령을 해석한 결과로 데이터를 제공하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-141">Typical actions of the “new connection” callback include echoing the data back and/or parsing the data and providing data as a result of interpreting a command from the client.</span></span>

<span data-ttu-id="1cac4-142">또한 이 콜백 루틴은 제공된 패킷을 릴리스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-142">Note that this callback routine must also release the supplied packet.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cac4-143">프로토타입</span><span class="sxs-lookup"><span data-stu-id="1cac4-143">Prototype</span></span>

```c
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, 
                          UINT logical_connection, NX_PACKET *packet_ptr);
```
### <a name="input-parameters"></a><span data-ttu-id="1cac4-144">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1cac4-144">Input Parameters</span></span>

- <span data-ttu-id="1cac4-145">**server_ptr**: 호출하는 텔넷 서버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-145">**server_ptr**: Pointer to the calling Telnet Server.</span></span>
- <span data-ttu-id="1cac4-146">**logical_connection**: 텔넷 서버에 대한 내부 논리적 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-146">**logical_connection**: The internal logical connection for the Telnet Server.</span></span> <span data-ttu-id="1cac4-147">이는 애플리케이션에서 각 클라이언트 연결에 특정된 버퍼 및/또는 데이터 구조에 대한 인덱스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-147">This can be used by the application as an index into buffers and/or data structures specific for each Client connection.</span></span> <span data-ttu-id="1cac4-148">값 범위는 0에서 NX_TELNET_MAX_CLIENTS - 1까지입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-148">Its value ranges from 0 through NX_TELNET_MAX_CLIENTS - 1.</span></span>
- <span data-ttu-id="1cac4-149">**packet_ptr**: 클라이언트에서 데이터를 포함하는 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-149">**packet_ptr**: Pointer to packet containing the data from the Client.</span></span>

## <a name="telnet-end-connection-callback"></a><span data-ttu-id="1cac4-150">텔넷 연결 종료 콜백</span><span class="sxs-lookup"><span data-stu-id="1cac4-150">Telnet End Connection Callback</span></span>

<span data-ttu-id="1cac4-151">NetX Duo Telnet 서버는 텔넷 클라이언트가 연결을 종료할 때마다 애플리케이션 지정 콜백 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-151">The NetX Duo Telnet Server calls the application specified callback function whenever a Telnet Client ends the connection.</span></span> <span data-ttu-id="1cac4-152">애플리케이션은 ***nx_telnet_server_create*** 함수를 통해 텔넷 서버를 만들 때 콜백 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-152">The application specifies the callback function when the Telnet Server is created via the ***nx_telnet_server_create*** function.</span></span> <span data-ttu-id="1cac4-153">“연결 종료” 콜백의 일반적인 작업에는 논리적 연결과 관련된 모든 클라이언트 특정 데이터 구조를 정리하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-153">Typical actions of the “end connection” callback include cleaning up any Client specific data structures associated with the logical connection.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cac4-154">프로토타입</span><span class="sxs-lookup"><span data-stu-id="1cac4-154">Prototype</span></span>
```c
void  telnet_end_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a><span data-ttu-id="1cac4-155">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1cac4-155">Input Parameters</span></span>

- <span data-ttu-id="1cac4-156">**server_ptr** 호출하는 텔넷 서버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-156">**server_ptr** Pointer to the calling Telnet Server.</span></span>
- <span data-ttu-id="1cac4-157">**logical_connection** 텔넷 서버에 대한 내부 논리적 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-157">**logical_connection** The internal logical connection for the Telnet Server.</span></span> <span data-ttu-id="1cac4-158">이는 애플리케이션에서 각 클라이언트 연결에 특정된 버퍼 및/또는 데이터 구조에 대한 인덱스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-158">This can be used by the application as an index into buffers and/or data structures specific for each Client connection.</span></span> <span data-ttu-id="1cac4-159">값 범위는 0에서 NX_TELNET_MAX_CLIENTS - 1까지입니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-159">Its value ranges from 0 through NX_TELNET_MAX_CLIENTS - 1.</span></span>

## <a name="telnet-option-negotiation"></a><span data-ttu-id="1cac4-160">텔넷 옵션 협상</span><span class="sxs-lookup"><span data-stu-id="1cac4-160">Telnet Option Negotiation</span></span>

<span data-ttu-id="1cac4-161">NetX Duo Telnet 서버는 제한된 텔넷 옵션 세트인 Echo 및 Suppress Go Ahead를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-161">The NetX Duo Telnet Server supports a limited set of Telnet options, Echo and Suppress Go Ahead.</span></span>

<span data-ttu-id="1cac4-162">이 기능을 사용하려면 NX_TELNET_SERVER_OPTION_DISABLE를 정의하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-162">To enable this feature the NX_TELNET_SERVER_OPTION_DISABLE must not be defined.</span></span> <span data-ttu-id="1cac4-163">기본적으로 정의되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-163">By default it is not defined.</span></span> <span data-ttu-id="1cac4-164">텔넷 서버는 *nx_telnet_server_create* 서비스에서 패킷 풀을 만들어 텔넷 옵션 요청을 클라이언트에 보내기 위한 패킷을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-164">The Telnet Server creates a packet pool in the *nx_telnet_server_create* service from which it allocates packets for sending telnet options requests to the Client.</span></span> <span data-ttu-id="1cac4-165">이 패킷 풀의 패킷 페이로드(NX_TELNET_SERVER_PACKET_PAYLOAD) 및 패킷 풀 크기(NX_TELNET_SERVER_PACKET_POOL_SIZE)를 설정하려면 “구성 옵션”을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1cac4-165">See “Configuration Options” for setting the packet payload (NX_TELNET_SERVER_PACKET_PAYLOAD) and packet pool size (NX_TELNET_SERVER_PACKET_POOL_SIZE) for this packet pool.</span></span> <span data-ttu-id="1cac4-166">*nx_telnet_server_delete* 서비스를 호출할 때 이 패킷 풀을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-166">It will delete this packet pool when the *nx_telnet_server_delete* service is called.</span></span>

<span data-ttu-id="1cac4-167">텔넷 클라이언트에 연결한 후 클라이언트로부터 옵션 요청을 받지 못한 경우 다음 텔넷 옵션 세트를 클라이언트에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-167">Upon making a connection with the Telnet Client, it will send out this set of telnet options to the Client if it has not received option requests from the Client:</span></span>

- <span data-ttu-id="1cac4-168">will echo</span><span class="sxs-lookup"><span data-stu-id="1cac4-168">will echo</span></span>
- <span data-ttu-id="1cac4-169">dont echo</span><span class="sxs-lookup"><span data-stu-id="1cac4-169">dont echo</span></span>
- <span data-ttu-id="1cac4-170">will sga</span><span class="sxs-lookup"><span data-stu-id="1cac4-170">will sga</span></span>

<span data-ttu-id="1cac4-171">클라이언트로부터 텔넷 데이터를 수신하는 경우 텔넷 서버는 첫 번째 바이트가 “IAC” 코드인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-171">When it receives Telnet data from the Client, the Telnet Server checks if the first byte is the “IAC” code.</span></span> <span data-ttu-id="1cac4-172">이런 경우 클라이언트 패킷의 모든 옵션을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-172">If so, it will process all the options in the Client packet.</span></span> <span data-ttu-id="1cac4-173">위의 목록에 없는 옵션은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-173">Options not in the list above are ignored.</span></span>

<span data-ttu-id="1cac4-174">기본적으로 NX_TELNET_SERVER_OPTION_DISABLE이 정의되어 있지 않고 텔넷 옵션 명령을 전송해야 하는 경우, 텔넷 서버는 자체 내부 패킷 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-174">By default, the Telnet Server creates its own internal packet pool if NX_TELNET_SERVER_OPTION_DISABLE is not defined and it needs to transmit Telnet option commands.</span></span> <span data-ttu-id="1cac4-175">텔넷 서버 패킷 풀은 NX_TELNET_SERVER_PACKET_PAYLOAD 및 NX_TELNET_SERVER_PACKET_POOLSIZE에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-175">The Telnet Server packet pool is defined by NX_TELNET_SERVER_PACKET_PAYLOAD and NX_TELNET_SERVER_PACKET_POOLSIZE.</span></span> <span data-ttu-id="1cac4-176">그러나 NX_TELNET_SERVER_USER_CREATE_PACKET_POOL이 정의되어 있는 경우 애플리케이션은 텔넷 서버 패킷 풀을 만들고 *_nx_telnet_server_packet_pool_set* 을 호출하여 텔넷 서버 패킷 풀로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-176">If, however, NX_TELNET_SERVER_USER_CREATE_PACKET_POOL is defined, the application must create the Telnet Server packet pool and set it as the Telnet Server packet pool by calling *_nx_telnet_server_packet_pool_set*.</span></span> <span data-ttu-id="1cac4-177">이 기능에 대한 자세한 내용은 3장 “텔넷 서비스 설명”을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1cac4-177">See Chapter 3 “Description of Telnet Services” for more details about this function.</span></span>

<span data-ttu-id="1cac4-178">NetX Duo Telnet 서버와 달리 NetX Duo Telnet 클라이언트 작업 스레드는 텔넷 서버에서 수신된 옵션을 자동으로 보내거나 응답하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-178">Unlike the NetX Duo Telnet Server, the NetX Duo Telnet Client task thread does not automatically send and respond to received options from the Telnet Server.</span></span> <span data-ttu-id="1cac4-179">이 작업은 텔넷 클라이언트 애플리케이션에서 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-179">This must be done by the Telnet Client application.</span></span>

## <a name="telnet-multi-thread-support"></a><span data-ttu-id="1cac4-180">텔넷 다중 스레드 지원</span><span class="sxs-lookup"><span data-stu-id="1cac4-180">Telnet Multi-Thread Support</span></span>

<span data-ttu-id="1cac4-181">NetX Duo Telnet Client 서비스는 다중 스레드에서 동시에 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-181">The NetX Duo Telnet Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="1cac4-182">그러나 특정 텔넷 클라이언트 인스턴스에 대한 읽기 또는 쓰기 요청은 동일한 스레드에서 순서대로 수행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-182">However, read or write requests for a particular Telnet Client instance should be done in sequence from the same thread.</span></span>

## <a name="telnet-rfcs"></a><span data-ttu-id="1cac4-183">텔넷 RFC</span><span class="sxs-lookup"><span data-stu-id="1cac4-183">Telnet RFCs</span></span>

<span data-ttu-id="1cac4-184">NetX Duo Telnet은 RFC854 및 관련 RFC를 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="1cac4-184">NetX Duo Telnet is compliant with RFC854 and related RFCs.</span></span>
