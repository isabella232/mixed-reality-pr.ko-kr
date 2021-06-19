---
title: 개발자 파이프라인 선택
description: HoloLens 응용 프로그램 개발에 대 한 최신 Unity development development 파이프라인 권장 사항을 최신 상태로 유지 합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394557"
---
# <a name="choosing-your-developer-pipeline"></a><span data-ttu-id="a9dbf-104">개발자 파이프라인 선택</span><span class="sxs-lookup"><span data-stu-id="a9dbf-104">Choosing your developer pipeline</span></span>

![Unity 로고 배너](../images/unity_logo_banner.png)<br>

<span data-ttu-id="a9dbf-106">현재 **Unity 2019.4 LTS를 설치 하 고 혼합 현실 개발용으로 레거시 기본 제공 XR를 사용 하는 것이 좋습니다** . 다른 Unity 구성으로 앱을 빌드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-106">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="mixed-reality-toolkit-recommended"></a><span data-ttu-id="a9dbf-107">Mixed Reality Toolkit (권장)</span><span class="sxs-lookup"><span data-stu-id="a9dbf-107">Mixed Reality Toolkit (Recommended)</span></span>

<span data-ttu-id="a9dbf-108">Microsoft의 최신 권장 Unity 구성은 HoloLens 2에 대 한 혼합 현실 도구 키트 ...</span><span class="sxs-lookup"><span data-stu-id="a9dbf-108">Microsoft’s current recommended Unity configuration for HoloLens 2 is the Mixed Reality Toolkit...</span></span>

### <a name="install-the-mixed-reality-feature-tool"></a><span data-ttu-id="a9dbf-109">혼합 현실 기능 도구 설치</span><span class="sxs-lookup"><span data-stu-id="a9dbf-109">Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="a9dbf-110">[Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)은 개발자가 혼합형 현실 기능 패키지를 검색하고 Unity 프로젝트에 추가하는 데 사용되는 새로운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-110">The [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="a9dbf-111">이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-111">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="a9dbf-112">원하는 패키지의 유효성을 검사하면 Mixed Reality Feature Tool에서 사용자가 선택한 프로젝트로 해당 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-112">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a9dbf-113">Unity 용 Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="a9dbf-113">Importing the Mixed Reality Toolkit for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="a9dbf-115">MRTK([Mixed Reality Toolkit](mrtk-getting-started.md))는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-115">[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="a9dbf-116">[설치 및 사용 지침](welcome-to-mr-feature-tool.md#system-requirements)을 따르고 **Mixed Reality Toolkit Foundation** 패키지를 선택하여 Mixed Reality Toolkit 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-116">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="a9dbf-117">큐레이트된 [HoloLens](unity-development-overview.md#1-getting-started) 또는 [VR](unity-development-wmr-overview.md#1-getting-started) 개발 경험의 시작 섹션을 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-117">We recommend completing the getting started section in our curated [HoloLens](unity-development-overview.md#1-getting-started) or [VR](unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="a9dbf-118">HoloLens용 Unity 개발 경험을 이미 따르고 있는 경우 아래 나열된 나머지 설정 단계를 완료하고 [HoloLens 2 시작 자습서](tutorials/mr-learning-base-01.md)를 계속 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-118">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9dbf-119">설치 지침은 MRTK 및 Unity 릴리스의 안정적인 최신 조합인 **MRTK 2.6.1** 및 **Unity 2019.4 LTS** 를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-119">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.6.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="a9dbf-120">Unity에 MRTK를 사용하지 않으려면 [모든 상호 작용과 동작을 직접 스크립팅](configure-unity-project.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9dbf-120">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="a9dbf-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 배너](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="a9dbf-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="a9dbf-122">**Mixed Reality Toolkit-Unity(GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="a9dbf-122">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a><span data-ttu-id="a9dbf-123">수동</span><span class="sxs-lookup"><span data-stu-id="a9dbf-123">Manual</span></span> 

<span data-ttu-id="a9dbf-124">TBD ...</span><span class="sxs-lookup"><span data-stu-id="a9dbf-124">TBD...</span></span>