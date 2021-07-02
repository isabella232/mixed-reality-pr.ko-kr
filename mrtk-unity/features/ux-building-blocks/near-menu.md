---
title: Near 메뉴
description: MRTK의 메뉴 형식 근처에서 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 주변 메뉴,
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175654"
---
# <a name="near-menu"></a>Near 메뉴

![Near 메뉴](../images/near-menu/MRTK_UX_NearMenu.png)

Near Menu는 단추나 다른 UI 구성 요소의 컬렉션을 제공 하는 UX 컨트롤입니다. 사용자의 본문 주위에 떠 있고 언제 든 지 쉽게 액세스할 수 있습니다. 사용자와 느슨하게 연결 되어 있으므로 대상 콘텐츠와의 상호 작용을 방해 하지 않습니다. 사용자는 ' 고정 ' 단추를 사용 하 여 전 세계의 메뉴 잠금/잠금 해제를 사용할 수 있습니다. 메뉴를 grabbed 하 고 특정 위치에 배치할 수 있습니다.

## <a name="interaction-behavior"></a>상호 작용 동작

- **태그** 표시:이 메뉴는 사용자를 따르며 가까운 상호 작용을 위해 사용자의 30-60cm 범위 내에 유지 됩니다.
- **고정**: ' 핀 ' 단추를 사용 하 여 메뉴를 전 세계에서 잠그고 해제할 수 있습니다.
- **잡기 및 이동**: 메뉴는 항상 grabbable 및 이동 가능 합니다. 이전 상태와 관계 없이 grabbed 및 해제 된 경우 메뉴가 고정 (세계 잠금) 됩니다. Grabbable 영역에 대 한 시각적 단서가 있습니다. 이는 가까이에 표시 됩니다.

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a>Prefabs

Near 메뉴 prefabs는 MRTK의 다양 한 구성 요소를 사용 하 여 거의 상호 작용 하는 메뉴를 만드는 방법을 보여 주기 위해 디자인 되었습니다.

- **NearMenu2x4. prefab**
- **NearMenu3x1. prefab**
- **NearMenu3x2. prefab**
- **NearMenu3x3. prefab**
- **NearMenu4x1. prefab**
- **NearMenu4x2. prefab**

## <a name="example-scene"></a>장면 예

장면에서 메뉴 prefabs 근처의 예제를 찾을 수 있습니다 `NearMenuExamples` .

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a>구조체

Near 메뉴 prefabs 다음 MRTK 구성 요소를 사용 하 여 수행 됩니다.

- [**PressableButtonHoloLens2**](button.md) prefab
- [**Grid 개체 컬렉션**](object-collection.md): 모눈의 여러 단추 레이아웃
- [**조작 처리기**](manipulation-handler.md): 메뉴를 잡고 이동 합니다.
- [**RadialView 해 찾기**](solvers/solver.md): 팔 로우 하기 (태그 동반) 동작

![메뉴 Prefab 가까이](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>사용자 지정 방법

**1. 단추 추가/제거**

개체 아래에서 `ButtonCollection` 단추를 추가 하거나 제거 합니다.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

**2. 그리드 개체 컬렉션 업데이트**

`Update Collection`개체의 검사기에서 단추를 클릭 `ButtonCollection` 합니다. 그리드 레이아웃이 업데이트 됩니다.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

Grid 개체 컬렉션의 속성을 사용 하 여 행 수를 구성할 수 있습니다 `Rows` .  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

**3. backplate 크기 조정**

개체의 크기를 조정 `Quad` 합니다 `Backplate` . Backplate의 너비와 높이는 이어야 합니다 `0.032 * [Number of the buttons + 1]` . 예를 들어 3 개의 x 단추가 있는 경우 backplate의 너비는이 `0.032 * 4` 고 높이는 `0.032 * 3` 입니다. Unity의 필드에이 식을 직접 입력할 수 있습니다.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- HoloLens 2 단추의 기본 크기는 3.2 x 3.2 cm (0.032 m)입니다.

## <a name="see-also"></a>참조

- [**단추**](button.md)
- [**범위 제어**](bounds-control.md)
- [**슬라이더**](sliders.md)
- [**Grid 개체 컬렉션**](object-collection.md)
- [**조작 처리기**](manipulation-handler.md)
- [**RadialView 해 찾기**](solvers/solver.md)
