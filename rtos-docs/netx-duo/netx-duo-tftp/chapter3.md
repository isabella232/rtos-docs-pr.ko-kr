---
title: 3장 - Azure RTOS NetX Duo TFTP 서비스 설명
description: 이 장에서는 알파벳 순서로 아래 나열된 모든 NetX Duo TFTP 서비스에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56f0d8edb991fff6ae30b6411e375ace58c544f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810524"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a><span data-ttu-id="0a52d-103">3장 - Azure RTOS NetX Duo TFTP 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="0a52d-103">Chapter 3 - Description of Azure RTOS NetX Duo TFTP services</span></span>

<span data-ttu-id="0a52d-104">이 장에서는 알파벳 순서로 아래 나열된 모든 NetX Duo TFTP 서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-104">This chapter contains a description of all NetX Duo TFTP services (listed below) in alphabetic order.</span></span> <span data-ttu-id="0a52d-105">특별히 지정되지 않은 한 모든 서비스에서 IPv6 및 IPv4 통신이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-105">Unless otherwise specified, all services support IPv6 and IPv4 communications.</span></span>

<span data-ttu-id="0a52d-106">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-106">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="0a52d-107">**nxd_tftp_client_file_open**: *TFTP 클라이언트 파일을 엽니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-107">**nxd_tftp_client_file_open**: *Open TFTP client file*</span></span>

- <span data-ttu-id="0a52d-108">**nxd_tftp_client_create**: *TFTP 클라이언트 인스턴스를 만듭니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-108">**nxd_tftp_client_create**: *Create a TFTP client instance*</span></span>

- <span data-ttu-id="0a52d-109">**nxd_tftp_client_delete**: *TFTP 클라이언트 인스턴스를 삭제합니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-109">**nxd_tftp_client_delete**: *Delete a TFTP client instance*</span></span>

- <span data-ttu-id="0a52d-110">**nxd_tftp_client_error_info_get**: *클라이언트 오류 정보를 가져옵니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-110">**nxd_tftp_client_error_info_get**: *Get client error information*</span></span>

- <span data-ttu-id="0a52d-111">**nxd_tftp_client_file_close**: *클라이언트 파일을 닫습니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-111">**nxd_tftp_client_file_close**: *Close client file*</span></span>

- <span data-ttu-id="0a52d-112">**nxd_tftp_client_file_open**: *클라이언트 파일을 엽니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-112">**nxd_tftp_client_file_open**: *Open client file*</span></span>

- <span data-ttu-id="0a52d-113">**nxd_tftp_client_file_read**: *클라이언트 파일에서 블록을 읽습니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-113">**nxd_tftp_client_file_read**: *Read a block from client file*</span></span>

- <span data-ttu-id="0a52d-114">**nxd_tftp_client_file_write**: *클라이언트 파일에 블록을 씁니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-114">**nxd_tftp_client_file_write**: *Write block to client file*</span></span>

- <span data-ttu-id="0a52d-115">**nxd_tftp_client_packet_allocate**: *클라이언트 파일 쓰기에 대해 패킷을 할당합니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-115">**nxd_tftp_client_packet_allocate**: *Allocate packet for client file write*</span></span>

- <span data-ttu-id="0a52d-116">**nxd_tftp_client_set_interface**: *TFTP 요청에 대해 실제 인터페이스를 설정합니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-116">**nxd_tftp_client_set_interface**: *Set the physical interface for TFTP requests*</span></span>

- <span data-ttu-id="0a52d-117">**nxd_tftp_server_create**: *TFTP 서버를 만듭니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-117">**nxd_tftp_server_create**: *Create TFTP server*</span></span>

- <span data-ttu-id="0a52d-118">**nxd_tftp_server_delete**: *TFTP 서버를 삭제합니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-118">**nxd_tftp_server_delete**: *Delete TFTP server*</span></span>

- <span data-ttu-id="0a52d-119">**nxd_tftp_server_start**: *TFTP 서버를 시작합니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-119">**nxd_tftp_server_start**: *Start TFTP server*</span></span>

- <span data-ttu-id="0a52d-120">**nxd_tftp_server_stop**: *TFTP 서버를 중지합니다.*</span><span class="sxs-lookup"><span data-stu-id="0a52d-120">**nxd_tftp_server_stop**: *Stop TFTP server*</span></span>

> [!NOTE] 
> <span data-ttu-id="0a52d-121">위에 나열된 모든 서비스의 IPv4 해당 항목은 NetX Duo TFTP 클라이언트 및 서버(예: *nx_tftp_server_create* 및 *nx_tftp_client_file_open*)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-121">The IPv4 equivalents of all the services listed above are available in NetX Duo TFTP Client and Server e.g. *nx_tftp_server_create* and *nx_tftp_client_file_open*.</span></span> <span data-ttu-id="0a52d-122">다음 페이지에는 ‘Duo’ API 설명(예: *nxd_* 로 시작하는 서비스)만 제공되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-122">Only the ‘Duo’ API descriptions, e.g. services beginning with *nxd_*, are provided in the following pages.</span></span> <span data-ttu-id="0a52d-123">NXD_ADDRESS \* 입력이 지정된 경우 IPv4 해당 API가 ULONG 입력을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-123">Where an NXD_ADDRESS \* input is specified, the IPv4 equivalent API calls for ULONG input.</span></span> <span data-ttu-id="0a52d-124">그렇지 않으면 API 사용에 차이가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-124">Otherwise there is no difference in using the API.</span></span>

