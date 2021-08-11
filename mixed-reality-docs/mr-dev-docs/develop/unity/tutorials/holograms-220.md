---
title: HoloLens(1세대) 공간 220 - 공간 사운드
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 공간 소리 개념에 대 한 자세한 내용을 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 아카데미, 자습서, 공간 사운드, HoloLens, 혼합 현실 아카데미, unity, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, Windows 10
ms.openlocfilehash: d53b449916405d8bf42bb8dd63cc1d3cb5d6127bbf9b2989ce7cb09c3762a6e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200414"
---
# <a name="hololens-1st-gen-spatial-220-spatial-sound"></a>HoloLens (첫 번째 gen) 공간 220: 공간 사운드

>[!IMPORTANT]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen), Unity 2017 및 혼합 현실 모던 헤드셋을 고려 하 여 설계 되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다. 이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않으며 최신 버전의 Unity와 호환 되지 않을 수 있습니다.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2에 대한 [새로운 자습서 시리즈](mrlearning-base.md)가 게시되었습니다.

[공간 사운드](../../../design/spatial-sound.md) 를 holograms로 breathes 세계에 제공 합니다. 홀로그램스은 가볍고 소리로 구성 되며 Holograms의 시야가 손실 되는 경우 공간 소리를 통해 찾을 수 있습니다. 공간 사운드는 라디오 공간에 배치 되는 일반적인 사운드와는 달리, 라디오 공간에 있습니다. 공간 사운드를 사용 하면 사용자, 사용자 옆 또는 머리에 있는 것 처럼 holograms 소리를 만들 수 있습니다. 이 과정에서는 다음을 수행 합니다.

* Microsoft 공간 소리를 사용 하도록 개발 환경을 구성 합니다.
* 공간 소리를 사용 하 여 상호 작용을 향상 시킵니다.
* 공간을 [공간 매핑과](../../../design/spatial-mapping.md)함께 사용 합니다.
* 사운드 디자인을 이해 하 고 모범 사례를 혼합 합니다.
* 소리를 사용 하 여 특수 효과를 향상 시키고 사용자를 혼합 현실 세계에 가져옵니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 공간 220: 공간 음향</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전에

### <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구로](../../../develop/install-the-tools.md)구성 된 Windows 10 PC.
* 몇 가지 기본적인 c # 프로그래밍 기능.
* [MR 기본 101](../../../develop/unity/tutorials/holograms-101.md)를 완료 해야 합니다.
* [개발용으로 구성](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 장치입니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) 을 다운로드 합니다. Unity 2017.2 이상이 필요 합니다.
  * Unity 5.6 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)를 사용 하세요. 이 릴리스는 더 이상 최신 버전이 아닙니다.
  * Unity 5.5 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)를 사용 하세요. 이 릴리스는 더 이상 최신 버전이 아닙니다.
  * Unity 5.4 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)를 사용 하세요. 이 릴리스는 더 이상 최신 버전이 아닙니다.
* 바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)있습니다.

### <a name="errata-and-notes"></a>정오표 및 참고 사항

* 코드에서 중단점을 적중 하려면 도구->옵션->디버깅 아래 Visual Studio에서 "내 코드만 사용"을 사용 하지 않도록 설정 (*선택 취소*) 해야 합니다.

## <a name="chapter-1---unity-setup"></a>1 장-Unity 설치

### <a name="objectives"></a>목표

* Microsoft 공간 소리를 사용 하도록 Unity의 소리 구성을 변경 합니다.
* Unity에서 개체에 3D 소리를 추가 합니다.

### <a name="instructions"></a>지침

* Unity를 시작합니다.
* **열기** 를 선택합니다.
* 바탕 화면으로 이동 하 여 이전에 보관 하지 않은 폴더를 찾습니다.
* **Starting\Decibel** 폴더를 클릭 한 다음 **폴더 선택** 단추를 누릅니다.
* Unity에서 프로젝트가 로드 될 때까지 기다립니다.
* **Project** 패널에서 **Scenes\Decibel.unity** 를 엽니다.
* **계층** 패널에서 **HologramCollection** 를 확장 하 고 **P0LY** 를 선택 합니다.
* 검사기에서 **오디오 소스** 를 확장 하 고 **Spatialize** 확인란이 있는지 확인 합니다.

