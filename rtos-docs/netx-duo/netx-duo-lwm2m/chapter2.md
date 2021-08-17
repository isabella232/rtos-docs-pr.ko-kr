---
title: 2장 - RTOS NetX Duo LWM2M 클라이언트 설치 및 사용
description: 이 장에서는 RTOS NetX Duo LWM2M 클라이언트를 설치하고 사용하는 방법을 설명합니다.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f804ae59dd639ca05d1b8f5251cf8b878e78bb9ad2575e08c21d43b14e727a19
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796517"
---
# <a name="chapter-2--installation-and-use-of-lwm2m-client"></a>2장 - LWM2M 클라이언트의 설치 및 사용

이 장에서는 LWM2M 클라이언트 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS LWM2M 클라이언트는 [https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m](https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m/)에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다. 패키지에는 다음과 같은 세 개의 원본 파일, 하나의 포함 파일이 포함되어 있습니다.

* **nx\_lwm2m\_client.h** LWM2M 클라이언트에 대한 헤더 파일

* **nx\_lwm2m\_client.c** LWM2M 클라이언트에 대한 C 원본 파일

* **demo\_netx\_lwm2m\_client.c** LWM2M 클라이언트 데모에 대한 C 원본 파일

## <a name="lwm2m-client-installation"></a>LWM2M 클라이언트 설치

LWM2M 클라이언트는 NetX Duo의 일부입니다. 따라서 GitHub 리포지토리에서 NetX Duo를 복제한 후 ***netxduo/addons/lwm2m*** 에서 LWM2M 클라이언트 원본을 찾을 수 있습니다.

## <a name="using-lwm2m_client"></a>LWM2M\_클라이언트 사용

LWM2M 클라이언트를 사용하는 것은 간단합니다. 기본적으로 애플리케이션 코드에는 ThreadX 및 NetX를 사용하기 위해 ***_ _tx\_api.h_ *_ 및 _* _nx\_api.h_ *_를 포함한 후에 nx\_lwm2m\_client.h*가 포함되어야 합니다. _* _nx\_lwm2m\_client.h_ *_가 포함되면 애플리케이션 코드는 이 가이드의 뒷부분에 지정된 LWM2M 클라이언트 함수 호출을 수행할 수 있습니다. 또한 애플리케이션은 __* _nx\_lwm2m\_client\_.\**** 파일을 NetX 라이브러리로 가져와야 합니다.

## <a name="configuration-options"></a>구성 옵션

LWM2M 클라이언트를 사용하여 LWM2M 클라이언트 라이브러리 및 애플리케이션을 빌드할 때 몇 가지 구성 옵션이 있습니다. 구성 옵션은 달리 지정되지 않은 경우 명령줄에서 애플리케이션 원본에 정의할 수 있습니다.

