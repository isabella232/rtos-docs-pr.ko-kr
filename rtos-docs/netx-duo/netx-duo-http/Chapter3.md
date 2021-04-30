---
title: 3장 - Azure RTOS NetX Duo HTTP 서비스 설명
description: 이 장에는 동일한 서비스에 해당하는 ‘NetX’(IPv4만 해당)가 함께 쌍을 이루는 경우를 제외하고 모든 Azure RTOS NetX Duo HTTP 서비스(아래 참조)에 대한 설명이 알파벳 순서로 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 703071cd5a1d0677a3e995fccfe35d8b1dbbd9f3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810783"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a><span data-ttu-id="f6ddf-103">3장 - Azure RTOS NetX Duo HTTP 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="f6ddf-103">Chapter 3 - Description of Azure RTOS NetX Duo HTTP Services</span></span>

<span data-ttu-id="f6ddf-104">이 장에는 동일한 서비스에 해당하는 ‘NetX’(IPv4만 해당)가 함께 쌍을 이루는 경우를 제외하고 모든 Azure RTOS NetX Duo HTTP 서비스(아래 참조)에 대한 설명이 알파벳 순서로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-104">This chapter contains a description of all Azure RTOS NetX Duo HTTP services (listed below) in alphabetical order except for the ‘NetX’ (IPv4 only) equivalent of the same service are paired together).</span></span>

<span data-ttu-id="f6ddf-105">다음 API 설명의 “반환 값” 섹션에서 BOLD로 표시된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의에 영향을 받지 않으며, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-105">In the “Return Values” section in the following API descriptions, values in BOLD are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="f6ddf-106">**HTTP 클라이언트 서비스:**</span><span class="sxs-lookup"><span data-stu-id="f6ddf-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="f6ddf-107">**nx_http_client_create** *HTTP 클라이언트 인스턴스를 만듭니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-107">**nx_http_client_create** *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="f6ddf-108">**nx_http_client_delete** *HTTP 클라이언트 인스턴스를 삭제합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-108">**nx_http_client_delete** *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="f6ddf-109">**nx_http_client_get_start** *HTTP GET 요청을 시작합니다(IPv4만 해당).*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-109">**nx_http_client_get_start** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="f6ddf-110">**nx_http_client_get_start_extended** *HTTP GET 요청을 시작합니다(IPv4만 해당).*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-110">**nx_http_client_get_start_extended** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="f6ddf-111">**nxd_http_client_get_start** *HTTP GET 요청을 시작합니다(IPv4 또는 IPv6).*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-111">**nxd_http_client_get_start** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="f6ddf-112">**nxd_http_client_get_start_extended** *HTTP GET 요청을 시작합니다(IPv4 또는 IPv6).*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-112">**nxd_http_client_get_start_extended** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="f6ddf-113">**nx_http_client_get_packet** *다음 리소스 데이터 패킷을 가져옵니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-113">**nx_http_client_get_packet** *Get next resource data packet*</span></span>
- <span data-ttu-id="f6ddf-114">**nx_http_client_put_start** *HTTP PUT 요청을 시작합니다(IPv4만 해당).*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-114">**nx_http_client_put_start** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="f6ddf-115">**nx_http_client_put_start_extended** *HTTP PUT 요청을 시작합니다(IPv4만 해당).*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-115">**nx_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="f6ddf-116">**nxd_http_client_put_start** *HTTP PUT 요청을 시작합니다(IPv4 또는 IPv6).*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-116">**nxd_http_client_put_start** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="f6ddf-117">**nxd_http_client_put_start_extended** *HTTP PUT 요청을 시작합니다(IPv4 또는 IPv6).*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-117">**nxd_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="f6ddf-118">**nx_http_client_put_packet** *다음 리소스 데이터 패킷을 전송합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-118">**nx_http_client_put_packet** *Send next resource data packet*</span></span>
- <span data-ttu-id="f6ddf-119">**nx_http_client_set_connect_port** *HTTP 서버에 연결하도록 포트를 변경합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-119">**nx_http_client_set_connect_port** *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="f6ddf-120">**HTTP 서버 서비스:**</span><span class="sxs-lookup"><span data-stu-id="f6ddf-120">**HTTP server services:**</span></span>

- <span data-ttu-id="f6ddf-121">**nx_http_server_cache_info_callback_set** *지정된 URL의 기간 및 마지막 수정 날짜를 검색하도록 콜백을 설정합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-121">**nx_http_server_cache_info_callback_set** *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="f6ddf-122">**nx_http_server_callback_data_send** *콜백 함수에서 HTTP 데이터를 보냅니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-122">**nx_http_server_callback_data_send** *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="f6ddf-123">**nx_http_server_callback_generate_response_header** *콜백 함수에 응답 헤더를 만듭니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-123">**nx_http_server_callback_generate_response_header** *Create response header in callback functions*</span></span>
- <span data-ttu-id="f6ddf-124">**nx_http_server_callback_generate_response_header_extended** *콜백 함수에 응답 헤더를 만듭니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-124">**nx_http_server_callback_generate_response_header_extended** *Create response header in callback functions*</span></span>
- <span data-ttu-id="f6ddf-125">**nx_http_server_callback_packet_send** *HTTP 콜백에서 HTTP 패킷을 보냅니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-125">**nx_http_server_callback_packet_send** *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="f6ddf-126">**nx_http_server_callback_response_send** *콜백 함수에서 응답을 보냅니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-126">**nx_http_server_callback_response_send** *Send response from callback function*</span></span>
- <span data-ttu-id="f6ddf-127">**nx_http_server_callback_response_send_extended** *콜백 함수에서 응답을 보냅니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-127">**nx_http_server_callback_response_send_extended** *Send response from callback function*</span></span>
- <span data-ttu-id="f6ddf-128">**nx_http_server_content_get** *요청에서 콘텐츠를 가져옵니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-128">**nx_http_server_content_get** *Get content from the request*</span></span>
- <span data-ttu-id="f6ddf-129">**nx_http_server_content_get_extended** *요청에서 콘텐츠를 가져옵니다. 비어 있는(콘텐츠 길이가 0인) 요청을 지원합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-129">**nx_http_server_content_get_extended** *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="f6ddf-130">**nx_http_server_content_length_get** *요청에서 콘텐츠 길이를 가져옵니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-130">**nx_http_server_content_length_get** *Get length of content in the request*</span></span>
- <span data-ttu-id="f6ddf-131">**nx_http_server_content_length_get_extended** *요청에서 콘텐츠 길이를 가져옵니다. 비어 있는(콘텐츠 길이가 0인) 요청을 지원합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-131">**nx_http_server_content_length_get_extended** *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="f6ddf-132">**nx_http_server_create** *HTTP 서버 인스턴스를 만듭니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-132">**nx_http_server_create** *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="f6ddf-133">**nx_http_server_delete** *HTTP 서버 인스턴스를 삭제합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-133">**nx_http_server_delete** \* Delete an HTTP Server instance\*</span></span>
- <span data-ttu-id="f6ddf-134">**nx_http_server_get_entity_content** *URL에서 엔터티의 크기 및 위치를 반환합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-134">**nx_http_server_get_entity_content** *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="f6ddf-135">**nx_http_server_get_entity_header** *URL 엔터티 헤더를 지정된 버퍼로 추출합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-135">**nx_http_server_get_entity_header** *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="f6ddf-136">**nx_http_server_gmt_callback_set** *GMT 날짜 및 시간을 검색하도록 콜백을 설정합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-136">**nx_http_server_gmt_callback_set** *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="f6ddf-137">**nx_http_server_invalid_userpassword_notify_set** *클라이언트 요청에서 잘못된 사용자 이름 및 암호를 받은 경우에 대한 콜백을 설정합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-137">**nx_http_server_invalid_userpassword_notify_set** *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="f6ddf-138">**nx_http_server_mime_maps_additional_set** *HTML에 대한 추가 MIME 맵을 정의합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-138">**nx_http_server_mime_maps_additional_set** *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="f6ddf-139">**nx_http_server_packet_content_find** *HTTP 헤더에서 콘텐츠 길이를 추출하고 콘텐츠 데이터 시작 부분으로 포인터를 설정합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-139">**nx_http_server_packet_content_find** *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="f6ddf-140">**nx_http_server_packet_get** *클라이언트 패킷을 직접 수신합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-140">**nx_http_server_packet_get** *Receive client packet directly*</span></span>
- <span data-ttu-id="f6ddf-141">**nx_http_server_param_get** *요청에서 매개 변수를 가져옵니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-141">**nx_http_server_param_get** *Get parameter from the request*</span></span>
- <span data-ttu-id="f6ddf-142">**nx_http_server_query_get** *요청에서 쿼리를 가져옵니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-142">**nx_http_server_query_get** *Get query from the request*</span></span>
- <span data-ttu-id="f6ddf-143">**nx_http_server_start** *HTTP 서버를 시작합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-143">**nx_http_server_start** *Start the HTTP Server*</span></span>
- <span data-ttu-id="f6ddf-144">**nx_http_server_stop** *HTTP 서버를 중지합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-144">**nx_http_server_stop** *Stop the HTTP Server*</span></span>
- <span data-ttu-id="f6ddf-145">**nx_http_server_type_get (deprecated)** *헤더에서 HTTP 형식(예: 텍스트/일반)을 추출합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-145">**nx_http_server_type_get (deprecated)** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="f6ddf-146">**nx_http_server_type_get_extended** *헤더에서 HTTP 형식(예: 텍스트/일반)을 추출합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-146">**nx_http_server_type_get_extended** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="f6ddf-147">**nx_http_server_digest_authenticate_notify_set** *다이제스트 인증 콜백 함수를 설정합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-147">**nx_http_server_digest_authenticate_notify_set** *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="f6ddf-148">**nx_http_server_authentication_check_set** *인증 확인 콜백 함수를 설정합니다.*</span><span class="sxs-lookup"><span data-stu-id="f6ddf-148">**nx_http_server_authentication_check_set** *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="f6ddf-149">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="f6ddf-149">nx_http_client_create</span></span>

<span data-ttu-id="f6ddf-150">PPPoE 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="f6ddf-150">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-151">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-151">Prototype</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="f6ddf-152">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-152">Description</span></span>

<span data-ttu-id="f6ddf-153">이 서비스는 지정된 IP 인스턴스에 HTTP 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-153">This service creates an HTTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-154">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-154">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-155">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-155">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-156">**client_name** HTTP 클라이언트 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-156">**client_name** Name of HTTP Client instance.</span></span>
 - <span data-ttu-id="f6ddf-157">**ip_ptr** IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-157">**ip_ptr** Pointer to IP instance.</span></span>
 - <span data-ttu-id="f6ddf-158">**pool_ptr** 기본 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-158">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="f6ddf-159">이 풀의 패킷에는 전체 응답 헤더를 처리할 수 있을 만큼 큰 페이로드가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-159">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="f6ddf-160">이것은 *nx_http.h* 의 NX_HTTP_CLIENT_MIN_PACKET_SIZE에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-160">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http.h*.</span></span>
 - <span data-ttu-id="f6ddf-161">**window_size** 클라이언트의 TCP 소켓 수신 창의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-161">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-162">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-162">Return Values</span></span>

 - <span data-ttu-id="f6ddf-163">**NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="f6ddf-163">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
 - <span data-ttu-id="f6ddf-164">NX_PTR_ERROR (0x07) 잘못된 HTTP, ip_ptr 또는 패킷 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-164">NX_PTR_ERROR (0x07) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
 - <span data-ttu-id="f6ddf-165">NX_HTTP_POOL_ERROR (0xE9) 패킷 풀의 잘못된 페이로드 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-165">NX_HTTP_POOL_ERROR (0xE9) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-166">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-166">Allowed From</span></span>

<span data-ttu-id="f6ddf-167">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-167">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-168">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-168">Example</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="f6ddf-169">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="f6ddf-169">nx_http_client_delete</span></span>

<span data-ttu-id="f6ddf-170">HTTP 클라이언트 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-170">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-171">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-171">Prototype</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="f6ddf-172">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-172">Description</span></span>

