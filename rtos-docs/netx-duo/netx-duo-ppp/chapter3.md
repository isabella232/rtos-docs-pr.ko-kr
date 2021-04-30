---
title: 챕터 3 - Azure RTOS NetX Duo PPP(지점 간 프로토콜) 서비스 설명
description: 이 챕터에서는 모든 Azure RTOS NetX Duo PPP 서비스(아래 참조)를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 90c24cad5e595087ba27178243f9dda0dab11029
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810639"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-point-to-point-protocol-ppp-services"></a>챕터 3 - Azure RTOS NetX Duo PPP(지점 간 프로토콜) 서비스 설명

이 챕터에서는 모든 Azure RTOS NetX Duo PPP 서비스(아래 참조)를 알파벳 순서로 설명합니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- **nx_ppp_byte_receive**: *직렬 ISR에서 바이트 수신*
- **nx_ppp_chap_challenge**: *CHAP 챌린지 생성*
- **nx_ppp_chap_enable**: *CHAP 인증 사용*
- **nx_ppp_create**: *PPP 인스턴스 만들기*
- **nx_ppp_delete**: *PPP 인스턴스 삭제*
- **nx_ppp_dns_address_get**: *DNS 서버 IP 주소 가져오기*
- **nx_ppp_dns_address_set**: *DNS 서버 IP 주소 설정*
- **nx_ppp_secondary_dns_address_get**: *보조 DNS 서버 IP 주소 가져오기*
- **nx_ppp_secondary_dns_address_set**: *보조 DNS 서버 IP 주소 설정*
- **nx_ppp_interface_index_get**: *IP 인터페이스 인덱스 가져오기*
- **nx_ppp_ip_address_assign**: *IPCP에 대한 IP 주소 할당*
- **nx_ppp_link_down_notify**: *연결 해제 시 애플리케이션에 알림*
- **nx_ppp_link_up_notify**: *연결 사용 시 애플리케이션에 알림*
- **nx_ppp_nak_authentication_notify**: *인증 NAK가 수신되면 애플리케이션에 알림*
- **nx_ppp_pap_enable**: *PAP 인증 사용*
- **nx_ppp_ping_request**: *LCP 에코 요청 보내기*
- **nx_ppp_raw_string_send**: *비 PPP 문자열 보내기*
- **nx_ppp_restart**: *PPP 처리 다시 시작*
- **nx_ppp_start**: *PPP 처리 시작*
- **nx_ppp_status_get**: *현재 PPP 상태 가져오기*
- **nx_ppp_stop**: *PPP 처리 중지*
- **nx_ppp_packet_receive**: *PPP 패킷 수신*
- **nx_ppp_packet_send_set**: *PPP 패킷 전송 함수 설정*

## <a name="nx_ppp_byte_receive"></a>nx_ppp_byte_receive

직렬 ISR에서 바이트 수신

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a>설명

이 서비스는 일반적으로 수신 바이트를 PPP로 전송하기 위해 애플리케이션의 직렬 드라이버 ISR(인터럽트 서비스 루틴)에서 호출됩니다. 이 루틴은 호출되면 수신 바이트를 순환 바이트 버퍼에 배치하고 처리를 위해 적절한 PPP 스레드에 알립니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **byte**: 직렬 디바이스에서 받은 바이트입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP 바이트를 성공적으로 수신했습니다.
- **NX_PPP_BUFFER_FULL**: (0xB1) PPP 직렬 버퍼가 이미 가득 찼습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

스레드, ISR

### <a name="example"></a>예제

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a>nx_ppp_chap_challenge

CHAP 챌린지 생성

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a>설명

이 서비스는 PPP 연결이 이미 설정되고 실행된 후 CHAP 챌린지를 시작합니다. 이렇게 하면 애플리케이션이 정기적으로 연결의 신뢰성을 확인할 수 있습니다. 챌린지에 실패하면 PPP 링크가 닫힙니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP 챌린지를 성공적으로 시작했습니다.
- **NX_PPP_FAILURE**: (0xB0) 잘못된 PPP 챌린지입니다. CHAP가 응답에만 사용하도록 설정되었습니다.
- **NX_NOT_IMPLEMENTED**: (0x80) CHAP 논리가 NX_PPP_DISABLE_CHAP를 통해 사용하지 않도록 설정되었습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

