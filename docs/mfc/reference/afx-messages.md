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
ms.openlocfilehash: 409760eff6ba6b31413c11fb45ea91a6d07b9485
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832395"
---
# <a name="afx-messages"></a>AFX 訊息

這些訊息會在 MFC 中使用。

## <a name="messages"></a>訊息

下表列出 MFC 程式庫中使用的訊息：

|訊息|描述|在 *wParam*|除非另有說明，否則*lParam* (所有參數都是 [in]。 ) |傳回值|
|-|-|-|-|-|
|AFX_WM_ACCGETOBJECT|未使用。|未使用。|不適用。|不適用。|
|AFX_WM_ACCGETSTATE|用於協助工具支援。 將此訊息傳送至 `CMFCPopupMenu` 或 `CMFCRibbonPanelMenu` ，以抓取目前專案的狀態。|元素的索引，可能是功能表按鈕或分隔符號。|未使用。|元素狀態。 如果索引無效，則為-1，如果功能表按鈕沒有特殊屬性，則為0。 否則，它是下列旗標的組合：<br /><br /> TBBS_DISABLED-專案已停用<br /><br /> TBBS_CHECKED-已核取專案<br /><br /> TBBS_BUTTON-專案是標準的按鍵<br /><br /> TBBS_PRESSED-已按下按鈕<br /><br /> TBBS_INDETERMINATE-未定義的狀態<br /><br /> TBBS_SEPARATOR （而非功能表按鈕），此元素會形成其他功能表項目之間的分隔|
|AFX_WM_CHANGE_ACTIVE_TAB|架構會將此訊息傳送至可調整大小的控制列控制項。 當使用者變更使用中的索引標籤時，請處理此訊息以接收物件的通知 `CMFCTabCtrl` 。|索引標籤的索引。|未使用。|零。|
|AFX_WM_CHANGE_CURRENT_FOLDER|`CMFCShellListCtrl`當使用者變更了目前的資料夾時，架構會將此訊息傳送至的父系。|未使用。|未使用。|未使用。|
|AFX_WM_CHANGEVISUALMANAGER|當使用者變更目前的視覺管理員時，此架構會將此訊息傳送至所有框架視窗。 為了回應此訊息，框架視窗會重新計算其區域，並視需要調整其他參數。 如果您需要收到有關此事件的通知，您可以在應用程式中處理 AFX_WM_CHANGEVISUALMANAGER 訊息。 您必須 () 呼叫基類處理常式， `OnChangeVisualManager` 以確保此事件的架構內部處理發生。|未使用。|未使用。|未使用。|
|AFX_WM_CHANGING_ACTIVE_TAB|傳送至物件的父系 `CMFCTabCtrl` 。  如果您想要在使用者重設索引標籤時從物件接收通知，請處理此訊息 `CMFCTabCtrl` 。|正在啟用之索引標籤的索引。|未使用。|零。|
|AFX_WM_CHECKEMPTYMINIFRAME|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_CREATETOOLBAR|`CMFCToolBarsListPropertyPage`當使用者在自訂程式期間建立新工具列時傳送。 您可以處理這個訊息，將自訂的 CMFCToolBar 衍生物件具現化。 如果您處理此訊息並建立您自己的工具列，請省略對預設處理常式的呼叫。|未使用。|包含工具列名稱之字串的指標。|新建立之工具列的指標。 Null 表示已取消建立工具列。|
|AFX_WM_CUSTOMIZEHELP|`CMFCToolbarCustomize Dialog`當使用者按下 [說明] 按鈕或 F1 鍵時，從自訂**Help**屬性工作表傳送至主框架視窗。|指定自訂屬性工作表的使用中頁面。|`CMFCToolbarCustomize Dialog` 物件的指標。|零個。|
|AFX_WM_CUSTOMIZETOOLBAR|傳送 `CMFCToolbarCustomize Dialog` 此訊息以通知父框架，使用者正在建立新的工具列。|自訂啟動時為 TRUE，自訂完成時為 FALSE。|未使用。|零個。|
|AFX_WM_DELETETOOLBAR|當使用者即將刪除自訂模式中的工具列時，傳送至主框架視窗。<br /><br /> 當使用者刪除自訂模式中的工具列時，請處理此訊息以採取其他動作。 您也應該呼叫預設處理常式 (`OnToolbarDelete`) ，這會移除工具欄。 預設處理常式會傳回值，指出是否可以移除工具欄。|未使用。|要 `CMFCToolBar` 刪除之物件的指標。|如果無法移除工具欄，則為非零;否則為0。|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` 將此訊息傳送至主框架視窗，以取得檔色彩。|未使用。|[in，out]物件的指標 `CList<COLORREF, COLORREF>` 。|零個。|
|AFX_WM_GETDRAGBOUNDS|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|當使用者反白顯示功能區清單專案時，傳送至主框架視窗。|反白顯示專案的索引|指標，指向 `CMFCBaseRibbonElement`|未使用。|
|AFX_WM_ON_AFTER_SHELL_COMMAND|`CMFCShellListCtrl` `CMFCShellTreeCtrl` 當使用者完成執行 shell 命令時，傳送至的父系或控制項。|使用者執行之命令的識別碼|未使用。|如果應用程式處理此訊息，則應該傳回零。|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|架構會將此訊息傳送至功能區的父系，然後才會顯示快顯功能表。 您可以隨時處理此訊息並修改快顯功能表。|未使用。|指標，指向 `CMFCBaseRibbonElement`|未使用。|
|AFX_WM_ON_CANCELTABMOVE|僅供內部使用。|不適用。|不適用。||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|當使用者變更作用中功能區控制項類別時，架構會將此訊息傳送至主框架。|未使用。|`CMFCRibbonBar`其類別已變更之的指標。|未使用。|
|AFX_WM_ON_CLOSEPOPUPWINDOW|架構會傳送此訊息，以通知要關閉視窗的擁有者 `CMFCDesktopAlertWnd` 。|未使用。|物件的指標 `CMFCDesktopAlertWnd` 。|未使用。|
|AFX_WM_ON_DRAGCOMPLETE|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_ON_GET_TAB_TOOLTIP|當索引標籤視窗即將顯示索引標籤的工具提示時，如果已啟用自訂工具提示，則會傳送至主框架視窗。|未使用。|結構的指標 `CMFCTabToolTipInfo` 。|未使用。|
|AFX_WM_ON_HSCROLL|傳送至可調整大小的控制列控制項。 處理此訊息，以便在索引 `CMFCTabCtrl` 標籤式 widget 水準捲軸中發生滾動事件時，接收物件的通知。|低序位字組指定捲軸值，指出使用者的滾動要求。  如需詳細資訊，請參閱這個主題稍後的資料表。|未使用。|零。|
|AFX_WM_ON_MOVE_TAB|當使用者將索引標籤拖曳至新位置時，傳送至索引標籤式視窗的父系。|索引標籤以零起始的索引（以零為基底）。|擴展索引標籤以零為基底的索引，其位於新的位置。|零個。|
|AFX_WM_ON_MOVETABCOMPLETE|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_ON_MOVETOTABGROUP|當使用者將 MDI 子視窗從一個索引標籤式群組移至另一個時，傳送至主框架視窗。|索引標籤式視窗的控制碼， (`CMFCTabCtrl` 已移除 MDI 子視窗的) 。|擴展索引標籤式視窗的控制碼， (`CMFCTabCtrl` 已插入 MDI 子視窗的) 。|忽略。|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|`CDockablePane`當使用者按一下控制列標題上的 [**關閉**] 按鈕時，傳送至的父系。|未使用。|可停駐窗格的指標，使用者按一下 [ **關閉** ] 按鈕。|如果無法關閉窗格，則為 TRUE;否則為 FALSE。|
|AFX_WM_ON_RENAME_TAB|在使用者重新命名可編輯的索引標籤之後，傳送至索引標籤式視窗的父代。|已重新命名索引標籤之以零為基底的索引。|擴展字串的指標，其中包含新的索引標籤名稱。|如果應用程式處理此訊息，則為非零;架構會抑制的呼叫 `CMFCBaseTabCtrl::SetTabLabel` 。  如果傳回零，則 `CMFCBaseTabCtrl::SetTabLabel` 會由架構呼叫。|
|AFX_WM_ON_RIBBON_CUSTOMIZE|當使用者開始自訂時，傳送至父框架。 如果您想要顯示自己的自訂對話方塊，請處理此訊息。|未使用。|要自訂之功能區控制項的指標。|如果應用程式處理此訊息並顯示自己的自訂對話方塊，則為非零。 如果應用程式傳回零，架構會顯示 [內建自訂] 對話方塊。|
|AFX_WM_ON_TABGROUPMOUSEMOVE|僅供內部使用。|不適用。|不適用。|不適用。|
|AFX_WM_POSTSETPREVIEWFRAME|傳送以通知主框架使用者變更了預覽列印模式|TRUE 表示已設定預覽列印模式。 FALSE 表示預覽列印模式已關閉。|未使用。|未使用。|
|AFX_WM_PROPERTY_CHANGED|`CMFCPropertyGridCtrl`當使用者變更選取之屬性的值時，傳送至屬性方格控制項的擁有者 () 。|屬性清單的控制項識別碼。|已變更之屬性 () 的指標 `CMFCPropertyGridProperty` 。|未使用。|
|AFX_WM_RESETCONTEXTMENU|當使用者在自訂期間重設內容功能表時，傳送至主框架視窗。|內容功能表的資源識別碼。|指向目前內容功能表的指標 `CMFCPopupMenu` 。|未使用。|
|AFX_WM_RESETKEYBOARD|當使用者在自訂期間重設所有鍵盤加速器時，架構會將此訊息傳送至主框架視窗。|未使用。|未使用。|未使用。|
|AFX_WM_RESETMENU|當使用者在自訂期間重設應用程式框架功能表時，架構會將此訊息傳送給功能表擁有者 (框架視窗) |功能表資源識別碼。|未使用。|未使用。|
|AFX_WM_RESETPROMPT|當使用者從工具列 [自訂] 對話方塊重設工具列時，架構會傳送此訊息。 預設處理常式會顯示訊息方塊，詢問使用者是否要重設工具列。|未使用。|未使用。|未使用。|
|AFX_WM_RESETTOOLBAR|`CMFCToolBar`當工具列還原為其原始狀態（也就是從資源載入）時，物件會傳送此訊息。 處理此訊息以重新插入其類別衍生自的工具列按鈕 `CMFCToolbarButton` 。 如需詳細資訊，請參閱`CMFCToolbarComboBoxButton`。|已還原其狀態之工具列的資源識別碼。|未使用。|零個。|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` 當使用者按一下一般功能表按鈕時，物件會將此訊息傳送給其擁有者。 當您在 `CMFCToolbarMenuButton` 使用者按一下按鈕時，每次使用來顯示快顯功能表時，請處理此訊息。|傳送訊息之按鈕的命令識別碼。|資料指標的螢幕座標。 低序位字組指定 x 座標。 高序位字組指定 y 座標。|未使用。|
|AFX_WM_TOOLBARMENU|當使用者放開滑鼠右鍵時，當滑鼠指標位於窗格的用戶端或非工作區時，傳送至主框架視窗。|未使用。|滑鼠指標的螢幕座標。 低序位字組指定 x 座標。 高序位字組指定 y 座標。|如果應用程式處理此訊息，則為零。否則為非零。|
|AFX_WM_UPDATETOOLTIPS|傳送至所有工具提示擁有者，以指出應該重新建立其工具提示控制項。|應該處理此訊息的控制項類型。 如需可能值的清單，請參閱本主題稍後的表格。|未使用。|未使用。|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` 當使用者 **按一下 [說明** ] 按鈕，或按一下 [說明 **] 標題按鈕** 或 F1 鍵進入 [說明] 模式時，會將此訊息傳送至父框架。|未使用。|實例的指標 `CMFCWindowsManagerDialog` 。|未使用。|

下表顯示 AFX_WM_HSCROLL 方法之 *lParam* 參數的低字組值：

|值|意義|
|-|-|
|SB_ENDSCROLL|使用者結束捲軸。|
|SB_LEFT|使用者會滾動至左上方。|
|SB_RIGHT|使用者會向右下方滾動。|
|SB_LINELEFT|使用者向左滾動一個單位。|
|SB_LINERIGHT|使用者向右滾動一個單位。|
|SB_PAGELEFT|使用者會以視窗的寬度向左滾動。|
|SB_PAGERIGHT|使用者會向右滾動視窗的寬度。|
|SB_THUMBPOSITION|使用者已拖曳捲動方塊 (thumb) 並放開滑鼠按鍵。 高序位單字表示在拖曳作業結束時，捲動方塊的位置。|
|SB_THUMBTRACK|使用者正在拖曳捲軸方塊。 AFX_WM_ON_HSCROLL 的訊息會以這個值重複傳送，直到使用者放開滑鼠按鍵為止。 高序位單字表示拖曳捲動方塊的位置。|

> [!NOTE]
> 若 SB_THUMBPOSITION 或 SB_THUMBTRACK 低序位字組，則 *lParam* 參數的高序位單字會指定捲動方塊的目前位置。否則，就不會使用這個字。

下表列出 AFX_WM_UPDATETOOLTIPS 訊息的 *lParam* 參數旗標值：

|旗標|值|
|-|-|
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
