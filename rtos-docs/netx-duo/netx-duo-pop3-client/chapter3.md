---
title: 3장 - POP3 클라이언트 서비스 설명
description: 이 장에서는 아래에 나열된 모든 NetX Duo POP3 클라이언트 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f7681c8f3fe161db8a37a82574ab7d5e9bf348e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810657"
---
# <a name="chapter-3---description-of-pop3-client-services"></a><span data-ttu-id="5ac44-103">3장 - POP3 클라이언트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="5ac44-103">Chapter 3 - Description of POP3 Client Services</span></span>

<span data-ttu-id="5ac44-104">이 장에서는 아래에 나열된 모든 NetX Duo POP3 클라이언트 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-104">This chapter contains a description of all NetX Duo POP3 Client services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="5ac44-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="5ac44-106">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="5ac44-106">nx_pop3_client_create</span></span>

<span data-ttu-id="5ac44-107">IPv4에 대한 POP3 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="5ac44-107">Create a POP3 Client instance for IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="5ac44-108">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ac44-108">Prototype</span></span>

```C
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address, ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="5ac44-109">Description</span><span class="sxs-lookup"><span data-stu-id="5ac44-109">Description</span></span>

<span data-ttu-id="5ac44-110">이 서비스는 POP3 클라이언트의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-110">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="5ac44-111">IPv4 POP3 서버 주소만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-111">It supports only IPv4 POP3 server addresses.</span></span>

<span data-ttu-id="5ac44-112">먼저 디바이스 애플리케이션에서 패킷을 전송하기 위해 POP3 클라이언트에 대한 IP 인스턴스 및 패킷 풀을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-112">Note that the device application must first create an IP instance and a packet pool for the POP3 Client to transmit packets.</span></span> <span data-ttu-id="5ac44-113">이 패킷 풀은 POP3 클라이언트 작업에서 단독으로 사용하거나 IP 인스턴스를 만들 때 사용되는 것과 동일한 패킷 풀을 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-113">This packet pool created for use exclusively by the POP3 Client task or the same packet pool used in the IP instance creation.</span></span> <span data-ttu-id="5ac44-114">패킷 풀은 이더넷 드라이버 패킷 풀과 공유될 수도 있지만 이 경우에는 POP3 클라이언트가 비교적 작은 POP3 메시지 패킷을 서버에 보내기 위해 페이로드가 잠재적으로 많은 패킷 페이로드를 수신하기 위한 페이로드가 있는 대량 패킷 풀을 사용할 때의 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-114">The packet pool may also be shared with the Ethernet driver packet pool but this has the disadvantage of using large packet pools whose payload is intended for receiving potentially large packets payload for the POP3 Client to send relatively small POP3 message packets to the server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ac44-115">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-115">Input Parameters</span></span>

- <span data-ttu-id="5ac44-116">**client_ptr** 만들 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-116">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="5ac44-117">**APOP_authentication** APOP 인증 사용</span><span class="sxs-lookup"><span data-stu-id="5ac44-117">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="5ac44-118">**ip_ptr** IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-118">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="5ac44-119">**packet_pool_ptr** 클라이언트 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-119">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="5ac44-120">**server_ip_address** POP3 서버 IPv4 주소</span><span class="sxs-lookup"><span data-stu-id="5ac44-120">**server_ip_address** POP3 server IPv4 address</span></span>
- <span data-ttu-id="5ac44-121">**server_port** POP3 서버 포트</span><span class="sxs-lookup"><span data-stu-id="5ac44-121">**server_port** POP3 server port</span></span>
- <span data-ttu-id="5ac44-122">**client_name** 클라이언트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-122">**client_name** Pointer to Client name</span></span>
- <span data-ttu-id="5ac44-123">**client_password** 클라이언트 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-123">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="5ac44-124">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ac44-124">Return Values</span></span>

- <span data-ttu-id="5ac44-125">**NX_SUCCESS** (0x00) 클라이언트를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="5ac44-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="5ac44-126">**status** NetX Duo 및 ThreadX 서비스 호출의 상태 완료</span><span class="sxs-lookup"><span data-stu-id="5ac44-126">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="5ac44-127">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-127">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="5ac44-128">NX_POP3_PARAM_ERROR (0xB1) 잘못된 포인터가 아닌 입력</span><span class="sxs-lookup"><span data-stu-id="5ac44-128">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ac44-129">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5ac44-129">Allowed From</span></span>

<span data-ttu-id="5ac44-130">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="5ac44-130">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5ac44-131">예제</span><span class="sxs-lookup"><span data-stu-id="5ac44-131">Example</span></span>

```C
/* Create the POP3 Client. Note that the Client uses its password for its APOP shared
    secret. */

