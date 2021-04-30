---
title: 1장 - HTTP 및 HTTPS 소개
description: 이 장에서는 웹 모듈을 위한 Azure RTOS NetX Duo HTTP/HTTPS를 소개합니다.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c784843e4d3f11ee306e866223c0a19bfcba3b85
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811809"
---
# <a name="chapter-1---introduction-to-http-and-https"></a><span data-ttu-id="e97bf-103">1장 - HTTP 및 HTTPS 소개</span><span class="sxs-lookup"><span data-stu-id="e97bf-103">Chapter 1 - Introduction to HTTP and HTTPS</span></span>

<span data-ttu-id="e97bf-104">HTTP(Hypertext Transfer Protocol)는 웹에서 콘텐츠를 전송하기 위해 설계된 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-104">The Hypertext Transfer Protocol (HTTP) is a protocol designed for transferring content on the Web.</span></span> <span data-ttu-id="e97bf-105">HTTP는 콘텐츠 전송 기능을 수행하기 위해 신뢰할 수 있는 TCP(Transmission Control Protocol) 서비스를 사용하는 간단한 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-105">HTTP is a simple protocol that utilizes reliable Transmission Control Protocol (TCP) services to perform its content transfer function.</span></span> <span data-ttu-id="e97bf-106">따라서 HTTP는 매우 안정적인 콘텐츠 전송 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-106">Because of this, HTTP is a highly reliable content transfer protocol.</span></span> <span data-ttu-id="e97bf-107">HTTP는 가장 많이 사용되는 애플리케이션 프로토콜 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-107">HTTP is one of the most used application protocols.</span></span> <span data-ttu-id="e97bf-108">웹의 모든 작업에 HTTP 프로토콜이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-108">All operations on the Web utilize the HTTP protocol.</span></span>

<span data-ttu-id="e97bf-109">HTTPS는 HTTP 프로토콜의 보안 버전이며, 기본 TCP 연결을 보호하기 위해 TLS(전송 계층 보안)를 사용하여 HTTP를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-109">HTTPS is the secure version of the HTTP protocol, which implements HTTP using Transport Layer Security (TLS) to secure the underlying TCP connection.</span></span> <span data-ttu-id="e97bf-110">TLS 설정에 필요한 추가 구성을 제외하고 HTTPS는 HTTP와 기본적으로 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-110">Other than the additional configuration required to set up TLS, HTTPS is basically identical to HTTP in use.</span></span>

## <a name="general-http-requirements"></a><span data-ttu-id="e97bf-111">일반 HTTP 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e97bf-111">General HTTP Requirements</span></span>

<span data-ttu-id="e97bf-112">NetX Web HTTP 패키지가 올바르게 작동하기 위해서는 NetX Duo(버전 5.10 이상)가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-112">In order to function properly, the NetX Web HTTP package requires that NetX Duo (version 5.10 or later) is installed.</span></span> <span data-ttu-id="e97bf-113">또한 IP 인스턴스를 만들고 동일한 IP 인스턴스에서 TCP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-113">In addition, an IP instance must be created, and TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="e97bf-114">HTTPS 지원을 위해서는 NetX Secure TLS(버전 5.11 이상)도 설치해야 합니다(다음 섹션 참조).</span><span class="sxs-lookup"><span data-stu-id="e97bf-114">For HTTPS support, NetX Secure TLS (version 5.11 or later) must also be installed (see next section).</span></span> <span data-ttu-id="e97bf-115">**2장** 의 “작은 예제 시스템” 섹션에 있는 데모 파일은 이를 수행하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-115">The demo file in section “Small Example System” in **Chapter 2** demonstrates how this is done.</span></span>

<span data-ttu-id="e97bf-116">NetX Web HTTP 패키지의 HTTP 클라이언트 부분에는 추가 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-116">The HTTP Client portion of the NetX Web HTTP package has no further requirements.</span></span>

<span data-ttu-id="e97bf-117">NetX Web HTTP 패키지의 HTTP 서버 부분에는 여러 추가 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-117">The HTTP Server portion of the NetX Web HTTP package has several additional requirements.</span></span> <span data-ttu-id="e97bf-118">먼저 모든 클라이언트 HTTP 요청을 처리하기 위해 TCP의 *잘 알려진 포트 80* 에 대한 전체 액세스 권한이 필요합니다(애플리케이션이 다른 유효한 TCP 포트로 변경할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="e97bf-118">First, it requires complete access to TCP *well-known port 80* for handling all Client HTTP requests (this can be changed by the application to any other valid TCP port).</span></span> <span data-ttu-id="e97bf-119">또한 HTTP 서버는 FileX 포함된 파일 시스템에 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-119">The HTTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="e97bf-120">FileX를 사용할 수 없으면 사용자가 사용된 FileX 부분을 자신의 고유 환경으로 이식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-120">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="e97bf-121">이에 대해서는 이 가이드의 이후 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-121">This is discussed in later sections of this guide.</span></span>

## <a name="https-requirements"></a><span data-ttu-id="e97bf-122">HTTPS 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e97bf-122">HTTPS Requirements</span></span>

<span data-ttu-id="e97bf-123">HTTPS가 올바르게 작동하기 위해서는 NetX Web HTTP 패키지에 NetX Duo(버전 5.10 이상) 및 NetX Secure TLS(버전 5.11 이상)가 모두 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-123">For HTTPS to function properly, the NetX Web HTTP package requires that NetX Duo (version 5.10 or later) and NetX Secure TLS (version 5.11 or later) are both installed.</span></span> <span data-ttu-id="e97bf-124">또한 IP 인스턴스를 만들고 TLS에 사용하도록 동일한 IP 인스턴스에서 TCP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-124">In addition, an IP instance must be created, and TCP must be enabled on that same IP instance for use with TLS.</span></span> <span data-ttu-id="e97bf-125">적합한 암호화 루틴, 신뢰할 수 있는 CA 인증서를 사용하여 TLS 세션을 초기화하고, TLS 핸드셰이크 중 원격 서버 호스트로 제공되는 인증서에 대해 공간을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-125">The TLS session will need to be initialized with appropriate cryptographic routines, a trusted CA certificate, and space must be allocated for certificates that will be provided by remote server hosts during the TLS handshake.</span></span> <span data-ttu-id="e97bf-126">**2장** 의 “작은 예제 HTTPS 시스템” 섹션에 있는 데모 파일은 이를 수행하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-126">The demo file in section “Small Example HTTPS System” in **Chapter 2** will demonstrate how this is done.</span></span>

