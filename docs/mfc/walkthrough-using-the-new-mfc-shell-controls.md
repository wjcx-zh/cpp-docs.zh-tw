---
title: 逐步解說：使用新的 MFC Shell 控制項
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: 5786fbbf7ec9f31e7d895a96dae27b8fc95abda1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360217"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>逐步解說：使用新的 MFC Shell 控制項

在本演練中,您將創建類似於檔案資源管理員的應用程式。 您將建立一個包含兩個窗格的視窗。 左側窗格將包含一個[CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md)物件,該物件在分層視圖中顯示您的桌面。 右側窗格將包含一個[CMFCShellListCtrl,](../mfc/reference/cmfcshelllistctrl-class.md)該顯示左側窗格中選擇的資料夾中的檔。

## <a name="prerequisites"></a>Prerequisites

- 在 Visual Studio 2017 及更高版本中,MFC 支援是可選元件。 要安裝它,請從「Windows 開始」功能表打開可視化工作室安裝程式。 尋找您正在使用的 Visual Studio 版本,然後選擇 **「修改」** 按鈕。 確保選取**了帶有C++磁貼的桌面開發**。 在 **「可選元件**」下,檢查**MFC 支援**按鈕。

- 這個演練假定您已設定 Visual Studio 以使用**一般開發設定**。 如果您使用的是其他開發設置,則默認情況下可能不會顯示我們在本演練中使用的某些 Visual Studio 視窗。

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>使用 MFC 應用程式精靈建立新的 MFC 應用程式

這些步驟因您使用的 Visual Studio 版本而異。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>在 Visual Studio 2019 建立 MFC 專案

1. 從主功能表，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [建立新專案]**** 對話方塊。

1. 在頂端的搜尋框中,鍵入**MFC,** 然後從結果清單中選擇**MFC 應用**。

1. 按 [下一步]  。 在下一頁中,輸入專案的名稱,並根據需要指定專案位置。

1. 選擇 [建立] **** 按鈕以建立專案。

   **顯示 MFC 應用程式精靈**後,請使用以下選項:

   1. 選擇左**邊 的應用程式類型**。 然後選擇 **「單一文檔」** 並選擇 **「文檔/檢視體系結構支援**」。 在 **「項目樣式**」下,選擇**Visual Studio**,並從**視覺樣式和顏色**下拉清單中選擇**Office 2007(藍色主題)。**

   1. 在 **"複合文件支援"** 窗格中,選擇 **"無**"。

   1. 不要對 **「文檔範本屬性」** 窗格進行任何更改。

   1. 在 **「使用者介面功能」** 窗格中,請確保選擇了 **「使用功能表欄」和「工具列」** 選項。 保留所有其他選項。

   1. 在 **「進階功能**」窗格中,選擇**ActiveX 控制件**、**常見控制件清單**和**導航窗格**選項。 保持一切不變。 "**導覽窗格「** 選項將導致精靈在視窗左側`CMFCShellTreeCtrl`建立已 嵌入的窗格。

   1. 我們不會對 **「生成類」** 窗格進行任何更改,因此單擊 **「完成」** 以創建新的 MFC 專案。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>在 Visual Studio 2017 或更早版本建立 MFC 專案

1. 使用**MFC 應用程式精靈**創建新的 MFC 應用程式。 要執行精靈,請從 **「檔」** 選單中選擇 **「新建**」,然後選擇 **「專案**」。 將顯示新**項目**對話框。

1. 在 **「新項目**」 對話框中,展開 **「項目類型」** 窗格中的**視覺C++** 節點並選擇**MFC**。 然後,在**樣本**窗格中,選擇**MFC 應用程式**。 鍵入項目的名稱,如`MFCShellControls`並按下 **「確定**」。

   **顯示 MFC 應用程式精靈**後,請使用以下選項:

   1. 在 **「應用程式類型」** 窗格下,在 **「應用程式類型**」 下,清除**選項卡式文件**選項。 接下來,選擇 **「單一文檔」** 並選擇 **「文檔/檢視體系結構支援**」。。 在 **「項目樣式**」下,選擇**Visual Studio**,並從**視覺樣式和顏色**下拉清單中選擇**Office 2007(藍色主題)。**

   1. 在 **"複合文件支援"** 窗格中,選擇 **"無**"。

   1. 不要對 **「文檔範本字串」** 窗格進行任何更改。

   1. 在 **「資料庫支援**」窗格(Visual Studio 2015 及更高版)上,選擇 **「無」,** 因為應用程式不使用資料庫。

   1. 在 **「使用者介面功能」** 窗格中,請確保選擇了 **「使用功能表欄」和「工具列」** 選項。 保留所有其他選項。

   1. 在 **「進階功能**」 「窗格中, 在 **「進階功能**」 ,僅選擇**ActiveX 控制件**與**通用控制清單**。 在 **「進階框架窗格」 下**,僅選擇 **「導航窗格」** 選項。 這會導致精靈建立視窗左邊的窗格,其中已嵌入了窗格`CMFCShellTreeCtrl`。

   1. 我們不會對 **「生成類」** 窗格進行任何更改,因此單擊 **「完成」** 以創建新的 MFC 專案。

