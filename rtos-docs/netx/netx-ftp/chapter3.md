---
title: 3장 - Azure RTOS NetX FTP 서비스 설명
description: 이 장에서는 아래에 나열된 모든 Azure RTOS NetX FTP 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1aec01088236dcae359c0273a0206c10ea09201eb486478ebd678529413badae
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799458"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a>3장 - Azure RTOS NetX FTP 서비스 설명

이 장에서는 아래에 나열된 모든 Azure RTOS NetX FTP 서비스에 대해 알파벳 순서로 설명하고 있습니다.

다음 API 설명의 “반환 값” 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- **nx_ftp_client_connect**: *FTP 서버에 연결*
- **nx_ftp_client_create**: *FTP 클라이언트 인스턴스 만들기*
- **nx_ftp_client_delete**: *FTP 클라이언트 인스턴스 삭제*
- **nx_ftp_client_directory_create**: *서버에서 디렉터리 만들기*
- **nx_ftp_client_directory_default_set**: *서버에서 기본 디렉터리 설정*
- **nx_ftp_client_directory_delete**: *서버에서 디렉터리 삭제*
- **nx_ftp_client_directory_listing_get**: *서버에서 디렉터리 목록 가져오기*
- **nx_ftp_client_directory_listing_continue**: *서버에서 디렉터리 나열 계속*
- **nx_ftp_client_disconnect**: *FTP 서버에서 연결 해제*
- **nx_ftp_client_file_close**: *클라이언트 파일 닫기*
- **nx_ftp_client_file_delete**: *서버에서 파일 삭제*
- **nx_ftp_client_file_open**: *클라이언트 파일 열기*
- **nx_ftp_client_file_read**: *파일에서 읽기*
- **nx_ftp_client_file_rename**: *서버에서 파일 이름 변경*
- **nx_ftp_client_file_write**: *파일에서 읽기*
- **nx_ftp_server_create**: *FTP 서버 만들기*
- **nx_ftp_server_delete**: *FTP 서버 삭제*
- **nx_ftp_server_start**: *FTP 서버 시작*
- **nx_ftp_server_stop**: *FTP 서버 중지*

## <a name="nx_ftp_client_connect"></a>nx_ftp_client_connect

FTP 서버에 연결

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 FTP 클라이언트 인스턴스를 제공된 IP 주소에서 FTP 서버에 연결합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **server_ip**: FTP 서버의 IP 주소입니다.
- **username**: 인증을 위한 클라이언트 사용자 이름입니다.
- **password**: 인증을 위한 클라이언트 암호입니다.
- **wait_option**: 서비스에서 FTP 클라이언트 연결을 대기하는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP를 성공적으로 연결했습니다.
- **NX_TFTP_EXPECTED_22X_CODE**: (0xDB) 22X(ok) 응답을 가져오지 못했습니다.
- **NX_FTP_EXPECTED_23X_CODE**: (0xDC) 23X(ok) 응답을 가져오지 못했습니다.
- **NX_FTP_EXPECTED_33X_CODE**: (0xDE) 33X(ok) 응답을 가져오지 못했습니다.
- **NX_FTP_NOT_DISCONNECTED**: (0xD4) 클라이언트가 이미 연결되어 있습니다.
- NX_PTR_ERROR: (0x07) 잘못된 포인터 입력/출력입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.
- NX_IP_ADDRESS_ERROR: (0x21) 잘못된 IP 주소입니다.

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a>nx_ftp_client_create

FTP 클라이언트 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Description

이 서비스는 FTP 클라이언트 인스턴스를 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **ftp_client_name**: FTP 클라이언트의 이름입니다.
- **ip_ptr**: 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **window_size**: 이 FTP 클라이언트의 TCP 소켓에 대해 보급된 창 크기입니다.
- **pool_ptr**: 이 FTP 클라이언트의 기본 패킷 풀에 대한 포인터입니다. 최소 패킷 페이로드는 전체 경로 및 파일 또는 디렉터리 이름을 저장할 수 있을 만큼 커야 합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 클라이언트를 성공적으로 만들었습니다.
- NX_PTR_ERROR: (0x16) 잘못된 FTP, IP 포인터 또는 패킷 풀 포인터입니다. 암호 포인터입니다.

### <a name="allowed-from"></a>허용되는 원본

초기화 및 스레드

