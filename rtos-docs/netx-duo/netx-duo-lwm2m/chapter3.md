---
title: 챕터 3 - LWM2M 클라이언트의 기능 설명
description: 이 챕터에서는 LWM2M 클라이언트의 기능 설명을 포함합니다.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810753"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a>챕터 3 - LWM2M 클라이언트의 기능 설명

> 이 챕터에서는 LWM2M 클라이언트의 기능 설명을 포함합니다.

## <a name="lwm2m-client-initialization"></a>LWM2M 클라이언트 초기화

LWM2M 클라이언트는 ***nx_lwm2m_client_create*** 서비스를 호출하여 초기화됩니다. LWM2M 클라이언트는 자체 스레드에서 실행되며, 콜백을 사용하거나 애플리케이션에서 구현하는 사용자 지정 개체의 메서드를 호출하여 애플리케이션에 일부 이벤트를 보고할 수 있습니다.

또한 하나 이상의 서버와 통신할 수 있도록 ***nx_lwm2m_client_session_create*** 를 호출하여 LWM2M 클라이언트 세션을 만들어야 합니다. 세션은 부트스트랩 서버 또는 LWM2M 서버(디바이스 관리)와 같은 두 가지 유형의 서버와 통신할 수 있습니다.

### <a name="bootstrap-server-session"></a>부트스트랩 서버 세션

LWM2M 클라이언트에 중요한 정보를 프로비전하여 LWM2M 클라이언트가 하나 이상의 LWM2M 서버에서 "Register(레지스터)" 작업을 수행할 수 있도록 하는 부트스트랩 서버와의 통신 세션을 사용합니다. 이 유형의 서버는 클라이언트 시작 및 서버 시작 부트스트랩 모드를 실행하는 동안 사용됩니다.

애플리케이션은 ***nx_lwm2m_client_session_bootstrap** _ 또는 _*_nx_lwm2m_client_session_bootstrap_dtls_*_ 를 호출하여 부트스트랩 세션을 시작할 수 있으며 서버의 IP 주소 및 포트 번호와 선택적 보안 개체 인스턴스 ID를 제공해야 합니다. _*_Nx_lwm2m_client_session_bootstrap_*_ 함수는 안전하지 않은 통신을 사용하지만 _ *_nx_lwm2m_client_session_bootstrap_dtls_**는 서버와의 안전한 DTLS 연결을 설정합니다.

부트스트랩 작업에 성공하면 부트스트랩 서버에서 부트스트랩 및 LWM2M 서버에 대한 보안 개체 인스턴스와 LWM2M 서버에 대한 서버 개체 인스턴스를 만들어야 합니다. 애플리케이션은 ***nx_lwm2m_client_session_register_info_get*** 를 호출하여 LWM2M 서버 정보를 가져오고 LWM2M 서버를 사용하여 세션을 설정하는 데 이 정보를 사용할 수 있습니다.

다음에 디바이스를 다시 부팅할 때 LWM2M 클라이언트를 구성하려면 애플리케이션의 비휘발성 메모리에 부트스트랩 데이터를 저장해야 합니다.

### <a name="lwm2m-server-session"></a>LWM2M 서버 세션

LWM2M 서버와 통신 세션은 등록, 디바이스 관리 및 서비스를 사용하는 데 사용됩니다.

애플리케이션은 ***nx_lwm2m_client_session_register** _ 또는 _*_nx_lwm2m_client_session_register_dtls_*_ 를 호출하여 서버에 LWM2M 클라이언트를 등록할 수 있습니다. 이 클라이언트는 서버의 IP 주소와 포트 번호 및 기존 서버 개체 인스턴스에 해당하는 약식 서버 ID를 제공해야 합니다. _*_nx_lwm2m_client_session_register_*_ 함수는 안전하지 않은 통신을 사용하지만 _ *_nx_lwm2m_client_session_register_dtls_**는 서버와의 안전한 DTLS 연결을 설정합니다.

