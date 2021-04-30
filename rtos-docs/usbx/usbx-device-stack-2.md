---
title: 2장 - Azure RTOS USBX 디바이스 스택 설치
description: Azure RTOS USBX 디바이스 스택을 설치하는 방법과 설치하기 전에 고려해야 할 중요한 호스트 고려 사항을 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dd58f77130fa252be9163bd70c29f7deee400d30
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549779"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a><span data-ttu-id="00a40-103">2장 - Azure RTOS USBX 디바이스 스택 설치</span><span class="sxs-lookup"><span data-stu-id="00a40-103">Chapter 2 - Azure RTOS USBX Device Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="00a40-104">호스트 고려 사항</span><span class="sxs-lookup"><span data-stu-id="00a40-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="00a40-105">컴퓨터 유형</span><span class="sxs-lookup"><span data-stu-id="00a40-105">Computer Type</span></span>

<span data-ttu-id="00a40-106">임베디드 개발은 일반적으로 Windows PC 또는 Unix 호스트 컴퓨터에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="00a40-107">애플리케이션이 컴파일되거나, 링크되거나 호스트에 배치된 후 실행할 수 있도록 대상 하드웨어에 다운로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="00a40-108">인터페이스 다운로드</span><span class="sxs-lookup"><span data-stu-id="00a40-108">Download Interfaces</span></span>

<span data-ttu-id="00a40-109">병렬 인터페이스, USB, 이더넷이 점점 대중화되고 있지만 일반적으로 대상 다운로드는 RS-232 직렬 인터페이스를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-109">Usually the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="00a40-110">사용 가능한 옵션은 개발 도구 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00a40-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="00a40-111">디버깅 도구</span><span class="sxs-lookup"><span data-stu-id="00a40-111">Debugging Tools</span></span>

<span data-ttu-id="00a40-112">디버깅은 일반적으로 프로그램 이미지 다운로드와 동일한 링크를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="00a40-113">대상에서 실행되는 소형 모니터 프로그램부터 BDM(Background Debug Monitor) 및 ICE(In-Circuit Emulator) 도구까지 다양한 디버거가 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="00a40-114">ICE 도구는 실제 대상 하드웨어에 대해 가장 강력한 디버깅을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="00a40-115">필요한 하드 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="00a40-115">Required Hard Disk Space</span></span>

<span data-ttu-id="00a40-116">USBX의 소스 코드는 ASCII 형식으로 제공되며 호스트 컴퓨터의 하드 디스크에 약 500KB 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

### <a name="target-considerations"></a><span data-ttu-id="00a40-117">대상 고려 사항</span><span class="sxs-lookup"><span data-stu-id="00a40-117">Target Considerations</span></span>

<span data-ttu-id="00a40-118">USBX에는 호스트 모드의 대상에 24KB에서 64KB 사이의 ROM(읽기 전용 메모리)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="00a40-119">필요한 메모리 양은 사용된 컨트롤러 유형 및 USBX에 연결된 USB 클래스에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="00a40-120">또한 USBX 글로벌 데이터 구조 및 메모리 풀에 대상의 32KB RAM(Random Access Memory)이 추가로 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="00a40-121">이 메모리 풀은 USB의 예상 디바이스 수 및 USB 컨트롤러 유형에 따라 조정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="00a40-122">USBX 디바이스 측에는 디바이스 컨트롤러 유형에 따라 약 10~12K의 ROM이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="00a40-123">RAM 메모리 사용량은 디바이스에서 에뮬레이트되는 클래스 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="00a40-124">또한 USBX에는 ThreadX 세마포, 뮤텍스, 다중 스레드 보호를 위한 스레드, USB 버스 토폴로지 모니터링을 위한 I/O 일시 중단 및 정기적 처리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="00a40-125">제품 배포</span><span class="sxs-lookup"><span data-stu-id="00a40-125">Product Distribution</span></span>

<span data-ttu-id="00a40-126">Azure RTOS USBX는 <https://github.com/azure-rtos/usbx/>에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="00a40-127">다음은 리포지토리에 있는 몇 가지 중요한 파일 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-127">The following is a list of several important files in the repository.</span></span>

