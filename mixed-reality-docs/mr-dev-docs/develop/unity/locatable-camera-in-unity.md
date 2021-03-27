---
title: Unity의 사진 비디오 카메라
description: 파일이 나 Texture2D 사진을 캡처하는 방법, 사진을 캡처하고 raw 바이트와 상호 작용 하는 방법 및 비디오를 캡처하는 방법에 대해 알아봅니다.
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: 사진, 비디오, hololens, 카메라, unity, 과정이, PVC, photo video 카메라, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 웹캠, 사진 캡처, 비디오 캡처
ms.openlocfilehash: 1cae796a793036ed59c1d0805df76cb8ac143027
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636215"
---
# <a name="photo-video-camera-in-unity"></a><span data-ttu-id="e20ca-104">Unity의 사진 비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="e20ca-104">Photo Video camera in Unity</span></span>

## <a name="enabling-the-capability-for-camera-access"></a><span data-ttu-id="e20ca-105">카메라 액세스를 위한 기능 사용</span><span class="sxs-lookup"><span data-stu-id="e20ca-105">Enabling the capability for camera access</span></span>

<span data-ttu-id="e20ca-106">[카메라](../platform-capabilities-and-apis/locatable-camera.md)를 사용 하려면 앱에 대해 "웹캠" 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>

1. <span data-ttu-id="e20ca-107">Unity 편집기에서 "> 프로젝트 설정 > 플레이어 편집" 페이지로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="e20ca-108">"Windows 스토어" 탭을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-108">Select the "Windows Store" tab</span></span>
3. <span data-ttu-id="e20ca-109">"게시 설정 > 기능" 섹션에서 **웹캠** 및 **마이크** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="e20ca-110">카메라에서는 한 번에 하나의 작업만 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="e20ca-111">`UnityEngine.XR.WSA.WebCam.Mode`Unity 2018 및 이전 또는 unity 2019 이상에서 현재 카메라가 있는 모드를 확인할 수 있습니다 `UnityEngine.Windows.WebCam.Mode` .</span><span class="sxs-lookup"><span data-stu-id="e20ca-111">You can check which mode the camera is currently in with `UnityEngine.XR.WSA.WebCam.Mode` in Unity 2018 and earlier or `UnityEngine.Windows.WebCam.Mode` in Unity 2019  and later.</span></span> <span data-ttu-id="e20ca-112">사용 가능한 모드는 사진, 동영상 또는 없음입니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-112">Available modes are photo, video, or none.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="e20ca-113">사진 캡처</span><span class="sxs-lookup"><span data-stu-id="e20ca-113">Photo capture</span></span>

<span data-ttu-id="e20ca-114">**네임 스페이스 (Unity 2019 이전):** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="e20ca-114">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="e20ca-115">**네임 스페이스 (Unity 2019 이상):** *Unityengine. Windows 웹캠*</span><span class="sxs-lookup"><span data-stu-id="e20ca-115">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="e20ca-116">**형식:** *사진 캡처*</span><span class="sxs-lookup"><span data-stu-id="e20ca-116">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="e20ca-117">사진 *캡처* 유형을 사용 하면 사진 비디오 카메라와 사진을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-117">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="e20ca-118">사진 *캡처* 를 사용 하 여 사진을 촬영 하는 일반적인 패턴은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-118">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>

1. <span data-ttu-id="e20ca-119">*사진 캡처* 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="e20ca-119">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="e20ca-120">원하는 설정을 사용 하 여 *CameraParameters* 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-120">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="e20ca-121">*Startphoto Modeasync* 를 통해 사진 모드 시작</span><span class="sxs-lookup"><span data-stu-id="e20ca-121">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="e20ca-122">원하는 사진 가져오기</span><span class="sxs-lookup"><span data-stu-id="e20ca-122">Take the photo you want</span></span>
    * <span data-ttu-id="e20ca-123">필드 해당 사진과 상호 작용</span><span class="sxs-lookup"><span data-stu-id="e20ca-123">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="e20ca-124">사진 모드 중지 및 리소스 정리</span><span class="sxs-lookup"><span data-stu-id="e20ca-124">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="e20ca-125">사진 캡처에 대 한 공통 설정</span><span class="sxs-lookup"><span data-stu-id="e20ca-125">Common set-up for PhotoCapture</span></span>