애플리케이션은 ***nx_lwm2m_client_session_deregister** _을(를) 호출하여 LWM2M 클라이언트를 등록 취소하고 _ *_nx_lwm2m_client_session_update_**를 호출하여 'Update(업데이트)' 메시지를 보내도록 클라이언트에 요청할 수 있습니다.

### <a name="session-state-callback"></a>세션 상태 콜백

애플리케이션은 세션의 상태가 업데이트될 때 호출되는 세션을 만들 때 콜백을 등록합니다. 콜백 함수 **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** 에는 다음 프로토타입이 있습니다.

typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \* SESSION_PTR, UINT state);

정의되는 상태는 다음과 같습니다.

| 세션&nbsp;상태 | Description |
| --- | --- |
| **NX_LWM2M_CLIENT_SESSION_INIT** | 세션 생성 후 초기 상태입니다. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING** | 클라이언트에서 'Hold Off(보류 중)' 타이머 또는 서버 시작 부트스트랩이 만료될 때까지 기다리고 있습니다. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING** | 클라이언트에서 부트스트랩 서버(클라이언트 시작 부트스트랩)로 'Request(요청)' 메시지를 보냈습니다. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED** | 클라이언트가 부트스트랩 서버에서 데이터를 수신하고 있습니다. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED** | 부트스트랩 서버에서 'Finished(완료)' 메시지를 보냈습니다. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR** | 부트스트랩 세션이 실패했습니다. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERING** | 클라이언트가 LWM2M 서버에 'Register(등록)' 메시지를 보냈습니다. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERED** | 클라이언트가 LWM2M 서버에 등록되어 있습니다. |
| **NX_LWM2M_CLIENT_SESSION_UPDATING** | 클라이언트가 LWM2M 서버에 'Update(업데이트)' 메시지를 보냈습니다. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERING** | 클라이언트가 LWM2M 서버에 'De-register(등록 취소)' 메시지를 보냈습니다. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERED** | 클라이언트가 LWM2M 서버에서 등록 취소되었습니다. |
| **NX_LWM2M_CLIENT_SESSION_DISABLED** | LWM2M 서버를 사용할 수 없습니다. 비활성화 타이머가 만료된 후 'Register(등록)'가 전송됩니다. |
| **NX_LWM2M_CLIENT_SESSION_ERROR** | LWM2M 서버에 대한 등록 또는 업데이트 작업이 실패했습니다. |
| **NX_LWM2M_CLIENT_SESSION_DELETED** | LWM2M 서버에 해당하는 서버 개체 인스턴스가 삭제되었습니다. |

오류가 발생하는 경우 애플리케이션은 ***nx_lwm2m_client_session_error_get*** 를 호출하여 오류의 원인을 검색할 수 있습니다.

## <a name="local-device-management"></a>로컬 디바이스 관리

애플리케이션은 로컬 디바이스 관리 기능을 사용하여 LWM2M 클라이언트의 개체에 액세스할 수 있습니다. 지원되는 함수는 다음과 같습니다.

| 함수&nbsp;이름 | Description |
| --- | --- |
| ***nx_lwm2m_client_object_read*** | 개체 인스턴스에서 리소스를 읽습니다. |
| ***nx_lwm2m_client_object_discover*** | 개체 인스턴스의 리소스 목록을 가져옵니다.
| ***nx_lwm2m_client_object_write*** | 개체 인스턴스에 리소스를 씁니다. |
| ***nx_lwm2m_client_object_execute*** | 개체 인스턴스의 리소스에서 실행 작업을 수행합니다. |
| ***nx_lwm2m_client_object_create*** | 새 개체 인스턴스를 만듭니다. |
| ***nx_lwm2m_client_object_delete*** | 기존 개체 인스턴스를 삭제합니다. |
| ***nx_lwm2m_client_object_next_get*** | LWM2M 클라이언트를 통해 다음 개체 ID를 가져옵니다. |
| ***nx_lwm2m_client_object_instance_next_get*** | 개체의 다음 인스턴스를 가져옵니다. |

