---
title: 3장 - Azure RTOS NetX FTP 서비스 설명
description: 이 장에서는 아래에 나열된 모든 Azure RTOS NetX FTP 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b05d03c45607c45acf32474cf8e40861532c5fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811538"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a><span data-ttu-id="90498-103">3장 - Azure RTOS NetX FTP 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="90498-103">Chapter 3 - Description of Azure RTOS NetX FTP services</span></span>

<span data-ttu-id="90498-104">이 장에서는 아래에 나열된 모든 Azure RTOS NetX FTP 서비스에 대해 알파벳 순서로 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-104">This chapter contains a description of all Azure RTOS NetX FTP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="90498-105">다음 API 설명의 “반환 값” 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="90498-106">**nx_ftp_client_connect**: *FTP 서버에 연결*</span><span class="sxs-lookup"><span data-stu-id="90498-106">**nx_ftp_client_connect**: *Connect to FTP Server*</span></span>
- <span data-ttu-id="90498-107">**nx_ftp_client_create**: *FTP 클라이언트 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="90498-107">**nx_ftp_client_create**: *Create an FTP Client instance*</span></span>
- <span data-ttu-id="90498-108">**nx_ftp_client_delete**: *FTP 클라이언트 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="90498-108">**nx_ftp_client_delete**: *Delete an FTP Client instance*</span></span>
- <span data-ttu-id="90498-109">**nx_ftp_client_directory_create**: *서버에서 디렉터리 만들기*</span><span class="sxs-lookup"><span data-stu-id="90498-109">**nx_ftp_client_directory_create**: *Create a directory on Server*</span></span>
- <span data-ttu-id="90498-110">**nx_ftp_client_directory_default_set**: *서버에서 기본 디렉터리 설정*</span><span class="sxs-lookup"><span data-stu-id="90498-110">**nx_ftp_client_directory_default_set**: *Set default directory on Server*</span></span>
- <span data-ttu-id="90498-111">**nx_ftp_client_directory_delete**: *서버에서 디렉터리 삭제*</span><span class="sxs-lookup"><span data-stu-id="90498-111">**nx_ftp_client_directory_delete**: *Delete a directory on Server*</span></span>
- <span data-ttu-id="90498-112">**nx_ftp_client_directory_listing_get**: *서버에서 디렉터리 목록 가져오기*</span><span class="sxs-lookup"><span data-stu-id="90498-112">**nx_ftp_client_directory_listing_get**: *Get directory listing from Server*</span></span>
- <span data-ttu-id="90498-113">**nx_ftp_client_directory_listing_continue**: *서버에서 디렉터리 나열 계속*</span><span class="sxs-lookup"><span data-stu-id="90498-113">**nx_ftp_client_directory_listing_continue**: *Continue directory listing from Server*</span></span>
- <span data-ttu-id="90498-114">**nx_ftp_client_disconnect**: *FTP 서버에서 연결 해제*</span><span class="sxs-lookup"><span data-stu-id="90498-114">**nx_ftp_client_disconnect**: *Disconnect from FTP Server*</span></span>
- <span data-ttu-id="90498-115">**nx_ftp_client_file_close**: *클라이언트 파일 닫기*</span><span class="sxs-lookup"><span data-stu-id="90498-115">**nx_ftp_client_file_close**: *Close Client file*</span></span>
- <span data-ttu-id="90498-116">**nx_ftp_client_file_delete**: *서버에서 파일 삭제*</span><span class="sxs-lookup"><span data-stu-id="90498-116">**nx_ftp_client_file_delete**: *Delete file on Server*</span></span>
- <span data-ttu-id="90498-117">**nx_ftp_client_file_open**: *클라이언트 파일 열기*</span><span class="sxs-lookup"><span data-stu-id="90498-117">**nx_ftp_client_file_open**: *Open Client file*</span></span>
- <span data-ttu-id="90498-118">**nx_ftp_client_file_read**: *파일에서 읽기*</span><span class="sxs-lookup"><span data-stu-id="90498-118">**nx_ftp_client_file_read**: *Read from file*</span></span>
- <span data-ttu-id="90498-119">**nx_ftp_client_file_rename**: *서버에서 파일 이름 변경*</span><span class="sxs-lookup"><span data-stu-id="90498-119">**nx_ftp_client_file_rename**: *Rename file on Server*</span></span>
- <span data-ttu-id="90498-120">**nx_ftp_client_file_write**: *파일에서 읽기*</span><span class="sxs-lookup"><span data-stu-id="90498-120">**nx_ftp_client_file_write**: *Write to file*</span></span>
- <span data-ttu-id="90498-121">**nx_ftp_server_create**: *FTP 서버 만들기*</span><span class="sxs-lookup"><span data-stu-id="90498-121">**nx_ftp_server_create**: *Create FTP Server*</span></span>
- <span data-ttu-id="90498-122">**nx_ftp_server_delete**: *FTP 서버 삭제*</span><span class="sxs-lookup"><span data-stu-id="90498-122">**nx_ftp_server_delete**: *Delete FTP Server*</span></span>
- <span data-ttu-id="90498-123">**nx_ftp_server_start**: *FTP 서버 시작*</span><span class="sxs-lookup"><span data-stu-id="90498-123">**nx_ftp_server_start**: *Start FTP Server*</span></span>
- <span data-ttu-id="90498-124">**nx_ftp_server_stop**: *FTP 서버 중지*</span><span class="sxs-lookup"><span data-stu-id="90498-124">**nx_ftp_server_stop**: *Stop FTP Server*</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="90498-125">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="90498-125">nx_ftp_client_connect</span></span>

