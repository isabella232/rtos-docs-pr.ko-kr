---
title: 1장 - Azure RTOS NetX Duo TFTP 소개
description: TFTP(Trivial File Transfer Protocol)는 파일 전송을 위해 디자인된 간단한 프로토콜입니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4431b23e143d05214090547e7f179a6f5def8217
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810525"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a><span data-ttu-id="15b26-103">1장 - Azure RTOS NetX Duo TFTP 소개</span><span class="sxs-lookup"><span data-stu-id="15b26-103">Chapter 1 - Introduction to Azure RTOS NetX Duo TFTP</span></span> 

<span data-ttu-id="15b26-104">TFTP(Trivial File Transfer Protocol)는 파일 전송을 위해 디자인된 간단한 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-104">The Trivial File Transfer Protocol (TFTP) is a lightweight protocol designed for file transfers.</span></span> <span data-ttu-id="15b26-105">좀 더 강력한 프로토콜과 달리 TFTP는 광범위한 오류 검사를 수행하지 않으며 중지 후 대기 프로토콜에 해당하므로 성능이 제한될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-105">Unlike more robust protocols, TFTP does not perform extensive error checking and can also have limited performance because it is a stop-and-wait protocol.</span></span> <span data-ttu-id="15b26-106">TFTP 데이터 패킷이 전송되면 보낸 사람은 받는 사람이 ACK를 반환할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-106">After a TFTP data packet is sent, the sender waits for an ACK to be returned by the recipient.</span></span> <span data-ttu-id="15b26-107">이 과정은 간단하지만 전반적인 TFTP 처리량을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-107">Although this is simple, it does limit the overall TFTP throughput.</span></span> <span data-ttu-id="15b26-108">TFTP 패키지를 사용하면 호스트에서 IP 네트워크를 통해 TFTP 프로토콜을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-108">The TFTP package enables hosts to use the TFTP protocol over IP networks.</span></span>

## <a name="tftp-requirements"></a><span data-ttu-id="15b26-109">TFTP 요구 사항</span><span class="sxs-lookup"><span data-stu-id="15b26-109">TFTP Requirements</span></span>

<span data-ttu-id="15b26-110">올바른 작동을 위해 NetX Duo TFTP 패키지의 TFTP 클라이언트 부분에는 IP 인스턴스가 이미 생성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-110">In order to function properly, the TFTP Clients portion of the NetX Duo TFTP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="15b26-111">또한 동일한 IP 인스턴스에서 UDP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-111">In addition, UDP must be enabled on that same IP instance.</span></span> <span data-ttu-id="15b26-112">NetX Duo TFTP 패키지의 클라이언트 부분에는 추가 요구 사항이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-112">The Client portion of the NetX Duo TFTP package has no further requirements.</span></span>

<span data-ttu-id="15b26-113">NetX Duo TFTP 패키지의 TFTP 서버 부분에는 여러 추가 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-113">The TFTP Server portion of the NetX Duo TFTP package has several additional requirements.</span></span> <span data-ttu-id="15b26-114">먼저 모든 클라이언트 TFTP 요청을 처리하려면 UDP의 잘 알려진 포트 69에 대한 완전한 액세스 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-114">First, it requires complete access to the UDP *well known port 69* for handling all client TFTP requests.</span></span> <span data-ttu-id="15b26-115">또한 TFTP 서버는 FileX 포함된 파일 시스템에 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-115">The TFTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="15b26-116">FileX를 사용할 수 없으면 사용자가 사용된 FileX 부분을 자신의 고유 환경으로 이식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-116">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="15b26-117">이에 대해서는 이 가이드의 이후 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-117">This is discussed in later sections of this guide.</span></span>

## <a name="tftp-file-names"></a><span data-ttu-id="15b26-118">TFTP 파일 이름</span><span class="sxs-lookup"><span data-stu-id="15b26-118">TFTP File Names</span></span> 

