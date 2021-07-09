---
title: Mixed Reality OpenXR 플러그 인 릴리스 정보
description: 최신 릴리스 정보와 Mixed Reality OpenXR 플러그 인에 대한 업그레이드의 최신 상태를 유지합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394631"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a><span data-ttu-id="a3e78-104">Mixed Reality OpenXR 플러그 인 릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="a3e78-104">Mixed Reality OpenXR plugin release notes</span></span>

## <a name="100---current-release"></a><span data-ttu-id="a3e78-105">1.0.0 - 현재 릴리스</span><span class="sxs-lookup"><span data-stu-id="a3e78-105">1.0.0 - Current release</span></span>

* <span data-ttu-id="a3e78-106">ARAnchorManagers 존재 여부에 관계없이 앱 시작 시 XRAnchorSubsystem이 항상 시작되는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-106">Fixed a bug where a the XRAnchorSubsystem was always started on app start regardless ARAnchorManager’s present.</span></span>
* <span data-ttu-id="a3e78-107">재투영 모드가 제대로 작동하지 않는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-107">Fixed a bug where the reprojection mode didn’t work properly.</span></span>

## <a name="100-preview2---2021-06-14"></a><span data-ttu-id="a3e78-108">1.0.0-preview.2 - 2021-06-14</span><span class="sxs-lookup"><span data-stu-id="a3e78-108">1.0.0-preview.2 - 2021-06-14</span></span>

* <span data-ttu-id="a3e78-109">Unitys 1.2.2 OpenXR 플러그 인에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-109">Depends on Unity’s 1.2.2 OpenXR plugin.</span></span>
* <span data-ttu-id="a3e78-110">Holographic 원격 기능을 개별 기능 그룹으로 변경했습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-110">Changed Holographic Remoting features in to individual feature groups.</span></span>
* <span data-ttu-id="a3e78-111">“Apply HoloLens 2 프로젝트 설정”이 프로젝트 색 공간을 변경하는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-111">Fixed a bug where “Apply HoloLens 2 project settings” changes project color space.</span></span> <span data-ttu-id="a3e78-112">Unity OpenXR 1.2.0 플러그 인 이후에는 더 이상 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-112">This is no longer needed after Unity OpenXR 1.2.0 plugin.</span></span>
* <span data-ttu-id="a3e78-113">애플리케이션을 일시 중지하고 다시 시작한 후 연결 해제 없이 입력 디바이스가 연결되는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-113">Fixed a bug where a input device get connected without disconnect after application suspended and resumed.</span></span>
* <span data-ttu-id="a3e78-114">ARSession을 통해 플러그 인 및 현재 추적 상태를 감지하기 위한 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-114">Added support for detecting plugin and current tracking states via ARSession.</span></span>
* <span data-ttu-id="a3e78-115">“AR 기본 평면” ARFoundation 프리팹이 보이지 않는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-115">Fixed a bug where the “AR Default Plane” ARFoundation prefab wouldn’t be visible.</span></span>

## <a name="100-preview1---2021-06-02"></a><span data-ttu-id="a3e78-116">1.0.0-preview.1 - 2021-06-02</span><span class="sxs-lookup"><span data-stu-id="a3e78-116">1.0.0-preview.1 - 2021-06-02</span></span>

* <span data-ttu-id="a3e78-117">미리 보기 확장 대신 MSFT 확장을 이해하는 OpenXR 장면이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-117">Supports OpenXR scene understanding MSFT extensions instead of preview extensions.</span></span>
* <span data-ttu-id="a3e78-118">HoloLens 2의 평면 검색에는 더 이상 Mixed Reality OpenXR 런타임의 미리 보기 버전이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-118">Plane detection on HoloLens 2 no longer requires preview versions of the Mixed Reality OpenXR runtimes.</span></span>

## <a name="095---2021-05-21"></a><span data-ttu-id="a3e78-119">0.9.5 - 2021-05-21</span><span class="sxs-lookup"><span data-stu-id="a3e78-119">0.9.5 - 2021-05-21</span></span>

