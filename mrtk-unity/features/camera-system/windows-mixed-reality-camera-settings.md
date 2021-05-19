---
title: Windows Mixed Reality 카메라 설정
description: MRTK에서 Windows Mixed Reality 카메라를 사용하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 카메라,
ms.openlocfilehash: 94e00f47dc565af0824ef6acf5c08a9e99d4529f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145161"
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

4. Windows Mixed Reality 카메라 설정 공급자 선택

    ![Windows Mixed Reality 설정 공급자 선택](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> Microsoft Mixed Reality Toolkit 기본 프로필을 사용하는 경우 Windows Mixed Reality 카메라 설정 공급자가 이미 사용하도록 설정되고 구성됩니다.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality 카메라 설정 공급자 구성

Windows Mixed Reality 카메라 설정은 프로필도 지원합니다. 이 프로필은 다음 옵션을 제공합니다.

![카메라 설정 구성 Windows Mixed Reality](../images/camera-system/WMRCameraSettingsProfile.png)

### <a name="render-mixed-reality-capture-from-the-photovideo-camera"></a>사진/비디오 카메라에서 혼합 현실 캡처 렌더링

HoloLens 2에서이 설정을 사용 하면 혼합 현실 캡처에서 홀로그램 맞춤을 사용 하도록 설정할 수 있습니다. 사용 하도록 설정 된 경우 혼합 현실 캡처 사진 또는 비디오를 사용 하는 경우 플랫폼에서 앱에 추가 HolographicCamera을 제공 합니다. 이 HolographicCamera는 photo/video 카메라 위치에 해당 하는 뷰 매트릭스를 제공 하 고, 보기의 사진/비디오 카메라 필드를 사용 하 여 프로젝션 매트릭스를 제공 합니다. 이렇게 하면 holograms (예: 손 모양)가 비디오 출력에 시각적으로 정렬 된 상태로 유지 됩니다.

### <a name="hololens-2-reprojection-method"></a>HoloLens 2 reprojection 방법

HoloLens 2 reprojection에 대 한 초기 방법을 설정 합니다. 기본적인 권장 사항은 깊이 다시 프로젝션을 사용 하는 것입니다. 장면의 모든 부분은 사용자의 거리를 기준으로 독립적으로 안정화 되기 때문입니다. Holograms 여전히 불안정 하 게 표시 되는 경우 모든 개체가 깊이 버퍼에 깊이를 올바르게 제출 했는지 확인 하세요. 이는 때때로 셰이더 설정입니다. 깊이가 제대로 전송 되 고 불안정성이 아직 있는 경우 깊이 버퍼를 사용 하 여 안정화 평면을 계산 하는 autoplanar 안정화를 시도 합니다. 앱에서 이러한 옵션 중 하나를 사용할 수 있는 충분 한 깊이 데이터를 전송할 수 없는 경우에는 평면 다시 프로젝션이 대체 (fallback)로 제공 됩니다. 이 메서드는 [SetFocusPointForFrame](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.SetFocusPointForFrame.html)을 통해 앱에서 제공 하는 포커스 지점 데이터를 기반으로 합니다.

런타임에 reprojection 메서드를 업데이트 하려면 다음과 같이에 액세스 합니다 `WindowsMixedRealityReprojectionUpdater` .

```c#
var reprojectionUpdater = CameraCache.Main.EnsureComponent<WindowsMixedRealityReprojectionUpdater>();
reprojectionUpdater.ReprojectionMethod = HolographicDepthReprojectionMethod.AutoPlanar;
```

이는 한 번만 업데이트 하면 되 고 모든 후속 프레임에 값이 다시 사용 됩니다. 메서드가 자주 업데이트 되는 경우에는 자주 호출 하는 대신 결과를 캐시 하는 것이 좋습니다 `EnsureComponent` .

## <a name="see-also"></a>참고 항목

- [카메라 시스템 개요](camera-system-overview.md)
- [카메라 설정 공급자 만들기](create-settings-provider.md)
- [PV 카메라에서 혼합 현실 캡처 렌더링](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Holographic reprojection](/windows/mixed-reality/hologram-stability#reprojection)