### <a name="example"></a>예제

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a>nx_ftp_client_delete

FTP 클라이언트 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a>Description

이 서비스는 FTP 클라이언트 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 클라이언트를 성공적으로 삭제했습니다.
- **NX_FTP_NOT_DISCONNECTED**: (0xD4) FTP 클라이언트 삭제 오류입니다.
- NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a>nx_ftp_client_directory_create

FTP 서버에 디렉터리 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에 지정된 디렉터리를 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **directory_name**: 만들 디렉터리의 이름입니다.
- **wait_option**: 서비스에서 FTP 디렉터리 생성을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 디렉터리를 성공적으로 만들었습니다.
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다. 
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다. 
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a>nx_ftp_client_directory_default_set

FTP 서버에 기본 디렉터리 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에 지정된 디렉터리를 설정합니다. 이 기본 디렉터리는 이 클라이언트의 연결에만 적용됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **directory_path**: 설정할 디렉터리 경로의 이름입니다.
- **wait_option**: 서비스에서 FTP 기본 디렉터리 설정을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 기본 설정이 성공적으로 수행되었습니다.
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다. 
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다. 
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a>nx_ftp_client_directory_delete

FTP 서버에서 디렉터리 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에서 지정된 디렉터리를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **directory_name**: 삭제할 디렉터리의 이름입니다.
- **wait_option**: 서비스에서 FTP 디렉터리 삭제를 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 디렉터리를 성공적으로 삭제했습니다.
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다. 
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다. 
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a>nx_ftp_client_directory_listing_get

FTP 서버에서 디렉터리 목록 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에서 지정된 디렉터리의 콘텐츠를 가져옵니다. 제공된 패킷 포인터는 하나 이상의 디렉터리 항목을 포함합니다. 각 항목은 &lt;cr/lf\ 조합으로 구분됩니다. ***nx_ftp_client_directory_listing_continue***: 디렉터리 가져오기 작업을 완료하기 위해 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **directory_name**: 콘텐츠를 가져올 디렉터리의 이름입니다.
- **packet_ptr**: 대상 패킷 포인터에 대한 포인터입니다. 성공하는 경우 패킷 페이로드에 하나 이상의 디렉터리 항목이 포함됩니다.
- **wait_option**: 서비스에서 FTP 디렉터리 목록 나열을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 디렉터리를 성공적으로 나열했습니다.
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.
- **NX_NOT_ENABLED**: (0x14) 서비스(IPv6)를 사용할 수 없음
- **NX_FTP_EXPECTED_1XX_CODE**: (0xD9) 1XX(ok) 응답을 가져오지 못했습니다.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a>nx_ftp_client_directory_listing_continue

FTP 서버에서 디렉터리 나열 계속

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 FTP 클라이언트에 연결된 FTP 서버에서 지정된 디렉터리의 콘텐츠를 계속 가져옵니다. ***nx_ftp_client_directory_listing_get*** 에 대한 호출 바로 앞에 와야 합니다. 성공하는 경우 제공된 패킷 포인터는 하나 이상의 디렉터리 항목을 포함합니다. 이 루틴은 NX_FTP_END_OF_LISTING 상태가 수신될 때까지 호출되어야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **packet_ptr**: 대상 패킷 포인터에 대한 포인터입니다. 성공하는 경우 패킷 페이로드에 하나 이상의 디렉터리 항목이 &lt;cr/lf&gt;로 구분되어 포함됩니다.
- **wait_option**: 서비스에서 FTP 디렉터리 목록 나열을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 디렉터리를 성공적으로 나열했습니다.
- **NX_FTP_END_OF_LISTING**: (0xD8) 이 디렉터리에 항목이 더 이상 없습니다.
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a>nx_ftp_client_disconnect

FTP 서버에서 연결 끊기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 FTP 클라이언트와 이전에 설정된 FTP 서버의 연결을 끊습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **wait_option**: 서비스에서 FTP 클라이언트 연결 해제를 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 연결을 성공적으로 해제했습니다.
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a>nx_ftp_client_file_close

클라이언트 파일 닫기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 FTP 서버에서 이전에 열린 파일을 닫습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **wait_option**: 서비스에서 FTP 클라이언트 파일 닫기를 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 파일을 성공적으로 닫았습니다.
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.
- **NX_FTP_NOT_OPEN(0xD5)** : 파일이 열려 있지 않습니다. 닫을 수 없습니다.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a>nx_ftp_client_file_delete

