---
title: 在 Visual Studio 中安裝 C++ 支援
description: 安裝視覺工作室支援視覺C++
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

如果您尚未下載並安裝 Visual Studio 和視覺C++工具,請介紹如何入門。

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Visual Studio 2019 安裝

歡迎使用 Visual Studio 2019！ 在此版本中，您可以輕鬆選擇並安裝需要的功能。 因為降低了磁碟使用量下限，所以安裝快速，且對系統影響更小。

> [!NOTE]
> 本主題適用於在 Windows 上安裝可視化工作室。 [Visual Studio Code](https://code.visualstudio.com/)是一種輕量級的跨平臺開發環境,在 Windows、Mac 和 Linux 系統上運行。 適用於 Visual Studio 代碼擴展的 Microsoft [C/C++](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)支援 IntelliSense、調試、程式碼格式設置和自動完成。 適用於 Mac 的 Visual Studio 不支援微軟 C++,但支援 .NET 語言和跨平台開發。 有關安裝說明,請參閱[為 Mac 安裝視覺化工作室](/visualstudio/mac/installation/)。

是否想要深入了解此版本的其他新功能？ 請參閱可視化工作室[發行說明](/visualstudio/releases/2019/release-notes/)。

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

安裝安裝程式後,可以通過選擇所需的*工作負載*、功能集來自定義安裝。 方法如下。

1. 在 [安裝 Visual Studio]**** 畫面中找到您想要的工作負載。

   ![視覺化工作室 2019: 安裝工作負載](../get-started/media/vs-installer-workloads.png)

   對於核心C++支援,請選擇"具有C++的桌面開發"工作負載。 它隨附預設核心編輯器，其中包括超過 20 種語言的基本程式碼編輯支援、能夠從任何資料夾開啟及編輯程式碼而不需要專案，以及整合的原始程式碼控制。

   其他工作負載支援其他類型的C++開發。 例如,選擇「通用 Windows 平台開發」工作負荷以創建使用 Microsoft 應用商店的 Windows 運行時的應用。 選擇「帶C++的遊戲開發」以創建使用 DirectX、虛幻和 Cocos2d 的遊戲。 選擇「帶有C++的Linux開發」來定位Linux平臺,包括物聯網開發。

   「**安裝詳細資訊**」 的表格列出了每個工作負荷安裝的包含元件和可選元件。 您可以在此清單中選擇或取消選擇可選元件。 例如,要使用 Visual Studio 2017 或 2015 編譯器工具集支援開發,請選擇 MSVC v141 或 MSVC v140 可選元件。 您可以添加對 MFC、實驗模組語言擴展、IncrediBuild 等的支援。

1. 選擇所需的工作負載和可選元件後,請選擇 **「安裝**」。

   接著會出現狀態畫面，顯示 Visual Studio 的安裝進度。

> [!TIP]
> 您可以在安裝後，隨時安裝一開始未安裝的工作負載或元件。 如果打開了可視化工作室,則轉到 > **「工具獲取工具和功能...",** 打開可視化工作室安裝**Tools**程式。 或者，從 [開始] 功能表開啟 [Microsoft Visual Studio 安裝程式]****。 您可以在此選擇想要安裝的工作負載或元件。 然後，選擇 [修改]****。

### <a name="step-5---choose-individual-components-optional"></a>步驟 5：選取個別元件 (選擇性)

如果您不想使用工作負載功能自定義 Visual Studio 安裝,或者希望添加比工作負載安裝更多的元件,則可以通過從 **「單個元件**」選項卡安裝或添加單個元件來執行此操作。

  ![視覺工作室 2019 - 安裝單個元件](../get-started/media/vs-installer-individual-components.png "安裝視覺化工作室各個元件")

### <a name="step-6---install-language-packs-optional"></a>步驟 6：安裝語言套件 (選擇性)

根據預設，安裝程式會在第一次執行時，嘗試比對作業系統的語言。 若要以您選擇的語言安裝 Visual Studio，請選擇 Visual Studio 安裝程式的 [語言套件]**** 索引標籤，然後遵循提示作業。

  ![視覺工作室 2019 - 安裝語言包](../get-started/media/vs-installer-language-packs.png "安裝視覺化工作室語言包")

#### <a name="change-the-installer-language-from-the-command-line"></a>從命令列變更安裝程式語言

另一個變更預設語言的方法，便是從命令列執行安裝程式。 例如，您可以使用下列命令來強制安裝程式以英文執行：`vs_installer.exe --locale en-US`。 安裝程式下次運行時將記住此設置。 安裝程式支援下列語言權杖：zh-cn、zh-tw、cs-cz、en-us、es-es、fr-fr、de-de、it-it、ja-jp、ko-kr、pl-pl、pt-br、ru-ru 和 tr-tr。

### <a name="step-7---change-the-installation-location-optional"></a>步驟 7 - 變更安裝位置 (選擇性)

您可以減少系統磁碟機上的 Visual Studio 安裝磁碟使用量。 您可以選擇將快取、共用元件、SDK 和工具下載至不同的磁碟機，並將 Visual Studio 保留在以最快速度執行它的磁碟機上。

  ![視覺工作室 2019 - 更改安裝位置](../get-started/media/vs-installer-installation-locations.png "變更安裝位置")

> [!IMPORTANT]
> 您只有在第一次安裝 Visual Studio 時才可以選取不同的磁碟機。 如已安裝 Visual Studio 並想要變更磁碟機，您必須解除安裝它，再重新安裝。

### <a name="step-8---start-developing"></a>步驟 8 - 開始開發

1. 在完成 Visual Studio 安裝後，請選擇 [啟動]**** 按鈕以開始使用 Visual Studio 來進行開發。

1. 在啟動視窗中,選擇 **「創建新專案**」。

1. 在搜尋方塊中，輸入您想要建立的應用程式類型，以查看可用的範本清單。 範本清單取決於您在安裝期間所選擇的工作負載。 若要查看不同的範本，請選擇不同的工作負載。

   您也可以使用 [語言]**** 下拉式清單來篩選搜尋特定的程式設計語言。 您也可以使用 [平台]**** 清單和 [專案類型]**** 清單來篩選。

1. Visual Studio 會開啟您的新專案，而您已準備好撰寫程式碼！

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Visual Studio 2017 安裝

在 Visual Studio 2017 中,只需選擇並安裝所需的功能即可。 因為降低了磁碟使用量下限，所以安裝快速，且對系統影響更小。

### <a name="prerequisites"></a>Prerequisites

- 寬頻互聯網連接。 可視化工作室安裝程式可以下載幾千兆位元組的數據。

- 執行 Microsoft Windows 7 或更新版本的電腦。 建議使用 Windows 10 以獲得最佳開發體驗。 在安裝 Visual Studio 之前,請確保將最新的更新應用於您的系統。

- 足夠的可用磁碟空間。 Visual Studio 至少需要 7 GB 的磁碟空間,如果安裝了許多常見選項,則可能需要 50 GB 或更多。 我們建議您將其安裝在 C: 驅動器上。

有關磁碟空間和作業系統要求的詳細資訊,請參閱[Visual Studio 產品系列系統要求](/visualstudio/productinfo/vs2017-system-requirements-vs)。 安裝程式報告您選擇的選項需要多少磁碟空間。

### <a name="download-and-install"></a>下載並安裝

1. 下載適用於 Windows 的最新 Visual Studio 2017 安裝程式。

   > [!div class="nextstepaction"]
   > [安裝 Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Community Edition 是針對個別開發人員、課堂學習、學術研究和開放原始碼開發。 針對其他用途，請安裝 [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 或 [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

1. 尋找您下載的安裝程式檔並執行它。 它可能顯示在您的瀏覽器中,或者您可能會在"下載"資料夾中找到它。 安裝程式需要管理員許可權才能運行。 您可能會看到**使用者帳戶控制**對話方塊,要求您授予允許安裝程式對系統進行更改的許可權;選擇 **"是**"。 如果遇到問題,請在檔案資源管理器中找到下載的檔,右鍵單擊安裝程式圖示,然後從上下文菜單中選擇 **「以管理員身份運行**」。。

   ![下載並安裝視覺化工作室安裝程式](media/vscpp-concierge-run-installer.gif "下載並安裝視覺化工作室安裝程式")

1. 安裝程式會顯示一份工作負載清單，而工作負載是特定開發區域的相關選項群組。 對C++的支持現在是預設未安裝的可選工作負載的一部分。

   ![具有C++工作負載的桌面開發](media/desktop-development-with-cpp.png "使用 C++ 的桌面開發")

   對於C++,選擇**具有C++工作負載的桌面開發**,然後選擇 **「安裝**」。。

   ![使用C++工作負載安裝桌面開發](media/vscpp-concierge-choose-workload.gif "使用C++工作負載安裝桌面開發")

1. 安裝完成後,選擇 **「啟動**」按鈕以啟動可視化工作室。

   首次運行 Visual Studio 時,系統會要求您使用 Microsoft 帳戶登錄。 如果您沒有組織，您可以免費建立一個。 您必須選擇主題。 別擔心,如果願意,你可以稍後更改它。

   視覺工作室可能需要幾分鐘時間才能在第一次運行時投入使用。 下面是快速延時時的樣子:

   ![視覺工作室 2017 登錄](media/vscpp-quickstart-first-run.gif "視覺工作室 2017 登錄")

   當您再次運行時,可視化工作室的啟動速度要快得多。

1. 開啟 Visual Studio 時,請檢查標題列中的標誌圖示是否突出顯示:

   ![視覺化工作室 2017 通知標誌](media/vscpp-first-start-page-flag.png "視覺化工作室 2017 通知標誌")

   如果突出顯示,請選擇它以打開 **「通知」** 視窗。 如果 Visual Studio 有任何可用的更新,我們建議您立即安裝它們。 安裝完成後,重新啟動可視化工作室。

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Visual Studio 2015 安裝

若要安裝 Visual Studio 2015，請前往[下載舊版 Visual Studio](https://www.visualstudio.com/vs/older-downloads/)。 執行安裝程式，並選擇 [自訂安裝]****，然後選擇 C++ 元件。 要向現有的 Visual Studio 2015 安裝添加C++支援,請按下「Windows 開始」按鈕並鍵入 **「添加刪除程式**」。 從結果清單中打開程式,然後在已安裝的程式清單中找到您的 Visual Studio 2015 安裝。 按兩下它,然後選擇 **「修改」** 並選擇要安裝的視覺化C++元件。

一般來說，即使需要使用 Visual Studio 2015 編譯器，編譯您的程式碼，也都非常建議您使用 Visual Studio 2017。 如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](../porting/use-native-multi-targeting.md)。

::: moniker-end

當 Visual Studio 執行時,您已準備好繼續執行下一步。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [建立C++專案](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
