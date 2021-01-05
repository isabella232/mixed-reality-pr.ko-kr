---
ms.openlocfilehash: eb51caa4caf0d425b5e49c3abca2a523b08fc312
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717667"
---
# <a name="426"></a>[<span data-ttu-id="ffe19-101">4.26</span><span class="sxs-lookup"><span data-stu-id="ffe19-101">4.26</span></span>](#tab/426) 

## <a name="pv-camera-feed-setup"></a><span data-ttu-id="ffe19-102">PV 카메라 피드 설정</span><span class="sxs-lookup"><span data-stu-id="ffe19-102">PV Camera Feed Setup</span></span>

- <span data-ttu-id="ffe19-103">**프로젝트 설정 > HoloLens** 에서 **웹캠** 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-103">In **Project Settings > HoloLens**, enable the **Webcam** capability:</span></span>

![웹캠 속성이 강조 표시된 HoloLens 프로젝트 설정의 스크린샷](../images/unreal-pvc-img-01.png)

- <span data-ttu-id="ffe19-105">"CamCapture"라는 새 행위자를 만들고 카메라 피드를 렌더링하는 평면을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-105">Create a new actor called “CamCapture” and add a plane to render the camera feed:</span></span>

![평면이 추가된 행위자의 스크린샷](../images/unreal-pvc-img-02.png)

- <span data-ttu-id="ffe19-107">장면에 행위자를 추가하고, Texture Object 매개 변수와 텍스처 샘플을 사용하여 CamTextureMaterial이라는 새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-107">Add the actor to your scene, create a new material called CamTextureMaterial with a Texture Object Parameter, and a texture sample.</span></span>  <span data-ttu-id="ffe19-108">텍스처의 rgb 데이터를 출력 발광 색으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-108">Send the texture’s rgb data to the output emissive color:</span></span>

