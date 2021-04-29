---
title: 3장 - Azure RTOS NetX Duo Telnet 서비스 설명
description: 이 장에서는 아래 알파벳 순서로 나열된 모든 Azure RTOS NetX Duo Telnet 서비스에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810530"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a><span data-ttu-id="edbfd-103">3장 - Azure RTOS NetX Duo Telnet 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="edbfd-103">Chapter 3 - Description of Azure RTOS NetX Duo Telnet services</span></span>

<span data-ttu-id="edbfd-104">이 장에서는 아래 알파벳 순서로 나열된 모든 Azure RTOS NetX Duo Telnet 서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-104">This chapter contains a description of all Azure RTOS NetX Duo Telnet Services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="edbfd-105">다음 API 설명의 “반환 값” 섹션에서 **굵게 표시** 된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않으며, 굵게 표시되지 않은 값은 완전히 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="edbfd-106">**nx_telnet_client_connect**: IPv4 주소를 사용하여 텔넷 클라이언트 연결</span><span class="sxs-lookup"><span data-stu-id="edbfd-106">**nx_telnet_client_connect**: *Connect a Telnet Client with IPv4 address*</span></span>
- <span data-ttu-id="edbfd-107">**nxd_telnet_client_connect**: IPv6 주소를 사용하여 IPv6 텔넷 클라이언트 연결</span><span class="sxs-lookup"><span data-stu-id="edbfd-107">**nxd_telnet_client_connect**: *Connect an IPv6 Telnet Client with IPv6 address*</span></span>
- <span data-ttu-id="edbfd-108">**nx_telnet_client_create**: 텔넷 클라이언트 만들기</span><span class="sxs-lookup"><span data-stu-id="edbfd-108">**nx_telnet_client_create**: *Create a Telnet Client*</span></span>
- <span data-ttu-id="edbfd-109">**nx_telnet_client_delete**: 텔넷 클라이언트 삭제</span><span class="sxs-lookup"><span data-stu-id="edbfd-109">**nx_telnet_client_delete**: *Delete a Telnet Client*</span></span>
- <span data-ttu-id="edbfd-110">**nx_telnet_client_disconnect**: 텔넷 클라이언트 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="edbfd-110">**nx_telnet_client_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="edbfd-111">**nx_telnet_client_packet_receive**: 텔넷 클라이언트를 통해 패킷 수신</span><span class="sxs-lookup"><span data-stu-id="edbfd-111">**nx_telnet_client_packet_receive**: *Receive packet via Telnet Client*</span></span>
- <span data-ttu-id="edbfd-112">**nx_telnet_client_packet_send**: 텔넷 클라이언트를 통해 패킷 전송</span><span class="sxs-lookup"><span data-stu-id="edbfd-112">**nx_telnet_client_packet_send**: *Send packet via Telnet Client*</span></span>
- <span data-ttu-id="edbfd-113">**nx_telnet_server_create**: 텔넷 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="edbfd-113">**nx_telnet_server_create**: *Create a Telnet Server*</span></span>
- <span data-ttu-id="edbfd-114">**nx_telnet_server_delete**: 텔넷 서버 삭제</span><span class="sxs-lookup"><span data-stu-id="edbfd-114">**nx_telnet_server_delete**: *Delete a Telnet Server*</span></span>
- <span data-ttu-id="edbfd-115">**nx_telnet_server_disconnect**: 텔넷 클라이언트 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="edbfd-115">**nx_telnet_server_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="edbfd-116">**nx_telnet_server_get_open_connection_count**: 열린 연결 수 검색</span><span class="sxs-lookup"><span data-stu-id="edbfd-116">**nx_telnet_server_get_open_connection_count**: *Retrieve the number of open connections*</span></span>
- <span data-ttu-id="edbfd-117">**nx_telnet_server_packet_send**: 클라이언트 연결을 통해 패킷 전송</span><span class="sxs-lookup"><span data-stu-id="edbfd-117">**nx_telnet_server_packet_send**: *Send packet through Client connection*</span></span>
- <span data-ttu-id="edbfd-118">**nx_telnet_server_packet_pool_set**: 패킷 풀을 텔넷 서버 패킷 풀로 설정</span><span class="sxs-lookup"><span data-stu-id="edbfd-118">**nx_telnet_server_packet_pool_set**: *Set packet pool as Telnet Server packet pool*</span></span>
- <span data-ttu-id="edbfd-119">**nx_telnet_server_start**: 텔넷 서버 시작</span><span class="sxs-lookup"><span data-stu-id="edbfd-119">**nx_telnet_server_start**: *Start a Telnet Server*</span></span>
- <span data-ttu-id="edbfd-120">**nx_telnet_server_stop**: 텔넷 서버 중지</span><span class="sxs-lookup"><span data-stu-id="edbfd-120">**nx_telnet_server_stop**: *Stop a Telnet Server*</span></span>

