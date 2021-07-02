---
title: 텍스트 prefab
description: MRTK의 TextPrefab 개요
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, mrtk, TMP,
ms.openlocfilehash: 1839109043cfad9a20697c5d6526b349fd7ea2e4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175641"
---
# <a name="text-prefab"></a>텍스트 prefab

이러한 prefabs는 Windows Mixed Reality의 렌더링 품질에 맞게 최적화 되어 있습니다. 자세한 내용은 Microsoft Windows 개발자 센터에서 [Unity의 지침 텍스트](/windows/mixed-reality/text-in-unity) 를 참조 하세요.

## <a name="prefabs"></a>Prefabs

### <a name="3dtextprefab"></a>3DTextPrefab

3D 텍스트 메시 prefab (자산/m RTK/SDK/StandardAssets/Prefabs/Text)는 2 미터 거리에서 최적화 된 배율 인수를 사용 합니다. (아래 지침을 참조 하세요.)

### <a name="uitextprefab"></a>UITextPrefab

UI 텍스트 메시 prefab (자산/m RTK/SDK/StandardAssets/Prefabs/Text)는 2 미터 거리에서 최적화 된 배율 인수를 사용 합니다. (아래 지침을 참조 하세요.)

## <a name="fonts"></a>글꼴

혼합 현실 Toolkit에 포함 된 오픈 소스 글꼴 (자산/MRTK/Core/StandardAssets/Fonts)입니다.

> [!IMPORTANT]
> 텍스트 Prefab는 오픈 소스 글꼴 ' Selawik '를 사용 합니다. 다른 글꼴로 텍스트 Prefab을 사용 하려면 글꼴 파일을 가져오고 아래 지침을 따르세요. 아래 예제에서는 텍스트 Prefab에 ' 맑은 고딕 ' 글꼴을 사용 하는 방법을 보여 줍니다.

![맑은 고딕 글꼴 파일 가져오기](../images/text-prefab/TextPrefabInstructions01.png)

1. 3DTextSegoeUI 재질에 글꼴 질감을 할당 합니다.

    ![글꼴 질감 할당](../images/text-prefab/TextPrefabInstructions02.png)

1. 3DTextSegoeUI 재질에서 셰이더 Custom/3DTextShader를 선택 합니다.

    ![셰이더 할당](../images/text-prefab/TextPrefabInstructions03.png)

1. Prefabs의 텍스트 구성 요소에 맑은 고딕 font 및 3DTextSegoeUI 재질을 할당 합니다.

    ![글꼴 파일 및 재질 할당](../images/text-prefab/TextPrefabInstructions04.png)

### <a name="working-with-fonts-in-unity"></a>Unity에서 글꼴 작업

Unity에서 장면에 새 3D TextMesh를 추가 하는 경우 시각적으로 눈에 띄는 두 가지 문제가 있습니다. 하나는 글꼴이 매우 크고 두 번 표시 되 면 글꼴이 매우 흐리게 표시 됩니다. 또한 검사기에서 기본 글꼴 크기 값이 0으로 설정 된 것을 알 수 있습니다. 이 값이 0 인 값을 13으로 바꾸면 13이 실제로 기본값 이기 때문에 크기 차이는 없습니다.

Unity는 장면에 추가 된 모든 새 요소가 1 개의 Unity 단위 또는 100% Transform 배율 (HoloLens에서 약 1 미터로 변환 됨) 이라고 가정 합니다. 글꼴의 경우 3D TextMesh의 경계 상자는 기본적으로 높이의 약 1 미터에 제공 됩니다.

### <a name="font-scale-and-font-sizes"></a>글꼴 배율 및 글꼴 크기

대부분의 비주얼 디자이너에서는 요소를 사용 하 여 실제 세계의 글꼴 크기와 디자인 프로그램을 정의 합니다. 1 미터에 약 2835 (2, 834.645666399962) 점이 있습니다. 1 미터에 대 한 시점 시스템 변환과 Unity의 기본 TextMesh 글꼴 크기인 13을 기반으로 하 여 2835 13의 단순 수학 13은 0.0046 (정확 하 게 0.004586111116)로 시작 하는 데 적합 한 표준 크기를 제공 합니다. 단, 일부는 0.005로 반올림 해야 할 수 있습니다.

어느 방법을 사용 하 든 텍스트 개체 또는 컨테이너를 이러한 값으로 크기를 조정 하면 디자인 프로그램에서의 글꼴 크기를 1:1으로 변환할 수 있을 뿐만 아니라 응용 프로그램 또는 게임 전체에서 일관성을 유지 하는 표준도 제공 됩니다.

### <a name="ui-text"></a>UI 텍스트

장면에 UI 또는 canvas 기반 텍스트 요소를 추가 하는 경우 차이가 크기는 더 커집니다. 두 크기의 차이점은 약 1000% 이며,이는 UI 기반 텍스트 구성 요소에 대 한 배율 인수를 0.00046 (정확 하 게 0.0004586111116) 또는 0.0005 (반올림 된 값)로 가져오는 것입니다.

고 **지** 사항: 글꼴의 기본값은 해당 글꼴의 질감 크기 또는 해당 글꼴을 Unity로 가져온 방법에 의해 영향을 받을 수 있습니다. 이러한 테스트는 Unity의 기본 Arial 글꼴 및 가져온 다른 글꼴을 기반으로 수행 되었습니다.

![크기 조정 요소를 사용 하는 글꼴 크기](../images/text-prefab/TextPrefabInstructions07.png)

### <a name="text3dselawikmat"></a>[Text3DSelawik](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/StandardAssets/Materials/)

3DTextPrefab에 대 한 자료는 폐색 지원 합니다. 3DTextShader 필요 합니다. 셰이더

![기본 글꼴 재질 vs 3DTextSegoeUI 재질](../images/text-prefab/TextPrefabInstructions06.png)

### <a name="text3dshadershader"></a>[Text3DShader](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/StandardAssets/Shaders)

폐색를 지 원하는 3DTextPrefab 용 셰이더.
