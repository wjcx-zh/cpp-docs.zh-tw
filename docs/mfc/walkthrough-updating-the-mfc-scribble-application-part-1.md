---
title: 逐步解說：更新 MFC Scribble 應用程式 （第 1 部分）
ms.date: 09/20/2018
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 213bc8087b58eac232cc8fcfccc88e13785a807e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358283"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>逐步解說：更新 MFC Scribble 應用程式 （第 1 部分）

本逐步解說示範如何修改現有的 MFC 應用程式使用功能區使用者介面。 Visual Studio 支援 Office 2007 功能區和 Windows 7 Scenic Ribbon。 如需有關功能區使用者介面的詳細資訊，請參閱 <<c0> [ 功能區](/windows/desktop/uxguide/cmd-ribbons)。

本逐步解說中修改傳統 Scribble 1.0 MFC 範例，可讓您使用滑鼠來建立線條繪圖。 這部分的逐步解說示範如何修改 Scribble 範例，使其顯示功能區列。 [第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)將更多的按鈕加入至功能區列。

## <a name="prerequisites"></a>必要條件

[Scribble 1.0 MFC 範例](http://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe)。 如需將轉換成 Visual Studio 2017 說明，請參閱[移植指南：MFC Scribble](../porting/porting-guide-mfc-scribble.md)。

##  <a name="top"></a> 章節

本逐步解說的這個部分會有下列各節：

- [取代的基底類別](#replaceclass)

- [將點陣圖新增至專案](#addbitmap)

- [專案中加入功能區資源](#addribbon)

- [建立功能區列的執行個體](#createinstance)

- [加入功能區分類](#addcategory)

- [設定應用程式的外觀](#setlook)

##  <a name="replaceclass"></a> 取代的基底類別

若要轉換的應用程式，支援的應用程式，支援的功能區功能表，您必須從更新基底類別衍生應用程式、 框架視窗和工具列類別。 （我們建議您不要修改原始的 Scribble 範例。 相反地，清除 Scribble 專案、 將它複製到另一個目錄，，然後修改複本。）

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>若要取代 Scribble 應用程式中的基底類別

1. 在 scribble.cpp，確認`CScribbleApp::InitInstance`包含呼叫[AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)。

1. Stdafx.h 檔案中加入下列程式碼。

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. 在 scribble.h，修改的定義`CScribbleApp`類別，因此它衍生自[CWinAppEx 類別](../mfc/reference/cwinappex-class.md)。

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Windows 應用程式用來儲存使用者喜好設定資料的初始設定 (.ini) 檔案時，就是撰寫 scribble 1.0。 而不是初始設定檔案，修改 Scribble 的登錄中儲存使用者喜好設定。 若要設定登錄機碼和基底，輸入下列程式碼`CScribbleApp::InitInstance`之後`LoadStdProfileSettings()`陳述式。

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. 多重文件介面 (MDI) 應用程式的主框架不會再衍生自`CMDIFrameWnd`類別。 相反地，它衍生自[CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md)類別。

    在稱為 mainfrm.h 和 mainfrm.cpp 檔案中，取代所有參考`CMDIFrameWnd`與`CMDIFrameWndEx`。

1. Childfrm.h 和 childfrm.cpp 檔案中，取代`CMDIChildWnd`與`CMDIChildWndEx`。

    在 childfrm。 h 檔案，取代`CSplitterWnd`與`CSplitterWndEx`。

1. 修改工具列和狀態列，若要使用新的 MFC 類別。

    在稱為 mainfrm.h 檔中：

    1. 將 `CToolBar` 取代為 `CMFCToolBar`。

    1. 將 `CStatusBar` 取代為 `CMFCStatusBar`。

1. 中的 mainfrm.cpp 檔案：

    1. 取代`m_wndToolBar.SetBarStyle`與 `m_wndToolBar.SetPaneStyle`

    1. 取代`m_wndToolBar.GetBarStyle`與 `m_wndToolBar.GetPaneStyle`

    1. 取代`DockControlBar(&m_wndToolBar)`與 `DockPane(&m_wndToolBar)`

1. 在 ipframe.cpp 檔案中，註解化下列三行程式碼。

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. 儲存變更然後建置並執行應用程式。

##  <a name="addbitmap"></a> 將點陣圖新增至專案

本逐步解說的接下來四個步驟需要點陣圖的資源。 您可以在各種不同的方式取得適當的點陣圖：

- 使用[資源編輯器](../windows/resource-editors.md)發明自己的點陣圖。 或使用資源編輯器來組合從可攜式網路圖形 (.png) 映像隨附於 Visual Studio，您可以從下載的點陣圖[Visual Studio 影像庫](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library)。

    不過，**功能區**使用者介面會需要某些點陣圖支援透明的映像。 透明的點陣圖使用 32 位元像素為單位，其中 24 位元指定色彩的紅色、 綠色和藍色元件，以及 8 位元定義*alpha 色頻*指定色彩的透明度。 目前的資源編輯器可以檢視，但無法修改 使用 32 位元的像素的點陣圖。 因此，使用外部影像編輯器而不是資源編輯器來操作透明的點陣圖。

- 為適當的資源檔複製到您的專案的另一個應用程式，然後從該檔案匯入點陣圖。

本逐步解說會複製中建立的範例中的資源檔[逐步解說：使用 MFC 建立功能區應用程式](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)。

### <a name="to-add-bitmaps-to-the-project"></a>將點陣圖新增至專案

1. 若要從 資源 目錄中複製下列.bmp 檔案使用檔案總管 (`res`) 的功能區範例資源目錄 (`res`) 的 Scribble 專案：

   1. 複製 main.bmp 到 Scribble 專案。

   1. 您可以複製 filesmall.bmp 和 filelarge.bmp 到 Scribble 專案。

   1. 建立新的 filelarge.bmp 和 filesmall.bmp 檔案複本，但將複本儲存在功能區範例。 重新命名複製 homesmall.bmp 和 homelarge.bmp，然後將複本移至您的 Scribble 專案。

   1. 建立一份 toolbar.bmp 檔案，但將複本儲存在功能區範例。 重新命名複製 panelicons.bmp，然後將複本移至 Scribble 專案。

1. 匯入的 MFC 應用程式的點陣圖。 在 **資源檢視**，按兩下**scribble.rc**節點，按兩下**點陣圖**節點，然後再按一下**新增資源**。 在出現的對話方塊中，按一下 **匯入**。 瀏覽至`res`目錄中，選取 main.bmp 檔案，然後按一下**開啟**。

   Main.bmp 點陣圖包含 26 x 26 映像。 變更至點陣圖的 ID `IDB_RIBBON_MAIN`。

1. 匯入附加至 檔案 功能表的點陣圖**應用程式** 按鈕。

   1. 匯入 filesmall.bmp 檔案，其中包含十一個 16 x 16 (16 x 176) 映像。 變更至點陣圖的 ID `IDB_RIBBON_FILESMALL`。

   > [!NOTE]
   > 因為我們需要只有前八個 16 x 16 個映像 (16 x 128)，您可能會選擇性地裁剪 176 128 此點陣圖的右端寬度。

   1. 匯入 filelarge.bmp，其中包含九個 32 x 32 (32 x 288) 映像。 變更至點陣圖的 ID `IDB_RIBBON_FILELARGE`。

1. 匯入的功能區分類和面板的點陣圖。 在功能區列上的每個索引標籤是類別，且包含的文字標籤和選擇性的映像。

   1. 匯入 homesmall.bmp 點陣圖，其中包含十一個 16 x 16 小按鈕點陣圖影像。 變更至點陣圖的 ID `IDB_RIBBON_HOMESMALL`。

   1. 匯入 homelarge.bmp 點陣圖，其中包含九個 32 x 32 大按鈕點陣圖影像。 變更至點陣圖的 ID `IDB_RIBBON_HOMELARGE`。

1. 匯入已調整大小的功能區面板的點陣圖。 如果功能區太小而無法顯示整個面板，是會調整大小作業之後使用這些點陣圖 或 面板 圖示。

   1. 匯入 panelicons.bmp 點陣圖，其中包含八個 16 x 16 的映像。 在 **屬性**視窗**點陣圖編輯器**，調整為 64 (16 x 64) 點陣圖的寬度。 變更至點陣圖的 ID `IDB_PANEL_ICONS`。

   > [!NOTE]
   > 因為我們需要只有前四個 16 x 16 個映像 (16 x 64)，您可能會選擇性地裁剪右側點陣圖的寬度這個 128 為 64。

##  <a name="addribbon"></a> 專案中加入功能區資源

當您轉換使用功能表來使用功能區的應用程式的應用程式時，您不需要移除或停用現有的功能表。 只要建立功能區資源、 新增功能區按鈕，並將關聯的新按鈕現有的功能表項目。 雖然不會再顯示功能表，從功能區列的訊息會路由傳送透過功能表和功能表的捷徑繼續運作。

功能區所組成**應用程式**按鈕，也就是功能區的左上方的 [大型] 按鈕，然後一或多個類別索引標籤。 每個類別目錄 索引標籤包含一或多個做為容器的功能區按鈕與控制項的面板。 下列程序示範如何建立功能區資源，然後自訂**應用程式** 按鈕。

### <a name="to-add-a-ribbon-resource-to-the-project"></a>若要將功能區資源新增至專案

1. Scribble 專案中選取**方案總管**，請在**專案**功能表上，按一下 **加入資源**。

1. 在 **加入資源**對話方塊中，選取**功能區**，然後按一下 **新增**。

   Visual Studio 建立功能區資源，並在 [設計] 檢視中開啟。 功能區資源識別碼`IDR_RIBBON1`，會顯示在**資源檢視**。 功能區包含一個類別目錄和一個面板。

1. 您可以自訂**應用程式**按鈕修改其屬性。 [] 功能表中已定義此程式碼中使用的訊息識別碼 Scribble 1.0。

1. 在 設計 檢視中，按一下**應用程式** 按鈕以顯示其屬性。 請變更屬性值，如下所示：**映像**來`IDB_RIBBON_MAIN`，**提示**來`File`，**金鑰**至`f`，**大型影像**來`IDB_RIBBON_FILELARGE`，及**Small Images**至`IDB_RIBBON_FILESMALL`。

1. 下列修改建立當使用者按一下出現的功能表**應用程式** 按鈕。 按一下省略符號 (**...**) 旁**主要項目**以開啟**項目編輯器**。

   1. 具有**項目**型別 **] 按鈕**選取，按一下 [**新增**加入的按鈕。 變更**標題**要`&New`，**識別碼**來`ID_FILE_NEW`，**映像**到`0`，**大型影像**以`0`.

   1. 按一下 **新增**加入的按鈕。 變更**標題**要`&Save`，**識別碼**來`ID_FILE_SAVE`，**映像**到`2`，和**大型影像**至`2`.

   1. 按一下 **新增**加入的按鈕。 變更**標題**要`Save &As`，**識別碼**來`ID_FILE_SAVE_AS`，**映像**到`3`，和**大型影像**至`3`.

   1. 按一下 **新增**加入的按鈕。 變更**標題**要`&Print`，**識別碼**來`ID_FILE_PRINT`，**映像**到`4`，和**大型影像**至`4`.

   1. 變更**項目**類型**分隔符號**，然後按一下 **新增**。

   1. 變更**項目**類型** 按鈕**。 按一下 **新增**加入的第五個按鈕。 變更**標題**要`&Close`，**識別碼**來`ID_FILE_CLOSE`，**映像**到`5`，和**大型影像**至`5`.

1. 下列修改建立子功能表下的**列印**您在上一個步驟中建立的按鈕。

   1. 按一下 **列印**按鈕，變更**項目**輸入到**標籤**，然後按一下**插入**。 變更**Caption**至`Preview and print the document`。

   1. 按一下 **列印**按鈕，變更**項目**類型**按鈕**，然後按一下**插入**。 變更**標題**要`&Print`，**識別碼**來`ID_FILE_PRINT`，**映像**到`4`，和**大型影像**至`4`.

   1. 按一下 **列印**按鈕，然後按一下**插入**加入的按鈕。 變更**標題**要`&Quick Print`，**識別碼**來`ID_FILE_PRINT_DIRECT`，**映像**到`7`，和**大型影像**至`7`.

   1. 按一下 **列印**按鈕，然後按一下**插入**加入另一個按鈕。 變更**標題**要`Print Pre&view`，**識別碼**來`ID_FILE_PRINT_PREVIEW`，**映像**到`6`，和**大型影像**至`6`.

   1. 您現在已修改**主要項目**。 按一下 **關閉**以結束**項目編輯器**。

1. 以下修改會出現 [結束] 按鈕建立底部**應用程式**按鈕功能表。

   1. 在 **屬性** 視窗中，按一下省略符號 (**...**) 旁** 按鈕**以開啟**項目編輯器**。

   1. 具有**項目**型別 **] 按鈕**選取，按一下 [**新增**加入的按鈕。 變更**標題**要`E&xit`，**識別碼**來`ID_APP_EXIT`，**映像**到`8`。

   1. 您已修改**按鈕**。 按一下 **關閉**以結束**項目編輯器**。

##  <a name="createinstance"></a> 建立功能區列的執行個體

下列步驟示範如何建立功能區列的執行個體，您的應用程式啟動時。 若要將功能區列新增至應用程式中，宣告稱為 mainfrm.h 檔案中的功能區列。 然後，在 mainfrm.cpp 檔案中，撰寫程式碼載入功能區資源。

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>若要建立功能區列的執行個體

1. 在稱為 mainfrm.h 檔案中，將資料成員新增到受保護的區段`CMainFrame`，主要畫面格的類別定義。 這個成員是功能區列。

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. 在 mainfrm.cpp 檔案中，加入下列的程式碼，最後再`return`陳述式的結尾`CMainFrame::OnCreate`函式。 它會建立功能區列的執行個體。

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

##  <a name="addcategory"></a> 自訂功能區資源

既然您已建立**應用程式** 按鈕，您可以加入功能區中的項目。

> [!NOTE]
> 本逐步解說會使用相同的面板 圖示，所有的面板。 不過，您可以使用其他的影像清單索引，以顯示其他圖示。

### <a name="to-add-a-home-category-and-edit-panel"></a>將首頁分類加入和編輯面板

1. Scribble 程式需要一種類別。 在 [設計] 檢視中，在**工具箱**，按兩下**分類**加入一個，並顯示其屬性。 請變更屬性值，如下所示：**標題**要`&Home`，**大型映像**來`IDB_RIBBON_HOMELARGE`，**小型影像**至`IDB_RIBBON_HOMESMALL`。

1. 每個功能區分類會組織成具名的面板。 每個面板包含一組控制項，完整的相關的作業。 此類別目錄具有一個面板。 按一下 **面板**，然後變更**標題**到`Edit`。

1. 若要**編輯** 面板中，新增按鈕負責清除文件的內容。 中的這個按鈕的訊息識別碼已定義`IDR_SCRIBBTYPE`功能表資源。 指定`Clear All`做為按鈕文字和裝飾按鈕點陣圖的索引。 開啟**工具箱**，然後將拖曳** 按鈕**來**編輯**面板。 按一下按鈕，然後變更**標題**要`Clear All`，**識別碼**來`ID_EDIT_CLEAR_ALL`，**映像索引**到`0`， **Large Image Index**至`0`。

1. 儲存變更，然後建置並執行應用程式。 Scribble 應用程式應該會顯示，，而且它應該在視窗中，而不是功能表列頂端功能區列。 功能區列應該有一個類別，**首頁**，並**Home**應該有一個面板，**編輯**。 您新增的功能區按鈕應該與現有的事件處理常式，而**開放**，**關閉**，**儲存**，**列印**，並**全部清除**按鈕應該會如預期般運作。

##  <a name="setlook"></a> 設定應用程式的外觀

A*視覺化管理員*會控制所有活動，抽獎獲得應用程式的全域物件。 由於原始的 Scribble 應用程式使用 Office 2000 使用者介面 (UI) 樣式，看起來舊式應用程式。 您可以重設應用程式使用 Office 2007 的視覺管理員，使它類似 Office 2007 應用程式。

### <a name="to-set-the-look-of-the-application"></a>若要設定應用程式的外觀

1. 在 `CMainFrame::OnCreate`函式中，輸入下列程式碼，再`return 0;`陳述式來變更預設視覺化管理員和樣式。

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. 儲存變更，然後建置並執行應用程式。 應用程式的 UI 應類似於 Office 2007 UI。

## <a name="next-steps"></a>後續步驟

您修改了傳統的 Scribble 1.0 MFC 範例，以使用**功能區設計工具**。 現在請移至[第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)。

## <a name="see-also"></a>另請參閱

[逐步解說](../mfc/walkthroughs-mfc.md)<br/>
[逐步解說：更新 MFC Scribble 應用程式 (第 2 部分)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
