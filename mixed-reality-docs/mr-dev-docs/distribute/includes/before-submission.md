---
ms.openlocfilehash: c9ce068adc3b4b550ecaf1b1c106d9b12f363ac0
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443511"
---
# <a name="hololens"></a>[HoloLens](#tab/hololens)

HoloLens 응용 프로그램이 있는 경우 아래 표에서 선호 하는 [배포 옵션](../distribute-overview.md#distribution-options) 을 선택 합니다. Microsoft Store에 게시 하는 경우 [앱 내 구매](../in-app-purchases.md) 를 추가 하 여 콘텐츠를 수익 창출 수 있습니다.

# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

Windows Mixed Reality 헤드셋을 대상으로 하는 몰입 형 응용 프로그램을 사용 하는 경우 3D 앱 시작 관리자를 만든 다음 아래 표에서 기본 [배포 옵션](../distribute-overview.md#distribution-options) 을 선택 합니다. Microsoft Store에 게시 하는 경우 [앱 내 구매](../in-app-purchases.md) 를 추가 하 여 콘텐츠를 수익 창출 수 있습니다.

### <a name="designing-3d-app-launchers-for-vr"></a>VR 용 3D 앱 관리자 디자인 

3D 앱 시작은 사용자가 몰입 형 헤드셋을 배치할 때마다 나타나는 Windows Mixed Reality 홈 환경에서 개체로 표시 됩니다. 이러한 개체는 사용자가 원하는 대로 만들고 사용자 지정할 수 있지만, 크기 조정, 유형, 색 선택, 질감 등을 비롯 한 적절 [한 디자인 관행](../3d-app-launcher-design-guidance.md) 을 중단 하 여 가상 환경에서 제공 하는 것이 좋습니다.

### <a name="modeling-and-exporting-3d-app-launchers"></a>3D 앱 응용 프로그램 모델링 및 내보내기

3D 앱 시작 관리자에 대 한 아이디어를 설정 하 고 나면 자산 파일 형식, 삼각형 수, 질감 크기, 애니메이션 길이 및 자산 최적화를 비롯 한 Microsoft Store 요구 사항을 충족 하는지 확인 해야 합니다. 이 프로세스는 매우 기술적 이므로 [3d 모델 생성](../creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 문서를 사용 하 여 모든 상자를 선택 하는 것이 좋습니다. 이 제작 사양을 충족 하지 않는 자산은 Windows Mixed Reality 홈에서 렌더링 되지 않습니다.

### <a name="adding-3d-app-launchers-in-your-apps"></a>앱에서 3D 앱 관리자 추가

3D 앱 시작 관리자가 Windows Mixed Reality 제작 지침을 충족 하는지 확인 한 후 Windows Mixed Reality 홈 환경에서 응용 프로그램의 기본 2D 시작 관리자를 재정의 하는 데 사용할 수 있습니다. 3D 앱 시작 관리자를 응용 프로그램에 통합 하는 프로세스는 개발 중인 응용 프로그램의 형식에 따라 달라 집니다.

* [UWP 앱](../implementing-3d-app-launchers.md)
* [Win32 앱](../implementing-3d-app-launchers-win32.md)

### <a name="optional-placing-3d-models-in-the-windows-mixed-reality-home"></a>필드 Windows Mixed Reality 홈에 3D 모델 배치

추가 된 보너스로, 일부 2D 응용 프로그램을 사용 하면 3D 모델을 Windows Mixed Reality 홈에 직접 추가 하거나 전체 3D에서 추가 검사를 수행할 수 있습니다. 모델 추가 프로토콜을 사용 하 여 웹 사이트나 응용 프로그램의 3D 모델을 Windows Mixed Reality 홈으로 보낼 수 있습니다. 여기에서 3D 앱 시작, 2D 앱 및 holograms와 같이 유지 됩니다. [Windows Mixed Reality 홈에서 3d 모델을 준비 하는 방법](../enable-placement-of-3d-models-in-the-home.md) 을 확인 하 여 고유한 앱을 생동감 있게 하는 방법에 대 한 자세한 내용과 지침을 알아보세요.