---
title: 3장 - Azure RTOS NetX Duo SNMP 에이전트 서비스 설명
description: 이 장에서는 아래에 나열된 모든 NetX Duo SNMP 에이전트 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810584"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a><span data-ttu-id="3c32e-103">3장 - Azure RTOS NetX Duo SNMP 에이전트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="3c32e-103">Chapter 3 - Description of Azure RTOS NetX Duo SNMP agent services</span></span>

<span data-ttu-id="3c32e-104">이 장에서는 아래에 나열된 모든 Azure RTOS NetX Duo SNMP 에이전트 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-104">This chapter contains a description of all Azure RTOS NetX Duo SNMP agent services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="3c32e-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="3c32e-106">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="3c32e-106">nx_snmp_agent_auth_trap_key_use</span></span>](#nx_snmp_agent_auth_trap_key_use)
   - <span data-ttu-id="3c32e-107">트랩 메시지의 인증 키(SNMP v3만 해당) 지정</span><span class="sxs-lookup"><span data-stu-id="3c32e-107">*Specify authentication key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="3c32e-108">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="3c32e-108">nx_snmp_agent_authenticate_key_use</span></span>](#nx_snmp_agent_authenticate_key_use)
   - <span data-ttu-id="3c32e-109">응답 메시지의 인증 키(SNMP v3만 해당) 지정</span><span class="sxs-lookup"><span data-stu-id="3c32e-109">*Specify authentication key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="3c32e-110">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-110">nx_snmp_agent_community_get</span></span>](#nx_snmp_agent_community_get)
   - <span data-ttu-id="3c32e-111">커뮤니티 이름 검색</span><span class="sxs-lookup"><span data-stu-id="3c32e-111">*Retrieve community name*</span></span>
- [<span data-ttu-id="3c32e-112">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-112">nx_snmp_agent_context_engine_set</span></span>](#nx_snmp_agent_context_engine_set)
   - <span data-ttu-id="3c32e-113">컨텍스트 엔진 설정(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-113">*Set context engine (SNMP v3 only)*</span></span>
- [<span data-ttu-id="3c32e-114">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-114">nx_snmp_agent_context_name_set</span></span>](#nx_snmp_agent_context_name_set)
   - <span data-ttu-id="3c32e-115">컨텍스트 이름 설정(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-115">*Set context name (SNMP v3 only)*</span></span>
- [<span data-ttu-id="3c32e-116">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="3c32e-116">nx_snmp_agent_create</span></span>](#nx_snmp_agent_create)
   - <span data-ttu-id="3c32e-117">SNMP 에이전트 만들기</span><span class="sxs-lookup"><span data-stu-id="3c32e-117">*Create SNMP agent*</span></span>
- [<span data-ttu-id="3c32e-118">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-118">nx_snmp_agent_current_version_get</span></span>](#nx_snmp_agent_current_version_get)
   - <span data-ttu-id="3c32e-119">수신된 패킷의 SNMP 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-119">*Get the SNMP version of received packet*</span></span>
- [<span data-ttu-id="3c32e-120">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="3c32e-120">nx_snmp_agent_request_get_type_test</span></span>](#nx_snmp_agent_request_get_type_test)
   - <span data-ttu-id="3c32e-121">마지막 SNMP 요청이 GET 형식인지 또는 SET 형식인지 지정</span><span class="sxs-lookup"><span data-stu-id="3c32e-121">*Indicate if last SNMP request is GET or SET type*</span></span>
- [<span data-ttu-id="3c32e-122">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="3c32e-122">nx_snmp_agent_private_string_test</span></span>](#nx_snmp_agent_private_string_test)
   - <span data-ttu-id="3c32e-123">문자열이 에이전트 프라이빗 문자열과 일치하는지 확인</span><span class="sxs-lookup"><span data-stu-id="3c32e-123">*Determine if string matches agent private string*</span></span>
- [<span data-ttu-id="3c32e-124">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="3c32e-124">nx_snmp_agent_public_string_test</span></span>](#nx_snmp_agent_public_string_test)
   - <span data-ttu-id="3c32e-125">문자열이 에이전트 퍼블릭 문자열과 일치하는지 확인</span><span class="sxs-lookup"><span data-stu-id="3c32e-125">*Determine if string matches agent public string*</span></span>
- [<span data-ttu-id="3c32e-126">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="3c32e-126">nx_snmp_agent_set_interface</span></span>](#nx_snmp_agent_set_interface)
   - <span data-ttu-id="3c32e-127">SNMP 메시징에 대한 네트워크 인터페이스 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-127">*Set network interface for SNMP messaging*</span></span>
- [<span data-ttu-id="3c32e-128">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-128">nx_snmp_agent_private_string_set</span></span>](#nx_snmp_agent_private_string_set)
   - <span data-ttu-id="3c32e-129">SNMP 에이전트 프라이빗 커뮤니티 문자열 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-129">*Set the SNMP agent private community string*</span></span>
- [<span data-ttu-id="3c32e-130">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-130">nx_snmp_agent_public_string_set</span></span>](#nx_snmp_agent_public_string_set)
   - <span data-ttu-id="3c32e-131">SNMP 에이전트 퍼블릭 커뮤니티 문자열 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-131">*Set the SNMP agent public community string*</span></span>
- [<span data-ttu-id="3c32e-132">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-132">nx_snmp_agent_version_set</span></span>](#nx_snmp_agent_version_set)
   - <span data-ttu-id="3c32e-133">모든 SNMP 버전의 SNMP 에이전트 상태 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-133">*Set the SNMP agent status for all SNMP versions*</span></span>
- [<span data-ttu-id="3c32e-134">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="3c32e-134">nx_snmp_agent_delete</span></span>](#nx_snmp_agent_delete)
   - <span data-ttu-id="3c32e-135">SNMP 에이전트 삭제</span><span class="sxs-lookup"><span data-stu-id="3c32e-135">*Delete SNMP agent*</span></span>
- [<span data-ttu-id="3c32e-136">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="3c32e-136">nx_snmp_agent_md5_key_create</span></span>](#nx_snmp_agent_md5_key_create)
   - <span data-ttu-id="3c32e-137">md5 키 만들기(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-137">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="3c32e-138">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="3c32e-138">nx_snmp_agent_md5_key_create_extended</span></span>](#nx_snmp_agent_md5_key_create_extended)
   - <span data-ttu-id="3c32e-139">md5 키 만들기(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-139">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="3c32e-140">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="3c32e-140">nx_snmp_agent_priv_trap_key_use</span></span>](#nx_snmp_agent_priv_trap_key_use)
   - <span data-ttu-id="3c32e-141">트랩 메시지의 암호화 키(SNMP v3만 해당) 지정</span><span class="sxs-lookup"><span data-stu-id="3c32e-141">*Specify encryption key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="3c32e-142">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="3c32e-142">nx_snmp_agent_privacy_key_use</span></span>](#nx_snmp_agent_privacy_key_use)
   - <span data-ttu-id="3c32e-143">응답 메시지의 암호화 키(SNMP v3만 해당) 지정</span><span class="sxs-lookup"><span data-stu-id="3c32e-143">*Specify encryption key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="3c32e-144">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="3c32e-144">nx_snmp_agent_sha_key_create</span></span>](#nx_snmp_agent_sha_key_create)
   - <span data-ttu-id="3c32e-145">sha 키 만들기(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-145">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="3c32e-146">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="3c32e-146">nx_snmp_agent_sha_key_create_extended</span></span>](#nx_snmp_agent_sha_key_create_extended)
   - <span data-ttu-id="3c32e-147">sha 키 만들기(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-147">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="3c32e-148">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="3c32e-148">nx_snmp_agent_start</span></span>](#nx_snmp_agent_start)
   - <span data-ttu-id="3c32e-149">SNMP 에이전트 시작</span><span class="sxs-lookup"><span data-stu-id="3c32e-149">*Start SNMP agent*</span></span>
- [<span data-ttu-id="3c32e-150">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="3c32e-150">nx_snmp_agent_stop</span></span>](#nx_snmp_agent_stop)
   - <span data-ttu-id="3c32e-151">SNMP 에이전트 중지</span><span class="sxs-lookup"><span data-stu-id="3c32e-151">*Stop SNMP agent*</span></span>
- [<span data-ttu-id="3c32e-152">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-152">nx_snmp_agent_trap_send</span></span>](#nx_snmp_agent_trap_send)
   - <span data-ttu-id="3c32e-153">SNMP v1 트랩 보내기(IPv4만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-153">*Send SNMP v1 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="3c32e-154">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-154">nx_snmp_agent_trapv2_send</span></span>](#nx_snmp_agent_trapv2_send)
   - <span data-ttu-id="3c32e-155">SNMP v2 트랩 보내기(IPv4만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-155">*Send SNMP v2 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="3c32e-156">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-156">nx_snmp_agent_trapv2_oid_send</span></span>](#nx_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="3c32e-157">OID를 지정하여 SNMP v2 트랩 보내기(IPv4만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-157">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="3c32e-158">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-158">nx_snmp_agent_trapv3_send</span></span>](#nx_snmp_agent_trapv3_send)
   - <span data-ttu-id="3c32e-159">SNMP v3 트랩 보내기(IPv4만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-159">*Send SNMP v3 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="3c32e-160">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-160">nx_snmp_agent_trapv3_oid_send</span></span>](#nx_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="3c32e-161">OID를 지정하여 SNMP v2 트랩 보내기(IPv4만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-161">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="3c32e-162">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-162">nxd_snmp_agent_trap_send</span></span>](#nxd_snmp_agent_trap_send)
   - <span data-ttu-id="3c32e-163">SNMP v1 트랩 보내기(IPv4 및 IPv6)</span><span class="sxs-lookup"><span data-stu-id="3c32e-163">*Send SNMP v1 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="3c32e-164">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-164">nxd_snmp_agent_trapv2_send</span></span>](#nxd_snmp_agent_trapv2_send)
   - <span data-ttu-id="3c32e-165">SNMP v2 트랩 보내기(IPv4 및 IPv6)</span><span class="sxs-lookup"><span data-stu-id="3c32e-165">*Send SNMP v2 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="3c32e-166">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-166">nxd_snmp_agent_trapv2_oid_send</span></span>](#nxd_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="3c32e-167">OID를 지정하여 SNMP v2 트랩 보내기(IPv4/IPv6)</span><span class="sxs-lookup"><span data-stu-id="3c32e-167">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="3c32e-168">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-168">nxd_snmp_agent_trapv3_send</span></span>](#nxd_snmp_agent_trapv3_send)
   - <span data-ttu-id="3c32e-169">SNMP v3 트랩 보내기(IPv4 및 IPv6)</span><span class="sxs-lookup"><span data-stu-id="3c32e-169">*Send SNMP v3 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="3c32e-170">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-170">nxd_snmp_agent_trapv3_oid_send</span></span>](#nxd_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="3c32e-171">OID를 지정하여 SNMP v2 트랩 보내기(IPv4/IPv6)</span><span class="sxs-lookup"><span data-stu-id="3c32e-171">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="3c32e-172">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-172">nx_snmp_agent_v3_context_boots_set</span></span>](#nx_snmp_agent_v3_context_boots_set)
   - <span data-ttu-id="3c32e-173">다시 부팅 수 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-173">*Set the number of reboots*</span></span>
- [<span data-ttu-id="3c32e-174">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="3c32e-174">nx_snmp_object_compare</span></span>](#nx_snmp_object_compare)
   - <span data-ttu-id="3c32e-175">두 개체 비교</span><span class="sxs-lookup"><span data-stu-id="3c32e-175">*Compare two objects*</span></span>
- [<span data-ttu-id="3c32e-176">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="3c32e-176">nx_snmp_object_compare_extended</span></span>](#nx_snmp_object_compare_extended)
   - <span data-ttu-id="3c32e-177">두 개체 비교</span><span class="sxs-lookup"><span data-stu-id="3c32e-177">*Compare two objects*</span></span>
- [<span data-ttu-id="3c32e-178">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="3c32e-178">nx_snmp_object_copy</span></span>](#nx_snmp_object_copy)
   - <span data-ttu-id="3c32e-179">개체 복사</span><span class="sxs-lookup"><span data-stu-id="3c32e-179">*Copy an object*</span></span>
- [<span data-ttu-id="3c32e-180">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="3c32e-180">nx_snmp_object_copy_extended</span></span>](#nx_snmp_object_copy_extended)
   - <span data-ttu-id="3c32e-181">개체 복사</span><span class="sxs-lookup"><span data-stu-id="3c32e-181">*Copy an object*</span></span>
- [<span data-ttu-id="3c32e-182">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-182">nx_snmp_object_counter_get</span></span>](#nx_snmp_object_counter_get)
   - <span data-ttu-id="3c32e-183">카운터 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-183">*Get counter object*</span></span>
- [<span data-ttu-id="3c32e-184">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-184">nx_snmp_object_counter_set</span></span>](#nx_snmp_object_counter_set)
   - <span data-ttu-id="3c32e-185">카운터 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-185">*Set counter object*</span></span>
- [<span data-ttu-id="3c32e-186">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-186">nx_snmp_object_counter64_get</span></span>](#nx_snmp_object_counter64_get)
   - <span data-ttu-id="3c32e-187">64비트 카운터 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-187">*Get 64-bit counter object*</span></span>
- [<span data-ttu-id="3c32e-188">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-188">nx_snmp_object_counter64_set</span></span>](#nx_snmp_object_counter64_set)
   - <span data-ttu-id="3c32e-189">64비트 카운터 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-189">*Set 64-bit counter object*</span></span>
- [<span data-ttu-id="3c32e-190">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="3c32e-190">nx_snmp_object_end_of_mib</span></span>](#nx_snmp_object_end_of_mib)
   - <span data-ttu-id="3c32e-191">end-of-mib 값 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-191">*Set end-of-mib value*</span></span>
- [<span data-ttu-id="3c32e-192">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-192">nx_snmp_object_gauge_get</span></span>](#nx_snmp_object_gauge_get)
   - <span data-ttu-id="3c32e-193">계기 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-193">*Get gauge object*</span></span>
- [<span data-ttu-id="3c32e-194">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-194">nx_snmp_object_gauge_set</span></span>](#nx_snmp_object_gauge_set)
   - <span data-ttu-id="3c32e-195">계기 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-195">*Set gauge object*</span></span>
- [<span data-ttu-id="3c32e-196">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-196">nx_snmp_object_id_get</span></span>](#nx_snmp_object_id_get)
   - <span data-ttu-id="3c32e-197">개체 ID 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-197">*Get object id*</span></span>
- [<span data-ttu-id="3c32e-198">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-198">nx_snmp_object_id_set</span></span>](#nx_snmp_object_id_set)
   - <span data-ttu-id="3c32e-199">개체 ID 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-199">*Set object id*</span></span>
- [<span data-ttu-id="3c32e-200">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-200">nx_snmp_object_integer_get</span></span>](#nx_snmp_object_integer_get)
   - <span data-ttu-id="3c32e-201">정수 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-201">*Get integer object*</span></span>
- [<span data-ttu-id="3c32e-202">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-202">nx_snmp_object_integer_set</span></span>](#nx_snmp_object_integer_set)
   - <span data-ttu-id="3c32e-203">정수 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-203">*Set integer object*</span></span>
- [<span data-ttu-id="3c32e-204">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-204">nx_snmp_object_ip_address_get</span></span>](#nx_snmp_object_ip_address_get)
   - <span data-ttu-id="3c32e-205">IP 주소 개체 가져오기(IPv4만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-205">*Get IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="3c32e-206">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-206">nx_snmp_object_ip_address_set</span></span>](#nx_snmp_object_ip_address_set)
   - <span data-ttu-id="3c32e-207">IP 주소 개체 설정(IPv4만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-207">*Set IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="3c32e-208">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-208">nx_snmp_object_ipv6_address_get</span></span>](#nx_snmp_object_ipv6_address_get)
   - <span data-ttu-id="3c32e-209">IP 주소 개체 가져오기(IPv6만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-209">*Get IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="3c32e-210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-210">nx_snmp_object_ipv6_address_set</span></span>](#nx_snmp_object_ipv6_address_set)
   - <span data-ttu-id="3c32e-211">IP 주소 개체 설정(IPv6만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-211">*Set IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="3c32e-212">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="3c32e-212">nx_snmp_object_no_instance</span></span>](#nx_snmp_object_no_instance)
   - <span data-ttu-id="3c32e-213">no-instance 값 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-213">*Set no-instance value*</span></span>
- [<span data-ttu-id="3c32e-214">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="3c32e-214">nx_snmp_object_not_found</span></span>](#nx_snmp_object_not_found)
   - <span data-ttu-id="3c32e-215">not-found 값 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-215">*Set not-found value*</span></span>
- [<span data-ttu-id="3c32e-216">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-216">nx_snmp_object_octet_string_get</span></span>](#nx_snmp_object_octet_string_get)
   - <span data-ttu-id="3c32e-217">옥텟 문자열 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-217">*Get octet string object*</span></span>
- [<span data-ttu-id="3c32e-218">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-218">nx_snmp_object_octet_string_set</span></span>](#nx_snmp_object_octet_string_set)
   - <span data-ttu-id="3c32e-219">옥텟 문자열 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-219">*Set octet string object*</span></span>
- [<span data-ttu-id="3c32e-220">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-220">nx_snmp_object_string_get</span></span>](#nx_snmp_object_string_get)
   - <span data-ttu-id="3c32e-221">ASCII 문자열 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-221">*Get ASCII string object*</span></span>
- [<span data-ttu-id="3c32e-222">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-222">nx_snmp_object_string_set</span></span>](#nx_snmp_object_string_set)
   - <span data-ttu-id="3c32e-223">ASCII 문자열 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-223">*Set ASCII string object*</span></span>
- [<span data-ttu-id="3c32e-224">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-224">nx_snmp_object_timetics_get</span></span>](#nx_snmp_object_timetics_get)
   - <span data-ttu-id="3c32e-225">timetics 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-225">*Get timetics object*</span></span>
- [<span data-ttu-id="3c32e-226">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-226">nx_snmp_object_timetics_set</span></span>](#nx_snmp_object_timetics_set)
   - <span data-ttu-id="3c32e-227">timetics 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-227">*Set timetics object*</span></span>

## <a name="nx_snmp_agent_auth_trap_key_use"></a><span data-ttu-id="3c32e-228">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="3c32e-228">nx_snmp_agent_auth_trap_key_use</span></span>
<span data-ttu-id="3c32e-229">트랩 메시지의 인증 키 지정</span><span class="sxs-lookup"><span data-stu-id="3c32e-229">Specify authentication key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-230">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-230">Prototype</span></span>

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="3c32e-231">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-231">Description</span></span>

<span data-ttu-id="3c32e-232">이 서비스는 트랩 메시지의 SNMPv3 보안 헤더에서 인증 매개 변수를 설정하는 데 사용할 키를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-232">This service specifies the key to be used for setting authentication parameters in the SNMPv3 security header in trap messages.</span></span> <span data-ttu-id="3c32e-233">키에 대해 NX_NULL 값을 제공하면 인증이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-233">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="3c32e-234">이 키는 미리 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-234">The key must be previously created.</span></span> <span data-ttu-id="3c32e-235">nx_snmp_agent_md5_key_create 또는 nx_snmp_agent_sha_key_create를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c32e-235">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-236">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-236">Input Parameters</span></span>

- <span data-ttu-id="3c32e-237">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-237">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-238">**key** 이전에 만든 MD5 또는 SHA 키에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-238">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-239">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-239">Return Values</span></span>

- <span data-ttu-id="3c32e-240">**NX_SUCCESS**(0X00) 성공적인 인증 키 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-240">**NX_SUCCESS** (0x00) Successful authentication key set.</span></span>
- <span data-ttu-id="3c32e-241">**NX_NOT_ENABLED**(0X14) SNMP 보안이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-241">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span> 
- <span data-ttu-id="3c32e-242">**NX_PTR_ERROR**(0X07) 잘못된 SNMP 에이전트 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-242">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-243">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-243">Allowed From</span></span>

<span data-ttu-id="3c32e-244">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-244">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-245">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-245">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a><span data-ttu-id="3c32e-246">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="3c32e-246">nx_snmp_agent_authenticate_key_use</span></span>
<span data-ttu-id="3c32e-247">응답 메시지의 인증 키 지정</span><span class="sxs-lookup"><span data-stu-id="3c32e-247">Specify authentication key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-248">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-248">Prototype</span></span>

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="3c32e-249">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-249">Description</span></span>

<span data-ttu-id="3c32e-250">이 서비스는 설정된 후에 수행된 모든 요청에 대해 SNMPv3 보안 매개 변수의 인증 매개 변수에 사용할 키를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-250">This service specifies the key to be used for authentication parameters in the SNMPv3 security parameter for all requests made after it is set.</span></span> <span data-ttu-id="3c32e-251">키에 대해 NX_NULL 값을 제공하면 인증이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-251">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="3c32e-252">이 키는 미리 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-252">The key must be previously created.</span></span> <span data-ttu-id="3c32e-253">nx_snmp_agent_md5_key_create 또는 nx_snmp_agent_sha_key_create를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c32e-253">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-254">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-254">Input Parameters</span></span>

- <span data-ttu-id="3c32e-255">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-255">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-256">**key** 이전에 만든 MD5 또는 SHA 키에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-256">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-257">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-257">Return Values</span></span>

- <span data-ttu-id="3c32e-258">**NX_SUCCESS**(0x00) 성공적인 SNMP 키 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-258">**NX_SUCCESS** (0x00) Successful SNMP key set.</span></span>
- <span data-ttu-id="3c32e-259">**NX_NOT_ENABLED**(0X14) SNMP 보안이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-259">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span>
- <span data-ttu-id="3c32e-260">**NX_PTR_ERROR**(0X07) 잘못된 SNMP 에이전트 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-260">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-261">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-261">Allowed From</span></span>

<span data-ttu-id="3c32e-262">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-262">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-263">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-263">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a><span data-ttu-id="3c32e-264">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-264">nx_snmp_agent_community_get</span></span>
<span data-ttu-id="3c32e-265">커뮤니티 이름 검색</span><span class="sxs-lookup"><span data-stu-id="3c32e-265">Retrieve community name</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-266">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-266">Prototype</span></span>

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a><span data-ttu-id="3c32e-267">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-267">Description</span></span>

<span data-ttu-id="3c32e-268">이 서비스는 SNMP 에이전트에서 받은 가장 최근의 SNMP 요청에서 커뮤니티 이름을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-268">This service retrieves the community name from the most recent SNMP request received by the SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-269">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-269">Input Parameters</span></span>

- <span data-ttu-id="3c32e-270">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-270">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-271">**community_string_ptr** SNMP 에이전트 커뮤니티 문자열을 반환할 문자열 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-271">**community_string_ptr** Pointer to a string pointer to return the SNMP Agent community string.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-272">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-272">Return Values</span></span>

- <span data-ttu-id="3c32e-273">**NX_SUCCESS**(0x00) 성공적인 SNMP 커뮤니티 가져오기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-273">**NX_SUCCESS** (0x00) Successful SNMP community get.</span></span>
- <span data-ttu-id="3c32e-274">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-274">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-275">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-275">Allowed From</span></span>

<span data-ttu-id="3c32e-276">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-276">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-277">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-277">Example</span></span>

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a><span data-ttu-id="3c32e-278">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="3c32e-278">nx_snmp_agent_request_get_type_test</span></span>
<span data-ttu-id="3c32e-279">마지막 SNMP 요청이 GET 형식인지 또는 SET 형식인지 지정</span><span class="sxs-lookup"><span data-stu-id="3c32e-279">Indicate if last SNMP request is GET or SET type</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-280">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-280">Prototype</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a><span data-ttu-id="3c32e-281">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-281">Description</span></span>

<span data-ttu-id="3c32e-282">이 서비스는 SNMP 관리자의 가장 최근 요청이 GET 형식(GET, GETNEXT 또는 GETBULK)인지 또는 SET 형식인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-282">This service indicates if the most recent request from the SNMP Manager is a GET (GET, GETNEXT, or GETBULK) or SET type.</span></span> <span data-ttu-id="3c32e-283">SNMPv1 또는 SNMPv2 애플리케이션에서 요청이 GET 형식이면 수신된 커뮤니티 문자열을 SNMP 에이전트 퍼블릭 문자열과 비교하고, SET 형식이면 SNMP 에이전트 프라이빗 문자열과 비교하려는 사용자 이름 콜백과 함께 사용하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-283">It is intended for use with the username callback where the SNMPv1 or SNMPv2 application will want to compare the received community string to the SNMP Agent public string if the request is a GET type, or to the SNMP Agent private string if the request is a SET type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-284">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-284">Input Parameters</span></span>

- <span data-ttu-id="3c32e-285">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-285">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-286">**is_get_type** 요청 형식 상태에 대한 포인터로, 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-286">**is_get_type** Pointer to request type status:</span></span>  
<span data-ttu-id="3c32e-287">GET 형식이면 NX_TRUE</span><span class="sxs-lookup"><span data-stu-id="3c32e-287">NX_TRUE if GET type</span></span>  
<span data-ttu-id="3c32e-288">SET 형식이면 NX_FALSE</span><span class="sxs-lookup"><span data-stu-id="3c32e-288">NX_FALSE if SET type</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-289">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-289">Return Values</span></span>

- <span data-ttu-id="3c32e-290">**NX_SUCCESS**(0x00) 성공적으로 반환된 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-290">**NX_SUCCESS** (0x00) Successfully returned type</span></span>
- <span data-ttu-id="3c32e-291">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-291">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-292">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-292">Allowed From</span></span>

<span data-ttu-id="3c32e-293">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-293">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-294">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-294">Example</span></span>

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a><span data-ttu-id="3c32e-295">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-295">nx_snmp_agent_context_engine_set</span></span>
<span data-ttu-id="3c32e-296">컨텍스트 엔진 설정(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-296">Set context engine (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-297">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-297">Prototype</span></span>

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a><span data-ttu-id="3c32e-298">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-298">Description</span></span>

<span data-ttu-id="3c32e-299">이 서비스는 SNMP 에이전트의 컨텍스트 엔진을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-299">This service sets the context engine of the SNMP Agent.</span></span> <span data-ttu-id="3c32e-300">SNMPv3 처리에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-300">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="3c32e-301">컨텍스트 엔진 ID가 키 만들기 프로세스에서 사용되므로 애플리케이션이 인증 및 암호화를 사용하는 경우 보안 키를 만들기 전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-301">This should be called before creating security keys if the application is using authentication and encryption, since the context engine ID is used in the key creation process.</span></span> <span data-ttu-id="3c32e-302">그러지 않으면 NetX Duo SNMP는 *nxd_snmp.c* 맨 위에 기본 컨텍스트 엔진 ID를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-302">If not, NetX Duo SNMP provides a default context engine id at the top of *nxd_snmp.c:*</span></span>

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a><span data-ttu-id="3c32e-303">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-303">Input Parameters</span></span>

- <span data-ttu-id="3c32e-304">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-304">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-305">**context_engine** 컨텍스트 엔진 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-305">**context_engine** Pointer to the context engine string.</span></span>
- <span data-ttu-id="3c32e-306">**context_engine_size** 컨텍스트 엔진 문자열의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-306">**context_engine_size** Size of context engine string.</span></span> <span data-ttu-id="3c32e-307">컨텍스트 엔진의 최대 바이트 수는 NX_SNMP_MAX_CONTEXT_STRING으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-307">Note that the maximum number of bytes in a context engine is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-308">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-308">Return Values</span></span>

- <span data-ttu-id="3c32e-309">**NX_SUCCESS**(0X00) 성공적인 SNMP 컨텍스트 엔진 세트입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-309">**NX_SUCCESS** (0x00) Successful SNMP context engine set.</span></span>
- <span data-ttu-id="3c32e-310">**NX_NOT_ENABLED**(0x14) SNMPv3가 사용하도록 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-310">**NX_NOT_ENABLED** (0x14) SNMPv3 is not enabled</span></span>
- <span data-ttu-id="3c32e-311">**NX_SNMP_ERROR**(0X100) 컨텍스트 엔진 크기 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-311">**NX_SNMP_ERROR** (0x100) Context engine size error.</span></span>
- <span data-ttu-id="3c32e-312">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-312">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-313">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-313">Allowed From</span></span>

<span data-ttu-id="3c32e-314">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-314">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-315">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-315">Example</span></span>

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a><span data-ttu-id="3c32e-316">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-316">nx_snmp_agent_context_name_set</span></span>
<span data-ttu-id="3c32e-317">컨텍스트 이름 설정(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-317">Set context name (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-318">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-318">Prototype</span></span>

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a><span data-ttu-id="3c32e-319">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-319">Description</span></span>

<span data-ttu-id="3c32e-320">이 서비스는 SNMP 에이전트의 컨텍스트 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-320">This service sets the context name of the SNMP Agent.</span></span> <span data-ttu-id="3c32e-321">SNMPv3 처리에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-321">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="3c32e-322">호출하지 않으면 NetX Duo SNMP 에이전트는 컨텍스트 이름을 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-322">If not called, NetX Duo SNMP Agent will leave the context name blank.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-323">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-323">Input Parameters</span></span>

- <span data-ttu-id="3c32e-324">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-324">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-325">**context_name** 컨텍스트 이름 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-325">**context_name** Pointer to the context name string.</span></span>
- <span data-ttu-id="3c32e-326">**context_name_size** 컨텍스트 이름 문자열의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-326">**context_name_size** Size of context name string.</span></span> <span data-ttu-id="3c32e-327">컨텍스트 이름의 최대 바이트 수는 NX_SNMP_MAX_CONTEXT_STRING으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-327">Note that the maximum number of bytes in a context name is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-328">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-328">Return Values</span></span>

- <span data-ttu-id="3c32e-329">**NX_SUCCESS**(0X00) 성공적인 SNMP 컨텍스트 이름 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-329">**NX_SUCCESS** (0x00) Successful SNMP context name set.</span></span>
- <span data-ttu-id="3c32e-330">**NX_SNMP_ERROR**(0X100) 컨텍스트 이름 크기 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-330">**NX_SNMP_ERROR** (0x100) Context name size error.</span></span>
- <span data-ttu-id="3c32e-331">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-331">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-332">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-332">Allowed From</span></span>

<span data-ttu-id="3c32e-333">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-333">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-334">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-334">Example</span></span>

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a><span data-ttu-id="3c32e-335">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="3c32e-335">nx_snmp_agent_create</span></span>
<span data-ttu-id="3c32e-336">SNMP 에이전트 만들기</span><span class="sxs-lookup"><span data-stu-id="3c32e-336">Create SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-337">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-337">Prototype</span></span>

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a><span data-ttu-id="3c32e-338">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-338">Description</span></span>

<span data-ttu-id="3c32e-339">이 서비스는 지정된 IP 인스턴스에 SNMP 에이전트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-339">This service creates a SNMP Agent on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-340">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-340">Input Parameters</span></span>

- <span data-ttu-id="3c32e-341">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-341">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-342">**snmp_agent_name** SNMP 에이전트 이름 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-342">**snmp_agent_name** Pointer to the SNMP Agent name string.</span></span>
- <span data-ttu-id="3c32e-343">**ip_ptr** IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-343">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="3c32e-344">**stack_ptr** SNMP 에이전트 스레드 스택 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-344">**stack_ptr** Pointer to SNMP Agent thread stack pointer.</span></span>
- <span data-ttu-id="3c32e-345">**stack_size** 스택 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-345">**stack_size** Stack size in bytes.</span></span>
- <span data-ttu-id="3c32e-346">**pool_ptr** 이 SNMP 에이전트의 기본 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-346">**pool_ptr** Pointer the default packet pool for this SNMP Agent.</span></span>
- <span data-ttu-id="3c32e-347">**snmp_agent_username_process** 애플리케이션의 사용자 이름 처리 루틴에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-347">**snmp_agent_username_process** Function pointer to application’s username handling routine.</span></span>
- <span data-ttu-id="3c32e-348">**snmp_agent_get_process** 애플리케이션의 GET 요청 처리 루틴에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-348">**snmp_agent_get_process** Function pointer to application’s GET request handling routine.</span></span>
- <span data-ttu-id="3c32e-349">**snmp_agent_getnext_process** 애플리케이션의 GETNEXT 요청 처리 루틴에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-349">**snmp_agent_getnext_process** Function pointer to application’s GETNEXT request handling routine.</span></span>
- <span data-ttu-id="3c32e-350">**snmp_agent_set_process** 애플리케이션의 SET 요청 처리 루틴에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-350">**snmp_agent_set_process** Function pointer to application’s SET request handling routine.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-351">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-351">Return Values</span></span>

- <span data-ttu-id="3c32e-352">**NX_SUCCESS**(0x00) 성공적인 SNMP 에이전트 만들기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-352">**NX_SUCCESS** (0x00) Successful SNMP Agent create.</span></span>
- <span data-ttu-id="3c32e-353">**NX_SNMP_ERROR**(0X100) SNMP 에이전트 만들기 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-353">**NX_SNMP_ERROR** (0x100) SNMP Agent create error.</span></span>
- <span data-ttu-id="3c32e-354">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-354">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-355">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-355">Allowed From</span></span>

<span data-ttu-id="3c32e-356">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-356">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-357">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-357">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a><span data-ttu-id="3c32e-358">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-358">nx_snmp_agent_current_version_get</span></span>
<span data-ttu-id="3c32e-359">SNMP 패킷 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-359">Get the SNMP packet version</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-360">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-360">Prototype</span></span>

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a><span data-ttu-id="3c32e-361">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-361">Description</span></span>

<span data-ttu-id="3c32e-362">이 서비스는 가장 최근에 받은 SNMP 패킷에서 구문 분석된 SNMP 버전을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-362">This service retrieves the SNMP version parsed from the most recent SNMP packet received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-363">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-363">Input Parameters</span></span>

- <span data-ttu-id="3c32e-364">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-364">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-365">**version** 수신된 SNMP 패킷에서 구문 분석된 SNMP 버전에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-365">**version** Pointer to the SNMP version parsed from received SNMP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-366">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-366">Return Values</span></span>

- <span data-ttu-id="3c32e-367">**NX_SUCCESS**(0x00) 성공적인 SNMP 버전 가져오기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-367">**NX_SUCCESS** (0x00) Successful SNMP version get</span></span>
- <span data-ttu-id="3c32e-368">**NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-368">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-369">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-369">Allowed From</span></span>

<span data-ttu-id="3c32e-370">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-370">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-371">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-371">Example</span></span>

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a><span data-ttu-id="3c32e-372">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="3c32e-372">nx_snmp_agent_private_string_test</span></span>
<span data-ttu-id="3c32e-373">프라이빗 문자열이 에이전트 프라이빗 문자열과 일치하는지 확인</span><span class="sxs-lookup"><span data-stu-id="3c32e-373">Verify private string matches Agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-374">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-374">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a><span data-ttu-id="3c32e-375">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-375">Description</span></span>

<span data-ttu-id="3c32e-376">이 서비스는 null 종료 입력 커뮤니티 문자열과 SNMP 에이전트 프라이빗 문자열을 비교하고 일치하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-376">This service compares the null terminated input community string with the SNMP agent private string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-377">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-377">Input Parameters</span></span>

- <span data-ttu-id="3c32e-378">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-378">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-379">**community_string** 비교할 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-379">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="3c32e-380">**is_private** 비교 결과에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-380">**is_private** Pointer to result of comparison</span></span>  
<span data-ttu-id="3c32e-381">NX_TRUE - 문자열 일치</span><span class="sxs-lookup"><span data-stu-id="3c32e-381">NX_TRUE - string matches</span></span>  
<span data-ttu-id="3c32e-382">NX_FALSE - 문자열이 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="3c32e-382">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-383">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-383">Return Values</span></span>

- <span data-ttu-id="3c32e-384">**NX_SUCCESS**(0x00) 비교 성공</span><span class="sxs-lookup"><span data-stu-id="3c32e-384">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="3c32e-385">**NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-385">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-386">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-386">Allowed From</span></span>

<span data-ttu-id="3c32e-387">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-388">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-388">Example</span></span>

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a><span data-ttu-id="3c32e-389">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="3c32e-389">nx_snmp_agent_public_string_test</span></span>
<span data-ttu-id="3c32e-390">수신되는 퍼블릭 문자열이 에이전트의 퍼블릭 문자열과 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-390">Verify received public string matches Agent’s public string</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-391">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-391">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a><span data-ttu-id="3c32e-392">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-392">Description</span></span>

<span data-ttu-id="3c32e-393">이 서비스는 null 종료 입력 커뮤니티 문자열과 SNMP 에이전트 퍼블릭 문자열을 비교하고 일치하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-393">This service compares a null terminated input community string with the SNMP agent public string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-394">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-394">Input Parameters</span></span>

- <span data-ttu-id="3c32e-395">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-395">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-396">**community_string** 비교할 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-396">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="3c32e-397">**is_public** 비교 결과에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-397">**is_public** Pointer to result of comparison</span></span>  
<span data-ttu-id="3c32e-398">NX_TRUE - 문자열 일치</span><span class="sxs-lookup"><span data-stu-id="3c32e-398">NX_TRUE - string matches</span></span>  
<span data-ttu-id="3c32e-399">NX_FALSE - 문자열이 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="3c32e-399">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-400">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-400">Return Values</span></span>

- <span data-ttu-id="3c32e-401">**NX_SUCCESS**(0x00) 비교 성공</span><span class="sxs-lookup"><span data-stu-id="3c32e-401">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="3c32e-402">**NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-402">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-403">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-403">Allowed From</span></span>

<span data-ttu-id="3c32e-404">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-405">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-405">Example</span></span>

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a><span data-ttu-id="3c32e-406">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-406">nx_snmp_agent_version_set</span></span>
<span data-ttu-id="3c32e-407">각 SNMP 버전의 SNMP 에이전트 상태 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-407">Set the SNMP agent status for each SNMP version</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-408">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-408">Prototype</span></span>

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a><span data-ttu-id="3c32e-409">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-409">Description</span></span>

<span data-ttu-id="3c32e-410">이 서비스는 SNMP 에이전트의 각 SNMP 버전인 V1, V2 및 V3에 대해 상태(사용/사용 안 함)를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-410">This service sets the status (enabled/disabled) for each of the SNMP versions, V1, V2 and V3 on the SNMP agent.</span></span> <span data-ttu-id="3c32e-411">사용자 구성 가능 옵션, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 및 NX_SNMP_DISABLE_V3는 이러한 런타임 설정을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-411">Note that the user configurable options, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2, and NX_SNMP_DISABLE_V3, will override these run time settings.</span></span> <span data-ttu-id="3c32e-412">기본적으로 SNMP 에이전트는 세 가지 버전 모두에 대해 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-412">By default, the SNMP agent is enabled for all three versions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-413">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-413">Input Parameters</span></span>

- <span data-ttu-id="3c32e-414">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-414">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-415">**enabled_v1** SNMP V1에 대한 enabled 상태를 on/off로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-415">**enabled_v1** Sets enabled status for SNMP V1 to on/off.</span></span>
- <span data-ttu-id="3c32e-416">**enabled_v2** SNMP V2에 대한 enabled 상태를 on/off로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-416">**enabled_v2** Sets enabled status for SNMP V2 to on/off.</span></span>
- <span data-ttu-id="3c32e-417">**enabled_v3** SNMP V3에 대한 enabled 상태를 on/off로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-417">**enabled_v3** Sets enabled status for SNMP V3 to on/off.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-418">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-418">Return Values</span></span>

- <span data-ttu-id="3c32e-419">**NX_SUCCESS**(0x00) 성공적인 SNMP 버전 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-419">**NX_SUCCESS** (0x00) Successful SNMP version set</span></span>
- <span data-ttu-id="3c32e-420">**NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-420">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-421">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-421">Allowed From</span></span>

<span data-ttu-id="3c32e-422">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-422">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-423">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-423">Example</span></span>

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a><span data-ttu-id="3c32e-424">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-424">nx_snmp_agent_private_string_set</span></span>
<span data-ttu-id="3c32e-425">SNMP 에이전트 프라이빗 문자열 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-425">Set the SNMP agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-426">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-426">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="3c32e-427">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-427">Description</span></span>

<span data-ttu-id="3c32e-428">이 서비스는 입력 null 종료 문자열을 사용하여 SNMP 에이전트 프라이빗 커뮤니티 문자열을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-428">This service sets the SNMP agent private community string with the input null terminated string.</span></span> <span data-ttu-id="3c32e-429">기본값은 NULL(프라이빗 문자열이 설정되지 않음)이며, 이 경우 "프라이빗" 커뮤니티 문자열과 함께 수신된 모든 SNMP 패킷이 읽기/쓰기 액세스를 위해 SNMP 에이전트에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-429">The default value is NULL (no private string set), such that any SNMP packet received with a “private” community string will not be accepted by the SNMP agent for read/write access.</span></span> <span data-ttu-id="3c32e-430">입력 문자열은 사용자가 구성할 수 있는 NX_SNMP_MAX_USER_NAME(null 종료를 위한 공간 허용) 크기보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-430">The input string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-431">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-431">Input Parameters</span></span>

- <span data-ttu-id="3c32e-432">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-432">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-433">**community_string** 할당할 프라이빗 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-433">**community_string** Pointer to the private string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-434">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-434">Return Values</span></span>

- <span data-ttu-id="3c32e-435">**NX_SUCCESS**(0x00) 프라이빗 문자열을 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-435">**NX_SUCCESS** (0x00) Successfully set private string</span></span>
- <span data-ttu-id="3c32e-436">**NX_SNMP_ERROR_TOOBIG**(0X01) 문자열 크기가 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-436">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span> 
- <span data-ttu-id="3c32e-437">**NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-437">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-438">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-438">Allowed From</span></span>

<span data-ttu-id="3c32e-439">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-439">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-440">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-440">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a><span data-ttu-id="3c32e-441">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-441">nx_snmp_agent_public_string_set</span></span>
<span data-ttu-id="3c32e-442">SNMP 에이전트 퍼블릭 문자열 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-442">Set the SNMP agent public string</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-443">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-443">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="3c32e-444">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-444">Description</span></span>

<span data-ttu-id="3c32e-445">이 서비스는 입력 null 종료 문자열을 사용하여 SNMP 에이전트 퍼블릭 커뮤니티 문자열을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-445">This service sets the SNMP agent public community string with the input null terminated string.</span></span> <span data-ttu-id="3c32e-446">커뮤니티 문자열은 사용자가 구성할 수 있는 NX_SNMP_MAX_USER_NAME(null 종료를 위한 공간 허용) 크기보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-446">The community string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-447">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-447">Input Parameters</span></span>

- <span data-ttu-id="3c32e-448">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-448">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-449">**community_string** 할당할 퍼블릭 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-449">**community_string** Pointer to the public string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-450">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-450">Return Values</span></span>

- <span data-ttu-id="3c32e-451">**NX_SUCCESS**(0x00) 퍼블릭 문자열을 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-451">**NX_SUCCESS** (0x00) Successfully set public string</span></span>
- <span data-ttu-id="3c32e-452">**NX_SNMP_ERROR_TOOBIG**(0X01) 문자열 크기가 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-452">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span>
- <span data-ttu-id="3c32e-453">**NX_PTR_ERROR**(0x07) 포인터 입력이 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-453">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-454">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-454">Allowed From</span></span>

<span data-ttu-id="3c32e-455">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-456">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-456">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a><span data-ttu-id="3c32e-457">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="3c32e-457">nx_snmp_agent_delete</span></span>
<span data-ttu-id="3c32e-458">SNMP 에이전트 삭제</span><span class="sxs-lookup"><span data-stu-id="3c32e-458">Delete SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-459">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-459">Prototype</span></span>

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="3c32e-460">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-460">Description</span></span>

<span data-ttu-id="3c32e-461">이 서비스는 이전에 만든 SNMP 에이전트를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-461">This service deletes a previously created SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-462">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-462">Input Parameters</span></span>

- <span data-ttu-id="3c32e-463">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-463">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-464">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-464">Return Values</span></span>

- <span data-ttu-id="3c32e-465">**NX_SUCCESS**(0x00) 성공적인 SNMP 에이전트 삭제입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-465">**NX_SUCCESS** (0x00) Successful SNMP Agent delete.</span></span>
- <span data-ttu-id="3c32e-466">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-466">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-467">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-467">Allowed From</span></span>

<span data-ttu-id="3c32e-468">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-468">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-469">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-469">Example</span></span>

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a><span data-ttu-id="3c32e-470">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="3c32e-470">nx_snmp_agent_set_interface</span></span>
<span data-ttu-id="3c32e-471">SNMP 에이전트 네트워크 인터페이스 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-471">Set the SNMP agent network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-472">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-472">Prototype</span></span>

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a><span data-ttu-id="3c32e-473">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-473">Description</span></span>

<span data-ttu-id="3c32e-474">이 서비스는 입력 인터페이스 인덱스로 지정된 SNMP 에이전트의 SNMP 네트워크 인터페이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-474">This service sets the SNMP network interface for the SNMP Agent as specified by the input interface index.</span></span> <span data-ttu-id="3c32e-475">여러 네트워크 인터페이스를 지원하는 NetX Duo 5.6 이상인 SNMP 호스트 애플리케이션에만 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-475">This is only useful for SNMP host applications with NetX Duo 5.6 or higher which support multiple network interfaces.</span></span> <span data-ttu-id="3c32e-476">기본 인터페이스에 대해 호스트에서 지정하지 않은 경우 기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-476">The default value if not specified by the host is zero, for the primary interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-477">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-477">Input Parameters</span></span>

- <span data-ttu-id="3c32e-478">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-478">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-479">**If_index** SNMP 인터페이스를 지정하는 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-479">**If_index** Index specifying the SNMP interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-480">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-480">Return Values</span></span>

- <span data-ttu-id="3c32e-481">**NX_SUCCESS**(0x00) 성공적인 SNMP 인터페이스 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-481">**NX_SUCCESS** (0x00) Successful SNMP interface set.</span></span>
- <span data-ttu-id="3c32e-482">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-482">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-483">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-483">Allowed From</span></span>

<span data-ttu-id="3c32e-484">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-484">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-485">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-485">Example</span></span>

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a><span data-ttu-id="3c32e-486">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="3c32e-486">nx_snmp_agent_md5_key_create</span></span>
<span data-ttu-id="3c32e-487">md5 키 만들기(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-487">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-488">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-488">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a><span data-ttu-id="3c32e-489">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-489">Description</span></span>

<span data-ttu-id="3c32e-490">이 서비스는 인증 및 암호화에 사용할 수 있는 MD5 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-490">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="3c32e-491">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-491">This service is deprecated.</span></span> <span data-ttu-id="3c32e-492">개발자는 nx_snmp_agent_md5_key_create_extended()로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-492">Developers are encouraged to migrate to *nx_snmp_agent_md5_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-493">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-493">Input Parameters</span></span>

- <span data-ttu-id="3c32e-494">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-494">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-495">**password** 암호 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-495">**password** Pointer to password string.</span></span>
- <span data-ttu-id="3c32e-496">**destination_key** SNMP 키 데이터 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-496">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-497">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-497">Return Values</span></span>

- <span data-ttu-id="3c32e-498">**NX_SUCCESS**(0x00) 성공적인 키 만들기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-498">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="3c32e-499">**NX_NOT_ENABLED**(0x14) 보안이 사용하지 않도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-499">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="3c32e-500">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-500">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-501">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-501">Allowed From</span></span>

<span data-ttu-id="3c32e-502">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-502">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-503">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-503">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a><span data-ttu-id="3c32e-504">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="3c32e-504">nx_snmp_agent_md5_key_create_extended</span></span>
<span data-ttu-id="3c32e-505">md5 키 만들기(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-505">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-506">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-506">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="3c32e-507">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-507">Description</span></span>

<span data-ttu-id="3c32e-508">이 서비스는 인증 및 암호화에 사용할 수 있는 MD5 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-508">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="3c32e-509">이 서비스는 nx_snmp_agent_md5_key_create()를 대신합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-509">This service replaces *nx_snmp_agent_md5_key_create().*</span></span> <span data-ttu-id="3c32e-510">이 버전을 사용하려면 호출자가 암호 길이를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-510">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-511">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-511">Input Parameters</span></span>

- <span data-ttu-id="3c32e-512">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-512">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-513">**password** 암호 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-513">**password** Pointer to password string.</span></span>
- <span data-ttu-id="3c32e-514">**password_length** 암호 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-514">**password_length** Length of password string.</span></span>
- <span data-ttu-id="3c32e-515">**destination_key** SNMP 키 데이터 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-515">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-516">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-516">Return Values</span></span>

- <span data-ttu-id="3c32e-517">**NX_SUCCESS**(0x00) 성공적인 키 만들기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-517">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="3c32e-518">**NX_NOT_ENABLED**(0x14) 보안이 사용하지 않도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-518">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="3c32e-519">**NX_SNMP_FAILED**(0x102) SNMP가 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-519">**NX_SNMP_FAILED** (0x102) SNMP failed.</span></span>
- <span data-ttu-id="3c32e-520">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-520">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-521">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-521">Allowed From</span></span>

<span data-ttu-id="3c32e-522">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-522">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-523">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-523">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a><span data-ttu-id="3c32e-524">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="3c32e-524">nx_snmp_agent_priv_trap_key_use</span></span>
<span data-ttu-id="3c32e-525">트랩 메시지의 암호화 키 지정</span><span class="sxs-lookup"><span data-stu-id="3c32e-525">Specify encryption key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-526">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-526">Prototype</span></span>

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a><span data-ttu-id="3c32e-527">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-527">Description</span></span>

<span data-ttu-id="3c32e-528">이 서비스는 이전에 만든 프라이빗 키를 SNMPv3 트랩 메시지의 암호화 및 암호 해독에 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-528">This service specifies that a previously created privacy key is to be used for encryption and decryption of SNMPv3 trap messages.</span></span>

> [!NOTE]
> <span data-ttu-id="3c32e-529">이전에 인증 키를 만들어야 합니다. SNMP v3 개인 정보 보호(암호화)를 사용하려면 인증이 필요합니다. 자세한 내용은 nx_snmp_agent_auth_trap_key_use를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c32e-529">*An authentictation key must be previously created. SNMP v3 privacy (encryption) requires authentication. See nx_snmp_agent_auth_trap_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-530">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-530">Input Parameters</span></span>

- <span data-ttu-id="3c32e-531">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-531">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-532">**key** 이전에 키를 만들기 위한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-532">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-533">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-533">Return Values</span></span>

- <span data-ttu-id="3c32e-534">**NX_SUCCESS**(0X00) 성공적인 프라이빗 키 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-534">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="3c32e-535">**NX_NOT_ENABLED**(0x14) 보안이 사용하지 않도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-535">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="3c32e-536">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-536">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-537">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-537">Allowed From</span></span>

<span data-ttu-id="3c32e-538">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-538">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-539">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-539">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a><span data-ttu-id="3c32e-540">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="3c32e-540">nx_snmp_agent_privacy_key_use</span></span>
<span data-ttu-id="3c32e-541">응답 메시지에 대한 암호화 키 지정</span><span class="sxs-lookup"><span data-stu-id="3c32e-541">Specify encryption key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-542">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-542">Prototype</span></span>

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="3c32e-543">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-543">Description</span></span>

<span data-ttu-id="3c32e-544">이 서비스는 이전에 만든 키를 SNMPv3 응답 메시지의 암호화 및 암호 해독에 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-544">This service specifies that the previously created key is to be used for encryption and decryption of SNMPv3 response messages.</span></span>

> [!NOTE]
> <span data-ttu-id="3c32e-545">이전에 인증 키를 지정했어야 합니다. SNMP v3 암호화를 위해서는 인증 키도 만들어야 합니다. 자세한 내용은 nx_snmp_agent_authentiation_key_use를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c32e-545">*An authentication key must have previously been specified. SNMP v3 encryption requires creation of an authentication key as well. See nx_snmp_agent_authentiation_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-546">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-546">Input Parameters</span></span>

- <span data-ttu-id="3c32e-547">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-547">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-548">**key** 이전에 키를 만들기 위한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-548">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-549">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-549">Return Values</span></span>

- <span data-ttu-id="3c32e-550">**NX_SUCCESS**(0X00) 성공적인 프라이빗 키 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-550">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="3c32e-551">**NX_NOT_ENABLED**(0x14) 보안이 사용하지 않도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-551">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="3c32e-552">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-552">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-553">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-553">Allowed From</span></span>

<span data-ttu-id="3c32e-554">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-554">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-555">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-555">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a><span data-ttu-id="3c32e-556">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="3c32e-556">nx_snmp_agent_sha_key_create</span></span>
<span data-ttu-id="3c32e-557">SHA 키 만들기(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-557">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-558">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-558">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a><span data-ttu-id="3c32e-559">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-559">Description</span></span>

<span data-ttu-id="3c32e-560">이 서비스는 인증 및 암호화에 사용할 수 있는 SHA 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-560">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="3c32e-561">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-561">This service is deprecated.</span></span> <span data-ttu-id="3c32e-562">개발자는 nx_snmp_agent_sha_key_create_extended()로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-562">Developers are encouraged to migrate to *nx_snmp_agent_sha_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-563">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-563">Input Parameters</span></span>

- <span data-ttu-id="3c32e-564">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-564">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-565">**password** 암호 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-565">**password** Pointer to password string.</span></span>
- <span data-ttu-id="3c32e-566">**destination_key** SNMP 키 데이터 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-566">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-567">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-567">Return Values</span></span>

- <span data-ttu-id="3c32e-568">**NX_SUCCESS**(0x00) 성공적인 키 만들기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-568">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="3c32e-569">**NX_SNMP_ERROR**(0x100) 키 만들기 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-569">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="3c32e-570">**NX_PTR_ERROR**(0X07) 잘못된 SNMP 에이전트 또는 키 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-570">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-571">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-571">Allowed From</span></span>

<span data-ttu-id="3c32e-572">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-572">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-573">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-573">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a><span data-ttu-id="3c32e-574">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="3c32e-574">nx_snmp_agent_sha_key_create_extended</span></span>
<span data-ttu-id="3c32e-575">SHA 키 만들기(SNMP v3만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-575">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-576">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-576">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="3c32e-577">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-577">Description</span></span>

<span data-ttu-id="3c32e-578">이 서비스는 인증 및 암호화에 사용할 수 있는 SHA 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-578">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="3c32e-579">이 서비스는 nx_snmp_agent_sha_key_create()를 대신합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-579">This service replaces *nx_snmp_agent_sha_key_create().*</span></span> <span data-ttu-id="3c32e-580">이 버전을 사용하려면 호출자가 암호 길이를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-580">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-581">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-581">Input Parameters</span></span>

- <span data-ttu-id="3c32e-582">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-582">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-583">**password** 암호 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-583">**password** Pointer to password string.</span></span>
- <span data-ttu-id="3c32e-584">**password_length** 암호 문자열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-584">**password_length** Length of password string.</span></span>
- <span data-ttu-id="3c32e-585">**destination_key** SNMP 키 데이터 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-585">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-586">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-586">Return Values</span></span>

- <span data-ttu-id="3c32e-587">**NX_SUCCESS**(0x00) 성공적인 키 만들기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-587">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="3c32e-588">**NX_SNMP_ERROR**(0x100) 키 만들기 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-588">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="3c32e-589">**NX_SNMP_FAILED**(0x102) 키를 만들지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-589">**NX_SNMP_FAILED** (0x102) Key create failed.</span></span>
- <span data-ttu-id="3c32e-590">**NX_PTR_ERROR**(0X07) 잘못된 SNMP 에이전트 또는 키 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-590">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-591">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-591">Allowed From</span></span>

<span data-ttu-id="3c32e-592">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-592">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-593">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-593">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a><span data-ttu-id="3c32e-594">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="3c32e-594">nx_snmp_agent_start</span></span>
<span data-ttu-id="3c32e-595">SNMP 에이전트 시작</span><span class="sxs-lookup"><span data-stu-id="3c32e-595">Start SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-596">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-596">Prototype</span></span>

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="3c32e-597">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-597">Description</span></span>

<span data-ttu-id="3c32e-598">이 서비스는 UDP 소켓을 SNMP 포트 161에 바인딩하고 SNMP 에이전트 스레드 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-598">This service binds the UDP socket to the SNMP port 161 and starts the SNMP Agent thread task.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-599">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-599">Input Parameters</span></span>

- <span data-ttu-id="3c32e-600">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-600">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-601">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-601">Return Values</span></span>

- <span data-ttu-id="3c32e-602">**NX_SUCCESS**(0x00) SNMP 에이전트를 성공적으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-602">**NX_SUCCESS** (0x00) Successful start of SNMP Agent.</span></span>
- <span data-ttu-id="3c32e-603">**NX_SNMP_ERROR**(0X100) SNMP 에이전트 시작 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-603">**NX_SNMP_ERROR** (0x100) SNMP Agent start error.</span></span>
- <span data-ttu-id="3c32e-604">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-604">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-605">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-605">Allowed From</span></span>

<span data-ttu-id="3c32e-606">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-606">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-607">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-607">Example</span></span>

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a><span data-ttu-id="3c32e-608">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="3c32e-608">nx_snmp_agent_stop</span></span>
<span data-ttu-id="3c32e-609">SNMP 에이전트 중지</span><span class="sxs-lookup"><span data-stu-id="3c32e-609">Stop SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-610">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-610">Prototype</span></span>

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="3c32e-611">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-611">Description</span></span>

<span data-ttu-id="3c32e-612">이 서비스는 SNMP 에이전트 스레드 작업을 중지하고 SNMP 포트에 대한 UDP 소켓 바인딩을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-612">This service stops the SNMP Agent thread task and unbinds the UDP socket to the SNMP port.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-613">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-613">Input Parameters</span></span>

- <span data-ttu-id="3c32e-614">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-614">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-615">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-615">Return Values</span></span>

- <span data-ttu-id="3c32e-616">**NX_SUCCESS**(0x00) SNMP 에이전트를 성공적으로 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-616">**NX_SUCCESS** (0x00) Successful stop of SNMP Agent.</span></span>
- <span data-ttu-id="3c32e-617">**NX_PTR_ERROR**(0X07) 잘못된 SNMP 에이전트 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-617">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-618">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-618">Allowed From</span></span>

<span data-ttu-id="3c32e-619">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-619">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-620">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-620">Example</span></span>

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a><span data-ttu-id="3c32e-621">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-621">nx_snmp_agent_trap_send</span></span>
<span data-ttu-id="3c32e-622">SNMPv1 트랩 보내기(IPv4만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-622">Send SNMPv1 trap *(IPv4 only)*</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-623">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-623">Prototype</span></span>

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="3c32e-624">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-624">Description</span></span>

<span data-ttu-id="3c32e-625">이 서비스는 SNMP 트랩을 지정된 IPv4 주소의 SNMP 관리자로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-625">This service sends an SNMP trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="3c32e-626">NetX Duo에서 SNMP 트랩을 전송하는 기본 방법은 nxd_snmp_agent_trap_send 서비스를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-626">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trap_send* service.</span></span> <span data-ttu-id="3c32e-627">기존 NetX SNMP 에이전트 애플리케이션을 지원하기 위해 nx_snmp_agent_trap_send가 NetX Duo에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-627">*nx_snmp_agent_trap_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-628">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-628">Input Parameters</span></span>

- <span data-ttu-id="3c32e-629">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-629">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-630">**ip_address** SNMP 관리자의 IPv4 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-630">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="3c32e-631">**enterprise** 엔터프라이즈 개체 ID 문자열(sysObectID)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-631">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="3c32e-632">**trap_type** 다음과 같은 요청된 트랩의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-632">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="3c32e-633">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="3c32e-633">NX_SNMP_TRAP_COLDSTART (0)</span></span>  
   - <span data-ttu-id="3c32e-634">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="3c32e-634">NX_SNMP_TRAP_WARMSTART (1)</span></span>  
   - <span data-ttu-id="3c32e-635">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="3c32e-635">NX_SNMP_TRAP_LINKDOWN (2)</span></span>  
   - <span data-ttu-id="3c32e-636">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="3c32e-636">NX_SNMP_TRAP_LINKUP (3)</span></span>  
   - <span data-ttu-id="3c32e-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="3c32e-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>  
   - <span data-ttu-id="3c32e-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="3c32e-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  

- <span data-ttu-id="3c32e-639">**trap_code** 트랩 코드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-639">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="3c32e-640">**elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="3c32e-640">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="3c32e-641">**object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-641">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="3c32e-642">목록은 NX_NULL 로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-642">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-643">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-643">Return Values</span></span>

- <span data-ttu-id="3c32e-644">**NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-644">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="3c32e-645">**NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-645">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="3c32e-646">**NX_NOT_ENABLED**(0x14) SNMPv1이 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-646">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="3c32e-647">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-647">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-648">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-648">Allowed From</span></span>

<span data-ttu-id="3c32e-649">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-650">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-650">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a><span data-ttu-id="3c32e-651">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-651">nxd_snmp_agent_trap_send</span></span>
<span data-ttu-id="3c32e-652">SNMPv1 트랩 보내기(IPv4 및 IPv6)</span><span class="sxs-lookup"><span data-stu-id="3c32e-652">Send SNMPv1 trap *(IPv4 and IPv6)*</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-653">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-653">Prototype</span></span>

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="3c32e-654">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-654">Description</span></span>

<span data-ttu-id="3c32e-655">이 서비스는 SNMP 트랩을 지정된 IP 주소의 SNMP 관리자로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-655">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="3c32e-656">NetX에서 SNMP 트랩을 전송하는 것과 동일한 방법은 nxd_snmp_agent_trap_send 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-656">The equivalent method for sending an SNMP trap in NetX is the *nxd_snmp_agent_trap_send* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-657">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-657">Input Parameters</span></span>

- <span data-ttu-id="3c32e-658">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-658">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-659">**ip_address** SNMP 관리자의 IPv4 또는 IPv6 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-659">**ip_address** IPv4 or IPv6 address of the SNMP Manager.</span></span>
- <span data-ttu-id="3c32e-660">**enterprise** 엔터프라이즈 개체 ID 문자열(sysObectID)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-660">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="3c32e-661">**trap_type** 다음과 같은 요청된 트랩의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-661">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="3c32e-662">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="3c32e-662">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="3c32e-663">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="3c32e-663">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="3c32e-664">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="3c32e-664">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="3c32e-665">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="3c32e-665">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="3c32e-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="3c32e-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="3c32e-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="3c32e-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

- <span data-ttu-id="3c32e-668">**trap_code** 트랩 코드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-668">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="3c32e-669">**elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="3c32e-669">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="3c32e-670">**object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-670">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="3c32e-671">목록은 NX_NULL 로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-671">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-672">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-672">Return Values</span></span>

- <span data-ttu-id="3c32e-673">**NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-673">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="3c32e-674">**NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-674">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="3c32e-675">**NX_NOT_ENABLED**(0x14) SNMPv1이 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-675">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="3c32e-676">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-676">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-677">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-677">Allowed From</span></span>

<span data-ttu-id="3c32e-678">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-678">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-679">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-679">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a><span data-ttu-id="3c32e-680">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-680">nx_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="3c32e-681">SNMPv2 트랩 보내기(IPv4만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-681">Send SNMPv2 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-682">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-682">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="3c32e-683">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-683">Description</span></span>

<span data-ttu-id="3c32e-684">이 서비스는 SNMPv2 트랩을 지정된 IPv4 주소의 SNMP 관리자로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-684">This service sends an SNMPv2 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="3c32e-685">NetX Duo에서 SNMP 트랩을 전송하는 기본 방법은 nxd_snmp_agent_trapv2_send 서비스를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-685">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv2_send* service.</span></span> <span data-ttu-id="3c32e-686">기존 NetX SNMP 에이전트 애플리케이션을 지원하기 위해 nx_snmp_agent_trapv2_send가 NetX Duo에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-686">*nx_snmp_agent_trapv2_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-687">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-687">Input Parameters</span></span>

- <span data-ttu-id="3c32e-688">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-688">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-689">**ip_address** SNMP 관리자의 IPv4 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-689">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="3c32e-690">**community** 커뮤니티 이름(사용자 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-690">**community** Community name (username).</span></span>
- <span data-ttu-id="3c32e-691">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="3c32e-691">**trap_type**</span></span>  
   <span data-ttu-id="3c32e-692">요청된 트랩의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-692">Type of trap requested.</span></span> <span data-ttu-id="3c32e-693">표준 이벤트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-693">The standard events are:</span></span>  
   - <span data-ttu-id="3c32e-694">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="3c32e-694">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="3c32e-695">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="3c32e-695">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="3c32e-696">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="3c32e-696">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="3c32e-697">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="3c32e-697">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="3c32e-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="3c32e-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="3c32e-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="3c32e-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="3c32e-700">소유 데이터의 경우:</span><span class="sxs-lookup"><span data-stu-id="3c32e-700">For proprietary data:</span></span>  
   - <span data-ttu-id="3c32e-701">NX_SNMP_TRAP_CUSTOM(0xFFFFFFFF)(nxd_snmp.h에 정의됨)</span><span class="sxs-lookup"><span data-stu-id="3c32e-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>
   
- <span data-ttu-id="3c32e-702">**elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="3c32e-702">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="3c32e-703">**object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-703">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="3c32e-704">목록은 NX_NULL 로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-704">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-705">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-705">Return Values</span></span>

- <span data-ttu-id="3c32e-706">**NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-706">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="3c32e-707">**NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-707">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="3c32e-708">**NX_NOT_ENABLED**(0x14) SNMPv2가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-708">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="3c32e-709">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-709">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-710">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-710">Allowed From</span></span>

<span data-ttu-id="3c32e-711">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-711">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-712">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-712">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="3c32e-713">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-713">nx_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="3c32e-714">OID를 직접 지정하는 SNMPv2 트랩 보내기</span><span class="sxs-lookup"><span data-stu-id="3c32e-714">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-715">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-715">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="3c32e-716">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-716">Description</span></span>

<span data-ttu-id="3c32e-717">이 서비스는 지정된 IP 주소(IPv4만 해당)에서 SNMP 관리자에 SNMPv2 트랩을 보내고 호출자가 OID를 직접 지정할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-717">This service sends an SNMPv2 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="3c32e-718">NetX Duo에서 지정된 OID를 사용하여 SNMP 트랩을 전송하는 기본 방법은 nxd_snmp_agent_trapv2_oid_send 서비스를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-718">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv2_oid_send* service.</span></span> <span data-ttu-id="3c32e-719">기존 NetX SNMP 에이전트 애플리케이션을 지원하기 위해 nx_snmp_agent_trapv2_oid_ send가 NetX Duo에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-719">*nx_snmp_agent_trapv2_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-720">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-720">Input Parameters</span></span>

- <span data-ttu-id="3c32e-721">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-721">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-722">**ip_address** SNMP 관리자의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-722">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="3c32e-723">**community** 커뮤니티 이름(사용자 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-723">**community** Community name (username).</span></span>
- <span data-ttu-id="3c32e-724">**oid** OID를 포함하는 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-724">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="3c32e-725">**elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="3c32e-725">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="3c32e-726">**object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-726">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="3c32e-727">목록은 NX_NULL 로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-727">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-728">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-728">Return Values</span></span>

- <span data-ttu-id="3c32e-729">**NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-729">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="3c32e-730">**NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-730">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="3c32e-731">**NX_PTR_ERROR**(0x16) 잘못된 SNMP 에이전트 또는 매개 변수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-731">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="3c32e-732">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-732">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="3c32e-733">**NX_OPTION_ERROR**(0x0A) 잘못된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-733">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-734">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-734">Allowed From</span></span>

<span data-ttu-id="3c32e-735">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-736">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-736">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a><span data-ttu-id="3c32e-737">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-737">nxd_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="3c32e-738">SNMPv2 트랩 보내기(IPv4 및 IPv6)</span><span class="sxs-lookup"><span data-stu-id="3c32e-738">Send SNMPv2 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-739">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-739">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="3c32e-740">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-740">Description</span></span>

<span data-ttu-id="3c32e-741">이 서비스는 지정된 IP 주소의 SNMP 관리자에 SNMP V2 트랩을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-741">This service sends an SNMP V2 trap to the SNMP Manager at the specified IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-742">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-742">Input Parameters</span></span>

- <span data-ttu-id="3c32e-743">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-743">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-744">**ip_address** SNMP 관리자의 IP(IPv4 또는 IPv6) 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-744">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="3c32e-745">**community** 커뮤니티 이름(사용자 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-745">**community** Community name (username).</span></span>
- <span data-ttu-id="3c32e-746">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="3c32e-746">**trap_type**</span></span>  
   <span data-ttu-id="3c32e-747">요청된 트랩의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-747">Type of trap requested.</span></span> <span data-ttu-id="3c32e-748">표준 이벤트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-748">The standard events are:</span></span>  
   - <span data-ttu-id="3c32e-749">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="3c32e-749">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="3c32e-750">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="3c32e-750">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="3c32e-751">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="3c32e-751">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="3c32e-752">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="3c32e-752">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="3c32e-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="3c32e-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="3c32e-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="3c32e-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="3c32e-755">소유 데이터의 경우:</span><span class="sxs-lookup"><span data-stu-id="3c32e-755">For proprietary data:</span></span>

   - <span data-ttu-id="3c32e-756">NX_SNMP_TRAP_CUSTOM(0xFFFFFFFF)(nxd_snmp.h에 정의됨)</span><span class="sxs-lookup"><span data-stu-id="3c32e-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="3c32e-757">**elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="3c32e-757">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="3c32e-758">**object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-758">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="3c32e-759">목록은 NX_NULL 로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-759">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-760">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-760">Return Values</span></span>

- <span data-ttu-id="3c32e-761">**NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-761">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="3c32e-762">**NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-762">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="3c32e-763">**NX_NOT_ENABLED**(0x14) SNMPv2가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-763">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="3c32e-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR**(0x104) 지원되지 않는 IP 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="3c32e-765">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-765">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-766">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-766">Allowed From</span></span>

<span data-ttu-id="3c32e-767">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-767">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-768">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-768">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="3c32e-769">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-769">nxd_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="3c32e-770">OID를 직접 지정하는 SNMPv2 트랩 보내기</span><span class="sxs-lookup"><span data-stu-id="3c32e-770">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-771">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-771">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="3c32e-772">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-772">Description</span></span>

<span data-ttu-id="3c32e-773">이 서비스는 지정된 IP 주소(IPv4/IPv6)의 SNMP 관리자에 SNMP v2 트랩을 보내고 호출자가 직접 OID를 지정할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-773">This service sends an SNMP v2 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-774">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-774">Input Parameters</span></span>

- <span data-ttu-id="3c32e-775">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-775">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-776">**ip_address** SNMP 관리자의 IP 주소입니다(IPv4/IPv6).</span><span class="sxs-lookup"><span data-stu-id="3c32e-776">**ip_address** IP address of SNMP Manager (IPv4/IPv6).</span></span>
- <span data-ttu-id="3c32e-777">**community** 커뮤니티 이름(사용자 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-777">**community** Community name (username).</span></span>
- <span data-ttu-id="3c32e-778">**oid** OID를 포함하는 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-778">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="3c32e-779">**elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="3c32e-779">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="3c32e-780">**object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-780">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="3c32e-781">목록은 NX_NULL 로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-781">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-782">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-782">Return Values</span></span>

- <span data-ttu-id="3c32e-783">**NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-783">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="3c32e-784">**NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-784">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="3c32e-785">**NX_PTR_ERROR**(0x16) 잘못된 SNMP 에이전트 또는 매개 변수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-785">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="3c32e-786">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-786">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="3c32e-787">**NX_OPTION_ERROR**(0x0A) 잘못된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-787">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-788">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-788">Allowed From</span></span>

<span data-ttu-id="3c32e-789">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-789">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-790">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-790">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a><span data-ttu-id="3c32e-791">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-791">nx_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="3c32e-792">SNMPv3 트랩 보내기(IPv4만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-792">Send SNMPv3 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-793">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-793">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="3c32e-794">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-794">Description</span></span>

<span data-ttu-id="3c32e-795">이 서비스는 SNMPv3 트랩을 지정된 IPv4 주소의 SNMP 관리자로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-795">This service sends an SNMPv3 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="3c32e-796">NetX Duo에서 SNMP 트랩을 전송하는 기본 방법은 nxd_snmp_agent_trapv3_send 서비스를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-796">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv3_send* service.</span></span> <span data-ttu-id="3c32e-797">기존 NetX SNMP 에이전트 애플리케이션을 지원하기 위해 nx_snmp_agent_trapv3_send가 NetX Duo에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-797">*nx_snmp_agent_trapv3_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-798">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-798">Input Parameters</span></span>

- <span data-ttu-id="3c32e-799">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-799">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-800">**ip_address** SNMP 관리자의 IPv4 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-800">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="3c32e-801">**username** 커뮤니티 이름(사용자 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-801">**username** Community name (username).</span></span>
- <span data-ttu-id="3c32e-802">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="3c32e-802">**trap_type**</span></span>  
   <span data-ttu-id="3c32e-803">요청된 트랩의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-803">Type of trap requested.</span></span> <span data-ttu-id="3c32e-804">표준 이벤트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-804">The standard events are:</span></span>  
   - <span data-ttu-id="3c32e-805">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="3c32e-805">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="3c32e-806">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="3c32e-806">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="3c32e-807">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="3c32e-807">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="3c32e-808">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="3c32e-808">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="3c32e-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="3c32e-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="3c32e-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="3c32e-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="3c32e-811">소유 데이터의 경우:</span><span class="sxs-lookup"><span data-stu-id="3c32e-811">For proprietary data:</span></span>
   - <span data-ttu-id="3c32e-812">NX_SNMP_TRAP_CUSTOM(0xFFFFFFFF)(nxd_snmp.h에 정의됨)</span><span class="sxs-lookup"><span data-stu-id="3c32e-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="3c32e-813">**elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="3c32e-813">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="3c32e-814">**object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-814">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="3c32e-815">목록은 NX_NULL 로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-815">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-816">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-816">Return Values</span></span>

- <span data-ttu-id="3c32e-817">**NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-817">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="3c32e-818">**NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-818">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="3c32e-819">**NX_NOT_ENABLED**(0x14) SNMPv3가 사용하도록 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-819">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="3c32e-820">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-820">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-821">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-821">Allowed From</span></span>

<span data-ttu-id="3c32e-822">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-822">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-823">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-823">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="3c32e-824">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-824">nx_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="3c32e-825">OID를 직접 지정하는 SNMPv3 트랩 보내기</span><span class="sxs-lookup"><span data-stu-id="3c32e-825">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-826">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-826">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="3c32e-827">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-827">Description</span></span>

<span data-ttu-id="3c32e-828">이 서비스는 지정된 IP 주소(IPv4만 해당)에서 SNMP 관리자에 SNMPv3 트랩을 보내고 호출자가 OID를 직접 지정할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-828">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="3c32e-829">NetX Duo에서 지정된 OID를 사용하여 SNMP 트랩을 전송하는 기본 방법은 nxd_snmp_agent_trapv3_oid_send 서비스를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-829">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv3_oid_send* service.</span></span> <span data-ttu-id="3c32e-830">기존 NetX SNMP 에이전트 애플리케이션을 지원하기 위해 nx_snmp_agent_trapv3_oid_ send가 NetX Duo에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-830">*nx_snmp_agent_trapv3_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-831">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-831">Input Parameters</span></span>

- <span data-ttu-id="3c32e-832">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-832">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-833">**ip_address** SNMP 관리자의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-833">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="3c32e-834">**username** 커뮤니티 이름(사용자 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-834">**username** Community name (username).</span></span>
- <span data-ttu-id="3c32e-835">**oid** OID를 포함하는 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-835">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="3c32e-836">**elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="3c32e-836">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="3c32e-837">**object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-837">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="3c32e-838">목록은 NX_NULL 로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-838">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-839">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-839">Return Values</span></span>

- <span data-ttu-id="3c32e-840">**NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-840">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="3c32e-841">**NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-841">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="3c32e-842">**NX_PTR_ERROR**(0x16) 잘못된 SNMP 에이전트 또는 매개 변수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-842">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="3c32e-843">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-843">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="3c32e-844">**NX_OPTION_ERROR**(0x0A) 잘못된 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-844">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-845">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-845">Allowed From</span></span>

<span data-ttu-id="3c32e-846">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-847">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-847">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a><span data-ttu-id="3c32e-848">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-848">nxd_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="3c32e-849">SNMPv3 트랩 보내기(IPv4 및 IPv6)</span><span class="sxs-lookup"><span data-stu-id="3c32e-849">Send SNMPv3 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-850">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-850">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="3c32e-851">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-851">Description</span></span>

<span data-ttu-id="3c32e-852">이 서비스는 SNMP 트랩을 지정된 IP 주소의 SNMP 관리자로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-852">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="3c32e-853">이 트랩은 SNMP v3 PDU에 포함된 트랩 메시지 형식을 제외하고 기본적으로 SNMP v2 트랩과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-853">This trap is basically the same as the SNMP v2 trap, except the trap message format is contained in the SNMP v3 PDU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-854">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-854">Input Parameters</span></span>

- <span data-ttu-id="3c32e-855">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-855">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-856">**ip_address** SNMP 관리자의 IP(IPv4 또는 IPv6) 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-856">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="3c32e-857">**username** 커뮤니티 이름(사용자 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-857">**username** Community name (username).</span></span>
- <span data-ttu-id="3c32e-858">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="3c32e-858">**trap_type**</span></span>  
   <span data-ttu-id="3c32e-859">요청된 트랩의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-859">Type of trap requested.</span></span> <span data-ttu-id="3c32e-860">표준 이벤트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-860">The standard events are:</span></span>
   - <span data-ttu-id="3c32e-861">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="3c32e-861">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="3c32e-862">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="3c32e-862">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="3c32e-863">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="3c32e-863">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="3c32e-864">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="3c32e-864">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="3c32e-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="3c32e-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="3c32e-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="3c32e-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  
   <span data-ttu-id="3c32e-867">소유 데이터의 경우:</span><span class="sxs-lookup"><span data-stu-id="3c32e-867">For proprietary data:</span></span>
   - <span data-ttu-id="3c32e-868">NX_SNMP_TRAP_CUSTOM(0xFFFFFFFF)(nxd_snmp.h에 정의됨)</span><span class="sxs-lookup"><span data-stu-id="3c32e-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="3c32e-869">**elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="3c32e-869">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="3c32e-870">**object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-870">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="3c32e-871">목록은 NX_NULL 로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-871">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-872">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-872">Return Values</span></span>

- <span data-ttu-id="3c32e-873">**NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-873">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="3c32e-874">**NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-874">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="3c32e-875">**NX_NOT_ENABLED**(0x14) SNMPv3가 사용하도록 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-875">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="3c32e-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR**(0x104) 지원되지 않는 IP 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="3c32e-877">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-877">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-878">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-878">Allowed From</span></span>

<span data-ttu-id="3c32e-879">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-879">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-880">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-880">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="3c32e-881">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="3c32e-881">nxd_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="3c32e-882">OID를 직접 지정하는 SNMPv3 트랩 보내기</span><span class="sxs-lookup"><span data-stu-id="3c32e-882">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-883">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-883">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="3c32e-884">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-884">Description</span></span>

<span data-ttu-id="3c32e-885">이 서비스는 지정된 IP 주소(IPv4/IPv6)의 SNMP 관리자에 SNMPv3 트랩을 보내고 호출자가 직접 OID를 지정할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-885">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-886">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-886">Input Parameters</span></span>

- <span data-ttu-id="3c32e-887">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-887">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="3c32e-888">**ip_address** SNMP 관리자의 IP 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-888">**ip_address** Pointer to IP address of SNMP Manager.</span></span>
- <span data-ttu-id="3c32e-889">**username** 사용자 이름(커뮤니티 이름)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-889">**username** Username (community name).</span></span>
- <span data-ttu-id="3c32e-890">**oid** OID를 포함하는 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-890">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="3c32e-891">**elapsed_time** 시간 시스템이 가동되었습니다(sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="3c32e-891">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="3c32e-892">**object_list_ptr** SNMP 트랩에 포함할 개체 및 연결된 값의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-892">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="3c32e-893">목록은 NX_NULL 로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-893">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-894">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-894">Return Values</span></span>

- <span data-ttu-id="3c32e-895">**NX_SUCCESS**(0x00) 성공적인 SNMP 트랩 보내기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-895">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="3c32e-896">**NX_SNMP_ERROR**(0x100) SNMP 트랩을 보내는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-896">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="3c32e-897">**NX_PTR_ERROR**(0x16) 잘못된 SNMP 에이전트 또는 매개 변수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-897">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="3c32e-898">**NX_IP_ADDRESS_ERROR**(0x21) 잘못된 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-898">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-899">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-899">Allowed From</span></span>

<span data-ttu-id="3c32e-900">스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-900">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-901">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-901">Example</span></span>

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a><span data-ttu-id="3c32e-902">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-902">nx_snmp_agent_v3_context_boots_set</span></span>
<span data-ttu-id="3c32e-903">다시 부팅 수 설정(SNMPv3를 사용하도록 설정한 경우)</span><span class="sxs-lookup"><span data-stu-id="3c32e-903">Set the number of reboots (if SNMPv3 enabled)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-904">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-904">Prototype</span></span>

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a><span data-ttu-id="3c32e-905">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-905">Description</span></span>

<span data-ttu-id="3c32e-906">이 서비스는 SNMP 에이전트가 기록한 다시 부팅 횟수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-906">This service sets the number of reboots recorded by the SNMP agent.</span></span> <span data-ttu-id="3c32e-907">이 서비스는 부팅 수가 SNMPv3 프로토콜에서만 사용되므로 SNMP 에이전트에 대해 SNMPv3를 사용하도록 설정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-907">This service is only available if SNMPv3 is enabled for the SNMP agent because boot count is only used in the SNMPv3 protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-908">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-908">Input Parameters</span></span>

- <span data-ttu-id="3c32e-909">**agent_ptr** SNMP 에이전트 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-909">**agent_ptr** Pointer to SNMP Agent control block</span></span>
- <span data-ttu-id="3c32e-910">**boots** SNMP 에이전트 부팅 횟수를 설정할 값입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-910">**boots** The value to set SNMP Agent boot count to</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-911">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-911">Return Values</span></span>

- <span data-ttu-id="3c32e-912">**NX_SUCCESS**(0x00) 부팅 횟수를 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-912">**NX_SUCCESS** (0x00) Successfully set boot count</span></span>
- <span data-ttu-id="3c32e-913">**NX_SNMP_ERROR**(0X100) 부팅 횟수 설정 오류</span><span class="sxs-lookup"><span data-stu-id="3c32e-913">**NX_SNMP_ERROR** (0x100) Error setting boot count</span></span>
- <span data-ttu-id="3c32e-914">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-914">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-915">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-915">Allowed From</span></span>

<span data-ttu-id="3c32e-916">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-916">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-917">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-917">Example</span></span>

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a><span data-ttu-id="3c32e-918">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="3c32e-918">nx_snmp_object_compare</span></span>
<span data-ttu-id="3c32e-919">두 개체 비교</span><span class="sxs-lookup"><span data-stu-id="3c32e-919">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-920">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-920">Prototype</span></span>

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a><span data-ttu-id="3c32e-921">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-921">Description</span></span>

<span data-ttu-id="3c32e-922">이 서비스는 제공된 개체 ID를 참조 개체 ID와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-922">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="3c32e-923">두 개체 ID는 모두 ASCII SMI-S 표기법으로 되어 있습니다. 예를 들어, 두 개체는 모두 ASCII 문자열 "1.3.6"으로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-923">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="3c32e-924">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-924">This service is deprecated.</span></span> <span data-ttu-id="3c32e-925">개발자는 nx_snmp_object_compare_extended()로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-925">Developers are encouraged to migrate to *nx_snmp_object_compare_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-926">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-926">Input Parameters</span></span>

- <span data-ttu-id="3c32e-927">**object** 개체 ID에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-927">**object** Pointer to object ID.</span></span>
- <span data-ttu-id="3c32e-928">**reference_object** 참조 개체 ID에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-928">**reference_object** Pointer to the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-929">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-929">Return Values</span></span>

- <span data-ttu-id="3c32e-930">**NX_SUCCESS**(0x00) 개체가 참조 개체와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-930">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="3c32e-931">**NX_SNMP_NEXT_ENTRY**(0x101) 개체가 참조 개체보다 작습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-931">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="3c32e-932">**NX_SNMP_ERROR**(0x100) 개체가 참조 개체보다 큽니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-932">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="3c32e-933">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-933">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-934">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-934">Allowed From</span></span>

<span data-ttu-id="3c32e-935">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-935">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-936">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-936">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a><span data-ttu-id="3c32e-937">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="3c32e-937">nx_snmp_object_compare_extended</span></span>
<span data-ttu-id="3c32e-938">두 개체 비교</span><span class="sxs-lookup"><span data-stu-id="3c32e-938">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-939">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-939">Prototype</span></span>

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a><span data-ttu-id="3c32e-940">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-940">Description</span></span>

<span data-ttu-id="3c32e-941">이 서비스는 제공된 개체 ID를 참조 개체 ID와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-941">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="3c32e-942">두 개체 ID는 모두 ASCII SMI-S 표기법으로 되어 있습니다. 예를 들어, 두 개체는 모두 ASCII 문자열 "1.3.6"으로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-942">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="3c32e-943">이 서비스는 nx_snmp_object_compare()를 대신합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-943">This service replaces *nx_snmp_object_compare().*</span></span> <span data-ttu-id="3c32e-944">이 버전을 사용하려면 호출자가 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-944">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-945">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-945">Input Parameters</span></span>

- <span data-ttu-id="3c32e-946">**request_object** 요청 개체 ID에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-946">**request_object** Pointer to request object ID.</span></span>
- <span data-ttu-id="3c32e-947">**request_object_length** 요청 개체 ID의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-947">**request_object_length** Length of the request object ID.</span></span>
- <span data-ttu-id="3c32e-948">**reference_object** 참조 개체 ID에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-948">**reference_object** Pointer to the reference object ID.</span></span>
- <span data-ttu-id="3c32e-949">**reference_object_length** 참조 개체 ID의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-949">**reference_object_length** Length of the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-950">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-950">Return Values</span></span>

- <span data-ttu-id="3c32e-951">**NX_SUCCESS**(0x00) 개체가 참조 개체와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-951">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="3c32e-952">**NX_SNMP_NEXT_ENTRY**(0x101) 개체가 참조 개체보다 작습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-952">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="3c32e-953">**NX_SNMP_ERROR**(0x100) 개체가 참조 개체보다 큽니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-953">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="3c32e-954">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-954">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-955">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-955">Allowed From</span></span>

<span data-ttu-id="3c32e-956">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-956">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-957">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-957">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a><span data-ttu-id="3c32e-958">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="3c32e-958">nx_snmp_object_copy</span></span>
<span data-ttu-id="3c32e-959">개체 복사</span><span class="sxs-lookup"><span data-stu-id="3c32e-959">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-960">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-960">Prototype</span></span>

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a><span data-ttu-id="3c32e-961">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-961">Description</span></span>

<span data-ttu-id="3c32e-962">이 서비스는 ASCII SIM 표기법의 소스 개체를 대상 개체로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-962">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="3c32e-963">이 서비스는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-963">This service is deprecated.</span></span> <span data-ttu-id="3c32e-964">개발자는 로 마이그레이션하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-964">Developers are encouraged to migrate to *nx_snmp_object_copy_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-965">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-965">Input Parameters</span></span>

- <span data-ttu-id="3c32e-966">**source_object_name** 소스 개체 ID에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-966">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="3c32e-967">**destination_object_name** 대상 개체 ID에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-967">**destination_object_name** Pointer to destination object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-968">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-968">Return Values</span></span>

- <span data-ttu-id="3c32e-969">**size** 대상 이름으로 복사할 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-969">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="3c32e-970">오류가 발생하면 0이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-970">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-971">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-971">Allowed From</span></span>

<span data-ttu-id="3c32e-972">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-972">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-973">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-973">Example</span></span>

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a><span data-ttu-id="3c32e-974">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="3c32e-974">nx_snmp_object_copy_extended</span></span>
<span data-ttu-id="3c32e-975">개체 복사</span><span class="sxs-lookup"><span data-stu-id="3c32e-975">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-976">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-976">Prototype</span></span>

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a><span data-ttu-id="3c32e-977">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-977">Description</span></span>

<span data-ttu-id="3c32e-978">이 서비스는 ASCII SIM 표기법의 소스 개체를 대상 개체로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-978">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="3c32e-979">이 서비스는 nx_snmp_object_copy()를 대신합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-979">This service replaces *nx_snmp_object_copy().*</span></span> <span data-ttu-id="3c32e-980">이 버전을 사용하려면 호출자가 길이 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-980">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-981">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-981">Input Parameters</span></span>

- <span data-ttu-id="3c32e-982">**source_object_name** 소스 개체 ID에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-982">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="3c32e-983">**source_object_name_length** 소스 개체 ID의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-983">**source_object_name_length** Length of source object ID.</span></span>
- <span data-ttu-id="3c32e-984">**destination_object_name_buffer** 대상 개체 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-984">**destination_object_name_buffer** Pointer to destination object buffer.</span></span>
- <span data-ttu-id="3c32e-985">**destination_object_name_buffer_size** 대상 개체 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-985">**destination_object_name_buffer_size** Size of destination object buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-986">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-986">Return Values</span></span>

- <span data-ttu-id="3c32e-987">**size** 대상 이름으로 복사할 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-987">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="3c32e-988">오류가 발생하면 0이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-988">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-989">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-989">Allowed From</span></span>

<span data-ttu-id="3c32e-990">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-990">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-991">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-991">Example</span></span>

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a><span data-ttu-id="3c32e-992">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-992">nx_snmp_object_counter_get</span></span>
<span data-ttu-id="3c32e-993">카운터 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-993">Get counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-994">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-994">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="3c32e-995">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-995">Description</span></span>

<span data-ttu-id="3c32e-996">이 서비스는 소스 포인터로 지정된 주소에서 카운터 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-996">This service retrieves the counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-997">이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-997">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-998">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-998">Input Parameters</span></span>

- <span data-ttu-id="3c32e-999">**source_ptr** 카운터 소스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-999">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="3c32e-1000">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1000">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1001">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1001">Return Values</span></span>

- <span data-ttu-id="3c32e-1002">**NX_SUCCESS**(0x00) 카운터 개체가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1002">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="3c32e-1003">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1003">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1004">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1004">Allowed From</span></span>

<span data-ttu-id="3c32e-1005">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1005">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1006">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1006">Example</span></span>

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a><span data-ttu-id="3c32e-1007">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-1007">nx_snmp_object_counter_set</span></span>
<span data-ttu-id="3c32e-1008">카운터 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1008">Set counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1009">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1009">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1010">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1010">Description</span></span>

<span data-ttu-id="3c32e-1011">이 서비스는 대상 포인터로 지정된 주소의 카운터를 NetX 개체 데이터 구조의 카운터 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1011">This service sets the counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1012">이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1012">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1013">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1013">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1014">**destination_ptr** 카운터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1014">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="3c32e-1015">**object_data** 카운터 소스 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1015">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1016">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1016">Return Values</span></span>

- <span data-ttu-id="3c32e-1017">**NX_SUCCESS**(0x00) 카운터 개체가 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1017">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="3c32e-1018">**NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1018">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="3c32e-1019">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1019">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1020">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1020">Allowed From</span></span>

<span data-ttu-id="3c32e-1021">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1021">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1022">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1022">Example</span></span>

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a><span data-ttu-id="3c32e-1023">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-1023">nx_snmp_object_counter64_get</span></span>
<span data-ttu-id="3c32e-1024">64비트 카운터 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-1024">Get 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1025">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1025">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1026">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1026">Description</span></span>

<span data-ttu-id="3c32e-1027">이 서비스는 소스 포인터로 지정된 주소에서 64비트 카운터 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1027">This service retrieves the 64-bit counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1028">이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1028">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1029">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1029">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1030">**source_ptr** 카운터 소스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1030">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="3c32e-1031">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1031">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1032">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1032">Return Values</span></span>

- <span data-ttu-id="3c32e-1033">**NX_SUCCESS**(0x00) 카운터 개체가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1033">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="3c32e-1034">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1034">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1035">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1035">Allowed From</span></span>

<span data-ttu-id="3c32e-1036">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1036">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1037">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1037">Example</span></span>

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a><span data-ttu-id="3c32e-1038">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-1038">nx_snmp_object_counter64_set</span></span>
<span data-ttu-id="3c32e-1039">64비트 카운터 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1039">Set 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1040">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1040">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="3c32e-1041">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1041">Description</span></span>

<span data-ttu-id="3c32e-1042">이 서비스는 대상 포인터로 지정된 주소의 64비트 카운터를 NetX 개체 데이터 구조의 카운터 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1042">This service sets the 64-bit counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1043">이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1043">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1044">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1044">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1045">**destination_ptr** 카운터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1045">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="3c32e-1046">**object_data** 카운터 소스 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1046">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1047">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1047">Return Values</span></span>

- <span data-ttu-id="3c32e-1048">**NX_SUCCESS**(0x00) 카운터 개체가 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1048">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="3c32e-1049">**NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1049">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="3c32e-1050">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1050">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1051">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1051">Allowed From</span></span>

<span data-ttu-id="3c32e-1052">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1052">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1053">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1053">Example</span></span>

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a><span data-ttu-id="3c32e-1054">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="3c32e-1054">nx_snmp_object_end_of_mib</span></span>
<span data-ttu-id="3c32e-1055">end-of-mib 값 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1055">Set end-of-mib value</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1056">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1056">Prototype</span></span>

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1057">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1057">Description</span></span>

<span data-ttu-id="3c32e-1058">이 서비스는 MIB의 끝에 신호를 보내는 개체를 만들며 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1058">This service creates an object signaling the end of the MIB and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1059">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1059">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1060">**not_used_ptr** 포인터가 사용되지 않습니다. NX_NULL이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1060">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="3c32e-1061">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1061">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1062">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1062">Return Values</span></span>

- <span data-ttu-id="3c32e-1063">**NX_SUCCESS**(0x00) end-of-mib 개체가 빌드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1063">**NX_SUCCESS** (0x00) The end-of-mib object has be successfully built.</span></span>
- <span data-ttu-id="3c32e-1064">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1064">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1065">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1065">Allowed From</span></span>

<span data-ttu-id="3c32e-1066">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1066">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1067">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1067">Example</span></span>

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a><span data-ttu-id="3c32e-1068">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-1068">nx_snmp_object_gauge_get</span></span>
<span data-ttu-id="3c32e-1069">계기 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-1069">Get gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1070">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1070">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1071">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1071">Description</span></span>

<span data-ttu-id="3c32e-1072">이 서비스는 소스 포인터로 지정된 주소에서 계기 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1072">This service retrieves the gauge object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1073">이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1073">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1074">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1074">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1075">**source_ptr** 계기 소스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1075">**source_ptr** Pointer to gauge source.</span></span>
- <span data-ttu-id="3c32e-1076">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1076">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1077">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1077">Return Values</span></span>

- <span data-ttu-id="3c32e-1078">**NX_SUCCESS**(0x00) 계기 개체가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1078">**NX_SUCCESS** (0x00) The gauge object has be successfully retrieved.</span></span>
- <span data-ttu-id="3c32e-1079">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1079">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1080">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1080">Allowed From</span></span>

<span data-ttu-id="3c32e-1081">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1081">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1082">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1082">Example</span></span>

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a><span data-ttu-id="3c32e-1083">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-1083">nx_snmp_object_gauge_set</span></span>
<span data-ttu-id="3c32e-1084">계기 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1084">Set gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1085">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1085">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1086">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1086">Description</span></span>

<span data-ttu-id="3c32e-1087">이 서비스는 대상 포인터로 지정된 주소의 계기를 NetX 개체 데이터 구조의 계기 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1087">This service sets the gauge at the address specified by the destination pointer with the gauge value in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1088">이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1088">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1089">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1089">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1090">**destination_ptr** 계기 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1090">**destination_ptr** Pointer to gauge destination.</span></span>
- <span data-ttu-id="3c32e-1091">**object_data** 계기 소스 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1091">**object_data** Pointer to gauge source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1092">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1092">Return Values</span></span>

- <span data-ttu-id="3c32e-1093">**NX_SUCCESS**(0x00) 계기 개체가 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1093">**NX_SUCCESS** (0x00) The gauge object has be successfully set.</span></span>
- <span data-ttu-id="3c32e-1094">**NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1094">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="3c32e-1095">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1095">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1096">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1096">Allowed From</span></span>

<span data-ttu-id="3c32e-1097">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1097">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1098">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1098">Example</span></span>

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a><span data-ttu-id="3c32e-1099">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-1099">nx_snmp_object_id_get</span></span>
<span data-ttu-id="3c32e-1100">개체 ID 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-1100">Get object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1101">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1101">Prototype</span></span>

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1102">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1102">Description</span></span>

<span data-ttu-id="3c32e-1103">이 서비스는 소스 포인터로 지정된 주소에서 개체 ID(ASCII SIM 표기법)를 검색한 후 NetX 개체 데이터 구조에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1103">This service retrieves the object ID (in ASCII SIM notation) at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1104">이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1104">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1105">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1105">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1106">**source_ptr** 개체 ID 소스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1106">**source_ptr** Pointer to object ID source.</span></span>
- <span data-ttu-id="3c32e-1107">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1107">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1108">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1108">Return Values</span></span>

- <span data-ttu-id="3c32e-1109">**NX_SUCCESS**(0x00) 개체 ID가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1109">**NX_SUCCESS** (0x00) The object ID has be successfully retrieved.</span></span>
- <span data-ttu-id="3c32e-1110">**NX_SNMP_ERROR**(0X100) 잘못된 개체 길이</span><span class="sxs-lookup"><span data-stu-id="3c32e-1110">**NX_SNMP_ERROR** (0x100) Invalid length of object</span></span>
- <span data-ttu-id="3c32e-1111">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1111">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1112">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1112">Allowed From</span></span>

<span data-ttu-id="3c32e-1113">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1113">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1114">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1114">Example</span></span>

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a><span data-ttu-id="3c32e-1115">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-1115">nx_snmp_object_id_set</span></span>
<span data-ttu-id="3c32e-1116">개체 ID 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1116">Set object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1117">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1117">Prototype</span></span>

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1118">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1118">Description</span></span>

<span data-ttu-id="3c32e-1119">이 서비스는 대상 포인터로 지정된 주소의 개체 ID(ASCII SIM 표기법)를 NetX 개체 데이터 구조의 개체 ID로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1119">This service sets the object ID (in ASCII SIM notation) at the address specified by the destination pointer with the object ID in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1120">이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1120">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1121">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1121">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1122">**destination_ptr** 개체 ID 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1122">**destination_ptr** Pointer to object ID destination.</span></span>
- <span data-ttu-id="3c32e-1123">**object_data** 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1123">**object_data** Pointer to object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1124">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1124">Return Values</span></span>

- <span data-ttu-id="3c32e-1125">**NX_SUCCESS**(0x00) 개체 ID가 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1125">**NX_SUCCESS** (0x00) The object ID has been successfully set.</span></span>
- <span data-ttu-id="3c32e-1126">**NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1126">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="3c32e-1127">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1127">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1128">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1128">Allowed From</span></span>

<span data-ttu-id="3c32e-1129">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1129">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1130">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1130">Example</span></span>

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a><span data-ttu-id="3c32e-1131">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-1131">nx_snmp_object_integer_get</span></span>
<span data-ttu-id="3c32e-1132">정수 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-1132">Get integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1133">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1133">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1134">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1134">Description</span></span>

<span data-ttu-id="3c32e-1135">이 서비스는 소스 포인터로 지정된 주소에서 정수 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1135">This service retrieves the integer object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1136">이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1136">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1137">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1137">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1138">**source_ptr** 정수 소스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1138">**source_ptr** Pointer to integer source.</span></span>
- <span data-ttu-id="3c32e-1139">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1139">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1140">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1140">Return Values</span></span>

- <span data-ttu-id="3c32e-1141">**NX_SUCCESS**(0x00) 정수 개체가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1141">**NX_SUCCESS** (0x00) The integer object has been successfully retrieved.</span></span>
- <span data-ttu-id="3c32e-1142">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1142">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1143">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1143">Allowed From</span></span>

<span data-ttu-id="3c32e-1144">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1145">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1145">Example</span></span>

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a><span data-ttu-id="3c32e-1146">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-1146">nx_snmp_object_integer_set</span></span>
<span data-ttu-id="3c32e-1147">정수 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1147">Set integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1148">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1148">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1149">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1149">Description</span></span>

<span data-ttu-id="3c32e-1150">이 서비스는 대상 포인터로 지정된 주소의 정수를 NetX 개체 데이터 구조의 정수 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1150">This service sets the integer at the address specified by the destination pointer with the integer value in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1151">이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1151">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1152">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1152">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1153">**destination_ptr** 정수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1153">**destination_ptr** Pointer to integer destination.</span></span>
- <span data-ttu-id="3c32e-1154">**object_data** 정수 소스 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1154">**object_data** Pointer to integer source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1155">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1155">Return Values</span></span>

- <span data-ttu-id="3c32e-1156">**NX_SUCCESS**(0x00) 정수 개체가 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1156">**NX_SUCCESS** (0x00) The integer object has been successfully set.</span></span>
- <span data-ttu-id="3c32e-1157">**NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1157">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="3c32e-1158">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1158">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1159">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1159">Allowed From</span></span>

<span data-ttu-id="3c32e-1160">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1160">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1161">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1161">Example</span></span>

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a><span data-ttu-id="3c32e-1162">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-1162">nx_snmp_object_ip_address_get</span></span>
<span data-ttu-id="3c32e-1163">IP 주소 개체 가져오기(IPv4만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-1163">Get IP address object (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-1164">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1164">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1165">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1165">Description</span></span>

<span data-ttu-id="3c32e-1166">이 서비스는 소스 포인터로 지정된 주소에서 IP 주소 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1166">This service retrieves the IP address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1167">이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1167">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1168">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1168">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1169">**source_ptr** IPv4 주소 소스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1169">**source_ptr** Pointer to IPv4 address source.</span></span>
- <span data-ttu-id="3c32e-1170">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1170">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1171">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1171">Return Values</span></span>

- <span data-ttu-id="3c32e-1172">**NX_SUCCESS**(0x00) IP 주소 개체가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1172">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="3c32e-1173">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1173">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1174">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1174">Allowed From</span></span>

<span data-ttu-id="3c32e-1175">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1175">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1176">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1176">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a><span data-ttu-id="3c32e-1177">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-1177">nx_snmp_object_ipv6_address_get</span></span>
<span data-ttu-id="3c32e-1178">IP 주소 개체 가져오기(IPv6만 해당)</span><span class="sxs-lookup"><span data-stu-id="3c32e-1178">Get IP address object (IPv6 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="3c32e-1179">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1179">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1180">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1180">Description</span></span>

<span data-ttu-id="3c32e-1181">이 서비스는 소스 포인터로 지정된 주소에서 IPv6 주소 개체를 검색한 후 NetX 개체 데이터 구조에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1181">This service retrieves the IPv6 address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span>
<span data-ttu-id="3c32e-1182">이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1182">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1183">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1183">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1184">**source_ptr** IPv6 주소 소스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1184">**source_ptr** Pointer to IPv6 address source.</span></span>
- <span data-ttu-id="3c32e-1185">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1185">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1186">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1186">Return Values</span></span>

- <span data-ttu-id="3c32e-1187">**NX_SUCCESS**(0x00) IP 주소 개체가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1187">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="3c32e-1188">**NX_SNMP_ERROR_WRONGTYPE**(0X07) 잘못된 입력 SNMP 개체 코드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1188">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Incorrect input SNMP object code</span></span>
- <span data-ttu-id="3c32e-1189">**NX_NOT_ENABLED**(0x14) IPv6가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1189">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="3c32e-1190">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1190">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1191">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1191">Allowed From</span></span>

<span data-ttu-id="3c32e-1192">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1192">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1193">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1193">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a><span data-ttu-id="3c32e-1194">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-1194">nx_snmp_object_ip_address_set</span></span>
<span data-ttu-id="3c32e-1195">IPv4 주소 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1195">Set IPv4 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1196">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1196">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1197">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1197">Description</span></span>

<span data-ttu-id="3c32e-1198">이 서비스는 대상 포인터로 지정된 주소의 IPv4 주소를 NetX 개체 데이터 구조의 IP 주소로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1198">This service sets the IPv4 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1199">이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1199">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1200">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1200">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1201">**destination_ptr** 설정할 IP 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1201">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="3c32e-1202">**object_data** IP 주소 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1202">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1203">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1203">Return Values</span></span>

- <span data-ttu-id="3c32e-1204">**NX_SUCCESS**(0x00) IP 주소 개체가 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1204">**NX_SUCCESS** (0x00) The IP address object has been successfully set.</span></span>
- <span data-ttu-id="3c32e-1205">**NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1205">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="3c32e-1206">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1206">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1207">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1207">Allowed From</span></span>

<span data-ttu-id="3c32e-1208">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1209">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1209">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a><span data-ttu-id="3c32e-1210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-1210">nx_snmp_object_ipv6_address_set</span></span>
<span data-ttu-id="3c32e-1211">IPv6 주소 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1211">Set IPv6 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1212">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1212">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1213">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1213">Description</span></span>

<span data-ttu-id="3c32e-1214">이 서비스는 대상 포인터로 지정된 주소의 IPv6 주소를 NetX 개체 데이터 구조의 IP 주소로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1214">This service sets the IPv6 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1215">이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1215">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1216">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1216">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1217">**destination_ptr** 설정할 IP 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1217">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="3c32e-1218">**object_data** IP 주소 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1218">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1219">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1219">Return Values</span></span>

- <span data-ttu-id="3c32e-1220">**NX_SUCCESS**(0x00) IPv6 주소가 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1220">**NX_SUCCESS** (0x00) The IPv6 address has been successfully set.</span></span>
- <span data-ttu-id="3c32e-1221">**NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1221">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="3c32e-1222">**NX_NOT_ENABLED**(0x14) IPv6가 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1222">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="3c32e-1223">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1223">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1224">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1224">Allowed From</span></span>

<span data-ttu-id="3c32e-1225">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1225">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1226">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1226">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a><span data-ttu-id="3c32e-1227">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="3c32e-1227">nx_snmp_object_no_instance</span></span>
<span data-ttu-id="3c32e-1228">no-instance 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1228">Set no-instance object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1229">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1229">Prototype</span></span>

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1230">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1230">Description</span></span>

<span data-ttu-id="3c32e-1231">이 서비스는 지정된 개체의 인스턴스가 없음을 신호로 알리는 개체를 만들며 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1231">This service creates an object signaling that there was no instance of the specified object and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1232">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1232">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1233">**not_used_ptr** 포인터가 사용되지 않습니다. NX_NULL이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1233">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="3c32e-1234">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1234">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1235">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1235">Return Values</span></span>

- <span data-ttu-id="3c32e-1236">**NX_SUCCESS**(0x00) no-instance 개체가 빌드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1236">**NX_SUCCESS** (0x00) The no-instance object has been successfully built.</span></span>
- <span data-ttu-id="3c32e-1237">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1237">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1238">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1238">Allowed From</span></span>

<span data-ttu-id="3c32e-1239">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1239">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1240">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1240">Example</span></span>

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a><span data-ttu-id="3c32e-1241">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="3c32e-1241">nx_snmp_object_not_found</span></span>
<span data-ttu-id="3c32e-1242">not-found 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1242">Set not-found object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1243">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1243">Prototype</span></span>

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1244">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1244">Description</span></span>

<span data-ttu-id="3c32e-1245">이 서비스는 개체를 찾을 수 없다는 신호를 보내는 개체를 만들며 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1245">This service creates an object signaling the object was not found and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1246">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1246">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1247">**not_used_ptr** 포인터가 사용되지 않습니다. NX_NULL이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1247">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="3c32e-1248">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1248">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1249">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1249">Return Values</span></span>

- <span data-ttu-id="3c32e-1250">**NX_SUCCESS**(0x00) not-found 개체가 빌드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1250">**NX_SUCCESS** (0x00) The not-found object has been successfully built.</span></span>
- <span data-ttu-id="3c32e-1251">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1251">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1252">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1252">Allowed From</span></span>

<span data-ttu-id="3c32e-1253">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1253">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1254">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1254">Example</span></span>

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a><span data-ttu-id="3c32e-1255">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-1255">nx_snmp_object_octet_string_get</span></span>
<span data-ttu-id="3c32e-1256">옥텟 문자열 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-1256">Get octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1257">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1257">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a><span data-ttu-id="3c32e-1258">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1258">Description</span></span>

<span data-ttu-id="3c32e-1259">이 서비스는 소스 포인터로 지정된 주소에서 옥텟 문자열을 검색한 후 NetX 개체 데이터 구조에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1259">This service retrieves the octet string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1260">이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1260">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1261">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1261">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1262">**source_ptr** 옥텟 문자열 소스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1262">**source_ptr** Pointer to octet string source.</span></span>
- <span data-ttu-id="3c32e-1263">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1263">**object_data** Pointer to destination object structure.</span></span>
- <span data-ttu-id="3c32e-1264">**length** 옥텟 문자열의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1264">**length** Number of bytes in octet string.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1265">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1265">Return Values</span></span>

- <span data-ttu-id="3c32e-1266">**NX_SUCCESS**(0x00) 옥텟 문자열 개체가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1266">**NX_SUCCESS** (0x00) The octet string object has been successfully retrieved.</span></span>
- <span data-ttu-id="3c32e-1267">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1267">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1268">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1268">Allowed From</span></span>

<span data-ttu-id="3c32e-1269">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1269">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1270">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1270">Example</span></span>

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a><span data-ttu-id="3c32e-1271">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-1271">nx_snmp_object_octet_string_set</span></span>
<span data-ttu-id="3c32e-1272">옥텟 문자열 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1272">Set octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1273">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1273">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1274">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1274">Description</span></span>

<span data-ttu-id="3c32e-1275">이 서비스는 대상 포인터로 지정된 주소의 옥텟 문자열을 NetX 개체 데이터 구조의 옥텟 문자열로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1275">This service sets the octet string at the address specified by the destination pointer with the octet string in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1276">이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1276">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1277">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1277">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1278">**destination_ptr** 옥텟 문자열 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1278">**destination_ptr** Pointer to octet string destination.</span></span>
- <span data-ttu-id="3c32e-1279">**object_data** 옥텟 문자열 소스 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1279">**object_data** Pointer to octet string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1280">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1280">Return Values</span></span>

- <span data-ttu-id="3c32e-1281">**NX_SUCCESS**(0x00) 옥텟 문자열 개체가 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1281">**NX_SUCCESS** (0x00) The octet string object has been successfully set.</span></span>
- <span data-ttu-id="3c32e-1282">**NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1282">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="3c32e-1283">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1283">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1284">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1284">Allowed From</span></span>

<span data-ttu-id="3c32e-1285">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1285">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1286">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1286">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a><span data-ttu-id="3c32e-1287">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-1287">nx_snmp_object_string_get</span></span>
<span data-ttu-id="3c32e-1288">ASCII 문자열 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-1288">Get ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1289">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1289">Prototype</span></span>

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1290">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1290">Description</span></span>

<span data-ttu-id="3c32e-1291">이 서비스는 소스 포인터로 지정된 주소에서 ASCII 문자열을 검색한 후 NetX 개체 데이터 구조에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1291">This service retrieves the ASCII string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1292">이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1292">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1293">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1293">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1294">**source_ptr** ASCII 문자열 소스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1294">**source_ptr** Pointer to ASCII string source.</span></span>
- <span data-ttu-id="3c32e-1295">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1295">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1296">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1296">Return Values</span></span>

- <span data-ttu-id="3c32e-1297">**NX_SUCCESS**(0x00) ASCII 문자열 개체가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1297">**NX_SUCCESS** (0x00) The ASCII string object has been successfully retrieved.</span></span>
- <span data-ttu-id="3c32e-1298">**NX_SNMP_ERROR**(0X100) 문자열이 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1298">**NX_SNMP_ERROR** (0x100) String is too big</span></span>  
- <span data-ttu-id="3c32e-1299">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1299">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1300">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1300">Allowed From</span></span>

<span data-ttu-id="3c32e-1301">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1301">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1302">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1302">Example</span></span>

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a><span data-ttu-id="3c32e-1303">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-1303">nx_snmp_object_string_set</span></span>
<span data-ttu-id="3c32e-1304">ASCII 문자열 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1304">Set ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1305">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1305">Prototype</span></span>

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1306">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1306">Description</span></span>

<span data-ttu-id="3c32e-1307">이 서비스는 대상 포인터로 지정된 주소의 ASCII 문자열을 NetX 개체 데이터 구조의 ASCII 문자열로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1307">This service sets the ASCII string at the address specified by the destination pointer with the ASCII string in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1308">이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1308">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1309">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1309">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1310">**destination_ptr** ASCII 문자열 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1310">**destination_ptr** Pointer to ASCII string destination.</span></span>
- <span data-ttu-id="3c32e-1311">**object_data** ASCII 문자열 소스 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1311">**object_data** Pointer to ASCII string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1312">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1312">Return Values</span></span>

- <span data-ttu-id="3c32e-1313">**NX_SUCCESS**(0x00) ASCII 문자열 개체가 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1313">**NX_SUCCESS** (0x00) The ASCII string object has been successfully set.</span></span>
- <span data-ttu-id="3c32e-1314">**NX_SNMP_ERROR**(0X100) 문자열이 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1314">**NX_SNMP_ERROR** (0x100) String too large.</span></span>
- <span data-ttu-id="3c32e-1315">**NX_SNMP_ERROR_BADVALUE**(0x03) 문자열에 잘못된 문자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1315">**NX_SNMP_ERROR_BADVALUE** (0x03) Invalid character in string</span></span>
- <span data-ttu-id="3c32e-1316">**NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1316">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="3c32e-1317">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1317">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1318">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1318">Allowed From</span></span>

<span data-ttu-id="3c32e-1319">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1319">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1320">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1320">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a><span data-ttu-id="3c32e-1321">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="3c32e-1321">nx_snmp_object_timetics_get</span></span>
<span data-ttu-id="3c32e-1322">timetics 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="3c32e-1322">Get timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1323">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1323">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1324">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1324">Description</span></span>

<span data-ttu-id="3c32e-1325">이 서비스는 소스 포인터로 지정된 주소에서 timetics를 검색한 후 NetX 개체 데이터 구조에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1325">This service retrieves the timetics at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="3c32e-1326">이 루틴은 일반적으로 GET 또는 GETNEXT 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1326">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1327">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1327">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1328">**source_ptr** timetics 소스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1328">**source_ptr** Pointer to timetics source.</span></span>
- <span data-ttu-id="3c32e-1329">**object_data** 대상 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1329">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1330">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1330">Return Values</span></span>

- <span data-ttu-id="3c32e-1331">**NX_SUCCESS**(0x00) timetics 개체가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1331">**NX_SUCCESS** (0x00) The timetics object has been successfully retrieved.</span></span>
- <span data-ttu-id="3c32e-1332">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1332">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1333">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1333">Allowed From</span></span>

<span data-ttu-id="3c32e-1334">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1334">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1335">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1335">Example</span></span>

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a><span data-ttu-id="3c32e-1336">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="3c32e-1336">nx_snmp_object_timetics_set</span></span>
<span data-ttu-id="3c32e-1337">timetics 개체 설정</span><span class="sxs-lookup"><span data-stu-id="3c32e-1337">Set timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="3c32e-1338">프로토타입</span><span class="sxs-lookup"><span data-stu-id="3c32e-1338">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="3c32e-1339">Description</span><span class="sxs-lookup"><span data-stu-id="3c32e-1339">Description</span></span>

<span data-ttu-id="3c32e-1340">이 서비스는 대상 포인터로 지정된 주소의 timetics 변수를 NetX 개체 데이터 구조의 timetics로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1340">This service sets the timetics variable at the address specified by the destination pointer with the timetics in the NetX object data structure.</span></span>
<span data-ttu-id="3c32e-1341">이 루틴은 일반적으로 SET 애플리케이션 콜백 루틴에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1341">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3c32e-1342">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="3c32e-1342">Input Parameters</span></span>

- <span data-ttu-id="3c32e-1343">**destination_ptr** timetics 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1343">**destination_ptr** Pointer to timetics destination.</span></span>
- <span data-ttu-id="3c32e-1344">**object_data** timetics 소스 개체 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1344">**object_data** Pointer to timetics source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="3c32e-1345">반환 값</span><span class="sxs-lookup"><span data-stu-id="3c32e-1345">Return Values</span></span>

- <span data-ttu-id="3c32e-1346">**NX_SUCCESS**(0x00) timetics 개체가 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1346">**NX_SUCCESS** (0x00) The timetics object has been successfully set.</span></span>
- <span data-ttu-id="3c32e-1347">**NX_SNMP_ERROR_WRONGTYPE**(0x07) 잘못된 개체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1347">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="3c32e-1348">**NX_PTR_ERROR**(0x07) 잘못된 입력 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3c32e-1348">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3c32e-1349">허용 위치</span><span class="sxs-lookup"><span data-stu-id="3c32e-1349">Allowed From</span></span>

<span data-ttu-id="3c32e-1350">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="3c32e-1350">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3c32e-1351">예제</span><span class="sxs-lookup"><span data-stu-id="3c32e-1351">Example</span></span>

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```