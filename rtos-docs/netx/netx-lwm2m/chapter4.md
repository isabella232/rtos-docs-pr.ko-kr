---
title: 챕터 4 - Azure RTOS NetX LWM2M 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX LWM2M 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811490"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a><span data-ttu-id="d1ff9-103">챕터 4 - Azure RTOS NetX LWM2M 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="d1ff9-103">Chapter 4 - Description of Azure RTOS NetX LWM2M services</span></span>

<span data-ttu-id="d1ff9-104">이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX LWM2M 서비스에 대해 알파벳 순서로 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-104">This chapter contains a description of all Azure RTOS NetX LWM2M services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="d1ff9-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

### <a name="lwm2m-client-management"></a><span data-ttu-id="d1ff9-106">LWM2M 클라이언트 관리</span><span class="sxs-lookup"><span data-stu-id="d1ff9-106">LWM2M Client Management</span></span>

- <span data-ttu-id="d1ff9-107">**nx_lwm2m_client_create**: *LWM2M 클라이언트 만들기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-107">**nx_lwm2m_client_create**: *Create LWM2M Client*</span></span>
- <span data-ttu-id="d1ff9-108">**nx_lwm2m_client_delete**: *LWM2M 클라이언트 삭제*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-108">**nx_lwm2m_client_delete**: *Delete LWM2M Client*</span></span>
- <span data-ttu-id="d1ff9-109">**nx_lwm2m_client_lock**: *LWM2M 클라이언트 잠금*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-109">**nx_lwm2m_client_lock**: *Lock LWM2M Client*</span></span>
- <span data-ttu-id="d1ff9-110">**nx_lwm2m_client_object_add**: *LWM2M 클라이언트에 개체 구현 추가*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-110">**nx_lwm2m_client_object_add**: *Add Object implementation to the LWM2M Client*</span></span>
- <span data-ttu-id="d1ff9-111">**nx_lwm2m_client_unlock**: *LWM2M 클라이언트 잠금 해제*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-111">**nx_lwm2m_client_unlock**: *Unlock LWM2M Client*</span></span>

### <a name="lwm2m-client-session-management"></a><span data-ttu-id="d1ff9-112">LWM2M 클라이언트 세션 관리</span><span class="sxs-lookup"><span data-stu-id="d1ff9-112">LWM2M Client Session Management</span></span>

- <span data-ttu-id="d1ff9-113">**nx_lwm2m_client_session_bootstrap**: *부트스트랩 서버를 사용하여 세션 시작*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-113">**nx_lwm2m_client_session_bootstrap**: *Start a session with a Bootstrap Server*</span></span>
- <span data-ttu-id="d1ff9-114">**nx_lwm2m_client_session_bootstrap_dtls**: *부트스트랩 서버를 사용하여 보안 세션 시작*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-114">**nx_lwm2m_client_session_bootstrap_dtls**: *Start a secure session with a Bootstrap Server*</span></span>
- <span data-ttu-id="d1ff9-115">**nx_lwm2m_client_session_create**: *LWM2M 클라이언트 세션 만들기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-115">**nx_lwm2m_client_session_create**: *Create LWM2M Client Session*</span></span>
- <span data-ttu-id="d1ff9-116">**nx_lwm2m_client_session_delete**: *LWM2M 클라이언트 세션 삭제*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-116">**nx_lwm2m_client_session_delete**: *Delete LWM2M Client Session*</span></span>
- <span data-ttu-id="d1ff9-117">**nx_lwm2m_client_session_deregister**: *LWM2M 서버를 사용하여 세션 종료*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-117">**nx_lwm2m_client_session_deregister**: *Terminate a session with a LWM2M Server*</span></span>
- <span data-ttu-id="d1ff9-118">**nx_lwm2m_client_session_error_get**: *세션의 마지막 오류 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-118">**nx_lwm2m_client_session_error_get**: *Get last error of a session*</span></span>
- <span data-ttu-id="d1ff9-119">**nx_lwm2m_client_session_register**: *LWM2M 서버를 사용하여 세션 시작*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-119">**nx_lwm2m_client_session_register**: *Start a session with a LWM2M Server*</span></span>
- <span data-ttu-id="d1ff9-120">**nx_lwm2m_client_session_register_dtls**: *LWM2M 서버를 사용하여 보안 세션 시작*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-120">**nx_lwm2m_client_session_register_dtls**: *Start a secure session with a LWM2M Server*</span></span>
- <span data-ttu-id="d1ff9-121">**nx_lwm2m_client_session_update**: *LWM2M 서버를 사용하여 세션 업데이트*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-121">**nx_lwm2m_client_session_update**: *Update a session with a LWM2M Server*</span></span>

### <a name="security-object-implementation"></a><span data-ttu-id="d1ff9-122">보안 개체 구현</span><span class="sxs-lookup"><span data-stu-id="d1ff9-122">Security Object Implementation</span></span>

- <span data-ttu-id="d1ff9-123">**nx_lwm2m_client_security_key_callbacks_set**: *보안 키 관리 콜백 설정*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-123">**nx_lwm2m_client_security_key_callbacks_set**: *Set security key management callbacks*</span></span>

### <a name="device-object-implementation"></a><span data-ttu-id="d1ff9-124">디바이스 개체 구현</span><span class="sxs-lookup"><span data-stu-id="d1ff9-124">Device Object Implementation</span></span>

- <span data-ttu-id="d1ff9-125">**nx_lwm2m_client_device_callbacks_set**: *디바이스 개체 애플리케이션 호출 설정*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-125">**nx_lwm2m_client_device_callbacks_set**: *Set Device Object application callbacks*</span></span>
- <span data-ttu-id="d1ff9-126">**nx_lwm2m_client_device_error_push**: *디바이스 개체에 오류 코드 추가*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-126">**nx_lwm2m_client_device_error_push**: *Add error code to Device Object*</span></span>
- <span data-ttu-id="d1ff9-127">**nx_lwm2m_client_device_error_reset**: *디바이스 개체의 오류 코드 다시 설정*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-127">**nx_lwm2m_client_device_error_reset**: *Reset error codes of Device Object*</span></span>
- <span data-ttu-id="d1ff9-128">**nx_lwm2m_client_device_resource_changed**: *디바이스 개체 리소스에 대한 변경 신호 보내기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-128">**nx_lwm2m_client_device_resource_changed**: *Signal change of Device Object resource*</span></span>

### <a name="custom-objects-implementation"></a><span data-ttu-id="d1ff9-129">사용자 지정 개체 구현</span><span class="sxs-lookup"><span data-stu-id="d1ff9-129">Custom Objects Implementation</span></span>

- <span data-ttu-id="d1ff9-130">**nx_lwm2m_object_resource_changed**: *개체 인스턴스의 리소스 값에 대한 변경 신호 보내기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-130">**nx_lwm2m_object_resource_changed**: *Signal change of a resource value of an Object Instance*</span></span>

### <a name="local-device-management"></a><span data-ttu-id="d1ff9-131">로컬 디바이스 관리</span><span class="sxs-lookup"><span data-stu-id="d1ff9-131">Local Device Management</span></span>

- <span data-ttu-id="d1ff9-132">**nx_lwm2m_client_object_create**: *새 개체 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-132">**nx_lwm2m_client_object_create**: *Create a new Object Instance*</span></span>
- <span data-ttu-id="d1ff9-133">**nx_lwm2m_client_object_delete**: *개체 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-133">**nx_lwm2m_client_object_delete**: *Delete an Object Instance*</span></span>
- <span data-ttu-id="d1ff9-134">**nx_lwm2m_client_object_discover**: *개체 인스턴스의 리소스 검색*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-134">**nx_lwm2m_client_object_discover**: *Discover resources of an Object Instance*</span></span>
- <span data-ttu-id="d1ff9-135">**nx_lwm2m_client_object_execute**: *개체 인스턴스의 리소스 실행*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-135">**nx_lwm2m_client_object_execute**: *Execute resource of an Object Instance*</span></span>
- <span data-ttu-id="d1ff9-136">**nx_lwm2m_client_object_get_next**: *LWM2M 클라이언트에서 구현하는 개체의 목록 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-136">**nx_lwm2m_client_object_get_next**: *Get the list of Objects implemented by the LWM2M Client*</span></span>
- <span data-ttu-id="d1ff9-137">**nx_lwm2m_client_object_instance_get_next**: *개체의 인스턴스 목록 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-137">**nx_lwm2m_client_object_instance_get_next**: *Get the list of Instances of an Object*</span></span>
- <span data-ttu-id="d1ff9-138">**nx_lwm2m_client_object_read**: *개체 인스턴스의 리소스 값 읽기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-138">**nx_lwm2m_client_object_read**: *Read resources values of an Object Instance*</span></span>
- <span data-ttu-id="d1ff9-139">**nx_lwm2m_client_object_write**: *개체 인스턴스의 리소스 값 변경*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-139">**nx_lwm2m_client_object_write**: *Change resources values of an Object instance*</span></span>

### <a name="resources-values-decoding"></a><span data-ttu-id="d1ff9-140">리소스 값 디코딩</span><span class="sxs-lookup"><span data-stu-id="d1ff9-140">Resources Values Decoding</span></span>

