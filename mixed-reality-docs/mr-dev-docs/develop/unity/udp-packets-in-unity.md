---
title: Unity UWP 앱의 UDP 패킷
description: 보안 네트워크를 통해 UDP 패킷을 보내고 받도록 Unity UWP 앱을 설정 하는 방법에 대해 알아봅니다.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, UDP 패킷, 소켓, 클라이언트 서버, 끝점, 네트워킹, 원격 컴퓨터, datagramsocket, 샘플, .net
ms.openlocfilehash: b38897f228a62abeb63b7e2ffc0f2a98a840b781
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550523"
---
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="7919e-104">Unity UWP 앱의 UDP 패킷</span><span class="sxs-lookup"><span data-stu-id="7919e-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="7919e-105">UDP 소켓 클라이언트 및 서버를 사용 하 여 UDP 패킷을 받도록 UWP (유니버설 Windows 플랫폼) Unity 앱을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7919e-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="7919e-106">UDP 소켓은 두 끝점에 대 한 연결을 유지 하지 않으므로 원격 컴퓨터 간의 네트워킹을 위한 빠르고 간단한 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="7919e-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="7919e-107">그러나 UDP 소켓이 자동으로 수행 하지 않으므로 패킷이 대상에 수신 되는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7919e-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="7919e-108">설정</span><span class="sxs-lookup"><span data-stu-id="7919e-108">Setup</span></span>

<span data-ttu-id="7919e-109">파일에서 HoloLens manifest.js프로젝트를 열고 다음을 사용 하도록 설정 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7919e-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="7919e-110">**인터넷 (클라이언트 & 서버)**</span><span class="sxs-lookup"><span data-stu-id="7919e-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="7919e-111">**개인 네트워크 (클라이언트 & 서버)**.</span><span class="sxs-lookup"><span data-stu-id="7919e-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="7919e-112">소켓 클라이언트 및 서버 빌드</span><span class="sxs-lookup"><span data-stu-id="7919e-112">Build your socket client and server</span></span> 

<span data-ttu-id="7919e-113">[기본 UDP 소켓 클라이언트 및 서버를 구축](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server)하는 방법에 대 한 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="7919e-113">Follow the instructions for [building a basic UDP socket client and server](/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="7919e-114">[DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) 클래스를 사용 하 여 UDP를 통해 데이터를 보내고 받으며 echo 클라이언트 및 서버를 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7919e-114">You'll be using the [DatagramSocket](/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="7919e-115">또한 사용자 지정 및 복잡 한 사용 사례에 적용 되므로이 문서의 다른 리소스 섹션을 읽는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7919e-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="7919e-116">PC에서 PC로 UDP 패킷을 전송 하는 데 문제가 있는 경우 네트워크에서 이러한 작업을 허용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7919e-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="7919e-117">네트워크에서 어떤 방식으로든 UDP 패킷을 차단 하는 경우 HoloLens 장치에서 수신 대기할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7919e-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="7919e-118">아래 링크에서 전체 DatagramSocket UDP 샘플 앱을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7919e-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7919e-119">도구 설치</span><span class="sxs-lookup"><span data-stu-id="7919e-119">Install the tools</span></span>](/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="7919e-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7919e-120">See also</span></span> 
* [<span data-ttu-id="7919e-121">공유 Holograms 및 Azure Blob Storage/UDP 멀티 캐스트를 사용한 실험</span><span class="sxs-lookup"><span data-stu-id="7919e-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)