---
title: 3D 피아노 모델 빌드
description: Babylon.js로 코딩하여 3D 피아노 모델을 만드는 방법 알아보기
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: mixed reality, javascript, 자습서, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, 몰입형 웹
ms.localizationpriority: high
ms.openlocfilehash: e5c3dd6206566f781ceb52e5d13a49a0c9ab1018
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932512"
---
# <a name="tutorial-build-a-3d-piano-model"></a>자습서: 3D 피아노 모델 빌드

이 시리즈의 이전 자습서에서는 카메라와 조명이 있는 Babylon.js 장면을 포함하는 웹 페이지를 설정했습니다. 이 자습서에서는 피아노 모델을 빌드하고 장면에 추가합니다.

![스탠드업 피아노 메시](./images/standup-piano-mesh.png)

이 자습서에서는 다음 작업 방법을 배웁니다.

> [!div class="checklist"]
> * 메시 생성, 배치 및 병합
> * 상자 메시에서 피아노 키보드 빌드
> * 피아노 프레임의 3D 모델 가져오기

## <a name="before-you-begin"></a>시작하기 전에

[이 시리즈의 이전 자습서](introduction-01.md)를 완료했고 코드에 계속 추가할 준비가 되었는지 확인합니다.

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

## <a name="getting-started"></a>시작

먼저 다음과 같은 구조의 간단한 피아노 키보드를 만들어 보겠습니다.

![피아노 음역 설명](./images/piano-register.jpg)

이 이미지에는 각각 음 이름으로 레이블이 지정된 7개의 흰색 건반과 5개의 검은색 건반이 있습니다. 풀 사이즈 88키 피아노 키보드에는 이러한 건반 모음이 7번 반복되고 4개의 추가 건반이 있습니다. 각 음역의 주파수는 이전 음역의 두 배입니다. 예를 들어 C5의 음 높이 주파수(즉, 다섯 번째 음역의 C 음)는 C4의 두 배이고, D5의 음 높이 주파수는 D4의 두 배인 경우입니다.

시각적으로 각 음역은 다른 음역과 똑같아 보이므로 이 건반 모음을 사용하여 간단한 피아노 키보드를 만드는 방법을 살펴볼 수 있습니다. 나중에 범위를 88키 풀 사이즈 키보드로 확장하는 방법을 찾아낼 수 있습니다.

## <a name="build-a-simple-piano-keyboard"></a>간단한 피아노 키보드 빌드

> [!NOTE]
> 온라인 소스에서 미리 만들어진 3D 피아노 키보드 모델을 찾아 웹 페이지로 가져올 수 있지만 이 자습서에서는 최대 사용자 지정 기능을 허용하고 Babylon.js를 통해 3D 모델을 만드는 방법을 보여 주기 위해 키보드를 처음부터 빌드합니다.

1. 키보드를 빌드하기 위해 메시를 만들기 전에 각 검은색 건반이 두 흰색 건반의 정가운데에 정렬되어 있지 않고 모든 건반의 너비가 동일하지 않다는 것에 유의하세요. 즉, 각 건반에 대한 메시를 개별적으로 만들고 배치해야 합니다.

    ![검은색 건반 정렬](./images/black-key-position.png)

1. 각 흰색 건반은 (1) 검은색 건반 아래의 아래쪽 부분과 (2) 검은색 건반 옆의 위쪽 부분의 두 부분으로 구성된 것을 알 수 있습니다. 두 부분은 서로 차원이 다르지만 스택되어 흰색 건반 하나를 만듭니다.

    ![흰색 건반 모양](./images/white-key-shape-label.png)