<span data-ttu-id="15b26-119">TFTP 파일 이름은 대상 파일 시스템의 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-119">TFTP file names should be in the format of the target file system.</span></span> <span data-ttu-id="15b26-120">필요한 경우 전체 경로 정보를 포함하는 NULL 종료 ASCII 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-120">They should be NULL terminated ASCII strings, with full path information if necessary.</span></span> <span data-ttu-id="15b26-121">NetX Duo TFTP 구현에서는 TFTP 파일 이름 크기 제한이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-121">There is no specified limit in the size of TFTP file names in the NetX Duo TFTP implementation.</span></span>

## <a name="tftp-messages"></a><span data-ttu-id="15b26-122">TFTP 메시지</span><span class="sxs-lookup"><span data-stu-id="15b26-122">TFTP Messages</span></span>

<span data-ttu-id="15b26-123">TFTP에는 파일 열기, 읽기, 쓰기 및 닫기를 위한 매우 간단한 메커니즘이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-123">The TFTP has a very simple mechanism for opening, reading, writing, and closing files.</span></span> <span data-ttu-id="15b26-124">UDP 헤더 아래에는 기본적으로 2-4바이트의 TFTP 헤더가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-124">There are basically 2-4 bytes of TFTP header underneath the UDP header.</span></span> <span data-ttu-id="15b26-125">TFTP 파일 열기 메시지의 정의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-125">The definition of the TFTP file open messages has the following format:</span></span>

<span data-ttu-id="15b26-126">**oooof…f0OCTET0**</span><span class="sxs-lookup"><span data-stu-id="15b26-126">**oooof…f0OCTET0**</span></span>

<span data-ttu-id="15b26-127">위치:</span><span class="sxs-lookup"><span data-stu-id="15b26-127">Where:</span></span>

- <span data-ttu-id="15b26-128">**oooo** 2바이트 Opcode 필드</span><span class="sxs-lookup"><span data-stu-id="15b26-128">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="15b26-129">0x0001 -> 읽기 위해 열기</span><span class="sxs-lookup"><span data-stu-id="15b26-129">0x0001 -> Open for read</span></span>  
<span data-ttu-id="15b26-130">0x0002 -> 쓰기 위해 열기</span><span class="sxs-lookup"><span data-stu-id="15b26-130">0x0002 -> Open for write</span></span>

- <span data-ttu-id="15b26-131">**f…f** n바이트 파일 이름 필드</span><span class="sxs-lookup"><span data-stu-id="15b26-131">**f…f** n-byte Filename field</span></span>

- <span data-ttu-id="15b26-132">0  1바이트 NULL 종료 문자</span><span class="sxs-lookup"><span data-stu-id="15b26-132">0  1-byte NULL termination character</span></span>

- <span data-ttu-id="15b26-133">**OCTET** 이진 전송을 지정하기 위한 ASCII "OCTET"</span><span class="sxs-lookup"><span data-stu-id="15b26-133">**OCTET** ASCII “OCTET” to specify binary transfer</span></span>

- <span data-ttu-id="15b26-134">0  1바이트 NULL 종료 문자</span><span class="sxs-lookup"><span data-stu-id="15b26-134">0  1-byte NULL termination character</span></span>

<span data-ttu-id="15b26-135">TFTP 쓰기, ACK 및 오류 메시지의 정의는 약간 다르며 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-135">The definition of the TFTP write, ACK, and error messages are slightly different and are defined as follows:</span></span>

<span data-ttu-id="15b26-136">**oooobbbbd…d**</span><span class="sxs-lookup"><span data-stu-id="15b26-136">**oooobbbbd…d**</span></span>

<span data-ttu-id="15b26-137">위치:</span><span class="sxs-lookup"><span data-stu-id="15b26-137">Where:</span></span>

