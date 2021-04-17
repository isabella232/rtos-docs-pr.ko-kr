---
title: 3장 - Azure RTOS NetX AutoIP 서비스 설명
description: 이 장에는 모든 Azure RTOS NetX AutoIP 서비스(아래에 나열됨)에 대한 설명이 알파벳 순서로 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 22cc06c32cc9f1857b32d1d2b44a506ea1652cfd
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811664"
---
# <a name="chapter-3---description-of-azure-rtos-netx-autoip-services"></a>3장 - Azure RTOS NetX AutoIP 서비스 설명

이 장에는 모든 Azure RTOS NetX AutoIP 서비스(아래에 나열됨)에 대한 설명이 알파벳 순서로 포함되어 있습니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 비활성화하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만 굵게 표시되지 않은 값은 완전히 비활성화됩니다.

- **nx_auto_ip_create**: *AutoIP 인스턴스 만들기*
- **nx_auto_ip_delete**: *AutoIP 인스턴스 삭제*
- **nx_auto_ip_get_address**: *현재 AutoIP 주소 가져오기*
- **nx_auto_ip_set_interface**: *AutoIP 주소를 필요로 하는 IP 인터페이스 설정*
- **nx_auto_ip_start**: *AutoIP 처리 시작*
- **nx_auto_ip_stop**: *AutoIP 처리 중지*

## <a name="nx_auto_ip_create"></a>nx_auto_ip_create

AutoIP 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
            NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
            UINT priority);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에 AutoIP 인스턴스를 만듭니다.

- **auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.
- **name**: AutoIP 인스턴스의 이름입니다.
- **ip_ptr**: IP 인스턴스에 대한 포인터입니다.
- **stack_ptr**: AutoIP 스레드 스택 영역에 대한 포인터입니다.
- **stack_size**: AutoIP 스레드 스택 영역의 크기입니다.
- **priority**: AutoIP 스레드의 우선 순위입니다.

> [!NOTE]
> DHCP를 사용하는 경우 DHCP 스레드의 우선 순위는 IP 인스턴스 스레드와 AutoIP 스레드보다 높아야 합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적인 AutoIP 생성.
- **NX_AUTO_IP_ERROR**: (0xA00) AutoIP 생성 오류.
- NX_PTR_ERROR: (0x16) AutoIP, ip_ptr 또는 스택 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a>참고 항목

nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_delete"></a>nx_auto_ip_delete

AutoIP 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에서 이전에 만든 AutoIP 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적인 AutoIP 삭제.
- **NX_AUTO_IP_ERROR**: (0xA00) AutoIP 삭제 오류.
- NX_PTR_ERROR(0x16): AutoIP 포인터가 잘못되었습니다.
- NX_CALLER_ERROR(0x11): 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

스레드

### <a name="example"></a>예제

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a>참고 항목

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_get_address"></a>nx_auto_ip_get_address

현재 AutoIP 주소 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a>Description

이 서비스는 현재 설정된 AutoIP 주소를 검색합니다. IP 주소가 없는 경우 0.0.0.0이 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.
- **local_ip_address**: 반환 IP 주소의 대상입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적인 AutoIP 주소 가져오기.
- **NX_AUTO_IP_NO_LOCAL**: (0xA01) 올바른 AutoIP 주소가 없습니다.
- NX_PTR_ERROR: (0x16) AutoIP 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 타이머, 스레드, ISR

### <a name="example"></a>예제

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a>참고 항목

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_set_interface"></a>nx_auto_ip_set_interface

AutoIP용 네트워크 인터페이스 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Description

이 서비스는 네트워크 인터페이스 AutoIP가 네트워크 IP 주소를 검색할 인덱스를 설정합니다. 기본값은 0(기본 네트워크 인터페이스)입니다. 멀티홈 디바이스에만 적용됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.
- **interface_index**: IP 주소를 검색하기 위한 인터페이스

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적인 AutoIP 인터페이스 집합
- **NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) 잘못된 네트워크 인터페이스 
- NX_PTR_ERROR: (0x16) AutoIP 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 타이머, 스레드, ISR

### <a name="example"></a>예제

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block auto_ip_0. */
```

### <a name="see-also"></a>참고 항목

nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_start"></a>nx_auto_ip_start

AutoIP 처리 시작

### <a name="prototype"></a>프로토타입

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 AutoIP 인스턴스에서 AutoIP 프로토콜을 시작합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.
- **starting_local_address**: 선택적 AutoIP 시작 주소입니다. IP_ADDRESS(0,0,0,0) 값은 임의의 AutoIP 주소를 파생하도록 지정합니다. 그렇지 않고 유효한 AutoIP 주소가 지정된 경우 NetX AutoIP가 해당 주소를 할당하려고 합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적인 AutoIP 시작.
- **NX_AUTO_IP_ERROR**: (0xA00) AutoIP 시작 오류.
- NX_PTR_ERROR: (0x16) AutoIP 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a>참고 항목

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop

## <a name="nx_auto_ip_stop"></a>nx_auto_ip_stop

AutoIP 처리 중지

### <a name="prototype"></a>프로토타입

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 생성되고 시작된 AutoIP 인스턴스에서 AutoIP 프로토콜을 시작합니다. 이 서비스는 일반적으로 IP 주소가 DHCP를 통해 변경되거나 수동으로 비 AutoIP 주소로 변경될 때 사용됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 성공적인 AutoIP 중지.
- **NX_AUTO_IP_ERROR**: (0xA00) AutoIP 중지 오류.
- NX_PTR_ERROR: (0x16) AutoIP 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

스레드

### <a name="example"></a>예제

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a>참고 항목

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start