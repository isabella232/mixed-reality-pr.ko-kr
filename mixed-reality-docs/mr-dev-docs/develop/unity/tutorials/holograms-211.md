---
title: HoloLens(1세대) 입력 211 - 제스처
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 따라 제스처 개념에 대 한 자세한 내용을 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, 아카데미, 자습서, 제스처, HoloLens, 혼합 현실 아카데미, unity, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, Windows 10
ms.openlocfilehash: 75cfb836e5a9702c1d949ed57450984081db0c5d6ec14c76cae5148edf637e7e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206432"
---
# <a name="hololens-1st-gen-input-211-gesture"></a>HoloLens (첫 번째 gen) 입력 211: 제스처

>[!IMPORTANT]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen), Unity 2017 및 혼합 현실 모던 헤드셋을 고려 하 여 설계 되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다. 이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않으며 최신 버전의 Unity와 호환 되지 않을 수 있습니다.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2에 대한 [새로운 자습서 시리즈](mrlearning-base.md)가 게시되었습니다.

[제스처](../../../design/gaze-and-commit.md#composite-gestures) 사용자 의도를 작업으로 설정 합니다. 제스처를 사용하면 사용자가 홀로그램과 상호 작용할 수 있습니다. 이 과정에서는 사용자의 손을 추적 하 고, 사용자 입력에 응답 하 고, 직접 상태 및 위치에 따라 사용자에 게 피드백을 제공 하는 방법을 알아봅니다.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

[MR 기본 101](../../../develop/unity/tutorials/holograms-101.md)에서는 간단한 공기 탭 제스처를 사용 하 여 holograms와 상호 작용 했습니다. 이제는 공중 탭 제스처를 벗어나 이동 하 여 다음에 대 한 새로운 개념을 살펴보겠습니다.

* 사용자의 손을 추적 하 고 사용자에 게 피드백을 제공 하는 경우를 감지 합니다.
* 탐색 제스처를 사용 하 여 holograms를 회전 합니다.
* 사용자의 손을 볼 때 사용자 의견을 제공 하세요.
* 조작 이벤트를 사용 하 여 사용자가 손을 holograms 이동할 수 있도록 합니다.

이 과정에서는 [MR 입력 210](holograms-210.md)에서 빌드된 Unity 프로젝트 **모델 탐색기** 를 다시 방문 합니다. Astronaut 친구는 이러한 새 제스처 개념을 탐색 하는 데 도움이 됩니다.

>[!IMPORTANT]
>아래 각 장에 포함 된 비디오는 이전 버전의 Unity를 사용 하 여 기록 되 고 혼합 된 현실을 Toolkit. 단계별 지침은 정확 하 고 최신 상태 이지만 최신의 비디오에서 스크립트 및 시각적 개체를 볼 수 있습니다. Posterity에 대 한 비디오는 포함 되어 있지만 적용 되는 개념은 그대로 유지 됩니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 입력 211: 제스처</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전에

### <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구로](../../../develop/install-the-tools.md)구성 된 Windows 10 PC.
* 몇 가지 기본적인 c # 프로그래밍 기능.
* [MR 기본 101](../../../develop/unity/tutorials/holograms-101.md)를 완료 해야 합니다.
* [MR 입력 210](holograms-210.md)을 완료 해야 합니다.
* [개발용으로 구성](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 장치입니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) 을 다운로드 합니다. Unity 2017.2 이상이 필요 합니다.
* 바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)있습니다.

### <a name="errata-and-notes"></a>정오표 및 참고 사항

* 코드에서 중단점을 적중 하려면 도구->옵션->디버깅 아래 Visual Studio에서 "내 코드만 사용"을 사용 하지 않도록 설정 (*선택 취소*) 해야 합니다.

## <a name="chapter-0---unity-setup"></a>0 장-Unity 설치

### <a name="instructions"></a>지침

