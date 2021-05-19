---
title: 자산 교환 유틸리티
description: Unity 용 MRTK에서 asset swap 유틸리티를 사용 하는 방법에 대 한 설명서입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: c277cadffb356b93ffc359233b0b8307f43e8d57
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144129"
---
# <a name="asset-swap-utility"></a><span data-ttu-id="03510-104">자산 교환 유틸리티</span><span class="sxs-lookup"><span data-stu-id="03510-104">Asset swap utility</span></span>

<span data-ttu-id="03510-105">찾기 및 바꾸기는 텍스트 및 콘텐츠 생성 도구에서 작업할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="03510-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="03510-106">Unity 장면 내에서 많은 자산을 교환 해야 하는 경우이는 [Assetswaputility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) 인 [tabletableobject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 및 editor가 손 모양으로 할 수 있는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="03510-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="03510-107">유틸리티는 패키지에 포함 되어 `Microsoft.MixedReality.Toolkit.Unity.Tools` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03510-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="03510-108">은 `AssetSwapUtility` 모든 찾기 및 바꾸기 작업을 Tritableobject로 저장 하 여 앞뒤로 교환 하거나 나중에 사용할 수 있도록 스왑 "테마"를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="03510-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="03510-109">자산 교환</span><span class="sxs-lookup"><span data-stu-id="03510-109">Swapping assets</span></span>

<span data-ttu-id="03510-110">을 만들면 자산을 쉽게 교체할 수 있습니다 `AssetSwapCollection` .</span><span class="sxs-lookup"><span data-stu-id="03510-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="03510-111">장면에서 두 개의 파란 구를 사용 하 여 두 개의 빨간색 큐브를 바꿔 사용 하는 방법을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="03510-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="03510-112">먼저 기본 Unity 큐브와 재질을 사용 하는 두 개의 빨간색 큐브를 장면에 추가 `MRTK_Standard_Red` 합니다.</span><span class="sxs-lookup"><span data-stu-id="03510-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="03510-113">`AssetSwapCollection`을 만들려면 **혼합 현실 도구 키트 > 유틸리티로 이동 하 여 자산 교환 컬렉션 만들기를 >** 합니다.</span><span class="sxs-lookup"><span data-stu-id="03510-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="03510-114">선택한을 사용 하 여 `AssetSwapCollection` 아래 이미지에 표시 된 대로 속성을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="03510-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Unity 편집기의 자산 교환 컬렉션](images/asset-swap-img-01.png)

<span data-ttu-id="03510-116">그런 다음 "선택한 테마" 드롭다운에서 "파란색 구"를 선택 하 고 "적용"을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="03510-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="03510-117">장면 내의 모든 빨간색 큐브는 파란색 구로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03510-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![선택한 테마가 강조 표시 된 Unity 편집기의 자산 교환 컬렉션](images/asset-swap-img-02.png)

<span data-ttu-id="03510-119">이 예제에서는 전체 장면 바꾸기를 수행 했지만 "선택 모드"를 변경 하 여 장면의 일부를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03510-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="03510-120">"선택한 테마" 드롭다운에서 "Red 큐브"를 선택 하 고 "적용"을 다시 선택 하 여 빨간색 큐브로 다시 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03510-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="03510-121">오디오 파일, 글꼴, 프리팹 등과 같은 자산 형식을 교환할 수 있습니다. `AssetSwapUtility` 는 몇 가지 온전성 검사를 수행하여 유사한 형식으로 교환하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="03510-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>