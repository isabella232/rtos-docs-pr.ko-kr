---
title: 3장 - Azure RTOS NetX POP3 클라이언트 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX POP3 클라이언트 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1a0ab96a454bea9f56ced0d7aa8de5d481b284e9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811478"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a><span data-ttu-id="1c198-103">3장 - Azure RTOS NetX POP3 클라이언트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="1c198-103">Chapter 3 - Description of Azure RTOS NetX POP3 Client services</span></span>

<span data-ttu-id="1c198-104">이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX POP3 클라이언트 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-104">This chapter contains a description of all Azure RTOS NetX POP3 Client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="1c198-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="1c198-106">nx_pop3_client_create: *POP3 클라이언트 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="1c198-106">nx_pop3_client_create: *Create a POP3 Client Instance*</span></span>
- <span data-ttu-id="1c198-107">nx_pop3_client_delete: *POP3 클라이언트 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="1c198-107">nx_pop3_client_delete: *Delete a POP3 Client instance*</span></span>
- <span data-ttu-id="1c198-108">nx_pop3_client_ mail_item_get: *서버 maildrop에서 클라이언트 메일 항목 삭제*</span><span class="sxs-lookup"><span data-stu-id="1c198-108">nx_pop3_client_ mail_item_get: *Delete a Client mail item from Server maildrop*</span></span>
- <span data-ttu-id="1c198-109">nx_pop3_client_mail_item_get: *특정 메일 메시지 크기 검색*</span><span class="sxs-lookup"><span data-stu-id="1c198-109">nx_pop3_client_mail_item_get: *Retrieve a specific mail message size*</span></span>
- <span data-ttu-id="1c198-110">nx_pop3_client_mail_items_get: *maildrop의 메일 항목 수 가져오기*</span><span class="sxs-lookup"><span data-stu-id="1c198-110">nx_pop3_client_mail_items_get: *Obtain the number of mail items in maildrop*</span></span>
- <span data-ttu-id="1c198-111">nx_pop3_client_mail_item_message _get: *특정 메일 메시지 다운로드*</span><span class="sxs-lookup"><span data-stu-id="1c198-111">nx_pop3_client_mail_item_message _get: *Download a specific mail message*</span></span>
- <span data-ttu-id="1c198-112">nx_pop3_client_mail_item_size_get: *특정 메일 항목의 크기 가져오기*</span><span class="sxs-lookup"><span data-stu-id="1c198-112">nx_pop3_client_mail_item_size_get: *Obtain the size of a specific mail item*</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="1c198-113">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="1c198-113">nx_pop3_client_create</span></span>

<span data-ttu-id="1c198-114">POP3 클라이언트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="1c198-114">Create a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1c198-115">프로토타입</span><span class="sxs-lookup"><span data-stu-id="1c198-115">Prototype</span></span>

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="1c198-116">Description</span><span class="sxs-lookup"><span data-stu-id="1c198-116">Description</span></span>

<span data-ttu-id="1c198-117">이 서비스는 POP3 클라이언트의 인스턴스를 만들고 입력 매개 변수를 사용하여 해당 구성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-117">This service creates an instance of the POP3 Client and sets up its configuration with the input parameters.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1c198-118">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-118">Input Parameters</span></span>

- <span data-ttu-id="1c198-119">**client_ptr**: 만들 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-119">**client_ptr**: Pointer to Client to create</span></span>
- <span data-ttu-id="1c198-120">**APOP_authentication** APOP 인증 사용</span><span class="sxs-lookup"><span data-stu-id="1c198-120">**APOP_authentication**: Enable APOP authentication</span></span>
- <span data-ttu-id="1c198-121">**ip_ptr**: IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-121">**ip_ptr**: Pointer to IP instance</span></span>
- <span data-ttu-id="1c198-122">**packet_pool_ptr**: 클라이언트 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-122">**packet_pool_ptr**: Pointer to Client packet pool</span></span>
- <span data-ttu-id="1c198-123">**server_ip_address**: POP3 서버 주소</span><span class="sxs-lookup"><span data-stu-id="1c198-123">**server_ip_address**: POP3 server address</span></span>
- <span data-ttu-id="1c198-124">**server_port**: POP3 서버 포트</span><span class="sxs-lookup"><span data-stu-id="1c198-124">**server_port**: POP3 server port</span></span>
- <span data-ttu-id="1c198-125">**client_name**: 클라이언트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-125">**client_name**: Pointer to Client name</span></span>
- <span data-ttu-id="1c198-126">**client_password**: 클라이언트 암호에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-126">**client_password**: Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="1c198-127">반환 값</span><span class="sxs-lookup"><span data-stu-id="1c198-127">Return Values</span></span>

