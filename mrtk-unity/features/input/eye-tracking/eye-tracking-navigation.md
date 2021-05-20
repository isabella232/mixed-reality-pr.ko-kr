---
title: 시선 추적 탐색
description: MRTK의 탐색에 눈동자 대상 지정을 사용 하는 방법
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, EyeTracking,
ms.openlocfilehash: d966bbe1d3a256e55c62532e8101c1f2846e1136
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145269"
---
# <a name="eye-supported-navigation-in-mrtk"></a>MRTK의 눈 지원 탐색

![MRTK](../../images/eye-tracking/mrtk_et_navigation.png)

슬레이트에 대 한 정보를 읽고 표시 된 텍스트의 끝에 도달 하면 텍스트가 자동으로 이동 하 여 더 많은 콘텐츠를 표시 한다고 가정 합니다. 또는 원하는 위치에서 확대를 운용 수 있습니다. 지도는 또한 보기의 필드 내에서 관심 있는 항목을 유지 하도록 콘텐츠를 자동으로 조정 합니다. 또 다른 흥미로운 응용 프로그램은 앞으로 보려는 홀로그램의 일부를 자동으로 가져와 3D holograms를 자유롭게 관찰 하는 것입니다. 이러한 예제 중 일부는 눈에 잘 지 원하는 탐색의 컨텍스트에서이 페이지에 설명 되어 있습니다.

다음 설명에서는 mrtk [장면에서 눈 추적을 설정](eye-tracking-basic-setup.md) 하는 방법과 Mrtk Unity에서 [눈 추적 데이터에 액세스](eye-tracking-target-selection.md) 하는 기본 사항을 사용 하는 방법을 이미 잘 알고 있다고 가정 합니다.
다음에 설명 된 예제는 `EyeTrackingDemo-03-Navigation` (asset/MRTK/예제/데모/EyeTracking/EyeTrackingDemo) 장면의 모든 부분입니다.

**요약:** 텍스트 자동 스크롤, 눈에 잘 지 원하는 가상 맵의 이동 및 확대/축소

## <a name="auto-scroll"></a>자동 스크롤

자동 스크롤을 사용 하면 사용자가 손가락을 떼지 않고 텍스트를 스크롤할 수 있습니다.
읽기를 계속 하 고 사용자가 찾고 있는 위치에 따라 텍스트가 자동으로 위아래로 이동 합니다.
에서 제공 하는 예제 `EyeTrackingDemo-03-Navigation` (asset/MRTK/example/데모/EyeTracking/장면)에서 시작할 수 있습니다.
이 예제에서는 [Textmesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) 구성 요소를 사용 하 여 새 텍스트를 유연 하 게 로드 하 고 서식을 지정할 수 있습니다.
자동 스크롤을 사용 하도록 설정 하려면 다음 두 스크립트를 텍스트 상자의 collider 구성 요소에 추가 하기만 하면 됩니다.

### <a name="scrollrecttransf"></a>ScrollRectTransf