1. Unity를 시작합니다.
2. **열기** 를 선택합니다.
3. 이전에 보관 하지 않은 **제스처** 폴더로 이동 합니다.
4.  / **모델 탐색기** 시작 폴더를 찾아 선택 합니다.
5. **폴더 선택** 단추를 클릭 합니다.
6. **Project** 패널에서 **장면** 폴더를 확장 합니다.
7. **모델 탐색기** 장면을 두 번 클릭 하 여 Unity에서 로드 합니다.

### <a name="building"></a>빌딩

1. Unity에서 **파일 > 빌드 설정** 를 선택 합니다.
2. 백그라운드에서 장면 **/모델 탐색기** 가 **백그라운드** 에서 표시 되지 않는 경우 **열린 장면 추가** 를 클릭 하 여 장면을 추가 합니다.
3. HoloLens에 대해 구체적으로 개발 하는 경우 **대상 장치** 를 **HoloLens** 로 설정 합니다. 그렇지 않으면 **모든 장치** 에 그대로 둡니다.
4. **빌드 형식이** **D3D** 로 설정 되 고 **sdk** 가 **최신 버전** 으로 설정 되어 있는지 확인 합니다 (sdk 16299 이상 이어야 함).
5. **빌드** 를 클릭한 다음
6. "App" 이라는 **새 폴더** 를 만듭니다.
7. 단일 **앱** 폴더를 클릭 합니다.
8. **폴더 선택** 을 클릭 하면 Unity가 Visual Studio에 대 한 프로젝트 빌드를 시작 합니다.

Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.

1. **앱** 폴더를 엽니다.
2. **모델 탐색기 Visual Studio 솔루션** 을 엽니다.

HoloLens에 배포 하는 경우:

1. Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86** 으로 변경 합니다.
2. 로컬 컴퓨터 단추 옆에 있는 드롭다운 화살표를 클릭 하 고 **원격 컴퓨터** 를 선택 합니다.
3. **HoloLens 장치 IP 주소** 를 입력 하 고 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** 로 설정 합니다. **선택** 을 클릭합니다. 장치 IP 주소를 모르는 경우 **설정 > 네트워크 & 인터넷 > 고급 옵션** 을 확인 하세요.
4. 상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5** 를 누릅니다. 처음으로 장치에 배포 하는 경우 [Visual Studio와 쌍](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)으로 연결 해야 합니다.
5. 앱이 배포 되 면 **선택 제스처로** **fitbox** 를 해제 합니다.

모던 헤드셋에 배포 하는 경우:

1. Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 x **64** 로 변경 합니다.
2. 배포 대상이 **로컬 컴퓨터** 로 설정 되었는지 확인 합니다.
3. 상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5** 를 누릅니다.
4. 앱이 배포 되 면 동작 컨트롤러에서 트리거를 당겨 **Fitbox** 를 해제 합니다.

>[!NOTE]
>Visual Studio 오류 패널에 몇 가지 빨간색 오류가 표시 될 수 있습니다. 무시 해도 됩니다. 출력 패널로 전환 하 여 실제 빌드 진행률을 확인 합니다. 출력 패널에 오류가 발생 하면 문제를 해결 해야 합니다 (대부분 스크립트에서 실수로 인해 발생 하는 경우).

## <a name="chapter-1---hand-detected-feedback"></a>1 장 검색 된 피드백

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>목표

* 직접 추적 이벤트를 구독 합니다.
* 커서 피드백을 사용 하 여 손을 추적할 때 사용자를 표시 합니다.

>[!NOTE]
>HoloLens 2에서 손 모양 검색은 손가락이 표시 될 때마다 발생 합니다 (손가락이 가리키는 경우에만).

### <a name="instructions"></a>지침

* **계층** 패널에서 **inputmanager** 개체를 확장 합니다.
* **GesturesInput** 개체를 찾고 선택 합니다.

**InteractionInputSource** 스크립트는 다음 단계를 수행 합니다.

1. InteractionSourceDetected 및 InteractionSourceLost 이벤트를 구독 합니다.
2. 수동 검색 상태를 설정 합니다.
3. InteractionSourceDetected 및 InteractionSourceLost 이벤트의 구독을 취소 합니다.

