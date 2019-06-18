---
title: 在 Visual Studio 中安裝 C++ Linux 工作負載
description: 描述如何在 Visual Studio 中下載、安裝和設定 Linux 工作負載。
ms.date: 06/07/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: af4e3ec0ac21951163e92786555559cd02e8148f
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821576"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>下載、安裝和設定 Linux 工作負載


::: moniker range=">=vs-2017"

您可以在 Windows 中使用 Visual Studio IDE 來建立、編輯 C++ 專案 (執行於 Linux 實體電腦、虛擬機器或[適用於 Linux 的 Windows 子系統](/windows/wsl/about)) 並為其進行偵錯。 

您可以使用採用 CMake 或任何其他組建系統的現有程式碼基底，而不必將它轉換成 Visual Studio 專案。 如果程式碼基底為跨平台，您可以從 Visual Studio 內將 Windows 和 Linux 鎖定為目標。 例如，您可以在 Windows 上使用 Visual Studio 編輯、偵錯並為您的程式碼設定設定檔，然後快速地將目標重設為 Linux 專案以進行進一步測試。 Linux 標頭檔會自動複製到您的本機電腦，Visual Studio 會使用它們來提供完整的 IntelliSense 支援 (陳述式完成、移至定義等)。 
 
針對上述任何一種情況，**使用 C++ 進行 Linux 開發**工作負載是必要項目。 

::: moniker-end

::: moniker range="vs-2019"

在 Visual Studio 2019 中，您可以指定不同的目標來進行建置和偵錯。 以 WSL 為目標時，不再需要新增遠端連線或設定 SSH。

[AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) 的支援已整合到適用於 Linux 專案的 Visual Studio 中。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Visual Studio 安裝程式

1. 在 Windows 搜尋方塊中鍵入「Visual Studio 安裝程式」：![Windows 搜尋方塊](media/visual-studio-installer-search.png)
2. 在 [應用程式]  結果下方尋找該安裝程式，然後按兩下。 安裝程式開啟後，選擇 [修改]  ，然後按一下 [工作負載]  標籤。向下捲動至 [其他工具組]  ，然後選取 [使用 C++ 進行 Linux 開發]  工作負載。

   ![適用於 Linux 開發的 Visual C++ 工作負載](media/linuxworkload.png)

1. 如果您的目標是 IoT 或內嵌平台，請移至右側的 [安裝詳細資料]  窗格，在 [使用 C++ 進行 Linux 開發]  下方，展開 [選用元件]  並選擇您需要的元件。 預設會選取適用於 Linux 的 CMake 支援。

1. 按一下 [修改]  繼續安裝。

## <a name="options-for-creating-a-linux-environment"></a>建立 Linux 環境的選項

如果您還沒有 Linux 機器，您可以在 Azure 上建立 Linux 虛擬機器。 如需詳細資訊，請參閱[快速入門：在 Azure 入口網站中建立 Linux 虛擬機器](/azure/virtual-machines/linux/quick-create-portal)。

在 Windows 10 上，您可以在適用於 Linux 的 Windows 子系統 (WSL) 上安裝最愛的 Linux 發行版本，並以其為目標。 如需詳細資訊，請參閱 [Windows 10 版適用於 Linux 的 Windows 子系統安裝指南](/windows/wsl/install-win10)。 WSL 是一種方便存取的主控台環境，但不建議用於圖形化應用程式。 

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Linux 安裝程式：WSL 上的 Ubuntu

在 WSL 上，不需要任何遠端連線。 使用 Visual Studio 自動同步處理 Linux 標頭以獲取 Intellisense 支援時，需要 **zip** 和 **rsync**。 如果還沒有這些必要的應用程式，您可以依下列方式進行安裝：

```bash
sudo g++ gdb make rsync zip
```
::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>遠端 Linux 系統上的 Ubuntu

目標 Linux 系統必須已安裝 **openssh-server**、**g++** 、**gdb** 和 **gdbserver**，且 ssh 精靈必須正在執行。 使用本機電腦來自動同步遠端標頭以進行 Intellisense 支援時，需要 **zip**。 如果還沒有這些應用程式，您可以依下列方式進行安裝︰

1. 在 Linux 電腦的殼層提示字元中，執行︰

   ```bash
   sudo apt-get install openssh-server g++ gdb gdbserver zip
   ```

   因為是 sudo 命令，所以系統可能會提示您輸入根密碼。  如果是這樣，請輸入它後繼續。 完成後，將會安裝這些必要服務與工具。

1. 確定 ssh 服務正在您的 Linux 電腦上執行，方法是執行︰

   ```bash
   sudo service ssh start
   ```
   這會啟動服務並在背景執行，以準備好接受連線。

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>WSL 上的 Fedora

Fedora 會使用 **dnf** 套件安裝程式。 若要下載 **g++** 、**gdb**、**rsync** 和 **zip**，請執行：

   ```bash
   sudo dnf install gcc-g++ gdb rsync zip
   ```

使用 Visual Studio 自動同步處理 Linux 標頭以獲取 Intellisense 支援時，需要 **zip** 和 **rsync**。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>遠端 Linux 系統上的 Fedora

執行 Fedora 的目標電腦使用 **dnf** 套件安裝程式。 若要下載 **openssh-server**、**g++** 、**gdb**，**gdbserver** 與 **zip** 並重新啟動 ssh 精靈，請依照下列指示執行：

1. 在 Linux 電腦的殼層提示字元中，執行︰

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip
   ```
   因為是 sudo 命令，所以系統可能會提示您輸入根密碼。  如果是這樣，請輸入它後繼續。 完成後，將會安裝這些必要服務與工具。

1. 確定 ssh 服務正在您的 Linux 電腦上執行，方法是執行︰

   ```bash
   sudo systemctl start sshd
   ```

   這會啟動服務並在背景執行，以準備好接受連線。

::: moniker-end

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本有提供 Linux C++ 開發的支援。

::: moniker-end

## <a name="next-steps"></a>後續步驟

您現在已準備好建立或開啟 Linux 專案，並將它設定為在目標系統上執行。 如需詳細資訊，請參閱:

- [建立新的 Linux 專案](create-a-new-linux-project.md)
- [設定 Linux CMake 專案](cmake-linux-project.md)
