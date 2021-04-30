---
title: 3장 - Azure RTOS NetX PPP(지점 간 프로토콜) 서비스 설명
description: 이 장에서는 아래에 나열된 모든 Azure RTOS NetX PPP 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f24d7366d27a8223b069a54ef7b93f6b3e38bf3a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811467"
---
# <a name="chapter-3---description-of-azure-rtos-netx-point-to-point-protocol-ppp-services"></a><span data-ttu-id="3cbb8-103">3장 - Azure RTOS NetX PPP(지점 간 프로토콜) 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="3cbb8-103">Chapter 3 - Description of Azure RTOS NetX Point-to-Point Protocol (PPP) services</span></span>

<span data-ttu-id="3cbb8-104">이 장에서는 아래에 나열된 모든 Azure RTOS NetX PPP 서비스에 대해 알파벳 순서로 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-104">This chapter contains a description of all Azure RTOS NetX PPP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="3cbb8-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="3cbb8-106">**nx_ppp_byte_receive**: *직렬 ISR에서 바이트 수신*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-106">**nx_ppp_byte_receive**: *Receive a byte from serial ISR*</span></span>
- <span data-ttu-id="3cbb8-107">**nx_ppp_chap_challenge**: *CHAP 챌린지 생성*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-107">**nx_ppp_chap_challenge**: *Generate a CHAP challenge*</span></span>
- <span data-ttu-id="3cbb8-108">**nx_ppp_chap_enable**: *CHAP 인증 사용*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-108">**nx_ppp_chap_enable**: *Enable CHAP authentication*</span></span>
- <span data-ttu-id="3cbb8-109">**nx_ppp_create**: *PPP 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-109">**nx_ppp_create**: *Create a PPP instance*</span></span>
- <span data-ttu-id="3cbb8-110">**nx_ppp_delete**: *PPP 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-110">**nx_ppp_delete**: *Delete a PPP instance*</span></span>
- <span data-ttu-id="3cbb8-111">**nx_ppp_dns_address_get**: *DNS IP 주소 가져오기*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-111">**nx_ppp_dns_address_get**: *Get DNS IP address*</span></span>
- <span data-ttu-id="3cbb8-112">**nx_ppp_dns_address_set**: *DNS 서버 IP 주소 설정*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-112">**nx_ppp_dns_address_set**:*Set DNS Server IP address*</span></span>
- <span data-ttu-id="3cbb8-113">**nx_ppp_secondary_dns_address_get**: *보조 DNS 서버 IP 주소 가져오기*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-113">**nx_ppp_secondary_dns_address_get**: *Get Secondary DNS Server IP address*</span></span>
- <span data-ttu-id="3cbb8-114">**nx_ppp_secondary_dns_address_set**: *보조_DNS 서버 IP 주소 설정*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-114">**nx_ppp_secondary_dns_address_set**: *Set Secondary_DNS Server IP address*</span></span>
- <span data-ttu-id="3cbb8-115">**nx_ppp_interface_index_get**: *IP 인터페이스 인덱스 가져오기*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-115">**nx_ppp_interface_index_get**: *Get IP interface index*</span></span>
- <span data-ttu-id="3cbb8-116">**nx_ppp_ip_address_assign**: *IPCP에 대한 IP 주소 할당*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-116">**nx_ppp_ip_address_assign**: *Assign IP addresses for IPCP*</span></span>
- <span data-ttu-id="3cbb8-117">**nx_ppp_link_down_notify**: *링크 다운 시 애플리케이션에 알림*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-117">**nx_ppp_link_down_notify**: *Notify application on link down*</span></span>
- <span data-ttu-id="3cbb8-118">**nx_ppp_link_up_notify**: *링크 연결 시 애플리케이션에 알림*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-118">**nx_ppp_link_up_notify**: *Notify application on link up*</span></span>
- <span data-ttu-id="3cbb8-119">**nx_ppp_nak_authentication_notify**: *인증 NAK가 수신되면 애플리케이션에 알림*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-119">**nx_ppp_nak_authentication_notify**: *Notify application if authentication NAK is received*</span></span>
- <span data-ttu-id="3cbb8-120">**nx_ppp_pap_enable**: *PAP 인증 사용*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-120">**nx_ppp_pap_enable**: *Enable PAP authentication*</span></span>
- <span data-ttu-id="3cbb8-121">**nx_ppp_ping_request**: *LCP echo 요청 보내기*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-121">**nx_ppp_ping_request**: *Send an LCP echo request*</span></span>
- <span data-ttu-id="3cbb8-122">**nx_ppp_raw_string_send**: *비 PPP 문자열 보내기*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-122">**nx_ppp_raw_string_send**: *Send non PPP string*</span></span>
- <span data-ttu-id="3cbb8-123">**nx_ppp_restart**: *PPP 처리 다시 시작*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-123">**nx_ppp_restart**: *Restart PPP processing*</span></span>
- <span data-ttu-id="3cbb8-124">**nx_ppp_start**: *PPP 처리 시작*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-124">**nx_ppp_start**: *Start PPP processing*</span></span>
- <span data-ttu-id="3cbb8-125">**nx_ppp_status_get**: *현재 PPP 상태 가져오기*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-125">**nx_ppp_status_get**: *Get current PPP status*</span></span>
- <span data-ttu-id="3cbb8-126">**nx_ppp_stop**: *PPP 처리 중지*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-126">**nx_ppp_stop**: *Stop PPP processing*</span></span>
- <span data-ttu-id="3cbb8-127">**nx_ppp_packet_receive**: *PPP 패킷 수신*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-127">**nx_ppp_packet_receive**: *Receive PPP packet*</span></span>
- <span data-ttu-id="3cbb8-128">**nx_ppp_packet_send_set**: *PPP 패킷 송신 기능 설정*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-128">**nx_ppp_packet_send_set**: *Set PPP packet send function*</span></span>

## <a name="nx_ppp_byte_receive"></a><span data-ttu-id="3cbb8-129">nx_ppp_byte_receive</span><span class="sxs-lookup"><span data-stu-id="3cbb8-129">nx_ppp_byte_receive</span></span>

<span data-ttu-id="3cbb8-130">직렬 ISR에서 바이트 수신</span><span class="sxs-lookup"><span data-stu-id="3cbb8-130">Receive a byte from serial ISR</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-131">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-131">Prototype</span></span>

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a><span data-ttu-id="3cbb8-132">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-132">Description</span></span>

