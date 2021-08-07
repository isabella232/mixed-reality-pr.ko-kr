---
title: HoloLens(1세대) 공유 240 - 여러 HoloLens 디바이스
description: holograms를 공유 하는 방법에 대 한 자세한 내용은 Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 따르세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 공유, 네트워킹, 아카데미, 자습서, HoloLens, 혼합 현실 아카데미, unity, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, Windows 10
ms.openlocfilehash: 1714c9cf1b64953ff319eefb8633b1891568d5a50f2ed778e6e890d3149d3908
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208703"
---
# <a name="hololens-1st-gen-sharing-240-multiple-hololens-devices"></a>HoloLens (1 세대) 공유 240: 여러 HoloLens 장치

>[!IMPORTANT]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen), Unity 2017 및 혼합 현실 모던 헤드셋을 고려 하 여 설계 되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다. 이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않으며 최신 버전의 Unity와 호환 되지 않을 수 있습니다.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2에 대한 [새로운 자습서 시리즈](mrlearning-base.md)가 게시되었습니다.

홀로그램스은 공간에서 이동 하는 동안 전 세계에 남아 있습니다. HoloLens은 다양 한 [좌표계](../../../design/coordinate-systems.md) 를 사용 하 여 개체의 위치와 방향을 추적 하는 방식으로 holograms을 유지 합니다. 이러한 좌표계를 장치 간에 공유할 때 공유 holographic 세계에 참여 하는 데 사용할 수 있는 공유 환경을 만들 수 있습니다.

이 자습서에서는 다음 작업을 수행합니다.

* 공유 환경의 네트워크를 설정 합니다.
* HoloLens 장치에서 holograms을 공유 합니다.
* 공유 holographic 세계에서 다른 사람을 검색 하세요.
* 다른 플레이어를 대상으로 하 고 projectiles를 시작할 수 있는 공유 대화형 환경을 만듭니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 공유 240: 여러 HoloLens 디바이스</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전에

### <a name="prerequisites"></a>필수 구성 요소

* 인터넷 액세스로 설치 된 올바른 [도구로](../../../develop/install-the-tools.md) 구성 된 Windows 10 PC입니다.
* [개발용으로 구성 된](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)두 개 이상의 HoloLens 장치

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) 을 다운로드 합니다. Unity 2017.2 이상이 필요 합니다.
  * Unity 5.6 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)를 사용 하세요.
  * Unity 5.5 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)를 사용 하세요.
  * Unity 5.4 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)를 사용 하세요.
* 바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다. 폴더 이름을 **SharedHolograms** 로 유지 합니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)있습니다.

## <a name="chapter-1---holo-world"></a>1 장-Holo 세계

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

이 장에서는 첫 번째 Unity 프로젝트를 설정 하 고 빌드 및 배포 프로세스를 단계별로 진행 합니다.

### <a name="objectives"></a>목표

* Holographic apps를 개발 하는 Unity를 설정 합니다.
* 홀로그램을 확인 하세요.

### <a name="instructions"></a>지침

* Unity를 시작합니다.
* **열기** 를 선택합니다.
* 이전에 unarchived **SharedHolograms** 폴더로 위치를 입력 합니다.
* **Project 이름** 을 선택 하 고 **폴더 선택** 을 클릭 합니다.
* **계층** 에서 **주 카메라** 를 마우스 오른쪽 단추로 클릭 하 고 **삭제** 를 선택 합니다.
* HoloToolkit- **240/Prefabs/카메라** 폴더에서 **기본 카메라** prefab를 찾습니다.
* **주 카메라** 를 **계층** 으로 끌어 놓습니다.
* **계층** 에서 **만들기** 를 클릭 하 고 **빈 상태로 만들기** 를 클릭 합니다.
* 새 **GameObject** 를 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기** 를 선택 합니다.
* GameObject의 이름을 **HologramCollection** 로 바꿉니다.
* **계층** 에서 **HologramCollection** 개체를 선택 합니다.
* **Inspector** 에서 **변환 위치** 를 **X: 0, Y:-0.25, Z: 2** 로 설정 합니다.
* **Project 패널** 의 **홀로그램스** 폴더에서 **EnergyHub** 자산을 찾습니다.
* **EnergyHub** 개체를 **Project 패널** 에서 **계층** 으로 **HologramCollection의 자식** 으로 끌어 놓습니다.
* **파일 > 다른 이름으로 장면 저장** ...을 선택 합니다.
* 장면 이름을 **SharedHolograms** 로 하 고 **저장** 을 클릭 합니다.
* Holograms를 미리 보려면 Unity의 **재생** 단추를 누릅니다.
* **재생** 을 두 번 눌러 미리 보기 모드를 중지 합니다.

