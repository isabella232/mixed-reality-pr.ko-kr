---
title: Unity의 공간 매핑
description: Unity 혼합 현실 앱에서 렌더링을 사용하고 실제 기하 도형과 충돌하는 방법을 알아봅니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 공간 매핑, 렌더러, 충돌체, 메시, 검사, 구성 요소, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 62e4c4fad725dbe58773035b0bb47f1911098217
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905702"
---
# <a name="spatial-mapping-in-unity"></a>Unity의 공간 매핑

[공간 매핑을](../../design/spatial-mapping.md) 사용하면 HoloLens 디바이스 주위의 전 세계 표면을 나타내는 삼각형 메시를 검색할 수 있습니다. 배치, 폐색 및 공간 분석에 표면 데이터를 사용하여 Unity 프로젝트에 추가 몰입을 제공할 수 있습니다.

Unity에는 다음과 같은 방법으로 개발자에게 노출되는 공간 매핑에 대한 전체 지원이 포함되어 있습니다.

1. MixedRealityToolkit에서 사용할 수 있는 공간 매핑 구성 요소로, 공간 매핑을 시작하기 위한 편리하고 빠른 경로를 제공합니다.
2. 모든 권한을 제공하고 보다 정교한 애플리케이션별 사용자 지정을 가능하게 하는 하위 수준 공간 매핑 API

앱에서 공간 매핑을 사용하려면 AppxManifest에서 SpatialPerception 기능을 설정해야 합니다.

## <a name="device-support"></a>디바이스 지원

