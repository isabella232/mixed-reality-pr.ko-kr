---
title: Maquette 설치
description: VSCode에서 Maquette를 설치 하 고 구성 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, 프로토타입, 혼합 현실, 가상 현실, VR, MR, 피드백, 피드백 허브, 버그
ms.openlocfilehash: c31f461adbe553a5c10e7acfff3037ea0c2b65caf2bbe63bfc234e067a6369e8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214776"
---
# <a name="installing-maquette"></a>Maquette 설치

<!-- TODO(Harrison): Need consolidated logo with text. -->
![로고 ](../images/MaquetteIcon.png) MaquetteScript 설치

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
MaquetteScript 개발은 기본적으로 VSCode 내에서 수행 됩니다. MaquetteScript는 파일에 포함 된 스크립트 `.mqjs` 와 특수 VSCode 확장 인터페이스를 통해 실행할 수 있습니다. 확장 인터페이스를 사용 하도록 설정 하기 위해 VSCode와 Maquette를 통합 하는 것은 MaquetteScript VSCode 확장을 사용 하 여 수행 됩니다.

## <a name="installing-the-vscode-extension"></a>VSCode 확장 설치

* [Vscode](https://code.visualstudio.com)를 다운로드 하 여 설치 합니다. 

Maquette javascript 확장은 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript)에 있습니다.

* [확장에 대 한 설치 절차](vscode:extension/ms-maquette.vscode-maquette-javascript)를 실행 합니다.

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a>스크립팅 사용

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

시험판 동안 스크립팅을 사용할 수 있도록 설정 하려면 다음을 수행 합니다.

* Maquette의 사용자 문서 디렉터리에 이름으로 파일을 저장 `scripting.enabled` `~/Documents/Maquette/Settings` 합니다.

설치 후에는 보안상의 이유로 스크립팅을 기본적으로 사용 하지 않도록 설정 됩니다.

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* 스크립트를 실행할 수 있도록 설정 하려면 보조 창이 나 json 설정 파일의 주 탭에서 설정 합니다.

![VS Code에서 스크립팅 사용](images/IntroductionEnableScripting.png)


