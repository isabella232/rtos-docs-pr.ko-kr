---
title: 챕터 4 - LWM2M 클라이언트 서비스 설명
description: 이 챕터에서는 모든 LWM2M 클라이언트 서비스를 알파벳 순서로 설명합니다.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810746"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a><span data-ttu-id="70980-103">챕터 4 - LWM2M 클라이언트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="70980-103">Chapter 4  Description of LWM2M CLIENT Services</span></span>

<span data-ttu-id="70980-104">이 챕터에서는 아래에 나열된 모든 LWM2M 클라이언트 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-104">This chapter contains a description of all LWM2M Client services listed below in alphabetic order.</span></span>

<span data-ttu-id="70980-105">다음 API 설명의 "반환 값" 섹션에서 **굵게 표시된** 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the  **NX_DISABLE_ERROR_CHECKING** define that is used to disable API  error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="70980-106">**LWM2M 클라이언트 관리:**</span><span class="sxs-lookup"><span data-stu-id="70980-106">**LWM2M Client Management:**</span></span>

- <span data-ttu-id="70980-107">nx_lwm2m_client_create: *LWM2M 클라이언트 만들기*</span><span class="sxs-lookup"><span data-stu-id="70980-107">nx_lwm2m_client_create: *Create LWM2M Client*</span></span>

- <span data-ttu-id="70980-108">nx_lwm2m_client_delete: *LWM2M 클라이언트 삭제하기*</span><span class="sxs-lookup"><span data-stu-id="70980-108">nx_lwm2m_client_delete: *Delete LWM2M Client*</span></span>

- <span data-ttu-id="70980-109">nx_lwm2m_client_lock: *LWM2M 클라이언트 잠그기*</span><span class="sxs-lookup"><span data-stu-id="70980-109">nx_lwm2m_client_lock: *Lock LWM2M Client*</span></span>

- <span data-ttu-id="70980-110">nx_lwm2m_client_unlock: *LWM2M 클라이언트 잠금 해제하기*</span><span class="sxs-lookup"><span data-stu-id="70980-110">nx_lwm2m_client_unlock: *Unlock LWM2M Client*</span></span>

<span data-ttu-id="70980-111">**LWM2M 클라이언트 세션 관리:**</span><span class="sxs-lookup"><span data-stu-id="70980-111">**LWM2M Client Session Management:**</span></span>

- <span data-ttu-id="70980-112">nx_lwm2m_client_session_create: *LWM2M 클라이언트 세션 만들기*</span><span class="sxs-lookup"><span data-stu-id="70980-112">nx_lwm2m_client_session_create: *Create LWM2M Client Session*</span></span>

- <span data-ttu-id="70980-113">nx_lwm2m_client_session_delete: *LWM2M 클라이언트 세션 삭제*</span><span class="sxs-lookup"><span data-stu-id="70980-113">nx_lwm2m_client_session_delete: *Delete LWM2M Client Session*</span></span>

- <span data-ttu-id="70980-114">nx_lwm2m_client_session_bootstrap: *부트스트랩 서버를 사용하여 세션 시작*</span><span class="sxs-lookup"><span data-stu-id="70980-114">nx_lwm2m_client_session_bootstrap: *Start a session with a Bootstrap Server*</span></span>

- <span data-ttu-id="70980-115">nx_lwm2m_client_session_bootstrap_dtls: *부트스트랩 서버를 사용하여 보안 세션 시작*</span><span class="sxs-lookup"><span data-stu-id="70980-115">nx_lwm2m_client_session_bootstrap_dtls: *Start a secure session with a Bootstrap Server*</span></span>

- <span data-ttu-id="70980-116">nx_lwm2m_client_session_register_info_get: *LWM2M 서버 등록 정보 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-116">nx_lwm2m_client_session_register_info_get: *Get LWM2M Server register info*</span></span>

- <span data-ttu-id="70980-117">nx_lwm2m_client_session_register: *LWM2M 서버를 사용하여 세션 시작*</span><span class="sxs-lookup"><span data-stu-id="70980-117">nx_lwm2m_client_session_register: *Start a session with a LWM2M Server*</span></span>

- <span data-ttu-id="70980-118">nx_lwm2m_client_session_register_dtls: *LWM2M 서버를 사용하여 보안 세션 시작*</span><span class="sxs-lookup"><span data-stu-id="70980-118">nx_lwm2m_client_session_register_dtls: *Start a secure session with a LWM2M Server*</span></span>

- <span data-ttu-id="70980-119">nx_lwm2m_client_session_update: *LWM2M 서버를 사용하여 세션 업데이트*</span><span class="sxs-lookup"><span data-stu-id="70980-119">nx_lwm2m_client_session_update: *Update a session with a LWM2M Server*</span></span>

- <span data-ttu-id="70980-120">nx_lwm2m_client_session_deregister: *LWM2M 서버를 사용하여 세션 종료*</span><span class="sxs-lookup"><span data-stu-id="70980-120">nx_lwm2m_client_session_deregister: *Terminate a session with a LWM2M Server*</span></span>

- <span data-ttu-id="70980-121">nx_lwm2m_client_session_error_get: *세션의 마지막 오류 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-121">nx_lwm2m_client_session_error_get: *Get last error of a session*</span></span>

<span data-ttu-id="70980-122">**디바이스 개체 구현:**</span><span class="sxs-lookup"><span data-stu-id="70980-122">**Device Object Implementation:**</span></span>

- <span data-ttu-id="70980-123">nx_lwm2m_client_device_callbacks_set: *디바이스 개체 애플리케이션 호출 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-123">nx_lwm2m_client_device_callbacks_set: *Set Device Object application callbacks*</span></span>

- <span data-ttu-id="70980-124">nx_lwm2m_client_device_error_push: *디바이스 개체에 오류 코드 추가*</span><span class="sxs-lookup"><span data-stu-id="70980-124">nx_lwm2m_client_device_error_push: *Add error code to Device Object*</span></span>

- <span data-ttu-id="70980-125">nx_lwm2m_client_device_error_reset: *디바이스 개체의 오류 코드 초기화*</span><span class="sxs-lookup"><span data-stu-id="70980-125">nx_lwm2m_client_device_error_reset: *Reset error codes of Device Object*</span></span>

- <span data-ttu-id="70980-126">nx_lwm2m_client_device_resource_changed: *디바이스 개체 리소스에 대한 변경 신호 보내기*</span><span class="sxs-lookup"><span data-stu-id="70980-126">nx_lwm2m_client_device_resource_changed: *Signal change of Device Object resource*</span></span>

<span data-ttu-id="70980-127">**펌웨어 업데이트 개체 구현:**</span><span class="sxs-lookup"><span data-stu-id="70980-127">**Firmware Update Object Implementation:**</span></span>

- <span data-ttu-id="70980-128">nx_lwm2m_firmware_create: *펌웨어 업데이트 개체 만들기*</span><span class="sxs-lookup"><span data-stu-id="70980-128">nx_lwm2m_firmware_create: *Create Firmware Update Object*</span></span>

- <span data-ttu-id="70980-129">nx_lwm2m_firmware_package_info_set: *펌웨어 업데이트 패키지 정보 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-129">nx_lwm2m_firmware_package_info_set: *Set Firmware Update Package Information*</span></span>

- <span data-ttu-id="70980-130">nx_lwm2m_firmware_result_set: *펌웨어 업데이트 결과 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-130">nx_lwm2m_firmware_result_set: *Set Firmware Update Result*</span></span>

- <span data-ttu-id="70980-131">nx_lwm2m_firmware_state_set: *펌웨어 업데이트 상태 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-131">nx_lwm2m_firmware_state_set: *Set Firmware Update State*</span></span>

<span data-ttu-id="70980-132">**사용자 지정 개체 구현:**</span><span class="sxs-lookup"><span data-stu-id="70980-132">**Custom Objects Implementation:**</span></span>

- <span data-ttu-id="70980-133">nx_lwm2m_client_object_add: *LWM2M 클라이언트에 개체 구현 추가*</span><span class="sxs-lookup"><span data-stu-id="70980-133">nx_lwm2m_client_object_add: *Add Object implementation to LWM2M Client*</span></span>

- <span data-ttu-id="70980-134">nx_lwm2m_client_object_remove: *LWM2M 클라이언트에서 개체 구현 제거*</span><span class="sxs-lookup"><span data-stu-id="70980-134">nx_lwm2m_client_object_remove: *Remove Object implementation from LWM2M Client*</span></span>

- <span data-ttu-id="70980-135">nx_lwm2m_client_object_instance_add: *LWM2M 클라이언트에 개체 인스턴스 추가*</span><span class="sxs-lookup"><span data-stu-id="70980-135">nx_lwm2m_client_object_instance_add: *Add Object Instance to LWM2M Client*</span></span>

- <span data-ttu-id="70980-136">nx_lwm2m_client_object_instance_remove: *LWM2M 클라이언트에서 개체 인스턴스 제거*</span><span class="sxs-lookup"><span data-stu-id="70980-136">nx_lwm2m_client_object_instance_remove: *Remove Object Instance from LWM2M Client*</span></span>

- <span data-ttu-id="70980-137">nx_lwm2m_object_resource_changed: *개체 인스턴스의 리소스 값에 대한 변경 신호 보내기*</span><span class="sxs-lookup"><span data-stu-id="70980-137">nx_lwm2m_object_resource_changed: *Signal change of a resource value of an Object Instance*</span></span>

<span data-ttu-id="70980-138">**로컬 디바이스 관리**</span><span class="sxs-lookup"><span data-stu-id="70980-138">**Local Device Management**</span></span>

- <span data-ttu-id="70980-139">nx_lwm2m_client_object_create: *새 개체 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="70980-139">nx_lwm2m_client_object_create: *Create a new Object Instance*</span></span>

- <span data-ttu-id="70980-140">nx_lwm2m_client_object_delete: *개체 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="70980-140">nx_lwm2m_client_object_delete: *Delete an Object Instance*</span></span>

- <span data-ttu-id="70980-141">nx_lwm2m_client_object_discover: *개체 인스턴스의 리소스 검색*</span><span class="sxs-lookup"><span data-stu-id="70980-141">nx_lwm2m_client_object_discover: *Discover resources of an Object Instance*</span></span>

- <span data-ttu-id="70980-142">nx_lwm2m_client_object_execute: *개체 인스턴스의 리소스 실행*</span><span class="sxs-lookup"><span data-stu-id="70980-142">nx_lwm2m_client_object_execute: *Execute resource of an Object Instance*</span></span>

- <span data-ttu-id="70980-143">nx_lwm2m_client_object_next_get: *LWM2M 클라이언트에서 구현하는 개체의 목록 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-143">nx_lwm2m_client_object_next_get: *Get the list of Objects implemented by the LWM2M Client*</span></span>

- <span data-ttu-id="70980-144">nx_lwm2m_client_object_instance_get_next: *개체의 인스턴스 목록 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-144">nx_lwm2m_client_object_instance_next_get: *Get the list of Instances of an Object*</span></span>

- <span data-ttu-id="70980-145">nx_lwm2m_client_object_read: *개체 인스턴스의 리소스 값 읽기*</span><span class="sxs-lookup"><span data-stu-id="70980-145">nx_lwm2m_client_object_read: *Read resources values of an Object Instance*</span></span>

- <span data-ttu-id="70980-146">nx_lwm2m_client_object_write: *개체 인스턴스의 리소스 값 변경*</span><span class="sxs-lookup"><span data-stu-id="70980-146">nx_lwm2m_client_object_write: *Change resources values of an Object instance*</span></span>

<span data-ttu-id="70980-147">**리소스 정보 및 값 설정:**</span><span class="sxs-lookup"><span data-stu-id="70980-147">**Resources Info and Values Setting:**</span></span>

- <span data-ttu-id="70980-148">nx_lwm2m_client_resource_info_set: *리소스 정보 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-148">nx_lwm2m_client_resource_info_set: *Set the resource info*</span></span>

- <span data-ttu-id="70980-149">nx_lwm2m_client_resource_string_set: *리소스 값을 문자열로 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-149">nx_lwm2m_client_resource_string_set: *Set the resource value as string*</span></span>

- <span data-ttu-id="70980-150">nx_lwm2m_client_resource_integer32_set: *리소스 값을 32비트 정수로 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-150">nx_lwm2m_client_resource_integer32_set: *Set the resource value as 32-Bit integer*</span></span>

- <span data-ttu-id="70980-151">nx_lwm2m_client_resource_integer64_set: *리소스 값을 64비트 정수로 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-151">nx_lwm2m_client_resource_integer64_set: *Set the resource value as 64-Bit integer*</span></span>

- <span data-ttu-id="70980-152">nx_lwm2m_client_resource_float32_set: *리소스 값을 32비트 float로 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-152">nx_lwm2m_client_resource_float32_set: *Set the resource value as 32-Bit float*</span></span>

- <span data-ttu-id="70980-153">nx_lwm2m_client_resource_float64_set: *리소스 값을 64비트 float로 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-153">nx_lwm2m_client_resource_float64_set: *Set the resource value as 64-Bit float*</span></span>

