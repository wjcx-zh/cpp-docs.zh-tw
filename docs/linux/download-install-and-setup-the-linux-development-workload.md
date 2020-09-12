---
title: 在 Visual Studio 中安裝 C++ Linux 工作負載
description: 如何在 Visual Studio 中下載、安裝及設定 c + + 的 Linux 工作負載。
ms.date: 05/03/2020
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 3f8e6eb8285652078e5f26ca58601bc6ccfa80d1
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040973"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>下載、安裝和設定 Linux 工作負載

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux 專案。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end

::: moniker range=">=vs-2017"

您可以使用 Windows 上的 Visual Studio IDE，來建立、編輯和調試在遠端 Linux 系統、虛擬機器或 [Windows 子系統 Linux 版](/windows/wsl/about)上執行的 c + + 專案。

您可以使用 CMake 的現有程式碼基底，而不必將它轉換成 Visual Studio 專案。 如果程式碼基底為跨平台，您可以從 Visual Studio 內將 Windows 和 Linux 鎖定為目標。 例如，您可以使用 Visual Studio，在 Windows 上編輯、建立和偵錯工具代碼。 然後，快速地將用於 Linux 的專案重定目標，以在 Linux 環境中建立及進行 debug 錯。 Linux 標頭檔會自動複製到您的本機電腦。 Visual Studio 使用它們來提供完整的 IntelliSense 支援 (語句完成、移至定義等等) 。

針對上述任何一種情況，**使用 C++ 進行 Linux 開發**工作負載是必要項目。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Visual Studio 安裝程式

1. 在 Windows 搜尋方塊中鍵入「Visual Studio 安裝程式」：

   ![Windows 搜尋方塊](media/visual-studio-installer-search.png)

1. 在 [應用程式]**** 結果下方尋找該安裝程式，然後按兩下。 當安裝程式開啟時，選擇 [ **修改**]，然後按一下 [ **工作負載** ] 索引標籤。向下滾動至 **其他工具** 組，並選取 **使用 c + + 的 Linux 開發** 工作負載。

   ![適用於 Linux 開發的 Visual C++ 工作負載](media/linuxworkload.png)

1. 如果您的目標是 IoT 或內嵌平臺，請移至右側的 [ **安裝詳細資料** ] 窗格。 在 [ **使用 c + + 進行 Linux 開發**] 底下，展開 [ **選用元件**]，然後選擇您需要的元件。 預設會選取適用於 Linux 的 CMake 支援。

1. 按一下 [修改]**** 繼續安裝。

## <a name="options-for-creating-a-linux-environment"></a>建立 Linux 環境的選項

如果您還沒有 Linux 機器，您可以在 Azure 上建立 Linux 虛擬機器。 如需詳細資訊，請參閱[快速入門：在 Azure 入口網站中建立 Linux 虛擬機器](/azure/virtual-machines/linux/quick-create-portal)。

在 Windows 10 上，您可以在適用於 Linux 的 Windows 子系統 (WSL) 上安裝最愛的 Linux 發行版本，並以其為目標。 如需詳細資訊，請參閱 [Windows 10 版適用於 Linux 的 Windows 子系統安裝指南](/windows/wsl/install-win10)。 如果您無法存取 Windows Store，您可以 [手動下載 WSL 發行版本套件](/windows/wsl/install-manual)。 WSL 是方便的主控台環境，但不建議用於圖形化應用程式。

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 中的 linux 專案需要在您的遠端 Linux 系統或 WSL 上安裝下列相依性：

