---
title: Unity UWP 앱의 UDP 패킷
description: 보안 네트워크를 통해 UDP 패킷을 보내고 받도록 Unity UWP 앱을 설정 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, UDP 패킷, 소켓, 클라이언트 서버, 끝점, 네트워킹, 원격 컴퓨터, datagramsocket, 샘플, .net
ms.openlocfilehash: e4fbdc12a1f7fbca44e14f6ace89ef791a09608f
ms.sourcegitcommit: 8647702638f7600c51df1d89d76c761b52bdf0d7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99566984"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>Unity UWP 앱의 UDP 패킷

UDP 소켓 클라이언트 및 서버를 사용 하 여 UDP 패킷을 받도록 UWP (유니버설 Windows 플랫폼) Unity 앱을 설정할 수 있습니다. UDP 소켓은 두 끝점에 대 한 연결을 유지 하지 않으므로 원격 컴퓨터 간의 네트워킹을 위한 빠르고 간단한 솔루션입니다. 그러나 UDP 소켓이 자동으로 수행 하지 않으므로 패킷이 대상에 수신 되는지 확인 해야 합니다.

## <a name="setup"></a>설치 프로그램

파일에서 HoloLens manifest.js프로젝트를 열고 다음을 사용 하도록 설정 했는지 확인 합니다.
* **인터넷 (클라이언트 & 서버)** 
* **개인 네트워크 (클라이언트 & 서버)**.

## <a name="build-your-socket-client-and-server"></a>소켓 클라이언트 및 서버 빌드 

[기본 UDP 소켓 클라이언트 및 서버를 구축](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server)하는 방법에 대 한 지침을 따르세요. [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) 클래스를 사용 하 여 UDP를 통해 데이터를 보내고 받으며 echo 클라이언트 및 서버를 형성 합니다. 또한 사용자 지정 및 복잡 한 사용 사례에 적용 되므로이 문서의 다른 리소스 섹션을 읽는 것이 좋습니다. 

> [!IMPORTANT]
> PC에서 PC로 UDP 패킷을 전송 하는 데 문제가 있는 경우 네트워크에서 이러한 작업을 허용 하는지 확인 합니다. 네트워크에서 어떤 방식으로든 UDP 패킷을 차단 하는 경우 HoloLens 장치에서 수신 대기할 수 없습니다.

아래 링크에서 전체 DatagramSocket UDP 샘플 앱을 다운로드할 수 있습니다.

> [!div class="nextstepaction"]
> [도구 설치](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>참고 항목 
* [공유 Holograms 및 Azure Blob Storage/UDP 멀티 캐스트를 사용한 실험](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)