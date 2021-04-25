---
title: 챕터 3 - LWM2M 클라이언트의 기능 설명
description: 이 챕터에서는 LWM2M 클라이언트의 기능 설명을 포함합니다.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810753"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a><span data-ttu-id="8d870-103">챕터 3 - LWM2M 클라이언트의 기능 설명</span><span class="sxs-lookup"><span data-stu-id="8d870-103">Chapter 3  Functional Description of LWM2M Client</span></span>

> <span data-ttu-id="8d870-104">이 챕터에서는 LWM2M 클라이언트의 기능 설명을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-104">This chapter contains a functional description of LWM2M Client.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="8d870-105">LWM2M 클라이언트 초기화</span><span class="sxs-lookup"><span data-stu-id="8d870-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="8d870-106">LWM2M 클라이언트는 ***nx_lwm2m_client_create*** 서비스를 호출하여 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="8d870-107">LWM2M 클라이언트는 자체 스레드에서 실행되며, 콜백을 사용하거나 애플리케이션에서 구현하는 사용자 지정 개체의 메서드를 호출하여 애플리케이션에 일부 이벤트를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="8d870-108">또한 하나 이상의 서버와 통신할 수 있도록 ***nx_lwm2m_client_session_create*** 를 호출하여 LWM2M 클라이언트 세션을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="8d870-109">세션은 부트스트랩 서버 또는 LWM2M 서버(디바이스 관리)와 같은 두 가지 유형의 서버와 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="8d870-110">부트스트랩 서버 세션</span><span class="sxs-lookup"><span data-stu-id="8d870-110">Bootstrap Server Session</span></span>

<span data-ttu-id="8d870-111">LWM2M 클라이언트에 중요한 정보를 프로비전하여 LWM2M 클라이언트가 하나 이상의 LWM2M 서버에서 "Register(레지스터)" 작업을 수행할 수 있도록 하는 부트스트랩 서버와의 통신 세션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation “Register” with one or more LWM2M Servers.</span></span> <span data-ttu-id="8d870-112">이 유형의 서버는 클라이언트 시작 및 서버 시작 부트스트랩 모드를 실행하는 동안 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="8d870-113">애플리케이션은 ***nx_lwm2m_client_session_bootstrap** _ 또는 _*_nx_lwm2m_client_session_bootstrap_dtls_\*_ 를 호출하여 부트스트랩 세션을 시작할 수 있으며 서버의 IP 주소 및 포트 번호와 선택적 보안 개체 인스턴스 ID를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="8d870-114">_*_Nx_lwm2m_client_session_bootstrap_*_ 함수는 안전하지 않은 통신을 사용하지만 _ \*_nx_lwm2m_client_session_bootstrap_dtls_\*\*는 서버와의 안전한 DTLS 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="8d870-115">부트스트랩 작업에 성공하면 부트스트랩 서버에서 부트스트랩 및 LWM2M 서버에 대한 보안 개체 인스턴스와 LWM2M 서버에 대한 서버 개체 인스턴스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="8d870-116">애플리케이션은 ***nx_lwm2m_client_session_register_info_get*** 를 호출하여 LWM2M 서버 정보를 가져오고 LWM2M 서버를 사용하여 세션을 설정하는 데 이 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-116">The application can call ***nx_lwm2m_client_session_register_info_get*** to get LWM2M Server(s) information and use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="8d870-117">다음에 디바이스를 다시 부팅할 때 LWM2M 클라이언트를 구성하려면 애플리케이션의 비휘발성 메모리에 부트스트랩 데이터를 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-117">The Bootstrap data should be saved to non-volatile memory by the application to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="8d870-118">LWM2M 서버 세션</span><span class="sxs-lookup"><span data-stu-id="8d870-118">LWM2M Server Session</span></span>

<span data-ttu-id="8d870-119">LWM2M 서버와 통신 세션은 등록, 디바이스 관리 및 서비스를 사용하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="8d870-120">애플리케이션은 ***nx_lwm2m_client_session_register** _ 또는 _*_nx_lwm2m_client_session_register_dtls_\*_ 를 호출하여 서버에 LWM2M 클라이언트를 등록할 수 있습니다. 이 클라이언트는 서버의 IP 주소와 포트 번호 및 기존 서버 개체 인스턴스에 해당하는 약식 서버 ID를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="8d870-121">_*_nx_lwm2m_client_session_register_*_ 함수는 안전하지 않은 통신을 사용하지만 _ \*_nx_lwm2m_client_session_register_dtls_\*\*는 서버와의 안전한 DTLS 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas  _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="8d870-122">애플리케이션은 \***nx_lwm2m_client_session_deregister** _을(를) 호출하여 LWM2M 클라이언트를 등록 취소하고 _ \*_nx_lwm2m_client_session_update_\*\*를 호출하여 'Update(업데이트)' 메시지를 보내도록 클라이언트에 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an ‘Update’ message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="8d870-123">세션 상태 콜백</span><span class="sxs-lookup"><span data-stu-id="8d870-123">Session State Callback</span></span>

<span data-ttu-id="8d870-124">애플리케이션은 세션의 상태가 업데이트될 때 호출되는 세션을 만들 때 콜백을 등록합니다. 콜백 함수 **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** 에는 다음 프로토타입이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** has the following prototype.</span></span>

