---
title: Unreal에서 프로젝트 업그레이드
description: Unreal 프로젝트의 버전 업그레이드 단계 및 사용되지 않는 API에 대한 개요입니다.
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 개발, 설명서, 가이드, 기능, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 이식, 업그레이드
ms.openlocfilehash: 0ba10b8ee1067da4494f147d43f8834010e1250f
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609664"
---
# <a name="upgrading-projects-in-unreal"></a>Unreal에서 프로젝트 업그레이드

새 버전의 Unreal로 업데이트할 때 청사진을 컴파일하거나 프로젝트를 패키징하면 사용되지 않는 함수가 경고로 표시됩니다.  기존 함수를 대체하는 새 함수가 추가되면 기존 함수는 사용되지 않습니다. 

## <a name="426-upgrades"></a>4.26 업그레이드
 
4\.26에서는 공통 인터페이스를 추가하고 애플리케이션 코드 플랫폼의 제약을 받지 않도록 모든 AR 및 VR 플랫폼이 리팩터링되었기 때문에 평소보다 더 많은 경고가 표시될 수 있습니다.  프로젝트를 다른 플랫폼으로 보다 쉽게 이식할 수 있도록 새 API로 업데이트하는 것이 좋습니다.

더 이상 사용되지 않는 함수와 대신 사용되는 함수를 알려주는 경고 메시지가 표시됩니다.  사용되지 않는 모든 함수는 이 릴리스에서는 계속 작동하지만 이후 릴리스에서는 작동하지 않을 수 있습니다.  뿐만 아니라 사용되지 않는 함수는 청사진에서 함수를 검색할 때 더 이상 나열되지 않습니다.

![Create Named ARPin 함수의 청사진](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a>4.25 사용 중단

| 더 이상 사용되지 않는 함수 | 새 함수 |
| --- | --- |
| CreateNamedARPin | ![Pin Component 함수의 청사진](images/unreal-porting-img-02.png) |
| LoadWMRAnchorStoreARPins | ![Load ARPins from Local Store 함수의 청사진](images/unreal-porting-img-03.png) |
| LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins | ![Save ARPin to Local Store 함수의 청사진](images/unreal-porting-img-04.png) |
| RemoveARPinFromWMRAnchorStore | ![Remove ARPin from Local Store 함수의 청사진](images/unreal-porting-img-05.png) |
| SetEnabledMixedRealityCamera | ![Set Enabled XRCamera 함수의 청사진](images/unreal-porting-img-06.png) |
| ResizeMixedRealityCamera | ![Resize XRCamera 함수의 청사진](images/unreal-porting-img-07.png) |
| StartCameraCapture | ![카메라 캡처를 시작하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-08.png) |
| StopCameraCapture | ![카메라 캡처를 중지하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-09.png) |
| StartQRCodeCapture | ![QR 코드 캡처를 시작하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-10.png) |
| StopQRCodeCapture | ![QR 코드 캡처를 중지하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-11.png) |
| 4\.25에서는 공간 매핑이 자동으로 시작되었지만 4.26에서는 직접 전환해야 합니다. | ![공간 매핑을 사용하도록 설정하는 Toggle ARCapture 함수의 청사진](images/unreal-porting-img-12.png) |
| ShowKeyboard | 포커스가 텍스트 위젯으로 이동하면 키보드가 자동으로 표시되기 때문에 4.26에서 제거되었습니다. |
| HideKeyboard | 텍스트 위젯의 포커스가 다른 곳으로 이동하면 키보드가 자동으로 표시되기 때문에 4.26에서 제거되었습니다. |
| SupportsHandTracking | ![Supports Hand Tracking 속성의 청사진](images/unreal-porting-img-13.png) |
| IsDisplayOpaque | ![IsDisplayOpaque 속성의 청사진](images/unreal-porting-img-14.png) |
| GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus | ![Get Motion Controller Data 함수의 청사진](images/unreal-porting-img-15.png) |
| GetVersionString | ![Get Version String 함수의 청사진](images/unreal-porting-img-16.png) |
| IsTrackingAvailable | ![IsTrackingAvailable 속성의 청사진](images/unreal-porting-img-17.png) |
| IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed | Unreal의 입력 작업 시스템을 사용합니다. |
| SetFocusPointForFrame | 4\.26에서는 제거되었습니다.  이전에는 원격 접속 시 리프로젝션에 사용되었지만, 지금은 깊이 리프로젝션을 지원합니다. |