기본적으로 Unity는 spatializer 플러그 인을 로드 하지 않습니다. 다음 단계에서는 프로젝트에서 공간 소리를 사용 하도록 설정 합니다.

* Unity의 최상위 메뉴에서 **편집 > Project 설정 > 오디오** 로 이동 합니다.
* **Spatializer 플러그 인** 드롭다운을 찾고 **MS hrtf Spatializer** 를 선택 합니다.
* **계층** 패널에서 **HologramCollection > P0LY** 를 선택 합니다.
* **검사기** 패널에서 **오디오 원본** 구성 요소를 찾습니다.
* **Spatialize** 확인란을 선택 합니다.
* **공간 Blend** 슬라이더를 **3d** 로 끌어 놓거나 편집 상자에 **1** 을 입력 합니다.

이제 Unity에서 프로젝트를 빌드하고 Visual Studio에서 솔루션을 구성 합니다.

1. Unity에서 **파일 > 빌드 설정** 를 선택 합니다.
2. 열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.
3. **플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 클릭 합니다.
4. HoloLens에 대해 구체적으로 개발 하는 경우 **대상 장치** 를 **HoloLens** 로 설정 합니다. 그렇지 않으면 **모든 장치** 에 그대로 둡니다.
5. **빌드 형식이** **D3D** 로 설정 되 고 **sdk** 가 **최신 버전** 으로 설정 되어 있는지 확인 합니다 (sdk 16299 이상 이어야 함).
6. **빌드** 를 클릭한 다음
7. "App" 이라는 **새 폴더** 를 만듭니다.
8. 단일 **앱** 폴더를 클릭 합니다.
9. **폴더 선택** 을 누릅니다.

Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.

1. **앱** 폴더를 엽니다.
2. **데시벨 Visual Studio 솔루션** 을 엽니다.

HoloLens에 배포 하는 경우:

1. Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86** 으로 변경 합니다.
2. 로컬 컴퓨터 단추 옆에 있는 드롭다운 화살표를 클릭 하 고 **원격 컴퓨터** 를 선택 합니다.
3. **HoloLens 장치 IP 주소** 를 입력 하 고 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** 로 설정 합니다. **선택** 을 클릭합니다. 장치 IP 주소를 모르는 경우 **설정 > 네트워크 & 인터넷 > 고급 옵션** 을 확인 하세요.
4. 상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5** 를 누릅니다. 처음으로 장치에 배포 하는 경우 [Visual Studio와 쌍](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)으로 연결 해야 합니다.

모던 헤드셋에 배포 하는 경우:

1. Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 x **64** 로 변경 합니다.
2. 배포 대상이 **로컬 컴퓨터** 로 설정 되었는지 확인 합니다.
3. 상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5** 를 누릅니다.

## <a name="chapter-2---spatial-sound-and-interaction"></a>2 장-공간 소리 및 상호 작용

### <a name="objectives"></a>목표

* 소리를 사용 하 여 홀로그램 현실감을 향상 시킵니다.
* 소리를 사용 하 여 사용자의 응시를 보냅니다.
* 소리를 사용 하 여 제스처 피드백을 제공 합니다.

### <a name="part-1---enhancing-realism"></a>1 부-현실감 향상

#### <a name="key-concepts"></a>주요 개념

* Spatialize 홀로그램 소리.
* 소리 원본은 홀로그램의 적절한 위치에 배치되어야 합니다.

소리에 대한 적절한 위치는 홀로그램에 따라 달라집니다. 예를 들어 홀로그램이 사람인 경우 소리 소스는 발이 아니라 입 근처에 있어야 합니다.

#### <a name="instructions"></a>지침

다음 지침은 공간화된 소리를 홀로그램에 연결합니다.

* 계층 **구조** 패널에서 **HologramCollection을** 확장하고 **P0LY를** 선택합니다.
* **Inspector** 패널의 **AudioSource** 에서 **AudioClip** 옆의 원을 클릭하고 팝업에서 **PolyHover를** 선택합니다.
* **출력** 옆에 있는 원을 클릭하고 팝업에서 **SoundEffects를** 선택합니다.

Project Decibel은 Unity **AudioMixer** 구성 요소를 사용하여 소리 그룹에 대한 소리 수준을 조정할 수 있도록 합니다. 이러한 방식으로 소리를 그룹화하면 각 소리의 상대 볼륨을 유지하면서 전체 볼륨을 조정할 수 있습니다.