<span data-ttu-id="8d870-125">typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \* SESSION_PTR, UINT state);</span><span class="sxs-lookup"><span data-stu-id="8d870-125">typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);</span></span>

<span data-ttu-id="8d870-126">정의되는 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-126">The following states are defined.</span></span>

| <span data-ttu-id="8d870-127">세션&nbsp;상태</span><span class="sxs-lookup"><span data-stu-id="8d870-127">Session&nbsp;State</span></span> | <span data-ttu-id="8d870-128">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-128">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d870-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span><span class="sxs-lookup"><span data-stu-id="8d870-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span></span> | <span data-ttu-id="8d870-130">세션 생성 후 초기 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-130">The initial state after session creation.</span></span> |
| <span data-ttu-id="8d870-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span><span class="sxs-lookup"><span data-stu-id="8d870-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span></span> | <span data-ttu-id="8d870-132">클라이언트에서 'Hold Off(보류 중)' 타이머 또는 서버 시작 부트스트랩이 만료될 때까지 기다리고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-132">The client is waiting for the expiration of the ‘Hold Off’ timer or Server Initiated Bootstrap.</span></span> |
| <span data-ttu-id="8d870-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span><span class="sxs-lookup"><span data-stu-id="8d870-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span></span> | <span data-ttu-id="8d870-134">클라이언트에서 부트스트랩 서버(클라이언트 시작 부트스트랩)로 'Request(요청)' 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-134">The client has sent a ‘Request’ message to the Bootstrap Server (Client Initiated Bootstrap).</span></span> |
| <span data-ttu-id="8d870-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span><span class="sxs-lookup"><span data-stu-id="8d870-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span></span> | <span data-ttu-id="8d870-136">클라이언트가 부트스트랩 서버에서 데이터를 수신하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-136">The client is receiving data from the Bootstrap Server.</span></span> |
| <span data-ttu-id="8d870-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span><span class="sxs-lookup"><span data-stu-id="8d870-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span></span> | <span data-ttu-id="8d870-138">부트스트랩 서버에서 'Finished(완료)' 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-138">The Bootstrap Server has sent a ‘Finished’ message.</span></span> |
| <span data-ttu-id="8d870-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span><span class="sxs-lookup"><span data-stu-id="8d870-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span></span> | <span data-ttu-id="8d870-140">부트스트랩 세션이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-140">The bootstrap session has failed.</span></span> |
| <span data-ttu-id="8d870-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span><span class="sxs-lookup"><span data-stu-id="8d870-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span></span> | <span data-ttu-id="8d870-142">클라이언트가 LWM2M 서버에 'Register(등록)' 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-142">The client has sent a ‘Register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="8d870-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span><span class="sxs-lookup"><span data-stu-id="8d870-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span></span> | <span data-ttu-id="8d870-144">클라이언트가 LWM2M 서버에 등록되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-144">The client is registered to the LWM2M Server.</span></span> |
| <span data-ttu-id="8d870-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span><span class="sxs-lookup"><span data-stu-id="8d870-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span></span> | <span data-ttu-id="8d870-146">클라이언트가 LWM2M 서버에 'Update(업데이트)' 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-146">The client has sent an ‘Update’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="8d870-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span><span class="sxs-lookup"><span data-stu-id="8d870-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span></span> | <span data-ttu-id="8d870-148">클라이언트가 LWM2M 서버에 'De-register(등록 취소)' 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-148">The client has sent an ‘De-register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="8d870-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span><span class="sxs-lookup"><span data-stu-id="8d870-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span></span> | <span data-ttu-id="8d870-150">클라이언트가 LWM2M 서버에서 등록 취소되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-150">The client is de-registered from the LWM2M Server.</span></span> |
| <span data-ttu-id="8d870-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="8d870-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span></span> | <span data-ttu-id="8d870-152">LWM2M 서버를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-152">The LWM2M Server is disabled.</span></span> <span data-ttu-id="8d870-153">비활성화 타이머가 만료된 후 'Register(등록)'가 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-153">A ‘Register’ will be sent after the expiration of the disable timer.</span></span> |
| <span data-ttu-id="8d870-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span><span class="sxs-lookup"><span data-stu-id="8d870-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span></span> | <span data-ttu-id="8d870-155">LWM2M 서버에 대한 등록 또는 업데이트 작업이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-155">The registration or update operation to the LWM2M Server has failed.</span></span> |
| <span data-ttu-id="8d870-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span><span class="sxs-lookup"><span data-stu-id="8d870-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span></span> | <span data-ttu-id="8d870-157">LWM2M 서버에 해당하는 서버 개체 인스턴스가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-157">The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> |

<span data-ttu-id="8d870-158">오류가 발생하는 경우 애플리케이션은 ***nx_lwm2m_client_session_error_get*** 를 호출하여 오류의 원인을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-158">In case of error the application can retrieve the cause of the error by calling ***nx_lwm2m_client_session_error_get***.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="8d870-159">로컬 디바이스 관리</span><span class="sxs-lookup"><span data-stu-id="8d870-159">Local Device Management</span></span>

