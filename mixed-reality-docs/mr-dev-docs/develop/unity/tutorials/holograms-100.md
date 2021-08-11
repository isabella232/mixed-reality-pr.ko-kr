---
title: HoloLens(1세대) 기본 사항 100 - Unity 시작
description: HoloLens 및 Windows Mixed Reality 디바이스에 대한 첫 번째 기본 혼합 현실 "hello world" 애플리케이션을 만드는 방법을 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 혼합 현실, Windows Mixed Reality, HoloLens, 몰입형, vr, mr, 시작, 홀로그램, academy, 자습서, Mixed Reality Academy, unity, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 518be5642304b6307f0b26f30f37315eba4164448493d928f6effb3027f7d611
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196512"
---
# <a name="hololens-1st-gen-basics-100-getting-started-with-unity"></a>HoloLens(1세대) 기본 사항 100: Unity 시작

>[!IMPORTANT]
>Mixed Reality Academy 자습서는 HoloLens(1세대), Unity 2017 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다. 이러한 **_자습서는_** HoloLens 2 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 않으며 최신 버전의 Unity와 호환되지 않을 수 있습니다.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2에 대한 [새로운 자습서 시리즈](mrlearning-base.md)가 게시되었습니다.

이 자습서에서는 Unity를 통해 빌드된 기본 혼합 현실 앱을 만드는 작업을 안내합니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 기본 100: Unity 시작</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>필수 조건

* 올바른 도구로 구성된 Windows 10 [PC가 설치되어 있습니다.](../../install-the-tools.md)

## <a name="chapter-1---create-a-new-project"></a>1장 - 새 Project 만들기

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Unity를 사용하여 앱을 빌드하려면 먼저 프로젝트를 만들어야 합니다. 이 프로젝트는 몇 개의 폴더로 구성되며, 가장 중요한 것은 Assets 폴더입니다. 이 폴더는 Maya, Max Editor 4D 또는 Photoshop과 같은 디지털 콘텐츠 생성 도구에서 가져오는 모든 자산, Visual Studio 또는 즐겨 사용하는 코드 편집기를 사용하여 만드는 모든 코드, 편집기에서 장면, 애니메이션 및 기타 Unity 자산 형식을 작성할 때 Unity에서 만드는 콘텐츠 파일의 수에 관계없이 보관합니다.

UWP 앱을 빌드하고 배포하기 위해 Unity는 프로젝트를 필요한 모든 자산 및 코드 파일을 포함하는 Visual Studio 솔루션으로 내보낼 수 있습니다.

1. Unity 시작
2. **새로 만들기** 를 선택합니다.
3. 프로젝트 이름 입력(예: "MixedRealityIntroduction")
4. 프로젝트를 저장할 위치 입력
5. **3D** 토글이 선택되어 있는지 확인합니다.
6. **프로젝트 만들기를** 선택합니다.

축하합니다. 이제 혼합 현실 사용자 지정을 시작할 수 있습니다.

## <a name="chapter-2---setup-the-camera"></a>2장 - 카메라 설정

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Unity 주 카메라는 머리 추적 및 스테레오 범위 렌더링을 처리합니다. 혼합 현실에서 사용하기 위해 주 카메라를 몇 가지 변경해야 합니다.

1. 파일 > 새 장면 선택

먼저 사용자의 시작 위치를 (**X**: 0, **Y**: 0, **Z**: 0)로 간주하는 경우 앱 레이아웃이 더 쉽습니다. 주 카메라는 사용자의 머리 이동을 추적하기 때문에 주 카메라의 시작 위치를 설정하여 사용자의 시작 위치를 설정할 수 있습니다.

1. 계층 패널에서 **주 카메라를** **선택합니다.**
2. **검사기** 패널에서 **변환** 구성 요소를 찾아 **위치를** (**X**: 0, Y : **1,** **Z**: -10)에서 (**X**: 0, **Y**: 0, **Z**: 0)로 변경합니다.

둘째, 기본 카메라 배경에는 약간의 생각이 필요합니다.

**HoloLens 애플리케이션의 경우** 실제 세계는 Skybox 질감이 아니라 카메라가 렌더링하는 모든 것 뒤에 표시되어야 합니다.

1. **계층 구조** 패널에서 **기본 카메라를** 선택한 상태에서 Inspector 패널에서 **Camera** 구성 요소를 찾고 플래그 **지우기** 드롭다운을 **Skybox에서** **단색으로** 변경합니다. 
2. **배경색** 선택기를 선택하고 **RGBA** 값을 (0, 0, 0, 0)으로 변경합니다.

