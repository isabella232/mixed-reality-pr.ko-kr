---
title: 탄력 시스템
description: MRTK의 탄력적 시뮬레이션과 관련된 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, ElasticsSystem,
ms.openlocfilehash: 01a4c4a337593252e0955c03e883e35e1329fc45
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145185"
---
# <a name="elastic-system-experimental"></a><span data-ttu-id="a1740-104">탄력적 시스템(실험적)</span><span class="sxs-lookup"><span data-stu-id="a1740-104">Elastic system (experimental)</span></span>

![탄력 시스템](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="a1740-106">MRTK는 4차원 4차원 쿼터니언 Spring, 3차원 볼륨 Spring 및 간단한 선형 Spring 시스템에 대한 바인딩을 제공하는 다양하고 유연하고 다양한 서브클래스를 포함하는 탄력적 시뮬레이션 시스템과 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="a1740-107">현재 [탄력적 관리자를](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) 지원하는 다음 MRTK 구성 요소는 탄력적 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="a1740-108">경계 컨트롤</span><span class="sxs-lookup"><span data-stu-id="a1740-108">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="a1740-109">개체 조작자</span><span class="sxs-lookup"><span data-stu-id="a1740-109">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="a1740-110">Elastics 관리자</span><span class="sxs-lookup"><span data-stu-id="a1740-110">Elastics manager</span></span>

![탄력적 시스템 2](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="a1740-112">탄력적 관리자는 전달된 변환을 처리하고 탄력적 시스템에 공급합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="a1740-113">사용자 지정 구성 요소에 탄력적 기능을 사용하도록 설정하는 것은 다음 두 단계로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="a1740-114">조작 시작 시 Initialize 메서드를 호출하여 현재 호스트 변환으로 시스템을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="a1740-115">업데이트된 대상 변환에서 탄력적 계산을 수행해야 할 때마다 ApplyHostTransform을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="a1740-116">탄력적은 조작이 끝나면(Elastics Manager 업데이트 루프를 통해) 시뮬레이션을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="a1740-117">동작을 차단하기 위해 Elastics 자동 업데이트 [EnableElasticsUpdate를](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) false로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="a1740-118">기본적으로 elastics Manager 구성 요소는 게임 개체에 추가될 때 변환 형식에 대해 활성화된 탄력적 을 갖지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="a1740-119">선택한 `Manipulation types using elastic feedback` 형식에 대한 탄력적 구성 및 익스텐트 만들기를 위해 특정 변환 형식에 대해 필드를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="a1740-120">탄력적 구성</span><span class="sxs-lookup"><span data-stu-id="a1740-120">Elastics configurations</span></span>

<span data-ttu-id="a1740-121">범위 [제어 구성과](../ux-building-blocks/bounds-control.md#configuration-objects)마찬가지로 탄력적 관리자는 스크립팅 가능한 개체로 저장하고 서로 다른 인스턴스 또는 프리팹 간에 공유할 수 있는 구성 개체 집합과 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-121">Similar to [bounds control configurations](../ux-building-blocks/bounds-control.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="a1740-122">구성은 개별 스크립팅 가능한 자산 파일 또는 프리팹 내에 중첩된 스크립팅 가능한 자산으로 공유 및 연결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="a1740-123">외부 또는 중첩 된 스크립트 가능한 자산에 연결 하지 않고도 인스턴스에서 직접 구성을 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="a1740-124">탄력적 manager 검사기는 속성 검사자에 메시지를 표시 하 여 구성이 공유 되는지 또는 현재 인스턴스의 일부로 인라인 되어 있는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="a1740-125">또한 탄력적 manager 속성 창 자체에서 공유 인스턴스를 직접 편집할 수는 없지만 대신 연결 되는 자산은 공유 구성에 대 한 실수로 인 한 변경 사항을 방지 하기 위해 직접 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="a1740-126">탄력적 manager는 다음과 같은 변환 형식에 대 한 구성 개체 옵션을 제공 합니다. 각 개체에는 [탄력적 구성 개체가](#elastic-configuration-object)표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="a1740-127">변환 탄력적</span><span class="sxs-lookup"><span data-stu-id="a1740-127">Translation Elastic</span></span>
- <span data-ttu-id="a1740-128">회전 탄력적</span><span class="sxs-lookup"><span data-stu-id="a1740-128">Rotation Elastic</span></span>
- <span data-ttu-id="a1740-129">탄력적 확장</span><span class="sxs-lookup"><span data-stu-id="a1740-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="a1740-130">탄력적 구성 개체</span><span class="sxs-lookup"><span data-stu-id="a1740-130">Elastic configuration object</span></span>

<span data-ttu-id="a1740-131">탄력적 구성은 damp 조화 오실 레이 터 차등 시스템에 대 한 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="a1740-132">다음 속성은 조정 될 수 있지만 이미 MRTK의 기본값 집합과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="a1740-133">**Mass**: 시뮬레이션 된 오실 레이 터 요소의 질량입니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="a1740-134">**수동 k**: 손 스프링 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="a1740-135">**Endk**: end 캡 스프링 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="a1740-136">**SnapK**: snap point 스프링 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="a1740-137">**끌어서** 놓기/댐퍼 계수를 속도에 비례 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="a1740-138">탄력적 익스텐트</span><span class="sxs-lookup"><span data-stu-id="a1740-138">Elastics extents</span></span>

<span data-ttu-id="a1740-139">탄력적 익스텐트 설정은 조작 유형에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="a1740-140">변환 및 소수 자릿수는 [볼륨 탄력적 범위로](#volume-elastic-extent) 표현 되며, 회전은 [4 원수 탄력적 범위로](#quaternion-elastic-extent)표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="a1740-141">볼륨 탄력적 범위</span><span class="sxs-lookup"><span data-stu-id="a1740-141">Volume elastic extent</span></span>

<span data-ttu-id="a1740-142">볼륨 익스텐트는 damp 조화 오실 레이 터가 자유롭게 이동할 수 있는 3 차원 공간을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![탄력적 볼륨 스트레치 범위](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="a1740-144">**StretchBounds**: 탄력적 공간의 하한을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="a1740-145">**UseBounds:** 시스템에서 확장 범위를 적용해야 하는지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="a1740-146">true이면 대상 위치의 현재 반복이 늘이기 범위를 벗어나면 끝 강제가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="a1740-147">**SnapPoints:** 시스템이 맞춰질 공간 내부를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="a1740-148">**RepeatSnapPoints**: 맞춤 지점을 무한대로 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="a1740-149">기존 맞춤 지점은 실제 맞춤 지점이 모든 맞춤 지점의 가장 가까운 정수 배수에 매핑되는 모듈로 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="a1740-150">**SnapRadius:** 맞춤 지점이 강제로 봄을 적용하기 시작하는 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![탄력적 볼륨 맞춤 표](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="a1740-152">4원수 탄력적 익스텐트</span><span class="sxs-lookup"><span data-stu-id="a1740-152">Quaternion elastic extent</span></span>

<span data-ttu-id="a1740-153">4원수 익스텐트에서는 4차원 회전 공간을 정의합니다. 이 공간은 습한 경기성 오실레이터를 자유롭게 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![탄력적 회전 예제](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="a1740-155">**SnapPoints:** 시스템이 맞춰질 내러 각도입니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="a1740-156">**RepeatSnapPoints**: 맞춤 지점을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="a1740-157">기존 맞춤 지점은 실제 맞춤 지점이 모든 맞춤 지점의 가장 가까운 정수 배수에 매핑되는 모듈로 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="a1740-158">**SnapRadius:** 맞춤 지점이 유러 도의 봄을 강제로 시작하는 원호 각도입니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="a1740-159">탄력적 예제 장면</span><span class="sxs-lookup"><span data-stu-id="a1740-159">Elastics example scene</span></span>

<span data-ttu-id="a1740-160">장면에서 탄력적 구성의 예를 찾을 수 `ElasticSystemExample` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1740-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![탄력적 예제 장면](../images/elastics/Elastics_Example_Scene.png)
