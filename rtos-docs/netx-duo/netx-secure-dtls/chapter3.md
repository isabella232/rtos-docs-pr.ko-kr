---
title: 챕터 3 - Azure RTOS NetX Secure DTLS의 기능 설명
description: 이 챕터에는 Azure RTOS NetX Secure DTLS에 대한 기능 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 468f1dc8a8334dc89064594b29dc8cfabd7d8fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811796"
---
# <a name="chapter-3-functional-description-of-azure-rtos-netx-secure-dtls"></a>챕터 3: Azure RTOS NetX Secure DTLS의 기능 설명

## <a name="execution-overview"></a>실행 개요

이 챕터에는 Azure RTOS NetX Secure DTLS에 대한 기능 설명이 포함되어 있습니다. NetX Secure DTLS 애플리케이션에는 초기화 및 애플리케이션 인터페이스 호출이라는 두 가지 주요 프로그램 실행 형식이 있습니다. 

NetX Secure는 ThreadX 및 NetX/NetXDuo가 있다고 가정합니다. ThreadX에서 스레드 실행, 일시 중단, 주기적인 타이머 및 상호 제외 기능이 필요합니다. NetX/NetXDuo에서는 UDP 및 IP 네트워킹 기능과 드라이버가 필요합니다.

## <a name="datagram-transport-layer-security-dtls-and-transport-layer-security-tls"></a>DTLS(데이터그램 전송 계층 보안) 및 TLS(전송 계층 보안)

NetX Secure DTLS는 RFC 6347에 정의된 데이터그램 전송 계층 보안 프로토콜 버전 1.2를 구현합니다. DTLS 버전 1.0은 RFC 4347에서 정의되었으며 TLS 버전 1.1에 해당합니다. DTLS는 기본적으로 TLS의 확장이므로 다음 버전에서 해당 TLS 버전과 동일한 버전 번호를 사용하도록 결정되었습니다. 따라서 DTLS 버전 1.2가 TLS 버전 1.2에 해당하므로 DTLS 버전 1.1은 없습니다.

> [!NOTE]
> NetX Secure는 DTLS 버전 1.2를 지원합니다. DTLS 1.0(RFC 4347)은 현재 지원되지 **않습니다**.

SSL(*Secure Sockets Layer*)은 RFC 2246에서 표준이 되기 전 TLS의 원래 이름이며 "SSL"이 TLS 프로토콜의 일반적인 이름으로 사용되는 경우가 많습니다. SSL의 마지막 버전은 3.0이고 TLS 1.0을 SSL 버전 3.1이라고 하는 경우도 있습니다. 공식 "SSL" 프로토콜의 모든 버전은 더 이상 사용되지 않고 안전하지 않은 것으로 간주되며 현재 NetX Secure는 SSL 구현을 제공하지 않습니다.

TLS는 TLS 클라이언트와 서버 간의 TLS *핸드셰이크* 중에 만들어지는 *세션 키* 를 생성하는 프로토콜을 지정하며, 이러한 키는 TLS *세션* 중에 애플리케이션에서 보낸 데이터를 암호화하는 데 사용됩니다.

기본 보안 메커니즘을 프로토콜 간에 공유하므로 DTLS가 TLS와 긴밀하게 결합되어 있습니다. 그러나 TLS는 패킷 전송 및 순서를 보장하는 전송 계층 프로토콜(실제로는 거의 항상 TCP)을 통해 작동하도록 설계되었으며 UDP처럼 신뢰할 수 없는 프로토콜에서는 작동하지 않습니다. 정확하게 말하자면, DTLS가 도입된 UDP 때문입니다. DTLS는 UDP 및 유사한 프로토콜의 신뢰할 수 없는 특성을 처리하도록 설계되었습니다. 이를 위해 TCP처럼 신뢰할 수 있는 프로토콜과 비슷하게 순서 및 안정성 논리(예: 삭제된 데이터 재전송)를 포함시킵니다.

TLS에 대한 전체 설명은 NetX Secure TLS 사용자 가이드의 챕터 3에 포함되어 있으며, 이 문서에서는 TLS와 DTLS의 차이점을 집중적으로 다룹니다.

### <a name="dtls-record-header"></a>DTLS 레코드 헤더

그림 1처럼 유효한 모든 DTLS 레코드에는 DTLS 헤더가 있어야 합니다. 헤더는 TLS와 동일하며 아래 설명처럼 16비트 *epoch* 필드 및 48비트 *시퀀스 번호* 필드가 새로 추가되었습니다.

![DTLS 레코드 헤더의 다이어그램](media/image2.png)

**그림 1 - DTLS 레코드 헤더**

TLS 레코드 헤더의 필드는 다음과 같이 정의됩니다.

| TLS 헤더 필드 | 용도  |
| ---------------- | --------- |
| **8비트 메시지 유형** | 이 필드에는 전송되는 DTLS 레코드 형식이 포함됩니다. 유효한 형식은 다음과 같습니다.<br />- ChangeCipherSpec: 0x14<br />- 경고: 0x15<br />- 핸드셰이크: 0x16<br />- 애플리케이션 데이터: 0x17<br /> |
| **16비트 프로토콜 버전** | 이 필드에는 DTLS 프로토콜 버전이 포함됩니다. 유효한 값은 다음과 같습니다.<br />- DTLS 1.1: 0xFEFD |
|  **16비트 Epoch** |  이 필드에는 암호화 상태가 바뀔 때마다(예: 새 세션 키를 생성하는 경우) 증가하는 카운터인 DTLS "epoch"가 포함됩니다.  |
|  **48비트 시퀀스 번호** |  이 필드에는 특정 레코드를 식별하는 시퀀스 번호가 포함됩니다. DTLS에서 레코드 순서를 유지하고 재전송이 필요한지 확인하는 데 사용됩니다. |
|  **16비트 길이** |  이 필드에는 DTLS 레코드에 캡슐화된 데이터의 길이가 포함됩니다.  |

### <a name="dtls-handshake-record-header"></a>DTLS 핸드셰이크 레코드 헤더

그림 2처럼 유효한 모든 DTLS 핸드셰이크 레코드에는 DTLS 핸드셰이크 헤더가 있어야 합니다.

![DTLS 핸드셰이크 레코드 헤더의 다이어그램](media/image3.png)

**그림 2 - DTLS 핸드셰이크 레코드 헤더**

DTLS 핸드셰이크 레코드 헤더의 필드는 다음과 같이 정의됩니다.

