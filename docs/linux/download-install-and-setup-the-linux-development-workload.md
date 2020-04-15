---
title: 在 Visual Studio 中安裝 C++ Linux 工作負載
description: 描述如何在 Visual Studio 中下載、安裝和設定 Linux 工作負載。
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 8e10521ab35f3d85ced8bffd771b4e101d4d4fe6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364334"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>下載、安裝和設定 Linux 工作負載

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux 專案。

::: moniker-end

::: moniker range=">=vs-2017"

您可以使用 Windows 上的可視化工作室 IDE 創建、編輯和除錯C++在遠端 Linux 系統、虛擬機器或 Linux 的[Windows 子系統](/windows/wsl/about)上執行的專案。

您可以處理使用 CMake 的現有代碼庫,而無需將其轉換為 Visual Studio 專案。 如果程式碼基底為跨平台，您可以從 Visual Studio 內將 Windows 和 Linux 鎖定為目標。 例如,您可以使用 Visual Studio 在 Windows 上編輯、構建和調試代碼,然後快速重新置放 Linux 的專案,以在 Linux 環境中生成和調試。 Linux 標記會自動複製到本地電腦,Visual Studio 使用它們提供完整的 IntelliSense 支援(聲明完成、轉到定義等)。

針對上述任何一種情況，**使用 C++ 進行 Linux 開發**工作負載是必要項目。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Visual Studio 安裝程式

1. 在 Windows 搜尋方塊中鍵入「Visual Studio 安裝程式」：

   ![Windows 搜尋方塊](media/visual-studio-installer-search.png)

1. 在 [應用程式]**** 結果下方尋找該安裝程式，然後按兩下。 安裝程式開啟時,選擇 **「修改**」,然後按下 **「工作負載」** 選項卡。向下滾動到**其他工具集**,然後選擇**具有C++** 工作負載的 Linux 開發。

   ![適用於 Linux 開發的 Visual C++ 工作負載](media/linuxworkload.png)

1. 如果定位為 IoT 或嵌入式平臺,請轉到右側的 **「安裝詳細資訊**」窗格。 在**Linux 開發下,C++,** 展開**可選元件**,並選擇您需要的元件。 預設會選取適用於 Linux 的 CMake 支援。

1. 按一下 [修改]**** 繼續安裝。

## <a name="options-for-creating-a-linux-environment"></a>建立 Linux 環境的選項

如果您還沒有 Linux 機器，您可以在 Azure 上建立 Linux 虛擬機器。 如需詳細資訊，請參閱[快速入門：在 Azure 入口網站中建立 Linux 虛擬機器](/azure/virtual-machines/linux/quick-create-portal)。

在 Windows 10 上，您可以在適用於 Linux 的 Windows 子系統 (WSL) 上安裝最愛的 Linux 發行版本，並以其為目標。 如需詳細資訊，請參閱 [Windows 10 版適用於 Linux 的 Windows 子系統安裝指南](/windows/wsl/install-win10)。 如果您無法存取 Windows 應用程式商店,則可以[手動下載 WSL 發行版套件](/windows/wsl/install-manual)。 WSL 是一個方便的控制台環境,但不建議用於圖形應用程式。

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 中的 Linux 專案需要在遠端 Linux 系統或 WSL 上安裝以下依賴項:

- **編譯器**- Visual Studio 2019 具有開箱即用的支援 GCC 和[Clang](/cpp/build/clang-support-cmake?view=vs-2019)。
- **gdb** - Visual Studio 在 Linux 系統上自動啟動 gdb,並使用 Visual Studio 調試器的前端在 Linux 上提供全保真調試體驗。
- **rsync**和**zip** - 包含 rsync 和 zip 允許 Visual Studio 從 Linux 系統中提取標頭檔到 Windows 檔案系統供 IntelliSense 使用。
- **讓**
- **打開伺服器**(僅限遠端 Linux 系統) - Visual Studio 透過安全的 SSH 連接連接到遠端 Linux 系統。
- **CMake(** 只有限制 CMake 專案) ─您可以安裝微軟的[靜態連結的 CMake 二進位檔案,用於 Linux](https://github.com/microsoft/CMake/releases)。
- **忍者構建**(僅限 CMake 專案) -[忍者](https://ninja-build.org/)是 Visual Studio 2019 版 16.6 或更高版本中 Linux 和 WSL 配置的預設生成器。

以下命令假定您使用的是 g# 而不是 clang。

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 中的 Linux 專案需要在遠端 Linux 系統或 WSL 上安裝以下依賴項:

- **gcc** - Visual Studio 2017 對 GCC 提供了現成的支援。
- **gdb** - Visual Studio 在 Linux 系統上自動啟動 gdb,並使用 Visual Studio 調試器的前端在 Linux 上提供全保真調試體驗。
- **rsync**和**zip** - 包含 rsync 和 zip 允許 Visual Studio 從 Linux 系統中提取標頭檔到 Windows 檔案系統,用於 IntelliSense。
- **讓**
- **打開伺服器**- Visual Studio 透過安全的 SSH 連接連接到遠端 Linux 系統。
- **CMake(** 只有限制 CMake 專案) ─您可以安裝微軟的[靜態連結的 CMake 二進位檔案,用於 Linux](https://github.com/microsoft/CMake/releases)。

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Linux 設定:WSL 上的 Ubuntu

當您以 WSL 為目標時，不需要新增遠端連線，也不需要設定 SSH，就可以建置及偵錯。 使用 Visual Studio 自動同步處理 Linux 標頭以獲取 Intellisense 支援時，需要 **zip** 和 **rsync**。 如果所需的應用程式不存在,您可以按如下方式安裝它們。 **忍者構建**僅適用於 CMake 專案。

```bash
sudo apt-get install g++ gdb make ninja-build rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>遠端 Linux 系統上的 Ubuntu

目標 Linux 系統必須具有**打開伺服器****、g#、gdb、****忍者生成**(僅限 CMake 專案)並**安裝** **gdb** ,並且 ssh 守護進程必須運行。 **自動同步和** **rsync**是自動同步遠端標頭與本地電腦的智慧感知支援所必需的。 如果還沒有這些應用程式，您可以依下列方式進行安裝︰

1. 在 Linux 電腦的殼層提示字元中，執行︰

   ```bash
   sudo apt-get install openssh-server g++ gdb make ninja-build rsync zip
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

Fedora 會使用 **dnf** 套件安裝程式。 要下載**g#**, **gdb**,**讓**, **rsync,****忍者建構**, 與**zip**, 執行:

   ```bash
   sudo dnf install gcc-g++ gdb rsync ninja-build make zip
   ```

使用 Visual Studio 自動同步處理 Linux 標頭以獲取 Intellisense 支援時，需要 **zip** 和 **rsync**。 **忍者構建**僅適用於 CMake 專案。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>遠端 Linux 系統上的 Fedora

執行 Fedora 的目標電腦使用 **dnf** 套件安裝程式。 要下載**開啟伺服器**, **g#**, **gdb**,**使**,**忍者建構**, **rsync,** 和**zip**, 並重新啟動 ssh 守護行程, 按照這些說明。 **忍者構建**僅適用於 CMake 專案。

1. 在 Linux 電腦的殼層提示字元中，執行︰

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb ninja-build make rsync zip
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

您現在已準備好建立或開啟 Linux 專案，並將它設定為在目標系統上執行。 如需詳細資訊，請參閱

- [建立新的 Linux 專案](create-a-new-linux-project.md)
- [設定 Linux CMake 專案](cmake-linux-project.md)
