---
title: 장면 이해 SDK
description: 혼합 현실 앱에서 구성 요소, 메시 및 개체를 포함하여 Scene Understanding SDK를 설치하고 사용하는 방법을 알아봅니다.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: 장면 이해, 공간 매핑, Windows Mixed Reality, Unity
ms.openlocfilehash: 1b93f3137e1ac1309ee56e974a0fa33608114f16dfb65a13e369490f45d6beb3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193644"
---
# <a name="scene-understanding-sdk-overview"></a>장면 이해 SDK 개요

장면 이해는 Mixed Reality 디바이스가 캡처하는 비정형 환경 센서 데이터를 변환하고 강력한 추상 표현으로 변환합니다. SDK는 애플리케이션과 Scene Understanding 런타임 간의 통신 계층 역할을 합니다. 3D 표현을 위한 3D 장면 그래프, 2D 애플리케이션에 대한 2D 사각형 및 패널과 같은 기존 표준 구문을 모방하는 것을 목표로 합니다. Scene Understanding이 모방하는 구문은 구체적인 프레임워크에 매핑되지만, 일반적으로 SceneUnderability는 프레임워크와 상호 작용하는 다양한 프레임워크 간의 상호 운용성을 허용하는 프레임워크에 구애받지 않습니다. Scene Understanding이 발전함에 따라 SDK의 역할은 통합 프레임워크 내에서 새로운 표현과 기능이 계속 노출되도록 하는 것입니다. 이 문서에서는 먼저 개발 환경/사용량을 익힌 다음, 특정 클래스 및 구문에 대한 보다 자세한 설명서를 제공하는 데 도움이 되는 개략적인 개념을 소개합니다.

## <a name="where-do-i-get-the-sdk"></a>SDK는 어디서 얻을 수 있나요?

SceneUnderund SDK는 [Mixed Reality 기능 도구를](../unity/welcome-to-mr-feature-tool.md)통해 다운로드할 수 있습니다.

**참고:** 최신 릴리스는 미리 보기 패키지에 따라 달라지며, 이를 보려면 릴리스 전 패키지를 사용하도록 설정해야 합니다.

버전 0.5.2022-rc 이상의 경우 Scene Understanding은 애플리케이션이 Win32 또는 UWP 플랫폼용 애플리케이션을 개발할 수 있도록 C# 및 C++에 대한 언어 프로젝션을 지원합니다. 이 버전에서 SceneUnderstanding은 HoloLens2와 통신하는 데만 사용되는 SceneObserver를 제외하는 Unity 편집기 내 지원을 지원합니다. 

SceneUnderund에는 Windows SDK 버전 18362 이상이 필요합니다. 

## <a name="conceptual-overview"></a>개념적 개요

### <a name="the-scene"></a>장면

