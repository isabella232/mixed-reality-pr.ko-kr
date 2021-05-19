---
title: 확장 서비스 만들기 마법사
description: 싱글톤에서 서비스 MRTK로 전환하기 위한 마법사 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 83797a9d6d465a150406b27162a5e84c157567f1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143543"
---
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="e3263-104">확장 서비스 만들기 마법사</span><span class="sxs-lookup"><span data-stu-id="e3263-104">Extension service creation wizard</span></span>

<span data-ttu-id="e3263-105">싱글톤에서 서비스로 전환하는 것은 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3263-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="e3263-106">이 마법사는 개발자가 새 MonoBehaviour 스크립트를 만드는 것과 거의 동일한 용이성을 사용하여 새 서비스를 만들 수 있도록 하여 다른 설명서 및 샘플 코드를 보완할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3263-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="e3263-107">서비스를 처음부터 만드는 방법에 대한 자세한 내용은 등록된 서비스 빌드 가이드(출시 예정)를 참조하세요. [](../../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="e3263-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../configuration/mixed-reality-configuration-guide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="e3263-108">마법사 시작</span><span class="sxs-lookup"><span data-stu-id="e3263-108">Launching the wizard</span></span>

<span data-ttu-id="e3263-109">주 메뉴에서 마법사를 시작합니다. **MixedRealityToolkit/Utilities/Create Extension Service** - 마법사는 서비스 스크립트, 인터페이스 및 프로필 클래스를 생성하는 프로세스를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="e3263-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="e3263-110">서비스 스크립트 편집</span><span class="sxs-lookup"><span data-stu-id="e3263-110">Editing your service script</span></span>

<span data-ttu-id="e3263-111">기본적으로 새 스크립트 자산은 `MixedRealityToolkit.Generated/Extensions` 폴더에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3263-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="e3263-112">마법사를 완료했으면 여기로 이동하여 새 서비스 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e3263-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="e3263-113">생성된 서비스 스크립트에는 새 MonoBehaviour 스크립트와 유사한 몇 가지 프롬프트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3263-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="e3263-114">서비스를 초기화하고 업데이트할 위치를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3263-114">They will let you know where to initialize and update your service.</span></span>

```csharp
namespace Microsoft.MixedReality.Toolkit.Extensions
{
    [MixedRealityExtensionService(SupportedPlatforms.WindowsStandalone|SupportedPlatforms.MacStandalone|SupportedPlatforms.LinuxStandalone|SupportedPlatforms.WindowsUniversal)]
    public class NewService : BaseExtensionService, INewService, IMixedRealityExtensionService
    {
        private NewServiceProfile newServiceProfile;

        public NewService(IMixedRealityServiceRegistrar registrar,  string name,  uint priority,  BaseMixedRealityProfile profile) : base(registrar, name, priority, profile) 
        {
            newServiceProfile = (NewServiceProfile)profile;
        }

        public override void Initialize()
        {
            // Do service initialization here.
        }

        public override void Update()
        {
            // Do service updates here.
        }
    }
}
```

<span data-ttu-id="e3263-115">마법사에서 서비스를 등록하도록 선택한 경우 이 스크립트를 편집하기만 하면 서비스가 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3263-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="e3263-116">그렇지 않으면 여기에서 [새 서비스 등록에](../../configuration/mixed-reality-configuration-guide.md)대해 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3263-116">Otherwise you can read about [registering your new service here](../../configuration/mixed-reality-configuration-guide.md).</span></span>