[Textmesh](https://docs.unity3d.com/ScriptReference/TextMesh.html) 를 스크롤하거나 보다 일반적으로 [연관 recttransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) 구성 요소를 사용 하 여 스크롤하려면 [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) 스크립트를 사용할 수 있습니다.
[RectTransform](https://docs.unity3d.com/ScriptReference/RectTransform.html)대신 질감을 스크롤하려면 [ScrollRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf)대신 [ScrollTexture를](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollTexture) 사용합니다.
다음에서 Unity 편집기에서 사용할 수 있는 [ScrollRectTransf의](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ScrollRectTransf) 매개 변수에 대해 자세히 설명합니다.

매개 변수 | 설명
:---- | :----
LimitPanning | 사용하도록 설정하면 는 해당 경계에서 스크롤 가능한 콘텐츠를 중지합니다.
RectTransfToNavigate | 스크롤할 [RectTransform에](https://docs.unity3d.com/ScriptReference/RectTransform.html) 대한 참조입니다.
RefToViewport | 올바른 오프셋과 경계를 확인하기 위해 스크롤 가능한 콘텐츠의 부모 [RectTransform에](https://docs.unity3d.com/ScriptReference/RectTransform.html) 대한 참조입니다.
AutoGazeScrollIsActive | 사용하도록 설정하면 사용자가 *활성 영역을* 보면 텍스트가 자동으로 스크롤됩니다(예: 세로 스크롤 속도가 0이 아닌 경우 스크롤 패널의 위쪽 및 아래쪽 부분).
ScrollSpeed_x | 0과 다른 값으로 설정하면 가로 스크롤이 활성화됩니다. 음수 값은 스크롤 방향의 변경을 의미합니다. 왼쪽에서 오른쪽으로, 오른쪽에서 왼쪽으로 변경합니다.
ScrollSpeed_y | 0과 다른 값으로 설정하면 세로 스크롤이 활성화됩니다. 음수 값은 스크롤 방향의 변화를 의미합니다. 최대 아래로 또는 아래로 변경합니다.
MinDistFromCenterForAutoScroll | 대상 적중 상자(0, 0)의 중심에서 스크롤할 x 및 y의 최소 거리를 정규화했습니다. 따라서 값의 범위는 0(항상 스크롤)에서 0.5(스크롤 안 함) 사이여야 합니다.
UseSkimProofing | 사용 하도록 설정 하면 신속 하 게 살펴볼 때 급격 한 스크롤 이동을 방지 합니다. 이렇게 하면 스크롤 속도가 더 떨어질 수 있습니다. *SkimProofUpdateSpeed* 값으로 튜닝할 수 있습니다.
SkimProofUpdateSpeed | 값이 낮을수록 skimming 후 스크롤 속도가 빨라집니다. 권장 값: 5.

![Unity에서 지원 되는 스크롤 설정](../../images/eye-tracking/mrtk_et_nav_scroll.jpg)

### <a name="eyetrackingtarget"></a>EyeTrackingTarget

EyeTrackingTarget 구성 요소를 연결 하면 눈에  관련 이벤트를 유연 하 게 처리할 수 있습니다.
Scroll 샘플은 사용자가 패널을 볼 때 시작 되 고 *사용자가 해당* 패널에서 *떨어져* 있는 경우 중지 하는 스크롤 텍스트를 보여 줍니다.
![Unity에서 지원 되는 스크롤 설정: EyeTrackingTarget](../../images/eye-tracking/mrtk_et_nav_scroll_ettarget.jpg)

## <a name="gaze-supported-pan-and-zoom"></a>응시-지원 되는 이동 및 확대/축소

자신의 홈을 검색 하거나 완전히 새로운 위치를 탐색 하기 전에 가상 지도를 사용 하지 않은 사용자는 누구 인가요? 아이 추적을 사용 하면 관심 있는 부분을 직접 파악 하 고 확대 한 후에는 여러 번의 작업을 원활 하 게 수행 하 여 환경을 탐색할 수 있습니다.
이는 지리적 지도를 탐색 하는 데 유용 하 고 사진, 데이터 시각화 또는 라이브 스트리밍 의료 이미지에서 세부 정보를 확인 하는 데에도 유용 합니다. 앱에서이 기능을 사용 하는 것이 쉽습니다. [질감]( https://docs.unity3d.com/ScriptReference/Texture.html) 으로 렌더링 된 콘텐츠 (예: 사진, 스트리밍 데이터)의 경우 [PanZoomTexture](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomTexture) 스크립트를 추가 하기만 하면 됩니다.
[연관 recttransform](https://docs.unity3d.com/ScriptReference/RectTransform.html) 의 경우 [PanZoomRectTransf](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.PanZoomRectTransf)를 사용 합니다. [자동 스크롤](#auto-scroll) 기능을 확장 하면 기본적으로 동시에 가로와 세로로 스크롤할 수 있으며 사용자의 현재 포커스 지점 주위에서 콘텐츠를 확대할 수 있습니다.

매개 변수 | 설명
:---- | :----
핸들 이동 | 사용하도록 설정하면 는 해당 경계에서 스크롤 가능한 콘텐츠를 중지합니다.
HandZoomEnabledOnStartup | 손 제스처가 확대/축소 제스처를 수행하도록 자동으로 설정되는지 여부를 나타냅니다. 실수로 확대/축소 작업을 트리거하지 않도록 처음에 사용하지 않도록 설정할 수 있습니다.
RendererOfTextureToBeNavigated | 탐색할 질감의 참조된 렌더러입니다.
Zoom_Acceleration | 로지스틱 속도 함수 매핑의 가속도를 정의하는 확대/축소 가속.
Zoom_SpeedMax | 최대 확대/축소 속도입니다.
Zoom_MinScale | 확대를 위한 질감의 최소 배율(예: 0.5f(원래 크기의 절반))입니다.
Zoom_MaxScale | 축소할 질감의 최대 배율(예: 1f(원래 크기) 또는 2.0f(원래 크기의 두 배))
Zoom_TimeInSecToZoom | 시간 지정된 확대/축소: 트리거되면 지정된 시간(초)에 대해 확대/축소가 수행됩니다.
Zoom_Gesture | 확대/축소에 사용할 손 제스처의 유형입니다.
--- | ---
Pan_AutoScrollIsActive | 사용하도록 설정하면 사용자가 *활성 영역을* 보면 텍스트가 자동으로 스크롤됩니다(예: 세로 스크롤 속도가 0이 아닌 경우 스크롤 패널의 위쪽 및 아래쪽 부분).
Pan_Speed_x | 0이 아닌 값으로 설정 하면 가로 스크롤이 사용 됩니다. 음수 값은 스크롤 방향 변경 (왼쪽에서 오른쪽 및 오른쪽에서 왼쪽으로)입니다.
Pan_Speed_y | 0이 아닌 값으로 설정 하면 세로 스크롤이 사용 됩니다. 음수 값은 스크롤 방향에 대 한 변경 내용입니다.
Pan_MinDistFromCenter | 스크롤할 대상의 적중 상자 (0, 0)의 중심에서 x 및 y의 정규화 된 최소 거리입니다. 따라서 값의 범위는 0 (항상 스크롤)과 0.5 (스크롤 안 함) 사이 여야 합니다.
UseSkimProofing | 사용 하도록 설정 하면 신속 하 게 살펴볼 때 급격 한 스크롤 이동을 방지 합니다. 이렇게 하면 스크롤 속도가 더 떨어질 수 있습니다. *SkimProofUpdateSpeed* 값으로 튜닝할 수 있습니다.
SkimProofUpdateSpeed | 값이 낮을수록 skimming 후 스크롤 속도가 빨라집니다. 권장 값: 5.

![Unity에서 지원 되는 이동 및 확대/축소 설치](../../images/eye-tracking/mrtk_et_nav_panzoom.jpg)

## <a name="attention-based-3d-rotation"></a>주의 기반 3D 회전

3D 개체와 보다 긴밀 하 게 magically 하는 부분을 확인 하는 것이 좋습니다. 시스템에서 사용자의 마음을 읽고 항목을 사용자에 게 전환 하는 것을 알고 있어야 합니다.
이는 손가락을 떼지 않고도 홀로그램의 모든 측면을 조사할 수 있는 주의 기반 3D 회전의 개념입니다.
이 동작을 사용하도록 설정하려면 [충돌체](https://docs.unity3d.com/ScriptReference/Collider.html) 구성 요소가 있는 [GameObject의 부분에 OnLookAtRotateByEyeGaze](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) 스크립트를 추가하기만 하면 됩니다.
아래에 나열된 여러 매개 변수를 조정하여 홀로그램이 회전하는 속도와 방향을 제한할 수 있습니다.

생각해 볼 수 있듯이, 이 동작을 항상 활성화하면 장면에 매우 방해가 될 수 있습니다.
이 때문에 이 동작을 사용하지 않도록 설정한 다음, 음성 명령을 사용하여 빠르게 사용하도록 설정할 수 있습니다.
또는 `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes)에 포커스가 있는 대상을 선택할 수 있는 [TargetMoveToCamera를](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.TargetMoveToCamera) 사용하는 예제를 추가했습니다. 여기서는 *"Come to me"라고* 말합니다.

근사 모드에서 자동 회전 모드가 자동으로 활성화됩니다.
이 모드에서는 모든 측면에서 관찰할 수 있습니다. 단순히 뒤로 움켜서 보고, 주변을 둘러보거나, 손을 잡고 회전하기 위해 다가갈 수 있습니다. 대상을 해제하면(& 손가락 모으기 또는 *"다시 보내기"라고* 말함) 원래 위치로 돌아가서 멀리서 반응하지 않습니다.

매개 변수 | 설명
:---- | :----
SpeedX | 수평 회전 속도입니다.
빠른 | 수직 회전 속도입니다.
InverseX | 가로 회전 방향을 역방향으로 합니다.
역방향 | 세로 회전 방향을 역방향으로 변환합니다.
RotationThreshInDegrees | '대상에 응시'와 '대상으로 카메라' 사이의 각도가 이 값보다 작은 경우 아무 것도 수행하지 않습니다. 이는 작은 지터 회전을 방지하기 위한 것입니다.
MinRotX | 최소 가로 회전 각도입니다. 이는 다른 방향으로 회전을 제한 하기 위한 것입니다.
MaxRotX | 최대 가로 회전 각도입니다. 이는 다른 방향으로 회전을 제한 하기 위한 것입니다.
MinRotY | X 축을 중심으로 회전을 제한 하는 최소 세로 회전 각도입니다.
MaxRotY | Y 축을 중심으로 회전을 제한 하는 최대 세로 회전 각도입니다.

![Unity의 눈 지원 3D 회전 설정](../../images/eye-tracking/mrtk_et_nav_rotate.jpg)

요약 하면 위의 스크립트를 사용 하 여 텍스트 스크롤, 확대/축소 및 이동 뿐만 아니라 조사 3D holograms를 회전 하는 것과 같은 다양 한 입력 탐색 작업에 대해 눈동자를 사용 하기 시작할 수 있습니다.

### <a name="see-also"></a>참고 항목

- [아이 추적을 사용 하기 위한 기본 MRTK 설정](eye-tracking-basic-setup.md)
- [눈 지원 대상 선택](eye-tracking-target-selection.md)

---
["MixedRealityToolkit의 눈동자 추적"으로 돌아가기](eye-tracking-main.md)
