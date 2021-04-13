---
title: 시작 자습서 - 3. MRTK 프로필 구성
description: 이 과정에서는 MRTK(Mixed Reality Toolkit) 프로필을 구성하는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, 공간 인식
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300458"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. MRTK 프로필 구성

## <a name="overview"></a>개요

이 자습서에서는 MRTK 프로필을 사용자 지정하고 구성하는 방법을 알아봅니다.

<a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK 프로필</a>은 MRTK 시스템 및 기능을 초기화하는 방법에 대한 구성 정보를 구성하는 중첩된 프로필 트리입니다. 최상위 프로필인 Configuration Profile에는 각 기본 코어 시스템에 대한 중첩 프로필이 포함되어 있습니다. 각 중첩 프로필은 해당 시스템의 동작을 구성하도록 설계되었습니다.

이 예제에서는 공간 메시 관찰자의 설정을 변경하여 공간 인식 메시를 숨기는 방법을 보여줍니다. 그러나 MRTK 프로필의 설정 또는 값을 사용자 지정할 때 이러한 원칙을 그대로 적용해도 됩니다.

[이전 자습서](mr-learning-base-02.md#congratulations)에서 HoloLens 2에 프로젝트를 배포할 때처럼 <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">공간 인식</a> 메시는 환경의 기하 도형을 나타내는 메시 컬렉션입니다. 처음에 볼 때는 유용하지만, 시각적 산만함과 이 기능을 사용할 때의 추가 성능 저하를 피하기 위해 일반적으로 꺼져 있습니다.

## <a name="objectives"></a>목표

* MRTK 프로필을 사용자 지정 및 구성하는 방법 알아보기
* 공간 인식 메시 숨기기

## <a name="changing-the-spatial-awareness-display-option"></a>공간 인식 표시 옵션 변경

공간 인식 메시를 숨기기 위해 수행하는 주요 단계는 다음과 같습니다.

1. 기본 구성 프로필 복제
2. 공간 인식 시스템 사용
3. 기본 공간 인식 시스템 프로필 복제
4. 기본 공간 인식 메시 관찰자 프로필 복제
5. 공간 인식 메시의 표시 유형 변경

> [!NOTE]
> 기본적으로 MRTK 프로필은 편집할 수 없습니다. 이러한 기본 프로필 템플릿을 편집하려면 먼저 복제해야 합니다. 중첩된 여러 프로필 레이어가 있습니다. 따라서 하나 이상의 설정을 구성할 때 여러 프로필을 복제하여 편집하는 것이 일반적입니다.

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 MRTK 프로필 및 설정을 복제, 사용자 지정 및 구성하는 방법을 배웠습니다.

> [!div class="nextstepaction"]
> [다음 자습서: 4. 장면에서 개체 위치 지정](mr-learning-base-04.md)