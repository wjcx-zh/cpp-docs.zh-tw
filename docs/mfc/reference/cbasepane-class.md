---
title: "CBasePane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBasePane::get_accKeyboardShortcut"
  - "CBasePane.get_accKeyboardShortcut"
  - "CBasePane.accSelect"
  - "get_accDefaultAction"
  - "accSelect"
  - "CBasePane.accHitTest"
  - "CBasePane.get_accRole"
  - "get_accKeyboardShortcut"
  - "CBasePane::Serialize"
  - "CBasePane"
  - "CBasePane::get_accDefaultAction"
  - "get_accParent"
  - "CBasePane::accSelect"
  - "accLocation"
  - "CBasePane.get_accDescription"
  - "get_accName"
  - "CBasePane::get_accChildCount"
  - "CBasePane.get_accChild"
  - "CBasePane::accHitTest"
  - "accHitTest"
  - "get_accHelp"
  - "CBasePane.get_accChildCount"
  - "CBasePane.get_accValue"
  - "CBasePane::get_accDescription"
  - "get_accChildCount"
  - "CBasePane.accLocation"
  - "CBasePane.PreTranslateMessage"
  - "CBasePane.get_accName"
  - "PreTranslateMessage"
  - "CBasePane::get_accFocus"
  - "get_accDescription"
  - "CBasePane::get_accRole"
  - "get_accValue"
  - "CBasePane.Serialize"
  - "CBasePane::accLocation"
  - "get_accRole"
  - "CBasePane::get_accChild"
  - "get_accFocus"
  - "CBasePane::get_accHelp"
  - "CBasePane.get_accDefaultAction"
  - "CBasePane.get_accHelp"
  - "CBasePane::PreTranslateMessage"
  - "CBasePane::get_accState"
  - "CBasePane.get_accParent"
  - "CBasePane::get_accParent"
  - "get_accChild"
  - "CBasePane::get_accValue"
  - "Serialize"
  - "get_accState"
  - "CBasePane.get_accState"
  - "CBasePane.get_accFocus"
  - "CBasePane::get_accName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accHitTest method"
  - "accLocation method"
  - "accSelect method"
  - "CBasePane class"
  - "get_accChild method"
  - "get_accChildCount method"
  - "get_accDefaultAction method"
  - "get_accDescription method"
  - "get_accFocus method"
  - "get_accHelp method"
  - "get_accKeyboardShortcut method"
  - "get_accName method"
  - "get_accParent method"
  - "get_accRole method"
  - "get_accState method"
  - "get_accValue method"
  - "PreTranslateMessage method"
  - "Serialize method"
ms.assetid: 8163dd51-d7c7-4def-9c74-61f8ecdfad82
caps.latest.revision: 43
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 44
---
# CBasePane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所有窗格的基底類別實作。  
  
## 語法  
  
