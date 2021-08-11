---
title: Mixed Reality OpenXR 플러그 인 릴리스 정보
description: 최신 릴리스 정보와 Mixed Reality OpenXR 플러그 인에 대한 업그레이드의 최신 상태를 유지합니다.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: 568d5f25eceed385a1331cd2cf5fe6e3adb6f8228e85d6d2d316749fc2ee431c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187625"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a>Mixed Reality OpenXR 플러그 인 릴리스 정보

## <a name="100---current-release"></a>1.0.0 - 현재 릴리스

* ARAnchorManagers 존재 여부에 관계없이 앱 시작 시 XRAnchorSubsystem이 항상 시작되는 버그가 수정되었습니다.
* 재투영 모드가 제대로 작동하지 않는 버그가 수정되었습니다.

## <a name="100-preview2---2021-06-14"></a>1.0.0-preview.2 - 2021-06-14

* Unitys 1.2.2 OpenXR 플러그 인에 따라 다릅니다.
* Holographic 원격 기능을 개별 기능 그룹으로 변경했습니다.
* “Apply HoloLens 2 프로젝트 설정”이 프로젝트 색 공간을 변경하는 버그가 수정되었습니다. Unity OpenXR 1.2.0 플러그 인 이후에는 더 이상 필요하지 않습니다.
* 애플리케이션을 일시 중지하고 다시 시작한 후 연결 해제 없이 입력 디바이스가 연결되는 버그가 수정되었습니다.
* ARSession을 통해 플러그 인 및 현재 추적 상태를 감지하기 위한 지원이 추가되었습니다.
* “AR 기본 평면” ARFoundation 프리팹이 보이지 않는 버그가 수정되었습니다.

## <a name="100-preview1---2021-06-02"></a>1.0.0-preview.1 - 2021-06-02

* 미리 보기 확장 대신 MSFT 확장을 이해하는 OpenXR 장면이 지원됩니다.
* HoloLens 2의 평면 검색에는 더 이상 Mixed Reality OpenXR 런타임의 미리 보기 버전이 필요하지 않습니다.

## <a name="095---2021-05-21"></a>0.9.5 - 2021-05-21

* Unitys 1.2.0 OpenXR 플러그 인에 따라 다릅니다.
* 구성을 위해 새로운 기능 UI(OpenXR Plugin 1.2.0)에 적용되었습니다.
* 검색 가능한 카메라 공급자가 제대로 등록 취소되지 않는 버그가 수정되었습니다.
* [보존]의 일부 추가 사용을 정리했습니다.
* 입력 시스템 UI에서 “HP Reverb G2 컨트롤러(OpenXR)” 이름을 업데이트합니다.

## <a name="094---2021-05-20"></a>0.9.4 - 2021-05-20

* Unitys 1.2.0 OpenXR 플러그 인에 따라 다릅니다.
* 모션 컨트롤러 glTF 모델을 얻기 위해 새로운 C# API를 추가했습니다.
* 뷰 구성을 사용하도록 설정하고 재투영 설정을 지정하는 새로운 C# API를 추가했습니다.
* XRMeshSubsystem으로 메시를 계산하기 위한 추가 설정을 설정하는 새로운 C# API가 추가되었습니다.
* 동작 인식 이벤트를 구성하고 구독하기 위한 새로운 C# API가 추가되었습니다.
* Windows->XR->편집기 원격 설정 대화 상자를 추가했습니다.
* HoloLens UWP 애플리케이션에 대한 ARM 지원이 추가되었습니다.

## <a name="093---2021-04-29"></a>0.9.3 - 2021-04-29

* Holographic 원격 연결이 안정적이지 않은 버그가 수정되었습니다.
* Unity 1.1.1 OpenXR 플러그 인으로 업그레이드한 후 VR 렌더링 성능이 최적화되지 않는 버그가 수정되었습니다.

## <a name="092---2021-04-21"></a>0.9.2 - 2021-04-21

* 플러그 인 버전 0.9.1의 HoloLens 2에서 평면 검색은 Mixed Reality OpenXR 미리 보기 런타임의 버전 105에서 작동합니다.
* 플러그 인 버전 0.9.2의 HoloLens 2에서 평면 검색은 Mixed Reality OpenXR 미리 보기 런타임의 버전 106에서 작동합니다.
* XRInputSubsystem.* GetTrackingOriginMode(입력 시스템에서 관리하지 않음)와 같은 호출이 잘못된 값으로 성공을 반환하지 못하도록 InputProvider에서 사용하지 않는 일부 콜백을 제거했습니다.
* Unity 콘솔 경고를 방지하기 위해 사용되지 않는 XRAnchorStore 버전을 자체 파일로 분할합니다.

## <a name="091---2021-04-20"></a>0.9.1 - 2021-04-20

* Unitys 1.1.1 OpenXR 플러그 인에 따라 다릅니다.
* UWP 플랫폼용 Holographic 원격 애플리케이션에 대한 지원이 추가되었습니다.
* XRAnchorStore가 기본 스레드 외부에서 설정 인스턴스를 가져오려고 하는 UnityException을 수정했습니다.

## <a name="090---2021-03-29"></a>0.9.0 - 2021-03-29

* XRMeshSubsystem 및 ARMeshManager를 통한 공간 매핑 지원이 추가되었습니다.
* 다른 Unity 패키지를 지원하기 위해 OpenXR 핸들을 가져오는 새로운 C# API가 추가되어 OpenXR 확장을 사용합니다.
* Perception WinRT API를 사용하는 다른 Unity 패키지를 지원하기 위해 Windows.Perception API와 상호 운용할 수 있는 새로운 C# API를 추가했습니다.
* Windows Mixed Reality 기능 세트의 필수 기능에서 상호 작용 프로필을 제거하여 개발자가 테스트한 모션 컨트롤러를 선택할 수 있습니다.
* 사용자가 편집기 원격 기능을 올바르게 설정할 수 있도록 Holographic 편집기 원격 기능 검사기를 추가했습니다.
* 연결 실패 후 Holographic 편집기 원격 모드를 종료할 때 Unity 편집기가 충돌하는 버그가 수정되었습니다.
* 미리 곱하지 않는 알파 텍스처가 HoloLens 2에서 성능이 최적화되지 않는 버그가 수정되었습니다.
* 장면 원점이 바닥 수준에 있을 때 손 추적이 올바르게 위치하지 않는 버그가 수정되었습니다.
* 새 장면을 나가고 로드한 후 손 메시 추적이 사라지는 버그가 수정되었습니다.
* 검색 가능한 카메라 공급자가 제대로 정리되지 않는 버그가 수정되었습니다.
* XRAnchorStore API의 네임스페이스를 Microsoft.MixedReality.OpenXR로 수정했습니다.