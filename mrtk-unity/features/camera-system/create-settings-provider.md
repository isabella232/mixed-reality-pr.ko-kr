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
# <a name="creating-a-camera-settings-provider"></a><span data-ttu-id="d28de-104">카메라 설정 공급자 만들기</span><span class="sxs-lookup"><span data-stu-id="d28de-104">Creating a camera settings provider</span></span>

<span data-ttu-id="d28de-105">카메라 시스템은 플랫폼 특정 카메라 구성을 지원 하기 위한 확장 가능한 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-105">The Camera system is an extensible system for providing support for platform specific camera configurations.</span></span> <span data-ttu-id="d28de-106">새 카메라 구성에 대 한 지원을 추가 하려면 사용자 지정 설정 공급자가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-106">To add support for a new camera configuration, a custom settings provider may be required.</span></span>

> [!NOTE]
> <span data-ttu-id="d28de-107">이 예제에서 사용 되는 전체 소스 코드는 **Mrtk/Providers/UnityAR** 폴더에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-107">The complete source code used in this example can be found in the **MRTK/Providers/UnityAR** folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="d28de-108">네임 스페이스 및 폴더 구조</span><span class="sxs-lookup"><span data-stu-id="d28de-108">Namespace and folder structure</span></span>

<span data-ttu-id="d28de-109">데이터 공급자는 다음 두 가지 방법 중 하나로 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-109">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="d28de-110">타사 추가 기능</span><span class="sxs-lookup"><span data-stu-id="d28de-110">Third party add-ons</span></span>
1. <span data-ttu-id="d28de-111">Microsoft Mixed Reality Toolkit의 일부</span><span class="sxs-lookup"><span data-stu-id="d28de-111">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="d28de-112">새 데이터 공급자를 MRTK에 제출 하는 승인 프로세스는 사례별로 다르며 초기 제안의 시점에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="d28de-113">새 [ *기능 요청* 유형 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)를 만들어 제안을 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-113">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-ons"></a><span data-ttu-id="d28de-114">타사 추가 기능</span><span class="sxs-lookup"><span data-stu-id="d28de-114">Third party add-ons</span></span>

<span data-ttu-id="d28de-115">**네임스페이스**</span><span class="sxs-lookup"><span data-stu-id="d28de-115">**Namespace**</span></span>

<span data-ttu-id="d28de-116">데이터 공급자는 잠재적 이름 충돌을 완화 하기 위해 네임 스페이스가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-116">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="d28de-117">네임 스페이스는 다음 구성 요소를 포함 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-117">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="d28de-118">추가 기능을 생성 하는 회사 이름</span><span class="sxs-lookup"><span data-stu-id="d28de-118">Company name producing the add-on</span></span>
- <span data-ttu-id="d28de-119">기능 영역</span><span class="sxs-lookup"><span data-stu-id="d28de-119">Feature area</span></span>

<span data-ttu-id="d28de-120">예를 들어 Contoso 회사에서 만들고 제공 하는 카메라 설정 공급자는 *"MixedReality"* 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-120">For example, a camera settings provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.Camera"*.</span></span>

<span data-ttu-id="d28de-121">**폴더 구조**</span><span class="sxs-lookup"><span data-stu-id="d28de-121">**Folder structure**</span></span>

<span data-ttu-id="d28de-122">다음 이미지와 같이 폴더 계층 구조에서 데이터 공급자에 대 한 소스 코드를 레이아웃 되도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-122">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![폴더 구조의 예](../images/camera-system/ExampleProviderFolderStructure.png)

<span data-ttu-id="d28de-124">*ContosoCamera* 폴더에는 데이터 공급자의 구현이 포함 되 고, *Editor* 폴더에는 검사기 (및 기타 Unity 편집기 관련 코드)가 포함 되며, *Profiles* 폴더에는 미리 작성 된 프로필 스크립트 가능한 개체가 하나 이상 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-124">Where the *ContosoCamera* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="d28de-125">MRTK 제출</span><span class="sxs-lookup"><span data-stu-id="d28de-125">MRTK submission</span></span>

<span data-ttu-id="d28de-126">**네임스페이스**</span><span class="sxs-lookup"><span data-stu-id="d28de-126">**Namespace**</span></span>

