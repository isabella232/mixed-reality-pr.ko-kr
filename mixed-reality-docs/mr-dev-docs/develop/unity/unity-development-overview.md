---
title: HoloLens용 Unity 개발
description: 큐레이트된 검사점 경험을 통해 Unity 및 HoloLens에서 혼합 현실 앱 빌드를 시작합니다.
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, 포팅, 기능, 카메라, 시뮬레이션, 에뮬레이션, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 가상 현실이란, 증강 현실이란, MRTK, mixed reality toolkit, 공간 매핑, 음성 입력, 위치를 찾을 수 있는 카메라, 에뮬레이터, Azure, 자습서
ms.openlocfilehash: f47e37f56f203590a16ec804c4a36a6ac601ec61cb2f3b7dfb69987d411eef15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202871"
---
# <a name="unity-development-for-hololens"></a>HoloLens용 Unity 개발

![Unity 배너 로고](../images/unity_logo_banner.png)

Unity는 시장을 선도하는 실시간 개발 플랫폼 중 하나로, C++로 작성된 기본 런타임 코드를 제공하며 모든 개발 스크립팅이 C#에서 수행됩니다. Unity는 게임, 영화 및 애니메이션 영화 예술을 빌드하거나 건축 또는 엔지니어링 개념을 가상 세계에 렌더링하려는 사용자를 지원할 수 있는 인프라를 갖추고 있습니다. 시작할 준비가 되면 아래 개발 검사점으로 이동하세요!

> [!IMPORTANT]
> HoloLens 2로 가져오려는 기존 Unity 프로젝트가 있는 경우 **[포트 가이드](../porting-apps/porting-overview.md)** 를 살펴보세요. HTK, MRTK v1 또는 SteamVR을 사용하는 프로젝트에 대한 가이드가 있습니다.

## <a name="development-checkpoints"></a>개발 검사점

다음 검사점을 사용하여 Unity 게임 및 애플리케이션을 혼합 현실 세계로 가져옵니다. [Holograms 샘플 애플리케이션 디자인](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)을 아직 살펴보지 않았다면 이를 다운로드하여 Mixed Reality UX의 기본 사항을 숙지하는 데 사용하는 것이 좋습니다.

## <a name="1-getting-started"></a>1. 시작

Unity에서 개발하는 가장 쉬운 방법은 Mixed Reality Toolkit를 사용하는 것입니다. MRTK는 Mixed Reality 프로젝트를 자동으로 설정하고, 개발 프로세스를 가속화할 수 있는 기능 세트를 제공하는 데 도움이 됩니다. 이 섹션이 완료되면 Mixed Reality Toolkit, Mixed Reality 앱에 맞게 적절하게 구성된 개발 환경 및 직접 빌드한 Unity에서 작동하는 MRTK 프로젝트에 대해 기본적으로 이해할 수 있게 됩니다.

|  검사점  |  결과  |
| --- | --- |
| [Mixed Reality Toolkit 소개](mrtk-getting-started.md) | Mixed Reality Toolkit 및 이 도구 키트에서 제공해야 하는 항목을 숙지하여 과정을 시작합니다. |
| [Mixed Reality Feature Tool 다운로드](welcome-to-mr-feature-tool.md) | 혼합 현실 기능 패키지를 검색, 업데이트하고 Unity 프로젝트에 추가하는 데 사용되는 새로운 개발자 도구입니다. |
| [개발자 환경 설정](../install-the-tools.md) | 최신 Unity 패키지를 다운로드 및 설치하고, 혼합 현실에 맞게 프로젝트를 설정합니다. |
| [HoloLens 2 자습서 시리즈 완료](tutorials/mr-learning-base-01.md) | HoloLens 2 하드웨어에 대한 초보자 수준 MRTK 자습서를 살펴봅니다. |

> [!IMPORTANT]
> Mixed Reality Toolkit를 가져오지 않고 새 Unity 프로젝트를 만들려면 Windows Mixed Reality에 대해 수동으로 변경해야 하는 작은 Unity 설정 세트가 있습니다. 자세한 내용은 [구성 가이드](choosing-unity-version.md)를 참조하세요.

> [!NOTE]
> 프로젝트에서 MRTK가 설정되면 카메라와 같은 표준 Unity 게임 개체가 즉시 점등되어 좌석 크기의 환경을 제공합니다. 애플리케이션의 환경 크기를 조정하는 방법은 [좌표계](coordinate-systems-in-unity.md) 페이지에서 확인할 수 있습니다.

## <a name="2-core-building-blocks"></a>2. 핵심 구성 요소