* <span data-ttu-id="a3e78-120">Unitys 1.2.0 OpenXR 플러그 인에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-120">Depends on Unity’s 1.2.0 OpenXR Plugin</span></span>
* <span data-ttu-id="a3e78-121">구성을 위해 새로운 기능 UI(OpenXR Plugin 1.2.0)에 적용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-121">Adapted to the new feature UI (in OpenXR Plugin 1.2.0) for configuration.</span></span>
* <span data-ttu-id="a3e78-122">검색 가능한 카메라 공급자가 제대로 등록 취소되지 않는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-122">Fixed a bug where the locatable camera provider wasn’t properly unregistering.</span></span>
* <span data-ttu-id="a3e78-123">[보존]의 일부 추가 사용을 정리했습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-123">Cleaned up some extra usages of [Preserve].</span></span>
* <span data-ttu-id="a3e78-124">입력 시스템 UI에서 “HP Reverb G2 컨트롤러(OpenXR)” 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-124">Update “HP Reverb G2 Controller (OpenXR)” name in the input system UI.</span></span>

## <a name="094---2021-05-20"></a><span data-ttu-id="a3e78-125">0.9.4 - 2021-05-20</span><span class="sxs-lookup"><span data-stu-id="a3e78-125">0.9.4 - 2021-05-20</span></span>

* <span data-ttu-id="a3e78-126">Unitys 1.2.0 OpenXR 플러그 인에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-126">Depends on Unity’s 1.2.0 OpenXR Plugin.</span></span>
* <span data-ttu-id="a3e78-127">모션 컨트롤러 glTF 모델을 얻기 위해 새로운 C# API를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-127">Added new C# API to get motion controller glTF model.</span></span>
* <span data-ttu-id="a3e78-128">뷰 구성을 사용하도록 설정하고 재투영 설정을 지정하는 새로운 C# API를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-128">Added new C# API to get enabled view configurations and set reprojection settings.</span></span>
* <span data-ttu-id="a3e78-129">XRMeshSubsystem으로 메시를 계산하기 위한 추가 설정을 설정하는 새로운 C# API가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-129">Added new C# API to set additional settings for computing meshes with XRMeshSubsystem.</span></span>
* <span data-ttu-id="a3e78-130">동작 인식 이벤트를 구성하고 구독하기 위한 새로운 C# API가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-130">Added new C# API to configure and subscribe to gesture recognition events.</span></span>
* <span data-ttu-id="a3e78-131">Windows->XR->편집기 원격 설정 대화 상자를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-131">Added Windows->XR->Editor Remoting settings dialog.</span></span>
* <span data-ttu-id="a3e78-132">HoloLens UWP 애플리케이션에 대한 ARM 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-132">Added ARM support for HoloLens UWP applications.</span></span>

## <a name="093---2021-04-29"></a><span data-ttu-id="a3e78-133">0.9.3 - 2021-04-29</span><span class="sxs-lookup"><span data-stu-id="a3e78-133">0.9.3 - 2021-04-29</span></span>

* <span data-ttu-id="a3e78-134">Holographic 원격 연결이 안정적이지 않은 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-134">Fixed a bug where Holographic remoting connection is not reliable</span></span>
* <span data-ttu-id="a3e78-135">Unity 1.1.1 OpenXR 플러그 인으로 업그레이드한 후 VR 렌더링 성능이 최적화되지 않는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-135">Fixed a bug where the VR rendering performance is sub-optimum after upgrade to Unity’s 1.1.1 OpenXR plugin.</span></span>

## <a name="092---2021-04-21"></a><span data-ttu-id="a3e78-136">0.9.2 - 2021-04-21</span><span class="sxs-lookup"><span data-stu-id="a3e78-136">0.9.2 - 2021-04-21</span></span>

* <span data-ttu-id="a3e78-137">플러그 인 버전 0.9.1의 HoloLens 2에서 평면 검색은 Mixed Reality OpenXR 미리 보기 런타임의 버전 105에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-137">Plane detection on HoloLens 2 in plugin version 0.9.1 will work with version 105 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="a3e78-138">플러그 인 버전 0.9.2의 HoloLens 2에서 평면 검색은 Mixed Reality OpenXR 미리 보기 런타임의 버전 106에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-138">Plane detection on HoloLens 2 in plugin version 0.9.2 will work with version 106 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="a3e78-139">XRInputSubsystem.\* GetTrackingOriginMode(입력 시스템에서 관리하지 않음)와 같은 호출이 잘못된 값으로 성공을 반환하지 못하도록 InputProvider에서 사용하지 않는 일부 콜백을 제거했습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-139">Removed some unused callbacks from InputProvider to prevent calls like XRInputSubsystem.\* GetTrackingOriginMode (which aren’t managed by our input system) from returning success with misleading values.</span></span>
* <span data-ttu-id="a3e78-140">Unity 콘솔 경고를 방지하기 위해 사용되지 않는 XRAnchorStore 버전을 자체 파일로 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-140">Split out deprecated version of XRAnchorStore into its own file to prevent Unity console warning.</span></span>

