---
ms.openlocfilehash: 12634c1fc18366e28a51688b19fc739ea69d37ec
ms.sourcegitcommit: 71c2a4884bd83599e35dd894771a5e43e951b574
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2021
ms.locfileid: "128184631"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| 옵션 | 설명 |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | 연결할 HoloLens 2 디바이스의 IP 주소(및 옵션 포트)를 사용합니다. 포트를 제공하지 않으면 기본값은 8265입니다. |
| `-RemotingBitrate=<bitrate>` | (선택 사항) 기본값은 8000입니다. 최대 네트워크 전송 속도(kb/s)입니다. |
| `-HoloLensRemotingListen` | (선택 사항) 수신 대기 서버 시작 |
| `-HoloLensRemotingListenPort=<port>` | (선택 사항) 수신할 포트를 사용합니다. HoloLens 디바이스에서 PC 또는 VM에 연결하는 데 사용됩니다. |
| `-HoloLens1Remoting=<IP address>` | (4.26에서는 사용되지 않음)연결할 HoloLens 1 디바이스의 IP 주소를 사용합니다. |
| `-eyetracking=WindowsMixedRealityEyeTracker` | (선택 사항) Windows Mixed Reality 시선 추적기를 사용합니다. |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| 옵션 | 설명 |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | 연결할 HoloLens 2 디바이스의 IP 주소(및 선택적 포트, 기본값 8265) 또는 앱이 연결에 대해 수신 대기해야 하는 포트를 사용합니다. |
| `-EnableAudio` | (선택 사항) 원격의 경우 PC 오디오 사용  |
| `-Listen` | (선택 사항) 수신 대기 서버 시작 |
| `-RemotingBitrate=<bitrate>` | (선택 사항) 기본값은 8000입니다. 최대 네트워크 전송 속도(kb/s)입니다. |
| `-RemotingCodec=<codec>` | (선택 사항) 연결 코덱  |
| `-eyetracking=OpenXREyeTracker` | (선택 사항) OpenXR 시선 추적기를 사용합니다. |