- <span data-ttu-id="15b26-138">**oooo** 2바이트 Opcode 필드</span><span class="sxs-lookup"><span data-stu-id="15b26-138">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="15b26-139">0x0003 -> 데이터 패킷</span><span class="sxs-lookup"><span data-stu-id="15b26-139">0x0003 -> Data packet</span></span>  
<span data-ttu-id="15b26-140">0x0004 -> 마지막 읽기를 위한 ACK</span><span class="sxs-lookup"><span data-stu-id="15b26-140">0x0004 -> ACK for last read</span></span>  
<span data-ttu-id="15b26-141">0x0005 -> 오류 조건</span><span class="sxs-lookup"><span data-stu-id="15b26-141">0x0005 -> Error condition</span></span>  

- <span data-ttu-id="15b26-142">**bbbb** 2바이트 블록 번호 필드(1-n)</span><span class="sxs-lookup"><span data-stu-id="15b26-142">**bbbb** 2-byte Block Number field (1-n)</span></span>

- <span data-ttu-id="15b26-143">**d…d** n바이트 데이터 필드</span><span class="sxs-lookup"><span data-stu-id="15b26-143">**d…d** n-byte Data field</span></span>


- <span data-ttu-id="15b26-144">0x0001 (읽기) 파일 이름 0 OCTET 0</span><span class="sxs-lookup"><span data-stu-id="15b26-144">0x0001 (read) File Name 0 OCTET 0</span></span>

- <span data-ttu-id="15b26-145">0x0002 (쓰기) 파일 이름 0 OCTET 0</span><span class="sxs-lookup"><span data-stu-id="15b26-145">0x0002 (write) File Name 0 OCTET 0</span></span>

## <a name="tftp-communication"></a><span data-ttu-id="15b26-146">TFTP 통신</span><span class="sxs-lookup"><span data-stu-id="15b26-146">TFTP Communication</span></span>

<span data-ttu-id="15b26-147">TFTP 서버는 잘 알려진 UDP 포트 69를 활용하여 클라이언트 요청을 수신 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-147">TFTP Servers utilize the well-known UDP port 69 to listen for Client requests.</span></span> <span data-ttu-id="15b26-148">TFTP 클라이언트 소켓은 사용 가능한 모든 UDP 포트에 바인딩될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-148">TFTP Client sockets may bind to any available UDP port.</span></span> <span data-ttu-id="15b26-149">업로드하거나 다운로드할 파일이 포함된 데이터 패킷 페이로드는 512바이트 미만을 포함하는 마지막 패킷에 도달할 때까지 512바이트 청크로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-149">Data packet payload containing the file to upload or download is sent in 512 byte chunks, until the last packet containing < 512 bytes.</span></span> <span data-ttu-id="15b26-150">따라서 512바이트 미만의 패킷은 파일의 끝임을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-150">Therefore a packet containing fewer than 512 bytes signals the end of file.</span></span> <span data-ttu-id="15b26-151">이벤트의 일반 시퀀스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-151">The general sequence of events is as follows:</span></span>

<span data-ttu-id="15b26-152">TFTP 파일 읽기 요청:</span><span class="sxs-lookup"><span data-stu-id="15b26-152">TFTP Read File Requests:</span></span>

1.  <span data-ttu-id="15b26-153">클라이언트는 파일 이름을 포함하는 "읽기 위해 열기" 요청을 실행하고 서버의 응답을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-153">The Client issues an “Open For Read” request with the file name and waits for a reply from the Server.</span></span>

2.  <span data-ttu-id="15b26-154">서버는 파일의 처음 512바이트를 전송하며, 파일 크기가 512바이트보다 작으면 더 적은 바이트를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-154">The Server sends the first 512 bytes of the file or less if the file size is less than 512 bytes.</span></span>

3.  <span data-ttu-id="15b26-155">클라이언트는 데이터를 받고 ACK를 보내며, 512바이트를 초과하는 파일의 경우 서버의 다음 패킷을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-155">The Client receives data, sends an ACK, and waits for the next packet from the Server for files containing more than 512 bytes.</span></span>

4.  <span data-ttu-id="15b26-156">클라이언트에서 512바이트 미만의 패킷을 수신하면 시퀀스가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-156">The sequence ends when the Client receives a packet containing fewer than 512 bytes.</span></span>