**Unity에서 Visual Studio로 프로젝트를 내보냅니다.**

* Unity에서 **파일 > 빌드 설정** 를 선택 합니다.
* 열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.
* **플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 클릭 합니다.
* **SDK** 를 **Universal 10** 으로 설정 합니다.
* **대상 장치** 를 **HoloLens** 및 **UWP 빌드 형식** 으로 **D3D** 로 설정 합니다.
* **Unity c # 프로젝트** 를 확인 합니다.
* **빌드** 를 클릭한 다음
* 표시 되는 파일 탐색기 창에서 "App" 이라는 **새 폴더** 를 만듭니다.
* 단일 **앱** 폴더를 클릭 합니다.
* **폴더 선택** 을 누릅니다.
* Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.
* **앱** 폴더를 엽니다.
* **SharedHolograms** 를 열어 Visual Studio를 시작 합니다.
* Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86** 으로 변경 합니다.
* 로컬 컴퓨터 옆의 드롭다운 화살표를 클릭 하 고 **원격 장치** 를 선택 합니다.
    * **주소** 를 HoloLens의 이름 또는 IP 주소로 설정 합니다. 장치 IP 주소를 모르는 경우 **설정 > 네트워크 & 인터넷 > 고급 옵션** 을 확인 하거나 Cortana **"안녕하세요 Cortana, 내 IP 주소는 무엇입니까?"** 를 확인 합니다.
    * **인증 모드** 를 **유니버설** 으로 설정 된 상태로 둡니다.
    * **선택** 클릭
* **디버그 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5** 를 누릅니다. 처음으로 장치에 배포 하는 경우 [Visual Studio와 쌍](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)으로 연결 해야 합니다.
* HoloLens에 추가 하 고 EnergyHub 홀로그램을 찾습니다.

## <a name="chapter-2---interaction"></a>2 장-상호 작용

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

