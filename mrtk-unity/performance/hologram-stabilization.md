---
title: 홀로그램 안정화
description: 다른 환경 및 프레임 속도 조건에서 holograms의 성능
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 환경 추적, TMP,
ms.openlocfilehash: 338ae2719764b84b7c58c1422e08fe02176eccf0
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333435"
---
# <a name="hologram-stabilization"></a><span data-ttu-id="3a3b1-104">홀로그램 안정화</span><span class="sxs-lookup"><span data-stu-id="3a3b1-104">Hologram stabilization</span></span>

## <a name="performance"></a><span data-ttu-id="3a3b1-105">성능</span><span class="sxs-lookup"><span data-stu-id="3a3b1-105">Performance</span></span>

<span data-ttu-id="3a3b1-106">기본 혼합 현실 플랫폼과 장치에서 최상의 결과를 얻으려면 프레임 속도를 수행 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-106">In order for the underlying mixed reality platform and device to produce the best results, it is important to achieve performing frame rates.</span></span> <span data-ttu-id="3a3b1-107">대상 프레임 속도 (예: 60 FPS 또는 90 FPS)는 플랫폼과 장치에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-107">The target framerate (ex: 60 FPS or 90 FPS) will vary across platforms and devices.</span></span> <span data-ttu-id="3a3b1-108">그러나 프레임 속도를 충족 하는 혼합 현실 응용 프로그램은 안정적인 holograms 뿐만 아니라 효율적인 헤드 추적, 수동 추적 등을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-108">However, mixed reality applications meeting framerate will have stable holograms as well as efficient head tracking, hand tracking and more.</span></span>  

## <a name="environment-tracking"></a><span data-ttu-id="3a3b1-109">환경 추적</span><span class="sxs-lookup"><span data-stu-id="3a3b1-109">Environment tracking</span></span>

<span data-ttu-id="3a3b1-110">안정적인 holographic 렌더링은 플랫폼 & 장치에의 한 헤드 포즈 추적에 크게 의존 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-110">Stable holographic rendering heavily relies on head-pose tracking by the platform & device.</span></span> <span data-ttu-id="3a3b1-111">Unity는 카메라의 모든 프레임을 예상 하 고 기본 플랫폼에서 제공 하는 장면으로 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-111">Unity will render the scene every frame from the camera pose estimated and supplied by the underlying platform.</span></span> <span data-ttu-id="3a3b1-112">이 추적이 실제 헤드 이동을 올바르게 따르지 않으면 holograms가 시각적으로 부정확 하 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-112">If this tracking does not correctly follow actual head movement, then holograms will appear visually inaccurate.</span></span> <span data-ttu-id="3a3b1-113">이는 사용자가 가상 holograms를 실제 세계와 연결할 수 있는 HoloLens와 같은 AR 장치에서 특히 명확 하 고 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-113">This is especially evident and important for AR devices like HoloLens where users can relate virtual holograms to the real world.</span></span> <span data-ttu-id="3a3b1-114">안정적인 헤드 추적에는 성능이 중요 하지만 [다른 중요 한 기능도](/windows/mixed-reality/environment-considerations-for-hololens)있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-114">Performance is significant for reliable head tracking, but there can be [other important features](/windows/mixed-reality/environment-considerations-for-hololens), as well.</span></span> <span data-ttu-id="3a3b1-115">사용자 환경에 영향을 주는 환경 요소의 형식은 대상 플랫폼 세부 사항에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-115">The types of environment elements impacting user experience will depend on the targeted platform specifics.</span></span>

## <a name="windows-mixed-reality"></a><span data-ttu-id="3a3b1-116">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3a3b1-116">Windows Mixed Reality</span></span>

<span data-ttu-id="3a3b1-117">Windows Mixed Reality 플랫폼은 플랫폼에서 holograms를 안정화 하기 위한 [참조 자료](/windows/mixed-reality/hologram-stability) 를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-117">The Windows Mixed Reality platform provides some [reference material](/windows/mixed-reality/hologram-stability) for stabilizing holograms on the platform.</span></span> <span data-ttu-id="3a3b1-118">개발자가 사용자를 위한 홀로그램 시각적 환경을 개선 하는 데 활용할 수 있는 몇 가지 주요 도구가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-118">There are a handful of key tools though that developers can utilize to improve the hologram visual experience for users.</span></span>

