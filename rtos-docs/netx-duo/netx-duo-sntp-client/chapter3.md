---
title: 3장 - Azure RTOS NetX Duo SNTP 클라이언트 서비스 설명
description: 이 장에서는 아래에 나열된 모든 NetX Duo SNTP 클라이언트 서비스를 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810561"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a>3장 - Azure RTOS NetX Duo SNTP 클라이언트 서비스 설명

이 장에서는 아래에 나열된 모든 Azure RTOS NetX Duo SNTP 클라이언트 서비스를 알파벳 순서로 설명하고 있습니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- **nx_sntp_client_create**: *SNTP 클라이언트 만들기*
- **nx_sntp_client_delete**: *SNTP 클라이언트 삭제*
- **nx_sntp_client_get_local_time**: *SNTP 클라이언트 로컬 시간 가져오기*
- **nx_sntp_client_get_local_time_extended**: *SNTP 클라이언트 로컬 시간 가져오기*
- **nx_sntp_client_initialize_broadcast**: *IPv4 브로드캐스트 작업을 위해 클라이언트 초기화*
- **nxd_sntp_client_initialize_broadcast**: *IPv6 또는 IPv4 브로드캐스트 작업을 위해 클라이언트 초기화*
- **nx_sntp_client_initialize_unicast**: *IPv4 유니캐스트 작업을 위해 클라이언트 초기화*
- **nxd_sntp_client_initialize_unicast**: *IPv4 또는 IPv6 유니캐스트 작업을 위해 클라이언트 초기화*
- **nx_sntp_client_receiving_udpates**: *클라이언트가 현재 유효한 SNTP 업데이트를 받고 있음*
- **nx_sntp_client_request_unicast_time**: *유니캐스트 요청을 NTP 서버로 직접 보내기*
- **nx_sntp_client_run_broadcast**: *브로드캐스트 모드로 클라이언트 실행* .
- **nx_sntp_client_run_unicast**: *클라이언트를 유니캐스트 모드로 실행*
- **nx_sntp_client_set_local_time**: *SNTP 클라이언트 초기 로컬 시간 설정*
- **nx_SNTP_client_set_time_update_notify**: *SNTP 업데이트 콜백 설정*
- **nx_SNTP_client_stop**: *SNTP 클라이언트 스레드 중지*
- **nx_sntp_client_utility_display_date_and_time**: *NTP 시간(초) 표시*
- **nx_sntp_client_utility_msecs_to_fraction**: *밀리초를 NTP 분율 구성 요소로 변환*
- **nx_sntp_client_utility_usecs_to_fraction**: *마이크로초를 NTP 분율 구성 요소로 변환*
- **nx_sntp_client_utility_fraction_to_usecs**: *NTP 분율 구성 요소를 마이크로초로 변환*


## <a name="nx_sntp_client_create"></a>nx_sntp_client_create

SNTP 클라이언트 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a>Description

이 서비스는 SNTP 클라이언트 인스턴스를 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

- **client_ptr** 클라이언트 IP 인스턴스에 대한 포인터입니다.

- **iface_index** SNTP 네트워크 인터페이스에 대한 인덱스입니다.

- **packet_pool_ptr** 클라이언트 패킷 풀에 대한 포인터입니다.

- **leap_second_handler** 임박한 윤초에 대한 애플리케이션 응답의 콜백입니다.

- **kiss_of_death_handler** 수신 Kiss of Death 패킷에 대한 애플리케이션 응답의 콜백입니다.

- **random_number_generator** 난수 생성기 서비스에 대한 콜백입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트를 만들었습니다.

- **NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD**(0xD2A) 잘못된 포인터가 아닌 입력입니다.

- NX_PTR_ERROR (0x07) 잘못된 포인터 입력입니다.

- NX_INVALID_INTERFACE(0x4C) 잘못된 네트워크 인터페이스입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a>nx_sntp_client_delete

SNTP 클라이언트 삭제

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 SNTP 클라이언트 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트를 만들었습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

- NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a>nx_sntp_client_get_local_time

SNTP 클라이언트 로컬 시간 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a>Description

