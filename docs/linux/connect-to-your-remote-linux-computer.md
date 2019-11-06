---
title: 連線至 Visual Studio 中的目標 Linux 系統
description: 如何從 Visual Studio C++ 專案內連線至遠端 Linux 電腦或 WSL。
ms.date: 09/04/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 3d91faa7aa83c86e8c2f3544ee61c16f75f8c346
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626792"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>連線至 Visual Studio 中的目標 Linux 系統

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range=">=vs-2017"

您可以設定 Linux 專案，以遠端電腦或適用於 Linux 的 Windows 子系統 (WSL) 為目標。 針對遠端電腦以及 Visual Studio 2017 上的 WSL，您需要設定遠端連線。 

## <a name="connect-to-a-remote-linux-computer"></a>連線至遠端 Linux 電腦

針對遠端 Linux 系統 (VM 或實體機器) 建置 C++ Linux 專案時，Linux 原始程式碼會複製到您的遠端 Linux 電腦，然後根據 Visual Studio 設定編譯。

設定此遠端連線：

1. 第一次建置專案，或選取 [工具] > [選項] 手動建立新項目，並開啟 [跨平台] > [連線管理員] 節點，然後按一下 [新增] 按鈕。

   ![連線管理員](media/settings_connectionmanager.png)

   在任一情況下，都會顯示 [Connect to Remote System]\(連線到遠端系統) 視窗。

   ![連線到遠端系統](media/connect.png)