## <a name="nx_telnet_client_connect"></a><span data-ttu-id="edbfd-121">nx_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="edbfd-121">nx_telnet_client_connect</span></span>

<span data-ttu-id="edbfd-122">IPv4 주소를 사용하여 텔넷 클라이언트 연결</span><span class="sxs-lookup"><span data-stu-id="edbfd-122">Connect a Telnet Client with IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-123">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-123">Prototype</span></span>

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="edbfd-124">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-124">Description</span></span>

<span data-ttu-id="edbfd-125">이 서비스는 텔넷 서버의 IPv4 주소를 사용하여 이전에 만든 텔넷 클라이언트 인스턴스를 지정된 IP 및 포트의 서버에 연결하려 합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-125">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using an IPv4 address for the Telnet Server.</span></span> <span data-ttu-id="edbfd-126">이 서비스는 ULONG 서버 IP 주소를 NXD_ADDRESS 제어 블록에 삽입하고, 아래에 설명된 *nxd_telnet_client_connect* 서비스를 호출하기 전에 IP 버전을 4로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-126">This service actually inserts the ULONG server IP address in an NXD_ADDRESS control block and sets the IP version to 4 before calling the *nxd_telnet_client_connect* service described below.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-127">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-127">Input Parameters</span></span>

- <span data-ttu-id="edbfd-128">**client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-128">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="edbfd-129">**server_ip**: 텔넷 서버의 IPv4 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-129">**server_ip**: IPv4 Address of the Telnet Server.</span></span>
- <span data-ttu-id="edbfd-130">**server_port**: 서버의 TCP 포트입니다(텔넷 서버: 포트 23).</span><span class="sxs-lookup"><span data-stu-id="edbfd-130">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="edbfd-131">**wait_option**: 서비스에서 텔넷 클라이언트 연결을 대기할 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-131">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="edbfd-132">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-132">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="edbfd-133">**시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-133">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="edbfd-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF)Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-135">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-135">Return Values</span></span>

- <span data-ttu-id="edbfd-136">**NX_SUCCESS**: (0x00) 클라이언트를 성공적으로 연결했습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-136">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="edbfd-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) 클라이언트가 이미 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="edbfd-138">NX_PTR_ERROR: (0x07) 클라이언트 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-138">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="edbfd-139">NX_IP_ADDRESS_ERROR: (0x21) IP 주소가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-139">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="edbfd-140">NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-140">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-141">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-141">Allowed From</span></span>

<span data-ttu-id="edbfd-142">스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-142">Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-143">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-143">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a><span data-ttu-id="edbfd-144">nxd_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="edbfd-144">nxd_telnet_client_connect</span></span>

<span data-ttu-id="edbfd-145">IPv6 또는 IPv4 주소를 사용하여 텔넷 클라이언트 연결</span><span class="sxs-lookup"><span data-stu-id="edbfd-145">Connect a Telnet Client with IPv6 or IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-146">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-146">Prototype</span></span>

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="edbfd-147">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-147">Description</span></span>

<span data-ttu-id="edbfd-148">이 서비스는 텔넷 서버의 IPv6 주소를 사용하여 이전에 만든 텔넷 클라이언트 인스턴스를 지정된 IP 및 포트의 서버에 연결하려 합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-148">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using the Telnet Server’s IPv6 address.</span></span> <span data-ttu-id="edbfd-149">이 서비스는 IPv4 또는 IPv6 주소를 사용할 수 있지만 NXD_ADDRESS 변수 *server_ip_address* 에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-149">This service can take an IPv4 or an IPv6 address but must be contained in the NXD_ADDRESS variable *server_ip_address.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-150">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-150">Input Parameters</span></span>

- <span data-ttu-id="edbfd-151">**client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-151">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="edbfd-152">**server_ip_address**: 서버의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-152">**server_ip_address**: IP Address of Server.</span></span>
- <span data-ttu-id="edbfd-153">**server_port**: 서버의 TCP 포트입니다(텔넷 서버: 포트 23).</span><span class="sxs-lookup"><span data-stu-id="edbfd-153">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="edbfd-154">**wait_option**: 서비스에서 텔넷 클라이언트 연결을 대기할 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-154">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="edbfd-155">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-155">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="edbfd-156">**시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-156">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="edbfd-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-158">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-158">Return Values</span></span>

