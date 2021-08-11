---
title: Unity의 텍스트
description: Unity에서 텍스트를 표시하기 위해 사용할 수 있는 텍스트 구성 요소에는 UI 텍스트와 3D 텍스트 메시의 두 가지 유형이 있습니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 컨트롤, 글꼴, 입력 체계, ui, ux, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 3e5f296e9526e62bde7d03a0fee7847f4664e4a67187fcda1e66e22aa03053b4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207975"
---
# <a name="text-in-unity"></a>Unity의 텍스트

텍스트는 홀로그램 앱에서 가장 중요한 구성 요소 중 하나입니다. Unity에서 텍스트를 표시하기 위해 UI 텍스트, 3D 텍스트 메시 및 텍스트 메시 Pro 세 가지 유형의 텍스트 구성 요소를 사용할 수 있습니다. 기본적으로 UI 텍스트 및 3D 텍스트 메시는 흐리게 표시되고 너무 큽니다. 몇 가지 변수를 변경하면 관리가 용이한 크기로 더 선명하고 품질이 높은 텍스트가 HoloLens. UI 텍스트 및 3D 텍스트 메시 구성 요소를 사용할 때 크기 조정 요소를 적용하여 적절한 차원을 가져오면 렌더링 품질을 향상할 수 있습니다.

![선명하고 멋진 텍스트를 얻는 방법](images/hug-text-02-640px.png)<br>
*Unity의 흐린 기본 텍스트*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>Unity의 3D 텍스트(텍스트 메시) 및 UI 텍스트 작업

Unity는 장면에 추가된 모든 새 요소가 하나의 Unity 단위 크기 또는 100% 변환 배율이라고 가정합니다. 하나의 Unity 단위는 HoloLens 약 1미터로 변환됩니다. 글꼴의 경우 3D TextMesh에 대한 경계 상자는 기본적으로 약 1미터 높이로 제공됩니다.

![Unity에서 글꼴 작업](images/640px-hug-text-03.png)<br>
*기본 Unity 3D 텍스트(텍스트 메시)는 하나의 Unity 단위(1미터)를 차지합니다.*

<br>

대부분의 비주얼 디자이너는 점을 사용하여 실제 세계에서 글꼴 크기를 정의합니다. 1미터에는 약 2835(2,834.645666399962)의 지점이 있습니다. 포인트 시스템을 1미터로 변환하고 Unity의 기본 텍스트 메시 글꼴 크기 13을 2835로 나눈 간단한 수학은 0.0046(정확히 0.004586111116)과 같습니다(일부는 0.005로 반올림할 수 있음). 텍스트 개체 또는 컨테이너를 이러한 값으로 확장하면 디자인 프로그램에서 글꼴 크기를 1:1로 변환할 수 있을 뿐만 아니라 환경 전체에서 일관성을 유지할 수 있도록 표준을 제공합니다.

![Unity 3D 텍스트 및 UI 텍스트에 대한 값 크기 조정](images/Text_In_Unity_Measurements1.png)<br>
*Unity 3D 텍스트 및 UI 텍스트에 대한 값 크기 조정*

<br>

![최적화된 값을 가진 Unity 3D 텍스트 메시](images/hug-text-05-1000px.png)<br>
*최적화된 값을 가진 Unity 3D 텍스트 메시*

<br>

장면에 UI 또는 캔버스 기반 텍스트 요소를 추가할 때 크기 차이는 여전히 더 커야 합니다. 두 크기의 차이는 약 1000%이며, UI 기반 텍스트 구성 요소의 배율 비율은 0.00046(0.0004586111116)으로, 반올림된 값의 경우 0.0005입니다.

![최적화된 값을 가진 Unity UI 텍스트](images/hug-text-04-1000px.png)<br>
*최적화된 값을 가진 Unity UI 텍스트*

<br>

>[!NOTE]
>모든 글꼴의 기본값은 해당 글꼴의 질감 크기 또는 글꼴을 Unity로 가져온 방법에 의해 영향을 받을 수 있습니다. 이러한 테스트는 Unity의 기본 Arial 글꼴뿐만 아니라 가져온 다른 글꼴을 기반으로 수행되었습니다.

## <a name="working-with-text-mesh-pro"></a>텍스트 메시 Pro 작업

