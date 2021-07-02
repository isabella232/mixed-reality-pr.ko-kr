---
title: 플랫폼 기능 검색
description: MRTK가 지 원하는 다양 한 기능에 대 한 세부 정보
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 기능,
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175518"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="7219e-104">플랫폼 기능 검색</span><span class="sxs-lookup"><span data-stu-id="7219e-104">Detecting platform capabilities</span></span>

<span data-ttu-id="7219e-105">mrtk에 대 한 일반적인 질문은 응용 프로그램을 실행 하는 데 사용 되는 특정 장치 (예: Microsoft HoloLens 2)를 파악 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7219e-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="7219e-106">정확한 하드웨어를 식별 하는 것은 다양 한 플랫폼에서 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7219e-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="7219e-107">대신, MRTK는 런타임에 특정 기능을 식별 하는 방법을 제공 합니다 (예: 현재 장치 끝점이 트레일러 식을 지 원하는 경우).</span><span class="sxs-lookup"><span data-stu-id="7219e-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="7219e-108">기능</span><span class="sxs-lookup"><span data-stu-id="7219e-108">Capabilities</span></span>

<span data-ttu-id="7219e-109">혼합 현실 Toolkit는 [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) 응용 프로그램이 런타임에 쿼리할 수 있는 기능 집합을 정의 하는 열거형을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7219e-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="7219e-110">입력 시스템 기능</span><span class="sxs-lookup"><span data-stu-id="7219e-110">Input system capabilities</span></span>

<span data-ttu-id="7219e-111">기본 MRTK 입력 시스템은 다음 기능에 대 한 쿼리를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7219e-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="7219e-112">기능</span><span class="sxs-lookup"><span data-stu-id="7219e-112">Capability</span></span> | <span data-ttu-id="7219e-113">Description</span><span class="sxs-lookup"><span data-stu-id="7219e-113">Description</span></span> |
|---|---|
| <span data-ttu-id="7219e-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="7219e-114">ArticulatedHand</span></span> | <span data-ttu-id="7219e-115">트레일러 식 입력</span><span class="sxs-lookup"><span data-stu-id="7219e-115">Articulated hand input</span></span> |
| <span data-ttu-id="7219e-116">EyeTracking</span><span class="sxs-lookup"><span data-stu-id="7219e-116">EyeTracking</span></span> | <span data-ttu-id="7219e-117">아이 응시 대상</span><span class="sxs-lookup"><span data-stu-id="7219e-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="7219e-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="7219e-118">GGVHand</span></span> | <span data-ttu-id="7219e-119">응시-제스처-음성 입력</span><span class="sxs-lookup"><span data-stu-id="7219e-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="7219e-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="7219e-120">MotionController</span></span> | <span data-ttu-id="7219e-121">동작 컨트롤러 입력</span><span class="sxs-lookup"><span data-stu-id="7219e-121">Motion controller input</span></span> |
| <span data-ttu-id="7219e-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="7219e-122">VoiceCommand</span></span> | <span data-ttu-id="7219e-123">앱에서 정의한 키워드를 사용 하는 음성 명령</span><span class="sxs-lookup"><span data-stu-id="7219e-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="7219e-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="7219e-124">VoiceDictation</span></span> | <span data-ttu-id="7219e-125">음성 텍스트 받아쓰기</span><span class="sxs-lookup"><span data-stu-id="7219e-125">Voice to text dictation</span></span> |

<span data-ttu-id="7219e-126">아래 예제 코드에서는 입력 시스템에서 트레일러 식에 대 한 지원을 포함 하는 데이터 공급자를 로드 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7219e-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="7219e-127">공간 인식 기능</span><span class="sxs-lookup"><span data-stu-id="7219e-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="7219e-128">기본 MRTK 공간 인식 시스템은 다음 기능에 대 한 쿼리를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7219e-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="7219e-129">기능</span><span class="sxs-lookup"><span data-stu-id="7219e-129">Capability</span></span> | <span data-ttu-id="7219e-130">Description</span><span class="sxs-lookup"><span data-stu-id="7219e-130">Description</span></span> |
|---|---|
| <span data-ttu-id="7219e-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="7219e-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="7219e-132">공간 메시</span><span class="sxs-lookup"><span data-stu-id="7219e-132">Spatial meshes</span></span> |
| <span data-ttu-id="7219e-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="7219e-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="7219e-134">공간 평면</span><span class="sxs-lookup"><span data-stu-id="7219e-134">Spatial planes</span></span> |
| <span data-ttu-id="7219e-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="7219e-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="7219e-136">공간 점수</span><span class="sxs-lookup"><span data-stu-id="7219e-136">Spatial points</span></span> |

<span data-ttu-id="7219e-137">이 예제에서는 공간 인식 시스템이 공간 메시를 지 원하는 데이터 공급자를 로드 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7219e-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="7219e-138">참조</span><span class="sxs-lookup"><span data-stu-id="7219e-138">See also</span></span>

- [<span data-ttu-id="7219e-139">IMixedRealityCapabilityCheck API 설명서</span><span class="sxs-lookup"><span data-stu-id="7219e-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="7219e-140">MixedRealityCapability enum 설명서</span><span class="sxs-lookup"><span data-stu-id="7219e-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
