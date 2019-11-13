---
title: 連線至 Visual Studio 中的目標 Linux 系統
description: 如何從 Visual Studio C++專案內部，連接至 linux 的遠端 linux 電腦或 Windows 子系統。
ms.date: 11/09/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 6f7116ab5dc6c77f88d0787beac32d1c1e0a4716
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966578"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>連線至 Visual Studio 中的目標 Linux 系統

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range=">=vs-2017"

您可以設定 Linux 專案，以遠端電腦或適用於 Linux 的 Windows 子系統 (WSL) 為目標。 針對遠端電腦以及 Visual Studio 2017 上的 WSL，您需要設定遠端連線。

## <a name="connect-to-a-remote-linux-computer"></a>連線至遠端 Linux 電腦

建立遠端 Linux C++系統（VM 或實體機器）的 linux 專案時，會將 linux 原始程式碼複製到您的遠端 linux 電腦。 然後，它會根據 Visual Studio 設定進行編譯。

設定此遠端連線：

1. 第一次建立專案。 或者，您可以手動建立新的專案。 選取 **工具 > 選項**，開啟 **跨平臺 > 連線管理員** 節點，然後選擇 **新增** 按鈕。

   ![連線管理員](media/settings_connectionmanager.png)

   在任一情況下，都會顯示 [**連接到遠端系統**] 視窗。

   ![連線到遠端系統](media/connect.png)

