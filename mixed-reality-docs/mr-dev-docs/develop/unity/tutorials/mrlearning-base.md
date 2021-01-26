---
title: 자습서 개요 및 목표
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: b7e04a03f01beb1438f6f723c3938d05a60c9131
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581164"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="12cc6-104">1. 개요 및 목표</span><span class="sxs-lookup"><span data-stu-id="12cc6-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="12cc6-105">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="12cc6-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="12cc6-106"><strong>과정</strong></span><span class="sxs-lookup"><span data-stu-id="12cc6-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="12cc6-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="12cc6-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="12cc6-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="12cc6-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="12cc6-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="12cc6-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="12cc6-110">✔️</span><span class="sxs-lookup"><span data-stu-id="12cc6-110">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="12cc6-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="12cc6-111">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="12cc6-112">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="12cc6-112">Prerequisites</span></span>

* <span data-ttu-id="12cc6-113">올바른 [도구가 설치](../../install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="12cc6-113">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="12cc6-114">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="12cc6-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="12cc6-115">몇 가지 기본 C# 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="12cc6-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="12cc6-116">[개발용으로 구성](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="12cc6-116">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="12cc6-117">Unity 2019.2.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="12cc6-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="12cc6-118">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다.</span><span class="sxs-lookup"><span data-stu-id="12cc6-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="12cc6-119">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="12cc6-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="12cc6-120">다음 단원: 2. 프로젝트 및 첫 번째 애플리케이션 초기화</span><span class="sxs-lookup"><span data-stu-id="12cc6-120">Next lesson: 2. Initializing your project and first application</span></span>](./mr-learning-base-02.md)