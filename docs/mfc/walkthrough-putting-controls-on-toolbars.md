---
title: 逐步解說：將控制項放在工具列上
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: 2a801e61c49301d9b8780bbf7eb77025990337ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360262"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>逐步解說：將控制項放在工具列上

本文介紹如何向工具列添加包含 Windows 控制件的工具列按鈕。 在 MFC 中,工具列按鈕必須是[CMFCToolBarButton 類派生類](../mfc/reference/cmfctoolbarbutton-class.md),例如[CMFCToolBarComboxButton 類](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)[、CMFCToolBarEditBox按鈕類](../mfc/reference/cmfctoolbareditboxbutton-class.md)[、CMFCDown下拉工具列按鈕類](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)或[CMFCToolBarMenuButton 類](../mfc/reference/cmfctoolbarmenubutton-class.md)。

## <a name="adding-controls-to-toolbars"></a>將控制項加入至工具列

若要將控制項加入至工具列，請依照下列步驟執行：

1. 為父工具列資源的按鈕保留假的資源 ID。 有關如何使用視覺化工作室中的**工具列編輯器**創建按鈕的詳細資訊,請參閱[工具列編輯器](../windows/toolbar-editor.md)一文。

1. 為父工具列的所有點陣圖中的按鈕保留工具列按鈕影像 (按鈕圖示)。