## <a name="resource-information"></a>리소스 정보

개체에서 읽고 쓰는 경우 리소스는 NX_LWM2M_CLIENT_RESOURCE 구조로 표시됩니다. 이 구조에는 리소스/인스턴스 ID 및 해당 값이 포함됩니다.

리소스 정보 및 값을 설정하기 위해 제공되는 함수는 다음과 같습니다.

| 함수&nbsp;이름 | Description |
| --- | --- |
| ***nx_lwm2m_client_resource_info_set*** | 리소스 정보 설정: 리소스 ID 및 작업: 읽기, 쓰기, 실행 파일. |
| ***nx_lwm2m_client_resource_string_set*** | 리소스 값을 문자열로 설정합니다. |
| ***nx_lwm2m_client_resource_integer32_set*** | 리소스 값을 32비트 정수로 설정합니다. |
| ***nx_lwm2m_client_resource_integer64_set*** | 리소스 값을 64비트 정수로 설정합니다. |
| ***nx_lwm2m_client_resource_float32_set*** | 리소스 값을 32비트 float로 설정합니다. |
| ***nx_lwm2m_client_resource_float64_set*** | 리소스 값을 64비트 float로 설정합니다. |
| ***nx_lwm2m_client_resource_boolean_set*** | 리소스 값을 부울로 설정합니다. |
| ***nx_lwm2m_client_resource_objlnk_set*** | 리소스 값을 개체 링크로 설정합니다. |
| ***nx_lwm2m_client_resource_opaque_set*** | 리소스 값을 불투명으로 설정합니다. |
| ***nx_lwm2m_client_resource_instance_set*** | 리소스 값을 여러 리소스에 대한 인스턴스로 설정합니다. |
| ***nx_lwm2m_client_resource_dim_set*** | 검색을 위해 여러 리소스에 대한 리소스 차원을 설정합니다. |

리소스 정보 및 값을 가져오기 위해 제공되는 함수는 다음과 같습니다.

| 함수&nbsp;이름 | Description |
| --- | --- |
| ***nx_lwm2m_client_resource_info_get*** | 리소스 정보 가져오기: 리소스 ID 및 작업: 읽기, 쓰기, 실행 파일 |
| ***nx_lwm2m_client_resource_string_get*** | 문자열 리소스의 값을 가져옵니다. |
| ***nx_lwm2m_client_resource_integer32_get*** | 32비트 정수 리소스의 값을 가져옵니다. |
| ***nx_lwm2m_client_resource_integer64_get*** | 64비트 정수 리소스의 값을 가져옵니다. |
| ***nx_lwm2m_client_resource_float32_get*** | 32비트 float 리소스의 값을 가져옵니다. |
| ***nx_lwm2m_client_resource_float64_get*** | 64비트 float 리소스의 값을 가져옵니다. |
| ***nx_lwm2m_client_resource_boolean_get*** | 부울 리소스의 값을 가져옵니다. |
| ***nx_lwm2m_client_resource_objlnk_get*** | 개체 링크 리소스의 값을 가져옵니다. |
| ***nx_lwm2m_client_resource_opaque_get*** | 불투명 리소스의 값을 가져옵니다. |
| ***nx_lwm2m_client_resource_instance_get*** | 여러 리소스에 대한 리소스 인스턴스를 가져옵니다. |
| ***nx_lwm2m_client_resource_dim_get*** | 여러 리소스에 대한 리소스 차원을 가져옵니다. |

## <a name="object-implementation"></a>디바이스 개체 구현

LWM2M 클라이언트는 보안(0), 서버(1), 액세스 제어(2) 및 디바이스(3)와 같은 필수 OMA LWM2M 개체를 구현합니다. 다른 디바이스별 개체는 애플리케이션에서 구현해야 합니다.