## <a name="091---2021-04-20"></a><span data-ttu-id="a3e78-141">0.9.1 - 2021-04-20</span><span class="sxs-lookup"><span data-stu-id="a3e78-141">0.9.1 - 2021-04-20</span></span>

* <span data-ttu-id="a3e78-142">Unitys 1.1.1 OpenXR 플러그 인에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-142">Depends on Unity’s 1.1.1 OpenXR Plugin.</span></span>
* <span data-ttu-id="a3e78-143">UWP 플랫폼용 Holographic 원격 애플리케이션에 대한 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-143">Added support for Holographic Remoting application for UWP platform.</span></span>
* <span data-ttu-id="a3e78-144">XRAnchorStore가 기본 스레드 외부에서 설정 인스턴스를 가져오려고 하는 UnityException을 수정했습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-144">Fix UnityException where XRAnchorStore was trying to get a settings instance outside the main thread.</span></span>

## <a name="090---2021-03-29"></a><span data-ttu-id="a3e78-145">0.9.0 - 2021-03-29</span><span class="sxs-lookup"><span data-stu-id="a3e78-145">0.9.0 - 2021-03-29</span></span>

* <span data-ttu-id="a3e78-146">XRMeshSubsystem 및 ARMeshManager를 통한 공간 매핑 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-146">Added support for spatial mapping via XRMeshSubsystem and ARMeshManager.</span></span>
* <span data-ttu-id="a3e78-147">다른 Unity 패키지를 지원하기 위해 OpenXR 핸들을 가져오는 새로운 C# API가 추가되어 OpenXR 확장을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-147">Added new C# API to get OpenXR handles to support other Unity packages consumes OpenXR extensions.</span></span>
* <span data-ttu-id="a3e78-148">Perception WinRT API를 사용하는 다른 Unity 패키지를 지원하기 위해 Windows.Perception API와 상호 운용할 수 있는 새로운 C# API를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-148">Added new C# API to interop with Windows.Perception APIs to support other Unity packages consuming Perception WinRT APIs.</span></span>
* <span data-ttu-id="a3e78-149">Windows Mixed Reality 기능 세트의 필수 기능에서 상호 작용 프로필을 제거하여 개발자가 테스트한 모션 컨트롤러를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-149">Removed interaction profiles from required features in Windows Mixed Reality feature set, so developers can choose the motion controllers they tested with.</span></span>
* <span data-ttu-id="a3e78-150">사용자가 편집기 원격 기능을 올바르게 설정할 수 있도록 Holographic 편집기 원격 기능 검사기를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-150">Added Holographic editor remoting feature validator to help users to setup editor remoting properly.</span></span>
* <span data-ttu-id="a3e78-151">연결 실패 후 Holographic 편집기 원격 모드를 종료할 때 Unity 편집기가 충돌하는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-151">Fixed a bug where Unity editor crashes when exiting Holographic editor remoting mode after connection failure.</span></span>
* <span data-ttu-id="a3e78-152">미리 곱하지 않는 알파 텍스처가 HoloLens 2에서 성능이 최적화되지 않는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-152">Fixed a bug where unpremultipled alpha textures leads to sub-optimum performance on HoloLens 2.</span></span>
* <span data-ttu-id="a3e78-153">장면 원점이 바닥 수준에 있을 때 손 추적이 올바르게 위치하지 않는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-153">Fixed a bug where hand tracking was not located correctly when the scene origin was at floor level.</span></span>
* <span data-ttu-id="a3e78-154">새 장면을 나가고 로드한 후 손 메시 추적이 사라지는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-154">Fixed a bug where hand mesh tracking disappear after leaving and loading a new scene.</span></span>
* <span data-ttu-id="a3e78-155">검색 가능한 카메라 공급자가 제대로 정리되지 않는 버그가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-155">Fixed a bug where locatable camera provider didn’t properly clean up.</span></span>
* <span data-ttu-id="a3e78-156">XRAnchorStore API의 네임스페이스를 Microsoft.MixedReality.OpenXR로 수정했습니다.</span><span class="sxs-lookup"><span data-stu-id="a3e78-156">Revised the namespace of XRAnchorStore API into Microsoft.MixedReality.OpenXR.</span></span>