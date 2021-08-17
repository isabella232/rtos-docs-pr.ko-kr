---
title: 3장 - Azure RTOS NetX Duo TFTP 서비스 설명
description: 이 장에서는 알파벳 순서로 아래 나열된 모든 NetX Duo TFTP 서비스에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db7b7469bda02597db6428ecbf080b37a095413411eef2abefb1c4804d7bb1d3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799066"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a>3장 - Azure RTOS NetX Duo TFTP 서비스 설명

이 장에서는 알파벳 순서로 아래 나열된 모든 NetX Duo TFTP 서비스에 대해 설명합니다. 특별히 지정되지 않은 한 모든 서비스에서 IPv6 및 IPv4 통신이 지원됩니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- **nxd_tftp_client_file_open**: *TFTP 클라이언트 파일을 엽니다.*

- **nxd_tftp_client_create**: *TFTP 클라이언트 인스턴스를 만듭니다.*

- **nxd_tftp_client_delete**: *TFTP 클라이언트 인스턴스를 삭제합니다.*

- **nxd_tftp_client_error_info_get**: *클라이언트 오류 정보를 가져옵니다.*

- **nxd_tftp_client_file_close**: *클라이언트 파일을 닫습니다.*

- **nxd_tftp_client_file_open**: *클라이언트 파일을 엽니다.*

- **nxd_tftp_client_file_read**: *클라이언트 파일에서 블록을 읽습니다.*

- **nxd_tftp_client_file_write**: *클라이언트 파일에 블록을 씁니다.*

- **nxd_tftp_client_packet_allocate**: *클라이언트 파일 쓰기에 대해 패킷을 할당합니다.*

- **nxd_tftp_client_set_interface**: *TFTP 요청에 대해 실제 인터페이스를 설정합니다.*

- **nxd_tftp_server_create**: *TFTP 서버를 만듭니다.*

- **nxd_tftp_server_delete**: *TFTP 서버를 삭제합니다.*

- **nxd_tftp_server_start**: *TFTP 서버를 시작합니다.*

- **nxd_tftp_server_stop**: *TFTP 서버를 중지합니다.*

> [!NOTE] 
> 위에 나열된 모든 서비스의 IPv4 해당 항목은 NetX Duo TFTP 클라이언트 및 서버(예: *nx_tftp_server_create* 및 *nx_tftp_client_file_open*)에서 사용할 수 있습니다. 다음 페이지에는 ‘Duo’ API 설명(예: *nxd_* 로 시작하는 서비스)만 제공되어 있습니다. NXD_ADDRESS \* 입력이 지정된 경우 IPv4 해당 API가 ULONG 입력을 호출합니다. 그렇지 않으면 API 사용에 차이가 없습니다.

## <a name="nxd_tftp_client_create"></a>nxd_tftp_client_create

TFTP 클라이언트 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 IP 인스턴스에 대해 TFTP 클라이언트 인스턴스를 만듭니다.

> [!IMPORTANT]
> 애플리케이션은 제공된 IP 및 패킷 풀이 이미 생성되어 있는지 확인해야 합니다. 또한 이 서비스를 호출하기 전 IP 인스턴스에 대해 UDP를 사용하도록 설정해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_client_ptr** TFTP 클라이언트 제어 블록에 대한 포인터입니다.

- **tftp_client_name** 이 TFTP 클라이언트 인스턴스의 이름입니다.

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

- **pool_ptr** 패킷 풀 TFTP 클라이언트 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) TFTP를 성공적으로 만들었습니다.

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) IP 버전이 잘못되었거나 지원되지 않습니다.

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 잘못된 서버 IP 주소가 수신되었습니다.

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) 서버 ACK가 수신되지 않았습니다.

- NX_PTR_ERROR (0x16) 잘못된 IP, 풀 또는 TFTP 포인터입니다.

- NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화 및 스레드

### <a name="example"></a>예제

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a>nxd_tftp_client_delete

TFTP 클라이언트 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 TFTP 클라이언트 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_client_ptr** 이전에 만든 TFTP 클라이언트 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) TFTP 클라이언트를 성공적으로 삭제했습니다.

- NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a>nxd_tftp_client_error_info_get

클라이언트 오류 정보 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a>Description

