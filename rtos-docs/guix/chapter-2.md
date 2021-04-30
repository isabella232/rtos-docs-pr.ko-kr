---
title: 2장 - GUIX 설치 및 사용
description: 이 장에는 고성능 사용자 인터페이스 제품 GUIX의 설치, 설정 및 사용과 관련된 다양한 문제에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6527227062fc667b3f527a798d6621914c374c5c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811208"
---
# <a name="chapter-2---installation-and-use-of-guix"></a><span data-ttu-id="029fa-103">2장 - GUIX 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="029fa-103">Chapter 2 - Installation and Use of GUIX</span></span>

<span data-ttu-id="029fa-104">이 장에는 고성능 사용자 인터페이스 제품 GUIX의 설치, 설정 및 사용과 관련된 다양한 문제에 대한 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-104">This chapter contains a description of various issues related to installation, setup, and use of the highperformance user interface product GUIX.</span></span>  

## <a name="host-considerations"></a><span data-ttu-id="029fa-105">호스트 고려 사항</span><span class="sxs-lookup"><span data-stu-id="029fa-105">Host Considerations</span></span>

<span data-ttu-id="029fa-106">임베디드 개발은 일반적으로 Windows 또는 Linux(Unix) 호스트 컴퓨터에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-106">Embedded development is usually performed on Windows or Linux (Unix) host computers.</span></span> <span data-ttu-id="029fa-107">애플리케이션이 컴파일되고 연결된 후 호스트에서 실행 파일이 생성되면 실행을 위해 대상 하드웨어로 다운로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-107">After the application is compiled, linked, and the executable is generated on the host, it is downloaded to the target hardware for execution.</span></span>

<span data-ttu-id="029fa-108">일반적으로 대상 다운로드는 개발 도구의 디버거 내에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-108">Usually the target download is done from within the development tool's debugger.</span></span> <span data-ttu-id="029fa-109">다운로드 후 디버거는 대상 실행 제어(이동, 중지, 중단점 등) 뿐만 아니라 메모리 및 프로세서 레지스터에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-109">After download, the debugger is responsible for providing target execution control (go, halt, breakpoint, etc.) as well as access to memory and processor registers.</span></span>

<span data-ttu-id="029fa-110">대부분의 개발 도구 디버거는 JTAG(IEEE 1149.1) 및 BDM(백그라운드 디버그 모드)과 같은 OCD(온-칩 디버그) 연결을 통해 대상 하드웨어와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-110">Most development tool debuggers communicate with the target hardware via on-chip debug (OCD) connections such as JTAG (IEEE 1149.1) and Background Debug Mode (BDM).</span></span> <span data-ttu-id="029fa-111">또한 디버거는 ICE(회로 내 에뮬레이션) 연결을 통해 대상 하드웨어와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-111">Debuggers also communicate with target hardware through In-Circuit Emulation (ICE) connections.</span></span> <span data-ttu-id="029fa-112">OCD와 ICE 연결은 모두 대상 상주 소프트웨어에 대한 최소 침입으로 강력한 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-112">Both OCD and ICE connections provide robust solutions with minimal intrusion on the target resident software.</span></span>

<span data-ttu-id="029fa-113">호스트에서 사용되는 리소스의 경우에는 GUXI에 대한 소스 코드를 ASCII 형식으로 전달하고 호스트 컴퓨터의 하드 디스크에 약 30MB의 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-113">As for resources used on the host, the source code for GUXI is delivered in ASCII format and requires approximately 30 Mbytes of space on the host computer’s hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="029fa-114">대상 고려 사항</span><span class="sxs-lookup"><span data-stu-id="029fa-114">Target Considerations</span></span>

