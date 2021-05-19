---
title: 장면 시스템 장면 유형
description: MRTK의 여러 장면 유형에 대 한 설명서
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 06bfd1dbad3986044f099510c2de4d36cda50fc0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144570"
---
# <a name="scene-types"></a><span data-ttu-id="15852-104">장면 유형</span><span class="sxs-lookup"><span data-stu-id="15852-104">Scene types</span></span>

<span data-ttu-id="15852-105">장면은 세 가지 형식으로 나뉘어 있으며 각 형식에는 다른 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-105">Scenes have been divided into three types, and each type has a different function.</span></span>

![계층의 장면 시스템](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a><span data-ttu-id="15852-107">콘텐츠 장면</span><span class="sxs-lookup"><span data-stu-id="15852-107">Content scenes</span></span>

<span data-ttu-id="15852-108">이는를 처리 하는 데 사용 하는 배경입니다.</span><span class="sxs-lookup"><span data-stu-id="15852-108">These are the scenes you're used to dealing with.</span></span> <span data-ttu-id="15852-109">모든 종류의 콘텐츠를 저장 하 고 모든 조합에서 로드 하거나 언로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-109">Any kind of content can be stored in them, and they can be loaded or unloaded in any combination.</span></span>

<span data-ttu-id="15852-110">콘텐츠 장면을 기본적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-110">Content scenes are enabled by default.</span></span> <span data-ttu-id="15852-111">프로필의 배열에 포함 된 모든 장면을 `Content Scenes` 서비스에서 로드/언로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-111">Any scenes included in your profile's `Content Scenes` array can be loaded / unloaded by the service.</span></span>

___

## <a name="manager-scenes"></a><span data-ttu-id="15852-112">관리자 장면</span><span class="sxs-lookup"><span data-stu-id="15852-112">Manager scenes</span></span>

<span data-ttu-id="15852-113">필수 MixedRealityToolkit 인스턴스가 있는 단일 장면.</span><span class="sxs-lookup"><span data-stu-id="15852-113">A single scene with a required MixedRealityToolkit instance.</span></span> <span data-ttu-id="15852-114">이 장면은 처음 시작할 때 로드 되 고 앱의 수명 동안 로드 된 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15852-114">This scene will be loaded first on launch and will remain loaded for the lifetime of the app.</span></span> <span data-ttu-id="15852-115">또한 관리자 장면은 제거 되지 않아야 하는 다른 개체를 호스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-115">The manager scene can also host other objects that should never be destroyed.</span></span> <span data-ttu-id="15852-116">이는 DontDestroyOnLoad에 대 한 기본 설정 대안입니다.</span><span class="sxs-lookup"><span data-stu-id="15852-116">This is the preferred alternative to DontDestroyOnLoad.</span></span>

<span data-ttu-id="15852-117">이 기능을 사용 하도록 설정 하려면 프로필을 체크 인하고 `Use Manager Scene` 장면 개체를 필드로 끕니다 `Manager Scene` .</span><span class="sxs-lookup"><span data-stu-id="15852-117">To enable this feature, check `Use Manager Scene` in your profile and drag a scene object into the `Manager Scene` field.</span></span>

___

## <a name="lighting-scenes"></a><span data-ttu-id="15852-118">조명 장면</span><span class="sxs-lookup"><span data-stu-id="15852-118">Lighting scenes</span></span>

<span data-ttu-id="15852-119">조명 정보 및 조명 개체를 저장 하는 장면 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="15852-119">A set of scenes which store lighting information and lighting objects.</span></span> <span data-ttu-id="15852-120">한 번에 하나만 로드할 수 있으며 부드러운 조명 전환을 위해 로드 하는 동안 해당 설정을 혼합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-120">Only one can be loaded at a time, and their settings can be blended during loads for smooth lighting transitions.</span></span>

<span data-ttu-id="15852-121">Unity의 조명 설정-앰비언트 광원, skyboxes 등은 개별 장면에 연결 되 고 재정의 동작이 간단 하지 않으므로 추가 로드를 사용 하는 경우 관리 하기가 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-121">Unity's lighting settings - ambient light, skyboxes, etc - can be tricky to manage when using additive loading because they're tied to individual scenes and override behavior is not straightforward.</span></span> <span data-ttu-id="15852-122">실제로는 자산이 런타임에 가져오지 않는 조명 조건에서 작성 될 때 혼동을 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-122">In practice this can cause confusion when assets are authored in lighting conditions that don't obtain at runtime.</span></span>

![장면 시스템 조명 설정](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

<span data-ttu-id="15852-124">장면 시스템은 조명 장면을 사용하여 편집 모드와 재생 모드 모두에서 로드되거나 활성 상태인 장면에 관계없이 이러한 설정이 일관되게 유지되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="15852-124">The Scene System uses lighting scenes to ensure that these settings remain consistent regardless of what scenes are loaded or active, both in edit mode and in play mode.</span></span>

<span data-ttu-id="15852-125">이 기능을 사용하도록 설정하려면 프로필을 체크 `Use Lighting Scene` 인하고 배열을 채웁 수 `Lighting Scenes` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-125">To enable this feature, check `Use Lighting Scene` in your profile and populate the `Lighting Scenes` array.</span></span>

### <a name="cached-lighting-settings"></a><span data-ttu-id="15852-126">캐시된 조명 설정</span><span class="sxs-lookup"><span data-stu-id="15852-126">Cached lighting settings</span></span>

<span data-ttu-id="15852-127">프로필은 조명 장면에 보관된 조명 설정의 캐시된 복사본을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15852-127">Your profile stores cached copies of the lighting settings kept in your lighting scenes.</span></span> <span data-ttu-id="15852-128">조명 장면에서 이러한 설정이 변경되면 재생 모드에서 조명이 예상대로 표시되도록 캐시를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15852-128">If those settings change in your lighting scenes, you will need to update your cache to ensure lighting appears as expected in play mode.</span></span> <span data-ttu-id="15852-129">캐시된 설정이 만료된 것으로 의심되는 프로필에 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="15852-129">Your profile will display a warning when it suspects your cached settings are out of date.</span></span> <span data-ttu-id="15852-130">클릭하면 `Update Cached Lighting Settings` 각 조명 장면을 로드하고, 설정을 추출한 다음, 프로필에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="15852-130">Clicking `Update Cached Lighting Settings` will load each of your lighting scenes, extract their settings, then store them in your profile.</span></span>

![장면 시스템 캐시 조명 설정](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a><span data-ttu-id="15852-132">편집기 동작</span><span class="sxs-lookup"><span data-stu-id="15852-132">Editor behavior</span></span>

<span data-ttu-id="15852-133">조명 장면을 사용할 경우의 이점 중 하나는 편집하는 동안 콘텐츠가 올바르게 켜져 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="15852-133">One benefit of using lighting scenes is knowing your content is lit correctly while editing.</span></span> <span data-ttu-id="15852-134">이를 위해 장면 서비스는 항상 조명 장면을 로드하고 해당 장면의 조명 설정을 현재 활성 장면에 복사합니다.\*</span><span class="sxs-lookup"><span data-stu-id="15852-134">To this end, the Scene Service will keep a lighting scene loaded at all times, and will copy that scene's lighting settings to the current active scene.\*</span></span>

<span data-ttu-id="15852-135">장면 시스템의 [서비스 검사기](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) 를 열어 로드되는 조명 장면을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-135">You can change which lighting scene is loaded by opening the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="15852-136">편집 모드에서는 조명 장면 간에 즉시 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-136">In edit mode you can instantaneously transition between lighting scenes.</span></span> <span data-ttu-id="15852-137">재생 모드에서는 전환을 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15852-137">In play mode, you can preview transitions.</span></span>

![장면 시스템 검사기](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

<span data-ttu-id="15852-139">\**참고: 일반적으로 활성 장면에 따라 편집기에서 조명 설정이 결정됩니다. 그러나 활성 장면도 새로 만든 개체가 기본적으로 배치되고 조명 장면에 조명 구성 요소만 포함할 수 있으므로 이 기능을 사용하여 조명 설정을 적용하지 않도록 선택합니다. 대신 현재 조명 장면의 설정이 활성 장면의 설정에 자동으로 복사됩니다. 이렇게 하면 콘텐츠 장면의 조명 설정이 덮어쓰여집니다.*</span><span class="sxs-lookup"><span data-stu-id="15852-139">\**Note: Typically the active scene determines your lighting settings in editor. However we choose not to use this feature to enforce lighting settings, because the active scene is also where newly created objects are placed by default, and lighting scenes are only permitted to contain lighting components. Instead, the current lighting scene's settings are automatically copied to the active scene's settings instead. Keep in mind that this will result in your content scene's lighting settings being over-written.*</span></span>
