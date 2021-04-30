---
title: 챕터 1 - NetX HTTP 소개
description: 이 문서에서는 HTTP가 웹에서 콘텐츠를 전송 하기 위해 설계된 프로토콜인 이유를 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6137cc0d8deb753d784be844d5abc7778dd62295
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811533"
---
# <a name="chapter-1---introduction-to-netx-http"></a><span data-ttu-id="9be78-103">챕터 1 - NetX HTTP 소개</span><span class="sxs-lookup"><span data-stu-id="9be78-103">Chapter 1 - Introduction to NetX HTTP</span></span>

<span data-ttu-id="9be78-104">HTTP(Hypertext Transfer Protocol)는 웹에서 콘텐츠를 전송하기 위해 설계된 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-104">The Hypertext Transfer Protocol (HTTP) is a protocol designed for transferring content on the Web.</span></span> <span data-ttu-id="9be78-105">HTTP는 콘텐츠 전송 기능을 수행하기 위해 신뢰할 수 있는 TCP(Transmission Control Protocol) 서비스를 사용하는 간단한 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-105">HTTP is a simple protocol that utilizes reliable Transmission Control Protocol (TCP) services to perform its content transfer function.</span></span> <span data-ttu-id="9be78-106">따라서 HTTP는 매우 안정적인 콘텐츠 전송 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-106">Because of this, HTTP is a highly reliable content transfer protocol.</span></span> <span data-ttu-id="9be78-107">HTTP는 가장 많이 사용되는 애플리케이션 프로토콜 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-107">HTTP is one of the most used application protocols.</span></span> <span data-ttu-id="9be78-108">웹의 모든 작업에 HTTP 프로토콜이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-108">All operations on the Web utilize the HTTP protocol.</span></span>

## <a name="http-requirements"></a><span data-ttu-id="9be78-109">HTTP 요구 사항</span><span class="sxs-lookup"><span data-stu-id="9be78-109">HTTP Requirements</span></span>

<span data-ttu-id="9be78-110">NetX HTTP 패키지가 올바르게 작동하기 위해서는 NetX(버전 5.2 이상)가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-110">In order to function properly, the NetX HTTP package requires that a NetX (version 5.2 or later) is installed.</span></span> <span data-ttu-id="9be78-111">또한 IP 인스턴스가 이미 생성되어 있어야 하며, 해당 IP 인스턴스에서 TCP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-111">In addition, an IP instance must already be created and TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="9be78-112">**챕터 2** 에서 “작은 예제 시스템” 섹션의 데모 파일은 이를 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-112">The demo file in section “Small Example System” in **Chapter 2** will demonstrate how this is done.</span></span>

<span data-ttu-id="9be78-113">NetX HTTP 패키지의 HTTP 클라이언트 부분에는 추가 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-113">The HTTP Client portion of the NetX HTTP package has no further requirements.</span></span>

<span data-ttu-id="9be78-114">NetX HTTP 패키지의 HTTP 서버 부분에는 여러 추가 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-114">The HTTP Server portion of the NetX HTTP package has several additional requirements.</span></span> <span data-ttu-id="9be78-115">먼저 모든 클라이언트 HTTP 요청을 처리하려면 TCP의 *잘 알려진 포트 80* 에 대한 완전한 액세스 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-115">First, it requires complete access to TCP *well-known port 80* for handling all Client HTTP requests.</span></span> <span data-ttu-id="9be78-116">HTTP 서버는 또한 FileX 포함된 파일 시스템에 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-116">The HTTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="9be78-117">FileX를 사용할 수 없으면 사용자가 사용된 FileX 부분을 자신의 고유 환경으로 이식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-117">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="9be78-118">이에 대해서는 이 가이드의 이후 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-118">This is discussed in later sections of this guide.</span></span>

## <a name="http-constraints"></a><span data-ttu-id="9be78-119">HTTP 제약 조건</span><span class="sxs-lookup"><span data-stu-id="9be78-119">HTTP Constraints</span></span> 

<span data-ttu-id="9be78-120">NetX HTTP 프로토콜은 HTTP 1.0 표준을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-120">The NetX HTTP protocol implements the HTTP 1.0 standard.</span></span> <span data-ttu-id="9be78-121">그러나 다음과 같은 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-121">However, there are following constraints:</span></span>

