---
title: 連線至 Visual Studio 中的目標 Linux 系統
description: 如何從 Visual Studio C++ 專案內連線至遠端 Linux 電腦或 WSL。
ms.date: 06/19/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 00d7facca2857efb0b8b43b5aaf38edce348a511
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861140"
---
# <a name="connect-to-your-target-linux-system-in-visual-studio"></a>連線至 Visual Studio 中的目標 Linux 系統

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range=">=vs-2017"

您可以設定 Linux 專案，以遠端電腦或適用於 Linux 的 Windows 子系統 (WSL) 為目標。 針對遠端電腦以及 Visual Studio 2017 上的 WSL，您需要設定連線。 

## <a name="connect-to-a-remote-linux-computer"></a>連線至遠端 Linux 電腦

針對遠端 Linux 系統 (VM 或實體機器) 建置 C++ Linux 專案時，Linux 程式碼會複製到您的遠端 Linux 電腦，然後根據 Visual Studio 設定編譯。

設定此遠端連線：

1. 第一次建置專案，或選取 [工具] > [選項]  手動建立新項目，並開啟 [跨平台] > [連線管理員]  節點，然後按一下 [新增]  按鈕。

   ![連線管理員](media/settings_connectionmanager.png)

   在任一情況下，都會顯示 [Connect to Remote System]\(連線到遠端系統)  視窗。

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

1. 按一下 [連線]  按鈕，嘗試連線到遠端電腦。 

   如果連線成功，Visual Studio 會開始將 IntelliSense 設定為使用遠端標頭。 如需詳細資訊，請參閱[適用於遠端系統標頭的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

   如果連線失敗，將會以紅色標出需要變更的輸入方塊。

   ![連線管理員錯誤](media/settings_connectionmanagererror.png)

   如果您使用金鑰檔案進行驗證，請確定目標電腦的 SSH 伺服器正在執行而且設定正確。

   ::: moniker-end

   ::: moniker range="vs-2019"

   移至 [工具] > [選項] > [跨平台] > [記錄]  來啟用記錄，以協助疑難排解連線問題：

   ![遠端記錄](media/remote-logging-vs2019.png)

   記錄檔包含連線、傳送到遠端電腦 (其文字、結束代碼和執行時間) 的所有命令，以及從 Visual Studio 到殼層的所有輸出。 記錄適用於任何跨平台的 CMake 專案或 Visual Studio 中的 MSBuild 型 Linux 專案。

   您可以設定輸出到檔案或 [輸出] 視窗中的 [跨平台記錄]  窗格。 對於 MSBuild 型 Linux 專案，MSBuild 發出到遠端電腦的命令不會路由傳送至 [輸出視窗]  ，因為它們是跨處理序發出的。 但是，它們會記錄到前置詞為 "msbuild_" 的檔案中。

   ::: moniker-end

## <a name="connect-to-wsl"></a>連線到 WSL

::: moniker range="vs-2017"

在 Visual Studio 2017 中，您可以使用與連線到遠端 Linux 電腦的相同步驟，連線到 WSL，如本文稍早所述。 使用 **localhost** 作為 [主機名稱]  。

::: moniker-end

::: moniker range="vs-2019"

在 Visual Studio 2019 16.1 版中，以 WSL 為目標時，不需要新增遠端連線或設定 SSH。 Linux 系統上只需要 gcc、gdb、make、rsync 及 zip。 Visual Studio 僅需要 rsync 及 zip 在第一次使用時，將標頭檔從 WSL 執行個體擷取到 Windows 檔案系統，就能用於 IntelliSense。 在 Visual Studio 2019 16.1 版中，WSL 支援是以 Windows 1809 版為基礎。 您可以執行更新版本的 Windows，但 Visual Studio 還不會利用新的 WSL 功能。

如果您的散發套件支援 apt，可以使用下列命令來安裝所需的套件：

```bash
sudo apt install g++ gdb make rsync zip
```

若要設定 WSL 的專案，請參閱[設定 Linux 專案](configure-a-linux-project.md)或[設定 Linux CMake 專案](cmake-linux-project.md)，端視您所擁有的專案類型而定。

::: moniker-end

## <a name="see-also"></a>另請參閱

[設定 Linux 專案](configure-a-linux-project.md)<br />
[設定 Linux CMake 專案](cmake-linux-project.md)<br />
[部署、執行及偵錯 Linux 專案](deploy-run-and-debug-your-linux-project.md)<br />