| TLS 헤더 필드 | 용도 |
| ---------------- | ------------------------------------------------ |
| **8비트 메시지 유형** | 이 필드에는 전송되는 DTLS 레코드 형식이 포함됩니다. 유효한 형식은 다음과 같습니다.<br />- ChangeCipherSpec: 0x14<br />- 경고: 0x15<br />- 핸드셰이크: 0x16<br />- 애플리케이션 데이터: 0x17 |
|  **16비트 Epoch** | 이 필드에는 암호화 상태가 바뀔 때마다(예: 새 세션 키를 생성하는 경우) 증가하는 카운터인 DTLS "epoch"가 포함됩니다. |
|  **48비트 시퀀스 번호** | 이 필드에는 특정 레코드를 식별하는 시퀀스 번호가 포함됩니다. DTLS에서 레코드 순서를 유지하고 재전송이 필요한지 확인하는 데 사용됩니다. |
|  **16비트 프로토콜 버전** | 이 필드에는 DTLS 프로토콜 버전이 포함됩니다. 유효한 값은 다음과 같습니다.<br />- DTLS 1.1: 0xFEFD |
| **16비트 길이** | 이 필드에는 DTLS 레코드에 캡슐화된 데이터의 길이가 포함됩니다. |
| **8비트 핸드셰이크 유형** | 이 필드는 핸드셰이크 메시지 유형을 포함합니다. 유효한 값은 다음과 같습니다.<br />- HelloRequest: 0x00<br />- ClientHello: 0x01<br />- ServerHello: 0x02<br />- Certificate: 0x0B<br />- ServerKeyExchange: 0x0C<br />- CertificateRequest: 0x0D<br />- ServerHelloDone: 0x0E<br />- CertificateVerify: 0x0F<br />- ClientKeyExchange: 0x10<br />- 완료됨 | 0x14 |
| **24비트 길이** | 이 필드는 핸드셰이크 메시지 데이터의 길이를 포함합니다. |
| **16비트 시퀀스 번호** | 이 필드에는 시퀀스 번호가 포함됩니다. |

### <a name="the-dtls-handshake-and-dtls-session"></a>DTLS 핸드셰이크 및 DTLS 세션

그림 3은 일반적인 DTLS 핸드셰이크입니다. 일반적인 TLS 핸드셰이크와 거의 같지만 결정적인 차이점이 있습니다. ClientHello 메시지가 처음으로 전송되면 서버에서는 "쿠키"가 포함된 새 DTLS 관련 메시지인 *HelloVerifyRequest* 로 응답합니다. DTLS 클라이언트에서는 핸드셰이크를 진행하려면 해당 쿠키가 포함된 두 번째 ClientHello 메시지로 응답해야 합니다. UDP가 비연결형 프로토콜이므로 특정 DoS(서비스 거부) 공격을 방지하기 위해 이 메커니즘이 DTLS에 추가되었습니다(TCP는 전용 연결/포트가 필요하므로 TLS에서는 동일한 문제가 발생하지 않음).

DTLS 핸드셰이크는 클라이언트에서 DTLS 서버에 *ClientHello* 메시지를 보내서 DTLS 세션을 시작하려 한다는 의도를 알릴 때 시작됩니다. 이 메시지에는 클라이언트가 세션에 사용할 암호화에 대한 정보와 함께 나중에 핸드셰이크에서 세션 키를 생성하는 데 사용되는 정보가 포함됩니다. 세션 키가 생성될 때까지 DTLS 핸드셰이크의 모든 메시지는 암호화되지 않습니다. 위에서 언급했듯이, DTLS 서버는 ClientHello에 대한 응답으로 HelloVerifyRequest를 전송하여 클라이언트가 두 번째 업데이트된 ClientHello로 응답하도록 강제할 수 있습니다.

두 번째 ClientHello 메시지가 수신되면 DTLS 서버는 쿠키를 확인하고, 쿠키가 올바른 경우 클라이언트에서 제공하는 암호화 옵션의 선택 항목을 나타내는 ServerHello 메시지로 응답합니다. ServerHello 뒤에는 Certificate 메시지가 오며, 여기에는 클라이언트에서 서버의 ID를 인증하기 위해 서버가 제공하는 디지털 인증서가 포함됩니다(X.509 확인을 사용하는 경우). 마지막으로 서버는 ServerHelloDone 메시지를 보내서 더 이상 보낼 메시지가 없음을 알립니다. 서버에서는 필요하다면 ServerHello 다음에 다른 메시지를 보낼 수도 있고, 경우에 따라 Certificate 메시지를 보내지 않을 수도 있기 때문에(예: 미리 공유한 키가 사용되는 경우) ServerHelloDone 메시지가 필요합니다.

클라이언트가 서버의 모든 메시지를 수신하면 세션 키를 생성하기에 충분한 정보를 갖게 됩니다. TLS/DTLS는 고정 크기이며 암호화가 활성화되면 필요한 모든 키를 생성하기 위해 시드로 사용되는 *Pre-Master Secret* 이라는 임의 데이터의 공유 비트를 생성하여 이 작업을 수행합니다. Pre-Master Secret은 Hello 메시지에 지정된 공개 키 알고리즘(예: RSA)(공개 키 알고리즘에 대한 자세한 내용은 아래 참조) 및 서버가 인증서에서 제공한 공개 키를 사용하여 암호화됩니다. PSK(미리 공유한 키)라는 선택적 TLS/DTLS 기능을 사용하면 인증서를 사용하는 대신 호스트 간에 공유되는 비밀 값(일반적으로 물리적 전송 또는 기타 보안 방법을 통해)을 사용하는 암호 그룹을 사용할 수 있습니다. PSK를 사용하면 미리 공유한 비밀 키를 사용하여 Pre-Master Secret이 생성됩니다. 아래의 "인증 방법"에서 미리 공유한 키 섹션을 참조하세요.

일반적인 TLS/DTLS 핸드셰이크에서, 암호화된 Pre-Master Secret은 ClientKeyExchange 메시지에 포함되어 서버로 전송됩니다. 서버에서는 ClientKeyExchange 메시지를 받으면 자체 프라이빗 키를 사용하여 Pre-Master Secret을 해독하고 TLS/DTLS 클라이언트와 병렬로 세션 키 생성을 진행합니다.

세션 키가 생성되면 Hello 메시지에서 선택한 프라이빗 키 알고리즘(예: AES)을 사용하여 모든 추가 메시지를 암호화할 수 있습니다. 클라이언트와 서버 모두에서 ChangeCipherSpec이라는 암호화되지 않은 마지막 메시지 하나를 보내서 모든 추가 메시지가 암호화된다는 것을 나타냅니다.

클라이언트와 서버 모두에서 보낸 첫 번째 암호화된 메시지는 Finished라는 최종 TLS 핸드셰이크 메시지이기도 합니다. 이 메시지는 송수신한 모든 핸드셰이크 메시지의 해시를 포함합니다. 이 해시는 핸드셰이크의 어떤 메시지도 변조되거나 손상(보안 위반 가능성을 나타냄)되지 않았다는 것을 확인하는 데 사용됩니다.

Finished 메시지를 받고 핸드셰이크 해시가 확인되면, TLS/DTLS 세션이 시작되고 애플리케이션은 데이터 송수신을 시작합니다. TLS/DTLS 세션 중에 양쪽에서 전송된 모든 데이터는 먼저 Hello 메시지에서 선택한 해시 알고리즘을 사용하여 해시되고(메시지 무결성을 제공하기 위해) 생성된 세션 키와 함께 선택한 프라이빗 키 알고리즘을 사용하여 암호화됩니다.

