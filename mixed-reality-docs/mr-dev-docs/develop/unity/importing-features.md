---
title: 기능 가져오기
description: HoloLens 및 VR 개발용 MR Feature Tool에서 기능을 가져오고 설치하는 방법에 대해 알아봅니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: 6cf3712ce8029695076ceaec4191df53eb72789c62568206c056f1afc6c04c3b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225791"
---
# <a name="importing-features"></a>기능 가져오기

기능이 다운로드되면 검토하고 Unity 프로젝트로 가져올 수 있습니다. 이 단계에서는 애플리케이션 창이 다음 이미지와 같이 표시됩니다.

![기능 가져오기](images/FeatureToolImport.png)

## <a name="features-list"></a>Features list

**Features(기능)** 목록에는 검색 중에 선택된 패키지 컬렉션이 포함되어 있습니다. 가져오기 전에 각 기능을 선택하거나 선택 취소할 수 있습니다. 패키지 세부 정보는 아래와 같은 **Details(세부 정보)** 링크를 사용하여 볼 수 있습니다.

![Features list](images/FeaturesList.png)

## <a name="required-dependencies-list"></a>필수 종속성 목록

**필수 종속성** 목록에는 하나 이상의 선택된 기능이 작동하는 데 필요한 패키지가 포함되어 있습니다. 이 목록에는 종속성의 종속성도 포함됩니다. 가져오기 전에 각 종속성을 선택하거나 선택 취소할 수 있습니다. 패키지 세부 정보는 아래와 같은 **Details(세부 정보)** 링크를 사용하여 볼 수 있습니다.

![종속성 목록](images/RequiredDependencyList.png)

> [!NOTE]
> 필수 종속성을 선택 취소하면 Unity에서 프로젝트를 로드할 때 종속성이 하나 이상 누락되었다는 오류가 발생합니다. 이러한 기능은 프로젝트에서 사용할 수 없습니다.

## <a name="validating-selections"></a>선택 항목 유효성 검사

기능을 가져오기 전에 선택한 기능의 유효성을 검사하는 것이 좋습니다. 이 단계에서는 성공적인 프로젝트 개발에 방해가 될 수 있는 모든 문제를 발생시킵니다.

![유효성 검사 문제](images/ValidationIssues.png)

Mixed Reality Feature Tool은 두 가지 자동 문제 해결 방법(다음 섹션에서 설명) 및 문제를 수동으로 취소하고 해결하는 옵션을 제공합니다.

### <a name="enable-dependencies"></a>종속성 사용

**종속성 사용** 단추를 클릭하면 누락된 종속성이 자동으로 다시 선택됩니다. 이는 명시적으로 선택된 종속성(**기능** 목록에 표시됨)과 선택한 기능의 요구 사항에 따라 암시적으로 선택된 종속성에 대해 적용됩니다.

### <a name="disable-features"></a>기능 사용 안 함

**기능 사용 안 함** 을 선택하면 선택되지 않은 하나 이상의 종속성에 종속된 모든 기능이 자동으로 선택 취소됩니다. 이는 암시적으로 선택된 종속성 패키지 및 명시적으로 선택한 기능에 적용됩니다.

## <a name="importing"></a>가져오기

**가져오기** 를 선택하여 선택한 기능을 추가하고 [최종 승인](reviewing-changes.md) 후 대상 프로젝트를 업데이트합니다.

> [!IMPORTANT]
> 가져오는 동안 유효성 검사 문제가 계속되면 경고 메시지가 표시됩니다. [아니요]를 선택하고 **유효성 검사** 를 클릭하여 표시된 문제를 해결하는 것이 좋습니다.
>
> ![유효성 검사 문제 계속](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a>이전 단계로 돌아가기

**기능 가져오기** 에서 Mixed Reality Feature Tool을 사용하여 [탐색](discovering-features.md)으로 돌아갈 수 있습니다. **돌아가기** 를 선택하여 다른 기능 패키지를 다운로드합니다.

## <a name="see-also"></a>참조

- [Mixed Reality Feature Tool 시작](welcome-to-mr-feature-tool.md)
- [검색 및 가져오기](discovering-features.md)
- [기능 패키지 세부 정보 보기](viewing-package-details.md)
- [프로젝트 수정 내용 검토 및 승인](reviewing-changes.md)