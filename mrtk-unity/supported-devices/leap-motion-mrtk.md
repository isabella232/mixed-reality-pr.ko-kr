---
title: 도약 동작 MRTK
description: Leap 동작을 구성 하는 설명서
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Leap 동작
ms.openlocfilehash: 285328b1248f04504f30192f1294e9ae665b3fc9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145190"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>MRTK에서 Ultraleap (Leap 동작) 수동 추적을 구성 하는 방법

이 데이터 공급자를 사용 하려면 [Leap 동작 컨트롤러가](https://www.ultraleap.com/product/leap-motion-controller/) 필요 합니다.

도약 동작 Data Provider는 VR에 대해 트레일러 식 추적을 사용할 수 있으며 편집기에서 빠른 프로토타입 생성에 유용할 수 있습니다.  데이터 공급자는 헤드셋에 탑재 된 Leap 모션 컨트롤러를 사용 하거나 책상 면에 배치 되도록 구성할 수 있습니다.

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

이 공급자는 독립 실행형 플랫폼에 있는 동안 편집기 및 장치에서 사용할 수 있습니다.  Uwp 플랫폼에서는 있지만 UWP 빌드에서는 사용 하지 않을 수도 있습니다.

|Leap 동작 Unity 모듈 버전 지원|
|---|
|4.5.0|
|4.5.1|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a>MRTK에서 윤 움직임 (Ultraleap) 직접 추적 사용

1. MRTK 및 Leap 동작 Unity 모듈 가져오기
    - [Leap 모션 SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) 설치 (아직 설치 되지 않은 경우)
    - Unity 프로젝트에 **MixedReality** 패키지를 가져옵니다.
    - 최신 버전의 [Leap 동작 Unity 모듈](https://developer.leapmotion.com/unity) 을 다운로드 하 여 프로젝트로 가져오기
        - Unity 모듈 내 에서만 **핵심** 패키지를 가져옵니다.

1. 도약 동작 Unity 모듈을 MRTK와 통합
    - Unity 모듈이 프로젝트에 있으면 **Mixed Reality Toolkit**  >  **leap 동작**  >  **통합 leap 동작 Unity 모듈** 로 이동 합니다.
    > [!NOTE]
    > Unity 모듈을 MRTK에 통합 하면 10 개의 어셈블리 정의가 프로젝트에 추가 되 고 **MixedReality. LeapMotion** 어셈블리 정의에 참조가 추가 됩니다. Visual Studio를 닫습니다.

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. Leap Motion Data Provider 추가
    - 새 Unity 장면 만들기
    - **Mixed Reality Toolkit** 장면에 추가 및 구성으로 이동하여 MRTK를  >  **장면에 추가합니다.**
    - 계층 구조에서 MixedRealityToolkit 게임 개체를 선택하고 **복사 및 사용자 지정을** 선택하여 기본 혼합 현실 프로필을 복제합니다.

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - **입력** 구성 프로필 선택

    ![입력 구성 프로필 1](../images/cross-platform/InputConfigurationProfile.png)

    - 입력 시스템 프로필에서 **복제를** 선택하여 수정을 사용하도록 설정합니다.

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - 입력 **데이터 공급자 섹션을** 열고 맨 위에서 **Data Provider 추가를** 선택하면 목록 끝에 새 데이터 공급자가 추가됩니다.  새 데이터 공급자를 열고 **Type을** **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager로** 설정합니다.

    ![Leap Add Data Provider](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - **복제를** 선택하여 기본 Leap Motion 설정을 변경합니다.

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - Leap Motion Data Provider Leap Motion `LeapControllerOrientation` Controller의 위치인 속성을 포함합니다. `LeapControllerOrientation.Headset` 는 컨트롤러가 헤드셋에 탑재되었음을 나타냅니다. `LeapControllerOrientation.Desk` 는 컨트롤러가 데스크에 평면으로 배치되었음을 나타냅니다. 기본값은 로 `LeapControllerOrientation.Headset` 설정됩니다.
    - 각 컨트롤러 방향에는 오프셋 속성이 포함됩니다.
      - **헤드셋** 방향 오프셋 속성은 LeapXRServiceProvider 구성 요소의 오프셋 속성을 미러합니다.  에는 `LeapVRDeviceOffsetMode` 기본, 수동 헤드 오프셋 및 변환의 세 가지 옵션이 있습니다.  오프셋 모드가 기본값 인 경우 오프셋은 윤 동작 컨트롤러에 적용 되지 않습니다.  수동 헤드 오프셋 모드에서는 세 가지 속성 `LeapVRDeviceOffsetY` , 및를 수정할 수 있습니다 `LeapVRDeviceOffsetZ` . `LeapVRDeviceTiltX`  그러면 축 오프셋 속성 값이 기본 컨트롤러 배치에 적용 됩니다.  변환 오프셋 모드에는 `LeapVRDeviceOrigin` 윤 동작 컨트롤러의 새 원본을 지정 하는 transform 속성이 포함 되어 있습니다.
      - **책상** 방향에는 `LeapControllerOffset` 책상 윤 바늘의 앵커 위치를 정의 하는 속성이 포함 되어 있습니다.  오프셋은 기본 카메라 위치를 기준으로 계산 되며, 기본 값은 (0,-0.2, 0.35)가 카메라의 앞과 뒤에 표시 되도록 합니다.

        > [!NOTE]
        > 프로필의 오프셋 속성은 응용 프로그램이 시작 될 때 한 번 적용 됩니다.  런타임 중에 값을 수정 하려면 Leap 동작 장치 관리자에서 Leap 모션 서비스 공급자를 가져옵니다.
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - `EnterPinchDistance` 및 `ExitPinchDistance` 는 하강/공기 탭 제스처 검색의 거리 임계값입니다.  손으로 만든 제스처는 인덱스 손가락 팁과 엄지 단추 사이의 거리를 측정 하 여 계산 됩니다.  입력 다운 이벤트를 발생 시키려면 기본값 `EnterPinchDistance` 은 0.02로 설정 됩니다.  입력 시 입력 이벤트를 발생 시키기 위해 (하강 종료) 인덱스 손가락 팁과 엄지 단추 사이의 기본 거리가 0.05입니다.

    `LeapControllerOrientation`: 헤드셋 (기본값) |  `LeapControllerOrientation`: 책상
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. 도약 동작 테스트 Data Provider
    - 입력 시스템 프로필에 도약 이동 Data Provider 추가 된 후 play를 누르고, 윤 동작 컨트롤러 앞으로 손을 이동 하 고, 바늘의 조인트 표현이 표시 되어야 합니다.

1. 프로젝트 빌드
    - **파일 > 빌드 설정** 으로 이동 합니다.
    - Data Provider Leap 동작을 사용 하는 경우 독립 실행형 빌드만 지원 됩니다.
    - 독립 실행형 빌드에 Windows Mixed Reality 헤드셋을 사용 하는 방법에 대 한 지침은 [MRTK (독립 실행형) 빌드 및 배포](wmr-mrtk.md#building-and-deploying-mrtk-standalone)를 참조 하세요.

## <a name="getting-the-hand-joints"></a>직접 조인트 가져오기

도약 동작 Data Provider를 사용 하 여 조인트를 가져오는 것은 MRTK에 대 한 직접 검색에 사용 하는 것과 동일 합니다.  자세한 내용은 [직접 추적](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)을 참조 하세요.

Unity 장면에서 MRTK를 사용 하 고 입력 시스템 프로필에 도약 동작을 입력 Data Provider로 추가 Data Provider 빈 게임 개체를 만들고 다음 예제 스크립트를 연결 합니다.

이 스크립트는 도약 동작에서 야자나무 조인트의 포즈를 검색 하는 방법의 간단한 예입니다.  구는 왼쪽 아래에 오는 반면, 정육면체는 오른쪽 윤 바늘을 따릅니다.

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

도약 동작 Data Provider를 사용 하는 경우에는 VR 헤드셋이 필요 하지 않습니다.  MRTK 앱에 대 한 변경 내용을 편집기에서 테스트 하 여 헤드셋 없이 Leap 손을 테스트할 수 있습니다.

Leap 운동 손을 편집기에 표시 하며,이는 VR 헤드셋이 연결 되어 있지 않습니다.  `LeapControllerOrientation`가 **헤드셋** 으로 설정 된 경우에는 윤 동작 컨트롤러를 카메라 앞으로 향하는 손을 사용 해야 합니다.

> [!NOTE]
> 편집기에서 WASD 키를 사용 하 여 카메라를 이동 하 고 `LeapControllerOrientation` 가 **헤드셋** 인 경우 손이 카메라를 따르지 않습니다. 가 헤드셋을 설정 하는 동안에는 VR 헤드셋이 연결 된 경우에만 카메라 이동이 진행 됩니다 `LeapControllerOrientation` .   `LeapControllerOrientation`가 **Desk** 로 설정 된 경우 Leap 손이 편집기에서 카메라 움직임을 따릅니다.

## <a name="removing-leap-motion-from-the-project"></a>프로젝트에서 Leap 동작 제거

1. **Mixed Reality Toolkit**  >  **Leap Motion** 별도의 Leap Motion Unity  >  **모듈로 이동합니다.**
    - **Unity를 Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** 파일의 참조로 새로 고치도록 합니다.
1. Unity 닫기
1. Visual Studio 닫습니다(열려 있는 경우).
1. 파일 탐색기 열고 MRTK Unity 프로젝트의 루트로 이동합니다.
    - **UnityProjectName/Library** 디렉터리 삭제
    - **UnityProjectName/Assets/Plugins/LeapMotion** 디렉터리를 삭제합니다.
    - **UnityProjectName/Assets/Plugins/LeapMotion.meta 파일을 삭제합니다.**
1. Unity 다시 열기

Unity 2018.4에서는 라이브러리 및 Leap Motion Core 자산을 삭제한 후에도 콘솔에 오류가 남아 있음을 알 수 있습니다.
다시 연 후 오류가 기록되면 Unity를 다시 시작합니다.

## <a name="common-errors"></a>일반 오류

### <a name="leap-motion-has-not-integrated-with-mrtk"></a>Leap Motion이 MRTK와 통합되지 않았습니다.

Leap Motion Unity 모듈이 MRTK와 통합되었는지 테스트하려면 다음을 수행합니다.

- Mixed Reality **Toolkit > 유틸리티 > Leap Motion > 통합 상태 확인으로** 이동합니다.
  - 그러면 Leap Motion Unity 모듈이 MRTK와 통합되었는지 여부에 대한 메시지가 포함된 팝업 창이 표시됩니다.
- 자산이 통합되지 않았다는 메시지가 표시됩니다.
  - Leap Motion Unity 모듈이 프로젝트에 있는지 확인합니다.
  - 추가된 버전이 지원되는지 확인합니다. 지원되는 버전은 페이지 맨 위에 있는 표를 참조하세요.
  - **Mixed Reality Toolkit > Utilities > Leap Motion > Integration Leap Motion Unity Modules** 사용해 보세요.

### <a name="copying-assembly-multiplayer-hlapi-failed"></a>어셈블리 다중 재생 HLAPI 복사 실패

Leap 동작 Unity 코어 자산의 가져오기 시이 오류가 기록 될 수 있습니다.

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

**해결 방법**

- 단기 솔루션은 Unity를 다시 시작 하는 것입니다. 자세한 내용은 [문제 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 을 참조 하세요.

## <a name="leap-motion-example-scene"></a>윤 동작 예제 장면

예제 장면에서는 DefaultLeapMotionConfiguration 프로필을 사용 하 고 Unity 프로젝트가 Leap Data Provider 동작을 사용 하도록 올바르게 구성 되었는지 여부를 확인 합니다.

예제 장면은 **Mrtk/example/데모/수동 추적/** 디렉터리의 **MixedReality** 패키지에 포함 되어 있습니다.  

## <a name="see-also"></a>참고 항목

-[입력 공급자](../features/input/input-providers.md) 
- [수동 추적](../features/input/hand-tracking.md)
