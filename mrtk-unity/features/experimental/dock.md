---
title: Dock
description: Dock 컨트롤에 대한 설명입니다.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 4446dbe3199aab63d7ee85474d3696a45cf4401f1d8100a8d99885a7265c7fe2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226575"
---
# <a name="dock"></a>Dock

![Dock](../images/dock/MRTK_UX_Dock_Main.png)

이 컨트롤을 사용하면 미리 결정된 위치 안팎으로 개체를 이동하여 색상표, 보류 및 탐색 모음을 만들 수 있습니다.

## <a name="features"></a>기능

- 여러 도킹 위치 및 레이아웃을 지원합니다(에서 잘 [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 작동).
- 도킹된 개체가 자동으로 이동되어 새 개체에 대한 공간을 확보합니다.
- 개체는 도킹된 공간에 맞게 크기를 조정한 다음, 끌어서 놓으면 원래 위치로 크기를 조정합니다.

## <a name="getting-started-with-dock"></a>Dock 시작

- Dock 구성 요소를 사용하여 GameObject를 만들고 일부 자식 GameObjects를 추가합니다.
- 각 자식에 DockPosition 구성 요소를 추가합니다.
- 도킹 가능한 구성 요소를 장면의 여러 개체에 추가하여 도킹할 수 있도록 합니다. [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator)구성 요소와 충돌체도 있어야 합니다.
- *선택 사항:* [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) 도킹에 를 사용하여 DockPositions를 자동으로 레이아웃합니다.

### <a name="prerequisites"></a>필수 조건

- 도킹 가능한 모든 개체에는 또는 가 있는 충돌체가 있어야 [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) 합니다.
- 장면 로드 시 개체가 도킹을 시작하도록 하려면 DockPosition의 도킹된 개체 속성에 할당합니다.

## <a name="how-it-works"></a>작동 방식

도킹 가능한 구성 요소는 끌기된 개체를 특정 위치에서 도킹 및 도킹 해제할 수 있도록 조작 이벤트를 기반으로 합니다. 배치는 끌어 온 개체에 대해 가장 겹치는 트리거된 DockPosition에 의해 결정되므로 두 개체 모두 트리거를 활성화하기 위해 충돌체가 있어야 합니다.