<span data-ttu-id="e97bf-127">NetX Web HTTP 패키지의 HTTPS 클라이언트 부분에는 추가 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-127">The HTTPS Client portion of the NetX Web HTTP package has no further requirements.</span></span>

<span data-ttu-id="e97bf-128">NetX Web HTTP 패키지의 HTTPS 서버 부분에는 몇 가지 추가 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-128">The HTTPS Server portion of the NetX Web HTTP package has several additional requirements.</span></span> <span data-ttu-id="e97bf-129">첫째, 모든 클라이언트 HTTPS 요청을 처리하기 위해 TCP의 *잘 알려진 포트 443* 에 대한 전체 액세스 권한이 필요합니다(일반 텍스트 HTTP와 마찬가지로 이 포트도 애플리케이션이 변경할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="e97bf-129">First, it requires complete access to TCP *well-known port 443* for handling all Client HTTPS requests (as with plaintext HTTP, this port can be changed by the application).</span></span> <span data-ttu-id="e97bf-130">둘째, 적절한 암호화 루틴 및 서버 ID 인증서(또는 사전 공유 키)를 사용하여 TLS 세션을 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-130">Second, the TLS session will need to be initialized with proper cryptographic routines and a server identity certificate (or Pre-Shared Key).</span></span> <span data-ttu-id="e97bf-131">또한 HTTPS 서버는 FileX 포함된 파일 시스템에 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-131">The HTTPS Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="e97bf-132">FileX를 사용할 수 없으면 사용자가 사용된 FileX 부분을 자신의 고유 환경으로 이식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-132">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="e97bf-133">FileX 사용에 대해서는 이 가이드의 이후 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-133">The use of FileX is discussed in later sections of this guide.</span></span>

<span data-ttu-id="e97bf-134">TLS의 구성 옵션에 대한 자세한 내용은 NetX 보안 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e97bf-134">Refer to the NetX Secure documentation for more information on configuration options for TLS.</span></span>

<span data-ttu-id="e97bf-135">특별한 언급이 없으면 이 문서에 설명된 모든 HTTP 기능이 HTTPS에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-135">Unless noted, all HTTP functionality described in this document also applies to HTTPS.</span></span>

## <a name="http-and-https-constraints"></a><span data-ttu-id="e97bf-136">HTTP 및 HTTPS 제약 조건</span><span class="sxs-lookup"><span data-stu-id="e97bf-136">HTTP and HTTPS Constraints</span></span>

<span data-ttu-id="e97bf-137">NetX Web HTTP는 HTTP 1.1 표준을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-137">NetX Web HTTP implements the HTTP 1.1 standard.</span></span> <span data-ttu-id="e97bf-138">하지만 다음과 같은 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-138">However, here are following constraints:</span></span>

1. <span data-ttu-id="e97bf-139">요청 파이프라인이 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="e97bf-139">Request pipelining is not supported</span></span>
1. <span data-ttu-id="e97bf-140">HTTP 서버가 기본 및 MD5 다이제스트 인증을 모두 지원하지만 MD5-sess는 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-140">The HTTP Server supports both basic and MD5 digest authentication, but not MD5-sess.</span></span> <span data-ttu-id="e97bf-141">현재까지 HTTP 클라이언트는 기본 인증만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-141">At present, the HTTP Client supports only basic authentication.</span></span> <span data-ttu-id="e97bf-142">HTTPS에 TLS를 사용할 때에도 HTTP 인증을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-142">When using TLS for HTTPS, HTTP authentication may still be used.</span></span>
1. <span data-ttu-id="e97bf-143">콘텐츠 압축은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-143">No content compression is supported.</span></span>
1. <span data-ttu-id="e97bf-144">TRACE, OPTIONS 및 CONNECT 요청은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-144">TRACE, OPTIONS, and CONNECT requests are not supported.</span></span>
1. <span data-ttu-id="e97bf-145">HTTP 서버 또는 클라이언트와 연결된 패킷 풀은 전체 HTTP 헤더를 저장할 수 있을 만큼 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-145">The packet pool associated with the HTTP Server or Client must be large enough to hold the complete HTTP header.</span></span>
1. <span data-ttu-id="e97bf-146">HTTP 클라이언트 서비스는 콘텐츠 전송용으로만 제공되며, 이 패키지에는 디스플레이 유틸리티가 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-146">HTTP Client services are for content transfer only—there are no display utilities provided in this package.</span></span>

## <a name="http-url-resource-names"></a><span data-ttu-id="e97bf-147">HTTP URL(리소스 이름)</span><span class="sxs-lookup"><span data-stu-id="e97bf-147">HTTP URL (Resource Names)</span></span>

<span data-ttu-id="e97bf-148">HTTP 프로토콜은 웹에서 콘텐츠를 전송하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-148">The HTTP protocol is designed to transfer content on Web.</span></span> <span data-ttu-id="e97bf-149">요청된 콘텐츠는 URL(Universal Resource Locator)로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-149">The requested content is specified by the Universal Resource Locator (URL).</span></span> <span data-ttu-id="e97bf-150">이것은 모든 HTTP 요청의 기본 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-150">This is the primary component of every HTTP request.</span></span> <span data-ttu-id="e97bf-151">URL은 항상 “/” 문자로 시작하며 일반적으로 HTTP 서버에 있는 파일을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-151">URLs always start with a “/” character and typically correspond to files on the HTTP Server.</span></span> <span data-ttu-id="e97bf-152">일반적인 HTTP 파일 확장자는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-152">Common HTTP file extensions are shown below:</span></span>

