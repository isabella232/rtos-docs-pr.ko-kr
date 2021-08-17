---
title: 2장 - Azure RTOS NetX LWM2M 설치 및 사용
description: 이 장에서는 Azure RTOS NetX LWM2M 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ad8963c342e907201074559929f3a7a2d70c9f13e135cd95c9a2e9b224e17cf
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791230"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a>2장 - Azure RTOS NetX LWM2M 설치 및 사용

이 장에서는 Azure RTOS NetX LWM2M 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

NetX LWM2M은 [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx)에서 사용할 수 있습니다. 패키지에는 다음과 같이 3개의 원본 파일, 하나의 포함 파일 및 이 문서를 포함하는 PDF 파일이 포함되어 있습니다.

- **nx_lwm2m_client.h**: NetX LWM2M 클라이언트에 대한 헤더 파일

- **nx_lwm2m_*.c/h**: NetX LWM2M에 대한 C/H 원본 파일

- **demo_netx_lwm2m_client.c**: NetX LWM2M 클라이언트 데모에 대한 C 원본 파일

- **NetX_LWM2M_User_Guide.pdf**: NetX LWM2M 제품에 대한 PDF 설명

## <a name="netx-lwm2m-installation"></a>NetX LWM2M 설치

NetX LWM2M을 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX가 " *\\threadx\\arm7\\green*" 디렉터리에 설치된 경우 *nx_lwm2m&#42;.&#42;* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="using-netx-lwm2m"></a>NetX LWM2M 사용

NetX LWM2M을 사용하는 것은 쉽습니다. 기본적으로 애플리케이션 코드는 ThreadX 및 NetX를 사용하기 위해 *tx_api.h* 및 *nx_api.h* 를 포함한 후 *nx_lwm2m_client.h* 를 포함해야 합니다. *nx_lwm2m_client.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 NetX LWM2M 함수 호출을 수행할 수 있습니다. 또한 애플리케이션은 *nx_lwm2m&#42;.&#42;* 파일을 NetX 라이브러리로 가져와야 합니다.

## <a name="configuration-options"></a>구성 옵션

LWM2M 클라이언트를 사용하여 LWM2M 클라이언트 라이브러리 및 애플리케이션을 빌드할 때 몇 가지 구성 옵션이 있습니다. 구성 옵션은 달리 지정되지 않은 경우 명령줄에서 애플리케이션 원본에 정의할 수 있습니다.

### <a name="nx_lwm2m_client_disable_error_checking"></a>NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING

정의된 경우 기본 LWM2M 클라이언트 오류 검사 API를 제거하고 성능을 향상시킵니다. 오류 검사를 사용하지 않도록 설정해도 영향을 받지 않는 API 반환 코드는 API 정의의 굵은 서체에 나열됩니다.

### <a name="nx_lwm2m_client_disable_float"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT

정의된 경우 부동 소수점 숫자 값의 지원을 제거합니다. 사용하지 않도록 설정된 경우 LWM2M 클라이언트는 부동 데이터 형식의 리소스를 지원할 수 없습니다.

### <a name="nx_lwm2m_client_disable_float64"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT64

정의된 경우 64비트 부동 소수점 숫자 값의 지원을 제거합니다. LWM2M 클라이언트는 64비트 부동 소수점 숫자가 포함된 TLV 메시지를 수신할 수 있지만, 값은 처리를 위해 32비트 부동 소수점으로 변환됩니다.

### <a name="nx_lwm2m_client_priority"></a>NX_LWM2M_CLIENT_PRIORITY

LWM2M 클라이언트 스레드의 우선 순위를 지정합니다. 기본적으로 이 값은 우선 순위 16을 지정하는 16으로 정의되어 있습니다.

### <a name="nx_lwm2m_client_max_device_errors"></a>NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS

디바이스 개체에 의해 저장되는 최대 오류 코드 수를 지정합니다. 기본값은 8입니다.

### <a name="nx_lwm2m_client_max_security_instances"></a>NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES

보안 개체 인스턴스의 최대 수를 지정합니다. 부트스트랩 서버와 표준 서버를 지원하기 위한 기본값은 2입니다.

### <a name="nx_lwm2m_client_max_server_instances"></a>NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES

서버 개체 인스턴스의 최대 수를 지정합니다. 단일 표준 서버를 지원하기 위한 기본값은 1입니다.

### <a name="nx_lwm2m_client_max_server_uri"></a>NX_LWM2M_CLIENT_MAX_SERVER_URI

nil 종료 문자를 포함하여 서버 URI의 최대 길이를 지정합니다. 기본값은 128입니다.

### <a name="nx_lwm2m_client_max_access_control_instances"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES

Access Control 인스턴스의 최대 수를 지정합니다. 기본값은 0이며, 이 값은 액세스 제어를 사용하지 않도록 설정합니다. 애플리케이션에서 둘 이상의 LWM2M 서버를 지원하는 경우 Access Control 인스턴스의 최대 수를 LWM2M 클라이언트에서 지원할 최대 개체 인스턴스 수로 설정해야 합니다. 단, 보안 개체 인스턴스를 제외하고 각 개체 인스턴스에 대해 하나의 Access Control 인스턴스를 만들어야 합니다.

### <a name="nx_lwm2m_client_max_access_control_acls"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS

Access Control 인스턴스당 ACL 리소스의 최대 수를 지정합니다. 기본값은 4입니다.

### <a name="nx_lwm2m_client_max_notifications"></a>NX_LWM2M_CLIENT_MAX_NOTIFICATIONS

LWM2M 클라이언트가 지원할 최대 알림 수를 지정합니다. LWM2M 서버는 개체, 개체 인스턴스 및 리소스에 대한 알림을 설정할 수 있습니다. 기본값은 8입니다.

### <a name="nx_lwm2m_client_max_resources"></a>NX_LWM2M_CLIENT_MAX_RESOURCES

개체당 최대 리소스 수를 지정합니다. 기본값은 32입니다.

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a>NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER

세션을 중단하기 전에 부트스트랩 세션이 시작될 때 부트스트랩 서버 요청을 대기할 최대 시간을 지정합니다. 기본값은 60초입니다.

### <a name="nx_lwm2m_client_dtls_start_timeout"></a>NX_LWM2M_CLIENT_DTLS_START_TIMEOUT

DTLS 핸드셰이크 완료를 대기할 최대 시간을 지정합니다. 기본값은 30초입니다.

### <a name="nx_lwm2m_client_dtls_end_timeout"></a>NX_LWM2M_CLIENT_DTLS_END_TIMEOUT

DTLS 종료 완료를 대기할 최대 시간을 지정합니다. 기본값은 5 초입니다.