두 데이터 구조를 사용하여 개체를 정의합니다. NX_LWM2M_CLIENT_OBJECT 구조는 개체 ID와 개체 메서드를 포함하는 개체 구현을 정의하고 NX_LWM2M_CLIENT_OBJECT_INSTANCE 구조는 개체 인스턴스의 데이터를 포함합니다.

지원되는 함수는 다음과 같습니다.

| 함수&nbsp;이름 | Description |
| --- | --- |
| ***nx_lwm2m_client_object_add*** | 개체 구현을 LWM2M 클라이언트에 추가합니다. |
| ***nx_lwm2m_client_object_remove*** | LWM2M 클라이언트에서 개체 구현을 제거합니다. |
| ***nx_lwm2m_client_object_instance_add*** | 개체에 개체 인스턴스를 추가합니다. |
| ***nx_lwm2m_client_object_instance_remove*** | 개체에서 개체 인스턴스를 제거합니다. |

개체 메서드 콜백 함수에는 아래와 같은 시그니처가 있습니다.

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a>'Read' 메서드

'Read' 메서드는 개체 인스턴스에서 리소스 값을 읽는 데 사용됩니다. 매개 변수는 다음과 같이 정의됩니다.

| 매개 변수 | Description |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_READ** |
| **object_ptr** | 개체 구현에 대한 포인터. |
| **instance_ptr** | 개체 인스턴스에 대한 포인터. |
| **resource** | 읽는 리소스의 ID가 포함되는 **NX_LWM2M_CLIENT_RESOURCE** 배열에 대한 포인터입니다. 반환 시 배열이 해당 형식 및 값으로 채워집니다. |
| **resource_count** | 읽을 리소스의 수에 대한 포인터입니다. |
| **args_ptr** | 읽기에 사용되지 않는 매개 변수입니다. |
| **args_length** | 읽기에 사용되지 않는 매개 변수입니다. |

### <a name="the-discover-method"></a>'Discover' 메서드

'Discover' 메서드는 개체에 의해 구현된 모든 리소스 목록을 검색하는 데 사용됩니다. 매개 변수는 다음과 같이 정의됩니다.

| 매개 변수 | Description |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_DISCOVER** |
| **object_ptr** | 개체 구현에 대한 포인터. |
| **instance_ptr** | 개체 인스턴스에 대한 포인터. |
| **resource** | NX_LWM2M_CLIENT_RESOURCE 배열에 대한 포인터입니다. 반환 시 배열은 해당 리소스 정보로 채워집니다. |
| **resource_count** | 검색할 리소스의 수에 대한 포인터입니다. 반환 시 이 매개 변수는 true 값으로 업데이트해야 합니다. |
| **args_ptr** | 검색에 사용되지 않는 매개 변수입니다. |
| **args_length** | 검색에 사용되지 않는 매개 변수입니다. |

### <a name="the-write-method"></a>'Write' 메서드입니다.

'Write' 메서드는 개체 인스턴스의 리소스를 업데이트하거나 바꾸는 데 사용됩니다. 매개 변수는 다음과 같이 정의됩니다.

| 매개 변수  | Description |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_WRITE** |
| **object_ptr** | 개체 구현에 대한 포인터. |
| **instance_ptr** | 개체 인스턴스에 대한 포인터. |
| **resource** | 읽는 리소스의 ID가 포함되는 **NX_LWM2M_CLIENT_RESOURCE** 배열에 대한 포인터입니다. 반환 시 배열이 해당 형식 및 값으로 채워집니다. |
| **resource_count** | 검색할 리소스의 수에 대한 포인터입니다. |
| **args_ptr** | 쓰기 플래그입니다. |
| **args_length** | 인수의 길이입니다. |

*flag* 매개 변수에 지정할 수 있는 쓰기 작업은 다음과 같습니다.