이 서비스는 수신된 마지막 오류 코드를 반환하고 포인터를 클라이언트의 내부 오류 문자열로 설정합니다. 오류 조건에서 사용자는 서버에서 마지막으로 보낸 오류를 확인할 수 있습니다. null 오류 문자열은 오류가 없음을 나타냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_client_ptr** 이전에 만든 TFTP 클라이언트 인스턴스에 대한 포인터입니다.

- **error_code** 오류 코드의 대상 영역에 대한 포인터입니다.

- **error_string** 오류 문자열의 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) TFTP 오류 정보를 성공적으로 가져왔습니다.  

- NX_PTR_ERROR (0x16) 잘못된 TFTP 클라이언트 포인터입니다.

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a>nxd_tftp_client_file_close

클라이언트 파일 닫기

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a>Description

이 서비스는 TFTP 클라이언트 인스턴스가 이전에 연 파일을 닫습니다. TFTP 클라이언트 인스턴스는 파일을 한 번에 하나만 열 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_client_ptr** 이전에 만든 TFTP 클라이언트 인스턴스에 대한 포인터입니다.

- **ip_type** 사용할 IP 주소를 나타냅니다. 유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) TFTP 파일을 성공적으로 닫았습니다.

- NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.

- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

- NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a>nx_tftp_client_file_open

TFTP 클라이언트 파일 열기

### <a name="prototype"></a>프로토타입

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 주소로 TFTP 서버에서 지정된 파일을 열려고 시도합니다. 파일은 읽기 또는 쓰기용으로 열립니다. 

> [!NOTE] 
> 이것은 IPv4 패킷으로만 제한되며 NetX TFTP 애플리케이션을 지원하기 위해 사용됩니다. 개발자가 동등한 “duo” 서비스 *nxd_tftp_client_file_open* 을 사용하도록 애플리케이션을 이식하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_client_ptr** TFTP 제어 블록에 대한 포인터입니다.

- **file_name** NULL로 종료되었고 적합한 경로 정보를 포함하는 ASCII 파일 이름입니다.

- **server_ip_address** 서버 TFTP 주소입니다.

- **open_type** 열기 요청의 유형 중 하나입니다.

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** 서비스에서 TFTP 클라이언트 파일 열기를 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.

  **시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF) 
  
  TX_WAIT_FOREVER를 선택하면 TFTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다. 
  
  숫자 값(1-0xFFFFFFFE)을 선택하면 TFTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

- **ip_type** 사용할 IP 주소를 나타냅니다. 유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 클라이언트 파일을 성공적으로 열었습니다.

- **NX_TFTP_NOT_CLOSED** (0xC3) 클라이언트가 파일을 이미 열었습니다.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 잘못된 서버 주소가 수신되었습니다.

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) 서버에서 ACK가 수신되지 않았습니다.

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 잘못된 서버 IP가 수신되었습니다.

- **NX_TFTP_CODE_ERROR** (0x05) 오류 코드가 수신되었습니다.

- NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.

- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

- NX_IP_ADDRESS_ERROR (0x21) 잘못된 서버 IP 주소입니다.

- NX_OPTION_ERROR (0x0A) 잘못된 개방형 형식입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a>nxd_tftp_client_file_open

TFTP 클라이언트 파일 열기

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Description

이 서비스는 지정된 IPv6 주소로 TFTP 서버에서 지정된 파일을 열려고 시도합니다. 파일은 읽기 또는 쓰기용으로 열립니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_client_ptr** TFTP 제어 블록에 대한 포인터입니다.

- **file_name** NULL로 종료되었고 적합한 경로 정보를 포함하는 ASCII 파일 이름입니다.

- **server_ip_address** 서버 TFTP 주소입니다.

- **open_type** 열기 요청의 유형 중 하나입니다.

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** 서비스에서 TFTP 클라이언트 파일 열기를 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.

  **시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  TX_WAIT_FOREVER를 선택하면 TFTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중단됩니다.

  숫자 값(1-0xFFFFFFFE)을 선택하면 TFTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

- **ip_type** 사용할 IP 주소를 나타냅니다. 유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 클라이언트 파일을 성공적으로 열었습니다.

