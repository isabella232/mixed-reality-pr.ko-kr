---
title: MRTK의 컨트롤러
description: MRTK에서 다양한 컨트롤러 사용에 대한 설명서
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 컨트롤러, HP Reverb, Oculus, HTC Vive, Hands
ms.openlocfilehash: 953b1cd56dbf7d7a548a3aba8da07ce5875fec74
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145488"
---
# <a name="controllers-in-mrtk"></a><span data-ttu-id="98d7e-104">MRTK의 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="98d7e-104">Controllers in MRTK</span></span>

<span data-ttu-id="98d7e-105">MRTK는 다양한 컨트롤러를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="98d7e-105">MRTK has support for many different controllers.</span></span> <span data-ttu-id="98d7e-106">HTC Vive Knuckles 및 HTC Vive Wands와 같은 많은 컨트롤러는 MRTK로 빌드된 애플리케이션이 호환되는 디바이스에서 시작되면 기본적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="98d7e-106">Many controllers, such as HTC Vive Knuckles and HTC Vive Wands, will work natively once an application built with MRTK is launched on the compatible device.</span></span> <span data-ttu-id="98d7e-107">Oculus Quest 및 HP Reverb G2 컨트롤러의 굴절된 손과 같은 다른 컨트롤러는 MRTK에서 인식되기 전에 추가 패키지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="98d7e-107">Other controllers, such as articulated hands on the Oculus Quest and the HP Reverb G2 Controllers, require additional packages before they are recognized by MRTK.</span></span>

<span data-ttu-id="98d7e-108">이 문서에서는 추가 패키지를 설치해야 하는 일반적인 시나리오를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98d7e-108">This document will describe the common scenarios where extra packages need to be installed.</span></span> <span data-ttu-id="98d7e-109">컨트롤러에 대한 자세한 내용은 기능 페이지 를 [**방문하세요.**](../features/input/controllers.md)</span><span class="sxs-lookup"><span data-stu-id="98d7e-109">For additional information about controllers, visit the [**features page**](../features/input/controllers.md).</span></span> <span data-ttu-id="98d7e-110">컨트롤러 관련 문제를 디버그하려면 [ **컨트롤러 매핑 도구를 참조하세요.**](../features/tools/controller-mapping-tool.md)</span><span class="sxs-lookup"><span data-stu-id="98d7e-110">To debug issues with controllers, see the [**Controller mapping tool**](../features/tools/controller-mapping-tool.md)</span></span>

## <a name="hp-reverb-g2-controllers"></a><span data-ttu-id="98d7e-111">HP Reverb G2 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="98d7e-111">HP Reverb G2 Controllers</span></span>

<span data-ttu-id="98d7e-112">MRTK를 사용할 때 HP Reverb G2 컨트롤러를 검색하고 표시하려면 다음 단계에 따라 [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="98d7e-112">To detect and show the HP Reverb G2 controllers when using MRTK, follow these steps to install the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package.</span></span> <span data-ttu-id="98d7e-113">이 패키지가 설치되면 컨트롤러가 HP Reverb에 표시되기 위해 기본 프로필을 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98d7e-113">Once this package is installed, no other changes to the default profiles need to be made to have the controllers show up on the HP Reverb.</span></span> 

<span data-ttu-id="98d7e-114">편집기에서 컨트롤러를 표시하려면 [**OpenXR 플러그 인**](/windows/mixed-reality/develop/unity/openxr-getting-started)을 사용하여 를 사용하고 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d7e-114">In order to display the controllers in editor, you need to ensure that you are using the using the [**OpenXR Plugin**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span></span>

## <a name="oculus-controllers"></a><span data-ttu-id="98d7e-115">Oculus 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="98d7e-115">Oculus Controllers</span></span> 

<span data-ttu-id="98d7e-116">Oculus 컨트롤러 모델을 시각화하려면 Oculus Quest 배포 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="98d7e-116">To visualize Oculus controller models, follow the Oculus Quest deployment instructions.</span></span> <span data-ttu-id="98d7e-117">컨트롤러를 사용할 때 가상 손을 표시하려면 XR SDK Oculus 디바이스 **관리자에서 컨트롤러 대신 아바타 손 렌더링을** 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98d7e-117">If you wish to show virtual hands when using the controllers, make sure that **Render Avatar Hands Instead Of Controllers** is checked under the XR SDK Oculus Device Manager.</span></span> <span data-ttu-id="98d7e-118">그렇지 않으면 이 옵션을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="98d7e-118">Otherwise, uncheck this option.</span></span>

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