<span data-ttu-id="e20ca-126">세 가지 용도 모두에서 위의 세 단계를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-126">For all three uses, start with the same first three steps above</span></span>

<span data-ttu-id="e20ca-127">*사진 캡처* 개체를 만들어 시작</span><span class="sxs-lookup"><span data-stu-id="e20ca-127">Start by creating a *PhotoCapture* object</span></span>

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

<span data-ttu-id="e20ca-128">그런 다음 개체를 저장 하 고, 매개 변수를 설정 하 고, 사진 모드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-128">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
private PhotoCapture photoCaptureObject = null;

void OnPhotoCaptureCreated(PhotoCapture captureObject)
{
    photoCaptureObject = captureObject;

    Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

    CameraParameters c = new CameraParameters();
    c.hologramOpacity = 0.0f;
    c.cameraResolutionWidth = cameraResolution.width;
    c.cameraResolutionHeight = cameraResolution.height;
    c.pixelFormat = CapturePixelFormat.BGRA32;

    captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
}
```

<span data-ttu-id="e20ca-129">끝으로 여기에 제공 된 동일한 정리 코드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-129">In the end, you'll also use the same clean-up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

<span data-ttu-id="e20ca-130">이러한 단계를 수행 하 고 나면 캡처할 사진 유형을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-130">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="e20ca-131">파일에 사진 캡처</span><span class="sxs-lookup"><span data-stu-id="e20ca-131">Capture a photo to a file</span></span>

<span data-ttu-id="e20ca-132">가장 간단한 작업은 파일에 직접 사진을 캡처하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-132">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="e20ca-133">사진은 JPG 또는 PNG로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-133">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="e20ca-134">사진 모드를 성공적으로 시작 하는 경우 사진을 촬영 하 고 디스크에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-134">If you successfully started photo mode, take a photo and store it on disk</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
        string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

<span data-ttu-id="e20ca-135">사진을 디스크로 캡처한 후 사진 모드를 종료 하 고 개체를 정리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-135">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        Debug.Log("Saved Photo to disk!");
        photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
    }
    else
    {
        Debug.Log("Failed to save Photo to disk");
    }
}
```

### <a name="capture-a-photo-to-a-texture2d-with-location"></a><span data-ttu-id="e20ca-136">위치를 사용 하 여 Texture2D에 사진 캡처</span><span class="sxs-lookup"><span data-stu-id="e20ca-136">Capture a photo to a Texture2D with location</span></span>

<span data-ttu-id="e20ca-137">Texture2D에 데이터를 캡처할 때 프로세스는 디스크에 캡처하는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-137">When capturing data to a Texture2D, the process is similar to capturing to disk.</span></span>

<span data-ttu-id="e20ca-138">위의 설치 프로세스를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="e20ca-138">Follow the setup process above.</span></span>