혼합 현실 디바이스는 사용자 환경에 표시되는 내용에 대한 정보를 지속적으로 통합하고 있습니다. Scene Understanding은 이러한 모든 데이터 원본을 유입하고 하나의 응집력 있는 추상화 하나를 생성합니다. Scene Understanding은 단일 사물의 인스턴스(예: 벽/최면/바닥)를 나타내는 [SceneObjects의](scene-understanding-SDK.md#sceneobjects) 컴퍼지션인 Scenes를 생성합니다. 장면 개체 자체는 이 SceneObject를 구성하는 보다 세분화된 부분을 나타내는 [SceneComponents]의 컴퍼지션입니다. 구성 요소의 예로는 쿼드와 메시가 있지만 나중에 경계 상자, 충돌 메시, 메타데이터 등을 나타낼 수 있습니다.

원시 센서 데이터를 장면으로 변환하는 프로세스는 중간 공간(~10x10m)의 경우 몇 초에서 큰 공간의 경우 분(~50x50m)으로 소요될 수 있는 비용이 많이 드는 작업이므로 애플리케이션 요청 없이 디바이스에서 계산되는 작업이 아닙니다. 대신, 장면 생성은 주문형 애플리케이션에 의해 트리거됩니다. SceneObserver 클래스에는 장면을 컴퓨팅 또는 역직렬화할 수 있는 정적 메서드가 있으며, 이 메서드를 열거/상호 작용할 수 있습니다. "Compute" 작업은 주문형으로 실행되며 CPU에서 실행되지만 별도의 프로세스(Mixed Reality 드라이버)에서 실행됩니다. 그러나 다른 프로세스에서 컴퓨팅을 수행하는 동안 결과 장면 데이터는 Scene 개체의 애플리케이션에 저장되고 유지 관리됩니다. 

다음은 이 프로세스 흐름을 보여 주는 다이어그램이며 Scene Understanding 런타임과 상호 작용한 두 애플리케이션의 예를 보여 줍니다. 

![프로세스 다이어그램](images/SU-ProcessFlow.png)

왼쪽에는 항상 자체 프로세스에서 실행되고 있는 혼합 현실 런타임의 다이어그램이 있습니다. 이 런타임은 디바이스 추적, 공간 매핑 및 Scene Understanding이 주변 세계를 이해하고 추론하는 데 사용하는 기타 작업을 수행합니다. 다이어그램의 오른쪽에는 Scene Understanding을 사용하는 두 가지 이론적 애플리케이션이 표시됩니다. 첫 번째 애플리케이션은 내부적으로 Scene Understanding SDK를 사용하는 MRTK와 인터페이스하고, 두 번째 앱은 두 개의 개별 장면 인스턴스를 계산하고 사용합니다. 이 다이어그램의 세 장면 모두 장면의 고유한 인스턴스를 생성합니다. 드라이버는 애플리케이션과 장면 개체 간에 공유되는 글로벌 상태를 추적하지 않습니다. 한 장면에서 다른 장면에서는 찾을 수 없습니다. Scene Understanding은 시간에 따라 추적하는 메커니즘을 제공하지만 SDK를 사용하여 수행됩니다. 추적 코드가 앱 프로세스의 SDK에서 이미 실행되고 있습니다.

각 장면 애플리케이션의 메모리 공간에 데이터를 저장하기 때문에 장면 개체 또는 내부 데이터의 모든 기능이 항상 애플리케이션의 프로세스에서 실행된다고 가정할 수 있습니다.

### <a name="layout"></a>Layout

Scene Understanding을 작업하려면 런타임이 구성 요소를 논리적 및 물리적으로 어떻게 나타내는지 알고 이해하는 것이 중요할 수 있습니다. 장면 은 주요 수정이 필요 없이 향후 요구 사항을 충족할 수 있는 기본 구조를 유지하면서 단순하도록 선택된 특정 레이아웃의 데이터를 나타냅니다. 장면에서는 모든 구성 요소(모든 장면 개체의 구성 요소)를 플랫 목록에 저장하고 특정 구성 요소가 다른 구성 요소를 참조하는 참조를 통해 계층 및 컴퍼지션을 정의하여 이 작업을 수행합니다.

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

다음 섹션에서는 Scene Understanding의 구문에 대한 개략적인 개요를 제공합니다. 이 섹션을 읽으면 장면을 표시하는 방법 및 다양한 구성 요소의 용도를 이해할 수 있습니다. 다음 섹션에서는 구체적인 코드 예제와 이 개요에 설명된 추가 세부 정보를 제공합니다.

아래에 설명된 모든 형식은 `Microsoft.MixedReality.SceneUnderstanding` 네임스페이스에 있습니다.

### <a name="scenecomponents"></a>SceneComponents

장면의 논리적 레이아웃을 이해했으므로 이제 SceneComponents의 개념과 이를 사용하여 계층 구조를 구성하는 방법을 제시할 수 있습니다. SceneComponents는 메시, 쿼드 또는 경계 상자와 같은 단일 코어를 나타내는 SceneUnderstanding에서 가장 세분화된 분해입니다. SceneComponents는 독립적으로 업데이트할 수 있고 다른 SceneComponents에서 참조할 수 있는 요소이므로 이러한 유형의 추적/참조 메커니즘을 허용하는 단일 전역 속성에 고유한 ID가 있습니다. ID는 장면 계층 구조의 논리적 컴퍼지션과 개체 지속성(한 장면을 다른 장면에 상대적으로 업데이트하는 동작)에 사용됩니다. 

새로 계산된 모든 장면을 고유한 것으로 취급하고 그 안에 있는 모든 데이터를 열거하는 경우 ID는 대부분 투명합니다. 그러나 여러 업데이트를 통해 구성 요소를 추적하려는 경우 ID를 사용하여 Scene 개체 간의 SceneComponents를 인덱싱하고 찾습니다.

### <a name="sceneobjects"></a>SceneObjects

SceneObject는 "사물"(예: 벽, 바닥, 상한 등)의 인스턴스를 나타내는 SceneComponent입니다. 해당 Kind 속성으로 표현됩니다. SceneObjects는 기하학적이므로 공간의 위치를 나타내는 함수와 속성을 갖습니다. 그러나 기하학적 또는 논리적 구조는 포함하지 않습니다. 대신 SceneObjects는 시스템에서 지원하는 다양한 표현을 제공하는 다른 SceneComponents, 특히 SceneQuads 및 SceneMeshes를 참조합니다. 새 장면을 계산할 때 애플리케이션은 장면의 SceneObjects를 열거하여 관심 있는 것을 처리할 가능성이 큽니다.

SceneObjects는 다음 중 하나를 가질 수 있습니다.

<table>
<tr>
<th>SceneObjectKind</th> <th>Description</th>
</tr>
<tr><td>배경</td><td>SceneObject는 인식되는 다른 종류의 장면 개체 중 하나가 <b>아닌</b> 것으로 알려져 있습니다. 이 클래스는 배경이 벽/바닥/상한 등이 아닌 것으로 알려진 알 수 없음과 혼동해서는 안 됩니다. 알 수 없음은 아직 분류되지 않았습니다.</b></td></tr>
<tr><td>벽</td><td>실제 벽입니다. 벽은 이동 불가능한 환경 구조로 간주합니다.</td></tr>
<tr><td>Floor</td><td>바닥은 사람이 볼 수 있는 모든 표면입니다. 참고: 스트루는 바닥이 아닙니다. 또한 바닥은 볼 수 있는 표면을 가정하므로 단수 층을 명시적으로 가정하지 않습니다. 다중 수준 구조체, 램프 등... 는 모두 층으로 분류되어야 합니다.</td></tr>
<tr><td>Ceiling</td><td>방의 위쪽 표면입니다.</td></tr>
<tr><td>플랫폼</td><td>Holograms를 놓을 수 있는 커다란 플랫 표면입니다. 이는 테이블, countertops 및 기타 넓은 가로 표면을 나타내는 경향이 있습니다.</td></tr>
<tr><td>World</td><td>레이블 지정과 무관 한 기하학적 데이터의 예약 된 레이블입니다. EnableWorldMesh 업데이트 플래그를 설정 하 여 생성 된 메시는 세계로 분류 됩니다.</td></tr>
<tr><td>Unknown</td><td>이 장면 개체는 아직 분류 되어 있으며 종류를 할당 해야 합니다. 이 개체는 아무것도 될 수 있으므로 배경과 혼동 해서는 안 됩니다. 시스템은 아직 충분히 강력한 분류로 제공 되지 않습니다.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

SceneMesh은 삼각형 목록을 사용 하 여 임의 기하학적 개체의 기 하 도형에 근사치를 주는 SceneComponent입니다. SceneMeshes는 여러 다른 컨텍스트에서 사용 되며, watertight 셀 구조의 구성 요소를 나타내거나 장면에 연결 된 바인딩되지 않은 공간 매핑 메시를 나타내는 WorldMesh로 나타낼 수 있습니다. 각 메시와 함께 제공 되는 인덱스 및 꼭 짓 점 데이터는 모든 최신 렌더링 Api에서 삼각형 메시를 렌더링 하는 데 사용 되는 [꼭 짓 점 및 인덱스 버퍼](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) 와 동일한 익숙한 레이아웃을 사용 합니다. 장면 이해에서 메시는 32 비트 인덱스를 사용 하며 특정 렌더링 엔진에 대 한 청크로 분할 되어야 할 수 있습니다.

#### <a name="winding-order-and-coordinate-systems"></a>권선 순서 및 좌표계

장면 이해로 생성 된 모든 메시는 시계 방향 권선 순서를 사용 하 여 Right-Handed 좌표계에서 메시를 반환할 것으로 예상 됩니다. 

참고: 191105 이전 OS 빌드에는 "세계" 메시가 이후에 수정 된 Counter-Clockwise 권선 순서로 반환 되는 알려진 버그가 있을 수 있습니다.

### <a name="scenequad"></a>SceneQuad

SceneQuad는 3d 세계를 차지 하는 2d 표면을 나타내는 SceneComponent입니다. SceneQuads는 ARKit Arkit Eanchor 또는 Arkit 평면과 유사 하 게 사용할 수 있지만, 플랫 앱 또는 확대 된 UX에서 사용할 2d canvas로 더 높은 수준의 기능을 제공 합니다. quads에 대 한 2D 특정 Api가 제공 되어 배치 및 레이아웃을 간단 하 게 사용할 수 있으며, quads를 사용 하 여 개발 (렌더링 제외)을 개발 하는 것은 3d 메시 보다 2d 캔버스 작업에 더 유사 해야 합니다.

#### <a name="scenequad-shape"></a>SceneQuad 셰이프

SceneQuads는 2d에서 경계가 지정 된 사각형 표면을 정의 합니다. 그러나 SceneQuads는 임의의 잠재적으로 복잡 한 모양 (예: 도넛형 모양의 표)을 포함 하는 표면을 나타냅니다. 쿼드 표면의 복합 셰이프를 나타내려면 GetSurfaceMask API를 사용 하 여 표면의 셰이프를 제공 된 이미지 버퍼에 렌더링할 수 있습니다. 쿼드를 포함 하는 SceneObject에도 메쉬가 있으면 망상 삼각형은 렌더링 된 이미지와 동일 해야 하며, 둘 다 2d 또는 3d 좌표에서 표면의 실제 기 하 도형을 나타냅니다.

## <a name="scene-understanding-sdk-details-and-reference"></a>SDK 세부 정보 및 참조 장면 이해

> [!NOTE] 
> MRTK를 사용 하는 경우 MRTK와 상호 작용 [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) 하므로 대부분의 경우이 섹션을 건너뛸 수 있습니다. 자세한 내용은 [Mrtk 장면 이해 문서](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) 를 참조 하세요.

다음 섹션에서는 SceneUnderstanding의 기본 사항에 대해 알아봅니다. 이 섹션에서는 SceneUnderstanding를 사용 하는 방법을 확인 하기 위해 샘플 응용 프로그램을 탐색 하는 데 충분 한 컨텍스트를 제공 해야 하는 기본 사항에 대해 설명 합니다.

### <a name="initialization"></a>초기화

SceneUnderstanding를 사용 하는 첫 번째 단계는 응용 프로그램에서 장면 개체에 대 한 참조를 얻는 것입니다. 이 작업은 두 가지 방법 중 하나로 수행할 수 있습니다. 즉, 드라이버에서 장면을 계산 하거나 과거에 계산 된 기존 장면을 deserialize 할 수 있습니다. 후자는 혼합 현실 장치 없이 응용 프로그램 및 환경을 빠르게 프로토타입화 할 수 있는 개발 중 SceneUnderstanding 작업에 유용 합니다.

SceneObserver를 사용 하 여 장면을 계산 합니다. 장면을 만들기 전에 응용 프로그램은 SceneUnderstanding를 지원 하는지 확인 하 고 SceneUnderstanding에 필요한 정보에 대 한 사용자 액세스를 요청할 수 있도록 장치를 쿼리해야 합니다.

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

RequestAccessAsync ()를 호출 하지 않으면 새 장면을 계산 하는 작업이 실패 합니다. 다음으로는 혼합 현실 헤드셋을 기반으로 하는 새 장면을 계산 하 고 10 미터 반지름이 있습니다.

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

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>데이터에서 초기화 (라고도 함) PC 경로)

