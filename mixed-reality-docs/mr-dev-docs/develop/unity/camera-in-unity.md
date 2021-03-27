---
title: Unity에서 카메라 설정
description: Holographic 렌더링을 수행 하기 위해 Windows Mixed Reality 개발용 Unity의 기본 카메라를 설정 하 고 사용 하는 방법에 대해 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, holographic 렌더링, holographic, 몰입 형, 포커스 지점, 깊이 버퍼, 방향 전용, 위치, 불투명, 투명, 클립, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636306"
---
# <a name="camera-setup-in-unity"></a><span data-ttu-id="d3bd1-104">Unity에서 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="d3bd1-104">Camera setup in Unity</span></span>

<span data-ttu-id="d3bd1-105">혼합 현실 헤드셋을 착용 하면 holographic 세계의 중심이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="d3bd1-106">Unity [카메라](https://docs.unity3d.com/Manual/class-Camera.html) 구성 요소는 stereoscopic 렌더링을 자동으로 처리 하 고 헤드 이동 및 회전을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-106">The Unity [Camera](https://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and follow your head movement and rotation.</span></span> <span data-ttu-id="d3bd1-107">그러나 시각적 품질 및 [홀로그램 안정성](../platform-capabilities-and-apis/hologram-stability.md)을 완벽 하 게 최적화 하려면 아래에서 설명 하는 카메라 설정을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-107">However, to fully optimize visual quality and [hologram stability](../platform-capabilities-and-apis/hologram-stability.md), you should set the camera settings described below.</span></span>

## <a name="hololens-vs-vr-immersive-headsets"></a><span data-ttu-id="d3bd1-108">HoloLens vs VR 모던 헤드셋</span><span class="sxs-lookup"><span data-stu-id="d3bd1-108">HoloLens vs VR immersive headsets</span></span>

<span data-ttu-id="d3bd1-109">Unity 카메라 구성 요소의 기본 설정은 일반적인 3D 응용 프로그램을 위한 것 이며 실제 세계에 있지 않기 때문에 skybox 같은 배경을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-109">The default settings on the Unity Camera component are for traditional 3D applications, which need a skybox-like background as they don't have a real world.</span></span>

* <span data-ttu-id="d3bd1-110">**[몰입 형 헤드셋](../../discover/immersive-headset-hardware-details.md)** 에서 실행 하는 경우 사용자에 게 표시 되는 모든 항목을 렌더링 하 게 되므로 skybox를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-110">When running on an **[immersive headset](../../discover/immersive-headset-hardware-details.md)**, you're rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="d3bd1-111">그러나 [HoloLens](/hololens/hololens2-hardware)와 같은 **holographic 헤드셋** 에서 실행 하는 경우 실제 세계는 카메라에서 렌더링 하는 모든 항목 뒤에 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-111">However, when running on a **holographic headset** like [HoloLens](/hololens/hololens2-hardware), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="d3bd1-112">Skybox 질감이 아닌 카메라 배경을 투명 하 게 설정 합니다 (HoloLens에서 검정색 렌더링 투명).</span><span class="sxs-lookup"><span data-stu-id="d3bd1-112">Set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="d3bd1-113">계층 패널에서 주 카메라를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-113">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="d3bd1-114">검사기 패널에서 카메라 구성 요소를 찾아 Clear Flags dropdown을 Skybox에서 Solid Color로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-114">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="d3bd1-115">배경색 선택을 선택 하 고 RGBA 값을 (0, 0, 0, 0)으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-115">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>
        1. <span data-ttu-id="d3bd1-116">코드에서이 설정을 사용 하는 경우 Unity의 [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span><span class="sxs-lookup"><span data-stu-id="d3bd1-116">If setting this from code, you can use Unity's [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span></span>

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a><span data-ttu-id="d3bd1-117">카메라 설정</span><span class="sxs-lookup"><span data-stu-id="d3bd1-117">Camera setup</span></span>

<span data-ttu-id="d3bd1-118">개발 중인 모든 종류의 환경에서 기본 카메라는 항상 장치의 헤드 탑재 디스플레이에 연결 된 기본 스테레오 렌더링 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-118">Whatever kind of experience you're developing, the Main Camera is always the primary stereo rendering component attached to your device's head-mounted display.</span></span> <span data-ttu-id="d3bd1-119">사용자의 시작 위치 (X: 0, Y: 0, Z: 0)를 사용 하는 경우 앱의 레이아웃을 보다 쉽게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-119">It'll be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="d3bd1-120">주 카메라가 사용자 헤드의 이동을 추적 하므로 기본 카메라의 시작 위치를 설정 하 여 사용자의 시작 위치를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-120">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

<span data-ttu-id="d3bd1-121">선택 해야 하는 중심은 HoloLens 또는 VR 모던 헤드셋을 개발 하 고 있는지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-121">The central choice you need to make is whether you're developing for HoloLens or VR immersive headsets.</span></span> <span data-ttu-id="d3bd1-122">이를 받은 후에는 적용 되는 설정 섹션으로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-122">Once you've got that, skip to whichever setup section applies.</span></span>

### <a name="hololens-camera-setup"></a><span data-ttu-id="d3bd1-123">HoloLens 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="d3bd1-123">HoloLens camera setup</span></span>

<span data-ttu-id="d3bd1-124">HoloLens 앱의 경우 장면 환경에 잠그려는 모든 개체에 대 한 앵커를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-124">For HoloLens apps, you need to use anchors for any objects you want to lock to the scene environment.</span></span> <span data-ttu-id="d3bd1-125">제한 없는 공간을 사용 하 여 안정성을 최대화 하 고 여러 방에 앵커를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-125">We recommend using unbounded space to maximize stability and create anchors in multiple rooms.</span></span>

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a><span data-ttu-id="d3bd1-126">VR 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="d3bd1-126">VR camera setup</span></span>

<span data-ttu-id="d3bd1-127">Windows Mixed Reality는 규모에 상관 없이 공간 규모 앱을 통해 응용 프로그램을 수평으로 확장 하 여 규모에 상관 없이 광범위 한 [환경](../../design/coordinate-systems.md#mixed-reality-experience-scales)에서 앱을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-127">Windows Mixed Reality supports apps across a wide range of [experience scales](../../design/coordinate-systems.md#mixed-reality-experience-scales), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="d3bd1-128">HoloLens에서 더 나아가 사용자가 5 미터 이상 이동할 수 있도록 하는 세계적인 규모의 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-128">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="d3bd1-129">Unity에서 혼합 현실 환경을 빌드하는 첫 번째 단계는 앱이 대상으로 하는 [환경 크기](../../design/coordinate-systems.md) 를 결정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-129">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](../../design/coordinate-systems.md) your app will target:</span></span>

* [<span data-ttu-id="d3bd1-130">방향 또는 고정 크기 조정</span><span class="sxs-lookup"><span data-stu-id="d3bd1-130">Orientation or seated-scale</span></span>](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [<span data-ttu-id="d3bd1-131">단일 또는 공간 규모</span><span class="sxs-lookup"><span data-stu-id="d3bd1-131">Standing or room-scale</span></span>](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [<span data-ttu-id="d3bd1-132">전 세계 규모</span><span class="sxs-lookup"><span data-stu-id="d3bd1-132">World-scale</span></span>](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a><span data-ttu-id="d3bd1-133">공간 규모 또는 서 환경</span><span class="sxs-lookup"><span data-stu-id="d3bd1-133">Room-scale or standing experiences</span></span>

> [!NOTE]
> <span data-ttu-id="d3bd1-134">HL2에 대해 빌드하는 경우에는 눈에 잘 맞는 환경을 만드는 것이 좋습니다. 또는 장면의 밑면에 대 한 이유를 [장면 이해](../platform-capabilities-and-apis/scene-understanding-sdk.md) 를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-134">If you're building for HL2, we recommend creating an eye-level experience, or consider using [Scene Understanding](../platform-capabilities-and-apis/scene-understanding-sdk.md) to reason about the floor of your scene.</span></span>

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a><span data-ttu-id="d3bd1-135">장착 환경</span><span class="sxs-lookup"><span data-stu-id="d3bd1-135">Seated experiences</span></span>

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a><span data-ttu-id="d3bd1-136">카메라 배경 설정</span><span class="sxs-lookup"><span data-stu-id="d3bd1-136">Setting up the camera background</span></span>

<span data-ttu-id="d3bd1-137">MRTK를 사용 하는 경우 카메라의 배경이 자동으로 구성 되 고 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-137">If you're using MRTK, the camera's background is automatically configured and managed.</span></span> <span data-ttu-id="d3bd1-138">XR SDK 또는 레거시 WSA 프로젝트의 경우 카메라의 배경을 HoloLens의 검정색으로 설정 하 고 VR의 skybox을 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-138">For XR SDK or Legacy WSA projects, we recommend setting the camera's background to solid black on HoloLens and keeping the skybox for VR.</span></span>

## <a name="using-multiple-cameras"></a><span data-ttu-id="d3bd1-139">여러 카메라 사용</span><span class="sxs-lookup"><span data-stu-id="d3bd1-139">Using multiple cameras</span></span>

<span data-ttu-id="d3bd1-140">장면에 여러 카메라 구성 요소가 있는 경우 Unity는 MainCamera 태그가 있는 GameObject을 기준으로 stereoscopic 렌더링에 사용할 카메라를 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-140">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering based on which GameObject has the MainCamera tag.</span></span> <span data-ttu-id="d3bd1-141">레거시 XR에서이 태그를 사용 하 여 헤드 추적을 동기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-141">In legacy XR, it also uses this tag to sync head tracking.</span></span> <span data-ttu-id="d3bd1-142">XR SDK에서 헤드 추적은 카메라에 연결 된 TrackedPoseDriver 스크립트에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-142">In XR SDK, head tracking is driven by a TrackedPoseDriver script attached to the camera.</span></span>

## <a name="sharing-depth-buffers"></a><span data-ttu-id="d3bd1-143">깊이 버퍼 공유</span><span class="sxs-lookup"><span data-stu-id="d3bd1-143">Sharing depth buffers</span></span>

<span data-ttu-id="d3bd1-144">Windows에 앱의 깊이 버퍼를 공유 하면 각 프레임에서 렌더링 하는 헤드셋의 유형에 따라 홀로그램 안정성의 두 가지 향상 된 기능 중 하나를 앱에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-144">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>

* <span data-ttu-id="d3bd1-145">**VR 모던 헤드셋** 은 깊이 버퍼가 제공 될 때 위치를 다시 프로젝션 하 여 위치와 방향 모두에서 misprediction에 대 한 holograms를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-145">**VR immersive headsets** can take care of positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="d3bd1-146">**HoloLens 헤드셋** 에는 몇 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-146">**HoloLens headsets** have a few different methods.</span></span> <span data-ttu-id="d3bd1-147">HoloLens 1은 깊이 버퍼가 제공 될 때 [포커스 지점을](focus-point-in-unity.md) 자동으로 선택 하 여 대부분의 콘텐츠와 교차 하는 평면을 따라 홀로그램의 안정성을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-147">HoloLens 1 will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span> <span data-ttu-id="d3bd1-148">HoloLens 2는 [깊이 LSR (설명 참조)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)을 사용 하 여 콘텐츠를 안정화 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-148">HoloLens 2 will stabilize content using [Depth LSR (see Remarks)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span></span>

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a><span data-ttu-id="d3bd1-149">클리핑 평면 사용</span><span class="sxs-lookup"><span data-stu-id="d3bd1-149">Using clipping planes</span></span>

<span data-ttu-id="d3bd1-150">사용자에 게 너무 가까운 렌더링 콘텐츠는 혼합 현실에서 불편을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-150">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="d3bd1-151">카메라 구성 요소에서 [근거리 및 원거리 클립 평면](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) 을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-151">You can adjust the [near and far clip planes](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>

1. <span data-ttu-id="d3bd1-152">**계층** 패널에서 **주 카메라** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-152">Select the **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="d3bd1-153">**검사기** 패널에서 **평면 클리핑** **카메라** 구성 요소를 찾아 **가까운** 텍스트 상자를 **0.3** 에서 **0.85** 으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-153">In the **Inspector** panel, find the **Camera** component **Clipping Planes** and change the **Near** textbox from **0.3** to **0.85**.</span></span> <span data-ttu-id="d3bd1-154">더 가까이 렌더링 된 콘텐츠는 사용자 discomfort 발생할 수 있으므로 [렌더링 거리 지침](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)에 따라 피해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-154">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span></span>

## <a name="recentering-the-camera"></a><span data-ttu-id="d3bd1-155">카메라 입력</span><span class="sxs-lookup"><span data-stu-id="d3bd1-155">Recentering the camera</span></span>

<span data-ttu-id="d3bd1-156">통합 된 [환경을](../../design/coordinate-systems.md)구축 하는 경우 XR를 호출 하 여 사용자의 현재 헤드 위치에서 Unity의 세계 원본을 recenter 수 있습니다 **[.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 레거시 XR의 Recenter 메서드 또는 XR SDK의 **[Xrinputsubsystem. TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** 메서드</span><span class="sxs-lookup"><span data-stu-id="d3bd1-156">If you're building a [seated-scale experience](../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method in legacy XR or the **[XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** method in XR SDK.</span></span>

## <a name="teleportation"></a><span data-ttu-id="d3bd1-157">순간 이동</span><span class="sxs-lookup"><span data-stu-id="d3bd1-157">Teleportation</span></span>

<span data-ttu-id="d3bd1-158">이 기능은 일반적으로 VR 환경용으로 예약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-158">This feature is typically reserved for VR experiences:</span></span>

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a><span data-ttu-id="d3bd1-159">재 투영 모드</span><span class="sxs-lookup"><span data-stu-id="d3bd1-159">Reprojection modes</span></span>

<span data-ttu-id="d3bd1-160">HoloLens 및 몰입 형 헤드셋은 모두 앱이 렌더링 하는 각 프레임을 다시 프로젝션 하 여 photons를 내보낼 때 사용자의 실제 헤드 위치 misprediction 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-160">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="d3bd1-161">기본적으로 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-161">By default:</span></span>

* <span data-ttu-id="d3bd1-162">응용 프로그램에서 지정 된 프레임에 대 한 깊이 버퍼를 제공 하는 경우 **VR 모던 헤드셋** 은 위치 다시 프로젝션을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-162">**VR immersive headsets** will take care of positional reprojection if the app provides a depth buffer for a given frame.</span></span> <span data-ttu-id="d3bd1-163">또한 몰입 형 헤드셋은 위치와 방향 모두에서 misprediction에 대 한 holograms을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-163">Immersive headsets will also adjust your holograms for misprediction in both position and orientation.</span></span> <span data-ttu-id="d3bd1-164">깊이 버퍼가 제공 되지 않은 경우 시스템은 방향 으로만 mispredictions을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-164">If a depth buffer isn't provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="d3bd1-165">HoloLens 2와 같은 **Holographic 헤드셋** 은 앱이 깊이 버퍼를 제공 하는지 여부에 관계 없이 위치를 다시 프로젝션 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-165">**Holographic headsets** like HoloLens 2 will take care of positional reprojection whether the app provides its depth buffer or not.</span></span> <span data-ttu-id="d3bd1-166">렌더링은 실제 세계에서 제공 하는 안정적인 배경을 사용 하는 스파스 인 경우가 많기 때문에 HoloLens의 깊이 버퍼 없이 위치 다시 프로젝션이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-166">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="d3bd1-167">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="d3bd1-167">Next Development Checkpoint</span></span>

<span data-ttu-id="d3bd1-168">앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-168">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="d3bd1-169">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-169">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d3bd1-170">응시</span><span class="sxs-lookup"><span data-stu-id="d3bd1-170">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="d3bd1-171">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-171">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d3bd1-172">공유 환경</span><span class="sxs-lookup"><span data-stu-id="d3bd1-172">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="d3bd1-173">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3bd1-173">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3bd1-174">참조</span><span class="sxs-lookup"><span data-stu-id="d3bd1-174">See also</span></span>

* [<span data-ttu-id="d3bd1-175">홀로그램 안정성</span><span class="sxs-lookup"><span data-stu-id="d3bd1-175">Hologram stability</span></span>](../platform-capabilities-and-apis/hologram-stability.md)
* [<span data-ttu-id="d3bd1-176">환경 크기 조정</span><span class="sxs-lookup"><span data-stu-id="d3bd1-176">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="d3bd1-177">공간 스테이지</span><span class="sxs-lookup"><span data-stu-id="d3bd1-177">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="d3bd1-178">Unity의 손실 추적</span><span class="sxs-lookup"><span data-stu-id="d3bd1-178">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="d3bd1-179">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d3bd1-179">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="d3bd1-180">Unity의 지속성</span><span class="sxs-lookup"><span data-stu-id="d3bd1-180">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="d3bd1-181">Unity의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="d3bd1-181">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="d3bd1-182">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d3bd1-182">Azure Spatial Anchors</span></span>](/azure/spatial-anchors)
* [<span data-ttu-id="d3bd1-183">Unity 용 Azure 공간 앵커 SDK</span><span class="sxs-lookup"><span data-stu-id="d3bd1-183">Azure Spatial Anchors SDK for Unity</span></span>](/dotnet/api/Microsoft.Azure.SpatialAnchors)