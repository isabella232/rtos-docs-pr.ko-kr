---
title: Microsoft Azure RTOS란?
description: Azure RTOS는 MCU(마이크로 컨트롤러 단위)로 구동되는 IoT 및 에지 디바이스의 RTOS(실시간 운영 체제)입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: d9bd7cfda454e73e9bd270b86616780ab7ceab1a76160a66cf49a9ef82efae05
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792403"
---
# <a name="what-is-microsoft-azure-rtos"></a>Microsoft Azure RTOS란?

Azure RTOS는 MCU(마이크로 컨트롤러 단위)로 구동되는 IoT(사물 인터넷) 및 에지 디바이스의 RTOS(실시간 운영 체제)입니다. Azure RTOS는 대부분의 매우 제한된 디바이스(배터리 전원을 공급하고 64KB 미만의 플래시 메모리)를 지원하도록 설계되었습니다.

Azure RTOS는 다양한 안전 표준에 대해 사전 인증을 받았습니다. 여기에는 IEC 61508 SIL 4, IEC 62304 클래스 C 및 ISO 26262 ASIL D 인증이 포함됩니다.

Azure RTOS는 TLS 및 DTLS를 통해 IPsec 및 소켓 계층 보안을 통해 전체 IP 계층 보안을 비롯하여 EAL4+ Common Criteria 보안 인증 환경을 제공합니다. 소프트웨어 암호화 라이브러리는 FIPS 140-2 인증을 달성했습니다. 또한 하드웨어 암호화 기능, ThreadX 모듈을 통한 메모리 보호 및 ARM의 TrustZone ARMv8-M 보안 기능에 대한 지원을 활용합니다.

## <a name="components-of-azure-rtos"></a>Azure RTOS의 구성 요소

Azure RTOS 플랫폼은 Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo 및 Azure RTOS USBX를 비롯한 런타임 솔루션의 컬렉션입니다.

### <a name="azure-rtos-threadx"></a>Azure RTOS ThreadX

Azure [RTOS ThreadX](threadx/overview-threadx.md)는 깊게 포함된 애플리케이션용으로 특별히 디자인된 고급 RTOS(실시간 운영 체제)입니다. Azure RTOS ThreadX에서 제공하는 여러 이점 중 하나는 고급 예약 기능, 메시지 전달, 인터럽트 관리 및 메시징 서비스입니다. Azure RTOS ThreadX에는 picokernel 아키텍처, preemption-threshold 스케줄링, event-chaining 및 다양한 시스템 서비스 집합을 포함한 많은 고급 기능이 있습니다.

### <a name="azure-rtos-filex"></a>Azure RTOS FileX

Azure [RTOS FileX](filex/overview-filex.md)는 고성능 FAT 호환 파일 시스템입니다. Azure RTOS ThreadX와 완전히 통합되고 지원되는 모든 프로세서에서 사용할 수 있습니다. Azure RTOS FileX는 Azure RTOS ThreadX와 마찬가지로 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 파일 작업이 필요한 오늘날의 긴밀하게 포함된 애플리케이션에 적합합니다. Azure RTOS FileX는 Azure RTOS LevelX를 통해 RAM 디스크, USBX, SD 카드 및 NAND/NOR 플래시 메모리를 비롯한 대부분의 물리적 미디어를 지원합니다.

### <a name="azure-rtos-guix"></a>Azure RTOS GUIX

Azure [RTOS GUIX](guix/overview-guix.md)는 포함된 시스템 개발자의 요구 사항에 맞게 제작된 전문적인 품질의 그래픽 사용자 인터페이스 패키지입니다. 다른 대안과 달리 Azure RTOS GUIX는 그래픽 출력을 지원할 수 있는 거의 모든 하드웨어 구성으로 작고 빠르고 쉽게 이식할 수 있습니다. 또한 Azure RTOS GUIX는 애플리케이션 수준 사용자 인터페이스 개발을 위한 뛰어난 시각적 효과와 직관적이고 강력한 API를 제공합니다.

