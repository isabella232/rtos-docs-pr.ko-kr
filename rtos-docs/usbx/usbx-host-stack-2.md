---
title: 챕터 2 - Azure RTOS USBX 호스트 스택 설치
description: USBX 호스트 스택을 설치하는 방법을 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 4c33f95b8ac268c557fd947a1303ec3af315a37e
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377087"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a><span data-ttu-id="2f53a-103">챕터 2 - Azure RTOS USBX 호스트 스택 설치</span><span class="sxs-lookup"><span data-stu-id="2f53a-103">Chapter 2 - Azure RTOS USBX Host Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="2f53a-104">호스트 고려 사항</span><span class="sxs-lookup"><span data-stu-id="2f53a-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="2f53a-105">컴퓨터 유형</span><span class="sxs-lookup"><span data-stu-id="2f53a-105">Computer Type</span></span>

<span data-ttu-id="2f53a-106">임베디드 개발은 일반적으로 Windows PC 또는 Unix 호스트 컴퓨터에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="2f53a-107">애플리케이션이 컴파일되거나, 링크되거나, 호스트에 배치된 후 실행할 수 있도록 대상 하드웨어에 다운로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="2f53a-108">인터페이스 다운로드</span><span class="sxs-lookup"><span data-stu-id="2f53a-108">Download Interfaces</span></span>

<span data-ttu-id="2f53a-109">병렬 인터페이스, USB 및 이더넷이 보다 보편화되고 있지만 일반적으로 대상 다운로드는 RS-232 직렬 인터페이스를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-109">Usually, the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="2f53a-110">사용 가능한 옵션은 개발 도구 문서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f53a-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="2f53a-111">디버깅 도구</span><span class="sxs-lookup"><span data-stu-id="2f53a-111">Debugging Tools</span></span>

<span data-ttu-id="2f53a-112">디버깅은 일반적으로 프로그램 이미지 다운로드와 동일한 링크를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="2f53a-113">대상에서 실행되는 소형 모니터 프로그램부터 BDM(Background Debug Monitor) 및 ICE(In-Circuit Emulator) 도구까지 다양한 디버거가 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="2f53a-114">ICE 도구는 실제 대상 하드웨어에 대해 가장 강력한 디버깅을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="2f53a-115">필요한 하드 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="2f53a-115">Required Hard Disk Space</span></span>

<span data-ttu-id="2f53a-116">USBX의 소스 코드는 ASCII 형식으로 제공되며 호스트 컴퓨터의 하드 디스크에 약 500KB 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="2f53a-117">대상 고려 사항</span><span class="sxs-lookup"><span data-stu-id="2f53a-117">Target Considerations</span></span>

<span data-ttu-id="2f53a-118">USBX에는 호스트 모드의 대상에 24KB에서 64KB 사이의 ROM(읽기 전용 메모리)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="2f53a-119">필요한 메모리 양은 사용된 컨트롤러 유형 및 USBX에 연결된 USB 클래스에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="2f53a-120">또한 USBX 전역 데이터 구조 및 메모리 풀에 대상의 32KB RAM(Random Access Memory)이 추가로 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="2f53a-121">이 메모리 풀은 USB의 예상 디바이스 수 및 USB 컨트롤러 유형에 따라 조정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="2f53a-122">USBX 디바이스 측에는 디바이스 컨트롤러 유형에 따라 약 10~12K의 ROM이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="2f53a-123">RAM 메모리 사용량은 디바이스에서 에뮬레이트되는 클래스 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="2f53a-124">또한 USBX에는 ThreadX 세마포, 뮤텍스, 다중 스레드 보호를 위한 스레드, USB 버스 토폴로지 모니터링을 위한 I/O 일시 중단 및 정기적 처리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="2f53a-125">제품 배포</span><span class="sxs-lookup"><span data-stu-id="2f53a-125">Product Distribution</span></span>

<span data-ttu-id="2f53a-126">Azure RTOS USBX는 <https://github.com/azure-rtos/usbx/>에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="2f53a-127">다음은 리포지토리에 있는 몇 가지 중요한 파일 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-127">The following is a list of several important files in the repository:</span></span>

