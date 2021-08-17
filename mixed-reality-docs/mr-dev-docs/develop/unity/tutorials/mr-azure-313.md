---
title: HoloLens(1세대) 및 Azure 313 - IoT Hub 서비스
description: Ubuntu 16.4를 실행하는 가상 머신에서 Azure IoT Hub 서비스를 구현하고 Microsoft HoloLens 또는 VR 헤드셋을 사용하여 메시지 데이터를 시각화하는 방법을 알아봅니다.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure, mixed reality, academy, edge, iot edge, tutorial, api, notification, functions, tables, hololens, immersive, vr, iot, virtual machine, ubuntu, python, Windows 10, Visual Studio
ms.openlocfilehash: fbd793a5941a5fa1b236403672680aa7df375f8d
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905765"
---
# <a name="hololens-1st-gen-and-azure-313-iot-hub-service"></a>HoloLens(1세대) 및 Azure 313: IoT Hub Service

>[!NOTE]
>Mixed Reality 아카데미 자습서는 HoloLens(1세대) 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다.  이러한 자습서는 HoloLens 2에 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 **_않습니다_**.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2 위해 개발하는 방법을 보여 주는 새로운 자습서 시리즈가 나중에 게시될 예정입니다.  이 알림은 해당 자습서가 게시될 때 해당 자습서에 대한 링크로 업데이트됩니다.

![과정 결과](images/AzureLabs-Lab313-00.png)

이 과정에서는 Ubuntu 16.4 운영 체제를 실행하는 가상 머신에서 **Azure IoT Hub 서비스를** 구현하는 방법을 알아봅니다. 그런 **다음, Azure 함수 앱을** 사용하여 Ubuntu VM에서 메시지를 수신하고 **결과를 Azure Table Service** 내에 저장합니다. 그런 **다음, Microsoft HoloLens** 또는 몰입형(VR) 헤드셋에서 Power BI 사용하여 이 데이터를 볼 수 있습니다.

이 과정의 내용은 IoT Edge 디바이스에 *적용할 수* 있지만, 이 과정에서는 실제 Edge 디바이스에 액세스할 필요가 없도록 가상 머신 환경에 집중합니다.

이 과정을 완료하면 다음을 배울 수 있습니다.

- IoT 디바이스를 나타내는 Virtual Machine(Ubuntu 16 OS)에 **IoT Edge 모듈을** 배포합니다.
- 컨테이너에 저장된 이미지를 분석하는 코드를 사용하여 **Azure Custom Vision Tensorflow 모델을** Edge 모듈에 추가합니다.
- 분석 결과 메시지를 **IoT Hub 서비스** 로 다시 보내도록 모듈을 설정합니다.
- Azure **함수 앱을** 사용하여 Azure 테이블 내에 메시지를 **저장합니다.**
- 저장된 메시지를 수집하고 보고서를 만들도록 **Power BI** 설정합니다.
- **Power BI** 내에서 IoT 메시지 데이터를 시각화합니다.

사용할 서비스는 다음과 같습니다.

