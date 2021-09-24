---
title: BabylonJS를 사용하여 WebXR에서 피아노 빌드
description: BabylonJS를 사용하여 WebXR에서 작동하는 88키 피아노 키보드를 빌드하는 방법을 알아보려면 이 자습서 시리즈를 완료하세요.
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: mixed reality, javascript, 자습서, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, 몰입형 웹
ms.localizationpriority: high
ms.openlocfilehash: 93a3896b081e736bb62bceb6c8ae609685d7c5b5
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932495"
---
# <a name="tutorial-build-a-piano-in-webxr-using-babylonjs"></a>자습서: Babylon.js를 사용하여 WebXR에서 피아노 빌드

피아노를 실제로 제작하려면 시간, 기술, 재료 등이 많이 필요합니다. VR/AR 세계에서 제작하는 건 어떨까요?

이 자습서 시리즈에서는 Babylon.js를 사용하여 가상 세계에서 작동하는 88키 스탠드업 피아노가 포함된 Mixed Reality 웹앱을 만드는 방법을 알아봅니다. 완성된 앱에서 피아노로 텔레포트하고 Mixed Reality 컨트롤러를 사용하여 건반을 연주할 수 있습니다.

이 자습서 시리즈에서는 다음을 수행하는 방법에 대해 알아봅니다.

> [!div class="checklist"]
> * 메시를 생성, 배치 및 병합하여 피아노 키보드 빌드
> * 스탠드업 피아노 프레임의 Babylon.js 모델 가져오기
> * 각 피아노 건반에 포인터 상호 작용 추가
> * WebXR에서 텔레포트 및 멀티 포인터 지원 활성화

## <a name="prerequisites"></a>필수 구성 요소

* 인터넷에 연결된 컴퓨터
* JavaScript 기본 지식
* [WebXR Javascript Hello World 자습서](../babylonjs-webxr-helloworld/introduction-01.md)
* WebXR 지원 브라우저(예: [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md))
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 이상
* [VR 헤드셋](../../../../discover/immersive-headset-hardware-details.md) 또는 [Windows Mixed Reality 시뮬레이터](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)
* 선택 사항: Windows Mixed Reality 시뮬레이터를 사용하려는 경우 [Windows 10 크리에이터 업데이트](https://www.microsoft.com/software-download/windows10)

## <a name="getting-started"></a>시작

Babylon.js 장면이 포함될 HTML 웹 페이지를 설정하는 것부터 시작하겠습니다.

1. *babylonjs-piano-tutorial* 이라는 폴더를 만들고 Visual Studio Code에서 해당 폴더를 엽니다.

    > [!NOTE]
    > 원하는 코드 편집기를 사용하여 이 자습서를 진행할 수 있지만 편의를 위해 이 자습서 전체에서 Visual Studio Code를 사용하겠습니다.

1. 이 폴더 내에 *index.html* 이라는 파일을 만들고 아래 템플릿을 파일에 삽입합니다.

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas"); 
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
        
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

    이 템플릿의 콘텐츠에 대한 자세한 설명이 필요한 경우 이 자습서의 필수 구성 요소인 [Hello World 자습서](../babylonjs-webxr-helloworld/introduction-01.md)를 참조하세요.

1. 브라우저에서 이 파일을 열려고 하면 콘솔에서 `createScene()` 함수를 찾을 수 없다는 오류를 표시합니다. 다음 섹션에서 `createScene()` 함수를 구현하여 이 오류를 해결해 보겠습니다.

## <a name="setup-the-scene"></a>장면 설정

1. *index.html* 과 같은 폴더에 *scene.js* 라는 또 다른 파일을 만듭니다. 장면 설정 및 피아노 만들기와 관련된 모든 javascript 코드를 이 파일에 저장할 것입니다.

1. *scene.js* 에 `createScene()` 함수를 추가해 보겠습니다.

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        return scene;
    }
    ```

    `createScene()`을 비동기 함수로 만들고 있습니다. 이유를 알고 싶다면 계속 진행하세요.

1. 다음으로, 장면을 볼 수 있도록 조명 및 카메라가 필요합니다. `createScene()` 함수를 업데이트합니다.

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);

        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;

        return scene;
    }
    ```

    여기서는 거의 완전히 아래쪽을 가리키고 공간의 원점을 대상으로 하는 [ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera)를 만들었습니다. 여기서 만든 조명은 하늘을 가리키는 [HemisphericLight](https://doc.babylonjs.com/divingDeeper/lights/lights_introduction#the-hemispheric-light)이며 주변 공간을 시뮬레이션하는 데 유용합니다. 또한 조명 강도를 낮춰 조명을 약간 희미하게 만들었습니다.

    카메라 및 조명을 만드는 방법이 잘 생각나지 않는다면 다음 단계를 진행하기 전에 [Hello World 자습서 시리즈의 장면 준비 섹션](../babylonjs-webxr-helloworld/prepare-scene-02.md#add-a-camera)을 다시 참조하세요.

1. 마지막으로, WebXR 플랫폼용으로 개발 중이므로 `return scene;` 앞에 다음 줄을 삽입하여 장면에 [XR 환경을 활성화](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR)해야 합니다.

    ```javascript
    const xrHelper = await scene.createDefaultXRExperienceAsync();
    ```

    Javascript에서 특정 함수 내부에 있는 `async` 함수에서 `await` 키보드를 사용하려면 부모 함수도 `async`여야 합니다. 그래서 이전에 `createScene` 함수를 비동기로 정의한 것입니다. 이 자습서 시리즈의 뒷부분에서는 이 `xrHelper`를 사용하여 Babylon.js에서 지원하는 다양한 WebXR 기능을 활성화하고 구성합니다.

1. 완성된 *scene.js* 는 다음과 같습니다.

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        
        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. 이제 `createScene()` 함수가 작동하므로 *index.html* 에서 `createScene()` 함수를 인식할 수 있도록 *index.html* 이 *scene.js* 파일을 스크립트로 로드하도록 하겠습니다. html 파일의 `<header>` 섹션 내에 다음 코드 줄을 추가합니다.

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <script src="scene.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas");
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
                
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

1. 브라우저에서 *index.html* 을 열면 앞서 살펴본 오류 메시지가 더 이상 표시되지 않고 해당 페이지에 빈 Babylon.js 장면이 표시됩니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [다음 자습서: 3D 피아노 모델 빌드](keyboard-model-02.md)