- <span data-ttu-id="e97bf-153">**.htm**(또는 **.html**) HTML(Hypertext Markup Language)</span><span class="sxs-lookup"><span data-stu-id="e97bf-153">**.htm** (or **.html**) Hypertext Markup Language (HTML)</span></span>
- <span data-ttu-id="e97bf-154">**.txt** 일반 ASCII 텍스트</span><span class="sxs-lookup"><span data-stu-id="e97bf-154">**.txt** Plain ASCII text</span></span>
- <span data-ttu-id="e97bf-155">**.gif** 이진 GIF 이미지</span><span class="sxs-lookup"><span data-stu-id="e97bf-155">**.gif** Binary GIF image</span></span>
- <span data-ttu-id="e97bf-156">**.xbm** 이진 Xbitmap 이미지</span><span class="sxs-lookup"><span data-stu-id="e97bf-156">**.xbm** Binary Xbitmap image</span></span>

## <a name="http-client-requests"></a><span data-ttu-id="e97bf-157">HTTP 클라이언트 요청</span><span class="sxs-lookup"><span data-stu-id="e97bf-157">HTTP Client Requests</span></span>

<span data-ttu-id="e97bf-158">HTTP에는 웹 콘텐츠 요청을 위한 간단한 메커니즘이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-158">The HTTP has a simple mechanism for requesting Web content.</span></span> <span data-ttu-id="e97bf-159">TCP의 *잘 알려진 포트 80(HTTPS의 경우 포트 443)* 에서 연결이 성공적으로 설정된 후 클라이언트에서 실행되는 표준 HTTP 명령 세트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-159">There is a set of standard HTTP commands that are issued by the Client after a connection has been successfully established on the TCP *well-known port 80 (port 443 for HTTPS)*.</span></span> <span data-ttu-id="e97bf-160">다음은 기본 HTTP 명령 중 일부를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-160">The following shows some of the basic HTTP commands:</span></span>

- <span data-ttu-id="e97bf-161">**GET *resource* HTTP/1.1** 지정된 리소스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-161">**GET *resource* HTTP/1.1** Get the specified resource</span></span>
- <span data-ttu-id="e97bf-162">**POST *resource* HTTP/1.1** 지정된 리소스를 가져오고 연결된 입력을 HTTP 서버에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-162">**POST *resource* HTTP/1.1** Get the specified resource and pass attached input to the HTTP Server</span></span>
- <span data-ttu-id="e97bf-163">**HEAD *resource* HTTP/1.1** GET와 비슷하게 취급되지만 콘텐츠가 HTTP 서버에서 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-163">**HEAD *resource* HTTP/1.1** Treated like a GET but not content is returned by the HTTP Server</span></span>
- <span data-ttu-id="e97bf-164">**PUT *resource* HTTP/1.1** 리소스를 HTTP 서버에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-164">**PUT *resource* HTTP/1.1** Place resource on HTTP Server</span></span>
- <span data-ttu-id="e97bf-165">**DELETE *resource* HTTP/1.1** 서버에서 리소스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-165">**DELETE *resource* HTTP/1.1** Delete resource on the Server</span></span>

<span data-ttu-id="e97bf-166">이러한 ASCII 명령은 HTTP 서버로 HTTP 작업을 수행하기 위해 웹 브라우저 및 NetX Web HTTP 클라이언트 서비스에서 내부적으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-166">These ASCII commands are generated internally by Web browsers and the NetX Web HTTP Client services to perform HTTP operations with an HTTP Server.</span></span>

<span data-ttu-id="e97bf-167">HTTP 클라이언트 애플리케이션에는 포트 80 또는 포트 443(HTTPS가 사용된 경우)이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-167">Note that the HTTP Client application should use port 80, or port 443 if HTTPS is used.</span></span> <span data-ttu-id="e97bf-168">클라이언트 및 서버 HTTP API는 모두 포트를 매개 변수로 사용합니다. 매크로 NX_WEB_HTTP_SERVER_PORT(포트 80) 및 NX_WEB_HTTPS_SERVER_PORT(포트 443)는 편의를 위해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-168">Both the Client and Server HTTP APIs take the port as a parameter – the macros NX_WEB_HTTP_SERVER_PORT (port 80) and NX_WEB_HTTPS_SERVER_PORT (port 443) are defined for convenience.</span></span> <span data-ttu-id="e97bf-169">또한 *nx_web_http_client_set_connect_port()* 서비스를 사용하여 런타임에 HTTP 서버 포트를 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-169">The HTTP Server port can also be changed at runtime using the *nx_web_http_client_set_connect_port()* service.</span></span> <span data-ttu-id="e97bf-170">이 서비스에 대한 자세한 내용은 4장을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e97bf-170">See Chapter 4 for more details on this service.</span></span>

## <a name="http-server-responses"></a><span data-ttu-id="e97bf-171">HTTP 서버 응답</span><span class="sxs-lookup"><span data-stu-id="e97bf-171">HTTP Server Responses</span></span>

<span data-ttu-id="e97bf-172">HTTP 서버는 동일한 *잘 알려진 TCP 포트 80(HTTPS의 경우 443)* 을 사용하여 클라이언트 명령 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-172">The HTTP Server utilizes the same *well-known TCP port 80 (443 for HTTPS)* to send Client command responses.</span></span> <span data-ttu-id="e97bf-173">HTTP 서버가 클라이언트 명령을 처리하면 3자리 숫자 상태 코드가 포함된 ASCII 응답 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-173">Once the HTTP Server processes the Client command, it returns an ASCII response string that includes a 3-digit numeric status code.</span></span> <span data-ttu-id="e97bf-174">이 숫자 응답은 HTTP 클라이언트 소프트웨어에서 작업의 성공 또는 실패 여부를 결정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-174">The numeric response is used by the HTTP Client software to determine whether the operation succeeded or failed.</span></span> <span data-ttu-id="e97bf-175">다음은 클라이언트 명령에 대한 여러 HTTP 서버 응답 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-175">Following is a list of various HTTP Server responses to Client commands:</span></span>