이 서비스는 문자열 메시지 형식으로 데이터를 수신하는 옵션 버퍼 포인터 입력을 사용하여 SNTP 클라이언트 로컬 시간을 가져옵니다.

이 서비스는 더 이상 사용되지 않습니다. 개발자는 nx_SNTP_client_get_local_time_extended()로 마이그레이션하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

- **seconds** 로컬 시간(초)에 대한 포인터입니다.

- **fraction** 로컬 시간 분율 구성 요소입니다.

- **buffer** 시간 데이터를 쓸 버퍼에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트를 만들었습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

- NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a>nx_sntp_client_get_local_time_extended

확장된 SNTP 클라이언트 로컬 시간 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a>Description

이 서비스는 문자열 메시지 형식으로 데이터를 수신하는 옵션 버퍼 포인터 입력을 사용하여 확장된 SNTP 클라이언트 로컬 시간을 가져옵니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

- **seconds** 로컬 시간(초)에 대한 포인터입니다.

- **fraction** 분율 구성 요소에 대한 포인터입니다.

- **buffer** 시간 데이터를 쓸 버퍼에 대한 포인터입니다.

- **buffer_size** 버퍼의 길이입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트를 만들었습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

- NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.

- NX_SIZE_ERROR(0x09) 버퍼 크기 검사가 실패합니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a>nx_sntp_client_initialize_broadcast

브로드캐스트 작업을 위해 클라이언트를 초기화합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a>Description

이 서비스는 SNTP 서버 IP 주소를 설정하고 SNTP 시작 매개 변수 및 시간 제한을 초기화하여 브로드캐스트 작업을 위해 클라이언트를 초기화합니다. 멀티캐스트 및 브로드캐스트 주소 중 하나라도 null이 아니면 멀티캐스트 주소가 선택됩니다. 두 가지 주소가 모두 null이면 오류가 반환됩니다. 참고로, IPv4 서버 주소만 지원됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

- **multicast_server_address** SNTP 멀티캐스트 주소입니다.

- **broadcast_time_server** SNTP 서버 브로드캐스트 주소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트를 만들었습니다.

- **NX_INVALID_PARAMETERS**(0x4D) 비포인터 입력이 잘못되었습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

- NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a>nxd_sntp_client_initialize_broadcast

IPv4 또는 IPv6 브로드캐스트 작업을 위해 클라이언트 초기화

### <a name="prototype"></a>프로토타입

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a>Description

이 서비스는 SNTP 서버 IP 주소를 설정하고 SNTP 시작 매개 변수 및 시간 제한을 초기화하여 브로드캐스트 작업을 위해 클라이언트를 초기화합니다. 브로드캐스트 및 멀티캐스트 주소 포인터 중 하나라도 null이 아닌 경우 멀티캐스트 주소가 선택됩니다. 두 주소 포인터가 모두 null이면 오류가 반환됩니다. IPv4 및 IPv6 주소 유형이 모두 지원됩니다. IPv6에서는 브로드캐스트를 지원하지 않으므로 브로드캐스트 주소 포인터가 IPv6로 설정되면 오류가 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

- **multicast_server_address** SNTP 서버 멀티캐스트 주소입니다.

- **broadcast_server_address** SNTP 서버 브로드캐스트 주소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트를 초기화했습니다.

- NX_SNTP_PARAM_ERROR(0xD0D) 잘못된 비포인터 입력입니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

- NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.


### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a>nx_sntp_client_initialize_unicast

유니캐스트에서 실행되도록 SNTP 클라이언트 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a>Description

이 서비스는 SNTP 서버 IP 주소를 설정하고 SNTP 시작 매개 변수 및 시간 제한을 초기화하여 유니캐스트 작업을 위해 클라이언트를 초기화합니다. 참고로, IPv4 서버 주소만 지원됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

- **unicast_time_server** SNTP 서버 IP 주소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트를 초기화했습니다.

- NX_INVALID_PARAMETERS(0x4D) 비포인터 입력이 잘못되었습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

- NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a>nxd_sntp_client_initialize_unicast

