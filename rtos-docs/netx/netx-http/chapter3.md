---
title: 챕터 3 - NetX HTTP 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 NetX HTTP 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c58d0e3d7eca86816a9d656bf2b92a896ffb96fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811527"
---
# <a name="chapter-3---description-of-netx-http-services"></a><span data-ttu-id="9fdf6-103">챕터 3 - NetX HTTP 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="9fdf6-103">Chapter 3 - Description of NetX HTTP services</span></span>

<span data-ttu-id="9fdf6-104">이 챕터에서는 아래에 나열된 모든 NetX HTTP 서비스에 대해 알파벳 순서로 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-104">This chapter contains a description of all NetX HTTP services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="9fdf6-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="9fdf6-106">**HTTP 클라이언트 서비스:**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="9fdf6-107">nx_http_client_create *HTTP 클라이언트 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-107">nx_http_client_create *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="9fdf6-108">nx_http_client_delete *HTTP 클라이언트 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-108">nx_http_client_delete *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="9fdf6-109">nx_http_client_get_start *HTTP GET 요청 시작*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-109">nx_http_client_get_start *Start an HTTP GET request*</span></span>
- <span data-ttu-id="9fdf6-110">nx_http_client_get_start_extended *HTTP GET 요청 시작*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-110">nx_http_client_get_start_extended *Start an HTTP GET request*</span></span>
- <span data-ttu-id="9fdf6-111">nx_http_client_get_packet *다음 리소스 데이터 패킷 가져오기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-111">nx_http_client_get_packet *Get next resource data packet*</span></span>
- <span data-ttu-id="9fdf6-112">nx_http_client_put_start *HTTP PUT 요청 시작*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-112">nx_http_client_put_start *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="9fdf6-113">nx_http_client_put_start_extended *HTTP PUT 요청 시작*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-113">nx_http_client_put_start_extended *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="9fdf6-114">nx_http_client_put_packet *다음 리소스 데이터 패킷 보내기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-114">nx_http_client_put_packet *Send next resource data packet*</span></span>
- <span data-ttu-id="9fdf6-115">*nx_http_client_set_connect_port* *HTTP 서버에 연결할 포트 변경*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-115">*nx_http_client_set_connect_port* *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="9fdf6-116">**HTTP 서버 서비스:**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-116">**HTTP Server services:**</span></span>

- <span data-ttu-id="9fdf6-117">nx_http_server_cache_info_callback_set *지정된 URL의 기간 및 마지막으로 수정한 날짜를 검색하는 콜백 설정*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-117">nx_http_server_cache_info_callback_set *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="9fdf6-118">nx_http_server_callback_data_send *콜백 함수에서 HTTP 데이터 보내기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-118">nx_http_server_callback_data_send *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="9fdf6-119">nx_http_server_callback_generate_response_header *콜백 함수에서 응답 헤더 만들기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-119">nx_http_server_callback_generate_response_header *Create response header in callback functions*</span></span>
- <span data-ttu-id="9fdf6-120">nx_http_server_callback_generate_response_header_extended *콜백 함수에서 응답 헤더 만들기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-120">nx_http_server_callback_generate_response_header_extended *Create response header in callback functions*</span></span>
- <span data-ttu-id="9fdf6-121">nx_http_server_callback_packet_send *HTTP 콜백에서 HTTP 패킷 보내기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-121">nx_http_server_callback_packet_send *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="9fdf6-122">nx_http_server_callback_response_send *콜백 함수에서 응답 보내기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-122">nx_http_server_callback_response_send *Send response from callback function*</span></span>
- <span data-ttu-id="9fdf6-123">nx_http_server_callback_response_send_extended *콜백 함수에서 응답 보내기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-123">nx_http_server_callback_response_send_extended *Send response from callback function*</span></span>
- <span data-ttu-id="9fdf6-124">nx_http_server_content_get *요청에서 콘텐츠 가져오기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-124">nx_http_server_content_get *Get content from the request*</span></span>
- <span data-ttu-id="9fdf6-125">nx_http_server_content_get_extended *요청에서 콘텐츠 가져오기, 빈(콘텐츠 길이 0) 요청 지원*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-125">nx_http_server_content_get_extended *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="9fdf6-126">nx_http_server_content_length_get *요청에서 콘텐츠 길이 가져오기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-126">nx_http_server_content_length_get *Get length of content in the request*</span></span>
- <span data-ttu-id="9fdf6-127">nx_http_server_content_length_get_extended *요청에서 콘텐츠 길이 가져오기, 빈(콘텐츠 길이 0) 요청 지원*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-127">nx_http_server_content_length_get_extended *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="9fdf6-128">nx_http_server_create *HTTP 서버 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-128">nx_http_server_create *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="9fdf6-129">nx_http_server_delete *HTTP 서버 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-129">nx_http_server_delete *Delete an HTTP Server instance*</span></span>
- <span data-ttu-id="9fdf6-130">nx_http_server_get_entity_content *URL에서 엔터티 콘텐츠의 크기 및 위치 반환*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-130">nx_http_server_get_entity_content *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="9fdf6-131">nx_http_server_get_entity_header *URL 엔터티 헤더를 지정된 버퍼로 추출*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-131">nx_http_server_get_entity_header *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="9fdf6-132">nx_http_server_gmt_callback_set *GMT 날짜 및 시간을 검색하는 콜백 설정*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-132">nx_http_server_gmt_callback_set *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="9fdf6-133">nx_http_server_invalid_userpassword_notify_set *클라이언트 요청에서 잘못된 사용자 이름과 암호를 받은 경우의 콜백 설정*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-133">nx_http_server_invalid_userpassword_notify_set *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="9fdf6-134">nx_http_server_mime_maps_additional_set *HTML에 대한 추가 MIME 맵 정의*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-134">nx_http_server_mime_maps_additional_set *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="9fdf6-135">nx_http_server_packet_content_find *HTTP 헤더에서 콘텐츠 길이 추출 및 콘텐츠 데이터 시작에 대한 포인터 설정*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-135">nx_http_server_packet_content_find *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="9fdf6-136">nx_http_server_packet_get *클라이언트 패킷 직접 받기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-136">nx_http_server_packet_get *Receive client packet directly*</span></span>
- <span data-ttu-id="9fdf6-137">nx_http_server_param_get *요청에서 매개 변수 가져오기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-137">nx_http_server_param_get *Get parameter from the request*</span></span>
- <span data-ttu-id="9fdf6-138">nx_http_server_query_get *요청에서 쿼리 가져오기*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-138">nx_http_server_query_get *Get query from the request*</span></span>
- <span data-ttu-id="9fdf6-139">nx_http_server_start *HTTP 서버 시작*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-139">nx_http_server_start *Start the HTTP Server*</span></span>
- <span data-ttu-id="9fdf6-140">nx_http_server_stop *HTTP 서버 중지*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-140">nx_http_server_stop *Stop the HTTP Server*</span></span>
- <span data-ttu-id="9fdf6-141">nx_http_server_type_get *헤더에서 HTTP 형식(예: 텍스트/일반) 추출*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-141">nx_http_server_type_get *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="9fdf6-142">nx_http_server_type_get_extended *헤더에서 HTTP 형식(예: 텍스트/일반) 추출*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-142">nx_http_server_type_get_extended *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="9fdf6-143">nx_http_server_digest_authenticate_notify_set *다이제스트 인증 콜백 함수 설정*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-143">nx_http_server_digest_authenticate_notify_set *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="9fdf6-144">nx_http_server_authentication_check_set *인증 확인 콜백 함수 설정*</span><span class="sxs-lookup"><span data-stu-id="9fdf6-144">nx_http_server_authentication_check_set *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="9fdf6-145">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="9fdf6-145">nx_http_client_create</span></span>

### <a name="create-an-http-client-instance"></a><span data-ttu-id="9fdf6-146">HTTP 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-146">Create an HTTP Client Instance</span></span>

<span data-ttu-id="9fdf6-147">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-147">**Prototype**</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
                          CHAR *client_name, NX_IP *ip_ptr, 
                          NX_PACKET_POOL *pool_ptr,
                          ULONG window_size);
```

<span data-ttu-id="9fdf6-148">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-148">**Description**</span></span>

<span data-ttu-id="9fdf6-149">이 서비스는 지정된 IP 인스턴스에서 HTTP 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-149">This service creates an HTTP Client instance on the specified IP instance.</span></span>

<span data-ttu-id="9fdf6-150">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-150">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-151">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-151">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="9fdf6-152">**client_name** HTTP 클라이언트 인스턴스의 이름</span><span class="sxs-lookup"><span data-stu-id="9fdf6-152">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="9fdf6-153">**ip_ptr** IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-153">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="9fdf6-154">**pool_ptr** 기본 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-154">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="9fdf6-155">이 풀의 패킷에는 전체 응답 헤더를 처리할 수 있을 만큼 큰 페이로드가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-155">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="9fdf6-156">이는 *nx_http_client.h* 의 NX_HTTP_CLIENT_MIN_PACKET_SIZE에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-156">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http_client.h*.</span></span>
- <span data-ttu-id="9fdf6-157">**window_size** 클라이언트의 TCP 소켓 수신 창의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-157">**window_size** Size of the Client’s TCP socket receive window.</span></span>

<span data-ttu-id="9fdf6-158">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-158">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-159">**NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="9fdf6-159">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="9fdf6-160">NX_PTR_ERROR (0x16) 잘못된 HTTP, ip_ptr 또는 패킷 풀 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-160">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="9fdf6-161">NX_HTTP_POOL_ERROR (0xE9) 패킷 풀의 잘못된 페이로드 크기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-161">NX_HTTP_POOL_ERROR(0xE9) Invalid payload size in packet pool</span></span>

<span data-ttu-id="9fdf6-162">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-162">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-163">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-163">Initialization, Threads</span></span>

<span data-ttu-id="9fdf6-164">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-164">**Example**</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status = nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);
  
/* If status is NX_SUCCESS an HTTP Client instance was successfully  created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="9fdf6-165">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="9fdf6-165">nx_http_client_delete</span></span>

### <a name="delete-an-http-client-instance"></a><span data-ttu-id="9fdf6-166">HTTP 클라이언트 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="9fdf6-166">Delete an HTTP Client Instance</span></span>

<span data-ttu-id="9fdf6-167">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-167">**Prototype**</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

<span data-ttu-id="9fdf6-168">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-168">**Description**</span></span>

<span data-ttu-id="9fdf6-169">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-169">This service deletes a previously created HTTP Client instance.</span></span>

<span data-ttu-id="9fdf6-170">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-170">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-171">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-171">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="9fdf6-172">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-172">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-173">**NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-173">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="9fdf6-174">NX_PTR_ERROR (0x16) 잘못된 HTTP 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-174">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="9fdf6-175">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-175">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="9fdf6-176">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-176">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-177">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-177">Threads</span></span>

<span data-ttu-id="9fdf6-178">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-178">**Example**</span></span>

```c
/* Delete the HTTP Client instance “my_client.” */
status = nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully  deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="9fdf6-179">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="9fdf6-179">nx_http_client_get_start</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="9fdf6-180">HTTP GET 요청 시작</span><span class="sxs-lookup"><span data-stu-id="9fdf6-180">Start an HTTP GET request</span></span>

<span data-ttu-id="9fdf6-181">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-181">**Prototype**</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource, CHAR *input_ptr,
                             UINT input_size, CHAR *username, CHAR *password,
                             ULONG wait_option);
