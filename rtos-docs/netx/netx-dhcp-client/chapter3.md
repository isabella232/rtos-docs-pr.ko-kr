---
title: 챕터 3 - Azure RTOS NetX DHCP 클라이언트 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX DHCP 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 50902d37f823302910b1b219658dcbf1a41406f480c14795ffceea6e733a0848
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799543"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a>챕터 3 - Azure RTOS NetX DHCP 클라이언트 서비스 설명

이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX DHCP 서비스에 대해 알파벳 순서로 설명하고 있습니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- **nx_dhcp_create**: *DHCP 인스턴스 만들기*

- **nx_dhcp_clear_broadcast_flag**: 클라이언트 메시지에서 브로드캐스트 플래그 지우기

- **nx_dhcp_delete**: *DHCP 인스턴스 삭제*

- **nx_dhcp_decline**: *서버에 거부 메시지* 보내기

- **nx_dhcp_force_renew**: *강제 갱신 메시지 보내기*

- **nx_dhcp_packet_pool_set**: *DHCP 클라이언트 패킷 풀 설정*

- **nx_dhcp_release**: *서버에 릴리스 메시지* 보내기

- **nx_dhcp_reinitialize**: *DHCP 클라이언트 네트워크 매개 변수 지우기*

- **nx_dhcp_request_client_ip**: *특정 IP 주소 지정*

- **nx_dhcp_send_request**: *서버에 DHCP 메시지 보내기*

- **nx_dhcp_server_address_get**: *DHCP 클라이언트의 DHCP 서버 주소 검색*

- **nx_dhcp_set_interface_index**: *클라이언트 네트워크 인터페이스 지정*

- **nx_dhcp_start**: *DHCP 처리 시작*

- **nx_dhcp_state_change_notify**: *애플리케이션에 DHCP 상태 변경 알림*

- **nx_dhcp_stop**: *DHCP 처리 중지*

- **nx_dhcp_user_option_retrieve**: *DHCP 옵션 검색*

- **nx_dhcp_user_option_convert**: *4바이트를 ULONG으로 변환*

인터페이스 특정 DHCP 클라이언트 서비스:

- **nx_dhcp_interface_clear_broadcast_flag**: *지정된 인터페이스의 클라이언트 메시지에서 브로드캐스트 플래그 지우기*

- **nx_dhcp_interface_enable**: *지정된 인터페이스에서 DHCP를 실행하는 인터페이스 사용*

- **nx_dhcp_interface_disable**: *지정된 인터페이스에서 DHCP를 실행하는 인터페이스 사용 안 함*

- **nx_dhcp_interface_decline**: *지정된 인터페이스에서 서버에 거부 메시지 보내기*

- **nx_dhcp_interface_force_renew**: *지정된 인터페이스에서 강제 갱신 메시지 보내기*

- **nx_dhcp_interface_reinitialize**: *지정된 인터페이스에서 DHCP 클라이언트 네트워크 매개 변수 지우기*

- **nx_dhcp_interface_release**: *지정된 인터페이스에서 서버에 릴리스 메시지 보내기*

- **nx_dhcp_interface_request_client_ip**: *지정된 인터페이스에서 특정 IP 주소 지정*

- **nx_dhcp_interface_send_request**: *지정된 인터페이스에서 서버에 DHCP 메시지 보내기*

- **nx_dhcp_interface_server_address_get**: *지정된 인터페이스에서 DHCP 서버 IP 주소 가져오기*

- **nx_dhcp_interface_start**: *지정된 인터페이스에서 DHCP 클라이언트 처리 시작*

- **nx_dhcp_interface_stop**: *지정된 인터페이스에서 DHCP 클라이언트 처리 중지*

- **nx_dhcp_interface_state_change_notify**: *지정된 인터페이스에서 DHCP 상태가 변경될 때 콜백 함수 설정*

- **nx_dhcp_interface_user_option_retrieve**: *지정된 인터페이스에서 지정된 DHCP 옵션 검색*

NX_DHCP_CLIENT_RESORE_STATE가 정의된 경우 DHCP 클라이언트 서비스:

- **nx_dhcp_resume**: *이전에 설정된 DHCP 클라이언트 상태 다시 시작*

- **nx_dhcp_suspend**: *DHCP 클라이언트 상태 처리 일시 중단*

- **nx_dhcp_client_get_record**: *DHCP 클라이언트 상태에 대한 레코드 만들기*

- **nx_dhcp_client_restore_record**: *이전에 저장된 레코드를 DHCP 클라이언트에 복원*

- **nx_dhcp_client_update_time_remaining**: *남아 있는 현재 DHCP 상태 시간 업데이트*

NX_DHCP_CLIENT_RESORE_STATE가 정의된 경우 인터페이스 특정 DHCP 클라이언트 서비스:

- **nx_dhcp_client_interface_get_record**: *지정된 인터페이스에서 DHCP 클라이언트 상태에 대한 레코드 만들기*

- **nx_dhcp_client_interface_restore_record**: *지정된 인터페이스에서 이전에 저장된 레코드를 DHCP 클라이언트에 복원*

- **nx_dhcp_client_interface_update_time_remaining**: *지정된 인터페이스에서 남아 있는 현재 DHCP 상태 시간 업데이트*

## <a name="nx_dhcp_create"></a>nx_dhcp_create

DHCP 인스턴스를 만듭니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 IP 인스턴스에 대한 DHCP 인스턴스를 만듭니다. 기본적으로 기본 인터페이스가 DHCP를 실행하는 데 사용하도록 설정됩니다. 이름 입력은 DHCP 클라이언트의 NetX 구현에서 사용되지 않지만 호스트 이름에 대한 RFC 1035 조건을 따라야 합니다. 총 길이는 255자를 초과할 수 없으며, 점으로 구분된 레이블은 문자로 시작하고 문자 또는 숫자로 끝나야 하며, 하이픈은 포함할 수 있지만 영숫자가 아닌 다른 문자는 포함할 수 없습니다.

애플리케이션에서 IP 인스턴스에 등록된 다른 인터페이스인 DHCP를 실행하려는 경우(*nx_ip_interface_attach* 사용) 애플리케이션에서 *nx_dhcp_set_interface_index* 를 호출하여 해당 인터페이스에서만 DHCP를 실행하거나 *nx_dhcp_interface_enable* 을 호출하여 해당 인터페이스에서도 DHCP를 실행합니다. 자세한 내용은 이러한 서비스에 대한 설명을 참조하세요.

> [!NOTE]
> 애플리케이션에서 DHCP 클라이언트 패킷 풀 페이로드가 RFC 2131 섹션 2(548바이트의 DHCP 메시지 데이터와 UDP, IP 및 실제 네트워크 프레임 헤더)에서 지정한 최소 DHCP 메시지 크기를 지원할 수 있는지 확인해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터  
- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터  
- **name_ptr** DHCP 인스턴스의 호스트 이름에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP를 성공적으로 만듦

- **NX_DHCP_INVALID_NAME** (0xA8) 잘못된 호스트 이름

- **NX_DHCP_INVALID_PAYLOAD** (0x9C) DHCP 메시지에 대한 페이로드가 너무 작음

- NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터

### <a name="allowed-from"></a>허용되는 원본

**스레드,** 초기화

### <a name="example"></a>예제

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a>nx_dhcp_interface_enable

DHCP를 실행하도록 지정된 인터페이스를 사용하도록 설정합니다. 

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Description

이 서비스를 사용하면 지정된 인터페이스에서 DHCP를 실행할 수 있습니다. 기본적으로 기본 인터페이스가 DHCP 클라이언트에 사용하도록 설정됩니다. 이 시점에서 *nx_dhcp_interface_start* 를 호출하여 이 인터페이스에서 DHCP를 시작하거나 사용하도록 설정된 모든 *nx_dhcp_start* 인터페이스에서 DHCP를 시작할 수 있습니다.

애플리케이션에서 먼저 *nx_ip_interface_attach.* 를 사용하여 이 인터페이스를 IP 인스턴스에 등록해야 합니다.

또한 이 인터페이스를 사용하도록 설정된 인터페이스 목록에 추가하려면 사용 가능한 DHCP 클라이언트 인터페이스 '레코드'가 있어야 합니다. 기본적으로 NX_DHCP_CLIENT_MAX_RECORDS가 1로 정의됩니다. 이 옵션을 DHCP 클라이언트를 동시에 실행하는 데 필요한 최대 인터페이스 수로 설정합니다. 일반적으로 NX_DHCP_CLIENT_MAX_RECORDS는 NX_MAX_PHYSICAL_INTERFACES와 동일합니다. 그러나 DHCP 클라이언트를 실행하는 데 필요한 것보다 더 많은 실제 인터페이스가 디바이스에 있는 경우 NX_DHCP_CLIENT_MAX_RECORDS를 해당 숫자보다 작게 설정하여 메모리를 절약할 수 있습니다. 실제 인터페이스와 DHCP 클라이언트 인터페이스 레코드의 일대일 매핑이 없습니다.

이 서비스와 *nx_dhcp_set_interface_index* 의 차이점은 후자는 DHCP를 실행하는 단일 인터페이스만 설정하는 반면, 이 서비스는 지정된 인터페이스를 DHCP에 사용하도록 설정된 클라이언트 인터페이스 목록에 추가한다는 것입니다.

DHCP에 대한 인터페이스를 사용하지 않도록 설정하기 위해 애플리케이션에서 *nx_dhcp_interface_disable* 서비스를 호출할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터  