혼합 현실 애플리케이션의 모든 핵심 구성 요소는 다른 Unity API와 일치하는 방식으로 공개됩니다. 이러한 구성 요소는 독립 실행형 기능으로 사용하거나 Mixed Reality Toolkit를 통해 사용할 수 있습니다. 한 번에 모두 필요하지 않을 수도 있지만 일찍 살펴보는 것이 좋습니다. 아래에 나열된 핵심 구성 요소를 살펴보았으면 자체적으로 또는 MRTK를 통해 Mixed Reality 프로젝트에 통합할 수 있는 모든 기능을 갖춘 도구 상자를 사용할 수 있습니다.

|  기능  |  기능  |
| --- | --- |
| [카메라](../unity/camera-in-unity.md) | Mixed Reality 앱에서 시각적 품질 및 홀로그램 안정성을 완벽하게 최적화 |
| [세계 잠금 및 공간 앵커](spatial-anchors-in-unity.md) | 안정화 문제 해결, 카메라 조정 및 안정적인 좌표계 솔루션 통합 |
| [공유 환경](shared-experiences-in-unity.md) | 공간 앵커 공유를 사용하여 공간의 고정 지점에서 동일한 홀로그램을 보고 집합적으로 상호 작용합니다. |
| [응시](../unity/gaze-in-unity.md) | 사용자가 홀로그램을 확인하여 대상으로 할 수 있습니다. |
| [모션 컨트롤러](../unity/motion-controllers-in-unity.md) | 혼합 현실 앱에 공간 작업 추가 |
| [제스처](../unity/gestures-in-unity.md) | 혼합 현실 경험에서 손 제스처를 입력으로 사용 |
| [손 및 시선 추적](../unity/hand-eye-in-unity.md) | 연결된 손 및 시선 추적 입력을 사용자 환경에 통합 |
| [공간 매핑](../unity/spatial-mapping-in-unity.md) | 가상 메시 오버레이를 사용하여 실제 공간을 매핑하여 환경 경계 표시 |
| [공간 음향](../unity/spatial-sound-in-unity.md) | 몰입형 3D 오디오를 사용하여 앱 향상 |
| [Text](../unity/text-in-unity.md) | 관리 가능한 크기 및 품질 렌더링을 사용하는 선명한 고품질 텍스트 가져오기 |
| [음성 입력 ](../unity/voice-input-in-unity.md) | 사용자의 음성 키워드, 구 및 받아쓰기 캡처|

## <a name="3-advanced-features"></a>3. 고급 기능

혼합 현실 애플리케이션에서 역할을 수행하는 다른 주요 기능은 추가 패키지 또는 설정 없이 Unity API를 통해 사용할 수 있습니다. 이러한 기능은 MRTK의 설치 여부에 관계없이 Unity 프로젝트에 추가할 수 있습니다. Unity에서 제공하는 고급 기능을 자세히 살펴보았으면 더 깊고 복잡한 Mixed Reality 앱을 빌드할 수 있습니다.

|  기능  |  기능  |
| --- | --- |
| [사진 비디오 카메라](locatable-camera-in-unity.md) | Mixed Reality 애플리케이션에서 사진 및 비디오 콘텐츠를 캡처합니다. |
| [포커스 지점](focus-point-in-unity.md) | 현재 표시 중인 홀로그램에서 안정화를 가장 효율적으로 수행하는 방법에 대한 힌트를 HoloLens에 제공합니다. |
| [추적 손실](tracking-loss-in-unity.md) | 디바이스가 애플리케이션 세계 공간에서 자체를 찾을 수 없는 시나리오를 처리합니다. |
| [키보드 입력](keyboard-input-in-unity.md) | 현실 세계 및 Mixed Reality 키보드의 입력을 앱에 가져옵니다. |

## <a name="4-deploying-to-a-device-or-emulator"></a>4. 디바이스 또는 에뮬레이터에 배포

홀로그램 Unity 프로젝트를 테스트할 준비가 되면 다음 단계로 Unity Visual Studio 솔루션을 내보내고 빌드합니다. 해당 VS 솔루션을 직접 사용하는 경우 실제 디바이스 또는 시뮬레이션된 디바이스에서 다음 세 가지 방법 중 하나로 애플리케이션을 실행할 수 있습니다. 이 섹션이 완료되면 개발 요구 사항에 맞는 디바이스 또는 에뮬레이터에 애플리케이션을 배포할 수 있습니다.

