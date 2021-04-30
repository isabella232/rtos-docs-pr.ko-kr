---
title: 챕터 3 - Azure RTOS NetX Duo PPP(지점 간 프로토콜) 서비스 설명
description: 이 챕터에서는 모든 Azure RTOS NetX Duo PPP 서비스(아래 참조)를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 90c24cad5e595087ba27178243f9dda0dab11029
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810639"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-point-to-point-protocol-ppp-services"></a><span data-ttu-id="97421-103">챕터 3 - Azure RTOS NetX Duo PPP(지점 간 프로토콜) 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="97421-103">Chapter 3 - Description of Azure RTOS NetX Duo Point-to-Point Protocol (PPP) services</span></span>

<span data-ttu-id="97421-104">이 챕터에서는 모든 Azure RTOS NetX Duo PPP 서비스(아래 참조)를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-104">This chapter contains a description of all Azure RTOS NetX Duo PPP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="97421-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="97421-106">**nx_ppp_byte_receive**: *직렬 ISR에서 바이트 수신*</span><span class="sxs-lookup"><span data-stu-id="97421-106">**nx_ppp_byte_receive**: *Receive a byte from serial ISR*</span></span>
- <span data-ttu-id="97421-107">**nx_ppp_chap_challenge**: *CHAP 챌린지 생성*</span><span class="sxs-lookup"><span data-stu-id="97421-107">**nx_ppp_chap_challenge**: *Generate a CHAP challenge*</span></span>
- <span data-ttu-id="97421-108">**nx_ppp_chap_enable**: *CHAP 인증 사용*</span><span class="sxs-lookup"><span data-stu-id="97421-108">**nx_ppp_chap_enable**: *Enable CHAP authentication*</span></span>
- <span data-ttu-id="97421-109">**nx_ppp_create**: *PPP 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="97421-109">**nx_ppp_create**: *Create a PPP instance*</span></span>
- <span data-ttu-id="97421-110">**nx_ppp_delete**: *PPP 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="97421-110">**nx_ppp_delete**: *Delete a PPP instance*</span></span>
- <span data-ttu-id="97421-111">**nx_ppp_dns_address_get**: *DNS 서버 IP 주소 가져오기*</span><span class="sxs-lookup"><span data-stu-id="97421-111">**nx_ppp_dns_address_get**: *Get DNS Server IP address*</span></span>
- <span data-ttu-id="97421-112">**nx_ppp_dns_address_set**: *DNS 서버 IP 주소 설정*</span><span class="sxs-lookup"><span data-stu-id="97421-112">**nx_ppp_dns_address_set**:*Set DNS Server IP address*</span></span>
- <span data-ttu-id="97421-113">**nx_ppp_secondary_dns_address_get**: *보조 DNS 서버 IP 주소 가져오기*</span><span class="sxs-lookup"><span data-stu-id="97421-113">**nx_ppp_secondary_dns_address_get**: *Get Secondary DNS Server IP address*</span></span>
- <span data-ttu-id="97421-114">**nx_ppp_secondary_dns_address_set**: *보조 DNS 서버 IP 주소 설정*</span><span class="sxs-lookup"><span data-stu-id="97421-114">**nx_ppp_secondary_dns_address_set**: *Set Secondary_DNS Server IP address*</span></span>
- <span data-ttu-id="97421-115">**nx_ppp_interface_index_get**: *IP 인터페이스 인덱스 가져오기*</span><span class="sxs-lookup"><span data-stu-id="97421-115">**nx_ppp_interface_index_get**: *Get IP interface index*</span></span>
- <span data-ttu-id="97421-116">**nx_ppp_ip_address_assign**: *IPCP에 대한 IP 주소 할당*</span><span class="sxs-lookup"><span data-stu-id="97421-116">**nx_ppp_ip_address_assign**: *Assign IP addresses for IPCP*</span></span>
- <span data-ttu-id="97421-117">**nx_ppp_link_down_notify**: *연결 해제 시 애플리케이션에 알림*</span><span class="sxs-lookup"><span data-stu-id="97421-117">**nx_ppp_link_down_notify**: *Notify application on link down*</span></span>
- <span data-ttu-id="97421-118">**nx_ppp_link_up_notify**: *연결 사용 시 애플리케이션에 알림*</span><span class="sxs-lookup"><span data-stu-id="97421-118">**nx_ppp_link_up_notify**: *Notify application on link up*</span></span>
- <span data-ttu-id="97421-119">**nx_ppp_nak_authentication_notify**: *인증 NAK가 수신되면 애플리케이션에 알림*</span><span class="sxs-lookup"><span data-stu-id="97421-119">**nx_ppp_nak_authentication_notify**: *Notify application if authentication NAK is received*</span></span>
- <span data-ttu-id="97421-120">**nx_ppp_pap_enable**: *PAP 인증 사용*</span><span class="sxs-lookup"><span data-stu-id="97421-120">**nx_ppp_pap_enable**: *Enable PAP authentication*</span></span>
- <span data-ttu-id="97421-121">**nx_ppp_ping_request**: *LCP 에코 요청 보내기*</span><span class="sxs-lookup"><span data-stu-id="97421-121">**nx_ppp_ping_request**: *Send an LCP echo request*</span></span>
- <span data-ttu-id="97421-122">**nx_ppp_raw_string_send**: *비 PPP 문자열 보내기*</span><span class="sxs-lookup"><span data-stu-id="97421-122">**nx_ppp_raw_string_send**: *Send non PPP string*</span></span>
- <span data-ttu-id="97421-123">**nx_ppp_restart**: *PPP 처리 다시 시작*</span><span class="sxs-lookup"><span data-stu-id="97421-123">**nx_ppp_restart**: *Restart PPP processing*</span></span>
- <span data-ttu-id="97421-124">**nx_ppp_start**: *PPP 처리 시작*</span><span class="sxs-lookup"><span data-stu-id="97421-124">**nx_ppp_start**: *Start PPP processing*</span></span>
- <span data-ttu-id="97421-125">**nx_ppp_status_get**: *현재 PPP 상태 가져오기*</span><span class="sxs-lookup"><span data-stu-id="97421-125">**nx_ppp_status_get**: *Get current PPP status*</span></span>
- <span data-ttu-id="97421-126">**nx_ppp_stop**: *PPP 처리 중지*</span><span class="sxs-lookup"><span data-stu-id="97421-126">**nx_ppp_stop**: *Stop PPP processing*</span></span>
- <span data-ttu-id="97421-127">**nx_ppp_packet_receive**: *PPP 패킷 수신*</span><span class="sxs-lookup"><span data-stu-id="97421-127">**nx_ppp_packet_receive**: *Receive PPP packet*</span></span>
- <span data-ttu-id="97421-128">**nx_ppp_packet_send_set**: *PPP 패킷 전송 함수 설정*</span><span class="sxs-lookup"><span data-stu-id="97421-128">**nx_ppp_packet_send_set**: *Set PPP packet send function*</span></span>

## <a name="nx_ppp_byte_receive"></a><span data-ttu-id="97421-129">nx_ppp_byte_receive</span><span class="sxs-lookup"><span data-stu-id="97421-129">nx_ppp_byte_receive</span></span>

