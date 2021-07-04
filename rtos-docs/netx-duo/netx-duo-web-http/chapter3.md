---
title: 챕터 3 - HTTP 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 NetX 웹 HTTP 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6bb2743f05c5b56331d1c0e948601ad23bf340d1
ms.sourcegitcommit: 95f4ae0842a486fec8f10d1480203695faa9592d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111875275"
---
# <a name="chapter-3---description-of-http-services"></a><span data-ttu-id="8a501-103">챕터 3 - HTTP 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="8a501-103">Chapter 3 - Description of HTTP services</span></span>

<span data-ttu-id="8a501-104">이 챕터에서는 아래에 나열된 모든 NetX 웹 HTTP 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-104">This chapter contains a description of all NetX Web HTTP services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="8a501-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="http-and-https-client-api"></a><span data-ttu-id="8a501-106">HTTP 및 HTTPS 클라이언트 API</span><span class="sxs-lookup"><span data-stu-id="8a501-106">HTTP and HTTPS Client API</span></span>

## <a name="nx_web_http_client_connect"></a><span data-ttu-id="8a501-107">nx_web_http_client_connect</span><span class="sxs-lookup"><span data-stu-id="8a501-107">nx_web_http_client_connect</span></span>

<span data-ttu-id="8a501-108">사용자 지정 요청을 위해 HTTP 서버에 대한 일반 텍스트 소켓을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-108">Open a plaintext socket to an HTTP server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-109">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-109">Prototype</span></span>

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-110">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-110">Description</span></span>

<span data-ttu-id="8a501-111">이 메서드는 **일반 텍스트** HTTP에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-111">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="8a501-112">이 서비스는 HTTP 서버에 대한 일반 텍스트 TCP 소켓을 열지만 요청을 보내지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-112">This service opens a plaintext TCP socket to an HTTP server but does not send any requests.</span></span> <span data-ttu-id="8a501-113">요청은 n *x_web_http_client_request_initialize()* 를 사용하여 만들어지고 *nx_web_http_client_request_send()* 를 사용하여 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-113">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="8a501-114">*nx_web_http_client_request_header_add()* 를 사용하여 사용자 지정 HTTP 헤더를 요청에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-114">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="8a501-115">이 서비스를 사용하면 애플리케이션에서 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-115">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="8a501-116">**이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8a501-116">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="8a501-117">nx_web_http_client_\*_start 메서드는 편의를 위해 제공되며(예: *nx_web_http_client_get_start*()) 요청 생성 및 소켓 연결을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-117">The nx_web_http_client_\*_start methods are provided for convenience (e.g. *nx_web_http_client_get_start*()) and handle the request generation and socket connection.</span></span> <span data-ttu-id="8a501-118">요청에 사용자 지정 HTTP 헤더가 필요하지 않은 경우에는 *nx_web_http_client_connect()* 대신 이러한 서비스 및 관련 루틴을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-118">You can use those services instead of *nx_web_http_client_connect()* and the related routines if you do not need custom HTTP headers in your requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-119">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-119">Input Parameters</span></span>

- <span data-ttu-id="8a501-120">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-120">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-121">**server_ip** 원격 HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-121">**server_ip** IP address of remote HTTP server.</span></span>
- <span data-ttu-id="8a501-122">**server_port** 원격 HTTP 서버의 포트(예: HTTP의 경우 80)</span><span class="sxs-lookup"><span data-stu-id="8a501-122">**server_port** Port on remote HTTP server (e.g. 80 for HTTP).</span></span>
- <span data-ttu-id="8a501-123">**wait_option** 서비스가 기본 네트워크 작업을 대기하는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-123">**wait_option** Defines how long the service will wait for underlying network operations.</span></span> <span data-ttu-id="8a501-124">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-124">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-125">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-125">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-127">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-127">Return Values</span></span>

- <span data-ttu-id="8a501-128">**NX_SUCCESS** (0x00) TCP 소켓이 연결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-128">**NX_SUCCESS** (0x00) Successful connection of TCP socket.</span></span>
- <span data-ttu-id="8a501-129">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-129">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-130">NX_WEB_HTTP_NOT_READY (0x3000A) 다른 요청이 이미 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-130">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-131">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-131">Allowed From</span></span>

<span data-ttu-id="8a501-132">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-133">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-133">Example</span></span>

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a><span data-ttu-id="8a501-134">nx_web_http_client_create</span><span class="sxs-lookup"><span data-stu-id="8a501-134">nx_web_http_client_create</span></span>

<span data-ttu-id="8a501-135">HTTP 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="8a501-135">Create an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-136">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-136">Prototype</span></span>

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="8a501-137">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-137">Description</span></span>

<span data-ttu-id="8a501-138">이 서비스는 지정된 IP 인스턴스에서 HTTP 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-138">This service creates an HTTP Client instance on the specified IP instance.</span></span> <span data-ttu-id="8a501-139">클라이언트 인스턴스는 HTTP 또는 HTTPS에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-139">The Client instance can be used for either HTTP or HTTPS.</span></span> <span data-ttu-id="8a501-140">HTTP 또는 HTTPS 인스턴스를 시작하는 방법에 대한 자세한 내용은 *nx_web_http_client_connect()* 및 *nx_web_http_client_secure_connect()* 서비스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-140">See the services *nx_web_http_client_connect()* and *nx_web_http_client_secure_connect()* for more information on starting an HTTP or HTTPS instance.</span></span> <span data-ttu-id="8a501-141">GET, PUT 및 POST 메서드를 간단하게 호출하는 방법은 \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** 에 대한 API를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-141">Also refer to the API for \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** for simple invocations of GET, PUT, and POST methods.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-142">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-142">Input Parameters</span></span>

- <span data-ttu-id="8a501-143">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-143">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-144">**client_name** HTTP 클라이언트 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-144">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="8a501-145">**ip_ptr** IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-145">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="8a501-146">**pool_ptr** 기본 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-146">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="8a501-147">이 풀의 패킷에는 전체 응답 헤더를 처리할 수 있을 만큼 큰 페이로드가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-147">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="8a501-148">*nx_web_http_client.h* 의 *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* 에서 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-148">This is defined by *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* in *nx_web_http_client.h*.</span></span>
- <span data-ttu-id="8a501-149">**window_size** 클라이언트의 TCP 소켓 수신 창의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-149">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-150">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-150">Return Values</span></span>

- <span data-ttu-id="8a501-151">**NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="8a501-151">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="8a501-152">NX_PTR_ERROR (0x16) 잘못된 HTTP, ip_ptr 또는 패킷 풀 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-152">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="8a501-153">NX_WEB_HTTP_POOL_ERROR (0x30009) 패킷 풀의 페이로드 크기가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-154">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-154">Allowed From</span></span>

<span data-ttu-id="8a501-155">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-155">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-156">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-156">Example</span></span>

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a><span data-ttu-id="8a501-157">nx_web_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="8a501-157">nx_web_http_client_delete</span></span>

<span data-ttu-id="8a501-158">HTTP 클라이언트 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="8a501-158">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-159">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-159">Prototype</span></span>

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="8a501-160">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-160">Description</span></span>

<span data-ttu-id="8a501-161">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-161">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-162">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-162">Input Parameters</span></span>

- <span data-ttu-id="8a501-163">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-163">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-164">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-164">Return Values</span></span>

- <span data-ttu-id="8a501-165">**NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="8a501-165">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="8a501-166">NX_PTR_ERROR (0x16) 잘못된 HTTP 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-166">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="8a501-167">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-168">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-168">Allowed From</span></span>

<span data-ttu-id="8a501-169">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-170">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-170">Example</span></span>

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a><span data-ttu-id="8a501-171">nx_web_http_client_delete_start</span><span class="sxs-lookup"><span data-stu-id="8a501-171">nx_web_http_client_delete_start</span></span>

<span data-ttu-id="8a501-172">일반 텍스트 HTTP DELETE 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-172">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-173">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-173">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-174">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-174">Description</span></span>

<span data-ttu-id="8a501-175">이 메서드는 **일반 텍스트** HTTP에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-175">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="8a501-176">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 삭제(DELETE)하는 요청을 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-176">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-177">이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 서버의 응답을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-177">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="8a501-178">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-178">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-179">이 API는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-179">This API is deprecated.</span></span> <span data-ttu-id="8a501-180">개발자는 *nx_web_http_client_delete_start_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-180">Developers are encouraged to use *nx_web_http_client_delete_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-181">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-181">Input Parameters</span></span>

- <span data-ttu-id="8a501-182">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-182">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-183">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-183">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-184">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-184">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-185">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-185">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-186">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-186">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-187">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-187">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-188">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-188">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-189">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-189">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-190">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-190">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-191">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-191">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-192">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-192">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-193">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-193">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-195">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-195">Return Values</span></span>

- <span data-ttu-id="8a501-196">**NX_SUCCESS** (0x00) HTTP 클라이언트 DELETE 요청 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-196">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="8a501-197">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-197">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-201">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-201">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-202">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-202">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-203">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-203">Allowed From</span></span>

<span data-ttu-id="8a501-204">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-204">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-205">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-205">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a><span data-ttu-id="8a501-206">nx_web_http_client_delete_start_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-206">nx_web_http_client_delete_start_extended</span></span>

<span data-ttu-id="8a501-207">일반 텍스트 HTTP DELETE 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-207">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-208">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-208">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-209">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-209">Description</span></span>

<span data-ttu-id="8a501-210">이 메서드는 **일반 텍스트** HTTP에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-210">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="8a501-211">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 삭제(DELETE)하는 요청을 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-211">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-212">이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 서버의 응답을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-212">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="8a501-213">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-213">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-214">리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-214">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-215">이 서비스는 *nx_web_http_client_delete_start* ()를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-215">This service replaces *nx_web_http_client_delete_start* ().</span></span> <span data-ttu-id="8a501-216">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-216">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-217">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-217">Input Parameters</span></span>

- <span data-ttu-id="8a501-218">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-218">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-219">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-219">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-220">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-220">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-221">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-221">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-222">**resource_length** 요청된 리소스의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-222">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="8a501-223">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-223">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-224">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-224">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-225">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-225">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-226">**host_length** 호스트의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-226">**host_length** String length of host.</span></span>
- <span data-ttu-id="8a501-227">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-227">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-228">**username_length** 인증을 위한 사용자 이름의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-228">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="8a501-229">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-229">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-230">**password_length** 인증을 위한 암호의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-230">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="8a501-231">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-231">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-232">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-232">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-233">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-233">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-235">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-235">Return Values</span></span>

- <span data-ttu-id="8a501-236">**NX_SUCCESS** (0x00) HTTP 클라이언트 DELETE 요청 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-236">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="8a501-237">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-237">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-241">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-241">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-242">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-242">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-243">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-243">Allowed From</span></span>

<span data-ttu-id="8a501-244">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-244">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-245">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-245">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a><span data-ttu-id="8a501-246">nx_web_http_client_delete_secure_start</span><span class="sxs-lookup"><span data-stu-id="8a501-246">nx_web_http_client_delete_secure_start</span></span>

<span data-ttu-id="8a501-247">암호화된 HTTPS DELETE 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-247">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-248">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-248">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-249">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-249">Description</span></span>

<span data-ttu-id="8a501-250">이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-250">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="8a501-251">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 삭제(DELETE)하는 요청을 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-251">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-252">이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 서버의 응답을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-252">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="8a501-253">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-253">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-254">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-254">This service is deprecated.</span></span> <span data-ttu-id="8a501-255">개발자는 *nx_web_http_client_delete_secure_start_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-255">Developers are encouraged to use *nx_web_http_client_delete_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-256">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-256">Input Parameters</span></span>

- <span data-ttu-id="8a501-257">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-257">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-258">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-258">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-259">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-259">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-260">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-260">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="8a501-261">리소스는 NULL로 종료되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-261">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="8a501-262">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-262">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-263">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-263">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-264">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-264">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-265">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-265">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-266">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-266">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-267">**tls_setup** TLS 구성을 설정하는 데 사용되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-267">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="8a501-268">애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-268">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="8a501-269">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-269">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-270">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-270">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-271">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-271">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-273">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-273">Return Values</span></span>

- <span data-ttu-id="8a501-274">**NX_SUCCESS** (0x00) HTTP 클라이언트 DELETE 요청 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-274">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="8a501-275">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-275">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-279">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-279">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-280">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-280">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-281">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-281">Allowed From</span></span>

<span data-ttu-id="8a501-282">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-283">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-283">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a><span data-ttu-id="8a501-284">nx_web_http_client_delete_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-284">nx_web_http_client_delete_secure_start_extended</span></span>

<span data-ttu-id="8a501-285">암호화된 HTTPS DELETE 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-285">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-286">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-286">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-287">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-287">Description</span></span>

<span data-ttu-id="8a501-288">이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-288">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="8a501-289">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 삭제(DELETE)하는 요청을 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-289">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-290">이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 서버의 응답을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-290">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="8a501-291">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-291">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-292">리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-292">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-293">이 서비스는 *nx_web_http_client_delete_secure_start* ()를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-293">This service replaces *nx_web_http_client_delete_secure_start*().</span></span> <span data-ttu-id="8a501-294">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-294">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-295">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-295">Input Parameters</span></span>

- <span data-ttu-id="8a501-296">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-296">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-297">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-297">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-298">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-298">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-299">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-299">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="8a501-300">리소스는 NULL로 종료되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-300">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="8a501-301">**resource_length** 요청된 리소스의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-301">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="8a501-302">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-302">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-303">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-303">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-304">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-304">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-305">**host_length** 호스트의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-305">**host_length** String length of host.</span></span>
- <span data-ttu-id="8a501-306">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-306">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-307">**username_length** 인증을 위한 사용자 이름의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-307">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="8a501-308">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-308">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-309">**password_length** 인증을 위한 암호의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-309">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="8a501-310">**tls_setup** TLS 구성을 설정하는 데 사용되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-310">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="8a501-311">애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-311">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="8a501-312">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-312">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-313">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-313">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-314">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-314">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-316">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-316">Return Values</span></span>

- <span data-ttu-id="8a501-317">**NX_SUCCESS** (0x00) HTTP 클라이언트 DELETE 요청 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-317">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="8a501-318">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-318">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-322">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-322">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-323">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-323">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="8a501-324">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-324">Allowed From</span></span>

<span data-ttu-id="8a501-325">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-325">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-326">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-326">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a><span data-ttu-id="8a501-327">nx_web_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="8a501-327">nx_web_http_client_get_start</span></span>

<span data-ttu-id="8a501-328">일반 텍스트 HTTP GET 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-328">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-329">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-329">Prototype</span></span>

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-330">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-330">Description</span></span>

<span data-ttu-id="8a501-331">이 메서드는 **일반 텍스트** HTTP에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-331">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="8a501-332">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 가져오려고(GET) 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-332">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-333">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-333">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="8a501-334">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-334">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-335">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-335">This service is deprecated.</span></span> <span data-ttu-id="8a501-336">개발자는 *nx_web_http_client_get_start_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-336">Developers are encouraged to use *nx_web_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-337">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-337">Input Parameters</span></span>

- <span data-ttu-id="8a501-338">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-338">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-339">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-339">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-340">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-340">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-341">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-341">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-342">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-342">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-343">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-343">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-344">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-344">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-345">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-345">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-346">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-346">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-347">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-347">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-348">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-348">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-349">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-349">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-351">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-351">Return Values</span></span>

- <span data-ttu-id="8a501-352">**NX_SUCCESS** (0x00) HTTP 클라이언트 GET 시작 메시지를 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-352">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="8a501-353">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-353">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-357">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-357">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-358">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-358">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-359">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-359">Allowed From</span></span>

<span data-ttu-id="8a501-360">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-361">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-361">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a><span data-ttu-id="8a501-362">nx_web_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-362">nx_web_http_client_get_start_extended</span></span>

<span data-ttu-id="8a501-363">일반 텍스트 HTTP GET 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-363">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-364">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-364">Prototype</span></span>

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-365">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-365">Description</span></span>

<span data-ttu-id="8a501-366">이 메서드는 **일반 텍스트** HTTP에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-366">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="8a501-367">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 가져오려고(GET) 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-367">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-368">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-368">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="8a501-369">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-369">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-370">리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-370">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-371">이 서비스는 *nx_web_http_client_get_start*()를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-371">This service replaces *nx_web_http_client_get_start*().</span></span> <span data-ttu-id="8a501-372">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-372">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-373">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-373">Input Parameters</span></span>

- <span data-ttu-id="8a501-374">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-374">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-375">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-375">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-376">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-376">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-377">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-377">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-378">**resource_length** 요청된 리소스의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-378">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="8a501-379">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-379">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-380">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-380">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-381">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-381">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-382">**host_length** 호스트의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-382">**host_length** String length of host.</span></span>
- <span data-ttu-id="8a501-383">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-383">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-384">**username_length** 인증을 위한 사용자 이름의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-384">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="8a501-385">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-385">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-386">**password_length** 인증을 위한 암호의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-386">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="8a501-387">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-387">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-388">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-388">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-389">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-389">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-391">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-391">Return Values</span></span>

- <span data-ttu-id="8a501-392">**NX_SUCCESS** (0x00) HTTP 클라이언트 GET 시작 메시지를 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-392">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="8a501-393">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-393">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-397">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-397">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-398">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-398">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-399">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-399">Allowed From</span></span>

<span data-ttu-id="8a501-400">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-401">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-401">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a><span data-ttu-id="8a501-402">nx_web_http_client_get_secure_start</span><span class="sxs-lookup"><span data-stu-id="8a501-402">nx_web_http_client_get_secure_start</span></span>

<span data-ttu-id="8a501-403">암호화된 HTTPS GET 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-403">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-404">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-404">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-405">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-405">Description</span></span>

<span data-ttu-id="8a501-406">이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-406">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="8a501-407">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 가져오려고(GET) 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-407">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-408">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-408">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="8a501-409">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-409">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-410">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-410">This service is deprecated.</span></span> <span data-ttu-id="8a501-411">개발자는 *nx_web_http_client_get_secure_start_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-411">Developers are encouraged to use *nx_web_http_client_get_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-412">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-412">Input Parameters</span></span>

- <span data-ttu-id="8a501-413">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-413">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-414">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-414">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-415">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-415">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-416">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-416">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-417">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-417">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-418">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-418">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-419">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-419">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-420">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-420">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-421">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-421">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-422">**tls_setup** TLS 구성을 설정하는 데 사용되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-422">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="8a501-423">애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-423">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="8a501-424">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-424">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-425">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-425">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-426">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-426">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-428">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-428">Return Values</span></span>

- <span data-ttu-id="8a501-429">**NX_SUCCESS** (0x00) HTTP 클라이언트 GET 시작 메시지를 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-429">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="8a501-430">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-430">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-434">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-434">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-435">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-435">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-436">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-436">Allowed From</span></span>