1.  <span data-ttu-id="9be78-122">영구 연결이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-122">Persistent connections are not supported</span></span>

2.  <span data-ttu-id="9be78-123">요청 파이프라인이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-123">Request pipelining is not supported</span></span>

3.  <span data-ttu-id="9be78-124">HTTP 서버는 기본 및 MD5 다이제스트 인증을 모두 지원하지만 MD5-sess는 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-124">The HTTP Server supports both basic and MD5 digest authentication, but not MD5-sess.</span></span> <span data-ttu-id="9be78-125">현재 HTTP 클라이언트는 기본 인증만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-125">At present, the HTTP Client supports only basic authentication.</span></span>

4.  <span data-ttu-id="9be78-126">콘텐츠 압축은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-126">No content compression is supported.</span></span>

5.  <span data-ttu-id="9be78-127">TRACE, OPTIONS 및 CONNECT 요청은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-127">TRACE, OPTIONS, and CONNECT requests are not supported.</span></span>

6.  <span data-ttu-id="9be78-128">HTTP 서버 또는 클라이언트와 연결된 패킷 풀은 전체 HTTP 헤더를 저장하도록 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-128">The packet pool associated with the HTTP Server or Client must be large enough to hold the complete HTTP header.</span></span>

7.  <span data-ttu-id="9be78-129">HTTP 클라이언트 서비스는 콘텐츠 전송용으로만 사용되며, 이 패키지에 제공되는 디스플레이 유틸리티는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-129">HTTP Client services are for content transfer only—there are no display utilities provided in this package.</span></span>

## <a name="http-url-resource-names"></a><span data-ttu-id="9be78-130">HTTP URL(리소스 이름)</span><span class="sxs-lookup"><span data-stu-id="9be78-130">HTTP URL (Resource Names)</span></span>

<span data-ttu-id="9be78-131">HTTP 프로토콜은 웹에서 콘텐츠를 전송하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-131">The HTTP protocol is designed to transfer content on Web.</span></span> <span data-ttu-id="9be78-132">요청된 콘텐츠는 URL(Universal Resource Locator)로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-132">The requested content is specified by the Universal Resource Locator (URL).</span></span> <span data-ttu-id="9be78-133">이는 모든 HTTP 요청의 기본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-133">This is the primary component of every HTTP request.</span></span> <span data-ttu-id="9be78-134">URL은 항상 “/” 문자로 시작하며 일반적으로 HTTP 서버에 있는 파일을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-134">URLs always start with a “/” character and typically correspond to files on the HTTP Server.</span></span> <span data-ttu-id="9be78-135">일반적인 HTTP 파일 확장자는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-135">Common HTTP file extensions are shown below:</span></span>

- <span data-ttu-id="9be78-136">**.htm(또는 .html)** HTML(Hypertext Markup Language)</span><span class="sxs-lookup"><span data-stu-id="9be78-136">**.htm (or .html)** Hypertext Markup Language (HTML)</span></span>
- <span data-ttu-id="9be78-137">**.txt** 일반 ASCII 텍스트</span><span class="sxs-lookup"><span data-stu-id="9be78-137">**.txt** Plain ASCII text</span></span>
- <span data-ttu-id="9be78-138">**.gif** 이진 GIF 이미지</span><span class="sxs-lookup"><span data-stu-id="9be78-138">**.gif** Binary GIF image</span></span>
- <span data-ttu-id="9be78-139">**.xbm** 이진 Xbitmap 이미지</span><span class="sxs-lookup"><span data-stu-id="9be78-139">**.xbm** Binary Xbitmap image</span></span>

## <a name="http-client-requests"></a><span data-ttu-id="9be78-140">HTTP 클라이언트 요청</span><span class="sxs-lookup"><span data-stu-id="9be78-140">HTTP Client Requests</span></span>

<span data-ttu-id="9be78-141">HTTP에는 웹 콘텐츠 요청을 위한 간단한 메커니즘이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-141">The HTTP has a simple mechanism for requesting Web content.</span></span> <span data-ttu-id="9be78-142">기본적으로 TCP의 *잘 알려진 포트 80* 에서 연결이 성공적으로 설정된 후 클라이언트에서 실행되는 표준 HTTP 명령 세트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-142">There is basically a set of standard HTTP commands that are issued by the Client after a connection has been successfully established on the TCP *well-known port 80*.</span></span> <span data-ttu-id="9be78-143">다음은 기본 HTTP 명령 중 일부를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-143">The following shows some of the basic HTTP commands:</span></span>

