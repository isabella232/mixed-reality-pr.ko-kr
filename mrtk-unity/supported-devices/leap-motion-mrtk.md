---
title: 도약 동작 MRTK
description: Leap 동작을 구성 하는 설명서
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Leap 동작
ms.openlocfilehash: 8ef5d26512d50a93691932789e84c099c6246bc3
ms.sourcegitcommit: b4bdac2c4d7315902712ce74fd909fb8383d4bfd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110543239"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="3e790-104">MRTK에서 Ultraleap (Leap 동작) 수동 추적을 구성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="3e790-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="3e790-105">이 데이터 공급자를 사용 하려면 [Leap 동작 컨트롤러가](https://www.ultraleap.com/product/leap-motion-controller/) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="3e790-106">도약 동작 Data Provider는 VR에 대해 트레일러 식 추적을 사용할 수 있으며 편집기에서 빠른 프로토타입 생성에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="3e790-107">데이터 공급자는 헤드셋에 탑재 된 Leap 모션 컨트롤러를 사용 하거나 책상 면에 배치 되도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="3e790-109">이 공급자는 독립 실행형 플랫폼에 있는 동안 편집기 및 장치에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="3e790-110">Uwp 플랫폼에서는 있지만 UWP 빌드에서는 사용 하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="3e790-111">MRTK 버전</span><span class="sxs-lookup"><span data-stu-id="3e790-111">MRTK Version</span></span> | <span data-ttu-id="3e790-112">Leap 동작 Unity 모듈 버전 지원</span><span class="sxs-lookup"><span data-stu-id="3e790-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="3e790-113">2.6. x</span><span class="sxs-lookup"><span data-stu-id="3e790-113">2.6.x</span></span> | <span data-ttu-id="3e790-114">4.5.0, 4.5.1</span><span class="sxs-lookup"><span data-stu-id="3e790-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="3e790-115">2.7. x</span><span class="sxs-lookup"><span data-stu-id="3e790-115">2.7.x</span></span>| <span data-ttu-id="3e790-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span><span class="sxs-lookup"><span data-stu-id="3e790-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="3e790-117">MRTK에서 윤 움직임 (Ultraleap) 직접 추적 사용</span><span class="sxs-lookup"><span data-stu-id="3e790-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="3e790-118">MRTK 및 Leap 동작 Unity 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="3e790-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="3e790-119">최신 [Leap 동작 SDK](https://developer.leapmotion.com/releases/?category=orion) 를 설치 합니다 (아직 설치 하지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="3e790-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="3e790-120">Unity 프로젝트에 **MixedReality** 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="3e790-121">최신 버전의 [Leap 동작 Unity 모듈](https://developer.leapmotion.com/unity) 을 다운로드 하 여 프로젝트로 가져오기</span><span class="sxs-lookup"><span data-stu-id="3e790-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="3e790-122">Unity 모듈 내 에서만 **핵심** 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="3e790-123">도약 동작 Unity 모듈을 MRTK와 통합</span><span class="sxs-lookup"><span data-stu-id="3e790-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="3e790-124">Unity 모듈이 프로젝트에 있으면 **Mixed Reality Toolkit**  >  **leap 동작**  >  **통합 leap 동작 Unity 모듈** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="3e790-125">Unity 모듈을 MRTK에 통합 하면 10 개의 어셈블리 정의가 프로젝트에 추가 되 고 **MixedReality. LeapMotion** 어셈블리 정의에 참조가 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="3e790-126">Visual Studio를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="3e790-128">도약 동작 Data Provider 추가</span><span class="sxs-lookup"><span data-stu-id="3e790-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="3e790-129">새 Unity 장면 만들기</span><span class="sxs-lookup"><span data-stu-id="3e790-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="3e790-130">**Mixed Reality 도구 키트** 로 이동 하 여 장면에 mrtk 추가 장면에 추가  >  **및 구성**</span><span class="sxs-lookup"><span data-stu-id="3e790-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="3e790-131">계층에서 MixedRealityToolkit game 개체를 선택 하 고 **복사 및 사용자 지정** 을 선택 하 여 기본 혼합 현실 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="3e790-133">**입력** 구성 프로필을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-133">Select the **Input** Configuration Profile</span></span>

    ![입력 구성 프로필 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="3e790-135">입력 시스템 프로필에서 **복제** 를 선택 하 여 수정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="3e790-137">**입력 데이터 공급자** 섹션을 열고 맨 위에 있는 **Data Provider 추가** 를 선택 하면 새 데이터 공급자가 목록의 끝에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="3e790-138">새 데이터 공급자를 열고 **유형을** MixedReality로 설정 합니다. **LeapMotion > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="3e790-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Data Provider Leap 추가](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="3e790-140">**복제** 를 선택 하 여 기본 Leap 동작 설정을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="3e790-142">도약 동작 Data Provider는 `LeapControllerOrientation` Leap 동작 컨트롤러의 위치인 속성을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="3e790-143">`LeapControllerOrientation.Headset` 컨트롤러가 헤드셋에 탑재 되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="3e790-144">`LeapControllerOrientation.Desk` 컨트롤러가 책상에 플랫으로 배치 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="3e790-145">기본값은로 설정 됩니다 `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="3e790-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="3e790-146">각 컨트롤러 방향은 오프셋 속성을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="3e790-147">**헤드셋** 방향 오프셋 속성은 LeapXRServiceProvider 구성 요소의 오프셋 속성을 미러링합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="3e790-148">에는 `LeapVRDeviceOffsetMode` 기본, 수동 헤드 오프셋 및 변환의 세 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="3e790-149">오프셋 모드가 기본값 인 경우 오프셋은 윤 동작 컨트롤러에 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="3e790-150">수동 헤드 오프셋 모드에서는 세 가지 속성 `LeapVRDeviceOffsetY` , 및를 수정할 수 있습니다 `LeapVRDeviceOffsetZ` . `LeapVRDeviceTiltX`</span><span class="sxs-lookup"><span data-stu-id="3e790-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="3e790-151">그러면 축 오프셋 속성 값이 기본 컨트롤러 배치에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="3e790-152">변환 오프셋 모드에는 `LeapVRDeviceOrigin` 윤 동작 컨트롤러의 새 원본을 지정 하는 transform 속성이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="3e790-153">**책상** 방향에는 `LeapControllerOffset` 책상 윤 바늘의 앵커 위치를 정의 하는 속성이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="3e790-154">오프셋은 기본 카메라 위치를 기준으로 계산 되며, 기본 값은 (0,-0.2, 0.35)가 카메라의 앞과 뒤에 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="3e790-155">프로필의 오프셋 속성은 응용 프로그램이 시작 될 때 한 번 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="3e790-156">런타임 중에 값을 수정 하려면 Leap 동작 장치 관리자에서 Leap 모션 서비스 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="3e790-157">`EnterPinchDistance` 및 `ExitPinchDistance` 는 하강/공기 탭 제스처 검색의 거리 임계값입니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="3e790-158">손으로 만든 제스처는 인덱스 손가락 팁과 엄지 단추 사이의 거리를 측정 하 여 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="3e790-159">입력 다운 이벤트를 발생 시키려면 기본값 `EnterPinchDistance` 은 0.02로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="3e790-160">입력 시 입력 이벤트를 발생 시키기 위해 (하강 종료) 인덱스 손가락 팁과 엄지 단추 사이의 기본 거리가 0.05입니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="3e790-161">`LeapControllerOrientation`: 헤드셋 (기본값)</span><span class="sxs-lookup"><span data-stu-id="3e790-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="3e790-162">`LeapControllerOrientation`: 책상</span><span class="sxs-lookup"><span data-stu-id="3e790-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="3e790-167">도약 동작 테스트 Data Provider</span><span class="sxs-lookup"><span data-stu-id="3e790-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="3e790-168">입력 시스템 프로필에 도약 이동 Data Provider 추가 된 후 play를 누르고, 윤 동작 컨트롤러 앞으로 손을 이동 하 고, 바늘의 조인트 표현이 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="3e790-169">프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="3e790-169">Building your project</span></span>
    - <span data-ttu-id="3e790-170">**파일 > 빌드 설정** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="3e790-171">Data Provider Leap 동작을 사용 하는 경우 독립 실행형 빌드만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="3e790-172">독립 실행형 빌드에 Windows Mixed Reality 헤드셋을 사용 하는 방법에 대 한 지침은 [MRTK를 WMR 헤드셋에 빌드 및 배포 (독립 실행형)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3e790-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK to WMR Headsets (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="3e790-173">직접 조인트 가져오기</span><span class="sxs-lookup"><span data-stu-id="3e790-173">Getting the hand joints</span></span>

<span data-ttu-id="3e790-174">도약 동작 Data Provider를 사용 하 여 조인트를 가져오는 것은 MRTK에 대 한 직접 검색에 사용 하는 것과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="3e790-175">자세한 내용은 [직접 추적](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3e790-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="3e790-176">Unity 장면에서 MRTK를 사용 하 고 입력 시스템 프로필에 도약 동작을 입력 Data Provider로 추가 Data Provider 빈 게임 개체를 만들고 다음 예제 스크립트를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="3e790-177">이 스크립트는 도약 동작에서 야자나무 조인트의 포즈를 검색 하는 방법의 간단한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="3e790-178">구는 왼쪽 아래에 오는 반면, 정육면체는 오른쪽 윤 바늘을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="3e790-179">Unity 편집기 워크플로 팁</span><span class="sxs-lookup"><span data-stu-id="3e790-179">Unity editor workflow tip</span></span>

<span data-ttu-id="3e790-180">도약 동작 Data Provider를 사용 하는 경우에는 VR 헤드셋이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="3e790-181">MRTK 앱에 대 한 변경 내용을 편집기에서 테스트 하 여 헤드셋 없이 Leap 손을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="3e790-182">Leap 운동 손을 편집기에 표시 하며,이는 VR 헤드셋이 연결 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="3e790-183">`LeapControllerOrientation`가 **헤드셋** 으로 설정 된 경우에는 윤 동작 컨트롤러를 카메라 앞으로 향하는 손을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="3e790-184">편집기에서 WASD 키를 사용 하 여 카메라를 이동 하 고 `LeapControllerOrientation` 가 **헤드셋** 인 경우 손이 카메라를 따르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="3e790-185">가 헤드셋을 설정 하는 동안에는 VR 헤드셋이 연결 된 경우에만 카메라 이동이 진행 됩니다 `LeapControllerOrientation` . </span><span class="sxs-lookup"><span data-stu-id="3e790-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="3e790-186">`LeapControllerOrientation`가 **Desk** 로 설정 된 경우 Leap 손이 편집기에서 카메라 움직임을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="3e790-187">프로젝트에서 Leap 동작 제거</span><span class="sxs-lookup"><span data-stu-id="3e790-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="3e790-188">**Mixed Reality Toolkit**  >  **leap 동작**  >  **별도의 leap 동작 Unity 모듈로** 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="3e790-189">이 단계에서 **MixedReality. LeapMotion** 파일의 참조로 Unity 새로 고침이 수정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="3e790-190">Unity 닫기</span><span class="sxs-lookup"><span data-stu-id="3e790-190">Close Unity</span></span>
1. <span data-ttu-id="3e790-191">열려 있는 경우 Visual Studio를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="3e790-192">파일 탐색기를 열고 MRTK Unity 프로젝트의 루트로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="3e790-193">**Unityprojectname/Library** 디렉터리를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="3e790-194">**Unityprojectname/asset/플러그 인/LeapMotion** 디렉터리를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="3e790-195">**Unityprojectname/asset/플러그 인/LeapMotion** 파일을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="3e790-196">Unity 다시 열기</span><span class="sxs-lookup"><span data-stu-id="3e790-196">Reopen Unity</span></span>

<span data-ttu-id="3e790-197">Unity 2018.4에서 라이브러리와 Leap 동작 코어 자산을 삭제 한 후에도 콘솔에 오류가 계속 남아 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="3e790-198">다시 연 후에 오류가 기록 되 면 Unity를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="3e790-199">일반 오류</span><span class="sxs-lookup"><span data-stu-id="3e790-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="3e790-200">도약 동작이 MRTK와 통합 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="3e790-201">도약 동작 Unity 모듈이 MRTK와 통합 되었는지 테스트 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="3e790-202">**혼합 현실 도구 키트 > 유틸리티 > Leap 동작 > 통합 상태 확인** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="3e790-203">그러면 Leap 동작 Unity 모듈이 MRTK와 통합 되었는지 여부에 대 한 메시지가 포함 된 팝업 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="3e790-204">메시지에 자산이 통합 되지 않은 것으로 표시 되 면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="3e790-205">Leap 동작 Unity 모듈이 프로젝트에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="3e790-206">추가 된 버전이 지원 되는지 확인 하십시오. 지원 되는 버전은 페이지 맨 위에 있는 표를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3e790-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="3e790-207">**혼합 현실 도구 키트 > 유틸리티 > leap 동작 > 사용해 서 Leap 동작 Unity 모듈 통합**</span><span class="sxs-lookup"><span data-stu-id="3e790-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="3e790-208">어셈블리 멀티 플레이 HLAPI 복사 실패</span><span class="sxs-lookup"><span data-stu-id="3e790-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="3e790-209">Leap 동작 Unity 코어 자산의 가져오기 시이 오류가 기록 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="3e790-210">**해결 방법**</span><span class="sxs-lookup"><span data-stu-id="3e790-210">**Solution**</span></span>

- <span data-ttu-id="3e790-211">단기 솔루션은 Unity를 다시 시작 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="3e790-212">자세한 내용은 [문제 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3e790-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="3e790-213">윤 동작 예제 장면</span><span class="sxs-lookup"><span data-stu-id="3e790-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="3e790-214">예제 장면에서는 DefaultLeapMotionConfiguration 프로필을 사용 하 고 Unity 프로젝트가 Leap Data Provider 동작을 사용 하도록 올바르게 구성 되었는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="3e790-215">예제 장면은 **Mrtk/example/데모/수동 추적/** 디렉터리의 **MixedReality** 패키지에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e790-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3e790-216">참조</span><span class="sxs-lookup"><span data-stu-id="3e790-216">See also</span></span>

- [<span data-ttu-id="3e790-217">입력 공급자</span><span class="sxs-lookup"><span data-stu-id="3e790-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="3e790-218">수동 추적</span><span class="sxs-lookup"><span data-stu-id="3e790-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
