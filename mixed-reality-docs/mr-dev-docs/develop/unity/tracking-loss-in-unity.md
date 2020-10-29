---
title: Unity의 손실 추적
description: Unity 앱 내에서 추적 손실 처리.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 손실 추적, 손실 이미지 추적
ms.openlocfilehash: 5aa17def844735088bcee6137a7b76a586107e44
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683118"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="a8da7-104">Unity의 손실 추적</span><span class="sxs-lookup"><span data-stu-id="a8da7-104">Tracking loss in Unity</span></span>

<span data-ttu-id="a8da7-105">장치를 세계에서 찾을 수 없는 경우 앱이 "추적 손실"를 경험 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="a8da7-106">기본적으로 Unity는 업데이트 루프를 일시 중지 하 고 사용자에 게 시작 이미지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="a8da7-107">추적이 회복 되 면 시작 이미지가 사라지고 업데이트 루프가 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="a8da7-108">대신 사용자가 설정에서 옵트아웃 하 여이 전환을 수동으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="a8da7-109">모든 콘텐츠를 처리 하기 위해 아무것도 수행 하지 않은 경우 추적 손실을 추적 하는 동안 모든 콘텐츠가 본문으로 잠긴 것으로 보입니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="a8da7-110">기본 처리</span><span class="sxs-lookup"><span data-stu-id="a8da7-110">Default Handling</span></span>

<span data-ttu-id="a8da7-111">기본적으로 앱의 업데이트 루프와 모든 메시지 및 이벤트는 손실 추적 기간 동안 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="a8da7-112">이때 이미지가 사용자에 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="a8da7-113">편집 >설정->플레이어로 이동 하 고 시작 이미지를 클릭 한 다음 Holographic 추적 손실 이미지를 설정 하 여이 이미지를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="a8da7-114">수동 처리</span><span class="sxs-lookup"><span data-stu-id="a8da7-114">Manual Handling</span></span>

<span data-ttu-id="a8da7-115">추적 손실을 수동으로 처리 하려면 **편집**  >  **프로젝트 설정**  >  **플레이어**  >  **유니버설 Windows 플랫폼 설정 탭**  >  **시작 이미지**  >  **Windows Holographic** 로 이동 하 고 "손실 일시 중지 및 이미지 표시"를 선택 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="a8da7-116">그런 다음 아래 지정 된 Api를 사용 하 여 변경 내용 추적을 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="a8da7-117">**네임 스페이스:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="a8da7-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="a8da7-118">**유형:** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="a8da7-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="a8da7-119">세계 관리자는 WorldManager 된 추적 ( *OnPositionalLocatorStateChanged* ) 및 현재 상태 ( *WorldManager* )를 쿼리 하는 속성을 검색 하는 이벤트를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-119">World Manager exposes an event to detect tracking lost/gained ( *WorldManager.OnPositionalLocatorStateChanged* ) and a property to query the current state ( *WorldManager.state* )</span></span>
* <span data-ttu-id="a8da7-120">추적 상태가 활성이 아닌 경우 사용자가 변환 하는 동안에도 카메라가 가상 환경에서 변환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="a8da7-121">즉, 개체는 더 이상 실제 위치에 해당 하지 않으며 모두 본문이 잠깁니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="a8da7-122">변경 내용 추적을 처리 하는 경우 각 프레임의 state 속성에 대해 폴링하거나 *OnPositionalLocatorStateChanged* 이벤트를 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="a8da7-123">폴링</span><span class="sxs-lookup"><span data-stu-id="a8da7-123">Polling</span></span>

<span data-ttu-id="a8da7-124">가장 중요 한 상태는 *Positionalloc를* 사용 하는 상태입니다. 활성은 추적이 완전히 작동 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="a8da7-125">다른 모든 상태는 주 카메라에만 회전 델타를 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="a8da7-126">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="a8da7-127">OnPositionalLocatorStateChanged 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="a8da7-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="a8da7-128">또는 더 편리 하 게 *OnPositionalLocatorStateChanged* 를 구독 하 여 전환을 처리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8da7-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="a8da7-129">참조</span><span class="sxs-lookup"><span data-stu-id="a8da7-129">See also</span></span>
* [<span data-ttu-id="a8da7-130">DirectX에서 추적 손실 처리</span><span class="sxs-lookup"><span data-stu-id="a8da7-130">Handling tracking loss in DirectX</span></span>](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