<span data-ttu-id="d28de-127">카메라 설정 공급자가 [Mixed Reality Toolkit 리포지토리에](https://github.com/Microsoft/MixedRealityToolkit-Unity)제출 되는 경우 네임 스페이스는 MixedReality (예: *MixedReality CameraSystem*)로 시작 **해야** 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-127">If a camera settings provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.CameraSystem*).</span></span>

<span data-ttu-id="d28de-128">**폴더 구조**</span><span class="sxs-lookup"><span data-stu-id="d28de-128">**Folder structure**</span></span>

<span data-ttu-id="d28de-129">모든 코드는 MRTK/Providers (예: MRTK/Providers/UnityAR) 아래에 있는 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-129">All code must be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/UnityAR).</span></span>

## <a name="define-the-camera-settings-object"></a><span data-ttu-id="d28de-130">카메라 설정 개체 정의</span><span class="sxs-lookup"><span data-stu-id="d28de-130">Define the camera settings object</span></span>

<span data-ttu-id="d28de-131">카메라 설정 공급자를 만드는 첫 번째 단계는 응용 프로그램에 제공 하는 데이터 형식 (예: 메시 또는 평면)을 결정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-131">The first step in creating a camera settings provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="d28de-132">모든 공간 데이터 개체는 인터페이스를 구현 해야 합니다 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) .</span><span class="sxs-lookup"><span data-stu-id="d28de-132">All spatial data objects must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.</span></span>

## <a name="implement-the-settings-provider"></a><span data-ttu-id="d28de-133">설정 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="d28de-133">Implement the settings provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="d28de-134">인터페이스 및/또는 기본 클래스 상속 지정</span><span class="sxs-lookup"><span data-stu-id="d28de-134">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="d28de-135">모든 카메라 설정 공급자는 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 카메라 시스템에 필요한 최소 기능을 지정 하는 인터페이스를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-135">All camera settings providers must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, which specifies the minimum functionality required by the camera system.</span></span> <span data-ttu-id="d28de-136">MRTK foundation에는 [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) 필요한 기능의 기본 구현을 제공 하는 클래스가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-136">The MRTK foundation includes the [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) class which provides a default implementation of the required functionality.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="d28de-137">MixedRealityDataProvider 특성 적용</span><span class="sxs-lookup"><span data-stu-id="d28de-137">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="d28de-138">카메라 설정 공급자를 만드는 핵심 단계는 특성을 클래스에 적용 하는 것입니다 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) .</span><span class="sxs-lookup"><span data-stu-id="d28de-138">A key step in creating a camera settings provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="d28de-139">이 단계에서는 데이터 공급자에 대 한 기본 프로필 및 플랫폼을 카메라 시스템 프로필에서 선택 하 고 이름, 폴더 경로 등으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-139">This step enables setting the default profile and platform(s) for the data provider, when selected in the Camera System profile as well as name, folder path, and more.</span></span>

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="d28de-140">IMixedRealityDataProvider 메서드 구현</span><span class="sxs-lookup"><span data-stu-id="d28de-140">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="d28de-141">클래스가 정의 되 면 다음 단계는 인터페이스의 구현을 제공 하는 것입니다 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) .</span><span class="sxs-lookup"><span data-stu-id="d28de-141">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="d28de-142">클래스를 [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) 통해 클래스는 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 메서드에 대해 빈 구현을 제공 합니다 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) .</span><span class="sxs-lookup"><span data-stu-id="d28de-142">The [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="d28de-143">이러한 메서드의 세부 정보는 일반적으로 데이터 공급자별로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-143">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="d28de-144">데이터 공급자에 의해 구현 되어야 하는 메서드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-144">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> <span data-ttu-id="d28de-145">모든 설정 공급자가 이러한 모든 메서드에 대 한 구현을 필요로 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-145">Not all settings providers will require implementations for all of these methods.</span></span> <span data-ttu-id="d28de-146">최소한으로 구현 하는 것이 좋습니다 `Destroy()` `Initialize()` .</span><span class="sxs-lookup"><span data-stu-id="d28de-146">It is highly recommended that `Destroy()` and `Initialize()` be implemented at a minimum.</span></span>

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="d28de-147">데이터 공급자 논리 구현</span><span class="sxs-lookup"><span data-stu-id="d28de-147">Implement the data provider logic</span></span>

<span data-ttu-id="d28de-148">다음 단계는 를 구현하여 설정 공급자의 논리를 추가하는 [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-148">The next step is to add the logic of the settings provider by implementing [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider).</span></span> <span data-ttu-id="d28de-149">데이터 공급자의 이 부분은 일반적으로 카메라 구성에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-149">This portion of the data provider will typically be camera configuration specific.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="d28de-150">프로필 및 검사기 만들기</span><span class="sxs-lookup"><span data-stu-id="d28de-150">Create the profile and inspector</span></span>

<span data-ttu-id="d28de-151">Mixed Reality 도구 키트에서 데이터 공급자는 프로필을 사용하여 [구성됩니다.](../profiles/profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d28de-151">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="d28de-152">프로필 정의</span><span class="sxs-lookup"><span data-stu-id="d28de-152">Define the profile</span></span>

<span data-ttu-id="d28de-153">프로필 콘텐츠는 개발자가 선택할 수 있는 구성 옵션을 미러해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-153">Profile contents should mirror the developer selectable configuration options.</span></span> <span data-ttu-id="d28de-154">각 인터페이스에 정의된 사용자 구성 가능한 속성도 프로필에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-154">Any user configurable properties defined in each interface should also be contained with the profile.</span></span>

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

<span data-ttu-id="d28de-155">`CreateAssetMenu`특성은 프로필 클래스에 적용하여 고객이 자산 만들기 Mixed Reality 도구 키트 프로필 메뉴를 사용하여 프로필 인스턴스를 **만들** 수 있도록  >    >    >   합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-155">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="d28de-156">검사기 구현</span><span class="sxs-lookup"><span data-stu-id="d28de-156">Implement the inspector</span></span>

<span data-ttu-id="d28de-157">프로필 검사자는 프로필 콘텐츠를 구성하고 보기 위한 사용자 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-157">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="d28de-158">각 프로필 검사기에서 클래스를 확장해야 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-158">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="d28de-159">`CustomEditor`특성은 검사자가 적용되는 자산 유형을 Unity에 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-159">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="d28de-160">어셈블리 정의 만들기</span><span class="sxs-lookup"><span data-stu-id="d28de-160">Create assembly definition(s)</span></span>

<span data-ttu-id="d28de-161">Mixed Reality 도구 키트는 어셈블리 정의([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 파일을 사용하여 구성 요소 간의 의존성을 지정하고 Unity를 통해 컴파일 시간을 단축합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-161">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="d28de-162">모든 데이터 공급자 및 해당 편집기 구성 요소에 대해 어셈블리 정의 파일을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-162">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="d28de-163">이전 예제의 [폴더 구조를](#namespace-and-folder-structure) 사용하면 ContosoCamera 데이터 공급자에 대한 두 개의 .asmdef 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-163">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoCamera data provider.</span></span>

<span data-ttu-id="d28de-164">첫 번째 어셈블리 정의는 데이터 공급자에 대한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-164">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="d28de-165">이 예제에서는 ContosoCamera라고 하며 예제의 *ContosoCamera* 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-165">For this example, it will be called ContosoCamera and will be located in the example's *ContosoCamera* folder.</span></span> <span data-ttu-id="d28de-166">이 어셈블리 정의는 Microsoft.MixedReality.Toolkit 및 해당 어셈블리가 종속된 다른 어셈블리에 대한 종속성을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-166">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="d28de-167">ContosoCameraEditor 어셈블리 정의는 프로필 검사자와 편집기별 코드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-167">The ContosoCameraEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="d28de-168">이 파일은 편집기 코드의 루트 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-168">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="d28de-169">이 예제에서 파일은 *ContosoCamera\Editor* 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-169">In this example, the file will be located in the *ContosoCamera\Editor* folder.</span></span> <span data-ttu-id="d28de-170">이 어셈블리 정의에는 ContosoCamera 어셈블리에 대 한 참조 및가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-170">This assembly definition will contain a reference to the ContosoCamera assembly as well as:</span></span>

- <span data-ttu-id="d28de-171">MixedReality</span><span class="sxs-lookup"><span data-stu-id="d28de-171">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="d28de-172">MixedReality. 검사기</span><span class="sxs-lookup"><span data-stu-id="d28de-172">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="d28de-173">MixedReality. 유틸리티</span><span class="sxs-lookup"><span data-stu-id="d28de-173">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="d28de-174">데이터 공급자 등록</span><span class="sxs-lookup"><span data-stu-id="d28de-174">Register the data provider</span></span>

<span data-ttu-id="d28de-175">데이터 공급자를 만든 후에는 응용 프로그램에서 사용할 카메라 시스템에 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-175">Once created, the data provider can be registered with the Camera system to be used in the application.</span></span>

![카메라 설정 공급자 선택](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="d28de-177">패키징 및 배포</span><span class="sxs-lookup"><span data-stu-id="d28de-177">Packaging and distribution</span></span>

<span data-ttu-id="d28de-178">타사 구성 요소로 배포 되는 데이터 공급자에는 개발자의 기본 설정에 대 한 패키징 및 배포에 대 한 구체적인 정보가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-178">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="d28de-179">가장 일반적인 해결책은 unitypackage를 생성 하 고 Unity Asset Store를 통해 배포 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-179">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="d28de-180">Microsoft Mixed Reality Toolkit 패키지의 일부로 데이터 공급자를 제출 하 고 수락한 경우 Microsoft MRTK 팀은 MRTK 제품의 일부로 패키지 하 고 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="d28de-180">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="d28de-181">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d28de-181">See also</span></span>

- [<span data-ttu-id="d28de-182">카메라 시스템 개요</span><span class="sxs-lookup"><span data-stu-id="d28de-182">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="d28de-183">`BaseCameraSettingsProvider` 클래스</span><span class="sxs-lookup"><span data-stu-id="d28de-183">`BaseCameraSettingsProvider` class</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [<span data-ttu-id="d28de-184">`IMixedRealityCameraSettingsProvider` 감열재</span><span class="sxs-lookup"><span data-stu-id="d28de-184">`IMixedRealityCameraSettingsProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [<span data-ttu-id="d28de-185">`IMixedRealityDataProvider` 감열재</span><span class="sxs-lookup"><span data-stu-id="d28de-185">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
