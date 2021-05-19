---
title: 직접 물리학 서비스 개요
description: MRTK에서 직접 물리학 확장 서비스를 사용 하는 설명서
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 751aec148d3a40da4728d2fdd60a60402b59a4de
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145086"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="77024-104">직접 물리학 확장 서비스</span><span class="sxs-lookup"><span data-stu-id="77024-104">Hand physics extension service</span></span>

![직접 물리학 확장 서비스](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="77024-106">이에 대 한 실제 서비스를 사용 하면 엄격한 본문 충돌 이벤트와 상호 작용을 통해 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77024-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="77024-107">확장 사용</span><span class="sxs-lookup"><span data-stu-id="77024-107">Enabling the extension</span></span>

<span data-ttu-id="77024-108">확장을 사용 하도록 설정 하려면 RegisteredServiceProvider 프로필을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="77024-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="77024-109">`Register a new Service Provider`새 구성을 추가 하려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77024-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="77024-110">구성 요소 유형 필드에서 HandPhysicsService를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="77024-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="77024-111">구성 프로필 필드에서 확장에 포함 된 기본 직접 물리학 프로필을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="77024-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="77024-112">프로필 옵션</span><span class="sxs-lookup"><span data-stu-id="77024-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="77024-113">직접 물리학 계층</span><span class="sxs-lookup"><span data-stu-id="77024-113">Hand physics layer</span></span>

<span data-ttu-id="77024-114">인스턴스화된 손을 조인트가 이동할 계층을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="77024-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="77024-115">서비스는 기본적으로 "default" 계층 (0)으로 설정 되지만, 직접 물리 개체에 대해 별도의 계층을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="77024-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="77024-116">그렇지 않으면 원치 않는 충돌 및/또는 부정확 한 raycasts를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77024-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="77024-117">핑거 팁 기구학 본문 prefab</span><span class="sxs-lookup"><span data-stu-id="77024-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="77024-118">어떤 prefab를 손쉽게 인스턴스화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77024-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="77024-119">서비스가 예상 대로 작동 하려면 prefab에 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="77024-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="77024-120">IsKinematic이 활성화 된 rigidbody 구성 요소</span><span class="sxs-lookup"><span data-stu-id="77024-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="77024-121">Collider</span><span class="sxs-lookup"><span data-stu-id="77024-121">A collider</span></span>
- <span data-ttu-id="77024-122">`JointKinematicBody` 구성 요소</span><span class="sxs-lookup"><span data-stu-id="77024-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="77024-123">손무한 키니틱 본문 사용</span><span class="sxs-lookup"><span data-stu-id="77024-123">Use palm kinematic body</span></span>

<span data-ttu-id="77024-124">서비스가 손만 조인트에서 프리팹을 인스턴스화하려고 하는지 여부를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="77024-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="77024-125">손무한 키네틱 본문 프리팹</span><span class="sxs-lookup"><span data-stu-id="77024-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="77024-126">`UsePalmKinematicBody`를 사용하도록 설정하면 인스턴스화할 프리팹입니다.</span><span class="sxs-lookup"><span data-stu-id="77024-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="77024-127">와 마찬가지로 `FingerTipKinematicBodyPrefab` 이 프리팹에는 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="77024-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="77024-128">isKinematic을 사용하도록 설정된 고정된 구성 요소</span><span class="sxs-lookup"><span data-stu-id="77024-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="77024-129">충돌(collider)</span><span class="sxs-lookup"><span data-stu-id="77024-129">A collider</span></span>
- <span data-ttu-id="77024-130">`JointKinematicBody` 구성 요소</span><span class="sxs-lookup"><span data-stu-id="77024-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="77024-131">서비스를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="77024-131">How to use the service</span></span>

<span data-ttu-id="77024-132">사용하도록 설정되면 모든 충돌자의 속성을 사용하여 `IsTrigger` 10자리 전체에서 충돌 이벤트를 수신합니다(활성화된 경우 손아귀).</span><span class="sxs-lookup"><span data-stu-id="77024-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
