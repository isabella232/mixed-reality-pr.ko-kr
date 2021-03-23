---
title: MRTK for Unreal 소개
description: Mixed Reality Toolkit for Unreal이 새로운 혼합 현실 개발자에게 제공하는 모든 기능을 시작하세요.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 테스트, Mixed Reality Toolkit, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 플랫폼 간
ms.openlocfilehash: 4aa21cbee75c4c362abfd609add922ad9c922682
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584832"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="4db49-104">MRTK for Unreal 소개</span><span class="sxs-lookup"><span data-stu-id="4db49-104">Introducing MRTK for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="4db49-106">MRTK(Mixed Reality Toolkit)란?</span><span class="sxs-lookup"><span data-stu-id="4db49-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="4db49-107">MRTK는 HoloLens가 처음 릴리스된 이후부터 사용되어 온 놀라운 오픈 소스 도구 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="4db49-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="4db49-108">기여 개발자 커뮤니티의 노력이 없었다면 오늘날의 도구 키트가 될 수 없었을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4db49-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="4db49-109">MRTK-Unreal(Mixed Reality Toolkit for Unreal)은 플러그 인, 샘플 및 설명서의 형태로 구성된 구성 요소 세트로, Unreal Engine을 사용하여 혼합 현실 애플리케이션의 개발을 지원하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4db49-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="4db49-110">현재 이 도구 키트는 다음과 같은 요소로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4db49-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="4db49-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) - Hololens 2 애플리케이션용 UX 기능 구현을 위한 코드, 청사진 및 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4db49-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="4db49-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal) - 성능 예산에 맞추면서 혼합 현실 애플리케이션의 시각적 충실도를 개선하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4db49-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="4db49-113">[GitHub의 MRTK 설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)를 살펴보고 [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) 또는 [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) 설치 가이드를 시작하세요.</span><span class="sxs-lookup"><span data-stu-id="4db49-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="4db49-114">모듈식</span><span class="sxs-lookup"><span data-stu-id="4db49-114">Modular</span></span>

<span data-ttu-id="4db49-115">모듈식으로 MRTK Unreal을 빌드했으므로 도구 키트의 모든 비트를 프로젝트에 적용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4db49-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="4db49-116">필요한 플러그 인을 선택하고 적절하다고 생각할 때마다 추가하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4db49-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="4db49-117">이 방법을 통해 더 쉽게 프로젝트 크기를 더 작게 유지하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4db49-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="4db49-118">성능 기준에 적합</span><span class="sxs-lookup"><span data-stu-id="4db49-118">Performant</span></span>

<span data-ttu-id="4db49-119">모바일 플랫폼을 사용하는 경우 성능을 고려하여 MRTK Unreal을 구축했습니다.</span><span class="sxs-lookup"><span data-stu-id="4db49-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="4db49-120">이는 매우 중요하며, 도구가 사용자에게 불리하게 작동하지 않도록 하려 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4db49-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="4db49-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4db49-121">See also</span></span>

* [<span data-ttu-id="4db49-122">도구 설치</span><span class="sxs-lookup"><span data-stu-id="4db49-122">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="4db49-123">MRTK for Unreal을 사용한 개발</span><span class="sxs-lookup"><span data-stu-id="4db49-123">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="4db49-124">UX Tools - 설치 가이드(GitHub)</span><span class="sxs-lookup"><span data-stu-id="4db49-124">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="4db49-125">UX Tools - 설명서 홈(GitHub)</span><span class="sxs-lookup"><span data-stu-id="4db49-125">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="4db49-126">Graphics Tools - 설치 가이드(GitHub)</span><span class="sxs-lookup"><span data-stu-id="4db49-126">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="4db49-127">Graphics Tools - 설명서 홈(GitHub)</span><span class="sxs-lookup"><span data-stu-id="4db49-127">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)