### <a name="azure-rtos-netx"></a>Azure RTOS NetX

Azure [RTOS NetX](netx/overview-netx.md)는 TCP/IP 프로토콜 표준의 고성능 구현입니다. Azure RTOS ThreadX와 완전히 통합되고 지원되는 모든 프로세서에서 사용할 수 있습니다. Azure RTOS NetX에는 고유한 Piconet 아키텍처가 있습니다. 제로 복사 API와 함께 사용하면 네트워크에 연결해야 하는 오늘날의 긴밀하게 포함된 애플리케이션에 완벽하게 부합합니다.

### <a name="azure-rtos-netx-duo"></a>Azure RTOS NetX Duo

Azure [RTOS NetX](netx-duo/overview-netx-duo.md) Duo는 긴밀하게 포함된 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 고급, 산업용 TCP/IP 네트워크 스택입니다. Azure RTOS NetX Duo는 이중 IPv4 및 IPv6 네트워크 스택이고, NetX는 원래 IPv4 네트워크 스택이며, 기본적으로 Azure RTOS NetX Duo의 하위 집합입니다.

### <a name="azure-rtos-usbx"></a>Azure RTOS USBX

Azure [RTOS USBX](usbx/overview-usbx.md)는 고성능의 USB 호스트, 디바이스 및 OTG(On-The-Go) 포함 스택입니다. ThreadX와 완전히 통합되고 지원되는 모든 Azure RTOS ThreadX 프로세서에서 사용할 수 있습니다. Azure RTOS USBX는 Azure RTOS ThreadX와 마찬가지로 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 USB 디바이스와 인터페이스가 필요한 긴밀하게 포함된 애플리케이션에 적합합니다.

### <a name="windows-tools"></a>Windows 도구

Azure [RTOS GUIX Studio](guix/about-guix-studio.md)는 전체 GUI 애플리케이션 디자인 환경을 제공하여 애플리케이션의 GUI에서 모든 그래픽 요소를 만들고 유지 관리하는 작업을 용이하게 합니다. Azure RTOS GUIX Studio는 대상에서 컴파일되고 실행할 준비가 된 Azure RTOS GUIX 라이브러리와 호환되는 C 코드를 자동으로 생성합니다.

Azure [RTOS TraceX](tracex/overview-tracex.md)는 포함된 시스템 개발자에게 실시간 시스템 이벤트에 대한 그래픽 보기를 제공하고, 실시간 시스템의 동작을 시각화하고 더 잘 이해할 수 있도록 하는 호스트 기반 분석 도구입니다.

## <a name="the-azure-rtos-advantage"></a>Azure RTOS의 이점
Azure RTOS는 다른 실시간 운영 체제에 비해 다음과 같은 이점을 제공합니다.

### <a name="most-deployed-rtos"></a>가장 많이 배포된 RTOS

선도적인 M2M 시장 인텔리전스 회사인 VDC Research에 따르면 Azure RTOS는 전 세계적으로 62억 개 이상의 배포를 보유하고 있습니다. Azure RTOS의 인기는 신뢰도, 품질, 크기, 성능, 고급 기능, 사용 편의성 및 전반적인 출시 시간 이점에 대한 증거입니다.

> *"우리는 회사 창립 이래 무선 및 IoT 시장에서 THREADX의 성장 궤적을 따라왔으며, THREADX의 광범위한 업계 채택에 점점 더 깊은 인상을 받았습니다."* – Chris Rommel, 부사장, VDC Research

### <a name="intuitive-and-consistent-api-design"></a>직관적이고 일관된 API 디자인

