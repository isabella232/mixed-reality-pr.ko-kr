---
title: 다중 사용자 기능 자습서 소개
description: 이 과정을 완료하여 HoloLens 2 애플리케이션에서 공유된 다중 사용자 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, 다중 사용자 기능, Photon, MRTK, mixed reality toolkit, UWP, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: c18bd7c10ed042278053a51c2d1894564000dfe2
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699022"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a><span data-ttu-id="c3a1b-104">1. 다중 사용자 기능 자습서 소개</span><span class="sxs-lookup"><span data-stu-id="c3a1b-104">1. Introduction to the Multi-user capabilities tutorials</span></span>

<span data-ttu-id="c3a1b-105">다중 사용자 기능 자습서를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a1b-105">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="c3a1b-106">이 자습서 시리즈를 통해 <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity 네트워킹</a>(PUN)을 사용하여 다중 사용자 환경을 구축하는 기본 사항을 배우게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3a1b-106">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="c3a1b-107">PUN은 혼합 현실 개발자가 공유 환경을 만드는 데 사용할 수 있는 몇 가지 네트워킹 옵션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="c3a1b-107">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="c3a1b-108">이 시리즈의 자습서:</span><span class="sxs-lookup"><span data-stu-id="c3a1b-108">Tutorials in this series:</span></span>

* [<span data-ttu-id="c3a1b-109">Photon Unity 네트워킹 설정</span><span class="sxs-lookup"><span data-stu-id="c3a1b-109">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="c3a1b-110">여러 사용자 연결</span><span class="sxs-lookup"><span data-stu-id="c3a1b-110">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="c3a1b-111">여러 사용자와 개체 움직임 공유</span><span class="sxs-lookup"><span data-stu-id="c3a1b-111">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="c3a1b-112">공유 환경에 Azure Spatial Anchors 통합</span><span class="sxs-lookup"><span data-stu-id="c3a1b-112">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="c3a1b-113">목표</span><span class="sxs-lookup"><span data-stu-id="c3a1b-113">Objectives</span></span>

* <span data-ttu-id="c3a1b-114">PUN 앱을 만들고 Unity 프로젝트를 연결하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="c3a1b-114">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="c3a1b-115">공유 환경에서 여러 사용자를 연결하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="c3a1b-115">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="c3a1b-116">개체 이동을 다른 사용자와 공유하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="c3a1b-116">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="c3a1b-117">여러 디바이스 간의 공간 맞춤을 구현하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="c3a1b-117">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3a1b-118">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c3a1b-118">Prerequisites</span></span>

* <span data-ttu-id="c3a1b-119">올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="c3a1b-119">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="c3a1b-120">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="c3a1b-120">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="c3a1b-121">[개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="c3a1b-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="c3a1b-122">Unity 2019 LTS가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="c3a1b-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="c3a1b-123">다음 자습서의 [Spatial Anchors 리소스 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션을 완료했습니다. [빠른 시작: Azure Spatial Anchors를 사용하는 Unity HoloLens 앱 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서)을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a1b-123">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="c3a1b-124">[시작 자습서](mr-learning-base-01.md) 시리즈 또는 Unity 및 MRTK를 사용하는 몇 가지 기본 사전 경험을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a1b-124">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="c3a1b-125">Azure Spatial Anchors 계정을 만드는 [Azure Spatial Anchors 자습서](mr-learning-asa-01.md) 시리즈 또는 이전 환경을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a1b-125">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="c3a1b-126">Android 및 HoloLens에 배포하려는 경우</span><span class="sxs-lookup"><span data-stu-id="c3a1b-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="c3a1b-127">Windows 또는 macOS 컴퓨터에 USB 연결을 사용하는 <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">개발자 사용</a> 및 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 지원 가능</a> Android 디바이스</span><span class="sxs-lookup"><span data-stu-id="c3a1b-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="c3a1b-128">Unity 2019 LTS가 설치되고 Android 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="c3a1b-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Android Build Support module added</span></span>
* <span data-ttu-id="c3a1b-129">iOS 및 HoloLens에 배포하려는 경우</span><span class="sxs-lookup"><span data-stu-id="c3a1b-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="c3a1b-130">최신 버전의 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 및 <a href="https://cocoapods.org" target="_blank">CocoaPods</a>가 설치된 macOS 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="c3a1b-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="c3a1b-131">macOS 컴퓨터에 USB로 연결된 <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 호환</a> iOS 디바이스</span><span class="sxs-lookup"><span data-stu-id="c3a1b-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="c3a1b-132">Unity 2019 LTS가 설치되고 iOS 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="c3a1b-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="c3a1b-133">이 자습서 시리즈에 권장되는 Mixed Reality Toolkit 버전은 MRTK 2.5.1입니다.</span><span class="sxs-lookup"><span data-stu-id="c3a1b-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.5.1.</span></span>

> [!CAUTION]
> <span data-ttu-id="c3a1b-134">이 자습서 시리즈에 권장되는 Unity 버전은 Unity 2019 LTS입니다. 이 버전은 위의 링크에 연결된 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a1b-134">The recommended Unity version for this tutorial series is Unity 2019 LTS This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c3a1b-135">다음 자습서: 2. Photon Unity 네트워킹 설정</span><span class="sxs-lookup"><span data-stu-id="c3a1b-135">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