/* Set up user defined callback services. */
/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_ADDRESS IP_ADDRESS(192,2,2,92)
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. */
status = nx_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    POP3_SERVER_ADDRESS, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nxd_pop3_client_create"></a><span data-ttu-id="5ac44-132">nxd_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="5ac44-132">nxd_pop3_client_create</span></span>

<span data-ttu-id="5ac44-133">IPv4 또는 IPv6에 대한 POP3 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="5ac44-133">Create a POP3 Client instance for IPv4 or IPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="5ac44-134">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ac44-134">Prototype</span></span>

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address,
    ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="5ac44-135">Description</span><span class="sxs-lookup"><span data-stu-id="5ac44-135">Description</span></span>

<span data-ttu-id="5ac44-136">이 서비스는 POP3 클라이언트의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-136">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="5ac44-137">IPv4 및 IPv6 POP3 서버 주소를 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-137">It supports both IPv4 and IPv6 POP3 server addresses.</span></span> <span data-ttu-id="5ac44-138">POP3 클라이언트 만들기 프로세스에 대한 자세한 내용은 앞에서 설명한 *nx_pop3_client_create* 서비스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ac44-138">See the previously described *nx_pop3_client_create* service for more details on POP3 Client create process.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ac44-139">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-139">Input Parameters</span></span>

- <span data-ttu-id="5ac44-140">**client_ptr** 만들 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-140">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="5ac44-141">**APOP_authentication** APOP 인증 사용</span><span class="sxs-lookup"><span data-stu-id="5ac44-141">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="5ac44-142">**ip_ptr** IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-142">**ip_ptr** Pointer to IP instance</span></span>
- <span data-ttu-id="5ac44-143">**packet_pool_ptr** 클라이언트 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-143">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="5ac44-144">**server_ip_address** POP3 서버 IPv6 또는 IPv4 주소</span><span class="sxs-lookup"><span data-stu-id="5ac44-144">**server_ip_address** POP3 server IPv6 or IPv4 address</span></span>
- <span data-ttu-id="5ac44-145">**server_port** POP3 서버 포트</span><span class="sxs-lookup"><span data-stu-id="5ac44-145">**server_port** POP3 server port</span></span>
- <span data-ttu-id="5ac44-146">**client_name** 클라이언트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-146">**client_name**  Pointer to Client name</span></span>
- <span data-ttu-id="5ac44-147">**client_password** 클라이언트 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-147">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="5ac44-148">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ac44-148">Return Values</span></span>

- <span data-ttu-id="5ac44-149">**NX_SUCCESS** (0x00) 클라이언트를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="5ac44-149">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="5ac44-150">**status** NetX Duo 및 ThreadX 서비스 호출의 상태 완료</span><span class="sxs-lookup"><span data-stu-id="5ac44-150">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="5ac44-151">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-151">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="5ac44-152">NX_POP3_PARAM_ERROR (0xB1) 잘못된 포인터가 아닌 입력</span><span class="sxs-lookup"><span data-stu-id="5ac44-152">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ac44-153">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5ac44-153">Allowed From</span></span>

<span data-ttu-id="5ac44-154">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="5ac44-154">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5ac44-155">예제</span><span class="sxs-lookup"><span data-stu-id="5ac44-155">Example</span></span>

