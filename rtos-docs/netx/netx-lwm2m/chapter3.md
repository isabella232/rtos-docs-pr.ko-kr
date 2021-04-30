---
title: 챕터 3 - Azure RTOS NetX LWM2M의 기능 설명
description: 이 챕터에는 Azure RTOS NetX LWM2M에 대한 기능 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f49a4f5f4c899dfa461a9d57a8b56e4503d6acd4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811496"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a>챕터 3 - Azure RTOS NetX LWM2M의 기능 설명

이 챕터에는 Azure RTOS NetX LWM2M에 대한 기능 설명이 포함되어 있습니다.

## <a name="lwm2m-client-initialization"></a>LWM2M 클라이언트 초기화

LWM2M 클라이언트는 ***nx_lwm2m_client_create*** 서비스를 호출하여 초기화됩니다. LWM2M 클라이언트는 자체 스레드에서 실행되며, 콜백을 사용하거나 애플리케이션에서 구현하는 사용자 지정 개체의 메서드를 호출하여 애플리케이션에 일부 이벤트를 보고할 수 있습니다.

또한 하나 이상의 서버와 통신할 수 있도록 ***nx_lwm2m_client_session_create*** 를 호출하여 LWM2M 클라이언트 세션을 만들어야 합니다. 세션은 부트스트랩 서버 또는 LWM2M 서버(디바이스 관리)와 같은 두 가지 유형의 서버와 통신할 수 있습니다.

### <a name="bootstrap-server-session"></a>부트스트랩 서버 세션

부트스트랩 서버와의 통신 세션은 LWM2M 클라이언트가 하나 이상의 LWM2M 서버에 "등록" 작업을 수행할 수 있도록 LWM2M 클라이언트에 중요한 정보를 프로비전하는 데 사용됩니다. 이 유형의 서버는 클라이언트 시작 및 서버 시작 부트스트랩 모드를 실행하는 동안 사용됩니다.

애플리케이션은 ***nx_lwm2m_client_session_bootstrap** _ 또는 _*_nx_lwm2m_client_session_bootstrap_dtls_*_ 를 호출하여 부트스트랩 세션을 시작할 수 있으며 서버의 IP 주소 및 포트 번호와 선택적 보안 개체 인스턴스 ID를 제공해야 합니다. _*_Nx_lwm2m_client_session_bootstrap_*_ 함수는 안전하지 않은 통신을 사용하지만 _ *_nx_lwm2m_client_session_bootstrap_dtls_**는 서버와의 안전한 DTLS 연결을 설정합니다.

부트스트랩 작업에 성공하면 부트스트랩 서버에서 부트스트랩 및 LWM2M 서버에 대한 보안 개체 인스턴스와 LWM2M 서버에 대한 서버 개체 인스턴스를 만들어야 합니다. 애플리케이션은 LWM2M 서버와의 세션을 설정하는 데 이 정보를 사용해야 합니다.

다음에 디바이스를 다시 부팅할 때 LWM2M 클라이언트를 구성하려면 애플리케이션의 비휘발성 메모리에 부트스트랩 데이터를 저장해야 합니다.

### <a name="lwm2m-server-session"></a>LWM2M 서버 세션

LWM2M 서버와의 통신 세션은 등록, 디바이스 관리 및 서비스 활성화에 사용됩니다.

애플리케이션은 ***nx_lwm2m_client_session_register** _ 또는 _*_nx_lwm2m_client_session_register_dtls_*_ 를 호출하여 서버에 LWM2M 클라이언트를 등록할 수 있습니다. 이 클라이언트는 서버의 IP 주소와 포트 번호 및 기존 서버 개체 인스턴스에 해당하는 약식 서버 ID를 제공해야 합니다. _*_nx_lwm2m_client_session_register_*_ 함수는 안전하지 않은 통신을 사용하지만 _ *_nx_lwm2m_client_session_register_dtls_**는 서버와의 안전한 DTLS 연결을 설정합니다.

애플리케이션은 ***nx_lwm2m_client_session_deregister** _를 호출하여 LWM2M 클라이언트를 등록 취소하고 _ *_nx_lwm2m_client_session_update_**를 호출하여 'Update' 메시지를 보내도록 클라이언트에 요청할 수 있습니다.