* <span data-ttu-id="00a40-128">***ux_api.h***: 이 C 헤더 파일에는 모든 시스템 이큐에이트, 데이터 구조 및 서비스 프로토타입이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
* <span data-ttu-id="00a40-129">***ux_port.h***: 이 C 헤더 파일에는 모든 개발 도구 관련 데이터 정의 및 구조가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
* <span data-ttu-id="00a40-130">***ux.lib***: USBX C 라이브러리의 이진 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-130">***ux.lib***:  This is the binary version of the USBX C library.</span></span> <span data-ttu-id="00a40-131">표준 패키지로 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-131">It is distributed with the standard package.</span></span>
* <span data-ttu-id="00a40-132">***demo_usbx.c***: 간단한 USBX 데모가 포함된 C 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="00a40-133">모든 파일 이름은 소문자로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-133">All filenames are in lower-case.</span></span> <span data-ttu-id="00a40-134">이 명명 규칙을 사용하면 명령어를 Unix 개발 플랫폼으로 쉽게 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="00a40-135">USBX 설치</span><span class="sxs-lookup"><span data-stu-id="00a40-135">USBX Installation</span></span>

<span data-ttu-id="00a40-136">USBX는 GitHub 리포지토리를 로컬 컴퓨터에 복제하여 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="00a40-137">다음은 PC에서 USBX 리포지토리의 복제본을 만들기 위한 일반적인 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="00a40-138">또는 GitHub 기본 페이지의 다운로드 단추를 사용하여 리포지토리의 복사본을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="00a40-139">또한 온라인 리포지토리의 프런트 페이지에서 USBX 라이브러리를 빌드하기 위한 지침을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="00a40-140">다음 일반 지침은 거의 모든 설치에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="00a40-141">이전에 호스트 하드 드라이브에 ThreadX를 설치한 것과 동일한 디렉터리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="00a40-142">모든 USBX 이름은 고유하며 이전 USBX 설치를 방해하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
1. <span data-ttu-id="00a40-143">_\*_tx_application_define_\*\*의 시작 지점 또는 그 부근에 \***ux_system_initialize** _에 대한 호출을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _*_tx_application_define_\*\*.</span></span> <span data-ttu-id="00a40-144">여기에서 USBX 리소스가 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-144">This is where the USBX resources are initialized.</span></span>
1. <span data-ttu-id="00a40-145">***ux_device_stack_initialize*** 에 대한 호출을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-145">Add a call to \***ux_device_stack_initialize\*.**</span></span>
1. <span data-ttu-id="00a40-146">필요한 USBX 클래스를 초기화하기 위해 하나 이상의 호출을 추가합니다(호스트 및/또는 디바이스 클래스).</span><span class="sxs-lookup"><span data-stu-id="00a40-146">Add one or more calls to initialize the required USBX classes (either host and/or devices classes)</span></span>
1. <span data-ttu-id="00a40-147">시스템에서 사용 가능한 디바이스 컨트롤러를 초기화하기 위해 하나 이상의 호출을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-147">Add one or more calls to initialize the device controller available in the system.</span></span>
1. <span data-ttu-id="00a40-148">하위 수준 하드웨어 초기화를 추가하고 벡터 라우팅을 인터럽트하도록 tx_low_level_initialize.c 파일을 수정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-148">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="00a40-149">이것은 하드웨어 플랫폼과 관련되며 여기에서 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-149">This is specific to the hardware platform and will not be discussed here.|</span></span>
1. <span data-ttu-id="00a40-150">애플리케이션 소스 코드를 컴파일하고 USBX 및 ThreadX 런타임 라이브러리(USB 스토리지 클래스 및/또는 USB 네트워크 클래스를 컴파일하려는 경우 FileX 및/또는 Netx도 필요할 수 있음), ux.a(또는 ux.lib) 및 tx.a(또는 tx.lib)를 사용하여 링크합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-150">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="00a40-151">결과를 대상에 다운로드하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-151">The resulting can be downloaded to the target and executed!</span></span>

## <a name="configuration-options"></a><span data-ttu-id="00a40-152">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="00a40-152">Configuration Options</span></span>

<span data-ttu-id="00a40-153">USBX 라이브러리를 빌드하는 데에는 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-153">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="00a40-154">모든 옵션은 ***ux_user.h*** 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-154">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="00a40-155">아래 목록에서는 각 구성 옵션에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-155">The list below details each configuration option.</span></span>

