---
title: Unity의 HP 반향 G2 컨트롤러
description: SteamVR 및 Windows Mixed Reality에서 HP 반향 G2 컨트롤러를 사용 하는 방법에 대 한 지침입니다.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, 반향, 반향 G2, HP 반향 G2, 혼합 현실, 개발, 동작 컨트롤러, 사용자 입력, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 기능, holograms, 게임 개발
ms.openlocfilehash: 3add2ae52fbaba087da257212e1d8ddfdffe702a
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638390"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="71577-104">Unity의 HP 반향 G2 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="71577-104">HP Reverb G2 Controllers in Unity</span></span>

## <a name="getting-started"></a><span data-ttu-id="71577-105">시작</span><span class="sxs-lookup"><span data-stu-id="71577-105">Getting started</span></span>

<span data-ttu-id="71577-106">SteamVR 용으로 개발 중이거나 Windows Mixed Reality 입력 API (XR)를 사용 하는 경우 HP 반향 G2 컨트롤러를 사용 하는 데 필요한 추가 설치는 없습니다. WSA. 입력).</span><span class="sxs-lookup"><span data-stu-id="71577-106">There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input).</span></span> <span data-ttu-id="71577-107">그러나 SteamVR을 사용 하지 않는 한, A, B, X, Y 단추 및는 현재 입력 관리자를 통해 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71577-107">However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR.</span></span> <span data-ttu-id="71577-108">추가 반향 G2 입력에 대 한 지원은 가까운 장래에 제공 될 예정 이므로 다시 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="71577-108">Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!</span></span>

## <a name="porting-existing-applications"></a><span data-ttu-id="71577-109">기존 응용 프로그램 포팅</span><span class="sxs-lookup"><span data-stu-id="71577-109">Porting existing applications</span></span>

<span data-ttu-id="71577-110">Windows Mixed Reality 모던 헤드셋에 대해 개발 중인 기존 앱이 이미 있는 경우에는 [이식 가이드](../porting-apps/porting-guides.md) 및 [프로젝트 설정](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) 섹션에서 일반적인 제안을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="71577-110">If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.</span></span>

## <a name="mapping-input"></a><span data-ttu-id="71577-111">매핑 입력</span><span class="sxs-lookup"><span data-stu-id="71577-111">Mapping input</span></span>

<span data-ttu-id="71577-112">새 컨트롤러에 대 한 입력 매핑 및 실행 준비가 완료 되 면 몰입 형 포팅 가이드의 [입력 매핑](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) 섹션에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="71577-112">When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide.</span></span> <span data-ttu-id="71577-113">Unity에서 입력을 구성 하는 방법에 대 한 지침은 참조를 위한 전체 [단추 및 축 매핑 표와](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) 함께 [제스처 및 동작 컨트롤러](gestures-and-motion-controllers-in-unity.md)에 자세히 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71577-113">Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="71577-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71577-114">See also</span></span>
* [<span data-ttu-id="71577-115">SteamVR용 업데이트</span><span class="sxs-lookup"><span data-stu-id="71577-115">Updating for SteamVR</span></span>](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)