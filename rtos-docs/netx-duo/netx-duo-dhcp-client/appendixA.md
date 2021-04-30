---
title: 부록 A - Azure RTOS NetX Duo DHCP 클라이언트 서비스의 복원 상태 기능 설명
description: 이 장에서는 Azure RTOS NetX Duo DHCP 클라이언트 서비스의 복원 상태 기능 설명을 포함합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 008ca6fb0052339e188e0240cc38a81d3a6b40e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810962"
---
# <a name="appendix-a--description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="f7b6c-103">부록 A: Azure RTOS NetX Duo DHCP 클라이언트 서비스의 복원 상태 기능 설명</span><span class="sxs-lookup"><span data-stu-id="f7b6c-103">Appendix A : Description of the Restore state feature for Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="f7b6c-104">NetX Duo DHDP 클라이언트 구성 옵션인 NX_DHCP_CLIENT_RESTORE_STATE를 사용하면 시스템 다시 부팅 간에 Bound 상태에서 이전에 만든 DHCP 클라이언트 레코드를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-104">The NetX Duo DHDP Client configuration option, NX_DHCP_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client Record in a Bound state between system reboots.</span></span>

<span data-ttu-id="f7b6c-105">이 옵션을 사용하도록 설정하면 애플리케이션이 DHCP 클라이언트 스레드를 일시 중단하고 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-105">When this option is enabled, the application can suspend and resume the DHCP Client thread.</span></span> <span data-ttu-id="f7b6c-106">또한 스레드를 일시 중단하고 다시 시작하는 시간 사이에 경과된 시간으로 DHCP 클라이언트를 업데이트하는 서비스도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-106">There is also a service to update the DHCP Client with the elapsed time between suspending and resuming the thread.</span></span>

## <a name="restoring-the-dhcp-client-between-reboots"></a><span data-ttu-id="f7b6c-107">다시 부팅 간에 DHCP 클라이언트 복원</span><span class="sxs-lookup"><span data-stu-id="f7b6c-107">Restoring the DHCP Client between Reboots</span></span>

<span data-ttu-id="f7b6c-108">다시 부팅한 후 DHCP 클라이언트를 복원하기 전에 이전에 만든 DHCP 클라이언트는 Bound 상태에 도달해야 하며 DHCP 서버의 IP 주소가 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-108">Before restoring a DHCP Client after rebooting, a previously created DHCP Client that must reach the Bound state and be is assigned an IP address from the DHCP server.</span></span> <span data-ttu-id="f7b6c-109">전원이 꺼질 때까지 DHCP 애플리케이션은 현재 DHCP 클라이언트 레코드를 비휘발성 메모리로 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-109">Before it powers down, the DHCP application must then save the current DHCP Client record to non-volatile memory.</span></span> <span data-ttu-id="f7b6c-110">또한 시스템의 다른 곳에 독립적인 '시간 키퍼'가 있어야 이 전원이 꺼진 상태에서 경과된 시간을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-110">There must also be an independent ‘time keeper’ elsewhere in the system to keep track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="f7b6c-111">전원을 켜면 애플리케이션은 새 DHCP 클라이언트 인스턴스를 만든 다음, 이전에 만든 DHCP 클라이언트 레코드를 사용하여 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-111">On powering up, the application creates a new DHCP Client instance, and then updates it with the previously created DHCP Client record.</span></span> <span data-ttu-id="f7b6c-112">경과된 시간은 "시간 키퍼"에서 가져온 다음, DHCP 클라이언트 임대의 남은 시간에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-112">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Client lease.</span></span> <span data-ttu-id="f7b6c-113">이로 인해 DHCP 클라이언트가 상태를 변경(예: BOUND에서 RENEWING으로)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-113">Note that this may cause the DHCP Client to change states e.g. from BOUND to RENEWING.</span></span> <span data-ttu-id="f7b6c-114">이 시점에서 애플리케이션은 DHCP 클라이언트를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-114">At this point, the application can resume the DHCP Client.</span></span>

