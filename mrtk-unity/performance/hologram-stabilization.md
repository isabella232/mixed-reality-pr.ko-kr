---
title: 홀로그램 안정화
description: 다양한 환경 및 프레임 속도 조건에서 홀로그램의 성능.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 환경 추적, TMP,
ms.openlocfilehash: e2c83e7e4ca909e31803d55aabbc0c2344e89139
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143890"
---
# <a name="hologram-stabilization"></a><span data-ttu-id="c9e75-104">홀로그램 안정화</span><span class="sxs-lookup"><span data-stu-id="c9e75-104">Hologram stabilization</span></span>

## <a name="performance"></a><span data-ttu-id="c9e75-105">성능</span><span class="sxs-lookup"><span data-stu-id="c9e75-105">Performance</span></span>

<span data-ttu-id="c9e75-106">기본 혼합 현실 플랫폼 및 디바이스가 최상의 결과를 생성하려면 프레임 속도를 달성하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-106">In order for the underlying mixed reality platform and device to produce the best results, it is important to achieve performing frame rates.</span></span> <span data-ttu-id="c9e75-107">대상 프레임 속도(예: 60 FPS 또는 90 FPS)는 플랫폼 및 디바이스에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-107">The target framerate (ex: 60 FPS or 90 FPS) will vary across platforms and devices.</span></span> <span data-ttu-id="c9e75-108">그러나 프레임 속도 충족 혼합 현실 애플리케이션에는 안정적인 홀로그램뿐만 아니라 효율적인 헤드 추적, 손 추적 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-108">However, mixed reality applications meeting framerate will have stable holograms as well as efficient head tracking, hand tracking and more.</span></span>  

## <a name="environment-tracking"></a><span data-ttu-id="c9e75-109">환경 추적</span><span class="sxs-lookup"><span data-stu-id="c9e75-109">Environment tracking</span></span>

<span data-ttu-id="c9e75-110">안정적인 홀로그램 렌더링은 플랫폼 & 디바이스의 머리 자세 추적에 크게 의존합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-110">Stable holographic rendering heavily relies on head-pose tracking by the platform & device.</span></span> <span data-ttu-id="c9e75-111">Unity는 기본 플랫폼에서 예측하고 제공하는 카메라 자세의 모든 프레임마다 장면을 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-111">Unity will render the scene every frame from the camera pose estimated and supplied by the underlying platform.</span></span> <span data-ttu-id="c9e75-112">이 추적이 실제 머리 이동을 올바르게 따르지 않으면 홀로그램이 시각적으로 부정확하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-112">If this tracking does not correctly follow actual head movement, then holograms will appear visually inaccurate.</span></span> <span data-ttu-id="c9e75-113">이는 특히 사용자가 가상 홀로그램을 실제 세계와 관련할 수 있는 HoloLens와 같은 AR 디바이스에서 분명하고 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-113">This is especially evident and important for AR devices like HoloLens where users can relate virtual holograms to the real world.</span></span> <span data-ttu-id="c9e75-114">성능은 신뢰할 수 있는 헤드 추적에 중요하지만 [다른 중요한 기능도](/windows/mixed-reality/environment-considerations-for-hololens)있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-114">Performance is significant for reliable head tracking, but there can be [other important features](/windows/mixed-reality/environment-considerations-for-hololens), as well.</span></span> <span data-ttu-id="c9e75-115">사용자 환경에 영향을 미치는 환경 요소의 유형은 대상 플랫폼 세부 사항에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-115">The types of environment elements impacting user experience will depend on the targeted platform specifics.</span></span>

## <a name="windows-mixed-reality"></a><span data-ttu-id="c9e75-116">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c9e75-116">Windows Mixed Reality</span></span>

