---
title: 사례 연구 - 안정화 평면 사용
description: 개발 팀이 안정화 평면을 사용하여 혼합 현실 애플리케이션에서 홀로그램 난해를 줄이는 방법을 살펴봅니다.
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 홀로그램, 안정화, 사례 연구, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 4227be39c18e43ad712a14dd61217994a8fc761f41f9416b95b511be5396712a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202366"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>사례 연구 - 안정화 평면을 사용하여 홀로그램 난해 줄이기

홀로그램을 작업하는 것은 까다로운 경우가 많습니다. 공간을 이동하고 모든 다른 각도에서 홀로그램을 살펴보면 일반 컴퓨터 화면에서 사용할 수 없는 몰입 수준이 제공됩니다. 이러한 홀로그램을 배치하고 현실적인 상태로 유지하는 것은 Microsoft HoloLens 하드웨어와 홀로그램 앱의 인텔리전트 디자인 둘 다에서 수행하는 기술적 작업입니다.

## <a name="the-tech"></a>기술

홀로그램이 실제로 공간을 공유하는 것처럼 표시되도록 하려면 색 구분 없이 제대로 렌더링되어야 합니다. 이는 부분적으로 안정화 평면에 고정된 홀로그램을 유지하는 HoloLens 하드웨어에 기본 제공되는 기술을 통해 [달성됩니다.](hologram-stability.md#reprojection)

평면은 점과 표준으로 정의됩니다. 항상 평면이 카메라를 향하도록 하려면 평면의 점을 설정하는 것이 좋습니다. 모든 것을 고정하고 안정적으로 유지하기 위해 처리에 초점을 맞출 지점을 HoloLens 알려줄 수 있습니다. 그러나 이 포커스 지점을 설정하는 것은 앱에 따라 달라지고 콘텐츠에 따라 앱을 만들거나 중단시킬 수 있습니다.

홀로그램스 안정화 평면이 제대로 적용될 때 가장 잘 작동하지만 실제로 의미하는 것은 만드는 애플리케이션의 유형에 따라 달라집니다. 현재 사용할 수 있는 앱 중 일부를 HoloLens 이 문제를 해결하는 방법을 살펴보겠습니다.

## <a name="behind-the-scenes"></a>배후 상황

다음 앱을 개발하는 동안 평면을 사용하지 않을 때 헤드가 이동하면 개체가 움직이는 것을 발견했습니다. 빠른 머리 또는 홀로그램 이동으로 색 구분도 확인할 수 있습니다. 결국 안정화 평면을 가장 잘 사용하고 해결할 수 없는 문제를 해결하기 위해 앱을 디자인하는 방법을 시행착오를 통해 학습했습니다.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy Explorer: 고정 콘텐츠, 3D 대화형

[Galaxy Explorer에는](../unity/galaxy-explorer.md) 장면에 두 가지 주요 요소가 있습니다. 즉, 정수 콘텐츠의 기본 보기와 응시 뒤에 있는 작은 UI 도구 모음이 있습니다. 안정화 논리의 경우 현재 응시 벡터가 각 프레임에서 교차하는 내용을 확인하여 지정된 충돌 계층에 있는 항목에 도달했는지 확인합니다. 이 경우 관심 있는 계층은 행성이므로 응시가 행성에 놓이면 안정화 평면이 배치됩니다. 대상 충돌 계층의 개체가 적중되지 않으면 앱은 보조 "계획 B" 계층을 사용합니다. 아무 것도 끊기지 않으면 안정화 평면은 콘텐츠를 스태핑할 때와 동일한 거리에 유지됩니다. UI 도구는 전체 장면의 안정성을 근사하고 훨씬 감소시키는 것을 발견했기 때문에 평면 대상으로 제외됩니다.

Galaxy Explorer의 디자인은 사물을 안정적으로 유지하고 색 구분의 영향을 줄이는 데 매우 좋습니다. 사용자는 콘텐츠를 좌우로 이동하지 않고 주변을 이동하고 회전하는 것이 좋으며, 행성은 색 구분이 눈에 띄지 않을 만큼 느리게 회전합니다. 또한 상수 60 FPS가 유지 관리되어 색 구분이 발생하지 않도록 방지할 수 있습니다.

이를 직접 확인하려면 [GitHub Galaxy Explorer 코드에서](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)LSRPlaneModifier.cs라는 파일을 찾습니다.

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: UI 포커스가 있는 고정 콘텐츠

HoloStudio 작업 중인 동일한 모델을 보는 데 대부분의 시간을 보냅니다. 응시는 새 도구를 선택하거나 UI를 탐색하려는 경우를 제외하고 상당한 양을 이동하지 않으므로 평면 설정 논리를 간단하게 유지할 수 있습니다. UI를 보면 평면은 응시가 맞춰지는 UI 요소로 설정됩니다. 모델을 볼 때 평면은 설정된 거리이며, 이는 모델 간의 기본 거리에 해당합니다.

![사용자가 홈 단추를 응시할 때 HoloStudio 시각화된 안정화 평면](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour 및 3D 뷰어: 애니메이션 및 동영상이 있는 고정 콘텐츠

HoloTour 및 3D 뷰어 위에 3D 효과가 추가된 멋진 애니메이션 개체 또는 영화를 보고 있습니다. 이러한 앱의 안정화는 현재 보고 있는 모든 것으로 설정됩니다.

또한 HoloTour는 고정된 위치에 유지하는 대신 사용자와 함께 이동하게 하여 가상 세계에서 너무 멀리 떨어져 있는 것을 방지합니다. 이렇게 하면 안정성 문제가 해결될 수 있도록 다른 홀로그램에서 충분히 멀리 떨어져 있지 않습니다.

![HoloTour의 이 예제에서 안정화 평면은 Had Pantheon의 이 영화로 설정됩니다.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: 동적 콘텐츠 및 환경 상호 작용

RoboRaid에서 안정화 평면을 설정하는 것은 가장 갑작스러운 이동이 필요한 앱임에도 불구하고 놀라울 정도로 간단합니다. 평면은 벽이나 주변 개체를 둘러들이는 쪽으로 맞춰져 있으며, 충분히 멀리 떨어져 있을 때는 고정된 거리 앞에 부동합니다.

RoboRaid는 안정화 평면을 염두에 두고 설계되었습니다. 머리가 잠겨 있기 때문에 가장 많이 이동하는 reticle은 빨간색과 파란색만 사용하여 이를 우회합니다. 그러면 색 색이 최소화됩니다. 또한 조각 사이에 약간의 깊이를 포함하며, 이미 예상된 시차 효과로 마스킹하여 발생하는 색 피가 최소화됩니다. 로봇은 빠르게 이동하지 않고 정기적으로 짧은 거리만 이동합니다. 안정화가 기본적으로 설정되는 2미터 정도 앞에 있는 경향이 있습니다.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>조각 및 Young Conker: 환경 상호 작용이 있는 동적 콘텐츠

C++의 Asobo Studio에서 작성한 Fragments 및 Young Conker는 안정화 평면을 설정하는 다른 접근 방식을 취합니다. POI(관심 지점)는 코드에서 정의되고 우선 순위에 따라 정렬됩니다. POI는 Young Conker의 Conker 모델, 메뉴, 목표 리틱 및 로고와 같은 게임 내 콘텐츠입니다. POI는 사용자의 응시에 의해 교차되고 평면은 우선 순위가 가장 높은 개체의 가운데로 설정됩니다. 교집합이 발생하지 않으면 평면이 기본 거리로 설정됩니다.

또한 조각 및 Young Conker는 이전에 재생 공간으로 검사한 것 밖으로 이동하는 경우 앱을 일시 중지하여 홀로그램에서 너무 멀리 떨어져 있는 것을 디자인합니다. 따라서 가장 안정적인 환경을 제공하는 것으로 발견되는 경계 내에 유지됩니다.

## <a name="do-it-yourself"></a>직접 수행

HoloLens 있고 이 문서의 개념을 사용하려는 경우 테스트 장면을 다운로드하여 다음 연습을 시도해 볼 수 있습니다. 테스트 장면에서는 Unity의 기본 제공 gizmo API를 사용하여 평면이 설정되는 위치를 시각화할 수 있습니다. 이 코드는 이 사례 연구에서 스크린샷을 캡처하는 데도 사용되었습니다.
1. 최신 버전의 [MixedRealityToolkit-Unity를 동기화합니다.](https://github.com/Microsoft/MixedRealityToolkit-Unity)
2. [HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) 장면을 엽니다.
3. 생성된 프로젝트를 빌드하고 구성합니다.
4. 디바이스에서 를 실행합니다.

### <a name="exercise-1"></a>연습 1

서로 다른 방향으로 주위에 여러 개의 흰색 점이 표시됩니다. 앞에는 세 개의 점이 서로 다른 깊이로 표시됩니다. 에어 탭을 사용하여 평면이 설정된 점을 변경합니다. 이 연습에서는 다른 두 가지의 경우 점을 쳐다보고 공간을 이동합니다. 왼쪽, 오른쪽, 위로 및 아래로 헤드를 켭니다. 점과 더 가깝고 더 멀리 이동합니다. 안정화 평면이 다른 대상으로 설정되면 어떻게 반응하는지 확인합니다.

### <a name="exercise-2"></a>연습 2

이제 두 개의 이동 점이 표시될 때까지 오른쪽으로 전환합니다. 하나는 가로 경로에서 진동하고 다른 하나는 세로 경로에 있습니다. 다시 한번, 에어 탭하여 평면이 설정된 점을 변경합니다. 색 구분이 줄고 평면에 연결된 점에 표시되는 방식을 알아차리기 다시 탭하여 평면 설정 함수에서 점의 속도를 사용합니다. 이 매개 변수는 개체의 의도한 동작에 대한 HoloLens 힌트를 제공합니다. 한 점에 속도가 사용되는 경우 다른 이동 점이 더 큰 색 구분을 표시하기 때문에 이 점을 사용해야 하는 경우를 알아야 합니다. 앱을 디자인할 때 이 점을 염두에 두어야 합니다. 개체의 동작에 대한 응집력 있는 흐름을 사용하면 아티팩트 표시를 방지할 수 있습니다.

### <a name="exercise-3"></a>연습 3

점의 새 구성이 표시될 때까지 한 번 더 오른쪽으로 전환합니다. 이 경우 거리에 점이 있고 한 점 앞에 점이 있습니다. 에어 탭을 사용하여 평면이 설정된 점을 변경하고, 뒷면의 점과 동작 중인 점 사이를 교대로 전환합니다. 평면 위치와 속도를 점으로 설정하면 아티팩트가 어디에나 표시되는지 확인할 수 있습니다.

**팁**
* 평면 설정 논리를 단순하게 유지합니다. 보셨듯이 몰입형 환경을 만들기 위해 복잡한 평면 설정 알고리즘이 필요하지 않습니다. 안정화 평면은 장난감의 한 부분일 뿐입니다.
* 가능한 경우 항상 대상 간에 평면을 원활하게 이동합니다. 멀리 떨어진 대상을 즉시 전환하면 시각적으로 장면을 방해할 수 있습니다.
* 평면 설정 논리에 특정 대상에 잠그는 옵션이 있는 것이 좋습니다. 이렇게 하면 필요한 경우 로고 또는 제목 화면과 같은 개체에서 평면을 잠글 수 있습니다.

## <a name="about-the-author"></a>작성자 정보

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Str도스</b><br>소프트웨어 엔지니어 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>추가 정보
* [MR 기본 100: Unity 시작](../unity/tutorials/holograms-100.md)
* [Unity의 포커스 포인트](../unity/focus-point-in-unity.md)
* [홀로그램 안정성](hologram-stability.md)
