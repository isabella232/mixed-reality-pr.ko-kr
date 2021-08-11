---
title: HoloLens(1세대) 기본 사항 101 - 디바이스를 사용하여 프로젝트 완료
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 Windows Mixed Reality의 기본 사항을 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 혼합 현실, Windows Mixed Reality, HoloLens, 홀로그램, 아카데미, 자습서, HoloLens, 혼합 현실 아카데미, unity, 혼합 현실 헤드셋, Windows mixed reality 헤드셋, 가상 현실 헤드셋, Windows 10
ms.openlocfilehash: 63219edebeb63dbf4589e8162f8dc1bab83275c38f29b106db9bae234cdabde0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200963"
---
# <a name="hololens-1st-gen-basics-101-complete-project-with-device"></a>HoloLens (첫 번째 gen) 기본 사항 101: 장치를 사용 하 여 프로젝트 완료

<br>

>[!IMPORTANT]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen), Unity 2017 및 혼합 현실 모던 헤드셋을 고려 하 여 설계 되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다. 이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않으며 최신 버전의 Unity와 호환 되지 않을 수 있습니다.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2에 대한 [새로운 자습서 시리즈](mrlearning-base.md)가 게시되었습니다.

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

이 자습서에서는 [응시](../../../design/gaze-and-commit.md), [제스처](../../../design/gaze-and-commit.md#composite-gestures), [음성 입력](../../../design/voice-input.md), [공간 음향](../../../design/spatial-sound.md) 및 [공간 매핑을](../../../design/spatial-mapping.md)비롯 한 HoloLens의 핵심 Windows Mixed Reality 기능을 보여 주는 Unity 기반의 전체 프로젝트를 안내 합니다.

자습서를 완료 하는 데 약 1 시간이 소요 됩니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 기본 101: 디바이스를 사용하여 프로젝트 수행</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전에

### <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구로](../../install-the-tools.md)구성 된 Windows 10 PC.
* [개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 장치입니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) 을 다운로드 합니다. Unity 2017.2 이상이 필요 합니다.
  * Unity 5.6 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)를 사용 하세요.
  * Unity 5.5 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)를 사용 하세요.
  * Unity 5.4 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)를 사용 하세요.
* 바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다. 폴더 이름을 **종이 접기** 로 유지 합니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)있습니다.

## <a name="chapter-1---holo-world"></a>1 장-"Holo" 세계

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

이 장에서는 첫 번째 Unity 프로젝트를 설정 하 고 빌드 및 배포 프로세스를 단계별로 진행 합니다.

### <a name="objectives"></a>목표

* Holographic 개발용 Unity를 설정 합니다.
* 홀로그램을 만듭니다.
* 만든 홀로그램을 확인 하세요.

### <a name="instructions"></a>지침

* Unity를 시작합니다.
* **열기** 를 선택합니다.
* 이전에 보관 하지 않은 **종이 접기** 폴더로 위치를 입력 합니다.
* **종이** 를 선택 하 고 **폴더 선택** 을 클릭 합니다.
* **종이** 에는 장면이 포함 되지 않으므로 빈 기본 장면을 새 파일에 저장 합니다. **파일** 에  /  **장면 저장** 을 사용 합니다.
* 새 장면 **종이** 의 이름을로 하 고 **저장** 단추를 누릅니다.

#### <a name="setup-the-main-virtual-camera"></a>기본 가상 카메라 설정

* **계층 구조 패널** 에서 **주 카메라** 를 선택합니다.
* **Inspector** 의 변환 위치를 **0, 0, 0** 으로 설정 합니다.
* **Clear Flags** 속성을 찾고 Dropdown을 **Skybox** 에서 **Solid color** 로 변경 합니다.
* **백그라운드** 필드를 클릭하여 색 선택을 엽니다.
* **R, G, B 및 A** 를 **0** 으로 설정합니다.

#### <a name="setup-the-scene"></a>장면 설정