다음으로, 사용자의 작업에 따라 사용자 의견을 표시 하는 커서를 [MR 입력 210](holograms-210.md) 에서 하나로 업그레이드 합니다.

1. **계층** 패널에서 **커서** 개체를 선택 하 고 삭제 합니다.
2. **Project** 패널에서 **CursorWithFeedback** 를 검색 하 여 **계층** 패널로 끕니다.
3. **계층** 패널에서 **inputmanager** 를 클릭 한 다음,이 **계층** 에서 **CursorWithFeedback** 개체를 **검사기** 의 맨 아래에 있는 inputmanager의 **simplesinglepointerselector** 필드로 끕니다. 
4. **계층** 구조 에서 **CursorWithFeedback을** 클릭합니다.
5. **검사기** 패널의 개체 커서 스크립트에서 **커서 상태 데이터를** **확장합니다.**

**커서 상태 데이터는** 다음과 같이 작동합니다.

* **모든 관찰** 상태는 손은 검색되지 않으며 사용자가 단순히 주변을 둘러보고 있음을 의미합니다.
* **상호 작용** 상태는 손 또는 컨트롤러가 검색됨을 의미합니다.
* **가리키기** 상태는 사용자가 홀로그램을 보고 있다는 것을 의미합니다.

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity에서 **파일 > 빌드 설정** 사용하여 애플리케이션을 다시 빌드합니다.
* **앱** 폴더를 엽니다.
* 아직 열려 있지 않은 경우 **ModelExplorer Visual Studio 솔루션을** 엽니다.
  * (설정하는 동안 Visual Studio 이 프로젝트를 이미 빌드/배포한 경우 VS의 해당 인스턴스를 열고 메시지가 표시되면 '모두 다시 로드'를 클릭할 수 있습니다.)
* Visual Studio **디버그 -> 디버깅하지 않고 시작을** 클릭하거나 **Ctrl + F5** 키를 누릅니다.
* 애플리케이션이 HoloLens 배포된 후 에어 탭 제스처를 사용하여 fitbox를 해제합니다.
* 손을 보기로 이동하고, 손 추적을 시작하기 위해 인덱스 손가락이 하늘로 가리키도록 합니다.
* 손을 왼쪽, 오른쪽, 위아래로 이동합니다.
* 손을 감지한 다음 보기에서 분실할 때 커서가 어떻게 변경되는지 확인합니다.
* 몰입형 헤드셋을 사용할 경우 컨트롤러를 연결하고 연결을 끊어야 합니다. 연결된 컨트롤러는 항상 "사용 가능"하게 되기 때문에 몰입형 디바이스에서는 이러한 피드백이 덜 흥미롭습니다.

## <a name="chapter-2---navigation"></a>2장 - 탐색

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>목표

* 탐색 제스처 이벤트를 사용하여 우주 비행사를 회전합니다.

### <a name="instructions"></a>지침

앱에서 탐색 제스처를 사용하려면 Navigation 제스처가 발생할 때 개체를 회전하도록 **GestureAction.cs를** 편집합니다. 또한 탐색을 사용할 수 있을 때 표시할 피드백을 커서에 추가합니다.

1. **Hierarchy** 패널에서 **CursorWithFeedback 을** 확장합니다.
2. **홀로그램스** 폴더에서 **ScrollFeedback** 자산을 찾습니다.
3. **ScrollFeedback** 프리팹을 **Hierarchy** 의 **CursorWithFeedback** GameObject로 끌어서 놓습니다.
4. **커서WithFeedback을** 클릭합니다.
5. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭합니다.
6. 메뉴에서 검색 상자 **CursorFeedback을 입력합니다.** 검색 결과를 선택합니다.
7. **ScrollFeedback** 개체를 **Hierarchy에서** **Inspector** 의 **Cursor Feedback** 구성 요소에 있는 **Scroll Detected Game Object** 속성으로 끌어서 놓습니다.
8. 계층 **패널에서** **AstroMan** 개체를 선택합니다.
9. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭합니다.
10. 메뉴에서 검색 상자 **제스처 동작** 을 입력합니다. 검색 결과를 선택합니다.

