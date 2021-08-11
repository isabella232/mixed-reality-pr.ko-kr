---
title: 시선 추적 예제 개요
description: MRTK에서 eyetracking을 빌드하는 예제
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, mrtk, EyeTracking,
ms.openlocfilehash: 32ae64a470572dda71578948d5091887bea9e0e084d97ede7f2f14af596b5a6b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223221"
---
# <a name="eye-tracking-examples-overview"></a>시선 추적 예제 개요

이 항목에서는 MRTK 눈동자 추적 예제 (asset/MRTK/예제/데모/EyeTracking)를 빌드하여 MRTK에서 신속 하 게 눈을 추적 하는 방법을 설명 합니다.
이러한 샘플을 통해 새 마법 입력 기능 ( **눈 추적**) 중 하나를 경험할 수 있습니다.
이 데모에는 암시적 눈 기반 활성화에서 **음성** 및 **직접** 입력으로 보고 있는 내용에 대 한 정보를 원활 하 게 결합 하는 방법에 이르기까지 다양 한 사용 사례가 포함 되어 있습니다.
이를 통해 사용자는 목표를 확인 하 고 _' 선택 '_ 하거나 직접 제스처를 수행 하 여 holographic 콘텐츠를 신속 하 고 간편 하 게 선택 하 고 간편 하 게 선택 하 고 이동할 수 있습니다.
또한이 데모에는 슬레이트에서 텍스트 및 이미지를 시각적으로 전달 하 고, 이동 하 고, 확대/축소 하는 방법에 대 한 예제가 포함 되어 있습니다.
마지막으로 2D 슬레이트에서 사용자의 시각적 주의를 기록 하 고 시각화 하기 위한 예제를 제공 합니다.
다음 섹션에는 MRTK 눈동자 추적 예제 패키지 (asset/MRTK/example/samples/EyeTracking)의 각 샘플에 대 한 자세한 내용이 나와 있습니다.

