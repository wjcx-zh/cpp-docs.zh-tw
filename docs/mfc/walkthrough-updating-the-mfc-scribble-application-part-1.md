---
title: "逐步解說： 更新 MFC Scribble 應用程式 （第 1 部分） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65dea486e80e4f6f1b98dffe6c387f2e530c9ef3
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>逐步解說： 更新 MFC Scribble 應用程式 （第 1 部分）
本逐步解說示範如何修改現有的 MFC 應用程式使用功能區使用者介面。 Visual Studio 支援 Office 2007 功能區和 Windows 7 Scenic 功能區。 如需功能區使用者介面的詳細資訊，請參閱[功能區](http://go.microsoft.com/fwlink/p/?linkid=129233)MSDN 網站上。  
  
 本逐步解說修改傳統 Scribble 1.0 MFC 範例，可讓您使用滑鼠來建立線條繪圖。 此部分的逐步解說示範如何修改 Scribble 範例，讓它顯示功能區列。 [第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)將更多的按鈕加入至功能區列。  
  
## <a name="prerequisites"></a>必要條件  
 [Visual C++ 範例](../visual-cpp-samples.md)  
  
 [Visual C++ 範例](../visual-cpp-samples.md)  
  
##  <a name="top"></a> 章節  
 此部分的逐步解說包含下列各節：  
  
- [取代基底類別](#replaceclass)  
  
- [加入至專案的點陣圖](#addbitmap)  
  
- [專案中加入功能區資源](#addribbon)  
  
- [建立功能區列的執行個體](#createinstance)  
  
- [加入功能區分類](#addcategory)  
  
- [設定應用程式的外觀](#setlook)  
  
##  <a name="replaceclass"></a>取代基底類別  
 若要轉換支援功能表支援的功能區的應用程式的應用程式，必須從更新的基底類別衍生應用程式、 框架視窗和工具列類別。 （我們建議您不要不修改原始 Scribble 範例; 相反地，清除 Scribble 專案、 將它複製到另一個目錄，並再修改複本）。  
  
#### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>若要取代 Scribble 應用程式中的基底類別  
  
1.  在 scribble.cpp，確認`CScribbleApp::InitInstance`包含呼叫[AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)。  
  
2.  Stdafx.h 檔案中加入下列程式碼。  
  
 ```  
    #include <afxcontrolbars.h>  
 ```  
  
3.  在 scribble.h，修改的定義`CScribbleApp`類別，因此它衍生自[CWinAppEx 類別](../mfc/reference/cwinappex-class.md)。  
  
 ```  
    class CScribbleApp: public CWinAppEx  
 ```  
  
4.  Windows 應用程式用來儲存使用者喜好設定資料的初始設定 (.ini) 檔案時，已寫入 scribble 1.0。 而不是初始設定檔案，修改 Scribble 使用者喜好設定儲存在登錄中。 若要設定的登錄機碼和基底，輸入下列程式碼中的`CScribbleApp::InitInstance`之後`LoadStdProfileSettings()`陳述式。  
  
 ```  
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));

 SetRegistryBase(_T("Settings"));

 ```  
  
5.  多重文件介面 (MDI) 應用程式的主框架不會再衍生自`CMDIFrameWnd`類別。 相反地，它衍生自[CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md)類別。  
  
     Mainfrm.h 和 mainfrm.cpp 檔案中，以取代所有參考`CMDIFrameWnd`與`CMDIFrameWndEx`。  
  
6.  Childfrm.h 和 childfrm.cpp 檔案中，取代`CMDIChildWnd`與`CMDIChildWndEx`。  
  
     在 childfrm。 h 檔案，取代`CSplitterWnd`與`CSplitterWndEx`。  
  
7.  修改工具列和狀態列，若要使用新的 MFC 類別。  
  
     在 mainfrm.h 檔中：  
  
    1.  將 `CToolBar` 取代為 `CMFCToolBar`。  
  
    2.  將 `CStatusBar` 取代為 `CMFCStatusBar`。  
  
8.  中的 mainfrm.cpp 檔案：  
  
    1.  取代`m_wndToolBar.SetBarStyle`與`m_wndToolBar.SetPaneStyle`  
  
    2.  取代`m_wndToolBar.GetBarStyle`與`m_wndToolBar.GetPaneStyle`  
  
    3.  取代`DockControlBar(&m_wndToolBar)`與`DockPane(&m_wndToolBar)`  
  
9. 在 ipframe.cpp 檔案中，註解下列三行程式碼。  
  
 ```  
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);

 pWndFrame->EnableDocking(CBRS_ALIGN_ANY);

    pWndFrame->DockPane(&m_wndToolBar);

 ```  
  
10. 如果您想要以靜態方式連結您的應用程式，請在專案的資源 (.rc) 檔的開頭中加入下列程式碼。  
  
 ```  
    #include "afxribbon.rc"  
 ```  
  
     Afxribbon.rc 檔案包含在執行階段所需的資源。 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)自動包含此檔案，當您建立應用程式。  
  
11. 儲存變更然後建置並執行應用程式。  
  
 [[區段](#top)]  
  
##  <a name="addbitmap"></a>加入至專案的點陣圖  
 本逐步解說的下一個四個步驟需要點陣圖的資源。 您可以取得適當的點陣圖，以各種方式：  
  
-   使用[資源編輯器](../windows/resource-editors.md)來自創您自己的點陣圖。 使用資源編輯器來組合點陣圖從隨附於可攜式網路圖形 (.png) 映像或[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。 這些映像位於`VS2008ImageLibrary`目錄。  
  
     不過，功能區使用者介面需要特定的點陣圖支援透明的映像。 透明的點陣圖使用 32 位元像素，其中的 24 位元指定色彩的紅色、 綠色和藍色元件以及 8 位元定義*alpha 色板*指定色彩的透明度。 目前的資源編輯器可以檢視，但無法修改 與 32 位元的像素的點陣圖。 因此，使用外部影像編輯器而不是資源編輯器，以管理透明的點陣圖。  
  
-   適當的資源檔案複製到專案的另一個應用程式，然後從該檔案匯入點陣圖。  
  
 本逐步解說會從範例目錄中的應用程式資源檔案複製。  
  
#### <a name="to-add-bitmaps-to-the-project"></a>若要加入至專案的點陣圖  
  
1.  使用檔案總管 從 資源 目錄複製下列.bmp 檔案 (`res`) 的 RibbonGadgets 範例：  
  
    1.  複製 main.bmp 至 Scribble 專案。  
  
    2.  複製 filesmall.bmp 和 filelarge.bmp Scribble 專案。  
  
    3.  新的 filelarge.bmp 和 filesmall.bmp 檔案複本，但將複本儲存在 RibbonGadgets 範例。 重新命名複製 homesmall.bmp 和 homelarge.bmp，然後將複製至 Scribble 專案。  
  
    4.  建立一份 toolbar.bmp 檔案，但在 RibbonGadgets 範例儲存複本。 重新命名複製 panelicons.bmp，然後將複製至 Scribble 專案。  
  
2.  匯入的 MFC 應用程式的點陣圖。 在**資源檢視**，按兩下**scribble.rc**節點中，按兩下**點陣圖**節點，然後再按一下**加入資源**。 在出現的對話方塊中，按一下 **匯入**。 瀏覽至`res`目錄中，選取 main.bmp 檔案，然後按一下**開啟**。  
  
     Main.bmp 點陣圖包含 26 x 26 映像。 將 IDB_RIBBON_MAIN 點陣圖的 ID。  
  
3.  匯入附加至應用程式按鈕的 [檔案] 功能表的點陣圖。  
  
    1.  匯入 filesmall.bmp 檔案，其中包含十個 16 x 16 (16 x 160) 映像。 由於我們必須只有八個 16x16 影像 (16 x 128)，因此使用**資源檢視**從 160 變更該點陣圖的寬度，為 128。 將 IDB_RIBBON_FILESMALL 點陣圖的 ID。  
  
    2.  匯入 filelarge.bmp，其中包含八個 32 x 32 (32 x 256) 映像。 將 IDB_RIBBON_FILELARGE 點陣圖的 ID。  
  
4.  匯入的功能區分類和面板的點陣圖。 在功能區列上的每個索引標籤是一個類別，並且包含具有文字標籤和選擇性的映像。  
  
    1.  匯入 homesmall.bmp 點陣圖，其中包含八個 16 x 16 小按鈕點陣圖影像。 將 IDB_RIBBON_HOMESMALL 點陣圖的 ID。  
  
    2.  匯入 homelarge.bmp 點陣圖，其中包含八個 32 x 32 的映像的大型按鈕點陣圖。 將 IDB_RIBBON_HOMELARGE 點陣圖的 ID。  
  
5.  匯入的調整大小功能區面板的點陣圖。 是調整大小作業之後使用這些點陣圖或面板 圖示，功能區太小，無法顯示整個面板是否使用。  
  
    1.  匯入 panelicons.bmp 點陣圖，其中包含八個 16 x 16 映像。 在**屬性**視窗**點陣圖編輯器**，調整至 64 (16 x 64) 點陣圖的寬度。 將 IDB_PANEL_ICONS 點陣圖的 ID。  
  
 [[區段](#top)]  
  
##  <a name="addribbon"></a>專案中加入功能區資源  
 當您轉換使用功能表以使用功能區的應用程式的應用程式時，您不必移除或停用現有的功能表。 您建立功能區資源、 加入功能區按鈕，然後將新按鈕與現有的功能表項目產生關聯。 雖然不再顯示功能表，從功能區列的訊息會路由傳送到功能表。 此外，功能表快速鍵繼續運作。  
  
 功能區是由應用程式按鈕，這是功能區的左上角的 [大型] 按鈕，以及一或多個類別索引標籤所組成。 每個類別目錄 索引標籤包含一或多個做為容器的功能區按鈕、 控制項的面板。 下列程序示範如何建立功能區資源，然後自訂應用程式按鈕。  
  
#### <a name="to-add-a-ribbon-resource-to-the-project"></a>將功能區資源加入至專案  
  
1.  在**專案**功能表上，按一下 **加入資源**。  
  
2.  在**加入資源**對話方塊中，選取**功能區**，然後按一下 **新增**。  
  
     Visual Studio 建立功能區資源，並在 [設計] 檢視中開啟。 功能區資源識別碼是 IDR_RIBBON1，它會顯示在**資源檢視**。 功能區包含一個類別目錄和一個面板。  
  
3.  您可以自訂的應用程式按鈕修改其屬性。 [] 功能表中已定義這段程式碼中使用的訊息識別碼 Scribble 1.0。  
  
4.  在 [設計] 檢視中，按一下應用程式按鈕以顯示其內容。 變更屬性值，如下所示：**映像**至`IDB_RIBBON_MAIN`，**提示**至`File`，**金鑰**至`f`，**大型影像**至`IDB_RIBBON_FILELARGE`，和**Small Images**至`IDB_RIBBON_FILESMALL`。  
  
5.  下列修改建立使用者按一下 [應用程式] 按鈕時出現的功能表。 按一下省略符號 (**...**) 旁邊**Main 項目**開啟**項目編輯器**。  
  
    1.  按一下**新增**加入的按鈕。 變更**標題**至`&New`，**識別碼**至`ID_FILE_NEW`，**映像**至`0`，**映像的大型**至`0`.  
  
    2.  按一下**新增**加入的第二個按鈕。 變更**標題**至`&Save`，**識別碼**至`ID_FILE_SAVE`，**映像**至`2`，和**映像的大型**至`2`.  
  
    3.  按一下**新增**加入的第三個按鈕。 變更**標題**至`Save &As`，**識別碼**至`ID_FILE_SAVE_AS`，**映像**至`3`，和**映像的大型**至`3`.  
  
    4.  按一下**新增**加入的第四個按鈕。 變更**標題**至`&Print`，**識別碼**至`ID_FILE_PRINT`，**映像**至`4`，和**映像的大型**至`4`.  
  
    5.  變更**項目**類型**分隔符號**，然後按一下 **新增**。  
  
    6.  變更**項目**類型**按鈕**。 按一下**新增**来加入第五個按鈕。 變更**標題**至`&Close`，**識別碼**至`ID_FILE_CLOSE`，**映像**至`5`，和**映像的大型**至`5`.  
  
6.  下列修改建立子功能表下，您在上一個步驟中建立的 [列印] 按鈕。  
  
    1.  按一下**列印**按鈕，變更**項目**類型**標籤**，然後按一下 **插入**。 變更**標題**至`Preview and print the document`。  
  
    2.  按一下**列印**按鈕，變更**項目**類型**按鈕**，然後按一下**插入**。 變更**標題**至`&Print`，**識別碼**至`ID_FILE_PRINT`，**映像**至`4`，和**映像的大型**至`4`.  
  
    3.  按一下**列印**按鈕，然後按一下**插入**加入的按鈕。 變更**標題**至`&Quick Print`，**識別碼**至`ID_FILE_PRINT_DIRECT`，**映像**至`7`，和**映像的大型**至`7`.  
  
    4.  按一下**列印**按鈕，然後按一下**插入**加入另一個按鈕。 變更**標題**至`Print Pre&view`，**識別碼**至`ID_FILE_PRINT_PREVIEW`，**映像**至`6`，和**映像的大型**至`6`.  
  
    5.  您現在已經修改**Main 項目**。 按一下**關閉**結束**項目編輯器**。  
  
7.  下列的修改會建立底部的 [應用程式] 按鈕功能表會出現 [結束] 按鈕。  
  
    1.  在**屬性**視窗中，按一下省略符號 (**...**) 旁邊**按鈕**開啟**項目編輯器**。  
  
    2.  按一下**新增**加入的按鈕。 變更**標題**至`E&xit`，**識別碼**至`ID_APP_EXIT`，**映像**至`8`。  
  
 [[區段](#top)]  
  
##  <a name="createinstance"></a>建立功能區列的執行個體  
 下列步驟示範如何建立功能區列的執行個體，您的應用程式啟動時。 若要將功能區列加入至應用程式中，宣告 mainfrm.h 檔案中的功能區列。 然後，在 mainfrm.cpp 檔案中，撰寫程式碼載入功能區資源。  
  
#### <a name="to-create-an-instance-of-the-ribbon-bar"></a>若要建立功能區列的執行個體  
  
1.  在 mainfrm.h 檔案中，將資料成員加入至保護區段`CMainFrame`，主要畫面格的類別定義。 這個成員代表功能區列。  
  
 '' * / / 功能區列的應用程式  
    CMFCRibbonBar m_wndRibbonBar;  
 ```  
  
2.  In the mainfrm.cpp file, add the following code before the final `return` statement at the end of the `CMainFrame::OnCreate` function. This creates an instance of the ribbon bar.  
  
 ``` *// Create the ribbon bar  
    if (!m_wndRibbonBar.Create(this))  
 {  
    return -1;   //Failed to create ribbon bar  
 }  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);

 ```  
  
 [[區段](#top)]  
  
##  <a name="addcategory"></a>自訂功能區資源  
 既然您已經建立的應用程式按鈕，您可以將項目加入功能區。  
  
> [!NOTE]
>  本逐步解說會使用相同的面板 圖示，所有的面板。 不過，您可以使用其他的影像清單索引，以顯示其他圖示。  
  
#### <a name="to-add-a-home-category-and-edit-panel"></a>加入首頁類別目錄和編輯面板  
  
1.  在 Scribble 程式需要只有一個類別目錄。 在 [設計] 檢視中，按一下**類別**以顯示其內容。 變更屬性值，如下所示：**標題**至`&Home`，**大型影像**至`IDB_RIBBON_HOMELARGE`， **Small Images**至`IDB_RIBBON_HOMESMALL`。  
  
2.  每個功能區分類會組織成具名的面板。 每個面板包含一組執行相關的作業的控制項。 此類別目錄具有一個面板。 按一下**面板**，然後變更**標題**至`Edit`和**映像索引**至`0`。  
  
3.  若要**編輯** 面板中，加入按鈕負責清除文件的內容。 IDR_SCRIBBTYPE 功能表資源中已定義此按鈕的訊息識別碼。 指定`Clear All`按鈕文字和裝飾按鈕點陣圖的索引。 開啟**工具箱**，然後將拖曳**按鈕**至**編輯**面板。 按一下按鈕，然後變更**標題**至`Clear All`，**識別碼**至`ID_EDIT_CLEAR_ALL`，**映像索引**至`0`， **Large Image Index**至`0`。  
  
4.  儲存變更，然後建置並執行應用程式。 Scribble 應用程式應該會顯示，且它必須有功能區列上方的視窗中，而不是功能表列。 功能區列應該有一個分類，**首頁**，和**首頁**應該有一個面板，**編輯**。 您新增的功能區按鈕應該與現有的事件處理常式，而**開啟**，**關閉**，**儲存**，**列印**，和**全部清除**按鈕應該可正常運作。  
  
 [[區段](#top)]  
  
##  <a name="setlook"></a>設定應用程式的外觀  
 A*視覺管理員*控制應用程式的所有繪圖為全域物件。 由於原始 Scribble 應用程式使用 Office 2000 使用者介面 (UI) 樣式，應用程式可能看起來舊式。 您可以重設應用程式使用 Office 2007 視覺管理員，讓它類似 Office 2007 應用程式。  
  
#### <a name="to-set-the-look-of-the-application"></a>若要設定應用程式的外觀  
  
1.  在`CMainFrame::OnCreate`函式中，輸入下列的程式碼，以變更預設視覺化管理員和樣式。  
  
 '' * / Office 2007 中設定預設管理員   
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));

 CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);

 ```  
  
2.  Save the changes, and then build and run the application. The application UI should resemble the Office 2007 UI.  
  
 [[Sections](#top)]  
  
## Next Steps  
 You have modified the classic Scribble 1.0 MFC sample to use the Ribbon Designer. Now go to [Part 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)   
 [Walkthrough: Updating the MFC Scribble Application (Part 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)

