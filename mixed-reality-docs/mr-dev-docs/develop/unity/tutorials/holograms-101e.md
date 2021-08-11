---
title: HoloLens(1세대) 기본 사항 101E - 에뮬레이터를 사용하여 프로젝트 완료
description: Unity, Visual Studio 및 HoloLens Emulator 사용하여 이 코딩 연습을 수행하여 홀로그램 애플리케이션의 기본 내용을 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 혼합 현실, Windows Mixed Reality, 홀로그램, academy, 자습서, 에뮬레이터, HoloLens, Mixed Reality Academy, unity, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, Windows 10, 응시, 제스처, 음성 입력, 공간 소리, 공간 매핑
ms.openlocfilehash: 3cbd1fbba8d4dac4a1d3d0ac1b78a38ed7c8bfa5a7f0b5b3b8d61e9a87f924dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200843"
---
# <a name="hololens-1st-gen-basics-101e-complete-project-with-emulator"></a>HoloLens(1세대) 기본 사항 101E: 에뮬레이터를 통해 프로젝트 완료

>[!IMPORTANT]
>Mixed Reality Academy 자습서는 HoloLens(1세대), Unity 2017 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다. 이러한 **_자습서는_** HoloLens 2 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 않으며 최신 버전의 Unity와 호환되지 않을 수 있습니다.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2에 대한 [새로운 자습서 시리즈](mrlearning-base.md)가 게시되었습니다.

<br>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

이 자습서에서는 [응시,](../../../design/gaze-and-commit.md) [제스처,](../../../design/gaze-and-commit.md#composite-gestures) [음성 입력,](../../../design/voice-input.md) [공간 소리](../../../design/spatial-sound.md) 및 [공간 매핑을](../../../design/spatial-mapping.md)포함하여 HoloLens 대한 핵심 Windows Mixed Reality 기능을 보여 주는 Unity로 빌드된 전체 프로젝트를 안내합니다. 자습서를 완료하는 데 약 1시간이 소요됩니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 기본 101E: 에뮬레이터를 사용하여 프로젝트 수행</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전에

### <a name="prerequisites"></a>필수 구성 요소

* 올바른 도구로 구성된 Windows 10 [PC입니다.](../../install-the-tools.md)

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일을](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) 다운로드합니다. Unity 2017.2 이상 필요
  * Unity 5.6 지원이 여전히 필요한 경우 [이 릴리스를](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)사용하세요.
  * Unity 5.5 지원이 여전히 필요한 경우 [이 릴리스를](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)사용하세요.
  * Unity 5.4 지원이 여전히 필요한 경우 [이 릴리스를](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)사용하세요.
* 바탕 화면 또는 기타 쉽게 도달할 수 있는 위치에 파일을 보관 해제합니다. 폴더 이름을 **Origami** 로 유지합니다.

>[!NOTE]
>다운로드하기 전에 소스 코드를 살펴보려면 GitHub 에서 [사용할 수 있습니다.](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)

## <a name="chapter-1---holo-world"></a>1장 - "Holo" world

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

이 장에서는 첫 번째 Unity 프로젝트를 설치하고 빌드 및 배포 프로세스를 단계별로 진행합니다.

### <a name="objectives"></a>목표

* 홀로그램 개발을 위한 Unity를 설정합니다.
* 홀로그램을 만듭니다.
* 만든 홀로그램을 참조하세요.

### <a name="instructions"></a>지침

* Unity를 시작합니다.
* **열기** 를 선택합니다.
* 이전에 보관하지 않은 **Origami** 폴더로 위치를 입력합니다.
* **Origami를** 선택하고 **폴더 선택을** 클릭합니다.
* 새 장면 파일   /  **저장 장면을 로 저장합니다.**
* 장면 이름을 **Origami로** 지정하고 **저장** 단추를 누릅니다.

#### <a name="setup-the-main-camera"></a>기본 카메라 설정

* **계층 구조 패널** 에서 **주 카메라** 를 선택합니다.
* **검사기에서** 변환 위치를 **0,0,0으로** 설정합니다.
* 플래그 **지우기** 속성을 찾고 드롭다운을 **Skybox에서** **단색** 으로 변경합니다.
* **백그라운드** 필드를 클릭하여 색 선택을 엽니다.
* **R, G, B 및 A** 를 **0** 으로 설정합니다.

#### <a name="setup-the-scene"></a>장면 설정

