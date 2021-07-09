---
title: 3D 개체와 상호 작용하는 Babylon.js 자습서
description: babylon.js를 사용하고 3D 개체와 상호 작용하는 방법을 알아봅니다.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: mixed reality, javascript, 자습서, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, 몰입형 웹
ms.localizationpriority: high
ms.openlocfilehash: a3dbab0572cd50105dac3d877a0d72c5cbc504b6
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584522"
---
# <a name="tutorial-interact-with-3d-object"></a><span data-ttu-id="85b27-104">자습서: 3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="85b27-104">Tutorial: Interact with 3D object</span></span>

<span data-ttu-id="85b27-105">babylon.js를 사용하여 Mixed Reality 환경에서 3D 개체 및 상호 작용을 만드는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-105">Learn how to create 3D objects and interactions for a Mixed Reality experience using babylon.js.</span></span> <span data-ttu-id="85b27-106">이 섹션에서는 개체를 선택할 때 큐브의 면을 색칠하는 간단한 작업으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-106">In this section, you'll start with something simple, like painting the faces of a cube when you select the object.</span></span>

<span data-ttu-id="85b27-107">이 자습서에서는 다음 항목을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-107">This tutorial covers the following topics:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="85b27-108">상호 작용을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="85b27-108">How to add interactions</span></span>
> * <span data-ttu-id="85b27-109">WebXR 몰입형 모드 사용</span><span class="sxs-lookup"><span data-stu-id="85b27-109">Enable WebXR immersive mode</span></span>
> * <span data-ttu-id="85b27-110">Windows Mixed Reality 시뮬레이터에서 앱 실행</span><span class="sxs-lookup"><span data-stu-id="85b27-110">Run the app on Windows Mixed Reality Simulator</span></span>
> * <span data-ttu-id="85b27-111">Android Chrome에서 앱 실행 및 디버그</span><span class="sxs-lookup"><span data-stu-id="85b27-111">Run and debug the app on Android Chrome</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="85b27-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="85b27-112">Before you begin</span></span>

<span data-ttu-id="85b27-113">이전 자습서에서는 장면이 있는 기본 웹 페이지를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-113">In previous tutorial step a basic web page with a scene was created.</span></span> <span data-ttu-id="85b27-114">편집할 호스팅 웹 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-114">Have the hosting web page open for editing.</span></span>

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

## <a name="add-interaction"></a><span data-ttu-id="85b27-115">상호 작용 추가</span><span class="sxs-lookup"><span data-stu-id="85b27-115">Add interaction</span></span>