<span data-ttu-id="8d870-160">애플리케이션은 로컬 디바이스 관리 기능을 사용하여 LWM2M 클라이언트의 개체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-160">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="8d870-161">지원되는 함수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-161">The following functions are provided.</span></span>

| <span data-ttu-id="8d870-162">함수&nbsp;이름</span><span class="sxs-lookup"><span data-stu-id="8d870-162">Function&nbsp;Name</span></span> | <span data-ttu-id="8d870-163">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-163">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d870-164">***nx_lwm2m_client_object_read***</span><span class="sxs-lookup"><span data-stu-id="8d870-164">***nx_lwm2m_client_object_read***</span></span> | <span data-ttu-id="8d870-165">개체 인스턴스에서 리소스를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-165">Read resources from an Object Instance.</span></span> |
| <span data-ttu-id="8d870-166">***nx_lwm2m_client_object_discover***</span><span class="sxs-lookup"><span data-stu-id="8d870-166">***nx_lwm2m_client_object_discover***</span></span> | <span data-ttu-id="8d870-167">개체 인스턴스의 리소스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-167">Get the list of the resources of an Object Instance.</span></span>
| <span data-ttu-id="8d870-168">***nx_lwm2m_client_object_write***</span><span class="sxs-lookup"><span data-stu-id="8d870-168">***nx_lwm2m_client_object_write***</span></span> | <span data-ttu-id="8d870-169">개체 인스턴스에 리소스를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-169">Write resources to an Object Instance.</span></span> |
| <span data-ttu-id="8d870-170">***nx_lwm2m_client_object_execute***</span><span class="sxs-lookup"><span data-stu-id="8d870-170">***nx_lwm2m_client_object_execute***</span></span> | <span data-ttu-id="8d870-171">개체 인스턴스의 리소스에서 실행 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-171">Perform the Execute operation on a resource of an Object Instance.</span></span> |
| <span data-ttu-id="8d870-172">***nx_lwm2m_client_object_create***</span><span class="sxs-lookup"><span data-stu-id="8d870-172">***nx_lwm2m_client_object_create***</span></span> | <span data-ttu-id="8d870-173">새 개체 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-173">Create a new Object Instance.</span></span> |
| <span data-ttu-id="8d870-174">***nx_lwm2m_client_object_delete***</span><span class="sxs-lookup"><span data-stu-id="8d870-174">***nx_lwm2m_client_object_delete***</span></span> | <span data-ttu-id="8d870-175">기존 개체 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-175">Delete an existing Object Instance.</span></span> |
| <span data-ttu-id="8d870-176">***nx_lwm2m_client_object_next_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-176">***nx_lwm2m_client_object_next_get***</span></span> | <span data-ttu-id="8d870-177">LWM2M 클라이언트를 통해 다음 개체 ID를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-177">Get the next Object ID by the LWM2M Client.</span></span> |
| <span data-ttu-id="8d870-178">***nx_lwm2m_client_object_instance_next_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-178">***nx_lwm2m_client_object_instance_next_get***</span></span> | <span data-ttu-id="8d870-179">개체의 다음 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-179">Get the next Instance of an Object.</span></span> |

## <a name="resource-information"></a><span data-ttu-id="8d870-180">리소스 정보</span><span class="sxs-lookup"><span data-stu-id="8d870-180">Resource Information</span></span>

<span data-ttu-id="8d870-181">개체에서 읽고 쓰는 경우 리소스는 NX_LWM2M_CLIENT_RESOURCE 구조로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-181">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_CLIENT_RESOURCE structure.</span></span> <span data-ttu-id="8d870-182">이 구조에는 리소스/인스턴스 ID 및 해당 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-182">This structure contains the ID of the Resource/Instance and its value.</span></span>

<span data-ttu-id="8d870-183">리소스 정보 및 값을 설정하기 위해 제공되는 함수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-183">The following functions are provided for setting resource info and value.</span></span>

