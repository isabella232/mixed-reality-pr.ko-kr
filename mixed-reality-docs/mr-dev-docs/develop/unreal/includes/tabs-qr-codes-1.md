---
ms.openlocfilehash: 24348394ef99d4a86e783012544512e1391ef064
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "97717617"
---
# <a name="426"></a>[<span data-ttu-id="0a4f0-101">4.26</span><span class="sxs-lookup"><span data-stu-id="0a4f0-101">4.26</span></span>](#tab/426)

<span data-ttu-id="0a4f0-102">UE 4.26을 사용하는 경우 AR 세션을 시작한 후 QR 코드 추적을 초기화해야 하므로 다음 청사진 설치를 사용하여 약간의 지연을 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a4f0-102">If you're using UE 4.26, we recommend using the following blueprint setup to add a small delay, because QR code tracking must be initialized AFTER starting an AR Session:</span></span>

![지연이 있는 Toggle ARCapture 함수의 청사진](../images/qr-codes-img-01.png)

# <a name="425"></a>[<span data-ttu-id="0a4f0-104">4.25</span><span class="sxs-lookup"><span data-stu-id="0a4f0-104">4.25</span></span>](#tab/425)

<span data-ttu-id="0a4f0-105">UE 4.25에만 해당되는 추가 활성화 단계는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0a4f0-105">There are no additional enabling steps specific to UE 4.25.</span></span>