* **계층 패널** 에서 **만들기** 를 클릭 하 고 **빈 상태로 만들기** 를 클릭 합니다.
* 새 **GameObject** 를 마우스 오른쪽 단추로 클릭 하 고 이름 바꾸기를 선택 합니다. GameObject의 이름을 **OrigamiCollection** 로 바꿉니다.
* Project 패널의 **홀로그램스** 폴더에서 자산을 확장 하 고 홀로그램스를 선택 하거나 Project 패널에서 홀로그램스 폴더를 두 번 클릭 합니다.
  * **스테이지** 를 계층 구조로 끌어 **OrigamiCollection** 의 자식으로 만듭니다.
  * **Sphere1** 를 계층 구조로 끌어 **OrigamiCollection** 의 자식으로 만듭니다.
  * **Sphere2** 를 계층 구조로 끌어 **OrigamiCollection** 의 자식으로 만듭니다.
* **계층 패널** 에서 **방향 광원** 개체를 마우스 오른쪽 단추로 클릭 하 고 **삭제** 를 선택 합니다.
* **홀로그램스** 폴더에서 **조명을** **계층 패널** 의 루트로 끕니다.
* **계층** 에서 **OrigamiCollection** 를 선택 합니다.
* **검사기** 에서 변환 위치를 **0,-0.5, 2.0** 로 설정 합니다.
* Holograms를 미리 보려면 Unity의 **재생** 단추를 누릅니다.
* 미리 보기 창에 종이 개체를 표시 해야 합니다.
* **재생** 을 두 번 눌러 미리 보기 모드를 중지 합니다.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Unity에서 Visual Studio로 프로젝트를 내보냅니다.

* Unity에서 **파일 > 빌드 설정** 를 선택 합니다.
* **플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 클릭 합니다.
* **SDK** 를 **Universal 10** 으로 설정 하 고 **빌드 형식을** **D3D** 로 설정 합니다.
* **Unity c # 프로젝트** 를 확인 합니다.
* 열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.
* **빌드** 를 클릭한 다음
* 표시 되는 파일 탐색기 창에서 "App" 이라는 **새 폴더** 를 만듭니다.
* 단일 **앱 폴더** 를 클릭 합니다.
* **폴더 선택** 을 누릅니다.
* Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.
* **앱** 폴더를 엽니다.
* (두 번 클릭) **종이** 를 엽니다.
* Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86** 으로 변경 합니다.
* 장치 단추 옆의 화살표를 클릭 하 고 **원격 컴퓨터** 를 선택 하 여 wi-fi를 통해 배포 합니다.
  * **주소** 를 HoloLens의 이름 또는 IP 주소로 설정 합니다. 장치 IP 주소를 모르는 경우 **설정 > 네트워크 & 인터넷 > 고급 옵션** 을 확인 하거나 Cortana **"안녕하세요 Cortana, 내 IP 주소는 무엇입니까?"** 를 확인 합니다.
  * HoloLens usb를 통해 연결 된 경우 **장치** 를 선택 하 여 usb를 통해 배포할 수 있습니다.
  * **인증 모드** 를 **유니버설** 으로 설정 된 상태로 둡니다.
  * **선택** 클릭

* **디버그 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5** 를 누릅니다. 처음으로 장치에 배포 하는 경우 [Visual Studio와 쌍](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)으로 연결 해야 합니다.

* 이제 종이 접기 프로젝트가 작성 되 고 HoloLens에 배포 된 다음를 실행 합니다.
* HoloLens에 추가 하 고 새 holograms를 확인 하세요.

## <a name="chapter-2---gaze"></a>2 장-응시

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

이 장에서는 holograms와 상호 작용 하는 세 가지 방법, 즉 [응시](../../../design/gaze-and-commit.md)를 소개 하겠습니다.

### <a name="objectives"></a>목표

* 전 세계 잠긴 커서를 사용 하 여 응시를 시각화 합니다.

### <a name="instructions"></a>지침

