---
ms.openlocfilehash: 2886a9ad26ff38a2051d4ea6961286e1e190588128a2f045ae39841470113157
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198093"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

### <a name="1-switching-build-platform"></a>1. 빌드 플랫폼 전환

Unity 메뉴에서 파일 > 빌드 설정을 차례로 선택하여 빌드 설정 창을 엽니다.

빌드 설정 창에서 **PC, Mac & Linux 독립 실행형** 플랫폼을 선택하고 **플랫폼 전환** 단추를 클릭하여 빌드 플랫폼을 변경합니다.

![빌드 플랫폼 전환](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

Unity에서 플랫폼 전환을 완료하면 x 아이콘을 클릭하여 빌드 설정 창을 닫습니다.

### <a name="2-set-the-project-settings"></a>2. 프로젝트 설정 지정

Unity 메뉴에서 **편집** > **프로젝트 설정** > **XR 플러그 인 관리** 를 선택하고 Windows 독립 실행형 탭에 있는지 확인하고 **OpenXR**  및 **Windows Mixed Reality 기능 세트** 확인란을 선택합니다.

![OpenXR 및 Windows Mixed Reality 기능 세트 사용 설정](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

프로젝트 설정 창에서 **OpenXR** 을 선택하고 Windows 독립 실행형 탭에 있는지 확인하고 **깊이 제출 모드** 를 없음에서 **깊이 16비트** 로 변경합니다.

상호 작용 프로필 탭에서 + 기호를 클릭하여 **시선 응시 상호 작용 프로필** 및 **Microsoft 손 상호 작용 프로필** 을 추가합니다.

![시선 응시 상호 작용 프로필 및 Microsoft 손 상호 작용 프로필 추가](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

**Open XR 기능 그룹** > **모든 기능** > **Holographic 앱 원격** 확인란을 선택합니다.

![Holographic 앱 원격 사용 설정](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

그런 다음 **Windows Mixed Reality** 확인란을 선택하고 Windows Mixed Reality 그룹에서 **Holographic 앱 원격** 확인란을 선택합니다.

![Windows Mixed Reality Holographic 앱 원격 사용 설정](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a>3. Unity 프로젝트 빌드

Unity 메뉴에서 파일 > 빌드 설정을 차례로 선택하여 빌드 설정 창을 엽니다.

Build Settings(빌드 설정) 창에서 ***Add Open Scenes** _ 단추를 클릭하여 현재 장면을 Scenes(장면)에 추가합니다. 빌드 목록에서 _ *빌드** 단추를 클릭합니다.

![장면이 추가된 Unity Build Settings 창](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

빌드를 저장할 적절한 위치를 선택합니다(예: Documents\MixedRealityLearning). 새 폴더를 만들고 적절한 이름(예: PCHolographicRemoting)을 지정합니다. 그런 다음, ***폴더 선택*** 단추를 클릭하여 빌드 프로세스를 시작합니다.

![Select Folder 프롬프트 창이 있는 Unity Build Settings 창](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.

![진행 중인 Unity 빌드 프로세스](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

실행 파일을 두 번 클릭하여 PC에서 PC Holographic 원격 애플리케이션을 엽니다.

> [!NOTE]
> UWP로 빌드된 PC 앱용 Holographic 원격의 일부 알려진 문제로 인해 PC 앱을 OpenXR용 Windows 독립 실행형으로 빌드하고 있습니다.


# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)

### <a name="1-set-the-player-settings"></a>1. 플레이어 설정 지정

**XR 설정** 섹션에서 **WSA 홀로그램 원격 지원** 확인란을 선택하고 홀로그램 원격을 사용하도록 설정합니다.

![WSA 홀로그램 원격 지원이 사용되도록 설정된 Unity XR 설정 창](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a>2. Unity 프로젝트 빌드

Unity 메뉴에서 파일 > 빌드 설정을 차례로 선택하여 빌드 설정 창을 엽니다.

Build Settings(빌드 설정) 창에서 ***Add Open Scenes** _ 단추를 클릭하여 현재 장면을 Scenes(장면)에 추가합니다. Build 목록에서 _ *_Build 단추_**를 클릭하여 유니버설 Windows 플랫폼 빌드 창을 엽니다.

![장면이 추가된 Unity Build Settings 창](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

빌드 유니버설 Windows 플랫폼 창에서 빌드를 저장할 적합한 위치(예: Documents\MixedRealityLearning)를 선택합니다. 새 폴더를 만들고 적절한 이름(예: PCHolographicRemoting)을 지정합니다. 그런 다음, ***폴더 선택*** 단추를 클릭하여 빌드 프로세스를 시작합니다.

![Select Folder 프롬프트 창이 있는 Unity Build Settings 창](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.

![진행 중인 Unity 빌드 프로세스](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a>3. 애플리케이션 빌드 및 배포

빌드 프로세스가 완료되면 Unity에서 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다. 폴더 내부를 탐색하고 .sln 파일을 두 번 클릭하여 Visual Studio에서 엽니다.

![새로 만든 Visual Studio 솔루션이 선택된 Windows 탐색기](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 도구 설치 설명서에서 지정한 대로 모든 필수 구성 요소가 설치되어 있는지 확인합니다.

릴리스 구성, x64 아키텍처 및 로컬 머신을 대상으로 선택하여 PC에 대해 Visual Studio를 구성합니다.

![로컬 컴퓨터에 대해 구성된 Visual Studio](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

***로컬 머신*** 이라고 표시된 단추를 클릭합니다. 애플리케이션을 빌드하고 PC에 배포하기 시작합니다. 애플리케이션은 기본적으로 PC에 설치됩니다.
