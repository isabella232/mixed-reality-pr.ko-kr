---
title: 응시
description: MRTK의 응시 유형에 대한 누적
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 응시,
ms.openlocfilehash: 95dad85ca8154d35f73906b53019d3a52ced546f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176916"
---
# <a name="gaze"></a><span data-ttu-id="d27e2-104">응시</span><span class="sxs-lookup"><span data-stu-id="d27e2-104">Gaze</span></span>

<span data-ttu-id="d27e2-105">[응시는](/windows/mixed-reality/gaze) 사용자가 보고 있는 위치에 따라 세계와 상호 작용하는 입력의 한 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-105">[Gaze](/windows/mixed-reality/gaze) is a form of input that interacts with the world based on where the user is looking.</span></span> <span data-ttu-id="d27e2-106">응시는 서로 다른 두 가지 지역에 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-106">Gaze exists in two different flavors</span></span>

## <a name="head-gaze"></a><span data-ttu-id="d27e2-107">머리 응시</span><span class="sxs-lookup"><span data-stu-id="d27e2-107">Head gaze</span></span>

<span data-ttu-id="d27e2-108">이 유형의 응시는 머리/카메라가 보고 있는 방향을 기반으로 하며,</span><span class="sxs-lookup"><span data-stu-id="d27e2-108">This type of gaze is based on the direction that the head/camera is looking at.</span></span> <span data-ttu-id="d27e2-109">머리 응시는 시선 응시를 지원하지 않는 시스템 또는 하드웨어가 시선 응시를 지원할 수 있지만 올바른 권한 집합 [및 설정이](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) 수행되지 않은 경우 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-109">Head gaze is active on systems that don't support eye gaze, or in cases where the hardware may support eye gaze, but the right set of [permissions and setup](eye-tracking/eye-tracking-basic-setup.md#eye-tracking-requirements-checklist) has not been performed.</span></span>

<span data-ttu-id="d27e2-110">머리 응시는 일반적으로 홀로그램 프레임의 가운데에 배치한 다음 에어 탭 제스처를 수행하여 개체를 보는 것과 관련된 HoloLens 1 스타일 상호 작용과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-110">Head gaze is usually associated with HoloLens 1 style interactions involving looking at object by placing it in the center of the Holographic Frame and then performing the air tap gesture.</span></span>

## <a name="eye-gaze"></a><span data-ttu-id="d27e2-111">응시</span><span class="sxs-lookup"><span data-stu-id="d27e2-111">Eye gaze</span></span>

<span data-ttu-id="d27e2-112">이러한 유형의 응시는 사용자의 시선이 보이는 위치에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-112">This type of gaze is based on where the user's eyes are looking.</span></span> <span data-ttu-id="d27e2-113">시선 응시는 시선 추적을 지원하는 시스템에만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-113">Eye gaze is only present on systems that support eye tracking.</span></span> <span data-ttu-id="d27e2-114">시선 응시를 사용하는 방법에 대한 자세한 내용은 [시선 추적 설명서를](eye-tracking/eye-tracking-main.md) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d27e2-114">See the [eye tracking documentation](eye-tracking/eye-tracking-main.md) for more details on how to use eye gaze.</span></span>

## <a name="gazeprovider"></a><span data-ttu-id="d27e2-115">GazeProvider</span><span class="sxs-lookup"><span data-stu-id="d27e2-115">GazeProvider</span></span>

<span data-ttu-id="d27e2-116">응시 기능(머리 및 눈 모두)은 [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider)에서 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-116">Gaze functionality (both head and eye) is provided by the [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider).</span></span> <span data-ttu-id="d27e2-117">이 공급자는 입력 시스템 프로필의 *포인터* 섹션에서 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-117">This provider can be configured in the *Pointer* section of the input system profile:</span></span>

![응시 구성 진입점](../images/input/GazeConfigurationEntrypoint.png)

<span data-ttu-id="d27e2-119">다른 입력 소스와 마찬가지로 응시 공급자는 포인터를 사용하여 장면의 개체와 상호 [작용합니다(포인터에 대한 자세한 내용은 이 문서 참조).](../../architecture/controllers-pointers-and-focus.md)</span><span class="sxs-lookup"><span data-stu-id="d27e2-119">Like other sources of input, the gaze provider interacts with objects in the scene through use of a pointer [(see this document for information on pointers)](../../architecture/controllers-pointers-and-focus.md).</span></span>
<span data-ttu-id="d27e2-120">응시 공급자의 경우 포인터는 을 통해 `InternalGazePointer` 구현되며 프로필을 통해 구성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-120">In the case of the gaze provider, its pointer is implemented via `InternalGazePointer` and is not configured through a profile.</span></span>