| 기능 | [HoloLens(1세대)](/hololens/hololens1-hardware) | [HoloLens 2](/hololens/hololens2-hardware) | [몰입형 헤드셋](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| 공간 매핑 | ✔️ | ✔️ | ❌ |

## <a name="setting-the-spatialperception-capability"></a>SpatialPerception 기능 설정

앱이 공간 매핑 데이터를 사용하려면 SpatialPerception 기능을 사용하도록 설정해야 합니다.

SpatialPerception 기능을 사용하도록 설정하는 방법:

1. Unity 편집기에서 **"플레이어 설정"** 창(> Project 설정 > Player 편집)을 엽니다.
2. **"Windows Store"** 탭에서 를 선택합니다.
3. **"게시 설정"를** 확장하고 **"기능" 목록에서 "SpatialPerception"** 기능을 **확인합니다.**

> [!NOTE]
> Unity 프로젝트를 Visual Studio 솔루션으로 이미 내보낸 경우 새 폴더로 내보내거나 Visual Studio [AppxManifest에서 이 기능을](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)수동으로 설정해야 합니다.

공간 매핑에는 10.0.10586.0 이상의 MaxVersionTested가 필요합니다.

1. Visual Studio 솔루션 탐색기 **Package.appxmanifest를** 마우스 오른쪽 단추로 클릭하고 코드 **보기를** 선택합니다.
2. **TargetDeviceFamily를** 지정하는 줄을 찾고 **MaxVersionTested="10.0.10240.0"을** **MaxVersionTested="10.0.10586.0"으로** 변경합니다.
3. Package.appxmanifest를 **저장합니다.**

## <a name="how-to-add-mapping-in-unity"></a>Unity에서 매핑을 추가하는 방법

[!INCLUDE[](includes/unity-spatial-mapping.md)]

## <a name="higher-level-mesh-analysis-spatial-understanding"></a>상위 수준 메시 분석: 공간 이해

> [!CAUTION]
> Spatial Understanding은 [Scene Understanding](../../design/scene-understanding.md)을 위해 더 이상 사용되지 않습니다.

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit는</a> Unity의 홀로그램 API를 기반으로 하는 홀로그램 개발을 위한 유틸리티 코드 컬렉션입니다.

### <a name="spatial-understanding"></a>공간 이해

실제 세계에 홀로그램을 배치하는 경우 공간 매핑의 메시 및 표면 평면을 벗어나는 것이 바람직한 경우가 많습니다. 배치가 절차적으로 수행되면 더 높은 수준의 환경 이해가 바람직합니다. 이를 위해서는 일반적으로 바닥, 상한 및 벽이 무엇인지 결정해야 합니다. 또한 배치 제약 조건 집합에 대해 최적화하여 홀로그램 개체에 가장 적합한 물리적 위치를 결정할 수 있습니다.

Young Conker 및 Fragments를 개발하는 동안 Asobo Studios는 방 해결기 개발로 이 문제에 직면했습니다. 이러한 각 게임에는 게임별 요구 사항이 있었지만 핵심 공간 이해 기술을 공유했습니다. HoloToolkit.SpatialUnderstanding 라이브러리는 이 기술을 캡슐화하여 벽에서 빈 공간을 빠르게 찾고, 개체를 최대값에 배치하고, 문자가 배치되도록 식별하며, 수많은 기타 공간 이해 쿼리를 할 수 있도록 합니다.

모든 소스 코드가 포함되어 있어 요구 사항에 맞게 사용자 지정하고 개선 사항을 커뮤니티와 공유할 수 있습니다. C++ 해결기용 코드는 UWP dll로 래핑되고 MixedRealityToolkit 내에 포함된 프리팹 드롭으로 Unity에 노출되었습니다.

### <a name="understanding-modules"></a>모듈 이해

모듈에서 노출하는 세 가지 기본 인터페이스는 간단한 표면 및 공간 쿼리용 토폴로지, 개체 검색을 위한 셰이프 및 개체 집합의 제약 조건 기반 배치를 위한 개체 배치 해결기입니다. 아래에서는 이러한 각 방법에 대해 설명합니다. 세 가지 기본 모듈 인터페이스 외에도 광선 캐스팅 인터페이스를 사용하여 태그가 지정된 표면 형식을 검색할 수 있으며 사용자 지정 watertight 플레이스페이스 메시를 복사할 수 있습니다.

### <a name="ray-casting"></a>광선 캐스팅

방 스캔이 완료되면 바닥, 상한 및 벽과 같은 표면에 대한 레이블이 내부적으로 생성됩니다. `PlayspaceRaycast`이 함수는 광선을 가져와서 광선이 알려진 표면과 충돌하는 경우 를 반환하고, 그렇다면 해당 표면에 대한 정보를 형식으로 `RaycastResult` 반환합니다.

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology,
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface,
                    //  but vertical surface that looks like a
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

내부적으로 raycast는 재생 영역의 계산된 8cm 복셀 표현에 대해 계산됩니다. 각 복셀에는 처리된 토폴로지 데이터(즉, 표면)가 있는 표면 요소 집합이 포함되어 있습니다. 교차된 복셀 셀 내에 포함된 복셀을 비교하고 토폴로지 정보를 조회하는 데 가장 적합한 일치를 비교합니다. 이 토폴로지 데이터에는 교차된 표면의 표면 영역뿐만 아니라 "SurfaceTypes" 열거형의 형태로 반환된 레이블 지정이 포함됩니다.

Unity 샘플에서 커서는 각 프레임에 광선을 캐스팅합니다. 먼저 Unity의 충돌체에 대해 둘째, 이해 모듈의 세계 표현에 대한 것입니다. 마지막으로, 다시 UI 요소입니다. 이 애플리케이션에서 UI는 우선 순위를 가져오고 그 다음에는 결과를 이해하고 마지막으로 Unity의 충돌체를 가져옵니다. SurfaceType은 커서 옆에 있는 텍스트로 보고됩니다.

![표면 유형은 커서 옆에 레이블이 지정됩니다.](images/su-raycastresults-300px.jpg)<br>
*표면 유형은 커서 옆에 레이블이 지정됩니다.*

### <a name="topology-queries"></a>토폴로지 쿼리

DLL 내에서 토폴로지 관리자는 환경의 레이블 지정을 처리합니다. 위에서 설명한 것처럼 대부분의 데이터는 복셀 볼륨 내에 포함된, 파셸 내에 저장됩니다. 또한 "PlaySpaceInfos" 구조는 세계 맞춤(아래의 자세한 내용), 바닥 및 최대 높이를 포함하여 플레이스페이스에 대한 정보를 저장하는 데 사용됩니다. 추론은 바닥, 최면 및 벽 결정에 사용됩니다. 예를 들어 1m2보다 큰 표면이 있는 가장 크고 가장 낮은 가로 표면은 바닥으로 간주됩니다.

> [!NOTE]
> 검색 프로세스 중에 카메라 경로도 이 프로세스에 사용됩니다.

토폴로지 관리자가 노출하는 쿼리의 하위 집합은 dll을 통해 노출됩니다. 노출된 토폴로지 쿼리는 다음과 같습니다.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

각 쿼리에는 쿼리 유형에 한정된 매개 변수 집합이 있습니다. 다음 예제에서 사용자는 원하는 볼륨의 최소 높이 & 너비, 바닥 위의 최소 배치 높이 및 볼륨 앞의 최소 제한량을 지정합니다. 모든 측정값은 미터 단위입니다.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

이러한 각 쿼리는 "TopologyResult" 구조체의 미리 할당된 배열을 취합니다. "locationCount" 매개 변수는 전달된 배열의 길이를 지정합니다. 반환 값은 반환된 위치의 수를 보고합니다. 이 숫자는 전달된 "locationCount" 매개 변수보다 크지 않습니다.

"TopologyResult"에는 반환된 볼륨의 중심 위치, 방향(즉, 보통) 및 찾은 공간의 크기가 포함됩니다.

```cpp
struct TopologyResult
{
    DirectX::XMFLOAT3 position;
    DirectX::XMFLOAT3 normal;
    float width;
    float length;
};
```

> [!NOTE]
> Unity 샘플에서 이러한 각 쿼리는 가상 UI 패널의 단추에 연결됩니다. 샘플에서는 이러한 각 쿼리에 대한 매개 변수를 적절한 값으로 하드 코딩합니다. 자세한 예제는 샘플 코드에서 SpaceVisualizer.cs를 참조하세요.

### <a name="shape-queries"></a>셰이프 쿼리

dll에서 도형 분석기("ShapeAnalyzer_W")는 토폴로지 분석기를 사용하여 사용자가 정의한 사용자 지정 셰이프와 일치합니다. Unity 샘플은 셰이프 집합을 정의하고 셰이프 탭 내의 앱 내 쿼리 메뉴를 통해 결과를 노출합니다. 사용자가 자신의 개체 셰이프 쿼리를 정의하고 애플리케이션에 필요한 대로 해당 쿼리를 사용할 수 있습니다.

셰이프 분석은 가로 표면에서만 작동합니다. 예를 들어, couch는 평면 시트 표면과 평면 상단의 다시에 의해 정의됩니다. 셰이프 쿼리는 두 표면이 정렬되고 연결된 특정 크기, 높이 및 가로 세로 범위의 두 표면을 찾습니다. API 용어를 사용하여 couch seat 및 back top은 셰이프 구성 요소이고 맞춤 요구 사항은 셰이프 구성 요소 제약 조건입니다.

Unity 샘플(ShapeDefinition.cs)에서 "sittable" 개체에 대해 정의된 예제 쿼리는 다음과 같습니다.

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

각 셰이프 쿼리는 구성 요소 간의 의존도를 나열하는 일련의 구성 요소 제약 조건 및 셰이프 제약 조건 집합이 있는 셰이프 구성 요소 집합에 의해 정의됩니다. 이 예제에는 단일 구성 요소 정의에 세 개의 제약 조건이 포함되며 구성 요소 간에는 셰이프 제약 조건이 없습니다(하나의 구성 요소만 있기 때문에).

반면, couch 셰이프에는 두 개의 셰이프 구성 요소와 4개의 셰이프 제약 조건이 있습니다. 구성 요소는 사용자의 구성 요소 목록에서 해당 인덱스로 식별됩니다(이 예제에서는 0과 1).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

래퍼 함수는 사용자 지정 셰이프 정의를 쉽게 만들 수 있는 Unity 모듈에 제공됩니다. 구성 요소 및 셰이프 제약 조건의 전체 목록은 "ShapeComponentConstraint" 및 "ShapeConstraint" 구조체 내의 "SpatialUnderstandingDll.cs"에서 찾을 수 있습니다.

![사각형 모양이 이 화면에 있습니다.](images/su-shapequery-300px.jpg)<br>
*사각형 모양이 이 화면에 있습니다.*

### <a name="object-placement-solver"></a>개체 배치 해결기

개체 배치 해결기를 사용하여 개체를 배치할 실제 공간의 이상적인 위치를 식별할 수 있습니다. 해결기에서 개체 규칙 및 제약 조건이 지정된 경우 가장 적합한 위치를 찾습니다. 또한 개체 쿼리는 "Solver_RemoveObject" 또는 "Solver_RemoveAllObjects" 호출을 통해 개체가 제거될 때까지 유지되어 제한된 다중 개체 배치를 허용합니다. 개체 배치 쿼리는 매개 변수가 있는 배치 유형, 규칙 목록 및 제약 조건 목록의 세 부분으로 구성됩니다. 쿼리를 실행하려면 다음 API를 사용합니다.

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

이 함수는 개체 이름, 배치 정의 및 규칙 및 제약 조건 목록을 가져옵니다. C# 래퍼는 규칙 및 제약 조건을 쉽게 만들 수 있는 구조 도우미 함수를 제공합니다. 배치 정의에는 쿼리 형식, 즉 다음 중 하나가 포함됩니다.

```cpp
public enum PlacementType
{
    Place_OnFloor,
    Place_OnWall,
    Place_OnCeiling,
    Place_OnShape,
    Place_OnEdge,
    Place_OnFloorAndCeiling,
    Place_RandomInAir,
    Place_InMidAir,
    Place_UnderFurnitureEdge,
};
```

각 배치 형식에는 형식에 고유한 매개 변수 집합이 있습니다. "ObjectPlacementDefinition" 구조체에는 이러한 정의를 만들기 위한 정적 도우미 함수 집합이 포함되어 있습니다. 예를 들어 개체를 층으로 배치할 위치를 찾으려면 다음 함수를 사용할 수 있습니다. public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) 배치 유형 외에도 규칙 및 제약 조건 집합을 제공할 수 있습니다. 규칙을 위반할 수 없습니다. 형식 및 규칙을 충족하는 가능한 배치 위치는 최적의 배치 위치를 선택하기 위해 제약 조건 집합에 대해 최적화됩니다. 제공된 정적 생성 함수에서 각 규칙 및 제약 조건을 만들 수 있습니다. 예제 규칙 및 제약 조건 구성 함수는 다음과 같습니다.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