- <span data-ttu-id="d1ff9-141">**nx_lwm2m_resource_get_boolean**: *부울 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-141">**nx_lwm2m_resource_get_boolean**: *Get the value of a Boolean Resource*</span></span>
- <span data-ttu-id="d1ff9-142">**nx_lwm2m_resource_get_float32**: *32비트 부동 소수점 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-142">**nx_lwm2m_resource_get_float32**: *Get the value of a 32-bit Floating Point Resource*</span></span>
- <span data-ttu-id="d1ff9-143">**nx_lwm2m_resource_get_float64**: *64비트 부동 소수점 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-143">**nx_lwm2m_resource_get_float64**: *Get the value of a 64-bit Floating Point Resource*</span></span>
- <span data-ttu-id="d1ff9-144">**nx_lwm2m_resource_get_integer32**: *32비트 정수 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-144">**nx_lwm2m_resource_get_integer32**: *Get the value of a 32-Bit Integer Resource*</span></span>
- <span data-ttu-id="d1ff9-145">**nx_lwm2m_resource_get_integer64**: *64비트 정수 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-145">**nx_lwm2m_resource_get_integer64**: *Get the value of a 64-Bit Integer Resource*</span></span>
- <span data-ttu-id="d1ff9-146">**nx_lwm2m_resource_get_objlnk**: *개체 링크 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-146">**nx_lwm2m_resource_get_objlnk**: *Get the value of an Object Link Resource*</span></span>
- <span data-ttu-id="d1ff9-147">**nx_lwm2m_resource_get_opaque**: *불투명 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-147">**nx_lwm2m_resource_get_opaque**: *Get the value of an Opaque Resource*</span></span>
- <span data-ttu-id="d1ff9-148">**nx_lwm2m_resource_get_string**: *문자열 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-148">**nx_lwm2m_resource_get_string**: *Get the value of a String Resource*</span></span>
- <span data-ttu-id="d1ff9-149">**nx_lwm2m_resource_multiple_get_boolean**: *부울 리소스 다중 리소스 인스턴스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-149">**nx_lwm2m_resource_multiple_get_boolean**: *Get the value of a Boolean Resource Multiple Resource Instance*</span></span>
- <span data-ttu-id="d1ff9-150">**nx_lwm2m_resource_multiple_get_float32**: *32비트 부동 소수점 다중 리소스 인스턴스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-150">**nx_lwm2m_resource_multiple_get_float32**: *Get the value of a 32-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="d1ff9-151">**nx_lwm2m_resource_multiple_get_float64**: *64비트 부동 소수점 다중 리소스 인스턴스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-151">**nx_lwm2m_resource_multiple_get_float64**: *Get the value of a 64-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="d1ff9-152">**nx_lwm2m_resource_multiple_get_integer32**: *32비트 정수 다중 리소스 인스턴스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-152">**nx_lwm2m_resource_multiple_get_integer32**: *Get the value of a 32-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="d1ff9-153">**nx_lwm2m_resource_multiple_get_integer64**: *64비트 정수 다중 리소스 인스턴스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-153">**nx_lwm2m_resource_multiple_get_integer64**: *Get the value of a 64-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="d1ff9-154">**nx_lwm2m_resource_multiple_get_objlnk**: *개체 링크 다중 리소스 인스턴스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-154">**nx_lwm2m_resource_multiple_get_objlnk**: *Get the value of an Object Link Multiple Resource Instance*</span></span>
- <span data-ttu-id="d1ff9-155">**nx_lwm2m_resource_multiple_get_opaque**: *불투명 다중 리소스 인스턴스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-155">**nx_lwm2m_resource_multiple_get_opaque**: *Get the value of an Opaque Multiple Resource Instance*</span></span>
- <span data-ttu-id="d1ff9-156">**nx_lwm2m_resource_multiple_get_string**: *문자열 다중 리소스 인스턴스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-156">**nx_lwm2m_resource_multiple_get_string**: *Get the value of a String Multiple Resource Instance*</span></span>

### <a name="firmware-update-object"></a><span data-ttu-id="d1ff9-157">펌웨어 업데이트 개체</span><span class="sxs-lookup"><span data-stu-id="d1ff9-157">Firmware Update Object</span></span>

- <span data-ttu-id="d1ff9-158">**nx_lwm2m_firmware_create**: *펌웨어 업데이트 개체 만들기*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-158">**nx_lwm2m_firmware_create**: *Create Firmware Update Object*</span></span>
- <span data-ttu-id="d1ff9-159">**nx_lwm2m_firmware_package_info_set**: *펌웨어 업데이트 패키지 정보 설정*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-159">**nx_lwm2m_firmware_package_info_set**: *Set Firmware Update Package Information*</span></span>
- <span data-ttu-id="d1ff9-160">**nx_lwm2m_firmware_result_set**: *펌웨어 업데이트 결과 설정*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-160">**nx_lwm2m_firmware_result_set**: *Set Firmware Update Result*</span></span>
- <span data-ttu-id="d1ff9-161">**nx_lwm2m_firmware_state_set**: *펌웨어 업데이트 상태 설정*</span><span class="sxs-lookup"><span data-stu-id="d1ff9-161">**nx_lwm2m_firmware_state_set**: *Set Firmware Update State*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="d1ff9-162">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="d1ff9-162">nx_lwm2m_client_create</span></span>

<span data-ttu-id="d1ff9-163">LWM2M 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-163">Create LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-164">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-164">Prototype</span></span>

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="d1ff9-165">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-165">Description</span></span>

<span data-ttu-id="d1ff9-166">이 서비스는 자체 ThreadX 스레드의 컨텍스트에서 실행되는 LWM2M 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-166">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="d1ff9-167">LWM2M 클라이언트는 보안(0), 서버(1), 액세스 제어(2) 및 디바이스(3)와 같은 OMA LWM2M 개체를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-167">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="d1ff9-168">다른 개체 구현은 애플리케이션에서 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-168">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-169">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-169">Parameters</span></span>

- <span data-ttu-id="d1ff9-170">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-170">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-171">**ip_ptr**: 이전에 만든 IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-171">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d1ff9-172">**packet_pool_ptr**: 이 LWM2M 클라이언트의 기본 패킷 풀에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-172">**packet_pool_ptr**: Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="d1ff9-173">**local_port**: 비보안 통신에 사용되는 로컬 UDP 포트</span><span class="sxs-lookup"><span data-stu-id="d1ff9-173">**local_port**: The local UDP port used for non-secure communication.</span></span>
- <span data-ttu-id="d1ff9-174">**name_ptr**: LWM2M 클라이언트 엔드포인트 이름에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-174">**name_ptr**: Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="d1ff9-175">**msisdn_ptr**: SMS 바인딩에서 사용하기 위해 LWM2M 클라이언트에 연결할 수 있는 MSISDN에 대한 포인터이며, SMS 바인딩이 지원되지 않는 경우 NULL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-175">**msisdn_ptr**: Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="d1ff9-176">**binding_modes**: LWM2M 클라이언트에서 지원하는 바인딩 및 모드이며, NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S 및 NX_LWM2M_BINDING_SQ 플래그의 조합이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-176">**binding_modes**: The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="d1ff9-177">**stack_ptr**: LWM2M 클라이언트 스레드 스택 영역에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-177">**stack_ptr**: Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="d1ff9-178">**stack_size**: LWM2M 클라이언트 스레드 스택 크기</span><span class="sxs-lookup"><span data-stu-id="d1ff9-178">**stack_size**: The LWM2M Client thread stack size.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-179">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-179">Return Values</span></span>

- <span data-ttu-id="d1ff9-180">**NX_SUCCESS**: LWM2M 클라이언트를 성공적으로 만듦</span><span class="sxs-lookup"><span data-stu-id="d1ff9-180">**NX_SUCCESS**: The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="d1ff9-181">**NX_LWM2M_ERROR**: LWM2M 클라이언트 만들기 오류</span><span class="sxs-lookup"><span data-stu-id="d1ff9-181">**NX_LWM2M_ERROR**: LWM2M Client create error.</span></span>
- <span data-ttu-id="d1ff9-182">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-182">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="d1ff9-183">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="d1ff9-183">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="d1ff9-184">LWM2M 클라이언트를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-184">Delete LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-185">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-185">Prototype</span></span>

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-186">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-186">Description</span></span>

<span data-ttu-id="d1ff9-187">이 서비스는 이전에 만든 LWM2M 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-187">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="d1ff9-188">현재 클라이언트에 연결된 모든 세션도 이 호출을 통해 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-188">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-189">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-189">Parameters</span></span>

- <span data-ttu-id="d1ff9-190">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-190">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-191">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-191">Return Values</span></span>

- <span data-ttu-id="d1ff9-192">**NX_SUCCESS**: LWM2M 클라이언트를 성공적으로 삭제함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-192">**NX_SUCCESS**: The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="d1ff9-193">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-193">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_callbacks_set"></a><span data-ttu-id="d1ff9-194">nx_lwm2m_client_device_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="d1ff9-194">nx_lwm2m_client_device_callbacks_set</span></span>

<span data-ttu-id="d1ff9-195">디바이스 개체 애플리케이션 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-195">Set Device Object application callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-196">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-196">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a><span data-ttu-id="d1ff9-197">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-197">Description</span></span>

<span data-ttu-id="d1ff9-198">이 서비스는 LWM2M 클라이언트에서 처리하지 않는 LWM2M 디바이스 개체 리소스에 대한 작업을 구현하는 애플리케이션 콜백을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-198">This service installs the application callbacks for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="d1ff9-199">LWM2M 클라이언트는 오류 코드(11), 다시 설정 오류 코드(12) 및 지원되는 바인딩 및 모드(16)와 같은 리소스를 구현합니다. 다른 리소스에 대한 작업은 애플리케이션으로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-199">The LWM2M Client implements the following resources : Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-200">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-200">Parameters</span></span>

- <span data-ttu-id="d1ff9-201">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-201">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-202">**read_callback**: 'Read' 메서드 콜백</span><span class="sxs-lookup"><span data-stu-id="d1ff9-202">**read_callback**: The 'Read' method callback.</span></span>
- <span data-ttu-id="d1ff9-203">**discover_callback**: 'Discover' 메서드 콜백</span><span class="sxs-lookup"><span data-stu-id="d1ff9-203">**discover_callback**: The 'Discover' method callback.</span></span>
- <span data-ttu-id="d1ff9-204">**write_callback**: 'Write' 메서드 콜백</span><span class="sxs-lookup"><span data-stu-id="d1ff9-204">**write_callback**: The 'Write' method callback.</span></span>
- <span data-ttu-id="d1ff9-205">**execute_callback**: 'Execute' 메서드 콜백</span><span class="sxs-lookup"><span data-stu-id="d1ff9-205">**execute_callback**: The 'Execute' method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-206">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-206">Return Values</span></span>

- <span data-ttu-id="d1ff9-207">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-207">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-208">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-208">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="d1ff9-209">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="d1ff9-209">nx_lwm2m_client_device_error_push</span></span>

<span data-ttu-id="d1ff9-210">오류 코드를 디바이스 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-210">Add error code to Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-211">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-211">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a><span data-ttu-id="d1ff9-212">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-212">Description</span></span>

<span data-ttu-id="d1ff9-213">이 서비스는 새 인스턴스를 개체 디바이스의 오류 코드(11) 리소스에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-213">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-214">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-214">Parameters</span></span>

