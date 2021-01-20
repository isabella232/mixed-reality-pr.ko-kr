---
title: Unreal의 재질 권장 사항
description: Unreal engine의 재질 개요.
author: hferrone
ms.author: safarooq
ms.date: 09/18/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 개발, 자료, 설명서, 가이드, 기능, holograms, 게임 개발, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: bfe70e730c5fbd6e5d103737b03e76bfd0ab65f6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580794"
---
# <a name="material-recommendations-in-unreal"></a>Unreal의 재질 권장 사항

사용 하는 자료는 Unreal Engine에서 프로젝트가 얼마나 잘 실행 될 지에 직접적으로 영향을 줄 수 있습니다. 이 페이지는 혼합 현실 응용 프로그램에서 최상의 성능을 얻기 위해 사용 해야 하는 기본 설정에 대 한 빠른 시작 역할을 합니다.

## <a name="using-customizeduvs"></a>CustomizedUVs 사용

재질에 UV 바둑판식 배열을 제공 해야 하는 경우 텍스처 노드의 UV를 직접 수정 하는 대신 CustomizedUVs를 사용 합니다. CustomizedUVs를 사용 하면 픽셀 셰이더가 아닌 꼭 짓 점 셰이더에서 UVs를 조작할 수 있습니다.

![진짜의 재질 설정](images/unreal-materials-img-01c.png)

다음 스크린샷에서 [Unreal Engine 설명서](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) 및 모범 사례 예제에서 자료 정보를 찾을 수 있습니다.

[ ![ 실제 ](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox) 
 *권장 자료* 설정의 권장 자료 설정

실제 권장 되지 않는 재질 설정 [ ![ 의 권장 되지 않는 재질 설정 ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 

## <a name="changing-blend-mode"></a>Blend 모드 변경

그렇지 않은 경우에는 강한 이유가 없으면 blend 모드를 불투명 모드로 설정 하는 것이 좋습니다. 마스킹된 및 반투명 자료는 느립니다. 자료에 대 한 자세한 내용은 [Unreal Engine 설명서](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)에서 확인할 수 있습니다.

![Blend 모드 변경](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a>모바일에 대 한 조명 업데이트

전체 전체 자릿수가 꺼져 있어야 합니다. 방향 정보를 켜서 Lightmap 조명을 종료할 수 있습니다. 이 기능을 사용 하지 않도록 설정 하면 lightmaps의 조명이 평면 이지만 비용이 저렴 합니다.

![Unreal의 모바일 재질 설정](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a>전방 음영 조정

이러한 옵션은 성능 비용으로 시각적 충실도를 향상 시킵니다. 최대 성능을 위해 해제 해야 합니다.

![Unreal의 전방 음영 재질 설정](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a>재질 반투명도 설정

블 룸 또는 DOF의 반투명 재질에 영향을 주지 않음을 나타냅니다. MR에서는 이러한 효과가 거의 없기 때문에이 설정은 기본적으로 설정 되어 있어야 합니다.

![Unreal의 모바일 개별 반투명도 설정](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a>선택적 설정

다음 설정을 사용 하면 성능이 향상 될 수 있지만 특정 기능을 사용할 수 없습니다. 해당 기능이 필요하지 않는 경우에만 이 설정을 사용하세요.

![Unreal의 선택적 재질 설정](images/unreal-materials-img-06.jpg)

재질에 반사 또는 빛이 필요 하지 않은 경우이 옵션을 설정 하면 성능이 크게 향상 될 수 있습니다. 내부 테스트에서 조명 정보를 제공 하는 동안 "unlit" 만큼 빠릅니다.

## <a name="best-practices"></a>모범 사례

다음은 자료와 관련 된 모범 사례 만큼 "설정" 되지 않습니다.

매개 변수를 만들 때 가능 하면 "정적 매개 변수"를 사용 하는 것이 좋습니다. 정적 스위치를 사용 하 여 런타임 비용 없이 재질의 전체 분기를 제거할 수 있습니다. 인스턴스는 서로 다른 값을 가질 수 있으므로 템플릿 셰이더를 설정 하 여 성능 손실을 방지할 수 있습니다. 단점은 셰이더 재컴파일을 발생 시키는 여러 순열이 생성 된다는 것입니다. 재질의 정적 매개 변수 수와 사용 되는 정적 매개 변수의 순열의 수를 최소화 합니다. 문서를 렌더링 하는 방법에 대 한 자세한 내용은 [Unreal Engine 설명서](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter)에서 확인할 수 있습니다.

![재질 설정에 대 한 모범 사례](images/unreal-materials-img-07.jpg)

재질 인스턴스를 만들 때 재질에 대해 재료 인스턴스 **상수** 에 대 한 기본 설정을 지정 해야 합니다. **재질 인스턴스 상수** 는 런타임 전 한 번만 계산 하는 인스턴스화된 재질입니다.

콘텐츠 브라우저를 통해 만든 재질 인스턴스 (**재질 인스턴스 > 만들기를 마우스 오른쪽 단추로 클릭**)는 재질 인스턴스 상수입니다. 자재 인스턴스 동적은 코드를 통해 생성 됩니다. 자료 인스턴스에 대 한 자세한 내용은 [Unreal Engine 설명서](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)에서 확인할 수 있습니다.

![Unreal에서 재질 인스턴스 만들기](images/unreal-materials-img-08.png)

재질/셰이더의 복잡성에 주목 하세요. 플랫폼 통계 아이콘을 클릭 하 여 다양 한 플랫폼에서 자료의 비용을 볼 수 있습니다. 또한, [Unreal Engine 설명서](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)에서 자료에 대 한 자세한 내용을 확인할 수 있습니다.

![Unreal에서 재질 인스턴스 동적 설정 만들기](images/unreal-materials-img-09.png)

셰이더 복잡성 [보기 모드](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)를 통해 셰이더의 상대적 복잡도를 빠르게 파악할 수 있습니다.

* 보기 모드 바로 가기 키: Alt + 8
* 콘솔 명령: viewmode shadercomplexity

![실수부의 자재 복잡성](images/unreal-materials-img-10.png)

## <a name="see-also"></a>참고 항목
* [모바일 자료](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [보기 모드](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [재질 인스턴스](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
