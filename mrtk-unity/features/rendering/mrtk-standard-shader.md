---
title: MRTK 표준 셰이더
description: MRTKStandardShader에 대한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 재질 셰이더
ms.openlocfilehash: 0a92388bc9be7c11967501709031f559f17f8966
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176443"
---
# <a name="mrtk-standard-shader"></a>MRTK 표준 셰이더

![표준 셰이더 예제](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

MRTK Standard 음영 시스템은 Unity의 표준 셰이더와 비슷한 시각적 개체를 구현하고, [Fluent Design 시스템](https://www.microsoft.com/design/fluent/) 원칙을 구현하고, 혼합 현실 디바이스에서 뛰어난 성과를 유지할 수 있는 유연한 단일 셰이더를 활용합니다.

## <a name="example-scenes"></a>예제 장면

아래에 있는 **MaterialGallery** 장면에서 셰이더 재질 예제를 찾을 수 `MRTK/Examples/Demos/StandardShader/Scenes/` 있습니다. 이 장면의 모든 재질은 MRTK/표준 셰이더를 사용하고 있습니다.

![재질 갤러리](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

아래의 **StandardMaterialComparison** 장면에서 Unity/표준 셰이더 예제와 MRTK/표준 셰이더를 비교하고 테스트하는 비교 장면을 찾을 수 `MRTK/Examples/Demos/StandardShader/Scenes/` 있습니다.

![재질 비교](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a>Architecture

MRTK/표준 음영 시스템은 [Unity의 셰이더 프로그램 변형 기능을](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) 사용하여 재질 속성에 따라 최적의 셰이더 코드를 자동으로 생성하는 "uber 셰이더"입니다. 사용자가 재질 검사기에서 재질 속성을 선택하면 사용하도록 설정한 기능에 대한 성능 비용만 발생합니다.

## <a name="material-inspector"></a>재질 검사기

라는 MRTK/표준 셰이더에 대한 사용자 지정 재질 검사자가 [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) 있습니다. 검사기에서는 사용자 선택 및 렌더링 상태 설정에 따라 셰이더 기능을 자동으로 사용하거나 사용하지 않도록 설정합니다. 각 기능에 대한 자세한 내용은 **도구 설명에 대한 Unity 편집기에서 각 속성을 마우스로 가리키세요.**

![재질 검사기](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

검사기의 첫 번째 부분은 재질의 렌더링 상태를 제어합니다. *렌더링 모드는* 재질이 렌더링되는 시기와 방법을 결정합니다. MRTK/표준 셰이더의 목표는 [Unity/표준 셰이더 에 있는 렌더링 모드를 미러링하는](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)것입니다. MRTK/표준 셰이더에는 추가 *렌더링* 모드와 완전한 사용자 정의 컨트롤을 위한 *사용자 지정* 렌더링 모드도 포함되어 있습니다.

| 렌더링 모드 |         Description                                                       |
|----------------|---------------------------------------------------------------------------|
| 불투명         | (기본값) 투명 영역이 없는 일반 단색 개체에 적합합니다.    |
| 컷아웃         | 불투명 영역과 투명 영역 사이에 하드 가장자리가 있는 투명 효과를 만들 수 있습니다. 이 모드에서는 반투명 영역이 없거나 질감이 100% 불투명하거나 보이지 않습니다. 투명도를 사용하여 초목과 같은 재질 모양을 만들 때 유용합니다. |
| 페이드           | 반사 강조 표시 또는 리플렉션을 포함하여 투명도 값이 개체를 완전히 페이드 아웃하도록 허용합니다. 이 모드는 개체 페이드 인 또는 아웃에 애니메이션을 적용하려는 경우에 유용합니다. 반사와 강조 표시도 흐리게 표시되므로 투명한 투명 재질(예: 투명 투명 재질)을 렌더링하는 데 적합하지 않습니다. |
| 투명    | 투명 투명 재질(예: 투명 투명 재질)을 렌더링하는 데 적합합니다. 이 모드에서는 재질 자체가 투명도 값(질감의 알파 채널 및 색조 색의 알파에 따라)을 적용합니다. 그러나 반사 및 조명 강조 표시는 실제 투명 재질의 경우처럼 완전히 명확하게 표시됩니다. |
| 더하기       | 이전 픽셀 색을 현재 픽셀 색과 합산하는 가감 혼합 모드를 사용하도록 설정합니다. 투명도 정렬 문제를 방지하기 위한 기본 투명도 모드입니다.     |
| 사용자 지정         | 렌더링 모드의 모든 측면을 수동으로 제어할 수 있습니다. 고급 용도로만 사용할 수 있습니다.   |

![렌더링 모드](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| 추리 모드 |             Description                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 끄기       | 얼굴 제거를 사용하지 않도록 설정합니다. 두 면 메시가 필요한 경우에만 끄기로 설정해야 합니다.                                                                                        |
| Front     | 앞면을 자를 수 있습니다.                                                                                                                                                        |
| 뒤로      | (기본값) [백페이스 중에서 을(를) 자를 수 있습니다.](https://en.wikipedia.org/wiki/Back-face_culling) 렌더링 성능을 향상하기 위해 가능한 한 자주 얼굴 전경색을 사용하도록 설정해야 합니다. |

## <a name="performance"></a>성능

Unity 표준 셰이더보다 MRTK 표준 셰이더를 사용하는 경우의 주요 이점 중 하나는 성능입니다. MRTK 표준 셰이더를 사용하면 활성화된 기능만 활용할 수 있습니다. 그러나 MRTK 표준 셰이더도 Unity 표준 셰이더와 비슷한 미적 결과를 제공하기 위해 작성되었지만 훨씬 저렴한 비용으로 작성되었습니다. 셰이더 성능을 비교하는 간단한 방법 중 하나는 GPU에서 수행해야 하는 작업 수를 통하는 것입니다. 물론 계산 크기는 사용하도록 설정된 기능 및 기타 렌더링 구성에 따라 변동될 수 있습니다. 그러나 일반적으로 MRTK 표준 셰이더가 Unity 표준 셰이더보다 훨씬 적은 계산을 수행합니다.

Unity 표준 셰이더 통계 예제

![Unity 표준 셰이더 통계](../images/performance/UnityStandardShader-Stats.PNG)

MRTK 표준 셰이더 통계 예제

![MRTK 표준 셰이더 통계](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> Unity 검사기에서 [셰이더 자산을](https://docs.unity3d.com/Manual/class-Shader.html) 선택하고 본 다음 *컴파일 및 코드 표시* 단추를 클릭하여 이러한 결과를 생성할 수 있습니다.

## <a name="lighting"></a>조명

MRTK/표준은 조명에 간단한 근사값을 사용합니다. 이 셰이더에서는 물리적 정확성 및 에너지 소모를 계산하지 않으므로 빠르고 효율적으로 렌더링합니다. Blinn-Phong 기본 조명 기술로, Fresnel 및 이미지 기반 조명과 혼합되어 물리적 조명을 기반으로 합니다. 셰이더에서 지원하는 조명 기술은 다음과 같습니다.

### <a name="directional-light"></a>방향성 광원

셰이더가 장면에서 첫 번째 Unity Directional Light의 방향, 색 및 강도를 준수합니다(사용하도록 설정된 경우). 동적 점등, 스폿 조명 또는 기타 Unity 광원은 실시간 조명에서 고려되지 않습니다.

### <a name="spherical-harmonics"></a>구면 계열

셰이더가 광원 프로브를 사용하여 구형 운율(사용하도록 설정된 경우)을 사용하여 장면의 [광원을 대략적으로 표시합니다.](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html) 구면 계측 계산은 계산 비용을 줄이기 위해 꼭짓점별로 수행됩니다.

### <a name="lightmapping"></a>Lightmapping

정적 조명의 경우 셰이더가 Unity의 Lightmapping 시스템 로 빌드된 [Lightmaps를 준수합니다.](https://docs.unity3d.com/Manual/Lightmapping.html) 렌더러를 정적(또는 lightmap static)으로 표시하기만 하면 lightmaps를 사용할 수 있습니다.

### <a name="hover-light"></a>마우스로 가리키기 조명

* [마우스로 가리키기 조명을 참조하세요.](hover-light.md)

### <a name="proximity-light"></a>근접 광원

* [근접 광원을 참조하세요.](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>경량 스크립팅 가능한 렌더링 파이프라인 지원

MRTK에는 개발자가 MRTK 셰이더를 사용하여 Unity의 LWRP(Lightweight Scriptable Render Pipeline)를 활용할 수 있도록 하는 업그레이드 경로가 포함되어 있습니다. Unity 2019.1.1f1 및 경량 RP 5.7.2 패키지에서 테스트되었습니다. 또는 LWRP 시작에 대한 지침은 [이 페이지를](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html)참조하세요.

MRTK 업그레이드를 수행하려면 **Mixed Reality Toolkit -> 유틸리티 -> Lightweight Render Pipeline용 MRTK 표준 셰이더 업그레이드를** 선택합니다.

![lwrp 업그레이드](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

업그레이드가 발생한 후 MRTK/표준 셰이더가 변경되고 자홍(셰이더 오류) 재질을 수정해야 합니다. 업그레이드가 성공적으로 수행되었는지 확인하려면 **콘솔에서 업그레이드된 자산/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader에서 경량 렌더링 파이프라인과 함께 사용할** 수 있는지 확인합니다.

## <a name="ugui-support"></a>UGUI 지원

MRTK 표준 음영 시스템은 Unity의 기본 제공 [UI 시스템 에서](https://docs.unity3d.com/Manual/UISystem.html)작동합니다. Unity UI 구성 요소에서 unity_ObjectToWorld 행렬은 그래픽 구성 요소가 있는 로컬 변환의 변환 매트릭스가 아니라 부모 Canvas의 변환 매트릭스입니다. 많은 MRTK/표준 셰이더 효과를 사용하려면 개체 배율 을 알고 있어야 합니다. 이 문제를 해결하기 위해 는 [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) UI 메시 생성 중에 크기 조정 정보를 UV 채널 특성에 저장합니다.

Unity 이미지 구성 요소를 사용하는 경우 Unity UI에서 추가 꼭짓점을 생성하지 못하도록 원본 이미지에 "없음(스프라이트)"을 지정하는 것이 좋습니다.

MRTK 내의 캔버스는 필요한 경우를 추가 하 라는 메시지를 표시 합니다 [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) .

![크기 조정 메시 효과](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>질감 결합 자

픽셀 금속성 Unity 표준 셰이더를 사용 하 여 패리티를 향상 시키기 위해 발광 및 폐색 값은 모두 [채널 압축](http://wiki.polycount.com/wiki/ChannelPacking)을 통해 제어할 수 있습니다. 예를 들어:

![채널 맵 예](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

채널 압축을 사용 하는 경우 4 개의 개별 항목 대신 메모리에 하나의 질감을 샘플링 하 고 로드 하기만 하면 됩니다. 질감이 나 Photoshop과 같은 프로그램에서 질감 맵을 작성 하는 경우 다음과 같이 직접 압축할 수 있습니다.

| 채널 | 속성             |
|---------|----------------------|
| 빨강     | 금속             |
| 녹색   | 폐색            |
| 파랑    | 내보내기 (회색조로 변환) |
| 알파   | 원활           |

또는 MRTK 텍스처 결합 자 도구를 사용할 수 있습니다. 이 도구를 열려면 다음 창을 열 **혼합 현실 Toolkit-> 유틸리티-> 텍스처 결합 자** 를 선택 합니다.

![질감 결합 자 예제](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

Unity 표준 셰이더를 선택 하 고 "표준 자료에서 자동"를 클릭 하 여이 창을 자동으로 채울 수 있습니다. 또는 빨강, 녹색, 파랑 또는 알파 채널 별로 텍스처 (또는 상수 값)를 수동으로 지정할 수 있습니다. 질감 조합은 GPU 가속 이며 입력 질감이 CPU에 액세스할 필요가 없습니다.

## <a name="additional-feature-documentation"></a>추가 기능 설명서

다음은 MRTK/표준 셰이더에 제공 되는 몇 가지 기능 정보에 대 한 추가 세부 정보입니다.

### <a name="primitive-clipping"></a>기본 클리핑

![기본 클리핑](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* [기본 클리핑](clipping-primitive.md) 참조

### <a name="mesh-outlines"></a>메시 윤곽선

많은 메시 개요 기술은 [post 처리](https://docs.unity3d.com/Manual/PostProcessingOverview.html) 기술을 사용 하 여 수행 됩니다. 사후 처리는 뛰어난 품질의 개요를 제공 하지만 많은 혼합 현실 장치에서 매우 많은 비용이 소요 될 수 있습니다. 의  **OutlineExamples** 장면에서 메시 윤곽선의 사용을 보여 주는 장면을 찾을 수 있습니다 `MRTK/Examples/Demos/StandardShader/Scenes/` .

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) 및 [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) 는 메시 렌더러 주위에 윤곽선을 렌더링 하는 데 사용할 수 있습니다. 이 구성 요소를 사용 하도록 설정 하면 윤곽이 설정 된 개체의 추가 렌더링 패스가 도입 되지만, 모바일 혼합 현실 장치에서 performantly를 실행 하 고 post 프로세스를 활용 하지 않습니다. 이 효과의 제한 사항에는 watertight 되지 않는 개체 (또는 양면 이어야 함)에서 제대로 작동 하지 않는 경우와 겹치는 개체에서 깊이 정렬 문제가 발생할 수 있습니다.

개요 동작은 MRTK/표준 셰이더와 함께 사용 하도록 설계 되었습니다. 개요 재질은 일반적으로 단색 unlit 색 이지만 광범위 한 효과를 얻기 위해 구성 될 수 있습니다. 개요 재질의 기본 구성은 다음과 같습니다.

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. 개요를 사용 하 여 다른 개체의 렌더링을 방해 하지 않도록 개요 자료에 대해 깊이 쓰기를 사용 하지 않도록 설정 해야 합니다.
2. 꼭 짓 점 밀어내기-개요를 렌더링 하려면 사용 하도록 설정 해야 합니다.
3. 부드러운 법선 사용-일부 메시의 경우이 설정은 선택 사항입니다. 밀어내기는 꼭 짓 점 법선을 따라 이동 하 여 발생 합니다. 일부 메시의 경우 기본 법선을 따라 extruding 윤곽선의 불연속성이 발생 합니다. 이러한 불연속성를 해결 하려면이 상자를 선택 하 여에서 생성 되는 다른 곡선 법선 집합을 사용할 수 있습니다. [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)

[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 는 메시에서 곡선의 법선을 자동으로 생성 하는 데 사용할 수 있는 구성 요소입니다. 이 메서드는 공간의 동일한 위치를 공유 하는 망상의 꼭 짓 점을 그룹화 하 고 해당 꼭 짓 점의 법선을 평균 합니다. 이 프로세스는 기본 메시의 복사본을 만들고 필요한 경우에만 사용 해야 합니다.

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. 를 통해 부드러운 법선이 생성 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 됩니다.
2. 기본 법선을 사용 합니다. 큐브 모퉁이 주위의 아티팩트를 확인 합니다.

### <a name="stencil-testing"></a>스텐실 테스트

광범위 한 효과를 얻기 위해 구성 가능한 스텐실 테스트 지원이 기본 제공 됩니다. 예: 포털:

![스텐실 테스트](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>인스턴스화된 색 지원

인스턴스화된 색 지원: 수천 개의 GPU 인스턴스 메시 고유의 재질 속성:

![인스턴스 속성](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>Triplanar 매핑

Triplanar 매핑은 메시를 프로그래밍 방식으로 텍스처 하는 기술입니다. UVs를 사용 하지 않거나 셰이프를 래핑 하기 어려운 지형에서 주로 사용 됩니다. 이 구현은 세계 또는 지역 공간 프로젝션을 지원 하 고 혼합 혼합 및 법선 지도 지원을 지원 합니다. 사용 되는 각 질감에는 3 개의 질감 샘플이 필요 하므로 성능에 중요 한 상황에서는 아주 드물게 사용 합니다.

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>꼭 짓 점 밀어내기

세계 공간의 꼭 짓 점 입체 면입니다. 돌출 경계 볼륨 또는 전환을 시각화/축소 하는 데 유용 합니다.

![법선 지도 눈금 1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>기타

Albedo 최적화를 제어 하는 확인란입니다. 최적화 albedo 질감이 지정 되지 않은 경우 최적화를 사용할 수 없습니다. 이는 [원격 질감 로드](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)를 제어 하는 데 유용 합니다.

이 확인란을 선택 하면 됩니다.

![albedo 할당](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

픽셀 클리핑 질감, 로컬 가장자리 기반 앤티 앨리어싱 및 법선 지도 배율이 지원 됩니다.

![기본 지도 배율 2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>참조

* [상호 작용 가능](../ux-building-blocks/interactable.md)
* [가리키기 라이트](hover-light.md)
* [근접 조명](proximity-light.md)
* [기본 클리핑](clipping-primitive.md)
