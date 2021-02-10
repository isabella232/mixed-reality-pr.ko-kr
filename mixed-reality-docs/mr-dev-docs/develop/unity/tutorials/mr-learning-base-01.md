---
title: MRTK 자습서 소개
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 처음부터 혼합 현실 애플리케이션을 만드는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, solvers, 시선 추적, 음성 명령
ms.localizationpriority: high
ms.openlocfilehash: 8bae8b821e7ffe67b745bbbab763193612a58485
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590415"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="8a8b0-104">1. MRTK 자습서 소개</span><span class="sxs-lookup"><span data-stu-id="8a8b0-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="8a8b0-105">초보자를 위한 자습서 시리즈를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8a8b0-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="8a8b0-106">이러한 자습서의 과정을 통해 MRTK(Mixed Reality Toolkit) 및 제공해야 하는 기능 중 일부에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="8a8b0-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="8a8b0-107">또한 사용자가 NASA의 Mars Curiosity Rover 이후에 모델링된 홀로그램을 탐색할 수 있는 혼합 현실 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="8a8b0-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="8a8b0-108">이 시리즈의 끝 부분에서는 MRTK를 이해하고 개발 프로세스의 속도를 높이는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="8a8b0-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="8a8b0-109">이 시리즈의 자습서는 순차적이므로 올바른 순서로 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="8a8b0-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="8a8b0-110">[소개](mr-learning-base-01.md)(이미 여기에 있음)</span><span class="sxs-lookup"><span data-stu-id="8a8b0-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="8a8b0-111">프로젝트 초기화 및 첫 번째 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="8a8b0-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="8a8b0-112">MRTK 프로필 구성</span><span class="sxs-lookup"><span data-stu-id="8a8b0-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="8a8b0-113">장면에서 개체 위치 지정</span><span class="sxs-lookup"><span data-stu-id="8a8b0-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="8a8b0-114">해결기를 사용하여 동적 콘텐츠 만들기</span><span class="sxs-lookup"><span data-stu-id="8a8b0-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="8a8b0-115">사용자 인터페이스 만들기</span><span class="sxs-lookup"><span data-stu-id="8a8b0-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="8a8b0-116">3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="8a8b0-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="8a8b0-117">시선 추적 사용</span><span class="sxs-lookup"><span data-stu-id="8a8b0-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="8a8b0-118">음성 명령 사용</span><span class="sxs-lookup"><span data-stu-id="8a8b0-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="8a8b0-119">목표</span><span class="sxs-lookup"><span data-stu-id="8a8b0-119">Objectives</span></span>

* <span data-ttu-id="8a8b0-120">MRTK에 대한 Unity를 구성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="8a8b0-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="8a8b0-121">빌드하고 디바이스에 배포하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="8a8b0-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="8a8b0-122">MRTK의 주요 기능 중 일부를 사용하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="8a8b0-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="8a8b0-123">완전한 혼합 현실 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="8a8b0-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a8b0-124">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="8a8b0-124">Prerequisites</span></span>

* <span data-ttu-id="8a8b0-125">올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="8a8b0-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="8a8b0-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="8a8b0-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="8a8b0-127">[개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="8a8b0-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>

* <span data-ttu-id="8a8b0-128">Unity 2019 LTS가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="8a8b0-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="8a8b0-129">이 자습서 시리즈에 추천되는 MRTK 버전은 MRTK 2.5.3입니다.</span><span class="sxs-lookup"><span data-stu-id="8a8b0-129">The recommended MRTK version for this tutorial series is MRTK 2.5.3.</span></span>

> [!CAUTION]
> <span data-ttu-id="8a8b0-130">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019 LTS입니다.</span><span class="sxs-lookup"><span data-stu-id="8a8b0-130">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="8a8b0-131">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="8a8b0-131">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8a8b0-132">다음 자습서: 2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="8a8b0-132">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
