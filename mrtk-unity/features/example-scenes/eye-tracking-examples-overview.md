---
title: 시선 추적 예제 개요
description: MRTK에서 시선 추적을 빌드하는 예제
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK, EyeTracking,
ms.openlocfilehash: b5fd3ee35e54c54f2f6b21dc1ce53625c68f65b4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144682"
---
# <a name="eye-tracking-examples"></a>시선 추적 예제

이 항목에서는 MRTK 시선 추적 예제(Assets/MRTK/Examples/Demos/EyeTracking)를 기반으로 하여 MRTK에서 시선 추적을 빠르게 시작하는 방법을 설명합니다.
이러한 샘플을 통해 새로운 입력 기능인 **시선 추적!**
데모에는 암시적 시선 기반 활성화에서 **음성** 및 **손** 입력으로 보고 있는 내용에 대한 정보를 원활하게 결합하는 방법에 이르기까지 다양한 사용 사례가 포함되어 있습니다.
이렇게 하면 사용자는 대상을 보고 _'선택'이라고_ 말하거나 손 제스처를 수행하여 홀로그램 콘텐츠를 빠르고 쉽게 선택하고 보기 전체로 이동할 수 있습니다.
데모에는 슬레이트에 있는 텍스트 및 이미지의 시선 응시 지향 스크롤, 이동 및 확대/축소 예제도 포함되어 있습니다.
마지막으로, 2D 슬레이트에서 사용자의 시각적 주의를 기록하고 시각화하는 예제가 제공됩니다.
다음 섹션에서는 MRTK 시선 추적 예제 패키지(Assets/MRTK/Examples/Demos/EyeTracking)에 포함된 각 샘플에 대한 자세한 내용을 확인할 수 있습니다.

