---
title: 逐步解說：使用新的 MFC Shell 控制項
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: cf0a6bd230364b48c78c72b8e453e7e641fb2d0e
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907400"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>逐步解說：使用新的 MFC Shell 控制項

在此逐步解說中，您將建立類似于 [檔案瀏覽器] 的應用程式。 您將建立具有兩個窗格的視窗。 左窗格會保留[CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md)物件，以階層式視圖顯示您的桌面。 右窗格會保存[CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md) ，其中會顯示在左窗格中選取之資料夾內的檔案。

## <a name="prerequisites"></a>必要條件

- 在 Visual Studio 2017 和更新版本中，MFC 支援是選擇性的元件。 若要安裝它，請從 Windows [開始] 功能表開啟 [Visual Studio 安裝程式]。 尋找您使用的 Visual Studio 版本，然後選擇 [**修改**] 按鈕。 請確定已核取 [**使用C++磚進行桌面開發**]。 在 [**選用元件**] 底下，勾選 [ **MFC 支援**] 按鈕。

- 本逐步解說假設您已設定 Visual Studio 使用 **[一般開發設定**]。 如果您使用不同的開發設定，則預設不會顯示我們在本逐步解說中使用的某些 Visual Studio 視窗。

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>若要使用 MFC 應用程式精靈建立新的 MFC 應用程式

這些步驟會根據您使用的 Visual Studio 版本而有所不同。 請確認本頁面左上角的版本選取器已正確設定。

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>若要在 Visual Studio 2019 中建立 MFC 專案

1. 從主功能表，選擇 [檔案] > [新增] > [專案]，以開啟 [建立新專案] 對話方塊。

1. 在頂端的 [搜尋] 方塊中，輸入**mfc** ，然後從結果清單中選擇 [ **mfc 應用程式**]。 

1. 按一下 [下一步]。 在下一個頁面中，輸入專案的名稱，並視需要指定專案位置。

1. 選擇 [建立] 按鈕以建立專案。

   [ **MFC 應用程式精靈]** 顯示之後，請使用下列選項：
 
   1. 選擇左側的 [**應用程式類型**]。 然後選取 [**單一檔**]，然後選取 [**檔/視圖架構支援**]。 在 [**專案樣式**] 底下，選取 [ **Visual Studio**]，然後從 [**視覺化樣式和色彩**] 下拉式清單中選取 [ **Office 2007 （藍色主題）** ]。

   1. 在 [**複合檔案支援**] 窗格上，選取 [**無**]。

   1. 不要對 [**檔範本屬性**] 窗格進行任何變更。

   1. 在 [**使用者介面功能**] 窗格上，請確定已選取 [**使用功能表列和工具列**] 選項。 保留所有其他選項。

   1. 在 [ **Advanced Features** ] 窗格中，選取 [ **ActiveX 控制項**]、[**通用控制項資訊清單**] 和 [**流覽窗格]** 選項。 保留所有其他專案。 [**流覽窗格**] 選項會使嚮導在視窗左側建立窗格，並`CMFCShellTreeCtrl`已內嵌。

   1. 我們不會對 [**產生的類別**] 窗格進行任何變更，因此請按一下 **[完成]** 來建立新的 MFC 專案。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>若要在 Visual Studio 2017 或更早版本中建立 MFC 專案

1. 使用 [ **Mfc 應用程式精靈]** 建立新的 mfc 應用程式。 若要執行嚮導，請在 **[檔案**] 功能表中選取 [**新增**]，然後選取 [**專案**]。 [**新增專案**] 對話方塊隨即顯示。

1. 在 [**新增專案**] 對話方塊中，展開 [**專案類型**] 窗格中的**視覺效果C++** 節點，然後選取 [ **MFC**]。 然後，在 [**範本**] 窗格中，選取 [ **MFC 應用程式**]。 輸入專案的名稱，例如`MFCShellControls` ，然後按一下 **[確定]** 。 

   [ **MFC 應用程式精靈]** 顯示之後，請使用下列選項：

   1. 在 [**應用程式類型**] 窗格的 [**應用程式類型**] 底下，清除 [索引標籤**式檔**] 選項。 接下來，選取 [**單一檔**]，然後選取 [**檔/視圖架構支援**]。 在 [**專案樣式**] 底下，選取 [ **Visual Studio**]，然後從 [**視覺化樣式和色彩**] 下拉式清單中選取 [ **Office 2007 （藍色主題）** ]。

   1. 在 [**複合檔案支援**] 窗格上，選取 [**無**]。

   1. 不要對 [**檔範本字串**] 窗格進行任何變更。

   1. 在 [**資料庫支援**] 窗格（Visual Studio 2015 和更舊版本）上，選取 [**無**]，因為應用程式不會使用資料庫。

   1. 在 [**使用者介面功能**] 窗格上，請確定已選取 [**使用功能表列和工具列**] 選項。 保留所有其他選項。

   1. 在 [ **Advanced features** ] 窗格的 [ **advanced features**] 底下，選取 [只有**ActiveX 控制項**和**通用控制項資訊清單**]。 在 [**高級框架窗格**] 底下，只選取 [**流覽窗格]** 選項。 這會導致嚮導在視窗左側建立窗格，並`CMFCShellTreeCtrl`已內嵌。

   1. 我們不會對 [**產生的類別**] 窗格進行任何變更，因此請按一下 **[完成]** 來建立新的 MFC 專案。