1. <span data-ttu-id="85b27-116">먼저 큐브를 만드는 코드를 업데이트해 보겠습니다. 그러면 큐브는 임의의 색으로 칠해집니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-116">First, let's update our code that creates the cube, so that the cube is painted with a random color.</span></span> <span data-ttu-id="85b27-117">이를 위해 큐브에 [재질](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction)을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-117">To do that, we will add [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) to our cube.</span></span> <span data-ttu-id="85b27-118">재질은 색과 텍스처를 지정하고 다른 개체를 포함하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-118">Material allows us to specify color and textures and can be used to cover other objects.</span></span> <span data-ttu-id="85b27-119">재질의 표시 방법은 장면에서 사용되는 광원 및 반응하도록 설정하는 방법에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-119">How a material appears depends on the light or lights used in the scene and how it is set to react.</span></span> <span data-ttu-id="85b27-120">예를 들어 diffuseColor는 연결된 메시 전체에 색을 분산합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-120">For example, the diffuseColor spreads the color all over the mesh to which it is attached.</span></span> <span data-ttu-id="85b27-121">다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-121">Add the following code:</span></span>

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. <span data-ttu-id="85b27-122">이제 큐브가 임의의 색으로 칠해졌으므로 다음과 같이 상호 작용을 추가해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-122">Now that the cube is painted with a random color, let's add an interaction to:</span></span>

    * <span data-ttu-id="85b27-123">큐브를 클릭했을 때 색 변경</span><span class="sxs-lookup"><span data-stu-id="85b27-123">Change the color when the cube is clicked</span></span>
    * <span data-ttu-id="85b27-124">색이 변경된 후 큐브 이동</span><span class="sxs-lookup"><span data-stu-id="85b27-124">Move the cube after the color is changed</span></span>

    <span data-ttu-id="85b27-125">상호 작용을 추가하려면 [작업](https://doc.babylonjs.com/divingDeeper/events/actions)을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-125">To add interactions we should be using [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span></span> <span data-ttu-id="85b27-126">작업은 이벤트 트리거에 대한 응답으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-126">An action is launched in response to the event trigger.</span></span> <span data-ttu-id="85b27-127">예를 들어 사용자가 큐브를 클릭하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-127">For example, when the user clicks on the cube.</span></span> <span data-ttu-id="85b27-128">BABYLON.ActionManager를 인스턴스화하고 특정 트리거에 대한 작업을 등록하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-128">All we need to do is instantiate BABYLON.ActionManager and register an action for certain trigger.</span></span> <span data-ttu-id="85b27-129">[BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction)은 누군가 큐브를 클릭할 때 JavaScript 함수를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-129">The [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) will run our JavaScript function when someone clicks on the cube:</span></span>

    ```javascript
    box.actionManager = new BABYLON.ActionManager(scene);
    box.actionManager.registerAction(new BABYLON.ExecuteCodeAction(
        BABYLON.ActionManager.OnPickTrigger, 
        function (evt) {
            const sourceBox = evt.meshUnderPointer;
            
            //move the box upright
            sourceBox.position.x += 0.1;
            sourceBox.position.y += 0.1;

            //update the color
            boxMaterial.diffuseColor = BABYLON.Color3.Random();
        }));
    ```

1. <span data-ttu-id="85b27-130">웹 페이지의 최종 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-130">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));

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

## <a name="enable-webxr-immersive-experience"></a><span data-ttu-id="85b27-131">WebXR 몰입형 환경 사용 설정</span><span class="sxs-lookup"><span data-stu-id="85b27-131">Enable WebXR immersive experience</span></span>

<span data-ttu-id="85b27-132">이제 큐브의 색이 변경되었으므로 몰입형 환경을 사용해 볼 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-132">Now that our cube is changing colors, we're ready to try the immersive experience.</span></span>

1. <span data-ttu-id="85b27-133">이 단계에서는 [지면](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground)을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-133">In this step we're going to introduce a [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span></span> <span data-ttu-id="85b27-134">큐브가 공중에 매달려 있고 아래쪽에는 바닥이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-134">The cube will be hanging in the air and we will see a floor at the bottom.</span></span> <span data-ttu-id="85b27-135">다음과 같이 지면을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-135">Add the ground as follows:</span></span>

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    <span data-ttu-id="85b27-136">이렇게 하면 단순한 4x4미터 바닥이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-136">This creates a simple 4x4-meter floor.</span></span>

1. <span data-ttu-id="85b27-137">WebXR 지원을 추가하려면 *프라미스* 결과가 있는 *createDefaultXRExperienceAsync* 를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-137">In order to add WebXR support, we need to call *createDefaultXRExperienceAsync*, which has a *Promise* result.</span></span> <span data-ttu-id="85b27-138">*return scene;* 대신 *createScene* 함수 끝에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-138">Add this code at the end of *createScene* function instead of *return scene;*:</span></span>

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. <span data-ttu-id="85b27-139">이제 *createScene* 함수가 장면 대신 프라미스를 반환하므로 *createScene* 및 *engine.runRenderLoop* 가 호출되는 방식을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-139">Since the *createScene* function is now returning a promise instead of a scene, we need to modify how *createScene* and *engine.runRenderLoop* are called.</span></span> <span data-ttu-id="85b27-140">*\</script>* 태그 바로 앞에 있는 이러한 함수의 현재 호출을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-140">Replace the current calls of these functions, which are located right before the *\</script>* tag, with the code below:</span></span>

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. <span data-ttu-id="85b27-141">웹 페이지의 최종 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-141">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));
                    
                const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
                
                const xrPromise = scene.createDefaultXRExperienceAsync({
                    floorMeshes: [ground]
                });
                
                return xrPromise.then((xrExperience) => {
                    console.log("Done, WebXR is enabled.");
                    return scene;
                });
            };
            
            createScene().then(sceneToRender => {
                engine.runRenderLoop(() => sceneToRender.render());
            });
        </script>
    </body>
    </html>
    ```

1. <span data-ttu-id="85b27-142">위의 코드는 브라우저 창에 다음 출력을 생성합니다. ![WebXR 장면](../images/hello-world-webxr-scene.png)</span><span class="sxs-lookup"><span data-stu-id="85b27-142">The above code generates the following output in the browser window: ![WebXR scene](../images/hello-world-webxr-scene.png)</span></span>

## <a name="run-on-a-windows-mixed-reality-simulator"></a><span data-ttu-id="85b27-143">Windows Mixed Reality 시뮬레이터에서 실행</span><span class="sxs-lookup"><span data-stu-id="85b27-143">Run on a Windows Mixed Reality Simulator</span></span>

1. <span data-ttu-id="85b27-144">이전에 사용하지 않은 경우 [Windows Mixed Reality 시뮬레이터를 사용하도록 설정합니다.](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="85b27-144">[Enable the Windows Mixed Reality Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) if you have not done so in the past.</span></span>

1. <span data-ttu-id="85b27-145">오른쪽 하단에 있는 몰입형 VR 단추를 선택합니다. ![몰입형 VR 단추](../images/immersive-vr-button.png)</span><span class="sxs-lookup"><span data-stu-id="85b27-145">Select the Immersive-VR button on the bottom right corner: ![Immersive VR Button](../images/immersive-vr-button.png)</span></span>

1. <span data-ttu-id="85b27-146">이 작업을 수행하면 아래와 같이 Windows Mixed Reality 시뮬레이터 창이 시작됩니다. ![Mixed Reality 포털](../images/mixed-reality-portal.png)</span><span class="sxs-lookup"><span data-stu-id="85b27-146">This action will launch the Windows Mixed Reality Simulator window as shown below: ![Mixed Reality Portal](../images/mixed-reality-portal.png)</span></span>

1. <span data-ttu-id="85b27-147">키보드에서 W, A, S 및 D 키를 사용하여 앞으로, 뒤로, 왼쪽 및 오른쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-147">Use the W,A,S, and D keys on your keyboard to walk forward, back left and right accordingly.</span></span> <span data-ttu-id="85b27-148">시뮬레이션된 손을 사용하여 큐브를 대상으로 하고 키보드에서 Enter 키를 눌러 클릭 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-148">Use simulated hand to target the cube and press the Enter key on your keyboard to perform the click action.</span></span> <span data-ttu-id="85b27-149">큐브의 색이 변경되고 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-149">The cube will change its color and move to a new position.</span></span>

> [!NOTE]
> <span data-ttu-id="85b27-150">큐브를 대상으로 하는 경우 위 그림에 표시된 것처럼 손 광선(흰색 원)의 끝이 큐브와 교차하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-150">When targeting the cube, make sure that the end of hand ray (white circle) intersects with the cube as shown on the picture above.</span></span> <span data-ttu-id="85b27-151">[손으로 가리키기 및 커밋](../../../../design/point-and-commit.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-151">Learn more about [Point and commit with hands](../../../../design/point-and-commit.md).</span></span>

## <a name="run-and-debug-on-android-device"></a><span data-ttu-id="85b27-152">Android 디바이스에서 실행 및 디버그</span><span class="sxs-lookup"><span data-stu-id="85b27-152">Run and debug on Android device</span></span>

<span data-ttu-id="85b27-153">Android 디바이스에서 디버깅을 사용하도록 설정하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-153">Perform the following steps to enable debugging on your Android device:</span></span>

### <a name="prerequisites"></a><span data-ttu-id="85b27-154">필수 조건</span><span class="sxs-lookup"><span data-stu-id="85b27-154">Prerequisites</span></span>

* <span data-ttu-id="85b27-155">개발 컴퓨터에서 보안 컨텍스트(https:// 또는 localhost의 포트 전달을 통해)의 정적 html 페이지를 제공하는 웹 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-155">A web server that serves static html page in secure context (https:// or via Port forwarding on localhost) on development machine.</span></span> <span data-ttu-id="85b27-156">예를 들어 *serve* npm 패키지를 정적 html 파일을 제공하는 간단한 경량 웹 서버로 활용하려면 더 많은 [npm serve](https://github.com/vercel/serve#readme)를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="85b27-156">For example leverage *serve* npm package as simple lightweight web server that serves static html files, check more [npm serve](https://github.com/vercel/serve#readme)</span></span>
* <span data-ttu-id="85b27-157">디바이스는 원래 Google Play 스토어가 함께 제공되며 Android 7.0 이상 버전을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-157">The device originally shipped with the Google Play Store and must be running Android 7.0 or newer</span></span>
* <span data-ttu-id="85b27-158">개발 워크스테이션과 디바이스 모두에서 최신 버전의 [Google Chrome](https://support.google.com/chrome/answer/95346)</span><span class="sxs-lookup"><span data-stu-id="85b27-158">The latest version of [Google Chrome](https://support.google.com/chrome/answer/95346) on both the development workstation and on the device</span></span>
* <span data-ttu-id="85b27-159">디바이스가 WebXR을 실행하도록 올바르게 구성되었는지 확인하려면 디바이스에서 [샘플 WebXR 페이지](https://immersive-web.github.io/webxr-samples/)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-159">To verify that the device is correctly configured to run WebXR, browse to a [sample WebXR page](https://immersive-web.github.io/webxr-samples/) on the device.</span></span> <span data-ttu-id="85b27-160">다음 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-160">You should see the message, such as:</span></span>

    > <span data-ttu-id="85b27-161">브라우저는 WebXR을 지원하고 적절한 하드웨어가 있는 경우 가상 현실 및 증강 현실 환경을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-161">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware.</span></span>

1. <span data-ttu-id="85b27-162">Android 디바이스에서 개발자 모드 및 USB 디버깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-162">Enable developer mode and USB debugging on an Android device.</span></span> <span data-ttu-id="85b27-163">공식 문서 페이지 [디바이스 개발자 옵션 구성](https://developer.android.com/studio/debug/dev-options)에서 사용 중인 Android 버전에 대해 이 작업을 수행하는 방법을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85b27-163">See how to do this for your version of Android at the official documentation page [Configure on-device developer options](https://developer.android.com/studio/debug/dev-options)</span></span>
1. <span data-ttu-id="85b27-164">다음으로, USB 케이블을 통해 Android 디바이스를 개발 컴퓨터 또는 랩톱에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-164">Next, connect Android device to your development machine or laptop via USB cable</span></span>
1. <span data-ttu-id="85b27-165">개발 컴퓨터의 웹 서버가 실행되고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-165">Ensure that the web server on the development machine is running.</span></span> <span data-ttu-id="85b27-166">예를 들어 웹 호스팅 페이지(index.html)를 포함하는 루트 폴더로 이동하고 다음 코드를 실행합니다(serve npm 패키지를 사용한다고 가정).</span><span class="sxs-lookup"><span data-stu-id="85b27-166">For example, navigate to the root folder containing your web hosting page (index.html) and execute the following code (assuming you use serve npm package):</span></span>

    ```bash
    serve
    ```

1. <span data-ttu-id="85b27-167">개발 컴퓨터에서 Google Chrome을 열고 주소 표시줄에 다음 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-167">Open Google Chrome on your development machine and enter in the address bar the following text:</span></span>
    > <span data-ttu-id="85b27-168">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span><span class="sxs-lookup"><span data-stu-id="85b27-168">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span></span>
1. <span data-ttu-id="85b27-169">*USB 디바이스 검색* 확인란이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-169">Ensure that the *Discover USB devices* checkbox is enabled</span></span>
1. <span data-ttu-id="85b27-170">*포트 전달* 단추를 클릭하고 *포트 전달* 이 사용하도록 설정되어 있고 아래와 같이 *localhost:5000* 항목이 포함되어 있는지 확인합니다. ![Chrome 포트 전달 창](../images/chrome-port-forwarding.png)</span><span class="sxs-lookup"><span data-stu-id="85b27-170">Click the button *Port forwarding* and ensure that *Port forwarding* is enabled and contains an entry *localhost:5000* as shown below:  ![Chrome Port Forwarding window](../images/chrome-port-forwarding.png)</span></span>
1. <span data-ttu-id="85b27-171">연결된 Android 디바이스에서 Google Chrome 창을 열고 *http://localhost:5000* 으로 이동하면 큐브가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-171">In your connected Android device open a Google Chrome window and browse to *http://localhost:5000* and you should see the cube</span></span>
1. <span data-ttu-id="85b27-172">개발 컴퓨터의 Chrome에는 현재 디바이스와 여기에 열려있는 웹 페이지 목록이 표시됩니다. ![Chrome 검사 창](../images/chrome-inspect.png)</span><span class="sxs-lookup"><span data-stu-id="85b27-172">On your development machine, in Chrome, you will see your device and a list of web pages currently opened in there:  ![Chrome Inspect window](../images/chrome-inspect.png)</span></span>
1. <span data-ttu-id="85b27-173">항목 *http://localhost:5000* 옆에 있는 *검사* 단추를 클릭합니다. ![ Chrome DevTools 디버그 창](../images/chrome-debug.png)</span><span class="sxs-lookup"><span data-stu-id="85b27-173">Click the button *Inspect* next to an entry *http://localhost:5000*:  ![Chrome DevTools Debug window](../images/chrome-debug.png)</span></span>
1. <span data-ttu-id="85b27-174">[Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools)를 사용하여 페이지 디버그</span><span class="sxs-lookup"><span data-stu-id="85b27-174">Use the [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) to debug the page</span></span>

## <a name="takeaways"></a><span data-ttu-id="85b27-175">핵심 내용</span><span class="sxs-lookup"><span data-stu-id="85b27-175">Takeaways</span></span>

<span data-ttu-id="85b27-176">다음은 이 자습서에서 가장 중요한 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-176">The following are the most important takeaways from this tutorial:</span></span>
* <span data-ttu-id="85b27-177">Babylon.js를 사용하면 JavaScript를 사용하여 몰입형 환경을 간편하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-177">Babylon.js makes it easy to create immersive experiences using JavaScript</span></span>
* <span data-ttu-id="85b27-178">가상 장면을 만들려면 로우 코드를 작성하거나 새로운 기술을 배울 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-178">To create virtual scenes you don't need to write low-level code or learn a new technology</span></span>
* <span data-ttu-id="85b27-179">헤드셋을 구입할 필요 없이 WebXR 지원 브라우저를 사용하여 Mixed Reality 애플리케이션을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-179">You can build Mixed Reality applications with WebXR-supported browser without need to buy a headset</span></span>

## <a name="next-steps"></a><span data-ttu-id="85b27-180">다음 단계</span><span class="sxs-lookup"><span data-stu-id="85b27-180">Next steps</span></span>

<span data-ttu-id="85b27-181">축하합니다!</span><span class="sxs-lookup"><span data-stu-id="85b27-181">Congratulations!</span></span> <span data-ttu-id="85b27-182">일련의 babylon.js 자습서를 완료하고 다음을 수행하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="85b27-182">You've completed our series of babylon.js tutorials and learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="85b27-183">개발 환경 설정</span><span class="sxs-lookup"><span data-stu-id="85b27-183">Set up a development environment</span></span>
> * <span data-ttu-id="85b27-184">결과를 표시할 새 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="85b27-184">Create a new web page to display results</span></span>
> * <span data-ttu-id="85b27-185">기본 3D 요소를 만들고 상호 작용하는 babylon.js API</span><span class="sxs-lookup"><span data-stu-id="85b27-185">The babylon.js API to create and interact with basic 3D elements</span></span>
> * <span data-ttu-id="85b27-186">Windows Mixed Reality 시뮬레이터에서 애플리케이션 실행 및 테스트</span><span class="sxs-lookup"><span data-stu-id="85b27-186">Run and test the application in a Windows Mixed Reality Simulator</span></span>

<span data-ttu-id="85b27-187">Mixed Reality JavaScript 개발에 대한 자세한 내용은 [JavaScript 개발 개요](/javascript-development-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85b27-187">For more information on Mixed Reality JavaScript development see [JavaScript development overview](/javascript-development-overview.md).</span></span>