- <span data-ttu-id="e97bf-176">**200** 요청이 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-176">**200** Request was successful</span></span>
- <span data-ttu-id="e97bf-177">**400** 요청이 올바르게 구성되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-177">**400** Request was not formed properly</span></span>
- <span data-ttu-id="e97bf-178">**401** 권한이 없는 요청입니다. 클라이언트가 인증을 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-178">**401** Unauthorized request, client needs to send authentication</span></span>
- <span data-ttu-id="e97bf-179">**404** 요청에 지정된 리소스를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-179">**404** Specified resource in request was not found</span></span>
- <span data-ttu-id="e97bf-180">**500** 내부 HTTP 서버 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-180">**500** Internal HTTP Server error</span></span>
- <span data-ttu-id="e97bf-181">**501** HTTP 서버에서 요청이 구현되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-181">**501** Request not implemented by HTTP Server</span></span>
- <span data-ttu-id="e97bf-182">**502** 서비스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-182">**502** Service is not available</span></span>

<span data-ttu-id="e97bf-183">예를 들어, “test.htm” 파일을 PUT하기 위한 성공적인 클라이언트 요청은 “HTTP/1.1 200 OK” 메시지로 응답됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-183">For example, a successful Client request to PUT the file “test.htm” is responded with the message “HTTP/1.1 200 OK.”</span></span>

## <a name="http-communication"></a><span data-ttu-id="e97bf-184">HTTP 통신</span><span class="sxs-lookup"><span data-stu-id="e97bf-184">HTTP Communication</span></span>

<span data-ttu-id="e97bf-185">앞에서 설명한 것처럼 HTTP 서버는 클라이언트 요청 처리를 위해 *잘 알려진 TCP 포트 80(HTTPS의 경우 443)* 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-185">As mentioned previously, the HTTP Server utilizes the *well-known TCP port 80 (443 for HTTPS)* to field Client requests.</span></span> <span data-ttu-id="e97bf-186">HTTP 클라이언트는 진행 중인 연결에 대해 사용 가능한 모든 TCP 포트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-186">HTTP Clients may use any available TCP port for outgoing connections.</span></span> <span data-ttu-id="e97bf-187">HTTP 이벤트의 일반 시퀀스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-187">The general sequence of HTTP events is as follows:</span></span>

<span data-ttu-id="e97bf-188">**HTTP GET 요청**:</span><span class="sxs-lookup"><span data-stu-id="e97bf-188">**HTTP GET Request**:</span></span>

1. <span data-ttu-id="e97bf-189">클라이언트가 서버 포트 80(또는 HTTPS의 경우 443)에 TCP 연결을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-189">Client issues TCP connect to Server port 80 (or 443 for HTTPS).</span></span>
1. <span data-ttu-id="e97bf-190">HTTPS를 사용하는 경우 TCP 연결 후 TLS 핸드셰이크를 통해 서버를 인증하고 보안 채널을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-190">If HTTPS is being used, the TCP connection is followed by a TLS handshake to authenticate the server and establish a secure channel.</span></span>
1. <span data-ttu-id="e97bf-191">클라이언트가 “**GET *resource* HTTP/1.1**” 요청을 보냅니다(다른 헤더 정보 포함).</span><span class="sxs-lookup"><span data-stu-id="e97bf-191">Client sends “**GET *resource* HTTP/1.1**” request (along with other header information).</span></span>
1. <span data-ttu-id="e97bf-192">서버가 추가 정보 바로 다음에 리소스 콘텐츠(있는 경우)가 포함된 “**HTTP/1.1 200 OK**” 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-192">Server builds an “**HTTP/1.1 200 OK**” message with additional information followed immediately by the resource content (if any).</span></span>
1. <span data-ttu-id="e97bf-193">서버가 클라이언트에서 연결을 해제합니다(HTTPS를 사용하는 경우 TLS가 종료됨).</span><span class="sxs-lookup"><span data-stu-id="e97bf-193">Server disconnects from the client (TLS is shut down if HTTPS is being used).</span></span>
1. <span data-ttu-id="e97bf-194">클라이언트가 소켓에서 연결을 해제합니다(TLS가 종료되고 서버의 연결 해제 경고가 표시됨).</span><span class="sxs-lookup"><span data-stu-id="e97bf-194">Client disconnects from the socket (TLS is shut down following the disconnection alert from the server).</span></span>

<span data-ttu-id="e97bf-195">**HTTP PUT 요청**:</span><span class="sxs-lookup"><span data-stu-id="e97bf-195">**HTTP PUT Request**:</span></span>

1. <span data-ttu-id="e97bf-196">클라이언트가 서버 포트 80(또는 443)에 TCP 연결을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-196">Client issues TCP connect to Server port 80 (or 443).</span></span>
1. <span data-ttu-id="e97bf-197">HTTPS를 사용하는 경우 TCP 연결 후 TLS 핸드셰이크를 통해 서버를 인증하고 보안 채널을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-197">If HTTPS is being used, the TCP connection is followed by a TLS handshake to authenticate the server and establish a secure channel.</span></span>
1. <span data-ttu-id="e97bf-198">클라이언트가 다른 헤더 정보와 함께 “PUT resource HTTP/1.1” 요청을 보낸 다음, 리소스 콘텐츠를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-198">Client sends “PUT resource HTTP/1.1” request, along with other header information, and followed by the resource content.</span></span>
1. <span data-ttu-id="e97bf-199">서버가 추가 정보 바로 다음에 리소스 콘텐츠가 포함된 “HTTP/1.1 200 OK” 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-199">Server builds an “HTTP/1.1 200 OK” message with additional information followed immediately by the resource content.</span></span>
1. <span data-ttu-id="e97bf-200">서버가 연결 해제를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-200">Server performs a disconnection.</span></span>
1. <span data-ttu-id="e97bf-201">클라이언트가 연결 해제를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-201">Client performs a disconnection.</span></span>