- <span data-ttu-id="70980-154">nx_lwm2m_client_resource_boolean_set: *리소스 값을 부울로 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-154">nx_lwm2m_client_resource_boolean_set: *Set the resource value as boolean*</span></span>

- <span data-ttu-id="70980-155">nx_lwm2m_client_resource_objlnk_set: *리소스 값을 개체 링크로 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-155">nx_lwm2m_client_resource_objlnk_set: *Set the resource value as object link*</span></span>

- <span data-ttu-id="70980-156">nx_lwm2m_client_resource_opaque_set: *리소스 값을 불투명으로 설정합니다*</span><span class="sxs-lookup"><span data-stu-id="70980-156">nx_lwm2m_client_resource_opaque_set: *Set the resource value as opaque*</span></span>

- <span data-ttu-id="70980-157">nx_lwm2m_client_resource_instance_set: *리소스 값을 여러 리소스에 대한 인스턴스로 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-157">nx_lwm2m_client_resource_instance_set: *Set the resource value as instance for multiple resource*</span></span>
-
- <span data-ttu-id="70980-158">nx_lwm2m_client_resource_dim_set: *여러 리소스에 대한 리소스 차원 설정*</span><span class="sxs-lookup"><span data-stu-id="70980-158">nx_lwm2m_client_resource_dim_set: *Set the resource dimension for multiple resource.*</span></span>

<span data-ttu-id="70980-159">**리소스 정보 및 값 가져오기:**</span><span class="sxs-lookup"><span data-stu-id="70980-159">**Resources Info and Values Getting:**</span></span>

- <span data-ttu-id="70980-160">nx_lwm2m_client_resource_info_get: *리소스 정보 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-160">nx_lwm2m_client_resource_info_get: *Get the resource info*</span></span>

- <span data-ttu-id="70980-161">nx_lwm2m_client_resource_string_get: *문자열 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-161">nx_lwm2m_client_resource_string_get: *Get the value of a string resource*</span></span>

- <span data-ttu-id="70980-162">nx_lwm2m_client_resource_integer32_get: *32비트 정수 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-162">nx_lwm2m_client_resource_integer32_get: *Get the value of a 32-Bit integer resource*</span></span>

- <span data-ttu-id="70980-163">nx_lwm2m_client_resource_integer64_get: *64비트 정수 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-163">nx_lwm2m_client_resource_integer64_get: *Get the value of a 64-Bit integer resource*</span></span>

- <span data-ttu-id="70980-164">nx_lwm2m_client_resource_float32_get: *32비트 float 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-164">nx_lwm2m_client_resource_float32_get: *Get the value of a 32-Bit float resource*</span></span>

- <span data-ttu-id="70980-165">nx_lwm2m_client_resource_float64_get: *64비트 float 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-165">nx_lwm2m_client_resource_float64_get: *Get the value of a 64-Bit float resource*</span></span>

- <span data-ttu-id="70980-166">nx_lwm2m_client_resource_boolean_get: *부울 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-166">nx_lwm2m_client_resource_boolean_get: *Get the value of a boolean resource*</span></span>

- <span data-ttu-id="70980-167">nx_lwm2m_client_resource_objlnk_get: *개체 링크 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-167">nx_lwm2m_client_resource_objlnk_get: *Get the value of an object link resource*</span></span>

- <span data-ttu-id="70980-168">nx_lwm2m_client_resource_opaque_get: *불투명 리소스의 값 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-168">nx_lwm2m_client_resource_opaque_get: *Get the value of an opaque resource*</span></span>

- <span data-ttu-id="70980-169">nx_lwm2m_client_resource_instance_get: *여러 리소스에 대한 리소스 인스턴스 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-169">nx_lwm2m_client_resource_instance_get: *Get the resource instance for multiple resource*</span></span>

- <span data-ttu-id="70980-170">nx_lwm2m_client_resource_dim_get: *여러 리소스에 대한 리소스 차원 가져오기*</span><span class="sxs-lookup"><span data-stu-id="70980-170">nx_lwm2m_client_resource_dim_get: *Get the resource dimension for multiple resource.*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="70980-171">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="70980-171">nx_lwm2m_client_create</span></span>

<span data-ttu-id="70980-172">LWM2M 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="70980-172">Creates a LWM2M client.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-173">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-173">Prototype</span></span>

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="70980-174">Description</span><span class="sxs-lookup"><span data-stu-id="70980-174">Description</span></span>

<span data-ttu-id="70980-175">이 서비스는 자체 ThreadX 스레드의 컨텍스트에서 실행되는 LWM2M 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="70980-175">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="70980-176">LWM2M 클라이언트는 보안(0), 서버(1), 액세스 제어(2) 및 디바이스(3)와 같은 OMA LWM2M 개체를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-176">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="70980-177">다른 개체 구현은 애플리케이션에서 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-177">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-178">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-178">Parameters</span></span>

- <span data-ttu-id="70980-179">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-179">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-180">**ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-180">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="70980-181">**packet_pool_ptr** 이 LWM2M 클라이언트의 기본 패킷 풀에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-181">**packet_pool_ptr** Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="70980-182">**name_ptr** LWM2M 클라이언트 엔드포인트 이름에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-182">**name_ptr** Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="70980-183">**name_length** LWM2M 클라이언트 엔드포인트 이름의 길이.</span><span class="sxs-lookup"><span data-stu-id="70980-183">**name_length** Length of LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="70980-184">**msisdn_ptr** SMS 바인딩에서 사용하기 위해 LWM2M 클라이언트에 연결할 수 있는 MSISDN에 대한 포인터이며, SMS 바인딩이 지원되지 않는 경우 NULL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-184">**msisdn_ptr** Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="70980-185">**msisdn_length** MSISDN 번호의 길이.</span><span class="sxs-lookup"><span data-stu-id="70980-185">**msisdn_length** Length of MSISDN number.</span></span>
- <span data-ttu-id="70980-186">**binding_modes** LWM2M 클라이언트에서 지원하는 바인딩 및 모드이며, NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S 및 NX_LWM2M_BINDING_SQ 플래그의 조합이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-186">**binding_modes** The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="70980-187">**stack_ptr** LWM2M 클라이언트 스레드 스택 영역에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-187">**stack_ptr** Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="70980-188">**stack_size** LWM2M 클라이언트 스레드 스택 크기.</span><span class="sxs-lookup"><span data-stu-id="70980-188">**stack_size** The LWM2M Client thread stack size.</span></span>
- <span data-ttu-id="70980-189">**priority** LWM2M 클라이언트의 우선 순위.</span><span class="sxs-lookup"><span data-stu-id="70980-189">**priority** Priority of LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-190">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-190">Return Values</span></span>

- <span data-ttu-id="70980-191">**NX_SUCCESS** LWM2M 클라이언트를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-191">**NX_SUCCESS** The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="70980-192">**NX_LWM2M_CLIENT_ERROR** LWM2M 클라이언트 만들기 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="70980-192">**NX_LWM2M_CLIENT_ERROR** LWM2M Client create error.</span></span>
- <span data-ttu-id="70980-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** 포트를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="70980-194">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-194">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="70980-195">**NX_SIZE_ERROR** 잘못된 스택 크기.</span><span class="sxs-lookup"><span data-stu-id="70980-195">**NX_SIZE_ERROR** Invalid stack size.</span></span>
- <span data-ttu-id="70980-196">**NX_OPTION_ERROR** 잘못된 우선 순위.</span><span class="sxs-lookup"><span data-stu-id="70980-196">**NX_OPTION_ERROR** Invalid priority.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-197">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-197">Allowed From</span></span>

<span data-ttu-id="70980-198">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-198">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-199">예제</span><span class="sxs-lookup"><span data-stu-id="70980-199">Example</span></span>

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="70980-200">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="70980-200">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="70980-201">LWM2M 클라이언트를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-201">Deletes a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-202">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-202">Prototype</span></span>

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-203">Description</span><span class="sxs-lookup"><span data-stu-id="70980-203">Description</span></span>

<span data-ttu-id="70980-204">이 서비스는 이전에 만든 LWM2M 클라이언트 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-204">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="70980-205">현재 클라이언트에 연결된 모든 세션도 이 호출을 통해 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-205">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-206">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-206">Parameters</span></span>

- <span data-ttu-id="70980-207">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-207">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-208">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-208">Return Values</span></span>

- <span data-ttu-id="70980-209">**NX_SUCCESS** LWM2M 클라이언트를 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-209">**NX_SUCCESS** The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="70980-210">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-210">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-211">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-211">Allowed From</span></span>

<span data-ttu-id="70980-212">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-212">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-213">예제</span><span class="sxs-lookup"><span data-stu-id="70980-213">Example</span></span>

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a><span data-ttu-id="70980-214">nx_lwm2m_client_device_callback_set</span><span class="sxs-lookup"><span data-stu-id="70980-214">nx_lwm2m_client_device_callback_set</span></span>

<span data-ttu-id="70980-215">디바이스 개체의 애플리케이션 콜백을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-215">Sets a device object's application callback.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-216">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-216">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a><span data-ttu-id="70980-217">Description</span><span class="sxs-lookup"><span data-stu-id="70980-217">Description</span></span>

<span data-ttu-id="70980-218">이 서비스는 LWM2M 클라이언트에서 처리하지 않는 LWM2M 디바이스 개체 리소스에 대한 작업을 구현하는 애플리케이션 콜백을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-218">This service installs the application callback for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="70980-219">LWM2M 클라이언트는 오류 코드(11), 다시 설정 오류 코드(12) 및 지원되는 바인딩 및 모드(16)와 같은 리소스를 구현합니다. 다른 리소스에 대한 작업은 애플리케이션으로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-219">The LWM2M Client implements the following resources: Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-220">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-220">Parameters</span></span>

- <span data-ttu-id="70980-221">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-221">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-222">**operation_callback** "읽기", "검색", "쓰기" 및 "실행"에 대한 작업 콜백입니다.</span><span class="sxs-lookup"><span data-stu-id="70980-222">**operation_callback** The operation callback for “Read”, “Discover”, “Write” and “Execute”.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-223">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-223">Return Values</span></span>

- <span data-ttu-id="70980-224">**NX_SUCCESS** 작업 콜백이 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-224">**NX_SUCCESS** The operation callback has been successfully set.</span></span>
- <span data-ttu-id="70980-225">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-225">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-226">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-226">Allowed From</span></span>

<span data-ttu-id="70980-227">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-227">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-228">예제</span><span class="sxs-lookup"><span data-stu-id="70980-228">Example</span></span>

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="70980-229">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="70980-229">nx_lwm2m_client_device_error_push</span></span>
<span data-ttu-id="70980-230">디바이스 개체에 오류 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-230">Adds an error code to a device object.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-231">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-231">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a><span data-ttu-id="70980-232">Description</span><span class="sxs-lookup"><span data-stu-id="70980-232">Description</span></span>

<span data-ttu-id="70980-233">이 서비스는 새 인스턴스를 개체 디바이스의 오류 코드(11) 리소스에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-233">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-234">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-234">Parameters</span></span>

- <span data-ttu-id="70980-235">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-235">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-236">**code** 새 오류 코드.</span><span class="sxs-lookup"><span data-stu-id="70980-236">**code** The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-237">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-237">Return Values</span></span>

- <span data-ttu-id="70980-238">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-238">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span><span class="sxs-lookup"><span data-stu-id="70980-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span></span>

<span data-ttu-id="70980-240">저장된 오류 코드의 최대 개수에</span><span class="sxs-lookup"><span data-stu-id="70980-240">The maximum number of stored error codes has</span></span>

<span data-ttu-id="70980-241">도달했습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-241">been reached.</span></span>

<span data-ttu-id="70980-242">NX_PTR_ERROR 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-242">NX_PTR_ERROR Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-243">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-243">Allowed From</span></span>

<span data-ttu-id="70980-244">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-244">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-245">예제</span><span class="sxs-lookup"><span data-stu-id="70980-245">Example</span></span>

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="70980-246">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="70980-246">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="70980-247">디바이스 개체의 오류 코드를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-247">Resets the error codes of Device Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-248">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-248">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-249">Description</span><span class="sxs-lookup"><span data-stu-id="70980-249">Description</span></span>

<span data-ttu-id="70980-250">이 서비스는 디바이스 개체에서 모든 오류 코드 리소스 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-250">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="70980-251">이는 리소스 다시 설정 오류 코드(12)를 실행하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-251">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-252">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-252">Parameters</span></span>

- <span data-ttu-id="70980-253">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-253">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-254">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-254">Return Values</span></span>

- <span data-ttu-id="70980-255">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-255">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-256">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-256">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-257">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-257">Allowed From</span></span>

<span data-ttu-id="70980-258">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-258">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-259">예제</span><span class="sxs-lookup"><span data-stu-id="70980-259">Example</span></span>

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="70980-260">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="70980-260">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="70980-261">디바이스 개체 리소스를 변경하도록 신호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="70980-261">Signals a change to a Device Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-262">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-262">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a><span data-ttu-id="70980-263">Description</span><span class="sxs-lookup"><span data-stu-id="70980-263">Description</span></span>