* 직관적이고 일관된 API.
* 명사-동사 명명 규칙.
* 모든 API에는 ThreadX의 경우 *tx_* , FileX의 경우 *fx_* 와 같은 선행 접두사가 있어, 해당 접두사가 속한 Azure RTOS 구성 요소를 쉽게 식별할 수 있습니다.
* API 전반에 걸쳐 기능적 일관성을 유지합니다. 예를 들어 일시 중단된 모든 API 함수는 동일한 방식으로 작동하는 선택적 시간 제한이 있습니다.
* 많은 API를 애플리케이션 ISR에서 직접 사용할 수 있습니다.
- 미디어 및 파일 작업에 대한 선택적 사용자 알림 콜백.
* 이벤트 구동 프로그래밍 모델(API).

### <a name="high-efficiency"></a>높은 효율성

- 작은 코드 공간.
- 사용된 서비스를 기반으로 하는 확장 가능한 코드 공간.
- IEC 61508 SIL 4, IEC 62304 클래스 C, ISO 26262 ASIL D 및 EN 50128 SW-SIL4에 따라 TUV 및 UL에 의해 사전 인증됨.
- 고속 실행. Azure RTOS는 속도를 위해 설계되었으며 가능한 가장 빠른 성능을 달성하는 데 도움이 되도록 내부 함수 호출 계층화를 최소화합니다.

### <a name="fastest-time-to-market"></a>가장 빠른 출시 시간

Azure RTOS는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리가 쉽습니다. 결과적으로 Azure RTOS는 Broadcom, Gainspan 등의 많은 SoC를 포함하여 임베디드 IoT 디바이스에 가장 많이 사용되는 실시간 운영 체제 중 하나입니다. 일관적인 출시 시간 이점은 다음을 기반으로 합니다.

* 전체 소스 코드 가용성.
* 사용하기 쉬운 API.
* 포괄적인 고급 기능 세트.
* 품질 설명서.

### <a name="one-simple-license"></a>하나의 간단한 라이선스

사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.

### <a name="full-highest-quality-source-code"></a>최고 품질의 전체 소스 코드

오랜 시간에 걸쳐 Azure RTOS 소스 코드는 품질 및 이해 용이성의 기준을 정립했습니다. 또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.

### <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>TUV 및 UL을 비롯한 여러 안전 표준의 사전 인증

Azure RTOS는 안전이 매우 중요한 시스템에서의 사용을 위해 IEC-61508 SIL 4, IEC-62304 SW 안전 클래스 C, ISO 26262 ASIL D 및 EN 50128에 따라 SGS-TUV Saar 인증을 받았습니다. 이 인증은 "전기, 전자 및 프로그램 가능한 전자 안전 관련 시스템의 기능적 안전"에 대한 최고 수준의 IEC-61508, IEC-62304, ISO 26262 및 EN 50128의 안전 무결성 등급에 따라, Azure RTOS를 보안 관련 소프트웨어의 개발에 사용할 수 있음을 확인합니다. 독일 SGS-Group 및 TUV Saarland의 공동 벤처인 SGS-TUV Saar는 세계적으로 안전 관련 시스템용 포함 소프트웨어를 테스트, 감사, 확인 및 검증하는 최고 권위의 독립 기업으로 자리했습니다. 산업 보안 표준 IEC 61508과, 거기에서 파생된 모든 표준(IEC-62304, ISO 26262 및 EN 50128 포함)은 전기, 전자 및 프로그래밍 가능한 전자 안전 관련 의료 장비, 공정 제어 시스템, 산업용 기계, 자동차, 철도 제어 시스템의 기능 안전을 보장하는 데 사용됩니다.

:::image type="content" source="media/partener-logo-sgs-tuv-saar.png" alt-text="인증":::

UL은 Azure RTOS가 프로그래밍 가능한 구성 요소에서의 소프트웨어에 대한 UL 60730-1 부칙 H, CSA E60730-1 부칙 H, IEC 60730-1 부칙 H, UL 60335-1 부칙 R, IEC 60335-1 부칙 R 및 UL 1998 안전 표준의 규정을 준수한다고 인정했습니다. UL은 공공 에너지 도입, 첨단 지속 가능성 기술, 재생 에너지, 나노 기술 등을 망라하는 안전 솔루션 혁신 분야에서 백년이 넘는 전문 기술을 갖춘 글로벌 독립 안전 과학 기업입니다.