> [!NOTE]
> <span data-ttu-id="e97bf-202">앞에서 설명한 것처럼 HTTP 서버는 클라이언트에 연결하기 위해 대체 포트를 사용하는 웹 서버에 대해 *nx_web_http_client_set_connect_port()* 를 사용하여 런타임에 다른 포트로 기본 연결 포트(80 또는 443)를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-202">As mentioned previously, the HTTP Server can change the default connect port (80 or 443) at runtime another port using the *nx_web_http_client_set_connect_port()* for web servers that use alternate ports to connect to clients.</span></span>

## <a name="http-authentication"></a><span data-ttu-id="e97bf-203">HTTP 인증</span><span class="sxs-lookup"><span data-stu-id="e97bf-203">HTTP Authentication</span></span>

<span data-ttu-id="e97bf-204">HTTP 인증은 선택 사항이며 모든 웹 요청에 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-204">HTTP authentication is optional and is not required for all Web requests.</span></span> <span data-ttu-id="e97bf-205">인증에는 *기본* 및 *다이제스트* 라는 두 가지 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-205">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="e97bf-206">기본 인증은 많은 프로토콜에서 사용되는 *이름* 및 *암호* 인증과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-206">Basic authentication is equivalent to the *name* and *password* authentication found in many protocols.</span></span> <span data-ttu-id="e97bf-207">HTTP 기본 인증에서 이름 및 암호가 연결되고 base64 형식으로 인코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-207">In HTTP basic authentication, the name and passwords are concatenated and encoded in the base64 format.</span></span> <span data-ttu-id="e97bf-208">기본 인증의 주요 단점은 이름 및 암호가 요청에서 공개적으로 전송된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-208">The main disadvantage of basic authentication is the name and password are transmitted openly in the request.</span></span> <span data-ttu-id="e97bf-209">따라서 이름 및 암호를 쉽게 도난당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-209">This makes it somewhat easy for the name and password to be stolen.</span></span> <span data-ttu-id="e97bf-210">다이제스트 인증은 이름 및 암호를 요청으로 전송하지 않는 방식으로 이 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-210">Digest authentication addresses this problem by never transmitting the name and password in the request.</span></span> <span data-ttu-id="e97bf-211">대신 이름, 암호 및 기타 정보로부터 128비트 다이제스트를 파생하기 위한 알고리즘이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-211">Instead, an algorithm is used to derive a 128-bit digest from the name, password, and other information.</span></span> <span data-ttu-id="e97bf-212">NetX Web HTTP 서버는 표준 MD5 다이제스트 알고리즘을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-212">The NetX Web HTTP Server supports the standard MD5 digest algorithm.</span></span>

<span data-ttu-id="e97bf-213">인증은 언제 필요한가요?</span><span class="sxs-lookup"><span data-stu-id="e97bf-213">When is authentication required?</span></span> <span data-ttu-id="e97bf-214">HTTP 서버는 요청된 리소스에 인증이 필요한지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-214">The HTTP Server decides if a requested resource requires authentication.</span></span> <span data-ttu-id="e97bf-215">인증이 필요하고 클라이언트 요청에 적합한 인증이 포함되지 않은 경우 필요한 인증 유형이 포함된 “HTTP/1.1 401 권한 없음” 응답이 클라이언트에 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-215">If authentication is required and the Client request did not include the proper authentication, a “HTTP/1.1 401 Unauthorized” response with the type of authentication required is sent to the Client.</span></span> <span data-ttu-id="e97bf-216">그런 다음, 클라이언트는 적절한 인증으로 새 요청을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-216">The Client is then expected to form a new request with the proper authentication.</span></span>

<span data-ttu-id="e97bf-217">HTTPS를 사용하는 경우에도 HTTPS 서버는 HTTP 인증을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-217">When HTTPS is used, the HTTPS Server can still utilize HTTP authentication.</span></span> <span data-ttu-id="e97bf-218">이 경우 TLS는 모든 HTTP 트래픽을 암호화하는 데 사용되므로 *기본* HTTP 인증을 사용하는 경우 보안 위험이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-218">In this case, TLS is used to encrypt all HTTP traffic so using *basic* HTTP authentication does not pose a security risk.</span></span> <span data-ttu-id="e97bf-219">*다이제스트* 인증도 허용되지만 TLS를 통한 기본 인증에 비해 크게 향상된 보안 기능을 제공하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-219">*Digest* authentication is also permitted but provides no significant security improvement over basic authentication over TLS.</span></span>

## <a name="http-authentication-callback"></a><span data-ttu-id="e97bf-220">HTTP 인증 콜백</span><span class="sxs-lookup"><span data-stu-id="e97bf-220">HTTP Authentication Callback</span></span>

<span data-ttu-id="e97bf-221">앞에서 설명한 것처럼 HTTP 인증은 선택 사항이며 모든 웹 전송에 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-221">As mentioned before, HTTP authentication is optional and isn’t required on all Web transfers.</span></span> <span data-ttu-id="e97bf-222">또한 인증은 일반적으로 리소스에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-222">In addition, authentication is typically resource dependent.</span></span> <span data-ttu-id="e97bf-223">서버에서 일부 리소스는 액세스할 때 인증이 필요하지만, 다른 리소스는 인증이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-223">Access of some resources on the Server require authentication, while others do not.</span></span> <span data-ttu-id="e97bf-224">NetX Web HTTP 서버 패키지는 애플리케이션이 ***nx_web_http_server_create*** 호출을 통해 각 HTTP 클라이언트 요청 처리를 시작할 때 호출되는 인증 콜백 루틴을 지정하도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-224">The NetX Web HTTP Server package allows the application to specify (via the ***nx_web_http_server_create*** call) an authentication callback routine that is called at the beginning of handling each HTTP Client request.</span></span>

