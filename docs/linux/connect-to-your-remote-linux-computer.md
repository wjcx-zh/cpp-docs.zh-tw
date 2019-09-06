---
title: 連線至 Visual Studio 中的目標 Linux 系統
description: 如何從 Visual Studio C++ 專案內連線至遠端 Linux 電腦或 WSL。
ms.date: 09/04/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 75d8b3db64d9b1f3562d6730685b7c29fe4982f4
ms.sourcegitcommit: a42d3b0408f02138dcd6fabcb98d50b0cb159191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70383395"
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

   | 進入 | 說明
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

   ::: moniker-end

## <a name="connect-to-wsl"></a>連線到 WSL

::: moniker range="vs-2017"

在 Visual Studio 2017 中，您可以使用與連線到遠端 Linux 電腦的相同步驟，連線到 WSL，如本文稍早所述。 使用 **localhost** 作為 [主機名稱]。

::: moniker-end

::: moniker range="vs-2019"

使用[適用於 Linux 的 Windows 子系統 (WSL)](https://docs.microsoft.com/windows/wsl/about) 時對使用 C++ 的 Visual Studio 2019 16.1 版新增原生支援。  這表示您不再需要新增遠端連線，也不需要設定 SSH，就可在自己的本機 WSL 安裝上進行建置及偵錯。 您可於此處找到[如何安裝 WSL](https://docs.microsoft.com/windows/wsl/install-win10)的詳細資料。

若要將 WSL 安裝設定為使用 Visual Studio，您需要安裝下列工具：gcc、gdb、make、rsync 和 zip。 您可以在搭配此命令使用 apt 的發行版上安裝它們： 

```bash
sudo apt install g++ gdb make rsync zip
```

若要設定 WSL 的專案，請參閱[設定 Linux 專案](configure-a-linux-project.md)或[設定 Linux CMake 專案](cmake-linux-project.md)，端視您所擁有的專案類型而定。 為了遵循逐步指示來透過 WSL 建立簡單的主控台應用程式，請閱讀這篇簡介部落格文章：[C++ with Visual Studio 2019 and the Windows Subsystem for Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/)。

::: moniker-end

## <a name="see-also"></a>另請參閱

[設定 Linux 專案](configure-a-linux-project.md)<br />
[設定 Linux CMake 專案](cmake-linux-project.md)<br />
[部署、執行及偵錯 Linux 專案](deploy-run-and-debug-your-linux-project.md)<br />
[設定 CMake 偵錯工作階段](../build/configure-cmake-debugging-sessions.md)
