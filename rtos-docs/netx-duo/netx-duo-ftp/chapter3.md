---
title: 챕터 3 - FTP 서비스 설명
description: 이 챕터에는 모든 NetX FTP 서비스(아래 참조)에 대한 설명이 알파벳 순서로 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d721d8bd3e08d8cccdc13011807b4c5017c84173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810795"
---
# <a name="chapter-3---description-of-ftp-services"></a><span data-ttu-id="50933-103">챕터 3 - FTP 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="50933-103">Chapter 3 - Description of FTP services</span></span>

<span data-ttu-id="50933-104">이 챕터에는 모든 NetX FTP 서비스(아래 참조)에 대한 설명이 알파벳 순서로 포함되어 있습니다. 단, 동일한 서비스의 IPv4 및 IPv6 항목은 쌍으로 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-104">This chapter contains a description of all NetX FTP services (listed below) in alphabetic order (except where IPv4 and IPv6 equivalents of the same service are paired together).</span></span>

> [!NOTE]
> <span data-ttu-id="50933-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="50933-106">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="50933-106">nx_ftp_client_connect</span></span>

<span data-ttu-id="50933-107">IPv4를 통해 FTP 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="50933-107">Connect to an FTP Server over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-108">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-108">Prototype</span></span>

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-109">Description</span><span class="sxs-lookup"><span data-stu-id="50933-109">Description</span></span>

<span data-ttu-id="50933-110">이 서비스는 이전에 만든 NetX FTP 클라이언트 인스턴스를 제공된 IP 주소의 FTP 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-110">This service connects the previously created NetX FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-111">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-111">Input Parameters</span></span>

- <span data-ttu-id="50933-112">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-112">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-113">**server_ip** FTP 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-113">**server_ip** IP address of FTP Server.</span></span>
- <span data-ttu-id="50933-114">**username** 인증을 위한 클라이언트 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-114">**username** Client username for authentication.</span></span>
- <span data-ttu-id="50933-115">**password** 인증을 위한 클라이언트 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-115">**password** Client password for authentication.</span></span>
- <span data-ttu-id="50933-116">**wait_option** 서비스에서 FTP 클라이언트 연결을 대기하는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-116">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="50933-117">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-117">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-118">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-118">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-119">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-119">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-120">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-120">Return Values</span></span>

