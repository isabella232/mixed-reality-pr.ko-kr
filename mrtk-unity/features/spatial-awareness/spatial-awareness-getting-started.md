---
title: 공간 인식 시작
description: MRTK의 공간 인식에 대해 설명 합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 46bb78bc4e2574fd4da14f19edf52624b7b301c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176712"
---
# <a name="spatial-awareness-getting-started"></a><span data-ttu-id="2b26f-104">공간 인식 시작</span><span class="sxs-lookup"><span data-stu-id="2b26f-104">Spatial awareness getting started</span></span>

![공간 인식](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

<span data-ttu-id="2b26f-106">공간 인식 시스템은 혼합 현실 응용 프로그램에서 실제 환경 인식을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-106">The Spatial Awareness system provides real-world environmental awareness in mixed reality applications.</span></span> <span data-ttu-id="2b26f-107">Microsoft HoloLens에 대해 도입 된 공간 인식에서는 환경의 기 하 도형을 나타내는 메시 컬렉션을 제공 하 여 holograms와 실제 환경 간의 강력한 상호 작용을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-107">When introduced on Microsoft HoloLens, Spatial Awareness provided a collection of meshes, representing the geometry of the environment, which allowed for compelling interactions between holograms and the real-world.</span></span>

> [!NOTE]
> <span data-ttu-id="2b26f-108">이번에는 혼합 현실 Toolkit HoloToolkit에서 원래 패키지 된 공간을 인식 하는 알고리즘과 함께 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-108">At this time, the Mixed Reality Toolkit does not ship with Spatial Understanding algorithms as originally packaged in the HoloToolkit.</span></span> <span data-ttu-id="2b26f-109">일반적으로 공간을 이해 하려면 공간 메시 데이터를 변환 하 여 평면, 벽, 층, 최대값이 등의 단순화 및/또는 그룹화 된 메시 데이터를 생성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-109">Spatial Understanding generally involves transforming Spatial Mesh data to create simplified and/or grouped Mesh data such as planes, walls, floors, ceilings, etc.</span></span>

## <a name="getting-started"></a><span data-ttu-id="2b26f-110">시작</span><span class="sxs-lookup"><span data-stu-id="2b26f-110">Getting started</span></span>

<span data-ttu-id="2b26f-111">공간 인식에 대 한 지원을 추가 하려면 혼합 현실 Toolkit의 두 가지 주요 구성 요소 (공간 인식 시스템 및 지원 되는 플랫폼 공급자)가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-111">Adding support for Spatial Awareness requires two key components of the Mixed Reality Toolkit: the Spatial Awareness system and a supported platform provider.</span></span>

1. <span data-ttu-id="2b26f-112">공간 인식 시스템 [사용](#enable-the-spatial-awareness-system)</span><span class="sxs-lookup"><span data-stu-id="2b26f-112">[Enable](#enable-the-spatial-awareness-system) the Spatial Awareness system</span></span>
2. <span data-ttu-id="2b26f-113">하나 이상의 공간 관찰자를 [등록](#register-observers) 하 고 [구성](configuring-spatial-awareness-mesh-observer.md) 하 여 메시 데이터 제공</span><span class="sxs-lookup"><span data-stu-id="2b26f-113">[Register](#register-observers) and [configure](configuring-spatial-awareness-mesh-observer.md) one or more spatial observers to provide mesh data</span></span>
3. <span data-ttu-id="2b26f-114">공간 인식을 지 원하는 플랫폼에 [빌드 및 배포](#build-and-deploy)</span><span class="sxs-lookup"><span data-stu-id="2b26f-114">[Build and deploy](#build-and-deploy) to a platform that supports Spatial Awareness</span></span>

### <a name="enable-the-spatial-awareness-system"></a><span data-ttu-id="2b26f-115">공간 인식 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="2b26f-115">Enable the spatial awareness system</span></span>

<span data-ttu-id="2b26f-116">공간 인식 시스템은 MixedRealityToolkit 개체 또는 다른 [서비스 등록자](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) 구성 요소에 의해 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-116">The Spatial Awareness system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span> <span data-ttu-id="2b26f-117">*MixedRealityToolkit* 프로필에서 *공간 인식 시스템* 을 사용 하거나 사용 하지 않도록 설정 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-117">Follow the steps below to enable or disable the *Spatial Awareness system* in the *MixedRealityToolkit* profile.</span></span>

<span data-ttu-id="2b26f-118">혼합 현실 Toolkit는 미리 구성 된 몇 가지 기본 프로필과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-118">The Mixed Reality Toolkit ships with a few default pre-configured profiles.</span></span> <span data-ttu-id="2b26f-119">이러한 중 일부에는 기본적으로 공간 인식 시스템이 활성화 되거나 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-119">Some of these have the Spatial Awareness system enabled OR disabled by default.</span></span> <span data-ttu-id="2b26f-120">특히 사용 하지 않도록 설정 된 경우이 사전 구성의 의도는 메시를 계산 하 고 렌더링 하는 시각적 오버 헤드를 방지 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-120">The intent of this pre-configuration, particularly for when disabled, is to avoid the visual overhead of calculating and rendering the meshes.</span></span>

| <span data-ttu-id="2b26f-121">프로필</span><span class="sxs-lookup"><span data-stu-id="2b26f-121">Profile</span></span> | <span data-ttu-id="2b26f-122">기본적으로 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="2b26f-122">System Enabled by Default</span></span> |
| --- | --- |
| <span data-ttu-id="2b26f-123">`DefaultHoloLens1ConfigurationProfile` (자산/m RTK/SDK/Profiles/HoloLens1)</span><span class="sxs-lookup"><span data-stu-id="2b26f-123">`DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1)</span></span> | <span data-ttu-id="2b26f-124">False</span><span class="sxs-lookup"><span data-stu-id="2b26f-124">False</span></span> |
| <span data-ttu-id="2b26f-125">`DefaultHoloLens2ConfigurationProfile` (자산/m RTK/SDK/Profiles/HoloLens2)</span><span class="sxs-lookup"><span data-stu-id="2b26f-125">`DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2)</span></span> | <span data-ttu-id="2b26f-126">False</span><span class="sxs-lookup"><span data-stu-id="2b26f-126">False</span></span> |
| <span data-ttu-id="2b26f-127">`DefaultMixedRealityToolkitConfigurationProfile` (자산/m RTK/SDK/프로필)</span><span class="sxs-lookup"><span data-stu-id="2b26f-127">`DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles)</span></span> | <span data-ttu-id="2b26f-128">True</span><span class="sxs-lookup"><span data-stu-id="2b26f-128">True</span></span> |

1. <span data-ttu-id="2b26f-129">장면 계층 구조에서 MixedRealityToolkit 개체를 선택 하 여 검사기 패널에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-129">Select the MixedRealityToolkit object in the scene hierarchy to open in the Inspector Panel.</span></span>

    ![MRTK 구성 장면 계층 구조](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="2b26f-131">*공간 인식 시스템* 섹션으로 이동 하 여 *공간 인식 시스템 사용* 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-131">Navigate to the *Spatial Awareness System* section and check *Enable Spatial Awareness System*</span></span>

    ![공간 인식 사용](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. <span data-ttu-id="2b26f-133">원하는 공간 인식 시스템 구현 유형을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-133">Select the desired Spatial Awareness system implementation type.</span></span> <span data-ttu-id="2b26f-134">는 [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) 제공 된 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-134">The [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) is the default provided.</span></span>

    ![공간 인식 시스템 구현 선택](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a><span data-ttu-id="2b26f-136">관찰자 등록</span><span class="sxs-lookup"><span data-stu-id="2b26f-136">Register observers</span></span>

<span data-ttu-id="2b26f-137">혼합 현실 Toolkit의 서비스에는 플랫폼 특정 데이터 및 구현 제어와 함께 주 서비스를 보완 하는 [Data Provider 서비스가](../../architecture/systems-extensions-providers.md) 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-137">Services in the Mixed Reality Toolkit can have [Data Provider services](../../architecture/systems-extensions-providers.md) that supplement the main service with platform specific data and implementation controls.</span></span> <span data-ttu-id="2b26f-138">이에 대 한 예는 다양 한 플랫폼별 Api에서 컨트롤러 및 기타 관련 입력 정보를 가져오기 위해 [여러 데이터 공급자](../input/input-providers.md) 가 있는 혼합 현실 입력 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-138">An example of this is the Mixed Reality Input System which has [multiple data providers](../input/input-providers.md) to get controller and other related input information from various platform-specific APIs.</span></span>

<span data-ttu-id="2b26f-139">공간 인식 시스템은 데이터 공급자가 시스템에 실제 환경을 위한 메시 데이터를 제공 한다는 점에서 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-139">The Spatial Awareness system is similar in that data providers supply the system with mesh data about the real-world.</span></span> <span data-ttu-id="2b26f-140">공간 인식 프로필에는 하나 이상의 공간 관찰자가 등록 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-140">The Spatial Awareness profile must have at least one Spatial Observer registered.</span></span> <span data-ttu-id="2b26f-141">일반적으로 공간 관찰자는 플랫폼 특정 끝점에서 다양 한 유형의 메시 데이터를 제공 하기 위한 공급자 역할을 하는 플랫폼별 구성 요소입니다 (즉,</span><span class="sxs-lookup"><span data-stu-id="2b26f-141">Spatial Observers are generally platform specific components that act as the provider for surfacing various types of mesh data from a platform specific endpoint (i.e</span></span> <span data-ttu-id="2b26f-142">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="2b26f-142">HoloLens).</span></span>

1. <span data-ttu-id="2b26f-143">*공간 인식 시스템 프로필* 을 열거나 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-143">Open or expand the *Spatial Awareness System profile*</span></span>

    ![공간 인식 시스템 프로필](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. <span data-ttu-id="2b26f-145">*"공간 관찰자 추가"* 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-145">Click the *"Add Spatial Observer"* button</span></span>
1. <span data-ttu-id="2b26f-146">원하는 *공간 관찰자 구현 유형을* 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-146">Select the desired *Spatial Observer implementation type*</span></span>

    ![공간 관찰자 구현을 선택 합니다.](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. <span data-ttu-id="2b26f-148">필요 [에 따라 관찰자의 구성 속성을 수정](configuring-spatial-awareness-mesh-observer.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-148">[Modify configuration properties on the observer](configuring-spatial-awareness-mesh-observer.md) as necessary</span></span>

> [!NOTE]
> <span data-ttu-id="2b26f-149">`DefaultMixedRealityToolkitConfigurationProfile`(asset/mrtk/SDK/profile)의 사용자에 게는 클래스를 사용 하는 Windows Mixed Reality 플랫폼용으로 미리 구성 된 공간 인식 시스템이 있습니다 [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) .</span><span class="sxs-lookup"><span data-stu-id="2b26f-149">Users of the `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) will have the Spatial Awareness system pre-configured for the Windows Mixed Reality platform which uses the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="2b26f-150">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="2b26f-150">Build and deploy</span></span>

<span data-ttu-id="2b26f-151">공간 인식 시스템이 원하는 관찰자로 구성 되 면 프로젝트를 빌드하고 대상 플랫폼에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-151">Once the Spatial Awareness system is configured with the desired observer(s), the project can be built and deployed to the target platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b26f-152">Windows Mixed Reality 플랫폼을 대상으로 하는 경우 (예: HoloLens) 장치에서 공간 인식 시스템을 사용 하기 위해 [공간 인식 기능이](/windows/mixed-reality/spatial-mapping-in-unity) 사용 되도록 설정 되어 있는지 확인 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-152">If targeting the Windows Mixed Reality platform (ex: HoloLens), it is important to ensure the [Spatial Perception capability](/windows/mixed-reality/spatial-mapping-in-unity) is enabled in order to use the Spatial Awareness system on device.</span></span>

> [!WARNING]
> <span data-ttu-id="2b26f-153">Microsoft HoloLens를 비롯 한 일부 플랫폼은 Unity 내에서 원격 실행을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-153">Some platforms, including Microsoft HoloLens, provide support for remote execution from within Unity.</span></span> <span data-ttu-id="2b26f-154">이 기능을 사용 하면 빌드 및 배포 단계를 요구 하지 않고 신속 하 게 개발 하 고 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-154">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="2b26f-155">대상 하드웨어 및 플랫폼에서 실행 되는 응용 프로그램의 빌드 및 배포 버전을 사용 하 여 최종 승인 테스트를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-155">Be sure to do final acceptance testing using a built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2b26f-156">다음 단계</span><span class="sxs-lookup"><span data-stu-id="2b26f-156">Next steps</span></span>

<span data-ttu-id="2b26f-157">위의 절차에 따라 공간 인식 시스템을 사용 하도록 설정 하면 시스템을 더 자세히 구성 하 고 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b26f-157">After following the procedures above to enable the Spatial Awareness system, the system can be configured and controlled in more detail.</span></span>

<span data-ttu-id="2b26f-158">Inspector에서 관찰자를 구성 하는 방법에 대 한 정보:</span><span class="sxs-lookup"><span data-stu-id="2b26f-158">Information for configuring observers in inspector:</span></span>

- [<span data-ttu-id="2b26f-159">장치 사용에 대 한 관찰자 구성</span><span class="sxs-lookup"><span data-stu-id="2b26f-159">Configuring Observers for on device usage</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="2b26f-160">편집기에서 사용 하기 위한 관찰자 구성</span><span class="sxs-lookup"><span data-stu-id="2b26f-160">Configuring Observers for in-editor usage</span></span>](spatial-object-mesh-observer.md)

<span data-ttu-id="2b26f-161">코드를 통해 관찰자를 제어 및 확장 하는 방법에 대 한 정보:</span><span class="sxs-lookup"><span data-stu-id="2b26f-161">Information for controlling and extending observers via code:</span></span>

- [<span data-ttu-id="2b26f-162">코드를 통해 관찰자 구성</span><span class="sxs-lookup"><span data-stu-id="2b26f-162">Configuring Observers via Code</span></span>](usage-guide.md)
- [<span data-ttu-id="2b26f-163">사용자 지정 관찰자 만들기</span><span class="sxs-lookup"><span data-stu-id="2b26f-163">Creating a custom Observer</span></span>](create-data-provider.md)

## <a name="see-also"></a><span data-ttu-id="2b26f-164">참조</span><span class="sxs-lookup"><span data-stu-id="2b26f-164">See also</span></span>

- [<span data-ttu-id="2b26f-165">공간 인식 API 설명서</span><span class="sxs-lookup"><span data-stu-id="2b26f-165">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [<span data-ttu-id="2b26f-166">공간 매핑 개요 WMR</span><span class="sxs-lookup"><span data-stu-id="2b26f-166">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/spatial-mapping)
- [<span data-ttu-id="2b26f-167">Unity WMR의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="2b26f-167">Spatial Mapping in Unity WMR</span></span>](/windows/mixed-reality/spatial-mapping-in-unity)
