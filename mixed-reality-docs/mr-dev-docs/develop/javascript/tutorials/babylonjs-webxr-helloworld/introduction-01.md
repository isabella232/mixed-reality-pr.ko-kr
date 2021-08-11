---
title: babylon.js 및 WebXR 자습서 소개
description: babylon.js를 사용하고 기본 Mixed Reality 애플리케이션을 만드는 방법을 알아보려면 이 과정을 완료하세요.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: mixed reality, javascript, 자습서, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, 몰입형 웹
ms.localizationpriority: high
ms.openlocfilehash: e2006e911ad9dae00252c929c7739ff2209f4bf7796f1c49e713cfaf53267cd2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196827"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a>자습서: babylon.js를 사용하여 첫 번째 WebXR 애플리케이션 만들기

이 자습서에서는 babylon.js 및 Visual Studio Code를 사용하여 기본 Mixed Reality 앱을 만드는 방법을 보여 줍니다. 빌드할 앱은 큐브를 렌더링하고, 다른 면을 뷰로 전환하고, 상호 작용을 추가하는 데 사용할 수 있습니다. 이 자습서에서는 다음과 같은 작업을 수행하는 방법을 살펴봅니다.

> [!div class="checklist"]
> * 개발 환경 설정
> * 기본 3D 요소를 만드는 babylon.js API  
> * 새 웹 페이지 만들기
> * 3D 요소와 상호 작용
> * Windows Mixed Reality 시뮬레이터에서 애플리케이션 실행

## <a name="prerequisites"></a>필수 조건

* WebXR 지원 브라우저(예: [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md))
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 이상
* [NodeJS](https://nodejs.org/)
* 선택 사항: Windows Mixed Reality 시뮬레이터를 사용하려는 경우 [Windows 10 크리에이터 업데이트](https://www.microsoft.com/software-download/windows10)
* 선택 사항: [Windows Mixed Reality 시뮬레이터](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="getting-started"></a>시작

이 프로젝트를 처음부터 만들려면 Visual Studio Code(VSCode) 프로젝트부터 시작합니다.

> [!NOTE]
> VSCode를 사용하는 것은 필수는 아니지만 자습서의 편의를 위해 사용할 예정입니다. 경험이 많은 JavaScript 개발자는 가장 간단한 메모장을 비롯하여 원하는 다른 편집기를 사용할 수 있습니다.

1. [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 단일 파일을 다운로드하거나 [공식 babylon.js 웹 사이트](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers)에서 찾을 수 있는 온라인 버전을 사용하세요. [GitHub](https://github.com/BabylonJS/Babylon.js)에서 전체 babylon.js 프로젝트를 복제할 수도 있습니다.
1. 빈 파일을 만들고 html 페이지로 저장합니다(예: index.html).
1. 기본 html 태그를 만들고 babylon.js javascript 파일을 참조합니다. 최종 코드는 다음과 같습니다.

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
        </head>
    <body>
    </body>
    </html>
    ```

1. body 안에 *canvas* HTML 요소를 추가하여 babylon.js의 콘텐츠를 렌더링합니다. canvas에는 나중에 JavaScript에서 이 HTML 요소에 액세스할 수 있는 id 특성이 있습니다.

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
    <body>
        <canvas id="renderCanvas"></canvas>
    </body>
    </html>
    ```

1. 캔버스가 전체 웹 페이지를 차지합니다. 이것으로 웹 페이지가 완성됩니다. 이제 웹 페이지가 준비되었습니다. 모든 브라우저에서 열 수 있으며, 아직 몰입형 환경이 없더라도 표시되는 오류가 없는지 확인할 수 있습니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [다음 자습서: 2. 장면 준비](prepare-scene-02.md)