---
title: 장면 시스템 시작
description: MRTK를 이용한 장면 시스템의 방문 페이지
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 205b89d4defdeb5418a8a82896551d681cccde3d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144300"
---
# <a name="scene-system-overview"></a><span data-ttu-id="3fc11-104">장면 시스템 개요</span><span class="sxs-lookup"><span data-stu-id="3fc11-104">Scene system overview</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="3fc11-105">장면 시스템을 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="3fc11-105">When to use the scene system</span></span>

<span data-ttu-id="3fc11-106">프로젝트가 단일 장면으로 구성된 경우 장면 시스템이 필요하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="3fc11-107">다음 중 하나 이상이 true인 경우 가장 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="3fc11-108">프로젝트에는 여러 장면이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="3fc11-109">단일 장면 로드에 익숙하지만 MixedRealityToolkit 인스턴스를 삭제하는 방식이 마음에 들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="3fc11-110">여러 장면을 추가적으로 로드하여 환경을 구성하는 간단한 방법을 원합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="3fc11-111">진행 중인 로드 작업을 추적하는 간단한 방법 또는 한 번에 로드되는 여러 장면에 대한 장면 활성화를 제어하는 간단한 방법을 원합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="3fc11-112">모든 장면에서 조명을 일관되고 예측 가능하게 유지하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="3fc11-113">장면 시스템 리소스</span><span class="sxs-lookup"><span data-stu-id="3fc11-113">Scene System Resources</span></span>

<span data-ttu-id="3fc11-114">기본적으로 장면 시스템은 한 쌍의 장면 개체(DefaultManagerScene 및 DefaultLighting 장면)를 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="3fc11-115">이러한 장면 중 하나를 배치할 수 없는 경우 장면 시스템 프로필 검사기에서 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![기본 리소스 메시지](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="3fc11-117">! [참고] 프로젝트에서 사용자 지정 관리자 및 조명 장면을 사용하는 경우 이 메시지는 무시해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="3fc11-118">다음 섹션에서는 Mixed Reality 도구 키트를 가져오는 데 사용된 메서드에 따라 이 메시지를 해결하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="3fc11-119">Unity 패키지 관리자(UPM)</span><span class="sxs-lookup"><span data-stu-id="3fc11-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="3fc11-120">Mixed Reality Toolkit UPM 패키지에서 장면 시스템 리소스는 샘플로 패키지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="3fc11-121">UPM 패키지는 변경이 불가능하기 때문에 Unity는 프로젝트로 명시적으로 가져오지 않는 한 필요한 장면 파일을 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="3fc11-122">가져오려면 다음 단계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-122">To import use the following steps:</span></span>

- <span data-ttu-id="3fc11-123">**창**  >  **패키지 관리자** 선택</span><span class="sxs-lookup"><span data-stu-id="3fc11-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="3fc11-124">**Mixed Reality Toolkit Foundation** 선택</span><span class="sxs-lookup"><span data-stu-id="3fc11-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="3fc11-125">**샘플** 섹션에서 **장면 시스템 리소스** 찾기</span><span class="sxs-lookup"><span data-stu-id="3fc11-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![장면 시스템 리소스 가져오기](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="3fc11-127">**가져오기** 선택</span><span class="sxs-lookup"><span data-stu-id="3fc11-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="3fc11-128">Asset (unitypackage) 파일</span><span class="sxs-lookup"><span data-stu-id="3fc11-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="3fc11-129">SceneSystemResources 폴더가 삭제 되었거나 가져오기 중에 선택 취소 된 경우 다음 단계를 사용 하 여 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="3fc11-130">**자산**  >  **가져오기 패키지**  >  **사용자 지정 패키지** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="3fc11-131">**MixedReality** 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="3fc11-132">**Services/SceneSystem/SceneSystemResources** 및 모든 자식 옵션이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![장면 시스템 리소스 다시 가져오기](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="3fc11-134">**가져오기** 선택</span><span class="sxs-lookup"><span data-stu-id="3fc11-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="3fc11-135">장면 시스템을 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="3fc11-135">How to use the scene system</span></span>

- [<span data-ttu-id="3fc11-136">장면 유형</span><span class="sxs-lookup"><span data-stu-id="3fc11-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="3fc11-137">콘텐츠 장면 로드</span><span class="sxs-lookup"><span data-stu-id="3fc11-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="3fc11-138">콘텐츠 로드 모니터링</span><span class="sxs-lookup"><span data-stu-id="3fc11-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="3fc11-139">조명 장면 로드</span><span class="sxs-lookup"><span data-stu-id="3fc11-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="3fc11-140">편집기 설정</span><span class="sxs-lookup"><span data-stu-id="3fc11-140">Editor settings</span></span>

<span data-ttu-id="3fc11-141">기본적으로 장면 시스템은 Unity 편집기에서 여러 동작을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="3fc11-142">이러한 동작 중 하나를 발견 하면 장면 시스템 프로필의 **편집기 설정** 섹션에서 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="3fc11-143">`Editor Manage Build Settings:` True 이면 서비스에서 빌드 설정을 자동으로 업데이트 하 여 모든 관리자, 조명 및 콘텐츠 장면이 추가 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="3fc11-144">빌드 설정을 완전히 제어 하려면이 기능을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="3fc11-145">`Editor Enforce Scene Order:` True 이면 서비스에서 관리자 장면이 먼저 장면 계층 구조에 표시 되 고 그 다음에는 조명 및 콘텐츠가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="3fc11-146">장면 계층 구조를 전체 제어 하려면이 기능을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="3fc11-147">`Editor Manage Loaded Scenes:` True 이면 서비스에서 관리자, 콘텐츠 및 조명 장면이 항상 로드 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="3fc11-148">편집기에서 로드 되는 장면을 전체 제어 하려면 사용 안 함을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="3fc11-149">`Editor Enforce Lighting Scene Types:` True 이면이 서비스는에 정의 된 조명 관련 구성 요소만 `PermittedLightingSceneComponentTypes` 조명 장면에서 허용 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="3fc11-150">조명 장면의 콘텐츠를 완전히 제어 하려면 사용 안 함을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fc11-150">Disable if you want total control over the content of lighting scenes.</span></span>

![시스템 편집기 설정 장면](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
