---
title: Unity의 카메라 설정
description: Windows Mixed Reality 개발을 위해 Unity의 주 카메라를 설정하고 사용하여 홀로그램 렌더링을 수행하는 방법을 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 홀로그램 렌더링, 홀로그램, 몰입형, 포커스 지점, 깊이 버퍼, 방향 전용, 위치, 불투명, 투명, 클립, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 1ac8c16e7bdd6b85b05c837e1a27fbd1e4cf4489ccb03d10ea5e952b2656cbe8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212290"
---
# <a name="camera-setup-in-unity"></a>Unity의 카메라 설정

혼합 현실 헤드셋을 사용하면 홀로그램 세계의 중심이 됩니다. Unity [카메라](https://docs.unity3d.com/Manual/class-Camera.html) 구성 요소는 자동으로 스테레오 범위 렌더링을 처리하고 머리 이동 및 회전을 따릅니다. 그러나 시각적 품질 및 [홀로그램 안정성을](../platform-capabilities-and-apis/hologram-stability.md)완전히 최적화하려면 아래에 설명된 카메라 설정을 설정해야 합니다.

## <a name="hololens-vs-vr-immersive-headsets"></a>HoloLens vs VR 몰입형 헤드셋

Unity 카메라 구성 요소의 기본 설정은 실제 환경이 없기 때문에 skybox와 같은 배경이 필요한 기존 3D 애플리케이션에 대한 것입니다.

* **[몰입형 헤드셋](../../discover/immersive-headset-hardware-details.md)** 에서 실행하는 경우 사용자에게 표시되는 모든 것을 렌더링하므로 skybox를 유지할 수 있습니다.
* 그러나 [HoloLens](/hololens/hololens2-hardware)같은 **홀로그램 헤드셋에서** 실행하는 경우 실제 세계는 카메라가 렌더링하는 모든 것 뒤에 표시되어야 합니다. 카메라 배경을 Skybox 질감 대신 투명(HoloLens 검은색 렌더링)으로 설정합니다.
    1. 계층 패널에서 주 카메라를 선택합니다.
    2. 검사기 패널에서 카메라 구성 요소를 찾고 플래그 지우기 드롭다운을 Skybox에서 단색으로 변경합니다.
    3. 배경색 선택기를 선택하고 RGBA 값을 (0, 0, 0, 0)으로 변경합니다.
        1. 코드에서 이를 설정하는 경우 Unity의 를 사용할 수 있습니다. [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a>카메라 설정

어떤 종류의 경험을 개발하든 주 카메라는 항상 디바이스의 헤드 탑재 디스플레이에 연결된 기본 스테레오 렌더링 구성 요소입니다. 사용자의 시작 위치를 (X: 0, Y: 0, Z: 0)로 간주하는 경우 앱 레이아웃이 더 쉽습니다. 주 카메라는 사용자의 머리 이동을 추적하기 때문에 주 카메라의 시작 위치를 설정하여 사용자의 시작 위치를 설정할 수 있습니다.

HoloLens 또는 VR 몰입형 헤드셋을 개발 중인지 여부를 선택해야 합니다. 이 설정이 완료되면 적용되는 설정 섹션으로 건너뜁니다.

### <a name="hololens-camera-setup"></a>카메라 설정 HoloLens

HoloLens 앱의 경우 장면 환경에 잠그려는 모든 개체에 앵커를 사용해야 합니다. 안정성을 최대화하고 여러 공간에 앵커를 만들려면 무제한 공간을 사용하는 것이 좋습니다.

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a>VR 카메라 설정

Windows Mixed Reality 방향 전용 및 좌표 크기 조정 앱에서 실내 크기 조정 앱을 통해 다양한 [환경 규모에서](../../design/coordinate-systems.md#mixed-reality-experience-scales)앱을 지원합니다. HoloLens 사용자가 5미터를 넘어 건물 전체 층을 탐색할 수 있는 세계적 규모의 앱을 빌드할 수 있습니다.

Unity에서 혼합 현실 환경을 빌드하는 첫 번째 단계는 앱의 대상 [환경 크기를](../../design/coordinate-systems.md) 결정하는 것입니다.

* [방향 또는 좌표 크기 조정](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [서 있거나 방 크기 조정](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [세계적 규모](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a>방 크기 조정 또는 서 있는 환경

> [!NOTE]
> HL2용으로 빌드하는 경우 시선 수준 환경을 만들거나 장면 [이해를](../platform-capabilities-and-apis/scene-understanding-sdk.md) 사용하여 장면의 층을 추론하는 것이 좋습니다.

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a>착석 환경

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a>카메라 배경 설정

MRTK를 사용하는 경우 카메라의 배경이 자동으로 구성되고 관리됩니다. XR SDK 또는 레거시 WSA 프로젝트의 경우 카메라 배경을 HoloLens 검은색으로 설정하고 VR용 skybox를 유지하는 것이 좋습니다.

## <a name="using-multiple-cameras"></a>여러 카메라 사용

장면에 카메라 구성 요소가 여러 개 있는 경우 Unity는 MainCamera 태그가 있는 GameObject에 따라 스테레오 범위 렌더링에 사용할 카메라를 알고 있습니다. 레거시 XR에서는 이 태그를 사용하여 헤드 추적을 동기화합니다. XR SDK에서 헤드 추적은 카메라에 연결된 TrackedPoseDriver 스크립트에 의해 구동됩니다.

## <a name="sharing-depth-buffers"></a>깊이 버퍼 공유

각 프레임을 Windows 앱의 깊이 버퍼를 공유하면 렌더링하는 헤드셋 유형에 따라 홀로그램 안정성이 크게 향상됩니다.

* **VR 몰입형 헤드셋은** 깊이 버퍼가 제공될 때 위치 재프로젝션을 처리하여 위치와 방향 모두에서 잘못된 예측에 맞게 홀로그램을 조정할 수 있습니다.
* **HoloLens 헤드셋에는** 몇 가지 다른 방법이 있습니다. HoloLens 1은 깊이 버퍼가 제공되면 [자동으로 포커스 지점을](focus-point-in-unity.md) 선택하여 대부분의 콘텐츠와 교차하는 평면을 따라 홀로그램 안정성을 최적화합니다. HoloLens 2 깊이 LSR을 사용하여 콘텐츠를 [안정화합니다(주의 참조).](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a>클리핑 평면 사용

사용자에게 너무 가까운 렌더링 콘텐츠는 혼합 현실에서 혼동될 수 있습니다. 카메라 구성 요소에서 [근거리 및 원거리 클립 평면을](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 조정할 수 있습니다.

1. **계층 패널에서** **주 카메라를** 선택합니다.
2. **검사기** 패널에서 **카메라** 구성 요소 **클리핑 평면을** 찾아 **Near** 텍스트 상자를 **0.3에서** **0.85로** 변경합니다. 콘텐츠가 더 가깝게 렌더링될 경우 사용자 불편이 발생할 수 있으며 [렌더링 거리 지침](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)에 따라 피해야 합니다.

## <a name="recentering-the-camera"></a>카메라 최근화

[착석 규모 환경을](../../design/coordinate-systems.md)빌드하는 경우 XR을 호출하여 사용자의 현재 헤드 위치에서 Unity의 세계 원본을 더 최근에 만들 수 **[있습니다. 레거시 XR의 InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 메서드 또는 XR SDK의 **[XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** 메서드.

## <a name="teleportation"></a>순간 이동

이 기능은 일반적으로 VR 환경을 위해 예약됩니다.

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a>다시 프로젝션 모드

HoloLens 헤드셋과 몰입형 헤드셋은 모두 photon을 내보낸 경우 사용자의 실제 머리 위치에 대한 잘못된 예측에 맞게 조정하도록 앱이 렌더링하는 각 프레임을 다시 프로젝션합니다.

기본적으로 다음과 같습니다.

* **VR 몰입형 헤드셋은** 앱이 지정된 프레임에 대한 깊이 버퍼를 제공하는 경우 위치 재프로젝션을 처리합니다. 또한 몰입형 헤드셋은 위치와 방향 모두에서 잘못된 예측에 맞게 홀로그램을 조정합니다. 깊이 버퍼가 제공되지 않으면 시스템은 방향에서 잘못된 예측만 수정합니다.
* HoloLens 2 같은 **홀로그램 헤드셋은** 앱이 깊이 버퍼를 제공하는지 여부에 관계없이 위치 재프로젝션을 처리합니다. 렌더링이 실제 세계에서 제공하는 안정적인 배경에서 스파스되는 경우가 많기 때문에 위치 재프로젝션은 HoloLens 깊이 버퍼 없이도 가능합니다.

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unity 개발 여정을 수행하는 경우 MRTK 핵심 구성 요소 탐색을 진행하는 중입니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [응시](gaze-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목

* [홀로그램 안정성](../platform-capabilities-and-apis/hologram-stability.md)
* [환경 크기 조정](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [공간 단계](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity의 손실 추적](tracking-loss-in-unity.md)
* [Spatial Anchors](../../design/spatial-anchors.md)
* [Unity의 지속성](persistence-in-unity.md)
* [Unity의 공유 환경](shared-experiences-in-unity.md)
* [Azure Spatial Anchors](/azure/spatial-anchors)
* [Unity용 Azure Spatial Anchors SDK](/dotnet/api/Microsoft.Azure.SpatialAnchors)