<span data-ttu-id="8a501-437">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-438">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-438">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a><span data-ttu-id="8a501-439">nx_web_http_client_get_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-439">nx_web_http_client_get_secure_start_extended</span></span>

<span data-ttu-id="8a501-440">암호화된 HTTPS GET 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-440">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-441">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-441">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-442">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-442">Description</span></span>

<span data-ttu-id="8a501-443">이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-443">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="8a501-444">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 가져오려고(GET) 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-444">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-445">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-445">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="8a501-446">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-446">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-447">리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-447">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-448">이 서비스는 *nx_web_http_client_secure_start*()를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-448">This service replaces *nx_web_http_client_secure_start*().</span></span> <span data-ttu-id="8a501-449">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-449">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-450">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-450">Input Parameters</span></span>

- <span data-ttu-id="8a501-451">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-451">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-452">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-452">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-453">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-453">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-454">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-454">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-455">**resource_length** 요청된 리소스의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-455">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="8a501-456">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-456">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-457">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-457">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-458">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-458">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-459">**host_length** 호스트의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-459">**host_length** String length of host.</span></span>
- <span data-ttu-id="8a501-460">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-460">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-461">**username_length** 인증을 위한 사용자 이름의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-461">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="8a501-462">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-462">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-463">**password_length** 인증을 위한 암호의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-463">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="8a501-464">**tls_setup** TLS 구성을 설정하는 데 사용되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-464">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="8a501-465">애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-465">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="8a501-466">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-466">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-467">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-467">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-468">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-468">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-470">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-470">Return Values</span></span>

- <span data-ttu-id="8a501-471">**NX_SUCCESS** (0x00) HTTP 클라이언트 GET 시작 메시지를 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-471">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="8a501-472">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-472">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-476">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-477">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-477">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-478">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-478">Allowed From</span></span>

<span data-ttu-id="8a501-479">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-480">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-480">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a><span data-ttu-id="8a501-481">nx_web_http_client_head_start</span><span class="sxs-lookup"><span data-stu-id="8a501-481">nx_web_http_client_head_start</span></span>

<span data-ttu-id="8a501-482">일반 텍스트 HTTP HEAD 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-482">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-483">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-483">Prototype</span></span>

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-484">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-484">Description</span></span>

<span data-ttu-id="8a501-485">이 메서드는 **일반 텍스트** HTTP에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-485">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="8a501-486">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스의 HEAD 메타데이터를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-486">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-487">이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 응답을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-487">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="8a501-488">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-488">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-489">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-489">This service is deprecated.</span></span> <span data-ttu-id="8a501-490">개발자는 *nx_web_http_client_head_start_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-490">Developers are encouraged to use *nx_web_http_client_head_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-491">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-491">Input Parameters</span></span>

- <span data-ttu-id="8a501-492">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-492">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-493">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-493">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-494">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-494">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-495">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-495">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-496">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-496">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-497">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-497">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-498">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-498">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-499">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-499">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-500">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-500">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-501">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-501">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-502">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-502">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-503">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-503">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-505">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-505">Return Values</span></span>

- <span data-ttu-id="8a501-506">**NX_SUCCESS** (0x00) HTTP 클라이언트 HEAD 요청 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-506">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="8a501-507">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-507">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-511">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-511">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-512">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-513">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-513">Allowed From</span></span>

<span data-ttu-id="8a501-514">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-515">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-515">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a><span data-ttu-id="8a501-516">nx_web_http_client_head_start_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-516">nx_web_http_client_head_start_extended</span></span>

<span data-ttu-id="8a501-517">일반 텍스트 HTTP HEAD 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-517">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-518">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-518">Prototype</span></span>

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-519">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-519">Description</span></span>

<span data-ttu-id="8a501-520">이 메서드는 **일반 텍스트** HTTP에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-520">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="8a501-521">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스의 HEAD 메타데이터를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-521">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-522">이 루틴이 NX_SUCCESS를 반환하는 경우 애플리케이션에서는 *nx_web_http_client_response_body_get()* 을 호출하여 응답을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-522">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="8a501-523">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-523">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-524">리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-524">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-525">이 서비스는 *nx_web_http_client_head_start*()를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-525">This service replaces *nx_web_http_client_head_start*().</span></span> <span data-ttu-id="8a501-526">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-526">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-527">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-527">Input Parameters</span></span>

- <span data-ttu-id="8a501-528">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-528">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-529">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-529">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-530">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-530">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-531">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-531">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-532">**resource_length** 요청된 리소스의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-532">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="8a501-533">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-533">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-534">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-534">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-535">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-535">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-536">**host_length** 호스트의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-536">**host_length** String length of host.</span></span>
- <span data-ttu-id="8a501-537">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-537">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-538">**username_length** 인증을 위한 사용자 이름의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-538">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="8a501-539">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-539">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-540">**password_length** 인증을 위한 암호의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-540">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="8a501-541">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-541">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-542">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-542">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-543">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-543">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-545">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-545">Return Values</span></span>

- <span data-ttu-id="8a501-546">**NX_SUCCESS** (0x00) HTTP 클라이언트 HEAD 요청 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-546">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="8a501-547">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-547">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-551">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-551">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-552">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-552">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-553">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-553">Allowed From</span></span>

<span data-ttu-id="8a501-554">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-555">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-555">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a><span data-ttu-id="8a501-556">nx_web_http_client_head_secure_start</span><span class="sxs-lookup"><span data-stu-id="8a501-556">nx_web_http_client_head_secure_start</span></span>

<span data-ttu-id="8a501-557">암호화된 HTTPS HEAD 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-557">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-558">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-558">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-559">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-559">Description</span></span>

<span data-ttu-id="8a501-560">이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-560">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="8a501-561">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스의 HEAD 메타데이터를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-561">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-562">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 호출하여 요청된 리소스 콘텐츠에 해당하는 서버의 응답을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-562">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="8a501-563">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-563">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-564">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-564">This service is deprecated.</span></span> <span data-ttu-id="8a501-565">개발자는 *nx_web_http_client_head_secure_start_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-565">Developers are encouraged to use *nx_web_http_client_head_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-566">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-566">Input Parameters</span></span>

- <span data-ttu-id="8a501-567">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-567">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-568">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-568">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-569">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-569">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-570">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-570">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-571">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-571">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-572">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-572">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-573">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-573">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-574">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-574">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-575">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-575">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-576">**tls_setup** TLS 구성을 설정하는 데 사용되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-576">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="8a501-577">애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-577">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="8a501-578">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-578">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-579">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-579">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-580">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-580">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-582">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-582">Return Values</span></span>

- <span data-ttu-id="8a501-583">**NX_SUCCESS** (0x00) HTTP 클라이언트 HEAD 요청 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-583">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="8a501-584">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-584">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-588">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-589">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-589">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-590">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-590">Allowed From</span></span>

<span data-ttu-id="8a501-591">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-591">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-592">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-592">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a><span data-ttu-id="8a501-593">nx_web_http_client_head_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-593">nx_web_http_client_head_secure_start_extended</span></span>

<span data-ttu-id="8a501-594">암호화된 HTTPS HEAD 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-594">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-595">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-595">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-596">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-596">Description</span></span>

<span data-ttu-id="8a501-597">이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-597">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="8a501-598">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스의 HEAD 메타데이터를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-598">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8a501-599">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_web_http_client_response_body_get()* 을 호출하여 요청된 리소스 콘텐츠에 해당하는 서버의 응답을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-599">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="8a501-600">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-600">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8a501-601">리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-601">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-602">이 서비스는 *nx_web_http_client_head_secure_start*()를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-602">This service replaces *nx_web_http_client_head_secure_start*().</span></span> <span data-ttu-id="8a501-603">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-603">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-604">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-604">Input Parameters</span></span>

- <span data-ttu-id="8a501-605">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-605">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-606">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-606">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-607">**server_port** 원격 HTTP 서버의 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-607">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-608">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-608">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-609">**resource_length** 요청된 리소스의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-609">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="8a501-610">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-610">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-611">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-611">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-612">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-612">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-613">**host_length** 호스트의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-613">**host_length** String length of host.</span></span>
- <span data-ttu-id="8a501-614">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-614">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-615">**username_length** 인증을 위한 사용자 이름의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-615">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="8a501-616">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-616">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-617">**password_length** 인증을 위한 암호의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-617">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="8a501-618">**tls_setup** TLS 구성을 설정하는 데 사용되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-618">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="8a501-619">애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-619">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="8a501-620">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-620">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-621">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-621">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-622">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-622">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-624">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-624">Return Values</span></span>

- <span data-ttu-id="8a501-625">**NX_SUCCESS** (0x00) HTTP 클라이언트 HEAD 요청 메시지를 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-625">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="8a501-626">**NX_WEB_HTTP_ERROR** (0x30000) 내부 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-626">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="8a501-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP 클라이언트가 HTTP 서버와 통신하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8a501-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="8a501-630">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-630">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-631">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-631">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-632">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-632">Allowed From</span></span>

<span data-ttu-id="8a501-633">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-633">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-634">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-634">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a><span data-ttu-id="8a501-635">nx_web_http_client_request_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="8a501-635">nx_web_http_client_request_packet_allocate</span></span>

<span data-ttu-id="8a501-636">HTTP(S) 패킷을 할당</span><span class="sxs-lookup"><span data-stu-id="8a501-636">Allocate a HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-637">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-637">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-638">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-638">Description</span></span>

<span data-ttu-id="8a501-639">이 서비스는 클라이언트 HTTP(S)에 사용할 패킷을 할당하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-639">This service attempts to allocates a packet for Client HTTP(S).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-640">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-640">Input Parameters</span></span>