- <span data-ttu-id="9be78-144">GET resource HTTP/1.0 *지정된 리소스를 가져옵니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-144">GET resource HTTP/1.0 *Get the specified resource*</span></span>
- <span data-ttu-id="9be78-145">POST resource HTTP/1.0 *지정된 리소스를 가져오고 연결된 입력을 HTTP 서버에 전달합니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-145">POST resource HTTP/1.0 *Get the specified resource and pass attached input to the HTTP Server*</span></span>
- <span data-ttu-id="9be78-146">HEAD resource HTTP/1.0 *GET와 비슷하게 취급되지만 콘텐츠가 HTTP 서버에서 반환되지 않습니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-146">HEAD resource HTTP/1.0 *Treated like a GET but not content is returned by the HTTP Server*</span></span>
- <span data-ttu-id="9be78-147">PUT resource HTTP/1.0 *리소스를 HTTP 서버에 배치합니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-147">PUT resource HTTP/1.0 *Place resource on HTTP Server*</span></span>
- <span data-ttu-id="9be78-148">DELETE resource HTTP/1.0 *서버에서 리소스를 삭제합니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-148">DELETE resource HTTP/1.0 *Delete resource on the Server*</span></span>

<span data-ttu-id="9be78-149">이러한 ASCII 명령은 HTTP 서버로 HTTP 작업을 수행하기 위해 웹 브라우저 및 NetX HTTP 클라이언트 서비스에서 내부적으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-149">These ASCII commands are generated internally by Web browsers and the NetX HTTP Client services to perform HTTP operations with an HTTP Server.</span></span>

>[!NOTE] 
> <span data-ttu-id="9be78-150">HTTP 클라이언트 애플리케이션의 기본 연결 포트는 80입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-150">The HTTP Client application default to the connect port of 80.</span></span> <span data-ttu-id="9be78-151">그러나 *nx_http_client_set_connect_port* 서비스를 사용하여 런타임에 HTTP 서버에 대한 연결 포트를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-151">However, it can change the connect port to the HTTP Server at runtime using the *nx_http_client_set_connect_port* service.</span></span> <span data-ttu-id="9be78-152">이 서비스에 대한 자세한 내용은 챕터 4를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9be78-152">See Chapter 4 for more details of this service.</span></span> <span data-ttu-id="9be78-153">이는 때때로 클라이언트 연결에 대체 포트를 사용하는 웹 서버를 수용하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-153">This is to accommodate web servers that occasionally use alternate ports for Client connections.</span></span>

## <a name="http-server-responses"></a><span data-ttu-id="9be78-154">HTTP 서버 응답</span><span class="sxs-lookup"><span data-stu-id="9be78-154">HTTP Server Responses</span></span>

<span data-ttu-id="9be78-155">HTTP 서버는 동일한 *잘 알려진 TCP 포트 80* 을 사용하여 클라이언트 명령 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-155">The HTTP Server utilizes the same *well-known TCP port 80* to send Client command responses.</span></span> <span data-ttu-id="9be78-156">HTTP 서버는 클라이언트 명령을 처리한 후 3자릿수 숫자 상태 코드가 포함된 ASCII 응답 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-156">Once the HTTP Server processes the Client command, it returns an ASCII response string that includes a 3-digit numeric status code.</span></span> <span data-ttu-id="9be78-157">이 숫자 응답은 HTTP 클라이언트 소프트웨어가 작업 성공 또는 실패 여부를 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-157">The numeric response is used by the HTTP Client software to determine whether the operation succeeded or failed.</span></span> <span data-ttu-id="9be78-158">다음은 클라이언트 명령에 대한 여러 HTTP 서버 응답 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-158">Following is a list of various HTTP Server responses to Client commands:</span></span>