1. 在處理`AFX_WM_RESETTOOLBAR`消息的消息處理程式中,執行以下步驟:

   1. 使用 `CMFCToolbarButton` 衍生類別建構按鈕控制項。

   1. 使用[CMFCToolBar:::替換按鈕](../mfc/reference/cmfctoolbar-class.md#replacebutton),用新控制項替換虛擬按鈕。 由於 `ReplaceButton` 會複製按鈕物件並維護複本，您可以在堆疊上建構按鈕物件。

> [!NOTE]
> 如果在應用程式中啟用了自訂,則可能必須使用 **「自訂」** 對話方塊**工具列選項卡上的****「重置**」按鈕來重置工具列,才能在重新編譯後查看應用程式中的更新控制項。 工具列狀態儲存在 Windows 登錄中，且 `ReplaceButton` 方法在應用程式啟動期間執行後，登錄資訊會被載入並套用。

## <a name="toolbar-controls-and-customization"></a>工具列控制項和自訂

**「自訂」** 對話方塊的 **「指令」** 選項卡包含應用程式中可用的命令清單。 預設情況下,「**自訂」** 對話框處理應用程式功能表,並在每個選單類別中生成標準工具列按鈕的清單。 要保留工具列控制件提供的擴充功能,必須在 **「自訂」** 對話方塊中用自訂控制項替代標準工具列按鈕。

啟用自訂時,請使用[CMFCToolBars 自訂對話方塊類別](../mfc/reference/cmfctoolbarscustomizedialog-class.md)在自訂`OnViewCustomize`處理程式中創建 **「自訂**」對話方塊。 在透過調用[CMFCToolBars 自訂對話框顯示](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create)**「自訂**」對話方塊之前:創建 ,調用[CMFCToolBars 自訂對話框:替換按鈕](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)以將標準按鈕替換為新控制項。

## <a name="example-creating-a-find-combo-box"></a>範例：建立搜尋下拉式方塊

本節介紹如何創建顯示在工具列上並包含最近使用的搜索字串的 **「查找**組合框」控件。 使用者可以在控制項中輸入字串，然後按 ENTER 鍵搜尋文件，或按 Esc 鍵將焦點移回主框架。 此示例假定文件顯示在[CEditView 類](../mfc/reference/ceditview-class.md)派生檢視中。

### <a name="creating-the-find-control"></a>建立尋找控制項

首先,建立 **「尋找**組合框」控制件:

1. 將按鈕和其命令加入至應用程式資源：

   1. 在應用程式資源中，將具有 `ID_EDIT_FIND` 命令 ID 的新按鈕加入至應用程式的工具列，以及任何與工具列相關的點陣圖。

   1. 使用`ID_EDIT_FIND`指令 ID 建立新的選單項。

   1. 將新字串「Find the text\nFind」加入至字串資料表，並將`ID_EDIT_FIND_COMBO` 命令 ID 指派給它。 此 ID 將用作 **「尋找**組合框」 按鈕的命令 ID。

        > [!NOTE]
        > 由於 `ID_EDIT_FIND` 是由 `CEditView` 處理的標準命令，因此您不需要實作這個命令的特殊處理常式。  不過，您必須實作新命令 `ID_EDIT_FIND_COMBO` 的處理常式。

1. 建立新類別`CFindComboBox`,派生自[CComboBox 類別](../mfc/reference/ccombobox-class.md)。

1. 在 `CFindComboBox`類別中，覆寫 `PreTranslateMessage` 虛擬方法。 此方法將使組合框能夠處理[WM_KEYDOWN](/windows/win32/inputdev/wm-keydown)消息。 如果使用者點閱 Esc 鍵 (`VK_ESCAPE`)，便會將焦點移回主框架視窗。 如果使用者點閱 ENTER 鍵 (`VK_ENTER`)，便會將包含 `WM_COMMAND` 命令 ID 的 `ID_EDIT_FIND_COMBO` 訊息張貼到主框架視窗內。

1. 創建從[CMFCToolBarComBoBoxButton 類](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)派生的 **「查找**組合框」按鈕的類。 在此範例中，其名稱是 `CFindComboButton`。

1. `CMFCToolbarComboBoxButton` 的建構函式接受三個參數：按鈕的命令 ID、按鈕影像索引和下拉式方塊樣式。 設定這些參數，如下所示：

   1. 傳遞 `ID_EDIT_FIND_COMBO` 做為命令 ID。

   1. 使用[CCommandManager::獲取CmdImage](reference/internal-classes.md)`ID_EDIT_FIND`獲取圖像索引。

   1. 關於可用的組合框樣式的清單,請參考[的組合框樣式](../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。

1. 在 `CFindComboButton` 類別中，覆寫 `CMFCToolbarComboBoxButton::CreateCombo` 方法。 您應該建立 `CFindComboButton` 物件，並將指標傳回給該物件。

1. 使用[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)宏使組合按鈕持久化。 工作區管理員會自動載入，並將按鈕狀態儲存在 Windows 登錄中。

1. 實作您文件檢視中的 `ID_EDIT_FIND_COMBO` 處理常式。 使用[CMFCToolBar:取得命令按鈕](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons)以`ID_EDIT_FIND_COMBO`檢索所有 **「查找**組合框」 按鈕。 有了自訂功能，即可用相同命令 ID 建立數個按鈕複本。

1. 在消息`ID_EDIT_FIND`處理`OnFind`程式 中,使用[CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton)確定查找命令是否從 **「尋找**組合」框按鈕發送。 如果是，請尋找文字並將搜尋字串加入至下拉式方塊。

### <a name="adding-the-find-control-to-the-main-toolbar"></a>將尋找控制項加入至主要工具列

若要將下拉式方塊按鈕加入至工具列，請依照下列步驟執行：

1. 實作主框架視窗的 `AFX_WM_RESETTOOLBAR` 訊息處理常式 `OnToolbarReset`。

    > [!NOTE]
    > 在應用程式啟動期間工具列初始化時，或當工具列在自訂期間重設時，架構會傳送訊息至主框架視窗。 在這兩種情況下,都必須將標準工具列按鈕替換為自定義 **「尋找**組合框」按鈕。

1. 在處理程式`AFX_WM_RESETTOOLBAR`中,檢查工具列 ID,即AFX_WM_RESETTOOLBAR消息的*WPARAM。* 如果工具列 ID 等於包含 **「搜尋**組合框」按鈕的工具列 ID,請致電[CMFCToolBar::取代Button](../mfc/reference/cmfctoolbar-class.md#replacebutton)以取代 **「尋找**」按鈕(即使用`ID_EDIT_FIND)`帶`CFindComboButton`有物件的指令 ID 的 按鈕)。

    > [!NOTE]
    > 由於 `CFindComboBox` 會複製按鈕物件並維護複本，因此您可以在堆疊上建構 `ReplaceButton` 物件。

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>將尋找控制項加入至自訂對話方塊

在自訂`OnViewCustomize`處理程式中,調用[CMFCToolBars 自訂對話框:替換 Button](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)以將 **「尋找**`ID_EDIT_FIND`「按鈕(`CFindComboButton`即命令 ID 中的按鈕) 替換為物件。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../mfc/hierarchy-chart.md)<br/>
[類別](../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton 類別](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton 類別](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCToolBarsCustomizeDialog 類別](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