- <span data-ttu-id="8a501-641">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-641">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-642">**packet_ptr** 할당된 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-642">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="8a501-643">**wait_option** 패킷 풀에 사용 가능한 패킷이 없는 경우 대기 시간을 틱 단위로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-643">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="8a501-644">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-644">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-645">**NX_NO_WAIT** (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8a501-645">**NX_NO_WAIT** (0x00000000)</span></span>
  - <span data-ttu-id="8a501-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8a501-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="8a501-647">**timeout in ticks** (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8a501-647">**timeout in ticks** (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-648">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-648">Return Values</span></span>

- <span data-ttu-id="8a501-649">**NX_SUCCESS** (0x00) 패킷을 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-649">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="8a501-650">**NX_NO_PACKET** (0x01) 사용 가능한 패킷이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-650">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="8a501-651">**NX_WAIT_ABORTED** (0x1A) 요청된 일시 중단이 *tx_thread_wait_abort* 호출 때문에 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-651">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="8a501-652">**NX_INVALID_PARAMETERS** (0x4D) 프로토콜을 지원하지 않는 패킷 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-652">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="8a501-653">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-653">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-654">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-654">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-655">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-655">Allowed From</span></span>

<span data-ttu-id="8a501-656">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-657">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-657">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a><span data-ttu-id="8a501-658">nx_web_http_client_post_start</span><span class="sxs-lookup"><span data-stu-id="8a501-658">nx_web_http_client_post_start</span></span>

<span data-ttu-id="8a501-659">HTTP POST 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-659">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-660">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-660">Prototype</span></span>

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-661">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-661">Description</span></span>

<span data-ttu-id="8a501-662">이 메서드는 **일반 텍스트** HTTP에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-662">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="8a501-663">이 서비스는 지정된 리소스가 포함된 POST 요청을, 제공된 IP 주소 및 포트의 HTTP 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-663">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="8a501-664">이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-664">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="8a501-665">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-665">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8a501-666">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-666">This service is deprecated.</span></span> <span data-ttu-id="8a501-667">개발자는 *nx_web_http_client_post_start_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-667">Developers are encouraged to use *nx_web_http_client_post_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-668">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-668">Input Parameters</span></span>

- <span data-ttu-id="8a501-669">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-669">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-670">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-670">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-671">**server_port** 원격 HTTP 서버의 TCP 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-671">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-672">**resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-672">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="8a501-673">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-673">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-674">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-674">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-675">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-675">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-676">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-676">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-677">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-677">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-678">**total_bytes** 전송 중인 리소스의 총 바이트 수.</span><span class="sxs-lookup"><span data-stu-id="8a501-678">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8a501-679">후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-679">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="8a501-680">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-680">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-681">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-681">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-682">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-682">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-684">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-684">Return Values</span></span>

- <span data-ttu-id="8a501-685">**NX_SUCCESS** (0x00) POST 요청을 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-685">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="8a501-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="8a501-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-688">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-688">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-689">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="8a501-689">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="8a501-690">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-690">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-691">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-691">Allowed From</span></span>

<span data-ttu-id="8a501-692">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-693">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-693">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a><span data-ttu-id="8a501-694">nx_web_http_client_post_start_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-694">nx_web_http_client_post_start_extended</span></span>

<span data-ttu-id="8a501-695">HTTP POST 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-695">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-696">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-696">Prototype</span></span>

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-697">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-697">Description</span></span>

<span data-ttu-id="8a501-698">이 메서드는 **일반 텍스트** HTTP에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-698">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="8a501-699">이 서비스는 지정된 리소스가 포함된 POST 요청을, 제공된 IP 주소 및 포트의 HTTP 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-699">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="8a501-700">이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-700">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="8a501-701">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-701">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8a501-702">리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-702">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-703">이 서비스는 *nx_web_http_client_post_start* ()를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-703">This service replaces *nx_web_http_client_post_start* ().</span></span> <span data-ttu-id="8a501-704">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-704">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-705">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-705">Input Parameters</span></span>

- <span data-ttu-id="8a501-706">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-706">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-707">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-707">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-708">**server_port** 원격 HTTP 서버의 TCP 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-708">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-709">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-709">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-710">**resource_length** 요청된 리소스의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-710">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="8a501-711">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-711">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-712">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-712">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-713">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-713">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-714">**host_length** 호스트의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-714">**host_length** String length of host.</span></span>
- <span data-ttu-id="8a501-715">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-715">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-716">**username_length** 인증을 위한 사용자 이름의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-716">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="8a501-717">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-717">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-718">**password_length** 인증을 위한 암호의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-718">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="8a501-719">**total_bytes** 전송 중인 리소스의 총 바이트 수.</span><span class="sxs-lookup"><span data-stu-id="8a501-719">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8a501-720">후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-720">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="8a501-721">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-721">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-722">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-722">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-723">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-723">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-725">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-725">Return Values</span></span>

- <span data-ttu-id="8a501-726">**NX_SUCCESS** (0x00) POST 요청을 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-726">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="8a501-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="8a501-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-729">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-729">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-730">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="8a501-730">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="8a501-731">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-732">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-732">Allowed From</span></span>

<span data-ttu-id="8a501-733">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-734">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-734">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a><span data-ttu-id="8a501-735">nx_web_http_client_post_secure_start</span><span class="sxs-lookup"><span data-stu-id="8a501-735">nx_web_http_client_post_secure_start</span></span>

<span data-ttu-id="8a501-736">암호화된 HTTPS POST 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-736">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-737">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-737">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-738">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-738">Description</span></span>

<span data-ttu-id="8a501-739">이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-739">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="8a501-740">이 서비스는 지정된 리소스가 포함된 POST 요청을, 제공된 IP 주소 및 포트의 HTTPS 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-740">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="8a501-741">이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-741">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="8a501-742">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-742">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8a501-743">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-743">This service is deprecated.</span></span> <span data-ttu-id="8a501-744">개발자는 *nx_web_http_client_post_secure_start_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-744">Developers are encouraged to use *nx_web_http_client_post_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-745">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-745">Input Parameters</span></span>

- <span data-ttu-id="8a501-746">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-746">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-747">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-747">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-748">**server_port** 원격 HTTP 서버의 TCP 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-748">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-749">**resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-749">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="8a501-750">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-750">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-751">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-751">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-752">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-752">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-753">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-753">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-754">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-754">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-755">**total_bytes** 전송 중인 리소스의 총 바이트 수.</span><span class="sxs-lookup"><span data-stu-id="8a501-755">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8a501-756">후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-756">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="8a501-757">**tls_setup** TLS 구성을 설정하는 데 사용되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-757">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="8a501-758">애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-758">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="8a501-759">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-759">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-760">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-760">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-761">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-761">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-763">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-763">Return Values</span></span>

- <span data-ttu-id="8a501-764">**NX_SUCCESS** (0x00) POST 요청을 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-764">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="8a501-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="8a501-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-767">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-767">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-768">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="8a501-768">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="8a501-769">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-769">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-770">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-770">Allowed From</span></span>

<span data-ttu-id="8a501-771">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-771">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-772">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-772">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a><span data-ttu-id="8a501-773">nx_web_http_client_post_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-773">nx_web_http_client_post_secure_start_extended</span></span>

<span data-ttu-id="8a501-774">암호화된 HTTPS POST 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-774">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-775">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-775">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-776">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-776">Description</span></span>

<span data-ttu-id="8a501-777">이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-777">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="8a501-778">이 서비스는 지정된 리소스가 포함된 POST 요청을, 제공된 IP 주소 및 포트의 HTTPS 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-778">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="8a501-779">이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-779">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="8a501-780">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-780">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8a501-781">리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-781">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-782">이 서비스는 *nx_web_http_client_post_secure_start* ()를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-782">This service replaces *nx_web_http_client_post_secure_start* ().</span></span> <span data-ttu-id="8a501-783">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-783">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-784">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-784">Input Parameters</span></span>

- <span data-ttu-id="8a501-785">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-785">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-786">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-786">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-787">**server_port** 원격 HTTP 서버의 TCP 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-787">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-788">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-788">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-789">**resource_length** 요청된 리소스의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-789">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="8a501-790">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-790">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-791">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-791">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-792">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-792">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-793">**host_length** 호스트의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-793">**host_length** String length of host.</span></span>
- <span data-ttu-id="8a501-794">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-794">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-795">**username_length** 인증을 위한 사용자 이름의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-795">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="8a501-796">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-796">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-797">**password_length** 인증을 위한 암호의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-797">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="8a501-798">**total_bytes** 전송 중인 리소스의 총 바이트 수.</span><span class="sxs-lookup"><span data-stu-id="8a501-798">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8a501-799">후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-799">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="8a501-800">**tls_setup** TLS 구성을 설정하는 데 사용되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-800">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="8a501-801">애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-801">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="8a501-802">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-802">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-803">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-803">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-804">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-804">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-806">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-806">Return Values</span></span>

- <span data-ttu-id="8a501-807">**NX_SUCCESS** (0x00) POST 요청을 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-807">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="8a501-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="8a501-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-810">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-810">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-811">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="8a501-811">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="8a501-812">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-812">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-813">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-813">Allowed From</span></span>

<span data-ttu-id="8a501-814">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-814">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-815">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-815">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a><span data-ttu-id="8a501-816">nx_web_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="8a501-816">nx_web_http_client_put_start</span></span>

<span data-ttu-id="8a501-817">HTTP PUT 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-817">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-818">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-818">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-819">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-819">Description</span></span>

<span data-ttu-id="8a501-820">이 메서드는 **일반 텍스트** HTTP에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-820">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="8a501-821">이 서비스는 지정된 리소스가 포함된 PUT 요청을, 제공된 IP 주소 및 포트의 HTTP 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-821">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="8a501-822">이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-822">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="8a501-823">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-823">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8a501-824">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-824">This service is deprecated.</span></span> <span data-ttu-id="8a501-825">개발자는 *nx_web_http_client_put_start_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-825">Developers are encouraged to use *nx_web_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-826">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-826">Input Parameters</span></span>

- <span data-ttu-id="8a501-827">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-827">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-828">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-828">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-829">**server_port** 원격 HTTP 서버의 TCP 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-829">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-830">**resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-830">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="8a501-831">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-831">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-832">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-832">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-833">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-833">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-834">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-834">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-835">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-835">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-836">**total_bytes** 전송 중인 리소스의 총 바이트 수.</span><span class="sxs-lookup"><span data-stu-id="8a501-836">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8a501-837">후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-837">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="8a501-838">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-838">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-839">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-839">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-840">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-840">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-842">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-842">Return Values</span></span>

- <span data-ttu-id="8a501-843">**NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-843">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="8a501-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="8a501-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-846">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-846">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-847">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="8a501-847">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="8a501-848">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-848">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-849">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-849">Allowed From</span></span>

<span data-ttu-id="8a501-850">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-850">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-851">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-851">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a><span data-ttu-id="8a501-852">nx_web_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-852">nx_web_http_client_put_start_extended</span></span>

<span data-ttu-id="8a501-853">HTTP PUT 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-853">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-854">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-854">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-855">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-855">Description</span></span>

<span data-ttu-id="8a501-856">이 메서드는 **일반 텍스트** HTTP에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-856">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="8a501-857">이 서비스는 지정된 리소스가 포함된 PUT 요청을, 제공된 IP 주소 및 포트의 HTTP 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-857">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="8a501-858">이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-858">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="8a501-859">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-859">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8a501-860">리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-860">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-861">이 서비스는 *nx_web_http_client_put_start* ()를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-861">This service replaces *nx_web_http_client_put_start* ().</span></span> <span data-ttu-id="8a501-862">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-862">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-863">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-863">Input Parameters</span></span>

- <span data-ttu-id="8a501-864">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-864">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-865">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-865">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-866">**server_port** 원격 HTTP 서버의 TCP 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-866">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-867">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-867">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-868">**resource_length** 요청된 리소스의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-868">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="8a501-869">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-869">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-870">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-870">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-871">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-871">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-872">**host_length** 호스트의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-872">**host_length** String length of host.</span></span>
- <span data-ttu-id="8a501-873">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-873">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-874">**username_length** 인증을 위한 사용자 이름의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-874">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="8a501-875">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-875">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-876">**password_length** 인증을 위한 암호의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-876">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="8a501-877">**total_bytes** 전송 중인 리소스의 총 바이트 수.</span><span class="sxs-lookup"><span data-stu-id="8a501-877">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8a501-878">후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-878">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="8a501-879">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-879">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-880">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-880">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-881">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-881">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-883">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-883">Return Values</span></span>

- <span data-ttu-id="8a501-884">**NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-884">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="8a501-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="8a501-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-887">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-887">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-888">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="8a501-888">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="8a501-889">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-889">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-890">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-890">Allowed From</span></span>

<span data-ttu-id="8a501-891">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-892">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-892">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a><span data-ttu-id="8a501-893">nx_web_http_client_put_secure_start</span><span class="sxs-lookup"><span data-stu-id="8a501-893">nx_web_http_client_put_secure_start</span></span>

<span data-ttu-id="8a501-894">암호화된 HTTPS PUT 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-894">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-895">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-895">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-896">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-896">Description</span></span>

<span data-ttu-id="8a501-897">이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-897">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="8a501-898">이 서비스는 지정된 리소스가 포함된 PUT 요청을, 제공된 IP 주소 및 포트의 HTTPS 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-898">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="8a501-899">이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-899">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="8a501-900">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-900">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8a501-901">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-901">This service is deprecated.</span></span> <span data-ttu-id="8a501-902">개발자는 *nx_web_http_client_put_secure_start_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-902">Developers are encouraged to use *nx_web_http_client_put_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-903">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-903">Input Parameters</span></span>

- <span data-ttu-id="8a501-904">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-904">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-905">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-905">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-906">**server_port** 원격 HTTP 서버의 TCP 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-906">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-907">**resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-907">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="8a501-908">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-908">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-909">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-909">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-910">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-910">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-911">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-911">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-912">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-912">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-913">**total_bytes** 전송 중인 리소스의 총 바이트 수.</span><span class="sxs-lookup"><span data-stu-id="8a501-913">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8a501-914">후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-914">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="8a501-915">**tls_setup** TLS 구성을 설정하는 데 사용되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-915">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="8a501-916">애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-916">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="8a501-917">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-917">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-918">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-919">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-919">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-921">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-921">Return Values</span></span>

- <span data-ttu-id="8a501-922">**NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-922">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="8a501-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="8a501-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-925">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-925">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-926">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="8a501-926">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="8a501-927">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-927">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-928">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-928">Allowed From</span></span>

<span data-ttu-id="8a501-929">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-929">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-930">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-930">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a><span data-ttu-id="8a501-931">nx_web_http_client_put_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-931">nx_web_http_client_put_secure_start_extended</span></span>

<span data-ttu-id="8a501-932">암호화된 HTTPS PUT 요청 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-932">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-933">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-933">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-934">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-934">Description</span></span>

<span data-ttu-id="8a501-935">이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-935">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="8a501-936">이 서비스는 지정된 리소스가 포함된 PUT 요청을, 제공된 IP 주소 및 포트의 HTTPS 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-936">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="8a501-937">이 루틴이 성공하면 애플리케이션 코드에서 *nx_web_http_client_put_packet()* 루틴을 연속적으로 호출하여 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-937">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="8a501-938">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-938">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8a501-939">리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-939">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-940">이 서비스는 *nx_web_http_client_put_secure_start*()를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-940">This service replaces *nx_web_http_client_put_secure_start*().</span></span> <span data-ttu-id="8a501-941">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-941">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-942">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-942">Input Parameters</span></span>

- <span data-ttu-id="8a501-943">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-943">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-944">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-944">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8a501-945">**server_port** 원격 HTTP 서버의 TCP 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-945">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="8a501-946">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-946">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8a501-947">**resource_length** 요청된 리소스의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-947">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="8a501-948">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-948">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-949">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-949">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-950">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-950">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-951">**host_length** 호스트의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-951">**host_length** String length of host.</span></span>
- <span data-ttu-id="8a501-952">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-952">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-953">**username_length** 인증을 위한 사용자 이름의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-953">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="8a501-954">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-954">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-955">**password_length** 인증을 위한 암호의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-955">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="8a501-956">**total_bytes** 전송 중인 리소스의 총 바이트 수.</span><span class="sxs-lookup"><span data-stu-id="8a501-956">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8a501-957">후속 호출을 통해 *nx_web_http_client_put_packet()* 에 보내는 모든 패킷의 총 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-957">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="8a501-958">**tls_setup** TLS 구성을 설정하는 데 사용되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-958">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="8a501-959">애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-959">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="8a501-960">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-960">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-961">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-961">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-962">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-962">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-964">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-964">Return Values</span></span>

- <span data-ttu-id="8a501-965">**NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-965">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="8a501-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) 사용자 이름이 버퍼에 비해 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="8a501-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-968">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-968">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-969">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="8a501-969">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="8a501-970">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-970">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-971">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-971">Allowed From</span></span>

<span data-ttu-id="8a501-972">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-972">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-973">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-973">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a><span data-ttu-id="8a501-974">nx_web_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="8a501-974">nx_web_http_client_put_packet</span></span>

<span data-ttu-id="8a501-975">다음 리소스 데이터 패킷 보내기</span><span class="sxs-lookup"><span data-stu-id="8a501-975">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-976">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-976">Prototype</span></span>

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-977">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-977">Description</span></span>

<span data-ttu-id="8a501-978">이 서비스는 PUT 및 POST 작업에서 리소스 콘텐츠의 다음 패킷을 HTTP 서버로 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-978">This service attempts to send the next packet of resource content to the HTTP Server for both PUT and POST operations.</span></span> <span data-ttu-id="8a501-979">전송된 모든 패킷의 총 길이가 위의 *nx_web_http_client_put_start()* 또는 *nx_web_http_client_post_start()* 호출(또는 해당하는 보안 버전)에 지정된 "total_bytes"와 같을 때까지 이 루틴을 반복적으로 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-979">Note that this routine should be called repetitively until the combined length of the packets sent equals the "total_bytes" specified in the previous *nx_web_http_client_put_start()* or *nx_web_http_client_post_start()* call (or their corresponding secure versions).</span></span>

<span data-ttu-id="8a501-980">또한 이 서비스는 HTTP(또는 HTTPS) 연결 설정에 문제가 있는 경우에 서버의 응답을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-980">This service also checks for a response from the server in case there was a problem establishing the HTTP (or HTTPS) connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-981">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-981">Input Parameters</span></span>

- <span data-ttu-id="8a501-982">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-982">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-983">**packet_ptr** HTTP 서버에 보내는 리소스의 다음 콘텐츠에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-983">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="8a501-984">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-984">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-985">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-985">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-986">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-986">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-988">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-988">Return Values</span></span>

- <span data-ttu-id="8a501-989">**NX_SUCCESS** (0x00) HTTP 클라이언트 패킷을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-989">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="8a501-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 준비되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="8a501-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE**(0x3000E) 서버 오류 코드가 수신되었습니다.\*\*</span><span class="sxs-lookup"><span data-stu-id="8a501-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Received Server error code\*\*</span></span>
- <span data-ttu-id="8a501-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) 패킷 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="8a501-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) 이름 및/또는 암호가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or Password</span></span>
- <span data-ttu-id="8a501-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) PUT이 완료되기 전에 서버가 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Server responds before PUT is complete</span></span>
- <span data-ttu-id="8a501-995">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-995">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-996">NX_INVALID_PACKET (0x12) 패킷이 TCP 헤더에 비해 너무 작음</span><span class="sxs-lookup"><span data-stu-id="8a501-996">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="8a501-997">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-997">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-998">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-998">Allowed From</span></span>

<span data-ttu-id="8a501-999">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-999">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1000">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1000">Example</span></span>

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a><span data-ttu-id="8a501-1001">nx_web_http_client_request_chunked_set</span><span class="sxs-lookup"><span data-stu-id="8a501-1001">nx_web_http_client_request_chunked_set</span></span>

<span data-ttu-id="8a501-1002">HTTP(S) 요청에 대한 청크 분할 전송 설정</span><span class="sxs-lookup"><span data-stu-id="8a501-1002">Set chunked transfer for HTTP(S) request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1003">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1003">Prototype</span></span>

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="8a501-1004">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1004">Description</span></span>

<span data-ttu-id="8a501-1005">이 서비스는 청크 분할 전송 코딩을 사용하여 이전에 원격 호스트에 대한 소켓 연결을 설정한 *nx_web_http_client_connect()* 또는 *nx_web_http_client_secure_connect()* 호출에서 지정한 서버로 사용자 지정 HTTP(S) 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1005">This service uses chunked transfer coding to send a custom HTTP(S) request to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* call which has previously established the socket connection to the remote host.</span></span>

> [!NOTE]
> <span data-ttu-id="8a501-1006">애플리케이션에서 청크 분할 전송 코딩을 사용하여 요청 데이터 패킷을 보내는 경우 애플리케이션에서 *nx_web_http_client_request_packet_allocate*()를 호출한 후, 그리고 *nx_web_http_client_reqeust_packet_send* ()를 호출하기 전에 이 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1006">If the application uses chunked transfer coding to send a request data packet, it must call this service after calling *nx_web_http_client_request_packet_allocate*(), and before call *nx_web_http_client_reqeust_packet_send* ().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1007">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1007">Input Parameters</span></span>

- <span data-ttu-id="8a501-1008">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1008">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-1009">**chunk_size** 청크 데이터의 크기(8진수)</span><span class="sxs-lookup"><span data-stu-id="8a501-1009">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="8a501-1010">**packet_ptr** HTTP(S) 요청 데이터 패킷 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1010">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1011">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1011">Return Values</span></span>

- <span data-ttu-id="8a501-1012">**NX_SUCCESS** (0x00) 청크 분할을 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1012">**NX_SUCCESS** (0x00) Successfully set chunked.</span></span>
- <span data-ttu-id="8a501-1013">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1013">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1014">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1014">Allowed From</span></span>

<span data-ttu-id="8a501-1015">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1015">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1016">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1016">Example</span></span>

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a><span data-ttu-id="8a501-1017">nx_web_http_client_request_header_add</span><span class="sxs-lookup"><span data-stu-id="8a501-1017">nx_web_http_client_request_header_add</span></span>

<span data-ttu-id="8a501-1018">사용자 지정 HTTP 요청에 사용자 지정 헤더 추가</span><span class="sxs-lookup"><span data-stu-id="8a501-1018">Add a custom header to a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1019">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1019">Prototype</span></span>

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-1020">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1020">Description</span></span>

<span data-ttu-id="8a501-1021">이 서비스는 n *x_web_http_client_request_initialize()* 를 사용하여 만든 사용자 지정 HTTP 요청에 사용자 지정 헤더를 (필드 이름 및 값 형식으로) 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1021">This service adds a custom header (in the form of a field name and value) to a custom HTTP request created with n *x_web_http_client_request_initialize()*.</span></span>

<span data-ttu-id="8a501-1022">이 서비스를 사용하면 애플리케이션에서 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1022">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="8a501-1023">**이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8a501-1023">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="8a501-1024">편의를 위해 nx_web_http_client_\*_start 메서드가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1024">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="8a501-1025">이 모든 함수는 내부적으로(*nx_web_http_client_request_initialize()와 함께)* 이 루틴을 사용하여 HTTP 요청을 만들고 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1025">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1026">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1026">Input Parameters</span></span>

- <span data-ttu-id="8a501-1027">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1027">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-1028">**field_name** 필드 이름 문자열(예: "Content-Type")</span><span class="sxs-lookup"><span data-stu-id="8a501-1028">**field_name** Field name string (e.g. "Content-Type").</span></span>
- <span data-ttu-id="8a501-1029">**name_length** 필드 이름 문자열의 길이(바이트)</span><span class="sxs-lookup"><span data-stu-id="8a501-1029">**name_length** Length of field name string in bytes.</span></span>
- <span data-ttu-id="8a501-1030">**field_value** 필드 값 문자열(예: "application/octet-stream")</span><span class="sxs-lookup"><span data-stu-id="8a501-1030">**field_value** Field value string (e.g. "application/octet-stream").</span></span>
- <span data-ttu-id="8a501-1031">**value_length** 값 문자열의 길이(바이트)</span><span class="sxs-lookup"><span data-stu-id="8a501-1031">**value_length** Length of value string in bytes.</span></span>
- <span data-ttu-id="8a501-1032">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1032">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-1033">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1033">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-1034">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1034">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1036">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1036">Return Values</span></span>

- <span data-ttu-id="8a501-1037">**NX_SUCCESS** (0x00) 헤더를 요청에 추가했습니다</span><span class="sxs-lookup"><span data-stu-id="8a501-1037">**NX_SUCCESS** (0x00) Successful addition of header to request.</span></span>
- <span data-ttu-id="8a501-1038">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1038">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1039">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1039">Allowed From</span></span>

<span data-ttu-id="8a501-1040">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1040">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1041">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1041">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a><span data-ttu-id="8a501-1042">nx_web_http_client_request_initialize</span><span class="sxs-lookup"><span data-stu-id="8a501-1042">nx_web_http_client_request_initialize</span></span>

<span data-ttu-id="8a501-1043">사용자 지정 HTTP 요청 초기화</span><span class="sxs-lookup"><span data-stu-id="8a501-1043">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1044">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1044">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-1045">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1045">Description</span></span>

<span data-ttu-id="8a501-1046">이 서비스는 사용자 지정 HTTP 요청을 만들고 HTTP 클라이언트 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1046">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="8a501-1047">간단한 *nx_web_http_client_get_start()* 와 달리(해당 API의 PUT, POST 및 관련 보안 버전에 대한 메서드 포함), 사용자 지정 요청은 *nx_web_http_client_request_send()* 서비스를 호출할 때까지 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1047">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="8a501-1048">이 서비스를 사용하면 애플리케이션에서 ***nx_web_http_client_request_header_add()*** 서비스를 사용하여 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1048">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="8a501-1049">이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1049">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="8a501-1050">편의를 위해 nx_web_http_client_\*_start 메서드가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1050">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="8a501-1051">이 모든 함수는 내부적으로(*nx_web_http_client_request_send()와 함께)* 이 루틴을 사용하여 HTTP 요청을 만들고 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1051">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="8a501-1052">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1052">This service is deprecated.</span></span> <span data-ttu-id="8a501-1053">개발자는 *nx_web_http_client_request_initialize_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1053">Developers are encouraged to use *nx_web_http_client_request_initialize_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1054">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1054">Input Parameters</span></span>

- <span data-ttu-id="8a501-1055">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1055">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-1056">**method** 사용할 HTTP 요청 메서드.</span><span class="sxs-lookup"><span data-stu-id="8a501-1056">**method** The HTTP request method to use.</span></span> <span data-ttu-id="8a501-1057">옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1057">The options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="8a501-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="8a501-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="8a501-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="8a501-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="8a501-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="8a501-1064">**resource** 전송되는 리소스의 이름</span><span class="sxs-lookup"><span data-stu-id="8a501-1064">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="8a501-1065">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-1065">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-1066">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1066">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-1067">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1067">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-1068">**input_size** PUT 및 POST 작업의 입력 데이터 크기.</span><span class="sxs-lookup"><span data-stu-id="8a501-1068">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="8a501-1069">다른 작업에는 0을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1069">Pass 0 for other operations.</span></span>
- <span data-ttu-id="8a501-1070">**transfer_encoding_trunked** 향후 트렁크 전송을 지원하기 위해 예약된 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1070">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="8a501-1071">**username** 보호된 리소스의 사용자 이름</span><span class="sxs-lookup"><span data-stu-id="8a501-1071">**username** Username for protected resources.</span></span>
- <span data-ttu-id="8a501-1072">**password** 보호된 리소스의 암호</span><span class="sxs-lookup"><span data-stu-id="8a501-1072">**password** Password for protected resources.</span></span>
- <span data-ttu-id="8a501-1073">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1073">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-1074">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1074">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-1075">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1075">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1077">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1077">Return Values</span></span>

