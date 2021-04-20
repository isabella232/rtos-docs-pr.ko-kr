---
title: 2장 - Azure RTOS FileX 설치 및 사용
description: 이 장에서는 다음을 포함하여 Azure RTOS FileX에 대한 소개와 설치 조건, 절차 및 사용에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6703b10d8e0895984bb92d74d5dff809dca1a7f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810326"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-filex"></a>2장 - Azure RTOS FileX 설치 및 사용

이 장에서는 Azure RTOS FileX에 대한 소개와 설치 조건, 절차 및 사용에 대해 설명합니다. 

## <a name="host-considerations"></a>호스트 고려 사항

### <a name="computer-type"></a>컴퓨터 유형

임베디드 개발은 일반적으로 Windows 또는 Linux(Unix) 호스트 컴퓨터에서 수행됩니다. 애플리케이션이 호스트에서 컴파일, 링크 및 배치된 후 실행할 수 있도록 대상 하드웨어에 다운로드됩니다.

### <a name="download-interfaces"></a>인터페이스 다운로드

일반적으로 대상 다운로드는 개발 도구의 디버거 내에서 수행됩니다. 다운로드 후 디버거는 대상 실행 제어(이동, 중지, 중단점 등)뿐만 아니라 메모리 및 프로세서 레지스터에 대한 액세스를 제공해야 합니다.

### <a name="debugging-tools"></a>디버깅 도구

대부분의 개발 도구 디버거는 JTAG(IEEE 1149.1) 및 BDM(백그라운드 디버그 모드)과 같은 OCD(온칩 디버그) 연결을 통해 대상 하드웨어와 통신합니다. 디버거는 ICE(회로 내 에뮬레이션) 연결을 통해 대상 하드웨어와 통신하기도 합니다. OCD 및 ICE 연결 모두 대상 상주 소프트웨어에 대한 침입이 최소화된 강력한 솔루션을 제공합니다.

### <a name="required-hard-disk-space"></a>최소 하드 디스크 공간

FileX의 소스 코드는 ASCII 형식으로 제공되며 호스트 컴퓨터의 하드 디스크에 약 500KB의 공간이 필요합니다.

## <a name="target-considerations"></a>대상 고려 사항

FileX를 사용하려면 대상에 6 ~ 30KB의 ROM(읽기 전용 메모리)이 있어야 합니다. 또한 FileX 글로벌 데이터 구조에 대상의 100KB RAM(Random Access Memory)이 추가로 필요합니다. 또한 열려 있는 각 미디어에는 하나의 섹터(일반적으로 512바이트)의 데이터를 저장하는 RAM 외에도 제어 블록에 1.5KB의 RAM이 필요합니다.

날짜/시간 스탬프가 제대로 작동하려면 FileX에서 ThreadX 타이머 기능에 의존합니다. 이는 FileX를 초기화하는 동안 FileX 관련 타이머를 만들어 구현합니다. 또한 FileX는 다중 스레드 보호 및 I/O 일시 중단에 대해 ThreadX 세마포를 사용합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS FileX는 <https://github.com/azure-rtos/filex/>에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다.

다음은 리포지토리에 있는 몇 가지 중요한 파일 목록입니다.

- ***fx_api.h***: 이 C 헤더 파일에는 모든 시스템 이큐에이트, 데이터 구조 및 서비스 프로토타입이 포함됩니다.
- ***fx_port.h***: 이 C 헤더 파일에는 모든 개발 도구 관련 데이터 정의 및 구조가 포함됩니다.
- ***demo_filex.c***: 이 C 파일에는 작은 데모 애플리케이션이 포함됩니다.
- ***fx.a(또는 fx.lib)***: FileX C 라이브러리의 이진 버전입니다. 표준 패키지로 배포됩니다.

> [!IMPORTANT]
> *모든 파일 이름은 소문자로 되어 있습니다. 이 명명 규칙을 사용하면 명령을 Linux(Unix) 개발 플랫폼으로 좀 더 쉽게 변환할 수 있습니다.*

## <a name="filex-installation"></a>FileX 설치

FileX는 GitHub 리포지토리를 로컬 컴퓨터에 복제하여 설치됩니다. 다음은 PC에서 FileX 리포지토리의 복제본을 만들기 위한 일반적인 구문입니다.

