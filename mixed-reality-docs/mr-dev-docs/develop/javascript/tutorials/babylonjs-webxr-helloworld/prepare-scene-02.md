---
title: 기본 3D 개체로 장면을 준비하는 Babylon.js 자습서
description: babylon.js를 사용하고 장면에 기본 3D 개체를 추가하는 방법을 알아봅니다.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: mixed reality, javascript, 자습서, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, 몰입형 웹
ms.localizationpriority: high
ms.openlocfilehash: 8213c445da9c1bbf0eeb591b7995fb61bc6d5b5f
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584510"
---
# <a name="tutorial-prepare-a-scene"></a><span data-ttu-id="0b24c-104">자습서: 장면 준비</span><span class="sxs-lookup"><span data-stu-id="0b24c-104">Tutorial: Prepare a scene</span></span>

<span data-ttu-id="0b24c-105">장면을 준비하고 몇 가지 기본 3D 요소를 추가하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-105">Learn how to prepare a scene, and add some basic 3D elements to it.</span></span>

<span data-ttu-id="0b24c-106">이 자습서에서는 다음 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-106">In this tutorial, learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="0b24c-107">장면 만들기</span><span class="sxs-lookup"><span data-stu-id="0b24c-107">Create a scene</span></span>
> * <span data-ttu-id="0b24c-108">카메라 추가</span><span class="sxs-lookup"><span data-stu-id="0b24c-108">Add a camera</span></span>
> * <span data-ttu-id="0b24c-109">광원 추가</span><span class="sxs-lookup"><span data-stu-id="0b24c-109">Add light</span></span>
> * <span data-ttu-id="0b24c-110">기본 3D 요소 추가</span><span class="sxs-lookup"><span data-stu-id="0b24c-110">Add basic 3D elements</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="0b24c-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="0b24c-111">Before you begin</span></span>

<span data-ttu-id="0b24c-112">이전 자습서 단계에서는 기본 웹 페이지를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-112">In previous tutorial step a basic web page was created.</span></span> <span data-ttu-id="0b24c-113">편집할 웹 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-113">Have the web page open for editing.</span></span>

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

## <a name="create-a-scene"></a><span data-ttu-id="0b24c-114">장면 만들기</span><span class="sxs-lookup"><span data-stu-id="0b24c-114">Create a scene</span></span>