FTP 서버에서 파일 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 FTP 서버에서 지정된 파일을 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **file_name**: 삭제할 파일의 이름입니다.
- **wait_option**: 서비스에서 FTP 클라이언트 파일 닫기를 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 파일을 성공적으로 삭제했습니다.
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a>nx_ftp_client_file_open

FTP 서버에서 파일 열기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 클라이언트 인스턴스에 이전에 연결된 FTP 서버에서 읽기 또는 쓰기를 위해 지정된 파일을 엽니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **file_name**: 열 파일의 이름입니다.
- **open_type**: **NX_FTP_OPEN_FOR_READ** 또는 **NX_FTP_OPEN_FOR_WRITE** 중 하나입니다.
- **wait_option**: 서비스에서 FTP 클라이언트 파일 열기를 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 파일을 성공적으로 열었습니다.
- **NX_OPTION_ERROR**: (0x0A) 개방형 형식이 잘못되었습니다.
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.
- **NX_FTP_NOT_CLOSED**: (0xD6) FTP 클라이언트가 이미 열려 있습니다.
- **NX_NO_FREE_PORTS**: (0x45) 할당할 수 있는 TCP 포트가 없습니다.
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a>nx_ftp_client_file_read

파일에서 읽기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 열린 파일에서 패킷을 읽습니다. NX_FTP_END_OF_FILE 상태가 수신될 때까지 반복적으로 호출되어야 합니다.

호출자는 이 서비스에 대한 패킷을 할당하지 않습니다.  패킷 포인터에 대한 포인터만 제공해야 합니다. 이 서비스는 소켓 수신 큐에서 검색된 패킷을 가리키도록 해당 패킷 포인터를 업데이트합니다.  성공 상태가 반환되면 사용 가능한 패킷이 있음을 의미하며, 호출자는 작업을 수행할 때 패킷을 해제해야 하는 책임이 있습니다.

0이 아닌 상태(오류 상태 또는 NX_FTP_END_OF_FILE)가 반환되면 호출자는 패킷을 해제하지 않습니다. 그렇지 않으면 패킷 포인터가 NULL인 경우 오류가 생성됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **packet_ptr**: 큐에서 검색된 데이터 패킷 포인터의 대상에 대한 포인터입니다. 성공하는 경우 패킷 데이터는 파일의 일부 또는 전부를 포함합니다.
- **wait_option**: 서비스에서 FTP 클라이언트 파일 읽기를 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 파일을 성공적으로 읽었습니다.
- **NX_FTP_NOT_OPEN**: (0xD5) FTP 클라이언트가 열려 있지 않습니다.
- **NX_FTP_END_OF_FILE**: (0xD7) 파일의 끝 조건입니다.
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

        /* Check status.  */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }
        else
        {
            /* Release packet when done with it. */
            nx_packet_release(my_packet);
        }

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a>nx_ftp_client_file_rename

FTP 서버에서 파일 이름 변경

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 FTP 서버에서 파일의 이름을 바꿉니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **filename**: 현재 파일 이름입니다.
- **new_filename**: 파일에 사용할 새 이름입니다.
- **wait_option**: 서비스에서 FTP 클라이언트 파일 이름 변경을 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 파일 이름을 성공적으로 변경했습니다.
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP 클라이언트가 연결되어 있지 않습니다.
- **NX_FTP_EXPECTED_3XX_CODE**: (0XDD) 3XX(ok) 응답을 받지 못했습니다.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX(ok) 응답을 가져오지 못했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a>nx_ftp_client_file_write