:::image type="content" source="media/cru-logo-certification.png" alt-text="CRU UL 인증":::

TUV 및 UL 인증과 관련한 아티팩트(인증서, 안전 매뉴얼, 테스트 보고서 등)는 판매 가능합니다.

애플리케이션에 추가 인증이 필요한 경우, 실제 하드웨어 플랫폼을 사용한 다양한 표준에 대한 턴키 방식의 인증을 제공하고 애플리케이션 코드까지도 다루는 인증 서비스를 Microsoft를 통해 사용할 수 있습니다. 인증 서비스에 대한 자세한 내용은 Microsoft에 문의하세요.

### <a name="eal4-common-criteria-security-certification"></a>EAL4+ Common Criteria 보안 인증

Azure RTOS는 EAL4+ Common Criteria 보안 인증을 달성했습니다. TOE(평가 대상)는 Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS 및 Azure RTOS NetX MQTT를 포함합니다. 이는 깊이 내장된 센서, 디바이스, 에지 라우터 및 게이트웨이에 필요한 가장 일반적인 IoT 프로토콜을 나타냅니다.

:::image type="content" source="media/eal-logo-certification.png" alt-text="EAL 인증":::

Microsoft Azure RTOS SC 보안 인증에 사용되는 IT 보안 평가 시설은 Brightsight BV이고 인증 기관은 SERTIT입니다.

### <a name="fips-140-2-validated"></a>FIPS 140-2 유효성 검사

Azure RTOS 암호화 라이브러리는 암호화 모듈에 대한 요구 사항을 지정하는 소프트웨어용 FIPS 140-2(Federal Information Processing Standard 140-2) 인증을 획득했습니다. FIPS 140-2에 따르면 암호화 기반 보안을 사용하는 모든 연방 정부 기관 및 부서는 암호화 강도 및 기능과 관련된 특정 표준을 충족해야 합니다. 이러한 암호화 기반 보안 표준은 캐나다 및 유럽 연합에서도 인정되고 있습니다.

Azure RTOS 암호화 라이브러리에 사용되는 정보 보안 평가 랩은 atsec이었으며 인증 기관은 [NIST(National Institute of Standards and Technology)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394)입니다.

### <a name="supports-most-popular-architectures"></a>대부분의 주요 아키텍처 지원

가장 널리 사용되는 32/64비트 마이크로프로세서의 Azure RTOS는 즉시 사용 가능하며 다음과 같은 고급 아키텍처를 포함하여 즉시 완전히 테스트되고 완벽하게 지원됩니다.

- **아날로그 디바이스**: SHARC, Blackfin, CM4xx

- **Andes Core**: RISC-V

- **Ambiqmicro**: Apollo MCU

- **ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64비트/R4/R5, TrustZone ARMv8-M

- **Cadence**: Xtensa, Diamond

- **CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi

- **Cypress**: RISC-V

- **EnSilica**: eSi-RISC

- **Infineon**: XMC1000, XMC4000, TriCore

- **Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10

- **Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

- **Microsemi**: RISC-V

- **NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

- **Renesas**: SH, HS, V850, RX, RZ, Synergy

- **Silicon Labs**: EFM32

- **Synopsys**: ARC 600, 700, ARC EM, ARC HS

- **ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

- **Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

- **Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class

- **Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*나열된 모든 타이밍 및 크기 수치는 예상치이며, 개발 플랫폼에 따라 다를 수 있습니다.*

## <a name="in-the-context-of-azure-iot"></a>Azure IoT의 컨텍스트에서

Azure IoT에 직접 연결하거나 Azure IoT Edge를 통해 간접적으로 연결하는 것 외에도 Azure RTOS를 Azure Sphere 디바이스에서 사용할 수도 있습니다. Azure RTOS와 Azure Sphere의 조합은 하나의 디바이스에서 최상의 실시간 처리 및 보안을 제공합니다.
