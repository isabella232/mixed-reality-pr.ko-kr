---
title: 시선 추적 탐색
description: MRTK에서 탐색에 시선 대상 지정을 사용하는 방법
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, EyeTracking,
ms.openlocfilehash: e1ca34054a019e26bebf14282cd351467e5c65e2c2c3fa4f35647dd5aba680ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197119"
---
# <a name="eye-supported-navigation-in-mrtk"></a>MRTK에서 시선 지원 탐색

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

슬레이트에서 정보를 읽는 Imagine 표시된 텍스트의 끝에 도달하면 텍스트가 자동으로 위로 스크롤되어 더 많은 콘텐츠를 표시합니다. 또는 보고 있는 위치를 유창하게 확대할 수 있습니다. 또한 지도는 관심 있는 내용을 보기 필드 내에 유지하도록 콘텐츠를 자동으로 조정합니다. 또 다른 흥미로운 애플리케이션은 사용자가 보고 있는 홀로그램 부분을 전면에 자동으로 가져와서 3D 홀로그램을 실습하지 않는 관찰입니다. 다음은 시선 지원 탐색의 컨텍스트에서 이 페이지에 설명된 몇 가지 예제입니다.

다음 설명에서는 [MRTK 장면에서 시선 추적을 설정하는 방법과 MRTK Unity에서 시선](eye-tracking-basic-setup.md) [추적 데이터에 액세스하는](eye-tracking-target-selection.md) 기본 사항과 관련하여 이미 잘 알고 있다고 가정합니다.
다음에 설명된 예제는 모두 `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes/EyeTrackingDemo-03-Navigation) 장면의 일부입니다.

**요약:** 텍스트 자동 스크롤, 시선 응시 지원 팬 및 가상 맵의 확대/축소, 자가 응시 지향 3D 회전.

## <a name="auto-scroll"></a>자동 스크롤

자동 스크롤을 사용하면 사용자가 손가락을 떼지 않고 텍스트를 스크롤할 수 있습니다.
계속 읽으면 사용자가 보는 위치에 따라 텍스트가 자동으로 위로 또는 아래로 스크롤됩니다.
`EyeTrackingDemo-03-Navigation`(Assets/MRTK/Examples/Demos/EyeTracking/Scenes)에 제공된 예제에서 시작할 수 있습니다.
이 예제에서는 [TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) 구성 요소를 사용하여 새 텍스트를 유연하게 로드하고 서식을 지정할 수 있습니다.
자동 스크롤을 사용하도록 설정하려면 텍스트 상자의 collider 구성 요소에 다음 두 스크립트를 추가하기만 하면 됩니다.

### <a name="scrollrecttransf"></a>ScrollRectTransf

[TextMesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) 또는 일반적으로 [RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) 구성 요소를 스크롤하려면 [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) 스크립트를 사용할 수 있습니다.
[RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html)대신 질감을 스크롤하려면 [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf)대신 [ScrollTexture를](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) 사용합니다.
다음에서 Unity 편집기에서 사용할 수 있는 [ScrollRectTransf의](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) 매개 변수에 대해 자세히 설명합니다.

매개 변수 | Description
:---- | :----
LimitPanning | 사용하도록 설정하면 는 해당 경계에서 스크롤 가능한 콘텐츠를 중지합니다.
RectTransfToNavigate | 스크롤할 [RectTransform에](https://docs.unity3d.com/ScriptReference/RectTransform.html) 대한 참조입니다.
RefToViewport | 올바른 오프셋과 경계를 확인하기 위해 스크롤 가능한 콘텐츠의 부모 [RectTransform에](https://docs.unity3d.com/ScriptReference/RectTransform.html) 대한 참조입니다.
AutoGazeScrollIsActive | 사용하도록 설정하면 사용자가 *활성 영역을* 보면 텍스트가 자동으로 스크롤됩니다(예: 세로 스크롤 속도가 0이 아닌 경우 스크롤 패널의 위쪽 및 아래쪽 부분).
ScrollSpeed_x | 0과 다른 값으로 설정하면 가로 스크롤이 활성화됩니다. 음수 값은 스크롤 방향의 변경을 의미합니다. 왼쪽에서 오른쪽으로, 오른쪽에서 왼쪽으로 변경합니다.
ScrollSpeed_y | 0과 다른 값으로 설정하면 세로 스크롤이 활성화됩니다. 음수 값은 스크롤 방향의 변화를 의미합니다. 최대 아래로 또는 아래로 변경합니다.
MinDistFromCenterForAutoScroll | 대상 적중 상자(0, 0)의 중심에서 스크롤할 x 및 y의 최소 거리를 정규화했습니다. 따라서 값의 범위는 0(항상 스크롤)에서 0.5(스크롤 안 함) 사이여야 합니다.
UseSkimProofing | 사용하도록 설정하면 빠르게 주변을 살펴볼 때 갑작스러운 스크롤 이동을 방지할 수 있습니다. 이렇게 하면 스크롤의 응답성이 떨어집니다. *SkimProofUpdateSpeed* 값으로 튜닝할 수 있습니다.
SkimProofUpdateSpeed | 값이 낮을수록 스키밍 후 스크롤 속도가 느려집니다. 권장 값: 5.

![Unity에서 시선 지원 스크롤 설정](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

_EyeTrackingTarget_ 구성 요소를 연결하면 시선 응시 관련 이벤트를 유연하게 처리할 수 있습니다.
스크롤 샘플은 사용자가 패널을 *보고* 사용자가 패널을 *벗어날* 때 중지할 때 시작되는 스크롤 텍스트를 보여 줍니다.
![Unity에서 시선 지원 스크롤 설정: EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>응시 지원 팬 및 확대/축소

Who 이전에 가상 맵을 사용하여 집이나 완전히 새로운 장소를 탐색하지 않았나요? 시선 추적을 사용하면 관심 있는 부분을 정확히 파악할 수 있으며 확대하면 거리 과정을 원활하게 따라 주변을 탐색할 수 있습니다.
지리적 지도를 탐색할 뿐만 아니라 사진, 데이터 시각화 또는 라이브 스트리밍 의료 이미지의 세부 정보를 확인하는 데에도 유용합니다. 앱에서 이 기능을 사용하는 것은 쉽습니다. [질감에]( https://docs.unity3d.com/ScriptReference/Texture.html) 렌더링된 콘텐츠(예: 사진, 스트리밍된 데이터)의 경우 [PanZoomTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture) 스크립트를 추가하기만 하면됩니다.
[RectTransform의](https://docs.unity3d.com/ScriptReference/RectTransform.html) 경우 [PanZoomRectTransf 를](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf)사용합니다. [자동 스크롤](#auto-scroll) 기능을 확장하면 기본적으로 를 사용하여 세로 및 가로로 동시에 스크롤하고 사용자의 현재 포커스 지점을 중심으로 콘텐츠를 확대할 수 있습니다.

매개 변수 | Description
:---- | :----
LimitPanning | 사용하도록 설정하면 는 해당 경계에서 스크롤 가능한 콘텐츠를 중지합니다.
HandZoomEnabledOnStartup | 손 제스처가 확대/축소 제스처를 수행하도록 자동으로 설정되는지 여부를 나타냅니다. 실수로 확대/축소 작업을 트리거하지 않도록 처음에 사용하지 않도록 설정할 수 있습니다.
RendererOfTextureToBeNavigated | 탐색할 질감의 참조된 렌더러입니다.
Zoom_Acceleration | 로지스틱 속도 함수 매핑의 가속도를 정의하는 확대/축소 가속.
Zoom_SpeedMax | 최대 확대/축소 속도입니다.
Zoom_MinScale | 확대를 위한 질감의 최소 배율(예: 0.5f(원래 크기의 절반))입니다.
Zoom_MaxScale | 축소를 위한 질감의 최대 배율(예: 1f(원래 크기) 또는 2.0f(원래 크기의 두 배))
Zoom_TimeInSecToZoom | 시간 지정된 확대/축소: 트리거되면 지정된 시간(초)에 대해 확대/축소가 수행됩니다.
Zoom_Gesture | 확대/축소에 사용할 손 제스처의 유형입니다.
--- | ---
Pan_AutoScrollIsActive | 사용하도록 설정하면 사용자가 *활성 영역을* 보면 텍스트가 자동으로 스크롤됩니다(예: 세로 스크롤 속도가 0이 아닌 경우 스크롤 패널의 위쪽 및 아래쪽 부분).
Pan_Speed_x | 0과 다른 값으로 설정하면 가로 스크롤이 활성화됩니다. 음수 값은 스크롤 방향의 변경을 의미합니다. 왼쪽에서 오른쪽으로, 오른쪽에서 왼쪽으로 변경합니다.
Pan_Speed_y | 0과 다른 값으로 설정하면 세로 스크롤이 활성화됩니다. 음수 값은 스크롤 방향의 변화를 의미합니다. 최대 아래로 또는 아래로 변경합니다.
Pan_MinDistFromCenter | 대상 적중 상자(0, 0)의 중심에서 스크롤할 x 및 y의 최소 거리를 정규화했습니다. 따라서 값의 범위는 0(항상 스크롤)에서 0.5(스크롤 안 함) 사이여야 합니다.
UseSkimProofing | 사용하도록 설정하면 빠르게 주변을 살펴볼 때 갑작스러운 스크롤 이동을 방지할 수 있습니다. 이렇게 하면 스크롤의 응답성이 떨어집니다. *SkimProofUpdateSpeed* 값으로 튜닝할 수 있습니다.
SkimProofUpdateSpeed | 값이 낮을수록 스키밍 후 스크롤 속도가 느려집니다. 권장 값: 5.

![Unity에서 시선 지원 이동 및 확대/축소 설정](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>주의 기반 3D 회전

Imagine 3D 개체와 보려는 파트가 마치 시스템에서 사용자의 마음에 읽혀지고 항목이 자동으로 바뀌는 것을 알 수 있는 것처럼 좀 더 성실하게 방향을 전환하는 것을 볼 수 있습니다.
이는 손가락을 떼지 않고 홀로그램의 모든 측면을 조사할 수 있는 주의 기반 3D 회전에 대한 아이디어입니다.
이 동작을 사용하도록 설정하려면 [Collider](https://docs.unity3d.com/ScriptReference/Collider.html) 구성 요소가 있는 [GameObject 부분에 OnLookAtRotateByEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) 스크립트를 추가하기만 하면 됩니다.
아래에 나열된 여러 매개 변수를 조정하여 홀로그램이 회전하는 속도와 방향을 제한할 수 있습니다.

생각해 볼 수 있듯이, 이 동작을 항상 활성화하면 장면에 매우 방해가 될 수 있습니다.
이 때문에 이 동작을 사용하지 않도록 설정한 다음, 음성 명령을 사용하여 빠르게 사용하도록 설정할 수 있습니다.
또는 `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes)에 포커스가 있는 대상을 선택할 수 있는 [TargetMoveToCamera를](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera) 사용하는 예제를 추가했습니다. 여기서는 *"Come to me"라고* 말합니다.

