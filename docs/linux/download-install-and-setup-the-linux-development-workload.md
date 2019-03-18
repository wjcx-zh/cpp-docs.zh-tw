---
title: 在 Visual Studio 中安裝 C++ Linux 工作負載
description: 描述如何在 Visual Studio 中下載、安裝和設定 Linux 工作負載。
ms.date: 03/05/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 74155724abb3a0e02cc27dd8a8d144f142ee4b6f
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747718"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>下載、安裝和設定 Linux 工作負載

您可以在 Windows 中使用 Visual Studio 2017 IDE 來建立、編輯 C++ 專案 (執行於 Linux 實體電腦、虛擬機器或[適用於 Linux 的 Windows 子系統](/windows/wsl/about)) 並為其進行偵錯。 

您可以使用採用 CMake 或任何其他組建系統的現有程式碼基底，而不必將它轉換成 Visual Studio 專案。 如果程式碼基底為跨平台，您可以從 Visual Studio 內將 Windows 和 Linux 鎖定為目標。 例如，您可以在 Windows 上使用 Visual Studio 編輯、偵錯並為您的程式碼設定設定檔，然後快速地將目標重設為 Linux 專案以進行進一步測試。 Linux 標頭檔會自動複製到您的本機電腦，Visual Studio 會使用它們來提供完整的 IntelliSense 支援 (陳述式完成、移至定義等)。
 
針對上述任何一種情況，**使用 C++ 進行 Linux 開發**工作負載是必要項目。 

## <a name="visual-studio-setup"></a>Visual Studio 安裝程式

1. 在 Windows 搜尋方塊中鍵入「Visual Studio 安裝程式」：![Windows 搜尋方塊](media/visual-studio-installer-search.png)
2. 在 [應用程式] 結果下方尋找該安裝程式，然後按兩下。 安裝程式開啟後，選擇 [修改]，然後按一下 [工作負載]標籤。向下捲動至 [其他工具組]，然後選取 [使用 C++ 進行 Linux 開發] 工作負載。

   ![適用於 Linux 開發的 Visual C++ 工作負載](media/linuxworkload.png)

1. 如果您使用 CMake，或您的目標是 IoT 或內嵌平台，請前往右側的 [安裝詳細資料] 窗格，在 [使用 C++ 進行 Linux 開發] 下方展開 [選用元件] 並選擇您需要的元件。

    **Visual Studio 2017 15.4 版和更新版本**<br/>:當您為 Visual Studio 安裝 Linux C++ 工作負載時，預設會選取適用於 Linux 的 CMake 支援。

1. 按一下 [修改] 繼續安裝。

## <a name="options-for-creating-a-linux-environment"></a>建立 Linux 環境的選項

如果您還沒有 Linux 機器，您可以在 Azure 上建立 Linux 虛擬機器。 如需詳細資訊，請參閱[快速入門：在 Azure 入口網站中建立 Linux 虛擬機器](/azure/virtual-machines/linux/quick-create-portal)。

在 Windows 10 上的另一個選項是啟動適用於 Linux 的 Windows 子系統。 如需詳細資訊，請參閱 [Windows 10 安裝指南](/windows/wsl/install-win10)。

## <a name="linux-setup-ubuntu"></a>Linux 安裝程式：Ubuntu

目標 Linux 電腦必須已安裝 **openssh-server**、**g++**、**gdb** 和 **gdbserver**，而且 ssh 精靈必須正在執行。 使用本機電腦來自動同步遠端標頭以進行 Intellisense 支援時，需要 **zip**。 如果還沒有這些應用程式，您可以依下列方式進行安裝︰

1. 在 Linux 電腦的殼層提示字元中，執行︰

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   因為是 sudo 命令，所以系統可能會提示您輸入根密碼。  如果是這樣，請輸入它後繼續。 完成後，將會安裝這些必要服務與工具。

1. 確定 ssh 服務正在您的 Linux 電腦上執行，方法是執行︰

   `sudo service ssh start`

   這會啟動服務並在背景執行，以準備好接受連線。

## <a name="linux-setup-fedora"></a>Linux 安裝程式：Fedora

執行 Fedora 的目標電腦使用 **dnf** 套件安裝程式。 若要下載 **openssh-server**、**g++**、**gdb**，**gdbserver** 與 **zip** 並重新啟動 ssh 精靈，請依照下列指示執行：

1. 在 Linux 電腦的殼層提示字元中，執行︰

   `sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip`

   因為是 sudo 命令，所以系統可能會提示您輸入根密碼。  如果是這樣，請輸入它後繼續。 完成後，將會安裝這些必要服務與工具。

1. 確定 ssh 服務正在您的 Linux 電腦上執行，方法是執行︰

   `sudo systemctl start sshd`

   這會啟動服務並在背景執行，以準備好接受連線。

## <a name="ensure-you-have-cmake-38-on-the-remote-linux-machine"></a>請確定您在遠端 Linux 電腦上擁有 CMake 3.8

您的 Linux 發行套件可能會有較舊版本的 CMake。 Visual Studio 中的 CMake 支援需要 CMake 3.8 中所引進的伺服器模式支援。 如需 Microsoft 提供的 CMake 種類，請在 [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) 下載最新之預先建置二進位檔案到您的 Linux 電腦。
