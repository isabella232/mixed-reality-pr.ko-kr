---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719701"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="e8b50-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="e8b50-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="e8b50-102">Mixed Reality OpenXR 플러그 인은 Unity의 ARFoundation **ARAnchorManager** 구현을 통해 기본적인 앵커 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-102">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="e8b50-103">Aranchors의 ARAnchors에 대 한 기본 사항을 알아보려면 [AR 앵커 관리자에 대 한 Aranchors 설명서](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8b50-103">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="e8b50-104">Unity 2019/2020 + Windows XR 플러그 인</span><span class="sxs-lookup"><span data-stu-id="e8b50-104">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="e8b50-105">Mixed Reality OpenXR 플러그 인은 Unity의 ARFoundation **ARAnchorManager** 구현을 통해 기본적인 앵커 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-105">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="e8b50-106">Aranchors의 ARAnchors에 대 한 기본 사항을 알아보려면 [AR 앵커 관리자에 대 한 Aranchors 설명서](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8b50-106">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="e8b50-107">레거시 WSA</span><span class="sxs-lookup"><span data-stu-id="e8b50-107">Legacy WSA</span></span>](#tab/wsa)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="e8b50-108">세계 최고 규모 환경 구축</span><span class="sxs-lookup"><span data-stu-id="e8b50-108">Building a world-scale experience</span></span>

<span data-ttu-id="e8b50-109">**네임 스페이스:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="e8b50-109">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="e8b50-110">**유형:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="e8b50-110">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="e8b50-111">사용자가 5 미터를 wander 수 있도록 하는 HoloLens의 진정한 **세계 규모 환경** 에서는 공간 규모 환경에 사용 되는 기술이 아닌 새로운 기술이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-111">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="e8b50-112">사용할 수 있는 한 가지 핵심 기술은 holograms의 클러스터를 물리적 환경에서 정확 [하 게 배치 하 여](../../../design/coordinate-systems.md#spatial-anchors) 사용자가 로밍 하는 거리에 관계 없이 [해당 holograms를 다시 찾는](../../../design/coordinate-systems.md#spatial-anchor-persistence)것입니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-112">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="e8b50-113">Unity에서는 GameObject에 **WorldAnchor** Unity 구성 요소를 추가 하 여 공간 앵커를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-113">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="e8b50-114">세계 앵커 추가</span><span class="sxs-lookup"><span data-stu-id="e8b50-114">Adding a World Anchor</span></span>

<span data-ttu-id="e8b50-115">세계 앵커를 추가 하려면 `AddComponent<WorldAnchor>()` 실제 지역에서 고정 하려는 변환을 사용 하 여 game 개체에 대해를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-115">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="e8b50-116">이것으로 끝입니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-116">That's it!</span></span> <span data-ttu-id="e8b50-117">이 게임 개체는 이제 실제 세계의 현재 위치에 고정 되어 있습니다 .이를 통해 Unity 세계 좌표가 약간 조정 되어 물리적 맞춤을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-117">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="e8b50-118">이후 앱 세션에서이 앵커 된 위치를 다시 찾으려면 [세계 앵커 로드](#loading-a-worldanchor) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e8b50-118">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="e8b50-119">세계 앵커 제거</span><span class="sxs-lookup"><span data-stu-id="e8b50-119">Removing a World Anchor</span></span>

<span data-ttu-id="e8b50-120">GameObject를 실제 세계 위치로 잠글 필요가 없으며이 프레임으로 이동 하지 않으려면 세계 앵커 구성 요소에 대해 소멸을 호출 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-120">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="e8b50-121">GameObject이 프레임을 이동 하려면 DestroyImmediate를 대신 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-121">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="e8b50-122">세계 고정 GameObject 이동</span><span class="sxs-lookup"><span data-stu-id="e8b50-122">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="e8b50-123">GameObject은 세계 앵커가 있는 동안 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-123">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="e8b50-124">GameObject이 프레임을 이동 해야 하는 경우 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-124">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="e8b50-125">세계 앵커 구성 요소 DestroyImmediate</span><span class="sxs-lookup"><span data-stu-id="e8b50-125">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="e8b50-126">GameObject 이동</span><span class="sxs-lookup"><span data-stu-id="e8b50-126">Move the GameObject</span></span>
3. <span data-ttu-id="e8b50-127">GameObject에 새 세계 앵커 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-127">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="e8b50-128">Locatability 변경 내용 처리</span><span class="sxs-lookup"><span data-stu-id="e8b50-128">Handling Locatability Changes</span></span>

<span data-ttu-id="e8b50-129">WorldAnchor는 특정 시점에 물리적 세계에 과정이 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-129">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="e8b50-130">이 경우 Unity는 고정 된 개체의 변환을 업데이트 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-130">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="e8b50-131">이는 앱이 실행 되는 동안에도 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-131">This also can change while an app is running.</span></span> <span data-ttu-id="e8b50-132">Locatability의 변경을 처리 하지 못하면 개체가 전 세계의 올바른 물리적 위치에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-132">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="e8b50-133">Locatability 변경 내용에 대 한 알림이 표시 되는 경우:</span><span class="sxs-lookup"><span data-stu-id="e8b50-133">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="e8b50-134">OnTrackingChanged 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="e8b50-134">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="e8b50-135">이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-135">Handle the event</span></span>

<span data-ttu-id="e8b50-136">**Ontrackingchanged** 이벤트는 기본 공간 앵커가 과정이의 상태와 과정이 되지 않는 사이에 변경 될 때마다 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-136">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="e8b50-137">그런 다음 이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-137">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="e8b50-138">경우에 따라 앵커가 즉시 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-138">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="e8b50-139">이 경우 AddComponent ()가 반환 되 면 앵커의이 isLocated 속성은 true로 설정 됩니다 <WorldAnchor> .</span><span class="sxs-lookup"><span data-stu-id="e8b50-139">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="e8b50-140">따라서 OnTrackingChanged 이벤트가 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-140">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="e8b50-141">깨끗 한 패턴은 앵커를 연결한 후 초기 IsLocated 상태를 사용 하 여 OnTrackingChanged 처리기를 호출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e8b50-141">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```