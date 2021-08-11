---
title: PC 홀로그램 원격 시작
description: 이 과정을 완료하여 혼합 현실 애플리케이션을 PC에서 HoloLens 2로 원격으로 수행하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, PC 홀로그램 원격, 도구 설명, 시선 추적
ms.localizationpriority: high
ms.openlocfilehash: 3a8c409d06861d99a217dcf4e670a9aa543b441c352ea68bc738779a3f779046
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225550"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a>1. PC 홀로그램 원격 시작

HoloLens 2 자습서를 시작합니다. 2부로 구성된 이 자습서 시리즈에서는 혼합 현실 환경 데모를 만드는 방법 및 홀로그램 원격을 위한 PC 앱에 대해 알아봅니다.

[홀로그램 원격의 기본 사항에 대해 알아봅니다.](../../platform-capabilities-and-apis/holographic-remoting-overview.md)

이 자습서에서는 혼합 현실 환경을 만드는 방법에 대해 알아봅니다. 여기서는 UI 요소, 3D 모델 조작, 모델 클리핑 및 시선 추적 기능을 시연합니다.

두 번째 자습서인 [홀로그램 원격 애플리케이션 만들기](mr-learning-pc-holographic-remoting-02.md)에서는 홀로그램 원격을 사용하는 PC 앱을 만드는 방법을 학습하여 진행 중인 작업을 HoloLens로 스트리밍하여 먼저 빌드하지 않고도 볼 수 있습니다.

## <a name="objectives"></a>목표

* 자산 가져오기 및 장면 설정
* UI 요소 및 단추를 사용하여 홀로그램과 상호 작용
* 클리핑 기능에 대한 3D 개체 구성
* 시선 추적을 사용하여 도구 설명을 활성화하는 방법 알아보기

