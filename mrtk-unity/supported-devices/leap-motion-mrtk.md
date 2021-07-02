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
# <a name="using-leap-motion"></a><span data-ttu-id="67805-104">Leap Motion 사용</span><span class="sxs-lookup"><span data-stu-id="67805-104">Using Leap Motion</span></span>

<span data-ttu-id="67805-105">이 데이터 공급자를 사용하려면 [Leap Motion Controller가](https://www.ultraleap.com/product/leap-motion-controller/) 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="67805-106">Leap Motion Data Provider VR에 대한 연속된 손 추적을 지원하며 편집기에서 신속한 프로토타이핑에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="67805-107">데이터 공급자는 헤드셋에 탑재된 Leap Motion Controller를 사용하거나 데스크에 탑재되도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="67805-109">이 공급자는 독립 실행형 플랫폼에 있는 동안 편집기 및 디바이스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="67805-110">UWP 플랫폼에 있는 동안에는 편집기에서 사용할 수 있지만 UWP 빌드에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="67805-111">MRTK 버전</span><span class="sxs-lookup"><span data-stu-id="67805-111">MRTK Version</span></span> | <span data-ttu-id="67805-112">Leap Motion Unity 모듈 버전 지원됨</span><span class="sxs-lookup"><span data-stu-id="67805-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="67805-113">2.6.x</span><span class="sxs-lookup"><span data-stu-id="67805-113">2.6.x</span></span> | <span data-ttu-id="67805-114">4.5.0, 4.5.1</span><span class="sxs-lookup"><span data-stu-id="67805-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="67805-115">2.7.x</span><span class="sxs-lookup"><span data-stu-id="67805-115">2.7.x</span></span>| <span data-ttu-id="67805-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span><span class="sxs-lookup"><span data-stu-id="67805-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="67805-117">MRTK에서 Leap Motion(Ultraleap) 손 추적 사용</span><span class="sxs-lookup"><span data-stu-id="67805-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="67805-118">MRTK 및 Leap Motion Unity 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="67805-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="67805-119">최신 [Leap Motion SDK가](https://developer.leapmotion.com/releases/?category=orion) 아직 설치되지 않은 경우 설치</span><span class="sxs-lookup"><span data-stu-id="67805-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="67805-120">**Microsoft.MixedReality.Toolkit 가져옵니다. Unity** 프로젝트에 대한 Foundation 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="67805-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="67805-121">최신 버전의 Leap Motion [Unity 모듈을](https://developer.leapmotion.com/unity) 다운로드하여 프로젝트로 가져오기</span><span class="sxs-lookup"><span data-stu-id="67805-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="67805-122">Unity 모듈 **내에서만 Core** 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="67805-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="67805-123">MRTK와 Leap Motion Unity 모듈 통합</span><span class="sxs-lookup"><span data-stu-id="67805-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="67805-124">Unity 모듈이 프로젝트에 있는 후 **Mixed Reality Toolkit**  >  **Leap Motion** 통합 Leap Motion Unity  >  **모듈로 이동합니다.**</span><span class="sxs-lookup"><span data-stu-id="67805-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="67805-125">Unity 모듈을 MRTK에 통합하는 경우 프로젝트에 10개의 어셈블리 정의가 추가되고 **Microsoft.MixedReality.Toolkit 대한 참조가 추가됩니다. Providers.LeapMotion** 어셈블리 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="67805-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="67805-126">Visual Studio를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="67805-128">Leap Motion Data Provider 추가</span><span class="sxs-lookup"><span data-stu-id="67805-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="67805-129">새 Unity 장면 만들기</span><span class="sxs-lookup"><span data-stu-id="67805-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="67805-130">**장면에** 추가 및 구성 Mixed Reality Toolkit 이동하여 MRTK를  >  **장면에 추가합니다.**</span><span class="sxs-lookup"><span data-stu-id="67805-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="67805-131">계층 구조에서 MixedRealityToolkit 게임 개체를 선택하고 **복사 및 사용자 지정을** 선택하여 기본 혼합 현실 프로필을 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="67805-133">**입력** 구성 프로필 선택</span><span class="sxs-lookup"><span data-stu-id="67805-133">Select the **Input** Configuration Profile</span></span>

    ![입력 구성 프로필 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="67805-135">입력 시스템 프로필에서 **복제를** 선택하여 수정을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="67805-137">입력 **데이터 공급자 섹션을** 열고 맨 위에서 **Data Provider 추가를** 선택하면 목록 끝에 새 데이터 공급자가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="67805-138">새 데이터 공급자를 열고 **형식을** **Microsoft.MixedReality.Toolkit 설정합니다. LeapMotion.Input > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="67805-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap Add Data Provider](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="67805-140">**복제를** 선택하여 기본 Leap Motion 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="67805-142">Leap Motion Data Provider Leap Motion `LeapControllerOrientation` Controller의 위치인 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="67805-143">`LeapControllerOrientation.Headset` 는 컨트롤러가 헤드셋에 탑재되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="67805-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="67805-144">`LeapControllerOrientation.Desk` 는 컨트롤러가 데스크에 평면으로 배치되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="67805-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="67805-145">기본값은 로 `LeapControllerOrientation.Headset` 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="67805-146">각 컨트롤러 방향에는 오프셋 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="67805-147">**헤드셋** 방향 오프셋 속성은 LeapXRServiceProvider 구성 요소의 오프셋 속성을 미러합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="67805-148">`LeapVRDeviceOffsetMode`에는 기본, 수동 헤드 오프셋 및 변환의 세 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="67805-149">오프셋 모드가 Default이면 Leap Motion Controller에 오프셋이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="67805-150">수동 헤드 오프셋 모드에서는 , 및 의 세 가지 속성을 수정할 수 `LeapVRDeviceOffsetY` `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="67805-151">그런 다음 축 오프셋 속성 값이 기본 컨트롤러 배치에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="67805-152">변환 오프셋 모드에는 `LeapVRDeviceOrigin` Leap Motion Controller의 새 원점이 지정되는 Transform 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="67805-153">**Desk** 방향에는 `LeapControllerOffset` 데스크 윤손의 앵커 위치를 정의하는 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="67805-154">오프셋은 주 카메라 위치를 기준으로 계산되며, 기본값은 (0,-0.2, 0.35)이며, 카메라가 전면 및 보기에 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="67805-155">애플리케이션이 시작될 때 프로필의 오프셋 속성이 한 번 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="67805-156">런타임 중에 값을 수정하려면 Leap Motion 디바이스 관리자에서 Leap Motion Service 공급자를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="67805-157">`EnterPinchDistance` 및 `ExitPinchDistance` 는 손가락 모으기/에어 탭 제스처 감지에 대한 거리 임계값입니다.</span><span class="sxs-lookup"><span data-stu-id="67805-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="67805-158">손가락 모으기 제스처는 인덱스 손가락 팁과 엄지 팁 사이의 거리를 측정하여 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="67805-159">입력 다운 이벤트에서 를 발생시키기 위해 `EnterPinchDistance` 기본값은 0.02로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="67805-160">입력 시 을 발생시키기 위해(손가락 모으기 종료) 인덱스 손가락 팁과 엄지 팁 사이의 기본 거리는 0.05입니다.</span><span class="sxs-lookup"><span data-stu-id="67805-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="67805-161">`LeapControllerOrientation`: 헤드셋(기본값)</span><span class="sxs-lookup"><span data-stu-id="67805-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="67805-162">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="67805-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="67805-167">Leap Motion Data Provider 테스트</span><span class="sxs-lookup"><span data-stu-id="67805-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="67805-168">Leap Motion Data Provider 입력 시스템 프로필에 추가된 후 재생을 누르고, Leap Motion Controller 앞에서 손을 움직이면 손의 공동 표현이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="67805-169">프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="67805-169">Building your project</span></span>
    - <span data-ttu-id="67805-170">파일 **> 빌드 설정** 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="67805-171">Leap Motion Data Provider 사용하는 경우 독립 실행형 빌드만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="67805-172">독립 실행형 빌드에 Windows Mixed Reality 헤드셋을 사용하는 방법에 대한 지침은 [WMR 헤드셋(독립 실행형)에 MRTK 빌드 및 배포를 참조하세요.](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)</span><span class="sxs-lookup"><span data-stu-id="67805-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK to WMR Headsets (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="67805-173">손 조인트 얻기</span><span class="sxs-lookup"><span data-stu-id="67805-173">Getting the hand joints</span></span>

<span data-ttu-id="67805-174">Leap Motion Data Provider 사용하여 조인을 가져오는 것은 MRTK에 대한 손 공동 검색과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="67805-175">자세한 내용은 [손 추적을](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)참조하세요.</span><span class="sxs-lookup"><span data-stu-id="67805-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="67805-176">Unity 장면에 MRTK가 있고 Leap Motion Data Provider 입력 시스템 프로필에 입력 Data Provider 추가된 경우 빈 게임 개체를 만들고 다음 예제 스크립트를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="67805-177">이 스크립트는 Leap Motion Hand에서 손만의 자세를 검색하는 방법의 간단한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="67805-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="67805-178">구는 왼쪽 윤면 뒤에, 큐브는 오른쪽 윤을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="67805-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="67805-179">Unity 편집기 워크플로 팁</span><span class="sxs-lookup"><span data-stu-id="67805-179">Unity editor workflow tip</span></span>

<span data-ttu-id="67805-180">Leap Motion Data Provider 사용하려면 VR 헤드셋이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="67805-181">MRTK 앱에 대한 변경 내용은 헤드셋 없이 Leap hands를 사용하여 편집기에서 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="67805-182">LEAP Motion Hands는 VR 헤드셋을 연결하지 않고 편집기에서 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="67805-183">가 `LeapControllerOrientation` **헤드셋** 로 설정된 경우 Leap Motion 컨트롤러는 카메라를 앞으로 향하여 한 손으로 보유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="67805-184">편집기에서 WASD 키를 사용하여 카메라를 이동하고 `LeapControllerOrientation` 헤드셋인 경우 손은 카메라를 따르지 않습니다. </span><span class="sxs-lookup"><span data-stu-id="67805-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="67805-185">은 `LeapControllerOrientation` **헤드셋으로** 설정된 동안 VR 헤드셋이 연결된 경우에만 카메라 이동을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="67805-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="67805-186">이 Desk 로 설정된 경우 Leap 손은 편집기에서 카메라 이동을 `LeapControllerOrientation` 따릅니다. </span><span class="sxs-lookup"><span data-stu-id="67805-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="67805-187">Project Leap Motion 제거</span><span class="sxs-lookup"><span data-stu-id="67805-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="67805-188">**Mixed Reality Toolkit**  >  **Leap Motion** 별도  >  **Leap Motion Unity 모듈로 이동합니다.**</span><span class="sxs-lookup"><span data-stu-id="67805-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="67805-189">Microsoft.MixedReality.Toolkit Unity를 참조로 새로 고치도록 **합니다. Providers.LeapMotion.asmdef** 파일은 이 단계에서 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="67805-190">Unity 닫기</span><span class="sxs-lookup"><span data-stu-id="67805-190">Close Unity</span></span>
1. <span data-ttu-id="67805-191">Visual Studio 닫습니다(열려 있는 경우).</span><span class="sxs-lookup"><span data-stu-id="67805-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="67805-192">파일 탐색기 열고 MRTK Unity 프로젝트의 루트로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="67805-193">**UnityProjectName/Library** 디렉터리 삭제</span><span class="sxs-lookup"><span data-stu-id="67805-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="67805-194">**UnityProjectName/Assets/Plugins/LeapMotion** 디렉터리를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="67805-195">**UnityProjectName/Assets/Plugins/LeapMotion.meta** 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="67805-196">Unity 다시 열기</span><span class="sxs-lookup"><span data-stu-id="67805-196">Reopen Unity</span></span>

<span data-ttu-id="67805-197">Unity 2018.4에서는 라이브러리 및 Leap Motion Core 자산을 삭제한 후에도 콘솔에 오류가 남아 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="67805-198">다시 연 후 오류가 기록되면 Unity를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="67805-199">일반 오류</span><span class="sxs-lookup"><span data-stu-id="67805-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="67805-200">Leap Motion이 MRTK와 통합되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="67805-201">도약 동작 Unity 모듈이 MRTK와 통합 되었는지 테스트 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="67805-202">**혼합 현실 Toolkit > 유틸리티 > Leap 동작 > 통합 상태 확인** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="67805-203">그러면 Leap 동작 Unity 모듈이 MRTK와 통합 되었는지 여부에 대 한 메시지가 포함 된 팝업 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67805-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="67805-204">메시지에 자산이 통합 되지 않은 것으로 표시 되 면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="67805-205">Leap 동작 Unity 모듈이 프로젝트에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="67805-206">추가 된 버전이 지원 되는지 확인 하십시오. 지원 되는 버전은 페이지 맨 위에 있는 표를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="67805-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="67805-207">**혼합 현실 Toolkit > 유틸리티 > >** leap 동작을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="67805-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="67805-208">어셈블리 멀티 플레이 HLAPI 복사 실패</span><span class="sxs-lookup"><span data-stu-id="67805-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="67805-209">Leap 동작 Unity 코어 자산의 가져오기 시이 오류가 기록 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67805-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="67805-210">**해결 방법**</span><span class="sxs-lookup"><span data-stu-id="67805-210">**Solution**</span></span>

- <span data-ttu-id="67805-211">단기 솔루션은 Unity를 다시 시작 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="67805-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="67805-212">자세한 내용은 [문제 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="67805-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="67805-213">윤 동작 예제 장면</span><span class="sxs-lookup"><span data-stu-id="67805-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="67805-214">예제 장면에서는 DefaultLeapMotionConfiguration 프로필을 사용 하 고 Unity 프로젝트가 Leap Data Provider 동작을 사용 하도록 올바르게 구성 되었는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="67805-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="67805-215">예제 장면이 Toolkit MixedReality에 포함 되어 있습니다. \*\*\*\* **Mrtk/예제/데모/수동 추적/** 디렉터리의 예제 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="67805-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="67805-216">참조</span><span class="sxs-lookup"><span data-stu-id="67805-216">See also</span></span>

- [<span data-ttu-id="67805-217">입력 공급자</span><span class="sxs-lookup"><span data-stu-id="67805-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="67805-218">수동 추적</span><span class="sxs-lookup"><span data-stu-id="67805-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