- <span data-ttu-id="edbfd-159">**NX_SUCCESS**: (0x00) 클라이언트를 성공적으로 연결했습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-159">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="edbfd-160">**NX_TELNET_ERROR**: (0xF0) 클라이언트 연결 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-160">**NX_TELNET_ERROR**: (0xF0) Client connect error.</span></span>
- <span data-ttu-id="edbfd-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) 클라이언트가 이미 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="edbfd-162">NX_PTR_ERROR: (0x07) 클라이언트 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-162">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="edbfd-163">NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-163">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="edbfd-164">NX_TELNET_INVALID_PARAMETER: (0xF5) 포인터가 아닌 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-164">NX_TELNET_INVALID_PARAMETER: (0xF5) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-165">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-165">Allowed From</span></span>

<span data-ttu-id="edbfd-166">스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-166">Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-167">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-167">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a><span data-ttu-id="edbfd-168">nx_telnet_client_create</span><span class="sxs-lookup"><span data-stu-id="edbfd-168">nx_telnet_client_create</span></span>

<span data-ttu-id="edbfd-169">텔넷 클라이언트 만들기</span><span class="sxs-lookup"><span data-stu-id="edbfd-169">Create a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-170">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-170">Prototype</span></span>

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="edbfd-171">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-171">Description</span></span>

<span data-ttu-id="edbfd-172">이 서비스는 텔넷 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-172">This service creates a Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-173">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-173">Input Parameters</span></span>

- <span data-ttu-id="edbfd-174">**client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-174">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="edbfd-175">**client_name**: 클라이언트 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-175">**client_name**: Name of Client instance.</span></span>
- <span data-ttu-id="edbfd-176">**ip_ptr**: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-176">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="edbfd-177">**window_size**: 이 클라이언트의 TCP 수신 창 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-177">**window_size**: Size of TCP receive window for this Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-178">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-178">Return Values</span></span>

- <span data-ttu-id="edbfd-179">**NX_SUCCESS**: (0x00) 클라이언트를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-179">**NX_SUCCESS**: (0x00) Successful Client create.</span></span>
- <span data-ttu-id="edbfd-180">**NX_TELNET_ERROR**: (0xF0) 소켓 만들기 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-180">**NX_TELNET_ERROR**: (0xF0) Socket create error.</span></span>
- <span data-ttu-id="edbfd-181">NX_PTR_ERROR: (0x07) 클라이언트 또는 IP 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-181">NX_PTR_ERROR: (0x07) Invalid Client or IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-182">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-182">Allowed From</span></span>

<span data-ttu-id="edbfd-183">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-183">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-184">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-184">Example</span></span>

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a><span data-ttu-id="edbfd-185">nx_telnet_client_delete</span><span class="sxs-lookup"><span data-stu-id="edbfd-185">nx_telnet_client_delete</span></span>

<span data-ttu-id="edbfd-186">텔넷 클라이언트 삭제</span><span class="sxs-lookup"><span data-stu-id="edbfd-186">Delete a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-187">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-187">Prototype</span></span>

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="edbfd-188">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-188">Description</span></span>

<span data-ttu-id="edbfd-189">이 서비스는 이전에 만든 텔넷 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-189">This service deletes a previously created Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-190">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-190">Input Parameters</span></span>

- <span data-ttu-id="edbfd-191">**client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-191">**client_ptr**: Pointer to Telnet Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-192">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-192">Return Values</span></span>

- <span data-ttu-id="edbfd-193">**NX_SUCCESS**: (0x00) 클라이언트를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-193">**NX_SUCCESS**: (0x00) Successful Client delete.</span></span>
- <span data-ttu-id="edbfd-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) 클라이언트가 아직 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client still connected.</span></span>
- <span data-ttu-id="edbfd-195">NX_PTR_ERROR: (0x07) 클라이언트 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-195">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="edbfd-196">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-196">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-197">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-197">Allowed From</span></span>

<span data-ttu-id="edbfd-198">스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-199">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-199">Example</span></span>

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a><span data-ttu-id="edbfd-200">nx_telnet_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="edbfd-200">nx_telnet_client_disconnect</span></span>

<span data-ttu-id="edbfd-201">텔넷 클라이언트 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="edbfd-201">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-202">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-202">Prototype</span></span>

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="edbfd-203">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-203">Description</span></span>