## <a name="nxd_tftp_client_create"></a><span data-ttu-id="0a52d-125">nxd_tftp_client_create</span><span class="sxs-lookup"><span data-stu-id="0a52d-125">nxd_tftp_client_create</span></span>

<span data-ttu-id="0a52d-126">TFTP 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="0a52d-126">Create a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-127">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-127">Prototype</span></span>

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="0a52d-128">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-128">Description</span></span>

<span data-ttu-id="0a52d-129">이 서비스는 이전에 만든 IP 인스턴스에 대해 TFTP 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-129">This service creates a TFTP Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a52d-130">애플리케이션은 제공된 IP 및 패킷 풀이 이미 생성되어 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-130">The application must make certain the supplied IP and packet pool are already created.</span></span> <span data-ttu-id="0a52d-131">또한 이 서비스를 호출하기 전 IP 인스턴스에 대해 UDP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-131">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-132">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-132">Input Parameters</span></span>

- <span data-ttu-id="0a52d-133">**tftp_client_ptr** TFTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-133">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="0a52d-134">**tftp_client_name** 이 TFTP 클라이언트 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-134">**tftp_client_name** Name of this TFTP Client instance</span></span>

- <span data-ttu-id="0a52d-135">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-135">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="0a52d-136">**pool_ptr** 패킷 풀 TFTP 클라이언트 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-136">**pool_ptr** Pointer to packet pool TFTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-137">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-137">Return Values</span></span>

- <span data-ttu-id="0a52d-138">**NX_SUCCESS** (0x00) TFTP를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-138">**NX_SUCCESS**(0x00) Successful TFTP create.</span></span>

- <span data-ttu-id="0a52d-139">**NX_TFTP_INVALID_IP_VERSION** (0x0C) IP 버전이 잘못되었거나 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-139">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid or unsupported IP version</span></span>

- <span data-ttu-id="0a52d-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 잘못된 서버 IP 주소가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP address received</span></span>

- <span data-ttu-id="0a52d-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09) 서버 ACK가 수신되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Server ACK not received</span></span>

- <span data-ttu-id="0a52d-142">NX_PTR_ERROR (0x16) 잘못된 IP, 풀 또는 TFTP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-142">NX_PTR_ERROR (0x16) Invalid IP, pool, or TFTP pointer.</span></span>

- <span data-ttu-id="0a52d-143">NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="0a52d-143">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="0a52d-144">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-144">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-145">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-145">Allowed From</span></span>

<span data-ttu-id="0a52d-146">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-146">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-147">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-147">Example</span></span>

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a><span data-ttu-id="0a52d-148">nxd_tftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="0a52d-148">nxd_tftp_client_delete</span></span>

<span data-ttu-id="0a52d-149">TFTP 클라이언트 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="0a52d-149">Delete a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-150">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-150">Prototype</span></span>

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="0a52d-151">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-151">Description</span></span>

<span data-ttu-id="0a52d-152">이 서비스는 이전에 만든 TFTP 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-152">This service deletes a previously created TFTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-153">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-153">Input Parameters</span></span>

- <span data-ttu-id="0a52d-154">**tftp_client_ptr** 이전에 만든 TFTP 클라이언트 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-154">**tftp_client_ptr** Pointer to previously created TFTP client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-155">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-155">Return Values</span></span>

- <span data-ttu-id="0a52d-156">**NX_SUCCESS** (0x00) TFTP 클라이언트를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-156">**NX_SUCCESS** (0x00) Successful TFTP Client delete.</span></span>

- <span data-ttu-id="0a52d-157">NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-157">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0a52d-158">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-158">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-159">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-159">Allowed From</span></span>

<span data-ttu-id="0a52d-160">스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-160">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-161">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-161">Example</span></span>

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a><span data-ttu-id="0a52d-162">nxd_tftp_client_error_info_get</span><span class="sxs-lookup"><span data-stu-id="0a52d-162">nxd_tftp_client_error_info_get</span></span>

<span data-ttu-id="0a52d-163">클라이언트 오류 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="0a52d-163">Get client error information</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-164">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-164">Prototype</span></span>

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a><span data-ttu-id="0a52d-165">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-165">Description</span></span>

