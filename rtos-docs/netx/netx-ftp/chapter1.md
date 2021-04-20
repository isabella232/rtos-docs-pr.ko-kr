---
title: 챕터 1 - Azure RTOS NetX FTP 소개
description: FTP(파일 전송 프로토콜)는 파일 전송을 위해 설계된 프로토콜입니다. FTP는 신뢰할 수 있는 TCP(Transmission Control Protocol) 서비스를 사용하여 파일 전송 기능을 수행합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86e132daf96f9039631234f10c8e239b61ad5126
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811550"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-ftp"></a><span data-ttu-id="76624-104">챕터 1 - Azure RTOS NetX FTP 소개</span><span class="sxs-lookup"><span data-stu-id="76624-104">Chapter 1 - Introduction to Azure RTOS NetX FTP</span></span>

<span data-ttu-id="76624-105">FTP(파일 전송 프로토콜)는 파일 전송을 위해 설계된 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="76624-105">The File Transfer Protocol (FTP) is a protocol designed for file transfers.</span></span> <span data-ttu-id="76624-106">FTP는 신뢰할 수 있는 TCP(Transmission Control Protocol) 서비스를 사용하여 파일 전송 기능을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-106">FTP utilizes reliable Transmission Control Protocol (TCP) services to perform its file transfer function.</span></span> <span data-ttu-id="76624-107">따라서 FTP는 신뢰성이 높은 파일 전송 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="76624-107">Because of this, FTP is a highly reliable file transfer protocol.</span></span> <span data-ttu-id="76624-108">또한 FTP는 성능이 뛰어납니다.</span><span class="sxs-lookup"><span data-stu-id="76624-108">FTP is also high-performance.</span></span> <span data-ttu-id="76624-109">실제 FTP 파일 전송은 전용 FTP 연결에서 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="76624-109">The actual FTP file transfer is performed on a dedicated FTP connection.</span></span>

## <a name="ftp-requirements"></a><span data-ttu-id="76624-110">FTP 요구 사항</span><span class="sxs-lookup"><span data-stu-id="76624-110">FTP Requirements</span></span>

<span data-ttu-id="76624-111">Azure RTOS NetX FTP 패키지를 제대로 작동하려면 NetX IP 인스턴스가 이미 생성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-111">In order to function properly, the Azure RTOS NetX FTP package requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="76624-112">또한 동일한 IP 인스턴스에서 TCP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-112">In addition, TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="76624-113">NetX FTP 패키지의 FTP 클라이언트 부분에는 추가 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-113">The FTP Client portion of the NetX FTP package has no further requirements.</span></span>

<span data-ttu-id="76624-114">NetX FTP 패키지의 FTP 서버 부분에는 여러 추가 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-114">The FTP Server portion of the NetX FTP package has several additional requirements.</span></span> <span data-ttu-id="76624-115">먼저 모든 클라이언트 FTP 명령 처리를 위해 TCP의 *잘 알려진 포트 21*, 모든 클라이언트 FTP 데이터 전송 처리를 위해 *잘 알려진 포트 20* 에 대한 완전한 액세스 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-115">First, it requires complete access to TCP *well-known port 21* for handling all Client FTP command requests and *well-known port 20* for handling all Client FTP data transfers.</span></span> <span data-ttu-id="76624-116">또한 FTP 서버는 FileX 포함된 파일 시스템에 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-116">The FTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="76624-117">FileX를 사용할 수 없으면 사용자가 사용된 FileX 부분을 자신의 고유 환경으로 이식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-117">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="76624-118">이에 대해서는 이 가이드의 이후 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-118">This is discussed in later sections of this guide.</span></span>

## <a name="ftp-constraints"></a><span data-ttu-id="76624-119">FTP 제약 조건</span><span class="sxs-lookup"><span data-stu-id="76624-119">FTP Constraints</span></span>

<span data-ttu-id="76624-120">FTP 표준에는 파일 데이터 표현과 관련된 많은 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-120">The FTP standard has many options regarding the representation of file data.</span></span> <span data-ttu-id="76624-121">Unix 구현과 마찬가지로 NetX FTP는 다음과 같은 파일 형식 제약 조건을 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-121">Similar to Unix implementations, NetX FTP assumes the following file format constraints:</span></span>

- <span data-ttu-id="76624-122">파일 형식: **이진**</span><span class="sxs-lookup"><span data-stu-id="76624-122">File Type: **Binary**</span></span>
- <span data-ttu-id="76624-123">파일 형식: **비 인쇄 전용**</span><span class="sxs-lookup"><span data-stu-id="76624-123">File Format: **Nonprint Only**</span></span>
- <span data-ttu-id="76624-124">파일 구조: **파일 구조만**</span><span class="sxs-lookup"><span data-stu-id="76624-124">File Structure: **File Structure Only**</span></span>
- <span data-ttu-id="76624-125">전송 모드: **스트림 모드만**</span><span class="sxs-lookup"><span data-stu-id="76624-125">Transmission Mode: **Stream Mode Only**</span></span>

