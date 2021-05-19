---
title: 플랫폼 기능 검색
description: MRTK에서 지원하는 다양한 기능에 대한 세부 정보
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 기능,
ms.openlocfilehash: e6f5a70120b2634a4c8c75cdca3d8b369967c4b0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143863"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="206a0-104">플랫폼 기능 검색</span><span class="sxs-lookup"><span data-stu-id="206a0-104">Detecting platform capabilities</span></span>

<span data-ttu-id="206a0-105">MRTK에 대한 일반적인 질문은 애플리케이션을 실행하는 데 사용되는 특정 디바이스(예: Microsoft HoloLens 2)를 파악하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="206a0-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="206a0-106">정확한 하드웨어를 식별하는 것은 다양한 플랫폼에서 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="206a0-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="206a0-107">대신 MRTK는 런타임에 특정 기능을 식별하는 방법을 제공합니다(예: 현재 디바이스 엔드포인트가 굴절된 손을 지원하는 경우).</span><span class="sxs-lookup"><span data-stu-id="206a0-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="206a0-108">기능</span><span class="sxs-lookup"><span data-stu-id="206a0-108">Capabilities</span></span>

<span data-ttu-id="206a0-109">Mixed Reality 도구 키트는 [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) 애플리케이션이 런타임에 쿼리할 수 있는 기능 집합을 정의하는 열거형을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="206a0-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="206a0-110">입력 시스템 기능</span><span class="sxs-lookup"><span data-stu-id="206a0-110">Input system capabilities</span></span>

<span data-ttu-id="206a0-111">기본 MRTK 입력 시스템은 다음 기능 쿼리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="206a0-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="206a0-112">기능</span><span class="sxs-lookup"><span data-stu-id="206a0-112">Capability</span></span> | <span data-ttu-id="206a0-113">설명</span><span class="sxs-lookup"><span data-stu-id="206a0-113">Description</span></span> |
|---|---|
| <span data-ttu-id="206a0-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="206a0-114">ArticulatedHand</span></span> | <span data-ttu-id="206a0-115">굴절형 손 입력</span><span class="sxs-lookup"><span data-stu-id="206a0-115">Articulated hand input</span></span> |
| <span data-ttu-id="206a0-116">EyeTracking</span><span class="sxs-lookup"><span data-stu-id="206a0-116">EyeTracking</span></span> | <span data-ttu-id="206a0-117">시선 응시 대상 지정</span><span class="sxs-lookup"><span data-stu-id="206a0-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="206a0-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="206a0-118">GGVHand</span></span> | <span data-ttu-id="206a0-119">응시 제스처-음성 손 입력</span><span class="sxs-lookup"><span data-stu-id="206a0-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="206a0-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="206a0-120">MotionController</span></span> | <span data-ttu-id="206a0-121">모션 컨트롤러 입력</span><span class="sxs-lookup"><span data-stu-id="206a0-121">Motion controller input</span></span> |
| <span data-ttu-id="206a0-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="206a0-122">VoiceCommand</span></span> | <span data-ttu-id="206a0-123">앱 정의 키워드를 사용하는 음성 명령</span><span class="sxs-lookup"><span data-stu-id="206a0-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="206a0-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="206a0-124">VoiceDictation</span></span> | <span data-ttu-id="206a0-125">음성 텍스트 받아쓰기</span><span class="sxs-lookup"><span data-stu-id="206a0-125">Voice to text dictation</span></span> |

<span data-ttu-id="206a0-126">아래 예제 코드는 입력 시스템이 굴절된 손을 지원하는 데이터 공급자를 로드했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="206a0-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="206a0-127">공간 인식 기능</span><span class="sxs-lookup"><span data-stu-id="206a0-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="206a0-128">기본 MRTK 공간 인식 시스템은 다음 기능 쿼리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="206a0-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="206a0-129">기능</span><span class="sxs-lookup"><span data-stu-id="206a0-129">Capability</span></span> | <span data-ttu-id="206a0-130">설명</span><span class="sxs-lookup"><span data-stu-id="206a0-130">Description</span></span> |
|---|---|
| <span data-ttu-id="206a0-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="206a0-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="206a0-132">공간 메시</span><span class="sxs-lookup"><span data-stu-id="206a0-132">Spatial meshes</span></span> |
| <span data-ttu-id="206a0-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="206a0-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="206a0-134">공간 평면</span><span class="sxs-lookup"><span data-stu-id="206a0-134">Spatial planes</span></span> |
| <span data-ttu-id="206a0-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="206a0-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="206a0-136">공간 지점</span><span class="sxs-lookup"><span data-stu-id="206a0-136">Spatial points</span></span> |

<span data-ttu-id="206a0-137">이 예제에서는 공간 인식 시스템이 공간 메시를 지원하는 데이터 공급자를 로드했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="206a0-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="206a0-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="206a0-138">See also</span></span>

- [<span data-ttu-id="206a0-139">IMixedRealityCapabilityCheck API 설명서</span><span class="sxs-lookup"><span data-stu-id="206a0-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="206a0-140">MixedRealityCapability 열거형 설명서</span><span class="sxs-lookup"><span data-stu-id="206a0-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
