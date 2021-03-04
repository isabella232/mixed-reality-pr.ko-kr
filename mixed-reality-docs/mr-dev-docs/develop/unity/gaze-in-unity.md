---
title: Unity의 응시
description: 사용자가 혼합 현실에서 만든 holograms를 대상으로 하는 기본 방법으로 응시 입력을 사용 하는 방법에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 눈에 응시, 헤드-응시, unity, 홀로그램, 혼합 현실, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 7602eb27da19dc77e4eab1c1a428dc9a1cf8b252
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759689"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="8dc84-104">헤드-Unity에서의 응시</span><span class="sxs-lookup"><span data-stu-id="8dc84-104">Head-gaze in Unity</span></span>

<span data-ttu-id="8dc84-105">[Holograms](../../discover/hologram.md) 는 사용자가 [혼합 현실](../../discover/mixed-reality.md)에서 만든 앱을 대상으로 [하는 기본](../../design/gaze-and-commit.md) 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="8dc84-106">헤드-응시 구현</span><span class="sxs-lookup"><span data-stu-id="8dc84-106">Implementing head-gaze</span></span>

<span data-ttu-id="8dc84-107">개념적으로 사용자의 헤드셋에서 광선을 전달 하 여 [헤드](../../design/gaze-and-commit.md) 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="8dc84-108">Unity에서 사용자의 헤드 위치와 방향은 [카메라](camera-in-unity.md) [(구체적으로](https://docs.unity3d.com/ScriptReference/Camera-main.html)는 안 됨)를 통해 노출 됩니다. [transform. forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) 및 [Unityengine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transform. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="8dc84-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="8dc84-109">GameObject [를 호출 하면](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 3d 충돌 지점을 비롯 한 충돌에 대 한 정보를 포함 하는 [Raycasthit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) 및 헤드-응시 빛의 기타 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="8dc84-110">예: 헤드-응시 구현</span><span class="sxs-lookup"><span data-stu-id="8dc84-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="8dc84-111">모범 사례</span><span class="sxs-lookup"><span data-stu-id="8dc84-111">Best practices</span></span>

<span data-ttu-id="8dc84-112">위의 예제에서는 업데이트 루프에서 단일 raycast를 실행 하 여 사용자의 헤드가 가리키는 대상을 찾는 반면 단일 개체를 사용 하 여 모든 헤드-응시 프로세스를 관리 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="8dc84-113">헤드-응시 논리를 결합 하 여 앱의 귀중 한 처리 능력을 절약 하 고, raycasting를 프레임당 하나로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="8dc84-114">헤드 시각화-응시</span><span class="sxs-lookup"><span data-stu-id="8dc84-114">Visualizing head-gaze</span></span>

<span data-ttu-id="8dc84-115">컴퓨터에서 마우스 포인터를 사용 하는 것과 마찬가지로 사용자의 헤드를 나타내는 [커서](../../design/cursors.md) 를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="8dc84-116">사용자가 대상으로 하는 콘텐츠를 알면 상호 작용할 대상이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="8dc84-117">Head-Mixed Reality Toolkit의 Head-응시</span><span class="sxs-lookup"><span data-stu-id="8dc84-117">Head-gaze in the Mixed Reality Toolkit</span></span> 
<span data-ttu-id="8dc84-118">MRTK의 [입력 관리자](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md) 에서 헤드-응시에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-118">You can access head-gaze from the [Input Manager](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="8dc84-119">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="8dc84-119">Next Development Checkpoint</span></span>

<span data-ttu-id="8dc84-120">앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="8dc84-121">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8dc84-122">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="8dc84-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="8dc84-123">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8dc84-124">공유 환경</span><span class="sxs-lookup"><span data-stu-id="8dc84-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="8dc84-125">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8dc84-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8dc84-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8dc84-126">See also</span></span>
* [<span data-ttu-id="8dc84-127">카메라</span><span class="sxs-lookup"><span data-stu-id="8dc84-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="8dc84-128">커서</span><span class="sxs-lookup"><span data-stu-id="8dc84-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="8dc84-129">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="8dc84-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