* 계층 **구조 패널에서** 빈 만들기 및 **만들기를** 클릭합니다. 
* 새 **GameObject를** 마우스 오른쪽 단추로 클릭하고 이름 바꾸기를 선택합니다. GameObject의 이름을 **OrigamiCollection** 로 바꿉니다.
* **Project** **패널의 홀로그램스** 폴더에서:
  * **스테이지를** 계층 구조로 끌어 **OrigamiCollection** 의 자식이 됩니다.
  * **Sphere1을** 계층 구조로 끌어 **OrigamiCollection** 의 자식이 됩니다.
  * **Sphere2를** 계층 구조로 끌어 **OrigamiCollection** 의 자식이 됩니다.
* 계층 구조 **패널에서** **Directional Light** 개체를 마우스 오른쪽 단추로 클릭하고 **삭제를** 선택합니다.
* **홀로그램스** 폴더에서 **조명을** **계층 패널** 의 루트로 끕니다.
* **계층** 구조에서 **OrigamiCollection 을** 선택합니다.
* **검사기에서** 변환 위치를 **0, -0.5, 2.0으로** 설정합니다.
* Unity에서 **재생** 단추를 눌러 홀로그램을 미리 봅니다.
* 미리 보기 창에 Origami 개체가 표시됩니다.
* 미리 보기 모드를 중지하려면 **재생을** 두 번째로 누릅니다.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Unity에서 Visual Studio 프로젝트 내보내기

* Unity에서 **파일 > 빌드 설정** 선택합니다.
* **플랫폼** 목록에서 **Windows 스토어를** 선택하고 **플랫폼 전환을** 클릭합니다.
* **SDK를** **유니버설 10으로** 설정하고 **빌드 형식을** **D3D** 로 설정합니다.
* **Unity C# 프로젝트를 확인합니다.**
* **열린 장면 추가를** 클릭하여 장면을 추가합니다.
* **플레이어 설정... 를** 클릭합니다.
* 검사기 패널에서 **Windows 스토어 로고** 를 선택합니다. 그런 다음 **설정 게시를** 선택합니다.
* **기능** 섹션에서 **마이크** 및 **SpatialPerception** 기능을 선택합니다.
* 빌드 설정 창으로 돌아가 **빌드를** 클릭합니다.
* "App"이라는 **새 폴더를** 만듭니다.
* **앱 폴더** 를 한 번 클릭합니다.
* **폴더 선택을** 누릅니다.
* Unity가 완료되면 파일 탐색기 창이 나타납니다.
* **App** 폴더를 엽니다.
* **Origami Visual Studio 솔루션을 엽니다.**
* Visual Studio 위쪽 도구 모음을 사용하여 대상을 디버그에서 **릴리스로,** ARM에서 **X86으로** 변경합니다.
  * 디바이스 단추 옆의 화살표를 클릭하고 **HoloLens Emulator** 선택합니다.
  * **디버그 -> 디버깅하지 않고 시작을** 클릭하거나 **Ctrl + F5** 키를 누릅니다.
  * 잠시 후 에뮬레이터가 Origami 프로젝트로 시작됩니다. 에뮬레이터 를 처음 시작할 때 [에뮬레이터를](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)시작하는 데 15분 정도 걸릴 수 있습니다. 시작되면 닫지 마십시오.

## <a name="chapter-2---gaze"></a>2장 - 응시

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

이 장에서는 홀로그램과 상호 작용하는 세 가지 방법 중 첫 번째 방법인 [응시를](../../../design/gaze-and-commit.md)소개합니다.

### <a name="objectives"></a>목표

* 세계로 잠긴 커서를 사용하여 응시를 시각화합니다.

### <a name="instructions"></a>지침

* Unity 프로젝트로 돌아가기 빌드 설정 창이 열려 있는 경우 닫습니다.
* **Project** **패널에서 홀로그램스** 폴더를 선택합니다.
* **Cursor** 개체를 루트 수준의 **계층 패널로** 끕니다.
* **Cursor** 개체를 두 번 클릭하여 자세히 살펴봅니다.
* Project 패널에서 **Scripts** 폴더를 마우스 오른쪽 단추로 클릭합니다.
* **만들기** 하위 메뉴를 클릭합니다.
* **C# 스크립트를** 선택합니다.
* 스크립트 이름을 **WorldCursor 로 지정합니다.** 참고: 이름은 대/소문자 구분입니다. .Cs 확장명을 추가할 필요가 없습니다.
* **계층 패널** 에서 **Cursor** 개체를 선택 합니다.
* **WorldCursor** 스크립트를 **검사기 패널로** 끌어 놓습니다.
* **WorldCursor** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
* 이 코드를 복사 하 여 **WorldCursor** 에 붙여넣고 **모두 저장** 합니다.

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* **빌드 설정 > 파일** 에서 앱을 다시 빌드합니다.
* 에뮬레이터에 배포 하는 데 이전에 사용한 Visual Studio 솔루션으로 돌아갑니다.
* 메시지가 표시 되 면 ' 모두 다시 로드 '를 선택 합니다.
* **디버그를 클릭 하 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5** 를 누릅니다.
* Xbox 컨트롤러를 사용 하 여 장면을 살펴볼 수 있습니다. 커서가 개체 모양과 상호 작용 하는 방식을 확인 합니다.

