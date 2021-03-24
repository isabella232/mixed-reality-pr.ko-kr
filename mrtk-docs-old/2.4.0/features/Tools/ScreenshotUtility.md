---
title: ScreenshotUtility
description: MRTK에서 스크린샷 도구를 사용하는 방법에 대한 설명서
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 개발, MRTK
ms.openlocfilehash: 6aafcf6602caae94cf69bc62faf02601de830bbd
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687893"
---
# <a name="screenshot-utility"></a><span data-ttu-id="f87de-104">스크린샷 유틸리티</span><span class="sxs-lookup"><span data-stu-id="f87de-104">Screenshot utility</span></span>

<span data-ttu-id="f87de-105">Unity에서 문서화 및 판촉 이미지를 위해 스크린샷을 찍는 것은 부담스러울 수 있으며, 출력도 종종 바람직하지 않게 보입니다.</span><span class="sxs-lookup"><span data-stu-id="f87de-105">Often taking screenshots in Unity for documentation and promotional imagery can be burdensome and the output often looks less than desirable.</span></span> <span data-ttu-id="f87de-106">여기에서 `ScreenshotUtility`(xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) 클래스가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f87de-106">This is where the `ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) class comes into play.</span></span>

<span data-ttu-id="f87de-107">ScreenshotUtility 클래스는 Unity 편집기 내의 메뉴 항목 및 공용 API를 통해 스크린샷을 촬영하는 데 도움을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f87de-107">The ScreenshotUtility class aides in taking screenshots via menu items and public APIs within the Unity editor.</span></span> <span data-ttu-id="f87de-108">스크린샷은 다양한 해상도와 투명하고 선명한 색상으로 캡처하여 쉽게 이미지를 합성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f87de-108">Screenshots can be captured at various resolutions and with transparent clear colors for use in easy post compositing of images.</span></span> <span data-ttu-id="f87de-109">독립 실행형 빌드에서 스크린샷을 찍는 것은 이 도구에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f87de-109">Taking screenshots from a standalone build is not supported by this tool.</span></span>

## <a name="taking-screenshots"></a><span data-ttu-id="f87de-110">스크린샷 찍기</span><span class="sxs-lookup"><span data-stu-id="f87de-110">Taking screenshots</span></span>

<span data-ttu-id="f87de-111">편집기에서 *Mixed Reality Toolkit->Utilities->Take Screenshot* 을 선택하고 원하는 옵션을 선택하면 스크린샷을 쉽게 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f87de-111">Screenshots can be easily capture while in the editor by selecting *Mixed Reality Toolkit->Utilities->Take Screenshot* and then selecting your desired option.</span></span> <span data-ttu-id="f87de-112">게임을 플레이하지 않고 캡처하는 경우 게임 창 탭이 표시되는지 확인하세요. 스크린샷이 저장되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f87de-112">Make sure to have the game window tab visible if capturing while not playing, or a screenshot may not be saved.</span></span>

<span data-ttu-id="f87de-113">기본적으로 모든 스크린샷은 [임시 캐시 경로](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)에 저장되며 스크린샷 경로는 Unity 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f87de-113">By default, all screenshots are saved to your [temporary cache path](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html), the path to the screenshot will be displayed in the Unity console.</span></span>

![스크린샷 유틸리티 메뉴 항목](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a><span data-ttu-id="f87de-115">스크린샷 캡처 예</span><span class="sxs-lookup"><span data-stu-id="f87de-115">Example screenshot capture</span></span>

<span data-ttu-id="f87de-116">아래 스크린샷은 *"4x 해상도(투명 배경)"* 옵션으로 캡처되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f87de-116">The below screenshot was captured with the *"4x Resolution (Transparent Background)"* option.</span></span> <span data-ttu-id="f87de-117">이렇게 하면 일반적으로 투명 픽셀로 저장된 투명 색상으로 표시되는 모든 픽셀이 고해상도 이미지를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="f87de-117">This outputs a high-resolution image with whatever pixels normally represented by the clear color saved as transparent pixels.</span></span> <span data-ttu-id="f87de-118">이 기법을 사용하면 개발자가 이 이미지를 다른 이미지 위에 겹쳐서 스토어 또는 기타 언론 매체에 애플리케이션을 소개할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f87de-118">This technique helps developers showcase their application for the store, or other media outlets, by overlaying this image on top of other imagery.</span></span>

![스크린샷 유틸리티 캡처 예](../Images/ScreenshotUtility/MRTK_ScreenshotUtility_Example_Capture.png)
