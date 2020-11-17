---
title: Unity의 위치를 찾을 수 있는 카메라
description: 파일이 나 Texture2D 사진을 캡처하는 방법, 사진을 캡처하고 raw 바이트와 상호 작용 하는 방법 및 비디오를 캡처하는 방법에 대해 알아봅니다.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 사진, 비디오, hololens, 카메라, unity, 과정이, PVC, photo video 카메라, 혼합 현실 헤드셋, windows mixed reality 헤드셋, 가상 현실 헤드셋, 웹캠, 사진 캡처, 비디오 캡처
ms.openlocfilehash: c41ff88650da4aa6dc0d98c05b1b881362123a4f
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678602"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="e3399-104">Unity의 위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="e3399-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="e3399-105">사진 비디오 카메라 기능 사용</span><span class="sxs-lookup"><span data-stu-id="e3399-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="e3399-106">[카메라](../platform-capabilities-and-apis/locatable-camera.md)를 사용 하려면 앱에 대해 "웹캠" 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>
1. <span data-ttu-id="e3399-107">Unity 편집기에서 "> 프로젝트 설정 > 플레이어 편집" 페이지로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="e3399-108">"Windows 스토어" 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-108">Click the "Windows Store" tab</span></span>
3. <span data-ttu-id="e3399-109">"게시 설정 > 기능" 섹션에서 **웹캠** 및 **마이크** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="e3399-110">카메라에서는 한 번에 하나의 작업만 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="e3399-111">카메라의 현재 모드 (사진, 비디오 또는 없음)를 확인 하려면 UnityEngine. XR을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-111">To determine which mode (photo, video, or none) the camera is currently in, you can check UnityEngine.XR.WSA.WebCam.Mode.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="e3399-112">사진 캡처</span><span class="sxs-lookup"><span data-stu-id="e3399-112">Photo Capture</span></span>

<span data-ttu-id="e3399-113">**네임 스페이스:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="e3399-113">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="e3399-114">**형식:** *사진 캡처*</span><span class="sxs-lookup"><span data-stu-id="e3399-114">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="e3399-115">사진 *캡처* 유형을 사용 하면 사진 비디오 카메라와 사진을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-115">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="e3399-116">사진 *캡처* 를 사용 하 여 사진을 촬영 하는 일반적인 패턴은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-116">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="e3399-117">*사진 캡처* 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="e3399-117">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="e3399-118">원하는 설정을 사용 하 여 *CameraParameters* 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-118">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="e3399-119">*Startphoto Modeasync* 를 통해 사진 모드 시작</span><span class="sxs-lookup"><span data-stu-id="e3399-119">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="e3399-120">원하는 사진 가져오기</span><span class="sxs-lookup"><span data-stu-id="e3399-120">Take the desired photo</span></span>
    * <span data-ttu-id="e3399-121">필드 해당 사진과 상호 작용</span><span class="sxs-lookup"><span data-stu-id="e3399-121">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="e3399-122">사진 모드 중지 및 리소스 정리</span><span class="sxs-lookup"><span data-stu-id="e3399-122">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="e3399-123">사진 캡처에 대 한 일반적인 설정</span><span class="sxs-lookup"><span data-stu-id="e3399-123">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="e3399-124">세 가지 용도 모두에서 위의 동일한 첫 3 단계를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-124">For all three uses, start with the same first 3 steps above</span></span>

<span data-ttu-id="e3399-125">*사진 캡처* 개체를 만들어 시작</span><span class="sxs-lookup"><span data-stu-id="e3399-125">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="e3399-126">그런 다음 개체를 저장 하 고, 매개 변수를 설정 하 고, 사진 모드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-126">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
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

<span data-ttu-id="e3399-127">끝으로 여기에 제공 된 동일한 정리 코드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-127">In the end, you will also use the same clean up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="e3399-128">이러한 단계를 수행 하 고 나면 캡처할 사진 유형을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-128">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="e3399-129">파일에 사진 캡처</span><span class="sxs-lookup"><span data-stu-id="e3399-129">Capture a Photo to a File</span></span>

<span data-ttu-id="e3399-130">가장 간단한 작업은 파일에 직접 사진을 캡처하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-130">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="e3399-131">사진은 JPG 또는 PNG로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-131">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="e3399-132">사진 모드를 성공적으로 시작 하는 경우 사진을 촬영 하 고 디스크에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-132">If you successfully started photo mode, take a photo and store it on disk</span></span>

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

<span data-ttu-id="e3399-133">사진을 디스크로 캡처한 후 사진 모드를 종료 하 고 개체를 정리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-133">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

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

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="e3399-134">Texture2D에 사진 캡처</span><span class="sxs-lookup"><span data-stu-id="e3399-134">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="e3399-135">Texture2D으로 데이터를 캡처할 때 프로세스는 디스크에 캡처하는 것과 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-135">When capturing data to a Texture2D, the process is extremely similar to capturing to disk.</span></span>

<span data-ttu-id="e3399-136">위의 설정 프로세스를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-136">Follow the set up process above.</span></span>

<span data-ttu-id="e3399-137">*Onsale Modestarted* 에서 프레임을 메모리로 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-137">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

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