스레드

### <a name="example"></a>예제

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a>nx_ppp_chap_enable

CHAP 인증 사용

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a>설명

이 서비스는 지정된 PPP 인스턴스에 대해 CHAP(Challenge-Handshake 인증 프로토콜)를 사용하도록 설정합니다.

“***get_challenge_values** _” 및 “_ *_get_verification_values_**” 함수 포인터를 지정하는 경우 이 PPP 인스턴스에 CHAP가 필요합니다. 그렇지 않으면 CHAP는 피어의 챌린지 요청에만 응답합니다.

필수 콜백 함수에서 다음과 같은 몇 가지 데이터 항목을 참조합니다. 데이터 항목 *secret*, *name* 및 *system* 은 최대 크기가 NX_PPP_NAME_SIZE-1인 NULL로 종료되는 문자열이어야 합니다. 데이터 항목 *rand_value* 는 최대 크기가 NX_PPP_VALUE_SIZE-1인 NULL로 종료되는 문자열이어야 합니다. 데이터 항목 *id* 는 단순 부호 없는 문자 형식입니다.

>[!NOTE]
> 이 함수는 *nx_ppp_create* 이후, nx_ip_create 또는 *nx_ip_interface_attach* 이전에 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **get_challenge_values**: 챌린지에 사용되는 값을 검색하는 애플리케이션 함수에 대한 포인터입니다. *rand_value*, *id* 및 *secret* 값을 제공된 대상에 복사해야 합니다.
- **get_responder_values**: 챌린지에 응답하는 데 사용되는 값을 검색하는 애플리케이션 함수에 대한 포인터입니다. *system*, *name* 및 *secret* 값을 제공된 대상에 복사해야 합니다.
- **get_verification_values**: 챌린지 응답을 확인하는 데 사용된 값을 검색하는 애플리케이션 함수에 대한 포인터입니다. *system*, *name* 및 *secret* 값을 제공된 대상에 복사해야 합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP CHAP를 성공적으로 사용하도록 설정했습니다.
- **NX_NOT_IMPLEMENTED**: (0x80) CHAP 논리가 NX_PPP_DISABLE_CHAP를 통해 사용하지 않도록 설정되었습니다.
- NX_PTR_ERROR: (0x07) PPP 포인터나 콜백 함수 포인터가 잘못되었습니다. *get_challenge_values* 가 지정된 경우 *get_verification_values* 함수도 제공해야 합니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a>nx_ppp_create

PPP 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a>설명

이 서비스는 지정된 NetX IP 인스턴스에 대한 PPP 인스턴스를 만듭니다. NetX IP 인스턴스를 만들기 전에 이 함수를 호출해야 합니다.

>[!NOTE]
> 일반적으로는 PPP 스레드 우선 순위보다 우선 순위가 높은 NetX IP 스레드를 만드는 것이 좋습니다. IP 스레드 우선 순위를 지정하는 방법에 대한 자세한 내용은 *nx_ip_create* 서비스를 참조하세요.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **name**: 이 PPP 인스턴스의 이름입니다.
- **ip_ptr**: 아직 생성되지 않은 IP 인스턴스의 제어 블록에 대한 포인터입니다.
- **stack_memory_ptr**: PPP 스레드의 스택 영역 시작에 대한 포인터입니다.
- **stack_size** 스레드 스택의 크기(바이트)입니다.
- **pool_ptr** 기본 패킷 풀에 대한 포인터입니다.
- **thread_priority**: 내부 PPP 스레드의 우선 순위(1-31)입니다.
- **ppp_invalid_packet_handler**: 모든 비 PPP 패킷에 대한 애플리케이션 처리기에 대한 함수 포인터입니다. NetX PPP는 일반적으로 초기화하는 동안 이 루틴을 호출합니다. 애플리케이션이 모뎀 명령에 응답하거나 Windows XP의 경우 NetX PPP 애플리케이션이 Windows XP에서 전송하는 초기 "클라이언트"에 "클라이언트 서버"로 응답하여 PPP를 시작할 수 있는 위치입니다.
- **ppp_byte_send**: 애플리케이션의 직렬 바이트 출력 루틴에 대한 함수 포인터입니다.


### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP를 성공적으로 만들었습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP, IP 또는 바이트 출력 함수 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a>nx_ppp_delete