<span data-ttu-id="70980-264">이 서비스는 애플리케이션에서 개체 디바이스의 리소스가 변경되었다는 신호를 LWM2M 클라이언트에 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-264">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="70980-265">LWM2M 서버에서 리소스를 관찰하는 경우 LWM2M 클라이언트에서 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="70980-265">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-266">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-266">Parameters</span></span>

- <span data-ttu-id="70980-267">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-267">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-268">**resource** 변경된 리소스를 설명하는 구조체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-268">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-269">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-269">Return Values</span></span>

- <span data-ttu-id="70980-270">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-270">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-271">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-271">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-272">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-272">Allowed From</span></span>

<span data-ttu-id="70980-273">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-273">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-274">예제</span><span class="sxs-lookup"><span data-stu-id="70980-274">Example</span></span>

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a><span data-ttu-id="70980-275">nx_lwm2m_client_firmware_create</span><span class="sxs-lookup"><span data-stu-id="70980-275">nx_lwm2m_client_firmware_create</span></span>

<span data-ttu-id="70980-276">LWM2M 클라이언트 펌웨어 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="70980-276">Create a LWM2M Client Firmware Object.</span></span> 

### <a name="prototype"></a><span data-ttu-id="70980-277">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-277">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="70980-278">Description</span><span class="sxs-lookup"><span data-stu-id="70980-278">Description</span></span>

<span data-ttu-id="70980-279">서비스는 애플리케이션에서 펌웨어 개체를 만드는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-279">The service is used by the application to create firmware object.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-280">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-280">Parameters</span></span>

- <span data-ttu-id="70980-281">**firmware_ptr** LWM2M 클라이언트 펌웨어 개체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-281">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="70980-282">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-282">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-283">**protocols** 지원되는 프로토콜.</span><span class="sxs-lookup"><span data-stu-id="70980-283">**protocols** The supported protocols.</span></span>
- <span data-ttu-id="70980-284">**package_callback** 패키지 콜백.</span><span class="sxs-lookup"><span data-stu-id="70980-284">**package_callback** The package callback.</span></span>
- <span data-ttu-id="70980-285">**package_uri_callback** 패키지 URI 콜백.</span><span class="sxs-lookup"><span data-stu-id="70980-285">**package_uri_callback** The package URI callback.</span></span>
- <span data-ttu-id="70980-286">**update_callback** 업데이트 콜백.</span><span class="sxs-lookup"><span data-stu-id="70980-286">**update_callback** The update callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-287">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-287">Return Values</span></span>

<span data-ttu-id="70980-288">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-288">**NX_SUCCESS** Successful operation.</span></span>
<span data-ttu-id="70980-289">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-289">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-290">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-290">Allowed From</span></span>

<span data-ttu-id="70980-291">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-291">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-292">예제</span><span class="sxs-lookup"><span data-stu-id="70980-292">Example</span></span>

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a><span data-ttu-id="70980-293">nx_lwm2m_client_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="70980-293">nx_lwm2m_client_firmware_package_info_set</span></span>

<span data-ttu-id="70980-294">LWM2M 클라이언트 펌웨어 패키지 정보를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-294">Sets the LWM2M Client Firmware package information.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-295">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-295">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a><span data-ttu-id="70980-296">Description</span><span class="sxs-lookup"><span data-stu-id="70980-296">Description</span></span>

<span data-ttu-id="70980-297">서비스는 애플리케이션에서 펌웨어 업데이트 개체의 패키지 정보 리소스를 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-297">The service is used by the application to set the package information resources of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-298">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-298">Parameters</span></span>

- <span data-ttu-id="70980-299">**firmware_ptr** LWM2M 클라이언트 펌웨어 개체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-299">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="70980-300">**name** 펌웨어 패키지의 이름.</span><span class="sxs-lookup"><span data-stu-id="70980-300">**name** The name of firmware package.</span></span>
- <span data-ttu-id="70980-301">**name_length** 이름 길이.</span><span class="sxs-lookup"><span data-stu-id="70980-301">**name_length** The length of name.</span></span>
- <span data-ttu-id="70980-302">**version** 펌웨어 패키지의 버전.</span><span class="sxs-lookup"><span data-stu-id="70980-302">**version** The version of firmware package.</span></span>
- <span data-ttu-id="70980-303">**version_length** 버전의 길이.</span><span class="sxs-lookup"><span data-stu-id="70980-303">**version_length** The length of version.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-304">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-304">Return Values</span></span>

- <span data-ttu-id="70980-305">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-305">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-306">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-306">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-307">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-307">Allowed From</span></span>

<span data-ttu-id="70980-308">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-308">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-309">예제</span><span class="sxs-lookup"><span data-stu-id="70980-309">Example</span></span>

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a><span data-ttu-id="70980-310">nx_lwm2m_client_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="70980-310">nx_lwm2m_client_firmware_result_set</span></span>

<span data-ttu-id="70980-311">펌웨어 업데이트 개체의 업데이트 결과 리소스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-311">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-312">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-312">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="70980-313">Description</span><span class="sxs-lookup"><span data-stu-id="70980-313">Description</span></span>

<span data-ttu-id="70980-314">서비스는 애플리케이션에서 펌웨어 업데이트 개체의 업데이트 결과 리소스를 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-314">The service is used by the application to set the update result resource of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-315">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-315">Parameters</span></span>

- <span data-ttu-id="70980-316">**firmware_ptr** LWM2M 클라이언트 펌웨어 개체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-316">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="70980-317">**result** 업데이트 결과.</span><span class="sxs-lookup"><span data-stu-id="70980-317">**result** The update result.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-318">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-318">Return Values</span></span>

- <span data-ttu-id="70980-319">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-319">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-320">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-320">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-321">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-321">Allowed From</span></span>

<span data-ttu-id="70980-322">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-322">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-323">예제</span><span class="sxs-lookup"><span data-stu-id="70980-323">Example</span></span>

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a><span data-ttu-id="70980-324">nx_lwm2m_client_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="70980-324">nx_lwm2m_client_firmware_state_set</span></span>

<span data-ttu-id="70980-325">펌웨어 업데이트 개체의 업데이트 결과 리소스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-325">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-326">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-326">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="70980-327">Description</span><span class="sxs-lookup"><span data-stu-id="70980-327">Description</span></span>

<span data-ttu-id="70980-328">서비스는 애플리케이션에서 펌웨어 업데이트 개체의 상태를 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-328">The service is used by the application to set the state of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-329">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-329">Parameters</span></span>

- <span data-ttu-id="70980-330">**firmware_ptr** LWM2M 클라이언트 펌웨어 개체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-330">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="70980-331">**state** 펌웨어 개체의 상태.</span><span class="sxs-lookup"><span data-stu-id="70980-331">**state** The state of the firmware object.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-332">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-332">Return Values</span></span>

- <span data-ttu-id="70980-333">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-333">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-334">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-334">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-335">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-335">Allowed From</span></span>

<span data-ttu-id="70980-336">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-336">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-337">예제</span><span class="sxs-lookup"><span data-stu-id="70980-337">Example</span></span>

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="70980-338">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="70980-338">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="70980-339">LWM2M 클라이언트를 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="70980-339">Locks the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-340">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-340">Prototype</span></span>

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-341">Description</span><span class="sxs-lookup"><span data-stu-id="70980-341">Description</span></span>

<span data-ttu-id="70980-342">이 서비스는 서버 또는 다른 애플리케이션 스레드에서 LWM2M 개체로의 동시 액세스를 방지하기 위해 LWM2M 클라이언트를 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="70980-342">This service locks the LWM2M Client to prevent concurrent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="70980-343">LWM2M 클라이언트가 현재 다른 스레드에서 잠겨 있는 경우 LWM2M 클라이언트의 잠금이 해제될 때까지 이 함수가 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-343">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="70980-344">***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** 쌍에 대한 호출은 중첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-344">Calls to \***nx_lwm2m_client_lock**_/_*_nx_lwm2m_client_unlock_*\* pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-345">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-345">Parameters</span></span>

- <span data-ttu-id="70980-346">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-346">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-347">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-347">Return Values</span></span>

- <span data-ttu-id="70980-348">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-348">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-349">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-349">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-350">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-350">Allowed From</span></span>

<span data-ttu-id="70980-351">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-351">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-352">예제</span><span class="sxs-lookup"><span data-stu-id="70980-352">Example</span></span>

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="70980-353">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="70980-353">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="70980-354">개체 구현을 LWM2M 클라이언트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-354">Adds an Object implementation to the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-355">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-355">Prototype</span></span>

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a><span data-ttu-id="70980-356">Description</span><span class="sxs-lookup"><span data-stu-id="70980-356">Description</span></span>

<span data-ttu-id="70980-357">이 서비스는 새 개체 구현을 LWM2M 클라이언트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-357">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-358">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-358">Parameters</span></span>

- <span data-ttu-id="70980-359">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-359">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-360">**object_ptr** 개체 구현을 정의하는 구조체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-360">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="70980-361">**object_id** 개체 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-361">**object_id** The object id.</span></span>
- <span data-ttu-id="70980-362">**object_operation** 개체 작업 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="70980-362">**object_operation** The object operation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-363">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-363">Return Values</span></span>

- <span data-ttu-id="70980-364">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-364">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-365">**NX_LWM2M_ALREADY_EXIST** 개체 ID가 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="70980-366">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-366">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-367">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-367">Allowed From</span></span>

<span data-ttu-id="70980-368">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-368">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-369">예제</span><span class="sxs-lookup"><span data-stu-id="70980-369">Example</span></span>

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="70980-370">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="70980-370">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="70980-371">새 개체 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="70980-371">Creates a new Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-372">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-372">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-373">Description</span><span class="sxs-lookup"><span data-stu-id="70980-373">Description</span></span>

<span data-ttu-id="70980-374">이 서비스는 LWM2M 클라이언트의 개체에 대한 '만들기(Create)' 작업을 수행하여 새 개체 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="70980-374">This service performs a ‘Create’ operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-375">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-375">Parameters</span></span>

- <span data-ttu-id="70980-376">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-376">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-377">**object_id** 개체 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-377">**object_id** The Object ID.</span></span>
- <span data-ttu-id="70980-378">**instance_id_ptr** 새 인스턴스의 ID에 대한 포인터이며 LWM2M 클라이언트에서 인스턴스 ID를 할당해야 하는 경우 **NULL** 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-378">**instance_id_ptr** Pointer to the ID of the new instance, can be **NULL** if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="70980-379">ID가 예약된 65535 값인 경우 LWM2M 클라이언트에서 인스턴스 ID를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-379">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="70980-380">NULL이 아닌 경우 할당된 ID가 호출 후에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-380">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="70980-381">**num_values** 설정하는 값의 수.</span><span class="sxs-lookup"><span data-stu-id="70980-381">**num_values** The number of values to set.</span></span>
- <span data-ttu-id="70980-382">**values_ptr** 새 개체 인스턴스를 초기화하는 리소스 값의 배열에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-382">**values_ptr** Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-383">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-383">Return Values</span></span>

- <span data-ttu-id="70980-384">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-384">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-385">**NX_LWM2M_ALREADY_EXIST** 개체 인스턴스 ID가 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object Instance ID already exists.</span></span>
- <span data-ttu-id="70980-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** 개체에서 인스턴스 만들기를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance creation.</span></span>
- <span data-ttu-id="70980-387">**NX_LWM2M_CLIENT_NO_MEMORY** 새 인스턴스를 저장하는 메모리를 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-387">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="70980-388">**NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-388">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID doesn’t exist.</span></span>
- <span data-ttu-id="70980-389">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-389">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-390">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-390">Allowed From</span></span>

<span data-ttu-id="70980-391">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-391">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-392">예제</span><span class="sxs-lookup"><span data-stu-id="70980-392">Example</span></span>

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="70980-393">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="70980-393">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="70980-394">개체 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-394">Deletes an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-395">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-395">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="70980-396">Description</span><span class="sxs-lookup"><span data-stu-id="70980-396">Description</span></span>

<span data-ttu-id="70980-397">이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Delete(삭제)' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-397">This service performs a ‘Delete’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-398">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-398">Parameters</span></span>

- <span data-ttu-id="70980-399">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-399">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-400">**object_id** 개체 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-400">**object_id** The Object ID.</span></span>
- <span data-ttu-id="70980-401">**instance_id** 개체 인스턴스 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-401">**instance_id** The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-402">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-402">Return Values</span></span>

- <span data-ttu-id="70980-403">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-403">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** 개체에서 인스턴스 삭제를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance deletion.</span></span>
- <span data-ttu-id="70980-405">**NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID 또는 개체 인스턴스 ID가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-405">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="70980-406">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-406">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-407">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-407">Allowed From</span></span>

<span data-ttu-id="70980-408">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-408">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-409">예제</span><span class="sxs-lookup"><span data-stu-id="70980-409">Example</span></span>

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="70980-410">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="70980-410">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="70980-411">개체 인스턴스의 리소스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-411">Discovers resources of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-412">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-412">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a><span data-ttu-id="70980-413">Description</span><span class="sxs-lookup"><span data-stu-id="70980-413">Description</span></span>

<span data-ttu-id="70980-414">이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Discover(검색)' 작업을 수행하여 개체에서 구현한 리소스 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-414">This service performs a ‘Discover’ operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-415">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-415">Parameters</span></span>

