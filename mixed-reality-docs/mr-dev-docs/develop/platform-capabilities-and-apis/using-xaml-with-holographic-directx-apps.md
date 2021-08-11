---
title: 홀로그램 DirectX 앱에서 XAML 사용
description: DirectX 앱에서 2D XAML 보기와 몰입형 보기 간 전환의 영향과 XAML 보기와 몰입형 보기를 효율적으로 활용하는 방법을 설명합니다.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows 혼합 현실, UWP, 앱 보기 관리, xaml, 키보드, 연습, DirectX
ms.openlocfilehash: 3c7edfdf4ff2ed629699dca0514efabc9ce7241cb1781e4b9c914ad4bff1f900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220949"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>홀로그램 DirectX 앱에서 XAML 사용

> [!NOTE]
> 이 문서는 레거시 WinRT 네이티브 API와 관련이 있습니다.  새 네이티브 앱 프로젝트의 경우 **[OpenXR API](../native/openxr-getting-started.md)** 를 사용하는 것이 좋습니다.

이 항목에서는 DirectX 앱에서 [2D XAML 보기와 몰입형 보기](../../design/app-views.md) 간 전환의 영향과 XAML 보기와 몰입형 보기를 효율적으로 활용하는 방법에 대해 설명합니다.

## <a name="xaml-view-switching-overview"></a>XAML 보기 전환 개요

HoloLens 나중에 2D XAML 보기를 표시할 수 있는 몰입형 앱은 먼저 해당 XAML 보기를 초기화하고 해당 위치에서 몰입형 보기로 즉시 전환해야 합니다. XAML은 앱이 작업을 수행할 수 있도록 하기 전에 로드되며, 이로 인해 시작 시간이 약간 늘어나게 됩니다. XAML은 백그라운드에서 유지되는 동안 앱 프로세스에서 메모리 공간을 계속 차지합니다. 시작 지연 및 메모리 사용량은 네이티브 보기로 전환하기 전에 앱이 XAML로 수행하는 내용에 따라 달라집니다. 처음에는 몰입형 보기를 시작하는 것 외에 XAML 시작 코드에서 아무 것도 수행하지 않는 경우 영향은 사소해야 합니다. 또한 홀로그램 렌더링이 몰입형 보기에 직접 수행되므로 해당 렌더링에 대한 XAML 관련 제한을 피할 수 있습니다.

CPU 및 GPU 모두에 대한 메모리 사용량 수입니다. Direct3D 11은 가상 그래픽 메모리를 교환할 수 있지만 XAML GPU 리소스의 일부 또는 전부를 교체하지 못할 수 있으며 성능이 눈에 띄게 저하될 수 있습니다. 어떤 방법이든, 필요하지 않은 XAML 기능을 로드하지 않으면 앱에 더 많은 공간을 남겨 두고 더 나은 환경을 제공할 수 있습니다.

## <a name="xaml-view-switching-workflow"></a>XAML 뷰 전환 워크플로

XAML에서 몰입형 모드로 직접 진행되는 앱의 워크플로는 다음과 같습니다.
* 앱은 2D XAML 보기에서 시작됩니다.
* 앱의 XAML 시작 시퀀스는 현재 시스템에서 홀로그램 렌더링을 지원하는지 검색합니다.
* 그렇다면 앱은 몰입형 보기를 만들어 전경으로 바로 가져옵니다. XAML 보기의 렌더링 클래스 및 자산 로드를 포함하여 Windows Mixed Reality 디바이스에서 필요하지 않은 모든 경우 XAML 로드를 건너뜁니다. 앱이 키보드 입력에 XAML을 사용하는 경우에도 해당 입력 페이지를 만들어야 합니다.
* 그렇지 않은 경우 XAML 보기는 평소처럼 비즈니스를 계속할 수 있습니다.

## <a name="tip-for-rendering-graphics-across-both-views"></a>두 보기에서 그래픽을 렌더링하기 위한 팁

앱이 Windows Mixed Reality XAML 보기에 대해 DirectX에서 렌더링을 어느 정도 구현해야 하는 경우 두 보기에서 모두 사용할 수 있는 렌더러 하나를 만드는 것이 가장 좋습니다. 렌더러는 두 보기에서 모두 액세스할 수 있는 하나의 인스턴스여야 하며, 2D와 홀로그램 렌더링 간에 전환해야 합니다. 이러한 방식으로 GPU 자산은 한 번만 로드되어 보기를 전환할 때 로드 시간, 메모리 영향 및 교환된 리소스의 양을 줄입니다.