<span data-ttu-id="0a52d-166">이 서비스는 수신된 마지막 오류 코드를 반환하고 포인터를 클라이언트의 내부 오류 문자열로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-166">This service returns the last error code received and sets the pointer to the client’s internal error string.</span></span> <span data-ttu-id="0a52d-167">오류 조건에서 사용자는 서버에서 마지막으로 보낸 오류를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-167">In error conditions, the user can view the last error sent by the server.</span></span> <span data-ttu-id="0a52d-168">null 오류 문자열은 오류가 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-168">A null error string indicates no error is present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-169">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-169">Input Parameters</span></span>

- <span data-ttu-id="0a52d-170">**tftp_client_ptr** 이전에 만든 TFTP 클라이언트 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-170">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="0a52d-171">**error_code** 오류 코드의 대상 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-171">**error_code** Pointer to destination area for error code</span></span>

- <span data-ttu-id="0a52d-172">**error_string** 오류 문자열의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-172">**error_string** Pointer to destination for error string</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-173">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-173">Return Values</span></span>

- <span data-ttu-id="0a52d-174">**NX_SUCCESS** (0x00) TFTP 오류 정보를 성공적으로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-174">**NX_SUCCESS** (0x00) Successful TFTP error info get.</span></span>  

- <span data-ttu-id="0a52d-175">NX_PTR_ERROR (0x16) 잘못된 TFTP 클라이언트 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-175">NX_PTR_ERROR (0x16) Invalid TFTP Client pointer.</span></span>

- <span data-ttu-id="0a52d-176">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-176">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-177">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-177">Allowed From</span></span>

<span data-ttu-id="0a52d-178">스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-178">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-179">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-179">Example</span></span>

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a><span data-ttu-id="0a52d-180">nxd_tftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="0a52d-180">nxd_tftp_client_file_close</span></span>

<span data-ttu-id="0a52d-181">클라이언트 파일 닫기</span><span class="sxs-lookup"><span data-stu-id="0a52d-181">Close client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-182">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-182">Prototype</span></span>

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="0a52d-183">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-183">Description</span></span>

<span data-ttu-id="0a52d-184">이 서비스는 TFTP 클라이언트 인스턴스가 이전에 연 파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-184">This service closes the previously opened file by this TFTP Client instance.</span></span> <span data-ttu-id="0a52d-185">TFTP 클라이언트 인스턴스는 파일을 한 번에 하나만 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-185">A TFTP Client instance is allowed to have only one file open at a time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-186">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-186">Input Parameters</span></span>

- <span data-ttu-id="0a52d-187">**tftp_client_ptr** 이전에 만든 TFTP 클라이언트 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-187">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="0a52d-188">**ip_type** 사용할 IP 주소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-188">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0a52d-189">유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-189">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-190">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-190">Return Values</span></span>

- <span data-ttu-id="0a52d-191">**NX_SUCCESS** (0x00) TFTP 파일을 성공적으로 닫았습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-191">**NX_SUCCESS** (0x00) Successful TFTP file close.</span></span>

- <span data-ttu-id="0a52d-192">NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-192">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0a52d-193">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-193">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="0a52d-194">NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-194">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-195">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-195">Allowed From</span></span>

<span data-ttu-id="0a52d-196">스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-197">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-197">Example</span></span>

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a><span data-ttu-id="0a52d-198">nx_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="0a52d-198">nx_tftp_client_file_open</span></span>

<span data-ttu-id="0a52d-199">TFTP 클라이언트 파일 열기</span><span class="sxs-lookup"><span data-stu-id="0a52d-199">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-200">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-200">Prototype</span></span>

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0a52d-201">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-201">Description</span></span>

<span data-ttu-id="0a52d-202">이 서비스는 지정된 IP 주소로 TFTP 서버에서 지정된 파일을 열려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-202">This service attempts to open the specified file on the TFTP Server at the specified IP address.</span></span> <span data-ttu-id="0a52d-203">파일은 읽기 또는 쓰기용으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-203">The file will be opened for either reading or writing.</span></span> 

> [!NOTE] 
> <span data-ttu-id="0a52d-204">이것은 IPv4 패킷으로만 제한되며 NetX TFTP 애플리케이션을 지원하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-204">This is limited to IPv4 packets only, and is intended for supporting NetX TFTP applications.</span></span> <span data-ttu-id="0a52d-205">개발자가 동등한 “duo” 서비스 *nxd_tftp_client_file_open* 을 사용하도록 애플리케이션을 이식하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-205">Developers are encouraged to port their applications to using equivalent “duo” service *nxd_tftp_client_file_open.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-206">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-206">Input Parameters</span></span>

- <span data-ttu-id="0a52d-207">**tftp_client_ptr** TFTP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-207">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="0a52d-208">**file_name** NULL로 종료되었고 적합한 경로 정보를 포함하는 ASCII 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-208">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="0a52d-209">**server_ip_address** 서버 TFTP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-209">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="0a52d-210">**open_type** 열기 요청의 유형 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-210">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="0a52d-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="0a52d-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="0a52d-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="0a52d-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="0a52d-213">**wait_option** 서비스에서 TFTP 클라이언트 파일 열기를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-213">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="0a52d-214">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-214">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0a52d-215">**시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0a52d-215">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="0a52d-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0a52d-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span> 
  
  <span data-ttu-id="0a52d-217">TX_WAIT_FOREVER를 선택하면 TFTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-217">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span> 
  
  <span data-ttu-id="0a52d-218">숫자 값(1-0xFFFFFFFE)을 선택하면 TFTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-218">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="0a52d-219">**ip_type** 사용할 IP 주소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-219">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0a52d-220">유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-220">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-221">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-221">Return Values</span></span>