아래 개체 배치 쿼리는 반 미터 큐브를 표면 가장자리에 배치할 위치를 찾고 있습니다. 이 위치는 이전에 배치된 다른 개체에서 멀리 떨어져 있고 공간의 중심 근처에 있습니다.

```cs
List<ObjectPlacementRule> rules =
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints =
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f),
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

성공하면 배치 위치, 차원 및 방향을 포함하는 "ObjectPlacementResult" 구조체가 반환됩니다. 또한 배치된 개체의 dll 내부 목록에 배치가 추가됩니다. 후속 배치 쿼리는 이 개체를 고려합니다. Unity 샘플의 "LevelSolver.cs" 파일에는 더 많은 예제 쿼리가 포함되어 있습니다.

![개체 배치 결과](images/su-objectplacement-1000px.jpg)<br>
*그림 3: 파란색 상자는 카메라 위치 규칙에서 벗어난 바닥 쿼리의 3개 위치 결과*

수준 또는 애플리케이션 시나리오에 필요한 여러 개체의 배치 위치를 해결하는 경우 먼저 공백을 찾을 수 있는 확률을 최대화하기 위해 필수 및 큰 개체를 해결합니다. 배치 순서가 중요합니다. 개체 배치를 찾을 수 없는 경우 덜 제한된 구성을 시도합니다. 대체 구성 집합을 갖는 것은 여러 실내 구성에서 기능을 지원하는 데 중요합니다.

### <a name="room-scanning-process"></a>실내 검색 프로세스

HoloLens 제공하는 공간 매핑 솔루션은 전체 문제 공간 영역의 요구 사항을 충족할 만큼 충분히 일반적이도록 설계되었지만 공간 이해 모듈은 두 가지 특정 게임의 요구 사항을 지원하도록 빌드되었습니다. 솔루션은 특정 프로세스와 가정 집합을 중심으로 구성되며 아래에 요약되어 있습니다.

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

사용자 기반 플레이스페이스 "그리기" – 스캔 단계에서 사용자는 재생 속도를 이동하고 둘러보며 포함해야 하는 영역을 효과적으로 그렸습니다. 생성된 메시는 이 단계에서 사용자 피드백을 제공하는 데 중요합니다. 실내 홈 또는 사무실 설정 – 쿼리 함수는 직각으로 평면 표면과 벽 주위에 설계되었습니다. 소프트 제한 사항입니다. 그러나 검색 단계 중에 주 축과 보조 축을 따라 메시 공간을 최적화하기 위해 기본 축 분석이 완료됩니다. 포함된 SpatialUnderstanding.cs 파일은 검사 단계 프로세스를 관리합니다. 다음 함수를 호출합니다.

```txt
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan –
    Called each frame to update the scanning process. The camera position and
    orientation is passed in and is used for the playspace painting process,
    described above.

