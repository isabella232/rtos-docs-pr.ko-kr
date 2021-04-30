---
title: 부록 A - Azure RTOS NetX Duo DHCPv6 클라이언트의 복원 상태 기능 설명
description: Azure RTOS NetX Duo DHDPv6 클라이언트 구성 옵션인 NX_DHCPV6_CLIENT_RESTORE_STATE를 사용하면 시스템 다시 부팅 간에 Bound 상태에서 이전에 만든 DHCP 클라이언트를 복원할 수 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3e642af158202bb3b2a4e2a37397b47d707b566e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810915"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a><span data-ttu-id="77bd0-103">부록 A - Azure RTOS NetX Duo DHCPv6 클라이언트의 복원 상태 기능 설명</span><span class="sxs-lookup"><span data-stu-id="77bd0-103">Appendix A - Description of the Restore State Feature for Azure RTOS NetX Duo DHCPv6 Client</span></span>

<span data-ttu-id="77bd0-104">Azure RTOS NetX Duo DHDPv6 클라이언트 구성 옵션인 NX_DHCPV6_CLIENT_RESTORE_STATE를 사용하면 시스템 다시 부팅 간에 Bound 상태에서 이전에 만든 DHCP 클라이언트를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-104">The Azure RTOS NetX Duo DHDPv6 Client configuration option, NX_DHCPV6_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client in a Bound state between system reboots.</span></span>

<span data-ttu-id="77bd0-105">이 옵션을 사용하면 애플리케이션에서 DHCPv6 클라이언트 스레드를 일시 중단하고 다시 시작할 수 있으며, 전원 끄기 없이 스레드를 일시 중단하고 다시 시작하는 동안 경과된 시간으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-105">This option also allows an application to suspend the DHCPv6 Client thread and resume it, updated with the elapsed time between suspending and resuming the thread without powering down.</span></span>

## <a name="restoring-the-dhcpv6-client-between-reboots"></a><span data-ttu-id="77bd0-106">다시 부팅 간에 DHCPv6 클라이언트 복원</span><span class="sxs-lookup"><span data-stu-id="77bd0-106">Restoring the DHCPv6 Client between Reboots</span></span>

<span data-ttu-id="77bd0-107">다시 부팅 간에 DHCPv6 클라이언트를 복원하기 위해 DHCPv6 애플리케이션은 DHCPv6 클라이언트의 인스턴스를 만든 다음, 일반 DHCPv6 프로토콜을 사용하고 *nx_dhcpv6_start* 를 호출하여 IP 주소 임대를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-107">To restore a DHCPv6 Client between reboots, the DHCPv6 application creates an instance of the DHCPv6 Client, and then obtains an IP address lease using the normal DHCPv6 protocol and calling *nx_dhcpv6_start*.</span></span> <span data-ttu-id="77bd0-108">그런 다음, DHCPv6 애플리케이션은 프로토콜이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-108">Then the DHCPv6 application waits for the protocol to complete.</span></span> <span data-ttu-id="77bd0-109">모두 제대로 작동하는 경우 디바이스는 DHCPv6 서버에서 할당된 유효한 IP 주소를 사용하여 BOUND 상태를 달성합니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-109">If all goes well, the device achieves the BOUND state with an assigned valid IP address from its DHCPv6 Server.</span></span> <span data-ttu-id="77bd0-110">전원이 꺼질 때까지 DHCPv6 클라이언트 애플리케이션은 현재 DHCPv6 클라이언트 인스턴스를 DHCPv6 클라이언트 레코드에 저장합니다. 그러면 비휘발성 메모리에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-110">Before it powers down, the DHCPv6 Client application saves the current DHCPv6 Client instance to a DHCPv6 Client record which is then stored in non-volatile memory.</span></span> <span data-ttu-id="77bd0-111">시스템의 다른 곳에서 독립적인 '시간 키퍼'는 이 전원이 꺼진 상태에서 경과된 시간을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-111">An independent ‘time keeper’ elsewhere in the system keeps track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="77bd0-112">전원을 켜면 애플리케이션은 새 DHCPv6 클라이언트 인스턴스를 만든 다음, 이전에 만든 DHCPv6 클라이언트 레코드를 사용하여 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-112">On powering up, the application creates a new DHCPv6 Client instance, and then updates it with the previously created DHCPv6 Client record.</span></span> <span data-ttu-id="77bd0-113">경과된 시간은 "시간 키퍼"에서 가져온 다음, DHCP Clientv6 임대의 남은 시간에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-113">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Clientv6 lease.</span></span> <span data-ttu-id="77bd0-114">이 시점에서 애플리케이션은 DHCPv6 클라이언트를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-114">At this point, the application can resume the DHCPv6 Client.</span></span>

