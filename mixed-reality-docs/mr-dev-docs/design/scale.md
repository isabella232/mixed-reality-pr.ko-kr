---
title: 확장
description: 홀로그램 형태로 사실적으로 보이는 콘텐츠를 표시하는 핵심 요소는 실제 세계의 시각적 통계를 최대한 긴밀하게 모방하는 것입니다.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed reality, 스타일, 디자인, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, 규모, holograms
ms.openlocfilehash: 12b1c96146f76274831c9bc3427cef93bb326f70
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583313"
---
# <a name="scale"></a><span data-ttu-id="25cf1-104">확장</span><span class="sxs-lookup"><span data-stu-id="25cf1-104">Scale</span></span>

<span data-ttu-id="25cf1-105">현실적인 holographic 콘텐츠를 표시 하는 핵심은 최대한 긴밀 하 게 실제 세계의 시각적 통계를 모방는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-105">The key to displaying realistic holographic content is mimicking the visual statistics of the real world as closely as possible.</span></span> <span data-ttu-id="25cf1-106">시각적 신호를 통합 하 여 실제 사용자가 개체의 위치, 개체의 크기 및 구성에 대 한 이해를 도울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-106">Incorporate visual cues to help real-world users understand where objects are, how big they are, and what they’re made of.</span></span> <span data-ttu-id="25cf1-107">개체의 크기는 개체 크기와 해당 위치에 대 한 신호를 이해 하기 위해 가장 중요 한 시각적 신호 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-107">The scale of an object is one of the most important visual cues because it gives viewer a sense of the objects size and cues to its location.</span></span> <span data-ttu-id="25cf1-108">또한 실제 규모에서 개체를 보는 것은 일반적으로 혼합 현실에 대 한 주요 환경 차이점 중 하나입니다. 이전 화면 기반 보기에서 사용할 수 없는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-108">Further, viewing objects at real scale is one of the key experience differentiators for mixed reality in general – something that hasn’t been possible on previous screen-based viewing.</span></span>

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a><span data-ttu-id="25cf1-109">개체 및 환경의 규모를 제안 하는 방법</span><span class="sxs-lookup"><span data-stu-id="25cf1-109">How to suggest the scale of objects and environments</span></span>

<span data-ttu-id="25cf1-110">개체의 눈금을 제안 하는 방법에는 여러 가지가 있으며, 그 중 일부는 다른 가시 요소에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-110">There are many ways to suggest the scale of an object, some of which have possible effects on other perceptual factors.</span></span> <span data-ttu-id="25cf1-111">중요 한 것은 개체를 ' 실제 ' 크기로 표시 하 고 사용자가 이동할 때 현실적인 크기를 유지 관리 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-111">The key one is to display objects at a ‘real’ size, and maintain that realistic size as users move.</span></span> <span data-ttu-id="25cf1-112">Holograms는 실제 개체가 수행 하는 것과 동일한 방식으로 사용자의 사용자의 시각적 각도를 더 가까이 또는 더 멀리 갈 때 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-112">Holograms will take up a different amount of a user’s visual angle of a user as they come closer or further away, the same way that real objects do.</span></span>

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a><span data-ttu-id="25cf1-113">사용자에 게 표시 되는 개체의 거리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-113">Use the distance of objects as they're presented to the user</span></span>