<span data-ttu-id="e20ca-139">*Onsale Modestarted* 에서 프레임을 메모리로 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-139">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
{
    if (result.success)
    {
        photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
    }
    else
    {
        Debug.LogError("Unable to start photo mode!");
    }
}
```

<span data-ttu-id="e20ca-140">그런 다음 결과를 질감에 적용 하 고 위의 일반적인 정리 코드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-140">You'll then apply your result to a texture and use the common clean-up code above.</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        // Create our Texture2D for use and set the correct resolution
        Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
        // Copy the raw image data into our target texture
        photoCaptureFrame.UploadImageDataToTexture(targetTexture);
        // Do as we wish with the texture such as apply it to a material, etc.
    }
    // Clean up
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

#### <a name="locatable-camera"></a><span data-ttu-id="e20ca-141">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="e20ca-141">Locatable camera</span></span>

<span data-ttu-id="e20ca-142">장면에이 텍스처를 놓고 과정이 카메라 매트릭스를 사용 하 여 표시 하려면 다음 코드를 확인의 *OnCapturedPhotoToMemory* 에 추가 합니다 `result.success` .</span><span class="sxs-lookup"><span data-stu-id="e20ca-142">To place this texture in the scene and display it using the locatable camera matrices, add the following code to *OnCapturedPhotoToMemory* in the `result.success` check:</span></span>

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

<span data-ttu-id="e20ca-143">Unity는 포럼의 특정 셰이더에 프로젝션 행렬을 적용 하기 위한 [샘플 코드를 제공](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-143">[Unity has provided sample code](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) for applying the projection matrix to a specific shader on their forums.</span></span>

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="e20ca-144">사진 캡처 및 원시 바이트 조작</span><span class="sxs-lookup"><span data-stu-id="e20ca-144">Capture a photo and interact with the raw bytes</span></span>

<span data-ttu-id="e20ca-145">메모리 프레임에 있는 원시 바이트와 상호 작용 하려면 Texture2D에 사진을 캡처하는 것 처럼 위와 동일한 설정 *단계를 수행* 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-145">To interact with the raw bytes of an in memory frame, follow the same setup steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="e20ca-146">원시 바이트를 가져와 상호 작용할 수 있는 *OnCapturedPhotoToMemory* 에서 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-146">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="e20ca-147">이 예제에서는 *Setpixels ()* 을 통해 추가 처리 또는 텍스처에 적용 되는 *목록을 <Color>* 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-147">In this example, you'll create a *List<Color>* to be further processed or applied to a texture via *SetPixels()*</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
{
    if (result.success)
    {
        List<byte> imageBufferList = new List<byte>();
        // Copy the raw IMFMediaBuffer data into our empty byte list.
        photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

        // In this example, we captured the image using the BGRA32 format.
        // So our stride will be 4 since we have a byte for each rgba channel.
        // The raw image data will also be flipped so we access our pixel data
        // in the reverse order.
        int stride = 4;
        float denominator = 1.0f / 255.0f;
        List<Color> colorArray = new List<Color>();
        for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
        {
            float a = (int)(imageBufferList[i - 0]) * denominator;
            float r = (int)(imageBufferList[i - 1]) * denominator;
            float g = (int)(imageBufferList[i - 2]) * denominator;
            float b = (int)(imageBufferList[i - 3]) * denominator;

            colorArray.Add(new Color(r, g, b, a));
        }
        // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
    }
    photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
}
```

## <a name="video-capture"></a><span data-ttu-id="e20ca-148">비디오 캡처</span><span class="sxs-lookup"><span data-stu-id="e20ca-148">Video capture</span></span>

<span data-ttu-id="e20ca-149">**네임 스페이스 (Unity 2019 이전):** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="e20ca-149">**Namespace (before Unity 2019):** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="e20ca-150">**네임 스페이스 (Unity 2019 이상):** *Unityengine. Windows 웹캠*</span><span class="sxs-lookup"><span data-stu-id="e20ca-150">**Namespace (Unity 2019 and later):** *UnityEngine.Windows.WebCam*</span></span><br>
<span data-ttu-id="e20ca-151">**유형:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="e20ca-151">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="e20ca-152">*VideoCapture* 는 *사진 캡처* 와 유사 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-152">*VideoCapture* functions similarly to *PhotoCapture*.</span></span> <span data-ttu-id="e20ca-153">두 가지 차이점은 FPS (초당 프레임 수) 값을 지정 해야 하 고, mp4 파일로는 디스크에 직접 저장 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-153">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as a .mp4 file.</span></span> <span data-ttu-id="e20ca-154">*VideoCapture* 를 사용 하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-154">The steps to use *VideoCapture* are as follows:</span></span>