<span data-ttu-id="e97bf-225">콜백 루틴은 NetX Web HTTP 서버에 사용자 이름, 암호 및 리소스와 연결된 영역 문자열을 제공하고 필요한 인증 유형을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-225">The callback routine provides the NetX Web HTTP Server with the username, password, and realm strings associated with the resource and return the type of authentication necessary.</span></span> <span data-ttu-id="e97bf-226">리소스에 인증이 필요하지 않으면 인증 콜백이 **NX_WEB_HTTP_DONT_AUTHENTICATE** 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-226">If no authentication is necessary for the resource, the authentication callback should return the value of **NX_WEB_HTTP_DONT_AUTHENTICATE**.</span></span> <span data-ttu-id="e97bf-227">그렇지 않고, 지정된 리소스에 대해 기본 인증이 필요하면 루틴이 **NX_WEB_HTTP_BASIC_AUTHENTICATE** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-227">Otherwise, if basic authentication is required for the specified resource, the routine should return **NX_WEB_HTTP_BASIC_AUTHENTICATE**.</span></span> <span data-ttu-id="e97bf-228">그리고 마지막으로 MD5 다이제스트 인증이 필요하면 콜백 루틴이 **NX_WEB_HTTP_DIGEST_AUTHENTICATE** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-228">And finally, if MD5 digest authentication is required, the callback routine should return **NX_WEB_HTTP_DIGEST_AUTHENTICATE**.</span></span> <span data-ttu-id="e97bf-229">HTTP 서버에서 제공되는 리소스에 인증이 필요하지 않으면 콜백이 필요하지 않고 HTTP 서버 만들기 호출에 NULL 포인터를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-229">If no authentication is required for any resource provided by the HTTP Server, the callback is not needed, and a NULL pointer can be provided to the HTTP Server create call.</span></span>

<span data-ttu-id="e97bf-230">애플리케이션 인증 콜백 루틴의 형식은 매우 간단하며 아래에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-230">The format of the application authenticate callback routine is very simple and is defined below:</span></span>

```C
UINT nx_web_http_server_authentication_check(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type, CHAR *resource,
    CHAR **name, CHAR **password,
    CHAR **realm);
```

<span data-ttu-id="e97bf-231">입력 매개 변수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-231">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="e97bf-232">**request_type** HTTP 클라이언트 요청을 지정합니다. 유효한 요청은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-232">**request_type** Specifies the HTTP Client request, valid requests are defined as:</span></span>
  - <span data-ttu-id="e97bf-233">**NX_WEB_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e97bf-233">**NX_WEB_HTTP_SERVER_GET_REQUEST**</span></span>
  - <span data-ttu-id="e97bf-234">**NX_WEB_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e97bf-234">**NX_WEB_HTTP_SERVER_POST_REQUEST**</span></span>
  - <span data-ttu-id="e97bf-235">**NX_WEB_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e97bf-235">**NX_WEB_HTTP_SERVER_HEAD_REQUEST**</span></span>
  - <span data-ttu-id="e97bf-236">**NX_WEB_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e97bf-236">**NX_WEB_HTTP_SERVER_PUT_REQUEST**</span></span>
  - <span data-ttu-id="e97bf-237">**NX_WEB_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e97bf-237">**NX_WEB_HTTP_SERVER_DELETE_REQUEST**</span></span>
- <span data-ttu-id="e97bf-238">**resource** 요청된 특정 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-238">**resource** Specific resource requested.</span></span>
- <span data-ttu-id="e97bf-239">**name** 필요한 사용자 이름에 대한 포인터의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-239">**name** Destination for the pointer to the required username.</span></span>
- <span data-ttu-id="e97bf-240">**password** 필요한 암호에 대한 포인터의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-240">**password** Destination for the pointer to the required password.</span></span>
- <span data-ttu-id="e97bf-241">**realm** 이 인증의 영역에 대한 포인터의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-241">**realm** Destination for the pointer to the realm for this authentication.</span></span>

<span data-ttu-id="e97bf-242">인증 루틴의 반환 값은 인증이 필요한지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-242">The return value of the authentication routine specifies if authentication is required.</span></span> <span data-ttu-id="e97bf-243">**NX_WEB_HTTP_DONT_AUTHENTICATE** 가 인증 콜백 루틴으로 반환된 경우 이름, 암호 및 영역 포인터가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-243">name, password, and realm pointers are not used if **NX_WEB_HTTP_DONT_AUTHENTICATE** is returned by the authentication callback routine.</span></span> <span data-ttu-id="e97bf-244">그렇지 않으면 HTTP 서버 개발자가 *nx_web_http_server.h* 에 정의된 **NX_WEB_HTTP_MAX_USERNAME** 및 **NX_WEB_HTTP_MAX_PASSWORD** 가 인증 콜백에 지정된 사용자 이름 및 암호에 대해 충분히 큰지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-244">Otherwise the HTTP server developer must ensure that **NX_WEB_HTTP_MAX_USERNAME** and **NX_WEB_HTTP_MAX_PASSWORD** defined in *nx_web_http_server.h* are large enough for the username and password specified in the authentication callback.</span></span> <span data-ttu-id="e97bf-245">이러한 두 값 모두 기본 크기는 20자입니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-245">These both have a default size of 20 characters.</span></span>