마지막으로, TLS/DTLS 세션은 클라이언트나 서버에서 종료하기로 선택하는 경우에만 성공적으로 종료될 수 있습니다. 잘린 세션은 보안 위반으로 간주되며(모든 송신 데이터가 수신되는 것을 공격자가 막으려고 시도할 수 있기 때문에) 따라서 둘 중 한쪽에서 세션을 종료하려고 하면 CloseNotify 경고라는 특별한 알림이 전송됩니다. 세션 종료에 성공하려면 클라이언트와 서버 모두 CloseNotify 경고를 보내고 처리해야 합니다.

![일반적인 DTLS 핸드셰이크 세션의 다이어그램](media/image4.png)

**그림 3 - 일반적인 DTLS 핸드셰이크**

### <a name="initialization"></a>초기화

NetX Secure DTLS를 사용하기 전에 NetX 또는 NetXDuo 스택을 초기화해야 합니다. UDP 작업에 사용할 TCP/IP 스택을 제대로 초기화하는 방법에 대한 자세한 내용은 NetX 또는 NetXDuo 사용자 가이드를 참조하세요.

NetX UDP가 초기화되면 DTLS를 사용하도록 설정할 수 있습니다. 내부적으로 모든 DTLS 네트워크 트래픽 및 처리는 사용자의 개입 없이 NetX/NetXDuo 스택에서 처리됩니다. 단, DTLS에는 기본 네트워크 스택과 별도로 처리해야 하는 요구 사항이 있습니다. DTLS 클라이언트 작업의 경우 ***NX_SECURE_DTLS_SESSION** _이라는 매개 변수가 DTLS 제어 블록에 할당됩니다. DTLS 서버 작업의 경우 제어 블록을 _ *_NX_SECURE_DTLS_SERVER_**라고 하며, 여기에는 단일 UDP 포트에서 여러 DTLS 세션을 처리하는 데 필요한 인프라가 포함되어 있습니다. 이는 각 TLS 세션이 단일 TCP 포트에 바인딩되는 TLS와 다른 점입니다.

DTLS의 두 가지 모드인 서버 모드 및 클라이언트 모드는 애플리케이션에서 활성화할 수 있으며(단, NetX 소켓당 한 가지 모드만 가능), 각 모드의 고유한 요구 사항이 아래에 자세히 설명되어 있습니다.

### <a name="initialization--dtls-server"></a>초기화 – DTLS 서버

NetX Secure DTLS 서버 모드는 기본 네트워크 전송 프로토콜에 UDP를 사용하기 때문에 TLS 서버 모드와 다릅니다. TCP를 사용하는 경우 TLS 세션 동안 포트가 단일 원격 호스트에 바인딩됩니다. UDP는 원격 호스트와 관련된 개념이 없으므로 여러 호스트의 DTLS 요청을 동일한 UDP 인터페이스에서 모두 수신합니다. 따라서 DTLS는 TLS 및 TCP를 사용하는 것처럼 소켓에 의존하지 말고 세션 상태를 유지해야 합니다. 이러한 이유로 DTLS 서버 제어 블록(NX_SECURE_DTLS_SERVER)은 원격 호스트 정보(IP 주소 및 포트)와 DTLS 세션의 매핑을 유지합니다. DTLS 서버에 할당된 UDP 소켓으로 들어오는 모든 데이터는 원격 호스트에 따라 기존 또는 새 DTLS 세션에 매핑됩니다. 이러한 이유로 DTLS 서버를 만들려면 TLS 및 DTLS 클라이언트에 필요한 것보다 많은 추가 매개 변수가 필요합니다.

DTLS 서버 제어 블록, TLS ciphersuite 및 cipher scratchspace/metadata buffer 외에도 DTLS 서버에는 DTLS 세션을 유지하기 위한 버퍼와 수신 DTLS 레코드를 해독하는 데 사용되는 패킷 리어셈블리 버퍼가 필요합니다.

세션 버퍼 외에도 DTLS 서버에는 연결하는 TLS 클라이언트에서 TLS 서버를 식별하는 데 사용되는 문서인 *디지털 인증서* 와 인증서에 해당하는 *프라이빗 키*(일반적으로 RSA 암호화 알고리즘에 사용)가 필요합니다. International Telecommunications Union X.509 표준은 TLS/DTLS에서 사용하는 인증서 형식을 지정하며 X.509 디지털 인증서를 만들 수 있는 다양한 유틸리티가 있습니다.

NetX Secure DTLS의 경우 X.509 인증서는 DER(Distinguished Encoding Rules) 형식인 ASN.1을 사용하여 이진으로 인코딩해야 합니다. DER은 인증서에 사용되는 표준 TLS 네트워크 이진 형식입니다.

제공된 인증서와 연결된 프라이빗 키는 DER 인코딩 PKCS#1 형식이어야 합니다. 프라이빗 키는 디바이스에서만 사용되며 네트워크를 통해 전송되지 않습니다. 프라이빗 키는 TLS/DTLS 통신 보안에 중요하므로 안전하게 보관해야 합니다.

DTLS 서버 인증서를 초기화하려면 애플리케이션에서 ***nx_secure_x509_certificate_intialize*** 서비스를 사용하여 DER 인코딩 X.509 인증서 및 선택적 DER 인코딩 PKCS#1 RSA 프라이빗 키 데이터를 포함하는 버퍼에 대한 포인터를 제공해야 합니다. 이 서비스는 **NX_SECURE_X509_CERT** 구조를 TLS에서 사용할 적절한 인증서 데이터로 채우는 서비스입니다.

서버 인증서가 초기화되면 ***nx_secure_dtls_server_local_certificate_add*** 서비스를 사용하여 TLS 제어 블록에 인증서를 추가해야 합니다.

서버 인증서가 DTLS 서버 제어 블록에 추가되면 보안 DTLS 통신에 서버를 사용할 수 있습니다(위 예제 참조).

### <a name="initialization--dtls-client"></a>초기화 – DTLS 클라이언트

NetX Secure DTLS 클라이언트 모드는 UDP 소켓을 통해 원격 호스트로 나가는 단일 연결만 있으므로 DTLS 서버에 비해 작업이 간단합니다.

DTLS 클라이언트를 설정하려면 신뢰할 수 있는 CA(인증 기관)의 X.509 인코딩 디지털 인증서 컬렉션인 *신뢰할 수 있는 인증서 저장소* 가 필요합니다. 이러한 인증서는 DTLS 프로토콜이 "신뢰할 수 있는" 프로토콜로써 DTLS 서버 엔터티에서 제공하는 인증서를 NetX Secure DTLS 클라이언트 애플리케이션에 인증하기 위한 기본으로 사용됩니다.

신뢰할 수 있는 CA 인증서는 *자체 서명* 되는 경우도 있고 다른 CA에서 서명하는 경우도 있으며, 어떤 경우든 해당 인증서를 *ICA(중간 CA)* 라고 합니다. 일반적인 TLS/DTLS 애플리케이션에서 서버는 해당 서버 인증서와 함께 ICA 인증서를 제공하지만, 인증이 성공하기 위한 유일한 요구 사항은 발급자 체인(다른 인증서에 서명하는 데 사용되는 인증서)을 서버 인증서에서 신뢰할 수 있는 인증서 저장소의 신뢰할 수 있는 CA 인증서까지 추적할 수 있어야 한다는 것입니다. 이 체인을 *신뢰 체인* 또는 *인증서 체인* 이라고 합니다.