직접 소비를 위해 장면을 계산할 수 있지만 나중에 사용할 수 있도록 serialize 된 형식으로 계산 될 수도 있습니다. 이는 개발자가 장치 없이 작업을 수행 하 고 장면 이해를 테스트할 수 있게 해 주는 개발에 유용한 것으로 입증 되었습니다. 장면을 직렬화 하는 작업은 응용 프로그램에 의해 로컬에서 deserialize 되는 대신 응용 프로그램에 반환 되는 것과 거의 동일 합니다. 사용자는 직접 deserialize 하거나 나중에 사용할 수 있도록 저장할 수 있습니다.

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

이제 응용 프로그램에 장면이 있으므로 응용 프로그램은 SceneObjects를 보고 상호 작용 합니다. **SceneObjects** 속성에 액세스 하 여이 작업을 수행 합니다.

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

### <a name="component-update-and-refinding-components"></a>구성 요소 업데이트 및 refinding 구성 요소

***FindComponent*** 라는 장면에서 구성 요소를 검색 하는 다른 함수가 있습니다. 이 함수는 추적 개체를 업데이트 하 고 나중에 백그라운드에서 찾을 때 유용 합니다. 다음 코드는 이전 장면을 기준으로 새 장면을 계산 하 고 새 장면에서 바닥을 찾습니다.

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

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>장면 개체에서 메시 및 Quads 액세스