<span data-ttu-id="d27e2-121">[IMixedRealityGazeProvider 및 IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) 를 구현하는 다른 클래스를 참조하도록 *응시 공급자 형식을* 변경하여 스톡 GazeProvider를 대체 구현으로 바꿀 수 있습니다. [](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider)</span><span class="sxs-lookup"><span data-stu-id="d27e2-121">It is possible to replace the stock GazeProvider with an alternate implementation by changing *Gaze Provider Type* to reference a different class that implements [IMixedRealityGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider) and [IMixedRealityEyeGazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider).</span></span>
<span data-ttu-id="d27e2-122">GazeProvider를 다시 구현하는 것은 사소하지 않을 수 있기 때문에 일반적으로 주식 GazeProvider를 사용하고 버그를 찾을 때 문제를 제출하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-122">It's generally recommended to use the stock GazeProvider (and filing issues in when finding bugs) as re-implementing the GazeProvider is non-trivial.</span></span>

### <a name="alternative-platform-provided-gaze-poses"></a><span data-ttu-id="d27e2-123">대체 플랫폼 제공 응시 자세</span><span class="sxs-lookup"><span data-stu-id="d27e2-123">Alternative platform-provided gaze poses</span></span>

<span data-ttu-id="d27e2-124">기본적으로 MRTK GazeProvider는 카메라 프레임의 중심을 응시 원점으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-124">By default, the MRTK GazeProvider uses the center of the camera's frame as the gaze origin.</span></span> <span data-ttu-id="d27e2-125">HoloLens 2 Windows Mixed Reality 같은 일부 플랫폼에서는 대체적으로 정의된 응시 자세를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-125">Some platforms, like Windows Mixed Reality on HoloLens 2, provide an alternatively defined gaze pose.</span></span> <span data-ttu-id="d27e2-126">응시 설정의 설정을 통해 `Use Head Gaze Override` 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-126">This is managed via the `Use Head Gaze Override` setting in the gaze settings.</span></span> <span data-ttu-id="d27e2-127">사용하도록 설정하면 대체 응시 재정의가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-127">When enabled, the alternative gaze override will be used.</span></span> <span data-ttu-id="d27e2-128">사용하지 않도록 설정하면 기본 프레임 중심 원점이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-128">When disabled, the default frame center origin will be used.</span></span> <span data-ttu-id="d27e2-129">특히 HoloLens 2 경우 응시 각도는 대상 지정을 위해 헤드를 사용할 때 사용자의 편의를 고려하여 몇 도씩 높아질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-129">Specifically, for HoloLens 2, the gaze angle will be raised several degrees to account for user comfort in using their head for targeting.</span></span>

## <a name="usage"></a><span data-ttu-id="d27e2-130">사용</span><span class="sxs-lookup"><span data-stu-id="d27e2-130">Usage</span></span>

### <a name="how-get-the-current-gaze-target"></a><span data-ttu-id="d27e2-131">현재 응시 대상을 얻는 방법</span><span class="sxs-lookup"><span data-stu-id="d27e2-131">How get the current gaze target</span></span>

<span data-ttu-id="d27e2-132">이 샘플에서는 사용자 응시의 대상이 되는 현재 게임 개체를 얻는 방법을 보여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d27e2-132">This sample shows how to get the current game object that is targeted by the user gaze.</span></span>

```c#
void LogCurrentGazeTarget()
{
    if (CoreServices.InputSystem.GazeProvider.GazeTarget)
    {
        Debug.Log("User gaze is currently over game object: "
            + CoreServices.InputSystem.GazeProvider.GazeTarget)
    }
}
```

### <a name="how-to-get-the-current-gaze-direction-and-origin"></a><span data-ttu-id="d27e2-133">현재 응시 방향 및 원점 얻는 방법</span><span class="sxs-lookup"><span data-stu-id="d27e2-133">How to get the current gaze direction and origin</span></span>

<span data-ttu-id="d27e2-134">이 샘플에서는 사용자 응시의 방향과 원점(방향이 진행되는 지점)을 나타내는 Vector3을 얻는 방법을 보여 주며,</span><span class="sxs-lookup"><span data-stu-id="d27e2-134">This sample shows how to get the Vector3 representing the direction of the user gaze and the origin (the point from which the direction is going).</span></span>

```c#
void LogGazeDirectionOrigin()
{
    Debug.Log("Gaze is looking in direction: "
        + CoreServices.InputSystem.GazeProvider.GazeDirection);

    Debug.Log("Gaze origin is: "
        + CoreServices.InputSystem.GazeProvider.GazeOrigin);
}
```
