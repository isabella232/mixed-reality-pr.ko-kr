---
title: 자산 교환 유틸리티
description: Unity용 MRTK에서 자산 교환 유틸리티 사용에 대한 설명서입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 50ef252913575988b5f377dd9ff92f9e9ade3a72
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176160"
---
# <a name="asset-swap-utility"></a><span data-ttu-id="b86f0-104">자산 교환 유틸리티</span><span class="sxs-lookup"><span data-stu-id="b86f0-104">Asset swap utility</span></span>

<span data-ttu-id="b86f0-105">찾기 및 바꾸기는 텍스트 및 콘텐츠 만들기 도구에서 작업할 때 유비쿼터스입니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="b86f0-106">Unity 장면 내에서 많은 자산을 교환해야 하는 경우 [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject와](https://docs.unity3d.com/Manual/class-ScriptableObject.html) 편집기가 도움을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="b86f0-107">유틸리티는 패키지에 포함되어 `Microsoft.MixedReality.Toolkit.Unity.Tools` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="b86f0-108">는 `AssetSwapUtility` 모든 찾기 및 바꾸기 작업을 ScriptableObject로 저장하므로 나중에 사용할 수 있도록 앞뒤로 교환하거나 교환 "테마"를 저장하는 것이 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="b86f0-109">자산 교환</span><span class="sxs-lookup"><span data-stu-id="b86f0-109">Swapping assets</span></span>

<span data-ttu-id="b86f0-110">을 만든 후에는 자산을 쉽게 교환할 수 `AssetSwapCollection` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="b86f0-111">장면에서 두 개의 빨간색 큐브를 두 개의 파란색 구로 교환하여 사용하는 것을 보여 봅시다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="b86f0-112">먼저 기본 Unity 큐브와 재질을 사용하는 두 개의 빨간색 큐브를 장면에 `MRTK_Standard_Red` 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="b86f0-113">를 만들려면 `AssetSwapCollection` Mixed Reality Toolkit > 유틸리티 > Asset Swap Collection **만들기로** 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="b86f0-114">선택한 를 통해 `AssetSwapCollection` 아래 이미지와 같이 속성을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Unity 편집기에서 자산 교환 컬렉션](images/asset-swap-img-01.png)

<span data-ttu-id="b86f0-116">다음으로"선택한 테마" 드롭다운에서 "Blue Spheres"를 선택하고 "적용"을 적중합니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="b86f0-117">장면 내의 모든 빨간색 큐브는 파란색 구로 대체해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![선택한 테마가 강조 표시된 Unity 편집기에서 자산 교환 컬렉션](images/asset-swap-img-02.png)

<span data-ttu-id="b86f0-119">이 예제에서는 전체 장면 바꾸기를 수행했지만 "선택 모드"를 변경하여 장면의 일부를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="b86f0-120">"선택한 테마" 드롭다운에서 "빨간색 큐브"를 선택하고 "적용"을 다시 하여 빨간색 큐브로 다시 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="b86f0-121">오디오 파일, 글꼴, 프리팹 등과 같은 자산 형식을 교환할 수 있습니다. `AssetSwapUtility` 는 몇 가지 온전성 검사를 수행하여 유사한 형식으로 교환하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b86f0-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>
