---
title: Mixed Reality Feature Tool 시작
description: HoloLens 및 VR 개발용 MR Feature Tool의 기본 사항에 대해 알아봅니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: b9d54edb251cfe22d4f5fbea6fa8c923f6ff2d69
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244068"
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

환경을 설정한 후 다음을 수행합니다.

* [Microsoft 다운로드 센터](https://aka.ms/MRFeatureTool)에서 최신 버전의 Mixed Reality Feature Tool을 다운로드합니다.
* 다운로드가 완료되면 파일의 압축을 풀고 바탕 화면에 저장합니다.
    * 더 빠른 액세스를 위해 실행 파일에 대한 바로 가기를 만드는 것이 좋습니다.

## <a name="1-getting-started"></a>1. 시작

실행 파일에서 Mixed Reality Feature Tool을 시작합니다. 처음 시작하는 경우 시작 페이지가 표시됩니다.

![시작](images/FeatureToolStart.png)

시작 페이지에서 다음을 수행할 수 있습니다.

* **기어 아이콘** 단추를 사용하여 도구 설정 [구성](configuring-feature-tool.md)
* **물음표** 단추를 사용하여 기본 웹 브라우저를 시작하고 설명서 표시
* **Start(시작)** 를 선택하여 기능 패키지 검색 시작

## <a name="2-discovering-and-acquiring-feature-packages"></a>2. 기능 패키지 검색 및 가져오기

시작을 누르면 바로 기능 패키지 카탈로그가 검색됩니다. 기능이 범주별로 그룹화되어 있어 필요한 기능을 더 쉽게 찾을 수 있습니다. 예를 들어 **Mixed Reality Toolkit** 범주에는 선택할 수 있는 몇 가지 기능이 있습니다.

![검색 및 가져오기](images/FeatureToolDiscovery.png)

원하는 항목을 선택했으면 **Get features(기능 가져오기)** 를 선택하여 카탈로그에서 필요한 패키지를 모두 가져옵니다. 자세한 내용은 [기능 검색 및 가져오기](discovering-features.md)를 참조하세요.

## <a name="3-importing-feature-packages"></a>3. 기능 패키지 가져오기

가져오기가 완료되면 전체 패키지 집합이 필수 종속성 목록과 함께 표시됩니다. 기능 또는 패키지 선택 항목을 변경해야 한다면 이때 변경하는 것이 좋습니다.

![패키지 가져오기](images/FeatureToolImport.png)

**Validate(유효성 검사)** 단추를 사용하여 Unity 프로젝트에서 선택한 기능을 성공적으로 가져올 수 있는지 확인하는 것이 좋습니다. 유효성 검사가 완료되면 성공 메시지 또는 식별된 문제 목록이 포함된 팝업 대화 상자가 표시됩니다.

또한 가져오기 전에 대상 Unity 프로젝트의 위치를 설정해야 합니다. 프로젝트 경로 필드의 왼쪽에 있는 **줄임표** 단추를 사용하여 찾아보세요. 파일 시스템 탐색이 완료되면 대상 Unity 프로젝트를 포함하는 폴더를 엽니다.

> [!NOTE]
> Unity 프로젝트 폴더를 검색할 때 표시되는 대화 상자에는 파일 이름에 '_'가 포함됩니다. 파일 이름에 대한 값이 있어야 폴더를 선택할 수 있습니다.

**Import(가져오기)** 를 선택하여 계속합니다.

> [!NOTE]
> **Import(가져오기)** 단추를 클릭한 후에도 문제가 계속되면 단순 메시지가 표시됩니다. 아니요를 클릭하고 **Validate(유효성 검사)** 단추를 사용하여 문제를 확인하고 해결하는 것이 좋습니다.

자세한 내용은 [기능 가져오기](importing-features.md)를 참조하세요.

## <a name="4-reviewing-and-approving-project-changes"></a>4. 프로젝트 변경 내용 검토 및 승인

최종 단계는 매니페스트 및 프로젝트 파일에 대한 제안된 변경 내용을 검토하고 승인하는 것입니다.

* 매니페스트에 대한 제안된 변경 내용이 왼쪽에 표시됩니다.
* 프로젝트에 추가할 파일은 오른쪽에 나열됩니다.
* **Compare(비교)** 단추를 사용하여 현재 매니페스트 및 제안된 변경 내용을 나란히 볼 수 있습니다.

![권한 부여](images/FeatureToolApprovalRequest.png)

자세한 내용은 [프로젝트 수정 내용 검토 및 승인](reviewing-changes.md)을 참조하세요.

## <a name="5-project-updated"></a>5. 프로젝트 업데이트

제안된 변경 내용이 승인되면 선택된 혼합 현실 기능을 참조하도록 대상 Unity 프로젝트가 업데이트됩니다.

![프로젝트 업데이트](images/FeatureToolProjectUpdated.png)

Unity 프로젝트의 **Packages(패키지)** 폴더에는 이제 기능 패키지 파일과 함께 **MixedReality** 하위 폴더가 있으며, 매니페스트에는 적절한 참조가 포함됩니다.

Unity로 돌아가서 선택된 새 기능이 로드될 때까지 기다린 후 빌드를 시작합니다.

## <a name="see-also"></a>참조

- [기능 도구 구성](configuring-feature-tool.md)
- [검색 및 가져오기](discovering-features.md)
- [기능 패키지 세부 정보 보기](viewing-package-details.md)
- [선택한 패키지 가져오기](importing-features.md)
- [프로젝트 수정 내용 검토 및 승인](reviewing-changes.md)
