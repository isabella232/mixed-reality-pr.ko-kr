---
title: 위치를 찾을 수 있는 카메라
description: HoloLens 전면 카메라, 작동 방법 및 개발자가 사용할 수 있는 프로필 및 해상도에 대한 일반 정보입니다.
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: camera, hololens, color camera, front facing, hololens 2, cv, computer vision, fiducial, markers, qr code, qr, photo, video
ms.openlocfilehash: 33faa4107c6b44041958f422329d8967958a666606a474949184628abcd12544
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217099"
---
# <a name="locatable-camera"></a>위치를 찾을 수 있는 카메라

HoloLens 디바이스 전면에 탑재된 전 세계 카메라를 포함하여 앱에서 사용자에게 표시되는 내용을 볼 수 있습니다. 개발자는 스마트폰, 휴대용 또는 데스크톱에서 색 카메라를 사용할 때와 마찬가지로 카메라에 액세스하고 제어할 수 있습니다. 모바일 및 데스크톱에서 작동하는 동일한 유니버설 Windows [미디어 캡처](/uwp/api/Windows.Media.Capture.MediaCapture) 및 windows media foundation API는 HoloLens 작동합니다. Unity는 [이러한 Windows API를](../unity/locatable-camera-in-unity.md) HoloLens 카메라 사용 기능을 추상화하도록 래핑했습니다. 기능 작업에는 일반 사진 및 비디오(홀로그램을 사용하거나 포함하지 않는 경우) 및 장면에서 카메라의 위치 및 큐브 뷰 찾기가 포함됩니다.

## <a name="device-camera-information"></a>디바이스 카메라 정보

### <a name="hololens-first-generation"></a>HoloLens(1세대)

* 자동 흰색 균형, 자동 노출 및 전체 이미지 처리 파이프라인을 사용하여 포커스 PV(사진/비디오) 카메라를 수정했습니다.
* 카메라가 활성 상태일 때마다 전 세계를 향하여 흰색 개인 정보 LED가 켜집니다.
* 카메라는 30, 24, 20, 15 및 5 fps에서 다음 모드(모든 모드는 16:9 가로 세로 비율임)를 지원합니다.

  |  동영상  |  미리 보기  |  아직도  |  가로 보기 필드(H-FOV) |  권장 사용량 | 
  |----------|----------|----------|----------|----------|
  |  1280x720 |  1280x720 |  1280x720 |  45 deg  |  (비디오 안정화가 있는 기본 모드) | 
  |  해당 없음 |  해당 없음 |  2048x1152 |  67 deg |  고해상도 여전히 이미지 | 
  |  1408x792 |  1408x792 |  1408x792 |  48 deg |  비디오 안정화 전에 오버스캐닝(패딩) 해상도 | 
  |  1344x756 |  1344x756 |  1344x756 |  67 deg |  오버스캐스가 있는 대형 FOV 비디오 모드 | 
  |  896x504 |  896x504 |  896x504 |  48 deg |  이미지 처리 작업에 대한 저전력/저해상도 모드 | 

### <a name="hololens-2"></a>HoloLens 2