- <span data-ttu-id="d1ff9-215">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-215">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-216">**code**: 새 오류 코드</span><span class="sxs-lookup"><span data-stu-id="d1ff9-216">**code**: The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-217">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-217">Return Values</span></span>

- <span data-ttu-id="d1ff9-218">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-218">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-219">**NX_LWM2M_BUFFER_TOO_SMALL**: 저장된 최대 오류 코드 수에 도달함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-219">**NX_LWM2M_BUFFER_TOO_SMALL**: The maximum number of stored error codes has been reached.</span></span>
- <span data-ttu-id="d1ff9-220">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-220">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="d1ff9-221">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="d1ff9-221">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="d1ff9-222">디바이스 개체의 오류 코드를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-222">Reset error codes of Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-223">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-223">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-224">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-224">Description</span></span>

<span data-ttu-id="d1ff9-225">이 서비스는 디바이스 개체에서 모든 오류 코드 리소스 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-225">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="d1ff9-226">이는 리소스 다시 설정 오류 코드(12)를 실행하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-226">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-227">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-227">Parameters</span></span>

- <span data-ttu-id="d1ff9-228">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-228">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-229">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-229">Return Values</span></span>

- <span data-ttu-id="d1ff9-230">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-230">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-231">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-231">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="d1ff9-232">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="d1ff9-232">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="d1ff9-233">디바이스 개체 리소스에 대한 변경 신호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-233">Signal change of Device Object resource</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-234">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-234">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="d1ff9-235">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-235">Description</span></span>

<span data-ttu-id="d1ff9-236">이 서비스는 애플리케이션에서 개체 디바이스의 리소스가 변경되었다는 신호를 LWM2M 클라이언트에 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-236">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="d1ff9-237">LWM2M 서버에서 리소스를 관찰하는 경우 LWM2M 클라이언트에서 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-237">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-238">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-238">Parameters</span></span>

- <span data-ttu-id="d1ff9-239">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-239">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-240">**resource**: 변경된 리소스를 설명하는 구조체에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-240">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-241">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-241">Return Values</span></span>

- <span data-ttu-id="d1ff9-242">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-242">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-243">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-243">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="d1ff9-244">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="d1ff9-244">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="d1ff9-245">LWM2M 클라이언트를 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-245">Lock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-246">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-246">Prototype</span></span>

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-247">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-247">Description</span></span>

<span data-ttu-id="d1ff9-248">이 서비스는 서버 또는 다른 애플리케이션 스레드에서 LWM2M 개체에 대한 동시 액세스를 방지하기 위해 LWM2M 클라이언트를 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-248">This service locks the LWM2M Client to prevent concurent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="d1ff9-249">LWM2M 클라이언트가 현재 다른 스레드에서 잠겨 있는 경우 LWM2M 클라이언트의 잠금이 해제될 때까지 이 함수가 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-249">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="d1ff9-250">nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() 쌍에 대한 호출은 중첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-250">Calls to nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-251">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-251">Parameters</span></span>

- <span data-ttu-id="d1ff9-252">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-252">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-253">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-253">Return Values</span></span>

- <span data-ttu-id="d1ff9-254">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-254">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-255">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-255">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="d1ff9-256">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="d1ff9-256">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="d1ff9-257">개체 구현을 LWM2M 클라이언트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-257">Add Object implementation to the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-258">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-258">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-259">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-259">Description</span></span>

<span data-ttu-id="d1ff9-260">이 서비스는 새 개체 구현을 LWM2M 클라이언트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-260">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-261">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-261">Parameters</span></span>

- <span data-ttu-id="d1ff9-262">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-262">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-263">**object_ptr**: 개체 구현을 정의하는 구조체에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-263">**object_ptr**: Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-264">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-264">Return Values</span></span>

- <span data-ttu-id="d1ff9-265">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-265">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-266">**NX_LWM2M_ALREADY_EXIST**: 개체 ID가 이미 있음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-266">**NX_LWM2M_ALREADY_EXIST**: The Object ID already exists.</span></span>
- <span data-ttu-id="d1ff9-267">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-267">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="d1ff9-268">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="d1ff9-268">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="d1ff9-269">새 개체 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-269">Create a new Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-270">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-270">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-271">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-271">Description</span></span>

<span data-ttu-id="d1ff9-272">이 서비스는 LWM2M 클라이언트의 개체에 대한 'Create' 작업을 수행하여 새 개체 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-272">This service performs a 'Create' operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-273">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-273">Parameters</span></span>

- <span data-ttu-id="d1ff9-274">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-274">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-275">**object_id**: 개체 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-275">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="d1ff9-276">**instance_id_ptr**: 새 인스턴스의 ID에 대한 포인터이며 LWM2M 클라이언트에서 인스턴스 ID를 할당해야 하는 경우 NULL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-276">**instance_id_ptr**: Pointer to the ID of the new instance, can be NULL if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="d1ff9-277">ID가 예약된 65535 값인 경우 LWM2M 클라이언트에서 인스턴스 ID를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-277">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="d1ff9-278">NULL이 아닌 경우 할당된 ID가 호출 후에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-278">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="d1ff9-279">**num_values**: 설정하는 값의 수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-279">**num_values**: The number of values to set.</span></span>
- <span data-ttu-id="d1ff9-280">**values_ptr**: 새 개체 인스턴스를 초기화하는 리소스 값의 배열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-280">**values_ptr**: Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-281">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-281">Return Values</span></span>

- <span data-ttu-id="d1ff9-282">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-282">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-283">**NX_LWM2M_ALREADY_EXIST**: 개체 인스턴스 ID가 이미 있음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-283">**NX_LWM2M_ALREADY_EXIST**: The Object Instance ID already exists.</span></span>
- <span data-ttu-id="d1ff9-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: 개체에서 인스턴스 만들기를 지원하지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance creation.</span></span>
- <span data-ttu-id="d1ff9-285">**NX_LWM2M_NO_MEMORY**: 새 인스턴스를 저장하는 메모리를 할당할 수 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-285">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="d1ff9-286">**NX_LWM2M_NOT_FOUND**: 개체 ID가 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-286">**NX_LWM2M_NOT_FOUND**: The Object ID doesn't exist.</span></span>
- <span data-ttu-id="d1ff9-287">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-287">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="d1ff9-288">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="d1ff9-288">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="d1ff9-289">개체 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-289">Delete an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-290">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-290">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="d1ff9-291">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-291">Description</span></span>

<span data-ttu-id="d1ff9-292">이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Delete' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-292">This service performs a 'Delete' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-293">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-293">Parameters</span></span>

- <span data-ttu-id="d1ff9-294">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-294">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-295">**object_id**: 개체 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-295">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="d1ff9-296">**instance_id**: 개체 인스턴스 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-296">**instance_id**: The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-297">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-297">Return Values</span></span>

- <span data-ttu-id="d1ff9-298">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-298">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: 개체에서 인스턴스 삭제를 지원하지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance deletion.</span></span>
- <span data-ttu-id="d1ff9-300">**NX_LWM2M_NOT_FOUND**: 개체 ID 또는 개체 인스턴스 ID가 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-300">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="d1ff9-301">NX_PTR_ERROR 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-301">NX_PTR_ERROR Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="d1ff9-302">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="d1ff9-302">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="d1ff9-303">개체 인스턴스의 리소스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-303">Discover resources of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-304">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-304">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-305">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-305">Description</span></span>

<span data-ttu-id="d1ff9-306">이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Discover' 작업을 수행하여 개체에서 구현한 리소스 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-306">This service performs a 'Discover' operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-307">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-307">Parameters</span></span>

- <span data-ttu-id="d1ff9-308">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-308">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-309">**object_id**: 개체 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-309">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="d1ff9-310">**instance_id**: 개체 인스턴스 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-310">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="d1ff9-311">**num_resources_ptr**: 입력 시 대상 버퍼의 크기 및 출력 시 버퍼에 쓰인 요소의 수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-311">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>
- <span data-ttu-id="d1ff9-312">**resources_ptr**: 대상 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-312">**resources_ptr**: Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-313">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-313">Return Values</span></span>

- <span data-ttu-id="d1ff9-314">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-314">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="d1ff9-315">**NX_LWM2M_BUFFER_TOO_SMALL**: 리소스 버퍼가 너무 작아 리소스 목록을 저장할 수 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-315">**NX_LWM2M_BUFFER_TOO_SMALL**: The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="d1ff9-316">**NX_LWM2M_NOT_FOUND**: 개체 ID 또는 개체 인스턴스 ID가 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-316">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="d1ff9-317">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-317">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="d1ff9-318">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="d1ff9-318">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="d1ff9-319">개체 인스턴스의 리소스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-319">Execute resource of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-320">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-320">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="d1ff9-321">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-321">Description</span></span>

<span data-ttu-id="d1ff9-322">이 서비스는 LWM2M 클라이언트의 개체 인스턴스 리소스에 대한 'Execute' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-322">This service performs the 'Execute' operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-323">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-323">Parameters</span></span>

- <span data-ttu-id="d1ff9-324">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-324">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-325">**object_id**: 개체 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-325">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="d1ff9-326">**instance_id**: 개체 인스턴스 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-326">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="d1ff9-327">**resource_id**: 리소스 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-327">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="d1ff9-328">**arguments_ptr**: 실행 작업의 인수에 대한 포인터이며,</span><span class="sxs-lookup"><span data-stu-id="d1ff9-328">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="d1ff9-329">arguments_length가 0인 경우 NULL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-329">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="d1ff9-330">**arguments_length**: 인수의 길이</span><span class="sxs-lookup"><span data-stu-id="d1ff9-330">**arguments_length**: The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-331">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-331">Return Values</span></span>

- <span data-ttu-id="d1ff9-332">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-332">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: 리소스에서 실행 작업을 지원하지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: The resource doesn't support the execute operation.</span></span>
- <span data-ttu-id="d1ff9-334">**NX_LWM2M_NOT_FOUND**: 개체 ID, 개체 인스턴스 ID 또는 리소스 ID가 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-334">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or the resource ID doesn't exist.</span></span>
- <span data-ttu-id="d1ff9-335">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-335">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_get_next"></a><span data-ttu-id="d1ff9-336">nx_lwm2m_client_object_get_next</span><span class="sxs-lookup"><span data-stu-id="d1ff9-336">nx_lwm2m_client_object_get_next</span></span>