### <a name="session-state-callback"></a>세션 상태 콜백

애플리케이션은 세션의 상태가 업데이트될 때 호출되는 콜백을 세션 생성 시 등록합니다. 콜백 함수 NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK에는 다음 프로토타입이 있습니다.

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

정의되는 상태는 다음과 같습니다.

- **NX_LWM2M_CLIENT_SESSION_INIT**: 세션 생성 후 초기 상태입니다.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: 클라이언트가 'Hold Off' 타이머 또는 서버 시작 부트스트랩이 만료되기를 기다리고 있습니다.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: 클라이언트가 부트스트랩 서버에 'Request' 메시지를 보냈습니다(클라이언트 시작 부트스트랩).

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: 클라이언트가 부트스트랩 서버에서 데이터를 수신하고 있습니다.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: 부트스트랩 서버가 'Finished' 메시지를 보냈습니다.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: 부트스트랩 세션이 실패했습니다.

- **NX_LWM2M_CLIENT_SESSION_REGISTERING**: 클라이언트가 LWM2M 서버에 'Register' 메시지를 보냈습니다.

- **NX_LWM2M_CLIENT_SESSION_REGISTERED**: 클라이언트가 LWM2M 서버에 등록되었습니다.

- **NX_LWM2M_CLIENT_SESSION_UPDATING**: 클라이언트가 LWM2M 서버에 'Update' 메시지를 보냈습니다.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: 클라이언트가 LWM2M 서버에 'De-register' 메시지를 보냈습니다.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: 클라이언트가 LWM2M 서버에서 등록 취소되었습니다.

- **NX_LWM2M_CLIENT_SESSION_DISABLED**: LWM2M 서버를 사용할 수 없습니다. 비활성화 타이머가 만료된 후 'Register'가 전송됩니다.

- **NX_LWM2M_CLIENT_SESSION_ERROR**: LWM2M 서버에 대한 등록 또는 업데이트 작업이 실패했습니다.

- **NX_LWM2M_CLIENT_SESSION_DELETED**: LWM2M 서버에 해당하는 서버 개체 인스턴스가 삭제되었습니다. 오류가 발생할 경우 애플리케이션은 **_nx_lwm2m_client_session_error_get_** 을 호출하여 오류의 원인을 검색할 수 있습니다.

## <a name="local-device-management"></a>로컬 디바이스 관리

애플리케이션은 로컬 디바이스 관리 기능을 사용하여 LWM2M 클라이언트의 개체에 액세스할 수 있습니다. 지원되는 함수는 다음과 같습니다.

- ***nx_lwm2m_client_object_read***: 개체 인스턴스에서 리소스를 읽습니다.

- ***nx_lwm2m_client_object_discover***: 개체 인스턴스의 리소스 목록을 가져옵니다.

- ***nx_lwm2m_client_object_write***: 개체 인스턴스에 리소스를 씁니다.

- ***nx_lwm2m_client_object_execute***: 개체 인스턴스의 리소스에서 실행 작업을 수행합니다.

- ***nx_lwm2m_client_object_create***: 새 개체 인스턴스를 만듭니다.

- ***nx_lwm2m_client_object_delete***: 기존 개체 인스턴스를 삭제합니다.

- ***nx_lwm2m_client_object_get_next***: LWM2M 클라이언트에서 구현하는 다음 개체 ID를 가져옵니다.

- ***nx_lwm2m_client_object_instance_get_next***: 개체의 다음 인스턴스를 가져옵니다.

## <a name="resource-information"></a>리소스 정보

개체에서 읽고 쓸 때 리소스는 NX_LWM2M_RESOURCE 구조체로 표시됩니다. 이 구조체에는 리소스/인스턴스 ID 및 해당 값이 포함됩니다. 값의 인코딩은 해당 형식과 원본(애플리케이션 또는 네트워크)에 따라 달라집니다.

NX_LWM2M_RESOURCE 구조체의 정의는 다음과 같습니다.

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- **nx_lwm2m_resource_id**: 리소스 또는 인스턴스의 ID입니다.
- **nx_lwm2m_resource_type**: 값의 형식입니다. 아래를 참조하세요.
- **nx_lwm2m_resource_value**: 리소스의 값은 값의 형식에 따라 달라집니다.

다음과 같은 형식의 값이 정의됩니다.