- <span data-ttu-id="50933-121">**NX_SUCCESS** (0x00) FTP를 성공적으로 연결했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-121">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="50933-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) 22X(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="50933-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) 23X(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="50933-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) 33X(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="50933-125">**NX_FTP_NOT_DISCONNECTED** (0xD4) 클라이언트가 이미 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-125">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="50933-126">NX_PTR_ERROR (0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-126">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="50933-127">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-127">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="50933-128">NX_IP_ADDRESS_ERROR (0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-128">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-129">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-129">Allowed From</span></span>

<span data-ttu-id="50933-130">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-130">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-131">예제</span><span class="sxs-lookup"><span data-stu-id="50933-131">Example</span></span>

```C
/* Connect the FTP Client instance “my_client” to the FTP Server at

IP address 1.2.3.4. */

status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="50933-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50933-132">See Also</span></span>

<span data-ttu-id="50933-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="50933-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span></span>

## <a name="nxd_ftp_client_connect"></a><span data-ttu-id="50933-134">nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="50933-134">nxd_ftp_client_connect</span></span>

<span data-ttu-id="50933-135">IPv6를 지원하는 FTP 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="50933-135">Connect to an FTP Server with IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-136">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-136">Prototype</span></span>

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-137">Description</span><span class="sxs-lookup"><span data-stu-id="50933-137">Description</span></span>

<span data-ttu-id="50933-138">이 서비스는 이전에 만든 NetX Duo FTP 클라이언트 인스턴스를 제공된 IP 주소의 FTP 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-138">This service connects the previously created NetX Duo FTP Client instance to the FTP Server at the supplied IP address.</span></span> <span data-ttu-id="50933-139">IPv4 및 IPv6 네트워크가 모두 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-139">Both IPv4 and IPv6 networks are supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-140">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-140">Input Parameters</span></span>

- <span data-ttu-id="50933-141">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-141">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-142">**server_ipduo** FTP 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-142">**server_ipduo** IP address of the FTP Server.</span></span>
- <span data-ttu-id="50933-143">**username** 인증을 위한 클라이언트 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-143">**username** Client username for authentication.</span></span>
- <span data-ttu-id="50933-144">**password** 인증을 위한 클라이언트 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-144">**password** Client password for authentication.</span></span>
- <span data-ttu-id="50933-145">**wait_option** 서비스에서 FTP 클라이언트 연결을 대기하는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-145">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="50933-146">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-146">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-147">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-147">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-148">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-148">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-149">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-149">Return Values</span></span>

- <span data-ttu-id="50933-150">**NX_SUCCESS** (0x00) FTP를 성공적으로 연결했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-150">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="50933-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) 22X(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="50933-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) 23X(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="50933-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) 33X(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="50933-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) 클라이언트가 이미 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected</span></span>
- <span data-ttu-id="50933-155">NX_PTR_ERROR (0x07) 잘못된 포인터 입력/출력입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-155">NX_PTR_ERROR (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="50933-156">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-156">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="50933-157">NX_IP_ADDRESS_ERROR (0x21) 잘못된 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-157">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-158">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-158">Allowed From</span></span>

<span data-ttu-id="50933-159">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-159">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-160">예제</span><span class="sxs-lookup"><span data-stu-id="50933-160">Example</span></span>

```C
/* Connect an FTP Client instance to the FTP Server. */

/* Set up an IPv6 address for the server here.
    Note this could also be an IPv4 address as well*/

server_ip_addr.nxd_ip_address.v6[3] = 0x106;
server_ip_addr.nxd_ip_address.v6[2] = 0x0;
server_ip_addr.nxd_ip_address.v6[1] = 0x0000f101;
server_ip_addr.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V6;

status = nxd_ftp_client_connect(&my_client, server_ip_addr, NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="50933-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50933-161">See Also</span></span>

<span data-ttu-id="50933-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="50933-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span></span>

## <a name="nx_ftp_client_create"></a><span data-ttu-id="50933-163">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="50933-163">nx_ftp_client_create</span></span>

<span data-ttu-id="50933-164">FTP 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="50933-164">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-165">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-165">Prototype</span></span>

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="50933-166">Description</span><span class="sxs-lookup"><span data-stu-id="50933-166">Description</span></span>

<span data-ttu-id="50933-167">이 서비스는 FTP 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50933-167">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-168">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-168">Input Parameters</span></span>

- <span data-ttu-id="50933-169">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-169">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-170">**ftp_client_name** FTP 클라이언트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-170">**ftp_client_name** Name of FTP Client.</span></span>
- <span data-ttu-id="50933-171">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-171">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="50933-172">**window_size** 이 FTP 클라이언트의 TCP 소켓에 대해 보급된 창 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-172">**window_size** Advertised window size for TCP sockets of this FTP Client.</span></span>
- <span data-ttu-id="50933-173">**pool_ptr** 이 FTP 클라이언트의 기본 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-173">**pool_ptr** Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="50933-174">최소 패킷 페이로드는 전체 경로 및 파일 또는 디렉터리 이름을 저장할 수 있을 만큼 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-174">Note that the minimum packet payload must be large enough to hold  complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-175">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-175">Return Values</span></span>

- <span data-ttu-id="50933-176">**NX_SUCCESS** (0x00) FTP 클라이언트를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-176">**NX_SUCCESS** (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="50933-177">NX_PTR_ERROR (0x07) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-177">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-178">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-178">Allowed From</span></span>

<span data-ttu-id="50933-179">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="50933-179">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-180">예제</span><span class="sxs-lookup"><span data-stu-id="50933-180">Example</span></span>

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="50933-181">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="50933-181">nx_ftp_client_delete</span></span>

<span data-ttu-id="50933-182">FTP 클라이언트 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="50933-182">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-183">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-183">Prototype</span></span>

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="50933-184">Description</span><span class="sxs-lookup"><span data-stu-id="50933-184">Description</span></span>

<span data-ttu-id="50933-185">이 서비스는 FTP 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-185">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-186">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-186">Input Parameters</span></span>

- <span data-ttu-id="50933-187">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-187">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-188">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-188">Return Values</span></span>

- <span data-ttu-id="50933-189">**NX_SUCCESS** (0x00) FTP 클라이언트를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-189">**NX_SUCCESS** (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="50933-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) FTP 클라이언트의 연결이 해제되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) FTP client not disconnected</span></span>
- <span data-ttu-id="50933-191">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-191">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-192">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-192">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-193">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-193">Allowed From</span></span>

<span data-ttu-id="50933-194">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-194">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-195">예제</span><span class="sxs-lookup"><span data-stu-id="50933-195">Example</span></span>

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="50933-196">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="50933-196">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="50933-197">FTP 서버에 디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="50933-197">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-198">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-198">Prototype</span></span>

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-199">Description</span><span class="sxs-lookup"><span data-stu-id="50933-199">Description</span></span>

<span data-ttu-id="50933-200">이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에 지정된 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50933-200">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-201">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-201">Input Parameters</span></span>

- <span data-ttu-id="50933-202">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-202">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-203">**directory_name** 만들 디렉터리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-203">**directory_name** Name of directory to create.</span></span>
- <span data-ttu-id="50933-204">**wait_option** 서비스에서 FTP 디렉터리 생성을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-204">**wait_option** Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="50933-205">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-205">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-206">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-206">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-207">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-207">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-208">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-208">Return Values</span></span>

- <span data-ttu-id="50933-209">**NX_SUCCESS** (0x00) FTP 디렉터리를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-209">**NX_SUCCESS** (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="50933-210">**NX_FTP_NOT_CONNECTED** (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-210">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="50933-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="50933-212">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-212">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-213">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-213">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-214">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-214">Allowed From</span></span>

<span data-ttu-id="50933-215">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-216">예제</span><span class="sxs-lookup"><span data-stu-id="50933-216">Example</span></span>

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="50933-217">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="50933-217">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="50933-218">FTP 서버에 기본 디렉터리 설정</span><span class="sxs-lookup"><span data-stu-id="50933-218">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-219">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-219">Prototype</span></span>

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-220">Description</span><span class="sxs-lookup"><span data-stu-id="50933-220">Description</span></span>