```

<span data-ttu-id="9fdf6-182">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-182">**Description**</span></span>

<span data-ttu-id="9fdf6-183">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 가져오려고(GET) 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-183">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="9fdf6-184">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_http_client_get_packet* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-184">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="9fdf6-185">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-185">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="9fdf6-186">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-186">This service is deprecated.</span></span> <span data-ttu-id="9fdf6-187">개발자는 *nx_http_client_get_start_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-187">Developers are encouraged to migrate to *nx_http_client_get_start_extended()*</span></span>

<span data-ttu-id="9fdf6-188">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-188">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-189">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-189">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="9fdf6-190">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="9fdf6-190">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="9fdf6-191">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-191">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="9fdf6-192">**input_ptr** GET 요청의 추가 데이터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-192">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="9fdf6-193">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-193">This is optional.</span></span> <span data-ttu-id="9fdf6-194">유효한 경우 지정된 입력이 메시지의 콘텐츠 영역에 배치되고 GET 작업 대신 POST가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-194">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="9fdf6-195">**input_size** input_ptr에서 가리키는 선택적 추가 입력의 바이트 수</span><span class="sxs-lookup"><span data-stu-id="9fdf6-195">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="9fdf6-196">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-196">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="9fdf6-197">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-197">**password** Pointer to optional password for authentication.</span></span><span data-ttu-id="9fdf6-198">
-\*\*wait_option*\* 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-198">
-\*\*wait_option*\* Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="9fdf6-199">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-199">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="9fdf6-200">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-200">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="9fdf6-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="9fdf6-202">TX_WAIT_FOREVER는 HTTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-202">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="9fdf6-203">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-203">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="9fdf6-204">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-204">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-205">**NX_SUCCESS** (0x00) HTTP 클라이언트 GET 시작 메시지를 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="9fdf6-205">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="9fdf6-206">**NX_HTTP_ERROR** (0xE0) 내부 HTTP 클라이언트 오류</span><span class="sxs-lookup"><span data-stu-id="9fdf6-206">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="9fdf6-207">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-207">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="9fdf6-208">**NX_HTTP_FAILED** (0xE2) HTTP 서버와 통신하는 중 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-208">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="9fdf6-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 및/또는 암호</span><span class="sxs-lookup"><span data-stu-id="9fdf6-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="9fdf6-210">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-210">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-211">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-211">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="9fdf6-212">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-212">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-213">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-213">Threads</span></span>

<span data-ttu-id="9fdf6-214">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-214">**Example**</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  POST_MESSAGE, sizeof(POST_MESSAGE),
                                  “myname”, “mypassword”, 1000);
 
/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```


## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="9fdf6-215">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="9fdf6-215">nx_http_client_get_start_extended</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="9fdf6-216">HTTP GET 요청 시작</span><span class="sxs-lookup"><span data-stu-id="9fdf6-216">Start an HTTP GET request</span></span>

<span data-ttu-id="9fdf6-217">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-217">**Prototype**</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *input_ptr, UINT input_size, CHAR *username,
     UINT username_length, CHAR *password, UINT password_length,
     ULONG wait_option);
```

<span data-ttu-id="9fdf6-218">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-218">**Description**</span></span>

<span data-ttu-id="9fdf6-219">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스의 "리소스" 포인터에서 지정한 리소스를 가져오려고(GET) 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-219">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="9fdf6-220">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_http_client_get_packet* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-220">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="9fdf6-221">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 GET 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-221">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="9fdf6-222">이 서비스는 *nx_http_client_get_start()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-222">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="9fdf6-223">호출자가 리소스, 사용자 이름 및 암호의 길이를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-223">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="9fdf6-224">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-224">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-225">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-225">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="9fdf6-226">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="9fdf6-226">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="9fdf6-227">**resource** 요청된 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-227">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="9fdf6-228">**resource_length** 요청된 리소스에 대한 URL 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-228">**resource_length** Length of URL string for requested resource.</span></span>
- <span data-ttu-id="9fdf6-229">**input_ptr** GET 요청의 추가 데이터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-229">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="9fdf6-230">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-230">This is optional.</span></span> <span data-ttu-id="9fdf6-231">유효한 경우 지정된 입력이 메시지의 콘텐츠 영역에 배치되고 GET 작업 대신 POST가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-231">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="9fdf6-232">**input_size** input_ptr에서 가리키는 선택적 추가 입력의 바이트 수</span><span class="sxs-lookup"><span data-stu-id="9fdf6-232">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="9fdf6-233">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-233">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="9fdf6-234">**username_length** 인증을 위한 선택적 사용자 이름의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-234">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="9fdf6-235">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-235">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="9fdf6-236">**password_length** 인증을 위한 선택적 암호의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-236">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="9fdf6-237">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-237">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="9fdf6-238">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-238">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="9fdf6-239">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-239">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="9fdf6-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="9fdf6-241">TX_WAIT_FOREVER는 HTTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-241">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="9fdf6-242">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-242">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="9fdf6-243">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-243">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-244">**NX_SUCCESS** (0x00) HTTP 클라이언트 GET 시작 메시지를 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="9fdf6-244">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="9fdf6-245">**NX_HTTP_ERROR** (0xE0) 내부 HTTP 클라이언트 오류</span><span class="sxs-lookup"><span data-stu-id="9fdf6-245">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="9fdf6-246">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-246">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="9fdf6-247">**NX_HTTP_FAILED** (0xE2) HTTP 서버와 통신하는 중 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-247">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="9fdf6-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 및/또는 암호</span><span class="sxs-lookup"><span data-stu-id="9fdf6-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="9fdf6-249">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-249">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-250">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-250">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="9fdf6-251">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-251">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-252">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-252">Threads</span></span>

<span data-ttu-id="9fdf6-253">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-253">**Example**</span></span>
            
```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5),
                                           “/TEST.HTM”,
                                           9, NX_NULL, 0, “myname”, 6,
                                           “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), 
                                           “/TEST.HTM”,
                                           9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                           “myname”, 6, “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="9fdf6-254">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="9fdf6-254">nx_http_client_get_packet</span></span>

### <a name="get-next-resource-data-packet"></a><span data-ttu-id="9fdf6-255">다음 리소스 데이터 패킷 가져오기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-255">Get next resource data packet</span></span>

<span data-ttu-id="9fdf6-256">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-256">**Prototype**</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET **packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="9fdf6-257">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-257">**Description**</span></span>

<span data-ttu-id="9fdf6-258">이 서비스는 이전 *nx_http_client_get_start* 호출에서 요청한 리소스 콘텐츠의 다음 패킷을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-258">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="9fdf6-259">이 루틴에 대한 연속 호출은 NX_HTTP_GET_DONE의 반환 상태를 받을 때까지 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-259">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

<span data-ttu-id="9fdf6-260">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-260">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-261">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-261">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="9fdf6-262">**packet_ptr** 부분 리소스 콘텐츠가 포함된 패킷 포인터의 대상</span><span class="sxs-lookup"><span data-stu-id="9fdf6-262">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="9fdf6-263">**wait_option** 서비스에서 HTTP 클라이언트 GET 패킷을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-263">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="9fdf6-264">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-264">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="9fdf6-265">**시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-265">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="9fdf6-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="9fdf6-267">TX_WAIT_FOREVER는 HTTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-267">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="9fdf6-268">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-268">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="9fdf6-269">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-269">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-270">**NX_SUCCESS** (0x00) HTTP 클라이언트 GET 패킷을 성공적으로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-270">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
- <span data-ttu-id="9fdf6-271">**NX_HTTP_GET_DONE** (0xEC) HTTP 클라이언트 GET 패킷이 완료됨</span><span class="sxs-lookup"><span data-stu-id="9fdf6-271">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
- <span data-ttu-id="9fdf6-272">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 GET 모드가 아님</span><span class="sxs-lookup"><span data-stu-id="9fdf6-272">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="9fdf6-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) 잘못된 패킷 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="9fdf6-274">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-275">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-275">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="9fdf6-276">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-276">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-277">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-277">Threads</span></span>

<span data-ttu-id="9fdf6-278">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-278">**Example**</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
Note that the nx_http_client_get_start routine must have been called
previously. */
status = nx_http_client_get_packet(&my_client, &next_packet, 1000);
 
/* If status is NX_SUCCESS, the next packet of content is pointed to by 
“next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="9fdf6-279">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="9fdf6-279">nx_http_client_put_start</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="9fdf6-280">HTTP PUT 요청 시작</span><span class="sxs-lookup"><span data-stu-id="9fdf6-280">Start an HTTP PUT request</span></span> 

<span data-ttu-id="9fdf6-281">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-281">**Prototype**</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource,
                             CHAR *username, CHAR *password,
                             ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="9fdf6-282">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-282">**Description**</span></span>

<span data-ttu-id="9fdf6-283">이 서비스는 지정된 리소스가 포함된 PUT 요청을 제공된 IP 주소의 HTTP 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-283">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="9fdf6-284">이 루틴이 성공하면 애플리케이션 코드에서 *nx_http_client_put_packet* 루틴을 연속적으로 호출하여 실제로 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-284">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="9fdf6-285">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-285">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="9fdf6-286">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-286">This service is deprecated.</span></span> <span data-ttu-id="9fdf6-287">개발자는 *nx_http_client_put_start_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-287">Developers are encouraged to migrate to *nx_http_client_put_start_extended()*.</span></span>

<span data-ttu-id="9fdf6-288">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-288">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-289">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-289">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="9fdf6-290">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="9fdf6-290">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="9fdf6-291">**resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-291">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="9fdf6-292">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-292">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="9fdf6-293">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-293">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="9fdf6-294">**total_bytes** 전송 중인 리소스의 총 바이트 수</span><span class="sxs-lookup"><span data-stu-id="9fdf6-294">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="9fdf6-295">후속 호출을 통해 *nx_http_client_put_packet* 에 보내는 모든 패킷의 결합된 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-295">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="9fdf6-296">**wait_option** 서비스에서 HTTP 클라이언트 PUT 시작을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-296">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="9fdf6-297">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-297">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="9fdf6-298">**시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-298">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="9fdf6-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="9fdf6-300">TX_WAIT_FOREVER는 HTTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-300">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="9fdf6-301">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-301">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="9fdf6-302">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-302">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-303">**NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="9fdf6-303">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="9fdf6-304">**NX_HTTP_USERNAME_TOO_LONG**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-304">**NX_HTTP_USERNAME_TOO_LONG**</span></span>
- <span data-ttu-id="9fdf6-305">**(0xF1) 사용자 이름이 버퍼에 비해 너무 큼**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-305">**(0xF1) Username too large for buffer**</span></span>
- <span data-ttu-id="9fdf6-306">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-306">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="9fdf6-307">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-307">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-308">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-308">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="9fdf6-309">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-309">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="9fdf6-310">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-310">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-311">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-311">Threads</span></span>

<span data-ttu-id="9fdf6-312">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-312">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                 “/TEST.HTM”, “myname”, “mypassword”, 20, 
                                 NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="9fdf6-313">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="9fdf6-313">nx_http_client_put_start_extended</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="9fdf6-314">HTTP PUT 요청 시작</span><span class="sxs-lookup"><span data-stu-id="9fdf6-314">Start an HTTP PUT request</span></span>

<span data-ttu-id="9fdf6-315">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-315">**Prototype**</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *username,UINT username_length, CHAR *password,
     UINT password_length, ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="9fdf6-316">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-316">**Description**</span></span>

<span data-ttu-id="9fdf6-317">이 서비스는 지정된 리소스가 포함된 PUT 요청을 제공된 IP 주소의 HTTP 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-317">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="9fdf6-318">이 루틴이 성공하면 애플리케이션 코드에서 *nx_http_client_put_packet* 루틴을 연속적으로 호출하여 실제로 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-318">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="9fdf6-319">리소스 문자열은 로컬 파일(예: "/index.htm")을 참조할 수 있습니다. 또는 HTTP 서버에서 PUT 요청 참조를 지원한다고 나타내는 경우 다른 URL(예: `http://abc.website.com/index.htm`)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-319">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="9fdf6-320">이 서비스는 *nx_http_client_put_start()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-320">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="9fdf6-321">호출자가 리소스, 사용자 이름 및 암호의 길이를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-321">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="9fdf6-322">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-322">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-323">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-323">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="9fdf6-324">**ip_address** HTTP 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="9fdf6-324">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="9fdf6-325">**resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-325">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="9fdf6-326">**resource_length** 서버에 보내는 리소스에 대한 URL 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-326">**resource_length** Length of URL string for resource to send to Server.</span></span>
- <span data-ttu-id="9fdf6-327">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-327">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="9fdf6-328">**username_length** 인증을 위한 선택적 사용자 이름의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-328">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="9fdf6-329">**password** 인증을 위한 선택적 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-329">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="9fdf6-330">**password_length** 인증을 위한 선택적 암호의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-330">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="9fdf6-331">**total_bytes** 전송 중인 리소스의 총 바이트 수</span><span class="sxs-lookup"><span data-stu-id="9fdf6-331">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="9fdf6-332">후속 호출을 통해 *nx_http_client_put_packet* 에 보내는 모든 패킷의 결합된 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-332">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="9fdf6-333">**wait_option** 서비스에서 HTTP 클라이언트 PUT 시작을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-333">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="9fdf6-334">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-334">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="9fdf6-335">**시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-335">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="9fdf6-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="9fdf6-337">TX_WAIT_FOREVER는 HTTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-337">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="9fdf6-338">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-338">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="9fdf6-339">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-339">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-340">**NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="9fdf6-340">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="9fdf6-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) 사용자 이름이 버퍼에 비해 너무 큼</span><span class="sxs-lookup"><span data-stu-id="9fdf6-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
- <span data-ttu-id="9fdf6-342">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-342">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="9fdf6-343">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-343">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-344">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-344">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="9fdf6-345">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-345">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="9fdf6-346">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-346">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-347">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-347">Threads</span></span>

<span data-ttu-id="9fdf6-348">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-348">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                          “/TEST.HTM”, 9, “myname”, 6, 
                                          “mypassword”, 
                                          10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="9fdf6-349">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="9fdf6-349">nx_http_client_put_packet</span></span>

### <a name="send-next-resource-data-packet"></a><span data-ttu-id="9fdf6-350">다음 리소스 데이터 패킷 보내기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-350">Send next resource data packet</span></span>

<span data-ttu-id="9fdf6-351">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-351">**Prototype**</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET *packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="9fdf6-352">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-352">**Description**</span></span>

<span data-ttu-id="9fdf6-353">이 서비스는 리소스 콘텐츠의 다음 패킷을 HTTP 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-353">This service attempts to send the next packet of resource content to the HTTP Server.</span></span> <span data-ttu-id="9fdf6-354">이 루틴은 보낸 패킷의 결합된 길이가 이전 *nx_http_client_put_start()* 호출에 지정된 "total_bytes"와 같을 때까지 반복적으로 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-354">Note that this routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start()* call.</span></span>

<span data-ttu-id="9fdf6-355">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-355">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-356">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-356">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="9fdf6-357">**packet_ptr** HTTP 서버에 보내는 리소스의 다음 콘텐츠에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-357">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="9fdf6-358">**wait_option** 서비스에서 HTTP 클라이언트 PUT 패킷을 처리하기 위해 내부적으로 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-358">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="9fdf6-359">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-359">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="9fdf6-360">**시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-360">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="9fdf6-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="9fdf6-362">TX_WAIT_FOREVER는 HTTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-362">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /> <span data-ttu-id="9fdf6-363">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-363">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="9fdf6-364">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-364">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-365">**NX_SUCCESS** (0x00) HTTP 클라이언트 패킷을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="9fdf6-365">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="9fdf6-366">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-366">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="9fdf6-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) \*\* 서버 오류 코드를 받음 -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) 잘못된 패킷 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code\*\* -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="9fdf6-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 및/또는 암호</span><span class="sxs-lookup"><span data-stu-id="9fdf6-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
- <span data-ttu-id="9fdf6-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) PUT이 완료되기 전에 서버에서 응답함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
- <span data-ttu-id="9fdf6-370">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-370">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-371">NX_INVALID_PACKET (0x12) 패킷이 TCP 헤더에 비해 너무 작음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-371">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="9fdf6-372">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-372">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="9fdf6-373">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-373">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-374">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-374">Threads</span></span>

<span data-ttu-id="9fdf6-375">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-375">**Example**</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
“/TEST.HTM” to the HTTP Server. */
status = nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                                  NX_PACKET *packet_ptr,
                                  ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM
has successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="9fdf6-376">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="9fdf6-376">nx_http_client_set_connect_port</span></span>

### <a name="set-the-connection-port-to-the-server"></a><span data-ttu-id="9fdf6-377">서버에 대한 연결 포트 설정</span><span class="sxs-lookup"><span data-stu-id="9fdf6-377">Set the connection port to the Server</span></span>

<span data-ttu-id="9fdf6-378">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-378">**Prototype**</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                    UINT port);
```

<span data-ttu-id="9fdf6-379">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-379">**Description**</span></span>

<span data-ttu-id="9fdf6-380">이 서비스는 런타임에 지정된 포트에서 HTTP 서버에 연결할 때 연결 포트를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-380">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="9fdf6-381">그렇지 않으면 연결 포트의 기본값은 80입니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-381">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="9fdf6-382">이는 *nx_http_client_get_start*() 및 *nx_http_client_put_start*() 전에 호출해야 합니다(예: HTTP 클라이언트에서 서버에 연결하는 경우).</span><span class="sxs-lookup"><span data-stu-id="9fdf6-382">This must be called before *nx_http_client_get_start*() and *nx_http_client_put_start*() e.g. when the HTTP Client connects with the Server.</span></span>

<span data-ttu-id="9fdf6-383">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-383">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-384">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-384">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="9fdf6-385">**port** 서버에 연결하기 위한 포트</span><span class="sxs-lookup"><span data-stu-id="9fdf6-385">**port** Port for connecting to the Server.</span></span>

<span data-ttu-id="9fdf6-386">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-386">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-387">**NX_SUCCESS** (0x00) 연결 포트를 성공적으로 변경함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-387">**NX_SUCCESS** (0x00) Successfully changed the connect port</span></span>
- <span data-ttu-id="9fdf6-388">**NX_INVALID_PORT** (0x46) 포트가 최댓값(0xFFFF)을 초과하거나 0임</span><span class="sxs-lookup"><span data-stu-id="9fdf6-388">**NX_INVALID_PORT** (0x46) Port exceeds the maximum (0xFFFF) or is zero.</span></span>
- <span data-ttu-id="9fdf6-389">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-389">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-390">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-390">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-391">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="9fdf6-391">Threads, Initialization</span></span>

<span data-ttu-id="9fdf6-392">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-392">**Example**</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status = nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="9fdf6-393">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="9fdf6-393">nx_http_server_cache_info_callback_set</span></span>

### <a name="set-the-callback-to-retrieve-url-max-age-and-date"></a><span data-ttu-id="9fdf6-394">URL 최대 기간 및 날짜를 검색하는 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="9fdf6-394">Set the callback to retrieve URL max age and date</span></span>

<span data-ttu-id="9fdf6-395">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-395">**Prototype**</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                           UINT (*cache_info_get)(CHAR *resource,
                                           UINT *max_age,
                                           NX_HTTP_SERVER_DATE *date));
```

<span data-ttu-id="9fdf6-396">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-396">**Description**</span></span>

<span data-ttu-id="9fdf6-397">이 서비스는 지정된 리소스의 최대 기간 및 마지막으로 수정한 날짜를 가져오기 위해 호출되는 콜백 서비스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-397">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

<span data-ttu-id="9fdf6-398">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-398">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-399">**server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-399">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="9fdf6-400">**cache_info_get** 콜백에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-400">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="9fdf6-401">**max_age** 리소스의 최대 기간에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-401">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="9fdf6-402">**data** 반환된 마지막으로 수정한 날짜에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-402">**data** Pointer to last modified date returned.</span></span>

<span data-ttu-id="9fdf6-403">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-403">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-404">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-404">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="9fdf6-405">**NX_PTR_ERROR** (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-405">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-406">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-406">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-407">초기화</span><span class="sxs-lookup"><span data-stu-id="9fdf6-407">Initialization</span></span>

<span data-ttu-id="9fdf6-408">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-408">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
UINT cache_info_get(CHAR *resource, UINT *max_age,
                   NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP
server is set by nx_http_server_start(), set the cache info callback: */
status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="9fdf6-409">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="9fdf6-409">nx_http_server_callback_data_send</span></span>

### <a name="send-data-from-callback-function"></a><span data-ttu-id="9fdf6-410">콜백 함수에서 데이터 보내기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-410">Send data from callback function</span></span>

<span data-ttu-id="9fdf6-411">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-411">**Prototype**</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                      VOID *data_ptr,
                                      ULONG data_length);
```

<span data-ttu-id="9fdf6-412">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-412">**Description**</span></span>

<span data-ttu-id="9fdf6-413">이 서비스는 애플리케이션의 콜백 루틴에서 제공된 패킷의 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-413">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="9fdf6-414">일반적으로 GET/POST 요청과 연결된 동적 데이터를 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-414">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="9fdf6-415">이 함수를 사용할 경우 콜백 루틴에서 전체 응답을 적절한 형식으로 보내di 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-415">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="9fdf6-416">또한 콜백 루틴에서 NX_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-416">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="9fdf6-417">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-417">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-418">**server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="9fdf6-419">**data_ptr** 보내는 데이터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-419">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="9fdf6-420">**data_length** 보내는 바이트의 수</span><span class="sxs-lookup"><span data-stu-id="9fdf6-420">**data_length** Number of bytes to send.</span></span>

<span data-ttu-id="9fdf6-421">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-421">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-422">**NX_SUCCESS** (0x00) 서버 데이터를 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="9fdf6-422">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="9fdf6-423">**NX_PTR_ERROR** (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-423">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-424">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-424">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-425">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-425">Threads</span></span>

<span data-ttu-id="9fdf6-426">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-426">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
       (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
        contents directly. */

        nx_http_server_callback_data_send(server_ptr,
                                         "HTTP/1.0 200 \r\nContent-Length:
                                         103\r\nContent-Type: text/html\r\n\r\n",
                                         63);
        nx_http_server_callback_data_send(server_ptr, "<HTML>> r\n<HEAD><TITLE>NetX
                                         HTTP Test </TITLE></HEAD>\r\n
                                         <BODY>\r\n<H1>NetX Test Page
                                         </H1>\r\n</BODY>> r\n</HTML>\r\n", 103);
        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="9fdf6-427">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="9fdf6-427">nx_http_server_callback_generate_response_header</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="9fdf6-428">콜백 함수에서 응답 헤더 만들기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-428">Create a response header in a callback function</span></span>

<span data-ttu-id="9fdf6-429">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-429">**Prototype**</span></span>

```c
UINT nx_http_server_callback_generate_response_header(NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr, CHAR *status_code, UINT content_length,
     CHAR *content_type, CHAR* additional_header);
```

<span data-ttu-id="9fdf6-430">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-430">**Description**</span></span>

<span data-ttu-id="9fdf6-431">이 서비스는 HTTP 서버에서 클라이언트 GET, PUT 및 DELETE 요청에 응답할 때 _ *nx_http_server_generate_response_header* 내부 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-431">This service calls the internal function _ *nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="9fdf6-432">HTTP 서버 애플리케이션에서 클라이언트에 대한 응답을 설계하는 경우 HTTP 서버 콜백 함수에서 사용하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-432">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="9fdf6-433">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-433">This service is deprecated.</span></span> <span data-ttu-id="9fdf6-434">개발자는 *nxd_http_server_callback_generate_response_header_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-434">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

<span data-ttu-id="9fdf6-435">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-435">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-436">**server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-436">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="9fdf6-437">**packet_pptr** 메시지에 할당된 패킷 포인터를 가리키는 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-437">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="9fdf6-438">**status_code** 리소스의 상태 표시</span><span class="sxs-lookup"><span data-stu-id="9fdf6-438">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="9fdf6-439">예제:</span><span class="sxs-lookup"><span data-stu-id="9fdf6-439">Examples:</span></span>
- <span data-ttu-id="9fdf6-440">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-440">**NX_HTTP_STATUS_OK**</span></span>
- <span data-ttu-id="9fdf6-441">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-441">**NX_HTTP_STATUS_MODIFIED**</span></span>
- <span data-ttu-id="9fdf6-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="9fdf6-443">**content_length** 콘텐츠의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-443">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="9fdf6-444">**content_type** HTTP 형식(예: "텍스트/일반")</span><span class="sxs-lookup"><span data-stu-id="9fdf6-444">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="9fdf6-445">**additional_header** 추가 헤더 텍스트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-445">**additional_header** Pointer to additional header text</span></span>

<span data-ttu-id="9fdf6-446">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-446">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-447">**NX_SUCCESS** (0x00) HTML 헤더를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="9fdf6-447">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="9fdf6-448">**NX_PTR_ERROR** (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-448">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-449">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-449">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-450">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-450">Threads</span></span>

<span data-ttu-id="9fdf6-451">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-451">**Example**</span></span>

```c
CHAR demotestbuffer[] = “<html>\r\n\r\n<head> r\n\r\n<title>Main                 \
                        Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n  \ 
                        </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
the HTTP server in nx_http_server_create, creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET     *sresp_packet_ptr;
    ULONG         string_length;
    CHAR          temp_string[30];
    ULONG         length = 0;

        length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length = (ULONG) nx_http_server_type_get(server_ptr, server_ptr ->
                   nx_http_server_request_resource, temp_string);