| <span data-ttu-id="8d870-184">함수&nbsp;이름</span><span class="sxs-lookup"><span data-stu-id="8d870-184">Function&nbsp;Name</span></span> | <span data-ttu-id="8d870-185">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-185">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d870-186">***nx_lwm2m_client_resource_info_set***</span><span class="sxs-lookup"><span data-stu-id="8d870-186">***nx_lwm2m_client_resource_info_set***</span></span> | <span data-ttu-id="8d870-187">리소스 정보 설정: 리소스 ID 및 작업: 읽기, 쓰기, 실행 파일.</span><span class="sxs-lookup"><span data-stu-id="8d870-187">Set resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="8d870-188">***nx_lwm2m_client_resource_string_set***</span><span class="sxs-lookup"><span data-stu-id="8d870-188">***nx_lwm2m_client_resource_string_set***</span></span> | <span data-ttu-id="8d870-189">리소스 값을 문자열로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-189">Set the resource value as string.</span></span> |
| <span data-ttu-id="8d870-190">***nx_lwm2m_client_resource_integer32_set***</span><span class="sxs-lookup"><span data-stu-id="8d870-190">***nx_lwm2m_client_resource_integer32_set***</span></span> | <span data-ttu-id="8d870-191">리소스 값을 32비트 정수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-191">Set the resource value as 32-Bit integer.</span></span> |
| <span data-ttu-id="8d870-192">***nx_lwm2m_client_resource_integer64_set***</span><span class="sxs-lookup"><span data-stu-id="8d870-192">***nx_lwm2m_client_resource_integer64_set***</span></span> | <span data-ttu-id="8d870-193">리소스 값을 64비트 정수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-193">Set the resource value as 64-Bit integer.</span></span> |
| <span data-ttu-id="8d870-194">***nx_lwm2m_client_resource_float32_set***</span><span class="sxs-lookup"><span data-stu-id="8d870-194">***nx_lwm2m_client_resource_float32_set***</span></span> | <span data-ttu-id="8d870-195">리소스 값을 32비트 float로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-195">Set the resource value as 32-Bit float.</span></span> |
| <span data-ttu-id="8d870-196">***nx_lwm2m_client_resource_float64_set***</span><span class="sxs-lookup"><span data-stu-id="8d870-196">***nx_lwm2m_client_resource_float64_set***</span></span> | <span data-ttu-id="8d870-197">리소스 값을 64비트 float로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-197">Set the resource value as 64-Bit float.</span></span> |
| <span data-ttu-id="8d870-198">***nx_lwm2m_client_resource_boolean_set***</span><span class="sxs-lookup"><span data-stu-id="8d870-198">***nx_lwm2m_client_resource_boolean_set***</span></span> | <span data-ttu-id="8d870-199">리소스 값을 부울로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-199">Set the resource value as boolean.</span></span> |
| <span data-ttu-id="8d870-200">***nx_lwm2m_client_resource_objlnk_set***</span><span class="sxs-lookup"><span data-stu-id="8d870-200">***nx_lwm2m_client_resource_objlnk_set***</span></span> | <span data-ttu-id="8d870-201">리소스 값을 개체 링크로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-201">Set the resource value as object link.</span></span> |
| <span data-ttu-id="8d870-202">***nx_lwm2m_client_resource_opaque_set***</span><span class="sxs-lookup"><span data-stu-id="8d870-202">***nx_lwm2m_client_resource_opaque_set***</span></span> | <span data-ttu-id="8d870-203">리소스 값을 불투명으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-203">Set the resource value as opaque.</span></span> |
| <span data-ttu-id="8d870-204">***nx_lwm2m_client_resource_instance_set***</span><span class="sxs-lookup"><span data-stu-id="8d870-204">***nx_lwm2m_client_resource_instance_set***</span></span> | <span data-ttu-id="8d870-205">리소스 값을 여러 리소스에 대한 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-205">Set the resource value as instance for multiple resource.</span></span> |
| <span data-ttu-id="8d870-206">***nx_lwm2m_client_resource_dim_set***</span><span class="sxs-lookup"><span data-stu-id="8d870-206">***nx_lwm2m_client_resource_dim_set***</span></span> | <span data-ttu-id="8d870-207">검색을 위해 여러 리소스에 대한 리소스 차원을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-207">Set the resource dimension for multiple resource for discover.</span></span> |

<span data-ttu-id="8d870-208">리소스 정보 및 값을 가져오기 위해 제공되는 함수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-208">The following functions are provided for getting resource info and value.</span></span>

| <span data-ttu-id="8d870-209">함수&nbsp;이름</span><span class="sxs-lookup"><span data-stu-id="8d870-209">Function&nbsp;Name</span></span> | <span data-ttu-id="8d870-210">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-210">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d870-211">***nx_lwm2m_client_resource_info_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-211">***nx_lwm2m_client_resource_info_get***</span></span> | <span data-ttu-id="8d870-212">리소스 정보 가져오기: 리소스 ID 및 작업: 읽기, 쓰기, 실행 파일</span><span class="sxs-lookup"><span data-stu-id="8d870-212">Get resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="8d870-213">***nx_lwm2m_client_resource_string_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-213">***nx_lwm2m_client_resource_string_get***</span></span> | <span data-ttu-id="8d870-214">문자열 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-214">Get the value of a string resource.</span></span> |
| <span data-ttu-id="8d870-215">***nx_lwm2m_client_resource_integer32_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-215">***nx_lwm2m_client_resource_integer32_get***</span></span> | <span data-ttu-id="8d870-216">32비트 정수 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-216">Get the value of a 32-Bit integer resource.</span></span> |
| <span data-ttu-id="8d870-217">***nx_lwm2m_client_resource_integer64_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-217">***nx_lwm2m_client_resource_integer64_get***</span></span> | <span data-ttu-id="8d870-218">64비트 정수 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-218">Get the value of a b4-Bit integer resource.</span></span> |
| <span data-ttu-id="8d870-219">***nx_lwm2m_client_resource_float32_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-219">***nx_lwm2m_client_resource_float32_get***</span></span> | <span data-ttu-id="8d870-220">32비트 float 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-220">Get the value of a 32-Bit float resource.</span></span> |
| <span data-ttu-id="8d870-221">***nx_lwm2m_client_resource_float64_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-221">***nx_lwm2m_client_resource_float64_get***</span></span> | <span data-ttu-id="8d870-222">64비트 float 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-222">Get the value of a 64-Bit float resource.</span></span> |
| <span data-ttu-id="8d870-223">***nx_lwm2m_client_resource_boolean_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-223">***nx_lwm2m_client_resource_boolean_get***</span></span> | <span data-ttu-id="8d870-224">부울 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-224">Get the value of a Boolean resource.</span></span> |
| <span data-ttu-id="8d870-225">***nx_lwm2m_client_resource_objlnk_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-225">***nx_lwm2m_client_resource_objlnk_get***</span></span> | <span data-ttu-id="8d870-226">개체 링크 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-226">Get the value of an object link resource.</span></span> |
| <span data-ttu-id="8d870-227">***nx_lwm2m_client_resource_opaque_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-227">***nx_lwm2m_client_resource_opaque_get***</span></span> | <span data-ttu-id="8d870-228">불투명 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-228">Get the value of an opaque resource.</span></span> |
| <span data-ttu-id="8d870-229">***nx_lwm2m_client_resource_instance_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-229">***nx_lwm2m_client_resource_instance_get***</span></span> | <span data-ttu-id="8d870-230">여러 리소스에 대한 리소스 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-230">Get the resource instance for multiple resource.</span></span> |
| <span data-ttu-id="8d870-231">***nx_lwm2m_client_resource_dim_get***</span><span class="sxs-lookup"><span data-stu-id="8d870-231">***nx_lwm2m_client_resource_dim_get***</span></span> | <span data-ttu-id="8d870-232">여러 리소스에 대한 리소스 차원을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-232">Get the resource dimension for multiple resource.</span></span> |