::: moniker-end

通過生成並運行應用程式,驗證應用程式是否成功創建。 要產生應用程式,請從**產生**選單中選擇**產生解決方案**。 如果應用程式生成成功,則通過從**調試**功能表中選擇 **「開始調試」** 來運行應用程式。

嚮導會自動創建一個應用程式,該應用程式具有標準功能表欄、標準工具列、標準狀態列和視窗左側的 Outlook 欄,其中有**資料夾**檢視和**日曆**視圖。

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>將 shell 清單控制檔到文件檢視

1. 在本節中,您將`CMFCShellListCtrl`向嚮導創建的視圖添加實例。 通過在**解決方案資源管理器**中按**兩下 MFCShellControlsView.h**打開檢視頭檔。

   尋找`#pragma once`標頭檔頂部附近的指令。 它立即新增此代碼以包含的`CMFCShellListCtrl`標頭檔:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   現在添加類型`CMFCShellListCtrl`的成員變數。 首先,在標頭檔中找到以下註解:

   ```cpp
   // Generated message map functions
   ```

   在註解的緊要上方,添加此代碼:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **MFC 應用程式精靈**已在`CMainFrame`類中`CMFCShellTreeCtrl`創建了一個物件,但它是受保護的成員。 稍後我們將訪問該物件,因此現在為其創建一個訪問器。 通過在**解決方案資源管理器**中按兩下 MainFrm.h 標頭檔,打開該檔。 找到以下註解:

   ```cpp
   // Attributes
   ```

   立即在它下面加入以下方法聲明:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   接下來,透過在**解決方案資源管理器**中按兩下 MainFrm.cpp 源檔來打開該檔。 在該檔案的底部,新增以下方法定義:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. 現在,我們更新`CMFCShellControlsView`類以`WM_CREATE`處理 視窗消息。 打開 **「班級檢視」** 視窗並`CMFCShellControlsView`選擇 類。 按一下滑鼠右鍵並選取 [內容]****。

   接下來,在[「類嚮導」](reference/mfc-class-wizard.md)中,按一下 **「消息」** 選項`WM_CREATE`卡。向下滾動 ,直到找到郵件。 從 旁邊的下拉清單`WM_CREATE`中 ,選擇**\<"添加>創建**。 該命令為我們創建一個消息處理程式,並自動更新 MFC 消息映射。

   在`OnCreate`方法中,我們現在將建立物件`CMFCShellListCtrl`。 在`OnCreate`MFCShellControlsView.cpp 源檔案中尋找方法定義,並將其實現取代為以下代碼:

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

1. 重複上一步,但對`WM_SIZE`消息。 每當使用者更改應用程式視窗的大小時,它將導致重新繪製應用程式檢視。 將`OnSize`方法定義取代為以下代碼:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. 最後一步是使用`CMFCShellTreeCtrl`[CMFCShellTreeCtrl:set關聯清單](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist)方法`CMFCShellListCtrl`連接 和 物件。 呼叫`CMFCShellTreeCtrl::SetRelatedList`後`CMFCShellListCtrl`, 將自動顯示 中選取項目`CMFCShellTreeCtrl`的內容。 我們連接`OnActivateView`方法中的物件,該物件從[CView 重寫::onActivateView](../mfc/reference/cview-class.md#onactivateview)。

   在 MFCShellControlsView.h 標頭檔中`CMFCShellControlsView`,在 類別聲明中,添加以下方法聲明:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   接下來,將該方法的定義添加到 MFCShellControlsView.cpp 源檔案中:

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

   由於我們從`CMainFrame`類調用方法,因此必須在 MFCShellControlsView.cpp 源檔的頂部`#include`添加一個 指令:

    ```cpp
    #include "MainFrm.h"
    ```

1. 通過生成並運行應用程式,驗證應用程式是否成功創建。 要產生應用程式,請從**產生**選單中選擇**產生解決方案**。 如果應用程式生成成功,請通過從**除錯**功能表中選擇 **「開始除錯」** 來執行它。

   現在,您應該在視窗格`CMFCShellTreeCtrl`中看到所選項目的詳細資訊。 點選中的`CMFCShellTreeCtrl`節點時,將自動更新`CMFCShellListCtrl`。 同樣,如果雙擊 中的`CMFCShellListCtrl`資料夾`CMFCShellTreeCtrl`, 應自動更新 。

   右鍵按一下樹控制件或清單控制件中的任何項。 你得到的上下文菜單與使用實際**文件資源管理器**相同。

## <a name="next-steps"></a>後續步驟

- 該嚮導建立了一個 Outlook 欄,其中同時包含 **"資料夾"** 窗格和 **"日曆"** 窗格。 在**資源管理員**視窗中使用 **「行事曆」** 窗格可能沒有意義,因此請立即刪除該窗格。

- 支援`CMFCShellListCtrl`以不同模式檢視檔案,如**大圖示**,**您可以顯示在小圖示**、**清單**與**詳細資訊**。 更新應用程式以實現此功能。 提示:請參閱[視覺C++範例](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>另請參閱

[逐步解說](../mfc/walkthroughs-mfc.md)