## <a name="ftp-file-names"></a><span data-ttu-id="76624-126">FTP 파일 이름</span><span class="sxs-lookup"><span data-stu-id="76624-126">FTP File Names</span></span>

<span data-ttu-id="76624-127">FTP 파일 이름은 대상 파일 시스템(일반적으로 FileX)의 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-127">FTP file names should be in the format of the target file system (usually FileX).</span></span> <span data-ttu-id="76624-128">필요한 경우 전체 경로 정보를 포함하는 NULL 종료 ASCII 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-128">They should be NULL terminated ASCII strings, with full path information if necessary.</span></span> <span data-ttu-id="76624-129">NetX FTP 구현에서는 FTP 파일 이름 크기 제한이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-129">There is no specified limit for the size of FTP file names in the NetX FTP implementation.</span></span> <span data-ttu-id="76624-130">하지만 패킷 풀 페이로드 크기는 최대 경로 및/또는 파일 이름을 수용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-130">However, the packet pool payload size should be able to accommodate the maximum path and/or file name.</span></span>

## <a name="ftp-client-commands"></a><span data-ttu-id="76624-131">FTP 클라이언트 명령</span><span class="sxs-lookup"><span data-stu-id="76624-131">FTP Client Commands</span></span>

<span data-ttu-id="76624-132">FTP에는 연결을 열고 파일 및 디렉터리 작업을 수행하는 간편한 메커니즘이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-132">The FTP has a simple mechanism for opening connections and performing file and directory operations.</span></span> <span data-ttu-id="76624-133">기본적으로 TCP의 *잘 알려진 포트 21* 에서 연결이 성공적으로 설정된 후 클라이언트에서 실행되는 표준 FTP 명령 세트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-133">There is basically a set of standard FTP commands that are issued by the Client after a connection has been successfully established on the TCP *well-known port 21*.</span></span> <span data-ttu-id="76624-134">다음은 몇 가지 기본 FTP 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="76624-134">The following shows some of the basic FTP commands:</span></span>

### <a name="ftp-command-and-meaning"></a><span data-ttu-id="76624-135">FTP 명령 및 의미</span><span class="sxs-lookup"><span data-stu-id="76624-135">FTP Command and Meaning</span></span>

- <span data-ttu-id="76624-136">**CWD path**: *작업 디렉터리 변경*</span><span class="sxs-lookup"><span data-stu-id="76624-136">**CWD path**: *Change working directory*</span></span>
- <span data-ttu-id="76624-137">**DELE filename**: *지정된 파일 이름 삭제*</span><span class="sxs-lookup"><span data-stu-id="76624-137">**DELE filename**: *Delete specified file name*</span></span>
- <span data-ttu-id="76624-138">**LIST directory**: *디렉터리 목록 가져오기*</span><span class="sxs-lookup"><span data-stu-id="76624-138">**LIST directory**: *Get directory listing*</span></span>
- <span data-ttu-id="76624-139">**MKD directory**: *새 디렉터리 만들기*</span><span class="sxs-lookup"><span data-stu-id="76624-139">**MKD directory**: *Make new directory*</span></span>
- <span data-ttu-id="76624-140">**NLST directory**: *디렉터리 목록 가져오기*</span><span class="sxs-lookup"><span data-stu-id="76624-140">**NLST directory**: *Get directory listing*</span></span>
- <span data-ttu-id="76624-141">**NOOP**: *작업 없음, 성공 반환*</span><span class="sxs-lookup"><span data-stu-id="76624-141">**NOOP**: *No operation, returns success*</span></span>
- <span data-ttu-id="76624-142">**PASS password**: *로그인 암호 제공*</span><span class="sxs-lookup"><span data-stu-id="76624-142">**PASS password**: *Provide password for login*</span></span>
- <span data-ttu-id="76624-143">**PASV**: *수동 전송 모드 요청*</span><span class="sxs-lookup"><span data-stu-id="76624-143">**PASV**: *Request passive transfer mode*</span></span>
- <span data-ttu-id="76624-144">**PWD path**: *현재 디렉터리 경로 픽업*</span><span class="sxs-lookup"><span data-stu-id="76624-144">**PWD path**: *Pickup current directory path*</span></span>
- <span data-ttu-id="76624-145">**QUIT**: *클라이언트 연결 종료*</span><span class="sxs-lookup"><span data-stu-id="76624-145">**QUIT**: *Terminate Client connection*</span></span>
- <span data-ttu-id="76624-146">**RETR filename**: *지정된 파일 읽기*</span><span class="sxs-lookup"><span data-stu-id="76624-146">**RETR filename**: *Read specified file*</span></span>
- <span data-ttu-id="76624-147">**RMD directory**: *지정된 디렉터리 삭제*</span><span class="sxs-lookup"><span data-stu-id="76624-147">**RMD directory**: *Delete specified directory*</span></span>
- <span data-ttu-id="76624-148">**RNFR oldfilename**: *이름을 바꿀 파일 지정*</span><span class="sxs-lookup"><span data-stu-id="76624-148">**RNFR oldfilename**: *Specify file to rename*</span></span>
- <span data-ttu-id="76624-149">**RNTO newfilename**: *제공된 파일 이름으로 파일 이름 바꾸기*</span><span class="sxs-lookup"><span data-stu-id="76624-149">**RNTO newfilename**: *Rename file to supplied file name*</span></span>
- <span data-ttu-id="76624-150">**STOR filename**: *지정된 파일 쓰기*</span><span class="sxs-lookup"><span data-stu-id="76624-150">**STOR filename**: *Write specified file*</span></span>
- <span data-ttu-id="76624-151">**TYPE I**: *이진 파일 이미지 선택*</span><span class="sxs-lookup"><span data-stu-id="76624-151">**TYPE I**: *Select binary file image*</span></span>
- <span data-ttu-id="76624-152">**USER username**: *로그인 사용자 이름 입력*</span><span class="sxs-lookup"><span data-stu-id="76624-152">**USER username**: *Provide username for login*</span></span>
- <span data-ttu-id="76624-153">**PORT ip_address,port**: *IP 주소 및 클라이언트 데이터 포트 제공*</span><span class="sxs-lookup"><span data-stu-id="76624-153">**PORT ip_address,port**: *Provide IP address and Client data port*</span></span>

