---
title: 逐步解說：將控制項放在工具列上
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: 0c62a8b484cb666427f873244221afec5d4719da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510735"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>逐步解說：將控制項放在工具列上

本文說明如何將包含 Windows 控制項的工具列按鈕加入至工具列。 在 MFC 中, 工具列按鈕必須是[CMFCToolBarButton 類別](../mfc/reference/cmfctoolbarbutton-class.md)衍生類別, 例如[CMFCToolBarComboBoxButton 類別](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)、 [CMFCToolBarEditBoxButton 類別](../mfc/reference/cmfctoolbareditboxbutton-class.md)、 [CMFCDropDownToolbarButton 類別](../mfc/reference/cmfcdropdowntoolbarbutton-class.md), 或[CMFCToolBarMenuButton 類別](../mfc/reference/cmfctoolbarmenubutton-class.md)。

## <a name="adding-controls-to-toolbars"></a>將控制項加入至工具列

若要將控制項加入至工具列，請依照下列步驟執行：

1. 為父工具列資源的按鈕保留假的資源 ID。 如需如何在 Visual Studio 中使用**工具列編輯器**來建立按鈕的詳細資訊, 請參閱[工具列編輯器](../windows/toolbar-editor.md)一文。

1. 為父工具列的所有點陣圖中的按鈕保留工具列按鈕影像 (按鈕圖示)。

1. 在處理`AFX_WM_RESETTOOLBAR`訊息的訊息處理常式中, 執行下列步驟:

   1. 使用 `CMFCToolbarButton` 衍生類別建構按鈕控制項。

   1. 使用[CMFCToolBar:: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton), 以新的控制項取代 [虛擬] 按鈕。 由於 `ReplaceButton` 會複製按鈕物件並維護複本，您可以在堆疊上建構按鈕物件。

> [!NOTE]
>  如果您已在應用程式中啟用自訂, 您可能必須使用 [**自訂**] 對話方塊之 [**工具列**] 索引標籤上的 [**重設**] 按鈕來重設工具列, 以便在重新編譯之後, 看到應用程式中的更新控制項。 工具列狀態儲存在 Windows 登錄中，且 `ReplaceButton` 方法在應用程式啟動期間執行後，登錄資訊會被載入並套用。

## <a name="toolbar-controls-and-customization"></a>工具列控制項和自訂

[**自訂**] 對話方塊的 [**命令**] 索引標籤包含應用程式中可用的命令清單。 根據預設, [**自訂**] 對話方塊會處理應用程式功能表, 並建立每個功能表分類中的標準工具列按鈕清單。 若要保留工具列控制項提供的擴充功能, 您必須以 [**自訂**] 對話方塊中的自訂控制項取代 [標準] 工具列按鈕。

當您啟用自訂時, 您可以使用[CMFCToolBarsCustomizeDialog 類別](../mfc/reference/cmfctoolbarscustomizedialog-class.md)類別, 在`OnViewCustomize`自訂處理常式中建立 [**自訂**] 對話方塊。 呼叫[CMFCToolBarsCustomizeDialog:: Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create)以顯示 [**自訂**] 對話方塊之前, 請呼叫[CMFCToolBarsCustomizeDialog:: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) , 將標準按鈕取代為新的控制項。

## <a name="example-creating-a-find-combo-box"></a>範例：建立尋找下拉式方塊

本節說明如何建立出現在工具列上的 [**尋找**] 下拉式方塊控制項, 並包含最近使用的搜尋字串。 使用者可以在控制項中輸入字串，然後按 ENTER 鍵搜尋文件，或按 Esc 鍵將焦點移回主框架。 這個範例假設檔顯示在[CEditView 類別](../mfc/reference/ceditview-class.md)衍生的視圖中。

### <a name="creating-the-find-control"></a>建立尋找控制項

首先, 建立 [**尋找**] 下拉式方塊控制項:

1. 將按鈕和其命令加入至應用程式資源：

   1. 在應用程式資源中，將具有 `ID_EDIT_FIND` 命令 ID 的新按鈕加入至應用程式的工具列，以及任何與工具列相關的點陣圖。

   1. 使用`ID_EDIT_FIND`命令識別碼來建立新的功能表項目。

   1. 將新字串「Find the text\nFind」加入至字串資料表，並將`ID_EDIT_FIND_COMBO` 命令 ID 指派給它。 此識別碼將用來做為 [**尋找**下拉式方塊] 按鈕的命令 ID。

        > [!NOTE]
        > 由於 `ID_EDIT_FIND` 是由 `CEditView` 處理的標準命令，因此您不需要實作這個命令的特殊處理常式。  不過，您必須實作新命令 `ID_EDIT_FIND_COMBO` 的處理常式。