- **interface_index** DHCP를 사용하도록 설정하는 인터페이스의 인덱스

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP를 성공적으로 사용하도록 설정함

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) DHCP에 사용하도록 설정할 다른 인터페이스에 사용할 수 있는 레코드가 없음

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) DHCP에 사용하도록 설정된 인터페이스

- NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드, 초기화

### <a name="example"></a>예제

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a>nx_dhcp_interface_disable

DHCP를 실행하도록 지정된 인터페이스를 사용하지 않도록 설정합니다. 

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Description

이 서비스를 사용하지 않으면 지정된 인터페이스에서 DHCP를 실행할 수 없습니다. 이 인터페이스에서 DHCP 클라이언트를 다시 초기화합니다.

DHCP 클라이언트를 다시 시작하려면 애플리케이션에서 *nx_dhcp_interface_enable* 을 사용하여 인터페이스를 다시 사용하도록 설정하고 *nx_dhcp_interface_start* 를 호출하여 DHCP를 다시 시작해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터  

- **interface_index** DHCP를 사용하지 않도록 설정하는 인터페이스의 인덱스

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP를 성공적으로 만듦

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스

- NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a>nx_dhcp_clear_broadcast_flag

DHCP 브로드캐스트 플래그를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a>Description

이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스에 대한 DHCP 메시지 헤더의 브로드캐스트 플래그를 설정하거나 지웁니다. 일부 DHCP 메시지(예: DISCOVER)의 경우 클라이언트에 IP 주소가 없으므로 브로드캐스트 플래그가 브로드캐스트로 설정됩니다.

__clear_flag__


- **NX_TRUE** 브로드캐스트 플래그가 지워짐(요청 유니캐스트 응답)

- **NX_FALSE** 브로드캐스트 플래그가 설정됨(요청 브로드캐스트 응답)

이 서비스는 라우터를 통해 DHCP 서버에 도달해야 하는 DHCP 클라이언트를 위한 것입니다. 여기서 라우터는 브로드캐스트 메시지 전달을 거부합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터  

- **clear_flag** 브로드캐스트 플래그를 설정하는 값

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 브로드캐스트 플래그를 성공적으로 업데이트함

- NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드, 초기화

### <a name="example"></a>예제

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a>nx_dhcp_interface_clear_broadcast_flag

지정된 인터페이스에서 브로드캐스트 플래그를 설정하거나 지웁니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a>Description

이 서비스를 사용하면 DHCP 클라이언트 호스트 애플리케이션이 DHCP 클라이언트 메시지의 브로드캐스트 플래그를 지정된 인터페이스의 DHCP 서버로 설정하거나 지울 수 있습니다. 자세한 내용은 **nx_dhcp_clear_broadcast_flag** 를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터

- **interface_index** 브로드캐스트 플래그를 설정하는 인터페이스의 인덱스  

- **clear_flag** 브로드캐스트 플래그를 설정하는 값

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 브로드캐스트 플래그를 성공적으로 업데이트함

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스

- NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드, 초기화

### <a name="example"></a>예제

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a>nx_dhcp_delete

DHCP 인스턴스를 삭제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 DHCP 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP를 성공적으로 삭제함

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a>nx_dhcp_ force_renew

강제 갱신 메시지를 보냅니다. 

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

이 서비스를 사용하면 DHCP에 사용하도록 설정된 호스트 애플리케이션의 모든 인터페이스에서 강제 갱신 메시지를 보낼 수 있습니다. DHCP 클라이언트는 BOUND 상태여야 합니다. 이 함수는 T1 시간 제한이 만료되기 전에 DHCP 클라이언트에서 갱신을 시도하도록 상태를 RENEW로 설정합니다.

여러 인터페이스에서 DHCP를 사용하도록 설정된 경우 특정 인터페이스에서 강제 갱신을 보내려면 *nx_dhcp_interface_force_renew* 를 사용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 강제 갱신을 성공적으로 보냄  

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a>nx_dhcp_interface_force_renew

지정된 인터페이스에서 강제 갱신 메시지를 보냅니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Description

이 서비스를 사용하면 입력 인터페이스가 DHCP에 사용하도록 설정된 경우 호스트 애플리케이션의 해당 인터페이스에서 강제 갱신 메시지를 보낼 수 있습니다(*nx_dhcp_interface_enable* 참조). 지정된 인터페이스의 DHCP 클라이언트가 BOUND 상태여야 합니다. 이 함수는 T1 시간 제한이 만료되기 전에 DHCP 클라이언트에서 갱신을 시도하도록 상태를 RENEW로 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 강제 갱신을 성공적으로 보냄  

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스

- NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a>nx_dhcp_packet_pool_set