- <span data-ttu-id="9be78-159">200 *요청이 성공했습니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-159">200 *Request was successful*</span></span>
- <span data-ttu-id="9be78-160">400 *요청이 올바르게 구성되지 않았습니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-160">400 *Request was not formed properly*</span></span>
- <span data-ttu-id="9be78-161">401 *권한이 없는 요청입니다. 클라이언트가 인증을 보내야 합니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-161">401 *Unauthorized request, client needs to send authentication*</span></span>
- <span data-ttu-id="9be78-162">404 *요청에 지정된 리소스를 찾을 수 없습니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-162">404 *Specified resource in request was not found*</span></span>
- <span data-ttu-id="9be78-163">500 *내부 HTTP 서버 오류입니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-163">500 *Internal HTTP Server error*</span></span>
- <span data-ttu-id="9be78-164">501 *HTTP 서버에서 요청이 구현되지 않았습니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-164">501 *Request not implemented by HTTP Server*</span></span>
- <span data-ttu-id="9be78-165">502 *서비스를 사용할 수 없습니다.*</span><span class="sxs-lookup"><span data-stu-id="9be78-165">502 *Service is not available*</span></span>

<span data-ttu-id="9be78-166">예를 들어 “test.htm” 파일을 PUT하기 위한 클라이언트 요청에 성공하면 “HTTP/1.0 200 OK” 응답 메시지가 수신됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-166">For example, a successful Client request to PUT the file “test.htm” is responded with the message “HTTP/1.0 200 OK.”</span></span>

## <a name="http-communication"></a><span data-ttu-id="9be78-167">HTTP 통신</span><span class="sxs-lookup"><span data-stu-id="9be78-167">HTTP Communication</span></span>

<span data-ttu-id="9be78-168">앞에서 설명한 대로, HTTP 서버는 *잘 알려진 TCP 포트 80* 을 활용하여 클라이언트 요청을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-168">As mentioned previously, the HTTP Server utilizes the *well-known TCP port 80* to field Client requests.</span></span> <span data-ttu-id="9be78-169">HTTP 클라이언트는 사용 가능한 모든 TCP 포트를 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-169">HTTP Clients may use any available TCP port.</span></span> <span data-ttu-id="9be78-170">HTTP 이벤트의 일반 시퀀스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-170">The general sequence of HTTP events is as follows:</span></span>

<span data-ttu-id="9be78-171">**HTTP GET 요청**:</span><span class="sxs-lookup"><span data-stu-id="9be78-171">**HTTP GET Request**:</span></span>

1.  <span data-ttu-id="9be78-172">클라이언트가 서버 포트 80에 TCP 연결을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-172">Client issues TCP connect to Server port 80.</span></span>

2.  <span data-ttu-id="9be78-173">클라이언트가 “**GET resource HTTP/1.0**” 요청을 보냅니다(다른 헤더 정보 포함).</span><span class="sxs-lookup"><span data-stu-id="9be78-173">Client sends “**GET resource HTTP/1.0**” request (along with other header information).</span></span>

3.  <span data-ttu-id="9be78-174">서버가 추가 정보 바로 다음에 리소스 콘텐츠(있는 경우)가 포함된 “**HTTP/1.0 200 OK**” 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-174">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content (if any).</span></span>

4.  <span data-ttu-id="9be78-175">서버가 연결 해제를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-175">Server performs a disconnection.</span></span>

5.  <span data-ttu-id="9be78-176">클라이언트가 연결 해제를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-176">Client performs a disconnection.</span></span>

<span data-ttu-id="9be78-177">**HTTP PUT 요청**:</span><span class="sxs-lookup"><span data-stu-id="9be78-177">**HTTP PUT Request**:</span></span>

1. <span data-ttu-id="9be78-178">클라이언트가 서버 포트 80에 TCP 연결을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-178">Client issues TCP connect to Server port 80.</span></span>

2. <span data-ttu-id="9be78-179">클라이언트가 다른 헤더 정보 다음에 리소스 콘텐츠가 포함된 “**PUT resource HTTP/1.0**” 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-179">Client sends “**PUT resource HTTP/1.0**” request, along with other header information, and followed by the resource content.</span></span>

3. <span data-ttu-id="9be78-180">서버가 추가 정보 바로 다음에 리소스 콘텐츠가 포함된 “**HTTP/1.0 200 OK**” 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-180">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content.</span></span>

4. <span data-ttu-id="9be78-181">서버가 연결 해제를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-181">Server performs a disconnection.</span></span>

5. <span data-ttu-id="9be78-182">클라이언트가 연결 해제를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-182">Client performs a disconnection.</span></span>