IPv4 또는 IPv6 유니캐스트에서 실행되도록 SNTP 클라이언트 설정

### <a name="prototype"></a>프로토타입

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a>Description

이 서비스는 SNTP 서버 IP 주소를 설정하고 SNTP 시작 매개 변수 및 시간 제한을 초기화하여 유니캐스트 작업을 위해 클라이언트를 초기화합니다. IPv4 및 IPv6 주소 유형이 모두 지원됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

- **unicast_time_server** SNTP 서버 IP 주소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 클라이언트를 초기화했습니다.

- NX_INVALID_PARAMETERS(0x4D) 비포인터 입력이 잘못되었습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

- NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a>nx_sntp_client_receiving_updates

클라이언트에서 유효한 업데이트를 받는지 여부 표시

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a>Description

이 서비스는 클라이언트가 유효한 SNTP 업데이트를 수신하고 있는지 여부를 나타냅니다. 유효한 업데이트 없이 최대 시간이 경과하거나 잘못된 연속 업데이트에 대한 제한을 초과하면 수신 상태가 false로 반환됩니다. SNTP 클라이언트가 아직 실행 중이고, 애플리케이션이 다른 유니캐스트 또는 브로드캐스트/멀티캐스트 서버를 사용하여 SNTP 클라이언트를 다시 시작하려고 하면  서비스를 사용하여 SNTP 클라이언트를 중지하고, 다른 서버에서 초기화 서비스 중 하나를 사용하여 클라이언트를 다시 초기화해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

- **receive_status** 클라이언트가 유효한 업데이트를 수신하는지 나타내기 위한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 클라이언트가 업데이트 상태를 받았습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a>nx_sntp_client_request_unicast_time

유니캐스트 요청을 NTP 서버로 직접 보내기


### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a>Description

이 서비스를 사용하여 애플리케이션에서는 SNTP 클라이언트 스레드 작업과는 비동기식으로 유니캐스트 요청을 NTP 서버로 직접 보낼 수 있습니다. 대기 옵션은 응답을 대기하는 시간을 지정합니다. 성공하면 애플리케이션은 다른 SNTP 클라이언트 서비스를 사용하여 최신 시간을 얻을 수 있습니다. 자세한 내용은 **SNTP 비동기 유니캐스트 요청** 섹션을 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

- **Wait_option** NTP 응답(타이머 틱)에 대한 대기 옵션입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 클라이언트가 유니캐스트 업데이트를 성공적으로 보내고 받습니다.

- **NX_SNTP_CLIENT_NOT_STARTED**(0xD0B) 클라이언트 스레드가 시작되지 않았습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

- NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a>nx_sntp_client_run_broadcast

브로드캐스트 모드로 클라이언트 실행

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 클라이언트를 브로드캐스트 모드로 시작하여 SNTP 서버의 브로드캐스트를 수신 대기합니다. 유효한 브로드캐스트 SNTP 메시지가 수신되면 업데이트 없는 최대 시간 경과에 대한 SNTP 클라이언트 제한 시간 및 수신된 잘못된 연속 메시지 수가 다시 설정됩니다. 이러한 한도를 초과하는 경우 SNTP 클라이언트는 업데이트 수신을 계속 대기하지만 서버 상태를 잘못됨으로 설정합니다. 애플리케이션은 SNTP 클라이언트 작업에서 서버 상태를 폴링할 수 있으며, 잘못된 경우 SNTP 클라이언트를 중지하고 다른 SNTP 브로드캐스트 주소를 사용하여 다시 초기화할 수 있습니다. 유니캐스트 SNTP 서버로 전환할 수도 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **status** --------실제 완료 상태입니다.

- **NX_SNTP_CLIENT_ALREADY_STARTED**(0XD0C) 클라이언트가 이미 시작되었습니다.

- **NX_SNTP_CLIENT_NOT_INITIALIZED**(0xD01) 클라이언트가 초기화되지 않았습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

- NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a>nx_sntp_client_run_unicast

