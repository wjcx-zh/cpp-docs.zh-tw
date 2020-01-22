---
title: 連線至 Visual Studio 中的目標 Linux 系統
description: 如何從 Visual Studio C++專案內部，連接至 linux 的遠端 linux 電腦或 Windows 子系統。
ms.date: 01/17/2020
ms.openlocfilehash: d0065b63d7a81d3ae3d68b26184c88aca77f601c
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518214"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>連線至 Visual Studio 中的目標 Linux 系統

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range="vs-2017"

您可以設定 Linux 專案，以遠端電腦或適用於 Linux 的 Windows 子系統 (WSL) 為目標。 對於遠端電腦和 WSL，您都需要在 Visual Studio 2017 中設定遠端連線。

::: moniker-end

::: moniker range="vs-2019"

您可以設定 Linux 專案，以遠端電腦或適用於 Linux 的 Windows 子系統 (WSL) 為目標。 若為遠端電腦，您必須在 Visual Studio 中設定遠端連線。 若要連線到 WSL，請直接跳至 [連線[至 WSL]](#connect-to-wsl)區段。

::: moniker-end

::: moniker range=">=vs-2017"

使用遠端連線時，Visual Studio 會在C++遠端電腦上建立 Linux 專案。 如果它是實體機器、雲端中的 VM 或 WSL，則不重要。
若要建立專案，Visual Studio 將原始程式碼複製到遠端 Linux 電腦。 然後，程式碼會根據 Visual Studio 設定進行編譯。

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Visual Studio 2019 16.5 和更新版本也支援安全、聯邦資訊處理標準（FIPS）140-2 與 Linux 系統的相容密碼編譯連線，以進行遠端開發。 若要使用符合 FIPS 規範的連線，請改為遵循[設定 fips 相容的安全遠端 Linux 開發](set-up-fips-compliant-secure-remote-linux-development.md)中的步驟。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="set-up-the-ssh-server-on-the-remote-system"></a>在遠端系統上設定 SSH 伺服器

如果 ssh 尚未在您的 Linux 系統上設定並執行，請依照下列步驟進行安裝。 本文中的範例使用 Ubuntu 18.04 LTS 與 OpenSSH 伺服器版本7.6。 不過，所有使用最新的 OpenSSH 版本的散發版本的指示應該都相同。

1. 在 Linux 系統上，安裝並啟動 OpenSSH 伺服器：

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. 如果您想要在系統開機時自動啟動 ssh 伺服器，請使用 systemctl 啟用它：

   ```bash
   sudo systemctl enable ssh
   ```

## <a name="set-up-the-remote-connection"></a>設定遠端連線

1. 在 Visual Studio 中，選擇功能表列上的 [**工具 > 選項**] 以開啟 [**選項**] 對話方塊。 然後選取 [**跨平臺 > 連線管理員**] 以開啟 [連線管理員] 對話方塊。

   如果您之前未在 Visual Studio 中設定連接，則當您第一次建立專案時，Visual Studio 會為您開啟 [連接管理員] 對話方塊。

1. 在 [連線管理員] 對話方塊中，選擇 **[新增] 按鈕以**加入新的連接。

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

   您可以使用密碼或金鑰檔，以及用於驗證的複雜密碼。 在許多開發案例中，密碼驗證就已足夠，但金鑰檔案會更安全。 如果您已經有金鑰組，就可以重複使用它。 目前 Visual Studio 僅支援用於遠端連線的 RSA 和 DSA 金鑰。

1. 選擇 [連線 **]** 按鈕以嘗試連接到遠端電腦。

   如果連接成功，Visual Studio 會將 IntelliSense 設定為使用遠端標頭。 如需詳細資訊，請參閱[適用於遠端系統標頭的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

   如果連線失敗，將會以紅色標出需要變更的輸入方塊。

   ![連線管理員錯誤](media/settings_connectionmanagererror.png)

   如果您使用金鑰檔案進行驗證，請確定目的電腦的 SSH 伺服器正在執行且已正確設定。

   ::: moniker-end

   ::: moniker range="vs-2019"

## <a name="logging-for-remote-connections"></a>遠端連線的記錄

   您可以啟用記錄功能，以協助疑難排解連接問題。 在功能表列上，選取 [工具] [ **> 選項**]。 在 [**選項**] 對話方塊中，選取 [**跨平臺 > 記錄**]：

   ![遠端記錄](media/remote-logging-vs2019.png)

   記錄檔包含連線、傳送到遠端電腦 (其文字、結束代碼和執行時間) 的所有命令，以及從 Visual Studio 到殼層的所有輸出。 記錄適用於任何跨平台的 CMake 專案或 Visual Studio 中的 MSBuild 型 Linux 專案。

   您可以將輸出設定為移至檔案或 [輸出] 視窗中的 [**跨平臺記錄**] 窗格。 對於以 MSBuild 為基礎的 Linux 專案，傳送至遠端電腦的 MSBuild 命令不會路由傳送至**輸出視窗**，因為它們是以跨進程的形式發出。 相反地，它們會記錄到前置詞為 "msbuild_" 的檔案。

## <a name="command-line-utility-for-the-connection-manager"></a>連接管理員的命令列公用程式  

**Visual Studio 2019 16.5 版或更新**版本： ConnectionManager 是一個命令列公用程式，可管理 Visual Studio 以外的遠端開發連接。 這適用于布建新開發電腦的工作。 或者，您可以使用它來設定持續整合的 Visual Studio。 如需範例和 ConnectionManager 命令的完整參考，請參閱[connectionmanager 參考](connectionmanager-reference.md)。  

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="tcp-port-forwarding"></a>TCP 埠轉送

Visual Studio 的 Linux 支援相依于 TCP 埠轉送。 如果遠端系統上的 TCP 埠轉送已停用， **Rsync**和**gdbserver**會受到影響。 如果您受到此相依性的影響，您可以在開發人員社區上附議這項[建議票證](https://developercommunity.visualstudio.com/idea/840265/dont-rely-on-ssh-tcp-port-forwarding-for-c-remote.html)。

以 MSBuild 為基礎的 Linux 專案和 CMake 專案會使用 rsync，將[標頭從您的遠端系統複製到 Windows，供 IntelliSense 使用](configure-a-linux-project.md#remote_intellisense)。 當您無法啟用 TCP 埠轉送時，請停用自動下載遠端標頭。 若要停用它，請使用**工具 > 選項 > 跨平臺 > 連線管理員 > 遠端標頭 IntelliSense 管理員**。 如果遠端系統未啟用 TCP 埠轉送，當下載 IntelliSense 的遠端標頭開始時，您會看到此錯誤：

![標頭錯誤](media/port-forwarding-headers-error.png)

Visual Studio 的 CMake 支援也會使用 rsync，將來源檔案複製到遠端系統。 如果您無法啟用 TCP 埠轉送，您可以使用 sftp 做為遠端複製來源方法。 sftp 通常會比 rsync 慢，但不會相依于 TCP 埠轉送。 您可以使用 [ [CMake 設定編輯器](../build/cmakesettings-reference.md#additional-settings-for-cmake-linux-projects)] 中的 [ **remoteCopySourcesMethod** ] 屬性來管理遠端複製來源方法。 如果遠端系統上的 TCP 埠轉送已停用，當第一次叫用 rsync 時，您會在 [CMake 輸出] 視窗中看到錯誤。

![Rsync 錯誤](media/port-forwarding-copy-error.png)

gdbserver 可用於在內嵌裝置上進行偵錯工具。 如果您無法啟用 TCP 埠轉送，則必須在所有遠端偵錯程式案例中使用 gdb。 在遠端系統上的專案進行調試時，預設會使用 gdb。

## <a name="connect-to-wsl"></a>連線到 WSL

::: moniker-end

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