/* Null terminate the string. */
   temp_string[temp] = 0;

/* Now build a response header with server status is OK and no additional header info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
            &resp_packet_ptr, NX_HTTP_STATUS_OK,
            length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
            length, server_ptr >>
            nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

/* Now send the packet! */
   status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
            resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
        nx_packet_release(resp_packet_ptr);
        return status;
    }
/* Let HTTP server know the response has been sent. */
   return NX_HTTP_CALLBACK_COMPLETED;
}
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="9fdf6-452">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="9fdf6-452">nx_http_server_callback_generate_response_header_extended</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="9fdf6-453">콜백 함수에서 응답 헤더 만들기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-453">Create a response header in a callback function</span></span>

<span data-ttu-id="9fdf6-454">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-454">**Prototype**</span></span>

```c
UINT nx_http_server_callback_generate_response_header_extended(
     NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr,
     CHAR *status_code, UINT status_code_length,
     UINT content_length,
     CHAR *content_type, UINT content_type_length,
     CHAR *additional_header,
     UINT additional_header_length);
```

<span data-ttu-id="9fdf6-455">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-455">**Description**</span></span>

<span data-ttu-id="9fdf6-456">이 서비스는 HTTP 서버에서 클라이언트 GET, PUT 및 DELETE 요청에 응답할 때 _ *nx_http_server_generate_response_header()* 내부 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-456">This service calls the internal function _ *nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="9fdf6-457">HTTP 서버 애플리케이션에서 클라이언트에 대한 응답을 설계하는 경우 HTTP 서버 콜백 함수에서 사용하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-457">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="9fdf6-458">이 서비스는 *nx_http_server_callback_generate_response_header()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-458">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="9fdf6-459">이 버전은 추가 길이 정보를 콜백 함수에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-459">This version supplies additional length information to the callback function.</span></span>

<span data-ttu-id="9fdf6-460">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-460">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-461">**server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-461">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="9fdf6-462">**packet_pptr** 메시지에 할당된 패킷 포인터를 가리키는 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-462">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="9fdf6-463">**status_code** 리소스의 상태 표시</span><span class="sxs-lookup"><span data-stu-id="9fdf6-463">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="9fdf6-464">예제:</span><span class="sxs-lookup"><span data-stu-id="9fdf6-464">Examples:</span></span>
  - <span data-ttu-id="9fdf6-465">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-465">**NX_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="9fdf6-466">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-466">**NX_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="9fdf6-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="9fdf6-468">**status_code** 상태 코드의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-468">**status_code** Length of status code</span></span>
- <span data-ttu-id="9fdf6-469">**content_length** 콘텐츠의 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-469">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="9fdf6-470">**content_type** HTTP 형식(예: "텍스트/일반")</span><span class="sxs-lookup"><span data-stu-id="9fdf6-470">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="9fdf6-471">**content_type_length** HTTP 형식의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-471">**content_type_length** Length of HTTP type</span></span>
- <span data-ttu-id="9fdf6-472">**additional_header** 추가 헤더 텍스트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-472">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="9fdf6-473">**additional_header_length** 추가 헤더 텍스트의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-473">**additional_header_length** Length of additional header text</span></span>

