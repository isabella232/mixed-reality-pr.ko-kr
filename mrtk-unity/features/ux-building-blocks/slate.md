---
title: 슬레이트
description: MRTK의 슬레이트 설명서
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 슬레이트,
ms.openlocfilehash: 6bc1f18c71367ce05aadae0ff3f8aa51fd17d10c943022525fc5043d8d7989a2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224027"
---
# <a name="slate"></a>슬레이트

![슬레이트](../images/slate/MRTK_Slate_Main.png)

슬레이트 prefab는 2D 콘텐츠 (예: 일반 텍스트 또는 미디어를 포함 하는 문서)를 표시 하기 위한 씬 창 스타일 컨트롤을 제공 합니다. Grabbable 제목 표시줄 뿐만 아니라 *추가* 기능 및 *닫기* 기능을 제공 합니다. 내용 창은 트레일러 식 입력을 통해 스크롤할 수 있습니다.

## <a name="how-to-use-a-slate-control"></a>슬레이트 컨트롤을 사용 하는 방법

슬레이트 컨트롤은 다음 요소로 구성 됩니다.

* **TitleBar**: 슬레이트 위에 있는 전체 제목 표시줄입니다.
* **제목**: 제목 표시줄의 왼쪽에 있는 제목 영역입니다.
* **Buttons**: 제목 표시줄의 오른쪽에 있는 단추 영역입니다.
* **Backplate**: 슬레이트의 뒷면입니다.
* **Contentquad**: 콘텐츠가 자료로 할당 됩니다. 이 예제에서는 샘플 재질 ' s e r t e r '를 사용 합니다.

<img src="../images/slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Structure in the Unity editor">

## <a name="bounds-control"></a>경계 컨트롤

슬레이트 컨트롤에는 크기 조정 및 회전을 위한 경계 제어 스크립트가 포함 되어 있습니다. 범위 컨트롤에 대 한 자세한 내용은 [경계 컨트롤](bounds-control.md) 페이지를 참조 하세요.

<img src="../images/slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a>단추

표준 슬레이트는 제목 표시줄의 오른쪽 위에 다음과 같은 두 개의 단추를 기본으로 제공 합니다.

* **팔 로우** 하기: 궤도 해 찾기 구성 요소를 전환 하 여 슬레이트 개체가 사용자에 게 따르도록 합니다.
* **Close**: 슬레이트 개체를 사용 하지 않도록 설정 합니다.

<img src="../images/slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Button">

## <a name="scripts"></a>스크립트

일반적으로 스크립트는 `NearInteractionTouchable.cs` 에서 터치 이벤트를 수신 하려는 모든 개체에 연결 되어야 합니다 `IMixedRealityTouchHandler` .

<img src="../images/slate/MRTK_Slate_Scripts.png" alt="Slate Structure">

* `HandInteractionPan.cs` 이 스크립트는 슬레이트의 *Contentquad* 에서 콘텐츠를 터치 하 고 이동 하기 위한 트레일러 식 입력을 처리 합니다.

* `HandInteractionPanZoom.cs`: 패닝 상호 작용 외에도이 스크립트는 두 가지 확대 확대/축소를 지원 합니다.

<img src="../images/slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate Pan Zooming">