<span data-ttu-id="029fa-115">GUIX에는 대상에서 5KB ~ 80KB의 ROM(읽기 전용 메모리)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-115">GUIX requires between 5 KBytes and 80 Kbytes of Read-Only Memory (ROM) on the target.</span></span> <span data-ttu-id="029fa-116">GUIX 스레드 스택 및 기타 글로벌 데이터 구조에는 대상에서 5 ~ 10KB의 RAM(Random Access Memory)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-116">Another 5 to 10KBytes of the target’s Random Access Memory (RAM) are required for the GUIX thread stack and other global data structures.</span></span>

<span data-ttu-id="029fa-117">또한 GUIX를 사용하려면 ThreadX 타이머와 ThreadX 뮤텍스 개체를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-117">In addition, GUIX requires the use of a ThreadX timer and a ThreadX mutex object.</span></span> <span data-ttu-id="029fa-118">이러한 기능은 GUIX 내의 정기적인 처리 요구 사항 및 스레드 보호에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-118">These facilities are used for periodic processing needs and thread protection inside GUIX.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="029fa-119">제품 배포</span><span class="sxs-lookup"><span data-stu-id="029fa-119">Product Distribution</span></span>

<span data-ttu-id="029fa-120">Azure RTOS GUIX는 <https://github.com/azure-rtos/guix/>에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-120">Azure RTOS GUIX can be obtained from our public source code repository at <https://github.com/azure-rtos/guix/>.</span></span>

<span data-ttu-id="029fa-121">다음은 대부분의 제품 배포에 공통적인 중요한 파일 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-121">The following is a list of the important files common to most product distributions:</span></span>

| <span data-ttu-id="029fa-122">파일 이름&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="029fa-122">Filename&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></span>| <span data-ttu-id="029fa-123">Description</span><span class="sxs-lookup"><span data-stu-id="029fa-123">Description</span></span>   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="029fa-124">gx_api.h</span><span class="sxs-lookup"><span data-stu-id="029fa-124">gx_api.h</span></span>        | <span data-ttu-id="029fa-125">이 C 헤더 파일에는 모든 시스템 등식, 데이터 구조 및 서비스 프로토타입이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-125">This C header file contains all system equates, data structures, and service prototypes.</span></span> |
| <span data-ttu-id="029fa-126">gx_port.h</span><span class="sxs-lookup"><span data-stu-id="029fa-126">gx_port.h</span></span>       | <span data-ttu-id="029fa-127">이 C 헤더 파일에는 모든 대상별 및 개발 도구별 데이터 정의 및 구조가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-127">This C header file contains all target-specific and development tool-specific data definitions and structures.</span></span>                                                                                                                                         |
| <span data-ttu-id="029fa-128">gx.a(또는 gx.lib)</span><span class="sxs-lookup"><span data-stu-id="029fa-128">gx.a (or gx.lib)</span></span> | <span data-ttu-id="029fa-129">GUIX C 라이브러리의 이진 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-129">This is the binary version of the GUIX C library.</span></span> <span data-ttu-id="029fa-130">이는 일반적으로 제공된 GUIX 라이브러리 원본 파일을 컴파일하고 보관하여 빌드되지만, 이 라이브러리는 하드웨어 대상과 라이선스 유형에 따라 미리 작성된 형태로 제공될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-130">This is normally built by compiling and archiving the provided GUIX library source files, however this library may be provided in pre-built form depending on your hardware target and license type.</span></span> |
|

> [!IMPORTANT]
> <span data-ttu-id="029fa-131">*모든 파일은 소문자이므로 명령을 Linux(Unix) 개발 플랫폼으로 쉽게 변환할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="029fa-131">*All files are in lower-case, making it easy to convert the commands to Linux (Unix) development platforms.*</span></span>

## <a name="guix-installation"></a><span data-ttu-id="029fa-132">GUIX 설치</span><span class="sxs-lookup"><span data-stu-id="029fa-132">GUIX Installation</span></span>