<span data-ttu-id="9fdf6-474">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-474">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-475">**NX_SUCCESS** (0x00) 헤더를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="9fdf6-475">**NX_SUCCESS** (0x00) Successfully created header</span></span>
- <span data-ttu-id="9fdf6-476">**NX_PTR_ERROR** (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-476">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-477">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-477">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-478">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-478">Threads</span></span>

<span data-ttu-id="9fdf6-479">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-479">**Example**</span></span>

```c
  CHAR demotestbuffer[] = “<html>\r\n\r\n<head>\r\n\r\n<title>Main                    \
                          Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n     \
                          </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
   the HTTP server in nx_http_server_create, creates a response to the received
   Client request. */

   UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, NX_PACKET *recv_packet_ptr)
   {
     NX_PACKET *sresp_packet_ptr;
     ULONG string_length;
     CHAR temp_string[30];
     ULONG length = 0;

     length = sizeof(demotestbuffer) - 1;

    /* Derive the client request type from the client request. */
       string_length = (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr >>
                       nx_http_server_request_resource, temp_string,
                       sizeof(temp_string));

    /* Null terminate the string. */
       temp_string[temp] = 0;

    /* Now build a response header with server status is OK and no additional header
      info. */
      status = nx_http_server_callback_generate_response_header_extended(
               http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
               sizeof(NX_HTTP_STATUS_OK) - 1, length,
               temp_string, string_length, NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
       status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                length, server_ptr ->
                nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
       status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                   resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);
    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }
    /* Let HTTP server know the response has been sent. */
       return NX_HTTP_CALLBACK_COMPLETED;
}
```

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="9fdf6-480">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="9fdf6-480">nx_http_server_callback_packet_send</span></span>

### <a name="send-an-http-packet-from-callback-function"></a><span data-ttu-id="9fdf6-481">콜백 함수에서 HTTP 패킷 보내기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-481">Send an HTTP packet from callback function</span></span>

<span data-ttu-id="9fdf6-482">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-482">**Prototype**</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr);
```

<span data-ttu-id="9fdf6-483">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-483">**Description**</span></span>

<span data-ttu-id="9fdf6-484">이 서비스는 HTTP 콜백에서 전체 HTTP 서버 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-484">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="9fdf6-485">HTTP 서버는 NX_HTTP_SERVER _TIMEOUT_SEND를 사용하여 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-485">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="9fdf6-486">HTTP 헤더와 데이터는 패킷에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-486">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="9fdf6-487">반환 상태에서 오류가 표시되는 경우 HTTP 애플리케이션에서 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-487">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="9fdf6-488">콜백에서 NX_HTTP_CALLBACK_COMPLETED를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-488">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="9fdf6-489">자세한 예제는 *nx_http_server_callback_generate_response_header()* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-489">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

<span data-ttu-id="9fdf6-490">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-490">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-491">**server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-491">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="9fdf6-492">**packet_ptr** 보내는 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-492">**packet_ptr** Pointer to the packet to send</span></span>

<span data-ttu-id="9fdf6-493">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-493">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-494">**NX_SUCCESS** (0x00) HTTP 서버 패킷을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="9fdf6-494">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="9fdf6-495">**NX_PTR_ERROR** (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-495">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-496">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-496">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-497">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-497">Threads</span></span>

<span data-ttu-id="9fdf6-498">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-498">**Example**</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
Client directly. */

   status = nx_http_server_callback_response_send**(server_ptr, packet_ptr);
   
   if (status != NX_SUCCESS)
   {
        nx_packet_release(packet_ptr);
   }
    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="9fdf6-499">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="9fdf6-499">nx_http_server_callback_response_send</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="9fdf6-500">콜백 함수에서 응답 보내기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-500">Send response from callback function</span></span>

<span data-ttu-id="9fdf6-501">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-501">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
     CHAR *header, CHAR *information, CHAR additional_info);
```

<span data-ttu-id="9fdf6-502">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-502">**Description**</span></span>

<span data-ttu-id="9fdf6-503">이 서비스는 애플리케이션의 콜백 루틴에서 제공된 응답 정보를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-503">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="9fdf6-504">일반적으로 GET/POST 요청과 연결된 사용자 지정 응답을 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-504">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="9fdf6-505">이 함수를 사용하는 경우 콜백 루틴에서 NX_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-505">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="9fdf6-506">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-506">This service is deprecated.</span></span> <span data-ttu-id="9fdf6-507">개발자는 *nx_http_server_callback_response_send_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-507">Developers are encouraged to migrate to *nx_http_server_callback_response_send_extended().*</span></span>

<span data-ttu-id="9fdf6-508">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-508">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-509">**server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-509">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="9fdf6-510">**header** 응답 헤더 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-510">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="9fdf6-511">**information** 정보 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-511">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="9fdf6-512">**additional_info** 추가 정보 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-512">**additional_info** Pointer to the additional information string.</span></span>

<span data-ttu-id="9fdf6-513">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-513">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-514">**NX_SUCCESS** (0x00) HTTP 서버 응답을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="9fdf6-514">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

<span data-ttu-id="9fdf6-515">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-515">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-516">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-516">Threads</span></span>

<span data-ttu-id="9fdf6-517">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-517">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
       {

            /* In this example, we will complete the GET processing with
               a resource not found response. */
               nx_http_server_callback_response_send(server_ptr,
                                                    "HTTP/1.0 404 ",
                                                    "NetX HTTP Server unable to find
                                                    file: ", resource);
            /* Return completion status. */
               return(NX_HTTP_CALLBACK_COMPLETED);
        }
        return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="9fdf6-518">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="9fdf6-518">nx_http_server_callback_response_send_extended</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="9fdf6-519">콜백 함수에서 응답 보내기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-519">Send response from callback function</span></span>

<span data-ttu-id="9fdf6-520">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-520">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
     NX_HTTP_SERVER *server_ptr, CHAR *heade
     UINT header_length, CHAR *information,
     UINT information_length, CHAR *additional_info,
     UINT additional_info_length);
```

<span data-ttu-id="9fdf6-521">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-521">**Description**</span></span>

<span data-ttu-id="9fdf6-522">이 서비스는 애플리케이션의 콜백 루틴에서 제공된 응답 정보를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-522">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="9fdf6-523">일반적으로 GET/POST 요청과 연결된 사용자 지정 응답을 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-523">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="9fdf6-524">이 함수를 사용하는 경우 콜백 루틴에서 NX_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-524">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="9fdf6-525">이 서비스는 *nx_http_server_callback_response_send()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-525">This service replaces *nx_http_server_callback_response_send().*</span></span> <span data-ttu-id="9fdf6-526">이 버전은 길이 정보를 입력 인수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-526">This version takes length information as input argument.</span></span>

<span data-ttu-id="9fdf6-527">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-527">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-528">**server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-528">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="9fdf6-529">**header** 응답 헤더 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-529">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="9fdf6-530">**header_length** 응답 헤더 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-530">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="9fdf6-531">**information** 정보 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-531">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="9fdf6-532">**information_length** 정보 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-532">**information_length** Length of the information string.</span></span>
- <span data-ttu-id="9fdf6-533">**additional_info** 추가 정보 문자열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-533">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="9fdf6-534">**additional_info_length** 추가 정보 문자열의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-534">**additional_info_length** Length of the additional information string.</span></span>

<span data-ttu-id="9fdf6-535">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-535">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-536">**NX_SUCCESS** (0x00) 서버 응답을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="9fdf6-536">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

<span data-ttu-id="9fdf6-537">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-537">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-538">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-538">Threads</span></span>

<span data-ttu-id="9fdf6-539">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-539">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
           a resource not found response. */
           nx_http_server_callback_response_send_extended(server_ptr,
                                                         "HTTP/1.0 404 ", 12,
                                                         "NetX HTTP Server unable to find
                                                         file: ", 38, resource, 9);
        /* Return completion status. */
           return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="9fdf6-540">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="9fdf6-540">nx_http_server_content_get</span></span>

### <a name="get-content-from-the-request"></a><span data-ttu-id="9fdf6-541">요청에서 콘텐츠 가져오기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-541">Get content from the request</span></span>

<span data-ttu-id="9fdf6-542">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-542">**Prototype**</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

<span data-ttu-id="9fdf6-543">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-543">**Description**</span></span>

<span data-ttu-id="9fdf6-544">이 서비스는 POST 또는 PUT HTTP 클라이언트 요청에서 지정된 양의 콘텐츠를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-544">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="9fdf6-545">HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-545">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="9fdf6-546">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-546">This service is deprecated.</span></span> <span data-ttu-id="9fdf6-547">개발자는 nx_http_server_content_get_extended()로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-547">Developers are encouraged to migrate to nx_http_server_content_get_extended().</span></span>

<span data-ttu-id="9fdf6-548">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-548">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-549">**server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-549">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="9fdf6-550">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-550">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="9fdf6-551">이 패킷은 요청 알림 콜백에서 해제하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-551">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="9fdf6-552">**byte_offset** 콘텐츠 영역으로 오프셋하는 바이트의 수</span><span class="sxs-lookup"><span data-stu-id="9fdf6-552">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="9fdf6-553">**destination_ptr** 콘텐츠의 대상 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-553">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="9fdf6-554">**destination_size** 대상 영역에서 사용 가능한 최대 바이트 수</span><span class="sxs-lookup"><span data-stu-id="9fdf6-554">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="9fdf6-555">**actual_size** 복사된 콘텐츠의 실제 크기로 설정되는 대상 변수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-555">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="9fdf6-556">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-556">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-557">**NX_SUCCESS** (0x00) HTTP 서버 콘텐츠를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="9fdf6-557">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="9fdf6-558">**NX_HTTP_ERROR** (0xE0) HTTP 서버 내부 오류</span><span class="sxs-lookup"><span data-stu-id="9fdf6-558">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="9fdf6-559">**NX_HTTP_DATA_END** (0xE7) 요청 콘텐츠의 끝</span><span class="sxs-lookup"><span data-stu-id="9fdf6-559">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="9fdf6-560">**NX_HTTP_TIMEOUT** (0xE1) 콘텐츠의 다음 패킷을 가져오는 중에 HTTP 서버 시간이 초과됨</span><span class="sxs-lookup"><span data-stu-id="9fdf6-560">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="9fdf6-561">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-561">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-562">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-562">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="9fdf6-563">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-563">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-564">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-564">Threads</span></span>

<span data-ttu-id="9fdf6-565">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-565">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get(&my_server, packet_ptr,
                                   0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="9fdf6-566">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="9fdf6-566">nx_http_server_content_get_extended</span></span>

### <a name="get-content-from-the-requestsupports-zero-length-content-length"></a><span data-ttu-id="9fdf6-567">요청에서 콘텐츠 가져오기/길이가 0인 콘텐츠 길이 지원</span><span class="sxs-lookup"><span data-stu-id="9fdf6-567">Get content from the request/supports zero length Content Length</span></span>

<span data-ttu-id="9fdf6-568">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-568">**Prototype**</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr,
                                        ULONG byte_offset,
                                        CHAR *destination_ptr,
                                        UINT destination_size,
                                        UINT *actual_size);
```

<span data-ttu-id="9fdf6-569">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-569">**Description**</span></span>

<span data-ttu-id="9fdf6-570">이 서비스는 *nx_http_server_content_get()* 과 거의 동일하며, POST 또는 PUT HTTP 클라이언트 요청에서 지정된 양의 콘텐츠를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-570">This service is almost identical to *nx_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="9fdf6-571">그러나 콘텐츠 길이가 0인 요청('빈 요청')을 유효한 요청으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-571">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="9fdf6-572">HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-572">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="9fdf6-573">이 서비스는 *nx_http_server_content_get()* 을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-573">This service replaces *nx_http_server_content_get().*</span></span> <span data-ttu-id="9fdf6-574">이 버전을 사용하려면 호출자가 추가 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-574">This version requires caller to supply additional length information.</span></span>

<span data-ttu-id="9fdf6-575">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-575">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-576">**server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-576">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="9fdf6-577">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-577">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="9fdf6-578">이 패킷은 요청 알림 콜백에서 해제하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-578">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="9fdf6-579">**byte_offset** 콘텐츠 영역으로 오프셋하는 바이트의 수</span><span class="sxs-lookup"><span data-stu-id="9fdf6-579">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="9fdf6-580">**destination_ptr** 콘텐츠의 대상 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-580">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="9fdf6-581">**destination_size** 대상 영역에서 사용 가능한 최대 바이트 수</span><span class="sxs-lookup"><span data-stu-id="9fdf6-581">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="9fdf6-582">**actual_size** 복사된 콘텐츠의 실제 크기로 설정되는 대상 변수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-582">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="9fdf6-583">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-583">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-584">**NX_SUCCESS** (0x00) HTTP 콘텐츠를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="9fdf6-584">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="9fdf6-585">**NX_HTTP_ERROR** (0xE0) HTTP 서버 내부 오류</span><span class="sxs-lookup"><span data-stu-id="9fdf6-585">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="9fdf6-586">**NX_HTTP_DATA_END** (0xE7) 요청 콘텐츠의 끝</span><span class="sxs-lookup"><span data-stu-id="9fdf6-586">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="9fdf6-587">**NX_HTTP_TIMEOUT** (0xE1) 다음 패킷을 가져오는 중에 HTTP 서버 시간이 초과됨</span><span class="sxs-lookup"><span data-stu-id="9fdf6-587">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="9fdf6-588">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-589">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-589">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="9fdf6-590">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-590">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-591">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-591">Threads</span></span>

<span data-ttu-id="9fdf6-592">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-592">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get_extended(&my_server, packet_ptr,
                                            0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="9fdf6-593">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="9fdf6-593">nx_http_server_content_length_get</span></span>

### <a name="get-length-of-content-in-the-request"></a><span data-ttu-id="9fdf6-594">요청에서 콘텐츠 길이 가져오기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-594">Get length of content in the request</span></span>

<span data-ttu-id="9fdf6-595">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-595">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```
<span data-ttu-id="9fdf6-596">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-596">**Description**</span></span>

<span data-ttu-id="9fdf6-597">이 서비스는 제공된 패킷에서 HTTP 콘텐츠 길이를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-597">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="9fdf6-598">HTTP 콘텐츠가 없는 경우 이 루틴에서 0 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-598">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="9fdf6-599">HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-599">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="9fdf6-600">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-600">This service is deprecated.</span></span> <span data-ttu-id="9fdf6-601">개발자는 nx_http_server_content_length_get_extended()로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-601">Developers are encouraged to migrate to nx_http_server_content_length_get_extended().</span></span>

<span data-ttu-id="9fdf6-602">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-602">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-603">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-603">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="9fdf6-604">이 패킷은 요청 알림 콜백에서 해제하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-604">Note that this packet must not be released by the request notify callback.</span></span>

<span data-ttu-id="9fdf6-605">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-605">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-606">**content length** 오류 시 0 값이 반환됨</span><span class="sxs-lookup"><span data-stu-id="9fdf6-606">**content length** On error, a value of zero is returned</span></span>

<span data-ttu-id="9fdf6-607">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-607">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-608">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-608">Threads</span></span>

<span data-ttu-id="9fdf6-609">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-609">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
length = nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="9fdf6-610">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="9fdf6-610">nx_http_server_content_length_get_extended</span></span>

### <a name="get-length-of-content-in-the-requestsupports-content-length-of-zero-value"></a><span data-ttu-id="9fdf6-611">요청에서 콘텐츠 길이 가져오기/0 값의 콘텐츠 길이 지원</span><span class="sxs-lookup"><span data-stu-id="9fdf6-611">Get length of content in the request/supports Content Length of zero value</span></span>

<span data-ttu-id="9fdf6-612">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-612">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                               UINT *content_length);
```

<span data-ttu-id="9fdf6-613">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-613">**Description**</span></span>

<span data-ttu-id="9fdf6-614">이 서비스는 *nx_http_server_content_length_get()* 과 비슷하며, 제공된 패킷에서 HTTP 콘텐츠 길이를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-614">This service is similar to *nx_http_server_content_length_get()*; attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="9fdf6-615">그러나 반환 값은 성공적인 완료 상태를 나타내며, 실제 길이 값은 content_length 입력 포인터에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-615">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="9fdf6-616">HTTP 콘텐츠가 없거나 콘텐츠 길이가 0인 경우에도 이 루틴에서 여전히 성공적인 완료 상태를 반환하며 content_length 입력 포인터가 유효한 길이(0)를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-616">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="9fdf6-617">HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-617">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="9fdf6-618">이 서비스는 *nx_http_server_content_length_get*()을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-618">This service replaces *nx_http_server_content_length_get*().</span></span>

<span data-ttu-id="9fdf6-619">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-619">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-620">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-620">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="9fdf6-621">이 패킷은 요청 알림 콜백에서 해제하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-621">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="9fdf6-622">**content_length** 콘텐츠 길이 필드에서 검색된 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-622">**content_length** Pointer to value retrieved from Content Length field</span></span>

<span data-ttu-id="9fdf6-623">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-623">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-624">**NX_SUCCESS** (0x00) HTTP 서버 콘텐츠를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="9fdf6-624">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="9fdf6-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) 잘못된 HTTP 헤더 형식</span><span class="sxs-lookup"><span data-stu-id="9fdf6-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
- <span data-ttu-id="9fdf6-626">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-626">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-627">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-627">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-628">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-628">Threads</span></span>

<span data-ttu-id="9fdf6-629">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-629">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
ULONG content_length;

status = nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="9fdf6-630">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="9fdf6-630">nx_http_server_create</span></span>

### <a name="create-an-http-server-instance"></a><span data-ttu-id="9fdf6-631">HTTP 서버 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-631">Create an HTTP Server instance</span></span>

<span data-ttu-id="9fdf6-632">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-632">**Prototype**</span></span>

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
     CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
     VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
     UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
     UINT request_type, CHAR *resource, CHAR **name,
     CHAR **password, CHAR **realm),
     UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
     UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

<span data-ttu-id="9fdf6-633">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-633">**Description**</span></span>

<span data-ttu-id="9fdf6-634">이 서비스는 자체 ThreadX 스레드의 컨텍스트에서 실행되는 HTTP 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-634">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="9fdf6-635">선택적 *authentication_check* 및 *request_notify* 애플리케이션 콜백 루틴은 HTTP 서버의 기본 작업에 대한 애플리케이션 소프트웨어 제어를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-635">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="9fdf6-636">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-636">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-637">**http_server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-637">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="9fdf6-638">**http_server_name** HTTP 서버 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-638">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="9fdf6-639">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-639">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="9fdf6-640">**media_ptr** 이전에 만든 FileX 미디어 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-640">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="9fdf6-641">**stack_ptr** HTTP 서버 스레드 스택 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-641">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="9fdf6-642">**stack_size** HTTP 서버 스레드 스택 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-642">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="9fdf6-643">**authentication_check** 애플리케이션의 인증 확인 루틴에 대한 함수 포인터.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-643">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="9fdf6-644">지정되면 이 루틴이 각 HTTP 클라이언트 요청에 대해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-644">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="9fdf6-645">이 매개 변수가 NULL이면 인증이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-645">If this parameter is NULL no authentication will be performed.</span></span>
- <span data-ttu-id="9fdf6-646">**request_notify** 애플리케이션의 요청 알림 루틴에 대한 함수 포인터.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-646">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="9fdf6-647">지정되면 HTTP 서버에서 요청을 처리하기 전에 이 루틴이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-647">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="9fdf6-648">이렇게 하면 HTTP 클라이언트 요청을 완료하기 전에 리소스 이름을 리디렉션하거나 리소스 내의 필드를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-648">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

<span data-ttu-id="9fdf6-649">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-649">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-650">**NX_SUCCESS** (0x00) HTTP 서버를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="9fdf6-650">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="9fdf6-651">NX_PTR_ERROR (0x07) 잘못된 HTTP 서버, IP, 미디어, 스택 또는 패킷 풀 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-651">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="9fdf6-652">NX_HTTP_POOL_ERROR (0xE9) 풀의 패킷 페이로드가 전체 HTTP 요청을 포함할 만큼 충분히 크지 않음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-652">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

<span data-ttu-id="9fdf6-653">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-653">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-654">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-654">Initialization, Threads</span></span>

<span data-ttu-id="9fdf6-655">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-655">**Example**</span></span>

```c
/* Create an HTTP Server instance called “my_server.” */
status = nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
                              stack_ptr, stack_size, &pool_0,
                              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="9fdf6-656">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="9fdf6-656">nx_http_server_delete</span></span>

### <a name="delete-an-http-server-instance"></a><span data-ttu-id="9fdf6-657">HTTP 서버 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="9fdf6-657">Delete an HTTP Server instance</span></span>

<span data-ttu-id="9fdf6-658">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-658">**Prototype**</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="9fdf6-659">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-659">**Description**</span></span>

<span data-ttu-id="9fdf6-660">이 서비스는 이전에 만든 HTTP 서버 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-660">This service deletes a previously created HTTP Server instance.</span></span>

<span data-ttu-id="9fdf6-661">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-661">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-662">**http_server_ptr** HTTP 서버 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-662">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

<span data-ttu-id="9fdf6-663">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-663">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-664">**NX_SUCCESS** (0x00) HTTP 서버를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-664">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="9fdf6-665">NX_PTR_ERROR (0x07) 잘못된 HTTP 서버 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-665">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="9fdf6-666">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-666">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="9fdf6-667">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-667">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-668">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-668">Threads</span></span>

<span data-ttu-id="9fdf6-669">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-669">**Example**</span></span>

```c
/* Delete the HTTP Server instance called “my_server.” */
status = nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="9fdf6-670">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="9fdf6-670">nx_http_server_get_entity_content</span></span>

### <a name="retrieve-the-location-and-length-of-entity-data"></a><span data-ttu-id="9fdf6-671">엔터티 데이터의 위치 및 길이 검색</span><span class="sxs-lookup"><span data-stu-id="9fdf6-671">Retrieve the location and length of entity data</span></span>

<span data-ttu-id="9fdf6-672">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-672">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="9fdf6-673">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-673">**Description**</span></span>

<span data-ttu-id="9fdf6-674">이 서비스는 받은 클라이언트 메시지의 현재 다중 파트 엔터티 내의 데이터 시작 위치 및 경계 문자열이 포함되지 않는 데이터 길이를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-674">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="9fdf6-675">내부적으로 HTTP 서버는 여러 엔터티가 있는 메시지에 대해 동일한 클라이언트 데이터그램에서 이 함수를 다시 호출할 수 있도록 자체 오프셋을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-675">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="9fdf6-676">패킷 포인터를 클라이언트 메시지가 다중 패킷 데이터그램인 다음 패킷으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-676">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="9fdf6-677">이 서비스를 사용하려면 NX_HTTP_MULTIPART_ENABLE을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-677">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="9fdf6-678">자세한 내용은 *nx_http_server_get_entity_header* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-678">See *nx_http_server_get_entity_header* for more details.</span></span>

<span data-ttu-id="9fdf6-679">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-679">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-680">**server_ptr** HTTP 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-680">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="9fdf6-681">**packet_pptr** 패킷 포인터의 위치에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-681">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="9fdf6-682">애플리케이션에서 이 패킷을 해제하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-682">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="9fdf6-683">**available_offset** 패킷 선행 포인터에서 엔터티 데이터의 오프셋에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-683">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="9fdf6-684">**available_length** 엔터티 데이터의 길이에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-684">**available_length** Pointer to length of entity data</span></span>

<span data-ttu-id="9fdf6-685">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-685">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-686">**NX_SUCCESS** (0x00) 엔터티 콘텐츠의 크기와 위치를 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-686">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="9fdf6-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) HTTP 서버 내부 다중 파트 표식에 대한 콘텐츠가 이미 있음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="9fdf6-688">NX_HTTP_ERROR (0xE0) HTTP 서버 내부 오류</span><span class="sxs-lookup"><span data-stu-id="9fdf6-688">NX_HTTP_ERROR (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="9fdf6-689">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-689">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-690">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-690">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-691">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-691">Threads</span></span>

<span data-ttu-id="9fdf6-692">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-692">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

UINT         offset, length;
NX_PACKET    *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
the entity header to determine details about the multipart data. If
successful, it then calls this service to get the location of entity data: */
status = nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
                                          &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="9fdf6-693">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="9fdf6-693">nx_http_server_get_entity_header</span></span>

### <a name="retrieve-the-contents-of-entity-header"></a><span data-ttu-id="9fdf6-694">엔터티 헤더의 콘텐츠 검색</span><span class="sxs-lookup"><span data-stu-id="9fdf6-694">Retrieve the contents of entity header</span></span>

<span data-ttu-id="9fdf6-695">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-695">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);
```

<span data-ttu-id="9fdf6-696">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-696">**Description**</span></span>

<span data-ttu-id="9fdf6-697">이 서비스는 지정된 버퍼에서 엔터티 헤더를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-697">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="9fdf6-698">다중 엔터티 헤더가 있는 클라이언트 데이터그램에서 다음 다중 파트 엔터티를 찾도록 HTTP 서버에서 내부적으로 자체 포인터를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-698">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="9fdf6-699">패킷 포인터를 클라이언트 메시지가 다중 패킷 데이터그램인 다음 패킷으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-699">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="9fdf6-700">이 서비스를 사용하려면 NX_HTTP_MULTIPART_ENABLE을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-700">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="9fdf6-701">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-701">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-702">**server_ptr** HTTP 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-702">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="9fdf6-703">**packet_pptr** 패킷 포인터의 위치에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-703">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="9fdf6-704">애플리케이션에서 이 패킷을 해제하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-704">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="9fdf6-705">**entity_header_buffer** 엔터티 헤더를 저장하는 위치에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-705">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="9fdf6-706">**buffer_size** 입력 버퍼의 크기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-706">**buffer_size** Size of input buffer</span></span>

<span data-ttu-id="9fdf6-707">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-707">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-708">**NX_SUCCESS** (0x00) 엔터티 헤더를 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-708">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
- <span data-ttu-id="9fdf6-709">**NX_HTTP_NOT_FOUND (0xE6)** 엔터티 헤더 필드가 없음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-709">**NX_HTTP_NOT_FOUND (0xE6)** Entity header field not found</span></span>
- <span data-ttu-id="9fdf6-710">**NX_HTTP_TIMEOUT (0xE1)** 다중 패킷 클라이언트 메시지에 대한 다음 패킷을 받는 시간이 만료됨</span><span class="sxs-lookup"><span data-stu-id="9fdf6-710">**NX_HTTP_TIMEOUT (0xE1)** Time expired to receive next packet for multipacket client message</span></span> 
- <span data-ttu-id="9fdf6-711">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-711">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-712">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-712">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="9fdf6-713">NX_HTTP_ERROR (0xE0) 내부 HTTP 오류</span><span class="sxs-lookup"><span data-stu-id="9fdf6-713">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>

<span data-ttu-id="9fdf6-714">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-714">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-715">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-715">Threads</span></span>

<span data-ttu-id="9fdf6-716">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-716">**Example**</span></span>

```c
/* my_request_notify* is the application request notify callback registered with
the HTTP server in *nx_http_server_create,* creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

NX_PACKET     *sresp_packet_ptr;
UINT          offset, length;**
NX_PACKET     *response_pkt;
UCHAR         buffer[1440];

/* Process multipart data. */
if(request_type == NX_HTTP_SERVER_POST_REQUEST)
{

    /* Get the content header. */
    while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                          sizeof(buffer)) == NX_SUCCESS)
    {

        /* Header obtained successfully. Get the content data location. */
        while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                               &length) == NX_SUCCESS)
        {

            /* Write content data to buffer. */
            nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
            buffer[length] = 0;
        }
    }
    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
             &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
             "Server: NetX HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
                                              NX_SUCCESS)
        {
            nx_packet_release(response_pkt);
        }
    }
}
Else
{

        /* Indicate we have not processed the response to client yet.*/        
        return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="9fdf6-717">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="9fdf6-717">nx_http_server_gmt_callback_set</span></span>

### <a name="set-the-callback-to-obtain-gmt-date-and-time"></a><span data-ttu-id="9fdf6-718">GMT 날짜 및 시간을 가져오는 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="9fdf6-718">Set the callback to obtain GMT date and time</span></span>

<span data-ttu-id="9fdf6-719">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-719">**Prototype**</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="9fdf6-720">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-720">**Description**</span></span>

<span data-ttu-id="9fdf6-721">이 서비스는 이전에 만든 HTTP 서버에서 GMT 날짜 및 시간을 가져오는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-721">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="9fdf6-722">이 서비스는 HTTP 서버에서 헤더를 클라이언트에 대한 HTTP 서버 응답에 만들 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-722">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

<span data-ttu-id="9fdf6-723">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-723">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-724">**server_ptr** HTTP 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-724">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="9fdf6-725">**gmt_get** GMT 콜백에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-725">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="9fdf6-726">**date** 검색된 날짜에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-726">**date** Pointer to the date retrieved</span></span>

<span data-ttu-id="9fdf6-727">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-727">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-728">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-728">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="9fdf6-729">NX_PTR_ERROR (0x07) 잘못된 패킷 또는 매개 변수 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-729">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

<span data-ttu-id="9fdf6-730">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-730">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-731">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-731">Threads</span></span>

<span data-ttu-id="9fdf6-732">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-732">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the GMT
retrieve callback: */

status = nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="9fdf6-733">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="9fdf6-733">nx_http_server_invalid_userpassword_notify_set</span></span>

### <a name="set-the-callback-to-to-handle-invalid-userpassword"></a><span data-ttu-id="9fdf6-734">잘못된 사용자/암호를 처리하는 콜백 설정</span><span class="sxs-lookup"><span data-stu-id="9fdf6-734">Set the callback to to handle invalid user/password</span></span>

<span data-ttu-id="9fdf6-735">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-735">**Prototype**</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*invalid_username_password_callback)
     (CHAR *resource,
     ULONG client_address,
     UINT request_type));
```

<span data-ttu-id="9fdf6-736">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-736">**Description**</span></span>

<span data-ttu-id="9fdf6-737">이 서비스는 다이제스트 또는 기본 인증을 통해 클라이언트 GET, PUT 또는 DELETE 요청에서 잘못된 사용자 이름 및 암호를 받을 때 호출되는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-737">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="9fdf6-738">HTTP 서버는 이전에 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-738">The HTTP server must be previously created.</span></span>

<span data-ttu-id="9fdf6-739">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-739">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-740">**server_ptr** HTTP 서버에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-740">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="9fdf6-741">**invalid_username_password_callback** 잘못된 사용자/전달 콜백에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-741">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="9fdf6-742">**resource** 클라이언트에서 지정한 리소스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-742">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="9fdf6-743">**client_address** 클라이언트 주소</span><span class="sxs-lookup"><span data-stu-id="9fdf6-743">**client_address** Client address</span></span>
- <span data-ttu-id="9fdf6-744">**request_type** 클라이언트 요청 유형 표시</span><span class="sxs-lookup"><span data-stu-id="9fdf6-744">**request_type** Indicates client request type.</span></span> <span data-ttu-id="9fdf6-745">다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-745">May be:</span></span>
  - <span data-ttu-id="9fdf6-746">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="9fdf6-746">NX_HTTP_SERVER_GET_REQUEST</span></span>
  - <span data-ttu-id="9fdf6-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="9fdf6-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span></span>
  - <span data-ttu-id="9fdf6-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="9fdf6-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span></span>

<span data-ttu-id="9fdf6-749">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-749">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-750">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-750">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="9fdf6-751">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-751">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-752">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-752">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-753">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-753">Threads</span></span>

<span data-ttu-id="9fdf6-754">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-754">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                        ULONG client_address,
                                        UINT request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the invalid
username password callback: */

status = nx_http_server_gmt_callback_set(&my_server,
                                        invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="9fdf6-755">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="9fdf6-755">nx_http_server_mime_maps_additional_set</span></span>

### <a name="set-additional-mime-maps-for-html"></a><span data-ttu-id="9fdf6-756">HTML에 대한 추가 MIME 맵 설정</span><span class="sxs-lookup"><span data-stu-id="9fdf6-756">Set additional MIME maps for HTML</span></span> 

<span data-ttu-id="9fdf6-757">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-757">**Prototype**</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
     NX_HTTP_SERVER *server_ptr,
     NX_HTTP_SERVER_MIME_MAP *mime_maps,
     UINT mime_maps_num);
```

<span data-ttu-id="9fdf6-758">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-758">**Description**</span></span>

<span data-ttu-id="9fdf6-759">이 서비스를 통해 HTTP 애플리케이션 개발자는 NetX HTTP 서버에서 제공하는 기본 MIME 형식에서 추가 MIME 형식을 추가할 수 있습니다(정의된 형식 목록은 *nx_http_server_get_type* 참조).</span><span class="sxs-lookup"><span data-stu-id="9fdf6-759">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="9fdf6-760">클라이언트 요청(예: GET 요청)을 받으면 HTTP 서버에서 우선적으로 추가 MIME 맵 세트를 사용하여 HTTP 헤더에서 요청된 파일 형식을 구문 분석하고, 일치하는 항목이 없는 경우 HTTP 서버의 기본 MIME 맵에서 일치 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-760">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="9fdf6-761">일치하는 항목이 없으면 MIME 형식은 기본적으로 "텍스트/일반"으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-761">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="9fdf6-762">요청 알림 함수가 HTTP 서버에 등록된 경우 요청 알림 콜백에서 *nx_http_server_type_get* 을 호출하여 파일 형식을 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-762">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_get* to parse the file type.</span></span>

<span data-ttu-id="9fdf6-763">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-763">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-764">**server_ptr** HTTP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-764">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="9fdf6-765">**mime_maps** MIME 맵 배열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-765">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="9fdf6-766">**mime_map_num** 배열의 MIME 맵 수</span><span class="sxs-lookup"><span data-stu-id="9fdf6-766">**mime_map_num** Number of MIME maps in array</span></span>

<span data-ttu-id="9fdf6-767">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-767">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-768">**NX_SUCCESS** (0x00) HTTP 서버 MIME 맵을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-768">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="9fdf6-769">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-769">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-770">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-770">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-771">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-771">Initialization, Threads</span></span>

<span data-ttu-id="9fdf6-772">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-772">**Example**</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_http_server_mime_maps_additional_set(&my_server,
                                                &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="9fdf6-773">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="9fdf6-773">nx_http_server_packet_content_find</span></span>

### <a name="extract-content-length-and-set-pointer-to-start-of-data"></a><span data-ttu-id="9fdf6-774">콘텐츠 길이 추출 및 데이터 시작에 대한 포인터 설정</span><span class="sxs-lookup"><span data-stu-id="9fdf6-774">Extract content length and set pointer to start of data</span></span>

<span data-ttu-id="9fdf6-775">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-775">**Prototype**</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_ptr,
                                       UINT *content_length);
```

<span data-ttu-id="9fdf6-776">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-776">**Description**</span></span>

<span data-ttu-id="9fdf6-777">이 서비스는 HTTP 헤더에서 콘텐츠 길이를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-777">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="9fdf6-778">또한 제공된 패킷을 다음과 같이 업데이트합니다. 패킷 선행 포인터(쓸 패킷 버퍼의 시작 위치)가 HTTP 헤더를 방금 전달한 HTTP 콘텐츠(데이터)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-778">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="9fdf6-779">현재 패킷에서 콘텐츠의 시작 위치를 찾을 수 없는 경우 함수에서 NX_HTTP_SERVER_TIMEOUT_RECEIVE 대기 옵션을 사용하여 다음 패킷을 받을 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-779">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="9fdf6-780">이 서비스는 엔터티 헤더 앞의 선행 포인터를 수정하므로 *nx_http_server_get_entity_header()* 를 호출하기 전에 호출하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-780">Note this should not be called before calling *nx_http_server_get_entity_header()* because it modifies the prepend pointer past the entity header.</span></span>

<span data-ttu-id="9fdf6-781">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-781">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-782">**server_ptr** HTTP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-782">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="9fdf6-783">**packet_ptr** 업데이트된 선행 포인터를 사용하여 패킷을 반환하는 패킷 포인터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-783">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="9fdf6-784">**content_length** 추출된 content_length에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-784">**content_length** Pointer to extracted content_length</span></span>

<span data-ttu-id="9fdf6-785">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-785">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-786">**NX_SUCCESS** (0x00) HTTP 콘텐츠 길이가 있고 패킷을 성공적으로 업데이트함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-786">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="9fdf6-787">**NX_HTTP_TIMEOUT** (0xE1) 다음 패킷을 기다리는 시간이 만료됨</span><span class="sxs-lookup"><span data-stu-id="9fdf6-787">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="9fdf6-788">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-788">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-789">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-789">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-790">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-790">Threads</span></span>

<span data-ttu-id="9fdf6-791">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-791">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function 
registere with the HTTP server. */

UINT content_length;

status = nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                           &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="9fdf6-792">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="9fdf6-792">nx_http_server_packet_get</span></span>

### <a name="receive-the-next-http-packet"></a><span data-ttu-id="9fdf6-793">다음 HTTP 패킷 받기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-793">Receive the next HTTP packet</span></span>

<span data-ttu-id="9fdf6-794">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-794">**Prototype**</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

<span data-ttu-id="9fdf6-795">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-795">**Description**</span></span>

<span data-ttu-id="9fdf6-796">이 서비스는 HTTP 서버 소켓에서 받은 다음 패킷을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-796">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="9fdf6-797">패킷 수신 대기 옵션은 NX_HTTP_SERVER_TIMEOUT_RECEIVE입니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-797">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="9fdf6-798">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-798">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-799">**server_ptr** HTTP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-799">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="9fdf6-800">**packet_ptr** 받은 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-800">**packet_ptr** Pointer to received packet</span></span>

<span data-ttu-id="9fdf6-801">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-801">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-802">**NX_SUCCESS** (0x00) 다음 HTTP 패킷을 성공적으로 받음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-802">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="9fdf6-803">**NX_HTTP_TIMEOUT** (0xE1) 다음 패킷을 기다리는 시간이 만료됨</span><span class="sxs-lookup"><span data-stu-id="9fdf6-803">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="9fdf6-804">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-804">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-805">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-805">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-806">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-806">Threads</span></span>

<span data-ttu-id="9fdf6-807">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-807">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="9fdf6-808">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="9fdf6-808">nx_http_server_param_get</span></span>

### <a name="get-parameter-from-the-request"></a><span data-ttu-id="9fdf6-809">요청에서 매개 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-809">Get parameter from the request</span></span>

<span data-ttu-id="9fdf6-810">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-810">**Prototype**</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                             UINT param_number, CHAR *param_ptr,
                             UINT max_param_size);
