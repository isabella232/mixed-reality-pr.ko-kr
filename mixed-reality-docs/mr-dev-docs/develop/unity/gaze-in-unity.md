---
title: Unity의 응시
description: 사용자가 혼합 현실에서 앱이 만드는 홀로그램을 대상으로 지정하는 기본 방법으로 응시 입력을 사용하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 시선 응시, 헤드 게이즈, unity, 홀로그램, 혼합 현실, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f10079d36f737e5d8a2ee74a88ca0f8b2b3d791c
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600152"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="16d22-104">Unity의 헤드 응시</span><span class="sxs-lookup"><span data-stu-id="16d22-104">Head-gaze in Unity</span></span>

<span data-ttu-id="16d22-105">[응시는](../../design/gaze-and-commit.md) 사용자가 앱이 [Mixed Reality](../../discover/mixed-reality.md)만드는 [홀로그램을](../../discover/hologram.md) 대상으로 지정하는 기본 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="16d22-106">헤드 응시 구현</span><span class="sxs-lookup"><span data-stu-id="16d22-106">Implementing head-gaze</span></span>

<span data-ttu-id="16d22-107">개념적으로 사용자의 헤드셋에서 광선을 앞으로 프로젝팅하여 [헤드 게이즈(head-gaze)를](../../design/gaze-and-commit.md) 결정하여 적중되는 것을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="16d22-108">Unity에서 사용자의 머리 위치와 방향은 [카메라,](camera-in-unity.md)특히 [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html)을 통해 노출됩니다. [transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) 및 [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="16d22-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="16d22-109">[Physics.RayCast를](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 호출하면 3D 충돌 지점 및 헤드 응시 광선 적중을 포함한 다른 GameObject를 포함하여 충돌에 대한 정보가 포함된 [RaycastHit가](https://docs.unity3d.com/ScriptReference/RaycastHit.html) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="16d22-110">예제: 헤드 응시 구현</span><span class="sxs-lookup"><span data-stu-id="16d22-110">Example: Implement head-gaze</span></span>

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a><span data-ttu-id="16d22-111">모범 사례</span><span class="sxs-lookup"><span data-stu-id="16d22-111">Best practices</span></span>

<span data-ttu-id="16d22-112">위의 예제에서는 업데이트 루프에서 단일 광선 캐스팅을 발생하여 사용자의 헤드포인트가 있는 대상을 찾는 동안 단일 개체를 사용하여 모든 헤드 응시 프로세스를 관리하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="16d22-113">헤드 게이즈 논리를 결합하면 앱의 처리 능력이 절약되고 광선 캐스팅이 프레임당 하나로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="16d22-114">머리 응시 시각화</span><span class="sxs-lookup"><span data-stu-id="16d22-114">Visualizing head-gaze</span></span>

<span data-ttu-id="16d22-115">컴퓨터의 마우스 포인터와 마찬가지로 사용자의 머리 응시를 나타내는 [커서를](../../design/cursors.md) 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="16d22-116">사용자가 대상으로 하는 콘텐츠를 알면 상호 작용하려는 내용에 대한 신뢰도가 높아질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="16d22-117">Mixed Reality 도구 키트의 머리 응시</span><span class="sxs-lookup"><span data-stu-id="16d22-117">Head-gaze in the Mixed Reality Toolkit</span></span>

<span data-ttu-id="16d22-118">MRTK의 [입력 관리자에서](/windows/mixed-reality/mrtk-unity/features/input/overview) 헤드 응시에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-118">You can access head-gaze from the [Input Manager](/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="16d22-119">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="16d22-119">Next Development Checkpoint</span></span>

<span data-ttu-id="16d22-120">앞에서 설명한 Unity 개발 여정을 수행하는 경우 MRTK 핵심 구성 요소 탐색을 진행하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="16d22-121">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="16d22-122">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="16d22-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="16d22-123">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="16d22-124">공유 환경</span><span class="sxs-lookup"><span data-stu-id="16d22-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="16d22-125">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16d22-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="16d22-126">참조</span><span class="sxs-lookup"><span data-stu-id="16d22-126">See also</span></span>
* [<span data-ttu-id="16d22-127">카메라</span><span class="sxs-lookup"><span data-stu-id="16d22-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="16d22-128">커서</span><span class="sxs-lookup"><span data-stu-id="16d22-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="16d22-129">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="16d22-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)