SceneObjects 발견 되 면 응용 프로그램은 구성 된 quads/메시에 포함 된 데이터에 액세스 하려고 할 가능성이 높습니다. 이 데이터는 ***Quads** _ 및 _ *_메시_** 속성을 사용 하 여 액세스 됩니다. 다음 코드는 floor 개체의 모든 quads 및 메시를 열거 합니다.

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

이는 장면 원점에 상대적인 변환을 포함 하는 SceneObject입니다. 이는 SceneObject가 "사물"의 인스턴스를 나타내므로 공간에 과정이, quads 및 망상은 부모를 기준으로 변환 되는 기 하 도형을 나타낸다는 것입니다. 별도의 SceneObjects가 동일한 SceneMesh/SceneQuad SceneComponents를 참조할 수 있으며 SceneObject에 두 개 이상의 SceneMesh/SceneQuad가 있을 수 있습니다.

### <a name="dealing-with-transforms"></a>변형 처리

장면 이해는 변환을 처리할 때 일반적인 3D 장면 표현과 맞추는 시도를 만들었습니다. 따라서 각 장면은 가장 일반적인 3D 환경 표현과 마찬가지로 단일 좌표계로 한정 됩니다. SceneObjects는 각 좌표계에 상대적인 위치를 제공 합니다. 응용 프로그램이 단일 원본에서 제공 하는 것의 제한을 스트레치 하는 장면을 처리 하는 경우 SpatialAnchors에 SceneObjects을 고정 하거나 여러 개의 장면을 생성 하 고 함께 병합할 수 있습니다. 하지만 간단 하 게 하기 위해에 의해 정의 된 하나의 NodeId로 지역화 된 자체 원본에 watertight 장면이 있다고 가정 합니다.