```

<span data-ttu-id="9fdf6-811">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-811">**Description**</span></span>

<span data-ttu-id="9fdf6-812">이 서비스는 제공된 요청 패킷에서 지정된 HTTP URL 매개 변수를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-812">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="9fdf6-813">요청된 HTTP 매개 변수가 없는 경우 이 루틴에서 NX_HTTP_NOT_FOUND 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-813">If the requested HTTP parameter is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="9fdf6-814">이 루틴은 HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-814">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="9fdf6-815">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-815">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-816">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-816">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="9fdf6-817">애플리케이션에서 이 패킷을 해제하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-817">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="9fdf6-818">**param_number** 매개 변수 목록에서 왼쪽에서 오른쪽으로 0에서 시작하는 매개 변수의 논리적 번호</span><span class="sxs-lookup"><span data-stu-id="9fdf6-818">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="9fdf6-819">**param_ptr** 매개 변수를 복사하는 대상 영역</span><span class="sxs-lookup"><span data-stu-id="9fdf6-819">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="9fdf6-820">**max_param_size** 매개 변수 대상 영역의 최대 크기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-820">**max_param_size** Maximum size of the parameter destination area.</span></span>

<span data-ttu-id="9fdf6-821">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-821">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-822">**NX_SUCCESS** (0x00) HTTP 서버 매개 변수를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="9fdf6-822">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="9fdf6-823">**NX_HTTP_NOT_FOUND** (0xE6) 지정된 매개 변수가 없음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-823">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
- <span data-ttu-id="9fdf6-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) 요청 매개 변수가 제대로 종료되지 않음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
- <span data-ttu-id="9fdf6-825">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-825">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-826">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="9fdf6-827">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-827">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-828">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-828">Threads</span></span>

<span data-ttu-id="9fdf6-829">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-829">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first parameter of the HTTP Client request. */

status = nx_http_server_param_get(request_packet_ptr, 0, param_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="9fdf6-830">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="9fdf6-830">nx_http_server_query_get</span></span>

### <a name="get-query-from-the-request"></a><span data-ttu-id="9fdf6-831">요청에서 쿼리 가져오기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-831">Get query from the request</span></span>

<span data-ttu-id="9fdf6-832">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-832">**Prototype**</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                             CHAR *query_ptr, UINT max_query_size);
```