<span data-ttu-id="97421-130">직렬 ISR에서 바이트 수신</span><span class="sxs-lookup"><span data-stu-id="97421-130">Receive a byte from serial ISR</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-131">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-131">Prototype</span></span>

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a><span data-ttu-id="97421-132">설명</span><span class="sxs-lookup"><span data-stu-id="97421-132">Description</span></span>

<span data-ttu-id="97421-133">이 서비스는 일반적으로 수신 바이트를 PPP로 전송하기 위해 애플리케이션의 직렬 드라이버 ISR(인터럽트 서비스 루틴)에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-133">This service is typically called from the application’s serial driver Interrupt Service Routine (ISR) to transfer a received byte to PPP.</span></span> <span data-ttu-id="97421-134">이 루틴은 호출되면 수신 바이트를 순환 바이트 버퍼에 배치하고 처리를 위해 적절한 PPP 스레드에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="97421-134">When called, this routine places the received byte into a circular byte buffer and notifies the appropriate PPP thread for processing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-135">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-135">Input Parameters</span></span>

- <span data-ttu-id="97421-136">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-136">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-137">**byte**: 직렬 디바이스에서 받은 바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-137">**byte**: Byte received from serial device</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-138">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-138">Return Values</span></span>

- <span data-ttu-id="97421-139">**NX_SUCCESS**: (0x00) PPP 바이트를 성공적으로 수신했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-139">**NX_SUCCESS**: (0x00) Successful PPP byte receive.</span></span>
- <span data-ttu-id="97421-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP 직렬 버퍼가 이미 가득 찼습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP serial buffer is already full.</span></span>
- <span data-ttu-id="97421-141">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-141">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-142">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-142">Allowed From</span></span>

<span data-ttu-id="97421-143">스레드, ISR</span><span class="sxs-lookup"><span data-stu-id="97421-143">Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="97421-144">예제</span><span class="sxs-lookup"><span data-stu-id="97421-144">Example</span></span>

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a><span data-ttu-id="97421-145">nx_ppp_chap_challenge</span><span class="sxs-lookup"><span data-stu-id="97421-145">nx_ppp_chap_challenge</span></span>

<span data-ttu-id="97421-146">CHAP 챌린지 생성</span><span class="sxs-lookup"><span data-stu-id="97421-146">Generate a CHAP challenge</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-147">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-147">Prototype</span></span>

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="97421-148">설명</span><span class="sxs-lookup"><span data-stu-id="97421-148">Description</span></span>

<span data-ttu-id="97421-149">이 서비스는 PPP 연결이 이미 설정되고 실행된 후 CHAP 챌린지를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-149">This service initiates a CHAP challenge after the PPP connection is already up and running.</span></span> <span data-ttu-id="97421-150">이렇게 하면 애플리케이션이 정기적으로 연결의 신뢰성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-150">This gives the application the ability to verify the authenticity of the connection on a periodic basis.</span></span> <span data-ttu-id="97421-151">챌린지에 실패하면 PPP 링크가 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="97421-151">If the challenge is unsuccessful, the PPP link is closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-152">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-152">Input Parameters</span></span>

- <span data-ttu-id="97421-153">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-153">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-154">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-154">Return Values</span></span>

- <span data-ttu-id="97421-155">**NX_SUCCESS**: (0x00) PPP 챌린지를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-155">**NX_SUCCESS**: (0x00) Successful PPP challenge initiated.</span></span>
- <span data-ttu-id="97421-156">**NX_PPP_FAILURE**: (0xB0) 잘못된 PPP 챌린지입니다. CHAP가 응답에만 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-156">**NX_PPP_FAILURE**: (0xB0) Invalid PPP challenge, CHAP was enabled only for response.</span></span>
- <span data-ttu-id="97421-157">**NX_NOT_IMPLEMENTED**: (0x80) CHAP 논리가 NX_PPP_DISABLE_CHAP를 통해 사용하지 않도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-157">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="97421-158">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-158">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="97421-159">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-159">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-160">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-160">Allowed From</span></span>

<span data-ttu-id="97421-161">스레드</span><span class="sxs-lookup"><span data-stu-id="97421-161">Threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-162">예제</span><span class="sxs-lookup"><span data-stu-id="97421-162">Example</span></span>

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a><span data-ttu-id="97421-163">nx_ppp_chap_enable</span><span class="sxs-lookup"><span data-stu-id="97421-163">nx_ppp_chap_enable</span></span>

<span data-ttu-id="97421-164">CHAP 인증 사용</span><span class="sxs-lookup"><span data-stu-id="97421-164">Enable CHAP authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-165">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-165">Prototype</span></span>

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a><span data-ttu-id="97421-166">설명</span><span class="sxs-lookup"><span data-stu-id="97421-166">Description</span></span>

<span data-ttu-id="97421-167">이 서비스는 지정된 PPP 인스턴스에 대해 CHAP(Challenge-Handshake 인증 프로토콜)를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-167">This service enables the Challenge-Handshake Authentication Protocol (CHAP) for the specified PPP instance.</span></span>

<span data-ttu-id="97421-168">“\***get_challenge_values** _” 및 “_ \*_get_verification_values_\*\*” 함수 포인터를 지정하는 경우 이 PPP 인스턴스에 CHAP가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-168">If the “\***get_challenge_values**_” and “_\*_get_verification_values_\*\*” function pointers are specified, CHAP is required by this PPP instance.</span></span> <span data-ttu-id="97421-169">그렇지 않으면 CHAP는 피어의 챌린지 요청에만 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-169">Otherwise, CHAP only responds to the peer’s challenge requests.</span></span>

<span data-ttu-id="97421-170">필수 콜백 함수에서 다음과 같은 몇 가지 데이터 항목을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-170">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="97421-171">데이터 항목 *secret*, *name* 및 *system* 은 최대 크기가 NX_PPP_NAME_SIZE-1인 NULL로 종료되는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-171">The data items *secret*, *name*, and *system* are expected to be NULL-terminated strings with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="97421-172">데이터 항목 *rand_value* 는 최대 크기가 NX_PPP_VALUE_SIZE-1인 NULL로 종료되는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-172">The data item *rand_value* is expected to be a NULL-terminated string with a maximum size of NX_PPP_VALUE_SIZE-1.</span></span> <span data-ttu-id="97421-173">데이터 항목 *id* 는 단순 부호 없는 문자 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-173">The data item *id* is a simple unsigned character type.</span></span>

>[!NOTE]
> <span data-ttu-id="97421-174">이 함수는 *nx_ppp_create* 이후, nx_ip_create 또는 *nx_ip_interface_attach* 이전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-174">This function must be called after *nx_ppp_create* but before nx_ip_create or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-175">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-175">Input Parameters</span></span>