<span data-ttu-id="25cf1-114">일반적인 방법 중 하나는 사용자에 게 표시 되는 개체의 거리를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-114">One common method is to use the distance of objects as they're presented to the user.</span></span> <span data-ttu-id="25cf1-115">예를 들어 사용자 앞에 대형 패밀리 자동차를 시각화 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-115">For example, consider visualizing a large family car in front of the user.</span></span> <span data-ttu-id="25cf1-116">자동차가 arm의 길이 내에서 바로 앞에 있는 경우에는 너무 커서 사용자의 보기 필드에 적합 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-116">If the car was directly in front of them within arm’s length, it would be too large to fit in the user’s field of view.</span></span> <span data-ttu-id="25cf1-117">개체 닫기를 사용 하려면 사용자가 head 및 body를 이동 하 여 개체 전체를 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-117">Close objects require the user to move their head and body to understand the entirety of the object.</span></span> <span data-ttu-id="25cf1-118">자동차를 실내에 더 멀리 배치 하는 경우 사용자는 보기의 해당 필드에 있는 전체 개체를 확인 하 여 눈금의 의미를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-118">If the car is placed further away (across the room), the user can establish a sense of scale by seeing the entire object in their field of view.</span></span> <span data-ttu-id="25cf1-119">그러면 사용자가 개체에 더 가깝게 이동 하 여 보다 자세한 검사를 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-119">Users could then move themselves closer to the object for a more detailed inspection.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="25cf1-120">**[Volvo는이 기술을 사용](https://www.youtube.com/watch?v=DilzwF90vec)** 하 여 사용자에 게 실제적이 고 직관적인 방식으로 holographic car의 규모를 사용 하 여 새 자동차에 대 한 showroom 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-120">**[Volvo used this technique to create a showroom](https://www.youtube.com/watch?v=DilzwF90vec)** experience for a new car, using the scale of the holographic car in a way that felt realistic and intuitive to the user.</span></span> <span data-ttu-id="25cf1-121">이 환경은 실제 테이블에서 자동차가 시작 되며 사용자가 모델의 전체 크기와 모양을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-121">The experience begins with the car hologram on a physical table, allowing the user to understand the total size and shape of the model.</span></span> <span data-ttu-id="25cf1-122">환경에서 나중에 자동차는 장치의 보기 필드 크기 보다 큰 규모로 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-122">Later in the experience, the car expands to a scale beyond the size of the device's field of view.</span></span> <span data-ttu-id="25cf1-123">사용자가 더 작은 모델에서 참조 프레임을 이미 확보 했으므로 자동차의 기능을 적절 하 게 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-123">Since the user already acquired a frame of reference from the smaller model, they can adequately navigate around features of the car.</span></span><br>
        <br>
        <span data-ttu-id="25cf1-124">*이미지: HoloLens 용 Volvo 자동차 환경*</span><span class="sxs-lookup"><span data-stu-id="25cf1-124">*Image: Volvo Cars experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens 용 Volvo 자동차 환경](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a><span data-ttu-id="25cf1-126">Holograms를 사용 하 여 사용자의 실제 공간을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-126">Use holograms to modify the user's real space</span></span>

<span data-ttu-id="25cf1-127">또 다른 방법은 holograms을 사용 하 여 사용자의 실제 공간을 수정 하 고, 기존 옆면과 최대값이를 환경으로 바꾸거나 ' 구멍 ' 또는 ' windows '를 추가 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-127">Another method is to use holograms to modify the user's real space, replacing the existing walls or ceilings with environments or appending ‘holes’ or ‘windows’.</span></span> <span data-ttu-id="25cf1-128">이렇게 하면 크기가 큰 개체가 실제 공간을 ' 중단 ' 하는 것으로 보입니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-128">This allows over-sized objects to seemingly 'break-through' the physical space.</span></span> <span data-ttu-id="25cf1-129">예를 들어 큰 트리가 대부분의 사용자에 게는 적합 하지 않을 수 있지만, 해당 상한에 가상 하늘을 배치 하면 실제 공간이 가상으로 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-129">For example, a large tree might not fit in most users’ living rooms, but by putting a virtual sky on their ceiling, the physical space expands into the virtual.</span></span> <span data-ttu-id="25cf1-130">이를 통해 사용자는 가상 트리의 기반을 탐색 하 고 규모와 실제 환경의 의미를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-130">This allows the user to walk around the base of the virtual tree and gather a sense of scale and real-world appearance.</span></span> <span data-ttu-id="25cf1-131">그러면 사용자가 공간을 차지 하는 공간 보다 크게 확장 된 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-131">Users can then look up to see it extend far beyond the physical space of the room.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="25cf1-132">Minecraft는 유사한 기법을 사용 하 여 **[개념 환경을 개발](https://minecraft.net/)** 했습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-132">**[Minecraft developed a concept experiences](https://minecraft.net/)** using a similar technique.</span></span> <span data-ttu-id="25cf1-133">실제 표면에 가상 창을 추가 하면 방에 있는 기존 개체가 실내의 물리적인 크기 제한을 초과 하는 매우 큰 환경의 컨텍스트에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-133">By adding a virtual window to a physical surface, the existing objects in the room are placed in the context of a vastly larger environment, beyond the physical scale limitations of the room.</span></span><br>
        <br>
        <span data-ttu-id="25cf1-134">*이미지: HoloLens의 Minecraft 개념 환경*</span><span class="sxs-lookup"><span data-stu-id="25cf1-134">*Image: Minecraft concept experience for HoloLens*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens를 위한 Minecraft 개념 환경](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a><span data-ttu-id="25cf1-136">규모 실험</span><span class="sxs-lookup"><span data-stu-id="25cf1-136">Experimenting with scale</span></span>

<span data-ttu-id="25cf1-137">디자이너는 개체의 표시 된 ' 실제 ' 크기를 변경 하 여 눈금을 수정 하는 것을 실험 합니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-137">Designers have experimented with modifying the scale by changing the displayed ‘real’ size of the object.</span></span> <span data-ttu-id="25cf1-138">동시에 실제로 이동 하지 않고 개체를 뷰어로 이동 하는 단일 개체 위치를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-138">At the same time, they maintain a single object position to approximate an object moving towards the viewer without any actual movement.</span></span> <span data-ttu-id="25cf1-139">이는 일부 경우에는 "편안 하 게 영역" 보다 더 가까운 가상 콘텐츠 보기에 대 한 잠재적인 편안 한 제한 사항을 준수 하면서 항목의 정리를 시뮬레이션 하는 방법으로 테스트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-139">This was tested in some cases as a way to simulate up-close viewing of items while still respecting potential comfort limitations of viewing virtual content closer than the “zone of comfort” would suggest.</span></span>

<span data-ttu-id="25cf1-140">이렇게 하면 환경에서 몇 가지 가능한 아티팩트가 생성 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-140">This can create a few possible artifacts in the experience however:</span></span>
* <span data-ttu-id="25cf1-141">' 알려진 ' 크기의 특정 개체를 뷰어로 나타내는 가상 개체의 경우 위치를 변경 하지 않고 배율을 변경 하면 충돌 하는 시각적 표시로 이어질 수 있습니다. Vergence 큐로 인해 눈에도 개체를 어느 정도 깊이에서 볼 수 있습니다. 자세한 내용은 [편안한](comfort.md) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25cf1-141">For virtual objects that represent some object with a ‘known’ size to the viewer, changing the scale without changing the position leads to conflicting visual cues. The eyes may still ‘see’ the object at some depth because of vergence cues. For more information, see the [Comfort](comfort.md) article.</span></span> <span data-ttu-id="25cf1-142">크기는 개체가 더 monocular 큐로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-142">The size acts as a monocular cue that the object might be getting closer.</span></span> <span data-ttu-id="25cf1-143">이러한 충돌 하는 큐는 혼동을 야기 합니다. 예를 들어, 뷰어에는 상수 깊이 큐로 인해 개체가 그대로 유지 되지만 신속 하 게 증가 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-143">These conflicting cues lead to confused perceptions – viewers often see the object as staying in place (because of the constant depth cue) but growing rapidly.</span></span>
* <span data-ttu-id="25cf1-144">경우에 따라 소수 자릿수가 뷰어에 따라 크기가 변경 되는 것으로 표시 될 수도 있고 표시 되지 않을 수도 있는 ' looming ' 큐로 표시 되는 경우도 있습니다. 그러나 뷰어의 눈에 직접 이동 하는 것으로 보입니다 (불쾌 한 하루아침 수 있음).</span><span class="sxs-lookup"><span data-stu-id="25cf1-144">In some cases, change of scale is seen as a ‘looming’ cue instead, where the object may or may not be seen to change scale by a viewer, but does appear to be moving directly toward the viewer’s eyes (which can be an uncomfortable sensation).</span></span>
* <span data-ttu-id="25cf1-145">실제 세계의 비교 표면에서는 여러 축을 따라 위치를 변경 하는 경우를 들 수 있습니다. 즉, 개체가 더 가깝게 이동 하는 대신 드롭다운으로 표시 됩니다 (경우에 따라 3D 이동의 2D 프로젝션과 유사).</span><span class="sxs-lookup"><span data-stu-id="25cf1-145">With comparison surfaces in the real world, such scaling changes are sometimes seen as changing position along multiple axes – objects appear to drop lower instead of moving closer (similar in a 2D projection of 3D movement in some cases).</span></span>
* <span data-ttu-id="25cf1-146">마지막으로, 알려진 ' 실제 세계 ' 크기가 없는 개체 (예: 임의의 크기, UI 요소 등의 임의 셰이프)의 경우 크기 변경으로 인해 변화 하는 거리를 모방 하는 방법으로 기능적으로 동작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-146">Finally, for objects without a known ‘real world’ size (for example, arbitrary shapes with arbitrary sizes, UI elements, and so on), changing scale may act functionally as a way to mimic changes in distance.</span></span> <span data-ttu-id="25cf1-147">뷰어에는 개체의 true 크기 또는 위치를 이해 하기 위한 기존의 하향식 큐가 많지 않으므로 소수 자릿수를 보다 중요 한 큐로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25cf1-147">Viewers don't have as many pre-existing top-down cues to understand the object’s true size or location, so the scale can be processed as a more important cue.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="25cf1-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25cf1-148">See also</span></span>
* [<span data-ttu-id="25cf1-149">색, 광원 및 재질</span><span class="sxs-lookup"><span data-stu-id="25cf1-149">Color, light, and materials</span></span>](./color-light-and-materials.md)
* [<span data-ttu-id="25cf1-150">입력 체계</span><span class="sxs-lookup"><span data-stu-id="25cf1-150">Typography</span></span>](typography.md)
* [<span data-ttu-id="25cf1-151">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="25cf1-151">Spatial sound design</span></span>](spatial-sound-design.md)