* Unity 프로젝트로 돌아가서 빌드 설정 창이 열려 있으면 닫습니다.
* **Project 패널** 에서 **홀로그램스** 폴더를 선택 합니다.
* **커서** 개체를 루트 수준에서 **계층 패널로** 끕니다.
* **커서** 개체를 두 번 클릭 하면 자세히 살펴볼 수 있습니다.
* Project 패널에서 **Scripts** 폴더를 마우스 오른쪽 단추로 클릭 합니다.
* **만들기** 하위 메뉴를 클릭 합니다.
* **C # 스크립트** 를 선택 합니다.
* 스크립트 이름을 **WorldCursor 로 지정합니다.** 참고: 이름은 대/소문자 구분입니다. .cs 확장을 추가할 필요가 없습니다.
* **계층 패널에서** **커서** 개체를 선택합니다.
* **WorldCursor** 스크립트를 **검사기 패널** 로 끌어서 놓습니다.
* **WorldCursor** 스크립트를 두 번 클릭하여 Visual Studio 엽니다.
* 이 코드를 복사하여 **WorldCursor.cs에** 붙여넣고 **모두 저장합니다.**

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

            // Move the cursor to the point where the raycast hit.
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

* 파일 > 빌드 설정 에서 **앱을 다시 빌드합니다.**
* 이전에 HoloLens 배포하는 데 사용한 Visual Studio 솔루션으로 돌아갑니다.
* 메시지가 표시되면 '모두 다시 로드'를 선택합니다.
* **디버그 -> 디버깅하지 않고 시작을** 클릭하거나 **Ctrl + F5** 키를 누릅니다.
* 이제 장면을 살펴보고 커서가 개체의 모양과 상호 작용하는 방법을 알아차리고 있습니다.

## <a name="chapter-3---gestures"></a>3장 - 제스처

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