- <span data-ttu-id="97421-176">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-176">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-177">**get_challenge_values**: 챌린지에 사용되는 값을 검색하는 애플리케이션 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-177">**get_challenge_values**: Pointer to application function to retrieve values used for the challenge.</span></span> <span data-ttu-id="97421-178">*rand_value*, *id* 및 *secret* 값을 제공된 대상에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-178">Note that the *rand_value*, *id*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="97421-179">**get_responder_values**: 챌린지에 응답하는 데 사용되는 값을 검색하는 애플리케이션 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-179">**get_responder_values**: Pointer to application function that retrieves values used to respond to a challenge.</span></span> <span data-ttu-id="97421-180">*system*, *name* 및 *secret* 값을 제공된 대상에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-180">Note that the *system*, *name*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="97421-181">**get_verification_values**: 챌린지 응답을 확인하는 데 사용된 값을 검색하는 애플리케이션 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-181">**get_verification_values**: Pointer to application function that retrieves values used to verify the challenge response.</span></span> <span data-ttu-id="97421-182">*system*, *name* 및 *secret* 값을 제공된 대상에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-182">Note that the *system*,*name*, and *secret* values must be copied into the supplied destinations.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-183">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-183">Return Values</span></span>

- <span data-ttu-id="97421-184">**NX_SUCCESS**: (0x00) PPP CHAP를 성공적으로 사용하도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-184">**NX_SUCCESS**: (0x00) Successful PPP CHAP enable</span></span>
- <span data-ttu-id="97421-185">**NX_NOT_IMPLEMENTED**: (0x80) CHAP 논리가 NX_PPP_DISABLE_CHAP를 통해 사용하지 않도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-185">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="97421-186">NX_PTR_ERROR: (0x07) PPP 포인터나 콜백 함수 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-186">NX_PTR_ERROR: (0x07) Invalid PPP pointer or callback function pointer.</span></span> <span data-ttu-id="97421-187">*get_challenge_values* 가 지정된 경우 *get_verification_values* 함수도 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-187">Note that if *get_challenge_values* is specified, then the *get_verification_values* function must also be supplied.</span></span>
- <span data-ttu-id="97421-188">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-188">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-189">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-189">Allowed From</span></span>

<span data-ttu-id="97421-190">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="97421-190">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-191">예제</span><span class="sxs-lookup"><span data-stu-id="97421-191">Example</span></span>

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
## <a name="nx_ppp_create"></a><span data-ttu-id="97421-192">nx_ppp_create</span><span class="sxs-lookup"><span data-stu-id="97421-192">nx_ppp_create</span></span>

<span data-ttu-id="97421-193">PPP 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="97421-193">Create a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-194">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-194">Prototype</span></span>

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a><span data-ttu-id="97421-195">설명</span><span class="sxs-lookup"><span data-stu-id="97421-195">Description</span></span>

<span data-ttu-id="97421-196">이 서비스는 지정된 NetX IP 인스턴스에 대한 PPP 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97421-196">This service creates a PPP instance for the specified NetX IP instance.</span></span> <span data-ttu-id="97421-197">NetX IP 인스턴스를 만들기 전에 이 함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-197">This function must be called prior to creating the NetX IP instance.</span></span>

>[!NOTE]
> <span data-ttu-id="97421-198">일반적으로는 PPP 스레드 우선 순위보다 우선 순위가 높은 NetX IP 스레드를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-198">It is generally a good idea to create the NetX IP thread at a higher priority than the PPP thread priority.</span></span> <span data-ttu-id="97421-199">IP 스레드 우선 순위를 지정하는 방법에 대한 자세한 내용은 *nx_ip_create* 서비스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97421-199">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-200">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-200">Input Parameters</span></span>

- <span data-ttu-id="97421-201">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-201">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-202">**name**: 이 PPP 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-202">**name**: Name of this PPP instance.</span></span>
- <span data-ttu-id="97421-203">**ip_ptr**: 아직 생성되지 않은 IP 인스턴스의 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-203">**ip_ptr**: Pointer to control block for not-yet-created IP instance.</span></span>
- <span data-ttu-id="97421-204">**stack_memory_ptr**: PPP 스레드의 스택 영역 시작에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-204">**stack_memory_ptr**: Pointer to start of PPP thread’s stack area.</span></span>
- <span data-ttu-id="97421-205">**stack_size** 스레드 스택의 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-205">**stack_size**: Size in bytes in the thread’s stack.</span></span>
- <span data-ttu-id="97421-206">**pool_ptr** 기본 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-206">**pool_ptr**: Pointer to default packet pool.</span></span>
- <span data-ttu-id="97421-207">**thread_priority**: 내부 PPP 스레드의 우선 순위(1-31)입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-207">**thread_priority**: Priority of internal PPP threads (1-31).</span></span>
- <span data-ttu-id="97421-208">**ppp_invalid_packet_handler**: 모든 비 PPP 패킷에 대한 애플리케이션 처리기에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-208">**ppp_invalid_packet_handler**: Function pointer to application’s handler for all non-PPP packets.</span></span> <span data-ttu-id="97421-209">NetX PPP는 일반적으로 초기화하는 동안 이 루틴을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-209">The NetX PPP typically calls this routine during initialization.</span></span> <span data-ttu-id="97421-210">애플리케이션이 모뎀 명령에 응답하거나 Windows XP의 경우 NetX PPP 애플리케이션이 Windows XP에서 전송하는 초기 "클라이언트"에 "클라이언트 서버"로 응답하여 PPP를 시작할 수 있는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-210">This is where the application can respond to modem commands or in the case of Windows XP, the NetX PPP application can initiate PPP by responding with“ CLIENT SERVER” to the initial “CLIENT” sent by Windows XP.</span></span>
- <span data-ttu-id="97421-211">**ppp_byte_send**: 애플리케이션의 직렬 바이트 출력 루틴에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-211">**ppp_byte_send**: Function pointer to application’s serial byte output routine.</span></span>


### <a name="return-values"></a><span data-ttu-id="97421-212">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-212">Return Values</span></span>

- <span data-ttu-id="97421-213">**NX_SUCCESS**: (0x00) PPP를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-213">**NX_SUCCESS**: (0x00) Successful PPP create.</span></span>
- <span data-ttu-id="97421-214">NX_PTR_ERROR: (0x07) 잘못된 PPP, IP 또는 바이트 출력 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-214">NX_PTR_ERROR: (0x07) Invalid PPP, IP, or byte output function pointer.</span></span>
- <span data-ttu-id="97421-215">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-216">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-216">Allowed From</span></span>

<span data-ttu-id="97421-217">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="97421-217">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-218">예제</span><span class="sxs-lookup"><span data-stu-id="97421-218">Example</span></span>

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a><span data-ttu-id="97421-219">nx_ppp_delete</span><span class="sxs-lookup"><span data-stu-id="97421-219">nx_ppp_delete</span></span>

<span data-ttu-id="97421-220">PPP 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="97421-220">Delete a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-221">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-221">Prototype</span></span>

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="97421-222">설명</span><span class="sxs-lookup"><span data-stu-id="97421-222">Description</span></span>

<span data-ttu-id="97421-223">이 서비스는 이전에 만든 PPP 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-223">This service deletes the previously created PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-224">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-224">Input Parameters</span></span>

- <span data-ttu-id="97421-225">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-225">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-226">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-226">Return Values</span></span>

- <span data-ttu-id="97421-227">**NX_SUCCESS**: (0x00) PPP를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-227">**NX_SUCCESS**: (0x00) Successful PPP deletion.</span></span>
- <span data-ttu-id="97421-228">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-228">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="97421-229">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-229">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-230">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-230">Allowed From</span></span>