<span data-ttu-id="90498-126">FTP 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="90498-126">Connect to an FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-127">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-127">Prototype</span></span>

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-128">Description</span><span class="sxs-lookup"><span data-stu-id="90498-128">Description</span></span>

<span data-ttu-id="90498-129">이 서비스는 이전에 만든 FTP 클라이언트 인스턴스를 제공된 IP 주소에서 FTP 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-129">This service connects the previously created FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-130">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-130">Input Parameters</span></span>

- <span data-ttu-id="90498-131">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-131">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-132">**server_ip**: FTP 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-132">**server_ip**: IP address of FTP Server.</span></span>
- <span data-ttu-id="90498-133">**username**: 인증을 위한 클라이언트 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-133">**username**: Client username for authentication.</span></span>
- <span data-ttu-id="90498-134">**password**: 인증을 위한 클라이언트 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-134">**password**: Client password for authentication.</span></span>
- <span data-ttu-id="90498-135">**wait_option**: 서비스에서 FTP 클라이언트 연결을 대기하는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-135">**wait_option**: Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="90498-136">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-136">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-137">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-137">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-138">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-138">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-139">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-139">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-140">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-140">Return Values</span></span>

- <span data-ttu-id="90498-141">**NX_SUCCESS**: (0x00) FTP를 성공적으로 연결했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-141">**NX_SUCCESS**: (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="90498-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) 22X(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="90498-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) 23X(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="90498-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) 33X(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="90498-145">**NX_FTP_NOT_DISCONNECTED**: (0xD4) 클라이언트가 이미 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-145">**NX_FTP_NOT_DISCONNECTED**: (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="90498-146">NX_PTR_ERROR: (0x07) 잘못된 포인터 입력/출력입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-146">NX_PTR_ERROR: (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="90498-147">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-147">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="90498-148">NX_IP_ADDRESS_ERROR: (0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-148">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-149">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-149">Allowed From</span></span>

<span data-ttu-id="90498-150">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-150">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-151">예제</span><span class="sxs-lookup"><span data-stu-id="90498-151">Example</span></span>

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a><span data-ttu-id="90498-152">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="90498-152">nx_ftp_client_create</span></span>

<span data-ttu-id="90498-153">FTP 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="90498-153">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-154">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-154">Prototype</span></span>

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="90498-155">Description</span><span class="sxs-lookup"><span data-stu-id="90498-155">Description</span></span>

<span data-ttu-id="90498-156">이 서비스는 FTP 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="90498-156">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-157">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-157">Input Parameters</span></span>

- <span data-ttu-id="90498-158">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-158">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-159">**ftp_client_name**: FTP 클라이언트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-159">**ftp_client_name**: Name of FTP Client.</span></span>
- <span data-ttu-id="90498-160">**ip_ptr**: 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-160">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="90498-161">**window_size**: 이 FTP 클라이언트의 TCP 소켓에 대해 보급된 창 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-161">**window_size**: Advertised window size for TCP socket of this FTP Client.</span></span>
- <span data-ttu-id="90498-162">**pool_ptr**: 이 FTP 클라이언트의 기본 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-162">**pool_ptr**: Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="90498-163">최소 패킷 페이로드는 전체 경로 및 파일 또는 디렉터리 이름을 저장할 수 있을 만큼 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-163">Note that the minimum packet payload must be large enough to hold complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-164">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-164">Return Values</span></span>

- <span data-ttu-id="90498-165">**NX_SUCCESS**: (0x00) FTP 클라이언트를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-165">**NX_SUCCESS**: (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="90498-166">NX_PTR_ERROR: (0x16) 잘못된 FTP, IP 포인터 또는 패킷 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-166">NX_PTR_ERROR: (0x16) Invalid FTP, IP pointer, or packet pool pointer.</span></span> <span data-ttu-id="90498-167">암호 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-167">password pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-168">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-168">Allowed From</span></span>

<span data-ttu-id="90498-169">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="90498-169">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-170">예제</span><span class="sxs-lookup"><span data-stu-id="90498-170">Example</span></span>

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="90498-171">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="90498-171">nx_ftp_client_delete</span></span>

<span data-ttu-id="90498-172">FTP 클라이언트 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="90498-172">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-173">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-173">Prototype</span></span>

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="90498-174">Description</span><span class="sxs-lookup"><span data-stu-id="90498-174">Description</span></span>

<span data-ttu-id="90498-175">이 서비스는 FTP 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-175">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-176">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-176">Input Parameters</span></span>

- <span data-ttu-id="90498-177">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-177">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-178">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-178">Return Values</span></span>

- <span data-ttu-id="90498-179">**NX_SUCCESS**: (0x00) FTP 클라이언트를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-179">**NX_SUCCESS**: (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="90498-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) FTP 클라이언트 삭제 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) FTP Client delete error.</span></span>
- <span data-ttu-id="90498-181">NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-181">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-182">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-182">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-183">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-183">Allowed From</span></span>