<span data-ttu-id="76624-154">이러한 ASCII 명령은 NetX FTP 클라이언트 소프트웨어 내부에서 FTP 서버를 사용하는 FTP 작업을 수행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-154">These ASCII commands are used internally by the NetX FTP Client software to perform FTP operations with the FTP Server.</span></span>

## <a name="ftp-server-responses"></a><span data-ttu-id="76624-155">FTP 서버 응답</span><span class="sxs-lookup"><span data-stu-id="76624-155">FTP Server Responses</span></span>

<span data-ttu-id="76624-156">FTP 서버는 필드 클라이언트 명령 요청에 대해 *잘 알려진 TCP 포트 21* 을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-156">The FTP Server utilizes the *well-known TCP port 21* to field Client command requests.</span></span> <span data-ttu-id="76624-157">FTP 서버가 클라이언트 명령을 처리한 후 ASCII 형식의 3자리 숫자 응답과 선택 사항인 ASCII 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-157">Once the FTP Server processes the Client command, it returns a 3-digit numeric response in ASCII followed by an optional ASCII string.</span></span> <span data-ttu-id="76624-158">이 숫자 응답은 FTP 클라이언트 소프트웨어가 작업 성공 또는 실패 여부를 확인하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-158">The numeric response is used by the FTP Client software to determine whether the operation succeeded or failed.</span></span> <span data-ttu-id="76624-159">다음은 클라이언트 명령에 대한 다양한 FTP 서버 응답 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="76624-159">The following lists various FTP Server responses to Client commands:</span></span>

### <a name="first-numeric-field-and-meaning"></a><span data-ttu-id="76624-160">첫 번째 숫자 필드 및 의미</span><span class="sxs-lookup"><span data-stu-id="76624-160">First Numeric Field and Meaning</span></span>

- <span data-ttu-id="76624-161">**1xx**: *긍정 예비 상태 - 또 다른 회신 수신*.</span><span class="sxs-lookup"><span data-stu-id="76624-161">**1xx**: *Positive preliminary status – another reply coming*.</span></span>
- <span data-ttu-id="76624-162">**2xx**: *긍정 완료 상태*.</span><span class="sxs-lookup"><span data-stu-id="76624-162">**2xx**: *Positive completion status*.</span></span>
- <span data-ttu-id="76624-163">**3xx**: *긍정 예비 상태 - 또 다른 명령을 전송해야 함*.</span><span class="sxs-lookup"><span data-stu-id="76624-163">**3xx**: *Positive preliminary status – another command must be sent*.</span></span>
- <span data-ttu-id="76624-164">**4xx**: *임시 오류 조건*.</span><span class="sxs-lookup"><span data-stu-id="76624-164">**4xx**: *Temporary error condition*.</span></span>
- <span data-ttu-id="76624-165">**5xx**: *오류 조건.*</span><span class="sxs-lookup"><span data-stu-id="76624-165">**5xx**: *Error condition.*</span></span>

### <a name="second-numeric-field-and-meaning"></a><span data-ttu-id="76624-166">두 번째 숫자 필드 및 의미</span><span class="sxs-lookup"><span data-stu-id="76624-166">Second Numeric Field and Meaning</span></span>