- <span data-ttu-id="70980-416">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-416">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-417">**object_id** 개체 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-417">**object_id** The Object ID.</span></span>
- <span data-ttu-id="70980-418">**instance_id** 개체 인스턴스 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-418">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="70980-419">**num_resources** 입력 시 대상 버퍼의 크기 및 출력 시 버퍼에 쓰인 요소의 수.</span><span class="sxs-lookup"><span data-stu-id="70980-419">**num_resources** On input the size of the destination buffer, on output the number of elements written to the buffer.</span></span>
- <span data-ttu-id="70980-420">**resources** 대상 버퍼에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-420">**resources** Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-421">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-421">Return Values</span></span>

- <span data-ttu-id="70980-422">*NX_SUCCESS*\* 작업이 성공함.</span><span class="sxs-lookup"><span data-stu-id="70980-422">*NX_SUCCESS*\* Successful operation.</span></span>
- <span data-ttu-id="70980-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** 리소스 버퍼가 너무 작아 리소스 목록을 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="70980-424">**NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID 또는 개체 인스턴스 ID가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-424">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="70980-425">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-425">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-426">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-426">Allowed From</span></span>

<span data-ttu-id="70980-427">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-427">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-428">예제</span><span class="sxs-lookup"><span data-stu-id="70980-428">Example</span></span>

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="70980-429">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="70980-429">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="70980-430">개체 인스턴스의 리소스에 대해 'Execute(실행)' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-430">Performs an 'Execute' operation on a resource of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-431">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-431">Prototype</span></span>

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="70980-432">Description</span><span class="sxs-lookup"><span data-stu-id="70980-432">Description</span></span>

<span data-ttu-id="70980-433">이 서비스는 LWM2M 클라이언트의 개체 인스턴스 리소스에 대한 'Execute(실행)' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-433">This service performs the ‘Execute’ operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-434">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-434">Parameters</span></span>

- <span data-ttu-id="70980-435">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-435">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-436">**object_id** 개체 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-436">**object_id** The Object ID.</span></span>
- <span data-ttu-id="70980-437">**instance_id** 개체 인스턴스 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-437">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="70980-438">**resource_id** 리소스 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-438">**resource_id** The Resource ID.</span></span>
- <span data-ttu-id="70980-439">**arguments_ptr** 실행 작업의 인수에 대한 포인터이며,</span><span class="sxs-lookup"><span data-stu-id="70980-439">**arguments_ptr** Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="70980-440">arguments_length가 0인 경우 NULL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-440">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="70980-441">**arguments_length** 인수의 길이.</span><span class="sxs-lookup"><span data-stu-id="70980-441">**arguments_length** The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-442">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-442">Return Values</span></span>

- <span data-ttu-id="70980-443">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-443">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** 리소스 버퍼가 너무 작아 리소스 목록을 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="70980-445">**NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID 또는 개체 인스턴스 ID가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-445">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="70980-446">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-446">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-447">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-447">Allowed From</span></span>

<span data-ttu-id="70980-448">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-448">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-449">예제</span><span class="sxs-lookup"><span data-stu-id="70980-449">Example</span></span>

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a><span data-ttu-id="70980-450">nx_lwm2m_client_object_instance_add</span><span class="sxs-lookup"><span data-stu-id="70980-450">nx_lwm2m_client_object_instance_add</span></span>

<span data-ttu-id="70980-451">개체에 개체 인스턴스 구현을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-451">Adds an Object instance implementation to an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-452">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-452">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-453">Description</span><span class="sxs-lookup"><span data-stu-id="70980-453">Description</span></span>

<span data-ttu-id="70980-454">이 서비스는 새 개체 인스턴스 구현을 LWM2M 클라이언트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-454">This service adds a new Object instance implementation to the LWM2M Client.</span></span> <span data-ttu-id="70980-455">Instance_id_ptr 값이 **NX_LWM2M_CLIENT_RESERVED_ID** 이면 LWM2M 클라이언트는 사용되지 않는 인스턴스 ID를 자동으로 할당하고, 그렇지 않으면 LWM2M 클라이언트에서 값 애플리케이션 집합을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-455">If the value of instance_id_ptr is **NX_LWM2M_CLIENT_RESERVED_ID**, LWM2M Client will automatically assign an unused instance id, otherwise, LWM2M Client will use the value application set.</span></span> <span data-ttu-id="70980-456">새 인스턴스가 추가되면 애플리케이션으로 돌아가기 위해 instance_id가 instance_id_ptr에서 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="70980-456">Once new instance was added successfully, the instance_id will be filled in instance_id_ptr to return to application.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-457">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-457">Parameters</span></span>

- <span data-ttu-id="70980-458">**object_ptr** 개체 구현을 정의하는 구조체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-458">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="70980-459">**instance_ptr** 개체 인스턴스 구현을 정의하는 구조체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-459">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="70980-460">**instance_id_ptr** 개체 인스턴스 ID에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-460">**instance_id_ptr** Pointer to the object instance id.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-461">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-461">Return Values</span></span>

- <span data-ttu-id="70980-462">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-462">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** 개체 ID가 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="70980-464">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-464">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-465">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-465">Allowed From</span></span>

<span data-ttu-id="70980-466">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-466">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-467">예제</span><span class="sxs-lookup"><span data-stu-id="70980-467">Example</span></span>

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a><span data-ttu-id="70980-468">nx_lwm2m_client_object_instance_next_get</span><span class="sxs-lookup"><span data-stu-id="70980-468">nx_lwm2m_client_object_instance_next_get</span></span>

<span data-ttu-id="70980-469">개체의 다음 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-469">Gets the next instance of an Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-470">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-470">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-471">Description</span><span class="sxs-lookup"><span data-stu-id="70980-471">Description</span></span>

<span data-ttu-id="70980-472">이 서비스는 지정된 개체의 다음 개체 인스턴스에 대한 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-472">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="70980-473">현재 인스턴스 ID가 NX_LWM2M_RESERVED_ID (65535)로 설정된 경우 첫 번째 인스턴스의 ID가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-473">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-474">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-474">Parameters</span></span>

- <span data-ttu-id="70980-475">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-475">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-476">**object_id** 개체 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-476">**object_id** The Object ID.</span></span>
- <span data-ttu-id="70980-477">**instance_id_ptr** 현재 개체 인스턴스 ID에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-477">**instance_id_ptr** Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="70980-478">반환 시 개체의 다음 인스턴스 ID가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-478">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-479">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-479">Return Values</span></span>

- <span data-ttu-id="70980-480">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-480">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-481">**NX_CLIENT_LWM2M_NOT_FOUND** 지정된 인스턴스 ID가 개체의 마지막 ID이거나 개체 ID가 구현되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-481">**NX_CLIENT_LWM2M_NOT_FOUND** The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="70980-482">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-482">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-483">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-483">Allowed From</span></span>

<span data-ttu-id="70980-484">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-484">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-485">예제</span><span class="sxs-lookup"><span data-stu-id="70980-485">Example</span></span>

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a><span data-ttu-id="70980-486">nx_lwm2m_client_object_instance_remove</span><span class="sxs-lookup"><span data-stu-id="70980-486">nx_lwm2m_client_object_instance_remove</span></span>

<span data-ttu-id="70980-487">개체에서 개체 인스턴스 구현을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-487">Removes an  Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-488">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-489">Description</span><span class="sxs-lookup"><span data-stu-id="70980-489">Description</span></span>

<span data-ttu-id="70980-490">이 서비스는 개체에서 개체 인스턴스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-490">This service removes an Object instance from an object.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-491">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-491">Parameters</span></span>

- <span data-ttu-id="70980-492">***object_ptr*** 개체 구현을 정의하는 구조체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-492">***object_ptr*** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="70980-493">**instance_ptr** 개체 인스턴스 구현을 정의하는 구조체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-493">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-494">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-494">Return Values</span></span>

- <span data-ttu-id="70980-495">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-495">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-496">**NX_LWM2M_ALREADY_EXIST** 개체 ID가 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="70980-497">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-497">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-498">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-498">Allowed From</span></span>

<span data-ttu-id="70980-499">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-499">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-500">예제</span><span class="sxs-lookup"><span data-stu-id="70980-500">Example</span></span>

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a><span data-ttu-id="70980-501">nx_lwm2m_client_object_next_get</span><span class="sxs-lookup"><span data-stu-id="70980-501">nx_lwm2m_client_object_next_get</span></span>

<span data-ttu-id="70980-502">LWM2M 클라이언트의 다음 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-502">Gets the next object of the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-503">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-503">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-504">Description</span><span class="sxs-lookup"><span data-stu-id="70980-504">Description</span></span>

<span data-ttu-id="70980-505">이 서비스는 LWM2M 클라이언트에서 구현하는 다음 개체의 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-505">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="70980-506">현재 개체 ID가 NX_LWM2M_RESERVED_ID (65535)로 설정된 경우 첫 번째 개체 ID가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-506">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-507">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-507">Parameters</span></span>

- <span data-ttu-id="70980-508">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-508">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-509">**object_id_ptr**: 현재 개체 ID에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-509">**object_id_ptr** Pointer to the current Object ID.</span></span> <span data-ttu-id="70980-510">반환 시 LWM2M 클라이언트에서 구현하는 다음 개체 ID가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-510">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-511">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-511">Return Values</span></span>

- <span data-ttu-id="70980-512">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-512">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-513">**NX_LWM2M_CLIENT_NOT_FOUND** 지정된 개체 ID가 데이터베이스의 마지막 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="70980-513">**NX_LWM2M_CLIENT_NOT_FOUND** The given Object ID is the last of the database.</span></span>
<span data-ttu-id="70980-514">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-514">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-515">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-515">Allowed From</span></span>

<span data-ttu-id="70980-516">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-516">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-517">예제</span><span class="sxs-lookup"><span data-stu-id="70980-517">Example</span></span>

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="70980-518">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="70980-518">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="70980-519">개체 인스턴스의 리소스 값을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-519">Reads an Object Instance's resource's values.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-520">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-520">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="70980-521">Description</span><span class="sxs-lookup"><span data-stu-id="70980-521">Description</span></span>

<span data-ttu-id="70980-522">이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Read(읽기)' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-522">This service performs a ‘Read’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-523">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-523">Parameters</span></span>

- <span data-ttu-id="70980-524">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-524">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-525">**object_id** 개체 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-525">**object_id** The Object ID.</span></span>
- <span data-ttu-id="70980-526">**instance_id** 개체 인스턴스 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-526">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="70980-527">**num_values** 읽는 리소스의 수.</span><span class="sxs-lookup"><span data-stu-id="70980-527">**num_values** The number of resources to read.</span></span>
- <span data-ttu-id="70980-528">**values_ptr** 읽는 리소스의 ID가 포함되는 NX_LWM2M_RESOURCE 배열에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-528">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="70980-529">반환 시 배열이 해당 형식 및 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="70980-529">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-530">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-530">Return Values</span></span>

- <span data-ttu-id="70980-531">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-531">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** 리소스에서 읽기 작업을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the read operation.</span></span>
- <span data-ttu-id="70980-533">**NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID, 개체 인스턴스 ID 또는 리소스 ID가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-533">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="70980-534">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-534">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-535">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-535">Allowed From</span></span>

<span data-ttu-id="70980-536">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-536">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-537">예제</span><span class="sxs-lookup"><span data-stu-id="70980-537">Example</span></span>

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a><span data-ttu-id="70980-538">nx_lwm2m_client_object_remove</span><span class="sxs-lookup"><span data-stu-id="70980-538">nx_lwm2m_client_object_remove</span></span>

<span data-ttu-id="70980-539">개체에서 개체 인스턴스 구현을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-539">Removes an Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-540">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-540">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-541">Description</span><span class="sxs-lookup"><span data-stu-id="70980-541">Description</span></span>

<span data-ttu-id="70980-542">이 서비스는 LWM2M 클라이언트에서 개체를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-542">This service removes an Object from the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-543">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-543">Parameters</span></span>

- <span data-ttu-id="70980-544">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-544">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-545">**object_ptr** 개체 구현을 정의하는 구조체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-545">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-546">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-546">Return Values</span></span>

- <span data-ttu-id="70980-547">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-547">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-548">**NX_LWM2M_ALREADY_EXIST** 개체 ID가 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="70980-549">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-549">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="70980-550">**NX_LWM2M_CLIENT_FORBIDDEN** 내부 개체를 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-550">**NX_LWM2M_CLIENT_FORBIDDEN** Removing internal object is forbidden.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-551">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-551">Allowed From</span></span>

<span data-ttu-id="70980-552">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-552">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-553">예제</span><span class="sxs-lookup"><span data-stu-id="70980-553">Example</span></span>

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a><span data-ttu-id="70980-554">nx_lwm2m_client_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="70980-554">nx_lwm2m_client_object_resource_changed</span></span>

<span data-ttu-id="70980-555">개체 리소스의 변경을 신호로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="70980-555">Signals a change of an Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-556">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="70980-557">Description</span><span class="sxs-lookup"><span data-stu-id="70980-557">Description</span></span>