## <a name="http-invalid-usernamepassword-callback"></a><span data-ttu-id="e97bf-246">HTTP 잘못된 사용자 이름/암호 콜백</span><span class="sxs-lookup"><span data-stu-id="e97bf-246">HTTP Invalid Username/Password Callback</span></span>

<span data-ttu-id="e97bf-247">HTTP 서버가 클라이언트 요청에서 잘못된 사용자 이름 및 암호 조합을 수신하는 경우 NetX Web HTTP 서버에서 잘못된 사용자 이름/암호 콜백(선택 사항)이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-247">The optional invalid username/password callback in the NetX Web HTTP Server is invoked if the HTTP server receives an invalid username and password combination in a Client request.</span></span> <span data-ttu-id="e97bf-248">HTTP 서버 애플리케이션이 HTTP 서버에 콜백을 등록하는 경우 기본 또는 다이제스트 인증이 *nx_web_http_server_get_process()* , *nx_web_http_server_put_process()* 또는 *nx_web_http_server_delete_process()* 에서 실패할 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-248">If the HTTP server application registers a callback with HTTP server it will be invoked if either basic or digest authentication fails *in nx_web_http_server_get_process()*, in *nx_web_http_server_put_process(),* or *in nx_web_http_server_delete_process().*</span></span>

<span data-ttu-id="e97bf-249">HTTP 서버에 콜백을 등록하기 위해 NetX Web HTTP 서버에 대해 다음 서비스가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-249">To register a callback with the HTTP server, the following service is defined for the NetX Web HTTP Server.</span></span>

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource, ULONG *client_nx_address,
        UINT request_type));
```

<span data-ttu-id="e97bf-250">요청 유형은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-250">The request types are defined as follows:</span></span>

- <span data-ttu-id="e97bf-251">**NX_WEB_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e97bf-251">**NX_WEB_HTTP_SERVER_GET_REQUEST**</span></span>
- <span data-ttu-id="e97bf-252">**NX_WEB_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e97bf-252">**NX_WEB_HTTP_SERVER_POST_REQUEST**</span></span>
- <span data-ttu-id="e97bf-253">**NX_WEB_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e97bf-253">**NX_WEB_HTTP_SERVER_HEAD_REQUEST**</span></span>
- <span data-ttu-id="e97bf-254">**NX_WEB_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e97bf-254">**NX_WEB_HTTP_SERVER_PUT_REQUEST**</span></span>
- <span data-ttu-id="e97bf-255">**NX_WEB_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e97bf-255">**NX_WEB_HTTP_SERVER_DELETE_REQUEST**</span></span>

## <a name="http-insert-gmt-date-header-callback"></a><span data-ttu-id="e97bf-256">HTTP GMT 날짜 헤더 삽입 콜백</span><span class="sxs-lookup"><span data-stu-id="e97bf-256">HTTP Insert GMT Date Header Callback</span></span>

<span data-ttu-id="e97bf-257">NetX Web HTTP 서버에는 응답 메시지에 날짜 헤더를 삽입하기 위한 선택적인 콜백이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-257">There is an optional callback in the NetX Web HTTP Server to insert a date header in its response messages.</span></span> <span data-ttu-id="e97bf-258">이 콜백은 HTTP 서버가 put 또는 get 요청에 응답할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-258">This callback is invoked when the HTTP Server is responding to a put or get request</span></span>

<span data-ttu-id="e97bf-259">GMT 날짜 콜백을 HTTP 서버에 등록하기 위해 다음 서비스가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-259">To register a GMT date callback with the HTTP Server, the following service is defined.</span></span>

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="e97bf-260">NX_WEB_HTTP_SERVER_DATE 데이터 형식은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-260">The NX_WEB_HTTP_SERVER_DATE data type is defined as follows:</span></span>

```C
typedef struct NX_WEB_HTTP_SERVER_DATE_STRUCT
{
    USHORT nx_web_http_server_year; /* Year */
    UCHAR nx_web_http_server_month; /* Month */
    UCHAR nx_web_http_server_day; /* Day */
    UCHAR nx_web_http_server_hour; /* Hour */
    UCHAR nx_web_http_server_minute; /* Minute */
    UCHAR nx_web_http_server_second; /* Second */
    UCHAR nx_web_http_server_weekday; /* Weekday */
} NX_WEB_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a><span data-ttu-id="e97bf-261">HTTP 캐시 정보 가져오기 콜백</span><span class="sxs-lookup"><span data-stu-id="e97bf-261">HTTP Cache Info Get Callback</span></span>

<span data-ttu-id="e97bf-262">HTTP 서버에는 특정 리소스에 대해 HTTP 애플리케이션에서 최대 사용 기간 및 날짜를 요청하기 위한 콜백이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-262">The HTTP Server has a callback to request the maximum age and date from the HTTP application for a specific resource.</span></span> <span data-ttu-id="e97bf-263">이 정보는 HTTP 서버가 클라이언트 Get 요청에 대한 응답으로 전체 페이지를 보내는지 여부를 확인하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-263">This information is used to determine if the HTTP server sends an entire page in response to a Client Get request.</span></span> <span data-ttu-id="e97bf-264">클라이언트 요청에서 “이후 수정 여부”를 찾을 수 없거나 캐시 가져오기 콜백으로 반환된 “마지막 수정” 날짜와 일치하지 않으면 전체 페이지가 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-264">If the “if modified since” in the Client request is not found or does not match the “last modified” date returned by the get cache callback, the entire page is sent.</span></span>

<span data-ttu-id="e97bf-265">콜백을 HTTP 서버에 등록하기 위해 다음 서비스가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-265">To register the callback with the HTTP server the following service is defined:</span></span>

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)
    (CHAR *, UINT *, NX_WEB_HTTP_SERVER_DATE *));
