---
title: 공간 인식 Data Provider 만들기
description: MRTK에서 사용자 지정 데이터 공급자를 만드는 방법을 설명 합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 04a0cdbd18f666b6a99c120eb28966234cc8c92d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145156"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a>공간 인식 시스템 데이터 공급자 만들기

공간 인식 시스템은 응용 프로그램에 실제 환경에 대 한 데이터를 제공 하기 위한 확장 가능한 시스템입니다. 새 하드웨어 플랫폼에 대 한 지원을 추가 하거나 새로운 형식의 공간 인식 데이터를 추가 하려면 사용자 지정 데이터 공급자가 필요할 수 있습니다.

이 문서에서는 공간 인식 시스템에 대해 공간 관찰자 라고도 하는 [사용자 지정 데이터 공급자](../../architecture/systems-extensions-providers.md)를 만드는 방법을 설명 합니다. 여기에 표시 된 예제 코드는 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) [편집기에서 3d 메시 데이터를 로드 하](spatial-object-mesh-observer.md)는 데 유용 하 게 사용할 수 있는 클래스 구현에서 가져온 것입니다.

> [!NOTE]
> 이 예제에서 사용 되는 전체 소스 코드는 폴더에 있습니다 `Assets/MRTK/Providers/ObjectMeshObserver` .

## <a name="namespace-and-folder-structure"></a>네임 스페이스 및 폴더 구조

데이터 공급자는 다음 두 가지 방법 중 하나로 배포할 수 있습니다.

1. 타사 추가 기능
1. Microsoft Mixed Reality Toolkit의 일부