- <span data-ttu-id="76624-167">**x0x**: 명령의 구문 오류.</span><span class="sxs-lookup"><span data-stu-id="76624-167">**x0x**: Syntax error in command.</span></span>
- <span data-ttu-id="76624-168">**x1x**: 정보 메시지.</span><span class="sxs-lookup"><span data-stu-id="76624-168">**x1x**: Informational message.</span></span>
- <span data-ttu-id="76624-169">**x2x**: 연결 관련.</span><span class="sxs-lookup"><span data-stu-id="76624-169">**x2x**: Connection related.</span></span>
- <span data-ttu-id="76624-170">**x3x**: 인증 관련.</span><span class="sxs-lookup"><span data-stu-id="76624-170">**x3x**: Authentication related.</span></span>
- <span data-ttu-id="76624-171">**x4x**: 지정되지 않음.</span><span class="sxs-lookup"><span data-stu-id="76624-171">**x4x**: Unspecified.</span></span>
- <span data-ttu-id="76624-172">**x5x**: 파일 시스템 관련.</span><span class="sxs-lookup"><span data-stu-id="76624-172">**x5x**: File system related.</span></span>

<span data-ttu-id="76624-173">예를 들어 QUIT 명령을 사용하여 FTP 연결을 해제하는 클라이언트 요청에 대해 일반적으로 서버에서 "221" 코드를 사용하여 응답합니다(연결 해제가 완료된 경우).</span><span class="sxs-lookup"><span data-stu-id="76624-173">For example, a Client request to disconnect an FTP connection with the QUIT command will typically be responded with a "221" code from the Server – if the disconnect is successful.</span></span>

## <a name="ftp-passive-transfer-mode"></a><span data-ttu-id="76624-174">FTP 수동 전송 모드</span><span class="sxs-lookup"><span data-stu-id="76624-174">FTP Passive Transfer Mode</span></span>

<span data-ttu-id="76624-175">기본적으로 NetX FTP 클라이언트는 활성 전송 모드를 사용하여 FTP 서버와 데이터 소켓을 통해 데이터를 교환합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-175">By default, the NetX FTP Client uses the active transport mode to exchange data over the data socket with the FTP server.</span></span> <span data-ttu-id="76624-176">이에 대한 문제는 FTP 클라이언트에서 FTP 서버에 연결할 TCP 서버 소켓을 열어야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="76624-176">The problem with this arrangement is that it requires the FTP Client to open a TCP server socket for the FTP Server to connect to.</span></span> <span data-ttu-id="76624-177">이는 가능한 보안 위험을 나타내며 클라이언트 방화벽에 의해 차단될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-177">This represents a possible security risk and may be blocked by the Client firewall.</span></span> <span data-ttu-id="76624-178">수동 전송 모드는 FTP 서버에서 데이터 연결에 TCP 서버 소켓을 만들도록 하므로 활성 전송 모드와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-178">Passive transfer mode differs from active transport mode by having the FTP server create the TCP server socket on the data connection.</span></span> <span data-ttu-id="76624-179">이렇게 하면 (FTP 클라이언트에 대한) 보안 위험이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-179">This eliminates the security risk (for the FTP Client).</span></span>

<span data-ttu-id="76624-180">수동 데이터 전송을 사용하도록 두 번째 인수를 NX_TRUE로 설정하여 이전에 생성되었던 FTP 클라이언트에서 애플리케이션이 *nx_ftp_client_passive_mode_set* 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-180">To enable passive data transfer, the application calls *nx_ftp_client_passive_mode_set* on a previously created FTP Client with the second argument set to NX_TRUE.</span></span> <span data-ttu-id="76624-181">이후에 데이터를 전송하는 모든 후속 NetX FTP 클라이언트 서비스(NLST, RETR, STOR)는 수동 전송 모드에서 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-181">Thereafter, all subsequent NetX FTP Client services for transferring data (NLST, RETR, STOR) are attempted in the passive transport mode.</span></span>

<span data-ttu-id="76624-182">FTP 클라이언트는 먼저 PASV 명령(인수 없음)을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-182">The FTP Client first sends the PASV command (no arguments).</span></span> <span data-ttu-id="76624-183">FTP 서버에서 이 요청을 지원하는 경우 227 "OK" 응답을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-183">If the FTP server supports this request it will return the 227 "OK" response.</span></span> <span data-ttu-id="76624-184">그런 다음, 클라이언트가 요청을 보냅니다(예: RETR).</span><span class="sxs-lookup"><span data-stu-id="76624-184">Then the Client sends the request e.g. RETR.</span></span> <span data-ttu-id="76624-185">서버에서 수동 전송 모드를 거부하는 경우 NetX FTP 클라이언트 서비스는 오류 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-185">If the server refuses passive transfer mode, the NetX FTP Client service returns an error status.</span></span>

<span data-ttu-id="76624-186">수동 전송 모드를 사용하지 않도록 설정하고 활성 전송 모드를 반환하도록 애플리케이션에서 두 번째 인수가 NX_FALSE로 설정된 *nx_ftp_client_passive_mode_set* 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-186">To disable passive transport mode and return to active transport mode, the application calls *nx_ftp_client_passive_mode_set* with the second argument set to NX_FALSE.</span></span>

