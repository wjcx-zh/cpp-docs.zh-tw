---
title: 在 Visual Studio 中安裝 C++ 支援
description: 安裝 Visual C++ 的 Visual Studio 支援
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: d3018bef9254a8eab557057c035cde84310a2452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335358"
---
# <a name="install-c-support-in-visual-studio"></a>在 Visual Studio 中安裝 C++ 支援

如果您尚未下載並安裝 Visual Studio 和 Visual C++ 工具，以下是開始使用的方法。

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Visual Studio 2019 安裝

歡迎使用 Visual Studio 2019！ 在此版本中，您可以輕鬆選擇並安裝需要的功能。 因為降低了磁碟使用量下限，所以安裝快速，且對系統影響更小。

> [!NOTE]
> 本主題適用于 Windows 上的 Visual Studio 安裝。 [Visual Studio Code](https://code.visualstudio.com/)是輕量、跨平臺的開發環境，可在 Windows、Mac 和 Linux 系統上執行。 適用于 Visual Studio Code 擴充功能的 Microsoft [C/c + +](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)支援 IntelliSense、偵錯工具、程式碼格式設定、自動完成。 Visual Studio for Mac 不支援 Microsoft c + +，但是支援 .NET 語言和跨平臺開發。 如需安裝指示，請參閱[Install Visual Studio for Mac](/visualstudio/mac/installation/)。

是否想要深入了解此版本的其他新功能？ 請參閱 Visual Studio[版本](/visualstudio/releases/2019/release-notes/)資訊。

準備要安裝了嗎？ 我們將逐步引導完成安裝。

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>步驟 1：請確定您的電腦已準備好安裝 Visual Studio

在您開始安裝 Visual Studio 之前：

1. 檢查[系統需求](/visualstudio/releases/2019/system-requirements)。 這些需求可以幫助您了解電腦是否支援 Visual Studio 2019。

1. 套用最新的 Windows 更新。 這些更新可以確保您的電腦已具備最新的安全性更新，以及 Visual Studio 所需的系統元件。

1. 重新開機。 重新開機可以確保不會有任何擱置的安裝或更新會阻礙 Visual Studio 安裝。

1. 釋出空間。 透過執行 [磁碟清理] 應用程式之類的方式，將不必要的檔案及應用程式從 %SystemDrive% 移除。

如有並存執行舊版 Visual Studio 及 Visual Studio 2019 的相關問題，請參閱 [Visual Studio 2019 平台目標及相容性](/visualstudio/releases/2019/compatibility/)頁面。

### <a name="step-2---download-visual-studio"></a>步驟 2：下載 Visual Studio

接下來，請下載 Visual Studio 啟動載入器檔案。 若要這麼做，請依序選擇下列按鈕、您想要的 Visual Studio 版本、[儲存]**** 和 [開啟資料夾]****。

 > [!div class="button"]
 > [下載 Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>步驟 3：安裝 Visual Studio 安裝程式

執行啟動載入器檔案以安裝 Visual Studio 安裝程式。 這個新輕量型安裝程式包含安裝及自訂 Visual Studio 所需的全部內容。

1. 從您的 [下載]**** 資料夾中，按兩下符合或類似於下列其中一項檔案的啟動載入器：

   - **vs_community.exe** (適用於 Visual Studiofor Community)
   - **vs_professional.exe** (適用於 Visual Studio Professional)
   - **vs_enterprise.exe** (適用於 Visual Studio Enterprise)

   如果您收到使用者帳戶控制通知，請選擇 [是]****。

1. 我們將會要求您認可 Microsoft [授權條款](https://visualstudio.microsoft.com/license-terms/)和 Microsoft [隱私權聲明](https://privacy.microsoft.com/privacystatement)。 選擇 [繼續]****。

### <a name="step-4---choose-workloads"></a>步驟 4 - 選擇工作負載

安裝安裝程式之後，您可以藉由選取您想要的*工作負載*或功能集，使用它來自訂安裝。 方法如下。

1. 在 [安裝 Visual Studio]**** 畫面中找到您想要的工作負載。

   ![Visual Studio 2019：安裝工作負載](../get-started/media/vs-installer-workloads.png)

   如需核心 c + + 支援，請選擇「使用 c + + 進行桌面開發」工作負載。 它隨附預設核心編輯器，其中包括超過 20 種語言的基本程式碼編輯支援、能夠從任何資料夾開啟及編輯程式碼而不需要專案，以及整合的原始程式碼控制。

   其他工作負載支援其他類型的 c + + 開發。 例如，選擇 [通用 Windows 平臺開發] 工作負載，以建立使用 Microsoft Store Windows 執行階段的應用程式。 選擇 [使用 c + + 進行遊戲開發]，建立使用 DirectX、Unreal 和 Cocos2d 的遊戲。 選擇 [使用 c + + 進行 Linux 開發]，以 Linux 平臺為目標，包括 IoT 開發。

   [**安裝詳細資料**] 窗格會列出每個工作負載所安裝的內含和選用元件。 您可以選取或取消選取此清單中的選擇性元件。 例如，若要使用 Visual Studio 2017 或2015編譯器工具組來支援開發，請選擇 [MSVC v141] 或 [MSVC v140 選擇性元件]。 您可以新增 MFC 的支援、實驗性模組語言擴充功能、IncrediBuild 等等。

1. 選擇您想要的工作負載和選用元件之後，請選擇 [**安裝**]。

   接著會出現狀態畫面，顯示 Visual Studio 的安裝進度。

> [!TIP]
> 您可以在安裝後，隨時安裝一開始未安裝的工作負載或元件。 如果您已 Visual Studio 開啟，請移至 [**工具** > ] [**取得工具與功能 ...** ]，以開啟 [Visual Studio 安裝程式]。 或者，從 [開始] 功能表開啟 [Microsoft Visual Studio 安裝程式]****。 您可以在此選擇想要安裝的工作負載或元件。 然後，選擇 [修改]****。

### <a name="step-5---choose-individual-components-optional"></a>步驟 5：選取個別元件 (選擇性)

如果您不想使用 [工作負載] 功能來自訂您的 Visual Studio 安裝，或想要新增比工作負載安裝更多的元件，您可以從 [**個別元件**] 索引標籤安裝或新增個別元件來執行此動作。選擇您想要的內容，然後依照提示進行。

  ![Visual Studio 2019-安裝個別元件](../get-started/media/vs-installer-individual-components.png "安裝 Visual Studio 個別元件")

### <a name="step-6---install-language-packs-optional"></a>步驟 6：安裝語言套件 (選擇性)

根據預設，安裝程式會在第一次執行時，嘗試比對作業系統的語言。 若要以您選擇的語言安裝 Visual Studio，請選擇 Visual Studio 安裝程式的 [語言套件]**** 索引標籤，然後遵循提示作業。

  ![Visual Studio 2019-安裝語言套件](../get-started/media/vs-installer-language-packs.png "安裝 Visual Studio 語言套件")

#### <a name="change-the-installer-language-from-the-command-line"></a>從命令列變更安裝程式語言

另一個變更預設語言的方法，便是從命令列執行安裝程式。 例如，您可以使用下列命令來強制安裝程式以英文執行：`vs_installer.exe --locale en-US`。 安裝程式會在下一次執行時記住此設定。 安裝程式支援下列語言權杖：zh-cn、zh-tw、cs-cz、en-us、es-es、fr-fr、de-de、it-it、ja-jp、ko-kr、pl-pl、pt-br、ru-ru 和 tr-tr。

### <a name="step-7---change-the-installation-location-optional"></a>步驟 7 - 變更安裝位置 (選擇性)

您可以減少系統磁碟機上的 Visual Studio 安裝磁碟使用量。 您可以選擇將快取、共用元件、SDK 和工具下載至不同的磁碟機，並將 Visual Studio 保留在以最快速度執行它的磁碟機上。

  ![Visual Studio 2019-變更安裝位置](../get-started/media/vs-installer-installation-locations.png "變更安裝位置")

> [!IMPORTANT]
> 您只有在第一次安裝 Visual Studio 時才可以選取不同的磁碟機。 如已安裝 Visual Studio 並想要變更磁碟機，您必須解除安裝它，再重新安裝。

### <a name="step-8---start-developing"></a>步驟 8 - 開始開發

1. 在完成 Visual Studio 安裝後，請選擇 [啟動]**** 按鈕以開始使用 Visual Studio 來進行開發。

1. 在 [開始] 視窗中，選擇 [**建立新專案**]。

1. 在搜尋方塊中，輸入您想要建立的應用程式類型，以查看可用的範本清單。 範本清單取決於您在安裝期間所選擇的工作負載。 若要查看不同的範本，請選擇不同的工作負載。

   您也可以使用 [語言]**** 下拉式清單來篩選搜尋特定的程式設計語言。 您也可以使用 [平台]**** 清單和 [專案類型]**** 清單來篩選。

1. Visual Studio 會開啟您的新專案，而您已準備好撰寫程式碼！

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Visual Studio 2017 安裝

在 Visual Studio 2017 中，很容易就能選擇並安裝所需的功能。 因為降低了磁碟使用量下限，所以安裝快速，且對系統影響更小。

### <a name="prerequisites"></a>必要條件

- 寬頻網際網路連接。 Visual Studio 安裝程式可以下載數 gb 的資料。

- 執行 Microsoft Windows 7 或更新版本的電腦。 建議使用 Windows 10 以獲得最佳開發體驗。 安裝 Visual Studio 之前，請確定已將最新的更新套用到您的系統。

- 足夠的可用磁碟空間。 Visual Studio 需要至少 7 GB 的磁碟空間，而且如果安裝了許多通用選項，可能需要 50 GB 或更多。 我們建議您將它安裝在 C：磁片磁碟機上。

如需磁碟空間和作業系統需求的詳細資訊，請參閱[Visual Studio 產品系列系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs)。 安裝程式會報告您選取的選項需要多少磁碟空間。

### <a name="download-and-install"></a>下載並安裝

1. 下載適用于 Windows 的最新 Visual Studio 2017 安裝程式。

   > [!div class="nextstepaction"]
   > [安裝 Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Community Edition 是針對個別開發人員、課堂學習、學術研究和開放原始碼開發。 針對其他用途，請安裝 [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 或 [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

1. 尋找您已下載並執行的安裝程式檔案。 它可能會顯示在您的瀏覽器中，或者您可能會在 [下載] 資料夾中找到。 安裝程式需要系統管理員許可權才能執行。 您可能會看到 [**使用者帳戶控制**] 對話方塊，要求您授與許可權，讓安裝程式對您的系統進行變更;選擇 [**是]**。 如果您遇到問題，請在檔案瀏覽器中尋找下載的檔案，在安裝程式圖示上按一下滑鼠右鍵，然後從內容功能表選擇 [以**系統管理員身分執行**]。

   ![下載並安裝 Visual Studio 安裝程式](media/vscpp-concierge-run-installer.gif "下載並安裝 Visual Studio 安裝程式")

1. 安裝程式會顯示一份工作負載清單，而工作負載是特定開發區域的相關選項群組。 C + + 的支援現在是選擇性工作負載的一部分，預設不會安裝。

   ![使用 c + + 的桌面開發工作負載](media/desktop-development-with-cpp.png "使用 C++ 的桌面開發")

   針對 c + +，選取 [**使用 c + + 進行桌面開發**] 工作負載，然後選擇 [**安裝**]

   ![安裝使用 c + + 的桌面開發工作負載](media/vscpp-concierge-choose-workload.gif "安裝使用 c + + 的桌面開發工作負載")

1. 當安裝完成時，選擇 [**啟動**] 按鈕以啟動 Visual Studio。

   第一次執行 Visual Studio 時，系統會要求您使用 Microsoft 帳戶登入。 如果您沒有帳戶，可以免費建立一個。 您也必須選擇主題。 別擔心，如果您想要的話，可以稍後再變更。

   當您第一次執行時，可能需要 Visual Studio 幾分鐘的時間才能開始使用。 以下是快速時間的樣子：

   ![Visual Studio 2017 登入](media/vscpp-quickstart-first-run.gif "Visual Studio 2017 登入")

   當您再次執行時，Visual Studio 的啟動速度更快。

1. 當 Visual Studio 開啟時，請檢查標題列中的旗標圖示是否反白顯示：

   ![Visual Studio 2017 通知旗標](media/vscpp-first-start-page-flag.png "Visual Studio 2017 通知旗標")

   如果反白顯示，請選取它以開啟 [**通知**] 視窗。 如果 Visual Studio 有任何可用的更新，建議您立即安裝。 安裝完成後，請重新開機 Visual Studio。

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Visual Studio 2015 安裝

若要安裝 Visual Studio 2015，請前往[下載舊版 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)。 執行安裝程式，並選擇 [自訂安裝]****，然後選擇 C++ 元件。 若要將 c + + 支援新增至現有的 Visual Studio 2015 安裝，請按一下 Windows [開始] 按鈕，然後輸入 [新增] [**移除程式**]。 從 [結果] 清單中開啟程式，然後在已安裝的程式清單中尋找您的 Visual Studio 2015 安裝。 按兩下該檔案，然後選擇 [**修改**]，然後選取要安裝的 Visual C++ 元件。

一般來說，即使需要使用 Visual Studio 2015 編譯器，編譯您的程式碼，也都非常建議您使用 Visual Studio 2017。 如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](../porting/use-native-multi-targeting.md)。

::: moniker-end

當 Visual Studio 執行時，您就可以繼續進行下一個步驟。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [建立 c + + 專案](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