## <a name="chapter-3---gestures"></a>3 장-제스처

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

이 장에서는 [제스처](../../../design/gaze-and-commit.md#composite-gestures)에 대 한 지원을 추가 합니다. 사용자가 용지 구를 선택 하면 Unity의 물리학 엔진을 사용 하 여 무게를 설정 하 여 구를 설정 합니다.

### <a name="objectives"></a>목표

* 선택 제스처를 사용 하 여 holograms를 제어 합니다.

### <a name="instructions"></a>지침

먼저 선택 제스처를 검색할 수 있는 것 보다 스크립트를 만듭니다.

* **Scripts** 폴더에서 **GazeGestureManager** 라는 스크립트를 만듭니다.
* **GazeGestureManager** 스크립트를 계층의 **OrigamiCollection** 개체로 끌어 옵니다.
* Visual Studio에서 **GazeGestureManager** 스크립트를 열고 다음 코드를 추가 합니다.

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Scripts 폴더에 **SphereCommands** 이라는 다른 스크립트를 만듭니다.
* 계층 구조 뷰에서 **OrigamiCollection** 개체를 확장 합니다.
* **SphereCommands** 스크립트를 계층 패널의 **Sphere1** 개체로 끌어 옵니다.
* **SphereCommands** 스크립트를 계층 패널의 **Sphere2** 개체로 끌어 옵니다.
* 편집을 위해 Visual Studio에서 스크립트를 열고 기본 코드를 다음으로 바꿉니다.

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* HoloLens 에뮬레이터에 앱을 내보내고 빌드하고 배포 합니다.
* 장면을 중심으로 살펴보고 구 중 하나를 중심으로 합니다.
* Xbox 컨트롤러에서 **A** 단추를 누르거나 스페이스바를 눌러 선택 제스처를 시뮬레이션 합니다.

## <a name="chapter-4---voice"></a>4 장-음성

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

이 장에서는 두 개의 [음성 명령](../../../design/voice-input.md)에 대 한 지원을 추가 합니다. "다시 설정"을 사용 하 여 삭제 된 구를 원래 위치로 반환 하 고, "삭제 구"를 사용 하 여 구를 설정 합니다.

### <a name="objectives"></a>목표

* 백그라운드에서 항상 수신 대기 하는 음성 명령을 추가 합니다.
* 음성 명령에 반응 하는 홀로그램을 만듭니다.

### <a name="instructions"></a>지침

* **Scripts** 폴더에서 **SpeechManager** 라는 스크립트를 만듭니다.
* **SpeechManager** 스크립트를 계층의 **OrigamiCollection** 개체로 끌어 옵니다.
* Visual Studio에서 **SpeechManager** 스크립트를 엽니다.
* 이 코드를 복사 하 여 **SpeechManager** 에 붙여넣고 **모두 저장** 합니다.

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Visual Studio에서 **SphereCommands** 스크립트를 엽니다.
* 다음과 같이 스크립트를 업데이트 합니다.

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* HoloLens 에뮬레이터에 앱을 내보내고 빌드하고 배포 합니다.
* 에뮬레이터가 PC의 마이크를 지원 하 고 음성에 응답 합니다. 커서가 구 중 하나에 있도록 보기를 조정 하 고 "삭제 구" 라고 표시 합니다.
* 초기 위치로 다시 전환 하기 위해 "**세계 재설정**" 이라고 말할 수 있습니다.

## <a name="chapter-5---spatial-sound"></a>5 장-공간 소리

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

이 장에서는 앱에 음악을 추가한 다음 특정 작업에 대 한 음향 효과를 트리거합니다. 3D 공간에서 소리를 특정 위치에 제공 하기 위해 [공간 소리](../../../design/spatial-sound.md) 를 사용할 예정입니다.

### <a name="objectives"></a>목표

* 전 세계에서 holograms를 들어봅니다.

### <a name="instructions"></a>지침

* Unity의 상단 메뉴에서 선택 **> Project 설정 > 오디오를 편집** 합니다.
* **Spatializer 플러그 인** 설정을 찾아 **MS hrtf Spatializer** 를 선택 합니다.
* **홀로그램스** 폴더에서 **외계** 개체를 계층 패널의 **OrigamiCollection** 개체로 끌어 옵니다.
* **OrigamiCollection** 를 선택 하 고 **오디오 원본** 구성 요소를 찾습니다. 다음 속성을 변경 합니다.
  * **Spatialize** 속성을 확인 합니다.
  * 절전 모드 **해제를 확인 합니다.**
  * 슬라이더를 오른쪽으로 끌어 **공간 Blend** 를 **3d** 로 변경 합니다.
  * **Loop** 속성을 선택 합니다.
  * **3d 소리 설정** 를 확장 하 고 **Doppler 수준** 에 대해 **0.1** 을 입력 합니다.
  * **볼륨 Rolloff** 를 **로그 Rolloff** 로 설정 합니다.
  * **최대 거리** 를 **20** 으로 설정 합니다.
* **Scripts** 폴더에서 **SphereSounds** 라는 스크립트를 만듭니다.
* **SphereSounds** 를 계층의 **Sphere1** 및 **Sphere2** 개체로 끌어옵니다.
* Visual Studio에서 **SphereSounds** 을 열고 다음 코드를 업데이트 하 고 **모두 저장** 합니다.

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* 스크립트를 저장 하 고 Unity로 돌아갑니다.
* HoloLens 에뮬레이터에 앱을 내보내고 빌드하고 배포 합니다.
* 전체 효과를 얻으려면 헤드폰을 착용 하 고, 소리 변화를 들으려면 스테이지에서 더 가깝게 이동 합니다.

## <a name="chapter-6---spatial-mapping"></a>6 장-공간 매핑

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

이제 [공간 매핑을](../../../design/spatial-mapping.md) 사용 하 여 실제 개체에 게임 보드를 추가 하겠습니다.

### <a name="objectives"></a>목표

* 실제 세계를 가상 세계에 가져오세요.
* 가장 중요 한 위치에 holograms을 두십시오.

### <a name="instructions"></a>지침

* Project 패널에서 **홀로그램스** 폴더를 클릭 합니다.
* **공간 매핑** 자산을 **계층** 의 루트로 끌어 옵니다.
* 계층에서 **공간 매핑** 개체를 클릭 합니다.
* **검사기 패널** 에서 다음 속성을 변경 합니다.
  * **시각적 개체 메시 그리기** 상자를 선택 합니다.
  * **그리기 자료** 를 찾고 오른쪽에 있는 원을 클릭 합니다. 위쪽의 검색 필드에 "**골격형**"을 입력 합니다. 결과를 클릭 한 다음 창을 닫습니다.
* HoloLens 에뮬레이터에 앱을 내보내고 빌드하고 배포 합니다.
* 앱이 실행 되 면 이전에 스캔 한 실제 실내의 메쉬가 와이어 프레임으로 렌더링 됩니다.
* 롤링 구가 단계를 어떻게 진행 하는지 확인 합니다.

이제 OrigamiCollection를 새 위치로 이동 하는 방법을 보여 드리겠습니다.

* **Scripts** 폴더에서 **TapToPlaceParent** 라는 스크립트를 만듭니다.
* **계층** 에서 **OrigamiCollection** 를 확장 하 고 **단계** 개체를 선택 합니다.
* **TapToPlaceParent** 스크립트를 Stage 개체로 끌어 놓습니다.
* Visual Studio에서 **TapToPlaceParent** 스크립트를 열고 다음으로 업데이트 합니다.

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* 앱을 내보내고 빌드하고 배포 합니다.
* 이제 선택 제스처 (**a** 또는 스페이스바)를 사용 하 고, 새 위치로 이동 하 고, 선택 제스처를 다시 사용 하 여 특정 위치에 게임을 gazing 수 있습니다.

## <a name="the-end"></a>끝

이 자습서의 끝입니다!

다음에 대해 알아보았습니다.

* Unity에서 holographic 앱을 만드는 방법
* 응시, 제스처, 음성, 소리 및 공간 매핑을 활용 하는 방법입니다.
* Visual Studio를 사용 하 여 앱을 빌드하고 배포 하는 방법입니다.

이제 사용자 고유의 holographic apps를 만들 준비가 되었습니다.

## <a name="see-also"></a>추가 정보

* [MR 기본 101: 디바이스를 사용하는 완전한 프로젝트](holograms-101.md)
* [응시](../../../design/gaze-and-commit.md)
* [헤드 게이즈 및 커밋](../../../design/gaze-and-commit.md)
* [음성 입력 ](../../../design/voice-input.md)
* [공간 음향](../../../design/spatial-sound.md)
* [공간 매핑](../../../design/spatial-mapping.md)