GeneratePlayspace_RequestFinish –
    Called to finalize the playspace. This will use the areas “painted” during
    the scan phase to define and lock the playspace. The application can query
    statistics during the scanning phase as well as query the custom mesh for
    providing user feedback.

Import_UnderstandingMesh –
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by
    the module and placed on the understanding prefab will periodically query the
    custom mesh generated by the process. In addition, this is done once more
    after scanning has been finalized.
```

"SpatialUnderstanding" 동작에 의해 구동되는 검색 흐름은 InitScan을 호출한 다음, UpdateScan 각 프레임을 호출합니다. 통계 쿼리가 적절한 검사를 보고하면 사용자는 RequestFinish를 호출하여 검사 단계의 끝을 나타내는 airtap을 할 수 있습니다. UpdateScan은 dll이 처리를 완료했음을 반환 값으로 표시할 때까지 계속 호출됩니다.

### <a name="understanding-mesh"></a>메시 이해

understanding dll은 내부적으로 플레이스페이스를 8cm 크기의 복셀 큐브 그리드로 저장합니다. 검사의 초기 부분에서는 기본 구성 요소 분석을 완료하여 방의 축을 확인합니다. 내부적으로 이러한 축에 맞춰진 복셀 공간을 저장합니다. 메시는 복셀 볼륨에서 isosurface를 추출하여 약 1초마다 생성됩니다.

![복셀 볼륨에서 생성된 생성된 메시](images/su-custommesh.jpg)<br>
*복셀 볼륨에서 생성된 메시 생성*

## <a name="troubleshooting"></a>문제 해결

* [SpatialPerception](#setting-the-spatialperception-capability) 기능을 설정해야 합니다.
* 추적이 손실되면 다음 OnSurfaceChanged 이벤트가 모든 메시를 제거합니다.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Mixed Reality Toolkit 공간 매핑

Mixed Reality Toolkit 공간 매핑 사용에 대한 자세한 내용은 MRTK 문서의 [공간 인식 섹션을](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) 참조하세요.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unity 개발 여정을 수행하는 경우 MRTK 핵심 구성 요소 탐색을 진행하는 중입니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목

* [좌표계](../../design/coordinate-systems.md)
* [Unity의 좌표계](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>