* **AudioSource에서** **3D Sound 설정** 확장합니다.
* **Doppler 수준을** **0으로** 설정합니다.

Doppler 수준을 0으로 설정하면 동작(홀로그램 또는 사용자)으로 인한 피치 변경이 비활성화됩니다. Doppler의 대표적인 예는 빠르게 움직이는 자동차입니다. 자동차가 고정 수신기에 접근하면 엔진의 피치가 증가합니다. 수신기를 통과하면 거리와 함께 피치가 낮아질 수 있습니다.

### <a name="part-2---directing-the-users-gaze"></a>2부 - 사용자의 응시 지시

#### <a name="key-concepts"></a>주요 개념

* 소리를 사용하여 중요한 홀로그램에 주의를 집중합니다.
* 눈 모양이 되는 위치를 안내하는 데 도움이 됩니다.
* 브레인에는 몇 가지 학습된 기대치가 있습니다.

학습된 기대치의 한 가지 예는 일반적으로 조류가 사람의 머리 위에 있다는 것입니다. 사용자가 조류 소리를 들으면 초기 반응도 조회하는 것입니다. 새를 사용자 아래에 배치하면 소리의 올바른 방향을 향할 수 있지만 조회해야 한다는 기대에 따라 홀로그램을 찾을 수 없습니다.

#### <a name="instructions"></a>지침

다음 지침에 따라 P0LY가 숨겨지므로 소리를 사용하여 홀로그램을 찾을 수 있습니다.

* 계층 **구조** 패널에서 **관리자를** 선택합니다.
* **검사기** 패널에서 **음성 입력 처리기** 를 찾습니다.
* **음성 입력 처리기에서** **Go Hide를 확장합니다.**
* **함수 없음을** **PolyActions.GoHide 로 변경합니다.**