| 작업 | 작업 | Description |
| --- | ---| --- |
| 0 | 부분 업데이트 | 새 값으로 제공되는 리소스를 추가하거나 업데이트하고, 다른 기존 리소스는 변경하지 않은 상태로 유지합니다.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | 인스턴스 바꾸기 | 개체 인스턴스를 제공된 새 리소스 값으로 바꿉니다.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** |  리소스 바꾸기 | 리소스를 제공된 새 리소스 값(여러 리소스를 바꾸는 데 사용됨)으로 바꿉니다. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE** | 인스턴스 만들기 | 제공된 리소스 값(**_nx_lwm2m_object_create_** 메서드에서 호출됨)을 사용하여 새로 만든 개체 인스턴스를 초기화합니다. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | 부트스트랩 쓰기 | 부트스트랩 시퀀스 중에 호출됩니다. |

### <a name="the-execute-method"></a>'Execute' 메서드입니다.

'Execute' 메서드는 개체 리소스의 실행을 구현합니다.

입력 매개 변수는 다음과 같이 정의됩니다.

| 매개 변수  | Description |
| --- | --- |
| **operation** | NX_LWM2M_CLIENT_OBJECT_EXECUTE |
| **object_ptr** | 개체 구현에 대한 포인터. |
| **instance_ptr** | 개체 인스턴스에 대한 포인터. |
| **resource** | 읽는 리소스의 ID가 포함되는 **NX_LWM2M_CLIENT_RESOURCE** 배열에 대한 포인터입니다. 반환 시 배열이 해당 형식 및 값으로 채워집니다. |
| **resource_count** | 검색할 리소스의 수에 대한 포인터입니다. |
| **args_ptr** | 인수 목록에 대한 포인터입니다. |
| **args_length** | 인수의 길이입니다.  |

함수는 리소스 ID가 존재하지 않는 경우 **NX_LWM2M_CLIENT_NOT_FOUND** 를 반환하거나, 실행을 지원하지 않는 경우 **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** 를 반환해야 합니다.

### <a name="the-create-method"></a>'Create' 메서드입니다.

'Create' 메서드는 새 개체 인스턴스 만들기를 구현합니다.

입력 매개 변수는 다음과 같이 정의됩니다.

| 매개 변수  | Description |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_CREATE** |
| **object_ptr** | 개체 구현에 대한 포인터. |
| **instance_ptr** | 사용하지 않는 매개 변수입니다. |
| **resource** | 읽는 리소스의 ID가 포함되는 **NX_LWM2M_CLIENT_RESOURCE** 배열에 대한 포인터입니다. 반환 시 배열이 해당 형식 및 값으로 채워집니다. |
| **resource_count** | 검색할 리소스의 수에 대한 포인터입니다. |
| **args_ptr** | 개체 인스턴스 ID입니다. |
| **args_length** | 인수의 길이입니다. |

### <a name="the-delete-method"></a>'Delete' 메서드입니다.

'Delete' 메서드는 개체 인스턴스의 삭제를 구현하고 입력 매개 변수는 다음과 같이 정의됩니다.

| 매개 변수  | Description |
| --- | --- |
| **operation** | NX_LWM2M_CLIENT_OBJECT_DELETE |
| **object_ptr** | 개체 구현에 대한 포인터. |
| **instance_ptr** | 개체 인스턴스에 대한 포인터. |
| **resource** | 사용하지 않는 매개 변수입니다. |
| **resource_count** | 사용하지 않는 매개 변수입니다. |
| **args_ptr** | 사용하지 않는 매개 변수입니다. |
| **args_length** | 사용하지 않는 매개 변수입니다. |

성공 시 개체는 개체 인스턴스 데이터 및 인스턴스에 의해 할당된 다른 모든 리소스를 해제해야 합니다.

## <a name="example-of-lwm2m-client-application"></a>LWM2M 클라이언트 애플리케이션의 예

다음 코드는 온도 센서 및 광원 스위치로 구성된 사용자 지정 디바이스를 구현하는 간단한 LWM2M 클라이언트 애플리케이션의 예입니다.

서버는 디바이스를 사용하여 광원 스위치의 온도 센서 및 부울 상태 값을 읽고 광원 스위치를 켜기/끄기로 설정할 수 있습니다.

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```