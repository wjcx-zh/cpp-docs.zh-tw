---
title: 逐步解說： 使用新的 MFC Shell 控制項 |Microsoft Docs
ms.custom: ''
ms.date: 09/20/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e1cffc9d1231cd9e8e91b445f05eb7dbbbc4ce4
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169615"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>逐步解說：使用新的 MFC Shell 控制項

在此逐步解說中，您會建立類似檔案總管的應用程式。 您將建立包含兩個窗格的視窗。 左的窗格會包含[CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md)階層式檢視中顯示您的桌面物件。 右窗格會包含[CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md)的資料夾中，選取左窗格中顯示的檔案。

## <a name="prerequisites"></a>必要條件

本逐步解說假設已設定 Visual Studio 來使用**一般開發設定**。 如果您使用不同的開發設定，我們在本逐步解說中使用某些 Visual Studio 視窗可能不是預設顯示。

### <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>若要使用 MFC 應用程式精靈建立新的 MFC 應用程式

1. 使用**MFC 應用程式精靈**建立新的 MFC 應用程式。 若要執行精靈時，從**檔案**功能表中，選取**新增**，然後選取**專案**。 **新的專案**對話方塊會隨即顯示。

1. 在**新的專案**對話方塊方塊中，展開**Visual c + +** 節點中的**專案類型**窗格，然後選取**MFC**。 然後，在**範本**窗格中，選取**MFC 應用程式**。 輸入專案名稱，例如`MFCShellControls`，按一下  **確定**。 在後**MFC 應用程式精靈**出現時，請使用下列選項：

    1. 在上**應用程式類型**窗格下方**應用程式類型**，清除**索引標籤式文件**選項。 接下來，選取**單一文件**，然後選取**文件/檢視架構支援**。 底下**專案樣式**，選取**Visual Studio**，以及從**視覺化樣式和色彩**下拉式清單中，選取**Office 2007 （藍色佈景主題）**. 

    1. 在 **複合文件支援**窗格中，選取**無**。

    1. 不進行任何變更**文件樣板字串**窗格。

    1. 在 **資料庫支援**窗格 (Visual Studio 2015 和較舊版本)，選取**無**因為此應用程式不會使用資料庫。 

    1. 在 [**使用者介面功能**] 窗格中，請確定**使用功能表列和工具列**選項。 不，請保留所有其他選項。 

    1. 上**進階功能**窗格底下**進階功能**，選取 僅**ActiveX 控制項**並**通用控制項資訊清單**。 底下**進階框架窗格**，選取 僅**瀏覽窗格**選項。 這會導致精靈以建立與視窗的左邊窗格`CMFCShellTreeCtrl`已內嵌。 

    1. 我們不會進行任何變更**產生的類別**窗格。 因此，請按一下**完成**建立新的 MFC 專案。

1. 請確認應用程式已成功建立，建置並執行它。 若要建置應用程式，從**建置**功能表中，選取**建置方案**。 如果應用程式建置成功，請選取執行應用程式**開始偵錯**從**偵錯**功能表。

   精靈會自動建立的應用程式，具有標準功能表列、 標準工具列、 標準的狀態列，以及 Outlook 功能區與視窗的左邊**資料夾**檢視和**行事曆**檢視.

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>殼層清單控制項加入文件檢視

