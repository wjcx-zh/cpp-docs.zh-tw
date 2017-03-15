---
title: "AFX 訊息 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SB_LINELEFT"
  - "SB_THUMBTRACK"
  - "AFX_TOOLTIP_TYPE_EDIT"
  - "AFX_WM_ON_HSCROLL"
  - "SB_PAGERIGHT"
  - "AFX_WM_RESETPROMPT"
  - "AFX_WM_CHANGE_RIBBON_CATEGORY"
  - "AFX_TOOLTIP_TYPE_MINIFRAME"
  - "AFX_WM_CUSTOMIZETOOLBAR"
  - "AFX_WM_CHANGE_ACTIVE_TAB"
  - "AFX_WM_ACCGETOBJECT"
  - "AFX_WM_TOOLBARMENU"
  - "AFX_TOOLTIP_TYPE_DOCKBAR"
  - "AFX_WM_CUSTOMIZEHELP"
  - "AFX_WM_ON_GET_TAB_TOOLTIP"
  - "AFX_WM_ON_RIBBON_CUSTOMIZE"
  - "AFX_WM_ON_DRAGCOMPLETE"
  - "AFX_WM_RESETTOOLBAR"
  - "AFX_WM_ON_MOVETOTABGROUP"
  - "AFX_WM_CHECKEMPTYMINIFRAME"
  - "AFX_WM_GETDOCUMENTCOLORS"
  - "SB_RIGHT"
  - "AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU"
  - "AFX_WM_ACCGETSTATE"
  - "SB_PAGELEFT"
  - "SB_ENDSCROLL"
  - "AFX_WM_ON_CANCELTABMOVE"
  - "AFX_TOOLTIP_TYPE_TAB"
  - "AFX_WM_WINDOW_HELP"
  - "AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM"
  - "AFX_WM_SHOWREGULARMENU"
  - "AFX_TOOLTIP_TYPE_TOOLBAR"
  - "AFX_WM_CHANGE_CURRENT_FOLDER"
  - "AFX_WM_UPDATETOOLTIPS"
  - "AFX_WM_ON_MOVE_TAB"
  - "AFX_WM_CHANGING_ACTIVE_TAB"
  - "AFX_WM_RESETMENU"
  - "AFX_WM_GETDRAGBOUNDS"
  - "AFX_WM_RESETCONTEXTMENU"
  - "AFX_TOOLTIP_TYPE_BUTTON"
  - "AFX_WM_ON_CLOSEPOPUPWINDOW"
  - "AFX_TOOLTIP_TYPE_TOOLBOX"
  - "AFX_WM_CHANGEVISUALMANAGER"
  - "SB_LINERIGHT"
  - "AFX_WM_ON_RENAME_TAB"
  - "AFX_TOOLTIP_TYPE_DEFAULT"
  - "AFX_WM_ON_TABGROUPMOUSEMOVE"
  - "SB_LEFT"
  - "AFX_WM_DELETETOOLBAR"
  - "AFX_WM_PROPERTY_CHANGED"
  - "AFX_TOOLTIP_TYPE_ALL"
  - "AFX_WM_ACCHITTEST"
  - "AFX_WM_ON_AFTER_SHELL_COMMAND"
  - "AFX_WM_ON_PRESS_CLOSE_BUTTON"
  - "AFX_WM_RESETKEYBOARD"
  - "AFX_WM_ON_MOVETABCOMPLETE"
  - "AFX_WM_CREATETOOLBAR"
  - "SB_THUMBPOSITION"
  - "AFX_WM_POSTSETPREVIEWFRAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFX 訊息"
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# AFX 訊息
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些訊息會用於 MFC。  
  
## 訊息  
 下表列出用於 MFC 程式庫的訊息：  
  