- <span data-ttu-id="1c198-128">**NX_SUCCESS**: (0x00) 클라이언트를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="1c198-128">**NX_SUCCESS**: (0x00) Client successfully created</span></span>
- <span data-ttu-id="1c198-129">**status**: NetX 및 ThreadX 서비스 호출의 상태 완료</span><span class="sxs-lookup"><span data-stu-id="1c198-129">**status**: Status completion of NetX and ThreadX service calls</span></span>
- <span data-ttu-id="1c198-130">NX_PTR_ERROR: (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-130">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="1c198-131">NX_POP3_PARAM_ERROR: (0xB1) 잘못된 포인터가 아닌 입력</span><span class="sxs-lookup"><span data-stu-id="1c198-131">NX_POP3_PARAM_ERROR: (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1c198-132">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="1c198-132">Allowed From</span></span>

<span data-ttu-id="1c198-133">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="1c198-133">Application code</span></span>

### <a name="example"></a><span data-ttu-id="1c198-134">예제</span><span class="sxs-lookup"><span data-stu-id="1c198-134">Example</span></span>

```c
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST                   "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD          "pass"
#define POP3_SERVER_ADDRESS         IP_ADDRESS(192,2,2,92
#define POP3_SERVER_PORT            110

/* Create a NetX POP3 Client instance. */
ULONG server_ip_address = IP_ADDRESS(1,2,3,4);
status = nx_pop3_client_create(&demo_client,
        NX_FALSE /* disable APOP authentication */,
        &client_ip, &client_packet_pool,
        server_ip_address, POP3_SERVER_PORT,
        LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="1c198-135">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="1c198-135">nx_pop3_client_delete</span></span>

<span data-ttu-id="1c198-136">POP3 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-136">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1c198-137">프로토타입</span><span class="sxs-lookup"><span data-stu-id="1c198-137">Prototype</span></span>

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a><span data-ttu-id="1c198-138">Description</span><span class="sxs-lookup"><span data-stu-id="1c198-138">Description</span></span>

<span data-ttu-id="1c198-139">이 서비스는 이전에 만든 POP3 클라이언트를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-139">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="1c198-140">이 서비스는 POP3 클라이언트 패킷 풀을 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-140">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="1c198-141">디바이스 애플리케이션은 더 이상 패킷 풀을 사용하지 않는 경우 이 리소스를 개별적으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-141">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1c198-142">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-142">Input Parameters</span></span>

- <span data-ttu-id="1c198-143">**client_ptr**: 삭제할 클라이언트에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-143">**client_ptr**: Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="1c198-144">반환 값</span><span class="sxs-lookup"><span data-stu-id="1c198-144">Return Values</span></span>

- <span data-ttu-id="1c198-145">**NX_SUCCESS**: (0x00) 클라이언트를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-145">**NX_SUCCESS**: (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="1c198-146">NX_PTR_ERROR: (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-146">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1c198-147">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="1c198-147">Allowed From</span></span>

<span data-ttu-id="1c198-148">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="1c198-148">Application code</span></span>

### <a name="example"></a><span data-ttu-id="1c198-149">예제</span><span class="sxs-lookup"><span data-stu-id="1c198-149">Example</span></span>

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="1c198-150">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="1c198-150">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="1c198-151">클라이언트 maildrop에서 지정된 메일 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-151">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="1c198-152">프로토타입</span><span class="sxs-lookup"><span data-stu-id="1c198-152">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a><span data-ttu-id="1c198-153">Description</span><span class="sxs-lookup"><span data-stu-id="1c198-153">Description</span></span>

<span data-ttu-id="1c198-154">이 서비스는 클라이언트 maildrop에서 지정된 메일 항목을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-154">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="1c198-155">이는 메일 항목을 다운로드한 후에 사용할 수 있지만 일부 POP3 서버는 클라이언트가 요청한 후에 메일 항목을 자동으로 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-155">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1c198-156">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-156">Input Parameters</span></span>

- <span data-ttu-id="1c198-157">**client_ptr**: 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-157">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="1c198-158">**mail_index**: 클라이언트 maildrop에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="1c198-158">**mail_index**: Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="1c198-159">반환 값</span><span class="sxs-lookup"><span data-stu-id="1c198-159">Return Values</span></span>

- <span data-ttu-id="1c198-160">**NX_SUCCESS**: (0x00) 삭제 요청 성공</span><span class="sxs-lookup"><span data-stu-id="1c198-160">**NX_SUCCESS**: (0x00) Delete request successful</span></span>
- <span data-ttu-id="1c198-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) 잘못된 메일 항목 인덱스</span><span class="sxs-lookup"><span data-stu-id="1c198-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="1c198-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) POP3 요청에 대한 클라이언트 패킷 페이로드가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="1c198-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) 서버가 오류 상태로 응답</span><span class="sxs-lookup"><span data-stu-id="1c198-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="1c198-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) 잘못된 메일 인덱스 입력</span><span class="sxs-lookup"><span data-stu-id="1c198-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="1c198-165">NX_PTR_ERROR: (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-165">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1c198-166">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="1c198-166">Allowed From</span></span>

<span data-ttu-id="1c198-167">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="1c198-167">Application code</span></span>

### <a name="example"></a><span data-ttu-id="1c198-168">예제</span><span class="sxs-lookup"><span data-stu-id="1c198-168">Example</span></span>

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="1c198-169">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="1c198-169">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="1c198-170">지정된 메일 항목 검색</span><span class="sxs-lookup"><span data-stu-id="1c198-170">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="1c198-171">프로토타입</span><span class="sxs-lookup"><span data-stu-id="1c198-171">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a><span data-ttu-id="1c198-172">Description</span><span class="sxs-lookup"><span data-stu-id="1c198-172">Description</span></span>

<span data-ttu-id="1c198-173">이 서비스는 mail_item 인덱스에 지정된 클라이언트 maildrop에서 메일 항목을 검색하는 RETR 요청을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-173">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="1c198-174">RETR 요청을 만들고 서버에서 긍정 응답을 받은 후 클라이언트는 *nx_pop3_client_mail_item_message_get* 서비스를 사용하여 메일 메시지 다운로드를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-174">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="1c198-175">또한 서비스는 서버 회신에서 추출된 요청된 메일 항목의 크기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-175">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1c198-176">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-176">Input Parameters</span></span>

- <span data-ttu-id="1c198-177">**client_ptr**: 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-177">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="1c198-178">**mail_item**: 클라이언트 maildrop에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="1c198-178">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="1c198-179">**item_size**: 메일 메시지의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-179">**item_size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="1c198-180">반환 값</span><span class="sxs-lookup"><span data-stu-id="1c198-180">Return Values</span></span>

- <span data-ttu-id="1c198-181">**NX_SUCCESS**: (0x00) 메일 항목을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="1c198-181">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="1c198-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) 잘못된 메일 항목 인덱스</span><span class="sxs-lookup"><span data-stu-id="1c198-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="1c198-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) POP3 요청에 대한 클라이언트 패킷 페이로드가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="1c198-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) 서버가 오류 상태로 응답</span><span class="sxs-lookup"><span data-stu-id="1c198-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="1c198-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) 잘못된 메일 인덱스 입력</span><span class="sxs-lookup"><span data-stu-id="1c198-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="1c198-186">NX_PTR_ERROR: (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-186">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1c198-187">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="1c198-187">Allowed From</span></span>

<span data-ttu-id="1c198-188">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="1c198-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="1c198-189">예제</span><span class="sxs-lookup"><span data-stu-id="1c198-189">Example</span></span>

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="1c198-190">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="1c198-190">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="1c198-191">maildrop의 메일 항목 수 검색</span><span class="sxs-lookup"><span data-stu-id="1c198-191">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="1c198-192">프로토타입</span><span class="sxs-lookup"><span data-stu-id="1c198-192">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a><span data-ttu-id="1c198-193">Description</span><span class="sxs-lookup"><span data-stu-id="1c198-193">Description</span></span>

<span data-ttu-id="1c198-194">이 서비스는 클라이언트 maildrop에서 메일 항목 수와 메일 메시지 데이터의 총 크기를 검색하는 STAT 요청을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-194">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1c198-195">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-195">Input Parameters</span></span>

- <span data-ttu-id="1c198-196">**client_ptr**: 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-196">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="1c198-197">**number_mail_item**: 클라이언트 maildrop의 메일 수</span><span class="sxs-lookup"><span data-stu-id="1c198-197">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="1c198-198">**maildrop_total_size**: 모든 메일 메시지의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-198">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="1c198-199">반환 값</span><span class="sxs-lookup"><span data-stu-id="1c198-199">Return Values</span></span>

- <span data-ttu-id="1c198-200">**NX_SUCCESS**: (0x00) 메일 항목을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="1c198-200">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="1c198-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) 잘못된 메일 항목 인덱스</span><span class="sxs-lookup"><span data-stu-id="1c198-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="1c198-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) POP3 요청에 대한 클라이언트 패킷 페이로드가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="1c198-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) 서버가 오류 상태로 응답</span><span class="sxs-lookup"><span data-stu-id="1c198-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span> 
- <span data-ttu-id="1c198-204">NX_PTR_ERROR: (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-204">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1c198-205">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="1c198-205">Allowed From</span></span>

<span data-ttu-id="1c198-206">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="1c198-206">Application code</span></span>

### <a name="example"></a><span data-ttu-id="1c198-207">예제</span><span class="sxs-lookup"><span data-stu-id="1c198-207">Example</span></span>

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="1c198-208">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="1c198-208">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="1c198-209">지정된 메일 항목 메시지 검색</span><span class="sxs-lookup"><span data-stu-id="1c198-209">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="1c198-210">프로토타입</span><span class="sxs-lookup"><span data-stu-id="1c198-210">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a><span data-ttu-id="1c198-211">Description</span><span class="sxs-lookup"><span data-stu-id="1c198-211">Description</span></span>

<span data-ttu-id="1c198-212">이 서비스는 메일 항목 메시지, 메일 메시지의 크기 및 메일 메시지의 마지막 패킷인지 여부를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-212">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="1c198-213">`final_packet`이 NX_TRUE인 경우가 `recv_packet_ptr`이 가리키는 패킷은 메일 항목 메시지의 최종 패킷입니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-213">If `final_packet` is NX_TRUE the packet pointed to by `recv_packet_ptr` is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1c198-214">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-214">Input Parameters</span></span>

- <span data-ttu-id="1c198-215">**client_ptr**: 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-215">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="1c198-216">**recv_packet_ptr**: 메시지 데이터의 받은 패킷</span><span class="sxs-lookup"><span data-stu-id="1c198-216">**recv_packet_ptr**: Received packet of message data</span></span>
- <span data-ttu-id="1c198-217">**number_mail_item**: 클라이언트 maildrop의 메일 수</span><span class="sxs-lookup"><span data-stu-id="1c198-217">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="1c198-218">**maildrop_total_size**: 모든 메일 메시지의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-218">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="1c198-219">반환 값</span><span class="sxs-lookup"><span data-stu-id="1c198-219">Return Values</span></span>

- <span data-ttu-id="1c198-220">**NX_SUCCESS**: (0x00) 메일 항목을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="1c198-220">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="1c198-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) POP3 요청에 대한 클라이언트 패킷 페이로드가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="1c198-222">NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-222">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1c198-223">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="1c198-223">Allowed From</span></span>

<span data-ttu-id="1c198-224">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="1c198-224">Application code</span></span>

### <a name="example"></a><span data-ttu-id="1c198-225">예제</span><span class="sxs-lookup"><span data-stu-id="1c198-225">Example</span></span>

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="1c198-226">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="1c198-226">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="1c198-227">지정된 메일 항목의 크기 검색</span><span class="sxs-lookup"><span data-stu-id="1c198-227">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="1c198-228">프로토타입</span><span class="sxs-lookup"><span data-stu-id="1c198-228">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a><span data-ttu-id="1c198-229">Description</span><span class="sxs-lookup"><span data-stu-id="1c198-229">Description</span></span>

<span data-ttu-id="1c198-230">이 서비스는 지정된 메일 항목의 크기를 가져오는 LIST 요청을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-230">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1c198-231">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-231">Input Parameters</span></span>

- <span data-ttu-id="1c198-232">**client_ptr**: 클라이언트 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-232">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="1c198-233">**mail_item**: 클라이언트 maildrop에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="1c198-233">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="1c198-234">**size**: 메일 메시지의 크기에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="1c198-234">**size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="1c198-235">반환 값</span><span class="sxs-lookup"><span data-stu-id="1c198-235">Return Values</span></span>

- <span data-ttu-id="1c198-236">**NX_SUCCESS**: (0x00) 메일 항목을 성공적으로 검색함</span><span class="sxs-lookup"><span data-stu-id="1c198-236">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="1c198-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) 잘못된 메일 항목 인덱스</span><span class="sxs-lookup"><span data-stu-id="1c198-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="1c198-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) POP3 요청에 대한 클라이언트 패킷 페이로드가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="1c198-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="1c198-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) 서버가 오류 상태로 응답</span><span class="sxs-lookup"><span data-stu-id="1c198-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="1c198-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) 잘못된 메일 인덱스 입력</span><span class="sxs-lookup"><span data-stu-id="1c198-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="1c198-241">NX_PTR_ERROR: (0x07) 잘못된 입력 포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="1c198-241">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1c198-242">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="1c198-242">Allowed From</span></span>

<span data-ttu-id="1c198-243">애플리케이션 코드</span><span class="sxs-lookup"><span data-stu-id="1c198-243">Application code</span></span>

### <a name="example"></a><span data-ttu-id="1c198-244">예제</span><span class="sxs-lookup"><span data-stu-id="1c198-244">Example</span></span>

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