신뢰할 수 있는 CA 또는 ICA 인증서를 초기화하려면 애플리케이션에서 ***nx_secure_x509_certificate_intialize** _ 서비스를 사용하여 DER 인코딩 X.509 인증서를 포함하는 버퍼에 대한 포인터를 제공해야 합니다. 이 서비스는 _ *NX_SECURE_X509_CERT** 구조를 TLS에서 사용할 적절한 인증서 데이터로 채우는 서비스입니다.

또한 DTLS 클라이언트는 들어오는 서버 인증서를 할당할 공간(미리 공유한 키 모드를 사용하지 않는다고 가정) 및 패킷을 암호 해독할 DTLS 레코드로 어셈블하기 위한 버퍼가 필요합니다. 이러한 버퍼는 ***nx_secure_dtls_session_create*** 서비스에 매개 변수로 전달됩니다(자세한 내용은 API 참조에서 확인).

그러면 초기화된 신뢰할 수 있는 인증서가 ***nx_secure_dtls_session_trusted_certificate_add*** 서비스를 사용하여 만든 DTLS 세션 제어 블록에 추가됩니다. 인증서를 추가하지 못하면 DTLS 프로토콜이 원격 서버 호스트를 인증할 방법이 없기 때문에 DTLS 클라이언트 세션이 실패합니다.

신뢰할 수 있는 인증서 저장소를 만든 후에는 세션을 사용하여 보안 TLS 클라이언트 연결을 설정할 수 있습니다.

### <a name="application-interface-calls"></a>애플리케이션 인터페이스 호출

NetX Secure DTLS 애플리케이션은 일반적으로 ThreadX RTOS에서 실행되는 애플리케이션 스레드 내에서 함수 호출을 수행합니다. 일부 초기화, 특히 기본 네트워크 통신 프로토콜(예: UDP 및 IP)에 대한 초기화는 ***tx_application_define*** 에서 호출할 수 있습니다. 네트워크 통신 초기화에 대한 자세한 내용은 NetX/NetXDuo 사용자 가이드를 참조하세요.

DTLS는 프로세서 사용량이 많은 작업인 암호화 루틴을 많이 사용합니다. 일반적으로 이러한 작업은 호출 스레드의 컨텍스트 내에서 수행됩니다.

### <a name="dtls-session-start"></a>DTLS 세션 시작

DTLS가 작동하려면 기본 전송 계층 네트워크 프로토콜이 필요합니다. 일반적으로 사용되는 프로토콜은 TCP입니다. NetX Secure TLS 세션을 설정하려면 **NX_UDP_SOCKET** 을 만들어서 DTLS 클라이언트용 **_nx_secure_dtls_client_session_start_** 서비스에 전달해야 합니다.

DTLS 서버는 다르게 작동합니다. 들어오는 DTLS 클라이언트 요청에 사용되는 UDP 소켓은 NX_SECURE_DTLS_SERVER 제어 블록에 포함되어 있으며 로컬 UDP 포트를 매개 변수로 사용하는 ***nx_secure_dtls_server_create** _ 호출에서 초기화됩니다. 그 후 들어오는 요청을 처리하기 위해 _*_nx_secure_dtls_server_start_*_ 서비스를 사용하여 DTLS 서버를 시작합니다. 들어오는 모든 요청은 _nx_secure_dtls_server_create*에 제공(하나는 연결용, 하나는 알림 수신용으로 제공)되는 콜백 루틴에서 처리됩니다. 연결 알림이 수신될 때(DTLS에서 연결 알림 콜백을 호출) ***nx_secure_dtls_server_session_start**_ 를 호출하여 DTLS 세션 처리를 시작하는 것은 애플리케이션의 몫입니다. 또한 애플리케이션에서는 DTLS 핸드셰이크 완료 이후에 수신 알림 콜백이 호출될 때 _*_nx_secure_dtls_session_receive_**를 호출하여 들어오는 데이터를 처리해야 합니다. 자세한 내용은 위의 예제와 위에서 설명한 각 서비스의 API 참조에서 확인할 수 있습니다.

### <a name="dtls-packet-allocation"></a>DTLS 패킷 할당

NetX Secure DTLS는 DTLS 헤더의 공간이 올바르게 할당되도록 _*_nx_packet_allocate_*_ 서비스 대신 _ *_nx_secure_dtls_packet_allocate_** 서비스를 호출해야 한다는 점을 제외하고 NetX/NetXDuo TCP와 동일한 패킷 구조(***NX_PACKET** _)를 사용합니다.

### <a name="dtls-session-send"></a>DTLS 세션 보내기

TLS 세션이 시작되면 애플리케이션에서 ***nx_secure_dtls_session_send*** 서비스를 사용하여 데이터를 보낼 수 있습니다. 송신 서비스는 동일하게 ***nx_udp_socket_send** _ 서비스를 사용하며 전송되는 데이터, 대상 IP 주소 및 대상 UDP 포트를 포함하는 _ *_NX_PACKET_** 데이터 구조를 사용합니다.

> [!IMPORTANT]
> nx_secure_dtls_session_send를 사용하여 데이터를 보낼 때 세션을 즉시 새 주소 및 UDP 포트로 이동하는 메커니즘을 사용하지 않는 이상(일반적이지 않음) DTLS 세션을 설정할 때 사용한 IP 주소와 포트를 사용해야 합니다.

DTLS를 통해 전송되는 모든 데이터는 전송되기 전에 NX Secure DTLS 스택 및 구성된 암호화 루틴을 통해 암호화됩니다.

### <a name="dtls-session-receive"></a>DTLS 세션 받기

DTLS 세션이 시작되면 애플리케이션에서 ***nx_secure_Dtls_session_receive** _ 서비스를 사용하여 데이터 수신을 시작할 수 있습니다. DTLS 세션 보내기와 마찬가지로 이 서비스는 동일하게 _*_nx_udp_socket_receive_**를 사용하지만, 들어오는 데이터는 DTLS 스택에서 암호 해독되고 확인된 후 패킷 구조에 반환됩니다.

### <a name="tls-session-close"></a>TLS 세션 닫기

DTLS 세션이 완료되면 DTLS 클라이언트와 서버가 서로 CloseNotify 경고를 보내서 세션을 종료해야 합니다. 양쪽에서 경고를 수신하고 처리해야만 세션이 종료됩니다.

원격 호스트에서 CloseNotify 경고를 보내면 ***nx_secure_dtls_session_receive** _ 서비스는 경고를 처리하고, 해당 경고를 다시 원격 호스트로 보내고, _*_NX_SECURE_TLS_SESSION_CLOSED_** 값을 반환합니다. 세션이 종료되면 해당 DTLS 세션을 통해 데이터를 보내거나 받으려는 모든 시도가 실패합니다.

애플리케이션에서 TLS 세션을 닫으려면 ***nx_secure_dtls_session_end** _ 서비스를 호출해야 합니다. 그러면 이 서비스에서 CloseNotify 경고를 보내고 응답 CloseNotify를 처리합니다. 응답이 수신되지 않으면 DTLS 세션이 완전히 종료되지 않았으며 보안 위반 가능성이 있음을 알리는 _ *_NX_SECURE_TLS_SESSION_CLOSE_FAIL_** 오류 값이 반환됩니다.