<span data-ttu-id="f7b6c-115">전원 끄기 중 경과된 시간이 DHCP 클라이언트 상태를 RENEW 또는 REBIND 상태 중 하나로 설정하면 DHCP 클라이언트는 IP 주소 임대를 갱신하거나 리바인딩하기 위한 DHCP 메시지 요청을 자동으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-115">If the time elapsed during power down puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="f7b6c-116">IP 주소가 만료된 경우 DHCP 클라이언트는 자동으로 IP 인스턴스의 IP 주소를 지우고 새 IP 주소를 요청하여 INIT 상태에서 DHCP 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-116">If the IP address is expired, the DHCP Client will automatically clear the IP address on the IP instance and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="f7b6c-117">이러한 방식으로 DHCP 클라이언트는 중단 없이 다시 부팅 간에 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-117">In this manner the DHCP Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="f7b6c-118">이 기능에 대한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-118">Below is an illustration of this feature.</span></span> <span data-ttu-id="f7b6c-119">이때 DHCP 클라이언트는 기본 인터페이스에서만 실행되는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-119">This assumes DHCP Client is running only on the primary interface.</span></span>

```c
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{
    /* No previously saved Client record. Start the DHCP Client in the INIT state.  */
    status =  nx_dhcp_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    do
    {
        /* Wait for DHCP to assign the IP address.  */
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
        restore it to the current DHCP Client instance.  */

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
## <a name="resuming-the-dhcp-client-thread-after-suspension"></a><span data-ttu-id="f7b6c-120">일시 중단 후 DHCP 클라이언트 스레드 다시 시작</span><span class="sxs-lookup"><span data-stu-id="f7b6c-120">Resuming the DHCP Client Thread after Suspension</span></span> 

<span data-ttu-id="f7b6c-121">전원 끄기 없이 DHCP 클라이언트 스레드를 일시 중단하기 위해 애플리케이션은 BOUND 상태를 달성하고 유효한 IP 주소를 가진 DHCP 클라이언트에서 *nx_dhcp_suspend* 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-121">To suspend a DHCP Client thread without powering down, the application calls *nx_dhcp_suspend* on a DHCP Client which has achieved the BOUND state and which has a valid IP address.</span></span> <span data-ttu-id="f7b6c-122">DHCP 클라이언트를 다시 시작할 준비가 되면 먼저 *nx_dhcp_client_update_time_remaining* 을 호출하여 DHCP 주소 임대에서 남은 시간을 업데이트합니다(독립 시간 키퍼에서 경과된 시간 가져오기).</span><span class="sxs-lookup"><span data-stu-id="f7b6c-122">When it is ready to resume the DHCP Client it first calls *nx_dhcp_client_update_time_remaining* to update the time remaining on the DHCP address lease (obtaining the time elapsed from an independent time keeper).</span></span> <span data-ttu-id="f7b6c-123">그런 다음, *nx_dhcp_resume* 을 호출하여 DHCP 클라이언트 스레드를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-123">Then it calls the *nx_dhcp_resume* to resume the DHCP Client thread.</span></span>

<span data-ttu-id="f7b6c-124">경과된 시간이 DHCP 클라이언트 상태를 RENEW 또는 REBIND 상태 중 하나로 설정하면 DHCP 클라이언트는 IP 주소 임대를 갱신하거나 리바인딩하기 위한 DHCP 메시지 요청을 자동으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-124">If the time elapsed puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="f7b6c-125">IP 주소가 만료된 경우 DHCP 클라이언트는 자동으로 IP 주소를 지우고 새 IP 주소를 요청하여 INIT 상태에서 DHCP 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-125">If the IP address is expired, the DHCP Client will automatically clear the IP address and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="f7b6c-126">이 기능 사용에 대한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-126">Below is an illustration of using this feature.</span></span>

```c
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client.  */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   /* Wait for DHCP to obtain an IP address.  */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the network...  */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the elapsed      
     time. */


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
<span data-ttu-id="f7b6c-127">다음은 DHCP 클라이언트 상태를 메모리에서 복원하고 DHCP 클라이언트를 일시 중단하고 다시 시작하기 위한 서비스 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-127">Below is a list of services for restoring a DHCP Client state from memory and for suspending and resuming the DHCP Client.</span></span>

## <a name="nx_dhcp_client_get_record"></a><span data-ttu-id="f7b6c-128">nx_dhcp_client_get_record</span><span class="sxs-lookup"><span data-stu-id="f7b6c-128">nx_dhcp_client_get_record</span></span>

