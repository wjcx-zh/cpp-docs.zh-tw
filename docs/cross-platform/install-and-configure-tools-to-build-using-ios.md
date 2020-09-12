---
title: 安裝和設定工具以使用 iOS 進行建置
ms.date: 10/17/2019
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
ms.openlocfilehash: 26dea080f3d3f05885f348dcaf1c66a0db2a36b5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041987"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>安裝和設定工具以使用 iOS 進行建置

您可以使用 Visual Studio 搭配使用 **c + +** 工具的跨平臺行動裝置開發，來編輯、偵測 ios 程式碼，並將其部署至 ios 模擬器或 ios 裝置。 但是，由於授許可權制，必須在 Mac 上以遠端方式建立和執行程式碼。 若要使用 Visual Studio 建置並執行 iOS 應用程式，您必須在 Mac 上安裝及設定 [vcremote](https://www.npmjs.com/package/vcremote)遠端代理程式。 遠端代理程式會處理來自 Visual Studio 的建立要求，並在連接至 Mac 的 iOS 裝置或 Mac 中的 iOS 模擬器上執行應用程式。

> [!NOTE]
> 如需有關使用雲端裝載 Mac 服務 (而非使用 Mac) 的相關資訊，請參閱[設定 Visual Studio 以連線至雲端裝載的 Mac](/visualstudio/cross-platform/tools-for-cordova/tips-workarounds/host-a-mac-in-the-cloud?view=toolsforcordova-2017&preserve-view=true#configure-visual-studio-to-connect-to-your-cloud-hosted-mac) \(英文\)。 本指示是針對使用 Visual Studio Tools for Apache Cordova 進行建置。 若要使用以 c + + 建立的指示，請使用取代 `vcremote` `remotebuild` 。

當您安裝要使用 iOS 建立的工具之後，請參閱這篇文章，以瞭解如何在 Visual Studio 和您的 Mac 上快速設定和更新 iOS 開發的遠端代理程式。

## <a name="prerequisites"></a>必要條件

若要安裝和使用遠端代理程式來開發 iOS 的程式碼，您必須先具備這些必要條件：

- 執行 macOS Mojave 版本 10.14 或更新版本的 Mac 電腦

- [Apple ID](https://appleid.apple.com/)

- 使用中的 [Apple Developer Program](https://developer.apple.com/programs/) 帳戶

   您可以取得免費帳戶，其允許將應用程式側載到 iOS 裝置以進行測試，但無法進行散發。

- [Xcode](https://developer.apple.com/xcode/downloads/) 版本 10.2.1 或更新版本

   您可以從 App Store 下載 Xcode。

- Xcode 命令列工具

   若要安裝 Xcode 命令列工具，請在您的 Mac 上開啟終端機應用程式，並輸入下列命令：

   `xcode-select --install`

- 在 Xcode 中設為簽署身分識別的 Apple ID 帳戶用來簽署應用程式

   若要在 Xcode 中查看或設定簽署識別，請開啟 [Xcode] **** 功能表並選擇 [喜好設定] ****。 選取 [帳戶] **** 並選擇您的 Apple ID，然後選擇 [檢視詳細資料] **** 按鈕。 請參閱 [Add your Apple ID account](https://help.apple.com/xcode/mac/current/#/devaf282080a) (新增您的 Apple ID 帳戶) 以取得詳細說明。

   如需簽署需求的詳細資訊，請參閱 [What is app signing](https://help.apple.com/xcode/mac/current/#/dev3a05256b8) (什麼是應用程式簽署)。

- 如果您是使用 iOS 裝置進行開發，請在 Xcode 中為您的裝置設定佈建設定檔

   Xcode 會提供自動簽署，視需要為您建立簽署憑證。 如需 Xcode 自動簽署的詳細資訊，請參閱 [automatic signing](https://help.apple.com/xcode/mac/current/#/dev80cc24546) (自動簽署)。

   若您想要進行手動簽署，您需要為您的應用程式建立佈建設定檔。 如需建立佈建設定檔的詳細資訊，請參閱 [Create a development provisioning profile](https://help.apple.com/developer-account/#/devf2eb157f8) (建立開發佈建設定檔)。

- [Node.js](https://nodejs.org/) 版本12.14.1 和 npm 版本6.13。4

   在您的 Mac 上安裝 Node.js 的版本12.14.1。 如果您安裝 Node.js 套件，它應該會隨附 npm 版本6.13.4。 其他版本的 Node.js 和 npm 可能不支援遠端代理程式中使用的某些模組 `vcremote` ，這可能會導致 `vcremote` 安裝失敗。 建議您使用套件管理員（例如 [Node 版本管理員](https://nodejs.org/en/download/package-manager/#nvm)）來安裝 Node.js。 請避免使用命令 `sudo` 來安裝 Node.js，因為某些模組可能會在使用時無法安裝 `sudo` 。

## <a name="install-the-remote-agent-for-ios"></a><a name="Install"></a> 安裝 iOS 適用的遠端代理程式

當您安裝使用 c + + 工作負載的行動裝置開發時，Visual Studio 可以與 [vcremote](https://www.npmjs.com/package/vcremote)通訊，也就是在您的 Mac 上執行的遠端代理程式來傳送檔案、建立及執行您的 iOS 應用程式，以及傳送偵錯工具命令

安裝遠端代理程式之前，請確定您已滿足 [必要條件](#prerequisites) ，並已完成安裝 [使用 c + + 進行跨平臺行動開發](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#install-the-tools)的安裝步驟。

### <a name="to-download-and-install-the-remote-agent"></a><a name="DownloadInstall"></a> 若要下載及安裝遠端代理程式

- 從 Mac 上的終端機應用程式中，確認目前使用中的 Node.js 版本是所需的12.14.1 版本。 若要驗證版本，請執行下列命令：

  `node -v`
  
  如果不是正確的版本，您可能需要遵循必要條件中 Node.js 的安裝指示。 然後，重新開機 Node.js。

- 確認所需的 Node.js 正在使用中之後，請執行此命令，以在該 Node.js 版本下安裝 vcremote：

   `npm install -g --unsafe-perm vcremote`

   建議使用全域安裝 (**-g**) 參數，但非必要。 如果您未使用全域安裝參數，vcremote 會安裝在終端機應用程式中目前作用中的路徑下。

   在安裝期間， `vcremote` 會在您的 Mac 上安裝並啟用開發人員模式。 [Homebrew](https://brew.sh/) `vcremote-lib` 此外，也會安裝 Homebrew 和兩個 npm 套件 `vcremote-utils` 。 安裝完成時，針對已略過的選用相依性，您可以放心忽略相關的所有警告。

   > [!NOTE]
   > 若要安裝 Homebrew，您必須具備 sudo (系統管理員) 存取權。 如果您需要 `vcremote` 在不 sudo 的情況下安裝，可以在 usr/local 位置手動安裝 Homebrew，並將其 bin 資料夾新增至您的路徑。 如需詳細資訊，請參閱 [Homebrew 文件](https://github.com/Homebrew/homebrew/wiki/Installation)。 若要手動啟用開發人員模式，請在 Terminal 應用程式中輸入下列命令： `DevToolsSecurity -enable`

如果您已更新為新版 Visual Studio，也必須將遠端代理程式更新為目前版本。 若要更新遠端代理程式，請重複下載及安裝遠端代理程式的步驟。

## <a name="start-the-remote-agent"></a><a name="Start"></a> 啟動遠端代理程式

您必須為 Visual Studio 執行遠端代理程式，才能建置並執行您的 iOS 程式碼。 Visual Studio 必須搭配遠端代理程式才可進行通訊。 根據預設，遠端代理程式會以安全連線模式執行，其需要 PIN 碼與 Visual Studio 配對。

### <a name="to-start-the-remote-agent"></a><a name="RemoteAgentStartServer"></a> 若要啟動遠端代理程式

- 從 Mac 上的 Terminal 應用程式，輸入：

   `vcremote`

   此命令會啟動遠端代理程式，其預設組建目錄為 `~/vcremote` 。 如需其他組態選項，請參閱 [Configure the remote agent on the Mac](#ConfigureMac)。

當您第一次啟動代理程式，且每次建立新的用戶端憑證時，會提供您在 Visual Studio 中設定代理程式所需的資訊，包括主機名稱、埠和 PIN。

![使用 vcremote 產生安全 PIN 碼](../cross-platform/media/cppmdd-vcremote-generateclientcert.png "使用 vcremote 產生安全 PIN 碼")

如果您要使用主機名稱在 Visual Studio 中設定遠端代理程式，請使用主機名稱從 Windows ping 到 Mac 以確認可以存取。 如果不行，您可能要改用 IP 位址。

產生的 PIN 是供單次使用，並只在有限的期間內有效。 若您未在時效內將 Visual Studio 與遠端代理程式配對，則必須產生新的 PIN 碼。 如需詳細資訊，請參閱 [Generate a new security PIN](#GeneratePIN)。

您可以在不安全模式中使用遠端代理程式。 在不安全模式中，遠端代理程式可以在沒有 PIN 碼的情況下與 Visual Studio 配對。

#### <a name="to-disable-secured-connection-mode"></a>若要停用安全連線模式

- 若要在中停用安全的連接模式 `vcremote` ，請在 Mac 上的終端機應用程式中輸入下列命令：

   `vcremote --secure false`

#### <a name="to-enable-secured-connection-mode"></a>若要啟用安全連線模式

- 若要啟用安全連線模式，請輸入下列命令：

   `vcremote --secure true`

一旦啟動遠端代理程式，您便可以從 Visual Studio 加以使用，直到您將其停止為止。

#### <a name="to-stop-the-remote-agent"></a>若要停止遠端代理程式

- 在 [終端機] 視窗 `vcremote` 中執行，輸入**Control** + **C**。

## <a name="configure-the-remote-agent-in-visual-studio"></a><a name="ConfigureVS"></a> 在 Visual Studio 中設定遠端代理程式

若要從 Visual Studio 連接到遠端代理程式，您必須在 Visual Studio 選項中指定遠端組態。

### <a name="to-configure-the-remote-agent-from-visual-studio"></a>若要從 Visual Studio 設定遠端代理程式

1. 如果 Mac 上的代理程式尚未執行，請遵循 [啟動遠端代理程式](#Start)中的步驟。 您的 Mac 必須 `vcremote` 執行，才能讓 Visual Studio 成功配對、連接及建立您的專案。

1. 在您的 Mac 上，取得 Mac 主機名稱或 IP 位址。

   您可以在 Terminal 視窗中使用 **ifconfig** 命令取得 IP 位址。 請使用作用中的網路介面底下所列的網際網路位址。

1. 在 Visual Studio 功能表列上，選擇 [工具] ****、[選項] ****。

1. 展開 [選項] **** 對話方塊中的 [跨平台] ****、[C++] ****、[iOS] ****。

1. 在 [主機名稱] **** 和 [連接埠] **** 欄位中，輸入您啟動遠端代理程式時所指定的值。 主機名稱可能是您的 Mac DNS 名稱或 IP 位址。 預設連接埠是 3030。

   > [!NOTE]
   > 如果您無法使用主機名稱 ping 到 Mac，就需要使用 IP 位址。

1. 如果您是在預設的安全連線模式中使用遠端代理程式，請核取 [安全] **** 核取方塊，然後在 [Pin] **** 欄位中輸入遠端代理程式指定的 PIN 值。 如果您是在不安全的連線模式中使用遠端代理程式，請清除 [安全] **** 核取方塊，並將 [Pin] **** 欄位保留空白。

1. 若要啟用配對，請選擇 [配對] **** 。

   ![設定 iOS 組建的 vcremote 連接](../cross-platform/media/cppmdd-options-ios.png "設定 iOS 組建的 vcremote 連接")

   配對會一直保存，直到您變更主機名稱或連接埠為止。 如果您變更 [選項] **** 對話方塊中的主機名稱或連接埠，要復原變更時，請選擇 [還原] **** 按鈕以還原為先前的配對。

   如果未成功配對，請遵循 [Start the remote agent](#Start)中的步驟，確認遠端代理程式正在執行。 如果在產生遠端代理程式 PIN 後經過太久時間，請在 Mac 上進行 [Generate a new security PIN](#GeneratePIN) 中的步驟並再試一次。 如果您是使用 Mac 的主機名稱，請嘗試改用 [主機名稱] **** 欄位中的 IP 位址。

1. 更新 [遠端根目錄]**** 欄位中的資料夾名稱，以指定 Mac 主目錄 (*~*) 中遠端代理程式所使用的資料夾。 根據預設，遠端代理程式會使用 `/Users/<username>/vcremote` 做為遠端根目錄。

1. 選擇 [確定] **** 以儲存配對的遠端連線設定。

每次使用時，Visual Studio 都會使用相同的資訊來連接 Mac 上的遠端代理程式。 您不需再次配對 Visual Studio 與遠端代理程式，除非您在 Mac 上產生新的安全性憑證或其主機名稱或 IP 位址有所變更。

## <a name="generate-a-new-security-pin"></a><a name="GeneratePIN"></a> Generate a new security PIN

第一次啟動遠端代理程式時，產生的 PIN 碼是有時效性的—預設為 10 分鐘。 若您未在時效內將 Visual Studio 與遠端代理程式配對，則必須產生新的安全 PIN 碼。

### <a name="to-generate-a-new-pin"></a>產生新的 PIN 碼

1. 停止代理程式，或在 Mac 上開啟第二個 Terminal 應用程式視窗，以在其中輸入命令。

1. 在 Terminal 應用程式中，輸入下列命令：

   `vcremote generateClientCert`

   遠端代理程式會產生新的暫存 PIN。 若要使用新的 PIN 碼配對 Visual Studio，請重複 [在 Visual Studio 中設定遠端代理程式](#ConfigureVS)中的步驟。

## <a name="generate-a-new-server-certificate"></a><a name="GenerateCert"></a> 產生新的伺服器憑證

為了安全性目的，使用遠端代理程式配對出的 Visual Studio 伺服器憑證會與 Mac 的 IP 或主機名稱相關。 如果上述值有所變更，您就必須產生新的伺服器憑證，然後重新使用新值來設定 Visual Studio。

### <a name="to-generate-a-new-server-certificate"></a>若要產生新的伺服器憑證

1. 停止 `vcremote` 代理程式。

1. 在 Terminal 應用程式中，輸入下列命令：

   `vcremote resetServerCert`

1. 當提示確認時，請輸入 `Y`。

1. 在 Terminal 應用程式中，輸入下列命令：

   `vcremote generateClientCert`

   此命令會產生新的暫存 PIN。

1. 若要使用新的 PIN 碼配對 Visual Studio，請重複 [在 Visual Studio 中設定遠端代理程式](#ConfigureVS)中的步驟。

## <a name="configure-the-remote-agent-on-the-mac"></a><a name="ConfigureMac"></a> Configure the remote agent on the Mac

您可以使用各種命令列選項來設定遠端代理程式。 例如，您可以指定要接聽組建要求的通訊埠，並指定要在檔案系統上維護的最大組建數目。 預設上限為 10 個組建。 遠端代理程式會在關閉時，移除超出上限的組建。

### <a name="to-configure-the-remote-agent"></a>若要設定遠端代理程式

- 若要查看遠端代理程式命令的完整清單，請在 Terminal 應用程式中輸入：

   `vcremote --help`

- 若要停用安全模式並啟用簡單 HTTP 連線，請輸入：

   `vcremote --secure false`

   當您在 Visual Studio 中設定代理程式時使用了此選項，請取消核取 [安全]**** 核取方塊，並將 [PIN 碼]**** 欄位保留空白。

- 若要指定遠端代理程式檔的位置，請輸入：

   `vcremote --serverDir directory_path`

   其中， *directory_path* 是 Mac 將會存放記錄檔、組建與伺服器憑證的位置。 依預設，此位置為 `/Users/<username>/vcremote` 。 在這個位置中，組建會依組建編號排列。

- 若要使用背景處理序將 `stdout` 和 `stderr` 擷取至名為 server.log 的檔案，請輸入：

   `vcremote > server.log 2>&1 &`

   server.log 檔可協助進行組建問題的疑難排解。

- 若要使用組態檔 (而不是命令列參數) 執行代理程式，請輸入：

   `vcremote --config config_file_path`

   其中， *config_file_path* 是 JSON 格式的組態檔路徑。 啟動選項及其值不得包含破折號。

## <a name="troubleshoot-the-remote-agent"></a>針對遠端代理程式進行疑難排解

### <a name="debugging-on-an-ios-device"></a>在 iOS 裝置上進行偵錯

若在 iOS 裝置上進行偵錯無法正常運作，則可能是 [ideviceinstaller](https://github.com/libimobiledevice/ideviceinstaller) 工具本身的問題，該工具會用來和 iOS 裝置通訊。 這項工具通常會在安裝期間從 Homebrew 安裝 `vcremote` 。 請遵循以下步驟作為因應措施。

依序執行下列命令，以開啟終端機應用程式並更新及其相依性 `ideviceinstaller` ：

1. 確認 Homebrew 已完成更新

   `brew update`

1. 卸載 `libimobiledevice` 和 `usbmuxd`

   `brew uninstall --ignore-dependencies libimobiledevice`

   `brew uninstall --ignore-dependencies usbmuxd`

1. 安裝最新版本的 `libimobiledevice` 和 `usbmuxd`

   `brew install --HEAD usbmuxd`

   `brew unlink usbmuxd`

   `brew link usbmuxd`

   `brew install --HEAD libimobiledevice`

1. 卸載並重新安裝 `ideviceinstaller`

   `brew uninstall ideviceinstaller`

   `brew install ideviceinstaller`

`ideviceinstaller`嘗試列出安裝在裝置上的應用程式，確認可與裝置通訊：

`ideviceinstaller -l`

如果 `ideviceinstaller` 無法存取資料夾的錯誤 `/var/db/lockdown` ，請使用下列程式變更資料夾的許可權：

`sudo chmod 777 /var/db/lockdown`

如果 `ideviceinstaller` 可以與裝置通訊，請再次確認。

## <a name="see-also"></a>另請參閱

- [安裝 C++ 的跨平台行動裝置應用程式開發](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
