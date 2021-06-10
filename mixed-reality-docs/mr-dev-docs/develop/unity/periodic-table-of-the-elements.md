---
title: 원소의 주기율표
description: Elements 샘플 앱의 주기적 테이블과 함께 Object 컬렉션을 사용하여 다양한 표면 형식의 3D 공간에서 개체 배열을 레이아웃하는 방법을 알아봅니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 샘플 앱, 컨트롤, MRTK, Mixed Reality Toolkit, Unity, 샘플 앱, 예제 앱, 오픈 소스, Microsoft Store, HoloLens, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: ed8c35fc6467322c25b92924b134f176fa4a9b47
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743417"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="f0f1a-104">원소의 주기율표</span><span class="sxs-lookup"><span data-stu-id="f0f1a-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="f0f1a-105">이 문서에서는 혼합 현실 앱 개발에 대한 학습 및 제안을 공유하는 [Mixed Reality Design Labs에서](https://github.com/Microsoft/MRDesignLabs_Unity)만든 예비 샘플을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="f0f1a-106">디자인 관련 문서와 코드는 새로운 검색을 통해 발전할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="f0f1a-107">[주기적 요소 테이블은](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) Microsoft Mixed Reality Design Labs의 오픈 소스 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="f0f1a-108">**[개체 컬렉션](../../design/object-collection.md)** 을 사용하여 다양한 표면 형식의 3D 공간에서 개체 배열을 레이아웃하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-108">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="f0f1a-109">또한 HoloLens의 표준 입력에 응답하는 상호 작용 가능한 개체를 만드는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="f0f1a-110">이 프로젝트의 구성 요소를 사용하여 사용자 고유의 혼합 현실 앱 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Elements 앱의 기간 테이블](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="f0f1a-112">데모 동영상</span><span class="sxs-lookup"><span data-stu-id="f0f1a-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="f0f1a-113">혼합 현실 캡처 사용하여 HoloLens 2 기록</span><span class="sxs-lookup"><span data-stu-id="f0f1a-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="f0f1a-114">앱 정보</span><span class="sxs-lookup"><span data-stu-id="f0f1a-114">About the app</span></span>

<span data-ttu-id="f0f1a-115">요소의 주기적 테이블은 화학 요소와 각 속성을 3D 공간에서 시각화합니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="f0f1a-116">응시 및 에어 탭과 같은 HoloLens의 기본 상호 작용을 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="f0f1a-117">사용자는 애니메이션 3D 모델을 통해 요소에 대해 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="f0f1a-118">원통과 신경망으로 구성된 요소의 전자 셸과 해당 원통을 시각적으로 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="f0f1a-119">배경</span><span class="sxs-lookup"><span data-stu-id="f0f1a-119">Background</span></span>

<span data-ttu-id="f0f1a-120">HoloLens를 처음 접한 후 혼합 현실에서 주기적인 테이블 앱을 실험하고 싶습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-120">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="f0f1a-121">각 요소에는 텍스트와 함께 표시되는 많은 데이터 요소가 있기 때문에 3D 공간에서 입력 체계 컴퍼지션을 탐색하는 데 중요한 주제가 될 것이라고 생각합니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="f0f1a-122">사용자에게 요소의 전자 모델을 시각화할 수 있는 기회를 제공하는 것은 이 프로젝트의 또 다른 흥미로운 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-122">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="f0f1a-123">디자인</span><span class="sxs-lookup"><span data-stu-id="f0f1a-123">Design</span></span>

<span data-ttu-id="f0f1a-124">주기적 테이블의 기본 보기에서는 각 요소의 전자 모델이 포함된 3차원 상자를 생각해 보았습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="f0f1a-125">각 상자의 표면은 반투명하게 되어 사용자가 요소의 볼륨에 대한 대략적인 아이디어를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="f0f1a-126">응시 및 에어 탭을 통해 사용자는 각 요소의 자세한 보기를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="f0f1a-127">테이블 뷰와 세부 정보 보기 간의 전환을 원활하고 자연스럽게 만들기 위해 실제로 열리는 상자의 물리적 상호 작용과 유사하게 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="f0f1a-128">![디자인 스케치](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="f0f1a-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="f0f1a-129">*스케치 디자인*</span><span class="sxs-lookup"><span data-stu-id="f0f1a-129">*Design sketches*</span></span>

<span data-ttu-id="f0f1a-130">세부 정보 보기에서 각 요소의 정보를 3D 공간에서 렌더링된 텍스트로 시각화하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="f0f1a-131">애니메이션된 3D 전자 모델은 가운데 영역에 표시되며 다른 각도에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![상호 작용](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="f0f1a-133">![프로토 타입](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="f0f1a-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="f0f1a-134">*상호 작용 프로토타입*</span><span class="sxs-lookup"><span data-stu-id="f0f1a-134">*Interaction prototypes*</span></span>

<span data-ttu-id="f0f1a-135">사용자는 테이블 아래쪽의 단추를 에어 탭하여 표면 유형을 변경할 수 있습니다. 평면, 실린더, 구 및 분산형 간에 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="f0f1a-136">이 앱에서 사용되는 일반적인 컨트롤 및 패턴</span><span class="sxs-lookup"><span data-stu-id="f0f1a-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="f0f1a-137">상호 작용 가능한 개체(단추)</span><span class="sxs-lookup"><span data-stu-id="f0f1a-137">Interactable object (button)</span></span>

<span data-ttu-id="f0f1a-138">[상호 작용 가능한 개체는](../../design/interactable-object.md) 기본 HoloLens 입력에 응답할 수 있는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-138">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="f0f1a-139">모든 개체에 쉽게 적용할 수 있는 프리팹/스크립트로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-139">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="f0f1a-140">예를 들어 장면에서 커피 한 잔을 상호 작용 가능하도록 만들고 응시, 에어 탭, 탐색 및 조작 제스처와 같은 입력에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="f0f1a-141">자세한 정보</span><span class="sxs-lookup"><span data-stu-id="f0f1a-141">Learn more</span></span>](../../design/interactable-object.md)

![nteractable 개체](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="f0f1a-143">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="f0f1a-143">Object collection</span></span>

<span data-ttu-id="f0f1a-144">[개체 컬렉션은](../../design/object-collection.md) 여러 개체를 다양한 모양으로 레이아웃하는 데 도움이 되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-144">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="f0f1a-145">평면, 실린더, 구 및 분산형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-145">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="f0f1a-146">반경, 행 수 및 간격과 같은 추가 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="f0f1a-147">자세한 정보</span><span class="sxs-lookup"><span data-stu-id="f0f1a-147">Learn more</span></span>](../../design/object-collection.md)

![개체 컬렉션](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="f0f1a-149">기술 세부 정보</span><span class="sxs-lookup"><span data-stu-id="f0f1a-149">Technical details</span></span>

<span data-ttu-id="f0f1a-150">[Mixed Reality Design Labs GitHub에서](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)Elements 앱의 주기적 테이블에 대한 스크립트와 프리팹을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="f0f1a-151">HoloLens 2 대한 포팅 스토리</span><span class="sxs-lookup"><span data-stu-id="f0f1a-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="f0f1a-152">elements 앱의 주기적 테이블이 HoloLens 2 직관적 상호 작용으로 업데이트된 방법에 대한 스토리를 읽어보십시오.</span><span class="sxs-lookup"><span data-stu-id="f0f1a-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="f0f1a-153">원소의 주기율표 2.0</span><span class="sxs-lookup"><span data-stu-id="f0f1a-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="f0f1a-154">작성자 정보</span><span class="sxs-lookup"><span data-stu-id="f0f1a-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="f0f1a-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="f0f1a-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="f0f1a-156">UX 디자이너 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f0f1a-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="f0f1a-157">참조</span><span class="sxs-lookup"><span data-stu-id="f0f1a-157">See also</span></span>

* <span data-ttu-id="f0f1a-158">[MRTK 예제 허브](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(HoloLens 2의 Microsoft Store에서 다운로드)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="f0f1a-158">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="f0f1a-159">[Surfaces](sampleapp-surfaces.md) - [(HoloLens 2의 Microsoft Store에서 다운로드)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="f0f1a-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="f0f1a-160">원소의 주기율표 2.0</span><span class="sxs-lookup"><span data-stu-id="f0f1a-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="f0f1a-161">갤럭시 익스플로러 2.0</span><span class="sxs-lookup"><span data-stu-id="f0f1a-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)