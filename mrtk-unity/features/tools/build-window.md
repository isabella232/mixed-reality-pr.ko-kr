---
title: 빌드 창
description: Unity용 MRTK의 빌드 창 사용에 대한 설명서입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 빌드, 빌드 창, 도구
ms.openlocfilehash: b0b2bb1d06a561f5f647d01145fe88f562c53017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176153"
---
# <a name="build-window"></a><span data-ttu-id="72fe7-104">빌드 창</span><span class="sxs-lookup"><span data-stu-id="72fe7-104">Build window</span></span>
![빌드 & 배포 흐름](images/MRTK_BuildWindow0.png)

<span data-ttu-id="72fe7-106">MRTK의 빌드 창을 사용하면 MRTK-Unity 프로젝트를 쉽게 빌드하고 & 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fe7-106">MRTK's build window make it easy to build & deploy your MRTK-Unity projects.</span></span> <span data-ttu-id="72fe7-107">한 번의 단추 클릭으로 Unity 프로젝트를 빌드하고 Visual Studio 솔루션을 생성할 수 있습니다(. SLN), UWP 앱 패키지(. APPX)를 입력하고 디바이스에 앱 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="72fe7-107">With a single button click, you can build Unity project and generate Visual Studio solution(.SLN), UWP App package(.APPX), and install the app package on the device.</span></span> 


## <a name="unity-build-options"></a><span data-ttu-id="72fe7-108">Unity 빌드 옵션</span><span class="sxs-lookup"><span data-stu-id="72fe7-108">Unity Build Options</span></span>
![빌드 창 - Unity 빌드 옵션 1](images/MRTK_BuildWindow1.png)

<span data-ttu-id="72fe7-110">이러한 장면들은 Unity Build 설정.</span><span class="sxs-lookup"><span data-stu-id="72fe7-110">These scenes are from the Unity Build Settings.</span></span> <span data-ttu-id="72fe7-111">드롭다운 메뉴를 사용하여 대상 디바이스 유형을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fe7-111">You can change the target device type using the dropdown menu.</span></span>

## <a name="appx-build-options"></a><span data-ttu-id="72fe7-112">Appx 빌드 옵션</span><span class="sxs-lookup"><span data-stu-id="72fe7-112">Appx Build Options</span></span>
![빌드 창 - Appx 빌드 옵션 2](images/MRTK_BuildWindow2.png)

<span data-ttu-id="72fe7-114">이 탭에는 Visual Studio 솔루션에 대한 구성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="72fe7-114">This tab shows the configuration for the Visual Studio solution.</span></span> <span data-ttu-id="72fe7-115">HoloLens 2 시선 추적 입력 기능을 사용하도록 설정하려면 **응시 입력 기능** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72fe7-115">To enabled HoloLens 2's eye-tracking input capability, check **Gaze Input Capability** option.</span></span> 

<span data-ttu-id="72fe7-116">사용자 지정 3D 앱 시작 관리자 아이콘에 대한 **3D 앱 시작 관리자 모델** 필드에서 .glb 파일을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fe7-116">You can assign .glb file in the **3D App Launcher Model** field for custom 3D app launcher icon.</span></span> <span data-ttu-id="72fe7-117">자세한 내용은 [3D 앱 시작 관리자 디자인 지침을](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72fe7-117">See [3D app launcher design guideline](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) for more information.</span></span>

<span data-ttu-id="72fe7-118">기본적으로 버전 지정 **옵션에서 자동 증가가** 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fe7-118">By default, **Auto Increment** is checked in the Versioning Options.</span></span> <span data-ttu-id="72fe7-119">AppX 버전은 자동으로 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="72fe7-119">AppX versions will be automatically incremented.</span></span>


## <a name="deploy-options"></a><span data-ttu-id="72fe7-120">배포 옵션</span><span class="sxs-lookup"><span data-stu-id="72fe7-120">Deploy Options</span></span>
![빌드 창 - 배포 옵션 3](images/MRTK_BuildWindow3.png)

<span data-ttu-id="72fe7-122">이 탭에서 장치 포털 대한 사용자 이름 및 암호를 입력하여 디바이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fe7-122">In this tab, you can connect to the device by entering username and password for the Device Portal.</span></span> 

<span data-ttu-id="72fe7-123">페이지 아래쪽에서 생성된 앱 패키지 목록을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72fe7-123">On the bottom of the page, you can find list of the app packages that has been created.</span></span> 

