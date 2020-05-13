---
title: 逐步解說：更新 MFC Scribble 應用程式 (第 2 部分)
ms.date: 04/25/2019
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: bc204a152168accf3731eede8ca9ef960ab121d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360234"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>逐步解說：更新 MFC Scribble 應用程式 (第 2 部分)

本演練[的第 1 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)演示如何向經典 Scribble 應用程式添加 Office Fluent 功能區。 本部分演示如何添加功能區面板和控件,使用者可以使用這些面板和控制項,而不是功能表和命令。

## <a name="prerequisites"></a>Prerequisites

[Visual C++ 範例](../overview/visual-cpp-samples.md)

## <a name="sections"></a><a name="top"></a>部分

本演練的這一部分有以下部分:

- [新增面板區新增新面板](#addnewpanel)

- [新增功能區新增說明面板](#addhelppanel)

- [新增元件到功能區](#addpenpanel)

- [新增顏色按鈕](#addcolorbutton)

- [新增色彩名成員](#addcolormember)

- [初始化筆和儲存喜好選項](#initpensave)

## <a name="adding-new-panels-to-the-ribbon"></a><a name="addnewpanel"></a>新增面板區新增新面板

這些步驟展示如何添加**一個檢視**面板,其中包含兩個控制工具列和狀態列可見性的複選框,**以及包含垂直**方向拆分按鈕的視窗面板,該按鈕控制多文檔介面 (MDI) 視窗的創建和排列。

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>將「檢視」面板和「視窗」面板新增到功能區列

1. 創建名為的`View`面板,其中有兩個複選框來切換狀態列和工具列。

   1. 從**工具箱**,將**面板**拖動到 **「主頁」** 類別。 然後,將兩**個複選框**拖動到面板。

   1. 按一下面板可修改其屬性。 將**標題**變更`View`為 。

   1. 按一個複選框以修改其屬性。 將**ID**`ID_VIEW_TOOLBAR`ID`Toolbar`變更為與**標題**。

   1. 按一個複選框以修改其屬性。 將**ID**`ID_VIEW_STATUS_BAR`ID`Status Bar`變更為與**標題**。

1. 創建具有拆分按鈕`Window`的名為的面板。 當用戶按下拆分按鈕時,快捷功能表將顯示三個已在 Scribble 應用程式中定義的命令。

   1. 從**工具箱**,將**面板**拖動到 **「主頁」** 類別。 然後,將**按鈕**拖動到面板。

   1. 按一下面板可修改其屬性。 將**標題**變更`Window`為 。

   1. 按一下按鈕。 將**標題**變更`Windows`**Keys**為`w`,鍵改變為,**將大圖像索引**變更為`1`,`False`並將**模式分離分數**。 然後按下**選單項目**旁邊的省略號 (**...)** 以開啟 **「專案編輯器」** 對話方塊。

   1. 按下 **「添加**三次」可添加三個按鈕。

   1. 點選第一個按鈕,然後將 **「標題」**`New Window`變更為 「,ID」 變更為**ID**`ID_WINDOW_NEW`。

   1. 點選第二個按鈕,然後將 **「標題」**`Cascade`**ID**`ID_WINDOW_CASCADE`變更為 「ID」,並將「標題」更改為 。

   1. 點選第三個按鈕,然後將 **「標題」**`Tile`變更為 「,`ID_WINDOW_TILE_HORZ`並將**ID**變更為 。

1. 保存更改,然後生成並運行應用程式。 應顯示 **「檢視**」和「**視窗**」 面板。 按下按鈕以確認它們正常工作。

## <a name="adding-a-help-panel-to-the-ribbon"></a><a name="addhelppanel"></a>新增功能區新增說明面板

現在,您可以將在 Scribble 應用程式中定義的兩個功能表項分配給名為「**幫助主題**」和「**關於塗鴉」的**功能區按鈕。 這些按鈕將添加到名為 **「説明**」的新面板中。

### <a name="to-add-a-help-panel"></a>新增說明面板

1. 從**工具箱**,將**面板**拖動到 **「主頁」** 類別。 然後,將兩**個按鈕**拖動到面板上。

1. 按一下面板可修改其屬性。 將**標題**變更`Help`為 。

1. 按一個按鈕。 將**標題**變更為`Help Topics`,**ID**`ID_HELP_FINDER`並將 ID 變更為 。

1. 按一下第二個按鈕。 將**標題**變更為`About Scribble...`,**ID**`ID_APP_ABOUT`並將 ID 變更為 。

1. 保存更改,然後生成並運行應用程式。 應顯示包含兩個功能區按鈕**的幫助**面板。

   > [!IMPORTANT]
   > 按下「**說明主題」** 按鈕時,Scribble 應用程式將打開名為*your_project_name*.chm 的壓縮 HTML (.chm) 幫助檔。 因此,如果專案未命名為 Scribble,則必須將幫助檔重新命名為專案名稱。

## <a name="adding-a-pen-panel-to-the-ribbon"></a><a name="addpenpanel"></a>新增元件到功能區

現在,添加一個面板來顯示控制筆的厚度和顏色的按鈕。 此面板包含一個在粗筆和細筆之間切換的複選框。 其功能類似於 Scribble 應用程式中的 **「厚線**」功能表項。

原始塗鴉應用程式允許使用者從對話框中選擇筆寬度,當用戶單擊功能表上的 **「筆寬度**」時顯示。 由於功能區列有足夠的空間用於新控制項,因此可以使用功能區上的兩個組合框替換對話方塊。 一個組合框調整細筆的寬度,另一個組合框調整粗筆的寬度。

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>將「筆」面板與組合框加入功能區

1. 從**工具箱**,將**面板**拖動到 **「主頁」** 類別。 然後,將**複選框**和兩個**組合框**拖動到面板中。

1. 按一下面板可修改其屬性。 將**標題**變更`Pen`為 。

1. 按一下該核取方塊。 將**標題**變更為`Use Thick`,**ID**`ID_PEN_THICK_OR_THIN`並將 ID 變更為 。

1. 按一個組合框。 將**標題**變更`Thin Pen`為 **,**`ID_PEN_THIN_WIDTH``Drop List`則變更為 ,**鍵到**`1;2;3;4;5;6;7;8;9;`,**資料**變更`2`為 , 並將**文字**變更為 。

1. 按一個組合框。 將**標題**變更`Thick Pen`為 **,**`ID_PEN_THICK_WIDTH``Drop List`則變更為 ,**鍵到**`5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`,**資料**變更`5`為 , 並將**文字**變更為 。

1. 新的組合框不對應於任何現有的功能表項,因此您必須為每個筆選項創建一個功能表項。

   1. 在 **「資源檢視」** 視窗中,打開**IDR_SCRIBBTYPE**選單資源。

   1. 按下 **「筆」** 可打開筆選單。 然後按下 **「 在此鍵入」** 鍵`Thi&n Pen`入 。

   1. 右鍵按下鍵入的文字以開啟 **「屬性」** 視窗,然後將 ID`ID_PEN_THIN_WIDTH`屬性變更為 。

   1. 為每個筆菜單項創建事件處理程式。 右鍵按下您建立的**Th&n 筆**選單項,然後單擊「**添加事件處理程式**」 "。 將顯示**事件處理程式精靈**。

   1. 在精靈中的 **「類別」列表**框中,選擇**CScribbleDoc,** 然後按下「**添加和編輯**」 。 這個指令建立名為的事件處理程式`CScribbleDoc::OnPenThinWidth`。

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

1. 接下來,為粗筆創建功能表項和事件處理程式。

   1. 在 **「資源檢視」** 視窗中,打開**IDR_SCRIBBTYPE**選單資源。

   1. 按下 **「筆」** 可打開筆選單。 然後按下 **「 在此鍵入」** 鍵`Thic&k Pen`入 。

   1. 右鍵按下鍵入的文字以顯示 **「屬性」** 視窗。 將識別碼`ID_PEN_THICK_WIDTH`屬性變更為 。

   1. 右鍵按下您建立的 **「厚筆」** 選單項,然後按下「**添加事件處理程式**」 。。 將顯示**事件處理程式精靈**。

   1. 在精靈的 **「類別」列表**框中,選擇**CScribbleDoc,** 然後按下「**添加和編輯**」 。 這個指令建立名為的事件處理程式`CScribbleDoc::OnPenThickWidth`。

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

1. 保存更改,然後生成並運行應用程式。 應顯示新的按鈕和組合框。 嘗試使用不同的筆寬進行塗鴉。

## <a name="adding-a-color-button-to-the-pen-panel"></a><a name="addcolorbutton"></a>新增面板加入顏色按鈕

接下來,添加一個[CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md)物件,允許使用者以顏色塗鴉。

### <a name="to-add-a-color-button-to-the-pen-panel"></a>加入「筆」面板加入顏色按鈕

1. 在添加顏色按鈕之前,請為其創建功能表項。 在 **「資源檢視」** 視窗中,打開**IDR_SCRIBBTYPE**選單資源。 按下 **「筆」** 選單項以打開筆選單。 然後按下 **「 在此鍵入」** 鍵`&Color`入 。 右鍵按下鍵入的文字以顯示 **「屬性」** 視窗。 將識別碼變更為 `ID_PEN_COLOR`。

1. 現在添加顏色按鈕。 從**工具箱**「,將 **」顏色按鈕**「拖動到 **」筆「** 面板」。

1. 按一下顏色按鈕。 將**標題**變更`Color`為 **,ID** `ID_PEN_COLOR``True`變更為 「**簡單搜尋**」 ,**將大圖像索引**變更為`1`,將 **「分割模式」** 改變為`False`。

1. 保存更改,然後生成並運行應用程式。 新的顏色按鈕應顯示在 **「筆」** 面板上。 但是,它不能使用它,因為它還沒有一個事件處理程式。 接下來的步驟演示如何為顏色按鈕添加事件處理程式。

## <a name="adding-a-color-member-to-the-document-class"></a><a name="addcolormember"></a>新增色彩名成員

由於原始 Scribble 應用程式沒有彩色筆,因此必須為其編寫實現。 要儲存文件的筆顏色,向文件類別新增新成員`CscribbleDoc`。

### <a name="to-add-a-color-member-to-the-document-class"></a>新增色彩名成員

1. 在 scribdoc.h`CScribbleDoc`中 ,在`// Attributes`班級中 ,找到該部分。 在`m_nThickWidth`定義數據成員後添加以下代碼行。

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. 每個文檔都包含使用者已繪製的引點清單。 每個描邊都由`CStroke`物件定義。 類`CStroke`不包括有關筆顏色的資訊,因此必須修改類。 在 scribdoc.h`CStroke`中 ,在類`m_nPenWidth`中,在數據成員定義之後添加以下代碼行。

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. 在 scribdoc.h`CStroke`中, 添加一個新構造函數,其參數指定寬度和顏色。 在`CStroke(UINT nPenWidth);`語句之後添加以下代碼行。

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. 在 scribdoc.cpp 中,`CStroke`添加新 構造函數的實現。 在`CStroke::CStroke(UINT nPenWidth)`建構函數實現後添加以下代碼。

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. 更改`CStroke::DrawStroke`方法的第二行,如下所示。

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. 設置文檔類的預設筆顏色。 在 scribdoc.cpp 中`CScribbleDoc::InitDocument``m_nThickWidth = 5;`,在 語句之後向 添加以下行。

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. 在 scribdoc.cpp 中`CScribbleDoc::NewStroke`,將 方法的第一行更改為以下內容。

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. 將方法的最後一`CScribbleDoc::ReplacePen`行更改為以下內容。

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. 您在上`m_penColor`一步中添加了該成員。 現在,為設置成員的顏色按鈕創建事件處理程式。

   1. 在 **「資源檢視」** 視窗中,打開IDR_SCRIBBTYPE功能表資源。

   1. 右鍵按下 **「顏色」** 選單項,然後按下「**添加事件處理程式**」 。。 將顯示**事件處理程式精靈**。

   1. 在精靈中的 **「類別」列表**框中,選擇**CScribbleDoc,** 然後按下「**添加和編輯**」按鈕。 該命令建立`CScribbleDoc::OnPenColor`事件處理程式存根。

1. 將事件處理程式的`CScribbleDoc::OnPenColor`存根替換為以下代碼。

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

1. 保存更改,然後生成並運行應用程式。 現在,您可以按顏色按鈕並更改筆的顏色。

## <a name="initializing-pens-and-saving-preferences"></a><a name="initpensave"></a>初始化筆和儲存喜好選項

接下來,初始化筆的顏色和寬度。 最後,從檔保存並載入彩色圖形。

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>在功能區列上初始化控制項

1. 初始化功能區列上的筆。

   在`CScribbleDoc::InitDocument``m_sizeDoc = CSize(200,200)`語句之後的方法中將以下代碼添加到 scribdoc.cpp 中。

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

1. 將彩色圖形保存到檔中。 在`CStroke::Serialize``ar << (WORD)m_nPenWidth;`語句之後的方法中將以下語句添加到 scribdoc.cpp。

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. 最後,從檔載入彩色圖形。 在`CStroke::Serialize``m_nPenWidth = w;`語句之後的方法中添加以下代碼行。

   ```cpp
   ar >> m_penColor;
   ```

1. 現在,以彩色塗鴉,並將繪圖保存到檔中。

## <a name="conclusion"></a>結論

您已更新 MFC 塗鴉應用程式。 修改現有應用程式時,請本演練作為指南。

## <a name="see-also"></a>另請參閱

[逐步解說](../mfc/walkthroughs-mfc.md)<br/>
[逐步解說：更新 MFC Scribble 應用程式 (第 1 部分)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
