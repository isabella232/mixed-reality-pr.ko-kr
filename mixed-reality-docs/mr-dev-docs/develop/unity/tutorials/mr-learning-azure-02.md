---
title: Azure Storage 통합
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 Azure Table Storage 및 Azure Blob Storage를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, hololens 2, azure storage, azure cloud services, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 190e64c1de3d4e6724b428ea01cbd30cedbc07c2a7d76176cacad11e8bd84eae
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196486"
---
# <a name="2-integrating-azure-storage"></a>2. Azure Storage 통합

이 자습서에서는 엔터티 데이터를 Azure Table 스토리지에 저장하고 썸네일 이미지를 Azure Blob 스토리지에 저장하는 방법에 대해 알아봅니다. 이 기능을 사용하면 세션과 디바이스에서 ID, 이름, 썸네일 이미지 등과 같은 데이터를 사용하여 *추적된 개체* 를 클라우드에 저장하고 검색할 수 있습니다.

## <a name="objectives"></a>목표

* Azure 스토리지에 대한 기본 사항 알아보기
* Table 스토리지에서 데이터를 저장, 수정 및 검색하는 방법 알아보기
* Blob 스토리지에서 이미지를 저장 및 삭제하는 방법 알아보기

## <a name="understanding-azure-storage"></a>Azure 스토리지 이해

**Azure 스토리지** 는 클라우드에서 다양한 시나리오와 요구 사항을 처리할 수 있는 Microsoft 스토리지 솔루션입니다. 이는 크기를 대규모로 조정할 수 있고 개발자가 쉽게 접근할 수 있습니다. 모든 서비스는 **Azure 스토리지 계정** 의 지원을 통해 사용할 수 있습니다. 사용 사례에서는 *Table 스토리지* 및 *Blob 스토리지* 를 사용합니다.

[Azure 스토리지 서비스](/azure/storage/blobs/storage-blobs-overview)에 대해 자세히 알아보세요.

### <a name="azure-table-storage"></a>Azure Table 스토리지

이 서비스를 사용하면 데이터를 NoSQL 방식으로 저장할 수 있습니다. 이 프로젝트에서는 이름, 설명, 공간 앵커 ID 등과 같은 *추적된 개체* 에 대한 정보를 저장하기 위해 이 스토리지를 사용합니다.

데모 애플리케이션의 경우 두 개의 테이블이 필요합니다. 하나는 자습서([Azure Custom Vision 통합](mr-learning-azure-03.md))에서 학습된 모델의 상태에 대한 정보와 함께 프로젝트 관련 정보를 더 많이 저장하려는 테이블이고, 다른 하나는 *추적된 개체* 에 대한 정보를 저장하는 테이블입니다.

[Azure Table 스토리지](/azure/storage/tables/table-storage-overview)에 대해 자세히 알아보세요.

### <a name="azure-blob-storage"></a>Azure Blob 스토리지

이 서비스를 사용하면 큰 이진 파일을 저장할 수 있습니다. 이 서비스는 *추적된 개체* 에 대해 찍은 사진을 썸네일 이미지로 저장하는 데 사용됩니다.
데모 애플리케이션의 경우 이미지를 저장할 하나의 Blob 컨테이너가 필요합니다.

[Azure Blob 스토리지](/azure/storage/blobs/storage-blobs-introduction)에 대해 자세히 알아보세요.

## <a name="preparing-azure-storage"></a>Azure Storage 준비

Azure 스토리지 서비스를 사용하려면 Azure 스토리지 계정이 필요합니다. 스토리지 계정을 만들려면 [스토리지 계정 만들기](/azure/storage/common/storage-account-create?tabs=azure-portal)를 참조하세요. 스토리지 계정에 대한 자세한 내용은 [Azure 스토리지 계정 개요](/azure/storage/common/storage-account-overview)를 참조하세요.

스토리지 계정이 있으면 **Azure Portal** 에서 이 단원의 다음 섹션에 필요한 연결 문자열을 검색할 수 있습니다.

### <a name="optional-azure-storage-explorer"></a>선택적 Azure Storage Explorer

애플리케이션 내의 UI에서 모든 데이터 변경 내용을 확인할 수 있지만 [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/)를 설치하는 것이 좋습니다. 이 도구를 사용하면 Azure 스토리지의 데이터를 시각적으로 볼 수 있으며 디버그하고 학습할 때 큰 도움이 됩니다.

