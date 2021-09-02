---
title: 2장 - Azure RTOS NetX Duo Iperf 설치 및 사용
description: 이 장에서는 Iperf 샘플 설치 및 사용에 대한 지침을 제공합니다.
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7e80d89a334ceec3467b23574ab5c231a15f68a1
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2021
ms.locfileid: "122609797"
---
# <a name="chapter-2-installation-and-use"></a>2장 설치 및 사용

이 장에서는 NetX Duo Iperf 데모의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="installing-the-demonstration"></a>데모 설치

배포 시 제공된 플랫폼별 설치 지침을 따르세요.

## <a name="installing-iperf"></a>Iperf 설치

다양한 Iperf 프로그램을 사용할 수 있습니다. 그러나 이 문서의 예는 인터넷의 여러 소스에서 사용할 수 있는 Java 기반 ***Jperf 2.0.2*** 를 기반으로 합니다.

> [참고] *Jperf를 사용하려면 Java가 호스트 컴퓨터에 설치되어 있어야 합니다.*

## <a name="setting-the-ip-address"></a>IP 주소 설정

기본적으로 NetX Duo Iperf 데모의 IP 주소는 **192.2.2.149** 로 설정됩니다. 이는 _ **** nx_ip_create 호출에 대한 매개변수로 demo_netx_duo_iperf.c __ _ 파일에 설정됩니다.

## <a name="network-assumptions"></a>네트워크 가정

이 데모에서는 Iperf 호스트 컴퓨터와 NetX Duo Iperf 데모를 실행하는 대상 보드가 100Mbps 전이중 이더넷 스위치에 연결되어 있다고 가정합니다. 최상의 성능을 얻으려면 테스트 네트워크에 다른 트래픽이 없어야 합니다.

Iperf 호스트와 NetX Duo 대상 보드를 크로스오버 이더넷 케이블로 연속적으로 연결할 수도 있습니다.

## <a name="running-the-demonstration"></a>데모 실행

데모를 실행하는 것은 쉽습니다. 일반적으로 이름이 ***demo_netx_duo_iperf*** 인 NetX Duo Iperf 데모 프로젝트를 로드, 빌드 및 실행하기만 하면 됩니다.

## <a name="browse-to-the-demonstration"></a>데모 찾아보기

Iperf 호스트 플랫폼의 브라우저를 통해 대상 보드를 찾습니다. 대상 보드 IP 주소가 **192.2.2.149** 라고 가정하면 다음은 NetX Duo Iperf 데모 초기 웹 페이지의 예입니다.

![Iperf 초기 웹 페이지의 예](media/Picture1.jpg)

## <a name="running-jperf"></a>Jperf 실행

Jperf를 실행하는 것은 쉽습니다. Windows 배치 파일 ***jperf.bat** _를 두 번 클릭하기만 하면 됩니다. 그러면 아래와 같이 Jperf IDE가 시작됩니다. Jperf IDE가 표시되면 _ *Server Address** 필드를 NetX Duo Iperf 데모 대상 보드의 IP 주소로 설정해야 합니다. 이 예에서 NetX Duo 대상 보드 IP 주소는 **192.2.2.149** 입니다. **UDP 대역폭** 및 **UDP 패킷 크기** 필드도 주목할 가치가 있습니다. 아래와 같이 최적의 UDP 수신 성능을 위해 설정해야 합니다.

![UDP 성능 최적화.](media/Picture2.jpg)
