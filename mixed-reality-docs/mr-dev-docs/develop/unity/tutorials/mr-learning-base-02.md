---
title: 프로젝트 초기화 및 첫 번째 애플리케이션 배포
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)에 대해 Unity 프로젝트를 구성하는 방법과 HoloLens 2에 배포하는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176025"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포

이 자습서에서는 새 Unity 프로젝트를 만들어서 MRTK(Mixed Reality Toolkit) 개발에 맞게 구성하고, MRTK를 가져오는 방법을 알아봅니다. 기본 Unity 장면을 Visual Studio에서 HoloLens 2로 구성, 빌드 및 배포하는 과정도 안내합니다. HoloLens 2가 배포되면 HoloLens에서 인식한 표면을 포함하는 공간 매핑 메시가 표시됩니다. 또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다.

## <a name="objectives"></a>목표

* HoloLens 개발을 위해 Unity를 구성하는 방법 알아보기
* HoloLens에 앱을 빌드하고 배포하는 방법 알아보기
* HoloLens 2 디바이스에서 공간 매핑 메시, 손 메시 및 프레임 속도 카운터 경험하기

### <a name="steps-overview"></a>단계 개요
:::row:::
    :::column:::
       ![개요 1단계](images/mr-learning-base/base-02-overview-step1.png) **1. 새 Unity 프로젝트 만들기**
    :::column-end:::
    :::column:::
       ![개요 2단계](images/mr-learning-base/base-02-overview-step2.png) **2. 프로젝트로 MRTK 가져오기**
    :::column-end:::
    :::column:::
       ![개요 3단계](images/mr-learning-base/base-02-overview-step3.png) **3. MRTK로 새 장면 구성**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       ![개요 4단계](images/mr-learning-base/base-02-overview-step4.png) **4. Unity 프로젝트 빌드**
    :::column-end:::
    :::column:::
       ![개요 5단계](images/mr-learning-base/base-02-overview-step5.png) **5. UWP 프로젝트 빌드**
    :::column-end:::
    :::column:::
       ![개요 6단계](images/mr-learning-base/base-02-overview-step6.png) **6. 디바이스에서 프로젝트 실행**
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a>Unity 프로젝트 만들기

**Unity Hub** 를 시작하고, **Projects(프로젝트)** 탭을 선택한 다음, **New(새로 만들기)** 단추 옆의 **아래쪽 화살표** 를 클릭합니다.

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

