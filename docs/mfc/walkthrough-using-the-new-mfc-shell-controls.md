---
title: "逐步解說： 使用新的 MFC Shell 控制項 |Microsoft 文件"
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
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be882671da836f7d96f4c726753d6235735f363d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>逐步解說：使用新的 MFC Shell 控制項
在此逐步解說中，您會建立類似檔案總管的應用程式。 您將建立包含兩個窗格的視窗。 左的窗格將包含[CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md)桌面上顯示階層式檢視中的物件。 在右窗格會包含[CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md)的左窗格中選取的資料夾中顯示的檔案。  
  
## <a name="prerequisites"></a>必要條件  
 本逐步解說假設您有設定[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]使用**一般開發設定**。 如果您有些使用不同的開發設定，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]預設可能不會顯示我們在本逐步解說中使用的 windows。  
  
### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>若要使用 MFC 應用程式精靈建立新的 MFC 應用程式  
  
1.  使用**MFC 應用程式精靈**建立新的 MFC 應用程式。 若要從執行精靈，**檔案**功能表中選取**新增**，然後選取**專案**。 **新專案**會顯示對話方塊。  
  
2.  在**新專案**對話方塊方塊中，展開  **Visual c + +**節點**專案類型**窗格，然後選取**MFC**。 然後，在**範本**窗格中，選取**MFC 應用程式**。 輸入專案的名稱，例如`MFCShellControls`按一下**確定**。 **MFC 應用程式精靈**隨即出現。  
  
3.  在**MFC 應用程式精靈**對話方塊中，按一下 **下一步**。 **應用程式類型**窗格會顯示。  
  
4.  在**應用程式類型**窗格下**應用程式類型**，清除**索引標籤式文件**選項。 接下來，選取**單一文件**選取**文件/檢視架構支援**。 在下**專案樣式**，選取**Visual Studio**，以及從**視覺化樣式和色彩**下拉式清單中，選取**Office 2007 （藍色主題）**. 所有其他選項保持不變。 按一下**下一步**顯示**複合文件支援**窗格。  
  
5.  在**複合文件支援**窗格中，選取**無**。 按一下**下一步**顯示**文件樣板字串**窗格。  
  
6.  不進行任何變更**文件樣板字串**窗格。 按一下**下一步**顯示**資料庫支援**窗格。  
  
7.  在**資料庫支援**窗格中，選取**無**由於此應用程式不會使用資料庫。 按一下**下一步**顯示**使用者介面功能**窗格。  
  
8.  在**使用者介面功能** 窗格中，請確定**使用功能表和工具列**選取選項。 所有其他選項保持不變。 按一下**下一步**顯示**進階功能**窗格。  
  
9. 在**進階功能**窗格下**進階功能**，只選取**ActiveX 控制項**和**通用控制項資訊清單**。 在下**進階框架窗格**，只選取**瀏覽窗格**選項。 這會導致精靈以建立與視窗的左邊窗格`CMFCShellTreeCtrl`已內嵌。 按一下**下一步**顯示**產生的類別**窗格。  
  
10. 我們不會進行任何變更**產生的類別**窗格。 因此，可以按一下**完成**建立新的 MFC 專案。  
  
11. 請確認應用程式已成功建立，方式是建立並執行它。 若要建置應用程式，從**建置**功能表中選取**建置方案**。 如果應用程式建置成功，請選取執行應用程式**開始偵錯**從**偵錯**功能表。  
  
     精靈會自動建立具有標準功能表列、 標準工具列、 標準的狀態列，以及 outlook 功能區與視窗左邊的應用程式**資料夾**檢視和**行事曆**檢視.  
  
### <a name="to-add-the-shell-list-control-to-the-document-view"></a>若要將殼層清單控制項加入文件檢視  
  