PPP 인스턴스 삭제

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a>설명

이 서비스는 이전에 만든 PPP 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP를 성공적으로 삭제했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

스레드

### <a name="example"></a>예제

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a>nx_ppp_dns_address_get

DNS 서버 IP 주소 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>설명

이 서비스는 IPCP 핸드셰이크의 피어에서 제공한 DNS IP 주소를 검색합니다. 피어가 IP 주소를 제공하지 않은 경우 IP 주소 0이 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **dns_address_ptr**: DNS 서버 주소의 대상입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 주소를 성공적으로 가져왔습니다.
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어와 협상을 완료하지 못했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c

ULONG  my_dns_address;

/* Get DNS Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a>nx_ppp_secondary_dns_address_get

보조 DNS 서버 IP 주소 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>설명

이 서비스는 IPCP 핸드셰이크의 피어에서 제공한 보조 DNS IP 주소를 검색합니다. 피어가 IP 주소를 제공하지 않은 경우 IP 주소 0이 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **dns_address_ptr**: 보조 DNS 서버 주소의 대상입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 주소를 성공적으로 가져왔습니다.
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어와 협상을 완료하지 못했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a>nx_ppp_dns_address_set

주 DNS 서버 IP 주소 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>설명

이 서비스는 DNS 서버 IP 주소를 설정합니다. 피어가 IPCP 상태에서 DNS 서버 옵션 요청을 보내면 이 호스트가 정보를 제공합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **dns_address**: DNS 서버 주소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 주소를 성공적으로 설정했습니다.
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어와 협상을 완료하지 못했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a>nx_ppp_secondary_dns_address_set

보조 DNS 서버 IP 주소 설정

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>설명

이 서비스는 보조 DNS 서버 IP 주소를 설정합니다. 피어가 IPCP 상태에서 보조 DNS 서버 옵션 요청을 보내면 이 호스트가 정보를 제공합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **dns_address**: 보조 DNS 서버 주소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) DNS 주소를 성공적으로 설정했습니다. 
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP가 피어와 협상을 완료하지 못했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a>nx_ppp_interface_index_get

IP 인터페이스 인덱스 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a>설명

이 서비스는 이 PPP 인스턴스와 연결된 IP 인터페이스 인덱스를 검색합니다. 이는 PPP 인스턴스가 IP 인스턴스의 기본 인터페이스가 아닌 경우에만 유용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **index_ptr**: 인터페이스 인덱스의 대상입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP 인덱스를 성공적으로 가져왔습니다.
- **NX_IN_PROGRESS**: (0x37) PPP가 초기화를 완료하지 못했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a>nx_ppp_ip_address_assign

IPCP에 대한 IP 주소 할당

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a>설명

이 서비스는 IPCP(인터넷 프로토콜 제어 프로토콜)에서 사용할 로컬 및 피어 IP 주소를 설정합니다. 자체 및 다른 피어에 대한 유효한 IP 주소가 있는 PPP 인스턴스를 대상으로 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **local_ip_address** 로컬 IP 주소입니다.
- **peer_ip_address**: 피어의 IP 주소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP 주소를 성공적으로 할당했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a>nx_ppp_link_down_notify

연결 해제 시 애플리케이션에 알림

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a>설명

이 서비스는 지정된 PPP 인스턴스에 애플리케이션의 연결 해제 알림 콜백을 등록합니다. NULL이 아닌 경우 연결이 해제될 때마다 애플리케이션의 연결 해제 콜백 함수가 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **link_down_callback**: 애플리케이션의 연결 해제 알림 함수 포인터입니다. NULL인 경우 연결 해제 알림이 사용되지 않습니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 연결 해제 알림 콜백을 성공적으로 등록했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a>nx_ppp_link_up_notify

연결 사용 시 애플리케이션에 알림

### <a name="prototype"></a>프로토타입

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a>설명

이 서비스는 지정된 PPP 인스턴스에 애플리케이션의 연결 사용 알림 콜백을 등록합니다. NULL이 아닌 경우 연결이 사용될 때마다 애플리케이션의 연결 사용 콜백 함수가 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **link_up_callback**: 애플리케이션의 연결 사용 알림 함수 포인터입니다. NULL인 경우 연결 사용 알림이 사용되지 않습니다.**

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 연결 사용 알림 콜백을 성공적으로 등록했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a>nx_ppp_nak_authentication_notify

인증 NAK가 수신되면 애플리케이션에 알림

### <a name="prototype"></a>프로토타입

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a>설명

이 서비스는 지정된 PPP 인스턴스에 애플리케이션의 인증 nak 알림 콜백을 등록합니다. NULL이 아닌 경우 이 콜백 함수는 PPP 인스턴스가 인증 중에 NAK를 받을 때마다 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **nak_authentication_notify**: PPP 인스턴스가 인증 NAK를 받을 때 호출되는 함수에 대한 포인터입니다. NULL인 경우 알림이 사용되지 않습니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 알림 콜백을 성공적으로 등록했습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a>nx_ppp_pap_enable

PAP 인증 사용

### <a name="prototype"></a>프로토타입

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a>설명

이 서비스는 지정된 PPP 인스턴스에 PAP(암호 인증 프로토콜)를 사용하도록 설정합니다. "***verify_login***" 함수 포인터를 지정하는 경우 이 PPP 인스턴스에 PAP가 필요합니다. 그렇지 않으면 PAP는 LCP 협상 중에 지정된 피어의 PAP 요구 사항에만 응답합니다.

필수 콜백 함수에서 다음과 같은 몇 가지 데이터 항목을 참조합니다. 데이터 항목 *name* 은 최대 크기가 NX_PPP_NAME_SIZE-1인 NULL로 종료되는 문자열이어야 합니다. 데이터 항목 *password* 는 최대 크기가 NX_PPP_PASSWORD_SIZE-1인 NULL로 종료되는 문자열이어야 합니다.

>[!NOTE]
> 이 함수는 *nx_ppp_create* 이후, *nx_ip_create* 또는 *nx_ip_interface_attach* 이전에 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **generate_login**: 피어에서 인증을 위한 *name* 및 *password* 를 생성하는 애플리케이션 함수에 대한 포인터입니다. *name* 및 *password* 값을 제공된 대상에 복사해야 합니다.
- **verify_login**: 피어에서 제공한 *name* 및 *password* 를 확인하는 애플리케이션 함수에 대한 포인터입니다. 이 루틴은 제공된 *name* 및 *password* 를 비교해야 합니다. 이 루틴이 NX_SUCCESS를 반환하는 경우 name 및 password가 올바른 것이며, PPP가 다음 단계로 진행할 수 있습니다. 그렇지 않으면 이 루틴은 NX_PPP_ERROR를 반환하고 PPP는 다른 이름과 암호를 기다리기만 합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP PAP를 성공적으로 사용하도록 설정했습니다.
- **NX_NOT_IMPLEMENTED**: (0x80) PAP 논리가 NX_PPP_DISABLE_PAP를 통해 사용하지 않도록 설정되었습니다.
- NX_PTR_ERROR: (0x07) PPP 포인터나 애플리케이션 함수 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a>nx_ppp_ping_request

LCP ping 요청 보내기

### <a name="prototype"></a>프로토타입

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a>설명

이 서비스는 LCP 요청을 보내고 PPP 디바이스가 에코 응답을 기다리고 있다는 플래그를 설정합니다. 대기 옵션은 주로 *nx_packet_allocate* 호출과 관련이 있습니다. 이 서비스는 요청이 전송되는 즉시 반환됩니다. 응답을 기다리지 않습니다. 

일치하는 에코 응답이 수신되면 PPP 스레드 태스크가 플래그를 지웁니다. PPP 디바이스는 PPP 협상의 LCP 부분을 완료해야 합니다.

이 서비스는 링크 상태에 대한 하드웨어 폴링을 쉽게 수행할 수 없는 PPP 설정에 유용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **data**: 에코 요청에서 보낼 데이터에 대한 포인터입니다.
- **data_size**: LCP 에코 메시지를 보내기 위해 대기하는 wait_option 시간을 보낼 데이터의 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) 에코 요청을 성공적으로 보냈습니다.
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP 연결이 설정되지 않았습니다.
- NX_PTR_ERROR: (0x07) PPP 포인터나 애플리케이션 함수 포인터가 잘못되었습니다.
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

애플리케이션 스레드

### <a name="example"></a>예제

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  sizeof("username ") - 1;

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a>nx_ppp_raw_string_send

원시 ASCII 문자열 보내기

### <a name="prototype"></a>프로토타입

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a>설명

이 서비스는 PPP 인터페이스가 아닌 비 PPP ASCII 문자열을 직접 보냅니다. 이는 일반적으로 PPP가 모뎀 제어 정보를 포함하는 비 PPP 패킷을 수신한 후에 사용됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **string_ptr**: 보낼 문자열에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP 원시 문자열을 성공적으로 보냈습니다.
- NX_PTR_ERROR: (0x07) PPP 포인터나 문자열 포인터가 잘못되었습니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

스레드

### <a name="example"></a>예제

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a>nx_ppp_restart

PPP 처리 다시 시작

### <a name="prototype"></a>프로토타입

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a>설명

이 서비스는 PPP 처리를 다시 시작합니다. 일반적으로 연결 해제 콜백 또는 통신이 끊겼음을 알리는 비 PPP 모뎀 메시지로 인해 연결을 다시 설정해야 하는 경우에 호출됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP 다시 시작이 성공적으로 시작되었습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

스레드

### <a name="example"></a>예제

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a>nx_ppp_start

PPP 처리 시작

### <a name="prototype"></a>프로토타입

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a>설명

이 서비스는 PPP 처리를 시작합니다. 일반적으로 nx_ppp_stop()을 호출한 후에 호출됩니다.

>[!NOTE]
> 연결이 설정되면 PPP가 자동으로 PPP 처리를 시작합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP 시작이 성공적으로 시작되었습니다. 
- **NX_PPP_ALREADY_STARTED**: (0xb9) PPP가 이미 시작되었습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.
- NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

스레드

### <a name="example"></a>예제

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a>nx_ppp_status_get

현재 PPP 상태 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a>설명

이 서비스는 지정된 PPP 인스턴스의 현재 상태를 가져옵니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **status_ptr**: PPP 상태의 대상입니다. 가능한 상태 값은 다음과 같습니다.
    - **NX_PPP_STATUS_ESTABLISHED**
    - **NX_PPP_STATUS_LCP_IN_PROGRESS**
    - **NX_PPP_STATUS_LCP_FAILED**
    - **NX_PPP_STATUS_PAP_IN_PROGRESS**
    - **NX_PPP_STATUS_PAP_FAILED**
    - **NX_PPP_STATUS_CHAP_IN_PROGRESS**
    - **NX_PPP_STATUS_CHAP_FAILED**
    - **NX_PPP_STATUS_IPCP_IN_PROGRESS**
    - **NX_PPP_STATUS_IPCP_FAILED**

>[!NOTE]
> 이 상태는 API가 NX_SUCCESS를 반환하는 경우에만 유효합니다. 또한 *_FAILED 상태 값이 반환되는 경우 애플리케이션에서 다시 시작할 때까지 PPP 처리가 사실상 중지됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP 상태가 성공적으로 요청되었습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a>nx_ppp_stop

PPP 처리 중지

### <a name="prototype"></a>프로토타입

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a>설명

이 서비스는 PPP 처리를 중지합니다. 또한 사용자는 필요에 따라 nx_ppp_start()를 호출하여 PPP 처리를 시작할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP 시작이 성공적으로 시작되었습니다. 
- **NX_PPP_ALREADY_STOPPED**: (0xb8) PPP가 이미 중지되었습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.
- NX_CALLER_ERROR (0x11) 이 서비스의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용된 원본

스레드

### <a name="example"></a>예제

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a>nx_ppp_packet_receive

PPP 패킷 수신

### <a name="prototype"></a>프로토타입

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a>설명

이 서비스는 PPP 패킷을 수신합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **packet_ptr**: PPP 패킷에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP 상태가 성공적으로 요청되었습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a>nx_ppp_packet_send_set

PPP 패킷 전송 함수 설정

### <a name="prototype"></a>프로토타입

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a>설명

이 서비스는 PPP 패킷 전송 기능을 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **ppp_ptr**: PPP 제어 블록에 대한 포인터입니다.
- **nx_ppp_packet_send**: PPP 패킷을 전송하는 루틴입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: (0x00) PPP 상태가 성공적으로 요청되었습니다.
- NX_PTR_ERROR: (0x07) 잘못된 PPP 포인터입니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```