## <a name="object-implementation"></a><span data-ttu-id="8d870-233">디바이스 개체 구현</span><span class="sxs-lookup"><span data-stu-id="8d870-233">Object Implementation</span></span>

<span data-ttu-id="8d870-234">LWM2M 클라이언트는 보안(0), 서버(1), 액세스 제어(2) 및 디바이스(3)와 같은 필수 OMA LWM2M 개체를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-234">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="8d870-235">다른 디바이스별 개체는 애플리케이션에서 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-235">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="8d870-236">두 데이터 구조를 사용하여 개체를 정의합니다. NX_LWM2M_CLIENT_OBJECT 구조는 개체 ID와 개체 메서드를 포함하는 개체 구현을 정의하고 NX_LWM2M_CLIENT_OBJECT_INSTANCE 구조는 개체 인스턴스의 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-236">Two data structures are used to define an Object: the NX_LWM2M_CLIENT_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_CLIENT_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="8d870-237">지원되는 함수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-237">The following functions are provided.</span></span>

| <span data-ttu-id="8d870-238">함수&nbsp;이름</span><span class="sxs-lookup"><span data-stu-id="8d870-238">Function&nbsp;Name</span></span> | <span data-ttu-id="8d870-239">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-239">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d870-240">***nx_lwm2m_client_object_add***</span><span class="sxs-lookup"><span data-stu-id="8d870-240">***nx_lwm2m_client_object_add***</span></span> | <span data-ttu-id="8d870-241">개체 구현을 LWM2M 클라이언트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-241">Add object implementation to the LwM2M Client.</span></span> |
| <span data-ttu-id="8d870-242">***nx_lwm2m_client_object_remove***</span><span class="sxs-lookup"><span data-stu-id="8d870-242">***nx_lwm2m_client_object_remove***</span></span> | <span data-ttu-id="8d870-243">LWM2M 클라이언트에서 개체 구현을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-243">Remove object implementation from the LwM2M Client.</span></span> |
| <span data-ttu-id="8d870-244">***nx_lwm2m_client_object_instance_add***</span><span class="sxs-lookup"><span data-stu-id="8d870-244">***nx_lwm2m_client_object_instance_add***</span></span> | <span data-ttu-id="8d870-245">개체에 개체 인스턴스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-245">Add object instance to the Object.</span></span> |
| <span data-ttu-id="8d870-246">***nx_lwm2m_client_object_instance_remove***</span><span class="sxs-lookup"><span data-stu-id="8d870-246">***nx_lwm2m_client_object_instance_remove***</span></span> | <span data-ttu-id="8d870-247">개체에서 개체 인스턴스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-247">Remove object instance from the Object.</span></span> |

<span data-ttu-id="8d870-248">개체 메서드 콜백 함수에는 아래와 같은 시그니처가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-248">The object method callback function has signature shown below.</span></span>

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a><span data-ttu-id="8d870-249">'Read' 메서드</span><span class="sxs-lookup"><span data-stu-id="8d870-249">The ‘Read’ Method</span></span>

<span data-ttu-id="8d870-250">'Read' 메서드는 개체 인스턴스에서 리소스 값을 읽는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-250">The ‘Read’ method is used to read Resource values from an Object Instance.</span></span> <span data-ttu-id="8d870-251">매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-251">The parameters are defined as follows.</span></span>

