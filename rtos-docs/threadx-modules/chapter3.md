---
title: 3장 - 모듈 관리자 요구 사항
description: 이 문서에서는 ThreadX 모듈 관리자 빌드에 필요한 단계를 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8ea1a05096b5975de203648fddfb19c1a6105e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811412"
---
# <a name="chapter-3---module-manager-requirements"></a><span data-ttu-id="345d2-103">3장 - 모듈 관리자 요구 사항</span><span class="sxs-lookup"><span data-stu-id="345d2-103">Chapter 3 - Module Manager requirements</span></span>

<span data-ttu-id="345d2-104">ThreadX 모듈 관리자는 ThreadX RTOS와 함께 애플리케이션의 상주 부분에 위치합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-104">The ThreadX Module Manager resides in the resident portion of the application along with the ThreadX RTOS.</span></span> <span data-ttu-id="345d2-105">모듈 시작과, ThreadX API 서비스에 대한 모든 모듈 요청의 배치 및 발송을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-105">It is responsible for starting the module as well as fielding and dispatching all module requests for ThreadX API services.</span></span>

> [!NOTE]
> <span data-ttu-id="345d2-106">ThreadX 모듈 **관리자** 소스 파일(C 및 어셈블리)는 ThreadX 라이브러리 프로젝트 "**tx**"에 추가되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-106">The ThreadX Module **Manager** source files (C and assembly) should be added to the ThreadX library project "**tx**".</span></span>

<span data-ttu-id="345d2-107">ThreadX 모듈 관리자 빌드에 필요한 단계는 다음과 같습니다(각 단계는 아래에서 더 상세히 설명).</span><span class="sxs-lookup"><span data-stu-id="345d2-107">The following steps are required for building the ThreadX Module Manager (each step is described in greater detail below).</span></span>

