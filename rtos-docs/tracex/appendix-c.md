---
title: 부록 C - DOS 명령줄 유틸리티
description: 유틸리티 하위 디렉터리 아래의 Azure RTOS TraceX 설치에는 세 개의 DOS 명령줄 유틸리티가 있습니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 1a89f8be7e21e416659b904f0ec5b2a3a8f666cdb9a861786e652a38564db48f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791553"
---
# <a name="appendix-c---dos-command-line-utilities"></a>부록 C - DOS 명령줄 유틸리티

***유틸리티*** 하위 디렉터리 아래의 TraceX 설치에는 세 개의 DOS 명령줄 유틸리티가 있습니다.

제공되는 유틸리티는 다음과 같습니다.

| **유틸리티**                              | **용도**                               | **명령줄 정의** |
| -------------------------------- | ----------------------------------------- | ---------------------------- |
| **ea2tracex.exe**                | GHS 도구 converted_file이 있는 original_file 연결에서 ThreadX에 의해 생성된 추적 파일 ea2tracex를 TraceX 추적 파일 형식으로 변환합니다. GHS 도구용 ThreadX는 비 GHS 도구용 ThreadX와 다른 추적 형식을 생성하므로 이 변환 유틸리티가 필요합니다. | ``` > eatracex original_file converted_file <cr> ``` | 
**hex2tracex.exe** | ThreadX에서 생성되었지만 Intel HEX 형식의 개발 도구에서 덤프된 추적 파일을 이진 TraceX 추적 파일 형식으로 변환합니다. TraceX V5 이상에서는 HEX 파일을 변환하지 않고 열 수 있습니다. | ``` hex2tracex hex_file converted_file <cr> ``` | 
**mot2tracex.exe** | ThreadX에서 생성되었지만 Motorola S-Record 형식의 개발 도구에서 덤프된 추적 파일을 이진 TraceX 추적 파일 형식으로 변환합니다. TraceX V5 이상에서는 S-Record 파일을 변환하지 않고 열 수 있습니다. | ``` > mot2tracex mot_file converted_file <cr> ```|