<span data-ttu-id="edbfd-204">이 서비스는 이전에 연결된 텔넷 클라이언트 인스턴스의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-204">This service disconnects a previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-205">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-205">Input Parameters</span></span>

- <span data-ttu-id="edbfd-206">**client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-206">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="edbfd-207">**wait_option**: 서비스에서 텔넷 클라이언트 연결을 끊을 때까지 대기할 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-207">**wait_option**: Defines how long the service will wait for the Telnet Client disconnect.</span></span> <span data-ttu-id="edbfd-208">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-208">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="edbfd-209">**시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-209">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="edbfd-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-211">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-211">Return Values</span></span>

- <span data-ttu-id="edbfd-212">**NX_SUCCESS**: (0x00) 클라이언트 연결을 성공적으로 끊었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-212">**NX_SUCCESS**: (0x00) Successful Client disconnect.</span></span>
- <span data-ttu-id="edbfd-213">**NX_TELNET_NOT_CONNECTED**: (0xF3) 클라이언트가 연결되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-213">**NX_TELNET_NOT_CONNECTED**: (0xF3) Client not connected.</span></span>
- <span data-ttu-id="edbfd-214">NX_PTR_ERROR: (0x07) 클라이언트 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-214">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="edbfd-215">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="edbfd-216">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-216">Allowed From</span></span>

<span data-ttu-id="edbfd-217">스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-218">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-218">Example</span></span>

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a><span data-ttu-id="edbfd-219">nx_telnet_client_packet_receive</span><span class="sxs-lookup"><span data-stu-id="edbfd-219">nx_telnet_client_packet_receive</span></span>

<span data-ttu-id="edbfd-220">텔넷 클라이언트를 통해 패킷 수신</span><span class="sxs-lookup"><span data-stu-id="edbfd-220">Receive packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-221">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-221">Prototype</span></span>

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="edbfd-222">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-222">Description</span></span>

<span data-ttu-id="edbfd-223">이 서비스는 이전에 연결된 텔넷 클라이언트 인스턴스에서 패킷을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-223">This service receives a packet from the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-224">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-224">Input Parameters</span></span>

- <span data-ttu-id="edbfd-225">**client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-225">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="edbfd-226">**packet_ptr**: 수신된 패킷의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-226">**packet_ptr**: Pointer to the destination for the received packet.</span></span>
- <span data-ttu-id="edbfd-227">**wait_option**: 서비스에서 텔넷 클라이언트 패킷 수신을 대기할 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-227">**wait_option**: Defines how long the service will wait for the Telnet Client packet receive.</span></span> <span data-ttu-id="edbfd-228">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-228">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="edbfd-229">**시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-229">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="edbfd-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-231">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-231">Return Values</span></span>

- <span data-ttu-id="edbfd-232">**NX_SUCCESS**: (0x00) 클라이언트 패킷을 성공적으로 수신했습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-232">**NX_SUCCESS**: (0x00) Successful Client packet receive.</span></span>
- <span data-ttu-id="edbfd-233">NX_PTR_ERROR: (0x07) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-233">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="edbfd-234">NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-234">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-235">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-235">Allowed From</span></span>

<span data-ttu-id="edbfd-236">스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-236">Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-237">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-237">Example</span></span>

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a><span data-ttu-id="edbfd-238">nx_telnet_client_packet_send</span><span class="sxs-lookup"><span data-stu-id="edbfd-238">nx_telnet_client_packet_send</span></span>

<span data-ttu-id="edbfd-239">텔넷 클라이언트를 통해 패킷 전송</span><span class="sxs-lookup"><span data-stu-id="edbfd-239">Send packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-240">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-240">Prototype</span></span>

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="edbfd-241">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-241">Description</span></span>

<span data-ttu-id="edbfd-242">이 서비스는 이전에 연결된 텔넷 클라이언트 인스턴스를 통해 패킷을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-242">This service sends a packet through the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-243">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-243">Input Parameters</span></span>

- <span data-ttu-id="edbfd-244">**client_ptr**: 텔넷 클라이언트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-244">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="edbfd-245">**packet_ptr**: 전송할 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-245">**packet_ptr**: Pointer to the packet to send.</span></span>
- <span data-ttu-id="edbfd-246">**wait_option**: 서비스에서 텔넷 클라이언트 패킷 전송을 대기할 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-246">**wait_option**: Defines how long the service will wait for the Telnet Client packet send.</span></span> <span data-ttu-id="edbfd-247">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="edbfd-248">**시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-248">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="edbfd-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-250">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-250">Return Values</span></span>