<span data-ttu-id="d1ff9-337">LWM2M Client에서 구현하는 개체의 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-337">Get the list of Objects implemented by the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-338">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-338">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-339">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-339">Description</span></span>

<span data-ttu-id="d1ff9-340">이 서비스는 LWM2M 클라이언트에서 구현하는 다음 개체의 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-340">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="d1ff9-341">현재 개체 ID가 NX_LWM2M_RESERVED_ID (65535)로 설정된 경우 첫 번째 개체 ID가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-341">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-342">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-342">Parameters</span></span>

- <span data-ttu-id="d1ff9-343">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-343">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-344">**object_id_ptr**: 현재 개체 ID에 대한 포인터이며,</span><span class="sxs-lookup"><span data-stu-id="d1ff9-344">**object_id_ptr**: Pointer to the current Object ID.</span></span> <span data-ttu-id="d1ff9-345">반환 시 LWM2M 클라이언트에서 구현하는 다음 개체 ID가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-345">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-346">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-346">Return Values</span></span>

- <span data-ttu-id="d1ff9-347">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-347">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="d1ff9-348">**NX_LWM2M_NOT_FOUND**: 지정된 개체 ID가 데이터베이스의 마지막 ID임</span><span class="sxs-lookup"><span data-stu-id="d1ff9-348">**NX_LWM2M_NOT_FOUND**: The given Object ID is the last of the database.</span></span>
- <span data-ttu-id="d1ff9-349">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-349">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_instance_get_next"></a><span data-ttu-id="d1ff9-350">nx_lwm2m_client_object_instance_get_next</span><span class="sxs-lookup"><span data-stu-id="d1ff9-350">nx_lwm2m_client_object_instance_get_next</span></span>

<span data-ttu-id="d1ff9-351">개체의 인스턴스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-351">Get the list of Instances of an Object</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-352">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-352">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-353">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-353">Description</span></span>

<span data-ttu-id="d1ff9-354">이 서비스는 지정된 개체의 다음 개체 인스턴스에 대한 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-354">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="d1ff9-355">현재 인스턴스 ID가 NX_LWM2M_RESERVED_ID (65535)로 설정된 경우 첫 번째 인스턴스의 ID가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-355">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-356">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-356">Parameters</span></span>

- <span data-ttu-id="d1ff9-357">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-357">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-358">**object_id**: 개체 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-358">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="d1ff9-359">**instance_id_ptr**: 현재 개체 인스턴스 ID에 대한 포인터이며,</span><span class="sxs-lookup"><span data-stu-id="d1ff9-359">**instance_id_ptr**: Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="d1ff9-360">반환 시 개체의 다음 인스턴스 ID가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-360">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-361">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-361">Return Values</span></span>

- <span data-ttu-id="d1ff9-362">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-362">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="d1ff9-363">**NX_LWM2M_NOT_FOUND**: 지정된 인스턴스 ID가 개체의 마지막 ID이거나 개체 ID가 구현되지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-363">**NX_LWM2M_NOT_FOUND**: The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="d1ff9-364">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-364">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="d1ff9-365">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="d1ff9-365">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="d1ff9-366">개체 인스턴스의 리소스 값을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-366">Read resources values of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-367">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-367">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="d1ff9-368">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-368">Description</span></span>

<span data-ttu-id="d1ff9-369">이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Read' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-369">This service performs a 'Read' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-370">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-370">Parameters</span></span>

- <span data-ttu-id="d1ff9-371">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-371">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-372">**object_id**: 개체 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-372">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="d1ff9-373">**instance_id**: 개체 인스턴스 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-373">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="d1ff9-374">**num_values**: 읽는 리소스의 수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-374">**num_values**: The number of resources to read.</span></span>
- <span data-ttu-id="d1ff9-375">**values_ptr**: 읽는 리소스의 ID가 포함되는 NX_LWM2M_RESOURCE 배열에 대한 포인터이며,</span><span class="sxs-lookup"><span data-stu-id="d1ff9-375">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="d1ff9-376">반환 시 배열이 해당 형식 및 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-376">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-377">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-377">Return Values</span></span>

- <span data-ttu-id="d1ff9-378">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-378">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: 리소스에서 읽기 작업을 지원하지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the read operation.</span></span>
- <span data-ttu-id="d1ff9-380">**NX_LWM2M_NOT_FOUND**: 개체 ID, 개체 인스턴스 ID 또는 리소스 ID가 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-380">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="d1ff9-381">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-381">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="d1ff9-382">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="d1ff9-382">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="d1ff9-383">개체 인스턴스의 리소스 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-383">Change resources values of an Object instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-384">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-384">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a><span data-ttu-id="d1ff9-385">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-385">Description</span></span>

<span data-ttu-id="d1ff9-386">이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Write' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-386">This service performs a 'Write' operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="d1ff9-387">*write_op* 매개 변수에 지정할 수 있는 쓰기 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-387">The following write operations can be specified to the *write_op* parameter:</span></span>

- <span data-ttu-id="d1ff9-388">**0** &mdash; 부분 업데이트: 새 값으로 제공되는 리소스를 추가하거나 업데이트하고, 다른 기존 리소스는 변경하지 않은 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-388">**0** &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="d1ff9-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; 인스턴스 바꾸기: 개체 인스턴스를 제공된 새 리소스 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="d1ff9-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; 리소스 바꾸기: 리소스를 제공 된 새 리소스 값으로 바꿉니다(여러 리소스를 바꾸는 데 사용됨).</span><span class="sxs-lookup"><span data-stu-id="d1ff9-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="d1ff9-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; 부트스트랩 쓰기: 부트스트랩 시퀀스의 호출을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: indicates a call from a Bootstrap sequence.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-392">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-392">Parameters</span></span>

- <span data-ttu-id="d1ff9-393">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-393">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-394">**object_id**: 개체 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-394">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="d1ff9-395">**instance_id**: 개체 인스턴스 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-395">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="d1ff9-396">**num_values**: 쓰는 리소스의 수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-396">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="d1ff9-397">**values_ptr**: 리소스 ID, 형식 및 쓰는 값이 포함되는 NX_LWM2M_RESOURCE 배열에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-397">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="d1ff9-398">**write_op**: 쓰기 작업의 형식</span><span class="sxs-lookup"><span data-stu-id="d1ff9-398">**write_op**: The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-399">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-399">Return Values</span></span>

- <span data-ttu-id="d1ff9-400">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-400">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-401">**NX_LWM2M_BAD_ENCODING**: 리소스 종류가 잘못됨</span><span class="sxs-lookup"><span data-stu-id="d1ff9-401">**NX_LWM2M_BAD_ENCODING**: The type of a resource is not valid.</span></span>
- <span data-ttu-id="d1ff9-402">**NX_LWM2M_BUFFER_TOO_SMALL**: 값의 길이가 너무 커서 인스턴스에 저장할 수 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-402">**NX_LWM2M_BUFFER_TOO_SMALL**: The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="d1ff9-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: 리소스에서 쓰기 작업을 지원하지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the write operation.</span></span>
- <span data-ttu-id="d1ff9-404">**NX_LWM2M_NO_MEMORY**: 리소스 값을 저장하는 메모리를 할당할 수 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-404">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="d1ff9-405">**NX_LWM2M_NOT_ACCEPTABLE**: 리소스의 값이 잘못됨</span><span class="sxs-lookup"><span data-stu-id="d1ff9-405">**NX_LWM2M_NOT_ACCEPTABLE**: The value of a resource is not valid.</span></span>
- <span data-ttu-id="d1ff9-406">**NX_LWM2M_NOT_FOUND**: 개체 ID, 개체 인스턴스 ID 또는 리소스 ID가 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-406">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="d1ff9-407">NX_OPTION_ERROR: 잘못된 쓰기 작업의 형식</span><span class="sxs-lookup"><span data-stu-id="d1ff9-407">NX_OPTION_ERROR: Invalid type of write operation.</span></span>
- <span data-ttu-id="d1ff9-408">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-408">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a><span data-ttu-id="d1ff9-409">nx_lwm2m_client_security_key_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="d1ff9-409">nx_lwm2m_client_security_key_callbacks_set</span></span>

<span data-ttu-id="d1ff9-410">보안 개체 키 관리 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-410">Set Security Object key management callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-411">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-411">Prototype</span></span>

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a><span data-ttu-id="d1ff9-412">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-412">Description</span></span>

<span data-ttu-id="d1ff9-413">이 서비스는 보안 키와 관련된 LWM2M 보안 개체 리소스에 대한 작업을 구현하는 애플리케이션 콜백을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-413">This service installs the application callbacks for implementing operations on the LWM2M Security Object resources related to the security keys.</span></span>

<span data-ttu-id="d1ff9-414">LWM2M 클라이언트는 부트스트랩 세션 중에 보안 키 관리를 애플리케이션에 위임하고, 부트스트랩 서버에서 보안 개체 인스턴스에서 공개 키 또는 ID(3), 서버 공개 키(4), 비밀 키(5) 리소스를 쓰거나 삭제할 때 콜백이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-414">The LWM2M Client delegates the security key management to the application during the Bootstrap sessions, the callbacks will be called when the Bootstrap Server writes or deletes the following resources on a Security Object Instance: Public Key or Identity (3), Server Public Key (4), Secret Key (5).</span></span>

<span data-ttu-id="d1ff9-415">애플리케이션에서 키 데이터를 저장하고 LWM2M 클라이언트에서 사용하는 DTLS 세션을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-415">The application is responsible for storing the keys data and for configuring the DTLS sessions used by the LWM2M client.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-416">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-416">Parameters</span></span>

- <span data-ttu-id="d1ff9-417">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-417">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="d1ff9-418">**write_callback**: 'Write' 키 메서드 콜백</span><span class="sxs-lookup"><span data-stu-id="d1ff9-418">**write_callback**: The 'Write' key method callback.</span></span>
- <span data-ttu-id="d1ff9-419">**delete_callback**: 'Delete' 키 메서드 콜백</span><span class="sxs-lookup"><span data-stu-id="d1ff9-419">**delete_callback**: The 'Delete' key method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-420">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-420">Return Values</span></span>

