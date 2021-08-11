---
ms.openlocfilehash: 7fd590713322c296cbbb14e133b1085aa27bb0197b70d1feca1ecb59ed61a3c7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201723"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

**MixedRealityFeatureTool** 이 열리면 **시작** 을 클릭하여 Mixed Reality Feature Tool을 시작합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

첫 번째 단계는 **줄임표** 단추를 사용하여 Mixed Reality Feature Tool을 **프로젝트 경로** 로 지정하고 프로젝트 경로 옆에 있는 점 3개 줄임표 단추를 클릭하고 탐색기에서 프로젝트 폴더를 찾는 것입니다(예: _D:\MixedRealityLearning\MRTK Tutorials_).

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

프로젝트의 폴더를 찾았으면 열기 단추를 클릭하여 Mixed Reality Feature Tool로 돌아갑니다. 그런 다음 **기능 검색** 을 클릭합니다.

> [!NOTE]
> Unity 프로젝트 폴더를 검색할 때 표시되는 대화 상자에는 파일 이름에 '_'가 포함됩니다. 파일 이름에 대한 값이 있어야 폴더를 선택할 수 있습니다.

> [!Important]
> Mixed Reality Feature Tool은 유효성 검사를 수행하여 Unity 프로젝트 폴더로 지정되었는지 확인합니다. 폴더에는 자산, 패키지 및 프로젝트 설정 폴더가 있어야 합니다.

기능은 카테고리별로 그룹화되어 있어 쉽게 찾을 수 있습니다. **Mixed Reality Toolkit** 드롭다운을 클릭하여 Mixed Reality Toolkit과 관련된 패키지를 찾고 **플랫폼 지원** 드롭다운을 클릭하여 다양한 지원 플랫폼 관련 패키지를 찾습니다.

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

**Mixed Reality Toolkit Foundation** 을 선택하고 옆에 있는 드롭다운을 클릭하여 **MRTK 2.7.2** 를 선택하고 **Mixed Reality OpenXR Plugin 1.0.0** 도 선택하고 옆에 있는 드롭다운을 클릭하여 사용 가능한 최신 버전을 선택한 다음 **기능 가져오기** 단추를 클릭하여 선택한 패키지를 다운로드합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

다음으로 **유효성 검사** 단추를 클릭하여 선택한 패키지의 유효성을 검사하면 **유효성 검사 문제가 감지되지 않았습니다** 라는 팝업 메시지가 표시됩니다. **확인** 을 클릭하여 팝업을 닫고 **가져오기** 단추를 클릭합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


**승인** 단추를 클릭하여 **Mixed Reality Toolkit** 을 프로젝트에 추가합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a>Unity 프로젝트 구성

Unity가 이전 섹션에서 패키지 가져오기를 완료하면 새 플러그 인 시스템의 백 엔드를 사용하도록 설정하기 위해 Unity 편집기를 다시 시작하라는 경고 메시지가 표시됩니다. **예** 를 클릭합니다.

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

Unity가 다시 시작되면 MRTK Project Configurator 창이 나타납니다. 그렇지 않으면 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 프로젝트 구성** 으로 이동하여 수동으로 열 수 있습니다.

