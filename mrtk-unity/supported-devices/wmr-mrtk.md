---
title: Hololens 및 WMR 헤드셋에 배포
description: 다양한 디바이스에 앱을 빌드하고 배포하기 위한 설명서입니다.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Visual Studio
ms.openlocfilehash: 1547f0630d307e9e87505890adef4cad366d6c00
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441152"
---
# <a name="deploying-to-hololens-and-wmr-headsets"></a><span data-ttu-id="48e85-104">Hololens 및 WMR 헤드셋에 배포</span><span class="sxs-lookup"><span data-stu-id="48e85-104">Deploying to Hololens and WMR headsets</span></span>

<span data-ttu-id="48e85-105">MRTK를 사용 하 여 빌드된 응용 프로그램을 windows 장치, UWP (유니버설 Windows Platform) 및 독립 실행형 플랫폼에 배포 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-105">There are two ways to deploy applications built with MRTK to your windows device, the Univeral Windows Platform (UWP) and the Standalone Platform.</span></span> <span data-ttu-id="48e85-106">HoloLens 1 또는 HoloLens 2 용으로 빌드된 응용 프로그램은 UWP를 대상으로 해야 하지만 WMR 헤드셋 용으로 빌드된 응용 프로그램은 UWP 또는 독립 실행형을 대상으로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-106">Applications built for HoloLens 1 or HoloLens 2 must target UWP, while applications built for WMR headsets may target either UWP or Standalone.</span></span>

## <a name="building-and-deploying-mrtk-to-hololens-1-hololens-2-and-wmr-headsets-uwp"></a><span data-ttu-id="48e85-107">HoloLens 1, HoloLens 2 및 WMR 헤드셋 (UWP)으로 MRTK 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="48e85-107">Building and deploying MRTK to HoloLens 1, HoloLens 2 and WMR headsets (UWP)</span></span>

<span data-ttu-id="48e85-108">**Hololens 1** 및 **hololens** 를 빌드하는 방법에 대 한 지침은 [장치에 대 한 응용 프로그램](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device)빌드에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-108">Instructions on how to build and deploy for **HoloLens 1** and **HoloLens 2** (UWP) can be found at [building your application to device](/windows/mixed-reality/mrlearning-base-ch1#build-your-application-to-your-device).</span></span> <span data-ttu-id="48e85-109">이러한 단계를 통해 **WMR 헤드셋** 에 배포할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-109">These steps also allow you to deploy to **WMR headsets**.</span></span>

> [!NOTE]
> <span data-ttu-id="48e85-110">Visual Studio에서 장치에 응용 프로그램을 배포 하는 경우 장치에 따라 Visual Studio를 약간 다르게 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-110">When deploying your application to your device in Visual Studio, you need to configure Visual Studio slightly differently depending on the device.</span></span> <span data-ttu-id="48e85-111">구성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-111">The configurations are as follows</span></span>
>
>| <span data-ttu-id="48e85-112">플랫폼</span><span class="sxs-lookup"><span data-stu-id="48e85-112">Platform</span></span> | <span data-ttu-id="48e85-113">Configuration</span><span class="sxs-lookup"><span data-stu-id="48e85-113">Configuration</span></span> | <span data-ttu-id="48e85-114">아키텍처</span><span class="sxs-lookup"><span data-stu-id="48e85-114">Architecture</span></span> | <span data-ttu-id="48e85-115">대상</span><span class="sxs-lookup"><span data-stu-id="48e85-115">Target</span></span> |
|---|---|---|---|
| <span data-ttu-id="48e85-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="48e85-116">HoloLens 2</span></span> | <span data-ttu-id="48e85-117">릴리스 또는 마스터</span><span class="sxs-lookup"><span data-stu-id="48e85-117">Release or Master</span></span> | <span data-ttu-id="48e85-118">ARM64</span><span class="sxs-lookup"><span data-stu-id="48e85-118">ARM64</span></span> | <span data-ttu-id="48e85-119">디바이스</span><span class="sxs-lookup"><span data-stu-id="48e85-119">Device</span></span> |
| <span data-ttu-id="48e85-120">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="48e85-120">HoloLens 1</span></span> | <span data-ttu-id="48e85-121">릴리스 또는 마스터</span><span class="sxs-lookup"><span data-stu-id="48e85-121">Release or Master</span></span> | <span data-ttu-id="48e85-122">x86</span><span class="sxs-lookup"><span data-stu-id="48e85-122">x86</span></span> | <span data-ttu-id="48e85-123">디바이스</span><span class="sxs-lookup"><span data-stu-id="48e85-123">Device</span></span> |
| <span data-ttu-id="48e85-124">WMR 헤드셋</span><span class="sxs-lookup"><span data-stu-id="48e85-124">WMR Headsets</span></span> | <span data-ttu-id="48e85-125">릴리스 또는 마스터</span><span class="sxs-lookup"><span data-stu-id="48e85-125">Release or Master</span></span> | <span data-ttu-id="48e85-126">X64</span><span class="sxs-lookup"><span data-stu-id="48e85-126">x64</span></span> | <span data-ttu-id="48e85-127">로컬 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="48e85-127">Local Machine</span></span> |