이 장에서는 holograms와 상호 작용 합니다. 먼저, [응시](../../../design/gaze-and-commit.md)를 시각화 하는 커서를 추가 합니다. 그런 다음 [제스처](../../../design/gaze-and-commit.md#composite-gestures) 를 추가 하 고 손을 사용 하 여 holograms을 공간에 넣습니다.

### <a name="objectives"></a>목표

* 응시 입력을 사용 하 여 커서를 제어 합니다.
* 제스처 입력을 사용 하 여 holograms와 상호 작용 합니다.

### <a name="instructions"></a>지침

**응시**

* **계층 패널** 에서 **HologramCollection** 개체를 선택 합니다.
* **검사기 패널** 에서 **구성 요소 추가** 단추를 클릭 합니다.
* 메뉴의 검색 상자에 **응시 관리자** 를 입력 합니다. 검색 결과를 선택 합니다.
* **HoloToolkit-Sharing-240\Prefabs\Input** 폴더에서 **커서** 자산을 찾습니다.
* **커서** 자산을 **계층 구조** 에 끌어다 놓습니다.

**제스처**

* **계층 패널** 에서 **HologramCollection** 개체를 선택 합니다.
* **구성 요소 추가를** 클릭하고 검색 필드에 **제스처 관리자를** 입력합니다. 검색 결과를 선택합니다.
* 계층 **구조 패널에서** **HologramCollection 을** 확장합니다.
* 자식 **EnergyHub** 개체를 선택합니다.
* **검사기 패널에서** **구성 요소 추가** 단추를 클릭합니다.
* 메뉴에서 홀로그램 배치 검색 상자에 를 **입력합니다.** 검색 결과를 선택합니다.
* 파일 > 장면 **저장을 선택하여 장면을 저장합니다.**

**배포 및 이용**

* 이전 장의 지침을 사용하여 HoloLens 빌드하고 배포합니다.
* 앱이 HoloLens 시작되면 헤드를 이동하고 EnergyHub가 응시를 따르는 방법을 알아보세요.
* 홀로그램을 응시할 때 커서가 어떻게 표시되고, 홀로그램에서 움추지 않을 때 점등으로 변경됩니다.
* 에어 탭을 수행하여 홀로그램을 배치합니다. 현재 프로젝트에서 홀로그램을 한 번만 배치할 수 있습니다(다시 배포하여 다시 시도).

## <a name="chapter-3---shared-coordinates"></a>3장 - 공유 좌표

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

홀로그램을 보고 상호 작용하는 것은 재미있지만, 더 자세히 살펴보겠습니다. 첫 번째 공유 환경인 홀로그램 모두가 함께 볼 수 있도록 설정합니다.

### <a name="objectives"></a>목표

* 공유 환경을 위한 네트워크를 설치합니다.
* 공통 참조 지점을 설정합니다.
* 디바이스 간에 좌표계를 공유합니다.
* 모든 사람이 동일한 홀로그램을 볼 수 있습니다.

>[!NOTE]
>앱이 공유 서버에 연결하려면 **InternetClientServer** 및 **PrivateNetworkClientServer** 기능을 선언해야 합니다. 이 작업은 이미 홀로그램스 240에서 수행되지만 사용자 고유의 프로젝트에 대해 이 점을 염두에 두어야 합니다.

>1. Unity 편집기에서 "> Project 설정 > 플레이어 편집"으로 이동하여 플레이어 설정으로 이동합니다.
>2. "Windows Store" 탭을 클릭합니다.
>3. "게시 설정 > 기능" 섹션에서 **InternetClientServer** 기능 및 **PrivateNetworkClientServer** 기능을 확인합니다.

### <a name="instructions"></a>지침

* Project **패널에서** **HoloToolkit-Sharing-240\Prefabs\Sharing** 폴더로 이동합니다.
* **공유** 프리팹을 **계층 패널** 로 끌어서 놓습니다.

다음으로 공유 서비스를 시작해야 합니다. 공유 환경의 **PC 하나만** 이 단계를 수행해야 합니다.

* Unity의 위쪽 메뉴에서 **HoloToolkit-Sharing-240 메뉴를** 선택합니다.
* 드롭다운에서 **공유 서비스 시작** 항목을 선택합니다.
* 프라이빗 **네트워크** 옵션을 선택하고 방화벽 프롬프트가 표시되면 **액세스 허용을** 클릭합니다.
* 공유 서비스 콘솔 창에 표시된 IPv4 주소를 적어 둡다. 서비스가 실행되는 컴퓨터와 동일한 IP입니다.

공유 환경을 조인할 **모든 PC의** 나머지 지침을 따릅니다.

* **계층** 구조에서 **공유** 개체를 선택합니다.
* **검사기의** **공유 단계** 구성 요소에서 **서버 주소를** 'localhost'에서 SharingService.exe 실행하는 컴퓨터의 IPv4 주소로 변경합니다.
* **계층** 구조에서 **HologramCollection** 개체를 선택합니다.
* **검사기에서** **구성 요소 추가** 단추를 클릭합니다.
* 검색 상자에 Import **Export Anchor Manager** 를 입력합니다. 검색 결과를 선택합니다.
* Project **패널에서** **스크립트** 폴더로 이동합니다.
* **HologramPlacement** 스크립트를 두 번 클릭하여 Visual Studio 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Unity로 **돌아가서 계층 패널에서** **HologramCollection을** 선택합니다.
* **검사기 패널에서** **구성 요소 추가** 단추를 클릭합니다.
* 메뉴에서 App State Manager 검색 상자에 를 **입력합니다.** 검색 결과를 선택합니다.

**배포 및 이용**

* HoloLens 디바이스에 대한 프로젝트를 빌드합니다.
* 먼저 배포할 하나의 HoloLens 지정합니다. EnergyHub를 배치하려면 앵커가 서비스에 업로드될 때까지 기다려야 합니다(최대 30~60초가 걸릴 수 있습니다). 업로드가 완료될 때까지 탭 제스처는 무시됩니다.
* EnergyHub가 배치되면 해당 위치가 서비스에 업로드된 다음 다른 모든 HoloLens 디바이스에 배포할 수 있습니다.
* 새 HoloLens 처음 세션에 조인하면 해당 디바이스에서 EnergyHub의 위치가 올바르지 않을 수 있습니다. 그러나 앵커 및 EnergyHub 위치가 서비스에서 다운로드되는 즉시 EnergyHub는 새로운 공유 위치로 이동해야 합니다. 30-60초 이내에 발생하지 않는 경우 앵커를 설정하여 더 많은 환경 단서를 수집할 때 원래 HoloLens 있었던 위치로 안내합니다. 위치가 여전히 잠기지 않으면 디바이스에 다시 배포합니다.
* 디바이스가 모두 준비되고 앱을 실행하면 EnergyHub를 찾습니다. 홀로그램의 위치와 텍스트의 방향에 모두 동의할 수 있나요?

## <a name="chapter-4---discovery"></a>4장 - 검색

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

이제 모든 사람이 동일한 홀로그램을 볼 수 있습니다. 이제 공유 홀로그램 세계에 연결된 다른 모든 사람을 살펴보겠습니다. 이 장에서는 동일한 공유 세션에서 다른 모든 HoloLens 디바이스의 헤드 위치 및 회전을 살펴보겠습니다.

### <a name="objectives"></a>목표

* 공유 경험에서 서로를 검색합니다.
* 플레이어 아바타를 선택하고 공유합니다.
* 플레이어 아바타를 모든 사람의 머리 옆에 연결합니다.

### <a name="instructions"></a>지침

* Project **패널에서** **홀로그램스** 폴더로 이동합니다.
* **PlayerAvatarStore를** 계층 구조 로 끌어서 **놓습니다.**
* Project **패널에서** **스크립트** 폴더로 이동합니다.
* **AvatarSelector** 스크립트를 두 번 클릭하여 Visual Studio 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* **계층** 구조에서 **HologramCollection** 개체를 선택합니다.
* **검사기에서** **구성 요소 추가를** 클릭합니다.
* 검색 상자에 Local **Player Manager** 를 입력합니다. 검색 결과를 선택합니다.
* **계층** 구조에서 **HologramCollection** 개체를 선택합니다.
* **검사기에서** **구성 요소 추가를** 클릭합니다.
* 검색 상자에 Remote **Player Manager** 를 입력합니다. 검색 결과를 선택합니다.
* Visual Studio **HologramPlacement** 스크립트를 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Visual Studio **AppStateManager** 스크립트를 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**배포 및 즐겨**

* 프로젝트를 빌드하고 HoloLens 디바이스에 배포합니다.
* ping 소리를 들으면 아바타 선택 메뉴를 찾아서 에어 탭 제스처가 있는 아바타를 선택합니다.
* 홀로그램을 보지 않는 경우 HoloLens 서비스와 통신할 때 커서 주위의 점 광원은 초기화(진한 자주색), 앵커 다운로드(녹색), 위치 데이터 가져오기/내보내기(노란색), 앵커 업로드(파란색) 등 다른 색으로 바뀝니다. 커서 주위의 점등이 기본 색(연한 자주색)이면 세션에서 다른 플레이어와 상호 작용할 준비가 된 것입니다.
* 공간에 연결된 다른 사람을 살펴봅니다. 홀로그램 로봇이 머리 위로 떠 있고 머리 동작을 모방합니다.

## <a name="chapter-5---placement"></a>5장 - 배치

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

이 장에서는 앵커를 실제 화면에 배치할 수 있도록 합니다. 공유 좌표를 사용하여 공유 경험에 연결된 모든 사람 사이의 중간 지점에 앵커를 배치합니다.

### <a name="objectives"></a>목표

* 플레이어의 머리 위치에 따라 공간 매핑 메시에 홀로그램을 배치합니다.

### <a name="instructions"></a>지침

* **Project 패널** 에서 **홀로그램스** 폴더로 이동 합니다.
* **CustomSpatialMapping** Prefab를 **계층 구조** 에 끌어다 놓습니다.
* **Project 패널** 에서 **Scripts** 폴더로 이동 합니다.
* **AppStateManager** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* **Project 패널** 에서 **Scripts** 폴더로 이동 합니다.
* **HologramPlacement** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.
* 내용을 아래 코드로 바꿉니다.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**배포 및 이용**

* 프로젝트를 빌드하고 HoloLens 장치에 배포 합니다.
* 앱이 준비 되 면 원 안에 표시 되 고 EnergyHub이 모든 사람의 중앙에 표시 되는 방식을 확인 합니다.
* 을 탭 하 여 EnergyHub을 놓습니다.
* 음성 명령 ' 다시 설정 대상 '을 사용 하 여 EnergyHub 백업을 선택 하 고 그룹으로 함께 작업 하 여 홀로그램을 새 위치로 이동 합니다.

## <a name="chapter-6---real-world-physics"></a>6 장-Real-World 물리학

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

이 장에서는 실제 화면을 바운스 하는 holograms을 추가 합니다. 사용자와 친구 모두에 의해 시작 되는 프로젝트를 사용 하 여 공간을 채웁니다.

### <a name="objectives"></a>목표

* 실제 표면에서 바운스 된 projectiles를 시작 합니다.
* 다른 플레이어가 볼 수 있도록 projectiles을 공유 합니다.

### <a name="instructions"></a>지침

* **계층** 에서 **HologramCollection** 개체를 선택 합니다.
* **검사기** 에서 **구성 요소 추가** 를 클릭 합니다.
* 검색 상자에 **멀리로 시작 관리자** 를 입력 합니다. 검색 결과를 선택 합니다.

**배포 및 이용**

* HoloLens 장치를 빌드하고 배포 합니다.
* 앱이 모든 장치에서 실행 되는 경우에는 공기 탭을 수행 하 여 실제 화면에서 멀리 있는 게임을 시작 합니다.
* 멀리가 다른 플레이어의 아바타와 충돌 하는 경우 어떻게 되나요?를 참조 하세요.

## <a name="chapter-7---grand-finale"></a>7 장-그랜드 Finale

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

이 장에서는 공동 작업 에서만 검색할 수 있는 포털을 살펴봅니다.

### <a name="objectives"></a>목표

* 함께 작동 하 여 비밀 포털을 projectiles 앵커에서 충분 한를 시작 합니다.

### <a name="instructions"></a>지침

* **Project 패널** 에서 **홀로그램스** 폴더로 이동 합니다.
* 지 **각 자산을** **HologramCollection의 자식** 으로 끌어 놓습니다.
* **HologramCollection** 가 선택 된 상태에서 **검사기** 의 **구성 요소 추가** 단추를 클릭 합니다.
* 메뉴의 검색 상자에 **ExplodeTarget** 을 입력 합니다. 검색 결과를 선택 합니다.
* **HologramCollection** 를 선택 하면 **계층 구조** 에서 **EnergyHub** 개체를 **검사기** 의 **대상** 필드로 끕니다.
* **HologramCollection** 를 선택 하면 **계층 구조** 에서 지 수 **개체를** **검사기** 의 **지 수 필드로** 끕니다.

**배포 및 이용**

* HoloLens 장치를 빌드하고 배포 합니다.
* 앱이 시작 되 면 함께 공동 작업 하 여 EnergyHub에서 projectiles를 시작 합니다.
* 지가 표시 되 면 projectiles를 실행 합니다 (추가 재미를 위해 로봇이 세 번 적중).