근사 모드에서 자동 회전 모드가 자동으로 활성화됩니다.
이 모드에서는 모든 측면에서 관찰할 수 있습니다. 단순히 뒤로 움켜서 보고, 주변을 둘러보거나, 손을 잡고 회전하기 위해 다가갈 수 있습니다. 대상을 해제하면(& 손가락 모으기 또는 *"다시 보내기"라고* 말함) 원래 위치로 돌아가서 멀리서 반응하지 않습니다.

매개 변수 | Description
:---- | :----
SpeedX | 수평 회전 속도입니다.
빠른 | 수직 회전 속도입니다.
InverseX | 가로 회전 방향을 역방향으로 변환합니다.
역방향 | 세로 회전 방향을 역방향으로 변환합니다.
RotationThreshInDegrees | '대상에 응시'와 '대상으로 카메라' 사이의 각도가 이 값보다 작은 경우 아무 것도 수행하지 않습니다. 이는 작은 지터 회전을 방지하기 위한 것입니다.
MinRotX | 최소 가로 회전 각도입니다. 이는 회전을 다른 방향으로 제한하기 위한 것입니다.
MaxRotX | 최대 가로 회전 각도입니다. 이는 회전을 다른 방향으로 제한하기 위한 것입니다.
MinRotY | x축 주위의 회전을 제한하기 위한 최소 세로 회전 각도입니다.
MaxRotY | y축 주위의 회전을 제한하는 최대 세로 회전 각도입니다.

![Unity에서 시선 지원 3D 회전 설정](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

요약하면 위의 스크립트를 사용하면 텍스트 스크롤, 질감 확대/축소 및 이동, 3D 홀로그램 조사 회전과 같은 다양한 입력 탐색 작업에 시선 응시를 사용할 수 있습니다.

### <a name="see-also"></a>추가 정보

- [시선 추적을 사용하는 기본 MRTK 설정](eye-tracking-basic-setup.md)
- [시선 지원 대상 선택](eye-tracking-target-selection.md)

---
["MixedRealityToolkit의 시선 추적"으로 돌아가기](eye-tracking-main.md)
