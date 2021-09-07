---
title: 장면 이해 SDK
description: 혼합 현실 앱에서 구성 요소, 메시 및 개체를 포함하여 Scene Understanding SDK를 설치하고 사용하는 방법을 알아봅니다.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: 장면 이해, 공간 매핑, Windows Mixed Reality, Unity
ms.openlocfilehash: d7547e1517583e3822a9ac9b54cbf0557cd7780c
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123246320"
---
# <a name="scene-understanding-sdk-overview"></a>장면 이해 SDK 개요

장면 이해는 Mixed Reality 디바이스가 캡처하는 비정형 환경 센서 데이터를 변환하고 강력한 추상 표현으로 변환합니다. SDK는 애플리케이션과 Scene Understanding 런타임 간의 통신 계층 역할을 합니다. 3D 표현을 위한 3D 장면 그래프, 2D 애플리케이션용 2D 사각형 및 패널과 같은 기존 표준 구문을 모방하는 것을 목표로 합니다. Scene Understanding이 모방하는 구문은 구체적인 프레임워크에 매핑되지만, 일반적으로 SceneUnderability는 프레임워크와 상호 작용하는 다양한 프레임워크 간의 상호 운용성을 허용하는 프레임워크에 구애받지 않습니다. Scene Understanding이 발전함에 따라 SDK의 역할은 통합 프레임워크 내에서 새로운 표현과 기능이 계속 노출되도록 하는 것입니다. 이 문서에서는 먼저 개발 환경/사용에 익숙해지는 데 도움이 되는 개략적인 개념을 소개한 다음, 특정 클래스 및 구문에 대한 자세한 설명서를 제공합니다.

## <a name="where-do-i-get-the-sdk"></a>SDK는 어디서 얻을 수 있나요?

SceneUnderund SDK는 [Mixed Reality 기능 도구를](../unity/welcome-to-mr-feature-tool.md)통해 다운로드할 수 있습니다.
<!--Unity Note-->
**참고:** 최신 릴리스는 미리 보기 패키지에 따라 달라지며, 이를 보려면 릴리스 전 패키지를 사용하도록 설정해야 합니다.

버전 0.5.2022-rc 이상의 경우 Scene Understanding은 애플리케이션이 Win32 또는 UWP 플랫폼용 애플리케이션을 개발할 수 있도록 C# 및 C++에 대한 언어 프로젝션을 지원합니다. 이 버전에서 SceneUnderstanding은 HoloLens2와 통신하는 데만 사용되는 SceneObserver를 제외하는 Unity 편집기 내 지원을 지원합니다. 
<!-- Unity Note: Since C++ is mentioned, it's not strictly Unity. Not sure about the C#. -->
SceneUnderund에는 Windows SDK 버전 18362 이상이 필요합니다. 

## <a name="conceptual-overview"></a>개념적 개요

### <a name="the-scene"></a>장면

