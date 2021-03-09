---
title: 프로젝트 변경 내용 권한 부여
description: HoloLens 및 VR 개발용 MR Feature Tool에서 프로젝트 변경 권한을 부여하는 방법을 알아봅니다.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 최신, 도구, 시작, 기본 사항, unity, visual studio, 도구 키트, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 설치, Windows, HoloLens, 에뮬레이터, unreal, openxr
ms.openlocfilehash: db7ae079e19c7739f57f0b9e4a375a3e6f9a3cdd
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230783"
---
# <a name="authorizing-project-changes"></a>프로젝트 변경 내용 권한 부여

Unity 프로젝트를 수정하기 전에 매니페스트 및 프로젝트 파일의 변경 내용에 대한 검토 및 승인을 받아야 합니다.

![권한 부여 요청](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a>file:///

제안된 매니페스트 변경 내용은 왼쪽의 **매니페스트** 열에서 볼 수 있습니다. 변경 내용은 프로젝트 매니페스트(**Packages/manifest.json**)에 정확히 기록됩니다.

![매니페스트 미리 보기](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a>프로젝트에 복사할 파일

오른쪽의 **프로젝트에 복사할 파일** 섹션에는 Unity 프로젝트에 복사될 특정 기능 패키지 파일이 나열됩니다.

![복사할 파일이 포함된 매니페스트 미리 보기](images/FilesToCopy.png)

## <a name="compare-manifests"></a>매니페스트 비교

**비교** 를 선택하면 제안된 모든 변경 내용을 나란히 놓고 자세히 비교할 수 있습니다.

![매니페스트 비교](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a>변경 내용 승인

제안된 변경 내용이 승인되면 나열된 파일이 Unity 프로젝트에 복사되고 매니페스트가 해당 파일의 참조로 업데이트됩니다.

> [!NOTE]
> 기능 패키지(*.tgz) 파일을 원본 제어에 추가해야 합니다. 이러한 파일은 개발 팀이 기능 및 매니페스트 변경 내용을 쉽게 공유할 수 있도록 상대 경로를 사용하여 참조됩니다.

 수정 작업 중 하나로 현재 **manifest.json** 파일이 백업됩니다.

> [!IMPORTANT]
> 매니페스트 백업을 볼 때 가장 오래된 백업을 **manifest.json.backup** 이라고 부릅니다. 최신 백업에는 0부터 시작하는 숫자 값이 주석으로 추가됩니다.

## <a name="going-back-to-the-previous-step"></a>이전 단계로 돌아가기

기능 선택을 변경해야 하는 경우 **돌아가기** 를 사용하여 [가져오기](importing-features.md) 단계로 돌아갑니다.

## <a name="see-also"></a>참조

- [Mixed Reality Feature Tool 시작](welcome-to-mr-feature-tool.md)
- [선택한 패키지 가져오기](importing-features.md)