- <span data-ttu-id="0a52d-222">**NX_SUCCESS** (0x00) 클라이언트 파일을 성공적으로 열었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-222">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="0a52d-223">**NX_TFTP_NOT_CLOSED** (0xC3) 클라이언트가 파일을 이미 열었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-223">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="0a52d-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 잘못된 서버 주소가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="0a52d-225">**NX_TFTP_NO_ACK_RECEIVED** (0x09) 서버에서 ACK가 수신되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-225">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="0a52d-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 잘못된 서버 IP가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="0a52d-227">**NX_TFTP_CODE_ERROR** (0x05) 오류 코드가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-227">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="0a52d-228">NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-228">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0a52d-229">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="0a52d-229">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0a52d-230">NX_IP_ADDRESS_ERROR (0x21) 잘못된 서버 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-230">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="0a52d-231">NX_OPTION_ERROR (0x0A) 잘못된 개방형 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-231">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-232">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-232">Allowed From</span></span>

<span data-ttu-id="0a52d-233">스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-234">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-234">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a><span data-ttu-id="0a52d-235">nxd_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="0a52d-235">nxd_tftp_client_file_open</span></span>

<span data-ttu-id="0a52d-236">TFTP 클라이언트 파일 열기</span><span class="sxs-lookup"><span data-stu-id="0a52d-236">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-237">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-237">Prototype</span></span>

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="0a52d-238">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-238">Description</span></span>

<span data-ttu-id="0a52d-239">이 서비스는 지정된 IPv6 주소로 TFTP 서버에서 지정된 파일을 열려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-239">This service attempts to open the specified file on the TFTP Server at the specified IPv6 address.</span></span> <span data-ttu-id="0a52d-240">파일은 읽기 또는 쓰기용으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-240">The file will be opened for either reading or writing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-241">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-241">Input Parameters</span></span>

- <span data-ttu-id="0a52d-242">**tftp_client_ptr** TFTP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-242">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="0a52d-243">**file_name** NULL로 종료되었고 적합한 경로 정보를 포함하는 ASCII 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-243">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="0a52d-244">**server_ip_address** 서버 TFTP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-244">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="0a52d-245">**open_type** 열기 요청의 유형 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-245">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="0a52d-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="0a52d-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="0a52d-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="0a52d-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="0a52d-248">**wait_option** 서비스에서 TFTP 클라이언트 파일 열기를 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-248">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="0a52d-249">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-249">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0a52d-250">**시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0a52d-250">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="0a52d-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0a52d-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="0a52d-252">TX_WAIT_FOREVER를 선택하면 TFTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-252">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span>

  <span data-ttu-id="0a52d-253">숫자 값(1-0xFFFFFFFE)을 선택하면 TFTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-253">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="0a52d-254">**ip_type** 사용할 IP 주소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-254">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0a52d-255">유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-255">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-256">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-256">Return Values</span></span>

- <span data-ttu-id="0a52d-257">**NX_SUCCESS** (0x00) 클라이언트 파일을 성공적으로 열었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-257">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="0a52d-258">**NX_TFTP_NOT_CLOSED** (0xC3) 클라이언트가 파일을 이미 열었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-258">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="0a52d-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 잘못된 서버 주소가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="0a52d-260">**NX_TFTP_NO_ACK_RECEIVED** (0x09) 서버에서 ACK가 수신되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-260">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="0a52d-261">**NX_TFTP_INVALID_IP_VERSION** (0x0C) 잘못된 IP 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-261">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="0a52d-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 잘못된 서버 IP가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="0a52d-263">**NX_TFTP_CODE_ERROR** (0x05) 오류 코드가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-263">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="0a52d-264">NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-264">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0a52d-265">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="0a52d-265">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0a52d-266">NX_IP_ADDRESS_ERROR (0x21) 잘못된 서버 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-266">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="0a52d-267">NX_OPTION_ERROR (0x0A) 잘못된 개방형 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-267">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

- <span data-ttu-id="0a52d-268">NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="0a52d-268">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-269">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-269">Allowed From</span></span>

<span data-ttu-id="0a52d-270">스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-270">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-271">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-271">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a><span data-ttu-id="0a52d-272">nxd_tftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="0a52d-272">nxd_tftp_client_file_read</span></span>

<span data-ttu-id="0a52d-273">클라이언트 파일에서 블록 읽기</span><span class="sxs-lookup"><span data-stu-id="0a52d-273">Read a block from client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-274">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-274">Prototype</span></span>

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="0a52d-275">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-275">Description</span></span>