* 자동 흰색 균형 조정, 자동 노출 및 전체 이미지 처리 파이프라인이 있는 PV(사진/비디오) 카메라 자동 포커스
* 카메라가 활성 상태일 때마다 전 세계를 향할 수 있는 흰색 개인 정보 LED가 켜집니다.
* HoloLens 2 다양한 카메라 프로필을 지원합니다. [카메라 기능을 검색하고 선택하는](/windows/uwp/audio-video-camera/camera-profiles)방법을 알아봅니다.
* 카메라는 다음 프로필 및 해상도를 지원합니다(모든 비디오 모드는 16:9 가로 세로 비율임).
  
  | 프로필                                         | 동영상     | 미리 보기   | 아직도     | 프레임 속도 | 가로 보기 필드(H-FOV) | 권장 사용량                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | Legacy,0 BalancedVideoAndPhoto,100             | 2272x1278 | 2272x1278 |           | 15.30       | 64.69                            | 고품질 비디오 녹화                |
  | Legacy,0 BalancedVideoAndPhoto,100             | 896x504   | 896x504   |           | 15.30       | 64.69                            | 고품질 사진 캡처를 위한 미리 보기 스트림 |
  | Legacy,0 BalancedVideoAndPhoto,100             |           |           | 3904x2196 |             | 64.69                            | 고품질 사진 캡처                  |
  | BalancedVideoAndPhoto, 120                       | 1952x1100 | 1952x1100 | 1952x1100 | 15.30       | 64.69                            | 긴 기간 시나리오                     |
  | BalancedVideoAndPhoto, 120                       | 1504x846  | 1504x846  |           | 15.30       | 64.69                            | 긴 기간 시나리오                     |
  | VideoConferencing,100                           | 1952x1100 | 1952x1100 | 1952x1100 | 15,30,60    | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | 비디오 회의,100                           | 1504x846  | 1504x846  |           | 5,15,30,60  | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1920x1080 | 1920x1080 | 1920x1080 | 15,30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1280x720  | 1280x720  | 1280x720  | 15,30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 1128x636  |           |           | 15,30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 960 x 540   |           |           | 15,30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 760x428   |           |           | 15,30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 640x360   |           |           | 15,30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 500x282   |           |           | 15,30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |
  | Videoconferencing,100 BalancedVideoAndPhoto,120 | 424x240   |           |           | 15,30       | 64.69                            | 비디오 회의, 긴 기간 시나리오 |

> [!NOTE]
> 고객은 [혼합 현실 캡처를](/hololens/holographic-photos-and-videos) 활용하여 홀로그램 및 비디오 안정화를 포함한 앱의 비디오 또는 사진을 찍을 수 있습니다.
>
>개발자는 고객이 콘텐츠를 캡처할 때 최대한 잘 보이도록 앱을 만들 때 고려해야 할 사항이 있습니다. 앱 내에서 직접 혼합 현실 캡처를 사용하도록 설정(및 사용자 지정)할 수도 있습니다. [개발자를 위한 혼합 현실 캡처에서](mixed-reality-capture-for-developers.md)자세히 알아보세요.

## <a name="locating-the-device-camera-in-the-world"></a>세계에서 디바이스 카메라 찾기

HoloLens 사진 및 비디오를 촬영할 때 캡처된 프레임에는 세계에서 카메라의 위치와 카메라의 렌즈 모델이 포함됩니다. 이를 통해 애플리케이션은 증강 이미징 시나리오에서 실제 카메라의 위치를 추론할 수 있습니다. 개발자는 선호하는 이미지 처리 또는 사용자 지정 컴퓨터 비전 라이브러리를 사용하여 자신만의 시나리오를 창작할 수 있습니다.

HoloLens 설명서의 다른 곳에 있는 "카메라"는 "가상 게임 카메라"(앱이 렌더링하는 가상 게임 카메라)를 참조할 수 있습니다. 달리 표시하지 않는 한 이 페이지의 "카메라"는 실제 RGB 색 카메라를 나타냅니다.

### <a name="using-unity"></a>Unity 사용

'CameraIntrinsics' 및 'CameraCoordinateSystem'에서 애플리케이션/세계 좌표계로 이동하려면 [Unity에서 찾기 가능한 카메라](../unity/locatable-camera-in-unity.md) 문서의 지침을 따르세요.  CameraToWorldMatrix는 PhotoCaptureFrame 클래스에서 자동으로 제공되므로 아래에서 설명한 CameraCoordinateSystem 변환에 대해 걱정할 필요가 없습니다.

### <a name="using-mediaframereference"></a>MediaFrameReference 사용

이러한 지침은 [MediaFrameReference](/uwp/api/windows.media.capture.frames.mediaframereference) 클래스를 사용하여 카메라에서 이미지 프레임을 읽는 경우에 적용됩니다.

