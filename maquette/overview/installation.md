---
title: Maquette 설치
description: VSCode에서 Maquette를 설치 하 고 구성 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, 프로토타입, 혼합 현실, 가상 현실, VR, MR, 피드백, 피드백 허브, 버그
ms.openlocfilehash: ba0064326e83f04b056c0baa2f86f718e41bedfe
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935428"
---
# <a name="installing-maquette"></a><span data-ttu-id="e94fd-104">Maquette 설치</span><span class="sxs-lookup"><span data-stu-id="e94fd-104">Installing Maquette</span></span>

<!-- TODO(Harrison): Need consolidated logo with text. -->
<span data-ttu-id="e94fd-105">![로고 ](../images/MaquetteIcon.png) MaquetteScript 설치</span><span class="sxs-lookup"><span data-stu-id="e94fd-105">![Logo](../images/MaquetteIcon.png) MaquetteScript Installation</span></span>

<!-- TODO(Stefan): Need more explanation on the .mqjs route for running MaquetteScript. -->
<span data-ttu-id="e94fd-106">MaquetteScript 개발은 기본적으로 VSCode 내에서 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e94fd-106">MaquetteScript development is primarily done within VSCode.</span></span> <span data-ttu-id="e94fd-107">MaquetteScript는 파일에 포함 된 스크립트 `.mqjs` 와 특수 VSCode 확장 인터페이스를 통해 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e94fd-107">MaquetteScript can run from script contained in `.mqjs` files and also via a special VSCode extension interface.</span></span> <span data-ttu-id="e94fd-108">확장 인터페이스를 사용 하도록 설정 하기 위해 VSCode와 Maquette를 통합 하는 것은 MaquetteScript VSCode 확장을 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e94fd-108">Integration between VSCode and Maquette to enable the extension interface is accomplished with a MaquetteScript VSCode extension.</span></span>

## <a name="installing-the-vscode-extension"></a><span data-ttu-id="e94fd-109">VSCode 확장 설치</span><span class="sxs-lookup"><span data-stu-id="e94fd-109">Installing the VSCode Extension</span></span>

* <span data-ttu-id="e94fd-110">[Vscode](https://code.visualstudio.com)를 다운로드 하 여 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e94fd-110">Download and install [VSCode](https://code.visualstudio.com).</span></span> 

<span data-ttu-id="e94fd-111">Maquette javascript 확장은 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript)에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e94fd-111">The Maquette javascript extension is in [the Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-maquette.vscode-maquette-javascript).</span></span>

* <span data-ttu-id="e94fd-112">[확장에 대 한 설치 절차](vscode:extension/ms-maquette.vscode-maquette-javascript)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e94fd-112">Run the [installation procedure for the extension](vscode:extension/ms-maquette.vscode-maquette-javascript).</span></span>

<!-- TODO(Stefan): Are there plans to have the extension update manually in the future? If so, when will this be available? -->
`NOTE: The VSCode extension does not automatically update currently and will need to be updated manually.`

## <a name="enabling-scripting"></a><span data-ttu-id="e94fd-113">스크립팅 사용</span><span class="sxs-lookup"><span data-stu-id="e94fd-113">Enabling Scripting</span></span>

<!-- TODO(Stefan): Is scripting still a pre-release only option? If and when will it be available for current users? -->
`PRE-RELEASE NOTE: Javascript is already embedded within Maquette but requires additional steps and settings to access and enable. Scripting is currently only available for pre-release testing and is not a visible option for current users. Ensure at least version 2020.3.0.0.1315 but preferably use latest version.`

<span data-ttu-id="e94fd-114">시험판 동안 스크립팅을 사용할 수 있도록 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e94fd-114">To make scripting accessible during pre-release:</span></span>

* <span data-ttu-id="e94fd-115">Maquette의 사용자 문서 디렉터리에 이름으로 파일을 저장 `scripting.enabled` `~/Documents/Maquette/Settings` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e94fd-115">Put a file with the name `scripting.enabled` in the Users Documents directory for Maquette in: `~/Documents/Maquette/Settings`.</span></span>

<span data-ttu-id="e94fd-116">설치 후에는 보안상의 이유로 스크립팅을 기본적으로 사용 하지 않도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e94fd-116">After installation, scripting will be disabled by default for security reasons.</span></span>

<!-- TODO(Stefan): Missing a first step where the user has to select the {} tab in VSCode, shown in the screenshot, to access the scripting enabled setting.
                   - Also missing instructions and screenshot on how to turn on scripting in the JSON settings file.
 -->
* <span data-ttu-id="e94fd-117">스크립트를 실행할 수 있도록 설정 하려면 보조 창이 나 json 설정 파일의 주 탭에서 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e94fd-117">To enable execution of script, turn it ON in the main tab of the companion window or in the json settings file.</span></span>

![VS Code에서 스크립팅 사용](images/IntroductionEnableScripting.png)


