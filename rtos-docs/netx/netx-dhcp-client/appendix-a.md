---
title: 부록 A - 상태 복원 기능 설명
description: Azure RTOS NetX DHDP 클라이언트 구성 옵션인 NX_DHCP_CLIENT_RESTORE_STATE를 사용하면 시스템 재부팅 간에 바인딩된 상태에서 이전에 만든 DHCP 클라이언트 레코드를 복원할 수 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4b7286726eb6bfc666ba7a4b9983847da442fe212a45f4b28e184f70cf46e2b4
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801243"
---
# <a name="appendix-a---description-of-the-restore-state-feature"></a>부록 A - 상태 복원 기능 설명

Azure RTOS NetX DHDP 클라이언트 구성 옵션인 NX_DHCP_CLIENT_RESTORE_STATE를 사용하면 시스템 재부팅 간에 바인딩된 상태에서 이전에 만든 DHCP 클라이언트 레코드를 복원할 수 있습니다.

이 옵션을 사용하도록 설정하면 애플리케이션이 DHCP 클라이언트 스레드를 일시 중단하고 다시 시작할 수 있습니다. 또한 스레드를 일시 중단하고 다시 시작하는 시간 사이에 경과된 시간으로 DHCP 클라이언트를 업데이트하는 서비스도 있습니다.

## <a name="restoring-the-dhcp-client-between-reboots"></a>재부팅 간에 DHCP 클라이언트 복원

재부팅한 후 DHCP 클라이언트를 복원하기 전에 이전에 만든 DHCP 클라이언트는 바인딩된 상태에 도달해야 하며 DHCP 서버의 IP 주소가 할당되어야 합니다. 전원이 꺼질 때까지 DHCP 애플리케이션은 현재 DHCP 클라이언트 레코드를 비휘발성 메모리로 저장해야 합니다. 또한 시스템의 다른 곳에 독립적인 '시간 키퍼'가 있어야 이 전원이 꺼진 상태에서 경과된 시간을 추적할 수 있습니다. 전원을 켜면 애플리케이션은 새 DHCP 클라이언트 인스턴스를 만든 다음, 이전에 만든 DHCP 클라이언트 레코드를 사용하여 업데이트합니다. 경과된 시간은 "시간 키퍼"에서 가져온 다음, DHCP 클라이언트 임대의 남은 시간에 적용됩니다. 이로 인해 DHCP 클라이언트가 상태를 변경(예: BOUND에서 RENEWING으로)할 수 있습니다. 이 시점에서 애플리케이션은 DHCP 클라이언트를 다시 시작할 수 있습니다.

전원 끄기 중 경과된 시간이 DHCP 클라이언트 상태를 RENEW 또는 REBIND 상태 중 하나로 설정하면 DHCP 클라이언트는 IP 주소 임대를 갱신하거나 리바인딩하기 위한 DHCP 메시지 요청을 자동으로 시작합니다. IP 주소가 만료된 경우 DHCP 클라이언트는 자동으로 IP 인스턴스의 IP 주소를 지우고 새 IP 주소를 요청하여 INIT 상태에서 DHCP 프로세스를 시작합니다.

이러한 방식으로 DHCP 클라이언트는 중단 없이 재부팅 간에 작동할 수 있습니다.

이 기능에 대한 설명은 다음과 같습니다. 이때 DHCP 클라이언트는 기본 인터페이스에서만 실행되는 것으로 가정합니다.

```C
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define(). */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{


  /* No previously saved Client record. Start the DHCP Client in the INIT state. */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  do
  {
  
    /* Wait for DHCP to assign the IP address. */
  } while (status != NX_SUCCESS);

  /* We have a valid IP address. */

  /* At some point decide we power down the system. */

  /* Save the Client state data which we will subsequently need to restore the DHCP  
     Client. */
  status = nx_dhcp_client_get_record(&dhcp_0, &client_nv_record);         

  /* Copy this memory to non-volatile memory (not shown). */

  /* Delete the IP and DHCP Client instances before powering down. */
  nx_dhcp_delete(&dhcp_0);

  nx_ip_delete(&ip_0);

  /* Ready to power down, having released other resources as necessary. */

}
else
{

  /* The application has determined there is a previously saved record. We will 
     restore it to the current DHCP Client instance. */

  /* Get the previous Client state data from non-volatile memory. */

  /* Apply the record to the current Client instance. This will also 
     update the IP instance with IP address, mask etc. */
  status = nx_dhcp_client_restore_record(&dhcp_0, &client_nv_record, time_elapsed);   

     if (status != NX_SUCCESS)
      return;

     /* We are ready to resume the DHCP Client thread and use the assigned IP address. */
     status = nx_dhcp_resume(&dhcp_0);

     if (status != NX_SUCCESS)
      return;

}
```

