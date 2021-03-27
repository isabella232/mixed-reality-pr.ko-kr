---
title: Unity에서 카메라 설정
description: Holographic 렌더링을 수행 하기 위해 Windows Mixed Reality 개발용 Unity의 기본 카메라를 설정 하 고 사용 하는 방법에 대해 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, holographic 렌더링, holographic, 몰입 형, 포커스 지점, 깊이 버퍼, 방향 전용, 위치, 불투명, 투명, 클립, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636306"
---
# <a name="camera-setup-in-unity"></a>Unity에서 카메라 설정

혼합 현실 헤드셋을 착용 하면 holographic 세계의 중심이 됩니다. Unity [카메라](https://docs.unity3d.com/Manual/class-Camera.html) 구성 요소는 stereoscopic 렌더링을 자동으로 처리 하 고 헤드 이동 및 회전을 따릅니다. 그러나 시각적 품질 및 [홀로그램 안정성](../platform-capabilities-and-apis/hologram-stability.md)을 완벽 하 게 최적화 하려면 아래에서 설명 하는 카메라 설정을 설정 해야 합니다.

## <a name="hololens-vs-vr-immersive-headsets"></a>HoloLens vs VR 모던 헤드셋

Unity 카메라 구성 요소의 기본 설정은 일반적인 3D 응용 프로그램을 위한 것 이며 실제 세계에 있지 않기 때문에 skybox 같은 배경을 필요로 합니다.

* **[몰입 형 헤드셋](../../discover/immersive-headset-hardware-details.md)** 에서 실행 하는 경우 사용자에 게 표시 되는 모든 항목을 렌더링 하 게 되므로 skybox를 유지할 수 있습니다.
* 그러나 [HoloLens](/hololens/hololens2-hardware)와 같은 **holographic 헤드셋** 에서 실행 하는 경우 실제 세계는 카메라에서 렌더링 하는 모든 항목 뒤에 표시 되어야 합니다. Skybox 질감이 아닌 카메라 배경을 투명 하 게 설정 합니다 (HoloLens에서 검정색 렌더링 투명).
    1. 계층 패널에서 주 카메라를 선택 합니다.
    2. 검사기 패널에서 카메라 구성 요소를 찾아 Clear Flags dropdown을 Skybox에서 Solid Color로 변경 합니다.
    3. 배경색 선택을 선택 하 고 RGBA 값을 (0, 0, 0, 0)으로 변경 합니다.
        1. 코드에서이 설정을 사용 하는 경우 Unity의 [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>카메라 설정

개발 중인 모든 종류의 환경에서 기본 카메라는 항상 장치의 헤드 탑재 디스플레이에 연결 된 기본 스테레오 렌더링 구성 요소입니다. 사용자의 시작 위치 (X: 0, Y: 0, Z: 0)를 사용 하는 경우 앱의 레이아웃을 보다 쉽게 지정할 수 있습니다. 주 카메라가 사용자 헤드의 이동을 추적 하므로 기본 카메라의 시작 위치를 설정 하 여 사용자의 시작 위치를 설정할 수 있습니다.

선택 해야 하는 중심은 HoloLens 또는 VR 모던 헤드셋을 개발 하 고 있는지 여부입니다. 이를 받은 후에는 적용 되는 설정 섹션으로 건너뜁니다.

### <a name="hololens-camera-setup"></a>HoloLens 카메라 설정

HoloLens 앱의 경우 장면 환경에 잠그려는 모든 개체에 대 한 앵커를 사용 해야 합니다. 제한 없는 공간을 사용 하 여 안정성을 최대화 하 고 여러 방에 앵커를 만드는 것이 좋습니다.

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>VR 카메라 설정

Windows Mixed Reality는 규모에 상관 없이 공간 규모 앱을 통해 응용 프로그램을 수평으로 확장 하 여 규모에 상관 없이 광범위 한 [환경](../../design/coordinate-systems.md#mixed-reality-experience-scales)에서 앱을 지원 합니다. HoloLens에서 더 나아가 사용자가 5 미터 이상 이동할 수 있도록 하는 세계적인 규모의 앱을 빌드할 수 있습니다.

Unity에서 혼합 현실 환경을 빌드하는 첫 번째 단계는 앱이 대상으로 하는 [환경 크기](../../design/coordinate-systems.md) 를 결정 하는 것입니다.

* [방향 또는 고정 크기 조정](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [단일 또는 공간 규모](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [전 세계 규모](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>공간 규모 또는 서 환경

> [!NOTE]
> HL2에 대해 빌드하는 경우에는 눈에 잘 맞는 환경을 만드는 것이 좋습니다. 또는 장면의 밑면에 대 한 이유를 [장면 이해](../platform-capabilities-and-apis/scene-understanding-sdk.md) 를 사용 하는 것이 좋습니다.

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>장착 환경

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>카메라 배경 설정

MRTK를 사용 하는 경우 카메라의 배경이 자동으로 구성 되 고 관리 됩니다. XR SDK 또는 레거시 WSA 프로젝트의 경우 카메라의 배경을 HoloLens의 검정색으로 설정 하 고 VR의 skybox을 유지 하는 것이 좋습니다.

## <a name="using-multiple-cameras"></a>여러 카메라 사용

장면에 여러 카메라 구성 요소가 있는 경우 Unity는 MainCamera 태그가 있는 GameObject을 기준으로 stereoscopic 렌더링에 사용할 카메라를 알고 있습니다. 레거시 XR에서이 태그를 사용 하 여 헤드 추적을 동기화 합니다. XR SDK에서 헤드 추적은 카메라에 연결 된 TrackedPoseDriver 스크립트에 의해 결정 됩니다.

## <a name="sharing-depth-buffers"></a>깊이 버퍼 공유

Windows에 앱의 깊이 버퍼를 공유 하면 각 프레임에서 렌더링 하는 헤드셋의 유형에 따라 홀로그램 안정성의 두 가지 향상 된 기능 중 하나를 앱에 제공 합니다.

* **VR 모던 헤드셋** 은 깊이 버퍼가 제공 될 때 위치를 다시 프로젝션 하 여 위치와 방향 모두에서 misprediction에 대 한 holograms를 조정할 수 있습니다.
* **HoloLens 헤드셋** 에는 몇 가지 방법이 있습니다. HoloLens 1은 깊이 버퍼가 제공 될 때 [포커스 지점을](focus-point-in-unity.md) 자동으로 선택 하 여 대부분의 콘텐츠와 교차 하는 평면을 따라 홀로그램의 안정성을 최적화 합니다. HoloLens 2는 [깊이 LSR (설명 참조)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)을 사용 하 여 콘텐츠를 안정화 합니다.

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>클리핑 평면 사용

사용자에 게 너무 가까운 렌더링 콘텐츠는 혼합 현실에서 불편을 수 있습니다. 카메라 구성 요소에서 [근거리 및 원거리 클립 평면](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 을 조정할 수 있습니다.

1. **계층** 패널에서 **주 카메라** 를 선택 합니다.
2. **검사기** 패널에서 **평면 클리핑** **카메라** 구성 요소를 찾아 **가까운** 텍스트 상자를 **0.3** 에서 **0.85** 으로 변경 합니다. 더 가까이 렌더링 된 콘텐츠는 사용자 discomfort 발생할 수 있으므로 [렌더링 거리 지침](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)에 따라 피해 야 합니다.

## <a name="recentering-the-camera"></a>카메라 입력

통합 된 [환경을](../../design/coordinate-systems.md)구축 하는 경우 XR를 호출 하 여 사용자의 현재 헤드 위치에서 Unity의 세계 원본을 recenter 수 있습니다 **[.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 레거시 XR의 Recenter 메서드 또는 XR SDK의 **[Xrinputsubsystem. TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** 메서드

## <a name="teleportation"></a>순간 이동

이 기능은 일반적으로 VR 환경용으로 예약 되어 있습니다.

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>재 투영 모드

HoloLens 및 몰입 형 헤드셋은 모두 앱이 렌더링 하는 각 프레임을 다시 프로젝션 하 여 photons를 내보낼 때 사용자의 실제 헤드 위치 misprediction 조정 합니다.

기본적으로 다음과 같습니다.

* 응용 프로그램에서 지정 된 프레임에 대 한 깊이 버퍼를 제공 하는 경우 **VR 모던 헤드셋** 은 위치 다시 프로젝션을 처리 합니다. 또한 몰입 형 헤드셋은 위치와 방향 모두에서 misprediction에 대 한 holograms을 조정 합니다. 깊이 버퍼가 제공 되지 않은 경우 시스템은 방향 으로만 mispredictions을 수정 합니다.
* HoloLens 2와 같은 **Holographic 헤드셋** 은 앱이 깊이 버퍼를 제공 하는지 여부에 관계 없이 위치를 다시 프로젝션 합니다. 렌더링은 실제 세계에서 제공 하는 안정적인 배경을 사용 하는 스파스 인 경우가 많기 때문에 HoloLens의 깊이 버퍼 없이 위치 다시 프로젝션이 가능 합니다.

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [응시](gaze-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참조

* [홀로그램 안정성](../platform-capabilities-and-apis/hologram-stability.md)
* [환경 크기 조정](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [공간 스테이지](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity의 손실 추적](tracking-loss-in-unity.md)
* [Spatial Anchors](../../design/spatial-anchors.md)
* [Unity의 지속성](persistence-in-unity.md)
* [Unity의 공유 환경](shared-experiences-in-unity.md)
* [Azure Spatial Anchors](/azure/spatial-anchors)
* [Unity 용 Azure 공간 앵커 SDK](/dotnet/api/Microsoft.Azure.SpatialAnchors)