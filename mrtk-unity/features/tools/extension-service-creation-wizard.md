---
title: 확장 서비스 만들기 마법사
description: 단일 항목에서 서비스 MRTK로 전환 하는 마법사에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 4be9a58c7d63ab3bc93bcc326a90260cf6a3366b
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176612"
---
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="3620b-104">확장 서비스 만들기 마법사</span><span class="sxs-lookup"><span data-stu-id="3620b-104">Extension service creation wizard</span></span>

<span data-ttu-id="3620b-105">단일 항목에서 서비스로 전환 하는 것은 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3620b-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="3620b-106">이 마법사는 개발자를 사용 하 여 새 MonoBehaviour 스크립트를 만들 때와 동일한 방식으로 새 서비스를 만들 수 있도록 하 여 다른 설명서 및 샘플 코드를 보완할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3620b-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="3620b-107">서비스를 처음부터 만드는 방법에 대 한 자세한 내용은 [등록 된 서비스 구축 가이드](../../configuration/mixed-reality-configuration-guide.md) (서비스 예정)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3620b-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../configuration/mixed-reality-configuration-guide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="3620b-108">마법사 시작</span><span class="sxs-lookup"><span data-stu-id="3620b-108">Launching the wizard</span></span>

<span data-ttu-id="3620b-109">주 메뉴에서 마법사 시작: **MixedRealityToolkit/유틸리티/확장 서비스 만들기** -마법사는 서비스 스크립트, 인터페이스 및 프로필 클래스를 생성 하는 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="3620b-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="3620b-110">서비스 스크립트 편집</span><span class="sxs-lookup"><span data-stu-id="3620b-110">Editing your service script</span></span>

<span data-ttu-id="3620b-111">기본적으로 새 스크립트 자산은 폴더에 생성 됩니다 `MixedRealityToolkit.Generated/Extensions` .</span><span class="sxs-lookup"><span data-stu-id="3620b-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="3620b-112">마법사를 완료 한 후 여기로 이동 하 여 새 서비스 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3620b-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="3620b-113">생성 된 서비스 스크립트에는 새 MonoBehaviour 스크립트와 유사한 메시지가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3620b-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="3620b-114">이를 통해 서비스를 초기화 하 고 업데이트할 위치를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3620b-114">They will let you know where to initialize and update your service.</span></span>

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

<span data-ttu-id="3620b-115">마법사에서 서비스를 등록 하도록 선택한 경우이 스크립트만 편집 하면 되며 서비스는 자동으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3620b-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="3620b-116">그렇지 않으면 [여기에서 새 서비스를 등록](../../configuration/mixed-reality-configuration-guide.md)하는 방법에 대해 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3620b-116">Otherwise you can read about [registering your new service here](../../configuration/mixed-reality-configuration-guide.md).</span></span>