```C
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. Also note the details of IPv6 address validation
    and enabling IPv6 and ICMPv6 services on the IP task are not shown here. See the
    NetX Duo User Guide for more details on this process.
*/
NXD_ADDRESS server_ip_address;

/* Set client IP interface address. */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0xf101;
server_ip_address.nxd_ip_address.v6[2] = 0;
server_ip_address.nxd_ip_address.v6[3] = 0x101;
status = nxd_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    &server_ip_address, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="5ac44-156">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="5ac44-156">nx_pop3_client_delete</span></span>

<span data-ttu-id="5ac44-157">POP3 클라이언트 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="5ac44-157">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5ac44-158">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ac44-158">Prototype</span></span>

```C
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="5ac44-159">Description</span><span class="sxs-lookup"><span data-stu-id="5ac44-159">Description</span></span>

<span data-ttu-id="5ac44-160">이 서비스는 이전에 만든 POP3 클라이언트를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-160">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="5ac44-161">이 서비스는 POP3 클라이언트 패킷 풀을 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-161">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="5ac44-162">디바이스 애플리케이션은 더 이상 패킷 풀을 사용하지 않는 경우 이 리소스를 개별적으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-162">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ac44-163">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-163">Input Parameters</span></span>

- <span data-ttu-id="5ac44-164">**client_ptr** 삭제할 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-164">**client_ptr** Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="5ac44-165">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ac44-165">Return Values</span></span>

- <span data-ttu-id="5ac44-166">**NX_SUCCESS** (0x00) 클라이언트를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="5ac44-166">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="5ac44-167">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-167">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ac44-168">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5ac44-168">Allowed From</span></span>

<span data-ttu-id="5ac44-169">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="5ac44-169">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5ac44-170">예제</span><span class="sxs-lookup"><span data-stu-id="5ac44-170">Example</span></span>

```C
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="5ac44-171">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="5ac44-171">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="5ac44-172">클라이언트 maildrop에서 지정된 메일 항목 삭제</span><span class="sxs-lookup"><span data-stu-id="5ac44-172">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="5ac44-173">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ac44-173">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
    UINT mail_index);
```

### <a name="description"></a><span data-ttu-id="5ac44-174">Description</span><span class="sxs-lookup"><span data-stu-id="5ac44-174">Description</span></span>

<span data-ttu-id="5ac44-175">이 서비스는 클라이언트 maildrop에서 지정된 메일 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-175">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="5ac44-176">이는 메일 항목을 다운로드한 후에 사용할 수 있지만 일부 POP3 서버는 클라이언트가 요청한 후에 메일 항목을 자동으로 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-176">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ac44-177">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-177">Input Parameters</span></span>

- <span data-ttu-id="5ac44-178">**client_ptr** 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-178">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="5ac44-179">**mail_index** 클라이언트 maildrop에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="5ac44-179">**mail_index** Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="5ac44-180">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ac44-180">Return Values</span></span>