![MRTK Project Configurator 창을 엽니다.](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

**Unity OpenXR 플러그 인** 을 클릭하여 XR 플러그 인 관리를 사용하도록 설정하고 필요한 패키지를 프로젝트에 추가합니다.

![Unity OpenXR 플러그 인 추가 ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

그러면 XR 플러그 인 관리에 필요한 Unity 패키지를 가져옵니다. 완료되면 MRTK Project Configurator에서 **XR 플러그 인 관리 설정 표시** 를 클릭합니다.

![XR 플러그 인 관리 설정 표시 ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

그러면 **프로젝트 설정 창** 이 열립니다. **XR 플러그 인 관리** 아래의 프로젝트 설정 창에서 유니버설 Windows 플랫폼 설정(Windows 로고 탭)에 있는지 확인합니다. 또한 **시작 시 XR 초기화** 가 선택되어 있는지 확인한 다음 **OpenXR** 확인란과 **Microsoft HoloLens 기능 세트** 확인란을 클릭하여 사용하도록 설정합니다.

![Open XR 사용 설정](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

OpenXR 확인란을 선택하면 MRTK Project Configurator 창에 **설정 적용** 단추와 함께 업데이트된 메시지가 표시됩니다. **설정 적용** 단추를 클릭합니다. 

![프로젝트 설정 창 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

설정 적용을 클릭하면 콘솔에 이 오류 메시지가 표시될 수 있습니다. 이것이 유일한 오류이거나 오류가 없는 경우 계속할 수 있습니다.

![OpenXR 원격 오류 메시지](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

OpenXR 구성을 확인하려면 **XR 플러그 인 관리** 에서 **OpenXR** 을 클릭하고 다음 항목을 확인합니다.
* 깊이 제출 모드: **깊이 16비트**
* 상호 작용 프로필: **Microsoft 손 상호 작용 프로필**

![프로젝트 설정 창 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> Depth Format(심도 형식)을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다. 이 항목에 대한 자세한 정보는 MRTK의 성능 설명서의 <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.


**MRTK Project Configurator** 창에서 **다음** 을 클릭한 후 **적용** 단추를 클릭하여 설정을 적용합니다. (닫은 경우 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 구성 프로젝트** 로 이동하여 수동으로 열 수 있습니다.)

![프로젝트 설정 창 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![프로젝트 설정 창 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

적용을 클릭하면 Unity가 입력 시스템을 적용하기 위해 다시 시작을 시도하고 **적용** 을 클릭하여 Unity 편집기를 다시 시작합니다.

### <a name="configure-additional-project-settings"></a>추가 프로젝트 설정 구성

Unity 메뉴에서 **Edit(편집)** > **Project Settings(프로젝트 설정)** 를 선택하여 Project Settngs(프로젝트 설정) 창을 엽니다.

프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.

![Unity 게시 설정. 구성된 패키지 이름](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> '패키지 이름'은 앱의 고유 식별자입니다. 이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.

> [!TIP]
> '제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다. 개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 플러그 인](#tab/winxr)

**MixedRealityFeatureTool** 이 열리면 **시작** 을 클릭하여 Mixed Reality Feature Tool을 시작합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

첫 번째 단계는 **줄임표** 단추를 사용하여 Mixed Reality Feature Tool을 **프로젝트 경로** 로 지정하고 프로젝트 경로 옆에 있는 점 3개 줄임표 단추를 클릭하고 탐색기에서 프로젝트 폴더를 찾는 것입니다(예: _D:\MixedRealityLearning\MRTK Tutorials_).

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


프로젝트의 폴더를 찾았으면 열기 단추를 클릭하여 Mixed Reality Feature Tool로 돌아갑니다. 그런 다음 **기능 검색** 을 클릭합니다.

> [!NOTE]
> Unity 프로젝트 폴더를 검색할 때 표시되는 대화 상자에는 파일 이름에 '_'가 포함됩니다. 파일 이름에 대한 값이 있어야 폴더를 선택할 수 있습니다.

> [!Important]
> Mixed Reality Feature Tool은 유효성 검사를 수행하여 Unity 프로젝트 폴더로 지정되었는지 확인합니다. 폴더에는 자산, 패키지 및 프로젝트 설정 폴더가 있어야 합니다.

기능은 쉽게 찾을 수 있도록 카테고리별로 그룹화되어 있습니다. **Mixed Reality Toolkit** 드롭다운을 클릭하면 Mixed Reality Toolkit과 관련된 패키지를 찾을 수 있습니다.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

**Mixed Reality Toolkit Foundation** 에 대한 확인란을 선택하고 그 옆에 있는 드롭다운을 클릭하여 **MRTK 2.7.0** 을 선택한 후 **기능 다운로드** 단추를 클릭하여 선택한 패키지를 다운로드합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

다음으로 **유효성 검사** 단추를 클릭하여 선택한 패키지의 유효성을 검사하면 **유효성 검사 문제가 감지되지 않았습니다** 라는 팝업 메시지가 표시됩니다. **확인** 을 클릭하여 팝업을 닫고 **가져오기** 단추를 클릭합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


**승인** 단추를 클릭하여 **Mixed Reality Toolkit** 을 프로젝트에 추가합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Unity 프로젝트 구성

Unity가 이전 섹션에서 패키지 가져오기를 완료하면 MRTK Project Configurator 창이 표시됩니다. 그렇지 않으면 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 프로젝트 구성** 으로 이동하여 수동으로 열 수 있습니다.

![MRTK 구성 도구 열기](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

**Unity 플러그 인(비OpenXR) 기본 제공** 을 클릭하여 XR 플러그 인 관리를 사용하도록 설정하고 필요한 패키지를 프로젝트에 추가합니다.

![ MRTK 구성 도구](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> 위 스크린샷은 Unity 2020에서 가져온 것입니다. Unity 2019를 사용하는 경우 **XR SDK/XR 관리** 를 선택하세요.

이렇게 하면 XR 플러그 인 관리에 필요한 Unity 패키지를 가져옵니다. 완료되면 MRTK Project Configurator에서 **설정 표시** 를 클릭합니다.

![플레이어 설정 창](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

그러면 **프로젝트 설정 창** 이 열립니다. 프로젝트 설정 창의 **XR 플러그 인 관리** 아래에서 유니버설 Windows 플랫폼 설정에 있는지 확인하고 **시작 시 XR 초기화** 를 선택하고 **Windows Mixed Reality** 확인란을 선택합니다.

![플레이어 설정 창 Mixed Reality 사용-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

Unity가 Windows Mixed Reality SDK 가져오기를 마치면 MRTK Project Configurator 창이 다시 표시됩니다. 그렇지 않으면 Unity 메뉴를 사용하여 엽니다.

MRTK Project Configurator 창에서 **다음** 을 클릭한 후 Audio spatializer 드롭다운을 사용하여 **MS HRTF Spatializer** 를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.

![MRTK Project Configurator-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> MRTK 기본 설정을 적용하는 것은 선택 사항이지만, 다음과 같은 몇 가지 Unity 추천 설정을 구성하는 데 도움이 되므로 이러한 설정을 사용하는 것이 매우 좋습니다.

> * 단일 패스 인스턴스 렌더링 경로 설정: 동일한 그리기 호출에서 양쪽 눈에 대한 렌더링 파이프라인을 실행하여 그래픽 성능을 향상시킵니다. 이 항목에 대한 자세한 내용은 MRTK의 [성능](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) 설명서의 [단일 패스 인스턴스 렌더링](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) 섹션을 참조하세요.
> * 기본 공간 인식 계층 설정: 공간 인식이라는 Unity 계층을 만들고, 이 계층을 공간 인식 메시에 사용하도록 MRTK를 구성합니다. Unity 계층에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조하세요.

> [!TIP]
> Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다. MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다. 이 항목에 대한 자세한 정보는 <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">공간 오디오 자습서</a>를 참조하세요.

**다음** 을 클릭한 다음 MRTK Project Configurator 창에서 **완료** 를 클릭하여 XRSDK에 대한 Unity 프로젝트 구성을 완료합니다.

### <a name="configure-additional-project-settings"></a>추가 프로젝트 설정 구성

Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.

프로젝트 설정 창에서 **XR 플러그 인 관리** > **Windows Mixed Reality** > **런타임 설정** 을 선택한 후 **깊이 버퍼 형식** 드롭다운을 사용하여 **16비트 깊이** 를 선택합니다.

![Unity 16 깊이 사용](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> Depth Format을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다. 이 항목에 대한 자세한 정보는 MRTK의 성능 설명서의 <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.

프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.

![Unity 게시 설정. 구성된 패키지 이름](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> '패키지 이름'은 앱의 고유 식별자입니다. 이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.

> [!TIP]
> '제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다. 개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)

**MixedRealityFeatureTool** 이 열리면 **시작** 을 클릭하여 Mixed Reality Feature Tool을 시작합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

첫 번째 단계는 **줄임표** 단추를 사용하여 Mixed Reality Feature Tool을 **프로젝트 경로** 로 지정하고 프로젝트 경로 옆에 있는 점 3개 줄임표 단추를 클릭하고 탐색기에서 프로젝트 폴더를 찾는 것입니다(예: _D:\MixedRealityLearning\MRTK Tutorials_).

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

프로젝트의 폴더를 찾았으면 열기 단추를 클릭하여 Mixed Reality Feature Tool로 돌아갑니다. 그런 다음 **기능 검색** 을 클릭합니다.

> [!NOTE]
> Unity 프로젝트 폴더를 검색할 때 표시되는 대화 상자에는 파일 이름에 '_'가 포함됩니다. 파일 이름에 대한 값이 있어야 폴더를 선택할 수 있습니다.

> [!Important]
> Mixed Reality Feature Tool은 유효성 검사를 수행하여 Unity 프로젝트 폴더로 지정되었는지 확인합니다. 폴더에는 자산, 패키지 및 프로젝트 설정 폴더가 있어야 합니다.

기능은 쉽게 찾을 수 있도록 카테고리별로 그룹화되어 있습니다. **Mixed Reality Toolkit** 드롭다운을 클릭하면 Mixed Reality Toolkit과 관련된 패키지를 찾을 수 있습니다.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

**Mixed Reality Toolkit Foundation** 에 대한 확인란을 선택하고 그 옆에 있는 드롭다운을 클릭하여 **MRTK 2.7.0** 을 선택한 후 **기능 다운로드** 단추를 클릭하여 선택한 패키지를 다운로드합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

다음으로 **유효성 검사** 단추를 클릭하여 선택한 패키지의 유효성을 검사하면 **유효성 검사 문제가 감지되지 않았습니다** 라는 팝업 메시지가 표시됩니다. **확인** 을 클릭하여 팝업을 닫고 **가져오기** 단추를 클릭합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

**승인** 단추를 클릭하여 **Mixed Reality Toolkit** 을 프로젝트에 추가합니다.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Unity 프로젝트 구성

Unity가 이전 섹션에서 패키지 가져오기를 완료하면 MRTK Project Configurator 창이 표시됩니다. 그렇지 않으면 **Mixed Reality** > **Toolkit** > **유틸리티** > **MRTK용 프로젝트 구성** 으로 이동하여 수동으로 열 수 있습니다.

![Unity 프로젝트 구성 메뉴 경로](../images/mr-learning-base/base-02-section5-step1-1.png)

**레거시 XR** 을 클릭하여 레거시 XR을 사용하도록 설정하고 필요한 패키지를 프로젝트에 추가합니다.

![초](../images/mr-learning-base/base-02-section5-step1-2.png)

다음 단추를 클릭하여 레거시 XR에 대한 XR 파이프라인 설정을 사용하도록 설정합니다.

![Unity MRTK 구성 창](../images/mr-learning-base/base-02-section5-step1-3.PNG)

MRTK Project Configurator 창에서 모든 옵션이 선택되었는지 확인하고 **Audio spatializer** 드롭다운을 사용하여 **MS HRTF Spatializer** 를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.

![MRTK 구성 창](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> MRTK 기본 설정을 적용하는 것은 선택 사항이지만, 다음과 같은 몇 가지 Unity 추천 설정을 구성하는 데 도움이 되므로 이러한 설정을 사용하는 것이 매우 좋습니다.

> * 단일 패스 인스턴스 렌더링 경로 설정: 동일한 그리기 호출에서 양쪽 눈에 대한 렌더링 파이프라인을 실행하여 그래픽 성능을 향상시킵니다. 이 항목에 대한 자세한 내용은 MRTK의 [성능](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) 설명서의 [단일 패스 인스턴스 렌더링](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) 섹션을 참조하세요.
> * 기본 공간 인식 계층 설정: 공간 인식이라는 Unity 계층을 만들고, 이 계층을 공간 인식 메시에 사용하도록 MRTK를 구성합니다. Unity 계층에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조하세요.

> [!TIP]
> Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다. MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다. 이 항목에 대한 자세한 정보는 <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">공간 오디오 자습서</a>를 참조하세요.

**다음** 을 클릭한 다음 MRTK Project Configurator 창에서 **완료** 단추를 클릭하여 레거시 XR에 대한 Unity 프로젝트 구성을 완료합니다.

### <a name="configure-additional-project-settings"></a>추가 프로젝트 설정 구성

Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.

프로젝트 설정 창에서 **플레이어** > **XR 설정** 을 선택한 다음, **Depth Format**(수준 형식) 드롭다운을 사용하여 **16비트 수준** 을 선택합니다.

![Unity 16 깊이 사용](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> Depth Format을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다. 이 항목에 대한 자세한 정보는 MRTK의 성능 설명서의 <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.

프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.

![Unity 게시 설정. 구성된 패키지 이름](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> '패키지 이름'은 앱의 고유 식별자입니다. 이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.

> [!TIP]
> '제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다. 개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.