- <span data-ttu-id="edbfd-251">**NX_SUCCESS**: (0x00) 클라이언트 패킷을 성공적으로 전송했습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-251">**NX_SUCCESS**: (0x00) Successful Client packet send.</span></span>
- <span data-ttu-id="edbfd-252">**NX_TELNET_ERROR**: (0xF0) 패킷 전송 실패 - 호출자가 패킷을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-252">**NX_TELNET_ERROR**: (0xF0) Send packet failed – caller is responsible for releasing the packet.</span></span>
- <span data-ttu-id="edbfd-253">NX_PTR_ERROR: (0x07) 포인터 입력이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-253">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="edbfd-254">NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-254">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-255">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-255">Allowed From</span></span>

<span data-ttu-id="edbfd-256">스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-256">Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-257">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-257">Example</span></span>

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a><span data-ttu-id="edbfd-258">nx_telnet_server_create</span><span class="sxs-lookup"><span data-stu-id="edbfd-258">nx_telnet_server_create</span></span>

<span data-ttu-id="edbfd-259">텔넷 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="edbfd-259">Create a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-260">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-260">Prototype</span></span>

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a><span data-ttu-id="edbfd-261">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-261">Description</span></span>

<span data-ttu-id="edbfd-262">이 서비스는 지정된 IP 인스턴스에 텔넷 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-262">This service creates a Telnet Server instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-263">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-263">Input Parameters</span></span>

- <span data-ttu-id="edbfd-264">**server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-264">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="edbfd-265">**server_name**: 텔넷 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-265">**server_name**: Name of Telnet Server instance.</span></span>
- <span data-ttu-id="edbfd-266">**ip_ptr**: 연결된 IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-266">**ip_ptr**: Pointer to associated IP instance.</span></span>
- <span data-ttu-id="edbfd-267">**stack_ptr**: 내부 서버 스레드의 스택에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-267">**stack_ptr**: Pointer to stack for the internal Server thread.</span></span>
- <span data-ttu-id="edbfd-268">**sack_size**: 스택의 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-268">**sack_size**: Size of the stack, in bytes.</span></span>
- <span data-ttu-id="edbfd-269">**new_connection**: 애플리케이션 콜백 루틴 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-269">**new_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="edbfd-270">이 루틴은 서버가 새 텔넷 클라이언트 연결 요청을 검색할 때마다 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-270">This routine is called whenever a new Telnet Client connection request is detected by the Server.</span></span>
- <span data-ttu-id="edbfd-271">**receive_data**: 애플리케이션 콜백 루틴 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-271">**receive_data**: Application callback routine function pointer.</span></span> <span data-ttu-id="edbfd-272">이 루틴은 연결에 새 텔넷 클라이언트 데이터가 있을 때마다 호출되며</span><span class="sxs-lookup"><span data-stu-id="edbfd-272">This routine is called whenever a new Telnet Client data is present on the connection.</span></span> <span data-ttu-id="edbfd-273">패킷을 해제하는 역할을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-273">This routine is responsible for releasing the packet.</span></span>
- <span data-ttu-id="edbfd-274">**end_connection**: 애플리케이션 콜백 루틴 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-274">**end_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="edbfd-275">클라이언트에서 텔넷 클라이언트 연결을 끊거나 클라이언트 연결 시간이 초과할 때마다 이 루틴을 호출합니다(“작업 시간 초과” 만료).</span><span class="sxs-lookup"><span data-stu-id="edbfd-275">This routine is called whenever a Telnet Client connection is disconnected by the Client or the Client connection times out (“activity timeout” expires).</span></span> <span data-ttu-id="edbfd-276">서버는 아래에 설명된 *nx_telnet_server_disconnect* 서비스를 통해 연결을 끊을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-276">The Server can also disconnect via the *nx_telnet_server_disconnect* service described below.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-277">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-277">Return Values</span></span>

- <span data-ttu-id="edbfd-278">**NX_SUCCESS**: (0x00) 서버를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-278">**NX_SUCCESS**: (0x00) Successful Server create.</span></span>
- <span data-ttu-id="edbfd-279">NX_PTR_ERROR: (0x07) 서버, IP, 스택 또는 애플리케이션 콜백 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-279">NX_PTR_ERROR: (0x07) Invalid Server, IP, stack, or application callback pointers.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-280">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-280">Allowed From</span></span>

