---
ms.openlocfilehash: e79b14c19a452b5b78c6f8cf7ea24bd65bfa0eaa
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98605081"
---
# <a name="426"></a>[4.26](#tab/426) 

## <a name="pv-camera-feed-setup"></a>PV 카메라 피드 설정

> [!IMPORTANT]
> PV 카메라는 Windows Mixed Reality 및 OpenXR 플러그 인 모두에서 구현됩니다. 그러나 OpenXR은 [Microsoft OpenXR 플러그 인](https://github.com/microsoft/Microsoft-OpenXR-Unreal)을 설치해야 합니다. 또한 OpenXR은 현재 제한이 있으며, 카메라는 DirectX11 RHI와 함께 작동할 수 있습니다. 이 제한은 이후 Unreal 버전에서 수정될 예정입니다. 

- **프로젝트 설정 > HoloLens** 에서 **웹캠** 기능을 사용하도록 설정합니다.

![웹캠 속성이 강조 표시된 HoloLens 프로젝트 설정의 스크린샷](../images/unreal-pvc-img-01.png)

- "CamCapture"라는 새 행위자를 만들고 카메라 피드를 렌더링하는 평면을 추가합니다.

![평면이 추가된 행위자의 스크린샷](../images/unreal-pvc-img-02.png)

- 장면에 행위자를 추가하고, Texture Object 매개 변수와 텍스처 샘플을 사용하여 CamTextureMaterial이라는 새 장면을 만듭니다.  텍스처의 rgb 데이터를 출력 발광 색으로 보냅니다.

![재질 및 텍스처 샘플 청사진](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a>PV 카메라 피드 렌더링

- CamCapture 청사진에서 PV 카메라를 켭니다.

![PV 카메라가 켜진 Toggle ARCapture 함수의 청사진](../images/unreal-pvc-img-04.png)

- CamTextureMaterial에서 동적 재질 인스턴스를 만들고 이 재질을 행위자의 평면에 할당합니다.

![Create Dynamic Material Instance 함수의 청사진](../images/unreal-pvc-img-05.png)

- 카메라 피드에서 텍스처를 가져와 동적 재질에 할당합니다(유효한 경우).  텍스처가 유효하지 않으면 타이머를 시작하고, 타이머 시간이 끝난 후 다시 시도합니다.

![동적 재질에 할당된 카메라 텍스처의 청사진](../images/unreal-pvc-img-06.png)

- 마지막으로 평면의 크기를 카메라 이미지의 가로 세로 비율로 조정합니다.

![카메라 이미지의 가로 세로 비율에 맞게 크기가 조정된 평면의 청사진](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a>세계 공간에서 카메라 위치 찾기

HoloLens 2의 카메라는 디바이스의 머리 추적에서 수직으로 오프셋됩니다.  오프셋을 고려하여 세계 공간에서 카메라를 찾는 몇 가지 기능이 있습니다.

GetPVCameraToWorldTransform은 PV 카메라의 세계 공간에서 변환을 가져오고 카메라 렌즈에 다음과 같이 배치됩니다.

![Get PVCamera to World Transform 함수의 청사진](../images/unreal-pvc-img-08.png)

GetWorldSpaceRayFromCameraPoint는 카메라 렌즈의 광선을 Unreal 세계 공간의 장면으로 투사하여 카메라 프레임에서 픽셀의 콘텐츠를 찾습니다.

![Get World Space Ray from Camera Point의 청사진](../images/unreal-pvc-img-09.png)

GetPVCameraIntrinsics는 카메라 프레임에서 컴퓨터 비전 처리를 수행할 때 사용할 수 있는 카메라 내장 값을 반환합니다.

![Get PVCamera Intrinsics 함수의 청사진](../images/unreal-pvc-img-10.png)

세계 공간의 특정 픽셀 좌표에 무엇이 있는지 알아내려면 세계 공간 광선과 함께 선 추적을 사용합니다.

![세계 공간의 특정 좌표에 무엇이 있는지 알아내는 데 사용되는 세계 공간 광선의 청사진](../images/unreal-pvc-img-11.png)

여기서는 카메라 렌즈에서 프레임의 왼쪽 위에서부터 1/4이 되는 카메라 공간 위치로 2미터 광선을 쏩니다.  그런 다음, 적중 결과를 사용하여 세계 공간에서 물체가 있는 항목을 렌더링합니다.

![카메라 렌즈에서 프레임의 왼쪽 위에서부터 1/4이 되는 카메라 공간 위치로 방출되는 2미터 광선의 청사진](../images/unreal-pvc-img-12.png)

공간 매핑을 사용하는 경우 이 적중 위치는 카메라가 보는 표면과 일치합니다.

## <a name="rendering-the-pv-camera-feed-in-c"></a>C++에서 PV 카메라 피드 렌더링

- CamCapture라는 새 C++ 행위자 만들기
- 프로젝트 build.cs 파일의 PublicDependencyModuleNames 목록에 “AugmentedReality”를 추가합니다.

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

- CamCapture.h에 ARBlueprintLibrary.h를 포함시킵니다.

```cpp
#include "ARBlueprintLibrary.h"
```

- 또한 메시 및 재질의 지역 변수도 추가해야 합니다.

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- CamCapture.cpp에서 정적 메시를 장면에 추가하도록 생성자를 업데이트합니다.

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

BeginPlay에서, 프로젝트의 카메라 재질에서 동적 재질 인스턴스를 만들고, 정적 메시 구성 요소에 적용하고, HoloLens 카메라를 시작합니다. 
 
편집기의 콘텐츠 브라우저에서 CamTextureMaterial을 마우스 오른쪽 단추로 클릭하고 "참조 복사"를 선택하여 CameraMatPath에 대한 문자열을 가져옵니다.

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMaterial = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

[틱]에서 카메라의 텍스처를 가져오고, 해당 텍스처를 CamTextureMaterial 재질의 텍스처 매개 변수로 설정하고, 정적 메시 구성 요소의 크기를 카메라 프레임의 가로 세로 비율로 조정합니다.

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

# <a name="425"></a>[4.25](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a>MRC용 PV 카메라에서 렌더링

> [!NOTE]
> 여기에는 **Unreal Engine 4.25** 이상이 필요합니다.

시스템 및 사용자 지정 MRC 레코더는 앱에서 렌더링한 홀로그램과 PV 카메라를 결합하여 혼합 현실 캡처를 만듭니다.

기본적으로 혼합 현실 캡처는 오른쪽 눈의 홀로그램 출력을 사용합니다. 몰입 형 앱이 [PV 카메라에서 렌더링](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)하도록 선택한 경우 해당 항목을 대신 사용합니다. PV 카메라에서 렌더링하면 MRC 영상에서 실제 세계와 홀로그램의 매핑이 개선됩니다.

PV 카메라에서 렌더링하도록 옵트인하려면 다음을 수행합니다.

1. **SetEnabledMixedRealityCamera** 및 **ResizeMixedRealityCamera** 호출
    * **크기 X** 및 **크기 Y** 값을 사용하여 비디오 크기를 설정합니다.

![세 번째 카메라](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

그러면 Unreal은 PV 카메라의 관점에서 렌더링하는 MRC의 요청을 처리합니다.

> [!NOTE]
> [혼합 현실 캡처](/hololens/holographic-photos-and-videos)가 트리거된 경우에만 앱이 사진/비디오 카메라의 관점에서 렌더링하도록 요청됩니다.

## <a name="using-the-pv-camera"></a>PV 카메라 사용

웹캠 질감을 게임에서 런타임에 검색할 수 있지만 편집기의 **편집 > 프로젝트 설정** 에서 사용하도록 설정해야 합니다.
1. **플랫폼 > HoloLens > 기능** 으로 이동하여 **웹캠** 을 선택합니다.
    * **StartCameraCapture** 함수를 사용하여 런타임에 웹캠을 사용하고 **StopCameraCapture** 함수를 사용하여 기록을 중지합니다.

![Camera 시작 중지](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>이미지 렌더링
카메라 이미지를 렌더링하려면 다음을 수행합니다.
1. 프로젝트의 재질을 기반으로 동적 재질 인스턴스를 만듭니다. 아래 스크린샷에서 이름이 **PVCamMat** 입니다.  
2. 동적 재질 인스턴스를 **재질 인스턴스 동적 개체 참조** 변수로 설정합니다.  
3. 카메라 피드를 렌더링하는 장면의 개체 재질을 이 새로운 동적 재질 인스턴스로 설정합니다.
    * 카메라 이미지를 재질에 바인딩하는 데 사용할 타이머를 시작합니다.

![카메라 렌더링](../images/unreal-camera-render.PNG)

4. 이 타이머에 대한 새로운 함수를 만들고(이 경우 **MaterialTimer**), **GetARCameraImage** 를 호출하여 웹캠에서 질감을 가져옵니다.  
5. 이 질감이 유효한 경우 음영의 질감 매개 변수를 이 이미지로 설정합니다.  그렇지 않으면 재질 타이머를 다시 시작합니다.

![웹캠의 카메라 텍스처](../images/unreal-camera-texture.PNG)

5. 재질에 색 항목에 바인딩된 **SetTextureParameterValue** 의 이름과 일치하는 매개 변수가 있는지 확인합니다. 매개 변수가 없으면 카메라 이미지를 제대로 표시할 수 없습니다.

![카메라 텍스처](../images/unreal-camera-material.PNG)