>[!NOTE] 
> <span data-ttu-id="9be78-183">앞에서 설명한 것처럼, HTTP 클라이언트는 대체 포트를 사용하여 클라이언트에 연결하는 웹 서버에 *nx_http_client_set_connect_port* 를 사용하여 기본 연결 포트를 80에서 다른 포트로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-183">As mentioned previously, the HTTP Client can change the default connect port from 80 to another port using the *nx_http_client_set_connect_port* for web servers that use alternate ports to connect to clients.</span></span>

## <a name="http-authentication"></a><span data-ttu-id="9be78-184">HTTP 인증</span><span class="sxs-lookup"><span data-stu-id="9be78-184">HTTP Authentication</span></span>

<span data-ttu-id="9be78-185">HTTP 인증은 선택 사항이며 모든 웹 요청에 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-185">HTTP authentication is optional and isn’t required for all Web requests.</span></span> <span data-ttu-id="9be78-186">인증에는 *기본* 및 *다이제스트* 라는 두 가지 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-186">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="9be78-187">기본 인증은 많은 프로토콜에서 사용되는 *이름* 및 *암호* 인증과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-187">Basic authentication is equivalent to the *name* and *password* authentication found in many protocols.</span></span> <span data-ttu-id="9be78-188">HTTP 기본 인증에서는 이름 및 암호가 연결되고 base64 형식으로 인코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-188">In HTTP basic authentication, the name and passwords are concatenated and encoded in the base64 format.</span></span> <span data-ttu-id="9be78-189">기본 인증의 주요 단점은 이름 및 암호가 요청에서 공개적으로 전송된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-189">The main disadvantage of basic authentication is the name and password are transmitted openly in the request.</span></span> <span data-ttu-id="9be78-190">따라서 이름 및 암호를 쉽게 도난당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-190">This makes it somewhat easy for the name and password to be stolen.</span></span> <span data-ttu-id="9be78-191">다이제스트 인증은 이름 및 암호를 요청으로 전송하지 않는 방식으로 이 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-191">Digest authentication addresses this problem by never transmitting the name and password in the request.</span></span> <span data-ttu-id="9be78-192">대신, 이름, 암호 및 기타 정보로부터 128비트 키 또는 다이제스트를 파생하기 위한 알고리즘이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-192">Instead, an algorithm is used to derive a 128-bit key or digest from the name, password, and other information.</span></span> <span data-ttu-id="9be78-193">NetX HTTP 서버는 표준 MD5 다이제스트 알고리즘을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-193">The NetX HTTP Server supports the standard MD5 digest algorithm.</span></span>

<span data-ttu-id="9be78-194">인증은 언제 필요한가요?</span><span class="sxs-lookup"><span data-stu-id="9be78-194">When is authentication required?</span></span> <span data-ttu-id="9be78-195">기본적으로 HTTP 서버는 요청된 리소스에 인증이 필요한지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-195">Basically, the HTTP Server decides if a requested resource requires authentication.</span></span> <span data-ttu-id="9be78-196">인증이 필요하고 클라이언트 요청에 적합한 인증이 포함되지 않았으면 필요한 인증 유형이 포함된 “HTTP/1.0 401 권한 없음” 응답이 클라이언트에 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-196">If authentication is required and the Client request did not include the proper authentication, a “HTTP/1.0 401 Unauthorized” response with the type of authentication required is sent to the Client.</span></span> <span data-ttu-id="9be78-197">그러면 클라이언트는 적절한 인증으로 새 요청을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-197">The Client is then expected to form a new request with the proper authentication.</span></span>

## <a name="http-authentication-callback"></a><span data-ttu-id="9be78-198">HTTP 인증 콜백</span><span class="sxs-lookup"><span data-stu-id="9be78-198">HTTP Authentication Callback</span></span>

<span data-ttu-id="9be78-199">앞에서 설명한 것처럼, HTTP 인증은 선택 사항이며 모든 웹 전송에 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-199">As mentioned before, HTTP authentication is optional and isn’t required on all Web transfers.</span></span> <span data-ttu-id="9be78-200">또한 인증은 일반적으로 리소스에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-200">In addition, authentication is typically resource dependent.</span></span> <span data-ttu-id="9be78-201">서버에서 일부 리소스는 액세스할 때 인증이 필요하지만, 다른 리소스는 인증이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-201">Access of some resources on the Server require authentication, while others do not.</span></span> <span data-ttu-id="9be78-202">NetX HTTP 서버 패키지는 애플리케이션이 ***nx_http_server_create*** 호출을 통해 각 HTTP 클라이언트 요청 처리를 시작할 때 호출되는 인증 콜백 루틴을 지정하도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-202">The NetX HTTP Server package allows the application to specify (via the ***nx_http_server_create*** call) an authentication callback routine that is called at the beginning of handling each HTTP Client request.</span></span>