<span data-ttu-id="edbfd-281">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-281">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-282">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-282">Example</span></span>

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a><span data-ttu-id="edbfd-283">nx_telnet_server_delete</span><span class="sxs-lookup"><span data-stu-id="edbfd-283">nx_telnet_server_delete</span></span>

<span data-ttu-id="edbfd-284">텔넷 서버 삭제</span><span class="sxs-lookup"><span data-stu-id="edbfd-284">Delete a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-285">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-285">Prototype</span></span>

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="edbfd-286">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-286">Description</span></span>

<span data-ttu-id="edbfd-287">이 서비스는 이전에 만든 텔넷 서버 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-287">This service deletes a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-288">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-288">Input Parameters</span></span>

- <span data-ttu-id="edbfd-289">**server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-289">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-290">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-290">Return Values</span></span>

- <span data-ttu-id="edbfd-291">**NX_SUCCESS**: (0x00) 서버를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-291">**NX_SUCCESS**: (0x00) Successful Server delete.</span></span>
- <span data-ttu-id="edbfd-292">NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-292">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="edbfd-293">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-293">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-294">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-294">Allowed From</span></span>

<span data-ttu-id="edbfd-295">스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-295">Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-296">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-296">Example</span></span>

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a><span data-ttu-id="edbfd-297">nx_telnet_server_disconnect</span><span class="sxs-lookup"><span data-stu-id="edbfd-297">nx_telnet_server_disconnect</span></span>

<span data-ttu-id="edbfd-298">텔넷 클라이언트 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="edbfd-298">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-299">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-299">Prototype</span></span>

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a><span data-ttu-id="edbfd-300">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-300">Description</span></span>

<span data-ttu-id="edbfd-301">이 서비스는 해당 텔넷 서버 인스턴스에서 이전에 연결된 클라이언트 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-301">This service disconnects a previously connected Client on this Telnet Server instance.</span></span> <span data-ttu-id="edbfd-302">이 루틴은 일반적으로 수신된 데이터에서 검색된 조건에 응답하여 애플리케이션의 수신 데이터 콜백 함수에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-302">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-303">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-303">Input Parameters</span></span>

- <span data-ttu-id="edbfd-304">**server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-304">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="edbfd-305">**logical_connection**: 이 서버의 클라이언트 연결에 해당하는 논리적 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-305">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="edbfd-306">유효한 값 범위는 0에서 NX_TELENET_MAX_CLIENTS까지입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-306">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-307">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-307">Return Values</span></span>

- <span data-ttu-id="edbfd-308">**NX_SUCCESS**: (0x00) 서버 연결을 성공적으로 끊었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-308">**NX_SUCCESS**: (0x00) Successful Server disconnect.</span></span>
- <span data-ttu-id="edbfd-309">**NX_TELNET_ERROR**: (0xF0) 서버 연결을 끊지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-309">**NX_TELNET_ERROR**: (0xF0) Server disconnect failed.</span></span>
- <span data-ttu-id="edbfd-310">NX_OPTION_ERROR: (0x0A) 논리적 연결이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-310">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="edbfd-311">NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-311">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="edbfd-312">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-312">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-313">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-313">Allowed From</span></span>

<span data-ttu-id="edbfd-314">스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-314">Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-315">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-315">Example</span></span>

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a><span data-ttu-id="edbfd-316">nx_telnet_server_get_open_connection_count</span><span class="sxs-lookup"><span data-stu-id="edbfd-316">nx_telnet_server_get_open_connection_count</span></span>

<span data-ttu-id="edbfd-317">현재 열린 연결 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-317">Return number of currently open connections</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-318">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-318">Prototype</span></span>

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a><span data-ttu-id="edbfd-319">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-319">Description</span></span>

<span data-ttu-id="edbfd-320">이 서비스는 현재 연결된 텔넷 클라이언트의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-320">This service returns the number of currently connected Telnet Clients.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-321">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-321">Input Parameters</span></span>

- <span data-ttu-id="edbfd-322">**server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-322">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="edbfd-323">**Connection_count**: 연결 수를 저장할 메모리에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-323">**Connection_count**: Pointer to memory to store connection count</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-324">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-324">Return Values</span></span>

- <span data-ttu-id="edbfd-325">**NX_SUCCESS**: (0x00) 성공적으로 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-325">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="edbfd-326">NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-326">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="edbfd-327">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-327">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-328">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-328">Allowed From</span></span>

<span data-ttu-id="edbfd-329">스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-330">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-330">Example</span></span>

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a><span data-ttu-id="edbfd-331">nx_telnet_server_packet_send</span><span class="sxs-lookup"><span data-stu-id="edbfd-331">nx_telnet_server_packet_send</span></span>

