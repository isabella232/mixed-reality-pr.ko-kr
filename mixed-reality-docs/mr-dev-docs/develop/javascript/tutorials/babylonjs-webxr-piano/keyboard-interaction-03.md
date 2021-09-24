---
title: 3D 피아노 연주
description: Babylon.js를 사용하여 가상 피아노에 상호 작용을 추가하는 방법 알아보기
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: mixed reality, javascript, 자습서, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, 몰입형 웹
ms.localizationpriority: high
ms.openlocfilehash: 8f995d618398fef56ce42d6c3e9863256627bf75
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932427"
---
# <a name="tutorial-play-the-3d-piano"></a>자습서: 3D 피아노 연주

이전 자습서에서는 풀 사이즈 88키 피아노 키보드 모델을 성공적으로 만들었습니다. 이제 XR 공간에서 연주할 수 있게 만들어 보겠습니다.

이 자습서에서는 다음 작업 방법을 배웁니다.

> [!div class="checklist"]
> * 포인터 이벤트를 사용하여 대화형 피아노 기능 추가
> * 다른 크기로 메시 스케일링
> * XR에서 텔레포트 및 멀티 포인터 지원 활성화

## <a name="before-you-begin"></a>시작하기 전에

[이 시리즈의 이전 자습서](keyboard-model-02.md)를 완료했고 코드에 계속 추가할 준비가 되었는지 확인합니다.

*index.html*

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

*scene.js*

```javascript
const buildKey = function (scene, parent, props) {
    if (props.type === "white") {
        /*
        Props for building a white key should contain: 
        note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX

        As an example, the props for building the middle C white key would be
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
        */

        // Create bottom part
        const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);

        // Create top part
        const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
        top.position.z =  4.75;
        top.position.x += props.topPositionX;

        // Merge bottom and top parts
        // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
        const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.name = props.note + props.register;
        key.parent = parent;

        return key;
    }
    else if (props.type === "black") {
        /*
        Props for building a black key should contain: 
        note, wholePositionX, register, referencePositionX

        As an example, the props for building the C#4 black key would be
        {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
        */

        // Create black color material
        const blackMat = new BABYLON.StandardMaterial("black");
        blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

        // Create black key
        const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
        key.position.z += 4.75;
        key.position.y += 0.25;
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.material = blackMat;
        key.parent = parent;

        return key;
    }
}

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

    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }

    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});

    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });

    // Lift the piano keyboard
    keyboard.position.y += 80;

    const xrHelper = await scene.createDefaultXRExperienceAsync();

    return scene;
}
```

## <a name="making-the-piano-keyboard-playable"></a>피아노 키보드를 연주할 수 있게 만들기

현재 우리가 만든 피아노 키보드는 사용자 상호 작용에 응답하지 않는 정적 모델입니다. 이 섹션에서는 누군가 건반을 누르면 건반이 아래쪽으로 이동하고 소리를 내도록 건반을 프로그래밍합니다.