혼합 현실 디바이스는 사용자 환경에 표시되는 내용에 대한 정보를 지속적으로 통합하고 있습니다. Scene Understanding은 이러한 모든 데이터 원본을 깔때기하고 하나의 응집력 있는 추상화 하나를 생성합니다. Scene Understanding은 단일 사물의 인스턴스(예: 벽/최면/바닥)를 나타내는 [SceneObjects의](scene-understanding-SDK.md#sceneobjects) 컴퍼지션인 Scenes를 생성합니다. 장면 개체 자체는 이 SceneObject를 구성하는 보다 세부적인 부분을 나타내는 [SceneComponents]의 컴퍼지션입니다. 구성 요소의 예로는 쿼드와 메시가 있지만 나중에 경계 상자, 충돌 메시, 메타데이터 등을 나타낼 수 있습니다.

원시 센서 데이터를 장면으로 변환하는 프로세스는 보통 공간(~10x10m)의 경우 몇 초에서 큰 공간(~50x50m)의 경우 몇 분 정도 걸릴 수 있는 비용이 많이 드는 작업이므로 애플리케이션 요청 없이 디바이스에서 계산되는 작업이 아닙니다. 대신, 장면 생성은 주문형 애플리케이션에 의해 트리거됩니다. SceneObserver 클래스에는 장면을 컴퓨팅 또는 역직렬화할 수 있는 정적 메서드가 있으며, 이 메서드를 열거/상호 작용할 수 있습니다. "Compute" 작업은 주문형으로 실행되고 CPU에서 실행되지만 별도의 프로세스(Mixed Reality 드라이버)에서 실행됩니다. 그러나 다른 프로세스에서 컴퓨팅을 수행하는 동안 결과 장면 데이터는 Scene 개체의 애플리케이션에 저장되고 유지 관리됩니다. 

다음은 이 프로세스 흐름을 보여 주는 다이어그램이며 Scene Understanding 런타임과 상호 작용한 두 애플리케이션의 예를 보여 줍니다. 

![프로세스 다이어그램](images/SU-ProcessFlow.png)

왼쪽에는 항상 자체 프로세스에서 실행되고 있는 혼합 현실 런타임의 다이어그램이 있습니다. 이 런타임은 디바이스 추적, 공간 매핑 및 Scene Understanding이 주변 세계를 이해하고 추론하는 데 사용하는 기타 작업을 수행합니다. 다이어그램의 오른쪽에는 Scene Understanding을 사용하는 두 개의 이론적 애플리케이션이 표시됩니다. MRTK를 사용 하는 첫 번째 애플리케이션 인터페이스<!--Unity Note-->- Scene Understanding SDK를 내부적으로 사용하는 두 번째 앱은 두 개의 개별 장면 인스턴스를 계산하고 사용합니다. 이 다이어그램의 세 장면 모두 장면의 고유한 인스턴스를 생성합니다. 드라이버는 애플리케이션과 장면 개체 간에 공유되는 글로벌 상태를 추적하지 않습니다. 한 장면에서 다른 장면에서는 찾을 수 없습니다. Scene Understanding은 시간에 따라 추적하는 메커니즘을 제공하지만 SDK를 사용하여 수행됩니다. 추적 코드가 앱 프로세스의 SDK에서 이미 실행되고 있습니다.

각 장면 애플리케이션의 메모리 공간에 해당 데이터를 저장하기 때문에 장면 개체 또는 내부 데이터의 모든 함수가 항상 애플리케이션의 프로세스에서 실행된다고 가정할 수 있습니다.

### <a name="layout"></a>Layout

Scene Understanding을 작업하려면 런타임이 구성 요소를 논리적 및 물리적으로 어떻게 나타내는지 알고 이해하는 것이 중요할 수 있습니다. 장면 은 주요 수정이 필요 없이 향후 요구 사항을 충족할 수 있는 기본 구조를 유지하면서 단순하도록 선택된 특정 레이아웃의 데이터를 나타냅니다. 장면에서는 모든 구성 요소(모든 장면 개체에 대한 구성 요소)를 플랫 목록에 저장하고 특정 구성 요소가 다른 구성 요소를 참조하는 참조를 통해 계층 구조 및 컴퍼지션을 정의하여 이 작업을 수행합니다.

아래에서는 구조체의 예를 평면 및 논리 형식으로 제시합니다.

<table>
<tr><th>논리 레이아웃</th><th>물리적 레이아웃</th></tr>
<tr>
<td>
<ul>
  장면
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

이 그림에서는 장면의 물리적 레이아웃과 논리적 레이아웃 간의 차이점을 강조 표시합니다. 왼쪽에는 장면을 열거할 때 애플리케이션에서 볼 수 있는 데이터의 계층적 레이아웃이 표시됩니다. 오른쪽에서는 필요한 경우 개별적으로 액세스할 수 있는 12개의 개별 구성 요소로 구성된 장면을 볼 수 있습니다. 새 장면을 처리할 때 애플리케이션이 이 계층 구조를 논리적으로 안내할 것으로 예상합니다. 그러나 장면 업데이트 간에 추적할 때 일부 애플리케이션은 두 장면 간에 공유되는 특정 구성 요소를 대상으로 지정하는 데만 관심이 있을 수 있습니다.

## <a name="api-overview"></a>API 개요

다음 섹션에서는 Scene Understanding의 구문에 대한 개략적인 개요를 제공합니다. 이 섹션을 읽으면 장면을 나타내는 방법과 다양한 구성 요소의 용도를 이해할 수 있습니다. 다음 섹션에서는 구체적인 코드 예제와 이 개요에 설명된 추가 세부 정보를 제공합니다.

아래에 설명된 모든 형식은 `Microsoft.MixedReality.SceneUnderstanding` 네임스페이스에 있습니다.

### <a name="scenecomponents"></a>SceneComponents

장면의 논리적 레이아웃을 이해했으므로 SceneComponents의 개념과 이를 사용하여 계층 구조를 구성하는 방법을 제시할 수 있습니다. SceneComponents는 메시, 쿼드 또는 경계 상자와 같은 단일 코어를 나타내는 SceneUnderstanding에서 가장 세분화된 분해입니다. SceneComponents는 독립적으로 업데이트할 수 있고 다른 SceneComponents에서 참조할 수 있는 요소이므로 이러한 유형의 추적/참조 메커니즘을 허용하는 단일 전역 속성인 고유 ID가 있습니다. ID는 장면 계층 구조의 논리적 컴퍼지션과 개체 지속성(한 장면을 다른 장면에 상대적으로 업데이트하는 동작)에 사용됩니다.

새로 계산된 모든 장면을 고유한 장면으로 취급하고 그 안에 있는 모든 데이터를 열거하는 경우, 대부분 해당 장면에 대해 투명하게 표시됩니다. 그러나 여러 업데이트에 대한 구성 요소를 추적하려는 경우, 이D를 사용하여 Scene 개체 간의 SceneComponents를 인덱싱하고 찾습니다.

### <a name="sceneobjects"></a>SceneObjects

SceneObject는 "사물"(예: 벽, 바닥, 상한 등)의 인스턴스를 나타내는 SceneComponent입니다. 해당 Kind 속성으로 표현됩니다. SceneObject는 기하학적이므로 공간의 해당 위치를 나타내는 함수와 속성을 갖습니다. 그러나 기하학적 또는 논리적 구조는 포함하지 않습니다. 대신 SceneObjects는 시스템에서 지원하는 다양한 표현을 제공하는 다른 SceneComponents, 특히 SceneQuads 및 SceneMeshes를 참조합니다. 새 장면을 계산할 때 애플리케이션은 장면의 SceneObjects를 열거하여 관심 있는 것을 처리할 가능성이 높습니다.

SceneObjects는 다음 중 하나를 가질 수 있습니다.

<table>
<tr>
<th>SceneObjectKind</th> <th>설명</th>
</tr>
<tr><td>배경</td><td>SceneObject는 인식되는 다른 종류의 장면 개체 중 하나가 <b>아닌</b> 것으로 알려져 있습니다. 이 클래스는 배경이 벽/바닥/상한 등이 아닌 것으로 알려진 알 수 없음과 혼동해서는 안 됩니다. 알 수 없음은 아직 분류되지 않았습니다.</b></td></tr>
<tr><td>벽</td><td>실제 벽입니다. 벽은 이동 불가능한 환경 구조로 간주합니다.</td></tr>
<tr><td>Floor</td><td>바닥은 볼 수 있는 모든 표면입니다. 참고: 스트루는 바닥이 아닙니다. 또한 바닥은 볼 수 있는 표면을 가정하므로 단수 층을 명시적으로 가정하지 않습니다. 다중 수준 구조체, 램프 등... 는 모두 층으로 분류되어야 합니다.</td></tr>
<tr><td>Ceiling</td><td>방의 위쪽 표면입니다.</td></tr>
<tr><td>플랫폼</td><td>홀로그램을 배치할 수 있는 큰 평면 표면입니다. 테이블, 카운터톱 및 기타 큰 가로 표면을 나타내는 경향이 있습니다.</td></tr>
<tr><td>World</td><td>레이블 지정에 구애받지 않는 기하학적 데이터에 대한 예약된 레이블입니다. EnableWorldMesh 업데이트 플래그를 설정하여 생성된 메시는 세계로 분류됩니다.</td></tr>
<tr><td>Unknown</td><td>이 장면 개체는 아직 분류되어 할당되지 않았습니다. 이 개체는 무엇이든 될 수 있기 때문에 Background와 혼동해서는 안 됩니다. 시스템은 아직 충분히 강력한 분류를 제공하지 않았습니다.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

SceneMesh는 삼각형 목록을 사용하여 임의의 기하학적 개체의 기하 도형을 대략적인 것으로 만드는 SceneComponent입니다. SceneMeshes는 여러 다른 컨텍스트에서 사용됩니다. watertight 셀 구조의 구성 요소를 나타내거나 장면과 연결된 무제한 공간 매핑 메시를 나타내는 WorldMesh로 나타낼 수 있습니다. 각 메시와 함께 제공되는 인덱스 및 꼭짓점 데이터는 모든 최신 렌더링 API에서 삼각형 메시를 렌더링하는 데 사용되는 [꼭짓점 및 인덱스 버퍼와](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) 동일한 친숙한 레이아웃을 사용합니다. Scene Understanding에서 메시는 32비트 인덱스를 사용하며 특정 렌더링 엔진의 청크로 나누어야 할 수 있습니다.

#### <a name="winding-order-and-coordinate-systems"></a>권선 순서 및 좌표계

Scene Understanding에서 생성된 모든 메시는 시계 방향의 구불구불한 순서를 사용하여 Right-Handed 좌표계에서 메시를 반환해야 합니다. 

참고: .191105 이전의 OS 빌드에는 "World" 메시가 Counter-Clockwise 권선 순서로 반환되는 알려진 버그가 있을 수 있으며 이후에 수정되었습니다.

### <a name="scenequad"></a>SceneQuad

SceneQuad는 3D 세계를 차지하는 2d 표면을 나타내는 SceneComponent입니다. SceneQuads는 ARKit ARPlaneAnchor 또는 ARCore 평면과 유사하게 사용할 수 있지만 플랫 앱 또는 보강된 UX에서 사용할 수 있는 2d 캔버스로 더 높은 수준의 기능을 제공합니다. 2D 특정 API는 배치 및 레이아웃을 쉽게 사용할 수 있도록 하는 쿼드용으로 제공되며, 쿼드를 사용한 개발(렌더링 제외)은 3D 메시보다 2d 캔버스를 사용하는 것과 더 비슷합니다.

#### <a name="scenequad-shape"></a>SceneQuad 셰이프

SceneQuads는 경계가 있는 사각형 표면을 2d로 정의합니다. 그러나 SceneQuads는 임의적이고 잠재적으로 복잡한 도넛형 테이블(예: 도넛형 테이블)으로 표면을 나타냅니다. 쿼드 표면의 복잡한 모양을 나타내려면 GetSurfaceMask API를 사용하여 제공하는 이미지 버퍼에 표면의 모양을 렌더링할 수 있습니다. 쿼드가 있는 SceneObject에도 메시가 있는 경우 메시 삼각형은 이 렌더링된 이미지와 동일해야 하며, 둘 다 2d 또는 3d 좌표로 표면의 실제 기하 도형을 나타냅니다.

## <a name="scene-understanding-sdk-details-and-reference"></a>장면 이해 SDK 세부 정보 및 참조

> [!NOTE] 
> <!--Unity Note-->MRTK를 사용하는 경우 MRTK와 상호 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 작용하므로 대부분의 상황에서 이 섹션을 건너뛸 수 있습니다. 자세한 내용은 [MRTK 장면 이해 문서를](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) 참조하세요.

다음 섹션에서는 SceneUnderstanding의 기본 사항들을 익시키는 데 도움이 됩니다. 이 섹션에서는 기본을 제공해야 합니다. 이 시점에서 샘플 애플리케이션을 탐색하여 SceneUnderstanding이 전체적으로 사용되는 방식을 확인할 수 있는 충분한 컨텍스트가 있어야 합니다.

### <a name="initialization"></a>초기화

SceneUnderund를 사용하여 작업하는 첫 번째 단계는 애플리케이션이 Scene 개체에 대한 참조를 얻는 것입니다. 이 작업은 두 가지 방법 중 하나로 수행할 수 있습니다. 드라이버는 장면을 계산하거나 과거에 계산된 기존 장면을 직렬화 해제할 수 있습니다. 후자는 혼합 현실 디바이스 없이 애플리케이션 및 환경을 신속하게 프로토타입화할 수 있는 개발 중에 SceneUnderstanding으로 작업하는 데 유용합니다.

SceneObserver를 사용하여 장면을 계산합니다. 장면을 만들기 전에 애플리케이션은 디바이스를 쿼리하여 SceneUnderstanding을 지원하는지 확인하고 SceneUnderund에 필요한 정보에 대한 사용자 액세스를 요청해야 합니다.
<!--Unity Note-->
```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

RequestAccessAsync()가 호출되지 않으면 새 장면을 계산하지 못합니다. 다음으로, Mixed Reality 헤드셋을 중심으로 10미터 반경이 있는 새 장면을 컴퓨팅합니다.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>데이터에서 초기화(라고도 함) PC 경로)

직접 사용을 위해 장면을 계산할 수 있지만 나중에 사용할 수 있도록 직렬화된 형태로 계산할 수도 있습니다. 개발자가 디바이스 없이 Scene Understanding에서 작업하고 테스트할 수 있기 때문에 개발에 유용한 것으로 입증되었습니다. 장면을 직렬화하는 동작은 장면을 계산하는 것과 거의 동일하며, 데이터는 SDK에 의해 로컬로 deserialized되는 대신 애플리케이션에 반환됩니다. 그런 다음, 직접 deserialize하거나 나중에 사용하기 위해 저장할 수 있습니다.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a>SceneObject 열거형

이제 애플리케이션에 장면이 생겼으므로 애플리케이션은 SceneObjects를 보고 상호 작용합니다. 이 작업은 **SceneObjects** 속성에 액세스하여 수행됩니다.

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a>구성 요소 업데이트 및 구성 요소 구체화

***장면에 FindComponent*** 라는 구성 요소를 검색하는 또 다른 함수가 있습니다. 이 함수는 추적 개체를 업데이트하고 이후 장면에서 찾을 때 유용합니다. 다음 코드는 이전 장면을 기준으로 새 장면을 계산한 다음 새 장면에서 층을 찾습니다.

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>장면 개체에서 메시 및 쿼드 액세스

SceneObjects가 발견되면 애플리케이션은 구성되는 쿼드/메시에 포함된 데이터에 액세스하려고 할 가능성이 높습니다. 이 데이터는 ***쿼드** _ 및 _ *_메시_** 속성을 통해 액세스됩니다. 다음 코드는 floor 개체의 모든 쿼드와 메시를 열거합니다.

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

장면 원점과 상대적인 변환이 있는 SceneObject입니다. 이는 SceneObject가 "사물"의 인스턴스를 나타내고 공간에서 찾기 가능하고, 쿼드 및 메시가 부모를 기준으로 변환되는 기하 도형을 나타내기 때문입니다. 별도의 SceneObjects가 동일한 SceneMesh/SceneQuad SceneComponents를 참조할 수 있으며 SceneObject에 SceneMesh/SceneQuad가 두 개 이상 있는 것일 수도 있습니다.

### <a name="dealing-with-transforms"></a>변환 처리

Scene Understanding은 변환을 처리할 때 기존 3D 장면 표현에 맞게 의도적으로 시도했습니다. 따라서 각 장면 은 가장 일반적인 3D 환경 표현과 매우 유사하게 단일 좌표계로 제한됩니다. SceneObjects는 각각 해당 좌표계를 기준으로 해당 위치를 제공합니다. 애플리케이션이 단일 원점이 제공하는 한계를 확대하는 장면을 처리하는 경우 SceneObjects를 SpatialAnchors에 고정하거나 여러 장면을 생성하고 함께 병합할 수 있지만 간단히 하기 위해 Watertight 장면은 Scene.OriginSpatialGraphNodeId에 정의된 하나의 NodeId로 지역화된 자체 원점 안에 있다고 가정합니다.
<!--Unity Note-->
예를 들어 다음 Unity 코드는 Windows Perception 및 Unity API를 사용하여 좌표계를 맞추는 방법을 보여 있습니다. Windows Perception API에 대한 자세한 내용은 [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 및 [SpatialGraphInteropPreview를](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) 참조하고 Unity의 세계 원본에 해당하는 SpatialCoordinateSystem을 가져오는 방법을 보려면 [Unity에서 네이티브 개체를 Mixed Reality.](/windows/mixed-reality/unity-xrdevice-advanced)

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

각 `SceneObject` 에는 해당 개체에 적용되는 변환이 있습니다. Unity에서는 다음과 같이 오른쪽 좌표로 변환하고 로컬 변환을 할당합니다.

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a>쿼드

쿼드는 2D 배치 시나리오를 지원하도록 설계되었으며 2D 캔버스 UX 요소에 대한 확장으로 간주해야 합니다. 쿼드는 SceneObjects의 구성 요소이며 3D로 렌더링할 수 있지만 Quad API 자체는 쿼드가 2D 구조라고 가정합니다. 익스텐트, 셰이프 등의 정보를 제공하고 배치를 위한 API를 제공합니다.

쿼드에는 사각형 익스텐트가 있지만 임의로 모양의 2D 표면을 나타냅니다. 3D 환경 쿼드와 상호 작용하는 이러한 2D 화면에 배치할 수 있도록 하려면 이러한 상호 작용을 가능하게 하는 유틸리티를 제공합니다. 현재 Scene Understanding은 **FindCentermostPlacement** 및 **GetSurfaceMask의** 두 가지 함수를 제공합니다. FindCentermostPlacement는 쿼드에서 개체를 배치할 수 있는 위치를 찾고 제공된 경계 상자가 기본 화면에 유지되도록 하는 개체에 가장 적합한 위치를 찾으려고 시도하는 상위 수준 API입니다.

> [!NOTE]
> 출력의 좌표는 다른 창 사각형 형식과 마찬가지로 왼쪽 위 모퉁이가 (x = 0, y = 0)인 "쿼드 공간"의 쿼드를 기준으로 합니다. 사용자 고유의 개체의 원본으로 작업할 때 이를 고려해야 합니다. 

다음 예제에서는 가운데에서 가장 배치 가능한 위치를 찾아서 홀로그램을 쿼드에 고정하는 방법을 보여줍니다.

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

1-4단계는 특정 프레임워크/구현에 따라 크게 달라지지만 테마는 유사해야 합니다. 쿼드는 단순히 공간에서 지역화된 제한된 2D 평면을 나타낸다는 점에 유의해야 합니다. 엔진/프레임워크가 쿼드의 위치를 파악하고 쿼드를 기준으로 개체를 루팅하면 실제 세계와 관련하여 홀로그램이 올바르게 배치됩니다. 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>메시

메시는 개체 또는 환경의 기하학적 표현을 나타냅니다. 공간 [매핑과](../../design/spatial-mapping.md)마찬가지로, 각 공간 표면 메시와 함께 제공되는 메시 인덱스 및 꼭짓점 데이터는 모든 최신 렌더링 API에서 삼각형 메시를 렌더링하는 데 사용되는 꼭짓점 및 인덱스 버퍼와 동일한 친숙한 레이아웃을 사용합니다. 꼭짓점 위치는 의 좌표계에 `Scene` 제공됩니다. 이 데이터를 참조하는 데 사용되는 특정 API는 다음과 같습니다.

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

다음 코드는 메시 구조에서 삼각형 목록을 생성하는 예제를 제공합니다.

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

인덱스/꼭짓점 버퍼는 인덱스/꼭짓점 수 = >이어야 하지만, 그렇지 않으면 임의 크기로 크기를 정하여 효율적인 메모리 재사용을 허용할 수 있습니다.

### <a name="collidermesh"></a>ColliderMesh

장면 개체는 Meshes 및 ColliderMeshes 속성을 통해 메시 및 충돌체 메시 데이터에 대한 액세스를 제공합니다. 이러한 메시는 항상 일치하므로 Meshes 속성의 i번째 인덱스는 ColliderMeshes 속성의 i번째 인덱스와 동일한 기하 도형을 나타냅니다. 런타임/개체가 충돌체 메시를 지원하는 경우 가장 낮은 다각형, 가장 높은 순서 근사값을 보장하며, 애플리케이션에서 충돌체를 사용할 때마다 ColliderMeshes를 사용하는 것이 좋습니다. 시스템에서 충돌체를 지원하지 않는 경우 ColliderMeshes에서 반환된 Mesh 개체는 메모리 제약 조건을 줄이는 메시와 동일한 개체가 됩니다.

## <a name="developing-with-scene-understanding"></a>장면 이해를 통해 개발

이 시점에서 런타임 및 SDK를 이해하는 장면의 핵심 구성 요소에 대해 이해해야 합니다. 대부분의 기능과 복잡성은 액세스 패턴, 3D 프레임워크와의 상호 작용 및 공간 계획, 공간 분석, 탐색, 물리학 등과 같은 고급 작업을 수행하도록 이러한 API를 기반으로 작성할 수 있는 도구에 있습니다. 시나리오를 돋우도록 적절한 방향으로 안내해야 하는 샘플에서 이러한 내용을 캡처하기를 바랍니다. 다루지 않는 샘플 또는 시나리오가 있는 경우 알려주세요. 필요한 내용을 문서화/프로토타입으로 작성해 보겠습니다.

### <a name="where-can-i-get-sample-code"></a>샘플 코드는 어디서 얻을 수 있나요?
<!--Unity Note-->
Unity용 Scene Understanding 샘플 코드는 [Unity 샘플 페이지](https://github.com/sceneunderstanding-microsoft/unitysample) 페이지에서 찾을 수 있습니다. 이 응용 프로그램을 사용 하면 장치와 통신 하 여 다양 한 장면 개체를 렌더링 하거나, PC에서 serialize 된 장면을 로드 하 고, 장치 없이 장면 이해를 경험할 수 있습니다.

### <a name="where-can-i-get-sample-scenes"></a>샘플 장면을 어디에서 얻을 수 있나요?

HoloLens2가 있는 경우 ComputeSerializedAsync의 출력을 파일에 저장 하 고 사용자의 편의를 위해이를 deserialize 하 여 캡처한 장면을 저장할 수 있습니다. 

HoloLens2 장치가 없지만 장면 이해를 재생 하려는 경우에는 미리 캡처된 장면을 다운로드 해야 합니다. 장면 이해 샘플은 현재 사용자의 편의를 위해 다운로드 하 여 사용할 수 있는 직렬화 된 장면과 함께 제공 됩니다. 여기에서 찾을 수 있습니다.

[장면 이해 샘플 장면](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a>참고 항목

* [공간 매핑](../../design/spatial-mapping.md)
* [장면 이해](../../design/scene-understanding.md)
* [Unity 샘플](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)