---
title: Unreal을 사용하기 위한 권장 성능
description: 권장 Unreal 프로젝트 설정을 사용하여 혼합 현실 앱을 최대한 활용하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: safarooq
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 성능, 최적화, 설정, 설명서
ms.openlocfilehash: e956f12d27c826cff35e0b65957060953073a28b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583062"
---
# <a name="performance-recommendations-for-unreal"></a>Unreal을 사용하기 위한 권장 성능

Unreal Engine에는 [혼합 현실에 대한 성능 권장 사항](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)에 설명된 내용을 기반으로 앱 성능을 향상시킬 수 있는 여러 기능이 있습니다. 계속하기 전에 애플리케이션 병목, 혼합 현실 앱 분석 및 프로파일링, 일반 성능 수정 사항을 확인해 보는 것이 좋습니다.

## <a name="recommended-unreal-project-settings"></a>권장 Unreal 프로젝트 설정

**편집 > 프로젝트 설정** 에서 다음의 각 설정을 찾을 수 있습니다.

1. 모바일 VR 렌더러 사용:
    * **프로젝트** 섹션으로 스크롤하고 **대상 하드웨어** 를 선택한 다음, 대상 플랫폼을 **모바일/태블릿** 으로 설정합니다.

![모바일 대상 설정](images/unreal/performance-recommendations-img-01.png)

2. 전방 렌더러 사용: 
    * 전방 렌더러는 개별적으로 끌 수 있는 기능의 수가 많기 때문에 기본 지연 렌더링 파이프라인보다 혼합 현실에 훨씬 적합합니다. 
    * 자세한 내용은 [Unreal의 설명서](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html)에서 확인할 수 있습니다.

![전방 렌더링](images/unreal/performance-recommendations-img-04.png)

3. 모바일 다중 보기 사용:
    * **엔진** 섹션으로 스크롤하고 **렌더링** 을 선택한 다음, **VR** 섹션을 확장하고 **인스턴스 스테레오** 와 **모바일 다중 뷰** 를 모두 사용하도록 설정합니다. 모바일 HDR를 선택 취소해야 합니다.

![VR 렌더링 설정](images/unreal/performance-recommendations-img-03.png)

4. **[OpenXR만]** **기본값** 또는 **D3D12** 가 **기본 RHI** 로 선택되어 있는지 확인합니다.
    * 추가 렌더링 패스를 수행하는 플랫폼으로 인해 **D3D11** 을 선택하면 성능에 부정적인 영향을 미칩니다. **D3D12** 는 추가 렌더링 패스를 피하는 것 외에도 렌더링 성능 향상을 제공해야 합니다.

![기본 RHI](images/unreal/performance-recommendations-img-09.png)

5. 꼭짓점 Fogging 비활성화: 
    * 꼭짓점 fogging 다각형의 각 꼭짓점에 포그 계산을 적용한 다음, 다각형의 표면 전체에 결과를 보간합니다. 게임에서 안개를 사용하지 않는 경우 꼭짓점 Fogging을 비활성화하여 음영 성능을 높이는 것이 좋습니다.

![꼭짓점 fogging 옵션](images/unreal/performance-recommendations-img-05.png)

6. 폐색 고르기 사용 안 함:
    * **엔진** 섹션으로 스크롤하고 **렌더링** 을 선택한 다음, **고르기** 섹션을 확장하고 **폐색 고르기** 를 선택 취소합니다.
        + 렌더링되는 자세한 장면에 폐색 고르기가 필요한 경우 **엔진 > 렌더링** 에서 **소프트웨어 폐색 고르기 지원** 을 사용하도록 설정하는 것이 좋습니다. Unreal이 CPU에서 작동하며, HoloLens 2에서 성능이 좋지 않은 GPU 폐색 쿼리를 방지할 수 있습니다.
    * 모바일 디바이스에서 GPU에 대한 폐색 고르기 속도가 느립니다. 일반적으로 GPU는 주로 렌더링에 관여하려고 합니다. 폐색이 성능에 도움이 된다고 생각되면 대신 소프트웨어 폐색을 사용하도록 설정해 보세요. 

> [!NOTE]
> 많은 수의 그리기 호출로 인해 CPU가 이미 바인딩된 경우 소프트웨어 폐색을 사용하도록 설정하면 성능이 저하될 수 있습니다.

![폐색 고르기 사용 안 함](images/unreal/performance-recommendations-img-02.png)

7. 사용자 지정 깊이-스텐실 비활성화 패스:
    * 사용자 지정 깊이-스텐실을 비활성화하려면 추가 패스가 필요합니다. 즉, 속도가 느립니다. 반투명도는 Unreal에서도 느립니다. 자세한 내용은 [Unreal의 설명서](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html)에서 확인할 수 있습니다.

![깊이 스텐실](images/unreal/performance-recommendations-img-06.png)

8. 중첩된 섀도 맵 축소: 
    * 섀도 맵의 수를 줄이면 성능이 향상됩니다. 일반적으로 눈에 보이는 품질 손실이 없는 한 속성을 1로 설정해야 합니다. 

![중첩된 섀도 맵](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a>선택적 설정

> [!NOTE]
> 다음 설정을 사용하면 성능을 향상시킬 수 있지만 특정 기능을 사용하지 않도록 설정하는 비용이 듭니다. 해당 기능이 필요하지 않는 경우에만 이 설정을 사용하세요.

1. 모바일 셰이더 순열 감소
    * 조명이 카메라와 별개로 이동하지 않는 경우 속성 값을 안전하게 0으로 설정할 수 있습니다. 기본 장점은 Unreal이 여러 셰이더 순열을 제거하여 셰이더 컴파일의 속도를 높일 수 있다는 것입니다.

![모바일 셰이더 순열 감소](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a>참조

* [Unreal 엔진 모바일 성능 지침]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)