- <span data-ttu-id="5ac44-181">**NX_SUCCESS** (0x00) 삭제 요청 성공</span><span class="sxs-lookup"><span data-stu-id="5ac44-181">**NX_SUCCESS** (0x00) Delete request successful</span></span>
- <span data-ttu-id="5ac44-182">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) 잘못된 메일 항목 인덱스</span><span class="sxs-lookup"><span data-stu-id="5ac44-182">**NX_POP3_INVALID_MAIL_ITEM**(0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="5ac44-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) POP3 요청에 대한 클라이언트 패킷 페이로드가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="5ac44-184">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) 서버가 오류 상태로 응답</span><span class="sxs-lookup"><span data-stu-id="5ac44-184">**NX_POP3_SERVER_ERROR_STATUS**(0xB4) Server replies with error status</span></span>
- <span data-ttu-id="5ac44-185">NX_POP3_CLIENT_INVALID_INDEX (0xB8) 잘못된 메일 인덱스 입력</span><span class="sxs-lookup"><span data-stu-id="5ac44-185">NX_POP3_CLIENT_INVALID_INDEX(0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="5ac44-186">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-186">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ac44-187">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5ac44-187">Allowed From</span></span>

<span data-ttu-id="5ac44-188">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="5ac44-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5ac44-189">예제</span><span class="sxs-lookup"><span data-stu-id="5ac44-189">Example</span></span>

```C
ULONG item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status =
    NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="5ac44-190">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="5ac44-190">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="5ac44-191">지정된 메일 항목 검색</span><span class="sxs-lookup"><span data-stu-id="5ac44-191">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="5ac44-192">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ac44-192">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

### <a name="description"></a><span data-ttu-id="5ac44-193">Description</span><span class="sxs-lookup"><span data-stu-id="5ac44-193">Description</span></span>

<span data-ttu-id="5ac44-194">이 서비스는 mail_item 인덱스에 지정된 클라이언트 maildrop에서 메일 항목을 검색하는 RETR 요청을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-194">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="5ac44-195">RETR 요청을 만들고 서버에서 긍정 응답을 받은 후 클라이언트는 *nx_pop3_client_mail_item_message_get* 서비스를 사용하여 메일 메시지 다운로드를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-195">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="5ac44-196">또한 서비스는 서버 회신에서 추출된 요청된 메일 항목의 크기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-196">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ac44-197">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-197">Input Parameters</span></span>

- <span data-ttu-id="5ac44-198">**client_ptr** 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-198">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="5ac44-199">**mail_item** 클라이언트 maildrop에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="5ac44-199">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="5ac44-200">**item_size** 메일 메시지의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-200">**item_size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="5ac44-201">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ac44-201">Return Values</span></span>

- <span data-ttu-id="5ac44-202">**NX_SUCCESS** (0x00) 메일 항목을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="5ac44-202">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="5ac44-203">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) 잘못된 메일 항목 인덱스</span><span class="sxs-lookup"><span data-stu-id="5ac44-203">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="5ac44-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) POP3 요청에 대한 클라이언트 패킷 페이로드가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="5ac44-205">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) 서버가 오류 상태로 응답</span><span class="sxs-lookup"><span data-stu-id="5ac44-205">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="5ac44-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) 잘못된 메일 인덱스 입력</span><span class="sxs-lookup"><span data-stu-id="5ac44-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="5ac44-207">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-207">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ac44-208">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5ac44-208">Allowed From</span></span>

<span data-ttu-id="5ac44-209">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="5ac44-209">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5ac44-210">예제</span><span class="sxs-lookup"><span data-stu-id="5ac44-210">Example</span></span>

```C
ULONG item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="5ac44-211">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="5ac44-211">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="5ac44-212">maildrop의 메일 항목 수 검색</span><span class="sxs-lookup"><span data-stu-id="5ac44-212">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="5ac44-213">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ac44-213">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items,
    ULONG *maildrop_total_size);
```

### <a name="description"></a><span data-ttu-id="5ac44-214">Description</span><span class="sxs-lookup"><span data-stu-id="5ac44-214">Description</span></span>

<span data-ttu-id="5ac44-215">이 서비스는 클라이언트 maildrop에서 메일 항목 수와 메일 메시지 데이터의 총 크기를 검색하는 STAT 요청을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-215">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ac44-216">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-216">Input Parameters</span></span>

- <span data-ttu-id="5ac44-217">**client_ptr** 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-217">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="5ac44-218">**number_mail_item** 클라이언트 maildrop의 메일 수</span><span class="sxs-lookup"><span data-stu-id="5ac44-218">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="5ac44-219">**maildrop_total_size** 모든 메일 메시지의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-219">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="5ac44-220">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ac44-220">Return Values</span></span>

- <span data-ttu-id="5ac44-221">**NX_SUCCESS** (0x00) 메일 항목을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="5ac44-221">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="5ac44-222">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) 잘못된 메일 항목 인덱스</span><span class="sxs-lookup"><span data-stu-id="5ac44-222">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="5ac44-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) POP3 요청에 대한 클라이언트 패킷 페이로드가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="5ac44-224">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) 서버가 오류 상태로 응답</span><span class="sxs-lookup"><span data-stu-id="5ac44-224">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="5ac44-225">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-225">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ac44-226">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5ac44-226">Allowed From</span></span>

<span data-ttu-id="5ac44-227">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="5ac44-227">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5ac44-228">예제</span><span class="sxs-lookup"><span data-stu-id="5ac44-228">Example</span></span>

```C
UINT number_mail_items;

ULONG maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
    &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="5ac44-229">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="5ac44-229">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="5ac44-230">지정된 메일 항목 메시지 검색</span><span class="sxs-lookup"><span data-stu-id="5ac44-230">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="5ac44-231">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ac44-231">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

### <a name="description"></a><span data-ttu-id="5ac44-232">Description</span><span class="sxs-lookup"><span data-stu-id="5ac44-232">Description</span></span>

<span data-ttu-id="5ac44-233">이 서비스는 메일 항목 메시지, 메일 메시지의 크기 및 메일 메시지의 마지막 패킷인지 여부를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-233">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="5ac44-234">final_packet이 NX_TRUE인 경우 recv_packet_ptr가 가리키는 패킷이 메일 항목 메시지의 최종 패킷입니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-234">If final_packet is NX_TRUE the packet pointed to by recv_packet_ptr is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ac44-235">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-235">Input Parameters</span></span>

- <span data-ttu-id="5ac44-236">**client_ptr** 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-236">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="5ac44-237">**recv_packet_ptr** 메시지 데이터의 받은 패킷</span><span class="sxs-lookup"><span data-stu-id="5ac44-237">**recv_packet_ptr** Received packet of message data</span></span>
- <span data-ttu-id="5ac44-238">**number_mail_item** 클라이언트 maildrop의 메일 수</span><span class="sxs-lookup"><span data-stu-id="5ac44-238">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="5ac44-239">**maildrop_total_size** 모든 메일 메시지의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-239">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="5ac44-240">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ac44-240">Return Values</span></span>

- <span data-ttu-id="5ac44-241">**NX_SUCCESS** (0x00) 메일 항목을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="5ac44-241">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="5ac44-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) POP3 요청에 대한 클라이언트 패킷 페이로드가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="5ac44-243">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-243">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ac44-244">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5ac44-244">Allowed From</span></span>

<span data-ttu-id="5ac44-245">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="5ac44-245">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5ac44-246">예제</span><span class="sxs-lookup"><span data-stu-id="5ac44-246">Example</span></span>

```C
NX_PACKET *recv_packet_ptr;

ULONG bytes_retrieved;

UINT final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
    bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="5ac44-247">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="5ac44-247">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="5ac44-248">지정된 메일 항목의 크기 검색</span><span class="sxs-lookup"><span data-stu-id="5ac44-248">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="5ac44-249">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5ac44-249">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_size_get(
    NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *size);
```

### <a name="description"></a><span data-ttu-id="5ac44-250">Description</span><span class="sxs-lookup"><span data-stu-id="5ac44-250">Description</span></span>

<span data-ttu-id="5ac44-251">이 서비스는 지정된 메일 항목의 크기를 가져오는 LIST 요청을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-251">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5ac44-252">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-252">Input Parameters</span></span>

- <span data-ttu-id="5ac44-253">**client_ptr** 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-253">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="5ac44-254">**mail_item** 클라이언트 maildrop에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="5ac44-254">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="5ac44-255">**size** 메일 메시지의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="5ac44-255">**size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="5ac44-256">반환 값</span><span class="sxs-lookup"><span data-stu-id="5ac44-256">Return Values</span></span>

- <span data-ttu-id="5ac44-257">**NX_SUCCESS** (0x00) 메일 항목을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="5ac44-257">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="5ac44-258">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) 잘못된 메일 항목 인덱스</span><span class="sxs-lookup"><span data-stu-id="5ac44-258">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="5ac44-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) POP3 요청에 대한 클라이언트 패킷 페이로드가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac44-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="5ac44-260">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) 서버가 오류 상태로 응답</span><span class="sxs-lookup"><span data-stu-id="5ac44-260">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="5ac44-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) 잘못된 메일 인덱스 입력</span><span class="sxs-lookup"><span data-stu-id="5ac44-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="5ac44-262">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5ac44-262">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ac44-263">허용 위치</span><span class="sxs-lookup"><span data-stu-id="5ac44-263">Allowed From</span></span>

<span data-ttu-id="5ac44-264">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="5ac44-264">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5ac44-265">예제</span><span class="sxs-lookup"><span data-stu-id="5ac44-265">Example</span></span>

```C
ULONG size;

UINT mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
