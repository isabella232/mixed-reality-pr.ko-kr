---
title: Unity의 응시
description: 응시는 사용자가 혼합 현실에서 앱이 만드는 holograms를 대상으로 하는 기본 방법입니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 눈에 응시, 헤드-응시, unity, 홀로그램, 혼합 현실, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: ca33fef5a5a761df83ed7991b366cf711a5db224
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010364"
---
# <a name="head-gaze-in-unity"></a>헤드-Unity에서의 응시

[Holograms](../../discover/hologram.md) 는 사용자가 [혼합 현실](../../discover/mixed-reality.md)에서 만든 앱을 대상으로 [하는 기본](../../design/gaze-and-commit.md) 방법입니다.

## <a name="implementing-head-gaze"></a>헤드-응시 구현

개념적으로 사용자의 헤드셋에서 광선을 전달 하 여 [헤드](../../design/gaze-and-commit.md) 를 확인 합니다. Unity에서 사용자의 헤드 위치와 방향은 [카메라](camera-in-unity.md) [(구체적으로](https://docs.unity3d.com/ScriptReference/Camera-main.html)는 안 됨)를 통해 노출 됩니다. [transform. forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) 및 [Unityengine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transform. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

GameObject [를 호출 하면](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 3d 충돌 지점을 비롯 한 충돌에 대 한 정보를 포함 하는 [Raycasthit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) 및 헤드-응시 빛의 기타 제공 됩니다.

### <a name="example-implement-head-gaze"></a>예: 헤드-응시 구현

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>모범 사례

위의 예제에서는 업데이트 루프에서 단일 raycast를 실행 하 여 사용자의 헤드가 가리키는 대상을 찾는 반면 단일 개체를 사용 하 여 모든 헤드-응시 프로세스를 관리 하는 것이 좋습니다. 헤드-응시 논리를 결합 하 여 앱의 귀중 한 처리 능력을 절약 하 고, raycasting를 프레임당 하나로 제한 합니다.

## <a name="visualizing-head-gaze"></a>헤드 시각화-응시

컴퓨터에서 마우스 포인터를 사용 하는 것과 마찬가지로 사용자의 헤드를 나타내는 [커서](../../design/cursors.md) 를 구현 해야 합니다. 사용자가 대상으로 하는 콘텐츠를 알면 상호 작용할 대상이 높아집니다.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Head-Mixed Reality Toolkit의 Head-응시 
MRTK의 [입력 관리자](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) 에서 헤드-응시에 액세스할 수 있습니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞서 소개한 Unity 개발 경험을 팔로 사용할 경우 MRTK 핵심 빌딩 블록을 탐색 하는 것이 좋습니다. 여기에서 다음 구성 요소를 계속 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [제스처 및 모션 컨트롤러](gestures-and-motion-controllers-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [카메라](camera-in-unity.md)
* [커서](../../design/cursors.md)
* [헤드 게이즈 및 커밋](../../design/gaze-and-commit.md)