| <span data-ttu-id="00a40-156">구성&nbsp;옵션</span><span class="sxs-lookup"><span data-stu-id="00a40-156">Configuration&nbsp;Option</span></span> | <span data-ttu-id="00a40-157">Description</span><span class="sxs-lookup"><span data-stu-id="00a40-157">Description</span></span> |
| --- | --- |
| <span data-ttu-id="00a40-158">**UX_PERIODIC_RATE**</span><span class="sxs-lookup"><span data-stu-id="00a40-158">**UX_PERIODIC_RATE**</span></span> | <span data-ttu-id="00a40-159">이 값은 특정 하드웨어 플랫폼의 초당 틱 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-159">This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="00a40-160">기본값은 1000이며 밀리초당 1틱을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-160">The default is 1000 indicating 1 tick per millisecond.</span></span> |
| <span data-ttu-id="00a40-161">**UX_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="00a40-161">**UX_THREAD_STACK_SIZE**</span></span> | <span data-ttu-id="00a40-162">이 값은 USBX 스레드의 스택 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-162">This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="00a40-163">일반적으로 사용된 프로세스 및 호스트 컨트롤러에 따라 1024바이트 또는 2048바이트일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-163">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span> |
| <span data-ttu-id="00a40-164">**UX_THREAD_PRIORITY_ENUM**</span><span class="sxs-lookup"><span data-stu-id="00a40-164">**UX_THREAD_PRIORITY_ENUM**</span></span> | <span data-ttu-id="00a40-165">버스 토폴로지를 모니터링하는 USBX 열거형 스레드의 ThreadX 우선 순위 값입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-165">This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span> |
| <span data-ttu-id="00a40-166">**UX_THREAD_PRIORITY_CLASS**</span><span class="sxs-lookup"><span data-stu-id="00a40-166">**UX_THREAD_PRIORITY_CLASS**</span></span> | <span data-ttu-id="00a40-167">표준 USBX 스레드의 ThreadX 우선 순위 값입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-167">This is the ThreadX priority value for the standard USBX threads.</span></span> |
| <span data-ttu-id="00a40-168">**UX_THREAD_PRIORITY_KEYBOARD**</span><span class="sxs-lookup"><span data-stu-id="00a40-168">**UX_THREAD_PRIORITY_KEYBOARD**</span></span> | <span data-ttu-id="00a40-169">USBX HID 키보드 클래스의 ThreadX 우선 순위 값입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-169">This is the ThreadX priority value for the USBX HID keyboard class.</span></span> |
| <span data-ttu-id="00a40-170">**UX_THREAD_PRIORITY_DCD**</span><span class="sxs-lookup"><span data-stu-id="00a40-170">**UX_THREAD_PRIORITY_DCD**</span></span> | <span data-ttu-id="00a40-171">디바이스 컨트롤러 스레드의 ThreadX 우선 순위 값입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-171">This is the ThreadX priority value for the device controller thread.</span></span> |
| <span data-ttu-id="00a40-172">**UX_NO_TIME_SLICE**</span><span class="sxs-lookup"><span data-stu-id="00a40-172">**UX_NO_TIME_SLICE**</span></span> | <span data-ttu-id="00a40-173">이 값은 스레드에 사용되는 시간 조각을 실제로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-173">This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="00a40-174">예를 들어, 0으로 정의된 경우 ThreadX 대상 포트는 시간 조각을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-174">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span> |
| <span data-ttu-id="00a40-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span><span class="sxs-lookup"><span data-stu-id="00a40-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span></span> | <span data-ttu-id="00a40-176">ux_device_stack_class_register를 통해 등록될 수 있는 USBX 클래스의 최대 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-176">This is the maximum number of USBX classes that can be registered via ux_device_stack_class_register.</span></span> |
| <span data-ttu-id="00a40-177">**UX_MAX_SLAVE_LUN**</span><span class="sxs-lookup"><span data-stu-id="00a40-177">**UX_MAX_SLAVE_LUN**</span></span> | <span data-ttu-id="00a40-178">이 값은 디바이스 스토리지 클래스 드라이버에 제공된 현재 SCSI 논리적 단위 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-178">This value represents the current number of SCSI logical units represented in the device storage class driver.</span></span> |
| <span data-ttu-id="00a40-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span><span class="sxs-lookup"><span data-stu-id="00a40-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span></span> | <span data-ttu-id="00a40-180">정의된 경우 스토리지 클래스가 MMC(다중 미디어 명령), 즉 DVD-ROM을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-180">If defined, the storage class will handle Multi-Media Commands (MMC) that is, DVD-ROM.</span></span> |
| <span data-ttu-id="00a40-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span><span class="sxs-lookup"><span data-stu-id="00a40-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span></span> | <span data-ttu-id="00a40-182">이 값은 CDC-ECM 클래스의 패킷 풀에 있는 NetX 패킷 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-182">This value represents the number of NetX packets in the CDC-ECM class' packet pool.</span></span> <span data-ttu-id="00a40-183">기본값은 16입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-183">The default is 16.</span></span> |
| <span data-ttu-id="00a40-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="00a40-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span></span> | <span data-ttu-id="00a40-185">이 값은 디바이스 스택에서 제어 엔드포인트에 수신된 최대 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-185">This value represents the maximum number of bytes received on a control endpoint in the device stack.</span></span> <span data-ttu-id="00a40-186">기본값은 256바이트이지만 메모리가 제약된 환경에서 감소될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-186">The default is 256 bytes but can be reduced in memory constraint environments.</span></span> |
| <span data-ttu-id="00a40-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="00a40-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span></span> | <span data-ttu-id="00a40-188">이 값은 HID 보고서의 최대 길이(바이트)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-188">This value represents the maximum length in bytes of a HID report.</span></span> |
| <span data-ttu-id="00a40-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span><span class="sxs-lookup"><span data-stu-id="00a40-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span></span> | <span data-ttu-id="00a40-190">이 값은 한 번에 큐에 넣을 수 있는 HID 보고서의 최대 개수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-190">This value represents the maximum number of HID reports that can be queued at once.</span></span> |
| <span data-ttu-id="00a40-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="00a40-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span></span> | <span data-ttu-id="00a40-192">이 값은 디바이스 스택에서 대량 엔드포인트에 수신되는 최대 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-192">This value represents the maximum number of bytes received on a bulk endpoint in the device stack.</span></span> <span data-ttu-id="00a40-193">기본값은 4096바이트이지만 메모리가 제약된 환경에서 감소될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-193">The default is 4096 bytes but can be reduced in memory constraint environments.</span></span> |