<span data-ttu-id="9be78-203">콜백 루틴은 NetX HTTP 서버에 사용자 이름, 암호 및 리소스와 연결된 영역 문자열을 제공하고 필요한 인증 유형을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-203">The callback routine provides the NetX HTTP Server with the username, password, and realm strings associated with the resource and return the type of authentication necessary.</span></span> <span data-ttu-id="9be78-204">리소스에 인증이 필요하지 않으면 인증 콜백이 **NX_HTTP_DONT_AUTHENTICATE** 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-204">If no authentication is necessary for the resource, the authentication callback should return the value of **NX_HTTP_DONT_AUTHENTICATE**.</span></span> <span data-ttu-id="9be78-205">그렇지 않고, 지정된 리소스에 대해 기본 인증이 필요하면 루틴이 **NX_HTTP_BASIC_AUTHENTICATE** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-205">Otherwise, if basic authentication is required for the specified resource, the routine should return **NX_HTTP_BASIC_AUTHENTICATE**.</span></span> <span data-ttu-id="9be78-206">그리고 마지막으로 MD5 다이제스트 인증이 필요하면 콜백 루틴이 **NX_HTTP_DIGEST_AUTHENTICATE** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-206">And finally, if MD5 digest authentication is required, the callback routine should return **NX_HTTP_DIGEST_AUTHENTICATE**.</span></span> <span data-ttu-id="9be78-207">HTTP 서버에서 제공되는 리소스에 인증이 필요하지 않으면 콜백이 필요하지 않고 HTTP 서버 만들기 호출에 NULL 포인터를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-207">If no authentication is required for any resource provided by the HTTP Server, the callback is not needed and a NULL pointer can be provided to the HTTP Server create call.</span></span>

<span data-ttu-id="9be78-208">애플리케이션 인증 콜백 루틴의 형식은 매우 간단하며 아래에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-208">The format of the application authenticate callback routine is very simple and is defined below:</span></span>

```c
UINT nx_http_server_authentication_check (NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, CHAR **password,
                                         CHAR **realm);
```

<span data-ttu-id="9be78-209">입력 매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-209">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="9be78-210">*request_type* HTTP 클라이언트 요청을 지정합니다. 유효한 요청은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-210">*request_type* Specifies the HTTP Client request, valid requests are defined as:</span></span>
  - <span data-ttu-id="9be78-211">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="9be78-211">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
  - <span data-ttu-id="9be78-212">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="9be78-212">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
  - <span data-ttu-id="9be78-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="9be78-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
  - <span data-ttu-id="9be78-214">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="9be78-214">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
  - <span data-ttu-id="9be78-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="9be78-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>
- <span data-ttu-id="9be78-216">*resource* 요청된 특정 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-216">*resource* Specific resource requested.</span></span>
- <span data-ttu-id="9be78-217">*name* 필요한 사용자 이름에 대한 포인터의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-217">*name* Destination for the pointer to the required username.</span></span>
- <span data-ttu-id="9be78-218">*password* 필요한 암호에 대한 포인터의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-218">*password* Destination for the pointer to the required password.</span></span>
- <span data-ttu-id="9be78-219">*realm* 이 인증의 영역에 대한 포인터의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-219">*realm* Destination for the pointer to the realm for this authentication.</span></span>

<span data-ttu-id="9be78-220">인증 루틴의 반환 값은 인증이 필요한지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-220">The return value of the authentication routine specifies if authentication is required.</span></span> <span data-ttu-id="9be78-221">**NX_HTTP_DONT_AUTHENTICATE** 가 인증 콜백 루틴으로 반환된 경우 이름, 암호 및 영역 포인터가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-221">name, password, and realm pointers are not used if **NX_HTTP_DONT_AUTHENTICATE** is returned by the authentication callback routine.</span></span> <span data-ttu-id="9be78-222">그렇지 않으면 HTTP 서버 개발자가 *nx_http_server.h* 에 정의된 **NX_HTTP_MAX_USERNAME** 및 **NX_HTTP_MAX_PASSWORD** 가 인증 콜백에 지정된 사용자 이름 및 암호에 맞게 충분히 큰지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-222">Otherwise the HTTP server developer must ensure that **NX_HTTP_MAX_USERNAME** and **NX_HTTP_MAX_PASSWORD** defined in *nx_http_server.h* are large enough for the username and password specified in the authentication callback.</span></span> <span data-ttu-id="9be78-223">이는 모두 기본적으로 20자로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-223">These are both defaulted to size 20 chars.</span></span>

