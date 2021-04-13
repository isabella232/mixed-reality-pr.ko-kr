---
title: 수동으로 직접 조작
description: 사용자가 홀로그램을 직접 손으로 터치하는 입력 조작에 대해 알아봅니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 응시, 응시 타깃팅, 상호 작용, 디자인, 핸즈 니어, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit, 단추, 충돌체, 경계 상자, 2D, 직관적 제스처
ms.openlocfilehash: 555b27764d077332a2d8618672e6aed7def1dd3f
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300098"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="7497f-104">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="7497f-104">Direct manipulation with hands</span></span>

![단추](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="7497f-106">직접 조작은 홀로그램을 손으로 직접 터치하게 되는 입력 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="7497f-107">이 개념의 기본 아이디어는 개체가 실제 세계에서처럼 작동하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="7497f-108">단추는 간단히 눌러서 활성화하고, 개체는 잡아서 선택할 수 있으며, 2D 콘텐츠는 가상의 터치 스크린처럼 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="7497f-109">직접 조작은 어포던스를 기반으로 합니다. 즉, 사용자에게 친숙합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="7497f-110">사용자를 교육하기 위한 기호화된 제스처는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="7497f-111">모든 상호 작용은 사용자가 터치하거나 잡을 수 있는 시각적 요소를 중심으로 구축됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="7497f-112">팔을 뻗어 닿을 수 있는 콘텐츠와 상호 작용하는 데 가장 적합하다는 점에서 “근거리” 입력 모델로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="7497f-113">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="7497f-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="7497f-114"><strong>입력 모델</strong></span><span class="sxs-lookup"><span data-stu-id="7497f-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="7497f-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7497f-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="7497f-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="7497f-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="7497f-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="7497f-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="7497f-118">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="7497f-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="7497f-119">❌ 지원 안 됨</span><span class="sxs-lookup"><span data-stu-id="7497f-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="7497f-120">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="7497f-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="7497f-121"> 지원됨.</span><span class="sxs-lookup"><span data-stu-id="7497f-121">➕ Supported.</span></span>  <span data-ttu-id="7497f-122">UI의 경우 대신 <a href="point-and-commit.md">손을 사용하여 가리키고 커밋</a>하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="7497f-123">직접 조작은 HoloLens 2의 기본 입력 모델이며, 새로운 연결형 손 추적 시스템을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="7497f-124">입력 모델은 모션 컨트롤러를 사용하여 몰입형 헤드셋에서도 사용할 수 있지만, 개체 조작 이외의 상호 작용을 위한 기본 수단으로 추천되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="7497f-125">HoloLens(1세대)에서는 직접 조작을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="7497f-126">충돌 가능한 손끝</span><span class="sxs-lookup"><span data-stu-id="7497f-126">Collidable fingertip</span></span>

<span data-ttu-id="7497f-127">HoloLens 2에서 사용자의 손은 왼손 및 오른손 골격 모델로 인식 및 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-127">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="7497f-128">손으로 홀로그램을 직접 터치한다는 개념을 적절히 구현하기 위해 각 손 골격 모델의 5개 손끝에 5개의 충돌체(collider)를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-128">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="7497f-129">그러나 촉각 피드백이 부족하므로 충돌 가능한 10개의 손가락 끝으로 인해 홀로그램과 예기치 않은 충돌이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-129">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="7497f-130">각 집게손가락에만 충돌체(collider)를 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-130">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="7497f-131">충돌 가능한 집게손가락 끝은 다른 손가락을 포함하는 다양한 터치 제스처에 대한 활성 터치 지점으로 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="7497f-132">터치 제스처에는 아래와 같이 한 손가락으로 누르기, 한 손가락으로 탭하기, 두 손가락으로 누르기 및 다섯 손가락으로 누르기가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-132">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="7497f-133">![충돌 가능한 손끝](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-133">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="7497f-134">**충돌 가능한 손끝**</span><span class="sxs-lookup"><span data-stu-id="7497f-134">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-135">![한 손가락으로 누르기](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-135">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="7497f-136">**한 손가락으로 누르기**</span><span class="sxs-lookup"><span data-stu-id="7497f-136">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-137">![한 손가락으로 탭하기](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-137">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="7497f-138">**한 손가락으로 탭하기**</span><span class="sxs-lookup"><span data-stu-id="7497f-138">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-139">![다섯 손가락으로 누르기](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-139">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="7497f-140">**다섯 손가락으로 누르기**</span><span class="sxs-lookup"><span data-stu-id="7497f-140">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="7497f-141">구형 충돌체(collider)</span><span class="sxs-lookup"><span data-stu-id="7497f-141">Sphere collider</span></span>

<span data-ttu-id="7497f-142">임의의 일반 셰이프를 사용하는 대신, 구형 충돌체(collider)를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-142">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="7497f-143">그러면, 시각적 렌더링을 통해 근거리 대상 지정에 더 나은 단서를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-143">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="7497f-144">터치 정확도를 높이려면 구의 지름이 집게 손가락의 두께와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-144">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="7497f-145">손 API를 호출하여 손가락 두께 변수를 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-145">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="7497f-146">손끝 커서</span><span class="sxs-lookup"><span data-stu-id="7497f-146">Fingertip cursor</span></span>

<span data-ttu-id="7497f-147">충돌 가능한 구체를 집게손가락 끝에 렌더링하는 것 외에도 고급 손가락 끝 커서를 만들어 더 나은 근거리 대상 지정 환경을 구현했습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-147">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="7497f-148">이는 집게손가락 끝에 연결되는 도넛형 커서입니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-148">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="7497f-149">아래에서 설명한 대로 근접성에 따라 대상의 방향 및 크기에 대해 동적으로 반응합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-149">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="7497f-150">집게손가락이 홀로그램으로 움직이면 커서는 항상 홀로그램 표면과 평행이 되고 크기가 점차적으로 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-150">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="7497f-151">손가락으로 표면을 터치하는 즉시, 커서가 점으로 축소되고 터치 이벤트를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-151">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="7497f-152">대화형 피드백을 사용하면 사용자는 아래와 같이 하이퍼링크 트리거 또는 단추 누르기와 같은 높은 정확도의 근거리 대상 지정 작업을 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-152">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="7497f-153">![손끝 커서 멀리](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-153">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="7497f-154">**손끝 커서 멀리**</span><span class="sxs-lookup"><span data-stu-id="7497f-154">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-155">![손끝 커서 가까이](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-155">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="7497f-156">**손끝 커서 가까이**</span><span class="sxs-lookup"><span data-stu-id="7497f-156">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-157">![손끝 커서 접촉](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-157">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="7497f-158">**손끝 커서 접촉**</span><span class="sxs-lookup"><span data-stu-id="7497f-158">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="7497f-159">근접 셰이더가 있는 경계 상자</span><span class="sxs-lookup"><span data-stu-id="7497f-159">Bounding box with proximity shader</span></span>

<span data-ttu-id="7497f-160">홀로그램 자체에는 촉각 피드백 부족을 보정하기 위해 시각적 및 청각적 피드백을 둘 다 제공하는 기능도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-160">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="7497f-161">이를 위해 근접 셰이더를 포함하는 경계 상자 개념을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-161">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="7497f-162">경계 상자는 3D 개체를 둘러싸는 최소 체적 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-162">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="7497f-163">경계 상자에는 근접 셰이더라는 대화형 렌더링 메커니즘이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-163">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="7497f-164">근접 셰이더는 다음과 같이 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-164">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="7497f-165">![시각적 피드백이 있는 가리키기(멀리)](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-165">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="7497f-166">**가리키기(멀리)**</span><span class="sxs-lookup"><span data-stu-id="7497f-166">**Hover (far)**</span></span><br>
       <span data-ttu-id="7497f-167">집게 손가락이 범위 내에 있는 경우 손끝 스포트라이트가 경계 상자 표면에 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-167">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-168">![시각적 피드백이 있는 가리키기(가까이)](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-168">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="7497f-169">**가리키기(가까이)**</span><span class="sxs-lookup"><span data-stu-id="7497f-169">**Hover (near)**</span></span><br>
        <span data-ttu-id="7497f-170">손가락 끝이 표면에 가까워지면 스포트라이트가 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-170">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-171">![접촉 시작](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-171">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="7497f-172">**접촉 시작**</span><span class="sxs-lookup"><span data-stu-id="7497f-172">**Contact begins**</span></span><br>
       <span data-ttu-id="7497f-173">손끝이 표면을 터치하는 즉시, 전체 경계 상자의 색상이 바뀌거나 터치 상태를 반영하는 시각적 효과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-173">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-174">![접촉 끝](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-174">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="7497f-175">**접촉 끝**</span><span class="sxs-lookup"><span data-stu-id="7497f-175">**Contact ends**</span></span><br>
       <span data-ttu-id="7497f-176">또한 시각적 터치 피드백을 향상시키기 위해 음향 효과를 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-176">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="7497f-177">누를 수 있는 단추</span><span class="sxs-lookup"><span data-stu-id="7497f-177">Pressable button</span></span>

<span data-ttu-id="7497f-178">충돌 가능한 손끝을 사용하면 사용자가 기본적인 홀로그래픽 UI 구성 요소(예: 누를 수 있는 단추)와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-178">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="7497f-179">누를 수 있는 단추는 직접적인 손가락 누르기에 맞게 조정된 홀로그래픽 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-179">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="7497f-180">다시 말하지만, 촉각 피드백이 부족하므로 누를 수 있는 단추에는 촉각 피드백 관련 문제를 해결하기 위한 몇 가지 메커니즘이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-180">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="7497f-181">첫 번째 메커니즘은 근접 셰이더가 있는 경계 상자이며, 이전 섹션에 자세히 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-181">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="7497f-182">이 메커니즘은 사용자가 단추에 접근하여 접촉할 때 더 근접한 느낌을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-182">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="7497f-183">두 번째 메커니즘은 누르기입니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-183">The second mechanism is depression.</span></span> <span data-ttu-id="7497f-184">누르기는 손끝이 단추에 닿은 후 아래쪽을 누르는 감각을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-184">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="7497f-185">이 메커니즘은 단추가 손끝에 맞춰 깊이 축을 따라 움직이도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-185">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="7497f-186">단추는 선택한 깊이에 도달하거나(누를 때) 해당 깊이를 통과한 후 떠나면(뗄 때) 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-186">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="7497f-187">단추가 트리거될 때 피드백을 향상시키기 위해 음향 효과를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-187">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="7497f-188">![누를 수 있는 단추 멀리](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-188">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="7497f-189">**멀리 있는 손가락**</span><span class="sxs-lookup"><span data-stu-id="7497f-189">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-190">![누를 수 있는 단추 가까이](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-190">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="7497f-191">**접근하는 손가락**</span><span class="sxs-lookup"><span data-stu-id="7497f-191">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-192">![누를 수 있는 단추 접촉 시작](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-192">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="7497f-193">**접촉 시작**</span><span class="sxs-lookup"><span data-stu-id="7497f-193">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-194">![누를 수 있는 단추 누르기](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-194">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="7497f-195">**아래로 누르기**</span><span class="sxs-lookup"><span data-stu-id="7497f-195">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="7497f-196">2D 슬레이트 상호 작용</span><span class="sxs-lookup"><span data-stu-id="7497f-196">2D slate interaction</span></span>

<span data-ttu-id="7497f-197">2D [슬레이트](slate.md)는 웹 브라우저와 같은 2D 앱 콘텐츠를 호스트하는 데 사용되는 홀로그램 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-197">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="7497f-198">직접 조작을 통해 2D 슬레이트와 상호 작용하기 위한 디자인 개념은 실제 터치 화면과 상호 작용하는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-198">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="7497f-199">슬레이트 접촉 부분과 상호 작용하려면</span><span class="sxs-lookup"><span data-stu-id="7497f-199">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="7497f-200">![터치](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-200">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="7497f-201">**터치**</span><span class="sxs-lookup"><span data-stu-id="7497f-201">**Touch**</span></span><br>
       <span data-ttu-id="7497f-202">집게 손가락으로 하이퍼링크 또는 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-202">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-203">![스크롤](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-203">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="7497f-204">**스크롤**</span><span class="sxs-lookup"><span data-stu-id="7497f-204">**Scroll**</span></span><br>
        <span data-ttu-id="7497f-205">집게 손가락으로 슬레이트 콘텐츠 위/아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-205">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-206">![확대/축소](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="7497f-207">**확대/축소**</span><span class="sxs-lookup"><span data-stu-id="7497f-207">**Zoom**</span></span><br>
       <span data-ttu-id="7497f-208">사용자는 2개의 집게 손가락을 사용하여 손가락의 상대적 모션에 따라 슬레이트 콘텐츠를 확대 및 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-208">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="7497f-209">2D 슬레이트 자체를 조작하려면</span><span class="sxs-lookup"><span data-stu-id="7497f-209">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="7497f-210">![잡기 및 끌기 기능을 보여 주는 그래픽](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-210">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="7497f-211">**이동**</span><span class="sxs-lookup"><span data-stu-id="7497f-211">**Move**</span></span><br>
       <span data-ttu-id="7497f-212">손을 모서리와 가장자리 쪽으로 이동하여 가장 가까운 조작 어포던스를 드러냅니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-212">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="7497f-213">2D 슬레이트의 맨 위에 있는 홀로바를 잡으면, 슬레이트 전체를 옮길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-213">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-214">![크기 조정 기능을 보여 주는 그래픽](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-214">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="7497f-215">**크기 조정**</span><span class="sxs-lookup"><span data-stu-id="7497f-215">**Scale**</span></span><br>
        <span data-ttu-id="7497f-216">조작 어포던스를 잡고, 모서리 어포던스를 통해 균일한 크기 조정을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-216">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-217">![재배치](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-217">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="7497f-218">**재배치**</span><span class="sxs-lookup"><span data-stu-id="7497f-218">**Reflow**</span></span><br>
       <span data-ttu-id="7497f-219">조작 어포던스를 잡고, 가장자리 어포던스를 통해 재배치를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-219">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="7497f-220">3D 개체 조작</span><span class="sxs-lookup"><span data-stu-id="7497f-220">3D object manipulation</span></span>

<span data-ttu-id="7497f-221">HoloLens 2에서는 사용자가 3D 개체마다 경계 상자를 적용하여 손으로 3D 홀로그래픽 개체를 겨냥하고 조작할 수 잇습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-221">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="7497f-222">경계 상자는 근접 셰이더를 통해 더 나은 깊이 인식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-222">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="7497f-223">경계 상자를 사용하면 3D 개체 조작을 위해 두 가지 디자인 방식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-223">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="7497f-224">어포던스 기반 조작</span><span class="sxs-lookup"><span data-stu-id="7497f-224">Affordance-based manipulation</span></span>

<span data-ttu-id="7497f-225">어포던스 기반 조작에서는 경계 상자와 주변의 조작 어포던스를 통해 3D 개체를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-225">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="7497f-226">![개체 경계 상자와 이동 기능을 보여 주는 그래픽](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-226">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="7497f-227">**이동**</span><span class="sxs-lookup"><span data-stu-id="7497f-227">**Move**</span></span><br>
       <span data-ttu-id="7497f-228">사용자의 손이 3D 개체에 가까워지는 즉시 경계 상자 및 가장 가까운 어포던스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-228">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="7497f-229">사용자가 경계 상자를 잡고 전체 개체를 옮길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-229">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-230">![사용자가 회전할 개체 가장자리를 잡는 것을 보여 주는 그래픽](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-230">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="7497f-231">**회전**</span><span class="sxs-lookup"><span data-stu-id="7497f-231">**Rotate**</span></span><br>
        <span data-ttu-id="7497f-232">사용자가 가장자리 어포던스를 잡아서 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-232">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-233">![사용자가 개체 모서리를 잡아서 크기를 조정하는 것을 보여 주는 그래픽](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-233">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="7497f-234">**크기 조정**</span><span class="sxs-lookup"><span data-stu-id="7497f-234">**Scale**</span></span><br>
       <span data-ttu-id="7497f-235">사용자가 모서리 어포던스를 잡아서 균일하게 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-235">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="7497f-236">비 어포던스 기반 조작</span><span class="sxs-lookup"><span data-stu-id="7497f-236">Non-affordance-based manipulation</span></span>

<span data-ttu-id="7497f-237">비 어포던스 기반 조작은 어포던스를 경계 상자에 연결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-237">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="7497f-238">사용자는 경계 상자만 표시한 후 직접 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-238">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="7497f-239">한 손으로 경계 상자를 잡을 경우 개체의 변환 및 회전은 손의 동작 및 방향과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-239">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="7497f-240">두 손으로 경계 상자를 잡을 경우 두 손의 상대적 동작에 따라 변환, 크기 조정 및 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-240">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="7497f-241">특정 조작에는 정밀도가 요구됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-241">Specific manipulation requires precision.</span></span> <span data-ttu-id="7497f-242">따라서 더 높은 세분성을 제공하는 **어포던스 기반 조작** 을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-242">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="7497f-243">유연한 조작을 위해서는 즉각적이면서 유용한 환경을 지원하는 **비어포던스 조작** 을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-243">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="7497f-244">직관적 제스처</span><span class="sxs-lookup"><span data-stu-id="7497f-244">Instinctual gestures</span></span>

<span data-ttu-id="7497f-245">HoloLens(1세대)에서는 미리 정의된 몇 가지 제스처(예: 블룸 및 에어 탭)를 사용자에게 학습시켰습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-245">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="7497f-246">HoloLens 2에서는 사용자에게 기호화된 제스처를 기억하도록 요구하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-246">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="7497f-247">사용자가 홀로그램 및 콘텐츠와 상호 작용하는 데 필요한 모든 제스처는 직관적입니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-247">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="7497f-248">직관적 제스처를 달성하는 방법은 사용자가 UI 어포던스의 디자인을 통해 제스처를 수행하도록 돕는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-248">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="7497f-249">예를 들어, 사용자가 두 손가락 모으기로 개체나 제어점을 잡도록 하려면 개체나 제어점이 작아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-249">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="7497f-250">사용자가 다섯 손가락으로 잡기를 수행하도록 하려면 개체 또는 제어 지점이 비교적 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-250">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="7497f-251">단추와 마찬가지로 작은 단추는 사용자가 한 손가락으로 누르도록 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-251">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="7497f-252">큰 단추는 사용자가 손바닥으로 누르도록 유도합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-252">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="7497f-253">![사용자가 이동할 작은 개체를 잡는 것을 보여 주는 그래픽](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-253">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="7497f-254">**소형 개체**</span><span class="sxs-lookup"><span data-stu-id="7497f-254">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-255">![사용자가 이동할 중간 개체를 잡는 것을 보여 주는 그래픽](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-255">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="7497f-256">**중형 개체**</span><span class="sxs-lookup"><span data-stu-id="7497f-256">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7497f-257">![사용자가 이동할 큰 개체를 잡는 것을 보여 주는 그래픽](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="7497f-257">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="7497f-258">**대형 개체**</span><span class="sxs-lookup"><span data-stu-id="7497f-258">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="7497f-259">손과 6 DoF 컨트롤러 간의 대칭 디자인</span><span class="sxs-lookup"><span data-stu-id="7497f-259">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="7497f-260">AR의 손과 VR의 모션 컨트롤러 간에는 상호 작용 평행 이론이 작용한다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-260">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="7497f-261">두 입력은 모두 해당 환경에서 직접 조작을 트리거하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-261">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="7497f-262">HoloLens 2의 근거리에서 손으로 잡아 끄는 동작은 WMR 모션 컨트롤러에 있는 잡기 단추로 작동하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-262">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="7497f-263">이를 통해 사용자는 두 플랫폼 간에 상호 작용을 쉽게 수행할 수 있으므로 애플리케이션을 플랫폼 간에 이식하려는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-263">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="7497f-264">시선 추적으로 최적화</span><span class="sxs-lookup"><span data-stu-id="7497f-264">Optimize with eye tracking</span></span>

<span data-ttu-id="7497f-265">직접 조작은 의도한 대로 작동한다면 마법과 같이 느껴질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-265">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="7497f-266">하지만 손을 움직일 때마다 홀로그램이 의도와 다르게 트리거되면 당황할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-266">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="7497f-267">시선 추적은 사용자의 의도를 더 잘 식별하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-267">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="7497f-268">**사용할 때**: 조작 대응을 잘못 트리거하는 경우를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-268">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="7497f-269">시선 추적은 사용자가 현재 진행 중인 작업을 더 잘 이해할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-269">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="7497f-270">예를 들어 손을 뻗어 실제 작업 도구를 잡을 때 홀로그램(지침) 텍스트를 읽고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-270">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="7497f-271">이렇게 하면 이전에 알아채지 못했던 일부 대화형 홀로그램 단추 사이에서 손을 실수로 움직이게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-271">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="7497f-272">예를 들어 사용자의 FoV(시야) 밖에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-272">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="7497f-273">사용자가 잠시 동안 홀로그램을 보지 않았지만 터치 또는 잡기 이벤트가 감지되면 상호 작용이 의도하지 않은 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-273">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="7497f-274">**선택한 대상**:  또 다른 예로 가양성 활성화를 처리하는 것 외에, 여러 개의 홀로그램이 서로 가깝게 배치된 경우 특히, 사용자 관점에서 정확한 교차점을 알 수 없으므로 잡거나 찌를 홀로그램을 더 잘 식별하는 경우를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-274">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="7497f-275">HoloLens 2의 시선 추적은 시선 응시를 정확하게 결정할 수 있는 정도에 따라 제한이 있지만, 손 입력과 상호 작용할 때 깊이 차이로 인해 근거리 상호 작용에 여전히 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-275">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="7497f-276">따라서 예를 들어 조작 위젯을 정확히 잡기 위해 손을 홀로그램 뒤에 있는지 아니면 앞에 있는지를 결정하는 것이 어려운 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-276">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="7497f-277">**대상 위치**: 빨리 던지기 제스처에서 사용자가 바라보는 대상에 대한 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-277">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="7497f-278">홀로그램을 잡은 후 의도한 대상 쪽으로 대충 던집니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-278">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="7497f-279">경우에 따라 이 방법이 작동하지만, 손 제스처를 빠르게 수행하면 대상이 매우 부정확해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-279">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="7497f-280">하지만 시선 추적은 제스처의 정확도를 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-280">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="7497f-281">Unity용 MRTK(Mixed Reality Toolkit)의 조작</span><span class="sxs-lookup"><span data-stu-id="7497f-281">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="7497f-282">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 를 사용하면 **ObjectManipulator** 스크립트를 사용하여 일반적인 조작 동작을 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-282">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="7497f-283">ObjectManipulator를 사용하면 직접 손이나 손 광선으로 직접 개체를 잡아 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-283">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="7497f-284">또한 개체의 크기 조정 및 회전을 위해 양손 조작도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7497f-284">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="7497f-285">MRTK - 조작</span><span class="sxs-lookup"><span data-stu-id="7497f-285">MRTK - Manipulation</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator)

---

## <a name="see-also"></a><span data-ttu-id="7497f-286">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7497f-286">See also</span></span>

* [<span data-ttu-id="7497f-287">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="7497f-287">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="7497f-288">수동으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="7497f-288">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="7497f-289">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="7497f-289">Instinctual interactions</span></span>](interaction-fundamentals.md)