- **NX_TFTP_NOT_CLOSED** (0xC3) 클라이언트가 파일을 이미 열었습니다.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 잘못된 서버 주소가 수신되었습니다.

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) 서버에서 ACK가 수신되지 않았습니다.

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) 잘못된 IP 버전입니다.

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 잘못된 서버 IP가 수신되었습니다.

- **NX_TFTP_CODE_ERROR** (0x05) 오류 코드가 수신되었습니다.

- NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.

- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

- NX_IP_ADDRESS_ERROR (0x21) 잘못된 서버 IP 주소입니다.

- NX_OPTION_ERROR (0x0A) 잘못된 개방형 형식입니다.

- NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a>nxd_tftp_client_file_read

클라이언트 파일에서 블록 읽기

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Description

이 서비스는 이전에 연 TFTP 클라이언트 파일에서 512바이트 블록을 읽습니다. 512바이트 미만의 블록은 파일 끝을 신호로 보냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_client_ptr** TFTP 클라이언트 제어 블록에 대한 포인터입니다.

- **packet_ptr** 파일에서 읽은 블록을 포함하는 패킷의 대상입니다.

- **wait_option** 읽기가 완료될 때까지 서버가 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.

  **시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  TX_WAIT_FOREVER를 선택하면 TFTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중지됩니다.

  숫자 값(1-0xFFFFFFFE)을 선택하면 TFTP 서버가 파일 블록을 전송하도록 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

- **ip_type** 사용할 IP 주소를 나타냅니다. 유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 클라이언트 블록을 성공적으로 읽었습니다.

- **NX_TFTP_NOT_OPEN** (0xC3) 지정된 클라이언트 파일이 읽기용으로 열리지 않았습니다.

- **NX_NO_PACKET** (0x01) 서버에서 수신된 패킷이 없습니다.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 잘못된 서버 주소가 수신되었습니다.

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) 서버에서 ACK가 수신되지 않았습니다.

- **NX_TFTP_END_OF_FILE** (0xC5) 파일 끝이 검색되었습니다(오류 아님).

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) 잘못된 IP 버전입니다.

- **NX_TFTP_CODE_ERROR** (0x05) 오류 코드가 수신되었습니다.

- **NX_TFTP_FAILED** (0xC2) 알 수 없는 TFTP 코드가 수신되었습니다.

- **NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) 잘못된 블록 번호가 수신되었습니다.

- NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.

- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

- NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a>nxd_tftp_client_file_write

클라이언트 파일에 블록 쓰기

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Description

이 서비스는 이전에 열린 TFTP 클라이언트 파일에 512바이트 블록을 씁니다. 512바이트 미만의 블록을 지정하면 파일 끝을 신호로 보냅니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_client_ptr** TFTP 클라이언트 제어 블록에 대한 포인터입니다.

- **packet_ptr** 파일에 쓸 블록이 포함된 패킷입니다.

- **wait_option** 쓰기가 완료될 때까지 서버가 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.

  **시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  TX_WAIT_FOREVER를 선택하면 TFTP 서버가 요청에 응답할 때까지 호출 스레드가 무기한 일시 중지됩니다.
 
  숫자 값(1-0xFFFFFFFE)을 선택하면 TFTP 서버가 쓰기 요청에 대해 ACK를 전송하도록 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

- **ip_type** 사용할 IP 주소를 나타냅니다. 유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 클라이언트 블록을 성공적으로 썼습니다.

- **NX_TFTP_NOT_OPEN** (0xC3) 지정된 클라이언트 파일이 쓰기용으로 열리지 않았습니다.

- **NX_TFTP_TIMEOUT** (0xC1) 서버 ACK를 기다리는 동안 시간이 초과되었습니다.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 잘못된 서버 주소가 수신되었습니다.

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) 서버에서 ACK가 수신되지 않았습니다.

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) 잘못된 IP 버전입니다.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 잘못된 서버 주소가 수신되었습니다.

- **NX_TFTP_CODE_ERROR** (0x05) 오류 코드가 수신되었습니다.

- NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.

- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

- NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a>nxd_tftp_client_packet_allocate

클라이언트 파일 쓰기에 패킷 할당

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Description

이 서비스는 지정된 패킷 풀에서 UDP 패킷을 할당하고 패킷이 호출자에게 반환되기 전 4바이트 TFTP 헤더의 공간을 만듭니다. 그런 다음, 호출자가 클라이언트 파일에 쓰기를 위한 버퍼를 빌드할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pool_ptr** 패킷 풀에 대한 포인터입니다.

