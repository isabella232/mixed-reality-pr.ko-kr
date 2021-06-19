---
title: Unity의 OpenXR 플러그 인 지원 기능
description: Unity에서 혼합 현실 개발에 대해 OpenXR에서 지 원하는 기능을 알아봅니다.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 보강 현실, 가상 현실, 혼합 현실 헤드셋, 학습, 자습서, 시작
ms.openlocfilehash: 371815d6410a7add8ee9c62f72d746d74ad397b0
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392671"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Unity의 혼합 현실 OpenXR 지원 되는 기능

**Mixed Reality OpenXR 플러그 인** 패키지는 Unity의 **OpenXR 플러그 인** 을 확장 한 것으로, HoloLens 2 및 Windows Mixed Reality 헤드셋의 기능 모음을 지원 합니다. 계속 하기 전에 Unity 프로젝트가 [OpenXR에 대해 구성](openxr-getting-started.md)되어 있는지 확인 합니다.

## <a name="whats-supported"></a>지원되는 내용

현재 지원 되는 기능은 다음과 같습니다.

* HoloLens 2 용 UWP 응용 프로그램을 지원 하 고 HoloLens 2 응용 프로그램 모델을 최적화 합니다.
* 최신 컨트롤러 프로필 및 holographic app remoting과 함께 Windows Mixed Reality 헤드셋에 대해 Win32 VR 응용 프로그램을 지원 합니다.
* 앵커와 바인딩되지 않은 공간을 사용한 세계 크기 조정 추적.
* [저장소 API를 고정 하 여](spatial-anchors-in-unity.md) HoloLens 2 로컬 저장소에 앵커를 유지 합니다.
* 새 HP 반향 G2 컨트롤러를 포함 하 여 [동작 컨트롤러 및 직접 상호 작용](#motion-controller-and-hand-interactions).
* 26 개의 조인트와 조인트 반지름 입력을 사용 하 여 직접 추적 합니다.
* HoloLens 2의 눈 응시 상호 작용입니다.
* HoloLens 2에서 사진/비디오 (PV) 카메라를 찾는 중입니다.
* 혼합 현실 PV 카메라를 통한 세 번째 눈동자 렌더링을 사용 하 여 캡처합니다.
* 는 [Holographic Remoting 앱을 사용 하 여 HoloLens 2에 대 한 "Play"를](unity-play-mode.md#unity-play-mode-with-holographic-remoting)지원 하므로 개발자는 장치에 빌드 및 배포 하지 않고도 스크립트를 디버그할 수 있습니다.
* [Mrtk OpenXR 공급자 지원을](openxr-getting-started.md#using-mrtk-with-openxr-support)통해 Mrtk Unity 2.5.3 이상 버전과 호환 됩니다.
* Unity [Arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 이상 버전과 호환 됩니다.
* (0.1.3에 추가 됨) 빌드 및 배포 된 Windows 독립 실행형 앱에서 [데스크톱 앱 Holographic 원격](holographic-remoting-desktop.md) 을 지원 합니다.
* (0.1.4에 추가 됨) SpatialGraphNode을 통해 HoloLens2에서 [QR 코드 추적](#qr-codes) 을 지원 합니다.
* (0.2.0에 추가 됨) Holographic Remoting에서 **앵커** 지원
* (0.2.0에 추가 됨) **손을 조인트 및 손 모양 추적을** 모두 지원 합니다.
* (0.2.0에 추가 됨) 평면 검색을 위한 **Ar설계도 Esubsystems** 를 지원 하 고 **ARRaycastManager** 를 사용 하 여 홀로그램을 넣습니다.
* (0.9.0)는 공간 매핑에 대 한 **XRMeshSubsystem** 및 **ARMeshManager** 를 지원 합니다.
* (0.9.0에 추가 됨) Windows 플러그인 용 Azure 공간 앵커 SDK를 지원 합니다. 자세한 내용은 [GitHub의 Mixed Reality + OpenXR Azure 공간 앵커 샘플 프로젝트](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)를 참조 하세요.
* (0.9.1에 추가 됨) 빌드 및 배포 된 Windows UWP 앱에서 데스크톱 앱 Holographic 원격 기능을 지원 합니다.
* (0.9.4에 추가 됨) HoloLens 2 응용 프로그램에 대 한 ARM64 외에 ARM 플랫폼을 지원 합니다.

## <a name="motion-controller-and-hand-interactions"></a>동작 컨트롤러 및 직접 상호 작용

Unity의 혼합 현실 상호 작용에 대 한 기본 사항을 알아보려면 unity [XR 입력](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)을 참조 하세요. 이 Unity 설명서에서는 컨트롤러 특정 입력에서 보다 일반화할 수 있는 **Inputfeatureusage** s에 대 한 매핑, 사용 가능한 XR 입력을 식별 하 고 분류 하는 방법, 이러한 입력에서 데이터를 읽는 방법 등에 대해 설명 합니다.

Mixed Reality OpenXR 플러그 인은 아래에 설명 된 대로 표준 **Inputfeatureusage** 에 매핑되는 추가 입력 상호 작용 프로필을 제공 합니다.

| InputFeatureUsage | HP 반향 G2 컨트롤러 (OpenXR) | HoloLens 손 (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | 조이스틱이 | |
| primary2DAxisClick | 조이스틱-클릭 | |
| 트리거 | 트리거  | |
| 그리퍼 | 그리퍼 | 공중 탭 또는 꽉의 |
| primaryButton | [X/A]-키 누르기 | 에어 탭 |
| secondaryButton | [Y/B]-키 누르기 | |
| gripButton | 그립-누름 | |
| triggerButton | 트리거-누르기 | |
| menuButton | 메뉴 | |

### <a name="aim-and-grip-poses"></a>목표 및 그립 포즈

OpenXR 입력 상호 작용을 통해 두 가지 포즈 집합에 액세스할 수 있습니다.

* 손으로 개체를 렌더링 하는 그립
* 세계를 가리키는 목표입니다.

이 디자인 및 두 포즈 간의 차이점에 대 한 자세한 내용은 [OpenXR 사양 입력 하위 경로](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)에서 찾을 수 있습니다.

InputFeatureUsages **Deviceposition**, **devicerDeviceAngularVelocity ation**, **Devicevelocation** 및  에서 제공 하는 포즈는 모두 OpenXR **그립** 포즈를 나타냅니다. 그립 포즈와 관련 된 InputFeatureUsages은 Unity의 [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)에서 정의 됩니다.

InputFeatureUsages **Pointerposition**, **pointerposition**, **pointerposition** 에서 제공 하는 포즈는  모두 OpenXR **목표** 포즈를 나타냅니다. 이러한 InputFeatureUsages은 포함 된 c # 파일에 정의 되어 있지 않으므로 다음과 같이 사용자 고유의 InputFeatureUsages을 정의 해야 합니다.

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptics

Unity의 XR 입력 시스템에서 haptics를 사용 하는 방법에 대 한 자세한 내용은 unity의 unity [설명서 XR haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)를 참조 하세요.

## <a name="qr-codes"></a>QR 코드

HoloLens 2는 헤드셋 주변 환경의 QR 코드를 감지하여 각 코드의 실제 위치에 좌표계를 설정할 수 있습니다. 자세한 내용은 [QR 코드 추적](../platform-capabilities-and-apis/qr-code-tracking.md) 설명서에서 확인할 수 있습니다.  OpenXR 플러그 인을 사용 하는 경우 [ `SpatialGraphNodeId` qr api에서](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) 를 잡고 API를 사용 `Microsoft.MixedReality.OpenXR.SpatialGraphNode` 하 여 qr 코드를 찾습니다.

참조를 위해 GitHub에는 [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)에 대 한 자세한 사용 설명이 포함 된 [QR 추적 샘플 프로젝트가](https://github.com/yl-msft/QRTracking) 있습니다.

## <a name="troubleshooting"></a>문제 해결

HoloLens 2에서 Unity 앱을 일시 중단 하 고 다시 시작 하는 경우 앱이 올바르게 다시 시작 될 수 없습니다. 그러면 HoloLens 보기에서 4 개의 회전 점이 발생 합니다.

* OpenXR 프로젝트 설정에서 해결 방법으로 **깊이 전송 모드** 를 **없음** 으로 설정 합니다.
