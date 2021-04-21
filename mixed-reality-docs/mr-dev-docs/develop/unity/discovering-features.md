---
title: 기능 검색 및 가져오기
description: 혼합 현실 기능을 검색하고 다운로드합니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: 9f12a1eba0c28b89000f1541ba62747a03e3564b
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/19/2021
ms.locfileid: "107732011"
---
# <a name="discovering-and-acquiring-features"></a>기능 검색 및 가져오기

이 문서의 섹션에서는 Mixed Reality Feature Tool에서 기능 패키지를 찾는 방법을 간략하게 설명합니다. 특정 섹션에 대한 참조 정보가 필요한 경우 아래 스크린샷을 확인하세요.

![기능 검색](images/FeatureToolDiscovery.png)

## <a name="available-features"></a>사용 가능한 기능

### <a name="category"></a>범주

Mixed Reality Feature Tool은 원하는 항목을 쉽게 찾을 수 있도록 기능 범주 컬렉션을 표시합니다. 범주를 확장하면 사용 가능한 기능 컬렉션이 표시됩니다.

> [!NOTE]
> 원하는 기능을 찾을 수 없다면 **기타 기능** 을 확인하세요.

![기능 범주](images/FeatureCategory.png)

위의 스크린샷에서 범주 헤더에 포함되는 속성을 왼쪽에서 오른쪽 방향으로 나열하면 다음과 같습니다.

- 확장 및 축소 단추
- 범주 이름(예: Mixed Reality Toolkit)
- 선택한 기능 수
- 사용 가능한 기능 수
- 섹션 단추

> [!NOTE]
> 선택 단추는 상황에 따라 달라집니다. 범주 내의 기능 선택 상태에 따라 하나 이상의 `Select All` 및 `Select None` 단추가 표시됩니다.

### <a name="feature"></a>기능

![기능 항목](images/FeatureEntry.png)

기능은 해당 범주에 나열됩니다. 위의 스크린샷에서 기능 항목에 포함되는 요소를 왼쪽에서 오른쪽 방향으로 나열하면 다음과 같습니다.

- 선택 확인란
- 기능 이름(예: Mixed Reality Toolkit Foundation)
- 사용 가능한 버전 목록
- [기능 패키지 세부 정보](viewing-package-details.md)에 대한 링크

> [!NOTE]
> 조기 액세스(개인 미리 보기라고도 함) 프로그램에서 기능을 제공하는 경우 ![조기 액세스](images/EarlyAccess.png) 표시기 아이콘이 표시됩니다.

## <a name="refresh-the-feature-catalog"></a>기능 카탈로그 새로 고침

새 기능 및 업데이트된 기능을 확인하려면 새로 고침을 클릭합니다. ![새로 고침 단추](images/RefreshButton.png) 단추를 선택합니다. 그러면 카탈로그 사이트에 연결되고 최신 정보가 검색됩니다. 카탈로그를 읽으면 마지막 업데이트 날짜 및 시간이 표시됩니다.

## <a name="select-features"></a>기능 선택

범주를 확장하고, 버전을 선택하고, 확인란을 클릭하여 기능을 선택합니다.

![선택한 기능](images/SelectedFeatures.png)

범주 내의 모든 패키지를 선택하기 위해 `Select All` 단추가 제공됩니다. `Select None`은 선택한 모든 패키지를 선택 취소합니다. 

하나 이상의 기능이 선택된 각 범주가 업데이트되고 개수가 표시됩니다.

## <a name="acquiring-features"></a>기능 가져오기

기능을 선택한 후 **Get features(기능 가져오기)** 를 선택하면 선택한 기능 패키지 파일의 다운로드가 시작됩니다.

> [!NOTE]
> 기본적으로 이전에 가져온 기능 패키지 파일은 다시 다운로드되지 않습니다. 이 동작을 변경하려면 [기능 도구 구성](configuring-feature-tool.md)을 참조하세요.

다운로드가 완료되면 Mixed Reality Feature Tool이 [기능 가져오기](importing-features.md) 단계로 이동합니다.

## <a name="going-back-to-the-previous-step"></a>이전 단계로 돌아가기

**Discover features(기능 검색)** 에서 Mixed Reality Feature Tool을 사용하여 프로젝트 선택으로 다시 돌아갈 수 있습니다. **Go back(돌아가기)** 을 선택하여 다시 시작합니다.

## <a name="see-also"></a>참조

- [Mixed Reality Feature Tool 시작](welcome-to-mr-feature-tool.md)
- [기능 도구 구성](configuring-feature-tool.md)
- [기능 패키지 세부 정보 보기](viewing-package-details.md)
- [선택한 패키지 가져오기](importing-features.md)