<span data-ttu-id="3cbb8-133">이 서비스는 일반적으로 수신 바이트를 PPP로 전송하기 위해 애플리케이션의 직렬 드라이버 ISR(인터럽트 서비스 루틴)에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-133">This service is typically called from the application’s serial driver Interrupt Service Routine (ISR) to transfer a received byte to PPP.</span></span> <span data-ttu-id="3cbb8-134">이 루틴은 호출되면 수신 바이트를 순환 바이트 버퍼에 배치하고 처리를 위해 적절한 PPP 스레드에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-134">When called, this routine places the received byte into a circular byte buffer and notifies the appropriate PPP thread for processing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-135">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-135">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-136">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-136">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-137">**byte**: 직렬 디바이스에서 받은 바이트</span><span class="sxs-lookup"><span data-stu-id="3cbb8-137">**byte**: Byte received from serial device</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-138">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-138">Return Values</span></span>

- <span data-ttu-id="3cbb8-139">**NX_SUCCESS**: (0x00) PPP 바이트를 성공적으로 수신했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-139">**NX_SUCCESS**: (0x00) Successful PPP byte receive.</span></span>
- <span data-ttu-id="3cbb8-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP 직렬 버퍼가 이미 꽉 찼습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP serial buffer is already full.</span></span>
- <span data-ttu-id="3cbb8-141">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-141">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-142">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-142">Allowed From</span></span>

<span data-ttu-id="3cbb8-143">스레드, ISR</span><span class="sxs-lookup"><span data-stu-id="3cbb8-143">Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-144">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-144">Example</span></span>

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a><span data-ttu-id="3cbb8-145">nx_ppp_chap_challenge</span><span class="sxs-lookup"><span data-stu-id="3cbb8-145">nx_ppp_chap_challenge</span></span>

<span data-ttu-id="3cbb8-146">CHAP 챌린지 생성</span><span class="sxs-lookup"><span data-stu-id="3cbb8-146">Generate a CHAP challenge</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-147">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-147">Prototype</span></span>

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="3cbb8-148">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-148">Description</span></span>

<span data-ttu-id="3cbb8-149">이 서비스는 PPP 연결이 이미 설정되고 실행된 후 CHAP 챌린지를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-149">This service initiates a CHAP challenge after the PPP connection is already up and running.</span></span> <span data-ttu-id="3cbb8-150">이렇게 하면 애플리케이션이 정기적으로 연결의 신뢰성을 확인하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-150">This gives the application the ability to verify the authenticity of the connection on a periodic basis.</span></span> <span data-ttu-id="3cbb8-151">챌린지에 실패하면 PPP 링크가 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-151">If the challenge is unsuccessful, the PPP link is closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-152">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-152">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-153">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-153">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-154">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-154">Return Values</span></span>

- <span data-ttu-id="3cbb8-155">**NX_SUCCESS**: (0x00) PPP 챌린지를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-155">**NX_SUCCESS**: (0x00) Successful PPP challenge initiated.</span></span>
- <span data-ttu-id="3cbb8-156">**NX_PPP_FAILURE**: (0xB0) 잘못된 PPP 챌린지, CHAP가 응답에만 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-156">**NX_PPP_FAILURE**: (0xB0) Invalid PPP challenge, CHAP was enabled only for response.</span></span>
- <span data-ttu-id="3cbb8-157">**NX_NOT_IMPLEMENTED**: (0x80) CHAP 논리가 NX_PPP_DISABLE_CHAP를 통해 사용하지 않도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-157">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="3cbb8-158">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-158">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="3cbb8-159">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-159">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-160">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-160">Allowed From</span></span>

<span data-ttu-id="3cbb8-161">스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-161">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-162">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-162">Example</span></span>

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a><span data-ttu-id="3cbb8-163">nx_ppp_chap_enable</span><span class="sxs-lookup"><span data-stu-id="3cbb8-163">nx_ppp_chap_enable</span></span>

<span data-ttu-id="3cbb8-164">CHAP 인증 사용</span><span class="sxs-lookup"><span data-stu-id="3cbb8-164">Enable CHAP authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-165">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-165">Prototype</span></span>

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a><span data-ttu-id="3cbb8-166">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-166">Description</span></span>

<span data-ttu-id="3cbb8-167">이 서비스는 지정된 PPP 인스턴스에 대해 CHAP(Challenge-Handshake 인증 프로토콜)를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-167">This service enables the Challenge-Handshake Authentication Protocol (CHAP) for the specified PPP instance.</span></span>

<span data-ttu-id="3cbb8-168">“\***get_challenge_values** _” 및 “_ \*_get_verification_values_\*\*” 함수 포인터를 지정하는 경우 이 PPP 인스턴스에 CHAP가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-168">If the “\***get_challenge_values**_” and “_\*_get_verification_values_\*\*” function pointers are specified, CHAP is required by this PPP instance.</span></span> <span data-ttu-id="3cbb8-169">그렇지 않으면 CHAP는 피어의 챌지 요청에만 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-169">Otherwise, CHAP only responds to the peer’s challenge requests.</span></span>

<span data-ttu-id="3cbb8-170">필요한 콜백 함수에서 다음과 같은 몇 가지 데이터 항목을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-170">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="3cbb8-171">데이터 항목 *비밀*, *이름* 및 *시스템* 은 최대 크기가 NX_PPP_NAME_SIZE-1인 NULL로 종료되는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-171">The data items *secret*, *name*, and *system* are expected to be NULL-terminated strings with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="3cbb8-172">데이터 항목 *rand_value* 는 최대 크기가 NX_PPP_VALUE_SIZE-1인 NULL로 종료되는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-172">The data item *rand_value* is expected to be a NULL-terminated string with a maximum size of NX_PPP_VALUE_SIZE-1.</span></span> <span data-ttu-id="3cbb8-173">데이터 항목 *id* 는 단순 부호 없는 문자 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-173">The data item *id* is a simple unsigned character type.</span></span>

>[!NOTE]
> <span data-ttu-id="3cbb8-174">이 함수는 *nx_ppp_create* 후에 호출해야 하지만 nx_ip_create 또는 *nx_ip_interface_attach* 이전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-174">This function must be called after *nx_ppp_create* but before nx_ip_create or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-175">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-175">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-176">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-176">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-177">**get_challenge_values**: 챌린지에 사용되는 값을 검색하는 애플리케이션 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-177">**get_challenge_values**: Pointer to application function to retrieve values used for the challenge.</span></span> <span data-ttu-id="3cbb8-178">*rand_value*, *id* 및 *비밀* 값을 제공된 대상에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-178">Note that the *rand_value*, *id*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="3cbb8-179">**get_responder_values**: 챌린지에 응답하는 데 사용되는 값을 검색하는 애플리케이션 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-179">**get_responder_values**: Pointer to application function that retrieves values used to respond to a challenge.</span></span> <span data-ttu-id="3cbb8-180">*시스템*, *이름* 및 *비밀* 값을 제공된 대상에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-180">Note that the *system*, *name*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="3cbb8-181">**get_verification_values**: 챌린지 응답을 확인하는 데 사용된 값을 검색하는 애플리케이션 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-181">**get_verification_values**: Pointer to application function that retrieves values used to verify the challenge response.</span></span> <span data-ttu-id="3cbb8-182">*시스템*, *이름* 및 *비밀* 값을 제공된 대상에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-182">Note that the *system*,*name*, and *secret* values must be copied into the supplied destinations.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-183">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-183">Return Values</span></span>

