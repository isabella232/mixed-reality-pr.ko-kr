---
title: 엔진 선택
description: HoloLens 및 VR용 Mixed Reality 개발에 사용할 수 있는 엔진 선택 항목을 소개합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: c91a4df9db8ef71778421750bca48d81d4b4a02e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394527"
---
# <a name="choosing-your-engine"></a>엔진 선택

설명서를 통해 선택할 수 있는 몇 가지 개발 경로가 있습니다. 첫 번째 단계는 자신에게 맞는 기술을 찾는 것입니다. 이미 선택했다면 아래에 있는 해당 탭으로 바로 이동하세요. 아직 선택하지 못했거나 막 시작했다면, 각각의 도구를 살펴보면서 제공하는 기능, 사용 가능한 플랫폼 및 도구를 이해한 후 만들기 시작하세요!

> [!IMPORTANT]
> 기존 프로젝트를 HoloLens 2 또는 Reverb G2 같은 몰입형 VR 헤드셋으로 가져오려면 **[포팅 가이드 개요](porting-apps/porting-overview.md)** 를 살펴보세요. HTK, MRTK v1, SteamVR을 사용하거나 Oculus Greff 또는 HTC Vive와 같은 몰입형 헤드셋용으로 개발된 프로젝트에 대한 가이드가 있습니다.

## <a name="engine-overview"></a>엔진 개요

* **Unity는** C++로 작성된 기본 런타임 코드를 사용하여 시장에서 최고의 실시간 개발 플랫폼 중 하나이며 모든 개발 스크립팅은 C#에서 수행됩니다. Unity는 게임, 영화 및 애니메이션 영화 예술을 빌드하거나 건축 또는 엔지니어링 개념을 가상 세계에 렌더링하려는 사용자를 지원할 수 있는 인프라를 갖추고 있습니다.

* **Unreal Engine 4는** C++ 및 Blueprints 모두에서 혼합 현실에 대한 완전한 지원을 갖춘 강력한 오픈 소스 생성 엔진입니다. Unreal Engine 4.25부터 HoloLens 지원은 전체 기능을 갖추고 프로덕션 준비가 되어 있습니다. 유연한 청사진 시각적 스크립팅 시스템과 같은 기능이 제공되므로 디자이너는 일반적으로 프로그래머만 사용할 수 있는 모든 개념과 도구를 가상으로 사용할 수 있습니다. 모든 산업의 크리에이터는 자유로우면서도 통제된 환경을 활용하여 최첨단 콘텐츠, 대화형 환경 및 몰입형 가상 환경을 제공할 수 있습니다.

* 고유한 3D 렌더러를 작성한 경험이 있는 **네이티브** 개발자는 OpenXR을 사용하여 사용자 지정 엔진을 빌드할 수 있습니다. OpenXR은 Khronos의 로열티 없는 개방형 API 표준이며, 혼합 현실 스펙트럼 전반의 광범위한 벤더 디바이스에 대한 네이티브 액세스를 엔진에 제공합니다. 데스크톱의 Windows Mixed Reality 몰입형 헤드셋 또는 HoloLens 2에서 OpenXR을 사용하여 개발할 수 있습니다.

* 매력적인 브라우저 간 AR/VR 웹 환경을 만드는 웹 **개발자는** **WebXR을** 사용할 수 있습니다.

    > [!NOTE]
    > HoloLens 개발을 위한 **Babylon.js** 현재 진행 중입니다. 최신 뉴스를 확인하고 [커뮤니티에 참여하세요!](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR)

<!-- Babylon is a Javascript-based, open source, 3D graphics engine capable of powering 3D scenes in a web browser. Babylon.js 4.2+ includes support for WebXR. With Babylon React Native, you can even build cross-platform native     applications for PC, mobile, and mixed reality devices. -->

## <a name="features-and-devices"></a>기능 및 디바이스

<br>

| 물류 | Unity | Unreal | JavaScript | 사용자 지정 엔진 <br>(OpenXR 사용) |
|---|---|---|---|---|
| 언어 | C# | C++ | JavaScript | C/C++ |
| 가격 책정 | [Unity 가격 책정](https://store.unity.com/#plans-individual) | [Unreal 가격 책정](https://www.unrealengine.com/download) | 무료 | 무료 |

<br>

| 디바이스 기능 | Unity | Unreal | JavaScript | 사용자 지정 엔진 <br>(OpenXR 사용) |
|---|---|---|---|---|
| 디바이스/디스플레이 추적 | ✔️ | ✔️ | ✔️ | ✔️ |
| 손 입력 | ✔️ | ✔️ | ✔️ | ✔️ |
| 눈 입력 | ✔️ | ✔️ | ❌ | ✔️ |
| 음성 입력 | ✔️ | ✔️ | ✔️ | ✔️ |
| 모션 컨트롤러 | ✔️ | ✔️ | ✔️ | ✔️ |
| 평면/메시 적중 테스트 | ✔️ | ✔️ | ✔️ | ✔️ |
| 장면 이해 | ✔️ | ✔️ | ❌ | ✔️ |
| 공간 음향 | ✔️ | ✔️ | ✔️ | ✔️ |
| QR 코드 검색 | ✔️ | ✔️ | ❌ | ✔️ |

<br>

| 하드웨어 | Unity | Unreal | JavaScript | 사용자 지정 엔진 <br>(OpenXR 사용) |
|---|---|---|---|---|
| HoloLens 2 | ✔️ | ✔️ | ✔️ | ✔️ |
| HoloLens(1세대) | ✔️ | ✔️ | ❌ | WinRT (레거시)만 |
| [Windows Mixed Reality 헤드셋](../discover/immersive-headset-hardware-details.md) | ✔️ | ✔️ | ✔️ | ✔️ |
| SteamVR 헤드셋 | ✔️ | ✔️ | ✔️ | ✔️ |
| Oculus Quest/Rift | ✔️ | ✔️ | ✔️ | ✔️ |
| 모바일 (ARCore/Arcore) | ✔️ | ✔️ | ✔️ | ❌ |

<br>

| 도구 | Unity | Unreal | JavaScript | 사용자 지정 엔진 <br>(OpenXR 사용) |
|---|---|---|---|---|
| Mixed Reality Toolkit | ✔️ | ✔️ | ❌  | ❌ |
| 세계 잠금 도구 | ✔️ | ❌ | ❌  | ❌ |
<!-- | 메시 | ❌ | ❌ | ❌ | ❌ | -->

<br>

| Cloud Services | Unity | Unreal | JavaScript | 사용자 지정 엔진 <br>(OpenXR 사용) |
|---|---|---|---|---|
| Azure Spatial Anchors | ✔️ | ✔️ | ❌ | ✔️ |
| Azure Object Anchors | ✔️ | ❌ | ❌ | ✔️ |
| Azure Remote Rendering | ✔️ * | ❌ | ❌ | ✔️ * |

> [!NOTE]
> * Azure 원격 렌더링은 현재 레거시 WinRT Api (Unity의 Windows XR plugin)를 사용 하는 앱에서 지원 됩니다. OpenXR apps에 대 한 ARR 지원이 곧 제공 될 예정입니다.

## <a name="next-steps"></a>다음 단계

[!INCLUDE[](includes/tools-next-steps.md)]