<span data-ttu-id="15b26-157">TFTP 쓰기 요청:</span><span class="sxs-lookup"><span data-stu-id="15b26-157">TFTP Write Requests:</span></span>

1.  <span data-ttu-id="15b26-158">클라이언트는 파일 이름을 사용하여 "쓰기 위해 열기" 요청을 실행하고 서버에서 블록 번호가 0인 ACK를 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-158">The Client issues an “Open for Write” request with the file name and waits for an ACK with a block number of 0 from the Server.</span></span>

2.  <span data-ttu-id="15b26-159">서버는 파일을 쓸 준비가 되면 블록 번호가 0인 ACK를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-159">When the Server is ready to write the file, it sends an ACK with a block number of zero.</span></span>

3.  <span data-ttu-id="15b26-160">클라이언트는 파일의 처음 512바이트(또는 512바이트보다 작은 파일의 경우 더 적은 바이트)를 서버에 보내고 ACK를 다시 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-160">The Client sends the first 512 bytes of the file (or less for files less than 512 bytes) to the Server and waits for an ACK back.</span></span>

4.  <span data-ttu-id="15b26-161">서버는 해당 바이트를 쓴 후 ACK를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-161">The Server sends an ACK after the bytes are written.</span></span>

5.  <span data-ttu-id="15b26-162">클라이언트에서 512바이트 미만의 패킷 쓰기를 완료하면 시퀀스가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-162">The sequence ends when the Client completes writing a packet containing fewer than 512 bytes.</span></span>
 

## <a name="tftp-server-session-timer"></a><span data-ttu-id="15b26-163">TFTP 서버 세션 타이머</span><span class="sxs-lookup"><span data-stu-id="15b26-163">TFTP Server Session Timer</span></span>

<span data-ttu-id="15b26-164">TFTP 서버에는 제한된 수의 클라이언트 요청 슬롯이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-164">The TFTP Server has a limited number of client request slots.</span></span> <span data-ttu-id="15b26-165">클라이언트 세션이 삭제된 것으로 표시되면 해당 슬롯을 다시 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-165">If a client session appears to be dropped, that slot cannot be available for re-use.</span></span> <span data-ttu-id="15b26-166">그러나 NX_TFTP_SERVER_RETRANSMIT_ENABLE 옵션을 사용하도록 설정하는 경우 NetX Duo TFTP 서버는 각 클라이언트 세션에 대한 시간 제한을 모니터링하는 세션 타이머를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-166">However if the NX_TFTP_SERVER_RETRANSMIT_ENABLE option is enabled, the NetX Duo TFTP Server creates an session timer that monitors the timeout on each of its client sessions.</span></span> <span data-ttu-id="15b26-167">세션 제한 시간이 만료되면 종료되며 열려 있는 모든 파일이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-167">When a session timeout expires it is terminated and any open files are closed.</span></span> <span data-ttu-id="15b26-168">따라서 '슬롯'을 다른 TFTP 클라이언트 요청에 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-168">Thus the ‘slot’ becomes available for another TFTP Client request.</span></span>

<span data-ttu-id="15b26-169">제한 시간을 설정하려면 구성 옵션 NX_TFTP_SERVER_RETRANSMIT_TIMEOUT을 조정합니다. 이 옵션은 기본값이 200개 타이머 틱입니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-169">To set the timeout, adjust the configuration option NX_TFTP_SERVER_RETRANSMIT_TIMEOUT which by default is 200 timer ticks.</span></span> <span data-ttu-id="15b26-170">세션 제한 시간을 확인하는 간격은 NX_TFTP_SERVER_TIMEOUT_PERIOD로 설정되며 이 옵션은 기본값이 20개 타이머 틱입니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-170">The interval between which session timeouts are checked is set by the NX_TFTP_SERVER_TIMEOUT_PERIOD which is 20 timer ticks by default.</span></span>

