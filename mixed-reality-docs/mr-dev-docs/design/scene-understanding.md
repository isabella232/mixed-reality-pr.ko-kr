---
title: 장면 이해
description: SDK, 기능 및 일반적인 사용 시나리오를 포함하여 HoloLens 대한 장면 이해를 사용하여 개발하는 방법을 알아봅니다.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 장면 이해, 공간 매핑, Windows Mixed Reality, Unity, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, 폐색, SDK
ms.openlocfilehash: 4dd5a2c96478e50b2e9eda35be22c15c1db07f88cfc4d25d753c4860a1283f55
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213472"
---
# <a name="scene-understanding"></a>장면 이해

장면 이해는 Mixed Reality 개발자에게 환경 인식 애플리케이션을 직관적으로 개발할 수 있도록 설계된 구조화된 고수준 환경 표현을 제공합니다. 장면 이해는 정확하지만 덜 구조적인 [공간 매핑](spatial-mapping.md) 및 새로운 AI 기반 런타임과 같은 기존 혼합 현실 런타임의 기능을 결합하여 이를 수행합니다. 이러한 기술을 결합하여 장면 이해는 Unity 또는 ARKit/ARCore와 같은 프레임워크에서 사용했을 수 있는 것과 유사한 3D 환경의 표현을 생성합니다. 장면 이해 진입점은 애플리케이션에서 새 장면을 컴퓨팅하기 위해 호출하는 장면 관찰자로 시작합니다. 현재 이 기술은 고유하지만 관련된 세 가지 개체 범주를 생성할 수 있습니다.

* 평면 실내 구조를 복잡하게 유추하는 간소화된 watertight 환경 메시
* 쿼드라고 하는 배치를 위한 평면 영역
* 표면화한 Quads/Watertight 데이터와 일치하는 [공간 매핑](spatial-mapping.md) 메시의 스냅샷

![공간 매핑 메시, 레이블이 있는 평면 표면, watertight 메시](images/SUScenarios.png)