### <a name="tlsdtls-alerts"></a>TLS/DTLS 경고

TLS/DTLS는 최대 보안을 제공하도록 설계되었으므로 프로토콜의 모든 이상 동작이 잠재적 보안 위반으로 간주됩니다. 이러한 이유로 모든 메시지 처리 또는 암호화/암호 해독 오류는 치명적인 오류로 간주되어 핸드셰이크 또는 세션이 즉시 종료됩니다.

로컬 애플리케이션에서 오류를 처리하는 것은 비교적 간단하지만, 원격 호스트는 상황을 올바르게 처리하고 추가로 발생할 수 있는 보안 위반을 방지하려면 오류가 발생한 사실을 알아야 합니다. 이러한 이유로 TLS/DTLS는 오류 발생 시 원격 호스트에 *경고* 메시지를 보냅니다.

경고는 다른 TLS/DTLS 메시지와 동일한 방식으로 처리되며, 공격자가 제공된 경고 유형에서 정보를 수집하지 못하도록 세션이 열린 동안 암호화됩니다. 핸드셰이크 중에 전송되는 경고는 잠재적 공격자가 얻을 수 있는 정보의 양을 제한하기 위해 그 범위가 제한됩니다.

TLS/DTLS 세션을 닫는 데 사용되는 CloseNotify 경고는 유일하게 심각하지 않은 경고입니다. CloseNotify는 경고로 간주되고 경고 메시지를 보내기는 하지만, 오류가 발생했음을 알리지 않는다는 점에서 다른 경고와는 다릅니다.

### <a name="tlsdtls-session-renegotiation-and-resumption"></a>TLS/DTLS 세션 다시 협상 및 다시 시작

TLS는 기존 TLS 세션의 컨텍스트 내에서 TLS 세션 매개 변수를 재협상하는 "다시 협상"이라는 개념을 지원합니다.

TLS 세션 *다시 시작* 은 세션 *다시 협상* 과 비슷한 점이 있지만 혼동해서는 안 됩니다. 세션 *다시 협상* 은 기존 TLS 세션 내에서 새 핸드셰이크를 시작하는 반면, 세션 *다시 시작* 은 TLS 핸드셰이크를 완전히 수행하지 않고 닫힌 TLS 세션을 다시 시작하며 전적으로 선택적 기능입니다.

NX Secure DTLS는 원격 호스트에서 들어오는 다시 협상 요청을 처리합니다. 세션 다시 시작을 지원하지 **않습니다**. 이러한 기능에 대한 자세한 설명은 NetX Secure TLS 사용자 가이드의 챕터 3에서 찾을 수 있습니다.

### <a name="protocol-layering"></a>프로토콜 계층화

TLS 프로토콜(및 그에 따른 DTLS)은 전송 계층(예: TCP 또는 UDP)과 애플리케이션 계층 간의 네트워킹 스택에 적합합니다. TLS는 경우에 따라 전송 계층 프로토콜(따라서 *전송 계층* 보안)로 간주되지만, 기본 네트워크 프로토콜과 관련하여 애플리케이션으로 작동하기 때문에 애플리케이션 계층으로 그룹화되는 경우도 있습니다.

TLS를 사용하려면 TCP와 같은 순서 및 무손실 전송을 지원하는 전송 계층 프로토콜이 필요합니다. 이러한 요구 사항 때문에 데이터그램 전송을 보장하지 않는 TLS는 UDP에서 실행할 수 없습니다. *DTLS* 는 TLS의 수정 버전으로, UDP와 같은 데이터그램 프로토콜을 통해 TLS를 보호해야 하는 애플리케이션에 사용됩니다.

![TLS 프로토콜 계층화의 다이어그램](media/image6.png)

**그림 4 - TCP/IP, UDP 및 TLS/DTLS 프로토콜 계층**

## <a name="network-communications-security-and-encryption"></a>네트워크 통신 보안 및 암호화

공용 네트워크와 인터넷을 통해 통신을 보호하는 것은 매우 중요한 토픽이자 수많은 서적, 기사 및 솔루션의 주제입니다. 이 토픽은 매우 복잡하지만, 의도한 대상만 정보에 액세스하거나 정보를 변경할 수 있도록 네트워크를 통해 정보 보내기라는 간단한 개념으로 정리할 수 있습니다. 이 개념은 다시 기밀성, 무결성 및 인증이라는 세 가지 중요한 개념으로 세분화됩니다. TLS/DTLS 프로토콜은 세 가지 영역 모두에 솔루션을 제공합니다.

암호화는 TLS 및 DTLS 프로토콜 내에서 기밀성, 무결성 및 인증을 제공하는 여러 가지 방법에 사용됩니다. 세선 또는 서버 인스턴스를 만들 때 TLS 또는 DTLS에 암호화를 제공해야 합니다. TLS는 암호화 자체가 아닌 암호화를 사용하기 위한 유연한 프레임워크를 제공하기 때문입니다. NetX Secure DTLS는 대부분의 애플리케이션에 필요한 암호화 루틴을 제공하므로 적절한 암호화를 찾기 위해 고생할 필요가 없습니다.

이러한 토픽에 대한 자세한 설명은 NetX Secure TLS 사용자 가이드의 챕터 3에서 찾을 수 있습니다.

## <a name="tls-and-dtls-extensions"></a>TLS 및 DTLS 확장

TLS(및 그에 따른 DTLS)는 특정 애플리케이션을 위한 추가 기능이 포함된 여러 확장을 제공합니다. 이러한 확장은 일반적으로 ClientHello 또는 ServerHello 메시지의 일부로 전송되며, 확장을 사용해야 한다고 원격 호스트에 알리거나 보안 TLS 세션을 설정하는 데 사용할 추가 세부 정보를 원격 호스트에 제공합니다.

NetX Secure DTLS는 NetX Secure TLS에 있는 모든 확장을 지원하며, 자세한 설명은 NetX Secure TLS 사용자 가이드 챕터 3에서 찾을 수 있습니다.

## <a name="authentication-methods"></a>인증 방법

TLS 및 DTLS는 안전하지 않은 네트워크를 통해 두 디바이스 간에 보안 연결을 설정할 수 있는 프레임워크를 제공하지만, 해당 연결의 반대쪽 끝에 있는 디바이스 ID를 알아야 한다는 문제가 있습니다. 원격 호스트의 ID를 인증하는 메커니즘이 없으면 공격자가 신뢰할 수 있는 디바이스를 손쉽게 속일 수 있습니다.

처음에는 IP 주소, 하드웨어 MAC 주소 또는 DNS를 사용하면 네트워크에서 호스트를 식별하는 데 비교적 높은 수준의 신뢰도를 제공하는 것처럼 보일 수 있지만, TCP/IP 기술의 특성과 주소를 쉽게 스푸핑할 수 있고 DNS 항목이 손상(예: DNS 캐시 손상을 통해)될 수 있다는 점을 고려할 때 TLS에는 사기성 ID를 차단하기 위한 추가 보호 계층이 필요합니다.