<span data-ttu-id="c9e75-117">Windows Mixed Reality 플랫폼은 플랫폼에서 홀로그램을 안정화하기 위한 몇 가지 [참조 자료를](/windows/mixed-reality/hologram-stability) 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-117">The Windows Mixed Reality platform provides some [reference material](/windows/mixed-reality/hologram-stability) for stabilizing holograms on the platform.</span></span> <span data-ttu-id="c9e75-118">개발자가 사용자의 홀로그램 시각적 환경을 개선하는 데 활용할 수 있는 몇 가지 주요 도구가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-118">There are a handful of key tools though that developers can utilize to improve the hologram visual experience for users.</span></span>

### <a name="depth-buffer-sharing"></a><span data-ttu-id="c9e75-119">깊이 버퍼 공유</span><span class="sxs-lookup"><span data-stu-id="c9e75-119">Depth buffer sharing</span></span>

<span data-ttu-id="c9e75-120">Unity 개발자는 플랫폼과 애플리케이션의 깊이 버퍼를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-120">Unity developers have the option of sharing the application's depth buffer with the platform.</span></span> <span data-ttu-id="c9e75-121">이를 통해 현재 프레임에 홀로그램이 존재하는 경우 플랫폼이 Late-Stage Reprojection이라는 하드웨어 지원 프로세스를 통해 홀로그램을 안정화하는 데 활용할 수 있는 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-121">This provides information, where holograms exist for a current frame, that the platform can utilize to stabilize holograms via a hardware-assisted process known as Late-Stage Reprojection.</span></span>

#### <a name="late-stage-reprojection"></a><span data-ttu-id="c9e75-122">대기 단계 다시 프로젝션</span><span class="sxs-lookup"><span data-stu-id="c9e75-122">Late-stage reprojection</span></span>

<span data-ttu-id="c9e75-123">프레임을 렌더링 하는 끝에 Windows Mixed Reality 플랫폼은 응용 프로그램에서 생성 된 색 & 깊이 렌더링 대상을 사용 하 고 마지막 화면 출력을 변환 하 여 마지막 head 포즈 이후 약간의 이동 작업을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-123">At the end of rendering a frame, the Windows Mixed Reality platform takes the color & depth render targets produced by the application and transforms the final screen output to account for any slight head movement since the last head pose prediction.</span></span> <span data-ttu-id="c9e75-124">응용 프로그램의 게임 루프를 실행 하는 데 시간이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-124">An application's game loop takes time to execute.</span></span> <span data-ttu-id="c9e75-125">예를 들어 60 FPS에서 응용 프로그램은 프레임을 렌더링 하는 데 ~ 16.667 m을 사용 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-125">For example, at 60 FPS, this means the application is taking ~16.667ms to render a frame.</span></span> <span data-ttu-id="c9e75-126">이는 짧습니다 된 시간 처럼 보일 수 있지만, 사용자의 head 위치와 방향은 렌더링 시 카메라에 대 한 새 프로젝션 매트릭스를 변경 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-126">Even though this may seem like a miniscule amount of time, the user's position and orientation of their head will change resulting in new projection matrices for the camera in rendering.</span></span> <span data-ttu-id="c9e75-127">후반 단계 다시 프로젝션은 최종 이미지의 픽셀을이 새로운 큐브 뷰에 대 한 고려로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-127">Late-stage reprojection transforms the pixels in the final image to account for this new perspective.</span></span>

#### <a name="per-pixel-vs-stabilization-plane-lsr"></a><span data-ttu-id="c9e75-128">픽셀당 vs 안정화 평면 LSR</span><span class="sxs-lookup"><span data-stu-id="c9e75-128">Per-pixel vs stabilization plane LSR</span></span>