DHCP 클라이언트 패킷 풀을 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Description

이 서비스를 사용하면 애플리케이션에서 포인터를 이 서비스 호출의 이전에 만든 패킷 풀에 전달하여 DHCP 클라이언트 패킷 풀을 만들 수 있습니다. 이 기능을 사용하려면 호스트 애플리케이션에서 NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL을 정의해야 합니다. 정의되면 *nx_dhcp_create* 서비스에서 클라이언트의 패킷 풀을 만들지 않습니다. 애플리케이션에서 패킷 풀을 만들 때 *nx_dhcp.h* 에서 NX_DHCP_PACKET_PAYLOAD로 정의된 DHCP 클라이언트 패킷 풀 페이로드에 대한 기본값을 사용하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터  

- **packet_pool_ptr** 이전에 만든 패킷 풀에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP 클라이언트 패킷 풀이 설정됨

- **NX_NOT_ENABLED** (0x14) 서비스가 사용하도록 설정되지 않음

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_DHCP_INVALID_PAYLOAD (0x9C) 페이로드가 너무 작음

### <a name="allowed-from"></a>허용되는 원본

애플리케이션 코드

### <a name="example"></a>예제

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a>nx_dhcp_request_client_ip

DHCP 인스턴스에 대해 요청된 IP 주소를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a>Description

이 서비스는 DHCP 클라이언트 레코드의 DHCP에 사용하도록 설정된 첫 번째 인터페이스의 DHCP 서버에서 요청할 DHCP 클라이언트에 대한 IP 주소를 설정합니다. *skip_discover_message* 플래그가 설정되면 DHCP 클라이언트에서 검색 메시지를 건너뛰고 요청 메시지를 보냅니다.

특정 인터페이스에서 DHCP 메시지의 특정 IP에 대한 요청을 설정하려면 *nx_dhcp_interface_request_client_ip* 서비스를 사용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터  

- **client_ip_address** DHCP 서버에서 요청하는 IP 주소

- **skip_discover_message** true이면 DHCP 클라이언트에서 요청 메시지를 보냅니다.  
false이면 검색 메시지를 보냅니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 요청된 IP 주소가 설정됨

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스

- NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스
 
### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a>nx_dhcp_interface_request_client_ip

지정된 인터페이스에서 DHCP 인스턴스에 대해 요청된 IP 주소를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a>Description

인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 지정된 인터페이스에서 DHCP 서버로부터 요청할 DHCP 클라이언트에 대한 IP 주소를 설정합니다(*nx_dhcp_interface_enable* 참조). *skip_discover_message* 플래그가 설정되면 DHCP 클라이언트에서 검색 메시지를 건너뛰고 요청 메시지를 보냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터

- **Interface_index** IP 주소를 요청하는 인터페이스의 인덱스

- **client_ip_address** DHCP 서버에서 요청하는 IP 주소

- **skip_discover_message** true이면 DHCP 클라이언트에서 요청 메시지를 보냅니다. 그렇지 않으면 검색 메시지를 보냅니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 요청된 IP 주소가 설정됨

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스

- NX_PTR_ERROR (0x16) 잘못된 IP 또는 DHCP 포인터

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스


### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a>nx_dhcp_reinitialize

DHCP 클라이언트 네트워크 매개 변수를 지웁니다. 

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

이 서비스는 호스트 애플리케이션 네트워크 매개 변수(IP 주소, 네트워크 주소 및 네트워크 마스크)를 지우고, DHCP에 사용하도록 설정된 모든 인터페이스에서 DHCP 클라이언트 상태를 지웁니다. DHCP 상태 시스템을 '다시 시작'하기 위해 *nx_dhcp_stop* 및 *nx_dhcp_start* 와 함께 사용됩니다. 

nx_dhcp_stop(&my_dhcp);  
nx_dhcp_reinitialize(&my_dhcp);  
nx_dhcp_start(&my_dhcp);


여러 인터페이스가 DHCP에 사용하도록 설정된 경우 특정 인터페이스에서 DHCP 클라이언트를 다시 초기화하려면 *nx_dhcp_interface_reinitialize* 서비스를 사용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP를 성공적으로 다시 초기화함 

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a>nx_dhcp_interface_reinitialize

지정된 인터페이스에서 DHCP 클라이언트 네트워크 매개 변수를 지웁니다. 

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Description

해당 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 지정된 인터페이스에서 네트워크 매개 변수(IP 주소, 네트워크 주소 및 네트워크 마스크)를 지웁니다(*nx_dhcp_interface_enable* 참조). 자세한 내용은 *nx_dhcp_reinitialize* 를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

- **interface_index** 다시 초기화하는 인터페이스의 인덱스

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 인터페이스를 성공적으로 다시 초기화함

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a>nx_dhcp_release

임대 IP 주소를 해제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

