---
title: 단추
description: MRTK의 단추에 대 한 개요
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, MRTK 단추
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003118"
---
# <a name="button"></a>단추

![주 단추](../images/button/MRTK_Button_Main.png)

단추를 사용하면 즉각적인 작업을 트리거할 수 있습니다. 혼합 현실에서 가장 기본적인 구성 요소 중 하나입니다. MRTK는 다양 한 형식의 단추 prefabs 제공 합니다.

## <a name="button-prefabs-in-mrtk"></a>MRTK의 단추 prefabs

폴더 아래에 있는 단추 prefabs의 예 ``MRTK/SDK/Features/UX/Interactable/Prefabs``

### <a name="unity-ui-imagegraphic-based-buttons"></a>Unity UI 이미지/그래픽 기반 단추

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>Collider 기반 단추

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) PressableButtonHoloLens2 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) PressableButtonHoloLens2Unplated 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) PressableButtonHoloLens2Circular 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    테두리 밝은, 근접 조명 및 압축 된 front와 같은 다양 한 시각적 피드백을 지 원하는 백 판이 있는 HoloLens 2의 셸 스타일 단추
    :::column-end:::
    :::column:::
    HoloLens 2의 셸 스타일 단추 (backplate 불포함)
    :::column-end:::
    :::column:::
    원형 셰이프를 사용 하는 HoloLens 2의 셸 스타일 단추
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    ![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    광역 HoloLens 2의 셸 스타일 단추 32x96mm
    :::column-end:::
    :::column:::
    공유 백 판의 가로 HoloLens 2 단추 모음
    :::column-end:::
    :::column:::
    공유 백 판의 세로 HoloLens 2 단추 모음
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    HoloLens 2의 셸 스타일 확인란 32x32mm
    :::column-end:::
    :::column:::
    HoloLens 2의 셸 스타일 스위치 32x32mm 
    :::column-end:::
    :::column:::
    HoloLens 2의 셸 스타일 라디오 32x32mm
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96** 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    HoloLens 2의 셸 스타일 확인란 32x96mm
    :::column-end:::
    :::column:::
    HoloLens 2의 셸 스타일 스위치 32x96mm
    :::column-end:::
    :::column:::
    HoloLens 2의 셸 스타일 라디오 32x96mm
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![방사형 ](../images/button/MRTK_Button_Radial.png) **방사형**
    :::column-end:::
    :::column:::
    ![확인란](../images/button/MRTK_Button_Checkbox.png) **확인란**
    :::column-end:::
    :::column:::
    ![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    방사형 단추 
    :::column-end:::
    :::column:::
    확인란 
    :::column-end:::
    :::column:::
    토글 스위치
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**
    :::column-end:::
    :::column:::
    ![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton** 
    :::column-end:::
    :::column:::
    ![단추 기준 ](../images/button/MRTK_Button_Base.png) **단추**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    HoloLens 1 세대 셸 스타일 단추
    :::column-end:::
    :::column:::
    둥근 모양 푸시 단추
    :::column-end:::
    :::column:::
    기본 단추
    :::column-end:::
:::row-end:::

`Button`(자산/m a RTK/SDK/Features/UX/Interactable/Prefabs/prefab)는 [Interactable](interactable.md) 개념을 기반으로 하 여 단추 또는 다른 유형의 대화형 화면에 대 한 간편한 UI 컨트롤을 제공 합니다. 기준선 단추는 근접 한 상호 작용에 대 한 트레일러 입력을 포함 하는 모든 사용 가능한 입력 메서드를 지원 하며, 먼 상호 작용을 위해 응시 + 공기 탭도 지원 합니다. 음성 명령을 사용 하 여 단추를 트리거할 수도 있습니다.

`PressableButtonHoloLens2` (Asset/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2)는 직접 추적 입력 단추를 정확 하 게 이동할 수 있도록 하는 HoloLens 2의 셸 스타일 단추입니다. 스크립트 `Interactable` 와 스크립트를 결합 `PressableButton` 합니다.

HoloLens 2의 경우 불투명 backplate 사용 하는 단추를 사용 하는 것이 좋습니다. 투명 단추는 다음과 같은 유용성 및 안정성 문제로 인해 권장 되지 않습니다.

* 물리적 환경에서 아이콘 및 텍스트를 읽기 어렵습니다.
* 이벤트가 트리거되는 시기를 이해 하기 어렵습니다.
* 투명 평면을 통해 표시 되는 Holograms는 HoloLens 2의 깊이 LSR 안정화를 사용 하 여 불안정 해질 수 있습니다.

![Plated 단추](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>Pressable 단추를 사용 하는 방법

### <a name="unity-ui-based-buttons"></a>Unity UI 기반 단추

장면 (GameObject >-> Canvas)에서 캔버스를 만듭니다. 캔버스의 검사기 패널에서 다음을 수행 합니다.

* "MRTK 캔버스로 변환"을 클릭 합니다.
* "NearInteractionTouchableUnityUI 추가"를 클릭 합니다.
* Rect Transform 구성 요소의 X, Y 및 Z 소수 자릿수를 0.001으로 설정 합니다.

그런 다음 (asset/ `PressableButtonUnityUI` mrtk/sdk/features/ux/Interactable/Prefabs/prefab), `PressableButtonUnityUICircular` (asset/MRTK/Sdk/FEATURES/Ux/Interactable/Prefabs/PressableButtonUnityUICircular) 또는 `PressableButtonHoloLens2UnityUI` (ASSET/mrtk/sdk/features/ux/prefab/Interactable/Prefabs)를 캔버스에 끌어 놓습니다.

### <a name="collider-based-buttons"></a>Collider 기반 단추

(Asset `PressableButtonHoloLens2` /mrtk/sdk/features/ux/Interactable/Prefabs/PressableButtonHoloLens2) 또는 `PressableButtonHoloLens2Unplated` (자산/m RTK/Sdk/FEATURES/Ux/Interactable/Prefabs/PressableButtonHoloLens2Unplated)를 장면으로 끌어 놓기만 하면 됩니다. 이러한 단추 prefabs는 여러 개의 입력 형식에 대 한 오디오 시각적 피드백을 포함 하도록 이미 구성 되어 있습니다.

Prefab 자체와 [Interactable](interactable.md) 구성 요소에 노출 되는 이벤트를 사용 하 여 추가 작업을 트리거할 수 있습니다. [HandInteractionExample 장면의](../example-scenes/hand-interaction-examples.md) pressable 단추는 Interactable의 *OnClick* 이벤트를 사용 하 여 큐브의 색 변경을 트리거합니다. 이 이벤트는 pressable button 스크립트를 통해 실제 단추를 누르는 것 뿐만 아니라 응시, 공중 탭, 손으로 그린 등의 여러 입력 방법에 대해 트리거됩니다.

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

단추를 통해 pressable 단추가 *OnClick* 이벤트를 발생 시키는 시점을 구성할 수 있습니다 `PhysicalPressEventRouter` . 예를 들어 누름 시 이벤트를 *클릭* 하 여 *누르기* 를 설정 하는 대신 단추를 처음 누를 때 Interactable *를 실행 하도록 설정할 수* 있습니다.

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

특정 트레일러 식 입력 상태 정보를 활용 하려면 pressable buttons 이벤트- *터치 시작*, *터치 종료*, *단추 누름*, *단추* 를 사용할 수 있습니다. 그러나 이러한 이벤트는 공중 탭, 손 광선 또는 눈 입력에 대 한 응답으로 발생 하지 않습니다. **Near 및 far 상호 작용을 모두 지원 하려면 Interactable의 *OnClick* 이벤트를 사용 하는 것이 좋습니다.**

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a>상호 작용 상태

유휴 상태에서는 단추의 front 판이 표시 되지 않습니다. 손가락으로 나 응시 입력의 커서가 표면을 대상으로 하는 경우 front 판의 광선 테두리가 표시 됩니다. Front 판금 표면의 fingertip 위치를 추가로 강조 표시 합니다. 손가락이 푸시되 면 front 판금이 fingertip으로 이동 합니다. Fingertip는 프런트 판의 표면에 닿을 때 터치 점에 대 한 시각적 피드백을 제공 하기 위한 미묘한 펄스 효과를 보여 줍니다.

HoloLens 2 shell 스타일 단추에는 많은 시각적 신호 및 affordances 있어 사용자의 상호 작용에 대 한 신뢰도를 높일 수 있습니다.

|  ![근접 조명](../images/button/ux_button_affordance_proximitylight.jpg) | ![포커스 강조 표시](../images/button/ux_button_affordance_focushighlight.jpg)  | ![케이지 압축](../images/button/ux_button_affordance_compression.jpg) | ![펄스 on 트리거](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| 근접 조명 | 포커스 강조 표시 | 케이지 압축 | 펄스 on 트리거 |

미묘한 펄스 효과는 현재 상호 작용 하는 포인터에 살고 있는 *ProximityLight* 를 검색 하는 pressable 단추에 의해 트리거됩니다. 근접 조명이 발견 되 면 `ProximityLight.Pulse` 이 메서드를 호출 하 여 펄스를 표시 하는 셰이더 매개 변수에 자동으로 애니메이션 효과를 적용 합니다.

## <a name="inspector-properties"></a>Inspector 속성

![단추 구조](../images/button/MRTK_Button_Structure.png)

**상자 Collider** 
 `Box Collider` 단추의 front 플레이트입니다.

**Pressable 단추** 직접 누르기 상호 작용을 사용 하 여 단추 이동에 대 한 논리입니다.

**실제 누르기 이벤트 라우터** 이 스크립트는 [Interactable](interactable.md)에 대 한 직접 누르기 상호 작용에서 이벤트를 보냅니다.

**Interactable** 
 [Interactable](interactable.md) 는 다양 한 유형의 상호 작용 상태와 이벤트를 처리 합니다. HoloLens 응시, 제스처 및 음성 입력 및 몰입 형 헤드셋 동작 컨트롤러 입력은이 스크립트에 의해 직접 처리 됩니다.

**오디오 원본** 오디오 피드백 클립에 대 한 Unity 오디오 원본입니다.

*NearInteractionTouchable* 은 모든 개체를 touchable로 설정 하는 데 필요 합니다.

## <a name="prefab-layout"></a>Prefab 레이아웃

*Buttoncontent* 개체에는 front 판금, 텍스트 레이블 및 아이콘이 포함 되어 있습니다. *FrontPlate* 는 *Button_Box* 셰이더를 사용 하 여 인덱스 fingertip 근접에 응답 합니다. 빛나는 테두리, 근접 조명 및 터치에 대 한 펄스 효과를 표시 합니다. 텍스트 레이블은 TextMesh Pro를 사용 하 여 만들어집니다. *SeeItSayItLabel* 의 표시 유형은 [Interactable](interactable.md)의 테마에 의해 제어 됩니다.

![단추 레이아웃](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>아이콘 및 텍스트를 변경 하는 방법

MRTK 단추는 `ButtonConfigHelper` 구성 요소를 사용 하 여 단추의 아이콘, 텍스트 및 레이블을 변경 하는 데 도움을 줍니다. 선택 된 단추에 요소가 없는 경우 일부 필드는 없을 수 있습니다.

![단추 구성 도우미](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>아이콘 집합 만들기 및 수정

**아이콘 집합** 은 구성 요소에서 사용 하는 아이콘 자산의 공유 집합입니다 `ButtonConfigHelper` . 세 가지 아이콘 *스타일이* 지원 됩니다.

* **쿼드** 아이콘은를 사용 하 여 쿼드로 렌더링 됩니다 `MeshRenderer` . 기본 아이콘 스타일입니다.
* **스프라이트** 아이콘은를 사용 하 여 렌더링 됩니다 `SpriteRenderer` . 이 기능은 스프라이트 시트로 아이콘을 가져오거나 Unity UI 구성 요소와 아이콘 자산을 공유 하려는 경우에 유용 합니다. 이 스타일을 사용 하려면 스프라이트 편집기 패키지 **(Windows-> 패키지 관리자-> 2D 스프라이트)** 를 설치 해야 합니다.
* **문자** 아이콘은 구성 요소를 사용 하 여 렌더링 됩니다 `TextMeshPro` . 이는 아이콘 글꼴을 사용 하는 것이 좋습니다. HoloLens 아이콘 글꼴을 사용 하려면 `TextMeshPro` 글꼴 자산을 만들어야 합니다.

단추에 사용 되는 스타일을 변경 하려면 ButtonConfigHelper의 *아이콘* 드롭다운을 확장 하 고 *아이콘 스타일* 드롭다운에서를 선택 합니다.

자산 메뉴를 사용 하 여 새 단추 아이콘 집합을 만들 수 있습니다. **> Mixed Reality Toolkit > 아이콘 집합을 만듭니다.** 쿼드 및 스프라이트 아이콘을 추가 하려면 해당 하는 배열로 끌어 놓기만 하면 됩니다. 문자 아이콘을 추가 하려면 먼저 글꼴 자산을 만들고 할당 해야 합니다.

MRTK 2.4 이상에서는 사용자 지정 아이콘 질감이 IconSet로 이동 하는 것이 좋습니다.
프로젝트의 모든 단추에 대 한 자산을 새 권장 형식으로 업그레이드 하려면 ButtonConfigHelperMigrationHandler를 사용 합니다.
(혼합 현실 도구 키트-> 유틸리티-> 마이그레이션 창-> 마이그레이션 처리기 선택-> MixedReality)

단추를 업그레이드 하는 데 필요한 MixedRealityToolkit 패키지를 가져옵니다.

![업그레이드 창 대화 상자](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

마이그레이션 중에 기본 아이콘 집합에 아이콘이 없으면 사용자 지정 아이콘 집합이 MixedRealityToolkit/CustomIconSets에 생성 됩니다. 이 작업이 수행 되었음을 나타내는 대화 상자가 나타납니다.

![사용자 지정 아이콘 알림](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>HoloLens 아이콘 글꼴 자산 만들기

먼저 아이콘 글꼴을 Unity로 가져옵니다. Windows 컴퓨터에서는 *windows/Fonts/holomdl2* 에서 기본 HoloLens 글꼴을 찾을 수 있습니다. .ttf. 이 파일을 복사 하 여 자산 폴더에 붙여 넣습니다.

다음으로, **Window > TextMeshPro > Font Asset creator** 를 통해 TextMeshPro Font 자산 작성자를 엽니다. HoloLens 글꼴 아틀라스를 생성 하기 위한 권장 설정은 다음과 같습니다. 모든 아이콘을 포함 하려면 다음 유니코드 범위를 *문자 시퀀스* 필드에 붙여넣습니다.

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![단추 만들기 1](../images/button/MRTK_Font_Asset_Creation_1.png)

글꼴 자산이 생성 되 면 프로젝트에 저장 하 고 아이콘 집합의 *Char 아이콘 글꼴* 필드에 할당 합니다. 이제 *사용 가능한 아이콘* 드롭다운이 채워집니다. 단추에서 아이콘을 사용할 수 있도록 하려면 해당 아이콘을 클릭 합니다. *선택한 아이콘* 드롭다운에 추가 되며, 필요에 따라 `ButtonConfigHelper.` 아이콘에 태그를 지정할 수 있습니다. 이렇게 하면 런타임에 아이콘을 설정할 수 있습니다.

![단추 생성 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![단추 생성 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

아이콘 집합을 사용 하려면 단추를 선택 하 고에서 아이콘 드롭다운을 확장 `ButtonConfigHelper` 한 다음 *아이콘 집합* 필드에 할당 합니다.

![단추 아이콘 집합](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>단추 크기를 변경 하는 방법

HoloLens 2의 셸 스타일 단추 크기는 32x32mm입니다. 차원을 사용자 지정 하려면 prefab 단추에서 이러한 개체의 크기를 변경 합니다.

1. **FrontPlate**
2. 백 판금에서 **쿼드**
3. 루트의 **Box Collider**

그런 다음 단추의 루트에 있는 NearInteractionTouchable 스크립트에서 **범위 고정** 단추를 클릭 합니다.

FrontPlate ![ 단추 크기 사용자 지정 1의 크기를 업데이트 합니다.](../images/button/MRTK_Button_SizeCustomization1.png)

4 ![ 단추 크기 사용자 지정 2의 크기를 업데이트 합니다.](../images/button/MRTK_Button_SizeCustomization2.png)

상자 Collider ![ Button 크기 사용자 지정 3 상자 크기를 업데이트 합니다.](../images/button/MRTK_Button_SizeCustomization3.png)

' 범위 수정 ' ![ 단추 크기 사용자 지정 4를 클릭 합니다.](../images/button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it"></a>음성 명령 (' 참조-it ')

**음성 입력 처리기** Pressable의 [Interactable](interactable.md) 스크립트는 이미을 구현 `IMixedRealitySpeechHandler` 합니다. 음성 명령 키워드는 여기에서 설정할 수 있습니다.

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

**음성 입력 프로필** 또한 전역 *음성 명령 프로필* 에 음성 명령 키워드를 등록 해야 합니다.

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

**참조-it 레이블** Pressable button prefab에는 *SeeItSayItLabel* 개체 아래에 자리 표시자 Textmesh Pro 레이블이 있습니다. 이 레이블을 사용 하 여 단추에 대 한 음성 명령 키워드를 사용자에 게 전달할 수 있습니다.

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a>단추를 처음부터 만드는 방법

이러한 단추의 예는 **보도 Sablebuttonexample** 장면에서 찾을 수 있습니다.

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1. cube를 사용 하 여 pressable 단추 만들기 (근거리 상호 작용에만 해당)

1. Unity 큐브 만들기 (GameObject > 3D 개체 > 큐브)
2. `PressableButton.cs`스크립트 추가
3. `NearInteractionTouchable.cs`스크립트 추가

`PressableButton`의 검사기 패널에서 큐브 개체를 **이동 단추 시각적** 개체에 할당 합니다.

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

큐브를 선택 하면 개체에 색이 지정 된 여러 계층이 표시 됩니다. 그러면 **누름 설정** 에서 거리 값이 시각화 됩니다. 핸들을 사용 하 여 누르기를 시작할 시기 (개체 이동)와 이벤트를 트리거할 시기를 구성할 수 있습니다.

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

단추를 누르면 `PressableButton.cs` TouchBegin (), TouchEnd (), ButtonPressed (), Buttonpressed ()와 같은 스크립트에 노출 된 적절 한 이벤트가 이동 하 여 생성 됩니다.

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a>문제 해결

단추에서 두 번 누르기를 실행 하는 경우에는 **Front Push 적용** 속성이 활성 상태이 고 **푸시 거리** 평면이 **근접 한 상호 작용 Touchable** 평면 앞에 배치 되어 있는지 확인 합니다. **근접 한 상호 작용 Touchable** 평면은 아래 gif에서 흰색 화살표의 원점 앞에 놓인 파란색 평면으로 표시 됩니다.

![Front Push 속성이 강조 표시 된 Pressable button 스크립트 구성 요소](../images/button/MRTK_Button_Enforce_Push.png)

![근접 한 상호 작용 touchable 평면 앞에서 시작 푸시 거리를 이동 하는 애니메이션 예제](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2. 기본 큐브에 시각적 피드백 추가 단추

MRTK 표준 셰이더는 시각적 피드백을 쉽게 추가할 수 있게 해 주는 다양 한 기능을 제공 합니다. 재질을 만들고 셰이더를 선택 `Mixed Reality Toolkit/Standard` 합니다. 또는에서 MRTK 표준 셰이더를 사용 하는 기존 자료 중 하나를 사용 하거나 복제할 수 있습니다 `/SDK/StandardAssets/Materials/` .

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

`Hover Light` `Proximity Light` **흐름 옵션** 을 선택 합니다. 이를 통해 근거리 (근접 조명)와 원거리 포인터 (가리키기 광원) 상호 작용에 대 한 시각적 피드백을 사용할 수 있습니다.

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3. 기본 큐브에 오디오 피드백 추가 단추

`PressableButton.cs`스크립트는 TouchBegin (), TouchEnd (), ButtonPressed (), Buttonpressed ()와 같은 이벤트를 노출 하므로 오디오 피드백을 쉽게 할당할 수 있습니다. `Audio Source`큐브 개체에 Unity를 추가 하 고 PlayOneShot ()를 선택 하 여 오디오 클립을 할당 하기만 하면 됩니다. 폴더에서 MRTK_Select_Main 및 MRTK_Select_Secondary 오디오 클립을 사용할 수 있습니다 `/SDK/StandardAssets/Audio/` .

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4. 시각적 상태 추가 및 far 상호 작용 이벤트 처리

[Interactable](interactable.md) 는 다양 한 유형의 입력 상호 작용에 대 한 시각적 상태를 쉽게 만들 수 있도록 해 주는 스크립트입니다. 또한 먼 상호 작용 이벤트를 처리 합니다. `Interactable.cs`큐브 개체를 추가 하 여 **프로필** 의 **대상** 필드에 끌어다 놓습니다. 그런 다음 **ScaleOffsetColorTheme** 형식으로 새 테마를 만듭니다. 이 테마에서 **포커스** 및 **눌린** 특정 상호 작용 상태에 대 한 개체의 색을 지정할 수 있습니다. 크기 조정 및 오프셋도 제어할 수 있습니다. **감속/가속** 을 선택 하 고 시각적 전환을 매끄럽게 하기 위해 기간을 설정 합니다.

![프로필 테마 선택](../images/button/mrtk_button_profiles.gif)

개체가 far (손 모양 또는 응시 커서)와 근거리 (손) 상호 작용에 응답 하는 것을 볼 수 있습니다.

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a>사용자 지정 단추 예제

[HandInteractionExample 장면](../example-scenes/hand-interaction-examples.md)에서를 사용 하는 피아노 및 round 단추 예를 참조 하세요 `PressableButton` .

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

각 피아노 키에는 `PressableButton` 및 `NearInteractionTouchable` 스크립트가 할당 되어 있습니다. 의 *로컬 정방향* 방향이 올바른지 확인 하는 것이 중요 `NearInteractionTouchable` 합니다. 편집기에서 흰색 화살표로 표시 됩니다. 화살표가 단추의 정면 면을 가리키는지 확인 합니다.

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a>참조

* [상호 작용 가능](interactable.md)
* [시각적 개체 테마](visual-themes.md)