## <a name="resuming-the-dhcp-client-thread-after-suspension"></a>일시 중단 후 DHCP 클라이언트 스레드 다시 시작 

전원 끄기 없이 DHCP 클라이언트 스레드를 일시 중단하기 위해 애플리케이션은 BOUND 상태를 달성하고 유효한 IP 주소를 가진 DHCP 클라이언트에서 *nx_dhcp_suspend* 를 호출합니다. DHCP 클라이언트를 다시 시작할 준비가 되면 먼저 *nx_dhcp_client_update_time_remaining* 을 호출하여 DHCP 주소 임대에서 남은 시간을 업데이트합니다(독립 시간 키퍼에서 경과된 시간 가져오기). 그런 다음, *nx_dhcp_resume* 을 호출하여 DHCP 클라이언트 스레드를 다시 시작합니다.

경과된 시간이 DHCP 클라이언트 상태를 RENEW 또는 REBIND 상태 중 하나로 설정하면 DHCP 클라이언트는 IP 주소 임대를 갱신하거나 리바인딩하기 위한 DHCP 메시지 요청을 자동으로 시작합니다. IP 주소가 만료된 경우 DHCP 클라이언트는 자동으로 IP 주소를 지우고 새 IP 주소를 요청하여 INIT 상태에서 DHCP 프로세스를 시작합니다.

이 기능 사용에 대한 설명은 다음과 같습니다.

```C
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define(). */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client. */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   
    /* Wait for DHCP to obtain an IP address. */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the 
     network... */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the
     elapsed time. */


  /* At some point, we are ready to resume the DHCP Client thread. */

  /* Update the DHCP Client lease time remaining with the time elapsed. */
  status = nx_dhcp_client_update_time_remaining(&dhcp_0, time_elapsed);   

  if (status != NX_SUCCESS)
       return;

  /* We now can resume the DHCP Client thread. */
  status = nx_dhcp_resume(&dhcp_0);

  if (status != NX_SUCCESS)
       return;

  /* Resume tasks e.g. ping another host. */
  status =  nx_icmp_ping(…);

}
```

다음은 DHCP 클라이언트 상태를 메모리에서 복원하고, DHCP 클라이언트를 일시 중단 및 다시 시작하기 위한 서비스 목록입니다.

## <a name="nx_dhcp_client_get_record"></a>nx_dhcp_client_get_record

현재 DHCP 클라이언트 상태에 대한 레코드 만들기

### <a name="prototype"></a>프로토타입

```C
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, 
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Description

이 서비스는 DHCP 클라이언트 인스턴스에서 DHCP를 사용하는 첫 번째 인터페이스에서 실행되는 DHCP 클라이언트를 record_ptr이 가리키는 레코드에 저장합니다. 이를 통해 DHCP 클라이언트 애플리케이션은 전원을 끄고 재부팅하는 등의 방법으로 DHCP 클라이언트 상태를 복원할 수 있습니다.

DHCP에 대해 둘 이상의 인터페이스를 사용하는 경우 특정 인터페이스에 DHCP 클라이언트 레코드를 저장하려면 *nx_dhcp_interface_client_get_record* 서비스를 사용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 클라이언트에 대한 포인터

- **record_ptr** DHCP 클라이언트 레코드에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS (0x0)** 클라이언트 레코드를 만듦

- **NX_DHCP_NOT_BOUND** (0x94) 클라이언트가 바인딩 상태가 아님

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP에 사용하도록 설정된 인터페이스가 없음

- **NX_PTR_ERROR** (0x16) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
NX_DHCP_CLIENT_RECORD dhcp_record;


/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a>nx_dhcp_interface_client_get_record

지정된 인터페이스에서 현재 DHCP 클라이언트 상태에 대한 레코드 만들기

### <a name="prototype"></a>프로토타입

```C
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, 
                                 UINT interface_index,
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 인터페이스에서 실행되는 DHCP 클라이언트를 record_ptr이 가리키는 레코드에 저장합니다. 이를 통해 DHCP 클라이언트 애플리케이션은 전원을 끄고 재부팅하는 등의 방법으로 DHCP 클라이언트 상태를 복원할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 클라이언트에 대한 포인터

- **interface_index** 레코드를 가져올 인덱스

- **record_ptr** DHCP 클라이언트 레코드에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS (0x0)** 클라이언트 레코드를 만듦