Unity의 Text Mesh Pro 사용하면 텍스트 렌더링 품질을 보호할 수 있습니다. [SDF(Signed Distance Field)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) 기술을 사용하여 거리에 관계없이 간결한 텍스트 윤곽선을 지원합니다. 위에서 3D 텍스트 메시 및 UI 텍스트에 사용한 것과 동일한 계산 방법을 사용하여 기존 입력 지점과 함께 사용할 적절한 크기 조정 값을 찾을 수 있습니다. 크기가 36인 기본 3D 텍스트 메시 Pro 글꼴의 경계 크기는 2.5 Unity 단위(2.5m)이므로 크기 조정 값 0.005를 사용하여 점 크기를 얻을 수 있습니다. UI 메뉴 아래의 텍스트 메시 Pro 기본 경계 크기는 25 Unity 단위(25m)입니다. 크기 조정 값에 대해 0.0005를 제공합니다.

![Unity 3D 텍스트 및 UI에 대한 값 크기 조정](images/Text_In_Unity_Measurements2.png)<br>
*Unity 3D 텍스트 및 UI에 대한 값 크기 조정*

## <a name="recommended-text-size"></a>권장 텍스트 크기

예상할 수 있듯이 PC 또는 태블릿 디바이스에서 사용하는 형식 크기(일반적으로 12~32pt 사이)는 2미터의 거리만큼 작게 보입니다. 각 글꼴의 특성에 따라 달라지지만 일반적으로 권장되는 최소 보기 각도와 가독성을 위한 글꼴 높이는 사용자 연구 연구를 기반으로 약 0.35°-0.4°/12.21-13.97mm입니다. 위에서 도입된 배율 비율은 약 35-40pt입니다.

0.45m(45cm)에서 가까운 상호 작용의 경우 읽을 수 있는 최소 글꼴의 보기 각도와 높이는 0.4°-0.5° / 3.14-3.9mm입니다. 위에서 도입된 크기 조정 계수가 있는 약 9-12pt입니다.

![근거리 및 원거리 상호 작용 범위 ](images/typography-distance-1000px.jpg)
 *근거리 및 원거리 상호 작용 범위의 콘텐츠*

### <a name="the-minimum-legible-font-size"></a>읽을 수 있는 최소 글꼴 크기

| 거리 | 시야각 | 텍스트 높이 | 글꼴 크기 |
|---------|---------|---------|---------|
| 45cm(직접 조작 거리) | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2m | 0.35°-0.4° | 12.21–13.97mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>읽을 수 있는 편안하게 읽을 수 있는 글꼴 크기

| 거리 | 시야각 | 텍스트 높이 | 글꼴 크기 |
|---------|---------|---------|---------|
| 45cm(직접 조작 거리) | 0.65°-0.8° | 5.1-6.3mm | 14.47-17.8pt |
| 2m | 0.6°-0.75° | 20.9-26.2mm | 59.4-74.2 pt |

맑은 고딕(Windows 기본 글꼴)는 대부분의 경우 잘 작동합니다. 그러나 씬 세로 스트로크가 진동하고 가독성이 저하되므로 작은 크기의 밝은 글꼴 또는 반광 글꼴 패밀리를 사용하지 마십시오. 스트로크 두께가 충분한 최신 글꼴이 잘 작동합니다. 예를 들어 Helvetica 및 Arial은 일반 또는 굵은 가중치로 HoloLens 읽을 수 있습니다.

![보기 각도 ](images/Text_In_Unity_ViewingAngle.jpg)
 *보기 거리, 각도 및 텍스트 높이*

## <a name="text-with-mixed-reality-toolkit-v2"></a>Mixed Reality Toolkit v2가 있는 텍스트

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>적절한 차원의 선명한 텍스트 렌더링 품질

이러한 크기 조정 요인에 따라 [UI 텍스트 및 3D 텍스트 메시가 있는 텍스트 프리팹을](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)만들었습니다. 개발자는 이러한 프리팹을 사용하여 선명하고 일관된 글꼴 크기를 얻을 수 있습니다.

![적절한 차원의 선명한 텍스트 렌더링 품질](images/hug-text-06-1000px.png)<br>
*적절한 차원의 선명한 텍스트 렌더링 품질*

### <a name="shader-with-occlusion-support"></a>폐색이 지원된 셰이더

Unity의 기본 글꼴 재질은 폐색을 지원하지 않습니다. 이 때문에 기본적으로 개체 뒤에 텍스트가 표시됩니다. 폐색 을 지원하는 간단한 [셰이더를 포함했습니다.](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader) 아래 이미지는 기본 글꼴 재질(왼쪽)이 있는 텍스트와 적절한 폐색이 있는 텍스트(오른쪽)를 보여줍니다.

![폐색이 지원된 셰이더](images/hug-text-07-1000px.png)<br>
*폐색이 지원된 셰이더*

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unity 개발 여정을 따라가는 경우 MRTK 핵심 구성 요소에 대해 알아보세요. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [음성 입력 ](voice-input-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목

* [MRTK의 텍스트 프리팹](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [입력 체계](../../design/typography.md)
