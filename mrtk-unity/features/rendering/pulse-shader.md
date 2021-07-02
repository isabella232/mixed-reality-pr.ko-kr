---
title: 펄스 셰이더
description: MRTK의 펄스 셰이더에 대 한 설명입니다.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 087806d48c7304d43f8383285cbaa2a12d8bf99a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176311"
---
# <a name="pulse-shader"></a><span data-ttu-id="f407d-104">펄스 셰이더</span><span class="sxs-lookup"><span data-stu-id="f407d-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="f407d-106">펄스 셰이더를 사용 하 여 표면 재구성, 트레일러 모양 메쉬 또는 기타 메시에 대 한 시각적 펄스 효과에 애니메이션 효과를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="f407d-107">셰이더 및 재질</span><span class="sxs-lookup"><span data-stu-id="f407d-107">Shader and material</span></span>

<span data-ttu-id="f407d-108">다음 자료에서는 **SR_Triangles** 셰이더를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="f407d-109">채우기 색, 선 색 및 펄스 색과 같은 다양 한 옵션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="f407d-110">**MRTK_Pulse_SpatialMeshBlue입니다.**</span><span class="sxs-lookup"><span data-stu-id="f407d-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="f407d-111">**MRTK_Pulse_SpatialMeshPurple입니다.**</span><span class="sxs-lookup"><span data-stu-id="f407d-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="f407d-112">**MRTK_Pulse_ArticulatedHandMeshBlue입니다.**</span><span class="sxs-lookup"><span data-stu-id="f407d-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="f407d-113">**MRTK_Pulse_ArticulatedHandMeshPurple입니다.**</span><span class="sxs-lookup"><span data-stu-id="f407d-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="f407d-114">필수 조건</span><span class="sxs-lookup"><span data-stu-id="f407d-114">Prerequisites</span></span>

<span data-ttu-id="f407d-115">공간 메시 예의 경우 MRTK 설정-> 공간 인식-> 표시 설정 표시 되는 재질에 MRTK_Pulse_ArticulatedHandMeshBlue 또는 MRTK_Pulse_ArticulatedHandMeshPurple가 할당 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-115">For the spatial mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned under MRTK Settings -> Spatial Awareness -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="f407d-116">손 모양 메시 예제에서는 MRTK_Pulse_SpatialMeshBlue prefab 또는 MRTK_Pulse_SpatialMeshPurple이에 할당 되어 있는지 확인 합니다 .이는 MRTK 설정 > 입력 > 손 추적-> 손 모양 Prefab에 할당 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-116">For the hand mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="f407d-117">작동 방식</span><span class="sxs-lookup"><span data-stu-id="f407d-117">How it works</span></span>

<span data-ttu-id="f407d-118">손 모양 메시 셰이더는 UVs를 사용 하 여 핸드 메시를 따라 펄스를 매핑하고 손목을 페이드 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="f407d-119">표면 재구성 셰이더는 꼭 짓 점 위치를 사용 하 여 펄스를 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="f407d-120">공간 메시 예-PulseShaderSpatialMeshExample</span><span class="sxs-lookup"><span data-stu-id="f407d-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="f407d-121">HoloLens 2 셸 환경과 마찬가지로, 손 광선을 사용 하 여 마우스를 가리키고 공기 탭을 사용 하 여 공간 메시에 대해 깜박이는 효과를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="f407d-122">예제 장면에는 Unity 게임 모드의 테스트 공간 메시 데이터 인 ExampleSpatialMesh 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="f407d-123">이 개체는 장치에서 사용 하지 않도록 설정 되 고 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="f407d-124">**PulseShaderSpatialMeshHandler** 스크립트는가 true 인 경우 적중 지점 위치의 공간 메시에 대 한 펄스 효과를 생성 합니다 `PulseOnSelect` .</span><span class="sxs-lookup"><span data-stu-id="f407d-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="f407d-125">`Auto Pulse`애니메이션을 반복 하기 위해 재질 자체에서 속성을 true로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="f407d-126">예제 장면에서이 스크립트는 PulseShaderSpatialMeshParent prefab에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="f407d-127">이 prefab는 런타임 공간 메시 Prefab 속성을 통해 공간 인식 프로필에서 참조 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="f407d-128">런타임 중에 PulseShaderSpatialMeshParent prefab 및가 인스턴스화되고 공간 메시 계층 구조에 추가 됩니다 (장치 에서만이 동작은 편집기에서 관찰 될 수 없음).</span><span class="sxs-lookup"><span data-stu-id="f407d-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="f407d-129">핸드 메시 예제-PulseShaderHandMeshExample</span><span class="sxs-lookup"><span data-stu-id="f407d-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="f407d-130">이 예제 장면에서는 펄스 셰이더를 사용 하는 손 모양 메쉬 시각화를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="f407d-131">HoloLens 장치에서 손을 검색 하는 경우 펄스 애니메이션은 한 번 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="f407d-132">이 시각적 피드백은 사용자의 상호 작용 신뢰도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="f407d-133">**PulseShaderHandMeshHandler** 스크립트는 할당 된 재질에 대해 펄스 효과를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="f407d-134">기본적으로 ' 직접 펄스 감지 '가 선택 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f407d-134">By default, 'Pulse On Hand Detected' is checked.</span></span>