1. <span data-ttu-id="e20ca-155">*VideoCapture* 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="e20ca-155">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="e20ca-156">원하는 설정을 사용 하 여 *CameraParameters* 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-156">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="e20ca-157">*Startvideomodeasync* 를 통해 비디오 모드 시작</span><span class="sxs-lookup"><span data-stu-id="e20ca-157">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="e20ca-158">비디오 녹화 시작</span><span class="sxs-lookup"><span data-stu-id="e20ca-158">Start recording video</span></span>
5. <span data-ttu-id="e20ca-159">비디오 녹화 중지</span><span class="sxs-lookup"><span data-stu-id="e20ca-159">Stop recording video</span></span>
6. <span data-ttu-id="e20ca-160">비디오 모드 중지 및 리소스 정리</span><span class="sxs-lookup"><span data-stu-id="e20ca-160">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="e20ca-161">*VideoCapture* 개체 *VideoCapture m_VideoCapture = null* 을 만들어 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-161">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

<span data-ttu-id="e20ca-162">다음으로 기록 하 고 시작 하는 데 사용할 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-162">Next, set up the parameters you'll want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated(VideoCapture videoCapture)
{
    if (videoCapture != null)
    {
        m_VideoCapture = videoCapture;

        Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
        float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

        CameraParameters cameraParameters = new CameraParameters();
        cameraParameters.hologramOpacity = 0.0f;
        cameraParameters.frameRate = cameraFramerate;
        cameraParameters.cameraResolutionWidth = cameraResolution.width;
        cameraParameters.cameraResolutionHeight = cameraResolution.height;
        cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

        m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                            VideoCapture.AudioState.None,
                                            OnStartedVideoCaptureMode);
    }
    else
    {
        Debug.LogError("Failed to create VideoCapture Instance!");
    }
}
```

<span data-ttu-id="e20ca-163">시작 되 면 기록을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-163">Once started, begin the recording</span></span>

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    if (result.success)
    {
        string filename = string.Format("MyVideo_{0}.mp4", Time.time);
        string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

        m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
    }
}
```

<span data-ttu-id="e20ca-164">기록이 시작 된 후에는 중지할 수 있도록 UI 나 동작을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-164">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="e20ca-165">여기서는 로그만 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-165">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

<span data-ttu-id="e20ca-166">나중에 타이머 또는 사용자 입력을 사용 하 여 기록을 중지할 수 있습니다 (예를 들어).</span><span class="sxs-lookup"><span data-stu-id="e20ca-166">At a later point, you'll want to stop the recording using a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

<span data-ttu-id="e20ca-167">기록이 중지 되 면 비디오 모드를 중지 하 고 리소스를 정리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-167">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Stopped Recording Video!");
    m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
}

void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
{
    m_VideoCapture.Dispose();
    m_VideoCapture = null;
}
```

## <a name="troubleshooting"></a><span data-ttu-id="e20ca-168">문제 해결</span><span class="sxs-lookup"><span data-stu-id="e20ca-168">Troubleshooting</span></span>

* <span data-ttu-id="e20ca-169">사용 가능한 해결 방법이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-169">No resolutions are available</span></span>
  * <span data-ttu-id="e20ca-170">**웹캠** 기능이 프로젝트에 지정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-170">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="e20ca-171">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="e20ca-171">Next Development Checkpoint</span></span>

<span data-ttu-id="e20ca-172">앞서 소개한 Unity 개발 검사점 경험을 팔로 하는 경우 혼합 현실 플랫폼 기능과 Api를 탐색 하는 과정을 진행 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-172">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="e20ca-173">여기에서 다음 항목으로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-173">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e20ca-174">포커스 지점</span><span class="sxs-lookup"><span data-stu-id="e20ca-174">Focus point</span></span>](focus-point-in-unity.md)

<span data-ttu-id="e20ca-175">또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-175">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e20ca-176">HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋에 배포</span><span class="sxs-lookup"><span data-stu-id="e20ca-176">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="e20ca-177">언제든지 [Unity 개발 검사점](unity-development-overview.md#3-advanced-features)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e20ca-177">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="e20ca-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e20ca-178">See Also</span></span>

* [<span data-ttu-id="e20ca-179">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="e20ca-179">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)