### <a name="depth-buffer-sharing"></a><span data-ttu-id="3a3b1-119">깊이 버퍼 공유</span><span class="sxs-lookup"><span data-stu-id="3a3b1-119">Depth buffer sharing</span></span>

<span data-ttu-id="3a3b1-120">Unity 개발자에 게는 응용 프로그램의 깊이 버퍼를 플랫폼과 공유할 수 있는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-120">Unity developers have the option of sharing the application's depth buffer with the platform.</span></span> <span data-ttu-id="3a3b1-121">이는 holograms가 현재 프레임에 대 한 정보를 제공 하 고, 플랫폼은 Late-Stage Reprojection 이라는 하드웨어 기반 프로세스를 통해 안정화 holograms을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-121">This provides information, where holograms exist for a current frame, that the platform can utilize to stabilize holograms via a hardware-assisted process known as Late-Stage Reprojection.</span></span>

#### <a name="late-stage-reprojection"></a><span data-ttu-id="3a3b1-122">후반 단계 다시 프로젝션</span><span class="sxs-lookup"><span data-stu-id="3a3b1-122">Late-stage reprojection</span></span>

<span data-ttu-id="3a3b1-123">프레임 렌더링이 끝나면 Windows Mixed Reality 플랫폼은 애플리케이션에서 생성된 색 & 깊이 렌더링 대상을 가져와서 마지막 머리 자세 예측 이후 약간의 머리 이동을 고려하여 최종 화면 출력을 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-123">At the end of rendering a frame, the Windows Mixed Reality platform takes the color & depth render targets produced by the application and transforms the final screen output to account for any slight head movement since the last head pose prediction.</span></span> <span data-ttu-id="3a3b1-124">애플리케이션의 게임 루프를 실행하는 데 시간이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-124">An application's game loop takes time to execute.</span></span> <span data-ttu-id="3a3b1-125">예를 들어 60 FPS에서 애플리케이션이 프레임을 렌더링하는 데 최대 16.667ms가 걸리는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-125">For example, at 60 FPS, this means the application is taking ~16.667ms to render a frame.</span></span> <span data-ttu-id="3a3b1-126">이는 최소한의 시간처럼 보일 수 있지만, 사용자의 머리 위치와 방향이 변경되어 렌더링에서 카메라에 대한 새로운 프로젝션 행렬이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-126">Even though this may seem like a miniscule amount of time, the user's position and orientation of their head will change resulting in new projection matrices for the camera in rendering.</span></span> <span data-ttu-id="3a3b1-127">마지막 단계 다시 프로젝션은 이 새로운 큐브 뷰를 고려하도록 최종 이미지의 픽셀을 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-127">Late-stage reprojection transforms the pixels in the final image to account for this new perspective.</span></span>

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a><span data-ttu-id="3a3b1-128">픽셀당 및 안정화 평면 LSR</span><span class="sxs-lookup"><span data-stu-id="3a3b1-128">Per-pixel vs stabilization plane LSR</span></span>