- **NX_LWM2M_RESOURCE_NONE**: 리소스가 비어 있습니다.

- **NX_LWM2M_RESOURCE_STRING**: *nx_lwm2m_resource_stringdata* 에 저장된 null로 끝나는 UTF-8 문자열 값입니다.

- **NX_LWM2M_RESOURCE_INTEGER32**: *nx_lwm2m_resource_integer32data* 에 저장된 32비트 정수 값입니다.

- **NX_LWM2M_RESOURCE_INTEGER64**: *nx_lwm2m_resource_integer64data* 에 저장된 64비트 정수 값입니다.

- **NX_LWM2M_RESOURCE_FLOAT32**: *nx_lwm2m_resource_float32data* 에 저장된 32비트 부동 소수점 값입니다.

- **NX_LWM2M_RESOURCE_FLOAT64**: *nx_lwm2m_resource_float64data* 에 저장된 64비트 부동 소수점 값입니다.

- **NX_LWM2M_RESOURCE_BOOLEAN**: *nx_lwm2m_resource_booleandata* 에 저장된 부울 값입니다.

- **NX_LWM2M_RESOURCE_OPAQUE**: *nx_lwm2m_resource_bufferdata* 로 정의된 불투명 값입니다.

- **NX_LWM2M_RESOURCE_OBJLNK**: *nx_lwm2m_resource_objlnkdata* 에 저장된 개체 링크 값입니다.

- **NX_LWM2M_RESOURCE_TLV**: *nx_lwm2m_resource_bufferdata* 로 정의된 TLV 인코딩 값입니다.

- **NX_LWM2M_RESOURCE_TEXT**: *nx_lwm2m_resource_bufferdata* 로 정의된 일반 텍스트 인코딩 값입니다.

- **NX_LWM2M_RESOURCE_MULTIPLE**: *nx_lwm2m_resource_multipledata* 로 정의된 다중 리소스입니다. *nx_lwm2m_resource_multiple_ptr* 은 각 리소스 인스턴스에 대한 정보를 포함하는 **NX_LWM2M_RESOURCE** 구조체의 배열에 대한 포인터입니다.

- **NX_LWM2M_RESOURCE_MULTIPLE_TLV**: *nx_lwm2m_resource_multipledata* 로 정의된 다중 리소스입니다. *nx_lwm2m_resource_multiple_ptr* 은 TLV 인코딩 버퍼에 대한 포인터입니다.

값을 검색하고 형식을 확인하기 위해 편리한 함수가 제공됩니다. 애플리케이션은 NX_LWM2M_RESOURCE 구조체에서 값을 가져올 때 *nx_lwm2m_resource_value* 필드에 직접 액세스해서는 안 됩니다. 다음과 같은 함수가 정의됩니다.

- ***nx_lwm2m_resource_get_***: 지정된 형식의 값을 가져옵니다.
- ***nx_lwm2m_resource_multiple_get_***: 다중 리소스에서 지정된 형식의 값을 가져옵니다.

**NX_LWM2M_RESOURCE_IS_MULTIPLE**(형식) 매크로를 사용하여 리소스 형식이 다중 리소스인지 확인할 수 있습니다.

## <a name="object-implementation"></a>개체 구현

LWM2M 클라이언트는 보안(0), 서버(1), Access Control(2) 및 디바이스(3)와 같은 필수 OMA LWM2M 개체를 구현합니다. 다른 디바이스별 개체는 애플리케이션에서 구현해야 합니다.

두 데이터 구조를 사용하여 개체를 정의합니다. NX_LWM2M_OBJECT 구조는 개체 ID와 개체 메서드를 포함하는 개체 구현을 정의하고 NX_LWM2M_OBJECT_INSTANCE 구조는 개체 인스턴스의 데이터를 포함합니다.

NX_LWM2M_OBJECT 구조체의 정의는 다음과 같습니다.

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- **nx_lwm2m_object_next**: 목록의 다음 개체입니다.
- **nx_lwm2m_object_id**: 개체 ID입니다.
- **nx_lwm2m_object_read**: 'Read' 메서드입니다. 아래를 참조하세요.
- **nx_lwm2m_object_discover**: 'Discover' 메서드입니다. 아래를 참조하세요.
- **nx_lwm2m_object_write**: 'Write' 메서드입니다. 아래를 참조하세요.
- **nx_lwm2m_object_execute**: 'Execute' 메서드입니다. 아래를 참조하세요.
- **nx_lwm2m_object_create**: 'Create' 메서드입니다. 아래를 참조하세요.
- **nx_lwm2m_object_delete**: 'Delete' 메서드입니다. 아래를 참조하세요.
- **nx_lwm2m_object_instances**: 개체 인스턴스의 NULL로 끝나는 목록입니다.

