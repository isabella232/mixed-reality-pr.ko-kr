---
title: MRTK 프로필 구성
description: 이 과정에서는 혼합 현실 앱을 위한 MRTK(Mixed Reality Toolkit) 프로필을 구성하는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, MRTK, mixed reality toolkit, UWP, 공간 인식
ms.localizationpriority: high
ms.openlocfilehash: 9b0c914bd1f518d53abdd681b3a5f6959c9a6211
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98579354"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3. MRTK 프로필 구성

이 자습서에서는 MRTK 프로필을 사용자 지정하고 구성하는 방법을 알아봅니다.

<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">MRTK 프로필</a>은 MRTK 시스템 및 기능을 초기화하는 방법에 대한 구성 정보를 구성하는 중첩된 프로필 트리입니다. 최상위 프로필인 Configuration Profile에는 각 기본 코어 시스템에 대한 중첩 프로필이 포함되어 있습니다. 각 중첩 프로필은 해당 시스템의 동작을 구성하도록 설계되었습니다.

이 예제에서는 공간 메시 관찰자의 설정을 변경하여 공간 인식 메시를 숨기는 방법을 보여줍니다. 그러나 MRTK 프로필의 설정 또는 값을 사용자 지정할 때 이러한 원칙을 그대로 적용해도 됩니다.

[이전 자습서](mr-learning-base-02.md#congratulations)에서 HoloLens 2에 프로젝트를 배포할 때처럼 <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">공간 인식</a> 메시는 환경의 기하 도형을 나타내는 메시 컬렉션입니다. 처음에 볼 때는 유용하지만, 시각적 산만함과 이 기능을 사용할 때의 추가 성능 저하를 피하기 위해 일반적으로 꺼져 있습니다.

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

### <a name="1-clone-the-default-configuration-profile"></a>1. 기본 구성 프로필 복제

> [!NOTE]
> 구성 프로필은 최상위 수준 프로필입니다. 따라서 다른 프로필을 편집하려면 먼저 구성 프로필을 복제해야 합니다.

Hierarchy(계층 구조) 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector(검사기) 창에서 **MixedRealityToolkit** 구성 프로필이 **DefaultXRSDKConfigurationProfile** 로 설정되어 있는지 확인합니다.

![DefaultHoloLens2ConfigurationProfile이 선택된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-03-section1-step1-1.png)

다음과 같이 **MixedRealityToolkit** 개체를 선택한 상태로, [검사기] 창에서 **복제 및 사용자 지정** 단추를 클릭하여 [프로필 복제] 창을 엽니다.

![Unity MixedRealityToolkit 구성 요소 Copy & Customize 단추](images/mr-learning-base/base-03-section1-step1-2.png)

Clone Profile(프로필 복제) 창에서 적절한 **Profile Name(프로필 이름)** (예: _GettingStarted_XRSDKConfigurationProfile_)을 입력한 다음, **Clone(복제)** 단추를 클릭하여 **DefaultXRSDKConfigurationProfile** 의 편집 가능한 복사본을 만듭니다.

![Unity MixedRealityToolkit 복제 Configuration Profile 팝업 창](images/mr-learning-base/base-03-section1-step1-3.png)

이제 새로 만든 구성 프로필이 다음과 같이 장면의 구성 프로필로 할당됩니다.

![새로 만든 사용자 지정 HoloLens2ConfigurationProfile이 적용된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-03-section1-step1-4.png)

Unity 메뉴에서 **파일** > **저장** 을 선택하여 장면을 저장합니다.

> [!TIP]
> 자습서를 진행하는 동안 항상 작업을 저장해야 합니다.

### <a name="2-enable-the-spatial-awareness-system"></a>2. 공간 인식 시스템 사용

Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 **공간 인식** 탭을 선택한 다음, **공간 인식 시스템 사용** 확인란을 선택합니다.

![공간 인식 시스템이 사용된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> 향후 프로젝트에서 앱이 환경에 응답하거나 상호 작용할 필요가 없는 경우, 성능 비용을 줄이기 위해 공간 인식을 계속 해제해 두는 것이 좋습니다.

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. 기본 공간 인식 시스템 프로필 복제

다음과 같이 **공간 인식** 탭에서 **복제** 단추를 클릭하여 [프로필 복제] 창을 엽니다.

![공간 인식 탭이 선택된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-03-section1-step3-1.png)

Clone Profile(프로필 복제) 창에서 적절한 **프로필 이름**(예: _GettingStarted_XRSDKSpatialAwarenessSystemProfile_)을 입력한 다음, **Clone(복제)** 단추를 클릭하여 **DefaultXRSDKSpatialAwarenessSystemProfile** 의 편집 가능한 복사본을 만듭니다.

![Unity MixedRealityToolkit 복제 공간 인식 시스템 프로필 팝업 창](images/mr-learning-base/base-03-section1-step3-2.png)

이제 새로 만든 공간 인식 시스템 프로필이 다음과 같이 구성 프로필에 자동으로 할당됩니다.

![새로 만든 사용자 지정 MixedRealitySpatialAwarenessSystemProfile이 적용된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. 기본 공간 인식 메시 관찰자 프로필 복제

다음과 같이 **Spatial Awareness(공간 인식)** 탭을 선택한 상태로 **XR SDK Windows Mixed Reality Spatial Mesh Observer(XR SDK Windows Mixed Reality 공간 메시 관찰자)** 섹션을 확장한 다음, **Clone(복제)** 단추를 클릭하여 Clone Profile(프로필 복제) 창을 엽니다.

![Windows Mixed Reality 공간 메시 관찰자 섹션이 확장된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-03-section1-step4-1.png)

Clone Profile 창에서 적절한 **프로필 이름**(예: _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_)을 입력한 다음, **복제** 단추를 클릭하여 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 의 편집 가능한 복사본을 만듭니다.

![Unity MixedRealityToolkit 복제 공간 메시 관찰자 프로필 팝업 창](images/mr-learning-base/base-03-section1-step4-2.png)

이제 새로 만든 공간 인식 메시 관찰자 프로필이 다음과 같이 공간 인식 시스템 프로필에 자동으로 할당됩니다.

![새로 만든 사용자 지정 MixedRealitySpatialAwarenessMeshObserverProfile이 적용된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. 공간 인식 메시의 표시 유형 변경

다음과 같이 **공간 메시 관찰자 설정** 에서 **표시 옵션** 을 **폐색** 으로 변경하여 공간 매핑 메시가 계속 작동하는 동안에도 보이지 않도록 설정합니다.

![공간 메시 관찰자 표시 옵션이 폐색으로 설정된 Unity MixedRealityToolkit 구성 요소](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> 공간 매핑 메시가 보이지 않더라도 여전히 존재하며 작동 중입니다. 예를 들어 실제 벽 뒤의 홀로그램처럼 공간 매핑 메시 뒤의 홀로그램은 보이지 않습니다.

MRTK 프로필에서 설정을 수정하는 방법을 알아보았습니다. 보시는 것처럼, MRTK 설정을 사용자 지정하려면 먼저 기본 프로필의 복사본을 만들어야 합니다. 기본 프로필은 편집이 불가능하므로, 기본 설정으로 되돌리고 싶을 때 항상 기본 프로필을 참조로 사용할 수 있습니다. MRTK 프로필 및 해당 아키텍처에 대한 자세한 내용은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [MRTK 프로필 구성 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)를 참조하세요.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 MRTK 프로필 및 설정을 복제, 사용자 지정 및 구성하는 방법을 배웠습니다.

> [!div class="nextstepaction"]
> [다음 자습서: 4. 장면에서 개체 위치 지정](mr-learning-base-04.md)
