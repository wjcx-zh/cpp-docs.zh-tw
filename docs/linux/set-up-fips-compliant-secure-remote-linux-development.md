---
title: 設定符合 FIPS 規範的安全遠端 Linux 開發
description: 如何在 Visual Studio 和 Linux 電腦之間建立符合 FIPS 的加密連接,以便進行遠端開發。
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "76520890"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>設定符合 FIPS 規範的安全遠端 Linux 開發

::: moniker range="<=vs-2017"

Visual Studio 2017 及更新版本支援 Linux。 符合 FIPS 的安全遠端 Linux 開發在 Visual Studio 2019 版本 16.5 及更高版本中提供。

::: moniker-end

::: moniker range="vs-2019"

聯邦資訊處理標準 (FIPS) 出版物 140-2 是美國政府加密模組的標準。 標準的實現由NIST驗證。 Windows[已驗證了對符合 FIPS 的加密模組的支援](/windows/security/threat-protection/fips-140-validation)。 在 Visual Studio 2019 版本 16.5 及更高版本中,您可以使用與 Linux 系統相容 FIPS 的安全加密連接進行遠端開發。

下面介紹如何在 Visual Studio 和遠端 Linux 系統之間設置符合 FIPS 的安全連接。 當您在可視化工作室中構建 CMake 或 MSBuild Linux 專案時,本指南適用。 本文是[連接到遠端 Linux 計算機](connect-to-your-remote-linux-computer.md)中的符合 FIPS 的連接指令的版本。

## <a name="prepare-a-fips-compliant-connection"></a>準備符合 FIPS 連線

在 Visual Studio 和遠端 Linux 系統之間使用符合 FIPS 的加密安全 ssh 連接需要進行一些準備。 對於 FIPS-140-2 合規性,Visual Studio 僅支援 RSA 密鑰。

本文中的範例使用 Ubuntu 18.04 LTS 與 OpenSSH 伺服器版本 7.6。 但是,對於使用中等較新版本的 OpenSSH 的任何發行版,說明應相同。

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>在遠端系統上設定 SSH 伺服器

1. Linux 系統上,安裝並啟動 OpenSSH 伺服器:

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. 如果您希望 ssh 伺服器在系統啟動時自動啟動,請使用系統 ctl 啟用它:

   ```bash
   sudo systemctl enable ssh
   ```

