---
title: 아키텍처 개요
description: MRTK의 아키텍처 개요입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk 아키텍처,
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281919"
---
# <a name="architecture-overview"></a><span data-ttu-id="e2c47-104">아키텍처 개요</span><span class="sxs-lookup"><span data-stu-id="e2c47-104">Architecture overview</span></span>

<span data-ttu-id="e2c47-105">MRTK의 내용에 대 한 전반적인 소개를 위해이 문서에 포함 된 아키텍처 정보는 다음을 이해 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-105">For an overall introduction to the contents of MRTK, the architecture information contained in this document will help you understand the following:</span></span>

- <span data-ttu-id="e2c47-106">MRTK의 많은 부분과 연결 방법</span><span class="sxs-lookup"><span data-stu-id="e2c47-106">Large pieces of MRTK and how they connect</span></span>
- <span data-ttu-id="e2c47-107">MRTK가 소개 하는 개념은 바닐라 Unity에 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-107">Concepts that MRTK introduces which may not exist in vanilla Unity</span></span>
- <span data-ttu-id="e2c47-108">더 큰 시스템 (예: 입력)의 일부는 어떻게 작동 합니까?</span><span class="sxs-lookup"><span data-stu-id="e2c47-108">How some of the larger systems (such as Input) work</span></span>

<span data-ttu-id="e2c47-109">이 섹션은 작업을 수행 하는 방법을 설명 하기 위한 것이 아니라 이러한 작업을 구성 하는 방법 및 이유를 설명 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-109">This section isn't intended to teach you how to do tasks, but rather how such tasks are structured and why.</span></span>

## <a name="many-audiences-one-toolkit"></a><span data-ttu-id="e2c47-110">여러 대상 그룹, 도구 키트 하나</span><span class="sxs-lookup"><span data-stu-id="e2c47-110">Many audiences, one toolkit</span></span>

<span data-ttu-id="e2c47-111">MRTK에는 단일 단일 대상이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-111">MRTK doesn't have a single, uniform audience.</span></span> <span data-ttu-id="e2c47-112">해커 톤 행사는 처음부터 엔터프라이즈에 대 한 복잡 하 고 공유 된 환경을 구축 하는 개인에 이르는 사용 사례를 지원 하기 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-112">It's been written to support use cases ranging from first time hackathons, to individuals building complex, shared experiences for enterprise.</span></span> <span data-ttu-id="e2c47-113">일부 코드 및 Api는 다른 하나 이상에 대해 최적화 된 것으로 작성 되었을 수 있습니다. 즉, MRTK의 일부는 "한 번 클릭 구성"에 대해 최적화 된 것 처럼 보이지만 기록 및 높아지면 이유 중 일부는 더 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-113">Some code and APIs may have been written that are optimized for one more than the other (i.e. some parts of the MRTK seem more optimized for "one click configure"), but it's important to note that some of those are more for historical and resourcing reasons.</span></span> <span data-ttu-id="e2c47-114">MRTK가 진화 함에 따라 작성 되는 기능은 사용 사례의 범위를 지원 하도록 크기를 조정 하도록 설계 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-114">As MRTK evolves, the features that get built should be designed to scale to support the range of use cases.</span></span>

<span data-ttu-id="e2c47-115">MRTK에는 VR 및 AR 환경에서 원활 하 게 확장할 수 있는 요구 사항도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-115">MRTK also has requirements to gracefully scale across VR and AR experiences.</span></span> <span data-ttu-id="e2c47-116">HoloLens 2 또는 HoloLens 1에 배포 될 때 동작을 정상적으로 대체 하는 응용 프로그램을 쉽게 빌드할 수 있어야 합니다. openvr 및 WMR (및 기타 플랫폼)를 대상으로 하는 응용 프로그램을 빌드하는 것이 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-116">It should be easy to build applications that gracefully fallback in behavior when deployed on a HoloLens 2 OR a HoloLens 1, and it should be simple to build applications that target OpenVR and WMR (and other platforms).</span></span> <span data-ttu-id="e2c47-117">팀이 특정 시스템이 나 플랫폼에서 특정 반복에 집중할 수 있는 반면 장기적 목표는 사용자가 혼합 된 현실 환경을 구축할 때마다 광범위 한 지원을 구축 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-117">While at times the team may focus a particular iteration on a specific system or platform, the long term goal is to build a wide range of support for wherever people are building mixed reality experiences.</span></span>

## <a name="high-level-breakdown"></a><span data-ttu-id="e2c47-118">높은 수준의 분석</span><span class="sxs-lookup"><span data-stu-id="e2c47-118">High level breakdown</span></span>

<span data-ttu-id="e2c47-119">MRTK는 완전히 빠른 사용자 경험을 위한 도구 모음입니다. 또한 자체 런타임에 대 한 의견이 있는 응용 프로그램 프레임 워크, 확장 방법 및 구성 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-119">The MRTK is both a collection of tools for getting mixed reality (MR) experiences off the ground quickly, and also an application framework with opinions on its own runtime, how it should be extended, and how it should be configured.</span></span>

<span data-ttu-id="e2c47-120">상위 수준에서 MRTK는 다음과 같은 방법으로 세분화 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-120">At a high level, the MRTK can be broken down in the following ways:</span></span>

![아키텍처 개요 다이어그램](../features/images/architecture/MRTK_Architecture.png)

<span data-ttu-id="e2c47-122">MRTK에는 MRTK의 나머지 부분에 대 한 종속성이 거의 없는 또 다른 (빌드 도구, solvers, 오디오 영향 요인, 다듬기 유틸리티 및 선 렌더러) 집합도 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-122">The MRTK also contains another set of grab-bag utilities that have little to no dependencies on the rest of the MRTK (to list a few: build tools, solvers, audio influencers, smoothing utilities, and line renderers)</span></span>

<span data-ttu-id="e2c47-123">아키텍처 설명서의 나머지 부분에서는 프레임 워크 및 런타임에서 시작 하 여 입력과 같이 더 흥미롭고 복잡 한 시스템으로 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2c47-123">The remainder of the architecture documentation will build bottom up, starting from the framework and runtime, progressing to more interesting and complex systems, such as input.</span></span> <span data-ttu-id="e2c47-124">아키텍처 개요를 계속 진행 하려면 목차를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e2c47-124">Please see the table of contents to continue with the architectural overview.</span></span>