1. 다음은 C 음에 대한 단일 흰색 건반을 만드는 코드입니다(*scene.js* 에 추가하는 것은 아직 걱정하지 마세요).

    ```javascript
    const whiteKeyBottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: 2.3, height: 1.5, depth: 4.5}, scene);
    const whiteKeyTop = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: 1.4, height: 1.5, depth: 5}, scene);
    whiteKeyTop.position.z += 4.75;
    whiteKeyTop.position.x -= 0.45;

    // Parameters of BABYLON.Mesh.MergeMeshes:
    // (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
    const whiteKeyV1 = BABYLON.Mesh.MergeMeshes([whiteKeyBottom, whiteKeyTop], true, false, null, false, false);
    whiteKeyV1.material = whiteMat;
    whiteKeyV1.name = "C4";
    ```

    여기서는 각각 흰색 건반의 아래쪽 부분과 위쪽 부분에 해당하는 두 개의 [Box](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box#box-mesh) 메시를 만들었습니다. 그런 다음, 위쪽 부분의 위치를 수정하여 아래쪽 부분 위에 스택하고 왼쪽으로 옮겨서 인접한 검은색 건반(C#)을 위한 공간을 남겨 둡니다.

    마지막으로, 이러한 두 부분은 [MergeMeshes](https://doc.babylonjs.com/divingDeeper/mesh/mergeMeshes) 함수를 통해 병합되어 하나의 완전한 흰색 건반이 되었습니다. 이 코드가 생성하는 결과 메시는 다음과 같습니다.

    ![흰색 건반 C](./images/white-key-c.png)

1. 검은색 건반을 만드는 방법이 더 간단합니다. 모든 검은색 건반은 상자 모양이므로 검은색 [StandardMaterial](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction#color)을 사용하여 상자 메시를 만드는 것만으로 검은색 건반을 만들 수 있습니다.

    > [!NOTE]
    > 기본 메시 색은 흰색과 비슷한 연한 회색이므로 흰색 건반에 흰색 재질을 추가하는 단계는 이 자습서에서 다루지 않습니다. 그러나 흰색 건반에 정확히 흰색을 사용하려면 재질을 자유롭게 추가할 수 있습니다.

    다음은 검은색 건반 C#을 만드는 코드입니다(*scene.js* 에 추가하는 것은 걱정하지 마세요).

    ```javascript
    const blackMat = new BABYLON.StandardMaterial("black");
    blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

    const blackKey = BABYLON.MeshBuilder.CreateBox("C#4", {width: 1.4, height: 2, depth: 5}, scene);
    blackKey.position.z += 4.75;
    blackKey.position.y += 0.25;
    blackKey.position.x += 0.95;
    blackKey.material = blackMat;
    ```

    이 코드로 생성된 검은색 건반과 이전 흰색 건반의 모양은 다음과 같습니다.

    ![검은색 건반 C#](./images/black-key-csharp.png)

1. 보셨듯이 각 건반을 만들면 각 차원과 위치를 지정해야 하기 때문에 비슷한 코드가 많이 생길 수 있습니다. 다음 섹션에서 생성 프로세스를 보다 효율적으로 만들어 보겠습니다.

## <a name="build-a-simple-piano-keyboard-efficiently"></a>간단한 피아노 키보드를 효율적으로 빌드

1. 각 흰색 건반의 모양은 서로 약간 다르지만 위쪽 부분과 아래쪽 부분을 결합하여 모든 건반을 만들 수 있습니다. 일반 함수를 구현하여 흰색 건반을 만들고 배치해 보겠습니다.

    *scene.js* 의 `createScene()` 함수 외부에 아래 함수를 추가합니다.

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
    }
    ```

    이 코드 블록에서는 `props.type`이 `"white"`인 경우 흰색 건반을 빌드하고 반환하는 `buildKey()`라는 함수를 만들었습니다. 동일한 함수에서 if 문을 통해 분기하여 `props` 매개 변수로 건반 유형을 식별하면 검은색 건반과 흰색 건반을 모두 만들 수 있습니다.

    `buildKey()`의 매개 변수는 다음과 같습니다.
    * **scene**: 건반이 있는 장면
    * **parent**: 메시의 부모(이를 통해 모든 건반을 단일 부모로 그룹화할 수 있음)
    * **props**: 빌드할 건반의 속성

    흰색 건반의 `props`에는 다음 항목이 포함됩니다.
    * **type**: "white"
    * **name**: 건반이 나타내는 음의 이름
    * **topWidth**: 위쪽 부분의 너비
    * **bottomWidth**: 아래쪽 부분의 너비
    * **topPositionX**: 아래쪽 부분을 기준으로 한 위쪽 부분의 x 위치
    * **wholePositionX**: 음역의 끝점을 기준으로 한 단일 건반의 x 위치(B 건반의 오른쪽 가장자리).
    * **register**: 건반이 속한 음역(0과 8 사이의 숫자)
    * **referencePositionX**: 음역 끝점의 x 좌표(기준점으로 사용).

    `wholePositionX`와 `referencePositionX`를 구분하면 모든 음역 내에서 특정 유형의 건반(예: C)을 만드는 데 필요한 `props` 매개 변수를 초기화한 다음, 특정 음역(예: C4, C5)에서 해당 건반을 만들 때 `register` 및 `referencePositionX`를 `props`에 추가할 수 있습니다.

1. 마찬가지로, 검은색 건반을 만드는 제네릭 함수를 작성할 수도 있습니다. 해당 논리를 포함하도록 `buildKey()` 함수를 확장해 보겠습니다.

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
    ```

    검은색 건반의 `props`에는 다음 항목이 포함됩니다.

    * **type**: "black"
    * **name**: 건반이 나타내는 음의 이름
    * **wholePositionX**: 음역의 끝점을 기준으로 한 단일 건반의 x 위치(B 건반의 오른쪽 가장자리)
    * **register**: 건반이 속한 음역(0과 8 사이의 숫자)
    * **referencePositionX**: 음역 끝점의 x 좌표(기준점으로 사용).

    검은색 건반을 만들려면 상자를 만들기만 하면 되고 모든 검은색 건반의 너비와 z 위치가 동일하기 때문에 검은색 건반을 만드는 데 필요한 `props`는 훨씬 더 단순합니다.

1. 이제 건반을 보다 효율적으로 만들 수 있으므로 음역의 음에 해당하는 각 건반의 `props`를 저장하는 배열을 초기화한 다음, 각 건반과 함께 `buildKey()` 함수를 호출하여 4번째 음역의 간단한 키보드를 만들어 보겠습니다.

    또한 모든 피아노 건반의 [parent](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/parent#overview-of-a-parent) 역할을 하는 `keyboard`라는 [TransformNode](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/transform_node#a-transformnode)를 만듭니다. 부모에 적용된 위치 또는 스케일링 변경 사항은 자식에도 적용되므로 이러한 방식으로 건반을 그룹화하면 전체적으로 스케일링하거나 이동할 수 있습니다.

    다음 코드 줄을 `createScene()` 함수에 추가합니다.

    ```javascript
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

    keyParams.forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
    })
    ```

    앞에서 보았듯이 이 코드 블록에서는 공간의 원점을 기준으로 모든 건반을 배치합니다.

1. 지금까지 *scene.js* 에 포함된 코드는 다음과 같습니다.

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
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
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
    
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
        })

        const xrHelper = await scene.createDefaultXRExperienceAsync();

        return scene;
    }
    ```

1. 결과 키보드의 모양은 다음과 같습니다.

    ![하나의 음역이 있는 피아노 키보드](./images/piano-one-register.png)

## <a name="expanding-to-an-88-key-piano"></a>88키 피아노로 확장

이 섹션에서는 건반 생성 함수의 사용을 확장하여 풀 사이즈 88키 피아노 키보드를 생성해 보겠습니다.

1. 앞서 언급했듯이 풀 사이즈 88키 피아노 키보드에는 7개의 반복 음역과 4개의 기타 음이 포함되어 있습니다. 이러한 추가 음 중 3개는 음역 0(키보드의 왼쪽 끝)에 있고 1개는 음역 8(키보드의 오른쪽 끝)에 있습니다.

    ![88키 피아노 레이아웃](./images/88-key-piano-keyboard-layout.jpg)

1. 먼저 이전에 작성한 루프 주위에 루프를 더 추가하여 7개의 전체 반복을 빌드하는 작업을 수행합니다. `buildKey()` 함수의 이전 루프를 다음 코드로 바꿉니다.

    ```javascript
    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }
    ```

    이 루프에서는 음역 1~7의 건반을 빌드하고 다음 음역으로 이동할 때마다 기준 위치를 증분합니다.

1. 다음으로, 나머지 건반을 만들어 보겠습니다. `createScene()` 함수에 다음 조각을 추가합니다.

    ```javascript
    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    ```

    피아노 키보드의 가장 왼쪽에 있는 건반과 가장 오른쪽에 있는 건반은 `keyParams`에 정의된 props의 크기에 맞지 않으므로(가장자리의 검은색 건반 옆에 있지 않기 때문에) 각각에 대한 새 `props` 개체를 정의하여 특수한 모양을 지정해야 합니다.

1. 생성된 키보드의 변경 후 모양은 다음과 같습니다.

    ![풀 사이즈 피아노 키보드 메시](./images/full-keyboard-mesh.png)

## <a name="adding-a-piano-frame"></a>피아노 프레임 추가

1. 이 장면은 공간에 키보드만 떠 있어 약간 이상해 보입니다. 키보드 주위에 피아노 프레임을 추가하여 스탠드업 피아노의 모양을 만들어 보겠습니다.

1. 건반을 만드는 방법과 마찬가지로 상자 메시 그룹을 배치하고 결합하여 프레임을 만들 수도 있습니다.

    그러나 이는 직접 도전해 볼 수 있게 과제로 남겨 두고, [BABYLON.SceneLoader.ImportMesh](https://doc.babylonjs.com/divingDeeper/importers/loadingFileTypes#sceneloaderimportmesh)를 사용하여 미리 만들어진 스탠드업 피아노 프레임의 메시를 가져오겠습니다. 이 코드 조각을 `createScene()`에 추가합니다.

    ```javascript
    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });
    ```

    다시 한 번 `piano`라는 부모 `TransformNode`를 만들어 키보드와 프레임을 전체적으로 그룹화합니다. 이렇게 하면 필요한 경우에 전체 피아노를 훨씬 더 쉽게 이동하거나 스케일링할 수 있습니다.

1. 프레임을 가져오면 프레임의 아래쪽에 키보드가 있는 것을 확인할 수 있습니다(건반의 y 좌표가 기본적으로 0이므로). 키보드를 스탠드업 프레임에 맞게 들어 올려 보겠습니다.

    ```javascript
    // Lift piano keys
    keyboard.position.y += 80;
    ```

    `keyboard`는 모든 피아노 건반의 부모이므로 `keyboard`의 y 위치를 변경하기만 하면 모든 피아노 건반을 들어 올릴 수 있습니다.

1. *scene.js* 의 최종 코드는 다음과 같습니다.

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

1. 이제 ![스탠드업 피아노 메시](./images/standup-piano-mesh.png) 같은 스탠드업 피아노가 생겼습니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [다음 자습서: 3D 피아노 연주](keyboard-interaction-03.md)