- <span data-ttu-id="3cbb8-184">**NX_SUCCESS**: (0x00) PPP CHAP를 성공적으로 사용하도록 설정함</span><span class="sxs-lookup"><span data-stu-id="3cbb8-184">**NX_SUCCESS**: (0x00) Successful PPP CHAP enable</span></span>
- <span data-ttu-id="3cbb8-185">**NX_NOT_IMPLEMENTED**: (0x80) CHAP 논리가 NX_PPP_DISABLE_CHAP를 통해 사용하지 않도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-185">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="3cbb8-186">NX_PTR_ERROR: (0x07) PPP 포인터나 콜백 함수 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-186">NX_PTR_ERROR: (0x07) Invalid PPP pointer or callback function pointer.</span></span> <span data-ttu-id="3cbb8-187">*get_challenge_values* 가 지정된 경우 *get_verification_values* 함수도 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-187">Note that if *get_challenge_values* is specified, then the *get_verification_values* function must also be supplied.</span></span>
- <span data-ttu-id="3cbb8-188">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-188">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-189">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-189">Allowed From</span></span>

<span data-ttu-id="3cbb8-190">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-190">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-191">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-191">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a><span data-ttu-id="3cbb8-192">nx_ppp_create</span><span class="sxs-lookup"><span data-stu-id="3cbb8-192">nx_ppp_create</span></span>

<span data-ttu-id="3cbb8-193">PPP 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="3cbb8-193">Create a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-194">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-194">Prototype</span></span>

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a><span data-ttu-id="3cbb8-195">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-195">Description</span></span>

<span data-ttu-id="3cbb8-196">이 서비스는 지정된 NetX IP 인스턴스에 대한 PPP 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-196">This service creates a PPP instance for the specified NetX IP instance.</span></span>

>[!NOTE]
> <span data-ttu-id="3cbb8-197">일반적으로는 PPP 스레드 우선 순위보다 우선 순위가 높은 NetX IP 스레드를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-197">It is generally a good idea to create the NetX IP thread at a higher priority than the PPP thread priority.</span></span> <span data-ttu-id="3cbb8-198">IP 스레드 우선 순위를 지정하는 방법에 대한 자세한 내용은 *nx_ip_create* 서비스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-198">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-199">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-199">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-200">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-200">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-201">**name**: 이 PPP 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-201">**name**: Name of this PPP instance.</span></span>
- <span data-ttu-id="3cbb8-202">**ip_ptr**: 아직 생성되지 않은 IP 인스턴스의 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-202">**ip_ptr**: Pointer to control block for not-yet-created IP instance.</span></span>
- <span data-ttu-id="3cbb8-203">**stack_memory_ptr**: PPP 스레드의 스택 영역 시작에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-203">**stack_memory_ptr**: Pointer to start of PPP thread’s stack area.</span></span>
- <span data-ttu-id="3cbb8-204">**stack_size** 스레드의 스택에 있는 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-204">**stack_size**: Size in bytes in the thread’s stack.</span></span>
- <span data-ttu-id="3cbb8-205">**pool_ptr** 기본 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-205">**pool_ptr**: Pointer to default packet pool.</span></span>
- <span data-ttu-id="3cbb8-206">**thread_priority**: 내부 PPP 스레드의 우선 순위(1-31)입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-206">**thread_priority**: Priority of internal PPP threads (1-31).</span></span>
- <span data-ttu-id="3cbb8-207">**ppp_invalid_packet_handler**: 모든 비 PPP 패킷에 대한 애플리케이션 처리기에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-207">**ppp_invalid_packet_handler**: Function pointer to application’s handler for all non-PPP packets.</span></span> <span data-ttu-id="3cbb8-208">NetX PPP는 일반적으로 초기화하는 동안 이 루틴을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-208">The NetX PPP typically calls this routine during initialization.</span></span> <span data-ttu-id="3cbb8-209">애플리케이션이 모뎀 명령에 응답하거나 Windows XP의 경우 NetX PPP 애플리케이션이 Windows XP에서 전송하는 초기 "클라이언트"에 "클라이언트 서버"로 응답하여 PPP를 시작할 수 있는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-209">This is where the application can respond to modem commands or in the case of Windows XP, the NetX PPP application can initiate PPP by responding with“ CLIENT SERVER” to the initial “CLIENT” sent by Windows XP.</span></span>
- <span data-ttu-id="3cbb8-210">**ppp_byte_send**: 애플리케이션의 직렬 바이트 출력 루틴에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-210">**ppp_byte_send**: Function pointer to application’s serial byte output routine.</span></span>


### <a name="return-values"></a><span data-ttu-id="3cbb8-211">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-211">Return Values</span></span>

- <span data-ttu-id="3cbb8-212">**NX_SUCCESS**: (0x00) PPP를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-212">**NX_SUCCESS**: (0x00) Successful PPP create.</span></span>
- <span data-ttu-id="3cbb8-213">NX_PTR_ERROR: (0x07) 잘못된 PPP, IP 또는 바이트 출력 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-213">NX_PTR_ERROR: (0x07) Invalid PPP, IP, or byte output function pointer.</span></span>
- <span data-ttu-id="3cbb8-214">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-214">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-215">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-215">Allowed From</span></span>

<span data-ttu-id="3cbb8-216">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-216">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-217">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-217">Example</span></span>

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a><span data-ttu-id="3cbb8-218">nx_ppp_delete</span><span class="sxs-lookup"><span data-stu-id="3cbb8-218">nx_ppp_delete</span></span>

<span data-ttu-id="3cbb8-219">PPP 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-219">Delete a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-220">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-220">Prototype</span></span>

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="3cbb8-221">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-221">Description</span></span>

<span data-ttu-id="3cbb8-222">이 서비스는 이전에 만든 PPP 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-222">This service deletes the previously created PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-223">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-223">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-224">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-224">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-225">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-225">Return Values</span></span>

- <span data-ttu-id="3cbb8-226">**NX_SUCCESS**: (0x00) PPP를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-226">**NX_SUCCESS**: (0x00) Successful PPP deletion.</span></span>
- <span data-ttu-id="3cbb8-227">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-227">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="3cbb8-228">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-228">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-229">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-229">Allowed From</span></span>

<span data-ttu-id="3cbb8-230">스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-231">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-231">Example</span></span>

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a><span data-ttu-id="3cbb8-232">nx_ppp_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="3cbb8-232">nx_ppp_dns_address_get</span></span>