<span data-ttu-id="77bd0-115">전원 끄기 중 경과된 시간이 DHCPv6 클라이언트 상태를 RENEW 또는 REBIND 상태 중 하나로 설정하면 DHCPv6 클라이언트는 IP 주소 임대를 갱신하거나 리바인딩하기 위한 DHCPv6 메시지 요청을 자동으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-115">If the time elapsed during power down puts the DHCPv6 Client state in either a RENEW or REBIND state, the DHCPv6 Client will automatically initiate DHCPv6 messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="77bd0-116">IP 주소가 만료된 경우 DHCPv6 클라이언트는 자동으로 IP 인스턴스의 IP 주소를 지우고 새 IP 주소를 요청하여 INIT 상태에서 DHCPv6 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-116">If the IP address is expired, the DHCPv6 Client will automatically clear the IP address on the IP instance and begin the DHCPv6 process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="77bd0-117">이러한 방식으로 DHCPv6 클라이언트는 중단 없이 다시 부팅 간에 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-117">In this manner the DHCPv6 Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="77bd0-118">이 기능에 대한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-118">Below is an illustration of this feature.</span></span>

```C
/* On the power up, create an IP instance, DHCPv6 Client, enable ICMPv6 and UDP
   and other resources (not shown) for the DHCPv6 Client/application
   in tx_application_define(). */
 
/* Define the DHCPv6 Client application thread. */     
void    thread_dhcpv6_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCPV6_CLIENT_RECORD client_my_record;


    /* No previously saved Client record. Start the DHCPv6 Client in the INIT state. */
    status =  nx_dhcpv6_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    while(1)    
    {
    
        /* Wait for DHCPv6 Client to get the IP address. */
    }

    /* At some point decide we power down the system. */

    /* Save the Client state data which we will subsequently need to restore the DHCPv6    
       Client. */
    status = nx_dhcpv6_client_get_record(&dhcp_0, &client_my_record);               

    /* Copy this memory to non-volatile memory (not shown). */

    /* Delete the IP and DHCPv6 Client instances before powering down. */
    nx_dhcpv6_client_delete(&dhcp_0);

    nx_ip_delete(&ip_0);

    /* Ready to power down, having released other resources as necessary. */

    /* The application has determined there is a previously saved record. We will 
       restore it to the current DHCPv6 Client instance. */

/* Create the IP and DHCPv6 Client instances, enable ICMPv6 and UDP after powering up. */

/* Calculate the time elapsed during power down */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
       update the IP instance with IP address, mask etc. */
    status = nx_dhcpv6_client_restore_record(&dhcp_0, &client_my_record, time_elapsed);   

     if (status != NX_SUCCESS)
          return;

     /* We are ready to resume the DHCPv6 Client thread and use the assigned IP address. */
     status = nx_dhcpv6_resume(&dhcp_0);

     if (status != NX_SUCCESS)
          return;

}
```

## <a name="nx_dhcpv6_client_get_record"></a><span data-ttu-id="77bd0-119">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="77bd0-119">nx_dhcpv6_client_get_record</span></span>

<span data-ttu-id="77bd0-120">현재 DHCPv6 클라이언트 상태에 대한 레코드 만들기</span><span class="sxs-lookup"><span data-stu-id="77bd0-120">Create a record of the current DHCPv6 Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="77bd0-121">프로토타입</span><span class="sxs-lookup"><span data-stu-id="77bd0-121">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="77bd0-122">Description</span><span class="sxs-lookup"><span data-stu-id="77bd0-122">Description</span></span>

<span data-ttu-id="77bd0-123">이 서비스는 record_ptr이 가리키는 레코드에 DHCPv6 클라이언트를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-123">This service saves the DHCPv6 Client to the record pointed to by record_ptr.</span></span> <span data-ttu-id="77bd0-124">이를 통해 DHCPv6 클라이언트 애플리케이션은 전원을 끄고 다시 부팅하는 등의 방법으로 DHCPv6 클라이언트 상태를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-124">This allows the DHCPv6 Client application restore its DHCPv6 Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77bd0-125">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="77bd0-125">Input Parameters</span></span>

- <span data-ttu-id="77bd0-126">**dhcpv6_ptr** DHCPv6 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="77bd0-126">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="77bd0-127">**record_ptr** DHCPv6 클라이언트 레코드에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="77bd0-127">**record_ptr** Pointer to DHCPv6 Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="77bd0-128">반환 값</span><span class="sxs-lookup"><span data-stu-id="77bd0-128">Return Values</span></span>

- <span data-ttu-id="77bd0-129">**NX_SUCCESS (0x0)** 유효한 클라이언트 레코드를 만듦</span><span class="sxs-lookup"><span data-stu-id="77bd0-129">**NX_SUCCESS (0x0)** Valid Client record created</span></span>

- <span data-ttu-id="77bd0-130">**NX_DHCPV6_NOT_BOUND** (0xE94) 클라이언트가 바인딩된 상태가 아니므로 유효한 IP 주소가 할당되지 않음</span><span class="sxs-lookup"><span data-stu-id="77bd0-130">**NX_DHCPV6_NOT_BOUND** (0xE94) Client not in bound state, therefore not assigned valid IP address</span></span>