- <span data-ttu-id="d1ff9-421">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-421">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-422">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-422">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="d1ff9-423">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="d1ff9-423">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="d1ff9-424">부트스트랩 서버를 사용하여 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-424">Start a session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-425">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-425">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="d1ff9-426">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-426">Description</span></span>

<span data-ttu-id="d1ff9-427">이 서비스는 부트스트랩 서버를 사용하여 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-427">This service start a session with a Bootstrap Server.</span></span> <span data-ttu-id="d1ff9-428">서버의 보안 개체에는 해당 보안 인스턴스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-428">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="d1ff9-429">이 서버와 연결된 보안 인스턴스에서 'Hold Off'(지연) 리소스가 0과 다른 경우 세션에서 서버 시작 부트스트랩을 기다리며, 이 기간 이후에 서버에서 부트스트랩을 시작하지 않으면 클라이언트 시작 부트스트랩이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-429">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="d1ff9-430">현재 활성 세션은 이 호출에서 중단되고 새 부트스트랩 서버 세션으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-430">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-431">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-431">Parameters</span></span>

- <span data-ttu-id="d1ff9-432">**session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-432">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="d1ff9-433">**security_id**: 부트 스트랩 서버의 보안 인스턴스 ID이며, 부트 스트랩 서버에 정의된 보안 인스턴스가 없는 경우 NX_LWM2M_RESERVED_ID (65535)로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-433">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="d1ff9-434">**ip_address** 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="d1ff9-434">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="d1ff9-435">**port**: 서버의 UDP 포트</span><span class="sxs-lookup"><span data-stu-id="d1ff9-435">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-436">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-436">Return Values</span></span>

- <span data-ttu-id="d1ff9-437">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-437">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-438">**NX_LWM2M_NOT_FOUND**: 보안 인스턴스 ID에 해당하는 보안 개체 인스턴스가 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-438">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="d1ff9-439">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-439">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="d1ff9-440">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="d1ff9-440">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="d1ff9-441">부트스트랩 서버를 사용하여 보안 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-441">Start a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-442">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-442">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="d1ff9-443">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-443">Description</span></span>

<span data-ttu-id="d1ff9-444">이 서비스는 보안 DTLS 연결을 사용하여 부트스트랩 서버에서 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-444">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="d1ff9-445">서버의 보안 개체에는 해당 보안 인스턴스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-445">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="d1ff9-446">이 함수를 호출하기 전에 DTLS 세션을 적절한 암호 그룹 및 키 자료를 사용하여 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-446">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="d1ff9-447">NX_SECURE_ENABLE_DTLS를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-447">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="d1ff9-448">이 서버와 연결된 보안 인스턴스에서 'Hold Off'(지연) 리소스가 0과 다른 경우 세션에서 서버 시작 부트스트랩을 기다리며, 이 기간 이후에 서버에서 부트스트랩을 시작하지 않으면 클라이언트 시작 부트스트랩이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-448">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="d1ff9-449">현재 활성 세션은 이 호출에서 중단되고 새 부트스트랩 서버 세션으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-449">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-450">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-450">Parameters</span></span>

- <span data-ttu-id="d1ff9-451">**session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-451">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="d1ff9-452">**security_id**: 부트 스트랩 서버의 보안 인스턴스 ID이며, 부트 스트랩 서버에 정의된 보안 인스턴스가 없는 경우 NX_LWM2M_RESERVED_ID (65535)로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-452">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="d1ff9-453">**ip_address** 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="d1ff9-453">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="d1ff9-454">**port**: 서버의 UDP 포트</span><span class="sxs-lookup"><span data-stu-id="d1ff9-454">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="d1ff9-455">**dtls_session_ptr**: 부트스트랩 세션에 사용하는 DTLS 세션</span><span class="sxs-lookup"><span data-stu-id="d1ff9-455">**dtls_session_ptr**: The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="d1ff9-456">**dtls_local_port**: DTLS 세션에 사용되는 로컬 UDP 포트</span><span class="sxs-lookup"><span data-stu-id="d1ff9-456">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-457">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-457">Return Values</span></span>

- <span data-ttu-id="d1ff9-458">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-458">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-459">**NX_LWM2M_NOT_FOUND**: 보안 인스턴스 ID에 해당하는 보안 개체 인스턴스가 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-459">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="d1ff9-460">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-460">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="d1ff9-461">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="d1ff9-461">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="d1ff9-462">LWM2M 클라이언트 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-462">Create LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-463">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-463">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="d1ff9-464">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-464">Description</span></span>

<span data-ttu-id="d1ff9-465">이 서비스는 기존 LWM2M 클라이언트에 연결된 새 LWM2M 클라이언트 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-465">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="d1ff9-466">이 세션은 LWM2M 클라이언트에서 부트스트랩 서버 또는 LWM2M 서버와 통신하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-466">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span>

<span data-ttu-id="d1ff9-467">애플리케이션에서 세션 상태가 업데이트될 때 호출되는 콜백 함수를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-467">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-468">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-468">Parameters</span></span>

- <span data-ttu-id="d1ff9-469">**session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-469">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="d1ff9-470">**client_ptr**: 이전에 만든 LWM2M 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-470">**client_ptr**: Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="d1ff9-471">**state_callback**: 세션의 상태가 변경되었을 때 호출되는 애플리케이션 콜백</span><span class="sxs-lookup"><span data-stu-id="d1ff9-471">**state_callback**: Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-472">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-472">Return Values</span></span>

- <span data-ttu-id="d1ff9-473">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-473">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-474">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-474">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="d1ff9-475">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="d1ff9-475">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="d1ff9-476">LWM2M Client 세션을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-476">Delete LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-477">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-477">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-478">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-478">Description</span></span>

<span data-ttu-id="d1ff9-479">이 서비스는 LWM2M Client 세션을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-479">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="d1ff9-480">nx_lwm2m_client_delete를 호출하여 LWM2M 클라이언트를 삭제하면 클라이언트에 연결된 모든 세션도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-480">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-481">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-481">Parameters</span></span>

- <span data-ttu-id="d1ff9-482">**session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-482">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-483">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-483">Return Values</span></span>

- <span data-ttu-id="d1ff9-484">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-484">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-485">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-485">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="d1ff9-486">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="d1ff9-486">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="d1ff9-487">LWM2M 서버를 사용하여 세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-487">Terminate a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-488">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-489">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-489">Description</span></span>

<span data-ttu-id="d1ff9-490">이 서비스는 LWM2M 서버에 대한 'De-Register' 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-490">This service performs a 'De-Register' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-491">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-491">Parameters</span></span>

- <span data-ttu-id="d1ff9-492">**session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-492">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-493">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-493">Return Values</span></span>

- <span data-ttu-id="d1ff9-494">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-494">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-495">**NX_LWM2M_NOT_REGISTERED**: 클라이언트가 서버에 등록되어 있지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-495">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="d1ff9-496">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-496">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="d1ff9-497">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="d1ff9-497">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="d1ff9-498">세션의 마지막 오류를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-498">Get last error of a session</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-499">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-499">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-500">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-500">Description</span></span>

<span data-ttu-id="d1ff9-501">세션이 오류 상태인 경우 이 서비스에서 세션의 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-501">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-502">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-502">Parameters</span></span>

- <span data-ttu-id="d1ff9-503">**session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-503">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-504">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-504">Return Values</span></span>

- <span data-ttu-id="d1ff9-505">**NX_SUCCESS**: 세션이 오류 상태가 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-505">**NX_SUCCESS**: The session is not in error state.</span></span>
- <span data-ttu-id="d1ff9-506">**NX_LWM2M_ADDRESS_ERROR**: 잘못된 서버 주소</span><span class="sxs-lookup"><span data-stu-id="d1ff9-506">**NX_LWM2M_ADDRESS_ERROR**: Invalid server address.</span></span>
- <span data-ttu-id="d1ff9-507">**NX_LWM2M_BUFFER_TOO_SMALL**: 요청의 페이로드가 네트워크 버퍼에 맞지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-507">**NX_LWM2M_BUFFER_TOO_SMALL**: Payload of request doesn't fit in network buffer.</span></span>
- <span data-ttu-id="d1ff9-508">**NX_LWM2M_DTLS_ERROR**: 서버와의 보안 연결을 설정 하지 못함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-508">**NX_LWM2M_DTLS_ERROR**: Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="d1ff9-509">**NX_LWM2M_ERROR**: 알 수 없는 오류</span><span class="sxs-lookup"><span data-stu-id="d1ff9-509">**NX_LWM2M_ERROR**: Unspecified error.</span></span>
- <span data-ttu-id="d1ff9-510">**NX_LWM2M_FORBIDDEN**: 서버에서 등록을 거부함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-510">**NX_LWM2M_FORBIDDEN**: Registration refused by server.</span></span>
- <span data-ttu-id="d1ff9-511">**NX_LWM2M_NOT_FOUND**: 업데이트/등록 취소 시 서버에서 클라이언트를 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-511">**NX_LWM2M_NOT_FOUND**: Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="d1ff9-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: 세션에 해당 하는 서버 개체 인스턴스가 삭제됨</span><span class="sxs-lookup"><span data-stu-id="d1ff9-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="d1ff9-513">**NX_LWM2M_TIMED_OUT**: 서버에서 응답하지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-513">**NX_LWM2M_TIMED_OUT**: No answer from server.</span></span>
- <span data-ttu-id="d1ff9-514">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-514">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="d1ff9-515">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="d1ff9-515">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="d1ff9-516">LWM2M 서버를 사용하여 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-516">Start a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-517">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-517">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="d1ff9-518">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-518">Description</span></span>

<span data-ttu-id="d1ff9-519">이 서비스는 LWM2M 서버에 대한 'Register' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-519">This service performs a 'Register' operation to a LWM2M Server.</span></span> <span data-ttu-id="d1ff9-520">서버의 서버 개체에는 해당 서버 인스턴스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-520">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="d1ff9-521">등록이 성공하면 LWM2M 클라이언트는 서버에서 추가 작업을 처리하고, 클라이언트가 등록 취소될 때까지 '업데이트' 메시지를 정기적으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-521">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="d1ff9-522">현재 활성 세션은 이 호출에서 중단되고 새 LWM2M 서버 세션으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-522">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-523">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-523">Parameters</span></span>

