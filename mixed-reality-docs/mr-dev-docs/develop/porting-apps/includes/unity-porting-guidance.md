---
ms.openlocfilehash: 6c33618e6d09da156bc4a4480fbecf3c0da94378
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580576"
---
# <a name="project-settings"></a>[프로젝트 설정](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. 위에 나열 된 일반적인 포팅 단계를 검토 합니다.

위에 나열 된 일반적인 단계를 검토 하 여 개발 환경이 올바르게 설정 되었는지 확인 합니다. #3 단계에서 Visual Studio를 사용 하는 경우 Unity 워크 로드를 사용 하 여 **게임 개발** 을 선택 해야 합니다. 다음 단계에서 최신 버전의 Unity를 설치 하기 때문에 "Unity 편집기 옵션" 구성 요소를 선택 취소할 수 있습니다.

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. Windows MR 지원을 통해 Unity의 최신 공용 빌드로 업그레이드
1. 혼합 현실 지원을 통해 [Unity의 최신 권장 공용 빌드](../../install-the-tools.md) 를 다운로드 합니다.
2. 시작 하기 전에 프로젝트 복사본 저장
3. 프로젝트가 이전 버전의 Unity에서 빌드된 경우에는 Unity에서 제공 되는 [설명서](https://docs.unity3d.com/Manual/UpgradeGuides.html) 를 검토 하세요.
4. 자동 API 업데이트 프로그램을 사용 하기 위한 Unity 사이트의 [지침](https://docs.unity3d.com/Manual/APIUpdater.html) 을 따르세요.
5. 프로젝트를 실행 하기 위해 수행 해야 하는 추가 변경 내용이 있는지 확인 하 고 나머지 오류와 경고를 사용 하 여 작업 합니다. 

> [!Note] 
> 사용자가 사용 하는 미들웨어가 있는 경우 최신 릴리스를 사용 하 고 있는지 확인 합니다 (아래 3 단계에서 자세한 내용 참조).

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. 미들웨어를 최신 버전으로 업그레이드

모든 Unity 업데이트를 사용 하 여 게임 또는 응용 프로그램이 종속 된 하나 이상의 미들웨어 패키지를 업데이트 해야 할 가능성이 있습니다. 또한 최신 미들웨어를 최신 상태로 유지 하면 이식 프로세스의 나머지 부분에서 성공 가능성이 높아집니다.

### <a name="4-target-your-application-to-run-on-win32"></a>4. Win32에서 실행할 응용 프로그램을 대상으로 합니다.

Unity 응용 프로그램 내에서:

* 파일-> 빌드 설정으로 이동 합니다.
* "PC, Mac, Linux 독립 실행형"을 선택 합니다.
* 대상 플랫폼을 "Windows"로 설정 합니다.
* 아키텍처를 "x86" 선택 "플랫폼 전환"으로 설정

> [!NOTE] 
> 응용 프로그램에 스트림에서의 match와 같은 장치 관련 서비스에 대 한 종속성이 있는 경우이 단계에서 사용 하지 않도록 설정 해야 합니다. Windows에서 나중에 제공 하는 것과 동일한 서비스에 연결할 수 있습니다.

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. Windows Mixed Reality 하드웨어 설정
1. [모던 헤드셋 설정](/windows/mixed-reality/enthusiast-guide/before-you-start
) 의 단계 검토
2. [Windows Mixed reality 시뮬레이터를 사용 하](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 고 [windows mixed Reality 홈을 탐색](../../../discover/navigating-the-windows-mixed-reality-home.md) 하는 방법을 알아봅니다.

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. Windows Mixed Reality에서 실행할 응용 프로그램을 대상으로 합니다.
1. 먼저 특정 VR SDK와 관련 된 다른 모든 라이브러리 지원을 제거 하거나 조건부로 컴파일해야 합니다. 이러한 자산은 Windows Mixed Reality와 같이 다른 VR Sdk와 호환 되지 않는 방식으로 프로젝트의 설정 및 속성을 변경 하는 경우가 많습니다.
    * 예를 들어 프로젝트가 SteamVR SDK를 참조 하는 경우 Windows Mixed Reality와 SteamVR를 모두 지 원하는 Unity의 일반적인 VR Api를 대신 사용 하도록 프로젝트를 업데이트 해야 합니다.
    * 다른 VR Sdk를 조건부로 제외 하기 위한 구체적인 단계는 곧 제공 될 예정입니다.
2. Unity 프로젝트에서 [Windows 10 SDK를 대상으로 합니다](../../unity/tutorials/holograms-100.md#target-windows-10-sdk) .
3. 각 장면에 대해 [카메라를 설정 합니다](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera) .

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. 스테이지를 사용 하 여 바닥에 콘텐츠를 저장 합니다.

광범위 한 [환경 규모](../../../design/coordinate-systems.md)에서 혼합 현실 환경을 빌드할 수 있습니다.

통합 된 **환경을** 이식 하는 경우 Unity가 **고정** 된 추적 공간 종류로 설정 되었는지 확인 해야 합니다.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

위의 코드는 Unity의 세계 좌표계를 설정 하 여 [고정 된 참조 프레임](../../../design/coordinate-systems.md#spatial-coordinate-systems)을 추적 합니다. 고정 된 추적 모드에서 카메라의 기본 위치 바로 앞에 있는 편집기에 배치 된 콘텐츠 (앞으로-Z)는 앱이 시작 될 때 사용자 앞에 표시 됩니다. 사용자가 연결 된 원본을 recenter Unity의 XR를 호출할 수 있습니다 [. Recenter 메서드입니다.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

**대규모 환경이** 나 **공간 규모의 경험** 을 이식 하는 경우 층에 상대적인 콘텐츠를 배치 합니다. 사용자의 층을 사용 하는 이유는 사용자의 정의 된 최고 수준 원점 및 선택적 대화방 경계를 나타내는 **[공간 단계](../../../design/coordinate-systems.md#spatial-coordinate-systems)** 를 처음 실행 하는 동안 설정 하는 것입니다. 이러한 환경에서는 Unity가 **RoomScale** 추적 공간 형식으로 설정 되어 있는지 확인 해야 합니다. RoomScale가 기본값 이지만, 사용자가 보정 한 방에서 컴퓨터를 이동 하는 경우를 명시적으로 설정 하 고 true로 설정 하 여 사용자가 컴퓨터를 이동 하는 경우를 확인 하는 것이 좋습니다.

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

앱이 RoomScale 추적 공간 유형을 성공적으로 설정 하면 y = 0 평면에 배치 된 콘텐츠가 바닥에 표시 됩니다. (0, 0, 0)의 원점은 사용자가 대화방을 설치 하는 동안 구현 하는 바닥의 특정 위치가 되며,-Z는 설치 중에 전달 된 정방향 방향을 나타냅니다.

그런 다음 스크립트 코드에서 TryGetGeometry 메서드를 호출할 수 있습니다. XR 형식으로 경계 다각형을 가져오고 TrackedArea 경계 형식을 지정 합니다. 사용자가 경계를 정의 하는 경우 (꼭 짓 점 목록 다시 표시) 사용자에 게 **공간 확장 환경을** 제공 하 여 사용자가 만든 장면을 탐색할 수 있습니다.

사용자가 접근 하면 시스템에서 자동으로 경계를 렌더링 합니다. 앱은 경계 자체를 렌더링 하기 위해이 다각형을 사용할 필요가 없습니다.

자세한 내용은 [Unity의 좌표계](../../unity/coordinate-systems-in-unity.md) 페이지를 참조 하세요.

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

결과의 예는 다음과 같습니다.

![결과 예제](../../porting-apps/images/largestrectangle-400px.jpg)

알고리즘은 Daniel Smilkov의 블로그를 기반으로 합니다. [다각형의 가장 큰 사각형](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="8-work-through-your-input-model"></a>8. 입력 모델을 통해 작업

기존 HMD를 대상으로 하는 각 게임 또는 응용 프로그램에는 처리 하는 일련의 입력, 환경에 필요한 입력 형식 및 해당 입력을 가져오기 위해 호출 하는 특정 Api가 있습니다. Windows Mixed Reality에서 제공 되는 입력을 활용할 수 있도록 간단 하 고 간단 하 게 만드는 데 투자 했습니다.

Windows Mixed Reality에서 입력을 노출 하는 방법 및 응용 프로그램의 용도에 매핑되는 방법에 대 한 자세한 내용은 인접 탭의 [Unity에 대 한 입력 포팅 가이드](../porting-guides.md?tabs=input) 를 참조 하세요.

### <a name="9-performance-testing-and-tuning"></a>9. 성능 테스트 및 튜닝

Windows Mixed Reality는 하이엔드 게임 Pc부터 광범위 한 시장 메인스트림 Pc까지 광범위 한 장치 클래스에서 사용할 수 있습니다. 대상으로 지정 하는 시장에 따라 응용 프로그램에 사용할 수 있는 계산 및 그래픽 예산에 상당한 차이가 있습니다. 이 포팅 연습을 수행 하는 동안 프리미엄 PC를 활용 하 고 앱에 사용할 수 있는 중요 한 계산 및 그래픽 예산이 있을 수 있습니다. 앱을 더 광범위 한 사용자가 사용할 수 있도록 하려는 경우 [대상으로 지정 하려는 대표 하드웨어](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)에서 앱을 테스트 하 고 프로 파일링 해야 합니다.

[Unity](https://docs.unity3d.com/Manual/Profiler.html) 및 [Visual Studio](/visualstudio/profiling/index) 에는 성능 프로파일러가 포함 되며, [Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) 및 [Intel](https://software.intel.com/articles/vr-content-developer-guide) 은 성능 프로 파일링 및 최적화에 대 한 지침을 게시 합니다. [혼합 현실 성능을 이해](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)하는 데 사용할 수 있는 성능에 대 한 광범위 한 설명이 있습니다. Unity에 [대 한 성능 권장 사항](../../unity/performance-recommendations-for-unity.md)에서 unity에 대 한 구체적인 정보를 제공 합니다.

# <a name="input-mapping"></a>[입력 매핑](#tab/input)

Unity의 일반 입력의 두 방법 중 하나를 사용 하 여 입력 논리를 Windows Mixed Reality로 이식할 수 있습니다. 여러 플랫폼에 걸쳐 있는 GetButton/Getbutton Api 또는 Windows 별 XR. WSA. 동작 컨트롤러 및 HoloLens 바늘에 대해 구체적으로 다양 한 데이터를 제공 하는 입력 Api

> [!IMPORTANT]
> HP 반향 G2 컨트롤러를 사용 하는 경우 추가 입력 매핑 지침은 [이 문서](../../unity/unity-reverb-g2-controllers.md) 를 참조 하세요.

## <a name="unity-xr-input-apis"></a>Unity XR 입력 Api

새 프로젝트의 경우 처음부터 새 XR 입력 Api를 사용 하는 것이 좋습니다. 

[XR api](https://docs.unity3d.com/Manual/xr_input.html)에 대 한 자세한 내용은 여기에서 찾을 수 있습니다.

## <a name="inputgetbuttongetaxis-apis"></a>입력. GetButton/Getbutton Api

Unity는 현재 일반 입력을 사용 합니다. GetButton/Input. Getbutton Api를 사용 하 여 [Oculus sdk](https://docs.unity3d.com/Manual/OculusControllers.html) 및 [openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html)의 입력을 노출 합니다. 앱이 입력에 이러한 Api를 이미 사용 하 고 있는 경우 Windows Mixed Reality에서 동작 컨트롤러를 지원 하기에 가장 쉬운 경로입니다. 입력 관리자에서 단추와 축을 다시 매핑해야 합니다.

자세한 내용은 [unity 단추/축 매핑 표](../../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 및 [일반적인 unity api 개요](../../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)를 참조 하세요.

## <a name="windows-specific-xrwsainput-apis"></a>Windows 관련 XR. WSA. 입력 Api

> [!CAUTION]
> 프로젝트에서 XR를 사용 하는 경우 WSA Api는 향후 Unity 릴리스의 XR SDK에 대 한 것입니다. 새 프로젝트의 경우 처음부터 XR SDK를 사용 하는 것이 좋습니다. [XR 입력 시스템 및 api](https://docs.unity3d.com/Manual/xr_input.html)에 대 한 자세한 내용은 여기에서 찾을 수 있습니다.

앱에서 각 플랫폼에 대 한 사용자 지정 입력 논리를 이미 빌드하는 경우 **XR** 네임 스페이스에서 Windows 관련 공간 입력 api를 사용 하도록 선택할 수 있습니다. 이렇게 하면 위치 정확도 나 원본 종류와 같은 추가 정보에 액세스할 수 있으므로 HoloLens와 컨트롤러를 따로 지시할 수 있습니다.

> [!NOTE]
> HP 반향 G2 컨트롤러를 사용 하는 경우 InteractionSource를 제외 하 고 모든 입력 Api는 계속 작동 합니다 **. supportsTouchpad** 는 터치 패드 데이터 없이 false를 반환 합니다.

자세한 내용은 [UnityEngine. XR api 개요](../../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)를 참조 하세요.

## <a name="grip-pose-vs-pointing-pose"></a>그립 포즈 및 포인팅 포즈

Windows Mixed Reality는 다양 한 폼 팩터에서 동작 컨트롤러를 지원 하며, 각 컨트롤러의 디자인이 사용자의 손 위치와 앱이 컨트롤러를 렌더링할 때 사용 해야 하는 자연 스러운 "전달" 방향 간의 관계에 차이가 있습니다.

이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스에 대해 조사할 수 있는 두 가지 종류의 포즈가 있습니다.

* HoloLens에서 감지 된 손바닥의 위치 또는 이동 컨트롤러를 보유 하는 야자수의 위치를 나타내는 **그립 포즈** 입니다.
    * 모던 헤드셋에서는이 포즈를 사용 하 여 사용자 **의 손을** 나 **사용자의 손으로 보유 한 개체**(예: 소드 또는 포)를 렌더링 하는 데 가장 적합 합니다.
    * **그립 위치**: 컨트롤러를 자연스럽 게 유지 하는 경우 왼쪽 또는 오른쪽으로 조정 하 여 그립 내 위치를 가운데에 맞춥니다.
    * **그립 방향 오른쪽 축**: 손 모양 5 손가락 포즈를 형성 하는 손을 완전히 열 때 palm (왼쪽 야자나무에서 오른쪽으로 뒤로)의 광선을 만듭니다.
    * **그립 방향 전방 축: 핸들** 을 부분적으로 (컨트롤러를 보유 하는 것 처럼) 닫는 경우 비 엄지 손가락으로 형성 된 튜브를 통해 "전달" 하는 광선이 표시 됩니다.
    * **그립 방향 up 축**: 오른쪽 및 전방 정의에 의해 암시 된 위쪽 축입니다.
    * Unity의 교차 공급 업체 입력 API (XR)를 통해 그립 포즈에 액세스할 수 있습니다 **[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) 또는 Windows 특정 API (**sourcestate/Rotation**, 그립 포즈 요청)를 통해
* 앞에 있는 컨트롤러의 팁을 나타내는 **포인터가 포즈** 입니다.
    * 이 포즈는 컨트롤러 모델 자체를 렌더링할 때 **UI를 가리킬** 때 raycast에 가장 잘 사용 됩니다.
    * 현재 포인터 포즈는 Windows 관련 API (**Sourcestate/Rotation**, 포인터 포즈 요청)를 통해서만 사용할 수 있습니다.

이러한 포즈 좌표는 모두 Unity 세계 좌표로 표현 됩니다.