> [!TIP]
> Unity 편집기 내에서 테스트하는 경우 로컬 에뮬레이터를 사용할 수 있습니다.
>
> * Windows 10에서는 [Azure Storage 에뮬레이터](/azure/storage/common/storage-use-emulator)를 사용할 수 있습니다.
> * MacOS/Linux에서는 Docker용 [Azurite Docker Image](https://hub.docker.com/_/microsoft-azure-storage-azurite)를 사용할 수 있습니다.

## <a name="preparing-the-scene"></a>장면 준비

[계층 구조] 창에서 **DataManager** 개체를 찾아서 선택합니다.

![Inspector(검사기)에 표시된 DataManager 스크립트 구성 요소 구성 필드가 있는 Unity](images/mr-learning-azure/tutorial2-section4-step1-1.png)

[검사기] 창에서 **DataManager(스크립트)** 구성 요소가 모든 **Azure 스토리지** 관련 설정을 유지하는 위치임을 알 수 있습니다. 모든 관련 설정이 이미 설정되어 있으므로 *연결 문자열* 필드를 Azure Portal에서 검색할 수 있는 필드로 바꾸기만 하면 됩니다. 로컬 Azure 스토리지 에뮬레이터 솔루션을 사용하는 경우 이미 제공된 *연결 문자열* 을 유지할 수 있습니다.

**DataManager(스크립트)** 는 UI 구성 요소의 다른 컨트롤러 스크립트에서 사용하는 **Table 스토리지** 및 **Blob 스토리지** 와 통신해야 합니다.

## <a name="writing-and-reading-data-from-azure-table-storage"></a>Azure Table 스토리지에서 데이터 쓰기 및 읽기

모든 준비가 완료되면 이제 *추적된 개체* 를 만듭니다.

HoloLens에서 애플리케이션을 열고 **개체 설정** 을 클릭합니다. 그러면 *EnterObjectName* 개체가 계층 구조에서 활성화되는 방법이 표시됩니다. 이 메뉴에서 *검색 창* 을 클릭하고, *추적된 개체* 에 지정하려는 이름을 입력합니다. 이름이 제공되면 **개체 설정** 단추를 클릭합니다. 그러면 *추적된 개체* 가 Azure Table 스토리지에 만들어지고, 이제 **개체 카드** 가 표시됩니다.

이 **개체 카드** 는 *추적된 개체* 에 대한 UI 표현이며, 이 자습서 시리즈에서 중요한 역할을 여러 번 수행합니다.

이제 설명 *텍스트 상자* 를 클릭하고, "Car"를 입력한 다음, **저장** 단추를 클릭하여 변경 내용을 저장합니다. 애플리케이션을 중지하고 다시 실행합니다.

이제 **개체 검색** 을 클릭하고, *검색 창* 에서 이전에 *추적된 개체* 를 만들 때 사용한 이름을 입력합니다. **Azure Table 스토리지** 에서 모든 데이터가 포함된 **개체 카드** 가 검색됩니다.

자유롭게 **개체 카드** 를 닫고, 새 *추적된 개체* 를 만들고, 해당 데이터를 편집해 보세요.

> [!TIP]
> [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/)를 설치한 경우 *objects* 테이블을 살펴보면 만들어진 *추적된 개체* 가 표시됩니다.

## <a name="uploading-and-download-image-from-azure-blob-storage"></a>Azure Blob 스토리지에서 이미지 업로드 및 다운로드

이 섹션에서는 Azure Blob 스토리지를 사용하여 *추적된 개체* 에 대한 썸네일로 사용될 이미지를 업로드 및 다운로드합니다.

> [!NOTE]
> 이 자습서에서는 애플리케이션에서 사진을 찍어 이미지를 Blob 스토리지에 업로드합니다. Unity 편집기에서 이 작업을 로컬로 실행하는 경우 웹캠이 컴퓨터에 연결되어 있는지 확인하세요.

HoloLens에서 애플리케이션을 열고, **개체 설정** 을 클릭하고, *검색 창* 에서 "Car"라는 이름을 입력합니다. 이제 **개체 카드** 가 표시됩니다. **카메라** 단추를 클릭하면 AirTap을 수행하여 사진을 찍도록 지시하는 메시지가 표시됩니다. 사진을 찍으면 활성 업로드를 알려주는 메시지가 표시되고, 잠시 후 이전에 자리 표시자가 있던 위치에 이미지가 표시됩니다.

이제 애플리케이션을 다시 실행하고 *추적된 개체* 를 검색합니다. 그러면 이전에 업로드한 이미지가 썸네일로 표시됩니다.

## <a name="deleting-image-from-azure-blob-storage"></a>Azure Blob 스토리지에서 이미지 삭제

이전 섹션에서 새 이미지를 Azure Blob 스토리지에 업로드했습니다. 이 섹션에서는 *추적된 개체* 에 대한 썸네일 이미지를 삭제합니다.

HoloLens에서 애플리케이션을 열고, **개체 설정** 을 클릭하고, *검색 창* 에서 "Car"라는 이름을 입력합니다. 이제 썸네일 이미지가 있는 **개체 카드** 가 표시됩니다. 그러면 **삭제** 단추를 클릭합니다. 썸네일 이미지가 자리 표시자 이미지로 바뀌었습니다.

이제 애플리케이션을 다시 실행하고, 이전에 삭제한 썸네일 이미지에 대한 *추적된 개체* 를 검색합니다. 그러면 자리 표시자 이미지만 표시됩니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 **추적된 개체** 의 경우 및 **HoloLens 2** 데모 애플리케이션에 대한 썸네일 이미지 형식의 이진 파일과 같이 Azure 스토리지 서비스를 사용하여 클라우드에서 비정형 데이터를 유지하는 방법을 알아보았습니다.

다음 자습서에서는 Azure Custom Vision을 사용하여 *추적된 개체* 와 연결된 이미지를 감지하는 방법을 알아봅니다.

> [!div class="nextstepaction"]
> [다음 자습서: 3. Azure Custom Vision 통합](mr-learning-azure-03.md)