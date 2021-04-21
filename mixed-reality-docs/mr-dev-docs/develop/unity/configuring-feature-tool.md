---
title: Mixed Reality Feature Tool 구성
description: HoloLens 및 VR 개발용 MR Feature Tool에서 Mixed Reality Unity 패키지를 다운로드하고 설치하는 방법에 대해 알아봅니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731952"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Mixed Reality Feature Tool 구성

Mixed Reality Feature Tool을 사용하는 경우 다음과 같은 세 가지 설정 범주에 액세스하여 원하는 대로 사용자 지정할 수 있습니다.

* [다운로드 설정](#download-settings)
* [기능 설정](#feature-settings)
* [설정 가져오기](#import-settings)

## <a name="download-settings"></a>다운로드 설정

![다운로드 설정](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a>기존 패키지 파일 덮어쓰기

이 설정을 사용하도록 설정하면 패키지 파일을 가져올 때마다 패키지 파일이 다운로드됩니다. 

* **네트워크 대역폭 사용량을 줄이려면 이 옵션을 사용하지 않도록 설정하는 것이 좋습니다.**
* 기본적으로 이전에 가져온 기능 패키지 파일은 다시 다운로드되지 않습니다.

### <a name="package-cache"></a>패키지 캐시

기능 패키지가 다운로드되는 위치를 업데이트하려면 이 설정을 변경합니다.

> [!NOTE]
> 이 릴리스에서 이 설정은 **읽기 전용** 입니다. 이후 릴리스에서는 이 설정을 구성할 수 있게 될 수도 있습니다.

## <a name="feature-settings"></a>기능 설정

![기능 설정](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a>미리 보기 릴리스 표시

미리 보기 릴리스를 가져오려면 이 설정을 사용하도록 설정합니다.
* 기본적으로 미리 보기 릴리스는 Mixed Reality Feature Tool에 표시되지 않습니다. 

> [!NOTE]
> 미리 보기 릴리스란 패키지 버전에 **"-preview"** 가 지정된 것을 말합니다.

### <a name="show-early-access-program-features"></a>조기 액세스 프로그램 기능 표시

등록된 조기 액세스 프로그램 릴리스에서 기능을 가져오려면 이 설정을 사용합니다.

* 기본적으로 조기 액세스 기능은 Mixed Reality 기능 도구에 표시되지 않습니다. 

> [!NOTE]
> `Show preview releases`없이 `Show early access program features`를 사용하면 조기 액세스 패키지가 검색에 표시되지 않을 수 있습니다.

## <a name="import-settings"></a>설정 가져오기

![설정 가져오기](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a>기존 패키지 파일 바꾸기

기본적으로 Mixed Reality Feature Tool은 가져올 패키지의 이전 복사본을 제거하여 파일 크기와 불필요한 계산을 줄입니다. 

* 모든 버전을 유지하려면 이 설정을 선택 취소합니다.

### <a name="project-relative-import-path"></a>프로젝트 기준 가져오기 경로

가져올 때 기능 패키지가 복사되는 프로젝트 폴더 경로를 업데이트하려면 이 설정을 변경합니다. 

* 예를 들어 프로젝트 폴더가 **C:\GalaxyExplorer** 일 경우 정규화된 가져오기 경로는 **C:\GalaxyExplorer\Packages\MixedReality** 가 됩니다.

> [!NOTE]
> 이 릴리스에서 이 설정은 **읽기 전용** 입니다. 이후 릴리스에서는 이 설정을 구성할 수 있게 될 수도 있습니다.

## <a name="early-access-settings"></a>조기 액세스 설정

![조기 액세스 설정](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a>조기 액세스 프로그램을 제거하기 전에 확인 요청

이 설정은 조기 액세스 프로그램을 제거할 때마다 프롬프트를 표시할지 여부를 결정합니다.

### <a name="my-previews"></a>내 미리 보기

등록된 조기 액세스 프로그램 목록입니다. `Add`, `Edit` 및 `Remove`를 사용하여 등록된 프로그램 컬렉션을 관리합니다.

## <a name="diagnostic-settings"></a>진단 설정

![진단 설정](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a>로그 파일

진단 로그 파일의 경로를 표시합니다.

## <a name="see-also"></a>참조

- [Mixed Reality Feature Tool 시작](welcome-to-mr-feature-tool.md)