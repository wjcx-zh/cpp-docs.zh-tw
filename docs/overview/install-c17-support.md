---
title: 在 Visual Studio 中安裝 C11 和 C17 支援
description: 在 Visual Studio 中安裝適用于 C11 和 C17 的 Windows SDK 和 CRT 支援
ms.date: 09/11/2020
helpviewer_keywords:
- Install preview Windows SDK
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 86de38feb66ab0a057005140d22cf0dd3b03d4cf
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079074"
---
# <a name="install-c11-and-c17-support-in-visual-studio"></a>在 Visual Studio 中安裝 C11 和 C17 支援

::: moniker range="<=vs-2017"

C11 和 C17 標準的支援需要 Visual Studio 2019 16.8 版或更新版本。 若要查看此版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end

::: moniker range="vs-2019"

從 Visual Studio 2019 16.8 版開始，提供 C11 和 C17 標準的支援。 支援需要更新的通用 C 執行時間 (UCRT) 和最新的 Windows SDK 更新，才能與合格的預處理器 () 正常搭配運作 [`/Zc:preprocessor`](../build/reference/zc-preprocessor.md) 。

Windows SDK 版本會對應到 Windows 作業系統版本。 由於尚未有包含這些變更的 Windows 版本，因此您將需要 *Insider preview Windows SDK*。 這是 Windows SDK 的預覽版本，它會對應至 Windows 測試人員目前正在 *flighted*或測試的 windows 組建。 在您安裝 Insider Preview Windows 10 SDK 之後，設定為使用最新 Windows SDK 的 Visual Studio 專案將會使用 Insider preview。

## <a name="prerequisites"></a>必要條件