<span data-ttu-id="029fa-133">GUIX는 GitHub 리포지토리를 로컬 머신에 복제하여 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-133">GUIX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="029fa-134">다음은 PC에서 GUIX 리포지토리의 복제본을 만드는 일반적인 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-134">The following is typical syntax for creating a clone of the GUIX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/guix
```

<span data-ttu-id="029fa-135">또는 GitHub 기본 페이지의 다운로드 단추를 사용하여 리포지토리의 복사본을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-135">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="029fa-136">또한 온라인 리포지토리의 프런트 페이지에서 GUIX 라이브러리를 빌드하기 위한 지침을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-136">You will also find instructions for building the GUIX library on the front page of the online repository.</span></span>

>[!NOTE]  
> <span data-ttu-id="029fa-137">*애플리케이션 소프트웨어는 일반적으로 **gx.a**(또는 **gx.lib**)라고 하는 GUIX 라이브러리 파일과 C 포함 파일(\*\*gx_api.h*\* 및 **gx_port.h**)에 액세스해야 합니다. 이는 개발 도구에 대한 적절한 경로를 설정하거나 애플리케이션 개발 영역에 이러한 파일을 복사하여 수행됩니다.\*</span><span class="sxs-lookup"><span data-stu-id="029fa-137">*Application software needs access to the GUIX library file, usually called **gx.a** (or **gx.lib**), and the C include files **gx_api.h** and **gx_port.h**. This is accomplished either by setting the appropriate path for the development tools or by copying these files into the application development area.*</span></span>

## <a name="using-guix"></a><span data-ttu-id="029fa-138">GUIX 사용</span><span class="sxs-lookup"><span data-stu-id="029fa-138">Using GUIX</span></span>

<span data-ttu-id="029fa-139">GUIX를 사용하는 것은 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-139">Using GUIX is easy.</span></span> <span data-ttu-id="029fa-140">기본적으로 애플리케이션 코드는 컴파일하는 동안 ***gx_api.h** _를 포함해야 하며 GUIX 라이브러리 _*_gx.a_*_(또는 _ *_gx.lib_*)*와 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-140">Basically, the application code must include ***gx_api.h** _ during compilation and link with the GUIX library _*_gx.a_*_ (or _ *_gx.lib_*)*.</span></span>

<span data-ttu-id="029fa-141">GUIX 애플리케이션을 빌드하는 데 필요한 네 가지 간단한 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-141">There are four easy steps required to build a GUIX application:</span></span>

| <span data-ttu-id="029fa-142">단계</span><span class="sxs-lookup"><span data-stu-id="029fa-142">Steps</span></span>   | <span data-ttu-id="029fa-143">Description</span><span class="sxs-lookup"><span data-stu-id="029fa-143">Description</span></span>    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="029fa-144">1&nbsp;단계:</span><span class="sxs-lookup"><span data-stu-id="029fa-144">Step&nbsp;1:</span></span> | <span data-ttu-id="029fa-145">GUIX 서비스 또는 데이터 구조를 사용하는 모든 애플리케이션 파일에 ***gx_api.h*** 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-145">Include the ***gx_api.h*** file in all application files that use GUIX services or data structures.</span></span>                                                               |
| <span data-ttu-id="029fa-146">2&nbsp;단계:</span><span class="sxs-lookup"><span data-stu-id="029fa-146">Step&nbsp;2:</span></span> | <span data-ttu-id="029fa-147">_ *_tx_application_define_*\* 함수 또는 애플리케이션 스레드에서 \***gx_system_initialize** _를 호출하여 GUIX 시스템을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-147">Initialize the GUIX system by calling ***gx_system_initialize** _ from the _ *_tx_application_define_** function or an application thread.</span></span>                       |
| <span data-ttu-id="029fa-148">3&nbsp;단계:</span><span class="sxs-lookup"><span data-stu-id="029fa-148">Step&nbsp;3:</span></span> | <span data-ttu-id="029fa-149">표시 인스턴스를 만들고, 표시할 캔버스를 만든 후, 루트 창 및 필요한 다른 모든 창이나 위젯을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-149">Create a display instance, create a canvas for the display, and create the root window and any other windows or widgets necessary.</span></span>                                 |
| <span data-ttu-id="029fa-150">4&nbsp;단계:</span><span class="sxs-lookup"><span data-stu-id="029fa-150">Step&nbsp;4:</span></span> | <span data-ttu-id="029fa-151">애플리케이션 소스를 컴파일하고 GUIX 런타임 라이브러리 ***gx.a** _(또는 _*_gx.lib_\*\*)와 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-151">Compile application source and link with the GUIX runtime library ***gx.a** _ (or _*_gx.lib_\*\*).</span></span> <span data-ttu-id="029fa-152">결과 이미지를 대상에 다운로드하여 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-152">The resulting image can be downloaded to the target and executed!</span></span> |

## <a name="troubleshooting"></a><span data-ttu-id="029fa-153">문제 해결</span><span class="sxs-lookup"><span data-stu-id="029fa-153">Troubleshooting</span></span>

<span data-ttu-id="029fa-154">각 GUIX 포트는 특정 디스플레이 하드웨어에서 실행되는 데모 애플리케이션과 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-154">Each GUIX port is delivered with a demonstration application that executes on specific display hardware.</span></span> <span data-ttu-id="029fa-155">모든 버전의 GUIX와 함께 동일한 기본 데모가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-155">The same basic demonstration is delivered with all versions of GUIX.</span></span> <span data-ttu-id="029fa-156">항상 데모 시스템을 먼저 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-156">It is always a good idea to get the demonstration system running first.</span></span>

<span data-ttu-id="029fa-157">데모 시스템이 제대로 실행되지 않으면 다음 작업을 수행하여 문제의 범위를 좁힙니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-157">If the demonstration system does not run properly, perform the following operations to narrow the problem:</span></span>

1. <span data-ttu-id="029fa-158">데모가 어느 정도 실행되고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-158">Determine how much of the demonstration is running.</span></span>

2. <span data-ttu-id="029fa-159">컴파일 시간 상수 **GX_THREAD_STACK_SIZE** 를 변경하고 GUIX 라이브러리를 다시 컴파일하여 GUIX 스레드의 스택 크기를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-159">Increase the stack size of the GUIX thread by changing the  compile-time constant **GX_THREAD_STACK_SIZE** and recompiling  the GUIX library</span></span>

3. <span data-ttu-id="029fa-160">구성 옵션 섹션에 나열된 적절한 디버그 옵션을 사용하여 GUIX 라이브러리를 다시 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-160">Recompile the GUIX library with the appropriate debug options listed  in the configuration option section.</span></span>

4. <span data-ttu-id="029fa-161">모든 API 호출에서 반환 상태를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-161">Examine the return status from all API calls.</span></span>

5. <span data-ttu-id="029fa-162">***_gx_system_error_process*** 함수에서 중단점을 설정하여 내부 시스템 오류가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-162">Determine if there is an internal system error by setting a breakpoint at the function ***_gx_system_error_process***.</span></span> <span data-ttu-id="029fa-163">오류 코드와 호출자는 무엇이 잘못되고 있는지 알 수 있는 단서를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-163">There error code and caller should give clues as to what might be going wrong.</span></span>

6. <span data-ttu-id="029fa-164">최근 변경 내용을 일시적으로 무시하여 문제가 사라지거나 변경되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-164">Temporarily bypass any recent changes to see if the problem disappears or changes.</span></span> <span data-ttu-id="029fa-165">이러한 정보는 Microsoft 지원 엔지니어에게 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-165">Such information should prove useful to Microsoft support engineers.</span></span>

<span data-ttu-id="029fa-166">“제공할 사항” 섹션에 설명된 절차에 따라 문제 해결 단계에서 수집한 정보를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-166">Follow the procedures outlined in the section titled “What We Need From You” to send the information gathered from the troubleshooting steps.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="029fa-167">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="029fa-167">Configuration Options</span></span>

<span data-ttu-id="029fa-168">GUIX를 사용하여 GUIX 라이브러리 및 애플리케이션을 빌드할 때 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-168">There are several configuration options when building the GUIX library and the application using GUIX.</span></span> <span data-ttu-id="029fa-169">이러한 옵션은 애플리케이션 요구 사항에 가장 적합하도록 라이브러리 크기와 기능 세트를 조정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-169">These options are used to tune the library size and feature set to best fit your application requirements.</span></span> <span data-ttu-id="029fa-170">예를 들어 애플리케이션에 GUIX API 서비스를 활용하는 스레드가 하나만 있는 경우 여러 스레드에 의한 선점에서 중요한 코드 섹션을 보호하는 것과 관련된 오버 헤드를 없애기 위해 구성 플래그 **GX_DISABLE_MULTITHREAD_SUPPORT** 를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-170">For example, if your application will have only one thread utilizing the GUIX API services, the configuration flag **GX_DISABLE_MULTITHREAD_SUPPORT** should be defined to eliminate the overhead associated with protecting critical code sections from pre-emption by multiple threads.</span></span> <span data-ttu-id="029fa-171">애플리케이션 소스, 명령줄 또는 **_gx_user.h_** 포함 파일 내에서 다양한 구성 플래그를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-171">The various configuration flags can be defined in the application source, on the command line, or within the **_gx_user.h_** include file.</span></span>

<span data-ttu-id="029fa-172">GUIX 라이브러리 구성 플래그가 수정될 때마다 구성 변경 내용이 적용되도록 GUIX 라이브러리와 애플리케이션 모듈을 모두 다시 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-172">Whenever the GUIX library configuration flags are modified, it is required to rebuild both the GUIX library and your application modules for the configuration changes to take effect.</span></span>

<span data-ttu-id="029fa-173">구성 플래그의 전체 목록은 부록 H: GUIX 빌드 시간 구성 플래그에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-173">The complete list of configuration flags is documented in Appendix H: GUIX Build-Time Configuration Flags.</span></span>

## <a name="guix-version-id"></a><span data-ttu-id="029fa-174">GUIX 버전 ID</span><span class="sxs-lookup"><span data-stu-id="029fa-174">GUIX Version ID</span></span>

<span data-ttu-id="029fa-175">GUIX의 현재 버전은 런타임 중에 사용자와 애플리케이션 소프트웨어에서 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-175">The current version of GUIX is available to both the user and the application software during runtime.</span></span> <span data-ttu-id="029fa-176">프로그래머는 \***gx_port.h** _ 파일을 검사하여 GUIX 버전을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-176">The programmer can obtain the GUIX version from examination of the \***gx_port.h** _ file.</span></span> <span data-ttu-id="029fa-177">또한 이 파일에는 해당 포트 애플리케이션 소프트웨어의 버전 기록도 포함되어 있습니다. _\*_gx_port.h_\*\*의 글로벌 문자열 _ \*_ _gx_version_id_\* _를 검사하여 GUIX 버전을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-177">In addition, this file also contains a version history of the corresponding port Application software can obtain the GUIX version by examining the global string _ *_ _gx_version_id_* _ in _\*_gx_port.h_\*\*.</span></span>

<span data-ttu-id="029fa-178">애플리케이션 소프트웨어는 ***gx_api.h***에 정의된 아래에 표시된 상수에서 릴리스 정보를 가져올 수도 있습니다. 이러한 상수는 이름 및 제품 주 버전과 부 버전을 기준으로 현재 제품 릴리스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="029fa-178">Application software can also obtain release information from the constants shown below defined in \***gx_api.h**.\* These constants identify the current product release by name and the product major and minor version.</span></span>

```C
#define __PRODUCT_GUIX__

#define __GUIX_MAJOR_VERSION__

#define __GUIX_MINOR_VERSION__
```
