---
title: 관람자 보기
description: 외부 디바이스에서 홀로그램을 시각화하여 외부 디스플레이에 혼합 현실 환경을 표시하거나 기록합니다.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 관람자 보기, iPhone, iOS, iPad, OpenCV, 카메라, ARKit, HoloLens, Mixed Reality, Mixed Reality Toolkit, 데모, 레코드
ms.openlocfilehash: f30c745154056cda6b5ccf052efbbd0bb7f094ea
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779467"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>HoloLens 및 HoloLens 2의 관람자 보기

> [!WARNING]
> Microsoft는 Spectator View 샘플이 사용하는 Azure Spatial Anchors SDK 패키지 버전과의 비호환성으로 인해 이 샘플의 사용을 중단할 예정입니다. 또한 고객이 지원되는 2019 LTS 빌드로 이전함에 따라 Unity 환경에 다른 변경 사항이 적용되면서 이 샘플의 작동이 중단될 수 있습니다.
>
> Microsoft는 현재 위의 문제를 해결하기 위해 리소스를 투자하고 있지는 않지만 샘플에서 Azure Spatial Anchors 기능을 제거하고 QR 코드 같은 기술을 정렬에 사용할 수 있습니다.   Microsoft는 당분간 커뮤니티 구성원이 이러한 문제를 해결하기 위한 PR을 제출할 경우 해당 PR을 검토하고 수락할 것입니다.

![표식](images/SpecViewPhoneHero.jpg)

HoloLens를 쓰고 있을 때는 HoloLens를 쓰고 있지 않은 다른 사람이 자신이 보는 것과 똑같은 경이로움을 경험할 수 없다는 사실을 잊기 쉽습니다. Spectator View를 사용하면 HoloLens 사용자가 보고 있는 것을 다른 사람도 2D 화면으로 볼 수 있습니다. 또한 모바일 디바이스를 사용하여 홀로그램을 HD로 녹화하고 비디오 카메라를 사용하여 홀로그램을 고화질로 녹화하는 것도 빠르고 경제적인 접근법입니다.

## <a name="key-resources"></a>주요 리소스

* [**GitHub의 관람자 보기**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**관람자 보기 설명서**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**관람자 보기 샘플**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>사용 사례

* iPhone 또는 Android 디바이스를 사용하여 혼합 현실 환경을 녹화할 수 있습니다. Full HD로 녹화하고 홀로그램과 그림자에 앤티앨리어싱을 적용하면 홀로그램 동영상을 경제적이고 빠르게 녹화할 수 있습니다.
* 라이브 혼합 현실 환경을 지연 없이 iPhone 또는 iPad에서 Apple TV로 직접 스트림합니다!
* 게스트와 경험을 공유합니다. 비 HoloLens 사용자가 휴대폰 또는 태블릿에서 홀로그램을 직접 경험할 수 있도록 합니다.

## <a name="current-features"></a>현재 기능

* 홀로그램의 공간 동기화를 통해 모든 사용자가 똑같은 장소에서 홀로그램을 볼 수 있습니다.
* iOS(ARKit 사용 디바이스) 및 Android(ARCore 사용 디바이스)를 지원합니다.
여러 iOS 게스트가 사용할 수 있습니다.
비디오 + 홀로그램 + 주변 소리 + 홀로그램 소리를 녹화합니다.
비디오를 저장하거나, 이메일로 보내거나, 다른 지원 앱과 공유할 수 있도록 시트를 공유합니다.

![표식](images/SpecViewPhoneDemo.jpg)
![표식](images/hololensspectatorview-500px.jpg) ![표식](images/spectatorview-300px.png)

다음 표에는 다양한 관람자 보기 기능 및 해당 특성이 나와 있습니다. 비디오 녹화 요구 사항에 가장 적합한 옵션을 선택하세요.

|      기능                                | 모바일                  |                    비디오 카메라              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 품질                           |         Full HD         |        전문 품질 촬영(비디오 카메라)      |
| 간편한 카메라 이동                 |            ✔            |                      ✔                      |
| 3인칭 보기                    |            ✔            |                      ✔                      |
| 화면으로 스트리밍 가능           |            ✔            |                      ✔                      |
| 이식 가능                             |            ✔            |                                             |
| 무선                             |            ✔            |                                             |
| 추가 필수 하드웨어         |     Android 휴대폰, iPhone    | HoloLens + 의장품 + 삼각대 + 비디오 카메라 + PC + Unity |
| 하드웨어 투자                  |           낮음            |                     높음                    |
| 플랫폼 간                       |           Android, iOS   |                                             |
| 동기화된 콘텐츠                 |            ✔            |                      ✔                      |
| 런타임 설치 기간               |         인스턴트          |                     느림                    |
## <a name="see-also"></a>참조

* [혼합 현실 캡처](/hololens/holographic-photos-and-videos) 
* [개발자를 위한 혼합 현실 캡처](mixed-reality-capture-for-developers.md)
* [혼합 현실의 공유 환경](shared-experiences-in-mixed-reality.md)