---
title: Unity의 모션 컨트롤러
description: XR 및 공통 단추 및 축 API를 사용하여 모션 컨트롤러 입력을 사용하여 Unity에서 응시에 대한 조치를 취하는 방법을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: 모션 컨트롤러, unity, 입력, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: ccda5b11190e829ccc655989a6f679ef6ef647a920c01a3182548b23a3d85084
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216246"
---
# <a name="motion-controllers-in-unity"></a>Unity의 모션 컨트롤러

Unity, [손 제스처](../../design/gaze-and-commit.md#composite-gestures) 및 HoloLens 및 몰입형 HMD의 [모션 컨트롤러에서](../../design/motion-controllers.md) [응시에](gaze-in-unity.md)대한 작업을 수행하려면 두 가지 주요 방법이 있습니다. Unity에서 동일한 API를 통해 공간 입력의 두 원본에 대한 데이터에 액세스합니다.

Unity는 Windows Mixed Reality 공간 입력 데이터에 액세스하는 두 가지 기본 방법을 제공합니다. 일반적인 *Input.GetButton/Input.GetAxis* API는 여러 Unity XR SDK에서 작동하지만, Windows Mixed Reality 특정 *InteractionManager/GestureRecognizer* API는 공간 입력 데이터의 전체 집합을 노출합니다.

## <a name="unity-xr-input-apis"></a>Unity XR 입력 API

새 프로젝트의 경우 처음부터 새 XR 입력 API를 사용하는 것이 좋습니다. 

[XR API에](https://docs.unity3d.com/Manual/xr_input.html)대한 자세한 내용은 에서 확인할 수 있습니다.

## <a name="unity-buttonaxis-mapping-table"></a>Unity 단추/축 매핑 테이블

Unity의 Windows Mixed Reality 동작 컨트롤러용 Input Manager는 *Input.GetButton/GetAxis* API를 통해 아래에 나열된 단추 및 축 ID를 지원합니다. "Windows MR 관련" 열은 *InteractionSourceState* 형식에서 사용할 수 있는 속성을 나타냅니다. 이러한 각 API는 아래 섹션에 자세히 설명되어 있습니다.

Windows Mixed Reality 대한 단추/축 ID 매핑은 일반적으로 Oculus 단추/축 ID와 일치합니다.

Windows Mixed Reality 대한 단추/축 ID 매핑은 다음 두 가지 방법으로 OpenVR의 매핑과 다릅니다.
1. 매핑은 엄지스틱과 구별되는 터치 패드 ID를 사용하여 엄지스틱과 터치패드를 모두 사용하는 컨트롤러를 지원합니다.
2. 매핑은 메뉴 단추에 대한 A 및 X 단추의 ID를 오버로드하여 실제 ABXY 단추에 사용할 수 있도록 하는 것을 방지합니다.

<table>
<tr>
<th rowspan="2">입력 </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">일반 Unity API</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR 관련 입력 API</a><br />(XR. Wsa. 입력)</th>
</tr><tr>
<th> 왼손 </th><th> 오른쪽</th>
</tr><tr>
<td> 트리거 누른 선택 </td><td> 축 9 = 1.0 </td><td> 축 10 = 1.0 </td><td> selectPressed</td>
</tr><tr>
<td> 트리거 아날로그 값 선택 </td><td> 축 9 </td><td> 축 10 </td><td> SelectPressedAmount</td>
</tr><tr>
<td> 트리거를 부분적으로 누른 경우 선택 </td><td> 단추 <i>14(게임 패드 호환성)</i> </td><td> 단추 <i>15(게임 패드 호환성)</i> </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> 메뉴 단추를 눌렀습니다. </td><td> 단추 6* </td><td> 단추 7* </td><td> menuPressed</td>
</tr><tr>
<td> 그립 단추를 눌렀습니다. </td><td> 축 11 = 1.0(아날로그 값 없음)<br />단추 <i>4(게임 패드 호환성)</i> </td><td> 축 12 = 1.0(아날로그 값 없음)<br />단추 <i>5(게임 패드 호환성)</i> </td><td> 파악</td>
</tr><tr>
<td> Thumbstick <i>X(왼쪽: -1.0, 오른쪽: 1.0)</i> </td><td> 축 1 </td><td> 축 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> Thumbstick <i>Y(top: -1.0, bottom: 1.0)</i> </td><td> 축 2 </td><td> 축 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> Thumbstick 누른 경우 </td><td> 단추 8 </td><td> 단추 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> 터치 패드 <i>X(왼쪽: -1.0, 오른쪽: 1.0)</i> </td><td> 축 17* </td><td> 축 19* </td><td> touchpadPosition.x</td>
</tr><tr>
<td> 터치 패드 <i>Y(위쪽: -1.0, 아래쪽: 1.0)</i> </td><td> 축 18* </td><td> 축 20* </td><td> touchpadPosition.y</td>
</tr><tr>
<td> 터치 패드 터치 </td><td> 단추 18* </td><td> 단추 19* </td><td> touchpadTouched</td>
</tr><tr>
<td> 터치 패드 누른 </td><td> 단추 16* </td><td> 단추 17* </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF 그립 자세 또는 포인터 자세 </td><td colspan="2"> <i>그립</i> 자세만: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">Xr. InputTracking.GetLocalRotation</a></td><td> <i>그립</i> 또는 <i>포인터를</i> 인수로 전달: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> 추적 상태 </td><td colspan="2"> <i>MR별 API를 통해서만 사용할 수 있는 위치 정확도 및 원본 손실 위험</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>이러한 단추/축 ID는 게임 패드, Oculus Touch 및 OpenVR에서 사용하는 매핑의 충돌로 인해 Unity에서 OpenVR에 사용하는 ID와 다릅니다.

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->

### <a name="openxr"></a>OpenXR

Unity의 혼합 현실 상호 작용에 대한 기본 사항 알아보려면 Unity [XR 입력에 대한 Unity 설명서를 참조하세요.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html) 이 Unity 설명서에서는 컨트롤러별 입력에서 보다 일반적인 **InputFeatureUsage로의** 매핑, 사용 가능한 XR 입력을 식별하고 분류하는 방법, 이러한 입력에서 데이터를 읽는 방법 등에 대해 설명합니다.

Mixed Reality OpenXR 플러그 인은 아래에 설명된 대로 표준 **InputFeatureUsage에** 매핑된 추가 입력 상호 작용 프로필을 제공합니다.

| InputFeatureUsage | HP Reverb G2 컨트롤러(OpenXR) | HoloLens 손(OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | 조이스틱 | |
| primary2DAxisClick | 운정 - 클릭 | |
| 트리거 | 트리거  | |
| 그립 | 그립 | 에어 탭 또는 에어 탭 |
| primaryButton | [X/A] - 누르기 | 에어 탭 |
| secondaryButton | [Y/B] - 누르기 | |
| gripButton | 그립 - 누르기 | |
| triggerButton | 트리거 - 누르기 | |
| menuButton | 메뉴 | |

## <a name="grip-pose-vs-pointing-pose"></a>그립 자세와 포인팅 자세

Windows Mixed Reality 다양한 폼 팩터에서 모션 컨트롤러를 지원합니다. 각 컨트롤러의 디자인은 사용자의 손 위치와 앱이 컨트롤러를 렌더링할 때 가리키는 데 사용해야 하는 자연스러운 "앞으로" 방향 간의 관계에 따라 다릅니다.

이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스에 대해 조사할 수 있는 두 가지 종류의 자세인 **그립 자세와** **포인터 자세가** 있습니다. 그립 자세와 포인터 자세 좌표는 모두 전역 Unity 세계 좌표의 모든 Unity API로 표현됩니다.

### <a name="grip-pose"></a>그립 자세

**그립 자세는** HoloLens 감지하거나 모션 컨트롤러를 보유하는 사용자 손아귀의 위치를 나타냅니다.

몰입형 헤드셋에서 그립 자세는 **사용자의 손** 또는 사용자의 **손 에 보관된 개체를 렌더링하는** 데 가장 적합합니다. 그립 자세는 모션 컨트롤러를 시각화할 때도 사용됩니다. 모션 컨트롤러에 대해 Windows 제공되는 **렌더링 가능한 모델은** 그립 자세를 회전의 원점 및 중심으로 사용합니다.

그립 자세는 다음과 같이 구체적으로 정의됩니다.
* **그립 위치:** 컨트롤러를 자연스럽게 보유할 때의 손만 중심으로, 그립 내의 위치를 가운데에 맞도록 왼쪽 또는 오른쪽으로 조정됩니다. Windows Mixed Reality 모션 컨트롤러에서 이 위치는 일반적으로 이해 단추에 맞춥니다.
* **그립 방향의 오른쪽 축:** 손을 완전히 열어 플랫 5 손가락 자세를 형성하면 손끝에 정상인 광선(왼쪽 손끝에서 앞으로, 오른쪽 손끝에서 뒤로)입니다.
* **그립 방향의 앞으로 축:** 손을 부분적으로 닫을 때(컨트롤러를 보유하는 것처럼) 엄지 손가락이 아닌 손가락으로 형성된 선을 통해 "앞으로" 가리키는 광선입니다.
* **그립 방향의 Up 축:** 오른쪽 및 앞으로 정의에 암시된 Up 축입니다.

Unity의 공급업체 간 입력 API(XR)를 통해 그립 자세에 액세스할 수 *[있습니다. InputTracking .](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html) GetLocalPosition/Rotation*) 또는 Windows MR별 API를 *통해(sourceState.sourcePose.TryGetPosition/Rotation*, **그립** 노드에 대한 자세 데이터 요청)

### <a name="pointer-pose"></a>포인터 자세

**포인터 자세는** 앞으로 가리키는 컨트롤러의 끝을 나타냅니다.

시스템 제공 포인터 자세는 **컨트롤러 모델 자체를 렌더링할** 때 raycast에 가장 적합합니다. 가상 총과 같은 컨트롤러 대신 다른 가상 개체를 렌더링하는 경우 앱에서 정의한 총 모델을 따라 이동하는 광선과 같이 해당 가상 개체에 가장 자연스러운 광선을 가리킵니다. 사용자는 실제 컨트롤러가 아닌 가상 개체를 볼 수 있으므로 가상 개체를 가리키는 것이 앱을 사용하는 사용자에게 더 자연스럽습니다.

현재 포인터 자세는 Windows MR별 *API인 sourceState.sourcePose.TryGetPosition/Rotation을* 통해서만 Unity에서 사용할 수 있으며 *InteractionSourceNode.Pointer를* 인수로 전달합니다.

### <a name="openxr"></a>OpenXR 

OpenXR 입력 상호 작용을 통해 두 가지 자세 집합에 액세스할 수 있습니다.

* 손에서 개체를 렌더링하기 위한 그립 자세
* 목표는 세계를 가리키는 것입니다.

이 디자인과 두 가지 자세 간의 차이점에 대한 자세한 내용은 [OpenXR 사양 - 입력 하위 경로](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)에서 찾을 수 있습니다.

InputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** 및 **DeviceAngularVelocity에서** 제공하는 자세는 모두 OpenXR **그립** 자세를 나타냅니다. 그립 자세와 관련된 InputFeatureUsages는 Unity의 [CommonUsages 에 정의되어 있습니다.](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)

InputFeatureUsages **PointerPosition,** **PointerRotation,** PointerVelocity 및 **PointerAngularVelocity에서** 제공하는 자세는 모두 OpenXR **목표** 자세를 나타냅니다.  이러한 InputFeatureUsages는 포함된 C# 파일에 정의되지 않으므로 다음과 같이 사용자 고유의 InputFeatureUsages를 정의해야 합니다.

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

## <a name="haptics"></a>햅 틱

Unity의 XR 입력 시스템에서 haptics 사용에 대한 자세한 내용은 Unity [XR 입력을 위한 Unity 설명서 - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)에서 확인할 수 있습니다.

## <a name="controller-tracking-state"></a>컨트롤러 추적 상태

헤드셋과 마찬가지로 Windows Mixed Reality 모션 컨트롤러에는 외부 추적 센서를 설치할 필요가 없습니다. 대신 컨트롤러는 헤드셋 자체의 센서에 의해 추적됩니다.

사용자가 헤드셋의 보기 필드에서 컨트롤러를 이동하는 경우 Windows 대부분의 경우 컨트롤러 위치를 계속 유추합니다. 컨트롤러가 오랫동안 시각적 추적을 손실한 경우 컨트롤러의 위치는 근사 정확도 위치로 떨어집니다.

이 시점에서 시스템은 내부 방향 센서를 사용하여 컨트롤러의 진정한 방향을 계속 노출하면서 사용자가 이동할 때 사용자의 위치를 추적하여 컨트롤러를 사용자에게 본문 잠금합니다. 컨트롤러를 사용하여 UI 요소를 가리키고 활성화하는 많은 앱은 사용자가 모르게 대략적인 정확도로 정상적으로 작동할 수 있습니다.

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a>명시적으로 상태를 추적하는 이유

추적 상태에 따라 위치를 다르게 처리하려는 앱은 더 나아가서 컨트롤러의 상태(예: *SourceLossRisk* 및 *PositionAccuracy)에서* 속성을 검사할 수 있습니다.

<table>
<tr>
<th> 추적 상태 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>높은 정확도</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 높음 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>높은 정확도(손실 위험)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> 높음 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>대략적 정확도</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 근사치 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>위치 없음</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> 근사치 </td><td style="background-color: orange"> false</td>
</tr>
</table>

이러한 모션 컨트롤러 추적 상태는 다음과 같이 정의됩니다.
* **높은 정확도:** 모션 컨트롤러는 헤드셋의 보기 필드 내에 있는 동안 일반적으로 시각적 추적을 기반으로 높은 정확도 위치를 제공합니다. 일시적으로 보기 필드를 벗어나거나 헤드셋 센서(예: 사용자의 다른 손으로)에서 일시적으로 가려지는 이동 컨트롤러는 컨트롤러 자체의 관성 추적에 따라 짧은 시간 동안 높은 정확도의 자세를 계속 반환합니다.
* **높은 정확도(손실 위험):** 사용자가 헤드셋의 보기 필드 가장자리를 지나 모션 컨트롤러를 이동하면 헤드셋은 곧 컨트롤러의 위치를 시각적으로 추적할 수 없습니다. 앱은 **SourceLossRisk가** 1.0에 도달하는 것을 확인하여 컨트롤러가 이 FOV 경계에 도달한 시기를 알고 있습니다. 이 시점에서 앱은 안정적인 고품질 자세 스트림이 필요한 컨트롤러 제스처를 일시 중지하도록 선택할 수 있습니다.
* **대략적 정확도:** 컨트롤러가 오랫동안 시각적 추적을 손실한 경우 컨트롤러의 위치는 근사 정확도 위치로 떨어집니다. 이 시점에서 시스템은 내부 방향 센서를 사용하여 컨트롤러의 진정한 방향을 계속 노출하면서 사용자가 이동할 때 사용자의 위치를 추적하여 컨트롤러를 사용자에게 본문 잠금합니다. 컨트롤러를 사용하여 UI 요소를 가리키고 활성화하는 많은 앱은 사용자가 모르게 대략적인 정확도로 정상적으로 작동할 수 있습니다. 입력 요구 사항이 더 많은 앱은 **PositionAccuracy** 속성을 검사하여 높은 **정확도에서** **근사** 정확도로 이 저하를 감지하도록 선택할 수 있습니다. 예를 들어 이 시간 동안 사용자에게 화면 끄기 대상에서 더 큰 적중 상자를 제공할 수 있습니다.
* **위치 없음:** 컨트롤러가 오랜 시간 동안 대략적인 정확도로 작동할 수 있지만, 시스템에서는 현재 본문이 잠긴 위치도 의미가 없다는 것을 알고 있습니다. 예를 들어 켜진 컨트롤러가 시각적으로 관찰되지 않았거나 사용자가 컨트롤러를 내려 놓은 다음 다른 사용자가 선택할 수 있습니다. 이 경우 시스템은 앱에 위치를 제공하지 않으며 *TryGetPosition은* false를 반환합니다.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>일반적인 Unity API(Input.GetButton/GetAxis)

**네임스페이스:** *UnityEngine,* *UnityEngine.XR*<br>
**형식:** *입력*, *XR. InputTracking*

Unity는 현재 일반 *Input.GetButton/Input.GetAxis API를* 사용하여 손과 모션 컨트롤러를 [포함하여 Oculus SDK,](https://docs.unity3d.com/Manual/OculusControllers.html) [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 및 Windows Mixed Reality 대한 입력을 노출합니다. 앱에서 이러한 API를 입력에 사용하는 경우 Windows Mixed Reality 포함하여 여러 XR SDK에서 모션 컨트롤러를 쉽게 지원할 수 있습니다.

### <a name="getting-a-logical-buttons-pressed-state"></a>논리 단추의 누른 상태 얻기

일반 Unity 입력 API를 사용하려면 일반적으로 단추와 축을 [Unity 입력 관리자의](https://docs.unity3d.com/Manual/ConventionalGameInput.html)논리적 이름에 연결하고 단추 또는 축 ID를 각 이름에 바인딩하는 것으로 시작합니다. 그런 다음 해당 논리 단추/축 이름을 참조하는 코드를 작성할 수 있습니다.

예를 들어 왼쪽 모션 컨트롤러의 트리거 단추를 제출 작업에 매핑하려면 Unity 내에서 **> Project 설정 > 입력 편집으로** 이동하고 축 아래의 Submit 섹션의 속성을 확장합니다. 다음과 같이 **양의 단추** 또는 Alt **긍정 단추** 속성을 변경하여 **14 단추를** 읽습니다.

![Unity의 InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

그런 다음 스크립트는 입력을 사용 하 여 전송 작업을 확인할 수 있습니다 *. GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
**축** 에서 **크기** 속성을 변경 하 여 논리적 단추를 더 추가할 수 있습니다.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>물리적 단추의 누름 상태를 직접 가져오기

*입력. GetKey* 를 사용 하 여 정규화 된 이름으로 수동으로 단추에 액세스할 수도 있습니다.

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>직접 또는 동작 컨트롤러의 포즈 가져오기

XR를 사용 하 여 컨트롤러의 위치 및 회전에 액세스할 수 있습니다 *. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> 위의 코드는 컨트롤러의 그립 포즈 (사용자가 컨트롤러를 보유 하는 위치)를 나타내며,이는 사용자 쪽에서 소드를 렌더링 하거나 컨트롤러 자체의 모델을 렌더링 하는 데 유용 합니다.
> 
> 이 그립 포즈와 포인터 포즈 (컨트롤러의 팁) 간의 관계는 컨트롤러 마다 다를 수 있습니다. 이제 컨트롤러의 포인터 포즈에 액세스 하는 것은 아래 섹션에 설명 된 MR 특정 입력 API를 통해서만 가능 합니다.

## <a name="windows-specific-apis-xrwsainput"></a>Windows 특정 api (XR. WSA. 입력

> [!CAUTION]
> 프로젝트에서 XR를 사용 하는 경우 WSA Api는 향후 Unity 릴리스의 XR SDK에 대 한 것입니다. 새 프로젝트의 경우 처음부터 XR SDK를 사용 하는 것이 좋습니다. [XR 입력 시스템 및 api](https://docs.unity3d.com/Manual/xr_input.html)에 대 한 자세한 내용은 여기에서 찾을 수 있습니다.

**네임 스페이스:** *unityengine. XR*<br>
**유형**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Windows Mixed Reality 손으로 입력 (HoloLens) 및 동작 컨트롤러에 대 한 자세한 정보를 얻기 위해 *unityengine. XR* 네임 스페이스에서 Windows 특정 공간 입력 api를 사용 하도록 선택할 수 있습니다. 이를 통해 위치 정확도 나 소스 종류와 같은 추가 정보에 액세스할 수 있으므로 실습 및 컨트롤러를 구분할 수 있습니다.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>직접 및 동작 컨트롤러의 상태 폴링

*GetCurrentReading* 메서드를 사용 하 여 각 상호 작용 소스 (직접 또는 동작 컨트롤러)에 대해이 프레임의 상태를 폴링할 수 있습니다.

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

가져오는 각 *InteractionSourceState* 는 현재 시점에서 상호 작용 소스를 나타냅니다. *InteractionSourceState* 는 다음과 같은 정보를 노출 합니다.
* 어떤 [종류의 누름](../../design/motion-controllers.md) 이 발생 합니까 (선택/메뉴/-/터치 패드/엄지 스틱)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* 터치 패드 및/또는 엄지 스틱 XY 좌표 및 작업 된 상태와 같은 동작 컨트롤러에 해당 하는 기타 데이터

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* InteractionSourceKind는 원본이 나 동작 컨트롤러 인지 여부를 알 수 있습니다.

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>앞으로 예측 된 렌더링 동작에 대 한 폴링

* 손이 나 컨트롤러에서 상호 작용 원본 데이터를 폴링하는 경우이 프레임의 photons 사용자의 눈에 도달 하 게 되는 순간에 대해 앞으로 예측 하는 포즈를 얻을 수 있습니다.  앞으로 예측 되는 포즈는 컨트롤러를 렌더링 하거나 각 프레임에서 보유 한 개체를 **렌더링** 하는 데 가장 적합 합니다.  Controller를 사용 하 여 지정 된 보도 또는 릴리스를 대상으로 하는 경우 아래에 설명 된 기록 이벤트 Api를 사용 하는 경우 가장 정확 합니다.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* 이 현재 프레임에 대해 앞으로 예측 한 헤드 포즈를 얻을 수도 있습니다.  원본 포즈와 마찬가지로,이 기능은 커서를 **렌더링** 하는 데 유용 합니다. 단, 아래에 설명 된 기록 이벤트 api를 사용 하는 경우에는 지정 된 누름 또는 릴리스를 대상으로 하는 것이 가장 정확 합니다.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>상호 작용 소스 이벤트 처리

정확한 기록 포즈 데이터에서 발생 하는 입력 이벤트를 처리 하기 위해 폴링 대신 상호 작용 소스 이벤트를 처리할 수 있습니다.

상호 작용 소스 이벤트를 처리 하려면:
* *InteractionManager* 입력 이벤트에 등록 합니다. 관심이 있는 각 상호 작용 이벤트 형식에 대해 구독 해야 합니다.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* 이벤트를 처리 합니다. 상호 작용 이벤트를 구독 한 후에는 해당 하는 경우 콜백을 받게 됩니다. *Sourcepressed* 예제에서는 소스가 검색 된 후와 릴리스 또는 손실 되기 전에이 상태가 됩니다.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>이벤트 처리를 중지 하는 방법

이벤트에 더 이상 관심이 없거나 이벤트를 구독 하는 개체를 삭제 하려는 경우에는 이벤트 처리를 중지 해야 합니다. 이벤트 처리를 중지 하려면 이벤트의 구독을 취소 합니다.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>상호 작용 소스 이벤트 목록

사용할 수 있는 상호 작용 소스 이벤트는 다음과 같습니다.
* *InteractionSourceDetected* (원본이 활성화 됩니다.)
* *InteractionSourceLost* (비활성 상태가 됨)
* *InteractionSourcePressed* (누르기, 단추 누르기 또는 "Select" 재생)
* *InteractionSourceReleased* (탭의 끝, 단추 해제 또는 "Select" 재생 끝)
* *InteractionSourceUpdated* (다른 상태를 이동 하거나 변경 하지 않음)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>기록 대상 이벤트는 누름 또는 릴리스와 가장 정확 하 게 일치 합니다.

앞에서 설명한 폴링 Api는 앱을 앞으로 예측 하는 포즈를 제공 합니다.  이러한 예측 된 포즈는 컨트롤러 또는 가상 핸드헬드 개체를 렌더링 하는 데 가장 적합 하지만 다음 두 가지 주요 이유로 이후 포즈는 대상 지정에 적합 하지 않습니다.
* 사용자가 컨트롤러의 단추를 누르면 시스템에서 누르기를 받기 전에 Bluetooth 하는 데 20 밀리초의 무선 대기 시간이 있을 수 있습니다.
* 그런 다음 앞으로 예측 하는 포즈를 사용 하는 경우 현재 프레임의 photons 사용자의 눈에 도달 하는 시간을 대상으로 적용 하는 다른 10-20 ms의 전달 예측이 적용 됩니다.

즉, 폴링을 통해 사용자의 헤드와 손을 모두 사용 하는 경우에는 사용자의 헤드와 30-40를 전달 하는 소스 포즈 또는 헤드가 발생 합니다.  HoloLens 손으로 입력 하는 경우에는 무선 전송 지연 시간이 없지만, 누르기를 검색 하는 데 비슷한 처리 지연이 있습니다.

직접 또는 컨트롤러에 대 한 사용자의 원래 의도에 따라 정확 하 게 대상으로 지정 하려면 해당 *InteractionSourcePressed* 또는 *InteractionSourceReleased* 입력 이벤트에서 기록 원본 포즈 또는 head 포즈를 사용 해야 합니다.

사용자의 헤드 또는 해당 컨트롤러에서 기록 포즈 데이터를 사용 하 여 보도를 대상으로 지정할 수 있습니다.
* 사용자가 [gazing](../../design/gaze-and-commit.md) 된 항목을 확인 하기 위해 **대상 지정** 에 사용할 수 있는 제스처 또는 컨트롤러를 누를 때 발생 하는 시점의 헤드입니다.

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* 이동 컨트롤러를 사용 하 여 사용자가 컨트롤러를 가리킨 **항목을 확인 하는** 데 사용 될 수 있는 시점에 발생 하는 소스입니다.  이는 누름이 발생 한 컨트롤러의 상태가 됩니다.  컨트롤러 자체를 렌더링 하는 경우에는 핸들 포즈 대신 포인터 포즈를 요청 하 여 사용자가 렌더링 된 컨트롤러의 자연 스러운 팁을 고려 하는 대상 광선을 만들 수 있습니다.

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>이벤트 처리기 예

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk"></a>MRTK의 동작 컨트롤러

입력 관리자에서 [제스처 및 동작 컨트롤러](/windows/mixed-reality/mrtk-unity/features/input/controllers) 에 액세스할 수 있습니다.

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