| <span data-ttu-id="8d870-252">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8d870-252">Parameter</span></span> | <span data-ttu-id="8d870-253">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-253">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d870-254">**operation**</span><span class="sxs-lookup"><span data-stu-id="8d870-254">**operation**</span></span> | <span data-ttu-id="8d870-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span><span class="sxs-lookup"><span data-stu-id="8d870-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span></span> |
| <span data-ttu-id="8d870-256">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-256">**object_ptr**</span></span> | <span data-ttu-id="8d870-257">개체 구현에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="8d870-257">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="8d870-258">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-258">**instance_ptr**</span></span> | <span data-ttu-id="8d870-259">개체 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="8d870-259">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="8d870-260">**resource**</span><span class="sxs-lookup"><span data-stu-id="8d870-260">**resource**</span></span> | <span data-ttu-id="8d870-261">읽는 리소스의 ID가 포함되는 **NX_LWM2M_CLIENT_RESOURCE** 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-261">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="8d870-262">반환 시 배열이 해당 형식 및 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-262">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="8d870-263">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="8d870-263">**resource_count**</span></span> | <span data-ttu-id="8d870-264">읽을 리소스의 수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-264">Pointer to the number of resources to read.</span></span> |
| <span data-ttu-id="8d870-265">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-265">**args_ptr**</span></span> | <span data-ttu-id="8d870-266">읽기에 사용되지 않는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-266">Unused parameter for read.</span></span> |
| <span data-ttu-id="8d870-267">**args_length**</span><span class="sxs-lookup"><span data-stu-id="8d870-267">**args_length**</span></span> | <span data-ttu-id="8d870-268">읽기에 사용되지 않는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-268">Unused parameter for read.</span></span> |

### <a name="the-discover-method"></a><span data-ttu-id="8d870-269">'Discover' 메서드</span><span class="sxs-lookup"><span data-stu-id="8d870-269">The ‘Discover’ Method</span></span>

<span data-ttu-id="8d870-270">'Discover' 메서드는 개체에 의해 구현된 모든 리소스 목록을 검색하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-270">The ‘Discover’ method is used to retrieve the list of all Resources implemented by an Object.</span></span> <span data-ttu-id="8d870-271">매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-271">The parameters are defined as follows.</span></span>

| <span data-ttu-id="8d870-272">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8d870-272">Parameter</span></span> | <span data-ttu-id="8d870-273">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-273">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d870-274">**operation**</span><span class="sxs-lookup"><span data-stu-id="8d870-274">**operation**</span></span> | <span data-ttu-id="8d870-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span><span class="sxs-lookup"><span data-stu-id="8d870-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span></span> |
| <span data-ttu-id="8d870-276">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-276">**object_ptr**</span></span> | <span data-ttu-id="8d870-277">개체 구현에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="8d870-277">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="8d870-278">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-278">**instance_ptr**</span></span> | <span data-ttu-id="8d870-279">개체 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="8d870-279">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="8d870-280">**resource**</span><span class="sxs-lookup"><span data-stu-id="8d870-280">**resource**</span></span> | <span data-ttu-id="8d870-281">NX_LWM2M_CLIENT_RESOURCE 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-281">Pointer to an array of NX_LWM2M_CLIENT_RESOURCE.</span></span> <span data-ttu-id="8d870-282">반환 시 배열은 해당 리소스 정보로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-282">On return the array is filled with corresponding resource info.</span></span> |
| <span data-ttu-id="8d870-283">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="8d870-283">**resource_count**</span></span> | <span data-ttu-id="8d870-284">검색할 리소스의 수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-284">Pointer to the number of resources to discover.</span></span> <span data-ttu-id="8d870-285">반환 시 이 매개 변수는 true 값으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-285">On return this parameter must be updated as the true value.</span></span> |
| <span data-ttu-id="8d870-286">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-286">**args_ptr**</span></span> | <span data-ttu-id="8d870-287">검색에 사용되지 않는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-287">Unused parameter for discover.</span></span> |
| <span data-ttu-id="8d870-288">**args_length**</span><span class="sxs-lookup"><span data-stu-id="8d870-288">**args_length**</span></span> | <span data-ttu-id="8d870-289">검색에 사용되지 않는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-289">Unused parameter for discover.</span></span> |

### <a name="the-write-method"></a><span data-ttu-id="8d870-290">'Write' 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-290">The ‘Write’ Method</span></span>

<span data-ttu-id="8d870-291">'Write' 메서드는 개체 인스턴스의 리소스를 업데이트하거나 바꾸는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-291">The ‘Write’ method is used to update or replace resources of an Object Instance.</span></span> <span data-ttu-id="8d870-292">매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-292">The parameters are defined as follows.</span></span>

| <span data-ttu-id="8d870-293">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8d870-293">Parameter</span></span>  | <span data-ttu-id="8d870-294">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-294">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d870-295">**operation**</span><span class="sxs-lookup"><span data-stu-id="8d870-295">**operation**</span></span> | <span data-ttu-id="8d870-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span><span class="sxs-lookup"><span data-stu-id="8d870-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span></span> |
| <span data-ttu-id="8d870-297">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-297">**object_ptr**</span></span> | <span data-ttu-id="8d870-298">개체 구현에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="8d870-298">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="8d870-299">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-299">**instance_ptr**</span></span> | <span data-ttu-id="8d870-300">개체 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="8d870-300">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="8d870-301">**resource**</span><span class="sxs-lookup"><span data-stu-id="8d870-301">**resource**</span></span> | <span data-ttu-id="8d870-302">읽는 리소스의 ID가 포함되는 **NX_LWM2M_CLIENT_RESOURCE** 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-302">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="8d870-303">반환 시 배열이 해당 형식 및 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-303">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="8d870-304">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="8d870-304">**resource_count**</span></span> | <span data-ttu-id="8d870-305">검색할 리소스의 수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-305">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="8d870-306">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-306">**args_ptr**</span></span> | <span data-ttu-id="8d870-307">쓰기 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-307">Write flags.</span></span> |
| <span data-ttu-id="8d870-308">**args_length**</span><span class="sxs-lookup"><span data-stu-id="8d870-308">**args_length**</span></span> | <span data-ttu-id="8d870-309">인수의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-309">The length of the arguments.</span></span> |

