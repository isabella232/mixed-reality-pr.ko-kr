---
ms.openlocfilehash: 695db2d7e6765d3584c9e9a6459071ab537c1f003d13461ce5736481b98b7495
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202801"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

MRTK를 사용하여 **새 Unity 프로젝트를** 시작하려면 MRTK 자습서의 2단계부터 시작합니다.

> [!div class="nextstepaction"]
> [MRTK를 통해 새 OpenXR 프로젝트 설정](../../tutorials/mr-learning-base-02.md?tabs=openxr)

**기존 MRTK 프로젝트를 OpenXR로** 업그레이드하는 경우 먼저 MRTK-Unity 최신 버전(버전 2.7.2 이상)으로 업그레이드하여 Mixed Reality OpenXR 플러그 인과의 호환성을 위한 주요 수정 사항을 얻을 수 있습니다.  Mixed Reality [기능 도구를](../../welcome-to-mr-feature-tool.md) 사용하여 최신 버전의 MRTK로 업그레이드한 다음 [아래의 수동 OpenXR 설치 단계를 따릅니다.](#manual-setup-without-mrtk) 기존 MRTK [프로젝트를 OpenXR로 마이그레이션하는 자세한 내용은 MRTK](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)설명서를 참조하세요.

> [!NOTE]
> **2.5.3** 이전 버전의 MRTK에서 업그레이드하는 경우 다음 줄이 **Assets/MixedRealityToolkit.Generated/link.xml** 파일에 있는지 확인합니다.
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> MRTK 2.5.4 이상으로 시작한 경우 이 줄이 기본적으로 추가됩니다.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

MRTK를 사용하여 **새 Unity 프로젝트를** 시작하려면 MRTK 자습서의 2단계부터 시작합니다.

> [!div class="nextstepaction"]
> [MRTK를 Windows 새 XR 프로젝트 설정](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[Legacy XR](#tab/legacy)

MRTK를 사용하여 **새 Unity 프로젝트를** 시작하려면 MRTK 자습서의 2단계부터 시작합니다.

> [!div class="nextstepaction"]
> [MRTK를 통해 새 레거시 XR 프로젝트 설정](../../tutorials/mr-learning-base-02.md?tabs=wsa)