- <span data-ttu-id="d1ff9-524">**session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-524">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="d1ff9-525">**server_id**: LWM2M 서버의 약식 서버 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-525">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="d1ff9-526">**ip_address** 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="d1ff9-526">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="d1ff9-527">**port**: 서버의 UDP 포트</span><span class="sxs-lookup"><span data-stu-id="d1ff9-527">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-528">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-528">Return Values</span></span>

- <span data-ttu-id="d1ff9-529">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-529">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="d1ff9-530">**NX_LWM2M_NOT_FOUND**: 약식 서버 ID에 해당하는 서버 개체 인스턴스가 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-530">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="d1ff9-531">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-531">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="d1ff9-532">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="d1ff9-532">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="d1ff9-533">LWM2M 서버를 사용하여 보안 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-533">Start a secure session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-534">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-534">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="d1ff9-535">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-535">Description</span></span>

<span data-ttu-id="d1ff9-536">이 서비스는 보안 DTLS 연결을 사용하여 LWM2M 서버에 대한 'Register' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-536">This service performs a 'Register' operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="d1ff9-537">서버의 서버 개체에는 해당 서버 인스턴스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-537">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="d1ff9-538">이 함수를 호출하기 전에 DTLS 세션을 적절한 암호 그룹 및 키 자료를 사용하여 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-538">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="d1ff9-539">NX_SECURE_ENABLE_DTLS를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-539">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="d1ff9-540">각 DTLS 세션에서 통신을 위해 자체 UDP 소켓을 사용하므로 애플리케이션에서 여러 개의 보안 세션을 만드는 경우 각 세션에 대한 dtls_local_port 로컬 포트가 달라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-540">Each DTLS session uses its own UDP socket for communication, so the local port dtls_local_port must be different for each session if the application creates several secure sessions.</span></span>

<span data-ttu-id="d1ff9-541">등록이 성공하면 LWM2M 클라이언트는 서버에서 추가 작업을 처리하고, 클라이언트가 등록 취소될 때까지 '업데이트' 메시지를 정기적으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-541">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="d1ff9-542">현재 활성 세션은 이 호출에서 중단되고 새 LWM2M 서버 세션으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-542">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-543">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-543">Parameters</span></span>

- <span data-ttu-id="d1ff9-544">**session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-544">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="d1ff9-545">**server_id**: LWM2M 서버의 약식 서버 ID</span><span class="sxs-lookup"><span data-stu-id="d1ff9-545">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="d1ff9-546">**ip_address** 서버의 IP 주소</span><span class="sxs-lookup"><span data-stu-id="d1ff9-546">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="d1ff9-547">**port**: 서버의 UDP 포트</span><span class="sxs-lookup"><span data-stu-id="d1ff9-547">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="d1ff9-548">**dtls_session_ptr**: LWM2M 세션에 사용하는 DTLS 세션</span><span class="sxs-lookup"><span data-stu-id="d1ff9-548">**dtls_session_ptr**: The DTLS session to use for the LWM2M session.</span></span>
- <span data-ttu-id="d1ff9-549">**dtls_local_port**: DTLS 세션에 사용되는 로컬 UDP 포트</span><span class="sxs-lookup"><span data-stu-id="d1ff9-549">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-550">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-550">Return Values</span></span>

- <span data-ttu-id="d1ff9-551">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-551">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-552">**NX_LWM2M_NOT_FOUND**: 약식 서버 ID에 해당하는 서버 개체 인스턴스가 없음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-552">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="d1ff9-553">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-553">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="d1ff9-554">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="d1ff9-554">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="d1ff9-555">LWM2M 서버를 사용하여 세션을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-555">Update a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-556">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-557">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-557">Description</span></span>

<span data-ttu-id="d1ff9-558">이 서비스는 LWM2M 서버에 대한 'Update' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-558">This service performs an 'Update' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-559">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-559">Parameters</span></span>

- <span data-ttu-id="d1ff9-560">**session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-560">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-561">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-561">Return Values</span></span>

- <span data-ttu-id="d1ff9-562">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-562">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-563">**NX_LWM2M_NOT_REGISTERED**: 클라이언트가 서버에 등록되어 있지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-563">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="d1ff9-564">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-564">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="d1ff9-565">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="d1ff9-565">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="d1ff9-566">LWM2M 클라이언트의 잠금을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-566">Unlock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-567">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-567">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-568">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-568">Description</span></span>

<span data-ttu-id="d1ff9-569">이전에 nx_lwm2m_client_unlock()을 호출하여 잠긴 LWM2M 클라이언트의 잠금을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-569">This service unlocks the LWM2M Client previoulsy locked by a call to nx_lwm2m_client_unlock().</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-570">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-570">Parameters</span></span>

- <span data-ttu-id="d1ff9-571">**client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-571">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-572">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-572">Return Values</span></span>

- <span data-ttu-id="d1ff9-573">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-573">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-574">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-574">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_create"></a><span data-ttu-id="d1ff9-575">nx_lwm2m_firmware_create</span><span class="sxs-lookup"><span data-stu-id="d1ff9-575">nx_lwm2m_firmware_create</span></span>

<span data-ttu-id="d1ff9-576">펌웨어 업데이트 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-576">Create Firmware Update Object</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-577">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-577">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="d1ff9-578">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-578">Description</span></span>

<span data-ttu-id="d1ff9-579">이 서비스는 펌웨어 업데이트 개체를 초기화하고, 이 개체를 이전에 만든 LWM2M 클라이언트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-579">This service initializes a Firmware Update Object and adds the Object to a previously created LWM2M Client.</span></span> <span data-ttu-id="d1ff9-580">펌웨어 업데이트 개체는 LWM2M 서버와 통신하기 위한 리소스를 구현하지만, 애플리케이션에서 펌웨어에 대한 실제 작업(펌웨어 다운로드, 저장 및 업데이트)을 구현하는 콜백을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-580">The Firmware Update Object implements the resources for communicating with a LWM2M Server but the application must provide callbacks for implementing the actual operations on the firmware (dowloading, storing, and updating the firmware).</span></span>

<span data-ttu-id="d1ff9-581">protocols 매개 변수는 '패키지 URI' 리소스를 사용하여 펌웨어를 검색하기 위해 애플리케이션에서 지원하는 프로토콜을 나타내며, 다음과 같은 플래그가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-581">The protocols parameter indicates which protocols are supported by the application for retrieving the firmware with the 'Package URI' resource, the following flags are defined:</span></span>

<span data-ttu-id="d1ff9-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS</span><span class="sxs-lookup"><span data-stu-id="d1ff9-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-583">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-583">Parameters</span></span>

- <span data-ttu-id="d1ff9-584">**firmware_ptr**: 펌웨어 개체 제어 블록에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-584">**firmware_ptr**: Pointer to the Firmware Object control block.</span></span>
- <span data-ttu-id="d1ff9-585">**client_ptr**: 이전에 만든 LWM2M 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-585">**client_ptr**: Pointer to previsously created LWM2M Client.</span></span>
- <span data-ttu-id="d1ff9-586">**protocols**: 패키지 URI 리소스에서 지원하는 프로토콜을 나타내는 플래그</span><span class="sxs-lookup"><span data-stu-id="d1ff9-586">**protocols**: Flags indicating which protocols are supported by the Package URI resource.</span></span>
- <span data-ttu-id="d1ff9-587">**package_callback**: NULL이어야 함[미정].</span><span class="sxs-lookup"><span data-stu-id="d1ff9-587">**package_callback**: Must be NULL [TBD].</span></span>
- <span data-ttu-id="d1ff9-588">**package_uri_callback**: 패키지 URI 리소스를 구현하는 데 사용되는 콜백</span><span class="sxs-lookup"><span data-stu-id="d1ff9-588">**package_uri_callback**: Callback used to implement the Package URI resource.</span></span>
- <span data-ttu-id="d1ff9-589">**update_callback**: 업데이트 리소스를 구현하는 데 사용되는 콜백</span><span class="sxs-lookup"><span data-stu-id="d1ff9-589">**update_callback**: Callback used to implement the Update resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-590">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-590">Return Values</span></span>

- <span data-ttu-id="d1ff9-591">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-591">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-592">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-592">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_package_info_set"></a><span data-ttu-id="d1ff9-593">nx_lwm2m_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="d1ff9-593">nx_lwm2m_firmware_package_info_set</span></span>

<span data-ttu-id="d1ff9-594">펌웨어 업데이트 패키지 정보를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-594">Set Firmware Update Package Information</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-595">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-595">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a><span data-ttu-id="d1ff9-596">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-596">Description</span></span>

<span data-ttu-id="d1ff9-597">이 서비스는 펌웨어 업데이트 개체의 'PkgName' (6) 및 'PkgVersion' (7) 리소스에 대한 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-597">This service changes the values of the 'PkgName' (6) and 'PkgVersion' (7) resources of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-598">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-598">Parameters</span></span>

- <span data-ttu-id="d1ff9-599">**firmware_ptr**: 펌웨어 업데이트 개체에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-599">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="d1ff9-600">**name**: 패키지 이름의 새 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-600">**name**: The new value of the Package Name.</span></span>
- <span data-ttu-id="d1ff9-601">**version**: 패키지 버전의 새 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-601">**version**: The new value of the Package Version.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-602">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-602">Return Values</span></span>

- <span data-ttu-id="d1ff9-603">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-603">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-604">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-604">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_result_set"></a><span data-ttu-id="d1ff9-605">nx_lwm2m_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="d1ff9-605">nx_lwm2m_firmware_result_set</span></span>

<span data-ttu-id="d1ff9-606">펌웨어 업데이트 결과를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-606">Set Firmware Update Result</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-607">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-607">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a><span data-ttu-id="d1ff9-608">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-608">Description</span></span>

<span data-ttu-id="d1ff9-609">이 서비스는 펌웨어 업데이트 개체의 'Update Result' (5) 리소스에 대한 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-609">This service changes the value of the 'Update Result' (5) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-610">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-610">Parameters</span></span>

- <span data-ttu-id="d1ff9-611">**firmware_ptr**: 펌웨어 업데이트 개체에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-611">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="d1ff9-612">**result**: 업데이트 결과 리소스의 새 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-612">**result**: The new value of the Update Result resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-613">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-613">Return Values</span></span>

- <span data-ttu-id="d1ff9-614">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-614">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-615">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-615">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_state_set"></a><span data-ttu-id="d1ff9-616">nx_lwm2m_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="d1ff9-616">nx_lwm2m_firmware_state_set</span></span>