<span data-ttu-id="70980-558">이 서비스는 애플리케이션에서 개체 디바이스의 리소스가 변경되었다는 신호를 LWM2M 클라이언트에 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-558">The service is used by the application to signal to the LWM2M Client that a resource of the Object has changed.</span></span> <span data-ttu-id="70980-559">LWM2M 서버에서 리소스를 관찰하는 경우 LWM2M 클라이언트에서 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="70980-559">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-560">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-560">Parameters</span></span>

- <span data-ttu-id="70980-561">**object_ptr** 개체 구현을 정의하는 구조체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-561">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="70980-562">***instance_ptr*** 개체 인스턴스 구현을 정의하는 구조체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-562">***instance_ptr*** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="70980-563">**resource** 변경된 리소스를 설명하는 구조체에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-563">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-564">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-564">Return Values</span></span>

- <span data-ttu-id="70980-565">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-565">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-566">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-566">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-567">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-567">Allowed From</span></span>

<span data-ttu-id="70980-568">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-568">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-569">예제</span><span class="sxs-lookup"><span data-stu-id="70980-569">Example</span></span>

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="70980-570">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="70980-570">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="70980-571">개체 인스턴스의 리소스 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-571">Changes resource's values of an Object instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-572">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-572">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a><span data-ttu-id="70980-573">Description</span><span class="sxs-lookup"><span data-stu-id="70980-573">Description</span></span>

<span data-ttu-id="70980-574">이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Write(쓰기)' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-574">This service performs a ‘Write’ operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="70980-575">*write_op* 매개 변수에 지정할 수 있는 쓰기 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-575">The following write operations can be specified to the *write_op* parameter.</span></span>

| <span data-ttu-id="70980-576">값</span><span class="sxs-lookup"><span data-stu-id="70980-576">Value</span></span> | <span data-ttu-id="70980-577">쓰기 &nbsp; 작업</span><span class="sxs-lookup"><span data-stu-id="70980-577">Write&nbsp;Operation</span></span> | <span data-ttu-id="70980-578">Description</span><span class="sxs-lookup"><span data-stu-id="70980-578">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="70980-579">0</span><span class="sxs-lookup"><span data-stu-id="70980-579">0</span></span> | <span data-ttu-id="70980-580">부분 업데이트</span><span class="sxs-lookup"><span data-stu-id="70980-580">Partial Update</span></span> | <span data-ttu-id="70980-581">새 값으로 제공되는 리소스를 추가하거나 업데이트하고, 다른 기존 리소스는 변경하지 않은 상태로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-581">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span> |
| <span data-ttu-id="70980-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="70980-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="70980-583">인스턴스 바꾸기</span><span class="sxs-lookup"><span data-stu-id="70980-583">Replace Instance</span></span> | <span data-ttu-id="70980-584">개체 인스턴스를 제공된 새 리소스 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="70980-584">Replaces the Object Instance with the new provided resource values.</span></span> |
| <span data-ttu-id="70980-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="70980-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> | <span data-ttu-id="70980-586">리소스 바꾸기</span><span class="sxs-lookup"><span data-stu-id="70980-586">Replace Resource</span></span> | <span data-ttu-id="70980-587">리소스를 제공된 새 리소스 값(여러 리소스를 바꾸는 데 사용됨)으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="70980-587">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="70980-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="70980-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="70980-589">부트스트랩 쓰기</span><span class="sxs-lookup"><span data-stu-id="70980-589">Bootstrap Write</span></span> | <span data-ttu-id="70980-590">부트스트랩 시퀀스의 호출을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="70980-590">Indicates a call from a Bootstrap sequence.</span></span> |

### <a name="parameters"></a><span data-ttu-id="70980-591">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-591">Parameters</span></span>

- <span data-ttu-id="70980-592">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-592">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="70980-593">**object_id** 개체 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-593">**object_id** The Object ID.</span></span>
- <span data-ttu-id="70980-594">**instance_id** 개체 인스턴스 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-594">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="70980-595">**num_values** 쓰는 리소스의 수.</span><span class="sxs-lookup"><span data-stu-id="70980-595">**num_values** The number of resources to write.</span></span>
- <span data-ttu-id="70980-596">**values_ptr** 리소스 ID, 형식 및 쓰는 값이 포함되는 NX_LWM2M_RESOURCE 배열에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-596">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="70980-597">**write_op** 쓰기 작업의 형식.</span><span class="sxs-lookup"><span data-stu-id="70980-597">**write_op** The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-598">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-598">Return Values</span></span>

- <span data-ttu-id="70980-599">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-599">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-600">**NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 종류가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-600">**NX_LWM2M_CLIENT_BAD_ENCODING** The type of a resource is not valid.</span></span>
- <span data-ttu-id="70980-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** 값의 길이가 너무 커서 인스턴스에 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="70980-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** 리소스에서 쓰기 작업을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the write operation.</span></span>
- <span data-ttu-id="70980-603">**NX_LWM2M_CLIENT_NO_MEMORY** 리소스 값을 저장하는 메모리를 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-603">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="70980-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** 리소스의 값이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** The value of a resource is not valid.</span></span>
- <span data-ttu-id="70980-605">**NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID, 개체 인스턴스 ID 또는 리소스 ID가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-605">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="70980-606">**NX_OPTION_ERROR** 잘못된 쓰기 작업의 형식.</span><span class="sxs-lookup"><span data-stu-id="70980-606">**NX_OPTION_ERROR** Invalid type of write operation.</span></span> 
- <span data-ttu-id="70980-607">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-607">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-608">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-608">Allowed From</span></span>

<span data-ttu-id="70980-609">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-609">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-610">예제</span><span class="sxs-lookup"><span data-stu-id="70980-610">Example</span></span>

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a><span data-ttu-id="70980-611">nx_lwm2m_client_resource_boolean_get</span><span class="sxs-lookup"><span data-stu-id="70980-611">nx_lwm2m_client_resource_boolean_get</span></span>

<span data-ttu-id="70980-612">부울 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-612">Gets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-613">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-613">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-614">Description</span><span class="sxs-lookup"><span data-stu-id="70980-614">Description</span></span>

<span data-ttu-id="70980-615">이 서비스는 부울 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-615">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-616">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-616">Parameters</span></span>

- <span data-ttu-id="70980-617">**resource** 리소스 값 설명에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-617">**resource** Pointer to Resource value description.</span></span>
- <span data-ttu-id="70980-618">**bool_ptr**: 대상 부울 값에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-618">**bool_ptr** Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-619">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-619">Return Values</span></span>

- <span data-ttu-id="70980-620">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-620">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-621">**NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 부울 값이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="70980-621">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="70980-622">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-622">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-623">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-623">Allowed From</span></span>

<span data-ttu-id="70980-624">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-624">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-625">예제</span><span class="sxs-lookup"><span data-stu-id="70980-625">Example</span></span>

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a><span data-ttu-id="70980-626">nx_lwm2m_client_resource_boolean_set</span><span class="sxs-lookup"><span data-stu-id="70980-626">nx_lwm2m_client_resource_boolean_set</span></span>

<span data-ttu-id="70980-627">부울 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-627">Sets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-628">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-628">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a><span data-ttu-id="70980-629">Description</span><span class="sxs-lookup"><span data-stu-id="70980-629">Description</span></span>

<span data-ttu-id="70980-630">이 서비스는 부울 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-630">The service sets the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-631">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-631">Parameters</span></span>

- <span data-ttu-id="70980-632">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-632">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-633">**bool_data** 부울 데이터.</span><span class="sxs-lookup"><span data-stu-id="70980-633">**bool_data** Boolean data.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-634">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-634">Return Values</span></span>

- <span data-ttu-id="70980-635">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-635">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-636">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-636">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-637">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-637">Allowed From</span></span>

<span data-ttu-id="70980-638">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-638">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-639">예제</span><span class="sxs-lookup"><span data-stu-id="70980-639">Example</span></span>

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a><span data-ttu-id="70980-640">nx_lwm2m_client_resource_dim_get</span><span class="sxs-lookup"><span data-stu-id="70980-640">nx_lwm2m_client_resource_dim_get</span></span>

<span data-ttu-id="70980-641">여러 리소스에 대한 리소스 차원을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-641">Gets the resource dimension for multiple Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-642">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-642">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a><span data-ttu-id="70980-643">Description</span><span class="sxs-lookup"><span data-stu-id="70980-643">Description</span></span>

<span data-ttu-id="70980-644">서비스는 여러 리소스에 대한 리소스 차원을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-644">The service retrieves the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-645">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-645">Parameters</span></span>

- <span data-ttu-id="70980-646">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-646">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-647">**dim** 대상 차원에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-647">**dim** Pointer to the destination dimension.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-648">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-648">Return Values</span></span>

- <span data-ttu-id="70980-649">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-649">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-650">**NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 부울 값이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="70980-650">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="70980-651">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-651">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-652">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-652">Allowed From</span></span>

<span data-ttu-id="70980-653">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-654">예제</span><span class="sxs-lookup"><span data-stu-id="70980-654">Example</span></span>

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a><span data-ttu-id="70980-655">nx_lwm2m_client_resource_dim_set</span><span class="sxs-lookup"><span data-stu-id="70980-655">nx_lwm2m_client_resource_dim_set</span></span>

<span data-ttu-id="70980-656">여러 리소스에 대한 리소스 차원을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-656">Sets the resource dimension for multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-657">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-657">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a><span data-ttu-id="70980-658">Description</span><span class="sxs-lookup"><span data-stu-id="70980-658">Description</span></span>

<span data-ttu-id="70980-659">서비스는 여러 리소스에 대한 리소스 차원을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-659">The service sets the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-660">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-660">Parameters</span></span>

- <span data-ttu-id="70980-661">**value** 리소스 값 설명에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-661">**value** Pointer to Resource value description.</span></span>
- <span data-ttu-id="70980-662">**dim** 차원 값.</span><span class="sxs-lookup"><span data-stu-id="70980-662">**dim** Dimension value.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-663">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-663">Return Values</span></span>

- <span data-ttu-id="70980-664">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-664">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-665">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-665">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-666">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-666">Allowed From</span></span>

<span data-ttu-id="70980-667">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-667">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-668">예제</span><span class="sxs-lookup"><span data-stu-id="70980-668">Example</span></span>

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a><span data-ttu-id="70980-669">nx_lwm2m_client_resource_float32_get</span><span class="sxs-lookup"><span data-stu-id="70980-669">nx_lwm2m_client_resource_float32_get</span></span>

<span data-ttu-id="70980-670">32비트 **float** 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-670">Gets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-671">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-671">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-672">Description</span><span class="sxs-lookup"><span data-stu-id="70980-672">Description</span></span>

<span data-ttu-id="70980-673">이 서비스는 32비트 **float** 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-673">The service retrieves the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-674">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-674">Parameters</span></span>

- <span data-ttu-id="70980-675">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-675">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-676">**float32_ptr** 대상 32비트 **float** 값에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-676">**float32_ptr** Pointer to the destination 32-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-677">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-677">Return Values</span></span>

- <span data-ttu-id="70980-678">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-678">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-679">**NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 부울 값이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="70980-679">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="70980-680">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-680">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-681">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-681">Allowed From</span></span>

<span data-ttu-id="70980-682">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-682">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-683">예제</span><span class="sxs-lookup"><span data-stu-id="70980-683">Example</span></span>

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a><span data-ttu-id="70980-684">nx_lwm2m_client_resource_float32_set</span><span class="sxs-lookup"><span data-stu-id="70980-684">nx_lwm2m_client_resource_float32_set</span></span>

<span data-ttu-id="70980-685">32비트 **float** 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-685">Sets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-686">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-686">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a><span data-ttu-id="70980-687">Description</span><span class="sxs-lookup"><span data-stu-id="70980-687">Description</span></span>

<span data-ttu-id="70980-688">서비스는 32비트 **float** 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-688">The service sets the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-689">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-689">Parameters</span></span>

- <span data-ttu-id="70980-690">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-690">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-691">**float32_data** 32비트 **float** 데이터.</span><span class="sxs-lookup"><span data-stu-id="70980-691">**float32_data** 32-Bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-692">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-692">Return Values</span></span>

- <span data-ttu-id="70980-693">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-693">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-694">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-694">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-695">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-695">Allowed From</span></span>

<span data-ttu-id="70980-696">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-696">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-697">예제</span><span class="sxs-lookup"><span data-stu-id="70980-697">Example</span></span>

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a><span data-ttu-id="70980-698">nx_lwm2m_client_resource_float64_get</span><span class="sxs-lookup"><span data-stu-id="70980-698">nx_lwm2m_client_resource_float64_get</span></span>

<span data-ttu-id="70980-699">64비트 float 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-699">Gets the value of a 64-Bit float Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-700">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-700">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-701">Description</span><span class="sxs-lookup"><span data-stu-id="70980-701">Description</span></span>

<span data-ttu-id="70980-702">이 서비스는 64비트 **float** 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-702">The service retrieves the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-703">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-703">Parameters</span></span>

- <span data-ttu-id="70980-704">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-704">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-705">**float64_ptr** 대상 64비트 **float** 값에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-705">**float64_ptr** Pointer to the destination 64-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-706">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-706">Return Values</span></span>