유니캐스트 모드에서 클라이언트 실행

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 시간 업데이트를 위해 SNTP 서버에 유니캐스트 요청을 주기적으로 전송하는 유니캐스트 모드로 클라이언트를 시작합니다. 유효한 SNTP 메시지가 수신되면 업데이트 없는 최대 시간 경과에 대한 SNTP 클라이언트 제한 시간, 초기 폴링 간격 및 수신된 잘못된 연속 메시지 수가 다시 설정됩니다. 이러한 한도를 초과하는 경우 SNTP 클라이언트는 계속해서 폴링하고 업데이트 수신을 대기하지만 서버 상태를 잘못됨으로 설정합니다. 애플리케이션은 SNTP 클라이언트 작업에서 서버 상태를 폴링할 수 있으며, 잘못된 경우 SNTP 클라이언트를 중지하고 다른 SNTP 유니캐스트 주소를 사용하여 다시 초기화할 수 있습니다. 브로드캐스트 SNTP 서버로 전환할 수도 있습니다.

.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 유니캐스트 모드로 클라이언트를 시작했습니다.

- **NX_SNTP_CLIENT_ALREADY_STARTED**(0XD0C) 클라이언트가 이미 시작되었습니다.

- **NX_SNTP_CLIENT_NOT_INITIALIZED**(0xD01) 클라이언트가 초기화되지 않았습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

- NX_CALLER_ERROR(0x11) 잘못된 서비스 호출자입니다.


### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a>nx_sntp_client_set_local_time

SNTP 클라이언트 로컬 시간 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a>Description

이 서비스는 SNTP 형식(예: 초 및 초의 분율을 16진수 형식으로 입력하는 형식인 '분율')의 입력 시간을 사용하여 SNTP 클라이언트 로컬 시간을 설정합니다. 이 서비스는 실시간 클록과 같은 독립적인 시간 키퍼에서 SNTP 클라이언트 로컬 시간을 업데이트하기 위해 고안되었습니다. SNTP 프로토콜은 SNTP 시간 업데이트가 있을 때 로컬 클록 시간이 '드리프트'되지 않도록 하는 데 사용됩니다. SNTP 서버 시간 업데이트는 SNTP 클라이언트 로컬 시간에 대한 유일한 입력일 수 있지만, 애플리케이션 디바이스에 독립적인 시간 키퍼가 없는 경우라면 유일한 입력이 아닐 것입니다.

이 API를 사용하여 SNTP 클라이언트 스레드를 시작하기 전에 SNTP 클라이언트에 기본 시간을 제공할 수도 있습니다. SNTP 클라이언트 로컬 시간이 유효한 시간 데이터에 대해 수신된 업데이트와 비교됩니다. 업데이트를 처음 받을 때는 매우 큰 차이가 있을 수 있습니다. 따라서 SNTP 클라이언트가 첫 번째 업데이트에서 불일치를 무시하는 옵션이 제공됩니다. 이러한 방식으로, 기본 시간 없이 SNTP 클라이언트를 시작할 수 있습니다. 입력 시간은 알려진 Epoch 시간(일반적으로 인터넷에서 사용 가능)에서 얻을 수 있으며, 1900년 1월 1일 이후부터 새 'Epoch'가 시작될 2036년까지의 초 수로 계산됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

- **seconds** 시간 입력의 초 구성 요소입니다.

- **fraction** SNTP 분율 형식의 하위 초 구성 요소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 로컬 시간을 설정했습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

### <a name="allowed-from"></a>허용 위치

초기화

### <a name="example"></a>예제

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a>nx_sntp_client_set_time_update_notify

SNTP 업데이트 콜백 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a>Description

이 서비스는 SNTP 클라이언트가 유효한 시간 업데이트를 받을 때 애플리케이션에 알리도록 콜백을 설정합니다. 실제 SNTP 메시지와 SNTP 클라이언트의 로컬 시간(일반적으로 동일함)을 NTP 형식으로 제공합니다. 애플리케이션은 NTP 데이터를 직접 사용하거나 nx_sntp_client_utility_display_date_time 서비스를 호출하여 시간을 사람이 읽을 수 있는 형식으로 변환할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

- **time_update_cb** 콜백 함수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 콜백을 설정했습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