<span data-ttu-id="d1ff9-617">펌웨어 업데이트 업데이트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-617">Set Firmware Update State</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-618">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-618">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a><span data-ttu-id="d1ff9-619">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-619">Description</span></span>

<span data-ttu-id="d1ff9-620">이 서비스는 펌웨어 업데이트 개체의 'State' (3) 리소스에 대한 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-620">This service changes the value of the 'State' (3) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-621">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-621">Parameters</span></span>

- <span data-ttu-id="d1ff9-622">**firmware_ptr**: 펌웨어 업데이트 개체에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-622">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="d1ff9-623">**state**: 상태 리소스의 새 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-623">**state**: The new value of the State resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-624">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-624">Return Values</span></span>

- <span data-ttu-id="d1ff9-625">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-625">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-626">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-626">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_object_resource_changed"></a><span data-ttu-id="d1ff9-627">nx_lwm2m_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="d1ff9-627">nx_lwm2m_object_resource_changed</span></span>

<span data-ttu-id="d1ff9-628">개체 인스턴스의 리소스 값에 대한 변경 신호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-628">Signal change of a resource value of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-629">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-629">Prototype</span></span>

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="d1ff9-630">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-630">Description</span></span>

<span data-ttu-id="d1ff9-631">이 서비스는 개체 구현에서 해당 리소스 값 중 하나가 변경되었다는 신호를 LWM2M 클라이언트에 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-631">This service is used by an Object implementation to signals the LWM2M Client that one of its resource value has changed.</span></span> <span data-ttu-id="d1ff9-632">LWM2M 서버에서 리소스를 관찰하는 경우 LWM2M 클라이언트에서 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-632">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-633">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-633">Parameters</span></span>

- <span data-ttu-id="d1ff9-634">**object_ptr**: 개체 구현에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-634">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="d1ff9-635">**instance_ptr**: 개체 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-635">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="d1ff9-636">**resource**: 변경된 리소스를 설명하는 구조체에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-636">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-637">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-637">Return Values</span></span>

- <span data-ttu-id="d1ff9-638">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-638">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-639">NX_PTR_ERROR: 잘못된 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-639">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_resource_get_boolean"></a><span data-ttu-id="d1ff9-640">nx_lwm2m_resource_get_boolean</span><span class="sxs-lookup"><span data-stu-id="d1ff9-640">nx_lwm2m_resource_get_boolean</span></span>

<span data-ttu-id="d1ff9-641">부울 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-641">Get the value of a Boolean Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-642">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-642">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-643">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-643">Description</span></span>

<span data-ttu-id="d1ff9-644">이 서비스는 부울 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-644">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-645">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-645">Parameters</span></span>

- <span data-ttu-id="d1ff9-646">**value**: 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-646">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="d1ff9-647">**bool_ptr**: 대상 부울 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-647">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-648">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-648">Return Values</span></span>

- <span data-ttu-id="d1ff9-649">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-649">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-650">**NX_LWM2M_BAD_ENCODING**: 리소스 값이 부울 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-650">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_get_float32"></a><span data-ttu-id="d1ff9-651">nx_lwm2m_resource_get_float32</span><span class="sxs-lookup"><span data-stu-id="d1ff9-651">nx_lwm2m_resource_get_float32</span></span>

<span data-ttu-id="d1ff9-652">32비트 부동 소수점 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-652">Get the value of a 32-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-653">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-653">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-654">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-654">Description</span></span>

<span data-ttu-id="d1ff9-655">이 서비스는 32비트 부동 소수점 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-655">The service retrieves the value of a 32-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-656">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-656">Parameters</span></span>

- <span data-ttu-id="d1ff9-657">**value**: 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-657">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="d1ff9-658">**float32_ptr**: 대상 32비트 부동 소수점 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-658">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-659">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-659">Return Values</span></span>

- <span data-ttu-id="d1ff9-660">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-660">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-661">**NX_LWM2M_BAD_ENCODING**: 리소스 값이 부동 소수점 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-661">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_float64"></a><span data-ttu-id="d1ff9-662">nx_lwm2m_resource_get_float64</span><span class="sxs-lookup"><span data-stu-id="d1ff9-662">nx_lwm2m_resource_get_float64</span></span>

<span data-ttu-id="d1ff9-663">64비트 부동 소수점 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-663">Get the value of a 64-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-664">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-664">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-665">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-665">Description</span></span>

<span data-ttu-id="d1ff9-666">이 서비스는 64비트 부동 소수점 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-666">The service retrieves the value of a 64-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-667">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-667">Parameters</span></span>

- <span data-ttu-id="d1ff9-668">**value**: 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-668">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="d1ff9-669">**float64_ptr**: 대상 64비트 부동 소수점 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-669">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-670">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-670">Return Values</span></span>

- <span data-ttu-id="d1ff9-671">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-671">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-672">**NX_LWM2M_BAD_ENCODING**: 리소스 값이 부동 소수점 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-672">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_integer32"></a><span data-ttu-id="d1ff9-673">nx_lwm2m_resource_get_integer32</span><span class="sxs-lookup"><span data-stu-id="d1ff9-673">nx_lwm2m_resource_get_integer32</span></span>

<span data-ttu-id="d1ff9-674">32비트 정수 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-674">Get the value of a 32-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-675">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-675">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-676">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-676">Description</span></span>

<span data-ttu-id="d1ff9-677">이 서비스는 32비트 정수 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-677">The service retrieves the value of a 32-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-678">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-678">Parameters</span></span>

- <span data-ttu-id="d1ff9-679">**value**: 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-679">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="d1ff9-680">**int32_ptr**: 대상 32비트 정수 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-680">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-681">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-681">Return Values</span></span>

- <span data-ttu-id="d1ff9-682">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-682">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-683">**NX_LWM2M_BAD_ENCODING**: 리소스 값이 정수 값이 아니거나 정수 값이 32비트 숫자에 맞지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-683">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_get_integer64"></a><span data-ttu-id="d1ff9-684">nx_lwm2m_resource_get_integer64</span><span class="sxs-lookup"><span data-stu-id="d1ff9-684">nx_lwm2m_resource_get_integer64</span></span>

<span data-ttu-id="d1ff9-685">64비트 정수 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-685">Get the value of a 64-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-686">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-686">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-687">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-687">Description</span></span>

<span data-ttu-id="d1ff9-688">이 서비스는 64비트 정수 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-688">The service retrieves the value of a 64-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-689">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-689">Parameters</span></span>

- <span data-ttu-id="d1ff9-690">**value**: 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-690">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="d1ff9-691">**int64_ptr**: 대상 64비트 정수 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-691">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-692">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-692">Return Values</span></span>

- <span data-ttu-id="d1ff9-693">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-693">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-694">**NX_LWM2M_BAD_ENCODING**: 리소스 값이 정수 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-694">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_get_objlnk"></a><span data-ttu-id="d1ff9-695">nx_lwm2m_resource_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="d1ff9-695">nx_lwm2m_resource_get_objlnk</span></span>

<span data-ttu-id="d1ff9-696">개체 링크 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-696">Get the value of an Object Link Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-697">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-697">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-698">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-698">Description</span></span>

<span data-ttu-id="d1ff9-699">이 서비스는 개체 링크 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-699">The service retrieves the value of an Object Link Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-700">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-700">Parameters</span></span>

- <span data-ttu-id="d1ff9-701">**value**: 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-701">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="d1ff9-702">**objlnk_ptr**: 대상 개체 링크 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-702">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-703">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-703">Return Values</span></span>

- <span data-ttu-id="d1ff9-704">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-704">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-705">**NX_LWM2M_BAD_ENCODING**: 리소스 값이 개체 링크 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-705">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_get_opaque"></a><span data-ttu-id="d1ff9-706">nx_lwm2m_resource_get_opaque</span><span class="sxs-lookup"><span data-stu-id="d1ff9-706">nx_lwm2m_resource_get_opaque</span></span>

<span data-ttu-id="d1ff9-707">불투명 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-707">Get the value of an Opaque Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-708">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-708">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-709">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-709">Description</span></span>

<span data-ttu-id="d1ff9-710">이 서비스는 불투명 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-710">The service retrieves the value of an Opaque Resource.</span></span>

<span data-ttu-id="d1ff9-711">불투명 리소스 값은 버퍼 및 길이에 대한 포인터로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-711">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-712">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-712">Parameters</span></span>

- <span data-ttu-id="d1ff9-713">**value**: 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-713">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="d1ff9-714">**opaque_ptr_ptr**: 대상 불투명 버퍼 포인터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-714">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="d1ff9-715">**opaque_length_ptr**: 대상 불투명 버퍼 길이에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-715">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-716">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-716">Return Values</span></span>

- <span data-ttu-id="d1ff9-717">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-717">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-718">**NX_LWM2M_BAD_ENCODING**: 리소스 값이 불투명 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-718">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_get_string"></a><span data-ttu-id="d1ff9-719">nx_lwm2m_resource_get_string</span><span class="sxs-lookup"><span data-stu-id="d1ff9-719">nx_lwm2m_resource_get_string</span></span>

<span data-ttu-id="d1ff9-720">문자열 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-720">Get the value of a String Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-721">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-721">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-722">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-722">Description</span></span>

<span data-ttu-id="d1ff9-723">이 서비스는 문자열 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-723">The service retrieves the value of a String Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-724">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-724">Parameters</span></span>

- <span data-ttu-id="d1ff9-725">**value**: 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-725">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="d1ff9-726">**string_ptr_ptr**: 대상 문자열 포인터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-726">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="d1ff9-727">**string_length_ptr**: 대상 문자열 길이에 대한 포인터이며,</span><span class="sxs-lookup"><span data-stu-id="d1ff9-727">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="d1ff9-728">문자열이 null로 끝나는 경우 NULL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-728">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-729">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-729">Return Values</span></span>

- <span data-ttu-id="d1ff9-730">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-730">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-731">**NX_LWM2M_BAD_ENCODING**: 리소스 값이 문자열 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-731">**NX_LWM2M_BAD_ENCODING**: The resource value is not a String value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a><span data-ttu-id="d1ff9-732">nx_lwm2m_resource_multiple_get_boolean</span><span class="sxs-lookup"><span data-stu-id="d1ff9-732">nx_lwm2m_resource_multiple_get_boolean</span></span>