1. <span data-ttu-id="345d2-108">모듈 정보를 포함하려면 **TX_THREAD** 제어 블록을 확장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-108">The **TX_THREAD** control block must be extended to include module information.</span></span> <span data-ttu-id="345d2-109">이를 수행하는 가장 쉬운 방법은 **_tx_port.h_ *_ 파일의 **TX_THREAD_EXTENSION_2** 정의를 **_txm_module_port.h_** 의 _* TX_THREAD_EXTENSION_2** 로 바꾸는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-109">The easiest way to accomplish this is to replace the definition of **TX_THREAD_EXTENSION_2** in the **_tx_port.h_*_ file with the _\* TX_THREAD_EXTENSION_2*\* found in **_txm_module_port.h_**.</span></span> <span data-ttu-id="345d2-110">포트 관련 확장에 대해서는 [부록](appendix.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="345d2-110">See [appendix](appendix.md) for port-specific extensions.</span></span>

<span data-ttu-id="345d2-111">확장 예제:</span><span class="sxs-lookup"><span data-stu-id="345d2-111">Example extension:</span></span>

   ```c
   #define TX_THREAD_EXTENSION_2                     \
       VOID      tx_thread_module_instance_ptr;      \
       VOID      tx_thread_module_entry_info_ptr;    \
       ULONG     tx_thread_module_current_user_mode; \
       ULONG     tx_thread_module_user_mode;         \
       VOID     *tx_thread_module_kernel_stack_start;\
       VOID     *tx_thread_module_kernel_stack_end;  \
       ULONG     tx_thread_module_kernel_stack_size; \
       VOID     *tx_thread_module_stack_ptr;         \
       VOID     *tx_thread_module_stack_start;       \
       VOID     *tx_thread_module_stack_end;         \
       ULONG     tx_thread_module_stack_size;        \
       VOID     *tx_thread_module_reserved;
   ```

   <span data-ttu-id="345d2-112">다음 확장은 ***tx_port.h*** 에 정의되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-112">The following extensions must be defined in ***tx_port.h***.</span></span>

   ```c
   #define TX_EVENT_FLAGS_GROUP_EXTENSION  VOID    *tx_event_flags_group_module_instance; \
        VOID   (*tx_event_flags_group_set_module_notify)(struct TX_EVENT_FLAGS_GROUP_STRUCT *group_ptr);

   #define TX_QUEUE_EXTENSION              VOID    *tx_queue_module_instance; \
        VOID   (*tx_queue_send_module_notify)(struct TX_QUEUE_STRUCT *queue_ptr);

   #define TX_SEMAPHORE_EXTENSION          VOID    *tx_semaphore_module_instance; \
        VOID   (*tx_semaphore_put_module_notify)(struct TX_SEMAPHORE_STRUCT *semaphore_ptr);

   #define TX_TIMER_EXTENSION              VOID    *tx_timer_module_instance; \
        VOID   (*tx_timer_module_expiration_function)(ULONG id);
   ```

2. <span data-ttu-id="345d2-113">모든 ***txm_module_manager_\**** C 및 어셈블리 파일을 ThreadX 라이브러리 프로젝트 **_tx_** 에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-113">Add all the ***txm_module_manager_\**** C and assembly files to the ThreadX library project **_tx_**.</span></span>
3. <span data-ttu-id="345d2-114">모든 라이브러리와 실행 파일 프로젝트를 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-114">Rebuild all libraries and executable projects.</span></span> <span data-ttu-id="345d2-115">NetX Duo가 필요한 경우, 정의된 **TXM_MODULE_ENABLE_NETX_DUO** 를 사용하여 모든 모듈 및 모듈 관리자 C 코드를 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-115">If NetX Duo is required, all Module and Module Manager C code should be built with **TXM_MODULE_ENABLE_NETX_DUO** defined.</span></span>

## <a name="module-manager-sources"></a><span data-ttu-id="345d2-116">모듈 관리자 원본</span><span class="sxs-lookup"><span data-stu-id="345d2-116">Module Manager sources</span></span>

<span data-ttu-id="345d2-117">ThreadX 모듈 관리자에는 상주 ThreadX 코드에 직접 연결 및 배치할 수 있도록 설계된 원본 파일 세트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-117">The ThreadX Module Manager has a set of source files that are designed to be linked and located directly with the resident ThreadX code.</span></span> <span data-ttu-id="345d2-118">이 파일은 모듈을 실행하고, 모듈로부터의 후속 ThreadX API 요청을 배치하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-118">These files provide the ability to launch a module and field subsequent ThreadX API requests from the module.</span></span> <span data-ttu-id="345d2-119">모듈 관리자 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-119">The module manager files are as follows.</span></span>

| <span data-ttu-id="345d2-120">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="345d2-120">**File Name**</span></span> |  <span data-ttu-id="345d2-121">**콘텐츠**</span><span class="sxs-lookup"><span data-stu-id="345d2-121">**Contents**</span></span> |
|-------------- | ------------- |
| <span data-ttu-id="345d2-122">***txm_module.h***</span><span class="sxs-lookup"><span data-stu-id="345d2-122">***txm_module.h***</span></span> | <span data-ttu-id="345d2-123">모듈 정보를 정의하는 파일을 포함합니다(모듈 소스 코드에도 포함).</span><span class="sxs-lookup"><span data-stu-id="345d2-123">Include file that defines module information (also included in the module source code).</span></span> |
| <span data-ttu-id="345d2-124">***txm_module_manager_dispatch.h***</span><span class="sxs-lookup"><span data-stu-id="345d2-124">***txm_module_manager_dispatch.h***</span></span> | <span data-ttu-id="345d2-125">발송 도우미 함수를 정의하는 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-125">Include file that defines dispatch helper functions.</span></span>|
| <span data-ttu-id="345d2-126">***txm_module_manager_util.h***</span><span class="sxs-lookup"><span data-stu-id="345d2-126">***txm_module_manager_util.h***</span></span> | <span data-ttu-id="345d2-127">내부 유틸리티 도우미 매크로 및 함수를 정의하는 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-127">Include file that defines internal utility helper macros & functions.</span></span> |
| <span data-ttu-id="345d2-128">***txm_module_port.h***</span><span class="sxs-lookup"><span data-stu-id="345d2-128">***txm_module_port.h***</span></span> | <span data-ttu-id="345d2-129">포트 관련 모듈 정보를 정의하는 파일을 포함합니다(모듈 소스 코드에도 포함).</span><span class="sxs-lookup"><span data-stu-id="345d2-129">Include file that defines port-specific module information (also included in the module source code).</span></span> |
| <span data-ttu-id="345d2-130">\***tx_initialize_low_level.\[s,S,68\]** _</span><span class="sxs-lookup"><span data-stu-id="345d2-130">\***tx_initialize_low_level.\[s,S,68\]** _</span></span> | <span data-ttu-id="345d2-131">기존 ThreadX 라이브러리 파일을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-131">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="345d2-132">모듈 관리자 및 메모리 실행을 위한 벡터 테이블과 추가 벡터 처리기를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-132">Updated vector table and additional vector handlers for module manager and memory exceptions.</span></span> <span data-ttu-id="345d2-133">_ 이 파일은 Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR에만 있습니다.\*</span><span class="sxs-lookup"><span data-stu-id="345d2-133">_This file is only in Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.\*</span></span>|
| <span data-ttu-id="345d2-134">\***tx_thread_context_restore.s** _</span><span class="sxs-lookup"><span data-stu-id="345d2-134">\***tx_thread_context_restore.s** _</span></span> | <span data-ttu-id="345d2-135">기존 ThreadX 라이브러리 파일을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-135">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="345d2-136">인터럽트 처리 후 스레드 컨텍스트를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-136">Restore thread context after interrupt processing.</span></span> <span data-ttu-id="345d2-137">_ 이 파일은 Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR에만 있습니다.\*</span><span class="sxs-lookup"><span data-stu-id="345d2-137">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="345d2-138">***tx_thread_schedule.\[s,S,68\]***</span><span class="sxs-lookup"><span data-stu-id="345d2-138">***tx_thread_schedule.\[s,S,68\]***</span></span> | <span data-ttu-id="345d2-139">기존 ThreadX 라이브러리 파일을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-139">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="345d2-140">스케줄러 코드를 확장합니다. 이 경우 메모리 관리 레지스터를 업데이트하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-140">Extended scheduler code, which in this case is used to update memory management registers.</span></span> |
| <span data-ttu-id="345d2-141">\***tx_thread_stack_build.s** _</span><span class="sxs-lookup"><span data-stu-id="345d2-141">\***tx_thread_stack_build.s** _</span></span> | <span data-ttu-id="345d2-142">기존 ThreadX 라이브러리 파일을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-142">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="345d2-143">스레드의 스택 프레임을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-143">Builds the stack frame of a thread.</span></span> <span data-ttu-id="345d2-144">_ 이 파일은 Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR에만 있습니다.\*</span><span class="sxs-lookup"><span data-stu-id="345d2-144">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="345d2-145">***txm_module_manager_thread_stack_build.\[s,S,68\]***</span><span class="sxs-lookup"><span data-stu-id="345d2-145">***txm_module_manager_thread_stack_build.\[s,S,68\]***</span></span> | <span data-ttu-id="345d2-146">모든 모듈 초기 스택을 빌드하고, 위치 중립적 데이터 액세스를 위한 설정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-146">Builds all module initial stacks, includes setup for position-independent data access.</span></span> |
| <span data-ttu-id="345d2-147">\***txm_module_manager_user_mode_entry.\[s,S\]** _</span><span class="sxs-lookup"><span data-stu-id="345d2-147">\***txm_module_manager_user_mode_entry.\[s,S\]** _</span></span> | <span data-ttu-id="345d2-148">모듈이 커널 모드에 들어갈 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-148">Allows the module to enter kernel mode.</span></span> <span data-ttu-id="345d2-149">_ 이 파일은 Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR에만 있습니다.\*</span><span class="sxs-lookup"><span data-stu-id="345d2-149">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="345d2-150">***txm_module_manager_alignment_adjust.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-150">***txm_module_manager_alignment_adjust.c***</span></span> | <span data-ttu-id="345d2-151">포트 관련 정렬 요구 사항을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-151">Handles port-specific alignment requirements.</span></span>|
| <span data-ttu-id="345d2-152">***txm_module_manager_application_request.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-152">***txm_module_manager_application_request.c***</span></span> | <span data-ttu-id="345d2-153">상주 코드에 대한 애플리케이션 관련 요청을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-153">Handles the application-specific requests to the resident code.</span></span> |
| <span data-ttu-id="345d2-154">***txm_module_manager_callback_request.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-154">***txm_module_manager_callback_request.c***</span></span> | <span data-ttu-id="345d2-155">모듈에 콜백 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-155">Sends a callback request to a module.</span></span> |
| <span data-ttu-id="345d2-156">***txm_module_manager_event_flags_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-156">***txm_module_manager_event_flags_notify_trampoline.c***</span></span> | <span data-ttu-id="345d2-157">ThreadX로부터의 이벤트 플래그 설정 알림 호출을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-157">Processes the event flags set notification call from ThreadX.</span></span> |
| <span data-ttu-id="345d2-158">***txm_module_manager_external_memory_enable.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-158">***txm_module_manager_external_memory_enable.c***</span></span> | <span data-ttu-id="345d2-159">모듈이 액세스할 수 있는 공유 메모리 공간에 대해 메모리 관리 테이블에 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-159">Creates an entry in the memory management table for a shared memory space the module can access.</span></span> |
| <span data-ttu-id="345d2-160">***txm_module_manager_file_load.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-160">***txm_module_manager_file_load.c***</span></span> | <span data-ttu-id="345d2-161">모듈 메모리 영역에 바이너리 모듈 파일을 할당 및 로드하고 실행을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-161">Allocates and loads a binary module file into the module memory area and prepares it for execution.</span></span> |
| <span data-ttu-id="345d2-162">***txm_module_manager_in_place_load.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-162">***txm_module_manager_in_place_load.c***</span></span> | <span data-ttu-id="345d2-163">모듈 데이터 영역을 할당하고 제공된 코드 주소로부터 모듈 실행을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-163">Allocates the module data area and prepares for module execution from the supplied code address.</span></span> |
| <span data-ttu-id="345d2-164">***txm_module_manager_initialize.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-164">***txm_module_manager_initialize.c***</span></span> | <span data-ttu-id="345d2-165">모듈 로드 및 실행에 사용 가능한 모듈 메모리 영역의 지정을 포함하여, 모듈 관리자를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-165">Initializes the Module Manager, including specification of the module memory area available for loading and running modules.</span></span> |
| <span data-ttu-id="345d2-166">\***txm_module_manager_initialize_mmu.c** _</span><span class="sxs-lookup"><span data-stu-id="345d2-166">\***txm_module_manager_initialize_mmu.c** _</span></span> | <span data-ttu-id="345d2-167">MMU를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-167">Initialize MMU.</span></span> <span data-ttu-id="345d2-168">사용자는 자신의 메모리 맵에 따라 이 파일을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-168">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="345d2-169">_ 이 파일은 Cortex-A7/ARM에만 있음\*</span><span class="sxs-lookup"><span data-stu-id="345d2-169">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="345d2-170">\***txm_module_manager_mm_initialize.c** _</span><span class="sxs-lookup"><span data-stu-id="345d2-170">\***txm_module_manager_mm_initialize.c** _</span></span> | <span data-ttu-id="345d2-171">MPU/MMU를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-171">Initialize MPU/MMU.</span></span> <span data-ttu-id="345d2-172">사용자는 자신의 메모리 맵에 따라 이 파일을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-172">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="345d2-173">_ 이 파일은 Cortex-A7/ARM에만 있음\*</span><span class="sxs-lookup"><span data-stu-id="345d2-173">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="345d2-174">***txm_module_manager_kernel_dispatch.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-174">***txm_module_manager_kernel_dispatch.c***</span></span> | <span data-ttu-id="345d2-175">요청 ID를 기준으로 모듈 API 요청을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-175">Handles the module API requests, based on the request ID.</span></span> |
| <span data-ttu-id="345d2-176">***txm_module_manager_maximum_module_priority_set.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-176">***txm_module_manager_maximum_module_priority_set.c***</span></span> | <span data-ttu-id="345d2-177">모듈에서 허용되는 최대 스레드 우선 순위를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-177">Sets the maximum thread priority allowed in a module.</span></span> |
| <span data-ttu-id="345d2-178">***txm_module_manager_memory_fault_handler.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-178">***txm_module_manager_memory_fault_handler.c***</span></span> | <span data-ttu-id="345d2-179">실행 모듈에서 검색된 메모리 오류를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-179">Handles memory faults detected in an executing module.</span></span> |
| <span data-ttu-id="345d2-180">***txm_module_manager_memory_fault_notify.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-180">***txm_module_manager_memory_fault_notify.c***</span></span> | <span data-ttu-id="345d2-181">메모리 오류가 발생할 때마다 애플리케이션 알림 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-181">Registers an application notification callback whenever a memory fault occurs.</span></span> |
| <span data-ttu-id="345d2-182">***txm_module_manager_memory_load.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-182">***txm_module_manager_memory_load.c***</span></span> | <span data-ttu-id="345d2-183">모듈의 코드와 데이터를 할당 및 로드하고 모듈 실행을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-183">Allocates and loads a module's code and data and prepares the module for execution.</span></span> |
| <span data-ttu-id="345d2-184">***txm_module_manager_mm_register_setup.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-184">***txm_module_manager_mm_register_setup.c***</span></span> | <span data-ttu-id="345d2-185">코드와 데이터가 로드된 위치에 따라 모듈에 대해 MPU/MMU 레지스터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-185">Sets up MPU/MMU registers for the module based on where the code and data are loaded.</span></span> |
| <span data-ttu-id="345d2-186">***txm_module_manager_object_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-186">***txm_module_manager_object_allocate.c***</span></span> | <span data-ttu-id="345d2-187">모듈 개체에 대해 메모리를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-187">Allocates memory for a module object.</span></span> |
| <span data-ttu-id="345d2-188">***txm_module_manager_object_deallocate.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-188">***txm_module_manager_object_deallocate.c***</span></span> | <span data-ttu-id="345d2-189">모듈 개체에 대해 메모리를 할당 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-189">Deallocates memory for a module object.</span></span> |
| <span data-ttu-id="345d2-190">***txm_module_manager_object_pointer_get.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-190">***txm_module_manager_object_pointer_get.c***</span></span> | <span data-ttu-id="345d2-191">제공된 개체 형식과 이름을 검색하고, 찾으면 개체 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-191">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> |
| <span data-ttu-id="345d2-192">***txm_module_manager_object_pointer_get_extended.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-192">***txm_module_manager_object_pointer_get_extended.c***</span></span> | <span data-ttu-id="345d2-193">제공된 개체 형식과 이름을 검색하고, 찾으면 개체 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-193">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> <span data-ttu-id="345d2-194">안전을 위해 지정된 이름 길이</span><span class="sxs-lookup"><span data-stu-id="345d2-194">Name length specified for safety.</span></span> |
| <span data-ttu-id="345d2-195">***txm_module_manager_object_pool_create.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-195">***txm_module_manager_object_pool_create.c***</span></span>  | <span data-ttu-id="345d2-196">애플리케이션이 할당할 수 있게 모듈의 데이터 영역 밖에 개체 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-196">Creates a pool of objects outside the module's data area that module applications can allocate from.</span></span> |
| <span data-ttu-id="345d2-197">***txm_module_manager_properties_get.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-197">***txm_module_manager_properties_get.c***</span></span> | <span data-ttu-id="345d2-198">지정한 모듈의 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-198">Gets the properties of the specified module.</span></span> |
| <span data-ttu-id="345d2-199">***txm_module_manager_queue_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-199">***txm_module_manager_queue_notify_trampoline.c***</span></span> | <span data-ttu-id="345d2-200">ThreadX로부터의 큐 호출을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-200">Processes the queue notification call from ThreadX.</span></span> |
| <span data-ttu-id="345d2-201">***txm_module_manager_semaphore_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-201">***txm_module_manager_semaphore_notify_trampoline.c***</span></span> | <span data-ttu-id="345d2-202">ThreadX로부터의 세마포 Put 알림 호출을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-202">Processes the semaphore put notification call from ThreadX.</span></span>|
| <span data-ttu-id="345d2-203">***txm_module_manager_start.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-203">***txm_module_manager_start.c***</span></span> | <span data-ttu-id="345d2-204">모듈 실행을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-204">Starts execution of a module.</span></span> |
| <span data-ttu-id="345d2-205">***txm_module_manager_stop.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-205">***txm_module_manager_stop.c***</span></span> | <span data-ttu-id="345d2-206">모듈의 실행을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-206">Stops execution of a module.</span></span> |
| <span data-ttu-id="345d2-207">***txm_module_manager_thread_create.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-207">***txm_module_manager_thread_create.c***</span></span> | <span data-ttu-id="345d2-208">모든 모듈 스레드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-208">Creates all module threads.</span></span> |
| <span data-ttu-id="345d2-209">***txm_module_manager_thread_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-209">***txm_module_manager_thread_notify_trampoline.c***</span></span> | <span data-ttu-id="345d2-210">ThreadX로부터의 진입/진출 알림을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-210">Processes the thread entry/exit notification call from ThreadX.</span></span> |
| <span data-ttu-id="345d2-211">***txm_module_manager_thread_reset.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-211">***txm_module_manager_thread_reset.c***</span></span> | <span data-ttu-id="345d2-212">모듈 스레드를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-212">Reset a module thread.</span></span> |
| <span data-ttu-id="345d2-213">***txm_module_manager_timer_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-213">***txm_module_manager_timer_notify_trampoline.c***</span></span> | <span data-ttu-id="345d2-214">ThreadX로부터의 타이머 만료를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-214">Processes timer expirations from ThreadX.</span></span> |
| <span data-ttu-id="345d2-215">***txm_module_manager_unload.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-215">***txm_module_manager_unload.c***</span></span> | <span data-ttu-id="345d2-216">모듈 메모리 영역에서 모듈을 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-216">Unloads the module from the module memory area.</span></span> |
| <span data-ttu-id="345d2-217">***txm_module_manager_util.c***</span><span class="sxs-lookup"><span data-stu-id="345d2-217">***txm_module_manager_util.c***</span></span> | <span data-ttu-id="345d2-218">관리자에 대한 내부 도우미 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-218">Internal helper functions for manager.</span></span> |

## <a name="module-manager-initialization"></a><span data-ttu-id="345d2-219">모듈 관리자 초기화</span><span class="sxs-lookup"><span data-stu-id="345d2-219">Module Manager initialization</span></span>

<span data-ttu-id="345d2-220">애플리케이션의 상주 부분은 모듈 관리자 초기화 함수 ***Txm_module_manager_initialize*** 의 호출을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-220">The resident portion of the application is responsible for calling the Module Manager initialization function ***txm_module_manager_initialize***.</span></span> <span data-ttu-id="345d2-221">이 함수는 모듈 메모리 할당에 사용되는 메모리 영역 설정을 포함하여, 모듈 로드 및 언로드를 위한 내부 구조를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-221">This function sets up the internal structures for loading and unloading modules, including setting up the memory area used for allocating module memory.</span></span>

## <a name="module-manager-loading"></a><span data-ttu-id="345d2-222">모듈 관리자 로드</span><span class="sxs-lookup"><span data-stu-id="345d2-222">Module Manager loading</span></span>

<span data-ttu-id="345d2-223">모듈 관리자는 이미 상주 코드 영역에 있는 바이너리 모듈 파일이나 모듈 코드 섹션으로부터 동적으로 모듈을 모듈 메모리에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-223">The Module Manager can load modules dynamically into the module memory from binary module files or from a module code section that is already present in the resident code area.</span></span> <span data-ttu-id="345d2-224">또한 모듈 관리자는 위치에서 코드를 실행할 수 있습니다. 즉, 모듈 데이터만 모듈 메모리에 할당되며 코드 실행은 위치에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-224">In addition, the module manager can execute code in place, that is, only the module data is allocated in the module memory and the code execution is done in place.</span></span> <span data-ttu-id="345d2-225">다음 모듈 관리자 로드 API 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-225">The following Module Manager load API functions are available.</span></span>

* <span data-ttu-id="345d2-226">***txm_module_manager_file_load***</span><span class="sxs-lookup"><span data-stu-id="345d2-226">***txm_module_manager_file_load***</span></span>

* <span data-ttu-id="345d2-227">***txm_module_manager_in_place_load***</span><span class="sxs-lookup"><span data-stu-id="345d2-227">***txm_module_manager_in_place_load***</span></span>

* <span data-ttu-id="345d2-228">***txm_module_manager_memory_load***</span><span class="sxs-lookup"><span data-stu-id="345d2-228">***txm_module_manager_memory_load***</span></span>

<span data-ttu-id="345d2-229">모듈 관리자의 메모리 보호 버전은 모듈에 적합한 맞춤이 로드되고 메모리 관리 레지스터가 모듈마다 적합하게 설정되었는지도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-229">The memory protected version of the Module Manager also makes sure that the module is loaded with the proper alignment and the memory management registers are set up properly for each module.</span></span> <span data-ttu-id="345d2-230">모듈 프리앰블 옵션을 통해 메모리 보호를 사용하도록 설정하면 모듈 메모리 액세스가 모듈 코드 및 데이터 영역으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-230">When memory protection is enabled via the module preamble options, module memory access is restricted to the module code and data areas.</span></span>

## <a name="module-manager-starting"></a><span data-ttu-id="345d2-231">모듈 관리자 시작</span><span class="sxs-lookup"><span data-stu-id="345d2-231">Module Manager starting</span></span>

<span data-ttu-id="345d2-232">모듈 관리자는 ***txm_module_manager_start*** API 함수를 통해 이전에 로드된 모듈의 실행을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-232">The Module Manager initiates execution of a previously-loaded module via the ***txm_module_manager_start*** API function.</span></span> <span data-ttu-id="345d2-233">모듈 실행을 시작하기 위해 이 함수는 모듈 프리앰블에서 지정한 시작 위치에서 모듈을 입력하는 스레드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-233">To initiate module execution, this function creates a thread that enters the module at the starting location specified in the module preamble.</span></span> <span data-ttu-id="345d2-234">이 스레드의 우선 순위 및 스택 크기도 모듈 프리앰블에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-234">The priority and stack size of this thread is also specified in the module preamble.</span></span>

## <a name="module-manager-stopping"></a><span data-ttu-id="345d2-235">모듈 관리자 중지</span><span class="sxs-lookup"><span data-stu-id="345d2-235">Module Manager stopping</span></span>

<span data-ttu-id="345d2-236">모듈 관리자는 ***txm_module_manager_stop*** 함수를 통해 이전에 로드되어 실행 중인 모듈의 실행을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-236">The Module Manager terminates execution of a previously-loaded and executing module via the ***txm_module_manager_stop*** function.</span></span> <span data-ttu-id="345d2-237">이 API 함수는 먼저 초기 시작 스레드를 종료하고 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-237">This API function first terminates and deletes the initial starting thread.</span></span> <span data-ttu-id="345d2-238">모듈 프리앰블이 중지 스레드를 지정하는 경우 이 스레드를 만들고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-238">If the module preamble specifies a stop thread, this thread is created and executed.</span></span> <span data-ttu-id="345d2-239">모듈 관리자는 중지 스레드가 완료될 때까지 일정 시간 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-239">The Module Manager waits for a fixed period of time for the stop thread to complete.</span></span> <span data-ttu-id="345d2-240">완료되면 모듈이 만든 모든 시스템 리소스가 삭제되고 모듈이 유휴 상태로 들어가며, 여기서 다시 시작 또는 언로드될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-240">Once complete, all system resources created by the module are deleted and the module is placed in a dormant state, from which it can be either restarted or unloaded.</span></span>

## <a name="module-manager-unloading"></a><span data-ttu-id="345d2-241">모듈 관리자 언로드</span><span class="sxs-lookup"><span data-stu-id="345d2-241">Module Manager unloading</span></span>

<span data-ttu-id="345d2-242">모듈 관리자는 이전에 로드되었으나 실행 중이 아닌 모듈을 ***txm_module_manager_unload*** 함수를 통해 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-242">The Module Manager unloads a previously-loaded but not executing module via the ***txm_module_manager_unload*** function.</span></span> <span data-ttu-id="345d2-243">이 API는 모듈에 연결된 모든 메모리를 해제하여 향후 다른 모듈이 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-243">This API releases all memory associated with the module, freeing it for use with another module in the future.</span></span>

## <a name="module-manager-requests"></a><span data-ttu-id="345d2-244">모듈 관리자 요청</span><span class="sxs-lookup"><span data-stu-id="345d2-244">Module Manager requests</span></span>

<span data-ttu-id="345d2-245">모듈 관리자에 대한 모듈의 요청은 모듈 관리자가 모듈에 제공한 함수 포인터를 통해 모듈 관리자 발송 함수를 호출하기 위해 모든 ThreadX 호출을 매핑하는 ***txm_module.h*** 의 매크로를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-245">Requests made by modules to the Module Manager are done via macros in ***txm_module.h*** that map all ThreadX calls to call the Module Manager dispatch function via a function pointer supplied to the module by the Module Manager.</span></span>

<span data-ttu-id="345d2-246">***txm_module_application_request*** 를 호출하는 모듈을 통해 이루어지는 추가 애플리케이션 관련 서비스는 ThreadX API에 사용되는 것과 동일한 매크로 메커니즘으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-246">Additional application-specific services made via the module calling ***txm_module_application_request*** are handled by the same macro mechanism used for the ThreadX API.</span></span> <span data-ttu-id="345d2-247">기본적으로 모듈 관리자의 이 처리 함수는 비어 있고 애플리케이션 관련 요청을 처리하기 위해 필요한 코드를 애플리케이션이 추가하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-247">By default, this handling function in the Module Manager is empty and designed such that the application adds the necessary code to process the application-specific requests.</span></span>

<span data-ttu-id="345d2-248">모듈 관리자가 요청을 구현하지 않으면 모듈 관리자가 **TX_NOT_AVAILABLE** 오류 상태 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-248">If the request is not implemented by the Module Manager, a value of **TX_NOT_AVAILABLE** error status is returned by the Module Manager.</span></span> <span data-ttu-id="345d2-249">모듈의 액세스 범위를 벗어나는 작업을 모듈이 요청하는 경우에도 이 오류 코드가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-249">This error code is also returned if the module requests an operation that is outside the scope of the module's access.</span></span> <span data-ttu-id="345d2-250">예를 들어, 모듈은 타이머 제어 블록이 있는 타이머나, 모듈 코드 영역 외부의 콜백 주소를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-250">For example, a module is not allowed to create a timer with the timer control block or callback address outside of the module's code area.</span></span>

## <a name="module-manager-example"></a><span data-ttu-id="345d2-251">모듈 관리자 예제</span><span class="sxs-lookup"><span data-stu-id="345d2-251">Module Manager example</span></span>

<span data-ttu-id="345d2-252">다음은 이전에 2장에서 정의한 예제 모듈을 실행하는 모듈 관리자 코드의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-252">The following is an example of Module Manager code that launches the example module previously defined in Chapter 2.</span></span> <span data-ttu-id="345d2-253">디버거에서는 모듈이 이미 ROM 주소 0x00800000에 로그된 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-253">It is assumed that the module is already loaded, presumably by the debugger, at ROM address 0x00800000.</span></span>

```c
#include "tx_api.h"
#include "txm_module.h"

#define DEMO_STACK_SIZE 1024

/* Define the ThreadX object control blocks. */
TX_THREAD   module_manager;

/* Define thread prototype. */
void        module_manager_entry(ULONG thread_input);

/* Define the module object pool area. */
UCHAR       object_memory[8192];

/* Define the module data pool area. */
#define MODULE_DATA_SIZE 65536
UCHAR       module_data_area[MODULE_DATA_SIZE];

/* Define module instances. */
TXM_MODULE_INSTANCE     my_module1;
TXM_MODULE_INSTANCE     my_module2;

/* Define the count of memory faults. */
ULONG memory_faults;

/* Define fault handler. */
VOID module_fault_handler(TX_THREAD *thread, TXM_MODULE_INSTANCE *module)
{
    /* Just increment the fault counter. */
    memory_faults++;
}

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    /* Create the module manager thread. */
    tx_thread_create(&module_manager, "Module Manager Thread", module_manager_entry, 0,
                    first_unused_memory, DEMO_STACK_SIZE,
                    1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

/* Define the test threads. */
void module_manager_entry(ULONG thread_input)
{
    /* Initialize the module manager. */
    txm_module_manager_initialize((VOID *) module_data_area, MODULE_DATA_SIZE);

    /* Create a pool for module objects. */
    txm_module_manager_object_pool_create(object_memory, sizeof(object_memory));

    /* Register a fault handler. */
    txm_module_manager_memory_fault_notify(module_fault_handler);

    /* Load the module that is already there,
        in this example it is placed at 0x00800000. */
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Load a second instance of the module. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);

    /* Enable shared memory region for module2. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);

    /* Start the modules. */
    txm_module_manager_start(&my_module1);
    txm_module_manager_start(&my_module2);

    /* Sleep for a while and let the modules run... */
    tx_thread_sleep(300);

    /* Stop the modules. */
    txm_module_manager_stop(&my_module1);
    txm_module_manager_stop(&my_module2);

    /* Unload the modules. */
    txm_module_manager_unload(&my_module1);
    txm_module_manager_unload(&my_module2);

    /* Reload the modules. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Give both modules shared memory. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);
    txm_module_manager_external_memory_enable(&my_module1, (void*)0x20600000, 0x010000, 0x3F);

    /* Set maximum module1 priority to 5. */
    txm_module_manager_maximum_module_priority_set(&my_module1, 5);

    /* Start the modules again. */
    txm_module_manager_start(&my_module2);
    txm_module_manager_start(&my_module1);

    /* Now just spin... */
    while(1)
    {
        tx_thread_sleep(100);

        /* Threads 0 and 5 in module1 are not created because they violate the maximum priority. */
    }
}
```

## <a name="module-manager-building"></a><span data-ttu-id="345d2-254">모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="345d2-254">Module Manager building</span></span>

<span data-ttu-id="345d2-255">***txm_module_manager_\**** 원본 파일을 ThreadX 라이브러리에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-255">The ***txm_module_manager_\**** source files must be added to the ThreadX library.</span></span>

<span data-ttu-id="345d2-256">ThreadX 모듈 관리자 애플리케이션은 실제로 하나 이상의 애플리케이션 파일이 ThreadX 라이브러리 ***tx.a*** 에 하나로 연결된 표준 ThreadX 애플리케이션과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-256">A ThreadX Module Manager application is effectively the same as a standard ThreadX application, which is one or more application files linked together with the ThreadX library ***tx.a***.</span></span> <span data-ttu-id="345d2-257">모듈 관리자 애플리케이션 빌드는 사용 중인 도구 체인에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="345d2-257">Building a module manager application is dependent on the tool chain being used.</span></span> <span data-ttu-id="345d2-258">포트 관련 예제는 [부록](appendix.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="345d2-258">See [appendix](appendix.md) for port-specific examples.</span></span>