새 데이터 공급자를 MRTK에 제출 하는 승인 프로세스는 사례별로 다르며 초기 제안의 시점에 전달 됩니다. 새 [ *기능 요청* 유형 문제](https://github.com/microsoft/MixedRealityToolkit-Unity/issues)를 만들어 제안을 제출할 수 있습니다.

### <a name="third-party-add-on"></a>타사 추가 기능

**네임스페이스**

데이터 공급자는 잠재적 이름 충돌을 완화 하기 위해 네임 스페이스가 필요 합니다. 네임 스페이스는 다음 구성 요소를 포함 하는 것이 좋습니다.

- 추가 기능을 생성 하는 회사 이름
- 기능 영역

예를 들어 Contoso 회사에서 만들고 제공 하는 공간 인식 데이터 공급자는 *"MixedReality"* 일 수 있습니다.

**폴더 구조**

다음 이미지와 같이 폴더 계층 구조에서 데이터 공급자에 대 한 소스 코드를 레이아웃 되도록 하는 것이 좋습니다.

![폴더 구조의 예](../images/spatial-awareness/ExampleProviderFolderStructure.png)

*ContosoSpatialAwareness* 폴더에 데이터 공급자의 구현이 포함된 경우 *Editor* 폴더에는 검사기(및 다른 Unity 편집기 관련 코드)가 포함되고 *Profiles* 폴더에는 미리 만들어진 프로필 스크립팅 가능 개체가 하나 이상 포함되어 있습니다.

### <a name="mrtk-submission"></a>MRTK 제출

**네임스페이스**

공간 인식 시스템 데이터 공급자가 [Mixed Reality Toolkit 리포지토리에](https://github.com/Microsoft/MixedRealityToolkit-Unity)제출되는 경우 네임스페이스는 Microsoft.MixedReality.Toolkit(예: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver)로* 시작해야 **합니다.**

 및 코드는 MRTK/Providers(예: *MRTK/Providers/ObjectMeshObserver) 아래의* 폴더에 있어야 합니다.

**폴더 구조**

모든 코드는 MRTK/Providers(예: MRTK/Providers/ObjectMeshObserver) 아래의 폴더에 있어야 합니다.

## <a name="define-the-spatial-data-object"></a>공간 데이터 개체 정의

공간 인식 데이터 공급자를 만드는 첫 번째 단계는 애플리케이션에 제공할 데이터 형식(예: 메시 또는 평면)을 결정하는 것입니다.

모든 공간 데이터 개체는 인터페이스를 구현해야 [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) 합니다.

Mixed Reality 도구 키트 기반은 새 데이터 공급자에서 사용하거나 확장할 수 있는 다음과 같은 공간 개체를 제공합니다.

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a>데이터 공급자 구현

### <a name="specify-interface-andor-base-class-inheritance"></a>인터페이스 및/또는 기본 클래스 상속 지정

모든 공간 인식 데이터 공급자는 공간 인식 [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) 시스템에 필요한 최소 기능을 지정하는 인터페이스를 구현해야 합니다. MRTK 기초에는 [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) 이 필수 기능의 기본 구현을 제공하는 클래스가 포함되어 있습니다.

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)인터페이스는 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 클래스에서 SpatialAwarenessMesh 기능에 대한 지원을 제공한다는 것을 나타내기 위해 사용됩니다.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>MixedRealityDataProvider 특성 적용

공간 인식 데이터 공급자를 만드는 주요 단계는 [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) 특성을 클래스에 적용하는 것입니다. 이 단계에서는 공간 인식 프로필 및 이름, 폴더 경로 등에서 선택한 경우 데이터 공급자에 대한 기본 프로필 및 플랫폼을 설정할 수 있습니다.

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>IMixedRealityDataProvider 메서드 구현

클래스가 정의되면 다음 단계는 인터페이스의 구현을 제공하는 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 것입니다.

> [!NOTE]
> [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)클래스를 통해 [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) 클래스는 메서드에 대한 빈 구현만 [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) 제공합니다. 이러한 메서드의 세부 정보는 일반적으로 데이터 공급자별로 다릅니다.

데이터 공급자가 구현해야 하는 메서드는 다음과 같습니다.

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>데이터 공급자 논리 구현

다음 단계는 특정 데이터 공급자 인터페이스(예: )를 구현하여 데이터 공급자의 논리를 추가하는 [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) 것입니다. 데이터 공급자의 이 부분은 일반적으로 플랫폼별로 다릅니다.

### <a name="observation-change-notifications"></a>관찰 변경 알림

애플리케이션이 디바이스의 환경 이해 변경에 응답할 수 있도록 데이터 공급자는 인터페이스에 정의된 대로 알림 이벤트를 [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) 발생합니다.

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 예제의 다음 코드에서는 [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) 메시 데이터가 추가되면 및 이벤트가 발생되는 것을 보여 있습니다.

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) `OnObservationUpdated` 3D 모델이 한 번만 로드되므로 클래스는 이벤트를 발생시키지 않습니다. 구현을 클래스 관찰 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) 된 메시에 대 한 이벤트를 발생 하는 예제를 제공 `OnObservationUpdated` 합니다.

### <a name="add-unity-profiler-instrumentation"></a>Unity Profiler 계측 추가

성능은 혼합 현실 애플리케이션에서 매우 중요합니다. 모든 구성 요소는 애플리케이션이 고려해야 하는 약간의 오버헤드를 추가합니다. 이를 위해 모든 공간 인식 데이터 공급자는 내부 루프 및 자주 활용되는 코드 경로에 Unity Profiler 계측을 포함하는 것이 중요합니다.

사용자 지정 공급자를 계측할 때 MRTK에서 사용하는 패턴을 구현하는 것이 좋습니다.

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> 프로파일러 표식 식별에 사용되는 이름은 임의로 지정됩니다. MRTK는 다음 패턴을 사용합니다.
>
> "[product] className. methodName-선택 사항
>
> 사용자 지정 데이터 공급자는 추적을 분석할 때 특정 구성 요소 및 메서드를 쉽게 식별할 수 있도록 비슷한 패턴을 따르는 것이 좋습니다.

## <a name="create-the-profile-and-inspector"></a>프로필 및 검사기 만들기

혼합 현실 도구 키트에서 데이터 공급자는 [프로필](../profiles/profiles.md)을 사용 하 여 구성 됩니다.

### <a name="define-the-profile"></a>프로필 정의

프로필 콘텐츠는 데이터 공급자의 액세스 가능 속성 (예: 업데이트 간격)을 미러링합니다. 각 인터페이스에 정의 된 모든 사용자 구성 가능 속성은 프로필에 포함 되어야 합니다.

