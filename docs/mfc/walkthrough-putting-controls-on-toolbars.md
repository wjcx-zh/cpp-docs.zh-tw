---
title: 逐步解說： 將放在工具列上的控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 258d8f10238db58be26743694943ae3bd6abc20e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693571"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>逐步解說：將控制項放在工具列上
本主題說明如何將包含 Windows 控制項的工具列按鈕加入至工具列。 在 MFC 中，必須是工具列按鈕[CMFCToolBarButton 類別](../mfc/reference/cmfctoolbarbutton-class.md)-衍生類別，例如[CMFCToolBarComboBoxButton 類別](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)， [CMFCToolBarEditBoxButton 類別](../mfc/reference/cmfctoolbareditboxbutton-class.md)，[CMFCDropDownToolbarButton 類別](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)，或[CMFCToolBarMenuButton 類別](../mfc/reference/cmfctoolbarmenubutton-class.md)。  
  
## <a name="adding-controls-to-toolbars"></a>將控制項加入至工具列  
 若要將控制項加入至工具列，請依照下列步驟執行：  
  
1.  為父工具列資源的按鈕保留假的資源 ID。 如需如何在 Visual Studio 中使用工具列編輯器建立按鈕的詳細資訊，請參閱[工具列編輯器](../windows/toolbar-editor.md)主題。  
  
2.  為父工具列的所有點陣圖中的按鈕保留工具列按鈕影像 (按鈕圖示)。  
  
3.  訊息處理常式處理 AFX_WM_RESETTOOLBAR 訊息中，執行下列作業：  
  
    1.  使用 `CMFCToolbarButton` 衍生類別建構按鈕控制項。  
  
    2.  使用新的控制項取代假的按鈕[CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton)。 由於 `ReplaceButton` 會複製按鈕物件並維護複本，您可以在堆疊上建構按鈕物件。  
  
> [!NOTE]
>  如果您啟用自訂應用程式中，您可能必須使用重設工具列**重設**按鈕**工具列**索引標籤**自訂**對話方塊，請參閱更新之後重新編譯的應用程式中的控制項。 工具列狀態儲存在 Windows 登錄中，且 `ReplaceButton` 方法在應用程式啟動期間執行後，登錄資訊會被載入並套用。  
  
## <a name="toolbar-controls-and-customization"></a>工具列控制項和自訂  
 **命令**索引標籤**自訂**對話方塊包含一份可用的應用程式中的命令。 根據預設，**自訂**對話方塊處理應用程式功能表，並建立每個功能表類別中的 [標準] 工具列按鈕的清單。 若要保留工具列控制項提供的擴充的功能，您必須使用中的自訂控制項取代標準工具列按鈕**自訂** 對話方塊。  
  
 當您啟用自訂時，您會建立**自訂** 對話方塊中的自訂處理常式`OnViewCustomize`利用[CMFCToolBarsCustomizeDialog 類別](../mfc/reference/cmfctoolbarscustomizedialog-class.md)類別。 顯示之前**自訂**對話方塊中，藉由呼叫[CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create)，呼叫[CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)取代新的控制項 [標準] 按鈕。  
  
## <a name="example-creating-a-find-combo-box"></a>範例：建立搜尋下拉式方塊  
 本節說明如何建立**尋找**下拉式方塊控制項，會出現在工具列上，而包含最近使用過的搜尋字串。 使用者可以在控制項中輸入字串，然後按 ENTER 鍵搜尋文件，或按 Esc 鍵將焦點移回主框架。 這個範例假設文件會顯示在[CEditView 類別](../mfc/reference/ceditview-class.md)-衍生檢視。  
  
### <a name="creating-the-find-control"></a>建立尋找控制項  
 首先，建立 `Find` 下拉式方塊控制項：  
  
1.  將按鈕和其命令加入至應用程式資源：  
  
    1.  在應用程式資源中，將具有 `ID_EDIT_FIND` 命令 ID 的新按鈕加入至應用程式的工具列，以及任何與工具列相關的點陣圖。  
  
    2.  建立一個具有 ID_EDIT_FIND 命令 ID 的新功能表項目。  
  
    3.  將新字串「Find the text\nFind」加入至字串資料表，並將`ID_EDIT_FIND_COMBO` 命令 ID 指派給它。 這個 ID 將會用做 `Find` 下拉式方塊按鈕的命令 ID。  
  
        > [!NOTE]
        >  由於 `ID_EDIT_FIND` 是由 `CEditView` 處理的標準命令，因此您不需要實作這個命令的特殊處理常式。  不過，您必須實作新命令 `ID_EDIT_FIND_COMBO` 的處理常式。  
  