다음으로, Visual Studio **GestureAction.cs를** 엽니다. 코딩 연습 2.c에서 스크립트를 편집하여 다음을 수행합니다.

1. 탐색 제스처가 수행될 때마다 **AstroMan** 개체를 회전합니다.
2. **rotationFactor를** 계산하여 개체에 적용되는 회전의 양을 제어합니다.
3. 사용자가 손을 왼쪽 또는 오른쪽으로 이동할 때 y축을 중심으로 **개체를 회전합니다.**

스크립트에서 코딩 연습 2.c를 완료하거나 아래의 완료된 솔루션으로 코드를 대체합니다.

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

다른 탐색 이벤트는 이미 일부 정보로 채워져 있습니다. GameObject를 Toolkit InputSystem의 모달 스택에 푸시하므로 회전이 시작된 후에는 사용자가 우주 비행사에 집중할 필요가 없습니다. 이에 따라 제스처가 완료되면 스택에서 GameObject를 팝합니다.

### <a name="build-and-deploy"></a>빌드 및 배포

1. Unity에서 애플리케이션을 다시 빌드한 다음 Visual Studio 빌드하고 배포하여 HoloLens 실행합니다.
2. 우주 비행사를 응시하면 커서 양쪽에 두 개의 화살표가 표시됩니다. 이 새 시각적 개체는 우주 비행사를 회전할 수 있음을 나타냅니다.
3. HoloLens 손을 추적하기 시작할 수 있도록 준비 위치(하늘 을 가리키는 인덱스 손가락)에 손을 놓습니다.
4. 우주 비행사를 회전하려면 인덱스 손가락을 손가락 모으기 위치로 낮추고 왼쪽 또는 오른쪽으로 이동하여 NavigationX 제스처를 트리거합니다.

## <a name="chapter-3---hand-guidance"></a>3장 - 손 지침

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>목표

* **손 지침 점수를** 사용하여 손 추적이 손실되는 시기를 예측합니다.
* 커서에 **피드백을** 제공하여 사용자의 손을 카메라의 보기 가장자리 가까이에 놓을 때를 표시합니다.

### <a name="instructions"></a>지침

1. **Hierarchy** 패널에서 **CursorWithFeedback** 개체를 선택합니다.
2. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭합니다.
3. 메뉴에서 손 지침 검색 상자에 를 **입력합니다.** 검색 결과를 선택합니다.
4. **Project** 패널 **홀로그램스** 폴더에서 **HandGuidanceFeedback** 자산을 찾습니다.
5. **HandGuidanceFeedback** 자산을 **검사기** 패널의 **손 지침 표시기** 속성으로 끌어서 놓습니다.

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity에서 애플리케이션을 다시 빌드한 다음 Visual Studio 빌드하고 배포하여 HoloLens 앱을 경험합니다.
* 손을 보기로 가져오고, 인덱스 손가락을 올려 추적합니다.
* 탐색 제스처를 통해 우주 비행사 회전을 시작합니다(인덱스 손가락과 엄지 손가락 모으기).
* 손을 왼쪽, 오른쪽, 위로 및 아래로 이동합니다.
* 손은 제스처 프레임의 가장자리에 가까워지면 커서 옆에 화살표가 나타나 손 추적이 손실될 것임을 경고해야 합니다. 화살표는 추적이 손실되는 것을 방지하기 위해 손을 이동할 방향을 나타냅니다.

## <a name="chapter-4---manipulation"></a>4장 - 조작

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>목표

* 조작 이벤트를 사용하여 우주 비행사를 손으로 이동합니다.
* 커서에 피드백을 제공하여 조작을 사용할 수 있는 시기를 사용자에게 알릴 수 있습니다.

### <a name="instructions"></a>지침

GestureManager.cs 및 AstronautManager.cs를 사용하면 다음을 수행할 수 있습니다.

