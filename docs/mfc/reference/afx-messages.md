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
ms.openlocfilehash: b4ed86c11d3c5b5f1ce38e3146533109f3a6b00d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363589"
---
# <a name="afx-messages"></a>AFX 訊息

這些消息在 MFC 中使用。

## <a name="messages"></a>訊息

下表列出了在 MFC 庫中使用的消息:

||||||
|-|-|-|-|-|
|訊息|描述|[在]*wParam*|*lParam* (除非另有說明,否則所有參數均處於[in]。|傳回值|
|AFX_WM_ACCGETOBJECT|未使用。|未使用。|不適用。|不適用。|
|AFX_WM_ACCGETSTATE|用於輔助功能支援。 將此訊息發送到`CMFCPopupMenu``CMFCRibbonPanelMenu`或檢索當前元素的狀態。|元素的索引,可以是菜單按鈕或分隔符。|未使用。|元素狀態。 如果索引無效,則為 -1;如果功能表按鈕沒有特殊屬性,則為 0。 否則,它是以下標誌的組合:<br /><br /> 關閉TBBS_DISABLED = 項目<br /><br /> TBBS_CHECKED = 專案已選取<br /><br /> TBBS_BUTTON = 該項目是標準按鈕<br /><br /> 按下TBBS_PRESSED = 按鈕<br /><br /> TBBS_INDETERMINATE = 未定義狀態<br /><br /> TBBS_SEPARATOR - 而不是選單按鈕,此元素形成其他選單項之間的分隔|
|AFX_WM_CHANGE_ACTIVE_TAB|框架將此訊息發送到可調整大小的控制欄控制項。 處理此消息以在使用者更改活動`CMFCTabCtrl`選項卡時接收來自物件的通知。|選項卡的索引。|未使用。|零。|
|AFX_WM_CHANGE_CURRENT_FOLDER|當使用者更改當前資料夾`CMFCShellListCtrl`時,框架會將此消息發送到 父級。|未使用。|未使用。|未使用。|
|AFX_WM_CHANGEVISUALMANAGER|當使用者更改當前可視化管理器時,框架會將此消息發送到所有框架視窗。 為了回應此消息,幀視窗重新計算其區域並根據需要調整其他參數。 如果需要有關此事件的通知,可以在應用程式中處理AFX_WM_CHANGEVISUALMANAGER消息。 您必須呼叫基類別處理程式`OnChangeVisualManager`( 以確保框架對此事件的內部處理發生。|未使用。|未使用。|未使用。|
|AFX_WM_CHANGING_ACTIVE_TAB|傳送到物件的父`CMFCTabCtrl`層 。  如果要在使用者重置選項卡時接收來自`CMFCTabCtrl`物件的通知,請處理此消息。|正在啟動的選項卡的索引。|未使用。|零。|
|AFX_WM_CHECKEMPTYMINIFRAME|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_CREATETOOLBAR|在`CMFCToolBarsListPropertyPage`自定義過程中用戶創建新工具列時發送。 您可以處理此消息以實例化自定義 CMFCToolBar 派生的物件。 如果處理此消息並創建自己的工具列,請省略對預設處理程式的調用。|未使用。|指向包含工具列名稱的字串的指標。|指向新創建的工具列的指標。 NULL 表示工具列創建已取消。|
|AFX_WM_CUSTOMIZEHELP|當使用者按下 **「説明」** 按鈕或`CMFCToolbarCustomize Dialog`F1 鍵時,從自定義屬性工作表發送到主框架視窗。|指定自定義屬性表的活動頁。|`CMFCToolbarCustomize Dialog` 物件的指標。|零個。|
|AFX_WM_CUSTOMIZETOOLBAR|發送`CMFCToolbarCustomize Dialog`此消息以通知父幀使用者正在創建新工具列。|當自定義啟動時為 TRUE,自定義完成後 FALSE。|未使用。|零個。|
|AFX_WM_DELETETOOLBAR|當使用者要在自定義模式下刪除工具列時,發送到主框架視窗。<br /><br /> 處理此消息,當使用者在自定義模式下刪除工具列時執行其他操作。 還應呼叫預設處理程式`OnToolbarDelete`( , 刪除工具列。 預設處理程式返回一個值,指示是否可以刪除工具列。|未使用。|指向要刪除`CMFCToolBar`的物件的指標。|如果無法刪除工具列,則非零;否則 0。|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton`將此訊息發送到主框架視窗以檢索文件顏色。|未使用。|[進出]指向物件的指標`CList<COLORREF, COLORREF>`。|零個。|
|AFX_WM_GETDRAGBOUNDS|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|當使用者突出顯示功能區清單項時發送到主框架視窗。|突顯項目的索引|指向`CMFCBaseRibbonElement`|未使用。|
|AFX_WM_ON_AFTER_SHELL_COMMAND|當使用者完成執行 shell`CMFCShellListCtrl``CMFCShellTreeCtrl`命令時,已發送到或控制項的父項。|使用者執行的指令的識別碼|未使用。|如果應用程式處理此消息,則應返回零。|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|框架在顯示彈出功能表之前,會將此消息發送給功能區父級。 您可以隨時處理此消息並修改彈出式功能表。|未使用。|指向`CMFCBaseRibbonElement`|未使用。|
|AFX_WM_ON_CANCELTABMOVE|僅供內部使用。|不適用。|不適用。||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|當使用者更改活動功能區控制類別時,框架會將此消息發送到主框架。|未使用。|指向其類別已更改`CMFCRibbonBar`的的指標。|未使用。|
|AFX_WM_ON_CLOSEPOPUPWINDOW|框架發送此消息以通知所有者`CMFCDesktopAlertWnd`視窗即將關閉。|未使用。|指向`CMFCDesktopAlertWnd`物件的指標。|未使用。|
|AFX_WM_ON_DRAGCOMPLETE|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_ON_GET_TAB_TOOLTIP|如果啟用了自定義工具提示,則當選項卡視窗要顯示選項卡的工具提示時,發送到主框架視窗。|未使用。|指向結構的`CMFCTabToolTipInfo`指標。|未使用。|
|AFX_WM_ON_HSCROLL|發送到可調整大小的控制欄控制項。 處理此消息,在選項卡式小`CMFCTabCtrl`部件水平滾動欄中發生滾動事件時接收來自物件的通知。|低階單詞指定指示使用者滾動請求的滾動條值。  如需詳細資訊，請參閱這個主題稍後的資料表。|未使用。|零。|
|AFX_WM_ON_MOVE_TAB|當使用者將選項卡拖動到新位置時,已發送到選項卡視窗的父級。|選項卡的原始位置的零基索引。|[出]選項卡的新位置的零基索引。|零個。|
|AFX_WM_ON_MOVETABCOMPLETE|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_ON_MOVETOTABGROUP|當使用者將 MDI 子視窗從一個選項卡式組移動到另一個選項卡式組時,已發送到主框架視窗。|選項卡式視窗`CMFCTabCtrl`( ) 的句柄,從中刪除 MDI 子視窗。|[出]已插入 MDI`CMFCTabCtrl`子 視窗的選項卡式視窗的句柄。|忽略。|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|將使用者按一下控制`CDockablePane`欄標題上的 **「關閉**」按鈕時發送到父級。|未使用。|指向可停靠窗格的指標,用戶按下**其關閉「** 按鈕。|如果窗格無法關閉,則為 TRUE;如果窗格無法關閉,則為 TRUE。否則 FALSE。|
|AFX_WM_ON_RENAME_TAB|在使用者重新命名可編輯選項卡後,發送到選項卡式視窗的父級。|重命名選項卡的零基索引。|[出]指向包含新選項卡名稱的字串的指標。|如果應用程式處理此消息,則非零;框架將禁止對`CMFCBaseTabCtrl::SetTabLabel`的調用。  如果返回零,則`CMFCBaseTabCtrl::SetTabLabel`由框架調用。|
|AFX_WM_ON_RIBBON_CUSTOMIZE|當用戶開始自定義時發送到父框架。 如果要顯示自己的自定義對話框,請處理此消息。|未使用。|指向要自定義的功能區控件的指標。|如果應用程式處理此消息並顯示其自己的自定義對話框,則為非零。 如果應用程式返回零,框架將顯示內置自定義對話方塊。|
|AFX_WM_ON_TABGROUPMOUSEMOVE|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_POSTSETPREVIEWFRAME|已送出以通知主框架使用者更改列印預覽模式|TRUE 表示已設置列印預覽模式。 FALSE 表示列印預覽模式已關閉。|未使用。|未使用。|
|AFX_WM_PROPERTY_CHANGED|當使用者更改所選屬性的值時,將發送到屬性`CMFCPropertyGridCtrl`網格控件 ( ) 的擁有者。|屬性清單的控制 ID。|指定屬性的`CMFCPropertyGridProperty`指標 。|未使用。|
|AFX_WM_RESETCONTEXTMENU|當使用者在自定義期間重置上下文功能表時發送到主框架視窗。|上下文菜單的資源 ID。|在目前內容選單的指標`CMFCPopupMenu`。|未使用。|
|AFX_WM_RESETKEYBOARD|當使用者在自定義期間重置所有鍵盤快速鍵時,框架會將此消息發送到主框架視窗。|未使用。|未使用。|未使用。|
|AFX_WM_RESETMENU|當使用者在自訂期間重置應用程式框架選單時,框架會將此訊息發送給選單擁有者(框架視窗)|功能表資源識別碼。|未使用。|未使用。|
|AFX_WM_RESETPROMPT|當使用者從工具列自定義對話框重置工具列時,框架將發送此消息。 預設處理程式顯示一個訊息框,詢問使用者是否要重置工具列。|未使用。|未使用。|未使用。|
|AFX_WM_RESETTOOLBAR|當`CMFCToolBar`工具列還原到其原始狀態(即從資源載入)時,物件將發送此消息。 處理此消息以重新插入其類派生自`CMFCToolbarButton`的工具列按鈕。 如需詳細資訊，請參閱 `CMFCToolbarComboBoxButton`。|已還原狀態的工具列的資源 ID。|未使用。|零個。|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton`當用戶單擊常規功能表按鈕時,物件會向其擁有者發送此消息。 每次用戶按下按鈕時,您都`CMFCToolbarMenuButton`用於顯示彈出功能表時處理此消息。|發送消息的按鈕的命令 ID。|游標的螢幕座標。 低階單詞指定 x 座標。 高階單詞指定 y 座標。|未使用。|
|AFX_WM_TOOLBARMENU|當使用者釋放滑鼠的右鍵時,當滑鼠指標位於窗格的用戶端或非用戶端區域時,發送到主框架視窗。|未使用。|滑鼠指標的螢幕座標。 低階單詞指定 x 座標。 高階單詞指定 y 座標。|如果應用程式處理此消息,則為零;如果應用程式處理此消息,則為零。否則,非零。|
|AFX_WM_UPDATETOOLTIPS|發送給所有工具提示擁有者,以指示應重新創建其工具提示控制項。|應處理此消息的控件的類型。 有關可能值的清單,請參閱本主題後面的表。|未使用。|未使用。|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog`當使用者按下 **「説明」** 按鈕時,將此消息發送到父幀,或者通過按一下 **「幫助**標題」按鈕或 F1 鍵進入説明模式。|未使用。|指向 的實例`CMFCWindowsManagerDialog`的指標。|未使用。|

下表顯示AFX_WM_HSCROLL方法的*lParam*參數的低字的值:

|||
|-|-|
|值|意義|
|SB_ENDSCROLL|用戶結束滾動。|
|SB_LEFT|使用者滾動到左上角。|
|SB_RIGHT|使用者滾動到右下角。|
|SB_LINELEFT|用戶滾動由一個單位左。|
|SB_LINERIGHT|使用者按一個單位向右滾動。|
|SB_PAGELEFT|使用者按視窗的寬度向左滾動。|
|SB_PAGERIGHT|使用者按視窗的寬度向右滾動。|
|SB_THUMBPOSITION|使用者已拖動滾動框(拇指)並釋放滑鼠按鈕。 高階單詞指示滾動框在拖動操作結束時的位置。|
|SB_THUMBTRACK|使用者正在拖曳捲軸方塊。 在使用者釋放滑鼠按鈕之前,使用此值重複發送AFX_WM_ON_HSCROLL消息。 高階單詞指示滾動框已拖動到的位置。|

> [!NOTE]
> 如果低階詞SB_THUMBPOSITION或SB_THUMBTRACK,*則 lParam*參數的高階字指定滾動框的當前位置;否則,不使用這個詞。

下表列出了 AFX_WM_UPDATETOOLTIPS訊息的*lParam*參數的標誌值:

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