- <span data-ttu-id="8a501-1078">**NX_SUCCESS** (0x00) 요청을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1078">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="8a501-1079">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1079">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) 필요한 일부 정보가 누락되었습니다(예: PUT 또는 POST 작업의 input_size).</span><span class="sxs-lookup"><span data-stu-id="8a501-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1081">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1081">Allowed From</span></span>

<span data-ttu-id="8a501-1082">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1082">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1083">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1083">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a><span data-ttu-id="8a501-1084">nx_web_http_client_request_initialize_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-1084">nx_web_http_client_request_initialize_extended</span></span>

<span data-ttu-id="8a501-1085">사용자 지정 HTTP 요청 초기화</span><span class="sxs-lookup"><span data-stu-id="8a501-1085">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1086">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1086">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, UINT method,
    CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, UINT username_length,
    CHAR *password, UINT password_length, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-1087">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1087">Description</span></span>

<span data-ttu-id="8a501-1088">이 서비스는 사용자 지정 HTTP 요청을 만들고 HTTP 클라이언트 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1088">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="8a501-1089">간단한 *nx_web_http_client_get_start()* 와 달리(해당 API의 PUT, POST 및 관련 보안 버전에 대한 메서드 포함), 사용자 지정 요청은 *nx_web_http_client_request_send()* 서비스를 호출할 때까지 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1089">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="8a501-1090">이 서비스를 사용하면 애플리케이션에서 ***nx_web_http_client_request_header_add()*** 서비스를 사용하여 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1090">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="8a501-1091">이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1091">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="8a501-1092">편의를 위해 nx_web_http_client_\*_start 메서드가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1092">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="8a501-1093">이 모든 함수는 내부적으로(*nx_web_http_client_request_send()와 함께)* 이 루틴을 사용하여 HTTP 요청을 만들고 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1093">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="8a501-1094">리소스, 호스트, 사용자 이름 및 암호의 문자열은 NULL로 종결되어야 하며 각 문자열의 길이는 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1094">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-1095">이 서비스는 *nx_web_http_client_request_initialize*()를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1095">This service replaces *nx_web_http_client_request_initialize*().</span></span> <span data-ttu-id="8a501-1096">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1096">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1097">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1097">Input Parameters</span></span>

- <span data-ttu-id="8a501-1098">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1098">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-1099">**method** 사용할 HTTP 요청 메서드.</span><span class="sxs-lookup"><span data-stu-id="8a501-1099">**method** The HTTP request method to use.</span></span> <span data-ttu-id="8a501-1100">옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1100">The options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="8a501-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="8a501-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="8a501-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="8a501-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="8a501-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="8a501-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="8a501-1107">**resource** 전송되는 리소스의 이름</span><span class="sxs-lookup"><span data-stu-id="8a501-1107">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="8a501-1108">**resource_length** 요청된 리소스의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-1108">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="8a501-1109">**host** 서버 도메인 이름의 Null 종료 문자열.</span><span class="sxs-lookup"><span data-stu-id="8a501-1109">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="8a501-1110">이 문자열은 HTTP 호스트 헤더 필드를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1110">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="8a501-1111">호스트 문자열은 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1111">The host string cannot be NULL.</span></span>
- <span data-ttu-id="8a501-1112">**host_length** 호스트의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-1112">**host_length** String length of host.</span></span>
- <span data-ttu-id="8a501-1113">**input_size** PUT 및 POST 작업의 입력 데이터 크기.</span><span class="sxs-lookup"><span data-stu-id="8a501-1113">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="8a501-1114">다른 작업에는 0을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1114">Pass 0 for other operations.</span></span>
- <span data-ttu-id="8a501-1115">**transfer_encoding_trunked** 향후 트렁크 전송을 지원하기 위해 예약된 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1115">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="8a501-1116">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1116">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8a501-1117">**username_length** 인증을 위한 사용자 이름의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-1117">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="8a501-1118">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1118">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8a501-1119">**password_length** 인증을 위한 암호의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-1119">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="8a501-1120">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1120">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-1121">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1121">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-1122">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1122">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1124">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1124">Return Values</span></span>

- <span data-ttu-id="8a501-1125">**NX_SUCCESS** (0x00) 요청을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1125">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="8a501-1126">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1126">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) 필요한 일부 정보가 누락되었습니다(예: PUT 또는 POST 작업의 input_size).</span><span class="sxs-lookup"><span data-stu-id="8a501-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1128">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1128">Allowed From</span></span>

<span data-ttu-id="8a501-1129">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1130">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1130">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a><span data-ttu-id="8a501-1131">nx_web_http_client_request_packet_send</span><span class="sxs-lookup"><span data-stu-id="8a501-1131">nx_web_http_client_request_packet_send</span></span>

<span data-ttu-id="8a501-1132">HTTP(S) 요청 데이터 패킷을 원격 서버에 보내기</span><span class="sxs-lookup"><span data-stu-id="8a501-1132">Send HTTP(S) request data packet to remote server</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1133">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1133">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-1134">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1134">Description</span></span>

<span data-ttu-id="8a501-1135">이 서비스는 *nx_web_http_client_request_packet_allocate* ()를 사용하여 만든 사용자 지정 HTTP(S) 요청 데이터 패킷을, 이전에 원격 호스트에 대한 소켓 연결을 설정한 *nx_web_http_client_connect()* 또는 *nx_web_http_client_secure_connect(* ) 호출에서 지정한 서버로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1135">This service sends a custom HTTP(S) request data packet created with *nx_web_http_client_request_packet_allocate* () to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect(*) call which has previously established the socket connection to the remote host.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1136">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1136">Input Parameters</span></span>

- <span data-ttu-id="8a501-1137">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1137">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-1138">**packet_ptr** HTTP(S) 요청 데이터 패킷 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1138">**packet_ptr** HTTP(S) request data packet pointer.</span></span>
- <span data-ttu-id="8a501-1139">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1139">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-1140">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1140">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-1141">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1141">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1143">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1143">Return Values</span></span>

- <span data-ttu-id="8a501-1144">**NX_SUCCESS** (0x00) 요청 데이터 패킷을 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1144">**NX_SUCCESS** (0x00) Successful send of request data packet.</span></span>
- <span data-ttu-id="8a501-1145">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1145">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1146">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1146">Allowed From</span></span>

<span data-ttu-id="8a501-1147">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1148">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1148">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a><span data-ttu-id="8a501-1149">nx_web_http_client_request_send</span><span class="sxs-lookup"><span data-stu-id="8a501-1149">nx_web_http_client_request_send</span></span>

<span data-ttu-id="8a501-1150">사용자 지정 HTTP 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="8a501-1150">Send a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1151">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1151">Prototype</span></span>

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-1152">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1152">Description</span></span>

<span data-ttu-id="8a501-1153">이 서비스는 *nx_web_http_client_request_initialize()* 를 사용하여 만든 사용자 지정 HTTP 요청을, 이전에 원격 호스트에 대한 소켓 연결을 설정한 *nx_web_http_client_connect()* 또는 *nx_web_http_client_secure_connect(* ) 호출에서 지정한 서버로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1153">This service sends a custom HTTP request created with *nx_web_http_client_request_initialize()* to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* both of which have previously established the socket connection to the remote host.</span></span>

<span data-ttu-id="8a501-1154">이 서비스를 사용하면 애플리케이션에서 ***nx_web_http_client_request_header_add()*** 서비스를 사용하여 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1154">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="8a501-1155">이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1155">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="8a501-1156">편의를 위해 nx_web_http_client_\*_start 메서드가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1156">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="8a501-1157">이 모든 함수는 내부적으로(*nx_web_http_client_request_initialize()와 함께)* 이 루틴을 사용하여 HTTP 요청을 만들고 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1157">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1158">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1158">Input Parameters</span></span>

- <span data-ttu-id="8a501-1159">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1159">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-1160">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1160">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-1161">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1161">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-1162">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1162">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1164">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1164">Return Values</span></span>

- <span data-ttu-id="8a501-1165">**NX_SUCCESS** (0x00) 요청을 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1165">**NX_SUCCESS** (0x00) Successful send of request.</span></span>
- <span data-ttu-id="8a501-1166">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1166">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1167">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1167">Allowed From</span></span>

<span data-ttu-id="8a501-1168">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1169">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1169">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a><span data-ttu-id="8a501-1170">nx_web_http_client_response_body_get</span><span class="sxs-lookup"><span data-stu-id="8a501-1170">nx_web_http_client_response_body_get</span></span>

<span data-ttu-id="8a501-1171">다음 리소스 데이터 패킷 가져오기</span><span class="sxs-lookup"><span data-stu-id="8a501-1171">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1172">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1172">Prototype</span></span>

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-1173">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1173">Description</span></span>

<span data-ttu-id="8a501-1174">이 서비스는 이전 *nx_web_http_client_get_start()* 또는 *nx_web_http_client_get_secure_start()* 호출에서 요청한 리소스 콘텐츠의 다음 패킷을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1174">This service retrieves the next packet of content of the resource requested by the previous *nx_web_http_client_get_start()* or *nx_web_http_client_get_secure_start()* call.</span></span> <span data-ttu-id="8a501-1175">NX_WEB_HTTP_GET_DONE의 반환 상태를 받을 때까지 이 루틴을 연속적으로 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1175">Successive calls to this routine should be made until the return status of NX_WEB_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1176">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1176">Input Parameters</span></span>

- <span data-ttu-id="8a501-1177">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1177">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-1178">**packet_ptr** 부분 리소스 콘텐츠가 포함된 패킷 포인터의 대상</span><span class="sxs-lookup"><span data-stu-id="8a501-1178">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="8a501-1179">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1179">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-1180">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1180">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-1181">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1181">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1183">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1183">Return Values</span></span>

- <span data-ttu-id="8a501-1184">**NX_SUCCESS** (0x00) HTTP 클라이언트 패킷을 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1184">**NX_SUCCESS** (0x00) Successful get of HTTP Client packet.</span></span>
- <span data-ttu-id="8a501-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP 클라이언트 GET 패킷이 완료됨</span><span class="sxs-lookup"><span data-stu-id="8a501-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP Client get packet is done</span></span>
- <span data-ttu-id="8a501-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP 클라이언트가 가져오기 모드로 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="8a501-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) 패킷 길이가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="8a501-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP 상태 코드 100 계속</span><span class="sxs-lookup"><span data-stu-id="8a501-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP status code 100 Continue</span></span>
- <span data-ttu-id="8a501-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP 상태 코드 101 프로토콜 전환</span><span class="sxs-lookup"><span data-stu-id="8a501-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP status code 101 Switching Protocols</span></span>
- <span data-ttu-id="8a501-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP 상태 코드 201 생성됨</span><span class="sxs-lookup"><span data-stu-id="8a501-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP status code 201 Created</span></span>
- <span data-ttu-id="8a501-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP 상태 코드 202 수락됨</span><span class="sxs-lookup"><span data-stu-id="8a501-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP status code 202 Accepted</span></span>
- <span data-ttu-id="8a501-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP 상태 코드 203 신뢰할 수 없는 정보</span><span class="sxs-lookup"><span data-stu-id="8a501-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP status code 203 Non-Authoritative Information</span></span>
- <span data-ttu-id="8a501-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP 상태 코드 204 콘텐츠 없음</span><span class="sxs-lookup"><span data-stu-id="8a501-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP status code 204 No Content</span></span>
- <span data-ttu-id="8a501-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP 상태 코드 205 콘텐츠 다시 설정</span><span class="sxs-lookup"><span data-stu-id="8a501-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP status code 205 Reset Content</span></span>
- <span data-ttu-id="8a501-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP 상태 코드 206 부분 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="8a501-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP status code 206 Partial Content</span></span>
- <span data-ttu-id="8a501-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP 상태 코드 300 여러 선택 항목</span><span class="sxs-lookup"><span data-stu-id="8a501-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP status code 300 Multiple Choices</span></span>
- <span data-ttu-id="8a501-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP 상태 코드 301 영구적으로 이동됨</span><span class="sxs-lookup"><span data-stu-id="8a501-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP status code 301 Moved Permanently</span></span>
- <span data-ttu-id="8a501-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP 상태 코드 302 있음</span><span class="sxs-lookup"><span data-stu-id="8a501-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP status code 302 Found</span></span>
- <span data-ttu-id="8a501-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP 상태 코드 303 기타 참조</span><span class="sxs-lookup"><span data-stu-id="8a501-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP status code 303 See Other</span></span>
- <span data-ttu-id="8a501-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP 상태 코드 304 수정되지 않음</span><span class="sxs-lookup"><span data-stu-id="8a501-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP status code 304 Not Modified</span></span>
- <span data-ttu-id="8a501-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP 상태 코드 305 프록시 사용</span><span class="sxs-lookup"><span data-stu-id="8a501-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP status code 305 Use Proxy</span></span>
- <span data-ttu-id="8a501-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP 상태 코드 307 임시 리디렉션</span><span class="sxs-lookup"><span data-stu-id="8a501-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP status code 307 Temporary Redirect</span></span>
- <span data-ttu-id="8a501-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP 상태 코드 400 잘못된 요청</span><span class="sxs-lookup"><span data-stu-id="8a501-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP status code 400 Bad Request</span></span>
- <span data-ttu-id="8a501-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP 상태 코드 401 권한 없음</span><span class="sxs-lookup"><span data-stu-id="8a501-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP status code 401 Unauthorized</span></span>
- <span data-ttu-id="8a501-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP 상태 코드 402 결제 필요</span><span class="sxs-lookup"><span data-stu-id="8a501-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP status code 402 Payment Required</span></span>
- <span data-ttu-id="8a501-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP 상태 코드 403 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="8a501-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP status code 403 Forbidden</span></span>
- <span data-ttu-id="8a501-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP 상태 코드 404 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="8a501-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP status code 404 Not Found</span></span>
- <span data-ttu-id="8a501-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP 상태 코드 405 메서드를 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="8a501-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP status code 405 Method Not Allowed</span></span>
- <span data-ttu-id="8a501-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP 상태 코드 406 허용 안 됨</span><span class="sxs-lookup"><span data-stu-id="8a501-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP status code 406 Not Acceptable</span></span>
- <span data-ttu-id="8a501-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP 상태 코드 407 프록시 인증 필요</span><span class="sxs-lookup"><span data-stu-id="8a501-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP status code 407 Proxy Authentication Required</span></span>
- <span data-ttu-id="8a501-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP 상태 코드 408 요청 시간 제한</span><span class="sxs-lookup"><span data-stu-id="8a501-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP status code 408 Request Time-out</span></span>
- <span data-ttu-id="8a501-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP 상태 코드 409 충돌</span><span class="sxs-lookup"><span data-stu-id="8a501-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP status code 409 Conflict</span></span>
- <span data-ttu-id="8a501-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP 상태 코드 410 없음</span><span class="sxs-lookup"><span data-stu-id="8a501-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP status code 410 Gone</span></span>
- <span data-ttu-id="8a501-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP 상태 코드 411 길이가 필요함</span><span class="sxs-lookup"><span data-stu-id="8a501-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP status code 411 Length Required</span></span>
- <span data-ttu-id="8a501-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP 상태 코드 412 사전 조건 실패</span><span class="sxs-lookup"><span data-stu-id="8a501-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP status code 412 Precondition Failed</span></span>
- <span data-ttu-id="8a501-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP 상태 코드 413 요청 엔터티가 너무 큼</span><span class="sxs-lookup"><span data-stu-id="8a501-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP status code 413 Request Entity Too Large</span></span>
- <span data-ttu-id="8a501-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP 상태 코드 414 요청 URL이 너무 큼</span><span class="sxs-lookup"><span data-stu-id="8a501-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP status code 414 Request URL Too Large</span></span>
- <span data-ttu-id="8a501-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP 상태 코드 415 지원되지 않는 미디어 형식</span><span class="sxs-lookup"><span data-stu-id="8a501-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP status code 415 Unsupported Media Type</span></span>
- <span data-ttu-id="8a501-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP 상태 코드 416 요청한 범위가 충분하지 않음</span><span class="sxs-lookup"><span data-stu-id="8a501-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP status code 416 Requested range not satisfiable</span></span>
- <span data-ttu-id="8a501-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP 상태 코드 417 예상 실패</span><span class="sxs-lookup"><span data-stu-id="8a501-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP status code 417 Expectation Failed</span></span>
- <span data-ttu-id="8a501-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP 상태 코드 500 내부 서버 오류</span><span class="sxs-lookup"><span data-stu-id="8a501-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP status code 500 Internal Server Error</span></span>
- <span data-ttu-id="8a501-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP 상태 코드 501 구현되지 않음</span><span class="sxs-lookup"><span data-stu-id="8a501-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP status code 501 Not Implemented</span></span>
- <span data-ttu-id="8a501-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP 상태 코드 502 잘못된 게이트웨이</span><span class="sxs-lookup"><span data-stu-id="8a501-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP status code 502 Bad Gateway</span></span>
- <span data-ttu-id="8a501-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP 상태 코드 503 서비스를 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="8a501-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP status code 503 Service Unavailable</span></span>
- <span data-ttu-id="8a501-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP 상태 코드 504 게이트웨이 시간 제한</span><span class="sxs-lookup"><span data-stu-id="8a501-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP status code 504 Gateway Time-out</span></span>
- <span data-ttu-id="8a501-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) http 상태 코드 505 지원되지 않는 HTTP 버전</span><span class="sxs-lookup"><span data-stu-id="8a501-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP status code 505 HTTP Version not supported</span></span>
- <span data-ttu-id="8a501-1227">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1227">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1228">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-1228">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1229">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1229">Allowed From</span></span>

<span data-ttu-id="8a501-1230">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1231">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1231">Example</span></span>

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a><span data-ttu-id="8a501-1232">nx_web_http_client_response_header_callback_set</span><span class="sxs-lookup"><span data-stu-id="8a501-1232">nx_web_http_client_response_header_callback_set</span></span>

<span data-ttu-id="8a501-1233">HTTP 헤더를 처리할 때 호출할 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="8a501-1233">Set callback to invoke when processing HTTP headers</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1234">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1234">Prototype</span></span>

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a><span data-ttu-id="8a501-1235">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1235">Description</span></span>

<span data-ttu-id="8a501-1236">이 서비스는 NetX 웹 HTTP 클라이언트가 원격 HTTP 서버에서 들어오는 응답의 HTTP 헤더를 처리할 때마다 호출되는 콜백을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1236">This service assigns a callback that will be invoked whenever NetX Web HTTP Client processes an HTTP header in an incoming response from a remote HTTP server.</span></span> <span data-ttu-id="8a501-1237">콜백은 처리되는 응답의 헤더마다 한 번씩 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1237">The callback is invoked once for each header in the response as it is processed.</span></span> <span data-ttu-id="8a501-1238">콜백은 HTTP 애플리케이션이 HTTP 서버 응답의 각 헤더에 액세스하여 NetX 웹 HTTP 클라이언트의 기본 처리 작업 이상의 작업을 수행하는 것을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1238">The callback allows an HTTP Client application to access each of the headers in the HTTP server response to take any desired actions beyond the basic processing that NetX Web HTTP Client does.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1239">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1239">Input Parameters</span></span>

