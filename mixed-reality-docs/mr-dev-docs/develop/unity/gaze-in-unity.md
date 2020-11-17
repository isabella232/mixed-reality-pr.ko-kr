---
title: Unity의 응시
description: 응시는 사용자가 혼합 현실에서 앱이 만드는 holograms를 대상으로 하는 기본 방법입니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 눈에 응시, 헤드-응시, unity, 홀로그램, 혼합 현실, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0c62de9cb1b7ea892831ea2cedbeb23be5ea7b37
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677512"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="59064-104">헤드-Unity에서의 응시</span><span class="sxs-lookup"><span data-stu-id="59064-104">Head-gaze in Unity</span></span>

<span data-ttu-id="59064-105">[응시](../../design/gaze-and-commit.md) 는 사용자가 [혼합 현실](../../discover/mixed-reality.md)에서 앱이 만드는 [holograms](../../discover/hologram.md) 를 대상으로 하는 기본 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="59064-105">[Gaze](../../design/gaze-and-commit.md) is a primary way for users to target the [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="59064-106">헤드-응시 구현</span><span class="sxs-lookup"><span data-stu-id="59064-106">Implementing head-gaze</span></span>

<span data-ttu-id="59064-107">개념적으로 [head-응시](../../design/gaze-and-commit.md) 는 헤드셋이 있는 사용자 헤드의 광선을 전달 하 고, 정방향 방향으로, 광선이 충돌 하는 항목을 확인 하 여 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="59064-107">Conceptually, [head-gaze](../../design/gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span>
<span data-ttu-id="59064-108">Unity에서 사용자의 헤드 위치와 방향은 Unity 기본 [카메라](camera-in-unity.md) [(구체적으로](https://docs.unity3d.com/ScriptReference/Camera-main.html)는 없음)를 통해 노출 됩니다. [transform. forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) 및 [Unityengine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transform. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="59064-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="59064-109">[물리학](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 를 호출 하면 충돌이 발생 한 3d 지점과 다른 GameObject (헤드-응시 광선 충돌)를 포함 한 충돌에 대 한 정보가 포함 된 [Raycasthit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) 구조가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59064-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="59064-110">예: 헤드-응시 구현</span><span class="sxs-lookup"><span data-stu-id="59064-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="59064-111">모범 사례</span><span class="sxs-lookup"><span data-stu-id="59064-111">Best practices</span></span>

<span data-ttu-id="59064-112">위의 예제에서는 업데이트 루프에서 단일 raycast를 수행 하 여 사용자의 헤드가 가리키는 대상을 찾는 방법을 보여 주지만, gazed 되는 개체에 잠재적으로 관심이 있는 개체에서이 작업을 수행 하는 대신 헤드-응시를 관리 하는 단일 개체에서이 작업을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="59064-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="59064-113">이를 통해 앱은 각 프레임을 하나의 헤드 (각 프레임)만 수행 하 여 처리를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59064-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="59064-114">헤드 시각화-응시</span><span class="sxs-lookup"><span data-stu-id="59064-114">Visualizing head-gaze</span></span>

<span data-ttu-id="59064-115">마우스 포인터를 사용 하 여 콘텐츠를 대상으로 지정 하 고 상호 작용 하는 데스크톱과 마찬가지로 사용자의 헤드를 나타내는 [커서](../../design/cursors.md) 를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59064-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="59064-116">이렇게 하면 사용자가 상호 작용 하는 것에 대 한 확신을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59064-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="59064-117">Mixed Reality Toolkit v 2의 Head-응시</span><span class="sxs-lookup"><span data-stu-id="59064-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="59064-118">MRTK v 2의 [입력 관리자](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) 에서 헤드-응시에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59064-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="59064-119">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="59064-119">Next Development Checkpoint</span></span>

<span data-ttu-id="59064-120">앞에서 설명한 Unity 개발 검사점 경험을 수행하는 경우 MRTK 핵심 구성 요소를 탐색하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="59064-120">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="59064-121">여기에서 다음 구성 요소로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59064-121">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="59064-122">제스처 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="59064-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="59064-123">또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="59064-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="59064-124">공유 환경</span><span class="sxs-lookup"><span data-stu-id="59064-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="59064-125">언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59064-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="59064-126">참조</span><span class="sxs-lookup"><span data-stu-id="59064-126">See also</span></span>
* [<span data-ttu-id="59064-127">카메라</span><span class="sxs-lookup"><span data-stu-id="59064-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="59064-128">커서</span><span class="sxs-lookup"><span data-stu-id="59064-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="59064-129">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="59064-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
