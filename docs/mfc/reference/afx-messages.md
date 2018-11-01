---
title: AFX 訊息
ms.date: 11/04/2016
f1_keywords:
- SB_LINELEFT
- SB_THUMBTRACK
- AFX_TOOLTIP_TYPE_EDIT
- AFX_WM_ON_HSCROLL
- SB_PAGERIGHT
- AFX_WM_RESETPROMPT
- AFX_WM_CHANGE_RIBBON_CATEGORY
- AFX_TOOLTIP_TYPE_MINIFRAME
- AFX_WM_CUSTOMIZETOOLBAR
- AFX_WM_CHANGE_ACTIVE_TAB
- AFX_WM_ACCGETOBJECT
- AFX_WM_TOOLBARMENU
- AFX_TOOLTIP_TYPE_DOCKBAR
- AFX_WM_CUSTOMIZEHELP
- AFX_WM_ON_GET_TAB_TOOLTIP
- AFX_WM_ON_RIBBON_CUSTOMIZE
- AFX_WM_ON_DRAGCOMPLETE
- AFX_WM_RESETTOOLBAR
- AFX_WM_ON_MOVETOTABGROUP
- AFX_WM_CHECKEMPTYMINIFRAME
- AFX_WM_GETDOCUMENTCOLORS
- SB_RIGHT
- AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU
- AFX_WM_ACCGETSTATE
- SB_PAGELEFT
- SB_ENDSCROLL
- AFX_WM_ON_CANCELTABMOVE
- AFX_TOOLTIP_TYPE_TAB
- AFX_WM_WINDOW_HELP
- AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM
- AFX_WM_SHOWREGULARMENU
- AFX_TOOLTIP_TYPE_TOOLBAR
- AFX_WM_CHANGE_CURRENT_FOLDER
- AFX_WM_UPDATETOOLTIPS
- AFX_WM_ON_MOVE_TAB
- AFX_WM_CHANGING_ACTIVE_TAB
- AFX_WM_RESETMENU
- AFX_WM_GETDRAGBOUNDS
- AFX_WM_RESETCONTEXTMENU
- AFX_TOOLTIP_TYPE_BUTTON
- AFX_WM_ON_CLOSEPOPUPWINDOW
- AFX_TOOLTIP_TYPE_TOOLBOX
- AFX_WM_CHANGEVISUALMANAGER
- SB_LINERIGHT
- AFX_WM_ON_RENAME_TAB
- AFX_TOOLTIP_TYPE_DEFAULT
- AFX_WM_ON_TABGROUPMOUSEMOVE
- SB_LEFT
- AFX_WM_DELETETOOLBAR
- AFX_WM_PROPERTY_CHANGED
- AFX_TOOLTIP_TYPE_ALL
- AFX_WM_ACCHITTEST
- AFX_WM_ON_AFTER_SHELL_COMMAND
- AFX_WM_ON_PRESS_CLOSE_BUTTON
- AFX_WM_RESETKEYBOARD
- AFX_WM_ON_MOVETABCOMPLETE
- AFX_WM_CREATETOOLBAR
- SB_THUMBPOSITION
- AFX_WM_POSTSETPREVIEWFRAME
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
ms.openlocfilehash: 45c6a9174cbd39c4c0c24ffbdfdefb9d184a3cc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594684"
---
# <a name="afx-messages"></a>AFX 訊息

MFC 中，會使用這些訊息。

## <a name="messages"></a>訊息

下表列出 MFC 程式庫中所使用的訊息：

