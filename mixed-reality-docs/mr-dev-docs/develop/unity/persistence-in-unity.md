---
title: Unity의 지속성
description: 지속성을 사용하면 사용자가 원하는 위치에 개별 홀로그램을 고정한 다음, 나중에 여러 앱 사용을 통해 찾을 수 있습니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 지속성, Unity, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋
ms.openlocfilehash: 9283191c024cbe33ecda3946a4e9bcbd5f3708c21a3578484b547207ee70a49b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208973"
---
# <a name="persistence-in-unity"></a>Unity의 지속성

**네임스페이스:** *UnityEngine.XR.WSA.Persistence*<br>
**클래스:** *WorldAnchorStore*

WorldAnchorStore는 홀로그램이 애플리케이션의 인스턴스에서 특정 실제 위치에 유지되는 홀로그램 환경을 만드는 핵심입니다. 그런 다음, 사용자는 원하는 위치에 개별 홀로그램을 고정하고 나중에 앱의 여러 용도에 대해 동일한 지점에서 찾을 수 있습니다.

## <a name="how-to-persist-holograms-across-sessions"></a>세션 간에 홀로그램을 유지하는 방법

WorldAnchorStore를 사용하면 세션 간에 WorldAnchor의 위치를 유지할 수 있습니다. 세션 간에 홀로그램을 실제로 유지하려면 특정 세계 앵커를 사용하는 GameObjects를 별도로 추적해야 합니다. 종종 세계 앵커를 사용하여 GameObject 루트를 만들고 로컬 위치 오프셋을 사용하여 자식 홀로그램을 고정하는 것이 타당합니다.

이전 세션에서 홀로그램을 로드하려면 다음을 수행합니다.
1. WorldAnchorStore를 얻습니다.
2. 세계 앵커의 ID를 제공하는 세계 앵커와 관련된 앱 데이터 로드
3. ID에서 세계 앵커 로드

향후 세션에 대해 홀로그램을 저장하려면 다음을 수행합니다.
1. WorldAnchorStore를 얻습니다.
2. ID를 지정하여 세계 앵커 저장
3. ID와 함께 세계 앵커와 관련된 앱 데이터 저장

### <a name="getting-the-worldanchorstore"></a>WorldAnchorStore 받기

작업을 수행할 준비가 되면 알 수 있도록 WorldAnchorStore에 대한 참조를 유지하려고 합니다. 비동기 호출이므로 시작하는 즉시 다음을 호출하려고 합니다.

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

이 경우 StoreLoaded는 WorldAnchorStore가 로드를 완료한 경우에 대한 처리기입니다.

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

이제 특정 World Anchors를 저장하고 로드하는 데 사용할 WorldAnchorStore에 대한 참조가 있습니다.

### <a name="saving-a-worldanchor"></a>WorldAnchor 저장

저장하려면 저장하려는 이름을 지정하고 저장하려는 경우 이전에 얻은 WorldAnchor에 전달하기만 하면됩니다. 참고: 동일한 문자열에 두 개의 앵커를 저장하려고 하면 실패합니다(저장소. 저장하면 false가 반환됩니다.) 새 저장을 저장하기 전에 이전 저장을 삭제합니다.

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>WorldAnchor 로드

로드하려면 다음을 수행합니다.

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

저장소를 사용할 수도 있습니다. Delete() - 이전에 저장하고 저장한 앵커를 제거합니다. 이전에 저장된 모든 데이터를 제거하려면 Clear()를 선택합니다.

### <a name="enumerating-existing-anchors"></a>기존 앵커 열거

이전에 저장된 앵커를 검색하려면 GetAllIds를 호출합니다.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>여러 디바이스에 대한 홀로그램 유지

<a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 사용하여 로컬 WorldAnchor에서 지속성 클라우드 앵커를 만들 수 있습니다. 그러면 해당 디바이스가 동시에 함께 표시되지 않더라도 앱이 여러 HoloLens, iOS 및 Android 디바이스에서 찾을 수 있습니다.  클라우드 앵커는 영구적이므로 시간이 지남에 따라 여러 디바이스에서 동일한 물리적 위치에서 해당 앵커를 기준으로 렌더링된 콘텐츠를 볼 수 있습니다.

Unity에서 공유 환경 빌드를 시작하려면 5분 Azure Spatial Anchors Unity 빠른 시작을 사용해 <a href="/azure/spatial-anchors/unity-overview" target="_blank">보세요.</a>

Azure Spatial Anchors 실행하면 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞에서 설명한 Unity 개발 검사점 여정을 수행하는 경우 Mixed Reality 핵심 구성 요소에 대해 탐색해야 합니다. 여기에서 다음 구성 요소로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [공간 매핑](spatial-mapping-in-unity.md)

또는 Mixed Reality 플랫폼 기능 및 API로 이동합니다.

> [!div class="nextstepaction"]
> [공유 환경](shared-experiences-in-unity.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#2-core-building-blocks)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목
* [공간 앵커 지속성](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity용 Azure Spatial Anchors SDK</a>