1.  在本節中，您將加入的執行個體`CMFCShellListCtrl`精靈所建立的檢視。 按兩下 MFCShellControlsView.h 中的開啟檢視標頭檔**方案總管 中**。  
  
     找出`#pragma once`最上方的標頭檔指示詞。 下面將加入此程式碼，包含的標頭檔，請立即`CMFCShellListCtrl`:  
  
 ```  
    #include <afxShellListCtrl.h>  
 ```  
  
     現在，加入成員變數的型別`CMFCShellListCtrl`。 首先，尋找下列註解標頭檔：  
  
 '' * / / 產生訊息對應函式  
 ```  
  
     Immediately above that comment add this code:  
  
 ```  
    私用： CMFCShellListCtrl m_wndList;  
 ```  
  
2.  The **MFC Application Wizard** already created a `CMFCShellTreeCtrl` object in the `CMainFrame` class, but it is a protected member. We will access this object later. Therefore, create an accessor for it now. Open the MainFrm.h header file by double-clicking it in the **Solution Explorer**. Locate the following comment:  
  
 ``` *// Attributes  
 ```  
  
     立即在其下方加入下列方法宣告：  
  
 ```  
    public: 
    CMFCShellTreeCtrl& GetShellTreeCtrl();

 ```  
  
     接下來，開啟 MainFrm.cpp 原始程式檔中按兩下**方案總管 中**。 在該檔案最下方，加入下列方法定義：  
  
 ```  
    CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()  
 {  
    return m_wndTree;  
 }  
 ```  
  
3.  現在我們更新`CMFCShellControlsView`類別處理**WM_CREATE** windows 訊息。 開啟 MFCShellControlsView.h 標頭檔，然後按一下這行程式碼：  
  
 ```  
    class CMFCShellControlsView : public CView  
 ```  
  
     接下來，在**屬性**視窗中，按一下 **訊息**圖示。 向下捲動，直到您找到**WM_CREATE**訊息。 從下拉式清單旁邊的清單**WM_CREATE**，選取**\<新增 > OnCreate**。 這會為我們的訊息處理常式，並且 MFC 訊息對應會自動更新。  
  
     在`OnCreate`方法現在我們將建立我們`CMFCShellListCtrl`物件。 尋找`OnCreate`中 MFCShellControlsView.cpp 方法定義來源檔案，並以下列程式碼取代它的實作：  
  
 ```  
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)  
 {  
    if (CView::OnCreate(lpCreateStruct) == -1)  
    return -1;  
 
    CRect rectDummy (0,
    0,
    0,
    0);

    m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,  
    rectDummy,
    this,
    1);

 
    return 0;  
 }  
 ```  
  
4.  重複上述步驟，但針對**WM_SIZE**訊息。 這會導致您的應用程式檢視，來重新繪製每次使用者變更應用程式視窗的大小。 取代為定義`OnSize`方法取代下列程式碼：  
  
 ```  
    void CMFCShellControlsView::OnSize(UINT nType,
    int cx,
    int cy)  
 {  
    CView::OnSize(nType,
    cx,
    cy);

    m_wndList.SetWindowPos(NULL, -1, -1,
    cx,
    cy,  
    SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);

 }  
 ```  
  
5.  最後一個步驟是將連線`CMFCShellTreeCtrl`和`CMFCShellListCtrl`物件使用[CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist)方法。 呼叫這個方法之後,`CMFCShellListCtrl`會自動顯示在選取之項目的內容`CMFCShellTreeCtrl`。 我們會執行此作業`OnActivateView`方法，它會覆寫從[CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview)。  
  
     在 MFCShellControlsView.h 標頭檔中，內部`CMFCShellControlsView`類別宣告中，加入下列方法宣告：  
  
 ```  
    protected: 
    virtual void OnActivateView(BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView);

 ```  
  
     接下來，將此方法的定義加入至 MFCShellControlsView.cpp 原始程式檔：  
  
 ```  
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView)   
 {  
    if (bActivate&& AfxGetMainWnd() != NULL)  
 {  
 ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);

 }  
 
    CView::OnActivateView(bActivate,
    pActivateView,
    pDeactiveView);

 }  
 ```  
  
     因為我們將會呼叫方法，從`CMainFrame`類別中，我們必須加入`#include`MFCShellControlsView.cpp 原始程式檔頂端指示詞：  
  
 ```  
    #include "MainFrm.h"  
 ```  
  
6.  請確認應用程式已成功建立，方式是建立並執行它。 若要建置應用程式，從**建置**功能表中選取**建置方案**。 如果應用程式建置成功，會將它執行方法是選取**開始偵錯**從**偵錯**功能表。  
  
     您現在應該會看到在所選取的項目的詳細資料`CMFCShellTreeCtrl`[檢視] 窗格中。 當您按一下中的節點`CMFCShellTreeCtrl`、`CMFCShellListCtrl`會自動更新。 同樣地，如果您按兩下資料夾中的`CMFCShellListCtrl`、`CMFCShellTreeCtrl`應自動更新。  
  
     以滑鼠右鍵按一下任何項目樹狀結構控制項中，或在清單控制項中。 請注意，因為如果您使用實際的檔案總管 取得相同的內容功能表。  
  
## <a name="next-steps"></a>後續步驟  
  
-   精靈所建立的 outlook 功能區與這兩個**資料夾**窗格和**行事曆**窗格。 可能不會是合理的作法**行事曆**總管 視窗中的窗格。 因此，現在移除窗格。  
  
-   `CMFCShellListCtrl`支援在不同模式中，檢視檔案，例如**大圖示**，**小圖示**，**清單**，和**詳細資料**。 更新您的應用程式實作這項功能。 提示： 請參閱[Visual c + + 範例](../visual-cpp-samples.md)。  
  
## <a name="see-also"></a>請參閱  
 [逐步解說](../mfc/walkthroughs-mfc.md)