<span data-ttu-id="50933-221">이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에 지정된 디렉터리를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-221">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="50933-222">이 기본 디렉터리는 이 클라이언트의 연결에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-222">This default directory applies only to this client’s connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-223">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-223">Input Parameters</span></span>

- <span data-ttu-id="50933-224">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-224">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-225">**directory_path** 설정할 디렉터리 경로의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-225">**directory_path** Name of directory path to set.</span></span>
- <span data-ttu-id="50933-226">**wait_option** 서비스에서 FTP 기본 디렉터리 설정을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-226">**wait_option** Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="50933-227">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-227">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-228">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-228">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-229">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-229">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-230">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-230">Return Values</span></span>

- <span data-ttu-id="50933-231">**NX_SUCCESS** (0x00) FTP 기본 설정이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-231">**NX_SUCCESS** (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="50933-232">**NX_FTP_NOT_CONNECTED** (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-232">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="50933-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="50933-234">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-234">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-235">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-235">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-236">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-236">Allowed From</span></span>

<span data-ttu-id="50933-237">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-238">예제</span><span class="sxs-lookup"><span data-stu-id="50933-238">Example</span></span>

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="50933-239">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="50933-239">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="50933-240">FTP 서버에서 디렉터리 삭제</span><span class="sxs-lookup"><span data-stu-id="50933-240">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-241">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-241">Prototype</span></span>

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-242">Description</span><span class="sxs-lookup"><span data-stu-id="50933-242">Description</span></span>

<span data-ttu-id="50933-243">이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에서 지정된 디렉터리를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-243">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-244">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-244">Input Parameters</span></span>

- <span data-ttu-id="50933-245">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-245">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-246">**directory_name** 삭제할 디렉터리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-246">**directory_name** Name of directory to delete.</span></span>
- <span data-ttu-id="50933-247">**wait_option** 서비스에서 FTP 디렉터리 삭제를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-247">**wait_option** Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="50933-248">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-248">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-249">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-249">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-250">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-250">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-251">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-251">Return Values</span></span>

- <span data-ttu-id="50933-252">**NX_SUCCESS** (0x00) FTP 디렉터리를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-252">**NX_SUCCESS** (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="50933-253">**NX_FTP_NOT_CONNECTED** (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-253">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="50933-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="50933-255">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-255">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-256">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-256">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-257">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-257">Allowed From</span></span>

<span data-ttu-id="50933-258">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-258">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-259">예제</span><span class="sxs-lookup"><span data-stu-id="50933-259">Example</span></span>

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="50933-260">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="50933-260">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="50933-261">FTP 서버에서 디렉터리 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="50933-261">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-262">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-262">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-263">Description</span><span class="sxs-lookup"><span data-stu-id="50933-263">Description</span></span>

<span data-ttu-id="50933-264">이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에서 지정된 디렉터리의 콘텐츠를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="50933-264">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="50933-265">제공된 패킷 포인터는 하나 이상의 디렉터리 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-265">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="50933-266">각 항목은 \<cr/lf\> 조합으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-266">Each entry is separated by a \<cr/lf\> combination.</span></span> <span data-ttu-id="50933-267">디렉터리 가져오기 작업을 완료하려면 ***nx_ftp_client_directory_listing_continue*** 를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-267">The ***nx_ftp_client_directory_listing_continue*** should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-268">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-268">Input Parameters</span></span>

- <span data-ttu-id="50933-269">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-269">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-270">**directory_name** 콘텐츠를 가져올 디렉터리의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-270">**directory_name** Name of directory to get contents of.</span></span>
- <span data-ttu-id="50933-271">**packet_ptr** 대상 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-271">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="50933-272">성공하는 경우 패킷 페이로드에 하나 이상의 디렉터리 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-272">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="50933-273">**wait_option** 서비스에서 FTP 디렉터리 목록 나열을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-273">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="50933-274">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-274">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-275">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-275">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-276">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-276">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-277">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-277">Return Values</span></span>

- <span data-ttu-id="50933-278">**NX_SUCCESS** (0x00) FTP 디렉터리를 성공적으로 나열했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-278">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="50933-279">**NX_FTP_NOT_CONNECTED** (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-279">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="50933-280">**NX_NOT_ENABLED** (0x14) 서비스(IPv6)를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-280">**NX_NOT_ENABLED** (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="50933-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) 1XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="50933-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="50933-283">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-283">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-284">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-284">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-285">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-285">Allowed From</span></span>

<span data-ttu-id="50933-286">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-287">예제</span><span class="sxs-lookup"><span data-stu-id="50933-287">Example</span></span>