![재질 및 텍스처 샘플 청사진](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a><span data-ttu-id="ffe19-110">PV 카메라 피드 렌더링</span><span class="sxs-lookup"><span data-stu-id="ffe19-110">Rendering the PV Camera Feed</span></span>

- <span data-ttu-id="ffe19-111">CamCapture 청사진에서 PV 카메라를 켭니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-111">In the CamCapture blueprint, turn on the PV Camera:</span></span>

![PV 카메라가 켜진 Toggle ARCapture 함수의 청사진](../images/unreal-pvc-img-04.png)

- <span data-ttu-id="ffe19-113">CamTextureMaterial에서 동적 재질 인스턴스를 만들고 이 재질을 행위자의 평면에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-113">Create a dynamic material instance from CamTextureMaterial and assign this material to the actor’s plane:</span></span>

![Create Dynamic Material Instance 함수의 청사진](../images/unreal-pvc-img-05.png)

- <span data-ttu-id="ffe19-115">카메라 피드에서 텍스처를 가져와 동적 재질에 할당합니다(유효한 경우).</span><span class="sxs-lookup"><span data-stu-id="ffe19-115">Get the texture from the camera feed and assign it to the dynamic material if it's valid.</span></span>  <span data-ttu-id="ffe19-116">텍스처가 유효하지 않으면 타이머를 시작하고, 타이머 시간이 끝난 후 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-116">If the texture isn't valid, start a timer and try again after the timeout:</span></span>

![동적 재질에 할당된 카메라 텍스처의 청사진](../images/unreal-pvc-img-06.png)

- <span data-ttu-id="ffe19-118">마지막으로 평면의 크기를 카메라 이미지의 가로 세로 비율로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-118">Finally, scale the plane by the camera image’s aspect ratio:</span></span>

![카메라 이미지의 가로 세로 비율에 맞게 크기가 조정된 평면의 청사진](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a><span data-ttu-id="ffe19-120">세계 공간에서 카메라 위치 찾기</span><span class="sxs-lookup"><span data-stu-id="ffe19-120">Find Camera Positions in World Space</span></span>

<span data-ttu-id="ffe19-121">HoloLens 2의 카메라는 디바이스의 머리 추적에서 수직으로 오프셋됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-121">The camera on the HoloLens 2 is offset vertically from the device’s head tracking.</span></span>  <span data-ttu-id="ffe19-122">오프셋을 고려하여 세계 공간에서 카메라를 찾는 몇 가지 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-122">A few functions exist to locate the camera in world space to account for the offset.</span></span>

<span data-ttu-id="ffe19-123">GetPVCameraToWorldTransform은 PV 카메라의 세계 공간에서 변환을 가져오고 카메라 렌즈에 다음과 같이 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-123">GetPVCameraToWorldTransform gets the transform in world space of the PV Camera and will be positioned on the camera lens:</span></span>

![Get PVCamera to World Transform 함수의 청사진](../images/unreal-pvc-img-08.png)

<span data-ttu-id="ffe19-125">GetWorldSpaceRayFromCameraPoint는 카메라 렌즈의 광선을 Unreal 세계 공간의 장면으로 투사하여 카메라 프레임에서 픽셀의 콘텐츠를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-125">GetWorldSpaceRayFromCameraPoint casts a ray from the camera lens into the scene in Unreal world space to find a pixel's content in the camera frame:</span></span>

![Get World Space Ray from Camera Point의 청사진](../images/unreal-pvc-img-09.png)

<span data-ttu-id="ffe19-127">GetPVCameraIntrinsics는 카메라 프레임에서 컴퓨터 비전 처리를 수행할 때 사용할 수 있는 카메라 내장 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-127">GetPVCameraIntrinsics returns the camera intrinsic values, which can be used when doing computer vision processing on a camera frame:</span></span>

![Get PVCamera Intrinsics 함수의 청사진](../images/unreal-pvc-img-10.png)

<span data-ttu-id="ffe19-129">세계 공간의 특정 픽셀 좌표에 무엇이 있는지 알아내려면 세계 공간 광선과 함께 선 추적을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-129">To find what exists in world space at a particular pixel coordinate, use a line trace with the world space ray:</span></span>

![세계 공간의 특정 좌표에 무엇이 있는지 알아내는 데 사용되는 세계 공간 광선의 청사진](../images/unreal-pvc-img-11.png)

<span data-ttu-id="ffe19-131">여기서는 카메라 렌즈에서 프레임의 왼쪽 위에서부터 1/4이 되는 카메라 공간 위치로 2미터 광선을 쏩니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-131">Here we cast a 2-meter ray from the camera lens to the camera-space position ¼ from the top left of the frame.</span></span>  <span data-ttu-id="ffe19-132">그런 다음, 적중 결과를 사용하여 세계 공간에서 물체가 있는 항목을 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-132">Then use the hit result to render something where the object exists in world space:</span></span>

![카메라 렌즈에서 프레임의 왼쪽 위에서부터 1/4이 되는 카메라 공간 위치로 방출되는 2미터 광선의 청사진](../images/unreal-pvc-img-12.png)

<span data-ttu-id="ffe19-134">공간 매핑을 사용하는 경우 이 적중 위치는 카메라가 보는 표면과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-134">When using spatial mapping, this hit position will match the surface that the camera is seeing.</span></span>

## <a name="rendering-the-pv-camera-feed-in-c"></a><span data-ttu-id="ffe19-135">C++에서 PV 카메라 피드 렌더링</span><span class="sxs-lookup"><span data-stu-id="ffe19-135">Rendering the PV Camera Feed in C++</span></span>

- <span data-ttu-id="ffe19-136">CamCapture라는 새 C++ 행위자 만들기</span><span class="sxs-lookup"><span data-stu-id="ffe19-136">Create a new C++ actor called CamCapture</span></span>
- <span data-ttu-id="ffe19-137">프로젝트 build.cs 파일의 PublicDependencyModuleNames 목록에 “AugmentedReality”를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-137">In the project’s build.cs, add “AugmentedReality” to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "AugmentedReality"
});
```

- <span data-ttu-id="ffe19-138">CamCapture.h에 ARBlueprintLibrary.h를 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-138">In CamCapture.h, include ARBlueprintLibrary.h</span></span>

```cpp
#include "ARBlueprintLibrary.h"
```

- <span data-ttu-id="ffe19-139">또한 메시 및 재질의 지역 변수도 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-139">You also need to add local variables for the mesh and material:</span></span>

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- <span data-ttu-id="ffe19-140">CamCapture.cpp에서 정적 메시를 장면에 추가하도록 생성자를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-140">In CamCapture.cpp, update the constructor to add a static mesh to the scene:</span></span>

```cpp
ACamCapture::ACamCapture()
{
    PrimaryActorTick.bCanEverTick = true;

    // Load a mesh from the engine to render the camera feed to.
    StaticMesh = LoadObject<UStaticMesh>(nullptr, TEXT("/Engine/EngineMeshes/Cube.Cube"), nullptr, LOAD_None, nullptr);

    // Create a static mesh component to render the static mesh
    StaticMeshComponent = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CameraPlane"));
    StaticMeshComponent->SetStaticMesh(StaticMesh);

    // Scale and add to the scene
    StaticMeshComponent->SetWorldScale3D(FVector(0.1f, 1, 1));
    this->SetRootComponent(StaticMeshComponent);
}
```

<span data-ttu-id="ffe19-141">BeginPlay에서, 프로젝트의 카메라 재질에서 동적 재질 인스턴스를 만들고, 정적 메시 구성 요소에 적용하고, HoloLens 카메라를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-141">In BeginPlay create a dynamic material instance from the project’s camera material, apply it to the static mesh component, and start the HoloLens camera.</span></span> 
 
<span data-ttu-id="ffe19-142">편집기의 콘텐츠 브라우저에서 CamTextureMaterial을 마우스 오른쪽 단추로 클릭하고 "참조 복사"를 선택하여 CameraMatPath에 대한 문자열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-142">In the editor, right-click on the CamTextureMaterial in the content browser and select “Copy Reference” to get the string for CameraMatPath.</span></span>

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMateriall = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

<span data-ttu-id="ffe19-143">[틱]에서 카메라의 텍스처를 가져오고, 해당 텍스처를 CamTextureMaterial 재질의 텍스처 매개 변수로 설정하고, 정적 메시 구성 요소의 크기를 카메라 프레임의 가로 세로 비율로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-143">In Tick get the texture from the camera, set it to the texture parameter in the CamTextureMaterial material, and scale the static mesh component by the camera frame’s aspect ratio:</span></span>

```cpp
void ACamCapture::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    // Dynamic material instance only needs to be set once.
    if(IsTextureParamSet)
    {
        return;
    }

    // Get the texture from the camera.
    UARTexture* ARTexture = UARBlueprintLibrary::GetARTexture(EARTextureType::CameraImage);
    if(ARTexture != nullptr)
    {
        // Set the shader's texture parameter (named "Param") to the camera image.
        DynamicMaterial->SetTextureParameterValue("Param", ARTexture);
        IsTextureParamSet = true;

        // Get the camera instrincs
        FARCameraIntrinsics Intrinsics;
        UARBlueprintLibrary::GetCameraIntrinsics(Intrinsics);

        // Scale the camera mesh by the aspect ratio.
        float R = (float)Intrinsics.ImageResolution.X / (float)Intrinsics.ImageResolution.Y;
        StaticMeshComponent->SetWorldScale3D(FVector(0.1f, R, 1));
    }
}
```

# <a name="425"></a>[<span data-ttu-id="ffe19-144">4.25</span><span class="sxs-lookup"><span data-stu-id="ffe19-144">4.25</span></span>](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="ffe19-145">MRC용 PV 카메라에서 렌더링</span><span class="sxs-lookup"><span data-stu-id="ffe19-145">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="ffe19-146">여기에는 **Unreal Engine 4.25** 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-146">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="ffe19-147">시스템 및 사용자 지정 MRC 레코더는 앱에서 렌더링한 홀로그램과 PV 카메라를 결합하여 혼합 현실 캡처를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-147">The system and custom MRC recorders create mixed reality captures by combining the PV Camera with holograms rendered by the app.</span></span>

<span data-ttu-id="ffe19-148">기본적으로 혼합 현실 캡처는 오른쪽 눈의 홀로그램 출력을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-148">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="ffe19-149">몰입 형 앱이 [PV 카메라에서 렌더링](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)하도록 선택한 경우 해당 항목을 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-149">If an immersive app chooses to [render from the PV Camera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), then that will be used instead.</span></span> <span data-ttu-id="ffe19-150">PV 카메라에서 렌더링하면 MRC 영상에서 실제 세계와 홀로그램의 매핑이 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-150">Rendering from the PV Camera improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="ffe19-151">PV 카메라에서 렌더링하도록 옵트인하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-151">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="ffe19-152">**SetEnabledMixedRealityCamera** 및 **ResizeMixedRealityCamera** 호출</span><span class="sxs-lookup"><span data-stu-id="ffe19-152">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="ffe19-153">**크기 X** 및 **크기 Y** 값을 사용하여 비디오 크기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-153">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![세 번째 카메라](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="ffe19-155">그러면 Unreal은 PV 카메라의 관점에서 렌더링하는 MRC의 요청을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-155">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="ffe19-156">[혼합 현실 캡처](../../../mixed-reality-capture.md)가 트리거된 경우에만 앱이 사진/비디오 카메라의 관점에서 렌더링하도록 요청됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-156">Only when [Mixed Reality Capture](../../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="ffe19-157">PV 카메라 사용</span><span class="sxs-lookup"><span data-stu-id="ffe19-157">Using the PV Camera</span></span>

<span data-ttu-id="ffe19-158">웹캠 질감을 게임에서 런타임에 검색할 수 있지만 편집기의 **편집 > 프로젝트 설정** 에서 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-158">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="ffe19-159">**플랫폼 > HoloLens > 기능** 으로 이동하여 **웹캠** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-159">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="ffe19-160">**StartCameraCapture** 함수를 사용하여 런타임에 웹캠을 사용하고 **StopCameraCapture** 함수를 사용하여 기록을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-160">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Camera 시작 중지](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="ffe19-162">이미지 렌더링</span><span class="sxs-lookup"><span data-stu-id="ffe19-162">Rendering an image</span></span>
<span data-ttu-id="ffe19-163">카메라 이미지를 렌더링하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-163">To render the camera image:</span></span>
1. <span data-ttu-id="ffe19-164">프로젝트의 재질을 기반으로 동적 재질 인스턴스를 만듭니다. 아래 스크린샷에서 이름이 **PVCamMat** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-164">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="ffe19-165">동적 재질 인스턴스를 **재질 인스턴스 동적 개체 참조** 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-165">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="ffe19-166">카메라 피드를 렌더링하는 장면의 개체 재질을 이 새로운 동적 재질 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-166">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="ffe19-167">카메라 이미지를 재질에 바인딩하는 데 사용할 타이머를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-167">Start a timer that will be used to bind the camera image to the material.</span></span>

![카메라 렌더링](../images/unreal-camera-render.PNG)

4. <span data-ttu-id="ffe19-169">이 타이머에 대한 새로운 함수를 만들고(이 경우 **MaterialTimer**), **GetARCameraImage** 를 호출하여 웹캠에서 질감을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-169">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="ffe19-170">이 질감이 유효한 경우 음영의 질감 매개 변수를 이 이미지로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-170">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="ffe19-171">그렇지 않으면 재질 타이머를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-171">Otherwise, start the material timer again.</span></span>

![웹캠의 카메라 텍스처](../images/unreal-camera-texture.PNG)

5. <span data-ttu-id="ffe19-173">재질에 색 항목에 바인딩된 **SetTextureParameterValue** 의 이름과 일치하는 매개 변수가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-173">Make sure the material has a parameter that matches the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="ffe19-174">매개 변수가 없으면 카메라 이미지를 제대로 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ffe19-174">Without the parameter, the camera image can't be displayed properly.</span></span>

![카메라 텍스처](../images/unreal-camera-material.PNG)