### <a name="allowed-from"></a>허용 위치

초기화

### <a name="example"></a>예제

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a>nx_sntp_client_stop

SNTP 클라이언트 스레드 중지

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 SNTP 클라이언트 스레드를 중지합니다. 무한 루프로 실행되는 SNTP 클라이언트 스레드 작업은 모든 반복에서 일시 중지하여 SNTP 클라이언트 상태의 제어를 해제하고 애플리케이션이 SNTP 클라이언트에서 API 호출을 수행할 수 있도록 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 클라이언트 스레드를 중지했습니다.

- **NX_SNTP_CLIENT_NOT_STARTED**(0xDB) SNTP 클라이언트 스레드가 시작되지 않았습니다.

- NX_PTR_ERROR(0x07) 잘못된 포인터 입력입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a>nx_sntp_client_utility_display_date_time

NTP 시간을 날짜 및 시간 문자열로 변환

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a>Description

이 서비스는 SNTP 클라이언트 로컬 시간을 년월일 형식으로 변환하고 제공 된 버퍼의 날짜를 반환합니다. NX_SNTP_CURRENT_YEAR는 현재 클라이언트 시간과 같은 연도일 필요는 없지만 정의해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **client_ptr** SMTP 클라이언트에 대한 포인터입니다.

- **buffer** 날짜를 저장할 버퍼에 대한 포인터입니다.

- **length** 입력 버퍼의 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 변환에 성공했습니다.

- **NX_SNTP_ERROR_CONVERTING_DATETIME**(0xD08) NX_SNTP_CURRENT_YEAR가 정의되지 않았거나 로컬 클라이언트 시간이 설정되지 않았습니다.

- **NX_SNTP_INVALID_DATETIME_BUFFER**(0xD07) 버퍼 길이가 부족합니다.


### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a>nx_sntp_client_utility_msecs_to_fraction

밀리초를 NTP 분율 구성 요소로 변환

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a>Description

이 서비스는 입력 밀리초를 NTP 분율 구성 요소로 변환합니다. 이 서비스는 SNTP 클라이언트에 대한 시작 기반 시간이 있지만 NTP 초/분율 형식은 아닌 애플리케이션에서 사용하기 위한 것입니다. 유효한 분율을 만들려면 밀리초 수가 1,000 미만이어야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **milliseconds** 변환할 밀리초 수입니다.

- **fraction** 분율로 변환된 밀리초에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 변환에 성공했습니다.

- **NX_SNTP_OVERFLOW_ERROR**(0x32) 시간을 날짜로 변환하는 동안 오류가 발생했습니다.

- NX_SNTP_INVALID_TIME(0xD30) 잘못된 SNTP 데이터 입력입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a>nx_sntp_client_utility_usecs_to_fraction

마이크로초를 NTP 분율 구성 요소로 변환

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a>Description

이 서비스는 입력 마이크로초를 NTP 분율 구성 요소로 변환합니다. 이 서비스는 SNTP 클라이언트에 대한 시작 기반 시간이 있지만 NTP 초/분율 형식은 아닌 애플리케이션에서 사용하기 위한 것입니다. 유효한 분율을 만들려면 마이크로초 수가 1,000,000 미만이어야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **microseconds** 변환할 마이크로초입니다.

- **fraction** 분율로 변환된 마이크로초에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 변환에 성공했습니다.

- **NX_SNTP_OVERFLOW_ERROR**(0x32) 시간을 날짜로 변환하는 동안 오류가 발생했습니다.

- NX_SNTP_INVALID_TIME(0xD30) 잘못된 SNTP 데이터 입력입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a>nx_sntp_client_utility_fraction_to_usecs

NTP 분율 구성 요소를 마이크로초로 변환

### <a name="prototype"></a>프로토타입

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a>Description

이 서비스는 입력 NTP 분율 구성 요소를 마이크로초로 변환합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **fraction** 변환할 분율입니다.

- **microseconds** 마이크로초로 변환된 분율에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 변환에 성공했습니다.

- NX_SNTP_INVALID_TIME(0xD30) 잘못된 SNTP 데이터 입력입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```