- <span data-ttu-id="70980-707">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-707">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-708">**NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 float 값이 아님</span><span class="sxs-lookup"><span data-stu-id="70980-708">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a float value.</span></span>
- <span data-ttu-id="70980-709">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-709">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-710">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-710">Allowed From</span></span>

<span data-ttu-id="70980-711">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-711">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-712">예제</span><span class="sxs-lookup"><span data-stu-id="70980-712">Example</span></span>

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a><span data-ttu-id="70980-713">nx_lwm2m_client_resource_float64_set</span><span class="sxs-lookup"><span data-stu-id="70980-713">nx_lwm2m_client_resource_float64_set</span></span>

<span data-ttu-id="70980-714">64비트 **float** 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-714">Sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-715">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-715">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="70980-716">Description</span><span class="sxs-lookup"><span data-stu-id="70980-716">Description</span></span>

<span data-ttu-id="70980-717">서비스는 64비트 **float** 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-717">The service sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-718">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-718">Parameters</span></span>

- <span data-ttu-id="70980-719">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-719">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-720">**float64_data** 64비트 **float** 데이터.</span><span class="sxs-lookup"><span data-stu-id="70980-720">**float64_data** 64-bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-721">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-721">Return Values</span></span>

- <span data-ttu-id="70980-722">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-722">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-723">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-723">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-724">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-724">Allowed From</span></span>

<span data-ttu-id="70980-725">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-725">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-726">예제</span><span class="sxs-lookup"><span data-stu-id="70980-726">Example</span></span>

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a><span data-ttu-id="70980-727">nx_lwm2m_client_resource_info_get</span><span class="sxs-lookup"><span data-stu-id="70980-727">nx_lwm2m_client_resource_info_get</span></span>

<span data-ttu-id="70980-728">리소스 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-728">Gets the resource info.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-729">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-729">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a><span data-ttu-id="70980-730">Description</span><span class="sxs-lookup"><span data-stu-id="70980-730">Description</span></span>

<span data-ttu-id="70980-731">서비스는 리소스의 리소스 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-731">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-732">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-732">Parameters</span></span>

- <span data-ttu-id="70980-733">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-733">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-734">**resource_id** 대상 리소스 ID에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="70980-734">**resource_id** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="70980-735">**operation** 대상 리소스 작업에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="70980-735">**operation** Pointer to the destination resource operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-736">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-736">Return Values</span></span>

- <span data-ttu-id="70980-737">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-737">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-738">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-738">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-739">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-739">Allowed From</span></span>

<span data-ttu-id="70980-740">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-740">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-741">예제</span><span class="sxs-lookup"><span data-stu-id="70980-741">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a><span data-ttu-id="70980-742">nx_lwm2m_client_resource_info_set</span><span class="sxs-lookup"><span data-stu-id="70980-742">nx_lwm2m_client_resource_info_set</span></span>

<span data-ttu-id="70980-743">리소스 정보를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-743">Sets the resource information.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-744">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-744">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="70980-745">Description</span><span class="sxs-lookup"><span data-stu-id="70980-745">Description</span></span>

<span data-ttu-id="70980-746">서비스는 리소스 정보를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-746">The service sets the resource information.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-747">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-747">Parameters</span></span>

- <span data-ttu-id="70980-748">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-748">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-749">**resource_id** 리소스의 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-749">**resource_id** ID of the resource.</span></span>
- <span data-ttu-id="70980-750">**operation** 리소스의 작업.</span><span class="sxs-lookup"><span data-stu-id="70980-750">**operation** Operation of the resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-751">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-751">Return Values</span></span>

- <span data-ttu-id="70980-752">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-752">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-753">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-753">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-754">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-754">Allowed From</span></span>

<span data-ttu-id="70980-755">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-755">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-756">예제</span><span class="sxs-lookup"><span data-stu-id="70980-756">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a><span data-ttu-id="70980-757">nx_lwm2m_client_resource_instances_get</span><span class="sxs-lookup"><span data-stu-id="70980-757">nx_lwm2m_client_resource_instances_get</span></span>

<span data-ttu-id="70980-758">여러 리소스의 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-758">Gets the instance of multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-759">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-759">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a><span data-ttu-id="70980-760">Description</span><span class="sxs-lookup"><span data-stu-id="70980-760">Description</span></span>

<span data-ttu-id="70980-761">서비스는 리소스의 리소스 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-761">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-762">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-762">Parameters</span></span>

- <span data-ttu-id="70980-763">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-763">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-764">**resource_instances** 대상 리소스 ID에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-764">**resource_instances** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="70980-765">**count** 개수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="70980-765">**count** Pointer to the count.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-766">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-766">Return Values</span></span>

- <span data-ttu-id="70980-767">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-767">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-768">**NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 부울 값이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="70980-768">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="70980-769">**NX_LWM2M_CLIENT_NO_MEMORY** 인스턴스를 채울 메모리가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-769">**NX_LWM2M_CLIENT_NO_MEMORY** No memory to fill out instances.</span></span>
- <span data-ttu-id="70980-770">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-770">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-771">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-771">Allowed From</span></span>

<span data-ttu-id="70980-772">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-772">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-773">예제</span><span class="sxs-lookup"><span data-stu-id="70980-773">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a><span data-ttu-id="70980-774">nx_lwm2m_client_resource_instances_set</span><span class="sxs-lookup"><span data-stu-id="70980-774">nx_lwm2m_client_resource_instances_set</span></span>

<span data-ttu-id="70980-775">리소스 인스턴스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-775">Sets the resource instances.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-776">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-776">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a><span data-ttu-id="70980-777">Description</span><span class="sxs-lookup"><span data-stu-id="70980-777">Description</span></span>

<span data-ttu-id="70980-778">서비스는 여러 리소스에 대한 리소스 인스턴스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-778">The service sets the resource instances for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-779">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-779">Parameters</span></span>

- <span data-ttu-id="70980-780">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-780">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-781">**resource_instance** 리소스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="70980-781">**resource_instance** Pointer to resource instances.</span></span>
- <span data-ttu-id="70980-782">**count** 리소스 인스턴스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="70980-782">**count** Count of resource instances.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-783">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-783">Return Values</span></span>

- <span data-ttu-id="70980-784">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-784">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-785">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-785">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-786">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-786">Allowed From</span></span>

<span data-ttu-id="70980-787">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-787">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-788">예제</span><span class="sxs-lookup"><span data-stu-id="70980-788">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a><span data-ttu-id="70980-789">nx_lwm2m_client_resource_integer32_get</span><span class="sxs-lookup"><span data-stu-id="70980-789">nx_lwm2m_client_resource_integer32_get</span></span>

<span data-ttu-id="70980-790">32비트 정수 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-790">Gets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-791">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-791">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-792">Description</span><span class="sxs-lookup"><span data-stu-id="70980-792">Description</span></span>

<span data-ttu-id="70980-793">이 서비스는 32비트 정수 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-793">The service retrieves the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-794">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-794">Parameters</span></span>

- <span data-ttu-id="70980-795">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-795">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-796">**integer32_ptr** 32비트 정수 값에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-796">**integer32_ptr** Pointer to the 32-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-797">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-797">Return Values</span></span>

- <span data-ttu-id="70980-798">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-798">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-799">**NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 정수 값이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="70980-799">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not integer value.</span></span>
- <span data-ttu-id="70980-800">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-800">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-801">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-801">Allowed From</span></span>

<span data-ttu-id="70980-802">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-802">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-803">예제</span><span class="sxs-lookup"><span data-stu-id="70980-803">Example</span></span>

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a><span data-ttu-id="70980-804">nx_lwm2m_client_resource_integer32_set</span><span class="sxs-lookup"><span data-stu-id="70980-804">nx_lwm2m_client_resource_integer32_set</span></span>

<span data-ttu-id="70980-805">32비트 정수 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-805">Sets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-806">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-806">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a><span data-ttu-id="70980-807">Description</span><span class="sxs-lookup"><span data-stu-id="70980-807">Description</span></span>

<span data-ttu-id="70980-808">이 서비스는 32비트 정수 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-808">The service sets the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-809">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-809">Parameters</span></span>

- <span data-ttu-id="70980-810">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-810">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-811">**integer32_data** 32비트 정수 데이터.</span><span class="sxs-lookup"><span data-stu-id="70980-811">**integer32_data** 32-Bit integer data.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-812">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-812">Return Values</span></span>

- <span data-ttu-id="70980-813">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-813">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-814">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-814">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-815">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-815">Allowed From</span></span>

<span data-ttu-id="70980-816">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-816">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-817">예제</span><span class="sxs-lookup"><span data-stu-id="70980-817">Example</span></span>

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a><span data-ttu-id="70980-818">nx_lwm2m_client_resource_integer64_get</span><span class="sxs-lookup"><span data-stu-id="70980-818">nx_lwm2m_client_resource_integer64_get</span></span>

<span data-ttu-id="70980-819">64비트 정수 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-819">Gets the value of a 64-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-820">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-820">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-821">Description</span><span class="sxs-lookup"><span data-stu-id="70980-821">Description</span></span>

<span data-ttu-id="70980-822">이 서비스는 64비트 정수 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-822">The service retrieves the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-823">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-823">Parameters</span></span>

- <span data-ttu-id="70980-824">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-824">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-825">**integer64_ptr** 64비트 정수 값에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-825">**integer64_ptr** Pointer to the 64-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-826">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-826">Return Values</span></span>

- <span data-ttu-id="70980-827">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-827">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-828">**NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 64비트 정수 값이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="70980-828">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not 64-Bit integer value.</span></span>
- <span data-ttu-id="70980-829">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-829">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-830">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-830">Allowed From</span></span>

<span data-ttu-id="70980-831">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-831">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-832">예제</span><span class="sxs-lookup"><span data-stu-id="70980-832">Example</span></span>

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a><span data-ttu-id="70980-833">nx_lwm2m_client_resource_integer64_set</span><span class="sxs-lookup"><span data-stu-id="70980-833">nx_lwm2m_client_resource_integer64_set</span></span>

## <a name="set-the-value-of-a-64-bit-integer-resource"></a><span data-ttu-id="70980-834">64비트 정수 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-834">Set the value of a 64-Bit integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-835">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-835">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a><span data-ttu-id="70980-836">Description</span><span class="sxs-lookup"><span data-stu-id="70980-836">Description</span></span>

<span data-ttu-id="70980-837">이 서비스는 64비트 정수 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-837">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-838">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-838">Parameters</span></span>

- <span data-ttu-id="70980-839">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-839">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-840">**integer64_data** 64비트 정수.</span><span class="sxs-lookup"><span data-stu-id="70980-840">**integer64_data** 64-bit integer.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-841">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-841">Return Values</span></span>

- <span data-ttu-id="70980-842">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-842">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-843">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-843">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-844">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-844">Allowed From</span></span>

<span data-ttu-id="70980-845">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-845">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-846">예제</span><span class="sxs-lookup"><span data-stu-id="70980-846">Example</span></span>

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a><span data-ttu-id="70980-847">nx_lwm2m_client_resource_objlnk_get</span><span class="sxs-lookup"><span data-stu-id="70980-847">nx_lwm2m_client_resource_objlnk_get</span></span>

<span data-ttu-id="70980-848">개체 링크 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-848">Gets the value of an object link resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-849">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-849">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a><span data-ttu-id="70980-850">Description</span><span class="sxs-lookup"><span data-stu-id="70980-850">Description</span></span>

<span data-ttu-id="70980-851">이 서비스는 개체 링크의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-851">The service retrieves the value of object link.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-852">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-852">Parameters</span></span>

- <span data-ttu-id="70980-853">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-853">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-854">**object_id** 개체 ID에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-854">**object_id** Pointer to the object ID.</span></span>
- <span data-ttu-id="70980-855">**instance_id** 개체 인스턴스 ID에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-855">**instance_id** Pointer to the object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-856">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-856">Return Values</span></span>

- <span data-ttu-id="70980-857">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-857">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-858">**NX_LWM2M_BAD_ENCODING**: 리소스 값이 개체 링크 값이 아님.</span><span class="sxs-lookup"><span data-stu-id="70980-858">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an object link value.</span></span>
- <span data-ttu-id="70980-859">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-859">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-860">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-860">Allowed From</span></span>

<span data-ttu-id="70980-861">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-861">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-862">예제</span><span class="sxs-lookup"><span data-stu-id="70980-862">Example</span></span>

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a><span data-ttu-id="70980-863">nx_lwm2m_client_resource_objlnk_set</span><span class="sxs-lookup"><span data-stu-id="70980-863">nx_lwm2m_client_resource_objlnk_set</span></span>

<span data-ttu-id="70980-864">리소스 인스턴스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-864">Sets the resource instances</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-865">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-865">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="70980-866">Description</span><span class="sxs-lookup"><span data-stu-id="70980-866">Description</span></span>

<span data-ttu-id="70980-867">서비스는 개체 링크 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-867">The service sets the value of the object link resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-868">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-868">Parameters</span></span>

- <span data-ttu-id="70980-869">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-869">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-870">**object_id** 개체 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-870">**object_id** Object ID.</span></span>
- <span data-ttu-id="70980-871">**instance_id** 개체 인스턴스 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-871">**instance_id** Object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-872">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-872">Return Values</span></span>

