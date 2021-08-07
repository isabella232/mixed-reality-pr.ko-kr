---
title: Unity의 제스처
description: XR 및 일반 단추 및 축 Api를 사용 하 여 손으로 입력 하는 손으로 Unity에서 작업을 수행 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 제스처, unity, 응시, 입력, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, 혼합 현실 Toolkit
ms.openlocfilehash: 8dd6b64dd0bb52e64515a43d69713ecc5dc6bcec203a987568f7c25ac492a864
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214781"
---
# <a name="gestures-in-unity"></a>Unity의 제스처

HoloLens 및 몰입 형 HMD에서 Unity, [손 제스처](../../design/gaze-and-commit.md#composite-gestures) 및 [동작 컨트롤러](../../design/motion-controllers.md) 의 [응시](gaze-in-unity.md)에서 작업을 수행 하는 두 가지 주요 방법이 있습니다. Unity에서 동일한 Api를 통해 두 공간 입력 원본에 대 한 데이터에 액세스할 수 있습니다.

Unity는 Windows Mixed Reality에 대 한 공간 입력 데이터에 액세스 하는 두 가지 기본 방법을 제공 합니다. 일반적인 *입력. getbutton/Input. getbutton* api는 여러 Unity XR sdk에서 작동 하 고, Windows Mixed Reality 관련 된 *InteractionManager/GestureRecognizer* api는 전체 공간 입력 데이터 집합을 노출 합니다.

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>상위 수준 복합 제스처 Api (GestureRecognizer)

**네임 스페이스:** *unityengine. XR*<br>
**유형**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

앱은 공간 입력 소스, 탭, 유지, 조작 및 탐색 제스처에 대 한 상위 수준 복합 제스처를 인식할 수도 있습니다. GestureRecognizer를 사용 하 여 [직접](../../design/gaze-and-commit.md#composite-gestures) 및 [동작 컨트롤러](../../design/motion-controllers.md) 에서 이러한 복합 제스처를 인식할 수 있습니다.

GestureRecognizer의 각 제스처 이벤트는 입력에 대 한 SourceKind와 이벤트 시점의 대상 헤드 광선을 제공 합니다. 일부 이벤트는 추가 컨텍스트별 정보를 제공 합니다.

제스처 인식기를 사용 하 여 제스처를 캡처하는 데 필요한 몇 가지 단계만 있습니다.
1. 새 제스처 인식기 만들기
2. 감시할 제스처 지정
3. 이러한 제스처에 대 한 이벤트 구독
4. 제스처 캡처 시작

### <a name="create-a-new-gesture-recognizer"></a>새 제스처 인식기 만들기

*GestureRecognizer* 를 사용 하려면 *GestureRecognizer* 를 만들어야 합니다.

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>감시할 제스처 지정

*SetRecognizableGestures ()* 를 통해 관심 있는 제스처를 지정 합니다.

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>이러한 제스처에 대 한 이벤트 구독

관심이 있는 제스처에 대 한 이벤트를 구독 합니다.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>탐색 및 조작 제스처는 *GestureRecognizer* 의 인스턴스에서 함께 사용할 수 없습니다.

### <a name="start-capturing-gestures"></a>제스처 캡처 시작

기본적으로 *GestureRecognizer* 는 *Startcapturinggestures ()* 를 호출할 때까지 입력을 모니터링 하지 않습니다. *Stopcapturinggestures ()* 가 처리 된 프레임 보다 먼저 입력이 수행 되 면 *Stopcap의 ing제스처 ()* 가 호출 된 후에 제스처 이벤트가 생성 될 수 있습니다. *GestureRecognizer* 는 제스처가 실제로 발생 한 이전 프레임의 설정 또는 해제 여부를 기억할 것 이므로이 프레임의 응시 대상에 따라 제스처 모니터링을 시작 하 고 중지 하는 것은 안정적입니다.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>제스처 캡처 중지

제스처 인식을 중지 하려면:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>제스처 인식기 제거

*GestureRecognizer* 개체를 삭제 하기 전에 구독 이벤트의 구독을 취소 해야 합니다.

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Unity에서 동작 컨트롤러 모델 렌더링

![동작 컨트롤러 모델 및 teleportation](images/motioncontrollertest-teleport-1000px.png)<br>
*동작 컨트롤러 모델 및 teleportation*

응용 프로그램에서 사용자가 보유 하 고 있는 실제 컨트롤러와 일치 하는 동작 컨트롤러를 렌더링 하려면 [혼합 현실 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/)에서 **motioncontroller prefab** 를 사용할 수 있습니다.  이 prefab는 시스템의 설치 된 동작 컨트롤러 드라이버에서 런타임에 올바른 인 글 Tf 모델을 동적으로 로드 합니다.  편집기에서 수동으로 가져오는 대신 이러한 모델을 동적으로 로드 하는 것이 중요 합니다. 따라서 앱은 사용자에 게 있을 수 있는 현재 및 미래의 모든 컨트롤러에 대해 물리적으로 정확한 3D 모델을 표시 합니다.

1. [시작](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 지침에 따라 혼합 현실 Toolkit 다운로드 하 여 Unity 프로젝트에 추가 합니다.
2. 시작 단계의 일부로 카메라를 *MixedRealityCameraParent* prefab로 대체 한 경우에는 계속 진행 하는 것이 좋습니다.  이 prefab에는 동작 컨트롤러 렌더링이 포함 됩니다.  그렇지 않으면 Project 창에서 장면에 *자산/HoloToolkit/Input/Prefabs/motioncontrollers. prefab* 를 추가 합니다.  사용자가 장면 내에서 teleports 때 카메라를 이동 하는 데 사용 하는 모든 부모 개체의 자식으로 해당 prefab을 추가 하 여 컨트롤러를 사용자와 함께 사용할 수 있습니다.  앱이 teleporting를 포함 하지 않는 경우 장면의 루트에 prefab를 추가 합니다.

## <a name="throwing-objects"></a>개체 throw

가상 현실에서 개체를 throw 하는 것은 처음에 보이는 것 보다 더 어려운 문제입니다. 대부분의 물리적 기반 상호 작용의 경우와 마찬가지로 게임에서 throw 되는 것이 예기치 않은 방식으로 작동 하는 경우에는 즉시 명확 하 고 집중 교육 중단 됩니다. 실제로 올바른 throw 동작을 나타내는 방법에 대해 자세히 살펴보고, 플랫폼 업데이트를 통해 사용할 수 있는 몇 가지 지침을 제공 하 여 사용자와 공유 하 고 싶습니다.

[여기](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)에서 throw를 구현 하는 방법에 대 한 예제를 찾을 수 있습니다. 이 샘플은 다음 네 가지 지침을 따릅니다.
* **위치 대신 컨트롤러의 *속도* 를 사용** 합니다. Windows 11 월 업데이트에서 [' ' 근사치 ' ' 위치 추적 상태](../../design/motion-controllers.md#controller-tracking-state)에 있는 경우 동작이 변경 되었습니다. 이 상태에서 컨트롤러에 대 한 속도 정보는 높은 정확도를 기대 하는 동안에도 계속 보고 됩니다 .이는 일반적으로 위치가 높은 정확도를 유지 합니다.
* **컨트롤러의 *각도 속도* 를 통합** 합니다. 이 논리는 `throwing.cs` `GetThrownObjectVelAngVel` 위에 링크 된 패키지 내의 정적 메서드에 있는 파일에 모두 포함 됩니다.
   1. 각도 속도가 conserved throw 된 개체는 throw 시점에 있었던 것과 동일한 각도의 속도를 유지 해야 합니다. `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Throw 된 개체의 질량 중심은 그립 포즈의 원점에 있지 않을 수 있으므로 사용자 참조 프레임의 컨트롤러와 다른 속도를 가질 가능성이 높습니다. 이러한 방식으로 제공 되는 개체 속도의 부분은 컨트롤러 원본 주위에서 throw 된 개체의 질량 중심의 순간 탄젠트 속도입니다. 이 탄젠트 속도는 컨트롤러 원본 및 throw 된 개체의 질량 중심 사이의 거리를 나타내는 벡터와 컨트롤러의 각도 속도 간 곱입니다.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. Throw 된 개체의 총 속도는 컨트롤러의 속도와 이러한 탄젠트 속도의 합입니다. `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **속도를 적용 하는 *시간* 에 대 한 주의를** 기울여야 합니다. 단추를 누르면 해당 이벤트에서 운영 체제에 대 한 Bluetooth까지 버블링 하는 데 최대 20 밀리초까지 걸릴 수 있습니다. 이는 컨트롤러 상태 변경을 누른 상태에서 누르지 않음으로 또는 다른 방법으로 변경 하는 것을 폴링하는 경우 발생 하는 컨트롤러의 상태에 대 한 이러한 변경 내용에 대 한 정보를 얻을 수 있습니다. 또한 폴링 API에 의해 표시 되는 컨트롤러는 프레임이 표시 될 때, 향후 20 밀리초를 초과할 수 있는 포즈를 반영 하는 것으로 예상 됩니다. 이는 보류 중인 개체를 *렌더링* 하는 데 유용 하지만, 사용자가 throw를 릴리스한 순간의 궤적을 계산할 때 개체를 *대상으로 지정* 하는 데 시간이 복합어. 다행히 11 월 업데이트를 사용 하는 경우 *InteractionSourcePressed* 또는 *InteractionSourceReleased* 와 같은 Unity 이벤트가 전송 되 면이 상태에는 단추를 눌렀다 놓았을 때의 기록 포즈 데이터가 반환 됩니다.  을 throw 하는 동안 가장 정확한 컨트롤러 렌더링과 컨트롤러를 대상으로 하려면 적절 한 폴링 및 이벤트를 올바르게 사용 해야 합니다.
   * 각 프레임을 렌더링 하는 **컨트롤러** 의 경우 응용 프로그램은 현재 프레임의 photon 시간에 대해 앞으로 예측 되는 컨트롤러에서 컨트롤러의 *GameObject* 위치를 지정 해야 합니다.  Unity 폴링 Api (예: XR)에서이 데이터를 가져옵니다 *[. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 또는 *[XR. WSA. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Press 또는 릴리스부터 **컨트롤러를 대상** 으로 하는 경우 앱은 해당 누르기 또는 릴리스 이벤트에 대 한 기록 컨트롤러의 포즈를 기준으로 궤적을 ray로 계산 해야 합니다.  *[InteractionManager InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* 와 같은 Unity 이벤트 api에서이 데이터를 가져옵니다.
* **그립 포즈를 사용** 합니다. Angular 속도와 속도는 포인터가 아닌 그립 포즈를 기준으로 보고 됩니다.

throw는 향후 Windows 업데이트를 계속 개선 하 고 여기에서 자세한 정보를 찾을 수 있습니다.

## <a name="gesture-and-motion-controllers-in-mrtk"></a>MRTK의 제스처 및 동작 컨트롤러

입력 관리자에서 제스처 및 동작 컨트롤러에 액세스할 수 있습니다.

* [MRTK의 제스처](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [MRTK의 동작 컨트롤러](/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a>안내 따르기

보다 자세한 사용자 지정 예제가 포함 된 단계별 자습서는 혼합 현실 아카데미에서 제공 됩니다.

- [MR 입력 211: 제스처](tutorials/holograms-211.md)
- [MR 입력 213: 모션 컨트롤러](../../deprecated/mixed-reality-213.md)

[![MR 입력 213-동작 컨트롤러](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*MR 입력 213-동작 컨트롤러*

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [손 및 시선 추적](./hand-eye-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목

* [헤드 게이즈 및 커밋](../../design/gaze-and-commit.md)
* [모션 컨트롤러](../../design/motion-controllers.md)