<span data-ttu-id="0a52d-276">이 서비스는 이전에 연 TFTP 클라이언트 파일에서 512바이트 블록을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-276">This service reads a 512-byte block from the previously opened TFTP Client file.</span></span> <span data-ttu-id="0a52d-277">512바이트 미만의 블록은 파일 끝을 신호로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-277">A block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-278">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-278">Input Parameters</span></span>

- <span data-ttu-id="0a52d-279">**tftp_client_ptr** TFTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-279">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="0a52d-280">**packet_ptr** 파일에서 읽은 블록을 포함하는 패킷의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-280">**packet_ptr** Destination for packet containing the block read from the file.</span></span>

- <span data-ttu-id="0a52d-281">**wait_option** 읽기가 완료될 때까지 서버가 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-281">**wait_option** Defines how long the service will wait for the read to complete.</span></span> <span data-ttu-id="0a52d-282">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-282">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0a52d-283">**시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0a52d-283">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="0a52d-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0a52d-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="0a52d-285">TX_WAIT_FOREVER를 선택하면 TFTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-285">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>

  <span data-ttu-id="0a52d-286">숫자 값(1-0xFFFFFFFE)을 선택하면 TFTP 서버가 파일 블록을 전송하도록 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-286">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send a block of the file.</span></span>

- <span data-ttu-id="0a52d-287">**ip_type** 사용할 IP 주소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-287">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0a52d-288">유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-288">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-289">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-289">Return Values</span></span>

- <span data-ttu-id="0a52d-290">**NX_SUCCESS** (0x00) 클라이언트 블록을 성공적으로 읽었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-290">**NX_SUCCESS** (0x00) Successful Client block read</span></span>

- <span data-ttu-id="0a52d-291">**NX_TFTP_NOT_OPEN** (0xC3) 지정된 클라이언트 파일이 읽기용으로 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-291">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for reading</span></span>

- <span data-ttu-id="0a52d-292">**NX_NO_PACKET** (0x01) 서버에서 수신된 패킷이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-292">**NX_NO_PACKET** (0x01) No Packet received from Server.</span></span>

- <span data-ttu-id="0a52d-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 잘못된 서버 주소가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="0a52d-294">**NX_TFTP_NO_ACK_RECEIVED** (0x09) 서버에서 ACK가 수신되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-294">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from Server</span></span>

- <span data-ttu-id="0a52d-295">**NX_TFTP_END_OF_FILE** (0xC5) 파일 끝이 검색되었습니다(오류 아님).</span><span class="sxs-lookup"><span data-stu-id="0a52d-295">**NX_TFTP_END_OF_FILE** (0xC5) End of file detected (not an error).</span></span>

- <span data-ttu-id="0a52d-296">**NX_TFTP_INVALID_IP_VERSION** (0x0C) 잘못된 IP 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-296">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="0a52d-297">**NX_TFTP_CODE_ERROR** (0x05) 오류 코드가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-297">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="0a52d-298">**NX_TFTP_FAILED** (0xC2) 알 수 없는 TFTP 코드가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-298">**NX_TFTP_FAILED** (0xC2) Unknown TFTP code received</span></span>

- <span data-ttu-id="0a52d-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) 잘못된 블록 번호가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Invalid block number received</span></span>

- <span data-ttu-id="0a52d-300">NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-300">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0a52d-301">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="0a52d-301">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0a52d-302">NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="0a52d-302">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-303">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-303">Allowed From</span></span>

<span data-ttu-id="0a52d-304">스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-304">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-305">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-305">Example</span></span>

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a><span data-ttu-id="0a52d-306">nxd_tftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="0a52d-306">nxd_tftp_client_file_write</span></span>

<span data-ttu-id="0a52d-307">클라이언트 파일에 블록 쓰기</span><span class="sxs-lookup"><span data-stu-id="0a52d-307">Write a block to Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-308">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-308">Prototype</span></span>

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="0a52d-309">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-309">Description</span></span>

<span data-ttu-id="0a52d-310">이 서비스는 이전에 열린 TFTP 클라이언트 파일에 512바이트 블록을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-310">This service writes a 512-byte block to the previously opened TFTP Client file.</span></span> <span data-ttu-id="0a52d-311">512바이트 미만의 블록을 지정하면 파일 끝을 신호로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-311">Specifying a block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-312">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-312">Input Parameters</span></span>

- <span data-ttu-id="0a52d-313">**tftp_client_ptr** TFTP 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-313">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="0a52d-314">**packet_ptr** 파일에 쓸 블록이 포함된 패킷입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-314">**packet_ptr** Packet containing the block to write to the file.</span></span>

