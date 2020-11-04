---
title: Unreal 개발 개요
description: Unreal Engine 4를 사용하는 혼합 현실 개발의 개요
author: hferrone
ms.author: v-hferrone
ms.date: 08/04/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 스트리밍, 원격, 혼합 현실, 개발, 시작, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 특징, 홀로그램, 게임 개발
ms.openlocfilehash: 25842fb8083b7757e73e7dbe7551b6bde9d8d95e
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638590"
---
# <a name="unreal-development-overview"></a>Unreal 개발 개요

![Unreal 배너 로고](../images/unreal_logo_banner.png)

<a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="혼합 현실 문서"> 혼합 현실 애플리케이션</a>의 시작은 방대한 작업입니다. 새로운 개념, 플랫폼 및 최첨단 하드웨어가 장애물처럼 느껴질 수 있습니다. 그러나 Unreal 개발자라면 운이 좋습니다. <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality 문서">Windows Mixed Reality</a>(VR) 및 <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="HoloLens 2 문서">HoloLens 2</a>(AR)에 이제 Unreal Engine의 최신 <a href="https://docs.unrealengine.com/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Unreal Engine 4.25 릴리스 정보"> 릴리스</a>가 포함되었습니다. 이 업데이트의 내용은 다음과 같습니다.
* Mixed Reality UX Tools 플러그 인 지원
* OpenXR 지원
* 데스크톱 앱의 앱 원격 작업
* 성능 향상
* 혼합 현실 캡처
* Azure Spatial Anchors 초기 지원

Unreal 개발이 처음이라면 모르는 상태에서 넘어가지 마세요. Unreal <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">자습서 시리즈</a>를 탐색하여 필요한 지식을 갖추고 Unreal <a href="https://www.unrealengine.com/marketplace/store" target="_blank">마켓플레이스</a> 및 혼합 현실 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">포럼</a>에서 자산 및 지원을 모색합니다. 이러한 리소스를 통해 오늘날의 혼합 현실 시장에서 구축자와 문제 해결자 커뮤니티에 연결할 수 있습니다.

> [!IMPORTANT]
> 기존 Unreal 프로젝트를 HoloLens 2 또는 Reverb G2 같은 몰입형 헤드셋으로 가져오려면 **[포팅 가이드](../porting-apps/porting-overview.md)** 를 살펴보세요.

## <a name="development-checkpoints"></a>개발 검사점

다음 검사점을 사용하여 Unreal 게임과 애플리케이션을 혼합 현실 세계로 가져옵니다. [Holograms 샘플 애플리케이션 디자인](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)을 아직 살펴보지 않았다면 이를 다운로드하여 Mixed Reality UX의 기본 사항을 숙지하는 데 사용하는 것이 좋습니다.

### <a name="1-getting-started"></a>1. 시작

[Unreal용 Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unreal)는 Unreal에서의 개발 속도를 높이도록 설계된 구성 요소의 세트입니다. 각 구성 요소에는 몰입형 환경 설정을 위한 플러그 인, 샘플, 설명서가 포함되어 있습니다.

* [Unreal UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal)는 릴리스된 첫 번째 구성 요소이며 현재 HoloLens 2에서만 지원됩니다. 구성 요소 플러그 인에는 입력 시뮬레이션, 손 조작 행위자, 누를 수 있는 단추 구성 요소, 따르기 동작 구성 요소를 위한 일반 UX 기능의 코드, 청사진 및 예제 자산이 포함됩니다.

이 섹션을 마치면 Mixed Reality Toolkit, Mixed Reality 앱을 위해 적절하게 구성된 개발 환경, Unreal에서 작동하는 MRTK 프로젝트에 대한 기본적인 이해가 이루어질 것입니다.

|  검사점  |  결과  |
| --- | --- |
| [최신 도구 설치](../install-the-tools.md) | 최신 Unity 패키지를 다운로드 및 설치하고, 혼합 현실에 맞게 프로젝트를 설정합니다. |
| [HoloLens 2 자습서 시리즈](tutorials/unreal-uxt-ch1.md) | HoloLens 2 하드웨어에 대한 초보자 수준 MRTK 자습서 살펴보기 |

### <a name="2-core-building-blocks"></a>2. 핵심 구성 요소