1. 輸入下列資訊：

   | 進入 | 描述
   | ----- | ---
   | **主機名稱**           | 目標裝置的名稱或 IP 位址
   | **連接埠**                | 正在執行 SSH 服務的連接埠，一般是 22
   | **使用者名稱**           | 驗證使用者身分
   | **驗證類型** | 同時支援密碼或私密金鑰
   | **密碼**            | 所輸入使用者名稱的密碼
   | **私密金鑰檔**    | 為 SSH 連線所建立的私密金鑰檔案
   | **複雜密碼**          | 與上面選取的私密金鑰搭配使用的複雜密碼

   您可以使用密碼或金鑰檔案和複雜密碼進行驗證。 在許多的開發案例中，密碼驗證已經足夠。 如果您想要使用公開/私密金鑰檔案，可以建立一個新的公開/私密金鑰檔案，或[重複使用現有的公開/私密金鑰檔案](https://security.stackexchange.com/questions/10203/reusing-private-public-keys)。 目前僅支援 RSA 和 DSA 金鑰。 
   
   您可以依照下列步驟，建立私密 RSA 金鑰檔案：

    1. 在 Windows 電腦上，使用 `ssh-keygen -t rsa` 建立 ssh 金鑰組。 這將會建立一個公開金鑰和一個私密金鑰。 根據預設，金鑰會放在名稱為 `id_rsa.pub` 和 `id_rsa` 的 `C:\Users\%USERNAME%\.ssh` 底下。

    1. 將公開金鑰從 Windows 複製到 Linux 電腦：`scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`。

    1. 在 Linux 系統上，將金鑰新增至授權金鑰的清單中 (並確認檔案有正確的權限)：`cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. 按一下 [連線] 按鈕，嘗試連線到遠端電腦。 

   如果連線成功，Visual Studio 會開始將 IntelliSense 設定為使用遠端標頭。 如需詳細資訊，請參閱[適用於遠端系統標頭的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

   如果連線失敗，將會以紅色標出需要變更的輸入方塊。

   ![連線管理員錯誤](media/settings_connectionmanagererror.png)

   如果您使用金鑰檔案進行驗證，請確定目標電腦的 SSH 伺服器正在執行而且設定正確。

   ::: moniker-end

   ::: moniker range="vs-2019"

   移至 [工具] > [選項] > [跨平台] > [記錄] 來啟用記錄，以協助疑難排解連線問題：

   ![遠端記錄](media/remote-logging-vs2019.png)

   記錄檔包含連線、傳送到遠端電腦 (其文字、結束代碼和執行時間) 的所有命令，以及從 Visual Studio 到殼層的所有輸出。 記錄適用於任何跨平台的 CMake 專案或 Visual Studio 中的 MSBuild 型 Linux 專案。

   您可以設定輸出到檔案或 [輸出] 視窗中的 [跨平台記錄] 窗格。 對於 MSBuild 型 Linux 專案，MSBuild 發出到遠端電腦的命令不會路由傳送至 [輸出視窗]，因為它們是跨處理序發出的。 但是，它們會記錄到前置詞為 "msbuild_" 的檔案中。
   
## <a name="tcp-port-forwarding"></a>TCP 埠轉送

Visual Studio 的 Linux 支援相依于 TCP 埠轉送。 如果遠端系統上的 TCP 埠轉送已停用， **Rsync**和**gdbserver**會受到影響。 

以 MSBuild 為基礎的 Linux 專案和 CMake 專案會使用 Rsync，將[標頭從您的遠端系統複製到 Windows，以用於 IntelliSense](configure-a-linux-project.md#remote_intellisense)。 如果您無法啟用 TCP 埠轉送，則可以透過 工具 > 選項，停用自動下載遠端標頭 > 跨平臺 > 連線管理員 > 遠端標頭 IntelliSense 管理員。 如果您嘗試連線的遠端系統未啟用 TCP 埠轉送，則當 IntelliSense 的下載遠端標頭開始時，您會看到下列錯誤。

![標頭錯誤](media/port-forwarding-headers-error.png)

Visual Studio 的 CMake 支援也會使用 Rsync，將來源檔案複製到遠端系統。 如果您無法啟用 TCP 埠轉送，則可以使用 sftp 做為遠端複製來源方法。 Sftp 通常會比 rsync 慢，但不會相依于 TCP 埠轉送。 您可以使用 [ [CMake 設定編輯器](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects)] 中的 [remoteCopySourcesMethod] 屬性來管理遠端複製來源方法。 如果您的遠端系統上已停用 TCP 埠轉送，則第一次叫用 rsync 時，您會在 [CMake 輸出] 視窗中看到錯誤。

![Rsync 錯誤](media/port-forwarding-copy-error.png)

Gdbserver 可用於在內嵌裝置上進行偵錯工具。 如果您無法啟用 TCP 埠轉送，則必須在所有遠端偵錯程式案例中使用 gdb。 在遠端系統上的專案進行調試時，預設會使用 Gdb。 

   ::: moniker-end

## <a name="connect-to-wsl"></a>連線到 WSL

::: moniker range="vs-2017"

在 Visual Studio 2017 中，您可以使用與連線到遠端 Linux 電腦的相同步驟，連線到 WSL，如本文稍早所述。 使用 **localhost** 作為 [主機名稱]。

::: moniker-end

::: moniker range="vs-2019"

使用[適用於 Linux 的 Windows 子系統 (WSL)](https://docs.microsoft.com/windows/wsl/about) 時對使用 C++ 的 Visual Studio 2019 16.1 版新增原生支援。  這表示您不再需要新增遠端連線，也不需要設定 SSH，就可在自己的本機 WSL 安裝上進行建置及偵錯。 您可於此處找到[如何安裝 WSL](https://docs.microsoft.com/windows/wsl/install-win10)的詳細資料。

若要將 WSL 安裝設定為使用 Visual Studio 您需要安裝下列工具： gcc 或 clang、gdb、make、rsync 和 zip。 您可以在使用 apt 的散發版本上安裝它們，方法是使用此命令，這也會安裝 g + + 編譯器： 

```bash
sudo apt install g++ gdb make rsync zip
```
如需詳細資訊，請參閱[下載、安裝和設定 Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

若要設定 WSL 的專案，請參閱[設定 Linux 專案](configure-a-linux-project.md)或[設定 Linux CMake 專案](cmake-linux-project.md)，端視您所擁有的專案類型而定。 為了遵循逐步指示來透過 WSL 建立簡單的主控台應用程式，請閱讀這篇簡介部落格文章：[C++ with Visual Studio 2019 and the Windows Subsystem for Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/)。

::: moniker-end

## <a name="see-also"></a>請參閱

[設定 Linux 專案](configure-a-linux-project.md)<br />
[設定 Linux CMake 專案](cmake-linux-project.md)<br />
[部署、執行及偵錯 Linux 專案](deploy-run-and-debug-your-linux-project.md)<br />
[設定 CMake 偵錯工作階段](../build/configure-cmake-debugging-sessions.md)