이 서비스는 RELEASE 메시지를 DHCP 서버로 보내 해당 서버에서 가져온 IP 주소를 해제합니다. 그런 다음, DHCP 클라이언트를 다시 초기화합니다. 이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스에 적용됩니다.

애플리케이션에서 *nx_dhcp_start* 호출하여 DHCP 클라이언트를 다시 시작할 수 있습니다.

특정 인터페이스에서 주소를 DHCP 서버로 다시 해제하려면 *nx_dhcp_interface_release* 서비스를 사용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP를 성공적으로 해제함  

- **NX_DHCP_NOT_BOUND** (0x94) IP 주소가 임대되지 않았으므로 해제할 수 없음

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a>nx_dhcp_interface_release

지정된 인터페이스에서 IP 주소를 해제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Description

이 서비스는 지정된 인터페이스에서 가져온 DHCP 서버의 IP 주소를 해제하고 DHCP 클라이언트를 다시 초기화합니다. DHCP 클라이언트는 *nx_dhcp_start* 를 호출하여 다시 시작할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP를 성공적으로 해제함

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스

- **NX_DHCP_NOT_BOUND** (0x94) IP 주소가 임대되지 않았으므로 해제할 수 없음

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a>nx_dhcp_decline

DHCP 서버에서 IP 주소를 거부합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스의 DHCP 서버에서 임대된 IP 주소를 거부합니다. NX_DHCP_CLIENT_ SEND_ ARP_PROBE가 정의된 경우 IP 주소를 이미 사용하고 있음을 검색하면 DHCP 클라이언트에서 DECLINE 메시지를 보냅니다. NetX DHCP 클라이언트에서 ARP 프로브 구성에 대한 자세한 내용은 챕터 1의 **ARP 프로브** 를 참조하세요.

주소를 다른 방법으로 사용하고 있음을 검색하는 경우 애플리케이션에서 이 서비스를 사용하여 IP 주소를 거부할 수 있습니다.

이 서비스는 *nx_dhcp_start* 를 호출하여 다시 시작할 수 있도록 DHCP 클라이언트를 다시 초기화합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 거부를 성공적으로 보냄  

- **NX_DHCP_NOT_STARTED** (0x96) DHCP 인스턴스가 시작되지 않음

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a>nx_dhcp_interface_decline

지정된 인터페이스에서 DHCP 서버의 IP 주소를 거부합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Description

이 서비스는 DHCP 서버에서 할당한 IP 주소를 거부하기 위해 DECLINE 메시지를 서버에 보냅니다. 또한 DHCP 클라이언트를 다시 초기화합니다. 자세한 내용은 *nx_dhcp_decline* 을 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

- **Interface_index** IP 주소를 거부하는 인터페이스의 인덱스

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP 거부 메시지를 보냄  

- **NX_DHCP_NOT_BOUND** (0x94) DHCP 클라이언트가 바인딩되지 않음

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a>nx_dhcp_send_request

DHCP 메시지를 서버에 보냅니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a>Description

이 서비스는 DHCP 클라이언트 레코드에 있는 DHCP에 사용하도록 설정된 첫 번째 인터페이스에서 지정된 DHCP 메시지를 DHCP 서버에 보냅니다. RELEASE 또는 DECLINE 메시지를 보내려면 애플리케이션에서 *nx_dhcp[_interface]_release*() 또는 *nx_dhcp_interface_decline()* 서비스를 각각 사용해야 합니다.

INFORM_REQUEST 메시지 유형을 보내는 경우를 제외하고 이 서비스를 사용하려면 DHCP 클라이언트를 시작해야 합니다.

> [!NOTE] 
> 이 서비스는 호스트 애플리케이션에서 DHCP 클라이언트 상태 시스템을 '구동'하기 위한 것이 아닙니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터  

- **dhcp_message_type** 메시지 요청(*nx_dhcp.h* 에서 정의됨)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP 메시지를 보냄  

- **NX_DHCP_NOT_STARTED** (0x96) 잘못된 인터페이스 인덱스

- **NX_DHCP_INVALID_MESSAGE** (0x9B) 잘못된 보내는 메시지 유형

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a>nx_dhcp_interface_send_request

특정 인터페이스에서 DHCP 메시지를 서버에 보냅니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a>Description

지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 메시지를 DHCP 서버에 보냅니다. RELEASE 또는 DECLINE 메시지를 보내려면 애플리케이션에서 *nx_dhcp[_interface]_release*() 또는 *nx_dhcp_interface_decline()* 서비스를 각각 사용해야 합니다.

DHCP INFORM REQUEST 메시지 유형을 보내는 경우를 제외하고 이 서비스를 사용하려면 DHCP 클라이언트를 시작해야 합니다.