## <a name="source-code-tree"></a><span data-ttu-id="00a40-194">소스 코드 트리</span><span class="sxs-lookup"><span data-stu-id="00a40-194">Source Code Tree</span></span>

<span data-ttu-id="00a40-195">USBX 파일은 여러 디렉터리에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-195">The USBX files are provided in several directories.</span></span>

![소스 코드 트리](media/usbx-device-stack/source-code-tree.png)

<span data-ttu-id="00a40-197">이름으로 파일을 인식할 수 있도록 다음 규칙이 채택되었습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-197">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="00a40-198">파일 접미사 이름</span><span class="sxs-lookup"><span data-stu-id="00a40-198">File Suffix Name</span></span>  | <span data-ttu-id="00a40-199">파일 설명</span><span class="sxs-lookup"><span data-stu-id="00a40-199">File description</span></span>                          |
| ----------------- | ----------------------------------------- |
| <span data-ttu-id="00a40-200">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="00a40-200">ux_host_stack</span></span>   | <span data-ttu-id="00a40-201">usbx 호스트 스택 코어 파일</span><span class="sxs-lookup"><span data-stu-id="00a40-201">usbx host stack core files</span></span>                |
| <span data-ttu-id="00a40-202">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="00a40-202">ux_host_class</span></span>   | <span data-ttu-id="00a40-203">usbx 호스트 스택 클래스 파일</span><span class="sxs-lookup"><span data-stu-id="00a40-203">usbx host stack classes files</span></span>             |
| <span data-ttu-id="00a40-204">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="00a40-204">ux_hcd</span></span>           | <span data-ttu-id="00a40-205">usbx 호스트 스택 컨트롤러 드라이버 파일</span><span class="sxs-lookup"><span data-stu-id="00a40-205">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="00a40-206">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="00a40-206">ux_device_stack</span></span> | <span data-ttu-id="00a40-207">usbx 디바이스 스택 코어 파일</span><span class="sxs-lookup"><span data-stu-id="00a40-207">usbx device stack core files</span></span>              |
| <span data-ttu-id="00a40-208">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="00a40-208">ux_device_class</span></span> | <span data-ttu-id="00a40-209">usbx 디바이스 스택 클래스 파일</span><span class="sxs-lookup"><span data-stu-id="00a40-209">usbx device stack classes files</span></span>           |
| <span data-ttu-id="00a40-210">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="00a40-210">ux_dcd</span></span>           | <span data-ttu-id="00a40-211">usbx 디바이스 스택 컨트롤러 드라이버 파일</span><span class="sxs-lookup"><span data-stu-id="00a40-211">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="00a40-212">ux_otg</span><span class="sxs-lookup"><span data-stu-id="00a40-212">ux_otg</span></span>           | <span data-ttu-id="00a40-213">usbx otg 컨트롤러 드라이버 관련 파일</span><span class="sxs-lookup"><span data-stu-id="00a40-213">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="00a40-214">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="00a40-214">ux_pictbridge</span></span>    | <span data-ttu-id="00a40-215">usbx pictbridge 파일</span><span class="sxs-lookup"><span data-stu-id="00a40-215">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="00a40-216">ux_utility</span><span class="sxs-lookup"><span data-stu-id="00a40-216">ux_utility</span></span>       | <span data-ttu-id="00a40-217">usbx 유틸리티 함수</span><span class="sxs-lookup"><span data-stu-id="00a40-217">usbx utility functions</span></span>                    |
| <span data-ttu-id="00a40-218">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="00a40-218">demo_usbx</span></span>        | <span data-ttu-id="00a40-219">USBX의 데모 파일</span><span class="sxs-lookup"><span data-stu-id="00a40-219">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="00a40-220">USBX 리소스 초기화</span><span class="sxs-lookup"><span data-stu-id="00a40-220">Initialization of USBX resources</span></span>

