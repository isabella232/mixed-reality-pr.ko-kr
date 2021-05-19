---
title: 시선 추적 눈과 손
description: MRTK에서 손 동작과 함께 시선 대상 지정을 기본 포인터로 사용하는 방법
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, EyeTracking,
ms.openlocfilehash: c9d5f23610d821aa1e50a3217a4be736601dc14d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143991"
---
# <a name="eyes--hand-interaction"></a><span data-ttu-id="de1a6-104">눈 + 손 상호 작용</span><span class="sxs-lookup"><span data-stu-id="de1a6-104">Eyes + hand interaction</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="de1a6-105">_모양 + 손 동작(시선_ 응시 & 손 제스처)을 지원하는 방법</span><span class="sxs-lookup"><span data-stu-id="de1a6-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="de1a6-106">이 페이지에서는 손 동작과 함께 시선 대상 지정을 기본 포인터로 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="de1a6-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="de1a6-107">[MRTK 시선 추적 데모에서는](../../example-scenes/eye-tracking-examples-overview.md)눈 + 손을 사용하는 몇 가지 예를 설명합니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="de1a6-107">In our [MRTK eye tracking demos](../../example-scenes/eye-tracking-examples-overview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="de1a6-108">[선택:](eye-tracking-target-selection.md)먼 홀로그램 단추를 보고 손가락 모으기 제스처를 수행하여 빠르게 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="de1a6-108">[Selection](eye-tracking-target-selection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="de1a6-109">**위치(이 문서)**: 홀로그램을 보고, 인덱스 손가락과 엄지 손가락으로 묶어 잡고, 손을 사용하여 주변으로 이동하여 홀로그램을 장면 전체로 Fluently 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="de1a6-109">**Positioning (this article)**: Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="de1a6-110">[탐색:](eye-tracking-navigation.md)확대하려는 위치를 살펴보고, 인덱스 손가락과 엄지 손가락을 묶고, 손을 _끌어와_ 확대합니다.</span><span class="sxs-lookup"><span data-stu-id="de1a6-110">[Navigation](eye-tracking-navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="de1a6-111">MRTK는 현재 원거리 손 광선이 우선 순위가 있는 포커스 포인터 역할을 하는 방식으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="de1a6-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="de1a6-112">즉, 손을 감지하면 머리 및 시선 응시 포인터가 자동으로 표시되지 않으며 "선택"이라고 말하면 다시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="de1a6-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected and will become visible again after saying "Select".</span></span>
<span data-ttu-id="de1a6-113">그러나 이 방법은 멀리서 상호 작용하려는 방식이 아니고 보기에서 손의 존재와는 별개로 간단한 _'응시 및 커밋'_ 상호 작용을 선호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de1a6-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="de1a6-114">손 광선을 사용하지 않도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="de1a6-114">How to disable the hand ray</span></span>

<span data-ttu-id="de1a6-115">손 광선 포인터를 사용하지 않도록 설정하려면 _입력 -> 포인터_ MRTK 구성 설정에서 _'DefaultControllerPointer'를_ 제거하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="de1a6-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="de1a6-116">앱에서 위에서 설명한 대로 눈과 손을 사용하려면 [시선 추적을 사용하기 위한](eye-tracking-basic-setup.md)모든 요구 사항을 충족하는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="de1a6-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](eye-tracking-basic-setup.md).</span></span>

![손 광선을 제거하는 방법](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="de1a6-118">시선 추적 샘플 패키지의 입력 프로필 _EyeTrackingDemoPointerProfile이_ 참조로 설정되는 방법을 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de1a6-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

### <a name="how-to-keep-gaze-pointer-always-on"></a><span data-ttu-id="de1a6-119">응시 포인터를 항상 켜진 상태로 유지하는 방법</span><span class="sxs-lookup"><span data-stu-id="de1a6-119">How to keep gaze pointer always on</span></span>

<span data-ttu-id="de1a6-120">손을 감지한 후 머리 또는 시선 응시 포인터를 자동으로 표시하지 않도록 하기 위해 응시를 [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) 지정하여 설정 또는 해제 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="de1a6-120">To avoid having the head or eye gaze pointers automatically suppressed once a hand is detected, the gaze [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) can be specified to control whether it should be on or off.</span></span>

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="de1a6-121">[`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md) 참조</span><span class="sxs-lookup"><span data-stu-id="de1a6-121">See [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span></span>

---
[<span data-ttu-id="de1a6-122">"MixedRealityToolkit의 시선 추적"으로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="de1a6-122">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