```

## <a name="http-chunked-transfer-coding-support"></a><span data-ttu-id="e97bf-266">HTTP 청크 분할 전송 코딩 지원</span><span class="sxs-lookup"><span data-stu-id="e97bf-266">HTTP Chunked Transfer Coding Support</span></span>

<span data-ttu-id="e97bf-267">HTTP 메시지를 보내기 전에 전체 길이를 확인할 수 없는 경우 청크 분할 전송 코딩 기능을 사용하여 “Content-Length” 헤더 필드 없이 메시지를 일련의 청크로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-267">When the total length of HTTP message cannot be determined before sending it, the Chunked Transfer Coding feature can be used to send messages as series of chunks without the “Content-Length” header field.</span></span> <span data-ttu-id="e97bf-268">이 기능은 모든 HTTP 요청 및 응답 메시지에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-268">This feature is supported in all HTTP request and response messages.</span></span> <span data-ttu-id="e97bf-269">이 기능은 받는 사람에게 지원되며 청크 헤더는 내부 논리에 의해 투명하게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-269">As a receiver, this feature is supported, and the chunk header is processed transparently by internal logic.</span></span> <span data-ttu-id="e97bf-270">보낸 사람인 경우에는 클라이언트와 서버에서 각각 API *nx_web_http_client_request_chunked_set* 및 *nx_web_http_server_response_chunked_set* 를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-270">As a sender, the API *nx_web_http_client_request_chunked_set* and *nx_web_http_server_response_chunked_set* must be invoked by client and server respectively.</span></span>

```C
UINT nx_web_http_client_request_chunked_set(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);

UINT nx_web_http_server_response_chunked_set(NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);
```

<span data-ttu-id="e97bf-271">이러한 서비스에 대한 자세한 내용은 3장 “HTTP 서비스 설명”을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e97bf-271">For more details on these services, see their descriptions in Chapter 3 “Description of HTTP Services”.</span></span>

## <a name="http-multipart-support"></a><span data-ttu-id="e97bf-272">HTTP 다중 파트 지원</span><span class="sxs-lookup"><span data-stu-id="e97bf-272">HTTP Multipart Support</span></span>

<span data-ttu-id="e97bf-273">MIME(Multipurpose Internet Mail Extensions)는 처음에 SMTP 프로토콜을 위해 만들어졌지만 사용 범위가 HTTP로 확장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-273">Multipurpose Internet Mail Extensions (MIME) was originally intended for the SMTP protocol, but its use has spread to HTTP.</span></span> <span data-ttu-id="e97bf-274">MIME를 사용하면 동일한 메시지 내에 혼합된 메시지 유형(예: 이미지/jpg 및 텍스트/일반)을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-274">MIME allows messages to contain mixed message types (e.g. image/jpg and text/plain) within the same message.</span></span> <span data-ttu-id="e97bf-275">NetX Web HTTP 서버에는 클라이언트의 MIME를 포함하는 HTTP 메시지에서 콘텐츠 유형을 확인하기 위한 서비스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-275">The NetX Web HTTP Server has services to determine content type in HTTP messages containing MIME from the Client.</span></span> <span data-ttu-id="e97bf-276">HTTP 다중 파트 지원을 사용하도록 설정하고 이러한 서비스를 사용하기 위해서는 구성 옵션 **NX_WEB_HTTP_MULTIPART_ENABLE** 이 정의되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-276">To enable HTTP multipart support and use these services, the configuration option **NX_WEB_HTTP_MULTIPART_ENABLE** must be defined.</span></span>

```C
UINT nx_web_http_server_get_entity_header(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);

UINT nx_web_http_server_get_entity_content(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

<span data-ttu-id="e97bf-277">이러한 서비스 사용에 대한 자세한 내용은 3장 “HTTP 서비스 설명”을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e97bf-277">For more details on the use of these services, see their description in Chapter 3 “Description of HTTP Services”.</span></span>

## <a name="http-multi-thread-support"></a><span data-ttu-id="e97bf-278">HTTP 다중 스레드 지원</span><span class="sxs-lookup"><span data-stu-id="e97bf-278">HTTP Multi-Thread Support</span></span>

<span data-ttu-id="e97bf-279">NetX Web HTTP 클라이언트 서비스는 다중 스레드에서 동시에 호출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-279">The NetX Web HTTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="e97bf-280">하지만 특정 HTTP 클라이언트 인스턴스에 대한 읽기 또는 쓰기 요청은 동일한 스레드에서 순차적으로 수행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-280">However, read or write requests for a particular HTTP Client instance should be done in sequence from the same thread.</span></span>

<span data-ttu-id="e97bf-281">HTTPS를 사용하는 경우 NetX Web HTTP 클라이언트 서비스는 다중 스레드에서 호출될 수 있지만, 기본 TLS 기능이 복잡해지지 않도록 각 스레드에는 독립적인 단일 HTTP 클라이언트 인스턴스(NX_WEB_HTTP_CLIENT 컨트롤 구조)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-281">If using HTTPS, NetX Web HTTP Client services may be called from multiple threads but due to the added complexity of the underlying TLS functionality each thread should have a single, independent HTTP Client instance (NX_WEB_HTTP_CLIENT control structure).</span></span>

## <a name="http-rfcs"></a><span data-ttu-id="e97bf-282">HTTP RFC</span><span class="sxs-lookup"><span data-stu-id="e97bf-282">HTTP RFCs</span></span>

<span data-ttu-id="e97bf-283">NetX Web HTTP는 RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2616 “Hypertext Transfer Protocol – HTTP/1.1”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts” 및 관련 RFC를 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-283">NetX Web HTTP is compliant with RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2616 “Hypertext Transfer Protocol – HTTP/1.1”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts”, and related RFCs.</span></span>

<span data-ttu-id="e97bf-284">HTTPS의 경우 NetX Web HTTP는 RFC 2818 “HTTP over TLS”를 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="e97bf-284">For HTTPS, NetX Web HTTP is compliant with RFC 2818 “HTTP over TLS”.</span></span>
