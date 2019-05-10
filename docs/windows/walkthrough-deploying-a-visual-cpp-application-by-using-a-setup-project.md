---
title: 使用安裝專案部署 Visual C++ 應用程式
ms.date: 04/25/2019
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: 6829e917ed0a0e27bea7f42eb9bcfb2b9ad5d2e1
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877372"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>逐步解說：使用安裝專案部署 Visual C++ 應用程式

描述如何使用安裝專案部署 Visual C++ 應用程式。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成此逐步解說：

- 已安裝 Visual Studio 的電腦。

- 另一部不含 Visual C++ 程式庫的電腦。

## <a name="create-the-setup-project"></a>建立安裝專案

建立安裝專案的指示，端視您已安裝的 Visual Studio 版本而有所不同。 請確定您有版本選擇器右上方設為正確的版本。

::: moniker range="=vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中建立專案

1. 在功能表列上選擇 [**檔案** > **新增** > **專案**開啟**建立新的專案**] 對話方塊。

   ![MFC 應用程式專案](media/vs2019-mfc-app-new-project.png "新的 MFC 應用程式")

1. 在對話方塊頂端，輸入`MFC`在搜尋] 方塊，然後選擇 [ **MFC 應用程式**從結果清單中。 如果您找不到的話，您必須啟動 Visual Studio 安裝程式，從 Windows 開始 功能表，然後按一下   **C++的桌面開發工作負載**圖格。 底下**個別元件**，確定已核取 MFC 元件。

1. 在下一步 頁面中，輸入專案名稱，然後指定專案位置，如有需要。

1. 選擇**建立** 按鈕來建立用戶端專案。 當**MFC 應用程式精靈**出現時，接受所有預設值。

1. 將使用中的解決方案組態變更為 [發行]。 從 [建置] 功能表，選取 [組態管理員]。 在 [組態管理員] 對話方塊中，選取 [使用中的方案組態] 下拉式清單方塊上的 [發行]。 按一下 [ **關閉**]。

1. 按 **Ctrl**+**Shift**+**B** 建置應用程式。 或者，在 [建置] 功能表上，按一下 [建置方案]。 建置應用程式時，可讓安裝專案使用此 MFC 應用程式專案的輸出。

1. 如果您尚未這麼做，請下載 Microsoft Visual Studio 安裝程式專案延伸模組。 延伸模組是免費提供給 Visual Studio 開發人員使用，並可將安裝和部署專案範本的功能新增至 Visual Studio。 當您已連線到網際網路，請在 Visual Studio 中，選擇**延伸模組** > **管理延伸模組**。 選取 [延伸模組和更新] 對話方塊下方的 [線上] 索引標籤，然後在搜尋方塊中鍵入「Microsoft Visual Studio 安裝程式專案」。 按下**Enter**，選取**Microsoft Visual Studio\<版本 > 安裝程式專案**，然後按一下**下載**。 選擇執行並安裝延伸模組，然後重新啟動 Visual Studio。

   ![Visual Studio 安裝程式專案](media/vs2019-extension-dialog-installer-project.png "用戶端專案的名稱")

1. 在 Visual Studio 功能表列上選擇 **檔案** > **最新的專案和方案**，然後選擇重新開啟您的專案。

1. 在功能表列上選擇 [**檔案** > **新增** > **專案**開啟**建立新的專案**] 對話方塊。 在搜尋方塊中，輸入 Setup，然後從結果清單中選擇**安裝專案**。

1. 在 [名稱] 方塊中，輸入安裝專案的名稱。 在 [方案] 下拉式清單中，選取 [新增至方案]。 選擇 [確定] 按鈕以建立安裝專案。 編輯器視窗中隨即開啟 [File Assistant (ProjectName)] \(檔案小幫手 (ProjectName)\) 索引標籤。

::: moniker-end

::: moniker range="=vs-2017"

### <a name="to-create-the-project-in-visual-studio-2017"></a>在 Visual Studio 2017 中建立專案

1. 建立新的專案。 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。

1. 使用**MFC 應用程式精靈**建立新的 Visual Studio 方案。 若要尋找精靈，請從 [新增專案] 對話方塊方塊中，展開 [Visual C++] 節點、依序選取 [MFC] 和 [MFC 應用程式]、輸入專案名稱，然後按一下 [確定]。 按一下 [ **完成**]。

   > [!NOTE]
   > 如果**MFC 應用程式**遺漏類型中，選取**開啟 Visual Studio 安裝程式**中的左窗格**新專案** 對話方塊。 安裝位於 [選用元件] 區段中 [使用 C++ 的桌面開發] 下方的選項 ，其名稱為 **x86 與 x64 版 Visual C++ MFC**。

1. 將使用中的解決方案組態變更為 [發行]。 從 [建置] 功能表，選取 [組態管理員]。 在 [組態管理員] 對話方塊中，選取 [使用中的方案組態] 下拉式清單方塊上的 [發行]。 按一下 [ **關閉**]。

1. 按 **Ctrl**+**Shift**+**B** 建置應用程式。 或者，在 [建置] 功能表上，按一下 [建置方案]。 建置應用程式時，可讓安裝專案使用此 MFC 應用程式專案的輸出。

1. 如果您尚未這麼做，請下載 Microsoft Visual Studio 安裝程式專案延伸模組。 延伸模組是免費提供給 Visual Studio 開發人員使用，並可將安裝和部署專案範本的功能新增至 Visual Studio。 當您已連線到網際網路時，請在 Visual Studio 中選擇 [工具] > [延伸模組和更新]。 選取 [延伸模組和更新] 對話方塊下方的 [線上] 索引標籤，然後在搜尋方塊中鍵入「Microsoft Visual Studio 安裝程式專案」。 按下**Enter**，選取**Microsoft Visual Studio\<版本 > 安裝程式專案**，然後按一下**下載**。 選擇執行並安裝延伸模組，然後重新啟動 Visual Studio。

1. 在功能表列上選擇 **檔案** > **最新的專案和方案**，然後選擇重新開啟您的專案。

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]，以開啟 [新增專案] 對話方塊。 在對話方塊的左窗格中，展開 [已安裝] > [其他專案類型] 節點，然後選取 [Visual Studio 安裝程式]。 在中間窗格中，選取 [安裝專案]。