## <a name="ftp-communication"></a><span data-ttu-id="76624-187">FTP 통신</span><span class="sxs-lookup"><span data-stu-id="76624-187">FTP Communication</span></span>

<span data-ttu-id="76624-188">FTP 서버는 필드 클라이언트 요청에 대해 *잘 알려진 TCP 포트 21* 을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-188">The FTP Server utilizes the *well-known TCP port 21* to field Client requests.</span></span> <span data-ttu-id="76624-189">FTP 클라이언트는 사용 가능한 모든 TCP 포트를 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-189">FTP Clients may use any available TCP port.</span></span> <span data-ttu-id="76624-190">FTP 이벤트의 일반 시퀀스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-190">The general sequence of FTP events is as follows:</span></span>

### <a name="ftp-read-file-requests"></a><span data-ttu-id="76624-191">FTP 파일 읽기 요청</span><span class="sxs-lookup"><span data-stu-id="76624-191">FTP Read File Requests</span></span>

1. <span data-ttu-id="76624-192">클라이언트가 서버 포트 21에 TCP 연결을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-192">Client issues TCP connect to Server port 21.</span></span>
1. <span data-ttu-id="76624-193">서버에서 신호 성공에 "220" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-193">Server sends "220" response to signal success.</span></span>
1. <span data-ttu-id="76624-194">클라이언트에서 "사용자"를 포함한 "USER" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-194">Client sends "USER" message with "username."</span></span>
1. <span data-ttu-id="76624-195">서버에서 신호 성공에 "331" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-195">Server sends "331" response to signal success.</span></span>
1. <span data-ttu-id="76624-196">클라이언트에서 "암호"를 포함한 "PASS" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-196">Client sends "PASS" message with "password."</span></span>
1. <span data-ttu-id="76624-197">서버에서 신호 성공에 "230" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-197">Server sends "230" response to signal success.</span></span>
1. <span data-ttu-id="76624-198">클라이언트에서 이진 전송에 대해 "TYPE I" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-198">Client sends "TYPE I" message for binary transfer.</span></span>
1. <span data-ttu-id="76624-199">서버에서 신호 성공에 "200" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-199">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="76624-200">클라이언트에서 IP 주소 및 포트를 포함한 "PORT" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-200">Client sends "PORT" message with IP address and port.</span></span>
1. <span data-ttu-id="76624-201">서버에서 신호 성공에 "200" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-201">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="76624-202">클라이언트에서 읽을 파일 이름을 포함한 "RETR" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-202">Client sends "RETR" message with file name to read.</span></span>
1. <span data-ttu-id="76624-203">서버에서 데이터 소켓을 만들고 "PORT" 명령에 지정된 클라이언트 데이터 포트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-203">Server creates data socket and connects with client data port specified in the "PORT" command.</span></span>
1. <span data-ttu-id="76624-204">서버에서 "125" 응답을 보내 파일 읽기가 시작되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-204">Server sends "125" response to signal file read has started.</span></span>
1. <span data-ttu-id="76624-205">서버에서 데이터 연결을 통해 파일의 내용을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-205">Server sends contents of file through the data connection.</span></span> <span data-ttu-id="76624-206">이 프로세스는 파일이 완전히 전송될 때까지 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-206">This process continues until file is completely transferred.</span></span>
1. <span data-ttu-id="76624-207">완료되면 서버에서 데이터 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-207">When finished, Server disconnects data connection.</span></span>
1. <span data-ttu-id="76624-208">서버에서 "250" 응답을 보내 파일 읽기가 성공적임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-208">Server sends "250" response to signal file read is successful.</span></span>
1. <span data-ttu-id="76624-209">클라이언트에서 "QUIT"을 보내 FTP 연결을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-209">Clients sends "QUIT" to terminate FTP connection.</span></span>
1. <span data-ttu-id="76624-210">서버에서 "221" 응답을 보내 신호 연결 해제에 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-210">Server sends "221" response to signal disconnect is successful.</span></span>
1. <span data-ttu-id="76624-211">서버에서 FTP 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-211">Server disconnects FTP connection.</span></span>

<span data-ttu-id="76624-212">앞에서 설명한 것처럼 IPv4와 IPv6를 통해 실행되는 FTP의 유일한 차이점은 IPv6의 경우 PORT 명령이 EPRT 명령으로 바뀐다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="76624-212">As mentioned previously, the only difference between FTP running over IPv4 and IPv6 is the PORT command is replaced with the EPRT command for IPv6</span></span>

<span data-ttu-id="76624-213">FTP 클라이언트가 수동 전송 모드에서 읽기 요청을 수행하는 경우 명령 시퀀스는 다음과 같습니다(**굵게** 표시된 줄은 활성 전송 모드에서 단계가 다름을 의미함).</span><span class="sxs-lookup"><span data-stu-id="76624-213">If the FTP Client makes a read request in the passive transfer mode, the command sequence is as follows (**bolded** lines indicates a different step from active transfer mode):</span></span>

