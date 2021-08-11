---
title: 집에서 사용할 3D 모델 만들기
description: HoloLens 몰입형(VR) 헤드셋의 Windows Mixed Reality 홈에 사용되는 3D 모델에 대한 자산 요구 사항 및 제작 지침입니다.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, 모델링, 모델링 지침, 자산 요구 사항, 제작 지침, 시작 관리자, 3D 시작 관리자, 질감, 재질, 복잡성, 삼각형, 메시, 다각형, 다각형, 다각형, 제한, 혼합 현실 헤드셋, Windows 혼합 현실 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 9fdd485c67a757d40b049c08f114ce9982aafc27e9103c4b31c21fd8af08d186
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207683"
---
# <a name="create-3d-models-for-use-in-the-home"></a>집에서 사용할 3D 모델 만들기

[Windows Mixed Reality 홈은](../discover/navigating-the-windows-mixed-reality-home.md) 애플리케이션을 시작하기 전에 사용자가 시작하는 시작점입니다. Windows Mixed Reality 헤드셋용 애플리케이션을 디자인할 때 앱 [시작 관리자로 3D 모델을](implementing-3d-app-launchers.md) 사용하고 [Windows Mixed Reality 홈 에 3D 딥 링크를](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles)배치합니다. 이 문서에서는 Windows Mixed Reality 홈과 호환되는 3D 모델을 만들기 위한 지침을 간략하게 설명합니다.

## <a name="asset-requirements-overview"></a>자산 요구 사항 개요