1. 在 [名稱] 方塊中，輸入安裝專案的名稱。 在 [方案] 下拉式清單中，選取 [新增至方案]。 選擇 [確定] 按鈕以建立安裝專案。 編輯器視窗中隨即開啟 [File Assistant (ProjectName)] \(檔案小幫手 (ProjectName)\) 索引標籤。

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-the-project-in-visual-studio-2015"></a>在 Visual Studio 2015 中建立專案

1. 建立新的專案。 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。

1. 使用**MFC 應用程式精靈**建立新的 Visual Studio 方案。 若要尋找精靈，請從 [新增專案] 對話方塊方塊中，展開 [Visual C++] 節點、依序選取 [MFC] 和 [MFC 應用程式]、輸入專案名稱，然後按一下 [確定]。 按一下 [ **完成**]。

   > [!NOTE]
   > 如果**MFC 應用程式**遺漏類型中，按一下 Windows [開始] 按鈕並鍵入**新增或移除程式**。 從結果清單中開啟程式，然後在已安裝的程式清單中尋找您的 Microsoft Visual Studio 2015 安裝。 按兩下該安裝項目，然後選擇 [修改]，並選取 **Visual C++** 下方的 [Microsoft Foundation Classes]。

1. 將使用中的解決方案組態變更為 [發行]。 從**建置**功能表上，選取**Configuration Manager**。 在 [組態管理員] 對話方塊中，選取 [使用中的方案組態] 下拉式清單方塊上的 [發行]。 按一下 [ **關閉**]。

