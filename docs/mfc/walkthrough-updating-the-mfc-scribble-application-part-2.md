---
title: "逐步解說：更新 MFC Scribble 應用程式 (第 2 部分) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "逐步解說 [C++]"
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
caps.latest.revision: 36
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：更新 MFC Scribble 應用程式 (第 2 部分)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在本逐步解說的 [Part 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) 中，說明如何加入 Office Fluent 功能區至傳統 Scribble 應用程式中。  本節說明如何加入功能區面板及控制使用者可以使用而不是功能表和命令。  
  
## 必要條件  
 [Visual C\+\+ 範例](../top/visual-cpp-samples.md)  
  
##  <a name="top"></a> 章節  
 這部分的逐步解說中有下列部分:  
  
-   [將新的面板加入至功能區](#addNewPanel)  
  
-   [將說明面板加入至功能區](#addHelpPanel)  
  
-   [將畫筆面板加入至功能區](#addPenPanel)  
  
-   [將顏色按鈕加入至功能區。](#addColorButton)  
  
-   [將色彩成員加入至文件類別](#addColorMember)  
  
-   [初始化筆和儲存喜好設定](#initPenSave)  
  
##  <a name="addNewPanel"></a> 將新的面板加入至功能區  
 這些步驟顯示如何加入包含兩個控制工具列及狀態列的核取方塊的 \[**檢視**\] 面板，和包含控制多重文件介面\(MDI\)視窗的建立和排列的垂直方向分割按鈕的 **視窗** 面板。  
  
#### 將檢視面板和視窗面板加入至功能區列  
  
1.  建立名為 `檢視`的面板，有兩個核取方塊切換狀態列和工具列。  
  
    1.  從 \[**工具箱**\] 中，將 \[**面板** \] 拖曳至 \[**首頁**\] 分類。  然後拖曳兩個 \[**核取方塊。**\] 至面板。  
  
    2.  按一下面板來變更其屬性。  將 \[**標題**\] 變更為 \[`檢視`\]。  
  
    3.  按一下第一個核取方塊來修改其屬性。  將 \[**ID**\] 變更為 `ID_VIEW_TOOLBAR` 、將 \[**標題**\] 變更為 `工具列`。  
  
    4.  Click the second check box to modify its properties.  將 \[**ID**\] 變更為 `ID_VIEW_STATUS_BAR` 、將 \[**標題**\] 變更為 `狀態列`。  
  
2.  建立具有分割按鈕命名為 `視窗` 的面板。  當使用者按一下分割按鈕，捷徑功能表會顯示在 Scribble 應用程式已定義的三個命令。  
  
    1.  從 \[**工具箱**\] 中，將 \[**面板** \] 拖曳至 \[**首頁**\] 分類。  然後將 \[**按鈕**\] 拖曳至面板。  
  
    2.  按一下面板來變更其屬性。  將 \[**標題**\] 變更為 `視窗`。  
  
    3.  按一下這個按鈕。  將 \[**標題**\] 變更為 `視窗`， \[**索引鍵**\] 為 `w`， \[**大型影像索引**\] 設定為 `1`、將 \[**拆分模式**\] 變更為 `false`。  然後按一下 \[**功能表項目**\] 旁邊的省略符號 \(\[**...**\]\) 開啟 \[**項目編輯器**\] 對話方塊。  
  
    4.  按三次 \[**加入**\] 以加入三個按鈕。  
  
    5.  按一下第一個按鈕並將 \[**標題**\] 設定為 `新視窗`、將 \[**ID**\] 變更為 `ID_WINDOW_NEW`。  
  
    6.  按一下第二個按鈕並將 \[**標題**\] 設定為 `重疊顯示，`、將 \[**ID**\] 變更為 `ID_WINDOW_CASCADE`。  
  
    7.  按一下第三個按鈕並將 \[**標題**\] 設定為 `並排顯示`、將 \[**ID**\] 變更為 `ID_WINDOW_TILE_HORZ`。  
  
3.  儲存變更，接著建置並執行應用程式。  應該顯示 \[**檢視**\] 和 \[**視窗**\] 面板。  按一下按鈕以確認是否正確運作。  
  
 [章節](#top)  
  
##  <a name="addHelpPanel"></a> 將說明面板加入至功能區  
 現在，您可以指派兩個定義在 Scribble 應用程式中的功能表項目給名為 **Help Topics**  和  **About Scribble** 的功能區按鈕。  按鈕會加入命名為 \[**說明**\] 的新面板。  
  
#### 若要加入說明面板  
  
1.  從 \[**工具箱**\] 中，將 \[**面板** \] 拖曳至 \[**首頁**\] 分類。  然後拖曳兩個 \[**按鈕**\] 至面板中 。  
  
2.  按一下面板來變更其屬性。  將 \[**標題**\] 變更為 `說明`。  
  
3.  按一下第一個按鈕。  將 \[**標題**\] 變更為 `說明主題`、將 \[**ID**\] 變更為 `ID_HELP_FINDER`。  
  
4.  按一下第二個按鈕。  將 \[**標題**\] 變更為 `關於 Scribble…`、將 \[**ID**\] 變更為 `ID_APP_ABOUT`。  
  
5.  儲存變更，接著建置並執行應用程式。  包含兩個功能區按鈕的 \[**說明**\] 面板應顯示。  
  
    > [!IMPORTANT]
    >  當您按一下 \[**說明主題**\] 按鈕時， Scribble 應用程式開啟壓縮 HTML \(.chm\) 說明檔命名為 *your\_project\_name*.chm。  因此，如果您的專案未命名為 Scribble，您必須提供說明檔重新命名為您的專案名稱。  
  
 [章節](#top)  
  
##  <a name="addPenPanel"></a> 將畫筆面板加入至功能區  
 現在，請加入面板來顯示控制畫筆粗細和顏色的按鈕。  這個面板包含切換粗和細畫筆的核取方塊。  其功能類似於 Scribble 應用程式的 \[**粗線**\] 功能表項目。  
  
 原始的 Scribble 應用程式讓使用者點功能表上的 **畫筆寬度** 時，出現的對話方塊來選擇畫筆寬度。  由於功能區列有寬敞的空間給新控制項，使用在功能區上的兩個下拉式方塊可以取代對話方塊。  下拉式方塊調整這個細畫筆的寬度，而另一個下拉式方塊調整這個粗畫筆的寬度。  
  
#### 若要將畫筆面板和下拉式方塊加入至功能區  
  
1.  從 \[**工具箱**\] 中，將 \[**面板** \] 拖曳至 \[**首頁**\] 分類。  然後將 \[**核取方塊。**\] 和 \[**下拉式方塊**\] 拖曳至面板。  
  
2.  按一下面板來變更其屬性。  將 \[**標題**\] 變更為 `畫筆`。  
  
3.  按一下核取方塊。  將 \[**標題**\] 變更為 `使用粗`、將 \[**ID**\] 變更為 `ID_PEN_THICK_OR_THIN`。  
  
4.  按一下第一個下拉式方塊。  將 \[**標題**\] 變更為 `細畫筆`， \[**ID**\] 為 `ID_PEN_THIN_WIDTH`， \[**文字**\] 為 `2`， \[**型別**\] 設定為 `下拉式清單`、將 \[**資料**\] 變更為 `1; 2; 3; 4; 5; 6; 7; 8; 9;`。  
  
5.  按一下第二個下拉式方塊。  將 \[**標題**\] 變更為 `粗畫筆`， \[**ID**\] 為 `ID_PEN_THIN_WIDTH`， \[**文字**\] 為 `5`， \[**型別**\] 設定為 `下拉式清單`、將 \[**資料**\] 變更為 `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`。  
  
6.  新的下拉式方塊未對應到任何現有的功能表項目。  因此，您必須針對每個選項建立一個功能表項目。  
  
    1.  在 \[**資源檢視**\] 視窗中，開啟 IDR\_SCRIBBTYPE 功能表資源。  
  
    2.  按一下 \[**畫筆**\] 開啟 \[**畫筆**\] 功能表。  然後按一下 \[**在此輸入**\] 並輸入 `細&畫筆`。  
  
    3.  以滑鼠右鍵按一下您輸入開啟 \[**屬性**\] 視窗的文字，然後將 ID 屬性設定為 `ID_PEN_THIN_WIDTH`。  
  
    4.  您也必須建立每筆功能表項目的事件處理常式。  以滑鼠右鍵按一下您建立的 \[**細&畫筆**\] 功能表項目然後按一下 \[**加入事件處理常式**\]。  \[**事件處理常式精靈。**\] 隨即顯示。  
  
    5.  在精靈的 \[**類別清單**\] 方塊中選取 \[**CScribbleDoc**\] ，然後按一下 \[**加入和編輯**\]。  這會建立名為 `CScribbleDoc::OnPenThinWidth`的事件處理常式。  
  
    6.  將下列程式碼加入至 `CScribbleDoc::OnPenThinWidth`。  
  
        ```  
        // Get a pointer to the ribbon bar  
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();  
        ASSERT_VALID(pRibbon);  
        // Get a pointer to the Thin Width combo box  
        CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(  
           CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));  
        //Get the selected value  
        int nCurSel = pThinComboBox->GetCurSel();  
        if (nCurSel >= 0)  
        {  
           m_nThinWidth = atoi(pThinComboBox->GetItem(nCurSel));  
        }  
        // Create a new pen using the selected width  
        ReplacePen();    
        ```  
  
7.  接下來，為這個粗的畫筆建立一個功能表項目和事件處理常式。  
  
    1.  在 \[**資源檢視**\] 視窗中，開啟 IDR\_SCRIBBTYPE 功能表資源。  
  
    2.  按一下 \[**畫筆**\] 開啟 \[畫筆\] 功能表。  然後按一下 \[**在此輸入**\] 並輸入 `粗&畫筆`。  
  
    3.  以滑鼠右鍵按一下您輸入的字顯示 \[**屬性**\] 視窗中的文字。  變更 ID 屬性為 `ID_PEN_THICK_WIDTH`。  
  
    4.  以滑鼠右鍵按一下您建立的 \[**粗**畫筆**\] 功能表項目然後按一下 \[**加入事件處理常式\]。  \[**事件處理常式精靈。**\] 隨即顯示。  
  
    5.  在精靈的 \[**類別清單**\] 方塊中選取 \[**CScribbleDoc**\] ，然後按一下 \[**加入和編輯**\]。  這會建立名為 `CScribbleDoc::OnPenThickWidth`的事件處理常式。  
  
    6.  將下列程式碼加入至 `CScribbleDoc::OnPenThickWidth`。  
  
        ```  
        // Get a pointer to the ribbon bar  
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();  
        ASSERT_VALID(pRibbon);  
        CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(  
           CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));  
        // Get the selected value  
        int nCurSel = pThickComboBox->GetCurSel();  
        if (nCurSel >= 0)  
        {  
           m_nThickWidth = atoi(pThickComboBox->GetItem(nCurSel));  
        }  
        // Create a new pen using the selected width  
        ReplacePen();  
        ```  
  
8.  儲存變更，接著建置並執行應用程式。  應顯示新增按鈕和下拉式方塊。  使用 scribble 寫入不同的畫筆寬度的嘗試。  
  
 [章節](#top)  
  
##  <a name="addColorButton"></a> 將色彩按鈕加入至筆面板  
 接著，加入讓使用者以顏色書寫的 [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) 物件。  
  
#### 將色彩按鈕加入至畫筆面板  
  
1.  加入色彩按鈕之前，請先建立它的功能表項目。  在 \[**資源檢視**\] 視窗中，開啟 IDR\_SCRIBBTYPE 功能表資源。  按一下 \[**畫筆**\] 功能表項目以開啟畫筆功能表。  然後按一下 \[**在此處輸入**\] 並輸入 `&Color`。  以滑鼠右鍵按一下您輸入的字顯示 \[**屬性**\] 視窗中的文字。  變更 ID 為 `ID_PEN_COLOR`。  
  
2.  現在加入色彩按鈕。  從 \[**工具箱**\] 中，將 \[**色彩按鈕**\] 拖曳至 \[**畫筆**\] 面板。  
  
3.  按一下 \[色彩\] 按鈕。  將 \[**標題**\] 變更為 `色彩`、**ID** 為 `ID_PEN_COLOR`、\[**簡單**\] \[**觀看**\] 為 `true` 、\[**大型影像索引。**\] 設為 `1`，及 **拆分模式** 設為 `False`。  
  
4.  儲存變更，接著建置並執行應用程式。  在 \[**畫筆**\] 面板會顯示新的色彩按鈕。  不過，它因為沒有一個事件處理常式中尚無法使用。  下列步驟顯示如何將色彩按鈕加入事件處理常式。  
  
 [章節](#top)  
  
##  <a name="addColorMember"></a> 將色彩成員加入至文件類別  
 因為原始的 Scribble 應用程式沒有色彩筆，您必須為它們撰寫實作。  要儲存文件的畫筆顏色，將新的成員加入至文件， `CscribbleDoc.`類別  
  
#### 若要將色彩成員加入至文件類別  
  
1.  在 scribdoc.h， `CScribbleDoc` 類別，尋找 `// Attributes` 區段。  在 `m_nThickWidth` 資料成員的定義之後加入下列程式碼。  
  
    ```  
    // Current pen color  
    COLORREF   m_penColor;  
    ```  
  
2.  每個文件包含一份使用者已繪製的筆劃清單。  每個筆劃都是由 `CStroke` 物件所定義的。  `CStroke` 類別不包含畫筆的色彩資訊。  因此，您必須修改類別。  在 scribdoc.h， `CStroke` 類別，在 `m_nPenWidth` 資料成員的定義之後的加入下列程式碼。  
  
    ```  
    // Pen color for the stroke  
    COLORREF   m_penColor;  
    ```  
  
3.  在 scribdoc.h，請加入參數指定寬度和色彩的新 `CStroke` 建構函式。  將下列程式碼加入 `CStroke(UINT nPenWidth);` 陳述式之後。  
  
    ```  
    CStroke(UINT nPenWidth, COLORREF penColor);  
    ```  
  
4.  在 scribdoc.cpp，請加入新的 `CStroke` 建構函式的實作。  在 `CStroke::CStroke(UINT nPenWidth)` 的建構函式實作之後，加入下列程式碼。  
  
    ```  
    // Constructor that uses the document's current width and color  
    CStroke::CStroke(UINT nPenWidth, COLORREF penColor)  
    {  
       m_nPenWidth = nPenWidth;  
       m_penColor = penColor;  
       m_rectBounding.SetRectEmpty();  
    }  
    ```  
  
5.  如下變更 `CStroke::DrawStroke` 方法的第二行。  
  
    ```  
    if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))  
    ```  
  
6.  設定文件類別的預設畫筆顏色。  在 scribdoc.cpp，請將下列行加入至 `CScribbleDoc::InitDocument`，在 `m_nThickWidth = 5;` 陳述式之後。  
  
    ```  
    // default pen color is black  
    m_penColor = RGB(0,0,0);   
    ```  
  
7.  在 scribdoc.cpp，變更 `CScribbleDoc::NewStroke` 方法的第一行到下。  
  
    ```  
    CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);  
    ```  
  
8.  變更 `CScribbleDoc::ReplacePen` 方法的最後一行到下。  
  
    ```  
    m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);  
    ```  
  
9. 您加入上述步驟的 `m_penColor` 成員。  現在，請建立設定成員的色彩按鈕的事件處理常式。  
  
    1.  在 \[**資源檢視**\] 視窗中，開啟 IDR\_SCRIBBTYPE 功能表資源。  
  
    2.  以滑鼠右鍵按一下 \[**色彩**\] 功能表項目並按一下 \[**加入事件處理常式…**\]。  \[**事件處理常式精靈。**\] 隨即出現。  
  
    3.  在精靈的 \[**類別清單**\] 方塊中選取 \[**CScribbleDoc**\] ，然後按一下 \[**加入和編輯**\] 按鈕。  這個動作會建立 `CScribbleDoc::OnPenColor` 事件處理常式。  
  
10. 以下列程式碼取代 `CScribbleDoc::OnPenColor` 事件處理常式。  
  
    ```  
    void CScribbleDoc::OnPenColor()  
    {  
    // Change pen color to reflect color button's current selection  
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();  
    ASSERT_VALID(pRibbon);  
    CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(  
       CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));  
    m_penColor = pColorBtn->GetColor();  
    // Create new pen using the selected color  
    ReplacePen();  
    }  
    ```  
  
11. 儲存變更，接著建置並執行應用程式。  您應該可以按色彩按鈕和變更畫筆的色彩。  
  
 [章節](#top)  
  
##  <a name="initPenSave"></a> 初始化筆和儲存喜好設定  
 接著，初始畫筆的色彩和寬度。  最後，儲存並從檔案載入一個色彩繪製。  
  
#### 若要初始功能區列上的控制項  
  
1.  初始功能區列的畫筆。  
  
     將下列程式碼加入至 scribdoc.cpp，在 `CScribbleDoc::InitDocument` 方法， `m_sizeDoc = CSize(200,200)` 陳述式之後。  
  
    ```  
    // Reset the ribbon UI to its initial values  
    CMFCRibbonBar* pRibbon =   
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();  
    ASSERT_VALID(pRibbon);  
    CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(  
       CMFCRibbonColorButton,   
       pRibbon->FindByID(ID_PEN_COLOR));  
    // Set ColorButton to black  
    pColorBtn->SetColor(RGB(0,0,0));    
    CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(  
       CMFCRibbonComboBox,   
       pRibbon->FindByID(ID_PEN_THIN_WIDTH));  
    // Set Thin pen combobox to 2  
    pThinComboBox->SelectItem(1);   
    CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(  
       CMFCRibbonComboBox,   
       pRibbon->FindByID(ID_PEN_THICK_WIDTH));  
    // Set Thick pen combobox to 5  
    pThickComboBox->SelectItem(0);  
    ```  
  
2.  儲存繪製至檔案的色彩。  將下列陳述式加入至 scribdoc.cpp，在 `CStroke::Serialize` 方法， `ar << (WORD)m_nPenWidth;` 陳述式之後。  
  
    ```  
    ar << (COLORREF)m_penColor;  
    ```  
  
3.  最後，請從檔案載入一個色彩繪製。  加入下列程式碼，在 `CStroke::Serialize` 方法中，`m_nPenWidth = w;` 陳述式之後。  
  
    ```  
    ar >> m_penColor;  
    ```  
  
4.  現在以色彩繪製並儲存繪製到檔案。  
  
 [章節](#top)  
  
## 結論  
 您已更新 MFC Scribble 應用程式。  當您修改現有應用程式時，請使用這個逐步解說為導覽。  
  
## 請參閱  
 [逐步解說](../mfc/walkthroughs-mfc.md)   
 [逐步解說：更新 MFC Scribble 應用程式 \(第 1 部分\)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)