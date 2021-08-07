---
title: Unity 입력 포팅 가이드
description: Unity에서 Windows Mixed Reality에 대 한 입력을 처리 하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: 입력, unity, 포팅
ms.openlocfilehash: b2c328152d681a4c8753e29babf0f3ece6bdc0d3f21f9df6dd8de150c3fb47f0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212081"
---
# <a name="input-porting-guide-for-unity"></a>Unity 입력 포팅 가이드

두 가지 방법 중 하나를 사용 하 여 Windows Mixed Reality 입력 논리를 이식할 수 있습니다. 첫 번째 방법은 Unity의 일반 입력을 사용 하는 것입니다. GetButton/Getbutton Api는 여러 플랫폼에 걸쳐 있습니다. 두 번째는 Windows 관련 XR입니다. WSA. 입력 api-동작 컨트롤러 및 HoloLens에 대해 구체적으로 다양 한 데이터를 제공 합니다.

## <a name="general-inputgetbuttongetaxis-apis"></a>일반 입력. GetButton/Getbutton Api

Unity는 현재 일반 입력을 사용 합니다. GetButton/Input. Getbutton Api를 사용 하 여 [Oculus sdk](https://docs.unity3d.com/Manual/OculusControllers.html) 및 [openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html)의 입력을 노출 합니다. 앱이 입력에 이러한 Api를 이미 사용 하 고 있는 경우 입력. GetButton/Input. Getbutton Api는 Windows Mixed Reality에서 동작 컨트롤러를 지원 하기에 가장 쉬운 경로입니다. 입력 관리자에서 단추 및 축만 다시 매핑해야 합니다.

자세한 내용은 [unity 단추/축 매핑 표](../unity/motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 및 [일반적인 unity api 개요](../unity/motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)를 참조 하세요.

## <a name="windows-specific-xrwsainput-apis"></a>Windows 별 XR. WSA. 입력 Api

앱에서 각 플랫폼에 대 한 사용자 지정 입력 논리를 이미 빌드하는 경우 **XR** 네임 스페이스에서 Windows 특정 공간 입력 api를 사용할 수 있습니다. 여기에서 위치 정확도 나 원본 종류와 같은 추가 정보에 액세스 하 여 HoloLens에 대 한 실습 및 컨트롤러를 구분할 수 있습니다.

자세한 내용은 [UnityEngine. XR api 개요](../unity/motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)를 참조 하세요.

## <a name="grip-pose-vs-pointing-pose"></a>그립 포즈 및 포인팅 포즈

Windows Mixed Reality는 서로 다른 폼 팩터에서 동작 컨트롤러를 지원 합니다. 각 컨트롤러의 디자인은 사용자의 손 위치와 앱이 컨트롤러를 렌더링할 때를 가리키는 데 사용 해야 하는 자연 스러운 "전달" 방향 간의 관계에 차이가 있습니다.

이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스에 대해 조사할 수 있는 두 가지 종류의 포즈가 있습니다.

* **그립** 은 HoloLens에서 감지 된 손바닥의 위치 또는 동작 컨트롤러를 보유 하는 야자수의 위치를 나타냅니다.
    * 모던 헤드셋에서는이 포즈를 사용 하 여 사용자 **의 손을** 나 **사용자의 손으로 보유 한 개체**(예: 소드 또는 포)를 렌더링 하는 데 가장 적합 합니다.
    * **그립 위치**: 컨트롤러를 자연스럽 게 유지 하는 경우 왼쪽 또는 오른쪽으로 조정 하 여 그립 내 위치를 가운데에 맞춥니다.
    * **그립 방향 오른쪽 축**: 손 모양 5 손가락 포즈를 형성 하는 손을 완전히 열 때 palm (왼쪽 야자나무에서 오른쪽으로 뒤로)의 광선을 만듭니다.
    * **그립 방향 전방 축**: 컨트롤러를 보유 하 고 있는 것 처럼, 손 모양 없는 손가락으로 구성 된 튜브를 통해 "전달" 하는 빛을 부분적으로 닫는 경우입니다.
    * **그립 방향 up 축**: 오른쪽 및 전방 정의에 의해 암시 된 위쪽 축입니다.
    * Unity의 교차 공급 업체 입력 API (XR)를 통해 그립 포즈에 액세스할 수 있습니다 **[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). getlocalposition/rotation**) 또는 Windows 특정 API (**sourcestate/rotation**)를 통해 그립 포즈를 요청 합니다.
* 앞에 있는 컨트롤러의 팁을 나타내는 **포인터가 포즈** 입니다.
    * 이 포즈는 컨트롤러 모델 자체를 렌더링할 때 **UI를 가리킬** 때 raycast에 가장 잘 사용 됩니다.
    * 현재 포인터 포즈는 Windows 관련 API (**sourcestate/Rotation**, 포인터 포즈 요청)를 통해서만 사용할 수 있습니다.

이러한 포즈 좌표는 모두 Unity 세계 좌표로 표현 됩니다.

## <a name="see-also"></a>추가 정보
* [동작 컨트롤러](). /.. /design/motion-controllers.md)
* [Unity의 동작 컨트롤러](../unity/motion-controllers-in-unity.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR 추적](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [포팅 가이드](porting-guides.md)
