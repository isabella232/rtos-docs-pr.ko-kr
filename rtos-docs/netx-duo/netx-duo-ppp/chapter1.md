---
title: 1장 - Azure RTOS NetX Duo PPP(지점 간 프로토콜) 소개
description: 이 장에서는 Azure RTOS NetX Duo PPP(지점 간 프로토콜)를 소개합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56343d563833f30ca0d48f594b547f37fa264b8961a7cd75b0786aac4791d065
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797214"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-point-to-point-protocol-ppp"></a>1장 - Azure RTOS NetX Duo PPP(지점 간 프로토콜) 소개

일반적으로 NetX 애플리케이션은 이더넷을 통해 실제 물리적 네트워크에 연결합니다. 이는 빠르고 효율적인 네트워크 액세스를 제공합니다. 그러나 애플리케이션에 이더넷 액세스 권한이 없는 경우가 있습니다. 이러한 경우 애플리케이션은 다른 네트워크 구성원에 직접 연결된 직렬 인터페이스를 통해 네트워크에 계속 연결할 수 있습니다. 이러한 연결을 관리하는 데 사용되는 가장 일반적인 소프트웨어 프로토콜은 PPP(지점 간 프로토콜)입니다.

직렬 통신은 비교적 간단하지만 PPP는 다소 복잡합니다. PPP는 실제로 LCP(연결 제어 프로토콜), IPCP(인터넷 프로토콜 제어 프로토콜), PAP(암호 인증 프로토콜) 및 CHAP(Challenge-Handshake 인증 프로토콜)와 같은 여러 프로토콜로 구성됩니다. LCP는 PPP의 주요 프로토콜입니다. 여기에서 링크의 기본 구성 요소가 피어 투 피어 방식으로 동적으로 협상됩니다. 링크의 기본 특성을 성공적으로 협상한 후에는 PAP 및/또는 CHAP를 사용하여 연결된 피어가 유효한지 확인합니다. 두 피어가 모두 유효하면 IPCP를 사용하여 피어에서 사용하는 IP 주소를 협상합니다. IPCP가 완료되면 PPP는 IP 패킷을 보내고 받을 수 있습니다.

NetX는 PPP를 주로 디바이스 드라이버로 봅니다. *nx_ppp_driver* 함수는 NetX IP 생성 함수 *nx_ip_create* 에 제공됩니다. 그렇지 않으면 NetX는 PPP에 대한 직접적인 정보를 가지고 있지 않습니다.

## <a name="ppp-serial-communication"></a>PPP 직렬 통신

NetX PPP 패키지를 사용하려면 애플리케이션이 직렬 통신 드라이버를 제공해야 합니다. 드라이버는 8비트 문자를 지원해야 하며 소프트웨어 흐름 제어를 사용할 수도 있습니다. 드라이버를 초기화하는 것은 애플리케이션의 책임입니다. 이는 PPP 인스턴스를 만들기 전에 수행해야 합니다.

PPP 패킷을 보내려면 직렬 드라이버 출력 바이트 루틴을 PPP에 제공해야 합니다(*nx_ppp_create* 함수에 지정됨). 이 직렬 드라이버 바이트 출력 루틴은 전체 PPP 패킷을 전송하기 위해 반복적으로 호출됩니다. 출력을 버퍼링하는 것은 직렬 드라이버의 책임입니다. 수신 쪽에서 애플리케이션의 직렬 드라이버는 새 바이트가 도착할 때마다 PPP *nx_ppp_byte_receive* 함수를 호출해야 합니다. 일반적으로 이 작업은 ISR(Interrupt Service Routine)의 컨텍스트 내에서 수행됩니다. *nx_ppp_byte_receive* 함수는 들어오는 바이트를 순환 버퍼에 배치하고 PPP 수신 스레드에 해당 상태를 알립니다.

## <a name="ppp-over-ethernet-communication"></a>이더넷 통신을 통한 PPP

NetX PPP는 이더넷을 통해 PPP 메시지를 전송할 수도 있습니다. 이 경우 NetX PPP 패키지는 이더넷 드라이버를 제공하기 위해 애플리케이션이 필요합니다.

이더넷을 통해 PPP 패킷을 전송하려면 출력 루틴이 PPP에 제공되어야 합니다(*nx_ppp_packet_send_set* 함수에 지정됨). 이 출력 루틴은 전체 PPP 패킷을 전송하기 위해 반복적으로 호출됩니다. 수신 쪽에서 애플리케이션의 수신자는 새 패킷이 도착할 때마다 PPP *nx_ppp_packet_receive* 함수를 호출해야 합니다.

## <a name="ppp-packet"></a>PPP 패킷

PPP는 모든 PPP 프로토콜 제어와 사용자 데이터를 캡슐화하기 위해 AHDLC 프레이밍(HDLC의 하위 집합)을 활용합니다. AHDLC 프레임은 다음과 같습니다.

|**플래그**|**Addr**|**Ctrl**|**정보**|**CRC**|**플래그**|
|--------|--------|--------|---------------|-------|--------|
|7E |FF|03|[0-1502바이트]|2바이트| 7E|

