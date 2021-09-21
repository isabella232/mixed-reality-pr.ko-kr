---
title: Unity용 MRTK Figma Bridge
description: MRTK Figma Bridge for Unity를 사용하면 Figma Toolkit 레이아웃을 Unity로 가져올 수 있습니다.
author: dongpark
ms.author: dongpark
ms.date: 03/29/2021
ms.topic: article
keywords: Figma, Sketch, Adobe XD, 디자인, 디자이너, 디자인 파일, UX 디자인, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: d21caa796907ebc7ea1fb46ce940cf210e9fc49d
ms.sourcegitcommit: 9431e9d6d7e959954ab3e18ecc0e420a3583d1a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/21/2021
ms.locfileid: "128053861"
---
# <a name="mrtk-figma-bridge-for-unity-beta"></a>MRTK Figma Bridge for Unity(베타)

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWKiO4]

MRTK Figma Bridge for Unity를 사용하면 Figma Toolkit 레이아웃을 Unity로 가져올 수 있습니다. 브리지는 MRTK Figma Toolkit 만든 UI 레이아웃을 가져온 다음 적절한 위치와 크기로 해당 MRTK 프리팹을 인스턴스화할 수 있습니다. Figma Bridge는 디자이너와 개발자 간의 통합 프로세스 및 협업을 설계하는 데 도움이 됩니다.


HoloLens 2 스타일 UI 라이브러리가 있는 디자인 파일인 Figma Toolkit 대한 자세한 내용은 [MRTK Figma](figma-toolkit.md) Toolkit 페이지를 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
- Mixed Reality 개발에 필요한 소프트웨어용 [도구 설치를](/windows/mixed-reality/develop/install-the-tools) 참조하세요.
- Unity 2019 이상
- [MRTK-Unity 2.7.0 이상](/windows/mixed-reality/mrtk-unity/)

> [!IMPORTANT]
> **MRTK-Unity 2.7.0 이상 필요**
> 
> Figma Toolkit 및 Figma Bridge는 MRTK 2.7.0 프리팹을 기반으로 하며 MRTK 2.7.0 이상 버전이 필요합니다. 낮은 버전의 MRTK와 함께 사용하면 일부 구성 요소가 제대로 변환되지 않습니다.

## <a name="how-to-use-mrtk-figma-bridge"></a>MRTK Figma Bridge를 사용하는 방법

### <a name="1-installation"></a>1. 설치

Figma Unity Bridge는 [Mixed Reality 기능 도구를](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)통해 설치할 수 있습니다. Mixed Reality 기능 도구를 다운로드하고 실행합니다.

**기능 검색** 페이지의 **Mixed Reality Toolkit** 섹션에서 **MRTK Figma Unity Bridge를** 선택합니다. 단계에 따라 MR Feature Tool을 완료하고 Unity 프로젝트로 돌아갑니다. Unity는 MRTK Figma Bridge용 패키지를 가져옵니다.

### <a name="2-open-figma-bridge-window"></a>2. Figma Bridge 창 열기

가져오기 프로세스가 완료되면 Figma 브리지 Mixed Reality > Toolkit > 메뉴 아래에서 **Figma Bridge를** 찾을 수 있습니다.

<img src="images/FigmaToolkit/FigmaBridge_Menu.png" width="500px" alt="Figma Bridge - Menu"><br>

### <a name="3-generate-and-enter-your-figma-token"></a>3. Figma 토큰 생성 및 입력

Figma 웹 사이트의 왼쪽 위 모서리에서 Figma 메뉴를 클릭하고 계정 설정에 > 도움말 및 계정을 엽니다. '개인용 액세스 토큰' 섹션에서 새 개인용 액세스 토큰을 생성합니다.

<img src="images/FigmaToolkit/FigmaToolkit_Token.png" width="500px" alt="Figma Bridge - Get Token"><br>

<img src="images/FigmaToolkit/FigmaBridge_Token.png" width="500px" alt="Figma Bridge - Enter Token"><br>


### <a name="4-enter-id-for-a-figma-document"></a>4. Figma 문서의 ID 입력
각 Figma 문서에는 URL에 고유한 ID가 있습니다. 이 ID를 복사하여 Figma Bridge에 붙여넣습니다.

<img src="images/FigmaToolkit/FigmaToolkit_DocID.png" alt="Figma Bridge - Doc ID"><br>

**파일 다운로드를 클릭하여** Figma 파일을 다운로드합니다. 새 ID를 입력하여 다른 Figma 파일을 다운로드할 수 있습니다.

**파일 로드를** 클릭하여 Figma 파일을 엽니다.

<img src="images/FigmaToolkit/FigmaBridge_Files.png" width="500px" alt="Figma Bridge - Files"><br>

### <a name="5-build-a-page"></a>5. 페이지 빌드

Figma Bridge는 Figma 파일의 페이지 목록을 표시합니다. Unity에서 빌드하려는 페이지를 확인합니다. **페이지 빌드** 단추를 클릭합니다.

<img src="images/FigmaToolkit/FigmaBridge_Pages.png" width="500px" alt="Figma Bridge - Pages"><br>

<img src="images/FigmaToolkit/FigmaBridge_Result.png" alt="Figma Bridge - Result"><br>

### <a name="6-refresh-a-document-for-changes"></a>6. 변경 내용에 대한 문서 새로 고침

웹(또는 데스크톱 편집기 사용)에서 Figma 파일을 수정하고 **새로 고침을** 클릭하여 변경 내용을 검색할 수 있습니다. **빌드 페이지를** 클릭하여 업데이트로 빌드합니다. 이러한 방식으로 Figma에서 디자인을 쉽게 반복하고 Unity에서 볼 수 있습니다.



## <a name="see-also"></a>참고 항목
* [Figma 도구 키트](figma-toolkit.md)
* [커서](cursors.md)
* [손 광선](point-and-commit.md)
* [Button](button.md)
* [상호 작용 가능한 개체](interactable-object.md)
* [경계 상자 및 앱 바](app-bar-and-bounding-box.md)
* [조작](direct-manipulation.md)
* [손 메뉴](hand-menu.md)
* [Near 메뉴](near-menu.md)
* [개체 컬렉션](object-collection.md)
* [음성 명령](voice-input.md)
* [키보드](keyboard.md)
* [Tooltip](tooltip.md)
* [슬레이트](slate.md)
* [슬라이더](slider.md)
* [셰이더](shader.md)
* [빌보딩 및 태그얼롱](billboarding-and-tag-along.md)
* [진행률 표시](progress.md)
* [표면 자성](surface-magnetism.md)