- <span data-ttu-id="0a52d-315">**wait_option** 쓰기가 완료될 때까지 서버가 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-315">**wait_option** Defines how long the service will wait for the write to complete.</span></span> <span data-ttu-id="0a52d-316">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-316">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0a52d-317">**시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0a52d-317">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="0a52d-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0a52d-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="0a52d-319">TX_WAIT_FOREVER를 선택하면 TFTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-319">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>
 
  <span data-ttu-id="0a52d-320">숫자 값(1-0xFFFFFFFE)을 선택하면 TFTP 서버가 쓰기 요청에 대해 ACK를 전송하도록 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send an ACK for the write request.</span></span>

- <span data-ttu-id="0a52d-321">**ip_type** 사용할 IP 주소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-321">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0a52d-322">유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-322">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-323">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-323">Return Values</span></span>

- <span data-ttu-id="0a52d-324">**NX_SUCCESS** (0x00) 클라이언트 블록을 성공적으로 썼습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-324">**NX_SUCCESS** (0x00) Successful Client block write</span></span>

- <span data-ttu-id="0a52d-325">**NX_TFTP_NOT_OPEN** (0xC3) 지정된 클라이언트 파일이 쓰기용으로 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-325">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for writing</span></span>

- <span data-ttu-id="0a52d-326">**NX_TFTP_TIMEOUT** (0xC1) 서버 ACK를 기다리는 동안 시간이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-326">**NX_TFTP_TIMEOUT** (0xC1) Timeout waiting for Server ACK</span></span>

- <span data-ttu-id="0a52d-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 잘못된 서버 주소가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="0a52d-328">**NX_TFTP_NO_ACK_RECEIVED** (0x09) 서버에서 ACK가 수신되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-328">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="0a52d-329">**NX_TFTP_INVALID_IP_VERSION** (0x0C) 잘못된 IP 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-329">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="0a52d-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 잘못된 서버 주소가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="0a52d-331">**NX_TFTP_CODE_ERROR** (0x05) 오류 코드가 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-331">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="0a52d-332">NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-332">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0a52d-333">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="0a52d-333">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0a52d-334">NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="0a52d-334">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-335">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-335">Allowed From</span></span>

<span data-ttu-id="0a52d-336">스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-336">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-337">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-337">Example</span></span>

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a><span data-ttu-id="0a52d-338">nxd_tftp_client_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="0a52d-338">nxd_tftp_client_packet_allocate</span></span>

<span data-ttu-id="0a52d-339">클라이언트 파일 쓰기에 패킷 할당</span><span class="sxs-lookup"><span data-stu-id="0a52d-339">Allocate packet for Client file write</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-340">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-340">Prototype</span></span>

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="0a52d-341">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-341">Description</span></span>

<span data-ttu-id="0a52d-342">이 서비스는 지정된 패킷 풀에서 UDP 패킷을 할당하고 패킷이 호출자에게 반환되기 전 4바이트 TFTP 헤더의 공간을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-342">This service allocates a UDP packet from the specified packet pool and makes room for the 4-byte TFTP header before the packet is returned to the caller.</span></span> <span data-ttu-id="0a52d-343">그런 다음, 호출자가 클라이언트 파일에 쓰기를 위한 버퍼를 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-343">The caller can then build a buffer for writing to a client file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-344">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-344">Input Parameters</span></span>

- <span data-ttu-id="0a52d-345">**pool_ptr** 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-345">**pool_ptr** Pointer to packet pool.</span></span>

- <span data-ttu-id="0a52d-346">**packet_ptr** 할당된 패킷에 대한 포인터의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-346">**packet_ptr** Destination for pointer to allocated packet.</span></span>

- <span data-ttu-id="0a52d-347">**wait_option** 패킷 할당이 완료될 때까지 서버가 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-347">**wait_option** Defines how long the service will wait for the packet allocate to complete.</span></span> <span data-ttu-id="0a52d-348">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-348">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0a52d-349">**시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0a52d-349">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="0a52d-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0a52d-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="0a52d-351">TX_WAIT_FOREVER를 선택하면 할당이 완료될 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-351">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the allocation completes.</span></span>

  <span data-ttu-id="0a52d-352">숫자 값(1-0xFFFFFFFE)을 선택하면 패킷 할당을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-352">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the packet allocation.</span></span>

- <span data-ttu-id="0a52d-353">**ip_type** 사용할 IP 주소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-353">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0a52d-354">유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-354">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-355">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-355">Return Values</span></span>

- <span data-ttu-id="0a52d-356">**NX_SUCCESS** (0x00) 패킷을 성공적으로 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-356">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>

- <span data-ttu-id="0a52d-357">NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-357">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0a52d-358">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="0a52d-358">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0a52d-359">NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력</span><span class="sxs-lookup"><span data-stu-id="0a52d-359">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-360">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-360">Allowed From</span></span>

<span data-ttu-id="0a52d-361">스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-361">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-362">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-362">Example</span></span>

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a><span data-ttu-id="0a52d-363">nxd_tftp_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="0a52d-363">nxd_tftp_client_set_interface</span></span>

