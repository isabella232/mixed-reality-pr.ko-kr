---
title: 기본 3D 개체로 장면을 준비하는 Babylon.js 자습서
description: babylon.js를 사용하고 장면에 기본 3D 개체를 추가하는 방법을 알아봅니다.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: mixed reality, javascript, 자습서, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, 몰입형 웹
ms.localizationpriority: high
ms.openlocfilehash: 9d74104924aa859f5ab18248a487a7e80392809adb09361e84c5ad386f1321c4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212394"
---
# <a name="tutorial-prepare-a-scene"></a>자습서: 장면 준비

장면을 준비하고 몇 가지 기본 3D 요소를 추가하는 방법을 알아봅니다.

이 자습서에서는 다음 방법을 알아봅니다.

> [!div class="checklist"]
> * 장면 만들기
> * 카메라 추가
> * 광원 추가
> * 기본 3D 요소 추가

## <a name="before-you-begin"></a>시작하기 전에

이전 자습서 단계에서는 기본 웹 페이지를 만들었습니다. 편집할 웹 페이지를 엽니다.

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

## <a name="create-a-scene"></a>장면 만들기

장면에는 모든 콘텐츠가 표시됩니다. 여러 장면이 있을 수 있으며, 장면을 전환할 수 있습니다. [babylon.js 장면](https://doc.babylonjs.com/divingDeeper/scene)에 대해 자세히 알아봅니다.

1. canvas html 요소 뒤에 스크립트 태그를 추가하고 다음 코드를 추가하여 검은색으로 채워진 장면을 만듭니다.

    ```html
    <script type="text/javascript">
        const canvas = document.getElementById("renderCanvas");
        const engine = new BABYLON.Engine(canvas, true);
        
        const createScene = function() {
            const scene = new BABYLON.Scene(engine);
            scene.clearColor = new BABYLON.Color3.Black;
            return scene;
        }

        const sceneToRender = createScene();
    </script>
    ```

    위의 코드에서는 장면을 렌더링하고 캔버스에 이벤트를 후크하는 babylon.js 웹 렌더링 엔진의 인스턴스를 만들어야 합니다. 엔진에 대한 자세한 내용은 문서 페이지 [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)을 확인하세요.

1. 장면은 기본적으로 렌더링되지 않습니다. 여러 장면이 있을 수 있으며 표시되는 장면을 제어할 수 있습니다. 모든 프레임에서 장면을 반복적으로 렌더링하려면 *createScene* 함수를 호출한 후 다음 코드를 실행합니다.

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a>기본 3D 요소 추가

1. 첫 번째 3D 셰이프를 추가해 보겠습니다. 3D 가상 세계에서 셰이프는 *메시* 로 만들어지며, 많은 삼각형 패싯이 함께 결합되어 있으며 각 패싯은 세 개의 정점으로 만들어집니다. 미리 정의된 메시를 사용하거나 고유한 사용자 지정 메시를 만들 수 있습니다. 여기서는 미리 정의된 상자 메시(예: 큐브)를 사용합니다. 상자를 만들려면 [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box)를 사용합니다. 매개 변수는 이름, 옵션(메시의 유형에 따라 달라지는 옵션)입니다. *createScene* 함수에 다음 코드를 추가합니다.

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. Microsoft Edge 브라우저에서 웹 페이지를 열고 출력을 확인합니다. 브라우저 창에 빈 페이지가 표시됩니다. 키보드를 사용하여 DevTools를 열고 F12 또는 Control+Shift+I(Windows, Linux) 또는 Command+Option+I(macOS)를 선택합니다. *콘솔* 탭을 연 후 오류 찾기를 시작할 수 있습니다. 'Catch되지 않은 오류: 카메라가 정의되지 않음' 오류가 표시됩니다. 이제 장면에 카메라를 추가해야 합니다.

## <a name="add-a-camera"></a>카메라 추가

1. 가상 세계를 보고 상호 작용하려면 카메라를 캔버스에 연결해야 합니다. 대상을 중심으로 회전할 수 있는 [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) 유형의 카메라를 추가해 보겠습니다. 카메라 인스턴스를 만드는 데 필요한 매개 변수는 다음과 같습니다.
    1. **name**: 카메라 이름
    1. **alpha**: 세로 축을 따른 각도 위치(라디안)
    1. **beta**: 가로 축을 따른 각도 위치(라디안)
    1. **radius**: 대상으로부터의 거리
    1. **target**: 카메라가 항상 향하는 지점(x-y-z 좌표로 정의됨)
    1. **scene**: 카메라가 있는 장면

    Alpha, beta, radius, target은 아래 다이어그램에 표시된 것과 같이 공간에서 카메라의 위치를 정의합니다.

    ![카메라 알파 베타 반경](../images/camera-alpha-beta-radius.jpg)

    *createScene* 함수에 다음 코드를 추가합니다.

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. 브라우저에서 출력을 확인하는 경우 검은색 캔버스가 표시됩니다. 광원이 누락되었습니다.

## <a name="add-light"></a>광원 추가

1. 다양한 조명 속성과 함께 사용할 수 있는 광원에는 포인트, 방향, 스폿 및 반구 광원의 네 가지 유형이 있습니다. 다음과 같이 주변 광원 [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight)를 추가해 보겠습니다.

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. 웹 페이지의 최종 코드는 다음과 같습니다.

    ```html
    <html>
    <head>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    <body>
        <canvas id="renderCanvas"></canvas>
        <script>
            const canvas = document.getElementById("renderCanvas");
            const engine = new BABYLON.Engine(canvas, true);
            
            const createScene = function() {
                const scene = new BABYLON.Scene(engine);
                scene.clearColor = new BABYLON.Color3.Black;
                
                const alpha =  Math.PI/4;
                const beta = Math.PI/3;
                const radius = 8;
                const target = new BABYLON.Vector3(0, 0, 0);
                
                const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;
                
                return scene;
            };
            
            const sceneToRender = createScene();
            engine.runRenderLoop(function(){
                sceneToRender.render();
            });
        </script>
    </body>
    </html>
    ```

1. 브라우저의 출력을 확인합니다. 큐브를 표시하고 마우스를 사용하여 큐브 주위에서 카메라를 회전하고 큐브의 다른 면을 볼 수 있습니다.

![큐브가 있는 기본 장면](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [다음 자습서: 3. 3D 개체와 상호 작용](interact-03.md)