<span data-ttu-id="e3399-138">그런 다음 결과를 질감에 적용 하 고 위의 정리 코드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-138">You will then apply your result to a texture and use the common clean up code above.</span></span>

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="e3399-139">사진 캡처 및 원시 바이트 조작</span><span class="sxs-lookup"><span data-stu-id="e3399-139">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="e3399-140">메모리 프레임에 있는 원시 바이트와 상호 작용 하려면 Texture2D 사진 캡처에서와 같이 위와 동일한 설정 *단계를 수행* 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-140">To interact with the raw bytes of an in memory frame, follow the same set up steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="e3399-141">원시 바이트를 가져와 상호 작용할 수 있는 *OnCapturedPhotoToMemory* 에서 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-141">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="e3399-142">이 예제에서는 *Setpixels ()* 을 통해 텍스처에 추가로 처리 하거나 적용할 수 있는 *목록을 <Color>* 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-142">In this example, you will create a *List<Color>* which could be further processed or applied to a texture via *SetPixels()*</span></span>

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

## <a name="video-capture"></a><span data-ttu-id="e3399-143">비디오 캡처</span><span class="sxs-lookup"><span data-stu-id="e3399-143">Video Capture</span></span>

<span data-ttu-id="e3399-144">**네임 스페이스:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="e3399-144">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="e3399-145">**유형:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="e3399-145">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="e3399-146">*VideoCapture* 은 *사진 캡처와* 매우 유사 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-146">*VideoCapture* functions very similarly to *PhotoCapture*.</span></span> <span data-ttu-id="e3399-147">두 가지 차이점은 FPS (초당 프레임 수) 값을 지정 해야 하 고, mp4 파일로는 디스크에 직접 저장 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-147">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as an .mp4 file.</span></span> <span data-ttu-id="e3399-148">*VideoCapture* 를 사용 하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-148">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="e3399-149">*VideoCapture* 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="e3399-149">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="e3399-150">원하는 설정을 사용 하 여 *CameraParameters* 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-150">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="e3399-151">*Startvideomodeasync* 를 통해 비디오 모드 시작</span><span class="sxs-lookup"><span data-stu-id="e3399-151">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="e3399-152">비디오 녹화 시작</span><span class="sxs-lookup"><span data-stu-id="e3399-152">Start recording video</span></span>
5. <span data-ttu-id="e3399-153">비디오 녹화 중지</span><span class="sxs-lookup"><span data-stu-id="e3399-153">Stop recording video</span></span>
6. <span data-ttu-id="e3399-154">비디오 모드 중지 및 리소스 정리</span><span class="sxs-lookup"><span data-stu-id="e3399-154">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="e3399-155">*VideoCapture* 개체 *VideoCapture m_VideoCapture = null* 을 만들어 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-155">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="e3399-156">다음으로 기록 하 고 시작 하는 데 사용할 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-156">Next, set up the parameters you will want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
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

<span data-ttu-id="e3399-157">시작 되 면 기록을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-157">Once started, begin the recording</span></span>

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

<span data-ttu-id="e3399-158">기록이 시작 된 후에는 중지할 수 있도록 UI 나 동작을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-158">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="e3399-159">여기서는 로그만 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-159">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="e3399-160">나중에 기록을 중지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-160">At a later point, you will want to stop the recording.</span></span> <span data-ttu-id="e3399-161">이는 예를 들어 타이머 또는 사용자 입력에서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-161">This could happen from a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="e3399-162">기록이 중지 되 면 비디오 모드를 중지 하 고 리소스를 정리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-162">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

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

## <a name="troubleshooting"></a><span data-ttu-id="e3399-163">문제 해결</span><span class="sxs-lookup"><span data-stu-id="e3399-163">Troubleshooting</span></span>
* <span data-ttu-id="e3399-164">사용 가능한 해결 방법이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-164">No resolutions are available</span></span>
    * <span data-ttu-id="e3399-165">**웹캠** 기능이 프로젝트에 지정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="e3399-166">다음 개발 검사점</span><span class="sxs-lookup"><span data-stu-id="e3399-166">Next Development Checkpoint</span></span>

<span data-ttu-id="e3399-167">앞서 소개한 Unity 개발 검사점 경험을 팔로 하는 경우 혼합 현실 플랫폼 기능과 Api를 탐색 하는 과정을 진행 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-167">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="e3399-168">여기에서 다음 항목을 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-168">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e3399-169">포커스 지점</span><span class="sxs-lookup"><span data-stu-id="e3399-169">Focus point</span></span>](focus-point-in-unity.md)

<span data-ttu-id="e3399-170">또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-170">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e3399-171">HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋에 배포</span><span class="sxs-lookup"><span data-stu-id="e3399-171">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="e3399-172">언제든지 [Unity 개발 검사점](unity-development-overview.md#3-platform-capabilities-and-apis)으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3399-172">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3399-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3399-173">See Also</span></span>
* [<span data-ttu-id="e3399-174">위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="e3399-174">Locatable camera</span></span>](../platform-capab ilities-and-apis/locatable-camera.md)