<span data-ttu-id="8a501-1240">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1240">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="8a501-1241">**callback_function** 응답 헤더를 처리하는 동안 호출되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-1241">**callback_function** Callback invoked during response header processing.</span></span> <span data-ttu-id="8a501-1242">콜백은 필드 이름과 값을 문자열(및 해당 길이)로 사용하여 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1242">The callback is invoked with the field name and value as strings (and their lengths).</span></span> <span data-ttu-id="8a501-1243">예를 들어 "Content-Length: 100"이라는 헤더를 사용하면 *field_name* 은 "Content-Length"이고 *field_value* 는 문자열 "100"인 함수가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1243">For example, the header "Content-Length: 100" would cause the function to be invoked with "Content-Length" for *field_name* and the string "100" for *field_value*.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1244">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1244">Return Values</span></span>

- <span data-ttu-id="8a501-1245">**NX_SUCCESS** (0x00) 콜백을 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1245">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="8a501-1246">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1246">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1247">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1247">Allowed From</span></span>

<span data-ttu-id="8a501-1248">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1248">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1249">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1249">Example</span></span>

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a><span data-ttu-id="8a501-1250">nx_web_http_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="8a501-1250">nx_web_http_client_secure_connect</span></span>

<span data-ttu-id="8a501-1251">사용자 지정 요청을 위해 HTTPS 서버에 대한 TLS 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1251">Open a TLS session to an HTTPS server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1252">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1252">Prototype</span></span>

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-1253">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1253">Description</span></span>

<span data-ttu-id="8a501-1254">이 메서드는 **TLS로 보호되는** HTTPS에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1254">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="8a501-1255">이 서비스는 HTTPS 서버에 대한 보안 TLS 세션을 열지만 요청을 보내지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1255">This service opens a secured TLS session to an HTTPS server but does not send any requests.</span></span> <span data-ttu-id="8a501-1256">요청은 n *x_web_http_client_request_initialize()* 를 사용하여 만들어지고 *nx_web_http_client_request_send()* 를 사용하여 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1256">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="8a501-1257">*nx_web_http_client_request_header_add()* 를 사용하여 사용자 지정 HTTP 헤더를 요청에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1257">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="8a501-1258">이 서비스를 사용하면 애플리케이션에서 사용자 지정 헤더를 원하는 만큼 요청에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1258">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="8a501-1259">**이렇게 하면 특정 애플리케이션에 대해 사용자 지정된 HTTP 요청을 수행할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8a501-1259">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="8a501-1260">편의를 위해 nx_web_http_client_\*_start 메서드가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1260">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="8a501-1261">이 모든 함수는 내부적으로(*nx_web_http_client_request_initialize()와 함께)* 이 루틴을 사용하여 HTTP 요청을 만들고 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1261">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1262">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1262">Input Parameters</span></span>

- <span data-ttu-id="8a501-1263">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1263">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-1264">**server_ip** 원격 HTTPS 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-1264">**server_ip** IP address of remote HTTPS server.</span></span>
- <span data-ttu-id="8a501-1265">**server_port** 원격 HTTPS 서버의 포트(예: HTTPS의 경우 443)</span><span class="sxs-lookup"><span data-stu-id="8a501-1265">**server_port** Port on remote HTTPS server (e.g. 443 for HTTPS).</span></span>
- <span data-ttu-id="8a501-1266">**tls_setup** TLS 구성을 설정하는 데 사용되는 콜백.</span><span class="sxs-lookup"><span data-stu-id="8a501-1266">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="8a501-1267">애플리케이션에서는 이 콜백을 정의하여 TLS 암호화 및 자격 증명(예: 인증서)을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1267">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="8a501-1268">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1268">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8a501-1269">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1269">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-1270">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1270">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="8a501-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1272">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1272">Return Values</span></span>

- <span data-ttu-id="8a501-1273">**NX_SUCCESS** (0x00) TLS 세션이 연결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1273">**NX_SUCCESS** (0x00) Successful connection of TLS session.</span></span>
- <span data-ttu-id="8a501-1274">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1275">NX_WEB_HTTP_NOT_READY (0x3000A) 다른 요청이 이미 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1276">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1276">Allowed From</span></span>

<span data-ttu-id="8a501-1277">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1278">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1278">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a><span data-ttu-id="8a501-1279">HTTP 및 HTTPS 서버 API</span><span class="sxs-lookup"><span data-stu-id="8a501-1279">HTTP and HTTPS Server API</span></span>

## <a name="nx_web_http_server_cache_info_callback_set"></a><span data-ttu-id="8a501-1280">nx_web_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="8a501-1280">nx_web_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="8a501-1281">URL 최대 기간 및 날짜를 검색하는 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="8a501-1281">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1282">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1282">Prototype</span></span>

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a><span data-ttu-id="8a501-1283">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1283">Description</span></span>

<span data-ttu-id="8a501-1284">이 서비스는 지정된 리소스의 최대 사용 기간 및 마지막으로 수정한 날짜를 가져오기 위해 호출되는 콜백 서비스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1284">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1285">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1285">Input Parameters</span></span>

- <span data-ttu-id="8a501-1286">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1286">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8a501-1287">**cache_info_get** 콜백에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1287">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="8a501-1288">**max_age** 리소스의 최대 사용 기간에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1288">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="8a501-1289">**data** 반환된 마지막 수정 날짜에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1289">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1290">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1290">Return Values</span></span>