```C
/* Get the contents of directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_get(&my_client, “my_dir”, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="50933-288">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="50933-288">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="50933-289">FTP 서버에서 디렉터리 나열 계속</span><span class="sxs-lookup"><span data-stu-id="50933-289">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-290">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-290">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-291">Description</span><span class="sxs-lookup"><span data-stu-id="50933-291">Description</span></span>

<span data-ttu-id="50933-292">이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에서 지정된 디렉터리의 콘텐츠를 계속 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="50933-292">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="50933-293">***nx_ftp_client_directory_listing_get*** 에 대한 호출 바로 앞에 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-293">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="50933-294">성공하는 경우 제공된 패킷 포인터가 하나 이상의 디렉터리 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-294">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="50933-295">이 루틴은 NX_FTP_END_OF_LISTING 상태가 수신될 때까지 호출되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-295">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-296">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-296">Input Parameters</span></span>

- <span data-ttu-id="50933-297">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-297">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-298">**packet_ptr** 대상 패킷 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-298">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="50933-299">성공하는 경우 패킷 페이로드에 하나 이상의 디렉터리 항목이 <cr/lf>로 구분되어 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-299">If successful, the packet payload will contain one or more directory entries, separated by a <cr/lf>.</span></span>
- <span data-ttu-id="50933-300">**wait_option** 서비스에서 FTP 디렉터리 목록 나열을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-300">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="50933-301">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-301">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-302">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-302">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-303">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-303">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-304">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-304">Return Values</span></span>

- <span data-ttu-id="50933-305">**NX_SUCCESS** (0x00) FTP 디렉터리를 성공적으로 나열했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-305">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="50933-306">**NX_FTP_END_OF_LISTING** (0xD8) 이 디렉터리에 항목이 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-306">**NX_FTP_END_OF_LISTING** (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="50933-307">**NX_FTP_NOT_CONNECTED** (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-307">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="50933-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="50933-309">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-309">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-310">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-310">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-311">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-311">Allowed From</span></span>

<span data-ttu-id="50933-312">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-313">예제</span><span class="sxs-lookup"><span data-stu-id="50933-313">Example</span></span>

```C
/* Continue getting the contents of directory “my_dir” on the FTP Server
    connected to the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="50933-314">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="50933-314">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="50933-315">FTP 서버에서 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="50933-315">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-316">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-316">Prototype</span></span>

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-317">Description</span><span class="sxs-lookup"><span data-stu-id="50933-317">Description</span></span>

<span data-ttu-id="50933-318">이 서비스는 지정된 FTP 클라이언트와 이전에 설정된 FTP 서버의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-318">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-319">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-319">Input Parameters</span></span>

- <span data-ttu-id="50933-320">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-320">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-321">**wait_option** 서비스에서 FTP 클라이언트 연결 해제를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-321">**wait_option** Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="50933-322">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-322">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-323">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-323">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-324">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-324">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-325">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-325">Return Values</span></span>

- <span data-ttu-id="50933-326">**NX_SUCCESS** (0x00) FTP 연결을 성공적으로 해제했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-326">**NX_SUCCESS** (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="50933-327">**NX_FTP_NOT_CONNECTED** (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-327">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="50933-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="50933-329">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-329">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-330">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-330">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-331">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-331">Allowed From</span></span>

<span data-ttu-id="50933-332">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-332">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-333">예제</span><span class="sxs-lookup"><span data-stu-id="50933-333">Example</span></span>

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="50933-334">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="50933-334">nx_ftp_client_file_close</span></span>

<span data-ttu-id="50933-335">클라이언트 파일 닫기</span><span class="sxs-lookup"><span data-stu-id="50933-335">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-336">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-336">Prototype</span></span>

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-337">Description</span><span class="sxs-lookup"><span data-stu-id="50933-337">Description</span></span>

<span data-ttu-id="50933-338">이 서비스는 FTP 서버에서 이전에 열린 파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-338">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-339">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-339">Input Parameters</span></span>

- <span data-ttu-id="50933-340">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-340">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-341">**wait_option** 서비스에서 FTP 클라이언트 파일 닫기를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-341">**wait_option** Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="50933-342">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-342">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-343">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-343">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-344">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-344">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-345">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-345">Return Values</span></span>

- <span data-ttu-id="50933-346">**NX_SUCCESS** (0x00) FTP 파일을 성공적으로 닫았습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-346">**NX_SUCCESS** (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="50933-347">**NX_FTP_NOT_CONNECTED** (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-347">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="50933-348">**NX_FTP_NOT_OPEN (0xD5)** 파일이 열려 있지 않습니다. 닫을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-348">**NX_FTP_NOT_OPEN (0xD5)** File not open; cannot close it</span></span>
- <span data-ttu-id="50933-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="50933-350">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-350">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-351">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-351">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-352">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-352">Allowed From</span></span>

<span data-ttu-id="50933-353">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-354">예제</span><span class="sxs-lookup"><span data-stu-id="50933-354">Example</span></span>

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="50933-355">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="50933-355">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="50933-356">FTP 서버에서 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="50933-356">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-357">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-357">Prototype</span></span>

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-358">Description</span><span class="sxs-lookup"><span data-stu-id="50933-358">Description</span></span>

<span data-ttu-id="50933-359">이 서비스는 FTP 서버에서 지정된 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-359">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-360">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-360">Input Parameters</span></span>

- <span data-ttu-id="50933-361">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-361">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-362">**file_name** 삭제할 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-362">**file_name** Name of file to delete.</span></span>
- <span data-ttu-id="50933-363">**wait_option** 서비스에서 FTP 클라이언트 파일 삭제를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-363">**wait_option** Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="50933-364">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-364">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-365">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-365">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-366">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-366">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-367">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-367">Return Values</span></span>

- <span data-ttu-id="50933-368">**NX_SUCCESS** (0x00) FTP 파일을 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-368">**NX_SUCCESS** (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="50933-369">**NX_FTP_NOT_CONNECTED** (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-369">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="50933-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="50933-371">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-371">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-372">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-372">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-373">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-373">Allowed From</span></span>

<span data-ttu-id="50933-374">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-374">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-375">예제</span><span class="sxs-lookup"><span data-stu-id="50933-375">Example</span></span>

```C
/* Delete the file “my_file.txt” on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_delete(&my_client, “my_file.txt”, 200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="50933-376">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="50933-376">nx_ftp_client_file_open</span></span>

<span data-ttu-id="50933-377">FTP 서버에서 파일 열기</span><span class="sxs-lookup"><span data-stu-id="50933-377">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-378">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-378">Prototype</span></span>

```C
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-379">Description</span><span class="sxs-lookup"><span data-stu-id="50933-379">Description</span></span>

<span data-ttu-id="50933-380">이 서비스는 지정된 클라이언트 인스턴스에 이전에 연결된 FTP 서버에서 읽기 또는 쓰기 대상으로 지정된 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="50933-380">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-381">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-381">Input Parameters</span></span>

- <span data-ttu-id="50933-382">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-382">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-383">**file_name** 열 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-383">**file_name** Name of file to open.</span></span>
- <span data-ttu-id="50933-384">**open_type** **NX_FTP_OPEN_FOR_READ** 또는 **NX_FTP_OPEN_FOR_WRITE** 입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-384">**open_type** Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="50933-385">**wait_option** 서비스에서 FTP 클라이언트 파일 열기를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-385">**wait_option** Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="50933-386">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-386">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-387">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-387">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-388">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-388">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-389">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-389">Return Values</span></span>

- <span data-ttu-id="50933-390">**NX_SUCCESS** (0x00) FTP 파일을 성공적으로 열었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-390">**NX_SUCCESS** (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="50933-391">**NX_OPTION_ERROR** (0x0A) 잘못된 개방형 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-391">**NX_OPTION_ERROR** (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="50933-392">**NX_FTP_NOT_CONNECTED** (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-392">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="50933-393">**NX_FTP_NOT_CLOSED** (0xD6) FTP 클라이언트가 이미 열려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-393">**NX_FTP_NOT_CLOSED** (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="50933-394">**NX_NO_FREE_PORTS** (0x45) 할당할 수 있는 TCP 포트가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-394">**NX_NO_FREE_PORTS** (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="50933-395">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-395">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-396">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-396">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-397">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-397">Allowed From</span></span>

<span data-ttu-id="50933-398">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-399">예제</span><span class="sxs-lookup"><span data-stu-id="50933-399">Example</span></span>

```C
/* Open the file “my_file.txt” for reading on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_open(&my_client, “my_file.txt”, NX_FTP_OPEN_FOR_READ,
    200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="50933-400">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="50933-400">nx_ftp_client_file_read</span></span>

<span data-ttu-id="50933-401">파일에서 읽기</span><span class="sxs-lookup"><span data-stu-id="50933-401">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-402">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-402">Prototype</span></span>

```C
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-403">Description</span><span class="sxs-lookup"><span data-stu-id="50933-403">Description</span></span>

<span data-ttu-id="50933-404">이 서비스는 이전에 열린 파일에서 패킷을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-404">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="50933-405">NX_FTP_END_OF_FILE 상태가 수신될 때까지 반복적으로 호출되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-405">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="50933-406">호출자는 이 서비스에 대한 패킷을 할당하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-406">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="50933-407">패킷 포인터에 대한 포인터만 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-407">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="50933-408">이 서비스는 소켓 수신 큐에서 검색된 패킷을 가리키도록 해당 패킷 포인터를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-408">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="50933-409">성공 상태가 반환되면 사용 가능한 패킷이 있음을 의미하며, 호출자는 작업을 수행할 때 패킷을 해제해야 하는 책임이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-409">If a successful status is returned, that means there was a packet available, and it is the caller’s responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="50933-410">0이 아닌 상태(오류 상태 또는 NX_FTP_END_OF_FILE)가 반환되면 호출자는 패킷을 해제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-410">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="50933-411">그렇지 않으면 패킷 포인터가 NULL인 경우 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-411">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-412">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-412">Input Parameters</span></span>

- <span data-ttu-id="50933-413">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-413">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-414">**packet_ptr** 저장할 데이터 패킷 포인터의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-414">**packet_ptr** Pointer to destination for the data packet pointer to be stored.</span></span> <span data-ttu-id="50933-415">성공하는 경우 패킷은 파일의 일부 또는 전부를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-415">If successful, the packet some or all the contains of the file.</span></span>
- <span data-ttu-id="50933-416">**wait_option** 서비스에서 FTP 클라이언트 파일 읽기를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-416">**wait_option** Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="50933-417">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-417">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-418">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-418">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-419">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-419">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-420">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-420">Return Values</span></span>

- <span data-ttu-id="50933-421">**NX_SUCCESS** (0x00) FTP 파일을 성공적으로 읽었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-421">**NX_SUCCESS** (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="50933-422">**NX_FTP_NOT_OPEN** (0xD5) FTP 클라이언트가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-422">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="50933-423">**NX_FTP_END_OF_FILE** (0xD7) 파일의 끝 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-423">**NX_FTP_END_OF_FILE** (0xD7) End of file condition.</span></span>
- <span data-ttu-id="50933-424">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-424">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-425">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-425">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-426">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-426">Allowed From</span></span>

<span data-ttu-id="50933-427">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-428">예제</span><span class="sxs-lookup"><span data-stu-id="50933-428">Example</span></span>

```C
NX_PACKET   *my_packet;

/* Read a packet of data from the file “my_file.txt” that was previously opened
    from the client “my_client.” */

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

