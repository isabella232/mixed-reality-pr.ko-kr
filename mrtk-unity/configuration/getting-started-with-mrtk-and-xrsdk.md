---
title: MRTK 및 XR SDK 시작
description: XR SDK를 통해 MRTK에 대한 방문 페이지
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, XRSDK, XR SDK
ms.openlocfilehash: d3ff4306205cc6548bc5617d727f32a780855439
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647209"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>MRTK 및 XR SDK 시작

XR SDK는 Unity [2019.3 이상에서 Unity의 새로운 XR 파이프라인입니다.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) Unity 2019에서는 기존 XR 파이프라인에 대한 대안을 제공합니다. Unity 2020에서는 Unity에서 유일한 XR 파이프라인이 됩니다.

## <a name="prerequisites"></a>필수 구성 요소

Mixed Reality 도구 키트를 시작하려면 [제공된 단계에](../install-the-tools.md#importing-the-mixed-reality-toolkit) 따라 MRTK를 프로젝트에 추가합니다.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>XR SDK 파이프라인에 대한 Unity 구성

XR SDK 파이프라인은 현재 3개의 플랫폼인 Windows Mixed Reality, Oculus 및 OpenXR을 지원합니다. 아래 섹션에서는 각 플랫폼에 대해 XR SDK를 구성하는 데 필요한 단계를 다룹니다.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

**Unity의 패키지 관리자** 이동하여 Windows XR 플러그 인 패키지를 설치합니다. 이 패키지는 XR SDK에서 Windows Mixed Reality 대한 지원을 추가합니다. 그러면 몇 가지 종속성 패키지도 풀다운됩니다. 

1. 다음이 모두 성공적으로 설치되었는지 확인합니다.
   * XR 플러그 인 관리
   * Windows XR 플러그 인
   * XR 레거시 입력 도우미

2. **편집 > 프로젝트 설정** 으로 이동합니다.
3. 프로젝트 설정 창에서 XR 플러그 인 관리 탭을 클릭합니다.
4. 유니버설 Windows 플랫폼 설정으로 이동하여 플러그 인 공급자에서 Windows Mixed Reality 확인합니다.
5. 시작 시 XR 초기화가 선택되어 있는지 확인합니다.
6. **_(편집기 내 HoloLens Remoting에 필요하고, 그렇지 않으면 선택 사항)_** 독립 실행형 설정으로 이동하여 플러그 인 공급자에서 Windows Mixed Reality 확인합니다. 또한 시작 시 XR 초기화가 선택되어 있는지 확인합니다.

![독립 실행형 탭이 선택된 XR 플러그 인 관리](images/xr-management-img-02.png)

7. (**_선택 사항)_** XR 플러그 인 관리 아래의 Windows Mixed Reality 탭을 클릭하고 사용자 지정 설정 프로필을 만들어 기본값을 변경합니다. 설정 목록이 이미 있는 경우 프로필을 만들 필요가 없습니다.

![Windows 탭이 선택된 XR 플러그 인 관리](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. [끝으로 XR SDK 파이프라인을 사용하여 MRTK에서 Oculus Quest를 구성하는 방법](../supported-devices/oculus-quest-mrtk.md) 가이드를 따릅니다. 이 가이드에서는 Oculus Quest에 XR SDK 파이프라인을 사용하도록 Unity 및 MRTK를 구성하는 데 필요한 단계를 간략하게 설명합니다.

### <a name="openxr-preview"></a>OpenXR(미리 보기)

> [!IMPORTANT]
> Unity의 OpenXR은 Unity 2020.2 이상에서만 지원됩니다.
>
> 현재 x64 및 ARM64 빌드만 지원합니다.

1. 프로젝트에 [OpenXR 플러그 인을](/windows/mixed-reality/develop/unity/openxr-getting-started) 설치하도록 XR 플러그 인 관리 및 최적화를 구성하는 단계를 포함하여 Unity용 Mixed Reality OpenXR 플러그 인 사용 가이드를 따릅니다. 다음이 성공적으로 설치되었는지 확인합니다.
   1. XR 플러그 인 관리
   1. OpenXR 플러그 인
   1. OpenXR 플러그 인 Mixed Reality
1. 프로젝트 설정 > 편집으로 이동합니다.
1. 프로젝트 설정 창에서 XR 플러그 인 관리 탭을 클릭합니다.
1. 시작 시 XR 초기화가 선택되어 있는지 확인합니다.
1. (**_선택 사항)_** HoloLens 2 대상으로 하는 경우 UWP 플랫폼에 있는지 확인하고 Microsoft HoloLens 기능 집합을 선택합니다.

![플러그 인 관리 Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> UPM의 MRTK를 사용하는 기존 프로젝트가 있는 경우 다음 줄이 MixedRealityToolkit.Generated 폴더에 있는 **link.xml** 파일에 있는지 확인합니다.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> MRTK 및 OpenXR의 초기 릴리스에서는 HoloLens 2 개의 굴절된 손과 Windows Mixed Reality 모션 컨트롤러만 기본적으로 지원됩니다. 추가 하드웨어에 대한 지원은 향후 릴리스에서 추가될 예정입니다.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>XR SDK 파이프라인에 대한 MRTK 구성
::: moniker range=">= mrtkunity-2021-05" 
OpenXR을 사용하는 경우 활성 프로필로 "DefaultOpenXRConfigurationProfile"을 선택하거나 복제하여 사용자 지정합니다.

Windows Mixed Reality 또는 Oculus와 같은 XR 플러그 인 관리 구성에서 다른 XR 런타임을 사용하는 경우 활성 프로필로 "DefaultXRSDKConfigurationProfile"을 선택하거나 복제하여 사용자 지정합니다.

이러한 프로필은 필요한 경우 올바른 시스템 및 공급자를 통해 설정됩니다. XR SDK의 프로필 및 샘플 지원에 대한 자세한 내용은 프로필 [문서를](../features/profiles/profiles.md#xr-sdk) 참조하세요.

기존 프로필을 XR SDK로 마이그레이션하려면 다음 서비스 및 데이터 공급자를 추가해야 합니다. XR SDK 탭에서 새 데이터 공급자를 볼 수 있습니다.

![XR SDK 탭](../features/images/xrsdk/XrsdkTabView.png)

### <a name="camera"></a>카메라

다음 데이터 공급자 추가 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**및**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![XR SDK 카메라 설정](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>입력

다음 데이터 공급자 추가 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR:__

![OpenXR 입력 설정](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality:__

![XR SDK 입력 설정](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>경계

다음 데이터 공급자 추가 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 경계 설정](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>공간 인식

다음 데이터 공급자 추가 

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| 진행 중 | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![XR SDK 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>컨트롤러 매핑

사용자 지정 컨트롤러 매핑 프로필을 사용하는 경우 해당 프로필 중 하나를 열고 Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles 메뉴 항목을 실행하여 새 XR SDK 컨트롤러 유형이 정의되었는지 확인합니다.

## <a name="see-also"></a>참조

* [Unity에서 AR 개발 시작](https://docs.unity3d.com/Manual/AROverview.html)
* [Unity에서 VR 개발 시작](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
OpenXR을 사용하는 경우 활성 프로필로 "DefaultOpenXRConfigurationProfile"을 선택하거나 복제하여 사용자 지정합니다.

Windows Mixed Reality 또는 Oculus와 같은 XR 플러그 인 관리 구성에서 다른 XR 런타임을 사용하는 경우 활성 프로필로 "DefaultXRSDKConfigurationProfile"을 선택하거나 복제하여 사용자 지정합니다.

이러한 프로필은 필요한 경우 올바른 시스템 및 공급자를 통해 설정됩니다. XR SDK의 프로필 및 샘플 지원에 대한 자세한 내용은 프로필 [문서를](../features/profiles/profiles.md#xr-sdk) 참조하세요.

기존 프로필을 XR SDK로 마이그레이션하려면 다음 서비스 및 데이터 공급자를 업데이트해야 합니다.

### <a name="camera"></a>카메라

보낸 사람 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![레거시 카메라 설정](../features/images/xrsdk/CameraSystemLegacy.png)

을

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**및**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![XR SDK 카메라 설정](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>입력

보낸 사람 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![레거시 입력 설정](../features/images/xrsdk/InputSystemWMRLegacy.png)

을

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR:__

![OpenXR 입력 설정](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality:__

![XR SDK 입력 설정](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>경계

보낸 사람 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![레거시 경계 설정](../features/images/xrsdk/BoundarySystemLegacy.png)

을

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 경계 설정](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>공간 인식

보낸 사람 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![레거시 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessLegacy.png)

을

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| 진행 중 | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![XR SDK 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>컨트롤러 매핑

사용자 지정 컨트롤러 매핑 프로필을 사용하는 경우 해당 프로필 중 하나를 열고 Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles 메뉴 항목을 실행하여 새 XR SDK 컨트롤러 유형이 정의되었는지 확인합니다.

## <a name="see-also"></a>참조

* [Unity에서 AR 개발 시작](https://docs.unity3d.com/Manual/AROverview.html)
* [Unity에서 VR 개발 시작](https://docs.unity3d.com/Manual/VROverview.html)
::: moniker-end