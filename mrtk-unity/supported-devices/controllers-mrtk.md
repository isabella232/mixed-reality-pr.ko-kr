---
title: MRTK의 컨트롤러
description: MRTK와 함께 다양 한 컨트롤러 사용에 대 한 설명서
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, 컨트롤러, HP 반향, Oculus, HTC Vive, 실습
ms.openlocfilehash: 111ebf2b1eb26bbef8cde16832f780acfa758595
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743585"
---
# <a name="controllers-in-mrtk"></a><span data-ttu-id="d4b2c-104">MRTK의 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="d4b2c-104">Controllers in MRTK</span></span>

<span data-ttu-id="d4b2c-105">MRTK는 다양 한 컨트롤러에 대 한 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-105">MRTK has support for many different controllers.</span></span> <span data-ttu-id="d4b2c-106">HTC Vive Knuckles 및 HTC Vive 지팡이와 같은 많은 컨트롤러는 호환 되는 장치에서 MRTK로 빌드된 응용 프로그램이 시작 되 면 기본적으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-106">Many controllers, such as HTC Vive Knuckles and HTC Vive Wands, will work natively once an application built with MRTK is launched on the compatible device.</span></span> <span data-ttu-id="d4b2c-107">Oculus 퀘스트 및 HP 반향 G2 컨트롤러에 대 한 트레일러 식 같은 다른 컨트롤러는 MRTK에서 인식 하기 전에 추가 패키지가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-107">Other controllers, such as articulated hands on the Oculus Quest and the HP Reverb G2 Controllers, require additional packages before they are recognized by MRTK.</span></span>

<span data-ttu-id="d4b2c-108">이 문서에서는 추가 패키지를 설치 해야 하는 일반적인 시나리오에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-108">This document will describe the common scenarios where extra packages need to be installed.</span></span> <span data-ttu-id="d4b2c-109">장치에 배포 하는 방법에 대 한 지침은 [**Hololens/WMR**](./wmr-mrtk.md) 또는 [**Oculus 퀘스트**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) 배포 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-109">For instructions on how to deploy to your device, see the [**Hololens/WMR**](./wmr-mrtk.md) or [**Oculus Quest**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) deployment pages.</span></span> <span data-ttu-id="d4b2c-110">컨트롤러에 대 한 자세한 내용은 [**기능 페이지**](../features/input/controllers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-110">For additional information about controllers, visit the [**features page**](../features/input/controllers.md).</span></span> <span data-ttu-id="d4b2c-111">컨트롤러 관련 문제를 디버그 하려면 [ **컨트롤러 매핑 도구** 를 참조 하세요.](../features/tools/controller-mapping-tool.md)</span><span class="sxs-lookup"><span data-stu-id="d4b2c-111">To debug issues with controllers, see the [**Controller mapping tool**](../features/tools/controller-mapping-tool.md)</span></span>

## <a name="hp-reverb-g2-controllers"></a><span data-ttu-id="d4b2c-112">HP 반향 G2 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="d4b2c-112">HP Reverb G2 Controllers</span></span>

<span data-ttu-id="d4b2c-113">MRTK를 사용할 때 HP 반향 G2 컨트롤러를 검색 하 고 표시 하려면 다음 단계를 수행 하 여 [**MixedReality**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-113">To detect and show the HP Reverb G2 controllers when using MRTK, follow these steps to install the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package.</span></span> <span data-ttu-id="d4b2c-114">이 패키지를 설치한 후에는 컨트롤러가 HP 반향에 표시 되도록 기본 프로필에 대 한 다른 변경 작업을 수행 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-114">Once this package is installed, no other changes to the default profiles need to be made to have the controllers show up on the HP Reverb.</span></span> 

<span data-ttu-id="d4b2c-115">편집기에서 컨트롤러를 표시 하려면 [**OpenXR 플러그 인**](/windows/mixed-reality/develop/unity/openxr-getting-started)을 사용 하 여를 사용 하 고 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-115">In order to display the controllers in editor, you need to ensure that you are using the using the [**OpenXR Plugin**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span></span>

## <a name="oculus-controllers"></a><span data-ttu-id="d4b2c-116">Oculus 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="d4b2c-116">Oculus Controllers</span></span> 

<span data-ttu-id="d4b2c-117">Oculus 컨트롤러 모델을 시각화 하려면 Oculus 퀘스트 배포 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-117">To visualize Oculus controller models, follow the Oculus Quest deployment instructions.</span></span> <span data-ttu-id="d4b2c-118">컨트롤러를 사용 하는 경우 가상 손을 표시 하려면 XR SDK Oculus 장치 관리자에서 **컨트롤러 대신 아바타 손을 렌더링** 하도록 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-118">If you wish to show virtual hands when using the controllers, make sure that **Render Avatar Hands Instead Of Controllers** is checked under the XR SDK Oculus Device Manager.</span></span> <span data-ttu-id="d4b2c-119">그렇지 않은 경우이 옵션을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b2c-119">Otherwise, uncheck this option.</span></span>

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)