<span data-ttu-id="00a40-221">USBX에는 자체 메모리 관리자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-221">USBX has its own memory manager.</span></span> <span data-ttu-id="00a40-222">USBX의 호스트 또는 디바이스 측이 초기화되기 전 USBX에 메모리를 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-222">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="00a40-223">USBX 메모리 관리자는 메모리를 캐시할 수 있는 시스템을 수용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-223">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="00a40-224">다음 함수는 일반 메모리 128K로 USBX 메모리 리소스를 초기화하고 캐시 안전 메모리를 위한 별도의 풀은 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-224">The following function initializes USBX memory resources with 128 K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="00a40-225">ux_system_initialize의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-225">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

<span data-ttu-id="00a40-226">입력 매개 변수:</span><span class="sxs-lookup"><span data-stu-id="00a40-226">Input parameters:</span></span>

| <span data-ttu-id="00a40-227">매개 변수</span><span class="sxs-lookup"><span data-stu-id="00a40-227">Parameter</span></span>                          | <span data-ttu-id="00a40-228">Description</span><span class="sxs-lookup"><span data-stu-id="00a40-228">Description</span></span>                             |
| ---------------------------------- | --------------------------------------- |
| <span data-ttu-id="00a40-229">VOID \*regular_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="00a40-229">VOID \*regular_memory_pool_start</span></span>    | <span data-ttu-id="00a40-230">일반 메모리 풀의 시작 부분</span><span class="sxs-lookup"><span data-stu-id="00a40-230">Beginning of the regular memory pool</span></span>    |
| <span data-ttu-id="00a40-231">ULONG regular_memory_size</span><span class="sxs-lookup"><span data-stu-id="00a40-231">ULONG regular_memory_size</span></span>          | <span data-ttu-id="00a40-232">일반 메모리 풀의 크기</span><span class="sxs-lookup"><span data-stu-id="00a40-232">Size of the regular memory pool</span></span>         |
| <span data-ttu-id="00a40-233">VOID \*cache_safe_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="00a40-233">VOID \*cache_safe_memory_pool_start</span></span> | <span data-ttu-id="00a40-234">캐시 안전 메모리 풀의 시작 부분</span><span class="sxs-lookup"><span data-stu-id="00a40-234">Beginning of the cache safe memory pool</span></span> |
| <span data-ttu-id="00a40-235">ULONG cache_safe_memory_size</span><span class="sxs-lookup"><span data-stu-id="00a40-235">ULONG cache_safe_memory_size</span></span>       | <span data-ttu-id="00a40-236">캐시 안전 메모리 풀의 크기</span><span class="sxs-lookup"><span data-stu-id="00a40-236">Size of the cache safe memory pool</span></span>      |

