---
title: 1장 - 개요
author: philmea
description: 이 문서는 Azure RTOS ThreadX 모듈을 대략적으로 설명합니다.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0c9698086468d7bb41c33ebe9fa9d1ebb61b5f1f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810314"
---
# <a name="chapter-1-overview"></a>1장: 개요

ThreadX 모듈 구성 요소는 애플리케이션의 상주 부분과 별도로 제작된 모듈을 애플리케이션이 동적으로 로드하는 데 필요한 인프라를 제공합니다. 애플리케이션 코드 크기가 사용 가능한 메모리를 초과하는 경우에 특히 유용합니다. 핵심 이미지를 배포한 후 새 기능을 추가해야 하는 경우에도 도움이 될 수 있습니다. 또한 부분적인 펌웨어 업데이트가 필요한 경우 동적 로드 모듈을 사용할 수 있습니다.

로드된 모듈의 메모리 보호는 모듈 프리앰블에 지정된 속성을 기준으로 하는 선택 사항입니다. 메모리 보호를 지정하면 모듈의 모든 스레드가 모듈의 코드 및 데이터 메모리에만 액세스할 수 있도록 프로세서의 메모리 관리 하드웨어가 구성됩니다. 불필요한 메모리 액세스나 실행으로 인해 메모리 오류가 발생하고 잘못된 모듈 스레드가 종료됩니다. 애플리케이션이 메모리 오류 알림 콜백을 등록하는 경우 메모리 오류를 애플리케이션에 경고하기 위해 호출할 수도 있습니다.

ThreadX 모듈 구성 요소는 모듈을 로드할 수 있는 메모리 영역을 제공하기 위해 애플리케이션에 의존합니다. 각 모듈의 명령 영역을 원래 위치에서 실행하거나 실행을 위해 RAM 모듈 메모리 영역에 복사할 수 있습니다. 모든 경우에서 모듈 데이터 메모리 요구 사항은 모듈 메모리 영역에서 할당됩니다.

동시에 로드할 수 있는 모듈 수에는 제한이 없지만(사용 가능한 메모리의 양과는 별개임) 상주하는 모듈 관리자 코드의 복사본은 하나 뿐입니다. 그림 1에서는 모듈 관리자와 모듈 자체의 관계를 보여 줍니다.

![모듈 및 모듈 관리자 관계](media/image2.png)

**그림 1** 모듈 및 모듈 관리자

각 모듈에는 자체 메모리 영역이 있어야 하며 이 메모리 영역은 애플리케이션이 정의해야 합니다. 모듈 및 모듈 관리자는 모듈에서 요청하는 ThreadX 서비스에 해당하는 미리 정의된 요청 ID를 통해 소프트웨어 디스패치 기능을 사용하여 상호 작용합니다. 또한 이 모듈은 필요한 스택 크기, 우선 순위, 모듈 ID, 콜백 스레드 스택 크기/우선 순위 등을 비롯한 단일 스레드 진입점을 제공하는 데 필요합니다. 이 정보는 각 모듈의 프리앰블에 정의되어 있습니다.

모듈 관리자는 초기 모듈 스레드를 만들고 실행을 시작하는 일을 담당합니다. 모듈의 초기 스레드가 실행되면 모듈 관리자는 모듈에서 모든 ThreadX API 요청을 필드로 표시합니다. 모듈에는 모듈 내에서 추가 스레드를 만드는 기능을 포함하여 ThreadX API에 대한 모든 액세스 권한이 있습니다.  
  
모듈 소스 코드 명명 규칙은 간단합니다. 모든 모듈 관리자 원본 파일은 ***txm_module_manager_\**** 로 명명되고 해당 모듈과만 관련된 모든 파일은 이름의 "**_manager_ *_" 부분이 생략됩니다. 주 포함 파일 _* _txm_module.h_** 는 관리자 및 모듈 소스 코드에서 공유됩니다.