<span data-ttu-id="0b24c-115">장면에는 모든 콘텐츠가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-115">A scene is where all the contents will be displayed.</span></span> <span data-ttu-id="0b24c-116">여러 장면이 있을 수 있으며, 장면을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-116">There might be multiple scenes and it is possible to switch between scenes.</span></span> <span data-ttu-id="0b24c-117">[babylon.js 장면](https://doc.babylonjs.com/divingDeeper/scene)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-117">Read more about [babylon.js Scene](https://doc.babylonjs.com/divingDeeper/scene).</span></span>

1. <span data-ttu-id="0b24c-118">canvas html 요소 뒤에 스크립트 태그를 추가하고 다음 코드를 추가하여 검은색으로 채워진 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-118">Add the script tag after the canvas html element and add the following code to create a scene filled in black color:</span></span>

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

    <span data-ttu-id="0b24c-119">위의 코드에서는 장면을 렌더링하고 캔버스에 이벤트를 후크하는 babylon.js 웹 렌더링 엔진의 인스턴스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-119">In the code above we have to create an instance of babylon.js web rendering engine that renders a scene and hooks events on the canvas.</span></span> <span data-ttu-id="0b24c-120">엔진에 대한 자세한 내용은 문서 페이지 [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="0b24c-120">For more information about the engine, check the documentation page [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span></span>

1. <span data-ttu-id="0b24c-121">장면은 기본적으로 렌더링되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-121">The scene is not rendered by default.</span></span> <span data-ttu-id="0b24c-122">여러 장면이 있을 수 있으며 표시되는 장면을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-122">Remember, there might be multiple scenes and you control which scene is displayed.</span></span> <span data-ttu-id="0b24c-123">모든 프레임에서 장면을 반복적으로 렌더링하려면 *createScene* 함수를 호출한 후 다음 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-123">To render the scene repeatedly on every frame, execute the following code after the call to *createScene* function:</span></span>

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a><span data-ttu-id="0b24c-124">기본 3D 요소 추가</span><span class="sxs-lookup"><span data-stu-id="0b24c-124">Add basic 3D element</span></span>

1. <span data-ttu-id="0b24c-125">첫 번째 3D 셰이프를 추가해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-125">Let's add our first 3D shape.</span></span> <span data-ttu-id="0b24c-126">3D 가상 세계에서 셰이프는 *메시* 로 만들어지며, 많은 삼각형 패싯이 함께 결합되어 있으며 각 패싯은 세 개의 정점으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-126">In the 3D virtual world shapes are built from *meshes*, lots of triangular facets joined together, each facet made from three vertices.</span></span> <span data-ttu-id="0b24c-127">미리 정의된 메시를 사용하거나 고유한 사용자 지정 메시를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-127">You can either use a predefined mesh or create your own custom mesh.</span></span> <span data-ttu-id="0b24c-128">여기서는 미리 정의된 상자 메시(예: 큐브)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-128">Here we will be using a predefined box mesh, i.e. a cube.</span></span> <span data-ttu-id="0b24c-129">상자를 만들려면 [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-129">To create the box use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span></span> <span data-ttu-id="0b24c-130">매개 변수는 이름, 옵션(메시의 유형에 따라 달라지는 옵션)입니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-130">The parameters are name, and options (options are different according to the type of mesh).</span></span> <span data-ttu-id="0b24c-131">*createScene* 함수에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-131">Append the following code to the function *createScene*:</span></span>

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. <span data-ttu-id="0b24c-132">Microsoft Edge 브라우저에서 웹 페이지를 열고 출력을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-132">Open the web page in the Microsoft Edge browser and check the output.</span></span> <span data-ttu-id="0b24c-133">브라우저 창에 빈 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-133">The browser window shows a blank page.</span></span> <span data-ttu-id="0b24c-134">키보드를 사용하여 DevTools를 열고 F12 또는 Control+Shift+I(Windows, Linux) 또는 Command+Option+I(macOS)를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-134">Open DevTools by using the keyboard and select F12 or Control+Shift+I (Windows, Linux) or Command+Option+I (macOS).</span></span> <span data-ttu-id="0b24c-135">*콘솔* 탭을 연 후 오류 찾기를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-135">After opening the *Console* tab, you can start looking for errors.</span></span> <span data-ttu-id="0b24c-136">'Catch되지 않은 오류: 카메라가 정의되지 않음' 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-136">There will be an error displayed: 'Uncaught Error: No camera defined'.</span></span> <span data-ttu-id="0b24c-137">이제 장면에 카메라를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-137">Now we have to add a camera to the scene.</span></span>

## <a name="add-a-camera"></a><span data-ttu-id="0b24c-138">카메라 추가</span><span class="sxs-lookup"><span data-stu-id="0b24c-138">Add a camera</span></span>

1. <span data-ttu-id="0b24c-139">가상 세계를 보고 상호 작용하려면 카메라를 캔버스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-139">In order to view the virtual world and interact with it, a camera must be attached to the canvas.</span></span> <span data-ttu-id="0b24c-140">대상을 중심으로 회전할 수 있는 [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) 유형의 카메라를 추가해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-140">Let's add the camera of type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), which can be rotated around a target.</span></span> <span data-ttu-id="0b24c-141">카메라 인스턴스를 만드는 데 필요한 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-141">The parameters required to create an instance of the camera are:</span></span>
    1. <span data-ttu-id="0b24c-142">**name**: 카메라 이름</span><span class="sxs-lookup"><span data-stu-id="0b24c-142">**name**: name of the camera</span></span>
    1. <span data-ttu-id="0b24c-143">**alpha**: 세로 축을 따른 각도 위치(라디안)</span><span class="sxs-lookup"><span data-stu-id="0b24c-143">**alpha**: angular position along the longitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="0b24c-144">**beta**: 가로 축을 따른 각도 위치(라디안)</span><span class="sxs-lookup"><span data-stu-id="0b24c-144">**beta**: angular position along the latitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="0b24c-145">**radius**: 대상으로부터의 거리</span><span class="sxs-lookup"><span data-stu-id="0b24c-145">**radius**: distance from the target</span></span>
    1. <span data-ttu-id="0b24c-146">**target**: 카메라가 항상 향하는 지점(x-y-z 좌표로 정의됨)</span><span class="sxs-lookup"><span data-stu-id="0b24c-146">**target**: the point that the camera would always face towards (defined by x-y-z coordinates)</span></span>
    1. <span data-ttu-id="0b24c-147">**scene**: 카메라가 있는 장면</span><span class="sxs-lookup"><span data-stu-id="0b24c-147">**scene**: the scene that the camera is in</span></span>

    <span data-ttu-id="0b24c-148">Alpha, beta, radius, target은 아래 다이어그램에 표시된 것과 같이 공간에서 카메라의 위치를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-148">Alpha, beta, radius, and target together define the camera's position in the space, as shown in the diagram below:</span></span>

    ![카메라 알파 베타 반경](../images/camera-alpha-beta-radius.jpg)

    <span data-ttu-id="0b24c-150">*createScene* 함수에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-150">Add the following code to the *createScene* function:</span></span>

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. <span data-ttu-id="0b24c-151">브라우저에서 출력을 확인하는 경우 검은색 캔버스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-151">If you check the output in the browser, you will see a black canvas.</span></span> <span data-ttu-id="0b24c-152">광원이 누락되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-152">We are missing the light.</span></span>

## <a name="add-light"></a><span data-ttu-id="0b24c-153">광원 추가</span><span class="sxs-lookup"><span data-stu-id="0b24c-153">Add light</span></span>

1. <span data-ttu-id="0b24c-154">다양한 조명 속성과 함께 사용할 수 있는 광원에는 포인트, 방향, 스폿 및 반구 광원의 네 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-154">There are four types of lights that can be used with a range of lighting properties: Point, Directional, Spot and Hemispheric Light.</span></span> <span data-ttu-id="0b24c-155">다음과 같이 주변 광원 [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight)를 추가해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-155">Let's add the ambient light [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), as follows:</span></span>

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. <span data-ttu-id="0b24c-156">웹 페이지의 최종 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-156">The final code of the web page will look as follows:</span></span>

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

1. <span data-ttu-id="0b24c-157">브라우저의 출력을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-157">Check the output in the browser.</span></span> <span data-ttu-id="0b24c-158">큐브를 표시하고 마우스를 사용하여 큐브 주위에서 카메라를 회전하고 큐브의 다른 면을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b24c-158">You should see the cube and using the mouse you can rotate the camera around the cube and see the different faces of the cube:</span></span>

![큐브가 있는 기본 장면](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a><span data-ttu-id="0b24c-160">다음 단계</span><span class="sxs-lookup"><span data-stu-id="0b24c-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b24c-161">다음 자습서: 3. 3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="0b24c-161">Next Tutorial: 3. Interact with 3D object</span></span>](interact-03.md)
