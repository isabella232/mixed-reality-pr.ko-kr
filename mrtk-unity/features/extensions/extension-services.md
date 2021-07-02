---
title: 확장 서비스
description: MRTK의 확장된 기능에 대한 설명서
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: f8f7b8dbac0355c226e4bbfae39246e5c1c58f69
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176269"
---
# <a name="extension-services"></a><span data-ttu-id="dd0ce-104">확장 서비스</span><span class="sxs-lookup"><span data-stu-id="dd0ce-104">Extension services</span></span>

<span data-ttu-id="dd0ce-105">확장 서비스는 Mixed Reality Toolkit 기능을 확장하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="dd0ce-106">이러한 서비스는 MRTK 또는 다른 당사자가 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="dd0ce-107">확장 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="dd0ce-107">Creating an extension service</span></span>

<span data-ttu-id="dd0ce-108">확장 서비스를 만드는 가장 효율적인 방법은 [확장 서비스 만들기 마법사](../tools/extension-service-creation-wizard.md)를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../tools/extension-service-creation-wizard.md).</span></span>
<span data-ttu-id="dd0ce-109">확장 서비스 만들기 마법사를 시작하려면 **Mixed Reality Toolkit > 유틸리티 > 확장 서비스 만들기를** 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![확장 서비스 만들기 마법사](../images/extension-wizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="dd0ce-111">마법사는 서비스 구성 요소 생성을 자동화하고 적절한 인터페이스 상속을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![확장 서비스 만들기 마법사에서 만든 구성 요소](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="dd0ce-113">MRTK 버전 2.0.0에서는 확장 서비스 마법사에서 서비스 검사자 및 서비스 프로필을 생성해야 하는 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="dd0ce-114">자세한 내용은 문제 [5654를](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="dd0ce-115">마법사가 완료되면 서비스 기능을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="dd0ce-116">확장 서비스 등록</span><span class="sxs-lookup"><span data-stu-id="dd0ce-116">Registering an extension service</span></span>

<span data-ttu-id="dd0ce-117">애플리케이션에서 액세스할 수 있도록 하려면 새 확장 서비스를 Mixed Reality Toolkit 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="dd0ce-118">확장 서비스 만들기 마법사를 사용하여 서비스를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-118">The extension service creation wizard can be used to register the service.</span></span>

![확장 서비스 만들기 마법사 등록](../images/extension-wizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="dd0ce-120">Mixed Reality Toolkit 구성 검사기를 사용하여 서비스를 수동으로 등록할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![수동 확장 서비스 등록](../images/profiles/RegisterExtensionService.png)

<span data-ttu-id="dd0ce-122">확장 서비스에서 프로필을 사용하는 경우 검사기에서 프로필을 지정했는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![구성된 확장 서비스](../images/profiles/ConfiguredExtensionService.png)

<span data-ttu-id="dd0ce-124">구성 요소 이름 및 우선 순위를 조정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="dd0ce-125">확장 서비스 액세스</span><span class="sxs-lookup"><span data-stu-id="dd0ce-125">Accessing an extension service</span></span>

<span data-ttu-id="dd0ce-126">아래 예제와 같이 를 사용하여 코드에서 확장 서비스에 [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="dd0ce-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="dd0ce-127">참조</span><span class="sxs-lookup"><span data-stu-id="dd0ce-127">See also</span></span>

- [<span data-ttu-id="dd0ce-128">시스템, 확장 서비스 및 데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="dd0ce-128">Systems, extension services and data providers</span></span>](../../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="dd0ce-129">확장 서비스 만들기 마법사</span><span class="sxs-lookup"><span data-stu-id="dd0ce-129">Extension service creation wizard</span></span>](../tools/extension-service-creation-wizard.md)
- [<span data-ttu-id="dd0ce-130">IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="dd0ce-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="dd0ce-131">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="dd0ce-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
