---
title: 사용자 고유의 몰입형 환경 디자인
description: Windows Mixed Reality 홈 환경을 직접 만드는 방법을 알아봅니다.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Home, Custom Environments, places, house, skyloft, user, create, mixed reality 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: c0f006d3e05cb0892a0a9b2014a4d46a0668f628cf369e38c63c83756148d778
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198606"
---
# <a name="design-your-own-immersive-environments"></a>사용자 고유의 몰입형 환경 디자인

>[!NOTE]
>이는 실험적인 기능입니다. 시도해 보고 재미있게 만드세요. 하지만 모든 것이 예상대로 작동하지 않는 경우에는 놀라워하지 마세요. 이 기능의 실행 가능성과 사용에 대한 관심을 평가하고 있으므로 [개발자 포럼](https://forums.hololens.com/categories/custom-home-environments)에서 사용자 환경(및 발견한 버그)에 대해 알려주세요.

[Windows 10 2018년 4월 업데이트부터](/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)시작 메뉴 장소 선택기()에 사용자 지정 환경을 추가하여 [Windows Mixed Reality 홈으로](../discover/navigating-the-windows-mixed-reality-home.md)사용할 수 있는 실험적 기능을 사용하도록 설정했습니다. Windows Mixed Reality 클리프 하우스 및 Skyloft의 두 가지 기본 환경을 가정으로 선택할 수 있습니다. 사용자 지정 환경을 만들면 직접 만든 목록을 확장할 수 있습니다. 이 기능을 초기 상태에서 사용하여 작성자와 개발자의 관심을 평가할 수 있습니다. 만드는 세계의 종류를 확인하고 다양한 제작 도구를 사용하여 작업하는 방법을 이해합니다.

사용자 지정 환경을 사용하는 경우 원격 보고, 앱과 상호 작용 및 홀로그램 배치는 클리프 하우스 및 Skyloft에서와 마찬가지로 작동합니다. 지형에서 웹을 찾아보거나 홀로그램으로 미래 도시를 채울 수 있습니다. 가능성은 무한합니다!

## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>사용자 지정 홈 환경</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>샘플 환경 시도

사용자 지정 홈 환경의 몇 가지 창의적인 가능성을 보여 주는 샘플 환경을 만들었습니다. 다음 단계에 따라 사용해 보세요.
1. [샘플 을 다운로드합니다(자체](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) 압축 풀기 실행 파일의 연결 지점).

    ![Island 샘플 환경](images/FantasyLand.jpg)<br>
    *Island 샘플 환경*<br>

2. 다운로드한 **Fantasy_Island.exe** 파일을 실행합니다.

    > [!NOTE]
    > 웹에서 다운로드한 .exe 파일을 실행하려고 하면(예: ) "Windows PC 보호" 팝업이 나타날 수 있습니다. 이 팝업에서 Fantasy_Island.exe 실행하려면 추가 **정보를** 선택한 다음, **실행을 선택합니다.** 이 보안 설정은 신뢰하지 않을 수 있는 파일을 다운로드하지 못하도록 보호하기 위한 것이므로 파일의 원본을 신뢰할 때만 이 옵션을 선택하세요.

3. **파일 탐색기** 열고 주소 표시줄에 다음 파일 위치를 붙여넣어 environments 폴더로 `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` 이동합니다.
4. 다운로드한 샘플 환경을 이 폴더에 복사합니다.
5. **Mixed Reality 포털** 다시 시작하여 장소 선택기에서 환경 목록을 새로 고칩니다.
6. 헤드셋을 찍습니다. 홈에 있으면 컨트롤러의 Windows **단추를** 사용하여 시작 메뉴 엽니다.
7. 고정된 앱 목록 위에 있는 **장소** 아이콘을 선택하여 홈 환경을 선택합니다.
8. 다운로드한 힌지 아일랜드 환경은 장소 목록에서 찾을 수 있습니다. 새 사용자 지정 홈 환경을 입력하려면 **표시 아일랜드를** 선택합니다.

## <a name="creating-your-own-custom-environment"></a>사용자 고유의 사용자 지정 환경 만들기

샘플 환경을 사용하는 것 외에도 선호하는 3D 편집 소프트웨어를 사용하여 사용자 고유의 사용자 지정 환경을 내보낼 수 있습니다. 

### <a name="modeling-guidelines"></a>모델링 지침

환경을 모델링할 때 사용자가 안정적으로 크기가 적절한 환경에서 올바른 방향으로 생성되도록 다음 권장 사항을 염두에 두어야 합니다.

1. 사용자는 0,0,0에서 생성되므로 생성 위치를 원점 주위로 가운데에 배치합니다.
2. 전 세계에서 자산을 작성할 수 있도록 작업 단위를 미터로 설정해야 합니다.
3. Up 축은 "Y"로 설정해야 합니다.
4. 자산은 양의 Z 축을 "앞으로" 향해야 합니다.
5. 모든 메시를 결합할 필요는 없지만 리소스가 제한된 디바이스를 대상으로 하는 경우 권장됩니다.

### <a name="exporting-your-environment"></a>환경 내보내기

Windows Mixed Reality 환경의 자산 배달 형식으로 이진 glTF(.glb)를 사용합니다. glTF는 Khronos 그룹에서 유지 관리하는 3D 자산 배달을 위한 무료 개방형 표준입니다. glTF가 상호 운용 가능한 3D 콘텐츠에 대한 업계 표준으로 발전함에 따라 Windows 앱 및 환경의 형식에 대한 Microsoft의 지원이 증가할 것입니다.

사용자 지정 홈 환경으로 사용할 자산을 내보내는 첫 번째 단계는 glTF 2.0 모델을 생성하는 것입니다. glTF 작업 그룹은 [지원되는 내보내기 및 변환기 목록을](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) 유지 관리하여 glTF 2.0 모델을 만듭니다. 시작하려면 이 페이지에 나열된 프로그램 중 하나를 사용하여 glTF 2.0 모델을 만들고 내보내거나 지원되는 변환기 중 하나를 사용하여 기존 모델을 변환합니다.

<!-- Additionally, check out [this helpful article, which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.  -->

### <a name="environment-limits"></a>환경 제한

모든 환경은 < 256mbs여야 합니다. 256mbs보다 큰 환경은 로드에 실패하고 사용자를 둘러싼 기본 skybox만 있는 빈 세계로 되돌아가게 됩니다. 모델을 만들 때 이 파일 크기 제한을 염두에 두어야 합니다. 또한 아래 설명된 대로 WindowsMRAssetConverter를 사용하여 환경을 최적화하려는 경우 최적화에서 파일 크기가 더 크지만 로드 속도가 빠른 질감을 만들 때 질감 크기가 증가한다는 것을 인식해야 합니다. 

### <a name="optimizing-your-environment"></a>환경 최적화

Windows Mixed Reality 환경 로드 시간을 크게 줄일 수 있는 많은 선택적 최적화를 지원합니다. 텍스처가 많은 환경에서는 로드하는 동안 시간이 부족할 수 있기 때문에 특히 주의해야 합니다. 일반적으로 모든 자산에 대해 이 단계를 권장하지만, 해상도가 적거나 낮은 텍스처가 있는 작은 환경에서는 이 단계가 항상 필요하지는 않습니다. 

이 프로세스를 더 쉽게 수행할 수 있도록 최적화를 수행하는 [Windows Mixed Reality Asset Converter(GitHub 사용 가능)를](https://github.com/Microsoft/glTF-Toolkit/releases) 만들었습니다. 이 도구는 Microsoft glTF 도구 키트에서 사용할 수 있는 유틸리티 집합을 사용하여 추가 질감 압축, 압축 및 해상도 다운 스케일링을 수행하여 표준 2.0 glTF 또는.glb를 최적화합니다. 

변환기는 현재 최적화의 정확한 동작을 조정하기 위해 여러 플래그를 지원합니다. 최상의 결과를 위해 다음 플래그를 실행하여 실행하는 것이 좋습니다.

플래그|권장 값|Description
---|---|---
-max-texture-size|1024 또는 2048| 질감의 품질을 향상시키기 위해 값을 조정합니다. 기본값은 512x512입니다. 값이 클수록 환경의 파일 크기에 상당한 영향을 주므로 256mb 제한을 염두에 두어야 합니다.
-min-version|1803|사용자 지정 환경은 windows >= 1803 버전에서만 지원됩니다. 이 플래그는 이전 버전의 질감을 제거하고 최종 자산의 파일 크기를 줄입니다.

예를 들어:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>환경 테스트

final.glb 환경이 준비되면 헤드셋에서 테스트할 준비가 된 것입니다. 사용자 지정 환경을 혼합 현실 홈 사용하려면 ["샘플 환경 시도"](#trying-a-sample-environment) 섹션의 2단계에서 시작합니다. 

## <a name="sending-feedback"></a>피드백 보내기

이 실험적 기능을 평가하는 동안 사용자 지정 환경을 사용하는 방법, 찾을 수 있는 버그 및 기능을 어떻게 좋아하는지 알아보는 데 관심이 있습니다. 개발자 포럼 에서 사용자 지정 홈 환경을 만들고 사용하기 위한 피드백을 [공유합니다.](https://forums.hololens.com/categories/custom-home-environments)

## <a name="troubleshooting-and-tips"></a>문제 해결 및 팁

### <a name="how-do-i-change-the-name-of-the-environment"></a>환경 이름을 변경할 어떻게 할까요? 있나요?

environments 폴더의 파일 이름은 장소 선택기에서 사용됩니다. 환경 이름을 변경하려면 환경 파일 이름을 바꾼 다음, Mixed Reality 포털 다시 시작합니다.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>내 장소 선택기에서 사용자 지정 환경을 제거할 어떻게 할까요? 있나요?

사용자 지정 환경을 제거하려면 PC( )에서 environments 폴더를 열고 `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState` 환경을 삭제합니다. Mixed Reality 포털 다시 시작하면 이 환경이 더 이상 장소 선택기에서 표시되지 않습니다. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>어떻게 할까요? 기본값은 사용자 지정 환경인가요?

현재 기본 환경은 변경할 수 없습니다. Mixed Reality 포털 다시 시작할 때마다 클리프 하우스 환경으로 돌아갑니다. 

### <a name="i-spawn-into-a-blank-space"></a>빈 공간에 생성됩니다.

Windows Mixed Reality [256mb를 초과하는 환경을 지원하지 않습니다.](#environment-limits) 환경이 이 제한을 초과하면 모델이 없는 빈 하늘 상자에 표시됩니다.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>내 환경을 로드하는 데 시간이 오래 걸립니다.

환경에 선택적 최적화를 추가하여 더 빠르게 로드할 수 있습니다. 자세한 내용은 ["환경 최적화"를 참조하세요.](#optimizing-your-environment)

### <a name="the-scale-of-my-environment-is-incorrect"></a>내 환경의 규모가 잘못되었습니다.

Windows Mixed Reality 환경을 로드할 때 glTF 단위를 1미터로 변환합니다. 환경이 예기치 않은 규모를 로드하는 경우 내보내기를 다시 확인하여 1미터 규모로 모델링하고 있는지 확인합니다. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>내 환경의 생성 위치가 잘못되었습니다.

기본 생성 위치는 환경에서 0,0,0에 있습니다. 현재 이 위치를 사용자 지정할 수 없으므로 원하는 생성 지점에 배치된 원본으로 환경을 내보내서 생성 지점을 수정해야 합니다.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>환경에서 오디오가 올바르지 않습니다.

사용자 지정 환경을 만들 때 만든 물리적 공간과 일치하지 않는 음향 렌더링 시뮬레이션을 사용하게 됩니다. 소리는 잘못된 방향에서 올 수 있으며, 소리가 섞일 수 있습니다. 

## <a name="see-also"></a>추가 정보
* [Windows Mixed Reality Asset Converter(GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)