각각의 모든 PPP 프레임에는 이 전체적인 모양이 있습니다. 정보 필드의 처음 2바이트에는 PPP 프로토콜 형식이 포함되어 있습니다. 유효한 값은 다음과 같이 정의됩니다.

- C021: LCP
- 8021: IPCP
- C023: PAP
- C223: CHAP
- 0021: IP 데이터 패킷

0x0021 프로토콜 형식이 있는 경우 IP 패킷은 즉시 따라옵니다. 그렇지 않고 다른 프로토콜 중 하나가 있으면 다음 바이트가 특정 프로토콜에 해당합니다.

고유한 0x7E 시작/종료 프레임 표식을 보장하고 소프트웨어 흐름 제어를 지원하기 위해 AHDLC는 이스케이프 시퀀스를 사용하여 다양한 바이트 값을 나타냅니다. 0x7D 값은 다음 문자가 인코딩되도록 지정하는데, 이는 기본적으로 0x20과 배타적 OR로 처리된 원래 문자입니다. 예를 들어, 헤더의 Ctrl 필드에 대한 0x03 값은 2바이트 시퀀스인 7D 23으로 표현됩니다. 기본적으로 0x20보다 작은 값은 정보 필드에 있는 0x7E 및 0x7D 값과 함께 이스케이프 시퀀스로 변환됩니다. 이스케이프 시퀀스는 CRC 필드에도 적용됩니다.

## <a name="link-control-protocol-lcp"></a>LCP(연결 제어 프로토콜)

LCP는 기본 PPP 프로토콜이며 첫 번째로 실행할 프로토콜입니다. LCP는 사용할 MRU(최대 수신 단위) 및 인증 프로토콜(PAP, CHAP 또는 없음)을 비롯한 다양한 PPP 매개 변수를 협상합니다. LCP의 양쪽 모두가 PPP 매개 변수에 동의하면 인증 프로토콜(있는 경우)이 실행되기 시작합니다.

## <a name="password-authentication-protocol-pap"></a>PAP(암호 인증 프로토콜)

PAP는 연결의 한쪽에서 제공되는 이름 및 암호를 사용하는 비교적 간단한 프로토콜입니다(LCP에서 협상됨). 그런 다음, 다른 쪽에서 이 정보를 확인합니다. 올바른 경우, 승인 메시지가 보낸 사람에게 반환되고 PPP는 IPCP 상태 시스템으로 진행할 수 있습니다. 그렇지 않고 이름이나 암호가 잘못된 경우 연결이 거부됩니다.

>[!NOTE]
> 인터페이스 양쪽 모두에서 PAP를 요청할 수 있지만 일반적으로 PAP는 한 방향에서만 사용됩니다.

## <a name="challenge-handshake-authentication-protocol-chap"></a>CHAP(Challenge Handshake 인증 프로토콜)

CHAP는 PAP보다 더 복잡한 인증 프로토콜입니다. CHAP 인증자는 해당 피어에 이름과 값을 제공합니다. 그러면 피어는 제공된 이름을 사용하여 두 엔터티 간의 공유된 "비밀"을 찾습니다. 그런 다음, ID, 값 및 "비밀"에 대해 계산이 수행됩니다. 이 계산 결과는 응답에서 반환됩니다. 올바른 경우, PPP는 IPCP 상태 시스템으로 진행할 수 있습니다. 그렇지 않고 결과가 잘못된 경우 연결이 거부됩니다.

CHAP의 또 다른 흥미로운 측면은 연결이 설정된 후 임의의 간격으로 발생할 수 있다는 점입니다. 이는 연결이 인증된 후에 하이재킹되는 것을 방지하는 데 사용됩니다. 이러한 임의 시간 중 하나에서 챌린지에 실패하면 연결이 즉시 종료됩니다.

>[!NOTE]
> 인터페이스 양쪽 모두에서 CHAP를 요청할 수 있지만 일반적으로 CHAP는 한 방향에서만 사용됩니다.

## <a name="internet-protocol-control-protocol-ipcp"></a>IPCP(인터넷 프로토콜 제어 프로토콜)

IPCP는 NetX IP 데이터 전송에 PPP 통신을 사용할 수 있기 전에 실행할 마지막 프로토콜입니다. 이 프로토콜의 주요 목적은 한 피어가 다른 피어에게 해당 IP 주소를 알리는 것입니다. IP 주소가 설정되면 NetX IP 데이터 전송이 활성화됩니다.

## <a name="data-transfer"></a>데이터 전송

앞에서 언급했듯이 NetX IP 데이터 패킷은 프로토콜 ID가 0x0021인 PPP 프레임에 있습니다. 수신된 모든 데이터 패킷은 하나 이상의 NX_PACKET 구조에 배치되고 NetX 수신 처리로 전송됩니다. 전송 시 NetX 패킷 내용은 AHDLC 프레임에 배치되어 전송됩니다.

## <a name="ppp-rfcs"></a>PPP RFC

NetX PPP는 RFC1332, RFC1334, RFC1661, RFC1994 및 관련 RFC와 호환됩니다.