||||||
|-|-|-|-|-|
|訊息|描述|[in]*wParam*|*lParam* （所有參數都是 [in] 除非另有指明）。|傳回值|
|AFX_WM_ACCGETOBJECT|未使用。|未使用。|不適用。|不適用。|
|AFX_WM_ACCGETSTATE|用於協助工具支援。 傳送此訊息可`CMFCPopupMenu`或`CMFCRibbonPanelMenu`擷取目前項目的狀態。|可能是功能表按鈕或分隔符號項目的索引。|未使用。|項目狀態。 如果索引是無效的則為-1 0，表示功能表按鈕沒有任何特殊的屬性。 否則就是下列旗標的組合：<br /><br /> TBBS_DISABLED： 項目已停用<br /><br /> TBBS_CHECKED： 檢查項目<br /><br /> TBBS_BUTTON-項目是標準的按鈕<br /><br /> TBBS_PRESSED： 按鈕已按下<br /><br /> TBBS_INDETERMINATE： 未定義的狀態<br /><br /> TBBS_SEPARATOR-而不是功能表按鈕，其他功能表項目之間的區隔的此項目表單|
|AFX_WM_CHANGE_ACTIVE_TAB|架構會將此訊息傳送至可調整大小的控制列控制項。 處理此訊息以接收來自通知`CMFCTabCtrl`物件，當使用者變更作用中的索引標籤。|索引標籤的索引。|未使用。|非零值。|
|AFX_WM_CHANGE_CURRENT_FOLDER|架構會將此訊息傳送至的父系`CMFCShellListCtrl`時，使用者已變更目前的資料夾。|未使用。|未使用。|未使用。|
|AFX_WM_CHANGEVISUALMANAGER|架構會將此訊息傳送給所有框架視窗中，當使用者變更目前的視覺化管理員。 為了回應此訊息，框架視窗會重新計算其區域，並視需要調整其他參數。 如果您要收到此事件的通知，您可以在您的應用程式中處理 AFX_WM_CHANGEVISUALMANAGER 訊息。 您必須呼叫基底類別處理常式 (`OnChangeVisualManager`) 以確保架構的內部處理此事件會發生。|未使用。|未使用。|未使用。|
|AFX_WM_CHANGING_ACTIVE_TAB|傳送至父代`CMFCTabCtrl`物件。  處理此訊息，如果您想要接收通知`CMFCTabCtrl`物件時使用者重設 索引標籤。|正在啟動索引標籤的索引。|未使用。|非零值。|
|AFX_WM_CHECKEMPTYMINIFRAME|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_CREATETOOLBAR|從傳送`CMFCToolBarsListPropertyPage`當使用者自訂程序期間建立新的工具列。 您可以處理此訊息可具現化自訂 CMFCToolBar 衍生的物件。 如果您處理此訊息，並建立您自己的工具列，請省略的預設處理常式的呼叫。|未使用。|包含的工具列名稱的字串指標。|新建立的工具列指標。 NULL 表示工具列建立已取消。|
|AFX_WM_CUSTOMIZEHELP|從自訂屬性工作表傳送到主框架視窗`CMFCToolbarCustomize Dialog`當使用者按下**協助**按鈕或 F1 鍵。|指定使用的自訂屬性工作表中的頁面。|`CMFCToolbarCustomize Dialog` 物件的指標。|為零。|
|AFX_WM_CUSTOMIZETOOLBAR|`CMFCToolbarCustomize Dialog`傳送此訊息，通知使用者在建立新的工具列的父框架。|自訂啟動時，FALSE 完成自訂後，則為 TRUE。|未使用。|為零。|
|AFX_WM_DELETETOOLBAR|當使用者即將刪除自訂模式中的工具列，請傳送到主框架視窗。<br /><br /> 處理此訊息採取其他動作，當使用者刪除自訂模式中的工具列。 您也應該呼叫預設處理常式 (`OnToolbarDelete`)，此 cmdlet 會刪除工具列。 預設處理常式會傳回值，指出是否可以刪除工具列。|未使用。|指標`CMFCToolBar`来刪除的物件。|無法刪除工具列; 如果為非零否則為 0。|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` 將此訊息傳送至主框架視窗，以擷取文件色彩。|未使用。|[in、 out]指標`CList<COLORREF, COLORREF>`物件。|為零。|
|AFX_WM_GETDRAGBOUNDS|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|使用者會反白顯示功能區的清單項目時傳送到主框架視窗。|反白顯示的項目索引|指標 `CMFCBaseRibbonElement`|未使用。|
|AFX_WM_ON_AFTER_SHELL_COMMAND|傳送至父代`CMFCShellListCtrl`或`CMFCShellTreeCtrl`控制當使用者在完成執行 shell 命令。|使用者執行命令的識別碼|未使用。|如果應用程式會處理此訊息，它應會傳回零。|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|架構會將此訊息傳送至功能區的父系中之前它會顯示快顯功能表。 您可以處理此訊息，並隨時修改快顯功能表。|未使用。|指標 `CMFCBaseRibbonElement`|未使用。|
|AFX_WM_ON_CANCELTABMOVE|僅供內部使用。|不適用。|不適用。||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|此架構會將此訊息傳送回主框架中，當使用者變更作用中的 [功能區控制項] 類別。|未使用。|指標`CMFCRibbonBar`分類已變更。|未使用。|
|AFX_WM_ON_CLOSEPOPUPWINDOW|此架構會傳送此訊息，通知的擁有者`CMFCDesktopAlertWnd`視窗即將關閉。|未使用。|指標`CMFCDesktopAlertWnd`物件。|未使用。|
|AFX_WM_ON_DRAGCOMPLETE|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_ON_GET_TAB_TOOLTIP|索引標籤視窗即將顯示工具提示的索引標籤中，如果您啟用自訂的工具提示時，傳送到主框架視窗。|未使用。|指標`CMFCTabToolTipInfo`結構。|未使用。|
|AFX_WM_ON_HSCROLL|傳送至可調整大小的控制列控制項。 處理此訊息以接收來自通知`CMFCTabCtrl`物件索引標籤式的小工具水平捲軸的捲動事件發生時。|低序位文字指定捲軸值，指出使用者的捲動要求。  如需詳細資訊，請參閱這個主題稍後的資料表。|未使用。|非零值。|
|AFX_WM_ON_MOVE_TAB|當使用者將索引標籤拖曳到新的位置傳送到索引標籤式視窗的父代。|在其原始位置 索引標籤的以零為起始的索引。|[out]其新位置中的索引標籤的以零為起始的索引。|為零。|
|AFX_WM_ON_MOVETABCOMPLETE|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_ON_MOVETOTABGROUP|當使用者從一個索引標籤式群組的 MDI 子視窗移到另一個時，請傳送至主框架視窗。|索引標籤式視窗的控制代碼 (`CMFCTabCtrl`) 從已移除的 MDI 子視窗它。|[out]索引標籤式視窗的控制代碼 (`CMFCTabCtrl`) 的 MDI 子視窗有已插入。|忽略。|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|傳送至父代`CDockablePane`當使用者按下**關閉**標題的控制列上的按鈕。|未使用。|使用者所按的可停駐窗格的指標**關閉** 按鈕。|如果無法關閉窗格;，則為 TRUE。否則為 FALSE。|
|AFX_WM_ON_RENAME_TAB|之後使用者已重新命名可編輯的索引標籤，請傳送至索引標籤式視窗的父代。|已重新命名的索引標籤的以零為起始的索引。|[out]包含新的索引標籤名稱的字串指標。|非零值，如果應用程式會處理此訊息;架構會抑制呼叫`CMFCBaseTabCtrl::SetTabLabel`。  如果傳回的零，然後`CMFCBaseTabCtrl::SetTabLabel`由架構呼叫。|
|AFX_WM_ON_RIBBON_CUSTOMIZE|當使用者開始自訂傳送到父框架。 如果您想要顯示您自己的自訂對話方塊中，該資料，請處理此訊息。|未使用。|若要自訂功能區控制項指標。|如果應用程式會處理此訊息，並顯示它自己的自訂對話方塊中，非零值。 如果應用程式會傳回零，則架構會顯示內建的自訂對話方塊。|
|AFX_WM_ON_TABGROUPMOUSEMOVE|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_POSTSETPREVIEWFRAME|傳送至通知使用者已變更的預覽列印模式的主要畫面格|TRUE 表示已設定 預覽列印模式。 FALSE 表示該預覽列印模式關閉。|未使用。|未使用。|
|AFX_WM_PROPERTY_CHANGED|傳送至的屬性方格控制項擁有者 (`CMFCPropertyGridCtrl`) 的使用者變更所選屬性的值時。|屬性清單的控制項識別碼。|屬性的指標 (`CMFCPropertyGridProperty`) 已變更。|未使用。|
|AFX_WM_RESETCONTEXTMENU|當使用者重設進行自訂時的操作功能表時，傳送到主框架視窗。|內容功能表中的資源識別碼。|目前的操作功能表中，指標`CMFCPopupMenu`。|未使用。|
|AFX_WM_RESETKEYBOARD|此架構會將此訊息傳送到主框架視窗中，當使用者重設所有的鍵盤快速鍵，在自訂期間。|未使用。|未使用。|未使用。|
|AFX_WM_RESETMENU|架構會將此訊息傳送到功能表的擁有者 （框架視窗） 當使用者重設應用程式框架功能表進行自訂|功能表資源識別碼。|未使用。|未使用。|
|AFX_WM_RESETPROMPT|當使用者重設，從工具列的工具列的自訂對話方塊時，架構就會傳送此訊息。 預設處理常式會顯示訊息方塊，詢問使用者是否要重設工具列。|未使用。|未使用。|未使用。|
|AFX_WM_RESETTOOLBAR|A`CMFCToolBar`工具列會還原到其原始狀態，也就是從資源載入時，物件會傳送此訊息。 處理這個訊息，以便重新插入其類別衍生自的工具列按鈕`CMFCToolbarButton`。 如需詳細資訊，請參閱`CMFCToolbarComboBoxButton`。|工具列，其狀態已還原的資源識別碼。|未使用。|為零。|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` 物件會將此訊息傳送到其擁有者中，當使用者按一下一般功能表按鈕。 處理此訊息，供您每次`CMFCToolbarMenuButton`使用者按一下按鈕時顯示快顯功能表。|傳送訊息 按鈕的命令識別碼。|資料指標的螢幕座標。 的低序位字組指定的 x 座標。 高序位字組指定的 y 座標。|未使用。|
|AFX_WM_TOOLBARMENU|當使用者放開滑鼠右按鈕，在用戶端或非工作區 窗格的滑鼠指標時，傳送到主框架視窗。|未使用。|滑鼠指標的螢幕座標。 的低序位字組指定的 x 座標。 高序位字組指定的 y 座標。|如果應用程式會處理此訊息，則為零否則，非零值。|
|AFX_WM_UPDATETOOLTIPS|表示應該重新建立其工具提示控制項傳送給所有的工具提示擁有者。|應該處理此訊息的控制項型別。 請參閱稍後本主題的可能值的清單。|未使用。|未使用。|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` 將此訊息傳送至父框架中，當使用者按一下**幫助**按鈕，或按一下 輸入說明模式**協助**標題按鈕或 F1 鍵。|未使用。|執行個體的指標`CMFCWindowsManagerDialog`。|未使用。|

下表顯示的值低序位文字*lParam* AFX_WM_HSCROLL 方法的參數：

|||
|-|-|
|值|意義|
|SB_ENDSCROLL|使用者結束捲軸。|
|SB_LEFT|在使用者捲動至左上角。|
|SB_RIGHT|在使用者捲動至右下角。|
|SB_LINELEFT|在使用者捲動左一個單位。|
|SB_LINERIGHT|在使用者捲動一個單位的權限。|
|SB_PAGELEFT|在使用者捲動左旋轉視窗的寬度。|
|SB_PAGERIGHT|使用者會向右捲動視窗的寬度。|
|SB_THUMBPOSITION|使用者有拖曳捲動方塊 （捲動方塊），並放開滑鼠按鈕。 高序位文字表示在拖曳作業結尾處的捲動方塊的位置。|
|SB_THUMBTRACK|使用者正在拖曳捲軸方塊。 使用此值，直到使用者放開滑鼠按鈕 AFX_WM_ON_HSCROLL 訊息會重複傳送。 高序位文字指出已拖曳捲動方塊的位置。|

> [!NOTE]
>  高序位文字*lParam* SB_THUMBPOSITION 或 SB_THUMBTRACK 低序位字組時，參數會指定捲動方塊的目前位置; 否則不會使用這個字。

下表列出的旗標值*lParam* AFX_WM_UPDATETOOLTIPS 訊息參數：

|||
|-|-|
|旗標|值|
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