1. 輸入下列資訊：

   | 進入 | 描述
   | ----- | ---
   | **主機名稱**           | 目標裝置的名稱或 IP 位址
   | **連接埠**                | 正在執行 SSH 服務的連接埠，一般是 22
   | **使用者名稱**           | 驗證使用者身分
   | **驗證類型** | 同時支援密碼和私密金鑰
   | **密碼**            | 所輸入使用者名稱的密碼
   | **私密金鑰檔**    | 為 SSH 連線所建立的私密金鑰檔案
   | **複雜密碼**          | 與上面選取的私密金鑰搭配使用的複雜密碼

   您可以使用密碼或金鑰檔，以及用於驗證的複雜密碼。 在許多的開發案例中，密碼驗證已經足夠。 如果您想要使用公開/私密金鑰檔案，可以建立一個新的公開/私密金鑰檔案，或[重複使用現有的公開/私密金鑰檔案](https://security.stackexchange.com/questions/10203/reusing-private-public-keys)。 目前僅支援 RSA 和 DSA 金鑰。

   您可以依照下列步驟，建立私密 RSA 金鑰檔案：

   1. 在 Windows 電腦上，使用 `ssh-keygen -t rsa` 建立 ssh 金鑰組。 命令會建立公開金鑰和私密金鑰。 根據預設，它會使用 `id_rsa.pub` 和 `id_rsa`的名稱，將索引鍵放在 `C:\Users\%USERNAME%\.ssh`之下。

   1. 將公開金鑰從 Windows 複製到 Linux 電腦：`scp -p C:\Users\%USERNAME%\.ssh\id_rsa.pub user@hostname`。

   1. 在 Linux 系統上，將金鑰新增至授權金鑰的清單中 (並確認檔案有正確的權限)：`cat ~/id_rsa.pub >> ~/.ssh/authorized_keys; chmod 600 ~/.ssh/authorized_keys`

1. 選擇 [連線 **]** 按鈕以嘗試連接到遠端電腦。

   如果連線成功，Visual Studio 會開始將 IntelliSense 設定為使用遠端標頭。 如需詳細資訊，請參閱[適用於遠端系統標頭的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

   如果連線失敗，將會以紅色標出需要變更的輸入方塊。

   ![連線管理員錯誤](media/settings_connectionmanagererror.png)

   如果您使用金鑰檔案進行驗證，請確定目的電腦的 SSH 伺服器正在執行且已正確設定。

   ::: moniker-end

   ::: moniker range="vs-2019"

   移至 [工具] > [選項] > [跨平台] > [記錄] 來啟用記錄，以協助疑難排解連線問題：

   ![遠端記錄](media/remote-logging-vs2019.png)

   記錄檔包含連線、傳送到遠端電腦 (其文字、結束代碼和執行時間) 的所有命令，以及從 Visual Studio 到殼層的所有輸出。 記錄適用於任何跨平台的 CMake 專案或 Visual Studio 中的 MSBuild 型 Linux 專案。

   您可以設定輸出到檔案或 [輸出] 視窗中的 [跨平台記錄] 窗格。 對於以 MSBuild 為基礎的 Linux 專案，傳送至遠端電腦的 MSBuild 命令不會路由傳送至**輸出視窗**，因為它們是以跨進程的形式發出。 相反地，它們會記錄到前置詞為 "msbuild_" 的檔案。

## <a name="tcp-port-forwarding"></a>TCP 埠轉送

Visual Studio 的 Linux 支援相依于 TCP 埠轉送。 如果遠端系統上的 TCP 埠轉送已停用， **Rsync**和**gdbserver**會受到影響。 

以 MSBuild 為基礎的 Linux 專案和 CMake 專案會使用 rsync，將[標頭從您的遠端系統複製到 Windows，供 IntelliSense 使用](configure-a-linux-project.md#remote_intellisense)。 當您無法啟用 TCP 埠轉送時，請停用自動下載遠端標頭。 若要停用它，請使用**工具 > 選項 > 跨平臺 > 連線管理員 > 遠端標頭 IntelliSense 管理員**。 如果遠端系統未啟用 TCP 埠轉送，當下載 IntelliSense 的遠端標頭開始時，您會看到此錯誤：

![標頭錯誤](media/port-forwarding-headers-error.png)

Visual Studio 的 CMake 支援也會使用 Rsync，將來源檔案複製到遠端系統。 如果您無法啟用 TCP 埠轉送，您可以使用 sftp 做為遠端複製來源方法。 sftp 通常會比 rsync 慢，但不會相依于 TCP 埠轉送。 您可以使用 [ [CMake 設定編輯器](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects)] 中的 [ **remoteCopySourcesMethod** ] 屬性來管理遠端複製來源方法。 如果遠端系統上的 TCP 埠轉送已停用，當第一次叫用 rsync 時，您會在 [CMake 輸出] 視窗中看到錯誤。

![Rsync 錯誤](media/port-forwarding-copy-error.png)

Gdbserver 可用於在內嵌裝置上進行偵錯工具。 如果您無法啟用 TCP 埠轉送，則必須在所有遠端偵錯程式案例中使用 gdb。 在遠端系統上的專案進行調試時，預設會使用 Gdb。

::: moniker-end

## <a name="connect-to-wsl"></a>連線到 WSL

::: moniker range="vs-2017"

在 Visual Studio 2017 中，當您使用遠端 Linux 電腦時，您會使用相同的步驟來連接到 WSL。 使用 **localhost** 作為 [主機名稱]。

::: moniker-end

::: moniker range="vs-2019"

使用[適用於 Linux 的 Windows 子系統 (WSL)](/windows/wsl/about) 時對使用 C++ 的 Visual Studio 2019 16.1 版新增原生支援。 這表示您可以直接在本機 WSL 安裝上建立和偵錯工具。 您不再需要新增遠端連線或設定 SSH。 您可於此處找到[如何安裝 WSL](/windows/wsl/install-win10)的詳細資料。

若要將 WSL 安裝設定為使用 Visual Studio，您需要安裝下列工具： gcc 或 clang、gdb、make、rsync 和 zip。 您可以在使用 apt 的散發版本上安裝它們，方法是使用此命令，這也會安裝 g + + 編譯器：

```bash
sudo apt install g++ gdb make rsync zip
```

如需詳細資訊，請參閱[下載、安裝和設定 Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

若要設定 WSL 的 MSBuild 專案，請參閱[設定 Linux 專案](configure-a-linux-project.md)。 若要設定 WSL 的 CMake 專案，請參閱[設定 Linux CMake 專案](cmake-linux-project.md)。 為了遵循逐步指示來透過 WSL 建立簡單的主控台應用程式，請閱讀這篇簡介部落格文章：[C++ with Visual Studio 2019 and the Windows Subsystem for Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/)。

::: moniker-end

## <a name="see-also"></a>請參閱

[設定 Linux 專案](configure-a-linux-project.md)\
[設定 Linux CMake 專案](cmake-linux-project.md)\
[部署、執行及偵錯工具您的 Linux 專案](deploy-run-and-debug-your-linux-project.md)\
[設定 CMake 偵錯工作階段](../build/configure-cmake-debugging-sessions.md)