||||||  
|-|-|-|-|-|  
|Message|說明|\[in\] `wParam`|`lParam` \(所有參數為 \[in\]，除非另有說明\)。|傳回值|  
|AFX\_WM\_ACCGETOBJECT|不適用。|不適用。|不適用。|不適用。|  
|AFX\_WM\_ACCGETSTATE|用於協助工具支援。  傳送此訊息給 `CMFCPopupMenu` 或 `CMFCRibbonPanelMenu` 擷取目前項目的狀態。|項目索引，可能是功能表按鈕或分隔符號。|不適用。|項目的狀態。  如果索引無效則為 \-1，如果功能表按鈕沒有特殊屬性則為 0。  否則它會是下列旗標的組合：<br /><br /> TBBS\_DISABLED：項目已停用<br /><br /> TBBS\_CHECKED：項目已選取<br /><br /> TBBS\_BUTTON：項目是標準按鈕<br /><br /> TBBS\_PRESSED：按鈕已被按下<br /><br /> TBBS\_INDETERMINATE：未定義的狀態<br /><br /> TBBS\_SEPARATOR：不是功能表按鈕，這個項目會在其他功能表項目之間形成分隔|  
|AFX\_WM\_CHANGE\_ACTIVE\_TAB|架構會傳送訊息至可調整大小的控制列控制項。  當使用者變更使用中的索引標籤時，請處理這個訊息以接收來自 `CMFCTabCtrl` 物件的通知。|索引標籤的索引。|不適用。|非零。|  
|AFX\_WM\_CHANGE\_CURRENT\_FOLDER|當使用者變更目前資料夾時，架構會傳送訊息給 `CMFCShellListCtrl` 的父代。|不適用。|不適用。|不適用。|  
|AFX\_WM\_CHANGEVISUALMANAGER|當使用者變更目前視覺化管理員時，架構會傳送訊息給所有框架視窗。  為回應這個訊息，框架視窗會依需要重新計算其區域並調整其他參數。  如果需要收到有關這個事件的訊息，您可以處理應用程式的 AFX\_WM\_CHANGEVISUALMANAGER 訊息。  您必須呼叫基底類別處理常式 \(`OnChangeVisualManager`\) 保證這個事件的框架內部處理已發生。|不適用。|不適用。|不適用。|  
|AFX\_WM\_CHANGING\_ACTIVE\_TAB|傳送至 `CMFCTabCtrl` 物件的父代。如果您需要在使用者重設選項時，從 `CMFCTabCtrl` 物件接收通知，請處理這個訊息。|正在使用的索引標籤之索引。|不適用。|非零。|  
|AFX\_WM\_CHECKEMPTYMINIFRAME|僅供內部使用。|不適用。|不適用。|不適用。|  
|AFX\_WM\_CREATETOOLBAR|當使用者在自訂流程中建立新的工具列時，從 `CMFCToolBarsListPropertyPage` 傳送。  您可以處理這個訊息，以具現化一個自訂的 CMFCToolBar 衍生物件。  如果您處理這個訊息並建立自己的工具列，請省略所有的預設處理常式。|不適用。|包含工具列名稱之字串的指標。|新建立之工具列的指標。  NULL 表示工具列建立已取消。|  
|AFX\_WM\_CUSTOMIZEHELP|當使用者按下 \[**說明**\] 按鈕或 F1 鍵時，從自訂屬性工作表 `CMFCToolbarCustomize``Dialog` 傳送到主框架視窗。|指定自訂屬性工作表的使用中的頁面。|`CMFCToolbarCustomize` `Dialog` 物件的指標。|零|  
|AFX\_WM\_CUSTOMIZETOOLBAR|`CMFCToolbarCustomize` `Dialog` 傳送此訊息告知父框架使用者建立新的工具列。|自訂啟動時為 `TRUE`，自訂完成時為 `FALSE`。|不適用。|零|  
|AFX\_WM\_DELETETOOLBAR|當使用者即將在自訂模式刪除一個工具列時，傳送到主框架視窗。<br /><br /> 當使用者在自訂模式刪除一個工具列時，處理這個訊息以採取其他動作。  您也應該呼叫預設處理常式 \(`OnToolbarDelete`\)，刪除工具列。  預設處理常式會傳回值，表示是否可能刪除工具列。|不適用。|要刪除之 `CMFCToolBar` 物件的指標。|如果工具列無法刪除為非零；否則為 0。|  
|AFX\_WM\_GETDOCUMENTCOLORS|`CMFCColorMenuButton` 會傳送訊息至主框架視窗，以擷取文件色彩。|不適用。|\[in, out\] `CList<COLORREF, COLORREF>` 物件的指標。|零|  
|AFX\_WM\_GETDRAGBOUNDS|僅供內部使用。|不適用。|不適用。|不適用。|  
|AFX\_WM\_HIGHLIGHT\_RIBBON\_LIST\_ITEM|當使用者反白顯示功能區清單項目時，傳送到主框架視窗。|反白項目的索引。|`CMFCBaseRibbonElement` 的指標。|不適用。|  
|AFX\_WM\_ON\_AFTER\_SHELL\_COMMAND|當使用者完成執行 Shell 命令時，傳送到 `CMFCShellListCtrl` 或 `CMFCShellTreeCtrl` 控制項的父代。|使用者執行的命令之 ID。|不適用。|如果應用程式處理這個訊息，它應該傳回零。|  
|AFX\_WM\_ON\_BEFORE\_SHOW\_RIBBON\_ITEM\_MENU|在顯示快顯功能表之前，架構會傳送訊息至功能區的父代。  您可以處理這個訊息並隨時修改快顯功能表。|不適用。|`CMFCBaseRibbonElement` 的指標。|不適用。|  
|AFX\_WM\_ON\_CANCELTABMOVE|僅供內部使用。|不適用。|不適用。||  
|AFX\_WM\_ON\_CHANGE\_RIBBON\_CATEGORY|當使用者變更現用功能區控制項類別時，架構會傳送訊息給主框架。|不適用。|對分類已變更之 `CMFCRibbonBar` 的指標。|不適用。|  
|AFX\_WM\_ON\_CLOSEPOPUPWINDOW|架構會傳送通知訊息給視窗即將關閉的  `CMFCDesktopAlertWnd` 之擁有者。|不適用。|指向 `CMFCDesktopAlertWnd` 物件的指標。|不適用。|  
|AFX\_WM\_ON\_DRAGCOMPLETE|僅供內部使用。|不適用。|不適用。|不適用。|  
|AFX\_WM\_ON\_GET\_TAB\_TOOLTIP|如果自訂工具提示已啟用，當索引標籤視窗即將顯示索引標籤的工具提示時，傳送到主框架視窗。|不適用。|`CMFCTabToolTipInfo` 結構的指標。|不適用。|  
|AFX\_WM\_ON\_HSCROLL|傳送至可調整大小的控制列控制項。  當 Scroll 事件在索引標籤式裝飾水平捲軸發生時，請處理這個訊息，以接收來自 `CMFCTabCtrl` 物件的通知。|低序位文字表示指定使用者捲動要求的捲軸值。如需詳細資訊，請參閱這個主題稍後的資料表。|不適用。|非零。|  
|AFX\_WM\_ON\_MOVE\_TAB|當使用者拖曳索引標籤至新位置時，傳送至索引標籤式視窗的父代。|在原始位置之以零起始的索引標籤的索引。|\[out\] 在新位置之以零起始的索引標籤的索引。|零|  
|AFX\_WM\_ON\_MOVETABCOMPLETE|僅供內部使用。|不適用。|不適用。|不適用。|  
|AFX\_WM\_ON\_MOVETOTABGROUP|當使用者將 MDI 子視窗從一個索引標籤式群組移動至另一個群組時，傳送到主框架視窗。|MDI 子視窗被移除的索引標籤式視窗之控制代碼 \(`CMFCTabCtrl`\)。|\[out\] MDI 子視窗被插入的索引標籤式視窗之控制代碼 \(`CMFCTabCtrl`\)。|已忽略。|  
|AFX\_WM\_ON\_PRESS\_CLOSE\_BUTTON|當使用者在控制項標題列中按一下 \[**關閉**\] 按鈕時，傳送至 `CDockablePane` 的父代。|不適用。|使用者按下 \[**關閉**\] 按鈕之可停駐窗格的指標。|如果窗格無法關閉則為 `TRUE`；否則為 false。|  
|AFX\_WM\_ON\_RENAME\_TAB|在使用者重新命名一個可編輯的索引標籤之後，傳送至索引標籤式視窗的父代。|重新命名的索引標籤之以零起始的索引。|\[out\] 一個字串的指標，此字串包含新的索引標籤名稱。|如果應用程式處理序此訊息則為非零；架構會隱藏對 `CMFCBaseTabCtrl::SetTabLabel` 的呼叫。如果傳回零，則 `CMFCBaseTabCtrl::SetTabLabel` 會由架構呼叫。|  
|AFX\_WM\_ON\_RIBBON\_CUSTOMIZE|當使用者啟動自訂時，傳送至父框架。  如果您要顯示自訂對話方塊，請處理這個訊息。|不適用。|要自訂之功能區控制項的指標。|如果應用程式處理這個訊息並顯示其自訂對話方塊，則為非零。  如果應用程式傳回零，架構會顯示內建的自訂對話方塊。|  
|AFX\_WM\_ON\_TABGROUPMOUSEMOVE|僅供內部使用。|不適用。|不適用。|不適用。|  
|AFX\_WM\_POSTSETPREVIEWFRAME|傳送並通知主框架，使用者變更了預覽列印模式|`TRUE` 表示預覽列印模式已設定。  `FALSE` 表示預覽列印模式已關閉。|不適用。|不適用。|  
|AFX\_WM\_PROPERTY\_CHANGED|當使用者變更選取屬性的值，傳送至屬性方格控制項 \(`CMFCPropertyGridCtrl`\) 的擁有者。|屬性清單的控制項 ID。|改變的屬性 \(`CMFCProp``ertyGridProperty`\) 的指標。|不適用。|  
|AFX\_WM\_RESETCONTEXTMENU|當使用者在自訂中重設內容功能表時，傳送到主框架視窗。|內容功能表的資源 ID。|對目前內容功能表 `CMFCPopupMenu` 的指標。|不適用。|  
|AFX\_WM\_RESETKEYBOARD|當使用者在自訂重設所有鍵盤快速鍵時，架構會傳送訊息至主框架視窗。|不適用。|不適用。|不適用。|  
|AFX\_WM\_RESETMENU|當使用者在自訂時重設應用程式架構功能表時，架構會傳送訊息給功能表擁有人 \(Frame Window\)|功能表資源 ID。|不適用。|不適用。|  
|AFX\_WM\_RESETPROMPT|當使用者從工具列自訂對話方塊重設工具列架時，架構會傳送這個訊息。  預設處理常式會顯示訊息方塊，詢問使用者是否要重設工具列。|不適用。|不適用。|不適用。|  
|AFX\_WM\_RESETTOOLBAR|當工具列還原為其原始狀態，也就是從資源中載入時， `CMFCToolBar` 物件會傳送這個資訊。  處理這個訊息，以再插入類別衍生自 `CMFCToolbarButton` 的工具列按鈕。  如需詳細資訊，請參閱`CMFCToolbarComboBoxButton`。|狀態被還原的工具列的資源 ID。|不適用。|零|  
|AFX\_WM\_SHOWREGULARMENU|當使用者按下一般功能表按鈕時，`CMFCToolbarMenuButton` 物件會傳送訊息給它的擁有人。  每次您使用 `CMFCToolbarMenuButton` 時請處理這個訊息，以當使用者按一下按鈕時顯示快顯功能表。|傳送訊息之按鈕的命令 ID。|游標的螢幕座標。  低序位文字表示 X 座標。  高序位文字表示 Y 座標。|不適用。|  
|AFX\_WM\_TOOLBARMENU|當使用者在滑鼠指標在窗格的用戶端或非用戶端區域時放開滑鼠右按鈕，傳送到主框架視窗。|不適用。|滑鼠指標的螢幕座標。  低序位文字表示 X 座標。  高序位文字表示 Y 座標。|如果應用程式處理此訊息則為零；否則為非零。|  
|AFX\_WM\_UPDATETOOLTIPS|傳送至所有工具提示擁有者，表示應該重新建立其工具提示控制項。|應該處理此訊息的控制項型別。  關於可能值的清單，請參閱本主題之後的表格。|不適用。|不適用。|  
|AFX\_WM\_WINDOW\_HELP|當使用者按一下 \[**說明**\] 按鈕時，或按一下 \[**說明**\] 標題按鈕或 F1 鍵進入說明模式時，`CMFCWindowsManagerDialog` 會傳送訊息至父框架。|不適用。|對 `CMFCWindowsManagerDialog` 執行個體的指標。|不適用。|  
  
 下表顯示 AFX\_WM\_HSCROLL 方法的 `lParam` 參數之低位文字的值：  
  