기본 클래스는 새 데이터 공급자가 기존 공급자를 확장 하는 경우에 권장 됩니다. 예를 들어는를 [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) 확장 [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) 하 여 고객이 환경 데이터로 사용할 3d 모델을 제공할 수 있도록 합니다.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

`CreateAssetMenu`특성을 프로필 클래스에 적용 하 여 고객이 asset   >    >  **Mixed Reality 도구 키트**  >  **프로필** 만들기 메뉴를 사용 하 여 프로필 인스턴스를 만들 수 있도록 할 수 있습니다.

### <a name="implement-the-inspector"></a>검사기 구현

프로필 검사기는 프로필 내용을 구성 하 고 볼 수 있는 사용자 인터페이스입니다. 각 프로필 검사자는 클래스를 확장 해야 합니다 [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) .

`CustomEditor`특성은 검사기가 적용 되는 자산의 유형을 Unity에 알려 줍니다.

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a>어셈블리 정의 만들기

Mixed Reality Toolkit에서는 어셈블리 정의 ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) 파일을 사용 하 여 구성 요소 간의 종속성을 지정 하 고 컴파일 시간을 단축 하는 Unity를 지원할 수 있습니다.

모든 데이터 공급자와 해당 편집기 구성 요소에 대해 어셈블리 정의 파일을 만드는 것이 좋습니다.

이전 예제에서 [폴더 구조](#namespace-and-folder-structure) 를 사용 하는 경우 ContosoSpatialAwareness 데이터 공급자에 대 한 두 개의. asmdef 파일이 있습니다.

첫 번째 어셈블리 정의는 데이터 공급자에 대 한 것입니다. 이 예에서는 ContosoSpatialAwareness 라고 하 고 예제의 *ContosoSpatialAwareness* 폴더에 배치 됩니다. 이 어셈블리 정의는 Microsoft.MixedReality.Toolkit 및 해당 어셈블리가 종속된 다른 어셈블리에 대한 종속성을 지정해야 합니다.

ContosoInputEditor 어셈블리 정의는 프로필 검사자와 편집기별 코드를 지정합니다. 이 파일은 편집기 코드의 루트 폴더에 있어야 합니다. 이 예제에서 파일은 *ContosoSpatialAwareness\Editor 폴더에* 있습니다. 이 어셈블리 정의에는 ContosoSpatialAwareness 어셈블리에 대한 참조도 포함됩니다.

- Microsoft.MixedReality.Toolkit
- Microsoft.MixedReality.Toolkit.Editor.Inspectors
- Microsoft.MixedReality.Toolkit.Editor.Utilities

## <a name="register-the-data-provider"></a>데이터 공급자 등록

데이터 공급자를 만든 후에는 애플리케이션에서 사용할 공간 인식 시스템에 등록할 수 있습니다.

![공간 개체 메시 관찰자 선택](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a>패키징 및 배포

타사 구성 요소로 배포되는 데이터 공급자에는 패키징 및 배포에 대한 구체적인 세부 정보가 개발자의 기본 설정으로 남아 있습니다. 가장 일반적인 솔루션은 .unitypackage를 생성하고 Unity 자산 저장소를 통해 배포하는 것입니다.

Microsoft Mixed Reality Toolkit 패키지의 일부로 데이터 공급자를 제출하고 수락하는 경우 Microsoft MRTK 팀은 이를 MRTK 제품의 일부로 패키지하고 배포합니다.

## <a name="see-also"></a>참고 항목

- [공간 인식 시스템](spatial-awareness-getting-started.md)
- [`IMixedRealitySpatialAwarenessObject` 인터페이스](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [`BaseSpatialAwarenessObject` 클래스](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject` 클래스](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject` 클래스](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [`IMixedRealitySpatialAwarenessObserver` 인터페이스](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [`BaseSpatialObserver` 클래스](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [`IMixedRealitySpatialAwarenessMeshObserver` 인터페이스](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [`IMixedRealityDataProvider` 인터페이스](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` 인터페이스](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