| 구성&nbsp;옵션 | Description |
| --- | --- |
| **NX\_LWM2M\_CLIENT\_MTU** | IP 및 UDP 헤더를 포함하여 CoAP 메시지의 최대 크기를 지정합니다. 기본값은 1280입니다. |
| **NX\_LWM2M\_CLIENT\_SOCKET\_TOS** | LwM2M UDP에 필요한 서비스 유형입니다. 기본적으로 이 값은 일반 IP 패킷 서비스를 나타내기 위해 NX\_IP\_NORMAL로 정의됩니다. |
| **NX\_LWM2M\_CLIENT\_SOCKET\_TTL** | 이 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다. 기본값은 0x80으로 설정됩니다. |
| **NX\_LWM2M\_CLIENT\_SOCKET\_QUEUE\_MAX** | 수신 큐의 최대 깊이 수를 지정합니다. 기본값은 4로 설정됩니다. |
| **NX\_LWM2M\_CLIENT\_MAX\_COAP\_URI\_PATH** | CoAP Uri-Path 옵션의 최대 길이 수를 지정합니다. 기본값은 32로 설정됩니다. |
| **NX\_LWM2M\_CLIENT\_MAX\_DEVICE\_ERRORS** | 디바이스 개체에 의해 저장되는 최대 오류 코드 수를 지정합니다. 기본값은 8입니다. |
| **NX\_LWM2M\_CLIENT\_MAX\_SECURITY\_INSTANCES** | 보안 개체 인스턴스의 최대 수를 지정합니다. 부트스트랩 서버와 표준 서버를 지원하기 위한 기본값은 2입니다. |
| **NX\_LWM2M\_CLIENT\_MAX\_SERVER\_INSTANCES** | 서버 개체 인스턴스의 최대 수를 지정합니다. 단일 표준 서버를 지원하기 위한 기본값은 1입니다. |
| **NX\_LWM2M\_CLIENT\_MAX\_ACCESS\_CONTROL\_INSTANCES** | Access Control 인스턴스의 최대 수를 지정합니다. 기본값은 0이며, 이 값은 액세스 제어를 사용하지 않도록 설정합니다. 애플리케이션에서 둘 이상의 LWM2M 서버를 지원하는 경우 Access Control 인스턴스의 최대 수를 LWM2M 클라이언트에서 지원할 최대 개체 인스턴스 수로 설정해야 합니다. 단, 보안 개체 인스턴스를 제외하고 각 개체 인스턴스에 대해 하나의 Access Control 인스턴스를 만들어야 합니다. |
| **NX\_LWM2M\_CLIENT\_MAX\_ACCESS\_CONTROL\_ACLS** | Access Control 인스턴스당 ACL 리소스의 최대 수를 지정합니다. 기본값은 4입니다. |
| **NX\_LWM2M\_CLIENT\_MAX\_NOTIFICATIONS** | LWM2M 클라이언트가 지원할 최대 알림 수를 지정합니다. LWM2M 서버는 개체, 개체 인스턴스 및 리소스에 대한 알림을 설정할 수 있습니다. 기본값은 8입니다. |
| **NX\_LWM2M\_CLIENT\_MAX\_RESOURCES** | 개체당 최대 리소스 수를 지정합니다. 기본값은 32입니다. |
| **NX\_LWM2M\_CLIENT\_MAX\_MULTIPLE\_RESOURCES** | 여러 리소스에 대한 최대 리소스 인스턴스 수를 지정합니다. 기본값은 8입니다. |
| **NX\_LWM2M\_CLIENT\_BOOTSTRAP\_IDLE\_TIMER** | 세션을 중단하기 전에 부트스트랩 세션이 시작될 때 부트스트랩 서버 요청을 대기할 최대 시간을 지정합니다. 기본값은 60초입니다. |
| **NX\_LWM2M\_CLIENT\_DTLS\_START\_TIMEOUT** | DTLS 핸드셰이크 완료를 대기할 최대 시간을 지정합니다. 기본값은 30초입니다. |
| **NX\_LWM2M\_CLIENT\_DTLS\_END\_TIMEOUT** | DTLS 종료 완료를 대기할 최대 시간을 지정합니다. 기본값은 5 초입니다. |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_SERVER\_URI** | null 종료 문자를 포함하여 서버 URI의 최대 길이를 지정합니다. 기본값은 128입니다. |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_PUBLIC\_KEY\_OR\_IDENTITY** | DTLS에 대한 공개 키 또는 ID의 최대 길이를 지정합니다. 기본값은 128입니다. |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_SERVER\_PUBLIC\_KEY** | DTLS에 대한 서버 공개 키의 최대 길이를 지정합니다. 기본값은 128입니다. |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_SECRET\_KEY** | DTLS에 대한 비밀 키의 최대 길이를 지정합니다. 기본값은 128입니다. |
| **NX\_LWM2M\_CLIENT\_HOLD\_OFF** | 부트스트랩을 초기화할 때까지 기다리는 시간(초)을 지정합니다. 기본값은 1초입니다. |
| **NX\_LWM2M\_CLIENT\_LIFE\_TIME** | 등록 수명의 시간(초)을 지정합니다. 기본값은 600초입니다. |