1. Babylon.js는 상호 작용할 수 있는 다양한 종류의 이벤트 또는 [관찰 가능 개체](https://doc.babylonjs.com/divingDeeper/events/observables)를 제공합니다. 여기서는 누군가 마우스 클릭, 터치, XR 컨트롤러 단추 클릭 등 포인터를 통해 건반을 누를 때 작업을 수행하도록 건반을 프로그래밍하려고 하므로 `onPointerObservable`을 사용합니다.

    `onPointerObservable`에 동작을 추가하는 방법의 기본 구조는 다음과 같습니다.

    ```javascript
    scene.onPointerObservable.add((pointerInfo) => {
        // do something
    });
    ```

1. Babylon.js는 다양한 유형의 [포인터 이벤트를](https://doc.babylonjs.com/typedoc/classes/babylon.pointereventtypes) 제공하지만 여기서는 아래 구조를 통해 `POINTERDOWN` 및 `POINTERUP` 이벤트만 사용하여 피아노 건반의 동작을 프로그래밍합니다.

    ```javascript
    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                // When the pointer is down on a piano key,
                // move the piano key downward (to show that it is pressed)
                // and play the sound of the note
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                // When the pointer is released,
                // move the piano key upward to its original position
                // and stop the sound of the note of the key that is released
                break;
        }
    });
    ```

1. 먼저 건반을 눌렀다 놓을 때 피아노 건반을 아래쪽과 위쪽으로 이동하도록 하는 작업을 수행하도록 하겠습니다.

    포인터 아래로 이벤트 시에는 클릭 중인 메시를 감지하고 피아노 건반인지 확인한 후 메시의 y 좌표를 음수로 변경하여 건반이 눌린 것처럼 보이게 해야 합니다.

    포인터 업 이벤트의 경우에는 포인터가 건반을 누른 다음, 놓지 않을 수 있으므로 좀 더 복잡합니다. 예를 들어 누군가가 C4 건반을 클릭하고, 마우스를 E4로 끌어다 놓은 후, 클릭을 해제할 수 있습니다. 이 경우에도 `pointerUp` 이벤트가 발생한 위치(E4) 대신 눌린 건반(C4)을 해제하는 것이 좋습니다.

    다음 코드로 원하는 결과를 달성하는 방법을 살펴보겠습니다.

    ```javascript
    const pointerToKey = new Map();
    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                if(pointerInfo.pickInfo.hit) {
                    const pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    const pointerId = pointerInfo.event.pointerId;
                    if (pickedMesh.parent === keyboard) {
                        pickedMesh.position.y -= 0.5;
                        // play the sound of the note
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                const pointerId = pointerInfo.event.pointerId;
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5;
                    // stop the sound of the note of the key that is released
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });
    ```

    `pointerId`는 모든 포인터에 고유하며 여러 컨트롤러가 있거나 터치 스크린을 사용하는 경우 포인터를 식별하는 데 도움이 될 수 있습니다. 여기서는 포인터가 해제될 때 해제 발생 위치에 관계없이 해제할 건반을 알 수 있도록 어떤 포인터가 어떤 건반에 눌러졌는지를 보여주는 관계를 저장하기 위해 `pointerToKey`라는 `Map` 개체를 초기화했습니다.

1. 위의 코드로 상호 작용하는 모습은 다음과 같습니다.

    ![대화형 피아노 건반](./images/interactive-piano-keys.gif)

1. 이제 건반을 누르면 소리를 내고 건반에서 포인터를 떼면 소리를 멈추는 작업을 수행해 보겠습니다. 이를 위해 선택한 악기의 MIDI 사운드를 쉽게 재생할 수 있게 해주는 **soundfont-player** 라는 Javascript 라이브러리를 활용할 것입니다.

    [라이브러리의 축소된 코드를 다운로드하고](./files/soundfont-player.min.js), *index.html* 같은 폴더에 저장하고, *index.html* 의 `<header>` 태그에 포함합니다.

    ```html
    <head>
        <title>Babylon Template</title>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <script src="scene.js"></script>
        <script src="soundfont-player.min.js"></script>
        <style>
                body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    ```

    라이브러리를 가져온 후 라이브러리를 사용하여 악기를 초기화하고 MIDI 사운드를 재생/중지하는 방법은 다음과 같습니다.

    ```javascript
    const pianoSound = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');
    const C4 = piano.play("C4"); // Play note C4
    C4.stop(); // Stop note C4
    ```

1. 이제 이를 포인터 이벤트에 통합하고 이 섹션의 코드를 마무리하겠습니다.

    ```javascript
    const pointerToKey = new Map()
    const piano = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');

    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                if(pointerInfo.pickInfo.hit) {
                    let pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    let pointerId = pointerInfo.event.pointerId;
                    if (keys.has(pickedMesh)) {
                        pickedMesh.position.y -= 0.5; // Move the key downward
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh,
                            note: pianoSound.play(pointerInfo.pickInfo.pickedMesh.name) // Play the sound of the note
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                let pointerId = pointerInfo.event.pointerId;
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5; // Move the key upward
                    pointerToKey.get(pointerId).note.stop(); // Stop the sound of the note
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });
    ```

    각 건반의 메시 이름을 해당 건반이 나타내는 음으로 지정했으므로 메시의 이름을 `pianoSound.play()` 함수에 전달하여 재생할 음을 쉽게 나타낼 수 있습니다. 또한 건반을 놓을 때 중지할 사운드를 알 수 있도록 해당 사운드를 `pointerToKey` 맵에 저장합니다.

## <a name="scaling-the-piano-for-immersive-vr-mode"></a>몰입형 VR 모드에서 피아노 스케일링

지금쯤이면 대화형 기능이 추가되었으므로 마우스(또는 터치 스크린)를 사용하여 피아노를 이미 연주해 보았을 것입니다. 이 섹션에서는 몰입형 VR 공간으로 이동합니다.

1. 몰입형 VR 헤드셋에서 페이지를 열려면 먼저 헤드셋을 개발자 머신에 연결하고 [Windows Mixed Reality 앱에서 사용하도록 설정](/enthusiast-guide/set-up-windows-mixed-reality)되어 있는지 확인해야 합니다. Windows Mixed Reality 시뮬레이터를 사용하는 경우 [해당 시뮬레이터가 사용하도록 설정](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)되어 있는지 확인합니다.

1. 이제 웹 페이지의 오른쪽 하단에 몰입형 VR 단추가 표시됩니다. 이 단추를 클릭하면 연결된 XR 디바이스에서 피아노를 볼 수 있습니다.

    ![몰입형 VR 단추](../images/immersive-vr-button.png)

1. 가상 공간에 있으면 우리가 빌드한 피아노가 매우 크다는 것을 알 수 있습니다. VR 세계에서는 피아노 아래쪽에 서서 멀리 있는 건반을 포인터로 가리켜서 연주할 수만 있습니다.

    ![거대한 피아노](./images/huge-piano.jpg)

1. 실제 세계의 일반적인 스탠드업 피아노와 비슷한 크기로 피아노를 축소해 보겠습니다. 이렇게 하려면 [공간의 점을 기준으로 메시를 스케일링](https://doc.babylonjs.com/toolsAndResources/utilities/Pivot#enlargement)할 수 있게 해주는 유틸리티 함수를 사용해야 합니다. 이 함수를 *scene.js* 에 추가합니다(`createScene()` 외부).

    ```javascript
    const scaleFromPivot = function(transformNode, pivotPoint, scale) {
        const _sx = scale / transformNode.scaling.x;
        const _sy = scale / transformNode.scaling.y;
        const _sz = scale / transformNode.scaling.z;
        transformNode.scaling = new BABYLON.Vector3(_sx, _sy, _sz); 
        transformNode.position = new BABYLON.Vector3(pivotPoint.x + _sx * (transformNode.position.x - pivotPoint.x), pivotPoint.y + _sy * (transformNode.position.y - pivotPoint.y), pivotPoint.z + _sz * (transformNode.position.z - pivotPoint.z));
    }
    ```

    이 함수는 3개의 매개 변수를 사용합니다.
    * **transformNode**: 스케일링할 `TransformNode`
    * **pivotPoint**: 스케일링의 기준이 될 점을 나타내는 `Vector3` 개체
    * **scale**: 배율

1. 이 함수를 통해 원점의 피벗 점을 사용하여 0.015의 배율로 피아노 프레임 및 건반을 스케일링합니다. 함수 호출을 `keyboard.position.y += 80;` 뒤에 배치하여 `createScene()` 함수에 추가합니다.

    ```javascript
    // Put this line at the beginning of createScene()
    const scale = 0.015;
    ```

    ```javascript
    // Put this function call after keyboard.position.y += 80;

    // Scale the entire piano
    scaleFromPivot(piano, new BABYLON.Vector3(0, 0, 0), scale);
    ```

1. 카메라 위치를 스케일링하는 것도 잊지 마세요.

    ```javascript
    const alpha =  3*Math.PI/2;
    const beta = Math.PI/50;
    const radius = 220*scale; // scale the radius
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. 이제 VR 공간으로 다시 들어가면 피아노가 일반적인 스탠드업 피아노 크기가 되었을 것입니다.

    ![VR의 일반적인 스탠드업 피아노](./images/normal-standup-piano.jpg)

## <a name="enabling-webxr-features"></a>WebXR 기능 사용

이제 VR 공간에서 피아노를 적절한 크기로 스케일링했으므로 몇 가지 유용한 WebXR 기능을 사용하여 이 공간의 피아노 연주 환경을 개선해 보겠습니다.

1. 몰입형 VR 컨트롤러를 사용하여 피아노를 연주했다면 한 번에 하나의 컨트롤러만 사용할 수 있다는 것을 알 수 있었을 것입니다. Babylon.js의 [WebXR 기능 관리자](https://doc.babylonjs.com/divingDeeper/webXR/webXRFeaturesManager)를 사용하여 XR 공간에 [멀티 포인터 지원](https://doc.babylonjs.com/typedoc/interfaces/babylon.iwebxrcontrollerpointerselectionoptions)을 활성화하겠습니다.

    `createScene()` 함수에서 `xrHelper` 초기화 줄 뒤에 다음 코드를 추가합니다.

    ```javascript
    const featuresManager = xrHelper.baseExperience.featuresManager;

    const pointerSelection = featuresManager.enableFeature(BABYLON.WebXRFeatureName.POINTER_SELECTION, "stable", {
        xrInput: xrHelper.input,
        enablePointerSelectionOnAllControllers: true        
    });
    ```

1. 또한 시작점에 따라 피아노 앞에 서는 것이 약간 어려울 수 있습니다. 몰입형 VR 환경에 익숙한 경우 **텔레포트** 에 대해 이미 알고 있을 것입니다. 이 기능을 사용하면 해당 공간의 다른 지점을 가리켜서 즉시 이동할 수 있습니다.

1. Babylon.js의 [텔레포트 기능](https://doc.babylonjs.com/divingDeeper/webXR/WebXRSelectedFeatures#teleportation-module)을 사용하려면 먼저 VR 공간에서 "딛고 설" 수 있는 지면 메시가 있어야 합니다. `createScene()` 함수에 다음 코드를 추가하여 지면을 만듭니다.

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 400, height: 400});
    ```

1. 또한 텔레포트 지원에는 [맞춤 위치](https://doc.babylonjs.com/divingDeeper/webXR/WebXRSelectedFeatures#snap-to-hotspots)라는 매우 유용한 기능이 함께 제공됩니다. 즉, 맞춤 위치는 사용자가 도착하려는 특정 위치를 말합니다.

    예를 들어 사용자가 포인터로 피아노 근처를 가리킬 때 해당 위치로 쉽게 텔레포트할 수 있도록 피아노 앞에 맞춤 위치를 설정할 수 있습니다.

    아래 코드를 추가하여 텔레포트 기능을 활성화하고 맞춤 지점을 지정합니다.

    ```javascript
    const teleportation = featuresManager.enableFeature(BABYLON.WebXRFeatureName.TELEPORTATION, "stable", {
        xrInput: xrHelper.input,
        floorMeshes: [ground],
        snapPositions: [new BABYLON.Vector3(2.4*3.5*scale, 0, -10*scale)],
    });
    ```

1. 이제 피아노 앞의 맞춤 지점으로 텔레포트하면 피아노 앞에 손쉽게 설 수 있고, 두 개의 컨트롤러를 모두 사용하여 한 번에 두 개의 건반을 연주할 수 있습니다.

    ![피아노로 텔레포트](./images/teleportation-demo.gif)

    ![컨트롤러를 사용하여 피아노 연주](./images/play-piano-controller.gif)

## <a name="summary"></a>요약

축하합니다! 일련의 Babylon.js 피아노 빌드 자습서를 완료하고 다음을 수행하는 방법을 알아보았습니다.

> [!div class="checklist"]
> * 메시를 생성, 배치 및 병합하여 피아노 키보드 모델 빌드
> * 스탠드업 피아노 프레임의 Babylon.js 모델 가져오기
> * 각 피아노 건반에 포인터 상호 작용 추가
> * 피벗 점을 기준으로 메시 크기 스케일링
> * 텔레포트 및 멀티 포인터 지원과 같은 주요 WebXR 기능 활성화

*scene.js* 및 *index.html* 의 최종 코드는 다음과 같습니다.

*scene.js*

```javascript
const buildKey = function (scene, parent, props) {
    if (props.type === "white") {
        /*
        Props for building a white key should contain: 
        note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX

        As an example, the props for building the middle C white key would be
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
        */

        // Create bottom part
        const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);

        // Create top part
        const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
        top.position.z =  4.75;
        top.position.x += props.topPositionX;

        // Merge bottom and top parts
        // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
        const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.name = props.note + props.register;
        key.parent = parent;

        return key;
    }
    else if (props.type === "black") {
        /*
        Props for building a black key should contain: 
        note, wholePositionX, register, referencePositionX

        As an example, the props for building the C#4 black key would be
        {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
        */

        // Create black color material
        const blackMat = new BABYLON.StandardMaterial("black");
        blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

        // Create black key
        const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
        key.position.z += 4.75;
        key.position.y += 0.25;
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.material = blackMat;
        key.parent = parent;

        return key;
    }
}

const scaleFromPivot = function(transformNode, pivotPoint, scale) {
    const _sx = scale / transformNode.scaling.x;
    const _sy = scale / transformNode.scaling.y;
    const _sz = scale / transformNode.scaling.z;
    transformNode.scaling = new BABYLON.Vector3(_sx, _sy, _sz); 
    transformNode.position = new BABYLON.Vector3(pivotPoint.x + _sx * (transformNode.position.x - pivotPoint.x), pivotPoint.y + _sy * (transformNode.position.y - pivotPoint.y), pivotPoint.z + _sz * (transformNode.position.z - pivotPoint.z));
}

const createScene = async function(engine) {
    const scale = 0.015;
    const scene = new BABYLON.Scene(engine);

    const alpha =  3*Math.PI/2;
    const beta = Math.PI/50;
    const radius = 220*scale;
    const target = new BABYLON.Vector3(0, 0, 0);

    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);

    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
    light.intensity = 0.6;

    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }

    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});

    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });

    // Lift the piano keyboard
    keyboard.position.y += 80;

    // Scale the entire piano
    scaleFromPivot(piano, new BABYLON.Vector3(0, 0, 0), scale);

    const pointerToKey = new Map()
    const pianoSound = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');

    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                // Only take action if the pointer is down on a mesh
                if(pointerInfo.pickInfo.hit) {
                    let pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    let pointerId = pointerInfo.event.pointerId;
                    if (pickedMesh.parent === keyboard) {
                        pickedMesh.position.y -= 0.5; // Move the key downward
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh,
                            note: pianoSound.play(pointerInfo.pickInfo.pickedMesh.name) // Play the sound of the note
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                let pointerId = pointerInfo.event.pointerId;
                // Only take action if the released pointer was recorded in pointerToKey
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5; // Move the key upward
                    pointerToKey.get(pointerId).note.stop(); // Stop the sound of the note
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });

    const xrHelper = await scene.createDefaultXRExperienceAsync();

    const featuresManager = xrHelper.baseExperience.featuresManager;

    featuresManager.enableFeature(BABYLON.WebXRFeatureName.POINTER_SELECTION, "stable", {
        xrInput: xrHelper.input,
        enablePointerSelectionOnAllControllers: true        
    });

    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 400, height: 400});

    featuresManager.enableFeature(BABYLON.WebXRFeatureName.TELEPORTATION, "stable", {
        xrInput: xrHelper.input,
        floorMeshes: [ground],
        snapPositions: [new BABYLON.Vector3(2.4*3.5*scale, 0, -10*scale)],
    });

    return scene;
}
```

*index.html*

```html
<html>
    <head>
        <title>Babylon Template</title>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <script src="scene.js"></script>
        <script src="soundfont-player.min.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
   <body>
    <canvas id="renderCanvas"></canvas>
    <script>
        const canvas = document.getElementById("renderCanvas"); // Get the canvas element
        const engine = new BABYLON.Engine(canvas, true); // Generate the BABYLON 3D engine

        // Register a render loop to repeatedly render the scene
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

## <a name="next-steps"></a>다음 단계

Mixed Reality JavaScript 개발에 대한 자세한 내용은 [JavaScript 개발 개요](/javascript-development-overview.md)를 참조하세요.