```c
    git clone https://github.com/azure-rtos/filex
```

또는 GitHub 기본 페이지의 다운로드 단추를 사용하여 리포지토리의 복사본을 다운로드할 수 있습니다.

또한 온라인 리포지토리의 프런트 페이지에서 FileX 라이브러리를 빌드하기 위한 지침을 찾을 수 있습니다.

> [!IMPORTANT]
> 애플리케이션 소프트웨어는 FileX 라이브러리 파일(일반적으로 ***fx.a** _ 또는 _*_fx.lib_*_ 라고 함*)_에 액세스해야 하며 C에는 **fx_api. h** 및 **fx_port.h** 파일이 포함됩니다. 이렇게 하려면 개발 도구에 대한 적절한 경로를 설정하거나 해당 파일을 애플리케이션 개발 영역으로 복사합니다.

## <a name="using-filex"></a>FileX 사용

FileX는 쉽게 사용할 수 있습니다. 기본적으로 컴파일하는 동안 애플리케이션 코드가 ***fx_api.h** _를 포함하고 FileX 런타임 라이브러리 _*_tx.a_*_(또는 _*_tx.lib_*_)와 연결해야 합니다. 물론 ThreadX 파일, 즉 _*_tx_api.h_*_ 및 _*_tx.a_*_(또는 _*_tx.lib_*_)_*도 필요합니다.

> [!IMPORTANT]
> FileX를 독립 실행형 모드에서 사용하는 경우(**FX_STANDALONE_ENABLE** 을 정의해야 함) ThreadX 파일/라이브러리가 필요하지 않습니다.

ThreadX를 이미 사용하고 있다고 가정하면 FileX 애플리케이션을 빌드하는 데 필요한 네 가지 단계가 있습니다.

1. FileX 서비스 또는 데이터 구조를 사용하는 모든 애플리케이션 파일에 ***fx_api.h*** 파일을 포함합니다.
1. _ *_tx_application_define_** 함수 또는 애플리케이션 스레드에서 ***fx_system_initialize** _를 호출하여 FileX 시스템을 초기화합니다.

    > [!IMPORTANT]
    > FileX를 독립 실행형 모드에서 사용하는 경우 ***fx_system_initialize*** 를 애플리케이션 코드에서 직접 호출해야 합니다.

1. ***fx_media_open*** 에 대한 호출을 하나 이상 추가하여 FileX 미디어를 설정합니다. 애플리케이션 스레드의 컨텍스트에서 이 호출을 수행해야 합니다.

    > [!IMPORTANT]
    > ***fx_media_open** 호출에는 하나의 섹터에 대한 데이터를 저장하는 데 충분한 RAM이 필요합니다.*

1. 애플리케이션 소스를 컴파일하고 FileX 및 ThreadX 런타임 라이브러리, ***fx.a** _(또는 _*_fx.lib_*_) 및 _*_tx.a_*_(또는 _*_tx.lib_**)와 연결합니다. 결과 이미지를 대상으로 다운로드하여 실행할 수 있습니다.

## <a name="troubleshooting"></a>문제 해결

각 FileX 포트는 데모 애플리케이션과 함께 제공됩니다. 항상 대상 하드웨어 또는 특정 데모 환경에서 데모 시스템을 먼저 실행하는 것이 좋습니다.

데모 시스템이 작동하지 않는 경우 다음 작업을 수행하여 문제 범위를 좁힙니다.

1. 데모가 어느 정도 실행되고 있는지 확인합니다.
1. 스택 크기를 늘립니다(데모보다는 실제 애플리케이션 코드에서 더 중요함).
1. 32KB 기본 RAM 디스크 크기를 위한 충분한 RAM이 있는지 확인합니다. 기본 시스템은 훨씬 더 작은 RAM으로 작동합니다. 그러나 더 많은 RAM 디스크를 사용하는 경우 메모리가 충분하지 않으면 문제가 발생합니다.
1. 최근 변경 내용을 일시적으로 무시하여 문제가 사라지거나 달라지는지 확인합니다. 이러한 정보는 Microsoft 지원 엔지니어에게 유용합니다. "고객 지원 센터"에 설명된 절차에 따라 문제 해결 단계에서 수집한 정보를 보냅니다.