- <span data-ttu-id="70980-873">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-873">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-874">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-874">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-875">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-875">Allowed From</span></span>

<span data-ttu-id="70980-876">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-876">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-877">예제</span><span class="sxs-lookup"><span data-stu-id="70980-877">Example</span></span>

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a><span data-ttu-id="70980-878">nx_lwm2m_client_resource_opaque_get</span><span class="sxs-lookup"><span data-stu-id="70980-878">nx_lwm2m_client_resource_opaque_get</span></span>

<span data-ttu-id="70980-879">불투명 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-879">Gets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-880">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-880">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a><span data-ttu-id="70980-881">Description</span><span class="sxs-lookup"><span data-stu-id="70980-881">Description</span></span>

<span data-ttu-id="70980-882">이 서비스는 불투명 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-882">The service retrieves the value of an opaque Resource.</span></span> <span data-ttu-id="70980-883">불투명 리소스 값은 버퍼 및 길이에 대한 포인터로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-883">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-884">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-884">Parameters</span></span>

- <span data-ttu-id="70980-885">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-885">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-886">**opaque_ptr** 불투명 데이터에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-886">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="70980-887">**opaque_length** 불투명 데이터 길이에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-887">**opaque_length** Pointer to the opaque data length.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-888">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-888">Return Values</span></span>

- <span data-ttu-id="70980-889">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-889">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-890">**NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 불투명 리소스가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="70980-890">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an opaque resource.</span></span>
- <span data-ttu-id="70980-891">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-891">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-892">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-892">Allowed From</span></span>

<span data-ttu-id="70980-893">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-893">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-894">예제</span><span class="sxs-lookup"><span data-stu-id="70980-894">Example</span></span>

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a><span data-ttu-id="70980-895">nx_lwm2m_client_resource_opaque_set</span><span class="sxs-lookup"><span data-stu-id="70980-895">nx_lwm2m_client_resource_opaque_set</span></span>

<span data-ttu-id="70980-896">불투명 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-896">Sets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-897">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-897">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a><span data-ttu-id="70980-898">Description</span><span class="sxs-lookup"><span data-stu-id="70980-898">Description</span></span>

<span data-ttu-id="70980-899">이 서비스는 불투명 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-899">The service sets the value of an opaque Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-900">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-900">Parameters</span></span>

- <span data-ttu-id="70980-901">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-901">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-902">**opaque_ptr** 불투명 데이터에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-902">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="70980-903">**opaque_length** 불투명 데이터의 길이.</span><span class="sxs-lookup"><span data-stu-id="70980-903">**opaque_length** Length of the opaque data.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-904">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-904">Return Values</span></span>

- <span data-ttu-id="70980-905">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-905">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-906">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-906">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-907">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-907">Allowed From</span></span>

<span data-ttu-id="70980-908">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-908">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-909">예제</span><span class="sxs-lookup"><span data-stu-id="70980-909">Example</span></span>

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a><span data-ttu-id="70980-910">nx_lwm2m_client_resource_string_get</span><span class="sxs-lookup"><span data-stu-id="70980-910">nx_lwm2m_client_resource_string_get</span></span>

<span data-ttu-id="70980-911">문자열 리소스의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-911">Gets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-912">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-912">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a><span data-ttu-id="70980-913">Description</span><span class="sxs-lookup"><span data-stu-id="70980-913">Description</span></span>

<span data-ttu-id="70980-914">이 서비스는 문자열 리소스의 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-914">The service retrieves the value of a string Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-915">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-915">Parameters</span></span>

- <span data-ttu-id="70980-916">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-916">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-917">**string_ptr** 대상 문자열 포인터에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-917">**string_ptr** Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="70980-918">**string_length** 대상 문자열 길이에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-918">**string_length** Pointer to the destination string length.</span></span> <span data-ttu-id="70980-919">문자열이 null로 끝나는 경우 **NULL** 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-919">Can be **NULL** if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-920">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-920">Return Values</span></span>

- <span data-ttu-id="70980-921">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-921">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-922">**NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 문자열 값이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="70980-922">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a string value.</span></span>
- <span data-ttu-id="70980-923">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-923">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-924">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-924">Allowed From</span></span>

<span data-ttu-id="70980-925">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-925">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-926">예제</span><span class="sxs-lookup"><span data-stu-id="70980-926">Example</span></span>

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a><span data-ttu-id="70980-927">nx_lwm2m_client_resource_string_set</span><span class="sxs-lookup"><span data-stu-id="70980-927">nx_lwm2m_client_resource_string_set</span></span>

<span data-ttu-id="70980-928">문자열 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-928">Sets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-929">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-929">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a><span data-ttu-id="70980-930">Description</span><span class="sxs-lookup"><span data-stu-id="70980-930">Description</span></span>

<span data-ttu-id="70980-931">이 서비스는 64비트 정수 리소스의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-931">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-932">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-932">Parameters</span></span>

- <span data-ttu-id="70980-933">**resource** 리소스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-933">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="70980-934">**string_ptr** 문자열에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-934">**string_ptr** Pointer to the string.</span></span>
- <span data-ttu-id="70980-935">**string_length** 문자열의 길이.</span><span class="sxs-lookup"><span data-stu-id="70980-935">**string_length** Length of the string.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-936">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-936">Return Values</span></span>

- <span data-ttu-id="70980-937">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-937">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-938">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-938">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-939">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-939">Allowed From</span></span>

<span data-ttu-id="70980-940">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-940">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-941">예제</span><span class="sxs-lookup"><span data-stu-id="70980-941">Example</span></span>

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="70980-942">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="70980-942">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="70980-943">부트스트랩 서버를 사용하여 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-943">Starts a session with a Bootstrap Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-944">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-944">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a><span data-ttu-id="70980-945">Description</span><span class="sxs-lookup"><span data-stu-id="70980-945">Description</span></span>

<span data-ttu-id="70980-946">이 서비스는 부트스트랩 서버를 사용하여 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-946">This service starts a session with a Bootstrap Server.</span></span> <span data-ttu-id="70980-947">서버의 보안 개체에는 해당 보안 인스턴스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-947">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="70980-948">이 서버와 연결된 보안 인스턴스에서 'Hold Off'(지연) 리소스가 0과 다른 경우 세션에서 서버 시작 부트스트랩을 기다리며, 이 기간 이후에 서버에서 부트스트랩을 시작하지 않으면 클라이언트 시작 부트스트랩이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-948">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, If no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="70980-949">현재 활성 세션은 이 호출에서 중단되고 새 부트스트랩 서버 세션으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-949">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-950">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-950">Parameters</span></span>

- <span data-ttu-id="70980-951">**session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-951">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="70980-952">**security_id** 부트스트랩 서버의 보안 인스턴스 ID이며, 부트스트랩 서버에 정의된 보안 인스턴스가 없는 경우 NX_LWM2M_RESERVED_ID (65535)로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-952">**security_id** The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="70980-953">**ip_address** 서버의 IP 주소.</span><span class="sxs-lookup"><span data-stu-id="70980-953">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="70980-954">**port** 서버의 UDP 포트.</span><span class="sxs-lookup"><span data-stu-id="70980-954">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-955">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-955">Return Values</span></span>

- <span data-ttu-id="70980-956">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-956">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-957">**NX_LWM2M_CLIENT_ERROR** 부트스트랩 오류.</span><span class="sxs-lookup"><span data-stu-id="70980-957">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="70980-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** 포트를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="70980-959">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-959">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-960">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-960">Allowed From</span></span>

<span data-ttu-id="70980-961">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-961">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-962">예제</span><span class="sxs-lookup"><span data-stu-id="70980-962">Example</span></span>

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="70980-963">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="70980-963">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="70980-964">부트스트랩 서버를 사용하여 보안 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-964">Starts a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-965">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-965">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-966">Description</span><span class="sxs-lookup"><span data-stu-id="70980-966">Description</span></span>

<span data-ttu-id="70980-967">이 서비스는 보안 DTLS 연결을 사용하여 부트스트랩 서버에서 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-967">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="70980-968">서버의 보안 개체에는 해당 보안 인스턴스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-968">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="70980-969">이 함수를 호출하기 전에 DTLS 세션을 적절한 암호 그룹 및 키 자료를 사용하여 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-969">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="70980-970">**NX_SECURE_ENABLE_DTLS** 를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-970">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="70980-971">이 서버와 연결된 보안 인스턴스에서 'Hold Off'(지연) 리소스가 0과 다른 경우 세션에서 서버 시작 부트스트랩을 기다리며, 이 기간 이후에 서버에서 부트스트랩을 시작하지 않으면 클라이언트 시작 부트스트랩이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-971">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span> 

<span data-ttu-id="70980-972">현재 활성 세션은 이 호출에서 중단되고 새 부트스트랩 서버 세션으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-972">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-973">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-973">Parameters</span></span>