- **NX_DHCP_NOT_BOUND** (0x94) 클라이언트가 바인딩 상태가 아님

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) 잘못된 인터페이스 인덱스

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
NX_DHCP_CLIENT_RECORD dhcp_record;


/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a>nx_dhcp_ client_restore_record

이전에 저장한 레코드에서 DHCP 클라이언트 복원

### <a name="prototype"></a>프로토타입

```C
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD       
                                    *record_ptr, ULONG time_elapsed);
```
### <a name="description"></a>Description

이 서비스를 통해 애플리케이션은 record_ptr에서 가리키는 DHCP 클라이언트 레코드를 사용하여 이전 세션에서 해당 DHCP 클라이언트를 복원할 수 있습니다. time_elapsed 입력은 DHCP 클라이언트 임대에서 남은 시간에 적용됩니다.

이렇게 하려면 먼저 DHCP 클라이언트 애플리케이션에서 전원을 끄기 전에 DHCP 클라이언트의 레코드를 만들고 비휘발성 메모리에 해당 레코드를 저장해야 합니다.

DHCP 클라이언트에 대해 둘 이상의 인터페이스가 사용하도록 설정된 경우 이 서비스는 DHCP 클라이언트 인스턴스에서 찾은 첫 번째 유효한 인터페이스에 적용됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 클라이언트에 대한 포인터

- **record_ptr** DHCP 클라이언트 레코드에 대한 포인터

- **time_elapsed** 입력 클라이언트 레코드의 남은 임대 시간에서 뺄 시간

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x0) 클라이언트 레코드 복원됨

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP를 실행하는 인터페이스가 없음

- **NX_PTR_ERROR** (0x16) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제
```C
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr
   contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a>nx_dhcp_interace_client_restore_record

지정된 인터페이스의 이전에 저장된 레코드에서 DHCP 클라이언트 복원

### <a name="prototype"></a>프로토타입

```C
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD       
                                              *record_ptr, ULONG time_elapsed);
```
### <a name="description"></a>Description

이 서비스를 통해 애플리케이션은 record_ptr에서 가리키는 DHCP 클라이언트 레코드를 사용하여 지정된 인터페이스에서 해당 DHCP 클라이언트를 복원할 수 있습니다. time_elapsed 입력은 DHCP 클라이언트 임대에서 남은 시간에 적용됩니다.

이렇게 하려면 먼저 DHCP 클라이언트 애플리케이션에서 전원을 끄기 전에 DHCP 클라이언트의 레코드를 만들고 비휘발성 메모리에 해당 레코드를 저장해야 합니다.

DHCP 클라이언트에 대해 둘 이상의 인터페이스가 사용하도록 설정된 경우 이 서비스는 DHCP 클라이언트 인스턴스에서 찾은 첫 번째 유효한 인터페이스에 적용됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 클라이언트에 대한 포인터

- **record_ptr** DHCP 클라이언트 레코드에 대한 포인터

- **time_elapsed** 입력 클라이언트 레코드의 남은 임대 시간에서 뺄 시간

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x0) 클라이언트 레코드 복원됨

- **NX_DHCP_NOT_BOUND**: (0x94) 클라이언트가 IP 주소에 바인딩되지 않음

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) 잘못된 인터페이스 인덱스

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  
   contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a>nx_dhcp_ client_update_time_remaining

DHCP 클라이언트 임대에서 남은 시간 업데이트

### <a name="prototype"></a>프로토타입

```C
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr
                                           ULONG time_elapsed);
```
### <a name="description"></a>Description

이 서비스는 DHCP 클라이언트 인스턴스에서 DHCP를 사용하도록 설정된 첫 번째 인터페이스에 대한 time_elapsed 입력으로 DHCP 클라이언트 IP 주소 임대의 남은 시간을 업데이트합니다. 애플리케이션은 *nx_dhcp_suspend* 를 사용하여 이 서비스를 사용하기 전에 DHCP 클라이언트 스레드를 일시 중단해야 합니다. 이 서비스를 호출한 후 애플리케이션은 *nx_dhcp_resume* 을 호출하여 DHCP 클라이언트 스레드를 다시 시작할 수 있습니다.

이는 일정 시간 동안 DHCP 클라이언트 스레드를 일시 중단해야 하는 DHCP 클라이언트 애플리케이션을 위한 것이며 남은 IP 주소 임대 시간을 업데이트합니다.

> [!NOTE]
> 이 서비스는 이전에 설명한 *nx_dhcp_client_get_record* 및 *nx_dhcp_client_restore_record* 와 함께 사용 하기 위한 것이 아닙니다. 이러한 서비스는 이 섹션에서 이전에 설명되었습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 클라이언트에 대한 포인터

- **time_elapsed** IP 주소 임대의 남은 시간에서 뺄 시간

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x0) 클라이언트 IP 임대가 업데이트됨

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP에 사용하도록 설정된 인터페이스가 없음

- **NX_PTR_ERROR** (0x16) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```


