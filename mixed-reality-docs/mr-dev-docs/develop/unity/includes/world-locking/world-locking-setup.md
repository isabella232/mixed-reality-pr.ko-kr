---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528761"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="8fc7d-101">세계 잠금 도구 (권장)</span><span class="sxs-lookup"><span data-stu-id="8fc7d-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="8fc7d-102">새 혼합 현실 기능 도구를 사용 하 여 세계 잠금 도구를 설치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-102">We recommend installing World Locking Tools using the new Mixed Reality Feature Tool.</span></span> <span data-ttu-id="8fc7d-103">아래 링크에서 Mixed Reality 기능 도구를 다운로드 한 후에는 **세계 잠금 도구** 섹션에서 최신 버전의 **WLT Core** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-103">Once you've downloaded the Mixed Reality Feature Tool from the link below, select the latest version of **WLT Core** from the **World Locking Tools** section:</span></span>

![전역 잠금 도구를 선택 하 여 혼합 현실 기능 도구 기능 선택 창](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="8fc7d-105">MR 기능 도구를 사용 하 여 세계 잠금 도구 설치</span><span class="sxs-lookup"><span data-stu-id="8fc7d-105">Install World Locking Tools with the MR Feature Tool</span></span>](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a><span data-ttu-id="8fc7d-106">자동 설치</span><span class="sxs-lookup"><span data-stu-id="8fc7d-106">Automated setup</span></span>

<span data-ttu-id="8fc7d-107">프로젝트를 사용할 준비가 되 면 **혼합 현실 도구 키트 > 유틸리티 > 세계 잠금 도구** 에서 장면 구성 유틸리티를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-107">When your project is ready to go, run the configure scene utility from **Mixed Reality Toolkit > Utilities > World Locking Tools**:</span></span>

![혼합 현실 도구 키트 메뉴가 선택 된 Unity 편집기](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> <span data-ttu-id="8fc7d-109">장면 구성 유틸리티는 언제 든 지 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-109">The Configure scene utility can be rerun at any time.</span></span> <span data-ttu-id="8fc7d-110">예를 들어 AR 대상이 레거시에서 XR SDK로 변경 된 경우 다시 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-110">For example, it should be rerun if the AR target has been changed from Legacy to XR SDK.</span></span> <span data-ttu-id="8fc7d-111">장면이 이미 올바르게 구성 된 경우 유틸리티를 실행 해도 아무런 효과가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-111">If the scene is already properly configured, running the utility has no effect.</span></span>

### <a name="visualizers"></a><span data-ttu-id="8fc7d-112">시각화 도우미</span><span class="sxs-lookup"><span data-stu-id="8fc7d-112">Visualizers</span></span>

<span data-ttu-id="8fc7d-113">초기 개발 중에 시각화 도우미를 추가 하는 것이 WLT가 설치 되어 제대로 작동 하는지 확인 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-113">During early development, adding visualizers can be helpful to ensure WLT is setup and working properly.</span></span> <span data-ttu-id="8fc7d-114">프로덕션 성능에 대해 제거할 수 있으며, 어떤 이유로 든 더 이상 필요 하지 않은 경우에는 시각화 도우미 제거 유틸리티를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-114">They can be removed for production performance, or if for any reason are no longer needed, using the Remove visualizers utility.</span></span> <span data-ttu-id="8fc7d-115">시각화 도우미에 대 한 자세한 내용은 [도구 설명서](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-115">More details on the visualizers can be found in the [Tools documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="8fc7d-116">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="8fc7d-116">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="8fc7d-117">Mixed Reality OpenXR 플러그 인은 Unity의 ARFoundation **ARAnchorManager** 구현을 통해 기본적인 앵커 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-117">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="8fc7d-118">Aranchors의 ARAnchors에 대 한 기본 사항을 알아보려면 [AR 앵커 관리자에 대 한 Aranchors 설명서](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-118">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="worldanchor"></a>[<span data-ttu-id="8fc7d-119">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="8fc7d-119">WorldAnchor</span></span>](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="8fc7d-120">세계 최고 규모 환경 구축</span><span class="sxs-lookup"><span data-stu-id="8fc7d-120">Building a world-scale experience</span></span>

<span data-ttu-id="8fc7d-121">**네임 스페이스:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="8fc7d-121">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="8fc7d-122">**유형:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="8fc7d-122">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="8fc7d-123">사용자가 5 미터를 wander 수 있도록 하는 HoloLens의 진정한 **세계 규모 환경** 에서는 공간 규모 환경에 사용 되는 기술이 아닌 새로운 기술이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-123">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="8fc7d-124">사용할 수 있는 한 가지 핵심 기술은 holograms의 클러스터를 물리적 환경에서 정확 [하 게 배치 하 여](../../../../design/coordinate-systems.md#spatial-anchors) 사용자가 로밍 하는 거리에 관계 없이 [해당 holograms를 다시 찾는](../../../../design/coordinate-systems.md#spatial-anchor-persistence)것입니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-124">One key technique you'll use is to create a [spatial anchor](../../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="8fc7d-125">Unity에서는 GameObject에 **WorldAnchor** Unity 구성 요소를 추가 하 여 공간 앵커를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-125">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="8fc7d-126">세계 앵커 추가</span><span class="sxs-lookup"><span data-stu-id="8fc7d-126">Adding a World Anchor</span></span>

<span data-ttu-id="8fc7d-127">세계 앵커를 추가 하려면 `AddComponent<WorldAnchor>()` 실제 지역에서 고정 하려는 변환을 사용 하 여 game 개체에 대해를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-127">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="8fc7d-128">이것으로 끝입니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-128">That's it!</span></span> <span data-ttu-id="8fc7d-129">이 게임 개체는 이제 실제 세계의 현재 위치에 고정 되어 있습니다 .이를 통해 Unity 세계 좌표가 약간 조정 되어 물리적 맞춤을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-129">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="8fc7d-130">이후 앱 세션에서이 앵커 된 위치를 다시 찾으려면 [세계 앵커 로드](#loading-a-worldanchor) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-130">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="8fc7d-131">세계 앵커 제거</span><span class="sxs-lookup"><span data-stu-id="8fc7d-131">Removing a World Anchor</span></span>

<span data-ttu-id="8fc7d-132">GameObject를 실제 세계 위치로 잠글 필요가 없으며이 프레임으로 이동 하지 않으려면 세계 앵커 구성 요소에 대해 소멸을 호출 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-132">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="8fc7d-133">GameObject이 프레임을 이동 하려면 DestroyImmediate를 대신 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-133">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="8fc7d-134">세계 고정 GameObject 이동</span><span class="sxs-lookup"><span data-stu-id="8fc7d-134">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="8fc7d-135">GameObject은 세계 앵커가 있는 동안 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-135">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="8fc7d-136">GameObject이 프레임을 이동 해야 하는 경우 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-136">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="8fc7d-137">세계 앵커 구성 요소 DestroyImmediate</span><span class="sxs-lookup"><span data-stu-id="8fc7d-137">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="8fc7d-138">GameObject 이동</span><span class="sxs-lookup"><span data-stu-id="8fc7d-138">Move the GameObject</span></span>
3. <span data-ttu-id="8fc7d-139">GameObject에 새 세계 앵커 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-139">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="8fc7d-140">Locatability 변경 내용 처리</span><span class="sxs-lookup"><span data-stu-id="8fc7d-140">Handling Locatability Changes</span></span>

<span data-ttu-id="8fc7d-141">WorldAnchor는 특정 시점에 물리적 세계에 과정이 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-141">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="8fc7d-142">이 경우 Unity는 고정 된 개체의 변환을 업데이트 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-142">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="8fc7d-143">이는 앱이 실행 되는 동안에도 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-143">This also can change while an app is running.</span></span> <span data-ttu-id="8fc7d-144">Locatability의 변경을 처리 하지 못하면 개체가 전 세계의 올바른 물리적 위치에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-144">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="8fc7d-145">Locatability 변경 내용에 대 한 알림이 표시 되는 경우:</span><span class="sxs-lookup"><span data-stu-id="8fc7d-145">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="8fc7d-146">OnTrackingChanged 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="8fc7d-146">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="8fc7d-147">이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-147">Handle the event</span></span>

<span data-ttu-id="8fc7d-148">**Ontrackingchanged** 이벤트는 기본 공간 앵커가 과정이의 상태와 과정이 되지 않는 사이에 변경 될 때마다 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-148">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="8fc7d-149">그런 다음 이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-149">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="8fc7d-150">경우에 따라 앵커가 즉시 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-150">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="8fc7d-151">이 경우 AddComponent ()가 반환 되 면 앵커의이 isLocated 속성은 true로 설정 됩니다 <WorldAnchor> .</span><span class="sxs-lookup"><span data-stu-id="8fc7d-151">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="8fc7d-152">따라서 OnTrackingChanged 이벤트가 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-152">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="8fc7d-153">깨끗 한 패턴은 앵커를 연결한 후 초기 IsLocated 상태를 사용 하 여 OnTrackingChanged 처리기를 호출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8fc7d-153">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```