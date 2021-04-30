---
title: 2장 - Azure RTOS NetX LWM2M 설치 및 사용
description: 이 장에서는 Azure RTOS NetX LWM2M 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c13d3b092d3a5b59bd0369f6ffc162509d02590
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811515"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="08e61-103">2장 - Azure RTOS NetX LWM2M 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="08e61-103">Chapter 2 - Installation and use of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="08e61-104">이 장에서는 Azure RTOS NetX LWM2M 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX LWM2M component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="08e61-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="08e61-105">Product Distribution</span></span>

<span data-ttu-id="08e61-106">NetX LWM2M은 [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-106">NetX LWM2M is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="08e61-107">패키지에는 다음과 같이 3개의 원본 파일, 하나의 포함 파일 및 이 문서를 포함하는 PDF 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="08e61-108">**nx_lwm2m_client.h**: NetX LWM2M 클라이언트에 대한 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="08e61-108">**nx_lwm2m_client.h**: Header file for the NetX LWM2M Client</span></span>

- <span data-ttu-id="08e61-109">**nx_lwm2m_\*.c/h**: NetX LWM2M에 대한 C/H 원본 파일</span><span class="sxs-lookup"><span data-stu-id="08e61-109">**nx_lwm2m_\*.c/h**: C/H Source files for NetX LWM2M</span></span>

- <span data-ttu-id="08e61-110">**demo_netx_lwm2m_client.c**: NetX LWM2M 클라이언트 데모에 대한 C 원본 파일</span><span class="sxs-lookup"><span data-stu-id="08e61-110">**demo_netx_lwm2m_client.c**: C Source file for NetX LWM2M Client Demo</span></span>

- <span data-ttu-id="08e61-111">**NetX_LWM2M_User_Guide.pdf**: NetX LWM2M 제품에 대한 PDF 설명</span><span class="sxs-lookup"><span data-stu-id="08e61-111">**NetX_LWM2M_User_Guide.pdf**: PDF description of NetX LWM2M product</span></span>

## <a name="netx-lwm2m-installation"></a><span data-ttu-id="08e61-112">NetX LWM2M 설치</span><span class="sxs-lookup"><span data-stu-id="08e61-112">NetX LWM2M Installation</span></span>

<span data-ttu-id="08e61-113">NetX LWM2M을 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-113">In order to use NetX LWM2M, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="08e61-114">예를 들어 NetX가 " *\\threadx\\arm7\\green*" 디렉터리에 설치된 경우 *nx_lwm2m&#42;.&#42;* 파일을 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-114">For example, if NetX is installed in the directory "*\\threadx\\arm7\\green*" then the *nx_lwm2m&#42;.&#42;* files should be copied into this directory.</span></span>

## <a name="using-netx-lwm2m"></a><span data-ttu-id="08e61-115">NetX LWM2M 사용</span><span class="sxs-lookup"><span data-stu-id="08e61-115">Using NetX LWM2M</span></span>

<span data-ttu-id="08e61-116">NetX LWM2M을 사용하는 것은 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-116">Using NetX LWM2M is easy.</span></span> <span data-ttu-id="08e61-117">기본적으로 애플리케이션 코드는 ThreadX 및 NetX를 사용하기 위해 *tx_api.h* 및 *nx_api.h* 를 포함한 후 *nx_lwm2m_client.h* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-117">Basically, the application code must include *nx_lwm2m_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="08e61-118">*nx_lwm2m_client.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 NetX LWM2M 함수 호출을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-118">Once *nx_lwm2m_client.h* is included, the application code is then able to make the NetX LWM2M function calls specified later in this guide.</span></span> <span data-ttu-id="08e61-119">또한 애플리케이션은 *nx_lwm2m&#42;.&#42;* 파일을 NetX 라이브러리로 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-119">The application must also import the *nx_lwm2m&#42;.&#42;* files into the NetX library.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="08e61-120">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="08e61-120">Configuration Options</span></span>

<span data-ttu-id="08e61-121">LWM2M 클라이언트를 사용하여 LWM2M 클라이언트 라이브러리 및 애플리케이션을 빌드할 때 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-121">There are several configuration options when building the LWM2M Client library and the application using the LWM2M Client.</span></span> <span data-ttu-id="08e61-122">구성 옵션은 달리 지정되지 않은 경우 명령줄에서 애플리케이션 원본에 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-122">The configuration options can be defined in the application source, on the command line, unless otherwise specified.</span></span>

### <a name="nx_lwm2m_client_disable_error_checking"></a><span data-ttu-id="08e61-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span><span class="sxs-lookup"><span data-stu-id="08e61-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span></span>

<span data-ttu-id="08e61-124">정의된 경우 기본 LWM2M 클라이언트 오류 검사 API를 제거하고 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-124">Defined, removes the basic LWM2M Client error checking API and improves performance.</span></span> <span data-ttu-id="08e61-125">오류 검사를 사용하지 않도록 설정해도 영향을 받지 않는 API 반환 코드는 API 정의의 굵은 서체에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-125">API return codes not affected by disabling error checking are listed in bold typeface in the API definition.</span></span>

### <a name="nx_lwm2m_client_disable_float"></a><span data-ttu-id="08e61-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span><span class="sxs-lookup"><span data-stu-id="08e61-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span></span>

<span data-ttu-id="08e61-127">정의된 경우 부동 소수점 숫자 값의 지원을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-127">Defined, removes the support of floating point numbers values.</span></span> <span data-ttu-id="08e61-128">사용하지 않도록 설정된 경우 LWM2M 클라이언트는 부동 데이터 형식의 리소스를 지원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-128">When disabled the LWM2M Client cannot support Resources with Float data type.</span></span>

### <a name="nx_lwm2m_client_disable_float64"></a><span data-ttu-id="08e61-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span><span class="sxs-lookup"><span data-stu-id="08e61-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span></span>

<span data-ttu-id="08e61-130">정의된 경우 64비트 부동 소수점 숫자 값의 지원을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-130">Defined, removes the support of 64-bit floating point numbers values.</span></span> <span data-ttu-id="08e61-131">LWM2M 클라이언트는 64비트 부동 소수점 숫자가 포함된 TLV 메시지를 수신할 수 있지만, 값은 처리를 위해 32비트 부동 소수점으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-131">The LWM2M Client can still receive TLV messages containing 64-bit floating numbers, but the values are converted to 32-bit floating point for processing.</span></span>

### <a name="nx_lwm2m_client_priority"></a><span data-ttu-id="08e61-132">NX_LWM2M_CLIENT_PRIORITY</span><span class="sxs-lookup"><span data-stu-id="08e61-132">NX_LWM2M_CLIENT_PRIORITY</span></span>

<span data-ttu-id="08e61-133">LWM2M 클라이언트 스레드의 우선 순위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-133">Specifies the priority of the LWM2M Client thread.</span></span> <span data-ttu-id="08e61-134">기본적으로 이 값은 우선 순위 16을 지정하는 16으로 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-134">By default, this value is defined as 16 to specify priority 16.</span></span>

### <a name="nx_lwm2m_client_max_device_errors"></a><span data-ttu-id="08e61-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span><span class="sxs-lookup"><span data-stu-id="08e61-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span></span>

<span data-ttu-id="08e61-136">디바이스 개체에 의해 저장되는 최대 오류 코드 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-136">Specifies the maximum number of error codes stored by the Device Object.</span></span> <span data-ttu-id="08e61-137">기본값은 8입니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-137">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_security_instances"></a><span data-ttu-id="08e61-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="08e61-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span></span>

<span data-ttu-id="08e61-139">보안 개체 인스턴스의 최대 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-139">Specifies the maximum number of Security Object Instances.</span></span> <span data-ttu-id="08e61-140">부트스트랩 서버와 표준 서버를 지원하기 위한 기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-140">The default value is 2 for supporting a Bootstrap Server and a standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_instances"></a><span data-ttu-id="08e61-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="08e61-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span></span>

<span data-ttu-id="08e61-142">서버 개체 인스턴스의 최대 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-142">Specifies the maximum number of Server Object Instances.</span></span> <span data-ttu-id="08e61-143">단일 표준 서버를 지원하기 위한 기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-143">The default value is 1 for supporting a single standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_uri"></a><span data-ttu-id="08e61-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span><span class="sxs-lookup"><span data-stu-id="08e61-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span></span>

<span data-ttu-id="08e61-145">nil 종료 문자를 포함하여 서버 URI의 최대 길이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-145">Specifies the maximum length of a server URI, including terminating nil character.</span></span> <span data-ttu-id="08e61-146">기본값은 128입니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-146">The default value is 128.</span></span>

### <a name="nx_lwm2m_client_max_access_control_instances"></a><span data-ttu-id="08e61-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="08e61-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span></span>

<span data-ttu-id="08e61-148">Access Control 인스턴스의 최대 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-148">Specifies the maximum number of Access Control Instances.</span></span> <span data-ttu-id="08e61-149">기본값은 0이며, 이 값은 액세스 제어를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-149">The default value is 0, which disables access control.</span></span> <span data-ttu-id="08e61-150">애플리케이션에서 둘 이상의 LWM2M 서버를 지원하는 경우 Access Control 인스턴스의 최대 수를 LWM2M 클라이언트에서 지원할 최대 개체 인스턴스 수로 설정해야 합니다. 단, 보안 개체 인스턴스를 제외하고 각 개체 인스턴스에 대해 하나의 Access Control 인스턴스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-150">If the application supports more than one LWM2M Server, the maximum number of Access Control Instances must be set to the maximum number of Object Instances that the LWM2M Client will support, as one Access Control Instance must be created for each Object Instance (except for the Security Object Instances).</span></span>

### <a name="nx_lwm2m_client_max_access_control_acls"></a><span data-ttu-id="08e61-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span><span class="sxs-lookup"><span data-stu-id="08e61-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span></span>

<span data-ttu-id="08e61-152">Access Control 인스턴스당 ACL 리소스의 최대 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-152">Specifies the maximum number of ACL resources per Access Control Instance.</span></span> <span data-ttu-id="08e61-153">기본값은 4입니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-153">The default value is 4.</span></span>

### <a name="nx_lwm2m_client_max_notifications"></a><span data-ttu-id="08e61-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span><span class="sxs-lookup"><span data-stu-id="08e61-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span></span>

<span data-ttu-id="08e61-155">LWM2M 클라이언트가 지원할 최대 알림 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-155">Specifies the maximum number of notifications that the LWM2M Client will support.</span></span> <span data-ttu-id="08e61-156">LWM2M 서버는 개체, 개체 인스턴스 및 리소스에 대한 알림을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-156">A LWM2M Server can set notifications on Objects, Object Instances, and Resources.</span></span> <span data-ttu-id="08e61-157">기본값은 8입니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-157">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_resources"></a><span data-ttu-id="08e61-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span><span class="sxs-lookup"><span data-stu-id="08e61-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span></span>

<span data-ttu-id="08e61-159">개체당 최대 리소스 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-159">Specifies the maximum number of Resources per Object.</span></span> <span data-ttu-id="08e61-160">기본값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-160">The default value is 32.</span></span>

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a><span data-ttu-id="08e61-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span><span class="sxs-lookup"><span data-stu-id="08e61-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span></span>

<span data-ttu-id="08e61-162">세션을 중단하기 전에 부트스트랩 세션이 시작될 때 부트스트랩 서버 요청을 대기할 최대 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-162">Specifies the maximum time to wait for bootstrap server requests when the bootstrap session is initiated before aborting the session.</span></span> <span data-ttu-id="08e61-163">기본값은 60초입니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-163">The default value is 60 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_start_timeout"></a><span data-ttu-id="08e61-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08e61-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span></span>

<span data-ttu-id="08e61-165">DTLS 핸드셰이크 완료를 대기할 최대 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-165">Specifies the maximum time to wait for DTLS handshake completion.</span></span> <span data-ttu-id="08e61-166">기본값은 30초입니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-166">The default value is 30 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_end_timeout"></a><span data-ttu-id="08e61-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08e61-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span></span>

<span data-ttu-id="08e61-168">DTLS 종료 완료를 대기할 최대 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-168">Specifies the maximum time to wait for DTLS shutdown completion.</span></span> <span data-ttu-id="08e61-169">기본값은 5 초입니다.</span><span class="sxs-lookup"><span data-stu-id="08e61-169">The default value is 5 seconds.</span></span>
