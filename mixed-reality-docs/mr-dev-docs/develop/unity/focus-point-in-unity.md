---
title: Unity의 포커스 포인트
description: HoloLens 및 Windows Mixed Reality 모던 헤드셋에 대 한 포커스 지점을 설정 하 여 Unity의 홀로그램 안정성을 수동으로 조정 하는 방법을 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 포커스 지점, 포커스 평면, 안정화 평면, 안정화 지점, reprojection, LSR, 깊이 버퍼, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 91fba310cf86f145174512c4c1e23d69907d2f57f48f3fe1992b417eb283235f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203595"
---
# <a name="focus-point-in-unity"></a>Unity의 포커스 포인트

**네임 스페이스:** *unityengine. XR. WSA*<br>
**유형**: *HolographicSettings*

현재 표시 되는 holograms를 가장 잘 안정화 하는 방법에 대 한 힌트를 HoloLens 제공 하려면 [포커스 지점을](../platform-capabilities-and-apis/hologram-stability.md#reprojection) 사용 합니다.

Unity에서 포커스 지점을 설정 하려면 *HolographicSettings. SetFocusPointForFrame ()* 를 사용 하 여 모든 프레임을 설정 해야 합니다. 프레임에 대 한 포커스 지점이 설정 되지 않은 경우 기본 안정화 평면이 사용 됩니다.

> [!NOTE]
> 기본적으로 새 Unity 프로젝트에는 "깊이 버퍼 공유 사용" 옵션이 설정 되어 있습니다.  이 옵션을 사용 하는 경우 응용 프로그램에서 포커스 지점을 지정 하지 않고도 몰입 형 데스크톱 헤드셋 또는 RS4 (Windows 10 4 월 2018 업데이트) 이상을 실행 하는 HoloLens에서 실행 되는 Unity 앱이 Windows에 대 한 깊이 버퍼를 제출 하 여 홀로그램의 안정성을 자동으로 최적화 합니다.
> * 모던 데스크톱 헤드셋에서 픽셀 단위 깊이 기반 재 프로젝션을 사용 합니다.
> * Windows 10 4 월 2018 업데이트 이상을 실행 하는 HoloLens에서 깊이 버퍼를 분석 하 여 최적의 안정화 평면을 자동으로 선택 합니다.
>
> 이러한 방법 중 하나는 각 프레임에 대 한 포커스 지점을 선택 하기 위해 앱에서 명시적으로 작업 하지 않고도 이미지 품질을 더욱 개선 하는 것입니다.  포커스 지점을 수동으로 제공 하는 경우 위에서 설명한 자동 동작이 재정의 되 고 일반적으로 홀로그램 안정성이 감소 됩니다.  일반적으로 Windows 10 4 월 2018 업데이트로 아직 업데이트 되지 않은 HoloLens에서 앱이 실행 되는 경우에만 수동 포커스 지점을 지정 해야 합니다.

### <a name="example"></a>예제

*SetFocusPointForFrame* 정적 함수에서 사용할 수 있는 오버 로드에 의해 제안 된 대로 포커스 지점을 설정 하는 방법에는 여러 가지가 있습니다. 아래에서는 각 프레임에 대해 제공 된 개체에 포커스 평면을 설정 하는 간단한 예제를 제공 합니다.

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

> [!NOTE]
> 위의 간단한 코드는 포커스가 있는 개체가 사용자 뒤에서 종료 되는 경우 홀로그램의 안정성을 낮출 수 있습니다. 일반적으로 포커스 지점을 수동으로 지정 하는 대신 **[깊이 버퍼 공유 사용](camera-in-unity.md#sharing-depth-buffers)** 을 설정 하는 것이 좋습니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 혼합 현실 플랫폼 기능과 Api를 탐색 하는 것이 좋습니다. 여기에서 다음 항목으로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [추적 손실](tracking-loss-in-unity.md)

또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.

> [!div class="nextstepaction"]
> [HoloLens 또는 Windows Mixed Reality 모던 헤드셋에 배포](../platform-capabilities-and-apis/using-visual-studio.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#3-advanced-features)으로 돌아갈 수 있습니다.

### <a name="see-also"></a>참고 항목

* [안정화 평면](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
