---
title: Unity의 HP 반향 G2 컨트롤러
description: SteamVR 및 Windows Mixed Reality에서 HP 반향 G2 컨트롤러를 사용 하는 방법에 대 한 지침입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, 반향, 반향 G2, HP 반향 G2, 혼합 현실, 개발, 동작 컨트롤러, 사용자 입력, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 기능, holograms, 게임 개발
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638390"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Unity의 HP 반향 G2 컨트롤러

## <a name="getting-started"></a>시작

SteamVR 용으로 개발 중이거나 Windows Mixed Reality 입력 API (XR)를 사용 하는 경우 HP 반향 G2 컨트롤러를 사용 하는 데 필요한 추가 설치는 없습니다. WSA. 입력). 그러나 SteamVR을 사용 하지 않는 한, A, B, X, Y 단추 및는 현재 입력 관리자를 통해 액세스할 수 없습니다. 추가 반향 G2 입력에 대 한 지원은 가까운 장래에 제공 될 예정 이므로 다시 확인 하세요.

## <a name="porting-existing-applications"></a>기존 응용 프로그램 포팅

Windows Mixed Reality 모던 헤드셋에 대해 개발 중인 기존 앱이 이미 있는 경우에는 [이식 가이드](../porting-apps/porting-guides.md) 및 [프로젝트 설정](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) 섹션에서 일반적인 제안을 확인 하세요.

## <a name="mapping-input"></a>매핑 입력

새 컨트롤러에 대 한 입력 매핑 및 실행 준비가 완료 되 면 몰입 형 포팅 가이드의 [입력 매핑](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) 섹션에서 시작 합니다. Unity에서 입력을 구성 하는 방법에 대 한 지침은 참조를 위한 전체 [단추 및 축 매핑 표와](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) 함께 [제스처 및 동작 컨트롤러](gestures-and-motion-controllers-in-unity.md)에 자세히 설명 되어 있습니다.

## <a name="see-also"></a>참고 항목
* [SteamVR용 업데이트](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)