<span data-ttu-id="f7b6c-129">현재 DHCP 클라이언트 상태에 대한 레코드 만들기</span><span class="sxs-lookup"><span data-stu-id="f7b6c-129">Create a record of the current DHCP Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="f7b6c-130">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7b6c-130">Prototype</span></span>

```c
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="f7b6c-131">Description</span><span class="sxs-lookup"><span data-stu-id="f7b6c-131">Description</span></span>

<span data-ttu-id="f7b6c-132">이 서비스는 DHCP 클라이언트 인스턴스에서 DHCP를 사용하는 첫 번째 인터페이스에서 실행되는 DHCP 클라이언트를 record_ptr이 가리키는 레코드에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-132">This service saves the DHCP Client running on the first interface enabled for DHCP found on the DHCP Client instance to the record pointed to by record_ptr.</span></span> <span data-ttu-id="f7b6c-133">이를 통해 DHCP 클라이언트 애플리케이션은 전원을 끄고 다시 부팅하는 등의 방법으로 DHCP 클라이언트 상태를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-133">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

<span data-ttu-id="f7b6c-134">DHCP에 대해 둘 이상의 인터페이스를 사용하는 경우 특정 인터페이스에 DHCP 클라이언트 레코드를 저장하려면 *nx_dhcp_interface_client_get_record* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-134">To save a DHCP Client record on a specific interface if more than one interface is enabled for DHCP, use the *nx_dhcp_interface_client_get_record* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7b6c-135">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7b6c-135">Input Parameters</span></span>

- <span data-ttu-id="f7b6c-136">**dhcp_ptr**: DHCP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-136">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="f7b6c-137">**record_ptr**: DHCP 클라이언트 레코드에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-137">**record_ptr**: Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="f7b6c-138">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7b6c-138">Return Values</span></span>

- <span data-ttu-id="f7b6c-139">**NX_SUCCESS (0x0)** 클라이언트 레코드를 만듦</span><span class="sxs-lookup"><span data-stu-id="f7b6c-139">**NX_SUCCESS (0x0)**: Client record created</span></span>
- <span data-ttu-id="f7b6c-140">**NX_DHCP_NOT_BOUND**: (0x94) 클라이언트가 Bound 상태가 아님</span><span class="sxs-lookup"><span data-stu-id="f7b6c-140">**NX_DHCP_NOT_BOUND**: (0x94) Client not in Bound states</span></span>
- <span data-ttu-id="f7b6c-141">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP에 사용하도록 설정된 인터페이스가 없음</span><span class="sxs-lookup"><span data-stu-id="f7b6c-141">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="f7b6c-142">NX_PTR_ERROR: (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f7b6c-142">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7b6c-143">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7b6c-143">Allowed From</span></span>

<span data-ttu-id="f7b6c-144">스레드</span><span class="sxs-lookup"><span data-stu-id="f7b6c-144">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f7b6c-145">예제</span><span class="sxs-lookup"><span data-stu-id="f7b6c-145">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a><span data-ttu-id="f7b6c-146">nx_dhcp_interface_client_get_record</span><span class="sxs-lookup"><span data-stu-id="f7b6c-146">nx_dhcp_interface_client_get_record</span></span>

<span data-ttu-id="f7b6c-147">지정된 인터페이스에서 현재 DHCP 클라이언트 상태에 대한 레코드 만들기</span><span class="sxs-lookup"><span data-stu-id="f7b6c-147">Create a record of the current DHCP Client state on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="f7b6c-148">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7b6c-148">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, UINT interface_index,
                                          NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="f7b6c-149">Description</span><span class="sxs-lookup"><span data-stu-id="f7b6c-149">Description</span></span>

<span data-ttu-id="f7b6c-150">이 서비스는 지정된 인터페이스에서 실행되는 DHCP 클라이언트를 record_ptr이 가리키는 레코드에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-150">This service saves the DHCP Client running on the specified interface to the record pointed to by record_ptr.</span></span> <span data-ttu-id="f7b6c-151">이를 통해 DHCP 클라이언트 애플리케이션은 전원을 끄고 다시 부팅하는 등의 방법으로 DHCP 클라이언트 상태를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-151">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7b6c-152">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7b6c-152">Input Parameters</span></span>

- <span data-ttu-id="f7b6c-153">**dhcp_ptr**: DHCP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-153">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="f7b6c-154">**interface_index**: 레코드를 가져올 인덱스</span><span class="sxs-lookup"><span data-stu-id="f7b6c-154">**interface_index**: Index on which to get record</span></span>
- <span data-ttu-id="f7b6c-155">**record_ptr**: DHCP 클라이언트 레코드에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-155">**record_ptr**: Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="f7b6c-156">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7b6c-156">Return Values</span></span>

- <span data-ttu-id="f7b6c-157">**NX_SUCCESS (0x0)** 클라이언트 레코드를 만듦</span><span class="sxs-lookup"><span data-stu-id="f7b6c-157">**NX_SUCCESS (0x0)**: Client record created</span></span>
- <span data-ttu-id="f7b6c-158">**NX_DHCP_NOT_BOUND**: (0x94) **클라이언트가 Bound 상태가 아님**</span><span class="sxs-lookup"><span data-stu-id="f7b6c-158">**NX_DHCP_NOT_BOUND**: (0x94) **Client not in Bound state**</span></span>
- <span data-ttu-id="f7b6c-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) 잘못된 인터페이스 인덱스</span><span class="sxs-lookup"><span data-stu-id="f7b6c-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="f7b6c-160">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-160">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="f7b6c-161">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7b6c-161">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7b6c-162">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7b6c-162">Allowed From</span></span>

<span data-ttu-id="f7b6c-163">스레드</span><span class="sxs-lookup"><span data-stu-id="f7b6c-163">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f7b6c-164">예제</span><span class="sxs-lookup"><span data-stu-id="f7b6c-164">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a><span data-ttu-id="f7b6c-165">nx_dhcp_ client_restore_record</span><span class="sxs-lookup"><span data-stu-id="f7b6c-165">nx_dhcp_ client_restore_record</span></span>

<span data-ttu-id="f7b6c-166">이전에 저장한 레코드에서 DHCP 클라이언트 복원</span><span class="sxs-lookup"><span data-stu-id="f7b6c-166">Restore DHCP Client from a previously saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="f7b6c-167">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7b6c-167">Prototype</span></span>

```c
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD *record_ptr, 
                                    ULONG time_elapsed);