<span data-ttu-id="9fdf6-833">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-833">**Description**</span></span>

<span data-ttu-id="9fdf6-834">이 서비스는 제공된 요청 패킷에서 지정된 HTTP URL 쿼리를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-834">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="9fdf6-835">요청된 HTTP 쿼리가 없는 경우 이 루틴에서 NX_HTTP_NOT_FOUND 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-835">If the requested HTTP query is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="9fdf6-836">이 루틴은 HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-836">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="9fdf6-837">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-837">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-838">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-838">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="9fdf6-839">애플리케이션에서 이 패킷을 해제하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-839">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="9fdf6-840">**query_number** 쿼리 목록에서 왼쪽에서 오른쪽으로 0에서 시작하는 매개 변수의 논리적 번호</span><span class="sxs-lookup"><span data-stu-id="9fdf6-840">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="9fdf6-841">**query_ptr** 쿼리를 복사하는 대상 영역</span><span class="sxs-lookup"><span data-stu-id="9fdf6-841">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="9fdf6-842">**max_query_size** 쿼리 대상 영역의 최대 크기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-842">**max_query_size** Maximum size of the query destination area.</span></span>

<span data-ttu-id="9fdf6-843">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-843">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-844">**NX_SUCCESS** (0x00) HTTP 서버 쿼리를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="9fdf6-844">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="9fdf6-845">**NX_HTTP_FAILED** (0xE2) 쿼리 크기가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-845">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
- <span data-ttu-id="9fdf6-846">**NX_HTTP_NOT_FOUND** (0xE6) 지정된 쿼리가 없음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-846">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
- <span data-ttu-id="9fdf6-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) 쿼리가 클라이언트 요청에 없음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
- <span data-ttu-id="9fdf6-848">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-848">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-849">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-849">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="9fdf6-850">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-850">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-851">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-851">Threads</span></span>