- **packet_ptr** 할당된 패킷에 대한 포인터의 대상입니다.

- **wait_option** 패킷 할당이 완료될 때까지 서버가 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.

  **시간 제한 값** (0x00000001 ~ 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  TX_WAIT_FOREVER를 선택하면 할당이 완료될 때까지 호출 스레드가 무기한 일시 중단됩니다.

  숫자 값(1-0xFFFFFFFE)을 선택하면 패킷 할당을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

- **ip_type** 사용할 IP 주소를 나타냅니다. 유효한 옵션은 IPv4(4) 또는 IPv6(6)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 패킷을 성공적으로 할당했습니다.

- NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.

- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

- NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a>nxd_tftp_client_set_interface

TFTP 요청에 대한 실제 인터페이스 설정

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a>Description

이 서비스는 입력 인터페이스 인덱스를 사용하여 TFTP 클라이언트가 TFTP 패킷을 보내고 받을 실제 인터페이스를 설정합니다. 기본 인터페이스에 대한 기본값은 0입니다.

> [!NOTE]
> 이 서비스를 사용하려면 NetX Duo가 멀티홈 주소 지정(v5.6 이상)을 지원해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_client_ptr** TFTP 클라이언트 인스턴스에 대한 포인터입니다.

- **if_index** 사용할 실제 인터페이스의 인덱스입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 인터페이스를 성공적으로 설정했습니다. (0x0B) 잘못된 인터페이스 입력입니다.

- NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.

- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

- NX_TFTP_INVALID_INTERFACE (0x0B) 잘못된 인터페이스 입력입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a>nxd_tftp_server_create

TFTP 서버 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Description

이 서비스는 포트 69로 TFTP 클라이언트 요청에 응답하는 TFTP 서버를 만듭니다. *nxd_tftp_server_start* 에 대한 후속 호출로 서버를 시작해야 합니다.

> [!IMPORTANT]
> 애플리케이션에서 제공된 IP 인스턴스, 패킷 풀 및 FileX 미디어 인스턴스가 이미 생성되었는지 확인해야 합니다. 또한 이 서비스를 호출하기 전 IP 인스턴스에 대해 UDP를 사용하도록 설정해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_server_ptr** TFTP 서버 제어 블록에 대한 포인터입니다.

- **tftp_server_name** 이 TFTP 서버 인스턴스의 이름입니다.

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

- **media_ptr** FileX 미디어 인스턴스에 대한 포인터입니다.

- **stack_ptr** TFTP 서버 스택 영역에 대한 포인터입니다.

- **stack_size** TFTP 서버 스택의 바이트 수입니다.

- **pool_ptr** TFTP 패킷 풀에 대한 포인터입니다. 

> [!NOTE]
> 제공된 풀에는 최소 580바이트 크기의 패킷 페이로드가 있어야 합니다.<sup>1</sup>

<sup>1</sup> 패킷의 데이터 부분이 정확히 512바이트이지만 패킷 페이로드 크기는 최소 572바이트여야 합니다. 나머지 바이트는 UDP, IPv6 및 이더넷 헤더와 정렬을 위해 드라이버에 필요한 잠재적인 후행 바이트에 사용됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 서버를 성공적으로 만들었습니다.

- **NX_TFTP_POOL_ERROR** (0xC6) 패킷 풀의 패킷 크기가 560바이트 미만입니다.

- NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a>nxd_tftp_server_delete

TFTP 서버 삭제

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 TFTP 서버를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_server_ptr** TFTP 서버 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 서버를 성공적으로 삭제했습니다.

- NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.

- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a>nxd_tftp_server_start

TFTP 서버 시작

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 TFTP 서버를 시작합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_server_ptr** TFTP 서버 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력입니다.
 
### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a>nxd_tftp_server_stop

TFTP 서버 중지

### <a name="prototype"></a>프로토타입

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 TFTP 서버를 중지합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **tftp_server_ptr** TFTP 서버 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 서버를 성공적으로 중지했습니다.

- NX_PTR_ERROR (0x16) 포인터 입력이 잘못되었습니다.

- NX_CALLER_ERROR (0x11) 이 서비스의 잘못된 호출자

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```