|||  
|-|-|  
|值|意義|  
|SB\_ENDSCROLL|使用者結束捲動。|  
|SB\_LEFT|使用者捲動至左上角。|  
|SB\_RIGHT|使用者捲動至右下角。|  
|SB\_LINELEFT|使用者向左捲動一單位。|  
|SB\_LINERIGHT|使用者向右捲動一單位。|  
|SB\_PAGELEFT|使用者視窗的寬度向左移動。|  
|SB\_PAGERIGHT|使用者視窗的寬度向右移動。|  
|SB\_THUMBPOSITION|使用者拖曳捲動方塊 \(Thumb\) 並放開滑鼠按鈕。  高序位文字表示拖曳作業結束時，捲動方塊的位置。|  
|SB\_THUMBTRACK|使用者正在拖曳捲動方塊。  AFX\_WM\_ON\_HSCROLL 訊息會重複以此值傳送，直到使用者放開滑鼠按鈕。  高序位文字表示捲動方塊曾被拖曳至的位置。|  
  
> [!NOTE]
>  如果低序位文字是 SB\_THUMBPOSITION 或 SB\_THUMBTRACK， `lParam` 參數的高序位文字表示捲動方塊的目前位置；否則，不會使用此文字。  
  
 下表列出 AFX\_WM\_UPDATETOOLTIPS 訊息之 `lParam` 參數的旗標值：  
  
|||  
|-|-|  
|旗標|值|  
|AFX\_TOOLTIP\_TYPE\_DEFAULT|0x0001|  
|AFX\_TOOLTIP\_TYPE\_TOOLBAR|0x0002|  
|AFX\_TOOLTIP\_TYPE\_TAB|0x0004|  
|AFX\_TOOLTIP\_TYPE\_MINIFRAME|0x0008|  
|AFX\_TOOLTIP\_TYPE\_DOCKBAR|0x0010|  
|AFX\_TOOLTIP\_TYPE\_EDIT|0x0020|  
|AFX\_TOOLTIP\_TYPE\_BUTTON|0x0040|  
|AFX\_TOOLTIP\_TYPE\_TOOLBOX|0x0080|  
|AFX\_TOOLTIP\_TYPE\_ALL|0xFFFF|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)