<span data-ttu-id="edbfd-332">클라이언트 연결을 통해 패킷 전송</span><span class="sxs-lookup"><span data-stu-id="edbfd-332">Send packet through Client connection</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-333">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-333">Prototype</span></span>

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="edbfd-334">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-334">Description</span></span>

<span data-ttu-id="edbfd-335">이 서비스는 해당 텔넷 서버 인스턴스의 클라이언트 연결에 패킷을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-335">This service sends a packet to the Client connection on this Telnet Server instance.</span></span> <span data-ttu-id="edbfd-336">이 루틴은 일반적으로 수신된 데이터에서 검색된 조건에 응답하여 애플리케이션의 수신 데이터 콜백 함수에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-336">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-337">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-337">Input Parameters</span></span>

- <span data-ttu-id="edbfd-338">**server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-338">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="edbfd-339">**logical_connection**: 이 서버의 클라이언트 연결에 해당하는 논리적 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-339">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="edbfd-340">유효한 값 범위는 0에서 NX_TELENET_MAX_CLIENTS까지입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-340">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>
- <span data-ttu-id="edbfd-341">**packet_ptr**: 수신된 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-341">**packet_ptr**: Pointer to the received packet.</span></span>
- <span data-ttu-id="edbfd-342">**wait_option**: 서비스에서 텔넷 서버 패킷 전송을 대기할 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-342">**wait_option**: Defines how long the service will wait for the Telnet Server packet send.</span></span> <span data-ttu-id="edbfd-343">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-343">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="edbfd-344">**시간 제한 값**: (0x00000001~0xFFFFFFFE) 숫자 값(1~0xFFFFFFFE)을 선택하면 텔넷 서버 응답을 기다리는 동안 일시 중단 상태로 유지되는 최대 타이머 틱 수를 지정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-344">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="edbfd-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER를 선택하면 텔넷 서버가 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span> 

### <a name="return-values"></a><span data-ttu-id="edbfd-346">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-346">Return Values</span></span>

- <span data-ttu-id="edbfd-347">**NX_SUCCESS**: (0x00) 패킷을 성공적으로 전송했습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-347">**NX_SUCCESS**: (0x00) Successful packet send.</span></span>
- <span data-ttu-id="edbfd-348">**NX_TELNET_FAILED**: (0xF2) TCP 소켓을 전송하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-348">**NX_TELNET_FAILED**: (0xF2) TCP socket send failed.</span></span>
- <span data-ttu-id="edbfd-349">NX_OPTION_ERROR: (0x0A) 논리적 연결이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-349">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="edbfd-350">NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-350">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="edbfd-351">NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-351">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-352">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-352">Allowed From</span></span>

<span data-ttu-id="edbfd-353">스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-354">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-354">Example</span></span>

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a><span data-ttu-id="edbfd-355">nx_telnet_server_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="edbfd-355">nx_telnet_server_packet_pool_set</span></span>

<span data-ttu-id="edbfd-356">이전에 만든 패킷 풀을 텔넷 서버 풀로 설정</span><span class="sxs-lookup"><span data-stu-id="edbfd-356">Set previously created packet pool as Telnet Server pool</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-357">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-357">Prototype</span></span>

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a><span data-ttu-id="edbfd-358">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-358">Description</span></span>

<span data-ttu-id="edbfd-359">NX_TELNET_SERVER_USER_CREATE_PACKET_POOL이 정의된 경우 이 서비스는 이전에 만든 패킷 풀을 텔넷 서버 패킷 풀로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-359">This service sets a previously created packet pool as the Telnet Server packet pool if NX_TELNET_SERVER_USER_CREATE_PACKET_POOL is defined.</span></span> <span data-ttu-id="edbfd-360">또한 텔넷 서버가 텔넷 옵션을 텔넷 클라이언트로 전송하는 데 패킷 풀이 필요하도록 NX_TELNET_SERVER_OPTION_DISABLE을 정의하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-360">It also requires that NX_TELNET_SERVER_OPTION_DISABLE not be defined such that the Telnet Server needs a packet pool to transmit Telnet options to Telnet clients.</span></span>

