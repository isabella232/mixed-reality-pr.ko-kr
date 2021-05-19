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
# <a name="extension-service-creation-wizard"></a>확장 서비스 만들기 마법사

싱글톤에서 서비스로 전환하는 것은 어려울 수 있습니다. 이 마법사는 개발자가 새 MonoBehaviour 스크립트를 만드는 것과 거의 동일한 용이성을 사용하여 새 서비스를 만들 수 있도록 하여 다른 설명서 및 샘플 코드를 보완할 수 있습니다. 서비스를 처음부터 만드는 방법에 대한 자세한 내용은 등록된 서비스 빌드 가이드(출시 예정)를 참조하세요. [](../../configuration/mixed-reality-configuration-guide.md)

## <a name="launching-the-wizard"></a>마법사 시작

주 메뉴에서 마법사를 시작합니다. **MixedRealityToolkit/Utilities/Create Extension Service** - 마법사는 서비스 스크립트, 인터페이스 및 프로필 클래스를 생성하는 프로세스를 안내합니다.

## <a name="editing-your-service-script"></a>서비스 스크립트 편집

기본적으로 새 스크립트 자산은 `MixedRealityToolkit.Generated/Extensions` 폴더에 생성됩니다. 마법사를 완료했으면 여기로 이동하여 새 서비스 스크립트를 엽니다.

생성된 서비스 스크립트에는 새 MonoBehaviour 스크립트와 유사한 몇 가지 프롬프트가 포함됩니다. 서비스를 초기화하고 업데이트할 위치를 알 수 있습니다.

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

마법사에서 서비스를 등록하도록 선택한 경우 이 스크립트를 편집하기만 하면 서비스가 자동으로 업데이트됩니다. 그렇지 않으면 여기에서 [새 서비스 등록에](../../configuration/mixed-reality-configuration-guide.md)대해 읽을 수 있습니다.
