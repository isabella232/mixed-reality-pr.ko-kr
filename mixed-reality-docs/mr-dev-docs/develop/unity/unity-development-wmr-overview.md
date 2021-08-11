---
title: VR용 Unity 개발
description: VR 및 Windows Mixed Reality 몰입형 헤드셋에 대해 Unity에서 혼합 현실 앱 빌드를 시작합니다.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, 포팅, 기능, 카메라, 시뮬레이션, 에뮬레이션, 설명서, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 가상 현실이란, 증강 현실이란, MRTK, mixed reality toolkit, 음성 입력, 위치를 찾을 수 있는 카메라, 에뮬레이터, Azure, 자습서
ms.openlocfilehash: 74ac1825d8b94ba65075ef96244759ec0c8dcf1891556e0a1f36f100b9615221
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211691"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a>VR 및 Windows Mixed Reality용 Unity 개발

![Unity 배너 로고](../images/unity_logo_banner.png)

Unity를 처음 접하는 경우 계속하기 전에 Unity 학습 플랫폼에서 초보자 수준 [자습서](https://unity3d.com/learn/tutorials)를 살펴보는 것이 좋습니다. 또한 [Unity Mixed Reality 포럼](https://forum.unity3d.com/forums/hololens.102/)을 방문하여 혼합 현실 앱을 빌드하는 온라인 커뮤니티에 참여하는 것도 좋습니다. 거친 세계에서는 어떤 멋진 자산 또는 솔루션을 찾을 수 있는지 전혀 알 수 없습니다. MRTK를 시작할 준비가 되면 아래 개발 검사점으로 이동하세요!

> [!IMPORTANT]
> Windows Mixed Reality 몰입형 헤드셋으로 가져오려는 기존 Unity 프로젝트가 있는 경우 **[포트 가이드](../porting-apps/porting-overview.md)** 를 살펴보세요. 

## <a name="development-checkpoints"></a>개발 검사점

다음 검사점을 사용하여 Unity 게임 및 애플리케이션을 혼합 현실 세계로 가져옵니다.

### <a name="1-getting-started"></a>1. 시작

Windows Mixed Reality 및 VR 개발을 위해 수동으로 변경해야 하는 몇 가지 Unity 설정 집합이 있습니다. 이러한 설정은 두 가지 범주, 즉 프로젝트별 및 장면별 범주로 구분됩니다. 이 섹션을 마치면 도구와 프로젝트 설정을 통해 자신만의 앱을 만들 수 있습니다!

|  검사점  |  결과  |
| --- | --- |
| [최신 도구 설치](../install-the-tools.md) | 최신 Unity 패키지를 다운로드 및 설치하고, 혼합 현실에 맞게 프로젝트를 설정합니다. |
| [VR 및 Windows Mixed Reality 헤드셋을 위한 프로젝트 구성](./xr-project-setup.md?tabs=openxr) | 홀로그램 및 VR 디스플레이 디바이스에서 디지털 콘텐츠를 렌더링하는 애플리케이션을 빌드하는 방법에 대해 알아봅니다. |

> [!IMPORTANT]
> 프로젝트 설정에 대한 자세한 내용은 Unity 프로젝트 [구성 가이드](choosing-unity-version.md)를 참조하세요.

### <a name="2-core-building-blocks"></a>2. 핵심 구성 요소

새로운 몰입형 프로젝트를 시작한 후에는 몰입형 앱을 개발하기 위해 몇 가지 기본 구성 요소가 필요합니다. 혼합 현실 애플리케이션의 모든 핵심 구성 요소는 다른 Unity API와 일치하는 방식으로 공개됩니다. 한 번에 모두 필요하지 않을 수도 있지만 일찍 살펴보는 것이 좋습니다. 아래에 나열된 핵심 구성 요소를 살펴본 후 VR 프로젝트에 통합할 수 있는 모든 기능을 갖춘 도구 상자를 사용할 수 있습니다.

|  기능  |  기능  |
| --- | --- |
| [카메라](../unity/camera-in-unity.md) | Mixed Reality 앱에서 시각적 품질 및 홀로그램 안정성을 완벽하게 최적화 |
| [세계 잠금 및 공간 앵커](spatial-anchors-in-unity.md) | 안정화 문제 해결, 카메라 조정 및 안정적인 좌표계 솔루션 통합 || [모션 컨트롤러](../unity/motion-controllers-in-unity.md) | 혼합 현실 앱에 공간 작업 추가 |
| [제스처](../unity/gestures-in-unity.md) | 혼합 현실 경험에서 손 제스처를 입력으로 사용 |
| [공간 음향](../unity/spatial-sound-in-unity.md) | 몰입형 3D 오디오를 사용하여 앱 향상 |
| [Text](../unity/text-in-unity.md) | 관리 가능한 크기 및 품질 렌더링을 사용하는 선명한 고품질 텍스트 가져오기 |
| [음성 입력 ](../unity/voice-input-in-unity.md) | 사용자의 음성 키워드, 구 및 받아쓰기 캡처|

### <a name="3-advanced-features"></a>3. 고급 기능

몰입형 애플리케이션에서 역할을 수행하는 다른 주요 기능은 추가 패키지 또는 설정 없이 Unity API를 통해 사용할 수 있습니다. Unity에서 제공하는 고급 기능을 자세히 살펴본 후에는 더 깊고 복잡한 VR 앱을 빌드할 수 있습니다.

|  기능  |  기능  |
| --- | --- |
| [추적 손실](tracking-loss-in-unity.md) | 디바이스가 애플리케이션 세계 공간에서 자체를 찾을 수 없는 시나리오를 처리합니다. |
| [키보드 입력](keyboard-input-in-unity.md) | 현실 세계 및 Mixed Reality 키보드의 입력을 앱에 가져옵니다. |

### <a name="4-deploying-to-a-device-or-emulator"></a>4. 디바이스 또는 에뮬레이터에 배포

홀로그램 Unity 프로젝트를 테스트할 준비가 되면 다음 단계로 Unity Visual Studio 솔루션을 내보내고 빌드합니다. 해당 VS 솔루션을 직접 사용하는 경우 실제 또는 시뮬레이션된 디바이스에서 애플리케이션을 실행할 수 있습니다. 이 섹션이 완료되면 개발 요구 사항에 맞는 디바이스 또는 에뮬레이터에 애플리케이션을 배포할 수 있습니다.

* [Windows Mixed Reality 몰입형 헤드셋](../platform-capabilities-and-apis/using-visual-studio.md)
* [Windows Mixed Reality 몰입형 헤드셋 시뮬레이터](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a>다음 작업

특히 새 도구 또는 SDK를 학습하는 경우 개발자 작업이 수행되지 않습니다. 다음 섹션에서는 이미 완료한 초보자 수준 자료와 중단되는 경우 유용한 리소스 영역으로 모두 안내할 수 있습니다. 이러한 항목과 리소스는 순차적이지 않으므로 자유롭게 이동하여 살펴보세요!

### <a name="porting"></a>포팅

포팅하려는 기존 앱이 있는 경우 아래 나열된 문서가 다음 단계입니다.

* [VR 앱을 Windows Mixed Reality로 포팅](../porting-apps/porting-guides.md?tabs=project)
* [Windows Mixed Reality용 SteamVR 앱 업데이트](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a>추가 자료

혼합 현실 세계로 직접 들어가기 전에 아래에 나열된 추가 설명서를 살펴보는 것이 좋습니다. 

* [VR 마니아 가이드](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [Unity 자산 스토어](https://assetstore.unity.com)

## <a name="see-also"></a>참조 

* [Unity 권장 설정](recommended-settings-for-unity.md)
* [Unity의 권장 성능](performance-recommendations-for-unity.md)
* [Unity Visual Studio 솔루션 내보내기 및 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [Unity 및 Visual Studio 사용 모범 사례](best-practices-for-working-with-unity-and-visual-studio.md)