<span data-ttu-id="97421-231">스레드</span><span class="sxs-lookup"><span data-stu-id="97421-231">Threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-232">예제</span><span class="sxs-lookup"><span data-stu-id="97421-232">Example</span></span>

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a><span data-ttu-id="97421-233">nx_ppp_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="97421-233">nx_ppp_dns_address_get</span></span>

<span data-ttu-id="97421-234">DNS 서버 IP 주소 가져오기</span><span class="sxs-lookup"><span data-stu-id="97421-234">Get DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-235">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-235">Prototype</span></span>

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="97421-236">설명</span><span class="sxs-lookup"><span data-stu-id="97421-236">Description</span></span>

<span data-ttu-id="97421-237">이 서비스는 IPCP 핸드셰이크의 피어에서 제공한 DNS IP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-237">This service retrieves the DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="97421-238">피어가 IP 주소를 제공하지 않은 경우 IP 주소 0이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-238">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-239">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-239">Input Parameters</span></span>

- <span data-ttu-id="97421-240">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-240">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-241">**dns_address_ptr**: DNS 서버 주소의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-241">**dns_address_ptr**: Destination for DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-242">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-242">Return Values</span></span>

- <span data-ttu-id="97421-243">**NX_SUCCESS**: (0x00) DNS 주소를 성공적으로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-243">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="97421-244">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어와 협상을 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-244">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="97421-245">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-245">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-246">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-246">Allowed From</span></span>

<span data-ttu-id="97421-247">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="97421-247">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="97421-248">예제</span><span class="sxs-lookup"><span data-stu-id="97421-248">Example</span></span>

