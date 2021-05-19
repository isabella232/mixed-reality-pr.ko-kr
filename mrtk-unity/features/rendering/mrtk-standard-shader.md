---
title: MRTK 표준 세이더
description: MRTKStandardShader에 대한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 재질 셰이더
ms.openlocfilehash: 8b570ebb023305cecbeca16b32832417a3f57cce
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145111"
---
# <a name="mrtk-standard-shader"></a>MRTK 표준 세이더

![표준 셰이더 예제](../images/mrtk-standard-shader/MRTK_StandardShader.jpg)

MRTK 표준 음영 시스템은 Unity의 표준 셰이더와 비슷한 시각적 개체를 구현하고, [Fluent Design 시스템](https://www.microsoft.com/design/fluent/) 원칙을 구현하고, 혼합 현실 디바이스에서 뛰어난 성과를 유지할 수 있는 유연한 단일 셰이더를 활용합니다.

## <a name="example-scenes"></a>예제 장면

아래에 있는 **MaterialGallery** 장면에서 셰이더 재질 예제를 찾을 수 `MRTK/Examples/Demos/StandardShader/Scenes/` 있습니다. 이 장면의 모든 재질은 MRTK/표준 셰이더를 사용하고 있습니다.

![재질 갤러리](../images/mrtk-standard-shader/MRTK_MaterialGallery.jpg)

아래 **StandardMaterialComparison** 장면의 Unity/표준 셰이더 예제와 MRTK/표준 셰이더를 비교하고 테스트하는 비교 장면을 찾을 수 `MRTK/Examples/Demos/StandardShader/Scenes/` 있습니다.

![재질 비교](../images/mrtk-standard-shader/MRTK_StandardMaterialComparison.gif)

## <a name="architecture"></a>Architecture

MRTK/표준 음영 시스템은 [Unity의 셰이더 프로그램 변형 기능을](https://docs.unity3d.com/Manual/SL-MultipleProgramVariants.html) 사용하여 재질 속성에 따라 최적의 셰이더 코드를 자동으로 생성하는 "uber 셰이더"입니다. 사용자가 재질 검사기에서 재질 속성을 선택하면 사용하도록 설정한 기능에 대한 성능 비용만 발생합니다.

## <a name="material-inspector"></a>재질 검사기

라는 MRTK/표준 셰이더에 대한 사용자 지정 재질 검사자가 [`MixedRealityStandardShaderGUI.cs`](xref:Microsoft.MixedReality.Toolkit.Editor.MixedRealityStandardShaderGUI) 있습니다. 검사기에서는 사용자 선택 및 렌더링 상태 설정에 따라 셰이더 기능을 자동으로 사용하거나 사용하지 않도록 설정합니다. 각 기능에 대한 자세한 내용은 **도구 설명에 대한 Unity 편집기에서 각 속성을 마우스로 가리키세요.**

![재질 검사기](../images/mrtk-standard-shader/MRTK_MaterialInspector.jpg)

검사기의 첫 번째 부분은 재질의 렌더링 상태를 제어합니다. *렌더링 모드는* 재질을 렌더링할 시기와 방법을 결정합니다. MRTK/표준 셰이더의 목표는 [Unity/표준 셰이더 에 있는 렌더링 모드를 미러링하는](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html)것입니다. MRTK/표준 셰이더에는 추가 *렌더링* 모드와 완전한 사용자 정의 컨트롤을 위한 *사용자 지정* 렌더링 모드도 포함되어 있습니다.

| 렌더링 모드 |         설명                                                       |
|----------------|---------------------------------------------------------------------------|
| 불투명         | 기본 투명 영역이 없는 일반 solid 개체에 적합 합니다.    |
| 오려낸         | 불투명 영역과 투명 영역 사이에 가장자리가 딱딱한 투명 효과를 만들 수 있습니다. 이 모드에는 반 투명 영역이 없으며, 질감이 100% 불투명 하거나 보이지 않습니다. 이는 투명도를 사용 하 여 vegetation 등의 재질 셰이프를 만들 때 유용 합니다. |
| 인하           | 투명 값이 반사 하이라이트 또는 반사를 포함 하 여 개체를 완전히 페이드 아웃할 수 있도록 허용 합니다. 이 모드는 개체에 페이드 인 또는 페이드 아웃 효과를 적용 하려는 경우에 유용 합니다. 반사 및 강조 표시도 페이드 아웃 되기 때문에 선명한 플라스틱 또는 유리와 같은 사실적인 투명 자료를 렌더링 하는 데 적합 하지 않습니다. |
| 투명    | 선명한 플라스틱 또는 유리와 같이 사실적인 투명 자료를 렌더링 하는 데 적합 합니다. 이 모드에서 재질 자체는 질감의 알파 채널과 색조 색의 알파에 따라 투명도 값을 사용 합니다. 그러나 반사 및 조명 강조 표시는 실제 투명 자료를 사용 하는 경우 처럼 완전히 명확 하 게 표시 됩니다. |
| 더하기       | 현재 픽셀 색을 사용 하 여 이전 픽셀 색의 합계를 계산 하는 가산적 혼합 모드를 사용 하도록 설정 합니다. 투명도 정렬 문제를 방지 하기 위한 기본 투명도 모드입니다.     |
| 사용자 지정         | 렌더링 모드의 모든 측면을 수동으로 제어할 수 있습니다. 고급 사용을 위한 것입니다.   |

![렌더링 모드](../images/mrtk-standard-shader/MRTK_RenderingModes.jpg)

| 추려내 모드 |             설명                                                                                                                                                                       |
|-----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 끄기       | 얼굴 고르기 사용 하지 않습니다. 고르기은 두 개의 면 메쉬가 필요한 경우에만 Off로 설정 해야 합니다.                                                                                        |
| Front     | Front face 고르기를 사용 합니다.                                                                                                                                                        |
| 뒤로      | 기본 [뒷면 고르기](https://en.wikipedia.org/wiki/Back-face_culling)를 사용 하도록 설정 합니다. 렌더링 성능을 향상 시키려면 가능한 한 자주 고르기를 사용 하도록 설정 해야 합니다. |

## <a name="performance"></a>성능

Unity 표준 셰이더에 MRTK 표준 셰이더를 사용할 경우의 주요 이점 중 하나는 성능입니다. MRTK 표준 셰이더는 사용 하도록 설정 된 기능만 사용 하도록 확장할 수 있습니다. 그러나 MRTK 표준 셰이더는 Unity 표준 셰이더에 해당 하는 미적 결과를 제공 하기 위해 작성 되었지만 훨씬 더 저렴 합니다. 셰이더 성능을 비교 하는 한 가지 간단한 방법은 GPU에서 수행 해야 하는 작업 수를 통하는 것입니다. 물론 계산의 크기는 설정 된 기능 및 기타 렌더링 구성에 의해 변동 수 있습니다. 그러나 일반적으로 MRTK 표준 셰이더는 Unity 표준 셰이더에 비해 훨씬 더 많은 계산을 수행 합니다.

Unity 표준 셰이더 통계 예제

![Unity 표준 셰이더 통계](../images/performance/UnityStandardShader-Stats.PNG)

MRTK 표준 셰이더 통계 예제

![MRTK 표준 셰이더 통계](../images/performance/MRTKStandardShader-Stats.PNG)

> [!NOTE]
> 이러한 결과는 Unity 검사기에서 [셰이더 자산](https://docs.unity3d.com/Manual/class-Shader.html) 을 선택 하 고 표시 한 다음 *컴파일 및 코드 표시* 단추를 클릭 하 여 생성할 수 있습니다.

## <a name="lighting"></a>조명

MRTK/Standard는 조명에 대해 간단한 근사값을 사용 합니다. 이 셰이더는 물리적 정확성 및 에너지 절약을 계산 하지 않으므로 빠르고 효율적으로 렌더링 됩니다. Blinn-Phong는 물리적으로 가까운 조명에 맞게 프레스 넬 대칭 및 이미지 기반 조명과 혼합 되는 기본 조명 기술입니다. 셰이더는 다음과 같은 조명 기술을 지원 합니다.

### <a name="directional-light"></a>방향성 광원

셰이더는 장면의 첫 번째 Unity 방향성 광원의 방향, 색 및 강도를 반영 합니다 (설정 된 경우). 동적 점 광원, 스폿 광원 또는 기타 Unity 조명은 실시간 조명에서 고려 되지 않습니다.

### <a name="spherical-harmonics"></a>구면 고조파

셰이더가 광원 프로브를 사용하여 구형 운율(사용하도록 설정된 경우)을 사용하여 장면의 [광원을 대략적으로 표시합니다.](https://docs.unity3d.com/Manual/LightProbes-TechnicalInformation.html) 구면 계측 계산은 계산 비용을 줄이기 위해 꼭짓점별로 수행됩니다.

### <a name="lightmapping"></a>Lightmapping

정적 조명의 경우 셰이더가 Unity의 Lightmapping 시스템 에서 빌드한 [lightmaps를 준수합니다.](https://docs.unity3d.com/Manual/Lightmapping.html) 렌더러를 정적(또는 lightmap static)으로 표시하기만 하면 lightmaps를 사용할 수 있습니다.

### <a name="hover-light"></a>마우스로 가리키기 조명

* [마우스로 가리키기 조명을 참조하세요.](hover-light.md)

### <a name="proximity-light"></a>근접 광원

* [근접 광원을 참조하세요.](proximity-light.md)

## <a name="lightweight-scriptable-render-pipeline-support"></a>경량 스크립팅 가능한 렌더링 파이프라인 지원

MRTK에는 개발자가 MRTK 셰이더를 사용하여 Unity의 LWRP(Lightweight Scriptable Render Pipeline)를 활용할 수 있도록 하는 업그레이드 경로가 포함되어 있습니다. Unity 2019.1.1f1 및 경량 RP 5.7.2 패키지에서 테스트되었습니다. 또는 LWRP 시작에 대한 지침은 [이 페이지를](https://docs.unity3d.com/Packages/com.unity.render-pipelines.lightweight@5.10/manual/getting-started-with-lwrp.html)참조하세요.

MRTK 업그레이드를 수행하려면 **Mixed Reality Toolkit -> Utilities -> Lightweight Render Pipeline용 MRTK 표준 셰이더 업그레이드를** 선택합니다.

![lwrp 업그레이드](../images/mrtk-standard-shader/MRTK_LWRPUpgrade.jpg)

업그레이드가 발생한 후 MRTK/표준 셰이더가 변경되고 자홍(셰이더 오류) 재질을 수정해야 합니다. 업그레이드가 성공적으로 수행되었는지 확인하려면 **콘솔에서 업그레이드된 자산/MixedRealityToolkit/StandardAssets/Shaders/MixedRealityStandard.shader에서 경량 렌더링 파이프라인과 함께 사용할** 수 있는지 확인합니다.

## <a name="ugui-support"></a>UGUI 지원

MRTK 표준 음영 시스템은 Unity의 기본 제공 [UI 시스템 에서](https://docs.unity3d.com/Manual/UISystem.html)작동합니다. Unity UI 구성 요소에서 unity_ObjectToWorld 행렬은 그래픽 구성 요소가 있는 로컬 변환의 변환 매트릭스가 아니라 부모 Canvas의 변환 매트릭스입니다. 많은 MRTK/표준 셰이더 효과를 위해서는 개체 크기를 알고 있어야 합니다. 이 문제를 해결 하기 위해에서는 [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) UI 메시 생성 중에 확장 정보를 UV 채널 특성에 저장 합니다.

Unity 이미지 구성 요소를 사용 하는 경우 Unity UI에서 추가 꼭 짓 점 생성을 방지 하기 위해 원본 이미지에 대해 "없음 (스프라이트)"을 지정 하는 것이 좋습니다.

MRTK 내의 캔버스는 필요한 경우를 추가 하 라는 메시지를 표시 합니다 [`ScaleMeshEffect.cs`](xref:Microsoft.MixedReality.Toolkit.Input.Utilities.ScaleMeshEffect) .

![크기 조정 메시 효과](../images/mrtk-standard-shader/MRTK_ScaleMeshEffect.jpg)

## <a name="texture-combiner"></a>질감 결합 자

픽셀 금속성 Unity 표준 셰이더를 사용 하 여 패리티를 향상 시키기 위해 발광 및 폐색 값은 모두 [채널 압축](http://wiki.polycount.com/wiki/ChannelPacking)을 통해 제어할 수 있습니다. 예를 들면 다음과 같습니다.

![채널 맵 예](../images/mrtk-standard-shader/MRTK_ChannelMap.gif)

채널 압축을 사용 하는 경우 4 개의 개별 항목 대신 메모리에 하나의 질감을 샘플링 하 고 로드 하기만 하면 됩니다. 질감이 나 Photoshop과 같은 프로그램에서 질감 맵을 작성 하는 경우 다음과 같이 직접 압축할 수 있습니다.

| 채널 | 속성             |
|---------|----------------------|
| 빨간색     | 금속             |
| 녹색   | 폐색            |
| 파랑    | 내보내기 (회색조로 변환) |
| 알파   | 원활           |

또는 MRTK 텍스처 결합 자 도구를 사용할 수 있습니다. 이 도구를 열려면 다음 창을 열 **혼합 현실 도구 키트-> 유틸리티-> 텍스처 결합 자** 를 선택 합니다.

![질감 결합 자 예제](../images/mrtk-standard-shader/MRTK_TextureCombiner.jpg)

Unity 표준 셰이더를 선택 하 고 "표준 자료에서 자동"를 클릭 하 여이 창을 자동으로 채울 수 있습니다. 또는 빨강, 녹색, 파랑 또는 알파 채널 별로 텍스처 (또는 상수 값)를 수동으로 지정할 수 있습니다. 질감 조합은 GPU 가속 이며 입력 질감이 CPU에 액세스할 필요가 없습니다.

## <a name="additional-feature-documentation"></a>추가 기능 설명서

다음은 MRTK/표준 셰이더에서 사용할 수 있는 몇 가지 기능 세부 정보를 자세히 설명합니다.

### <a name="primitive-clipping"></a>기본 클리핑

![기본 클리핑](../images/mrtk-standard-shader/MRTK_PrimitiveClipping.gif)

* [클리핑 기본형을 참조하세요.](clipping-primitive.md)

### <a name="mesh-outlines"></a>메시 윤곽선

많은 메시 개요 기술은 [사후 처리](https://docs.unity3d.com/Manual/PostProcessingOverview.html) 기술을 사용하여 수행됩니다. 사후 처리는 뛰어난 품질의 개요를 제공하지만 많은 Mixed Reality 디바이스에서 엄청난 비용이 들 수 있습니다. **아래의 OutlineExamples** 장면에서 메시 윤곽선의 사용을 보여 주는 장면을 찾을 수 `MRTK/Examples/Demos/StandardShader/Scenes/` 있습니다.

<img src="../images/mrtk-standard-shader/MRTK_MeshOutline.jpg" width="900" alt="Mesh Outline">

[`MeshOutline.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutline) 및 는 [`MeshOutlineHierarchy.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshOutlineHierarchy) 메시 렌더러 주위에 윤곽선을 렌더링하는 데 사용할 수 있습니다. 이 구성 요소를 사용하도록 설정하면 설명되는 개체의 추가 렌더링 패스가 도입되지만 모바일 Mixed Reality 디바이스에서 효과적으로 실행되도록 설계되었으며 사후 프로세스를 활용하지 않습니다. 이 효과의 제한 사항으로는 watertight가 아니거나 양면에 필요한 개체에서 잘 작동하지 않고 겹치는 개체에서 깊이 정렬 문제가 발생할 수 있습니다.

개요 동작은 MRTK/표준 셰이더와 함께 사용되도록 설계되었습니다. 윤곽 재질은 일반적으로 단색이 아닌 색이지만 광범위한 효과를 달성하도록 구성할 수 있습니다. 개요 자료의 기본 구성은 다음과 같습니다.

<img src="../images/mrtk-standard-shader/MRTK_OutlineMaterial.jpg" width="450" alt="Mesh Outline Material">

1. 깊이 쓰기 - 윤곽선 재질이 다른 개체의 렌더링을 방해하지 않도록 하려면 윤곽 재질에 대해 사용하지 않도록 설정해야 합니다.
2. 꼭짓점 돌출 - 윤곽선을 렌더링하려면 사용하도록 설정해야 합니다.
3. 부드러운 보통 사용 - 이 설정은 일부 메시에 대해 선택 사항입니다. 꼭짓점 정상을 따라 꼭짓점을 이동하면 돌출이 발생합니다. 기본 표준에 따라 돌출된 일부 메시에서는 윤곽선에서 불연속성이 발생합니다. 이러한 불연속성을 해결하려면 이 확인란을 선택하면 에 의해 생성되는 다른 평활화 표준 집합을 사용할 수 있습니다. [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother)

[`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 는 메시에서 평활화된 보통을 자동으로 생성하는 데 사용할 수 있는 구성 요소입니다. 이 메서드는 공간에서 동일한 위치를 공유하는 메시의 꼭짓점을 그룹화한 다음 해당 꼭짓점의 법선 평균을 지정합니다. 이 프로세스는 기본 메시의 복사본을 만들고 필요한 경우에만 사용해야 합니다.

<img src="../images/mrtk-standard-shader/MRTK_SmoothNormals.jpg" width="450" alt="Smooth Normals Outline">

1. 을 통해 생성된 부드러운 [`MeshSmoother.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.MeshSmoother) 표준입니다.
2. 사용되는 기본 정규식은 큐브 모서리 주위의 아티팩트입니다.

### <a name="stencil-testing"></a>스텐실 테스트

다양한 효과를 얻기 위해 구성 가능한 스텐실 테스트 지원을 기본 제공합니다. 포털과 같은 경우:

![스텐실 테스트](../images/mrtk-standard-shader/MRTK_StencilTest.gif)

### <a name="instanced-color-support"></a>인스턴스 색 지원

수천 개의 GPU 인스턴스 메시에 고유한 재질 속성을 제공하는 인스턴스화 색 지원:

![instanced 속성](../images/mrtk-standard-shader/MRTK_InstancedProperties.gif)

### <a name="triplanar-mapping"></a>Triplanar 매핑

삼중자 매핑은 프로그래밍 방식으로 메시를 질감하는 기술입니다. 지형, VS가 없는 메시 또는 도형 래프 해제가 어려운 경우 자주 사용됩니다. 이 구현은 세계 또는 로컬 공간 프로젝션, 혼합 다듬기 사양 및 일반 지도 지원을 지원합니다. 사용된 각 질감에는 3개의 질감 샘플이 필요하므로 성능이 중요한 상황에서는 거의 사용하지 않습니다.

![triplanar](../images/mrtk-standard-shader/MRTK_TriplanarMapping.gif)

### <a name="vertex-extrusion"></a>꼭짓점 돌출

세계 공간의 꼭짓점 돌출. 돌출된 경계 볼륨 또는 메시 내/외부 전환을 시각화하는 데 유용합니다.

![법선 지도 눈금 1](../images/mrtk-standard-shader/MRTK_VertexExtrusion.gif)

### <a name="miscellaneous"></a>기타

Albedo 최적화를 제어 하는 확인란입니다. 최적화 albedo 질감이 지정 되지 않은 경우 최적화를 사용할 수 없습니다. 이는 [원격 질감 로드](http://dotnetbyexample.blogspot.com/2018/10/workaround-remote-texture-loading-does.html)를 제어 하는 데 유용 합니다.

이 확인란을 선택 하면 됩니다.

![albedo 할당](../images/mrtk-standard-shader/MRTK_AlbedoAssignment.jpg)

픽셀 클리핑 질감, 로컬 가장자리 기반 앤티 앨리어싱 및 법선 지도 배율이 지원 됩니다.

![기본 지도 배율 2](../images/mrtk-standard-shader/MRTK_NormalMapScale.gif)

## <a name="see-also"></a>참고 항목

* [상호 작용 가능](../ux-building-blocks/interactable.md)
* [가리키기 라이트](hover-light.md)
* [근접 조명](proximity-light.md)
* [기본 클리핑](clipping-primitive.md)