<span data-ttu-id="90498-184">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-185">예제</span><span class="sxs-lookup"><span data-stu-id="90498-185">Example</span></span>

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="90498-186">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="90498-186">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="90498-187">FTP 서버에 디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="90498-187">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-188">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-188">Prototype</span></span>

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-189">Description</span><span class="sxs-lookup"><span data-stu-id="90498-189">Description</span></span>

<span data-ttu-id="90498-190">이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에 지정된 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="90498-190">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-191">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-191">Input Parameters</span></span>

- <span data-ttu-id="90498-192">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-192">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-193">**directory_name**: 만들 디렉터리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-193">**directory_name**: Name of directory to create.</span></span>
- <span data-ttu-id="90498-194">**wait_option**: 서비스에서 FTP 디렉터리 생성을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-194">**wait_option**: Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="90498-195">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-195">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-196">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-196">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-197">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-197">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-198">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-198">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-199">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-199">Return Values</span></span>

- <span data-ttu-id="90498-200">**NX_SUCCESS**: (0x00) FTP 디렉터리를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-200">**NX_SUCCESS**: (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="90498-201">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-201">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="90498-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="90498-203">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-203">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="90498-204">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-205">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-205">Allowed From</span></span>

<span data-ttu-id="90498-206">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-206">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-207">예제</span><span class="sxs-lookup"><span data-stu-id="90498-207">Example</span></span>

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="90498-208">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="90498-208">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="90498-209">FTP 서버에 기본 디렉터리 설정</span><span class="sxs-lookup"><span data-stu-id="90498-209">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-210">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-210">Prototype</span></span>

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-211">Description</span><span class="sxs-lookup"><span data-stu-id="90498-211">Description</span></span>

<span data-ttu-id="90498-212">이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에 지정된 디렉터리를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-212">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="90498-213">이 기본 디렉터리는 이 클라이언트의 연결에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-213">This default directory applies only to this client's connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-214">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-214">Input Parameters</span></span>

- <span data-ttu-id="90498-215">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-215">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-216">**directory_path**: 설정할 디렉터리 경로의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-216">**directory_path**: Name of directory path to set.</span></span>
- <span data-ttu-id="90498-217">**wait_option**: 서비스에서 FTP 기본 디렉터리 설정을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-217">**wait_option**: Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="90498-218">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-218">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-219">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-219">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-220">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-220">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-221">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-221">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-222">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-222">Return Values</span></span>

- <span data-ttu-id="90498-223">**NX_SUCCESS**: (0x00) FTP 기본 설정이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-223">**NX_SUCCESS**: (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="90498-224">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-224">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="90498-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="90498-226">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-226">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="90498-227">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-227">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-228">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-228">Allowed From</span></span>

<span data-ttu-id="90498-229">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-230">예제</span><span class="sxs-lookup"><span data-stu-id="90498-230">Example</span></span>

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="90498-231">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="90498-231">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="90498-232">FTP 서버에서 디렉터리 삭제</span><span class="sxs-lookup"><span data-stu-id="90498-232">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-233">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-233">Prototype</span></span>

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-234">Description</span><span class="sxs-lookup"><span data-stu-id="90498-234">Description</span></span>

<span data-ttu-id="90498-235">이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에서 지정된 디렉터리를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-235">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-236">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-236">Input Parameters</span></span>

- <span data-ttu-id="90498-237">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-237">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-238">**directory_name**: 삭제할 디렉터리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-238">**directory_name**: Name of directory to delete.</span></span>
- <span data-ttu-id="90498-239">**wait_option**: 서비스에서 FTP 디렉터리 삭제를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-239">**wait_option**: Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="90498-240">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-240">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-241">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-241">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-242">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-242">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-243">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-243">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-244">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-244">Return Values</span></span>

- <span data-ttu-id="90498-245">**NX_SUCCESS**: (0x00) FTP 디렉터리를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-245">**NX_SUCCESS**: (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="90498-246">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-246">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="90498-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="90498-248">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-248">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="90498-249">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-249">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-250">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-250">Allowed From</span></span>

<span data-ttu-id="90498-251">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-252">예제</span><span class="sxs-lookup"><span data-stu-id="90498-252">Example</span></span>

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="90498-253">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="90498-253">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="90498-254">FTP 서버에서 디렉터리 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="90498-254">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-255">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-255">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-256">Description</span><span class="sxs-lookup"><span data-stu-id="90498-256">Description</span></span>