<span data-ttu-id="48e85-128">**팁:** HoloLens 1, HoloLens 2 또는 WMR에 대해 빌드할 때 빌드 설정 "대상 SDK 버전" 및 "최소 플랫폼 버전"은 아래 그림에 나와 있는 것 처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-128">**Tip:** When building for HoloLens 1, HoloLens 2, or WMR, it is recommended that the build settings "Target SDK Version" and "Minimum Platform Version" look like they do in the picture below:</span></span>

![빌드 창](../features/images/getting-started/BuildWindow.png)

<span data-ttu-id="48e85-130">기타 설정은 다를 수 있습니다(예를 들어, 빌드 구성/아키텍처/빌드 유형 및 다른 설정은 Visual Studio 솔루션 내에서 항상 변경할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="48e85-130">The other settings can be different (for example, Build Configuration/Architecture/Build Type and others can always be changed inside the Visual Studio solution).</span></span>

<span data-ttu-id="48e85-131">"대상 SDK 버전" 드롭다운에 "10.0.18362.0" 옵션이 포함되어 있는지 확인합니다. 이 항목이 없으면 [최신 Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-131">Make sure that the "Target SDK Version" dropdown includes the option "10.0.18362.0" - if this is missing, [the latest Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) needs to be installed.</span></span>

### <a name="unity-20193-and-hololens"></a><span data-ttu-id="48e85-132">Unity 2019.3 및 HoloLens</span><span class="sxs-lookup"><span data-stu-id="48e85-132">Unity 2019.3 and HoloLens</span></span>

<span data-ttu-id="48e85-133">HoloLens 앱이 디바이스에서 2D 패널로 표시되는 경우 UWP 앱을 배포하기 전에 Unity 2019.3.x에서 다음 설정이 구성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-133">If a HoloLens app appears as a 2D panel on device, make sure the following settings have been configured in Unity 2019.3.x before deploying your UWP app:</span></span>

<span data-ttu-id="48e85-134">레거시 XR을 사용하는 경우:</span><span class="sxs-lookup"><span data-stu-id="48e85-134">If using the legacy XR:</span></span>

1. <span data-ttu-id="48e85-135">편집 > 프로젝트 설정, 플레이어로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-135">Navigate to Edit > Project Settings, Player</span></span>
1. <span data-ttu-id="48e85-136">UWP 탭의 **XR 설정** 에서 **가상 현실 지원** 이 활성화되어 있고 **Windows Mixed Reality** SDK가 SDK에 추가되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-136">Under **XR Settings** in the UWP tab, make sure **Virtual Reality Supported** is enabled and the **Windows Mixed Reality** SDK has been added to SDKs.</span></span>
1. <span data-ttu-id="48e85-137">Visual Studio에서 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="48e85-137">Build and deploy in Visual Studio</span></span>

<span data-ttu-id="48e85-138">XR-Plugin을 사용하는 경우:</span><span class="sxs-lookup"><span data-stu-id="48e85-138">If using the XR-Plugin:</span></span>

1. <span data-ttu-id="48e85-139">[XRSDK 시작](../configuration/getting-started-with-mrtk-and-xrsdk.md)에 있는 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-139">Follow the steps found in [Getting Started with XRSDK](../configuration/getting-started-with-mrtk-and-xrsdk.md)</span></span>
1. <span data-ttu-id="48e85-140">구성 프로필이 **DefaultXRSDKConfigurationProfile** 인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-140">Make sure the configuration profile is the **DefaultXRSDKConfigurationProfile**</span></span>
1. <span data-ttu-id="48e85-141">**편집 > 프로젝트 설정, XR-Plugin 관리** 로 이동하여 **Windows Mixed Reality** 를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-141">Navigate to **Edit > Project Settings, XR-Plugin Management** and make sure **Windows Mixed Reality** is enabled.</span></span>
1. <span data-ttu-id="48e85-142">Visual Studio에서 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="48e85-142">Build and deploy in Visual Studio</span></span>

>[!IMPORTANT]
> <span data-ttu-id="48e85-143">Unity 2019.3.x를 사용하는 경우 Visual Studio의 빌드 아키텍처로 **ARM64** 를 선택하고 **ARM** 은 선택하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-143">If using Unity 2019.3.x, select **ARM64** and not **ARM** as the build architecture in Visual Studio.</span></span> <span data-ttu-id="48e85-144">Unity 2019.3.x의 기본 Unity 설정을 사용하면 Unity 버그로 인해 ARM이 선택된 경우 Unity 앱은 HoloLens에 배포하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-144">With the default Unity settings in Unity 2019.3.x, a Unity app will not deploy to a HoloLens if ARM is selected due to a Unity bug.</span></span> <span data-ttu-id="48e85-145">이는 [Unity의 문제 추적기](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)에서 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-145">This can be tracked on [Unity's issue tracker](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2).</span></span>
>
> <span data-ttu-id="48e85-146">ARM 아키텍처가 필요한 경우 **편집 > 프로젝트 설정, 플레이어** 로 이동하고 **기타 설정** 메뉴에서 **그래픽 작업** 을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-146">If the ARM architecture is required, navigate to **Edit > Project Settings, Player**, and under the **Other Settings** menu disable **Graphics Jobs**.</span></span> <span data-ttu-id="48e85-147">**그래픽 작업** 을 사용하지 않도록 설정하면 앱이 Unity 2019.3.x용 ARM 빌드 아키텍처를 사용하여 배포할 수는 있지만 ARM64가 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-147">Disabling **Graphics Jobs** will allow the app to deploy using the ARM build architecture for Unity 2019.3.x, but ARM64 is recommended.</span></span>

## <a name="building-and-deploying-mrtk-to-wmr-headsets-standalone"></a><span data-ttu-id="48e85-148">WMR 헤드셋에 MRTK 빌드 및 배포 (독립 실행형)</span><span class="sxs-lookup"><span data-stu-id="48e85-148">Building and deploying MRTK to WMR Headsets (Standalone)</span></span>

<span data-ttu-id="48e85-149">WMR 헤드셋에서 MRTK의 독립 실행형 빌드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-149">Standalone builds of MRTK can be used on WMR headsets.</span></span> <span data-ttu-id="48e85-150">WMR 헤드셋에 대한 독립 실행형 빌드를 사용하려면 다음과 같은 추가 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-150">A Standalone build for a WMR headset requires the following extra steps:</span></span>

> [!NOTE]
> <span data-ttu-id="48e85-151">Unity의 XR SDK는 또한 독립 실행형 빌드에서 기본 WMR을 지원하지만 SteamVR 또는 WMR 플러그인은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-151">Unity's XR SDK also supports native WMR in Standalone builds, but does not require SteamVR or WMR plugin.</span></span> <span data-ttu-id="48e85-152">이러한 단계는 Unity의 레거시 XR에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-152">These steps are required for Unity's legacy XR.</span></span>

1. <span data-ttu-id="48e85-153">[Steam](https://store.steampowered.com/about/)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-153">Install [Steam](https://store.steampowered.com/about/)</span></span>
1. <span data-ttu-id="48e85-154">[SteamVR](https://store.steampowered.com/app/250820/SteamVR/)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-154">Install [SteamVR](https://store.steampowered.com/app/250820/SteamVR/)</span></span>
1. <span data-ttu-id="48e85-155">[WMR 플러그 인](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-155">Install the [WMR Plugin](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)</span></span>

### <a name="how-to-use-wmr-plugin"></a><span data-ttu-id="48e85-156">WMR 플러그 인을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="48e85-156">How to use WMR plugin</span></span>

1. <span data-ttu-id="48e85-157">Steam를 열고 Windows Mixed Reality 플러그 인을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-157">Open Steam and search for the Windows Mixed Reality Plugin</span></span>
    - <span data-ttu-id="48e85-158">WMR 플러그 인을 시작하기 전에 SteamVR이 닫혀 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-158">Make sure SteamVR is closed before launching the WMR Plugin.</span></span> <span data-ttu-id="48e85-159">WMR 플러그 인을 시작하면 SteamVR도 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-159">Launching the WMR plugin also launches SteamVR.</span></span>
    - <span data-ttu-id="48e85-160">WMR 헤드셋이 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-160">Make sure the WMR headset is plugged in.</span></span>

    ![WMR 플러그 인 검색](../features/images/build-deploy/WMR/SteamSearchWMRPlugin.png)

1. <span data-ttu-id="48e85-162">SteamVR 플러그 인용 Windows Mixed Reality의 경우 **시작** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-162">Select **Launch** for the Windows Mixed Reality for SteamVR Plugin.</span></span>

    ![WMR 플러그 인](../features/images/build-deploy/WMR/WMRPlugin.png)

    - <span data-ttu-id="48e85-164">SteamVR 및 WMR 플러그 인이 시작되고 WMR 헤드셋에 대한 새 추적 상태 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-164">SteamVR and the WMR plugin will launch and a new tracking status window for the WMR headset will appear.</span></span>
    - <span data-ttu-id="48e85-165">자세한 내용은 [Windows Mixed Reality Steam 설명서](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="48e85-165">For more information visit the [Windows Mixed Reality Steam Documentation](https://support.microsoft.com/help/4053622/windows-10-play-steamvr-games-in-windows-mixed-reality)</span></span>

        ![WMR 시작 모양](../features/images/build-deploy/WMR/WMRPluginActive.png)

1. <span data-ttu-id="48e85-167">Unity에서 MRTK 장면이 열린 상태에서 **파일 > 빌드 설정** 으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-167">In Unity, with your MRTK scene open, navigate to **File > Build Settings**</span></span>

1. <span data-ttu-id="48e85-168">장면 빌드</span><span class="sxs-lookup"><span data-stu-id="48e85-168">Build the scene</span></span>
    - <span data-ttu-id="48e85-169">**열린 장면 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-169">Select **Add Open Scene**</span></span>
    - <span data-ttu-id="48e85-170">플랫폼이 **독립 실행형** 인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-170">Make sure the Platform is **Standalone**</span></span>
    - <span data-ttu-id="48e85-171">**빌드** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-171">Select **Build**</span></span>
    - <span data-ttu-id="48e85-172">파일 탐색기에서 새 빌드의 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-172">Choose the location for the new build in File Explorer</span></span>

    ![독립 실행형에 대한 빌드 설정](../features/images/build-deploy/WMR/BuildSettingsStandaloneUnity.png)

1. <span data-ttu-id="48e85-174">새 Unity 실행 파일이 생성되며, 앱을 시작하려면 파일 탐색기에서 Unity 실행 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="48e85-174">A new Unity executable will be created, to launch your app select the Unity executable in File Explorer.</span></span>

    ![파일 탐색기 Unity](../features/images/build-deploy/WMR/FileExplorerUnityExe.png)

## <a name="see-also"></a><span data-ttu-id="48e85-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="48e85-176">See also</span></span>

- [<span data-ttu-id="48e85-177">Android 및 iOS 지원</span><span class="sxs-lookup"><span data-stu-id="48e85-177">Android and iOS Support</span></span>](using-ar-foundation.md)
- [<span data-ttu-id="48e85-178">Leap Motion 지원</span><span class="sxs-lookup"><span data-stu-id="48e85-178">Leap Motion Support</span></span>](leap-motion-mrtk.md)
- [<span data-ttu-id="48e85-179">플랫폼 기능 검색</span><span class="sxs-lookup"><span data-stu-id="48e85-179">Detecting Platform Capabilities</span></span>](detecting-platform-capabilities.md)