- 在您的電腦上安裝並執行 Visual Studio 2019 16.8 版 Preview 3 或更新版本。 在安裝中，包括使用 c + + 的桌面開發工作負載。 您可以從 [Visual Studio 預覽](https://visualstudio.microsoft.com/vs/preview/) 頁面下載最新的預覽版本。 如果尚未安裝 Visual Studio，請參閱 [Visual Studio 中的安裝 c + + 支援](../build/vscpp-step-0-installation.md) ，以取得安裝指示。

## <a name="step-1-sign-in-by-using-an-insider-microsoft-account"></a>步驟1：使用 Insider Microsoft 帳戶登入

任何人都可以建立免費的 [Microsoft 帳戶](https://signup.live.com/) ，然後加入宣告 Insider 計畫。 移至 [ [開發人員的 Windows 測試人員計畫](https://insider.windows.com/for-developers) ] 頁面，選擇 [ **註冊**]，然後登入。

註冊之後，您就可以選擇開始試驗 Insider 版本的 Windows。 下載並使用 Insider Windows 10 SDK 並不需要此步驟。 當您註冊 Windows 測試人員時，它不會自動選擇讓您的電腦下載新的 Windows 航班。

一旦您進入 [ **Windows 歡迎畫面 測試人員計畫** ] 頁面，就不需要選擇 [ **立即航班**]。 繼續進行下一個步驟，以下載 Insider Preview Windows 10 SDK。

## <a name="step-2-download-the-insider-preview-windows-10-sdk"></a>步驟2：下載 Insider Preview Windows 10 SDK

您可以從 [Windows Insider Preview 下載](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK) ] 頁面安裝 Insider preview Windows SDK。 如果您看到一則訊息，指出「您必須是 Windows 測試人員計畫的成員」，請確定您已登入。 使用您用於 Insider 計畫的相同 Microsoft 帳戶。 如果您看到一則訊息，指出「抱歉，找不到您要求的頁面」，請嘗試將 URL 中的地區設定變更為 *en-us*。

Insider 頁面宣稱需要使用 Windows 10 Insider Preview OS。 這僅適用于 Windows SDK 中包含的部分內容。 該內容可能依存于較舊版本 Windows 上沒有的新 Api。 不過，Windows 和通用 C 執行時間標頭可以安裝，而且可以在沒有 Insider OS 的情況下使用。

選擇 [ **取得 SDK Insider preview-組建 20211** (或更新版本) 以開始下載。 Windows SDK 的較新版本也可以運作。

## <a name="step-3-install-the-insider-preview-windows-10-sdk"></a>步驟3：安裝 Insider Preview Windows 10 SDK

Insider Preview Windows SDK 下載為檔案 *`.iso`* 。 在檔案總管中，開啟包含所下載檔案的資料夾。 掛接檔案 *`.iso`* ，然後執行 *`WinSDKSetup.exe`* 以開始安裝。

在 [ **指定位置** ] 頁面上，選取 [ **將 Windows 軟體開發套件安裝 \<version> 到這部電腦**]，然後選擇 **[下一步]**。 在 [ **Windows 套件隱私權** ] 頁面上，選取是否允許 Microsoft 收集 Windows 10 套件的見解，然後選擇 **[下一步]**。 選擇 [ **接受** ] 以接受授權合約。 在 [ **選取您要安裝的功能** ] 頁面上，只選取下列功能：  

- 適用于桌面應用程式的 Windows SDK 簽署工具

- UWP 受管理應用程式的 Windows SDK

- UWP c + + 應用程式的 Windows SDK

- 適用于 Desktop c + + x86 應用程式的 Windows SDK (如果您打算建立 x86) 

- 如果您打算針對 amd64 進行組建，Windows SDK 適用于 Desktop c + + amd64 應用程式 () 

- 適用于桌面 c + + arm 應用程式的 Windows SDK (如果您打算為 arm 建立) 

- 如果您打算針對 arm64 建立，則適用于 Desktop c + + arm64 應用程式的 Windows SDK () 

![Windows SDK 安裝程式的螢幕擷取畫面，其中顯示已選取要安裝的元件](media/c11-7-windows-sdk-installer-select-features.png)

選擇 [ **安裝** ] 以安裝選取的 SDK 元件。 SDK 需要幾分鐘的時間才能完成安裝。 完成時，開啟 Visual Studio。

## <a name="step-4-configuring-c11-or-c17-mode-in-visual-studio"></a>步驟4：在 Visual Studio 中設定 C11 或 C17 模式

在 Visual Studio 中，開啟新的或現有的 C 專案，然後開啟專案的 [ **屬性頁** ] 對話方塊。

將專案設定為使用 insider Preview Windows 10 SDK。 在 [設定**屬性**] 的  >  **[一般**] 頁面上，將 [ **Windows SDK 版本**] 屬性設定為**10.0 (最新安裝的版本) **或您安裝的特定預覽版本。

您也會看到新的選項： **C 語言標準**。 將此屬性設定為 **Iso C11 standard (`/std:c11`) ** 或 **iso C17 (2018) standard (`/std:c17`) **。  

![設定屬性 [一般] 頁面上 [屬性頁] 對話方塊的螢幕擷取畫面，其中顯示 [C 語言標準] 屬性下拉式清單選取專案為 ISO C 17](media/c11-9-project-property-page-c-language-standard.png)

當語言為 c + + 時，會使用 c + + 語言標準。 這是副檔名為時的預設值 *`.cpp`* 。 當語言為 C 時，會使用 C 語言標準版本。這是副檔名為時的預設值 *`.c`* 。 若要使用 C11 或 C17 來建立，請將您的原始程式碼放入檔案中 *`.c`* ，或將程式碼設定為以 C 編譯。您可以在**Configuration Properties**  >  **C/c + +**  >  **Advanced**頁面上設定專案的這個屬性。 將 [ **編譯為** ] 屬性設定為 [編譯為 C 程式碼]， ** (/tc) **。

恭喜，您已設定在 Visual Studio 2019 16.8 版 preview 3 中建立 C11 和 C17 程式碼所需的一切！

## <a name="see-also"></a>另請參閱

[`/std` (指定語言標準版本) ](../build/reference/std-specify-language-standard-version.md)

::: moniker-end