2.  建立新的類別，`CFindComboBox`衍生自[CComboBox 類別](../mfc/reference/ccombobox-class.md)。  
  
3.  在 `CFindComboBox`類別中，覆寫 `PreTranslateMessage` 虛擬方法。 這個方法會啟用下拉式方塊處理[WM_KEYDOWN](/windows/desktop/inputdev/wm-keydown)訊息。 如果使用者點閱 Esc 鍵 (`VK_ESCAPE`)，便會將焦點移回主框架視窗。 如果使用者點閱 Enter 鍵 (`VK_ENTER`)，張貼到主框架視窗包含的 WM_COMMAND 訊息`ID_EDIT_FIND_COMBO`命令 id。  
  
4.  建立的類別**尋找**下拉式方塊按鈕，衍生自[CMFCToolBarComboBoxButton 類別](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。 在此範例中，它的名稱是 `CFindComboButton`。  
  
5.  `CMFCToolbarComboBoxButton` 的建構函式接受三個參數：按鈕的命令 ID、按鈕影像索引和下拉式方塊樣式。 設定這些參數，如下所示：  
  
    1.  傳遞 `ID_EDIT_FIND_COMBO` 做為命令 ID。  
  
    2.  使用[CCommandManager::GetCmdImage](reference/internal-classes.md)使用`ID_EDIT_FIND`取得的映像索引。  
  
    3.  如需可用下拉式方塊樣式的清單，請參閱 <<c0> [ 下拉式方塊樣式](../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。  
  
6.  在 `CFindComboButton` 類別中，覆寫 `CMFCToolbarComboBoxButton::CreateCombo` 方法。 您應該建立 `CFindComboButton` 物件，並將指標傳回給該物件。  
  
7.  使用[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)巨集讓下拉式按鈕的持續性。 工作區管理員會自動載入，並將按鈕狀態儲存在 Windows 登錄中。  
  
8.  實作您文件檢視中的 `ID_EDIT_FIND_COMBO` 處理常式。 使用[CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons)具有`ID_EDIT_FIND_COMBO`來擷取所有**尋找**下拉式方塊按鈕。 有了自訂功能，即可用相同命令 ID 建立數個按鈕複本。  
  
9. 在 ID_EDIT_FIND 訊息處理常式`OnFind`，使用[CMFCToolBar::IsLastCommandFromButton](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton)判斷尋找命令從傳送**尋找**下拉式方塊按鈕。 如果是，請尋找文字並將搜尋字串加入至下拉式方塊。  
  
### <a name="adding-the-find-control-to-the-main-toolbar"></a>將尋找控制項加入至主要工具列  
 若要將下拉式方塊按鈕加入至工具列，請依照下列步驟執行：  
  
1.  實作主框架視窗的 `AFX_WM_RESETTOOLBAR` 訊息處理常式 `OnToolbarReset`。  
  
    > [!NOTE]
    >  在應用程式啟動期間工具列初始化時，或當工具列在自訂期間重設時，架構會傳送訊息至主框架視窗。 在任一情況下，您必須取代標準工具列按鈕，以自訂**尋找**下拉式方塊按鈕。  
  
2.  在 `AFX_WM_RESETTOOLBAR`處理常式中，檢查工具列 ID，也就是，則*WPARAM* AFX_WM_RESETTOOLBAR 訊息。 如果工具列 ID 等於包含的工具列**尋找**下拉式方塊按鈕中，呼叫[CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton)來取代**尋找**按鈕 (也就是命令 id 的按鈕`ID_EDIT_FIND)`與`CFindComboButton`物件。  
  
    > [!NOTE]
    >  由於 `CFindComboBox` 會複製按鈕物件並維護複本，因此您可以在堆疊上建構 `ReplaceButton` 物件。  
  
### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>將尋找控制項加入至自訂對話方塊  
 在自訂處理常式`OnViewCustomize`，呼叫[CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)來取代**尋找** 按鈕 (也就是具有命令 ID 的按鈕`ID_EDIT_FIND)`與`CFindComboButton`物件。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../mfc/hierarchy-chart.md)   
 [類別](../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 類別](../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 類別](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCToolBarsCustomizeDialog 類別](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