1. 打開 */etc/ssh/sshd_config*作為根。 編輯(或添加,如果它們不存在):以下行:

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > ssh-rsa 是唯一支援符合 FIPS 的主機密鑰演演演算法 VS。 aes-ctr\*演演演算法也符合 FIPS,但 Visual Studio 中的實現未獲批准。 ecdh-\*密鑰交換演演演算法符合 FIPS 標準,但 Visual Studio 不支援它們。

   您並不限於這些選項。 您可以將 ssh 設定為使用其他密碼、主機金鑰演演算法等。 您可能需要考慮的其他其他安全選項是`PermitRootLogin`與`PasswordAuthentication` `PermitEmptyPasswords` 。 關於詳細資訊,請參閱 sshd_config 或文章[SSH 伺服器設定](https://www.ssh.com/ssh/sshd_config)。

1. 儲存並關閉sshd_config後,重新啟動 ssh 伺服器以應用新設定:

   ```bash
   sudo service ssh restart
   ```

接下來,您將在 Windows 電腦上創建 RSA 金鑰對。 然後,您將公開金鑰複製到遠端 Linux 系統供 ssh 使用。

### <a name="to-create-and-use-an-rsa-key-file"></a>建立與使用 RSA 金鑰檔案

1. 在 Windows 電腦上,使用以下指令產生公共/私有 RSA 金鑰對:

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   該命令建立公開金鑰和私密金鑰。 預設情況下,鍵會儲存到*\\\\%USERPROFILE% .ssh id_rsa*與 *%USERPROFILE%\\\\.ssh id_rsa.pub*. (Powershell`$env:USERPROFILE`中,使用而不是 cmd`%USERPROFILE%`宏 )如果更改金鑰名稱,請使用後續步驟中的更改名稱。  我們建議您使用密碼來提高安全性。

1. 從 Windows 將公開金鑰複製到 Linux 電腦:

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. 在 Linux 系統上,將金鑰加入授權金鑰清單中,並確保檔案有正確的權限:

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. 現在,您可以測試新密鑰是否在 ssh 中工作。 使用它從 Windows 登入:

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

您已成功設定 ssh、創建和部署加密金鑰,並測試了連接。 現在,您已準備好設置可視化工作室連接。

## <a name="connect-to-the-remote-system-in-visual-studio"></a>連接到視覺化工作室中的遠端系統

1. 在可視化工作室中,在選單欄上選擇 **「工具>選項**」以打開 **「選項**」對話框。 然後選擇**跨平臺>連接管理器**以打開連接管理器對話方塊。

   如果您以前未在 Visual Studio 中設定連接,則首次生成專案時,Visual Studio 會為您打開連接管理器對話方塊。

1. 在"連接管理員"對話框中,選擇 **'添加**"按鈕以新增新連接。

   ![連線管理員](media/settings_connectionmanager.png)

   將顯示連線**到遠端系統「** 視窗」。

   ![連線到遠端系統](media/connect.png)

1. 在**連接遠端系統對話**框中,輸入遠端電腦的連接詳細資訊。

   | 項目 | 描述
   | ----- | ---
   | **主機名稱**           | 目標裝置的名稱或 IP 位址
   | **連接埠**                | 正在執行 SSH 服務的連接埠，一般是 22
   | **使用者名稱**           | 驗證使用者身分
   | **驗證類型** | 為符合 FIPS 的連線選擇私密金鑰
   | **私密金鑰檔**    | 為 SSH 連線所建立的私密金鑰檔案
   | **密碼**          | 與上面選取的私密金鑰搭配使用的複雜密碼

   將認證類型變更為**私密金鑰**。 在 **「私鑰檔**」 欄位中輸入私密金鑰的路徑。 您可以使用 **「瀏覽」** 按鈕來瀏覽到私密金鑰檔。 然後,在密碼欄位中輸入用於加密私鑰文件**密碼。**

1. 選擇 **「連線**」按鈕以嘗試連接到遠端電腦。

   如果連接成功,Visual Studio 將 IntelliSense 配置為使用遠端標頭。 如需詳細資訊，請參閱[適用於遠端系統標頭的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

   如果連線失敗，將會以紅色標出需要變更的輸入方塊。

   ![連線管理員錯誤](media/settings_connectionmanagererror.png)

   有關對連線進行故障排除的詳細資訊,請參閱[連接到遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)。

## <a name="command-line-utility-for-the-connection-manager"></a>連線管理員的命令列實用程式  

**Visual Studio 2019 版本 16.5 或更高版本**:ConnectionManager.exe 是一個命令列實用程式,用於管理 Visual Studio 外部的遠端開發連接。 它對於預配新開發計算機等任務很有用。 或者,您可以使用它設置 Visual Studio 進行持續整合。 有關範例與連接管理員指令的完整參考,請參閱[連線管理員參考](connectionmanager-reference.md)。  

## <a name="optional-enable-or-disable-fips-mode"></a>選擇選擇或關閉 FIPS 模式

可以在 Windows 中全域啟用 FIPS 模式。

1. 要啟用 FIPS 模式,請按**Windows+R**打開"執行"對話框,然後運行 gpedit.msc。

1. 展開**本地電腦策略>計算機配置> Windows 設置>本地策略>"安全設置**"並選擇 **"安全選項**"。

1. 在 **"策略**"下,選擇 **"系統加密:使用符合 FIPS 的演算法進行加密、哈希和簽名**",然後按**Enter**打開其對話方塊。

1. 在 **「本地安全設定」** 選項卡中,選擇 **「已啟用**」或 **「已禁用**」,然後選擇 **「確定」** 以儲存更改。

> [!WARNING]
> 啟用 FIPS 模式可能會導致某些應用程式意外中斷或行為異常。 有關詳細資訊,請參閱博客文章[為什麼我們不建議"FIPS 模式"了](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)。

## <a name="additional-resources"></a>其他資源

[關於 FIPS 140 驗證的微軟文件](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2:加密模組的安全要求](https://csrc.nist.gov/publications/detail/fips/140/2/final)(來自 NIST)

[加密演算法驗證程式:驗證說明](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes)(來自 NIST)

微軟博客文章,[為什麼我們不推薦"FIPS模式"了](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)

[SSH 伺服器設定](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>另請參閱

[設定 Linux 專案](configure-a-linux-project.md)\
[設定 Linux CMake 專案](cmake-linux-project.md)\
[連接到遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)\
[部署、執行及除錯 Linux 專案](deploy-run-and-debug-your-linux-project.md)\
[設定 CMake 偵錯工作階段](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