드롭다운에서 [필수 구성 요소](mr-learning-base-01.md#prerequisites)에 지정된 Unity **버전** 을 선택합니다.

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> Unity 허브에서 특정 Unity 버전을 사용할 수 없으면 Unity의 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>(아카이브 다운로드)에서 설치를 시작할 수 있습니다.

Create a new project(새 프로젝트 만들기) 창에서 다음을 수행합니다.

* **Templates(템플릿)** 가 **3D** 로 설정되어 있는지 확인합니다.
* 적합한 **Project Name(프로젝트 이름)** 을 입력합니다(예: _MRTK 자습서_).
* 프로젝트를 저장할 적합한 **Location(위치)** 을 선택합니다(예: _D:\MixedRealityLearning_).
* **Create(만들기)** 단추를 클릭하여 새 Unity 프로젝트를 만들고 시작합니다.

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> Windows에서 작업하는 경우 MAX_PATH 제한은 255자입니다. 따라서 Unity 프로젝트를 드라이브의 루트에 가깝게 저장해야 합니다.

Unity에서 프로젝트가 만들어질 때까지 기다립니다.

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a>빌드 플랫폼 전환

Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.

![Unity Build Settings... 메뉴 경로](images/mr-learning-base/base-02-section2-step1-1.png)

Build Settings(빌드 설정) 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고

1. **Target device(대상 디바이스)** 를 **HoloLens** 로 설정합니다.
2. **Architecture(아키텍처)** 를 **ARM 64** 로 설정합니다. 
3. **Build Type(빌드 형식)** 을 **D3D Project(D3D 프로젝트)** 로 설정합니다.
4. **Target SDK Version(대상 SDK 버전)** 을 **Latest Installed(최신 설치)** 로 설정합니다.
5. **최소 플랫폼 버전** 을 **10.0.1024.0** 으로 설정합니다.
6. **Target Studio Version(대상 Studio 버전)** 을 **Latest Installed(최신 설치)** 로 설정합니다.
7. **Build and Run on(빌드 및 실행)** 을 **USB Device(USB 디바이스)** 로 설정합니다.
8. 디버그와 관련하여 알려진 성능 문제가 있으므로 **Build configuration(빌드 구성)** 을 **Release(릴리스)** 로 설정합니다.
9. Switch Platform(플랫폼 전환) 단추를 클릭합니다.

![유니버설 Windows 플랫폼 설정이 지정된 Unity 빌드 설정](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

Unity에서 플랫폼 전환이 완료될 때까지 기다립니다.

![진행 중인 Unity 플랫폼 전환](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

Unity에서 플랫폼 전환을 완료하면 **x** 아이콘을 클릭하여 빌드 설정 창을 닫습니다.

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a>Mixed Reality Toolkit 가져오기 및 Unity 프로젝트 구성

Mixed Reality Toolkit을 Unity 프로젝트로 가져오려면 개발자가 Unity 프로젝트에 Mixed Reality 기능 패키지를 검색, 업데이트 및 추가할 수 있는 [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md)을 사용해야 합니다. 이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다.

[Microsoft 다운로드 센터](https://aka.ms/MRFeatureTool)에서 최신 버전의 Mixed Reality Feature Tool을 다운로드합니다. 다운로드가 완료되면 파일의 압축을 풀고 데스크톱에 저장합니다.

> [!NOTE]
> Mixed Reality Feature Tool을 실행하기 전에 [.NET 5.0 런타임](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)을 설치합니다.

다운로드한 폴더에서 실행 파일 **MixedRealityFeatureTool** 을 열어 Mixed Reality Feature Tool을 시작합니다.  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>장면 만들기 및 MRTK 구성

Unity 메뉴에서 **파일** > **새 장면** 을 선택합니다.

![Unity New Scene 메뉴 경로](images/mr-learning-base/base-02-section6-step1-1.png)

**새 장면** 창에서 **기본(기본 제공)** 을 선택하고 **만들기** 를 클릭하여 새 장면을 만듭니다.

![Unity 새 장면 창](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> 위 스크린샷은 Unity 버전 2020에서 가져온 것입니다. Unity 2019를 사용하는 경우 **만들기** 를 클릭하면 새로운 빈 장면이 생성됩니다.

Unity 메뉴에서 **Mixed Reality** > **Toolkit** >  **장면에 추가 및 구성...** 을 차례로 선택하여 MRTK를 현재 장면에 추가합니다.

![Unity Add to Scene and Configure... 메뉴 경로](images/mr-learning-base/base-02-section6-step1-2.png)

계층 구조 창에 **MixedRealityToolkit** 개체가 아직 선택된 상태로 검사기 창에서 **MixedRealityToolkit** 구성 프로필이 **DefaultMixedRealityToolkitConfigurationProfile** 로 설정되어 있는지 확인합니다.

![DefaultMixedRealityTookitConfigurationProfile이 선택된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-02-section6-step1-3.png)

Unity 메뉴에서 **File(파일)**  > **Save As(다른 이름으로 저장)...** 를 차례로 선택하여 Save Scene(장면 저장) 창을 엽니다.

![Unity Save As... 메뉴 경로](images/mr-learning-base/base-02-section6-step1-4.png)

**자산** > **장면** 에서 프로젝트의 장면을 저장합니다.

![Unity Save Scene Save 프롬프트 창](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a>개체에 손 상호 작용 추가

Unity 메뉴에서 **GameObject** > **3D 개체** > **큐브** 를 선택하여 장면에 큐브 개체를 추가합니다.

![장면에 큐브 추가](images/mr-learning-base/base-02-section8-step1-1.png)

계층 구조 창에서 **큐브** 개체를 클릭한 다음 검사기 창에서 다음과 같이 **변환** 구성 요소를 구성합니다.

* **위치**: X = 0, Y = 0.1, Z = 0.5
* **회전**: X = 0, Y = 0, Z = 0
* **배율**: X = 0.1, Y = 0.1, Z = 0.1

1 Unity 단위는 1미터입니다. 큐브의 크기를 헤드셋 위치(0,0,0)에서 50cm에, 편안한 상호 작용을 위해 눈높이 10cm 아래에 배치하여 10x10x10cm로 업데이트했습니다. 

기본 배율(1,1,1)을 사용하면 큐브가 너무 커집니다. 기본 위치(0,0,0)를 사용하면 큐브가 헤드셋과 같은 위치에 배치되고 뒤로 이동할 때까지 볼 수 없습니다.

![변환 정보 조정](images/mr-learning-base/base-02-section8-step1-1b.png)

장면의 개체에 초점을 맞추기 위해 **Cube** 개체를 두 번 클릭한 다음, 약간씩 다시 확대할 수 있습니다. 또는 F 키를 사용하여 개체를 확대/축소하고 초점을 맞출 수 있습니다.

추적된 손으로 개체를 상호 작용하고 잡으려면 개체에 다음이 있어야 합니다.
 * **상자 충돌체** 와 같은 충돌체 구성 요소(Unity의 큐브에는 기본적으로 상자 충돌체가 이미 있음)
 * **Object Manipulator(스크립트)** 구성 요소
 * **NearInteractionGrabbable(스크립트)** 구성 요소

MRTK의 **ObjectManipulator** 스크립트를 사용하면 한 손 또는 양손을 사용하여 개체를 이동, 크기 조정, 회전할 수 있습니다. 사용자가 손으로 홀로그램을 직접 터치할 수 있으므로 이 스크립트는 직접 조작 입력 모델을 지원합니다.

Hierarchy 창에서 **Cube** 를 선택한 상태로 Inspector 창에서 **Add Component** 단추를 클릭한 다음, **Object Manipulator** 스크립트를 검색하고 선택하여 Object Manipulator 스크립트를 큐브 개체에 추가합니다.

![큐브에 Object Manipulator 추가](images/mr-learning-base/base-02-section8-step1-2.PNG)

동일한 작업을 반복하여 **Near Interaction Grabbable 스크립트** 를 큐브에 추가합니다.

![큐브에 Near Interaction Grabable 추가](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> 이 경우 Object Manipulator(Script)를 추가하면 Object Manipulator(Script)가 종속되어 있으므로 Constraint Manager(Script)가 자동으로 추가됩니다.

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a>MRTK 입력 시뮬레이션을 사용하여 Unity 편집기에서 애플리케이션 테스트

MRTK의 입력 시뮬레이션을 사용하면 디바이스를 빌드하고 배포하지 않고도 Unity 편집기에서 다양한 유형의 상호 작용을 테스트할 수 있습니다. 이를 통해 설계 및 개발 프로세스에서 아이디어를 빠르게 반복할 수 있습니다. 키보드와 마우스 조합을 사용하여 시뮬레이션된 입력을 제어합니다.

재생 단추를 클릭하여 재생 모드로 전환합니다. **왼쪽 Shift** 또는 **스페이스바** 키를 눌러 컨트롤러(시뮬레이션된 손)를 불러 오면 마우스 움직임으로 컨트롤러가 이동하고 마우스 휠을 사용하여 카메라에 더 가깝게 이동할 수 있습니다. 포인터가 Cube에 있으면 **마우스 왼쪽 단추** 를 누른 상태로 Cube 개체를 가져옵니다.

* **W, A, S, D, Q, E** 키를 눌러 카메라를 이동합니다.
* **마우스 오른쪽 단추** 를 누른 채 마우스를 움직여 주위를 둘러봅니다.
* 시뮬레이션된 손을 들어 가져오려면 **스페이스 바(오른손)** 또는 **왼쪽 Shift 키(왼손)** 를 누릅니다.
* 시뮬레이션된 손을 뷰에 유지하려면 **T** 또는 **Y** 키를 누릅니다.
* 시뮬레이션된 손을 회전하려면 **Ctrl** 키를 누른 상태에서 마우스를 이동합니다.

![게임 모드](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a>HoloLens 2에 애플리케이션 빌드

### <a name="1-build-the-unity-project"></a>1. Unity 프로젝트 빌드

Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.

Build Settings 창에서 **Add Open Scenes(열려 있는 장면 추가)** 단추를 클릭하여 현재 장면을 **Scenes In Build(빌드 중인 장면)** 목록에 추가한 다음, **Build(빌드)** 단추를 클릭하여 Build Universal Windows Platform(유니버설 Windows 플랫폼 빌드) 창을 엽니다.

![UWP가 선택된 Unity Build Settings 창](images/mr-learning-base/base-02-section9-step1-1.png)

Build Universal Windows Platform 창에서 빌드를 저장할 적합한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택하고, 새 폴더를 만들어 적합한 이름(예: _GettingStarted_)을 지정한 다음, **Select Folder(폴더 선택)** 단추를 클릭하여 빌드 프로세스를 시작합니다.

![Select Folder 프롬프트 창이 있는 Unity Build Settings 창](images/mr-learning-base/base-02-section9-step1-2.png)

Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.

![진행 중인 Unity 빌드 프로세스](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. 애플리케이션 빌드 및 배포

빌드 프로세스가 완료되면 Unity는 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다. 폴더 내부를 탐색하고 솔루션 파일을 두 번 클릭하여 Visual Studio에서 엽니다.

![새로 만든 Visual Studio 솔루션이 선택된 Windows 탐색기](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 잠시 시간을 내어 **[도구 설치](../../install-the-tools.md)** 설명서의 필수 구성 요소가 모두 있는지 확인합니다.

**마스터** 또는 **릴리스** 구성, **ARM64** 아키텍처 및 **디바이스** 를 대상으로 선택하여 HoloLens용 Visual Studio를 구성합니다.

![HoloLens 2에 배포하도록 구성된 Visual Studio](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> HoloLens(1세대)에 배포하는 경우 **x86** 아키텍처를 선택합니다.

> [!NOTE]
> HoloLens의 경우 일반적으로 ARM 아키텍처용으로 빌드합니다. 하지만 Unity 2019.3에는 Visual Studio에서 ARM을 빌드 아키텍처로 선택할 때 오류가 발생하는 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>알려진 문제</strong></a>가 있습니다. 권장 해결 방법은 ARM64용으로 빌드하는 것입니다. 그렇게 할 수 없으면 **편집 > 프로젝트 설정 > 플레이어 > 기타 설정** 으로 이동하여 **Graphics Jobs**(그래픽 작업)을 사용하지 않도록 설정합니다.

> [!NOTE]
> 디바이스가 대상 옵션으로 보이지 않으면, Visual Studio 솔루션의 시작 프로젝트를 IL2CPP 프로젝트에서 UWP 프로젝트로 변경해야 할 수 있습니다. 이렇게 하려면 솔루션 탐색기에서 YourProjectName(유니버설 Windows)을 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정** 을 선택합니다.

HoloLens를 컴퓨터에 연결한 다음, **디버그** > **디버그하지 않고 시작** 을 선택하여 빌드하고 디바이스에 배포합니다.

![Visual Studio Start Without Debugging 메뉴 경로](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> 디바이스에 빌드하기 전에 디바이스가 [개발자 모드]에 있고 개발 머신과 페어링되어야 합니다. 이 두 단계는 모두 [이러한 지침](../../platform-capabilities-and-apis/using-visual-studio.md)에 따라 완료할 수 있습니다.

> [!TIP]
> [HoloLens 에뮬레이터](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)에 배포하거나 테스트용 로드 [앱 패키지](/windows/uwp/packaging/packaging-uwp-apps)를 만들 수도 있습니다.

디버그하지 않고 시작을 사용하면 Visual Studio 디버거를 연결하지 않고 디바이스에서 앱이 자동으로 시작됩니다.

**빌드 > 솔루션 배포** 를 선택하여 앱을 자동으로 시작하지 않고 디바이스에 배포합니다.

> [!NOTE]
>앱에 Diagnostics 프로파일러가 보일 수 있으며, 음성 명령 **"Toggle Diagnostics"** 를 사용하여 표시 유형을 전환할 수 있습니다. 앱을 변경할 때 성능에 영향을 줄 수 있는 시점을 파악하려면 개발하는 동안 프로파일러가 대부분 표시되도록 하는 것이 좋습니다. 예를 들어 HoloLens 앱은 [60FPS에서 지속적으로 실행](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)해야 합니다.

## <a name="congratulations"></a>축하합니다.

이제 첫 번째 HoloLens 앱을 배포했습니다. 앱이 열리면 Cube 개체가 앞에 표시되어야 하며 큐브를 이동함으로써 상호 작용할 수 있어야 하며, 연습을 진행할 때 HoloLens가 인식하는 표면을 덮는 공간 매핑 메시가 표시되어야 합니다. 또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다. 이러한 기능은 MRTK에 포함된 몇 가지 기본적인 부분입니다. 다음 자습서에서는 장면에 콘텐츠를 추가하여 HoloLens와 MRTK의 기능을 살펴봅니다.

> [!div class="nextstepaction"]
> [다음 자습서: 3. MRTK 프로필 구성](mr-learning-base-03.md)