```  
class CBasePane : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CBasePane::CBasePane`|預設建構函式。|  
|`CBasePane::~CBasePane`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CBasePane::accHitTest`|呼叫由架構擷取子項目或子物件在畫面上的指定點。  \(覆寫 [CWnd::accHitTest](../Topic/CWnd::accHitTest.md)\)。|  
|`CBasePane::accLocation`|呼叫由架構擷取指定物件的目前螢幕位置。  \(覆寫 [CWnd::accLocation](../Topic/CWnd::accLocation.md)\)。|  
|[CBasePane::AccNotifyObjectFocusEvent](../Topic/CBasePane::AccNotifyObjectFocusEvent.md)|`CBasePane` 不使用這個方法。|  
|`CBasePane::accSelect`|呼叫框架修改選取範圍或移動指定物件的鍵盤焦點。  \(覆寫 [CWnd::accSelect](../Topic/CWnd::accSelect.md)\)。|  
|[CBasePane::AddPane](../Topic/CBasePane::AddPane.md)|將處理常式加入至停駐窗格。|  
|[CBasePane::AdjustDockingLayout](../Topic/CBasePane::AdjustDockingLayout.md)|將一個呼叫重新導向至停駐管理員調整停駐配置。|  
|[CBasePane::AdjustLayout](../Topic/CBasePane::AdjustLayout.md)|呼叫框架，該窗格應該調整其內部設定。|  
|[CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)|計算控制列的水平大小。|  
|[CBasePane::CanAcceptPane](../Topic/CBasePane::CanAcceptPane.md)|判斷其他窗格是否可以停駐窗格。|  
|[CBasePane::CanAutoHide](../Topic/CBasePane::CanAutoHide.md)|判斷  窗格是否支援自動隱藏模式。|  
|[CBasePane::CanBeAttached](../Topic/CBasePane::CanBeAttached.md)|判斷是否可停駐窗格加入至另一個窗格。|  
|[CBasePane::CanBeClosed](../Topic/CBasePane::CanBeClosed.md)|判斷窗格是否可以關閉。|  
|[CBasePane::CanBeDocked](../Topic/CBasePane::CanBeDocked.md)|判斷是否可停駐窗格加入至另一個窗格。|  
|[CBasePane::CanBeResized](../Topic/CBasePane::CanBeResized.md)|判斷窗格是否可以調整大小。|  
|[CBasePane::CanBeTabbedDocument](../Topic/CBasePane::CanBeTabbedDocument.md)|指定窗格是否可以轉換為 MDI 索引標籤式文件。|  
|[CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md)|判斷是否可以浮動窗格。|  
|[CBasePane::CanFocus](../Topic/CBasePane::CanFocus.md)|指定窗格是否可以接收焦點。|  
|[CBasePane::CopyState](../Topic/CBasePane::CopyState.md)|複製指定窗格的狀態。|  
|[CBasePane::CreateDefaultMiniframe](../Topic/CBasePane::CreateDefaultMiniframe.md)|如果可以浮動窗格，建立小型框架視窗。|  
|[CBasePane::CreateEx](../Topic/CBasePane::CreateEx.md)|建立窗格控制項。|  
|[CBasePane::DockPane](../Topic/CBasePane::DockPane.md)|停駐窗格加入至另一個窗格或到框架視窗。|  
|[CBasePane::DockPaneUsingRTTI](../Topic/CBasePane::DockPaneUsingRTTI.md)|您可以使用執行階段型別資訊，停駐窗格。|  
|[CBasePane::DockToFrameWindow](../Topic/CBasePane::DockToFrameWindow.md)|內建可停駐窗格至框架。|  
|[CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)|判斷其他窗格是否能夠以動態方式插入這個窗格和父框架之間。|  
|[CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md)|啟用窗格的停駐到主要畫面格。|  
|[CBasePane::EnableGripper](../Topic/CBasePane::EnableGripper.md)|啟用或停用移駐夾。  移駐夾有效，使用者可以將它重新定位窗格。|  
|`CBasePane::FillWindowRect`|內部使用。|  
|[CBasePane::FloatPane](../Topic/CBasePane::FloatPane.md)|浮動窗格。|  
|`CBasePane::get_accChild`|呼叫由架構擷取一 `IDispatch` 介面位址指定的子系。  \(覆寫 [CWnd::get\_accChild](../Topic/CWnd::get_accChild.md)\)。|  
|`CBasePane::get_accChildCount`|呼叫由架構擷取屬於這個物件的子系數目。  \(覆寫 [CWnd::get\_accChildCount](../Topic/CWnd::get_accChildCount.md)\)。|  
|`CBasePane::get_accDefaultAction`|呼叫由架構擷取描述物件的預設動作的字串。  \(覆寫 [CWnd::get\_accDefaultAction](../Topic/CWnd::get_accDefaultAction.md)\)。|  
|`CBasePane::get_accDescription`|呼叫由架構擷取描述指定物件之視覺外觀的字串。  \(覆寫 [CWnd::get\_accDescription](../Topic/CWnd::get_accDescription.md)\)。|  
|`CBasePane::get_accFocus`|呼叫由架構擷取具有鍵盤焦點的物件。  \(覆寫 [CWnd::get\_accFocus](../Topic/CWnd::get_accFocus.md)\)。|  
|`CBasePane::get_accHelp`|呼叫由架構擷取物件的說明屬性字串。  \(覆寫 [CWnd::get\_accHelp](../Topic/CWnd::get_accHelp.md)\)。|  
|[CBasePane::get\_accHelpTopic](../Topic/CBasePane::get_accHelpTopic.md)|呼叫由架構擷取與指定的物件和適當的主題識別項在該檔案中 WinHelpfile的完整路徑。  \(覆寫 [CWnd::get\_accHelpTopic](../Topic/CWnd::get_accHelpTopic.md)\)。|  
|`CBasePane::get_accKeyboardShortcut`|呼叫由架構擷取物件的指定快速鍵。  \(覆寫 [CWnd::get\_accKeyboardShortcut](../Topic/CWnd::get_accKeyboardShortcut.md)\)。|  
|`CBasePane::get_accName`|呼叫由架構擷取指定物件的名稱。  \(覆寫 [CWnd::get\_accName](../Topic/CWnd::get_accName.md)\)。|  
|`CBasePane::get_accParent`|呼叫由架構擷取物件的父代的 `IDispatch` 介面。  \(覆寫 [CWnd::get\_accParent](../Topic/CWnd::get_accParent.md)\)。|  
|`CBasePane::get_accRole`|呼叫由架構擷取描述指定之物件的相關資訊。  \(覆寫 [CWnd::get\_accRole](../Topic/CWnd::get_accRole.md)\)。|  
|[CBasePane::get\_accSelection](../Topic/CBasePane::get_accSelection.md)|呼叫由架構來擷取這個的選項之子系的物件。  \(覆寫 [CWnd::get\_accSelection](../Topic/CWnd::get_accSelection.md)\)。|  
|`CBasePane::get_accState`|呼叫由架構擷取指定物件的目前狀態。  \(覆寫 [CWnd::get\_accState](../Topic/CWnd::get_accState.md)\)。|  
|`CBasePane::get_accValue`|呼叫由架構擷取指定物件的值。  \(覆寫 [CWnd::get\_accValue](../Topic/CWnd::get_accValue.md)\)。|  
|[CBasePane::GetCaptionHeight](../Topic/CBasePane::GetCaptionHeight.md)|傳回標題高度。|  
|[CBasePane::GetControlBarStyle](../Topic/CBasePane::GetControlBarStyle.md)|傳回控制項的樣式。|  
|[CBasePane::GetCurrentAlignment](../Topic/CBasePane::GetCurrentAlignment.md)|傳回目前窗格對齊。|  
|[CBasePane::GetDockingMode](../Topic/CBasePane::GetDockingMode.md)|傳回目前停駐窗格的方式。|  
|[CBasePane::GetDockSiteFrameWnd](../Topic/CBasePane::GetDockSiteFrameWnd.md)|會將指標傳至檔案是窗格的停駐網站的視窗。|  
|[CBasePane::GetEnabledAlignment](../Topic/CBasePane::GetEnabledAlignment.md)|傳回套用至  窗格中的 CBRS\_ALIGN\_ 樣式。|  
|[CBasePane::GetMFCStyle](../Topic/CBasePane::GetMFCStyle.md)|傳回窗格樣式專屬於 MFC。|  
|[CBasePane::GetPaneIcon](../Topic/CBasePane::GetPaneIcon.md)|將控制代碼傳回給窗格圖示。|  
|`CBasePane::GetPaneRect`|內部使用。|  
|[CBasePane::GetPaneRow](../Topic/CBasePane::GetPaneRow.md)|傳回指向窗格停駐的 [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)物件。|  
|[CBasePane::GetPaneStyle](../Topic/CBasePane::GetPaneStyle.md)|傳回窗格樣式。|  
|[CBasePane::GetParentDockSite](../Topic/CBasePane::GetParentDockSite.md)|會將指標傳至父內建網站。|  
|[CBasePane::GetParentMiniFrame](../Topic/CBasePane::GetParentMiniFrame.md)|會將指標傳至父小型框架視窗。|  
|[CBasePane::GetParentTabbedPane](../Topic/CBasePane::GetParentTabbedPane.md)|會將指標傳至父代的索引窗格。|  
|[CBasePane::GetParentTabWnd](../Topic/CBasePane::GetParentTabWnd.md)|會將指標傳至索引標籤內的父視窗。|  
|[CBasePane::GetRecentVisibleState](../Topic/CBasePane::GetRecentVisibleState.md)|在  窗格中，從檔案還原時，架構會呼叫這個方法。|  
|[CBasePane::HideInPrintPreviewMode](../Topic/CBasePane::HideInPrintPreviewMode.md)|指定窗格是否在預覽列印隱藏。|  
|[CBasePane::InsertPane](../Topic/CBasePane::InsertPane.md)|註冊處理常式的指定停駐的窗格。|  
|[CBasePane::IsAccessibilityCompatible](../Topic/CBasePane::IsAccessibilityCompatible.md)|指定窗格是否支援 Active Accessibility。|  
|[CBasePane::IsAutoHideMode](../Topic/CBasePane::IsAutoHideMode.md)|判斷是否在窗格自動隱藏模式。|  
|[CBasePane::IsDialogControl](../Topic/CBasePane::IsDialogControl.md)|指定窗格是否為對話方塊控制項。|  
|[CBasePane::IsDocked](../Topic/CBasePane::IsDocked.md)|判斷是否停駐窗格。|  
|[CBasePane::IsFloating](../Topic/CBasePane::IsFloating.md)|判斷是否浮動窗格。|  
|[CBasePane::IsHorizontal](../Topic/CBasePane::IsHorizontal.md)|判斷是否水平停駐窗格。|  
|[CBasePane::IsInFloatingMultiPaneFrameWnd](../Topic/CBasePane::IsInFloatingMultiPaneFrameWnd.md)|指定窗格是否在多窗格框架視窗。|  
|[CBasePane::IsMDITabbed](../Topic/CBasePane::IsMDITabbed.md)|判斷窗格是否已加入至 MDI 子視窗，因為一個索引標籤式文件。|  
|[CBasePane::IsPaneVisible](../Topic/CBasePane::IsPaneVisible.md)|指定 `WS_VISIBLE` 旗標是否已設定窗格。|  
|[CBasePane::IsPointNearDockSite](../Topic/CBasePane::IsPointNearDockSite.md)|判斷指定的點是否包含在固定網站附近。|  
|[CBasePane::IsResizable](../Topic/CBasePane::IsResizable.md)|判斷窗格是否可以調整大小。|  
|[CBasePane::IsRestoredFromRegistry](../Topic/CBasePane::IsRestoredFromRegistry.md)|判斷  窗格是否從註冊還原。|  
|[CBasePane::IsTabbed](../Topic/CBasePane::IsTabbed.md)|判斷是否在窗格的索引標籤式視窗的索引標籤控制項會在此處。|  
|`CBasePane::IsTooltipTopmost`|內部使用。|  
|[CBasePane::IsVisible](../Topic/CBasePane::IsVisible.md)|判斷窗格是否可見。|  
|[CBasePane::LoadState](../Topic/CBasePane::LoadState.md)|從登錄載入窗格狀態。|  
|[CBasePane::MoveWindow](../Topic/CBasePane::MoveWindow.md)|捲動窗格。|  
|[CBasePane::OnAfterChangeParent](../Topic/CBasePane::OnAfterChangeParent.md)|呼叫框架，在變更窗格的父代。|  
|[CBasePane::OnBeforeChangeParent](../Topic/CBasePane::OnBeforeChangeParent.md)|在  窗格中呼叫之前的框架變更它的父視窗。|  
|[CBasePane::OnDrawCaption](../Topic/CBasePane::OnDrawCaption.md)|在繪製時，架構會呼叫這個方法標頭。|  
|[CBasePane::OnMovePaneDivider](../Topic/CBasePane::OnMovePaneDivider.md)|目前未使用這個方法。|  
|[CBasePane::OnPaneContextMenu](../Topic/CBasePane::OnPaneContextMenu.md)|呼叫由架構，在建立具有  窗格的清單中的功能表。|  
|[CBasePane::OnRemoveFromMiniFrame](../Topic/CBasePane::OnRemoveFromMiniFrame.md)|呼叫框架，該窗格從其父代 \(Parent\) 微型框架視窗中移除。|  
|[CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md)|`CBasePane` 不使用這個方法。|  
|`CBasePane::OnUpdateCmdUI`|內部使用。|  
|[CBasePane::PaneFromPoint](../Topic/CBasePane::PaneFromPoint.md)|傳回包含指定點的窗格。|  
|`CBasePane::PreTranslateMessage`|由類別 [CWinApp](../../mfc/reference/cwinapp-class.md) 將 Windows 訊息，然後才會傳送至 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前。  \(覆寫 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)\)。|  
|[CBasePane::RecalcLayout](../Topic/CBasePane::RecalcLayout.md)|`CBasePane` 不使用這個方法。|  
|[CBasePane::RemovePaneFromDockManager](../Topic/CBasePane::RemovePaneFromDockManager.md)|將窗格與停駐管理員的清單中移除。|  
|[CBasePane::SaveState](../Topic/CBasePane::SaveState.md)|儲存窗格的狀態變更登錄。|  
|[CBasePane::SelectDefaultFont](../Topic/CBasePane::SelectDefaultFont.md)|針對指定的裝置內容來選取預設字型。|  
|`CBasePane::Serialize`|讀取或寫入這個物件從或其中的檔案。  \(覆寫 [CObject::Serialize](../Topic/CObject::Serialize.md)\)。|  
|[CBasePane::SetControlBarStyle](../Topic/CBasePane::SetControlBarStyle.md)|設定控制項的樣式。|  
|[CBasePane::SetDockingMode](../Topic/CBasePane::SetDockingMode.md)|將窗格設定為的控制項。|  
|`CBasePane::SetMDITabbed`|內部使用。|  
|[CBasePane::SetPaneAlignment](../Topic/CBasePane::SetPaneAlignment.md)|將窗格的對齊方式。|  
|`CBasePane::SetPaneRect`|內部使用。|  
|[CBasePane::SetPaneStyle](../Topic/CBasePane::SetPaneStyle.md)|將窗格設定的樣式。|  
|`CBasePane::SetRestoredFromRegistry`|內部使用。|  
|[CBasePane::SetWindowPos](../Topic/CBasePane::SetWindowPos.md)|變更窗格的大小、位置和疊置順序。|  
|[CBasePane::ShowPane](../Topic/CBasePane::ShowPane.md)|顯示或隱藏窗格。|  
|[CBasePane::StretchPane](../Topic/CBasePane::StretchPane.md)|垂直或水平縮放控制\] 窗格。|  
|[CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md)|從目前停駐的內建網站、預設滑桿或小型框架視窗中移除窗格。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CBasePane::DoPaint](../Topic/CBasePane::DoPaint.md)|填滿窗格的背景。|  
  
## 備註  
 如果您想要建立支援擴充停駐功能可在窗格中的 MFC 類別，您必須衍生自 `CBasePane` 或從 [CPane Class](../../mfc/reference/cpane-class.md)。  
  
## 自訂秘訣  
 繼承自的下列自訂提示與 [CBasePane Class](../../mfc/reference/cbasepane-class.md) 和任何類別:  
  
-   當您建立窗格時，您可以將數個新樣式:  
  
    -   `AFX_CBRS_FLOAT` 執行窗格浮動。  
  
    -   `AFX_CBRS_AUTOHIDE` 啟動自動隱藏模式。  
  
    -   `AFX_CBRS_CLOSE` 讓窗格關閉 \(隱藏\)。  
  
     這些是您可以結合位元 OR 作業的旗標。  
  
     `CBasePane` 執行下列虛擬 Boolean 方法反映這些旗標: [CBasePane::CanBeClosed](../Topic/CBasePane::CanBeClosed.md)， [CBasePane::CanAutoHide](../Topic/CBasePane::CanAutoHide.md)， [CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md)。  您可以覆寫這些成員在衍生類別中自訂其行為。  
  
-   您可以透過覆寫 [CBasePane::CanAcceptPane](../Topic/CBasePane::CanAcceptPane.md)自訂的停駐行為。  將防止其他窗格的  窗格中的這個方法會傳回 `FALSE` 停駐到它。  
  
-   如果您要建立不可以浮動，並防止其他窗格停駐在它前面的靜態窗格 \(類似於 OutlookDemo 範例中的 Outlook 功能區\)，請建立為非浮動並覆寫 [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md) 傳回 `FALSE`。  如果建立窗格，而不用 `AFX_CBRS_FLOAT` 樣式，預設實作會傳回 `FALSE` 。  
  
-   \-1 以外，建立具有 ID 的所有窗格。  
  
-   若要判斷窗格可視性，請使用 [CBasePane::IsVisible](../Topic/CBasePane::IsVisible.md)。  它是以索引標籤和自動隱藏模式正確處理可視性狀態。  
  
-   如果您想要建立非浮動可調整大小的窗格，請建置專案，而不會 `AFX_CBRS_FLOAT` 樣式並呼叫 [CFrameWnd::DockControlBar](../Topic/CFrameWnd::DockControlBar.md)。  
  
-   從停駐配置排除窗格或從其停駐列移除工具列，請呼叫 [CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md)。  請不要呼叫這個方法窗格中的 \[自動隱藏模式或位於索引標籤式視窗索引標籤的  窗格中的。  
  
-   如果您想要取消停駐或浮動在自動隱藏模式的窗格，您必須呼叫 [CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md) 和 `FALSE` ，當第一個引數，在您呼叫 [CBasePane::FloatPane](../Topic/CBasePane::FloatPane.md) 或 [CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md)之前。  
  
## 範例  
 下列範例會在 `CBasePane` 類別會示範如何使用各種方法。  範例會示範如何從 `CFrameWndEx` 類別擷取窗格以及如何設定停駐窗格模式、對齊和窗格樣式。  程式碼是從 [文字填補範例](../../top/visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad#2](../../mfc/reference/codesnippet/CPP/cbasepane-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
## 需求  
 **標題:** afxbasepane.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPane](../../mfc/reference/cbasepane-class.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)