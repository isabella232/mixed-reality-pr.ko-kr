---
title: Unity 입력 포팅 가이드
description: Unity에서 Windows Mixed Reality의 입력을 처리 하는 방법에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: 입력, unity, 포팅
ms.openlocfilehash: 97280ff260729bfc2042f7760fa3950e949e27a4
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613267"
---
# <a name="input-porting-guide-for-unity"></a><span data-ttu-id="d6267-104">Unity 입력 포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="d6267-104">Input porting guide for Unity</span></span>

<span data-ttu-id="d6267-105">두 가지 방법 중 하나를 사용 하 여 Windows Mixed Reality에 입력 논리를 이식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-105">You can port your input logic to Windows Mixed Reality using one of two approaches.</span></span> <span data-ttu-id="d6267-106">첫 번째 방법은 Unity의 일반 입력을 사용 하는 것입니다. GetButton/Getbutton Api는 여러 플랫폼에 걸쳐 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-106">The first is to use Unity's general Input.GetButton/GetAxis APIs that span across multiple platforms.</span></span> <span data-ttu-id="d6267-107">두 번째는 Windows 관련 XR입니다. WSA. 입력 Api-동작 컨트롤러 및 HoloLens 바늘에 대해 더 다양 한 데이터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-107">The second is the Windows-specific XR.WSA.Input APIs, which offer richer data specifically for motion controllers and HoloLens hands.</span></span>

## <a name="general-inputgetbuttongetaxis-apis"></a><span data-ttu-id="d6267-108">일반 입력. GetButton/Getbutton Api</span><span class="sxs-lookup"><span data-stu-id="d6267-108">General Input.GetButton/GetAxis APIs</span></span>