![키워드: Go 숨기기](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>3부 - 제스처 피드백

#### <a name="key-concepts"></a>주요 개념

* 소리를 사용하여 사용자에게 긍정 제스처 확인 제공
* 사용자에게 과부전하지 않습니다. 너무 큰 소리가 방해가 될 수 있습니다.
* 미묘한 소리가 가장 잘 작동합니다. 환경을 뒤덮지 않습니다.

#### <a name="instructions"></a>지침

* 계층 **구조** 패널에서 **HologramCollection 을** 확장합니다.
* **EnergyHub를** 확장하고 **기본** 을 선택합니다.
* **검사기** 패널에서 **구성 요소 추가를** 클릭하고 **제스처 소리 처리기** 를 추가합니다.
* **제스처 소리 처리기에서** 탐색 시작 클립 및 **탐색 업데이트된** **클립** 옆의 원을 클릭하고 팝업에서 **회전클릭을** 선택합니다.
* "GestureSoundHandler"를 두 번 클릭하여 Visual Studio 로드합니다.

제스처 소리 처리기는 다음 작업을 수행합니다.

* **AudioSource** 를 만들고 구성합니다.
* **AudioSource를** 적절한 **GameObject** 의 위치에 배치합니다.
* 제스처와 연결된 **AudioClip을** 재생합니다.

#### <a name="build-and-deploy"></a>빌드 및 배포

1. Unity에서 **파일 > 빌드 설정** 선택합니다.
2. **빌드** 를 클릭한 다음
3. **App** 폴더를 한 번 클릭합니다.
4. **폴더 선택을** 누릅니다.

도구 모음에 "릴리스", "x86" 또는 "x64" 및 "원격 디바이스"가 표시되어 있는지 확인합니다. 그렇지 않은 경우 Visual Studio 코딩 인스턴스입니다. App 폴더에서 솔루션을 다시 열어야 할 수 있습니다.

* 메시지가 표시되면 프로젝트 파일을 다시 로드합니다.
* 이전과 마찬가지로 Visual Studio 배포합니다.

애플리케이션이 배포된 후:

* P0LY를 이동할 때 소리가 어떻게 변하는지 관찰합니다.
* P0LY를 뒤에 있는 위치로 이동하려면 *"숨기기로 이동"을* 말하십시오. 소리로 찾습니다.
* 에너지 허브의 밑을 응시합니다. 홀로그램을 탭하고 왼쪽 또는 오른쪽으로 끌어 홀로그램을 회전하고 클릭하는 소리가 제스처를 확인하는 방법을 확인합니다.

참고: 태그를 함께 사용할 텍스트 패널이 있습니다. 여기에는 이 과정 전체에서 사용할 수 있는 사용 가능한 음성 명령이 포함됩니다.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>3장 - 공간 소리 및 공간 매핑

### <a name="objectives"></a>목표

* 소리를 사용하여 홀로그램과 실제 세계 간의 상호 작용을 확인합니다.
* 실제 세계를 사용하여 소리를 폐색합니다.

### <a name="part-1---physical-world-interaction"></a>1부 - 물리적 세계 상호 작용

#### <a name="key-concepts"></a>주요 개념

* 물리적 개체는 일반적으로 표면이나 다른 개체가 발생할 때 소리를 내립니다.
* 소리는 환경 내에서 적절한 컨텍스트여야 합니다.

예를 들어 테이블에 대한 잔을 설정하면 금속 조각에 쇠를 놓는 것보다 더 작은 소리를 내야 합니다.

#### <a name="instructions"></a>지침

* 계층 **구조** 패널에서 **HologramCollection 을** 확장합니다.
* **EnergyHub를** 확장하고 **기본** 을 선택합니다.
* **Inspector(검사기)** 패널에서 **Add Component(구성 요소 추가)를** 클릭하고 **Tap To Place With Sound and Action(소리 및 작업과 함께 배치할 탭)을 추가합니다.**
* **탭하여 소리 및 동작으로 배치:**
  * **탭에서 부모 배치를** 선택합니다.
  * **배치 소리를** **배치로** 설정합니다.
  * **픽업 소리를 픽업** 로 설정합니다. 
  * **픽업** 작업 및 배치 작업에서 오른쪽 아래의 **+를** 누릅니다. 장면의 EnergyHub를 **없음(개체)** 필드로 끌어다 주세요.
    * **픽업 작업에서** 함수   ->  **없음 EnergyHubBase**  ->  **ResetAnimation을** 클릭합니다.
    * **배치 작업에서** 함수 **없음**  ->  **EnergyHubBase**  ->  **OnSelect를** 클릭합니다.

![소리와 동작으로 배치하려면 탭합니다.](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>2부 - 소리 폐색

#### <a name="key-concepts"></a>주요 개념

* 광원과 같은 소리는 폐색될 수 있습니다.

클래식 예제는 콘서트 홀입니다. 수신기가 홀 바깥쪽에 서 있고 문이 닫힌 경우 음악 소리가 섞입니다. 또한 일반적으로 볼륨이 감소합니다. 문이 열리면 소리의 전체 스펙트럼이 실제 볼륨에서 들립니다. 빈도가 높은 소리는 일반적으로 낮은 빈도보다 많이 흡수됩니다.

#### <a name="instructions"></a>지침

* 계층 **구조** 패널에서 **HologramCollection을** 확장하고 **P0LY를** 선택합니다.
* **검사기** 패널에서 **구성 요소 추가를** 클릭하고 **Audio Emitter 를** 추가합니다.

Audio Emitter 클래스는 다음과 같은 기능을 제공합니다.

* **AudioSource의** 볼륨에 대한 변경 내용을 복원합니다.
* **AudioEmitter가** 연결된 **GameObject** 방향의 사용자 위치에서 **Physics.RaycastNonAlloc을** 수행합니다.

RaycastNonAlloc 메서드는 반환되는 결과 수뿐만 아니라 할당을 제한하는 성능 최적화로 사용됩니다.

* 가 발생한 각 **IAudioInfluencer에** 대해 **ApplyEffect** 메서드를 호출합니다.
* 더 이상 발생하지 않는 이전의 각 **IAudioInfluencer에** 대해 **RemoveEffect** 메서드를 호출합니다.

AudioEmitter는 프레임 단위가 아니라 사람 시간 배율에 따라 업데이트됩니다. 이 작업은 일반적으로 사람이 매 분기 또는 1/2초보다 더 자주 업데이트해야 하는 효과를 충분히 빠르게 이동하지 않기 때문에 수행됩니다. 한 위치에서 다른 위치로 신속하게 원격 전송하는 홀로그램스홀로그램스 이러한 현상이 끊어질 수 있습니다.

* 계층 **구조** 패널에서 **HologramCollection 을** 확장합니다.
* **EnergyHub를** 확장하고 **BlobOutside를** 선택합니다.
* **검사기** 패널에서 **구성 요소 추가를** 클릭하고 **오디오 폐색 을** 추가합니다.
* **오디오 폐색에서** 중단 **빈도를** **1500으로** 설정합니다.

이 설정은 AudioSource 빈도를 1500Hz 이하로 제한합니다.

* **볼륨 통과를** **0.9로** 설정합니다.

이 설정은 AudioSource의 볼륨을 현재 수준의 90%로 줄입니다.

오디오 폐색은 IAudioInfluencer를 구현하여 다음을 수행합니다.

* **AudioSource** 관리형 구매 **AudioEmitter에** 연결되는 **AudioLowPassFilter를** 사용하여 폐색 효과를 적용합니다.
* AudioSource에 볼륨 감쇠를 적용합니다.
* 중립 차단 빈도를 설정하고 필터를 사용하지 않도록 설정하여 효과를 사용하지 않도록 설정합니다.

중립으로 사용되는 빈도는 22kHz(22000Hz)입니다. 이 빈도는 사람의 귀에서 들 수 있는 명목 최대 빈도를 초과하여 선택되었으며, 이는 소리에 눈에 띄는 영향을 미치지 않습니다.

* 계층 **패널에서** **SpatialMapping을** 선택합니다.
* **검사기** 패널에서 **구성 요소 추가를** 클릭하고 **오디오 폐색 을** 추가합니다.
* **오디오 폐색에서** 중단 **빈도를** **750으로** 설정합니다.

사용자와 **AudioEmitter** 사이의 경로에 여러 폐색이 있는 경우 가장 낮은 빈도가 필터에 적용됩니다.

* **볼륨 통과를** **0.75로** 설정합니다.

사용자와 **AudioEmitter** 사이의 경로에 여러 폐색이 있는 경우 볼륨 통과가 추가적으로 적용됩니다.

* 계층 **구조** 패널에서 **관리자를** 선택합니다.
* **검사기** 패널에서 **음성 입력 처리기 를 확장합니다.**
* **음성 입력 처리기에서** Go Charge 를 **확장합니다.**
* **함수 없음을** **PolyActions.GoCharge 로** 변경합니다.

![키워드: Go 요금](images/gocharge.png)

* **여기로 오세요를 확장합니다.**
* **함수 없음을** **PolyActions.ComeBack으로 변경합니다.**

![키워드: 여기로 오세요.](images/comehere.png)

#### <a name="build-and-deploy"></a>빌드 및 배포

* 이전과 마찬가지로 Unity에서 프로젝트를 빌드하고 Visual Studio 배포합니다.

애플리케이션이 배포된 후:

* *"Go Charge"라고* 말하여 P0LY가 에너지 허브에 들어가도록 합니다.

소리의 변경에 유의합니다. 약간 더 간결한 소리가 나야 합니다. 본인과 에너지 허브 사이에 벽 또는 다른 개체를 배치할 수 있는 경우 실제 세계의 폐색으로 인해 소리의 추가적인 접미사를 확인할 수 있습니다.

* *"여기로 오세요"라고* 말하면 P0LY가 에너지 허브를 벗어나서 자신을 앞에 배치하도록 합니다.

P0LY가 에너지 허브를 종료하면 소리 폐색이 제거됩니다. 여전히 폐색을 들은 경우 P0LY가 실제 세계에 의해 폐색될 수 있습니다. P0LY를 명확하게 볼 수 있도록 이동해 보세요.

### <a name="part-3---room-models"></a>3부 - 실내 모델

#### <a name="key-concepts"></a>주요 개념

* 공간의 크기는 소리 지역화에 기여하는 하위 큐를 제공합니다.
* 실내 모델은 **AudioSource에** 따라 설정됩니다.
* [Unity용 MixedRealityToolkit는](https://github.com/Microsoft/MixedRealityToolkit-Unity) 실내 모델을 설정하기 위한 코드를 제공합니다.
* Mixed Reality 환경의 경우 실제 공간에 가장 적합한 실내 모델을 선택합니다.

가상 현실 시나리오를 만드는 경우 가상 환경에 가장 적합한 실내 모델을 선택합니다.

## <a name="chapter-4---sound-design"></a>4장 - 사운드 디자인

### <a name="objectives"></a>목표

* 효과적인 사운드 디자인에 대한 고려 사항을 이해합니다.
* 혼합 기술 및 지침을 알아봅니다.

### <a name="part-1---sound-and-experience-design"></a>1부 - 소리 및 환경 디자인

이 섹션에서는 주요 사운드 및 경험 디자인 고려 사항 및 지침에 대해 설명합니다.

#### <a name="normalize-all-sounds"></a>모든 소리 정규화

이렇게 하면 소리당 볼륨 수준을 조정하는 특수 사례 코드가 필요하지 않으며, 시간이 오래 걸릴 수 있으며 사운드 파일을 쉽게 업데이트하는 기능이 제한됩니다.

#### <a name="design-for-an-untethered-experience"></a>테더링되지 않은 환경을 위한 디자인

HoloLens 완전히 포함된 테더링되지 않은 홀로그램 컴퓨터입니다. 사용자는 이동하는 동안 환경을 사용할 수 있고 사용할 수 있습니다. 주변을 둘러보면 오디오 조합을 테스트해야 합니다.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>홀로그램의 논리적 위치에서 소리 내보낸다

실제 세계에서 강아지는 꼬리를 벗지 않으며 사람의 음성은 발에서 나온 것이 아닙니다. 홀로그램의 예기치 않은 부분에서 소리가 내보낸 것을 방지합니다.

작은 홀로그램의 경우 기하 도형의 중심에서 소리를 내보낸 것이 합리적입니다.

#### <a name="familiar-sounds-are-most-localizable"></a>친숙한 소리는 가장 지역화할 수 있습니다.

사람의 음성과 음악은 지역화하기가 매우 쉽습니다. 누군가가 사용자의 이름을 호출하는 경우 음성이 나온 방향과 멀리 떨어져 있는 방향을 매우 정확하게 확인할 수 있습니다. 짧고 생소한 소리는 지역화하기가 더 어렵습니다.

#### <a name="be-cognizant-of-user-expectations"></a>사용자 기대치 인식

생명 경험은 소리의 위치를 식별하는 기능에서 중요한 역할을 합니다. 이것이 사람의 음성이 특히 지역화하기 쉬운 이유 중 하나입니다. 소리를 배치할 때 사용자의 학습된 기대치를 알고 있어야 합니다.

예를 들어 누군가가 새 노래의 소리를 들으면 일반적으로 위를 조회합니다. 조류가 가시선 위에 있는 경향이 있기 때문에(비행 또는 트리에서) 사용자가 소리의 올바른 방향을 전환하는 것은 드문 일이 아니지만, 잘못된 세로 방향을 보고 홀로그램을 찾을 수 없을 때 혼동하거나 불만스러울 수 있습니다.

#### <a name="avoid-hidden-emitters"></a>숨겨진 내보내기 방지

실제 세계에서 소리를 들으면 일반적으로 소리를 내보내는 개체를 식별할 수 있습니다. 이는 사용자 경험에서도 마찬가지입니다. 사용자가 소리를 듣고, 소리가 시작되는 위치를 알고, 개체를 볼 수 없는 경우 매우 어려울 수 있습니다.

이 지침에는 몇 가지 예외가 있습니다. 예를 들어 필드의 앰비언트 소리와 같은 앰비언트 소리는 볼 수 없습니다. 생명 경험을 통해 이러한 소리의 출처를 확인할 필요 없이 숙지할 수 있습니다.

### <a name="part-2---sound-mixing"></a>2부 - 소리 혼합

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>HoloLens 70% 볼륨에 대한 조합 대상 지정

Mixed Reality 환경을 통해 홀로그램을 실제 세계에서 볼 수 있습니다. 또한 실제 소리를 들도록 허용해야 합니다. 70% 볼륨 대상을 사용하면 사용자가 환경의 소리와 함께 주변 세계를 들어보는 데 사용할 수 있습니다.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>100% 볼륨의 HoloLens 외부 소리를 제외해야 합니다.

100%의 볼륨 수준은 가상 현실 환경과 비슷합니다. 시각적으로 사용자는 다른 세계로 전송됩니다. 동일한 가성적으로 유지되어야 합니다.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Unity AudioMixer를 사용하여 소리 범주 조정

혼합을 디자인할 때 소리 범주를 만들고 볼륨을 한 단위로 늘리거나 줄이는 기능을 갖는 것이 도움이 되는 경우가 많습니다. 이렇게 하면 각 소리의 상대 수준이 유지되고 전체적인 혼합을 빠르고 쉽게 변경할 수 있습니다. 일반적인 범주는 다음과 같습니다. 사운드 효과, 앰비언스, 음성 오버 및 배경 음악.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>사용자의 응시에 따라 소리 혼합

사용자가 찾고 있는 위치(또는 그렇지 않은 경우)에 따라 환경의 소리 조합을 변경하는 것이 유용할 수 있습니다. 이 기술의 한 가지 일반적인 용도는 사용자가 앞에 있는 정보에 더 쉽게 집중할 수 있도록 홀로그램 프레임 외부에 있는 홀로그램의 볼륨 수준을 줄이는 것입니다. 또 다른 용도는 중요 한 이벤트에 사용자의 주의가 필요한 소리의 볼륨을 늘리는 것입니다.

#### <a name="building-your-mix"></a>조합 빌드

조합을 빌드할 때 경험의 배경 오디오로 시작 하 고 중요도에 따라 레이어를 추가 하는 것이 좋습니다. 일반적으로 각 계층이 이전 보다 크게 크게 발생 합니다.

가장 중요 하지 않은 (일반적으로 quietest 소리) 아래쪽에 있는 반전 된 깔때기로 혼합을 발견 다음 다이어그램과 유사한 조합을 구성 하는 것이 좋습니다.

![사운드 조합 구조](images/soundlevels.png)

음성 failover)가은 흥미로운 시나리오입니다. 만드는 환경에 따라 스테레오 (지역화 되지 않음) 사운드가 나 음성 failover)가을 spatialize 수 있습니다. Microsoft에서 게시 한 두 가지 환경에서는 각 시나리오의 뛰어난 예를 보여 줍니다.

[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) 는 스테레오 음성을 사용 합니다. 내레이터가 표시 되는 위치를 설명 하는 경우 소리는 일관적 이며 사용자의 위치에 따라 달라 지지 않습니다. 이렇게 하면 내레이터가 환경의 spatialized 소리를 벗어나지 않고 장면을 설명할 수 있습니다.

[조각은](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) 감지 형식의 spatialized 음성을 활용 합니다. 감지의 음성은 실제 사람이 대화방에 있는 것 처럼 중요 한 단서를 사용자에 게 전달 하는 데 사용 됩니다. 이를 통해 집중 교육을 더 잘 이해할 수 있습니다.

### <a name="part-3--performance"></a>3 부-성능

#### <a name="cpu-usage"></a>CPU 사용량

공간 사운드를 사용 하는 경우 10-12는 CPU의 약 12%를 사용 합니다.

#### <a name="stream-long-audio-files"></a>긴 오디오 파일 스트림

오디오 데이터는 특히 일반적인 샘플 요금 (44.1 및 48 kHz)에서 클 수 있습니다. 일반적인 규칙은 응용 프로그램 메모리 사용을 줄이기 위해 5-10 초 보다 긴 오디오 파일을 스트리밍하는 것입니다.

Unity에서는 파일의 가져오기 설정에서 스트리밍을 위해 오디오 파일을 표시할 수 있습니다.

![오디오 가져오기 설정](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>5 장-특수 효과

### <a name="objectives"></a>목표

* "매직 Windows"에 깊이를 추가 합니다.
* 사용자를 가상 세계에 가져옵니다.

### <a name="magic-windows"></a>매직 Windows

#### <a name="key-concepts"></a>주요 개념

* 숨겨진 세계에 뷰를 만들면 시각적으로 매력적인 것입니다.
* 홀로그램 또는 사용자가 숨겨진 세계 가까이 있을 때 오디오 효과를 추가 하 여 현실감을 향상 시킵니다.

#### <a name="instructions"></a>지침

* **계층** 패널에서 **HologramCollection** 를 확장 하 고 지 각 **를 선택 합니다**.
* 지 각 **를 확장 하** 고 **VoiceSource** 를 선택 합니다.
* **검사기** 패널에서 **구성 요소 추가** 를 클릭 하 고 **사용자 음성 효과** 를 추가 합니다.

**VoiceSource** 에 **오디오 원본** 구성 요소가 추가 됩니다.

* **오디오 원본** 에서 **출력** 을 **UserVoice (Mixer)** 로 설정 합니다.
* **Spatialize** 확인란을 선택 합니다.
* **공간 Blend** 슬라이더를 **3d** 로 끌어 놓거나 편집 상자에 **1** 을 입력 합니다.
* **3D 소리 설정** 를 확장 합니다.
* **Doppler Level** 을 **0** 으로 설정 합니다.
* **사용자 음성 효과** 에서 **부모 개체** 를 장면의 지 수로 **설정 합니다.**
* **최대 거리** 를 **1** 로 설정 합니다.

**최대 거리** 를 설정 하면 효과를 사용 하도록 설정 하기 전에 사용자에 게 부모 개체에 대 한 사용자 **음성 효과** 를 알려 줍니다.

* **사용자 음성 효과** 에서 **코러스 매개 변수** 를 확장 합니다.
* **깊이** 를 **0.1** 으로 설정 합니다.
* **탭 1 볼륨** 을 설정 하 고 **2 볼륨을 탭** 한 다음 **볼륨 3** 개를 **0.8** 으로 탭 합니다.
* **원본 사운드 볼륨** 을 **0.5** 으로 설정 합니다.

이전 설정은 사용자의 음성에 다양 한 다양성을 추가 하는 데 사용 되는 Unity **AudioChorusFilter** 의 매개 변수를 구성 합니다.

* **사용자 음성 효과** 에서 **Echo 매개 변수** 를 확장 합니다.
* **지연 시간** 을 **300** 으로 설정
* **감소 비율** 을 **0.2** 로 설정 합니다.
* **원래 사운드 볼륨** 을 **0** 으로 설정 합니다.

이전 설정은 사용자의 음성 에코를 발생 시키는 데 사용 되는 Unity **AudioEchoFilter** 의 매개 변수를 구성 합니다.

사용자 음성 효과 스크립트는 다음을 담당 합니다.

* 사용자와 스크립트가 연결 된 **GameObject** 간의 거리를 측정 합니다.
* 사용자가 **GameObject** 를 연결 하는지 여부를 확인 하는 중입니다.

효과를 사용 하도록 설정 하려면 거리에 관계 없이 사용자가 GameObject 연결 해야 합니다.

* **AudioChorusFilter** 및 **AudioEchoFilter** 를 **오디오 소스** 에 적용 하 고 구성 합니다.
* 필터를 사용 하지 않도록 설정 하 여 효과를 비활성화 합니다.

사용자 음성 효과는 [MixedRealityToolkit For unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)에서 Mic 스트림 선택기 구성 요소를 사용 하 여 고품질의 음성 스트림을 선택 하 고 Unity의 오디오 시스템으로 라우팅합니다.

* **계층** 패널에서 **관리자** 를 선택 합니다.
* **검사기** 패널에서 **Speech Input Handler** 를 확장 합니다.
* **음성 입력 처리기** 에서 지 이상 **표시** 를 확장 합니다.
* **No 함수** 를 UnderworldBase로 변경 합니다 **.**

![키워드: 지 각 표시](images/showunderworld.png)

* 지 각 **지를 확장** 합니다.
* UnderworldBase **함수** 를 변경 하지 않습니다.

![키워드: 지 각을 숨깁니다.](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>빌드 및 배포

* 이전과 마찬가지로 Unity에서 프로젝트를 빌드하고 Visual Studio에 배포 합니다.

응용 프로그램을 배포한 후:

* 표면 (벽, 바닥, 테이블)을 표면에 표시 하 고 "지 각"을 *표시* 합니다.

지 수를 표시 하 고 다른 모든 holograms를 숨깁니다. 지 수가 표시 되지 않으면 실제 화면을 향하고 있는지 확인 합니다.

* 1 미터 내에서의 접근 방식으로 통신을 시작 합니다.

이제 오디오 효과가 음성에 적용 되었습니다.

* 지 수를 끄고 효과가 더 이상 적용 되지 않는 방식을 확인 합니다.
* 지 수를 숨기려면 "지 수 *숨기기"* 라고 표시 합니다.

지 수는 숨겨지고 이전에 숨겨진 holograms 다시 표시 됩니다.

## <a name="the-end"></a>끝

축하합니다! 이제 **MR 공간 220: 공간 소리** 를 완료 했습니다.

세계를 듣고 경험을 바탕으로 경험을 해보세요.