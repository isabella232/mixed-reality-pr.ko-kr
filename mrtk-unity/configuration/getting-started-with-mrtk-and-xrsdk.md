---
title: MRTK 및 XR SDK 시작
description: XR SDK를 사용 하는 MRTK의 방문 페이지
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, mrtk, xrsdk, XR SDK
ms.openlocfilehash: 681352ff854598ab34bd9521b46ae9f4e6f42f02
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905750"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>MRTK 및 XR SDK 시작

XR SDK는 unity [2019.3 이상에서 unity의 새로운 XR 파이프라인](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/)입니다. Unity 2019에서는 기존 XR 파이프라인에 대 한 대안을 제공 합니다. Unity 2020에서는 Unity의 유일한 XR 파이프라인입니다.

## <a name="prerequisites"></a>필수 구성 요소

혼합 현실 Toolkit를 시작 하려면 [제공 된 단계](/windows/mixed-reality/develop/install-the-tools#importing-the-mixed-reality-toolkit) 에 따라 mrtk를 프로젝트에 추가 합니다.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>XR SDK 파이프라인에 대 한 Unity 구성

XR SDK 파이프라인은 현재 Windows Mixed Reality, oculus 및 OpenXR의 3 개 플랫폼을 지원 합니다. 아래 섹션에서는 각 플랫폼에 대해 XR SDK를 구성 하는 데 필요한 단계에 대해 설명 합니다.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

**Unity의 패키지 관리자** 로 이동 하 여 XR SDK에서 Windows Mixed Reality에 대 한 지원을 추가 하는 Windows XR 플러그 인 패키지를 설치 합니다. 이렇게 하면 몇 가지 종속성 패키지도 풀 다운 됩니다.

1. 다음 모두가 성공적으로 설치 되었는지 확인 합니다.
   * XR 플러그 인 관리
   * Windows XR 플러그 인
   * XR 레거시 입력 도우미

2. **편집 > 프로젝트 설정** 으로 이동합니다.
3. Project 설정 창에서 XR 플러그 인 관리 탭을 클릭 합니다.
4. 유니버설 Windows 플랫폼 설정으로 이동 하 고 플러그 인 공급자에서 Windows Mixed Reality 확인 합니다.
5. 시작 시 XR 초기화가 선택 되어 있는지 확인 합니다.
6. (**_편집기 내 HoloLens 원격 기능에 필요 하며, 그렇지 않은 경우 선택 사항_**) 독립 실행형 설정으로 이동 하 고 플러그 인 공급자에서 Windows Mixed Reality가 선택 되어 있는지 확인 합니다. 또한 시작 시 XR 초기화가 선택 되어 있는지 확인 합니다.

    ![독립 실행형 탭이 선택 된 XR 플러그 인 관리](images/xr-management-img-02.png)

7. (**_선택 사항_**) XR 플러그 인 관리 아래에서 Windows Mixed Reality 탭을 클릭 하 고 사용자 지정 설정 프로필을 만들어 기본값을 변경 합니다. 설정 목록이 이미 있는 경우 프로필을 만들 필요가 없습니다.

    ![Windows 탭이 선택 된 XR 플러그 인 관리](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. [XR SDK 파이프라인 가이드를 사용 하 여 MRTK에서 Oculus 퀘스트를 구성 하는 방법](../supported-devices/oculus-quest-mrtk.md) 을 참조 하세요. 이 가이드에서는 XR SDK 파이프라인을 사용 하도록 Unity와 MRTK를 모두 구성 하는 데 필요한 단계를 설명 합니다.

### <a name="openxr"></a>OpenXR

> [!IMPORTANT]
> Unity의 OpenXR는 Unity 2020.2 이상 에서만 지원 됩니다.
> 또한 x64, ARM 및 ARM64 빌드를 지원 합니다.

1. XR 플러그 인 관리 및 최적화를 구성 하 여 프로젝트에 OpenXR 플러그 인을 설치 하는 단계를 포함 하 여 [OpenXR에 대 한 혼합 현실 플러그 인을 사용 하](/windows/mixed-reality/develop/unity/openxr-getting-started) 는 방법 가이드를 따릅니다. 다음이 성공적으로 설치 되었는지 확인 합니다.
   1. XR 플러그 인 관리
   1. OpenXR 플러그 인
   1. 혼합 현실 OpenXR 플러그 인
1. 편집 > Project 설정로 이동 합니다.
1. Project 설정 창에서 XR 플러그 인 관리 탭을 클릭 합니다.
1. 시작 시 XR 초기화가 선택 되어 있는지 확인 합니다.
1. (**_선택 사항_**) HoloLens 2를 대상으로 하는 경우 UWP 플랫폼에 있는지 확인 하 고 Microsoft HoloLens 기능 집합을 선택 합니다.

![플러그 인 관리 OpenXR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> UPM에서 MRTK를 사용 하는 기존 프로젝트가 있는 경우 MixedRealityToolkit 폴더에 있는 **link.xml** 파일에 다음 줄이 있는지 확인 합니다.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> mrtk 및 OpenXR의 초기 릴리스에서는 HoloLens 2로 된 Windows Mixed Reality 동작 컨트롤러만 기본적으로 지원 됩니다. 추가 하드웨어에 대 한 지원은 향후 릴리스에 추가 될 예정입니다.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>XR SDK 파이프라인에 대 한 MRTK 구성

::: moniker range=">= mrtkunity-2021-05"
모든 Unity의 XR 파이프라인에서 구성 된 기본 MRTK 프로필을 사용 합니다. 이전 "DefaultOpenXRConfigurationProfile" 및 "DefaultXRSDKConfigurationProfile"은 이제 사용 되지 않는 것으로 레이블이 지정 되었습니다.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
OpenXR를 사용 하는 경우 "DefaultOpenXRConfigurationProfile"을 활성 프로필로 선택 하거나 복제 하 여 사용자 지정을 수행 합니다.

Windows Mixed Reality 또는 oculus와 같은 XR 플러그 인 관리 구성에서 다른 XR 런타임을 사용 하는 경우 "DefaultXRSDKConfigurationProfile"를 활성 프로필로 선택 하거나 복제 하 여 사용자 지정을 수행 합니다.

이러한 프로필은 필요한 경우 올바른 시스템 및 공급자를 사용 하 여 설정 됩니다. XR SDK를 사용한 프로필 및 샘플 지원에 대 한 자세한 내용은 [프로필 문서를](../features/profiles/profiles.md#xr-sdk) 참조 하세요.
::: moniker-end

기존 프로필을 XR SDK로 마이그레이션하려면 다음 서비스 및 데이터 공급자를 업데이트 해야 합니다.
::: moniker range=">= mrtkunity-2021-05"
Unity 2019의 XR SDK 탭에서 또는 레거시 XR이 없는 Unity 2020 +의 주/전용 보기에서 새 데이터 공급자를 볼 수 있습니다.

![XR SDK 탭](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a>카메라

::: moniker range=">= mrtkunity-2021-05"
다음 데이터 공급자를 추가 합니다.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
보낸 사람 [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![레거시 카메라 설정](../features/images/xrsdk/CameraSystemLegacy.png)

에서
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| OpenXR 플러그 인 | Windows XR 플러그 인 |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| OpenXR 플러그 인 | Windows XR 플러그 인 |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![XR SDK 카메라 설정](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>입력

::: moniker range=">= mrtkunity-2021-05"
다음 데이터 공급자를 추가 합니다.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
보낸 사람 [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![레거시 입력 설정](../features/images/xrsdk/InputSystemWMRLegacy.png)

에서
::: moniker-end

| OpenXR 플러그 인 | Windows XR 플러그 인 |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR__:

![OpenXR 입력 설정](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![XR SDK 입력 설정](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>경계

::: moniker range=">= mrtkunity-2021-05"
다음 데이터 공급자를 추가 합니다.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
보낸 사람 [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![레거시 경계 설정](../features/images/xrsdk/BoundarySystemLegacy.png)

에서
::: moniker-end

| OpenXR 플러그 인 | Windows XR 플러그 인 |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![XR SDK 경계 설정](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>공간 인식

::: moniker range=">= mrtkunity-2021-05"
다음 데이터 공급자를 추가 합니다.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
보낸 사람 [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![레거시 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessLegacy.png)

에서
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| OpenXR 플러그 인 | Windows XR 플러그 인 |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (UWP의 경우) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (UWP의 경우) |
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (비 UWP) | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| OpenXR 플러그 인 | Windows XR 플러그 인 |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![XR SDK 공간 인식 설정](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>컨트롤러 매핑

사용자 지정 컨트롤러 매핑 프로필을 사용 하는 경우 이러한 프로필 중 하나를 열고 혼합 현실 Toolkit-> 유틸리티-> 업데이트 > 컨트롤러 매핑 프로필 메뉴 항목을 실행 하 여 새 XR SDK 컨트롤러 유형이 정의 되었는지 확인 합니다.

## <a name="see-also"></a>추가 정보

* [Unity에서 AR 개발 시작 하기](https://docs.unity3d.com/Manual/AROverview.html)
* [Unity에서 VR 개발 시작](https://docs.unity3d.com/Manual/VROverview.html)