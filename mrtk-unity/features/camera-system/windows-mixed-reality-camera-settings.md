---
title: Windows Mixed Reality 카메라 설정
description: MRTK에서 Windows Mixed Reality 카메라 설정을 사용 하는 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 카메라,
ms.openlocfilehash: 49b178b7ebd1fbcdaab9648baeaa6abfa9e885ea
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121641"
---
# <a name="windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality 카메라 설정 공급자

Windows Mixed Reality 카메라 설정 공급자는 응용 프로그램이 실행 되는 장치 유형을 결정 하 고 디스플레이 (투명 또는 불투명)에 따라 적절 한 구성 설정을 적용 합니다.

## <a name="enabling-the-windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality 카메라 설정 공급자 사용

다음 단계에서는 MixedRealityToolkit 개체를 사용 하는 것으로 가정 합니다. 다른 서비스 등록 기관 필요한 단계는 다를 수 있습니다.

1. 장면 계층 구조에서 MixedRealityToolkit 개체를 선택 합니다.

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

2. 검사기 패널에서 카메라 시스템 섹션으로 이동 하 여 **카메라 설정 공급자** 섹션을 확장 합니다.

    ![설정 공급자 확장](../images/camera-system/ExpandProviders.png)

3. **카메라 설정 공급자 추가** 를 클릭 하 고 새로 추가 된 **새 카메라 설정** 항목을 확장 합니다.

    ![새 설정 공급자 확장](../images/camera-system/ExpandNewProvider.png)

4. Windows Mixed Reality 카메라 설정 공급자를 선택 합니다.

    ![Windows Mixed Reality 설정 공급자 선택](../images/camera-system/SelectWindowsMixedRealitySettings.png)

> [!NOTE]
> Microsoft Mixed Reality Toolkit 기본 프로필을 사용 하는 경우 Windows Mixed Reality 카메라 설정 공급자가 이미 사용 하도록 설정 되 고 구성 됩니다.

## <a name="configuring-the-windows-mixed-reality-camera-settings-provider"></a>Windows Mixed Reality 카메라 설정 공급자 구성

Windows Mixed Reality 카메라 설정은 프로필도 지원 합니다. 이 프로필은 다음과 같은 옵션을 제공 합니다.

![Windows Mixed Reality 카메라 설정 구성](../images/camera-system/WMRCameraSettingsProfile.png)

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

## <a name="see-also"></a>참조

- [카메라 시스템 개요](camera-system-overview.md)
- [카메라 설정 공급자 만들기](create-settings-provider.md)
- [PV 카메라에서 혼합 현실 캡처 렌더링](/windows/mixed-reality/mixed-reality-capture-for-developers#render-from-the-pv-camera-opt-in)
- [Holographic reprojection](/windows/mixed-reality/hologram-stability#reprojection)