**몰입형 헤드셋을 대상으로 하는 혼합 현실 애플리케이션의 경우** Unity에서 제공하는 기본 Skybox 질감을 사용할 수 있습니다.

1. 계층 구조 패널에서 **기본 카메라를** 선택한 상태에서 **검사기** 패널에서  **카메라** 구성 요소를 찾아 **플래그 지우기** 드롭다운을 **Skybox** 로 유지합니다.

셋째, Unity에서 가까운 클립 평면을 고려하고 사용자가 개체에 접근하거나 개체가 사용자에게 접근할 때 개체가 사용자 눈과 너무 가깝게 렌더링되지 않도록 합니다.

**HoloLens 애플리케이션의 경우** 가까운 클립 평면을 [HoloLens 권장](../camera-in-unity.md#using-clipping-planes) 0.85미터로 설정할 수 있습니다.

1. **[계층 구조]** 패널에서 **기본 카메라를** 선택한 상태에서 **[검사기]** 패널에서 **카메라** 구성 요소를 **찾고, 주변 클립 평면** 필드를 기본값 **0.3에서** 권장되는 HoloLens **0.85로** 변경합니다.

**몰입형 헤드셋을 대상으로 하는 혼합 현실 애플리케이션의 경우** Unity에서 제공하는 기본 설정을 사용할 수 있습니다.

1. [계층 구조] 패널에서 **기본 카메라를** 선택한 상태에서 **[검사기]** 패널에서 **카메라** 구성 요소를 찾아 **거의 클립 평면** 필드를 기본값인 **0.3으로** 유지합니다. 

마지막으로, 지금까지 진행 상황을 저장해 보겠습니다. 장면 변경 내용을 저장하려면 **파일 > 장면을 다른 이름으로 저장을** 선택하고 장면 이름을 **Main** 로 지정한 **다음, 저장을** 선택합니다.

## <a name="chapter-3---setup-the-project-settings"></a>3장 - Project 설정 설정

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

이 장에서는 개발을 위해 Windows Holographic SDK를 대상으로 지정하는 데 도움이 되는 몇 가지 Unity 프로젝트 설정을 설정합니다. 또한 애플리케이션에 대한 몇 가지 품질 설정을 지정합니다. 마지막으로, 빌드 대상이 유니버설 Windows 플랫폼으로 설정되어 있는지 확인합니다.

### <a name="unity-performance-and-quality-settings"></a>Unity 성능 및 품질 설정

**HoloLens 대한 Unity 품질 설정**

![HoloLens 대한 Unity 품질 설정](images/qualitysettings.png)

HoloLens 높은 프레임 전송률 유지 관리가 매우 중요하므로 가장 빠른 성능을 위해 품질 설정을 조정하려고 합니다. 자세한 성능 정보는 [Unity에 대한 성능 권장 사항을 참조하세요.](../performance-recommendations-for-unity.md)

1. **> Project 설정 > 품질 편집을 선택합니다.**
2. **유니버설 Windows 플랫폼** 로고 아래의 **드롭다운을** 선택하고 **매우 낮음** 을 선택합니다. 유니버설 Windows 플랫폼 열 및 **매우 낮음** 행의 상자가 녹색이면 설정이 올바르게 적용된 것입니다.

**폐색 디스플레이를 대상으로 하는 혼합 현실 애플리케이션의 경우** 품질 설정을 기본값으로 그대로 둘 수 있습니다.

### <a name="target-windows-10-sdk"></a>대상 Windows 10 SDK

**대상 Windows Holographic SDK**

![대상 Windows Holographic SDK](../images/xrsettings.png)

내보내려는 앱이 2D 보기 대신 [몰입형 보기를](../../../design/app-views.md) 만들어야 한다는 사실을 Unity에 알려야 합니다. Windows 10 SDK를 대상으로 하는 Unity에서 Virtual Reality 지원을 사용하도록 설정하여 이 작업을 수행합니다.

1. 편집 **> Project 설정 > 플레이어** 로 이동합니다.
2. 플레이어 설정 대한 **검사기 패널에서** **유니버설 Windows 플랫폼** 아이콘을 선택합니다.
3. **XR 설정** 그룹을 확장합니다.
4. **렌더링** 섹션에서 **가상 현실 지원** 확인란을 선택하여 새 **가상 현실 SDK** 목록을 추가합니다.
5. 목록에 **Windows Mixed Reality** 가 나타나는지 확인합니다. 그렇지 않은 경우 목록 아래쪽에서 **+** 단추를 선택하고 **Windows Mixed Reality** 를 선택합니다.

>[!NOTE]
>**유니버설 Windows 플랫폼** 아이콘이 표시되지 않으면 설치하는 동안 유니버설 Windows 플랫폼 빌드 지원을 선택했는지 다시 확인합니다. 이 항목을 선택하지 않은 경우 올바른 Windows 설치를 사용하여 Unity를 다시 설치해야 할 수 있습니다.

모든 프로젝트 설정을 적용하는 데 대한 놀라운 작업입니다. 다음으로, 홀로그램을 추가해 보겠습니다.

## <a name="chapter-4---create-a-cube"></a>4장 - 큐브 만들기

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Unity 프로젝트에서 큐브를 만드는 것은 Unity에서 다른 개체를 만드는 것과 같습니다. Unity의 좌표계는 실제 세계에 매핑되므로 사용자 앞에 큐브를 배치하는 것이 쉽습니다. 여기서 Unity의 한 미터는 실제 세계에서 약 1미터입니다.

1. **계층 구조** 패널의 왼쪽 위 모서리에서 **만들기** 드롭다운을 선택하고 큐브 > **3D 개체를** 선택합니다.
2. **계층 패널에서** 새로 만든 **큐브를** 선택합니다.
3. **검사기에서** **변환** 구성 요소를 찾고 **위치를** (**X**: 0, Y : **0,** **Z**: 2)로 변경합니다. *이렇게 하면 큐브가 사용자의 시작 위치 앞에 2미터 배치됩니다.*
4. **변환** 구성 요소에서 **회전을** (**X**: 45, Y : **45,** **Z**: 45)로 변경하고 크기 **조정을** (**X**: 0.25, Y : 0.25, **Z**: 0.25)로 변경합니다.  *이렇게 하면 큐브의 크기가 0.25미터로 조정됩니다.*
5. 장면 변경 내용을 저장하려면 **파일 > 장면 저장을** 선택합니다.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>5장 - Unity 편집기에서 디바이스 확인

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

이제 큐브를 만들었으므로 디바이스를 빠르게 체크 인할 차례입니다. Unity 편집기 내에서 직접 이 작업을 수행할 수 있습니다.

### <a name="initial-setup"></a>초기 설정

1. 개발 PC의 Unity에서 **파일 > 빌드 설정** 창을 엽니다.
2. **플랫폼을** **유니버설 Windows 플랫폼으로** 변경하고 **플랫폼 전환을** 클릭합니다.

### <a name="for-hololens-use-unity-remoting"></a>HoloLens 경우 Unity Remoting을 사용합니다.

1. HoloLens Windows 스토어에서 사용할 수 있는 [홀로그램 Remoting Player](../../platform-capabilities-and-apis/holographic-remoting-player.md)를 설치하고 실행합니다. 디바이스에서 애플리케이션을 시작하면 대기 상태가 되며 디바이스의 IP 주소가 표시됩니다. IP를 적어 둡다.
2. **홀로그램 에뮬레이션 > XR > 창을** 엽니다.
3. **에뮬레이션 모드를** **없음에서** **원격 모드로 변경합니다.**
4. **원격 컴퓨터에서** 앞에서 기록한 HoloLens IP 주소를 입력합니다.
5. **연결** 을 클릭합니다.
6. 연결 **상태가** 녹색 **연결됨** 으로 변경되었는지 확인합니다.
7. 이제 Unity 편집기에서 **재생을** 클릭할 수 있습니다.

이제 디바이스 및 편집기에서 큐브를 볼 수 있습니다. 편집기에서 앱을 실행하는 것처럼 일시 중지, 검사 및 디버그할 수 있습니다. 이는 기본적으로 발생하지만 호스트 컴퓨터와 디바이스 간에 네트워크를 통해 앞뒤로 전송되는 비디오, 오디오 및 디바이스 입력을 사용하므로 디버그할 수 있습니다.

### <a name="for-other-mixed-reality-supported-headsets"></a>다른 혼합 현실 지원 헤드셋의 경우

1. USB 케이블과 HDMI 또는 디스플레이 포트 케이블을 사용하여 헤드셋을 개발 PC에 커넥트.
2. **Mixed Reality 포털** 시작하고 첫 번째 실행 환경을 완료해야 합니다.
3. 이제 Unity에서 재생 단추를 누를 수 있습니다.

이제 혼합 현실 헤드셋 및 편집기에서 큐브 렌더링을 볼 수 있습니다.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>6장 - Visual Studio 디바이스 빌드 및 배포

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

이제 프로젝트를 컴파일하여 대상 디바이스에 Visual Studio 배포할 준비가 되었습니다.

### <a name="export-to-the-visual-studio-solution"></a>Visual Studio 솔루션으로 내보내기

1. **파일 > 빌드 설정** 창을 엽니다.
1. **열린 장면 추가를** 클릭하여 장면을 추가합니다.
1. **플랫폼을** **유니버설 Windows 플랫폼으로** 변경하고 **플랫폼 전환을** 클릭합니다.
1. **유니버설 Windows 플랫폼** 설정에서 **SDK가** **유니버설 10인지** 확인합니다.
1. 대상 디바이스의 경우 모든 **디바이스에** 폐색 디스플레이를 그대로 두거나 **HoloLens** 로 전환합니다.
1. **UWP 빌드 형식은** **D3D** 여야 합니다.
1. **UWP SDK는** **최신 설치된** 에 남아 있을 수 있습니다.
1. **빌드** 를 클릭한 다음
1. 파일 탐색기에서 **새 폴더를** 클릭하고 폴더 이름을 **"App"으로** 지정합니다.
1. **앱** 폴더를 선택한 후 **폴더 선택** 단추를 클릭합니다.
1. Unity 빌드가 완료되면 Windows 파일 탐색기 창이 나타납니다.
1. 파일 탐색기에서 **App** 폴더를 엽니다.
1. 생성된 Visual Studio 솔루션 열기(이 예제에서는 MixedRealityIntroduction.sln)

### <a name="compile-the-visual-studio-solution"></a>Visual Studio 솔루션 컴파일

마지막으로 내보낸 Visual Studio 솔루션을 컴파일하고, 배포하고, 디바이스에서 사용해보겠습니다.

1. Visual Studio 위쪽 도구 모음을 사용하여 대상을 **디버그에서** **릴리스로,** **ARM에서** **X86으로** 변경합니다.

에뮬레이터와 디바이스에 배포하는 방법에 대한 지침은 다릅니다. 설정과 일치하는 지침을 따릅니다.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Wi-Fi 통해 혼합 현실 디바이스에 배포

1. **로컬 컴퓨터** 단추 옆의 화살표를 클릭하고 배포 대상을 원격 컴퓨터 로 **변경합니다.**
2. 혼합 현실 디바이스의 IP 주소를 입력하고 **인증 모드를** 다른 디바이스의 HoloLens **및** Windows 유니버설(암호화되지 않은 프로토콜)로 변경합니다.
3. **디버그 > 디버깅하지 않고 시작을** 클릭합니다.

**HoloLens** 경우 처음으로 디바이스에 배포하는 경우 [Visual Studio 를 사용하여](../../platform-capabilities-and-apis/using-visual-studio.md)페어링해야 합니다.

### <a name="deploy-to-mixed-reality-device-over-usb"></a>USB를 통해 혼합 현실 디바이스에 배포

USB 케이블을 통해 디바이스가 연결되어 있는지 확인합니다.

1. **HoloLens 경우** **로컬 머신** 단추 옆의 화살표를 클릭하고 배포 대상을 디바이스 로 **변경합니다.**
2. **PC에 연결된 폐색 디바이스를 대상으로 지정하려면** 설정을 로컬 컴퓨터로 유지합니다. **Mixed Reality 포털** 실행 중인지 확인합니다.
3. **디버그 > 디버깅하지 않고 시작을** 클릭합니다.

### <a name="deploy-to-emulator"></a>Emulator 배포

1. **디바이스** 단추 옆의 화살표를 클릭하고 드롭다운에서 **HoloLens Emulator** 선택합니다.
2. **디버그 > 디버깅하지 않고 시작을** 클릭합니다.

### <a name="try-out-your-app"></a>앱 사용해 보세요.

이제 앱이 배포된 후 큐브 주변을 모두 이동하고 사용자 앞에 있는 세계에 있는지 관찰합니다.

## <a name="see-also"></a>추가 정보

* [Unity 개발 개요](../unity-development-overview.md)
* [Unity 및 Visual Studio 사용 모범 사례](../best-practices-for-working-with-unity-and-visual-studio.md)
* [MR 기본 101](holograms-101.md)
* [MR 기본 101E](holograms-101e.md)