TLS에 이와 같은 추가 인증 계층을 제공할 수 있는 다양한 메커니즘이 있지만, 가장 일반적인 방법은 *디지털 인증서* 입니다. 기타 메커니즘으로는 PSK(미리 공유한 키) 및 암호 체계가 있습니다.

### <a name="digital-cerificates"></a>디지털 인증서

디지털 인증서는 TLS에서 원격 호스트를 인증하는 가장 일반적인 방법입니다. 기본적으로 디지털 인증서는 컴퓨터 네트워크 상의 디바이스에 대한 ID 정보를 제공하는 특정 형식을 포함하고 있는 문서입니다.

TLS는 일반적으로 International Telecommunication Union에서 개발한 표준인 X.509 형식을 사용하지만, 사용하려는 형식을 TLS 호스트에서 동의할 수 있다면 다른 형식의 인증서를 사용해도 됩니다. X.509는 디지털 문서를 작성하는 데 사용할 수 있는 다양한 인코딩 및 인증서의 형식을 정의합니다. TLS에 사용되는 대부분의 X.509 인증서는 다른 통신 표준의 변형인 ASN.1을 사용하여 인코딩됩니다. ASN.1에는 다양한 디지털 인코딩이 포함되어 있지만, TLS 인증서에 사용되는 가장 일반적인 인코딩은 DER(Distinguished Encoding Rules) 표준입니다. DER은 구문 분석을 쉽게 수행할 수 있도록 분명하게 설계된 ASN.1 BER(Basic Encoding Rules)의 간소화된 하위 세트입니다. 네트워크를 통해 TLS 인증서는 일반적으로 이진 DER로 인코딩되며, 이 형식은 NetX Secure에서 X.509 인증서에 요구하는 형식입니다.

DER 형식의 이진 인증서는 실제 TLS 프로토콜에 사용되지만 .pem, .crt, .p12 등의 파일 확장명을 사용하여 다양한 인코딩으로 생성하고 저장할 수 있습니다. 여러 제조업체의 다양한 애플리케이션에서 다양한 변형이 사용되지만, 일반적으로 널리 제공되는 도구를 사용하여 DER로 변환할 수 있습니다.

가장 일반적인 대체 인증서 인코딩은 PEM입니다. Privacy Enhanced Mail의 PEM 형식은 base-64로 인코딩된 DER 인코딩 버전으로, 인코딩 결과가 이메일 또는 웹 기반 프로토콜을 사용하여 쉽게 보낼 수 있는 인쇄 가능한 텍스트로 생성되기 때문에 자주 사용됩니다.