1. 음성 키워드 "**우주 비행사 이동"을** 사용하여 **조작** 제스처를 사용하도록 설정하고 " 우주 비행사 **회전"을** 사용하여 사용하지 않도록 설정합니다.
2. 조작 제스처 인식기 에 응답하도록 **전환합니다.**

이제 시작하겠습니다.

1. 계층 **구조** 패널에서 빈 GameObject를 새로 만듭니다. 이름을 "**AstronautManager**"로 지정합니다.
2. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭합니다.
3. 메뉴에서 **검색 상자의 우주 비행사 관리자** 를 입력합니다. 검색 결과를 선택합니다.
4. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭합니다.
5. 메뉴에서 검색 상자 **Speech Input Source** 를 입력합니다. 검색 결과를 선택합니다.

이제 우주 비행사의 상호 작용 상태를 제어하는 데 필요한 음성 명령을 추가합니다.

1. 검사기 에서 **키워드** 섹션을 **확장합니다.**
2. **+** 오른쪽의 를 클릭하여 새 키워드를 추가합니다.
3. 키워드를 이동 우주 비행사 로 **입력합니다.** 원하는 경우 키 바로 가기를 자유롭게 추가하세요.
4. **+** 오른쪽의 를 클릭하여 새 키워드를 추가합니다.
5. 키워드를 회전 우주 비행사 로 **입력합니다.** 원하는 경우 키 바로 가기를 자유롭게 추가하세요.
6. 해당 처리기 코드는 **ISpeechHandler.OnSpeechKeywordRecognized** 처리기의 **GestureAction.cs에서** 찾을 수 있습니다.

![4장용 Speech Input Source를 설정하는 방법](images/holograms211-speech.png)

다음으로 커서에 조작 피드백을 설정하겠습니다.

1. **Project** 패널 **홀로그램스** 폴더에서 **PathingFeedback** 자산을 찾습니다.
2. **PathingFeedback 프리팹을** **Hierarchy** 의 **CursorWithFeedback** 개체로 끌어서 놓습니다.
3. **Hierarchy(계층 구조)** 패널에서 **CursorWithFeedback(커서WithFeedback)을** 클릭합니다.
4. **Inspector** 의 **커서 피드백** 구성 요소에서 **Pathing 검색 된 게임 개체** 속성에 **pathingfeedback** 개체를 끌어서 놓습니다. 

이제 **GestureAction** 에 코드를 추가 하 여 다음을 사용 하도록 설정 해야 합니다.

1. **IManipulationHandler** 함수에 코드를 추가 합니다 .이 함수는 **조작** 제스처가 검색 될 때 astronaut를 이동 합니다.
2. **이동 벡터** 를 계산 하 여 astronaut 위치에 따라 이동 해야 하는 위치를 결정 합니다.
3. Astronaut를 새 위치로 **이동** 합니다.

**GestureAction** 에서 연습 4-5를 완료 하거나 아래에서 완성 된 솔루션을 사용 합니다.

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity에서 다시 빌드한 다음 Visual Studio에서 빌드하고 배포 하 여 HoloLens에서 앱을 실행 합니다.
* HoloLens 앞으로 손을 이동 하 고 추적할 수 있도록 인덱스 손가락을 올립니다.
* Astronaut 위에 커서를 올려 둡니다.
* Astronaut를 조작 제스처로 이동 하려면 ' Move Astronaut '를 표시 합니다.
* 이제 프로그램에서 조작 이벤트에 응답 하는 것을 나타내기 위해 커서 주위에 네 개의 화살표가 표시 됩니다.
* 인덱스 손가락을 엄지 단추 아래로 낮추고 pinched을 함께 유지 합니다.
* 손을 움직이면 astronaut도 이동 합니다 (이는 조작).
* Astronaut 조작을 중지 하도록 인덱스 손가락을 올립니다.
* 참고: 손을 이동 하기 전에 ' Move Astronaut '를 표시 하지 않으면 탐색 제스처가 대신 사용 됩니다.
* Rotatable 상태로 돌아가려면 ' Astronaut 회전 ' 이라고 합니다.

## <a name="chapter-5---model-expansion"></a>5 장-모델 확장

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>목표

