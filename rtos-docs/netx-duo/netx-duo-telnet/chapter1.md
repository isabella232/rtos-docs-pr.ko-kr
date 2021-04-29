---
title: 1장 - Azure RTOS NetX Duo Telnet 소개
description: Azure RTOS NetX Duo Telnet은 인터넷에서 두 노드 간에 명령과 응답을 전송하기 위해 설계된 프로토콜입니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d25f5ca4a7bf1ecf4c3d0c68ef6c8aeda7800098
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810549"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-telnet"></a>1장 - Azure RTOS NetX Duo Telnet 소개

Azure RTOS NetX Duo Telnet은 인터넷에서 두 노드 간에 명령과 응답을 전송하기 위해 설계된 프로토콜입니다. 텔넷은 신뢰할 수 있는 TCP(Transmission Control Protocol) 서비스를 활용하여 전송 기능을 수행하는 간단한 프로토콜입니다. 따라서 텔넷은 매우 신뢰할 수 있는 전송 프로토콜이며, 가장 많이 사용되는 애플리케이션 프로토콜 중 하나이기도 합니다.

## <a name="telnet-requirements"></a>텔넷 요구 사항

NetX Duo Telnet 패키지를 제대로 작동하려면 NetX IP 인스턴스가 이미 만들어져 있어야 합니다. 또한 동일한 IP 인스턴스에서 TCP를 사용하도록 설정해야 합니다. NetX Duo Telnet 패키지의 텔넷 클라이언트 부분에는 추가 요구 사항이 없습니다.

NetX Duo Telnet 패키지의 텔넷 서버 부분에는 추가 요구 사항이 하나 있습니다. 모든 클라이언트 텔넷 요청을 처리하려면 TCP의 ‘잘 알려진 포트 23’에 대한 완전한 액세스 권한이 필요합니다.

## <a name="telnet-constraints"></a>텔넷 제약 조건 

NetX Duo Telnet 프로토콜은 텔넷 표준을 구현합니다. 그러나 값이 255인 바이트로 표시되는 텔넷 명령의 해석 및 응답은 애플리케이션이 담당합니다. 다양한 텔넷 명령 및 명령 매개 변수는 *nxd_telnet_client.h, nxd_telnet_server.h* 파일에 정의됩니다.

## <a name="telnet-communication"></a>텔넷 통신

앞에서 설명한 대로 텔넷 서버는 ‘잘 알려진 TCP 포트 23’을 활용하여 클라이언트 요청을 처리합니다. 텔넷 클라이언트는 사용 가능한 모든 TCP 포트를 이용할 수 있습니다.

## <a name="telnet-authentication"></a>텔넷 인증

텔넷 인증은 애플리케이션의 텔넷 서버 콜백 함수가 담당합니다. 애플리케이션의 텔넷 서버 “새 연결” 콜백은 일반적으로 클라이언트에 이름 및/또는 암호를 묻는 프롬프트를 표시합니다. 그러면 클라이언트는 정보를 제공하는 역할을 담당하게 됩니다. 그런 다음, 서버는 “데이터 수신” 콜백의 정보를 처리합니다. 여기서 애플리케이션 서버 코드는 정보를 인증하고 그 정보가 유효한지 여부를 결정해야 합니다.

## <a name="telnet-new-connection-callback"></a>텔넷 새 연결 콜백

NetX Duo Telnet 서버는 새 텔넷 클라이언트 요청이 수신될 때마다 애플리케이션 지정 콜백 함수를 호출합니다. 애플리케이션은 ***nx_telnet_server_create*** 함수를 통해 텔넷 서버를 만들 때 콜백 함수를 지정합니다. “새 연결” 콜백의 일반적인 작업에는 클라이언트에 배너 또는 프롬프트를 보내는 작업이 포함됩니다. 여기에는 로그인 정보에 대한 프롬프트를 매우 잘 포함할 수 있습니다.

### <a name="prototype"></a>프로토타입

```c
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr**: 호출하는 텔넷 서버에 대한 포인터입니다.
- **logical_connection**: 텔넷 서버에 대한 내부 논리적 연결입니다. 이는 애플리케이션에서 각 클라이언트 연결에 특정된 버퍼 및/또는 데이터 구조에 대한 인덱스로 사용할 수 있습니다. 값 범위는 0에서 NX_TELNET_MAX_CLIENTS - 1까지입니다.

## <a name="telnet-receive-data-callback"></a>텔넷 데이터 수신 콜백

NetX Duo Telnet 서버는 새 텔넷 클라이언트 데이터가 수신될 때마다 애플리케이션 지정 콜백 함수를 호출합니다. 애플리케이션은 ***nx_telnet_server_create*** 함수를 통해 텔넷 서버를 만들 때 콜백 함수를 지정합니다. “새 연결” 콜백의 일반적인 작업에는 데이터를 다시 에코 하거나 데이터를 구문 분석하고 클라이언트에서 명령을 해석한 결과로 데이터를 제공하는 작업이 포함됩니다.

또한 이 콜백 루틴은 제공된 패킷을 릴리스해야 합니다.

### <a name="prototype"></a>프로토타입

```c
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, 
                          UINT logical_connection, NX_PACKET *packet_ptr);