NX_LWM2M_OBJECT_INSTANCE 구조체의 정의는 다음과 같습니다.

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- **nx_lwm2m_object_instance_next**: 목록의 다음 인스턴스입니다.
- **nx_lwm2m_object_instance_id**: 개체 인스턴스 ID입니다.

개체는 LWM2M 디바이스 관리 인터페이스로 정의된 'Read', 'Discover', 'Write', 'Execute', 'Create' 및 'Delete' 작업에 해당하는 메서드를 구현해야 합니다. 개체에서 인스턴스의 동적 생성을 지원하지 않는 경우 'Create' 및 'Delete' 메서드를 NULL로 설정할 수 있습니다.

### <a name="the-read-method"></a>'Read' 메서드

'Read' 메서드는 개체 인스턴스에서 리소스 값을 읽는 데 사용되며, 함수의 정의는 다음과 같습니다.

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

입력 매개 변수는 다음과 같이 정의됩니다.

- **object_ptr**: 개체 구현에 대한 포인터입니다.

- **instance_ptr**: 개체 인스턴스에 대한 포인터입니다.

- **num_values**: 읽을 리소스의 수입니다.

- **values_ptr**: 읽을 리소스의 ID를 포함하는 NX_LWM2M_RESOURCE 배열에 대한 포인터입니다. 반환 시 배열이 해당 형식 및 값으로 채워집니다.

### <a name="the-discover-method"></a>'Discover' 메서드

'Discover' 메서드는 개체로 구현된 모든 리소스의 목록을 검색하는 데 사용되며, 함수의 정의는 다음과 같습니다.

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

입력 매개 변수는 다음과 같이 정의됩니다.

- **object_ptr**: 개체 구현에 대한 포인터입니다.

- **instance_ptr**: 개체 인스턴스에 대한 포인터입니다.

- **num_resources_ptr**: 입력 시 대상 버퍼의 크기 및 출력 시 버퍼에 기록된 요소의 수입니다.

- **resources_ptr**: 대상 버퍼에 대한 포인터입니다.

리소스 정보는 다음과 같이 정의된 NX_LWM2M_RESOURCE_INFO 구조체로 반환됩니다.

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- **nx_lwm2m_resource_info_id**: 리소스의 ID입니다.

- **nx_lwm2m_resource_info_flags**: 아래를 참조하세요.

- **nx_lwm2m_resource_info_dim**: NX_LWM2M_RESOURCE_INFO_MULTIPLE 플래그가 설정된 경우 다중 리소스의 차원입니다.

*nx_lwm2m_resource_flags* 필드에는 다음 값을 사용할 수 있습니다.

- 0: 읽을 수 있는 단일 리소스입니다.

- **NX_LWM2M_RESOURCE_INFO_MULTIPLE**: 다중 리소스 *nx_lwm2m_resource_info_dim* 을 정의해야 합니다.

- **NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: 실행 가능하거나 읽을 수 없는 리소스입니다.

### <a name="the-write-method"></a>'Write' 메서드

'Write' 메서드는 개체 인스턴스의 리소스를 업데이트하거나 바꾸는 데 사용되며, 함수의 정의는 다음과 같습니다.

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

입력 매개 변수는 다음과 같이 정의됩니다.

- **object_ptr**: 개체 구현에 대한 포인터입니다.
- **instance_ptr**: 개체 인스턴스에 대한 포인터입니다.
- **num_values**: 기록할 리소스의 수입니다.
- **values_ptr**: 리소스 값에 대한 포인터입니다.
- **write_op**: 쓰기 작업의 형식입니다.

*write_op* 매개 변수에 지정할 수 있는 쓰기 작업은 다음과 같습니다.

