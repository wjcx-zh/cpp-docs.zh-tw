---
title: 逐步解說： 更新 MFC Scribble 應用程式 （第 2 部分） |Microsoft Docs
ms.custom: ''
ms.date: 09/20/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3623eb594ff82660e97809eef609a33e74e74dc
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235434"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>逐步解說：更新 MFC Scribble 應用程式 (第 2 部分)

[第 1 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)本逐步解說示範如何將 Office Fluent 功能區新增至傳統的 Scribble 應用程式。 此組件會示範如何加入功能區面板和控制項，使用者可以使用而不是功能表和命令。

## <a name="prerequisites"></a>必要條件

[Visual C++ 範例](../visual-cpp-samples.md)

##  <a name="top"></a> 章節

本逐步解說的這個部分會有下列各節：

- [在功能區中加入新的面板](#addnewpanel)

- [在功能區中加入說明面板](#addhelppanel)

- [在功能區中加入 [畫筆] 面板](#addpenpanel)

- [加入功能區色彩按鈕](#addcolorbutton)

- [將色彩成員加入至文件類別](#addcolormember)

- [初始化畫筆及儲存喜好設定](#initpensave)

##  <a name="addnewpanel"></a> 在功能區中加入新的面板

這些步驟顯示如何新增**檢視**面板，其中包含兩個核取方塊，以控制可見性的工具列和狀態列，以及**視窗**包含垂直方向的分割面板控制項的建立和排列多重文件介面 (MDI) 視窗的按鈕。

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>若要檢視面板和視窗 面板中加入功能區列

1. 建立名為面板`View`，其中包含兩個核取方塊的切換狀態 列和工具列。

   1. 從**工具箱**，拖曳**面板**來**首頁**類別目錄。 然後將兩個**核取方塊**面板。

   1. 按一下要修改其內容的面板。 變更**Caption**至`View`。

   1. 按一下第一個核取方塊，若要修改其屬性。 變更**識別碼**要`ID_VIEW_TOOLBAR`並**標題**至`Toolbar`。

   1. 按一下第二個核取方塊，若要修改其屬性。 變更**識別碼**要`ID_VIEW_STATUS_BAR`並**標題**至`Status Bar`。

1. 建立名為面板`Window`具有的分隔按鈕。 當使用者按一下 [分割] 按鈕時，快顯功能表會顯示 Scribble 應用程式中，已定義的三個命令。

   1. 從**工具箱**，拖曳**面板**來**首頁**類別目錄。 然後將拖曳** 按鈕**面板。

   1. 按一下要修改其內容的面板。 變更**Caption**至`Window`。

   1. 按一下按鈕。 變更**標題**要`Windows`，**金鑰**來`w`，**大型映像索引**到`1`，和**Split Mode**若要`False`。 然後按一下省略符號 (**...**) 旁**功能表項目**以開啟**項目編輯器** 對話方塊。

   1. 按一下 **新增**三次，以新增三個按鈕。

   1. 按一下第一個按鈕，然後變更**標題**要`New Window`，以及**識別碼**到`ID_WINDOW_NEW`。

   1. 按一下第二個按鈕，然後變更**標題**要`Cascade`，以及**識別碼**到`ID_WINDOW_CASCADE`。

   1. 按一下第三個按鈕，然後變更**標題**要`Tile`，以及**識別碼**至`ID_WINDOW_TILE_HORZ`。

1. 儲存變更，然後建置並執行應用程式。 **檢視**並**視窗**應該顯示面板。 按一下按鈕，以確認它們正常運作。

##  <a name="addhelppanel"></a> 在功能區中加入說明面板

現在，您可以指派至名為功能區按鈕 Scribble 應用程式中所定義的兩個功能表項目**說明主題**並**有關 Scribble**。 按鈕會新增至新的面板，名為**協助**。

### <a name="to-add-a-help-panel"></a>若要新增說明面板

1. 從**工具箱**，拖曳**面板**來**首頁**類別目錄。 然後將兩個**按鈕**面板。

1. 按一下要修改其內容的面板。 變更**Caption**至`Help`。

1. 按一下第一個按鈕。 變更**標題**要`Help Topics`，以及**識別碼**至`ID_HELP_FINDER`。

1. 按一下第二個按鈕。 變更**標題**要`About Scribble...`，以及**識別碼**至`ID_APP_ABOUT`。

1. 儲存變更，然後建置並執行應用程式。 A**協助**應該會顯示包含兩個功能區按鈕的面板。

   > [!IMPORTANT]
   > 當您按一下 [**說明主題**] 按鈕，Scribble 應用程式會開啟壓縮的 (.chm) 的 HTML 說明檔，名為*your_project_name*。 有 因此，如果您的專案名稱不是 Scribble，您必須重新命名的說明檔為您的專案名稱。

##  <a name="addpenpanel"></a> 在功能區中加入 [畫筆] 面板

現在，加入顯示按鈕，可控制粗細和色彩的畫筆的面板。 此面板包含核取方塊來切換厚重型和精簡型的畫筆。 其功能類似於**粗線**Scribble 應用程式中的功能表項目。

原始的 Scribble 應用程式可讓使用者選取使用者按一下時，會出現在對話方塊中的畫筆寬度**畫筆寬度**功能表上。 功能區列有充裕的空間，新的控制項，因為您可以使用功能區上的兩個下拉式方塊來取代對話方塊。 一個下拉式方塊調整細的畫筆的寬度，和其他下拉式方塊調整粗的畫筆的寬度。

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>若要加入功能區中的畫筆面板和下拉式方塊

1. 從**工具箱**，拖曳**面板**來**首頁**類別目錄。 然後將拖曳** 核取方塊**並將兩個**下拉式方塊**面板。

1. 按一下要修改其內容的面板。 變更**Caption**至`Pen`。

1. 按一下核取方塊。 變更**標題**要`Use Thick`，以及**識別碼**至`ID_PEN_THICK_OR_THIN`。

1. 按一下第一個下拉式方塊。 變更**標題**要`Thin Pen`，**識別碼**來`ID_PEN_THIN_WIDTH`，**類型**來`Drop List`，**資料**至`1;2;3;4;5;6;7;8;9;`，並**文字**至`2`。

1. 按一下第二個下拉式方塊。 變更**標題**要`Thick Pen`，**識別碼**來`ID_PEN_THICK_WIDTH`，**類型**來`Drop List`，**資料**至`5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`，並**文字**至`5`。

1. 新的下拉式方塊不對應至任何現有的功能表項目，因此您必須建立每個 [畫筆] 選項的功能表項目。

   1. 在 **資源檢視**視窗中，開啟**IDR_SCRIBBTYPE**功能表資源。

   1. 按一下 **畫筆**以開啟 畫筆 功能表。 然後按一下**在這裡輸入**並輸入`Thi&n Pen`。

   1. 以滑鼠右鍵按一下以開啟您所輸入的文字**屬性**視窗，然後再變更識別碼屬性`ID_PEN_THIN_WIDTH`。

   1. 建立每個 [畫筆] 功能表項目的事件處理常式。 以滑鼠右鍵按一下**這個 & n 畫筆**功能表項目，您建立，然後按一下**加入事件處理常式**。 **事件處理常式精靈**隨即出現。

   1. 在 **類別清單**在精靈中，選取方塊**CScribbleDoc** ，然後按一下 **新增和編輯**。 此命令會建立名為事件處理常式`CScribbleDoc::OnPenThinWidth`。

   1. 將下列程式碼加入至 `CScribbleDoc::OnPenThinWidth`。

    ```cpp
    // Get a pointer to the ribbon bar
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
    ASSERT_VALID(pRibbon);

    // Get a pointer to the Thin Width combo box
    CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
    CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));

    //Get the selected value
    int nCurSel = pThinComboBox->GetCurSel();
    if (nCurSel>= 0)
    {
        m_nThinWidth = atoi(CStringA(pThinComboBox->GetItem(nCurSel)));
    }

    // Create a new pen using the selected width
    ReplacePen();
    ```

1. 接下來，建立功能表項目和事件的處理常式，如粗的畫筆。

   1. 在 **資源檢視**視窗中，開啟**IDR_SCRIBBTYPE**功能表資源。

   1. 按一下 **畫筆**以開啟 畫筆 功能表。 然後按一下**在這裡輸入**並輸入`Thic&k Pen`。

   1. 以滑鼠右鍵按一下您要顯示您輸入的文字**屬性**視窗。 將識別碼屬性來變更`ID_PEN_THICK_WIDTH`。

   1. 以滑鼠右鍵按一下**粗的畫筆**功能表項目，您建立，然後按一下**加入事件處理常式**。 **事件處理常式精靈**隨即出現。

   1. 在 **類別清單** 方塊中的精靈中，選取**CScribbleDoc** ，然後按一下 **新增和編輯**。 此命令會建立名為事件處理常式`CScribbleDoc::OnPenThickWidth`。

   1. 將下列程式碼加入至 `CScribbleDoc::OnPenThickWidth`。

      ```cpp
      // Get a pointer to the ribbon bar
      CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
      ASSERT_VALID(pRibbon);

      CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
          CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
      // Get the selected value
      int nCurSel = pThickComboBox->GetCurSel();
      if (nCurSel>= 0)
      {
          m_nThickWidth = atoi(CStringA(pThickComboBox->GetItem(nCurSel)));
      }

      // Create a new pen using the selected width
      ReplacePen();
      ```

1. 儲存變更，然後建置並執行應用程式。 新的按鈕和下拉式方塊應該會顯示。 請嘗試使用不同的畫筆寬度 scribble。

##  <a name="addcolorbutton"></a> 加入 [畫筆] 面板中的色彩按鈕

接下來，新增[CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md)物件，可讓使用者手繪多邊形的色彩。

### <a name="to-add-a-color-button-to-the-pen-panel"></a>若要加入 [畫筆] 面板中的色彩按鈕

1. 新增色彩按鈕之前，請為其建立的功能表項目。 在 **資源檢視**視窗中，開啟**IDR_SCRIBBTYPE**功能表資源。 按一下 **畫筆**以開啟 畫筆 功能表的功能表項目。 然後按一下**在這裡輸入**並輸入`&Color`。 以滑鼠右鍵按一下您要顯示您輸入的文字**屬性**視窗。 變更要 ID `ID_PEN_COLOR`。

1. 現在加入色彩按鈕。 從**工具箱**，拖曳**色彩按鈕**來**畫筆**面板。

1. 按一下色彩按鈕。 變更**標題**要`Color`，**識別碼**來`ID_PEN_COLOR`， **Simple Look**到`True`，**大型映像索引**到`1`，並**Split Mode**至`False`。

1. 儲存變更，然後建置並執行應用程式。 新的 [色彩] 按鈕應該顯示在**畫筆**面板。 不過，它不能因為它還沒有事件處理常式。 接下來的步驟示範如何加入 [色彩] 按鈕的事件處理常式。

##  <a name="addcolormember"></a> 將色彩成員加入至文件類別

因為原始的 Scribble 應用程式沒有色彩的畫筆，您必須撰寫實作它們。 若要儲存文件中的畫筆顏色將新成員新增至文件類別， `CscribbleDoc`。

### <a name="to-add-a-color-member-to-the-document-class"></a>若要將色彩成員新增至文件類別

1. 在 scribdoc.h，在`CScribbleDoc`類別中，尋找`// Attributes`一節。 新增下列程式碼行的定義之後`m_nThickWidth`資料成員。

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. 每個文件包含一份 stokes，使用者已繪製。 每個筆劃由定義`CStroke`物件。 `CStroke`類別不包含畫筆顏色的相關資訊，因此您必須修改類別。 在 scribdoc.h，在`CStroke`類別中，新增下列程式碼行的定義之後`m_nPenWidth`資料成員。

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. 在 scribdoc.h，加入新`CStroke`建構函式的參數會指定寬度和色彩。 將下行程式碼之後新增`CStroke(UINT nPenWidth);`陳述式。

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. 在 scribdoc.cpp，加入新的實作`CStroke`建構函式。 實作之後新增下列程式碼`CStroke::CStroke(UINT nPenWidth)`建構函式。

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. 變更的第二行`CStroke::DrawStroke`方法，如下所示。

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. 設定預設的畫筆色彩的文件類別。 在 scribdoc.cpp，新增下列行以`CScribbleDoc::InitDocument`之後，`m_nThickWidth = 5;`陳述式。

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. 在 scribdoc.cpp，變更的第一行`CScribbleDoc::NewStroke`如下的方法。

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. 變更的最後一行`CScribbleDoc::ReplacePen`如下的方法。

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. 您加入`m_penColor`上一個步驟中的成員。 現在，建立事件處理常式來設定成員的色彩按鈕。

   1. 在 [**資源檢視**] 視窗中，開啟 IDR_SCRIBBTYPE 功能表資源。

   1. 以滑鼠右鍵按一下**色彩**功能表項目，然後按一下**加入事件處理常式**。 **事件處理常式精靈**隨即出現。

   1. 在 **類別清單**在精靈中，選取方塊**CScribbleDoc** ，然後按一下 **新增和編輯** 按鈕。 此命令會建立`CScribbleDoc::OnPenColor`事件處理常式 stub。

1. 取代為虛設常式`CScribbleDoc::OnPenColor`為下列程式碼的事件處理常式。

   ```cpp
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

1. 儲存變更然後建置並執行應用程式。 您現在可以按下 [色彩] 按鈕，並變更畫筆的顏色。

##  <a name="initpensave"></a> 初始化畫筆及儲存喜好設定

接下來，初始化色彩和畫筆的寬度。 最後，儲存及載入色彩繪製從檔案。

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>初始化位於功能區列的控制項

1. 初始化位於功能區列的畫筆。

   在 scribdoc.cpp，加入下列程式碼`CScribbleDoc::InitDocument`方法之後，`m_sizeDoc = CSize(200,200)`陳述式。

   ```cpp
   // Reset the ribbon UI to its initial values
   CMFCRibbonBar* pRibbon =
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
   ASSERT_VALID(pRibbon);

   CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
       CMFCRibbonColorButton,
       pRibbon->FindByID(ID_PEN_COLOR));

   // Set ColorButton to black
   pColorBtn->SetColor(RGB(0, 0, 0));

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

1. 儲存檔案所繪製的色彩。 在新增 scribdoc.cpp，下列陳述式`CStroke::Serialize`方法之後，`ar << (WORD)m_nPenWidth;`陳述式。

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. 最後，載入從檔案中繪製的色彩。 在中新增下列程式碼，行`CStroke::Serialize`方法之後，`m_nPenWidth = w;`陳述式。

   ```cpp
   ar >> m_penColor;
   ```

1. 現在手繪多邊形的色彩，並將您的繪圖儲存至檔案。

## <a name="conclusion"></a>結論

您已更新 MFC Scribble 應用程式。 當您修改現有的應用程式時，請使用本逐步解說作為指南。

## <a name="see-also"></a>另請參閱

[逐步解說](../mfc/walkthroughs-mfc.md)<br/>
[逐步解說：更新 MFC Scribble 應用程式 (第 1 部分)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