<span data-ttu-id="c9e75-129">Windows Mixed Reality 장치에서 실행 되는 장치 끝점 및 OS 버전에 따라 Late-Stage Reprojection 알고리즘이 픽셀 당 또는 [안정화 평면](/windows/mixed-reality/hologram-stability#stabilization-plane)을 통해 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-129">Depending on the device endpoint and OS version running on a Windows Mixed Reality device, the Late-Stage Reprojection algorithm will either be performed per-pixel or via a [stabilization plane](/windows/mixed-reality/hologram-stability#stabilization-plane).</span></span>

##### <a name="per-pixel-depth-based"></a><span data-ttu-id="c9e75-130">픽셀 단위 깊이 기반</span><span class="sxs-lookup"><span data-stu-id="c9e75-130">Per-pixel depth-based</span></span>

<span data-ttu-id="c9e75-131">픽셀 단위 깊이 기반 재 프로젝션에는 깊이 버퍼를 활용 하 여 픽셀당 이미지 출력을 수정 하 여 다양 한 거리에서 안정화 하는 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-131">Per-pixel depth-based reprojection involves utilizing the depth buffer to modify the image output per pixel and thus stabilize holograms at various distances.</span></span> <span data-ttu-id="c9e75-132">예를 들어, 10m 떨어져 있는 기둥 앞에 구 1m가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-132">For example, a sphere 1m away may be in front of a pillar that is 10m away.</span></span> <span data-ttu-id="c9e75-133">구를 나타내는 픽셀의 변환은 사용자가 해당 헤드를 약간 기울어진 경우 기둥을 나타내는 멀리 떨어져 있는 픽셀과 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-133">The pixels representing the sphere will have a different transform than the far away pixels representing the pillar if the user has tilted their head slightly.</span></span> <span data-ttu-id="c9e75-134">픽셀 단위 다시 프로젝션은 정확한 다시 프로젝션을 위해 모든 픽셀에서이 거리 차이를 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-134">Per-pixel reprojection will take into account this distance difference at every pixel for more accurate reprojection.</span></span>

##### <a name="stabilization-plane"></a><span data-ttu-id="c9e75-135">안정화 평면</span><span class="sxs-lookup"><span data-stu-id="c9e75-135">Stabilization plane</span></span>

<span data-ttu-id="c9e75-136">플랫폼과 공유할 정확한 깊이 버퍼를 만들 수 없는 경우 다른 형태의 LSR에서 안정화 평면을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-136">If it is not possible to create an accurate depth buffer to share with the platform, another form of LSR utilizes a stabilization plane.</span></span> <span data-ttu-id="c9e75-137">장면의 모든 holograms은 몇 가지 안정화를 수신 하지만 원하는 평면에 있는 holograms는 최대 하드웨어 안정화를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-137">All holograms in a scene will receive some stabilization, but holograms lying in the desired plane will receive the maximum hardware stabilization.</span></span> <span data-ttu-id="c9e75-138">*HolographicSettings* [Unity에서 제공](/windows/mixed-reality/focus-point-in-unity)하는 SetFocusPointForFrame API를 통해 평면에 대 한 point 및 normal을 플랫폼에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-138">The point and normal for the plane can be supplied to the platform via the *HolographicSettings.SetFocusPointForFrame* [API provided by Unity](/windows/mixed-reality/focus-point-in-unity).</span></span>

#### <a name="depth-buffer-format"></a><span data-ttu-id="c9e75-139">깊이 버퍼 형식</span><span class="sxs-lookup"><span data-stu-id="c9e75-139">Depth buffer format</span></span>

<span data-ttu-id="c9e75-140">개발을 위해 HoloLens를 대상으로 하는 경우 24비트 대비 16비트 깊이 버퍼 형식을 활용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-140">If targeting HoloLens for development, it is highly recommended to utilize the 16-bit depth buffer format compared to 24-bit.</span></span> <span data-ttu-id="c9e75-141">깊이 값의 정밀도가 낮아지더라도 성능이 크게 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-141">This can save tremendously on performance although depth values will have less precision.</span></span> <span data-ttu-id="c9e75-142">낮은 정밀도를 보정하고 [z-fighting을](https://en.wikipedia.org/wiki/Z-fighting)방지하려면 Unity에서 설정한 1000m 기본값에서 [원거리 클립 평면을](https://docs.unity3d.com/Manual/class-Camera.html) 줄이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-142">To compensate for the lower precision and avoid [z-fighting](https://en.wikipedia.org/wiki/Z-fighting), it is recommended to reduce the [far clip plane](https://docs.unity3d.com/Manual/class-Camera.html) from the 1000m default value set by Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="c9e75-143">*16비트 깊이 형식을* 사용하는 경우 Unity가 이 설정에서 [스텐실 버퍼를 만들지 않으므로 스텐실 버퍼에](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 필요한 효과가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-143">If using *16-bit depth format*, stencil buffer required effects will not work because [Unity does not create a stencil buffer](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) in this setting.</span></span> <span data-ttu-id="c9e75-144">*24비트 깊이 형식을* 선택하면 일반적으로 엔드포인트 그래픽 플랫폼에 해당하는 경우 [8비트 스텐실 버퍼](https://docs.unity3d.com/Manual/SL-Stencil.html)가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-144">Selecting *24-bit depth format* conversely will generally create an [8-bit stencil buffer](https://docs.unity3d.com/Manual/SL-Stencil.html), if applicable on the endpoint graphics platform.</span></span>

#### <a name="depth-buffer-sharing-in-unity"></a><span data-ttu-id="c9e75-145">Unity의 깊이 버퍼 공유</span><span class="sxs-lookup"><span data-stu-id="c9e75-145">Depth buffer sharing in Unity</span></span>

<span data-ttu-id="c9e75-146">깊이 기반 LSR을 활용하려면 개발자가 수행해야 하는 두 가지 중요한 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-146">In order to utilize depth-based LSR, there are two important steps that developers need to take.</span></span>

1. <span data-ttu-id="c9e75-147">프로젝트 설정 **편집**  >    >  **플레이어**  >  **XR 설정** Virtual Reality  >  **SDK** > 깊이 **버퍼 공유** 사용</span><span class="sxs-lookup"><span data-stu-id="c9e75-147">Under **Edit** > **Project Settings** > **Player** > **XR Settings** > **Virtual Reality SDKs** > Enable **Depth Buffer Sharing**</span></span>
    1. <span data-ttu-id="c9e75-148">HoloLens를 대상으로 하는 경우 **16비트 깊이 형식도** 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-148">If targeting HoloLens, it is recommended to select **16-bit depth format** as well.</span></span>
1. <span data-ttu-id="c9e75-149">화면에서 색을 렌더링하는 경우 렌더링 깊이도</span><span class="sxs-lookup"><span data-stu-id="c9e75-149">When rendering color on screen, render depth as well</span></span>

<span data-ttu-id="c9e75-150">Unity의 [불투명 GameObjects는](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) 일반적으로 깊이에 자동으로 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-150">[Opaque GameObjects](https://docs.unity3d.com/Manual/StandardShaderMaterialParameterRenderingMode.html) in Unity will generally write to depth automatically.</span></span> <span data-ttu-id="c9e75-151">그러나 투명 & 텍스트 개체는 일반적으로 기본적으로 깊이로 작성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-151">However, transparent & text objects will generally not write to depth by default.</span></span> <span data-ttu-id="c9e75-152">MRTK 표준 셰이더 또는 Text Mesh Pro를 활용하는 경우 쉽게 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-152">If utilizing the MRTK Standard Shader or Text Mesh Pro, this can be easily remedied.</span></span>

> [!NOTE]
> <span data-ttu-id="c9e75-153">장면에서 깊이 버퍼에 시각적으로 쓰지 않는 개체를 빠르게 확인하려면 MRTK 구성 프로필의 *편집기 설정에서* [ *렌더링 깊이 버퍼* 유틸리티를](../configuration/mixed-reality-configuration-guide.md#editor-utilities) 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-153">To quickly determine which objects in a scene do not write to the depth buffer visually, one can use the [*Render Depth Buffer* utility](../configuration/mixed-reality-configuration-guide.md#editor-utilities) under the *Editor Settings* in the MRTK Configuration profile.</span></span>

##### <a name="transparent-mrtk-standard-shader"></a><span data-ttu-id="c9e75-154">투명한 MRTK 표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="c9e75-154">Transparent MRTK Standard shader</span></span>

<span data-ttu-id="c9e75-155">[MRTK 표준 셰이더를](../features/rendering/MRTK-standard-shader.md)사용하는 투명 재질의 경우 *검사기* 창에서 볼 재질을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-155">For transparent materials using the [MRTK Standard shader](../features/rendering/MRTK-standard-shader.md), select the material to view it in the *Inspector* window.</span></span> <span data-ttu-id="c9e75-156">그런 다음 *지금 수정* 단추를 클릭하여 재질을 깊이에 쓰도록 변환합니다(즉,</span><span class="sxs-lookup"><span data-stu-id="c9e75-156">Then click the *Fix Now* button to convert the material to write to depth (i.e</span></span> <span data-ttu-id="c9e75-157">Z-Write On).</span><span class="sxs-lookup"><span data-stu-id="c9e75-157">Z-Write On).</span></span>

<span data-ttu-id="c9e75-158">이전</span><span class="sxs-lookup"><span data-stu-id="c9e75-158">Before</span></span>

![MRTK 표준 셰이더를 수정하기 전의 깊이 버퍼](../features/images/performance/DepthBufferFixNow_Before.PNG)

<span data-ttu-id="c9e75-160">이러한</span><span class="sxs-lookup"><span data-stu-id="c9e75-160">After</span></span>

![깊이 버퍼 고정 MRTK 표준 셰이더](../features/images/performance/DepthBufferFixNow_After.PNG)

##### <a name="text-mesh-pro"></a><span data-ttu-id="c9e75-162">텍스트 메시 Pro</span><span class="sxs-lookup"><span data-stu-id="c9e75-162">Text Mesh Pro</span></span>

<span data-ttu-id="c9e75-163">텍스트 메시 Pro 개체의 경우에는 TMP GameObject를 선택 하 여 검사기에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-163">For Text Mesh Pro objects, select the TMP GameObject to view it in the inspector.</span></span> <span data-ttu-id="c9e75-164">재질 구성 요소 아래에서 MRTK TextMeshPro 셰이더를 사용 하도록 할당 된 재질의 셰이더를 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-164">Under the material component, switch the shader for the assigned material to use the MRTK TextMeshPro shader.</span></span>

![텍스트 메시 Pro 깊이 버퍼 수정](../features/images/performance/TextMeshPro-DepthBuffer-Fix.PNG)

##### <a name="custom-shader"></a><span data-ttu-id="c9e75-166">사용자 지정 셰이더</span><span class="sxs-lookup"><span data-stu-id="c9e75-166">Custom shader</span></span>

<span data-ttu-id="c9e75-167">사용자 지정 셰이더를 작성 하는 경우 *통과* 블록 정의 위쪽에 [zwrite 플래그](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) 를 추가 하 여 깊이 버퍼에 쓰도록 셰이더를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-167">If writing a custom shader, add the [ZWrite flag](https://docs.unity3d.com/Manual/SL-CullAndDepth.html) to the top of the *Pass* block definition to configure the shader to write to the depth buffer.</span></span>

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

##### <a name="opaque-backings"></a><span data-ttu-id="c9e75-168">불투명 백</span><span class="sxs-lookup"><span data-stu-id="c9e75-168">Opaque backings</span></span>

<span data-ttu-id="c9e75-169">위의 메서드가 지정 된 시나리오에 대해 작동 하지 않는 경우 (즉,</span><span class="sxs-lookup"><span data-stu-id="c9e75-169">If the above methods do not work for a given scenario (i.e</span></span> <span data-ttu-id="c9e75-170">Unity UI를 사용 하 여 다른 개체가 깊이 버퍼에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-170">using Unity UI), it is possible to have another object write to the depth buffer.</span></span> <span data-ttu-id="c9e75-171">일반적인 예는 장면의 부동 패널에서 Unity UI 텍스트를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-171">A common example is using Unity UI Text on a floating panel in a scene.</span></span> <span data-ttu-id="c9e75-172">패널을 불투명 하 게 만들거나 최소 깊이에 쓰려면 해당 z 값이 서로 가까이 있으므로 패널 & 텍스트가 모두 플랫폼에 의해 안정화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-172">By making the panel opaque or at least writing to depth, then both the text & the panel will be stabilized by the platform since their z-values are so close to each other.</span></span>

### <a name="worldanchors-hololens"></a><span data-ttu-id="c9e75-173">WorldAnchors (HoloLens)</span><span class="sxs-lookup"><span data-stu-id="c9e75-173">WorldAnchors (HoloLens)</span></span>

<span data-ttu-id="c9e75-174">시각적 안정성을 보장 하기 위해 올바른 구성이 충족 되는지 확인 하는 것과 함께 올바른 물리적 위치에서 holograms 안정적으로 유지 되도록 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-174">Along with ensuring the correct configurations are met to ensure visual stability, it is important to ensure holograms remain stable at their correct physical locations.</span></span> <span data-ttu-id="c9e75-175">개발자는 물리적 공간에서 중요 한 위치를 플랫폼에 알리기 위해 한 곳에 유지 해야 하는 Gameobject의 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-175">To inform the platform on important locations in a physical space, developers can leverage [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) on GameObjects that need to stay in one place.</span></span> <span data-ttu-id="c9e75-176">[WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 는 해당 개체의 변환에 대 한 절대 제어를 사용 하는 GameObject에 추가 되는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-176">A [WorldAnchor](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) is a component added to a GameObject that takes absolute control over that object's transform.</span></span>

<span data-ttu-id="c9e75-177">HoloLens와 같은 장치는 계속 해 서 환경을 검색 하 고 학습 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-177">Devices such as HoloLens are constantly scanning and learning about the environment.</span></span> <span data-ttu-id="c9e75-178">따라서 HoloLens에서 이동 & 위치를 트랙으로 이동 하면 해당 추정치는 업데이트 되 고 [Unity 좌표계는 조정](/windows/mixed-reality/coordinate-systems-in-unity)됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-178">Thus, as the HoloLens tracks movement & position in space, its estimates will be updated and the [Unity coordinate system adjusted](/windows/mixed-reality/coordinate-systems-in-unity).</span></span> <span data-ttu-id="c9e75-179">예를 들어 GameObject가 시작 시 카메라에서 1m로 배치 되는 경우 HoloLens는 환경을 추적 하므로 GameObject가 위치한 실제 지점을 실제로 1.1 m 자리까지 발견할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-179">For example, if a GameObject is placed 1m from the camera at start, as the HoloLens tracks the environment, it may realize the physical point where the GameObject is located is actually 1.1m away.</span></span> <span data-ttu-id="c9e75-180">그러면 홀로그램 유동이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-180">This would result in the hologram drifting.</span></span> <span data-ttu-id="c9e75-181">GameObject에 WorldAnchor를 적용 하면 개체가 올바른 실제 위치 (예:)에 유지 되도록 개체의 변환을 제어 하도록 앵커를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-181">Applying a WorldAnchor to a GameObject will enable the anchor to control the object's transform so that the object will remain at the correct physical location (i.e</span></span> <span data-ttu-id="c9e75-182">런타임에 1m 대신 1.1 m 자리까지 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-182">update to 1.1m away instead of 1m at runtime).</span></span> <span data-ttu-id="c9e75-183">응용 프로그램 세션 간에 [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) 을 유지 하기 위해 개발자는 [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) 를 사용 하 여 [WorldAnchors을 저장 하 고 로드할](/windows/mixed-reality/persistence-in-unity)수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-183">To persist [WorldAnchors](https://docs.unity3d.com/ScriptReference/XR.WSA.WorldAnchor.html) across app sessions, developers can employ the [WorldAnchorStore](https://docs.unity3d.com/ScriptReference/XR.WSA.Persistence.WorldAnchorStore.html) to [save and load WorldAnchors](/windows/mixed-reality/persistence-in-unity).</span></span>

> [!NOTE]
> <span data-ttu-id="c9e75-184">GameObject에 WorldAnchor 구성 요소를 추가한 후에는 해당 GameObject의 변환을 수정할 수 없습니다 (즉,</span><span class="sxs-lookup"><span data-stu-id="c9e75-184">Once a WorldAnchor component has been added to a GameObject, it is not possible to modify that GameObject's transform (i.e</span></span> <span data-ttu-id="c9e75-185">transform. position = x).</span><span class="sxs-lookup"><span data-stu-id="c9e75-185">transform.position = x).</span></span> <span data-ttu-id="c9e75-186">개발자는 변환을 편집 하려면 WorldAnchor를 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9e75-186">A developer must remove the WorldAnchor to edit the transform.</span></span>

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

<span data-ttu-id="c9e75-187">수동으로 앵커를 사용 하는 방법에 대 한 대안을 원하는 경우 Microsoft 세계 잠금 도구를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="c9e75-187">If you want an alternative to manually working with Anchors, check out the Microsoft World Locking Tools.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="c9e75-188">MR 기능 도구를 사용 하 여 설치할</span><span class="sxs-lookup"><span data-stu-id="c9e75-188">Instal with the MR Feature Tool</span></span>](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLTviaMRFeatureTool.html)

## <a name="see-also"></a><span data-ttu-id="c9e75-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9e75-189">See also</span></span>

- [<span data-ttu-id="c9e75-190">성능</span><span class="sxs-lookup"><span data-stu-id="c9e75-190">Performance</span></span>](../performance/perf-getting-started.md)
- [<span data-ttu-id="c9e75-191">HoloLens 환경 고려 사항</span><span class="sxs-lookup"><span data-stu-id="c9e75-191">Environment Considerations for HoloLens</span></span>](/windows/mixed-reality/environment-considerations-for-hololens)
- [<span data-ttu-id="c9e75-192">홀로그램 안정성 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c9e75-192">Hologram Stability Windows Mixed Reality</span></span>](/windows/mixed-reality/hologram-stability)
- [<span data-ttu-id="c9e75-193">Unity의 포커스 포인트</span><span class="sxs-lookup"><span data-stu-id="c9e75-193">Focus point in Unity</span></span>](/windows/mixed-reality/focus-point-in-unity)
- [<span data-ttu-id="c9e75-194">Unity의 좌표계</span><span class="sxs-lookup"><span data-stu-id="c9e75-194">Coordinate systems in Unity</span></span>](/windows/mixed-reality/coordinate-systems-in-unity)
- [<span data-ttu-id="c9e75-195">Unity의 지속성</span><span class="sxs-lookup"><span data-stu-id="c9e75-195">Persistence in Unity</span></span>](/windows/mixed-reality/persistence-in-unity)
- [<span data-ttu-id="c9e75-196">혼합 현실 성능 이해</span><span class="sxs-lookup"><span data-stu-id="c9e75-196">Understanding Performance for Mixed Reality</span></span>](/windows/mixed-reality/understanding-performance-for-mixed-reality)
- [<span data-ttu-id="c9e75-197">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="c9e75-197">Performance recommendations for Unity</span></span>](/windows/mixed-reality/performance-recommendations-for-unity)