- **Azure IoT Hub는** 개발자가 IoT 자산을 연결, 모니터링 및 관리할 수 있는 Microsoft Azure 서비스입니다. 자세한 내용은 Azure IoT [ **Hub 서비스** 페이지 를 방문하세요.](https://azure.microsoft.com/services/iot-hub/)

- **Azure Container Registry** 개발자가 다양한 유형의 컨테이너에 대한 컨테이너 이미지를 저장할 수 있는 Microsoft Azure 서비스입니다. 자세한 내용은 Azure Container Registry [ **서비스** 페이지를 방문하세요.](https://azure.microsoft.com/services/container-registry/)

- **Azure 함수 앱은** 개발자가 Azure에서 작은 코드 'functions'를 실행할 수 있는 Microsoft Azure 서비스입니다. 이렇게 하면 많은 이점이 있을 수 있는 로컬 애플리케이션이 아닌 클라우드에 작업을 위임할 수 있습니다. **Azure Functions** \# C, F, \# Node.js, Java 및 PHP를 비롯한 여러 개발 언어를 지원합니다. 자세한 내용은 [ **Azure Functions** 페이지를 방문하세요.](/azure/azure-functions/functions-overview)

- **Azure Storage: 테이블은** 개발자가 구조화되고 SQL 아닌 데이터를 클라우드에 저장하여 어디서나 쉽게 액세스할 수 있도록 하는 Microsoft Azure 서비스입니다. 서비스는 스키마 없는 디자인을 통해 필요에 따라 테이블의 진화를 허용하므로 매우 유연합니다. 자세한 내용은 Azure [ **테이블** 페이지를 방문하세요.](/azure/cosmos-db/table-storage-overview)

이 과정에서는 IoT Hub 서비스를 설정 및 사용하는 방법을 학습한 다음, 디바이스에서 제공하는 응답을 시각화합니다. 빌드 중인 사용자 지정 IoT Hub 서비스 설정에 이러한 개념을 적용할 수 있습니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> MR 및 Azure 313: IoT Hub 서비스</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>필수 구성 요소

Microsoft HoloLens 포함하여 Mixed Reality 사용하여 개발하기 위한 최신 필수 구성 요소에 대해서는 [도구 설치](../../install-the-tools.md) 문서를 방문하세요.

> [!NOTE]
> 이 자습서는 Python에 대한 기본적인 경험이 있는 개발자를 위해 설계되었습니다. 또한 이 문서 내의 필수 조건 및 작성된 지침은 작성 당시 테스트 및 확인된 내용을 나타냅니다(2018년 7월). [도구 설치](../../install-the-tools.md) 문서에 나열된 대로 최신 소프트웨어를 자유롭게 사용할 수 있지만, 이 과정의 정보가 아래 나열된 것보다 최신 소프트웨어에서 찾을 수 있는 정보와 완벽하게 일치한다고 가정해서는 안 됩니다.

다음 하드웨어 및 소프트웨어가 필요합니다.

- Windows 10 Fall Creators Update 이상, **개발자 모드 사용**

    > [!WARNING]
    > Windows 10 Home 버전에서는 Hyper-V를 사용하여 Virtual Machine을 실행할 수 없습니다.

- Windows 10 SDK(최신 버전)
- HoloLens, 개발자 **모드 사용**
- Visual Studio 2017.15.4(Azure 클라우드 탐색기 액세스하는 데만 사용)
- Azure 및 IoT Hub Service에 대한 인터넷 액세스. 자세한 내용은 [IoT Hub 서비스 페이지에 대한 링크를](https://azure.microsoft.com/services/iot-hub/) 따르세요.
- Machine Learning 모델 모델을 사용할 준비가 되지 않은 경우 [이 과정과 함께 제공되는 모델을 사용할 수 있습니다.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)
- Windows 10 개발 머신에서 **Hyper-V** 소프트웨어가 사용하도록 설정됩니다.
- 개발 머신에서 실행되는 Ubuntu(16.4 또는 18.4)를 실행하는 Virtual Machine 또는 Linux(Ubuntu 16.4 또는 18.4)를 실행하는 별도의 컴퓨터를 사용할 수 있습니다. Hyper-V를 사용하여 Windows VM을 만드는 방법에 대한 자세한 내용은 ["시작하기 전에" 챕터에서](#before-you-start)확인할 수 있습니다. (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>시작하기 전에

1. HoloLens 설정하고 테스트합니다. HoloLens 설정을 지원해야 하는 경우 [HoloLens 설정 문서 를 방문하세요.](/hololens/hololens-setup)
2. 새 HoloLens 앱 개발을 시작할 때 **보정** 및 **센서 튜닝을** 수행하는 것이 좋습니다(때로는 각 사용자에 대해 이러한 작업을 수행하는 데 도움이 될 수 있습니다).

보정에 대한 도움말은 [HoloLens 보정 문서에 대한 이 링크를](/hololens/hololens-calibration#hololens-2)따르세요.

센서 튜닝에 대한 도움말은 [HoloLens 센서 튜닝 문서 링크를](/hololens/hololens-updates)따르세요.

3. **Hyper-V를** 사용하여 **Ubuntu Virtual Machine을** 설정합니다. 다음 리소스는 프로세스에 도움이 됩니다.
    1.  먼저 이 링크를 따라 [Ubuntu 16.04.4 LTS(Xenial Xerus) ISO](https://au.releases.ubuntu.com/16.04/)를 다운로드합니다. **64비트 PC(AMD64) 데스크톱 이미지** 를 선택합니다.
    2.  Windows 10 컴퓨터에서 **Hyper-V가** 사용하도록 설정되어 있는지 확인합니다. [Windows 10 Hyper-V를 설치하고 사용하도록 설정하는 지침은](/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)이 링크를 따를 수 있습니다.
    3.  Hyper-V를 시작하고 새 Ubuntu VM을 만듭니다. [Hyper-V를 사용하여 VM을 만드는 방법에 대한 단계별 가이드는](/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)이 링크를 따를 수 있습니다. **"부팅 가능한 이미지 파일에서 운영 체제 설치"를** 요청하면 이전에 다운로드한 **Ubuntu ISO를** 선택합니다.

    > [!NOTE]
    > **Hyper-V 빠른 생성은** 권장되지 않습니다.  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>1장 - Custom Vision 모델 검색

이 과정을 통해 이미지에서 키보드 및 마우스를 감지하는 [미리 빌드된 Custom Vision 모델에](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) 액세스할 수 있습니다. 이를 사용하는 경우 [2장 으로](#chapter-2---the-container-registry-service)진행합니다.

그러나 고유한 Custom Vision 모델을 사용하려는 경우 다음 단계를 수행할 수 있습니다.

1. **Custom Vision Project** **성능** 탭으로 이동합니다.

    > [!WARNING]
    > 모델을 내보내려면 모델이 *압축* 도메인을 사용해야 합니다. 프로젝트의 설정에서 모델 도메인을 변경할 수 있습니다.

    ![성능 탭](images/AzureLabs-Lab313-01.png)

2. 내보내려는 **반복을** 선택하고 **내보내기를** 클릭합니다. 블레이드가 표시됩니다.

    ![내보내기 블레이드](images/AzureLabs-Lab313-02.png)

3. 블레이드에서 **Docker 파일** 을 클릭합니다.

    ![docker 선택](images/AzureLabs-Lab313-03.png)

4. 드롭다운 메뉴에서 **Linux를** 클릭한 다음 **다운로드를** 클릭합니다.

    ![다운로드를 클릭합니다.](images/AzureLabs-Lab313-04.png)

5. 콘텐츠의 압축을 해제합니다. 이 과정은 이 과정의 후반부에서 사용합니다.

## <a name="chapter-2---the-container-registry-service"></a>2장 - Container Registry 서비스

**Container Registry Service는** 컨테이너를 호스트하는 데 사용되는 리포지토리입니다.

이 과정에서 빌드하고 사용할 **IoT Hub 서비스는** **Container Registry Service를** 참조하여 Edge 디바이스에 배포할 컨테이너를 얻습니다.

1. 먼저 이 [링크를](https://portal.azure.com/)따라 Azure Portal 에 연결하고 자격 증명으로 로그인합니다.

2. 리소스 **만들기로** 이동하여 **Container Registry** 찾습니다.

    ![컨테이너 레지스트리](images/AzureLabs-Lab313-05.png)

3. **만들기** 를 클릭합니다.

    ![](images/AzureLabs-Lab313-06.png)

4. 서비스 설정 매개 변수를 설정합니다.

    1. 프로젝트의 이름을 삽입합니다. 이 예제에서는 **IoTCRegistry라고** 합니다.

    2. 리소스 **그룹을** 선택하거나 새 리소스 그룹을 만듭니다. 리소스 그룹은 Azure 자산 컬렉션에 대한 액세스를 모니터링, 제어, 프로비전 및 관리, 청구하는 방법을 제공합니다. 모든 Azure 서비스를 단일 프로젝트(예: 이러한 과정)와 연결된 공용 리소스 그룹에 유지하는 것이 좋습니다.

    3. 서비스의 위치를 설정합니다.

    4. **관리 사용자를** **사용으로** 설정합니다.

    5. **SKU를** **기본** 로 설정합니다. 

    ![](images/AzureLabs-Lab313-07.png)

5. **만들기를** 클릭하고 서비스가 만들어질 때까지 기다립니다. 

6. *Container Registry* 성공적으로 생성했다는 알림이 표시되면 **리소스로 이동을** 클릭하여 서비스 페이지로 리디렉션합니다.

    ![](images/AzureLabs-Lab313-08.png)

7. *Container Registry* 서비스 페이지에서 **액세스 키** 를 클릭합니다.

8. 다음 매개 변수의 메모장 사용할 수 있습니다.
    1. **로그인 서버**
    2. **사용자 이름**
    3. **암호**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>3장 - IoT Hub 서비스

이제 **IoT Hub 서비스의** 만들기 및 설정을 시작합니다.

1. 아직 로그인하지 않은 경우 Azure Portal 에 [로그인합니다.](https://portal.azure.com)

2.  로그인한 후 왼쪽 위 모서리에서 **리소스 만들기를** 클릭하고 **IoT Hub** 검색한 다음 **Enter 키를** 클릭합니다.

 ![스토리지 계정 검색](images/AzureLabs-Lab313-10.png)

3.  새 페이지에서는 **Storage 계정** 서비스에 대한 설명을 제공합니다. 이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 클릭하여 이 서비스의 인스턴스를 만듭니다.

    ![스토리지 인스턴스 만들기](images/AzureLabs-Lab313-11.png)

4.  **만들기를** 클릭하면 패널이 표시됩니다.

    1. 리소스 **그룹을** 선택하거나 새 리소스 그룹을 만듭니다. 리소스 그룹은 Azure 자산 컬렉션에 대한 액세스를 모니터링, 제어, 프로비전 및 관리하는 방법을 제공합니다. 모든 Azure 서비스를 단일 프로젝트(예: 이러한 과정)와 연결된 공용 리소스 그룹에 유지하는 것이 좋습니다.

        > Azure 리소스 그룹에 대해 자세히 알아보려면 리소스 그룹을 [관리하는 방법에 대한](/azure/azure-resource-manager/resource-group-portal)이 링크를 따르세요.


    2. 적절한 **위치를** 선택합니다(이 과정에서 만든 모든 서비스에서 동일한 위치 사용).

    3. 이 서비스 인스턴스에 대해 원하는 **이름을** 삽입합니다.    

5.  페이지 아래쪽에서 **다음: 크기 조정 및 크기 조정을** 클릭합니다.

    ![스토리지 인스턴스 만들기](images/AzureLabs-Lab313-12.png)

6.  이 페이지에서 가격 **책정 및 크기 조정 계층을** 선택합니다(첫 번째 IoT Hub 서비스 인스턴스인 경우 무료 계층을 사용할 수 있어야 합니다).  

7.  검토 **+ 만들기를** 클릭합니다.

    ![스토리지 인스턴스 만들기](images/AzureLabs-Lab313-13.png)

8.  설정을 검토하고 **만들기를** 클릭합니다.

    ![스토리지 인스턴스 만들기](images/AzureLabs-Lab313-14.png)

9. *IoT Hub* 서비스를 성공적으로 생성했다는 알림이 표시되면 **리소스로 이동을** 클릭하여 서비스 페이지로 리디렉션합니다.

    ![스토리지 인스턴스 만들기](images/AzureLabs-Lab313-15.png)

10. *자동 장치 관리* 가 표시될 때까지 왼쪽의 측면 패널을 스크롤하고 **IoT Edge** 클릭합니다.

    ![스토리지 인스턴스 만들기](images/AzureLabs-Lab313-16.png)

11. 오른쪽에 표시되는 창에서 디바이스 추가 **IoT Edge** 클릭합니다. 오른쪽에 블레이드가 표시됩니다.

12. 블레이드에서 새 디바이스에 **디바이스 ID(선택한** 이름)를 제공합니다. 그런 다음 **저장** 을 클릭합니다. 자동 생성이 선택되어 있으면 *기본* 및 *보조 키가* 자동으로 **생성됩니다.**

    ![스토리지 인스턴스 만들기](images/AzureLabs-Lab313-17.png)

13. 새 디바이스가 나열되는 *IoT Edge 디바이스* 섹션으로 다시 이동합니다. 새 디바이스를 클릭합니다(아래 이미지에 빨간색으로 윤곽선이 표시되어 있습니다). 

    ![스토리지 인스턴스 만들기](images/AzureLabs-Lab313-18.png)

14. 표시되는 *디바이스 세부 정보* 페이지에서 **연결 문자열(기본** 키)의 복사본을 가져옵니다.

    ![스토리지 인스턴스 만들기](images/AzureLabs-Lab313-19.png)

15. 왼쪽 패널에 돌아가기 *공유 액세스 정책* 를 클릭하여 엽니다. 

16. 표시되는 페이지에서 **iothubowner** 를 클릭하면 화면 오른쪽에 블레이드가 표시됩니다. 

17. 나중에 **연결 문자열을** 디바이스로 설정하는 경우 사용할 수 있도록 연결 문자열(기본 키)의 (메모장)을  기록해 둡다.

    ![스토리지 인스턴스 만들기](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>4장 - 개발 환경 설정

*IoT Hub Edge용* 모듈을 만들고 배포하려면 Windows 10 실행하는 개발 머신에 다음 구성 요소가 설치되어 있어야 합니다.

1.  [Windows Docker는](https://store.docker.com/editions/community/docker-ce-desktop-windows)다운로드할 수 있는 계정을 만들라는 메시지가 표시됩니다. 

    [![Windows용 Docker 다운로드](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker를 실행하려면 *Windows 10 PRO,* *Enterprise 14393* 또는 *Windows Server 2016 RTM이* 필요합니다. 다른 버전의 Windows 10 실행하는 경우 Docker 도구 상자 를 사용하여 [Docker를](https://docs.docker.com/toolbox/toolbox_install_windows/)설치해 볼 수 있습니다.

2.  [Python 3.6](https://www.python.org/downloads/).

    [![python 3.6 다운로드](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code(VS Code이라고도 함)](https://code.visualstudio.com/download)입니다.

    [![다운로드 VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

위에서 언급한 소프트웨어를 설치한 후 컴퓨터를 다시 시작해야 합니다.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>5장 - Ubuntu 환경 설정

이제 **Ubuntu OS** 를 실행하는 디바이스 설정으로 이동할 수 있습니다. 다음 단계에 따라 필요한 소프트웨어를 설치하고 보드에 컨테이너를 배포합니다.

> [!IMPORTANT]
> 관리 사용자로 실행하려면 항상 **sudo를** 사용하여 터미널 명령 앞에 와야 합니다. 즉:
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  **Ubuntu 터미널 을** 열고 다음 명령을 사용하여 **pip** 를 설치합니다.

    > [! 힌트] 바로 가기 키를 사용하여 *터미널을* 매우 쉽게 열 수 있습니다. **Ctrl + Alt + T**.

    ```bash
        sudo apt-get install python-pip
    ```

2.  이 챕터 전체에서 *터미널* 에서 디바이스 스토리지를 사용할 수 있는 권한을 묻는 메시지가 표시될 수 있으며, **y/n(예** 또는 아니요)을 입력하고 **'y'를** 입력한 다음 **Enter** 키를 눌러 수락합니다.

3.  해당 명령이 완료되면 다음 명령을 사용하여 **curl을** 설치합니다.

    ```bash
        sudo apt install curl
    ```

4.  **pip** 및 **curl이** 설치되면 다음 명령을 사용하여 **IoT Edge 런타임** 을 설치합니다. 이는 보드에서 모듈을 배포하고 제어하는 데 필요합니다.

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. 이때 IoT Hub 서비스(14단계,[3장](#chapter-3---the-iot-hub-service))를 만들 때 적어 두는 디바이스 **연결 문자열** 를 삽입하기 위해 *런타임 구성 파일* 를 열라는 메시지가 **표시됩니다(메모장).** 터미널에서 다음 줄을 실행하여 해당 파일을 엽니다.

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. 편집할 준비가 된 **config.yaml** 파일이 표시됩니다.

    > [!WARNING]
    > 이 파일이 열리면 다소 혼동될 수 있습니다. *터미널* 자체 내에서 이 파일을 편집하는 텍스트가 됩니다. 

    1.  키보드의 화살표 키를 사용하여 아래로 스크롤하여(약간 아래로 스크롤해야 함) 포함하는 줄에 도달합니다.

        "**\<ADD DEVICE CONNECTION STRING HERE>**".

    2. **대괄호를 포함한** 선을 이전에 기록한 **디바이스 연결 문자열로** 대체합니다.

7. 연결 문자열이 있는 경우 키보드에서 **Ctrl-X** 키를 눌러 파일을 저장합니다. **Y** 를 입력하여 확인하라는 메시지가 표시됩니다. 그런 다음 Enter **키를** 눌러 확인합니다. 일반 *터미널* 로 돌아갑니다. 

8. 이러한 명령이 모두 성공적으로 실행되면 **IoT Edge 런타임** 을 설치합니다. 초기화되면 디바이스 전원이 켜질 때마다 런타임이 자체적으로 시작되고 백그라운드에 배치되어 **IoT Hub 서비스에서** 모듈이 배포될 때까지 대기합니다.

9.  다음 명령줄을 실행하여 *IoT Edge 런타임을* 초기화합니다.

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > .yaml 파일 또는 위의 설정을 변경하는 경우 *터미널* 내에서 위의 다시 시작 줄을 다시 실행해야 합니다.

10. 다음 명령줄을 실행하여 *IoT Edge 런타임* 상태를 확인합니다. 런타임은 활성 **상태(실행 중)와** 함께 녹색 텍스트로 표시됩니다.

    ```bash
        sudo systemctl status iotedge
    ```

11. **Ctrl+C** 키를 눌러 상태 페이지를 종료합니다. 다음 명령을 입력하여 *IoT Edge 런타임이* 컨테이너를 올바르게 끌어와고 있는지 확인할 수 있습니다.

    ```bash
        sudo docker ps
    ```

12. 컨테이너가 2개인 목록이 표시됩니다. 이러한 모듈은 IoT Hub 서비스(edgeAgent 및 edgeHub)에서 자동으로 생성되는 기본 모듈입니다. 사용자 고유의 모듈을 만들고 배포하면 기본 모듈 아래에 이 목록에 표시됩니다.

## <a name="chapter-6---install-the-extensions"></a>6장 - 확장 설치

> [!IMPORTANT]
> 다음 몇 장 (6-9)이 Windows 10 컴퓨터에서 수행 됩니다.

1. **VS Code** 를 엽니다.

2. VS Code 왼쪽 막대에서 **확장** (정사각형) 단추를 클릭 하 여 **확장 패널** 을 엽니다.

3. 아래 이미지에 표시 된 것 처럼 다음 확장을 검색 하 고 설치 합니다.

    1. Azure IoT Edge
    2. Azure IoT Toolkit
    3. Docker   

    ![컨테이너 만들기](images/AzureLabs-Lab313-24.png)

4. 확장이 설치 되 면 VS Code를 닫았다가 다시 엽니다.

5. VS Code를 한 번 더 열면   >  **통합 터미널** 보기로 이동 합니다.

6. 이제 **Cookiecutter** 를 설치 합니다. 터미널에서 다음 bash 명령을 실행 합니다.

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! 힌트] 명령을 사용 하는 데 문제가 있는 경우: 
    >1. VS Code 및/또는 컴퓨터를 다시 시작 합니다.
    >2. python을 설치 하는 데 사용 하는 것으로 **VS Code 터미널** 을 전환 해야 할 수도 **있습니다. 즉** , 특히 python 환경이 컴퓨터에 이미 설치 되어 있는 경우에 한 합니다. 터미널이 열리면 터미널의 오른쪽에 있는 드롭다운 메뉴를 찾을 수 있습니다.
     ![컨테이너 만들기](images/AzureLabs-Lab313-24b.png) 
    >3. **Python** 설치 경로가 컴퓨터에 **환경 변수로** 추가 되었는지 확인 합니다. Cookiecutter는 동일한 위치 경로의 일부 여야 합니다. [환경 변수에 대 한 자세한 내용은 다음 링크](/windows/win32/procthread/environment-variables)를 참조 하세요. 

7. **Cookiecutter** 설치가 완료 되 면 시스템 환경 내에서 **Cookiecutter** 가 명령으로 인식 되도록 컴퓨터를 다시 시작 해야 합니다.

## <a name="chapter-7---create-your-container-solution"></a>7 장-컨테이너 솔루션 만들기

이 시점에서 모듈을 사용 하 여 *Container Registry* 에 푸시할 컨테이너를 만들어야 합니다. 컨테이너를 푸시한 후에는 *IoT Hub Edge* 서비스를 사용 하 여 *IoT Edge 런타임을* 실행 하는 장치에 배포 합니다.

1. VS Code에서 **보기**  >  **명령 팔레트** 를 클릭 합니다.

2. 색상표에서 **Edge: 새 IoT Edge 솔루션** 을 검색 하 고 실행 Azure IoT 합니다.

3. 솔루션을 만들려는 위치로 이동 합니다. **Enter** 키를 눌러 위치를 적용 합니다.

4. 솔루션에 이름을 지정 합니다. **Enter** 키를 눌러 제공 된 이름을 확인 합니다.

5. 이제 솔루션에 대 한 템플릿 프레임 워크를 선택 하 라는 메시지가 표시 됩니다. **Python 모듈** 을 클릭 합니다. **Enter** 키를 눌러이 선택을 확인 합니다.

6. 모듈에 이름을 지정 합니다. **Enter** 키를 눌러 모듈의 이름을 확인 합니다. 나중에 사용 되므로 모듈 이름에 대 한 메모를 작성 해야 합니다 (메모장).

7. 미리 빌드된 *Docker 이미지 리포지토리* 주소가 색상표에 표시 됩니다. 다음과 같이 표시 됩니다.

    **localhost: 5000/-모듈의 이름-**. 

8. **Localhost: 5000** 을 삭제 하 고 해당 위치에서 **Container Registry 서비스** 를 만들 때 기록한 *Container Registry* **로그인 서버** 주소 ([2 장의 8 단계](#chapter-2---the-container-registry-service))를 삽입 합니다. **Enter** 키를 눌러 주소를 확인 합니다.

9. 이 시점에서 Python 모듈에 대 한 템플릿이 포함 된 솔루션이 만들어지고 해당 구조가 화면 왼쪽에 있는 VS Code의 **탐색 탭** 에 표시 됩니다. **탐색 탭** 이 열려 있지 않으면 왼쪽 표시줄에서 맨 위에 있는 단추를 클릭 하 여 열 수 있습니다.

    ![컨테이너 만들기](images/AzureLabs-Lab313-25.png)

10. 이 챕터의 마지막 단계에서는 **탐색 탭** 내에서 **env 파일** 을 클릭 하 여 열고 *Container Registry* **사용자 이름** 및 **암호** 를 추가 합니다. 이 파일은 git에서 무시 되지만 컨테이너를 빌드하는 동안 **Container Registry 서비스** 에 액세스 하기 위한 자격 증명을 설정 합니다.

    ![컨테이너 만들기](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>8 장-컨테이너 솔루션 편집

이제 다음 파일을 업데이트 하 여 컨테이너 솔루션을 완료 합니다.

- *<span></span> py* python 스크립트입니다.
- *requirements.txt*.
- *deployment.template.js* 합니다.
- *Dockerfile. amd64*

그런 다음 python 스크립트에서 *Custom Vision 모델* 에 대해 일치 시킬 이미지를 확인 하는 데 사용 하는 *images* 폴더를 만듭니다. 마지막으로, 모델을 읽는 데 도움이 되는 *labels.txt* 파일을 추가 하 고 모델인 모델 *pb* 파일을 추가 합니다.

1. VS Code 열린 상태에서 모듈 폴더로 이동 하 고 **<span></span> py** 라는 스크립트를 찾습니다. 이 로그를 두 번 클릭하여 엽니다.

2. 파일의 내용을 삭제 하 고 다음 코드를 삽입 합니다.

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  **requirements.txt** 파일을 열고 해당 콘텐츠를 다음으로 바꿉니다.

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  **에서deployment.template.js** 이라고 하는 파일을 열고 아래 지침에 따라 해당 콘텐츠를 대체 합니다.

    1. 고유 하 고 고유한 JSON 구조가 있으므로 예제를 복사 하는 대신 직접 편집 해야 합니다. 이 작업을 쉽게 하려면 아래 이미지를 가이드로 사용 합니다.
    2. 사용자와 다르게 보이지만 **변경 하지 않아야** 하는 영역이 노란색으로 강조 표시 됩니다.
    3. **삭제 해야 하는 섹션은 빨간색으로 강조 표시 됩니다.**
    4. 올바른 대괄호를 삭제 하 고 쉼표도 제거 해야 합니다.

        ![컨테이너 만들기](images/AzureLabs-Lab313-27.png)

    5. 완성 된 JSON은 다음 이미지와 같이 표시 되어야 합니다. 단, *사용자 이름/암호/모듈 이름/모듈 참조* 와 같은 고유한 차이점이 있습니다.

        ![컨테이너 만들기](images/AzureLabs-Lab313-28.png)

5.  **Dockerfile. amd64** 라는 파일을 열고 콘텐츠를 다음으로 바꿉니다.

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  **모듈** 아래에 있는 폴더를 마우스 오른쪽 단추로 클릭 하 고 (이전에 입력 한 이름을 포함 합니다. 아래 예제에서는 *pythonmodule* 라고 함) **새 폴더** 를 클릭 합니다. 폴더 이름을 **images** 로 합니다.

7.  폴더 안에 마우스나 키보드를 포함 하는 일부 이미지를 추가 합니다. 이러한 이미지는 Tensorflow 모델에서 분석할 이미지가 됩니다.

    > [!WARNING]
    > 사용자 고유의 모델을 사용 하는 경우 고유한 모델 데이터를 반영 하도록이를 변경 해야 합니다.

8.  이제 [1 장](#chapter-1---retrieve-the-custom-vision-model)에서 이전에 다운로드 했거나 사용자 고유의 **Custom Vision Service** 에서 만든 모델 폴더에서 **labels.txt** 및 **모델 pb** 파일을 검색 해야 합니다. 파일이 있으면 다른 파일과 함께 솔루션 내에 추가 합니다. 최종 결과는 아래 이미지와 같아야 합니다.

    ![컨테이너 만들기](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>9 장-솔루션을 컨테이너로 패키지

1.  이제 파일을 컨테이너로 "패키지" 하 고 **Azure Container Registry** 에 푸시할 수 있습니다. VS Code 내에서 *통합 터미널* (**View**  >  **integrated terminal** 또는 **Ctrl**)을 열고 + **\`** 다음 줄을 사용 하 여 **Docker** 에 로그인 합니다 (명령 값을 **ACR (Azure Container Registry** 의 자격 증명으로 대체).

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. **deployment.template.js** 파일을 마우스 오른쪽 단추로 클릭 하 고 **IoT Edge 솔루션 빌드** 를 클릭 합니다. 이 빌드 프로세스는 장치에 따라 상당한 시간이 걸리므로 대기할 준비가 됩니다. 빌드 프로세스가 완료 된 후에 파일 **에 대 한deployment.js** 는 **config** 라는 새 폴더 내에 생성 됩니다.

    ![배포 만들기](images/AzureLabs-Lab313-30.png)

3. **명령 팔레트** 를 다시 열고 **Azure: 로그인** 을 검색 합니다. Azure 계정 자격 증명을 사용 하 여 프롬프트를 따릅니다. VS Code은 복사 하 여 *열* 수 있는 옵션을 제공 합니다 .이 옵션을 사용 하면 곧 필요한 장치 코드를 복사 하 여 기본 웹 브라우저를 열 수 있습니다. 메시지가 표시 되 면 장치 코드를 붙여넣어 컴퓨터를 인증 합니다.

    ![복사 및 열기](images/AzureLabs-Lab313-31.png)

4. 로그인 하면 *탐색* 패널의 아래쪽에 **Azure IoT 허브 장치** 라는 새 섹션이 표시 됩니다. 이 섹션을 클릭 하 여 확장 합니다.

    ![edge 장치](images/AzureLabs-Lab313-32.png)

5. 장치를 사용할 수 없는 경우 *Azure IoT 허브 장치* 를 마우스 오른쪽 단추로 클릭 한 다음 **IoT Hub 연결 문자열 설정** 을 클릭 해야 합니다. 그러면 **명령 팔레트** (VS Code 위쪽)에 *연결 문자열* 을 입력 하 라는 메시지가 표시 됩니다. [3 장](#chapter-3---the-iot-hub-service)끝에 적어 둔 *연결 문자열* 입니다. 에서 문자열을 복사한 후 **enter** 키를 누릅니다.    

6. 장치가 로드 되 고 표시 됩니다. 장치 이름을 마우스 오른쪽 단추로 클릭 한 다음 **단일 장치에 대 한 배포 만들기** 를 클릭 합니다.

    ![배포 만들기](images/AzureLabs-Lab313-33b.png)

7. *파일 탐색기* 프롬프트가 표시 됩니다. 여기서 **config** 폴더로 이동한 다음 파일 **에서deployment.js** 를 선택할 수 있습니다. 해당 파일을 선택한 상태에서 **Edge 배포 매니페스트 선택** 단추를 클릭 합니다.

    ![배포 만들기](images/AzureLabs-Lab313-34.png)

8. 이제 **Azure Container Registry** 에서 컨테이너를 모듈로 배포 하 여 장치에 효과적으로 배포 하는 데 필요한 매니페스트와 함께 **IoT Hub 서비스** 를 제공 했습니다.

9. 장치에서 IoT Hub 전송 된 메시지를 보려면 **탐색기** 패널의 **Azure IoT 허브 장치** 섹션에서 장치 이름을 다시 마우스 오른쪽 단추로 클릭 하 고 **D2C 메시지 모니터링 시작** 을 클릭 합니다. 장치에서 전송 된 메시지는 VS 터미널에 표시 되어야 합니다. 다소 시간이 걸릴 수 있으므로 잠시 기다려 주십시오. 다음 챕터에서 디버깅을 참조 하 고 배포에 성공 했는지 확인 합니다.

이 모듈은 이제 각 반복에서 **이미지** 폴더의 이미지를 반복 하 고 분석 합니다. 이는 IoT Edge 장치 환경에서 기본적인 기계 학습 모델을 사용 하는 방법을 보여 주는 것입니다. 

이 예제의 기능을 확장 하기 위해 여러 가지 방법으로 진행할 수 있습니다. 한 가지 방법은 컨테이너에 일부 코드를 포함 하 여 장치에 연결 된 웹캠에서 사진을 캡처하고 이미지 폴더에 이미지를 저장 하는 것입니다. 

또 다른 방법은 IoT 장치에서 컨테이너로 이미지를 복사 하는 것입니다. 이 작업을 수행 하는 실용적인 방법은 IoT 장치 터미널에서 다음 명령을 실행 하는 것입니다. 프로세스를 자동화 하려는 경우 작은 앱이 작업을 수행할 수 있습니다. 파일이 저장 되는 폴더 위치에서 수동으로 실행 하 여이 명령을 테스트할 수 있습니다.

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>10 장-IoT Edge 런타임 디버깅

다음은 **Ubuntu 장치** 에서 *IoT Edge 런타임의* 메시징 활동을 모니터링 하 고 디버깅 하는 데 도움이 되는 명령줄 목록과 팁입니다. 

- 다음 명령줄을 실행 하 여 *IoT Edge 런타임* 상태를 확인 합니다.

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > 상태 보기를 마치려면 **ctrl + C** 를 눌러야 합니다.

- 현재 배포 된 컨테이너를 나열 합니다. *IoT Hub 서비스가* 성공적으로 컨테이너를 배포 하면 다음 명령줄을 실행 하 여 표시 됩니다.

    ```bash
        sudo iotedge list
    ```

    또는

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > 위의 내용은 목록에 표시 되는 대로 모듈이 성공적으로 배포 되었는지 여부를 확인 하는 좋은 방법입니다. 그렇지 않으면 *edgeHub* 및 *edgeAgent* **만** 표시 됩니다.

- 컨테이너의 코드 로그를 표시 하려면 다음 명령줄을 실행 합니다.

    ```bash
        journalctl -u iotedge
    ```

**IoT Edge 런타임을 관리 하는 데 유용한 명령:**

-  호스트의 모든 컨테이너를 삭제 하려면 다음을 수행 합니다.

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  *IoT Edge 런타임을* 중지 하려면:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>11 장-테이블 서비스 만들기 

azure Portal로 다시 이동 합니다. 여기서는 Storage 리소스를 만들어 azure Tables 서비스를 만듭니다.

1. 아직 로그인 하지 않은 경우 [Azure Portal](https://portal.azure.com)에 로그인 합니다.

2. 로그인 되 면 왼쪽 위 모서리에서 **리소스 만들기** 를 클릭 하 고 **Storage 계정을** 검색 한 다음 **enter** 키를 눌러 검색을 시작 합니다.

3. 표시 되 면 목록에서 **Storage 계정-blob, 파일, 테이블, 큐** 를 클릭 합니다.

    ![저장소 계정 검색](images/AzureLabs-Lab313-35.png)

4. 새 페이지에 **Storage 계정** 서비스에 대 한 설명이 제공 됩니다. 이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 클릭 하 여이 서비스의 인스턴스를 만듭니다.

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-36.png)

5. **만들기** 를 클릭 하면 패널이 표시 됩니다.

    1. 이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다 (*모두 소문자 여야 함*).

    2. **배포 모델** 에서 **리소스 관리자** 를 클릭 합니다.

    3. **계정 종류** 의 경우 드롭다운 메뉴를 사용 하 여 **Storage (범용 v1)** 를 클릭 합니다.

    4. 적절 한 **위치** 를 클릭 합니다.
    
    5. **복제** 드롭다운 메뉴에서 **읽기 액세스-지역 중복 저장소 (RA-GRS)** 를 클릭 합니다.

    6. **성능** 으로 **표준** 을 클릭 합니다.

    7. **보안 전송 필요** 섹션에서 **사용 안 함** 을 클릭 합니다.

    8. **구독** 드롭다운 메뉴에서 적절 한 구독을 클릭 합니다.

    9. 리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다. 리소스 그룹은 Azure 자산 컬렉션에 대 한 모니터링, 제어 액세스, 프로 비전 및 관리를 위한 방법을 제공 합니다. 단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.

        > Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹을 관리 하는 방법에 대](/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요.

    10. 이 옵션을 선택 하는 경우 **가상 네트워크** 를 **사용 안 함** 으로 유지 합니다.

    11. **만들기** 를 클릭합니다.

        ![저장소 정보 입력](images/AzureLabs-Lab313-37.png)

6. **만들기** 를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.

7. 서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다. 알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.

    ![새 저장소 알림](images/AzureLabs-Lab313-38.png)

8. 알림에서 **리소스로 이동** 단추를 클릭 하면 새 Storage 서비스 인스턴스 개요 페이지가 표시 됩니다.

    ![리소스로 이동](images/AzureLabs-Lab313-39.png)

9. 개요 페이지에서 오른쪽에 있는 **테이블** 을 클릭 합니다.
    
    ![테이블](images/AzureLabs-Lab313-40.png)

10. 오른쪽 패널은 새 테이블을 추가 해야 하는 **테이블 서비스** 정보를 표시 하도록 변경 됩니다. 왼쪽 위 모서리에서 **+ 테이블** 단추를 클릭 하 여이 작업을 수행 합니다.

    ![테이블 열기](images/AzureLabs-Lab313-41.png)

11. **테이블 이름을** 입력 해야 하는 새 페이지가 표시 됩니다. 이 이름은 이후 챕터의 응용 프로그램에서 데이터를 참조 하는 데 사용 됩니다 (함수 앱 만들기 및 Power BI). 이름으로 **Iotmessages** 를 삽입 하 고이 문서의 뒷부분에서 사용 되는 경우에만 기억할 수 있으며 **확인** 을 클릭 합니다. 

12. 새 테이블을 만든 후에는 **테이블 서비스** 페이지 (아래쪽)에서 볼 수 있습니다.

    ![새 테이블을 만들었습니다.](images/AzureLabs-Lab313-42.png)  

13. 이제 **액세스 키** 를 클릭 하 고 **Storage 계정 이름** 및 **키** 의 복사본을 가져옵니다 (메모장 사용) .이 과정의 뒷부분에서 **Azure 함수 앱** 를 만들 때 이러한 값을 사용 합니다.

    ![새 테이블을 만들었습니다.](images/AzureLabs-Lab313-43.png) 

14. 왼쪽의 패널을 다시 사용 하 여 *테이블 서비스* 섹션으로 스크롤하고 테이블 (또는 새 포털에서 **테이블 찾아보기**) **을 클릭 하** 고 **테이블 URL** 의 복사본 (메모장 사용)을 가져옵니다. 이 과정에서 나중에 테이블을 **Power BI** 응용 프로그램에 연결할 때이 값을 사용 합니다.

    ![새 테이블을 만들었습니다.](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>12 장-Azure 테이블 완료

이제 **Table Service** storage 계정이 설정 되었으므로 데이터를 추가 하 여 정보를 저장 하 고 검색 하는 데 사용 됩니다. 테이블 편집은 **Visual Studio** 를 통해 수행할 수 있습니다.

1. **Visual Studio** (Visual Studio Code **하지 않음** )을 엽니다.

2. 메뉴에서 클라우드 탐색기 **보기** 를 클릭  >  합니다.

    ![클라우드 탐색기 열기](images/AzureLabs-Lab313-45.png)

3. **클라우드 탐색기** 은 도킹 된 항목으로 열립니다. 로드 시 시간이 걸릴 수 있으므로 잠시 기다려 주십시오.

    > [!WARNING] 
    > *Storage 계정을* 만드는 데 사용한 구독이 표시 되지 않는 경우 다음을 확인 합니다. 
    > - Azure Portal에 사용한 것과 동일한 계정에 로그인 합니다.
    > - 계정 관리 페이지에서 구독을 선택 했습니다 (계정 설정에서 필터를 적용 해야 할 수 있음).  
    >
    >   ![구독 찾기](images/AzureLabs-Lab313-46.png)

4. Azure cloud Services가 표시 됩니다. **Storage 계정을** 찾고 왼쪽에 있는 화살표를 클릭 하 여 계정을 확장 합니다.

    ![저장소 계정 열기](images/AzureLabs-Lab313-47.png)

5. 확장 되 면 새로 만든 **Storage 계정을** 사용할 수 있습니다. 저장소 왼쪽에 있는 화살표를 클릭 한 다음 확장 되 면 **테이블** 을 찾아 해당 옆의 화살표를 클릭 하 여 마지막 챕터에서 만든 **테이블** 을 표시 합니다. **테이블** 을 두 번 클릭 합니다.

6. 테이블이 Visual Studio 창의 가운데에 열립니다. (더하기)가 있는 테이블 아이콘을 클릭 **+** 합니다.

    ![새 테이블 추가](images/AzureLabs-Lab313-48.png)

7. *엔터티를 추가* 하 라는 창이 표시 됩니다. 3 개의 속성을 포함 하지만 엔터티는 하나만 만듭니다. *PartitionKey* 및 *rowkey* 는 테이블에서 데이터를 찾기 위해 사용 되므로 이미 제공 된 것을 알 수 있습니다. 

    ![파티션 및 행 키](images/AzureLabs-Lab313-49.png)

8. 다음 값을 업데이트합니다.

    - 이름: **PartitionKey**, 값: **PK_IoTMessages** 

    - 이름: **Rowkey**, 값: **RK_1_IoTMessages** 

9. 그런 다음 *엔터티 추가* 창의 왼쪽 아래에 있는 **속성 추가** 를 클릭 하 고 다음 속성을 추가 합니다.

    - **MessageContent** 는 *문자열로* 값을 비워 둡니다.

10. 테이블은 아래 이미지의 테이블과 일치해야 합니다.

    ![올바른 값 추가](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > 엔터티가 행 키에 숫자 1을 가지는 이유는 이 과정을 추가로 실험하려는 경우 메시지를 더 추가할 수 있기 때문입니다.

11. 완료되면 **확인을** 클릭합니다. 이제 테이블을 사용할 준비가 되었습니다.

## <a name="chapter-13---create-an-azure-function-app"></a>13장 - Azure 함수 앱 만들기 

이제 이전 챕터에서 만든 **Table** *Service에 IoT Edge* 디바이스 메시지를 저장하기 위해 *IoT Hub* 서비스에서 호출되는 Azure *함수 앱을* 만들 차례입니다.

먼저 Azure Function에서 필요한 라이브러리를 로드할 수 있는 파일을 만들어야 합니다.

1.  **메모장** 엽니다(Windows *키를* 누르고 *메모장* 입력).

    ![메모장 열기](images/AzureLabs-Lab313-51.png)

2.  메모장 열린 후 아래에 JSON 구조를 삽입합니다. 이 작업이 완료되면 데스크톱에 **project.js저장합니다.** 이 파일은 함수에서 사용할 라이브러리를 정의합니다. NuGet 사용한 경우 익숙해 보일 것입니다.
    
    > [!WARNING]
    > 이름 지정이 올바른 것이 중요합니다. .txt파일 **확장명이 없는지** 확인합니다. 참조는 아래를 참조하세요.
    >
    > ![JSON 저장](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  [Azure Portal](https://portal.azure.com)에 로그인합니다.

4.  로그인하면 왼쪽 위 모서리에서 **리소스 만들기를** 클릭하고 **함수 앱을** 검색한 다음 **Enter** 키를 눌러 검색합니다. 결과에서 *함수 앱을* 클릭하여 새 패널을 엽니다.

    ![함수 앱 검색](images/AzureLabs-Lab313-53.png)

5.  새 패널에는 **함수 App** Service에 대한 설명이 표시됩니다. 이 패널의 왼쪽 아래에서 **만들기** 단추를 클릭하여 이 서비스와의 연결을 만듭니다.

    ![함수 앱 인스턴스](images/AzureLabs-Lab313-54.png)

6.  **만들기를** 클릭하면 다음을 입력합니다.

    1. **앱 이름** 의 경우 이 서비스 인스턴스에 원하는 이름을 삽입합니다.

    2. **구독** 을 선택합니다.

    3. **함수 App Service** 처음 만드는 경우 적합한 가격 책정 계층을 선택합니다. 무료 계층을 사용할 수 있어야 합니다.

    4. 리소스 **그룹을** 선택하거나 새 리소스 그룹을 만듭니다. 리소스 그룹은 Azure 자산 컬렉션에 대한 액세스를 모니터링, 제어, 프로비전 및 관리, 청구하는 방법을 제공합니다. 모든 Azure 서비스를 단일 프로젝트(예: 이러한 과정)와 연결된 공용 리소스 그룹에 유지하는 것이 좋습니다.

        > Azure 리소스 그룹에 대해 자세히 알아보려면 리소스 그룹을 [관리하는 방법에 대한](/azure/azure-resource-manager/resource-group-portal)이 링크를 따르세요.

    5. **OS의** 경우 의도한 플랫폼인 Windows 클릭합니다.

    6. 호스팅 **계획을** 선택합니다(이 자습서에서는 **소비 계획** 사용).

    7. **위치** 선택(이전 단계에서 빌드한 스토리지와 동일한 위치 선택)

    8. **Storage** 섹션의 경우 **이전 단계에서 만든 Storage 서비스를 선택해야 합니다.**

    9. 이 앱에는 *애플리케이션 Insights* 필요하지 않으므로 자유롭게 **끄기로 둡니다.**

    10. **만들기** 를 클릭합니다.

        ![새 인스턴스 만들기](images/AzureLabs-Lab313-55.png)

7.  **만들기를** 클릭하면 서비스가 생성될 때까지 기다려야 합니다. 이 경우 1분 정도 걸릴 수 있습니다.

8.  서비스 인스턴스가 만들어지면 포털에 알림이 표시됩니다.

    ![새 알림](images/AzureLabs-Lab313-56.png)

9.  배포가 성공하면 알림을 클릭합니다(완료).

10. 알림에서 **리소스로 이동** 단추를 클릭하여 새 서비스 인스턴스를 탐색합니다. 

    ![리소스로 이동](images/AzureLabs-Lab313-57.png)

11. 새 패널의 왼쪽에서 함수 옆에 있는 **+** (더하기) *아이콘을* 클릭하여 새 함수를 만듭니다.

    ![새 함수 추가](images/AzureLabs-Lab313-58.png)

12. 중앙 패널 내에 **함수** 만들기 창이 표시됩니다. Scroll down **사용자 지정 함수** 를 클릭합니다.

    ![사용자 지정 함수](images/AzureLabs-Lab313-59.png)

13. 다음 페이지를 Scroll down **IoT Hub(이벤트 허브)를** 찾을 때까지 해당 페이지를 클릭합니다.

    ![사용자 지정 함수](images/AzureLabs-Lab313-60.png)

14. **IoT Hub(Event Hub)** 블레이드에서 **언어를** **C#으로** 설정한 다음 **새** 를 클릭합니다.

    ![사용자 지정 함수](images/AzureLabs-Lab313-61.png)

15. 표시되는 창에서 **IoT Hub** 선택되어 있고 *IoT Hub* 필드의 이름이 이전에 만든 *IoT Hub 서비스의* [이름(8단계에서 3장](#chapter-3---the-iot-hub-service))과 일치하는지 확인합니다. 그런 다음 **선택** 단추를 클릭합니다.

    ![사용자 지정 함수](images/AzureLabs-Lab313-62.png)

16. **IoT Hub(Event Hub)** 블레이드로 **돌아가서 만들기를** 클릭합니다.

    ![사용자 지정 함수](images/AzureLabs-Lab313-63.png)

17. 함수 편집기로 리디렉션됩니다.

    ![사용자 지정 함수](images/AzureLabs-Lab313-64.png)

18. 이 코드의 모든 코드를 삭제하고 다음으로 대체합니다.

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. 다음 변수가 Storage 계정 에서 찾을 수 있는 **적절한 값(각각** [11장 및 13단계의](#chapter-11---create-table-service)**테이블** 및 Storage 값)에 해당하도록 다음 변수를 **변경합니다.**

    - **tableName**- **Storage 계정에** 있는 **테이블의** 이름입니다.
    - **tableURL**- **테이블의** URL이 Storage 계정에 **있습니다.**
    - **storageAccountName**- **Storage 계정** 이름의 이름과 일치하는 값의 이름입니다.
    - **storageAccountKey**- 이전에 만든 Storage 서비스에서 가져온 키를 갖습니다.

    ![사용자 지정 함수](images/AzureLabs-Lab313-65.png)

20. 코드를 배치한 후 **저장을** 클릭합니다.

21. 다음으로 **\<** 페이지의 오른쪽에 있는 (화살표) 아이콘을 클릭합니다.

    ![사용자 지정 함수](images/AzureLabs-Lab313-66.png)

22. 패널이 오른쪽에서 슬라이드됩니다. 해당 패널에서 **업로드** 클릭하면 *파일 브라우저가* 나타납니다.

23. 이전에 메모장 만든 **파일의** **project.js** 이동하여 클릭한 다음 **열기** 단추를 클릭합니다. 이 파일은 함수에서 사용할 라이브러리를 정의합니다.

    ![사용자 지정 함수](images/AzureLabs-Lab313-67.png)

24. 파일이 업로드되면 오른쪽 패널에 표시됩니다. 이를 클릭하면 **함수** 편집기 내에서 열립니다. 다음 이미지와 **정확히** 같아야 합니다.

    ![사용자 지정 함수](images/AzureLabs-Lab313-68.png)

25. 이 시점에서 *함수의* 기능을 테스트하여 테이블에 메시지를 저장하는 것이 좋습니다. 창의 오른쪽 위에서 **테스트를** 클릭합니다.

    ![사용자 지정 함수](images/AzureLabs-Lab313-69.png)

26. 위의 이미지와 같이 **요청 본문** 에 메시지를 삽입하고 **실행을** 클릭합니다. 

27. 함수가 실행되어 결과 상태를 표시합니다.(출력 창 위에 녹색 **상태 202 수락됨이** 표시됩니다. 즉, 성공적으로 호출되었습니다.) 

    ![출력 결과](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>14장 - 활성 메시지 보기

이제 Visual Studio(Visual Studio Code **않음)을** 열면 *MessageContent* 문자열 영역에 저장되기 때문에 테스트 메시지 결과를 시각화할 수 있습니다.

![사용자 지정 함수](images/AzureLabs-Lab313-71.png)

Table Service 및 함수 앱이 설치되면 Ubuntu 디바이스 메시지가 *IoTMessages* 테이블에 표시됩니다. 아직 실행하지 않은 경우 디바이스를 다시 시작하면 Visual Studio 클라우드 탐색기 사용하여 테이블 내에서 디바이스 및 모듈의 결과 메시지를 볼 수 *있습니다.*

![데이터 시각화](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>15장 - Power BI 설정

IOT 디바이스에서 데이터를 시각화하려면 **Power BI(데스크톱** 버전)를 설정하여 방금 만든 *Table* Service에서 데이터를 수집합니다. 그러면 *HoloLens* 버전의 Power BI 해당 데이터를 사용하여 결과를 시각화합니다.

1.  Microsoft Store on Windows 10 열고 **Power BI Desktop** 검색합니다.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  애플리케이션을 다운로드합니다. 다운로드가 완료되면 엽니다.

3.  *Microsoft 365* **계정으로 Power BI 로그인합니다.** 등록하기 위해 브라우저로 리디렉션될 수 있습니다. 등록한 후에는 Power BI 앱으로 돌아가서 다시 로그인합니다.

4.  데이터 **얻기를** 클릭한 다음 **자세히...** 를 클릭합니다.

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  **Azure**, **Azure Table Storage** 를 클릭한 **다음, 커넥트** 클릭합니다.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Table Service를 만드는 동안 이전에 수집한 테이블[URL(11장 13단계)을](#chapter-11---create-table-service)삽입하라는 메시지가 표시됩니다.  URL을 삽입한 후 테이블 "하위 폴더"(이 과정에서는 IoTMessages)를 참조하는 경로 부분을 삭제합니다. 최종 결과는 아래 이미지에 표시된 대로 여야 합니다. 그런 다음 **확인을** 클릭합니다.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Table Storage 만드는 동안 이전에 기록한 **Storage 키를** 삽입하라는 메시지가 표시됩니다(11장 의 [11단계).](#chapter-11---create-table-service) 그런 다음 **커넥트** 클릭합니다.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. **탐색기 패널이** 표시되고 테이블 옆의 상자를 선택한 다음 **로드를** 클릭합니다.

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. 이제 테이블이 Power BI 로드되었지만 테이블의 값을 표시하려면 쿼리가 필요합니다. 이렇게 하려면 화면 오른쪽의 **필드 패널에** 있는 테이블 이름을 마우스 오른쪽 단추로 클릭합니다. 그런 다음 **쿼리 편집** 을 클릭합니다.

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. **Power Query 편집기** 새 창으로 열리고 테이블이 표시됩니다. 테이블의 *콘텐츠* 열 내에서 **Record라는** 단어를 클릭하여 저장된 콘텐츠를 시각화합니다.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. 창의 왼쪽 위에서 **테이블로** 를 클릭합니다. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. **닫기 & 적용을** 클릭합니다.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. 쿼리 로드가 완료되면 화면 오른쪽의 **필드 패널** 내에서 **Name** 및 **Value** 매개 변수에 해당하는 상자를 선택해 **MessageContent** 열 콘텐츠를 시각화합니다.

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. 창의 왼쪽 위에 있는 **파란색 디스크 아이콘을** 클릭하여 선택한 폴더에 작업을 저장합니다.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. 이제 게시 단추를 클릭하여 작업 영역에 테이블을 업로드할 수 있습니다. 메시지가 표시되면 **내 작업 영역을** 클릭하고 *선택을* 클릭합니다. 제출의 성공적인 결과가 표시되기를 기다립니다.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> 다음 챕터는 HoloLens 관련이 있습니다. Power BI 현재 몰입형 애플리케이션으로 사용할 수 없습니다. 그러나 데스크톱 앱을 통해 Windows Mixed Reality Portal(즉, 클리프 하우스)에서 데스크톱 버전을 실행할 수 있습니다.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>16장 - HoloLens Power BI 데이터 표시

1. HoloLens 애플리케이션 목록에서 **아이콘을** 탭하여 Microsoft Store 에 로그인합니다.

    ![Power BI Hl](images/AzureLabs-Lab313-87.png)

2. **Power BI** 애플리케이션을 검색한 다음 다운로드합니다.

    ![Power BI Hl](images/AzureLabs-Lab313-88.png)

3. 애플리케이션 목록에서 **Power BI** 시작합니다. 

4. **Power BI** **Microsoft 365 계정에** 로그인하도록 요청할 수 있습니다.

5. 앱 내에서 작업 영역은 아래 이미지와 같이 기본적으로 표시되어야 합니다. 그렇지 않은 경우 창의 왼쪽에 있는 작업 영역 아이콘을 클릭하기만 하면 됩니다.

    ![Power BI Hl](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>IoT Hub 애플리케이션 완료

축하합니다. 시뮬레이션된 Virtual Machine Edge 디바이스를 통해 IoT Hub 서비스를 성공적으로 만들었습니다. 디바이스는 기계 학습 모델의 결과를 Azure Table Service에 전달할 수 있으며, Azure 함수 앱을 통해 Power BI 읽고 Microsoft HoloLens 내에서 시각화할 수 있습니다.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>보너스 연습

### <a name="exercise-1"></a>연습 1

테이블에 저장된 메시징 구조를 확장하고 그래프로 표시합니다. 나중에 표시하기 위해 더 많은 데이터를 수집하고 동일한 테이블에 저장할 수 있습니다.

### <a name="exercise-2"></a>연습 2

분석할 카메라를 통해 이미지를 캡처할 수 있도록 IoT 보드에 배포할 추가 "카메라 캡처" 모듈을 만듭니다.