<span data-ttu-id="d6267-109">Unity는 현재 일반 입력을 사용 합니다. GetButton/Input. Getbutton Api를 사용 하 여 [Oculus sdk](https://docs.unity3d.com/Manual/OculusControllers.html) 및 [openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html)의 입력을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-109">Unity currently uses its general Input.GetButton/Input.GetAxis APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) and [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html).</span></span> <span data-ttu-id="d6267-110">앱이 입력에 이러한 Api를 이미 사용 하 고 있는 경우에는 입력. GetButton/Input. Getbutton Api는 Windows Mixed Reality에서 동작 컨트롤러를 지원 하기에 가장 쉬운 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-110">If your apps are already using these APIs for input, the Input.GetButton/Input.GetAxis APIs are the easiest paths for supporting motion controllers in Windows Mixed Reality.</span></span> <span data-ttu-id="d6267-111">입력 관리자에서 단추 및 축만 다시 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-111">You'll only need to remap buttons and axes in the Input Manager.</span></span>

<span data-ttu-id="d6267-112">자세한 내용은 [unity 단추/축 매핑 표](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 및 [일반적인 unity api 개요](../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d6267-112">For more information, see the [Unity button/axis mapping table](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) and the [overview of the common Unity APIs](../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).</span></span>

## <a name="windows-specific-xrwsainput-apis"></a><span data-ttu-id="d6267-113">Windows 관련 XR. WSA. 입력 Api</span><span class="sxs-lookup"><span data-stu-id="d6267-113">Windows-specific XR.WSA.Input APIs</span></span>

<span data-ttu-id="d6267-114">앱에서 각 플랫폼에 대 한 사용자 지정 입력 논리를 이미 빌드하는 경우 **XR** 네임 스페이스에서 Windows 관련 공간 입력 api를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-114">If your app already builds custom input logic for each platform, you can use the Windows-specific spatial input APIs in the **UnityEngine.XR.WSA.Input** namespace.</span></span> <span data-ttu-id="d6267-115">여기에서 위치 정확도 나 원본 종류와 같은 추가 정보에 액세스 하 여 HoloLens와 컨트롤러를 따로 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-115">From there, you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart on HoloLens.</span></span>

<span data-ttu-id="d6267-116">자세한 내용은 [UnityEngine. XR api 개요](../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d6267-116">For more information, see the [overview of the UnityEngine.XR.WSA.Input APIs](../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="d6267-117">그립 포즈 및 포인팅 포즈</span><span class="sxs-lookup"><span data-stu-id="d6267-117">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="d6267-118">Windows Mixed Reality는 다양 한 폼 팩터에서 동작 컨트롤러를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-118">Windows Mixed Reality supports motion controllers in different form factors.</span></span> <span data-ttu-id="d6267-119">각 컨트롤러의 디자인은 사용자의 손 위치와 앱이 컨트롤러를 렌더링할 때를 가리키는 데 사용 해야 하는 자연 스러운 "전달" 방향 간의 관계에 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-119">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="d6267-120">이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스에 대해 조사할 수 있는 두 가지 종류의 포즈가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-120">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>

* <span data-ttu-id="d6267-121">그립은 HoloLens에서 감지한 손바닥의 위치 또는 이동 컨트롤러를 보유 하는 야자수의 위치를 나타내는 **그립 포즈** 입니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-121">The **grip pose**, which represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="d6267-122">모던 헤드셋에서는이 포즈를 사용 하 여 사용자 **의 손을** 나 **사용자의 손으로 보유 한 개체**(예: 소드 또는 포)를 렌더링 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-122">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="d6267-123">**그립 위치**: 컨트롤러를 자연스럽 게 유지 하는 경우 왼쪽 또는 오른쪽으로 조정 하 여 그립 내 위치를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-123">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="d6267-124">**그립 방향 오른쪽 축**: 손 모양 5 손가락 포즈를 형성 하는 손을 완전히 열 때 palm (왼쪽 야자나무에서 오른쪽으로 뒤로)의 광선을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-124">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="d6267-125">**그립 방향 전방 축**: 컨트롤러를 보유 하 고 있는 것 처럼, 손 모양 없는 손가락으로 구성 된 튜브를 통해 "전달" 하는 빛을 부분적으로 닫는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-125">The **grip orientation's Forward axis**: When you close your hand partially, as if holding the controller, the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="d6267-126">**그립 방향 up 축**: 오른쪽 및 전방 정의에 의해 암시 된 위쪽 축입니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-126">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="d6267-127">Unity의 교차 공급 업체 입력 API (XR)를 통해 그립 포즈에 액세스할 수 있습니다 **[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) 또는 Windows 특정 API (**sourcestate/Rotation**, 그립 포즈 요청)를 통해</span><span class="sxs-lookup"><span data-stu-id="d6267-127">You can access the grip pose through either Unity's cross-vendor input API (**[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation**) or through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Grip pose).</span></span>
* <span data-ttu-id="d6267-128">앞에 있는 컨트롤러의 팁을 나타내는 **포인터가 포즈** 입니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-128">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="d6267-129">이 포즈는 컨트롤러 모델 자체를 렌더링할 때 **UI를 가리킬** 때 raycast에 가장 잘 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-129">This pose is best used to raycast when **pointing at UI** when you're rendering the controller model itself.</span></span>
    * <span data-ttu-id="d6267-130">현재 포인터 포즈는 Windows 관련 API (**Sourcestate/Rotation**, 포인터 포즈 요청)를 통해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-130">Currently, the pointer pose is available only through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Pointer pose).</span></span>

<span data-ttu-id="d6267-131">이러한 포즈 좌표는 모두 Unity 세계 좌표로 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6267-131">These pose coordinates are all expressed in Unity world coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6267-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6267-132">See also</span></span>
* <span data-ttu-id="d6267-133">[동작 컨트롤러](). /.. /design/motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="d6267-133">[Motion controllers]()../../design/motion-controllers.md)</span></span>
* [<span data-ttu-id="d6267-134">Unity의 제스처 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="d6267-134">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="d6267-135">UnityEngine. XR</span><span class="sxs-lookup"><span data-stu-id="d6267-135">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="d6267-136">UnityEngine. XR 추적</span><span class="sxs-lookup"><span data-stu-id="d6267-136">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="d6267-137">포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="d6267-137">Porting guides</span></span>](porting-guides.md)
