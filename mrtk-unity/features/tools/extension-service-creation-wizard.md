---
title: 확장 서비스 만들기 마법사
description: 단일 항목에서 서비스 MRTK로 전환 하는 마법사에 대 한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 6b4efa39a99755f3c031757c7298465886d0c39512c93750f4653200edce9e17
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214299"
---
# <a name="extension-service-creation-wizard"></a>확장 서비스 만들기 마법사

단일 항목에서 서비스로 전환 하는 것은 어려울 수 있습니다. 이 마법사는 개발자를 사용 하 여 새 MonoBehaviour 스크립트를 만들 때와 동일한 방식으로 새 서비스를 만들 수 있도록 하 여 다른 설명서 및 샘플 코드를 보완할 수 있습니다. 서비스를 처음부터 만드는 방법에 대 한 자세한 내용은 [등록 된 서비스 구축 가이드](../../configuration/mixed-reality-configuration-guide.md) (서비스 예정)를 참조 하세요.

## <a name="launching-the-wizard"></a>마법사 시작

주 메뉴에서 마법사 시작: **MixedRealityToolkit/유틸리티/확장 서비스 만들기** -마법사는 서비스 스크립트, 인터페이스 및 프로필 클래스를 생성 하는 과정을 안내 합니다.

## <a name="editing-your-service-script"></a>서비스 스크립트 편집

기본적으로 새 스크립트 자산은 폴더에 생성 됩니다 `MixedRealityToolkit.Generated/Extensions` . 마법사를 완료 한 후 여기로 이동 하 여 새 서비스 스크립트를 엽니다.

생성 된 서비스 스크립트에는 새 MonoBehaviour 스크립트와 유사한 메시지가 포함 됩니다. 이를 통해 서비스를 초기화 하 고 업데이트할 위치를 알 수 있습니다.

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

마법사에서 서비스를 등록 하도록 선택한 경우이 스크립트만 편집 하면 되며 서비스는 자동으로 업데이트 됩니다. 그렇지 않으면 [여기에서 새 서비스를 등록](../../configuration/mixed-reality-configuration-guide.md)하는 방법에 대해 알아볼 수 있습니다.
