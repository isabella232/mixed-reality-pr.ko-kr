---
title: MR 입력 213
description: Unity, Visual Studio 및 몰입 형 헤드셋을 사용 하 여이 코딩 자습서를 수행 하 여 동작 컨트롤러의 세부 정보를 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 동작 컨트롤러, 아카데미, 자습서
ms.openlocfilehash: 1cb53ed619a978e2aef17b5006b6254e5c7d3b9f53a39fbcb5932ebcc44ca98b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210228"
---
# <a name="mr-input-213-motion-controllers"></a>MR 입력 213: 모션 컨트롤러

>[!NOTE]
>Mixed Reality 아카데미 자습서는 HoloLens(1세대) 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다.  이러한 자습서는 HoloLens 2에 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 **_않습니다_**.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2에 대한 [새로운 자습서 시리즈](../develop/unity/tutorials/mr-learning-base-01.md)가 게시되었습니다.

혼합 현실 세계의 동작 컨트롤러는 다른 수준의 대화형 작업을 추가 합니다. [동작 컨트롤러](../design/motion-controllers.md)를 사용 하 여 집중 교육 및 즐거움를 응용 프로그램 환경에서 확장 하는 실제 상호 작용과 비슷하게 보다 자연스럽 게 개체와 직접 상호 작용할 수 있습니다.

MR 입력 213에서는 간단한 공간 그리기 환경을 만들어 동작 컨트롤러의 입력 이벤트를 탐색 합니다. 이 앱을 사용 하면 다양 한 유형의 브러시 및 색을 사용 하 여 3 차원 공간으로 그릴 수 있습니다.

## <a name="topics-covered-in-this-tutorial"></a>이 자습서에서 다루는 항목

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**컨트롤러 시각화**|**컨트롤러 입력 이벤트**|**사용자 지정 컨트롤러 및 UI**|
|Unity의 게임 모드 및 런타임에 동작 컨트롤러 모델을 렌더링 하는 방법에 대해 알아봅니다.|다양 한 종류의 단추 이벤트 및 해당 응용 프로그램을 이해 합니다.|컨트롤러 위에 UI 요소를 오버레이 하거나 완전히 사용자 지정 하는 방법에 대해 알아봅니다.|

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 입력 213: 모션 컨트롤러</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전에

### <a name="prerequisites"></a>필수 구성 요소

[이 페이지](../develop/install-the-tools.md)의 모던 헤드셋에 대 한 설치 검사 목록을 참조 하세요.