1. 在本節中，您將加入的執行個體`CMFCShellListCtrl`精靈所建立的檢視。 按兩下以開啟檢視標頭檔**MFCShellControlsView.h**中**方案總管 中**。

   找出`#pragma once`指示詞標頭檔的頂端附近。 下面將新增此程式碼来包含的標頭檔，請立即`CMFCShellListCtrl`:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   現在加入成員變數的型別`CMFCShellListCtrl`。 首先，尋找下列註解標頭檔：

   ```cpp
   // Generated message map functions
   ```

   正上方的註解加入此程式碼：

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **MFC 應用程式精靈**已經建立`CMFCShellTreeCtrl`物件中`CMainFrame`類別，但它是受保護的成員。 我們稍後將會存取此物件。 因此，現在建立它的存取子。 按兩下開啟稱為 MainFrm.h 標頭檔**方案總管 中**。 找出下列註解：

   ```cpp
   // Attributes
   ```

   立即在其下方加入下列方法宣告：

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   接下來，開啟 MainFrm.cpp 原始程式檔，按兩下**方案總管 中**。 在該檔案的底部，新增下列方法定義：

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. 現在我們更新`CMFCShellControlsView`類別來處理`WM_CREATE`windows 訊息。 開啟**類別檢視**視窗，然後選取`CMFCShellControlsView`類別。 以滑鼠右鍵按一下並選取**屬性**。

    接下來，在**屬性** 視窗中，按一下**訊息**圖示。 向下捲動，直到您找到`WM_CREATE`訊息。 從下拉式清單旁`WM_CREATE`，選取**\<新增 > OnCreate**。 這為我們建立的訊息處理常式，並會自動更新的 MFC 訊息對應。

   在 `OnCreate`我們現在將建立的方法我們`CMFCShellListCtrl`物件。 尋找`OnCreate`MFCShellControlsView.cpp 中的方法定義原始程式檔，並以下列程式碼取代它的實作：

    ```cpp
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)
    {
        if (CView::OnCreate(lpCreateStruct) == -1)
            return -1;

        CRect rectDummy (0, 0, 0, 0);

        m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,
            rectDummy, this, 1);

        return 0;
    }
    ```

1. 重複上述步驟，但針對`WM_SIZE`訊息。 這會導致您的應用程式檢視，每當使用者變更的應用程式視窗大小重新繪製。 取代為定義`OnSize`為下列程式碼的方法：

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. 最後一個步驟是將連線`CMFCShellTreeCtrl`並`CMFCShellListCtrl`使用的物件[CMFCShellTreeCtrl::SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist)方法。 在您呼叫此方法中後,`CMFCShellListCtrl`會自動顯示在選取之項目的內容`CMFCShellTreeCtrl`。 我們將在中這麼`OnActivateView`方法，它會覆寫從[CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview)。

   MFCShellControlsView.h 標頭檔中，內`CMFCShellControlsView`類別宣告中，新增下列方法宣告：

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   接下來，新增此方法的定義 MFCShellControlsView.cpp 原始程式檔：

    ```cpp
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

   因為我們要呼叫方法`CMainFrame`類別中，我們必須加入`#include`MFCShellControlsView.cpp 原始程式檔頂端指示詞：

    ```cpp
    #include "MainFrm.h"
    ```

1. 請確認應用程式已成功建立，建置並執行它。 若要建置應用程式，從**建置**功能表中，選取**建置方案**。 如果應用程式建置成功，會將其執行方法是選取**開始偵錯**從**偵錯**功能表。

   您現在應該會看到選取的項目詳細資料`CMFCShellTreeCtrl`[檢視] 窗格中。 當您按一下 使用中的節點`CMFCShellTreeCtrl`，則`CMFCShellListCtrl`將會自動更新。 同樣地，如果您按兩下中的資料夾`CMFCShellListCtrl`，則`CMFCShellTreeCtrl`應該會自動更新。

   以滑鼠右鍵按一下任何項目樹狀結構控制項中，或在清單控制項中。 請注意，如同您使用實際取得相同的操作功能表**檔案總管**。

## <a name="next-steps"></a>後續步驟

- 精靈會建立 Outlook 功能區同時**資料夾** 窗格和**行事曆**窗格。 可能不會是合理的作法**行事曆** 窗格中的**總管**視窗。 因此，現在移除該窗格。

- `CMFCShellListCtrl`支援在不同的模式中檢視檔案時，也將這類**大圖示**，**小圖示**，**清單**，並**詳細資料**。 更新您的應用程式，來實作這項功能。 提示： 請參閱[Visual c + + 範例](../visual-cpp-samples.md)。

## <a name="see-also"></a>另請參閱

[逐步解說](../mfc/walkthroughs-mfc.md)