<span data-ttu-id="f6ddf-173">이 서비스는 이전에 만든 HTTP 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-173">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-174">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-174">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-175">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-175">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-176">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-176">Return Values</span></span>

 - <span data-ttu-id="f6ddf-177">**NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-177">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
 - <span data-ttu-id="f6ddf-178">NX_PTR_ERROR (0x07) 잘못된 HTTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-178">NX_PTR_ERROR (0x07) Invalid HTTP pointer</span></span>
 - <span data-ttu-id="f6ddf-179">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-179">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-180">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-180">Allowed From</span></span>

<span data-ttu-id="f6ddf-181">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-181">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-182">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-182">Example</span></span>

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="f6ddf-183">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="f6ddf-183">nx_http_client_get_start</span></span>

<span data-ttu-id="f6ddf-184">IPv4를 통해 HTTP GET 요청을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-184">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-185">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-185">Prototype</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6ddf-186">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-186">Description</span></span>

<span data-ttu-id="f6ddf-187">이 서비스는 이전에 생성된 HTTP 클라이언트 인스턴스에서 “리소스” 포인터로 지정된 리소스를 사용해서 GET 요청을 만들고 전송하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-187">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="f6ddf-188">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_http_client_get_packet* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-188">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-189">리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 GET 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-189">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="f6ddf-190">이 서비스는 IPv4 네트워크에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-190">This service works only over IPv4 network.</span></span> <span data-ttu-id="f6ddf-191">IPv6 네트워크 연결이 필요한 애플리케이션의 경우 *nxd_http_client_get_start_extended()* 를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-191">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="f6ddf-192">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-192">This service is deprecated.</span></span> <span data-ttu-id="f6ddf-193">개발자는 *nx_http_client_get_start_extended()* 또는 *nxd_http_client_get_start_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-193">Developers are encouraged to migrate to *nx_http_client_get_start_extended()* or *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-194">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-194">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-195">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-195">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-196">**ip_address** HTTP 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-196">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="f6ddf-197">**resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-197">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="f6ddf-198">**input_ptr** GET 요청의 추가 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-198">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="f6ddf-199">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-199">This is optional.</span></span> <span data-ttu-id="f6ddf-200">유효한 경우 지정된 입력이 메시지의 콘텐츠 영역에 배치되고 GET 작업 대신 POST가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-200">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="f6ddf-201">**input_size** ```input_ptr```에서 가리키는 선택적 추가 입력의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-201">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="f6ddf-202">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-202">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-203">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-203">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-204">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-204">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="f6ddf-205">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-205">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="f6ddf-206">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-206">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="f6ddf-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="f6ddf-208">TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-208">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="f6ddf-209">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-209">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-210">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-210">Return Values</span></span>

 - <span data-ttu-id="f6ddf-211">**NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 전송했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-211">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="f6ddf-212">시작 메시지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-212">GET start message.</span></span>
 - <span data-ttu-id="f6ddf-213">**NX_HTTP_ERROR** (0xE0) 내부 HTTP 클라이언트 오류</span><span class="sxs-lookup"><span data-stu-id="f6ddf-213">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="f6ddf-214">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-214">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="f6ddf-215">**NX_HTTP_FAILED** (0xE2) HTTP 서버와 통신하는 중 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-215">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="f6ddf-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 및/또는 암호</span><span class="sxs-lookup"><span data-stu-id="f6ddf-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="f6ddf-217">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-217">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-218">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-218">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-219">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-219">Allowed From</span></span>

<span data-ttu-id="f6ddf-220">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-221">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-221">Example</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                           NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                            POST_MESSAGE, sizeof(POST_MESSAGE),
                            “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="f6ddf-222">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="f6ddf-222">nx_http_client_get_start_extended</span></span>

<span data-ttu-id="f6ddf-223">IPv4를 통해 HTTP GET 요청을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-223">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-224">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-224">Prototype</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6ddf-225">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-225">Description</span></span>

<span data-ttu-id="f6ddf-226">이 서비스는 이전에 생성된 HTTP 클라이언트 인스턴스에서 “리소스” 포인터로 지정된 리소스를 사용해서 GET 요청을 만들고 전송하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-226">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="f6ddf-227">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_http_client_get_packet* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-227">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-228">리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 GET 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-228">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="f6ddf-229">이 서비스는 IPv4 네트워크에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-229">This service works only over IPv4 network.</span></span> <span data-ttu-id="f6ddf-230">IPv6 네트워크 연결이 필요한 애플리케이션의 경우 *nxd_http_client_get_start_extended()* 를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-230">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="f6ddf-231">이 서비스는 *nx_http_client_get_start()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-231">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="f6ddf-232">호출자가 리소스, 사용자 이름 및 암호의 길이를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-232">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-233">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-233">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-234">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-234">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-235">**ip_address** HTTP 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-235">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="f6ddf-236">**resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-236">**resource Pointer** to URL string for requested resource.</span></span>
 - <span data-ttu-id="f6ddf-237">**resource_length** 요청된 리소스에 대한 URL 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-237">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="f6ddf-238">**input_ptr** GET 요청의 추가 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-238">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="f6ddf-239">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-239">This is optional.</span></span> <span data-ttu-id="f6ddf-240">유효한 경우 지정된 입력이 메시지의 콘텐츠 영역에 배치되고 GET 작업 대신 POST가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-240">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="f6ddf-241">**input_size** ```input_ptr```에서 가리키는 선택적 추가 입력의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-241">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="f6ddf-242">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-242">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-243">**username_length** 인증을 위한 선택적 사용자 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-243">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-244">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-244">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-245">**password_length** 인증을 위한 선택적 암호의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-245">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-246">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-246">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="f6ddf-247">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="f6ddf-248">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-248">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="f6ddf-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="f6ddf-250">TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-250">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="f6ddf-251">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-251">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-252">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-252">Return Values</span></span>

 - <span data-ttu-id="f6ddf-253">**NX_SUCCESS** (0x00) HTTP 클라이언트를 성공적으로 전송했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-253">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="f6ddf-254">GET 시작 메시지</span><span class="sxs-lookup"><span data-stu-id="f6ddf-254">GET start message</span></span>
 - <span data-ttu-id="f6ddf-255">**NX_HTTP_ERROR** (0xE0) 내부 HTTP 클라이언트 오류</span><span class="sxs-lookup"><span data-stu-id="f6ddf-255">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="f6ddf-256">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-256">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="f6ddf-257">**NX_HTTP_FAILED** (0xE2) HTTP 서버와 통신하는 중 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-257">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="f6ddf-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 및/또는 암호</span><span class="sxs-lookup"><span data-stu-id="f6ddf-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="f6ddf-259">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-259">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-260">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-260">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-261">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-261">Allowed From</span></span>

<span data-ttu-id="f6ddf-262">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-262">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-263">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-263">Example</span></span>

