---
title: Mixed Reality Feature Tool 시작
description: HoloLens 및 VR 개발용 MR Feature Tool의 기본 사항에 대해 알아봅니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: 4e822f2dda2a314ce06bc394a4d92b1aa6953af3
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772416"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a>Mixed Reality Feature Tool 시작

![Mixed Reality Feature Tool 배너 이미지](images/feature-tool-banner.png)

> [!IMPORTANT]
> Mixed Reality Feature Tool은 현재 Unity에서만 사용할 수 있습니다. Unreal에서 개발 중인 경우 [도구 설치](../install-the-tools.md) 설명서를 참조하세요.

Mixed Reality Feature Tool은 개발자가 혼합형 현실 기능 패키지를 검색 및 업데이트하고 Unity 프로젝트에 추가하는 데 사용되는 새로운 방법입니다. 이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다. 이전에 매니페스트 파일을 사용한 적이 없다면 모든 프로젝트 패키지를 포함하는 JSON 파일입니다. 원하는 패키지의 유효성을 검사하면 Mixed Reality Feature Tool에서 사용자가 선택한 프로젝트로 해당 패키지를 다운로드합니다.

## <a name="system-requirements"></a>시스템 요구 사항

Mixed Reality Feature Tool을 실행하려면 다음이 필요합니다.

