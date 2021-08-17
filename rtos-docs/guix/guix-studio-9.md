---
title: GUIX Studio 명령줄
description: GUIX Studio는 Studio 생성 출력 파일을 업데이트하는 데 필요한 빌드 파이프라인에 유용한 명령줄 호출을 제공합니다.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bd88054d974aabea30b50c6f4e10b4c5df9994db03ab84a4a5d8f9394b4d6ed8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785399"
---
# <a name="chapter-9-guix-studio-command-line"></a>9장 - GUIX Studio 명령줄

GUIX Studio는 명령줄 호출을 지원합니다. 이 호출은 Studio 생성 출력 파일을 업데이트하는 데 필요한 빌드 파이프라인에 유용합니다.

## <a name="command-line-usage"></a>명령줄 사용법

**사용법:** guix_studio \[OPTION\] \[ARGUMENT\]

*.gxp* 프로젝트를 엽니다.

Studio 프로젝트를 열고 원하는 출력 파일을 생성합니다.


**예:**

`guix_studio demo.gxp`  
"demo.gxp" 프로젝트 열기


`guix_studio.exe –p demo.gxp`  
"demo.gxp" 프로젝트 열기


`guix_studio.exe –n –p demo.gxp`  
demo.gxp 프로젝트의 모든 출력 파일을 생성합니다.

`guix_studio.exe –n –r –p demo.gxp`  
demo.gxp 프로젝트의 리소스 파일을 생성합니다.


## <a name="command-line-options"></a>명령줄 옵션

```C
***-n --nogui***  
```

"nogui" 옵션입니다. GUIX Studio에 창 UI 인터페이스를 시작하지 않고 실행하도록 지시합니다.

```C
***-o pathname***  
***--log***  
```

로그 옵션, 로그 파일을 지정합니다.

```C
***-b***  
***--binary***  
```

이진 리소스 옵션입니다. C 파일이 아닌 이진 리소스 파일을 생성합니다.

```C
***-d display1, display2***  
***--display***  
```

표시 이름 옵션입니다. 이 옵션을 사용할 경우 지정된 표시 이름만 생성된 리소스 또는 사양 파일에 포함됩니다. 이 옵션을 사용하지 않으면 모든 표시가 포함됩니다.

```C
***-t theme1, theme2***  
***--theme***  
```

테마 이름 옵션입니다. 이 옵션을 사용할 경우 지정된 테마 이름만 생성된 리소스 또는 사양 파일에 포함됩니다. 이 옵션을 사용하지 않으면 모든 테마가 포함됩니다.

```C
***-l langage1, language2***  
***--language***  
```

언어 이름 옵션입니다. 이 옵션을 사용할 경우 지정된 언어 이름이 생성된 리소스 또는 사양 파일에 포함됩니다. 그렇지 않으면 모든 언어 이름이 포함됩니다.

```C
***-r [filename]***  
***--resource***  
```

리소스 옵션은 Studio에서 이전에 지정된 표시, 테마 및 언어에 대한 리소스 파일을 생성하도록 지정합니다.

```C
***-s [filename]***  
***--specification***  
```

사양 옵션은 Studio에서 지정된 표시, 테마 및 언어에 대한 사양 파일을 생성하도록 지정합니다.

```C
***-p project_pathname***  
***--project***  
```

프로젝트 경로 이름 옵션은 로드할 예제 프로젝트를 지정합니다.

```C
***-i [pathname]***  
***--import***  
```

xliff 또는 csv 서식 파일에서 문자열을 가져옵니다.

***--big_endian***  
big-endian 형식으로 리소스 데이터를 생성합니다.
