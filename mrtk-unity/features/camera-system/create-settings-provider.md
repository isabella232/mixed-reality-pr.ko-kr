---
title: 설정 공급자 만들기
description: MRTK의 카메라 설정에 대 한 데이터 공급자
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 6ec3fc1c88c1a32334cb2869ad1994863e55bf9a
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144891"
---
# <a name="creating-a-camera-settings-provider"></a>카메라 설정 공급자 만들기

카메라 시스템은 플랫폼 특정 카메라 구성을 지원 하기 위한 확장 가능한 시스템입니다. 새 카메라 구성에 대 한 지원을 추가 하려면 사용자 지정 설정 공급자가 필요할 수 있습니다.

> [!NOTE]
> 이 예제에서 사용 되는 전체 소스 코드는 **Mrtk/Providers/UnityAR** 폴더에서 찾을 수 있습니다.

## <a name="namespace-and-folder-structure"></a>네임 스페이스 및 폴더 구조

데이터 공급자는 다음 두 가지 방법 중 하나로 배포할 수 있습니다.

1. 타사 추가 기능
1. Microsoft Mixed Reality Toolkit의 일부

새 데이터 공급자를 MRTK에 제출 하는 승인 프로세스는 사례별로 다르며 초기 제안의 시점에 전달 됩니다. 새 [ *기능 요청* 유형 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)를 만들어 제안을 제출할 수 있습니다.

### <a name="third-party-add-ons"></a>타사 추가 기능

**네임스페이스**

데이터 공급자는 잠재적 이름 충돌을 완화 하기 위해 네임 스페이스가 필요 합니다. 네임 스페이스는 다음 구성 요소를 포함 하는 것이 좋습니다.

- 추가 기능을 생성 하는 회사 이름
- 기능 영역

예를 들어 Contoso 회사에서 만들고 제공 하는 카메라 설정 공급자는 *"MixedReality"* 일 수 있습니다.

**폴더 구조**

다음 이미지와 같이 폴더 계층 구조에서 데이터 공급자에 대 한 소스 코드를 레이아웃 되도록 하는 것이 좋습니다.

![폴더 구조의 예](../images/camera-system/ExampleProviderFolderStructure.png)

*ContosoCamera* 폴더에는 데이터 공급자의 구현이 포함 되 고, *Editor* 폴더에는 검사기 (및 기타 Unity 편집기 관련 코드)가 포함 되며, *Profiles* 폴더에는 미리 작성 된 프로필 스크립트 가능한 개체가 하나 이상 포함 되어 있습니다.

### <a name="mrtk-submission"></a>MRTK 제출

**네임스페이스**

카메라 설정 공급자가 [Mixed Reality Toolkit 리포지토리에](https://github.com/Microsoft/MixedRealityToolkit-Unity)제출 되는 경우 네임 스페이스는 MixedReality (예: *MixedReality CameraSystem*)로 시작 **해야** 합니다.

**폴더 구조**

모든 코드는 MRTK/Providers (예: MRTK/Providers/UnityAR) 아래에 있는 폴더에 있어야 합니다.

## <a name="define-the-camera-settings-object"></a>카메라 설정 개체 정의

카메라 설정 공급자를 만드는 첫 번째 단계는 응용 프로그램에 제공 하는 데이터 형식 (예: 메시 또는 평면)을 결정 하는 것입니다.

모든 공간 데이터 개체는 인터페이스를 구현 해야 합니다 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) .

## <a name="implement-the-settings-provider"></a>설정 공급자 구현

### <a name="specify-interface-andor-base-class-inheritance"></a>인터페이스 및/또는 기본 클래스 상속 지정

모든 카메라 설정 공급자는 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 카메라 시스템에 필요한 최소 기능을 지정 하는 인터페이스를 구현 해야 합니다. MRTK foundation에는 [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) 필요한 기능의 기본 구현을 제공 하는 클래스가 포함 되어 있습니다.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>MixedRealityDataProvider 특성 적용

카메라 설정 공급자를 만드는 핵심 단계는 특성을 클래스에 적용 하는 것입니다 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) . 이 단계에서는 데이터 공급자에 대 한 기본 프로필 및 플랫폼을 카메라 시스템 프로필에서 선택 하 고 이름, 폴더 경로 등으로 설정할 수 있습니다.

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>IMixedRealityDataProvider 메서드 구현

클래스가 정의 되 면 다음 단계는 인터페이스의 구현을 제공 하는 것입니다 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) .