<span data-ttu-id="8d870-310">*flag* 매개 변수에 지정할 수 있는 쓰기 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-310">The following write operations can be specified to the *flag* parameter.</span></span>

| <span data-ttu-id="8d870-311">작업</span><span class="sxs-lookup"><span data-stu-id="8d870-311">Operation</span></span> | <span data-ttu-id="8d870-312">작업</span><span class="sxs-lookup"><span data-stu-id="8d870-312">Action</span></span> | <span data-ttu-id="8d870-313">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-313">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="8d870-314">0</span><span class="sxs-lookup"><span data-stu-id="8d870-314">0</span></span> | <span data-ttu-id="8d870-315">부분 업데이트</span><span class="sxs-lookup"><span data-stu-id="8d870-315">Partial Update</span></span> | <span data-ttu-id="8d870-316">새 값으로 제공되는 리소스를 추가하거나 업데이트하고, 다른 기존 리소스는 변경하지 않은 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-316">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span>
| <span data-ttu-id="8d870-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="8d870-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="8d870-318">인스턴스 바꾸기</span><span class="sxs-lookup"><span data-stu-id="8d870-318">Replace Instance</span></span> | <span data-ttu-id="8d870-319">개체 인스턴스를 제공된 새 리소스 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-319">Replaces the Object Instance with the new provided resource values.</span></span>
| <span data-ttu-id="8d870-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="8d870-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> |  <span data-ttu-id="8d870-321">리소스 바꾸기</span><span class="sxs-lookup"><span data-stu-id="8d870-321">Replace Resource</span></span> | <span data-ttu-id="8d870-322">리소스를 제공된 새 리소스 값(여러 리소스를 바꾸는 데 사용됨)으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-322">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="8d870-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span><span class="sxs-lookup"><span data-stu-id="8d870-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span></span> | <span data-ttu-id="8d870-324">인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="8d870-324">Create Instance</span></span> | <span data-ttu-id="8d870-325">제공된 리소스 값(**_nx_lwm2m_object_create_** 메서드에서 호출됨)을 사용하여 새로 만든 개체 인스턴스를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-325">Initializes the newly created Object Instance with the provided resource values (called from the **_nx_lwm2m_object_create_** method).</span></span> |
| <span data-ttu-id="8d870-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="8d870-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="8d870-327">부트스트랩 쓰기</span><span class="sxs-lookup"><span data-stu-id="8d870-327">Bootstrap Write</span></span> | <span data-ttu-id="8d870-328">부트스트랩 시퀀스 중에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-328">Called during Bootstrap sequence.</span></span> |

### <a name="the-execute-method"></a><span data-ttu-id="8d870-329">'Execute' 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-329">The ‘Execute’ Method</span></span>

<span data-ttu-id="8d870-330">'Execute' 메서드는 개체 리소스의 실행을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-330">The ‘Execute’ method implements the execution of an Object Resource.</span></span>

<span data-ttu-id="8d870-331">입력 매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-331">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="8d870-332">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8d870-332">Parameter</span></span>  | <span data-ttu-id="8d870-333">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-333">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d870-334">**operation**</span><span class="sxs-lookup"><span data-stu-id="8d870-334">**operation**</span></span> | <span data-ttu-id="8d870-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="8d870-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span></span> |
| <span data-ttu-id="8d870-336">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-336">**object_ptr**</span></span> | <span data-ttu-id="8d870-337">개체 구현에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="8d870-337">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="8d870-338">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-338">**instance_ptr**</span></span> | <span data-ttu-id="8d870-339">개체 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="8d870-339">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="8d870-340">**resource**</span><span class="sxs-lookup"><span data-stu-id="8d870-340">**resource**</span></span> | <span data-ttu-id="8d870-341">읽는 리소스의 ID가 포함되는 **NX_LWM2M_CLIENT_RESOURCE** 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-341">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="8d870-342">반환 시 배열이 해당 형식 및 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-342">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="8d870-343">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="8d870-343">**resource_count**</span></span> | <span data-ttu-id="8d870-344">검색할 리소스의 수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-344">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="8d870-345">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-345">**args_ptr**</span></span> | <span data-ttu-id="8d870-346">인수 목록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-346">Pointer to the arguments.</span></span> |
| <span data-ttu-id="8d870-347">**args_length**</span><span class="sxs-lookup"><span data-stu-id="8d870-347">**args_length**</span></span> | <span data-ttu-id="8d870-348">인수의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-348">The length of the arguments.</span></span>  |