<span data-ttu-id="d1ff9-733">부울 리소스 다중 리소스 인스턴스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-733">Get the value of a Boolean Resource Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-734">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-734">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-735">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-735">Description</span></span>

<span data-ttu-id="d1ff9-736">이 서비스는 여러 리소스에서 부울 리소스 인스턴스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-736">The service retrieves the value of a Boolean Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-737">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-737">Parameters</span></span>

- <span data-ttu-id="d1ff9-738">**value**: 다중 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-738">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="d1ff9-739">**index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="d1ff9-739">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="d1ff9-740">**instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-740">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="d1ff9-741">**bool_ptr**: 대상 부울 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-741">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-742">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-742">Return Values</span></span>

- <span data-ttu-id="d1ff9-743">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-743">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-744">**NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남</span><span class="sxs-lookup"><span data-stu-id="d1ff9-744">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="d1ff9-745">**NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 부울 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-745">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float32"></a><span data-ttu-id="d1ff9-746">nx_lwm2m_resource_multiple_get_float32</span><span class="sxs-lookup"><span data-stu-id="d1ff9-746">nx_lwm2m_resource_multiple_get_float32</span></span>

<span data-ttu-id="d1ff9-747">32비트 부동 소수점 다중 리소스 인스턴스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-747">Get the value of a 32-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-748">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-748">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-749">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-749">Description</span></span>

<span data-ttu-id="d1ff9-750">이 서비스는 여러 리소스에서 32비트 부동 소수점 리소스 인스턴스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-750">The service retrieves the value of a 32-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-751">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-751">Parameters</span></span>

- <span data-ttu-id="d1ff9-752">**value**: 다중 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-752">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="d1ff9-753">**index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="d1ff9-753">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="d1ff9-754">**instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-754">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="d1ff9-755">**float32_ptr**: 대상 32비트 부동 소수점 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-755">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-756">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-756">Return Values</span></span>

- <span data-ttu-id="d1ff9-757">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-757">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-758">**NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남</span><span class="sxs-lookup"><span data-stu-id="d1ff9-758">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="d1ff9-759">**NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 부동 소수점 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-759">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float64"></a><span data-ttu-id="d1ff9-760">nx_lwm2m_resource_multiple_get_float64</span><span class="sxs-lookup"><span data-stu-id="d1ff9-760">nx_lwm2m_resource_multiple_get_float64</span></span>

<span data-ttu-id="d1ff9-761">64비트 부동 소수점 다중 리소스 인스턴스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-761">Get the value of a 64-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-762">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-762">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-763">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-763">Description</span></span>

<span data-ttu-id="d1ff9-764">이 서비스는 여러 리소스에서 64비트 부동 소수점 리소스 인스턴스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-764">The service retrieves the value of a 64-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-765">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-765">Parameters</span></span>

- <span data-ttu-id="d1ff9-766">**value**: 다중 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-766">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="d1ff9-767">**index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="d1ff9-767">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="d1ff9-768">**instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-768">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="d1ff9-769">**float64_ptr**: 대상 64비트 부동 소수점 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-769">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-770">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-770">Return Values</span></span>

- <span data-ttu-id="d1ff9-771">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-771">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-772">**NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남</span><span class="sxs-lookup"><span data-stu-id="d1ff9-772">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="d1ff9-773">**NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 부동 소수점 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-773">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a><span data-ttu-id="d1ff9-774">nx_lwm2m_resource_multiple_get_integer32</span><span class="sxs-lookup"><span data-stu-id="d1ff9-774">nx_lwm2m_resource_multiple_get_integer32</span></span>

<span data-ttu-id="d1ff9-775">32비트 정수 다중 리소스 인스턴스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-775">Get the value of a 32-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-776">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-776">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-777">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-777">Description</span></span>

<span data-ttu-id="d1ff9-778">이 서비스는 여러 리소스에서 32비트 정수 리소스 인스턴스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-778">The service retrieves the value of a 32-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-779">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-779">Parameters</span></span>

- <span data-ttu-id="d1ff9-780">**value**: 다중 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-780">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="d1ff9-781">**index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="d1ff9-781">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="d1ff9-782">**instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-782">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="d1ff9-783">**int32_ptr**: 대상 32비트 정수 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-783">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-784">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-784">Return Values</span></span>

- <span data-ttu-id="d1ff9-785">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-785">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-786">**NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남</span><span class="sxs-lookup"><span data-stu-id="d1ff9-786">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="d1ff9-787">**NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나, 리소스 값이 정수 값이 아니거나, 정수 값이 32비트 숫자에 맞지 않음</span><span class="sxs-lookup"><span data-stu-id="d1ff9-787">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a><span data-ttu-id="d1ff9-788">nx_lwm2m_resource_multiple_get_integer64</span><span class="sxs-lookup"><span data-stu-id="d1ff9-788">nx_lwm2m_resource_multiple_get_integer64</span></span>

<span data-ttu-id="d1ff9-789">64비트 정수 다중 리소스 인스턴스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-789">Get the value of a 64-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-790">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-790">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-791">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-791">Description</span></span>

<span data-ttu-id="d1ff9-792">이 서비스는 여러 리소스에서 64비트 정수 리소스 인스턴스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-792">The service retrieves the value of a 64-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-793">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-793">Parameters</span></span>

- <span data-ttu-id="d1ff9-794">**value**: 다중 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-794">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="d1ff9-795">**index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="d1ff9-795">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="d1ff9-796">**instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-796">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="d1ff9-797">**int64_ptr**: 대상 64비트 정수 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-797">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-798">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-798">Return Values</span></span>

- <span data-ttu-id="d1ff9-799">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-799">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-800">**NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남</span><span class="sxs-lookup"><span data-stu-id="d1ff9-800">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="d1ff9-801">**NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 정수 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-801">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a><span data-ttu-id="d1ff9-802">nx_lwm2m_resource_multiple_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="d1ff9-802">nx_lwm2m_resource_multiple_get_objlnk</span></span>

<span data-ttu-id="d1ff9-803">개체 링크 다중 리소스 인스턴스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-803">Get the value of an Object Link Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-804">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-804">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-805">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-805">Description</span></span>

<span data-ttu-id="d1ff9-806">이 서비스는 여러 리소스에서 개체 링크 리소스 인스턴스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-806">The service retrieves the value of an Object Link Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-807">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-807">Parameters</span></span>

- <span data-ttu-id="d1ff9-808">**value**: 다중 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-808">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="d1ff9-809">**index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="d1ff9-809">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="d1ff9-810">**instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-810">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="d1ff9-811">**objlnk_ptr**: 대상 개체 링크 값에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-811">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-812">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-812">Return Values</span></span>

- <span data-ttu-id="d1ff9-813">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-813">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-814">**NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남</span><span class="sxs-lookup"><span data-stu-id="d1ff9-814">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="d1ff9-815">**NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 개체 링크 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-815">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a><span data-ttu-id="d1ff9-816">nx_lwm2m_resource_multiple_get_opaque</span><span class="sxs-lookup"><span data-stu-id="d1ff9-816">nx_lwm2m_resource_multiple_get_opaque</span></span>

<span data-ttu-id="d1ff9-817">불투명 다중 리소스 인스턴스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-817">Get the value of an Opaque Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-818">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-818">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-819">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-819">Description</span></span>

<span data-ttu-id="d1ff9-820">이 서비스는 여러 리소스에서 불투명 리소스 인스턴스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-820">The service retrieves the value of an Opaque Resource Instance from a Multiple Resource.</span></span>

<span data-ttu-id="d1ff9-821">불투명 리소스 값은 버퍼 및 길이에 대한 포인터로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-821">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-822">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-822">Parameters</span></span>

- <span data-ttu-id="d1ff9-823">**value**: 다중 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-823">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="d1ff9-824">**index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="d1ff9-824">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="d1ff9-825">**instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-825">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="d1ff9-826">**opaque_ptr_ptr**: 대상 불투명 버퍼 포인터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-826">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="d1ff9-827">**opaque_length_ptr**: 대상 불투명 버퍼 길이에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-827">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-828">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-828">Return Values</span></span>

- <span data-ttu-id="d1ff9-829">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-829">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-830">**NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남</span><span class="sxs-lookup"><span data-stu-id="d1ff9-830">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="d1ff9-831">**NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 불투명 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-831">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_string"></a><span data-ttu-id="d1ff9-832">nx_lwm2m_resource_multiple_get_string</span><span class="sxs-lookup"><span data-stu-id="d1ff9-832">nx_lwm2m_resource_multiple_get_string</span></span>

<span data-ttu-id="d1ff9-833">문자열 다중 리소스 인스턴스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-833">Get the value of a String Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d1ff9-834">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d1ff9-834">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="d1ff9-835">Description</span><span class="sxs-lookup"><span data-stu-id="d1ff9-835">Description</span></span>

<span data-ttu-id="d1ff9-836">이 서비스는 여러 리소스에서 문자열 리소스 인스턴스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-836">The service retrieves the value of a String Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="d1ff9-837">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d1ff9-837">Parameters</span></span>

- <span data-ttu-id="d1ff9-838">**value**: 다중 리소스 값 설명에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-838">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="d1ff9-839">**index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스</span><span class="sxs-lookup"><span data-stu-id="d1ff9-839">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="d1ff9-840">**instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-840">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="d1ff9-841">**string_ptr_ptr**: 대상 문자열 포인터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d1ff9-841">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="d1ff9-842">**string_length_ptr**: 대상 문자열 길이에 대한 포인터이며,</span><span class="sxs-lookup"><span data-stu-id="d1ff9-842">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="d1ff9-843">문자열이 null로 끝나는 경우 NULL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1ff9-843">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="d1ff9-844">반환 값</span><span class="sxs-lookup"><span data-stu-id="d1ff9-844">Return Values</span></span>

- <span data-ttu-id="d1ff9-845">**NX_SUCCESS**: 작업이 성공함</span><span class="sxs-lookup"><span data-stu-id="d1ff9-845">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="d1ff9-846">**NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남</span><span class="sxs-lookup"><span data-stu-id="d1ff9-846">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="d1ff9-847">**NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 인스턴스 값이 문자열 값이 아님</span><span class="sxs-lookup"><span data-stu-id="d1ff9-847">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the instance value is not a String value.</span></span>