```
### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr**: 호출하는 텔넷 서버에 대한 포인터입니다.
- **logical_connection**: 텔넷 서버에 대한 내부 논리적 연결입니다. 이는 애플리케이션에서 각 클라이언트 연결에 특정된 버퍼 및/또는 데이터 구조에 대한 인덱스로 사용할 수 있습니다. 값 범위는 0에서 NX_TELNET_MAX_CLIENTS - 1까지입니다.
- **packet_ptr**: 클라이언트에서 데이터를 포함하는 패킷에 대한 포인터입니다.

## <a name="telnet-end-connection-callback"></a>텔넷 연결 종료 콜백

NetX Duo Telnet 서버는 텔넷 클라이언트가 연결을 종료할 때마다 애플리케이션 지정 콜백 함수를 호출합니다. 애플리케이션은 ***nx_telnet_server_create*** 함수를 통해 텔넷 서버를 만들 때 콜백 함수를 지정합니다. “연결 종료” 콜백의 일반적인 작업에는 논리적 연결과 관련된 모든 클라이언트 특정 데이터 구조를 정리하는 작업이 포함됩니다.

### <a name="prototype"></a>프로토타입
```c
void  telnet_end_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>입력 매개 변수

- **server_ptr** 호출하는 텔넷 서버에 대한 포인터입니다.
- **logical_connection** 텔넷 서버에 대한 내부 논리적 연결입니다. 이는 애플리케이션에서 각 클라이언트 연결에 특정된 버퍼 및/또는 데이터 구조에 대한 인덱스로 사용할 수 있습니다. 값 범위는 0에서 NX_TELNET_MAX_CLIENTS - 1까지입니다.

## <a name="telnet-option-negotiation"></a>텔넷 옵션 협상

NetX Duo Telnet 서버는 제한된 텔넷 옵션 세트인 Echo 및 Suppress Go Ahead를 지원합니다.

이 기능을 사용하려면 NX_TELNET_SERVER_OPTION_DISABLE를 정의하지 않아야 합니다. 기본적으로 정의되지 않았습니다. 텔넷 서버는 *nx_telnet_server_create* 서비스에서 패킷 풀을 만들어 텔넷 옵션 요청을 클라이언트에 보내기 위한 패킷을 할당합니다. 이 패킷 풀의 패킷 페이로드(NX_TELNET_SERVER_PACKET_PAYLOAD) 및 패킷 풀 크기(NX_TELNET_SERVER_PACKET_POOL_SIZE)를 설정하려면 “구성 옵션”을 참조하세요. *nx_telnet_server_delete* 서비스를 호출할 때 이 패킷 풀을 삭제합니다.

텔넷 클라이언트에 연결한 후 클라이언트로부터 옵션 요청을 받지 못한 경우 다음 텔넷 옵션 세트를 클라이언트에 보냅니다.

- will echo
- dont echo
- will sga

클라이언트로부터 텔넷 데이터를 수신하는 경우 텔넷 서버는 첫 번째 바이트가 “IAC” 코드인지 확인합니다. 이런 경우 클라이언트 패킷의 모든 옵션을 처리합니다. 위의 목록에 없는 옵션은 무시됩니다.

기본적으로 NX_TELNET_SERVER_OPTION_DISABLE이 정의되어 있지 않고 텔넷 옵션 명령을 전송해야 하는 경우, 텔넷 서버는 자체 내부 패킷 풀을 만듭니다. 텔넷 서버 패킷 풀은 NX_TELNET_SERVER_PACKET_PAYLOAD 및 NX_TELNET_SERVER_PACKET_POOLSIZE에 의해 정의됩니다. 그러나 NX_TELNET_SERVER_USER_CREATE_PACKET_POOL이 정의되어 있는 경우 애플리케이션은 텔넷 서버 패킷 풀을 만들고 *_nx_telnet_server_packet_pool_set* 을 호출하여 텔넷 서버 패킷 풀로 설정해야 합니다. 이 기능에 대한 자세한 내용은 3장 “텔넷 서비스 설명”을 참조하세요.

NetX Duo Telnet 서버와 달리 NetX Duo Telnet 클라이언트 작업 스레드는 텔넷 서버에서 수신된 옵션을 자동으로 보내거나 응답하지 않습니다. 이 작업은 텔넷 클라이언트 애플리케이션에서 수행해야 합니다.

## <a name="telnet-multi-thread-support"></a>텔넷 다중 스레드 지원

NetX Duo Telnet Client 서비스는 다중 스레드에서 동시에 호출할 수 있습니다. 그러나 특정 텔넷 클라이언트 인스턴스에 대한 읽기 또는 쓰기 요청은 동일한 스레드에서 순서대로 수행되어야 합니다.

## <a name="telnet-rfcs"></a>텔넷 RFC

NetX Duo Telnet은 RFC854 및 관련 RFC를 준수합니다.