- <span data-ttu-id="77bd0-131">**NX_PTR_ERROR** (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="77bd0-131">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77bd0-132">허용 위치</span><span class="sxs-lookup"><span data-stu-id="77bd0-132">Allowed From</span></span>

<span data-ttu-id="77bd0-133">스레드</span><span class="sxs-lookup"><span data-stu-id="77bd0-133">Threads</span></span>

### <a name="example"></a><span data-ttu-id="77bd0-134">예제</span><span class="sxs-lookup"><span data-stu-id="77bd0-134">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a><span data-ttu-id="77bd0-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="77bd0-135">See Also</span></span>

- <span data-ttu-id="77bd0-136">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="77bd0-136">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="77bd0-137">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="77bd0-137">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="77bd0-138">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="77bd0-138">nx_dhcpv6_client_restore_record</span></span>

## <a name="nx_dhcpv6_client_restore_record"></a><span data-ttu-id="77bd0-139">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="77bd0-139">nx_dhcpv6_client_restore_record</span></span>

<span data-ttu-id="77bd0-140">저장된 레코드에서 DHCPv6 클라이언트 상태 복원</span><span class="sxs-lookup"><span data-stu-id="77bd0-140">Restore DHCPv6 Client state from saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="77bd0-141">프로토타입</span><span class="sxs-lookup"><span data-stu-id="77bd0-141">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="77bd0-142">Description</span><span class="sxs-lookup"><span data-stu-id="77bd0-142">Description</span></span>

<span data-ttu-id="77bd0-143">이 서비스를 통해 DHCPv6 애플리케이션은 record_ptr에서 가리키는 DHCPv6 클라이언트 레코드를 사용하여 DHCPv6 클라이언트를 업데이트하여 이전 세션에서 DHCPv6 클라이언트 상태를 다시 만들고, time_elapsed 입력으로 DHCPv6 클라이언트 임대에서 남은 시간을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-143">This service enables a DHCPv6 application to recreate its DHCPv6 Client state from a previous session by updating the DHCPv6 Client with the DHCPv6 Client record pointed to by record_ptr, and updates the time remaining on DHCPv6 Client lease with the time_elapsed input.</span></span> <span data-ttu-id="77bd0-144">이를 통해 DHCPv6 클라이언트 애플리케이션은 전원을 끈 후와 같이 DHCPv6 클라이언트를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-144">This allows the DHCPv6 Client application to recreate its DHCPv6 Client, for example, after powering down.</span></span> <span data-ttu-id="77bd0-145">이렇게 하려면 먼저 DHCPv6 클라이언트 애플리케이션에서 전원을 끄기 전에 DHCPv6 클라이언트의 레코드를 만들고 비휘발성 메모리에 해당 레코드를 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77bd0-145">This requires that the DHCPv6 Client application created a record of the DHCPv6 Client before powering down, and saved that record to non-volatile memory.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="77bd0-146">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="77bd0-146">Input Parameters</span></span>

- <span data-ttu-id="77bd0-147">**dhcpv6_ptr** DHCPv6 클라이언트에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="77bd0-147">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="77bd0-148">**record_ptr** DHCPv6 클라이언트 레코드에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="77bd0-148">**record_ptr** Pointer to DHCPv6 Client record</span></span>

- <span data-ttu-id="77bd0-149">**time_elapsed** 입력 클라이언트 레코드의 남은 임대 시간에서 뺄 시간</span><span class="sxs-lookup"><span data-stu-id="77bd0-149">**time_elapsed** Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="77bd0-150">반환 값</span><span class="sxs-lookup"><span data-stu-id="77bd0-150">Return Values</span></span>

- <span data-ttu-id="77bd0-151">**NX_SUCCESS (0x0)** 클라이언트 레코드 복원됨</span><span class="sxs-lookup"><span data-stu-id="77bd0-151">**NX_SUCCESS (0x0)** Client record restored</span></span>

- <span data-ttu-id="77bd0-152">NX_PTR_ERROR (0x16) 잘못된 포인터 입력</span><span class="sxs-lookup"><span data-stu-id="77bd0-152">NX_PTR_ERROR (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="77bd0-153">허용 위치</span><span class="sxs-lookup"><span data-stu-id="77bd0-153">Allowed From</span></span>

<span data-ttu-id="77bd0-154">스레드</span><span class="sxs-lookup"><span data-stu-id="77bd0-154">Threads</span></span>

### <a name="example"></a><span data-ttu-id="77bd0-155">예제</span><span class="sxs-lookup"><span data-stu-id="77bd0-155">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a><span data-ttu-id="77bd0-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="77bd0-156">See Also</span></span>

- <span data-ttu-id="77bd0-157">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="77bd0-157">nx_dhcpv6_client_get_record</span></span>