각 이미지 프레임(사진 또는 비디오)에는 캡처 시 카메라에 [루팅된 SpatialCoordinateSystem이](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 포함되어 있으며 [MediaFrameReference](/uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)의 [CoordinateSystem](/uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) 속성을 사용하여 액세스할 수 있습니다. 각 프레임에는 [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 속성에서 찾을 수 있는 카메라 렌즈 모델에 대한 설명이 포함되어 있습니다. 이러한 변환은 픽셀을 생성한 광자에서 가져온 경로를 나타내는 3D 공간의 광선을 각 픽셀에 대해 정의합니다. 이러한 광선은 프레임의 좌표계에서 다른 좌표계(예: 고정 참조 프레임)로 변환을 얻어 [앱의](../../design/coordinate-systems.md#stationary-frame-of-reference)다른 콘텐츠와 관련될 수 있습니다. 

각 이미지 프레임은 다음을 제공합니다.
* 픽셀 데이터(RGB/NV12/JPEG/등 형식)
* 캡처 위치의 [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem)
* 카메라의 렌즈 모드를 포함하는 [CameraIntrinsics](/uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) 클래스

[HolographicFaceTracking 샘플은](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) 카메라의 좌표계와 사용자 고유의 애플리케이션 좌표계 간의 변환을 쿼리하는 매우 간단한 방법을 보여 줍니다.

### <a name="using-media-foundation"></a>미디어 파운데이션 사용

미디어 파운데이션 직접 사용하여 카메라에서 이미지 프레임을 읽는 경우 이 샘플 코드와 같이 각 프레임의 [MFSampleExtension_CameraExtrinsics 특성](/windows/win32/medfound/mfsampleextension-cameraextrinsics) 및 [MFSampleExtension_PinholeCameraIntrinsics 특성을](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) 사용하여 애플리케이션의 다른 좌표계를 기준으로 카메라 프레임을 찾을 수 있습니다.

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a>왜곡 오류

HoloLens 비디오 및 여전히 이미지 스트림은 애플리케이션에서 프레임을 사용할 수 있게 되기 전에 시스템의 이미지 처리 파이프라인에서 삭제되지 않습니다(미리 보기 스트림에는 왜곡된 원래 프레임이 포함). CameraIntrinsics만 사용할 수 있으므로 애플리케이션은 이미지 프레임이 완벽한 핀번 카메라를 나타낸다고 가정해야 합니다.

HoloLens(1세대)에서는 프레임 메타데이터에서 CameraIntrinsics를 사용할 때 이미지 프로세서의 삭제되지 않은 함수가 여전히 최대 10픽셀의 오류를 남겨 둘 수 있습니다. 많은 사용 사례에서 이 오류는 중요하지 않지만, 예를 들어 실제 포스터/표식에 홀로그램을 맞추는 경우 <10픽셀 오프셋(2미터 떨어진 홀로그램의 경우 약 11mm)을 발견할 경우 이러한 왜곡 오류가 원인일 수 있습니다. 

## <a name="locatable-camera-usage-scenarios"></a>찾기 가능한 카메라 사용 시나리오

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a>캡처된 세계 사진 또는 비디오 표시

디바이스 카메라 프레임에는 이미지를 촬영할 때 디바이스의 위치를 정확하게 표시하는 데 사용할 수 있는 "Camera To World" 변환이 함께 제공됩니다. 예를 들어 이 위치(CameraToWorld.MultiplyPoint(Vector3.zero))에 작은 홀로그램 아이콘을 배치하고 카메라가 있는 방향으로 작은 화살표를 그릴 수도 있습니다(CameraToWorld.MultiplyVector(Vector3.forward)).

### <a name="tag--pattern--poster--object-tracking"></a>태그/패턴/포스터/개체 추적

많은 혼합 현실 애플리케이션은 인식 가능한 이미지 또는 시각적 패턴을 사용하여 추적 가능한 공간을 만듭니다. 그런 다음 해당 지점을 기준으로 개체를 렌더링하거나 알려진 위치를 만드는 데 사용됩니다. HoloLens 몇 가지 용도로는 fiducials(예: QR 코드가 있는 TV 모니터)로 태그가 지정된 실제 개체 찾기, fiducials에 홀로그램 배치, Wi-Fi를 통해 HoloLens 통신하도록 설정된 태블릿과 같은 HoloLens 이외의 디바이스와 시각적으로 페어링 등이 있습니다.

시각적 패턴을 인식하고 애플리케이션 세계 공간에 개체를 배치하려면 몇 가지가 필요합니다.
1. QR 코드, AR 태그, 얼굴 찾기, 원 추적기, OCR 등과 같은 이미지 패턴 인식 도구 키트
2. 런타임에 이미지 프레임을 수집하고 인식 계층에 전달합니다.
3. 이미지 위치를 다시 세계 위치 또는 세계 광선으로 보호 해제합니다. 
4. 이러한 전 세계 위치에 가상 모델 배치

몇 가지 중요한 이미지 처리 링크:
* [OpenCV](https://opencv.org/)
* [QR 태그](https://en.wikipedia.org/wiki/QR_code)
* [FaceSDK](https://research.microsoft.com/projects/facesdk/)
* [Microsoft Translator](https://www.microsoft.com/translator/business)

특히 장기 실행 이미지 인식 알고리즘을 처리할 때 대화형 애플리케이션 프레임 속도를 유지하는 것이 중요합니다. 이러한 이유로 일반적으로 다음 패턴을 사용합니다.
1. 주 스레드: 카메라 개체를 관리합니다.
2. 주 스레드: 새 프레임 요청(비동기)
3. 주 스레드: 추적 스레드에 새 프레임 전달
4. 추적 스레드: 이미지를 처리하여 주요 지점 수집
5. 주 스레드: 가상 모델을 찾은 주요 지점과 일치하도록 이동
6. 주 스레드: 2단계에서 반복

일부 이미지 표식 시스템은 단일 픽셀 위치만 제공 합니다 (다른 사용자는이 섹션이 필요 하지 않은 전체 변환을 제공 함) .이는 가능한 위치의 광선과 동일 합니다. 단일 3d 위치로 이동 하려면 여러 광선을 활용 하 여 대략적인 교차를 기준으로 최종 결과를 찾을 수 있습니다. 이 작업을 수행하려면 다음 작업이 필요합니다.
1. 여러 카메라 이미지를 수집 하는 루프 가져오기
2. 연결 된 기능 지점과 해당 세계 광선 찾기
3. 여러 가지 세계 광선을 포함 하는 기능 사전이 있는 경우 다음 코드를 사용 하 여 이러한 광선의 교차를 해결할 수 있습니다.

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

두 개 이상의 추적 된 태그 위치가 지정 된 경우 사용자의 현재 시나리오에 맞게 모델링 된 장면을 배치할 수 있습니다. 중력을 가정할 수 없는 경우 세 가지 태그 위치가 필요 합니다. 대부분의 경우 흰색 구는 실시간 추적 된 태그 위치를 나타내고 파란색 구는 모델링 된 태그 위치를 나타내는 색 구성표를 사용 합니다. 이를 통해 사용자는 맞춤 품질을 시각적으로 측정할 수 있습니다. 모든 응용 프로그램에서 다음 설정을 가정 합니다.
* 두 개 이상의 모델링 한 태그 위치
* 장면에 있는 하나의 ' 보정 공간 '은 태그의 부모입니다.
* 카메라 기능 식별자
* 동작-보정 공간을 이동 하 여 모델링 된 태그를 실시간 태그에 맞춰 정렬 합니다. 즉, 다른 연결에 상대적인 위치에 있으므로 모델링 된 마커 자체가 아니라 부모 공간을 이동 하는 것은 주의를 기울여야 합니다.

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a>Led 또는 다른 인식기 라이브러리를 사용 하 여 태그가 지정 된 고정 또는 실제 개체/얼굴 이동 추적 또는 식별

예:
* Led가 있는 산업 로봇 (또는 느린 개체 이동에 대 한 QR 코드)
* 대화방의 개체 식별 및 인식
* 대화방에서 사람을 식별 하 고 인식 합니다 (예: 얼굴에 holographic 접점 카드 배치).

## <a name="see-also"></a>추가 정보
* [과정이 카메라 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [Unity의 위치를 찾을 수 있는 카메라](../unity/locatable-camera-in-unity.md)
* [혼합 현실 캡처](/hololens/holographic-photos-and-videos)
* [개발자를 위한 혼합 현실 캡처](mixed-reality-capture-for-developers.md)
* [미디어 캡처 소개](/windows/uwp/audio-video-camera/)
* [Holographic face 추적 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)