---
title: 직접 물리학 서비스
description: MRTK에서 직접 물리학 확장 서비스를 사용 하는 설명서
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: af7ea753d52b5e478c54ca19d6d8e391401eea6d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176252"
---
# <a name="hand-physics-service"></a><span data-ttu-id="bc9d9-104">직접 물리학 서비스</span><span class="sxs-lookup"><span data-stu-id="bc9d9-104">Hand physics service</span></span>

![직접 물리학 확장 서비스](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="bc9d9-106">이에 대 한 실제 서비스를 사용 하면 엄격한 본문 충돌 이벤트와 상호 작용을 통해 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="bc9d9-107">확장 사용</span><span class="sxs-lookup"><span data-stu-id="bc9d9-107">Enabling the extension</span></span>

<span data-ttu-id="bc9d9-108">확장을 사용 하도록 설정 하려면 RegisteredServiceProvider 프로필을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="bc9d9-109">`Register a new Service Provider`새 구성을 추가 하려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="bc9d9-110">구성 요소 유형 필드에서 HandPhysicsService를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="bc9d9-111">구성 프로필 필드에서 확장에 포함 된 기본 직접 물리학 프로필을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="bc9d9-112">프로필 옵션</span><span class="sxs-lookup"><span data-stu-id="bc9d9-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="bc9d9-113">직접 물리학 계층</span><span class="sxs-lookup"><span data-stu-id="bc9d9-113">Hand physics layer</span></span>

<span data-ttu-id="bc9d9-114">인스턴스화된 손을 조인트가 이동할 계층을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="bc9d9-115">서비스는 기본적으로 "default" 계층 (0)으로 설정 되지만, 직접 물리 개체에 대해 별도의 계층을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="bc9d9-116">그렇지 않으면 원치 않는 충돌 및/또는 부정확 한 raycasts를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="bc9d9-117">핑거 팁 기구학 본문 prefab</span><span class="sxs-lookup"><span data-stu-id="bc9d9-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="bc9d9-118">어떤 prefab를 손쉽게 인스턴스화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="bc9d9-119">서비스가 예상 대로 작동 하려면 prefab에 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="bc9d9-120">IsKinematic이 활성화 된 rigidbody 구성 요소</span><span class="sxs-lookup"><span data-stu-id="bc9d9-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="bc9d9-121">Collider</span><span class="sxs-lookup"><span data-stu-id="bc9d9-121">A collider</span></span>
- <span data-ttu-id="bc9d9-122">`JointKinematicBody` 구성 요소</span><span class="sxs-lookup"><span data-stu-id="bc9d9-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="bc9d9-123">팜 기구학 본문 사용</span><span class="sxs-lookup"><span data-stu-id="bc9d9-123">Use palm kinematic body</span></span>

<span data-ttu-id="bc9d9-124">서비스에서 팜 prefab의 인스턴스화를 시도할지 여부를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="bc9d9-125">야자수 기구학 본문 prefab</span><span class="sxs-lookup"><span data-stu-id="bc9d9-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="bc9d9-126">`UsePalmKinematicBody`을 사용 하도록 설정 하면이 prefab 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="bc9d9-127">마찬가지로 `FingerTipKinematicBodyPrefab` 이 prefab에는 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="bc9d9-128">IsKinematic이 활성화 된 rigidbody 구성 요소</span><span class="sxs-lookup"><span data-stu-id="bc9d9-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="bc9d9-129">Collider</span><span class="sxs-lookup"><span data-stu-id="bc9d9-129">A collider</span></span>
- <span data-ttu-id="bc9d9-130">`JointKinematicBody` 구성 요소</span><span class="sxs-lookup"><span data-stu-id="bc9d9-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="bc9d9-131">서비스를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="bc9d9-131">How to use the service</span></span>

<span data-ttu-id="bc9d9-132">사용 하도록 설정 되 면 모든 collider의 속성을 사용 `IsTrigger` 하 여 10 자리 (그리고 사용 하도록 설정 된 경우 palms)에서 충돌 이벤트를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc9d9-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