## <a name="nx_dhcp_interface_client_update_time_remaining"></a>nx_dhcp_interface_client_update_time_remaining

지정된 인터페이스에서 DHCP 클라이언트 임대의 남은 시간 업데이트

### <a name="prototype"></a>프로토타입

```C
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```
### <a name="description"></a>Description

이 서비스는 해당 인터페이스가 DHCP에 대해 사용하도록 설정된 경우 지정된 인터페이스에서 time_elapsed 입력으로 DHCP 클라이언트 IP 주소 임대의 남은 시간을 업데이트합니다. 애플리케이션은 *nx_dhcp_suspend* 를 사용하여 이 서비스를 사용하기 전에 DHCP 클라이언트 스레드를 일시 중단해야 합니다. 이 서비스를 호출한 후 애플리케이션은 *nx_dhcp_resume* 을 호출하여 DHCP 클라이언트 스레드를 다시 시작할 수 있습니다. 참고 DHCP 클라이언트 스레드를 일시 중단하고 다시 시작하면 DHCP에 활성화된 모든 인터페이스에 적용됩니다.

이는 일정 시간 동안 DHCP 클라이언트 스레드를 일시 중단해야 하는 DHCP 클라이언트 애플리케이션을 위한 것이며 남은 IP 주소 임대 시간을 업데이트합니다.

> [!NOTE] 
> 이 서비스는 이전에 설명한 *nx_dhcp_client_get_record* 및 *nx_dhcp_client_restore_record* 와 함께 사용 하기 위한 것이 아닙니다. 이러한 서비스는 이 섹션에서 이전에 설명되었습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 클라이언트에 대한 포인터

- **interface_index** 경과된 시간을 적용할 인터페이스에 대한 인덱스

- **time_elapsed** IP 주소 임대의 남은 시간에서 뺄 시간

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x0) 클라이언트 IP 임대가 업데이트됨

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR** (0x9A) 잘못된 인터페이스 인덱스

- NX_PTR_ERROR (0x16) 잘못된 DHCP 포인터

- NX_INVALID_INTERFACE (0x4C) 잘못된 네트워크 인터페이스

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```


## <a name="nx_dhcp_suspend"></a>nx_dhcp_suspend

DHCP 클라이언트 스레드 일시 중단

### <a name="prototype"></a>프로토타입

```C
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a>Description

이 서비스는 현재 DHCP 클라이언트 스레드를 일시 중단합니다. *nx_dhcp_stop* 과 달리 이 서비스를 호출하는 경우 DHCP 클라이언트 상태는 변경되지 않습니다.

이 서비스는 DHCP를 사용하도록 설정된 모든 인터페이스에서 실행되는 DHCP를 일시 중단합니다.

DHCP 클라이언트를 일시 중단하는 동안 경과된 시간으로 DHCP 클라이언트 상태를 업데이트하려면 앞에서 설명한 *nx_dhcp_client_update_time_remaining* 을 참조하세요. 일시 중단된 DHCP 클라이언트 스레드를 다시 시작하려면 애플리케이션이 *nx_dhcp_resume* 을 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 클라이언트에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x0) 클라이언트 스레드가 일시 중단됨

- **NX_PTR_ERROR** (0x16) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```


## <a name="nx_dhcp_resume"></a>nx_dhcp_resume

일시 중단된 DHCP 클라이언트 스레드 다시 시작

### <a name="prototype"></a>프로토타입

```C
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a>Description

이 서비스는 일시 중단된 DHCP 클라이언트 스레드를 다시 시작합니다. 클라이언트 스레드를 다시 시작한 후 실제 DHCP 클라이언트 상태는 변경되지 않습니다. DHCP 클라이언트 IP 주소 임대에서 남은 시간을 *nx_dhcp_resume* 을 호출하기 전에 경과된 시간으로 업데이트하려면 앞에서 설명한 *nx_dhcp_client_update_time_remaining* 을 참조하세요.

이 서비스는 DHCP를 사용하도록 설정된 모든 인터페이스에서 실행되는 DHCP를 다시 시작합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **dhcp_ptr** DHCP 클라이언트에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x0) 클라이언트 스레드가 다시 시작됨

- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```C
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```