- <span data-ttu-id="2f53a-128">***ux_api.h***: 이 C 헤더 파일에는 모든 시스템 이큐에이트, 데이터 구조 및 서비스 프로토타입이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
- <span data-ttu-id="2f53a-129">***ux_port.h***: 이 C 헤더 파일에는 모든 개발 도구 관련 데이터 정의 및 구조가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
- <span data-ttu-id="2f53a-130">***ux.lib***: USBX C 라이브러리의 이진 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-130">***ux.lib***: This is the binary version of the USBX C library.</span></span> <span data-ttu-id="2f53a-131">표준 패키지로 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-131">It is distributed with the standard package.</span></span>
- <span data-ttu-id="2f53a-132">***demo_usbx.c***: 간단한 USBX 데모가 포함된 C 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="2f53a-133">모든 파일 이름은 소문자로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-133">All filenames are in lower-case.</span></span> <span data-ttu-id="2f53a-134">이 명명 규칙을 사용하면 명령어를 Unix 개발 플랫폼으로 쉽게 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="2f53a-135">USBX 설치</span><span class="sxs-lookup"><span data-stu-id="2f53a-135">USBX Installation</span></span>

<span data-ttu-id="2f53a-136">USBX는 GitHub 리포지토리를 로컬 컴퓨터에 복제하여 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="2f53a-137">다음은 PC에서 USBX 리포지토리의 복제본을 만들기 위한 일반적인 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```powershell
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="2f53a-138">또는 GitHub 기본 페이지의 다운로드 단추를 사용하여 리포지토리의 복사본을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="2f53a-139">또한 온라인 리포지토리의 프런트 페이지에서 USBX 라이브러리를 빌드하기 위한 지침을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="2f53a-140">다음 일반 지침은 거의 모든 설치에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="2f53a-141">이전에 호스트 하드 드라이브에 ThreadX를 설치한 것과 동일한 디렉터리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="2f53a-142">모든 USBX 이름은 고유하며 이전 USBX 설치를 방해하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
2. <span data-ttu-id="2f53a-143">_ *_tx_application_define_.* \*의 시작 지점 또는 그 부근에 \***ux_system_initialize** _에 대한 호출을 추가하며 해당 위치에서 USBX 리소스를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _ *_tx_application_define_.** This is where the USBX resources are initialized.</span></span>
3. <span data-ttu-id="2f53a-144">***ux_host_stack_initialize*** 에 호출을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-144">Add a call to \***ux_host_stack_initialize\*.**</span></span>
4. <span data-ttu-id="2f53a-145">하나 이상의 호출을 추가하여 필요한 USBX를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-145">Add one or more calls to initialize the required USBX.</span></span>
5. <span data-ttu-id="2f53a-146">하나 이상의 호출을 추가하여 시스템에서 사용할 수 있는 호스트 컨트롤러를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-146">Add one or more calls to initialize the host controllers available in the system.</span></span>
6. <span data-ttu-id="2f53a-147">하위 수준 하드웨어 초기화를 추가하고 벡터 라우팅을 인터럽트하도록 tx_low_level_initialize.c 파일을 수정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-147">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="2f53a-148">이것은 하드웨어 플랫폼과 관련되며 여기에서 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-148">This is specific to the hardware platform and will not be discussed here.</span></span>
7. <span data-ttu-id="2f53a-149">애플리케이션 소스 코드를 컴파일하고 USBX 및 ThreadX 런타임 라이브러리(USB 스토리지 클래스 및/또는 USB 네트워크 클래스를 컴파일하려는 경우 FileX 및/또는 Netx도 필요할 수 있음), ux.a(또는 ux.lib) 및 tx.a(또는 tx.lib)를 사용하여 링크합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-149">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="2f53a-150">결과를 대상에 다운로드하고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-150">The resulting can be downloaded to the target and executed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="2f53a-151">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="2f53a-151">Configuration Options</span></span>

<span data-ttu-id="2f53a-152">USBX 라이브러리를 빌드하는 데에는 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-152">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="2f53a-153">모든 옵션은 ***ux_user.h*** 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-153">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="2f53a-154">아래 목록에서는 각 구성 옵션에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-154">The list below details each configuration option.</span></span>


- <span data-ttu-id="2f53a-155">**UX_PERIODIC_RATE**: 이 값은 특정 하드웨어 플랫폼의 초당 틱 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-155">**UX_PERIODIC_RATE**: This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="2f53a-156">기본값은 1000이며 밀리초당 틱 하나를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-156">The default is 1000 indicating one tick per millisecond.</span></span>
- <span data-ttu-id="2f53a-157">**UX_MAX_CLASS_DRIVER**: 이 값은 USBX에서 로드할 수 있는 최대 클래스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-157">**UX_MAX_CLASS_DRIVER**: This value is the maximum number of classes that can be loaded by USBX.</span></span> <span data-ttu-id="2f53a-158">이 값은 클래스의 인스턴스 수가 아니라 클래스 컨테이너를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-158">This value represents the class container and not the number of instances of a class.</span></span> <span data-ttu-id="2f53a-159">예를 들어 USBX의 특정 구현에 허브 클래스, 프린터 클래스 및 저장소 클래스가 필요한 경우 이러한 클래스에 속한 디바이스 수에 관계없이 UX_MAX_CLASS_DRIVER 값을 3으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-159">For instance, if a particular implementation of USBX needs the hub class, the printer class, and the storage class, then the UX_MAX_CLASS_DRIVER value can be set to 3 regardless of the number of devices that belong to these classes.</span></span>
- <span data-ttu-id="2f53a-160">**UX_MAX_HCD**: 이 값은 시스템에서 사용할 수 있는 다른 호스트 컨트롤러의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-160">**UX_MAX_HCD**: This value represents the number of different host controllers that are available in the system.</span></span> <span data-ttu-id="2f53a-161">USB 1.1 지원의 경우 이 값은 대부분 1입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-161">For USB 1.1 support, this value will mostly be 1.</span></span> <span data-ttu-id="2f53a-162">USB 2.0 지원의 경우 이 값은 1보다 큽니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-162">For USB 2.0 support this value can be more than 1.</span></span> <span data-ttu-id="2f53a-163">이 값은 동시에 실행 중인 동시 호스트 컨트롤러의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-163">This value represents the number of concurrent host controllers running at the same time.</span></span> <span data-ttu-id="2f53a-164">예를 들어 두 개의 OHCI 인스턴스를 실행하거나 하나의 EHCI 및 하나의 OHCI 컨트롤러를 실행하는 경우 UX_MAX_HCD는 2로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-164">If for instance, there are two instances of OHCI running or one EHCI and one OHCI controllers running, the UX_MAX_HCD should be set to 2.</span></span> 
- <span data-ttu-id="2f53a-165">**UX_MAX_DEVICES**: 이 값은 USB에 연결할 수 있는 디바이스의 최대 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-165">**UX_MAX_DEVICES**: This value represents the maximum number of devices that can be attached to the USB.</span></span> <span data-ttu-id="2f53a-166">일반적으로 단일 USB의 이론적인 디바이스의 최대 수는 127개입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-166">Normally, the theoretical maximum number on a single USB is 127 devices.</span></span> <span data-ttu-id="2f53a-167">메모리를 절약하기 위해 이 값을 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-167">This value can be scaled down to conserve memory.</span></span> <span data-ttu-id="2f53a-168">이 값은 시스템의 USB 버스 수에 관계없이 총 디바이스 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-168">It should be noted that this value represents the total number of devices regardless of the number of USB buses in the system.</span></span>
- <span data-ttu-id="2f53a-169">**UX_MAX_ED**: 이 값은 컨트롤러 풀의 최대 ED 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-169">**UX_MAX_ED**: This value represents the maximum number of EDs in the controller pool.</span></span> <span data-ttu-id="2f53a-170">이 숫자는 하나의 컨트롤러에만 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-170">This number is assigned to one controller only.</span></span> <span data-ttu-id="2f53a-171">컨트롤러의 인스턴스가 여러 개 있는 경우 이 값이 각 개별 컨트롤러에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-171">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="2f53a-172">**UX_MAX_TD 및 UX_MAX_ISO_TD**: 이 값은 컨트롤러 풀의 일반 및 등시 TD의 최대 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-172">**UX_MAX_TD and UX_MAX_ISO_TD**: This value represents the maximum number of regular and isochronous TDs in the controller pool.</span></span> <span data-ttu-id="2f53a-173">이 숫자는 하나의 컨트롤러에만 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-173">This number is assigned to one controller only.</span></span> <span data-ttu-id="2f53a-174">컨트롤러의 인스턴스가 여러 개 있는 경우 이 값이 각 개별 컨트롤러에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-174">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="2f53a-175">**UX_THREAD_STACK_SIZE**: 이 값은 USBX 스레드의 스택 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-175">**UX_THREAD_STACK_SIZE**: This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="2f53a-176">일반적으로 사용된 프로세스 및 호스트 컨트롤러에 따라 1024바이트 또는 2048바이트일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-176">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span>
- <span data-ttu-id="2f53a-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: 이 값은 USB 호스트 열거형 스레드의 스택 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: This value is the stack size of the USB host enumeration thread.</span></span> <span data-ttu-id="2f53a-178">이 기호를 설정하지 않은 경우 USBX 호스트 열거형 스레드 스택 크기가 **UX_THREAD_STACK_SIZE** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-178">If this symbol I not set, the USBX host enumeration thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span> 
- <span data-ttu-id="2f53a-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: 이 값은 USB 호스트 HCD 스레드의 스택 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: This value is the stack size of the USB host HCD thread.</span></span> <span data-ttu-id="2f53a-180">이 기호를 설정하지 않은 경우 USBX 호스트 HCD 스레드 스택 크기가 **UX_THREAD_STACK_SIZE** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-180">If this symbol I not set, the USBX host HCD thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span>
- <span data-ttu-id="2f53a-181">**UX_THREAD_PRIORITY_ENUM**: 버스 토폴로지를 모니터링하는 USBX 열거형 스레드의 ThreadX 우선 순위 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-181">**UX_THREAD_PRIORITY_ENUM**: This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span>
- <span data-ttu-id="2f53a-182">**UX_THREAD_PRIORITY_CLASS**: 표준 USBX 스레드의 ThreadX 우선 순위 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-182">**UX_THREAD_PRIORITY_CLASS**: This is the ThreadX priority value for the standard USBX threads.</span></span>
- <span data-ttu-id="2f53a-183">**UX_THREAD_PRIORITY_KEYBOARD**: USBX HID 키보드 클래스의 ThreadX 우선 순위 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-183">**UX_THREAD_PRIORITY_KEYBOARD**: This is the ThreadX priority value for the USBX HID keyboard class.</span></span>
- <span data-ttu-id="2f53a-184">**UX_THREAD_PRIORITY_HCD**: 호스트 컨트롤러 스레드의 ThreadX 우선 순위 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-184">**UX_THREAD_PRIORITY_HCD**: This is the ThreadX priority value for the host controller thread.</span></span>
- <span data-ttu-id="2f53a-185">**UX_NO_TIME_SLICE**: 이 값은 스레드에 사용되는 시간 조각을 실제로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-185">**UX_NO_TIME_SLICE**: This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="2f53a-186">예를 들어 0으로 정의되면 ThreadX 대상 포트는 시간 조각을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-186">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span>
- <span data-ttu-id="2f53a-187">**UX_MAX_HOST_LUN**: 이 값은 호스트 저장소 클래스 드라이버에 표시되는 최대 SCSI 논리 단위 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-187">**UX_MAX_HOST_LUN**: This value represents the maximum number of SCSI logical units represented in the host storage class driver.</span></span>
- <span data-ttu-id="2f53a-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: 정의되면 이 값에는 CB 또는 CBI 프로토콜(예: 플로피 디스크)을 사용하는 저장 장치의 처리 코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: If defined, this value includes code to handle storage devices that use the CB or CBI protocol (such as floppy disks).</span></span> <span data-ttu-id="2f53a-189">이러한 프로토콜은 더 이상 사용되지 않으므로 기본적으로 사용되지 않습니다. 이 프로토콜은 거의 모든 최신 저장 장치에서 사용하는 BOT(대량 전용 전송) 프로토콜로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-189">It is off by default because these protocols are obsolete, being superseded by the Bulk Only Transport (BOT protocol, which virtually all modern storage devices use.</span></span>
- <span data-ttu-id="2f53a-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: 이 값을 정의하면 ux_host_class_hid_keyboard_key_get에서 키 누름 및 키 놓음과 같은 키 변경 내용만 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: If defined, this value causes ux_host_class_hid_keyboard_key_get to only report key changes that is, key presses and key releases.</span></span> <span data-ttu-id="2f53a-191">기본적으로 키가 다운된 경우에만 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-191">By default, it only reports when a key is down.</span></span>
- <span data-ttu-id="2f53a-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** 가 정의된 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="2f53a-193">정의되면 ux_host_class_hid_keyboard_key_get에서 키 누름(down) 변경 내용만 보고하며 키 놓음(up) 변경 내용은 보고하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-193">If defined, causes ux_host_class_hid_keyboard_key_get to only report key pressed/down changes; key released/up changes are not reported.</span></span>
- <span data-ttu-id="2f53a-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** 가 정의된 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="2f53a-195">정의되면 ux_host_class_hid_keyboard_key_get에서 잠금 키(CapsLock/NumLock/ScrollLock) 변경 내용을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-195">If defined, causes ux_host_class_hid_keyboard_key_get to report lock key (CapsLock/NumLock/ScrollLock) changes.</span></span>
- <span data-ttu-id="2f53a-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** 가 정의된 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="2f53a-197">정의되면 ux_host_class_hid_keyboard_key_get에서 보조 키(Ctrl/Alt/Shift/GUI) 변경 내용을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-197">If defined, causes ux_host_class_hid_keyboard_key_get to report modifier key (Ctrl/Alt/Shift/GUI) changes.</span></span>
- <span data-ttu-id="2f53a-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: 정의되면 이 값은 CDC-ECM 호스트 클래스의 패킷 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: If defined, this value represents the number of packets in the CDC-ECM host class.</span></span> <span data-ttu-id="2f53a-199">기본값은 16입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-199">The default is 16.</span></span>

## <a name="source-code-tree"></a><span data-ttu-id="2f53a-200">소스 코드 트리</span><span class="sxs-lookup"><span data-stu-id="2f53a-200">Source Code Tree</span></span>

<span data-ttu-id="2f53a-201">USBX 파일은 여러 디렉터리에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-201">The USBX files are provided in several directories.</span></span>

![소스 코드 트리](media/usbx-host-stack/source-code-tree.png)

<span data-ttu-id="2f53a-203">이름으로 파일을 인식할 수 있도록 다음 규칙이 채택되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-203">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="2f53a-204">파일 접미사 이름</span><span class="sxs-lookup"><span data-stu-id="2f53a-204">File Suffix Name</span></span> | <span data-ttu-id="2f53a-205">파일 설명</span><span class="sxs-lookup"><span data-stu-id="2f53a-205">File description</span></span>                          |
| ---------------- | ----------------------------------------- |
| <span data-ttu-id="2f53a-206">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="2f53a-206">ux_host_stack</span></span>    | <span data-ttu-id="2f53a-207">usbx 호스트 스택 코어 파일</span><span class="sxs-lookup"><span data-stu-id="2f53a-207">usbx host stack core files</span></span>                |
| <span data-ttu-id="2f53a-208">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="2f53a-208">ux_host_class</span></span>    | <span data-ttu-id="2f53a-209">usbx 호스트 스택 클래스 파일</span><span class="sxs-lookup"><span data-stu-id="2f53a-209">usbx host stack classes files</span></span>             |
| <span data-ttu-id="2f53a-210">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="2f53a-210">ux_hcd</span></span>           | <span data-ttu-id="2f53a-211">usbx 호스트 스택 컨트롤러 드라이버 파일</span><span class="sxs-lookup"><span data-stu-id="2f53a-211">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="2f53a-212">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="2f53a-212">ux_device_stack</span></span>  | <span data-ttu-id="2f53a-213">usbx 디바이스 스택 코어 파일</span><span class="sxs-lookup"><span data-stu-id="2f53a-213">usbx device stack core files</span></span>              |
| <span data-ttu-id="2f53a-214">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="2f53a-214">ux_device_class</span></span>  | <span data-ttu-id="2f53a-215">usbx 디바이스 스택 클래스 파일</span><span class="sxs-lookup"><span data-stu-id="2f53a-215">usbx device stack classes files</span></span>           |
| <span data-ttu-id="2f53a-216">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="2f53a-216">ux_dcd</span></span>           | <span data-ttu-id="2f53a-217">usbx 디바이스 스택 컨트롤러 드라이버 파일</span><span class="sxs-lookup"><span data-stu-id="2f53a-217">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="2f53a-218">ux_otg</span><span class="sxs-lookup"><span data-stu-id="2f53a-218">ux_otg</span></span>           | <span data-ttu-id="2f53a-219">usbx otg 컨트롤러 드라이버 관련 파일</span><span class="sxs-lookup"><span data-stu-id="2f53a-219">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="2f53a-220">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="2f53a-220">ux_pictbridge</span></span>    | <span data-ttu-id="2f53a-221">usbx pictbridge 파일</span><span class="sxs-lookup"><span data-stu-id="2f53a-221">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="2f53a-222">ux_utility</span><span class="sxs-lookup"><span data-stu-id="2f53a-222">ux_utility</span></span>       | <span data-ttu-id="2f53a-223">usbx 유틸리티 함수</span><span class="sxs-lookup"><span data-stu-id="2f53a-223">usbx utility functions</span></span>                    |
| <span data-ttu-id="2f53a-224">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="2f53a-224">demo_usbx</span></span>        | <span data-ttu-id="2f53a-225">USBX의 데모 파일</span><span class="sxs-lookup"><span data-stu-id="2f53a-225">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="2f53a-226">USBX 리소스 초기화</span><span class="sxs-lookup"><span data-stu-id="2f53a-226">Initialization of USBX resources</span></span>

<span data-ttu-id="2f53a-227">USBX에는 고유 메모리 관리자가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-227">USBX has its own memory manager.</span></span> <span data-ttu-id="2f53a-228">USBX의 호스트 또는 디바이스 측이 초기화되기 전 USBX에 메모리를 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-228">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="2f53a-229">USBX 메모리 관리자는 메모리를 캐시할 수 있는 시스템을 수용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-229">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="2f53a-230">다음 함수는 일반 메모리 128K로 USBX 메모리 리소스를 초기화하고 캐시 안전 메모리를 위한 별도의 풀은 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-230">The following function initializes USBX memory resources with 128K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="2f53a-231">ux_system_initialize의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-231">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a><span data-ttu-id="2f53a-232">입력 매개 변수:</span><span class="sxs-lookup"><span data-stu-id="2f53a-232">Input parameters:</span></span>

- <span data-ttu-id="2f53a-233">**regular_memory_pool_start** 일반 메모리 풀의 시작입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-233">**regular_memory_pool_start** Beginning of the regular memory pool.</span></span>
- <span data-ttu-id="2f53a-234">**regular_memory_size** 일반 메모리 풀의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-234">**regular_memory_size** Size of the regular memory pool.</span></span>
- <span data-ttu-id="2f53a-235">**cache_safe_memory_pool_start** 캐시 안전 메모리 풀의 시작입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-235">**cache_safe_memory_pool_start** Beginning of the cache safe memory pool.</span></span>
- <span data-ttu-id="2f53a-236">**cache_safe_memory_size** 캐시 안전 메모리 풀의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-236">**cache_safe_memory_size** Size of the cache safe memory pool.</span></span>    |

<span data-ttu-id="2f53a-237">일부 시스템에는 캐시 안전 메모리 정의가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="2f53a-238">이러한 시스템에서 메모리 포인터 초기화 중 전달되는 값은 UX_NULL로 설정되고 풀 크기는 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="2f53a-239">그런 다음 USBX이 캐시 안전 풀 대신에 일반 메모리 풀을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="2f53a-240">일반 메모리의 캐시가 안전하지 않고 컨트롤러가 DMA 메모리(OHCI, EHCI 컨트롤러 등)를 수행해야 하는 시스템에서는 캐시 안전 영역에 메모리 풀을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory (like OHCI, EHCI controllers amongst others) it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="2f53a-241">USBX 리소스 초기화 해제</span><span class="sxs-lookup"><span data-stu-id="2f53a-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="2f53a-242">해당 리소스를 해제하여 USBX를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="2f53a-243">USBX를 종료하기 전 모든 클래스 및 컨트롤러 리소스를 적절하게 종료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="2f53a-244">다음 함수는 USBX 메모리 리소스를 초기화 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-244">The following function uninitializes USBX memory resources :</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="2f53a-245">ux_system_initialize의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-245">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a><span data-ttu-id="2f53a-246">USB 호스트 컨트롤러의 정의</span><span class="sxs-lookup"><span data-stu-id="2f53a-246">Definition of USB Host Controllers</span></span>

<span data-ttu-id="2f53a-247">호스트 모드에서 작동하려면 USBX에 대한 USB 호스트 컨트롤러를 하나 이상 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-247">It is required to define at least one USB host controller for USBX to operate in host mode.</span></span> <span data-ttu-id="2f53a-248">애플리케이션 초기화 파일에 이 정의가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="2f53a-249">다음 줄은 일반 호스트 컨트롤러의 정의를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-249">The following line performs the definition of a generic host controller.</span></span>

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

<span data-ttu-id="2f53a-250">ux_host_stack_hcd_register에는 다음 프로토타입이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-250">The ux_host_stack_hcd_register has the following prototype.</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

<span data-ttu-id="2f53a-251">ux_host_stack_hcd_register 함수에는 다음의 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-251">The ux_host_stack_hcd_register function has the following parameters.</span></span>

- <span data-ttu-id="2f53a-252">**hcd_name**: 컨트롤러 이름의 문자열</span><span class="sxs-lookup"><span data-stu-id="2f53a-252">**hcd_name**: string of the controller name</span></span>
- <span data-ttu-id="2f53a-253">**hcd_initialize_function**: 컨트롤러의 초기화 함수</span><span class="sxs-lookup"><span data-stu-id="2f53a-253">**hcd_initialize_function**: initialization function of the controller</span></span>
- <span data-ttu-id="2f53a-254">**hcd_param1**: 일반적으로 컨트롤러에서 사용하는 IO 값 또는 메모리</span><span class="sxs-lookup"><span data-stu-id="2f53a-254">**hcd_param1**: usually the IO value or Memory used by the controller</span></span>
- <span data-ttu-id="2f53a-255">**hcd_param2**: 일반적으로 컨트롤러에서 사용하는 IRQ</span><span class="sxs-lookup"><span data-stu-id="2f53a-255">**hcd_param2**: usually the IRQ used by the controller</span></span>

<span data-ttu-id="2f53a-256">이전 예제:</span><span class="sxs-lookup"><span data-stu-id="2f53a-256">In our previous example:</span></span>

- <span data-ttu-id="2f53a-257">'ux_hcd_controller'는 컨트롤러의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-257">"ux_hcd_controller" is the name of the controller</span></span>
- <span data-ttu-id="2f53a-258">'ux_hcd_controller_initialize'는 호스트 컨트롤러의 초기화 루틴입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-258">"ux_hcd_controller_initialize" is the initialization routine for the host controller</span></span>
- <span data-ttu-id="2f53a-259">0xd0000은 호스트 컨트롤러 레지스터가 메모리에 표시되는 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-259">0xd0000 is the address at which the host controller registers are visible in memory</span></span>
- <span data-ttu-id="2f53a-260">그리고 0x0a는 호스트 컨트롤러가 사용하는 IRQ입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-260">and 0x0a is the IRQ used by the host controller.</span></span>

<span data-ttu-id="2f53a-261">다음은 하나의 호스트 컨트롤러와 여러 클래스를 사용하여 호스트 모드에서 USBX를 초기화하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-261">Following is an example of the initialization of USBX in host mode with one host controller and several classes.</span></span>

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a><span data-ttu-id="2f53a-262">호스트 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="2f53a-262">Definition of Host Classes</span></span>

<span data-ttu-id="2f53a-263">USBX를 사용하여 하나 이상의 호스트 클래스를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-263">It is required to define one or more host classes with USBX.</span></span> <span data-ttu-id="2f53a-264">USB 스택이 USB 디바이스를 구성한 후 USB 디바이스를 구동하려면 USB 클래스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-264">A USB class is required to drive a USB device after the USB stack has configured the USB device.</span></span> <span data-ttu-id="2f53a-265">USB 클래스는 해당 디바이스에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-265">A USB class is specific to the device.</span></span> <span data-ttu-id="2f53a-266">USB 디바이스 설명자에 포함된 인터페이스 수에 따라 USB 디바이스를 구동하려면 하나 이상의 클래스가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-266">One or more classes may be required to drive a USB device depending on the number of interfaces contained in the USB device descriptors.</span></span>

<span data-ttu-id="2f53a-267">허브 클래스 등록의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-267">This is an example of the registration of the HUB class.</span></span>

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

<span data-ttu-id="2f53a-268">ux_host_class_register 함수에는 다음 프로토타입이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-268">The function ux_host_class_register has the following prototype.</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- <span data-ttu-id="2f53a-269">**class_name** 은 클래스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-269">**class_name** is the name of the class</span></span>
- <span data-ttu-id="2f53a-270">**class_entry_address** 는 클래스의 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-270">**class_entry_address** is the entry point of the class</span></span>

<span data-ttu-id="2f53a-271">허브 클래스 초기화 예제:</span><span class="sxs-lookup"><span data-stu-id="2f53a-271">In the example of the HUB class initialization:</span></span>

- <span data-ttu-id="2f53a-272">'ux_host_class_hub'는 허브 클래스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-272">"ux_host_class_hub" is the name of the hub class</span></span>
- <span data-ttu-id="2f53a-273">'ux_host_class_hub_entry'는 허브 클래스의 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-273">ux_host_class_hub_entry is the entry point of the HUB class.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="2f53a-274">문제 해결</span><span class="sxs-lookup"><span data-stu-id="2f53a-274">Troubleshooting</span></span>

<span data-ttu-id="2f53a-275">USBX는 데모 파일 및 시뮬레이션 환경으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-275">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="2f53a-276">항상 대상 하드웨어 또는 특정 데모 플랫폼에서 데모 플랫폼을 먼저 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-276">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

<span data-ttu-id="2f53a-277">데모 시스템이 작동하지 않는 경우 다음 작업을 수행하여 문제 범위를 좁힙니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-277">If the demonstration system does not work, try the following things to narrow the problem.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="2f53a-278">USBX 버전 ID</span><span class="sxs-lookup"><span data-stu-id="2f53a-278">USBX Version ID</span></span>

<span data-ttu-id="2f53a-279">USBX의 현재 버전은 런타임 중 사용자 및 애플리케이션 모두에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-279">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="2f53a-280">프로그래머는 \***ux_port.h** _ 파일을 조사하여 USBX 버전을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-280">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="2f53a-281">또한 이 파일에는 해당 포트의 버전 기록도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-281">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="2f53a-282">애플리케이션 소프트웨어는 _\*_ux_port.h_\*\*에 정의된 전역 문자열 _ \*_ _ux_version_id_\* _를 검사하여 USBX 버전을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f53a-282">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