## <a name="http-invalid-usernamepassword-callback"></a><span data-ttu-id="9be78-224">HTTP 잘못된 사용자 이름/암호 콜백</span><span class="sxs-lookup"><span data-stu-id="9be78-224">HTTP Invalid Username/Password Callback</span></span>

<span data-ttu-id="9be78-225">HTTP 서버가 클라이언트 요청에서 잘못된 사용자 이름 및 암호 조합을 수신하면 NetX HTTP 서버에서 선택적인 잘못된 사용자 이름/암호 콜백이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-225">The optional invalid username/password callback in NetX HTTP Server is invoked if HTTP server receives an invalid username and password combination in a Client request.</span></span> <span data-ttu-id="9be78-226">HTTP 서버 애플리케이션이 HTTP 서버에 콜백을 등록하면 *nx_http_server_get_process*, *nx_http_server_put_process* 또는 *nx_ttp_server_delete_process* 에서 기본 또는 다이제스트 인증이 실패할 경우 콜백이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-226">If the HTTP server application registers a callback with HTTP server it will be invoked if either basic or digest authentication fails *in nx_http_server_get_process*, in *nx_http_server_put_process,* or *in nx_http_server_delete_process.*</span></span>

<span data-ttu-id="9be78-227">HTTP 서버에 콜백을 등록하기 위해 NetX HTTP 서버에 다음 서비스가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-227">To register a callback with the HTTP server, the following service is defined in NetX HTTP Server.</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set (NX_HTTP_SERVER *http_server_ptr,
                                                    UINT *invalid_username_password_callback)
                                                    (CHAR *resource,
                                                    ULONG *client_nx_address,
                                                    UINT request_type));
```
<span data-ttu-id="9be78-228">요청 유형은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-228">The request types are defined as follows:</span></span>

- <span data-ttu-id="9be78-229">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="9be78-229">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
- <span data-ttu-id="9be78-230">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="9be78-230">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
- <span data-ttu-id="9be78-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="9be78-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
- <span data-ttu-id="9be78-232">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="9be78-232">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
- <span data-ttu-id="9be78-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="9be78-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>

## <a name="http-insert-gmt-date-header-callback"></a><span data-ttu-id="9be78-234">HTTP GMT 날짜 헤더 삽입 콜백</span><span class="sxs-lookup"><span data-stu-id="9be78-234">HTTP Insert GMT Date Header Callback</span></span>

<span data-ttu-id="9be78-235">NetX HTTP 서버에는 응답 메시지에 날짜 헤더를 삽입하기 위한 선택적인 콜백이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-235">There is an optional callback in NetX HTTP Server to insert a date header in its response messages.</span></span> <span data-ttu-id="9be78-236">이 콜백은 HTTP 서버가 put 또는 get 요청에 응답할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-236">This callback is invoked when the HTTP Server is responding to a put or get request</span></span>

<span data-ttu-id="9be78-237">HTTP 서버에 GMT 날짜 콜백을 등록하기 위해 NetX HTTP 서버에 다음 서비스가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-237">To register a GMT date callback with the HTTP server, the following service is defined in the NetX HTTP Server.</span></span>

```c
UINT _nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="9be78-238">NX_HTTP_SERVER_DATE 데이터 형식은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-238">The NX_HTTP_SERVER_DATE data type is defined as follows:</span></span>

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT     nx_http_server_year;         /* Year        */
    UCHAR      nx_http_server_month;        /* Month       */
    UCHAR      nx_http_server_day;          /* Day         */
    UCHAR      nx_http_server_hour;         /* Hour        */
    UCHAR      nx_http_server_minute;       /* Minute      */
    UCHAR      nx_http_server_second;       /* Second      */
    UCHAR      nx_http_server_weekday;      /* Weekday     */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a><span data-ttu-id="9be78-239">HTTP 캐시 정보 가져오기 콜백</span><span class="sxs-lookup"><span data-stu-id="9be78-239">HTTP Cache Info Get Callback</span></span>