/* If status is NX_SUCCESS, the packet pointer, “my_packet” points to the packet
    that contains the next bytes from the file. If the file is completely
    downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="50933-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="50933-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="50933-430">FTP 서버에서 파일 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="50933-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-431">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-431">Prototype</span></span>

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-432">Description</span><span class="sxs-lookup"><span data-stu-id="50933-432">Description</span></span>

<span data-ttu-id="50933-433">이 서비스는 FTP 서버에서 파일의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="50933-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-434">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-434">Input Parameters</span></span>

- <span data-ttu-id="50933-435">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-435">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-436">**filename** 현재 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-436">**filename** Current name of file.</span></span>
- <span data-ttu-id="50933-437">**new_filename** 파일에 사용할 새 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-437">**new_filename** New name for file.</span></span>
- <span data-ttu-id="50933-438">**wait_option** 서비스에서 FTP 클라이언트 파일 이름 변경을 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-438">**wait_option** Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="50933-439">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-440">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-440">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-442">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-442">Return Values</span></span>

- <span data-ttu-id="50933-443">**NX_SUCCESS** (0x00) FTP 파일 이름을 성공적으로 변경했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-443">**NX_SUCCESS** (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="50933-444">**NX_FTP_NOT_CONNECTED** (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-444">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="50933-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) 3XX(ok) 응답을 받지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="50933-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="50933-447">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-447">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-448">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-448">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-449">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-449">Allowed From</span></span>

<span data-ttu-id="50933-450">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-450">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-451">예제</span><span class="sxs-lookup"><span data-stu-id="50933-451">Example</span></span>

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="50933-452">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="50933-452">nx_ftp_client_file_write</span></span>

<span data-ttu-id="50933-453">파일에 쓰기</span><span class="sxs-lookup"><span data-stu-id="50933-453">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-454">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-454">Prototype</span></span>

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="50933-455">Description</span><span class="sxs-lookup"><span data-stu-id="50933-455">Description</span></span>

<span data-ttu-id="50933-456">이 서비스는 FTP 서버에서 이전에 열린 파일에 데이터 패킷을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="50933-456">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-457">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-457">Input Parameters</span></span>

- <span data-ttu-id="50933-458">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-458">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-459">**packet_ptr** 쓸 데이터를 포함하는 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-459">**packet_ptr** Packet pointer containing data to write.</span></span>
- <span data-ttu-id="50933-460">**wait_option** 서비스에서 FTP 클라이언트 파일 쓰기를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-460">**wait_option** Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="50933-461">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-461">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="50933-462">**시간 제한 값** (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-462">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="50933-463">**TX_WAIT_FOREVER** (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-463">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-464">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-464">Return Values</span></span>

- <span data-ttu-id="50933-465">**NX_SUCCESS** (0x00) FTP 파일을 성공적으로 썼습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-465">**NX_SUCCESS** (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="50933-466">**NX_FTP_NOT_OPEN** (0xD5) FTP 클라이언트가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-466">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="50933-467">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-467">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-468">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-469">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-469">Allowed From</span></span>

<span data-ttu-id="50933-470">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-471">예제</span><span class="sxs-lookup"><span data-stu-id="50933-471">Example</span></span>

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="50933-472">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="50933-472">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="50933-473">수동 전송 모드 사용 또는 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="50933-473">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-474">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-474">Prototype</span></span>

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="50933-475">Description</span><span class="sxs-lookup"><span data-stu-id="50933-475">Description</span></span>

<span data-ttu-id="50933-476">이 서비스를 이전에 만든 FTP 클라이언트 인스턴스에서 passive_mode_enabled 입력을 NX_TRUE로 설정하여, 이후 파일 읽기 또는 쓰기(RETR, STOR) 또는 디렉터리 목록 다운로드(NLST)에 대한 호출이 전송 모드에서 수행될 경우 수동 전송 모드를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-476">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="50933-477">수동 모드 전송을 사용하지 않도록 설정하고 활성 전송 모드의 기본 동작으로 돌아가려면 passive_mode_enabled 입력을 NX_FALSE로 설정하여 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-477">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-478">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-478">Input Parameters</span></span>

- <span data-ttu-id="50933-479">**ftp_client_ptr** FTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-479">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="50933-480">**passive_mode_enabled** NX_TRUE로 설정된 경우 수동 모드가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-480">**passive_mode_enabled** If set to NX_TRUE, passive mode is enabled.</span></span><br /><span data-ttu-id="50933-481">NX_FALSE로 설정된 경우 수동 모드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-481">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-482">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-482">Return Values</span></span>

- <span data-ttu-id="50933-483">**NX_SUCCESS** (0x00) 수동 모드를 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-483">**NX_SUCCESS** (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="50933-484">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-484">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-485">NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="50933-485">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-486">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-486">Allowed From</span></span>

<span data-ttu-id="50933-487">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-487">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-488">예제</span><span class="sxs-lookup"><span data-stu-id="50933-488">Example</span></span>

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="50933-489">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="50933-489">nx_ftp_server_create</span></span>

<span data-ttu-id="50933-490">FTP 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="50933-490">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-491">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-491">Prototype</span></span>

```C
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address,
        UINT client_port, CHAR *name, CHAR *password,
        CHAR *extra_info),
    UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address, UINT client_port,
         CHAR *name, CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="50933-492">Description</span><span class="sxs-lookup"><span data-stu-id="50933-492">Description</span></span>

<span data-ttu-id="50933-493">이 서비스는 이전에 만든 특정 NetX IP 인스턴스에 FTP 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50933-493">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="50933-494">***nx_ftp_server_start*** 를 호출하여 FTP 서버를 시작해야 작업이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-494">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-495">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-495">Input Parameters</span></span>

- <span data-ttu-id="50933-496">**ftp_server_ptr** FTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-496">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="50933-497">**ftp_server_name** FTP 서버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-497">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="50933-498">**ip_ptr** 연결된 NetX IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-498">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="50933-499">IP 인스턴스에는 FTP 서버가 하나만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-499">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="50933-500">**media_ptr** 연결된 FileX 미디어 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-500">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="50933-501">**stack_ptr** 내부 FTP 서버 스레드의 스택 영역에 대한 메모리 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-501">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="50933-502">**stack_size** *stack_ptr* 에 의해 지정된 스택 영역의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-502">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="50933-503">**pool_ptr** 기본 NetX 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-503">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="50933-504">풀에 있는 패킷의 페이로드 크기는 최대 파일 이름/경로를 수용할 만큼 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-504">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="50933-505">**ftp_login** 애플리케이션의 로그인 함수에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-505">**ftp_login** Function pointer to application’s login function.</span></span> <span data-ttu-id="50933-506">이 함수에는 연결을 요청하는 클라이언트의 사용자 이름 및 암호와 ULONG 데이터 형식의 클라이언트 주소가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-506">This function is supplied the username and password from the Client requesting a connection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="50933-507">유효한 경우 애플리케이션의 로그인 함수는 NX_SUCCESS를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-507">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="50933-508">**ftp_logout** 애플리케이션의 로그아웃 함수에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-508">**ftp_logout** Function pointer to application’s logout function.</span></span> <span data-ttu-id="50933-509">이 함수에는 연결 해제를 요청하는 클라이언트의 사용자 이름 및 암호와 ULONG 데이터 형식의 클라이언트 주소가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-509">This function is supplied the username and password from the Client requesting a disconnection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="50933-510">유효한 경우 애플리케이션의 로그인 함수는 NX_SUCCESS를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-510">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-511">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-511">Return Values</span></span>

- <span data-ttu-id="50933-512">**NX_SUCCESS** (0x00) FTP 서버를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-512">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="50933-513">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-513">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-514">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-514">Allowed From</span></span>

<span data-ttu-id="50933-515">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="50933-515">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-516">예제</span><span class="sxs-lookup"><span data-stu-id="50933-516">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nx_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nxd_ftp_server_create"></a><span data-ttu-id="50933-517">nxd_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="50933-517">nxd_ftp_server_create</span></span>

<span data-ttu-id="50933-518">IPv4 및 IPv6를 지원하는 FTP 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="50933-518">Create FTP Server with IPv4 and IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-519">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-519">Prototype</span></span>

```C
UINT nxd_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info),
    UINT (*ftp_logout_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="50933-520">Description</span><span class="sxs-lookup"><span data-stu-id="50933-520">Description</span></span>

<span data-ttu-id="50933-521">이 서비스는 이전에 만든 특정 NetX IP 인스턴스에 FTP 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50933-521">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="50933-522">FTP 서버가 생성된 후 작업을 시작하려는 경우에도 ***nx_ftp_server_start*** 호출을 사용하여 서버를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-522">Note the FTP Server still needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation after the Server is created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-523">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-523">Input Parameters</span></span>

- <span data-ttu-id="50933-524">**ftp_server_ptr** FTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-524">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="50933-525">**ftp_server_name** FTP 서버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-525">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="50933-526">**ip_ptr** 연결된 NetX IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-526">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="50933-527">IP 인스턴스에는 FTP 서버가 하나만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-527">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="50933-528">**media_ptr** 연결된 FileX 미디어 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-528">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="50933-529">**stack_ptr** 내부 FTP 서버 스레드의 스택 영역에 대한 메모리 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-529">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="50933-530">**stack_size** *stack_ptr* 에 의해 지정된 스택 영역의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-530">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="50933-531">**pool_ptr** 기본 NetX 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-531">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="50933-532">풀에 있는 패킷의 페이로드 크기는 최대 파일 이름/경로를 수용할 만큼 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-532">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="50933-533">**ftp_login_duo** 애플리케이션의 로그인 함수에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-533">**ftp_login_duo** Function pointer to application’s login function.</span></span> <span data-ttu-id="50933-534">이 함수에는 연결을 요청하는 클라이언트의 사용자 이름 및 암호와 NXD_ADDRESS 데이터 형식의 클라이언트 주소에 대한 포인터가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-534">This function is supplied the username and password from the Client requesting a connection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="50933-535">유효한 경우 애플리케이션의 로그인 함수는 NX_SUCCESS를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-535">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="50933-536">**ftp_logout_duo** 애플리케이션의 로그아웃 함수에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-536">**ftp_logout_duo** Function pointer to application’s logout function.</span></span> <span data-ttu-id="50933-537">이 함수에는 연결 해제를 요청하는 클라이언트의 사용자 이름 및 암호와 NXD_ADDRESS 데이터 형식의 클라이언트 주소에 대한 포인터가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="50933-537">This function is supplied the username and password from the Client requesting a disconnection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="50933-538">유효한 경우 애플리케이션의 로그인 함수는 NX_SUCCESS를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-538">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-539">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-539">Return Values</span></span>

- <span data-ttu-id="50933-540">**NX_SUCCESS** (0x00) FTP 서버를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-540">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="50933-541">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-541">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-542">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-542">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-543">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-543">Allowed From</span></span>

<span data-ttu-id="50933-544">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="50933-544">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-545">예제</span><span class="sxs-lookup"><span data-stu-id="50933-545">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nxd_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_duo_login, my_duo_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="50933-546">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="50933-546">nx_ftp_server_delete</span></span>

<span data-ttu-id="50933-547">FTP 서버 삭제</span><span class="sxs-lookup"><span data-stu-id="50933-547">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-548">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-548">Prototype</span></span>

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="50933-549">Description</span><span class="sxs-lookup"><span data-stu-id="50933-549">Description</span></span>

<span data-ttu-id="50933-550">이 서비스는 이전에 만든 FTP 서버 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-550">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-551">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-551">Input Parameters</span></span>

- <span data-ttu-id="50933-552">**ftp_server_ptr** FTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-552">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-553">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-553">Return Values</span></span>

- <span data-ttu-id="50933-554">**NX_SUCCESS** (0x00) FTP 서버를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-554">**NX_SUCCESS** (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="50933-555">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-555">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-556">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-556">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-557">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-557">Allowed From</span></span>

<span data-ttu-id="50933-558">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-558">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-559">예제</span><span class="sxs-lookup"><span data-stu-id="50933-559">Example</span></span>

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="50933-560">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="50933-560">nx_ftp_server_start</span></span>

<span data-ttu-id="50933-561">FTP 서버 시작</span><span class="sxs-lookup"><span data-stu-id="50933-561">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-562">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-562">Prototype</span></span>

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="50933-563">Description</span><span class="sxs-lookup"><span data-stu-id="50933-563">Description</span></span>

<span data-ttu-id="50933-564">이 서비스는 이전에 만든 FTP 서버 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-564">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-565">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-565">Input Parameters</span></span>

- <span data-ttu-id="50933-566">**ftp_server_ptr** FTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-566">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-567">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-567">Return Values</span></span>

- <span data-ttu-id="50933-568">**NX_SUCCESS** (0x00) FTP 서버를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-568">**NX_SUCCESS** (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="50933-569">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-569">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-570">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-570">Allowed From</span></span>

<span data-ttu-id="50933-571">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-571">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-572">예제</span><span class="sxs-lookup"><span data-stu-id="50933-572">Example</span></span>

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="50933-573">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="50933-573">nx_ftp_server_stop</span></span>

<span data-ttu-id="50933-574">FTP 서버 중지</span><span class="sxs-lookup"><span data-stu-id="50933-574">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="50933-575">프로토타입</span><span class="sxs-lookup"><span data-stu-id="50933-575">Prototype</span></span>

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="50933-576">Description</span><span class="sxs-lookup"><span data-stu-id="50933-576">Description</span></span>

<span data-ttu-id="50933-577">이 서비스는 이전에 만들어서 시작한 FTP 서버 인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="50933-577">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="50933-578">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="50933-578">Input Parameters</span></span>

- <span data-ttu-id="50933-579">**ftp_server_ptr** FTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-579">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="50933-580">반환 값</span><span class="sxs-lookup"><span data-stu-id="50933-580">Return Values</span></span>

- <span data-ttu-id="50933-581">**NX_SUCCESS** (0x00) FTP 서버를 성공적으로 중지했습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-581">**NX_SUCCESS** (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="50933-582">NX_PTR_ERROR (0x07) 잘못된 FTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="50933-582">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="50933-583">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50933-583">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="50933-584">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="50933-584">Allowed From</span></span>

<span data-ttu-id="50933-585">스레드</span><span class="sxs-lookup"><span data-stu-id="50933-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="50933-586">예제</span><span class="sxs-lookup"><span data-stu-id="50933-586">Example</span></span>

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