```

### <a name="description"></a><span data-ttu-id="f7b6c-168">Description</span><span class="sxs-lookup"><span data-stu-id="f7b6c-168">Description</span></span>

<span data-ttu-id="f7b6c-169">이 서비스를 통해 애플리케이션은 record_ptr에서 가리키는 DHCP 클라이언트 레코드를 사용하여 이전 세션에서 해당 DHCP 클라이언트를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-169">This service enables an application to restore its DHCP Client from a previous session using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="f7b6c-170">time_elapsed 입력은 DHCP 클라이언트 임대에서 남은 시간에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-170">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="f7b6c-171">이렇게 하려면 먼저 DHCP 클라이언트 애플리케이션에서 전원을 끄기 전에 DHCP 클라이언트의 레코드를 만들고 비휘발성 메모리에 해당 레코드를 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-171">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="f7b6c-172">DHCP 클라이언트에 대해 둘 이상의 인터페이스가 사용하도록 설정된 경우 이 서비스는 DHCP 클라이언트 인스턴스에서 찾은 첫 번째 유효한 인터페이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-172">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7b6c-173">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7b6c-173">Input Parameters</span></span>

- <span data-ttu-id="f7b6c-174">**dhcp_ptr**: DHCP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-174">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="f7b6c-175">**record_ptr**: DHCP 클라이언트 레코드에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-175">**record_ptr**: Pointer to DHCP Client record</span></span> 
- <span data-ttu-id="f7b6c-176">**time_elapsed**: 입력 클라이언트 레코드의 남은 임대 시간에서 뺄 시간</span><span class="sxs-lookup"><span data-stu-id="f7b6c-176">**time_elapsed**: Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="f7b6c-177">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7b6c-177">Return Values</span></span>

- <span data-ttu-id="f7b6c-178">**NX_SUCCESS**: (0x0) 클라이언트 레코드 복원됨</span><span class="sxs-lookup"><span data-stu-id="f7b6c-178">**NX_SUCCESS**: (0x0) Client record restored</span></span>
- <span data-ttu-id="f7b6c-179">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP를 실행하는 인터페이스가 없음</span><span class="sxs-lookup"><span data-stu-id="f7b6c-179">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces running DHCP</span></span>
- <span data-ttu-id="f7b6c-180">NX_PTR_ERROR: (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f7b6c-180">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7b6c-181">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7b6c-181">Allowed From</span></span>

<span data-ttu-id="f7b6c-182">스레드</span><span class="sxs-lookup"><span data-stu-id="f7b6c-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f7b6c-183">예제</span><span class="sxs-lookup"><span data-stu-id="f7b6c-183">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a><span data-ttu-id="f7b6c-184">nx_dhcp_interace_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="f7b6c-184">nx_dhcp_interace_client_restore_record</span></span>

<span data-ttu-id="f7b6c-185">지정된 인터페이스의 이전에 저장된 레코드에서 DHCP 클라이언트 복원</span><span class="sxs-lookup"><span data-stu-id="f7b6c-185">Restore DHCP Client from a previously saved record on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="f7b6c-186">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7b6c-186">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD *record_ptr, 
                                              ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="f7b6c-187">Description</span><span class="sxs-lookup"><span data-stu-id="f7b6c-187">Description</span></span>

<span data-ttu-id="f7b6c-188">이 서비스를 통해 애플리케이션은 record_ptr에서 가리키는 DHCP 클라이언트 레코드를 사용하여 지정된 인터페이스에서 해당 DHCP 클라이언트를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-188">This service enables an application to restore its DHCP Client on the specified interface using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="f7b6c-189">time_elapsed 입력은 DHCP 클라이언트 임대에서 남은 시간에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-189">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="f7b6c-190">이렇게 하려면 먼저 DHCP 클라이언트 애플리케이션에서 전원을 끄기 전에 DHCP 클라이언트의 레코드를 만들고 비휘발성 메모리에 해당 레코드를 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-190">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="f7b6c-191">DHCP 클라이언트에 대해 둘 이상의 인터페이스가 사용하도록 설정된 경우 이 서비스는 DHCP 클라이언트 인스턴스에서 찾은 첫 번째 유효한 인터페이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-191">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7b6c-192">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7b6c-192">Input Parameters</span></span>

- <span data-ttu-id="f7b6c-193">**dhcp_ptr**: DHCP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-193">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="f7b6c-194">**record_ptr**: DHCP 클라이언트 레코드에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-194">**record_ptr**: Pointer to DHCP Client record</span></span> 
- <span data-ttu-id="f7b6c-195">**time_elapsed**: 입력 클라이언트 레코드의 남은 임대 시간에서 뺄 시간</span><span class="sxs-lookup"><span data-stu-id="f7b6c-195">**time_elapsed**: Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="f7b6c-196">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7b6c-196">Return Values</span></span>

- <span data-ttu-id="f7b6c-197">**NX_SUCCESS**: (0x0) 클라이언트 레코드 복원됨</span><span class="sxs-lookup"><span data-stu-id="f7b6c-197">**NX_SUCCESS**: (0x0) Client record restored</span></span>
- <span data-ttu-id="f7b6c-198">**NX_DHCP_NOT_BOUND**: (0x94) 클라이언트가 IP 주소에 바인딩되지 않음</span><span class="sxs-lookup"><span data-stu-id="f7b6c-198">**NX_DHCP_NOT_BOUND**: (0x94) Client not bound to IP address</span></span>
- <span data-ttu-id="f7b6c-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) 잘못된 인터페이스 인덱스</span><span class="sxs-lookup"><span data-stu-id="f7b6c-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="f7b6c-200">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-200">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="f7b6c-201">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7b6c-201">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7b6c-202">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7b6c-202">Allowed From</span></span>

<span data-ttu-id="f7b6c-203">스레드</span><span class="sxs-lookup"><span data-stu-id="f7b6c-203">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f7b6c-204">예제</span><span class="sxs-lookup"><span data-stu-id="f7b6c-204">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a><span data-ttu-id="f7b6c-205">nx_dhcp_ client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="f7b6c-205">nx_dhcp_ client_update_time_remaining</span></span>

<span data-ttu-id="f7b6c-206">DHCP 클라이언트 임대에서 남은 시간 업데이트</span><span class="sxs-lookup"><span data-stu-id="f7b6c-206">Update the time remaining on DHCP Client lease</span></span>

### <a name="prototype"></a><span data-ttu-id="f7b6c-207">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7b6c-207">Prototype</span></span>

```c
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="f7b6c-208">Description</span><span class="sxs-lookup"><span data-stu-id="f7b6c-208">Description</span></span>