1. <span data-ttu-id="76624-214">클라이언트가 서버 포트 21에 TCP 연결을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-214">Client issues TCP connect to Server port 21.</span></span>
1. <span data-ttu-id="76624-215">서버에서 신호 성공에 "220" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-215">Server sends "220" response to signal success.</span></span>
1. <span data-ttu-id="76624-216">클라이언트에서 "사용자"를 포함한 "USER" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-216">Client sends "USER" message with "username."</span></span>
1. <span data-ttu-id="76624-217">서버에서 신호 성공에 "331" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-217">Server sends "331" response to signal success.</span></span>
1. <span data-ttu-id="76624-218">클라이언트에서 "암호"를 포함한 "PASS" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-218">Client sends "PASS" message with "password."</span></span>
1. <span data-ttu-id="76624-219">서버에서 신호 성공에 "230" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-219">Server sends "230" response to signal success.</span></span>
1. <span data-ttu-id="76624-220">클라이언트에서 이진 전송에 대해 "TYPE I" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-220">Client sends "TYPE I" message for binary transfer.</span></span>
1. <span data-ttu-id="76624-221">서버에서 신호 성공에 "200" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-221">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="76624-222">**클라이언트에서 "PASV" 메시지를 보냅니다.**</span><span class="sxs-lookup"><span data-stu-id="76624-222">**Client sends "PASV" message.**</span></span>
1. <span data-ttu-id="76624-223">**서버에서 "227" 응답, 연결할 클라이언트에 대한 IP 주소 및 포트를 보내 성공을 나타냅니다.**</span><span class="sxs-lookup"><span data-stu-id="76624-223">**Server sends "227" response, and IP address and port for the Client to connect to, to signal success.**</span></span>
1. <span data-ttu-id="76624-224">클라이언트에서 읽을 파일 이름을 포함한 "RETR" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-224">Client sends "RETR" message with file name to read.</span></span>
1. <span data-ttu-id="76624-225">**서버에서 데이터 서버 소켓을 만들고 "227" 응답에 지정된 포트를 사용하여 이 소켓에서 클라이언트 연결 요청을 수신합니다.**</span><span class="sxs-lookup"><span data-stu-id="76624-225">**Server creates data server socket and listens for the Client connect request on this socket using the port specified in the "227" response.**</span></span>
1. <span data-ttu-id="76624-226">**서버에서 제어 소켓에 "150" 응답을 보내 파일 읽기가 시작되었음을 나타냅니다.**</span><span class="sxs-lookup"><span data-stu-id="76624-226">**Server sends "150" response on the control socket to signal file read has started.**</span></span>
1. <span data-ttu-id="76624-227">서버에서 데이터 연결을 통해 파일의 내용을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-227">Server sends contents of file through the data connection.</span></span> <span data-ttu-id="76624-228">이 프로세스는 파일이 완전히 전송될 때까지 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-228">This process continues until file is completely transferred.</span></span>
1. <span data-ttu-id="76624-229">완료되면 서버에서 데이터 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-229">When finished, Server disconnects data connection.</span></span>
1. <span data-ttu-id="76624-230">**서버에서 제어 소켓에 "226" 응답을 보내 파일 읽기에 성공했음을 나타냅니다.**</span><span class="sxs-lookup"><span data-stu-id="76624-230">**Server sends "226" response on the control socket to signal file read is successful.**</span></span>
1. <span data-ttu-id="76624-231">클라이언트에서 "QUIT"을 보내 FTP 연결을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-231">Client sends "QUIT" to terminate FTP connection.</span></span>
1. <span data-ttu-id="76624-232">서버에서 "221" 응답을 보내 신호 연결 해제에 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-232">Server sends "221" response to signal disconnect is successful.</span></span>
1. <span data-ttu-id="76624-233">서버에서 FTP 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-233">Server disconnects FTP connection.</span></span>

### <a name="ftp-write-requests"></a><span data-ttu-id="76624-234">FTP 쓰기 요청</span><span class="sxs-lookup"><span data-stu-id="76624-234">FTP Write Requests</span></span>