<span data-ttu-id="8d870-349">함수는 리소스 ID가 존재하지 않는 경우 **NX_LWM2M_CLIENT_NOT_FOUND** 를 반환하거나, 실행을 지원하지 않는 경우 **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** 를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-349">The function must return **NX_LWM2M_CLIENT_NOT_FOUND** if the Resource ID doesn’t exist, or **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** if it doesn’t support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="8d870-350">'Create' 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-350">The ‘Create’ Method</span></span>

<span data-ttu-id="8d870-351">'Create' 메서드는 새 개체 인스턴스 만들기를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-351">The ‘Create’ method implements the creation of a new Object Instance.</span></span>

<span data-ttu-id="8d870-352">입력 매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-352">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="8d870-353">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8d870-353">Parameter</span></span>  | <span data-ttu-id="8d870-354">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-354">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d870-355">**operation**</span><span class="sxs-lookup"><span data-stu-id="8d870-355">**operation**</span></span> | <span data-ttu-id="8d870-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span><span class="sxs-lookup"><span data-stu-id="8d870-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span></span> |
| <span data-ttu-id="8d870-357">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-357">**object_ptr**</span></span> | <span data-ttu-id="8d870-358">개체 구현에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="8d870-358">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="8d870-359">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-359">**instance_ptr**</span></span> | <span data-ttu-id="8d870-360">사용하지 않는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-360">Unused parameter.</span></span> |
| <span data-ttu-id="8d870-361">**resource**</span><span class="sxs-lookup"><span data-stu-id="8d870-361">**resource**</span></span> | <span data-ttu-id="8d870-362">읽는 리소스의 ID가 포함되는 **NX_LWM2M_CLIENT_RESOURCE** 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-362">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="8d870-363">반환 시 배열이 해당 형식 및 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-363">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="8d870-364">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="8d870-364">**resource_count**</span></span> | <span data-ttu-id="8d870-365">검색할 리소스의 수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-365">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="8d870-366">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-366">**args_ptr**</span></span> | <span data-ttu-id="8d870-367">개체 인스턴스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-367">Object instance id.</span></span> |
| <span data-ttu-id="8d870-368">**args_length**</span><span class="sxs-lookup"><span data-stu-id="8d870-368">**args_length**</span></span> | <span data-ttu-id="8d870-369">인수의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-369">The length of the arguments.</span></span> |

### <a name="the-delete-method"></a><span data-ttu-id="8d870-370">'Delete' 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-370">The ‘Delete’ Method</span></span>

<span data-ttu-id="8d870-371">'Delete' 메서드는 개체 인스턴스의 삭제를 구현하고 입력 매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-371">The ‘Delete’ method implements the deletion of an object instance, the input parameters are defined as follows.</span></span>

| <span data-ttu-id="8d870-372">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8d870-372">Parameter</span></span>  | <span data-ttu-id="8d870-373">Description</span><span class="sxs-lookup"><span data-stu-id="8d870-373">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d870-374">**operation**</span><span class="sxs-lookup"><span data-stu-id="8d870-374">**operation**</span></span> | <span data-ttu-id="8d870-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span><span class="sxs-lookup"><span data-stu-id="8d870-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span></span> |
| <span data-ttu-id="8d870-376">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-376">**object_ptr**</span></span> | <span data-ttu-id="8d870-377">개체 구현에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="8d870-377">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="8d870-378">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-378">**instance_ptr**</span></span> | <span data-ttu-id="8d870-379">개체 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="8d870-379">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="8d870-380">**resource**</span><span class="sxs-lookup"><span data-stu-id="8d870-380">**resource**</span></span> | <span data-ttu-id="8d870-381">사용하지 않는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-381">Unused parameter.</span></span> |
| <span data-ttu-id="8d870-382">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="8d870-382">**resource_count**</span></span> | <span data-ttu-id="8d870-383">사용하지 않는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-383">Unused parameter.</span></span> |
| <span data-ttu-id="8d870-384">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="8d870-384">**args_ptr**</span></span> | <span data-ttu-id="8d870-385">사용하지 않는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-385">Unused parameter.</span></span> |
| <span data-ttu-id="8d870-386">**args_length**</span><span class="sxs-lookup"><span data-stu-id="8d870-386">**args_length**</span></span> | <span data-ttu-id="8d870-387">사용하지 않는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-387">Unused parameter.</span></span> |

<span data-ttu-id="8d870-388">성공 시 개체는 개체 인스턴스 데이터 및 인스턴스에 의해 할당된 다른 모든 리소스를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-388">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="8d870-389">LWM2M 클라이언트 애플리케이션의 예</span><span class="sxs-lookup"><span data-stu-id="8d870-389">Example of LWM2M Client Application</span></span>

<span data-ttu-id="8d870-390">다음 코드는 온도 센서 및 광원 스위치로 구성된 사용자 지정 디바이스를 구현하는 간단한 LWM2M 클라이언트 애플리케이션의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-390">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="8d870-391">서버는 디바이스를 사용하여 광원 스위치의 온도 센서 및 부울 상태 값을 읽고 광원 스위치를 켜기/끄기로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d870-391">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```