* 이 자습서에는 [Unity 2017.2.1 p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe) 가 필요 합니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일을 다운로드](https://github.com/Microsoft/MixedReality213/archive/master.zip) 하 고 바탕 화면에 파일을 추출 합니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/MixedReality213)있습니다.

## <a name="unity-setup"></a>Unity 설치

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>목표

* Windows Mixed Reality 개발용 Unity 최적화
* 혼합 현실 설치 카메라
* 설정 환경

### <a name="instructions"></a>지침

* Unity를 시작합니다.
* **열기** 를 선택합니다.
* 바탕 화면으로 이동 하 여 이전에 unarchived **MixedReality213** 폴더를 찾습니다.
* **폴더 선택** 을 클릭합니다.
* Unity에서 프로젝트 파일 로드를 마치면 Unity 편집기를 볼 수 있습니다.
* Unity에서 **파일 > 빌드 설정** 를 선택 합니다.

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* **플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 단추를 클릭 합니다.
* 대상 장치를 **모든 장치로** 설정
* Build Type(빌드 형식) 을 **D3D** 로 설정합니다.
* SDK를 **최신 설치** 로 설정
* **Unity c # 프로젝트** 확인
    * 이를 통해 Unity 프로젝트를 다시 빌드하지 않고 Visual Studio 프로젝트에서 스크립트 파일을 수정할 수 있습니다.
* **플레이어 설정** 를 클릭 합니다.
* **검사기** 패널에서 아래쪽으로 스크롤합니다.
* XR 설정에서 **지원 되는 가상 현실** 확인
* 가상 현실 sdk에서을 선택 **Windows Mixed Reality**

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* **빌드 설정** 창을 닫습니다.

### <a name="project-structure"></a>프로젝트 구조

이 자습서에서는 **[혼합 현실 Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 를 사용 합니다. [이 페이지](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)에서 릴리스를 찾을 수 있습니다.

![ProjectStructure](images/mr213-projectstructure-650px.png)

**참조용으로 완료 된 장면**

* **백그라운드** 폴더 아래에 두 개의 완료 된 Unity 장면을 찾을 수 있습니다.
    * **MixedReality213**: 단일 브러시를 사용 하 여 완료 된 장면
    * **MixedReality213Advanced**: 여러 브러시를 사용 하 여 고급 디자인을 위한 장면 완료

**자습서에 대 한 새 장면 설정**

* Unity에서 **파일 > 새 장면** 을 클릭 합니다.
* **기본 카메라** 및 **방향성 광원** 삭제
* **Project 패널** 에서 다음 prefabs를 검색 하 여 **계층** 패널로 끌어옵니다.
    * Asset/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * 자산/AppPrefabs/**환경**

    ![카메라 및 환경](images/mr213-cameraenvironment-300px.jpg)

* 혼합 현실 Toolkit에는 두 가지 카메라 prefabs 있습니다.
    * **MixedRealityCamera. prefab**: 카메라 전용
    * **MixedRealityCameraParent prefab**: 카메라 + Teleportation + 경계
    * 이 자습서에서는 teleportation 기능 없이 **MixedRealityCamera** 를 사용 합니다. 이로 인해 사용자가 접지 되도록 기본적인 층을 포함 하는 간단한 **환경** prefab를 추가 했습니다.
    * **MixedRealityCameraParent** 를 사용 하 여 teleportation에 대 한 자세한 내용은 [고급 디자인-teleportation 및 locomotion](#advanced-design---teleportation-and-locomotion) 를 참조 하세요.

**Skybox 설정**

* **창 > 조명 >** 를 클릭 설정
* **Skybox 재질 필드** 의 오른쪽에 있는 원을 클릭 합니다.
* ' 회색 '을 입력 하 고 **SkyboxGray** (자산/AppPrefabs/Support/재질/SkyboxGray)를 선택 합니다.

    ![Skybox 설정](images/mr123-skyboxsetting-400px.jpg)

* 할당 된 회색 그라데이션 Skybox을 볼 수 있도록 **Skybox** 옵션을 선택 합니다.

    ![Skybox 옵션 설정/해제](images/mr213-skyboxcheck-400px.jpg)

* MixedRealityCamera, 환경 및 회색 skybox이 포함 된 장면을 다음과 같이 표시 됩니다.

    ![MixedReality213 환경](images/mr213-environment-600px.jpg)

* **파일 > 장면 저장을** 클릭 합니다.
* 모든 이름의 장면 폴더 아래에 장면 **저장**

## <a name="chapter-1---controller-visualization"></a>1 장-컨트롤러 시각화

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>목표

* Unity의 게임 모드 및 런타임에 동작 컨트롤러 모델을 렌더링 하는 방법에 대해 알아봅니다.

Windows Mixed Reality는 컨트롤러 시각화를 위한 애니메이션 컨트롤러 모델을 제공 합니다. 앱에서 컨트롤러 시각화에 대해 수행할 수 있는 몇 가지 방법이 있습니다.

* 기본값-수정 하지 않고 기본 컨트롤러 사용
* 하이브리드-기본 컨트롤러를 사용 하지만 일부 요소 또는 겹쳐 있는 UI 구성 요소를 사용자 지정 합니다.
* 대체-컨트롤러에 대해 사용자 지정 된 사용자 지정 3D 모델 사용

이 장에서는 이러한 컨트롤러 사용자 지정의 예제에 대해 알아봅니다.

### <a name="instructions"></a>지침

* **Project** 패널에서 검색 상자에 **motioncontrollers** 를 입력 합니다. 자산/HoloToolkit/입력/Prefabs/에서 찾을 수도 있습니다.
* **Motioncontrollers** Prefab을 **계층** 패널로 끌어 옵니다.
* **계층** 패널에서 **motioncontrollers** prefab를 클릭 합니다.

**MotionControllers prefab**

**Motioncontrollers** prefab에는 대체 컨트롤러 모델용 슬롯을 제공 하는 **Motioncontroller시각기** 스크립트가 있습니다. 손 또는 소드와 같은 사용자 지정 3D 모델을 할당 하 고 ' 항상 대체 왼쪽/오른쪽 모델 사용 '을 선택 하면 기본 모델 대신 해당 모델이 표시 됩니다. 4 장에서이 슬롯을 사용 하 여 컨트롤러 모델을 브러시로 바꿉니다.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**지침**

* **검사기** 패널에서 **Motioncontrollervisualizer** 스크립트를 두 번 클릭 하 여 Visual Studio 코드를 확인 합니다.

**MotionControllerVisualizer 도우미 스크립트**

**Motioncontrollervisualizer** 및 **Motioncontrollervisualizer** 클래스는 기본 컨트롤러 모델을 액세스 & 수정 하는 방법을 제공 합니다. **Motioncontrollervisualizer** 는 Unity의 **InteractionSourceDetected** 이벤트를 구독 하 고 발견 되 면 컨트롤러 모델을 자동으로 인스턴스화합니다.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

컨트롤러 모델은 고 지 수 [설정](https://github.com/KhronosGroup/glTF)에 따라 제공 됩니다. 이 형식은 공통 형식을 제공 하기 위해 만들어졌지만 3D 자산의 전송 및 압축 풀기의 프로세스를 개선 합니다. 이 경우 가능한 한 원활 하 게 사용자 환경을 만들고 사용자가 사용 중일 수 있는 동작 컨트롤러의 버전을 보장 하지 않기 때문에 런타임에 컨트롤러 모델을 검색 하 고 로드 해야 합니다. 이 과정에서는 혼합 현실 Toolkit를 통해 Khronos 그룹의 [unity글 tf 프로젝트](https://github.com/KhronosGroup/UnityGLTF)버전을 사용 합니다.

컨트롤러가 전달 된 후에는 스크립트에서 **Motioncontrollerinfo** 를 사용 하 여 특정 컨트롤러 요소에 대 한 변환을 찾아 스스로 위치를 올바르게 지정할 수 있습니다.

이후 장에서는 이러한 스크립트를 사용 하 여 UI 요소를 컨트롤러에 연결 하는 방법을 배웁니다.

*일부 스크립트에서는 #if 된 코드 블록을 찾을 수 있습니다 **. UNITY_EDITOR** 또는 **UNITY_WSA**. 이러한 코드 블록은 Windows에 배포할 때 UWP 런타임에만 실행 됩니다. Unity 편집기와 UWP 앱 런타임에서 사용 하는 Api 집합이 다르기 때문입니다.*

* 장면을 **저장** 하 고 **재생** 단추를 클릭 합니다.

헤드셋에서 이동 컨트롤러를 사용 하는 장면을 볼 수 있습니다. 단추 클릭, 엄지 스틱 움직임 및 터치 패드 touch 강조 표시에 대 한 자세한 애니메이션을 볼 수 있습니다.

![MR213_Controller 시각화 기본값](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>2 장-컨트롤러에 UI 요소 연결

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>목표

* 동작 컨트롤러의 요소에 대 한 자세한 정보
* 컨트롤러의 특정 부분에 개체를 연결 하는 방법 알아보기

이 장에서는 사용자가 언제 든 지 쉽게 액세스 하 고 조작할 수 있는 사용자 인터페이스 요소를 컨트롤러에 추가 하는 방법을 배웁니다. 또한 터치 패드 입력을 사용 하 여 간단한 색 선택 UI를 추가 하는 방법을 알아봅니다.

### <a name="instructions"></a>지침

* **Project** 패널에서 **motioncontrollerinfo** 스크립트를 검색 합니다.
* 검색 결과에서 **Motioncontrollerinfo** 스크립트를 두 번 클릭 하 여 Visual Studio 코드를 확인 합니다.

**MotionControllerInfo 스크립트**

첫 번째 단계는 UI를 연결 하려는 컨트롤러의 요소를 선택 하는 것입니다. 이러한 요소는 **Motioncontrollerinfo. cs** 의 **controllerelementenum** 에 정의 되어 있습니다.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **Home**
* **메뉴**
* **잡습니다**
* **사용해**
* **Select**
* **터치패드**
* **가리키기 포즈** –이 요소는 정방향 방향을 가리키는 컨트롤러의 팁을 나타냅니다.

**지침**

* **Project** 패널에서 **AttachToController** 스크립트를 검색 합니다.
* 검색 결과에서 **AttachToController** 스크립트를 두 번 클릭 하 여 Visual Studio 코드를 확인 합니다.

**AttachToController 스크립트**

**AttachToController** 스크립트는 및 요소를 통해 지정 된 컨트롤러에 개체를 연결 하는 간단한 방법을 제공 합니다.

**AttachElementToController ()** 에서

* **Motioncontrollerinfo를** 사용 하 여 사용 하기
* **Motioncontrollerinfo. TryGetElement ()를** 사용 하 여 컨트롤러의 특정 요소를 가져옵니다.
* 컨트롤러 모델에서 요소의 변환을 검색 한 후 해당 개체의 부모 개체를 부모로 설정 하 고 개체의 로컬 위치를 0으로 & 설정 합니다.

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type &quot; + element + &quot; under controller &quot; + newController.ControllerParent.name + &quot;; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

**AttachToController** 스크립트를 사용 하는 가장 간단한 방법은 **Color kerwheel** 의 경우와 마찬가지로이 스크립트에서 상속 하는 것입니다. **OnAttachToController** 및 **OnDetachFromController** 함수를 재정의 하 여 컨트롤러를 검색/연결 해제 하는 경우 설정/분석을 수행 합니다.

**지침**

* **Project** 패널에서 **colorpickerwheel** 검색 상자에를 입력 합니다. 자산/AppPrefabs/에서 찾을 수도 있습니다.
* **Colorprefab Kerwheel** 을 **계층** 패널로 끌어 옵니다.
* **계층** 패널에서 **Colorpickerwheel** prefab를 클릭 합니다.
* **검사기** 패널에서 **Colorpickerwheel** 스크립트를 두 번 클릭 하 여 Visual Studio 코드를 확인 합니다.

![Colorprefab Kerwheel](images/mr213-colorpickerwheel-1000px.jpg)

**Color Kerwheel 스크립트**

**ColorAttachToController Kerwheel** 은 를 상속 하므로 **검사기** 패널에 **손** 및 **요소가** 표시 됩니다. UI를 왼쪽 컨트롤러의 터치 패드 요소에 연결 합니다.

![Color Kerwheel 스크립트](images/mr213-attachtocontroller-300px.jpg)

**Colorpickerwheel** 은 **OnAttachToController** 및 **OnDetachFromController** 를 재정의 하 여 입력 이벤트를 구독 합니다 .이 이벤트는 다음 챕터에서 터치 패드 입력을 사용 하 여 색을 선택 하는 데 사용 됩니다.

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* 장면을 **저장** 하 고 **재생** 단추를 클릭 합니다.

**개체를 컨트롤러에 연결 하는 다른 방법**

스크립트는 **AttachToController** 에서 상속 하 고 **OnAttachToController** 를 재정의 하는 것이 좋습니다. 그러나 이것이 항상 가능 하지는 않습니다. 다른 방법으로는 독립 실행형 구성 요소로 사용 합니다. 이는 스크립트를 리팩터링 하지 않고 컨트롤러에 기존 prefab를 연결 하려는 경우에 유용할 수 있습니다. 설치를 수행 하기 전에 클래스에서 IsAttached을 true로 설정할 때까지 대기 하기만 하면 됩니다. 이 작업을 수행 하는 가장 간단한 방법은 ' Start '에 코 루틴를 사용 하는 것입니다.

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>3 장-터치 패드 입력 작업

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>목표

* 터치 패드 입력 데이터 이벤트를 가져오는 방법 알아보기
* 앱 환경에 대 한 터치 패드 축 위치 정보를 사용 하는 방법을 알아봅니다.

### <a name="instructions"></a>지침

* **계층** 패널에서 **Colorpickerwheel** 을 클릭 합니다.
* **검사기** 패널의 **애니메이터** 아래에서 **ColorPickerWheelController** 를 두 번 클릭 합니다.
* **애니메이터** 탭이 열려 있는 것을 볼 수 있습니다.

**Unity 애니메이션 컨트롤러를 사용 하 여 UI 표시/숨기기**

애니메이션을 사용 하 여 **Colorpickerwheel** UI를 표시 하거나 숨기려면 [Unity의 애니메이션 시스템](https://docs.unity3d.com/Manual/AnimationOverview.html)을 사용 합니다. **Colorpickerwheel** 의 **Visible** 속성을 true 또는 false 트리거로 설정 하면 애니메이션 트리거가 **표시** 되 고 **숨겨집니다** . **표시** 및 **숨기기** 매개 변수는 **ColorPickerWheelController** 애니메이션 컨트롤러에서 정의 됩니다.

![Unity 애니메이션 컨트롤러](images/mr123-animationcontroller-550px.jpg)

**지침**

* **계층** 패널에서 **Colorpickerwheel** prefab를 선택 합니다.
* **검사기** 패널에서 **Colorpickerwheel** 스크립트를 두 번 클릭 하 여 Visual Studio 코드를 확인 합니다.

**Color Kerwheel 스크립트**

**Color Kerwheel** 은 Unity 이벤트를 수신 하는 Unity의 **InteractionSourceUpdated** 이벤트를 구독 합니다.

**InteractionSourceUpdated ()** 에서 스크립트는 먼저 다음을 확인 합니다.

* 는 실제로 터치 패드 이벤트 (.obj. 상태)입니다.**touchpadTouched**)
* 왼쪽 컨트롤러에서 생성 됩니다 **(obj. source. 손**)

둘 다 true이면 터치 패드 위치(obj.state.**touchpadPosition**)은 **selectorPosition** 에 할당됩니다.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

**Update()** 에서는 **표시되는** 속성에 따라 색 선택기의 animator 구성 요소에서 애니메이션 트리거 표시 및 숨기기를 트리거합니다.

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

**Update()에서** **selectorPosition은** UV 위치를 반환하는 색 휠의 메시 충돌체에서 광선을 캐스팅하는 데 사용됩니다. 그런 다음, 이 위치를 사용하여 색 휠 질감의 픽셀 좌표 및 색 값을 찾을 수 있습니다. 이 값은 **SelectedColor** 속성을 통해 다른 스크립트에서 액세스할 수 있습니다.

![Color Picker Wheel Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>4장 - 컨트롤러 모델 재정의

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>목표

* 사용자 지정 3D 모델을 사용하여 컨트롤러 모델을 재정의하는 방법을 알아봅니다.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>지침

* **계층 패널에서** **MotionControllers를** 클릭합니다.
* **대체 오른쪽 컨트롤러** 필드의 오른쪽에 있는 원을 클릭합니다.
* **'BrushController'를** 입력하고 결과에서 프리팹을 선택합니다. 자산/AppPrefabs/**BrushController** 에서 찾을 수 있습니다.
* **항상 대체 올바른 모델 사용** 확인

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

**BrushController** 프리팹은 **계층 패널에** 포함될 필요가 없습니다. 그러나 자식 구성 요소를 확인하려면 다음을 수행합니다.

* **Project** 패널에서 **BrushController를** 입력하고 **BrushController** 프리팹을 계층 **패널로 끌어다 붙입니다.**

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

**BrushController** 에서 **팁** 구성 요소를 찾을 수 있습니다. 변환을 사용하여 그리기 선을 시작/중지합니다.

* 계층 패널에서 **BrushController를** **삭제합니다.**
* 장면을 **저장하고** **재생** 단추를 클릭합니다. 브러시 모델이 오른쪽 모션 컨트롤러로 대체된 것을 볼 수 있습니다.

## <a name="chapter-5---painting-with-select-input"></a>5장 - 선택 입력으로 그리기

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>목표

* Select 단추 이벤트를 사용하여 선 그리기를 시작하고 중지하는 방법을 알아봅니다.

### <a name="instructions"></a>지침

* **Project** 패널에서 **BrushController** 프리팹을 검색합니다.
* **검사기** 패널에서 **BrushController** 스크립트를 두 번 클릭하여 코드를 Visual Studio

**BrushController 스크립트**

**BrushController는** InteractionManager의 **InteractionSourcePressed** 및 **InteractionSourceReleased 이벤트를 구독합니다.** **InteractionSourcePressed** 이벤트가 트리거되면 브러시의 **Draw** 속성이 true로 설정됩니다. **InteractionSourceReleased** 이벤트가 트리거되면 브러시의 **Draw** 속성이 false로 설정됩니다.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

**Draw는** true로 설정되지만 브러시는 인스턴스화된 Unity **LineRenderer** 에 점을 생성합니다. 이 프리팹에 대한 참조는 브러시의 스트로크 프리팹 필드에 **유지됩니다.**

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

색 선택기 휠 UI에서 현재 선택한 색을 사용하려면 **BrushController에** **ColorPickerWheel** 개체에 대한 참조가 있어야 합니다. **BrushController** 프리팹은 런타임에 대체 컨트롤러로 인스턴스화되므로 장면의 개체에 대한 참조는 런타임에 설정해야 합니다. 이 경우 **GameObject.FindObjectOfType을** 사용하여 **ColorPickerWheel** 을 찾습니다.

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* 장면을 **저장하고** **재생** 단추를 클릭합니다. 오른쪽 컨트롤러의 선택 단추를 사용하여 선을 그리고 그릴 수 있습니다.

## <a name="chapter-6---object-spawning-with-select-input"></a>6장 - Select 입력을 통해 개체 생성

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>목표

* 선택 및 파악 단추 입력 이벤트를 사용하는 방법 알아보기
* 개체를 인스턴스화하는 방법 알아보기

### <a name="instructions"></a>지침

* **Project** 패널의 검색 상자에 **ObjectSpawner를** 입력합니다. 자산/AppPrefabs/에서 찾을 수도 있습니다.
* **ObjectSpawner 프리팹을** **계층** 패널로 끕니다.
* **계층** 패널에서 **ObjectSpawner를** 클릭합니다.
* **ObjectSpawner에는** 색 **소스** 라는 필드가 있습니다.
* **Hierarchy** 패널에서 **ColorPickerWheel** 참조를 이 필드로 끌어 들입니다.

    ![개체 생성자 검사기](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* 계층 패널에서 **ObjectSpawner** **프리팹을** 클릭합니다.
* **검사기** 패널에서 **ObjectSpawner** 스크립트를 두 번 클릭하여 Visual Studio 코드를 확인합니다.

**ObjectSpawner 스크립트**

**ObjectSpawner는** 기본 메시(큐브, 구, 실린더)의 복사본을 공간으로 인스턴스화합니다. **InteractionSourcePressed가** 감지되면 전달 여부를 확인하고 **InteractionSourcePressType.Type.Type 또는** **InteractionSourcePressType.Select** 이벤트인지 여부를 확인합니다.

의 **경우, 이** 이벤트는 현재 메시 형식(구, 큐브, 실린더)의 인덱스를 증가합니다.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

**Select** 이벤트의 경우 **SpawnObject()에서** 새 개체가 인스턴스화되고 부모가 없는 것으로 전 세계에 릴리스됩니다.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner는** **ColorPickerWheel을** 사용하여 표시 개체 재질의 색을 설정합니다. 생성된 개체에는 이 재질의 인스턴스가 제공되므로 색을 유지합니다.

* 장면을 **저장하고** **재생** 단추를 클릭합니다.

이해 단추로 개체를 변경하고 선택 단추를 사용하여 개체를 생성할 수 있습니다.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Mixed Reality 포털 앱 빌드 및 배포

* Unity에서 **파일 > 빌드 설정** 선택합니다.
* **열린 장면 추가를** 클릭하여 현재 장면을 **빌드의 장면에 추가합니다.**
* **빌드** 를 클릭한 다음
* "App"이라는 **새 폴더를** 만듭니다.
* **App** 폴더를 한 번 클릭합니다.
* **폴더 선택** 을 클릭합니다.
* Unity가 완료되면 파일 탐색기 창이 나타납니다.
* **앱** 폴더를 엽니다.
* **YourSceneName.sln** Visual Studio Solution 파일을 두 번 클릭합니다.
* Visual Studio 위쪽 도구 모음을 사용하여 대상을 디버그에서 **릴리스로,** ARM에서 **X64로** 변경합니다.
* 디바이스 단추 옆의 드롭다운 화살표를 클릭하고 **로컬 컴퓨터** 를 선택합니다.
* 메뉴에서 **디버그 -> 디버깅하지 않고 시작을** 클릭하거나 **Ctrl + F5** 키를 누릅니다.

이제 앱이 빌드되고 Mixed Reality 포털 설치됩니다. Mixed Reality 포털 시작 메뉴 통해 다시 시작할 수 있습니다.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>고급 디자인 - 방사형 레이아웃이 있는 브러시 도구

![MixedReality213 Main](images/mr213-main-600px.jpg)

이 장에서는 기본 모션 컨트롤러 모델을 사용자 지정 브러시 도구 컬렉션으로 바꾸는 방법을 알아봅니다. 참조를 위해 Scenes **폴더에서** 완료된 장면 **MixedReality213고급을** 찾을 수 있습니다.

### <a name="instructions"></a>지침

* **Project** 패널의 검색 상자에 **BrushSelector를** 입력합니다. 자산/AppPrefabs/에서 찾을 수도 있습니다.
* **BrushSelector** 프리팹을 **계층** 패널로 끕니다.
* 조직의 경우 Brushes라는 빈 GameObject를 **만듭니다.**
* **Project** 패널에서 **브러시로** 다음 프리팹 끌기
    * Assets/AppPrefabs/**BrushFat**
    * Assets/AppPrefabs/**BrushThin**
    * Assets/AppPrefabs/**Eraser**
    * Assets/AppPrefabs/**MarkerFat**
    * Assets/AppPrefabs/**MarkerThin**
    * Assets/AppPrefabs/**연필**

    ![브러시](images/mixedreality213-brushes-250px.png)

* **계층 패널에서** **MotionControllers** 프리팹을 클릭합니다.
* **[검사기]** 패널의 **동작 컨트롤러 시각화 도우미에서** **항상 대체 오른쪽 모델 사용의** 선택을 취소합니다.
* 계층 **패널에서** **BrushSelector를** 클릭합니다.
* **BrushSelector에는** **ColorPicker라는 필드가** 있습니다.
* **Hierarchy** 패널에서 **ColorPickerWheel을** **Inspector** 패널의 **ColorPicker** 필드로 끕다.

    ![브러시 선택기로 ColorPickerWheel 할당](images/mr213-brushselector-500px.jpg)

* 계층 **패널의** **BrushSelector** 프리팹에서 **Menu** 개체를 선택합니다.
* **검사기** 패널의 **LineObjectCollection** 구성 요소 아래에서 **개체** 배열 드롭다운을 엽니다. 6개의 빈 슬롯이 표시됩니다.
* **Hierarchy** 패널에서 **Brushes** GameObject 아래에 있는 각 프리팹을 순서에 따라 이러한 슬롯으로 끕니다. (프로젝트 폴더의 프리팹이 아니라 장면에서 프리팹을 끌어와야 합니다.)

![브러시 선택기](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector 프리팹**

**BrushSelector는** **AttachToController** 를 상속하기 때문에 **Inspector** 패널에 **Handedness** 및 **Element** 옵션을 표시합니다. **오른쪽** 및 **포인팅 자세를** 선택하여 브러시 도구를 앞으로 방향으로 오른쪽 컨트롤러에 연결했습니다.

**BrushSelector는** 다음 두 유틸리티를 사용합니다.

* **타원:** 타원 모양을 따라 공간의 점을 생성하는 데 사용됩니다.
* **LineObjectCollection**: 모든 Line 클래스(예: Ellipse)에서 생성된 점을 사용하여 개체를 배포합니다. Ellipse 셰이프를 따라 브러시를 배치하는 데 사용할 것입니다.

이러한 유틸리티를 결합하면 방사형 메뉴를 만드는 데 사용할 수 있습니다.

**LineObjectCollection 스크립트**

**LineObjectCollection에는** 해당 선을 따라 분산된 개체의 크기, 위치 및 회전에 대한 컨트롤이 있습니다. 브러시 선택기 같은 방사형 메뉴를 만드는 데 유용합니다. 가운데에서 선택한 위치에 접근할 때 아무 것도 확장하지 않는 브러시의 모양을 만들기 위해 **ObjectScale** 곡선은 가운데에서 최고점이 되며 가장자리에서 탭이 끊어지게 합니다.

**BrushSelector 스크립트**

**BrushSelector** 의 경우 절차적 애니메이션을 사용하도록 선택했습니다. 먼저 브러시 모델은 **LineObjectCollection** 스크립트를 통해 타원으로 배포됩니다. 그런 다음 각 브러시는 선택 항목에 따라 변경되는 **DisplayMode** 값에 따라 사용자의 손에서 위치를 유지 관리합니다. 사용자가 브러시를 선택할 때 브러시 위치 전환이 중단될 가능성이 높기 때문에 절차적 접근 방식을 선택했습니다. Mecanim 애니메이션은 중단을 정상적으로 처리할 수 있지만 간단한 Lerp 작업보다 더 복잡한 경향이 있습니다.

**BrushSelector는** 둘의 조합을 사용합니다. 터치 패드 입력이 감지되면 브러시 옵션이 표시되고 방사형 메뉴를 따라 확장됩니다. 제한 시간(사용자가 선택했음을 나타낸 것)이 지나면 브러시 옵션이 다시 축소되어 선택한 브러시만 남게 합니다.

**터치 패드 입력 시각화**

컨트롤러 모델이 완전히 교체된 경우에도 원래 모델 입력에 입력을 표시하는 것이 유용할 수 있습니다. 이렇게 하면 실제로 사용자의 작업을 파악하는 데 도움이 됩니다. **BrushSelector의** 경우 입력을 받을 때 터치 패드를 간단하게 표시하도록 선택했습니다. 이 작업은 컨트롤러에서 Touchpad 요소를 검색하고, 재질을 사용자 지정 재질로 대체한 다음, 터치 패드 입력을 마지막으로 받은 시간을 기준으로 해당 재질의 색에 그라데이션을 적용하여 수행되었습니다.

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**터치 패드 입력을 사용하여 브러시 도구 선택**

브러시 선택기가 터치 패드의 누른 입력을 감지하면 입력 위치를 확인하여 왼쪽 또는 오른쪽에 있는지 확인합니다.

**SelectPressedAmount를 통해 스트로크 두께**

**InteractionSourcePressed()** 의 **InteractionSourcePressType.Select** 이벤트 대신 **selectPressedAmount** 를 통해 누른 금액의 아날로그 값을 얻을 수 있습니다. 이 값은 **InteractionSourceUpdated()** 에서 검색할 수 있습니다.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**지우개 스크립트**

**지우개는** 기본 Brush의 **DrawOverTime()** 함수를 재정의하는 특수한 유형의 **브러시입니다.** 그리기는 true이지만 지우개는 팁이 기존 브러시 스트로크와 교차하는지 확인합니다. 이 경우 축소 및 삭제할 큐에 추가됩니다.

## <a name="advanced-design---teleportation-and-locomotion"></a>고급 디자인 - 원격 보고 및 분해

사용자가 엄지스틱을 사용하여 원격 전송을 사용하여 장면 주변을 이동할 수 있도록 하려면 **MixedRealityCamera 대신 MixedRealityCameraParent를** 사용합니다.  또한 **InputManager** 및 **DefaultCursor 를** 추가해야 합니다. **MixedRealityCameraParent에는** 이미 **MotionControllers** 및 **Boundary가** 자식 구성 요소로 포함되어 있기 때문에 기존 **MotionControllers** 및 **환경** 프리팹을 제거해야 합니다.

### <a name="instructions"></a>지침

* 계층 **구조** 패널에서 **MixedRealityCamera**, **Environment** 및 **MotionControllers를 삭제합니다.**
* Project **패널에서** 다음 프리팹을 검색하여 계층 패널로 끌어 **다.**
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

    ![혼합 현실 카메라 부모](images/mr213-cameraparent-300px.png)

* 계층 **구조** 패널에서 입력 **관리자를** 클릭합니다.
* **검사기** 패널에서 **간단한 단일 포인터 선택기** 섹션까지 아래로 스크롤합니다.
* 계층 **구조** 패널에서 **DefaultCursor를** 커서 필드로 끕니다. 

    ![DefaultCursor 할당](images/mr213-defaultcursor-500px.png)

* 장면을 **저장하고** **재생** 단추를 클릭합니다. 엄지스틱을 사용하여 왼쪽/오른쪽 또는 원격 포트를 회전할 수 있습니다.

## <a name="the-end"></a>끝

이 자습서의 끝입니다. 다음에 대해 알아보았습니다.

* Unity의 게임 모드 및 런타임에서 모션 컨트롤러 모델을 작업하는 방법입니다.
* 다양한 유형의 단추 이벤트 및 해당 애플리케이션을 사용하는 방법입니다.
* 컨트롤러 위에 UI 요소를 오버레이하거나 완전히 사용자 지정하는 방법입니다.

이제 모션 컨트롤러를 사용하여 사용자 고유의 몰입형 환경을 만들 준비가 되었습니다.

## <a name="completed-scenes"></a>완료된 장면

* Unity의 **Project** 패널에서 **Scenes** 폴더를 클릭합니다.
* 두 Unity 장면 **MixedReality213** 및 **MixedReality213고급 를** 찾을 수 있습니다.
    * **MixedReality213:** 단일 브러시로 완성된 장면
    * **MixedReality213고급:** select 단추의 press amount 예제가 있는 여러 브러시가 있는 완료된 장면

## <a name="see-also"></a>추가 정보

* [MR 입력 213 프로젝트 파일](https://github.com/Microsoft/MixedReality213)
* [Mixed Reality Toolkit - 모션 컨트롤러 테스트 장면](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Mixed Reality Toolkit - 잡기 메커니즘](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [모션 컨트롤러 개발 지침](../design/motion-controllers.md)