NetX Secure 애플리케이션의 인증서 생성은 일반적으로 이 설명서의 범위를 벗어나지만, OpenSSL 명령줄 도구([www.openssl.org](http://www.openssl.org))는 광범위하게 사용할 수 있으며 대부분의 형식을 변환할 수 있습니다.

애플리케이션에 따라 사용자 고유의 인증서를 생성할 수도 있고, 제조업체 또는 정부 기관에서 인증서를 제공할 수도 있고, 상용 인증 기관에서 인증서를 구매할 수도 있습니다.

NetX Secure 애플리케이션에서 디지털 인증서를 사용하려면 먼저 인증서를 이진 DER 형식으로 변환하고, 필요에 따라 연결된 프라이빗 키(예: RSA의 경우 "프라이빗 지수")를 이진 형식(일반적으로 PKCS#1 형식의 DER 인코딩 RSA 키)으로 변환해야 합니다. 변환이 완료되면 디바이스에 인증서 및 프라이빗 키를 로드해야 합니다. 선택 가능한 옵션으로는 플래시 기반 파일 시스템을 사용하거나, 데이터에서 C 배열을 생성하고(Linux의 "xxd" 같은 도구를 사용하여) 인증서와 키를 애플리케이션에 상수 데이터로 컴파일하는 방법이 있습니다.

인증서가 디바이스에 로드되면 DTLS API를 사용하여 인증서를 DTLS 세션 또는 서버와 연결할 수 있습니다.

NetX Secure DTLS에서 X.509 인증서를 사용하는 방법에 대한 자세한 내용과 예제는 NetX Secure TLS 사용자 가이드의 "NetX Secure로 X.509 인증서 가져오기" 섹션을 참조하세요.

자세한 내용은 API 참조에서 다음 DTLS 서비스를 확인하세요.

- nx_secure_x509_certificate_initialize
- nx_secure_dtls_session_local_certificate_add
- nx_secure_dtls_server_local_certificate_add
- nx_secure_dtls_session_local_certificate_remove
- nx_secure_dtls_server_local_certificate_remove
- nx_secure_dtls_session_trusted_certificate_add
- nx_secure_dtls_server_trusted_certificate_add
- nx_secure_dtls_session_trusted_certificate_remove
- nx_secure_dtls_server_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>TLS 클라이언트 인증서 세부 정보

일반적으로 DTLS 클라이언트를 구현할 때 로컬 인증서를 디바이스에 로드하지 않아도 됩니다. 로컬 인증서는 로컬 디바이스를 식별하는 인증서입니다. 특히 로컬 인증서는 TLS/DTLS 애플리케이션이 로드되는 디바이스의 ID 정보를 제공합니다. 클라이언트 인증서 인증을 사용하도록 설정하는 경우에는 예외지만, 일반적인 상황은 아닙니다.

DTLS 클라이언트를 사용하려면 신뢰할 수 있는 인증서를 하나 이상 로드해야 하며(필요한 경우 더 많이 로드할 수 있음) 원격 인증서를 할당할 공간이 필요합니다. 신뢰할 수 있는 인증서는 직접 또는 PKI(공개 키 인프라)를 통해 원격 디바이스의 신뢰와 인증을 위한 기반을 제공하는 인증서입니다. 신뢰 체인의 루트를 일반적으로 인증 기관 또는 CA 인증서라고 합니다. 원격 인증서는 TLS 핸드셰이크 중에 원격 호스트에서 보낸 인증서를 참조합니다. 원격 인증서는 해당 원격 호스트의 ID를 제공하며, 로컬 디바이스의 신뢰할 수 있는 인증서와 비교하여 인증됩니다.

신뢰할 수 있는 인증서를 추가하고 원격 인증서의 공간을 할당하는 방법에 대한 자세한 내용은 nx_secure_dtls_session_create 및 nx_secure_dtls_session_trusted_certificate_add 서비스의 TLS API 참조를 확인하세요.

### <a name="tlsdtls-server-certificate-specifics"></a>TLS/DTLS 서버 인증서 세부 정보

일반적으로 DTLS 서버를 구현할 때 "신뢰할 수 있는" 인증서를 디바이스에 로드하거나 원격 인증서를 할당할 필요가 없습니다. 클라이언트 인증서 인증을 사용하는 경우에는 예외입니다.

TLS 서버의 경우 TLS 핸드셰이크 중에 원격 클라이언트에 인증서를 제공하여 서버를 클라이언트에 인증할 수 있도록 "로컬"(또는 "ID") 인증서를 로드해야 합니다.

NetX TLS 서버 애플리케이션에 사용할 로컬 인증서를 로드하는 방법에 대한 자세한 내용은 nx_secure_dtls_server_local_certificate_add 및 nx_secure_dtls_server_local_certificate_remove 서비스의 API 참조에서 확인할 수 있습니다.


### <a name="pre-shared-keys-psk"></a>PSK(미리 공유한 키)

TLS에서 식별 인증을 제공하는 또 다른 메커니즘은 PSK(미리 공유한 키)라는 개념입니다. PSK ciphersuite를 사용하면 프로세서 사용량이 많은 공개 키 암호화 작업을 수행할 필요가 없으므로 리소스가 제한적인 임베디드 디바이스에 유용합니다. PSK는 TLS/DTLS 핸드셰이크의 인증서를 대체하며 TLS/DTLS 세션 키 생성을 위해 암호화된 Pre-Master Secret 대신 사용됩니다.

PSK ciphersuite는 TLS/DTLS 세션을 설정하려면 두 디바이스 모두에 공유 비밀이 있어야 한다는 점에서 제한적입니다. 즉, TLS PSK 연결이 아닌 다른 안전한 방법으로 해당 비밀을 디바이스에 로드해야 합니다. PSK는 TLS PSK 연결을 통해 업데이트할 수 있지만, 디바이스는 반드시 다른 메커니즘을 통해 로드된 PSK를 사용하여 시작해야 합니다. 예를 들어 출하 전에 공장에서 PSK를 사용하여 센서 디바이스와 게이트웨이 디바이스를 로드하거나, 표준 TLS 연결(인증서 포함)을 사용하여 PSK를 로드할 수 있습니다.

PSK ciphersuite는 RFC 4279에 설명된 여러 가지 형식으로 제공됩니다. 첫 번째 형식은 표준 TLS 핸드셰이크에서 인증서에 전송된 공개 키와 동일한 방식으로 사용되는 RSA 또는 Diffie-Hellman 키를 사용합니다. 리소스가 제한적인 환경에서 더 많이 사용되는 두 번째 형식은 세션 키(AES에서 사용할)를 직접 생성하는 데 사용되는 PSK를 사용하며, 비용이 많이 드는 RSA 또는 Diffie-Hellman 작업의 사용을 방지합니다.

NetX Secure는 애플리케이션에서 모든 공개 키 암호화 코드 및 메모리를 사용하지 않도록 두 번째 PSK ciphersuite 형식을 지원합니다. PSK 자체는 AES 키가 아니지만 실제 키가 생성되는 암호와 비슷한 것으로 간주할 수 있습니다. PSK 값에는 몇 가지 제한 사항이 있지만, 암호와 마찬가지로 값이 길수록 강력한 보안을 제공합니다.

NetX Secure 애플리케이션에서 PSK를 사용하려면 먼저 글로벌 매크로 **NX_SECURE_ENABLE_PSK_CIPHERSUITES** 를 정의해야 합니다. 이 작업은 일반적으로 컴파일러 설정을 통해 수행되지만 nx_secure_tls.h 헤더 파일에 정의를 배치할 수도 있습니다. 매크로가 정의되면 PSK ciphersuite 지원이 NetX Secure DTLS 애플리케이션으로 컴파일됩니다.

PSK 지원을 사용하도록 설정한 후에는 DTLS API를 사용하여 애플리케이션에 대한 PSK를 설정할 수 있습니다. 각 PSK에는 PSK 값(실제 비밀 "키" – 안전하게 보관해야 함), 특정 PSK를 식별하는 데 사용되는 "ID" 값, 그리고 TLS 서버에서 특정 PSK 값을 선택하는 데 사용하는 "ID 힌트"가 필요합니다.

PSK 자체는 네트워크 연결을 통해 전송되지 않으므로 임의의 이진 값일 수 있습니다. PSK의 최대 길이는 64바이트입니다.

ID 및 힌트는 UTF-8을 사용하여 서식이 지정된 인쇄 가능한 문자열이어야 합니다. ID 및 힌트 값의 최대 길이는 128바이트입니다.

ID 및 PSK는 서로 통신해야 하는 네트워크 상의 모든 디바이스에 로드되는 고유한 쌍을 형성합니다.

"힌트"는 PSK를 함수 또는 서비스별로 그룹화하는 애플리케이션 프로필을 정의하는 데 주로 사용됩니다. 이러한 값은 미리 합의해야 하며 애플리케이션에 따라 달라집니다. 예를 들어 PSK를 사용하도록 설정된 OpenSSL 명령줄 서버 애플리케이션은 TLS 핸드셰이크를 계속하려면 TLS 클라이언트에서 제공해야 하는 기본 문자열인 "Client_identity"를 사용합니다.

PSK에 대한 자세한 내용은 nx_secure_dtls_psk_add 및 nx_secure_dtls_server_psk_add 서비스에 대한 NetX Secure API 참조를 확인하세요.

## <a name="importing-x509-certificates-into-netx-secure"></a>NetX Secure로 X.509 인증서 가져오기

디지털 인증서는 인터넷에서 이루어지는 대부분의 TLS 연결에 필요합니다. 인증서는 일반적으로 *CA(인증 기관)* 라고 하는 신뢰할 수 있는 중개자를 사용하여 인터넷을 통해 이전에는 알 수 없었던 호스트를 인증하는 방법을 제공합니다. NetX Secure 디바이스를 상용 클라우드 서비스(예: Amazon Web Services)와 연결하려면 인증서를 디바이스에 로드하여 인증서를 애플리케이션으로 가져와야 합니다.

인증서와 함께 인증서와 연결된 *프라이빗 키* 가 필요할 수도 있습니다. 일부 애플리케이션(예: 클라이언트 인증서 인증을 사용하지 않는 경우 TLS 클라이언트)에서는 인증서 하나로 충분하지만, 인증서를 사용하여 디바이스를 식별하는 경우에는 프라이빗 키가 필요합니다. 프라이빗 키는 일반적으로 인증서를 만들 때 생성되고 별도의 파일에 저장되며, 이러한 파일은 종종 암호로 암호화됩니다.

NetX Secure 애플리케이션으로 인증서를 가져오는 방법에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드의 챕터 3을 참조하세요.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>NetX Secure TLS의 클라이언트 인증서 인증

X.509 인증서 인증을 사용하는 경우 TLS/DTLS 프로토콜을 사용하려면 DTLS 서버 인스턴스에서 식별용 인증서를 제공해야 하지만, 기본적으로 DTLS 클라이언트 인스턴스는 다른 형태의 인증(예: 사용자 이름/암호 조합)을 사용하여 인증용 인증서를 제공할 필요가 없습니다. 따라서 인터넷의 웹 사이트에서 가장 일반적으로 사용되는 TLS에 적합합니다. 예를 들어 온라인 소매점 사이트는 웹 브라우저를 사용하는 잠재 고객에게 서버가 합법적이라는 것을 증명해야 하지만 사용자는 로그인/암호를 사용하여 특정 계정에 액세스합니다.

그러나 기본 사례가 항상 적절한 것은 아니므로 TLS/DTLS는 상황에 따라 DTLS 서버 인스턴스가 원격 클라이언트에서 인증서를 요청하는 것을 허용합니다. 이 기능을 사용하면 DTLS 서버는 핸드셰이크 중에 CertificateRequest 메시지를 DTLS 클라이언트에 보냅니다. 클라이언트는 자체 인증서 및 해당 인증서와 연결된 일치하는 프라이빗 키를 소유하고 있음을 증명하는 암호화 토큰이 포함된 CertificateVerify 메시지로 응답해야 합니다. 확인이 실패하거나 인증서가 서버의 신뢰할 수 있는 인증서에 연결되지 않은 경우 TLS 핸드셰이크가 실패합니다.

TLS의 클라이언트 인증서 인증에 대한 두 가지 사례가 있는데, 다음 섹션에서 다룹니다.

### <a name="client-certificate-authentication-for-dtls-clients"></a>DTLS 클라이언트용 클라이언트 인증서 인증

DTLS 클라이언트는 클라이언트 인증을 위해 인증서를 요청하는 서버에 연결을 시도할 수 있습니다. 이 경우 클라이언트는 서버에 인증서를 제공하고 인증서와 일치하는 프라이빗 키가 서버에 있는지 확인해야 합니다. 그렇지 않으면 서버가 DTLS 핸드셰이크를 종료합니다.

NetX Secure DTLS에는 이 기능을 지원하는 특별한 구성이 없지만 애플리케이션에서 *nx_secure_tls_session_local_certificate_add* 서비스를 사용하여 TLS 클라이언트 인스턴스에 대한 로컬 식별 인증서를 제공해야 합니다. 애플리케이션에서 인증서를 제공하지 않지만 원격 서버에서 클라이언트 인증서 인증을 사용하고 인증서를 요청하는 경우에는 DTLS 핸드셰이크가 실패합니다. DTLS 핸드셰이크를 완료하려면 *nx_secure_dtls_session_local_certificate_add* 를 사용하여 DTLS 세션에 제공된 인증서를 원격 서버에서 인식해야 합니다.

### <a name="client-certificate-authentication-for-tls-servers"></a>TLS 서버용 클라이언트 인증서 인증

클라이언트 인증서 인증에 대한 DTLS 서버 사례는 선택 사항으로 제공되는 기능 때문에 DTLS 클라이언트 사례보다 약간 더 복잡합니다. 이 경우 TLS 서버는 원격 TLS 클라이언트에서 인증서를 구체적으로 요청한 다음, CertificateVerify 메시지를 처리하여 원격 클라이언트가 일치하는 프라이빗 키를 소유하고 있는지 확인해야 합니다. 그 후 서버에서는 클라이언트가 제공한 인증서를 신뢰할 수 있는 로컬 인증서 저장소의 인증서까지 추적할 수 있는지 확인해야 합니다.

NetX Secure TLS 서버 인스턴스에서 클라이언트 인증서 인증은 *nx_secure_dtls_server_x509_client_verify_configure* 및 *nx_secure_dtls_server_x509_client_verify_disable* 서비스를 통해 제어됩니다.

클라이언트 인증서 인증을 사용하도록 설정하려면 애플리케이션에서 DTLS 서버 세션 인스턴스를 사용하여 *nx_secure_dtls_server_x509_client_verify_configure* 를 호출한 후 *nx_secure_dtls_server_start* 를 호출해야 합니다. 확인하려면 *nx_secure_dtls_server_x509_client_verify_configure* 의 매개 변수로 제공되는 수신 클라이언트 인증서를 위한 공간을 할당해야 합니다 버퍼는 클라이언트에서 제공하는 인증서 체인의 최대 크기를 충분히 수용할 수 있는 크기에 *DTLS 서버 세션 수를 곱한 값* 이어야 합니다. 각 서버 세션에는 제공된 단일 버퍼에서 할당되는 공간이 필요합니다. 버퍼가 충분히 커야 합니다. 그렇지 않으면 제공된 클라이언트 인증서 체인이 너무 클 경우 오류가 발생합니다.

클라이언트 인증서 인증을 사용하면 DTLS 서버는 DTLS 핸드셰이크 중에 원격 DTLS 클라이언트에 인증서를 요청합니다. NetX Secure DTLS 서버에서는 X.509 발급자 체인을 따라 *nx_secure_dtls_server_trusted_certificate_add* 를 사용하여 만든 신뢰할 수 있는 인증서 저장소와 대조하여 클라이언트 인증서를 확인합니다. 원격 클라이언트는 ID 인증서를 신뢰할 수 있는 저장소의 인증서에 연결하는 체인을 제공해야 합니다. 그렇지 않으면 DTLS 핸드셰이크가 실패합니다. 또한 CertificateVerify 메시지 처리가 실패하면 DTLS 핸드셰이크도 실패합니다.

CertificateVerify 메서드에 사용되는 서명 메서드는 TLS 버전 1.0 및 TLS 버전 1.1용으로 수정되었으며, NetX Secure DTLS의 기반이 되는 TLS 버전 1.2의 TLS 서버에서 지정합니다. DTLS 1.2의 경우 지원되는 서명 메서드는 일반적으로 암호화 메서드 테이블에 제공된 관련 메서드를 따르지만, 일반적으로 SHA-256과 함께 RSA를 사용합니다. 암호화 메서드로 TLS를 초기화하는 방법에 대한 자세한 내용은 "NetX Secure TLS의 암호화" 섹션을 참조하세요.

## <a name="cryptography-in-netx-secure-tls"></a>NetX Secure TLS의 암호화

TLS는 암호화를 사용하여 네트워크 통신을 보호할 수 있는 프로토콜을 정의합니다. 따라서 실제 암호화를 TLS 사용자에게 매우 광범위하게 사용할 수 있습니다. 이 사양에서는 단일 ciphersuite를 구현하기만 하면 됩니다. TLS 1.2의 경우에는 해당 ciphersuite는 TLS_RSA_WITH_AES_128_CBC_SHA입니다. 즉, 공개 키 작업에는 RSA를 사용하고, 세션 암호화에는 128비트 키를 사용하여 AES를 CBC 모드로 사용하고, 메시지 인증 해시에는 SHA-1을 사용합니다.

TLS 1.2 규격을 준수하는 NetX Secure는 기본적으로 필수 TLS_RSA_WITH_AES_128_CBC_SHA ciphersuite를 사용하지만, 하드웨어 기능과 기타 고려 사항으로 인해 각 암호화 메서드에 대해 가능한 구현 수를 고려하여 NetX Secure는 사용자가 TLS에서 사용할 암호화 메서드를 지정할 수 있는 일반 암호화 API를 제공합니다.

> [!NOTE]
> 일반 암호화 API 메커니즘을 사용하면 사용자가 고유의 ciphersuite를 구현할 수 있지만, TLS ciphersuite 및 확장에 익숙한 고급 사용자만 이 메커니즘을 사용하는 것이 좋습니다. 자체 ciphersuite를 지원하려면 Express 논리 담당자에게 문의하세요.

DTLS에 대한 암호화 메서드를 구성하는 방법에 대한 자세한 내용은 NetX Secure TLS 사용자 가이드의 챕터 3을 참조하세요. TLS 및 DTLS에 동일한 프로세스가 적용됩니다.
