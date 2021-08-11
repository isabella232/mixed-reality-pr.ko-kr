---
title: 도구 설명
description: MRTK의 도구 설명 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, 혼합 현실, 개발, mrtk, 도구 설명,
ms.openlocfilehash: af848db0962948b1f2ada73066c4ae90730b09a99dea231ebf468a05441b85ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193260"
---
# <a name="tooltip"></a>도구 설명

![도구 설명 주](../images/tooltip/MRTK_Tooltip_Main.png)

도구 설명은 일반적으로 개체를 자세히 검사할 때 힌트 또는 추가 정보를 전달 하는 데 사용 됩니다. 도구 설명을 사용 하 여 물리적 환경의 개체에 주석을 추가할 수 있습니다.

## <a name="how-to-use-a-tooltip"></a>도구 설명을 사용 하는 방법

도구 설명을 계층에 직접 추가 하 고 개체를 대상으로 지정할 수 있습니다.

이 방법을 사용 하려면 게임 개체와 도구 설명 prefabs (자산/MRTK/SDK/Features/UX/Prefabs/도구 설명) 중 하나를 장면 계층에 추가 하면 됩니다. Prefab의 검사기 패널에서 스크립트를 확장 합니다 [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) . 팁 상태를 선택 하 고 도구 설명을 구성 합니다.  텍스트 필드에 도구 설명에 해당 하는 텍스트를 입력 합니다. 스크립트를 확장 하 [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) 고 계층의 도구 설명을 포함 하는 개체를 *Target* 이라는 레이블이 있는 필드로 끕니다. 그러면 도구 설명이 개체에 연결 됩니다.
![도구 설명 연결선](../images/tooltip/MRTK_Tooltip_Connector.png)

이 사용에서는 도구 설명 구성 요소의 도구 설명 상태 속성을 변경 하 여 항상 표시 되거나 스크립트를 통해 표시 되는 도구 설명 이라고 가정 합니다.

## <a name="dynamically-spawning-tooltips"></a>동적으로 도구 설명 생성

도구 설명을 런타임에 개체에 동적으로 추가 하 고 탭 또는 포커스를 표시 하거나 숨기도록 미리 설정할 수 있습니다. 게임 개체에 스크립트를 추가 하기만 하면 됩니다 [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) . 표시 되는 지연 및 사라짐은 설정 된 기간 후에 도구 설명이 사라질 수 있도록 수명 뿐만 아니라 스크립트 검사기에서 설정할 수 있습니다. 도구 설명에는 spawner 스크립트의 배경 시각적 개체와 같은 기능 스타일 속성도 있습니다. 기본적으로 도구 설명은 spawner 스크립트를 사용 하 여 개체에 고정 됩니다. 이는 앵커 필드에 GameObject를 할당 하 여 변경할 수 있습니다.

## <a name="example-scene"></a>장면 예

예제 장면 (자산/m RTK/예제/데모/UX/도구 설명/장면)에서는 다양 한 도구 설명 예제를 찾을 수 있습니다.

![도구 설명 예](../images/tooltip/MRTK_Tooltip_Examples.png)