* [HoloLens 또는 Windows Mixed Reality 몰입형 헤드셋](../platform-capabilities-and-apis/using-visual-studio.md)
* [HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Windows Mixed Reality 몰입형 헤드셋 시뮬레이터](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="5-adding-services"></a>5. 서비스 추가

개발 과정의 이 시점에서 서비스를 추가하거나 상업적 배포에 도움을 받을 수 있습니다. [Azure Cloud Services](../mixed-reality-cloud-services.md)를 통합하면 주요 방식으로 프로젝트 수준을 높일 수 있습니다. Mixed Reality 지식을 검색하고 확장할 수 있는 몇 가지 시작 지점을 컴파일했습니다.

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

또한 자체 서비스를 기반으로 하여 Unity 프로젝트에 추가할 수 있는 [추가 Azure 서비스에 대한 포괄적인 지원 설명서 목록](../mixed-reality-cloud-services.md#standalone-unity-services)이 있습니다.

## <a name="6-low-code-alternatives"></a>6. 로우 코드 대안

[!INCLUDE[](../includes/unity-low-code.md)]

## <a name="whats-next"></a>다음 작업

특히 새 도구 또는 SDK를 학습하는 경우 개발자 작업이 수행되지 않습니다. 다음 섹션에서는 이미 완료한 초보자 수준 자료와 중단되는 경우 유용한 리소스 영역으로 모두 안내할 수 있습니다. 이러한 항목과 리소스는 순차적이지 않으므로 자유롭게 이동하여 살펴보세요!

### <a name="porting"></a>포팅

포팅하려는 기존 앱이 있는 경우 아래 나열된 문서가 다음 단계입니다.

* [HoloToolkit/MRTK에서 MRTK v2로](../porting-apps/porting-hl1-hl2.md)
* [몰입형 앱 포팅 가이드](../porting-apps/porting-guides.md)
* [입력 포팅 가이드](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a>자습서

특정 Mixed Reality 기능을 애플리케이션에 추가하려는 경우 엔드투엔드 프로세스를 실행할 수 있는 몇 가지 큐레이팅된 자습서가 있습니다. 가장 인기 있는 HoloLens 2 및 HoloLens(1세대) 콘텐츠가 아래에 나열되어 있지만, 자습서 개요를 방문하면 전체 컬렉션을 확인할 수 있습니다.

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a>추가 리소스

혼합 현실 세계로 직접 들어가기 전에 아래에 나열된 MRTK 관련 설명서를 살펴보는 것이 좋습니다. 이러한 문서는 MRTK가 작동하는 방법을 더 자세히 이해하기 위한 훌륭한 출발 지점이며, 앱을 성능 기준에 맞게 만드는 데 적합한 인사이트를 제공합니다.

|  항목  |  Description  |
| --- | --- |
| [MRTK 아키텍처 개요](/windows/mixed-reality/mrtk-unity/architecture/overview) | MRTK SDK가 프로젝트에서 작동하는 방법을 더 자세히 이해합니다. |
| [설정 및 성능](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started) | 앱을 프로파일링하고, Unity 설정을 업데이트하고, 최상의 홀로그램 안정화 성능을 제공합니다. |
| [MRTK + XR 시작](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk) | Unity에서 제공하는 대체 XR 파이프라인으로 전송합니다. |

### <a name="unity-resources"></a>Unity 리소스

Unity는 docs.microsoft.com에서 사용할 수 있는 이 설명서 외에도 Windows Mixed Reality 기능에 대한 설명서를 Unity 편집기와 함께 설치합니다. Unity에서 제공하는 설명서에는 별도의 다음 두 가지 섹션이 있습니다.

|  리소스  |  Description  |
| --- | --- |
| [스크립팅 참조](https://docs.unity3d.com/ScriptReference/) | 설명서의 이 섹션에는 Unity에서 제공하는 스크립팅 API에 대한 세부 정보가 포함되어 있으며, **도움말 > 스크립팅 참조** 를 차례로 클릭하여 Unity 편집기에서 온라인으로 액세스할 수 있습니다. |
| [수동](https://docs.unity3d.com/Manual/index.html) | 이 설명서는 기본 기술에서 고급 기술까지 Unity를 사용하는 방법을 학습하는 데 도움이 되도록 설계되었으며, 온라인 또는 Unity 편집기에서 **도움말 > 수동** 을 차례로 클릭하여 액세스할 수 있습니다. |

> [!div class="nextstepaction"]
> [MRTK 살펴보기](mrtk-getting-started.md)

## <a name="have-feedback"></a>의견이 있으신가요?

[Unity 포럼](https://aka.ms/unityforums)에서 **Microsoft** 를 태그로 지정하면 당사를 찾을 수 있으며 다음 태그를 조합하면 귀하가 피드백을 제공하는 플러그 인이 무엇인지 당사가 파악하는 데 도움이 됩니다.

* HoloLens 2 
* Windows Mixed Reality
* OpenXR
* XRSDK
* Legacy XR

## <a name="see-also"></a>참고 항목

* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [MR 기본 100: Unity 시작](tutorials/holograms-100.md)
* [Unity 권장 설정](recommended-settings-for-unity.md)
* [Unity의 권장 성능](performance-recommendations-for-unity.md)
* [Unity Visual Studio 솔루션 내보내기 및 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [HoloLens용 Unity 앱에서 Windows 네임스페이스 사용](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Unity 및 Visual Studio 사용 모범 사례](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 플레이 모드](unity-play-mode.md)
* [포팅 가이드](../porting-apps/porting-guides.md)