1. 按 **Ctrl**+**Shift**+**B** 建置應用程式。 或者，在 [建置] 功能表上，按一下 [建置方案]。 建置應用程式時，可讓安裝專案使用此 MFC 應用程式專案的輸出。

1. 如果您尚未這麼做，請下載 Microsoft Visual Studio 安裝程式專案延伸模組。 延伸模組是免費提供給 Visual Studio 開發人員使用，並可將安裝和部署專案範本的功能新增至 Visual Studio。 當您已連線到網際網路時，請在 Visual Studio 中選擇 [工具] > [延伸模組和更新]。 選取 [延伸模組和更新] 對話方塊下方的 [線上] 索引標籤，然後在搜尋方塊中鍵入「Microsoft Visual Studio 安裝程式專案」。 按下**Enter**，選取**Microsoft Visual Studio\<版本 > 安裝程式專案**，然後按一下**下載**。 選擇執行並安裝延伸模組，然後重新啟動 Visual Studio。

1. 在功能表列上選擇 **檔案** > **最新的專案和方案**，然後選擇重新開啟您的專案。

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]，以開啟 [新增專案] 對話方塊。 在對話方塊的左窗格中，展開 [已安裝] > [其他專案類型] 節點，然後選取 [Visual Studio 安裝程式]。 在中間窗格中，選取 [安裝專案]。

1. 在 [名稱] 方塊中，輸入安裝專案的名稱。 在 [方案] 下拉式清單中，選取 [新增至方案]。 選擇 [確定] 按鈕以建立安裝專案。 編輯器視窗中隨即開啟 [File Assistant (ProjectName)] \(檔案小幫手 (ProjectName)\) 索引標籤。

::: moniker-end

## <a name="add-items-to-the-project"></a>將項目加入至專案

1. 以滑鼠右鍵按一下 [應用程式資料夾] 節點，然後選取 [新增] > [專案輸出] 以開啟 [新增專案輸出群組] 對話方塊。 在對話方塊中選取 [主要輸出]，然後按一下 [確定]。 隨即顯示新項目，名稱為 [Primary Output from ProjectName (Active)] \(來自 ProjectName (使用中) 的主要輸出\)。

1. 以滑鼠右鍵按一下 [應用程式資料夾] 節點，然後選取 [新增] > [組件] 以開啟 [選取元件] 對話方塊。 如[決定要轉散發哪些 DLL](determining-which-dlls-to-redistribute.md) 一文所述，選取並新增程式所需的任何 Dll。

1. 選取 [Primary Output from ProjectName (Active)] \(來自 ProjectName (使用中) 的主要輸出\) 項目，再按一下滑鼠右鍵，然後選擇 [Create Shortcut to Primary Output from ProjectName (Active)] \(建立來自 ProjectName (使用中) 的主要輸出捷徑\)。 隨即顯示新項目，名稱為 [Shortcut to Primary Output from ProjectName (Active)] \(來自 ProjectName (使用中) 的主要輸出捷徑\)。 您可以重新命名捷徑項目，然後將項目拖曳至視窗左側的 [使用者的程式功能表] 節點。

1. 在功能表列上，選擇 [建置] > [組態管理員]。 在 [專案] 資料表的 [建置] 資料行下方，核取部署專案的方塊。 按一下 [ **關閉**]。

1. 在功能表列上，選擇 [建置] > [建置方案] 以建置 MFC 專案和部署專案。

1. 在方案資料夾中，找出透過部署專案所建置的 setup.exe 程式。 您可以複製這個檔案 (和 .msi 檔案) ，在另一部電腦上安裝應用程式及其必要的程式庫檔案。 在不含 Visual C++ 程式庫的第二部電腦上執行安裝程式。

## <a name="see-also"></a>另請參閱

[部署範例](deployment-examples.md)<br/>