<span data-ttu-id="9be78-240">HTTP 서버에는 HTTP 애플리케이션에서 특정 리소스의 최대 기간 및 날짜를 요청하기 위한 콜백이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-240">The HTTP Server has a callback to request the max age and date from the HTTP application for a specific resource.</span></span> <span data-ttu-id="9be78-241">이 정보는 HTTP 서버가 클라이언트 Get 요청에 대한 응답으로 전체 페이지를 보내는지 여부를 확인하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-241">This information is used to determine if the HTTP server sends the entire page in response to a Client Get request.</span></span> <span data-ttu-id="9be78-242">클라이언트 요청에서 “if modified since”가 없거나 캐시 가져오기 콜백으로 반환된 “last modified” 날짜와 일치하지 않으면 전체 페이지가 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-242">If the “if modified since” in the Client request is not found or does not match the “last modified” date returned by the get cache callback, the entire page is sent.</span></span>

<span data-ttu-id="9be78-243">콜백을 HTTP 서버에 등록하기 위해 다음 서비스가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-243">To register the callback with the HTTP server the following service is defined:</span></span>

```c
UINT _nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                            UINT (*cache_info_get)
                                            (CHAR *, UINT *, NX_HTTP_SERVER_DATE *));
```

## <a name="http-multipart-support"></a><span data-ttu-id="9be78-244">HTTP 다중 파트 지원</span><span class="sxs-lookup"><span data-stu-id="9be78-244">HTTP Multipart Support</span></span>

<span data-ttu-id="9be78-245">MIME(Multipurpose Internet Mail Extensions)은 처음에 SMTP 프로토콜을 위해 만들어졌지만 사용 범위가 HTTP로 확장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-245">Multipurpose Internet Mail Extensions (MIME) was originally intended for the SMTP protocol, but its use has spread to HTTP.</span></span> <span data-ttu-id="9be78-246">MIME을 사용하면 동일한 메시지 내에 혼합된 메시지 유형(예: 이미지/jpg 및 텍스트/일반)을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-246">MIME allows messages to contain mixed message types (e.g. image/jpg and text/plain) within the same message.</span></span> <span data-ttu-id="9be78-247">NetX HTTP 서버에는 클라이언트의 MIME을 포함하는 HTTP 메시지에서 콘텐츠 유형을 확인하기 위한 추가 서비스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-247">NetX HTTP Server has added services to determine content type in HTTP messages containing MIME from the Client.</span></span> <span data-ttu-id="9be78-248">HTTP 다중 파트 지원을 사용하도록 설정하고 이러한 서비스를 사용하기 위해서는 구성 옵션 **NX_HTTP_MULTIPART_ENABLE** 이 정의되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-248">To enable HTTP multipart support and use these services, the configuration option **NX_HTTP_MULTIPART_ENABLE** must be defined.</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);

UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="9be78-249">이러한 서비스 사용에 대한 자세한 내용은 3장 “HTTP 서비스 설명”을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9be78-249">For more details on the use of these services, see their description in Chapter 3 “Description of HTTP Services”.</span></span>

## <a name="http-multi-thread-support"></a><span data-ttu-id="9be78-250">HTTP 다중 스레드 지원</span><span class="sxs-lookup"><span data-stu-id="9be78-250">HTTP Multi-Thread Support</span></span>

<span data-ttu-id="9be78-251">NetX HTTP 클라이언트 서비스는 다중 스레드에서 동시에 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-251">The NetX HTTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="9be78-252">하지만 특정 HTTP 클라이언트 인스턴스에 대한 읽기 또는 쓰기 요청은 동일한 스레드에서 순차적으로 수행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-252">However, read or write requests for a particular HTTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="http-rfcs"></a><span data-ttu-id="9be78-253">HTTP RFC</span><span class="sxs-lookup"><span data-stu-id="9be78-253">HTTP RFCs</span></span>

<span data-ttu-id="9be78-254">NetX HTTP는 RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts” 및 관련 RFC와 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9be78-254">NetX HTTP is compliant with RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts”, and related RFCs.</span></span>