자습서 시리즈에서 다루지 않은 혼합 현실 개발의 몇 가지 핵심 기능을 제공합니다. 이러한 구성 요소는 독립 실행형 기능 및 Mixed Reality Toolkit을 통해 사용할 수 있습니다. 한 번에 모두 필요하지는 않지만 조기에 탐색하는 것이 좋습니다. 아래에 나열된 핵심 구성 요소를 살펴본 후 Mixed Reality 프로젝트에 통합할 수 있는 모든 기능을 갖춘 도구 상자를 사용할 수 있습니다.

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> 자세한 내용은 **[Unreal GitHub용 UX 도구](https://github.com/microsoft/MixedReality-UXTools-Unreal)** 리포지토리를 살펴보세요.

### <a name="3-platform-capabilities-and-apis"></a>3. 플랫폼 기능 및 API

혼합 현실 애플리케이션에서 역할을 수행하는 다른 주요 기능은 추가 패키지나 설정 없이 사용할 수 있습니다. 이러한 기능은 MRTK가 설치되거나 설치되지 않은 Unreal 프로젝트에 추가할 수 있습니다. 이러한 고급 기능을 파악한 후에는 더 복잡한 Mixed Reality 앱을 빌드할 수 있습니다.

|  기능  |  기능  |
| --- | --- |
| [HoloLens 카메라](unreal-hololens-camera.md) | HoloLens 디바이스에서 실행되는 앱에서 Mixed Reality 및 실제 시각적 콘텐츠 캡처 |
| [QR 코드](unreal-qr-codes.md) | 각 코드의 실제 위치에서 좌표계를 사용하여 QR 코드를 홀로그램으로 렌더링 |
| [WinRT](unreal-winrt.md) | Unreal의 빌드 시스템에서 사용할 수 있는 WinRT 코드를 통해 별도의 이진 파일을 만듭니다. |

### <a name="4-deploying-to-a-device"></a>4. 디바이스에 배포

HoloLens용 Unreal 앱을 처음으로 만들거나 배포하는 경우 Epic Launcher에서 [지원 파일을 다운로드](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)해야 합니다. 이러한 파일을 설치했으면 [Unreal 편집기](unreal-deploying.md) 또는 [장치 포털](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)에서 배포할 준비가 된것입니다.

### <a name="5-adding-services"></a>5. 서비스 추가

개발 과정의 이 시점에서 서비스를 추가하거나 상업적 배포에 도움을 받을 수 있습니다. [Azure Cloud Services](../mixed-reality-cloud-services.md) 및 Dynamics 365 기능을 통합하면 프로젝트 수준을 주요 방식으로 높일 수 있습니다. Mixed Reality 지식을 탐색하고 확장할 수 있는 몇 가지 시작점을 컴파일했습니다.

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>다음 작업

특히 새 도구 또는 SDK를 학습하는 경우 개발자 작업이 수행되지 않습니다. 다음 섹션에서는 이미 완료한 초보자 수준 자료를 벗어난 영역으로 안내할 수 있으며, 어려움이 있을 때 유용한 리소스로 안내할 수 있습니다. 이러한 항목과 리소스는 순차적으로 정렬되지 않으므로 자유롭게 이동하여 탐색하세요.

### <a name="streaming--debugging"></a>스트리밍 및 디버깅

아직 개발 중인 HoloLens 디바이스에서 애플리케이션을 테스트하려면 Unreal 편집기나 패키지된 Windows 실행 파일을 사용하여 [PC에서 직접 스트리밍](unreal-streaming.md)할 수 있습니다.

Visual Studio를 사용하여 애플리케이션을 디버깅하려면 다음 [지침](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package#remote)을 따르세요.

### <a name="performance"></a>성능

혼합 현실 개발에서는 플랫폼에 따라 성능 체크포인트가 있습니다. 홀로그램이 안정적이고 표시되고 빠르게 응답하려면 HoloLens 2 앱이 초당 60프레임으로 실행되어야 합니다. 다행히 Unreal 애플리케이션에서 이를 달성하기 위한 [성능 권장 사항](performance-recommendations-for-unreal.md)이 있습니다.

## <a name="supported-features"></a>지원되는 기능

| HoloLens 2 기능 | 지원되는 가장 빠른 Unreal Engine 버전 |
| ----------- | ----------- |
| ARM64 지원 | 4.23 |
| PC에서 스트리밍 | 4.23 |
| 공간 매핑 | 4.23 |
| 손 및 관절 추적 | 4.23 |
| 시선 추적 | 4.23 |
| 음성 입력 | 4.23 |
| 공간 앵커 | 4.23 |
| 카메라 액세스 | 4.23 |
| QR 코드 | 4.23 |
| 공간 오디오 | 4.23 |
| 스트리밍을 위한 관람자 화면 지원 | 4.24 |
| 스트리밍을 통한 평면 LSR | 4.24 |
| 샘플 앱([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) 및 [Mission AR](https://docs.unrealengine.com/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| 모바일 다중 보기: 60FPS 성능 도달 | 4.25 |
| 세 번째 카메라 렌더링 | 4.25 |
| 패키지 데스크톱 앱에서 스트리밍 | 4.25.1 |
| Azure Spatial Anchors for HoloLens 2(베타) | 4.25 |
| OpenXR 지원(베타) | 4.25 |
| UX Tools 지원(0.8) | 4.25 |
| 개발자 문서 및 자습서 | 4.25 |

> [!div class="nextstepaction"]
> [도구 설치](../install-the-tools.md)

## <a name="see-also"></a>참고 항목
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">에뮬레이터 및 디바이스에 스트리밍 및 배포하는 방법에 대한 Unreal 문서</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">모바일 디바이스에 대한 Unreal 성능 지침</a>