```c
/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                     9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                     “myname”, 6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nxd_http_client_get_start"></a><span data-ttu-id="f6ddf-264">nxd_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="f6ddf-264">nxd_http_client_get_start</span></span>

<span data-ttu-id="f6ddf-265">HTTP GET 요청 보내기(IPv4 또는 IPv6)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-265">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-266">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-266">Prototype</span></span>

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6ddf-267">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-267">Description</span></span>

<span data-ttu-id="f6ddf-268">이 서비스는 이전에 생성된 HTTP 클라이언트 인스턴스에서 “리소스” 포인터로 지정된 리소스를 사용해서 GET 요청을 만들고 전송하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-268">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="f6ddf-269">IPv4 또는 IPv6 네트워크에 연결하기 위해 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-269">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="f6ddf-270">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_http_client_get_packet* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-270">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
><span data-ttu-id="f6ddf-271">리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 GET 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-271">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="f6ddf-272">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-272">This service is deprecated.</span></span> <span data-ttu-id="f6ddf-273">개발자는 *nxd_http_client_get_start_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-273">Developers are encouraged to migrate to *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-274">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-274">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-275">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-275">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-276">**Server_ip** HTTP 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-276">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="f6ddf-277">**resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-277">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="f6ddf-278">**input_ptr** GET 요청의 추가 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-278">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="f6ddf-279">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-279">This is optional.</span></span> <span data-ttu-id="f6ddf-280">유효한 경우 지정된 입력이 메시지의 콘텐츠 영역에 배치되고 GET 작업 대신 POST가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-280">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="f6ddf-281">**input_size** ```input_ptr```에서 가리키는 선택적 추가 입력의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-281">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="f6ddf-282">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-282">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-283">**username_length** 인증을 위한 선택적 사용자 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-283">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-284">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-284">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-285">**password_length** 인증을 위한 선택적 암호의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-285">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-286">**wait_option** 서비스에서 HTTP 클라이언트 GET 시작 요청을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-286">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="f6ddf-287">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-287">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="f6ddf-288">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-288">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="f6ddf-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="f6ddf-290">TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-290">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="f6ddf-291">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-291">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-292">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-292">Return Values</span></span>

 - <span data-ttu-id="f6ddf-293">**NX_SUCCESS** (0x00) GET 요청을 성공적으로 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-293">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="f6ddf-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) 암호가 버퍼 크기를 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="f6ddf-295">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-295">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="f6ddf-296">**NX_HTTP_FAILED** (0xE2) 잘못된 패킷 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-296">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="f6ddf-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 또는 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="f6ddf-298">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-298">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-299">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-299">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-300">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-300">Allowed From</span></span>

<span data-ttu-id="f6ddf-301">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-302">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-302">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start(&my_client, server_ip_address, “/TEST.HTM”,
NX_NULL, 0, “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nxd_http_client_get_start_extended"></a><span data-ttu-id="f6ddf-303">nxd_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="f6ddf-303">nxd_http_client_get_start_extended</span></span>

<span data-ttu-id="f6ddf-304">HTTP GET 요청 보내기(IPv4 또는 IPv6)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-304">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-305">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-305">Prototype</span></span>

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6ddf-306">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-306">Description</span></span>

<span data-ttu-id="f6ddf-307">이 서비스는 이전에 생성된 HTTP 클라이언트 인스턴스에서 “리소스” 포인터로 지정된 리소스를 사용해서 GET 요청을 만들고 전송하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-307">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="f6ddf-308">IPv4 또는 IPv6 네트워크에 연결하기 위해 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-308">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="f6ddf-309">이 루틴에서 NX_SUCCESS를 반환하는 경우 애플리케이션에서 *nx_http_client_get_packet* 을 여러 번 호출하여 요청된 리소스 콘텐츠에 해당하는 데이터 패킷을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-309">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-310">리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 GET 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-310">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="f6ddf-311">이 서비스는 *nxd_http_client_get_start()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-311">This service replaces *nxd_http_client_get_start()*.</span></span> <span data-ttu-id="f6ddf-312">호출자가 리소스, 사용자 이름 및 암호의 길이를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-312">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-313">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-313">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-314">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-314">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-315">**Server_ip** HTTP 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-315">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="f6ddf-316">**resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-316">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="f6ddf-317">**resource_length** 요청된 리소스에 대한 URL 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-317">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="f6ddf-318">**input_ptr** GET 요청의 추가 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-318">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="f6ddf-319">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-319">This is optional.</span></span> <span data-ttu-id="f6ddf-320">유효한 경우 지정된 입력이 메시지의 콘텐츠 영역에 배치되고 GET 작업 대신 POST가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-320">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="f6ddf-321">**input_size** ```input_ptr```에서 가리키는 선택적 추가 입력의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-321">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="f6ddf-322">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-322">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-323">**username_length** 인증을 위한 선택적 사용자 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-323">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-324">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-324">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-325">**password_length** 인증을 위한 선택적 암호의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-325">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-326">**wait_option** HTTP 클라이언트 GET을 처리하기 위해 서비스가 내부적으로 기다려야 하는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-326">**wait_option** Defines how long the service will wait internally to process the HTTP Client get start.</span></span> <span data-ttu-id="f6ddf-327">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-327">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="f6ddf-328">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-328">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="f6ddf-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="f6ddf-330">TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-330">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="f6ddf-331">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-331">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-332">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-332">Return Values</span></span>

 - <span data-ttu-id="f6ddf-333">**NX_SUCCESS** (0x00) GET 요청을 성공적으로 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-333">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="f6ddf-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) 암호가 버퍼 크기를 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="f6ddf-335">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-335">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="f6ddf-336">**NX_HTTP_FAILED** (0xE2) 잘못된 패킷 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-336">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="f6ddf-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 또는 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="f6ddf-338">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-338">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-339">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-339">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-340">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-340">Allowed From</span></span>

<span data-ttu-id="f6ddf-341">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-342">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-342">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start_extended(&my_client, server_ip_address,
                                             “/TEST.HTM”, 9, NX_NULL, 0, “myname”,
        6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="f6ddf-343">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="f6ddf-343">nx_http_client_get_packet</span></span>

<span data-ttu-id="f6ddf-344">다음 리소스 데이터 패킷 가져오기</span><span class="sxs-lookup"><span data-stu-id="f6ddf-344">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-345">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-345">Prototype</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a><span data-ttu-id="f6ddf-346">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-346">Description</span></span>

<span data-ttu-id="f6ddf-347">이 서비스는 이전 *nx_http_client_get_start* 호출에서 요청한 리소스 콘텐츠의 다음 패킷을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-347">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="f6ddf-348">NX_HTTP_GET_DONE의 반환 상태를 받을 때까지 이 루틴에 대한 연속 호출을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-348">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-349">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-349">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-350">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-350">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-351">**packet_ptr** 부분 리소스 콘텐츠를 포함하는 패킷 포인터의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-351">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
 - <span data-ttu-id="f6ddf-352">**wait_option** 서비스에서 HTTP 클라이언트 GET 패킷을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-352">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="f6ddf-353">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-353">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="f6ddf-354">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-354">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="f6ddf-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="f6ddf-356">TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-356">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="f6ddf-357">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-357">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-358">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-358">Return Values</span></span>

 - <span data-ttu-id="f6ddf-359">**NX_SUCCESS** (0x00) HTTP 클라이언트 GET 패킷을 성공적으로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-359">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
 - <span data-ttu-id="f6ddf-360">**NX_HTTP_GET_DONE** (0xEC) HTTP 클라이언트 GET 패킷이 완료됨</span><span class="sxs-lookup"><span data-stu-id="f6ddf-360">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
 - <span data-ttu-id="f6ddf-361">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 GET 모드가 아님</span><span class="sxs-lookup"><span data-stu-id="f6ddf-361">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
 - <span data-ttu-id="f6ddf-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) 잘못된 패킷 길이</span><span class="sxs-lookup"><span data-stu-id="f6ddf-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="f6ddf-363">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-363">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-364">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-364">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-365">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-365">Allowed From</span></span>

<span data-ttu-id="f6ddf-366">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-366">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-367">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-367">Example</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="f6ddf-368">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="f6ddf-368">nx_http_client_put_start</span></span>

<span data-ttu-id="f6ddf-369">IPv4를 통해 HTTP PUT 요청을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-369">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-370">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-370">Prototype</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6ddf-371">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-371">Description</span></span>

<span data-ttu-id="f6ddf-372">이 서비스는 지정된 리소스가 포함된 PUT 요청을 제공된 IP 주소의 HTTP 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-372">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="f6ddf-373">이 루틴이 성공하면 애플리케이션 코드에서 *nx_http_client_put_packet()* 루틴을 연속적으로 호출하여 실제로 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-373">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-374">리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 PUT 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-374">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="f6ddf-375">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-375">This service is deprecated.</span></span> <span data-ttu-id="f6ddf-376">개발자는 *nx_http_client_put_start_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-376">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-377">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-377">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-378">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-378">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-379">**ip_address** HTTP 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-379">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="f6ddf-380">**resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-380">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="f6ddf-381">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-381">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-382">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-382">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-383">**total_bytes** 전송 중인 리소스의 총 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-383">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="f6ddf-384">*nx_http_client_put_packet* 에 대한 후속 호출을 통해 전송된 모든 패킷의 결합된 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-384">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="f6ddf-385">**wait_option** 서비스에서 HTTP 클라이언트 PUT 시작을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-385">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="f6ddf-386">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-386">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="f6ddf-387">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-387">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="f6ddf-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="f6ddf-389">TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-389">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="f6ddf-390">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-390">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-391">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-391">Return Values</span></span>

 - <span data-ttu-id="f6ddf-392">**NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="f6ddf-392">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="f6ddf-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) 사용자 이름이 버퍼에 비해 너무 큼</span><span class="sxs-lookup"><span data-stu-id="f6ddf-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="f6ddf-394">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-394">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="f6ddf-395">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-395">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-396">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="f6ddf-396">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="f6ddf-397">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-397">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-398">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-398">Allowed From</span></span>

<span data-ttu-id="f6ddf-399">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-400">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-400">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="f6ddf-401">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="f6ddf-401">nx_http_client_put_start_extended</span></span>

<span data-ttu-id="f6ddf-402">IPv4를 통해 HTTP PUT 요청을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-402">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-403">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-403">Prototype</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6ddf-404">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-404">Description</span></span>

<span data-ttu-id="f6ddf-405">이 서비스는 지정된 리소스가 포함된 PUT 요청을 제공된 IP 주소의 HTTP 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-405">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="f6ddf-406">이 루틴이 성공하면 애플리케이션 코드에서 *nx_http_client_put_packet()* 루틴을 연속적으로 호출하여 실제로 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-406">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-407">리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 PUT 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-407">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="f6ddf-408">이 서비스는 *nx_http_client_put_start()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-408">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="f6ddf-409">호출자가 리소스, 사용자 이름 및 암호의 길이를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-409">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-410">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-410">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-411">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-411">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-412">**ip_address** HTTP 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-412">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="f6ddf-413">**resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-413">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="f6ddf-414">**resource_length** 서버에 보내는 리소스에 대한 URL 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-414">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="f6ddf-415">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-415">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-416">**username_length** 인증을 위한 선택적 사용자 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-416">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-417">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-417">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-418">**password_length** 인증을 위한 선택적 암호의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-418">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-419">**total_bytes** 전송 중인 리소스의 총 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-419">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="f6ddf-420">*nx_http_client_put_packet* 에 대한 후속 호출을 통해 전송된 모든 패킷의 결합된 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-420">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="f6ddf-421">**wait_option** 서비스에서 HTTP 클라이언트 PUT 시작을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-421">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="f6ddf-422">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-422">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="f6ddf-423">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-423">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="f6ddf-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="f6ddf-425">TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-425">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="f6ddf-426">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-426">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-427">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-427">Return Values</span></span>

 - <span data-ttu-id="f6ddf-428">**NX_SUCCESS** (0x00) PUT 요청을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="f6ddf-428">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="f6ddf-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) 사용자 이름이 버퍼에 비해 너무 큼</span><span class="sxs-lookup"><span data-stu-id="f6ddf-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="f6ddf-430">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-430">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="f6ddf-431">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-431">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-432">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="f6ddf-432">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="f6ddf-433">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-433">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-434">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-434">Allowed From</span></span>

<span data-ttu-id="f6ddf-435">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-436">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-436">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a><span data-ttu-id="f6ddf-437">nxd_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="f6ddf-437">nxd_http_client_put_start</span></span>

<span data-ttu-id="f6ddf-438">HTTP PUT 요청을 시작합니다(IPv4 또는 IPv6).</span><span class="sxs-lookup"><span data-stu-id="f6ddf-438">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-439">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-439">Prototype</span></span>

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6ddf-440">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-440">Description</span></span>

<span data-ttu-id="f6ddf-441">이 서비스는 IPv6를 통해 제공된 IP 주소에서 HTTP 서버의 지정된 리소스를 PUT(전송)하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-441">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="f6ddf-442">이 루틴이 성공하면 애플리케이션 코드에서 *nx_http_client_put_packet()* 루틴을 연속적으로 호출하여 실제로 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-442">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-443">리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 PUT 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-443">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="f6ddf-444">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-444">This service is deprecated.</span></span> <span data-ttu-id="f6ddf-445">개발자는 *nx_http_client_put_start_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-445">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-446">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-446">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-447">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-447">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-448">**server_ip** HTTP 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-448">**server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="f6ddf-449">**resource** 서버에 보내는 리소스의 URL 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-449">**resource** Pointer to URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="f6ddf-450">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-450">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-451">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-451">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-452">**total_bytes** 전송 중인 리소스의 총 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-452">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="f6ddf-453">*nx_http_client_put_packet* 에 대한 후속 호출을 통해 전송된 모든 패킷의 결합된 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-453">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="f6ddf-454">**wait_option** 서비스에서 HTTP 클라이언트 PUT 시작을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-454">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="f6ddf-455">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-455">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="f6ddf-456">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-456">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="f6ddf-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="f6ddf-458">TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-458">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="f6ddf-459">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-459">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-460">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-460">Return Values</span></span>

 - <span data-ttu-id="f6ddf-461">**NX_SUCCESS** (0x00) HTTP 클라이언트 PUT 요청을 성공적으로 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-461">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="f6ddf-462">**NX_HTTP_ERROR** (0xE0) HTTP 클라이언트 내부 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-462">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="f6ddf-463">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-463">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="f6ddf-464">**NX_HTTP_FAILED** (0xE2) HTTP 서버와 통신하는 중 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-464">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="f6ddf-465">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-465">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-466">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="f6ddf-466">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="f6ddf-467">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-468">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-468">Allowed From</span></span>

<span data-ttu-id="f6ddf-469">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-470">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-470">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start(&my_client, &server_ip_address,
                                    "/client_test.htm", "name", "password", 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nxd_http_client_put_start_extended"></a><span data-ttu-id="f6ddf-471">nxd_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="f6ddf-471">nxd_http_client_put_start_extended</span></span>

<span data-ttu-id="f6ddf-472">HTTP PUT 요청을 시작합니다(IPv4 또는 IPv6).</span><span class="sxs-lookup"><span data-stu-id="f6ddf-472">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-473">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-473">Prototype</span></span>

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6ddf-474">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-474">Description</span></span>

<span data-ttu-id="f6ddf-475">이 서비스는 IPv6를 통해 제공된 IP 주소에서 HTTP 서버의 지정된 리소스를 PUT(전송)하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-475">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="f6ddf-476">이 루틴이 성공하면 애플리케이션 코드에서 *nx_http_client_put_packet()* 루틴을 연속적으로 호출하여 실제로 리소스 콘텐츠를 HTTP 서버에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-476">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-477">리소스 문자열은 로컬 파일(예: ``` “/index.htm” ```)을 호출하거나 HTTP 서버에 PUT 요청 참조 지원이 표시된 경우 다른 URL(예: ```http://abc.website.com/index.htm```)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-477">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="f6ddf-478">이 서비스는 *nxd_http_client_put_start()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-478">This service replaces *nxd_http_client_put_start()*.</span></span> <span data-ttu-id="f6ddf-479">호출자가 리소스, 사용자 이름 및 암호의 길이를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-479">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-480">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-480">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-481">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-481">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-482">**ip_address** HTTP 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-482">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="f6ddf-483">**resource** 요청된 리소스의 URL 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-483">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="f6ddf-484">**resource_length** 서버에 보내는 리소스에 대한 URL 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-484">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="f6ddf-485">**username** 인증을 위한 선택적 사용자 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-485">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-486">**username_length** 인증을 위한 선택적 사용자 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-486">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="f6ddf-487">**password** 인증을 위한 선택적 암호에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-487">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-488">**password_length** 인증을 위한 선택적 암호의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-488">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="f6ddf-489">**total_bytes** 전송 중인 리소스의 총 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-489">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="f6ddf-490">*nx_http_client_put_packet* 에 대한 후속 호출을 통해 전송된 모든 패킷의 결합된 길이는 이 값과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-490">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="f6ddf-491">**wait_option** 서비스에서 HTTP 클라이언트 PUT 시작을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-491">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="f6ddf-492">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-492">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="f6ddf-493">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-493">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="f6ddf-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="f6ddf-495">TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-495">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="f6ddf-496">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-496">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-497">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-497">Return Values</span></span>

 - <span data-ttu-id="f6ddf-498">**NX_SUCCESS** (0x00) HTTP 클라이언트 PUT 요청을 성공적으로 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-498">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="f6ddf-499">**NX_HTTP_ERROR** (0xE0) HTTP 클라이언트 내부 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-499">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="f6ddf-500">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-500">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="f6ddf-501">NX_HTTP_FAILED (0xE2) HTTP 서버와 통신하는 중 HTTP 클라이언트 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-501">NX_HTTP_FAILED (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="f6ddf-502">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-502">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-503">NX_SIZE_ERROR (0x09) 잘못된 총 리소스 크기</span><span class="sxs-lookup"><span data-stu-id="f6ddf-503">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="f6ddf-504">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-504">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-505">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-505">Allowed From</span></span>

<span data-ttu-id="f6ddf-506">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-507">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-507">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start_extended(&my_client, &server_ip_address,
                                            "/client_test.htm", 16, "name", 4, "password", 8, 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="f6ddf-508">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="f6ddf-508">nx_http_client_put_packet</span></span>

<span data-ttu-id="f6ddf-509">다음 리소스 데이터 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-509">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-510">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-510">Prototype</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6ddf-511">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-511">Description</span></span>

<span data-ttu-id="f6ddf-512">이 서비스는 리소스 콘텐츠의 다음 패킷을 HTTP 서버에 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-512">This service attempts to send the next packet of resource content to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-513">이 루틴은 전송된 패킷의 결합된 길이가 이전 *nx_http_client_put_start()* 호출에 지정된 "total_bytes"와 같아질 때까지 반복적으로 호출되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-513">This routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start* call.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-514">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-514">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-515">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-515">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-516">**packet_ptr** HTTP 서버에 보내는 리소스의 다음 콘텐츠에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-516">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
 - <span data-ttu-id="f6ddf-517">**wait_option** 서비스에서 HTTP 클라이언트 PUT 패킷을 처리하기 위해 내부적으로 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-517">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="f6ddf-518">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-518">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="f6ddf-519">**시간 제한 값** (0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-519">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="f6ddf-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="f6ddf-521">TX_WAIT_FOREVER를 선택하면 HTTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-521">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="f6ddf-522">숫자 값(0x1-0xFFFFFFFE)을 선택하면 HTTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-522">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-523">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-523">Return Values</span></span>

 - <span data-ttu-id="f6ddf-524">**NX_SUCCESS** (0x00) HTTP 클라이언트 패킷을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="f6ddf-524">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
 - <span data-ttu-id="f6ddf-525">**NX_HTTP_NOT_READY** (0xEA) HTTP 클라이언트가 준비되지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-525">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="f6ddf-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) 서버 오류 코드가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code</span></span>
 - <span data-ttu-id="f6ddf-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) 잘못된 패킷 길이</span><span class="sxs-lookup"><span data-stu-id="f6ddf-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="f6ddf-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) 잘못된 이름 및/또는 암호</span><span class="sxs-lookup"><span data-stu-id="f6ddf-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
 - <span data-ttu-id="f6ddf-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) PUT이 완료되기 전에 서버에서 응답함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
 - <span data-ttu-id="f6ddf-530">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-530">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-531">NX_INVALID_PACKET (0x12) 패킷이 TCP 헤더에 비해 너무 작음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-531">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
 - <span data-ttu-id="f6ddf-532">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-532">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-533">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-533">Allowed From</span></span>

<span data-ttu-id="f6ddf-534">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-535">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-535">Example</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="f6ddf-536">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="f6ddf-536">nx_http_client_set_connect_port</span></span>

<span data-ttu-id="f6ddf-537">서버에 대한 연결 포트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-537">Set the connection port to the Server</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-538">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-538">Prototype</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a><span data-ttu-id="f6ddf-539">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-539">Description</span></span>

<span data-ttu-id="f6ddf-540">이 서비스는 런타임에 지정된 포트에서 HTTP 서버에 연결할 때 연결 포트를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-540">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="f6ddf-541">그렇지 않으면 연결 포트의 기본값은 80입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-541">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="f6ddf-542">이는 *nx_http_client_get_start()* 및 *nx_http_client_put_start()* 전에 호출해야 합니다(예: HTTP 클라이언트에서 서버에 연결하는 경우).</span><span class="sxs-lookup"><span data-stu-id="f6ddf-542">This must be called before *nx_http_client_get_start()* and *nx_http_client_put_start()* e.g. when the HTTP Client connects with the Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-543">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-543">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-544">**client_ptr** HTTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-544">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="f6ddf-545">**port** 서버에 연결하기 위한 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-545">**port** Port for connecting to the Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-546">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-546">Return Values</span></span>

 - <span data-ttu-id="f6ddf-547">**NX_SUCCESS** (0x00) 포트를 성공적으로 변경했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-547">**NX_SUCCESS** (0x00) Successfully change port</span></span>
 - <span data-ttu-id="f6ddf-548">NX_INVALID_PORT (0x46) 포트가 최댓값(0xFFFF)을 초과하거나 0입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-548">NX_INVALID_PORT (0x46) Port exceeds the maximum (0xFFFF) or is zero</span></span>
 - <span data-ttu-id="f6ddf-549">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-549">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-550">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-550">Allowed From</span></span>

<span data-ttu-id="f6ddf-551">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="f6ddf-551">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-552">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-552">Example</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="f6ddf-553">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="f6ddf-553">nx_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="f6ddf-554">URL 최대 사용 기간 및 날짜를 검색하는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-554">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-555">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-555">Prototype</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
```

### <a name="description"></a><span data-ttu-id="f6ddf-556">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-556">Description</span></span>

<span data-ttu-id="f6ddf-557">이 서비스는 지정된 리소스의 최대 사용 기간 및 마지막으로 수정한 날짜를 가져오기 위해 호출되는 콜백 서비스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-557">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-558">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-558">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-559">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-559">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="f6ddf-560">**cache_info_get** 콜백에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-560">**cache_info_get** Pointer to the callback</span></span>
 - <span data-ttu-id="f6ddf-561">**max_age** 리소스의 최대 사용 기간에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-561">**max_age** Pointer to maximum age of a resource</span></span>
 - <span data-ttu-id="f6ddf-562">**data** 반환된 마지막 수정 날짜에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-562">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-563">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-563">Return Values</span></span>

 - <span data-ttu-id="f6ddf-564">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-564">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="f6ddf-565">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-565">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-566">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-566">Allowed From</span></span>

<span data-ttu-id="f6ddf-567">초기화</span><span class="sxs-lookup"><span data-stu-id="f6ddf-567">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-568">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-568">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
                           NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP  
   server is set by nx_http_server_start(), set the cache info callback: */

status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);


/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="f6ddf-569">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="f6ddf-569">nx_http_server_callback_data_send</span></span>

<span data-ttu-id="f6ddf-570">콜백 함수에서 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-570">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-571">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-571">Prototype</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="f6ddf-572">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-572">Description</span></span>

<span data-ttu-id="f6ddf-573">이 서비스는 애플리케이션의 콜백 루틴에서 제공된 패킷의 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-573">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="f6ddf-574">일반적으로 GET/POST 요청과 연결된 동적 데이터를 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-574">This is typically used to send dynamic data associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-575">이 함수를 사용할 경우 콜백 루틴에서 전체 응답을 적절한 형식으로 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-575">If this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="f6ddf-576">또한 콜백 루틴에서 NX_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-576">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-577">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-577">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-578">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-578">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="f6ddf-579">**data_ptr** 보내는 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-579">**data_ptr** Pointer to the data to send.</span></span>
 - <span data-ttu-id="f6ddf-580">**data_length** 보낼 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-580">**data_length**  Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-581">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-581">Return Values</span></span>

 - <span data-ttu-id="f6ddf-582">**NX_SUCCESS** (0x00) 서버 데이터를 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="f6ddf-582">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
 - <span data-ttu-id="f6ddf-583">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-583">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-584">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-584">Allowed From</span></span>

<span data-ttu-id="f6ddf-585">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-586">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-586">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
  CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
                (strcmp(resource, "/test.htm") == 0))
    {

        /* Found it, override the GET processing by sending the resource
    contents directly. */

        nx_http_server_callback_data_send(server_ptr,
    "HTTP/1.0 200 \r\nContent-Length:
    103\r\nContent-Type: text/html\r\n\r\n",
    63);

        nx_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX
    HTTP Test </TITLE></HEAD>\r\n
    <BODY>\r\n<H1>NetX Test Page
    </H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="f6ddf-587">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="f6ddf-587">nx_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="f6ddf-588">콜백 함수에서 응답 헤더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-588">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-589">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-589">Prototype</span></span>

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="f6ddf-590">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-590">Description</span></span>

<span data-ttu-id="f6ddf-591">이 서비스는 HTTP 서버에서 클라이언트 GET, PUT 및 DELETE 요청에 응답할 때 *_nx_http_server_generate_response_header* 내부 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-591">This service calls the internal function *_nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="f6ddf-592">HTTP 서버 애플리케이션에서 클라이언트에 대한 응답을 설계하는 경우 HTTP 서버 콜백 함수에서 사용하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-592">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="f6ddf-593">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-593">This service is deprecated.</span></span> <span data-ttu-id="f6ddf-594">개발자는 *nxd_http_server_callback_generate_response_header_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-594">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-595">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-595">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-596">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-596">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="f6ddf-597">**packet_pptr** 메시지에 할당된 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-597">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="f6ddf-598">**status_code** 리소스 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-598">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="f6ddf-599">예제:</span><span class="sxs-lookup"><span data-stu-id="f6ddf-599">Examples:</span></span>
    - <span data-ttu-id="f6ddf-600">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="f6ddf-600">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="f6ddf-601">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="f6ddf-601">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="f6ddf-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="f6ddf-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="f6ddf-603">**content_length** 콘텐츠의 크기입니다(바이트).</span><span class="sxs-lookup"><span data-stu-id="f6ddf-603">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="f6ddf-604">**content_type** HTTP 형식입니다(예: "텍스트/일반").</span><span class="sxs-lookup"><span data-stu-id="f6ddf-604">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="f6ddf-605">**additional_header** 추가 헤더 텍스트에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-605">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-606">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-606">Return Values</span></span>

 - <span data-ttu-id="f6ddf-607">**NX_SUCCESS** (0x00) 헤더를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="f6ddf-607">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="f6ddf-608">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-608">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-609">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-609">Allowed From</span></span>

<span data-ttu-id="f6ddf-610">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-610">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-611">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-611">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
            Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
                  &resp_packet_ptr, NX_HTTP_STATUS_OK,
                  length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
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

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="f6ddf-612">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="f6ddf-612">nx_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="f6ddf-613">콜백 함수에서 응답 헤더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-613">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-614">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-614">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="f6ddf-615">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-615">Description</span></span>

<span data-ttu-id="f6ddf-616">이 서비스는 HTTP 서버에서 클라이언트 GET, PUT 및 DELETE 요청에 응답할 때 *_nx_http_server_generate_response_header()* 내부 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-616">This service calls the internal function *_nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="f6ddf-617">HTTP 서버 애플리케이션에서 클라이언트에 대한 응답을 설계하는 경우 HTTP 서버 콜백 함수에서 사용하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-617">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="f6ddf-618">이 서비스는 *nx_http_server_callback_generate_response_header()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-618">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="f6ddf-619">이 버전은 추가 길이 정보를 콜백 함수에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-619">This version supplies additional length information to the callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-620">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-620">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-621">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-621">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="f6ddf-622">**packet_pptr** 메시지에 할당된 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-622">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="f6ddf-623">**status_code** 리소스 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-623">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="f6ddf-624">예제:</span><span class="sxs-lookup"><span data-stu-id="f6ddf-624">Examples:</span></span>
    - <span data-ttu-id="f6ddf-625">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="f6ddf-625">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="f6ddf-626">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="f6ddf-626">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="f6ddf-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="f6ddf-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="f6ddf-628">**status_code** 상태 코드의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-628">**status_code** Length of status code</span></span>
 - <span data-ttu-id="f6ddf-629">**content_length** 콘텐츠의 크기입니다(바이트).</span><span class="sxs-lookup"><span data-stu-id="f6ddf-629">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="f6ddf-630">**content_type** HTTP 형식입니다(예: "텍스트/일반").</span><span class="sxs-lookup"><span data-stu-id="f6ddf-630">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="f6ddf-631">**content_type_length** HTTP 형식의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-631">**content_type_length** Length of HTTP type</span></span>
 - <span data-ttu-id="f6ddf-632">**additional_header** 추가 헤더 텍스트에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-632">**additional_header** Pointer to additional header text</span></span>
 - <span data-ttu-id="f6ddf-633">**additional_header_length** 추가 헤더 텍스트의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-633">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-634">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-634">Return Values</span></span>

 - <span data-ttu-id="f6ddf-635">**NX_SUCCESS** (0x00) 헤더를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="f6ddf-635">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="f6ddf-636">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-636">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-637">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-637">Allowed From</span></span>

<span data-ttu-id="f6ddf-638">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-638">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-639">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-639">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
     Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
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
                 length,  server_ptr ->
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

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="f6ddf-640">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="f6ddf-640">nx_http_server_callback_packet_send</span></span>

<span data-ttu-id="f6ddf-641">콜백 함수에서 HTTP 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-641">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-642">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-642">Prototype</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="f6ddf-643">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-643">Description</span></span>

<span data-ttu-id="f6ddf-644">이 서비스는 HTTP 콜백에서 전체 HTTP 서버 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-644">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="f6ddf-645">HTTP 서버는 NX_HTTP_SERVER _TIMEOUT_SEND를 사용하여 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-645">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="f6ddf-646">HTTP 헤더 및 데이터를 패킷에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-646">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="f6ddf-647">반환 상태에서 오류가 표시되는 경우 HTTP 애플리케이션에서 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-647">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="f6ddf-648">콜백에서 NX_HTTP_CALLBACK_COMPLETED를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-648">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="f6ddf-649">자세한 예제는 *nx_http_server_callback_generate_response_header()* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-649">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-650">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-650">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-651">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-651">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="f6ddf-652">**packet_ptr** 전송할 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-652">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-653">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-653">Return Values</span></span>

 - <span data-ttu-id="f6ddf-654">**NX_SUCCESS** (0x00) 서버 패킷을 성공적으로 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-654">**NX_SUCCESS** (0x00) Successfully sent Server packet</span></span>
 - <span data-ttu-id="f6ddf-655">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-655">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-656">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-656">Allowed From</span></span>

<span data-ttu-id="f6ddf-657">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-657">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-658">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-658">Example</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
   Client directly. */

   status = nx_http_server_callback_response_send(server_ptr, packet_ptr);

   if (status != NX_SUCCESS)
   {

    nx_packet_release(packet_ptr);
   }

    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="f6ddf-659">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="f6ddf-659">nx_http_server_callback_response_send</span></span>

<span data-ttu-id="f6ddf-660">콜백 함수에서 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-660">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-661">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-661">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="f6ddf-662">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-662">Description</span></span>

<span data-ttu-id="f6ddf-663">이 서비스는 애플리케이션의 콜백 루틴에서 제공된 응답 정보를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-663">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="f6ddf-664">일반적으로 GET/POST 요청과 연결된 사용자 지정 응답을 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-664">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-665">이 함수를 사용하는 경우 콜백 루틴에서 NX_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-665">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="f6ddf-666">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-666">This service is deprecated.</span></span> <span data-ttu-id="f6ddf-667">개발자는 *nxd_http_server_callback_response_send_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-667">Developers are encouraged to migrate to *nxd_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-668">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-668">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-669">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-669">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="f6ddf-670">**header** 응답 헤더 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-670">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="f6ddf-671">**information** 정보 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-671">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="f6ddf-672">**additional_info** 추가 정보 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-672">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-673">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-673">Return Values</span></span>

 - <span data-ttu-id="f6ddf-674">**NX_SUCCESS** (0x00) 서버 응답을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="f6ddf-674">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-675">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-675">Allowed From</span></span>

<span data-ttu-id="f6ddf-676">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-677">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-677">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
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

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="f6ddf-678">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="f6ddf-678">nx_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="f6ddf-679">콜백 함수에서 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-679">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-680">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-680">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
                                          NX_HTTP_SERVER *server_ptr,
                                          CHAR *header,
                                          UINT header_length,
                                          CHAR *information,
                                          UINT information_length,
                                          CHAR *additional_info,
                                          UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="f6ddf-681">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-681">Description</span></span>

<span data-ttu-id="f6ddf-682">이 서비스는 애플리케이션의 콜백 루틴에서 제공된 응답 정보를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-682">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="f6ddf-683">일반적으로 GET/POST 요청과 연결된 사용자 지정 응답을 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-683">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-684">이 함수를 사용하는 경우 콜백 루틴에서 NX_HTTP_CALLBACK_COMPLETED 상태를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-684">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="f6ddf-685">이 서비스는 *nx_http_server_callback_response_send()* 를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-685">This service replaces *nx_http_server_callback_response_send()*.</span></span> <span data-ttu-id="f6ddf-686">이 버전은 추가 길이 정보를 인수로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-686">This version takes additional length information as arguments.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-687">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-687">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-688">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-688">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="f6ddf-689">**header** 응답 헤더 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-689">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="f6ddf-690">**header_length** 응답 헤더 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-690">**header_length** Length of the response header string.</span></span>
 - <span data-ttu-id="f6ddf-691">**information** 정보 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-691">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="f6ddf-692">**information_length** 정보 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-692">**information_length** Length of the information string.</span></span>
 - <span data-ttu-id="f6ddf-693">**additional_info** 추가 정보 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-693">**additional_info** Pointer to the additional information string.</span></span>
 - <span data-ttu-id="f6ddf-694">**additional_info_length** 추가 정보 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-694">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-695">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-695">Return Values</span></span>

 - <span data-ttu-id="f6ddf-696">**NX_SUCCESS** (0x00) 서버 응답을 성공적으로 보냄</span><span class="sxs-lookup"><span data-stu-id="f6ddf-696">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-697">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-697">Allowed From</span></span>

<span data-ttu-id="f6ddf-698">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-698">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-699">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-699">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send_extended(
                                             server_ptr,
                      "HTTP/1.0 404 ", 12,
                      "NetX HTTP Server unable to find  
                       file: ", 38, resource, 9);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="f6ddf-700">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="f6ddf-700">nx_http_server_content_get</span></span>

<span data-ttu-id="f6ddf-701">요청에서 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-701">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-702">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-702">Prototype</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="f6ddf-703">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-703">Description</span></span>

<span data-ttu-id="f6ddf-704">이 서비스는 POST 또는 PUT HTTP 클라이언트 요청에서 지정된 양의 콘텐츠를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-704">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="f6ddf-705">HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create*)에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-705">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="f6ddf-706">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-706">This service is deprecated.</span></span> <span data-ttu-id="f6ddf-707">개발자는 *nx_http_server_content_get_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-707">Developers are encouraged to migrate to *nx_http_server_content_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-708">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-708">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-709">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-709">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="f6ddf-710">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-710">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="f6ddf-711">이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-711">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="f6ddf-712">**byte_offset** 콘텐츠 영역으로 오프셋할 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-712">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="f6ddf-713">**destination_ptr** 콘텐츠의 대상 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-713">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="f6ddf-714">**destination_size** 대상 영역에서 사용 가능한 최대 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-714">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="f6ddf-715">**actual_size** 복사된 콘텐츠의 실제 크기로 설정되는 대상 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-715">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-716">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-716">Return Values</span></span>

 - <span data-ttu-id="f6ddf-717">**NX_SUCCESS** (0x00) HTTP 서버 콘텐츠를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="f6ddf-717">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
 - <span data-ttu-id="f6ddf-718">**NX_HTTP_ERROR** (0xE0) HTTP 서버 내부 오류</span><span class="sxs-lookup"><span data-stu-id="f6ddf-718">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="f6ddf-719">**NX_HTTP_DATA_END** (0xE7) 요청 콘텐츠의 끝</span><span class="sxs-lookup"><span data-stu-id="f6ddf-719">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="f6ddf-720">**NX_HTTP_TIMEOUT** (0xE1) 콘텐츠의 다음 패킷을 가져오는 중에 HTTP 서버 시간이 초과됨</span><span class="sxs-lookup"><span data-stu-id="f6ddf-720">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
 - <span data-ttu-id="f6ddf-721">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-721">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-722">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-722">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-723">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-723">Allowed From</span></span>

<span data-ttu-id="f6ddf-724">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-724">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-725">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-725">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="f6ddf-726">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="f6ddf-726">nx_http_server_content_get_extended</span></span>

<span data-ttu-id="f6ddf-727">요청에서 콘텐츠를 가져오고 길이가 0인 콘텐츠 길이를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-727">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-728">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-728">Prototype</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="f6ddf-729">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-729">Description</span></span>

<span data-ttu-id="f6ddf-730">이 서비스는 *nx_http_server_content_get();* 과 거의 동일하며, POST 또는 PUT HTTP 클라이언트 요청에서 지정된 양의 콘텐츠를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-730">This service is almost identical to *nx_http_server_content_get();* it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="f6ddf-731">그러나 콘텐츠 길이 값이 0인 요청('빈 요청')을 유효한 요청으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-731">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="f6ddf-732">HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-732">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="f6ddf-733">이 서비스는 *nx_http_server_content_get()* 을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-733">This service replaces *nx_http_server_content_get()*.</span></span> <span data-ttu-id="f6ddf-734">이 버전을 사용하려면 호출자가 추가 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-734">This version requires caller to supply additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-735">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-735">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-736">**server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-736">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="f6ddf-737">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-737">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="f6ddf-738">이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-738">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="f6ddf-739">**byte_offset** 콘텐츠 영역으로 오프셋할 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-739">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="f6ddf-740">**destination_ptr** 콘텐츠의 대상 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-740">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="f6ddf-741">**destination_size** 대상 영역에서 사용 가능한 최대 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-741">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="f6ddf-742">**actual_size** 복사된 콘텐츠의 실제 크기로 설정되는 대상 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-742">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-743">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-743">Return Values</span></span>

 - <span data-ttu-id="f6ddf-744">**NX_SUCCESS** (0x00) HTTP 콘텐츠를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="f6ddf-744">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
 - <span data-ttu-id="f6ddf-745">**NX_HTTP_ERROR** (0xE0) HTTP 서버 내부 오류</span><span class="sxs-lookup"><span data-stu-id="f6ddf-745">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="f6ddf-746">**NX_HTTP_DATA_END** (0xE7) 요청 콘텐츠의 끝</span><span class="sxs-lookup"><span data-stu-id="f6ddf-746">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="f6ddf-747">**NX_HTTP_TIMEOUT** (0xE1) 다음 패킷을 가져오는 중에 HTTP 서버 시간이 초과됨</span><span class="sxs-lookup"><span data-stu-id="f6ddf-747">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
 - <span data-ttu-id="f6ddf-748">NX_PTR_ERROR (0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-748">NX_PTR_ERROR (0x07) Invalid  pointer input</span></span>
 - <span data-ttu-id="f6ddf-749">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-749">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-750">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-750">Allowed From</span></span>

<span data-ttu-id="f6ddf-751">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-752">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-752">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="f6ddf-753">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="f6ddf-753">nx_http_server_content_length_get</span></span>

<span data-ttu-id="f6ddf-754">요청에서 콘텐츠 길이를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-754">Get length of content in the request</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-755">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-755">Prototype</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="f6ddf-756">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-756">Description</span></span>

<span data-ttu-id="f6ddf-757">이 서비스는 제공된 패킷에서 HTTP 콘텐츠 길이를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-757">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="f6ddf-758">HTTP 콘텐츠가 없는 경우 이 루틴은 0 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-758">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="f6ddf-759">HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create()* )에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-759">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="f6ddf-760">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-760">This service is deprecated.</span></span> <span data-ttu-id="f6ddf-761">개발자는 *nx_http_server_content_length_get_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-761">Developers are encouraged to migrate to *nx_http_server_content_length_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-762">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-762">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-763">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-763">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="f6ddf-764">이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-764">Note that this packet must not be released by the request notify callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-765">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-765">Return Values</span></span>

 - <span data-ttu-id="f6ddf-766">**content length** 오류 시 값 0이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-766">**content length** On error, a value of zero is returned</span></span>  

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-767">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-767">Allowed From</span></span>

<span data-ttu-id="f6ddf-768">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-768">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-769">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-769">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="f6ddf-770">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="f6ddf-770">nx_http_server_content_length_get_extended</span></span>

<span data-ttu-id="f6ddf-771">요청에서 콘텐츠 길이를 가져오고 콘텐츠 길이 값(0)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-771">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-772">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-772">Prototype</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="f6ddf-773">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-773">Description</span></span>

<span data-ttu-id="f6ddf-774">이 서비스는 *nx_http_server_content_length_get;* 과 비슷하며, 제공된 패킷에서 HTTP 콘텐츠 길이를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-774">This service is similar to *nx_http_server_content_length_get;* attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="f6ddf-775">그러나 반환 값은 성공적인 완료 상태를 나타내며, 실제 길이 값은 ```content_length``` 입력 포인터에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-775">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer ```content_length```.</span></span> <span data-ttu-id="f6ddf-776">HTTP 콘텐츠가 없거나 콘텐츠 길이가 0인 경우에도 이 루틴에서 여전히 성공적인 완료 상태를 반환하며 content_length 입력 포인터가 유효한 길이(0)를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-776">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="f6ddf-777">HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create*)에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-777">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="f6ddf-778">이 서비스는 *nx_http_server_content_length_get()* 을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-778">This service replaces *nx_http_server_content_length_get()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-779">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-779">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-780">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-780">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="f6ddf-781">이 패킷은 요청 알림 콜백에서 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-781">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="f6ddf-782">**content_length** 콘텐츠 길이 필드에서 검색된 값에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-782">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-783">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-783">Return Values</span></span>

 - <span data-ttu-id="f6ddf-784">**NX_SUCCESS** (0x00) 서버 콘텐츠를 성공적으로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-784">**NX_SUCCESS** (0x00) Successful Server content get</span></span>
 - <span data-ttu-id="f6ddf-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) 잘못된 HTTP 헤더 형식</span><span class="sxs-lookup"><span data-stu-id="f6ddf-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
 - <span data-ttu-id="f6ddf-786">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-786">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-787">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-787">Allowed From</span></span>

<span data-ttu-id="f6ddf-788">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-789">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-789">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="f6ddf-790">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="f6ddf-790">nx_http_server_create</span></span>

<span data-ttu-id="f6ddf-791">HTTP 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-791">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-792">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-792">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="f6ddf-793">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-793">Description</span></span>

<span data-ttu-id="f6ddf-794">이 서비스는 자체 ThreadX 스레드의 컨텍스트에서 실행되는 HTTP 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-794">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="f6ddf-795">선택적 *authentication_check* 및 request_notify 애플리케이션 콜백 루틴은 HTTP 서버의 기본 작업에 대한 애플리케이션 소프트웨어 제어를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-795">The optional *authentication_check* and request_notify application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-796">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-796">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-797">**http_server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-797">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="f6ddf-798">**http_server_name** HTTP 서버 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-798">**http_server_name** Pointer to HTTP Server’s name.</span></span>
 - <span data-ttu-id="f6ddf-799">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-799">**ip_ptr** Pointer to previously created IP instance.</span></span>
 - <span data-ttu-id="f6ddf-800">**media_ptr** 이전에 만든 FileX 미디어 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-800">**media_ptr** Pointer to previously created FileX media instance.</span></span>
 - <span data-ttu-id="f6ddf-801">**stack_ptr** HTTP 서버 스레드 스택 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-801">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
 - <span data-ttu-id="f6ddf-802">**stack_size** HTTP 서버 스레드 스택 크기에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-802">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
 - <span data-ttu-id="f6ddf-803">**authentication_check** 애플리케이션의 인증 확인 루틴에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-803">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="f6ddf-804">지정된 경우 이 루틴은 각 HTTP 클라이언트 요청에 대해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-804">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="f6ddf-805">이 매개 변수가 NULL이면 인증이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-805">If this parameter is NULL, no authentication will be performed.</span></span>
 - <span data-ttu-id="f6ddf-806">**request_notify** 애플리케이션의 요청 알림 루틴에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-806">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="f6ddf-807">지정된 경우 HTTP 서버에서 요청을 처리하기 전에 이 루틴이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-807">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="f6ddf-808">이렇게 하면 HTTP 클라이언트 요청을 완료하기 전에 리소스 이름을 리디렉션하거나 리소스 내의 필드를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-808">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-809">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-809">Return Values</span></span>

 - <span data-ttu-id="f6ddf-810">**NX_SUCCESS** (0x00) HTTP 서버를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="f6ddf-810">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
 - <span data-ttu-id="f6ddf-811">NX_PTR_ERROR (0x07) 잘못된 HTTP 서버, IP, 미디어, 스택 또는 패킷 풀 포인터</span><span class="sxs-lookup"><span data-stu-id="f6ddf-811">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
 - <span data-ttu-id="f6ddf-812">NX_HTTP_POOL_ERROR (0xE9) 풀의 패킷 페이로드가 전체 HTTP 요청을 포함할 만큼 충분히 크지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-812">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-813">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-813">Allowed From</span></span>

<span data-ttu-id="f6ddf-814">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-814">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-815">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-815">Example</span></span>

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="f6ddf-816">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="f6ddf-816">nx_http_server_delete</span></span>

<span data-ttu-id="f6ddf-817">HTTP 서버 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-817">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-818">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-818">Prototype</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="f6ddf-819">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-819">Description</span></span>

<span data-ttu-id="f6ddf-820">이 서비스는 이전에 만든 HTTP 서버 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-820">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-821">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-821">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-822">**http_server_ptr** HTTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-822">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-823">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-823">Return Values</span></span>

 - <span data-ttu-id="f6ddf-824">**NX_SUCCESS** (0x00) HTTP 서버를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-824">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
 - <span data-ttu-id="f6ddf-825">NX_PTR_ERROR (0x07) 잘못된 HTTP 서버 포인터</span><span class="sxs-lookup"><span data-stu-id="f6ddf-825">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
 - <span data-ttu-id="f6ddf-826">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-827">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-827">Allowed From</span></span>

<span data-ttu-id="f6ddf-828">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-828">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-829">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-829">Example</span></span>

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="f6ddf-830">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="f6ddf-830">nx_http_server_get_entity_content</span></span>

<span data-ttu-id="f6ddf-831">엔터티 데이터의 위치 및 길이를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-831">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-832">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-832">Prototype</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="f6ddf-833">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-833">Description</span></span>

<span data-ttu-id="f6ddf-834">이 서비스는 받은 클라이언트 메시지의 현재 다중 파트 엔터티 내에서 데이터 시작 위치 및 경계 문자열이 포함되지 않는 데이터 길이를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-834">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="f6ddf-835">내부적으로 HTTP 서버는 여러 엔터티가 있는 메시지에 대해 동일한 클라이언트 데이터그램에서 이 함수를 다시 호출할 수 있도록 자체 오프셋을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-835">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="f6ddf-836">패킷 포인터는 클라이언트 메시지가 다중 패킷 데이터그램인 다음 패킷으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-836">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-837">이 서비스를 사용하려면 NX_HTTP_MULTIPART_ENABLE을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-837">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="f6ddf-838">자세한 내용은 [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-838">See [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-839">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-839">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-840">**server_ptr** HTTP 서버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-840">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="f6ddf-841">**packet_pptr** 패킷 포인터의 위치에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-841">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="f6ddf-842">애플리케이션에서 이 패킷을 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-842">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="f6ddf-843">**available_offset** 패킷 선행 포인터에서 엔터티 데이터의 오프셋에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-843">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
 - <span data-ttu-id="f6ddf-844">**available_length** 엔터티 데이터의 길이에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-844">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-845">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-845">Return Values</span></span>

 - <span data-ttu-id="f6ddf-846">**NX_SUCCESS** (0x00) 엔터티 콘텐츠의 크기와 위치를 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-846">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
 - <span data-ttu-id="f6ddf-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) HTTP 서버 내부 다중 파트 표식에 대한 콘텐츠가 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server  internal multipart markers is already found</span></span>
 - <span data-ttu-id="f6ddf-848">NX_HTTP_ERROR (0xE0) 내부 HTTP 오류</span><span class="sxs-lookup"><span data-stu-id="f6ddf-848">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="f6ddf-849">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-849">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-850">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-850">Allowed From</span></span>

<span data-ttu-id="f6ddf-851">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-851">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-852">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-852">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT        offset, length;
NX_PACKET  *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
   the entity header to determine details about the multipart data. If
   successful, it then calls this service to get the location of entity data: */

status =  nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
&length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
   entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="f6ddf-853">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="f6ddf-853">nx_http_server_get_entity_header</span></span>

<span data-ttu-id="f6ddf-854">엔터티 헤더의 콘텐츠를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-854">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-855">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-855">Prototype</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="f6ddf-856">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-856">Description</span></span>

<span data-ttu-id="f6ddf-857">이 서비스는 지정된 버퍼에서 엔터티 헤더를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-857">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="f6ddf-858">다중 엔터티 헤더가 있는 클라이언트 데이터그램에서 다음 다중 파트 엔터티를 찾도록 HTTP 서버에서 내부적으로 자체 포인터를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-858">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="f6ddf-859">패킷 포인터는 클라이언트 메시지가 다중 패킷 데이터그램인 다음 패킷으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-859">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-860">이 서비스를 사용하려면 NX_HTTP_MULTIPART_ENABLE을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-860">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-861">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-861">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-862">**server_ptr** HTTP 서버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-862">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="f6ddf-863">**packet_pptr** 패킷 포인터의 위치에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-863">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="f6ddf-864">애플리케이션에서 이 패킷을 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-864">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="f6ddf-865">**entity_header_buffer** 엔터티 헤더를 저장하는 위치에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-865">**entity_header_buffer** Pointer to location to store entity header</span></span>
 - <span data-ttu-id="f6ddf-866">**buffer_size** 입력 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-866">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-867">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-867">Return Values</span></span>

 - <span data-ttu-id="f6ddf-868">**NX_SUCCESS** (0x00) 엔터티 헤더를 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-868">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
 - <span data-ttu-id="f6ddf-869">**NX_HTTP_NOT_FOUND** **(0xE6)** 엔터티 헤더 필드를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-869">**NX_HTTP_NOT_FOUND** **(0xE6)** Entity header field not found</span></span>
 - <span data-ttu-id="f6ddf-870">**NX_HTTP_TIMEOUT** **(0xE1)** 다중 패킷 클라이언트 메시지에 대한 다음 패킷을 받는 시간이 만료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-870">**NX_HTTP_TIMEOUT** **(0xE1)** Time expired to receive next packet for multipacket client message</span></span>
 - <span data-ttu-id="f6ddf-871">NX_HTTP_ERROR (0xE0) 내부 HTTP 오류</span><span class="sxs-lookup"><span data-stu-id="f6ddf-871">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="f6ddf-872">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-872">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-873">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-873">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-874">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-874">Allowed From</span></span>

<span data-ttu-id="f6ddf-875">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-875">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-876">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-876">Example</span></span>

```c
/* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, NX_PACKET *packet_ptr)
      {

        NX_PACKET   *sresp_packet_ptr;
        UINT        offset, length;
        NX_PACKET   *response_pkt;
        UCHAR       buffer[1440];

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
                         "Server: NetXDuo HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
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
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="f6ddf-877">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="f6ddf-877">nx_http_server_gmt_callback_set</span></span>

<span data-ttu-id="f6ddf-878">GMT 날짜 및 시간을 가져오는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-878">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-879">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-879">Prototype</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="f6ddf-880">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-880">Description</span></span>

<span data-ttu-id="f6ddf-881">이 서비스는 이전에 만든 HTTP 서버에서 GMT 날짜 및 시간을 가져오는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-881">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="f6ddf-882">이 서비스는 HTTP 서버가 클라이언트에 대한 HTTP 서버 응답에 헤더를 만들 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-882">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-883">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-883">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-884">**server_ptr** HTTP 서버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-884">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="f6ddf-885">**gmt_getv** GMT 콜백에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-885">**gmt_getv** Pointer to GMT callback</span></span>
 - <span data-ttu-id="f6ddf-886">**datev** 검색된 날짜에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-886">**datev** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-887">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-887">Return Values</span></span>

 - <span data-ttu-id="f6ddf-888">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-888">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="f6ddf-889">NX_PTR_ERROR (0x07) 잘못된 패킷 또는 매개 변수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-889">NX_PTR_ERROR (0x07)  Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-890">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-890">Allowed From</span></span>

<span data-ttu-id="f6ddf-891">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-892">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-892">Example</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the GMT
   retrieve callback: */

status =  nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
   response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="f6ddf-893">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="f6ddf-893">nx_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="f6ddf-894">잘못된 사용자/암호를 처리하는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-894">Set the callback to to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-895">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-895">Prototype</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="f6ddf-896">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-896">Description</span></span>

<span data-ttu-id="f6ddf-897">이 서비스는 다이제스트 또는 기본 인증을 통해 클라이언트 GET, PUT 또는 DELETE 요청에서 잘못된 사용자 이름 및 암호를 받을 때 호출되는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-897">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="f6ddf-898">HTTP 서버는 이전에 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-898">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-899">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-899">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-900">**server_ptr** HTTP 서버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-900">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="f6ddf-901">**invalid_username_password_callback** 잘못된 사용자/전달 콜백에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-901">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
 - <span data-ttu-id="f6ddf-902">**resource** 클라이언트에서 지정한 리소스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-902">**resource** Pointer to the resource specified by the client</span></span>
 - <span data-ttu-id="f6ddf-903">**client_address** 클라이언트 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-903">**client_address** Pointer to client address.</span></span> <span data-ttu-id="f6ddf-904">IPv4 또는 IPv6일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-904">Can be IPv4 or IPv6</span></span>
 - <span data-ttu-id="f6ddf-905">**request_type** 클라이언트 요청 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-905">**request_type** Indicates client request type.</span></span> <span data-ttu-id="f6ddf-906">다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-906">May be:</span></span>
    - <span data-ttu-id="f6ddf-907">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="f6ddf-907">NX_HTTP_SERVER_GET_REQUEST</span></span>
    - <span data-ttu-id="f6ddf-908">NX_HTTP_SERVER_POST_REQUEST</span><span class="sxs-lookup"><span data-stu-id="f6ddf-908">NX_HTTP_SERVER_POST_REQUEST</span></span>
    - <span data-ttu-id="f6ddf-909">NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="f6ddf-909">NX_HTTP_SERVER_HEAD_REQUEST</span></span>
    - <span data-ttu-id="f6ddf-910">NX_HTTP_SERVER_PUT_REQUEST</span><span class="sxs-lookup"><span data-stu-id="f6ddf-910">NX_HTTP_SERVER_PUT_REQUEST</span></span>
    - <span data-ttu-id="f6ddf-911">NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="f6ddf-911">NX_HTTP_SERVER_DELETE_REQUEST</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-912">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-912">Return Values</span></span>

 - <span data-ttu-id="f6ddf-913">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-913">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="f6ddf-914">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-914">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-915">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-915">Allowed From</span></span>

<span data-ttu-id="f6ddf-916">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-916">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-917">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-917">Example</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                         NXD_ADDRESS *client_address,
                                         UINT   request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the invalid
   username password callback: */

status =  nx_http_server_gmt_callback_set(&my_server,
                                          invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
   will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="f6ddf-918">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="f6ddf-918">nx_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="f6ddf-919">HTML에 대한 추가 MIME 맵을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-919">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-920">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-920">Prototype</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="f6ddf-921">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-921">Description</span></span>

<span data-ttu-id="f6ddf-922">이 서비스를 통해 HTTP 애플리케이션 개발자는 NetX Duo HTTP 서버에서 제공하는 기본 MIME 형식에서 추가 MIME 형식을 추가할 수 있습니다(정의된 형식 목록은 *nx_http_server_get_type* 참조).</span><span class="sxs-lookup"><span data-stu-id="f6ddf-922">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX Duo HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="f6ddf-923">클라이언트 요청(예: GET 요청)이 수신된 경우 HTTP 서버에서 우선적으로 추가 MIME 맵 집합을 사용하여 HTTP 헤더에서 요청된 파일 형식을 구문 분석하고, 일치하는 항목이 없는 경우 HTTP 서버의 기본 MIME 맵에서 일치 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-923">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="f6ddf-924">일치하는 항목이 없으면 MIME 형식은 기본적으로 "텍스트/일반"으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-924">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="f6ddf-925">요청 알림 함수가 HTTP 서버에 등록된 경우 요청 알림 콜백에서 *nx_http_server_type_retrieve()* 를 호출하여 파일 형식을 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-925">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_retrieve()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-926">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-926">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-927">**server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-927">**server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="f6ddf-928">**mime_maps** MIME 맵 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-928">**mime_maps** Pointer to a MIME map array</span></span>
 - <span data-ttu-id="f6ddf-929">**mime_map_num** 배열의 MIME 맵 수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-929">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-930">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-930">Return Values</span></span>

 - <span data-ttu-id="f6ddf-931">**NX_SUCCESS** (0x00) HTTP 서버 MIME 맵을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-931">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
 - <span data-ttu-id="f6ddf-932">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-932">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-933">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-933">Allowed From</span></span>

<span data-ttu-id="f6ddf-934">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-934">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-935">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-935">Example</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc",      "yourtype/abc"},
    {"xyz",      "mytype/xyz"},
};

status =  nx_http_server_mime_maps_additional_set(&my_server,
                                                  &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP  
  server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="f6ddf-936">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="f6ddf-936">nx_http_server_packet_content_find</span></span>

<span data-ttu-id="f6ddf-937">콘텐츠 길이를 추출하고 데이터 시작에 대한 포인터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-937">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-938">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-938">Prototype</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="f6ddf-939">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-939">Description</span></span>

<span data-ttu-id="f6ddf-940">이 서비스는 HTTP 헤더에서 콘텐츠 길이를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-940">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="f6ddf-941">또한 제공된 패킷을 다음과 같이 업데이트합니다. 패킷 선행 포인터(쓸 패킷 버퍼의 시작 위치)가 HTTP 헤더를 방금 전달한 HTTP 콘텐츠(데이터)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-941">It also  updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="f6ddf-942">현재 패킷에서 콘텐츠의 시작 위치를 찾을 수 없는 경우 함수에서 NX_HTTP_SERVER_TIMEOUT_RECEIVE 대기 옵션을 사용하여 다음 패킷을 받을 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-942">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-943">이 서비스는 엔터티 헤더를 지나 선행 포인터를 수정하므로 *nx_http_server_get_entity_header* 를 호출하기 전에 호출하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-943">This should not be called before calling *nx_http_server_get_entity_header* because it modifies the prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-944">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-944">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-945">**server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-945">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="f6ddf-946">**packet_ptr** 업데이트된 선행 포인터를 사용하여 패킷을 반환하는 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-946">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
 - <span data-ttu-id="f6ddf-947">**content_length** 추출된 ```content_length```에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-947">**content_length** Pointer to extracted ```content_length```</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-948">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-948">Return Values</span></span>

 - <span data-ttu-id="f6ddf-949">**NX_SUCCESS** (0x00) HTTP 콘텐츠 길이가 있고 패킷을 성공적으로 업데이트함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-949">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
 - <span data-ttu-id="f6ddf-950">**NX_HTTP_TIMEOUT** (0xE1) 다음 패킷을 기다리는 시간이 만료됨</span><span class="sxs-lookup"><span data-stu-id="f6ddf-950">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="f6ddf-951">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-951">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-952">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-952">Allowed From</span></span>

<span data-ttu-id="f6ddf-953">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-953">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-954">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-954">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function
registered with the HTTP server. */

UINT content_length;

status =  nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                             &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
   and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="f6ddf-955">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="f6ddf-955">nx_http_server_packet_get</span></span>

<span data-ttu-id="f6ddf-956">다음 HTTP 패킷을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-956">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-957">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-957">Prototype</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="f6ddf-958">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-958">Description</span></span>

<span data-ttu-id="f6ddf-959">이 서비스는 HTTP 서버 소켓에서 수신된 다음 패킷을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-959">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="f6ddf-960">패킷 수신 대기 옵션은 NX_HTTP_SERVER_TIMEOUT_RECEIVE입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-960">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-961">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-961">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-962">**server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-962">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="f6ddf-963">**packet_ptr** 받은 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-963">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-964">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-964">Return Values</span></span>

 - <span data-ttu-id="f6ddf-965">**NX_SUCCESS** (0x00) 다음 패킷을 성공적으로 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-965">**NX_SUCCESS** (0x00) Successfully received next packet</span></span>
 - <span data-ttu-id="f6ddf-966">**NX_HTTP_TIMEOUT** (0xE1) 다음 패킷을 기다리는 시간이 만료됨</span><span class="sxs-lookup"><span data-stu-id="f6ddf-966">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="f6ddf-967">NX_PTR_ERROR (0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-967">NX_PTR_ERROR (0x07)  Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-968">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-968">Allowed From</span></span>

<span data-ttu-id="f6ddf-969">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-969">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-970">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-970">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="f6ddf-971">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="f6ddf-971">nx_http_server_param_get</span></span>

<span data-ttu-id="f6ddf-972">요청에서 매개 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-972">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-973">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-973">Prototype</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="f6ddf-974">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-974">Description</span></span>

<span data-ttu-id="f6ddf-975">이 서비스는 제공된 요청 패킷에서 지정된 HTTP URL 매개 변수를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-975">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="f6ddf-976">요청된 HTTP 매개 변수가 없는 경우 이 루틴에서 NX_HTTP_NOT_FOUND 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-976">If the requested HTTP parameter is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="f6ddf-977">이 루틴은 HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create*)에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-977">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-978">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-978">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-979">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-979">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="f6ddf-980">애플리케이션에서 이 패킷을 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-980">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="f6ddf-981">**param_number** 매개 변수 목록에서 왼쪽에서 오른쪽으로 0에서 시작하는 매개 변수의 논리적 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-981">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
 - <span data-ttu-id="f6ddf-982">**param_ptr** 매개 변수를 복사하는 대상 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-982">**param_ptr** Destination area to copy the parameter.</span></span>
 - <span data-ttu-id="f6ddf-983">**max_param_size** 매개 변수 대상 영역의 최대 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-983">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-984">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-984">Return Values</span></span>

 - <span data-ttu-id="f6ddf-985">**NX_SUCCESS** (0x00) HTTP 서버 매개 변수를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="f6ddf-985">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
 - <span data-ttu-id="f6ddf-986">**NX_HTTP_NOT_FOUND** (0xE6) 지정된 매개 변수가 없음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-986">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
 - <span data-ttu-id="f6ddf-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) 요청 매개 변수가 제대로 종료되지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
 - <span data-ttu-id="f6ddf-988">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-988">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-989">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-989">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-990">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-990">Allowed From</span></span>

<span data-ttu-id="f6ddf-991">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-991">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-992">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-992">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="f6ddf-993">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="f6ddf-993">nx_http_server_query_get</span></span>

<span data-ttu-id="f6ddf-994">요청에서 쿼리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-994">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-995">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-995">Prototype</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="f6ddf-996">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-996">Description</span></span>

<span data-ttu-id="f6ddf-997">이 서비스는 제공된 요청 패킷에서 지정된 HTTP URL 쿼리를 검색하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-997">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="f6ddf-998">요청된 HTTP 쿼리가 없는 경우 이 루틴에서 NX_HTTP_NOT_FOUND 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-998">If the requested HTTP query is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="f6ddf-999">이 루틴은 HTTP 서버를 만드는 동안 지정된 애플리케이션의 요청 알림 콜백(*nx_http_server_create*)에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-999">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-1000">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1000">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-1001">**packet_ptr** HTTP 클라이언트 요청 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1001">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="f6ddf-1002">애플리케이션에서 이 패킷을 해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1002">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="f6ddf-1003">**query_number** 쿼리 목록에서 왼쪽에서 오른쪽으로 0에서 시작하는 매개 변수의 논리적 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1003">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
 - <span data-ttu-id="f6ddf-1004">**query_ptr** 쿼리를 복사할 대상 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1004">**query_ptr** Destination area to copy the query.</span></span>
 - <span data-ttu-id="f6ddf-1005">**max_query_size** 쿼리 대상 영역의 최대 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1005">**max_query_size** Maximum size of the query destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-1006">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1006">Return Values</span></span>

 - <span data-ttu-id="f6ddf-1007">**NX_SUCCESS** (0x00) HTTP 서버 쿼리를 성공적으로 가져옴</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1007">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
 - <span data-ttu-id="f6ddf-1008">**NX_HTTP_FAILED** (0xE2) 쿼리 크기가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1008">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
 - <span data-ttu-id="f6ddf-1009">**NX_HTTP_NOT_FOUND** (0xE6) 지정된 쿼리가 없음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1009">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
 - <span data-ttu-id="f6ddf-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) 쿼리가 클라이언트 요청에 없음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
 - <span data-ttu-id="f6ddf-1011">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1011">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-1012">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1012">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-1013">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1013">Allowed From</span></span>

<span data-ttu-id="f6ddf-1014">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1014">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-1015">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1015">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a><span data-ttu-id="f6ddf-1016">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1016">nx_http_server_start</span></span>

<span data-ttu-id="f6ddf-1017">HTTP 서버를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1017">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-1018">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1018">Prototype</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="f6ddf-1019">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1019">Description</span></span>

<span data-ttu-id="f6ddf-1020">이 서비스는 이전에 만든 HTTP 서버 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1020">This service starts the previously create HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-1021">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1021">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-1022">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1022">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-1023">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1023">Return Values</span></span>

 - <span data-ttu-id="f6ddf-1024">**NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1024">**NX_SUCCESS** (0x00) Successful Server start</span></span>
 - <span data-ttu-id="f6ddf-1025">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1025">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-1026">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1026">Allowed From</span></span>

<span data-ttu-id="f6ddf-1027">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1027">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-1028">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1028">Example</span></span>

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="f6ddf-1029">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1029">nx_http_server_stop</span></span>

<span data-ttu-id="f6ddf-1030">HTTP 서버를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1030">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-1031">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1031">Prototype</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="f6ddf-1032">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1032">Description</span></span>

<span data-ttu-id="f6ddf-1033">이 서비스는 이전에 만든 HTTP 서버 인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1033">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="f6ddf-1034">이 루틴은 HTTP 서버 인스턴스를 삭제하기 전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1034">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-1035">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1035">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-1036">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1036">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-1037">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1037">Return Values</span></span>

 - <span data-ttu-id="f6ddf-1038">**NX_SUCCESS** (0x00) 서버를 성공적으로 중지했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1038">**NX_SUCCESS** (0x00) Successful Server stop</span></span>
 - <span data-ttu-id="f6ddf-1039">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1039">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-1040">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1040">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-1041">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1041">Allowed From</span></span>

<span data-ttu-id="f6ddf-1042">스레드</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1042">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-1043">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1043">Example</span></span>

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="f6ddf-1044">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1044">nx_http_server_type_get</span></span>

<span data-ttu-id="f6ddf-1045">클라이언트 HTTP 요청에서 파일 형식을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1045">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-1046">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1046">Prototype</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a><span data-ttu-id="f6ddf-1047">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1047">Description</span></span>

> [!NOTE]
> <span data-ttu-id="f6ddf-1048">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1048">This service is deprecated.</span></span> <span data-ttu-id="f6ddf-1049">사용자는 *nx_http_server_type_retrieve()* 서비스를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1049">Users are encouraged to use the service *nx_http_server_type_retrieve()*.</span></span>

<span data-ttu-id="f6ddf-1050">이 서비스는 http_type_string 버퍼에서 HTTP 요청 유형을 추출하고, 입력 버퍼 이름(일반적으로 URL)에서 반환 값의 길이를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1050">This service extracts the HTTP request type in the buffer http_type_string and its length in the return value from the input buffer name, usually the URL.</span></span> <span data-ttu-id="f6ddf-1051">MIME 맵이 없는 경우 기본적으로 "텍스트/일반" 형식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1051">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="f6ddf-1052">그렇지 않으면 추출된 형식을 HTTP 서버 기본 MIME 맵과 비교하여 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1052">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="f6ddf-1053">NetX Duo HTTP 서버의 기본 MIME 맵은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1053">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="f6ddf-1054">**html** text/html</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1054">**html** text/html</span></span>
 - <span data-ttu-id="f6ddf-1055">**htm** text/html</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1055">**htm** text/html</span></span>
 - <span data-ttu-id="f6ddf-1056">**txt** text/plain</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1056">**txt** text/plain</span></span>
 - <span data-ttu-id="f6ddf-1057">**gif** image/gif</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1057">**gif** image/gif</span></span>
 - <span data-ttu-id="f6ddf-1058">**jpg** image/jpeg</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1058">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="f6ddf-1059">**ico** image/x-icon</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1059">**ico** image/x-icon</span></span>

<span data-ttu-id="f6ddf-1060">제공되는 경우 사용자 정의 추가 MIME 맵 집합도 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1060">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="f6ddf-1061">사용자 정의 맵에 대한 자세한 내용은 *nx_http_server_mime_maps_addtional_set()* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1061">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="f6ddf-1062">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1062">This service is deprecated.</span></span> <span data-ttu-id="f6ddf-1063">개발자는 *nx_http_server_type_get_extended()* 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1063">Developers are encouraged to migrate to *nx_http_server_type_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-1064">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1064">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-1065">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1065">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="f6ddf-1066">**name** 검색할 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1066">**name Pointer** to buffer to search</span></span>
 - <span data-ttu-id="f6ddf-1067">**http_type_string** (추출된 HTML 형식에 대한 포인터)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1067">**http_type_string** (Pointer to extracted HTML type)</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-1068">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1068">Return Values</span></span>

 - <span data-ttu-id="f6ddf-1069">**문자열 길이(바이트)** 0이 아닌 값은 성공입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1069">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="f6ddf-1070">0은 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1070">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-1071">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1071">Allowed From</span></span>

<span data-ttu-id="f6ddf-1072">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1072">Application</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-1073">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1073">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="f6ddf-1074">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1074">nx_http_server_type_get_extended</span></span>

<span data-ttu-id="f6ddf-1075">클라이언트 HTTP 요청에서 파일 형식을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1075">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-1076">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1076">Prototype</span></span>

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a><span data-ttu-id="f6ddf-1077">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1077">Description</span></span>

<span data-ttu-id="f6ddf-1078">이 서비스는 *http_type_string* 버퍼에서 HTTP 요청 유형을 추출하고, 입력 버퍼 *이름*(일반적으로 URL)에서 반환 값의 길이를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1078">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="f6ddf-1079">MIME 맵이 없는 경우 기본적으로 "텍스트/일반" 형식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1079">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="f6ddf-1080">그렇지 않으면 추출된 형식을 HTTP 서버 기본 MIME 맵과 비교하여 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1080">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="f6ddf-1081">NetX Duo HTTP 서버의 기본 MIME 맵은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1081">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="f6ddf-1082">**html** text/html</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1082">**html** text/html</span></span>
 - <span data-ttu-id="f6ddf-1083">**htm** text/html</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1083">**htm** text/html</span></span>
 - <span data-ttu-id="f6ddf-1084">**txt** text/plain</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1084">**txt** text/plain</span></span>
 - <span data-ttu-id="f6ddf-1085">**gif** image/gif</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1085">**gif** image/gif</span></span>
 - <span data-ttu-id="f6ddf-1086">**jpg** image/jpeg</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1086">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="f6ddf-1087">**ico** image/x-icon</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1087">**ico** image/x-icon</span></span>

<span data-ttu-id="f6ddf-1088">제공되는 경우 사용자 정의 추가 MIME 맵 집합도 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1088">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="f6ddf-1089">사용자 정의 맵에 대한 자세한 내용은 *nx_http_server_mime_maps_addtional_set()* 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1089">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="f6ddf-1090">이 서비스는 *nx_http_server_type_get()* 을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1090">This service replaces *nx_http_server_type_get()*.</span></span> <span data-ttu-id="f6ddf-1091">이 버전은 추가 길이 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1091">This version supplies additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-1092">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1092">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-1093">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1093">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="f6ddf-1094">**name** 검색할 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1094">**name** Pointer to buffer to search</span></span>
 - <span data-ttu-id="f6ddf-1095">**name_length** 검색할 버퍼의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1095">**name_length** Length of buffer to search</span></span>
 - <span data-ttu-id="f6ddf-1096">**http_type_string** (추출된 HTML 형식에 대한 포인터)</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1096">**http_type_string** (Pointer to extracted HTML type)</span></span>
 - <span data-ttu-id="f6ddf-1097">**http_type_string_max_size** http_type_string 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1097">**http_type_string_max_size** Size of the http_type_string buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-1098">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1098">Return Values</span></span>

 - <span data-ttu-id="f6ddf-1099">**문자열 길이(바이트)** 0이 아닌 값은 성공입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1099">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="f6ddf-1100">0은 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1100">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-1101">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1101">Allowed From</span></span>

<span data-ttu-id="f6ddf-1102">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1102">Application</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-1103">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1103">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

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
    string_length =  nx_http_server_type_get_extended(&my_server,
               my_server.nx_http_server_request_resource, resource_length,
               temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="f6ddf-1104">자세한 예제는 [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header)에 대한 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1104">For a more detailed example, see the description for [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="f6ddf-1105">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1105">nx_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="f6ddf-1106">다이제스트 인증 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1106">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-1107">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1107">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="f6ddf-1108">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1108">Description</span></span>

<span data-ttu-id="f6ddf-1109">이 서비스는 다이제스트 인증을 수행할 때 호출되는 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1109">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-1110">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1110">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-1111">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1111">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="f6ddf-1112">**digest_authenticate_callback** 다이제스트 인증 콜백에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1112">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-1113">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1113">Return Values</span></span>

 - <span data-ttu-id="f6ddf-1114">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1114">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="f6ddf-1115">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1115">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="f6ddf-1116">NX_NOT_SUPPORTED (0x4B) 다이제스트 인증을 사용하도록 설정되지 않음</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1116">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-1117">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1117">Allowed From</span></span>

<span data-ttu-id="f6ddf-1118">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1118">Application</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-1119">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1119">Example</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                  CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
                                  CHAR *authorization_uri, CHAR *authorization_nc,
                                  CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the digest authenticate callback: */

status =  nx_http_server_digest_authenticate_notify_set (&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
   will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="f6ddf-1120">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1120">nx_http_server_authentication_check_set</span></span>

<span data-ttu-id="f6ddf-1121">인증 확인 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1121">Set authentication checking callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="f6ddf-1122">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1122">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="f6ddf-1123">Description</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1123">Description</span></span>

<span data-ttu-id="f6ddf-1124">이 서비스는 인증 확인 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1124">This service sets the callback function of authentication checking.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6ddf-1125">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1125">Input Parameters</span></span>

 - <span data-ttu-id="f6ddf-1126">**http_server_ptr** HTTP 서버 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1126">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="f6ddf-1127">**authentication_check_extended** 애플리케이션의 인증 확인에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1127">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

### <a name="return-values"></a><span data-ttu-id="f6ddf-1128">반환 값</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1128">Return Values</span></span>

 - <span data-ttu-id="f6ddf-1129">**NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1129">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="f6ddf-1130">NX_PTR_ERROR (0x07) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1130">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6ddf-1131">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1131">Allowed From</span></span>

<span data-ttu-id="f6ddf-1132">애플리케이션</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1132">Application</span></span>

### <a name="example"></a><span data-ttu-id="f6ddf-1133">예제</span><span class="sxs-lookup"><span data-stu-id="f6ddf-1133">Example</span></span>

```c
static UINT  authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                           UINT request_type, CHAR *resource,
                                           CHAR **name, UINT *name_length,
                                           CHAR **password, UINT *password_length,
                                           CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
       requests and resources. */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the
   authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                         authentication_check_extended);
```
