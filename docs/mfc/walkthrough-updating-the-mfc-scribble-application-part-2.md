---
title: 逐步解說： 更新 MFC Scribble 應用程式 （第 2 部分） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: eae1dd3c1662aafb6b52d2ecb821e073adc0bfd5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385387"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>逐步解說：更新 MFC Scribble 應用程式 (第 2 部分)
[第 1 部分](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)本逐步解說示範如何將 Office Fluent 功能區加入至傳統的 Scribble 應用程式。 此部分顯示如何加入功能區面板和控制項，使用者可以使用而不是功能表和命令。  
  
## <a name="prerequisites"></a>必要條件  
 [Visual C++ 範例](../visual-cpp-samples.md)  
  
##  <a name="top"></a> 章節  
 此部分的逐步解說包含下列各節：  
  
- [在功能區中加入新的面板](#addnewpanel)  
  
- [在功能區加入說明面板](#addhelppanel)  
  
- [在功能區加入畫筆面板](#addpenpanel)  
  
- [加入功能區色彩按鈕](#addcolorbutton)  
  
- [將 Color 成員加入至文件類別](#addcolormember)  
  
- [初始化畫筆及儲存喜好設定](#initpensave)  
  
##  <a name="addnewpanel"></a> 在功能區中加入新的面板  
 這些步驟顯示如何新增**檢視**面板包含兩個核取方塊，以控制可見性的工具列和狀態列，以及**視窗**包含垂直方向的分割面板控制建立和排列多重文件介面 (MDI) 視窗的按鈕。  
  
#### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>若要將檢視面板和視窗面板加入至功能區列  
  
1.  建立名為面板`View`，其中包含兩個核取方塊的切換狀態 列和工具列。  
  
    1.  從**工具箱**，拖曳**面板**至**首頁**類別目錄。 拖放兩**核取方塊**面板。  
  
    2.  按一下要修改其內容的面板。 變更**標題**至`View`。  
  
    3.  按一下要修改其屬性的第一個核取方塊。 變更**識別碼**至`ID_VIEW_TOOLBAR`和**標題**至`Toolbar`。  
  
    4.  按一下第二個核取方塊來修改其屬性。 變更**識別碼**至`ID_VIEW_STATUS_BAR`和**標題**至`Status Bar`。  
  
2.  建立名為面板`Window`具有分割按鈕。 當使用者按一下分割按鈕時，快顯功能表就會顯示已定義在 Scribble 應用程式中的三個命令。  
  
    1.  從**工具箱**，拖曳**面板**至**首頁**類別目錄。 然後將拖曳**按鈕**面板。  
  
    2.  按一下要修改其內容的面板。 變更**標題**至`Window`。  
  
    3.  按一下按鈕。 變更**標題**至`Windows`，**金鑰**至`w`，**大型影像索引**至`1`，和**Split Mode**若要`False`。 然後按一下省略符號 (**...**) 旁邊**功能表項目**開啟**項目編輯器** 對話方塊。  
  
    4.  按一下**新增**三次，以新增三個按鈕。  
  
    5.  按一下第一個按鈕，然後變更**標題**至`New Window`，和**識別碼**至`ID_WINDOW_NEW`。  
  
    6.  按一下第二個按鈕，然後變更**標題**至`Cascade`，和**識別碼**至`ID_WINDOW_CASCADE`。  
  
    7.  按一下第三個按鈕，然後變更**標題**至`Tile`，和**識別碼**至`ID_WINDOW_TILE_HORZ`。  
  
3.  儲存變更，然後建置並執行應用程式。 **檢視**和**視窗**應該顯示面板。 按一下按鈕，以確認它們可以正常運作。  
  
 [[區段](#top)]  
  
##  <a name="addhelppanel"></a> 在功能區加入說明面板  
 現在，您可以將名為功能區按鈕 Scribble 應用程式中所定義的兩個功能表項目指派**說明主題**和**有關 Scribble**。 加入了新的面板，名為按鈕**協助**。  
  
#### <a name="to-add-a-help-panel"></a>若要加入說明面板  
  
1.  從**工具箱**，拖曳**面板**至**首頁**類別目錄。 拖放兩**按鈕**面板。  
  
2.  按一下要修改其內容的面板。 變更**標題**至`Help`。  
  
3.  按一下第一個按鈕。 變更**標題**至`Help Topics`，和**識別碼**至`ID_HELP_FINDER`。  
  
4.  按一下第二個按鈕。 變更**標題**至`About Scribble...`，和**識別碼**至`ID_APP_ABOUT`。  
  
5.  儲存變更，然後建置並執行應用程式。 A**協助**應該會顯示包含兩個功能區按鈕的面板。  
  
    > [!IMPORTANT]
    >  當您按一下**說明主題**按鈕，Scribble 應用程式會開啟名為的壓縮 (.chm) HTML 說明檔*your_project_name*。 有 因此，如果您的專案不是 Scribble，您必須將檔案重新命名說明您的專案名稱。  
  
 [[區段](#top)]  
  
##  <a name="addpenpanel"></a> 在功能區加入畫筆面板  
 現在，加入工作面板顯示按鈕，以控制粗細和畫筆的顏色。 此面板包含粗的精簡畫筆來切換核取方塊。 其功能類似**粗線**Scribble 應用程式中的功能表項目。  
  
 原始 Scribble 應用程式可讓使用者選取使用者按一下時，會出現在對話方塊中的畫筆寬度**畫筆寬度**功能表上。 功能區列有足夠空間可存放新的控制項，因為您可以使用功能區上的兩個下拉式方塊來取代對話方塊。 一個下拉式方塊會調整的精簡型的畫筆寬度和下拉式方塊調整粗的畫筆寬度。  
  
#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>若要加入至功能區畫筆面板和下拉式方塊  
  
1.  從**工具箱**，拖曳**面板**至**首頁**類別目錄。 然後將拖曳**核取方塊**和兩個**下拉式方塊**面板。  
  
2.  按一下要修改其內容的面板。 變更**標題**至`Pen`。  
  
3.  按一下核取方塊。 變更**標題**至`Use Thick`，和**識別碼**至`ID_PEN_THICK_OR_THIN`。  
  
4.  按一下第一個下拉式方塊。 變更**標題**至`Thin Pen`，**識別碼**至`ID_PEN_THIN_WIDTH`，**文字**至`2`，**類型**至`Drop List`，和**資料**至`1;2;3;4;5;6;7;8;9;`。  
  
5.  按一下第二個下拉式方塊。 變更**標題**至`Thick Pen`，**識別碼**至`ID_PEN_THICK_WIDTH`，**文字**至`5`，**類型**至`Drop List`，和**資料**至`5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`。  
  
6.  新的下拉式方塊未對應到任何現有的功能表項目。 因此，您必須建立畫筆的每個選項的功能表項目。  
  
    1.  在**資源檢視**視窗中，開啟 IDR_SCRIBBTYPE 功能表資源。  
  
    2.  按一下**畫筆**開啟 p**en**功能表。 然後按一下 **在這裡輸入**和型別`Thi&n Pen`。  
  
    3.  以滑鼠右鍵按一下您剛才輸入開啟的文字**屬性**視窗，然後再變更 ID 屬性`ID_PEN_THIN_WIDTH`。  
  
    4.  您也必須建立事件處理常式的每個畫筆功能表項目。 以滑鼠右鍵按一下**這個 & n 畫筆**您剛剛建立，然後按一下功能表項目**加入事件處理常式**。 **事件處理常式精靈**隨即出現。  
  
    5.  在**類別清單**在精靈中，選取方塊**CScribbleDoc** ，然後按一下 **新增和編輯**。 這會建立名為事件處理常式`CScribbleDoc::OnPenThinWidth`。  
  
    6.  將下列程式碼加入至 `CScribbleDoc::OnPenThinWidth`。  
  
 ``` *取得指標的功能區列 CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())]-> [GetRibbonBar();ASSERT_VALID(pRibbon);*/ / 取得指標的精簡型的寬度下拉式方塊 CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST (CMFCRibbonComboBox，pRibbon]-> [FindByID(ID_PEN_THIN_WIDTH)); * //Get 選取的值  
    int nCurSel = pThinComboBox]-> [GetCurSel();如果 (nCurSel > = 0)  
{  
m_nThinWidth = atoi (pThinComboBox]-> [GetItem(nCurSel));

 } * / / 建立新的畫筆使用選取的寬度  
    ReplacePen();

 ```  
  
7.  Next, create a menu item and event handlers for the thick pen.  
  
    1.  In the **Resource View** window, open the IDR_SCRIBBTYPE menu resource.  
  
    2.  Click **Pen** to open the pen menu. Then click **Type Here** and type `Thic&k Pen`.  
  
    3.  Right-click the text that you just typed to display the **Properties** window. Change the ID property to `ID_PEN_THICK_WIDTH`.  
  
    4.  Right-click the **Thick Pen** menu item that you just created and then click **Add Event Handler**. The **Event Handler Wizard** is displayed.  
  
    5.  In the **Class list** box of the wizard, select **CScribbleDoc** and then click **Add and Edit**. This creates an event handler named `CScribbleDoc::OnPenThickWidth`.  
  
    6.  Add the following code to `CScribbleDoc::OnPenThickWidth`.  
  
 ``` *// Get a pointer to the ribbon bar  
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
ASSERT_VALID(pRibbon);

 CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
    CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
*// Get the selected value  
    int nCurSel = pThickComboBox->GetCurSel();
if (nCurSel>= 0)  
 {  
    m_nThickWidth = atoi(pThickComboBox->GetItem(nCurSel));

 } *// Create a new pen using the selected width  
    ReplacePen();

 ```  
  
8.  儲存變更，然後建置並執行應用程式。 應該會顯示新的按鈕和下拉式方塊。 請嘗試使用不同的畫筆寬度 scribble。  
  
 [[區段](#top)]  
  
##  <a name="addcolorbutton"></a> 加入 [畫筆] 面板中的色彩按鈕  
 接下來，加入[CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md)物件，讓使用者手繪多邊形的色彩。  
  
#### <a name="to-add-a-color-button-to-the-pen-panel"></a>若要加入的色彩按鈕畫筆面板  
  
1.  新增 [色彩] 按鈕之前，請為其建立功能表項目。 在**資源檢視**視窗中，開啟 IDR_SCRIBBTYPE 功能表資源。 按一下**畫筆**以開啟 [畫筆] 功能表的功能表項目。 然後按一下 **在這裡輸入**和型別`&Color`。 以滑鼠右鍵按一下您剛才輸入顯示的文字**屬性**視窗。 變更要識別碼`ID_PEN_COLOR`。  
  
2.  現在加入 [色彩] 按鈕。 從**工具箱**，拖曳**色彩按鈕**至**畫筆**面板。  
  
3.  按一下色彩按鈕。 變更**標題**至`Color`，**識別碼**至`ID_PEN_COLOR`， **SimpleLook**至`True`，**大型影像索引**至`1`，和**Split Mode**至`False`。  
  
4.  儲存變更，然後建置並執行應用程式。 新的色彩按鈕應該顯示在**畫筆**面板。 不過，它不能因為它還沒有的事件處理常式。 接下來的步驟示範如何加入 [色彩] 按鈕的事件處理常式。  
  
 [[區段](#top)]  
  
##  <a name="addcolormember"></a> 將 Color 成員加入至文件類別  
 因為原始 Scribble 應用程式並沒有色彩畫筆，您必須為它們撰寫實作。 若要儲存文件的畫筆顏色，將新成員加入文件類別， `CscribbleDoc.`  
  
#### <a name="to-add-a-color-member-to-the-document-class"></a>若要將 color 成員加入至文件類別  
  
1.  在 scribdoc.h，在`CScribbleDoc`類別中，尋找`// Attributes`> 一節。 定義後面加入下列程式碼`m_nThickWidth`資料成員。  
  
 '' * / / 目前的畫筆色彩  
    COLORREF m_penColor;  
 ```  
  
2.  Every document contains a list of stokes that the user has already drawn. Every stroke is defined by a `CStroke` object. The `CStroke` class does not include information about pen color. Therefore, you must modify the class. In scribdoc.h, in the `CStroke` class, add the following lines of code after the definition of the `m_nPenWidth` data member.  
  
 ``` *// Pen color for the stroke  
    COLORREF m_penColor;  
 ```  
  
3.  在 scribdoc.h，加入新`CStroke`建構函式的參數指定寬度和色彩。 加入下列程式碼之後`CStroke(UINT nPenWidth);`陳述式。  
  
 ```  
    CStroke(UINT nPenWidth, COLORREF penColor);

 ```  
  
4.  在 scribdoc.cpp，加入新的實作`CStroke`建構函式。 實作之後加入下列程式碼`CStroke::CStroke(UINT nPenWidth)`建構函式。  
  
 '' * / / 建構函式的使用中文件的目前寬度和色彩  
    CStroke::CStroke （UINT nPenWidth、 COLORREF penColor）  
 {  
    m_nPenWidth = nPenWidth;  
    m_penColor = penColor;  
    m_rectBounding.SetRectEmpty();

 }  
 ```  
  
5.  Change the second line of the `CStroke::DrawStroke` method as follows.  
  
 ```  
    如果 (！ penStroke.CreatePen (PS_SOLID，m_nPenWidth、 m_penColor))  
 ```  
  
6.  Set the default pen color for the document class. In scribdoc.cpp, add the following lines to `CScribbleDoc::InitDocument`, after the `m_nThickWidth = 5;` statement.  
  
 ``` *// default pen color is black  
    m_penColor = RGB(0,
    0,
    0);

 ```  
  
7.  在 scribdoc.cpp，變更的第一行`CScribbleDoc::NewStroke`下的方法。  
  
 ```  
    CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);

 ```  
  
8.  變更的最後一行`CScribbleDoc::ReplacePen`下的方法。  
  
 ```  
    m_penCur.CreatePen(PS_SOLID,
    m_nPenWidth,
    m_penColor);

 ```  
  
9. 您加入`m_penColor`上一個步驟中的成員。 現在，建立事件處理常式來設定成員的色彩按鈕。  
  
    1.  在**資源檢視**視窗中，開啟 IDR_SCRIBBTYPE 功能表資源。  
  
    2.  以滑鼠右鍵按一下**色彩**功能表項目，然後按一下**加入事件處理常式**。 **事件處理常式精靈**隨即出現。  
  
    3.  在**類別清單**在精靈中，選取方塊**CScribbleDoc** ，然後按一下 [**新增和編輯**] 按鈕。 這會建立`CScribbleDoc::OnPenColor`事件處理常式虛設常式。  
  
10. 取代為虛設常式`CScribbleDoc::OnPenColor`為下列程式碼的事件處理常式。  
  
 ```  
    void CScribbleDoc::OnPenColor()  
 { *// Change pen color to reflect color button's current selection  
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
ASSERT_VALID(pRibbon);

 CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
    CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

    m_penColor = pColorBtn->GetColor();
*// Create new pen using the selected color  
    ReplacePen();

 }  
 ```  
  
11. 儲存變更然後建置並執行應用程式。 您應該能夠按下 [色彩] 按鈕，並變更畫筆的顏色。  
  
 [[區段](#top)]  
  
##  <a name="initpensave"></a> 初始化畫筆及儲存喜好設定  
 接下來，初始化的畫筆寬度與色彩。 最後，儲存及載入色彩繪製從檔案。  
  
#### <a name="to-initialize-controls-on-the-ribbon-bar"></a>初始化功能區列上的控制項  
  
1.  初始化在功能區列上的畫筆。  
  
     中，將下列程式碼加入至 scribdoc.cpp，`CScribbleDoc::InitDocument`方法，之後`m_sizeDoc = CSize(200,200)`陳述式。  
  
 ``` *重設為其初始值 CMFCRibbonBar 的功能區 UI* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())]-> [GetRibbonBar();ASSERT_VALID(pRibbon);

 CMFCRibbonColorButton * pColorBtn = DYNAMIC_DOWNCAST (CMFCRibbonColorButton，pRibbon]-> [FindByID(ID_PEN_COLOR));* / 設定為黑色 ColorButton  
    pColorBtn]-> [SetColor (RGB （0，0，0）);

 CMFCRibbonComboBox * pThinComboBox = DYNAMIC_DOWNCAST (CMFCRibbonComboBox，pRibbon]-> [FindByID(ID_PEN_THIN_WIDTH));* / 設定為 2 的精簡畫筆下拉式方塊  
    pThinComboBox]-> [SelectItem(1);

 CMFCRibbonComboBox * pThickComboBox = DYNAMIC_DOWNCAST (CMFCRibbonComboBox，pRibbon]-> [FindByID(ID_PEN_THICK_WIDTH));* / 設定為 5 的粗畫筆下拉式方塊  
    pThickComboBox]-> [SelectItem(0);

 ```  
  
2.  Save a color drawing to a file. Add the following statement to scribdoc.cpp, in the `CStroke::Serialize` method, after the `ar << (WORD)m_nPenWidth;` statement.  
  
 ```  
    ar << (COLORREF) m_penColor;  
 ```  
  
3.  Finally, load a color drawing from a file. Add the following line of code, in the `CStroke::Serialize` method, after the `m_nPenWidth = w;` statement.  
  
 ```  
    ar >> m_penColor;  
 ```  
  
4.  Now scribble in color and save your drawing to a file.  
  
 [[Sections](#top)]  
  
## Conclusion  
 You have updated the MFC Scribble application. Use this walkthrough as a guide when you modify your existing applications.  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)   
 [Walkthrough: Updating the MFC Scribble Application (Part 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)