<span data-ttu-id="00a40-237">일부 시스템에는 캐시 안전 메모리 정의가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="00a40-238">이러한 시스템에서 메모리 포인터 초기화 중 전달되는 값은 UX_NULL로 설정되고 풀 크기는 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="00a40-239">그런 다음, USBX는 캐시 안전 풀 대신 일반 메모리 풀을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="00a40-240">일반 메모리가 캐시 안전이 아니고 컨트롤러가 DMA 메모리를 수행해야 하는 시스템에서는 캐시 안전 영역에 메모리 풀을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="00a40-241">USBX 리소스 초기화 해제</span><span class="sxs-lookup"><span data-stu-id="00a40-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="00a40-242">해당 리소스를 해제하여 USBX를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="00a40-243">USBX를 종료하기 전 모든 클래스 및 컨트롤러 리소스를 적절하게 종료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="00a40-244">다음 함수는 USBX 메모리 리소스를 초기화 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-244">The following function uninitializes USBX memory resources:</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="00a40-245">ux_system_initialize의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-245">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a><span data-ttu-id="00a40-246">USB 디바이스 컨트롤러 정의</span><span class="sxs-lookup"><span data-stu-id="00a40-246">Definition of USB Device Controller</span></span>

<span data-ttu-id="00a40-247">언제든지 USB 디바이스 컨트롤러 하나만 디바이스 모드로 작동하도록 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-247">Only one USB device controller can be defined at any time to operate in device mode.</span></span> <span data-ttu-id="00a40-248">애플리케이션 초기화 파일에 이 정의가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="00a40-249">다음 줄은 일반 USB 컨트롤러에 대한 정의를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-249">The following line performs the definition of a generic usb controller:</span></span>

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

<span data-ttu-id="00a40-250">USB 디바이스 초기화에는 다음 프로토타입이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-250">The USB device initialization has the following prototype:</span></span>

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

<span data-ttu-id="00a40-251">다음 매개 변수 사용:</span><span class="sxs-lookup"><span data-stu-id="00a40-251">with the following parameters:</span></span>

| <span data-ttu-id="00a40-252">매개 변수</span><span class="sxs-lookup"><span data-stu-id="00a40-252">Pararmeter</span></span>               | <span data-ttu-id="00a40-253">Description</span><span class="sxs-lookup"><span data-stu-id="00a40-253">Description</span></span>                      |
| ------------------------ | -------------------------------- |
| <span data-ttu-id="00a40-254">ULONG dcd_io</span><span class="sxs-lookup"><span data-stu-id="00a40-254">ULONG dcd_io</span></span>            | <span data-ttu-id="00a40-255">컨트롤러 IO의 주소</span><span class="sxs-lookup"><span data-stu-id="00a40-255">Address of the controller IO</span></span>     |
| <span data-ttu-id="00a40-256">ULONG dcd_irq</span><span class="sxs-lookup"><span data-stu-id="00a40-256">ULONG dcd_irq</span></span>           | <span data-ttu-id="00a40-257">컨트롤러에서 사용하는 인터럽트</span><span class="sxs-lookup"><span data-stu-id="00a40-257">Interrupt used by the controller</span></span> |
| <span data-ttu-id="00a40-258">ULONG dcd_vbus_address</span><span class="sxs-lookup"><span data-stu-id="00a40-258">ULONG dcd_vbus_address</span></span> | <span data-ttu-id="00a40-259">VBUS GPIO의 주소</span><span class="sxs-lookup"><span data-stu-id="00a40-259">Address of the VBUS GPIO</span></span>         |

<span data-ttu-id="00a40-260">다음 예제는 스토리지 디바이스 클래스 및 일반 컨트롤러를 사용하여 디바이스 모드에서 USBX를 초기화하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-260">The following example is the initialization of USBX in device mode with the storage device class and a generic controller:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a><span data-ttu-id="00a40-261">문제 해결</span><span class="sxs-lookup"><span data-stu-id="00a40-261">Troubleshooting</span></span>

<span data-ttu-id="00a40-262">USBX는 데모 파일 및 시뮬레이션 환경으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-262">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="00a40-263">항상 대상 하드웨어 또는 특정 데모 플랫폼에서 데모 플랫폼을 먼저 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-263">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="00a40-264">USBX 버전 ID</span><span class="sxs-lookup"><span data-stu-id="00a40-264">USBX Version ID</span></span>

<span data-ttu-id="00a40-265">USBX의 현재 버전은 런타임 중 사용자 및 애플리케이션 모두에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-265">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="00a40-266">프로그래머는 \***ux_port.h** _ 파일을 조사하여 USBX 버전을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-266">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="00a40-267">또한 이 파일에는 해당 포트의 버전 기록도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-267">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="00a40-268">애플리케이션 소프트웨어는 _\*_ux_port.h_\*\*에 정의된 전체 문자열 _ \*_ _ux_version_id_\* _를 조사하여 USBX 버전을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00a40-268">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
