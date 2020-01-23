---
title: 設定 FIPS 相容的安全遠端 Linux 開發
description: 如何設定 Visual Studio 與 Linux 電腦之間符合 FIPS 規範的密碼編譯連線，以進行遠端開發。
ms.date: 01/17/2020
ms.openlocfilehash: 9a0e87f4ddf69bf489b52d4f83934d3279f2d085
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520890"
---
# <a name="set-up-fips-compliant-secure-remote-linux-development"></a>設定 FIPS 相容的安全遠端 Linux 開發

::: moniker range="<=vs-2017"

Visual Studio 2017 及更新版本支援 Linux。 Visual Studio 2019 16.5 版和更新版本中提供 FIPS 相容的安全遠端 Linux 開發。

::: moniker-end

::: moniker range="vs-2019"

聯邦資訊處理標準（FIPS）發行集140-2 是密碼編譯模組的美國政府標準。 標準的執行是由 NIST 進行驗證。 Windows 已[驗證支援 FIPS 相容的密碼編譯模組](/windows/security/threat-protection/fips-140-validation)。 在 Visual Studio 2019 16.5 版和更新版本中，您可以對 Linux 系統使用安全且符合 FIPS 標準的密碼編譯連線，以進行遠端開發。

以下說明如何在 Visual Studio 與您的遠端 Linux 系統之間設定安全、FIPS 相容的連接。 本指南適用于在 Visual Studio 中建立 CMake 或 MSBuild Linux 專案的情況。 這篇文章是連線[到您的遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)時，與 FIPS 相容的連線指示版本。

## <a name="prepare-a-fips-compliant-connection"></a>準備符合 FIPS 規範的連線

需要進行一些準備，才能在 Visual Studio 與您的遠端 Linux 系統之間使用符合 FIPS 規範、密碼編譯安全的 ssh 連線。 針對 FIPS-140-2 合規性，Visual Studio 只支援 RSA 金鑰。

本文中的範例使用 Ubuntu 18.04 LTS 與 OpenSSH 伺服器版本7.6。 不過，所有使用最新的 OpenSSH 版本的散發版本的指示應該都相同。

### <a name="to-set-up-the-ssh-server-on-the-remote-system"></a>在遠端系統上設定 SSH 伺服器

1. 在 Linux 系統上，安裝並啟動 OpenSSH 伺服器：

   ```bash
   sudo apt install openssh-server
   sudo service ssh start
   ```

1. 如果您想要在系統開機時自動啟動 ssh 伺服器，請使用 systemctl 啟用它：

   ```bash
   sudo systemctl enable ssh
   ```

