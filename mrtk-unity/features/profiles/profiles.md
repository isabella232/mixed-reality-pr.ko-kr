---
title: 프로필
description: MRTK의 문서 프로필
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, Profiles,
ms.openlocfilehash: 384614f27c099af197ea8a9aedc72c711f0c099e
ms.sourcegitcommit: f74d33d50c1fbfebe8571695d631ce78dd599f74
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881230"
---
# <a name="profiles"></a><span data-ttu-id="41764-104">프로필</span><span class="sxs-lookup"><span data-stu-id="41764-104">Profiles</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

<span data-ttu-id="41764-105">MRTK가 구성되는 주요 방법 중 하나는 Foundation 패키지에서 사용할 수 있는 프로필을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="41764-105">One of the main ways that the MRTK is configured is through the profiles available in the foundation package.</span></span> <span data-ttu-id="41764-106">장면의 주 [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) 개체에는 액티브 프로필(ScriptableObject)이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="41764-106">The main [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object in a scene will have the active profile, which is a ScriptableObject.</span></span> <span data-ttu-id="41764-107">최상위 MRTK 구성 프로필에는 기본 코어 시스템의 각 코어에 대한 하위 프로필 데이터가 포함되어 있으며, 각각은 해당 하위 시스템의 동작을 구성하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41764-107">The top level MRTK Configuration Profile contains sub-profile data for each core of the primary core systems, each of which are designed to configure the behavior of their corresponding subsystems.</span></span> <span data-ttu-id="41764-108">또한 이러한 하위 프로필은 ScriptableObjects이며, 따라서 한 수준 아래의 다른 프로필 개체에 대한 참조를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41764-108">Furthermore, these sub-profiles are also ScriptableObjects and thus can contain references to other profile objects one level below them.</span></span> <span data-ttu-id="41764-109">기본적으로 MRTK 하위 시스템과 기능을 초기화하는 방법에 대한 구성 정보를 구성하는 연결된 프로필로 이루어진 전체 트리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41764-109">There is essentially an entire tree of connected profiles that make up the configuration information for how to initialize the MRTK subsystems and features.</span></span>

<span data-ttu-id="41764-110">예를 들어 입력 시스템의 동작은 `DefaultMixedRealityInputSystemProfile`(자산/MRTK/SDK/프로필)과 같은 입력 시스템 프로필에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="41764-110">For example, the input system's behavior is governed by an input system profile, like the `DefaultMixedRealityInputSystemProfile` (Assets/MRTK/SDK/Profiles).</span></span>

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<span data-ttu-id="41764-111"><sup>프로필 검사기</sup></span><span class="sxs-lookup"><span data-stu-id="41764-111"><sup>Profile Inspector</sup></span></span>

## <a name="background"></a><span data-ttu-id="41764-112">배경</span><span class="sxs-lookup"><span data-stu-id="41764-112">Background</span></span>

<span data-ttu-id="41764-113">프로필은 주로 데이터 공급자를 통해 처리되는 여러 디바이스에서 특정 시나리오를 지원하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="41764-113">Profiles are mainly intended to support specific scenarios across multiple devices, which are handled via the data providers.</span></span> <span data-ttu-id="41764-114">이런 식으로 앱은 가능한 한 디바이스에 구애받지 않고 설계할 수 있으며 MRTK 및 프로필의 데이터 공급자가 플랫폼 간 지원을 처리하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41764-114">This way, an app can be designed as device-agnosticly as possible and let the MRTK and the profile's data providers handle cross-platform support.</span></span>

<span data-ttu-id="41764-115">GGV 스타일 상호 작용을 기본으로 하는 HoloLens 1 프로필과 같은 특정 디바이스의 입력 기능을 중심으로 구축된 프로필도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41764-115">There are also profiles built around the input features of specific devices, such as the HoloLens 1 profile which defaults to GGV-style interactions.</span></span>

## <a name="xr-sdk"></a><span data-ttu-id="41764-116">XR SDK</span><span class="sxs-lookup"><span data-stu-id="41764-116">XR SDK</span></span>

<span data-ttu-id="41764-117">현재 XR SDK에 대해 두 개의 프로필(`DefaultXRSDKConfigurationProfile` 및 `DefaultHoloLens2XRSDKConfigurationProfile`)이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="41764-117">Currently, there are two profiles provided for XR SDK, `DefaultXRSDKConfigurationProfile` and `DefaultHoloLens2XRSDKConfigurationProfile`.</span></span> <span data-ttu-id="41764-118">따라서 장면 및 시나리오별 구성으로 인해 모든 샘플 장면이 완전히 지원되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="41764-118">As a result, not all samples scenes are fully supported due to scene- and scenario-specific configurations.</span></span> <span data-ttu-id="41764-119">`DefaultMixedRealityToolkitConfigurationProfile` 및 `DefaultHoloLens2ConfigurationProfile`을 사용하는 모든 샘플은 해당 XR SDK 프로필로 교환 _할 수 있습니다_.</span><span class="sxs-lookup"><span data-stu-id="41764-119">Any samples that use `DefaultMixedRealityToolkitConfigurationProfile` and `DefaultHoloLens2ConfigurationProfile` _can_ be swapped over to their corresponding XR SDK profiles.</span></span> <span data-ttu-id="41764-120">XR SDK와 함께 OpenXR을 사용하는 경우 `DefaultOpenXRConfigurationProfile`을 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="41764-120">If you're using OpenXR with XR SDK, use the `DefaultOpenXRConfigurationProfile` instead.</span></span>

<span data-ttu-id="41764-121">기존 XR 및 XR SDK를 나란히 구성할 수 있도록 구성을 쉽게 하고 모든 샘플 장면을 지원하기 위한 추가 작업이 진행되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41764-121">Additional work is being undertaken to ease configuration and support all sample scenes, allowing for both legacy XR and XR SDK to be configured side-by-side.</span></span> <span data-ttu-id="41764-122">추적은 문제 [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41764-122">See issue [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) for tracking.</span></span>

<span data-ttu-id="41764-123">레거시 XR 및 XR SDK 간의 프로필 변환에 대한 자세한 내용은 [XR SDK 파이프라인에 대한 MRTK 구성](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41764-123">See [Configuring MRTK for the XR SDK pipeline](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline) for more information on converting profiles between legacy XR and XR SDK.</span></span>

## <a name="default-profile"></a><span data-ttu-id="41764-124">기본 프로필</span><span class="sxs-lookup"><span data-stu-id="41764-124">Default profile</span></span>

<span data-ttu-id="41764-125">MRTK는 MRTK가 지원하는 대부분의 플랫폼과 시나리오를 포괄하는 기본 프로필 세트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="41764-125">The MRTK provides a set of default profiles which cover most platforms and scenarios that the MRTK supports.</span></span> <span data-ttu-id="41764-126">예를 들어 `DefaultMixedRealityToolkitConfigurationProfile`(자산/MRTK/SDK/프로필)을 선택하면 VR(OpenVR, WMR) 및 HoloLens(1 및 2)에서 시나리오를 시험해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41764-126">For example, when you select the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) you will be able to try out scenarios on VR (OpenVR, WMR) and HoloLens (1 and 2).</span></span>

<span data-ttu-id="41764-127">이 프로필은 일반 사용 프로필이기 때문에 특정 사용 사례에 최적화되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41764-127">Note that because this is a general use profile, it's not optimized for any particular use case.</span></span> <span data-ttu-id="41764-128">다른 플랫폼에서 더 나은 성능/특정 설정을 지정하려면, 각 플랫폼에서 더 나은 성능을 발휘하도록 약간 조정되어 있는 다른 프로필을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41764-128">If you want to have more performant/specific settings that are better on other platforms, see the other profiles below, which are slightly tweaked to be better on their respective platforms.</span></span>

## <a name="hololens-2-profile"></a><span data-ttu-id="41764-129">HoloLens 2 프로필</span><span class="sxs-lookup"><span data-stu-id="41764-129">HoloLens 2 profile</span></span>

<span data-ttu-id="41764-130">MRTK는 또한 HoloLens 2: `DefaultHoloLens2ConfigurationProfile`(자산/MRTK/SDK/프로필/HoloLens2)에서 배포 및 테스트에 최적화된 기본 프로필을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="41764-130">The MRTK also provides a default profile that is optimized for deployment and testing on the HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2).</span></span>

<span data-ttu-id="41764-131">MixedRealityToolkit 개체에 대한 프로필을 선택하라는 메시지가 표시되면 기본 선택된 프로필 대신 이 프로필을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="41764-131">When prompted to choose a profile for the MixedRealityToolkit object, use this profile instead of the default selected profile.</span></span>

<span data-ttu-id="41764-132">HoloLens2 프로필과 기본 프로필의 주요 차이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="41764-132">The key differences between the HoloLens2 profile and the Default Profile are:</span></span>

<span data-ttu-id="41764-133">**사용할 수 없는** 기능:</span><span class="sxs-lookup"><span data-stu-id="41764-133">**Disabled** features:</span></span>

- [<span data-ttu-id="41764-134">경계 시스템</span><span class="sxs-lookup"><span data-stu-id="41764-134">Boundary system</span></span>](../boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="41764-135">시스템 텔레포트</span><span class="sxs-lookup"><span data-stu-id="41764-135">Teleport system</span></span>](../teleport-system/teleport-system.md)
- [<span data-ttu-id="41764-136">공간 인식 시스템</span><span class="sxs-lookup"><span data-stu-id="41764-136">Spatial awareness system</span></span>](../spatial-awareness/spatial-awareness-getting-started.md)
- <span data-ttu-id="41764-137">[손 메시 시각화](../input/hand-tracking.md)(성능 오버헤드 때문)</span><span class="sxs-lookup"><span data-stu-id="41764-137">[Hand mesh visualization](../input/hand-tracking.md) (due to performance overhead)</span></span>

<span data-ttu-id="41764-138">**사용할 수 있는** 시스템:</span><span class="sxs-lookup"><span data-stu-id="41764-138">**Enabled** systems:</span></span>

- <span data-ttu-id="41764-139">[시선 추적 공급자](../input/eye-tracking/eye-tracking-main.md)</span><span class="sxs-lookup"><span data-stu-id="41764-139">The [eye tracking provider](../input/eye-tracking/eye-tracking-main.md)</span></span>
- <span data-ttu-id="41764-140">시선 입력 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="41764-140">Eye input simulation</span></span>

<span data-ttu-id="41764-141">카메라 프로필 설정은 편집기 품질 및 플레이어 품질이 동일하게 일치하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="41764-141">Camera profile settings are set to match so that the editor quality and player quality are the same.</span></span> <span data-ttu-id="41764-142">이는 불투명 디스플레이가 더 높은 품질로 설정된 기본 카메라 프로필과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="41764-142">This is different from the default camera profile where opaque displays are set to a higher quality.</span></span> <span data-ttu-id="41764-143">이 변경 사항은 편집기 내 품질이 낮아져 디바이스에서 렌더링되는 것과 더 가깝게 일치함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="41764-143">This change means that in-editor quality will be lower, which will more closely match what will be rendered on the device.</span></span>

> [!NOTE]
> <span data-ttu-id="41764-144">공간 인식 시스템은 클라이언트 피드백에 따라 기본적으로 꺼져 있습니다. 얼핏 흥미롭게 보일 수 있지만, 일반적으로 시각적 산만함과 추가 성능 저하를 피하기 위해 꺼져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41764-144">The Spatial Awareness system is turned off by default based on client feedback - it is an interesting visualization to see initially but is typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span> <span data-ttu-id="41764-145">시스템은 [여기의 지침](../spatial-awareness/spatial-awareness-getting-started.md)에 따라 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41764-145">The system can be re-enabled by following the [instructions here](../spatial-awareness/spatial-awareness-getting-started.md).</span></span>