![시선 추적 장면 목록](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

다음 섹션은 개별 시선 추적 데모 장면에 대한 간략한 개요입니다.
MRTK 시선 추적 데모 장면이 [가감적으로 로드되며,](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)아래에서 설정하는 방법을 설명합니다.

## <a name="overview-of-the-eye-tracking-demo-samples"></a>시선 추적 데모 샘플 개요

### <a name="eye-supported-target-selection"></a>[**시선 지원 대상 선택**](../input/eye-tracking/eye-tracking-target-selection.md)

이 자습서에서는 시선 응시 데이터에 쉽게 액세스하여 대상을 선택하는 방법을 보여줍니다.
대상에 집중한다는 확신을 사용자에게 제공하기 위한 미묘한 피드백과 강력한 피드백의 예가 포함되어 있습니다.
또한 읽은 후 자동으로 사라지는 스마트 알림의 간단한 예가 있습니다.

**요약:** 눈, 음성 및 손 입력의 조합을 사용하여 빠르고 간편한 대상 선택

### <a name="eye-supported-navigation"></a>[**눈에 잘 지 원하는 탐색**](../input/eye-tracking/eye-tracking-navigation.md)

멀리 떨어져 있는 표시 또는 전자 판독기에서 몇 가지 정보를 읽고 표시 된 텍스트의 끝에 도달 하면 텍스트가 자동으로 이동 하 여 더 많은 콘텐츠를 표시 한다고 가정 합니다.
또는 원하는 위치로 직접 확대/축소 하는 방법에 대해 magically?
이 자습서에서는 눈에 전시 탐색에 대 한 몇 가지 예제를 보여 줍니다.
또한 현재 포커스에 따라 자동으로 회전 하도록 하 여 3D holograms의 수동 회전을 위한 예제가 있습니다.

**요약**: 눈동자, 음성 및 직접 입력의 조합을 사용 하 여 스크롤, 이동, 확대/축소, 3d 회전

### <a name="eye-supported-positioning"></a>[**눈 지원 위치**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

이 자습서에서는 이전 1980의 MIT 미디어 랩에서 눈에 잘 [맞는](https://youtu.be/CbIn8p4_4CQ) 음성 입력을 사용 하 여 연구 하는 방법에 대해 설명 합니다.
아이디어는 빠르게 목표를 선택 하 고 위치를 지정 하는 데 도움이 됩니다.
홀로그램을 살펴보고 _' 배치 '_ 라고 표시 하 고, 배치 하려는 위치를 확인 하 고 _' 거기! '_ 라고 합니다.
홀로그램을 보다 정확 하 게 배치 하기 위해 직접, 음성 또는 컨트롤러에서 추가 입력을 사용할 수 있습니다.

**요약**: 눈동자, 음성 및 직접 입력 (*끌어서 놓기*)을 사용 하 여 holograms을 배치 합니다. 눈 + 바늘을 사용 하는 눈에 잘 지는 슬라이더.

### <a name="visualization-of-visual-attention"></a>**시각적 주의 시각화**

사용자의 모습을 기반으로 하는 데이터는 디자인의 유용성을 평가 하 고 효율적인 작업 스트림의 문제를 식별 하는 매우 강력한 도구입니다.
이 자습서에서는 다양 한 눈 추적 시각화 및 여러 가지 요구 사항을 충족 하는 방법을 설명 합니다.
눈 추적 데이터를 기록 하 고 로드 하기 위한 기본 예제와 이러한 데이터를 시각화 하는 방법에 대 한 예제를 제공 합니다.

**요약**: 슬레이트의 2 차원 주의 맵 (열 지도) 눈 추적 데이터를 재생 하 &를 기록 합니다.

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>MRTK 눈동자 추적 샘플 설정

### <a name="prerequisites"></a>필수 조건

장치에서 눈 추적 샘플을 사용 하려면 패키지의 Appxmanifest.xml에 "응시 입력" 기능을 사용 하 여 빌드된 샘플 앱 패키지와 HoloLens 2가 필요 합니다.

장치에서 이러한 눈 추적 샘플을 사용 하려면 Visual Studio에서 앱을 빌드하기 전에 [다음 단계](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) 를 수행 해야 합니다.

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. Load EyeTrackingDemo-00-RootScene 있습니다.

*EyeTrackingDemo-00-RootScene* 은 모든 코어 MRTK 구성 요소가 포함 된 기본 (_루트_) 장면입니다.
이는 먼저 로드 해야 하며, 눈 추적 데모를 실행 하는 장면입니다.
[추가로 업데이트할지 로드](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)되는 다양 한 눈 추적 샘플 간을 쉽게 전환할 수 있는 그래픽 장면 메뉴를 제공 합니다.

![눈 추적 샘플의 장면 메뉴](../images/eye-tracking/mrtk_et_scenemenu.jpg)

루트 장면에는 MRTK 구성 된 프로필 및 장면 카메라와 같이 추가로 업데이트할지 로드 된 장면에서 지속 되는 몇 가지 핵심 구성 요소가 포함 되어 있습니다.
_MixedRealityBasicSceneSetup_ (아래 스크린샷 참조)에는 시작 시 참조 된 장면을 자동으로 로드 하는 스크립트가 포함 되어 있습니다.
기본적으로 _EyeTrackingDemo는 선택 사항_ 입니다.  

![OnLoadStartScene 스크립트의 예](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. 빌드 메뉴에 장면 추가

런타임 중에 추가 장면을 로드 하려면 빌드 _설정-빌드 메뉴의 > 장면_ 에 이러한 장면을 먼저 추가 해야 합니다.
루트 장면이 목록의 첫 번째 장면으로 표시 되는 것이 중요 합니다.

![빌드 설정 시각 추적 샘플에 대 한 장면 메뉴](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. Unity 편집기에서 눈 추적 샘플 재생

빌드 설정에 시각 추적 장면을 추가 하 고 _EyeTrackingDemo-00-rootscene_ 로드 한 후에는 마지막으로 확인할 수 있는 항목은 _MixedRealityBasicSceneSetup_ GameObject에 연결 된 _' onloadstartscene '_ 스크립트입니다. 이는 루트 장면에서 가장 먼저 로드할 데모 장면을 알 수 있도록 하는 것입니다.

![OnLoad_StartScene 스크립트의 예](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

시작합시다! _"Play"_!
여러 gem이 표시되고 장면 메뉴가 맨 위에 표시됩니다.

![ET 대상 선택 장면의 샘플 스크린샷](../images/eye-tracking/mrtk_et_targetselect.png)

또한 게임 보기의 가운데에 작은 반투명 원을 볼 수 있습니다.
시뮬레이션된 _시선 응시의_ 표시기(커서) 역할을 합니다. 마우스 _오른쪽 단추를_ 누르고 마우스를 이동하여 위치를 변경하기만 하면 됩니다.
커서가 gem 위로 마우스를 가져가면 현재 본 gem의 가운데에 맞춰지는 것을 알 수 있습니다.
이는 대상을 _"살펴볼"_ 때 이벤트가 예상대로 트리거되는지 테스트하는 좋은 방법입니다.
마우스 컨트롤을 통한 _시뮬레이션된 시선 응시는_ 빠르고 의도하지 않은 시선 이동에 비해 다소 좋지 않은 보완입니다.
그러나 HoloLens 2 디바이스에 배포하여 디자인을 계속 진행하기 전에 기본 기능을 테스트하는 데 적합합니다.
시선 추적 샘플 장면으로 돌아가기: gem은 보고 있는 동안 회전하며 , 및 ...를 "보고"하여 소멸될 수 있습니다.

- Enter 키를 누릅니다("select"라고 말하는 시뮬레이션) 
- 마이크에 _"select"라고_ 말
- _Space를_ 눌러 시뮬레이션된 손 입력을 표시하는 동안 마우스 왼쪽 단추를 클릭하여 시뮬레이션된 손가락 모으기를 수행합니다.

[**시선 지원 대상 선택**](../input/eye-tracking/eye-tracking-target-selection.md) 자습서에서 이러한 상호 작용을 달성할 수 있는 방법을 자세히 설명합니다.

장면의 위쪽 메뉴 모음까지 커서를 이동하면 현재 마우스로 가리킨 항목이 부분적으로 강조 표시됩니다.
위에서 설명한 커밋 방법 중 하나를 사용하여 현재 강조 표시된 항목을 선택할 수 있습니다(예: Enter 키를 _누른_ 경우).
이렇게 하면 다양한 시선 추적 샘플 장면 간에 전환할 수 있습니다.

### <a name="4-how-to-test-specific-sub-scenes"></a>4. 특정 하위 장면을 테스트하는 방법

특정 시나리오에서 작업하는 경우 매번 장면 메뉴를 거치지 않을 수 있습니다.
대신 _재생_ 단추를 누를 때 현재 작업 중인 장면에서 직접 시작할 수 있습니다.
문제없습니다! 수행할 수 있는 작업은 다음과 같습니다.

1. _루트_ 장면 로드
2. _루트_ 장면에서 _' Onloadstartscene '_ 스크립트를 사용 하지 않도록 설정 합니다.
3. 아래 스크린샷에 표시 된 것 처럼 아래에 설명 된 시각 추적 테스트 장면 중 하나 (또는 다른 장면)를 _계층_ 뷰에 _끌어_ 놓습니다.

    ![추가 장면의 예](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. _Play_ 누르기

이와 같은 하위 장면을 로드 하는 것은 영구적이 지 않습니다. 즉, 앱을 HoloLens 2 장치에 배포 하는 경우 루트 장면이 로드 됩니다 (빌드 설정의 맨 위에 표시 된다고 가정).
또한 프로젝트를 다른 사용자와 공유 하는 경우에는 하위 장면이 자동으로 로드 되지 않습니다.

---

이제 MRTK 눈 추적 예제 장면을 작업 하는 방법을 배웠으므로 이제 눈에 holograms를 선택 하는 방법에 대 한 자세한 내용을 계속 살펴보겠습니다. [눈에 잘 지 원하는 대상 선택](../input/eye-tracking/eye-tracking-target-selection.md)

---
["MixedRealityToolkit의 눈동자 추적"으로 돌아가기](../input/eye-tracking/eye-tracking-Main.md)