<span data-ttu-id="0a52d-364">TFTP 요청에 대한 실제 인터페이스 설정</span><span class="sxs-lookup"><span data-stu-id="0a52d-364">Set physical interface for TFTP requests</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-365">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-365">Prototype</span></span>

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a><span data-ttu-id="0a52d-366">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-366">Description</span></span>

<span data-ttu-id="0a52d-367">이 서비스는 입력 인터페이스 인덱스를 사용하여 TFTP 클라이언트가 TFTP 패킷을 보내고 받을 실제 인터페이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-367">This service uses the input interface index to set the physical interface for the TFTP Client to send and receive TFTP packets.</span></span> <span data-ttu-id="0a52d-368">기본 인터페이스에 대한 기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-368">The default value is zero, for the primary interface.</span></span>

> [!NOTE]
> <span data-ttu-id="0a52d-369">이 서비스를 사용하려면 NetX Duo가 멀티홈 주소 지정(v5.6 이상)을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-369">NetX Duo must support multihome addressing (v5.6 or later) to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-370">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-370">Input Parameters</span></span>

- <span data-ttu-id="0a52d-371">**tftp_client_ptr** TFTP 클라이언트 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-371">**tftp_client_ptr** Pointer to TFTP Client instance</span></span>

- <span data-ttu-id="0a52d-372">**if_index** 사용할 실제 인터페이스의 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-372">**if_index** Index of physical interface to use</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-373">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-373">Return Values</span></span>

- <span data-ttu-id="0a52d-374">**NX_SUCCESS** (0x00) 인터페이스를 성공적으로 설정했습니다. (0x0B) 잘못된 인터페이스 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-374">**NX_SUCCESS** (0x00) Successfully set interface (0x0B) Invalid interface input</span></span>

- <span data-ttu-id="0a52d-375">NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-375">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0a52d-376">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="0a52d-376">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0a52d-377">NX_TFTP_INVALID_INTERFACE (0x0B) 잘못된 인터페이스 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-377">NX_TFTP_INVALID_INTERFACE (0x0B) Invalid interface input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-378">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-378">Allowed From</span></span>

<span data-ttu-id="0a52d-379">스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-380">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-380">Example</span></span>

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a><span data-ttu-id="0a52d-381">nxd_tftp_server_create</span><span class="sxs-lookup"><span data-stu-id="0a52d-381">nxd_tftp_server_create</span></span>

<span data-ttu-id="0a52d-382">TFTP 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="0a52d-382">Create TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-383">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-383">Prototype</span></span>

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="0a52d-384">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-384">Description</span></span>

<span data-ttu-id="0a52d-385">이 서비스는 포트 69로 TFTP 클라이언트 요청에 응답하는 TFTP 서버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-385">This service creates a TFTP Server that responds to TFTP Client requests on port 69.</span></span> <span data-ttu-id="0a52d-386">*nxd_tftp_server_start* 에 대한 후속 호출로 서버를 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-386">The Server must be started by a subsequent call to *nxd_tftp_server_start*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a52d-387">애플리케이션에서 제공된 IP 인스턴스, 패킷 풀 및 FileX 미디어 인스턴스가 이미 생성되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-387">The application must make certain the supplied IP instance, packet pool, and FileX media instance are already created.</span></span> <span data-ttu-id="0a52d-388">또한 이 서비스를 호출하기 전 IP 인스턴스에 대해 UDP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-388">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-389">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-389">Input Parameters</span></span>

- <span data-ttu-id="0a52d-390">**tftp_server_ptr** TFTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-390">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

- <span data-ttu-id="0a52d-391">**tftp_server_name** 이 TFTP 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-391">**tftp_server_name** Name of this TFTP Server instance</span></span>

- <span data-ttu-id="0a52d-392">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-392">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="0a52d-393">**media_ptr** FileX 미디어 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-393">**media_ptr** Pointer to FileX media instance.</span></span>

- <span data-ttu-id="0a52d-394">**stack_ptr** TFTP 서버 스택 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-394">**stack_ptr** Pointer to TFTP Server stack area.</span></span>

- <span data-ttu-id="0a52d-395">**stack_size** TFTP 서버 스택의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-395">**stack_size** Number of bytes in the TFTP Server stack.</span></span>

- <span data-ttu-id="0a52d-396">**pool_ptr** TFTP 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-396">**pool_ptr** Pointer to TFTP packet pool.</span></span> 

> [!NOTE]
> <span data-ttu-id="0a52d-397">제공된 풀에는 최소 580바이트 크기의 패킷 페이로드가 있어야 합니다.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a52d-397">The supplied pool must have packet payloads at least 580 bytes in size.<sup>1</sup></span></span>

<span data-ttu-id="0a52d-398"><sup>1</sup> 패킷의 데이터 부분이 정확히 512바이트이지만 패킷 페이로드 크기는 최소 572바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-398"><sup>1</sup> The data portion of a packet is exactly 512 bytes, but the packet payload size must be at least 572 bytes.</span></span> <span data-ttu-id="0a52d-399">나머지 바이트는 UDP, IPv6 및 이더넷 헤더와 정렬을 위해 드라이버에 필요한 잠재적인 후행 바이트에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-399">The remaining bytes are used for the UDP, IPv6, and Ethernet headers and potential trailing bytes required by the driver for alignment.</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-400">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-400">Return Values</span></span>

