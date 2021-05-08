---
title: TextPrefab
description: MRTK의 TextPrefab 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, TMP,
ms.openlocfilehash: 7d50a35e3761cf2313a43fcc6ad43ed5bd3064a1
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489293"
---
# <a name="text-prefab"></a>텍스트 prefab

이러한 prefabs은 Windows Mixed Reality의 렌더링 품질에 맞게 최적화 되어 있습니다. 자세한 내용은 Microsoft Windows 개발자 센터의 [Unity에서 지침 텍스트](/windows/mixed-reality/text-in-unity) 를 참조 하세요.

## <a name="prefabs"></a>Prefabs

### <a name="3dtextprefab"></a>3DTextPrefab

3D 텍스트 메시 prefab (자산/m RTK/SDK/StandardAssets/Prefabs/Text)는 2 미터 거리에서 최적화 된 배율 인수를 사용 합니다. (아래 지침을 참조 하세요.)

### <a name="uitextprefab"></a>UITextPrefab

UI 텍스트 메시 prefab (자산/m RTK/SDK/StandardAssets/Prefabs/Text)는 2 미터 거리에서 최적화 된 배율 인수를 사용 합니다. (아래 지침을 참조 하세요.)

## <a name="fonts"></a>글꼴

혼합 현실 도구 키트에 포함 된 오픈 소스 글꼴 (자산/MRTK/Core/StandardAssets/Fonts).

> [!IMPORTANT]
> 텍스트 Prefab는 오픈 소스 글꼴 ' Selawik '를 사용 합니다. 다른 글꼴로 텍스트 Prefab을 사용 하려면 글꼴 파일을 가져오고 아래 지침을 따르세요. 아래 예제에서는 텍스트 Prefab에 ' 맑은 고딕 ' 글꼴을 사용 하는 방법을 보여 줍니다.

![맑은 고딕 글꼴 파일 가져오기](../images/text-prefab/TextPrefabInstructions01.png)

1. 3DTextSegoeUI 재질에 글꼴 질감을 할당 합니다.

    ![글꼴 질감 할당](../images/text-prefab/TextPrefabInstructions02.png)

1. 3DTextSegoeUI.mat 재질에서 셰이더 Custom/3DTextShader.shader를 선택합니다.

    ![셰이더 할당](../images/text-prefab/TextPrefabInstructions03.png)

1. 맑은 고딕 글꼴 및 3DTextSegoeUI 재질을 프리팹의 텍스트 구성 요소에 할당합니다.

    ![글꼴 파일 및 재질 할당](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>Unity에서 글꼴 작업

Unity의 장면에 새 3D TextMesh를 추가할 때 시각적으로 명백한 두 가지 문제가 있습니다. 하나는 글꼴이 매우 크게 표시되고 두 글꼴은 매우 흐리게 표시됩니다. 검사기에서 기본 글꼴 크기 값이 0으로 설정되어 있는지도 흥미롭습니다. 실제로 13이 기본값이므로 이 0 값을 13으로 바치면 크기가 달라지지 않습니다.

Unity는 장면에 추가된 모든 새 요소의 크기가 1 Unity 단위 또는 100% 변환 배율로, HoloLens에서 약 1미터로 변환된다고 가정합니다. 글꼴의 경우 3D TextMesh에 대한 경계 상자가 기본적으로 약 1미터 높이로 제공됩니다.

### <a name="font-scale-and-font-sizes"></a>글꼴 배율 및 글꼴 크기

대부분의 비주얼 디자이너는 포인트 를 사용하여 실제 세계와 디자인 프로그램에서 글꼴 크기를 정의합니다. 1미터에는 약 2835(2,834.645666399962)의 지점이 있습니다. 포인트 시스템을 1미터로 변환하고 Unity의 기본 TextMesh 글꼴 크기 13을 기준으로 13을 2835로 나눈 간단한 수학은 0.0046(정확하게 0.00458611116)과 동일하지만 일부는 0.005로 반올림하려고 할 수 있지만 시작할 수 있는 좋은 표준 배율입니다.

어느 방법을 사용하든 Text 개체 또는 컨테이너를 이러한 값으로 확장하면 디자인 프로그램에서 글꼴 크기를 1:1로 변환할 수 있을 뿐만 아니라 애플리케이션 또는 게임 전체에서 일관성을 유지하는 표준을 제공합니다.

### <a name="ui-text"></a>UI 텍스트

장면에 UI 또는 캔버스 기반 Text 요소를 추가할 때 크기 차이는 여전히 더 커야 합니다. 두 크기의 차이는 약 1000%이며, 반올림된 값의 경우 UI 기반 Text 구성 요소의 배율 비율을 0.00046(0.0004586111116)으로 가져오거나 0.0005로 가져옵니다.

**고지 사항:** 모든 글꼴의 기본값은 해당 글꼴의 질감 크기 또는 글꼴을 Unity로 가져온 방법에 의해 영향을 받을 수 있습니다. 이러한 테스트는 Unity의 기본 Arial 글꼴 및 가져온 다른 글꼴을 기반으로 수행 되었습니다.

![크기 조정 요소를 사용 하는 글꼴 크기](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSelawik](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

3DTextPrefab에 대 한 자료는 폐색 지원 합니다. 3DTextShader 필요 합니다. 셰이더

![기본 글꼴 재질 vs 3DTextSegoeUI 재질](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

폐색를 지 원하는 3DTextPrefab 용 셰이더.