<span data-ttu-id="f7b6c-209">이 서비스는 DHCP 클라이언트 인스턴스에서 DHCP를 사용하도록 설정된 첫 번째 인터페이스에 대한 time_elapsed 입력으로 DHCP 클라이언트 IP 주소 임대의 남은 시간을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-209">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the first interface enabled for DHCP found on the DHCP Client instance.</span></span> <span data-ttu-id="f7b6c-210">애플리케이션은 *nx_dhcp_suspend* 를 사용하여 이 서비스를 사용하기 전에 DHCP 클라이언트 스레드를 일시 중단해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-210">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="f7b6c-211">이 서비스를 호출한 후 애플리케이션은 *nx_dhcp_resume* 을 호출하여 DHCP 클라이언트 스레드를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-211">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span>

<span data-ttu-id="f7b6c-212">이는 일정 시간 동안 DHCP 클라이언트 스레드를 일시 중단해야 하는 DHCP 클라이언트 애플리케이션을 위한 것이며 남은 IP 주소 임대 시간을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-212">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

<span data-ttu-id="f7b6c-213">참고: 이 서비스는 이전에 설명한 *nx_dhcp_client_get_record* 및 *nx_dhcp_client_restore_record* 와 함께 사용 하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-213">Note: This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="f7b6c-214">이러한 서비스는 이 섹션에서 이전에 설명되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-214">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7b6c-215">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7b6c-215">Input Parameters</span></span>

