---
title: Unity의 카메라
description: Holographic 렌더링을 수행 하기 위해 Windows Mixed Reality 개발용 Unity의 기본 카메라를 설정 하 고 사용 하는 방법에 대해 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, holographic 렌더링, holographic, 몰입 형, 포커스 지점, 깊이 버퍼, 방향 전용, 위치, 불투명, 투명, 클립, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: cd5284a8fdef7254b7d0375b57877d30f5d0d708
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006393"
---
# <a name="camera-in-unity"></a>Unity의 카메라

혼합 현실 헤드셋을 착용 하면 holographic 세계의 중심이 됩니다. Unity [카메라](https://docs.unity3d.com/Manual/class-Camera.html) 구성 요소는 stereoscopic 렌더링을 자동으로 처리 하 고 헤드 이동 및 회전을 따릅니다. 그러나 시각적 품질 및 [홀로그램 안정성](../platform-capabilities-and-apis/hologram-stability.md)을 완벽 하 게 최적화 하려면 아래에서 설명 하는 카메라 설정을 설정 해야 합니다.

## <a name="setup"></a>설치 프로그램

1. **Windows 스토어 플레이어 설정** 의 **기타 설정** 섹션으로 이동 합니다.
2. **Windows Mixed Reality** 를 장치로 선택 합니다 .이는 이전 버전의 Unity에서 **windows Holographic** 으로 나열 될 수 있습니다.
3. **지원 되는 가상 현실** 선택

>[!NOTE]
>이러한 설정은 앱의 각 장면에서 카메라에 적용 해야 합니다.
>
>기본적으로 Unity에서 새 장면을 만들 때 카메라 구성 요소를 포함 하는 계층의 기본 카메라 GameObject가 포함 되지만, 아래에는 설정이 제대로 적용 되지 않습니다.

## <a name="holographic-vs-immersive-headsets"></a>Holographic 및 몰입 형 헤드셋

Unity 카메라 구성 요소의 기본 설정은 일반적인 3D 응용 프로그램을 위한 것 이며 실제 세계에 있지 않기 때문에 skybox 같은 배경을 필요로 합니다.

* **[몰입 형 헤드셋](../../discover/immersive-headset-hardware-details.md)** 에서 실행 하는 경우 사용자에 게 표시 되는 모든 항목을 렌더링 하 게 되므로 skybox를 유지할 수 있습니다.
* 그러나 [HoloLens](../../hololens-hardware-details.md)와 같은 **holographic 헤드셋** 에서 실행 하는 경우 실제 세계는 카메라에서 렌더링 하는 모든 항목 뒤에 표시 되어야 합니다. Skybox 질감이 아닌 카메라 배경을 투명 하 게 설정 합니다 (HoloLens에서 검정색 렌더링 투명).
    1. 계층 패널에서 주 카메라를 선택 합니다.
    2. 검사기 패널에서 카메라 구성 요소를 찾아 Clear Flags dropdown을 Skybox에서 Solid Color로 변경 합니다.
    3. 배경색 선택을 선택 하 고 RGBA 값을 (0, 0, 0, 0)으로 변경 합니다.

스크립트 코드를 사용 하 여 [HolographicSettings](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)를 확인 하 여 헤드셋이 몰입 또는 holographic 인지 여부를 런타임에 확인할 수 있습니다.

## <a name="positioning-the-camera"></a>카메라 위치 지정

사용자의 시작 위치 (X: 0, Y: 0, Z: 0)를 사용 하는 경우 앱을 레이아웃 하는 것이 더 쉽습니다. 주 카메라가 사용자 헤드의 이동을 추적 하므로 기본 카메라의 시작 위치를 설정 하 여 사용자의 시작 위치를 설정할 수 있습니다.

1. 계층 패널에서 주 카메라를 선택 합니다.
2. 검사기 패널에서 변형 구성 요소를 찾아 위치를 (X: 0, Y: 1, Z:-10)에서 (X: 0, Y: 0, Z: 0)로 변경 합니다.

   ![Unity의 검사기 창에 있는 카메라](images/maincamera-350px.png)  
   *Unity의 검사기 창에 있는 카메라*

## <a name="clip-planes"></a>클립 평면

사용자에 게 너무 가까운 렌더링 콘텐츠는 혼합 현실에서 불편을 수 있습니다. 카메라 구성 요소에서 [근거리 및 원거리 클립 평면](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 을 조정할 수 있습니다.

1. 계층 패널에서 주 카메라를 선택 합니다.
2. 검사기 패널에서 평면 클리핑 카메라 구성 요소를 찾아 가까운 텍스트 상자를 0.3에서 0.85으로 변경 합니다. 더 가까이 렌더링 된 콘텐츠는 사용자 discomfort 발생할 수 있으므로 [렌더링 거리 지침](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)에 따라 피해 야 합니다.

## <a name="multiple-cameras"></a>여러 카메라

장면에 여러 카메라 구성 요소가 있는 경우 Unity는 MainCamera 태그가 있는 GameObject을 기준으로 stereoscopic 렌더링 및 헤드 추적에 사용할 카메라를 알고 있습니다.

## <a name="recentering-a-seated-experience"></a>장착 된 환경 입력

통합 된 [환경을](../../design/coordinate-systems.md)구축 하는 경우 XR를 호출 하 여 사용자의 현재 헤드 위치에서 Unity의 세계 원본을 recenter 수 있습니다 **[. Recenter 메서드입니다.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)**

## <a name="reprojection-modes"></a>재 투영 모드

HoloLens 및 몰입 형 헤드셋은 모두 앱이 렌더링 하는 각 프레임을 다시 프로젝션 하 여 photons를 내보낼 때 사용자의 실제 헤드 위치 misprediction 조정 합니다.

기본적으로 다음과 같습니다.

* 앱이 지정 된 프레임에 대 한 깊이 버퍼를 제공 하는 경우 **몰입 형 헤드셋** 은 위치 다시 프로젝션을 처리 합니다. 또한 몰입 형 헤드셋은 위치와 방향 모두에서 misprediction에 대 한 holograms을 조정 합니다. 깊이 버퍼가 제공 되지 않은 경우 시스템은 방향 으로만 mispredictions을 수정 합니다.
* **Holographic 헤드셋** 과 같은 헤드셋은 앱이 깊이 버퍼를 제공 하는지 여부에 관계 없이 위치를 다시 프로젝션 합니다.  렌더링은 실제 세계에서 제공 하는 안정적인 배경을 사용 하는 스파스 인 경우가 많기 때문에 HoloLens의 깊이 버퍼 없이 위치 다시 프로젝션이 가능 합니다.

엄격 본문 잠긴 콘텐츠 (예: 360도 비디오 콘텐츠)를 사용 하 여 [방향 전용 환경을](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) 빌드하는 경우 [ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) 를 [HolographicReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)로 설정 하 여 reprojection 모드를 방향 으로만 명시적으로 설정할 수 있습니다.

## <a name="sharing-your-depth-buffers-with-windows"></a>Windows와 깊이 버퍼 공유

Windows에 앱의 깊이 버퍼를 공유 하면 각 프레임에서 렌더링 하는 헤드셋의 유형에 따라 홀로그램 안정성의 두 가지 향상 된 기능 중 하나를 앱에 제공 합니다.

* **몰입 형 헤드셋** 은 깊이 버퍼가 제공 될 때 위치를 다시 프로젝션 하 여 위치와 방향 모두에서 misprediction에 대 한 holograms를 조정할 수 있습니다.
* **Holographic 헤드셋** 에는 몇 가지 방법이 있습니다. HoloLens 1은 깊이 버퍼가 제공 될 때 [포커스 지점을](focus-point-in-unity.md) 자동으로 선택 하 여 대부분의 콘텐츠와 교차 하는 평면을 따라 홀로그램의 안정성을 최적화 합니다. HoloLens 2는 [깊이 LSR (설명 참조)](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)을 사용 하 여 콘텐츠를 안정화 합니다.

Unity 앱이 Windows에 깊이 버퍼를 제공할지 여부를 설정 하려면 다음을 수행 합니다.

1. **편집**  >  **프로젝트 설정**  >  **플레이어**  >  **유니버설 Windows 플랫폼 탭**  >  **XR 설정** 으로 이동 합니다.
2. **Windows Mixed REALITY SDK** 항목을 확장 합니다.
3. **깊이 버퍼 공유 사용** 확인란을 선택 하거나 선택 취소 합니다.  새 프로젝트에서는이 기능이 Unity에 추가 되었으며 업그레이드 된 이전 프로젝트에 대해서는 기본적으로 선택 취소 되기 때문에 깊이 버퍼 공유 사용은 새 프로젝트에서 기본적으로 선택 되어 있습니다.

깊이 버퍼를 사용 하면 Windows에서 기본 카메라의 Unity에 설정 된 근처 및 far 비행기를 사용 하 여 깊이 버퍼의 정규화 된 픽셀 당 깊이 값을 측정 단위로 다시 정확히 매핑할 수 있으므로 시각적 품질을 향상 시킬 수 있습니다.  렌더링 과정에서 일반적인 방법으로 깊이 값이 처리 되는 경우에는 일반적으로 여기에 자세히 설명 해야 합니다 .이는 기존 색 픽셀을 통해 표시 되는 동안 깊이 버퍼에 쓰는 반투명 렌더링 패스가 다시 프로젝션을 혼동 하는 것입니다.  렌더링 패스에서 깊이 값이 정확 하지 않은 최종 깊이 픽셀을 많이 사용 하는 경우 "깊이 버퍼 공유 사용"을 선택을 취소 하면 시각적 품질이 향상 될 가능성이 높습니다.

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit"></a>혼합 현실 도구 키트를 사용 하 여 자동 장면 및 카메라 설정 

[단계별 가이드에](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) 따라 Unity 프로젝트에 Mixed Reality Toolkit을 추가 하면 프로젝트가 자동으로 구성 됩니다. 아래 섹션의 가이드를 사용 하 여 MRTK 없이 프로젝트를 수동으로 구성할 수도 있습니다.

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
* [MixedRealityToolkit 주 카메라 prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