이 서비스는 호스트 애플리케이션에서 DHCP 클라이언트 상태 시스템을 '구동'하기 위한 것이 아닙니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터

- **Interface_index** 메시지를 보내는 인터페이스의 인덱스  

- **dhcp_message_type** 메시지 요청(*nx_dhcp.h* 에서 정의됨)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP 메시지를 보냄  

- **NX_DHCP_NOT_STARTED** (0x96) 잘못된 인터페이스 인덱스

- **NX_DHCP_INVALID_MESSAGE** (0x9B) 잘못된 보내는 메시지 유형

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) DHCP에 사용하지 않도록 설정된 인터페이스

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a>nx_dhcp_server_address_get

DHCP 클라이언트의 DHCP 서버 IP 주소를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a>Description

이 서비스는 DHCP 클라이언트 레코드에 있는 DHCP에 사용하도록 설정된 첫 번째 인터페이스에서 DHCP 클라이언트 DHCP 서버 IP 주소를 검색합니다. 호출자는 DHCP 클라이언트가 DHCP 서버에서 할당한 IP 주소에 바인딩된 후에만 이 서비스를 사용할 수 있습니다. 호스트 애플리케이션에서 *nx_ip_status_check* 서비스를 사용하여 IP 주소가 설정되어 있는지 확인하거나 *nx_dhcp_state_change_notify* 를 사용하여 DHCP 클라이언트 상태가 NX_DHCP_STATE_BOUND인지 쿼리할 수 있습니다. 상태 변경 콜백 함수를 설정하는 방법에 대한 자세한 내용은 *nx_dhcp_state_change_notify* 를 참조하세요.

여러 인터페이스가 DHCP 클라이언트에 사용하도록 설정된 경우 특정 인터페이스에서 DHCP 서버를 찾으려면 *nx_dhcp_interface_server_address_get* 서비스를 사용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터

- **server_address** 서버 IP 주소에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP 서버 주소가 반환됨

- NX_PTR_ERROR (0x16) 잘못된 입력 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a>nx_dhcp_interface_server_address_get

지정된 인터페이스에서 DHCP 클라이언트의 DHCP 서버 IP 주소를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a>Description

지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 DHCP 클라이언트 DHCP 서버 IP 주소를 검색합니다. DHCP 클라이언트는 바인딩됨 상태여야 합니다. 해당 인터페이스에서 DHCP 클라이언트를 시작하면 호스트 애플리케이션에서 *nx_ip_status_check* 서비스를 사용하여 IP 주소가 설정되어 있는지 확인하거나 DHCP 클라이언트 상태 변경 콜백을 사용하여 DHCP 클라이언트 상태가 NX_DHCP_STATE_BOUND인지 쿼리할 수 있습니다. 상태 변경 콜백 함수를 설정하는 방법에 대한 자세한 내용은 *nx_dhcp_state_change_notify* 를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터

- **Interface_index** IP 주소를 가져오는 인터페이스의 인덱스  

- **server_address** 서버 IP 주소에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP 서버 주소가 반환됨

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP에 사용하도록 설정된 인터페이스가 없음

- **NX_DHCP_NOT_BOUND** (0x94) DHCP 클라이언트가 바인딩되지 않음

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a>nx_dhcp_set_interface_index

DHCP 인스턴스에 대한 네트워크 인터페이스를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a>Description

이 서비스는 단일 네트워크 인터페이스에 대해 구성된 DHCP 클라이언트를 실행할 때 DHCP 인스턴스에서 DHCP 서버에 연결하는 네트워크 인터페이스를 설정합니다.

기본적으로 DHCP 클라이언트가 기본 인터페이스에서 실행됩니다. 보조 서비스에서 DHCP를 실행하려면 이 서비스를 사용하여 보조 인터페이스를 DHCP 클라이언트 인터페이스로 설정합니다. 애플리케이션에서 이전에 *nx_ip_interface_attach* 서비스를 사용하여 지정된 인터페이스를 IP 인스턴스에 등록해야 합니다.

이 서비스는 하나의 인터페이스에서만 DHCP 클라이언트를 실행하려는 애플리케이션을 위한 것입니다. 여러 인터페이스에서 DHCP를 실행하는 방법에 대한 자세한 내용은 *nx_dhcp_interface_enable* 을 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 제어 블록에 대한 포인터  

- **index** 디바이스 네트워크 인터페이스의 인덱스

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 인터페이스를 성공적으로 설정함

- **NX_INVALID_INTERFACE** (0x4C) 잘못된 네트워크 인터페이스

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) DHCP에 사용하도록 설정된 인터페이스

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) 다른 레코드에 사용할 수 있는 레코드가 없음

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a>nx_dhcp_start

