---
title: 대화 상자
description: MRTK의 대화 상자 오버레이 및 혼합 현실 응용 프로그램에서이를 사용 하는 방법에 대해 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 혼합 현실, HoloLens, UI 컨트롤, 상호 작용, ui, ux, UX 디자인, 공간 UI, 공간 상호 작용, 3D UI, 3D UX, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 18e446f6b35e8073f939d065de3572204e2967a1
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299998"
---
# <a name="dialog"></a><span data-ttu-id="65a94-104">대화 상자</span><span class="sxs-lookup"><span data-stu-id="65a94-104">Dialog</span></span>

![예 고 HoloLens에 단추가 표시 되지 않는 대화 상자 오버레이의 스크린샷](images/MRTK_UX_Dialog.jpg)

<span data-ttu-id="65a94-106">대화 상자 컨트롤은 종종 사용자 작업을 요청 하는 상황별 앱 정보를 제공 하는 UI 오버레이입니다.</span><span class="sxs-lookup"><span data-stu-id="65a94-106">Dialog controls are UI overlays that provide contextual app information, often requesting a user action.</span></span> <span data-ttu-id="65a94-107">대화 상자를 사용 하 여 작업을 완료 하기 전에 사용자에 게 중요 한 정보를 제공 하 고 확인 또는 추가 정보를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65a94-107">Use dialogs to give users important information and request confirmation or extra information before an action can be completed.</span></span>

<br>

---

## <a name="dialog-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="65a94-108">Unity 용 MRTK (Mixed Reality Toolkit)의 대화 상자</span><span class="sxs-lookup"><span data-stu-id="65a94-108">Dialog in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="65a94-109">MRTK는 하나 또는 두 개의 단추 옵션을 사용 하 여 세 가지 크기로 대화 상자 컨트롤을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="65a94-109">MRTK provides dialog control in three sizes with one or two button options.</span></span> <span data-ttu-id="65a94-110">근거리 또는 원거리 상호 작용 범위에 대 한 배치 거리를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65a94-110">You can also specify the placement distance for near or far interaction range.</span></span> 

- <span data-ttu-id="65a94-111">DialogSmall_192x96 prefab: 192x96mm</span><span class="sxs-lookup"><span data-stu-id="65a94-111">DialogSmall_192x96.prefab: 192x96mm</span></span>
- <span data-ttu-id="65a94-112">DialogMedium_192x128 prefab: 192x128mm</span><span class="sxs-lookup"><span data-stu-id="65a94-112">DialogMedium_192x128.prefab: 192x128mm</span></span>
- <span data-ttu-id="65a94-113">DialogLarge_192x192 prefab: 192x192mm</span><span class="sxs-lookup"><span data-stu-id="65a94-113">DialogLarge_192x192.prefab: 192x192mm</span></span>

![HoloLens에서 실행 되는 다양 한 크기 대화 상자 오버레이 스크린샷](images/MRTK_UX_Dialog_Types.jpg)


* <span data-ttu-id="65a94-115">자세한 내용은 [Mrtk-대화 상자](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="65a94-115">For more information, see [MRTK - Dialog](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/dialog).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="65a94-116">참조</span><span class="sxs-lookup"><span data-stu-id="65a94-116">See also</span></span>

* [<span data-ttu-id="65a94-117">커서</span><span class="sxs-lookup"><span data-stu-id="65a94-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="65a94-118">손 광선</span><span class="sxs-lookup"><span data-stu-id="65a94-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="65a94-119">Button</span><span class="sxs-lookup"><span data-stu-id="65a94-119">Button</span></span>](button.md)
* [<span data-ttu-id="65a94-120">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="65a94-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="65a94-121">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="65a94-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="65a94-122">조작</span><span class="sxs-lookup"><span data-stu-id="65a94-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="65a94-123">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="65a94-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="65a94-124">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="65a94-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="65a94-125">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="65a94-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="65a94-126">음성 명령</span><span class="sxs-lookup"><span data-stu-id="65a94-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="65a94-127">키보드</span><span class="sxs-lookup"><span data-stu-id="65a94-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="65a94-128">Tooltip</span><span class="sxs-lookup"><span data-stu-id="65a94-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="65a94-129">슬레이트</span><span class="sxs-lookup"><span data-stu-id="65a94-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="65a94-130">슬라이더</span><span class="sxs-lookup"><span data-stu-id="65a94-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="65a94-131">셰이더</span><span class="sxs-lookup"><span data-stu-id="65a94-131">Shader</span></span>](shader.md)
* [<span data-ttu-id="65a94-132">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="65a94-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="65a94-133">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="65a94-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="65a94-134">표면 자성</span><span class="sxs-lookup"><span data-stu-id="65a94-134">Surface magnetism</span></span>](surface-magnetism.md)