## <a name="configuration-options"></a>구성 옵션

FileX를 사용하여 FileX 라이브러리 및 애플리케이션을 빌드할 때 몇 가지 구성 옵션이 있습니다. 아래 옵션은 애플리케이션 소스, 명령줄 또는 ***fx_user.h*** 포함 파일 내에서 정의할 수 있습니다.

> [!IMPORTANT]
> ***fx_user.h** 에 정의된 옵션은 애플리케이션 및 ThreadX 라이브러리가 정의된 **_FX_INCLUDE_USER_DEFINE_FILE_*_로 빌드하는 경우에만 적용됩니다._ 독립 실행형 모드에서 FileX를 사용하는 경우(** FX_STANDALONE_ENABLE**을 정의해야 함), ThreadX 파일/라이브러리가 필요하지 않습니다.

다음 목록은 각 구성 옵션에 대해 자세히 설명합니다.

|정의|의미|
|----------    |-----------|
|FX_MAX_LAST_NAME_LEN        |이 값은 전체 경로 이름을 포함하는 최대 파일 이름 길이를 정의합니다. 기본적으로 이 값은 256입니다.|
|FX_DONT_UPDATE_OPEN_FILES    |정의된 경우, FileX는 이미 열려 있는 파일을 업데이트하지 않습니다.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |정의된 경우, 파일 검색 캐시 최적화를 사용하지 않습니다.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |정의된 경우, 파일 검색 캐시 최적화를 사용하지 않습니다.|
|FX_DISABLE_DIRECT_DATA_READ_CACHE_FILL |정의된 경우, 캐시의 직접 읽기 섹터 업데이트가 사용하지 않도록 설정됩니다.|
|FX_MEDIA_STATISTICS_DISABLE |정의된 경우, 미디어 통계 수집이 사용하지 않도록 설정됩니다.|
|FX_SINGLE_OPEN_LEGACY |정의된 경우, 동일한 파일에 대해 레거시 단일 오픈 논리를 사용하도록 설정합니다.|
|FX_RENAME_PATH_INHERIT    |정의된 경우, 이름 바꾸기는 경로 정보를 상속합니다.|
|FX_DISABLE_ERROR_CHECKING    |기본 FileX 오류 검사 API를 제거하고 성능이 향상되고(30% 정도) 코드 크기가 더 작아집니다.|
|FX_MAX_LONG_NAME_LEN    |FileX에 대한 최대 파일 이름 크기를 지정합니다. 기본값은 256이지만 명령줄 정의를 사용하여 이 값을 재정의할 수 있습니다. 올바른 값의 범위는 13에서 256 사이입니다.|
|FX_MAX_SECTOR_CACHE|FileX에서 캐시할 수 있는 최대 논리 섹터 수를 지정합니다. 캐시할 수 있는 실제 섹터 수는 이 상수와 fx_media_open에서 제공되는 메모리 양에 맞출 수 있는 섹터 수입니다. 기본값은 256입니다. 모든 값은 2의 거듭제곱이어야 합니다.|
|FX_FAT_MAP_SIZE    |FAT 업데이트 맵에 표시할 수 있는 섹터 수를 지정합니다. 기본값은 256이지만 명령줄 정의를 사용하여 이 값을 재정의할 수 있습니다. 값이 클수록 보조 FAT 섹터의 불필요한 업데이트를 줄이는 데 도움이 됩니다.|
|FX_MAX_FAT_CACHE    |내부 FAT 캐시의 항목 수를 지정합니다. 기본값은 16이지만 명령줄 정의를 사용하여 재정의할 수 있습니다. 모든 값은 2의 거듭제곱이어야 합니다.|
|FX_FAULT_TOLERANT    |정의된 경우, FileX는 모든 시스템 섹터(부팅, FAT 및 디렉터리 섹터)의 쓰기 요청을 미디어의 드라이버에 즉시 전달합니다. 이로 인해 성능이 저하될 수 있지만 손실된 클러스터에 대한 손상을 제한하는 데 도움이 됩니다. 이 기능을 사용하도록 설정해도 FileX 내결함성 모듈이 자동으로 사용하도록 설정되지는 않습니다.|
|FX_FAULT_TOLERANT_DATA    |정의된 경우, FileX는 모든 파일 데이터 쓰기 요청을 미디어의 드라이버에 즉시 전달합니다. 이로 인해 성능이 저하될 수 있지만 손실된 파일 데이터를 제한하는 데 도움이 됩니다. 이 기능을 사용하도록 설정한다고 해서 ***FX_ENABLE_FAULT_TOLERANT*** 를 정의하여 사용하도록 설정되는 FileX 내결함성 모듈이 자동으로 사용하도록 설정되지는 않습니다.|
|FX_NO_LOCAL_PATH|FileX에서 로컬 경로 논리를 제거하여 더 작은 코드 크기를 생성합니다.|
|FX_NO_TIMER|FileX 시스템 시간 및 날짜를 업데이트하는 ThreadX 타이머 설정을 제거합니다. 이렇게 하면 기본 시간 및 날짜가 모든 파일 작업에 배치됩니다.|
|FX_UPDATE_RATE_IN_SECONDS    |FileX에서 시스템 시간을 조정하는 속도를 지정합니다. 기본적으로 값은 10이며 FileX 시스템 시간이 10초마다 업데이트되도록 지정합니다.|
|FX_ENABLE_EXFAT| 정의된 경우, exFAT 파일 시스템을 처리하는 논리는 FileX에서 사용하도록 설정됩니다. 기본적으로 이 기호는 정의되어 있지 않습니다.| 
|FX_UPDATE_RATE_IN_TICKS| 기본 ThreadX 타이머 빈도를 제외하고 ***FX_UPDATE_RATE_IN_SECONDS***(위 참조)와 동일한 속도로 지정합니다. 기본값은 1000(10ms ThreadX 타이머 요율 및 10초 간격으로 가정)입니다.|
|FX_SINGLE_THREAD|FileX 원본에서 ThreadX 보호 논리를 제거합니다. FileX를 하나의 스레드에서만 사용하거나 ThreadX 없이 FileX를 사용하는 경우에 사용해야 합니다.|
|FX_DRIVER_USE_64BIT_LBA|정의된 경우, I/O 드라이버에서 64비트 섹터 주소를 사용하도록 설정합니다. 기본적으로 이 옵션은 정의되어 있지 않습니다.|
|FX_ENABLE_FAULT_TOLERANT| 정의된 경우, FileX 내결함성 모듈을 사용하도록 설정합니다. 내결함성을 사용하도록 설정하면 ***FX_FAULT_TOLERANT** _ 및 _*_FX_FAULT_TOLERANT_DATA_** 기호가 자동으로 정의됩니다. 기본적으로 이 옵션은 정의되어 있지 않습니다.|
|FX_FAULT_TOLERANT_BOOT_INDEX|내결함성 로그에 대한 클러스터가 있는 부팅 섹터의 바이트 오프셋을 정의합니다. 기본적으로 이 값은 116입니다. 이 필드에는 4바이트가 사용됩니다. 116~119 바이트는 FAT 12/16/32/exFAT 사양에서 예약된 것으로 표시되기 때문에 선택됩니다.|
|FX_FAULT_TOLERANT_MINIMAL_CLUSTER|이 기호는 사용되지 않습니다. FileX 내결함성이 더 이상 사용되지 않습니다.|
|FX_STANDALONE_ENABLE|정의된 경우, Azure RTOS 없이 독립 실행형 모드에서 FileX를 사용하도록 설정할 수 있습니다. 기본적으로 이 기호는 정의되어 있지 않습니다.|

> [!IMPORTANT]
> **FX_STANDALONE_ENABLE** 이 정의된 경우 로컬 경로 논리와 ThreadX 타이머 설치는 사용하지 않습니다.

## <a name="filex-version-id"></a>FileX 버전 ID

FileX의 현재 버전은 런타임 중 사용자 및 애플리케이션 모두에 제공됩니다. 프로그래머는 **fx_port.h** 파일을 조사하여 FileX 버전을 가져올 수 있습니다. 또한 이 파일에는 해당 포트의 버전 기록도 포함됩니다. 애플리케이션 소프트웨어는 전체 문자열 **_ _fx_version_id_** 를 검사하여 FileX 버전을 가져올 수 있습니다.
