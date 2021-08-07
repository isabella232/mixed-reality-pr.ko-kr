---
title: Windows Mixed Reality 카메라 설정
description: MRTK에서 Windows Mixed Reality 카메라 설정을 사용하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 카메라,
ms.openlocfilehash: 6d0231c070cd001d7e01b4a82ab66c2a9c5c115240b03e28b7d49a14de1753f1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212698"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality 카메라 설정 공급자

Windows Mixed Reality 카메라 설정 공급자는 애플리케이션이 실행되는 디바이스 유형을 결정하고 디스플레이(투명 또는 불투명)에 따라 적절한 구성 설정을 적용합니다.

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality 카메라 설정 공급자 사용

다음 단계에서는 MixedRealityToolkit 개체의 사용을 가정합니다. 다른 서비스 등록 기관에 필요한 단계는 다를 수 있습니다.

1. 장면 계층 구조에서 MixedRealityToolkit 개체를 선택합니다.

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

2. 검사기 패널을 카메라 시스템 섹션으로 이동하고 **카메라 설정 공급자 섹션을 확장합니다.**

    ![설정 공급자 확장](../images/camera-system/ExpandProviders.png)

3. **카메라 설정 공급자 추가를** 클릭하고 새로 추가된 새 카메라 **설정** 항목을 확장합니다.

    ![새 설정 공급자 확장](../images/camera-system/ExpandNewProvider.png)

4. Windows Mixed Reality Camera 설정 공급자 선택

    ![Windows Mixed Reality 설정 공급자 선택](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> Microsoft Mixed Reality Toolkit 기본 프로필을 사용하는 경우 Windows Mixed Reality 카메라 설정 공급자가 이미 사용하도록 설정되고 구성됩니다.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality 카메라 설정 공급자 구성

Windows Mixed Reality Camera 설정 프로필도 지원합니다. 이 프로필은 다음 옵션을 제공합니다.

![카메라 설정 구성 Windows Mixed Reality](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>사진/비디오 카메라에서 혼합 현실 캡처 렌더링

HoloLens 2 이 설정을 사용하면 혼합 현실 캡처에서 홀로그램 맞춤을 사용하도록 설정할 수 있습니다. 사용하도록 설정하면 혼합 현실 캡처 사진 또는 비디오를 촬영할 때 플랫폼이 앱에 추가 HolographicCamera를 제공합니다. 이 HolographicCamera는 사진/비디오 카메라 위치에 해당하는 보기 행렬을 제공하며, 사진/비디오 카메라 보기 필드를 사용하여 프로젝션 행렬을 제공합니다. 이렇게 하면 손 메시와 같은 홀로그램이 비디오 출력에서 눈에 띄게 정렬된 상태로 유지됩니다.

### <a name="hololens-2-reprojection-method"></a>HoloLens 2 다시 프로젝션 메서드

HoloLens 2 다시 프로젝션에 대한 초기 메서드를 설정합니다. 장면의 모든 부분이 사용자와의 거리에 따라 독립적으로 안정화되기 때문에 기본 권장 사항은 깊이 다시 프로젝션을 사용하는 것입니다. 홀로그램이 여전히 불안정해 보이면 모든 개체가 깊이 버퍼에 깊이를 올바르게 제출했는지 확인합니다. 이는 경우에 따라 셰이더 설정입니다. 깊이가 제대로 제출된 것으로 나타나고 불안정도가 여전히 있는 경우 안정화 평면을 계산하기 위해 깊이 버퍼를 사용하는 자동 평면 안정화를 시도합니다. 앱이 이러한 옵션 중 하나를 사용할 수 있도록 충분한 깊이 데이터를 제출할 수 없는 경우 평면 다시 프로젝션이 대체(fallback)로 제공됩니다. 이 메서드는 [SetFocusPointForFrame을](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)통해 앱에서 제공하는 포커스 지점 데이터를 기반으로 합니다.

런타임에 reprojection 메서드를 업데이트하려면 다음과 같이 에 액세스합니다. `WindowsMixedRealityReprojectionUpdater`

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

이 값은 한 번만 업데이트하면 되며 모든 후속 프레임에 대해 값이 재사용됩니다. 메서드가 자주 업데이트되는 경우 자주 호출하는 대신 결과를 캐시하는 `EnsureComponent` 것이 좋습니다.

## <a name="see-also"></a>추가 정보

- [카메라 시스템 개요](camera-system-overview.md)
- [카메라 설정 공급자 만들기](create-settings-provider.md)
- [PV 카메라에서 혼합 현실 캡처 렌더링](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [홀로그램 다시 프로젝션](/windows/mixed-reality/hologram-stability#reprojection)