<span data-ttu-id="90498-257">이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에서 지정된 디렉터리의 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="90498-257">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="90498-258">제공된 패킷 포인터는 하나 이상의 디렉터리 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-258">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="90498-259">각 항목은 &lt;cr/lf\ 조합으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-259">Each entry is separated by a &lt;cr/lf\combination.</span></span> <span data-ttu-id="90498-260">***nx_ftp_client_directory_listing_continue***: 디렉터리 가져오기 작업을 완료하기 위해 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-260">The ***nx_ftp_client_directory_listing_continue***: should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-261">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-261">Input Parameters</span></span>

- <span data-ttu-id="90498-262">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-262">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-263">**directory_name**: 콘텐츠를 가져올 디렉터리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-263">**directory_name**: Name of directory to get contents of.</span></span>
- <span data-ttu-id="90498-264">**packet_ptr**: 대상 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-264">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="90498-265">성공하는 경우 패킷 페이로드에 하나 이상의 디렉터리 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-265">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="90498-266">**wait_option**: 서비스에서 FTP 디렉터리 목록 나열을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-266">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="90498-267">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-267">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-268">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-268">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-269">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-269">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-270">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-270">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-271">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-271">Return Values</span></span>

- <span data-ttu-id="90498-272">**NX_SUCCESS**: (0x00) FTP 디렉터리를 성공적으로 나열했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-272">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="90498-273">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-273">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="90498-274">**NX_NOT_ENABLED**: (0x14) 서비스(IPv6)를 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="90498-274">**NX_NOT_ENABLED**: (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="90498-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) 1XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="90498-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="90498-277">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-277">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-278">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-278">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-279">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-279">Allowed From</span></span>

<span data-ttu-id="90498-280">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-281">예제</span><span class="sxs-lookup"><span data-stu-id="90498-281">Example</span></span>

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="90498-282">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="90498-282">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="90498-283">FTP 서버에서 디렉터리 나열 계속</span><span class="sxs-lookup"><span data-stu-id="90498-283">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-284">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-284">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-285">Description</span><span class="sxs-lookup"><span data-stu-id="90498-285">Description</span></span>

<span data-ttu-id="90498-286">이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에서 지정된 디렉터리의 콘텐츠를 계속 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="90498-286">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="90498-287">***nx_ftp_client_directory_listing_get*** 에 대한 호출 바로 앞에 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-287">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="90498-288">성공하는 경우 제공된 패킷 포인터는 하나 이상의 디렉터리 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-288">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="90498-289">이 루틴은 NX_FTP_END_OF_LISTING 상태가 수신될 때까지 호출되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-289">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-290">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-290">Input Parameters</span></span>

- <span data-ttu-id="90498-291">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-291">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-292">**packet_ptr**: 대상 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-292">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="90498-293">성공하는 경우 패킷 페이로드에 하나 이상의 디렉터리 항목이 &lt;cr/lf&gt;로 구분되어 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-293">If successful, the packet payload will contain one or more directory entries, separated by a &lt;cr/lf&gt;.</span></span>
- <span data-ttu-id="90498-294">**wait_option**: 서비스에서 FTP 디렉터리 목록 나열을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-294">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="90498-295">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-295">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-296">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-296">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-297">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-297">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-298">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-298">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-299">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-299">Return Values</span></span>

- <span data-ttu-id="90498-300">**NX_SUCCESS**: (0x00) FTP 디렉터리를 성공적으로 나열했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-300">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="90498-301">**NX_FTP_END_OF_LISTING**: (0xD8) 이 디렉터리에 항목이 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-301">**NX_FTP_END_OF_LISTING**: (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="90498-302">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-302">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="90498-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="90498-304">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-304">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-305">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-305">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-306">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-306">Allowed From</span></span>

<span data-ttu-id="90498-307">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-308">예제</span><span class="sxs-lookup"><span data-stu-id="90498-308">Example</span></span>

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="90498-309">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="90498-309">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="90498-310">FTP 서버에서 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="90498-310">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-311">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-311">Prototype</span></span>

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-312">Description</span><span class="sxs-lookup"><span data-stu-id="90498-312">Description</span></span>

<span data-ttu-id="90498-313">이 서비스는 지정된 FTP 클라이언트와 이전에 설정된 FTP 서버의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-313">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-314">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-314">Input Parameters</span></span>

- <span data-ttu-id="90498-315">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-315">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-316">**wait_option**: 서비스에서 FTP 클라이언트 연결 해제를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-316">**wait_option**: Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="90498-317">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-317">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-318">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-318">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-319">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-319">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-320">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-321">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-321">Return Values</span></span>

- <span data-ttu-id="90498-322">**NX_SUCCESS**: (0x00) FTP 연결을 성공적으로 해제했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-322">**NX_SUCCESS**: (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="90498-323">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-323">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="90498-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="90498-325">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-325">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-326">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-327">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-327">Allowed From</span></span>

<span data-ttu-id="90498-328">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-329">예제</span><span class="sxs-lookup"><span data-stu-id="90498-329">Example</span></span>

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="90498-330">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="90498-330">nx_ftp_client_file_close</span></span>

<span data-ttu-id="90498-331">클라이언트 파일 닫기</span><span class="sxs-lookup"><span data-stu-id="90498-331">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-332">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-332">Prototype</span></span>

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-333">Description</span><span class="sxs-lookup"><span data-stu-id="90498-333">Description</span></span>

<span data-ttu-id="90498-334">이 서비스는 FTP 서버에서 이전에 열린 파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-334">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-335">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-335">Input Parameters</span></span>

- <span data-ttu-id="90498-336">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-336">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-337">**wait_option**: 서비스에서 FTP 클라이언트 파일 닫기를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-337">**wait_option**: Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="90498-338">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-338">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-339">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-339">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-340">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-340">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-341">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-341">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-342">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-342">Return Values</span></span>

- <span data-ttu-id="90498-343">**NX_SUCCESS**: (0x00) FTP 파일을 성공적으로 닫았습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-343">**NX_SUCCESS**: (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="90498-344">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-344">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="90498-345">**NX_FTP_NOT_OPEN(0xD5)** : 파일이 열려 있지 않습니다. 닫을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-345">**NX_FTP_NOT_OPEN (0xD5)**: File not open; cannot close it</span></span>
- <span data-ttu-id="90498-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="90498-347">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-347">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-348">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-348">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-349">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-349">Allowed From</span></span>

<span data-ttu-id="90498-350">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-351">예제</span><span class="sxs-lookup"><span data-stu-id="90498-351">Example</span></span>

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="90498-352">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="90498-352">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="90498-353">FTP 서버에서 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="90498-353">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-354">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-354">Prototype</span></span>

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-355">Description</span><span class="sxs-lookup"><span data-stu-id="90498-355">Description</span></span>

<span data-ttu-id="90498-356">이 서비스는 FTP 서버에서 지정된 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-356">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-357">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-357">Input Parameters</span></span>

- <span data-ttu-id="90498-358">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-358">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-359">**file_name**: 삭제할 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-359">**file_name**: Name of file to delete.</span></span>
- <span data-ttu-id="90498-360">**wait_option**: 서비스에서 FTP 클라이언트 파일 닫기를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-360">**wait_option**: Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="90498-361">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-361">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-362">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-362">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-363">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-363">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-364">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-364">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-365">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-365">Return Values</span></span>

- <span data-ttu-id="90498-366">**NX_SUCCESS**: (0x00) FTP 파일을 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-366">**NX_SUCCESS**: (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="90498-367">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-367">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="90498-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="90498-369">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-369">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-370">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-371">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-371">Allowed From</span></span>

<span data-ttu-id="90498-372">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-373">예제</span><span class="sxs-lookup"><span data-stu-id="90498-373">Example</span></span>

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="90498-374">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="90498-374">nx_ftp_client_file_open</span></span>

<span data-ttu-id="90498-375">FTP 서버에서 파일 열기</span><span class="sxs-lookup"><span data-stu-id="90498-375">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-376">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-376">Prototype</span></span>

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-377">Description</span><span class="sxs-lookup"><span data-stu-id="90498-377">Description</span></span>

<span data-ttu-id="90498-378">이 서비스는 지정된 클라이언트 인스턴스에 이전에 연결된 FTP 서버에서 읽기 또는 쓰기를 위해 지정된 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="90498-378">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-379">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-379">Input Parameters</span></span>

- <span data-ttu-id="90498-380">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-380">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-381">**file_name**: 열 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-381">**file_name**: Name of file to open.</span></span>
- <span data-ttu-id="90498-382">**open_type**: **NX_FTP_OPEN_FOR_READ** 또는 **NX_FTP_OPEN_FOR_WRITE** 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-382">**open_type**: Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="90498-383">**wait_option**: 서비스에서 FTP 클라이언트 파일 열기를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-383">**wait_option**: Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="90498-384">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-384">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-385">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-385">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-386">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-386">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-387">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-387">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-388">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-388">Return Values</span></span>

- <span data-ttu-id="90498-389">**NX_SUCCESS**: (0x00) FTP 파일을 성공적으로 열었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-389">**NX_SUCCESS**: (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="90498-390">**NX_OPTION_ERROR**: (0x0A) 개방형 형식이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-390">**NX_OPTION_ERROR**: (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="90498-391">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-391">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="90498-392">**NX_FTP_NOT_CLOSED**: (0xD6) FTP 클라이언트가 이미 열려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-392">**NX_FTP_NOT_CLOSED**: (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="90498-393">**NX_NO_FREE_PORTS**: (0x45) 할당할 수 있는 TCP 포트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-393">**NX_NO_FREE_PORTS**: (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="90498-394">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-394">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-395">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-395">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-396">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-396">Allowed From</span></span>

<span data-ttu-id="90498-397">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-398">예제</span><span class="sxs-lookup"><span data-stu-id="90498-398">Example</span></span>

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="90498-399">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="90498-399">nx_ftp_client_file_read</span></span>

<span data-ttu-id="90498-400">파일에서 읽기</span><span class="sxs-lookup"><span data-stu-id="90498-400">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-401">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-401">Prototype</span></span>

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-402">Description</span><span class="sxs-lookup"><span data-stu-id="90498-402">Description</span></span>

<span data-ttu-id="90498-403">이 서비스는 이전에 열린 파일에서 패킷을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-403">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="90498-404">NX_FTP_END_OF_FILE 상태가 수신될 때까지 반복적으로 호출되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-404">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="90498-405">호출자는 이 서비스에 대한 패킷을 할당하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-405">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="90498-406">패킷 포인터에 대한 포인터만 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-406">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="90498-407">이 서비스는 소켓 수신 큐에서 검색된 패킷을 가리키도록 해당 패킷 포인터를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-407">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="90498-408">성공 상태가 반환되면 사용 가능한 패킷이 있음을 의미하며, 호출자는 작업을 수행할 때 패킷을 해제해야 하는 책임이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-408">If a successful status is returned, that means there was a packet available, and it is the caller's responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="90498-409">0이 아닌 상태(오류 상태 또는 NX_FTP_END_OF_FILE)가 반환되면 호출자는 패킷을 해제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-409">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="90498-410">그렇지 않으면 패킷 포인터가 NULL인 경우 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-410">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-411">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-411">Input Parameters</span></span>

- <span data-ttu-id="90498-412">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-412">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-413">**packet_ptr**: 큐에서 검색된 데이터 패킷 포인터의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-413">**packet_ptr**: Pointer to destination for the data packet pointer retrieved from the queue.</span></span> <span data-ttu-id="90498-414">성공하는 경우 패킷 데이터는 파일의 일부 또는 전부를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-414">If successful, the packet data contains some or all of the file.</span></span>
- <span data-ttu-id="90498-415">**wait_option**: 서비스에서 FTP 클라이언트 파일 읽기를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-415">**wait_option**: Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="90498-416">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-416">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-417">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-417">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-418">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-418">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-419">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-419">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-420">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-420">Return Values</span></span>

- <span data-ttu-id="90498-421">**NX_SUCCESS**: (0x00) FTP 파일을 성공적으로 읽었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-421">**NX_SUCCESS**: (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="90498-422">**NX_FTP_NOT_OPEN**: (0xD5) FTP 클라이언트가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-422">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="90498-423">**NX_FTP_END_OF_FILE**: (0xD7) 파일의 끝 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-423">**NX_FTP_END_OF_FILE**: (0xD7) End of file condition.</span></span>
- <span data-ttu-id="90498-424">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-424">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-425">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-425">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-426">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-426">Allowed From</span></span>

<span data-ttu-id="90498-427">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-428">예제</span><span class="sxs-lookup"><span data-stu-id="90498-428">Example</span></span>

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

        /* Check status.  */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }
        else
        {
            /* Release packet when done with it. */
            nx_packet_release(my_packet);
        }

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="90498-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="90498-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="90498-430">FTP 서버에서 파일 이름 변경</span><span class="sxs-lookup"><span data-stu-id="90498-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-431">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-431">Prototype</span></span>

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-432">Description</span><span class="sxs-lookup"><span data-stu-id="90498-432">Description</span></span>

<span data-ttu-id="90498-433">이 서비스는 FTP 서버에서 파일의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="90498-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-434">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-434">Input Parameters</span></span>

- <span data-ttu-id="90498-435">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-435">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-436">**filename**: 현재 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-436">**filename**: Current name of file.</span></span>
- <span data-ttu-id="90498-437">**new_filename**: 파일에 사용할 새 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-437">**new_filename**: New name for file.</span></span>
- <span data-ttu-id="90498-438">**wait_option**: 서비스에서 FTP 클라이언트 파일 이름 변경을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-438">**wait_option**: Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="90498-439">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-440">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-440">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-441">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-441">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-442">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-442">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-443">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-443">Return Values</span></span>

- <span data-ttu-id="90498-444">**NX_SUCCESS**: (0x00) FTP 파일 이름을 성공적으로 변경했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-444">**NX_SUCCESS**: (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="90498-445">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-445">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="90498-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) 3XX(ok) 응답을 받지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="90498-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="90498-448">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-448">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-449">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-449">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-450">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-450">Allowed From</span></span>

<span data-ttu-id="90498-451">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-452">예제</span><span class="sxs-lookup"><span data-stu-id="90498-452">Example</span></span>

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="90498-453">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="90498-453">nx_ftp_client_file_write</span></span>

<span data-ttu-id="90498-454">파일에 쓰기</span><span class="sxs-lookup"><span data-stu-id="90498-454">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-455">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-455">Prototype</span></span>

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="90498-456">Description</span><span class="sxs-lookup"><span data-stu-id="90498-456">Description</span></span>

<span data-ttu-id="90498-457">이 서비스는 FTP 서버에서 이전에 열린 파일에 데이터 패킷을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="90498-457">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-458">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-458">Input Parameters</span></span>

- <span data-ttu-id="90498-459">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-459">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-460">**packet_ptr**: 쓸 데이터를 포함하는 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-460">**packet_ptr**: Packet pointer containing data to write.</span></span>
- <span data-ttu-id="90498-461">**wait_option**: 서비스에서 FTP 클라이언트 파일 쓰기를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-461">**wait_option**: Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="90498-462">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90498-462">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="90498-463">**시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="90498-463">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="90498-464">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-464">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="90498-465">숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-465">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-466">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-466">Return Values</span></span>

- <span data-ttu-id="90498-467">**NX_SUCCESS**: (0x00) FTP 파일을 성공적으로 썼습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-467">**NX_SUCCESS**: (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="90498-468">**NX_FTP_NOT_OPEN**: (0xD5) FTP 클라이언트가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-468">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="90498-469">NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-469">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-470">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-470">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-471">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-471">Allowed From</span></span>

<span data-ttu-id="90498-472">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-473">예제</span><span class="sxs-lookup"><span data-stu-id="90498-473">Example</span></span>

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="90498-474">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="90498-474">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="90498-475">수동 전송 모드 사용 또는 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="90498-475">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-476">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-476">Prototype</span></span>

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="90498-477">Description</span><span class="sxs-lookup"><span data-stu-id="90498-477">Description</span></span>

<span data-ttu-id="90498-478">이 서비스를 이전에 만든 FTP 클라이언트 인스턴스에서 passive_mode_enabled 입력을 NX_TRUE로 설정하여, 이후 파일 읽기 또는 쓰기(RETR, STOR) 또는 디렉터리 목록 다운로드(NLST)에 대한 호출이 전송 모드에서 수행될 경우 수동 전송 모드를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-478">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="90498-479">수동 모드 전송을 사용하지 않도록 설정하고 활성 전송 모드의 기본 동작으로 돌아가려면 passive_mode_enabled 입력을 NX_FALSE로 설정하여 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-479">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-480">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-480">Input Parameters</span></span>

- <span data-ttu-id="90498-481">**ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-481">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="90498-482">**passive_mode_enabled**:</span><span class="sxs-lookup"><span data-stu-id="90498-482">**passive_mode_enabled**:</span></span>
  - <span data-ttu-id="90498-483">NX_TRUE로 설정된 경우 수동 모드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-483">If set to NX_TRUE, passive mode is enabled.</span></span>
  - <span data-ttu-id="90498-484">NX_FALSE로 설정된 경우 수동 모드를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-484">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-485">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-485">Return Values</span></span>

- <span data-ttu-id="90498-486">**NX_SUCCESS**: (0x00) 수동 모드를 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-486">**NX_SUCCESS**: (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="90498-487">NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-487">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-488">NX_INVALID_PARAMETERS: (0x4D) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-488">NX_INVALID_PARAMETERS: (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-489">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-489">Allowed From</span></span>

<span data-ttu-id="90498-490">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-491">예제</span><span class="sxs-lookup"><span data-stu-id="90498-491">Example</span></span>

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="90498-492">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="90498-492">nx_ftp_server_create</span></span>

<span data-ttu-id="90498-493">FTP 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="90498-493">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-494">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-494">Prototype</span></span>

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="90498-495">Description</span><span class="sxs-lookup"><span data-stu-id="90498-495">Description</span></span>

<span data-ttu-id="90498-496">이 서비스는 지정된 및 이전에 만든 NetX IP 인스턴스에 FTP 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="90498-496">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="90498-497">FTP 서버는 작업을 시작하기 위해 ***nx_ftp_server_start*** 를 호출하여 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-497">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-498">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-498">Input Parameters</span></span>

- <span data-ttu-id="90498-499">**ftp_server_ptr**: FTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-499">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="90498-500">**ftp_server_name**: FTP 서버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-500">**ftp_server_name**: Name of FTP Server.</span></span>
- <span data-ttu-id="90498-501">**ip_ptr**: 연결된 NetX IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-501">**ip_ptr**: Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="90498-502">IP 인스턴스에는 FTP 서버가 하나만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-502">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="90498-503">**media_ptr**: 연결된 FileX 미디어 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-503">**media_ptr**: Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="90498-504">**stack_ptr**: 내부 FTP 서버 스레드의 스택 영역에 대한 메모리 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-504">**stack_ptr**: Pointer to memory for the internal FTP Server thread's stack area.</span></span>
- <span data-ttu-id="90498-505">**stack_size**: *stack_ptr* 에 의해 지정된 스택 영역의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-505">**stack_size**: Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="90498-506">**pool_ptr**: 기본 NetX 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-506">**pool_ptr**: Pointer to default NetX packet pool.</span></span> <span data-ttu-id="90498-507">풀에 있는 패킷의 페이로드 크기는 최대 파일 이름/경로를 수용할 만큼 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-507">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="90498-508">**ftp_login**: 애플리케이션의 로그인 함수에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-508">**ftp_login**: Function pointer to application's login function.</span></span> <span data-ttu-id="90498-509">이 함수는 연결을 요청하는 클라이언트의 사용자 이름과 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-509">This function is supplied the username and password from the Client requesting a connection.</span></span> <span data-ttu-id="90498-510">유효한 경우 애플리케이션의 로그인 함수는 NX_SUCCESS를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-510">If this is valid, the application's login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="90498-511">**ftp_logout**: 애플리케이션의 로그아웃 함수에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-511">**ftp_logout**: Function pointer to application's logout function.</span></span> <span data-ttu-id="90498-512">이 함수는 연결 해제를 요청하는 클라이언트의 사용자 이름과 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-512">This function is supplied the username and password from the Client requesting a disconnection.</span></span> <span data-ttu-id="90498-513">유효한 경우 애플리케이션의 로그인 함수는 NX_SUCCESS를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-513">If this is valid, the application's login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-514">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-514">Return Values</span></span>

- <span data-ttu-id="90498-515">**NX_SUCCESS**: (0x00) FTP 서버를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-515">**NX_SUCCESS**: (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="90498-516">NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-516">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-517">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-517">Allowed From</span></span>

<span data-ttu-id="90498-518">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="90498-518">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-519">예제</span><span class="sxs-lookup"><span data-stu-id="90498-519">Example</span></span>

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="90498-520">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="90498-520">nx_ftp_server_delete</span></span>

<span data-ttu-id="90498-521">FTP 서버 삭제</span><span class="sxs-lookup"><span data-stu-id="90498-521">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-522">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-522">Prototype</span></span>

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="90498-523">Description</span><span class="sxs-lookup"><span data-stu-id="90498-523">Description</span></span>

<span data-ttu-id="90498-524">이 서비스는 이전에 만든 FTP 서버 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-524">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-525">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-525">Input Parameters</span></span>

- <span data-ttu-id="90498-526">**ftp_server_ptr**: FTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-526">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-527">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-527">Return Values</span></span>

- <span data-ttu-id="90498-528">**NX_SUCCESS**: (0x00) FTP 서버를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-528">**NX_SUCCESS**: (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="90498-529">NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-529">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-530">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-530">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-531">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-531">Allowed From</span></span>

<span data-ttu-id="90498-532">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-533">예제</span><span class="sxs-lookup"><span data-stu-id="90498-533">Example</span></span>

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="90498-534">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="90498-534">nx_ftp_server_start</span></span>

<span data-ttu-id="90498-535">FTP 서버 시작</span><span class="sxs-lookup"><span data-stu-id="90498-535">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-536">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-536">Prototype</span></span>

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="90498-537">Description</span><span class="sxs-lookup"><span data-stu-id="90498-537">Description</span></span>

<span data-ttu-id="90498-538">이 서비스는 이전에 만든 FTP 서버 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-538">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-539">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-539">Input Parameters</span></span>

- <span data-ttu-id="90498-540">**ftp_server_ptr**: FTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-540">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-541">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-541">Return Values</span></span>

- <span data-ttu-id="90498-542">**NX_SUCCESS**: (0x00) FTP 서버를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-542">**NX_SUCCESS**: (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="90498-543">NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-543">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-544">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-544">Allowed From</span></span>

<span data-ttu-id="90498-545">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="90498-545">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-546">예제</span><span class="sxs-lookup"><span data-stu-id="90498-546">Example</span></span>

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="90498-547">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="90498-547">nx_ftp_server_stop</span></span>

<span data-ttu-id="90498-548">FTP 서버 중지</span><span class="sxs-lookup"><span data-stu-id="90498-548">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="90498-549">프로토타입</span><span class="sxs-lookup"><span data-stu-id="90498-549">Prototype</span></span>

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="90498-550">Description</span><span class="sxs-lookup"><span data-stu-id="90498-550">Description</span></span>

<span data-ttu-id="90498-551">이 서비스는 이전에 만들어서 시작한 FTP 서버 인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="90498-551">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="90498-552">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="90498-552">Input Parameters</span></span>

- <span data-ttu-id="90498-553">**ftp_server_ptr**: FTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-553">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="90498-554">반환 값</span><span class="sxs-lookup"><span data-stu-id="90498-554">Return Values</span></span>

- <span data-ttu-id="90498-555">**NX_SUCCESS**: (0x00) FTP 서버를 성공적으로 중지했습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-555">**NX_SUCCESS**: (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="90498-556">NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="90498-556">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="90498-557">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90498-557">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="90498-558">허용되는 원본</span><span class="sxs-lookup"><span data-stu-id="90498-558">Allowed From</span></span>

<span data-ttu-id="90498-559">스레드</span><span class="sxs-lookup"><span data-stu-id="90498-559">Threads</span></span>

### <a name="example"></a><span data-ttu-id="90498-560">예제</span><span class="sxs-lookup"><span data-stu-id="90498-560">Example</span></span>

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