1. 以 root 身分開啟*到/etc/ssh/sshd_config* 。 編輯（如果不存在，則新增）下列幾行：

   ```config
   Ciphers aes256-cbc,aes192-cbc,aes128-cbc,3des-cbc
   HostKeyAlgorithms ssh-rsa
   KexAlgorithms diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1
   MACs hmac-sha2-256,hmac-sha1
   ```

   > [!NOTE]
   > ssh-rsa 是唯一符合 FIPS 規範的主機金鑰演算法與支援。 Aes\*ctr 演算法也符合 FIPS 標準，但不會核准 Visual Studio 中的執行。 Ecdh\* 金鑰交換演算法符合 FIPS 規範，但 Visual Studio 不支援它們。

   您不受限於這些選項。 您可以設定 ssh 使用額外的密碼、主機金鑰演算法等等。 您可能想要考慮的一些其他相關安全性選項是 `PermitRootLogin`、`PasswordAuthentication`和 `PermitEmptyPasswords`。 如需詳細資訊，請參閱 sshd_config 的手冊頁面或[SSH 伺服器](https://www.ssh.com/ssh/sshd_config)設定一文。

1. 儲存和關閉 sshd_config 之後，請重新開機 ssh 伺服器以套用新的設定：

   ```bash
   sudo service ssh restart
   ```

接下來，您將在 Windows 電腦上建立 RSA 金鑰組。 接著，您會將公開金鑰複製到遠端 Linux 系統，以供 ssh 使用。

### <a name="to-create-and-use-an-rsa-key-file"></a>建立和使用 RSA 金鑰檔案

1. 在 Windows 電腦上，使用下列命令來產生公開/私用 RSA 金鑰組：

   ```cmd
   ssh-keygen -t rsa -b 4096
   ```

   命令會建立公開金鑰和私密金鑰。 根據預設，金鑰會儲存到 *% userprofile%\\. ssh\\id_rsa*和 *% userprofile%\\. ssh\\id_rsa pub*。 （在 Powershell 中，使用 `$env:USERPROFILE`，而不是 cmd 宏 `%USERPROFILE%`）如果您變更索引鍵名稱，請在後續的步驟中使用變更的名稱。  我們建議您使用複雜密碼來提高安全性。

1. 從 Windows，將公開金鑰複製到 Linux 電腦：

   ```cmd
   scp %USERPROFILE%\.ssh\id_rsa.pub user@hostname:
   ```

1. 在 Linux 系統上，將金鑰新增至授權金鑰的清單，並確定檔案具有正確的許可權：

   ```bash
   cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

1. 現在，您可以測試以查看新的金鑰是否可在 ssh 中運作。 使用它從 Windows 登入：

    ```cmd
    ssh -i %USERPROFILE%\.ssh\id_rsa user@hostname
    ```

您已成功設定 ssh、已建立和部署的加密金鑰，並已測試您的連接。 現在您已準備好設定 Visual Studio 連線。

## <a name="connect-to-the-remote-system-in-visual-studio"></a>連接到 Visual Studio 中的遠端系統

1. 在 Visual Studio 中，選擇功能表列上的 [**工具 > 選項**] 以開啟 [**選項**] 對話方塊。 然後選取 [**跨平臺 > 連線管理員**] 以開啟 [連線管理員] 對話方塊。

   如果您之前未在 Visual Studio 中設定連接，則當您第一次建立專案時，Visual Studio 會為您開啟 [連接管理員] 對話方塊。

1. 在 [連線管理員] 對話方塊中，選擇 **[新增] 按鈕以**加入新的連接。

   ![連線管理員](media/settings_connectionmanager.png)

   [**連接到遠端系統**] 視窗隨即顯示。

   ![連線到遠端系統](media/connect.png)

1. 在 [**連接到遠端系統**] 對話方塊中，輸入遠端電腦的連線詳細資料。

   | 進入 | 描述
   | ----- | ---
   | **主機名稱**           | 目標裝置的名稱或 IP 位址
   | **連接埠**                | 正在執行 SSH 服務的連接埠，一般是 22
   | **使用者名稱**           | 驗證使用者身分
   | **驗證類型** | 為符合 FIPS 規範的連線選擇私密金鑰
   | **私密金鑰檔**    | 為 SSH 連線所建立的私密金鑰檔案
   | **複雜密碼**          | 與上面選取的私密金鑰搭配使用的複雜密碼

   將 [驗證類型] 變更為 [**私密金鑰**]。 在 [**私密金鑰**檔案] 欄位中輸入您的私密金鑰的路徑。 您可以使用 [**流覽]** 按鈕，改為流覽至您的私密金鑰檔案。 然後，在 [複雜**密碼**] 欄位中輸入用來加密私密金鑰檔案的複雜密碼。

1. 選擇 [連線 **]** 按鈕以嘗試連接到遠端電腦。

   如果連接成功，Visual Studio 會將 IntelliSense 設定為使用遠端標頭。 如需詳細資訊，請參閱[適用於遠端系統標頭的 IntelliSense](configure-a-linux-project.md#remote_intellisense)。

   如果連線失敗，將會以紅色標出需要變更的輸入方塊。

   ![連線管理員錯誤](media/settings_connectionmanagererror.png)

   如需疑難排解連線的詳細資訊，請參閱[連接到您的遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)。

## <a name="command-line-utility-for-the-connection-manager"></a>連接管理員的命令列公用程式  

**Visual Studio 2019 16.5 版或更新**版本： ConnectionManager 是一個命令列公用程式，可管理 Visual Studio 以外的遠端開發連接。 這適用于布建新開發電腦的工作。 或者，您可以使用它來設定持續整合的 Visual Studio。 如需範例和 ConnectionManager 命令的完整參考，請參閱[connectionmanager 參考](connectionmanager-reference.md)。  

## <a name="optional-enable-or-disable-fips-mode"></a>選擇性：啟用或停用 FIPS 模式

在 Windows 中，您可以全域啟用 FIPS 模式。

1. 若要啟用 FIPS 模式，請按**Windows + R**以開啟 [執行] 對話方塊，然後執行 gpedit.msc。

1. 展開 本機**電腦原則 > 電腦設定 > Windows 設定 > 安全性設定 > 本機原則**，然後選取 **安全性選項**

1. 在 [**原則**] 底下，選取 [**系統密碼編譯：使用 FIPS 相容演算法進行加密、雜湊和簽署**]，然後按**enter**鍵以開啟其對話方塊。

1. 在 [**本機安全性設定**] 索引標籤中，選取 [**已啟用**] 或 [**已停用**]，然後選擇 **[確定]** 儲存變更。

> [!WARNING]
> 啟用 FIPS 模式可能會導致某些應用程式意外中斷或行為。 如需詳細資訊，請參閱 blog 文章[為什麼我們不建議「FIPS 模式](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)」。

## <a name="additional-resources"></a>其他資源

[關於 FIPS 140 驗證的 Microsoft 檔](/windows/security/threat-protection/fips-140-validation)

[FIPS 140-2：密碼編譯模組的安全性需求](https://csrc.nist.gov/publications/detail/fips/140/2/final)（來自 NIST）

[密碼編譯演算法驗證程式：驗證注意事項](https://csrc.nist.gov/projects/cryptographic-algorithm-validation-program/Validation-Notes)（來自 NIST）

Microsoft blog 文章，說明[為什麼我們不建議「FIPS 模式](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/why-we-8217-re-not-recommending-8220-fips-mode-8221-anymore/ba-p/701037)」

[SSH 伺服器設定](https://www.ssh.com/ssh/sshd_config)

## <a name="see-also"></a>請參閱

[設定 Linux 專案](configure-a-linux-project.md)\
[設定 Linux CMake 專案](cmake-linux-project.md)\
[連接到您的遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)\
[部署、執行及偵錯工具您的 Linux 專案](deploy-run-and-debug-your-linux-project.md)\
[設定 CMake 偵錯工作階段](../build/configure-cmake-debugging-sessions.md)

::: moniker-end
