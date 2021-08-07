---
ms.openlocfilehash: e7f298b9d587df2243601670e187c109bb674a278deb67862b517568ca5198d7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213525"
---
# <a name="project-settings"></a>[프로젝트 설정](#tab/project)

### <a name="1-review-the-common-porting-steps-listed-above"></a>1. 위에 나열된 일반적인 이식 단계를 검토합니다.

위에 나열된 일반적인 단계를 검토하여 개발 환경이 올바르게 설정되었는지 확인합니다. #3 단계에서 Visual Studio 사용하는 경우 **Unity를** 사용한 게임 개발 워크로드를 선택해야 합니다. 다음 단계에서 최신 버전의 Unity를 설치할 예정이므로 "Unity 편집기 선택 사항" 구성 요소를 선택 취소할 수 있습니다.

### <a name="2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>2. Windows MR 지원을 사용하여 Unity의 최신 공용 빌드로 업그레이드
1. 혼합 현실 지원을 통해 [Unity의 최신 권장 공용 빌드를](../../install-the-tools.md) 다운로드합니다.
2. 시작하기 전에 프로젝트의 복사본을 저장합니다.
3. 프로젝트가 이전 버전의 Unity에서 빌드된 경우 업그레이드 시 Unity에서 사용할 수 있는 [설명서를](https://docs.unity3d.com/Manual/UpgradeGuides.html) 검토합니다.
4. Unity 사이트의 [지침에](https://docs.unity3d.com/Manual/APIUpdater.html) 따라 자동 API 업데이트기를 사용하세요.
5. 프로젝트를 실행하기 위해 수행해야 하는 추가 변경 내용이 있는지 확인하고 나머지 오류 및 경고를 처리합니다. 

> [!Note] 
> 사용하는 미들웨어가 있는 경우 최신 릴리스를 사용하고 있는지 확인합니다(아래 3단계의 자세한 내용).

### <a name="3-upgrade-your-middleware-to-the-latest-versions"></a>3. 미들웨어를 최신 버전으로 업그레이드

Unity 업데이트를 사용하면 게임 또는 애플리케이션이 의존하는 하나 이상의 미들웨어 패키지를 업데이트해야 할 가능성이 높습니다. 또한 최신 미들웨어를 최신 상태로 설정하면 포팅 프로세스의 나머지 부분 전체에서 성공할 가능성이 높아집니다.

### <a name="4-target-your-application-to-run-on-win32"></a>4. Win32에서 실행하도록 애플리케이션 대상 지정

Unity 애플리케이션 내에서 다음을 수행합니다.

* 파일 -> 빌드 설정
* "PC, Mac, Linux 독립 실행형" 선택
* 대상 플랫폼을 "Windows"로 설정
* 아키텍처를 "x86"으로 설정 "플랫폼 전환" 선택

> [!NOTE] 
> 애플리케이션에 디바이스별 서비스에 대한 모든 의존성(예: Steam의 일치 항목 만들기)이 있는 경우 이 단계에서 사용하지 않도록 설정해야 합니다. Windows 나중에 제공하는 동등한 서비스에 연결할 수 있습니다.

### <a name="5-setup-your-windows-mixed-reality-hardware"></a>5. Windows Mixed Reality 하드웨어 설정
1. [몰입형 헤드셋 설정의](/windows/mixed-reality/enthusiast-guide/before-you-start
) 단계 검토
2. Windows Mixed Reality [시뮬레이터 사용](../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) 및 Windows Mixed Reality 홈 탐색에 대해 알아봅니다. [](../../../discover/navigating-the-windows-mixed-reality-home.md)

### <a name="6-target-your-application-to-run-on-windows-mixed-reality"></a>6. Windows Mixed Reality 실행할 애플리케이션을 대상으로 지정합니다.
1. 먼저 특정 VR SDK와 관련된 다른 라이브러리 지원을 제거하거나 조건부로 컴파일해야 합니다. 이러한 자산은 Windows Mixed Reality 같은 다른 VR SDK와 호환되지 않는 방식으로 프로젝트의 설정 및 속성을 자주 변경합니다.
    * 예를 들어 프로젝트에서 SteamVR SDK를 참조하는 경우 Windows Mixed Reality 및 SteamVR을 모두 지원하는 Unity의 일반적인 VR API를 대신 사용하도록 프로젝트를 업데이트해야 합니다.
    * 다른 VR SDK를 조건부로 제외하기 위한 특정 단계가 곧 출시될 예정입니다.
2. Unity 프로젝트에서 [Windows 10 SDK를 대상으로 지정합니다.](../../unity/tutorials/holograms-100.md#target-windows-10-sdk)
3. 각 장면에 [대해 카메라를 설치합니다.](../../unity/tutorials/holograms-100.md#chapter-2---setup-the-camera)

### <a name="7-use-the-stage-to-place-content-on-the-floor"></a>7. 스테이지를 사용하여 콘텐츠를 지면에 배치

다양한 환경 규모에서 Mixed Reality [환경을 빌드할](../../../design/coordinate-systems.md)수 있습니다.

**좌표 크기 환경을** 이식하는 경우 Unity가 **고정** 추적 공간 유형으로 설정되어 있는지 확인해야 합니다.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

위의 코드는 고정 [참조 프레임을](../../../design/coordinate-systems.md#spatial-coordinate-systems)추적하도록 Unity의 세계 좌표계를 설정합니다. 고정 추적 모드에서는 앱이 시작되면 카메라의 기본 위치 바로 앞에 배치된 콘텐츠(정방향은 -Z)가 사용자 앞에 표시됩니다. 사용자의 착석 원본을 최근까지 Unity의 XR을 호출할 수 [있습니다. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 메서드.

**서 있는 규모 환경** 또는 방 **규모 환경을** 이식하는 경우 바닥과 관련된 콘텐츠를 배치하게 됩니다. 첫 번째 실행 중에 설정된 사용자의 정의된 층 수준 원점 및 선택적 방 경계를 나타내는 **[공간 단계](../../../design/coordinate-systems.md#spatial-coordinate-systems)** 를 사용하여 사용자의 층을 추론합니다. 이러한 환경의 경우 Unity가 **RoomScale** 추적 공간 유형으로 설정되어 있는지 확인해야 합니다. RoomScale이 기본값이지만 사용자가 보정한 방에서 컴퓨터를 이동한 상황을 파악하기 위해 명시적으로 설정하고 다시 true로 되돌리는 것이 중요합니다.

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

앱이 RoomScale 추적 공간 유형을 성공적으로 설정하면 y=0 평면에 배치된 콘텐츠가 층으로 표시됩니다. (0, 0, 0)의 원점은 사용자가 방 설치 중에 들여지는 층의 특정 위치이며, -Z는 설치 중에 발생한 정방향 방향을 나타냅니다.

그런 다음 스크립트 코드에서 UnityEngine.Experimental.XR.Boundary 형식에 대해 TryGetGeometry 메서드를 호출하여 경계 다각형을 가져올 수 있으며, 경계 형식은 TrackedArea입니다. 사용자가 경계를 정의한 경우(꼭짓점 목록을 다시 가져올 경우) 사용자가 만든 장면을 둘러 볼 수 있는 **공간 규모 환경을** 사용자에게 제공하는 것이 안전합니다.

시스템은 사용자가 경계에 접근하면 자동으로 경계를 렌더링합니다. 앱은 경계 자체를 렌더링하기 위해 이 다각형을 사용할 필요가 없습니다.

자세한 내용은 [Unity의 좌표계](../../unity/coordinate-systems-in-unity.md) 페이지를 참조하세요.

<!-- Some applications use a rectangle to constrain their interaction. Retrieving the largest inscribed rectangle is not directly supported in the UWP API or Unity. The example code linked to below shows how to find a rectangle within the traced bounds. It's heuristic-based so may not find the optimal solution, however, results are consistent with expectations. Parameters in the algorithm can be tuned to find more precise results at the cost of processing time. The algorithm is in a fork of the Mixed Reality Toolkit that uses the 5.6 preview MRTP version of Unity. This isn't publicly available. The code should be directly usable in 2017.2 and higher versions of Unity. The code will be ported to the current MRTK in the near future. -->

결과의 예:

![결과의 예](../../porting-apps/images/largestrectangle-400px.jpg)

알고리즘은 Daniel Smilkov: [다각형에서 가장 큰 사각형 블로그를](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/) 기반으로 하며

### <a name="8-work-through-your-input-model"></a>8. 입력 모델 작업

기존 HMD를 대상으로 하는 각 게임 또는 애플리케이션에는 처리하는 입력 집합, 경험에 필요한 입력 유형 및 해당 입력을 얻기 위해 호출하는 특정 API가 있습니다. Windows Mixed Reality 사용할 수 있는 입력을 최대한 간단하고 간단하게 활용할 수 있도록 하기 위해 투자했습니다.

인접한 탭에서 [Unity에 대한 입력 이식 가이드를](../porting-guides.md?tabs=input) 참조하여 Windows Mixed Reality 입력을 노출하는 방법 및 애플리케이션이 현재 수행할 수 있는 내용에 매핑되는 방법에 대해 자세히 설명합니다.

### <a name="9-performance-testing-and-tuning"></a>9. 성능 테스트 및 튜닝

Windows Mixed Reality 고급 게임 PC부터 광범위한 시장 일반 PC까지 광범위한 디바이스에서 사용할 수 있습니다. 대상으로 하는 시장에 따라 애플리케이션에 사용할 수 있는 컴퓨팅 및 그래픽 예산에 상당한 차이가 있습니다. 이 이식 연습 중에는 프리미엄 PC를 활용하고 앱에 사용할 수 있는 상당한 컴퓨팅 및 그래픽 예산이 있을 수 있습니다. 광범위한 대상에서 앱을 사용할 수 있도록 하려면 [를 대상으로 하려는 대표 하드웨어에서](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)앱을 테스트하고 프로파일러해야 합니다.

[Unity와](https://docs.unity3d.com/Manual/Profiler.html) [Visual Studio](/visualstudio/profiling/index) 모두 성능 프로파일러와 성능 프로파일링 및 최적화에 대한 [Microsoft](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) 및 [Intel](https://software.intel.com/articles/vr-content-developer-guide) 게시 지침을 포함합니다. Mixed Reality 성능 이해에서 사용할 수 있는 [성능에 대한](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)광범위한 설명이 있습니다. 또한 Unity의 [성능 권장 사항](../../unity/performance-recommendations-for-unity.md)Unity에 대한 특정 세부 정보가 있습니다.

# <a name="input-mapping"></a>[입력 매핑](#tab/input)

여러 플랫폼에 걸쳐 있는 Unity의 일반적인 Input.GetButton/GetAxis API 또는 Windows 관련 XR의 두 가지 방법 중 하나를 사용하여 입력 논리를 Windows Mixed Reality 이식할 수 있습니다. Wsa. 모션 컨트롤러 및 HoloLens 손을 위해 보다 풍부한 데이터를 제공하는 입력 API입니다.

> [!IMPORTANT]
> HP Reverb G2 컨트롤러를 사용하는 경우 추가 입력 매핑 [지침은 이 문서를](../../unity/unity-reverb-g2-controllers.md) 참조하세요.

## <a name="unity-xr-input-apis"></a>Unity XR 입력 API

새 프로젝트의 경우 처음부터 새 XR 입력 API를 사용하는 것이 좋습니다. 

[XR API에](https://docs.unity3d.com/Manual/xr_input.html)대한 자세한 내용은 에서 확인할 수 있습니다.

## <a name="inputgetbuttongetaxis-apis"></a>Input.GetButton/GetAxis API

Unity는 현재 일반 Input.GetButton/Input.GetAxis API를 사용하여 [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) 및 [OpenVR SDK에](https://docs.unity3d.com/Manual/OpenVRControllers.html)대한 입력을 노출합니다. 앱이 이미 이러한 API를 입력에 사용하고 있는 경우 Windows Mixed Reality 동작 컨트롤러를 지원하는 가장 쉬운 경로입니다. 입력 관리자에서 단추와 축을 다시맵하기만 하면 됩니다.

자세한 내용은 Unity [단추/축 매핑 테이블](../../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 및 [일반적인 Unity API 개요를 참조하세요.](../../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)

## <a name="windows-specific-xrwsainput-apis"></a>Windows 특정 XR. Wsa. 입력 API

> [!CAUTION]
> 프로젝트에서 XR을 사용하는 경우 WSA API는 향후 Unity 릴리스에서 XR SDK를 위해 단계적으로 해제됩니다. 새 프로젝트의 경우 XR SDK를 처음부터 사용하는 것이 좋습니다. [XR 입력 시스템 및 API에](https://docs.unity3d.com/Manual/xr_input.html)대한 자세한 내용은 에서 확인할 수 있습니다.

앱이 각 플랫폼에 대한 사용자 지정 입력 논리를 이미 빌드하는 경우 **UnityEngine.XR.WSA.Input** 네임스페이스에서 Windows 특정 공간 입력 API를 사용하도록 선택할 수 있습니다. 이렇게 하면 위치 정확도 또는 원본 종류와 같은 추가 정보에 액세스하여 HoloLens 손과 컨트롤러를 구분할 수 있습니다.

> [!NOTE]
> HP Reverb G2 컨트롤러를 사용하는 경우 Touchpad 데이터 없이 false를 반환하는 **InteractionSource.supportsTouchpad를** 제외한 모든 입력 API가 계속 작동합니다.

자세한 내용은 [UnityEngine.XR.WSA.Input API 개요를 참조하세요.](../../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)

## <a name="grip-pose-vs-pointing-pose"></a>그립 자세와 포인팅 자세

Windows Mixed Reality 다양한 폼 팩터에서 모션 컨트롤러를 지원하며, 각 컨트롤러의 디자인은 사용자의 손 위치와 앱이 컨트롤러를 렌더링할 때 가리키는 데 사용해야 하는 자연스러운 "앞으로" 방향 간의 관계가 다릅니다.

이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 원본에 대해 조사할 수 있는 두 가지 종류의 자세가 있습니다.

* **그립 자세로,** HoloLens 감지한 손의 손만 또는 모션 컨트롤러를 보유하는 손손의 위치를 나타냅니다.
    * 몰입형 헤드셋에서 이 자세는 사용자의 **손이나 사용자의 손을** **잡고 있는 개체(예:** 난소 또는 총)를 렌더링하는 데 가장 적합합니다.
    * **그립 위치:** 컨트롤러를 자연스럽게 보유할 때의 손만 중심으로, 그립 내의 위치를 가운데에 맞도록 왼쪽 또는 오른쪽으로 조정됩니다.
    * **그립 방향의 오른쪽 축:** 손을 완전히 열어 플랫 5 손가락 자세를 형성하면 손끝에 정상인 광선(왼쪽 손끝에서 앞으로, 오른쪽 손끝에서 뒤로)입니다.
    * **그립 방향의 앞으로 축:** 손을 부분적으로 닫을 때(컨트롤러를 보유하는 것처럼) 엄지 손가락이 아닌 손가락으로 형성된 선을 통해 "앞으로" 가리키는 광선입니다.
    * **그립 방향의 Up 축:** 오른쪽 및 앞으로 정의에 암시된 Up 축입니다.
    * Unity의 공급업체 간 입력 API(XR)를 통해 그립 자세에 액세스할 수 **[있습니다. InputTracking .](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html) GetLocalPosition/Rotation**) 또는 Windows 특정 API를 **통해(sourceState.sourcePose.TryGetPosition/Rotation**, 그립 자세 요청)
* **포인터는** 앞으로 가리키는 컨트롤러의 끝을 나타내는 입니다.
    * 이 자세는 컨트롤러 모델 자체를 렌더링할 때 **UI를 가리킬** 때 광선 캐스팅에 가장 적합합니다.
    * 현재 포인터 자세는 Windows 특정 **API(sourceState.sourcePose.TryGetPosition/Rotation**, 포인터 자세 요청)를 통해서만 사용할 수 있습니다.

이러한 자세 좌표는 모두 Unity 세계 좌표로 표현됩니다.