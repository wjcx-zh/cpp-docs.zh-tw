---
title: 連線至 Visual Studio 中的目標 Linux 系統
description: 如何從 Visual Studio C++專案中連接到遠端 Linux 電腦或 Linux Windows 子系統。
ms.date: 01/17/2020
ms.openlocfilehash: 624dce6bb05e4f4a961628e0c6f455e11c14dff8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364368"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>連線至 Visual Studio 中的目標 Linux 系統

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range="vs-2017"

您可以設定 Linux 專案，以遠端電腦或適用於 Linux 的 Windows 子系統 (WSL) 為目標。 對於遠端電腦和 WSL,您需要在 Visual Studio 2017 中設定遠端連接。

::: moniker-end

::: moniker range="vs-2019"

您可以設定 Linux 專案，以遠端電腦或適用於 Linux 的 Windows 子系統 (WSL) 為目標。 對於遠端電腦,您需要在 Visual Studio 中設定遠端連接。 要連接到 WSL,請跳到「[連接到 WSL」](#connect-to-wsl)部分。

::: moniker-end

::: moniker range=">=vs-2017"

使用遠端連接時,Visual Studio 在遠端電腦上生成C++ Linux 專案。 它是物理計算機、雲中的 VM 還是 WSL 並不重要。
要生成專案,Visual Studio 會將原始程式碼複製到遠端 Linux 電腦。 然後,根據可視化工作室設置編譯代碼。

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Visual Studio 2019 版本 16.5 及更高版本還支援安全、聯邦資訊處理標準 (FIPS) 140-2 相容的加密連接到 Linux 系統進行遠端開發。 要使用符合 FIPS 的連接,請按照[設定符合 FIPS 的安全遠端 Linux 開發](set-up-fips-compliant-secure-remote-linux-development.md)的步驟進行操作。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>在遠端系統上設定 SSH 伺服器

如果 ssh 尚未在 Linux 系統上設置和運行,請按照以下步驟安裝它。 本文中的範例使用 Ubuntu 18.04 LTS 與 OpenSSH 伺服器版本 7.6。 但是,對於使用中等較新版本的 OpenSSH 的任何發行版,說明應相同。

1. Linux 系統上,安裝並啟動 OpenSSH 伺服器:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. 如果您希望 ssh 伺服器在系統啟動時自動啟動,請使用系統 ctl 啟用它:

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>設定遠端連線

1. 在可視化工作室中,在選單欄上選擇 **「工具>選項**」以打開 **「選項**」對話框。 然後選擇**跨平臺>連接管理器**以打開連接管理器對話方塊。

   如果您以前未在 Visual Studio 中設定連接,則首次生成專案時,Visual Studio 會為您打開連接管理器對話方塊。

1. 在"連接管理員"對話框中,選擇 **'添加**"按鈕以新增新連接。

   ![連線管理員](media/settings_connectionmanager.png)

   在這兩種情況下,都顯示「**連接到遠端系統」** 視窗。

   ![連線到遠端系統](media/connect.png)

1. 輸入以下資訊：

   | 項目 | 描述
   | ----- | ---
   | **主機名稱**           | 目標裝置的名稱或 IP 位址
   | **連接埠**                | 正在執行 SSH 服務的連接埠，一般是 22
   | **使用者名稱**           | 驗證使用者身分
   | **驗證類型** | 密碼與私密金鑰都受支援
   | **密碼**            | 所輸入使用者名稱的密碼
   | **私密金鑰檔**    | 為 SSH 連線所建立的私密金鑰檔案
   | **密碼**          | 與上面選取的私密金鑰搭配使用的複雜密碼

   您可以使用密碼或金鑰檔和密碼進行身份驗證。 對於許多開發方案,密碼身份驗證就足夠了,但密鑰檔更安全。 如果您已經有一個密鑰對,則可以重用它。 目前 Visual Studio 僅支援用於遠端連接的 RSA 和 DSA 密鑰。

1. 選擇 **「連線**」按鈕以嘗試連接到遠端電腦。

   如果連接成功,Visual Studio 將 IntelliSense 配置為使用遠端標頭。 如需詳細資訊，請參閱[適用於遠端系統標頭的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

   如果連線失敗，將會以紅色標出需要變更的輸入方塊。

   ![連線管理員錯誤](media/settings_connectionmanagererror.png)

   如果使用金鑰檔進行身份驗證,請確保目標電腦的 SSH 伺服器正在執行並正確配置。

   ::: moniker-end

   ::: moniker range="vs-2019"

## <a name="logging-for-remote-connections"></a>遠端連線的紀錄記錄

   您可以啟用日誌記錄來幫助解決連接問題。 在選單列上,選擇**工具>選項**。 在**選項**「對話框中,選擇**跨平臺>日誌紀錄**:

   ![遠端記錄](media/remote-logging-vs2019.png)

   記錄檔包含連線、傳送到遠端電腦 (其文字、結束代碼和執行時間) 的所有命令，以及從 Visual Studio 到殼層的所有輸出。 記錄適用於任何跨平台的 CMake 專案或 Visual Studio 中的 MSBuild 型 Linux 專案。

   您可以將輸出設定為轉到檔案或「輸出」視窗中的**跨平台紀錄記錄**窗格。 對於基於 MSBuild 的 Linux 專案,發送到遠端電腦的 MSBuild 命令不會路由到**輸出視窗**,因為它們是行程外發出的。 相反,它們被記錄到檔,前置碼為"msbuild_"

## <a name="command-line-utility-for-the-connection-manager"></a>連線管理員的命令列實用程式  

**Visual Studio 2019 版本 16.5 或更高版本**:ConnectionManager.exe 是一個命令列實用程式,用於管理 Visual Studio 外部的遠端開發連接。 它對於預配新開發計算機等任務很有用。 或者,您可以使用它設置 Visual Studio 進行持續整合。 有關範例與連接管理員指令的完整參考,請參閱[連線管理員參考](connectionmanager-reference.md)。  

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="tcp-port-forwarding"></a>TCP 連接埠轉送

Visual Studio 的 Linux 支援依賴於 TCP 連接埠轉發。 如果遠端系統上禁用 TCP 連接埠轉送 **,Rsync**和**gdbserver**會受到影響。 如果您受到此依賴項的影響,則可以在開發人員[社區上上](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html)上上投票。

rsync 以 MSBuild 的 Linux 專案與 CMake 專案來[將標頭從遠端系統複製到 Windows,供 IntelliSense 使用](configure-a-linux-project.md#remote_intellisense)。 如果無法啟用 TCP 連接埠轉送,請關閉自動下載遠端標頭。 要關閉它,請使用**工具>選項>跨平臺>連接管理器>遠端標頭智慧感知管理程式**。 如果遠端系統未啟用 TCP 連接埠轉送,則在開始下載 IntelliSense 的遠端標頭時,您將看到此錯誤:

![標題錯誤](media/port-forwarding-headers-error.png)

rsync 還被 Visual Studio 的 CMake 支援用於將源檔案複製到遠端系統。 如果無法啟用 TCP 連接埠轉寄,則可以使用 sftp 作為遠端複製來源方法。 sftp 通常比 rsync 慢,但不依賴於 TCP 埠轉發。 您可以使用[「CMake 設定編輯器](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects)」中的**遠端CopySourcesMethod**屬性管理遠端複製來源方法。 如果在遠端系統上禁用 TCP 連接埠轉送,則在首次調用 rsync 時,在 CMake 輸出視窗中將看到錯誤。

![Rsync 錯誤](media/port-forwarding-copy-error.png)

gdbserver 可用於在嵌入式設備上進行調試。 如果無法啟用 TCP 連接埠轉發,則必須對所有遠端調試方案使用 gdb。 默認情況下,在遠端系統上調試專案時使用 gdb。

## <a name="connect-to-wsl"></a>連線到 WSL

::: moniker-end

::: moniker range="vs-2017"

在 Visual Studio 2017 中,使用與遠端 Linux 電腦相同的步驟連接到 WSL。 使用 **localhost** 作為 [主機名稱]****。

::: moniker-end

::: moniker range="vs-2019"

使用[適用於 Linux 的 Windows 子系統 (WSL)](/windows/wsl/about) 時對使用 C++ 的 Visual Studio 2019 16.1 版新增原生支援。 這意味著您可以直接在本地 WSL 安裝上生成和調試。 您不再需要添加遠端連接或配置 SSH。 您可於此處找到[如何安裝 WSL](/windows/wsl/install-win10)的詳細資料。

要將 WSL 安裝設定為使用 Visual Studio,您需要安裝以下工具:gcc 或 clang、gdb、製作、忍者生成(僅適用於使用 Visual Studio 2019 版本 16.6 或更高版本的 CMake 專案)、rsync 和 zip。 您可以使用此指令在使用 apt 的分版上安裝, 此指令安裝 g# 編譯器:

```bash
sudo apt install g++ gdb make ninja-build rsync zip
```

有關詳細資訊,請參閱[下載、安裝和設定 Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

要為 WSL 設定 MSBuild 專案,請參考[設定 Linux 專案](configure-a-linux-project.md)。 要為 WSL 設定 CMake 專案,請參考[設定 Linux CMake 專案](cmake-linux-project.md)。 為了遵循逐步指示來透過 WSL 建立簡單的主控台應用程式，請閱讀這篇簡介部落格文章：[C++ with Visual Studio 2019 and the Windows Subsystem for Linux (WSL)](https://devblogs.microsoft.com/cppblog/c-with-visual-studio-2019-and-windows-subsystem-for-linux-wsl/)。

::: moniker-end

## <a name="see-also"></a>另請參閱

[設定 Linux 專案](configure-a-linux-project.md)\
[設定 Linux CMake 專案](cmake-linux-project.md)\
[部署、執行及除錯 Linux 專案](deploy-run-and-debug-your-linux-project.md)\
[設定 CMake 偵錯工作階段](../build/configure-cmake-debugging-sessions.md)