예를 들어 다음 Unity 코드는 Windows 인식 및 Unity api를 사용 하 여 좌표계를 함께 맞추는 방법을 보여 줍니다. unity의 세계 원본에 해당 하는 SpatialCoordinateSystem를 가져오는 방법에 대 한 자세한 내용은 [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 및 [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) (영문) 및 [unity의 혼합 현실 네이티브 개체](/windows/mixed-reality/unity-xrdevice-advanced) 에 대 Windows 한 자세한 내용을 참조 하세요.

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

각 `SceneObject` 에는 해당 개체에 적용 되는 변환이 있습니다. Unity에서 다음과 같이 올바른 전달 좌표로 변환 하 고 로컬 변환을 할당 합니다.

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

### <a name="quad"></a>Led

Quads는 2D 배치 시나리오를 지원 하도록 설계 되었으며 2D canvas UX 요소에 대 한 확장으로 간주 되어야 합니다. Quads는 SceneObjects의 구성 요소이 고 3D로 렌더링 될 수 있지만 쿼드 Api 자체는 Quads이 2D 구조인 것으로 가정 합니다. 익스텐트, 모양, 배치를 위한 Api 제공 등의 정보를 제공 합니다.

Quads는 사각형 범위를 갖지만 임의의 모양의 2D 표면을 나타냅니다. 3D 환경 quads와 상호 작용 하는 이러한 2D 표면에서 배치를 사용 하도록 설정 하려면 이러한 상호 작용을 가능 하 게 하는 유틸리티를 제공 합니다. 현재 장면 이해는 **Findcentermostplacement** 및 **GetSurfaceMask** 의 두 가지 함수를 제공 합니다. FindCentermostPlacement는 개체를 배치할 수 있는 쿼드 위치를 찾고 개체에 가장 적합 한 위치를 찾으려고 시도 하는 상위 수준의 API로, 사용자가 제공 하는 경계 상자가 기본 화면에 유지 되도록 보장 합니다.

> [!NOTE]
> 출력의 좌표는 다른 windows Rect 형식에 있는 것 처럼 (x = 0, y = 0) 왼쪽 위 모퉁이가 있는 "쿼드 공간"의 쿼드에 상대적입니다. 사용자 고유의 개체의 원본으로 작업할 때는이를 고려해 야 합니다. 

다음 예에서는 가장 높은 배치 가능한 위치를 찾고 4 번째에 홀로그램을 고정 하는 방법을 보여 줍니다.

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

1-4 단계는 특정 프레임 워크/구현에 따라 달라 지지만 테마는 유사 해야 합니다. 4는 단지 공간에서 지역화 된 경계가 있는 2D 평면을 나타내는 것입니다. 엔진/프레임 워크에서 쿼드이 무엇 인지 확인 하 고 쿼드을 기준으로 개체를 루 팅 하면 holograms는 실제 세계와 관련 하 여 정확 하 게 배치 됩니다. 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>메시

메시는 개체 또는 환경의 기하학적 표현을 나타냅니다. [공간 매핑](../../design/spatial-mapping.md), 메시 인덱스 및 각 공간 표면 메시와 함께 제공 되는 꼭 짓 점 데이터는 모든 최신 렌더링 api에서 삼각형 메시 렌더링에 사용 되는 꼭 짓 점 및 인덱스 버퍼와 동일한 친숙 한 레이아웃을 사용 합니다. 꼭 짓 점 위치는의 좌표계에서 제공 됩니다 `Scene` . 이 데이터를 참조 하는 데 사용 되는 특정 Api는 다음과 같습니다.

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

다음 코드에서는 메시 구조에서 삼각형 목록을 생성 하는 예제를 제공 합니다.

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

인덱스/꼭 짓 점 버퍼는 인덱스/꼭 짓 점 수를 >해야 합니다. 그렇지 않으면 효율적인 메모리 재사용을 허용 하는 크기를 임의로 지정할 수 있습니다.

### <a name="collidermesh"></a>ColliderMesh

장면 개체는 메시 및 ColliderMeshes 속성을 통해 메시 및 collider 메시 데이터에 대 한 액세스를 제공 합니다. 이러한 메시는 항상 일치 합니다. 즉, 메시 속성의 i'th 인덱스가 ColliderMeshes 속성의 i'th 인덱스와 동일한 기 하 도형을 나타냅니다. 런타임/개체가 collider 메시를 지 원하는 경우, 응용 프로그램에서 colliders를 사용 하는 모든 위치에서 ColliderMeshes를 사용 하는 것이 좋습니다. 시스템에서 colliders을 지원 하지 않는 경우 ColliderMeshes에 반환 된 메시 개체는 메시에 서 메모리 제약 조건을 줄이는 것과 동일한 개체가 됩니다.

## <a name="developing-with-scene-understanding"></a>장면 이해로 개발

이 시점에서 런타임 및 SDK를 이해 하는 장면의 핵심 구성 요소를 이해 해야 합니다. 강력 하 고 복잡 한 점은 액세스 패턴, 3D 프레임 워크와의 상호 작용, 공간 계획, 방 분석, 탐색, 물리 등과 같은 고급 작업을 수행 하기 위해 이러한 Api 위에 작성할 수 있는 도구입니다. 시나리오를 표현할 수 있도록 적절 한 방향으로 안내 하는 샘플에서이를 캡처해야 합니다. 주소를 지정 하지 않는 샘플 또는 시나리오가 있으면 알려주세요. 그러면 필요한 항목을 문서화/프로토타입으로 시도 합니다.

### <a name="where-can-i-get-sample-code"></a>샘플 코드는 어디에서 얻을 수 있나요?

Unity 샘플 코드에 대 한 장면 이해는 [Unity 샘플 페이지](https://github.com/sceneunderstanding-microsoft/unitysample) 페이지에서 찾을 수 있습니다. 이 응용 프로그램을 사용 하면 장치와 통신 하 여 다양 한 장면 개체를 렌더링 하거나, PC에서 serialize 된 장면을 로드 하 고, 장치 없이 장면 이해를 경험할 수 있습니다.

### <a name="where-can-i-get-sample-scenes"></a>샘플 장면을 어디에서 얻을 수 있나요?

HoloLens2가 있는 경우 ComputeSerializedAsync의 출력을 파일에 저장 하 고 사용자의 편의를 위해이를 deserialize 하 여 캡처한 장면을 저장할 수 있습니다. 

HoloLens2 장치가 없지만 장면 이해를 재생 하려는 경우에는 미리 캡처된 장면을 다운로드 해야 합니다. 장면 이해 샘플은 현재 사용자의 편의를 위해 다운로드 하 여 사용할 수 있는 직렬화 된 장면과 함께 제공 됩니다. 여기에서 찾을 수 있습니다.

[장면 이해 샘플 장면](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a>참고 항목

* [공간 매핑](../../design/spatial-mapping.md)
* [장면 이해](../../design/scene-understanding.md)
* [Unity 샘플](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)