---
title: Leap Motion 사용
description: Leap Motion에 대해 구성할 설명서
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Leap Motion,
ms.openlocfilehash: 3ddf039f8409022d8aa2e425c46cd4d47ede16a0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176515"
---
# <a name="using-leap-motion"></a>Leap Motion 사용

이 데이터 공급자를 사용하려면 [Leap Motion Controller가](https://www.ultraleap.com/product/leap-motion-controller/) 필요합니다.

Leap Motion Data Provider VR에 대한 연속된 손 추적을 지원하며 편집기에서 신속한 프로토타이핑에 유용할 수 있습니다.  데이터 공급자는 헤드셋에 탑재된 Leap Motion Controller를 사용하거나 데스크에 탑재되도록 구성할 수 있습니다.

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

이 공급자는 독립 실행형 플랫폼에 있는 동안 편집기 및 디바이스에서 사용할 수 있습니다.  UWP 플랫폼에 있는 동안에는 편집기에서 사용할 수 있지만 UWP 빌드에서는 사용할 수 없습니다.

| MRTK 버전 | Leap Motion Unity 모듈 버전 지원됨 |
| --- | --- |
|2.6.x | 4.5.0, 4.5.1|
|2.7.x| 4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>MRTK에서 Leap Motion(Ultraleap) 손 추적 사용

1. MRTK 및 Leap Motion Unity 모듈 가져오기
    - 최신 [Leap Motion SDK가](https://developer.leapmotion.com/releases/?category=orion) 아직 설치되지 않은 경우 설치
    - **Microsoft.MixedReality.Toolkit 가져옵니다. Unity** 프로젝트에 대한 Foundation 패키지입니다.
    - 최신 버전의 Leap Motion [Unity 모듈을](https://developer.leapmotion.com/unity) 다운로드하여 프로젝트로 가져오기
        - Unity 모듈 **내에서만 Core** 패키지 가져오기

1. MRTK와 Leap Motion Unity 모듈 통합
    - Unity 모듈이 프로젝트에 있는 후 **Mixed Reality Toolkit**  >  **Leap Motion** 통합 Leap Motion Unity  >  **모듈로 이동합니다.**
    > [!NOTE]
    > Unity 모듈을 MRTK에 통합하는 경우 프로젝트에 10개의 어셈블리 정의가 추가되고 **Microsoft.MixedReality.Toolkit 대한 참조가 추가됩니다. Providers.LeapMotion** 어셈블리 정의입니다. Visual Studio를 닫습니다.

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. Leap Motion Data Provider 추가
    - 새 Unity 장면 만들기
    - **장면에** 추가 및 구성 Mixed Reality Toolkit 이동하여 MRTK를  >  **장면에 추가합니다.**
    - 계층 구조에서 MixedRealityToolkit 게임 개체를 선택하고 **복사 및 사용자 지정을** 선택하여 기본 혼합 현실 프로필을 복제합니다.

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - **입력** 구성 프로필 선택

    ![입력 구성 프로필 1](../images/cross-platform/InputConfigurationProfile.png)

    - 입력 시스템 프로필에서 **복제를** 선택하여 수정을 사용하도록 설정합니다.

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - 입력 **데이터 공급자 섹션을** 열고 맨 위에서 **Data Provider 추가를** 선택하면 목록 끝에 새 데이터 공급자가 추가됩니다.  새 데이터 공급자를 열고 **형식을** **Microsoft.MixedReality.Toolkit 설정합니다. LeapMotion.Input > LeapMotionDeviceManager**

    ![Leap Add Data Provider](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - **복제를** 선택하여 기본 Leap Motion 설정을 변경합니다.

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - Leap Motion Data Provider Leap Motion `LeapControllerOrientation` Controller의 위치인 속성을 포함합니다. `LeapControllerOrientation.Headset` 는 컨트롤러가 헤드셋에 탑재되었음을 나타냅니다. `LeapControllerOrientation.Desk` 는 컨트롤러가 데스크에 평면으로 배치되었음을 나타냅니다. 기본값은 로 `LeapControllerOrientation.Headset` 설정됩니다.
    - 각 컨트롤러 방향에는 오프셋 속성이 포함됩니다.
      - **헤드셋** 방향 오프셋 속성은 LeapXRServiceProvider 구성 요소의 오프셋 속성을 미러합니다.  `LeapVRDeviceOffsetMode`에는 기본, 수동 헤드 오프셋 및 변환의 세 가지 옵션이 있습니다.  오프셋 모드가 Default이면 Leap Motion Controller에 오프셋이 적용되지 않습니다.  수동 헤드 오프셋 모드에서는 , 및 의 세 가지 속성을 수정할 수 `LeapVRDeviceOffsetY` `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` 있습니다.  그런 다음 축 오프셋 속성 값이 기본 컨트롤러 배치에 적용됩니다.  변환 오프셋 모드에는 `LeapVRDeviceOrigin` Leap Motion Controller의 새 원점이 지정되는 Transform 속성이 포함되어 있습니다.
      - **Desk** 방향에는 `LeapControllerOffset` 데스크 윤손의 앵커 위치를 정의하는 속성이 포함되어 있습니다.  오프셋은 주 카메라 위치를 기준으로 계산되며, 기본값은 (0,-0.2, 0.35)이며, 카메라가 전면 및 보기에 표시되도록 합니다.

        > [!NOTE]
        > 애플리케이션이 시작될 때 프로필의 오프셋 속성이 한 번 적용됩니다.  런타임 중에 값을 수정하려면 Leap Motion 디바이스 관리자에서 Leap Motion Service 공급자를 받습니다.
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` 및 `ExitPinchDistance` 는 손가락 모으기/에어 탭 제스처 감지에 대한 거리 임계값입니다.  손가락 모으기 제스처는 인덱스 손가락 팁과 엄지 팁 사이의 거리를 측정하여 계산됩니다.  입력 다운 이벤트에서 를 발생시키기 위해 `EnterPinchDistance` 기본값은 0.02로 설정됩니다.  입력 시 을 발생시키기 위해(손가락 모으기 종료) 인덱스 손가락 팁과 엄지 팁 사이의 기본 거리는 0.05입니다.

    `LeapControllerOrientation`: 헤드셋(기본값) |  `LeapControllerOrientation`: Desk
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. Leap Motion Data Provider 테스트
    - Leap Motion Data Provider 입력 시스템 프로필에 추가된 후 재생을 누르고, Leap Motion Controller 앞에서 손을 움직이면 손의 공동 표현이 표시됩니다.

1. 프로젝트 빌드
    - 파일 **> 빌드 설정** 이동합니다.
    - Leap Motion Data Provider 사용하는 경우 독립 실행형 빌드만 지원됩니다.
    - 독립 실행형 빌드에 Windows Mixed Reality 헤드셋을 사용하는 방법에 대한 지침은 [WMR 헤드셋(독립 실행형)에 MRTK 빌드 및 배포를 참조하세요.](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)

## <a name="getting-the-hand-joints"></a>손 조인트 얻기

Leap Motion Data Provider 사용하여 조인을 가져오는 것은 MRTK에 대한 손 공동 검색과 동일합니다.  자세한 내용은 [손 추적을](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)참조하세요.

Unity 장면에 MRTK가 있고 Leap Motion Data Provider 입력 시스템 프로필에 입력 Data Provider 추가된 경우 빈 게임 개체를 만들고 다음 예제 스크립트를 연결합니다.

이 스크립트는 Leap Motion Hand에서 손만의 자세를 검색하는 방법의 간단한 예입니다.  구는 왼쪽 윤면 뒤에, 큐브는 오른쪽 윤을 따릅니다.

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a>Unity 편집기 워크플로 팁

Leap Motion Data Provider 사용하려면 VR 헤드셋이 필요하지 않습니다.  MRTK 앱에 대한 변경 내용은 헤드셋 없이 Leap hands를 사용하여 편집기에서 테스트할 수 있습니다.

LEAP Motion Hands는 VR 헤드셋을 연결하지 않고 편집기에서 표시됩니다.  가 `LeapControllerOrientation` **헤드셋** 로 설정된 경우 Leap Motion 컨트롤러는 카메라를 앞으로 향하여 한 손으로 보유해야 합니다.

> [!NOTE]
> 편집기에서 WASD 키를 사용하여 카메라를 이동하고 `LeapControllerOrientation` 헤드셋인 경우 손은 카메라를 따르지 않습니다.  은 `LeapControllerOrientation` **헤드셋으로** 설정된 동안 VR 헤드셋이 연결된 경우에만 카메라 이동을 따릅니다.  이 Desk 로 설정된 경우 Leap 손은 편집기에서 카메라 이동을 `LeapControllerOrientation` 따릅니다. 

## <a name="removing-leap-motion-from-the-project"></a>Project Leap Motion 제거

1. **Mixed Reality Toolkit**  >  **Leap Motion** 별도  >  **Leap Motion Unity 모듈로 이동합니다.**
    - Microsoft.MixedReality.Toolkit Unity를 참조로 새로 고치도록 **합니다. Providers.LeapMotion.asmdef** 파일은 이 단계에서 수정됩니다.
1. Unity 닫기
1. Visual Studio 닫습니다(열려 있는 경우).
1. 파일 탐색기 열고 MRTK Unity 프로젝트의 루트로 이동합니다.
    - **UnityProjectName/Library** 디렉터리 삭제
    - **UnityProjectName/Assets/Plugins/LeapMotion** 디렉터리를 삭제합니다.
    - **UnityProjectName/Assets/Plugins/LeapMotion.meta** 파일을 삭제합니다.
1. Unity 다시 열기

Unity 2018.4에서는 라이브러리 및 Leap Motion Core 자산을 삭제한 후에도 콘솔에 오류가 남아 있음을 알 수 있습니다.
다시 연 후 오류가 기록되면 Unity를 다시 시작합니다.

## <a name="common-errors"></a>일반 오류

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Leap Motion이 MRTK와 통합되지 않았습니다.

도약 동작 Unity 모듈이 MRTK와 통합 되었는지 테스트 하려면 다음을 수행 합니다.

- **혼합 현실 Toolkit > 유틸리티 > Leap 동작 > 통합 상태 확인** 으로 이동 합니다.
  - 그러면 Leap 동작 Unity 모듈이 MRTK와 통합 되었는지 여부에 대 한 메시지가 포함 된 팝업 창이 표시 됩니다.
- 메시지에 자산이 통합 되지 않은 것으로 표시 되 면 다음을 수행 합니다.
  - Leap 동작 Unity 모듈이 프로젝트에 있는지 확인 합니다.
  - 추가 된 버전이 지원 되는지 확인 하십시오. 지원 되는 버전은 페이지 맨 위에 있는 표를 참조 하세요.
  - **혼합 현실 Toolkit > 유틸리티 > >** leap 동작을 사용해 보세요.

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>어셈블리 멀티 플레이 HLAPI 복사 실패

Leap 동작 Unity 코어 자산의 가져오기 시이 오류가 기록 될 수 있습니다.

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**해결 방법**

- 단기 솔루션은 Unity를 다시 시작 하는 것입니다. 자세한 내용은 [문제 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 을 참조 하세요.

## <a name="leap-motion-example-scene"></a>윤 동작 예제 장면

예제 장면에서는 DefaultLeapMotionConfiguration 프로필을 사용 하 고 Unity 프로젝트가 Leap Data Provider 동작을 사용 하도록 올바르게 구성 되었는지 여부를 확인 합니다.

예제 장면이 Toolkit MixedReality에 포함 되어 있습니다. **** **Mrtk/예제/데모/수동 추적/** 디렉터리의 예제 패키지입니다.  

## <a name="see-also"></a>참조

- [입력 공급자](../features/input/input-providers.md)
- [수동 추적](../features/input/hand-tracking.md)