파일에 쓰기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 FTP 서버에서 이전에 열린 파일에 데이터 패킷을 씁니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **packet_ptr**: 쓸 데이터를 포함하는 패킷 포인터입니다.
- **wait_option**: 서비스에서 FTP 클라이언트 파일 쓰기를 기다리는 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **시간 제한 값**: (0x00000001 ~ 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER는 FTP 서버에서 요청에 응답할 때까지 호출 스레드가 무기한으로 일시 중단되도록 합니다. 숫자 값(1 ~ 0xFFFFFFFE)을 선택하면 FTP 서버 응답을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 파일을 성공적으로 썼습니다.
- **NX_FTP_NOT_OPEN**: (0xD5) FTP 클라이언트가 열려 있지 않습니다.
- NX_PTR_ERROR: (0x07) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a>nx_ftp_client_passive_mode_set

수동 전송 모드 사용 또는 사용 안 함

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a>Description

이 서비스를 이전에 만든 FTP 클라이언트 인스턴스에서 passive_mode_enabled 입력을 NX_TRUE로 설정하여, 이후 파일 읽기 또는 쓰기(RETR, STOR) 또는 디렉터리 목록 다운로드(NLST)에 대한 호출이 전송 모드에서 수행될 경우 수동 전송 모드를 활성화합니다. 수동 모드 전송을 사용하지 않도록 설정하고 활성 전송 모드의 기본 동작으로 돌아가려면 passive_mode_enabled 입력을 NX_FALSE로 설정하여 이 함수를 호출합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_client_ptr**: FTP 클라이언트 제어 블록에 대한 포인터입니다.
- **passive_mode_enabled**:
  - NX_TRUE로 설정된 경우 수동 모드를 사용합니다.
  - NX_FALSE로 설정된 경우 수동 모드를 사용하지 않습니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 수동 모드를 성공적으로 설정했습니다.
- NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.
- NX_INVALID_PARAMETERS: (0x4D) 잘못된 포인터 입력입니다.

### <a name="allowed-from"></a>허용되는 원본

스레드

### <a name="example"></a>예제

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a>nx_ftp_server_create

FTP 서버 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a>Description

이 서비스는 지정된 및 이전에 만든 NetX IP 인스턴스에 FTP 서버 인스턴스를 만듭니다. FTP 서버는 작업을 시작하기 위해 ***nx_ftp_server_start*** 를 호출하여 시작해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_server_ptr**: FTP 서버 제어 블록에 대한 포인터입니다.
- **ftp_server_name**: FTP 서버의 이름입니다.
- **ip_ptr**: 연결된 NetX IP 인스턴스에 대한 포인터입니다. IP 인스턴스에는 FTP 서버가 하나만 있을 수 있습니다.
- **media_ptr**: 연결된 FileX 미디어 인스턴스에 대한 포인터입니다.
- **stack_ptr**: 내부 FTP 서버 스레드의 스택 영역에 대한 메모리 포인터입니다.
- **stack_size**: *stack_ptr* 에 의해 지정된 스택 영역의 크기입니다.
- **pool_ptr**: 기본 NetX 패킷 풀에 대한 포인터입니다. 풀에 있는 패킷의 페이로드 크기는 최대 파일 이름/경로를 수용할 만큼 충분히 커야 합니다.
- **ftp_login**: 애플리케이션의 로그인 함수에 대한 함수 포인터입니다. 이 함수는 연결을 요청하는 클라이언트의 사용자 이름과 암호를 제공합니다. 유효한 경우 애플리케이션의 로그인 함수는 NX_SUCCESS를 반환해야 합니다.
- **ftp_logout**: 애플리케이션의 로그아웃 함수에 대한 함수 포인터입니다. 이 함수는 연결 해제를 요청하는 클라이언트의 사용자 이름과 암호를 제공합니다. 유효한 경우 애플리케이션의 로그인 함수는 NX_SUCCESS를 반환해야 합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 서버를 성공적으로 만들었습니다.
- NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.

### <a name="allowed-from"></a>허용되는 원본

초기화 및 스레드

### <a name="example"></a>예제

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a>nx_ftp_server_delete

FTP 서버 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 FTP 서버 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_server_ptr**: FTP 서버 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 서버를 성공적으로 삭제했습니다.
- NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a>nx_ftp_server_start

FTP 서버 시작

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 FTP 서버 인스턴스를 시작합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_server_ptr**: FTP 서버 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 서버를 성공적으로 시작했습니다.
- NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.

### <a name="allowed-from"></a>허용되는 원본

초기화 및 스레드

### <a name="example"></a>예제

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a>nx_ftp_server_stop

FTP 서버 중지

### <a name="prototype"></a>프로토타입

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만들어서 시작한 FTP 서버 인스턴스를 중지합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ftp_server_ptr**: FTP 서버 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) FTP 서버를 성공적으로 중지했습니다.
- NX_PTR_ERROR: (0x16) 잘못된 FTP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