<span data-ttu-id="15b26-171">TFTP 클라이언트가 TFTP FileX 미디어에 파일을 업로드(기록)하면 TFTP 서버 ram 디스크에서 기본 미디어(TFTP 클라이언트 디스크 메모리)로 데이터를 쓸 수 있도록 미디어를 플러시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-171">When the TFTP Client has uploaded (written) files to the TFTP FileX media, the media needs to be flushed so that data can be written from the TFTP server ram disk to the underlying media (TFTP Client disk memory).</span></span> <span data-ttu-id="15b26-172">애플리케이션에서 TFTP 서버를 닫지 않으려는 경우 fx_media_flush 서비스를 사용하여 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-172">This can be done using the fx_media_flush service if the application does not wish to close the TFTP Server.</span></span>

<span data-ttu-id="15b26-173">그러나 TFTP 서버를 닫은 후에 애플리케이션은 FileX 미디어를 추가로 사용하지 않는 경우 fx_media_close 서비스를 사용하여 미디어를 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-173">However, after closing the TFTP server, the application should, if it has no further use for the FileX media, then close the media using the fx_media_close service.</span></span> <span data-ttu-id="15b26-174">그러면 파일 데이터가 TFTP 클라이언트 디스크로 다시 플러시되고 열려 있는 파일이 닫히고, 디렉터리 정보가 미디어에 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-174">This will flush the file data back to the TFTP Client disk, close open files, and update the directory information to the media.</span></span>

<span data-ttu-id="15b26-175">이러한 내용은 이 장의 "소규모 예제" 섹션에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-175">The “Small Example” section in this chapter demonstrates this.</span></span>

<span data-ttu-id="15b26-176">FileX 미디어를 업데이트하는 세 번째 옵션은 Filex 서비스를 명시적으로 사용하는 대신 FX_FAULT_TOLERANT 또는 FX_FAULT_TOLERANT_DATA 옵션을 사용하여 FileX 라이브러리를 컴파일하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-176">A third option for updating the FileX media is to compile the FileX library with the FX_FAULT_TOLERANT or the FX_FAULT_TOLERANT_DATA options instead of using FileX services explicitly.</span></span> <span data-ttu-id="15b26-177">정의된 경우 FileX는 미디어 드라이버에 쓰기 요청을 자동으로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-177">If defined, FileX automatically passes write requests to the media driver.</span></span> <span data-ttu-id="15b26-178">이러한 옵션을 선택하면 성능이 제한될 수 있지만 손실된 파일 데이터 또는 손실된 클러스터를 통해 보호 효과가 더 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-178">These options may limit performance but offer greater protection from lost file data or lost clusters.</span></span> <span data-ttu-id="15b26-179">일반적으로 이 옵션 및 FileX에 대한 자세한 내용은 Express Logic FileX User Guide를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15b26-179">For more information about this and FileX in general, please see the Express Logic FileX User Guide.</span></span>

## <a name="tftp-multi-thread-support"></a><span data-ttu-id="15b26-180">TFTP 다중 스레드 지원</span><span class="sxs-lookup"><span data-stu-id="15b26-180">TFTP Multi-Thread Support</span></span>

<span data-ttu-id="15b26-181">NetX Duo TFTP 클라이언트 서비스는 다중 스레드에서 동시에 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-181">The NetX Duo TFTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="15b26-182">하지만 특정 TFTP 클라이언트 인스턴스에 대한 읽기 또는 쓰기 요청을 동일 스레드에서 순차적으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-182">However, read or write requests for a particular TFTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="tftp-rfcs"></a><span data-ttu-id="15b26-183">TFTP RFC</span><span class="sxs-lookup"><span data-stu-id="15b26-183">TFTP RFCs</span></span>

<span data-ttu-id="15b26-184">NetX Duo TFTP는 RFC1350 및 관련 RFC와 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="15b26-184">NetX Duo TFTP is compliant with RFC1350 and related RFCs.</span></span>