```c

ULONG  my_dns_address;

/* Get DNS Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a><span data-ttu-id="97421-249">nx_ppp_secondary_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="97421-249">nx_ppp_secondary_dns_address_get</span></span>

<span data-ttu-id="97421-250">보조 DNS 서버 IP 주소 가져오기</span><span class="sxs-lookup"><span data-stu-id="97421-250">Get Secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-251">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-251">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="97421-252">설명</span><span class="sxs-lookup"><span data-stu-id="97421-252">Description</span></span>

<span data-ttu-id="97421-253">이 서비스는 IPCP 핸드셰이크의 피어에서 제공한 보조 DNS IP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-253">This service retrieves the secondary DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="97421-254">피어가 IP 주소를 제공하지 않은 경우 IP 주소 0이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-254">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-255">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-255">Input Parameters</span></span>

- <span data-ttu-id="97421-256">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-256">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-257">**dns_address_ptr**: 보조 DNS 서버 주소의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-257">**dns_address_ptr**: Destination for Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-258">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-258">Return Values</span></span>

- <span data-ttu-id="97421-259">**NX_SUCCESS**: (0x00) DNS 주소를 성공적으로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-259">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="97421-260">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어와 협상을 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-260">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="97421-261">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-261">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-262">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-262">Allowed From</span></span>

<span data-ttu-id="97421-263">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="97421-263">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="97421-264">예제</span><span class="sxs-lookup"><span data-stu-id="97421-264">Example</span></span>

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a><span data-ttu-id="97421-265">nx_ppp_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="97421-265">nx_ppp_dns_address_set</span></span>

<span data-ttu-id="97421-266">주 DNS 서버 IP 주소 설정</span><span class="sxs-lookup"><span data-stu-id="97421-266">Set primary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-267">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-267">Prototype</span></span>

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="97421-268">설명</span><span class="sxs-lookup"><span data-stu-id="97421-268">Description</span></span>

<span data-ttu-id="97421-269">이 서비스는 DNS 서버 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-269">This service sets the DNS Server IP address.</span></span> <span data-ttu-id="97421-270">피어가 IPCP 상태에서 DNS 서버 옵션 요청을 보내면 이 호스트가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-270">If the peer sends a DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-271">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-271">Input Parameters</span></span>

- <span data-ttu-id="97421-272">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-272">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-273">**dns_address**: DNS 서버 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-273">**dns_address**: DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-274">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-274">Return Values</span></span>

- <span data-ttu-id="97421-275">**NX_SUCCESS**: (0x00) DNS 주소를 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-275">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span>
- <span data-ttu-id="97421-276">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어와 협상을 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-276">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="97421-277">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-277">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-278">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-278">Allowed From</span></span>

<span data-ttu-id="97421-279">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="97421-279">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-280">예제</span><span class="sxs-lookup"><span data-stu-id="97421-280">Example</span></span>

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a><span data-ttu-id="97421-281">nx_ppp_secondary_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="97421-281">nx_ppp_secondary_dns_address_set</span></span>

<span data-ttu-id="97421-282">보조 DNS 서버 IP 주소 설정</span><span class="sxs-lookup"><span data-stu-id="97421-282">Set secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-283">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-283">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="97421-284">설명</span><span class="sxs-lookup"><span data-stu-id="97421-284">Description</span></span>

<span data-ttu-id="97421-285">이 서비스는 보조 DNS 서버 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-285">This service sets the secondary DNS Server IP address.</span></span> <span data-ttu-id="97421-286">피어가 IPCP 상태에서 보조 DNS 서버 옵션 요청을 보내면 이 호스트가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-286">If the peer sends a secondary DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-287">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-287">Input Parameters</span></span>

- <span data-ttu-id="97421-288">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-288">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-289">**dns_address**: 보조 DNS 서버 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-289">**dns_address**: Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-290">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-290">Return Values</span></span>

- <span data-ttu-id="97421-291">**NX_SUCCESS**: (0x00) DNS 주소를 성공적으로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-291">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span> 
- <span data-ttu-id="97421-292">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어와 협상을 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-292">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="97421-293">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-293">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-294">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-294">Allowed From</span></span>

<span data-ttu-id="97421-295">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="97421-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-296">예제</span><span class="sxs-lookup"><span data-stu-id="97421-296">Example</span></span>

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a><span data-ttu-id="97421-297">nx_ppp_interface_index_get</span><span class="sxs-lookup"><span data-stu-id="97421-297">nx_ppp_interface_index_get</span></span>

<span data-ttu-id="97421-298">IP 인터페이스 인덱스 가져오기</span><span class="sxs-lookup"><span data-stu-id="97421-298">Get IP interface index</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-299">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-299">Prototype</span></span>

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a><span data-ttu-id="97421-300">설명</span><span class="sxs-lookup"><span data-stu-id="97421-300">Description</span></span>

<span data-ttu-id="97421-301">이 서비스는 이 PPP 인스턴스와 연결된 IP 인터페이스 인덱스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-301">This service retrieves the IP interface index associated with this PPP instance.</span></span> <span data-ttu-id="97421-302">이는 PPP 인스턴스가 IP 인스턴스의 기본 인터페이스가 아닌 경우에만 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-302">This is only useful when the PPP instance is not the primary interface of an IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-303">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-303">Input Parameters</span></span>

- <span data-ttu-id="97421-304">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-304">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-305">**index_ptr**: 인터페이스 인덱스의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-305">**index_ptr**: Destination for interface index</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-306">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-306">Return Values</span></span>

- <span data-ttu-id="97421-307">**NX_SUCCESS**: (0x00) PPP 인덱스를 성공적으로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-307">**NX_SUCCESS**: (0x00) Successful PPP index get.</span></span>
- <span data-ttu-id="97421-308">**NX_IN_PROGRESS**: (0x37) PPP가 초기화를 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-308">**NX_IN_PROGRESS**: (0x37) PPP has not completed initialization.</span></span>
- <span data-ttu-id="97421-309">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-309">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-310">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-310">Allowed From</span></span>

<span data-ttu-id="97421-311">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="97421-311">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-312">예제</span><span class="sxs-lookup"><span data-stu-id="97421-312">Example</span></span>

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a><span data-ttu-id="97421-313">nx_ppp_ip_address_assign</span><span class="sxs-lookup"><span data-stu-id="97421-313">nx_ppp_ip_address_assign</span></span>

<span data-ttu-id="97421-314">IPCP에 대한 IP 주소 할당</span><span class="sxs-lookup"><span data-stu-id="97421-314">Assign IP addresses for IPCP</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-315">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-315">Prototype</span></span>

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a><span data-ttu-id="97421-316">설명</span><span class="sxs-lookup"><span data-stu-id="97421-316">Description</span></span>

<span data-ttu-id="97421-317">이 서비스는 IPCP(인터넷 프로토콜 제어 프로토콜)에서 사용할 로컬 및 피어 IP 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-317">This service sets up the local and peer IP addresses for use in the Internet Protocol Control Protocol (IPCP.</span></span> <span data-ttu-id="97421-318">자체 및 다른 피어에 대한 유효한 IP 주소가 있는 PPP 인스턴스를 대상으로 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-318">It should be called for the PPP instance that has valid IP addresses for itself and the other peer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-319">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-319">Input Parameters</span></span>

- <span data-ttu-id="97421-320">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-320">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-321">**local_ip_address** 로컬 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-321">**local_ip_address**: Local IP address.</span></span>
- <span data-ttu-id="97421-322">**peer_ip_address**: 피어의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-322">**peer_ip_address**: Peer’s IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-323">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-323">Return Values</span></span>

- <span data-ttu-id="97421-324">**NX_SUCCESS**: (0x00) PPP 주소를 성공적으로 할당했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-324">**NX_SUCCESS**: (0x00) Successful PPP address assignment.</span></span>
- <span data-ttu-id="97421-325">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-325">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="97421-326">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-327">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-327">Allowed From</span></span>

<span data-ttu-id="97421-328">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="97421-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-329">예제</span><span class="sxs-lookup"><span data-stu-id="97421-329">Example</span></span>

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a><span data-ttu-id="97421-330">nx_ppp_link_down_notify</span><span class="sxs-lookup"><span data-stu-id="97421-330">nx_ppp_link_down_notify</span></span>

<span data-ttu-id="97421-331">연결 해제 시 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="97421-331">Notify application on link down</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-332">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-332">Prototype</span></span>

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a><span data-ttu-id="97421-333">설명</span><span class="sxs-lookup"><span data-stu-id="97421-333">Description</span></span>

<span data-ttu-id="97421-334">이 서비스는 지정된 PPP 인스턴스에 애플리케이션의 연결 해제 알림 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-334">This service registers the application’s link down notification callback with the specified PPP instance.</span></span> <span data-ttu-id="97421-335">NULL이 아닌 경우 연결이 해제될 때마다 애플리케이션의 연결 해제 콜백 함수가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-335">If non-NULL, the application’s link down callback function is called whenever the link goes down.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-336">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-336">Input Parameters</span></span>

- <span data-ttu-id="97421-337">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-337">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-338">**link_down_callback**: 애플리케이션의 연결 해제 알림 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-338">**link_down_callback**: Application’s link down notification function pointer.</span></span> <span data-ttu-id="97421-339">NULL인 경우 연결 해제 알림이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-339">If NULL, link down notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-340">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-340">Return Values</span></span>

- <span data-ttu-id="97421-341">**NX_SUCCESS**: (0x00) 연결 해제 알림 콜백을 성공적으로 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-341">**NX_SUCCESS**: (0x00) Successful link down notification callback registration.</span></span>
- <span data-ttu-id="97421-342">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-342">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-343">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-343">Allowed From</span></span>

<span data-ttu-id="97421-344">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="97421-344">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="97421-345">예제</span><span class="sxs-lookup"><span data-stu-id="97421-345">Example</span></span>

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
## <a name="nx_ppp_link_up_notify"></a><span data-ttu-id="97421-346">nx_ppp_link_up_notify</span><span class="sxs-lookup"><span data-stu-id="97421-346">nx_ppp_link_up_notify</span></span>

<span data-ttu-id="97421-347">연결 사용 시 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="97421-347">Notify application on link up</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-348">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-348">Prototype</span></span>

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a><span data-ttu-id="97421-349">설명</span><span class="sxs-lookup"><span data-stu-id="97421-349">Description</span></span>

<span data-ttu-id="97421-350">이 서비스는 지정된 PPP 인스턴스에 애플리케이션의 연결 사용 알림 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-350">This service registers the application’s link up notification callback with the specified PPP instance.</span></span> <span data-ttu-id="97421-351">NULL이 아닌 경우 연결이 사용될 때마다 애플리케이션의 연결 사용 콜백 함수가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-351">If non-NULL, the application’s link up callback function is called whenever the link comes up.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-352">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-352">Input Parameters</span></span>

- <span data-ttu-id="97421-353">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-353">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-354">**link_up_callback**: 애플리케이션의 연결 사용 알림 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-354">**link_up_callback**: Application’s link up notification function pointer.</span></span> <span data-ttu-id="97421-355">NULL인 경우 연결 사용 알림이 사용되지 않습니다.\*\*</span><span class="sxs-lookup"><span data-stu-id="97421-355">If NULL, link up notification is disabled.\*\*</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-356">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-356">Return Values</span></span>

- <span data-ttu-id="97421-357">**NX_SUCCESS**: (0x00) 연결 사용 알림 콜백을 성공적으로 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-357">**NX_SUCCESS**: (0x00) Successful link up notification callback registration.</span></span>
- <span data-ttu-id="97421-358">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-358">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-359">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-359">Allowed From</span></span>

<span data-ttu-id="97421-360">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="97421-360">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="97421-361">예제</span><span class="sxs-lookup"><span data-stu-id="97421-361">Example</span></span>

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

## <a name="nx_ppp_nak_authentication_notify"></a><span data-ttu-id="97421-362">nx_ppp_nak_authentication_notify</span><span class="sxs-lookup"><span data-stu-id="97421-362">nx_ppp_nak_authentication_notify</span></span>

<span data-ttu-id="97421-363">인증 NAK가 수신되면 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="97421-363">Notify application if authentication NAK received</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-364">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-364">Prototype</span></span>

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a><span data-ttu-id="97421-365">설명</span><span class="sxs-lookup"><span data-stu-id="97421-365">Description</span></span>

<span data-ttu-id="97421-366">이 서비스는 지정된 PPP 인스턴스에 애플리케이션의 인증 nak 알림 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-366">This service registers the application’s authentication nak notification callback with the specified PPP instance.</span></span> <span data-ttu-id="97421-367">NULL이 아닌 경우 이 콜백 함수는 PPP 인스턴스가 인증 중에 NAK를 받을 때마다 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-367">If non-NULL, this callback function is called whenever the PPP instance receives a NAK during authentiaction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-368">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-368">Input Parameters</span></span>

- <span data-ttu-id="97421-369">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-369">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-370">**nak_authentication_notify**: PPP 인스턴스가 인증 NAK를 받을 때 호출되는 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-370">**nak_authentication_notify**: Pointer to function called when the PPP instance receives an authentication NAK.</span></span> <span data-ttu-id="97421-371">NULL인 경우 알림이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-371">If NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-372">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-372">Return Values</span></span>

- <span data-ttu-id="97421-373">**NX_SUCCESS**: (0x00) 알림 콜백을 성공적으로 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-373">**NX_SUCCESS**: (0x00) Successful notification callback registration.</span></span>
- <span data-ttu-id="97421-374">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-374">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-375">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-375">Allowed From</span></span>

<span data-ttu-id="97421-376">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="97421-376">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="97421-377">예제</span><span class="sxs-lookup"><span data-stu-id="97421-377">Example</span></span>

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

## <a name="nx_ppp_pap_enable"></a><span data-ttu-id="97421-378">nx_ppp_pap_enable</span><span class="sxs-lookup"><span data-stu-id="97421-378">nx_ppp_pap_enable</span></span>

<span data-ttu-id="97421-379">PAP 인증 사용</span><span class="sxs-lookup"><span data-stu-id="97421-379">Enable PAP Authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-380">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-380">Prototype</span></span>

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a><span data-ttu-id="97421-381">설명</span><span class="sxs-lookup"><span data-stu-id="97421-381">Description</span></span>

<span data-ttu-id="97421-382">이 서비스는 지정된 PPP 인스턴스에 PAP(암호 인증 프로토콜)를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-382">This service enables the Password Authentication Protocol (PAP) for the specified PPP instance.</span></span> <span data-ttu-id="97421-383">"***verify_login***" 함수 포인터를 지정하는 경우 이 PPP 인스턴스에 PAP가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-383">If the “***verify_login***” function pointer is specified, PAP is required by this PPP instance.</span></span> <span data-ttu-id="97421-384">그렇지 않으면 PAP는 LCP 협상 중에 지정된 피어의 PAP 요구 사항에만 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-384">Otherwise, PAP only responds to the peer’s PAP requirements as specified during LCP negotiation.</span></span>

<span data-ttu-id="97421-385">필수 콜백 함수에서 다음과 같은 몇 가지 데이터 항목을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-385">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="97421-386">데이터 항목 *name* 은 최대 크기가 NX_PPP_NAME_SIZE-1인 NULL로 종료되는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-386">The data item *name* is expected to be NULL-terminated string with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="97421-387">데이터 항목 *password* 는 최대 크기가 NX_PPP_PASSWORD_SIZE-1인 NULL로 종료되는 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-387">The data item *password* is also expected to be a NULL-terminated string with a maximum size of NX_PPP_PASSWORD_SIZE-1.</span></span>

>[!NOTE]
> <span data-ttu-id="97421-388">이 함수는 *nx_ppp_create* 이후, *nx_ip_create* 또는 *nx_ip_interface_attach* 이전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-388">This function must be called after *nx_ppp_create* but before *nx_ip_create* or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-389">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-389">Input Parameters</span></span>

- <span data-ttu-id="97421-390">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-390">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-391">**generate_login**: 피어에서 인증을 위한 *name* 및 *password* 를 생성하는 애플리케이션 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-391">**generate_login**: Pointer to application function that produces a *name* and *password* for authentication by the peer.</span></span> <span data-ttu-id="97421-392">*name* 및 *password* 값을 제공된 대상에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-392">Note that the *name* and *password* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="97421-393">**verify_login**: 피어에서 제공한 *name* 및 *password* 를 확인하는 애플리케이션 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-393">**verify_login**: Pointer to application function that verifies the *name* and *password* supplied by the peer.</span></span> <span data-ttu-id="97421-394">이 루틴은 제공된 *name* 및 *password* 를 비교해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-394">This routine must compare the supplied *name* and *password*.</span></span> <span data-ttu-id="97421-395">이 루틴이 NX_SUCCESS를 반환하는 경우 name 및 password가 올바른 것이며, PPP가 다음 단계로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-395">If this routine returns NX_SUCCESS, the name and password are correct and PPP can proceed to the next step.</span></span> <span data-ttu-id="97421-396">그렇지 않으면 이 루틴은 NX_PPP_ERROR를 반환하고 PPP는 다른 이름과 암호를 기다리기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-396">Otherwise, this routine returns NX_PPP_ERROR and PPP simply waits for another name and password.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-397">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-397">Return Values</span></span>

- <span data-ttu-id="97421-398">**NX_SUCCESS**: (0x00) PPP PAP를 성공적으로 사용하도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-398">**NX_SUCCESS**: (0x00) Successful PPP PAP enable.</span></span>
- <span data-ttu-id="97421-399">**NX_NOT_IMPLEMENTED**: (0x80) PAP 논리가 NX_PPP_DISABLE_PAP를 통해 사용하지 않도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-399">**NX_NOT_IMPLEMENTED**: (0x80) PAP logic was disabled via NX_PPP_DISABLE_PAP.</span></span>
- <span data-ttu-id="97421-400">NX_PTR_ERROR: (0x07) PPP 포인터나 애플리케이션 함수 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-400">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="97421-401">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-401">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-402">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-402">Allowed From</span></span>

<span data-ttu-id="97421-403">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="97421-403">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-404">예제</span><span class="sxs-lookup"><span data-stu-id="97421-404">Example</span></span>

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

## <a name="nx_ppp_ping_request"></a><span data-ttu-id="97421-405">nx_ppp_ping_request</span><span class="sxs-lookup"><span data-stu-id="97421-405">nx_ppp_ping_request</span></span>

<span data-ttu-id="97421-406">LCP ping 요청 보내기</span><span class="sxs-lookup"><span data-stu-id="97421-406">Send an LCP ping request</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-407">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-407">Prototype</span></span>

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a><span data-ttu-id="97421-408">설명</span><span class="sxs-lookup"><span data-stu-id="97421-408">Description</span></span>

<span data-ttu-id="97421-409">이 서비스는 LCP 요청을 보내고 PPP 디바이스가 에코 응답을 기다리고 있다는 플래그를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-409">This service sends an LCP request and sets a flag that the PPP device is waiting for an echo response.</span></span> <span data-ttu-id="97421-410">대기 옵션은 주로 *nx_packet_allocate* 호출과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-410">The wait option is primarily for the *nx_packet_allocate* call.</span></span> <span data-ttu-id="97421-411">이 서비스는 요청이 전송되는 즉시 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-411">The service returns as soon as the request is sent.</span></span> <span data-ttu-id="97421-412">응답을 기다리지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-412">It does not wait for a response.</span></span> 

<span data-ttu-id="97421-413">일치하는 에코 응답이 수신되면 PPP 스레드 태스크가 플래그를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="97421-413">When a matching echo response is received, the PPP thread task will clear the flag.</span></span> <span data-ttu-id="97421-414">PPP 디바이스는 PPP 협상의 LCP 부분을 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-414">The PPP device must have completed the LCP part of the PPP negotiation.</span></span>

<span data-ttu-id="97421-415">이 서비스는 링크 상태에 대한 하드웨어 폴링을 쉽게 수행할 수 없는 PPP 설정에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-415">This service is useful for PPP set ups where polling the hardware for link status may not be readily possible.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-416">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-416">Input Parameters</span></span>

- <span data-ttu-id="97421-417">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-417">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-418">**data**: 에코 요청에서 보낼 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-418">**data**: Pointer to data to send in echo request.</span></span>
- <span data-ttu-id="97421-419">**data_size**: LCP 에코 메시지를 보내기 위해 대기하는 wait_option 시간을 보낼 데이터의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-419">**data_size**: Size of data to send wait_option Time to wait to send the LCP echo message.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-420">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-420">Return Values</span></span>

- <span data-ttu-id="97421-421">**NX_SUCCESS**: (0x00) 에코 요청을 성공적으로 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-421">**NX_SUCCESS**: (0x00) Successful sent echo request.</span></span>
- <span data-ttu-id="97421-422">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP 연결이 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-422">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP connection not established.</span></span>
- <span data-ttu-id="97421-423">NX_PTR_ERROR: (0x07) PPP 포인터나 애플리케이션 함수 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-423">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="97421-424">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-424">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-425">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-425">Allowed From</span></span>

<span data-ttu-id="97421-426">애플리케이션 스레드</span><span class="sxs-lookup"><span data-stu-id="97421-426">Application threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-427">예제</span><span class="sxs-lookup"><span data-stu-id="97421-427">Example</span></span>

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  sizeof("username ") - 1;

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

## <a name="nx_ppp_raw_string_send"></a><span data-ttu-id="97421-428">nx_ppp_raw_string_send</span><span class="sxs-lookup"><span data-stu-id="97421-428">nx_ppp_raw_string_send</span></span>

<span data-ttu-id="97421-429">원시 ASCII 문자열 보내기</span><span class="sxs-lookup"><span data-stu-id="97421-429">Send a raw ASCII string</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-430">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-430">Prototype</span></span>

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a><span data-ttu-id="97421-431">설명</span><span class="sxs-lookup"><span data-stu-id="97421-431">Description</span></span>

<span data-ttu-id="97421-432">이 서비스는 PPP 인터페이스가 아닌 비 PPP ASCII 문자열을 직접 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="97421-432">This service sends a non-PPP ASCII string directly out the PPP interface.</span></span> <span data-ttu-id="97421-433">이는 일반적으로 PPP가 모뎀 제어 정보를 포함하는 비 PPP 패킷을 수신한 후에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-433">It is typically used after PPP receives an non-PPP packet that contains modem control information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-434">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-434">Input Parameters</span></span>

- <span data-ttu-id="97421-435">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-435">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-436">**string_ptr**: 보낼 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-436">**string_ptr**: Pointer to string to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-437">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-437">Return Values</span></span>

- <span data-ttu-id="97421-438">**NX_SUCCESS**: (0x00) PPP 원시 문자열을 성공적으로 보냈습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-438">**NX_SUCCESS**: (0x00) Successful PPP raw string send.</span></span>
- <span data-ttu-id="97421-439">NX_PTR_ERROR: (0x07) PPP 포인터나 문자열 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-439">NX_PTR_ERROR: (0x07) Invalid PPP pointer or string pointer.</span></span>
- <span data-ttu-id="97421-440">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-440">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-441">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-441">Allowed From</span></span>

<span data-ttu-id="97421-442">스레드</span><span class="sxs-lookup"><span data-stu-id="97421-442">Threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-443">예제</span><span class="sxs-lookup"><span data-stu-id="97421-443">Example</span></span>

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a><span data-ttu-id="97421-444">nx_ppp_restart</span><span class="sxs-lookup"><span data-stu-id="97421-444">nx_ppp_restart</span></span>

<span data-ttu-id="97421-445">PPP 처리 다시 시작</span><span class="sxs-lookup"><span data-stu-id="97421-445">Restart PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-446">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-446">Prototype</span></span>

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="97421-447">설명</span><span class="sxs-lookup"><span data-stu-id="97421-447">Description</span></span>

<span data-ttu-id="97421-448">이 서비스는 PPP 처리를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-448">This service restarts the PPP processing.</span></span> <span data-ttu-id="97421-449">일반적으로 연결 해제 콜백 또는 통신이 끊겼음을 알리는 비 PPP 모뎀 메시지로 인해 연결을 다시 설정해야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-449">It is typically called when the link needs to be re-established either from a link down callback or by a non-PPP modem message indicating communication was lost.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-450">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-450">Input Parameters</span></span>

- <span data-ttu-id="97421-451">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-451">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-452">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-452">Return Values</span></span>

- <span data-ttu-id="97421-453">**NX_SUCCESS**: (0x00) PPP 다시 시작이 성공적으로 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-453">**NX_SUCCESS**: (0x00) Successful PPP restart initiated.</span></span>
- <span data-ttu-id="97421-454">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-454">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="97421-455">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-455">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-456">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-456">Allowed From</span></span>

<span data-ttu-id="97421-457">스레드</span><span class="sxs-lookup"><span data-stu-id="97421-457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-458">예제</span><span class="sxs-lookup"><span data-stu-id="97421-458">Example</span></span>

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a><span data-ttu-id="97421-459">nx_ppp_start</span><span class="sxs-lookup"><span data-stu-id="97421-459">nx_ppp_start</span></span>

<span data-ttu-id="97421-460">PPP 처리 시작</span><span class="sxs-lookup"><span data-stu-id="97421-460">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-461">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-461">Prototype</span></span>

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="97421-462">설명</span><span class="sxs-lookup"><span data-stu-id="97421-462">Description</span></span>

<span data-ttu-id="97421-463">이 서비스는 PPP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-463">This service starts the PPP processing.</span></span> <span data-ttu-id="97421-464">일반적으로 nx_ppp_stop()을 호출한 후에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-464">It is typically called after nx_ppp_stop() called.</span></span>

>[!NOTE]
> <span data-ttu-id="97421-465">연결이 설정되면 PPP가 자동으로 PPP 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-465">PPP automatically starts the PPP processing when the link is enabled.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-466">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-466">Input Parameters</span></span>

- <span data-ttu-id="97421-467">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-467">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-468">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-468">Return Values</span></span>

- <span data-ttu-id="97421-469">**NX_SUCCESS**: (0x00) PPP 시작이 성공적으로 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-469">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="97421-470">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP가 이미 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-470">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP already started.</span></span>
- <span data-ttu-id="97421-471">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-471">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="97421-472">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-472">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-473">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-473">Allowed From</span></span>

<span data-ttu-id="97421-474">스레드</span><span class="sxs-lookup"><span data-stu-id="97421-474">Threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-475">예제</span><span class="sxs-lookup"><span data-stu-id="97421-475">Example</span></span>

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a><span data-ttu-id="97421-476">nx_ppp_status_get</span><span class="sxs-lookup"><span data-stu-id="97421-476">nx_ppp_status_get</span></span>

<span data-ttu-id="97421-477">현재 PPP 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="97421-477">Get current PPP status</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-478">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-478">Prototype</span></span>

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a><span data-ttu-id="97421-479">설명</span><span class="sxs-lookup"><span data-stu-id="97421-479">Description</span></span>

<span data-ttu-id="97421-480">이 서비스는 지정된 PPP 인스턴스의 현재 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="97421-480">This service gets the current status of the specified PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-481">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-481">Input Parameters</span></span>

- <span data-ttu-id="97421-482">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-482">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-483">**status_ptr**: PPP 상태의 대상입니다. 가능한 상태 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-483">**status_ptr**: Destination for the PPP status, the following are possible status values:</span></span>
    - <span data-ttu-id="97421-484">**NX_PPP_STATUS_ESTABLISHED**</span><span class="sxs-lookup"><span data-stu-id="97421-484">**NX_PPP_STATUS_ESTABLISHED**</span></span>
    - <span data-ttu-id="97421-485">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="97421-485">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="97421-486">**NX_PPP_STATUS_LCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="97421-486">**NX_PPP_STATUS_LCP_FAILED**</span></span>
    - <span data-ttu-id="97421-487">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="97421-487">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="97421-488">**NX_PPP_STATUS_PAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="97421-488">**NX_PPP_STATUS_PAP_FAILED**</span></span>
    - <span data-ttu-id="97421-489">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="97421-489">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="97421-490">**NX_PPP_STATUS_CHAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="97421-490">**NX_PPP_STATUS_CHAP_FAILED**</span></span>
    - <span data-ttu-id="97421-491">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="97421-491">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="97421-492">**NX_PPP_STATUS_IPCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="97421-492">**NX_PPP_STATUS_IPCP_FAILED**</span></span>

>[!NOTE]
> <span data-ttu-id="97421-493">이 상태는 API가 NX_SUCCESS를 반환하는 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-493">The status is only valid if the API returns NX_SUCCESS.</span></span> <span data-ttu-id="97421-494">또한 \*_FAILED 상태 값이 반환되는 경우 애플리케이션에서 다시 시작할 때까지 PPP 처리가 사실상 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="97421-494">In addition, if any of the \*_FAILED status values are returned, PPP processing is effectively stopped until it is restarted again by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-495">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-495">Return Values</span></span>

- <span data-ttu-id="97421-496">**NX_SUCCESS**: (0x00) PPP 상태가 성공적으로 요청되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-496">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="97421-497">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-497">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-498">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-498">Allowed From</span></span>

<span data-ttu-id="97421-499">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="97421-499">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="97421-500">예제</span><span class="sxs-lookup"><span data-stu-id="97421-500">Example</span></span>

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a><span data-ttu-id="97421-501">nx_ppp_stop</span><span class="sxs-lookup"><span data-stu-id="97421-501">nx_ppp_stop</span></span>

<span data-ttu-id="97421-502">PPP 처리 중지</span><span class="sxs-lookup"><span data-stu-id="97421-502">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-503">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-503">Prototype</span></span>

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="97421-504">설명</span><span class="sxs-lookup"><span data-stu-id="97421-504">Description</span></span>

<span data-ttu-id="97421-505">이 서비스는 PPP 처리를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-505">This service stops the PPP processing.</span></span> <span data-ttu-id="97421-506">또한 사용자는 필요에 따라 nx_ppp_start()를 호출하여 PPP 처리를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-506">User also can calls nx_ppp_start() to start the PPP processing if needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-507">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-507">Input Parameters</span></span>

- <span data-ttu-id="97421-508">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-508">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-509">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-509">Return Values</span></span>

- <span data-ttu-id="97421-510">**NX_SUCCESS**: (0x00) PPP 시작이 성공적으로 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-510">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="97421-511">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP가 이미 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-511">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP already stopped.</span></span>
- <span data-ttu-id="97421-512">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-512">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="97421-513">NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-513">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-514">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-514">Allowed From</span></span>

<span data-ttu-id="97421-515">스레드</span><span class="sxs-lookup"><span data-stu-id="97421-515">Threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-516">예제</span><span class="sxs-lookup"><span data-stu-id="97421-516">Example</span></span>

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a><span data-ttu-id="97421-517">nx_ppp_packet_receive</span><span class="sxs-lookup"><span data-stu-id="97421-517">nx_ppp_packet_receive</span></span>

<span data-ttu-id="97421-518">PPP 패킷 수신</span><span class="sxs-lookup"><span data-stu-id="97421-518">Receive PPP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-519">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-519">Prototype</span></span>

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="97421-520">설명</span><span class="sxs-lookup"><span data-stu-id="97421-520">Description</span></span>

<span data-ttu-id="97421-521">이 서비스는 PPP 패킷을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-521">This service receives PPP packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-522">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-522">Input Parameters</span></span>

- <span data-ttu-id="97421-523">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-523">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-524">**packet_ptr**: PPP 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-524">**packet_ptr**: Pointer to PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-525">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-525">Return Values</span></span>

- <span data-ttu-id="97421-526">**NX_SUCCESS**: (0x00) PPP 상태가 성공적으로 요청되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-526">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="97421-527">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-527">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-528">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-528">Allowed From</span></span>

<span data-ttu-id="97421-529">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="97421-529">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-530">예제</span><span class="sxs-lookup"><span data-stu-id="97421-530">Example</span></span>

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a><span data-ttu-id="97421-531">nx_ppp_packet_send_set</span><span class="sxs-lookup"><span data-stu-id="97421-531">nx_ppp_packet_send_set</span></span>

<span data-ttu-id="97421-532">PPP 패킷 전송 함수 설정</span><span class="sxs-lookup"><span data-stu-id="97421-532">Set the PPP packet send function</span></span>

### <a name="prototype"></a><span data-ttu-id="97421-533">프로토타입</span><span class="sxs-lookup"><span data-stu-id="97421-533">Prototype</span></span>

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a><span data-ttu-id="97421-534">설명</span><span class="sxs-lookup"><span data-stu-id="97421-534">Description</span></span>

<span data-ttu-id="97421-535">이 서비스는 PPP 패킷 전송 기능을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="97421-535">This service sets the PPP packet send funciton.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="97421-536">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="97421-536">Input Parameters</span></span>

- <span data-ttu-id="97421-537">**ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-537">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="97421-538">**nx_ppp_packet_send**: PPP 패킷을 전송하는 루틴입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-538">**nx_ppp_packet_send**: Routine to send PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="97421-539">반환 값</span><span class="sxs-lookup"><span data-stu-id="97421-539">Return Values</span></span>

- <span data-ttu-id="97421-540">**NX_SUCCESS**: (0x00) PPP 상태가 성공적으로 요청되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97421-540">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="97421-541">NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="97421-541">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="97421-542">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="97421-542">Allowed From</span></span>

<span data-ttu-id="97421-543">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="97421-543">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="97421-544">예제</span><span class="sxs-lookup"><span data-stu-id="97421-544">Example</span></span>

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```