- <span data-ttu-id="70980-974">**session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-974">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="70980-975">**security_id** 부트스트랩 서버의 보안 인스턴스 ID이며, 부트스트랩 서버에 정의된 보안 인스턴스가 없는 경우 **NX_LWM2M_RESERVED_ID** (65535)로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-975">**security_id** The Security Instance ID of the Bootstrap Server, must be set to **NX_LWM2M_RESERVED_ID** (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="70980-976">**ip_address** 서버의 IP 주소.</span><span class="sxs-lookup"><span data-stu-id="70980-976">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="70980-977">**port** 서버의 UDP 포트.</span><span class="sxs-lookup"><span data-stu-id="70980-977">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="70980-978">**dtls_session_ptr** 부트스트랩 세션에 사용하는 DTLS 세션</span><span class="sxs-lookup"><span data-stu-id="70980-978">**dtls_session_ptr** The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="70980-979">**dtls_local_port** DTLS 세션에 사용되는 로컬 UDP 포트</span><span class="sxs-lookup"><span data-stu-id="70980-979">**dtls_local_port** The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-980">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-980">Return Values</span></span>

- <span data-ttu-id="70980-981">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-981">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-982">**NX_LWM2M_CLIENT_ERROR** 부트스트랩 오류.</span><span class="sxs-lookup"><span data-stu-id="70980-982">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="70980-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** 포트를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="70980-984">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-984">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-985">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-985">Allowed From</span></span>

<span data-ttu-id="70980-986">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-986">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-987">예제</span><span class="sxs-lookup"><span data-stu-id="70980-987">Example</span></span>

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="70980-988">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="70980-988">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="70980-989">LWM2M 클라이언트 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="70980-989">Creates a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-990">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-990">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="70980-991">Description</span><span class="sxs-lookup"><span data-stu-id="70980-991">Description</span></span>

<span data-ttu-id="70980-992">이 서비스는 기존 LWM2M 클라이언트에 연결된 새 LWM2M 클라이언트 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="70980-992">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="70980-993">이 세션은 LWM2M 클라이언트에서 부트스트랩 서버 또는 LWM2M 서버와 통신하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-993">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span> 

<span data-ttu-id="70980-994">애플리케이션에서 세션 상태가 업데이트될 때 호출되는 콜백 함수를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-994">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-995">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-995">Parameters</span></span>

- <span data-ttu-id="70980-996">**session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-996">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="70980-997">**client_ptr** 이전에 만든 LWM2M 클라이언트에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-997">**client_ptr** Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="70980-998">**state_callback** 세션의 상태가 변경되었을 때 호출되는 애플리케이션 콜백.</span><span class="sxs-lookup"><span data-stu-id="70980-998">**state_callback** Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-999">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-999">Return Values</span></span>

- <span data-ttu-id="70980-1000">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-1000">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-1001">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1001">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-1002">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-1002">Allowed From</span></span>

<span data-ttu-id="70980-1003">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-1003">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-1004">예제</span><span class="sxs-lookup"><span data-stu-id="70980-1004">Example</span></span>

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="70980-1005">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="70980-1005">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="70980-1006">LWM2M 클라이언트 세션 삭제하기</span><span class="sxs-lookup"><span data-stu-id="70980-1006">Deletes a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-1007">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-1007">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-1008">Description</span><span class="sxs-lookup"><span data-stu-id="70980-1008">Description</span></span>

<span data-ttu-id="70980-1009">이 서비스는 LWM2M 클라이언트 세션을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1009">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="70980-1010">nx_lwm2m_client_delete를 호출하여 LWM2M 클라이언트를 삭제하면 클라이언트에 연결된 모든 세션도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1010">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-1011">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-1011">Parameters</span></span>

- <span data-ttu-id="70980-1012">**session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1012">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-1013">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-1013">Return Values</span></span>

- <span data-ttu-id="70980-1014">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-1014">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-1015">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1015">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-1016">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-1016">Allowed From</span></span>

<span data-ttu-id="70980-1017">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-1017">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-1018">예제</span><span class="sxs-lookup"><span data-stu-id="70980-1018">Example</span></span>

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="70980-1019">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="70980-1019">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="70980-1020">LWM2M 서버를 사용하여 세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1020">Terminates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-1021">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-1021">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-1022">Description</span><span class="sxs-lookup"><span data-stu-id="70980-1022">Description</span></span>

<span data-ttu-id="70980-1023">이 서비스는 LWM2M 서버에 대한 'De-Register(등록 취소)' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1023">This service performs a ‘De-Register’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-1024">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-1024">Parameters</span></span>

- <span data-ttu-id="70980-1025">**session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1025">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-1026">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-1026">Return Values</span></span>

- <span data-ttu-id="70980-1027">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-1027">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** 클라이언트가 서버에 등록되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="70980-1029">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1029">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-1030">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-1030">Allowed From</span></span>

<span data-ttu-id="70980-1031">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-1031">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-1032">예제</span><span class="sxs-lookup"><span data-stu-id="70980-1032">Example</span></span>

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="70980-1033">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="70980-1033">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="70980-1034">세션의 마지막 오류를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1034">Gets the last error of a session.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-1035">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-1035">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-1036">Description</span><span class="sxs-lookup"><span data-stu-id="70980-1036">Description</span></span>

<span data-ttu-id="70980-1037">세션이 오류 상태인 경우 이 서비스에서 세션의 오류 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1037">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-1038">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-1038">Parameters</span></span>

- <span data-ttu-id="70980-1039">**session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1039">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-1040">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-1040">Return Values</span></span>

- <span data-ttu-id="70980-1041">**NX_SUCCESS** 세션이 오류 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1041">**NX_SUCCESS** The session is not in error state.</span></span>
- <span data-ttu-id="70980-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** 잘못된 서버 주소.</span><span class="sxs-lookup"><span data-stu-id="70980-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** Invalid server address.</span></span>
- <span data-ttu-id="70980-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** 요청의 페이로드가 네트워크 버퍼에 맞지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Payload of request doesn’t fit in network buffer.</span></span>
- <span data-ttu-id="70980-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** 서버와의 보안 연결을 설정하지 못함.</span><span class="sxs-lookup"><span data-stu-id="70980-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="70980-1045">**NX_LWM2M_ CLIENT_ERROR** 지정되지 않은 오류.</span><span class="sxs-lookup"><span data-stu-id="70980-1045">**NX_LWM2M_ CLIENT_ERROR** Unspecified error.</span></span>
- <span data-ttu-id="70980-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** 서버에서 등록을 거부함.</span><span class="sxs-lookup"><span data-stu-id="70980-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** Registration refused by server.</span></span>
- <span data-ttu-id="70980-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** 업데이트/등록 취소 시 서버에서 클라이언트를 찾을 수 없음.</span><span class="sxs-lookup"><span data-stu-id="70980-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="70980-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** 세션에 해당하는 서버 개체 인스턴스가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="70980-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** 서버에서 응답하지 않음.</span><span class="sxs-lookup"><span data-stu-id="70980-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** No answer from server.</span></span>
- <span data-ttu-id="70980-1050">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1050">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-1051">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-1051">Allowed From</span></span>

<span data-ttu-id="70980-1052">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-1052">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-1053">예제</span><span class="sxs-lookup"><span data-stu-id="70980-1053">Example</span></span>

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="70980-1054">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="70980-1054">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="70980-1055">LWM2M 서버를 사용하여 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1055">Starts a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-1056">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-1056">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a><span data-ttu-id="70980-1057">Description</span><span class="sxs-lookup"><span data-stu-id="70980-1057">Description</span></span>

<span data-ttu-id="70980-1058">이 서비스는 LWM2M 서버에 대한 'Register(등록)' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1058">This service performs a ‘Register’ operation to a LWM2M Server.</span></span> <span data-ttu-id="70980-1059">서버의 서버 개체에는 해당 서버 인스턴스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1059">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="70980-1060">등록이 성공하면 LWM2M 클라이언트는 서버에서 추가 작업을 처리하고, 클라이언트가 등록 취소될 때까지 'Update(업데이트)' 메시지를 정기적으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1060">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="70980-1061">현재 활성 세션은 이 호출에서 중단되고 새 LWM2M 서버 세션으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1061">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-1062">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-1062">Parameters</span></span>

- <span data-ttu-id="70980-1063">**session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1063">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="70980-1064">**server_id** LWM2M 서버의 약식 서버 ID</span><span class="sxs-lookup"><span data-stu-id="70980-1064">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="70980-1065">**ip_address** 서버의 IP 주소.</span><span class="sxs-lookup"><span data-stu-id="70980-1065">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="70980-1066">**port** 서버의 UDP 포트.</span><span class="sxs-lookup"><span data-stu-id="70980-1066">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-1067">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-1067">Return Values</span></span>

- <span data-ttu-id="70980-1068">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-1068">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-1069">**NX_LWM2M_CLIENT_ERROR** 부트스트랩 오류.</span><span class="sxs-lookup"><span data-stu-id="70980-1069">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="70980-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** 포트를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="70980-1071">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1071">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-1072">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-1072">Allowed From</span></span>

<span data-ttu-id="70980-1073">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-1073">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-1074">예제</span><span class="sxs-lookup"><span data-stu-id="70980-1074">Example</span></span>

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="70980-1075">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="70980-1075">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="70980-1076">LWM2M 서버를 사용하여 보안 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1076">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-1077">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-1077">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-1078">Description</span><span class="sxs-lookup"><span data-stu-id="70980-1078">Description</span></span>

<span data-ttu-id="70980-1079">이 서비스는 보안 DTLS 연결을 사용하여 LWM2M 서버에 대한 'Register(등록)' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1079">This service performs a ‘Register’ operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="70980-1080">서버의 서버 개체에는 해당 서버 인스턴스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1080">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="70980-1081">이 함수를 호출하기 전에 DTLS 세션을 적절한 암호 그룹 및 키 자료를 사용하여 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1081">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="70980-1082">**NX_SECURE_ENABLE_DTLS** 를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1082">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="70980-1083">등록이 성공하면 LWM2M 클라이언트는 서버에서 추가 작업을 처리하고, 클라이언트가 등록 취소될 때까지 'Update(업데이트)' 메시지를 정기적으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1083">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="70980-1084">현재 활성 세션은 이 호출에서 중단되고 새 LWM2M 서버 세션으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1084">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-1085">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-1085">Parameters</span></span>

- <span data-ttu-id="70980-1086">**session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1086">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="70980-1087">**server_id** LWM2M 서버의 약식 서버 ID</span><span class="sxs-lookup"><span data-stu-id="70980-1087">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="70980-1088">**ip_address** 서버의 IP 주소.</span><span class="sxs-lookup"><span data-stu-id="70980-1088">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="70980-1089">**port** 서버의 UDP 포트.</span><span class="sxs-lookup"><span data-stu-id="70980-1089">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="70980-1090">**dtls_session_ptr** LWM2M 세션에 사용하는 DTLS 세션</span><span class="sxs-lookup"><span data-stu-id="70980-1090">**dtls_session_ptr** The DTLS session to use for the LWM2M session.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-1091">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-1091">Return Values</span></span>

- <span data-ttu-id="70980-1092">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-1092">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-1093">**NX_LWM2M_CLIENT_ERROR** 부트스트랩 오류.</span><span class="sxs-lookup"><span data-stu-id="70980-1093">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="70980-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** 포트를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="70980-1095">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1095">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-1096">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-1096">Allowed From</span></span>

<span data-ttu-id="70980-1097">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-1097">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-1098">예제</span><span class="sxs-lookup"><span data-stu-id="70980-1098">Example</span></span>

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a><span data-ttu-id="70980-1099">nx_lwm2m_client_session_register_info_get</span><span class="sxs-lookup"><span data-stu-id="70980-1099">nx_lwm2m_client_session_register_info_get</span></span>

<span data-ttu-id="70980-1100">LWM2M 서버를 사용하여 보안 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1100">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-1101">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-1101">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a><span data-ttu-id="70980-1102">Description</span><span class="sxs-lookup"><span data-stu-id="70980-1102">Description</span></span>

<span data-ttu-id="70980-1103">부트스트랩 서버와 통신 세션이 설정된 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1103">Once a communication session with a Bootstrap server was established.</span></span> <span data-ttu-id="70980-1104">애플리케이션은 이 api를 호출하여 서버 및 다음 등록 단계에 대한 보안 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1104">Application can call this api to get the server and security information for the next registration step.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-1105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-1105">Parameters</span></span>

- <span data-ttu-id="70980-1106">**session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1106">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="70980-1107">**security_instance_id** 보안 인스턴스 ID.</span><span class="sxs-lookup"><span data-stu-id="70980-1107">**security_instance_id** Security instance ID.</span></span>
- <span data-ttu-id="70980-1108">**server_id** 대상 서버 ID에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1108">**server_id** Pointer to destination server ID.</span></span>
- <span data-ttu-id="70980-1109">**server_uri** 대상 서버 uri에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1109">**server_uri** Pointer to destination server uri.</span></span>
- <span data-ttu-id="70980-1110">**server_uri_len** 대상 서버 uri 길이에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1110">**server_uri_len** Pointer to destination server uri length.</span></span>
- <span data-ttu-id="70980-1111">**security_mode** 대상 보안 모드에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1111">**security_mode** Pointer to destination security mode.</span></span>
- <span data-ttu-id="70980-1112">**pub_key_or_id** 대상 공개 키 또는 ID에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1112">**pub_key_or_id** Pointer to destination public key or identity.</span></span>
- <span data-ttu-id="70980-1113">**pub_key_or_id_len** 대상 공개 키 또는 ID 길이에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1113">**pub_key_or_id_len** Pointer to destination public key or identity length.</span></span>
- <span data-ttu-id="70980-1114">**server_pub_key** 대상 서버 공개 키에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1114">**server_pub_key** Pointer to destination server public key.</span></span>
- <span data-ttu-id="70980-1115">**server_pub_key_len** 대상 서버 공개 키 길이에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1115">**server_pub_key_len** Pointer to destination server public key length.</span></span>
- <span data-ttu-id="70980-1116">**secret_key** 대상 비밀 키에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1116">**secret_key** Pointer to destination secret key.</span></span>
- <span data-ttu-id="70980-1117">**secret_key_len** 대상 비밀 키 길이에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1117">**secret_key_len** Pointer to destination secret key length.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-1118">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-1118">Return Values</span></span>

- <span data-ttu-id="70980-1119">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-1119">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-1120">**NX_LWM2M_CLIENT_NOT_FOUND** 보안 개체 인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1120">**NX_LWM2M_CLIENT_NOT_FOUND** There is no security Object instance.</span></span>
- <span data-ttu-id="70980-1121">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1121">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-1122">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-1122">Allowed From</span></span>

<span data-ttu-id="70980-1123">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-1123">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-1124">예제</span><span class="sxs-lookup"><span data-stu-id="70980-1124">Example</span></span>

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="70980-1125">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="70980-1125">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="70980-1126">LWM2M 서버를 사용하여 세션을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1126">Updates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-1127">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-1127">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-1128">Description</span><span class="sxs-lookup"><span data-stu-id="70980-1128">Description</span></span>

<span data-ttu-id="70980-1129">이 서비스는 LWM2M 서버에 대한 'Update(업데이트)' 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1129">This service performs an ‘Update’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-1130">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-1130">Parameters</span></span>

- <span data-ttu-id="70980-1131">**session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1131">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-1132">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-1132">Return Values</span></span>

- <span data-ttu-id="70980-1133">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-1133">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** 클라이언트가 서버에 등록되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="70980-1135">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1135">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-1136">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-1136">Allowed From</span></span>

<span data-ttu-id="70980-1137">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-1137">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-1138">예제</span><span class="sxs-lookup"><span data-stu-id="70980-1138">Example</span></span>

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="70980-1139">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="70980-1139">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="70980-1140">LWM2M 클라이언트의 잠금을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1140">Unlocks a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="70980-1141">프로토타입</span><span class="sxs-lookup"><span data-stu-id="70980-1141">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="70980-1142">Description</span><span class="sxs-lookup"><span data-stu-id="70980-1142">Description</span></span>

<span data-ttu-id="70980-1143">***nx_lwm2m_client_unlock*** 호출로 이전에 잠긴 LWM2M 클라이언트의 잠금을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="70980-1143">This service unlocks the LWM2M Client previously locked by a call to ***nx_lwm2m_client_unlock***.</span></span>

### <a name="parameters"></a><span data-ttu-id="70980-1144">매개 변수</span><span class="sxs-lookup"><span data-stu-id="70980-1144">Parameters</span></span>

- <span data-ttu-id="70980-1145">**client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1145">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="70980-1146">반환 값</span><span class="sxs-lookup"><span data-stu-id="70980-1146">Return Values</span></span>

- <span data-ttu-id="70980-1147">**NX_SUCCESS** 작업 성공.</span><span class="sxs-lookup"><span data-stu-id="70980-1147">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="70980-1148">**NX_PTR_ERROR** 잘못된 포인터.</span><span class="sxs-lookup"><span data-stu-id="70980-1148">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="70980-1149">허용된 위치</span><span class="sxs-lookup"><span data-stu-id="70980-1149">Allowed From</span></span>

<span data-ttu-id="70980-1150">스레드, 초기화</span><span class="sxs-lookup"><span data-stu-id="70980-1150">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="70980-1151">예제</span><span class="sxs-lookup"><span data-stu-id="70980-1151">Example</span></span>

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```