> [!NOTE]
> 클래스를 [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) 통해 클래스는 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 메서드에 대해 빈 구현을 제공 합니다 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) . 이러한 메서드의 세부 정보는 일반적으로 데이터 공급자별로 다릅니다.

데이터 공급자에 의해 구현 되어야 하는 메서드는 다음과 같습니다.

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> 모든 설정 공급자가 이러한 모든 메서드에 대 한 구현을 필요로 하는 것은 아닙니다. 최소한으로 구현 하는 것이 좋습니다 `Destroy()` `Initialize()` .

### <a name="implement-the-data-provider-logic"></a>데이터 공급자 논리 구현

다음 단계는 를 구현하여 설정 공급자의 논리를 추가하는 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 것입니다. 데이터 공급자의 이 부분은 일반적으로 카메라 구성에 따라 다릅니다.

## <a name="create-the-profile-and-inspector"></a>프로필 및 검사기 만들기

Mixed Reality 도구 키트에서 데이터 공급자는 프로필을 사용하여 [구성됩니다.](../profiles/profiles.md)

### <a name="define-the-profile"></a>프로필 정의

프로필 콘텐츠는 개발자가 선택할 수 있는 구성 옵션을 미러해야 합니다. 각 인터페이스에 정의된 사용자 구성 가능한 속성도 프로필에 포함되어야 합니다.

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

`CreateAssetMenu`특성은 프로필 클래스에 적용하여 고객이 자산 만들기 Mixed Reality 도구 키트 프로필 메뉴를 사용하여 프로필 인스턴스를 **만들** 수 있도록  >    >    >   합니다.

### <a name="implement-the-inspector"></a>검사기 구현

프로필 검사자는 프로필 콘텐츠를 구성하고 보기 위한 사용자 인터페이스입니다. 각 프로필 검사기에서 클래스를 확장해야 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 합니다.

`CustomEditor`특성은 검사자가 적용되는 자산 유형을 Unity에 알릴 수 있습니다.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a>어셈블리 정의 만들기

Mixed Reality 도구 키트는 어셈블리 정의([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 파일을 사용하여 구성 요소 간의 의존성을 지정하고 Unity를 통해 컴파일 시간을 단축합니다.

모든 데이터 공급자 및 해당 편집기 구성 요소에 대해 어셈블리 정의 파일을 만드는 것이 좋습니다.

이전 예제의 [폴더 구조를](#namespace-and-folder-structure) 사용하면 ContosoCamera 데이터 공급자에 대한 두 개의 .asmdef 파일이 있습니다.

첫 번째 어셈블리 정의는 데이터 공급자에 대한 것입니다. 이 예제에서는 ContosoCamera라고 하며 예제의 *ContosoCamera* 폴더에 있습니다. 이 어셈블리 정의는 Microsoft.MixedReality.Toolkit 및 해당 어셈블리가 종속된 다른 어셈블리에 대한 종속성을 지정해야 합니다.

ContosoCameraEditor 어셈블리 정의는 프로필 검사자와 편집기별 코드를 지정합니다. 이 파일은 편집기 코드의 루트 폴더에 있어야 합니다. 이 예제에서 파일은 *ContosoCamera\Editor* 폴더에 있습니다. 이 어셈블리 정의에는 ContosoCamera 어셈블리에 대 한 참조 및가 포함 됩니다.

- MixedReality
- MixedReality. 검사기
- MixedReality. 유틸리티

## <a name="register-the-data-provider"></a>데이터 공급자 등록

데이터 공급자를 만든 후에는 응용 프로그램에서 사용할 카메라 시스템에 등록할 수 있습니다.

![카메라 설정 공급자 선택](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a>패키징 및 배포

타사 구성 요소로 배포 되는 데이터 공급자에는 개발자의 기본 설정에 대 한 패키징 및 배포에 대 한 구체적인 정보가 있습니다. 가장 일반적인 해결책은 unitypackage를 생성 하 고 Unity Asset Store를 통해 배포 하는 것입니다.

Microsoft Mixed Reality Toolkit 패키지의 일부로 데이터 공급자를 제출 하 고 수락한 경우 Microsoft MRTK 팀은 MRTK 제품의 일부로 패키지 하 고 배포 합니다.

## <a name="see-also"></a>참고 항목

- [카메라 시스템 개요](camera-system-overview.md)
- [`BaseCameraSettingsProvider` 클래스](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [`IMixedRealityCameraSettingsProvider` 감열재](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [`IMixedRealityDataProvider` 감열재](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
