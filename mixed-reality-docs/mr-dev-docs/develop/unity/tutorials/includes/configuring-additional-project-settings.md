---
ms.openlocfilehash: 2b0dc328a1a47d9a0bd385cac6a88563dcc3938d
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107327029"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows XR 플러그 인](#tab/winxr)

Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.

![Unity Project Settings... 메뉴 경로](../images/mr-learning-base/base-02-section5-step2-1.png)

프로젝트 설정 창에서 **XR Plug-in Management** > **Install XR Plug-in Management(XR Plug-in Management 설치)** 를 선택하여 XR Plug-in Management를 설치합니다.

![Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-2.png)

Unity에서 XR Plug-in Management 설치를 완료한 후 유니버설 Windows 플랫폼 설정에 있는지 확인하고 **Initialize XR on Startup(시작 시 XR 초기화)** 및 **Windows Mixed Reality** 확인란을 선택합니다.

![Windows Mixed Reality SDK 추가가 표시된 Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-2-1.png)

Unity가 Windows Mixed Reality SDK 가져오기를 마치면 MRTK Project Configurator 창이 다시 표시됩니다. 그렇지 않으면 Unity 메뉴를 사용하여 엽니다.

MRTK Project Configurator 창에서 **Audio spatializer** 드롭다운을 사용하여 **MS HRTF Spatializer** 를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.

![Windows Mixed Reality SDK가 선택된 Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다. MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다. 이 항목에 대한 자세한 정보는 <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">공간 오디오 자습서</a>를 참조하세요.

Project Settings(프로젝트 설정) 창에서 **XR Plug-in Management(XR 플러그 인 관리)**  > **Windows Mixed Reality** > **Runtime Settings(런타임 설정)** 를 선택한 후 **Depth Buffer Format(깊이 버퍼 형식)** 드롭다운을 사용하여 **16-bit depth(16비트 깊이)** 를 선택합니다.

![패키지 이름이 강조 표시된 Unity 게시 설정](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> Depth Format을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다. 이 항목에 대한 자세한 정보는 MRTK의 <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank">성능</a> 설명서의 <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.

프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.

![패키지 이름이 표시된 Unity 게시 설정](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> '패키지 이름'은 앱의 고유 식별자입니다. 이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.

> [!TIP]
> '제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다. 개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.

![Unity Project Settings... 메뉴 경로](../images/mr-learning-base/base-02-section5-step2-1.png)

프로젝트 설정 창에서 **XR Plug-in Management** > **Install XR Plug-in Management(XR Plug-in Management 설치)** 를 선택하여 XR Plug-in Management를 설치합니다.

![Install XR plug-in management(XR 플러그 인 설치 관리)가 선택된 Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-2.png)

Unity에서 XR Plug-in Management 설치를 완료한 후 유니버설 Windows 플랫폼 설정에 있는지 확인하고 **Initialize XR on Startup(시작 시 XR 초기화)** , **OpenXR** 및 **Microsoft HoloLens feature set(Microsoft HoloLens 기능 세트)** 확인란을 선택합니다.

![OpenXR 및 Microsoft HoloLens 기능 추가가 선택된 Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

화면 상단의 메뉴 모음에서 **Mixed Reality > OpenXR > Apply recommended project settings for HoloLens 2(HoloLens 2에 권장되는 프로젝트 설정 적용)** 로 이동하여 앱 성능을 높입니다.

![OpenXR 및 HoloLens 2에 권장되는 프로젝트 설정 적용이 선택된 Mixed Reality 메뉴](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

>[!Important]
>OpenXR 플러그 인(미리 보기) 옆에 빨간색 경고 아이콘이 표시되는 경우 계속하기 전에 아이콘을 클릭하고 Fix all(모두 해결)을 선택합니다. Unity Editor를 다시 시작해야 변경 내용이 적용될 수 있습니다.
>![모든 문제가 해결 대상으로 선택된 OpenXR 프로젝트 유효성 검사 메뉴](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)

Unity가 필요한 파일 가져오기를 마치면 MRTK Project Configurator(MRTK 프로젝트 구성기) 창이 다시 표시됩니다. 그렇지 않으면 Unity 메뉴를 사용하여 엽니다.

MRTK Project Configurator 창에서 **Audio spatializer** 드롭다운을 사용하여 **MS HRTF Spatializer** 를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.

![기본 옵션이 선택된 MRTK 구성 창](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다. MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다. 이 항목에 대한 자세한 정보는 <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">공간 오디오 자습서</a>를 참조하세요.


프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.

![Unity 게시 설정](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> '패키지 이름'은 앱의 고유 식별자입니다. 이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.

> [!TIP]
> '제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다. 개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.

# <a name="legacy-wsa"></a>[레거시 WSA](#tab/wsa)

Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.

프로젝트 설정 창에서 **플레이어** > **XR 설정** 을 선택하고 **Virual Reality Supported** 확인란을 선택한 다음, **+** 아이콘을 클릭하고 Windows Mixed Reality를 선택하여 Windows Mixed Reality SDK를 추가합니다.

![Windows Mixed Reality SDK 추가가 선택된 Unity XR 설정](../images/mr-learning-base/base-02-section5-step2-4.png)

Unity가 Windows Mixed Reality SDK 가져오기를 마치면 MRTK Project Configurator 창이 다시 표시됩니다. 그렇지 않으면 Unity 메뉴에서 **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** 로 이동하여 수동으로 열 수 있습니다.

MRTK Project Configurator 창에서 **Audio spatializer** 드롭다운을 사용하여 **MS HRTF Spatializer** 를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.

![MRTK 구성 창](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>Audio spatializer 속성 설정은 선택 사항이지만, 프로젝트에서 오디오 환경을 향상시킬 수 있습니다. MS HRTF Spatializer로 설정하면 Unity의 AudioSource.spatialize 속성을 사용하도록 설정할 때 이 Spatializer 플러그 인이 사용됩니다. 이 항목에 대한 자세한 정보는 <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">공간 오디오 자습서</a>를 참조하세요.

프로젝트 설정 창에서 **플레이어** > **XR 설정** 을 선택한 다음, **Depth Format**(수준 형식) 드롭다운을 사용하여 **16비트 수준** 을 선택합니다.

![Unity 16 깊이 사용](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> Depth Format을 16비트로 줄이는 것은 선택 사항이지만, 프로젝트에서 그래픽 성능을 향상시킬 수 있습니다. 이 항목에 대한 자세한 정보는 MRTK의 성능 설명서의 <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">깊이 버퍼 공유(HoloLens)</a> 섹션을 참조하세요.

프로젝트 설정 창에서 **플레이어** > **게시 설정** 을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.

![Unity 게시 설정. 구성된 패키지 이름](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> '패키지 이름'은 앱의 고유 식별자입니다. 이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.

> [!TIP]
> '제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다. 개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.