1. 建立衍生自`CFindComboBox` [CComboBox 類別](../mfc/reference/ccombobox-class.md)的新類別。

1. 在 `CFindComboBox`類別中，覆寫 `PreTranslateMessage` 虛擬方法。 這個方法會啟用下拉式方塊來處理[WM_KEYDOWN](/windows/win32/inputdev/wm-keydown)訊息。 如果使用者點閱 Esc 鍵 (`VK_ESCAPE`)，便會將焦點移回主框架視窗。 如果使用者點閱 ENTER 鍵 (`VK_ENTER`)，便會將包含 `WM_COMMAND` 命令 ID 的 `ID_EDIT_FIND_COMBO` 訊息張貼到主框架視窗內。

1. 為 [**尋找**] 下拉式方塊按鈕建立一個衍生自[CMFCToolBarComboBoxButton 類別](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)的類別。 在此範例中，其名稱是 `CFindComboButton`。

1. `CMFCToolbarComboBoxButton` 的建構函式接受三個參數：按鈕的命令 ID、按鈕影像索引和下拉式方塊樣式。 設定這些參數，如下所示：

   1. 傳遞 `ID_EDIT_FIND_COMBO` 做為命令 ID。

   1. 使用[CCommandManager:: GetCmdImage](reference/internal-classes.md) `ID_EDIT_FIND`搭配來取得影像索引。

   1. 如需可用的下拉式列示方塊樣式清單, 請參閱[下拉式方塊樣式](../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。

1. 在 `CFindComboButton` 類別中，覆寫 `CMFCToolbarComboBoxButton::CreateCombo` 方法。 您應該建立 `CFindComboButton` 物件，並將指標傳回給該物件。

1. 使用 [ [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) ] 宏, 讓下拉式按鈕成為持續性的。 工作區管理員會自動載入，並將按鈕狀態儲存在 Windows 登錄中。

1. 實作您文件檢視中的 `ID_EDIT_FIND_COMBO` 處理常式。 使用[CMFCToolBar:: GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) `ID_EDIT_FIND_COMBO`搭配來取出所有**尋找**下拉式方塊按鈕。 有了自訂功能，即可用相同命令 ID 建立數個按鈕複本。

1. 在訊息處理常式`OnFind`中, 使用[CMFCToolBar:: IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton)來判斷是否從 [尋找] 下拉式方塊按鈕傳送 [尋找] 命令。 `ID_EDIT_FIND` 如果是，請尋找文字並將搜尋字串加入至下拉式方塊。

### <a name="adding-the-find-control-to-the-main-toolbar"></a>將尋找控制項加入至主要工具列

若要將下拉式方塊按鈕加入至工具列，請依照下列步驟執行：

1. 實作主框架視窗的 `AFX_WM_RESETTOOLBAR` 訊息處理常式 `OnToolbarReset`。

    > [!NOTE]
    > 在應用程式啟動期間工具列初始化時，或當工具列在自訂期間重設時，架構會傳送訊息至主框架視窗。 不論是哪一種情況, 您都必須使用 [自訂**尋找**] 下拉式方塊按鈕來取代 [標準] 工具列按鈕。

1. 在處理常式中, 檢查工具列識別碼, 也就是 AFX_WM_RESETTOOLBAR 訊息的*WPARAM。* `AFX_WM_RESETTOOLBAR` 如果工具列識別碼等於包含 [**尋找**] 下拉式方塊按鈕的工具列, 請呼叫[CMFCToolBar:: ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton)來取代 [**尋找**] 按鈕 (也就是具有`ID_EDIT_FIND)` `CFindComboButton`物件的命令識別碼的按鈕)。

    > [!NOTE]
    > 由於 `CFindComboBox` 會複製按鈕物件並維護複本，因此您可以在堆疊上建構 `ReplaceButton` 物件。

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>將尋找控制項加入至自訂對話方塊

在自訂處理`OnViewCustomize`程式中, 呼叫[CMFCToolBarsCustomizeDialog:: ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) , 以`CFindComboButton`物件取代 [**尋找**] 按鈕 (也就是具有`ID_EDIT_FIND`命令識別碼的按鈕)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../mfc/hierarchy-chart.md)<br/>
[類別](../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 類別](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 類別](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCToolBarsCustomizeDialog 類別](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