* [.NET 5.0 런타임](https://dotnet.microsoft.com/download/dotnet/5.0)
* [Windows 10](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> Mixed Reality Feature Tool은 현재 Windows에서만 실행되지만 MacOS 지원이 곧 제공될 예정입니다.

## <a name="download"></a>다운로드

환경을 설정한 후 다음을 수행합니다.

* Microsoft 다운로드 센터에서 [최신 버전의 Mixed Reality Feature Tool을 다운로드합니다](https://aka.ms/MRFeatureTool).
* 다운로드가 완료되면 파일의 압축을 풀고 바탕 화면에 저장합니다.
    * 더 빠른 액세스를 위해 실행 파일에 대한 바로 가기를 만드는 것이 좋습니다.

> [!NOTE]
> Unity 패키지 관리자를 처음 사용하는 경우 [UPM 지침](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager)을 따르세요.

## <a name="changes-in-this-release"></a>이 릴리스의 변경 내용:

버전 1.0.2103 베타에는 다음 수정 사항이 포함되어 있습니다.

* 다운로드 오류 검색 기능이 향상되었습니다.
* 올바르게 업데이트되도록 하기 위해 매니페스트를 작성하는 방법에 대한 업데이트입니다.
* 이스케이프가 프로젝트 매니페스트의 파일 경로에서 제거되었습니다.

이 릴리스에는 다음과 같은 기능이 추가되었습니다.

* 기능 카탈로그가 이제 캐시됩니다. 새 기능 및 업데이트를 확인하려면 검색에서 새로 고침 단추를 사용하세요.
* 가져오기 단계에서 검색 이전으로 프로젝트 선택을 이동합니다.
* 사용 가능한 패키지는 프로젝트의 지정된 Unity 버전을 기준으로 필터링됩니다.
* 이제 검색 뷰에 현재 설치된 패키지가 표시됩니다.

## <a name="1-getting-started"></a>1. 시작

실행 파일에서 Mixed Reality Feature Tool을 시작합니다. 처음 시작하는 경우 시작 페이지가 표시됩니다.

![시작](images/FeatureToolStart.png)

시작 페이지에서 다음을 수행할 수 있습니다.

* **기어 아이콘** 단추를 사용하여 도구 설정 [구성](configuring-feature-tool.md)
* **물음표** 단추를 사용하여 기본 웹 브라우저를 시작하고 설명서 표시
* **Start(시작)** 를 선택하여 기능 패키지 검색 시작

## <a name="2-selecting-your-unity-project"></a>2. Unity 프로젝트 선택

발견된 모든 기능이 Unity의 프로젝트 버전에서 지원되는지 확인하려면 첫 번째 단계는 프로젝트 경로 필드 오른쪽에 있는 **줄임표** 단추를 사용하여 Mixed Reality Feature Tool을 프로젝트로 지정하는 것입니다.

![Unity 프로젝트 선택](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> Unity 프로젝트 폴더를 검색할 때 표시되는 대화 상자에는 파일 이름에 '_'가 포함됩니다. 파일 이름에 대한 값이 있어야 폴더를 선택할 수 있습니다.

프로젝트의 폴더를 찾았으면 열기 단추를 클릭하여 Mixed Reality Feature Tool로 돌아갑니다.

> [!IMPORTANT]
> Mixed Reality Feature Tool은 유효성 검사를 수행하여 Unity 프로젝트 폴더로 지정되었는지 확인합니다. 폴더에는 `Assets`, `Packages` 및 `Project Settings` 폴더가 있어야 합니다.

## <a name="3-discovering-and-acquiring-feature-packages"></a>3. 기능 패키지 검색 및 가져오기

> [!NOTE]
> 이제 버전 1.0.2103 베타에서 서버에 액세스할 때마다 기능 카탈로그 콘텐츠를 캐시합니다. 이러한 변경을 통해 절대 최신 데이터를 표시하는 대신 사용 가능한 기능에 빠르게 액세스할 수 있습니다. 카탈로그를 업데이트하려면 **새로 고침** 단추를 사용하세요.

기능이 범주별로 그룹화되어 있어 필요한 기능을 더 쉽게 찾을 수 있습니다. 예를 들어 **Mixed Reality Toolkit** 범주에는 선택할 수 있는 몇 가지 기능이 있습니다.

![검색 및 가져오기](images/FeatureToolDiscovery.png)

Mixed Reality Feature Tool은 이전에 가져온 기능을 인식하는 경우 각각에 의해 알림 메시지를 표시합니다.

![가져온 기능 알림](images/feature-tool-imported-note.png)


원하는 항목을 선택했으면 **Get features(기능 가져오기)** 를 선택하여 카탈로그에서 필요한 패키지를 모두 가져옵니다. 자세한 내용은 [기능 검색 및 가져오기](discovering-features.md)를 참조하세요.

## <a name="4-importing-feature-packages"></a>4. 기능 패키지 가져오기

가져오기가 완료되면 전체 패키지 집합이 필수 종속성 목록과 함께 표시됩니다. 기능 또는 패키지 선택 항목을 변경해야 한다면 이때 변경하는 것이 좋습니다.

![패키지 가져오기](images/FeatureToolImport.png)

**Validate(유효성 검사)** 단추를 사용하여 Unity 프로젝트에서 선택한 기능을 성공적으로 가져올 수 있는지 확인하는 것이 좋습니다. 유효성 검사가 완료되면 성공 메시지 또는 식별된 문제 목록이 포함된 팝업 대화 상자가 표시됩니다.

**Import(가져오기)** 를 선택하여 계속합니다.

> [!NOTE]
> **Import(가져오기)** 단추를 클릭한 후에도 문제가 계속되면 단순 메시지가 표시됩니다. 아니요를 클릭하고 **Validate(유효성 검사)** 단추를 사용하여 문제를 확인하고 해결하는 것이 좋습니다.

자세한 내용은 [기능 가져오기](importing-features.md)를 참조하세요.

## <a name="5-reviewing-and-approving-project-changes"></a>5. 프로젝트 변경 내용 검토 및 승인

최종 단계는 매니페스트 및 프로젝트 파일에 대한 제안된 변경 내용을 검토하고 승인하는 것입니다.

* 매니페스트에 대한 제안된 변경 내용이 왼쪽에 표시됩니다.
* 프로젝트에 추가할 파일은 오른쪽에 나열됩니다.
* **Compare(비교)** 단추를 사용하여 현재 매니페스트 및 제안된 변경 내용을 나란히 볼 수 있습니다.

![권한 부여](images/FeatureToolApprovalRequest.png)

자세한 내용은 [프로젝트 수정 내용 검토 및 승인](reviewing-changes.md)을 참조하세요.

## <a name="6-project-updated"></a>6. 프로젝트 업데이트

제안된 변경 내용이 승인되면 선택된 Mixed Reality 기능을 참조하도록 대상 Unity 프로젝트가 업데이트됩니다.

![프로젝트 업데이트](images/FeatureToolProjectUpdated.png)

Unity 프로젝트의 **Packages(패키지)** 폴더에는 이제 기능 패키지 파일과 함께 **MixedReality** 하위 폴더가 있으며, 매니페스트에는 적절한 참조가 포함됩니다.

Unity로 돌아가서 선택된 새 기능이 로드될 때까지 기다린 후 빌드를 시작합니다.

## <a name="see-also"></a>참조

- [기능 도구 구성](configuring-feature-tool.md)
- [검색 및 가져오기](discovering-features.md)
- [기능 패키지 세부 정보 보기](viewing-package-details.md)
- [선택한 패키지 가져오기](importing-features.md)
- [프로젝트 수정 내용 검토 및 승인](reviewing-changes.md)