![시각 추적 장면 목록](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

다음 섹션에서는 개별 눈 추적 데모의 장면을 간략히 설명 합니다.
MRTK 눈 추적 데모 장면을 로드 하는 방법에 대 한 자세한 내용은 [추가로 업데이트할지](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)를 참조 하세요.

## <a name="overview-of-the-eye-tracking-demo-samples"></a>눈 추적 데모 샘플 개요

### <a name="eye-supported-target-selection"></a>[**눈 지원 대상 선택**](../input/eye-tracking/eye-tracking-target-selection.md)

이 자습서에서는 눈에 멋진 데이터에 액세스 하 여 대상을 선택 하는 용이성을 보여 줍니다.
여기에는 사용자에 게 대상이 과도 하 게 집중 되는 것이 아니라 유연 하다는 확신을 제공할 수 있는 미묘한 사용자 의견에 대 한 예제가 포함 되어 있습니다.
또한 읽은 후 자동으로 사라지는 간단한 스마트 알림 예제가 있습니다.

**요약**: 눈, 음성 및 직접 입력의 조합을 사용 하 여 빠르고 간편 하 게 대상 선택

### <a name="eye-supported-navigation"></a>[**눈에 잘 지 원하는 탐색**](../input/eye-tracking/eye-tracking-navigation.md)

사용자가 먼 표시 또는 전자 판독기에 대 한 일부 정보를 읽고 표시 된 텍스트의 끝에 도달 하면 텍스트가 자동으로 위로 스크롤되고 추가 콘텐츠가 표시 됩니다. Imagine
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

장치에서 눈 추적 샘플을 사용 하려면 패키지의 appxmanifest.xml에 대 한 "응시 입력" 기능을 사용 하 여 작성 된 HoloLens 2 및 샘플 앱 패키지가 필요 합니다.

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

런타임 중에 추가 장면을 로드 하려면 _빌드 메뉴에서 설정-> 장면_ 빌드에 이러한 장면을 먼저 추가 해야 합니다.
루트 장면이 목록의 첫 번째 장면으로 표시 되는 것이 중요 합니다.

![눈 추적 샘플에 대 한 빌드 설정 장면 메뉴](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. Unity 편집기에서 눈 추적 샘플 재생

상태 추적 장면을 빌드 설정에 추가 하 고 _EyeTrackingDemo-00-rootscene_ 로드 한 후에는 마지막으로 확인할 수 있는 항목은 _MixedRealityBasicSceneSetup_ GameObject에 연결 된 _' onloadstartscene '_ 스크립트입니다. 이는 루트 장면에서 가장 먼저 로드할 데모 장면을 알 수 있도록 하는 것입니다.

![OnLoad_StartScene 스크립트의 예](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

시작합시다! _"재생"_ 을 누릅니다.
여러 개의 보석 및 위쪽에 장면 메뉴가 표시 되어야 합니다.

![ET 대상 선택 장면에서 샘플 스크린샷](../images/eye-tracking/mrtk_et_targetselect.png)

또한 게임 보기의 중앙에 작은 반투명 원이 표시 되어야 합니다.
이는 _시뮬레이션 된 눈동자 응시_ 의 표시기 (커서) 역할을 합니다. 마우스 _오른쪽 단추_ 를 클릭 하 고 마우스를 이동 하 여 위치를 변경 하기만 하면 됩니다.
커서가 보석 위에 마우스를 가져가면 현재 표시 된 보석의 중심에 커서가 표시 됩니다.
이 방법은 대상에서 _"찾을"_ 때 이벤트가 예상 대로 트리거되는지 여부를 테스트 하는 좋은 방법입니다.
마우스 컨트롤을 통한 _시뮬레이션 된 눈동자_ 는 신속 하 고 의도 하지 않은 눈으로 이동 하는 것이 더 나쁜 점입니다.
그러나 HoloLens 2 장치에 배포 하 여 디자인을 반복 하기 전에 기본적인 기능을 테스트 하는 것이 좋습니다.
눈 추적 샘플 장면으로 돌아가기: 보석은 확인 하는 동안 회전 하 고,이를 "조사" 하 여 삭제할 수 있습니다.

- _Enter_ 키를 누르면 ("select"를 시뮬레이션)
- 마이크에 _"선택"_ 하는 것을 말합니다.
- _공간_ 을 눌러 시뮬레이션 된 손 입력을 표시 하는 동안 마우스 왼쪽 단추를 클릭 하 여 시뮬레이션을 수행 합니다.

[**눈에 잘 지 원하는 대상 선택**](../input/eye-tracking/eye-tracking-target-selection.md) 자습서에서 이러한 상호 작용을 달성할 수 있는 방법에 대해 자세히 설명 합니다.

커서를 장면의 상단 메뉴 모음으로 이동 하면 현재 가리킨 항목이 조금씩 강조 표시 됩니다.
위에서 설명한 커밋 방법 중 하나 (예: _enter_ 키 누름)를 사용 하 여 현재 강조 표시 된 항목을 선택할 수 있습니다.
이러한 방식으로 다양 한 시각 추적 샘플 장면을 전환할 수 있습니다.

### <a name="4-how-to-test-specific-sub-scenes"></a>4. 특정 하위 장면을 테스트 하는 방법

특정 시나리오에서 작업 하는 경우 매번 장면 메뉴를 거치지 않으려는 경우가 있습니다.
대신, _재생_ 단추를 누를 때 현재 작업 중인 장면에서 직접 시작할 수 있습니다.
문제없습니다! 수행할 수 있는 작업은 다음과 같습니다.

1. _루트_ 장면 로드
2. _루트_ 장면에서 _' Onloadstartscene '_ 스크립트를 사용 하지 않도록 설정 합니다.
3. 아래 스크린샷에 표시 된 것 처럼 아래에 설명 된 시각 추적 테스트 장면 중 하나 (또는 다른 장면)를 _계층_ 뷰에 _끌어_ 놓습니다.

    ![추가 장면의 예](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. _Play_ 누르기

이와 같은 하위 장면을 로드 하는 것은 영구적이 지 않습니다. 즉, HoloLens 2 장치에 앱을 배포 하는 경우 루트 장면이 로드 됩니다 (빌드 설정 맨 위에 표시 된다고 가정).
또한 프로젝트를 다른 사용자와 공유 하는 경우에는 하위 장면이 자동으로 로드 되지 않습니다.

---

이제 MRTK 눈 추적 예제 장면을 작업 하는 방법을 배웠으므로 이제 눈에 holograms를 선택 하는 방법에 대 한 자세한 내용을 계속 살펴보겠습니다. [눈에 잘 지 원하는 대상 선택](../input/eye-tracking/eye-tracking-target-selection.md)

---
["MixedRealityToolkit의 눈동자 추적"으로 돌아가기](../input/eye-tracking/eye-tracking-Main.md)