<span data-ttu-id="3cbb8-233">DNS IP 주소 가져오기</span><span class="sxs-lookup"><span data-stu-id="3cbb8-233">Get DNS IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-234">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-234">Prototype</span></span>

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="3cbb8-235">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-235">Description</span></span>

<span data-ttu-id="3cbb8-236">이 서비스는 피어에서 제공된 DNS IP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-236">This service retrieves the DNS IP address supplied by the peer.</span></span> <span data-ttu-id="3cbb8-237">피어가 IP 주소를 제공하지 않은 경우 IP 주소 0이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-237">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-238">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-238">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-239">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-239">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-240">**dns_address_ptr**: DNS IP 주소에 대한 대상</span><span class="sxs-lookup"><span data-stu-id="3cbb8-240">**dns_address_ptr**: Destination for DNS IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-241">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-241">Return Values</span></span>

- <span data-ttu-id="3cbb8-242">**NX_SUCCESS**: (0x00) PPP 주소를 성공적으로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-242">**NX_SUCCESS**: (0x00) Successful PPP address get.</span></span>
- <span data-ttu-id="3cbb8-243">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어 협상을 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-243">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="3cbb8-244">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-244">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-245">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-245">Allowed From</span></span>

<span data-ttu-id="3cbb8-246">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="3cbb8-246">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-247">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-247">Example</span></span>