- <span data-ttu-id="f7b6c-216">**dhcp_ptr**: DHCP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-216">**dhcp_ptr**: Pointer to DHCP Client</span></span> 
- <span data-ttu-id="f7b6c-217">**time_elapsed**: IP 주소 임대의 남은 시간에서 뺄 시간</span><span class="sxs-lookup"><span data-stu-id="f7b6c-217">**time_elapsed**: Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="f7b6c-218">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7b6c-218">Return Values</span></span>

- <span data-ttu-id="f7b6c-219">**NX_SUCCESS**: (0x0) 클라이언트 IP 임대가 업데이트됨</span><span class="sxs-lookup"><span data-stu-id="f7b6c-219">**NX_SUCCESS**: (0x0) Client IP lease updated</span></span>
- <span data-ttu-id="f7b6c-220">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) DHCP에 사용하도록 설정된 인터페이스가 없음</span><span class="sxs-lookup"><span data-stu-id="f7b6c-220">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="f7b6c-221">NX_PTR_ERROR: (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f7b6c-221">NX_PTR_ERROR: (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7b6c-222">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7b6c-222">Allowed From</span></span>

<span data-ttu-id="f7b6c-223">스레드</span><span class="sxs-lookup"><span data-stu-id="f7b6c-223">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f7b6c-224">예제</span><span class="sxs-lookup"><span data-stu-id="f7b6c-224">Example</span></span>

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```

## <a name="nx_dhcp_interface_client_update_time_remaining"></a><span data-ttu-id="f7b6c-225">nx_dhcp_interface_client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="f7b6c-225">nx_dhcp_interface_client_update_time_remaining</span></span>

<span data-ttu-id="f7b6c-226">지정된 인터페이스에서 DHCP 클라이언트 임대의 남은 시간 업데이트</span><span class="sxs-lookup"><span data-stu-id="f7b6c-226">Update the time remaining on DHCP Client lease on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="f7b6c-227">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7b6c-227">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="f7b6c-228">Description</span><span class="sxs-lookup"><span data-stu-id="f7b6c-228">Description</span></span>

<span data-ttu-id="f7b6c-229">이 서비스는 해당 인터페이스가 DHCP에 대해 사용하도록 설정된 경우 지정된 인터페이스에서 time_elapsed 입력으로 DHCP 클라이언트 IP 주소 임대의 남은 시간을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-229">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="f7b6c-230">애플리케이션은 *nx_dhcp_suspend* 를 사용하여 이 서비스를 사용하기 전에 DHCP 클라이언트 스레드를 일시 중단해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-230">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="f7b6c-231">이 서비스를 호출한 후 애플리케이션은 *nx_dhcp_resume* 을 호출하여 DHCP 클라이언트 스레드를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-231">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span> <span data-ttu-id="f7b6c-232">참고 DHCP 클라이언트 스레드를 일시 중단하고 다시 시작하면 DHCP에 활성화된 모든 인터페이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-232">Note suspending and resuming the DHCP Client thread applies to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="f7b6c-233">이는 일정 시간 동안 DHCP 클라이언트 스레드를 일시 중단해야 하는 DHCP 클라이언트 애플리케이션을 위한 것이며 남은 IP 주소 임대 시간을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-233">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

<span data-ttu-id="f7b6c-234">참고: 이 서비스는 이전에 설명한 *nx_dhcp_client_get_record* 및 *nx_dhcp_client_restore_record* 와 함께 사용 하기 위한 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-234">Note: This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="f7b6c-235">이러한 서비스는 이 섹션에서 이전에 설명되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-235">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7b6c-236">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7b6c-236">Input Parameters</span></span>

- <span data-ttu-id="f7b6c-237">**dhcp_ptr**: DHCP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-237">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="f7b6c-238">**interface_index**: 경과된 시간을 적용할 인터페이스에 대한 인덱스</span><span class="sxs-lookup"><span data-stu-id="f7b6c-238">**interface_index**: Index to interface to apply elapsed time to</span></span>
- <span data-ttu-id="f7b6c-239">**time_elapsed**: IP 주소 임대의 남은 시간에서 뺄 시간</span><span class="sxs-lookup"><span data-stu-id="f7b6c-239">**time_elapsed**: Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="f7b6c-240">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7b6c-240">Return Values</span></span>

- <span data-ttu-id="f7b6c-241">**NX_SUCCESS**: (0x0) 클라이언트 IP 임대가 업데이트됨</span><span class="sxs-lookup"><span data-stu-id="f7b6c-241">**NX_SUCCESS**: (0x0) Client IP lease updated</span></span>
- <span data-ttu-id="f7b6c-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) 잘못된 인터페이스 인덱스</span><span class="sxs-lookup"><span data-stu-id="f7b6c-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="f7b6c-243">NX_PTR_ERROR: (0x16) 잘못된 DHCP 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-243">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="f7b6c-244">NX_INVALID_INTERFACE: (0x4C) 잘못된 네트워크 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f7b6c-244">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7b6c-245">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7b6c-245">Allowed From</span></span>

<span data-ttu-id="f7b6c-246">스레드</span><span class="sxs-lookup"><span data-stu-id="f7b6c-246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f7b6c-247">예제</span><span class="sxs-lookup"><span data-stu-id="f7b6c-247">Example</span></span>

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */

```

## <a name="nx_dhcp_suspend"></a><span data-ttu-id="f7b6c-248">nx_dhcp_suspend</span><span class="sxs-lookup"><span data-stu-id="f7b6c-248">nx_dhcp_suspend</span></span>

<span data-ttu-id="f7b6c-249">DHCP 클라이언트 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="f7b6c-249">Suspend the DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f7b6c-250">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7b6c-250">Prototype</span></span>

```c
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="f7b6c-251">Description</span><span class="sxs-lookup"><span data-stu-id="f7b6c-251">Description</span></span>

<span data-ttu-id="f7b6c-252">이 서비스는 현재 DHCP 클라이언트 스레드를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-252">This service suspends the current DHCP Client thread.</span></span> <span data-ttu-id="f7b6c-253">*nx_dhcp_stop* 과 달리 이 서비스를 호출하는 경우 DHCP 클라이언트 상태는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-253">Note that unlike *nx_dhcp_stop*, there is no change to the DHCP Client state when this service is called.</span></span>

<span data-ttu-id="f7b6c-254">이 서비스는 DHCP를 사용하도록 설정된 모든 인터페이스에서 실행되는 DHCP를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-254">This service suspends DHCP running on all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="f7b6c-255">DHCP 클라이언트를 일시 중단하는 동안 경과된 시간으로 DHCP 클라이언트 상태를 업데이트하려면 앞에서 설명한 *nx_dhcp_client_update_time_remaining* 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-255">To update the DHCP Client state with elapsed time while the DHCP Client is suspended, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span> <span data-ttu-id="f7b6c-256">일시 중단된 DHCP 클라이언트 스레드를 다시 시작하려면 애플리케이션이 *nx_dhcp_resume* 을 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-256">To resume a suspended DHCP Client thread, the application should call *nx_dhcp_resume*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7b6c-257">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7b6c-257">Input Parameters</span></span>

- <span data-ttu-id="f7b6c-258">**dhcp_ptr**: DHCP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-258">**dhcp_ptr**: Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="f7b6c-259">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7b6c-259">Return Values</span></span>

- <span data-ttu-id="f7b6c-260">**NX_SUCCESS**: (0x0) 클라이언트 스레드가 일시 중단됨</span><span class="sxs-lookup"><span data-stu-id="f7b6c-260">**NX_SUCCESS**: (0x0) Client thread is suspended</span></span>
- <span data-ttu-id="f7b6c-261">NX_PTR_ERROR: (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f7b6c-261">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7b6c-262">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7b6c-262">Allowed From</span></span>

<span data-ttu-id="f7b6c-263">스레드</span><span class="sxs-lookup"><span data-stu-id="f7b6c-263">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f7b6c-264">예제</span><span class="sxs-lookup"><span data-stu-id="f7b6c-264">Example</span></span>

```c
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```

## <a name="nx_dhcp_resume"></a><span data-ttu-id="f7b6c-265">nx_dhcp_resume</span><span class="sxs-lookup"><span data-stu-id="f7b6c-265">nx_dhcp_resume</span></span>

<span data-ttu-id="f7b6c-266">일시 중단된 DHCP 클라이언트 스레드 다시 시작</span><span class="sxs-lookup"><span data-stu-id="f7b6c-266">Resume a suspended DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f7b6c-267">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f7b6c-267">Prototype</span></span>

```c
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="f7b6c-268">Description</span><span class="sxs-lookup"><span data-stu-id="f7b6c-268">Description</span></span>

<span data-ttu-id="f7b6c-269">이 서비스는 일시 중단된 DHCP 클라이언트 스레드를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-269">This service resumes a suspended DHCP Client thread.</span></span> <span data-ttu-id="f7b6c-270">클라이언트 스레드를 다시 시작한 후 실제 DHCP 클라이언트 상태는 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-270">Note that there is no change to the actual DHCP Client state after resuming the Client thread.</span></span> <span data-ttu-id="f7b6c-271">DHCP 클라이언트 IP 주소 임대에서 남은 시간을 *nx_dhcp_resume* 을 호출하기 전에 경과된 시간으로 업데이트하려면 앞에서 설명한 *nx_dhcp_client_update_time_remaining* 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-271">To update the time remaining on the DHCP Client IP address lease with elapsed time before calling *nx_dhcp_resume*, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span>

<span data-ttu-id="f7b6c-272">이 서비스는 DHCP를 사용하도록 설정된 모든 인터페이스에서 실행되는 DHCP를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f7b6c-272">This service resumes DHCP running on all interfaces enabled for DHCP.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f7b6c-273">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f7b6c-273">Input Parameters</span></span>

- <span data-ttu-id="f7b6c-274">**dhcp_ptr**: DHCP 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="f7b6c-274">**dhcp_ptr**: Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="f7b6c-275">반환 값</span><span class="sxs-lookup"><span data-stu-id="f7b6c-275">Return Values</span></span>

- <span data-ttu-id="f7b6c-276">**NX_SUCCESS**: (0x0) 클라이언트 스레드가 다시 시작됨</span><span class="sxs-lookup"><span data-stu-id="f7b6c-276">**NX_SUCCESS**: (0x0) Client thread is resumed</span></span>
- <span data-ttu-id="f7b6c-277">NX_PTR_ERROR: (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="f7b6c-277">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f7b6c-278">허용 위치</span><span class="sxs-lookup"><span data-stu-id="f7b6c-278">Allowed From</span></span>

<span data-ttu-id="f7b6c-279">스레드</span><span class="sxs-lookup"><span data-stu-id="f7b6c-279">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f7b6c-280">예제</span><span class="sxs-lookup"><span data-stu-id="f7b6c-280">Example</span></span>

```c
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```