이 문서는 시나리오 개요를 제공하고 장면 이해 및 공간 매핑이 공유하는 관계를 명확히 하기 위한 것입니다. Scene Understanding이 작동하는 모습을 보려면 **아래의 디자인 홀로그램스 - 공간 인식** 비디오 데모를 확인하세요.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*이 동영상은 "홀로그램 디자인" HoloLens 2 앱에서 가져온 것입니다. [여기](https://aka.ms/dhapp)에서 전체 환경을 다운로드하여 즐겨 보세요.*

## <a name="developing-with-scene-understanding"></a>Scene Understanding을 통해 개발

이 문서는 Scene Understanding 런타임 및 개념을 소개하는 데만 사용됩니다. Scene Understanding을 사용하여 개발하는 방법에 대한 설명서를 찾는 경우 다음 문서에 관심이 있을 수 있습니다.

[Scene Understanding SDK 개요](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

샘플 GitHub 사이트에서 Scene Understanding 샘플 앱을 다운로드할 수 있습니다.

[장면 이해 샘플](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

디바이스가 없고 샘플 장면에 액세스하여 Scene Understanding을 사용해 보려는 경우 샘플 자산 폴더에 다음과 같은 장면이 있습니다.

[장면 이해 샘플 장면](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK)

Scene Understanding을 통해 개발하는 데 대한 구체적인 세부 정보를 찾고 있는 경우 [Scene Understanding SDK 개요](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 설명서를 참조하세요.

### <a name="sample"></a>샘플

## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>장면 이해</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>일반 시나리오

![일반적인 공간 매핑 사용 시나리오의 그림: 배치, 폐색, 물리학 및 탐색](images/sm-concepts-1000px.png)<br>
*일반적인 공간 매핑 사용 시나리오: 배치, 폐색, 물리학 및 탐색.*

<br>

환경 인식 애플리케이션에 대한 많은 핵심 시나리오는 공간 매핑 및 장면 이해를 통해 해결할 수 있습니다. 이러한 핵심 시나리오에는 배치, 폐색, 물리학 등이 포함됩니다. 장면 이해와 공간 매핑의 핵심 차이점은 최대 정확도와 구조 및 단순성의 대기 시간을 절충하는 것입니다. 애플리케이션에 가장 낮은 대기 시간이 필요하고 액세스하려는 메시 삼각형이 필요한 경우 공간 매핑을 직접 사용합니다. 더 높은 수준의 처리를 수행하는 경우 기능 상위 집합을 제공해야 하며 장면 이해 모델로 전환하는 것이 좋습니다. 장면 이해는 공간 매핑 메시의 스냅샷을 표현의 일부로 제공하므로 항상 가능한 가장 완전하고 정확한 공간 매핑 데이터에 액세스할 수 있습니다.

다음 섹션에서는 새로운 Scene understanding SDK의 컨텍스트에서 핵심 공간 매핑 시나리오를 다시 방문합니다.

### <a name="placement"></a>배치

장면 이해는 배치 시나리오를 간소화하도록 설계된 새로운 구문을 제공합니다. 장면에서는 홀로그램을 배치할 수 있는 평면 표면을 설명하는 SceneQuads라는 기본형을 계산할 수 있습니다. SceneQuads는 배치를 중심으로 설계되었으며 2D 표면을 설명하고 해당 화면에 배치하기 위한 API를 제공합니다. 이전에는 삼각형 메시를 사용하여 배치를 수행할 때 쿼드의 모든 영역을 검사하고 구멍 채우기/후처리를 수행하여 개체 배치에 적합한 위치를 식별해야 했습니다. 이는 장면 이해 런타임이 검색되지 않은 쿼드 영역을 유추하고 표면의 일부가 아닌 영역을 무효화하기 때문에 Quads에서 항상 필요한 것은 아닙니다.

:::row:::
    :::column:::
       ![유추가 비활성화된 SceneQuads는 검색된 영역에 대한 배치 영역을 캡처합니다.](images/SUQuads.png)<br>
       **이미지 #1** - 유추를 사용하지 않도록 설정하여 스캔한 지역의 배치 영역을 캡처하는 SceneQuads입니다.
    :::column-end:::
        :::column:::
       ![유추를 사용하는 쿼드, 배치는 더 이상 검색된 영역으로 제한되지 않습니다.](images/SUWatertight.png)<br>
        **이미지 #2** - 유추가 활성화된 쿼드, 배치는 더 이상 검사된 영역으로 제한되지 않습니다.
    :::column-end:::
:::row-end:::

<br>


애플리케이션이 환경의 엄격한 구조에 2D 또는 3D 홀로그램을 배치하려는 경우 배치를 위한 SceneQuads의 단순성과 편의성은 [공간 매핑](spatial-mapping.md) 메시에서 이 정보를 계산하는 것이 좋습니다. 이 항목에 대한 자세한 내용은 [장면 이해 SDK 참조를 참조하세요.](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

**참고** 공간 매핑 메시에 의존하는 레거시 배치 코드의 경우 EnableWorldMesh 설정을 통해 공간 매핑 메시를 SceneQuads와 함께 계산할 수 있습니다. 장면 이해 API가 애플리케이션의 대기 시간 요구 사항을 충족하지 않는 경우 [공간 매핑 API](spatial-mapping.md#placement)를 계속 사용하는 것이 좋습니다.

### <a name="occlusion"></a>폐색

[공간 매핑 폐색은](spatial-mapping.md#occlusion) 환경의 실시간 상태를 캡처하는 최소 대기 시간으로 유지됩니다. 이는 매우 동적인 장면에서 폐색을 제공하는 데 유용할 수 있지만 여러 가지 이유로 폐색에 대한 장면 이해를 고려할 수 있습니다. Scene Understanding에서 생성된 공간 매핑 메시를 사용하는 경우 로컬 캐시에 저장되지 않고 인식 API에서 사용할 수 없는 공간 매핑에서 데이터를 요청할 수 있습니다. 폐색에 공간 매핑을 watertight 메시와 함께 사용하면 추가 값, 특히 스캐닝되지 않은 공간 구조의 완성을 제공합니다.

요구 사항으로 장면 이해의 대기 시간이 늘어날 수 있는 경우 애플리케이션 개발자는 장면 이해 watertight 메시 및 평면 표현과 함께 공간 매핑 메시를 함께 사용하는 것을 고려해야 합니다. 이렇게 하면 가능한 가장 현실적인 폐색 맵을 제공하는 더 미세한 비 평면 기하 도형으로 간소화된 watertight 폐색이 고갈되는 "두 세계 모두의 최상" 시나리오가 제공됩니다.

### <a name="physics"></a>Physics

장면 이해는 공간 매핑 메시가 적용되는 물리학에 대한 많은 제한 사항을 해결하기 위해 의미 체계를 사용하여 공간을 분해하는 watertight 메시를 생성합니다. Watertight 구조는 물리학 광선 캐스트가 항상 적중되도록 하고, 의미 체계 분해를 통해 실내 탐색을 위해 탐색 메시를 더 간단하게 생성할 수 있습니다. [폐색](#occlusion)섹션에 설명된 대로 EnableSceneObjectMeshes 및 EnableWorldMesh를 사용하여 장면을 만들면 물리적으로 가장 완전한 메시가 생성됩니다. 환경 메시의 watertight 속성은 적중 테스트가 적중 표면에 실패하는 것을 방지합니다. 메시 데이터는 물리학이 공간 구조뿐만 아니라 장면의 모든 개체와 상호 작용하도록 합니다.

### <a name="navigation"></a>탐색

의미 체계 클래스에 의해 분해되는 평면 메시는 탐색 및 경로 계획에 이상적인 구문이며 공간 [매핑 탐색](spatial-mapping.md#navigation) 개요에 설명된 많은 문제를 완화합니다. 장면에서 계산된 SceneMesh 개체는 탐색 메시 생성이 탐색 메시 생성이 탐색할 수 있는 표면으로 제한되도록 표면 형식으로 구성 해제됩니다. 바닥 구조의 단순성으로 인해 Unity와 같은 3d 엔진의 동적 탐색 메시 생성은 실시간 요구 사항에 따라 달성할 수 있습니다.

정확한 탐색 메시를 생성하려면 현재 사후 처리가 필요합니다. 즉, 애플리케이션은 탐색이 복잡한/테이블을 통과하지 않도록 여전히 폐색을 바닥으로 프로젝션해야 합니다. 이 작업을 수행하는 가장 정확한 방법은 장면을 EnableWorldMesh 플래그로 계산하는 경우 제공되는 세계 메시 데이터를 프로젝터하는 것입니다.

### <a name="visualization"></a>시각화

[공간 매핑 시각화를](spatial-mapping.md#visualization) 환경의 실시간 피드백에 사용할 수 있지만, 평면 및 워터타이트 개체의 단순성이 더 많은 성능 또는 시각적 품질을 제공하는 많은 시나리오가 있습니다. 공간 매핑을 사용하여 설명하는 섀도 프로젝션 및 접지 기술은 쿼드 또는 평면 watertight 메시에서 제공하는 평면 표면에 프로젝션되는 경우 더 복잡할 수 있습니다. 이는 장면이 유추되고 전체 환경 및 평면 가정이 아티팩트 최소화를 위해 철저한 사전 검사가 최적이 아닌 환경/시나리오에서 특히 그렇습니다.

또한 공간 매핑에서 반환되는 총 표면 수는 내부 공간 캐시에 의해 제한되는 반면, Scene understanding의 공간 매핑 메시 버전은 캐시되지 않은 공간 매핑 데이터에 액세스할 수 있습니다. 따라서 장면 이해는 시각화 또는 추가 메시 처리를 위해 더 큰 공간(예: 단일 공간보다 큰 공간)에 대한 메시 표현을 캡처하는 데 더 적합합니다. EnableWorldMesh와 함께 반환된 세계 메시는 전체에서 일관된 수준의 세부 정보를 가지며, 이는 와이어프레임으로 렌더링되는 경우 더 많은 시각적 개체를 생성할 수 있습니다.

### <a name="see-also"></a>참고 항목

* [장면 이해 SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [공간 매핑](spatial-mapping.md)