* Astronaut 모델을 사용자가 상호 작용할 수 있는 여러 개의 작은 조각으로 확장 합니다.
* 탐색 및 조작 제스처를 사용 하 여 각 부분을 개별적으로 이동 합니다.

### <a name="instructions"></a>지침

이 섹션에서는 다음 작업을 수행 합니다.

1. 새 "**모델 확장**" 키워드를 추가 하 여 astronaut 모델을 확장 합니다.
2. 새 키워드 "**모델 다시 설정**"을 추가 하 여 모델을 원래 형식으로 반환 합니다.

이전 장의 음성 입력 소스에 두 개 이상의 키워드를 추가 하 여이 작업을 수행 합니다. 또한 인식 이벤트를 처리 하는 또 다른 방법을 보여 드리겠습니다.

1. **검사기** 에서 **AstronautManager** 를 클릭 하 고 **검사기** 에서 **키워드** 섹션을 확장 합니다.
2. 오른쪽의를 클릭 **+** 하 여 새 키워드를 추가 합니다.
3. 키워드를 **확장 모델** 로 입력 합니다. 원한다 면 키 바로 가기를 자유롭게 추가할 수 있습니다.
4. 오른쪽의를 클릭 **+** 하 여 새 키워드를 추가 합니다.
5. 키워드를 **모델 다시 설정** 으로 입력 합니다. 원한다 면 키 바로 가기를 자유롭게 추가할 수 있습니다.
6. **검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.
7. 메뉴의 검색 상자에 **음성 입력 처리기** 를 입력 합니다. 검색 결과를 선택 합니다.
8. 이 명령은 GameObject에 관계 없이 작동 하기 때문에 **전역 수신기** 를 선택 합니다.
9. 단추를 클릭 **+** 하 고 키워드 드롭다운에서 **모델 확장** 을 선택 합니다.
10. **+** 응답 아래를 클릭 하 고 **계층** 의 **AstronautManager** 을 **None (Object)** 필드로 끕니다.
11. 이제 **함수 없음** 드롭다운을 클릭 하 고 **AstronautManager**, **ExpandModelCommand** 를 차례로 선택 합니다.
12. 음성 입력 처리기의 단추를 클릭 **+** 하 고 키워드 드롭다운에서 **모델 다시 설정** 을 선택 합니다.
13. **+** 응답 아래를 클릭 하 고 **계층** 의 **AstronautManager** 을 **None (Object)** 필드로 끕니다.
14. 이제 **함수 없음** 드롭다운을 클릭 하 고 **AstronautManager**, **resetmodelcommand** 를 차례로 선택 합니다.

![5 장의 음성 입력 소스 및 처리기를 설정 하는 방법](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>빌드 및 배포

* 사용해 보세요. HoloLens에 앱을 빌드하고 배포 합니다.
* **모델을 확장** 하 여 확장 된 astronaut 모델을 표시 한다고 가정 합니다.
* **탐색** 을 사용 하 여 astronaut 짝패의 개별 부분을 회전 합니다.
* **Astronaut를 이동한** 다음 **조작** 을 사용 하 여 Astronaut 짝패의 개별 부분을 이동 합니다.
* **Astronaut를 회전** 하 여 조각을 다시 회전 한다고 가정 합니다.
* **모델을 다시 설정** 하 여 원래 형식으로 astronaut를 반환 한다고 가정 합니다.

## <a name="the-end"></a>끝

축하합니다! 이제 **MR 입력 211: 제스처** 를 완료 했습니다.

* 직접 추적, 탐색 및 조작 이벤트를 검색 하 고 대응 하는 방법을 알고 있습니다.
* 탐색 제스처와 조작 제스처의 차이점을 이해 하 고 있습니다.
* 커서를 변경 하 여 손을 감지 했을 때, 손을 잃어 버릴 때, 개체가 서로 다른 상호 작용을 지 원하는 경우 (탐색 vs 조작)에 대 한 시각적 피드백을 제공 하도록 커서를 변경 하는 방법을 알고 있습니다.