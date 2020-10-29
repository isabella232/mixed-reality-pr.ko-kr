---
title: Unity의 지속성
description: 지 속성을 사용 하면 사용자가 원하는 위치에 개별 holograms 또는 작업 영역을 고정 한 다음, 앱의 많은 사용을 원하는 경우 나중에 찾을 수 있습니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 지 속성, Unity
ms.openlocfilehash: bb1a9b0544f9325a60c86c7424b7b451b6b4335b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91690080"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="b432b-104">Unity의 지속성</span><span class="sxs-lookup"><span data-stu-id="b432b-104">Persistence in Unity</span></span>

<span data-ttu-id="b432b-105">**네임 스페이스:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="b432b-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="b432b-106">**클래스:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="b432b-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="b432b-107">WorldAnchorStore는 응용 프로그램의 여러 인스턴스에서 holograms 특정 실제 위치에 유지 되는 holographic 환경을 만드는 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="b432b-108">이렇게 하면 사용자가 원하는 위치에 개별 holograms 또는 작업 영역을 고정 한 다음, 앱의 여러 사용을 원하는 위치에서 나중에 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="b432b-109">세션 간에 holograms를 유지 하는 방법</span><span class="sxs-lookup"><span data-stu-id="b432b-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="b432b-110">WorldAnchorStore를 사용 하면 세션 간에 WorldAnchor의 위치를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="b432b-111">실제로 세션 간에 holograms을 유지 하려면 특정 세계 앵커를 사용 하는 Gameobject를 별도로 추적 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="b432b-112">일반적으로 세계 앵커를 사용 하 여 GameObject 루트를 만들고 로컬 위치 오프셋을 사용 하 여 자식을 holograms 고정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="b432b-113">이전 세션에서 holograms를 로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="b432b-114">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="b432b-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="b432b-115">세계 앵커와 관련 된 앱 데이터를 로드 하 여 세계 앵커의 id를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="b432b-116">해당 id에서 전 세계 앵커 로드</span><span class="sxs-lookup"><span data-stu-id="b432b-116">Load a world anchor from its id</span></span>

<span data-ttu-id="b432b-117">이후 세션에 대해 holograms를 저장 하려면:</span><span class="sxs-lookup"><span data-stu-id="b432b-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="b432b-118">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="b432b-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="b432b-119">Id를 지정 하 여 전 세계 앵커 저장</span><span class="sxs-lookup"><span data-stu-id="b432b-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="b432b-120">Id와 함께 세계 앵커와 관련 된 앱 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="b432b-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="b432b-121">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="b432b-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="b432b-122">WorldAnchorStore에 대 한 참조를 유지 하 여 작업을 수행 하려는 경우 준비가 되었다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="b432b-123">비동기 호출 이므로 시작 하는 즉시,를 호출 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="b432b-124">이 경우 WorldAnchorStore가 로드를 완료 한 경우에 대 한 처리기입니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="b432b-125">이제 특정 세계 앵커를 저장 하 고 로드 하는 데 사용할 WorldAnchorStore에 대 한 참조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="b432b-126">WorldAnchor 저장</span><span class="sxs-lookup"><span data-stu-id="b432b-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="b432b-127">저장 하기 위해 저장 하는 항목의 이름을로 하 고 저장 하려는 경우 앞에서 받은 WorldAnchor에 전달 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="b432b-128">참고: 두 앵커를 같은 문자열에 저장 하려고 하면 실패 합니다 (store. Save는 false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="b432b-129">이전 저장을 삭제 한 후 새 저장을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-129">You need to Delete the previous save before saving the new one:</span></span>

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="b432b-130">WorldAnchor 로드</span><span class="sxs-lookup"><span data-stu-id="b432b-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="b432b-131">로드 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="b432b-132">저장소를 추가로 사용할 수도 있습니다. Delete ()-이전에 저장 하 고 저장 한 앵커를 제거 합니다. 이전에 저장 된 모든 데이터를 제거 하려면 ()를 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="b432b-133">기존 앵커 열거</span><span class="sxs-lookup"><span data-stu-id="b432b-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="b432b-134">이전에 저장 된 앵커를 검색 하려면 GetAllIds를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="b432b-135">여러 장치에 대 한 holograms 유지</span><span class="sxs-lookup"><span data-stu-id="b432b-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="b432b-136"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 로컬 WorldAnchor에서 영 속 클라우드 앵커를 만들 수 있습니다. 그러면 앱이 여러 HoloLens, IOS 및 Android 장치에서 해당 장치를 동시에 함께 제공 하지 않는 경우에도 해당 장치를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="b432b-137">클라우드 앵커는 지속 되기 때문에 시간에 따른 여러 장치는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="b432b-138">Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="b432b-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="b432b-139">Azure 공간 앵커를 사용 하 여 실행 하면 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b432b-140">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="b432b-140">Next Development Checkpoint</span></span>

<span data-ttu-id="b432b-141">앞서 설명한 Unity 개발 검사점 경험을 팔로 사용할 경우 혼합 현실 핵심 빌딩 블록을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-141">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="b432b-142">여기에서 다음 구성 요소를 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-142">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b432b-143">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="b432b-143">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="b432b-144">또는 혼합 현실 플랫폼 기능 및 Api로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-144">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b432b-145">공유 환경</span><span class="sxs-lookup"><span data-stu-id="b432b-145">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="b432b-146">언제 든 지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks) 으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b432b-146">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b432b-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b432b-147">See Also</span></span>
* [<span data-ttu-id="b432b-148">공간 앵커 지 속성</span><span class="sxs-lookup"><span data-stu-id="b432b-148">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="b432b-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="b432b-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="b432b-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a></span><span class="sxs-lookup"><span data-stu-id="b432b-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