- <span data-ttu-id="8a501-1291">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="8a501-1291">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="8a501-1292">**NX_PTR_ERROR** (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1292">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1293">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1293">Allowed From</span></span>

<span data-ttu-id="8a501-1294">초기화</span><span class="sxs-lookup"><span data-stu-id="8a501-1294">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1295">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1295">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a><span data-ttu-id="8a501-1296">nx_web_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="8a501-1296">nx_web_http_server_callback_data_send</span></span>

<span data-ttu-id="8a501-1297">콜백 함수의 데이터 보내기</span><span class="sxs-lookup"><span data-stu-id="8a501-1297">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1298">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1298">Prototype</span></span>

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="8a501-1299">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1299">Description</span></span>

<span data-ttu-id="8a501-1300">이 서비스는 애플리케이션의 콜백 루틴에서 제공된 패킷의 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1300">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="8a501-1301">일반적으로 GET/POST 요청과 연결된 동적 데이터를 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1301">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="8a501-1302">이 함수를 사용할 경우 콜백 루틴에서 전체 응답을 적절한 형식으로 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1302">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="8a501-1303">또한 콜백 루틴에서 NX_WEB_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1303">In addition, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1304">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1304">Input Parameters</span></span>

- <span data-ttu-id="8a501-1305">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1305">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8a501-1306">**data_ptr** 보내는 데이터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1306">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="8a501-1307">**data_length** 보내는 바이트 수</span><span class="sxs-lookup"><span data-stu-id="8a501-1307">**data_length** Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1308">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1308">Return Values</span></span>

- <span data-ttu-id="8a501-1309">**NX_SUCCESS** (0x00) 서버 데이터를 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-1309">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="8a501-1310">**NX_PTR_ERROR** (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1310">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1311">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1311">Allowed From</span></span>

<span data-ttu-id="8a501-1312">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1313">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1313">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a><span data-ttu-id="8a501-1314">nx_web_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="8a501-1314">nx_web_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="8a501-1315">콜백 함수에서 응답 헤더 만들기</span><span class="sxs-lookup"><span data-stu-id="8a501-1315">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1316">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1316">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="8a501-1317">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1317">Description</span></span>

<span data-ttu-id="8a501-1318">이 서비스는 http 응답 헤더를 생성하기 위해 (애플리케이션에서 정의한) HTTP(S) 서버 콜백 루틴에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1318">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="8a501-1319">HTTP 응답이 필요한 클라이언트 GET, PUT 및 DELETE 요청에 HTTP 서버가 응답할 때 서버 콜백 루틴이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1319">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="8a501-1320">이 함수는 애플리케이션의 응답 정보를 사용하여 적절한 응답 헤더를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1320">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="8a501-1321">서버 요청 콜백 루틴에 대한 자세한 내용은 *nx_web_http_server_create()* 서비스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-1321">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

<span data-ttu-id="8a501-1322">이 API는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1322">This API is deprecated.</span></span> <span data-ttu-id="8a501-1323">개발자는 *nx_web_http_server_callback_generate_response_header_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1323">Developers are encouraged to use *nx_web_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1324">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1324">Input Parameters</span></span>

- <span data-ttu-id="8a501-1325">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1325">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8a501-1326">**packet_pptr** 메시지에 할당된 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1326">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="8a501-1327">**status_code** 리소스 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1327">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="8a501-1328">예제:</span><span class="sxs-lookup"><span data-stu-id="8a501-1328">Examples:</span></span>
  - <span data-ttu-id="8a501-1329">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="8a501-1329">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="8a501-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="8a501-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="8a501-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="8a501-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="8a501-1332">**content_length** 콘텐츠 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="8a501-1332">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="8a501-1333">**content_type** HTTP 형식(예: "텍스트/일반")</span><span class="sxs-lookup"><span data-stu-id="8a501-1333">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="8a501-1334">**additional_header** 추가 헤더 텍스트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1334">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1335">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1335">Return Values</span></span>

- <span data-ttu-id="8a501-1336">**NX_SUCCESS** (0x00) HTML 헤더를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="8a501-1336">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="8a501-1337">**NX_PTR_ERROR** (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1337">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1338">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1338">Allowed From</span></span>

<span data-ttu-id="8a501-1339">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1339">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1340">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1340">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="8a501-1341">nx_web_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-1341">nx_web_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="8a501-1342">콜백 함수에서 응답 헤더 만들기</span><span class="sxs-lookup"><span data-stu-id="8a501-1342">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1343">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1343">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a><span data-ttu-id="8a501-1344">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1344">Description</span></span>

<span data-ttu-id="8a501-1345">이 서비스는 http 응답 헤더를 생성하기 위해 (애플리케이션에서 정의한) HTTP(S) 서버 콜백 루틴에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1345">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="8a501-1346">HTTP 응답이 필요한 클라이언트 GET, PUT 및 DELETE 요청에 HTTP 서버가 응답할 때 서버 콜백 루틴이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1346">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="8a501-1347">이 함수는 애플리케이션의 응답 정보를 사용하여 적절한 응답 헤더를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1347">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="8a501-1348">서버 요청 콜백 루틴에 대한 자세한 내용은 *nx_web_http_server_create()* 서비스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-1348">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1349">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1349">Input Parameters</span></span>

- <span data-ttu-id="8a501-1350">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1350">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8a501-1351">**packet_pptr** 메시지에 할당된 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1351">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="8a501-1352">**status_code** 리소스 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1352">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="8a501-1353">예제:</span><span class="sxs-lookup"><span data-stu-id="8a501-1353">Examples:</span></span>
  - <span data-ttu-id="8a501-1354">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="8a501-1354">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="8a501-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="8a501-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="8a501-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="8a501-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="8a501-1357">**status_code_length** 상태 코드의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-1357">**status_code_length** String length of status code</span></span>
- <span data-ttu-id="8a501-1358">**content_length** 콘텐츠 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="8a501-1358">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="8a501-1359">**content_type** HTTP 형식(예: "텍스트/일반")</span><span class="sxs-lookup"><span data-stu-id="8a501-1359">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="8a501-1360">**content_type_length** 콘텐츠 형식의 문자열 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-1360">**content_type_length** String length of content type</span></span>
- <span data-ttu-id="8a501-1361">**additional_header** 추가 헤더 텍스트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1361">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="8a501-1362">**additional_header_length** 추가 헤더 텍스트의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1362">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1363">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1363">Return Values</span></span>

- <span data-ttu-id="8a501-1364">**NX_SUCCESS** (0x00) HTML 헤더를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="8a501-1364">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="8a501-1365">**NX_PTR_ERROR** (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1365">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1366">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1366">Allowed From</span></span>

<span data-ttu-id="8a501-1367">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1368">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1368">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a><span data-ttu-id="8a501-1369">nx_web_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="8a501-1369">nx_web_http_server_callback_packet_send</span></span>

<span data-ttu-id="8a501-1370">콜백 함수의 HTTP 패킷 보내기</span><span class="sxs-lookup"><span data-stu-id="8a501-1370">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1371">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1371">Prototype</span></span>

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="8a501-1372">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1372">Description</span></span>

<span data-ttu-id="8a501-1373">이 서비스는 HTTP 콜백의 전체 HTTP 서버 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1373">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="8a501-1374">HTTP 서버는 NX_WEB_HTTP_SERVER _TIMEOUT_SEND를 사용하여 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1374">HTTP server will send the packet with the NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="8a501-1375">HTTP 헤더와 데이터는 패킷에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1375">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="8a501-1376">반환 상태에서 오류가 표시되는 경우 HTTP 애플리케이션에서 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1376">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="8a501-1377">콜백에서 NX_WEB_HTTP_CALLBACK_COMPLETED를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1377">The callback should return NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="8a501-1378">자세한 예제는 *nx_web_http_server_callback_generate_response_header()* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-1378">See *nx_web_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1379">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1379">Input Parameters</span></span>

- <span data-ttu-id="8a501-1380">**server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1380">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="8a501-1381">**packet_ptr** 보내는 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1381">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1382">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1382">Return Values</span></span>

- <span data-ttu-id="8a501-1383">**NX_SUCCESS** (0x00) HTTP 서버 패킷을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-1383">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="8a501-1384">**NX_PTR_ERROR** (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1384">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1385">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1385">Allowed From</span></span>

<span data-ttu-id="8a501-1386">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1386">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1387">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1387">Example</span></span>

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a><span data-ttu-id="8a501-1388">nx_web_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="8a501-1388">nx_web_http_server_callback_response_send</span></span>

<span data-ttu-id="8a501-1389">콜백 함수의 응답 보내기</span><span class="sxs-lookup"><span data-stu-id="8a501-1389">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1390">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1390">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="8a501-1391">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1391">Description</span></span>

<span data-ttu-id="8a501-1392">이 서비스는 애플리케이션의 콜백 루틴에서 제공된 응답 정보를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1392">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="8a501-1393">일반적으로 GET/POST 요청과 연결된 사용자 지정 응답을 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1393">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="8a501-1394">이 함수를 사용하는 경우 콜백 루틴에서 NX_WEB_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1394">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="8a501-1395">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1395">This service is deprecated.</span></span> <span data-ttu-id="8a501-1396">개발자는 *nx_web_http_server_callback_response_send_extended()* 를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1396">Developers are encouraged to use *nx_web_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1397">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1397">Input Parameters</span></span>

- <span data-ttu-id="8a501-1398">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1398">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8a501-1399">**header** 응답 헤더 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1399">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="8a501-1400">**information** 정보 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1400">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="8a501-1401">**additional_info** 추가 정보 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1401">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1402">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1402">Return Values</span></span>

- <span data-ttu-id="8a501-1403">**NX_SUCCESS** (0x00) HTTP 서버 응답을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-1403">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1404">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1404">Allowed From</span></span>

<span data-ttu-id="8a501-1405">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1405">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1406">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1406">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a><span data-ttu-id="8a501-1407">nx_web_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-1407">nx_web_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="8a501-1408">콜백 함수의 응답 보내기</span><span class="sxs-lookup"><span data-stu-id="8a501-1408">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1409">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1409">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="8a501-1410">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1410">Description</span></span>

<span data-ttu-id="8a501-1411">이 서비스는 애플리케이션의 콜백 루틴에서 제공된 응답 정보를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1411">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="8a501-1412">일반적으로 GET/POST 요청과 연결된 사용자 지정 응답을 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1412">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="8a501-1413">이 함수를 사용하는 경우 콜백 루틴에서 NX_WEB_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1413">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="8a501-1414">헤더, 정보 및 추가 정보의 문자열은 NULL로 종결되어야 하고 각 문자열의 길이가 인수 목록에 지정된 길이와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1414">The strings of header, information and additional_info must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="8a501-1415">이 서비스는 *nx_web_http_server_callback_response_send()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1415">This service replaces *nx_web_http_server_callback_response_send*().</span></span> <span data-ttu-id="8a501-1416">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1416">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1417">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1417">Input Parameters</span></span>

- <span data-ttu-id="8a501-1418">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8a501-1419">**header** 응답 헤더 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1419">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="8a501-1420">**header_length** 응답 헤더 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1420">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="8a501-1421">**information** 정보 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1421">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="8a501-1422">**information_length** 정보 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-1422">**Information_length** Length of the information string.</span></span>
- <span data-ttu-id="8a501-1423">**additional_info** 추가 정보 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1423">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="8a501-1424">**additional_info_length** 추가 정보 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1424">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1425">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1425">Return Values</span></span>

- <span data-ttu-id="8a501-1426">**NX_SUCCESS** (0x00) HTTP 서버 응답을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="8a501-1426">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1427">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1427">Allowed From</span></span>

<span data-ttu-id="8a501-1428">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1428">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1429">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1429">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a><span data-ttu-id="8a501-1430">nx_web_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="8a501-1430">nx_web_http_server_content_get</span></span>

<span data-ttu-id="8a501-1431">요청에서 콘텐츠 가져오기</span><span class="sxs-lookup"><span data-stu-id="8a501-1431">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1432">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1432">Prototype</span></span>

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="8a501-1433">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1433">Description</span></span>

<span data-ttu-id="8a501-1434">이 서비스는 POST 또는 PUT HTTP 클라이언트 요청에서 지정된 양의 콘텐츠를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1434">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="8a501-1435">HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_web_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1435">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1436">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1436">Input Parameters</span></span>

- <span data-ttu-id="8a501-1437">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1437">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8a501-1438">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1438">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="8a501-1439">이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1439">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="8a501-1440">**byte_offset** 콘텐츠 영역으로 오프셋할 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1440">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="8a501-1441">**destination_ptr** 콘텐츠의 대상 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1441">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="8a501-1442">**destination_size** 대상 영역에서 사용 가능한 최대 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1442">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="8a501-1443">**actual_size** 복사된 콘텐츠의 실제 크기로 설정되는 대상 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1443">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1444">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1444">Return Values</span></span>

- <span data-ttu-id="8a501-1445">**NX_SUCCESS** (0x00) HTTP 서버 콘텐츠를 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1445">**NX_SUCCESS** (0x00) Successful HTTP Server content Get</span></span>
- <span data-ttu-id="8a501-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP 서버 내부 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="8a501-1447">**NX_WEB_HTTP_DATA_END** (0x30007) 요청 콘텐츠의 끝입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1447">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="8a501-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) 콘텐츠의 다음 패킷을 가져오는 중에 HTTP 서버 시간이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="8a501-1449">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1449">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1450">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-1450">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1451">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1451">Allowed From</span></span>

<span data-ttu-id="8a501-1452">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1452">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1453">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1453">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a><span data-ttu-id="8a501-1454">nx_web_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-1454">nx_web_http_server_content_get_extended</span></span>

<span data-ttu-id="8a501-1455">요청에서 콘텐츠 가져오기/길이가 0인 콘텐츠 길이 지원</span><span class="sxs-lookup"><span data-stu-id="8a501-1455">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1456">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1456">Prototype</span></span>

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="8a501-1457">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1457">Description</span></span>

<span data-ttu-id="8a501-1458">이 서비스는 *nx_web_http_server_content_get()* 과 거의 동일하며, POST 또는 PUT HTTP 클라이언트 요청에서 지정된 양의 콘텐츠를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1458">This service is almost identical to *nx_web_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="8a501-1459">그러나 콘텐츠 길이가 0인 요청('빈 요청')을 유효한 요청으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1459">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="8a501-1460">HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_web_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1460">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

<span data-ttu-id="8a501-1461">이 서비스는 *nx_web_http_server_content_get()* 을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1461">This service replaces *nx_web_http_server_content_get*().</span></span> <span data-ttu-id="8a501-1462">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1462">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1463">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1463">Input Parameters</span></span>

- <span data-ttu-id="8a501-1464">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1464">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8a501-1465">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1465">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="8a501-1466">이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1466">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="8a501-1467">**byte_offset** 콘텐츠 영역으로 오프셋할 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1467">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="8a501-1468">**destination_ptr** 콘텐츠의 대상 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1468">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="8a501-1469">**destination_size** 대상 영역에서 사용 가능한 최대 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1469">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="8a501-1470">**actual_size** 복사된 콘텐츠의 실제 크기로 설정되는 대상 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1470">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1471">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1471">Return Values</span></span>

- <span data-ttu-id="8a501-1472">**NX_SUCCESS** (0x00) HTTP 콘텐츠를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="8a501-1472">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="8a501-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP 서버 내부 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="8a501-1474">**NX_WEB_HTTP_DATA_END** (0x30007) 요청 콘텐츠의 끝입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1474">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="8a501-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) 다음 패킷을 가져오는 중에 HTTP 서버 시간이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="8a501-1476">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1477">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-1477">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1478">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1478">Allowed From</span></span>

<span data-ttu-id="8a501-1479">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1480">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1480">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a><span data-ttu-id="8a501-1481">nx_web_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="8a501-1481">nx_web_http_server_content_length_get</span></span>

<span data-ttu-id="8a501-1482">요청에서 콘텐츠 길이 가져오기/콘텐츠 길이 0 지원</span><span class="sxs-lookup"><span data-stu-id="8a501-1482">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1483">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1483">Prototype</span></span>

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="8a501-1484">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1484">Description</span></span>

<span data-ttu-id="8a501-1485">이 서비스는 제공된 패킷에서 HTTP 콘텐츠 길이를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1485">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="8a501-1486">반환 값은 성공적인 완료 상태를 나타내며, 실제 길이 값은 content_length 입력 포인터에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1486">The return value indicates successful completion status and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="8a501-1487">HTTP 콘텐츠가 없거나 콘텐츠 길이가 0인 경우에도 이 루틴에서 여전히 성공적인 완료 상태를 반환하며 content_length 입력 포인터가 유효한 길이(0)를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1487">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="8a501-1488">HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_web_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1488">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1489">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1489">Input Parameters</span></span>

- <span data-ttu-id="8a501-1490">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1490">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="8a501-1491">이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1491">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="8a501-1492">**content_length** 콘텐츠 길이 필드에서 검색된 값에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1492">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1493">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1493">Return Values</span></span>

- <span data-ttu-id="8a501-1494">**NX_SUCCESS** (0x00) HTTP 서버 콘텐츠 길이를 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1494">**NX_SUCCESS** (0x00) Successful HTTP Server Content Length Get</span></span>
- <span data-ttu-id="8a501-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) HTTP 헤더 형식이 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Improper HTTP header format</span></span>
- <span data-ttu-id="8a501-1496">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1496">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1497">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1497">Allowed From</span></span>

<span data-ttu-id="8a501-1498">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1498">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1499">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1499">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a><span data-ttu-id="8a501-1500">nx_web_http_server_create</span><span class="sxs-lookup"><span data-stu-id="8a501-1500">nx_web_http_server_create</span></span>

<span data-ttu-id="8a501-1501">HTTP 서버 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="8a501-1501">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1502">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1502">Prototype</span></span>

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="8a501-1503">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1503">Description</span></span>

<span data-ttu-id="8a501-1504">이 서비스는 자체 ThreadX 스레드의 컨텍스트에서 실행되는 HTTP 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1504">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="8a501-1505">선택적 *authentication_check* 및 *request_notify* 애플리케이션 콜백 루틴은 HTTP 서버의 기본 작업에 대한 애플리케이션 소프트웨어 제어를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1505">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="8a501-1506">이 서비스는 일반 텍스트 HTTP 서버와 TLS 보안 HTTPS 서버를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1506">This service is used to create both plaintext HTTP servers and TLS-secured HTTPS servers.</span></span> <span data-ttu-id="8a501-1507">TLS를 통해 HTTPS를 사용하도록 설정하려면 *nx_web_http_server_secure_configure()* 서비스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-1507">To enable HTTPS using TLS, see the service *nx_web_http_server_secure_configure()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1508">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1508">Input Parameters</span></span>

- <span data-ttu-id="8a501-1509">**http_server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1509">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8a501-1510">**http_server_name** HTTP 서버 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1510">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="8a501-1511">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1511">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8a501-1512">**server_port** 서버 인스턴스의 TCP 수신 대기 포트</span><span class="sxs-lookup"><span data-stu-id="8a501-1512">**server_port** TCP listening port for server instance.</span></span>
- <span data-ttu-id="8a501-1513">**media_ptr** 이전에 만든 FileX 미디어 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1513">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="8a501-1514">**stack_ptr** HTTP 서버 스레드 스택 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1514">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="8a501-1515">**stack_size** HTTP 서버 스레드 스택 크기에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1515">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="8a501-1516">**authentication_check** 애플리케이션의 인증 확인 루틴에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1516">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="8a501-1517">지정된 경우 이 루틴은 각 HTTP 클라이언트 요청에 대해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1517">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="8a501-1518">이 매개 변수가 NULL이면 인증이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1518">If this parameter is NULL, no authentication will be performed.</span></span> <span data-ttu-id="8a501-1519">이 매개 변수는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1519">This parameter is deprecated.</span></span> <span data-ttu-id="8a501-1520">대신 *nx_web_http_server_authenticate_check_set*()를 호출하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-1520">Call *nx_web_http_server_authenticate_check_set*() instead.</span></span>
- <span data-ttu-id="8a501-1521">**request_notify** 애플리케이션의 요청 알림 루틴에 대한 함수 포인터.</span><span class="sxs-lookup"><span data-stu-id="8a501-1521">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="8a501-1522">지정된 경우 HTTP 서버에서 요청을 처리하기 전에 이 루틴이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1522">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="8a501-1523">이렇게 하면 HTTP 클라이언트 요청을 완료하기 전에 리소스 이름을 리디렉션하거나 리소스 내의 필드를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1523">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1524">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1524">Return Values</span></span>

- <span data-ttu-id="8a501-1525">**NX_SUCCESS** (0x00) HTTP 서버를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="8a501-1525">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="8a501-1526">NX_PTR_ERROR (0x07) 잘못된 HTTP 서버, IP, 미디어, 스택 또는 패킷 풀 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1526">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="8a501-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) 풀의 패킷 페이로드가 전체 HTTP 요청을 포함할 만큼 충분히 크지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1528">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1528">Allowed From</span></span>

<span data-ttu-id="8a501-1529">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1529">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1530">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1530">Example</span></span>

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a><span data-ttu-id="8a501-1531">nx_web_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="8a501-1531">nx_web_http_server_delete</span></span>

<span data-ttu-id="8a501-1532">HTTP 서버 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="8a501-1532">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1533">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1533">Prototype</span></span>

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="8a501-1534">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1534">Description</span></span>

<span data-ttu-id="8a501-1535">이 서비스는 이전에 만든 HTTP 서버 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1535">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1536">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1536">Input Parameters</span></span>

- <span data-ttu-id="8a501-1537">**http_server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1537">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1538">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1538">Return Values</span></span>

- <span data-ttu-id="8a501-1539">**NX_SUCCESS** (0x00) HTTP 서버를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="8a501-1539">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="8a501-1540">NX_PTR_ERROR (0x07) 잘못된 HTTP 서버 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1540">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="8a501-1541">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-1541">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1542">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1542">Allowed From</span></span>

<span data-ttu-id="8a501-1543">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1543">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1544">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1544">Example</span></span>

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a><span data-ttu-id="8a501-1545">nx_web_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="8a501-1545">nx_web_http_server_get_entity_content</span></span>

<span data-ttu-id="8a501-1546">엔터티 데이터의 위치 및 길이 검색</span><span class="sxs-lookup"><span data-stu-id="8a501-1546">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1547">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1547">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="8a501-1548">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1548">Description</span></span>

<span data-ttu-id="8a501-1549">이 서비스는 받은 클라이언트 메시지의 현재 다중 파트 엔터티 내의 데이터 시작 위치 및 경계 문자열이 포함되지 않는 데이터 길이를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1549">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="8a501-1550">내부적으로 HTTP 서버는 여러 엔터티가 있는 메시지에 대해 동일한 클라이언트 데이터그램에서 이 함수를 다시 호출할 수 있도록 자체 오프셋을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1550">Internally, the HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="8a501-1551">패킷 포인터를 클라이언트 메시지가 다중 패킷 데이터그램인 다음 패킷으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1551">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="8a501-1552">이 서비스를 사용하려면 NX_WEB_HTTP_MULTIPART_ENABLE을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1552">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="8a501-1553">또한 packet_pptr을 사용하여 가리킨 패킷을 애플리케이션에서 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1553">Also note that the application should not release the packet pointed to by packet_pptr.</span></span> <span data-ttu-id="8a501-1554">이 작업은 HTTP 서버에서 내부적으로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1554">This is done internally by the HTTP server.</span></span>

<span data-ttu-id="8a501-1555">자세한 내용은 *nx_web_http_server_get_entity_header()* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-1555">See *nx_web_http_server_get_entity_header()* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1556">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1556">Input Parameters</span></span>

- <span data-ttu-id="8a501-1557">**server_ptr** HTTP 서버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1557">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="8a501-1558">**packet_pptr** 패킷 포인터의 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1558">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="8a501-1559">애플리케이션에서 이 패킷을 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1559">Note that the application should not release this packet</span></span>
- <span data-ttu-id="8a501-1560">**available_offset** 패킷 선행 포인터에서 엔터티 데이터의 오프셋에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1560">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="8a501-1561">**available_length** 엔터티 데이터의 길이에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1561">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1562">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1562">Return Values</span></span>

- <span data-ttu-id="8a501-1563">**NX_SUCCESS** (0x00) 엔터티 콘텐츠의 크기와 위치를 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="8a501-1563">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="8a501-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) HTTP 서버 내부 다중 파트 표식에 대한 콘텐츠가 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="8a501-1565">NX_WEB_HTTP_ERROR(0x30000) HTTP 서버 내부 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1565">NX_WEB_HTTP_ERROR (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="8a501-1566">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1566">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1567">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1567">Allowed From</span></span>

<span data-ttu-id="8a501-1568">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1568">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1569">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1569">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a><span data-ttu-id="8a501-1570">nx_web_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="8a501-1570">nx_web_http_server_get_entity_header</span></span>

<span data-ttu-id="8a501-1571">엔터티 헤더의 콘텐츠 검색</span><span class="sxs-lookup"><span data-stu-id="8a501-1571">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1572">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1572">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="8a501-1573">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1573">Description</span></span>

<span data-ttu-id="8a501-1574">이 서비스는 지정된 버퍼에서 엔터티 헤더를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1574">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="8a501-1575">다중 엔터티 헤더가 있는 클라이언트 데이터그램에서 다음 다중 파트 엔터티를 찾도록 HTTP 서버에서 내부적으로 자체 포인터를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1575">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="8a501-1576">패킷 포인터를 클라이언트 메시지가 다중 패킷 데이터그램인 다음 패킷으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1576">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="8a501-1577">이 서비스를 사용하려면 NX_WEB_HTTP_MULTIPART_ENABLE을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1577">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="8a501-1578">또한 packet_pptr을 사용하여 가리킨 패킷을 애플리케이션에서 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1578">Note also that the application should not release the packet pointed to by packet_pptr.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1579">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1579">Input Parameters</span></span>

- <span data-ttu-id="8a501-1580">**server_ptr** HTTP 서버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1580">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="8a501-1581">**packet_pptr** 패킷 포인터의 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1581">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="8a501-1582">애플리케이션에서 이 패킷을 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1582">Note that the application should not release this packet</span></span>
- <span data-ttu-id="8a501-1583">**entity_header_buffer** 엔터티 헤더를 저장하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1583">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="8a501-1584">**buffer_size** 입력 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1584">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1585">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1585">Return Values</span></span>

- <span data-ttu-id="8a501-1586">**NX_SUCCESS** (0x00) 엔터티 헤더를 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1586">**NX_SUCCESS** (0x00) Successfully retrieved entity Header</span></span>
- <span data-ttu-id="8a501-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) 엔터티 헤더 필드가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Entity header field not found</span></span>
- <span data-ttu-id="8a501-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) 다중 패킷 클라이언트 메시지에 대한 다음 패킷을 받는 시간이 만료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired to receive next packet for multipacket client message</span></span>
- <span data-ttu-id="8a501-1589">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1589">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1590">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-1590">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8a501-1591">NX_WEB_HTTP_ERROR (0x30000) 내부 HTTP 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1591">NX_WEB_HTTP_ERROR (0x30000) Internal HTTP error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1592">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1592">Allowed From</span></span>

<span data-ttu-id="8a501-1593">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1593">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1594">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1594">Example</span></span>

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
                NX_SUCCESS)
            {
                nx_packet_release(response_pkt);
            }
        }
    }
    else
    {
        /* Indicate we have not processed the response to client yet.*/
        return(NX_SUCCESS);
    }

    /* Indicate the response to client is transmitted. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a><span data-ttu-id="8a501-1595">nx_web_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="8a501-1595">nx_web_http_server_gmt_callback_set</span></span>

<span data-ttu-id="8a501-1596">GMT 날짜 및 시간을 가져오는 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="8a501-1596">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1597">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1597">Prototype</span></span>

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="8a501-1598">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1598">Description</span></span>

<span data-ttu-id="8a501-1599">이 서비스는 이전에 만든 HTTP 서버에서 GMT 날짜 및 시간을 가져오는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1599">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="8a501-1600">이 서비스는 HTTP 서버가 클라이언트에 대한 HTTP 서버 응답에 헤더를 만들 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1600">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1601">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1601">Input Parameters</span></span>

- <span data-ttu-id="8a501-1602">**server_ptr** HTTP 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1602">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="8a501-1603">**gmt_get** GMT 콜백에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1603">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="8a501-1604">**date** 검색된 날짜에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1604">**date** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1605">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1605">Return Values</span></span>

- <span data-ttu-id="8a501-1606">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="8a501-1606">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="8a501-1607">NX_PTR_ERROR (0x07) 잘못된 패킷 또는 매개 변수 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1607">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1608">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1608">Allowed From</span></span>

<span data-ttu-id="8a501-1609">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1609">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1610">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1610">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="8a501-1611">nx_web_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="8a501-1611">nx_web_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="8a501-1612">잘못된 사용자/암호를 처리하는 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="8a501-1612">Set the callback to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1613">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1613">Prototype</span></span>

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="8a501-1614">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1614">Description</span></span>

<span data-ttu-id="8a501-1615">이 서비스는 다이제스트 또는 기본 인증을 통해 클라이언트 GET, PUT 또는 DELETE 요청에서 잘못된 사용자 이름 및 암호를 받을 때 호출되는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1615">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="8a501-1616">HTTP 서버는 이전에 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1616">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1617">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1617">Input Parameters</span></span>

- <span data-ttu-id="8a501-1618">**server_ptr** HTTP 서버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1618">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="8a501-1619">**invalid_username_password_callback** 잘못된 사용자/전달 콜백에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1619">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="8a501-1620">**resource** 클라이언트에서 지정한 리소스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1620">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="8a501-1621">**client_address** 클라이언트 주소</span><span class="sxs-lookup"><span data-stu-id="8a501-1621">**client_address** Client address</span></span>
- <span data-ttu-id="8a501-1622">**request_type** 클라이언트 요청 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1622">**request_type** Indicates client request type.</span></span> <span data-ttu-id="8a501-1623">다음과 같은 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1623">May be:</span></span>
  - <span data-ttu-id="8a501-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="8a501-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span></span>
  - <span data-ttu-id="8a501-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="8a501-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span></span>
  - <span data-ttu-id="8a501-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="8a501-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1627">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1627">Return Values</span></span>

- <span data-ttu-id="8a501-1628">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="8a501-1628">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="8a501-1629">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1629">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1630">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1630">Allowed From</span></span>

<span data-ttu-id="8a501-1631">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1631">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1632">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1632">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a><span data-ttu-id="8a501-1633">nx_web_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="8a501-1633">nx_web_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="8a501-1634">HTML에 대한 추가 MIME 맵 설정</span><span class="sxs-lookup"><span data-stu-id="8a501-1634">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1635">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1635">Prototype</span></span>

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="8a501-1636">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1636">Description</span></span>

<span data-ttu-id="8a501-1637">이 서비스를 통해 HTTP 애플리케이션 개발자는 NetX 웹 HTTP 서버에서 제공하는 기본 MIME 형식의 MIME 형식을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1637">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by the NetX Web HTTP Server.</span></span> <span data-ttu-id="8a501-1638">정의된 형식 목록은 *nx_web_http_server_get_type()* 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-1638">See *nx_web_http_server_get_type()* for list of defined types.</span></span>

<span data-ttu-id="8a501-1639">클라이언트 요청(예: GET 요청)을 받으면 HTTP 서버에서 우선적으로 추가 MIME 맵 세트를 사용하여 HTTP 헤더에서 요청된 파일 형식을 구문 분석하고, 일치하는 항목이 없는 경우 HTTP 서버의 기본 MIME 맵에서 일치 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1639">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="8a501-1640">일치하는 항목이 없으면 MIME 형식은 기본적으로 "텍스트/일반"으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1640">If no match is found, the MIME type defaults to "text/plain".</span></span>

<span data-ttu-id="8a501-1641">요청 알림 함수가 HTTP 서버에 등록된 경우 요청 알림 콜백에서 *nx_web_http_server_type_get_extended()* 를 호출하여 파일 형식을 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1641">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_web_http_server_type_get_extended()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1642">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1642">Input Parameters</span></span>

- <span data-ttu-id="8a501-1643">**server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1643">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="8a501-1644">**mime_maps** MIME 맵 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1644">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="8a501-1645">**mime_map_num** 배열의 MIME 맵 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1645">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1646">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1646">Return Values</span></span>

- <span data-ttu-id="8a501-1647">**NX_SUCCESS** (0x00) HTTP 서버 MIME 맵을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="8a501-1647">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="8a501-1648">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1648">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1649">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1649">Allowed From</span></span>

<span data-ttu-id="8a501-1650">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1650">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1651">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1651">Example</span></span>

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a><span data-ttu-id="8a501-1652">nx_web_http_server_response_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="8a501-1652">nx_web_http_server_response_packet_allocate</span></span>

<span data-ttu-id="8a501-1653">HTTP(S) 패킷 할당</span><span class="sxs-lookup"><span data-stu-id="8a501-1653">Allocate an HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1654">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1654">Prototype</span></span>

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8a501-1655">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1655">Description</span></span>

<span data-ttu-id="8a501-1656">이 서비스는 HTTP(S) 서버용 패킷을 할당하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1656">This service attempts to allocates a packet for the HTTP(S) server.</span></span>

<span data-ttu-id="8a501-1657">이 패킷을 입력으로 사용하는 후속 NetX 또는 HTTP 서버 API(예: nx_packet_data_append 또는 \*\*nx_web_http_server_callback_packet_send)가 **실패** 하는 경우 애플리케이션에서 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1657">Note that if a subsequent NetX or HTTP Server API using this packet as input **fails**, such as nx_packet_data_append or \*\*nx_web_http_server_callback_packet_send, the application is responsible for releasing the packet.</span></span> **

### <a name="input-parameters"></a><span data-ttu-id="8a501-1658">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1658">Input Parameters</span></span>

- <span data-ttu-id="8a501-1659">**server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1659">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8a501-1660">**packet_ptr** 할당된 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1660">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="8a501-1661">**wait_option** 패킷 풀에 사용 가능한 패킷이 없는 경우 대기 시간을 틱 단위로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1661">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="8a501-1662">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8a501-1663">**NX_NO_WAIT** (0x00000000) NX_NO_WAIT를 선택하면 요청을 수행할 수 없는 경우 호출 스레드가 즉시 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1663">**NX_NO_WAIT** (0x00000000) Selecting NX_NO_WAIT causes the calling thread to return immediately if the request cannot be fulfilled.</span></span>
  - <span data-ttu-id="8a501-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) NX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>
  - <span data-ttu-id="8a501-1665">**timeout value** (0x00000001 ~ 0xFFFFFFFE) 숫자 값(0x1 ~ 0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1665">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1666">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1666">Return Values</span></span>

- <span data-ttu-id="8a501-1667">**NX_SUCCESS** (0x00) 패킷을 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1667">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="8a501-1668">**NX_NO_PACKET** (0x01) 사용 가능한 패킷이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1668">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="8a501-1669">**NX_WAIT_ABORTED** (0x1A) 요청된 일시 중단이 *tx_thread_wait_abort* 호출 때문에 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1669">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="8a501-1670">**NX_INVALID_PARAMETERS** (0x4D) 프로토콜을 지원하지 않는 패킷 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1670">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="8a501-1671">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1671">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1672">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1672">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1673">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1673">Allowed From</span></span>

<span data-ttu-id="8a501-1674">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1675">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1675">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a><span data-ttu-id="8a501-1676">nx_web_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="8a501-1676">nx_web_http_server_packet_content_find</span></span>

<span data-ttu-id="8a501-1677">콘텐츠 길이를 추출하고 데이터 시작에 대한 포인터 설정</span><span class="sxs-lookup"><span data-stu-id="8a501-1677">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1678">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1678">Prototype</span></span>

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="8a501-1679">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1679">Description</span></span>

<span data-ttu-id="8a501-1680">이 서비스는 HTTP 헤더에서 콘텐츠 길이를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1680">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="8a501-1681">또한 제공된 패킷을 다음과 같이 업데이트합니다. 패킷 선행 포인터(쓸 패킷 버퍼의 시작 위치)가 HTTP 헤더를 방금 전달한 HTTP 콘텐츠(데이터)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1681">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="8a501-1682">현재 패킷에서 콘텐츠의 시작 위치를 찾을 수 없는 경우 함수에서 NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE 대기 옵션을 사용하여 다음 패킷을 받을 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1682">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="8a501-1683">이 서비스는 엔터티 헤더 앞의 패킷 선행 포인터를 수정하므로 *nx_web_http_server_get_entity_header()* 를 호출하기 전에 호출하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1683">Note this should not be called before calling *nx_web_http_server_get_entity_header()* because it modifies the packet prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1684">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1684">Input Parameters</span></span>

- <span data-ttu-id="8a501-1685">**server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1685">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="8a501-1686">**packet_ptr** 업데이트된 선행 포인터를 사용하여 패킷을 반환하는 패킷 포인터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1686">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="8a501-1687">**content_length** 추출된 content_length에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1687">**content_length** Pointer to extracted content_length</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1688">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1688">Return Values</span></span>

- <span data-ttu-id="8a501-1689">**NX_SUCCESS** (0x00) HTTP 콘텐츠 길이가 있고 패킷을 성공적으로 업데이트함</span><span class="sxs-lookup"><span data-stu-id="8a501-1689">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="8a501-1690">**NX_WEB_HTTP_TIMEOUT**(0x30001) 다음 패킷을 기다리는 시간이 만료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="8a501-1691">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1691">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1692">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1692">Allowed From</span></span>

<span data-ttu-id="8a501-1693">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1693">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1694">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1694">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a><span data-ttu-id="8a501-1695">nx_web_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="8a501-1695">nx_web_http_server_packet_get</span></span>

<span data-ttu-id="8a501-1696">다음 HTTP 패킷 받기</span><span class="sxs-lookup"><span data-stu-id="8a501-1696">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1697">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1697">Prototype</span></span>

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="8a501-1698">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1698">Description</span></span>

<span data-ttu-id="8a501-1699">이 서비스는 HTTP 서버 소켓에서 받은 다음 패킷을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1699">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="8a501-1700">패킷 수신 대기 옵션은 NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1700">The wait option to receive a packet is NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="8a501-1701">성공하면 애플리케이션에서 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1701">Note that if successful the application is responsible for releasing the packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1702">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1702">Input Parameters</span></span>

- <span data-ttu-id="8a501-1703">**server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1703">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="8a501-1704">**packet_ptr** 받은 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1704">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1705">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1705">Return Values</span></span>

- <span data-ttu-id="8a501-1706">**NX_SUCCESS** (0x00) 다음 HTTP 패킷을 성공적으로 받음</span><span class="sxs-lookup"><span data-stu-id="8a501-1706">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="8a501-1707">**NX_WEB_HTTP_TIMEOUT**(0x30001) 다음 패킷을 기다리는 시간이 만료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="8a501-1708">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1708">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1709">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1709">Allowed From</span></span>

<span data-ttu-id="8a501-1710">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1710">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1711">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1711">Example</span></span>

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a><span data-ttu-id="8a501-1712">nx_web_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="8a501-1712">nx_web_http_server_param_get</span></span>

<span data-ttu-id="8a501-1713">요청에서 매개 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="8a501-1713">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1714">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1714">Prototype</span></span>

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="8a501-1715">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1715">Description</span></span>

<span data-ttu-id="8a501-1716">이 서비스는 제공된 요청 패킷에서 지정된 HTTP URL 매개 변수를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1716">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="8a501-1717">요청된 HTTP 매개 변수가 없는 경우 이 루틴에서 NX_WEB_HTTP_NOT_FOUND 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1717">If the requested HTTP parameter is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="8a501-1718">이 루틴은 HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_web_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1718">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1719">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1719">Input Parameters</span></span>

- <span data-ttu-id="8a501-1720">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1720">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="8a501-1721">애플리케이션에서 이 패킷을 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1721">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="8a501-1722">**param_number** 매개 변수 목록에서 왼쪽에서 오른쪽으로 0에서 시작하는 매개 변수의 논리적 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1722">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="8a501-1723">**param_ptr** 매개 변수를 복사하는 대상 영역</span><span class="sxs-lookup"><span data-stu-id="8a501-1723">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="8a501-1724">**param_size** 총 매개 변수 데이터 길이(바이트)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1724">**param_size** Return the total parameter data length (in bytes).</span></span>
- <span data-ttu-id="8a501-1725">**max_param_size** 매개 변수 대상 영역의 최대 크기</span><span class="sxs-lookup"><span data-stu-id="8a501-1725">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1726">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1726">Return Values</span></span>

- <span data-ttu-id="8a501-1727">**NX_SUCCESS** (0x00) HTTP 서버 매개 변수를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="8a501-1727">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="8a501-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) 지정된 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified parameter not found</span></span>
- <span data-ttu-id="8a501-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) 요청 매개 변수가 제대로 종료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Request parameter not properly terminated</span></span>
- <span data-ttu-id="8a501-1730">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1730">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1731">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-1731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1732">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1732">Allowed From</span></span>

<span data-ttu-id="8a501-1733">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1734">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1734">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a><span data-ttu-id="8a501-1735">nx_web_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="8a501-1735">nx_web_http_server_query_get</span></span>

<span data-ttu-id="8a501-1736">요청에서 쿼리 가져오기</span><span class="sxs-lookup"><span data-stu-id="8a501-1736">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1737">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1737">Prototype</span></span>

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="8a501-1738">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1738">Description</span></span>

<span data-ttu-id="8a501-1739">이 서비스는 제공된 요청 패킷에서 지정된 HTTP URL 쿼리를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1739">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="8a501-1740">요청된 HTTP 쿼리가 없는 경우 이 루틴에서 NX_WEB_HTTP_NOT_FOUND 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1740">If the requested HTTP query is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="8a501-1741">이 루틴은 HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_web_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1741">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1742">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1742">Input Parameters</span></span>

- <span data-ttu-id="8a501-1743">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1743">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="8a501-1744">애플리케이션에서 이 패킷을 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1744">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="8a501-1745">**query_number** 쿼리 목록에서 왼쪽에서 오른쪽으로 0에서 시작하는 매개 변수의 논리적 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1745">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="8a501-1746">**query_ptr** 쿼리를 복사하는 대상 영역</span><span class="sxs-lookup"><span data-stu-id="8a501-1746">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="8a501-1747">**query_size** 쿼리 데이터 크기(바이트)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1747">**query_size** Return query data size (in bytes).</span></span>
- <span data-ttu-id="8a501-1748">**max_query_size** 쿼리 대상 영역의 최대</span><span class="sxs-lookup"><span data-stu-id="8a501-1748">**max_query_size** Maximum size of the query destination</span></span>

<span data-ttu-id="8a501-1749">크기</span><span class="sxs-lookup"><span data-stu-id="8a501-1749">area.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1750">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1750">Return Values</span></span>

- <span data-ttu-id="8a501-1751">**NX_SUCCESS** (0x00) HTTP 서버 쿼리를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="8a501-1751">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="8a501-1752">**NX_WEB_HTTP_FAILED** (0x30002) 쿼리 크기가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1752">**NX_WEB_HTTP_FAILED** (0x30002) Query size too small.</span></span>
- <span data-ttu-id="8a501-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) 지정된 쿼리가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified query not found</span></span>
- <span data-ttu-id="8a501-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) 클라이언트 요청에 쿼리가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) No query in Client request</span></span>
- <span data-ttu-id="8a501-1755">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1755">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1756">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-1756">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1757">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1757">Allowed From</span></span>

<span data-ttu-id="8a501-1758">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1758">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1759">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1759">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a><span data-ttu-id="8a501-1760">nx_web_http_server_response_chunked_set</span><span class="sxs-lookup"><span data-stu-id="8a501-1760">nx_web_http_server_response_chunked_set</span></span>

<span data-ttu-id="8a501-1761">HTTP(S) 응답에 대한 청크 분할 전송 설정</span><span class="sxs-lookup"><span data-stu-id="8a501-1761">Set chunked transfer for HTTP(S) response</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1762">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1762">Prototype</span></span>

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="8a501-1763">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1763">Description</span></span>

<span data-ttu-id="8a501-1764">이 서비스는 *nx_web_http_server_response_packet_allocate*()를 사용하여 만든 사용자 지정 HTTP(S) 응답 데이터 패킷을 클라이언트에 보내기 위해 청크 분할 전송 코딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1764">This service uses chunked transfer coding to send a custom HTTP(S) response data packet created with *nx_web_http_server_response_packet_allocate*() to the client.</span></span>

> [!NOTE]
> <span data-ttu-id="8a501-1765">애플리케이션에서 청크 분할 전송 코딩을 사용하여 응답 데이터 패킷을 보내는 경우 애플리케이션에서 *nx_web_http_server_response_packet_allocate*()를 호출한 후, 그리고 *nx_web_http_server_callback_packet_send*()를 호출하기 전에 이 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1765">If the application uses chunked transfer coding to send a response data packet, it must call this service after calling *nx_web_http_server_response_packet_allocate*(), and before calling *nx_web_http_server_callback_packet_send*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1766">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1766">Input Parameters</span></span>

- <span data-ttu-id="8a501-1767">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1767">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8a501-1768">**chunk_size** 청크 데이터의 크기(8진수)</span><span class="sxs-lookup"><span data-stu-id="8a501-1768">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="8a501-1769">**packet_ptr** HTTP(S) 요청 데이터 패킷 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1769">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1770">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1770">Return Values</span></span>

- <span data-ttu-id="8a501-1771">**NX_SUCCESS** (0x00) 청크 분할을 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1771">**NX_SUCCESS** (0x00) Successful set chunked.</span></span>
- <span data-ttu-id="8a501-1772">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1772">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1773">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1773">Allowed From</span></span>

<span data-ttu-id="8a501-1774">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1774">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1775">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1775">Example</span></span>

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a><span data-ttu-id="8a501-1776">nx_web_http_server_secure_configure</span><span class="sxs-lookup"><span data-stu-id="8a501-1776">nx_web_http_server_secure_configure</span></span>

<span data-ttu-id="8a501-1777">보안 HTTPS에 TLS를 사용하도록 HTTP 서버 구성</span><span class="sxs-lookup"><span data-stu-id="8a501-1777">Configure an HTTP Server to use TLS for secure HTTPS</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1778">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1778">Prototype</span></span>

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a><span data-ttu-id="8a501-1779">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1779">Description</span></span>

<span data-ttu-id="8a501-1780">이 서비스는 보안 HTTPS 통신에 TLS를 사용하도록 이전에 만든 NetX 웹 HTTP 서버 인스턴스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1780">This service configures a previously created NetX Web HTTP server instance to use TLS for secure HTTPS communications.</span></span> <span data-ttu-id="8a501-1781">들어오는 각 HTTPS 클라이언트에서 일관적인 동작을 경험할 수 있도록, 매개 변수는 상태가 같은 모든 TLS 세션을 구성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1781">The parameters are used to configure all the possible TLS sessions with identical state so that each incoming HTTPS Client experiences consistent behavior.</span></span> <span data-ttu-id="8a501-1782">TLS 세션 수는 NX_WEB_HTTP_SESSION_MAX 매크로를 사용하여 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1782">The number of TLS sessions is controlled using the macro NX_WEB_HTTP_SESSION_MAX.</span></span>

<span data-ttu-id="8a501-1783">암호화 루틴 테이블(ciphersuite 테이블)은 함수 포인터만 포함하므로 모든 TLS 세션 간에 공유됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1783">The cryptographic routine table (ciphersuite table) is shared between all TLS sessions as it just contains function pointers.</span></span>

<span data-ttu-id="8a501-1784">메타데이터 및 패킷 리어셈블리 버퍼는 모든 TLS 세션 간에 균등하게 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1784">The metadata and packet reassembly buffers are each divided equally between all TLS sessions.</span></span> <span data-ttu-id="8a501-1785">버퍼 크기를 세션 수로 균등하게 나눌 수 없는 경우 나머지 버퍼는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1785">If the buffer size is not evenly divisible by the number of sessions the remainder will be unused.</span></span>

<span data-ttu-id="8a501-1786">전달된 ID 인증서는 모든 세션에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1786">The passed-in identity certificate is used by all sessions.</span></span> <span data-ttu-id="8a501-1787">TLS 작업 중에는 서버 ID 인증서를 읽기만 하므로 각 세션에 복사본이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1787">During TLS operation the server identity certificate is only read from so copies are not needed for each session.</span></span>

<span data-ttu-id="8a501-1788">신뢰할 수 있는 인증서는 HTTPS 서버의 각 TLS 세션에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1788">The trusted certificates are added to each TLS session in the HTTPS Server.</span></span> <span data-ttu-id="8a501-1789">이러한 인증서는 원격 인증서 공간이 제공될 때 자동으로 사용하도록 설정되는 클라이언트 인증서 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1789">These are used for Client certificate authentication which is automatically enabled when remote certificate space is provided.</span></span>

<span data-ttu-id="8a501-1790">원격 인증서 배열 및 버퍼는 기본적으로 모든 TLS 세션 간에 공유됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1790">The remote certificate array and buffer is shared by default between all TLS sessions.</span></span> <span data-ttu-id="8a501-1791">원격 인증서는 원격 인증서 수가 0이 아닌 경우에 자동으로 사용하도록 설정되는 클라이언트 인증서 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1791">The remote certificates are used for Client certificate authentication which is automatically enabled when the remote certificate count is nonzero.</span></span> <span data-ttu-id="8a501-1792">버퍼를 공유하기 때문에 인증서의 유효성을 검사하는 동안 일부 세션이 차단될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1792">Due to the buffer being shared some sessions may block during certificate validation.</span></span>

<span data-ttu-id="8a501-1793">클라이언트 인증서 인증을 사용하지 않도록 설정하려면 remote_certificates 매개 변수에 NX_NULL을 전달하고 remote_certs_num 매개 변수에 0 값을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1793">To disable client certificate authentication, pass NX_NULL for the remote_certificates parameter and a value of 0 for the remote_certs_num parameter.</span></span>

<span data-ttu-id="8a501-1794">반환 값에는 TLS 세션 구성의 문제로 인한 모든 TLS 오류 코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1794">Return values will include any TLS error codes resulting from issues in the configuration of the TLS sessions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1795">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1795">Input Parameters</span></span>

- <span data-ttu-id="8a501-1796">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1796">**http_server_ptr** Pointer to HTTP Server instance.</span></span>
- <span data-ttu-id="8a501-1797">**crypto_table** TLS ciphersuite 테이블에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1797">**crypto_table** Pointer to TLS ciphersuite table.</span></span>
- <span data-ttu-id="8a501-1798">**metadata_buffer** 암호화 메타데이터 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1798">**metadata_buffer** Pointer to cryptographic metadata buffer.</span></span>
- <span data-ttu-id="8a501-1799">**metadata_size** 암호화 메타데이터 버퍼의 크기</span><span class="sxs-lookup"><span data-stu-id="8a501-1799">**metadata_size** Size of cryptographic metadata buffer.</span></span>
- <span data-ttu-id="8a501-1800">**packet_buffer** TLS 패킷 리어셈블리 버퍼</span><span class="sxs-lookup"><span data-stu-id="8a501-1800">**packet_buffer** TLS packet reassembly buffer.</span></span>
- <span data-ttu-id="8a501-1801">**packet_buffer** TLS 패킷 버퍼의 크기 - (<원하는 TLS 버퍼 크기 \* NX_WEB_HTTP_SESSION_MAX)와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1801">**packet_buffer** Size of TLS packet buffer – should be equal to (<desired TLS buffer size\* NX_WEB_HTTP_SESSION_MAX).</span></span>
- <span data-ttu-id="8a501-1802">**identity_certificate** TLS 서버 ID 인증서 - 모든 HTTPS 서버 세션에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1802">**identity_certificate** TLS server identity certificate – will be used for all HTTPS server sessions.</span></span>
- <span data-ttu-id="8a501-1803">**trusted_certificates** *remote_certs_num* 매개 변수에 0이 아닌 값을 전달하여 클라이언트 인증서 인증을 사용하도록 설정한 경우 들어오는 클라이언트 인증서의 유효성을 검사하는 데 사용되는 NX_SECURE_X509_CERT 개체 배열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1803">**trusted_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used to validate incoming client certificates if client certificate authentication is enabled by passing a non-zero value for the *remote_certs_num* parameter.</span></span>
- <span data-ttu-id="8a501-1804">**trusted_certs_num** *trusted_certificates* 배열에 들어 있는 신뢰할 수 있는 인증서의 수</span><span class="sxs-lookup"><span data-stu-id="8a501-1804">**trusted_certs_num** Number of trusted certificates in the *trusted_certificates* array.</span></span>
- <span data-ttu-id="8a501-1805">**remote_certificates** 들어오는 클라이언트 인증서에 사용되는 NX_SECURE_X509_CERT 개체 배열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1805">**remote_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used for incoming client certificates.</span></span>
- <span data-ttu-id="8a501-1806">**remote_certs_num** 원격 인증서의 수.</span><span class="sxs-lookup"><span data-stu-id="8a501-1806">**remote_certs_num** Number of remote certificates.</span></span> <span data-ttu-id="8a501-1807">클라이언트에서 예상되는 최대 인증서 수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1807">Should be the maximum number of expected certificates from clients.</span></span> <span data-ttu-id="8a501-1808">이 값이 0이 아니면 자동으로 클라이언트 인증서 인증을 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1808">Client certificate authentication is enabled automatically when this is non-zero.</span></span>
- <span data-ttu-id="8a501-1809">**remote_certificate_buffer** 클라이언트 인증서 인증을 사용하는 경우 클라이언트에서 들어오는 원격 인증서를 포함하는 버퍼</span><span class="sxs-lookup"><span data-stu-id="8a501-1809">**remote_certificate_buffer** Buffer to contain incoming remote certificates from clients if client certificate authentication is enabled.</span></span> <span data-ttu-id="8a501-1810">remote_cert_buffer_size 원격 인증서 버퍼의 크기.</span><span class="sxs-lookup"><span data-stu-id="8a501-1810">remote_cert_buffer_size Size of remote certificates buffer.</span></span> <span data-ttu-id="8a501-1811">(<예상하는 최대 인증서 크기 \* remote_certs_num)과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1811">Should be equal to (<maximum expected certificate size \* remote_certs_num).</span></span>


### <a name="return-values"></a><span data-ttu-id="8a501-1812">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1812">Return Values</span></span>

- <span data-ttu-id="8a501-1813">**NX_SUCCESS**(0x00) TLS 세션을 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1813">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="8a501-1814">**NX_NOT_CONNECTED** (0x38) 기본 TCP 소켓이 더 이상 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1814">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="8a501-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) 받은 TLS 메시지 유형이 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="8a501-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) 원격 호스트에서 제공하는 암호화가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="8a501-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) TLS 핸드셰이크 중 메시지 처리가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="8a501-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) 들어오는 메시지가 해시 MAC 검사에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a  hash MAC check.</span></span>
- <span data-ttu-id="8a501-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) 기본 TCP 소켓 보내기가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="8a501-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 들어오는 메시지의 길이 필드가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="8a501-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) 들어오는 ChangeCipherSpec 메시지가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="8a501-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) 들어오는 TLS 인증서를 원격 TLS 서버 식별에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="8a501-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) 원격 호스트에서 제공하는 공개 키 암호가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="8a501-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) NetX Secure TLS 스택에서 지원하는 ciphersuite가 없다고 원격 호스트에서 알렸습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="8a501-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) 받은 TLS 메시지의 헤더에 알 수 없는 TLS 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="8a501-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) 받은 TLS 메시지의 헤더에 알고 있지만 지원되지 않는 TLS 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="8a501-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) 내부 TLS 패킷을 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="8a501-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) 원격 호스트에서 제공한 인증서가 올바르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="8a501-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) 원격 호스트가 오류를 알리는 경고를 보내고 TLS 세션을 종료했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="8a501-1830">**NX_PTR_ERROR** (0x07) 잘못된 포인터를 사용하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1830">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1831">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1831">Allowed From</span></span>

<span data-ttu-id="8a501-1832">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1832">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1833">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1833">Example</span></span>

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a><span data-ttu-id="8a501-1834">nx_web_http_server_start</span><span class="sxs-lookup"><span data-stu-id="8a501-1834">nx_web_http_server_start</span></span>

<span data-ttu-id="8a501-1835">HTTP 서버 시작</span><span class="sxs-lookup"><span data-stu-id="8a501-1835">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1836">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1836">Prototype</span></span>

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="8a501-1837">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1837">Description</span></span>

<span data-ttu-id="8a501-1838">이 서비스는 이전에 만든 HTTP 또는 HTTPS 서버 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1838">This service starts a previously created HTTP or HTTPS Server instance.</span></span>

<span data-ttu-id="8a501-1839">HTTPS 서버는 HTTP와 동일한 API를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1839">HTTPS servers share the same API as HTTP.</span></span> <span data-ttu-id="8a501-1840">HTTP 서버에서 TLS를 통해 HTTPS를 사용하도록 설정하려면 *nx_web_http_server_secure_configure()* 서비스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-1840">To enable HTTPS using TLS on an HTTP server, see the service *nx_web_http_server_secure_configure().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1841">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1841">Input Parameters</span></span>

- <span data-ttu-id="8a501-1842">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1842">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1843">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1843">Return Values</span></span>

- <span data-ttu-id="8a501-1844">**NX_SUCCESS** (0x00) HTTP 서버를 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1844">**NX_SUCCESS** (0x00) Successful HTTP Server Start</span></span>
- <span data-ttu-id="8a501-1845">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1845">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1846">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1846">Allowed From</span></span>

<span data-ttu-id="8a501-1847">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1847">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1848">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1848">Example</span></span>

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a><span data-ttu-id="8a501-1849">nx_web_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="8a501-1849">nx_web_http_server_stop</span></span>

<span data-ttu-id="8a501-1850">HTTP 서버 중지</span><span class="sxs-lookup"><span data-stu-id="8a501-1850">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1851">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1851">Prototype</span></span>

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="8a501-1852">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1852">Description</span></span>

<span data-ttu-id="8a501-1853">이 서비스는 이전에 만든 HTTP 서버 인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1853">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="8a501-1854">이 루틴은 HTTP 서버 인스턴스를 삭제하기 전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1854">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1855">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1855">Input Parameters</span></span>

- <span data-ttu-id="8a501-1856">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1856">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1857">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1857">Return Values</span></span>

- <span data-ttu-id="8a501-1858">**NX_SUCCESS** (0x00) HTTP 서버를 중지했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1858">**NX_SUCCESS** (0x00) Successful HTTP Server Stop</span></span>
- <span data-ttu-id="8a501-1859">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1859">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1860">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="8a501-1860">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1861">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1861">Allowed From</span></span>

<span data-ttu-id="8a501-1862">스레드</span><span class="sxs-lookup"><span data-stu-id="8a501-1862">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1863">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1863">Example</span></span>

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a><span data-ttu-id="8a501-1864">nx_web_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="8a501-1864">nx_web_http_server_type_get</span></span>

<span data-ttu-id="8a501-1865">클라이언트 HTTP 요청에서 파일 형식 추출</span><span class="sxs-lookup"><span data-stu-id="8a501-1865">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1866">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1866">Prototype</span></span>

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="8a501-1867">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1867">Description</span></span>

> [!NOTE]
> <span data-ttu-id="8a501-1868">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1868">This service is deprecated.</span></span> <span data-ttu-id="8a501-1869">사용자는 *nx_web_http_server_type_get_extended()* 서비스를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1869">Users are encouraged to use the service *nx_web_http_server_type_get_extended()*.</span></span>

<span data-ttu-id="8a501-1870">이 서비스는 *http_type_string* 버퍼에서 HTTP 요청 유형을 추출하고, 입력 버퍼 *name*(일반적으로 URL)의 *string_size* 에서 길이를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1870">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="8a501-1871">MIME 맵이 없으면 기본적으로 "텍스트/일반" 형식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1871">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="8a501-1872">MIME 맵이 있으면 추출된 형식을 HTTP 서버 기본 MIME 맵과 비교하여 매칭합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1872">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="8a501-1873">NetX 웹 HTTP 서버의 기본 MIME 맵은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1873">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="8a501-1874">html text/html</span><span class="sxs-lookup"><span data-stu-id="8a501-1874">html text/html</span></span>
- <span data-ttu-id="8a501-1875">htm text/html</span><span class="sxs-lookup"><span data-stu-id="8a501-1875">htm text/html</span></span>
- <span data-ttu-id="8a501-1876">txt text/plain</span><span class="sxs-lookup"><span data-stu-id="8a501-1876">txt text/plain</span></span>
- <span data-ttu-id="8a501-1877">gif image/gif</span><span class="sxs-lookup"><span data-stu-id="8a501-1877">gif image/gif</span></span>
- <span data-ttu-id="8a501-1878">jpg image/jpeg</span><span class="sxs-lookup"><span data-stu-id="8a501-1878">jpg image/jpeg</span></span>
- <span data-ttu-id="8a501-1879">ico image/x-icon</span><span class="sxs-lookup"><span data-stu-id="8a501-1879">ico image/x-icon</span></span>

<span data-ttu-id="8a501-1880">제공할 경우 사용자 정의 추가 MIME 맵 세트도 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1880">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="8a501-1881">사용자 정의 맵에 대한 자세한 내용은 *nx_web_http_server_mime_maps_addtional_set()* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-1881">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1882">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1882">Input Parameters</span></span>

- <span data-ttu-id="8a501-1883">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1883">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="8a501-1884">**name** 검색할 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1884">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="8a501-1885">**http_type_string** 추출된 HTML 형식 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1885">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="8a501-1886">**string_size** 추출된 HTML 형식 문자열 길이를 반환하는 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1886">**string_size** Pointer to return extracted HTML type string length.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1887">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1887">Return Values</span></span>

- <span data-ttu-id="8a501-1888">**NX_SUCCESS** (0x00) 형식을 추출했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1888">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="8a501-1889">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1889">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) 기본 "텍스트/일반" 형식이 반환되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1891">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1891">Allowed From</span></span>

<span data-ttu-id="8a501-1892">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="8a501-1892">Application</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1893">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1893">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a><span data-ttu-id="8a501-1894">nx_web_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="8a501-1894">nx_web_http_server_type_get_extended</span></span>

<span data-ttu-id="8a501-1895">클라이언트 HTTP 요청에서 파일 형식 추출</span><span class="sxs-lookup"><span data-stu-id="8a501-1895">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1896">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1896">Prototype</span></span>

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="8a501-1897">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1897">Description</span></span>

<span data-ttu-id="8a501-1898">이 서비스는 *http_type_string* 버퍼에서 HTTP 요청 유형을 추출하고, 입력 버퍼 *name*(일반적으로 URL)의 *string_size* 에서 길이를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1898">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="8a501-1899">MIME 맵이 없으면 기본적으로 "텍스트/일반" 형식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1899">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="8a501-1900">MIME 맵이 있으면 추출된 형식을 HTTP 서버 기본 MIME 맵과 비교하여 매칭합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1900">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="8a501-1901">NetX 웹 HTTP 서버의 기본 MIME 맵은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1901">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="8a501-1902">html text/html</span><span class="sxs-lookup"><span data-stu-id="8a501-1902">html text/html</span></span>
- <span data-ttu-id="8a501-1903">htm text/html</span><span class="sxs-lookup"><span data-stu-id="8a501-1903">htm text/html</span></span>
- <span data-ttu-id="8a501-1904">txt text/plain</span><span class="sxs-lookup"><span data-stu-id="8a501-1904">txt text/plain</span></span>
- <span data-ttu-id="8a501-1905">gif image/gif</span><span class="sxs-lookup"><span data-stu-id="8a501-1905">gif image/gif</span></span>
- <span data-ttu-id="8a501-1906">jpg image/jpeg</span><span class="sxs-lookup"><span data-stu-id="8a501-1906">jpg image/jpeg</span></span>
- <span data-ttu-id="8a501-1907">ico image/x-icon</span><span class="sxs-lookup"><span data-stu-id="8a501-1907">ico image/x-icon</span></span>

<span data-ttu-id="8a501-1908">제공할 경우 사용자 정의 추가 MIME 맵 세트도 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1908">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="8a501-1909">사용자 정의 맵에 대한 자세한 내용은 *nx_web_http_server_mime_maps_addtional_set()* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a501-1909">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="8a501-1910">이 서비스는 *nx_web_http_server_type_get()* 을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1910">This service replaces *nx_web_http_server_type_get*().</span></span> <span data-ttu-id="8a501-1911">이 버전을 사용하려면 호출자가 함수에 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1911">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1912">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1912">Input Parameters</span></span>

- <span data-ttu-id="8a501-1913">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1913">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="8a501-1914">**name** 검색할 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1914">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="8a501-1915">**name_length** 이름 길이</span><span class="sxs-lookup"><span data-stu-id="8a501-1915">**name_length** Length of name</span></span>
- <span data-ttu-id="8a501-1916">**http_type_string** 추출된 HTML 형식 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1916">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="8a501-1917">**http_type_string_max_size** http_type_string 버퍼의 크기</span><span class="sxs-lookup"><span data-stu-id="8a501-1917">**http_type_string_max_size** Size of the http_type_string buffer size</span></span>
- <span data-ttu-id="8a501-1918">**string_size** 추출된 HTML 형식 문자열 길이를 반환하는</span><span class="sxs-lookup"><span data-stu-id="8a501-1918">**string_size** Pointer to return extracted HTML type string</span></span>

<span data-ttu-id="8a501-1919">포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1919">length.</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1920">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1920">Return Values</span></span>

- <span data-ttu-id="8a501-1921">**NX_SUCCESS** (0x00) 형식을 추출했습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1921">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="8a501-1922">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1922">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) 기본 "텍스트/일반" 형식이 반환되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1924">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1924">Allowed From</span></span>

<span data-ttu-id="8a501-1925">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="8a501-1925">Application</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1926">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1926">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="8a501-1927">nx_web_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="8a501-1927">nx_web_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="8a501-1928">다이제스트 인증 콜백 함수 설정</span><span class="sxs-lookup"><span data-stu-id="8a501-1928">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1929">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1929">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a><span data-ttu-id="8a501-1930">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1930">Description</span></span>

<span data-ttu-id="8a501-1931">이 서비스는 다이제스트 인증을 수행할 때 호출되는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1931">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1932">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1932">Input Parameters</span></span>

- <span data-ttu-id="8a501-1933">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1933">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="8a501-1934">**digest_authenticate_callback** 다이제스트 인증 콜백에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1934">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1935">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1935">Return Values</span></span>

- <span data-ttu-id="8a501-1936">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="8a501-1936">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="8a501-1937">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1937">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8a501-1938">NX_NOT_SUPPORTED (0x4B) 다이제스트 인증을 사용하도록 설정되지 않음</span><span class="sxs-lookup"><span data-stu-id="8a501-1938">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1939">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1939">Allowed From</span></span>

<span data-ttu-id="8a501-1940">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="8a501-1940">Application</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1941">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1941">Example</span></span>

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a><span data-ttu-id="8a501-1942">nx_web_http_server_authenticate_check_set</span><span class="sxs-lookup"><span data-stu-id="8a501-1942">nx_web_http_server_authenticate_check_set</span></span>

<span data-ttu-id="8a501-1943">다이제스트 인증 콜백 함수 설정</span><span class="sxs-lookup"><span data-stu-id="8a501-1943">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="8a501-1944">프로토타입</span><span class="sxs-lookup"><span data-stu-id="8a501-1944">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a><span data-ttu-id="8a501-1945">Description</span><span class="sxs-lookup"><span data-stu-id="8a501-1945">Description</span></span>

<span data-ttu-id="8a501-1946">이 서비스는 인증 검사를 수행할 때 호출되는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a501-1946">This service sets the callback invoked when authenticate check is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8a501-1947">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a501-1947">Input Parameters</span></span>

- <span data-ttu-id="8a501-1948">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1948">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="8a501-1949">**authenticate_check_externded** 인증 검사 콜백에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="8a501-1949">**authenticate_check_externded** Pointer to authenticate check callback</span></span>

### <a name="return-values"></a><span data-ttu-id="8a501-1950">반환 값</span><span class="sxs-lookup"><span data-stu-id="8a501-1950">Return Values</span></span>

- <span data-ttu-id="8a501-1951">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="8a501-1951">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="8a501-1952">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="8a501-1952">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8a501-1953">허용 위치</span><span class="sxs-lookup"><span data-stu-id="8a501-1953">Allowed From</span></span>

<span data-ttu-id="8a501-1954">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="8a501-1954">Application</span></span>

### <a name="example"></a><span data-ttu-id="8a501-1955">예제</span><span class="sxs-lookup"><span data-stu-id="8a501-1955">Example</span></span>

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
