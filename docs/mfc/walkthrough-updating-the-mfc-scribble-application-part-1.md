---
title: "逐步解說：更新 MFC Scribble 應用程式 (第 1 部分) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "範例 [C++], 更新現有的應用程式"
  - "MFC 功能套件, 更新現有的應用程式"
  - "Office Fluent UI, 移植至"
  - "功能區 UI, 移植至"
  - "範例 [C++], 更新現有的應用程式"
  - "逐步解說 [C++], 更新現有的應用程式"
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
caps.latest.revision: 54
caps.handback.revision: 50
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：更新 MFC Scribble 應用程式 (第 1 部分)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本逐步解說示範如何修改現有的 MFC 應用程式使用功能區使用者介面。  Visual Studio 支援 Office 2007 功能區和自 Windows 7 的功能區。  如需功能區使用者介面的詳細資訊，請參閱 MSDN 網站上 [功能區](http://go.microsoft.com/fwlink/?LinkId=129233) 。  
  
 這個逐步解說中修改可讓您使用滑鼠建立線條繪圖的傳統 Scribble MFC 1.0 範例。  這個逐步解說的這個部分顯示如何修改 Scribble 範例，使其顯示功能區列。  [第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) 會將多個按鈕加入至功能區列。  
  
## 必要條件  
 [Visual C\+\+ 範例](../top/visual-cpp-samples.md)  
  
 [Visual C\+\+ 範例](../top/visual-cpp-samples.md)  
  
##  <a name="top"></a> 章節  
 這部分的逐步解說中有下列部分:  
  
-   [取代基底類別](#replaceClass)  
  
-   [將點陣圖儲存至專案](#addBitmap)  
  
-   [將功能區資源加入至專案](#addRibbon)  
  
-   [建立功能區列表的執行個體。](#createInstance)  
  
-   [加入功能區類別](#addCategory)  
  
-   [設定應用程式的外觀。](#setLook)  
  
##  <a name="replaceClass"></a> 取代基底類別  
 若要轉換支援功能表對應用程式支援功能區的應用程式，您必須更新從基底類別衍生應用程式框架視窗和工具列類別。\(建議您不要修改原始的 Scribble 範例;相反地，請清除 Scribble 專案，複製至另一個目錄，然後修改複本\)。  
  
#### 取代在 Scribble 應用程式的基底類別。  
  
1.  在 scribble.cpp，確認 `CScribbleApp::InitInstance` 包含呼叫 [AfxOleInit](../Topic/AfxOleInit.md)。  
  
2.  將下列程式碼加入至 Stdafx.h 檔案：  
  
    ```  
    #include <afxcontrolbars.h>  
    ```  
  
3.  在 scribble.h，修改 `CScribbleApp` 類別定義，使其衍生自 [CWinAppEx Class](../mfc/reference/cwinappex-class.md)。  
  
    ```  
    class CScribbleApp: public CWinAppEx  
    ```  
  
4.  Scribble 1.0 時，當 Windows 應用程式使用初始化 \(.ini\) 檔案儲存使用者偏好設定資料。  請修改 Scribble 儲存使用者偏好設定在登錄中，而不是使用初始化檔案。  若要設定登錄機碼和基底，請在 `LoadStdProfileSettings()` 陳述式後面輸入在 `CScribbleApp::InitInstance` 的程式碼。  
  
    ```  
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));  
    SetRegistryBase(_T("Settings"));  
    ```  
  
5.  多重文件介面 \(MDI\) \(MDI\) 應用程式的主框架從 `CMDIFrameWnd` 類別不再衍生。  相反地，它衍生自 [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) 類別。  
  
     在 mainfrm.h 和 mainfrm.cpp 檔案，將 `CMDIFrameWndEx`取代為 `CMDIFrameWnd` 的所有參考。  
  
6.  在 childfrm.h 和 childfrm.cpp 檔案，將 `CMDIChildWndEx`取代為 `CMDIChildWnd` 。  
  
     在 childfrm.h 檔案，將 `CSplitterWndEx`取代成 `CSplitterWnd` 。  
  
7.  修改工具列和狀態列使用新的 MFC 類別。  
  
     在 mainfrm.h 檔案:  
  
    1.  將 `CToolBar` 取代為 `CMFCToolBar`。  
  
    2.  將 `CStatusBar` 取代為 `CMFCStatusBar`。  
  
8.  在 mainfrm.cpp 檔案:  
  
    1.  將 `m_wndToolBar.SetBarStyle` 取代為 `m_wndToolBar.SetPaneStyle`。  
  
    2.  將 `m_wndToolBar.GetBarStyle` 取代為 `m_wndToolBar.GetPaneStyle`。  
  
    3.  將 `DockControlBar(&m_wndToolBar)` 取代為 `DockPane(&m_wndToolBar)`。  
  
9. 在 ipframe.cpp 檔案，請註解下列三個程式碼。  
  
    ```  
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);  
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);  
    pWndFrame->DockPane(&m_wndToolBar);  
    ```  
  
10. 如果您打算以靜態方式連結到您的應用程式，請將下列程式碼加入至專案資源 \(.rc\) 檔的開頭。  
  
    ```  
    #include "afxribbon.rc"  
    ```  
  
     afxribbon.rc 檔案包含需要在執行階段的資源。  當您建立應用程式時， [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md) 會自動包含這個檔案。  
  
11. 儲存變更，接著建置並執行應用程式。  
  
 [章節](#top)  
  
##  <a name="addBitmap"></a> 將點陣圖儲存至專案  
 下一個步驟這個逐步解說需要點陣圖資源。  您可以取得適當的點陣圖以各種方式:  
  
-   使用 [Resource Editors](../mfc/resource-editors.md) 以發明您的點陣圖。  或使用資源編輯器組件從 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]包含的 PNG 檔案格式 \(.jpg\) 影像的點陣圖。  這些影像在 `VS2008ImageLibrary` 目錄。  
  
     不過，功能區使用者介面需要特定點陣圖支援透明影像。  透明點陣圖使用像素 32 位元， 24 位元指定色彩的紅色，綠色和藍色元件，8 位元定義指定色彩的透明度的 *Alpha 色頻* 。  目前的資源編輯器可以檢視，但是無法修改 32 位元像素的點陣圖。  因此，請使用外部影像編輯器，而不是資源編輯器操作透明點陣圖。  
  
-   複製另一個應用程式的資源檔加入至專案並匯入點陣圖該檔案。  
  
 這個逐步解說複製某個應用程式的資源檔在範例目錄。  
  
#### 若要將點陣圖加入至專案  
  
1.  使用檔案總管從資源目錄 \(`res`\) RibbonGadgets 範例中複製下列 .bmp 檔案:  
  
    1.  複製 main.bmp 至 Scribble 專案。  
  
    2.  複製 filesmall.bmp 和 filelarge.bmp 至 Scribble 專案。  
  
    3.  製造新的 filelarge.bmp 和 filesmall.bmp 檔案副本，不過要將副本儲存在 RibbonGadgets 範例。  將複製 homesmall.bmp 和 homelarge.bmp 重新命名並將其複製到您的 Scribble 專案。  
  
    4.  製作這個 toolbar.bmp 檔案，不過要將副本儲存在 RibbonGadgets 範例中。  將複製 panelicons.bmp 重新命名並將其複製到您的 Scribble 專案。  
  
2.  匯入 MFC 應用程式的點陣圖。  在 \[**資源檢視**\] 中，按兩下 \[**scribble.rc**\] 節點，按兩下 \[**點陣圖**\] 節點，然後按一下 \[**加入資源**\]。  在出現的對話方塊中按一下 \[**安裝**\]。  瀏覽至 `res` 目錄中，選取 main.bmp 檔案，然後按一下 \[**開啟**\]。  
  
     main.bmp 點陣圖包含 26x26 的影像。  變更點陣圖的 ID 加入至 IDB\_RIBBON\_MAIN。  
  
3.  匯入附加到應用程式按鈕的文件功能表的點陣圖。  
  
    1.  匯入包含十個16x16 \(16x160\) 影像的 filesmall.bmp 檔案，。  因為我們只需要八個 16x16 影像 \(16x128\)，請使用 \[**資源檢視**\] 來變更該點陣圖的寬度 \(從 160 到 128\)。  變更點陣圖的 ID 加入至 IDB\_RIBBON\_FILESMALL。  
  
    2.  匯入包含八個 32x32 \(32x256\) 影像的 filelarge.bmp 檔案。  變更點陣圖的 ID 加入至 IDB\_RIBBON\_FILESLARGE。  
  
4.  匯入區類別和面板的點陣圖。  功能區列的每個索引標籤是分類，並包含文字標籤和選擇性影像。  
  
    1.  匯入 homesmall.bmp 點陣圖，包含小按鈕點陣圖的八個 16x16 影像。  變更點陣圖的 ID 加入至 IDB\_RIBBON\_HOMESMALL。  
  
    2.  匯入 homelarge.bmp 點陣圖，包含大按鈕點陣圖的八個 32x32 影像。  變更點陣圖的 ID 加入至 IDB\_RIBBON\_HOMELARGE。  
  
5.  匯入調整大小的功能區面板的點陣圖。  如果功能區太小而無法顯示整個面板，在調整大小作業之後，使用這些點陣圖或面板圖示。  
  
    1.  匯入 panelicons.bmp 點陣圖，包含八個 16x16 的影像。  在 \[**點陣圖編輯器**\] 的 \[**屬性**\] 視窗，請調整點陣圖的寬度為 64 \(16x64\)。  變更點陣圖的 ID 加入至 IDB\_PANEL\_ICONS。  
  
 [章節](#top)  
  
##  <a name="addRibbon"></a> 將功能區資源加入至專案  
 當您將使用功能表對應用程式使用功能區的應用程式時，您不必移除或停用現有的功能表。  相反地，您可以建立功能區資源，新增功能區按鈕，然後將新按鈕與現有的功能表項目連結。  雖然功能表不再可見，訊息可以從功能區列的訊息傳遞。  此外，功能表快速鍵繼續運作。  
  
 功能區包括在功能區上的左上角邊的大按鈕和一個或多個分類選項的應用程式按鈕。  每個分類索引標籤包含做為功能區按鈕和控制項容器的一或多個面板。  下列程序顯示如何建立功能區資源然後自訂應用程式按鈕。  
  
#### 若要將功能區來源加入至專案  
  
1.  在 **\[專案\]** 功能表上，按一下 **\[新增參照\]**。  
  
2.  在 \[**加入資源** \] 對話方塊中，選取 \[**功能區** \]，然後按一下 \[**新增**\]。  
  
     Visual Studio 會建立功能區資源並在設計檢視中將它開啟。  功能區資源 ID 是 IDR\_RIBBON1，顯示在 \[**資源檢視**\] 中。  功能區包含類別和一個面板。  
  
3.  您可以修改它的屬性來自訂應用程式按鈕。  在這個程式碼的訊息 ID 在 Scribble 的 1.0 功能表已定義。  
  
4.  在設計檢視中，按一下應用程式按鈕顯示其屬性。  變更屬性值如下:為 `IDB_RIBBON_MAIN`的為 `檔案`的 \[**影像** \]，為 `f`的 \[**提示** \]，為 `IDB_RIBBON_FILELARGE`的 \[**索引鍵** \]，為 `IDB_RIBBON_FILESMALL`的 \[**大型影像**\] 和 \[**小型影像**\] 。  
  
5.  下列的修改會出現的功能表會在使用者按一下應用程式按鈕。  按一下 \[**主項目**\] 旁邊的省略符號 \(\[**...**\]\) 開啟 \[**項目編輯器**\]。  
  
    1.  請按一下 \[**加入**\] 以加入規則，。  將 \[**標題**\] 變更為 `&New`，其中\[**ID**\] 變更為 `ID_FILE_NEW`，\[**影像**\] 變更為 `0`，\[**大型影像**\] 變更為 `0` 。  
  
    2.  請按一下 \[**加入**\] 以加入第二個按鈕。  將 \[**標題** \] 變更為 `&Save`， \[**ID** \] 為 `ID_FILE_SAVE`， \[**影像** \] 設定為 `2`、將 \[**大型影像** \] 變更為 `2`。  
  
    3.  請按一下 \[**加入**\] 以加入第三個按鈕。  將 \[**標題** \] 變更為 `& As` ， \[**ID** \] 為 `ID_FILE_SAVE_AS`， \[**影像** \] 設定為 `3`、將 \[**大型影像** \] 變更為 `3`。  
  
    4.  請按一下 \[**加入**\] 以加入第四個按鈕。  將 \[**標題** \] 變更為 `&Print` ， \[**ID** \] 為 `ID_FILE_PRINT`， \[**影像** \] 設定為 `4`、將 \[**大型影像** \] 變更為 `4`。  
  
    5.  變更 \[**項目**\] 類型為 \[**分隔符號**\] 然後按一下 \[**加入**\]。  
  
    6.  變更 \[**項目**\] 類型變更為 \[**按鈕**\]。  請按一下 \[**加入**\] 加入第五個按鈕。  將 \[**標題** \] 變更為 `&Close` ， \[**ID** \] 為 `ID_FILE_CLOSE`， \[**影像** \] 設定為 `5`、將 \[**大型影像** \] 變更為 `5`。  
  
6.  下列修改建立子功能表在您於前一步驟所建立的列印按鈕之下。  
  
    1.  按一下 \[**列印**\] 按鈕，變更 \[**項目**\] 類型為 \[**標籤**\]，然後按一下 \[**插入**\]。  將 \[**標題**\] 變更為 `預覽並列印文件`。  
  
    2.  按一下 \[**列印**\] 按鈕，變更 \[**項目**\] 類型為 \[**按鈕**\]，然後按一下 \[**插入**\]。  將 \[**標題** \] 變更為 `&Print` ， \[**ID** \] 為 `ID_FILE_PRINT`， \[**影像** \] 設定為 `4`、將 \[**大型影像** \] 變更為 `4`。  
  
    3.  按一下 \[**列印**\] 按鈕然後按一下 \[**插入**\] 加入按鈕。  將 \[**標題** \] 變更為 `&Quick Print` ， \[**ID** \] 為 `ID_FILE_PRINT_DIRECT`， \[**影像** \] 設定為 `7`、將 \[**大型影像** \] 變更為 `7`。  
  
    4.  按一下 \[**列印**\] 按鈕然後按一下 \[**插入**\] 加入另一個按鈕。  將 \[**標題**\] 變更為 `目前的列印&檢視`， \[**ID**\] 為 `ID_FILE_PRINT_PREVIEW`， \[**影像**\] 設定為 `6`、將 \[**大型影像**\] 加入至 \[\]`6`。  
  
    5.  您現在已修改 \[**主項目**\]。  按一下完成 \[**項目編輯器**\] 中的 \[**關閉** \]。  
  
7.  下列的修改會出現在應用程式按鈕功能表底端的結束按鈕。  
  
    1.  在 \[**屬性**\] 視窗中，按一下在**按鈕**旁邊的省略按鈕 \(**...**\) 開啟 **物件編輯器**。  
  
    2.  請按一下 \[**加入**\] 以加入規則，。  將 \[**標題**\] 變更為 `E&xit`，其中 `ID_APP_EXIT`，對 \[\]`8`\[**影像**\] 的 \[**ID**\] 。  
  
 [章節](#top)  
  
##  <a name="createInstance"></a> 建立功能區列表的執行個體。  
 當應用程式啟動時，下列步驟說明如何建立功能區列的執行個體。  若要將功能區列到應用程式中，就在功能區列宣告 mainfrm.h 檔案。  然後在 mainfrm.cpp 檔案載入功能區資源的程式碼。  
  
#### 若要建立功能區列的執行個體  
  
1.  在 mainfrm.h 檔案，請將資料成員加入至 `CMainFrame` 主框架的類別定義的受保護區段。  這個成員表示功能區列。  
  
    ```  
    // Ribbon bar for the application  
    CMFCRibbonBar  m_wndRibbonBar;  
    ```  
  
2.  在 mainfrm.cpp 檔案中，在最後的 `return` 陳述式 `CMainFrame::OnCreate` 函式結尾之前加入下列程式碼。  建立功能區列的執行個體。  
  
    ```  
    // Create the ribbon bar  
    if (!m_wndRibbonBar.Create(this))  
    {  
    return -1;   //Failed to create ribbon bar  
    }  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);  
    ```  
  
 [章節](#top)  
  
##  <a name="addCategory"></a> 自訂功能區資源  
 現在您已經建立應用程式按鈕，您可以將項目加入至功能區。  
  
> [!NOTE]
>  這個逐步解說會提供適用於所有面板使用相同的面板圖示。  不過，您可以使用其他影像清單中顯示其他圖示。  
  
#### 將首頁分類和編輯面板  
  
1.  Scribble 程式只需要一個分類。  在設計檢視中，按一下以顯示 \[**分類**\] 屬性。  變更屬性值如下:為 `&Home`，其中 `IDB_RIBBON_HOMELARGE`，其中 `IDB_RIBBON_HOMESMALL`的 \[**小型影像**\] 加入 \[**大型影像**\] 中的 \[**標題**\] 。  
  
2.  每個功能區類別會組織成具名面板。  每個面板包含執行相關作業的控制項。  這個類別有一個面板。  按一下 \[**面板**\]，然後將 \[**標題** \] 變更為 `編輯` 、將 \[**影像索引。** \] 變更為 `0`。  
  
3.  若要 \[**編輯**\] 面板中，新增負責清除內容負責文件的按鈕。  這個按鈕的訊息 ID 已經在 IDR\_SCRIBBTYPE 功能表資源被定義。  指定 `清除所有` 做為按鈕文字和裝飾按鈕點陣圖的索引。  開啟 \[**工具箱**\]，然後將 \[**按鈕**\] 拖曳至 \[**編輯**\] 面板。  按一下按鈕來將 \[**標題** \] 變更為 `清除所有`，其中 `ID_EDIT_CLEAR_ALL`，其中 `0`，其中 `0`的 \[**大型影像索引。**\] 加入 \[**影像索引。**\] 中的 \[**ID** \]。  
  
4.  儲存變更，接著建置並執行應用程式。  應顯示 Scribble 應用程式，因此，它應該有功能區列位於視窗的頂端而非功能表列。  功能區列應該有一個分類， \[**首頁**\]，，而且 \[**首頁**\] 應該有一個面板， \[**編輯**\]。  您加入的功能區按鈕應該與現有的事件處理常式和 \[**開啟**\]、 \[**關閉**\]、 \[**儲存**\]、 \[**列印**\] 和 \[**清除所有**\] 按鈕應該如預期般運作。  
  
 [章節](#top)  
  
##  <a name="setLook"></a> 設定應用程式的外觀。  
 一個 *視覺化管理員* 是全域物件控制應用程式的所有繪製。  因為原始的 Scribble 應用程式使用 Office 2000 User Interface \(UI\) 樣式，應用程式看起來可能會古板。  您可以重新設定應用程式使用 Office 2007 視覺化管理員，使它類似 Office 2007 應用程式。  
  
#### 設定應用程式的外觀。  
  
1.  在 `CMainFrame::OnCreate` 函式中，輸入下列程式碼會變更預設視覺管理員和樣式。  
  
    ```  
    // Set the default manager to Office 2007   
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));  
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);  
    ```  
  
2.  儲存變更，接著建置並執行應用程式。  應用程式 UI 應類似 Office 2007 UI。  
  
 [章節](#top)  
  
## 後續步驟  
 您修改傳統 Scribble MFC 1.0 範例使用功能區設計工具。  現在移至 [第 2 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)。  
  
## 請參閱  
 [逐步解說](../mfc/walkthroughs-mfc.md)   
 [逐步解說：更新 MFC Scribble 應用程式 \(第 2 部分\)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)