```c

ULONG  my_dns_address;

/* Get IP Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a><span data-ttu-id="3cbb8-248">nx_ppp_secondary_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="3cbb8-248">nx_ppp_secondary_dns_address_get</span></span>

<span data-ttu-id="3cbb8-249">보조 DNS 서버 IP 주소 가져오기</span><span class="sxs-lookup"><span data-stu-id="3cbb8-249">Get Secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-250">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-250">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="3cbb8-251">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-251">Description</span></span>

<span data-ttu-id="3cbb8-252">이 서비스는 IPCP 핸드셰이크의 피어에서 제공된 보조 DNS IP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-252">This service retrieves the secondary DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="3cbb8-253">피어가 IP 주소를 제공하지 않은 경우 IP 주소 0이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-253">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-254">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-254">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-255">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-255">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-256">**dns_address_ptr**: 보조 DNS 서버 주소에 대한 대상</span><span class="sxs-lookup"><span data-stu-id="3cbb8-256">**dns_address_ptr**: Destination for Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-257">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-257">Return Values</span></span>

- <span data-ttu-id="3cbb8-258">**NX_SUCCESS**: (0x00) DNS 주소를 성공적으로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-258">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="3cbb8-259">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어 협상을 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-259">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="3cbb8-260">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-260">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-261">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-261">Allowed From</span></span>

<span data-ttu-id="3cbb8-262">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="3cbb8-262">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-263">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-263">Example</span></span>

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a><span data-ttu-id="3cbb8-264">nx_ppp_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="3cbb8-264">nx_ppp_dns_address_set</span></span>

<span data-ttu-id="3cbb8-265">주 DNS 서버 IP 주소 설정</span><span class="sxs-lookup"><span data-stu-id="3cbb8-265">Set primary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-266">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-266">Prototype</span></span>

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="3cbb8-267">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-267">Description</span></span>

<span data-ttu-id="3cbb8-268">이 서비스는 DNS 서버 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-268">This service sets the DNS Server IP address.</span></span> <span data-ttu-id="3cbb8-269">피어가 IPCP 상태에서 DNS 서버 옵션 요청을 보내는 경우 이 호스트는 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-269">If the peer sends a DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-270">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-270">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-271">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-271">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-272">**dns_address**: DNS 서버 주소</span><span class="sxs-lookup"><span data-stu-id="3cbb8-272">**dns_address**: DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-273">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-273">Return Values</span></span>

- <span data-ttu-id="3cbb8-274">**NX_SUCCESS**: (0x00) DNS 주소를 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-274">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span>
- <span data-ttu-id="3cbb8-275">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어 협상을 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-275">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="3cbb8-276">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-276">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-277">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-277">Allowed From</span></span>

<span data-ttu-id="3cbb8-278">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-278">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-279">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-279">Example</span></span>

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a><span data-ttu-id="3cbb8-280">nx_ppp_secondary_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="3cbb8-280">nx_ppp_secondary_dns_address_set</span></span>

<span data-ttu-id="3cbb8-281">보조 DNS 서버 IP 주소 설정</span><span class="sxs-lookup"><span data-stu-id="3cbb8-281">Set secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-282">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-282">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="3cbb8-283">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-283">Description</span></span>

<span data-ttu-id="3cbb8-284">이 서비스는 보조 DNS 서버 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-284">This service sets the secondary DNS Server IP address.</span></span> <span data-ttu-id="3cbb8-285">피어가 IPCP 상태에서 보조 DNS 서버 옵션 요청을 보내는 경우 이 호스트는 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-285">If the peer sends a secondary DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-286">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-286">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-287">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-287">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-288">**dns_address**: 보조 DNS 서버 주소</span><span class="sxs-lookup"><span data-stu-id="3cbb8-288">**dns_address**: Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-289">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-289">Return Values</span></span>

- <span data-ttu-id="3cbb8-290">**NX_SUCCESS**: (0x00) DNS 주소를 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-290">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span> 
- <span data-ttu-id="3cbb8-291">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어 협상을 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-291">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="3cbb8-292">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-292">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-293">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-293">Allowed From</span></span>

<span data-ttu-id="3cbb8-294">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-294">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-295">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-295">Example</span></span>

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a><span data-ttu-id="3cbb8-296">nx_ppp_interface_index_get</span><span class="sxs-lookup"><span data-stu-id="3cbb8-296">nx_ppp_interface_index_get</span></span>

<span data-ttu-id="3cbb8-297">IP 인터페이스 인덱스 가져오기</span><span class="sxs-lookup"><span data-stu-id="3cbb8-297">Get IP interface index</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-298">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-298">Prototype</span></span>

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a><span data-ttu-id="3cbb8-299">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-299">Description</span></span>

<span data-ttu-id="3cbb8-300">이 서비스는 이 PPP 인스턴스와 연결된 IP 인터페이스 인덱스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-300">This service retrieves the IP interface index associated with this PPP instance.</span></span> <span data-ttu-id="3cbb8-301">이는 PPP 인스턴스가 IP 인스턴스의 기본 인터페이스가 아닌 경우에만 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-301">This is only useful when the PPP instance is not the primary interface of an IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-302">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-302">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-303">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-303">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-304">**index_ptr**: 인터페이스 인덱스의 대상</span><span class="sxs-lookup"><span data-stu-id="3cbb8-304">**index_ptr**: Destination for interface index</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-305">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-305">Return Values</span></span>

- <span data-ttu-id="3cbb8-306">**NX_SUCCESS**: (0x00) PPP 인덱스를 성공적으로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-306">**NX_SUCCESS**: (0x00) Successful PPP index get.</span></span>
- <span data-ttu-id="3cbb8-307">**NX_IN_PROGRESS**: (0x37) PPP가 초기화를 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-307">**NX_IN_PROGRESS**: (0x37) PPP has not completed initialization.</span></span>
- <span data-ttu-id="3cbb8-308">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-308">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-309">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-309">Allowed From</span></span>

<span data-ttu-id="3cbb8-310">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="3cbb8-310">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-311">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-311">Example</span></span>

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a><span data-ttu-id="3cbb8-312">nx_ppp_ip_address_assign</span><span class="sxs-lookup"><span data-stu-id="3cbb8-312">nx_ppp_ip_address_assign</span></span>

<span data-ttu-id="3cbb8-313">IPCP에 대한 IP 주소 할당</span><span class="sxs-lookup"><span data-stu-id="3cbb8-313">Assign IP addresses for IPCP</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-314">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-314">Prototype</span></span>

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a><span data-ttu-id="3cbb8-315">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-315">Description</span></span>

<span data-ttu-id="3cbb8-316">이 서비스는 IPCP(인터넷 프로토콜 제어 프로토콜)에서 사용할 로컬 및 피어 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-316">This service sets up the local and peer IP addresses for use in the Internet Protocol Control Protocol (IPCP).</span></span> <span data-ttu-id="3cbb8-317">PPP 애플리케이션은 자체 및 다른 피어에 대해 유효한 IP 주소를 사용하는 PPP 인스턴스에서 이 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-317">The PPP application should invoke this service on a PPP instance with valid IP addresses for itself and the other peer.</span></span>  <span data-ttu-id="3cbb8-318">유효한 주소가 PPP 인스턴스에 등록되지 않은 경우에는 해당 IP 주소를 정의하는 데 PPP 피어를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-318">If no valid addresses are registered with a PPP instance, it must rely on the PPP peer to define its IP address.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="3cbb8-319">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-319">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-320">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-320">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-321">**local_ip_address** 로컬 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-321">**local_ip_address**: Local IP address.</span></span>
- <span data-ttu-id="3cbb8-322">**peer_ip_address**: 피어의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-322">**peer_ip_address**: Peer’s IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-323">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-323">Return Values</span></span>

- <span data-ttu-id="3cbb8-324">**NX_SUCCESS**: (0x00) PPP 주소를 성공적으로 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-324">**NX_SUCCESS**: (0x00) Successful PPP address assignment.</span></span>
- <span data-ttu-id="3cbb8-325">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-325">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="3cbb8-326">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-327">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-327">Allowed From</span></span>

<span data-ttu-id="3cbb8-328">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-329">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-329">Example</span></span>

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a><span data-ttu-id="3cbb8-330">nx_ppp_link_down_notify</span><span class="sxs-lookup"><span data-stu-id="3cbb8-330">nx_ppp_link_down_notify</span></span>

<span data-ttu-id="3cbb8-331">링크 다운 시 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="3cbb8-331">Notify application on link down</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-332">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-332">Prototype</span></span>

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a><span data-ttu-id="3cbb8-333">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-333">Description</span></span>

<span data-ttu-id="3cbb8-334">이 서비스는 지정된 PPP 인스턴스를 사용하여 애플리케이션의 링크 다운 알림 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-334">This service registers the application’s link down notification callback with the specified PPP instance.</span></span> <span data-ttu-id="3cbb8-335">NULL이 아닌 경우 링크가 중단될 때마다 애플리케이션의 링크 다운 콜백 함수가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-335">If non-NULL, the application’s link down callback function is called whenever the link goes down.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-336">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-336">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-337">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-337">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-338">**link_down_callback**: 애플리케이션의 링크 다운 알림 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-338">**link_down_callback**: Application’s link down notification function pointer.</span></span> <span data-ttu-id="3cbb8-339">NULL인 경우 링크 다운 알림이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-339">If NULL, link down notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-340">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-340">Return Values</span></span>

- <span data-ttu-id="3cbb8-341">**NX_SUCCESS**: (0x00) 링크 다운 알림 콜백을 성공적으로 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-341">**NX_SUCCESS**: (0x00) Successful link down notification callback registration.</span></span>
- <span data-ttu-id="3cbb8-342">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-342">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-343">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-343">Allowed From</span></span>

<span data-ttu-id="3cbb8-344">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="3cbb8-344">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-345">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-345">Example</span></span>

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a><span data-ttu-id="3cbb8-346">nx_ppp_link_up_notify</span><span class="sxs-lookup"><span data-stu-id="3cbb8-346">nx_ppp_link_up_notify</span></span>

<span data-ttu-id="3cbb8-347">링크 연결 시 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="3cbb8-347">Notify application on link up</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-348">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-348">Prototype</span></span>

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a><span data-ttu-id="3cbb8-349">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-349">Description</span></span>

<span data-ttu-id="3cbb8-350">이 서비스는 지정된 PPP 인스턴스를 사용하여 애플리케이션의 링크 연결 알림 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-350">This service registers the application’s link up notification callback with the specified PPP instance.</span></span> <span data-ttu-id="3cbb8-351">NULL이 아닌 경우 링크가 연결될 때마다 애플리케이션의 링크 연결 콜백 함수가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-351">If non-NULL, the application’s link up callback function is called whenever the link comes up.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-352">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-352">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-353">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-353">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-354">**link_up_callback**: 애플리케이션의 링크 연결 알림 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-354">**link_up_callback**: Application’s link up notification function pointer.</span></span> <span data-ttu-id="3cbb8-355">NULL인 경우 링크 연결 알림이 사용되지 않습니다.\*\*</span><span class="sxs-lookup"><span data-stu-id="3cbb8-355">If NULL, link up notification is disabled.\*\*</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-356">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-356">Return Values</span></span>

- <span data-ttu-id="3cbb8-357">**NX_SUCCESS**: (0x00) 링크 연결 알림 콜백을 성공적으로 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-357">**NX_SUCCESS**: (0x00) Successful link up notification callback registration.</span></span>
- <span data-ttu-id="3cbb8-358">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-358">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-359">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-359">Allowed From</span></span>

<span data-ttu-id="3cbb8-360">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="3cbb8-360">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-361">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-361">Example</span></span>

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a><span data-ttu-id="3cbb8-362">nx_ppp_nak_authentication_notify</span><span class="sxs-lookup"><span data-stu-id="3cbb8-362">nx_ppp_nak_authentication_notify</span></span>

<span data-ttu-id="3cbb8-363">인증 NAK가 수신되면 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="3cbb8-363">Notify application if authentication NAK received</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-364">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-364">Prototype</span></span>

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a><span data-ttu-id="3cbb8-365">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-365">Description</span></span>

<span data-ttu-id="3cbb8-366">이 서비스는 지정된 PPP 인스턴스를 사용하여 애플리케이션의 인증 nak 알림 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-366">This service registers the application’s authentication nak notification callback with the specified PPP instance.</span></span> <span data-ttu-id="3cbb8-367">NULL이 아닌 경우 이 콜백 함수는 PPP 인스턴스가 인증 중에 NAK를 받을 때마다 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-367">If non-NULL, this callback function is called whenever the PPP instance receives a NAK during authentiaction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-368">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-368">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-369">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-369">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-370">**nak_authentication_notify**: PPP 인스턴스가 인증 NAK를 받을 때 호출되는 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-370">**nak_authentication_notify**: Pointer to function called when the PPP instance receives an authentication NAK.</span></span> <span data-ttu-id="3cbb8-371">NULL인 경우 알림이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-371">If NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-372">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-372">Return Values</span></span>

- <span data-ttu-id="3cbb8-373">**NX_SUCCESS**: (0x00) 알림 콜백을 성공적으로 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-373">**NX_SUCCESS**: (0x00) Successful notification callback registration.</span></span>
- <span data-ttu-id="3cbb8-374">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-374">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-375">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-375">Allowed From</span></span>

<span data-ttu-id="3cbb8-376">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="3cbb8-376">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-377">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-377">Example</span></span>

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a><span data-ttu-id="3cbb8-378">nx_ppp_pap_enable</span><span class="sxs-lookup"><span data-stu-id="3cbb8-378">nx_ppp_pap_enable</span></span>

<span data-ttu-id="3cbb8-379">PAP 인증 사용</span><span class="sxs-lookup"><span data-stu-id="3cbb8-379">Enable PAP Authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-380">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-380">Prototype</span></span>

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a><span data-ttu-id="3cbb8-381">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-381">Description</span></span>

<span data-ttu-id="3cbb8-382">이 서비스는 지정된 PPP 인스턴스에 대해 PAP(암호 인증 프로토콜)를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-382">This service enables the Password Authentication Protocol (PAP) for the specified PPP instance.</span></span> <span data-ttu-id="3cbb8-383">"***Verify_login***" 함수 포인터를 지정하는 경우 이 PPP 인스턴스에 PAP가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-383">If the “***verify_login***” function pointer is specified, PAP is required by this PPP instance.</span></span> <span data-ttu-id="3cbb8-384">그렇지 않으면 PAP는 LCP 협상 중에 지정된 피어의 PAP 요구 사항에만 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-384">Otherwise, PAP only responds to the peer’s PAP requirements as specified during LCP negotiation.</span></span>

<span data-ttu-id="3cbb8-385">필요한 콜백 함수에서 다음과 같은 몇 가지 데이터 항목을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-385">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="3cbb8-386">데이터 항목 *이름* 은 최대 크기가 NX_PPP_NAME_SIZE-1인 NULL로 종료되는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-386">The data item *name* is expected to be NULL-terminated string with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="3cbb8-387">데이터 항목 *암호* 는 최대 크기가 NX_PPP_PASSWORD_SIZE-1인 NULL로 종료되는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-387">The data item *password* is also expected to be a NULL-terminated string with a maximum size of NX_PPP_PASSWORD_SIZE-1.</span></span>

>[!NOTE]
> <span data-ttu-id="3cbb8-388">이 함수는 *nx_ppp_create* 후에 호출해야 하지만 *nx_ip_create* 또는 *nx_ip_interface_attach* 이전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-388">This function must be called after *nx_ppp_create* but before *nx_ip_create* or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-389">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-389">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-390">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-390">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-391">**generate_login**: 피어에서 인증을 위한 *이름* 및 *암호* 를 생성하는 애플리케이션 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-391">**generate_login**: Pointer to application function that produces a *name* and *password* for authentication by the peer.</span></span> <span data-ttu-id="3cbb8-392">*이름* 및 *암호* 값을 제공된 대상에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-392">Note that the *name* and *password* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="3cbb8-393">**verify_login**: 피어에서 제공한 *이름* 및 *암호* 를 확인하는 애플리케이션 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-393">**verify_login**: Pointer to application function that verifies the *name* and *password* supplied by the peer.</span></span> <span data-ttu-id="3cbb8-394">이 루틴은 제공된 *이름* 및 *암호* 를 비교해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-394">This routine must compare the supplied *name* and *password*.</span></span> <span data-ttu-id="3cbb8-395">이 루틴이 NX_SUCCESS를 반환하는 경우 이름과 암호가 올바르고 PPP가 다음 단계로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-395">If this routine returns NX_SUCCESS, the name and password are correct and PPP can proceed to the next step.</span></span> <span data-ttu-id="3cbb8-396">그렇지 않으면 이 루틴은 NX_PPP_ERROR를 반환하고 PPP는 다른 이름과 암호를 대기하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-396">Otherwise, this routine returns NX_PPP_ERROR and PPP simply waits for another name and password.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-397">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-397">Return Values</span></span>

- <span data-ttu-id="3cbb8-398">**NX_SUCCESS**: (0x00) PPP PAP를 성공적으로 사용하도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-398">**NX_SUCCESS**: (0x00) Successful PPP PAP enable.</span></span>
- <span data-ttu-id="3cbb8-399">**NX_NOT_IMPLEMENTED**: (0x80) PAP 논리가 NX_PPP_DISABLE_PAP를 통해 사용하지 않도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-399">**NX_NOT_IMPLEMENTED**: (0x80) PAP logic was disabled via NX_PPP_DISABLE_PAP.</span></span>
- <span data-ttu-id="3cbb8-400">NX_PTR_ERROR: (0x07) PPP 포인터나 애플리케이션 함수 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-400">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="3cbb8-401">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-401">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-402">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-402">Allowed From</span></span>

<span data-ttu-id="3cbb8-403">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-403">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-404">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-404">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a><span data-ttu-id="3cbb8-405">nx_ppp_ping_request</span><span class="sxs-lookup"><span data-stu-id="3cbb8-405">nx_ppp_ping_request</span></span>

<span data-ttu-id="3cbb8-406">LCP ping 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="3cbb8-406">Send an LCP ping request</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-407">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-407">Prototype</span></span>

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a><span data-ttu-id="3cbb8-408">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-408">Description</span></span>

<span data-ttu-id="3cbb8-409">이 서비스는 LCP ping 요청을 보내고 PPP 디바이스가 echo 응답을 대기하고 있음을 플래그 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-409">This service sends an LCP ping request and sets a flag that the PPP device is waiting for an echo response.</span></span> <span data-ttu-id="3cbb8-410">요청이 전송되는 즉시 서비스가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-410">The service returns as soon as the request is sent.</span></span> <span data-ttu-id="3cbb8-411">응답을 기다리지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-411">It does not wait for a response.</span></span> 

<span data-ttu-id="3cbb8-412">일치하는 echo 응답이 수신되면 PPP 스레드 태스크가 플래그를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-412">When a matching echo response is received, the PPP thread task will clear the flag.</span></span> <span data-ttu-id="3cbb8-413">PPP 디바이스는 PPP 협상의 LCP 부분을 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-413">The PPP device must have completed the LCP part of the PPP negotiation.</span></span>

<span data-ttu-id="3cbb8-414">이 서비스는 링크 상태에 대한 하드웨어 폴링을 쉽게 수행할 수 없는 PPP 설정에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-414">This service is useful for PPP set ups where polling the hardware for link status may not be readily possible.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-415">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-415">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-416">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-416">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-417">**data**: echo 요청에서 보낼 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-417">**data**: Pointer to data to send in echo request.</span></span>
- <span data-ttu-id="3cbb8-418">**data_size**: LCP echo 메시지를 보내기 위해 대기하는 wait_option 시간을 보낼 데이터의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-418">**data_size**: Size of data to send wait_option Time to wait to send the LCP echo message.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-419">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-419">Return Values</span></span>

- <span data-ttu-id="3cbb8-420">**NX_SUCCESS**: (0x00) echo 요청을 성공적으로 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-420">**NX_SUCCESS**: (0x00) Successful sent echo request.</span></span>
- <span data-ttu-id="3cbb8-421">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP 연결이 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-421">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP connection not established.</span></span>
- <span data-ttu-id="3cbb8-422">NX_PTR_ERROR: (0x07) PPP 포인터나 애플리케이션 함수 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-422">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="3cbb8-423">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-423">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-424">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-424">Allowed From</span></span>

<span data-ttu-id="3cbb8-425">애플리케이션 스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-425">Application threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-426">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-426">Example</span></span>

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  strlen("username ");

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a><span data-ttu-id="3cbb8-427">nx_ppp_raw_string_send</span><span class="sxs-lookup"><span data-stu-id="3cbb8-427">nx_ppp_raw_string_send</span></span>

<span data-ttu-id="3cbb8-428">원시 ASCII 문자열 보내기</span><span class="sxs-lookup"><span data-stu-id="3cbb8-428">Send a raw ASCII string</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-429">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-429">Prototype</span></span>

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a><span data-ttu-id="3cbb8-430">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-430">Description</span></span>

<span data-ttu-id="3cbb8-431">이 서비스는 PPP 인터페이스가 아닌 비 PPP ASCII 문자열을 직접 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-431">This service sends a non-PPP ASCII string directly out the PPP interface.</span></span> <span data-ttu-id="3cbb8-432">이는 일반적으로 PPP가 모뎀 제어 정보를 포함하는 비 PPP 패킷을 수신한 후에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-432">It is typically used after PPP receives a non-PPP packet that contains modem control information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-433">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-433">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-434">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-434">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-435">**string_ptr**: 보낼 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-435">**string_ptr**: Pointer to string to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-436">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-436">Return Values</span></span>

- <span data-ttu-id="3cbb8-437">**NX_SUCCESS**: (0x00) PPP 원시 문자열을 성공적으로 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-437">**NX_SUCCESS**: (0x00) Successful PPP raw string send.</span></span>
- <span data-ttu-id="3cbb8-438">NX_PTR_ERROR: (0x07) PPP 포인터나 문자열 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-438">NX_PTR_ERROR: (0x07) Invalid PPP pointer or string pointer.</span></span>
- <span data-ttu-id="3cbb8-439">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-439">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-440">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-440">Allowed From</span></span>

<span data-ttu-id="3cbb8-441">스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-442">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-442">Example</span></span>

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a><span data-ttu-id="3cbb8-443">nx_ppp_restart</span><span class="sxs-lookup"><span data-stu-id="3cbb8-443">nx_ppp_restart</span></span>

<span data-ttu-id="3cbb8-444">PPP 처리 다시 시작</span><span class="sxs-lookup"><span data-stu-id="3cbb8-444">Restart PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-445">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-445">Prototype</span></span>

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="3cbb8-446">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-446">Description</span></span>

<span data-ttu-id="3cbb8-447">이 서비스는 PPP 처리를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-447">This service restarts the PPP processing.</span></span> <span data-ttu-id="3cbb8-448">일반적으로 링크 다운 콜백에서 또는 통신이 손실되었다는 비 PPP 모뎀 메시지에서 링크를 다시 설정해야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-448">It is typically called when the link needs to be re-established either from a link down callback or by a non-PPP modem message indicating communication was lost.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-449">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-449">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-450">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-450">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-451">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-451">Return Values</span></span>

- <span data-ttu-id="3cbb8-452">**NX_SUCCESS**: (0x00) PPP 다시 시작이 성공적으로 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-452">**NX_SUCCESS**: (0x00) Successful PPP restart initiated.</span></span>
- <span data-ttu-id="3cbb8-453">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-453">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="3cbb8-454">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-454">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-455">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-455">Allowed From</span></span>

<span data-ttu-id="3cbb8-456">스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-456">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-457">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-457">Example</span></span>

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a><span data-ttu-id="3cbb8-458">nx_ppp_start</span><span class="sxs-lookup"><span data-stu-id="3cbb8-458">nx_ppp_start</span></span>

<span data-ttu-id="3cbb8-459">PPP 처리 시작</span><span class="sxs-lookup"><span data-stu-id="3cbb8-459">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-460">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-460">Prototype</span></span>

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="3cbb8-461">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-461">Description</span></span>

<span data-ttu-id="3cbb8-462">이 서비스는 PPP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-462">This service starts the PPP processing.</span></span> <span data-ttu-id="3cbb8-463">일반적으로 nx_ppp_stop()을 호출한 후에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-463">It is typically called after nx_ppp_stop() called.</span></span>

>[!NOTE]
> <span data-ttu-id="3cbb8-464">연결이 설정되면 PPP가 자동으로 PPP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-464">PPP automatically starts the PPP processing when the link is enabled.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-465">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-465">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-466">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-466">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-467">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-467">Return Values</span></span>

- <span data-ttu-id="3cbb8-468">**NX_SUCCESS**: (0x00) PPP 시작이 성공적으로 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-468">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="3cbb8-469">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP가 이미 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-469">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP already started.</span></span>
- <span data-ttu-id="3cbb8-470">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-470">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="3cbb8-471">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-471">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-472">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-472">Allowed From</span></span>

<span data-ttu-id="3cbb8-473">스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-473">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-474">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-474">Example</span></span>

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a><span data-ttu-id="3cbb8-475">nx_ppp_status_get</span><span class="sxs-lookup"><span data-stu-id="3cbb8-475">nx_ppp_status_get</span></span>

<span data-ttu-id="3cbb8-476">현재 PPP 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="3cbb8-476">Get current PPP status</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-477">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-477">Prototype</span></span>

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a><span data-ttu-id="3cbb8-478">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-478">Description</span></span>

<span data-ttu-id="3cbb8-479">이 서비스는 지정된 PPP 인스턴스의 현재 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-479">This service gets the current status of the specified PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-480">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-480">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-481">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-481">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-482">**status_ptr**: PPP 상태에 대한 대상, 가능한 상태 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-482">**status_ptr**: Destination for the PPP status, the following are possible status values:</span></span>
    - <span data-ttu-id="3cbb8-483">**NX_PPP_STATUS_ESTABLISHED**</span><span class="sxs-lookup"><span data-stu-id="3cbb8-483">**NX_PPP_STATUS_ESTABLISHED**</span></span>
    - <span data-ttu-id="3cbb8-484">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="3cbb8-484">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="3cbb8-485">**NX_PPP_STATUS_LCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="3cbb8-485">**NX_PPP_STATUS_LCP_FAILED**</span></span>
    - <span data-ttu-id="3cbb8-486">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="3cbb8-486">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="3cbb8-487">**NX_PPP_STATUS_PAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="3cbb8-487">**NX_PPP_STATUS_PAP_FAILED**</span></span>
    - <span data-ttu-id="3cbb8-488">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="3cbb8-488">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="3cbb8-489">**NX_PPP_STATUS_CHAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="3cbb8-489">**NX_PPP_STATUS_CHAP_FAILED**</span></span>
    - <span data-ttu-id="3cbb8-490">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="3cbb8-490">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="3cbb8-491">**NX_PPP_STATUS_IPCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="3cbb8-491">**NX_PPP_STATUS_IPCP_FAILED**</span></span>

>[!NOTE]
> <span data-ttu-id="3cbb8-492">상태는 API가 NX_SUCCESS를 반환하는 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-492">The status is only valid if the API returns NX_SUCCESS.</span></span> <span data-ttu-id="3cbb8-493">또한 \*_FAILED 상태 값이 반환되는 경우 애플리케이션에서 다시 시작할 때까지 PPP 처리가 효과적으로 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-493">In addition, if any of the \*_FAILED status values are returned, PPP processing is effectively stopped until it is restarted again by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-494">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-494">Return Values</span></span>

- <span data-ttu-id="3cbb8-495">**NX_SUCCESS**: (0x00) PPP 상태가 성공적으로 요청되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-495">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="3cbb8-496">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-496">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-497">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-497">Allowed From</span></span>

<span data-ttu-id="3cbb8-498">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="3cbb8-498">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-499">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-499">Example</span></span>

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a><span data-ttu-id="3cbb8-500">nx_ppp_stop</span><span class="sxs-lookup"><span data-stu-id="3cbb8-500">nx_ppp_stop</span></span>

<span data-ttu-id="3cbb8-501">PPP 처리 시작</span><span class="sxs-lookup"><span data-stu-id="3cbb8-501">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-502">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-502">Prototype</span></span>

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="3cbb8-503">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-503">Description</span></span>

<span data-ttu-id="3cbb8-504">이 서비스는 PPP 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-504">This service stops the PPP processing.</span></span> <span data-ttu-id="3cbb8-505">또한 사용자는 필요에 따라 nx_ppp_start()를 호출하여 PPP 처리를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-505">User also can calls nx_ppp_start() to start the PPP processing if needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-506">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-506">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-507">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-507">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-508">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-508">Return Values</span></span>

- <span data-ttu-id="3cbb8-509">**NX_SUCCESS**: (0x00) PPP 시작이 성공적으로 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-509">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="3cbb8-510">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP가 이미 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-510">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP already stopped.</span></span>
- <span data-ttu-id="3cbb8-511">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-511">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="3cbb8-512">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-513">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-513">Allowed From</span></span>

<span data-ttu-id="3cbb8-514">스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-515">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-515">Example</span></span>

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a><span data-ttu-id="3cbb8-516">nx_ppp_packet_receive</span><span class="sxs-lookup"><span data-stu-id="3cbb8-516">nx_ppp_packet_receive</span></span>

<span data-ttu-id="3cbb8-517">PPP 패킷 수신</span><span class="sxs-lookup"><span data-stu-id="3cbb8-517">Receive PPP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-518">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-518">Prototype</span></span>

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="3cbb8-519">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-519">Description</span></span>

<span data-ttu-id="3cbb8-520">이 서비스는 PPP 패킷을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-520">This service receives PPP packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-521">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-521">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-522">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-522">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-523">**packet_ptr**: PPP 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-523">**packet_ptr**: Pointer to PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-524">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-524">Return Values</span></span>

- <span data-ttu-id="3cbb8-525">**NX_SUCCESS**: (0x00) PPP 상태가 성공적으로 요청되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-525">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="3cbb8-526">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-526">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-527">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-527">Allowed From</span></span>

<span data-ttu-id="3cbb8-528">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-528">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-529">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-529">Example</span></span>

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a><span data-ttu-id="3cbb8-530">nx_ppp_packet_send_set</span><span class="sxs-lookup"><span data-stu-id="3cbb8-530">nx_ppp_packet_send_set</span></span>

<span data-ttu-id="3cbb8-531">PPP 패킷 송신 기능 설정</span><span class="sxs-lookup"><span data-stu-id="3cbb8-531">Set the PPP packet send function</span></span>

### <a name="prototype"></a><span data-ttu-id="3cbb8-532">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3cbb8-532">Prototype</span></span>

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a><span data-ttu-id="3cbb8-533">Description</span><span class="sxs-lookup"><span data-stu-id="3cbb8-533">Description</span></span>

<span data-ttu-id="3cbb8-534">이 서비스는 PPP 패킷 송신 기능을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-534">This service sets the PPP packet send funciton.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3cbb8-535">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3cbb8-535">Input Parameters</span></span>

- <span data-ttu-id="3cbb8-536">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-536">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="3cbb8-537">**nx_ppp_packet_send**: PPP 패킷을 전송하는 루틴입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-537">**nx_ppp_packet_send**: Routine to send PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="3cbb8-538">반환 값</span><span class="sxs-lookup"><span data-stu-id="3cbb8-538">Return Values</span></span>

- <span data-ttu-id="3cbb8-539">**NX_SUCCESS**: (0x00) PPP 상태가 성공적으로 요청되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-539">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="3cbb8-540">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3cbb8-540">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3cbb8-541">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3cbb8-541">Allowed From</span></span>

<span data-ttu-id="3cbb8-542">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3cbb8-542">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="3cbb8-543">예제</span><span class="sxs-lookup"><span data-stu-id="3cbb8-543">Example</span></span>

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```