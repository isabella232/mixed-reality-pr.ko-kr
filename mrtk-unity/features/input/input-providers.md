---
title: 입력 공급자
description: MRTK의 다양한 입력 공급자 유형에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: f53932b5e12e60b3638c1d6c31e569016de983ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176750"
---
# <a name="input-providers"></a><span data-ttu-id="f5023-104">입력 공급자</span><span class="sxs-lookup"><span data-stu-id="f5023-104">Input providers</span></span>

<span data-ttu-id="f5023-105">입력 공급자는 Mixed Reality Toolkit 구성 요소에 있는 **등록된 서비스 공급자 프로필** 에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5023-105">Input providers are registered in the **Registered Service Providers Profile**, found in the Mixed Reality Toolkit component:</span></span>

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

<span data-ttu-id="f5023-106">다음은 해당 컨트롤러와 함께 사용할 수 있는 입력 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="f5023-106">These are the input providers available out of the box, together with their corresponding controllers:</span></span>

| <span data-ttu-id="f5023-107">입력 공급자</span><span class="sxs-lookup"><span data-stu-id="f5023-107">Input Provider</span></span> | <span data-ttu-id="f5023-108">Controllers</span><span class="sxs-lookup"><span data-stu-id="f5023-108">Controllers</span></span> |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | <span data-ttu-id="f5023-109">시뮬레이션된 손</span><span class="sxs-lookup"><span data-stu-id="f5023-109">Simulated Hand</span></span> |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | <span data-ttu-id="f5023-110">마우스</span><span class="sxs-lookup"><span data-stu-id="f5023-110">Mouse</span></span>  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | <span data-ttu-id="f5023-111">일반 OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span><span class="sxs-lookup"><span data-stu-id="f5023-111">Generic OpenVR, Vive Wand, Vive Knuckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR</span></span>  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | <span data-ttu-id="f5023-112">제네릭 틱</span><span class="sxs-lookup"><span data-stu-id="f5023-112">Generic Joystick</span></span>  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | <span data-ttu-id="f5023-113">Unity Touch Controller</span><span class="sxs-lookup"><span data-stu-id="f5023-113">Unity Touch Controller</span></span>  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | <span data-ttu-id="f5023-114">*없음*</span><span class="sxs-lookup"><span data-stu-id="f5023-114">*None*</span></span>  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | <span data-ttu-id="f5023-115">WMR 조인된 손, WMR 컨트롤러, WMR GGV(응시, 제스처 및 음성) 손</span><span class="sxs-lookup"><span data-stu-id="f5023-115">WMR Articulated Hand, WMR Controller, WMR GGV (Gaze, Gesture, and Voice) Hand</span></span> |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | <span data-ttu-id="f5023-116">*없음*</span><span class="sxs-lookup"><span data-stu-id="f5023-116">*None*</span></span> |

<span data-ttu-id="f5023-117">받아쓰기 및 음성 공급자는 컨트롤러를 만들지 않고 고유한 특수 입력 이벤트를 직접 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f5023-117">Dictation and Speech providers don't create any controllers, they raise their own specialized input events directly.</span></span>

<span data-ttu-id="f5023-118">인터페이스를 구현하여 사용자 지정 입력 공급자를 만들 수 [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5023-118">Custom input providers can be created by implementing the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface.</span></span>

<span data-ttu-id="f5023-119">자세한 내용은 입력 [시스템 데이터 공급자 만들기를](create-data-provider.md)참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f5023-119">For more information, please see [creating an input system data provider](create-data-provider.md).</span></span>