::: moniker-end

藉由建立並執行應用程式，確認已成功建立。 若要建立應用程式，請在 [**建立**] 功能表中選取 [**建立方案**]。 如果成功建立應用程式，請從 [**調試**程式] 功能表中選取 [**開始調試**程式] 來執行應用程式。

Wizard 會自動建立一個應用程式，其中包含標準功能表列、標準工具列、標準狀態列，以及視窗左側的 Outlook 橫條和 [**資料夾**] 和 [行事**曆**] 視圖。

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>將 shell 清單控制項新增至檔視圖

1. 在本節中，您會將的實例`CMFCShellListCtrl`加入至 wizard 所建立的視圖中。 按兩下 **方案總管**中的  **MFCShellControlsView**  來開啟 view 標頭檔。

   找出`#pragma once`標頭檔頂端附近的指示詞。 緊接在其底下新增下列程式`CMFCShellListCtrl`代碼，以包含的標頭檔：

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   現在加入類型`CMFCShellListCtrl`的成員變數。 首先，在標頭檔中找出下列批註：

   ```cpp
   // Generated message map functions
   ```

   在該批註的正上方，新增下列程式碼：

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. **MFC 應用程式精靈**已經在`CMainFrame`類別`CMFCShellTreeCtrl`中建立物件，但它是受保護的成員。 我們稍後會存取物件，因此請立即為其建立存取子。 按兩下 **方案總管**中的 mainfrm.cpp 標頭檔，以開啟該檔案。 找出下列批註：

   ```cpp
   // Attributes
   ```

   緊接在其底下，新增下列方法宣告：

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   接下來，在 [**方案總管**] 中按兩下 mainfrm.cpp，以開啟該原始檔案。 在該檔案的底部，新增下列方法定義：

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. 現在我們要更新`CMFCShellControlsView`類別來`WM_CREATE`處理 windows 訊息。 開啟 [**類別檢視**] 視窗，然後`CMFCShellControlsView`選取類別。 以滑鼠右鍵按一下並選取 [**屬性**]。

   接下來，在 [[類別] [Wizard](reference/mfc-class-wizard.md)] 中按一下 [**訊息**] 索引標籤。向下滾動，直到您`WM_CREATE`找到訊息為止。 從下拉式清單旁`WM_CREATE`，選取 **\<新增 > OnCreate** 。 命令會為我們建立訊息處理常式，並自動更新 MFC 訊息對應。

   在方法中，我們現在會`CMFCShellListCtrl`建立物件。 `OnCreate` 在 MFCShellControlsView 檔案中尋找方法定義，並以下列程式碼取代它的執行：`OnCreate`

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

1. 針對`WM_SIZE`訊息重複上一個步驟。 每當使用者變更應用程式視窗的大小時，就會重新繪製您的應用程式視圖。 將`OnSize`方法的定義取代為下列程式碼：

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. 最後一個步驟是使用`CMFCShellTreeCtrl` [CMFCShellTreeCtrl：： SetRelatedList](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist)方法來連接和`CMFCShellListCtrl`物件。 呼叫`CMFCShellTreeCtrl::SetRelatedList`之後`CMFCShellTreeCtrl`，將會自動顯示中所選取之專案的內容。 `CMFCShellListCtrl` 我們會連接`OnActivateView`方法中的物件，這會從[CView：： OnActivateView](../mfc/reference/cview-class.md#onactivateview)覆寫。

   在`CMFCShellControlsView`類別宣告內的 MFCShellControlsView 標頭檔中，新增下列方法宣告：

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   接下來，將方法的定義新增至 MFCShellControlsView 的 .cpp 原始程式檔：

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

   因為我們是從`CMainFrame`類別呼叫方法，所以必須在 MFCShellControlsView 檔案的頂端`#include`加入指示詞：

    ```cpp
    #include "MainFrm.h"
    ```

1. 藉由建立並執行應用程式，確認已成功建立。 若要建立應用程式，請在 [**建立**] 功能表中選取 [**建立方案**]。 如果成功建立應用程式，請從 [**調試**程式] 功能表選取 [**開始調試**] 來執行。

   您現在應該會在 [視圖] 窗格`CMFCShellTreeCtrl`中，看到所選取專案的詳細資料。 當您按一下中`CMFCShellTreeCtrl`的節點時`CMFCShellListCtrl` ，將會自動更新。 同樣地，如果您按兩下中`CMFCShellListCtrl`的資料夾`CMFCShellTreeCtrl` ，應該會自動更新。

   以滑鼠右鍵按一下樹狀目錄控制項或清單控制項中的任何專案。 您可以使用實際的檔案**瀏覽器**，取得相同的內容功能表。

## <a name="next-steps"></a>後續步驟

- Wizard 建立了具有 [**資料夾**] 窗格和 [行事**曆**] 窗格的 Outlook 橫條。 在**Explorer**視窗中具有行事**曆**窗格可能沒有意義，因此請立即移除該窗格。

- 支援`CMFCShellListCtrl`以不同的模式來查看檔案，例如**大型圖示**、**小型圖示**、**清單**和**詳細資料**。 更新您的應用程式以執行此功能。 提示：請[參閱C++ Visual Samples](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>另請參閱

[逐步解說](../mfc/walkthroughs-mfc.md)