<span data-ttu-id="3a3b1-129">Windows Mixed Reality 디바이스에서 실행되는 디바이스 엔드포인트 및 OS 버전에 따라 Late-Stage 다시 프로젝션 알고리즘은 픽셀당 또는 [안정화 평면을](/windows/mixed-reality/hologram-stability#stabilization-plane)통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-129">Depending on the device endpoint and OS version running on a Windows Mixed Reality device, the Late-Stage Reprojection algorithm will either be performed per-pixel or via a [stabilization plane](/windows/mixed-reality/hologram-stability#stabilization-plane).</span></span>

##### <a name="per-pixel-depth-based"></a><span data-ttu-id="3a3b1-130">픽셀당 깊이 기반</span><span class="sxs-lookup"><span data-stu-id="3a3b1-130">Per-pixel depth-based</span></span>

<span data-ttu-id="3a3b1-131">픽셀별 깊이 기반 다시 프로젝션에는 깊이 버퍼를 활용하여 픽셀당 이미지 출력을 수정하여 다양한 거리에 있는 홀로그램을 안정화하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-131">Per-pixel depth-based reprojection involves utilizing the depth buffer to modify the image output per pixel and thus stabilize holograms at various distances.</span></span> <span data-ttu-id="3a3b1-132">예를 들어 1m 떨어진 구는 10m 떨어진 핵심 요소 앞에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-132">For example, a sphere 1m away may be in front of a pillar that is 10m away.</span></span> <span data-ttu-id="3a3b1-133">구를 나타내는 픽셀은 사용자가 헤드를 약간 기울인 경우 핵심을 나타내는 멀리 떨어진 픽셀과 다른 변환을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-133">The pixels representing the sphere will have a different transform than the far away pixels representing the pillar if the user has tilted their head slightly.</span></span> <span data-ttu-id="3a3b1-134">픽셀당 다시 프로젝션은 보다 정확한 다시 프로젝션을 위해 모든 픽셀에서 이 거리 차이를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-134">Per-pixel reprojection will take into account this distance difference at every pixel for more accurate reprojection.</span></span>

##### <a name="stabilization-plane"></a><span data-ttu-id="3a3b1-135">안정화 평면</span><span class="sxs-lookup"><span data-stu-id="3a3b1-135">Stabilization plane</span></span>

<span data-ttu-id="3a3b1-136">플랫폼과 공유할 정확한 깊이 버퍼를 만들 수 없는 경우 또 다른 형태의 LSR은 안정화 평면을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-136">If it is not possible to create an accurate depth buffer to share with the platform, another form of LSR utilizes a stabilization plane.</span></span> <span data-ttu-id="3a3b1-137">장면의 모든 홀로그램은 일부 안정화를 받지만 원하는 평면에 있는 홀로그램은 최대 하드웨어 안정화를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-137">All holograms in a scene will receive some stabilization, but holograms lying in the desired plane will receive the maximum hardware stabilization.</span></span> <span data-ttu-id="3a3b1-138">평면의 점과 표준은 Unity에서 제공하는 *HolographicSettings.SetFocusPointForFrame* [API를](/windows/mixed-reality/focus-point-in-unity)통해 플랫폼에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-138">The point and normal for the plane can be supplied to the platform via the *HolographicSettings.SetFocusPointForFrame* [API provided by Unity](/windows/mixed-reality/focus-point-in-unity).</span></span>

#### <a name="depth-buffer-format"></a><span data-ttu-id="3a3b1-139">깊이 버퍼 형식</span><span class="sxs-lookup"><span data-stu-id="3a3b1-139">Depth buffer format</span></span>

<span data-ttu-id="3a3b1-140">개발을 위해 HoloLens를 대상으로 지정 하는 경우 24 비트와 비교 하 여 16 비트 깊이 버퍼 형식을 활용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-140">If targeting HoloLens for development, it is highly recommended to utilize the 16-bit depth buffer format compared to 24-bit.</span></span> <span data-ttu-id="3a3b1-141">이 경우 깊이 값의 정밀도가 크게 성능이 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-141">This can save tremendously on performance although depth values will have less precision.</span></span> <span data-ttu-id="3a3b1-142">더 낮은 정밀도를 보정 하 고 [z를 사용](https://en.wikipedia.org/wiki/Z-fighting)하지 않도록 하려면 Unity에 설정 된 1000m 기본값에서 [먼 클립 평면](https://docs.unity3d.com/Manual/class-Camera.html) 을 줄이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-142">To compensate for the lower precision and avoid [z-fighting](https://en.wikipedia.org/wiki/Z-fighting), it is recommended to reduce the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) from the 1000m default value set by Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="3a3b1-143">*16 비트 깊이 형식을* 사용 하는 경우 Unity에서이 설정에 [스텐실 버퍼를 만들지](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 않으므로 스텐실 버퍼 필요 효과가 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-143">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="3a3b1-144">이와 반대로 *24 비트 깊이 형식을* 선택 하면 일반적으로 끝점 그래픽 플랫폼에 해당 하는 경우 [8 비트 스텐실 버퍼가](https://docs.unity3d.com/Manual/SL-Stencil.html)생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-144">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html), if applicable on the endpoint graphics platform.</span></span>

#### <a name="depth-buffer-sharing-in-unity"></a><span data-ttu-id="3a3b1-145">Unity의 깊이 버퍼 공유</span><span class="sxs-lookup"><span data-stu-id="3a3b1-145">Depth buffer sharing in Unity</span></span>

<span data-ttu-id="3a3b1-146">깊이 기반 LSR를 활용 하기 위해 개발자가 수행 해야 하는 두 가지 중요 한 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-146">In order to utilize depth-based LSR, there are two important steps that developers need to take.</span></span>

1. <span data-ttu-id="3a3b1-147">  >  **프로젝트 설정** 편집에서  >  **플레이어**  >  **XR 설정**  >  **가상 현실 sdk** > **깊이 버퍼 공유** 사용</span><span class="sxs-lookup"><span data-stu-id="3a3b1-147">Under **Edit** > **Project Settings** > **Player** > **XR Settings** > **Virtual Reality SDKs** > Enable **Depth Buffer Sharing**</span></span>
    1. <span data-ttu-id="3a3b1-148">HoloLens를 대상으로 하는 경우 **16 비트 깊이 형식만** 선택 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-148">If targeting HoloLens, it is recommended to select **16-bit depth format** as well.</span></span>
1. <span data-ttu-id="3a3b1-149">화면에서 색을 렌더링할 때 깊이도 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-149">When rendering color on screen, render depth as well</span></span>

<span data-ttu-id="3a3b1-150">Unity의 [불투명 gameobject](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) 일반적으로 깊이에 자동으로 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-150">[Opaque GameObjects](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) in Unity will generally write to depth automatically.</span></span> <span data-ttu-id="3a3b1-151">그러나 투명 & 텍스트 개체는 일반적으로 기본적으로 깊이에 기록 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-151">However, transparent & text objects will generally not write to depth by default.</span></span> <span data-ttu-id="3a3b1-152">MRTK 표준 셰이더 또는 텍스트 메시 Pro를 활용 하는 경우이를 쉽게 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-152">If utilizing the MRTK Standard Shader or Text Mesh Pro, this can be easily remedied.</span></span>

> [!NOTE]
> <span data-ttu-id="3a3b1-153">장면에서 깊이 버퍼에 시각적으로 쓰지 않는 개체를 신속 하 게 확인 하기 위해 MRTK 구성 프로필의 *편집기 설정* 에서 [ *렌더링 수준 버퍼* 유틸리티](../configuration/mixed-reality-configuration-guide.md#editor-utilities) 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-153">To quickly determine which objects in a scene do not write to the depth buffer visually, one can use the [*Render Depth Buffer* utility](../configuration/mixed-reality-configuration-guide.md#editor-utilities) under the *Editor Settings* in the MRTK Configuration profile.</span></span>

##### <a name="transparent-mrtk-standard-shader"></a><span data-ttu-id="3a3b1-154">투명 MRTK 표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="3a3b1-154">Transparent MRTK Standard shader</span></span>

<span data-ttu-id="3a3b1-155">[Mrtk 표준 셰이더](../features/rendering/MRTK-standard-shader.md)를 사용 하는 투명 재질의 경우 *검사기* 창에서 볼 자료를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-155">For transparent materials using the [MRTK Standard shader](../features/rendering/MRTK-standard-shader.md), select the material to view it in the *Inspector* window.</span></span> <span data-ttu-id="3a3b1-156">그런 다음 [ *지금 수정* ] 단추를 클릭 하 여 자료를 자세히 (즉,</span><span class="sxs-lookup"><span data-stu-id="3a3b1-156">Then click the *Fix Now* button to convert the material to write to depth (i.e</span></span> <span data-ttu-id="3a3b1-157">Z-쓰기).</span><span class="sxs-lookup"><span data-stu-id="3a3b1-157">Z-Write On).</span></span>

<span data-ttu-id="3a3b1-158">이전</span><span class="sxs-lookup"><span data-stu-id="3a3b1-158">Before</span></span>

![MRTK 표준 셰이더 수정 전 깊이 버퍼](../features/images/performance/DepthBufferFixNow_Before.PNG)

<span data-ttu-id="3a3b1-160">After</span><span class="sxs-lookup"><span data-stu-id="3a3b1-160">After</span></span>

![깊이 버퍼 고정 MRTK 표준 셰이더](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a><span data-ttu-id="3a3b1-162">Text Mesh Pro</span><span class="sxs-lookup"><span data-stu-id="3a3b1-162">Text Mesh Pro</span></span>

<span data-ttu-id="3a3b1-163">Text Mesh Pro 개체의 경우 TMP GameObject를 선택하여 검사기에서 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-163">For Text Mesh Pro objects, select the TMP GameObject to view it in the inspector.</span></span> <span data-ttu-id="3a3b1-164">재질 구성 요소 아래에서 할당된 재질의 셰이더를 전환하여 MRTK TextMeshPro 셰이더를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-164">Under the material component, switch the shader for the assigned material to use the MRTK TextMeshPro shader.</span></span>

![Text Mesh Pro Depth 버퍼 수정](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a><span data-ttu-id="3a3b1-166">사용자 지정 셰이더</span><span class="sxs-lookup"><span data-stu-id="3a3b1-166">Custom shader</span></span>

<span data-ttu-id="3a3b1-167">사용자 지정 셰이더를 작성하는 경우 *Pass* 블록 정의의 맨 위에 [ZWrite 플래그를](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) 추가하여 깊이 버퍼에 쓰도록 셰이더를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-167">If writing a custom shader, add the [ZWrite flag](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) to the top of the *Pass* block definition to configure the shader to write to the depth buffer.</span></span>

```
Shader "Custom/MyShader"
{
    SubShader
    {
        Pass
        {
            ...
            ZWrite On
            ...
        }
    }
}
```

##### <a name="opaque-backings"></a><span data-ttu-id="3a3b1-168">불투명 지원</span><span class="sxs-lookup"><span data-stu-id="3a3b1-168">Opaque backings</span></span>

<span data-ttu-id="3a3b1-169">위의 메서드가 지정된 시나리오에서 작동하지 않는 경우(즉,</span><span class="sxs-lookup"><span data-stu-id="3a3b1-169">If the above methods do not work for a given scenario (i.e</span></span> <span data-ttu-id="3a3b1-170">Unity UI를 사용하여 깊이 버퍼에 다른 개체를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-170">using Unity UI), it is possible to have another object write to the depth buffer.</span></span> <span data-ttu-id="3a3b1-171">일반적인 예는 장면의 부동 패널에서 Unity UI 텍스트를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-171">A common example is using Unity UI Text on a floating panel in a scene.</span></span> <span data-ttu-id="3a3b1-172">패널을 불투명하게 만들거나 최소한 깊이에 쓰면 패널의 텍스트 & z-값이 서로 너무 가깝기 때문에 플랫폼에 의해 안정화됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-172">By making the panel opaque or at least writing to depth, then both the text & the panel will be stabilized by the platform since their z-values are so close to each other.</span></span>

### <a name="worldanchors-hololens"></a><span data-ttu-id="3a3b1-173">WorldAnchors(HoloLens)</span><span class="sxs-lookup"><span data-stu-id="3a3b1-173">WorldAnchors (HoloLens)</span></span>

<span data-ttu-id="3a3b1-174">시각적 안정성을 보장하기 위해 올바른 구성을 충족하는지 확인하는 것 외에 홀로그램이 올바른 물리적 위치에서 안정적으로 유지되도록 하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-174">Along with ensuring the correct configurations are met to ensure visual stability, it is important to ensure holograms remain stable at their correct physical locations.</span></span> <span data-ttu-id="3a3b1-175">물리적 공간의 중요한 위치에 대해 플랫폼에 알리기 위해 개발자는 한 곳에 유지해야 하는 GameObjects에서 [WorldAnchors를](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-175">To inform the platform on important locations in a physical space, developers can leverage [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) on GameObjects that need to stay in one place.</span></span> <span data-ttu-id="3a3b1-176">[WorldAnchor는](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 해당 개체의 변환을 절대 제어하는 GameObject에 추가된 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-176">A [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) is a component added to a GameObject that takes absolute control over that object's transform.</span></span>

<span data-ttu-id="3a3b1-177">HoloLens와 같은 디바이스는 지속적으로 환경을 검색하고 학습합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-177">Devices such as HoloLens are constantly scanning and learning about the environment.</span></span> <span data-ttu-id="3a3b1-178">따라서 HoloLens는 공간에서 이동 & 위치를 추적하므로 예상값이 업데이트되고 [Unity 좌표계가 조정됩니다.](/windows/mixed-reality/coordinate-systems-in-unity)</span><span class="sxs-lookup"><span data-stu-id="3a3b1-178">Thus, as the HoloLens tracks movement & position in space, its estimates will be updated and the [Unity coordinate system adjusted](/windows/mixed-reality/coordinate-systems-in-unity).</span></span> <span data-ttu-id="3a3b1-179">예를 들어, GameObject가 시작 시 카메라에서 1m 정도 배치되는 경우 HoloLens가 환경을 추적할 때 GameObject가 있는 물리적 지점이 실제로 1.1m 떨어져 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-179">For example, if a GameObject is placed 1m from the camera at start, as the HoloLens tracks the environment, it may realize the physical point where the GameObject is located is actually 1.1m away.</span></span> <span data-ttu-id="3a3b1-180">이로 인해 홀로그램이 드리프트될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-180">This would result in the hologram drifting.</span></span> <span data-ttu-id="3a3b1-181">GameObject에 WorldAnchor를 적용하면 앵커가 개체의 변환을 제어하여 개체가 올바른 물리적 위치(즉,</span><span class="sxs-lookup"><span data-stu-id="3a3b1-181">Applying a WorldAnchor to a GameObject will enable the anchor to control the object's transform so that the object will remain at the correct physical location (i.e</span></span> <span data-ttu-id="3a3b1-182">런타임에 1m 대신 1.1 m 자리까지 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-182">update to 1.1m away instead of 1m at runtime).</span></span> <span data-ttu-id="3a3b1-183">응용 프로그램 세션 간에 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 을 유지 하기 위해 개발자는 [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) 를 사용 하 여 [WorldAnchors을 저장 하 고 로드할](/windows/mixed-reality/persistence-in-unity)수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-183">To persist [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) across app sessions, developers can employ the [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) to [save and load WorldAnchors](/windows/mixed-reality/persistence-in-unity).</span></span>

> [!NOTE]
> <span data-ttu-id="3a3b1-184">GameObject에 WorldAnchor 구성 요소를 추가한 후에는 해당 GameObject의 변환을 수정할 수 없습니다 (즉,</span><span class="sxs-lookup"><span data-stu-id="3a3b1-184">Once a WorldAnchor component has been added to a GameObject, it is not possible to modify that GameObject's transform (i.e</span></span> <span data-ttu-id="3a3b1-185">transform. position = x).</span><span class="sxs-lookup"><span data-stu-id="3a3b1-185">transform.position = x).</span></span> <span data-ttu-id="3a3b1-186">개발자는 변환을 편집 하려면 WorldAnchor를 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-186">A developer must remove the WorldAnchor to edit the transform.</span></span>

```c#
WorldAnchor m_anchor;

public void AddAnchor()
{
    this.m_anchor = this.gameObject.AddComponent<WorldAnchor>();
}

public void RemoveAnchor()
{
    DestroyImmediate(m_anchor);
}
```

<span data-ttu-id="3a3b1-187">수동으로 앵커를 사용 하는 방법에 대 한 대안을 원하는 경우 Microsoft 세계 잠금 도구를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="3a3b1-187">If you want an alternative to manually working with Anchors, check out the Microsoft World Locking Tools.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a3b1-188">MR 기능 도구를 사용 하 여 설치</span><span class="sxs-lookup"><span data-stu-id="3a3b1-188">Install with the MR Feature Tool</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a><span data-ttu-id="3a3b1-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a3b1-189">See also</span></span>

- [<span data-ttu-id="3a3b1-190">성능</span><span class="sxs-lookup"><span data-stu-id="3a3b1-190">Performance</span></span>](../performance/perf-getting-started.md)
- [<span data-ttu-id="3a3b1-191">HoloLens 환경 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3a3b1-191">Environment Considerations for HoloLens</span></span>](/windows/mixed-reality/environment-considerations-for-hololens)
- [<span data-ttu-id="3a3b1-192">홀로그램 안정성 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3a3b1-192">Hologram Stability Windows Mixed Reality</span></span>](/windows/mixed-reality/hologram-stability)
- [<span data-ttu-id="3a3b1-193">Unity의 포커스 포인트</span><span class="sxs-lookup"><span data-stu-id="3a3b1-193">Focus point in Unity</span></span>](/windows/mixed-reality/focus-point-in-unity)
- [<span data-ttu-id="3a3b1-194">Unity의 좌표계</span><span class="sxs-lookup"><span data-stu-id="3a3b1-194">Coordinate systems in Unity</span></span>](/windows/mixed-reality/coordinate-systems-in-unity)
- [<span data-ttu-id="3a3b1-195">Unity의 지속성</span><span class="sxs-lookup"><span data-stu-id="3a3b1-195">Persistence in Unity</span></span>](/windows/mixed-reality/persistence-in-unity)
- [<span data-ttu-id="3a3b1-196">혼합 현실 성능 이해</span><span class="sxs-lookup"><span data-stu-id="3a3b1-196">Understanding Performance for Mixed Reality</span></span>](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [<span data-ttu-id="3a3b1-197">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="3a3b1-197">Performance recommendations for Unity</span></span>](/windows/mixed-reality/performance-recommendations-for-unity)