- 0 &mdash; 부분 업데이트: 새 값이 제공된 리소스를 추가하거나 업데이트하고, 다른 기존 리소스는 변경하지 않은 상태로 유지합니다.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; 인스턴스 바꾸기: 개체 인스턴스를 제공된 새 리소스 값으로 바꿉니다.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; 리소스 바꾸기: 리소스를 제공된 새 리소스 값으로 바꿉니다(여러 리소스를 바꾸는 데 사용됨).

- **NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; 인스턴스 만들기: 제공된 리소스 값(*nx_lwm2m_object_create* 메서드에서 호출됨)을 사용하여 새로 만든 개체 인스턴스를 초기화합니다.

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; 부트스트랩 쓰기: 부트스트랩 시퀀스 중에 호출됩니다.

### <a name="the-execute-method"></a>'Execute' 메서드

'Execute' 메서드는 개체 리소스의 실행을 구현하며, 함수의 정의는 다음과 같습니다.

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

입력 매개 변수는 다음과 같이 정의됩니다.

- **object_ptr**: 개체 구현에 대한 포인터입니다.
- **instance_ptr**: 개체 인스턴스에 대한 포인터입니다.
- **resource_id**: 리소스 ID입니다.
- **arguments_ptr**: 실행 작업의 인수에 대한 포인터입니다. *arguments_length* 가 0인 경우 NULL일 수 있습니다.
- **arguments_length**: 인수의 길이입니다.

이 함수는 리소스 ID가 존재하지 않는 경우 NX_LWM2M_NOT_FOUND를 반환하고, 실행을 지원하지 않는 경우 NX_LWM2M_METHOD_NOT_ALLOWED를 반환해야 합니다.

### <a name="the-create-method"></a>'Create' 메서드

'Create' 메서드는 새 개체 인스턴스의 생성을 구현하며, 함수의 정의는 다음과 같습니다.

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

입력 매개 변수는 다음과 같이 정의됩니다.

- **object_ptr**: 개체 구현에 대한 포인터입니다.
- **instance_id**: 새 인스턴스의 ID입니다.
- **num_values**: 초기화할 리소스의 수입니다.
- **values_ptr**: 리소스 값에 대한 포인터입니다.
- **instance_ptr**: 만든 인스턴스의 대상 포인터에 대한 포인터입니다.
- **bootstrap**: 부트스트랩 시퀀스에서 호출되는 경우 True입니다.

개체는 제공된 리소스 값 목록을 사용하여 새 개체 인스턴스를 할당하고 초기화해야 합니다.

### <a name="the-delete-method"></a>'Delete' 메서드

'Delete' 메서드는 개체 인스턴스의 삭제를 구현하며, 함수의 정의는 다음과 같습니다.

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

입력 매개 변수는 다음과 같이 정의됩니다.

- **object_ptr**: 개체 구현에 대한 포인터입니다.
- **instance_ptr**: 개체 인스턴스에 대한 포인터입니다.

성공 시 개체는 개체 인스턴스 데이터 및 인스턴스에 의해 할당된 다른 모든 리소스를 해제해야 합니다.

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a>LWM2M 클라이언트에 개체 구현 및 인스턴스 추가

애플리케이션은 ***nx_lwm2m_client_object_add*** 서비스를 호출하여 LWM2M 클라이언트에 새 개체 구현을 추가할 수 있습니다.

개체가 동적 인스턴스 생성을 지원하지 않는 경우(예: 단일 인스턴스 전용 개체인 경우) 개체 구조의 *nx_lwm2m_object_instances* 필드는 정적 인스턴스 구조의 목록을 가리켜야 합니다.

개체가 동적 인스턴스 생성을 지원하는 경우 *nx_lwm2m_object_instances* 를 NULL로 설정하고, ***nx_lwm2m_client_object_create*** 서비스를 대신 사용하여 개체의 'Create' 메서드를 호출해야 합니다.

## <a name="example-of-lwm2m-client-application"></a>LWM2M 클라이언트 애플리케이션의 예

다음 코드는 온도 센서 및 광원 스위치로 구성된 사용자 지정 디바이스를 구현하는 간단한 LWM2M 클라이언트 애플리케이션의 예입니다.

서버는 이 디바이스를 사용하여 광원 스위치의 온도 센서 및 부울 상태 값을 읽고 광원 스위치를 켜기/끄기로 설정할 수 있습니다.

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
