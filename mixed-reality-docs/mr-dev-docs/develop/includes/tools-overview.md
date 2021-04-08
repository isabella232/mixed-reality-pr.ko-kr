---
ms.openlocfilehash: d7e248788d4c4976acbb9ff23177d354894f57dd
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105958191"
---
# <a name="unity"></a>[Unity](#tab/unity)

![Unity 로고 배너](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-recommended-unity-version"></a>1. 권장 Unity 버전 다운로드 

Mixed Reality 개발에 권장되는 현재 버전은 **Unity 2019.4 LTS(장기 지원)** 입니다. Unity를 설치하고 관리할 때 가장 좋은 방법은 **Unity Hub** 를 사용하는 것입니다. 

> [!NOTE]
>  Unity 2020 LTS를 사용 중인 경우 HoloLens 2 개발에 Mixed Reality 지원이 제공됩니다. 그러나 현재 몇 가지 알려진 문제가 있습니다. 이 버전은 올해 후반에 권장 Unity 버전이 될 예정입니다. 

다양한 Unity 엔진과 XR 플러그 인 버전에서 사용할 수 있는 Mixed Reality 지원을 알아보려면 [Unity 버전 및 XR 플러그 인 선택](../unity/choosing-unity-version.md)을 참조하세요.

> [!div class="nextstepaction"]
> [Unity Hub 다운로드](https://unity3d.com/get-unity/download)

Unity를 설치할 때는 **'Platforms'('플랫폼')** 아래에서 다음 구성 요소를 확인하세요.
* **유니버설 Windows 플랫폼 빌드 지원** 
* **Windows 빌드 지원(IL2CPP)**

![Unity 유니버설 Windows 플랫폼 빌드 지원 옵션](../../develop/images/Unity_Install_Option_UWP.png)

이러한 옵션 없이 Unity를 설치한 경우 Unity Hub의 **'Add Modules'('모듈 추가')** 메뉴를 통해 추가할 수 있습니다.

![Unity Windows 빌드 지원 옵션](../../develop/images/Unity_Install_Option_UWP2.png)


### <a name="2-install-the-mixed-reality-feature-tool"></a>2. Mixed Reality Feature Tool 설치

[Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md)은 개발자가 혼합형 현실 기능 패키지를 검색하고 Unity 프로젝트에 추가하는 데 사용되는 새로운 방법입니다. 

이름 또는 범주로 패키지를 검색하고, 종속성을 확인하고, 가져오기 전에 프로젝트 매니페스트 파일에 대한 제안된 변경 내용도 볼 수 있습니다. 원하는 패키지의 유효성을 검사하면 Mixed Reality Feature Tool에서 사용자가 선택한 프로젝트로 해당 패키지를 다운로드합니다.

#### <a name="importing-the-mixed-reality-toolkit"></a>Mixed Reality Toolkit 가져오기

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK([Mixed Reality Toolkit](../unity/mrtk-getting-started.md))는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다. 

* [설치 및 사용 지침](../unity/welcome-to-mr-feature-tool.md#system-requirements)을 따르고 **Mixed Reality Toolkit Foundation** 패키지를 선택하여 Mixed Reality Toolkit 패키지를 설치합니다.

큐레이트된 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 또는 [VR](../unity/unity-development-wmr-overview.md#1-getting-started) 개발 경험의 시작 섹션을 완료하는 것이 좋습니다. HoloLens용 Unity 개발 경험을 이미 따르고 있는 경우 아래 나열된 나머지 설정 단계를 완료하고 [HoloLens 2 시작 자습서](../unity/tutorials/mr-learning-base-01.md)를 계속 진행하세요.

> [!IMPORTANT]
> 설치 지침은 MRTK 및 Unity 릴리스의 안정적인 최신 조합인 **MRTK 2.6.1** 및 **Unity 2019.4 LTS** 를 대상으로 합니다.

> [!NOTE]
> Unity에 MRTK를 사용하지 않으려면 [모든 상호 작용과 동작을 직접 스크립팅](../unity/configure-unity-project.md)해야 합니다.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity 배너](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality Toolkit-Unity(GitHub)** </a><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a>기타 도구 [선택 사항]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Mixed Reality 개발용 PC 설정

Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다. 또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다. 일부 도구는 이전 운영 체제에서 지원되지 않습니다.

> [!NOTE]
> HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다. 필요에 따라 아래 요구 사항을 충족해야 합니다.

#### <a name="for-hololens-development"></a>HoloLens 개발

HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 및 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 둘 다에 대한 시스템 요구 사항을 충족하는지 확인합니다. HoloLens 디바이스에서 앱을 실행하려면 [Windows 장치 포털 설치 지침](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)을 따라야 합니다. [HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.

HoloLens 에뮬레이터를 시작하려면 [HoloLens 에뮬레이터 사용](../platform-capabilities-and-apis/using-the-hololens-emulator.md)을 참조하세요.

HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.

#### <a name="hololens-troubleshooting"></a>HoloLens 문제 해결

##### <a name="setting-developer-mode-is-grayed-out"></a>개발자 모드 설정은 회색으로 표시됩니다.

디바이스에서 개발자 모드를 사용하는 데 문제가 발생하면 [디바이스 소유자](/hololens/security-adminless-os)가 아닐 수 있습니다. 다중 사용자 모드에서 디바이스를 먼저 사용하는 사용자가 디바이스 소유자입니다. 이후 사용자는 개발자 모드 또는 기타 구성 변경을 사용하는 데 필요한 권한이 없습니다. 하지만 [HoloLens 보안 설명서](/hololens/security-adminless-os#device-owner)에 자세히 설명된 Autopilot 환경의 첫 번째 사용자가 디바이스 소유자가 아닐 수 있는 예외가 있습니다.

가능한 솔루션은 다음과 같습니다.

* 디바이스를 다른 사용자나 개발자에게 전달하기 전에 디바이스 소유자가 개발자 모드를 켜도록 합니다.
* IT/MDM 관리자가 특정 디바이스 또는 개발자 디바이스 그룹에 대해 CSP [정책 ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)를 사용하도록 제안합니다. 
    * 이 정책은 [프로비전 패키지](/hololens/hololens-provisioning) 또는 [HoloLens 디바이스용 MDM](/hololens/hololens-mdm-configure)을 통해 설정할 수 있습니다.
* [ARC(Advanced Recovery Companion)](/hololens/hololens-recovery) 사용

> [!NOTE]
> 디바이스 관리에 대한 자세한 내용은 **[HoloLens 디바이스 관리](/hololens/hololens-csp-policy-overview)** 개요에서 확인할 수 있습니다.

##### <a name="i-cant-deploy-over-usb"></a>USB를 통해 배포할 수 없습니다.

USB를 통해 애플리케이션을 직접 배포할 수 없는 경우 위에 나열된 모든 설치 요구 사항을 충족했는지 확인하고 [단계별 자습서](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2)를 따르세요.

#### <a name="immersive-vr-headset-requirements"></a>몰입형 (VR) 헤드셋 요구 사항

>[!NOTE]
>다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.

>[!WARNING]
>이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.

몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.

현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.

<table>
<tr>
<th></th><th> 최소값</th><th> 권장</th>
</tr><tr>
<td> 프로세서</td><td> <b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</td><td> <b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</td>
</tr><tr>
<td> GPU</td><td> <b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td><td><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td>
</tr><tr>
<td> GPU 드라이버 WDDM 버전</td><td colspan="2"> WDDM 2.2 드라이버</td>
</tr><tr>
<td> 열 디자인 전원</td><td colspan="2"> 15W 이상</td>
</tr><tr>
<td> 그래픽 디스플레이 포트</td><td colspan="2"> 헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</td>
</tr><tr>
<td> 디스플레이 해상도</td><td colspan="2"> 해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</td>
</tr><tr>
<td> 메모리</td><td> 8GB&#160;RAM 이상</td><td> 16GB RAM 이상</td>
</tr><tr>
<td> 스토리지</td><td colspan="2"> &gt;10GB의 추가 사용 가능 공간</td>
</tr><tr>
<td> USB 포트</td><td colspan="2"> 헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0(액세서리 연결용)</td>
</tr>
</table>

Unity를 사용하는 MRTK 개발을 처음 접하는 경우 큐레이션된 Unity 개발 경험을 따르는 것이 좋습니다.

> [!div class="nextstepaction"]
> [HoloLens용 Unity 경험 시작](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [VR용 Unity 경험 시작](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 HoloLens용 Unity 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2 자습서 시리즈를 통해 작업하는 것입니다.

> [!div class="nextstepaction"]
> [HoloLens 2 자습서 시리즈](../unity/tutorials/mr-learning-base-01.md)

VR용 Unity 경험을 따르고 있는 경우, 다음 작업은 프로젝트를 설정하는 것입니다.

> [!div class="nextstepaction"]
> [WMR용 프로젝트 구성](../unity/configure-unity-project.md)

언제든지 [HoloLens](../unity/unity-development-overview.md#1-getting-started) 및 [VR](../unity/unity-development-wmr-overview.md#1-getting-started)용 Unity 개발 검사점으로 돌아갈 수 있습니다.

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1. 최신 버전 다운로드

HoloLens에 기본 제공되는 지원 기능을 최대한 활용하려면 [Unreal Engine 버전 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 이상을 설치하는 것이 좋습니다.

Epic Games 시작 관리자에서 **라이브러리** 탭으로 이동한 다음, **시작** 옆의 드롭다운 화살표를 선택하고 **옵션** 을 클릭합니다. **대상 플랫폼** 에서 **HoloLens 2** 를 선택하고 **적용** 을 클릭합니다.
![Unreal 설치 옵션 HoloLens 2](../../develop/images/Unreal_Install_Option_HoloLens2.png)

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. MRTK(Mixed Reality Toolkit) 가져오기
![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK(Mixed Reality Toolkit)는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다. MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다. 도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.

설치의 경우 큐레이션된 [Unreal 개발 경험](../unreal/unreal-development-overview.md)의 [시작 섹션](../unreal/unreal-development-overview.md#1-getting-started)을 완료하는 것이 좋습니다. Unreal 개발 경험을 이미 수행하고 있는 경우 아래 나열된 나머지 설정 단계를 완료하고 [HoloLens 2 시작 자습서](../unreal/tutorials/unreal-uxt-ch1.md)를 계속 진행하세요.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity 로고 이미지](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal(GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Unreal에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.

#### <a name="other-tools-optional"></a>기타 도구 [선택 사항]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. 혼합 현실 개발용 PC 설정

Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다. 또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다. 일부 도구는 이전 운영 체제에서 지원되지 않습니다.

> [!NOTE]
> HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다. 필요에 따라 아래 요구 사항을 충족해야 합니다.

#### <a name="for-hololens-development"></a>HoloLens 개발

HoloLens 개발을 위해 개발 PC를 설정할 때 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 및 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다. HoloLens 디바이스에서 앱을 실행하려면 [Windows 장치 포털 설치 지침](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)을 따라야 합니다. [HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.

HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.

#### <a name="hololens-troubleshooting"></a>HoloLens 문제 해결

##### <a name="setting-developer-mode-is-grayed-out"></a>개발자 모드 설정은 회색으로 표시됩니다.

디바이스에서 개발자 모드를 사용하는 데 문제가 발생하면 [디바이스 소유자](/hololens/security-adminless-os)가 아닐 수 있습니다. 다중 사용자 모드에서 디바이스를 먼저 사용하는 사용자가 디바이스 소유자입니다. 이후 사용자는 개발자 모드 또는 기타 구성 변경을 사용하는 데 필요한 권한이 없습니다. 하지만 [HoloLens 보안 설명서](/hololens/security-adminless-os#device-owner)에 자세히 설명된 Autopilot 환경의 첫 번째 사용자가 디바이스 소유자가 아닐 수 있는 예외가 있습니다.

가능한 솔루션은 다음과 같습니다.

* 디바이스를 다른 사용자나 개발자에게 전달하기 전에 디바이스 소유자가 개발자 모드를 켜도록 합니다.
* IT/MDM 관리자가 특정 디바이스 또는 개발자 디바이스 그룹에 대해 CSP [정책 ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)를 사용하도록 제안합니다. 
    * 이 정책은 [프로비전 패키지](/hololens/hololens-provisioning) 또는 [HoloLens 디바이스용 MDM](/hololens/hololens-mdm-configure)을 통해 설정할 수 있습니다.
* [ARC(Advanced Recovery Companion)](/hololens/hololens-recovery) 사용

> [!NOTE]
> 디바이스 관리에 대한 자세한 내용은 **[HoloLens 디바이스 관리](/hololens/hololens-csp-policy-overview)** 개요에서 확인할 수 있습니다.

##### <a name="i-cant-deploy-over-usb"></a>USB를 통해 배포할 수 없습니다.

USB를 통해 애플리케이션을 직접 배포할 수 없는 경우 위에 나열된 모든 설치 요구 사항을 충족했는지 확인하고 [단계별 자습서](../unreal/tutorials/unreal-uxt-ch6.md)를 따르세요.

#### <a name="immersive-vr-headset-requirements"></a>몰입형 (VR) 헤드셋 요구 사항

>[!NOTE]
>다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.

>[!WARNING]
>이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.

몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.

현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.

<table>
<tr>
<th></th><th> 최소값</th><th> 권장</th>
</tr><tr>
<td> 프로세서</td><td> <b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</td><td> <b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</td>
</tr><tr>
<td> GPU</td><td> <b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td><td><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td>
</tr><tr>
<td> GPU 드라이버 WDDM 버전</td><td colspan="2"> WDDM 2.2 드라이버</td>
</tr><tr>
<td> 열 디자인 전원</td><td colspan="2"> 15W 이상</td>
</tr><tr>
<td> 그래픽 디스플레이 포트</td><td colspan="2"> 헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</td>
</tr><tr>
<td> 디스플레이 해상도</td><td colspan="2"> 해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</td>
</tr><tr>
<td> 메모리</td><td> 8GB&#160;RAM 이상</td><td> 16GB RAM 이상</td>
</tr><tr>
<td> 스토리지</td><td colspan="2"> &gt;10GB의 추가 사용 가능 공간</td>
</tr><tr>
<td> USB 포트</td><td colspan="2"> 헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0(액세서리 연결용)</td>
</tr>
</table>

Unreal를 사용하는 MRTK 개발을 처음 접하는 경우 큐레이션된 Unreal 개발 경험을 따르는 것이 좋습니다.

> [!div class="nextstepaction"]
> [Unreal 경험 시작](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unreal 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2 자습서 시리즈를 통해 작업하는 것입니다.

> [!div class="nextstepaction"]
> [HoloLens 2 자습서 시리즈](../unreal/tutorials/unreal-uxt-ch1.md)

언제든지 [Unreal 개발 검사점](../unreal/unreal-development-overview.md#1-getting-started)으로 돌아갈 수 있습니다.

# <a name="native-openxr"></a>[네이티브(OpenXR)](#tab/native)

 ![네이티브 앱 개발](../images/native_logo_banner.png)

네이티브 OpenXR 개발의 경우 다운로드할 엔진이 없습니다. 개발을 시작하는 데 필요한 모든 것은 [OpenXR 시작](../native/openxr-getting-started.md) 문서에서 찾을 수 있습니다.

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1. 혼합 현실 개발용 PC 설정

Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다. 또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다. 일부 도구는 이전 운영 체제에서 지원되지 않습니다.

#### <a name="for-hololens-development"></a>HoloLens 개발

HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다. HoloLens 디바이스에서 앱을 실행하려면 [Windows 장치 포털 설치 지침](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal)을 따라야 합니다. [HoloLens 에뮬레이터](../platform-capabilities-and-apis/using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.

HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.

> [!NOTE]
> HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다. 필요에 따라 아래 요구 사항을 충족해야 합니다.

#### <a name="hololens-troubleshooting"></a>HoloLens 문제 해결

##### <a name="setting-developer-mode-is-grayed-out"></a>개발자 모드 설정은 회색으로 표시됩니다.

디바이스에서 개발자 모드를 사용하는 데 문제가 발생하면 [디바이스 소유자](/hololens/security-adminless-os)가 아닐 수 있습니다. 다중 사용자 모드에서 디바이스를 먼저 사용하는 사용자가 디바이스 소유자입니다. 이후 사용자는 개발자 모드 또는 기타 구성 변경을 사용하는 데 필요한 권한이 없습니다. 하지만 [HoloLens 보안 설명서](/hololens/security-adminless-os#device-owner)에 자세히 설명된 Autopilot 환경의 첫 번째 사용자가 디바이스 소유자가 아닐 수 있는 예외가 있습니다.

가능한 솔루션은 다음과 같습니다.

* 디바이스를 다른 사용자나 개발자에게 전달하기 전에 디바이스 소유자가 개발자 모드를 켜도록 합니다.
* IT/MDM 관리자가 특정 디바이스 또는 개발자 디바이스 그룹에 대해 CSP [정책 ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)를 사용하도록 제안합니다. 
    * 이 정책은 [프로비전 패키지](/hololens/hololens-provisioning) 또는 [HoloLens 디바이스용 MDM](/hololens/hololens-mdm-configure)을 통해 설정할 수 있습니다.
* [ARC(Advanced Recovery Companion)](/hololens/hololens-recovery) 사용

> [!NOTE]
> 디바이스 관리에 대한 자세한 내용은 **[HoloLens 디바이스 관리](/hololens/hololens-csp-policy-overview)** 개요에서 확인할 수 있습니다.

#### <a name="immersive-vr-headset-requirements"></a>몰입형 (VR) 헤드셋 요구 사항

>[!NOTE]
>다음 지침은 몰입형(VR) 헤드셋 *개발 PC* 에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.

>[!WARNING]
>이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양* 을 나타내는 [최소 PC 하드웨어 호환성 지침](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.

몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.

현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.

<table>
<tr>
<th></th><th> 최소값</th><th> 권장</th>
</tr><tr>
<td> 프로세서</td><td> <b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</td><td> <b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</td>
</tr><tr>
<td> GPU</td><td> <b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td><td><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</td>
</tr><tr>
<td> GPU 드라이버 WDDM 버전</td><td colspan="2"> WDDM 2.2 드라이버</td>
</tr><tr>
<td> 열 디자인 전원</td><td colspan="2"> 15W 이상</td>
</tr><tr>
<td> 그래픽 디스플레이 포트</td><td colspan="2"> 헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</td>
</tr><tr>
<td> 디스플레이 해상도</td><td colspan="2"> 해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</td>
</tr><tr>
<td> 메모리</td><td> 8GB&#160;RAM 이상</td><td> 16GB RAM 이상</td>
</tr><tr>
<td> 스토리지</td><td colspan="2"> &gt;10GB의 추가 사용 가능 공간</td>
</tr><tr>
<td> USB 포트</td><td colspan="2"> 헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0(액세서리 연결용)</td>
</tr>
</table>

MRTK를 사용하는 네이티브 개발을 처음 접하는 경우 큐레이션된 네이티브 개발 경험을 따르는 것이 좋습니다.

> [!div class="nextstepaction"]
> [기본 경험 시작](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 네이티브 개발 검사점 경험을 수행하는 경우 다음 작업은 HoloLens 2에 대한 개발 환경을 구성하는 것입니다.

> [!div class="nextstepaction"]
> [HoloLens 2 설정](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

언제든지 [네이티브 개발 검사점](../native/directx-development-overview.md#1-getting-started)으로 돌아갈 수 있습니다.