<span data-ttu-id="edbfd-361">이렇게 하면 애플리케이션은 텔넷 서버 스택과 다른 메모리(예: 캐시가 없는 메모리)에 패킷 풀을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-361">This permits applications to create the packet pool in different memory e.g. no cache memory, than the Telnet Server stack.</span></span> <span data-ttu-id="edbfd-362">이 함수는 텔넷 서버 패킷 풀이 이미 설정되어 있는지 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-362">Note that if this function does not check if the Telnet Server packet pool is already set.</span></span> <span data-ttu-id="edbfd-363">null이 아닌 텔넷 서버 패킷 풀 포인터에서 호출되는 경우 이를 덮어쓰고 기존 패킷 풀을 입력 포인터가 가리키는 패킷 풀로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-363">If it is called on a non null Telnet Server packet pool pointer, it will overwrite it and replace the existing packet pool with packet pool pointed to by the input pointer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-364">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-364">Input Parameters</span></span>

- <span data-ttu-id="edbfd-365">**server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-365">**server_ptr**: Pointer to Telnet Server control block</span></span>
- <span data-ttu-id="edbfd-366">**packet_pool_ptr**: 이전에 만든 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-366">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-367">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-367">Return Values</span></span>

- <span data-ttu-id="edbfd-368">**NX_SUCCESS**: (0x00) 풀을 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-368">**NX_SUCCESS**: (0x00) Successfully set pool.</span></span>
- <span data-ttu-id="edbfd-369">NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-369">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-370">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-370">Allowed From</span></span>

<span data-ttu-id="edbfd-371">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-371">Init, Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-372">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-372">Example</span></span>

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a><span data-ttu-id="edbfd-373">nx_telnet_server_start</span><span class="sxs-lookup"><span data-stu-id="edbfd-373">nx_telnet_server_start</span></span>

<span data-ttu-id="edbfd-374">텔넷 서버 시작</span><span class="sxs-lookup"><span data-stu-id="edbfd-374">Start a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-375">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-375">Prototype</span></span>

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="edbfd-376">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-376">Description</span></span>

<span data-ttu-id="edbfd-377">이 서비스는 이전에 만든 텔넷 서버 인스턴스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-377">This service starts a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-378">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-378">Input Parameters</span></span>

- <span data-ttu-id="edbfd-379">**server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-379">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-380">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-380">Return Values</span></span>

- <span data-ttu-id="edbfd-381">**NX_SUCCESS**: (0x00) 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-381">**NX_SUCCESS**: (0x00) Successfully started.</span></span>
- <span data-ttu-id="edbfd-382">**NX_TELNET_NO_PACKET_POOL**: (0xF6) 패킷 풀이 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-382">**NX_TELNET_NO_PACKET_POOL**: (0xF6) No packet pool set</span></span>
- <span data-ttu-id="edbfd-383">NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-383">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-384">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-384">Allowed From</span></span>

<span data-ttu-id="edbfd-385">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-385">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-386">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-386">Example</span></span>

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a><span data-ttu-id="edbfd-387">nx_telnet_server_stop</span><span class="sxs-lookup"><span data-stu-id="edbfd-387">nx_telnet_server_stop</span></span>

<span data-ttu-id="edbfd-388">텔넷 서버 중지</span><span class="sxs-lookup"><span data-stu-id="edbfd-388">Stop a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="edbfd-389">프로토타입</span><span class="sxs-lookup"><span data-stu-id="edbfd-389">Prototype</span></span>

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="edbfd-390">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-390">Description</span></span>

<span data-ttu-id="edbfd-391">이 서비스는 이전에 만들어 시작한 텔넷 서버 인스턴스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-391">This service stops a previously created and started Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="edbfd-392">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="edbfd-392">Input Parameters</span></span>

- <span data-ttu-id="edbfd-393">**server_ptr**: 텔넷 서버 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-393">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="edbfd-394">반환 값</span><span class="sxs-lookup"><span data-stu-id="edbfd-394">Return Values</span></span>

- <span data-ttu-id="edbfd-395">**NX_SUCCESS**: (0x00) 성공적으로 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-395">**NX_SUCCESS**: (0x00) Successfully stopped</span></span>
- <span data-ttu-id="edbfd-396">NX_PTR_ERROR: (0x07) 서버 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-396">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="edbfd-397">NX_CALLER_ERROR: (0x11) 서비스 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="edbfd-397">NX_CALLER_ERROR: (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="edbfd-398">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="edbfd-398">Allowed From</span></span>

<span data-ttu-id="edbfd-399">스레드</span><span class="sxs-lookup"><span data-stu-id="edbfd-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="edbfd-400">예제</span><span class="sxs-lookup"><span data-stu-id="edbfd-400">Example</span></span>

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```