- **編譯器** Visual Studio 2019 具有 GCC 和 [Clang](../build/clang-support-cmake.md)的完整支援。
- **gdb** Visual Studio 會在 linux 系統上自動啟動 gdb，並使用 Visual Studio 偵錯工具的前端，在 linux 上提供完全失真的偵錯工具體驗。
- **rsync** 和 **zip** -包含 rsync 和 zip 可讓 Visual Studio 將您 Linux 系統中的標頭檔解壓縮至 Windows 檔案系統，以供 IntelliSense 使用。
- **make**
- **openssh-伺服器** (遠端 linux 系統只) Visual Studio 透過安全的 SSH 連線連接到遠端 linux 系統。
- **CMake** (僅限 CMake 專案) -您可以安裝 [適用于 Linux 的 Microsoft 靜態連結 CMake 二進位](https://github.com/microsoft/CMake/releases)檔。
- **ninja-組建** (CMake 專案僅限) - [ninja](https://ninja-build.org/) 是 Visual Studio 2019 16.6 版或更新版本中的 Linux 和 WSL 設定的預設產生器。

下列命令假設您使用的是 g + +，而不是 clang。

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 中的 linux 專案需要在您的遠端 Linux 系統或 WSL 上安裝下列相依性：

- **gcc** -Visual Studio 2017 具有 gcc 的完整支援。
- **gdb** Visual Studio 會在 linux 系統上自動啟動 gdb，並使用 Visual Studio 偵錯工具的前端，在 linux 上提供完全失真的偵錯工具體驗。
- **rsync** 和 **zip** -包含 rsync 和 zip 可讓 Visual Studio 將您 Linux 系統中的標頭檔解壓縮至 Windows 檔案系統，以用於 IntelliSense。
- **make**
- **openssh 伺服器** Visual Studio 透過安全的 SSH 連線來連線到遠端 Linux 系統。
- **CMake** (僅限 CMake 專案) -您可以安裝 [適用于 Linux 的 Microsoft 靜態連結 CMake 二進位](https://github.com/microsoft/CMake/releases)檔。

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Linux 安裝程式： WSL 上的 Ubuntu

當您以 WSL 為目標時，不需要新增遠端連線或設定 SSH 來建立和偵錯工具。 使用 Visual Studio 自動同步處理 Linux 標頭以獲取 Intellisense 支援時，需要 **zip** 和 **rsync**。 **ninja-** 只有 CMake 專案需要組建。 如果所需的應用程式還不存在，您可以使用下列命令來安裝它們：

```bash
sudo apt-get install g++ gdb make ninja-build rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>遠端 Linux 系統上的 Ubuntu

目標 Linux 系統必須有**openssh-server**、 **g + +**、 **gdb**和**已安裝。** **ninja-** 只需要 CMake 專案的組建。 **Ssh**背景程式必須正在執行。 需要**zip**和**rsync** ，才能自動同步遠端標頭與您的本機電腦以進行 Intellisense 支援。 如果這些應用程式還不存在，您可以如下所示進行安裝：

1. 在 Linux 電腦的殼層提示字元中，執行︰

   ```bash
   sudo apt-get install openssh-server g++ gdb make ninja-build rsync zip
   ```

   系統可能會提示您輸入根密碼以執行 sudo 命令。 如果是這樣，請輸入它後繼續。 完成後，將會安裝這些必要服務與工具。

1. 確定 ssh 服務正在您的 Linux 電腦上執行，方法是執行︰

   ```bash
   sudo service ssh start
   ```

   此命令會啟動服務並在背景中執行，以準備好接受連線。

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>WSL 上的 Fedora

Fedora 會使用 **dnf** 套件安裝程式。 若要下載 **g + +**、 **gdb**、 **make**、 **rsync**、 **ninja-build**和 **zip**，請執行：

   ```bash
   sudo dnf install gcc-g++ gdb rsync ninja-build make zip
   ```

使用 Visual Studio 自動同步處理 Linux 標頭以獲取 Intellisense 支援時，需要 **zip** 和 **rsync**。 **ninja-** 只有 CMake 專案需要組建。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>遠端 Linux 系統上的 Fedora

執行 Fedora 的目標電腦使用 **dnf** 套件安裝程式。 若要下載 **openssh-server**、 **g + +**、 **gdb**、 **make**、 **ninja-build**、 **rsync**和 **zip**，然後重新開機 ssh daemon，請遵循下列指示。 **ninja-** 只有 CMake 專案需要組建。

1. 在 Linux 電腦的殼層提示字元中，執行︰

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb ninja-build make rsync zip
   ```

   系統可能會提示您輸入根密碼以執行 sudo 命令。 如果是這樣，請輸入它後繼續。 完成後，將會安裝這些必要服務與工具。

1. 確定 ssh 服務正在您的 Linux 電腦上執行，方法是執行︰

   ```bash
   sudo systemctl start sshd
   ```

   此命令會啟動服務並在背景中執行，以準備好接受連線。

## <a name="next-steps"></a>後續步驟

您現在已準備好建立或開啟 Linux 專案，並將其設定為在目標系統上執行。 如需詳細資訊，請參閱

- [建立新的 Linux 專案](create-a-new-linux-project.md)
- [設定 Linux CMake 專案](cmake-linux-project.md)

::: moniker-end
