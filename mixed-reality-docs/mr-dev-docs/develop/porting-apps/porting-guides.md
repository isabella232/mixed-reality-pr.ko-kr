---
title: VR 앱을 Windows Mixed Reality로 포팅
description: 기존 몰입형 애플리케이션을 Windows Mixed Reality 포팅하는 방법을 설명하는 단계별 연습입니다.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: port, unity, unreal, 미들웨어, 엔진, UWP, Win32, 이식, HoloLens 1세대, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 마이그레이션, Windows 10, 입력 매핑,
ms.openlocfilehash: c8f0ed76fc7288ed406e2044eb2f3edb8982865b5c956f460d2bc1b815e503df
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213520"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>VR 앱을 Windows Mixed Reality로 포팅

Windows 10 몰입형 및 홀로그램 헤드셋에 대한 지원이 포함되어 있습니다. OculusTunes 또는 HTC Vive와 같은 다른 디바이스용 콘텐츠를 빌드한 경우 운영 체제의 플랫폼 API 위에 있는 라이브러리에 대한 의존성이 있습니다. 기존 Win32 Unity VR 앱을 Windows Mixed Reality 가져오려면 공급업체별 VR SDK의 사용 대상을 Unity의 공급업체 간 VR API로 변경해야 합니다.

## <a name="porting-requirements"></a>포팅 요구 사항

높은 수준에서 다음 단계는 기존 콘텐츠 이식과 관련이 있습니다.
1. **PC에서 Windows 10 Fall Creators Update 실행 중인지 확인합니다(16299).** 이러한 빌드는 혼합 현실 개발에 가장 안정적이지 않기 때문에 Insider Skip Ahead 링에서 미리 보기 빌드를 더 이상 수신하지 않는 것이 좋습니다.
2. **최신 버전의 그래픽 또는 게임 엔진으로 업그레이드합니다.** 게임 엔진은 Windows 10 SDK 버전 10.0.15063.0(2017년 4월에 릴리스됨) 이상 버전을 지원해야 합니다.
3. **미들웨어, 플러그 인 또는 구성 요소를 업그레이드합니다.** 앱에 구성 요소가 포함된 경우 최신 버전으로 업그레이드하는 것이 좋습니다.
4. **중복 SDK에 대한 의존성 제거.** 콘텐츠가 대상으로 하는 디바이스에 따라 대신 Windows API를 대상으로 지정할 수 있도록 해당 SDK를 제거하거나 조건부로 컴파일해야 합니다. 이 시나리오의 예로는 SteamVR이 있습니다.
5. **빌드 문제를 통해 작업합니다.** 이 시점에서 이식 연습은 앱, 엔진 및 가지고 있는 구성 요소에만 해당됩니다.

## <a name="common-porting-steps"></a>일반적인 포팅 단계

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. 올바른 개발 하드웨어가 있는지 확인합니다.

[VR 마조 가이드](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) 페이지에는 권장 개발 하드웨어가 나열됩니다.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. 최신 Windows 10 플라이트로 업그레이드

Windows Mixed Reality 플랫폼은 아직 개발 중입니다. ["Windows 초기 참가자" 항공편에](https://insider.windows.com/) 액세스하려면 Windows 참가자 프로그램 가입하는 것이 좋습니다.
1. [Windows 10 크리에이터스 업데이트](https://www.microsoft.com/software-download/windows10) 설치
2. [](https://insider.windows.com/) Windows 참가자 프로그램 조인합니다.
3. [개발자 모드](/windows/uwp/get-started/enable-your-device-for-development) 사용
4. 설정 > 업데이트 & 보안 **섹션을** 통해 Windows 초기 참가자 [항공편으로](/archive/blogs/uktechnet/joining-insider-preview) 전환합니다.

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. Visual Studio 최신 빌드로 업그레이드
* Visual Studio 사용하는 경우 최신 빌드로 업그레이드합니다.
* Visual Studio 2019에서 [도구 설치](../install-the-tools.md#installation-checklist) 페이지를 참조하세요.

### <a name="4-choose-the-correct-adapter"></a>4. 올바른 어댑터 선택
* GPU가 두 개 있는 Notebook과 같은 [시스템에서는 올바른 어댑터 를 대상으로 합니다.](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications) 이 기능은 ID3D11Device가 명시적으로 또는 암시적으로(미디어 파운데이션) 생성되는 Unity 및 네이티브 DirectX 앱에 적용됩니다.

## <a name="unity-porting-guidance"></a>Unity 포팅 지침

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Unreal 이식 지침

> [!IMPORTANT]
> HP Reverb G2 컨트롤러를 사용하는 경우 추가 입력 매핑 [지침은 이 문서를](../unreal/unreal-reverb-g2-controllers.md) 참조하세요.

## <a name="see-also"></a>추가 정보
* [최소 PC 하드웨어 호환성 지침 Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Mixed Reality 성능 이해](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity용 성능 권장 사항](../unity/performance-recommendations-for-unity.md)
* [모션 컨트롤러](../../design/motion-controllers.md)
* [Unity의 모션 컨트롤러](../unity/motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [포팅 가이드](porting-guides.md)