1. <span data-ttu-id="76624-235">클라이언트가 서버 포트 21에 TCP 연결을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-235">Client issues TCP connect to Server port 21.</span></span>
1. <span data-ttu-id="76624-236">서버에서 신호 성공에 "220" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-236">Server sends "220" response to signal success.</span></span>
1. <span data-ttu-id="76624-237">클라이언트에서 "사용자"를 포함한 "USER" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-237">Client sends "USER" message with "username."</span></span>
1. <span data-ttu-id="76624-238">서버에서 신호 성공에 "331" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-238">Server sends "331" response to signal success.</span></span>
1. <span data-ttu-id="76624-239">클라이언트에서 "암호"를 포함한 "PASS" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-239">Client sends "PASS" message with "password."</span></span>
1. <span data-ttu-id="76624-240">서버에서 신호 성공에 "230" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-240">Server sends "230" response to signal success.</span></span>
1. <span data-ttu-id="76624-241">클라이언트에서 이진 전송에 대해 "TYPE I" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-241">Client sends "TYPE I" message for binary transfer.</span></span>
1. <span data-ttu-id="76624-242">서버에서 신호 성공에 "200" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-242">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="76624-243">클라이언트에서 IP 주소 및 포트를 포함한 "PORT" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-243">Client sends "PORT" message with IP address and port.</span></span>
1. <span data-ttu-id="76624-244">서버에서 신호 성공에 "200" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-244">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="76624-245">클라이언트에서 쓸 파일 이름을 포함한 "STOR" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-245">Client sends "STOR" message with file name to write.</span></span>
1. <span data-ttu-id="76624-246">서버에서 데이터 소켓을 만들고 "PORT" 명령에 지정된 클라이언트 데이터 포트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-246">Server creates data socket and connects with client data port specified in the "PORT" command.</span></span>
1. <span data-ttu-id="76624-247">서버에서 "125" 응답을 보내 파일 쓰기가 시작되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-247">Server sends "125" response to signal file write has started.</span></span>
1. <span data-ttu-id="76624-248">클라이언트에서 데이터 연결을 통해 파일의 내용을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-248">Client sends contents of file through the data connection.</span></span> <span data-ttu-id="76624-249">이 프로세스는 파일이 완전히 전송될 때까지 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-249">This process continues until file is completely transferred.</span></span>
1. <span data-ttu-id="76624-250">완료되면 클라이언트에서 데이터 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-250">When finished, Client disconnects data connection.</span></span>
1. <span data-ttu-id="76624-251">서버에서 "250" 응답을 보내 파일 쓰기가 성공적임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-251">Server sends "250" response to signal file write is successful.</span></span>
1. <span data-ttu-id="76624-252">클라이언트에서 "QUIT"을 보내 FTP 연결을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-252">Clients sends "QUIT" to terminate FTP connection.</span></span>
1. <span data-ttu-id="76624-253">서버에서 "221" 응답을 보내 신호 연결 해제에 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-253">Server sends "221" response to signal disconnect is successful.</span></span>
1. <span data-ttu-id="76624-254">서버에서 FTP 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-254">Server disconnects FTP connection.</span></span>

<span data-ttu-id="76624-255">FTP 클라이언트가 수동 전송 모드에서 쓰기 요청을 수행하는 경우 명령 시퀀스는 다음과 같습니다(**굵게** 표시된 줄은 활성 전송 모드에서 단계가 다름을 의미함).</span><span class="sxs-lookup"><span data-stu-id="76624-255">If the FTP Client makes a write request in the passive transfer mode, the command sequence is as follows (**bolded** lines indicates a different step from active transfer mode):</span></span>

