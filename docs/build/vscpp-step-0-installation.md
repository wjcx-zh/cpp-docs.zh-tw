---
title: 在 Visual Studio 中安裝 C++ 支援
description: 安裝 Visual Studio 支援視覺效果C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 2c2bed4063194bdc3c0f3fbc405be6bf9a4031e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315115"
---
# <a name="install-c-support-in-visual-studio"></a>在 Visual Studio 中安裝 C++ 支援

如果您還沒有下載並安裝 Visual Studio 和視覺效果C++工具，這裡的 如何開始使用。

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Visual Studio 2019 安裝

歡迎使用 Visual Studio 2019！ 在此版本中，您可以輕鬆選擇並安裝需要的功能。 因為降低了磁碟使用量下限，所以安裝快速，且對系統影響更小。

> [!NOTE]
> 本主題適用於在 Windows 上的 Visual Studio 的安裝。 [Visual Studio Code](https://code.visualstudio.com/)是一種輕量型、 跨平台的開發環境，在 Windows、 Mac 和 Linux 系統上執行。 Microsoft [C /C++適用於 Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)延伸模組支援 IntelliSense、 偵錯程式碼格式設定，自動完成。 Visual Studio for Mac 不支援 Microsoft C++，但可支援.NET 語言和跨平台開發。 如需安裝指示，請參閱[安裝 Visual Studio for Mac](/visualstudio/mac/installation/)。

是否想要深入了解此版本的其他新功能？ 請參閱 Visual Studio[版本資訊](/visualstudio/releases/2019/release-notes/)。

準備要安裝了嗎？ 我們將逐步引導完成安裝。

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>步驟 1：請確定您的電腦已準備好安裝 Visual Studio

在您開始安裝 Visual Studio 之前：

1. 檢查[系統需求](/visualstudio/releases/2019/system-requirements)。 這些需求可以幫助您了解電腦是否支援 Visual Studio 2019。

1. 套用最新的 Windows 更新。 這些更新可以確保您的電腦已具備最新的安全性更新，以及 Visual Studio 所需的系統元件。

1. 重新開機。 重新開機可以確保不會有任何擱置的安裝或更新會阻礙 Visual Studio 安裝。

1. 釋出空間。 透過執行 [磁碟清理] 應用程式之類的方式，將不必要的檔案及應用程式從 %SystemDrive% 移除。

如有並存執行舊版 Visual Studio 及 Visual Studio 2019 的相關問題，請參閱 [Visual Studio 2019 平台目標及相容性](/visualstudio/releases/2019/compatibility/)頁面。

### <a name="step-2---download-visual-studio"></a>步驟 2：下載 Visual Studio

接下來，請下載 Visual Studio 啟動載入器檔案。 若要這麼做，請依序選擇下列按鈕、您想要的 Visual Studio 版本、[儲存] 和 [開啟資料夾]。

 > [!div class="button"]
 > [下載 Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>步驟 3：安裝 Visual Studio 安裝程式

執行啟動載入器檔案以安裝 Visual Studio 安裝程式。 這個新輕量型安裝程式包含安裝及自訂 Visual Studio 所需的全部內容。

1. 從您的 [下載] 資料夾中，按兩下符合或類似於下列其中一項檔案的啟動載入器：

   * **vs_community.exe** (適用於 Visual Studiofor Community)
   * **vs_professional.exe** (適用於 Visual Studio Professional)
   * **vs_enterprise.exe** (適用於 Visual Studio Enterprise)

   如果您收到使用者帳戶控制通知，請選擇 [是]。

1. 我們將會要求您認可 Microsoft [授權條款](https://visualstudio.microsoft.com/license-terms/)和 Microsoft [隱私權聲明](https://privacy.microsoft.com/privacystatement)。 選擇 [繼續]。

### <a name="step-4---choose-workloads"></a>步驟 4 - 選擇工作負載

安裝完畢之後，您可用它來選取自訂安裝*工作負載*，或功能集，您想要的。 方式如下：

1. 在 [安裝 Visual Studio] 畫面中找到您想要的工作負載。

   ![Visual Studio 2019：安裝工作負載](../get-started/media/vs-installer-workloads.png)

   CoreC++支援，請選擇 「 使用桌面開發C++「 工作負載。 它隨附預設核心編輯器，其中包括超過 20 種語言的基本程式碼編輯支援、能夠從任何資料夾開啟及編輯程式碼而不需要專案，以及整合的原始程式碼控制。

   其他工作負載都支援其他類型的C++開發。 例如，選擇建立 Windows 執行階段用於 Microsoft Store 的應用程式的 「 通用 Windows 平台開發 」 工作負載。 選擇 「 遊戲開發使用C++"來建立使用 DirectX、 Unreal 及 Cocos2d 的遊戲。 選擇 「 使用的 Linux 開發C++「 目標 Linux 平台，包括 IoT 開發。

   **安裝詳細資料**窗格會列出安裝的每個工作負載的包含和選擇性元件。 您可以選取或取消選取這份清單中的選用元件。 例如，如果使用來支援開發的 Visual Studio 2017 或 2015年編譯器工具組，選擇 MSVC v141 或 MSVC v140 選用元件。 您可以加入支援 MFC、 實驗性模組語言延伸模組、 IncrediBuild，等等。

1. 您選擇的工作負載和您想要的選用元件之後，請選擇**安裝**。

    接著會出現狀態畫面，顯示 Visual Studio 的安裝進度。

> [!TIP]
> 您可以在安裝後，隨時安裝一開始未安裝的工作負載或元件。 如果您已開啟 Visual Studio，請移至 [工具] > [Get Tools and Features] (取得工具和功能)，以開啟 Visual Studio 安裝程式。 或者，從 [開始] 功能表開啟 [Microsoft Visual Studio 安裝程式]。 您可以在此選擇想要安裝的工作負載或元件。 然後，選擇 [修改]。

## <a name="step-5---choose-individual-components-optional"></a>步驟 5：選取個別元件 (選擇性)

如果您不想要使用工作負載功能來自訂您的 Visual Studio 安裝，或您想要新增比工作負載所安裝元件的更多元件，您可以從 [個別元件] 索引標籤安裝或新增個別的元件來完成此作業。選擇您想要的項目，然後遵循提示作業。

  ![Visual Studio 2019 - 安裝個別元件](../get-started/media/vs-installer-individual-components.png "安裝 Visual Studio 的個別元件")

## <a name="step-6---install-language-packs-optional"></a>步驟 6：安裝語言套件 (選擇性)

根據預設，安裝程式會在第一次執行時，嘗試比對作業系統的語言。 若要以您選擇的語言安裝 Visual Studio，請選擇 Visual Studio 安裝程式的 [語言套件] 索引標籤，然後遵循提示作業。

  ![Visual Studio 2019 - 安裝語言套件](../get-started/media/vs-installer-language-packs.png "安裝 Visual Studio 語言套件")

### <a name="change-the-installer-language-from-the-command-line"></a>從命令列變更安裝程式語言

另一個變更預設語言的方法，便是從命令列執行安裝程式。 例如，您可以使用下列命令來強制安裝程式以英文執行：`vs_installer.exe --locale en-US`。 下一次執行時，安裝程式將會記住這項設定。 安裝程式支援下列語言權杖：zh-cn、zh-tw、cs-cz、en-us、es-es、fr-fr、de-de、it-it、ja-jp、ko-kr、pl-pl、pt-br、ru-ru 和 tr-tr。

### <a name="step-7---change-the-installation-location-optional"></a>步驟 7 - 變更安裝位置 (選擇性)

您可以減少系統磁碟機上的 Visual Studio 安裝磁碟使用量。 您可以選擇將快取、共用元件、SDK 和工具下載至不同的磁碟機，並將 Visual Studio 保留在以最快速度執行它的磁碟機上。

  ![Visual Studio 2019 - 變更安裝位置](../get-started/media/vs-installer-installation-locations.png "變更安裝位置")

> [!IMPORTANT]
> 您只有在第一次安裝 Visual Studio 時才可以選取不同的磁碟機。 如已安裝 Visual Studio 並想要變更磁碟機，您必須解除安裝它，再重新安裝。

## <a name="step-8---start-developing"></a>步驟 8 - 開始開發

1. 在完成 Visual Studio 安裝後，請選擇 [啟動] 按鈕以開始使用 Visual Studio 來進行開發。

1. 在開始視窗中，選擇 [建立新專案]。

1. 在搜尋方塊中，輸入您想要建立的應用程式類型，以查看可用的範本清單。 範本清單取決於您在安裝期間所選擇的工作負載。 若要查看不同的範本，請選擇不同的工作負載。

   您也可以使用 [語言] 下拉式清單來篩選搜尋特定的程式設計語言。 您也可以使用 [平台] 清單和 [專案類型] 清單篩選。

1. Visual Studio 會開啟您的新專案，而您已準備好撰寫程式碼！

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Visual Studio 2017 安裝

在 Visual Studio 2017 中，很容易選擇並安裝您所需的功能。 因為降低了磁碟使用量下限，所以安裝快速，且對系統影響更小。

### <a name="prerequisites"></a>必要條件

- 寬頻網際網路連線。 Visual Studio 安裝程式可以下載好幾 gb 的資料。

- 執行 Microsoft Windows 7 或更新版本的電腦。 我們建議的最佳開發體驗的 Windows 10。 請確定您安裝 Visual Studio 之前，將最新的更新會套用到您的系統。

- 足夠的可用磁碟空間。 Visual Studio 至少需要 7 GB 的磁碟空間，而可能需要 50 GB 或更多如果安裝了許多常見的選項。 我們建議您將它安裝在您的 c： 磁碟機。

如需磁碟空間和作業系統需求的詳細資訊，請參閱[Visual Studio 產品系列系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs)。 安裝程式會報告您選取的選項需要多少磁碟空間。

### <a name="download-and-install"></a>下載並安裝

1. 下載最新的 Visual Studio 2017 安裝程式的 Windows。

   > [!div class="nextstepaction"]
   > [安裝 Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Community Edition 是針對個別開發人員、課堂學習、學術研究和開放原始碼開發。 針對其他用途，請安裝 [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 或 [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

1. 尋找您已下載並執行它的安裝程式檔案。 它可能會顯示在瀏覽器中，或您可能會發現您的 [下載] 資料夾中。 安裝程式需要系統管理員權限，才能執行。 您可能會看到**使用者帳戶控制**詢問是否要授與權限，讓安裝程式對您的系統進行變更; 選擇的對話方塊**是**。 如果您遇到問題，請在檔案總管中尋找下載的檔案，以滑鼠右鍵按一下 [安裝程式] 圖示，然後選擇**系統管理員身分執行**從內容功能表。

   ![下載並安裝 Visual Studio Installer](media/vscpp-concierge-run-installer.gif "下載並安裝 Visual Studio 安裝程式")

1. 安裝程式會顯示一份工作負載清單，而工作負載是特定開發區域的相關選項群組。 支援C++現在是選擇性的工作負載，並未預設安裝的一部分。

   ![使用的桌面開發C++工作負載](media/desktop-development-with-cpp.png "使用的桌面開發C++")

   針對C++，選取**使用的桌面開發C++** 工作負載，然後選擇**安裝**。

   ![安裝使用的桌面開發C++工作負載](media/vscpp-concierge-choose-workload.gif "安裝使用的桌面開發C++工作負載")

1. 當安裝完成時，選擇**啟動**按鈕來啟動 Visual Studio。

   第一次執行 Visual Studio 中，系統會詢問的 Microsoft 帳戶登入。 如果您沒有帳戶，您可以免費建立一個。 您也必須選擇一個佈景主題。 別擔心，您可以將它變更稍後如果您想要。

   可能需要 Visual Studio 幾分鐘，您就準備好使用您在執行第一次。 以下是看起來像是快速縮時攝影外：

   ![登入的 visual Studio 2017](media/vscpp-quickstart-first-run.gif "登入的 Visual Studio 2017")

   當您一次執行時，visual Studio 的啟動速度更快。

1. Visual Studio 開啟時，請查看標題列中的旗標圖示會反白顯示：

   ![Visual Studio 2017 通知 旗標](media/vscpp-first-start-page-flag.png "Visual Studio 2017 的通知旗標")

   如果會反白顯示，請選取它以開啟**通知**視窗。 如果有適用於 Visual Studio 的任何更新，我們建議您立即安裝它們。 安裝完成之後，重新啟動 Visual Studio。

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Visual Studio 2015 安裝

若要安裝 Visual Studio 2015，請前往[下載舊版 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)。 執行安裝程式，並選擇 [自訂安裝]，然後選擇 C++ 元件。 若要新增C++支援新增至現有的 Visual Studio 2015 安裝，請按一下 Windows [開始] 按鈕並鍵入**新增或移除程式**。 從結果清單中開啟的程式，然後尋找 Visual Studio 2015 安裝在已安裝的程式清單中。 連按兩下，然後選擇**修改**，然後選取視覺效果C++若要安裝的元件。

一般來說，即使需要使用 Visual Studio 2015 編譯器，編譯您的程式碼，也都非常建議您使用 Visual Studio 2017。 如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](../porting/use-native-multi-targeting.md)。

::: moniker-end

當 Visual Studio 執行時，您即可繼續下一個步驟。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [建立C++專案](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
