---
title: 입력 시뮬레이션 서비스
description: MRTK의 입력 시뮬레이션 서비스에 대한 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: f329cceded5e510d3d4fc1a1c13b5a504f1f3669ad408b733267595e77dd15a6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227622"
---
# <a name="input-simulation-service"></a>입력 시뮬레이션 서비스

![MRTK 입력 시뮬레이션](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

MRTK의 입력 시뮬레이션을 사용하면 디바이스를 빌드하고 배포하지 않고도 Unity 편집기에서 다양한 유형의 상호 작용을 테스트할 수 있습니다. 이를 통해 설계 및 개발 프로세스에서 아이디어를 빠르게 반복할 수 있습니다. 키보드와 마우스 조합을 사용하여 시뮬레이션된 입력을 제어합니다.

입력 시뮬레이션 서비스는 Unity 편집기에서 사용할 수 없는 디바이스 및 플랫폼의 동작을 에뮬레이트합니다. 다음은 이러한 템플릿의 예입니다.

* HoloLens 또는 VR 디바이스 헤드 추적
* 손 제스처 HoloLens
* HoloLens 2 손 추적
* 시선 추적 HoloLens 2
* VR 디바이스 컨트롤러

> [!WARNING]
> Unity의 XR 홀로그램 에뮬레이션 > 에뮬레이션 모드 = "편집기에서 시뮬레이트"를 사용하는 경우에는 작동하지 않습니다. Unity의 편집기 내 시뮬레이션은 MRTK의 입력 시뮬레이션에서 제어합니다. MRTK 입력 시뮬레이션 서비스를 사용하려면 XR 홀로그램 에뮬레이션을 에뮬레이션 모드 = *"없음"으로* 설정해야 합니다.

## <a name="how-to-use-mrtk-input-simulation"></a>MRTK 입력 시뮬레이션을 사용하는 방법 

입력 시뮬레이션은 MRTK와 함께 제공된 프로필에서 기본적으로 사용하도록 설정됩니다. **재생 단추를** 클릭하면 입력 시뮬레이션이 지원된 장면을 실행할 수 있습니다.

* **W, A, S, D, Q, E** 키를 눌러 카메라를 이동합니다.
* **마우스 오른쪽 단추** 를 누른 채 마우스를 움직여 주위를 둘러봅니다.
* 시뮬레이션된 손을 들어 가져오려면 **스페이스 바(오른손)** 또는 **왼쪽 Shift 키(왼손)** 를 누릅니다.
* 시뮬레이션된 손을 뷰에 유지하려면 **T** 또는 **Y** 키를 누릅니다.
* 시뮬레이션된 손을 회전하려면 **Ctrl 키를** 누른 채 마우스를 이동합니다.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a>편집기 입력 시뮬레이션 치트 시트에서

HandInteractionExamples 장면에서 **왼쪽 Ctrl+ H를** 눌러 입력 시뮬레이션 컨트롤이 있는 치트 시트를 표시합니다.

> ![MRTK 입력 시뮬레이션 치트 시트](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a>입력 시뮬레이션 서비스 사용

입력 시스템 데이터 공급자 구성에서 입력 시뮬레이션 서비스를 다음으로 구성할 수 있습니다.

* **형식은** *Microsoft.MixedReality.Toolkit. Input > InputSimulationService*.
* 서비스에서 키보드 및 마우스 입력을 사용하므로 **기본적으로 지원되는 플랫폼에는** 모든 *편집기* 플랫폼이 포함됩니다.

> [!NOTE]
> 원하는 대상을 포함하도록 **지원되는** 플랫폼 속성을 변경하여 독립 실행형과 같은 다른 플랫폼 엔드포인트에서 입력 시뮬레이션 서비스를 사용할 수 있습니다.
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a>카메라 컨트롤

헤드 이동은 입력 시뮬레이션 서비스에서 에뮬레이트할 수 있습니다.

### <a name="rotating-the-camera"></a>카메라 회전

1. 뷰포트 편집기 창을 마우스로 가리킵니다.
    *단추 누른 것이 작동하지 않는 경우 입력 포커스를 지정하려면 창을 클릭해야 할 수 있습니다.*
1. 마우스 모양 **단추를** 길게 누릅니다(기본값: 마우스 오른쪽 단추).
1. 뷰포트 창에서 마우스를 이동하여 카메라를 회전합니다.
1. 스크롤 휠을 사용하여 카메라를 보기 방향으로 굴려야 합니다.

입력 시뮬레이션 프로필에서 **마우스 모양 속도** 설정을 변경하여 카메라 회전 속도를 구성할 수 있습니다.

또는 **Look Horizontal** Look / **Vertical** 축을 사용하여 카메라를 회전합니다(기본값: 게임 컨트롤러 오른쪽 엄지스틱).

### <a name="moving-the-camera"></a>카메라 이동

가로  / **이동 세로로 이동** 축을 사용하여 카메라를 이동합니다(기본값: WASD 키 또는 게임 컨트롤러 왼쪽 엄지스틱).

카메라 위치 및 회전 각도는 도구 창에서도 명시적으로 설정할 수 있습니다. 다시 설정 단추를 사용하여 카메라를 기본값으로 **다시 설정할** 수 있습니다.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a>컨트롤러 시뮬레이션

입력 시뮬레이션은 에뮬레이트된 컨트롤러 디바이스(즉, 모션 컨트롤러 및 손)를 지원합니다. 이러한 가상 컨트롤러는 단추 또는 잡기 가능한 개체와 같은 일반 컨트롤러를 지원하는 모든 개체와 상호 작용할 수 있습니다.

### <a name="controller-simulation-mode"></a>컨트롤러 시뮬레이션 모드

입력 [시뮬레이션 도구 창에서](#input-simulation-tools-window) **기본 컨트롤러 시뮬레이션 모드** 설정은 세 개의 고유한 입력 모델 간에 전환됩니다. 이 기본 모드는 입력 시뮬레이션 프로필에서도 설정할 수 있습니다.

* *굴절형 손:* 공동 위치 데이터를 통해 완전히 굴절된 손 디바이스를 시뮬레이션합니다.

   HoloLens 2 상호 작용 모델을 에뮬레이트합니다.

   손의 정확한 위치를 기반으로 하거나 터치를 사용하는 상호 작용은 이 모드에서 시뮬레이션할 수 있습니다.

* *손 제스처:* 에어 탭 및 기본 제스처를 통해 간소화된 손 모델을 시뮬레이션합니다.

   HoloLens [상호 작용 모델을](/windows/mixed-reality/gestures)에뮬레이트합니다.

   포커스는 응시 포인터를 사용하여 제어됩니다. *에어 탭* 제스처는 단추와 상호 작용하는 데 사용됩니다.

* *모션 컨트롤러:* VR 헤드셋과 함께 사용되는 모션 컨트롤러를 시뮬레이션합니다. 이 동작은 굴절형 손과의 원거리 상호 작용과 유사하게 작동합니다.

   컨트롤러 상호 작용 모델을 통해 VR 헤드셋을 에뮬레이트합니다.

   트리거, 잡기 및 메뉴 키는 키보드 및 마우스 입력을 통해 시뮬레이션됩니다.

### <a name="simulating-controller-movement"></a>컨트롤러 이동 시뮬레이션

**왼쪽/오른쪽 컨트롤러 조작** 키(기본값: 왼쪽 컨트롤러의 *경우 왼쪽 시프트,* 오른쪽 컨트롤러의 경우 *공간)를* 길게 눌러 두 컨트롤러 중 하나를 제어합니다. 조작 키를 누르는 동안 컨트롤러가 뷰포트에 표시됩니다. 조작 키가 해제되면 컨트롤러는 짧은 **컨트롤러 숨기기 시간 제한** 이후에 사라집니다.

[입력 시뮬레이션 도구 창에서](#input-simulation-tools-window) 카메라를 기준으로 컨트롤러를 설정/고정하거나 **왼쪽/오른쪽 컨트롤러 키** 설정/(기본값: 왼쪽의 경우 *T,* 오른쪽의 *경우 Y)을* 눌러 컨트롤러를 설정/고정할 수 있습니다. 토글 키를 다시 눌러 컨트롤러를 다시 숨깁니다. 컨트롤러를 조작하려면 **왼쪽/오른쪽 컨트롤러 조작 키를** 보유해야 합니다. **왼쪽/오른쪽 컨트롤러 조작 키를** 두 번 탭하면 컨트롤러를 켜고 끌 수도 있습니다.

마우스 이동은 보기 평면에서 컨트롤러를 이동합니다. **컨트롤러는 마우스 휠** 을 사용하여 카메라로 더 이동하거나 더 가깝게 이동할 수 있습니다.

마우스를 사용하여 컨트롤러를 회전하려면 **왼쪽/오른쪽 컨트롤러 조작 키(왼쪽** *시프트* 또는 *공간)와* 컨트롤러 회전  단추(기본값: *왼쪽 Ctrl* 단추)를 모두 누른 다음 마우스를 이동하여 컨트롤러를 회전합니다.  컨트롤러 회전 속도는 입력 시뮬레이션 프로필에서 **마우스 컨트롤러 회전 속도** 설정을 변경하여 구성할 수 있습니다.

손을 기본값으로 다시 설정하는 것을 포함하여 [입력 시뮬레이션 도구 창에서](#input-simulation-tools-window)모든 손 배치를 변경할 수도 있습니다.

### <a name="additional-profile-settings"></a>추가 프로필 설정

* **컨트롤러 깊이 승수는** 마우스 스크롤 휠 깊이 이동의 민감도를 제어합니다. 숫자가 클수록 컨트롤러 확대/축소 속도가 빨라질 수 있습니다.
* **기본 컨트롤러 거리는** 카메라에서 컨트롤러의 초기 거리입니다. **다시 설정** 단추 컨트롤러를 클릭하면 컨트롤러도 이 거리에 배치됩니다.
* **컨트롤러 지터 양은** 컨트롤러에 임의 동작을 추가합니다. 이 기능은 디바이스에서 부정확한 컨트롤러 추적을 시뮬레이션하고 노이즈 입력과 상호 작용이 제대로 작동하는지 확인하는 데 사용할 수 있습니다.

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a>손 제스처

손가락 모으기, 잡기, poking 등과 같은 손 제스처도 시뮬레이션할 수 있습니다.

1. **왼쪽/오른쪽 컨트롤러 조작 키(왼쪽** *시프트* 또는 *공간)를* 사용하여 손 컨트롤 사용

2. 조작하는 동안 마우스 단추를 길게 눌러 손 제스처를 수행합니다.

각 마우스 단추를 매핑하여 *왼쪽/가운데/오른쪽 마우스 손* 제스처 설정을 사용하여 손 모양을 다른 제스처로 변환할 수 있습니다. *기본 손 제스처는* 단추를 누르지 않은 경우 손 모양입니다.

> [!NOTE]
> *손가락 모으기* 제스처는 이 시점에서 "선택" 작업을 수행하는 유일한 제스처입니다.

### <a name="one-hand-manipulation"></a>일회용 조작

1. **왼쪽/오른쪽 컨트롤러 조작 키(왼쪽** *시프트* 또는 *공간)를* 길게 누르고 있습니다.
2. 개체를 가리킵니다.
3. 마우스 단추를 눌러 손가락 모으기
4. 마우스를 사용하여 개체 이동
5. 마우스 단추를 놓아 상호 작용 중지

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a>양손 조작

두 손으로 동시에 개체를 조작하는 경우 영구 손 모드를 사용하는 것이 좋습니다.

1. 토글 키(*T/Y*)를 눌러 두 손을 전환합니다.
1. 한 번에 한 손으로 조작:
    1. 오른쪽을 제어 하기 위한 **공간** 보유
    1. 개체를 가져올 위치로 손 모양 이동
    1. **마우스 왼쪽 단추** 를 클릭 하 여 *손가락* 제스처를 활성화 합니다.
    1. 오른쪽의 제어를 중지 하는 **공간** 을 해제 합니다. 이 손을 고정 하 고 더 이상 조작 되지 않으므로 *손가락* 을 끄는 제스처로 잠깁니다.
1. 또 다른 위치에서 동일한 개체를 사용 하 여 프로세스를 반복 합니다.
1. 이제 두 손을 모두 동일한 개체를 잡기 때문에 두 항목 중 하나를 이동 하 여 두 번의 조작을 수행할 수 있습니다.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a>GGV (응시, 제스처 및 음성) 상호 작용

기본적으로 GGV 상호 작용은-편집기에서 사용 하도록 설정 되지만, 장면에는 구분 되지 않는 손으로 표시 되지 않습니다.

1. 카메라를 회전 하 여 응시 커서가 interactable 개체 (마우스 오른쪽 단추)를 가리키도록 합니다.
1. **마우스 왼쪽 단추** 를 클릭 하 여 상호 작용
1. 카메라를 다시 회전 하 여 개체를 조작 합니다.

입력 시뮬레이션 프로필 내에서 *직접 사용 가능 입력 사용* 옵션을 설정/해제 하 여이 옵션을 해제할 수 있습니다.

또한 시뮬레이션 된 손을 GGV 상호 작용에 사용할 수 있습니다.

1. **손으로 시뮬레이션 모드** 를 [입력 시뮬레이션 프로필](#enabling-the-input-simulation-service) 의 *제스처로* 전환 하 여 GGV 시뮬레이션 사용
1. 카메라를 회전 하 여 응시 커서가 interactable 개체 (마우스 오른쪽 단추)를 가리키도록 합니다.
1. 오른쪽을 제어 하기 위한 **공간** 보유
1. **마우스 왼쪽 단추** 를 클릭 하 여 상호 작용
1. 마우스를 사용 하 여 개체 이동
1. 마우스 단추를 놓으면 상호 작용 중지

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a>텔레포트 이벤트 발생

입력 시뮬레이션에서 텔레포트 이벤트를 발생 시키려면 입력 시뮬레이션 프로필에서 손 제스처 설정 구성 하 고 다른 하나는 텔레포트 **종료** 제스처를 수행 하는 동안 **텔레포트 시작** 제스처를 수행 하도록 합니다. 텔레포트 **시작** 제스처는 텔레포트 포인터를 표시 하 고, **텔레포트 End** gesure은 텔레포트 작업을 완료 하 고 사용자를 이동 합니다.

결과 텔레포트의 y 위치는 y 축을 따라 카메라의 변위에 따라 결정 됩니다. 편집기에서이는 기본적으로 0 이므로 **Q** 및 **E** 키를 사용 하 여 적절 한 높이로 조정 합니다.

![입력 시뮬레이션 텔레포트 설정](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a>동작 컨트롤러 상호 작용

시뮬레이션 된 동작 컨트롤러는 동일한 방식으로 조작할 수 있습니다. 상호 작용 모델은 트리거, 잡기 및 메뉴 키가 각각 *왼쪽 마우스 단추*, *G* 및 *M* 키에 매핑되는 동안 트레일러 식의 먼 상호 작용과 비슷합니다.

### <a name="eye-tracking"></a>시선 추적

[입력 시뮬레이션 프로필](#enabling-the-input-simulation-service)에서 **눈 위치 시뮬레이트** 옵션을 선택 하 여 [눈동자 추적 시뮬레이션](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) 을 사용 하도록 설정할 수 있습니다. 이는 GGV 또는 모션 컨트롤러 스타일 상호 작용에 사용 하면 안 됩니다. 따라서 **기본 컨트롤러 시뮬레이션 모드가** *트레일러* 식으로 설정 되어 있어야 합니다.

## <a name="input-simulation-tools-window"></a>입력 시뮬레이션 도구 창

**혼합 현실**  >  **Toolkit**  >  **유틸리티**  >  **입력 시뮬레이션** 메뉴에서 입력 시뮬레이션 도구 창을 사용 하도록 설정 합니다. 이 창에서는 재생 모드 동안 입력 시뮬레이션의 상태에 액세스할 수 있습니다.

## <a name="viewport-buttons-optional"></a>뷰포트 단추 (선택 사항)

기본 수동 배치를 제어 하는 편집기 내 단추의 prefab은 **표시기 prefab** 의 입력 시뮬레이션 프로필에 지정할 수 있습니다. 이 유틸리티는 선택적 유틸리티 이며 [입력 시뮬레이션 도구 창](#input-simulation-tools-window)에서 동일한 기능에 액세스할 수 있습니다.

> [!NOTE]
> 뷰포트 표시기는 현재 Unity UI 상호 작용을 방해할 수 있으므로 기본적으로 사용 하지 않도록 설정 되어 있습니다. 문제 [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)를 참조 하세요. 을 사용 하도록 설정 하려면 InputSimulationIndicators prefab를 **표시기 prefab** 에 추가 합니다.

손 아이콘은 시뮬레이트된 바늘의 상태를 표시 합니다.

* ![추적 되지 않은 손 모양 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) 이는 추적 되지 않습니다. 손으로 활성화 하려면 클릭 합니다.
* ![추적 된 손 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "추적 된 손 아이콘") 이 손을 추적 하지만 사용자가 제어 하지는 않습니다. 손을 숨기려면 클릭 합니다.
* ![제어 된 손 모양 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "제어 된 손 모양 아이콘") 사용자가 직접 추적 하 고 제어 합니다. 손을 숨기려면 클릭 합니다.
* ![손 모양 다시 설정 아이콘](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "손 모양 다시 설정 아이콘") 손 모양을 기본 위치로 다시 설정 하려면 클릭 합니다.


## <a name="see-also"></a>추가 정보

* [입력 시스템 프로필](../input/input-providers.md)입니다.
