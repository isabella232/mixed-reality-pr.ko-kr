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
# <a name="photo-video-camera-in-unity"></a>Unity의 사진 비디오 카메라

## <a name="enabling-the-capability-for-camera-access"></a>카메라 액세스를 위한 기능 사용

[카메라](../platform-capabilities-and-apis/locatable-camera.md)를 사용 하려면 앱에 대해 "웹캠" 기능을 선언 해야 합니다.

1. Unity 편집기에서 "> 프로젝트 설정 > 플레이어 편집" 페이지로 이동 하 여 플레이어 설정으로 이동 합니다.
2. "Windows 스토어" 탭을 선택 합니다.
3. "게시 설정 > 기능" 섹션에서 **웹캠** 및 **마이크** 기능을 확인 합니다.

카메라에서는 한 번에 하나의 작업만 수행할 수 있습니다. `UnityEngine.XR.WSA.WebCam.Mode`Unity 2018 및 이전 또는 unity 2019 이상에서 현재 카메라가 있는 모드를 확인할 수 있습니다 `UnityEngine.Windows.WebCam.Mode` . 사용 가능한 모드는 사진, 동영상 또는 없음입니다.

## <a name="photo-capture"></a>사진 캡처

**네임 스페이스 (Unity 2019 이전):** *UNITYENGINE. XR*<br>
**네임 스페이스 (Unity 2019 이상):** *Unityengine. Windows 웹캠*<br>
**형식:** *사진 캡처*

사진 *캡처* 유형을 사용 하면 사진 비디오 카메라와 사진을 계속 사용할 수 있습니다. 사진 *캡처* 를 사용 하 여 사진을 촬영 하는 일반적인 패턴은 다음과 같습니다.

1. *사진 캡처* 개체 만들기
2. 원하는 설정을 사용 하 여 *CameraParameters* 개체를 만듭니다.
3. *Startphoto Modeasync* 를 통해 사진 모드 시작
4. 원하는 사진 가져오기
    * 필드 해당 사진과 상호 작용
5. 사진 모드 중지 및 리소스 정리

### <a name="common-set-up-for-photocapture"></a>사진 캡처에 대 한 공통 설정

세 가지 용도 모두에서 위의 세 단계를 시작 합니다.

*사진 캡처* 개체를 만들어 시작

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

그런 다음 개체를 저장 하 고, 매개 변수를 설정 하 고, 사진 모드를 시작 합니다.

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

끝으로 여기에 제공 된 동일한 정리 코드를 사용 합니다.

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

이러한 단계를 수행 하 고 나면 캡처할 사진 유형을 선택할 수 있습니다.

### <a name="capture-a-photo-to-a-file"></a>파일에 사진 캡처

가장 간단한 작업은 파일에 직접 사진을 캡처하는 것입니다. 사진은 JPG 또는 PNG로 저장할 수 있습니다.

사진 모드를 성공적으로 시작 하는 경우 사진을 촬영 하 고 디스크에 저장 합니다.

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

사진을 디스크로 캡처한 후 사진 모드를 종료 하 고 개체를 정리 합니다.

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

### <a name="capture-a-photo-to-a-texture2d-with-location"></a>위치를 사용 하 여 Texture2D에 사진 캡처

Texture2D에 데이터를 캡처할 때 프로세스는 디스크에 캡처하는 것과 비슷합니다.

위의 설치 프로세스를 따르세요.

*Onsale Modestarted* 에서 프레임을 메모리로 캡처합니다.

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

그런 다음 결과를 질감에 적용 하 고 위의 일반적인 정리 코드를 사용 합니다.

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

#### <a name="locatable-camera"></a>위치를 찾을 수 있는 카메라

장면에이 텍스처를 놓고 과정이 카메라 매트릭스를 사용 하 여 표시 하려면 다음 코드를 확인의 *OnCapturedPhotoToMemory* 에 추가 합니다 `result.success` .

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

Unity는 포럼의 특정 셰이더에 프로젝션 행렬을 적용 하기 위한 [샘플 코드를 제공](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) 합니다.

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>사진 캡처 및 원시 바이트 조작

메모리 프레임에 있는 원시 바이트와 상호 작용 하려면 Texture2D에 사진을 캡처하는 것 처럼 위와 동일한 설정 *단계를 수행* 합니다. 원시 바이트를 가져와 상호 작용할 수 있는 *OnCapturedPhotoToMemory* 에서 차이가 있습니다.

이 예제에서는 *Setpixels ()* 을 통해 추가 처리 또는 텍스처에 적용 되는 *목록을 <Color>* 만듭니다.

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

## <a name="video-capture"></a>비디오 캡처

**네임 스페이스 (Unity 2019 이전):** *UNITYENGINE. XR*<br>
**네임 스페이스 (Unity 2019 이상):** *Unityengine. Windows 웹캠*<br>
**유형:** *VideoCapture*

*VideoCapture* 는 *사진 캡처* 와 유사 하 게 작동 합니다. 두 가지 차이점은 FPS (초당 프레임 수) 값을 지정 해야 하 고, mp4 파일로는 디스크에 직접 저장 하는 것입니다. *VideoCapture* 를 사용 하는 단계는 다음과 같습니다.

1. *VideoCapture* 개체 만들기
2. 원하는 설정을 사용 하 여 *CameraParameters* 개체를 만듭니다.
3. *Startvideomodeasync* 를 통해 비디오 모드 시작
4. 비디오 녹화 시작
5. 비디오 녹화 중지
6. 비디오 모드 중지 및 리소스 정리

*VideoCapture* 개체 *VideoCapture m_VideoCapture = null* 을 만들어 시작 합니다.

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

다음으로 기록 하 고 시작 하는 데 사용할 매개 변수를 설정 합니다.

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

시작 되 면 기록을 시작 합니다.

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

기록이 시작 된 후에는 중지할 수 있도록 UI 나 동작을 업데이트할 수 있습니다. 여기서는 로그만 합니다.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

나중에 타이머 또는 사용자 입력을 사용 하 여 기록을 중지할 수 있습니다 (예를 들어).

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

기록이 중지 되 면 비디오 모드를 중지 하 고 리소스를 정리 합니다.

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

## <a name="troubleshooting"></a>문제 해결

* 사용 가능한 해결 방법이 없습니다.
  * **웹캠** 기능이 프로젝트에 지정 되어 있는지 확인 합니다.

## <a name="next-development-checkpoint"></a>다음 개발 검사점

앞서 소개한 Unity 개발 검사점 경험을 팔로 하는 경우 혼합 현실 플랫폼 기능과 Api를 탐색 하는 과정을 진행 하 고 있습니다. 여기에서 다음 항목으로 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [포커스 지점](focus-point-in-unity.md)

또는 디바이스나 에뮬레이터에서 앱 배포로 직접 이동합니다.

> [!div class="nextstepaction"]
> [HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋에 배포](../platform-capabilities-and-apis/using-visual-studio.md)

언제든지 [Unity 개발 검사점](unity-development-overview.md#3-advanced-features)으로 돌아갈 수 있습니다.

## <a name="see-also"></a>참고 항목

* [위치를 찾을 수 있는 카메라](../platform-capabilities-and-apis/locatable-camera.md)