---
title: 프레임워크 및 런타임
description: MRTK의 프레임워크 및 런타임과 관련된 정보입니다.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121611"
---
# <a name="framework-and-runtime"></a><span data-ttu-id="3926e-104">프레임워크 및 런타임</span><span class="sxs-lookup"><span data-stu-id="3926e-104">Framework and runtime</span></span>

## <a name="changes-to-the-scene"></a><span data-ttu-id="3926e-105">장면 변경 내용</span><span class="sxs-lookup"><span data-stu-id="3926e-105">Changes to the scene</span></span>

<span data-ttu-id="3926e-106">도구 키트를 사용하려면 MixedRealityToolkit 스크립트의 인스턴스가 장면에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-106">To use the toolkit an instance of the MixedRealityToolkit script must be in your scene.</span></span>
<span data-ttu-id="3926e-107">추가하려면 메뉴 옵션인 Mixed Reality Toolkit -> 장면에 추가 및 구성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-107">To add one use the menu option: Mixed Reality Toolkit -> Add to Scene and Configure.</span></span> <span data-ttu-id="3926e-108">이 인스턴스는 서비스 등록, 업데이트 및 해체를 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-108">This instance is responsible for registering, updating and tearing down services.</span></span> <span data-ttu-id="3926e-109">구성 프로필이 선택되는 위치이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-109">It's also where your configuration profile is chosen.</span></span>

<span data-ttu-id="3926e-110">MRTK GameObject를 장면에 추가하는 것 외에도 메뉴 옵션도 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-110">Apart from adding the MRTK GameObject to the scene the menu option will also:</span></span>

- <span data-ttu-id="3926e-111">다른 많은 MRTK 구성 요소에서 전 세계 및 로컬 공간 변환을 추론하는 데 사용되는 MixedRealityPlayspace를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-111">Add the MixedRealityPlayspace, which is used by many other MRTK components to reason over world and local space transformations.</span></span>
- <span data-ttu-id="3926e-112">MixedRealityPlayspace의 자식으로 기본 카메라를 이동합니다(또한 UnityUI 및 응시 관련 입력 기능을 구동하는 데 도움이 되는 일부 입력 및 응시 관련 스크립트를 기본 카메라에 추가).</span><span class="sxs-lookup"><span data-stu-id="3926e-112">Move the main Camera as a child of the MixedRealityPlayspace (and also adding some input and gaze related scripts to the main Camera, which help power UnityUI and gaze related input functionality).</span></span>

## <a name="mixedrealitytoolkit-object-and-runtime"></a><span data-ttu-id="3926e-113">MixedRealityToolkit 개체 및 런타임</span><span class="sxs-lookup"><span data-stu-id="3926e-113">MixedRealityToolkit object and runtime</span></span>

<span data-ttu-id="3926e-114">MRTK에는 몇 가지 핵심 서비스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-114">The MRTK has several core services.</span></span> <span data-ttu-id="3926e-115">일부 좌표는 서로 조정합니다. 다른 것은 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-115">Some coordinate with one another; others are independent.</span></span>
<span data-ttu-id="3926e-116">모두 시작, 등록, 업데이트 및 해체와 같은 수명 주기를 공유하며, 이 수명 주기는 Unity의 MonoBehaviour 수명 주기와는 별개입니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-116">All share the same life cycle - startup, registration, update and teardown - and this life cycle stands apart from Unity's MonoBehaviour life cycle.</span></span> <span data-ttu-id="3926e-117">이 [중간 게시물에서는](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) 이 접근 방식의 배경과 동기 중 일부를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-117">This [medium post](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explains some of the background and motivation behind this approach.</span></span> <span data-ttu-id="3926e-118">MRTK에는 서비스의 수명 및 런타임을 관리하는 단일 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-118">MRTK has a single object that manages life and runtime of its services.</span></span>

<span data-ttu-id="3926e-119">이 엔터티는 다음을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-119">This entity ensures that:</span></span>

- <span data-ttu-id="3926e-120">게임이 시작되면 서비스의 검색 및 초기화가 미리 정의된 순서로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-120">when the game starts, discovery and initialization of services happens in a pre-defined order.</span></span>
- <span data-ttu-id="3926e-121">서비스가 스스로 등록하고(즉, "이 서비스를 지원합니다!") 다른 호출자가 해당 서비스를 보류할 수 있는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-121">it provides a mechanism for services to register themselves (i.e. “I support this service!”) and for other callers to get a hold of those services.</span></span>
- <span data-ttu-id="3926e-122">Update()/LateUpdate() 호출을 제공하고 다양한 서비스(즉, UpdateAllServices/LateUpdateAllServices를 통해)로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="3926e-122">it provides the Update()/LateUpdate() calls and forwards them onto the various services (i.e. via UpdateAllServices/LateUpdateAllServices).</span></span>