Windows Mixed Reality 대한 3D 모델을 만들 때 모든 자산이 충족해야 하는 몇 가지 요구 사항이 있습니다. 
1. [내보내기](#exporting-models) - 자산을 .glb 파일 형식(binary glTF)으로 전달해야 합니다.
2. [모델링](#modeling-guidelines) - 자산은 10,000개 미만의 삼각형이어야 하며, LOD당 64개 이하의 노드와 32개의 하위 캐시가 있어야 합니다.
3. [재질](#material-guidelines) - 질감은 4096 x 4096보다 클 수 없으며, 가장 작은 MIP 맵은 어느 차원에서든 4보다 크지 않아야 합니다.
4. [애니메이션](#animation-guidelines) - 애니메이션은 30 FPS(36,000개의 키 프레임)에서 20분 이상일 수 없으며, <= 8192모프 대상 꼭짓점을 포함해야 합니다.
5. [최적화](#optimizations) - [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases)를 사용하여 자산을 최적화해야 합니다. *Windows OS 버전 <필요 = 1709** 및 Windows OS 버전 >권장 = 1803

이 문서의 나머지 부분에는 이러한 요구 사항에 대한 자세한 개요와 모델이 Windows Mixed Reality 홈과 잘 작동하도록 하는 추가 지침이 포함되어 있습니다. 

## <a name="detailed-guidance"></a>자세한 지침

### <a name="exporting-models"></a>모델 내보내기

Windows Mixed Reality 홈에는 포함된 이미지 및 이진 데이터와 함께 .glb 파일 형식을 사용하여 3D 자산이 전달되어야 합니다. Glb는 glTF 형식의 이진 버전으로, Khronos 그룹에서 유지 관리하는 3D 자산 배달을 위한 무료 개방형 표준입니다. glTF는 상호 운용 가능한 3D 콘텐츠에 대한 업계 표준으로 발전함에 따라 microsoft는 Windows 앱 및 환경의 형식을 지원합니다. glTF 자산을 만들지 않은 경우 glTF 작업 그룹 github 페이지에서 [지원되는 내보내기 및 변환기 목록을](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) 찾을 수 있습니다.  

### <a name="modeling-guidelines"></a>모델링 지침

Windows Mixed Reality 홈 환경과의 호환성을 보장하기 위해 다음 모델링 지침을 사용하여 자산이 생성될 것으로 예상합니다. 선택한 프로그램에서 모델링할 때는 다음과 같은 권장 사항 및 제한 사항에 유의하세요.
1. Up 축은 "Y"로 설정해야 합니다.
2. 자산은 양의 Z 축을 "앞으로" 향해야 합니다.
3. 모든 자산은 장면 원점(0,0,0)의 접지 평면에 빌드되어야 합니다.
4. 전 세계에서 자산을 작성할 수 있도록 작업 단위를 미터 및 자산으로 설정해야 합니다.
5. 모든 메시를 결합할 필요는 없지만 리소스가 제한된 디바이스를 대상으로 하는 경우 권장됩니다.
6. 모든 메시는 하나의 재질을 공유해야 하며, 하나의 질감 집합만 전체 자산에 사용됩니다.
7. IV는 0-1 공간에서 정사각형 배열로 배치해야 합니다. 텍스처는 허용되지만 바둑판식 배열을 사용하지 마십시오.
8. 다중 IV는 지원되지 않습니다.
9. 양면 재질은 지원되지 않습니다.

### <a name="triangle-counts-and-levels-of-detail-lods"></a>삼각형 개수 및 세부 정보 수준(LOD)

Windows Mixed Reality 홈은 삼각형이 10,000개 이상인 모델을 지원하지 않습니다. 이 수를 초과하지 않도록 내보내기 전에 메시를 삼각측하는 것이 좋습니다. Windows 또한 MR는 고성능 및 고품질 환경을 보장하기 위해 선택적 LOD(기하 도형 수준의 세부 정보)를 지원합니다. [WindowsMRAssetConverter를](https://github.com/Microsoft/glTF-Toolkit/releases) 사용하면 3가지 버전의 모델을 단일 .glb 모델로 결합할 수 있습니다. Windows 모델이 차지하는 화면 부동산의 양에 따라 표시할 LOD를 결정합니다. 다음과 같은 권장 삼각형 개수로 3개의 LOD 수준만 지원됩니다.
<br>

|  LOD 수준  |  권장 삼각형 수  |  최대 삼각형 수 | 
|------|------|------|
|  LOD 0 |  10000 |  10000 | 
|  LOD 1 |  5,000  |  10000 | 
|  LOD 2 |  2,500  |  10000 | 

### <a name="node-counts-and-submesh-limits"></a>노드 수 및 하위 새로 고시 제한

Windows Mixed Reality 홈은 LOD당 64개 이상의 노드 또는 32개의 하위 캐시가 있는 모델을 지원하지 않습니다. 노드는 장면의 개체를 정의하는 [glTF 사양의](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) 개념입니다. 서브메시는 개체의 메시에 있는 [기본형](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) 배열에 정의됩니다. 

|  기능 |  Description  |  지원되는 최대값 | 설명서 |
|------|------|------|------|
|  노드 |  glTF 장면의 개체 |  LOD당 64 | [여기](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  하위메시 |  모든 메시의 기본형 합계 |  LOD당 32 | [여기](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>자료 지침

질감은 PBR 금속 대략성 워크플로를 사용하여 준비해야 합니다. 먼저 Albedo, Normal, Occlusion, Texture 및 Roughness를 비롯한 전체 질감 집합을 만듭니다. Windows Mixed Reality 해상도가 최대 4096x4096인 질감을 지원하지만 512x512에서 제작하는 것이 좋습니다. 질감은 해상도가 4의 배수로 작성되어야 합니다. 이는 아래에 설명된 내보내기 단계에서 질감에 적용되는 압축 형식에 대한 요구 사항입니다. MIP 맵 또는 질감을 생성할 때 가장 낮은 MIP는 최대 4x4여야 합니다.
<br>

|  권장되는 질감 크기  |  최대 질감 크기 | 가장 낮은 MIP
|----|----|----|
|  512x512  |  4096x4096 | 최대 4x4|

### <a name="albedo-base-color-map"></a>Albedo(기본 색) 지도

조명 정보가 없는 원시 색입니다. 또한 이 지도에는 각각 금속(금속 지도의 흰색) 및 단조기(금속 지도의 검은색) 표면에 대한 반사 및 확산 정보가 포함되어 있습니다.

### <a name="normal"></a>보통

탄젠트 공간 표준 지도

### <a name="roughness-map"></a>대략성 맵

개체의 마이크로 서체를 설명합니다. 흰색 1.0은 대략적인 검은색 0.0은 매끄럽습니다. 이 맵은 표면을 실제로 설명하기 때문에 자산에 가장 많은 문자를 제공합니다. 예를 들어 스크래치, 지문, 번거로움, 스크래치 등이 있습니다.

### <a name="ambient-occlusion-map"></a>주변 폐색 맵

반사를 차단하는 폐색 광원 영역을 보여주는 값 배율 맵

### <a name="metallic-map"></a>금속 지도

금속인지 여부를 셰이더에 알릴 수 있습니다. 원시 금속 = 1.0 흰색 비금속 = 0.0 검정. 원시 금속을 덮고 있는 것을 나타내는 전환 회색 값이 있을 수 있지만 일반적으로 이 지도는 검은색과 흰색이어야 합니다.

## <a name="optimizations"></a>최적화

Windows Mixed Reality 홈은 사용자 지정 확장 프로그램을 사용 하 여 정의 된 핵심 글 글을 기반으로 하는 일련의 최적화를 제공 합니다. 이러한 최적화는 Windows 버전 <= 1709에 필요 하며 최신 버전의 Windows에 권장 됩니다. [GitHub에서 사용할 수 있는 Windows Mixed Reality 자산 변환기](https://github.com/Microsoft/glTF-Toolkit/releases)를 사용 하 여 모든 인 글 tf 2.0 모델을 쉽게 최적화할 수 있습니다. 이 도구는 아래 지정 된 대로 올바른 질감 압축 및 최적화를 수행 합니다. 일반적인 사용을 위해 WindowsMRAssetConverter를 사용 하는 것이 좋습니다. 그러나 환경을 보다 세부적으로 제어 해야 하 고 사용자 고유의 최적화 파이프라인을 빌드 하려는 경우 아래 상세 사양을 참조할 수 있습니다.  

> [!NOTE]
> 정확한 모델 제한의 가능성을 명확 하 게 확인 하려면 Dynamics 365 응용 프로그램에서 사용할 수 있는 [3d 모델 최적화](/dynamics365/mixed-reality/guides/3d-content-guidelines/optimize-models) 문서를 참조 하세요.

### <a name="materials"></a>재질

혼합 현실 환경에서 자산 로드 시간을 개선 하기 위해 MR Windows이 섹션에 정의 된 질감 압축 체계에 따라 압축 된 DDS 질감 렌더링을 지원 합니다. DDS 질감이 [MSFT_texture_dds 확장](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)을 사용 하 여 참조 됩니다. 텍스처를 압축 하는 것이 좋습니다. 

#### <a name="hololens"></a>HoloLens

HoloLens 기반 혼합 현실에서는 다음 압축 사양을 사용 하 여 2 질감 설정을 사용 하 여 질감이 압축 될 것으로 간주 됩니다.
<br>

|  인 글 Tf 속성  |  질감  |  압축 체계 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  빨강 (R), 녹색 (G), 파랑 (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  보통 (RG), 황삭 (B), 금속 (A) | 


DDS 텍스처를 압축 하는 경우 각 맵에 다음과 같은 압축이 필요 합니다.
<br>

|  질감  |  예상 압축 | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>모던 (VR) 헤드셋

모던 (VR) 헤드셋을 위한 PC 기반 Windows Mixed Reality 환경에서는 다음 압축 사양을 사용 하 여 3 질감 설정을 사용 하 여 질감을 압축할 것으로 간주 합니다.

##### <a name="windows-os--1803"></a>Windows OS >= 1803

<br>

|  인 글 Tf 속성  |  질감  |  압축 체계 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  빨강 (R), 녹색 (G), 파랑 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  폐색 (R), 황삭 (G), 금속 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  보통 (RG) | 

DDS 텍스처를 압축 하는 경우 각 맵에 다음과 같은 압축이 필요 합니다.
<br>

|  질감  |  예상 압축 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS <= 1709
<br>

|  인 글 Tf 속성  |  질감  |  압축 체계 | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  빨강 (R), 녹색 (G), 파랑 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  황삭 (R), 금속 (G), 폐색 (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  보통 (RG) | 

DDS 텍스처를 압축 하는 경우 각 맵에 다음과 같은 압축이 필요 합니다.
<br>

|  질감  |  예상 압축 | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>메시 LODs 추가

Windows MR은 화면 검사에 따라 geometry 노드 LODs를 사용 하 여 다양 한 수준의 세부 정보로 3D 모델을 렌더링 합니다. 이 기능은 기술적으로 필수는 아니지만 모든 자산에 권장 됩니다. 현재 Windows은 3 가지 세부 수준을 지원 합니다. 기본 LOD는 최고 품질을 나타내는 0입니다. 다른 LODs는 순차적으로 번호가 매겨집니다 (예: 1, 2, 점진적으로 품질이 낮아집니다. [Windows Mixed Reality Asset Converter](https://github.com/Microsoft/glTF-Toolkit/releases) 는 여러 가지 영향을 받는 tf 모델을 수락 하 고 유효한 LOD 수준의 단일 자산에 병합 하 여이 LOD 사양을 충족 하는 자산 생성을 지원 합니다. 다음 표에서는 예상 되는 LOD 순서 지정 및 삼각형 대상에 대해 간략하게 설명 합니다.
<br>

|  LOD 수준  |  권장 삼각형 수  |  최대 삼각형 수 | 
|-------|-------|-------|
|  LOD 0 |  10000 |  10000 | 
|  LOD 1 |  5,000  |  10000 | 
|  LOD 2 |  2,500  |  10000 | 

LODs를 사용 하는 경우 항상 3 LOD 수준을 지정 합니다. LOD 시스템이 누락 된 LOD 수준으로 전환 될 때 LODs가 누락 되 면 모델이 예기치 않게 렌더링 되지 않습니다. 이 글 Tf 2.0은 현재 핵심 사양의 일부로 LODs를 지원 하지 않습니다. [MSFT_LOD 확장](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)을 사용 하 여 lods를 정의 해야 합니다.

### <a name="screen-coverage"></a>화면 검사

lods는 각 LOD에 설정 된 화면 범위 값으로 구동 되는 시스템에 따라 Windows Mixed Reality에 표시 됩니다. 현재 화면 공간을 더 많이 사용 하는 개체는 더 높은 LOD 수준에 표시 됩니다. 화면 범위는 핵심 글 조각 2.0 사양의 일부가 아니며 [MSFT_lod 확장](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)의 "추가 기능" 섹션에 MSFT_ScreenCoverage를 사용 하 여 지정 해야 합니다.
<br>

|  LOD 수준  |  권장 범위  |  기본 범위 | 
|-------|-------|-------|
|  LOD 0  |  100%-50% |  0.5 | 
|  LOD 1 |  50%-20% 미만  |  0.2 | 
|  LOD 2 |  20%-1% 미만  |  0.01 | 
|  LOD 4  |  1% 미만  |  - | 

## <a name="animation-guidelines"></a>애니메이션 지침

> [!NOTE]
> 이 기능은 [Windows 10 4 월 2018 업데이트](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)의 일부로 추가 되었습니다. 이전 버전의 Windows에서는 이러한 애니메이션이 재생 되지 않지만이 문서의 지침에 따라 작성 된 경우에도 로드 됩니다.  

혼합 현실 홈은 HoloLens 및 모던 (VR) 헤드셋에서 애니메이션 된 글 글을 지 원하는 tf 개체를 지원 합니다. 모델에 대 한 애니메이션을 트리거하려면 애니메이션 맵 확장을 지 원하는 Tf 형식으로 사용 해야 합니다. 이 확장을 사용 하면 전 세계 사용자의 현재 상태를 기반으로 하 여 인 사이트에서 애니메이션을 트리거할 수 있습니다. 예를 들어 사용자가 개체에 가까이 있거나 보고 있는 동안 애니메이션을 트리거할 수 있습니다. Tf 개체에 애니메이션이 있지만 트리거를 정의 하지 않으면 애니메이션이 재생 되지 않습니다. 다음 섹션에서는 이러한 트리거를 애니메이션 된 모든 개체에 추가 하는 한 가지 워크플로를 설명 합니다.

### <a name="tools"></a>도구

먼저, 다음 도구가 아직 없는 경우 다운로드 합니다. 이러한 도구를 사용 하면 쉽게 모든 프로그램을 열고, 미리 보고, 변경 하 고,
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [Visual Studio Code에 대 한 글 서 용 Tf 도구](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>모델 열기 및 미리 보기

먼저 파일을 편집기 창으로 끌어 VSCode에서 글 글 Tf 모델을 엽니다. ..Bf 파일이 아닌 경우 다운로드 한 글 어 도구 추가 기능을 사용 하 여 VSCode로 가져올 수 있습니다. "보기-> 명령 팔레트"로 이동 하 여 명령 팔레트에 "글 제 tf"를 입력 하 고 "& #에서 가져오기"를 선택 합니다. 그러면에 대 한 파일 선택이 표시 됩니다. 

사용자가 만든 Tf 모델을 열면 편집기 창에 JSON이 표시 됩니다. 파일 이름을 마우스 오른쪽 단추로 클릭 하 고 오른쪽 클릭 메뉴에서 "영향을 주는" 3D 모델 미리 보기 "명령 바로 가기를 선택 하 여 라이브 3D 뷰어에서 모델을 미리 볼 수도 있습니다. 

### <a name="adding-the-triggers"></a>트리거 추가

애니메이션 트리거는 애니메이션 맵 확장을 사용 하 여 글 지 Tf 모델 JSON에 추가 됩니다. 애니메이션 맵 확장은 [GitHub에서](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) 공개적으로 설명 됩니다 (참고: 초안 확장). 모델에 확장을 추가 하려면 편집기에서 인 글 Tf 파일의 끝으로 스크롤하고 "extensionsUsed" 및 "extensions" 블록을 파일에 추가 합니다 (아직 없는 경우). "ExtensionsUsed" 섹션에서는 "EXT_animation_map" 확장에 대 한 참조를 추가 하 고 "확장" 블록에 모델의 애니메이션에 대 한 매핑을 추가 합니다.

[사양에 설명 된](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) 것 처럼 애니메이션 인덱스의 배열인 "애니메이션" 목록에서 "의미 체계" 문자열을 사용 하 여 애니메이션을 트리거하는 항목을 정의 합니다. 아래 예제에서는 사용자가 개체에서 gazing 때 애니메이션을 재생 하도록 지정 했습니다.

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
다음 애니메이션 트리거 의미 체계가 Windows Mixed Reality 홈에서 지원 됩니다.  
* "ALWAYS": 애니메이션을 지속적으로 반복 합니다.
* "보유": 전체 기간 동안 반복 되는 개체는 grabbed입니다.
* "응시": 개체를 조회 하는 동안 반복 됩니다.
* "근접": 뷰어가 개체 근처에 있는 동안 반복 됩니다.
* "가리키기": 사용자가 개체를 가리키는 동안 반복 됩니다.

### <a name="saving-and-exporting"></a>저장 및 내보내기

인 글 어 어 모델을 변경한 후에는이를 직접 인 트 Tf로 저장할 수 있습니다. 편집기에서 파일의 이름을 마우스 오른쪽 단추로 클릭 하 고 "& f): & # (이진 파일)로 내보내기"를 선택 하 여 .bb를 내보낼 수도 있습니다. 

### <a name="restrictions"></a>제한

애니메이션은 20 분 보다 길 수 없으며 36000 개 보다 많은 키 프레임을 포함할 수 없습니다 (20 분 (30FPS)). 또한 모핑 대상 기반 애니메이션을 사용 하는 경우 8192 모핑 대상 꼭 짓 점 수를 초과 하지 않습니다. 이러한 횟수를 초과 하면 Windows Mixed Reality 홈에서 애니메이션 자산이 지원 되지 않습니다. 

|기능|최대|
|-----|-----|
|Duration|20분|
|키 프레임|36,000| 
|모핑 대상 꼭 짓 점|8192|

## <a name="gltf-implementation-notes"></a>글 서 Tf 구현 참고 사항

Windows MR은 음수 눈금을 사용 하 여 기 하 도형 이동을 지원 하지 않습니다. 배율이 음수인 기 하 도형은 시각적 아티팩트가 될 가능성이 높습니다.

인 글 tf 자산은 Windows MR에서 렌더링 되는 장면 특성을 사용 하 여 기본 장면을 가리켜야 합니다. Windows 또한 [Windows 10 4 월 2018 업데이트](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018) 에는 접근자 **가 필요** 합니다.
* Min 및 max 값이 있어야 합니다.
* 스칼라 형식은 componentType UNSIGNED_SHORT (5123) 또는 UNSIGNED_INT (5125) 여야 합니다.
* VEC2 및 VEC3 형식은 componentType FLOAT 여야 합니다 (5126).

다음 재질 속성은 core로 된 Tf 2.0 사양에서 사용 되지만 반드시 필요한 것은 아닙니다.
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture: dds에 저장 된 질감을 가리켜야 합니다.
* emissiveTexture: dds에 저장 된 질감을 가리켜야 합니다.
* emissiveFactor
* alphaMode

다음 재질 속성은 코어 사양에서 무시 됩니다.
* 모든 다중 UVs
* metalRoughnessTexture: 아래에 정의 된 Microsoft 최적화 된 텍스처 압축을 대신 사용 해야 합니다.
* normalTexture: 아래에 정의 된 Microsoft 최적화 된 질감 압축을 대신 사용 해야 합니다.
* normalScale
* occlusionTexture: 아래에 정의 된 Microsoft 최적화 된 텍스처 압축을 대신 사용 해야 합니다.
* occlusionStrength

Windows MR은 기본 모드 선 및 요소를 지원 하지 않습니다. 

단일 UV vertex 특성만 지원 됩니다.

## <a name="more-resources"></a>추가 리소스

* [글 내보내기 및 변환기](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [글 Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [글 Tf 2.0 사양](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft 글 Tf LOD 확장 사양](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [PC 혼합 현실 질감 압축 확장 사양](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens 혼합 현실 질감 압축 확장 사양](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS 질감 및 Tf 확장 사양](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>추가 정보

* [3D 앱 시작 관리자(UWP 앱) 구현](implementing-3d-app-launchers.md)
* [3D 앱 시작 관리자(Win32 앱) 구현](implementing-3d-app-launchers-win32.md)
* [Windows Mixed Reality 홈 탐색](../discover/navigating-the-windows-mixed-reality-home.md)