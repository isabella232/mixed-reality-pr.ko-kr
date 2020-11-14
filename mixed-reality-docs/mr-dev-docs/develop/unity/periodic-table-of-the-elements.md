---
title: 원소의 주기율표
description: 요소의 정기 테이블은 Microsoft의 혼합 현실 디자인 랩에서 오픈 소스 샘플 앱으로, 개체 컬렉션을 사용 하 여 다양 한 표면 유형을 포함 하는 3D 공간에서 개체의 배열을 레이아웃 하는 방법을 배울 수 있습니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 샘플 앱, 컨트롤
ms.openlocfilehash: 82ffa19b27c1d2687b67df659cb3bb50544748fc
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573267"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="986a0-104">원소의 주기율표</span><span class="sxs-lookup"><span data-stu-id="986a0-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="986a0-105">이 문서에서는 혼합 현실 앱 개발에 대 한 학습 정보 및 제안을 공유 하는 위치를 [혼합 현실 디자인 랩에서](https://github.com/Microsoft/MRDesignLabs_Unity)만든 예비 샘플에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="986a0-106">디자인 관련 문서와 코드는 새로운 검색을 수행할 때 개선 됩니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="986a0-107">[요소의 정기 테이블](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 은 Microsoft의 혼합 현실 디자인 랩에서 오픈 소스 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="986a0-108">이 프로젝트를 사용 하 여 **[개체 컬렉션](../../design/object-collection.md)** 을 사용 하는 다양 한 표면 형식으로 3d 공간에서 개체의 배열을 레이아웃 하는 방법을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="986a0-109">또한 HoloLens에서 표준 입력에 응답 하는 interactable 개체를 만드는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="986a0-110">이 프로젝트의 구성 요소를 사용 하 여 혼합 현실 앱 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![요소 앱의 기간 테이블](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="986a0-112">데모 비디오</span><span class="sxs-lookup"><span data-stu-id="986a0-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="986a0-113">혼합 현실 캡처를 사용 하 여 HoloLens 2로 기록 됨</span><span class="sxs-lookup"><span data-stu-id="986a0-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="986a0-114">앱 정보</span><span class="sxs-lookup"><span data-stu-id="986a0-114">About the app</span></span>

<span data-ttu-id="986a0-115">요소의 주기적 테이블은 시각화 요소와 각 속성을 3D 공간에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="986a0-116">이 도구는 응시 및 air 탭과 같은 HoloLens의 기본 상호 작용을 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="986a0-117">사용자는 애니메이션 3D 모델을 사용 하 여 요소에 대해 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="986a0-118">이러한 사용자는 protons 및 neutrons로 구성 된 요소의 전자 핵심 이기를 시각적으로 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="986a0-119">배경</span><span class="sxs-lookup"><span data-stu-id="986a0-119">Background</span></span>

<span data-ttu-id="986a0-120">HoloLens를 처음 경험 하 고 나면, 정기적 테이블 앱은 혼합 현실에서 시험해 보고 싶을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-120">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="986a0-121">각 요소에는 텍스트와 함께 표시 되는 데이터 요소가 많기 때문에 3D 공간에서 입력 컴퍼지션을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="986a0-122">요소의 전자 모델을 시각화할 수 있는 것은이 프로젝트의 또 다른 흥미로운 부분 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-122">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="986a0-123">디자인</span><span class="sxs-lookup"><span data-stu-id="986a0-123">Design</span></span>

<span data-ttu-id="986a0-124">정기적 테이블의 기본 보기에서는 각 요소의 전자 모델을 포함 하는 3 차원 상자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="986a0-125">사용자가 요소의 볼륨에 대 한 대략적인 아이디어를 얻을 수 있도록 각 상자의 표면이 반투명 하 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="986a0-126">사용자는 응시 및 air 탭을 사용 하 여 각 요소의 자세히 보기를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="986a0-127">테이블 뷰와 자세히 보기를 자연스럽 고 자연스럽 게 전환 하기 위해 실시간으로 열리는 상자의 물리적 상호 작용과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="986a0-128">![스케치 디자인](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="986a0-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="986a0-129">*디자인 스케치*</span><span class="sxs-lookup"><span data-stu-id="986a0-129">*Design sketches*</span></span>

<span data-ttu-id="986a0-130">자세히 보기에서는 원활 렌더링 된 텍스트를 사용 하 여 각 요소의 정보를 3D 공간에 시각화 하고자 했습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="986a0-131">애니메이션 3D 전자 모델은 가운데 영역에 표시 되며 다른 각도에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![조작](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="986a0-133">![모델링할](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="986a0-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="986a0-134">*상호 작용 프로토타입*</span><span class="sxs-lookup"><span data-stu-id="986a0-134">*Interaction prototypes*</span></span>

<span data-ttu-id="986a0-135">사용자는 테이블 아래쪽의 단추를 눌러 표면 유형을 변경할 수 있습니다. 평면, 원통, 구 및 산 사이를 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="986a0-136">이 응용 프로그램에서 사용 되는 공용 컨트롤 및 패턴</span><span class="sxs-lookup"><span data-stu-id="986a0-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="986a0-137">Interactable 개체 (button)</span><span class="sxs-lookup"><span data-stu-id="986a0-137">Interactable object (button)</span></span>

<span data-ttu-id="986a0-138">[Interactable 개체](../../design/interactable-object.md) 는 기본 HoloLens 입력에 응답할 수 있는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-138">[Interactable object](../../design/interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="986a0-139">모든 개체에 쉽게 적용할 수 있는 prefab/스크립트로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-139">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="986a0-140">예를 들어 장면 interactable에서 커피 컵을 만들고 응시, 공중 탭, 탐색 및 조작 제스처와 같은 입력에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="986a0-141">자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="986a0-141">Learn more</span></span>](../../design/interactable-object.md)

![nteractable 개체](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="986a0-143">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="986a0-143">Object collection</span></span>

<span data-ttu-id="986a0-144">[개체 컬렉션](../../design/object-collection.md) 은 다양 한 셰이프에서 여러 개체의 레이아웃을 설정 하는 데 도움이 되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-144">[Object collection](../../design/object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="986a0-145">평면, 원통, 구 및 산을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-145">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="986a0-146">Radius, 행 수 및 간격과 같은 추가 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="986a0-147">자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="986a0-147">Learn more</span></span>](../../design/object-collection.md)

![개체 컬렉션](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="986a0-149">기술 세부 정보</span><span class="sxs-lookup"><span data-stu-id="986a0-149">Technical details</span></span>

<span data-ttu-id="986a0-150">[혼합 현실 디자인 실험 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)에서 Elements 앱의 주기 테이블에 대 한 스크립트 및 prefabs를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="986a0-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="986a0-151">HoloLens의 포팅 스토리 2</span><span class="sxs-lookup"><span data-stu-id="986a0-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="986a0-152">요소 앱의 주기 테이블이 HoloLens 2의 instinctual 상호 작용으로 업데이트 된 방법에 대 한 스토리를 읽어 보세요.</span><span class="sxs-lookup"><span data-stu-id="986a0-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="986a0-153">원소의 주기율표 2.0</span><span class="sxs-lookup"><span data-stu-id="986a0-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="986a0-154">작성자 정보</span><span class="sxs-lookup"><span data-stu-id="986a0-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="986a0-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="986a0-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="986a0-156">UX 디자이너 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="986a0-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="986a0-157">참조</span><span class="sxs-lookup"><span data-stu-id="986a0-157">See also</span></span>

* <span data-ttu-id="986a0-158">[MRTK 예제 허브](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(HoloLens 2의 Microsoft Store에서 다운로드)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="986a0-158">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="986a0-159">[Surfaces](sampleapp-surfaces.md) - [(HoloLens 2의 Microsoft Store에서 다운로드)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="986a0-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="986a0-160">원소의 주기율표 2.0</span><span class="sxs-lookup"><span data-stu-id="986a0-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="986a0-161">갤럭시 익스플로러 2.0</span><span class="sxs-lookup"><span data-stu-id="986a0-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)