DHCP 처리를 시작합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCP에 사용하도록 설정된 모든 인터페이스에서 DHCP 처리를 시작합니다. 기본적으로 애플리케이션에서 *nx_dhcp_create* 를 호출할 때 기본 인터페이스가 DHCP에 사용하도록 설정됩니다.

IP 인스턴스가 DHCP 클라이언트 인터페이스의 IP 주소에 바인딩되어 있는지 확인하려면 *nx_ip_status_check* 를 사용하여 IP 주소가 유효한지 확인합니다.

이미 DHCP를 실행하는 다른 인터페이스가 있는 경우 이 서비스는 영향을 주지 않습니다.

여러 인터페이스가 사용하도록 설정된 경우 특정 인터페이스에서 DHCP를 시작하려면 *nx_dhcp_interface_start* 서비스를 사용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP를 성공적으로 시작함  

- **NX_DHCP_ALREADY_STARTED** (0x93) DHCP가 이미 시작됨

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a>nx_dhcp_interface_start

지정된 인터페이스에서 DHCP 처리를 시작합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Description

지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 DHCP 처리를 시작합니다. 인터페이스를 DHCP에 사용하도록 설정하는 방법에 대한 자세한 내용은 *nx_dhcp_interface_enable*()을 참조하세요. 기본적으로 애플리케이션에서 *nx_dhcp_create* 를 호출할 때 기본 인터페이스가 DHCP에 사용하도록 설정됩니다.

DHCP 클라이언트를 실행하는 다른 인터페이스가 없는 경우 이 서비스는 DHCP 클라이언트 스레드를 시작/다시 시작하고 DHCP 클라이언트 타이머를 (다시) 활성화합니다.  
  
애플리케이션에서 *nx_ip_status_check* 를 사용하여 IP 주소를 가져왔는지 확인해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

- **Interface_index** DHCP 클라이언트를 시작하는 인덱스

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP를 성공적으로 시작함  

- **NX_DHCP_ALREADY_STARTED** (0x93) DHCP 인스턴스가 이미 시작됨

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a>nx_dhcp_state_change_notify

DHCP 상태 변경 콜백 함수를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a>Description

이 서비스는 DHCP 상태 변경을 애플리케이션에 알리기 위해 지정된 dhcp_state_change_notify 콜백 함수를 등록합니다. 콜백 함수는 DHCP 클라이언트가 전환된 상태를 제공합니다.

다양한 DHCP 상태와 관련된 값은 다음과 같습니다.

| 주                             | 값 |
|-----------------------------------|-------|
| NX\_DHCP\_STATE\_BOOT             | 1     |
| NX\_DHCP\_STATE\_INIT             | 2     |
| NX\_DHCP\_STATE\_SELECTING        | 3     |
| NX\_DHCP\_STATE\_REQUESTING       | 4     |
| NX\_DHCP\_STATE\_BOUND            | 5     |
| NX\_DHCP\_STATE\_RENEWING         | 6     |
| NX\_DHCP\_STATE\_REBINDING        | 7     |
| NX_DHCP_STATE_FORCERENEW          | 8     |
| NX\_DHCP\_STATE\_ADDRESS\_PROBING | 9     |


### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

- **dhcp_state_change_notify** 상태 변경 콜백 함수 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함  

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드, 초기화

### <a name="example"></a>예제

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a>nx_dhcp_interface_state_change_notify

지정된 인터페이스에서 DHCP 상태 변경 콜백 함수를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a>Description

이 서비스는 DHCP 상태 변경을 애플리케이션에 알리기 위해 지정된 콜백 함수를 등록합니다. 콜백 함수 입력 인수는 인터페이스 인덱스 및 DHCP 클라이언트가 해당 인터페이스에서 전환된 상태입니다.

상태 변경 함수에 대한 자세한 내용은 *nx_dhcp_state_change_notify*()를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

- **dhcp_interface_state_change_notify** 애플리케이션 콜백 함수 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함  

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

### <a name="allowed-from"></a>허용되는 원본

스레드, 초기화

### <a name="example"></a>예제

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a>nx_dhcp_stop

DHCP 처리를 중지합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCP 처리를 시작한 모든 인터페이스에서 DHCP 처리를 중지합니다. DHCP를 처리하는 인터페이스가 없는 경우 이 서비스는 DHCP 클라이언트 스레드를 일시 중단하고 DHCP 클라이언트 타이머를 비활성화합니다.

여러 인터페이스가 DHCP에 사용하도록 설정된 경우 특정 인터페이스에서 DHCP를 중지하려면 *nx_dhcp_interface_stop* 서비스를 사용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP를 성공적으로 중지함

- **NX_DHCP_NOT_STARTED** (0x96) DHCP 인스턴스가 시작되지 않음

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a>nx_dhcp_interface_stop

지정된 인터페이스에서 DHCP 처리를 중지합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Description