<span data-ttu-id="9fdf6-852">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-852">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first query of the HTTP Client request. */
status = nx_http_server_query_get(request_packet_ptr, 0, query_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
in “query_destination.” */
```

##   
<span data-ttu-id="9fdf6-853">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="9fdf6-853">nx_http_server_start</span></span>

### <a name="start-the-http-server"></a><span data-ttu-id="9fdf6-854">HTTP 서버 시작</span><span class="sxs-lookup"><span data-stu-id="9fdf6-854">Start the HTTP Server</span></span>

<span data-ttu-id="9fdf6-855">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-855">**Prototype**</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="9fdf6-856">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-856">**Description**</span></span>

<span data-ttu-id="9fdf6-857">이 서비스는 이전에 만든 HTTP 서버 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-857">This service starts the previously create HTTP Server instance.</span></span>

<span data-ttu-id="9fdf6-858">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-858">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-859">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-859">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="9fdf6-860">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-860">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-861">**NX_SUCCESS** (0x00) HTTP 서버를 성공적으로 시작함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-861">**NX_SUCCESS** (0x00) Successful HTTP Server start</span></span>
- <span data-ttu-id="9fdf6-862">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-862">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-863">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-863">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-864">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-864">Initialization, Threads</span></span>

<span data-ttu-id="9fdf6-865">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-865">**Example**</span></span>

```c
/* Start the HTTP Server instance “my_server.” */
status = nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="9fdf6-866">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="9fdf6-866">nx_http_server_stop</span></span>

### <a name="stop-the-http-server"></a><span data-ttu-id="9fdf6-867">HTTP 서버 중지</span><span class="sxs-lookup"><span data-stu-id="9fdf6-867">Stop the HTTP Server</span></span>

<span data-ttu-id="9fdf6-868">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-868">**Prototype**</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="9fdf6-869">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-869">**Description**</span></span>

<span data-ttu-id="9fdf6-870">이 서비스는 이전에 만든 HTTP 서버 인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-870">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="9fdf6-871">이 루틴은 HTTP 서버 인스턴스를 삭제하기 전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-871">This routine should be called prior to deleting an HTTP Server instance.</span></span>

<span data-ttu-id="9fdf6-872">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-872">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-873">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-873">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="9fdf6-874">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-874">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-875">**NX_SUCCESS** (0x00) HTTP 서버를 성공적으로 중지함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-875">**NX_SUCCESS** (0x00) Successful HTTP Server stop</span></span>
- <span data-ttu-id="9fdf6-876">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-876">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-877">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="9fdf6-877">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="9fdf6-878">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-878">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-879">스레드</span><span class="sxs-lookup"><span data-stu-id="9fdf6-879">Threads</span></span>

<span data-ttu-id="9fdf6-880">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-880">**Example**</span></span>

```c
/* Stop the HTTP Server instance “my_server.” */

status = nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="9fdf6-881">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="9fdf6-881">nx_http_server_type_get</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="9fdf6-882">클라이언트 HTTP 요청에서 파일 형식 추출</span><span class="sxs-lookup"><span data-stu-id="9fdf6-882">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="9fdf6-883">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-883">**Prototype**</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                            CHAR *name, CHAR *http_type_string);
```

<span data-ttu-id="9fdf6-884">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-884">**Description**</span></span>

<span data-ttu-id="9fdf6-885">이 서비스는 *http_type_string* 버퍼에서 HTTP 요청 유형을 추출하고, *name* 입력 버퍼(일반적으로 URL)의 반환 값에서 해당 길이를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-885">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="9fdf6-886">MIME 맵이 없는 경우 기본적으로 "텍스트/일반" 형식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-886">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="9fdf6-887">그렇지 않으면 추출된 형식을 HTTP 서버 기본 MIME 맵과 비교하여 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-887">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="9fdf6-888">NetX HTTP 서버의 기본 MIME 맵은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-888">The default MIME maps in NetX HTTP Server are:</span></span>

- <span data-ttu-id="9fdf6-889">html text/html</span><span class="sxs-lookup"><span data-stu-id="9fdf6-889">html text/html</span></span>
- <span data-ttu-id="9fdf6-890">htm text/html</span><span class="sxs-lookup"><span data-stu-id="9fdf6-890">htm text/html</span></span>
- <span data-ttu-id="9fdf6-891">txt text/plain</span><span class="sxs-lookup"><span data-stu-id="9fdf6-891">txt text/plain</span></span>
- <span data-ttu-id="9fdf6-892">gif image/gif</span><span class="sxs-lookup"><span data-stu-id="9fdf6-892">gif image/gif</span></span>
- <span data-ttu-id="9fdf6-893">jpg image/jpeg</span><span class="sxs-lookup"><span data-stu-id="9fdf6-893">jpg image/jpeg</span></span>
- <span data-ttu-id="9fdf6-894">ico image/x-icon</span><span class="sxs-lookup"><span data-stu-id="9fdf6-894">ico image/x-icon</span></span>

<span data-ttu-id="9fdf6-895">제공되면 사용자 정의 추가 MIME 맵 세트도 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-895">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="9fdf6-896">사용자 정의 맵에 대한 자세한 내용은 *nx_http_server_mime_maps_addtional_set()* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-896">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="9fdf6-897">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-897">This service is deprecated.</span></span> <span data-ttu-id="9fdf6-898">개발자는 *nx_http_server_type_get_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-898">Developers are encouraged to migrate to *nx_http_server_type_get_extended().*</span></span>

<span data-ttu-id="9fdf6-899">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-899">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-900">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-900">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="9fdf6-901">**name** 검색하는 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-901">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="9fdf6-902">**http_type_string**(추출된 HTML 형식에 대한 포인터)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-902">**http_type_string** (Pointer to extracted HTML type)</span></span>

<span data-ttu-id="9fdf6-903">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-903">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-904">**문자열 길이(바이트)** 0이 아닌 값은 성공</span><span class="sxs-lookup"><span data-stu-id="9fdf6-904">**Length of string in bytes** Non zero value is success</span></span>
- <span data-ttu-id="9fdf6-905">**0은 오류를 나타냄**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-905">**Zero indicates error**</span></span>

<span data-ttu-id="9fdf6-906">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-906">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-907">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="9fdf6-907">Application</span></span>

<span data-ttu-id="9fdf6-908">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-908">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="9fdf6-909">자세한 예제는</span><span class="sxs-lookup"><span data-stu-id="9fdf6-909">For a more detailed example, see the description for</span></span>

<span data-ttu-id="9fdf6-910">*nx_http_server_callback_generate_response_header* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-910">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="9fdf6-911">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="9fdf6-911">nx_http_server_type_get_extended</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="9fdf6-912">클라이언트 HTTP 요청에서 파일 형식 추출</span><span class="sxs-lookup"><span data-stu-id="9fdf6-912">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="9fdf6-913">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-913">**Prototype**</span></span>

```c
UINT nx_http_server_type_get_extended(
     NX_HTTP_SERVER *http_server_ptr,
     CHAR *name, CHAR *http_type_string,
     UINT http_type_string_max_size);
```

<span data-ttu-id="9fdf6-914">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-914">**Description**</span></span>

<span data-ttu-id="9fdf6-915">이 서비스는 *http_type_string* 버퍼에서 HTTP 요청 유형을 추출하고, *name* 입력 버퍼(일반적으로 URL)의 반환 값에서 해당 길이를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-915">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="9fdf6-916">MIME 맵이 없는 경우 기본적으로 "텍스트/일반" 형식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-916">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="9fdf6-917">그렇지 않으면 추출된 형식을 HTTP 서버 기본 MIME 맵과 비교하여 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-917">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="9fdf6-918">NetX Duo HTTP 서버의 기본 MIME 맵은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-918">The default MIME maps in NetX Duo HTTP Server are:</span></span>

- <span data-ttu-id="9fdf6-919">html text/html</span><span class="sxs-lookup"><span data-stu-id="9fdf6-919">html text/html</span></span>
- <span data-ttu-id="9fdf6-920">htm text/html</span><span class="sxs-lookup"><span data-stu-id="9fdf6-920">htm text/html</span></span>
- <span data-ttu-id="9fdf6-921">txt text/plain</span><span class="sxs-lookup"><span data-stu-id="9fdf6-921">txt text/plain</span></span>
- <span data-ttu-id="9fdf6-922">gif image/gif</span><span class="sxs-lookup"><span data-stu-id="9fdf6-922">gif image/gif</span></span>
- <span data-ttu-id="9fdf6-923">jpg image/jpeg</span><span class="sxs-lookup"><span data-stu-id="9fdf6-923">jpg image/jpeg</span></span>
- <span data-ttu-id="9fdf6-924">ico image/x-icon</span><span class="sxs-lookup"><span data-stu-id="9fdf6-924">ico image/x-icon</span></span>

<span data-ttu-id="9fdf6-925">제공되면 사용자 정의 추가 MIME 맵 세트도 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-925">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="9fdf6-926">사용자 정의 맵에 대한 자세한 내용은 *nx_http_server_mime_maps_addtional_set()* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-926">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="9fdf6-927">이 서비스는 *nx_http_server_type_get()* 을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-927">This service replaces *nx_http_server_type_get().*</span></span> <span data-ttu-id="9fdf6-928">이 버전은 추가 길이 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-928">This version supplies additional length information.</span></span>

<span data-ttu-id="9fdf6-929">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-929">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-930">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-930">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="9fdf6-931">**name** 검색하는 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-931">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="9fdf6-932">**name_length** 검색하는 버퍼의 길이</span><span class="sxs-lookup"><span data-stu-id="9fdf6-932">**name_length** Length of buffer to search</span></span>
- <span data-ttu-id="9fdf6-933">**http_type_string**(추출된 HTML 형식에 대한 포인터)</span><span class="sxs-lookup"><span data-stu-id="9fdf6-933">**http_type_string** (Pointer to extracted HTML type)</span></span>
- <span data-ttu-id="9fdf6-934">**http_type_string_max_size**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-934">**http_type_string_max_size**</span></span>

<span data-ttu-id="9fdf6-935">*http_type_string* 버퍼의 크기</span><span class="sxs-lookup"><span data-stu-id="9fdf6-935">Size of the *http_type_string* buffer</span></span>

<span data-ttu-id="9fdf6-936">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-936">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-937">**문자열 길이(바이트)** 0이 아닌 값은 성공</span><span class="sxs-lookup"><span data-stu-id="9fdf6-937">**Length of string in bytes** Non zero value is success</span></span><br /><span data-ttu-id="9fdf6-938">0은 오류를 나타냄</span><span class="sxs-lookup"><span data-stu-id="9fdf6-938">Zero indicates error</span></span>

<span data-ttu-id="9fdf6-939">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-939">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-940">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="9fdf6-940">Application</span></span>

<span data-ttu-id="9fdf6-941">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-941">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
       my_server.nx_http_server_request_resource, &resource_length,
       sizeof(my_server.nx_http_server_request_resource) - 1))
    {
        return;
    }
/* Extract the HTTP type. */
string_length = nx_http_server_type_get_extended(&my_server,
                my_server.nx_http_server_request_resource, resource_length,
                temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="9fdf6-942">자세한 예제는</span><span class="sxs-lookup"><span data-stu-id="9fdf6-942">For a more detailed example, see the description for</span></span>

<span data-ttu-id="9fdf6-943">*nx_http_server_callback_generate_response_header* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-943">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="9fdf6-944">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="9fdf6-944">nx_http_server_digest_authenticate_notify_set</span></span>

### <a name="set-digest-authenticate-callback-function"></a><span data-ttu-id="9fdf6-945">다이제스트 인증 콜백 함수 설정</span><span class="sxs-lookup"><span data-stu-id="9fdf6-945">Set digest authenticate callback function</span></span>

<span data-ttu-id="9fdf6-946">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-946">**Prototype**</span></span>

```c
UINT nx_http_server_digest_authenticate_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                         CHAR *name_ptr,
                                         CHAR *realm_ptr,
                                         CHAR *password_ptr,
                                         CHAR *method,
                                         CHAR *authorization_uri,
                                         CHAR *authorization_nc,
                                         CHAR *authorization_cnonce
                                         ));
```

<span data-ttu-id="9fdf6-947">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-947">**Description**</span></span>

<span data-ttu-id="9fdf6-948">이 서비스는 다이제스트 인증을 수행할 때 호출되는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-948">This service sets the callback invoked when digest authenticate is performed.</span></span>

<span data-ttu-id="9fdf6-949">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-949">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-950">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-950">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="9fdf6-951">**digest_authenticate_callback** 다이제스트 인증 콜백에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-951">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

<span data-ttu-id="9fdf6-952">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-952">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-953">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-953">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="9fdf6-954">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-954">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9fdf6-955">NX_NOT_SUPPORTED (0x4B) 다이제스트 인증을 사용하도록 설정되지 않음</span><span class="sxs-lookup"><span data-stu-id="9fdf6-955">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

<span data-ttu-id="9fdf6-956">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-956">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-957">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="9fdf6-957">Application</span></span>

<span data-ttu-id="9fdf6-958">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-958">**Example**</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                 CHAR *realm_ptr, CHAR *password_ptr,
                                 CHAR *method,CHAR *authorization_uri,
                                 CHAR *authorization_nc,
                                 CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set the
digest authenticate callback: */

status = nx_http_server_digest_authenticate_notify_set (&my_server,
                                                       digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="9fdf6-959">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="9fdf6-959">nx_http_server_authentication_check_set</span></span>

### <a name="set-authentication-checking-callback-function"></a><span data-ttu-id="9fdf6-960">인증 확인 콜백 함수 설정</span><span class="sxs-lookup"><span data-stu-id="9fdf6-960">Set authentication checking callback function</span></span>

<span data-ttu-id="9fdf6-961">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-961">**Prototype**</span></span>

```c
UINT nx_http_server_authentication_check_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*authentication_check_extended)(
                                          NX_HTTP_SERVER *server_ptr,
                                          UINT request_type,
                                          CHAR *resource,
                                          CHAR **name,
                                          UINT *name_length,
                                          CHAR **password,
                                          UINT *password_length,
                                          CHAR **realm,
                                          UINT *realm_length
                                          ));
```

<span data-ttu-id="9fdf6-962">**설명**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-962">**Description**</span></span>

<span data-ttu-id="9fdf6-963">이 서비스는 인증 확인 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fdf6-963">This service sets the callback function of authentication checking.</span></span>

<span data-ttu-id="9fdf6-964">**입력 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-964">**Input Parameters**</span></span>

- <span data-ttu-id="9fdf6-965">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-965">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="9fdf6-966">**authentication_check_extended** 애플리케이션의 인증 확인에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="9fdf6-966">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

<span data-ttu-id="9fdf6-967">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-967">**Return Values**</span></span>

- <span data-ttu-id="9fdf6-968">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="9fdf6-968">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="9fdf6-969">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="9fdf6-969">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="9fdf6-970">**허용되는 원본**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-970">**Allowed From**</span></span>

<span data-ttu-id="9fdf6-971">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="9fdf6-971">Application</span></span>

<span data-ttu-id="9fdf6-972">**예제**</span><span class="sxs-lookup"><span data-stu-id="9fdf6-972">**Example**</span></span>

```c
static UINT authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, UINT *name_length,
                                         CHAR **password, 
                                         UINT *password_length,
                                         CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */

    *name = "name";
    *password = "password";
    *realm = "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set 
the authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                        authentication_check_extended);
```