이 장에서는 제스처에 대한 지원을 [추가합니다.](../../../design/gaze-and-commit.md#composite-gestures) 사용자가 용지 구를 선택하면 Unity의 물리학 엔진을 사용하여 무게를 켜서 구가 떨어지도록 만들겠습니다.

### <a name="objectives"></a>목표

* 선택 제스처를 통해 홀로그램을 제어합니다.

### <a name="instructions"></a>지침

스크립트를 만든 다음, 선택 제스처를 감지할 수 있습니다.

* **Scripts** 폴더에서 **GazeGestureManager라는 스크립트를** 만듭니다.
* **GazeGestureManager** 스크립트를 Hierarchy의 **OrigamiCollection** 개체로 끕니다.
* Visual Studio **GazeGestureManager** 스크립트를 열고 다음 코드를 추가합니다.

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
    void Awake()
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

* Scripts 폴더에 다른 스크립트를 만듭니다. 이번에는 **SphereCommands 입니다.**
* 계층 뷰에서 **OrigamiCollection** 개체를 확장합니다.
* **SphereCommands 스크립트를** 계층 패널의 **Sphere1** 개체로 끕니다.
* **SphereCommands 스크립트를** 계층 패널의 **Sphere2** 개체로 끕니다.
* 편집을 위해 Visual Studio 스크립트를 열고 기본 코드를 다음으로 대체합니다.

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

* HoloLens 앱을 내보내고, 빌드하고, 배포합니다.
* 구 중 하나를 살펴봅니다.
* 선택 제스처를 수행하고 아래 표면에 구가 놓이는 것을 관찰합니다.

## <a name="chapter-4---voice"></a>4장 - 음성

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

이 장에서는 두 개의 음성 [명령에](../../../design/voice-input.md)대한 지원을 추가합니다. 즉, 삭제된 구를 원래 위치로 반환하는 "Reset world"와 구가 떨어지도록 하는 "Drop sphere"를 추가합니다.

### <a name="objectives"></a>목표

* 항상 백그라운드에서 수신 대기하는 음성 명령을 추가합니다.
* 음성 명령에 반응하는 홀로그램을 만듭니다.

### <a name="instructions"></a>지침

* **Scripts** 폴더에서 **SpeechManager라는** 스크립트를 만듭니다.
* **SpeechManager** 스크립트를 Hierarchy의 **OrigamiCollection** 개체로 끌어다 놓습니다.
* Visual Studio **SpeechManager** 스크립트를 엽니다.
* 이 코드를 복사하여 **SpeechManager.cs에** 붙여넣고 **모두 저장합니다.**

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

* Visual Studio **SphereCommands** 스크립트를 엽니다.
* 다음과 같이 읽도록 스크립트를 업데이트합니다.

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

* HoloLens 앱을 내보내고, 빌드하고, 배포합니다.
* 구 중 하나를 살펴보고 " Drop **Sphere"라고** 말합니다.
* 초기 위치로 다시 가져오려면 **"Reset World"라고** 말합니다.

## <a name="chapter-5---spatial-sound"></a>5장 - 공간 소리

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

이 장에서는 앱에 음악이 추가된 다음 특정 작업에 대한 음향 효과를 트리거합니다. [공간 소리를](../../../design/spatial-sound.md) 사용하여 3D 공간에서 특정 위치를 소리에 제공합니다.

### <a name="objectives"></a>목표

* 전 세계의 홀로그램을 들었습니다.

### <a name="instructions"></a>지침

* Unity의 위쪽 메뉴에서 **> Project 설정 > 오디오 편집을** 선택합니다.
* 오른쪽의 검사기 패널에서 **Spatializer 플러그 인** 설정을 찾아 **MS HRTF Spatializer** 를 선택합니다.
* **Project** 패널의 홀로그램스 폴더에서 **Ambience** 개체를 계층 구조 패널의 **OrigamiCollection** 개체로 끌어 갑니다.
* **OrigamiCollection을** 선택하고 검사기 패널에서 **오디오 원본** 구성 요소를 찾습니다. 다음 속성을 변경합니다.
  * **Spatialize** 속성을 확인합니다.
  * Play **On Awake을** 확인합니다.
  * 슬라이더를 오른쪽으로 끌어 **Spatial Blend를** **3D로** 변경합니다. 슬라이더를 이동하면 값이 0에서 1로 변경되어야 합니다.
  * **루프** 속성을 확인합니다.
  * **3D Sound 설정** 확장하고 **Doppler Level** 에 **0.1을** 입력합니다.
  * **볼륨 롤오프를** **로그 롤오프** 로 설정합니다.
  * **최대 거리를** **20으로** 설정합니다.
* **Scripts** 폴더에서 **SphereSounds라는 스크립트를 만듭니다.**
* **SphereSounds를** 계층 구조의 **Sphere1** 및 **Sphere2** 개체로 끌어서 놓습니다.
* Visual Studio **SphereSounds를** 열고, 다음 코드를 업데이트하고, **모두 저장합니다.**

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

* 스크립트를 저장하고 Unity로 돌아갑니다.
* HoloLens 앱을 내보내고, 빌드하고, 배포합니다.
* 스테이지에서 더 가깝게 이동하고 나란히 전환하여 소리가 변하는 것을 들었습니다.

## <a name="chapter-6---spatial-mapping"></a>6장 - 공간 매핑

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

이제 [공간 매핑을](../../../design/spatial-mapping.md) 사용하여 실제 세계의 실제 개체에 게임 보드를 배치하겠습니다.

### <a name="objectives"></a>목표

* 실제 세계를 가상 세계로 가져옵니다.
* 홀로그램을 가장 중요한 위치에 배치합니다.

### <a name="instructions"></a>지침

* Unity의 Project 패널에서 **홀로그램스** 폴더를 클릭합니다.
* 공간 **매핑** 자산을 계층의 루트로 끌어 **끕다.**
* 계층에서 **공간 매핑** 개체를 클릭합니다.
* **검사기 패널에서** 다음 속성을 변경합니다.
  * 시각적 **메시 그리기** 상자를 선택합니다.
  * **그리기 재질을** 찾고 오른쪽의 원을 클릭합니다. 맨 위에 있는 검색 필드에 **"wireframe**"을 입력합니다. 결과를 클릭한 다음 창을 닫습니다. 이렇게 하면 그리기 재질의 값이 Wireframe으로 설정됩니다.
* HoloLens 앱을 내보내고, 빌드하고, 배포합니다.
* 앱이 실행되면 와이어프레임 메시가 실제 세계를 오버레이합니다.
* 롤링 구가 스테이지에서 어떻게 바닥으로 떨어지는지 보세요.

이제 OrigamiCollection을 새 위치로 이동하는 방법을 보여 드리겠습니다.

* **Scripts** 폴더에서 **TapToPlaceParent라는** 스크립트를 만듭니다.
* **계층에서** **OrigamiCollection을** 확장하고 **Stage** 개체를 선택합니다.
* **TapToPlaceParent** 스크립트를 Stage 개체로 끌어 놓습니다.
* Visual Studio **TapToPlaceParent** 스크립트를 열고 다음과 같이 업데이트합니다.

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

* 앱을 내보내고, 빌드하고, 배포합니다.
* 이제 게임을 특정 위치에 배치하고, 선택 제스처를 사용한 다음, 새 위치로 이동한 다음, 선택 제스처를 다시 사용하여 특정 위치에 게임을 배치할 수 있습니다.

## <a name="chapter-7---holographic-fun"></a>7장 - 홀로그램의 재미

### <a name="objectives"></a>목표

* 홀로그램 언더월드에 대한 진입을 공개합니다.

### <a name="instructions"></a>지침

이제 홀로그램 언더월드를 파악하는 방법을 살펴보겠습니다.

* **Project** 패널의 홀로그램스 폴더에서 다음을 수행합니다.
  * **Underworld를** Hierarchy로 끌어 **OrigamiCollection** 의 자식이 됩니다.
* **Scripts** 폴더에서 **HitTarget** 이라는 스크립트를 만듭니다.
* **계층에서** **OrigamiCollection** 을 확장합니다.
* **Stage** 개체를 확장하고 **대상** 개체(파란색 팬)를 선택합니다.
* **HitTarget 스크립트를** **Target** 개체로 끌어 놓습니다.
* Visual Studio **HitTarget** 스크립트를 열고 다음과 같이 업데이트합니다.

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* Unity에서 **대상** 개체를 선택합니다.
* 이제 **적중 대상** 구성 요소에 두 개의 공용 속성이 표시되며 장면에서 개체를 참조해야 합니다.
  * **Hierarchy** 패널에서 **Underworld를** **적중 대상** 구성 요소의 **Underworld** 속성으로 끕다.
  * **계층** 패널에서 **개체로 스테이지를** 끌어 **적중 대상** 구성 요소의 **숨기기** 속성입니다.
* 앱을 내보내고, 빌드하고, 배포합니다.
* Origami 컬렉션을 지면에 놓고 선택 제스처를 사용하여 구를 놓습니다.
* 구가 대상(파란색 팬)에 도달하면 폭증이 발생합니다. 컬렉션이 숨겨지고 언더월드에 대한 구멍이 나타납니다.

## <a name="the-end"></a>끝

이 자습서의 끝입니다.

다음에 대해 알아보았습니다.

* Unity에서 홀로그램 앱을 만드는 방법
* 응시, 제스처, 음성, 소리 및 공간 매핑을 사용하는 방법입니다.
* Visual Studio 사용하여 앱을 빌드하고 배포하는 방법입니다.

이제 고유한 홀로그램 환경을 만들 준비가 되었습니다.

## <a name="see-also"></a>추가 정보

* [MR 기본 101E: 에뮬레이터를 사용하는 완전한 프로젝트](holograms-101e.md)
* [응시](../../../design/gaze-and-commit.md)
* [헤드 게이즈 및 커밋](../../../design/gaze-and-commit.md)
* [음성 입력 ](../../../design/voice-input.md)
* [공간 음향](../../../design/spatial-sound.md)
* [공간 매핑](../../../design/spatial-mapping.md)