DHCP가 이미 시작된 경우 이 서비스는 지정된 인터페이스에서 DHCP 처리를 중지합니다. DHCP를 실행하는 다른 인터페이스가 없는 경우 DHCP 스레드 및 타이머가 일시 중단됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

- **Interface_index** DHCP 처리를 중지하는 인터페이스

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) DHCP를 성공적으로 중지함

- **NX_DHCP_NOT_STARTED** (0x96) DHCP가 시작되지 않음

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a>nx_dhcp_user_option_retrieve

마지막 서버 응답에서 DHCP 옵션을 검색합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Description

이 서비스는 DHCP 클라이언트 레코드에 있는 DHCP에 사용하도록 설정된 첫 번째 인터페이스에서 DHCP 옵션 버퍼로부터 지정된 DHCP 옵션을 검색합니다. 성공하면 옵션 데이터가 지정된 버퍼에 복사됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터  

- **request_option** RFC에서 지정한 DHCP 옵션. *nx_dhcp.h* 의 NX_DHCP_OPTION 옵션을 참조하세요.

- **destination_ptr** 응답 문자열의 대상에 대한 포인터  

- **destination_size** 대상 및 반환 시 반환되는 바이트 수를 저장할 대상의 크기에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 옵션을 성공적으로 검색함  

- **NX_DHCP_NOT_BOUND** (0x94) DHCP 클라이언트가 바인딩되지 않음

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP에 사용하도록 설정된 인터페이스가 없음

- **NX_DHCP_DEST_TO_SMALL** (0x95) 대상이 너무 작아서 응답을 보유할 수 없음

- **NX_DHCP_PARSE_ERROR** (0x97) 서버 응답에 DHCP 옵션이 없음

- NX_PTR_ERROR (0x16) 잘못된 입력 포인터

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a>nx_dhcp_interface_user_option_retrieve

지정한 인터페이스에서 마지막 서버 응답으로부터 DHCP 옵션을 검색합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Description

지정된 인터페이스가 DHCP에 사용하도록 설정된 경우 이 서비스는 해당 인터페이스에서 DHCP 옵션 버퍼로부터 지정된 DHCP 옵션을 검색합니다. 성공하면 옵션 데이터가 지정된 버퍼에 복사됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

- **Interface_index** 지정된 옵션을 검색하는 인덱스  

- **request_option** RFC에서 지정한 DHCP 옵션. *nx_dhcp.h* 의 NX_DHCP_OPTION 옵션을 참조하세요.  

- **destination_ptr** 응답 문자열의 대상에 대한 포인터  

- **destination_size** 대상 및 반환 시 반환되는 바이트 수를 저장할 대상의 크기에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 옵션을 성공적으로 검색함  

- **NX_DHCP_NOT_BOUND** (0x94) IP 주소가 할당되지 않음

- **NX_DHCP_DEST_TO_SMALL** (0x95) 버퍼가 너무 작음

- **NX_DHCP_PARSE_ERROR** (0x97) 서버 응답에 DHCP 옵션이 없음

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_CALLER_ERROR (0x11) 서비스의 잘못된 호출자

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a>nx_dhcp_user_option_convert

4바이트를 ULONG으로 변환합니다.

### <a name="prototype"></a>프로토타입

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a>Description

이 서비스는 "option_string_ptr"에서 가리키는 4개 문자를 서명되지 않은 long 값으로 변환합니다. 특히 IP 주소가 있는 경우 유용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **option_string_ptr** 이전에 검색한 옵션 문자열에 대한 포인터

### <a name="return-values"></a>반환 값

- **Value** 처음 4바이트의 값

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a>nx_dhcp_user_option_add_callback_set

사용자 제공 옵션을 추가하기 위한 콜백 함수를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a>Description

이 서비스는 사용자 제공 옵션을 추가하기 위해 지정된 콜백 함수를 등록합니다.

콜백 함수가 지정된 경우 애플리케이션에서 사용자가 제공한 옵션을 iface_index 및 message_type별로 패킷에 추가할 수 있습니다.

> [!NOTE]
> 사용자의 루틴에 있습니다. 사용자가 제공한 옵션을 추가하는 경우 애플리케이션에서 DHCP 옵션 형식을 따라야 합니다. 사용자 옵션의 총 크기는 user_option_length보다 작거나 같아야 하며, user_option_length를 실제 옵션 길이로 업데이트해야 합니다. 옵션이 성공적으로 추가되면 NX_TRUE를 반환하고, 그렇지 않으면 NX_FALSE를 반환합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ip_ptr** 이전에 만든 DHCP 인스턴스에 대한 포인터

- **dhcp_user_option_add** 사용자 옵션 추가 함수에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 콜백을 성공적으로 설정함

- NX_PTR_ERROR (0x16) 잘못된 포인터

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
