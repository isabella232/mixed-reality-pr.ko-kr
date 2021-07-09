---
title: babylon.js 및 WebXR 자습서 소개
description: babylon.js를 사용하고 기본 Mixed Reality 애플리케이션을 만드는 방법을 알아보려면 이 과정을 완료하세요.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: mixed reality, javascript, 자습서, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, 몰입형 웹
ms.localizationpriority: high
ms.openlocfilehash: 2d3f59b2769f99a756c4f0c10df1d8a8604a595e
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600122"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a><span data-ttu-id="3f3ac-104">자습서: babylon.js를 사용하여 첫 번째 WebXR 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="3f3ac-104">Tutorial: Create your first WebXR application using babylon.js</span></span>

<span data-ttu-id="3f3ac-105">이 자습서에서는 babylon.js 및 Visual Studio Code를 사용하여 기본 Mixed Reality 앱을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-105">This tutorial will show you how to create a basic Mixed Reality app using babylon.js and Visual Studio Code.</span></span> <span data-ttu-id="3f3ac-106">빌드할 앱은 큐브를 렌더링하고, 다른 면을 뷰로 전환하고, 상호 작용을 추가하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-106">The app you're going to build will render a cube, let you rotate it to bring the other faces into view, and add interactions.</span></span> <span data-ttu-id="3f3ac-107">이 자습서에서는 다음과 같은 작업을 수행하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="3f3ac-108">개발 환경 설정</span><span class="sxs-lookup"><span data-stu-id="3f3ac-108">Set up a development environment</span></span>
> * <span data-ttu-id="3f3ac-109">기본 3D 요소를 만드는 babylon.js API</span><span class="sxs-lookup"><span data-stu-id="3f3ac-109">The babylon.js API to create basic 3D elements</span></span>  
> * <span data-ttu-id="3f3ac-110">새 웹 페이지 만들기</span><span class="sxs-lookup"><span data-stu-id="3f3ac-110">Create a new web page</span></span>
> * <span data-ttu-id="3f3ac-111">3D 요소와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="3f3ac-111">Interact with 3D elements</span></span>
> * <span data-ttu-id="3f3ac-112">Windows Mixed Reality 시뮬레이터에서 애플리케이션 실행</span><span class="sxs-lookup"><span data-stu-id="3f3ac-112">Run the application in a Windows Mixed Reality Simulator</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f3ac-113">필수 조건</span><span class="sxs-lookup"><span data-stu-id="3f3ac-113">Prerequisites</span></span>

* <span data-ttu-id="3f3ac-114">WebXR 지원 브라우저(예: [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md))</span><span class="sxs-lookup"><span data-stu-id="3f3ac-114">WebXR-supported browser, for example [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span></span>
* <span data-ttu-id="3f3ac-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 이상</span><span class="sxs-lookup"><span data-stu-id="3f3ac-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 or higher</span></span>
* [<span data-ttu-id="3f3ac-116">NodeJS</span><span class="sxs-lookup"><span data-stu-id="3f3ac-116">NodeJS</span></span>](https://nodejs.org/)
* <span data-ttu-id="3f3ac-117">선택 사항: Windows Mixed Reality 시뮬레이터를 사용하려는 경우 [Windows 10 크리에이터 업데이트](https://www.microsoft.com/software-download/windows10)</span><span class="sxs-lookup"><span data-stu-id="3f3ac-117">Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) if you want to use a Windows Mixed Reality Simulator</span></span>
* <span data-ttu-id="3f3ac-118">선택 사항: [Windows Mixed Reality 시뮬레이터](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="3f3ac-118">Optional: [Windows Mixed Reality simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="getting-started"></a><span data-ttu-id="3f3ac-119">시작</span><span class="sxs-lookup"><span data-stu-id="3f3ac-119">Getting started</span></span>

<span data-ttu-id="3f3ac-120">이 프로젝트를 처음부터 만들려면 Visual Studio Code(VSCode) 프로젝트부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-120">To create this project from scratch, start with a Visual Studio Code (VSCode) project.</span></span>

> [!NOTE]
> <span data-ttu-id="3f3ac-121">VSCode를 사용하는 것은 필수는 아니지만 자습서의 편의를 위해 사용할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-121">Using VSCode isn't mandatory, but we'll be using it for convenience throughout the tutorial.</span></span> <span data-ttu-id="3f3ac-122">경험이 많은 JavaScript 개발자는 가장 간단한 메모장을 비롯하여 원하는 다른 편집기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-122">More experienced JavaScript developers can use any other editor of their choice, even the simplest Notepad.</span></span>

1. <span data-ttu-id="3f3ac-123">[babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 단일 파일을 다운로드하거나 [공식 babylon.js 웹 사이트](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers)에서 찾을 수 있는 온라인 버전을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-123">Either download the [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) single file or use an online version that can be found on the [official babylon.js web site](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span></span> <span data-ttu-id="3f3ac-124">[GitHub](https://github.com/BabylonJS/Babylon.js)에서 전체 babylon.js 프로젝트를 복제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-124">You can also clone the entire babylon.js project from [GitHub](https://github.com/BabylonJS/Babylon.js)</span></span>
1. <span data-ttu-id="3f3ac-125">빈 파일을 만들고 html 페이지로 저장합니다(예: index.html).</span><span class="sxs-lookup"><span data-stu-id="3f3ac-125">Create an empty file and save it as html page, for example index.html</span></span>
1. <span data-ttu-id="3f3ac-126">기본 html 태그를 만들고 babylon.js javascript 파일을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-126">Create a basic html markup and reference the babylon.js javascript file.</span></span> <span data-ttu-id="3f3ac-127">최종 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-127">The final code is as shown below:</span></span>

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

1. <span data-ttu-id="3f3ac-128">body 안에 *canvas* HTML 요소를 추가하여 babylon.js의 콘텐츠를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-128">Add a *canvas* HTML element inside the body to render the contents of babylon.js.</span></span> <span data-ttu-id="3f3ac-129">canvas에는 나중에 JavaScript에서 이 HTML 요소에 액세스할 수 있는 id 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-129">Note that the canvas has an id attribute, which lets you access this HTML element from JavaScript later on.</span></span>

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

1. <span data-ttu-id="3f3ac-130">캔버스가 전체 웹 페이지를 차지합니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-130">The canvas occupies the entire web page.</span></span> <span data-ttu-id="3f3ac-131">이것으로 웹 페이지가 완성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-131">That completes our web page.</span></span> <span data-ttu-id="3f3ac-132">이제 웹 페이지가 준비되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-132">At this point, the web page is ready.</span></span> <span data-ttu-id="3f3ac-133">모든 브라우저에서 열 수 있으며, 아직 몰입형 환경이 없더라도 표시되는 오류가 없는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f3ac-133">You can open it in any browser and ensure there are no errors shown, though there is no immersive experience yet.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f3ac-134">다음 단계</span><span class="sxs-lookup"><span data-stu-id="3f3ac-134">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3f3ac-135">다음 자습서: 2. 장면 준비</span><span class="sxs-lookup"><span data-stu-id="3f3ac-135">Next Tutorial: 2. Prepare a scene</span></span>](prepare-scene-02.md)