- <span data-ttu-id="0a52d-401">**NX_SUCCESS** (0x00) 서버를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-401">**NX_SUCCESS** (0x00) Successful Server create</span></span>

- <span data-ttu-id="0a52d-402">**NX_TFTP_POOL_ERROR** (0xC6) 패킷 풀의 패킷 크기가 560바이트 미만입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-402">**NX_TFTP_POOL_ERROR** (0xC6) Packet pool has packet size of less than 560 bytes</span></span>

- <span data-ttu-id="0a52d-403">NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-403">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-404">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-404">Allowed From</span></span>

<span data-ttu-id="0a52d-405">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-405">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-406">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-406">Example</span></span>

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a><span data-ttu-id="0a52d-407">nxd_tftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="0a52d-407">nxd_tftp_server_delete</span></span>

<span data-ttu-id="0a52d-408">TFTP 서버 삭제</span><span class="sxs-lookup"><span data-stu-id="0a52d-408">Delete TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-409">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-409">Prototype</span></span>

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0a52d-410">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-410">Description</span></span>

<span data-ttu-id="0a52d-411">이 서비스는 이전에 만든 TFTP 서버를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-411">This service deletes a previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-412">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-412">Input Parameters</span></span>

- <span data-ttu-id="0a52d-413">**tftp_server_ptr** TFTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-413">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-414">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-414">Return Values</span></span>

- <span data-ttu-id="0a52d-415">**NX_SUCCESS** (0x00) 서버를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-415">**NX_SUCCESS** (0x00) Successful Server delete</span></span>

- <span data-ttu-id="0a52d-416">NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-416">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0a52d-417">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="0a52d-417">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-418">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-418">Allowed From</span></span>

<span data-ttu-id="0a52d-419">스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-419">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-420">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-420">Example</span></span>

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a><span data-ttu-id="0a52d-421">nxd_tftp_server_start</span><span class="sxs-lookup"><span data-stu-id="0a52d-421">nxd_tftp_server_start</span></span>

<span data-ttu-id="0a52d-422">TFTP 서버 시작</span><span class="sxs-lookup"><span data-stu-id="0a52d-422">Start TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-423">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-423">Prototype</span></span>

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0a52d-424">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-424">Description</span></span>

<span data-ttu-id="0a52d-425">이 서비스는 이전에 만든 TFTP 서버를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-425">This service starts the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-426">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-426">Input Parameters</span></span>

- <span data-ttu-id="0a52d-427">**tftp_server_ptr** TFTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-427">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-428">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-428">Return Values</span></span>

- <span data-ttu-id="0a52d-429">**NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-429">**NX_SUCCESS** (0x00) Successful Server start</span></span>

- <span data-ttu-id="0a52d-430">NX_PTR_ERROR (0x16) 잘못된 포인터 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-430">NX_PTR_ERROR (0x16) Invalid pointer input .</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="0a52d-431">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-431">Allowed From</span></span>

<span data-ttu-id="0a52d-432">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-432">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-433">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-433">Example</span></span>

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a><span data-ttu-id="0a52d-434">nxd_tftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="0a52d-434">nxd_tftp_server_stop</span></span>

<span data-ttu-id="0a52d-435">TFTP 서버 중지</span><span class="sxs-lookup"><span data-stu-id="0a52d-435">Stop TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0a52d-436">프로토타입</span><span class="sxs-lookup"><span data-stu-id="0a52d-436">Prototype</span></span>

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0a52d-437">Description</span><span class="sxs-lookup"><span data-stu-id="0a52d-437">Description</span></span>

<span data-ttu-id="0a52d-438">이 서비스는 이전에 만든 TFTP 서버를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-438">This service stops the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0a52d-439">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a52d-439">Input Parameters</span></span>

- <span data-ttu-id="0a52d-440">**tftp_server_ptr** TFTP 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-440">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0a52d-441">반환 값</span><span class="sxs-lookup"><span data-stu-id="0a52d-441">Return Values</span></span>

- <span data-ttu-id="0a52d-442">**NX_SUCCESS** (0x00) 서버를 성공적으로 중지했습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-442">**NX_SUCCESS** (0x00) Successful Server stop</span></span>

- <span data-ttu-id="0a52d-443">NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a52d-443">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0a52d-444">NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자</span><span class="sxs-lookup"><span data-stu-id="0a52d-444">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0a52d-445">허용 위치</span><span class="sxs-lookup"><span data-stu-id="0a52d-445">Allowed From</span></span>

<span data-ttu-id="0a52d-446">스레드</span><span class="sxs-lookup"><span data-stu-id="0a52d-446">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0a52d-447">예제</span><span class="sxs-lookup"><span data-stu-id="0a52d-447">Example</span></span>

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```