## <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 PC
* 기본적인 C# 프로그래밍 지식
* [개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>(Unity 2020/2019 LTS가 탑재되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가되어 있음)

계속하기 전에 [시작](mr-learning-base-01.md) 자습서 시리즈 또는 Unity 및 MRTK에 대한 기본적인 사전 경험을 완료할 것을 **강력히 권장** 합니다.

> [!IMPORTANT]
> * 이 자습서 시리즈는 Open XR을 사용하는 경우 Unity 2020 LTS(현재 2020.3.x)를 지원하고 레거시 WSA를 사용하는 경우 Unity 2019 LTS(현재 2019.4.x)를 지원합니다. 이는 위에 링크된 필수 조건에 명시된 모든 Unity 버전 요구 사항을 대체합니다.

## <a name="creating-and-preparing-the-unity-project"></a>Unity 프로젝트 만들기 및 준비

이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.

이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.

1. [Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정
2. [빌드 플랫폼 전환](mr-learning-base-02.md#switching-the-build-platform)
3. [TextMeshPro 필수 리소스 가져오기](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Mixed Reality Toolkit 가져오기 및 Unity 프로젝트 구성](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [장면 만들기 및 설정](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) 및 장면에 적절한 이름 지정(예: **PC 홀로그램 원격**)

그런 다음, [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필을 **DefaultHoloLens2ConfigurationProfile** 로 변경합니다. 공간 인식 메시의 표시 옵션을 **폐색** 으로 변경합니다.

## <a name="importing-the-tutorial-assets"></a>자습서 자산 가져오기

[!INCLUDE[](includes/importing-tutorial-assets-pc-holographic-remoting.md)]

## <a name="configuring-and-preparing-the-scene"></a>장면 구성 및 준비

이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.

[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** 폴더로 차례로 이동합니다. Ctrl 단추를 누른 채 아래 6개의 프리팹을 클릭합니다.

* ButtonParent
* ClippingObjects
* HandSpatialMapButton
* 지침
* ModelParent
* 플랫폼

![선택한 장면에 추가할 프리팹이 있는 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

이러한 모델을 prefabs 폴더에서 **계층 구조 창** 으로 끌어서 놓습니다.

![새로 추가한 프리팹이 여전히 선택된 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

장면의 개체에 초점을 맞추기 위해 **ModelParent** 개체를 두 번 클릭한 다음, 약간씩 다시 확대할 수 있습니다.

![ModelParent 개체에 초점을 맞춘 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> 장면에서 큰 아이콘(예: 틀이 있는 매력적인 큰 'T' 아이콘)이 표시되는 경우 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmo를 끄기 위치로 전환</a>하여 이러한 아이콘을 숨길 수 있습니다.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>장면을 작동하도록 단추 구성

이 섹션에서는 스크립트를 장면에 추가하여 모델 전환 및 클리핑 기능의 기본 사항을 시연하는 단추 이벤트를 만듭니다.

### <a name="1-configuring-the-interactable-script-component"></a>1. Interactable(스크립트) 구성 요소 구성

[계층 구조] 창에서 **ButtonParent** 개체를 펼치고 **NextButton** 을 선택합니다. [검사기] 창에서 **Interactable(스크립트)** 구성 요소를 찾고, **OnClick ()** 이벤트 아래에서 **+** 아이콘을 클릭합니다.

![NextButton OnClick 이벤트가 추가된 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

[계층 구조] 창에서 **NextButton** 개체를 선택한 상태에서 [계층 구조] 창의 **ButtonParent** 개체를 클릭하여 방금 추가한 이벤트의 비어 있는 **없음(개체)** 필드로 끌어서 ButtonParent 개체에서 이 단추의 단추 클릭 이벤트를 수신 대기하도록 설정합니다.

![NextButton OnClick 이벤트 수신기가 구성된 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

동일한 이벤트의 **함수 없음** 드롭다운을 클릭합니다. 그런 다음, **ViewButtonControl** > **NextModel ()** 을 차례로 선택하여 **NextModel ()** 함수를 이 단추의 단추 누름 이벤트가 발생할 때 트리거되는 작업으로 설정합니다.

![NextButton OnClick 이벤트 동작 선택 경로가 있는 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a>2. 나머지 단추 구성

나머지 각 단추에 대해 위에서 설명하는 프로세스를 완료하여 함수를 **OnClick ()** 이벤트에 할당합니다.

* PreviousButton 개체에 대해 **ViewButtonControl** > **PreviousModel ()** 함수를 차례로 할당합니다.

* ClippingButton에 대해 **ToggleButton** > **ToggleClipping ()** 함수를 차례로 선택합니다.

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a>3. 보기 단추 컨트롤(스크립트) 및 토글 단추(스크립트) 구성 요소 구성

이제 단추는 모델 전환 및 클리핑 기능을 시연하도록 구성되었습니다. 이번에는 3D 모델 및 클리핑 개체를 스크립트에 추가해야 합니다.

시연을 위해 6가지 3D 모델이 제공되었습니다. ***ModelParentobject*** 를 펼쳐서 이러한 3D 모델을 표시합니다.

[계층 구조] 창에서 ButtonParent 개체를 여전히 선택한 상태에서 [검사기] 창에서 **보기 단추 컨트롤(스크립트)** 구성 요소를 찾아서 **모델** 변수를 펼칩니다.

**크기** 필드에서 장면에 포함하려는 3D 모델의 수를 입력합니다. 여기서는 6입니다. 새 3D 모델을 추가하기 위한 필드가 만들어집니다.

![ViewButtonControl 스크립트 구성 요소 필드가 있는 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

ModelParent 개체의 각 자식 개체를 이러한 필드로 끌어서 놓습니다.

![ViewButtonControl 스크립트 구성 요소 필드가 구성된 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

**ClippingObjects** 개체를 [계층 구조] 창에서 **토글 단추(스크립트)** 구성 요소의 **클리핑 개체** 필드로 끌어서 놓습니다.
>[!NOTE]
>단추 부모 개체에만 있습니다.

![ToggleButton 스크립트 구성 요소 필드가 구성된 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

[계층 구조] 창에서 **ClippingObjects** 프리팹을 선택하고, [검사기] 창에서 이를 사용하도록 설정하여 클리핑 개체를 설정합니다.

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a>클리핑 기능을 사용하도록 클리핑 개체 구성

이 섹션에서는 MarsCuriosityRover 개체의 자식 개체 렌더러를 개별 클리핑 개체에 추가하여 MarsCuriosityRover 모델의 클리핑을 시연합니다.

[계층 구조] 창에서 **ClippingObjects** 개체를 펼쳐서 이 프로젝트에서 사용할 서로 다른 세 가지 클리핑 개체를 표시합니다.

**ClippingSphere** 개체를 구성하려면 해당 개체를 클릭하고, [검사기] 창에서 **클리핑 구(스크립트)** 구성 요소를 찾습니다. 크기 필드에서 3D 모델에 추가해야 하는 렌더러의 수를 입력합니다. 여기서는 MarsCuriosityRover 자식 개체에 대해 10을 추가합니다. 렌더러를 추가하기 위한 필드를 만들고, MarsCuriosityRover 개체의 자식 모델 개체를 이러한 필드로 끌어서 놓습니다.

![ClippingSphere 스크립트 구성 요소 필드가 구성된 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

동일한 프로세스를 수행하고, MarsCuriosityRover의 자식 개체 렌더러를 **ClippingBox** 및 **ClippingPlane** 개체에 추가합니다.

이 자습서에서는 클리핑 기능을 시연하는 데 MarsCuriosityRover 모델만 사용합니다. 클리핑 기능을 더 많은 모델에 추가하고, 렌더러의 크기를 늘리며, 개별 메시 렌더러를 추가했습니다.

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a>도구 설명을 강조 표시하도록 시선 추적 구성

이 섹션에서는 프로젝트에서 시선 추적을 사용하도록 설정하는 방법을 살펴봅니다. 예를 들어 MarsCuriosityRover 부품에 연결된 도구 설명을 강조 표시하는 기능을 구현하면서 이를 살펴보고, 해당 부품에서 시선을 거둘 때 이를 숨깁니다.

### <a name="1-identify-target-objects-and-associated-tooltips"></a>1. 대상 개체 및 연결된 도구 설명 식별

[계층 구조] 창에서 ModelParent 개체를 선택합니다. ***MarsCuriosity -> Rover** _를 차례로 펼쳐서 5개의 MarsCuriosityRover 주요 부품(_*POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**)을 찾습니다.

* [계층 구조] 창에서 MarsCuriosityRover 부품과 연결된 5개의 해당 도구 설명 개체를 확인합니다.
* MarsCuriosityRover 부품을 살펴볼 때 환경을 강조 표시하도록 이러한 개체를 구성합니다.

![Rover 개체가 선택되어 펼쳐진 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a>2. While Looking At Target () 및 On Look Away () 이벤트 구현

Hierarchy(계층 구조) 창에서 ***POI-Camera** _ 개체를 선택합니다. Inspector(검사기) 창에서 _ *Eye Tracking Target (Script)* * 구성 요소를 찾고, **While Looking At Target ()**  & **On Look Away ()** 이벤트를 다음과 같이 구성합니다.

* **POI-Camera 도구 설명** 개체를 **없음(개체)** 필드에 할당합니다.
* **While Looking At Target ()** 이벤트의 **함수 없음** 드롭다운에서 **GameObject** > **SetActive(부울)** 를 차례로 선택합니다. 대상 개체를 볼 때 트리거되는 작업으로 도구 설명을 강조 표시하려면 아래쪽에 있는 **확인란** 을 선택합니다.

![EyeTrackingTarget WhileLookingAtTarget 이벤트 구성을 진행 중인 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* 동일한 프로세스를 수행하고, **On Look Away ()** 이벤트 수신기의 **함수 없음** 드롭다운을 클릭합니다. 그런 다음, **GameObject** > **SetActive(부울)** 를 차례로 선택하고, 대상 개체에서 시선을 거둘 때 트리거되는 작업으로 도구 설명을 숨기려면 **확인란** 을 비워 둡니다.

![EyeTrackingTarget OnLookAway 이벤트가 구성된 Unity](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

동일한 프로세스를 수행하고, 각 도구 설명 개체를 동일한 **MarsCuriosityRover** 부품의 **While Looking At Target ()**  & **On Look Away ()** 이벤트에 할당합니다.

시선 추적을 사용하도록 설정하려면 이러한 [지침](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations)을 따르세요.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 UI 요소, 3D 모델 조작, 모델 클리핑 및 시선 추적 기능을 시연하는 혼합 현실 환경을 빌드하는 방법을 알아보았습니다. 이 자습서에서는 3D 모델 뷰어 환경을 검색할 수 있도록 하는 NextButton 및 PreviousButton을 제공했습니다. ClippingObjectButton을 사용하여 클리핑 개체를 설정하고 클리핑 기능을 경험해 보았습니다. 또한 이 자습서에서는 환경에서 도구 설명을 강조 표시하도록 설정하는 시선 추적 요소를 제공했습니다.

다음 단원에서는 언제든지 PC에서 HoloLens 2를 연결할 수 있는 홀로그램 원격 애플리케이션을 만들고 혼합 현실에서 3D 콘텐츠를 시각화하는 방법을 알아봅니다.

> [!div class="nextstepaction"]
> [다음 단원: 2. 홀로그램 원격 애플리케이션 만들기](mr-learning-pc-holographic-remoting-02.md)