1. <span data-ttu-id="76624-256">클라이언트가 서버 포트 21에 TCP 연결을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-256">Client issues TCP connect to Server port 21.</span></span>
1. <span data-ttu-id="76624-257">서버에서 신호 성공에 "220" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-257">Server sends "220" response to signal success.</span></span>
1. <span data-ttu-id="76624-258">클라이언트에서 "사용자"를 포함한 "USER" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-258">Client sends "USER" message with "username."</span></span>
1. <span data-ttu-id="76624-259">서버에서 신호 성공에 "331" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-259">Server sends "331" response to signal success.</span></span>
1. <span data-ttu-id="76624-260">클라이언트에서 "암호"를 포함한 "PASS" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-260">Client sends "PASS" message with "password."</span></span>
1. <span data-ttu-id="76624-261">서버에서 신호 성공에 "230" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-261">Server sends "230" response to signal success.</span></span>
1. <span data-ttu-id="76624-262">클라이언트에서 이진 전송에 대해 "TYPE I" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-262">Client sends "TYPE I" message for binary transfer.</span></span>
1. <span data-ttu-id="76624-263">서버에서 신호 성공에 "200" 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-263">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="76624-264">**클라이언트에서 "PASV" 메시지를 보냅니다.**</span><span class="sxs-lookup"><span data-stu-id="76624-264">**Client sends "PASV" message.**</span></span>
1. <span data-ttu-id="76624-265">**서버에서 "227" 응답, 연결할 클라이언트에 대한 IP 주소 및 포트를 보내 성공을 나타냅니다.**</span><span class="sxs-lookup"><span data-stu-id="76624-265">**Server sends "227" response, and IP address and port for the Client to connect to, to signal success.**</span></span>
1. <span data-ttu-id="76624-266">클라이언트에서 쓸 파일 이름을 포함한 "STOR" 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-266">Client sends "STOR" message with file name to write.</span></span>
1. <span data-ttu-id="76624-267">**서버에서 데이터 서버 소켓을 만들고 "227" 응답에 지정된 포트를 사용하여 이 소켓에서 클라이언트 연결 요청을 수신합니다.**</span><span class="sxs-lookup"><span data-stu-id="76624-267">**Server creates data server socket and listens for the Client connect request on this socket using the port specified in the "227" response.**</span></span>
1. <span data-ttu-id="76624-268">**서버에서 제어 소켓에 "150" 응답을 보내 파일 쓰기가 시작되었음을 나타냅니다.**</span><span class="sxs-lookup"><span data-stu-id="76624-268">**Server sends "150" response on the control socket to signal file write has started.**</span></span>
1. <span data-ttu-id="76624-269">클라이언트에서 데이터 연결을 통해 파일의 내용을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-269">Client sends contents of file through the data connection.</span></span> <span data-ttu-id="76624-270">이 프로세스는 파일이 완전히 전송될 때까지 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-270">This process continues until file is completely transferred.</span></span>
1. <span data-ttu-id="76624-271">완료되면 클라이언트에서 데이터 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-271">When finished, Client disconnects data connection.</span></span>
1. <span data-ttu-id="76624-272">**서버에서 제어 소켓에 "226" 응답을 보내 파일 쓰기에 성공했음을 나타냅니다.**</span><span class="sxs-lookup"><span data-stu-id="76624-272">**Server sends "226" response on the control socket to signal file write is successful.**</span></span>
1. <span data-ttu-id="76624-273">클라이언트에서 "QUIT"을 보내 FTP 연결을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-273">Client sends "QUIT" to terminate FTP connection.</span></span>
1. <span data-ttu-id="76624-274">서버에서 "221" 응답을 보내 신호 연결 해제에 성공했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76624-274">Server sends "221" response to signal disconnect is successful.</span></span>
1. <span data-ttu-id="76624-275">서버에서 FTP 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-275">Server disconnects FTP connection.</span></span>

## <a name="ftp-authentication"></a><span data-ttu-id="76624-276">FTP Authentication</span><span class="sxs-lookup"><span data-stu-id="76624-276">FTP Authentication</span></span>

<span data-ttu-id="76624-277">FTP 연결이 이루어질 때마다 클라이언트는 서버는 *사용자 이름* 과 *암호* 를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-277">Whenever an FTP connection takes place, the Client must provide the Server with a *username* and *password*.</span></span> <span data-ttu-id="76624-278">일부 FTP 사이트에서는 특정 사용자 이름 및 암호 없이 FTP 액세스를 허용하는 *익명 FTP* 를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-278">Some FTP sites allow what is called *Anonymous FTP*, which allows FTP access without a specific username and password.</span></span> <span data-ttu-id="76624-279">이러한 유형의 연결에서는 사용자 이름에 "anonymous"를 입력해야 하며 암호는 전체 이메일 주소여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-279">For this type of connection, "anonymous" should be supplied for username and the password should be a complete e-mail address.</span></span>

<span data-ttu-id="76624-280">사용자는 로그인 및 로그아웃 인증 루틴이 포함된 NetX FTP를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76624-280">The user is responsible for supplying NetX FTP with login and logout authentication routines.</span></span> <span data-ttu-id="76624-281">\***nx_ftp_server_create** _ 함수 중에 제공되어 암호 처리에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-281">These are supplied during the \***nx_ftp_server_create** _ function and called from the password processing.</span></span> <span data-ttu-id="76624-282">_login\* 함수가 NX_SUCCESS를 반환하는 경우 연결이 인증되고 FTP 작업이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-282">If the _login\* function returns NX_SUCCESS, the connection is authenticated and FTP operations are allowed.</span></span> <span data-ttu-id="76624-283">반대로 *login* 함수가 NX_SUCCESS 이외의 것을 반환하는 경우 연결 시도가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-283">Otherwise, if the *login* function returns something other than NX_SUCCESS, the connection attempt is rejected.</span></span>

## <a name="ftp-multi-thread-support"></a><span data-ttu-id="76624-284">FTP 다중 스레드 지원</span><span class="sxs-lookup"><span data-stu-id="76624-284">FTP Multi-Thread Support</span></span>

<span data-ttu-id="76624-285">NetX FTP 클라이언트 서비스는 다중 스레드에서 동시에 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-285">The NetX FTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="76624-286">하지만 특정 FTP 클라이언트 인스턴에 대한 읽기 또는 쓰기 요청을 동일 스레드에서 순차적으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76624-286">However, read or write requests for a particular FTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="ftp-rfcs"></a><span data-ttu-id="76624-287">FTP RFC</span><span class="sxs-lookup"><span data-stu-id="76624-287">FTP RFCs</span></span>

<span data-ttu-id="76624-288">NetX FTP는 RFC959 및 관련 RFC와 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="76624-288">NetX FTP is compliant with RFC959 and related RFCs.</span></span>